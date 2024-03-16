| Total QA Reports |
|------------------|

| Risk   | Issues Details                                               | Number|          
|--------|--------------------------------------------------------------|-------|
| [L-1]  | `suspendMessages()` Lacks zero hashes check.                 |       |
| [L-2]  | lack of function to update single guardian in `Guardian.sol` |       |


## [L-1] `suspendMessages()` Lacks zero hashes check.

#### Description
https://github.com/code-423n4/2024-03-taiko/blob/b6885955903c4ec6a0d72ebb79b124c6d0a1002b/packages/protocol/contracts/bridge/Bridge.sol#L82C1-L95C6

#### Recommended Mitigation Steps
```solidity
    /// @notice Suspend or unsuspend invocation for a list of messages.
    /// @param _msgHashes The array of msgHashes to be suspended.
    /// @param _suspend True if suspend, false if unsuspend.
    function suspendMessages(
        bytes32[] calldata _msgHashes,
        bool _suspend
    )
        external
        onlyFromOwnerOrNamed("bridge_watchdog")
    {
        require(_msgHashes.length != 0, "Enter your message hashes");
        uint64 _timestamp = _suspend ? type(uint64).max : uint64(block.timestamp);
        for (uint256 i; i < _msgHashes.length; ++i) {
            bytes32 msgHash = _msgHashes[i];
            require(_msgHashes[i] != bytes32(0), "Message hashes must not be zero");
            proofReceipt[msgHash].receivedAt = _timestamp;
            emit MessageSuspended(msgHash, _suspend);
        }
    }

```

## [L-2] lack of function to update single guardian in `Guardian.sol`

#### Description
if the owner wants to replace a single guardian, he has to reset all the set of guardians.
consider adding a function to replace one guardian.

#### Recommended Mitigation Steps
add this event and the function below:
```solidity
event GuardiansUpdated(uint32 version, address oldGuardian, address newGuardian);
```
```solidity
    function replaceOneGuardian(address _oldGuardian, address _newGuardian) external onlyOwner nonReentrant {
        // Check if the new guardian address is valid
        if(_newGuardian == address(0)) revert INVALID_GUARDIAN();

        // Find the index of the old guardian
        uint256 oldGuardianIndex = guardianIds[_oldGuardian];
        if (oldGuardianIndex == 0) {
        revert GUARDIAN_NOT_FOUND();
        }

        // Update the guardian at the specified index
        guardians[oldGuardianIndex] = _newGuardian;
        duardianIds[_newGuardian] = oldGuardianIndex;

        // Bump the version so previous approvals get invalidated
        ++version;

        emit GuardianUpdated(version, _oldGuardian, _newGuardian);
    }
```