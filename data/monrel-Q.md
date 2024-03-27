
## L-1: Consider allowing only the originator of the message to call `recallMessage()`

`_message.from` has not implemented the `IRecallAbleSender()` interface the recall will default to only sending the ETH available.

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L189-L207

```solidity
if (block.timestamp >= invocationDelay + receivedAt) {
            delete proofReceipt[msgHash];
            messageStatus[msgHash] = Status.RECALLED;

            // Execute the recall logic based on the contract's support for the
            // IRecallableSender interface
            if (_message.from.supportsInterface(type(IRecallableSender).interfaceId)) {
                _storeContext(msgHash, address(this), _message.srcChainId);

                // Perform recall
                IRecallableSender(_message.from).onMessageRecalled{ value: _message.value }(
                    _message, msgHash
                );

                // Must reset the context after the message call
                _resetContext();
            } else {
                _message.srcOwner.sendEther(_message.value);
            }
```

A user could prevent this from happening by implementing the interface before `recallMessage()` is called and by doing so they can recover the intended message. If only `message.from` can call `recallMessage()` we allow for this.

### L-2: It is not possible to set a designated relayer which could increase the bridging cost.

If it is possible to set a designated relayer which guarantees that only they can call `processMessage()` for a period of time we could possibly decrease the bridging fee since relayers don't have to compete and big against each other to be the first to call `processMessage()`.

The designated relayer will have a a priori guarantee that they will receive the fee and it will therefore not have to pay to be the first to call `processMessage()`. 

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L217

### L-3: Blob re-use can lead to potentially unpredictable commitments for provers

When blobs are re-used the prover could end up committing to a large number of different blocks if they are not careful with their assignments

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L141-L176

```solidity
if (meta_.blobUsed) {
            if (!_config.blobAllowedForDA) revert L1_BLOB_FOR_DA_DISABLED();

            if (params.blobHash != 0) {
                if (!_config.blobReuseEnabled) revert L1_BLOB_REUSE_DISABLED();

                // We try to reuse an old blob
                if (!isBlobReusable(_state, _config, params.blobHash)) {
                    revert L1_BLOB_NOT_REUSABLE();
                }
                meta_.blobHash = params.blobHash;
            } else {
                // Always use the first blob in this transaction. If the
                // proposeBlock functions are called more than once in the same
                // L1 transaction, these multiple L2 blocks will share the same
                // blob.
                meta_.blobHash = blobhash(0);

                if (meta_.blobHash == 0) revert L1_BLOB_NOT_FOUND();

                // Depends on the blob data price, it may not make sense to
                // cache the blob which costs 20,000 (sstore) + 631 (event)
                // extra gas.
                if (_config.blobReuseEnabled && params.cacheBlobForReuse) {
                    _state.reusableBlobs[meta_.blobHash] = block.timestamp;
                    emit BlobCached(meta_.blobHash);
                }
            }

            // Check that the txList data range is within the max size of a blob
            if (uint256(params.txListByteOffset) + params.txListByteSize > MAX_BYTES_PER_BLOB) {
                revert L1_TXLIST_OFFSET();
            }

            meta_.txListByteOffset = params.txListByteOffset;
            meta_.txListByteSize = params.txListByteSize;
```

If the prover does not specify the metaHash, parentHash and sets loose boundaries on maxBlockID and maxProposeIn

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L82-L86

```solidity
            block.timestamp > assignment.expiry
                || assignment.metaHash != 0 && _blk.metaHash != assignment.metaHash
                || assignment.parentMetaHash != 0 && _meta.parentMetaHash != assignment.parentMetaHash
                || assignment.maxBlockId != 0 && _meta.id > assignment.maxBlockId
                || assignment.maxProposedIn != 0 && block.number > assignment.maxProposedI
```

They can end up committing to multiple blocks of any subset of the transactions in the blob. 

### L-4: Incorrect validation on proposer for the first block

When proposing `_isProposerPermitted()` is called to check if the proposer is permitted

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L298-L318

```solidity

    function _isProposerPermitted(
        TaikoData.SlotB memory _slotB,
        IAddressResolver _resolver
    )
        private
        view
        returns (bool)
    {
        if (_slotB.numBlocks == 1) {
            // Only proposer_one can propose the first block after genesis
            address proposerOne = _resolver.resolve("proposer_one", true);
            if (proposerOne != address(0) && msg.sender != proposerOne) {
                return false;
            }
        }

        address proposer = _resolver.resolve("proposer", true);
        return proposer == address(0) || msg.sender == proposer;
    }
}
```

The second validation is unnecessary and could revert the call. We should not check if `proposer = msg.sender` if `proposerOne = msg.sender` for the first block. They could be different and this would revert this call.

```diff
if (_slotB.numBlocks == 1) {
	// Only proposer_one can propose the first block after genesis
	address proposerOne = _resolver.resolve("proposer_one", true);
+   if (msg.sender == proposerOne) {return true;}

```


### L-5: Guardian can not un-approve a hash

If a guardian discovers that the have signed an incorrect hash or maybe if key have been stolen it would add extra security if a guardian could un-approve a previously approved hash

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/GuardianProver.sol#L35-L55

```solidity
    function approve(
        TaikoData.BlockMetadata calldata _meta,
        TaikoData.Transition calldata _tran,
        TaikoData.TierProof calldata _proof
    )
        external
        whenNotPaused
        nonReentrant
        returns (bool approved_)
    {
        if (_proof.tier != LibTiers.TIER_GUARDIAN) revert INVALID_PROOF();
        bytes32 hash = keccak256(abi.encode(_meta, _tran));
        approved_ = approve(_meta.id, hash);

        if (approved_) {
            deleteApproval(hash);
            ITaikoL1(resolve("taiko", false)).proveBlock(_meta.id, abi.encode(_meta, _tran, _proof));
        }

        emit GuardianApproval(msg.sender, _meta.id, _tran.blockHash, approved_);
    }
```

### L-6: We do not validate between the grant  and unlock parameters

When granting `validateGrant()` is called where we validate that the parameters for grant and unlock are valid

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L267-L271

```solidity
    function _validateGrant(Grant memory _grant) private pure {
        if (_grant.amount == 0) revert INVALID_GRANT();
        _validateCliff(_grant.grantStart, _grant.grantCliff, _grant.grantPeriod);
        _validateCliff(_grant.unlockStart, _grant.unlockCliff, _grant.unlockPeriod);
    
```

We do not validate between grant and unlock. E.g. an unlock with a cliff that is finished before the grant starts makes no sense and is a sign that the wrong parameters has been entered.

### L-6: The entire hook array should be passed to the AssigmentHooks to protect against conflicting hooks.

Provers and proposer will create their own hooks some of those hooks could interfere with each other.

En example of such a hook would be a hook that relies on swapping on a DEX to acquire TKO  directly in the hook. The prover could allow the proposer to pass in arbitrary data to swap on an any DEX. The prover relies entirely on the check after the hook has executed to guarantee that the correct amount of TKO has been transferred

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L268-L270

```solidity
            if (tko.balanceOf(address(this)) != tkoBalance + _config.livenessBond) {
                revert L1_LIVENESS_BOND_NOT_RECEIVED();
            
```


A proposer could potentially call both these hooks that are independently safe to steal funds from the prover.

Proposer calls both AssigmentHooks in the loop

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L244-L271

```solidity
for (uint256 i; i < params.hookCalls.length; ++i) {
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
            // Refund Ether
            if (address(this).balance != 0) {
                msg.sender.sendEther(address(this).balance);
            }

            // Check that after hooks, the Taiko Token balance of this contract
            // have increased by the same amount as _config.livenessBond (to prevent)
            // multiple draining payments by a malicious proposer nesting the same
            // hook.
            if (tko.balanceOf(address(this)) != tkoBalance + _config.livenessBond) {
                revert L1_LIVENESS_BOND_NOT_RECEIVED();
            }
        }
```

Example:

1. AssigmentHook is first called and transfers liveness bond
2. DexAssigmentHook is then called, proposer passes fake DEX data to steal the funds.
3. proposeBlock() does not revert since the first AssigmentHook provided the liveness bond

AssigmentHook and DexAssigmentHook are both safe in isolation but when combined they can be used to steal funds from the prover.

There is of course also the requirement that the prover is actively using both AssigmentHook and that there is some overlap in the signed assignment such that both are valid at the same time.

We can protect against this by passing the entire hook array when calling 

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L253-L255

```solidity
                IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }(
                    blk, meta_, params.hookCalls[i].data
                )
```

by doing so each AssigmentHook can add assignments to their signature that enforce a specific execution of hooks.