# Lo-01 TaikoToken:init can be front-run

## Description
The contract has no checks to provide initialization access-control. Therefore any party is able to initialize it and make Taiko deployer have to deploy a new contract from scratch.
The impact is low due to the not-so-high costs for deploying new contracts, but it should be noted as the gas spent to deploy a new contract is much bigger than the amount to initialize it.
## Recommended Mitigation Steps
Make sure to deploy the TaikoToken and initialize it atomically via a deployer contract, this way it is impossible to front-run the initialization.
A second option is to batch the transactions at a MEV-protected transaction bundle, making the deployment and initialization of the contract effectively protected.

_______________________________
# Lo-02 TaikoL2:anchor underflows block number making it revert when block number is zero 

## Description
On L2 genesis, the block.number is equal to zero. The init function at the TaikoL2 contract utilizes this value to calculate the publicInputHash global public bytes32. As can be seen at the following code snippet:
```solidity
function init(
        address _owner,
        address _addressManager,
        uint64 _l1ChainId,
        uint64 _gasExcess
    )
        external
        initializer
    {
    ...
    if (block.number == 0) {
        // This is the case in real L2 genesis
    }
    ...
    (publicInputHash,) = _calcPublicInputHash(block.number);
    }
```

This makes calling the anchor transaction impossible at the same block init is called. The reason for that is during the anchor call, the parent block is calculated inside an unchecked block as block.number -1. 
In this case, 0 - 1 results in 2^256 - 1 for the first ever block.
```solidity
function anchor(
        bytes32 _l1BlockHash,
        bytes32 _l1StateRoot,
        uint64 _l1BlockId,
        uint32 _parentGasUsed
    )
        external
        nonReentrant
    {
    ...
    uint256 parentId;
        unchecked {
            parentId = block.number - 1;
        }
    (bytes32 publicInputHashOld, bytes32 publicInputHashNew) = _calcPublicInputHash(parentId);
        if (publicInputHash != publicInputHashOld) {
            revert L2_PUBLIC_INPUT_HASH_MISMATCH();
        }
    ...
}
```

This will necessarily make the anchor call revert with the L2_PUBLIC_INPUT_HASH_MISMATCH error.
The issue is the anchor call is always the first call of a block at Taiko L2 instance. Therefore the genesis block is not able to hold a single transaction.

_____________________

# Lo-03 TimelockTokenPool:getMyGrantSummary accepts precision mismatches

## Description
The getMyGrantSummary view function is utilized for withdraw calculations at the TimelockTokenPool contract. It is crucial to determine the amount of taikoTokens and costTokens that will be withdrawn and payed respectively during withdraw calls.
The issue lies when it rounds the amountUnlocked variable in order to induce precision accounting at the token level but withdraws tokens with wei level precision. Take a look at the following code snippet, it returns a amountToWithdraw variable that is not divided by anything and a costToWithdraw based on amounts unlocked that round down anything that is less than 1e18:
```solidity
function getMyGrantSummary(address _recipient)
        public
        view
        returns (
            uint128 amountOwned,
            uint128 amountUnlocked,
            uint128 amountWithdrawn,
            uint128 amountToWithdraw,
            uint128 costToWithdraw
        )
    {
    ...
		amountWithdrawn = r.amountWithdrawn;
        amountToWithdraw = amountUnlocked - amountWithdrawn;

        // Note: precision is maintained at the token level rather than the wei level, otherwise,
        // `costPaid` must be a uint256.
        uint128 _amountUnlocked = amountUnlocked / 1e18; // divide first
        costToWithdraw = _amountUnlocked * r.grant.costPerToken - r.costPaid;
	}
```

This rounds down the amount paid per token while allowing more sub token amounts to be received without payment.
## Impact
A user is able to withdraw sub 1e18 amounts while paying zero cost tokens.
There's accumulation of dust amounts of up to 0.9999 token units per withdraw call.

## Proof of Concept
Paste the following code snippet at the TimelockTokenPool.t.sol:
```solidity
function test_precision_mismatch_1() public{
        uint64 grantStart = uint64(block.timestamp);
        uint32 grantPeriod = 1 days;
        pool.grant(
            Alice,
            TimelockTokenPool.Grant(1e18, strikePrice1, grantStart, 0, grantPeriod, 0, 0, 0)
        );

        vm.prank(Vault);
        tko.approve(address(pool), 1e18);

        uint256 halfTimeWithdrawCost = 5e17 / ONE_TKO_UNIT * strikePrice1;

        vm.warp(grantStart + 12 hours);
        (
            uint128 amountOwned,
            uint128 amountUnlocked,
            uint128 amountWithdrawn,
            uint128 amountToWithdraw,
            uint128 costToWithdraw
        ) = pool.getMyGrantSummary(Alice);

        assertEq(amountOwned, 5e17);
        assertEq(amountUnlocked, 5e17);
        assertEq(amountWithdrawn, 0);
        assertEq(amountToWithdraw, 5e17);
        assertEq(costToWithdraw, 0);

        vm.warp(grantStart + 1 days - 1);
        (amountOwned, amountUnlocked, amountWithdrawn, amountToWithdraw, costToWithdraw) =
            pool.getMyGrantSummary(Alice);
        assertApproxEqRel(amountOwned, 1e18, 1e15); // approximately 0.01% close
        assertApproxEqRel(amountUnlocked, 1e18, 1e15);
        assertEq(amountWithdrawn, 0);
        assertApproxEqRel(amountToWithdraw, 1e18, 1e15);
        assertEq(costToWithdraw, 0);

        vm.warp(grantStart + 1 days);
        (amountOwned, amountUnlocked, amountWithdrawn, amountToWithdraw, costToWithdraw) =
            pool.getMyGrantSummary(Alice);
        assertEq(amountOwned, 1e18);
        assertEq(amountUnlocked, 1e18);
        assertEq(amountWithdrawn, 0);
        assertEq(amountToWithdraw, 1e18);
        // notice how the cost to withdraw abruptly jumps
        assertEq(costToWithdraw, 1e4); // as it is 0.01 usdc per unit of tko

    }
```

Run it with the following command:
```shell
forge test --match-test test_precision_mismatch_1 -vvv
```
## Tools Used
Manual review
## Recommended Mitigation Steps
Divide amountToWithdraw by 1e18 then multiply it by 1e18 so it keeps the same entire token precision as used at the cost calculation.

_______________________________

# Lo-04 ERC721Vault:onMessageInvocation allows minting to the Vault contract

## Description
The ERC20Vault and ERC1155Vault have checks to ensure the vault contract is not the receiver on a transfer of tokens in the context of messageInvocation during bridging operations, as can be seen in the following code snippets:
ERC20Vault:
```solidity
function onMessageInvocation(bytes calldata _data)
        external
        payable
        nonReentrant
        whenNotPaused
    {
    ...
    if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();
    ...
}
```

ERC1155Vault:
```solidity
function onMessageInvocation(bytes calldata data) external payable nonReentrant whenNotPaused {
...
	if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();
...
```

The ERC721Vault's onMessageInvocation function doesn't have the same check, therefore it allows tokens to be transferred the contract itself.
## Recommended Mitigation Steps
Make sure to implement the same check at the ERC721Vault.onMessageInvocation function:
```solidity
if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();
```

_________________

# Lo-05 TimelockTokenPool:calcAmount private function returns the full amount if the start argument is equal zero.

## Impact
Grants that are created with a zero value at either the grantStart or the unlockStart values don't return amounts proportional to how much time has passed in relation to grantPeriod/unlockPeriod, but rather the calcAmount private function returns the full amount if start is zero.
Here is the code snippet outlining this behavior:
```solidity
function _calcAmount(
        uint128 _amount,
        uint64 _start,
        uint64 _cliff,
        uint64 _period
    )
        private
        view
        returns (uint128)
    {
	...   
		if (_start == 0) return _amount;
	...
	}
```

Effectively this breaks the getAmountOwned and the getAmountUnlocked private view functions, as it returns the full grant amount even if the period has not fully passed. 
getAmountOwned is utilized by getMyGrantSummary, a function that determines the amount a grant recipient can withdraw at the withdraw function. It is also utilized by voidGrant private function to determine the amount to be voided. 
getAmountUnlocked is also utilized by getMyGrantSummary, and it also has a role in determining the amounts to withdraw.
In practice this means all grants created with grantStart or unlockStart set to zero will be able to be fully voided or withdrawn right away.
## Recommended Mitigation Steps
Remove the following line of the calcAmount private view function to ensure this wrong behavior is not possible anymore:
```solidity
if (_start == 0) return _amount;
```

The final calcAmount method should look like this:
```solidity
function _calcAmount(
        uint128 _amount,
        uint64 _start,
        uint64 _cliff,
        uint64 _period
    )
        private
        view
        returns (uint128)
    {
        if (_amount == 0) return 0;

        if (block.timestamp <= _start) return 0;

        if (_period == 0) return _amount; // @audit this is correct
        if (block.timestamp >= _start + _period) return _amount; // @audit this is correct

        if (block.timestamp <= _cliff) return 0;

        return _amount * uint64(block.timestamp - _start) / _period;
    }
```