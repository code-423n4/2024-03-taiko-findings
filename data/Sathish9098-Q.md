# QA REPORTS

##

## [L-] Hardcoded ``MAX_TOKEN_PER_TXN`` value

Users who wish to bridge more than 10 tokens will have to perform multiple transactions. For users with large collections, this could lead to increased transaction costs (gas fees) and a more time-consuming process.

Implementing a governance mechanism to adjust the maximum tokens per transaction could provide flexibility while ensuring that changes are made responsibly and with community consensus.

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/tokenvault
/BaseNFTVault.sol

/// @notice Maximum number of tokens that can be transferred per transaction.
    uint256 public constant MAX_TOKEN_PER_TXN = 10;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L52-L53

##

## [L-1] Unsafe Down casting 

Casting the chain ID, which is a uint256 type, down to a uint64 type. This is considered unsafe downcasting because uint256 can represent much larger numbers than uint64 can. If the value of block.chainid exceeds the maximum value that uint64 can represent (which is 2^64 - 1), then the cast will result in data loss, leading to incorrect behavior.

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/L1/libs/LibDepositing.sol

90: amount: uint96(data),

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L90


##

## [L-] ``addresses`` upcast and compared to values larger than a ``uint160``, may result in collisions

If the value is being compared to an input value in order to reject it, rather than allowing it to be converted to an address, the check will pass if the value is larger than type(uint160).max, even if, when cast, it matches the gating address.

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/L1/libs/LibDepositing.sol

151: return (uint256(uint160(_addr)) << 96) | _amount;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L151

##

## [L- ] ``receive()/payable fallback()`` function does not authorize requests

Having no access control on the function (e.g. require(msg.sender == address(weth))) means that someone may send Ether to the contract, and have no way to get anything back out, which is a loss of funds. If the concern is having to spend a small amount of gas to check the sender against an immutable address, the code should at least have a function to rescue mistakenly-sent Ether.

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/bridge
/Bridge.sol

70: receive() external payable { }

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L70

##

## [L-] Code does not follow the best practice of check-effects-interaction

Code should follow the best-practice of [check-effects-interaction](https://blockchain-academy.hs-mittweida.de/courses/solidity-coding-beginners-to-intermediate/lessons/solidity-11-coding-patterns/topic/checks-effects-interactions/), where state variables are updated before any external calls are made. Doing so prevents a large class of reentrancy bugs.

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/L1/libs/LibProving.sol

196: if (returnLivenessBond) {
                tko.transfer(blk.assignedProver, blk.livenessBond);
                blk.livenessBond = 0;
            }


242: tko.transferFrom(msg.sender, address(this), tier.contestBond);

                // We retain the contest bond within the transition, just in
                // case this configuration is altered to a different value
                // before the contest is resolved.
                //
                // It's worth noting that the previous value of ts.contestBond
                // doesn't have any significance.
                ts.contestBond = tier.contestBond;



```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L196-L197

##

## [L-] Consider implementing two-step procedure for updating protocol addresses

A copy-paste error or a typo may end up bricking protocol functionality, or sending tokens to an address with no known private key. Consider implementing a two-step procedure for updating protocol addresses, where the recipient is set as pending, and must 'accept' the assignment by making an affirmative call. A straight forward way of doing this would be to have the target contracts implement EIP-165, and to have the 'set' functions ensure that the recipient is of the right interface type.

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/tokenvault/BridgedERC20.sol

80: function setSnapshoter(address _snapshooter) external onlyOwner {
        snapshooter = _snapshooter;
    }
```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L80-L82

##

## [L- ] Empty receive()/fallback() function

If the intention is for Ether sent by a caller to be used for an actual purpose (i.e. the function is not just a WETH withdraw() handler), the function should call another function (e.g. call weth.deposit() and use the token on the caller's behalf) or at least emit an event to track that funds were sent directly to it.

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/bridge
/Bridge.sol

70: receive() external payable { }

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L70

##

## [L-] External calls in an un-bounded for-loop may result in a DOS

Consider limiting the number of iterations in for-loops that make external calls

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/tokenvault
/ERC1155Vault.sol


269: for (uint256 i; i < _op.tokenIds.length; ++i) {
                    IERC1155(_op.token).safeTransferFrom({
                        from: msg.sender,
                        to: address(this),
                        id: _op.tokenIds[i],
                        amount: _op.amounts[i],
                        data: ""
                    });
                }
```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L251-L253

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/tokenvault
/ERC721Vault.sol

170: for (uint256 i; i < _tokenIds.length; ++i) {
                IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);
            }

210:  for (uint256 i; i < _op.tokenIds.length; ++i) {
                    t.safeTransferFrom(_user, address(this), _op.tokenIds[i]);
                }

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L170-L172

##

## [L-] No need ``nonReentrant`` modifier for  admin only functions 





## [L-] [1] Setters should prevent re-setting of the same value

[2] Incorrect comment in _stakeTokenSafeTransferFrom()








