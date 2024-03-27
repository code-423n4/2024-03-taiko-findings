# Summary

| Risk | Title |
| --- | --- |
| L-1 | Event not emitted when message status is changed to `RECALLED` | 
| L-2 | Replay signature in function `withdraw()` |
| L-3 | At `block.timestamp = claimEnd`, users can claim and withdraw at the same time |


# L-1. Event not emitted when message status is changed to `RECALLED`

https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L191

## Detail
When a message status is changed, the function `_updateMessageStatus()` is called to update the value and also emit an event. 

However, when the status is changed to `RECALLED`, `messageStatus[msgHash]` is updated directly without calling `_updateMessageStatus()`. As the result, the event `MessageStatusChanged` is forgot to emit.

---

# L-2. Replay signature in function `withdraw()`

https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L170

## Detail
The hash in the `withdraw()` does not include any information about chainId, nonce, contract address. As the result, the same signature could be reused in different transactions.
```solidity
function withdraw(address _to, bytes memory _sig) external {
    if (_to == address(0)) revert INVALID_PARAM();
    bytes32 hash = keccak256(abi.encodePacked("Withdraw unlocked Taiko token to: ", _to)); // @audit replay signature
    address recipient = ECDSA.recover(hash, _sig);
    _withdraw(recipient, _to);
}
```

---

# L-3. Changing the threshold could lead to trove liquidation

https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L40

## Details
In the ERC20Airdrop2 contract, there are 2 separated period, which are the claiming period and the withdrawal period. The claiming period will end at `claimEnd` while the withdrawal period will start from `claimEnd` and end at `claimEnd + withdrawalWindow`. 
```solidity
modifier ongoingWithdrawals() {
    if (claimEnd > block.timestamp || claimEnd + withdrawalWindow < block.timestamp) { // @audit at block.timestamp = claimEnd, can claim and withdraw at the same time
        revert WITHDRAWALS_NOT_ONGOING();
    }
    _;
}
```

However currently, if `block.timestamp == claimEnd`, both periods are valid at the same time. As the result, users could claim and withdraw at the same timestamp/block.

---
