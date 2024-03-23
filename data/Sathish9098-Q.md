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

## [L-] 







