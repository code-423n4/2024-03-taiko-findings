# GAS OPTIMIZATION REPORTS

##

## [G-] State variables only set in the constructor should be declared immutable

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

## [G-] Optimizing gas usage by caching state variables in local memory variables

The instances below point to the second+ access of a state variable within a function. Caching of a state variable replace each Gwarmaccess (100 gas) with a much cheaper stack read. Other less obvious fixes/optimizations include having local memory caches of state variable structs, or having local caches of state variable contracts/addresses. Most of the times this if statement will be true and we will save 100 gas at a small possibility of 3 gas loss

### [G-1.1] ``addressManager`` can be cached . Saves ``100 GAS`` , ``1 SLOD``

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

### [G-1.2] ``_state.slotA.numEthDeposits`` can be cached . Saves ``100 GAS`` , ``1 SLOD``

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

### [G-1.3] ``blk.blockId`` , ``blk.metaHash`` , ``blk.livenessBond``, ``_ts.contester``  can be cached  : ``700 GAS`` , ``7 SLODs``

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

### [G-1.4] ``ts.prover`` can be cached  : Saves ``200 GAS`` , ``2 SLODs``

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

### [G-1.5] ``version`` can be cached : Saves ``100 GAS`` , ``1 SLOD``

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

### [G-1.6] ``gasExcess`` , ``lastSyncedBlock`` can be cached  : Saves ``300 GAS`` , ``3 SLODs``

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

### ``migratingAddress`` can be cached : Saves ``300 GAS`` , ``3 SLODs``

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

### ``instances[idx].addr`` , ``nextInstanceId`` ``instances[id].validSince``  can be cached  : Saves ``400 GAS`` , ``4 SLODs``

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

## [G-] Using storage instead of memory for state variables saves gas

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

## [G-3] Cache the state variables outside the loop

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

## [G-] ``_newGuardians.length`` calculated multiple times 

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

## [G-] Using ``calldata`` instead of ``memory`` for read-only arguments in external functions saves gas

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





