**[1]** This comment is misleading. The code does the opposite.
```solidity
// Use the specified message gas limit if called by the owner, else
// use remaining gas
```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L278-L279

**[2]** This function is missing the `onlyInitializing` modifier:
```solidity
function __Essential_init(address _owner) internal virtual {
    _transferOwnership(_owner == address(0) ? msg.sender : _owner);
    __paused = _FALSE;
}
```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L109

**[3]** There is a typo in the comment:
```solidity
// Unchecked is safe:
// - _fee cannot be bigger than deposits_[i].amount
// - all values are in the same range (uint96) except loop
// counter, which obviously cannot be bigger than uint95 <- TYPO
// otherwise the function would be gassing out.
```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L98

**[4]** The `L1_TXLIST_OFFSET` error is not defined in the `TaikoErrors.sol`.
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L54

**[5]** There is a typo (`isAssignedPover`) in this code block:
```solidity
bool isAssignedPover = msg.sender == _blk.assignedProver;

// The assigned prover can only submit the very first transition.
if (_tid == 1 && _ts.tier == 0 && inProvingWindow) {
    if (!isAssignedPover) revert L1_NOT_ASSIGNED_PROVER();
} else {
    // Disallow the same address to prove the block so that we can detect that the
    // assigned prover should not receive his liveness bond back
    if (isAssignedPover) revert L1_ASSIGNED_PROVER_NOT_ALLOWED();
}
```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L416-L425

**[6]** Consider checking that the `Config.ethDepositRingBufferSize` is enough to accommodate `Config.ethDepositMaxCountPerBlock` deposits in the `LibVerifying._isConfigValid` function.
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L245

**[7]** Multiple contracts have comments specifying how the addresses of these contracts are labeled in the `AddressManager`. However, the `GuardianProver`, `GuardianVerifier`, and `SgxVerifier` are missing this comment. Consider adding these comments to improve clarity and consistency.