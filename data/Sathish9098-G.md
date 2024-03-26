# GAS OPTIMIZATION 

##

[G-1] Optimize State Variables to Fit Fewer Storage Slots

The EVM works with 32 byte words. Variables less than 32 bytes can be declared next to each other in storage and this will pack the values together into a single 32 byte storage slot (if the values combined are <= 32 bytes). If the variables packed together are retrieved together in functions we will effectively save ~2000 gas with every subsequent SLOAD for that storage slot. This is due to us incurring a Gwarmaccess (100 gas) versus a Gcoldsload (2100 gas).

### [G-1.1] ``srcChainId`` and ``snapshooter`` can be packed same slot : Saves ``2000 GAS`` , ``1 SLOT``

```solidity
uint64 chainId;
uint64 destChainId;

```

Even in other contracts using uint64 for chainId.

There are numerous blockchain platforms, but the number currently active and recognized does not exceed the range that a uint96 can represent. For instance, while there are many blockchain platforms, the actual number of unique, significant blockchain networks is far less than the maximum number that a ``uint96`` can store. A uint96 can store numbers up to ``79,228,162,514,264,337,593,543,950,335``. In comparison, the current number of significant blockchain platforms and networks, as indicated by sources discussing different types of blockchain networks and their applications, is only in the dozens or perhaps hundreds​​​​.

Even with the projected growth of blockchain technology and the creation of new chains, it is highly unlikely that the total number will approach the uint96 limit in any foreseeable future.

```diff
FILE: 2024-03-taiko/packages/protocol/contracts/tokenvault/BridgedERC20.sol

/// @dev Slot 1.
    address public srcToken;

    uint8 private __srcDecimals;

    /// @dev Slot 2.
-    uint256 public srcChainId;
+    uint96 public srcChainId;

    /// @dev Slot 3.
    address public snapshooter;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L21-L32

### [G-1.2] ``srcToken`` and ``srcChainId`` can be packed same slot : Saves ``4000 GAS`` , ``2 SLOT``

```diff
FILE: 2024-03-taiko/packages/protocol/contracts/tokenvault/BridgedERC721.sol

 /// @notice Address of the source token contract.
    address public srcToken;

    /// @notice Source chain ID where the token originates.
-    uint256 public srcChainId;
+    uint96 public srcChainId;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L13-L17


```diff
FILE: 2024-03-taiko/packages/protocol/contracts/tokenvault/BridgedERC1155.sol

 /// @notice Address of the source token contract.
    address public srcToken;

    /// @notice Source chain ID where the token originates.
-    uint256 public srcChainId;
+    uint96 public srcChainId;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L15-L19


### [G-1.3] ``_checkLocalEnclaveReport`` and ``owner`` can be packed same slot : Saves ``2000 GAS`` , ``1 SLOT``

```diff
FILE: 2024-03-taiko/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

 bool private _checkLocalEnclaveReport;
+    address public owner;
    mapping(bytes32 enclave => bool trusted) private _trustedUserMrEnclave;
    mapping(bytes32 signer => bool trusted) private _trustedUserMrSigner;

    // Quote Collateral Configuration

    // Index definition:
    // 0 = Quote PCKCrl
    // 1 = RootCrl
    mapping(uint256 idx => mapping(bytes serialNum => bool revoked)) private _serialNumIsRevoked;
    // fmspc => tcbInfo
    mapping(string fmspc => TCBInfoStruct.TCBInfo tcbInfo) public tcbInfo;
    EnclaveIdStruct.EnclaveId public qeIdentity;

-    address public owner;


```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L38-L52

##

## [G-2] State variables only set in the constructor should be declared immutable

Avoids a Gsset (20000 gas) in the constructor, and replaces the first access in each transaction (Gcoldsload - 2100 gas) and each access thereafter (Gwarmacces - 100 gas) with a PUSH32 (3 gas).

While strings are not value types, and therefore cannot be immutable/constant if not hard-coded outside of the constructor, the same behavior can be achieved by making the current contract abstract with virtual functions for the string accessors, and having a child contract override the functions with the hard-coded implementation-specific values.

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/automata-attestation
/AutomataDcapV3Attestation.sol

52: address public owner;


54: constructor(address sigVerifyLibAddr, address pemCertLibAddr) {
        sigVerifyLib = ISigVerifyLib(sigVerifyLibAddr);
        pemCertLib = PEMCertChainLib(pemCertLibAddr);
        owner = msg.sender;
    }

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L57

##

## [G-3] Optimizing gas usage by caching state variables in local memory variables

The instances below point to the second+ access of a state variable within a function. Caching of a state variable replace each Gwarmaccess (100 gas) with a much cheaper stack read. Other less obvious fixes/optimizations include having local memory caches of state variable structs, or having local caches of state variable contracts/addresses. Most of the times this if statement will be true and we will save 100 gas at a small possibility of 3 gas loss

### [G-3.1] ``addressManager`` can be cached . Saves ``100 GAS`` , ``1 SLOD``

```diff
FILE: 2024-03-taiko/packages/protocol/contracts/common/AddressResolver.sol

+  address addressManager_= addressManager ;
- if (addressManager == address(0)) revert RESOLVER_INVALID_MANAGER();
+ if (addressManager_== address(0)) revert RESOLVER_INVALID_MANAGER();
-        addr_ = payable(IAddressManager(addressManager).getAddress(_chainId, _name));
+        addr_ = payable(IAddressManager(addressManager_).getAddress(_chainId, _name));

        if (!_allowZeroAddress && addr_ == address(0)) {
            revert RESOLVER_ZERO_ADDR(_chainId, _name);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressResolver.sol#L81-L83

### [G-3.2] ``_state.slotA.numEthDeposits`` can be cached . Saves ``100 GAS`` , ``1 SLOD``

```diff
FILE:2024-03-taiko/packages/protocol/contracts/L1/libs
/LibDepositing.sol

// Append the deposit to the queue.
+  uint64 numEthDeposits_ =_state.slotA.numEthDeposits ;  
        address recipient_ = _recipient == address(0) ? msg.sender : _recipient;
-        uint256 slot = _state.slotA.numEthDeposits % _config.ethDepositRingBufferSize;
+        uint256 slot = numEthDeposits_ % _config.ethDepositRingBufferSize;

        // range of msg.value is checked by next line.
        _state.ethDeposits[slot] = _encodeEthDeposit(recipient_, msg.value);

        emit EthDeposited(
            TaikoData.EthDeposit({
                recipient: recipient_,
                amount: uint96(msg.value),
-                id: _state.slotA.numEthDeposits
+                id: numEthDeposits_ 
            })
        );

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L45

### [G-3.3] ``blk.blockId`` , ``blk.metaHash`` , ``blk.livenessBond``, ``_ts.contester``  can be cached  : ``700 GAS`` , ``7 SLODs``

```diff
FILE: 

/// @dev Proves or contests a block transition.
    /// @param _state Current TaikoData.State.
    /// @param _config Actual TaikoData.Config.
    /// @param _resolver Address resolver interface.
    /// @param _meta The block's metadata.
    /// @param _tran The transition data.
    /// @param _proof The proof.
    /// @param maxBlocksToVerify_ The number of blocks to be verified with this transaction.
    function proveBlock(
        TaikoData.State storage _state,
        TaikoData.Config memory _config,
        IAddressResolver _resolver,
        TaikoData.BlockMetadata memory _meta,
        TaikoData.Transition memory _tran,
        TaikoData.TierProof memory _proof
    )
        internal
        returns (uint8 maxBlocksToVerify_)
    {
        // Make sure parentHash is not zero
        // To contest an existing transition, simply use any non-zero value as
        // the blockHash and stateRoot.
        if (_tran.parentHash == 0 || _tran.blockHash == 0 || _tran.stateRoot == 0) {
            revert L1_INVALID_TRANSITION();
        }

        // Check that the block has been proposed but has not yet been verified.
        TaikoData.SlotB memory b = _state.slotB;
        if (_meta.id <= b.lastVerifiedBlockId || _meta.id >= b.numBlocks) {
            revert L1_INVALID_BLOCK_ID();
        }

        uint64 slot = _meta.id % _config.blockRingBufferSize;
        TaikoData.Block storage blk = _state.blocks[slot];

        // Check the integrity of the block data. It's worth noting that in
        // theory, this check may be skipped, but it's included for added
        // caution.
+   uint64 blockId_ = blk.blockId ;
+   uint64 metaHash_ = blk.metaHash ; 
-        if (blk.blockId != _meta.id || blk.metaHash !=
+        if (blockId_ != _meta.id || metaHash_ 
!=  keccak256(abi.encode(_meta))) {
            revert L1_BLOCK_MISMATCH();
        }

        // Each transition is uniquely identified by the parentHash, with the
        // blockHash and stateRoot open for later updates as higher-tier proofs
        // become available. In cases where a transition with the specified
        // parentHash does not exist, the transition ID (tid) will be set to 0.
        (uint32 tid, TaikoData.TransitionState storage ts) =
            _createTransition(_state, blk, _tran, slot);

        // The new proof must meet or exceed the minimum tier required by the
        // block or the previous proof; it cannot be on a lower tier.
        if (_proof.tier == 0 || _proof.tier < _meta.minTier || _proof.tier < ts.tier) {
            revert L1_INVALID_TIER();
        }

        // Retrieve the tier configurations. If the tier is not supported, the
        // subsequent action will result in a revert.
        ITierProvider.Tier memory tier =
            ITierProvider(_resolver.resolve("tier_provider", false)).getTier(_proof.tier);

        // Check if this prover is allowed to submit a proof for this block
        _checkProverPermission(_state, blk, ts, tid, tier);

        // We must verify the proof, and any failure in proof verification will
        // result in a revert.
        //
        // It's crucial to emphasize that the proof can be assessed in two
        // potential modes: "proving mode" and "contesting mode." However, the
        // precise verification logic is defined within each tier's IVerifier
        // contract implementation. We simply specify to the verifier contract
        // which mode it should utilize - if the new tier is higher than the
        // previous tier, we employ the proving mode; otherwise, we employ the
        // contesting mode (the new tier cannot be lower than the previous tier,
        // this has been checked above).
        //
        // It's obvious that proof verification is entirely decoupled from
        // Taiko's core protocol.
        {
            address verifier = _resolver.resolve(tier.verifierName, true);

            if (verifier != address(0)) {
                bool isContesting = _proof.tier == ts.tier && tier.contestBond != 0;

                IVerifier.Context memory ctx = IVerifier.Context({
-                    metaHash: blk.metaHash,
+                    metaHash: metaHash_ ,
                    blobHash: _meta.blobHash,
                    // Separate msgSender to allow the prover to be any address in the future.
                    prover: msg.sender,
                    msgSender: msg.sender,
-                    blockId: blk.blockId,
+                    blockId: blockId_, 
                    isContesting: isContesting,
                    blobUsed: _meta.blobUsed
                });

                IVerifier(verifier).verifyProof(ctx, _tran, _proof);
            } else if (tier.verifierName != TIER_OP) {
                // The verifier can be address-zero, signifying that there are no
                // proof checks for the tier. In practice, this only applies to
                // optimistic proofs.
                revert L1_MISSING_VERIFIER();
            }
        }

        bool isTopTier = tier.contestBond == 0;
        IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));

        if (isTopTier) {
            // A special return value from the top tier prover can signal this
            // contract to return all liveness bond.
+ uint96  livenessBond_ = blk.livenessBond ; 
-            bool returnLivenessBond = blk.livenessBond > 0 && _proof.data.length == 32
                && bytes32(_proof.data) == RETURN_LIVENESS_BOND;
+            bool returnLivenessBond = livenessBond_  > 0 && _proof.data.length == 32
                && bytes32(_proof.data) == RETURN_LIVENESS_BOND;

            if (returnLivenessBond) {
-                tko.transfer(blk.assignedProver, blk.livenessBond);
+                tko.transfer(blk.assignedProver, livenessBond_ );
                blk.livenessBond = 0;
            }
        }

        bool sameTransition = _tran.blockHash == ts.blockHash && _tran.stateRoot == ts.stateRoot;

        if (_proof.tier > ts.tier) {
            // Handles the case when an incoming tier is higher than the current transition's tier.
            // Reverts when the incoming proof tries to prove the same transition
            // (L1_ALREADY_PROVED).
            _overrideWithHigherProof(ts, _tran, _proof, tier, tko, sameTransition);

            emit TransitionProved({
-                blockId: blk.blockId,
+                blockId: blockId_,
                tran: _tran,
                prover: msg.sender,
                validityBond: tier.validityBond,
                tier: _proof.tier
            });
        } else {
            // New transition and old transition on the same tier - and if this transaction tries to
            // prove the same, it reverts
            if (sameTransition) revert L1_ALREADY_PROVED();

            if (isTopTier) {
                // The top tier prover re-proves.
                assert(tier.validityBond == 0);
                assert(ts.validityBond == 0 && ts.contestBond == 0 && ts.contester == address(0));

                ts.prover = msg.sender;
                ts.blockHash = _tran.blockHash;
                ts.stateRoot = _tran.stateRoot;

                emit TransitionProved({
-                    blockId: blk.blockId,
+                    blockId: blockId_,
                    tran: _tran,
                    prover: msg.sender,
                    validityBond: 0,
                    tier: _proof.tier
                });
            } else {
                // Contesting but not on the highest tier
                if (ts.contester != address(0)) revert L1_ALREADY_CONTESTED();

                // Burn the contest bond from the prover.
                tko.transferFrom(msg.sender, address(this), tier.contestBond);

                // We retain the contest bond within the transition, just in
                // case this configuration is altered to a different value
                // before the contest is resolved.
                //
                // It's worth noting that the previous value of ts.contestBond
                // doesn't have any significance.
                ts.contestBond = tier.contestBond;
                ts.contester = msg.sender;
                ts.contestations += 1;

                emit TransitionContested({
-                    blockId: blk.blockId,
+                    blockId: blockId_,
                    tran: _tran,
                    contester: msg.sender,
                    contestBond: tier.contestBond,
                    tier: _proof.tier
                });
            }
        }

        ts.timestamp = uint64(block.timestamp);
        return tier.maxBlocksToVerifyPerProof;
    }


 +  address contester_ = _ts.contester ;  
- if (_ts.contester != address(0)) {
+ if (contester_  != address(0)) {
            if (_sameTransition) {
                // The contested transition is proven to be valid, contestor loses the game
                reward = _ts.contestBond >> 2;
                _tko.transfer(_ts.prover, _ts.validityBond + reward);
            } else {
                // The contested transition is proven to be invalid, contestor wins the game
                reward = _ts.validityBond >> 2;
-                _tko.transfer(_ts.contester, _ts.contestBond + reward);
+                _tko.transfer(contester_, _ts.contestBond + reward);
            }

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L121

### [G-3.4] ``ts.prover`` can be cached  : Saves ``200 GAS`` , ``2 SLODs``

```diff
2024-03-taiko/packages/protocol/contracts/L1/libs
/LibVerifying.sol

 // Nevertheless, it's possible for the actual prover to be the
                // same individual or entity as the block's assigned prover.
                // Consequently, we have chosen to grant the actual prover only
                // half of the liveness bond as a reward.

+ address  prover_ = ts.prover ; 
-                if (ts.prover != blk.assignedProver) {
+                if (prover_ != blk.assignedProver) {
                    bondToReturn -= blk.livenessBond >> 1;
                }

                IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));
-                tko.transfer(ts.prover, bondToReturn);
+                tko.transfer(prover_ , bondToReturn);

                // Note: We exclusively address the bonds linked to the
                // transition used for verification. While there may exist
                // other transitions for this block, we disregard them entirely.
                // The bonds for these other transitions are burned either when
                // the transitions are generated or proven. In such cases, both
                // the provers and contesters of those transitions forfeit their bonds.

                emit BlockVerified({
                    blockId: blockId,
                    assignedProver: blk.assignedProver,
-                    prover: ts.prover,
+                    prover: prover_ ,
                    blockHash: blockHash,
                    stateRoot: stateRoot,
                    tier: ts.tier,
                    contestations: ts.contestations
                });



```

### [G-3.5] ``version`` can be cached : Saves ``100 GAS`` , ``1 SLOD``

```diff
FILE: 2024-03-taiko/packages/protocol/contracts/L1/provers/Guardians.sol

+  uint32 version_ = version ; 
 unchecked {
-            _approvals[version][_hash] |= 1 << (id - 1);
+            _approvals[version_ ][_hash] |= 1 << (id - 1);
        }

-        uint256 _approval = _approvals[version][_hash];
+        uint256 _approval = _approvals[version_ ][_hash];
        approved_ = isApproved(_approval);
        emit Approved(_operationId, _approval, approved_);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L116

### [G-3.6] ``gasExcess`` , ``lastSyncedBlock`` can be cached  : Saves ``300 GAS`` , ``3 SLODs``

```diff
FILE: 2024-03-taiko/packages/protocol/contracts/L2/TaikoL2.sol

{
        // gasExcess being 0 indicate the dynamic 1559 base fee is disabled.
+  uint64  gasExcess_ = gasExcess ; 
-        if (gasExcess > 0) {
+        if (gasExcess_ > 0) {
            // We always add the gas used by parent block to the gas excess
            // value as this has already happened
-            uint256 excess = uint256(gasExcess) + _parentGasUsed;
+            uint256 excess = uint256(gasExcess_) + _parentGasUsed;

            // Calculate how much more gas to issue to offset gas excess.
            // after each L1 block time, config.gasTarget more gas is issued,
            // the gas excess will be reduced accordingly.
            // Note that when lastSyncedBlock is zero, we skip this step
            // because that means this is the first time calculating the basefee
            // and the difference between the L1 height would be extremely big,
            // reverting the initial gas excess value back to 0.
            uint256 numL1Blocks;
+   uint64  lastSyncedBlock_ = lastSyncedBlock ;
-            if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {
+            if (lastSyncedBlock_ > 0 && _l1BlockId > lastSyncedBlock_ ) {
-                numL1Blocks = _l1BlockId - lastSyncedBlock;
+                numL1Blocks = _l1BlockId - lastSyncedBlock_;
            }

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L262-L277

### [G-3.7] ``migratingAddress`` can be cached : Saves ``300 GAS`` , ``3 SLODs``

```diff
FILE: 2024-03-taiko/packages/protocol/contracts/tokenvault
/BridgedERC20Base.sol

+ address migratingAddress_ = migratingAddress ;
- if (msg.sender == migratingAddress) {
+ if (msg.sender == migratingAddress_) {
            // Inbound migration
-            emit MigratedTo(migratingAddress, _account, _amount);
+            emit MigratedTo(migratingAddress_, _account, _amount);


+ address migratingAddress_ = migratingAddress ;
// Outbound migration
-            emit MigratedTo(migratingAddress, _account, _amount);
+            emit MigratedTo(migratingAddress_ , _account, _amount);
            // Ask the new bridged token to mint token for the user.
-            IBridgedERC20(migratingAddress).mint(_account, _amount);
+            IBridgedERC20(migratingAddress_).mint(_account, _amount);


 // Outbound migration
            emit MigratedTo(migratingAddress, _account, _amount);
            // Ask the new bridged token to mint token for the user.
            IBridgedERC20(migratingAddress).mint(_account, _amount);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L61-L64

### [G-3.8] ``instances[idx].addr`` , ``nextInstanceId`` ``instances[id].validSince``  can be cached  : Saves ``400 GAS`` , ``4 SLODs``

```diff
FILE: 2024-03-taiko/packages/protocol/contracts/verifiers
/SgxVerifier.sol

+ address addr_ = instances[idx].addr ; 

- if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();
+ if (addr_ == address(0)) revert SGX_INVALID_INSTANCE();

-            emit InstanceDeleted(idx, instances[idx].addr);
+            emit InstanceDeleted(idx, addr_);



for (uint256 i; i < _instances.length; ++i) {
            if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();

            addressRegistered[_instances[i]] = true;

            if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();

+  uint256 nextInstanceId_ = nextInstanceId ; 
-            instances[nextInstanceId] = Instance(_instances[i], validSince);
+            instances[nextInstanceId_ ] = Instance(_instances[i], validSince);
-            ids[i] = nextInstanceId;
+            ids[i] = nextInstanceId_;

-            emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);
+            emit InstanceAdded(nextInstanceId_ , _instances[i], address(0), validSince);

            nextInstanceId++;
        }


+  uint64 validSince_ = instances[id].validSince ;
- return instances[id].validSince <= block.timestamp
            && block.timestamp <= instances[id].validSince + INSTANCE_EXPIRY;
+ return validSince_  <= block.timestamp
            && block.timestamp <= validSince_ + INSTANCE_EXPIRY;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L107-L109

##

## [G-4] Consolidate Multiple Address/ID Mappings into Single Struct-Based Mapping

Saves a storage slot for the mapping. Depending on the circumstances and sizes of types, can avoid a Gsset (20000 gas) per mapping combined. Reads and subsequent writes can also be cheaper when a function requires both values and they both fit in the same storage slot. Finally, if both fields are accessed in the same function, can save ~42 gas per access due to not having to recalculate the key's keccak256 hash (Gkeccak256 - 30 gas) and that calculation's associated stack operations.

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/automata-attestation
/AutomataDcapV3Attestation.sol


+ struct TrustStatus {
+    bool byEnclave;
+    bool bySigner;
+ }

+ mapping(bytes32 => TrustStatus) private _trustedStatus;

-  mapping(bytes32 enclave => bool trusted) private _trustedUserMrEnclave;
-  mapping(bytes32 signer => bool trusted) private _trustedUserMrSigner;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L39-L40

## 

## [G-5] Using storage instead of memory for state variables saves gas

When fetching data from a storage location, assigning the data to a memory variable causes all fields of the struct/array to be read from storage, which incurs a Gcoldsload (2100 gas) for each field of the struct/array. If the fields are read from the new memory variable, they incur an additional MLOAD rather than a cheap stack read. Instead of declaring the variable with the memory keyword, declaring the variable with the storage keyword and caching any fields that need to be re-read in stack variables, will be much cheaper, only incurring the Gcoldsload for the fields actually read. The only time it makes sense to read the whole struct/array into a memory variable, is if the full struct/array is being returned by the function, is being passed to a function that requires memory, or if the array/struct is being read from another memory array/struct

```solidity
FILE:2024-03-taiko/packages/protocol/contracts/L1/libs
/LibProving.sol

110: TaikoData.SlotB memory b = _state.slotB;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L110

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/L1/libs
/LibUtils.sol

33: TaikoData.SlotB memory b = _state.slotB;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibUtils.sol#L33

##

## [G-6] Cache the state variables outside the loop

Accessing state variables (like minGuardians) is more expensive in terms of gas than accessing local variables. By reading minGuardians from storage once and storing it in a local variable (cachedMinGuardians), you reduce the cost associated with repeatedly reading this state variable inside the loop. Since minGuardians does not change within the function's scope, this optimization is safe and effective.

```diff
FILE: 2024-03-taiko/packages/protocol/contracts/L1/provers
/Guardians.sol

+   uint32 cachedMinGuardians = minGuardians ; 
unchecked {
            for (uint256 i; i < guardiansLength; ++i) {
                if (bits & 1 == 1) ++count;
-                if (count == minGuardians) return true;
+                if (count == cachedMinGuardians ) return true;
                bits >>= 1;
            }
        }

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L132-L137

##

## [G-7] ``_newGuardians.length`` calculated multiple times 

Calculating length of bytes every time costs gas. The better solution would be to calculate the length once and save it in a local variable

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/L1/provers
/Guardians.sol

 // We need at least MIN_NUM_GUARDIANS and at most 255 guardians (so the approval bits fit in
        // a uint256)
        if (_newGuardians.length < MIN_NUM_GUARDIANS || _newGuardians.length > type(uint8).max) {
            revert INVALID_GUARDIAN_SET();
        }
        // Minimum number of guardians to approve is at least equal or greater than half the
        // guardians (rounded up) and less or equal than the total number of guardians
        if (_minGuardians < (_newGuardians.length + 1) >> 1 || _minGuardians > _newGuardians.length)
        {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L61-L69

##

## [G-8] Using ``calldata`` instead of ``memory`` for read-only arguments in external functions saves gas

calldata must be used when declaring an external function's dynamic parameters

When a function with a memory array is called externally, the abi.decode ()  step has to use a for-loop to copy each index of the calldata to the memory index. Each iteration of this for-loop costs at least 60 gas (i.e. 60 * <mem_array>.length). Using calldata directly, obliviates the need for such a loop in the contract code and runtime execution. 

```diff
FILE: 2024-03-taiko/packages/protocol/contracts/L1/libs
/LibUtils.sol

23: function getTransition(
        TaikoData.State storage _state,
-        TaikoData.Config memory _config,
+        TaikoData.Config calldata _config,
        uint64 _blockId,
        bytes32 _parentHash
    )
        external
        view
        returns (TaikoData.TransitionState storage)

52: function getBlock(
        TaikoData.State storage _state,
-        TaikoData.Config memory _config,
+        TaikoData.Config calldata _config,
        uint64 _blockId
    )
        external
        view
        returns (TaikoData.Block storage blk_, uint64 slot_)

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibUtils.sol#L25

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/L1/provers
/Guardians.sol

53: function setGuardians(
-        address[] memory _newGuardians,
+        address[] calldata _newGuardians,
        uint8 _minGuardians
    )
        external
        onlyOwner
        nonReentrant

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L54

##

## [G-9] Replace Function Calls with Constants 

Functions like ``votingDelay``, ``votingPeriod``, and ``proposalThreshold`` are marked pure because they return fixed values without interacting with contract state. However, each function call consumes gas. Replacing these with direct values or constants in the code eliminates function execution overhead, saving gas.

While a pure function call might cost around ``700 to 800 gas`` per call due to execution and ``computational overhead``, accessing a constant directly is significantly cheaper, often costing around ``3 to 5`` gas. Therefore, replacing a function call with a direct value could save approximately ``695 to 797 gas`` per call.

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/L1/gov/TaikoGovernor.sol

// @notice How long after a proposal is created should voting power be fixed. A
    /// large voting delay gives users time to unstake tokens if necessary.
    /// @return The duration of the voting delay.
    function votingDelay() public pure override returns (uint256) {
        return 7200; // 1 day
    }

    /// @notice How long does a proposal remain open to votes.
    /// @return The duration of the voting period.
    function votingPeriod() public pure override returns (uint256) {
        return 50_400; // 1 week
    }

    /// @notice The number of votes required in order for a voter to become a proposer.
    /// @return The number of votes required.
    function proposalThreshold() public pure override returns (uint256) {
        return 1_000_000_000 ether / 10_000; // 0.01% of Taiko Token
    }

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L108-L125

##

## [G-10] Remove ``nonReentrant`` modifier from admin only functions to save gas 

Removing the nonReentrant modifier from functions that are only accessible by the contract's owner or administrators can save gas, as these functions are less likely to be exposed to reentrancy attacks due to the controlled access.

Given this, removing the nonReentrant modifier could theoretically save you around 5,000 to 20,000 gas for the added state changes, depending on the original and new states of the involved storage slot.

```solidity
FILE: 

53: function setGuardians(
        address[] memory _newGuardians,
        uint8 _minGuardians
    )
        external
        onlyOwner
        nonReentrant
    {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L53-L60

##

## [G-11] Use assembly to validate msg.sender

use assembly to load the msg.sender value directly, which is more gas-efficient than using the msg.sender global variable.

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/common/AddressResolver.sol

25: if (msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressResolver.sol#L25

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/L2/TaikoL2.sol

123: if (msg.sender != GOLDEN_TOUCH_ADDRESS) revert L2_INVALID_SENDER();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L123

##

## [G-12] Don't cache global variable ``msg.sender``

Using global variables like msg.sender is more gas efficient than cache with local variable 

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/L1/hooks/AssignmentHook.sol

93: address taikoL1Address = msg.sender;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L93

## 

## [G-13] Invert if-else statements that have a negation

The extra ! increases the computational cost. Compiler is can sometimes optimize this.

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/bridge
/Bridge.sol

132: if (!destChainEnabled) revert B_INVALID_CHAINID();
171: if (!isMessageProven) {
174: if (!ISignalService(signalService).isSignalSent(address(this), msgHash)) {
179: if (!_proveSignalReceived(signalService, failureSignal, _message.destChainId, _proof)) {
209: } else if (!isMessageProven) {
235: if (!isMessageProven) {
302:  } else if (!isMessageProven) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L132


```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/L1/libs
/LibProving.sol

77: if (!_pause) {
420: if (!isAssignedPover) revert L1_NOT_ASSIGNED_PROVER();
 
```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L420

##

## [G-14] Assigning state variables directly with named struct constructors wastes gas

Using named arguments for struct means that the compiler needs to organize the fields in memory before doing the assignment, which wastes gas. Set each field directly in storage (use dot-notation), or use the unnamed version of the constructor.

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/bridge
/Bridge.sol

243: proofReceipt[msgHash] = ProofReceipt({
                    receivedAt: receivedAt,
                    preferredExecutor: _message.gasLimit == 0 ? _message.destOwner : msg.sender
                });

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L243-L246

##

## [G-15] Consider using alternatives to ``OpenZeppelin``

OpenZeppelin is a great and popular smart contract library, but there are other alternatives that are worth considering. These alternatives offer better gas efficiency and have been tested and recommended by developers.

Two examples of such alternatives are Solmate and Solady.

Solmate is a library that provides a number of gas-efficient implementations of common smart contract patterns. Solady is another gas-efficient library that places a strong emphasis on using assembly.

```
"@openzeppelin/contracts": "4.8.2",
    "@openzeppelin/contracts-upgradeable": "4.8.2",

```

##

## [G-16] Using assembly to revert with an error message

When reverting in solidity code, it is common practice to use a require or revert statement to revert execution with an error message. This can in most cases be further optimized by using assembly to revert with the error message. we get a gas saving of over ``300 gas`` when reverting the error message with assembly.

```solidity
File: packages/protocol/contracts/automataattestation/AutomataDcapV3Attestation.sol

61:         require(msg.sender == owner, "onlyOwner");

```


```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

77:         require(_key.length > 0, "MerkleTrie: empty key");

89:             require(currentKeyIndex <= key.length, "MerkleTrie: key index exceeds total key length");

191:                     revert("MerkleTrie: received a node with an unknown prefix");

194:                 revert("MerkleTrie: received an unparseable node");

198:         revert("MerkleTrie: ran out of proof elements");


```

##

## [G-17] Do-While loops are cheaper than for loops

 In solidity do-while loops are more gas efficient than for loops

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/bridge
/Bridge.sol

90: for (uint256 i; i < _msgHashes.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L90

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/L2
/TaikoL2.sol

234:  for (uint256 i; i < 255 && _blockId >= i + 1; ++i) {


```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L234
 
##

## [G-18] Short-circuit Booleans

In Solidity, when you evaluate a boolean expression (e.g the || (logical or) or && (logical and) operators), in the case of || the second expression will only be evaluated if the first expression evaluates to false and in the case of && the second expression will only be evaluated if the first expression evaluates to true. This is called short-circuiting.

Short-circuiting is useful and it’s recommended to place the less expensive expression first, as the more costly one might be bypassed. If the second expression is more important than the first, it might be worth reversing their order so that the cheaper one gets evaluated first.

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/L2
/TaikoL2.sol

141: if (!skipFeeCheck() && block.basefee != basefee) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L141


[Gas-01-01] via updating storage while emiting events
Via doing so * 21gas * can be saved with each emit

function setValidator(address _newValidator) external onlyOwner {
-       address oldValidator = validator;
-       validator = _newValidator;
-       emit NewValidator(oldValidator, _newValidator);


+       emit NewValidator(validator, validator = _newValidator);
    }

[Gas-04] Some require statement should be at top to save excess gas cost during


[G-06] Use assembly in place of abi.decode to extract calldata values more efficiently
Instead of using abi.decode, we can use assembly to decode our desired calldata values directly. This will allow us to avoid decoding calldata values that we will not use. Reffrence

There are 1 instance of this issue

File:  code/contracts/ethereum/contracts/zksync/libraries/Diamond.sol
303   require(abi.decode(data, (bytes32)) == DIAMOND_INIT_SUCCESS_RETURN_VALUE, "lp1");

[G-16] Use hardcode address instead address(this)

[G-17] bytes constants are more eficient than string constans

[G-26] Count from n to zero instead of counting from zero to n
When setting a storage variable to zero, a refund is given, so the net gas spent on counting will be less if the final state of the storage variable is zero. Reffrence https://www.rareskills.io/post/gas-optimization#viewer-dkmii:~:text=to%20one%20writes.-,13.%20Count%20from%20n%20to%20zero%20instead%20of%20counting%20from%20zero%20to%20n,-When%20setting%20a

[G-29] Test if a number is even or odd by checking the last bit instead of using a modulo operator
The conventional way to check if a number is even or odd is to do x % 2 == 0 where x is the number in question. You can instead check if x & uint256(1) == 0. where x is assumed to be a uint256. Bitwise and is cheaper than the modulo op code. In binary, the rightmost bit represents "1" whereas all the bits to the are multiples of 2, which are even. Adding "1" to an even number causes it to be odd.

File: code/contracts/ethereum/contracts/common/libraries/L2ContractHelper.sol
27   require(bytecodeLenInWords % 2 == 1, "ps"); // bytecode length in words must be odd

43   require(_bytecodeLen(_bytecodeHash) % 2 == 1, "uy"); // Code length in words must be odd











