
## Title: Re-entrancy issue at `TaikoL2::Anchor`

## Impact

TaikoL2 contract plays a crucial role in anchoring L1 block details to L2, managing EIP-1559 gas pricing, and facilitating cross-layer communication in the Taiko Layer 2 system. The contract has non-reentrancy measure, such as nonReentrant modifier implemented for the `TaikoL2::Anchor` function. However, it is not adhering to the reentrancy guard "checks-effects-interactions" pattern best practice, where the necessary state variables are updated before the external calls are made.

The following state variable update in the `TaikoL2::anchor` function is not adhering to the “checks-effects-interactions" pattern best practice:
```javascript
lastSyncedBlock = _l1BlockId;
```
## Links to affected code

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L107

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L148C13-L148C27

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L154


## Recommendation

Ensure that any state changes or updates to the contract's storage are performed before making external calls. The anchor function state variable `lastSyncedBlock` should be written before the external call to `ISignalService`.
