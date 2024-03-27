**TAIKO GAS OPTIMIZATION REPORT**
INTRODUCTION
Highlighted below are optimizations exclusively targeting state-mutating functions and view/pure functions invoked by state-mutating functions. In the discussion that follows, only runtime gas is emphasized, given its inevitable dominance over deployment gas costs throughout the protocol's lifetime.

Please be aware that some code snippets may be shortened to conserve space, and certain code snippets may include @audit tags in comments to facilitate issue explanations."

## Gas Optimizations


1. [Reorder struct variables and pack them together to save storage slots+(Gas Saved ~ 8000 Gas)](#g-01-reorder-struct-variables-and-pack-them-together-to-save-storage-slotsgas-saved--8000-gas)
2. [Re-arrange state variable order to save storage slots (Saves ~4000 Gas)](#g-02-re-arrange-state-variable-order-to-save-storage-slots-saves-4000-gas)
3. [State variables can be packed by truncating timestamp(Gas Saved ~6000 GAS)](#g-03-state-variables-can-be-packed-by-truncating-timestampgas-saved-6000-gas)
4. [Cache state variable in stack variable when its come to use multiple time in function](#g-04-cache-state-variable-in-stack-variable-when-its-come-to-use-multiple-time-in-function)
5. [Using storage instead of memory for struct saves gas](#g-05-using-storage-instead-of-memory-for-struct-saves-gas)
6. [Cache variable in memory instead of state variable while emiting events](#g-06-cache-variable-in-memory-instead-of-state-variable-while-emiting-events)
7. [cache variable in local varibale reduce gas costs by minimizing redundant accesses to the array](#g-07-cache-variable-in-local-varibale-reduce-gas-costs-by-minimizing-redundant-accesses-to-the-array)
8. [No need to cache when used only once through out function](#g-08-no-need-to-cache-when-used-only-once-through-out-function)
9. [Caching the length of an array in a local variable can save gas ](#g-09-caching-the-length-of-an-array-in-a-local-variable-can-save-gas)
10. [use assembly for call can save compared to the higher level call](#g-10-use-assembly-for-call-can-save-compared-to-the-higher-level-call)
11. [Cache address(this).balance in local variable instead of fetching repeatedly](#g-11-cache-addressthisbalance-in-local-variable-instead-of-fetching-repeatedly)
12. [unchecked loop increments no valid in solidity > v0.8.22](#g-12-unchecked-loop-increments-no-valid-in-solidity--v0822)
13. [uint256 variable initialization to default value of 0 can be omitted](#g-13-uint256-variable-initialization-to-default-value-of-0-can-be-omitted)
14. [check zero amount for burn and mint](#g-14-check-zero-amount-for-burn-and-mint)
15. [Use require instead of assert because it consumes all remaining gas when it fails](#g-15-use-require-instead-of-assert-because-it-consumes-all-remaining-gas-when-it-fails)
16. [Do not cache global variable in local variable](#g-16-do-not-cache-global-variable-in-local-variable)
17. [`abi.encode` is more efficient than `abi.encodePacked`](#g-17-abiencode-is-more-efficient-than-abiencodepacked)
18. [Use assembly to emit events](#g-18-use-assembly-to-emit-events)
19. [Use assembly for small keccak256 hashes, in order to save gas](#g-19-use-assembly-for-small-keccak256-hashes-in-order-to-save-gas)
20. [Redundant event fields can be removed ](#g-20-redundant-event-fields-can-be-removed)
21. [ Use of emit inside a loop](#g-21-use-of-emit-inside-a-loop)
22. [ >=/ <= costs less gas than >/<](#g-22---costs-less-gas-than)
23. [ Use hardcode address instead of address(this) ](#g-23-use-hardcode-address-instead-of-addressthis)
24. [Long revert strings](#g-24-long-revert-strings)
25. [Constructors can be marked payable](#g-25-constructors-can-be-marked-payable)
26. [Usage of smaller uint/int types causes overhead](#g-26-usage-of-smaller-uintint-types-causes-overhead)
  
## Note: Sorted by gas savings, I have placed the findings with the greatest impact at the top of this report

## [G-01] Reorder struct variables and pack them together to save storage slots+(Gas Saved ~ 8000 Gas)

### Details
In first instances  `Config` we can re-arrange `blockSyncThreshold` struct variable save 1 slot.In second instances  `BlockParams` we can re-arrange `extraData` and `blobHash` struct variable save 1 slot.In third instances  `BlockParams` we can re-arrange `blobUsed` and `id` struct variable save 1 slot.
In third instances  `validityBond` we can re-arrange `blockSyncThreshold` struct variable save 1 slot.

In total we can save 4 slot 
### Proof of Code
- [L1/TaikoData.sol](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L10C1-L135C1)
```solidity
    struct Config {
        // ---------------------------------------------------------------------
        // Group 1: General configs
        // ---------------------------------------------------------------------
        // The chain ID of the network where Taiko contracts are deployed.
        uint64 chainId;
        // ---------------------------------------------------------------------
        // Group 2: Block level configs
        // ---------------------------------------------------------------------
        // The maximum number of proposals allowed in a single block.
        uint64 blockMaxProposals;
        // Size of the block ring buffer, allowing extra space for proposals.
        uint64 blockRingBufferSize;
        // The maximum number of verifications allowed when a block is proposed.
        uint64 maxBlocksToVerifyPerProposal;
        // The maximum gas limit allowed for a block.
        uint32 blockMaxGasLimit;
        // The maximum allowed bytes for the proposed transaction list calldata.
        uint24 blockMaxTxListBytes;
        // The max period in seconds that a blob can be reused for DA.
        uint24 blobExpiry;
        // True if EIP-4844 is enabled for DA
        bool blobAllowedForDA;
        // True if blob can be reused
        bool blobReuseEnabled;
        // ---------------------------------------------------------------------
        // Group 3: Proof related configs
        // ---------------------------------------------------------------------
        // The amount of Taiko token as a prover liveness bond
        uint96 livenessBond;
        // ---------------------------------------------------------------------
        // Group 4: ETH deposit related configs
        // ---------------------------------------------------------------------
        // The size of the ETH deposit ring buffer.
        uint256 ethDepositRingBufferSize;
        // The minimum number of ETH deposits allowed per block.
        uint64 ethDepositMinCountPerBlock;
        // The maximum number of ETH deposits allowed per block.
        uint64 ethDepositMaxCountPerBlock;
        // The minimum amount of ETH required for a deposit.
        uint96 ethDepositMinAmount;
        // The maximum amount of ETH allowed for a deposit.
        uint96 ethDepositMaxAmount;
        // The gas cost for processing an ETH deposit.
        uint256 ethDepositGas;
        // The maximum fee allowed for an ETH deposit.
        uint256 ethDepositMaxFee;
        // The max number of L2 blocks that can stay unsynced on L1 (a value of zero disables
        // syncing)
        uint8 blockSyncThreshold; //@audit reorder this variable
    }

78: struct BlockParams {
        address assignedProver;
        address coinbase;
        bytes32 extraData; //@audit reorder variable
        bytes32 blobHash;
        uint24 txListByteOffset;
        uint24 txListByteSize;
        bool cacheBlobForReuse;
        bytes32 parentMetaHash;
        HookCall[] hookCalls;
    }

94:  struct BlockMetadata {
        bytes32 l1Hash; // slot 1
        bytes32 difficulty; // slot 2
        bytes32 blobHash; //or txListHash (if Blob not yet supported), // slot 3
        bytes32 extraData; // slot 4
        bytes32 depositsHash; // slot 5
        address coinbase; // L2 coinbase, // slot 6
        uint64 id;
        uint32 gasLimit;
        uint64 timestamp; // slot 7
        uint64 l1Height;
        uint24 txListByteOffset;
        uint24 txListByteSize;
        uint16 minTier;
        bool blobUsed; //@audit reorder variable
        bytes32 parentMetaHash; // slot 8
    }

```
### Optimized code:

```diff
diff --git a/packages/protocol/contracts/L1/TaikoData.sol b/packages/protocol/contracts/L1/TaikoData.sol
index 0b5513e..bb2ca72 100644
--- a/packages/protocol/contracts/L1/TaikoData.sol
+++ b/packages/protocol/contracts/L1/TaikoData.sol
@@ -47,6 +47,9 @@ library TaikoData {
         // The maximum number of ETH deposits allowed per block.
         uint64 ethDepositMaxCountPerBlock;
         // The minimum amount of ETH required for a deposit.
+        // The max number of L2 blocks that can stay unsynced on L1 (a value of zero disables
+        // syncing)
+        uint8 blockSyncThreshold;
         uint96 ethDepositMinAmount;
         // The maximum amount of ETH allowed for a deposit.
         uint96 ethDepositMaxAmount;
@@ -54,9 +57,7 @@ library TaikoData {
         uint256 ethDepositGas;
         // The maximum fee allowed for an ETH deposit.
         uint256 ethDepositMaxFee;
-        // The max number of L2 blocks that can stay unsynced on L1 (a value of zero disables
-        // syncing)
-        uint8 blockSyncThreshold;
+
     }
 
     /// @dev Struct representing prover assignment
@@ -78,11 +79,11 @@ library TaikoData {
     struct BlockParams {
         address assignedProver;
         address coinbase;
-        bytes32 extraData;
-        bytes32 blobHash;
         uint24 txListByteOffset;
         uint24 txListByteSize;
         bool cacheBlobForReuse;
+        bytes32 extraData;
+        bytes32 blobHash;
         bytes32 parentMetaHash;
         HookCall[] hookCalls;
     }
@@ -98,14 +99,14 @@ library TaikoData {
         bytes32 extraData; // slot 4
         bytes32 depositsHash; // slot 5
         address coinbase; // L2 coinbase, // slot 6
-        uint64 id;
         uint32 gasLimit;
+        bool blobUsed;
+        uint64 id;
         uint64 timestamp; // slot 7
         uint64 l1Height;
         uint24 txListByteOffset;
         uint24 txListByteSize;
         uint16 minTier;
-        bool blobUsed;
         bytes32 parentMetaHash; // slot 8
     }
 
@@ -124,8 +125,8 @@ library TaikoData {
         bytes32 blockHash; // slot 2
         bytes32 stateRoot; // slot 3
         address prover; // slot 4
-        uint96 validityBond;
         address contester; // slot 5
+        uint96 validityBond;
         uint96 contestBond;
         uint64 timestamp; // slot 6 (90 bits)
         uint16 tier;
```

## [G-02] Re-arrange state variable order to save storage slots (Saves ~4000 Gas)
### Details
re-arrange the order of `_FALSE` and `_TRUE` to save 1 storage slot (~2000 Gas) pack with `__reentry`, `__paused`
### Proof of Code
- [EssentialContract.sol#L11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L11C3-L23C28)
```solidity
File: packages/protocol/contracts/common/EssentialContract.sol
11: uint8 private constant _FALSE = 1;

    uint8 private constant _TRUE = 2; //@audit pack

    /// @dev The slot in transient storage of the reentry lock. This is the keccak256 hash
    /// of "ownerUUPS.reentry_slot"
    bytes32 private constant _REENTRY_SLOT =
        0xa5054f728453d3dbe953bdc43e4d0cb97e662ea32d7958190f3dc2da31d9721a;

    /// @dev Slot 1.
    uint8 private __reentry;

    uint8 private __paused;
```
### Optimized code:

```diff
diff --git a/packages/protocol/contracts/common/EssentialContract.sol b/packages/protocol/contracts/common/EssentialContract.sol
index 3f27aa4..92f73c5 100644
--- a/packages/protocol/contracts/common/EssentialContract.sol
+++ b/packages/protocol/contracts/common/EssentialContract.sol
@@ -10,7 +10,11 @@ import "./AddressResolver.sol";
 abstract contract EssentialContract is UUPSUpgradeable, Ownable2StepUpgradeable, AddressResolver {
     uint8 private constant _FALSE = 1;
 
-    uint8 private constant _TRUE = 2;
+    uint8 private constant _TRUE = 2; 
+    
+    uint8 private __reentry;
+
+    uint8 private __paused;
 
     /// @dev The slot in transient storage of the reentry lock. This is the keccak256 hash
     /// of "ownerUUPS.reentry_slot"
@@ -18,9 +22,6 @@ abstract contract EssentialContract is UUPSUpgradeable, Ownable2StepUpgradeable,
         0xa5054f728453d3dbe953bdc43e4d0cb97e662ea32d7958190f3dc2da31d9721a;
 
     /// @dev Slot 1.
-    uint8 private __reentry;
-
-    uint8 private __paused;
 
     uint256[49] private __gap;
```
### Instances - 2
re-arrange the order of `INVALID_EXIT_CODE` and `_checkLocalEnclaveReport` to save 1 storage slot (~2000 Gas) pack with `owner`
### Proof of Code
- [AutomataDcapV3Attestation.sol#L35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L35C1-L38C43)
```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol
36:    uint8 internal constant INVALID_EXIT_CODE = 255; //@audit pack with address

38:    bool private _checkLocalEnclaveReport;
```
### Optimized code:

```diff
diff --git a/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol b/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol
index 9ec78e6..20737db 100644
--- a/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol
+++ b/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol
@@ -33,9 +33,6 @@ contract AutomataDcapV3Attestation is IAttestation {
     bytes32 internal constant ROOTCA_PUBKEY_HASH =
         0x89f72d7c488e5b53a77c23ebcb36970ef7eb5bcf6658e9b8292cfbe4703a8473;
 
-    uint8 internal constant INVALID_EXIT_CODE = 255;
-
-    bool private _checkLocalEnclaveReport;
     mapping(bytes32 enclave => bool trusted) private _trustedUserMrEnclave;
     mapping(bytes32 signer => bool trusted) private _trustedUserMrSigner;
 
@@ -50,7 +47,10 @@ contract AutomataDcapV3Attestation is IAttestation {
     EnclaveIdStruct.EnclaveId public qeIdentity;
 
     address public owner;
+    
+    uint8 internal constant INVALID_EXIT_CODE = 255;
 
+    bool private _checkLocalEnclaveReport;
     constructor(address sigVerifyLibAddr, address pemCertLibAddr) {
         sigVerifyLib = ISigVerifyLib(sigVerifyLibAddr);
         pemCertLib = PEMCertChainLib(pemCertLibAddr);
```
## [G-03] State variables can be packed by truncating timestamp(Gas Saved ~6000 GAS)
### Details
The EVM works with 32 byte words. Variables less than 32 bytes can be declared next to each other in storage and this will pack the values together into a single 32 byte storage slot (if values combined are <= 32 bytes). If the variables packed together are retrieved together in functions (more likely with structs), we will effectively save ~2000 gas with every subsequent SLOAD for that storage slot. This is due to us incurring a Gwarmaccess (100 gas) versus a Gcoldsload (2100 gas).

Here we can reduce size of `TREE_RADIX` `BRANCH_NODE_LENGTH` `LEAF_OR_EXTENSION_NODE_LENGTH` these variable are constant so we can assign uint8 and save three slot
### Proof of Code
- [MerkleTrie.sol#L21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L21C4-L28C1)
```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol
21:  uint256 internal constant TREE_RADIX = 16; //@audit tight pack

    /// @notice Branch nodes have TREE_RADIX elements and one value element.
    uint256 internal constant BRANCH_NODE_LENGTH = TREE_RADIX + 1;

    /// @notice Leaf nodes and extension nodes have two elements, a `path` and a `value`.
    uint256 internal constant LEAF_OR_EXTENSION_NODE_LENGTH = 2;

```
### Optimized code:

```diff
diff --git a/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol b/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol
index f961c59..8aa3b97 100644
--- a/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol
+++ b/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol
@@ -18,13 +18,13 @@ library MerkleTrie {
     }
 
     /// @notice Determines the number of elements per branch node.
-    uint256 internal constant TREE_RADIX = 16;
+    uint8 internal constant TREE_RADIX = 16;
 
     /// @notice Branch nodes have TREE_RADIX elements and one value element.
-    uint256 internal constant BRANCH_NODE_LENGTH = TREE_RADIX + 1;
+    uint8 internal constant BRANCH_NODE_LENGTH = TREE_RADIX + 1;
 
     /// @notice Leaf nodes and extension nodes have two elements, a `path` and a `value`.
-    uint256 internal constant LEAF_OR_EXTENSION_NODE_LENGTH = 2;
+    uint8 internal constant LEAF_OR_EXTENSION_NODE_LENGTH = 2;
 
     /// @notice Prefix for even-nibbled extension node paths.
     uint8 internal constant PREFIX_EXTENSION_EVEN = 0;
```
## [G-04] Cache state variable in stack variable when its come to use multiple time in function

### Details
cache `gasExcess` in local variable as a `uint256 _gasExcess = gasExcess;`
### Proof of Code
- [TaikoL2.sol#L274](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L274C11-L292C15)
```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol
253: function _calc1559BaseFee(
        Config memory _config,
        uint64 _l1BlockId,
        uint32 _parentGasUsed
    )
        private
        view
        returns (uint256 basefee_, uint64 gasExcess_)
    {
        // gasExcess being 0 indicate the dynamic 1559 base fee is disabled.
        if (gasExcess > 0) {
            // We always add the gas used by parent block to the gas excess
            // value as this has already happened
            uint256 excess = uint256(gasExcess) + _parentGasUsed; //@audit cache gasExcess

            // Calculate how much more gas to issue to offset gas excess.
            // after each L1 block time, config.gasTarget more gas is issued,
            // the gas excess will be reduced accordingly.
            // Note that when lastSyncedBlock is zero, we skip this step
            // because that means this is the first time calculating the basefee
            // and the difference between the L1 height would be extremely big,
            // reverting the initial gas excess value back to 0.
            uint256 numL1Blocks;
            if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) { //@audit cache state variable
                numL1Blocks = _l1BlockId - lastSyncedBlock;
            }

```
### Optimized code:
```diff
diff --git a/packages/protocol/contracts/L2/TaikoL2.sol b/packages/protocol/contracts/L2/TaikoL2.sol
index 8ad2c82..0d434b1 100644
--- a/packages/protocol/contracts/L2/TaikoL2.sol
+++ b/packages/protocol/contracts/L2/TaikoL2.sol
@@ -258,11 +259,12 @@ contract TaikoL2 is CrossChainOwned {
         view
         returns (uint256 basefee_, uint64 gasExcess_)
     {
+        uint256 _gasExcess = gasExcess;
         // gasExcess being 0 indicate the dynamic 1559 base fee is disabled.
-        if (gasExcess > 0) {
+        if (_gasExcess > 0) {
             // We always add the gas used by parent block to the gas excess
             // value as this has already happened
-            uint256 excess = uint256(gasExcess) + _parentGasUsed;
+            uint256 excess = uint256(_gasExcess) + _parentGasUsed;
 
             // Calculate how much more gas to issue to offset gas excess.
             // after each L1 block time, config.gasTarget more gas is issued,
@@ -272,8 +274,9 @@ contract TaikoL2 is CrossChainOwned {
             // and the difference between the L1 height would be extremely big,
             // reverting the initial gas excess value back to 0.
             uint256 numL1Blocks;
-            if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {
-                numL1Blocks = _l1BlockId - lastSyncedBlock;
+            uint256 _lastSyncedBlock = lastSyncedBlock;
+            if (_lastSyncedBlock > 0 && _l1BlockId > _lastSyncedBlock) {
+                numL1Blocks = _l1BlockId - _lastSyncedBlock;
             }
 
             if (numL1Blocks > 0) {
```
### Instances - 2
cache `addressManager_` in local variable as a `address addressManager_ = addressManager;`
### Optimized code:
- [AddressResolver.sol#L72](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L72C2-L88C6)
```diff
diff --git a/packages/protocol/contracts/common/AddressResolver.sol b/packages/protocol/contracts/common/AddressResolver.sol
index 122e93f..2fd3786 100644
--- a/packages/protocol/contracts/common/AddressResolver.sol
+++ b/packages/protocol/contracts/common/AddressResolver.sol
@@ -78,9 +78,10 @@ abstract contract AddressResolver is IAddressResolver, Initializable {
         view
         returns (address payable addr_)
     {
-        if (addressManager == address(0)) revert RESOLVER_INVALID_MANAGER();
+        address addressManager_ = addressManager;
+        if (addressManager_ == address(0)) revert RESOLVER_INVALID_MANAGER();
 
-        addr_ = payable(IAddressManager(addressManager).getAddress(_chainId, _name));
+        addr_ = payable(IAddressManager(addressManager_).getAddress(_chainId, _name));
 
         if (!_allowZeroAddress && addr_ == address(0)) {
             revert RESOLVER_ZERO_ADDR(_chainId, _name);
```
### Instances - 3   
cache `sharedVault`
### Optimized code:
- [TimelockTokenPool.sol#L203](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L203C3-L223C6)
```diff
diff --git a/packages/protocol/contracts/team/TimelockTokenPool.sol b/packages/protocol/contracts/team/TimelockTokenPool.sol
index 44850ab..7ee3a16 100644
--- a/packages/protocol/contracts/team/TimelockTokenPool.sol
+++ b/packages/protocol/contracts/team/TimelockTokenPool.sol
@@ -207,6 +207,7 @@ contract TimelockTokenPool is EssentialContract {
 
     function _withdraw(address _recipient, address _to) private {
         Recipient storage r = recipients[_recipient];
+        address _sharedVault = sharedVault;
 
         (,,, uint128 amountToWithdraw, uint128 costToWithdraw) = getMyGrantSummary(_recipient);
 
@@ -216,8 +217,8 @@ contract TimelockTokenPool is EssentialContract {
         totalAmountWithdrawn += amountToWithdraw;
         totalCostPaid += costToWithdraw;
 
-        IERC20(taikoToken).transferFrom(sharedVault, _to, amountToWithdraw);
-        IERC20(costToken).safeTransferFrom(_recipient, sharedVault, costToWithdraw);
+        IERC20(taikoToken).transferFrom(_sharedVault, _to, amountToWithdraw);
+        IERC20(costToken).safeTransferFrom(_recipient, _sharedVault, costToWithdraw);
 
         emit Withdrawn(_recipient, _to, amountToWithdraw, costToWithdraw);
     }
```
### Instances - 4 & 5
cache `migartingAddress`
- [BridgedERC20Base.sol#L57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L57C5-L70C6)
### Optimized code:
```diff
diff --git a/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol b/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol
index 73cb27f..e0fec82 100644
--- a/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol
+++ b/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol
@@ -57,10 +57,10 @@ abstract contract BridgedERC20Base is EssentialContract, IBridgedERC20 {
     function mint(address _account, uint256 _amount) public nonReentrant whenNotPaused {
         // mint is disabled while migrating outbound.
         if (_isMigratingOut()) revert BB_MINT_DISALLOWED();
-
-        if (msg.sender == migratingAddress) {
+        address _migratingAddress = migratingAddress;
+        if (msg.sender == _migratingAddress) {
             // Inbound migration
-            emit MigratedTo(migratingAddress, _account, _amount);
+            emit MigratedTo(_migratingAddress, _account, _amount); //@audit cache migratingAddress
         } else if (msg.sender != resolve("erc20_vault", true)) {
             // Bridging from vault
             revert BB_PERMISSION_DENIED();
@@ -77,9 +77,10 @@ abstract contract BridgedERC20Base is EssentialContract, IBridgedERC20 {
             // Only the owner of the tokens himself can migrate out
             if (msg.sender != _account) revert BB_PERMISSION_DENIED();
             // Outbound migration
-            emit MigratedTo(migratingAddress, _account, _amount);
+            address _migratingAddress = migratingAddress;
+            emit MigratedTo(_migratingAddress, _account, _amount); 
             // Ask the new bridged token to mint token for the user.
-            IBridgedERC20(migratingAddress).mint(_account, _amount);
+            IBridgedERC20(_migratingAddress).mint(_account, _amount);//@audit cache migratingAddress
         } else if (msg.sender != resolve("erc20_vault", true)) {
             // Only the vault can burn tokens when not migrating out
             revert RESOLVER_DENIED();
```
### Instances : 6
cache `nextTxId`
- [CrossChainOwned.sol#L42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L42C5-L55C1)
### Optimized code:

```diff
diff --git a/packages/protocol/contracts/L2/CrossChainOwned.sol b/packages/protocol/contracts/L2/CrossChainOwned.sol
index 8fe36fc..9a41b89 100644
--- a/packages/protocol/contracts/L2/CrossChainOwned.sol
+++ b/packages/protocol/contracts/L2/CrossChainOwned.sol
@@ -39,18 +39,28 @@ abstract contract CrossChainOwned is EssentialContract, IMessageInvocable {
         whenNotPaused
         onlyFromNamed("bridge")
     {
+        uint64 currentTxId = nextTxId;
         (uint64 txId, bytes memory txdata) = abi.decode(_data, (uint64, bytes));
-        if (txId != nextTxId) revert XCO_INVALID_TX_ID();
+        if (txId != currentTxId) revert XCO_INVALID_TX_ID(); //@audit cache nextTxId
 
         IBridge.Context memory ctx = IBridge(msg.sender).context();
         if (ctx.srcChainId != ownerChainId || ctx.from != owner()) {
             revert XCO_PERMISSION_DENIED();
         }
          (bool success,) = address(this).call(txdata);
         if (!success) revert XCO_TX_REVERTED();
 
-        emit TransactionExecuted(nextTxId++, bytes4(txdata));
+        emit TransactionExecuted(currentTxId , bytes4(txdata));
+        nextTxId = currentTxId + 1;
     }
```
### Instances-7
cache `state`
- [TaikoL1.sol#L94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L94)
### Proof of Code

```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol
75: function proveBlock(
        uint64 _blockId,
        bytes calldata _input
    )
        external
        nonReentrant
        whenNotPaused
        whenProvingNotPaused
    {
        (
            TaikoData.BlockMetadata memory meta,
            TaikoData.Transition memory tran,
            TaikoData.TierProof memory proof
        ) = abi.decode(_input, (TaikoData.BlockMetadata, TaikoData.Transition, TaikoData.TierProof));

        if (_blockId != meta.id) revert L1_INVALID_BLOCK_ID();

        TaikoData.Config memory config = getConfig();

        uint8 maxBlocksToVerify = LibProving.proveBlock(state, config, this, meta, tran, proof); //@audit cache state in local variable

        LibVerifying.verifyBlocks(state, config, this, maxBlocksToVerify);
    }
```
### Instances-8
cache `state`
- [TaikoL1.sol#L151](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L151)
### Proof of Code

```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol
145:  function getBlock(uint64 _blockId)
        public
        view
        returns (TaikoData.Block memory blk_, TaikoData.TransitionState memory ts_)
    {
        uint64 slot;
        (blk_, slot) = LibUtils.getBlock(state, getConfig(), _blockId); //@audit cache state in local variable

        if (blk_.verifiedTransitionId != 0) {
            ts_ = state.transitions[slot][blk_.verifiedTransitionId];
        }
    }
```
cache `_state`
### Instances - 9
- [LibDepositing.sol#L138](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L138C8-L143C6)
### Proof of Code
```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol
138:  unchecked {
            return _amount >= _config.ethDepositMinAmount && _amount <= _config.ethDepositMaxAmount
                && _state.slotA.numEthDeposits - _state.slotA.nextEthDepositToProcess
                    < _config.ethDepositRingBufferSize - 1;
        }
```
### Instances -10
cache `state`
- [TaikoL1.sol#L65](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L65C8-L72C6)
### Proof of Code
```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol
55:  function proposeBlock(
        bytes calldata _params,
        bytes calldata _txList
    )
        external
        payable
        nonReentrant
        whenNotPaused
        returns (TaikoData.BlockMetadata memory meta_, TaikoData.EthDeposit[] memory deposits_)
    {
        TaikoData.Config memory config = getConfig();

        (meta_, deposits_) = LibProposing.proposeBlock(state, config, this, _params, _txList); //@audit cache state in local variable

        if (!state.slotB.provingPaused) {
            LibVerifying.verifyBlocks(state, config, this, config.maxBlocksToVerifyPerProposal);
        }
    }
```
## [G-05] Using storage instead of memory for struct saves gas

### Details
We could make the _increaseResonanceFactor() function more gas efficient if we declare the borrowData struct variable as storage rather than memory . In implementing this we would avoid having to copy all the members of BorrowRatesEntry struct from storage to memory which would incur a Gcoldsload (2100 gas) for each storage slot read which totals to 10500 gas units. Declaring the borrowData struct variable as a storage variable would only cost 100 gas units (Gwarmsload) which totals to 300 gas for the members read in the function (deltaPole, pole and maxPole) and members read more than once in the function are cached in stack variable and the stack variable used subsequently. The diff below shows how the code should be refactored:

### Proof of Code
- [SignalService.sol#L94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L94C3-L94C72)
```solidity
File: packages/protocol/contracts/signal/SignalService.sol
83:  function proveSignalReceived(
        uint64 _chainId,
        address _app,
        bytes32 _signal,
        bytes calldata _proof
    )
        public
        virtual
        validSender(_app)
        nonZeroValue(_signal)
    {
        HopProof[] memory hopProofs = abi.decode(_proof, (HopProof[])); //@audit
        if (hopProofs.length == 0) revert SS_EMPTY_PROOF();
```
### Optimized code:

```diff
diff --git a/packages/protocol/contracts/signal/SignalService.sol b/packages/protocol/contracts/signal/SignalService.sol
index 499d496..b91d9e3 100644
--- a/packages/protocol/contracts/signal/SignalService.sol
+++ b/packages/protocol/contracts/signal/SignalService.sol
@@ -91,7 +91,7 @@ contract SignalService is EssentialContract, ISignalService {
         validSender(_app)
         nonZeroValue(_signal)
     {
-        HopProof[] memory hopProofs = abi.decode(_proof, (HopProof[]));
+        HopProof[] storage hopProofs = abi.decode(_proof, (HopProof[]));
         if (hopProofs.length == 0) revert SS_EMPTY_PROOF();
 
         uint64 chainId = _chainId;
```
## [G-06] Cache variable in memory instead of state variable while emiting events

### Details
When emitting events in Solidity, you typically don't need to persist the cached variable across transactions.This can save gas costs because modifying state variables incurs additional costs due to storage writes.

### Proof of Code
- [TaikoL2.sol#L154](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L154C7-L157C55)
```solidity 
File: packages/protocol/contracts/L2/TaikoL2.sol 
154:        l2Hashes[parentId] = blockhash(parentId);
        publicInputHash = publicInputHashNew;

        emit Anchored(blockhash(parentId), gasExcess); //@audit do not emit state 
    }

```
### Optimized code:

```diff
diff --git a/packages/protocol/contracts/L2/TaikoL2.sol b/packages/protocol/contracts/L2/TaikoL2.sol
index 8ad2c82..6b586a6 100644
--- a/packages/protocol/contracts/L2/TaikoL2.sol
+++ b/packages/protocol/contracts/L2/TaikoL2.sol
@@ -133,11 +133,11 @@ contract TaikoL2 is CrossChainOwned {
             revert L2_PUBLIC_INPUT_HASH_MISMATCH();
         }
 
        Config memory config = getConfig();

+        uint64 _gasExcess = gasExcess;
         // Verify the base fee per gas is correct
         uint256 basefee;
-        (basefee, gasExcess) = _calc1559BaseFee(config, _l1BlockId, _parentGasUsed);
+        (basefee, _gasExcess) = _calc1559BaseFee(config, _l1BlockId, _parentGasUsed);
         if (!skipFeeCheck() && block.basefee != basefee) {
             revert L2_BASEFEE_MISMATCH();
         }
@@ -150,11 +150,11 @@ contract TaikoL2 is CrossChainOwned {  
         l2Hashes[parentId] = blockhash(parentId);
         publicInputHash = publicInputHashNew;
 
-        emit Anchored(blockhash(parentId), gasExcess);
+        emit Anchored(blockhash(parentId), _gasExcess); 
     }

```
## [G-07] cache variable in local varibale reduce gas costs by minimizing redundant accesses to the array

### Instances - 1
cache `_tierFees[i]` in local varibale instead avoid fetch repeatly

### Proof of Code
- [AssignmentHook.sol#L172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L172C5-L176C6)
```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol
164: function _getProverFee(
        TaikoData.TierFee[] memory _tierFees,
        uint16 _tierId
    )
        private
        pure
        returns (uint256)
    {
        for (uint256 i; i < _tierFees.length; ++i) {
            if (_tierFees[i].tier == _tierId) return _tierFees[i].fee; //@aydit cache _tierFees[i]
        }
        revert HOOK_TIER_NOT_FOUND();
    }
```
### Optimized code:

```diff
diff --git a/packages/protocol/contracts/L1/hooks/AssignmentHook.sol b/packages/protocol/contracts/L1/hooks/AssignmentHook.sol
index f0cfb26..ef69631 100644
--- a/packages/protocol/contracts/L1/hooks/AssignmentHook.sol
+++ b/packages/protocol/contracts/L1/hooks/AssignmentHook.sol
@@ -170,7 +170,8 @@ contract AssignmentHook is EssentialContract, IHook {
         returns (uint256)
     {
         for (uint256 i; i < _tierFees.length; ++i) {
-            if (_tierFees[i].tier == _tierId) return _tierFees[i].fee;
+            uint256 tierFees = _tierFees[i];
+            if (tierFees.tier == _tierId) return _tierFees.fee;
         }
         revert HOOK_TIER_NOT_FOUND();
     }
```

### Instance -2

Caching deposit[i] can help reduce gas costs by minimizing redundant accesses to the deposits_ array. We can store the deposit[i] value in a local variable within the loop
### Proof of Code
- [LibDepositing.sol#L86](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L86C12-L105C18)
```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol
86:   for (uint256 i; i < deposits_.length;) {
                uint256 data = _state.ethDeposits[j % _config.ethDepositRingBufferSize];
                deposits_[i] = TaikoData.EthDeposit({ //@audit cache deposits_[i]
                    recipient: address(uint160(data >> 96)),
                    amount: uint96(data),
                    id: j
                });
                uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount;

                // Unchecked is safe:
                // - _fee cannot be bigger than deposits_[i].amount
                // - all values are in the same range (uint96) except loop
                // counter, which obviously cannot be bigger than uint95
                // otherwise the function would be gassing out.
                unchecked {
                    deposits_[i].amount -= _fee;
                    totalFee += _fee;
                    ++i;
                    ++j;
                }
```
### Optimized code:

```diff
diff --git a/packages/protocol/contracts/L1/libs/LibDepositing.sol b/packages/protocol/contracts/L1/libs/LibDepositing.sol
index 1d4c9fc..011696a 100644
--- a/packages/protocol/contracts/L1/libs/LibDepositing.sol
+++ b/packages/protocol/contracts/L1/libs/LibDepositing.sol
@@ -85,12 +85,12 @@ library LibDepositing {
             uint96 totalFee;
             for (uint256 i; i < deposits_.length;) {
                 uint256 data = _state.ethDeposits[j % _config.ethDepositRingBufferSize];
-                deposits_[i] = TaikoData.EthDeposit({
                 TaikoData.EthDeposit memory deposit  = TaikoData.EthDeposit({
                     recipient: address(uint160(data >> 96)),
                     amount: uint96(data),
                     id: j
                 });
-                uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount;
+                uint96 _fee = deposit.amount > fee ? fee : deposit.amount;
 
                 // Unchecked is safe:
                 // - _fee cannot be bigger than deposits_[i].amount
@@ -98,9 +98,10 @@ library LibDepositing {
                 // counter, which obviously cannot be bigger than uint95
                 // otherwise the function would be gassing out.
                 unchecked {
-                    deposits_[i].amount -= _fee;
+                    deposit.amount -= _fee;
                     totalFee += _fee;
                     ++i;
+                    deposits_[i] = deposit;
                     ++j;
                 }
             }
```
### Instances - 3
Caching certs[i] can help reduce gas costs by minimizing redundant accesses to the certs array. We can store the certs[i] value in a local variable within the loop
- [AutomataDcapV3Attestation.sol#L259](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L259C7-L278C1)
### Proof of Code
```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol
248: function _verifyCertChain(IPEMCertChainLib.ECSha256Certificate[] memory certs)
        private
        view
        returns (bool)
    {
        for (uint256 i; i < n; ++i) {
            IPEMCertChainLib.ECSha256Certificate memory issuer;
            if (i == n - 1) {
                // rootCA
                issuer = certs[i];
            } else {
                issuer = certs[i + 1];
                if (i == n - 2) {
                    // this cert is expected to be signed by the root
                    certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.ROOT)][certs[i] //@audit cache cert[i]
                        .serialNumber];
                } else if (certs[i].isPck) {
                    certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.PCK)][certs[i]
                        .serialNumber];
                }
                if (certRevoked) {
                    break;
                }
            }

            certNotExpired =
                block.timestamp > certs[i].notBefore && block.timestamp < certs[i].notAfter;
            if (!certNotExpired) {
                break;
```
### Insatnces - 4
Caching hookCalls[i] can help reduce gas costs by minimizing redundant accesses to the hookCalls[i] array. We can store the hookCalls[i] value in a local variable within the loop
### Proof of Code
- [LibProposing.sol#L243](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L243C11-L262C14)
```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol
244:  for (uint256 i; i < params.hookCalls.length; ++i) {
                if (uint160(prevHook) >= uint160(params.hookCalls[i].hook)) {
                    revert L1_INVALID_HOOK();
                }

                // When a hook is called, all ether in this contract will be send to the hook.
                // If the ether sent to the hook is not used entirely, the hook shall send the Ether
                // back to this contract for the next hook to use.
                // Proposers shall choose use extra hooks wisely.
                IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }(
                    blk, meta_, params.hookCalls[i].data
                );

                prevHook = params.hookCalls[i].hook;
            }
```
### Instances -5
Caching _proof[i] can help reduce gas costs by minimizing redundant accesses to the _proof[i] array. We can store the _proof[i] value in a local variable within the loop
### Proof of Code
- [MerkleTrie.sol#L205](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L205C4-L214C6)
```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol
205: function _parseProof(bytes[] memory _proof) private pure returns (TrieNode[] memory proof_) {
        uint256 length = _proof.length;
        proof_ = new TrieNode[](length);
        for (uint256 i = 0; i < length;) {
            proof_[i] = TrieNode({ encoded: _proof[i], decoded: RLPReader.readList(_proof[i]) });//@audit cache _proof[i]
            unchecked {
                ++i;
            }
        }
    }
```
## [G-08] No need to cache when used only once through out function

### Details
Caching a variable in memory is useful when you need to access it multiple times within a function.If varibale use once then directly accessing the variable or value is more efficient and concise.

### Proof of Code
- [TaikoL2.sol#L136](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L136)
```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol
131:"  (bytes32 publicInputHashOld, bytes32 publicInputHashNew) = _calcPublicInputHash(parentId);
        if (publicInputHash != publicInputHashOld) {
            revert L2_PUBLIC_INPUT_HASH_MISMATCH();
        }

        Config memory config = getConfig(); //@audit no need to cache
        
        // Verify the base fee per gas is correct
```
### Optimized code:

```diff
diff --git a/packages/protocol/contracts/L2/TaikoL2.sol b/packages/protocol/contracts/L2/TaikoL2.sol
index 8ad2c82..931e1a0 100644
--- a/packages/protocol/contracts/L2/TaikoL2.sol
+++ b/packages/protocol/contracts/L2/TaikoL2.sol
@@ -133,11 +133,10 @@ contract TaikoL2 is CrossChainOwned {
             revert L2_PUBLIC_INPUT_HASH_MISMATCH();
         }
 
-        Config memory config = getConfig();
-
+        uint64 _gasExcess = gasExcess;
         // Verify the base fee per gas is correct
         uint256 basefee;
-        (basefee, gasExcess) = _calc1559BaseFee(config, _l1BlockId, _parentGasUsed);
+        (basefee, _gasExcess) = _calc1559BaseFee(getConfig(), _l1BlockId, _parentGasUsed);
         if (!skipFeeCheck() && block.basefee != basefee) {
             revert L2_BASEFEE_MISMATCH();
         }
```

## [G-09] Caching the length of an array in a local variable can save gas 

### Details
In Solidity, accessing the length of an array inside a loop condition or during iteration can result in an SLOAD operation, which consumes gas. By caching the length of the array in a local variable, you avoid this repeated SLOAD operation, potentially saving gas.
### Proof of Code
- [Guardians.sol#L68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L68C7-L73C16)
```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol
63: if (_newGuardians.length < MIN_NUM_GUARDIANS || _newGuardians.length > type(uint8).max) {
            revert INVALID_GUARDIAN_SET();
        }
        // Minimum number of guardians to approve is at least equal or greater than half the
        // guardians (rounded up) and less or equal than the total number of guardians
        if (_minGuardians < (_newGuardians.length + 1) >> 1 || _minGuardians > _newGuardians.length) //@audit length
        {
            revert INVALID_MIN_GUARDIANS();
        }
```
### Optimized code:

```diff
diff --git a/packages/protocol/contracts/L1/provers/Guardians.sol b/packages/protocol/contracts/L1/provers/Guardians.sol
index a4daa55..5acc389 100644
--- a/packages/protocol/contracts/L1/provers/Guardians.sol
+++ b/packages/protocol/contracts/L1/provers/Guardians.sol
@@ -60,12 +60,13 @@ abstract contract Guardians is EssentialContract {
     {
         // We need at least MIN_NUM_GUARDIANS and at most 255 guardians (so the approval bits fit in
         // a uint256)
-        if (_newGuardians.length < MIN_NUM_GUARDIANS || _newGuardians.length > type(uint8).max) {
+        uint256 newguardiansLength = _newGuardians.length;
+        if (newguardiansLength < MIN_NUM_GUARDIANS || newguardiansLength > type(uint8).max) {
             revert INVALID_GUARDIAN_SET();
         }
         // Minimum number of guardians to approve is at least equal or greater than half the
         // guardians (rounded up) and less or equal than the total number of guardians
-        if (_minGuardians < (_newGuardians.length + 1) >> 1 || _minGuardians > _newGuardians.length)
+        if (_minGuardians < (newguardiansLength + 1) >> 1 || _minGuardians > newguardiansLength) //@audit cache length
         {
             revert INVALID_MIN_GUARDIANS();
         }
@@ -77,7 +78,7 @@ abstract contract Guardians is EssentialContract {
         delete guardians;
 
         // Set the new guardians
-        for (uint256 i = 0; i < _newGuardians.length; ++i) {
+        for (uint256 i = 0; i < newguardiansLength; ++i) {
             address guardian = _newGuardians[i];
             if (guardian == address(0)) revert INVALID_GUARDIAN();
             // This makes sure there are not duplicate addresses
```
### Instances - 2
- [MerkleTrie.sol#L84](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L84C6-L108C19)
### Proof of Code
```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol
68: function get(
        bytes memory _key,
        bytes[] memory _proof,
        bytes32 _root
    )
        internal
        pure
        returns (bytes memory value_)
    {
        require(_key.length > 0, "MerkleTrie: empty key"); //@audit cache length in local variable
```
### Optimized code:

```diff
diff --git a/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol b/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol
index f961c59..23f42ff 100644
--- a/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol
+++ b/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol
@@ -74,19 +74,20 @@ library MerkleTrie {
         pure
         returns (bytes memory value_)
     {
-        require(_key.length > 0, "MerkleTrie: empty key");
+        uint256 keylength = _key.length;
+        require(keylength > 0, "MerkleTrie: empty key"); //@audit 
 
         TrieNode[] memory proof = _parseProof(_proof);
         bytes memory key = Bytes.toNibbles(_key);
         bytes memory currentNodeID = abi.encodePacked(_root);
        uint256 currentKeyIndex = 0;  
 
         // Proof is top-down, so we start at the first element (root).
         for (uint256 i = 0; i < proof.length; i++) {
             TrieNode memory currentNode = proof[i];
 
             // Key index should never exceed total key length or we'll be out of bounds.
-            require(currentKeyIndex <= key.length, "MerkleTrie: key index exceeds total key length");
+            require(currentKeyIndex <= keylength, "MerkleTrie: key index exceeds total key length");
 
             if (currentKeyIndex == 0) {
                 // First proof element is always the root node.
@@ -109,7 +110,7 @@ library MerkleTrie {
             }
 
             if (currentNode.decoded.length == BRANCH_NODE_LENGTH) {
-                if (currentKeyIndex == key.length) {
+                if (currentKeyIndex == keylength) {
                     // Value is the last element of the decoded list (for branch nodes). There's
                     // some ambiguity in the Merkle trie specification because bytes(0) is a
                     // valid value to place into the trie, but for branch nodes bytes(0) can exist
```
### Instances - 3
- [Bytes.sol#L91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L91C5-L97C1) 
### Proof of Code
```solidity
File: packages/protocol/contracts/thirdparty/optimism/Bytes.sol
91:   function slice(bytes memory _bytes, uint256 _start) internal pure returns (bytes memory) {
        if (_start >= _bytes.length) { //@audit cache length
            return bytes("");
        }   
        return slice(_bytes, _start, _bytes.length - _start); //second access
    }
```
### Instances - 4
- [MerkleTrie.sol#L89C](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L89C13-L107C34)
### Proof of Code
```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol
68: function get(
        bytes memory _key,
        bytes[] memory _proof,
        bytes32 _root
    )
        internal
        pure
        returns (bytes memory value_)
    {
@>        require(_key.length > 0, "MerkleTrie: empty key"); //@audit cache _key.length
...        
            // Key index should never exceed total key length or we'll be out of bounds.
@>            require(currentKeyIndex <= key.length, "MerkleTrie: key index exceeds total key length");
...
@>            if (currentNode.decoded.length == BRANCH_NODE_LENGTH) {
                if (currentKeyIndex == key.length) {
```
## [G-10] use assembly for call can save compared to the higher level call
Directly using assembly for the call can save gas compared to the higher-level address.call method.
### Details

### Proof of Code
- [CrossChainOwned.sol#L50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L50)
```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol
36: function onMessageInvocation(bytes calldata _data)
        external
        payable
        whenNotPaused
        onlyFromNamed("bridge")
    {
        (uint64 txId, bytes memory txdata) = abi.decode(_data, (uint64, bytes));
        if (txId != nextTxId) revert XCO_INVALID_TX_ID();

        IBridge.Context memory ctx = IBridge(msg.sender).context();
        if (ctx.srcChainId != ownerChainId || ctx.from != owner()) {
            revert XCO_PERMISSION_DENIED();
        }

        (bool success,) = address(this).call(txdata); //@audit use assembly
        if (!success) revert XCO_TX_REVERTED();

        emit TransactionExecuted(nextTxId++, bytes4(txdata));
    }
```
### Optimized code:

```diff
diff --git a/packages/protocol/contracts/L2/CrossChainOwned.sol b/packages/protocol/contracts/L2/CrossChainOwned.sol
index 8fe36fc..d0089ea 100644
--- a/packages/protocol/contracts/L2/CrossChainOwned.sol
+++ b/packages/protocol/contracts/L2/CrossChainOwned.sol
@@ -40,14 +40,22 @@ abstract contract CrossChainOwned is EssentialContract, IMessageInvocable {
         onlyFromNamed("bridge")
     {
         (uint64 txId, bytes memory txdata) = abi.decode(_data, (uint64, bytes));
        if (txId != nextTxId) revert XCO_INVALID_TX_ID();
 
         IBridge.Context memory ctx = IBridge(msg.sender).context();
         if (ctx.srcChainId != ownerChainId || ctx.from != owner()) {
             revert XCO_PERMISSION_DENIED();
         }
-
-        (bool success,) = address(this).call(txdata);
+        
+        bool success;
+        bytes memory ret;
+        assembly {
+            let ptr := mload(0x40)
+            let size := calldatasize()
+            calldatacopy(ptr, 0, size)
+            success := call(gas(), address(this), 0, ptr, size, 0, 0)
+            ret := ptr
+        }
         if (!success) revert XCO_TX_REVERTED();
 
         emit TransactionExecuted(nextTxId++, bytes4(txdata));
```
## [G-11] Cache address(this).balance in local variable instead of fetching repeatedly

### Details
Each access to address(this).balance involves an SLOAD operation, which consumes gas. By caching it in a local variable, you avoid these redundant SLOAD operations.

### Proof of Code
- [AssignmentHook.sol#L125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L125C2-L127C10)
```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol
62:  function onBlockProposed(
        TaikoData.Block memory _blk,
        TaikoData.BlockMetadata memory _meta,
        bytes memory _data
    )
...
123: 
        // Send all remaining Ether back to TaikoL1 contract
        if (address(this).balance > 0) { //@audit cahe balance in local variable
            taikoL1Address.sendEther(address(this).balance);
        }
```
### Optimized code:

```diff
diff --git a/packages/protocol/contracts/L1/hooks/AssignmentHook.sol b/packages/protocol/contracts/L1/hooks/AssignmentHook.sol
index f0cfb26..0d3895d 100644
--- a/packages/protocol/contracts/L1/hooks/AssignmentHook.sol
+++ b/packages/protocol/contracts/L1/hooks/AssignmentHook.sol
@@ -120,10 +120,11 @@ contract AssignmentHook is EssentialContract, IHook {
         if (input.tip != 0 && block.coinbase != address(0)) {
             address(block.coinbase).sendEther(input.tip);
         }
-
+         
+        uint256 balance = address(this).balance;
         // Send all remaining Ether back to TaikoL1 contract
-        if (address(this).balance > 0) {
-            taikoL1Address.sendEther(address(this).balance);
+        if (balance > 0) {
+            taikoL1Address.sendEther(balance);
         }
 
         emit BlockAssigned(_blk.assignedProver, _meta, assignment);
```
## [G-12] unchecked loop increments no valid in solidity > v0.8.22
### Details
The new optimization in v0.8.22 removes the need for poor unchecked increment patterns in for loop bodies such
Solidity 0.8.22 introduces an overflow check optimization that automatically generates an unchecked arithmetic increment of the counter of for loops.
### Proof of Code
In newer versions of Solidity (>0.8.22), the unchecked keyword is not necessary. You can simply use i++ inside the loop without worrying about overflow as Solidity will revert the transaction in case of an overflow.
**Instances - 1**
- [MerkleTrie.sol#L209](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L209C1-L213C9)
```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol
210: unchecked {
                ++i;
            }

245: unchecked {
                ++shared_;
            }
```
**Instances - 2**
- [LibDepositing.sol#L100](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L100C4-L105C18)
```solidity
File:  packages/protocol/contracts/L1/libs/LibDepositing.sol
100:                unchecked {
                    deposits_[i].amount -= _fee;
                    totalFee += _fee;
                    ++i;
                    ++j;
                }
```

## [G-13] uint256 variable initialization to default value of 0 can be omitted
There is no need to initialize variables to their default values during declaration, since they are any way initialized to default value once declared.
<details>
<summary>There are 13 instances of this issue:</summary>

---
- [[80]](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L80)
```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

80:         for (uint256 i = 0; i < _newGuardians.length; ++i) {

```
- [[51]](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L51)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

51:         uint256 index = 0;

```
- [[18]](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L18)
```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

18:     bytes4 internal constant SUPPORTED_TEE_TYPE = 0;

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol
```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

80:         for (uint256 idx = 0; idx < shortest; idx += 32) {

331:         uint256 ret = 0;

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol
```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

46:         uint256 timestamp = 0;

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol
```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

72:         uint256 itemCount = 0;

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol
```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

58:         uint256 i = 0;

66:         for (uint256 j = 0; j < out_.length; j++) {

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol
```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

30:     uint8 internal constant PREFIX_EXTENSION_EVEN = 0;

82:         uint256 currentKeyIndex = 0;  

85:         for (uint256 i = 0; i < proof.length; i++) {

208:         for (uint256 i = 0; i < length;) {

```
</details>

## [G-14] check zero amount for burn and mint

### Details
Checking for zero amounts before performing minting or burning operations can save gas by preventing unnecessary computations and storage writes.
### Proof of Code

```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol
105: function _mint( //@audit not check zero
        address _to,
        uint256 _amount
    )
        internal
        override(ERC20Upgradeable, ERC20VotesUpgradeable)
    {
        super._mint(_to, _amount);
    }

    function _burn( //@audit not check zero
        address _from,
        uint256 _amount
    )
        internal
        override(ERC20Upgradeable, ERC20VotesUpgradeable)
    {
        super._burn(_from, _amount);
    }
```
### Instances - 2
### Proof of Code
```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol
163: function _mint( //@audit check zero
        address _to,
        uint256 _amount
    )
        internal
        override(ERC20Upgradeable, ERC20VotesUpgradeable)
    {
        super._mint(_to, _amount);
    }

    function _burn(
        address _from,
        uint256 _amount
    )
        internal
        override(ERC20Upgradeable, ERC20VotesUpgradeable)
    {
        super._burn(_from, _amount);
    }
```
## [G-15] Use require instead of assert because it consumes all remaining gas when it fails

### Details
Using assert in Solidity is generally discouraged because it consumes all remaining gas when it fails, leading to abrupt termination of the transaction. Instead, it's recommended to use require for conditions that should never evaluate to false during normal operation. require will revert the transaction and return remaining gas to the sender, which is a safer behavior.

### Proof of Code

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol
486:  assert(_message.from != address(this));
```
### Optimized code:

```diff
-486: assert(_message.from != address(this));
+486: require(_message.from != address(this),Only sender can send message);
```
## [G-16] Do not cache global variable in local variable

### Details
caching global variable in local variable is more gas consuming compare to use global variable itself
### Proof of Code

```solidity
93: address taikoL1Address = msg.sender; //@audit do not cache state variable
```

## [G-17] `abi.encode` is more efficient than `abi.encodePacked`
`abi.encode` uses less gas than `abi.encodePacked`: the gas saved depends on the number of arguments, with an average of ~90 per argument. Test available here.

<details>
<summary>There are 21 instances of this issue:</summary>

---
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol
```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

204:         meta_.difficulty = keccak256(abi.encodePacked(block.prevrandao, b.numBlocks, block.number));

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol
```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

163:         bytes memory retData = abi.encodePacked(INVALID_EXIT_CODE);

315:             abi.encodePacked(authDataV3.ecdsaAttestationKey, authDataV3.qeAuthData.data);

369:         bytes memory retData = abi.encodePacked(INVALID_EXIT_CODE);

482:         retData = abi.encodePacked(sha256(abi.encode(v3quote)), tcbStatus);

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol
```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

181:             cert.signature = abi.encodePacked(sigX, sigY);

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol
```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

119:         bytes memory headerBytes = abi.encodePacked(

129:         signedQuoteData = abi.encodePacked(headerBytes, V3Parser.packQEReport(localEnclaveReport));

251:         packedQEReport = abi.encodePacked(

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol
```solidity
File: packages/protocol/contracts/libs/Lib4844.sol

44:             abi.encodePacked(_blobHash, _x, _y, _commitment, _pointProof)

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol
```solidity
File: packages/protocol/contracts/libs/LibTrieProof.sol

48:                 SecureMerkleTrie.get(abi.encodePacked(_addr), _accountProof, _rootHash);

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol
```solidity
File: packages/protocol/contracts/signal/SignalService.sol

203:         return keccak256(abi.encodePacked("SIGNAL", _chainId, _app, _signal));

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol
```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

170:         bytes32 hash = keccak256(abi.encodePacked("Withdraw unlocked Taiko token to: ", _to));

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol
```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

17:             out_ = abi.encodePacked(_writeLength(_in.length, 128), _in);

56:         bytes memory b = abi.encodePacked(_x);

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol
```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

81:         bytes memory currentNodeID = abi.encodePacked(_root);

94:                     Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),

100:                     Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol
```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol

55:         hash_ = abi.encodePacked(keccak256(_key));

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol
```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

109:             abi.encodePacked(

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L54
```solidity
File: packages/protocol/contracts/tokenvault/LibBridgedToken.sol

54:             abi.encodePacked(

```
</details>

## [G-18] Use assembly to emit events
We can use assembly to emit events efficiently by utilizing `scratch space` and the `free memory pointer`. This will allow us to potentially avoid memory expansion costs. Note: In order to do this optimization safely, we will need to cache and restore the free memory pointer.

<details>
<summary>There are 56 instances of this issue:</summary>

---
- [[129]](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L129)
```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

129:         emit BlockAssigned(_blk.assignedProver, _meta, assignment);

```
- [[50]](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L50)
```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

50:         emit EthDeposited(

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol
```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

166:                     emit BlobCached(meta_.blobHash);

273:         emit BlockProposed({

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol
```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

80:         emit ProvingPaused(_pause);

209:             emit TransitionProved({

230:                 emit TransitionProved({

254:                 emit TransitionContested({

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol
```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

73:         emit BlockVerified({

198:                 emit BlockVerified({

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol
```solidity
File: packages/protocol/contracts/L1/provers/GuardianProver.sol

54:         emit GuardianApproval(msg.sender, _meta.id, _tran.blockHash, approved_);

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol
```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

95:         emit GuardiansUpdated(version, _newGuardians);

121:         emit Approved(_operationId, _approval, approved_);

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol
```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

53:         emit TransactionExecuted(nextTxId++, bytes4(txdata));

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol
```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

93:             emit MessageSuspended(msgHash, _suspend);

111:         emit AddressBanned(_addr, _ban);

151:         emit MessageSent(msgHash_, message_);

208:             emit MessageRecalled(msgHash);

210:             emit MessageReceived(msgHash, _message, true);

301:             emit MessageExecuted(msgHash);

303:             emit MessageReceived(msgHash, _message, false);

336:         emit MessageRetried(msgHash);

519:         emit MessageStatusChanged(_msgHash, _status);

```
- [[50]](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L50)
```solidity
File: packages/protocol/contracts/common/AddressManager.sol

50:         emit AddressSet(_chainId, _name, _newAddress, oldAddress);

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol
```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

71:         emit Paused(msg.sender);

80:         emit Unpaused(msg.sender);

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol
```solidity
File: packages/protocol/contracts/signal/SignalService.sol

59:         emit Authorized(_addr, _authorize);

250:         emit ChainDataSynced(_chainId, _blockId, _kind, _chainData, signal_);

268:         emit SignalSent(_app, _signal, slot_, _value);

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol
```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

143:         emit Granted(_recipient, _grant);

157:         emit Voided(_recipient, amountVoided);

222:         emit Withdrawn(_recipient, _to, amountToWithdraw, costToWithdraw);

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol
```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

93:         emit Withdrawn(user, amount);

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol
```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

74:         emit Claimed(hash);

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol
```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

51:         emit MigrationStatusChanged(_migratingAddress, _migratingInbound);

63:             emit MigratedTo(_migratingAddress, _account, _amount); //@audit cache migratingAddress

81:             emit MigratedTo(_migratingAddress, _account, _amount); 

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol
```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

80:         emit TokenSent({

114:         emit TokenReceived({

149:         emit TokenReleased({

314:         emit BridgedTokenDeployed({

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol
```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

191:         emit BridgedTokenChanged({

241:         emit TokenSent({

273:         emit TokenReceived({

306:         emit TokenReleased({

425:         emit BridgedTokenDeployed({

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol
```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

64:         emit TokenSent({

97:         emit TokenReceived({

131:         emit TokenReleased({

250:         emit BridgedTokenDeployed({

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol
```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

109:             emit InstanceDeleted(idx, instances[idx].addr);

220:             emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);

230:         emit InstanceAdded(id, newInstance, oldInstance, block.timestamp);

```
</details>


## [G-19] Use assembly for small keccak256 hashes, in order to save gas
Use assembly for small keccak256 hashes, in order to save gas


Instances of this issue:
- [[126]](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L126)
```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

126:                 depositsHash: keccak256(abi.encode(deposits_)),

213:             metaHash: keccak256(abi.encode(meta_)),

```
- [[121]](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L121)
```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

121:         if (blk.blockId != _meta.id || blk.metaHash != keccak256(abi.encode(_meta))) {

```
- [[46]](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L46)
```solidity
File: packages/protocol/contracts/L1/provers/GuardianProver.sol

46:         bytes32 hash = keccak256(abi.encode(_meta, _tran));

```
- [[450]](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L450)
```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

450:         return keccak256(abi.encode("TAIKO_MESSAGE", _message));

```
- [[186]](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L186)
```solidity
File: packages/protocol/contracts/signal/SignalService.sol

186:         return keccak256(abi.encode(_chainId, _kind, _blockId));

```
- [[68]](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L68)
```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

68:         bytes32 hash = keccak256(abi.encode("CLAIM_TAIKO_AIRDROP", data));

```
## [G-20] Redundant event fields can be removed  
Some parameters (block.timestamp and block.number) are added to event information by default so re-adding them wastes gas, as they are already included.


Instances of this issue:
[[230]](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L230)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

230:         emit InstanceAdded(id, newInstance, oldInstance, block.timestamp);

```
## [G-21] Use of emit inside a loop
Emitting an event inside a loop performs a LOG op N times, where N is the loop length. Consider refactoring the code to emit the event only once at the end of loop. Gas savings should be multiplied by the average loop length.


Instances of this issue:
[[90]](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L90)
```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

90:         for (uint256 i; i < _msgHashes.length; ++i) {

```
[[104]](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L104)
,[[210]](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210)
```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

104:         for (uint256 i; i < _ids.length; ++i) {

210:         for (uint256 i; i < _instances.length; ++i) {

```

,
## [G-22] >=/ <= costs less gas than >/<
The compiler uses opcodes GT and ISZERO for solidity code that uses >, but only requires LT for >=,which saves 3 gas

<details>
<summary>There are 96 instances of this issue:</summary>

---
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol
```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

82:             block.timestamp > assignment.expiry

85:                 || assignment.maxBlockId != 0 && _meta.id > assignment.maxBlockId

86:                 || assignment.maxProposedIn != 0 && block.number > assignment.maxProposedIn

125:         if (address(this).balance > 0) { //@audit use assembly

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol
```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

93:                 uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount;

139:             return _amount >= _config.ethDepositMinAmount && _amount <= _config.ethDepositMaxAmount

150:         if (_amount > type(uint96).max) revert L1_INVALID_ETH_DEPOSIT();

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol
```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

98:         if (b.numBlocks >= b.lastVerifiedBlockId + _config.blockMaxProposals + 1) {

171:             if (uint256(params.txListByteOffset) + params.txListByteSize > MAX_BYTES_PER_BLOB) {

195:         if (meta_.txListByteSize == 0 || meta_.txListByteSize > _config.blockMaxTxListBytes) {

296:         return _state.reusableBlobs[_blobHash] + _config.blobExpiry > block.timestamp;

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol
```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

111:         if (_meta.id <= b.lastVerifiedBlockId || _meta.id >= b.numBlocks) {

192:             bool returnLivenessBond = blk.livenessBond > 0 && _proof.data.length == 32

203:         if (_proof.tier > ts.tier) {

381:             if (reward > _tier.validityBond) {

415:             + _tier.provingWindow * 60 >= block.timestamp;

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol
```solidity
File: packages/protocol/contracts/L1/libs/LibUtils.sol

34:         if (_blockId < b.lastVerifiedBlockId || _blockId >= b.numBlocks) {

86:         if (tid_ >= _blk.nextTransitionId) revert L1_UNEXPECTED_TRANSITION_ID();

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol
```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

212:             if (numBlocksVerified > 0) {

238:         if (_lastVerifiedBlockId > lastSyncedBlock + _config.blockSyncThreshold) {

251:                 || _config.blockMaxTxListBytes > 128 * 1024 // calldata up to 128K

256:             || _config.ethDepositMaxCountPerBlock > 32

260:                 || _config.ethDepositMaxAmount > type(uint96).max || _config.ethDepositGas == 0

262:                 || _config.ethDepositMaxFee > type(uint96).max / _config.ethDepositMaxCountPerBlock

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol
```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

82:         if (block.chainid <= 1 || block.chainid > type(uint64).max) {

145:         if (_l1BlockId > lastSyncedBlock + BLOCK_SYNC_THRESHOLD) {

201:         if (_blockId >= block.number) return 0; //@audit we can cache block.number

202:         if (_blockId + 256 >= block.number) return blockhash(_blockId);

234:             for (uint256 i; i < 255 && _blockId >= i + 1; ++i) {

263:         if (_gasExcess > 0) {

277:             if (_lastSyncedBlock > 0 && _l1BlockId > _lastSyncedBlock) { //@audit cache state variable

277:             if (_lastSyncedBlock > 0 && _l1BlockId > _lastSyncedBlock) { //@audit cache state variable

281:             if (numL1Blocks > 0) {
```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol
```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

189:         if (block.timestamp >= invocationDelay + receivedAt) {

258:         if (block.timestamp >= invocationDelay + receivedAt) {

439:         } else if (block.chainid >= 32_300 && block.chainid <= 32_400) {

491:             _message.data.length >= 4 // msg can be empty

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol
```solidity
File: packages/protocol/contracts/thirdparty/optimism/Bytes.sol

25:             require(_length + 31 >= _length, "slice_overflow");

26:             require(_start + _length >= _start, "slice_overflow");

27:             require(_bytes.length >= _start + _length, "slice_outOfBounds");

92:         if (_start >= _bytes.length) { //@audit cache length

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol
```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

38:             _in.length > 0,

153:             _in.length > 0,

173:                 _in.length > strLen,

183:                 strLen != 1 || firstByteOfContent >= 0x80,

193:                 _in.length > lenOfStrLen,

194:                 "RLPReader: length of content must be > than length of string length (long string)"

213:                 strLen > 55,

218:                 _in.length > lenOfStrLen + strLen,

229:                 _in.length > listLen,

239:                 _in.length > lenOfListLen,

240:                 "RLPReader: length of content must be > than length of list length (long list)"

259:                 listLen > 55,

264:                 _in.length > lenOfListLen + listLen,

```
</details>


## [G-23] Use hardcode address instead of address(this) 
Instead of using address(this), it is more gas-efficient to pre-calculate and use the hardcoded address. Foundry’s script.sol and solmate’s LibRlp.sol contracts can help achieve this. References: https://book.getfoundry.sh/reference/forge-std/compute-create-address

<details>
<summary>There are 39 instances of this issue:</summary>

---
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol
```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

61:         if (_to == address(this)) revert TKO_INVALID_ADDR();

79:         if (_to == address(this)) revert TKO_INVALID_ADDR();

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol
```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

125:         if (address(this).balance > 0) { //@audit use assembly

126:             taikoL1Address.sendEther(address(this).balance);

151:                 address(this),

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.so
```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

238:             uint256 tkoBalance = tko.balanceOf(address(this));

253:                 IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }(

260:             if (address(this).balance != 0) {

261:                 msg.sender.sendEther(address(this).balance);

268:             if (tko.balanceOf(address(this)) != tkoBalance + _config.livenessBond) {

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol
```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

242:                 tko.transferFrom(msg.sender, address(this), tier.contestBond);

384:                 _tko.transferFrom(msg.sender, address(this), _tier.validityBond - reward);

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol
```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

50:         (bool success,) = address(this).call(txdata);

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol
```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

174:             _to.sendEther(address(this).balance);

176:             IERC20(_token).safeTransfer(_to, IERC20(_token).balanceOf(address(this)));

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol 
```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

174:             if (!ISignalService(signalService).isSignalSent(address(this), msgHash)) {

196:                 _storeContext(msgHash, address(this), _message.srcChainId);

343:             _app: address(this),

486:         assert(_message.from != address(this));

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol
```solidity
File: packages/protocol/contracts/signal/SignalService.sol

112:                 signalService = address(this);

131:         if (value == 0 || value != _loadSignalValue(address(this), signal)) {

149:         return _loadSignalValue(address(this), signal) == _chainData;

171:             chainData_ = _loadSignalValue(address(this), signal);

245:         _sendSignal(address(this), signal_, _chainData);

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol
```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

137:         if (_to == address(this)) revert BTOKEN_CANNOT_RECEIVE();

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol
```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

108:         if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

226:             IERC1155(token).safeBatchTransferFrom(address(this), to, tokenIds, amounts, "");

272:                         to: address(this),

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol
```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

267:         if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

378:             uint256 _balance = t.balanceOf(address(this));

379:             t.safeTransferFrom({ from: msg.sender, to: address(this), value: _amount });

380:             balanceChange_ = t.balanceOf(address(this)) - _balance;

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol
```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

91:         if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

171:                 IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);

211:                     t.safeTransferFrom(_user, address(this), _op.tokenIds[i]);

```
</details>

## [G-24] Long revert strings


Instances of this issue:
- [[89]](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L89)
```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

89:             require(currentKeyIndex <= key.length, "MerkleTrie: key index exceeds total key length");

```
## [G-25] Constructors can be marked payable
 Payable functions cost less gas to execute, since the compiler does not have to add extra checks to ensure that a payment was not provided. A constructor can safely be marked as payable, since only the deployer would be able to pass funds, and the project itself would not pass any funds.


Instances of this issue:
- [[54]](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L54)
```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

54:     constructor(address sigVerifyLibAddr, address pemCertLibAddr) {

```
- [[20]](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L20)
```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

20:     constructor(address es256Verifier) {

```
- [[64]](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L64)
```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

64:     constructor() {

```

Instances of this issue:

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

358:             uint16 svnValue = svnValueBytes.length < 2

```
[[358]](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L358)

## [G-26] Usage of smaller uint/int types causes overhead
When using a smaller int/uint type it first needs to be converted to it's 258 bit counterpart to be operated, this increases the gass cost and thus should be avoided. However it does make sense to use smaller int/uint values within structs provided you pack the struct properly.

<details>
<summary>There are 302 instances of this issue:</summary>

---

```solidity
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/ITaikoL1.sol

File: packages/protocol/contracts/L1/ITaikoL1.sol

27:     function proveBlock(uint64 _blockId, bytes calldata _input) external;

31:     function verifyBlocks(uint64 _maxBlocksToVerify) external;

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol
```solidity
File: packages/protocol/contracts/L1/TaikoData.sol

15:         uint64 chainId;

20:         uint64 blockMaxProposals;

22:         uint64 blockRingBufferSize;

24:         uint64 maxBlocksToVerifyPerProposal;

26:         uint32 blockMaxGasLimit;

46:         uint64 ethDepositMinCountPerBlock;

48:         uint64 ethDepositMaxCountPerBlock;

59:         uint8 blockSyncThreshold; //@audit

64:         uint16 tier;

65:         uint128 fee;

69:         uint16 tier;

101:         uint64 id;

102:         uint32 gasLimit;

103:         uint64 timestamp; // slot 7

104:         uint64 l1Height;

107:         uint16 minTier;

130:         uint64 timestamp; // slot 6 (90 bits)

131:         uint16 tier;

132:         uint8 contestations;

141:         uint64 blockId; // slot 3

142:         uint64 proposedAt; // timestamp

143:         uint64 proposedIn; // L1 block number

144:         uint32 nextTransitionId;

145:         uint32 verifiedTransitionId;

153:         uint64 id;

162:         uint64 genesisHeight;

163:         uint64 genesisTimestamp;

164:         uint64 numEthDeposits;

165:         uint64 nextEthDepositToProcess;

169:         uint64 numBlocks;

170:         uint64 lastVerifiedBlockId;

172:         uint8 __reserved1;

173:         uint16 __reserved2;

174:         uint32 __reserved3;                 

175:         uint64 lastUnpausedAt;

181:         mapping(uint64 blockId_mod_blockRingBufferSize => Block blk) blocks;

183:         mapping(uint64 blockId => mapping(bytes32 parentHash => uint32 transitionId)) transitionIds;

183:         mapping(uint64 blockId => mapping(bytes32 parentHash => uint32 transitionId)) transitionIds;

186:             uint64 blockId_mod_blockRingBufferSize

187:                 => mapping(uint32 transitionId => TransitionState ts)

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol
```solidity
File: packages/protocol/contracts/L1/TaikoEvents.sol

43:         uint16 tier,

44:         uint8 contestations

58:         uint16 tier

72:         uint16 tier

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol
```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

76:         uint64 _blockId,

94:         uint8 maxBlocksToVerify = LibProving.proveBlock(state, config, this, meta, tran, proof);

100:     function verifyBlocks(uint64 _maxBlocksToVerify)

145:     function getBlock(uint64 _blockId)

150:         uint64 slot;

163:         uint64 _blockId,

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol
```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

166:         uint16 _tierId

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol
```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

84:             uint64 j = _state.slotA.nextEthDepositToProcess;

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol
```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

37:         uint16 tier

51:         uint16 tier

100:         returns (uint8 maxBlocksToVerify_)

115:         uint64 slot = _meta.id % _config.blockRingBufferSize;

129:         (uint32 tid, TaikoData.TransitionState storage ts) =

273:         uint64 slot

276:         returns (uint32 tid_, TaikoData.TransitionState storage ts_)

405:         uint32 _tid,

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol
```solidity
File: packages/protocol/contracts/L1/libs/LibUtils.sol

26:         uint64 _blockId,

38:         uint64 slot = _blockId % _config.blockRingBufferSize;

42:         uint32 tid = getTransitionId(_state, blk, slot, _parentHash);

55:         uint64 _blockId

59:         returns (TaikoData.Block storage blk_, uint64 slot_)

73:         uint64 _slot,

78:         returns (uint32 tid_)

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol
```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

34:         uint16 tier,

35:         uint8 contestations

89:         uint64 _maxBlocksToVerify

100:         uint64 blockId = b.lastVerifiedBlockId;

102:         uint64 slot = blockId % _config.blockRingBufferSize;

107:         uint32 tid = blk.verifiedTransitionId;

117:         uint64 numBlocksVerified;

213:                 uint64 lastVerifiedBlockId = b.lastVerifiedBlockId + numBlocksVerified;

227:         uint64 _lastVerifiedBlockId,

234:         (uint64 lastSyncedBlock,) = signalService.getSyncedChainData(

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol
```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

19:     mapping(uint32 version => mapping(bytes32 hash => uint256 approvalBits)) internal _approvals;

27:     uint32 public version;

30:     uint32 public minGuardians;

37:     event GuardiansUpdated(uint32 version, address[] guardians);

55:         uint8 _minGuardians

```

```solidity
File: packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol

20:     function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol
```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

27:         uint32 gasTargetPerL1Block;

28:         uint8 basefeeAdjustmentQuotient;

35:     uint8 public constant BLOCK_SYNC_THRESHOLD = 5;

47:     uint64 public gasExcess;

50:     uint64 public lastSyncedBlock;

57:     event Anchored(bytes32 parentHash, uint64 gasExcess);

74:         uint64 _l1ChainId,

75:         uint64 _gasExcess

110:         uint64 _l1BlockId,

111:         uint32 _parentGasUsed

186:         uint64 _l1BlockId,

187:         uint32 _parentGasUsed

200:     function getBlockHash(uint64 _blockId) public view returns (bytes32) {

254:         uint64 _l1BlockId,

255:         uint32 _parentGasUsed

259:         returns (uint256 basefee_, uint64 gasExcess_)

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol
```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

9:         uint16 yrs;

10:         uint8 mnths;

11:         uint8 dys;

12:         uint8 hrs;

13:         uint8 mins;

14:         uint8 secs;

15:         uint8 offset;

35:         uint16 year,

36:         uint8 month,

37:         uint8 day,

38:         uint8 hour,

39:         uint8 minute,

40:         uint8 second

48:         for (uint16 i = 1970; i < year; ++i) {

59:         for (uint8 i = 1; i < month; ++i) {

71:     function isLeapYear(uint16 year) internal pure returns (bool) {

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol
```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

31:     uint128 public nextMessageId;

64:     modifier sameChain(uint64 _chainId) {

89:         uint64 _timestamp = _suspend ? type(uint64).max : uint64(block.timestamp);

168:         uint64 receivedAt = proofReceipt[msgHash].receivedAt;

230:         uint64 receivedAt = proofReceipt[msgHash].receivedAt;  //@audit cache proofReceipt[msgHash]

392:     function isDestChainEnabled(uint64 _chainId)

541:     function _storeContext(bytes32 _msgHash, address _from, uint64 _srcChainId) private {

559:             uint64 srcChainId;

580:         uint64 _chainId,

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol
```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

11:     uint8 private constant _FALSE = 1;

13:     uint8 private constant _TRUE = 2; //@audit pack

21:     uint8 private __reentry;

23:     uint8 private __paused;

119:     function _storeReentryLock(uint8 _reentry) internal virtual {

130:     function _loadReentryLock() internal view virtual returns (uint8 reentry_) {

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol
```solidity
File: packages/protocol/contracts/signal/ISignalService.sol

21:         uint64 chainId;

21:         uint64 chainId;

22:         uint64 blockId;

22:         uint64 blockId;

37:         uint64 indexed chainId,

37:         uint64 indexed chainId,

38:         uint64 indexed blockId,

38:         uint64 indexed blockId,

69:         uint64 _chainId,

69:         uint64 _chainId,

71:         uint64 _blockId,

71:         uint64 _blockId,

85:         uint64 _chainId,

85:         uint64 _chainId,

106:         uint64 _chainId,

106:         uint64 _chainId,

108:         uint64 _blockId,

108:         uint64 _blockId,

123:         uint64 _chainId,

123:         uint64 _chainId,

125:         uint64 _blockId

125:         uint64 _blockId

129:         returns (uint64 blockId_, bytes32 chainData_);

129:         returns (uint64 blockId_, bytes32 chainData_);

138:         uint64 _chainId,

138:         uint64 _chainId,

140:         uint64 _blockId

140:         uint64 _blockId

```
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol
```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

29:         uint128 amount;

31:         uint128 costPerToken;

34:         uint64 grantStart;

37:         uint64 grantCliff;

40:         uint32 grantPeriod;

43:         uint64 unlockStart;

46:         uint64 unlockCliff;

49:         uint32 unlockPeriod;

53:         uint128 amountWithdrawn;

54:         uint128 costPaid;

68:     uint128 public totalAmountGranted;

71:     uint128 public totalAmountVoided;

74:     uint128 public totalAmountWithdrawn;

77:     uint128 public totalCostPaid;

92:     event Voided(address indexed recipient, uint128 amount);

99:     event Withdrawn(address indexed recipient, address to, uint128 amount, uint128 cost);

99:     event Withdrawn(address indexed recipient, address to, uint128 amount, uint128 cost);

152:         uint128 amountVoided = _voidGrant(r.grant);

180:             uint128 amountOwned,

181:             uint128 amountUnlocked,

182:             uint128 amountWithdrawn,

183:             uint128 amountToWithdraw,

184:             uint128 costToWithdraw

197:         uint128 _amountUnlocked = amountUnlocked / 1e18; // divide first

211:         (,,, uint128 amountToWithdraw, uint128 costToWithdraw) = getMyGrantSummary(_recipient);

211:         (,,, uint128 amountToWithdraw, uint128 costToWithdraw) = getMyGrantSummary(_recipient);

225:     function _voidGrant(Grant storage _grant) private returns (uint128 amountVoided) {

226:         uint128 amountOwned = _getAmountOwned(_grant);

246:         uint128 _amount,

247:         uint64 _start,

```
</details>