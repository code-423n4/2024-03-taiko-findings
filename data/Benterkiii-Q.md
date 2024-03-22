| Total QA Reports |
|------------------|

| Risk   | Issues Details                                               | Number|          
|--------|--------------------------------------------------------------|-------|
| [L-1]  | Lacks zero hashes check.                                     |       |


## [L-1] Lacks zero hashes check in `Bridge.sol`.

#### Description
2 instances of this issue:
https://github.com/code-423n4/2024-03-taiko/blob/b6885955903c4ec6a0d72ebb79b124c6d0a1002b/packages/protocol/contracts/bridge/Bridge.sol#L82C1-L95C6
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L97C1-L112C6

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
```solidity
    /// @notice Ban or unban an address. A banned addresses will not be invoked upon
    /// with message calls.
    /// @param _addr The address to ban or unban.
    /// @param _ban True if ban, false if unban.
    function banAddress(
        address _addr,
        bool _ban
    )
        external
        onlyFromOwnerOrNamed("bridge_watchdog")
        nonReentrant
    {
        if (_addr == address(0)) revert B_INVALID_USER();
        if (addressBanned[_addr] == _ban) revert B_INVALID_STATUS();
        addressBanned[_addr] = _ban;
        emit AddressBanned(_addr, _ban);
    }
```