# QA REPORTS

##

## [L-1] Unsafe Down casting 

Casting the chain ID, which is a uint256 type, down to a uint64 type. This is considered unsafe downcasting because uint256 can represent much larger numbers than uint64 can. If the value of block.chainid exceeds the maximum value that uint64 can represent (which is 2^64 - 1), then the cast will result in data loss, leading to incorrect behavior.

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/common/AddressResolver.sol

39:  return _resolve(uint64(block.chainid), _name, _allowZeroAddress);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressResolver.sol#L39

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







