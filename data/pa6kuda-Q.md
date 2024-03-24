## [QA-01] `BridgedERC1155` tokens without name/symbol can confuse users as they will have same name/symbol.

## Relevant GitHub Links

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L50-L51

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L115-L117

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L28-L37

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L121-L123

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L39-L41

## Summary

As described in `BridgedERC1155.init()` function

> The symbol and the name can be empty for ERC1155 tokens so we use some placeholder data for them instead.

But these placeholders are the same and they aren't used to override name/sybmol if either of them is not provided. That means functions `BridgedERC1155.name()` and `BridgedERC1155.symbol()` will return the same data for other `BridgedERC1155` that don't have names and/or symbols which can confuse users, especially on some NFT marketplace.

## Recommended Mitigation Steps

Add some default name that will not confuse user, or add and display a unique id for every deployed `ERC1155` when calling `ERC1155Vault._handleMessage()`.

## [QA-02] Use existing `_inNonReentrant()` function in `EssentialContract.nonReentrant()` modifier.

## Relevant GitHub Links

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L46-L51

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L140-L142

## Summary

`EssentialContract` already have function that checks it reentry slot has value of _TRUE or _FALSE, so there is no need to recreate the same logic in `EssentialContract.nonReentrant()` modifier.

## Recommended Mitigation Steps

Use `EssentialContract._inNonReentrant()` instead of `_loadReentryLock() == _TRUE`

```diff
     modifier nonReentrant() {
-        if (_loadReentryLock() == _TRUE) revert REENTRANT_CALL();
+        if (_inNonReentrant()) revert REENTRANT_CALL();
         _storeReentryLock(_TRUE);
         _;
         _storeReentryLock(_FALSE);
     }
```

## [QA-03] Rename `TimelockTokenPool.getMyGrant()` and `TimelockTokenPool.getMyGrantSummary()` functions as they don't correspond to their's actions.

## Relevant GitHub Links

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L204-L206

## Summary

Function `TimelockTokenPool.getMyGrant()` have name that doesn't correspond to its actions, because it doesn't get message sender's grant, instead, it gets grant of the passed address. Same with `TimelockTokenPool.getMyGrantSummary()`.

## Recommended Mitigation Steps

Rename `TimelockTokenPool.getMyGrant()` on, for example, `getGrant` and `TimelockTokenPool.getMyGrantSummary()` on, for example, `getGrantSummary`:

```diff
-    function getMyGrant(address _recipient) public view returns (Grant memory) {
+    function getGrant(address _recipient) public view returns (Grant memory) {
         return recipients[_recipient].grant;
     }
```

## [QA-04] Use existing `whenNotPaused` modifier in `BridgedERC721._beforeTokenTransfer()`

## Relevant GitHub Links

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L115-L128

## Summary

`EssentialContract` that is the parent of `BridgedERC721` and `BridgedERC1155` contracts already have `whenNotPaused` modifier that should be used instead of `if (paused()) revert INVALID_PAUSE_STATUS();` as it's just a redundant code.

## Recommended Mitigation Steps

```diff
    function _beforeTokenTransfer(
        address, /*_from*/
        address _to,
        uint256, /*_firstTokenId*/
        uint256 /*_batchSize*/
    )
         internal
         virtual
         override
+        whenNotPaused
     {
         if (_to == address(this)) revert BTOKEN_CANNOT_RECEIVE();
-        if (paused()) revert INVALID_PAUSE_STATUS();
     }
    }
```

## [QA-05] Create function in `BaseVault` contract that returns destination owner.

## Relevant GitHub Links

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L227

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L50

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L64

## Summary

Code part `_op.destOwner != address(0) ? _op.destOwner : msg.sender` is used in multiple places, in that case, it should be separated into function.

## Recommended Mitigation Steps

Create a separate function in `BaseVault` contract

```diff
+    /// @notice Get's address of destination owner
+    /// @param _destOwner The address that can be address(0)
+    /// @return _destOwner if destOwner is not address(0), in other case msg.sender
+    function getDestinationOwner(address _destOwner) internal view returns (address) {
+        return _destOwner != address(0) ? _destOwner : msg.sender;
+    }
```