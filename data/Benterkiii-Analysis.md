## Consider adding an Owner function to update a single guardian in `Guardian.sol`

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

### Time spent:
27 hours