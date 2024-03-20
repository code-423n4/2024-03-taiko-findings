# Guardians.sol - repeated storage access
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L88

`guardians.length` is reading from storage. Gas can be saved by using `i + 1` since `guardians.length` matches `i + 1`.
```solidity
guardianIds[guardian] = i + 1;
```