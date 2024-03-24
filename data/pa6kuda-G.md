## [GAS-01] Reduce gas usage by caching `hopProofs.length` in `SignalService.proveSignalReceived()`.

## Relevant GitHub Links

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L83-L134

## Recommended Mitigation Steps

```diff
@@ -92,7 +92,9 @@ contract SignalService is EssentialContract, ISignalService {
         nonZeroValue(_signal)
     {
         HopProof[] memory hopProofs = abi.decode(_proof, (HopProof[]));
-        if (hopProofs.length == 0) revert SS_EMPTY_PROOF();
+        uint256 hopProofsLength = hopProofs.length;
+
+        if (hopProofsLength == 0) revert SS_EMPTY_PROOF();

         uint64 chainId = _chainId;
         address app = _app;
@@ -101,11 +103,11 @@ contract SignalService is EssentialContract, ISignalService {
         address signalService = resolve(chainId, "signal_service", false);

         HopProof memory hop;
-        for (uint256 i; i < hopProofs.length; ++i) {
+        for (uint256 i; i < hopProofsLength; ++i) {
             hop = hopProofs[i];

             bytes32 signalRoot = _verifyHopProof(chainId, app, signal, value, hop, signalService);
-            bool isLastHop = i == hopProofs.length - 1;
+            bool isLastHop = i == hopProofsLength - 1;

             if (isLastHop) {
                 if (hop.chainId != block.chainid) revert SS_INVALID_LAST_HOP_CHAINID();
```

## [GAS-02] Reduce gas usage by caching `_instances.length` in `SignalService._addInstances()`.

## Relevant GitHub Links

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L195-L224

## Recommended Mitigation Steps

```diff
@@ -199,7 +199,8 @@ contract SgxVerifier is EssentialContract, IVerifier {
         private
         returns (uint256[] memory ids)
     {
-        ids = new uint256[](_instances.length);
+        uint256 _instancesLength = _instances.length;
+        ids = new uint256[](_instancesLength);

         uint64 validSince = uint64(block.timestamp);

@@ -207,7 +208,7 @@ contract SgxVerifier is EssentialContract, IVerifier {
             validSince += INSTANCE_VALIDITY_DELAY;
         }

-        for (uint256 i; i < _instances.length; ++i) {
+        for (uint256 i; i < _instancesLength; ++i) {
             if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();

             addressRegistered[_instances[i]] = true;
```

## [GAS-03] Unnesessary calculation in `TaikoL2.init()` function.

## Relevant GitHub Links

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L71-L98

## Summary

`TaikoL2.init()` calculates parentHeight and then sets it to `l2Hashes` mapping its blockchash, but because there is condition `block.number == 1` operation `block.number - 1` will always be **0**.

## Recommended Mitigation Steps

```diff
@@ -87,7 +87,7 @@ contract TaikoL2 is CrossChainOwned {
             // This is the case in real L2 genesis
         } else if (block.number == 1) {
             // This is the case in tests
-            uint256 parentHeight = block.number - 1;
+            uint256 parentHeight;
             l2Hashes[parentHeight] = blockhash(parentHeight);
         } else {
             revert L2_TOO_LATE();
```
