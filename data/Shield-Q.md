# Quality Assuarance

## L-01 Discrepancy between documentation and logic implementation wrt BLOCK_SYNC_THRESHOLD

# Lines of code
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L145-L152

### Impact
BLOCK_SYNC_THRESHOLD has the following natspec comment:

`@notice The number of L2 blocks to wait before syncing L1 block details`

But the issue here is that, it mentions number of L2 blocks. But there is no need to add number of L2 blocks on the L1 block height because the block durations are different in two chains. Hence the natspec comments should be corrected as number of L1 blocks

### Tools Used
Manual review

### Recommended Mitigation Steps
Update the natspec comment for better clarity

## L-02 Renundant check for validityBond for top tier proof

# Lines of code

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L223

### Impact
There is a existing top tier check [here](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L186) & a validity bond check [here](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L224) so the check on line 223 should be removed

### Tools Used
Manual review

### Recommended Mitigation Steps
remove the renundant check

## L-03 Wrong max prover fee value declared as a constant 

# Lines of code

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L38

### Impact
During external calls only 63/64 of the total gas limit is available hence the tx will revert if more than 63/64th of the total gas is used i.e 49219 gas in this case

### Tools Used
Manual review

### Recommended Mitigation Steps
either update the comment on line 37 or update the max value to 49219

## L-04 Lack of information around reward calculation in a scenario where the new prover is also the contestor and no previous contestor exists 

# Lines of code

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L376

### Impact
there is no information regarding the reward calculation mentioned [here](https://taiko.mirror.xyz/Z4I5ZhreGkyfdaL5I9P0Rj0DNX4zaWFmcws-0CVMJ2A) where the new prover is also the contestor and no previous contestor exists


### Tools Used
Manual review

### Recommended Mitigation Steps
add information regarding this scenario in comments for more clarity

## L-05 data length check in onMessageInvocation can be skipped

# Lines of code

https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L491

### Impact
In case of a fallback method there is no `msg.data` involved hence the if check can be by passed whereas it should be handled there in case of a contract


### Tools Used
Manual review

### Recommended Mitigation Steps
update this check to handle the fallback scenario
```
        if (
            _message.data.length >= 4 // msg can be empty
                && bytes4(_message.data) != IMessageInvocable.onMessageInvocation.selector
                && _message.to.isContract()
        )
``` 
to

```
        if (
            _message.data.length >= 4 // msg can be empty
                || (bytes4(_message.data) != IMessageInvocable.onMessageInvocation.selector
                && _message.to.isContract())
        )
```


## L-06 ERC1155Vault.supportsInterface function does not indicate support for IMessageInvocable interface
 

# Lines of code

https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L192

### Impact
The ERC1155Vault.supportsInterface indicates that it implements the following interfaces :
```
ERC1155ReceiverUpgradeable
IRecallableSender
```

But the ERC1155Vault implements the IMessageInvocable interface and it is not referred in the ERC1155Vault.supportsInterface function.


### Tools Used
Manual review

### Recommended Mitigation Steps
update the BaseVault.supportsInterface function as shown below:
```
function supportsInterface(bytes4 _interfaceId) public view virtual override returns (bool) {
        return _interfaceId == type(IRecallableSender).interfaceId || _interfaceId == type(IMessageInvocable).interfaceId;
}
```

## L-07 No recovery logic implementation in the bridge contract to recover the ERC20, ERC721, ERC1155 tokens mistakenly sent to it.
 

# Lines of code

https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L115

### Impact
The bridge contract allows the native eth transfer by directly calling the `bridge.sendMessage` function. 

But for transfer of ERC20, ERC721 and ERC1155 the vaults should be used and the transaction should initiate from the sendToken function of the respective vault.

But a user might erroneously call the bridge.sendMessage direclty to bridge ERC20, ERC721 or ERC1155 tokens by directly transaferring to the bridge contract. 

There is no recovery function to recover these tokens from the bridge


### Tools Used
Manual review

### Recommended Mitigation Steps
have a fund recovery mechanism in the bridge contract


## L-08 Renundant data conversion in BridgedERC721.tokenURI
 

# Lines of code

https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L110

### Impact
In `BridgedERC721.tokenURI` the method `LibBridgedToken.buildURI` is called which also returns a string value hence there is no need to use `abi.encodePacked` and cast it to string again
`

### Tools Used
Manual review

### Recommended Mitigation Steps
remove the unecessary string casting in `tokenURI`


## L-09 Logic implementation does not match the natspec comments
 

# Lines of code

https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L266

### Impact
In the ERC20Vault.onMessageInvocation function there is a discrepency beween the natspec comments and the logic implementation.

```
//Don't send the tokens back to from because from is on the source chain.

if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();
```

Above natspec comments states that from address should not be allowed. 

Hence the check should be updated

### Tools Used
Manual review

### Recommended Mitigation Steps
Update the check to 
```
if (to == address(0) || to == address(this) || to == from) revert VAULT_INVALID_TO();
```

## L-10 No implementation of _authorizeUpgrade in terms of the UUPS upgrade mechanism
 

# Lines of code

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L114

### Impact
In `EssentialContract` UUPS upgrade mechanism is used but `_authorizeUpgrade` is not implemented then what is the point of using UUPS upgrade  if there is no upgrade mechanism


### Tools Used
Manual review

### Recommended Mitigation Steps
Add implementation for `_authorizeUpgrade`

## L-11 Missing override for renounceOwnership
 

# Lines of code

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L109-L112

### Impact
The EssentialContract is an abstract contract which inherits from the Ownable2StepUpgradeable contract. 

There are multiple contracts which implements the EssentialContract contract by inheriting it. 

The Owner of the each of the child contracts is set during the initialization and is never allowed to be set to `address(0)`` as per the following logic implementation of `_transferOwnership`

Hence it is recommended to override the renounceOwnership function to revert if called such that the ownership is not set to address(0) by mistake or by a malicious current owner


### Tools Used
Manual review

### Recommended Mitigation Steps
override the `renounceOwnership` function to revert if new owner is `address(0)`


## L-12 Possibility of DOS in message execution
 

# Lines of code

https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L290

### Impact
In case `refundTo` address is not a eoa it can revert ether transfer either intentionally or by mistake so there needs to be a mechanism implemented here which ensures that the message execution remains unaffected


### Tools Used
Manual review

### Recommended Mitigation Steps
add a  try/catch block for the refund mechanism to ensure there is no DOS possibility for message execution

## L-13 discrepency in code and docs in terms of the signal slot # Lines of code

https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L63-L65

### Impact
Acc to the [readme](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/README.md#process-message) & [the natspec docs](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/ISignalService.sol#L56) it is clear that the signal slot value should be set to 1 but actually it is set as the value of the signal


### Tools Used
Manual review

### Recommended Mitigation Steps
update the natspec comment and the readme

## L-14 incorrect natspec documentation for proveMessageReceived

https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L374

### Impact
The `proveMessageReceived` method is used to prove whether the message is received at the destination chain or not but it's natspec documentation is the same as `proveMessageFailed`


### Tools Used
Manual review

### Recommended Mitigation Steps
update the natspec doc for `proveMessageReceived`


## L-15 Lack of ERC165 implementation on the critical smart contracts of the protocol could lead to unexpected behavior or failed transactions.


https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L237-L239

### Impact
There are multiple interfaces declared in the taiko protocol and these interfaces are used to call on contract addresses by wrapping the address around the interface and calling the respective functions.

But some of these contracts don't implement ERC165 correctly and hence don't not check whether the given interface is actually implemented in the called contract.

For example the `ERC20Vault.sendToken` function is used to transfer ERC20 tokens to the specific vault and sends a message to the destination chain. Here initially the sendMessage of the source chain is called on the source bridge contract to transfer the native eth and then to deliver the message to the destination chain.


There is no check to ensure the resolved address returned from resolve("bridge", false) call actually implements the sendMessage function on the source bridge contract. If it does not and the resolved address has a fallback function which does not revert then the transaction will succeed and the sent native tokens will be lost as a result


### Tools Used
Manual review

### Recommended Mitigation Steps
in terms of the example given, update the `supportsInterface` method in the `BaseVault.sol` and make sure the bridge contract adheres to the `IBridge` interface

## L-16 Missing contract existence check for signalService


https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L591

### Impact
The `_proveSignalReceived` function is called multiple times in the Bridge.sol contract. This function is used to verify whether the signal is received by the destination chain. 

The _proveSignalReceived function returns a bool value which indicates the success of a staticCall to the _signalService contract.

        (success_,) = _signalService.staticcall(data);


The issue here is that there is no isContract check on the `_signalService` address. If the `_signalService` is mistakenly set to a EOA address then staticCall will always return true thus breaking the behavior of critical functions of the protocol.


### Tools Used
Manual review

### Recommended Mitigation Steps
check whether the `_signalService` is  a contract prior to the staticCall to it.

## L-17 No mechanism to update supported chain id's in `getInvocationDelays`


https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L417

### Impact
The `Bridge.getInvocationDelays` function is used to return the invocation delay values for each of the chains the taico protocol supports.

But the issue is that these chainIds and their respective invocation delay values are currently hardcoded. Hence the Taiko protocol will have to upgrade the Bridge contract for every new supported chain by updating the getInvocationDelays function. And if the invocation delay needs to be updated in the future the Bridge contract will again have to be upgraded


### Tools Used
Manual review

### Recommended Mitigation Steps
allow the owner of the contract or Taiko DAO to update the supported chain list of the Taiko protocol dynamically for their respective invocation delay values.

## L-18 Possibility of funds getting locked during `onMessageRecalled` execution


https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L285

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L127

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L110

### Impact
All token vaults implement `onMessageRecalled` method but there maybe a scenario where the token transfer reverts due to `_message.srcOwner` and this would result in funds getting, so hence there should be a recovery mechanism to handle this scenario


### Tools Used
Manual review

### Recommended Mitigation Steps
add a try/catch block on the transfer call so in case the transfer fails there is still a way to get the funds out

## L-19 discrepency between a natspec and logic implementation in `Bridge.processMessage`


https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L278

### Impact
In the natspec comment it is mentioned that
```
// Use the specified message gas limit if called by the owner, else
// use remaining gas
```

But `_message.destOwner` is allowed to call the `processMessage` with `_message.gasLimit == 0` as shown below:
```
            if (_message.gasLimit == 0 && msg.sender != _message.destOwner) {
                revert B_PERMISSION_DENIED();
            }
```

And if the `_invokeMessageCall` is called by the `_message.destOwner` with `_message.gasLimit == 0` then the transaction will revert in the `_invokeMessageCall` as shwon below:

`if (_gasLimit == 0) revert B_INVALID_GAS_LIMIT();`

Hence the _invokeMessageCall is called by the _message.destOwner with `gasleft()`


### Tools Used
Manual review

### Recommended Mitigation Steps
update the natspec commment for the same

## L-20 wrong key value been deleted in `bridgedToCanonical` mapping


https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L180

### Impact
The `ERC20Vault.changeBridgedToken` function is used to change the old bridged token to a new bridged token. 

The issue here is that the bridgedToCanonical mapping is cleared for the _btokenNew where as it should be cleared for the btokenOld_ address.

            delete bridgedToCanonical[_btokenNew];


If the bridgedToCanonical[_btokenNew] already had a value (to be deleted) the transaction would have reverted at the beginning.

        if (_btokenNew == address(0) || bridgedToCanonical[_btokenNew].addr != address(0)) {
            revert VAULT_INVALID_NEW_BTOKEN();
        } 

Hence the correct key's value should be removed from the mapping


### Tools Used
Manual review

### Recommended Mitigation Steps
change `delete bridgedToCanonical[_btokenNew];` to delete `bridgedToCanonical[btokenOld_];`


## L-21 User can claim the airdrop of a previous merkle root during merkle root change



https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L50

### Impact
The `ERC20Airdrop.claimAndDelegate` function is used by an external msg.sender to claim the airdrop for a user.

The airdrop amount and and recipient is determined by the merkle root stored in the MerkleClaimable contract.

The issue here is that the merkle root can be changed by the owner of the MerkleClaimable contract, which means the owner has the privilege to change the user and airdrop amount, by calling the `MerkleClaimale.setConfig` function.

If the owner decides to change the merkle root during an ongoing airdrop then the user can front run and claim the airdrop of the previous merkle root.
This can result in double spending in a way as well.


### Tools Used
Manual review

### Recommended Mitigation Steps
add the pause functionality to the `claimAndDelegate` function so that it can be paused when the merkle root is about to be changed so that the user is unable to claim at that time. 

## L-22 The maliciosu user can DoS the initial airdrop claim of another user


https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L50

### Impact
A malicious user can claim the airdrop by calling the `ERC20Airdrop.claimAndDelegate` function. But here the malicious user can user can use the delegationData of another user (User A) in the transaction and front run that user's airdrop claim transaction.

Hence when the transaction of User A is executed it will revert since the nonce of his delegation signature has already being consumed. Hence his claim transactino is DoS in hte first attempt which can cause delay. Hence user A will have to provide a new signature for delegation and then claim the airdrop.

This issue is here since both the airdrop claim and delegation is atomic 



### Tools Used
Manual review

### Recommended Mitigation Steps
it is recommended to make it `claimAndDelegate` a two step process


## L-23 User can not claim the same amount twice using the ERC20Airdrop.claimfunction



https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L50

### Impact
The ERC20Airdrop.claim allows multiple claims of amounts as per its logic implementation:

    function claim(address user, uint256 amount, bytes32[] calldata proof) external nonReentrant {

        _verifyClaim(abi.encode(user, amount), proof); 

        claimedAmount[user] += amount;
    } 


The += amount is used to calculate the claimedAmount of a user. This indicates that the merkle tree might have multiple leaves for a single user airdrops.

But the issue is if there are mulitple claims of the same amount for a user then the transaction will revert in the MerkleClaimable._verifyClaim function.

        if (isClaimed[hash]) revert CLAIMED_ALREADY();


This happens because the hash is calculated using the user, amount values and the same amount for the same user will result in the same hash. This will prompt the user to lose on his airdrop amount if the claim window is expired. 

And if the owner tries to update the merkle root to update the claim amounts then other users can front run this merkle root update and claim rewards twice thus prompting double spending.

Here is a poc to demonstrate this
```
// SPDX-License-Identifier: MIT
pragma solidity 0.8.24;

import "../../TaikoTest.sol";

contract MyERC20 is ERC20 {
    constructor(address owner) ERC20("Taiko Token", "TKO") {
        _mint(owner, 1_000_000_000e18);
    }
}

contract MockERC20Airdrop2 is ERC20Airdrop2 {
    function _verifyMerkleProof(
        bytes32[] calldata, /*proof*/
        bytes32, /*merkleRoot*/
        bytes32 /*value*/
    )
        internal
        pure
        override
        returns (bool)
    {
        return true;
    }
}

contract TestERC20Airdrop2 is TaikoTest {
    address public owner = randAddress();

    bytes32 public constant merkleRoot = bytes32(uint256(1));
    bytes32[] public merkleProof;
    uint64 public claimStart;
    uint64 public claimEnd;

    ERC20 token;
    ERC20Airdrop2 airdrop2;

    function setUp() public {
        claimStart = uint64(block.timestamp + 10);
        claimEnd = uint64(block.timestamp + 10_000);
        merkleProof = new bytes32[](3);

        token = new MyERC20(address(owner));

        airdrop2 = ERC20Airdrop2(
            deployProxy({
                name: "MockERC20Airdrop",
                impl: address(new MockERC20Airdrop2()),
                data: abi.encodeCall(
                    ERC20Airdrop2.init,
                    (address(0), claimStart, claimEnd, merkleRoot, address(token), owner, 10 days)
                    )
            })
        );

        vm.prank(owner, owner);
        MyERC20(address(token)).approve(address(airdrop2), 1_000_000_000e18);
        vm.roll(block.number + 1);
    }

    function test_claim_same__amount_airdrop2() public {
        vm.warp(uint64(block.timestamp + 11));

        vm.prank(Alice, Alice);
        airdrop2.claim(Alice, 100, merkleProof);

        vm.warp(uint64(block.timestamp + 1000));
        airdrop2.claim(Alice, 50, merkleProof);

        (uint256 balance, ) = airdrop2.getBalance(Alice);
        assertEq(balance, 150);

        vm.warp(uint64(block.timestamp + 2000));
        vm.expectRevert(MerkleClaimable.CLAIMED_ALREADY.selector);                
        airdrop2.claim(Alice, 100, merkleProof);        

    }
```
paste this code in a file according to the `TaikoTest` import and run `forge test --mt test_claim_same__amount_airdrop2 -vvvvv`

### Tools Used
Manual review

### Recommended Mitigation Steps
it is recommended to use a nonce value in the hash if multiple claims are allowed for a single user for the airdrop

## L-24 TKO token value can drop in the future

# Lines of code

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L207


### Impact
the bond when proving a block is the project's token TKO, the thing is that if the value of this token drops then the value of the validity bond would be small as well 

As Currently the liveness bond is 250 taiko tokens as defined in the TaikoL1.getConfig function.

            livenessBond: 250e18, // 250 Taiko token

### Tools Used
Manual review

### Recommended Mitigation Steps
Have a mechanism to update the bond value in case the price drops