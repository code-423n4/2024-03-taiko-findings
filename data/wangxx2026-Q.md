## L-01 __gap should be defined as an array of length 44
In style_code you can see that for scalability, 50 slots are used uniformly
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/SOLIDITY_STYLE_GUIDE.md?plain=1#L30-L33
```
To ensure upgradeability and prevent storage collisions in future contract versions, reserve a fixed number of storage slots at the end of each contract. This is achieved by declaring a placeholder array in the contract's storage layout as follows:
   // Reserve 50 storage slots for future use to ensure contract upgradeability.
uint256[50] private __gap;

```
The problem occurs in the following slot calculation method.
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L37-L38
```solidity
    /// @dev Slots 3, 4, and 5.
    Context private __ctx;
```
The Context type occupies 2 slots, but is incorrectly counted as 3 slots.
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/IBridge.sol#L60-L64
```solidity
    struct Context {
        bytes32 msgHash; // Message hash. @audit slot 1
        address from; // Sender's address. @audit 160 bit
        uint64 srcChainId; // Source chain ID. @audit 64 bit
    }
```
One slot can hold 256 bits. The from and srcChainId can be placed in the same slot.
The following code should be changed to:
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L48
```diff
-- uint256[43] private __gap;
++ uint256[44] private __gap;
```


