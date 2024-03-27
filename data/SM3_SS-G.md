


# Gas Optimizations

| Number | Issue | Instences |
|--------|-------|-----------|
|[G-01]| Consider using OpenZeppelin's EnumerateSet instead of nested mappings | 8 |
|[G-02]| Use assembly to emit an event | 55 | 
|[G-03]| Multiple accesses of the same mapping/array key/index should be cached | 18 |
|[G-04]| Using assembly to revert with an error message | 57 |
|[G-05]| Cache storage variables: write and read storage variables exactly once | 15 |
|[G-06]| Using mappings instead of arrays to avoid length checks | 3 |
|[G-07]| Make constructors payable | 3 |
|[G-08]| Custom errors are (usually) smaller than require statements | 57 |
|[G-09]| Use inline assembly to check for address(0) | 67 |
|[G-10]| Do-While loops are cheaper than for loops | 23 |
|[G-11]| Call msg.sender directly instead of caching them | 1 |
|[G-12]| Use uint8 Can Increase Gas Cost | 55 |
|[G-13]| Store Data in calldata Instead of Memory for Certain Function Parameters  | 120 |
|[G-14]| Using bytes32 is cheaper than using string. | 40 |
|[G-15]| Avoid Unnecessary Use of Storage | 5 |
|[G-16]| Precompute Off-Chain When Possible | 35 |
|[G-17]| abi.encode() is less efficient than abi.encodePacked() | 18 |
|[G-18]| Alternative Solady library can be used instead of OpenZeppelin to save gas | 2 |
|[G-19]| Avoid unnecessary public variables | 2 |
|[G-20]| Consider pre-calculating the address of address(this) | 41 |
|[G-21]| Counting down in for statements is more gas efficient | 43 |
|[G-22]| Do not calculate constants | 2 |
|[G-23]| do-while is cheaper than for-loops when the initial check can be skipped | 43 |
|[G-24]| Empty blocks should be removed or emit something | 5 |
|[G-25]| Nesting if-statements is cheaper than using && | 28 |
|[G-26]| Struct can be reordered to fit into fewer storage slots | 9 |
|[G-27]| Use assembly for small keccak256 hashes, in order to save gas | 10 |
|[G-28]| Use assembly in place of abi.decode to save gas | 16 |
|[G-29]| Use assembly to validate msg.sender | 17 |
|[G-30]| Use assembly to write address/contract storage values | 15 |
|[G-31]| Use selfbalance() instead of address(this).balance | 5 |
|[G-32]| Use uint256(1)/uint256(2) instead of true/false to save gas for changes | 95 |
|[G-33]| Using storage instead of memory for structs/arrays saves gas | 32 |
|[G-34]| State variables can be packed into fewer storage slots | 3 |
|[G-35]| Multiple mappings that share an ID can be combined into a single mapping of ID / struct | 2 |
|[G-36]| Cache state variables outside of loop to avoid reading storage on every iteration | 3 |
|[G-37]| Pre-calculate keccak256 for constant variables  | 3 |
|[G-38]| Use constants instead of type(uintX).max | 14 |
|[G-39]| Use of emit inside a loop | 2 |
|[G-40]| Consider Merge Sequential For-Loops | 4 |
|[G-41]| Mappings not used externally/internally can be marked private | 2 |
|[G-42]| Redundant state variable getters | 1 |
|[G-43]| Use assembly for loops | 26 |
|[G-44]| require()/revert() strings longer than 32 bytes cost extra gas | 57 |


## [G-01] Consider using OpenZeppelin's EnumerateSet instead of nested mappings

Nested mappings and multi-dimensional arrays in Solidity operate through a process of double hashing, wherein the original storage slot and the first key are concatenated and hashed, and then this hash is again concatenated with the second key and hashed. This process can be quite gas expensive due to the double-hashing operation and subsequent storage operation (sstore).

OpenZeppelin's EnumerableSet provides a potential solution to this problem. It creates a data structure that combines the benefits of set operations with the ability to enumerate stored elements, which is not natively available in Solidity. EnumerableSet handles the element uniqueness internally and can therefore provide a more gas-efficient and collision-resistant alternative to nested mappings or multi-dimensional arrays in certain scenarios.

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

47  mapping(uint256 idx => mapping(bytes serialNum => bool revoked)) private _serialNumIsRevoked;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L47

```solidity
file: blob/main/packages/protocol/contracts/common/AddressManager.sol

12   mapping(uint256 chainId => mapping(bytes32 name => address addr)) private __addresses;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L12

```solidity
file: blob/main/packages/protocol/contracts/L1/TaikoData.sol

183  mapping(uint64 blockId => mapping(bytes32 parentHash => uint32 transitionId)) transitionIds;

185  mapping(
            uint64 blockId_mod_blockRingBufferSize
                => mapping(uint32 transitionId => TransitionState ts)
            ) transitions;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L183

```solidity
file: blob/main/packages/protocol/contracts/L1/provers/Guardians.sol

19   mapping(uint32 version => mapping(bytes32 hash => uint256 approvalBits)) internal _approvals;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L19

```solidity
file: blob/main/packages/protocol/contracts/signal/SignalService.sol

17   mapping(uint64 chainId => mapping(bytes32 kind => uint64 blockId)) public topBlockId;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L17

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol

59  mapping(uint256 chainId => mapping(address ctoken => address btoken)) public canonicalToBridged;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L59

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol
 
49   mapping(uint256 chainId => mapping(address ctoken => address btoken)) public canonicalToBridged;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L49

## [G-02] Use assembly to emit an event

To efficiently emit events, it's possible to utilize assembly by making use of scratch space and the free memory pointer. This approach has the advantage of potentially avoiding the costs associated with memory expansion.

However, it's important to note that in order to safely optimize this process, it is preferable to cache and restore the free memory pointer.

A good example of such practice can be seen in Solady's(https://github.com/Vectorized/solady/blob/main/src/tokens/ERC1155.sol#L167) codebase.


```solidity
file: blob/main/packages/protocol/contracts/bridge/Bridge.sol

93   emit MessageSuspended(msgHash, _suspend);

111  emit AddressBanned(_addr, _ban);

151  emit MessageSent(msgHash_, message_);

208  emit MessageRecalled(msgHash);

210  emit MessageReceived(msgHash, _message, true);

301  emit MessageExecuted(msgHash);

303  emit MessageReceived(msgHash, _message, false);

336  emit MessageRetried(msgHash);

519  emit MessageStatusChanged(_msgHash, _status);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L93

```solidity
file: blob/main/packages/protocol/contracts/common/AddressManager.sol

50   emit AddressSet(_chainId, _name, _newAddress, oldAddress);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L50

```solidity
file: blob/main/packages/protocol/contracts/common/EssentialContract.sol

71  emit Paused(msg.sender);

80  emit Unpaused(msg.sender);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L71

```solidity
file: blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol

129   emit BlockAssigned(_blk.assignedProver, _meta, assignment);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L129

```solidity
file: blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol

50   emit EthDeposited(

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L50

```solidity
file: blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol

166  emit BlobCached(meta_.blobHash);

273  emit BlockProposed({

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L166

```solidity
file: blob/main/packages/protocol/contracts/L1/libs/LibProving.sol

80  emit ProvingPaused(_pause);

209 emit TransitionProved({

230 emit TransitionProved({

254 emit TransitionContested({

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L80

```solidity 
file: blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol

73  emit BlockVerified({

198 emit BlockVerified({

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L73

```solidity
file: blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol

54   emit GuardianApproval(msg.sender, _meta.id, _tran.blockHash, approved_);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L54

```solidity
file: blob/main/packages/protocol/contracts/L1/provers/Guardians.sol

95   emit GuardiansUpdated(version, _newGuardians);

121  emit Approved(_operationId, _approval, approved_);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L95

```solidity
file: blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol

53   emit TransactionExecuted(nextTxId++, bytes4(txdata));

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L53

```solidity
file: blob/main/packages/protocol/contracts/L2/TaikoL2.sol

157  emit Anchored(blockhash(parentId), gasExcess);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L157

```solidity
file: blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

39   emit ConfigAndExcessChanged(_newConfig, _newGasExcess);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L39

```solidity
file: blob/main/packages/protocol/contracts/signal/SignalService.sol

59   emit Authorized(_addr, _authorize);

250  emit ChainDataSynced(_chainId, _blockId, _kind, _chainData, signal_);

268  emit SignalSent(_app, _signal, slot_, _value);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L50


```solidity
file: blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol

143  emit Granted(_recipient, _grant);

157  emit Voided(_recipient, amountVoided);

222  emit Withdrawn(_recipient, _to, amountToWithdraw, costToWithdraw);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L143

```solidity
file: blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

93   emit Withdrawn(user, amount);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L93

```solidity
file: blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

74   emit Claimed(hash);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L74

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

51  emit MigrationStatusChanged(_migratingAddress, _migratingInbound);

63  emit MigratedTo(migratingAddress, _account, _amount);

80  emit MigratedTo(migratingAddress, _account, _amount);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L51


```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol

191  emit BridgedTokenChanged({

241  emit TokenSent({

273  emit TokenReceived({

306  emit TokenReleased({

425  emit BridgedTokenDeployed({

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L191

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol

64   emit TokenSent({

97   emit TokenReceived({

131  emit TokenReleased({

250  emit BridgedTokenDeployed({

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L64

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol

80  emit TokenSent({

114 emit TokenReceived({

149 emit TokenReleased({

314 emit BridgedTokenDeployed({

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L80

```solidity
file: blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol

109  emit InstanceDeleted(idx, instances[idx].addr);

220  emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);

230  emit InstanceAdded(id, newInstance, oldInstance, block.timestamp);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L109

## [G-03] Multiple accesses of the same mapping/array key/index should be cached

The instances below point to the second+ access of a value inside a mapping/array key/index, within a function. Caching a mapping's value in a local storage or calldata variable when the value is accessed multiple times,


```solidity
file: blob/main/packages/protocol/contracts/bridge/Bridge.sol

/// @audit messageStatus[msgHash] is also accessed on line 191

166  if (messageStatus[msgHash] != Status.NEW) revert B_STATUS_MISMATCH();

/// @audit messageStatus[_msgHash] is also accessed on line 518

512  if (messageStatus[_msgHash] == _status) return;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L166

```solidity
file: blob/main/packages/protocol/contracts/bridge/Bridge.sol

/// @audit addressBanned[_addr] is also accessed on line 110

109  if (addressBanned[_addr] == _ban) revert B_INVALID_STATUS();

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L109

```solidity
file: blob/main/packages/protocol/contracts/signal/SignalService.sol

/// @audit topBlockId[_chainId][_kind]  is also accessed on line 248  

247   if (topBlockId[_chainId][_kind] < _blockId) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L247

```solidity
file: blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol

/// @audit _instances[i] is also accessed on line 213,215,217 and line 220

211  if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L211


```solidity
file: blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol

/// @audit _instances[i] is also accessed on line 236 and line 237

235  if (instance != instances[id].addr) return false;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L235


```solidity
file: blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol

/// @audit addressRegistered[_instances[i]] is also accessed on line 213

211  if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L211

```solidity
file: blob/main/packages/protocol/contracts/signal/SignalService.sol

/// @audit isAuthorized[_addr]  is also accessed on line 58 

57  if (isAuthorized[_addr] == _authorize) revert SS_INVALID_STATE();

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L57


```solidity
file: blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol

/// @audit recipients[_recipient]  is also accessed on line 142 

137  if (recipients[_recipient].grant.amount != 0) revert ALREADY_GRANTED();

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L137

```solidity
file: blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

/// @audit isClaimed[hash] is also accessed on line 73 

70  if (isClaimed[hash]) revert CLAIMED_ALREADY();

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L70

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol

/// @audit bridgedToCanonical[_btokenNew] is also accessed on line 180 and line 188 

158  if (_btokenNew == address(0) || bridgedToCanonical[_btokenNew].addr != address(0)) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L158

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol

/// @audit bridgedToCanonical[_token] is also accessed on line 359

358  if (bridgedToCanonical[_token].addr != address(0)) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L358

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol

/// @audit canonicalToBridged[_ctoken.chainId][_ctoken.addr] is also accessed on line 189

168  btokenOld_ = canonicalToBridged[_ctoken.chainId][_ctoken.addr];

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L168

```solidity
file: blob/main/packages/protocol/contracts/L1/provers/Guardians.sol

/// @audit guardianIds[guardian] is also accessed on line 88    

84  if (guardianIds[guardian] != 0) revert INVALID_GUARDIAN_SET();

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L84

```solidity
file: blob/main/packages/protocol/contracts/L1/provers/Guardians.sol

/// @audit _approvals[version][_hash] is also accessed on line 119

116    _approvals[version][_hash] |= 1 << (id - 1);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L116

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

/// @audit _serialNumIsRevoked[index][serialNumBatch[i]] is also accessed on line 84

81  if (_serialNumIsRevoked[index][serialNumBatch[i]]) {

/// @audit _serialNumIsRevoked[index][serialNumBatch[i]] is also accessed on line 99

96  if (!_serialNumIsRevoked[index][serialNumBatch[i]]) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L81

```solidity
file: blob/main/packages/protocol/contracts/bridge/Bridge.sol

/// @audit proofReceipt[msgHash] is also accessed on line 184 and line 190

168  uint64 receivedAt = proofReceipt[msgHash].receivedAt;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L168

### use __addresses[_chainId][_name] mappping cached value instead of updating them from storage 
```solidity
file: blob/main/packages/protocol/contracts/common/AddressManager.sol

47      address oldAddress = __addresses[_chainId][_name];
        if (_newAddress == oldAddress) revert AM_INVALID_PARAMS();
        __addresses[_chainId][_name] = _newAddress;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L47-L50

## [G-04] Using assembly to revert with an error message

When reverting in solidity code, it is common practice to use a require or revert statement to revert execution with an error message. This can in most cases be further optimized by using assembly to revert with the error message.

Here’s an example;

<details> 

```solidity
/// calling restrictedAction(2) with a non-owner address: 24042
contract SolidityRevert {
    address owner;
    uint256 specialNumber = 1;

    constructor() {
        owner = msg.sender;
    }

    function restrictedAction(uint256 num)  external {
        require(owner == msg.sender, "caller is not owner");
        specialNumber = num;
    }
}

/// calling restrictedAction(2) with a non-owner address: 23734
contract AssemblyRevert {
    address owner;
    uint256 specialNumber = 1;

    constructor() {
        owner = msg.sender;
    }

    function restrictedAction(uint256 num)  external {
        assembly {
            if sub(caller(), sload(owner.slot)) {
                mstore(0x00, 0x20) // store offset to where length of revert message is stored
                mstore(0x20, 0x13) // store length (19)
                mstore(0x40, 0x63616c6c6572206973206e6f74206f776e657200000000000000000000000000) // store hex representation of message
                revert(0x00, 0x60) // revert with data
            }
        }
        specialNumber = num;
    }
}

```

</details>

From the example above we can see that we get a gas saving of over 300 gas when reverting wth the same error message with assembly against doing so in solidity. This gas savings come from the memory expansion costs and extra type checks the solidity compiler does under the hood.

```solidity
file:  blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

37  require(
            _in.length > 0,
            "RLPReader: length of an RLP item must be greater than zero to be decodable"
        );

56  require(
            itemType == RLPItemType.LIST_ITEM,
            "RLPReader: decoded item type for list is not a list item"
        );

61  require(
            listOffset + listLength == _in.length,
            "RLPReader: list item has an invalid data remainder"
        );

112  require(
            itemType == RLPItemType.DATA_ITEM,
            "RLPReader: decoded item type for bytes is not a data item"
        );

117  require(
            _in.length == itemOffset + itemLength,
            "RLPReader: bytes value contains an invalid remainder"
        );

152  require(
            _in.length > 0,
            "RLPReader: length of an RLP item must be greater than zero to be decodable"
        );

172  require(
                _in.length > strLen,
                "RLPReader: length of content must be greater than string length (short string)"
            );

182  require(
                strLen != 1 || firstByteOfContent >= 0x80,
                "RLPReader: invalid prefix, single byte < 0x80 are not prefixed (short string)"
            );

192  require(
                _in.length > lenOfStrLen,
                "RLPReader: length of content must be > than length of string length (long string)"
            );

202  require(
                firstByteOfContent != 0x00,
                "RLPReader: length of content must not have any leading zeros (long string)"
            );

212  require(
                strLen > 55,
                "RLPReader: length of content must be greater than 55 bytes (long string)"
            );

217  require(
                _in.length > lenOfStrLen + strLen,
                "RLPReader: length of content must be greater than total length (long string)"
            );

228  require(
                _in.length > listLen,
                "RLPReader: length of content must be greater than list length (short list)"
            );

238  require(
                _in.length > lenOfListLen,
                "RLPReader: length of content must be > than length of list length (long list)"
            );

248  require(
                firstByteOfContent != 0x00,
                "RLPReader: length of content must not have any leading zeros (long list)"
            );

258  require(
                listLen > 55,
                "RLPReader: length of content must be greater than 55 bytes (long list)"
            );

263  require(
                _in.length > lenOfListLen + listLen,
                "RLPReader: length of content must be greater than total length (long list)"
            );

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L37-L40

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol
 
77  require(
            localEnclaveReport.reserved3.length == 96 && localEnclaveReport.reserved4.length == 60
                && localEnclaveReport.reportData.length == 64,
            "local QE report has wrong length"
        );

82  require(
            pckSignedQeReport.reserved3.length == 96 && pckSignedQeReport.reserved4.length == 60
                && pckSignedQeReport.reportData.length == 64,
            "QE report has wrong length"
        );

87  require(
            v3Quote.v3AuthData.certification.certType == 5,
            "certType must be 5: Concatenated PCK Cert Chain (PEM formatted)"
        );

94  require(
            v3Quote.v3AuthData.ecdsa256BitSignature.length == 64
                && v3Quote.v3AuthData.ecdsaAttestationKey.length == 64
                && v3Quote.v3AuthData.qeReportSignature.length == 64,
            "Invalid ECDSA signature format"
        );

100  require(
            v3Quote.v3AuthData.qeAuthData.parsedDataSize
                == v3Quote.v3AuthData.qeAuthData.data.length,
            "Invalid QEAuthData size"
        );

116   require(totalQuoteSize >= MINIMUM_QUOTE_LENGTH, "Invalid quote size");

279   require(certParsedSuccessfully, "splitCertificateChain failed");

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L77-L81


```solidity
file: blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

77  require(_key.length > 0, "MerkleTrie: empty key");

89  require(currentKeyIndex <= key.length, "MerkleTrie: key index exceeds total key length");

93  require(
                    Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
                    "MerkleTrie: invalid root hash"
                );

99  require(
                    Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
                    "MerkleTrie: invalid large internal hash"
                );

105  require(
                    Bytes.equal(currentNode.encoded, currentNodeID),
                    "MerkleTrie: invalid internal node hash"
                );

119  require(
                        value_.length > 0,
                        "MerkleTrie: value length must be greater than zero (branch)"
                    );

125  require(
                        i == proof.length - 1,
                        "MerkleTrie: value node must be last node in proof (branch)"
                    );

150  require(
                    pathRemainder.length == sharedNibbleLength,
                    "MerkleTrie: path remainder must share all nibbles with key"
                );

162  require(
                        keyRemainder.length == sharedNibbleLength,
                        "MerkleTrie: key remainder must be identical to path remainder"
                    );

172  require(
                        value_.length > 0,
                        "MerkleTrie: value length must be greater than zero (leaf)"
                    );

178  require(
                        i == proof.length - 1,
                        "MerkleTrie: value node must be last node in proof (leaf)"
                    );

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L77

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

57   require(der[ptr.ixs()] == 0x03, "Not type BIT STRING");

67   require(der[ptr.ixs()] == 0x04, "Not type OCTET STRING");

88   require(der[ptr.ixs()] & 0x20 == 0x20, "Not a constructed type");

142  require(der[ptr.ixs()] == 0x02, "Not type INTEGER");

155  require(der[ptr.ixs()] == 0x02, "Not type INTEGER");

180  require(der[ptr.ixs()] == 0x03, "ixs Not type BIT STRING 0x03");

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L57

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

25  require(offset + len <= self.length, "invalid offset");

199 require(idx + 2 <= self.length, "invalid idx");

212 require(idx + 4 <= self.length, "unexpected idx");

225 require(idx + 32 <= self.length, "unexpected idx");

238 require(idx + 20 <= self.length, "unexpected idx");

264 require(len <= 32, "unexpected len");

265 require(idx + len <= self.length, "unexpected idx");

293 require(offset + len <= self.length, "unexpected offset");

329 require(len <= 52, "unexpected len");

335 require(char >= 0x30 && char <= 0x7A, "invalid char");

337 require(decoded <= 0x20, "invalid decoded");

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L25

```solidity
file: blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol

25  require(_length + 31 >= _length, "slice_overflow");

26  require(_start + _length >= _start, "slice_overflow");

27  require(_bytes.length >= _start + _length, "slice_outOfBounds");

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L25


## [G-05] Cache storage variables: write and read storage variables exactly once

You will see the following pattern frequently in efficient solidity code. Reading from a storage variable costs at least 100 gas as Solidity does not cache the storage read. Writes are considerably more expensive. Therefore, you should manually cache the variable to do exactly one storage read and exactly one storage write.

<details>

```solidity
// SPDX-License-Identifier: MIT
pragma solidity 0.8.20;

contract Counter1 {
    uint256 public number;

    function increment() public {
        require(number < 10);
        number = number + 1;
    }
}

contract Counter2 {
    uint256 public number;

    function increment() public {
        uint256 _number = number;
        require(_number < 10);
        number = _number + 1;
    }
}

```

</details>

### cache the addressManager state variable in memory variable 

```solidity
file: blob/main/packages/protocol/contracts/common/AddressResolver.sol

80  {
        if (addressManager == address(0)) revert RESOLVER_INVALID_MANAGER();

        addr_ = payable(IAddressManager(addressManager).getAddress(_chainId, _name));

        if (!_allowZeroAddress && addr_ == address(0)) {
            revert RESOLVER_ZERO_ADDR(_chainId, _name);
        }
    }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L80-L88


### cache the state variable in memory variable in  TaikoL1.proposeBlock()

```solidity
file:  blob/main/packages/protocol/contracts/L1/TaikoL1.sol

66  
        (meta_, deposits_) = LibProposing.proposeBlock(state, config, this, _params, _txList);

        if (!state.slotB.provingPaused) {
            LibVerifying.verifyBlocks(state, config, this, config.maxBlocksToVerifyPerProposal);
        }
    }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L66-L71

### cache the nextTxId state variable in memory variable 

```solidity
file: blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol

43   if (txId != nextTxId) revert XCO_INVALID_TX_ID();

        IBridge.Context memory ctx = IBridge(msg.sender).context();
        if (ctx.srcChainId != ownerChainId || ctx.from != owner()) {
            revert XCO_PERMISSION_DENIED();
        }

        (bool success,) = address(this).call(txdata);
        if (!success) revert XCO_TX_REVERTED();

        emit TransactionExecuted(nextTxId++, bytes4(txdata));
    }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L43-L54

### cache the gasExcess,lastSyncedBlock and publicInputHash state variables in memory variable to save gas 

```solidity
file: blob/main/packages/protocol/contracts/L2/TaikoL2.sol

132  if (publicInputHash != publicInputHashOld) {
            revert L2_PUBLIC_INPUT_HASH_MISMATCH();
        }

        Config memory config = getConfig();

        // Verify the base fee per gas is correct
        uint256 basefee;
        (basefee, gasExcess) = _calc1559BaseFee(config, _l1BlockId, _parentGasUsed);
        if (!skipFeeCheck() && block.basefee != basefee) {
            revert L2_BASEFEE_MISMATCH();
        }

        if (_l1BlockId > lastSyncedBlock + BLOCK_SYNC_THRESHOLD) {
            // Store the L1's state root as a signal to the local signal service to
            // allow for multi-hop bridging.
            ISignalService(resolve("signal_service", false)).syncChainData(
                ownerChainId, LibSignals.STATE_ROOT, _l1BlockId, _l1StateRoot
            );
            lastSyncedBlock = _l1BlockId;
        }
        // Update state variables
        l2Hashes[parentId] = blockhash(parentId);
        publicInputHash = publicInputHashNew;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L132-L155


### cache the gasExcess and lastSyncedBlock  state variables in memory variable to save gas in function TaikoL2._calc1559BaseFee()


```solidity
file: blob/main/packages/protocol/contracts/L2/TaikoL2.sol

262   if (gasExcess > 0) {
            // We always add the gas used by parent block to the gas excess
            // value as this has already happened
            uint256 excess = uint256(gasExcess) + _parentGasUsed;

            // Calculate how much more gas to issue to offset gas excess.
            // after each L1 block time, config.gasTarget more gas is issued,
            // the gas excess will be reduced accordingly.
            // Note that when lastSyncedBlock is zero, we skip this step
            // because that means this is the first time calculating the basefee
            // and the difference between the L1 height would be extremely big,
            // reverting the initial gas excess value back to 0.
            uint256 numL1Blocks;
            if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {
                numL1Blocks = _l1BlockId - lastSyncedBlock;
            }

            if (numL1Blocks > 0) {
                uint256 issuance = numL1Blocks * _config.gasTargetPerL1Block;
                excess = excess > issuance ? excess - issuance : 1;
            }

            gasExcess_ = uint64(excess.min(type(uint64).max));

            // The base fee per gas used by this block is the spot price at the
            // bonding curve, regardless the actual amount of gas used by this
            // block, however, this block's gas used will affect the next
            // block's base fee.
            basefee_ = Lib1559Math.basefee(
                gasExcess_, uint256(_config.basefeeAdjustmentQuotient) * _config.gasTargetPerL1Block
            );
        }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L262-L293

### cache the token state variable in memory variable to save gas

```solidity
file: blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

63      IERC20(token).transferFrom(vault, user, amount);

        // Delegate the voting power to delegatee.
        // Note that the signature (v,r,s) may not correspond to the user address,
        // but since the data is provided by Taiko backend, it's not an issue even if
        // client can change the data to call delegateBySig for another user.
        (address delegatee, uint256 nonce, uint256 expiry, uint8 v, bytes32 r, bytes32 s) =
            abi.decode(delegationData, (address, uint256, uint256, uint8, bytes32, bytes32));
        IVotes(token).delegateBySig(delegatee, nonce, expiry, v, r, s);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L63-L71


### cache the withdrawalWindow state variable in memory variable to save gas

```solidity
file: blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

117     uint256 timeBasedAllowance = balance
            * (block.timestamp.min(claimEnd + withdrawalWindow) - claimEnd) / withdrawalWindow;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L117-L118

### cache the sharedVault state variable in memory variable to save gas

```solidity
file:  blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol

219     IERC20(taikoToken).transferFrom(sharedVault, _to, amountToWithdraw);
        IERC20(costToken).safeTransferFrom(_recipient, sharedVault, costToWithdraw);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L219-L220

### cache the _grant state variable in memory variable to save gas

```solidity
file:  blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol

226     uint128 amountOwned = _getAmountOwned(_grant);

        amountVoided = _grant.amount - amountOwned;
        _grant.amount = amountOwned;

        _grant.grantStart = 0;
        _grant.grantPeriod = 0;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L226-L232

### cache the usdc state variable in memory variable to save gas

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

48   usdc.transferFrom(_from, address(this), _amount);
        usdc.burn(_amount);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L48-L49

### cache the migratingAddress and migratingInbound state variables in memory variable to save gas

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

45          if (_migratingAddress == migratingAddress && _migratingInbound == migratingInbound) {
            revert BB_INVALID_PARAMS();
        }

        migratingAddress = _migratingAddress;
        migratingInbound = _migratingInbound;

61  if (msg.sender == migratingAddress) {
            // Inbound migration
            emit MigratedTo(migratingAddress, _account, _amount);
        } else if (msg.sender != resolve("erc20_vault", true)) {
            // Bridging from vault
            revert BB_PERMISSION_DENIED();
        }

80    emit MigratedTo(migratingAddress, _account, _amount);
       // Ask the new bridged token to mint token for the user.
      IBridgedERC20(migratingAddress).mint(_account, _amount);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L45-L50

### cache the nextInstanceId  state variable in memory variable to save gas


```solidity
file:  blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol

210          for (uint256 i; i < _instances.length; ++i) {
            if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();

            addressRegistered[_instances[i]] = true;

            if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();

            instances[nextInstanceId] = Instance(_instances[i], validSince);
            ids[i] = nextInstanceId;

            emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);

            nextInstanceId++;
        }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210-L223

## [G-06] Using mappings instead of arrays to avoid length checks

When storing a list or group of items that you wish to organize in a specific order and fetch with a fixed key/index, it’s common practice to use an array data structure. This works well, but did you know that a trick can be implemented to save 2,000+ gas on each read using a mapping?


See the example below

<details>

```solidity

/// get(0) gas cost: 4860 
contract Array {
    uint256[] a;

    constructor() {
        a.push() = 1;
        a.push() = 2;
        a.push() = 3;
    }

    function get(uint256 index) external view returns(uint256) {
        return a[index];
    }
}

/// get(0) gas cost: 2758
contract Mapping {
    mapping(uint256 => uint256) a;

    constructor() {
        a[0] = 1;
        a[1] = 2;
        a[2] = 3;
    }

    function get(uint256 index) external view returns(uint256) {
        return a[index];
    }
}

```

</details>

Just by using a mapping, we get a gas saving of 2102 gas. Why? Under the hood when you read the value of an index of an array, solidity adds bytecode that checks that you are reading from a valid index (i.e an index strictly less than the length of the array) else it reverts with a panic error (Panic(0x32) to be precise). This prevents from reading unallocated or worse, allocated storage/memory locations.


Due to the way mappings are (simply a key => value pair), no check like that exists and we are able to read from the a storage slot directly. It’s important to note that when using mappings in this manner, your code should ensure that you are not reading an out of bound index of your canonical array.

```solidity
file: blob/main/packages/protocol/contracts/L1/provers/Guardians.sol

23   address[] public guardians;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L23

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol

33  uint256[] tokenIds;

35  uint256[] amounts;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L33

## [G-07] Make constructors payable

Making the constructor payable saved 200 gas on deployment. This is because non-payable functions have an implicit require(msg.value == 0) inserted in them. Additionally, fewer bytecode at deploy time mean less gas cost due to smaller calldata.
There are good reasons to make a regular functions non-payable, but generally a contract is deployed by a privileged address who you can reasonably assume won’t send ether. This might not apply if inexperienced users are deploying the contract.

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

54   constructor(address sigVerifyLibAddr, address pemCertLibAddr) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L54

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

20   constructor(address es256Verifier) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L20

```solidity
file: blob/main/packages/protocol/contracts/common/EssentialContract.sol

64   constructor() {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L64

## [G-08] Custom errors are (usually) smaller than require statements

Custom errors are cheaper than require statements with strings because of how custom errors are handled. Solidity stores only the first 4 bytes of the hash of the error signature and returns only that. This means during reverting, only 4 bytes needs to be stored in memory. In the case of string messages in require statements, Solidity has to store(in memory) and revert with at least 64 by

```solidity
file:  blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

37  require(
            _in.length > 0,
            "RLPReader: length of an RLP item must be greater than zero to be decodable"
        );

56  require(
            itemType == RLPItemType.LIST_ITEM,
            "RLPReader: decoded item type for list is not a list item"
        );

61  require(
            listOffset + listLength == _in.length,
            "RLPReader: list item has an invalid data remainder"
        );

112  require(
            itemType == RLPItemType.DATA_ITEM,
            "RLPReader: decoded item type for bytes is not a data item"
        );

117  require(
            _in.length == itemOffset + itemLength,
            "RLPReader: bytes value contains an invalid remainder"
        );

152  require(
            _in.length > 0,
            "RLPReader: length of an RLP item must be greater than zero to be decodable"
        );

172  require(
                _in.length > strLen,
                "RLPReader: length of content must be greater than string length (short string)"
            );

182  require(
                strLen != 1 || firstByteOfContent >= 0x80,
                "RLPReader: invalid prefix, single byte < 0x80 are not prefixed (short string)"
            );

192  require(
                _in.length > lenOfStrLen,
                "RLPReader: length of content must be > than length of string length (long string)"
            );

202  require(
                firstByteOfContent != 0x00,
                "RLPReader: length of content must not have any leading zeros (long string)"
            );

212  require(
                strLen > 55,
                "RLPReader: length of content must be greater than 55 bytes (long string)"
            );

217  require(
                _in.length > lenOfStrLen + strLen,
                "RLPReader: length of content must be greater than total length (long string)"
            );

228  require(
                _in.length > listLen,
                "RLPReader: length of content must be greater than list length (short list)"
            );

238  require(
                _in.length > lenOfListLen,
                "RLPReader: length of content must be > than length of list length (long list)"
            );

248  require(
                firstByteOfContent != 0x00,
                "RLPReader: length of content must not have any leading zeros (long list)"
            );

258  require(
                listLen > 55,
                "RLPReader: length of content must be greater than 55 bytes (long list)"
            );

263  require(
                _in.length > lenOfListLen + listLen,
                "RLPReader: length of content must be greater than total length (long list)"
            );

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L37-L40

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol
 
77  require(
            localEnclaveReport.reserved3.length == 96 && localEnclaveReport.reserved4.length == 60
                && localEnclaveReport.reportData.length == 64,
            "local QE report has wrong length"
        );

82  require(
            pckSignedQeReport.reserved3.length == 96 && pckSignedQeReport.reserved4.length == 60
                && pckSignedQeReport.reportData.length == 64,
            "QE report has wrong length"
        );

87  require(
            v3Quote.v3AuthData.certification.certType == 5,
            "certType must be 5: Concatenated PCK Cert Chain (PEM formatted)"
        );

94  require(
            v3Quote.v3AuthData.ecdsa256BitSignature.length == 64
                && v3Quote.v3AuthData.ecdsaAttestationKey.length == 64
                && v3Quote.v3AuthData.qeReportSignature.length == 64,
            "Invalid ECDSA signature format"
        );

100  require(
            v3Quote.v3AuthData.qeAuthData.parsedDataSize
                == v3Quote.v3AuthData.qeAuthData.data.length,
            "Invalid QEAuthData size"
        );

116   require(totalQuoteSize >= MINIMUM_QUOTE_LENGTH, "Invalid quote size");

279   require(certParsedSuccessfully, "splitCertificateChain failed");

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L77-L81


```solidity
file: blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

77  require(_key.length > 0, "MerkleTrie: empty key");

89  require(currentKeyIndex <= key.length, "MerkleTrie: key index exceeds total key length");

93  require(
                    Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
                    "MerkleTrie: invalid root hash"
                );

99  require(
                    Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
                    "MerkleTrie: invalid large internal hash"
                );

105  require(
                    Bytes.equal(currentNode.encoded, currentNodeID),
                    "MerkleTrie: invalid internal node hash"
                );

119  require(
                        value_.length > 0,
                        "MerkleTrie: value length must be greater than zero (branch)"
                    );

125  require(
                        i == proof.length - 1,
                        "MerkleTrie: value node must be last node in proof (branch)"
                    );

150  require(
                    pathRemainder.length == sharedNibbleLength,
                    "MerkleTrie: path remainder must share all nibbles with key"
                );

162  require(
                        keyRemainder.length == sharedNibbleLength,
                        "MerkleTrie: key remainder must be identical to path remainder"
                    );

172  require(
                        value_.length > 0,
                        "MerkleTrie: value length must be greater than zero (leaf)"
                    );

178  require(
                        i == proof.length - 1,
                        "MerkleTrie: value node must be last node in proof (leaf)"
                    );

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L77

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

57   require(der[ptr.ixs()] == 0x03, "Not type BIT STRING");

67   require(der[ptr.ixs()] == 0x04, "Not type OCTET STRING");

88   require(der[ptr.ixs()] & 0x20 == 0x20, "Not a constructed type");

142  require(der[ptr.ixs()] == 0x02, "Not type INTEGER");

155  require(der[ptr.ixs()] == 0x02, "Not type INTEGER");

180  require(der[ptr.ixs()] == 0x03, "ixs Not type BIT STRING 0x03");

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L57

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

25  require(offset + len <= self.length, "invalid offset");

293 require(offset + len <= self.length, "unexpected offset");

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L25

```solidity
file: blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol

25  require(_length + 31 >= _length, "slice_overflow");

26  require(_start + _length >= _start, "slice_overflow");

27  require(_bytes.length >= _start + _length, "slice_outOfBounds");

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L25

## [G-09] Use inline assembly to check for address(0)

Writing contracts in inline assembly is generally considered gas optimized. we can manipulate memory directly and use fewer opcodes instead of leaving it to the Solidity compiler.


Authentication mechanism is one example where using inline assembly is good, like implementing address zero check.

Here’s an example below:

<details>

```solidity

// SPDX-License-Identifier: MIT
pragma solidity 0.8.20;

contract NormalAddressZeroCheck {
    function check(address _caller) public pure returns (bool) {
        require(_caller != address(0x00), "Zero address");
        return true;
    }
}

contract AddressZeroCheckAssembly {
    // Saves about 90 gasfunction checkOptimized(address _caller) public pure returns (bool) {
        assembly {
            if iszero(_caller) {
                mstore(0x00, 0x20)
                mstore(0x20, 0x0c)
                mstore(0x40, 0x5a65726f20416464726573730000000000000000000000000000000000000000) // load hex of "Zero Address" to memory
                revert(0x00, 0x60)
            }
        }

        return true;
    }
}
```

</details>

```solidity
file: blob/main/packages/protocol/contracts/bridge/Bridge.sol

124  if (_message.srcOwner == address(0) || _message.destOwner == address(0)) {

270   _message.to == address(0) || _message.to == address(this)

291  _message.refundTo == address(0) ? _message.destOwner : _message.refundTo;

398   enabled_ = destBridge_ != address(0);

531  _storeContext(bytes32(0), address(0), uint64(0));

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L124

```solidity
file: blob/main/packages/protocol/contracts/common/AddressResolver.sol

81  if (addressManager == address(0)) revert RESOLVER_INVALID_MANAGER();

85  if (!_allowZeroAddress && addr_ == address(0)) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L81

```solidity
file: blob/main/packages/protocol/contracts/common/EssentialContract.sol

105   if (_addressManager == address(0)) revert ZERO_ADDR_MANAGER();

110  _transferOwnership(_owner == address(0) ? msg.sender : _owner);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L105

```solidity
file: blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol

109  if (assignment.feeToken == address(0)) {

120  if (input.tip != 0 && block.coinbase != address(0)) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L109

```solidity
file: blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol

44  address recipient_ = _recipient == address(0) ? msg.sender : _recipient;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L44

```solidity
file: blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol

81  if (params.assignedProver == address(0)) {

85  if (params.coinbase == address(0)) {

310 if (proposerOne != address(0) && msg.sender != proposerOne) {

316  return proposer == address(0) || msg.sender == proposer;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L81

```solidity
file: blob/main/packages/protocol/contracts/L1/libs/LibProving.sol

163  if (verifier != address(0)) {

224  assert(ts.validityBond == 0 && ts.contestBond == 0 && ts.contester == address(0));

239  if (ts.contester != address(0)) revert L1_ALREADY_CONTESTED();

303  ts_.contester = address(0);

332  ts_.prover = address(0);

363  if (_ts.contester != address(0)) {

390  _ts.contester = address(0);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L163

```solidity
file: blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol

70   ts.prover = address(0);

75   assignedProver: address(0),

76   prover: address(0),

145  if (ts.contester != address(0)) {

148   if (tierProvider == address(0)) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L70

```solidity
file: blob/main/packages/protocol/contracts/L2/TaikoL2.sol

172  if (_to == address(0)) revert L2_INVALID_PARAM();

173  if (_token == address(0)) {'

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L172

```solidity
file: blob/main/packages/protocol/contracts/libs/LibAddress.sol

24   if (_to == address(0)) revert ETH_TRANSFER_FAILED();

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L24


```solidity
file: blob/main/packages/protocol/contracts/signal/SignalService.sol

36   if (_app == address(0)) revert SS_INVALID_SENDER();

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L36


```solidity
file: blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol

121  if (_taikoToken == address(0)) revert INVALID_PARAM();

124  if (_costToken == address(0)) revert INVALID_PARAM();

127  if (_sharedVault == address(0)) revert INVALID_PARAM();

136  if (_recipient == address(0)) revert INVALID_PARAM();

169  if (_to == address(0)) revert INVALID_PARAM();

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L121

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol

149    if (_op.token == address(0)) revert VAULT_INVALID_TOKEN();

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L149

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

102  return migratingAddress != address(0) && !migratingInbound;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L102

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol
 
158   if (_btokenNew == address(0) || bridgedToCanonical[_btokenNew].addr != address(0)) {

170   if (btokenOld_ != address(0)) {

215   if (_op.token == address(0)) revert VAULT_INVALID_TOKEN();

223   from: address(0), // will receive a new value

227   destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,

267   if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

358   if (bridgedToCanonical[_token].addr != address(0)) {

397   if (btoken == address(0)) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L158

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol

46   from: address(0), // will receive a new value

50   destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,

91   if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

195  if (bridgedToCanonical[_op.token].addr != address(0)) {

230  if (btoken_ == address(0)) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L46

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol

60   from: address(0), // will receive a new value

64   destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,

108  if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

249  if (bridgedToCanonical[_op.token].addr != address(0)) {

293  if (btoken_ == address(0)) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L60


```solidity
file: blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol

21  _srcToken == address(0) || _srcChainId == 0 || _srcChainId == block.chainid

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L21

```solidity
file: blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol

107  if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();

124  if (automataDcapAttestation == address(0)) {

215  if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();

220  emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);

234  if (instance == address(0)) return false;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L107

## [G-10] Do-While loops are cheaper than for loops

If you want to push optimization at the expense of creating slightly unconventional code, Solidity do-while loops are more gas efficient than for loops, even if you add an if-condition check for the case where the loop doesn’t execute at all.

<details> 

```solidity
// SPDX-License-Identifier: MIT
pragma solidity 0.8.20;

// times == 10 in both tests
contract Loop1 {
    function loop(uint256 times) public pure {
        for (uint256 i; i < times;) {
            unchecked {
                ++i;
            }
        }
    }
}

contract Loop2 {
    function loop(uint256 times) public pure {
        if (times == 0) {
            return;
        }

        uint256 i;

        do {
            unchecked {
                ++i;
            }
        } while (i < times);
    }
}

```

</details>

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

240  for (uint256 i; i < CPUSVN_LENGTH; ++i) {
            if (pckCpuSvns[i] < tcbCpuSvns[i]) {
                return false;
            }
        }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L240-L244

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

244  for (uint256 i; i < split.length; ++i) {
            contentStr = LibString.concat(contentStr, split[i]);
        }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L244-L246

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

281  for (uint256 i; i < 3; ++i) {
            quoteCerts[i] = Base64.decode(string(quoteCerts[i]));
        }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L281-L283

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

140   for (uint256 i = 2; i < 2 + paddingLen; ++i) {
            if (decipher[i] != 0xff) {
                return false;
            }
        }

152   for (uint256 i; i < digestAlgoWithParamLen; ++i) {
                if (decipher[3 + paddingLen + i] != bytes1(sha256ExplicitNullParam[i])) {
                    return false;
                }
            }

158   for (uint256 i; i < digestAlgoWithParamLen; ++i) {
                if (decipher[3 + paddingLen + i] != bytes1(sha256ImplicitNullParam[i])) {
                    return false;
                }
            }
174   for (uint256 i; i < _sha256.length; ++i) {
            if (decipher[5 + paddingLen + digestAlgoWithParamLen + i] != _sha256[i]) {
                return false;
            }
        }

273  for (uint256 i = 2; i < 2 + paddingLen; ++i) {
            if (decipher[i] != 0xff) {
                return false;
            }
        }

283  for (uint256 i; i < sha1Prefix.length; ++i) {
            if (decipher[3 + paddingLen + i] != bytes1(sha1Prefix[i])) {
                return false;
            }
        }

290  for (uint256 i; i < _sha1.length; ++i) {
            if (decipher[3 + paddingLen + sha1Prefix.length + i] != _sha1[i]) {
                return false;
            }
        }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L140-L144

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

59  for (uint8 i = 1; i < month; ++i) {
            timestamp += uint256(monthDays[i - 1]) * 86_400; // Days in seconds
        }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L59

```solidity
file: blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol

172  for (uint256 i; i < _tierFees.length; ++i) {
            if (_tierFees[i].tier == _tierId) return _tierFees[i].fee;
        }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L172-L174

```solidity
file: blob/main/packages/protocol/contracts/L1/provers/Guardians.sol

74  for (uint256 i; i < guardians.length; ++i) {
            delete guardianIds[guardians[i]];
        }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L74-L76


```solidity
file: blob/main/packages/protocol/contracts/L2/TaikoL2.sol
 
234  for (uint256 i; i < 255 && _blockId >= i + 1; ++i) {
                uint256 j = _blockId - i - 1;
                inputs[j % 255] = blockhash(j);
            }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L234-L237

```solidity
file: blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

59  for (uint256 i; i < tokenIds.length; ++i) {
            IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);
        }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59-L60

```solidity
file: blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

66   for (uint256 j = 0; j < out_.length; j++) {
            out_[j] = b[i++];
        }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66-L68


```solidity
file: blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

208  for (uint256 i = 0; i < length;) {
            proof_[i] = TrieNode({ encoded: _proof[i], decoded: RLPReader.readList(_proof[i]) });
            unchecked {
                ++i;
            }
        }

244  for (; shared_ < max && _a[shared_] == _b[shared_];) {
            unchecked {
                ++shared_;
            }
        }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L208-L213


```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol

34  for (uint256 i; i < _op.tokenIds.length; ++i) {
            if (_op.amounts[i] != 0) revert VAULT_INVALID_AMOUNT();
        }

170  for (uint256 i; i < _tokenIds.length; ++i) {
                IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);
            }

175  for (uint256 i; i < _tokenIds.length; ++i) {
                BridgedERC721(token_).mint(_to, _tokenIds[i]);
            }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L34-L36

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol

47  for (uint256 i; i < _op.amounts.length; ++i) {
            if (_op.amounts[i] == 0) revert VAULT_INVALID_AMOUNT();
        }

251 for (uint256 i; i < _op.tokenIds.length; ++i) {
                    BridgedERC1155(_op.token).burn(_user, _op.tokenIds[i], _op.amounts[i]);
                }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L47-L49

## [G-11] Call msg.sender directly instead of caching them

In the instance below, instead of caching msg.sender and incurring unnecessary stack manipulation, we can call msg.sender directly.

```solidity
file: blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol

93   address taikoL1Address = msg.sender;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L93


## [G-12] Use uint8 Can Increase Gas Cost

A smart contract's gas consumption can be higher if developers use items that are less than 32 bytes in size because the Ethereum Virtual Machine can only handle 32 bytes at a time. In order to increase the element's size to the necessary size, the EVM has to perform additional operations.

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol

24  uint8 private __srcDecimals;

57  uint8 _decimals,

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L24

```solidity
file: blob/main/packages/protocol/contracts/common/EssentialContract.sol

11  uint8 private constant _FALSE = 1;

13  uint8 private constant _TRUE = 2;

21  uint8 private __reentry;

23  uint8 private __paused;

119 function _storeReentryLock(uint8 _reentry) internal virtual {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L11


```solidity
file: blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

30   uint8 internal constant PREFIX_EXTENSION_EVEN = 0;

33   uint8 internal constant PREFIX_EXTENSION_ODD = 1;

36   uint8 internal constant PREFIX_LEAF_EVEN = 2;

39   uint8 internal constant PREFIX_LEAF_ODD = 3;

134  uint8 branchKey = uint8(key[currentKeyIndex]);

141  uint8 prefix = uint8(path[0]);

142  uint8 offset = 2 - (prefix % 2);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L30

```solidity
file: blob/main/packages/protocol/contracts/L2/TaikoL2.sol

35   uint8 public constant BLOCK_SYNC_THRESHOLD = 5;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L35


```solidity
file: blob/main/packages/protocol/contracts/L1/TaikoL1.sol

94  uint8 maxBlocksToVerify = LibProving.proveBlock(state, config, this, meta, tran, proof);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L94

```solidity
file:  blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

136  uint8 internal constant INVALID_EXIT_CODE = 255;

231  uint8[] memory tcbCpuSvns

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L136

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol

15  uint8[] sgxTcbCompSvnArr;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol#L15

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

188  function readUint8(bytes memory self, uint256 idx) internal pure returns (uint8 ret) {

189  return uint8(self[idx]);

332   uint8 decoded;

336   decoded = uint8(BASE32_HEX_TABLE[uint256(uint8(char)) - 0x30]);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L188

```solidity
file:  blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

10     uint8 mnths;

11     uint8 dys;

12     uint8 hrs;

13     uint8 mins;

14     uint8 secs;

15     uint8 offset;

18     if (uint8(x509Time[0]) - 48 < 5) yrs += 2000;

21     yrs += (uint8(x509Time[0]) - 48) * 1000 + (uint8(x509Time[1]) - 48) * 100;

36     uint8 month,

37     uint8 day,

38     uint8 hour,

39     uint8 minute,

40     uint8 second

56     uint8[12] memory monthDays = [31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31];

59    for (uint8 i = 1; i < month; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L10


```solidity
file: blob/main/packages/protocol/contracts/L1/provers/Guardians.sol

55   uint8 _minGuardians

63   if (_newGuardians.length < MIN_NUM_GUARDIANS || _newGuardians.length > type(uint8).max) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L55

```solidity
file: blob/main/packages/protocol/contracts/L1/TaikoData.sol

28   uint24 blockMaxTxListBytes;

30   uint24 blobExpiry;

59   uint8 blockSyncThreshold;

83   uint24 txListByteOffset;

84   uint24 txListByteSize

105  uint24 txListByteOffset;

106  uint24 txListByteSize;

132  uint8 contestations;

172  uint8 __reserved1;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L59

```solidity
file: blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

69  (address delegatee, uint256 nonce, uint256 expiry, uint8 v, bytes32 r, bytes32 s) =

70    abi.decode(delegationData, (address, uint256, uint256, uint8, bytes32, bytes32));

```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L69

```solidity
file: blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

14  if (_in.length == 1 && uint8(_in[0]) < 128) {

35  out_[0] = bytes1(uint8(_len) + uint8(_offset));

45   out_[0] = bytes1(uint8(lenLen) + uint8(_offset) + 55);

47   out_[i] = bytes1(uint8((_len / (256 ** (lenLen - i))) % 256))

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L14


## [G-13] Store Data in calldata Instead of Memory for Certain Function Parameters 

Instead of copying variables to memory, it is typically more cost-effective to load them immediately from calldata. If all you need to do is read data, you can conserve gas by saving the data in calldata.

<details>

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

229  function _isCpuSvnHigherOrGreater(
        uint256[] memory pckCpuSvns,
        uint8[] memory tcbCpuSvns
    )

248  function _verifyCertChain(IPEMCertChainLib.ECSha256Certificate[] memory certs)

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L229-L232


```solidity
file: blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol
 
48  function propose(
        address[] memory _targets,
        uint256[] memory _values,
        bytes[] memory _calldatas,
        string memory _description
    )

69  function propose(
        address[] memory _targets,
        uint256[] memory _values,
        string[] memory _signatures,
        bytes[] memory _calldatas,
        string memory _description
    )

127   function _execute(
        uint256 _proposalId,
        address[] memory _targets,
        uint256[] memory _values,
        bytes[] memory _calldatas,
        bytes32 _descriptionHash
    )

140  function _cancel(
        address[] memory _targets,
        uint256[] memory _values,
        bytes[] memory _calldatas,
        bytes32 _descriptionHash
    )

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L48-L53

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

303 function _enclaveReportSigVerification(
        bytes memory pckCertPubKey,
        bytes memory signedQuoteData,
        V3Struct.ECDSAQuoteV3AuthData memory authDataV3,
        V3Struct.EnclaveReport memory qeEnclaveReport
    )

355  function verifyParsedQuote(V3Struct.ParsedV3QuoteStruct calldata v3quote)

364   function _verifyParsedQuote(V3Struct.ParsedV3QuoteStruct memory v3quote)

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L303-L308

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol

38  function verifyAttStmtSignature(
        bytes memory tbs,
        bytes memory signature,
        PublicKey memory publicKey,
        Algorithm alg
    )

48  function verifyCertificateSignature(
        bytes memory tbs,
        bytes memory signature,
        PublicKey memory publicKey,
        CertSigAlgorithm alg
    )

58  function verifyRS256Signature(
        bytes memory tbs,
        bytes memory signature,
        bytes memory publicKey
    )

67   function verifyRS1Signature(
        bytes memory tbs,
        bytes memory signature,
        bytes memory publicKey
    )

76  function verifyES256Signature(
        bytes memory tbs,
        bytes memory signature,
        bytes memory publicKey
    )

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L38-L43

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

216  function _removeHeadersAndFooters(string memory pemData)

270  bytes memory der,

342   bytes memory der,

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L216

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

47  function root(bytes memory der) internal pure returns (uint256) {

56  function rootOfBitStringAt(bytes memory der, uint256 ptr) internal pure returns (uint256) {

66  function rootOfOctetStringAt(bytes memory der, uint256 ptr) internal pure returns (uint256) {

77  function nextSiblingOf(bytes memory der, uint256 ptr) internal pure returns (uint256) {

87  function firstChildOf(bytes memory der, uint256 ptr) internal pure returns (uint256) {

111 function bytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes memory) {

121 function allBytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes memory) {

131 function bytes32At(bytes memory der, uint256 ptr) internal pure returns (bytes32) {

141 function uintAt(bytes memory der, uint256 ptr) internal pure returns (uint256) {

154 function uintBytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes memory) {

165 function keccakOfBytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes32) {

169 function keccakOfAllBytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes32) {

179 function bitstringAt(bytes memory der, uint256 ptr) internal pure returns (bytes memory) {

187 function _readNodeLength(bytes memory der, uint256 ix) private pure returns (uint256) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L47

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

17  bytes memory self,

39  function compare(bytes memory self, bytes memory other) internal pure returns (int256) {

56 function compare(
        bytes memory self,
        uint256 offset,
        uint256 len,
        bytes memory other,
        uint256 otheroffset,
        uint256 otherlen
    )

116 function equals(
        bytes memory self,
        uint256 offset,
        bytes memory other,
        uint256 otherOffset,
        uint256 len
    )

138  function equals(
        bytes memory self,
        uint256 offset,
        bytes memory other,
        uint256 otherOffset
    )

160 function equals(
        bytes memory self,
        uint256 offset,
        bytes memory other
    )

178  function equals(bytes memory self, bytes memory other) internal pure returns (bool) {

188   function readUint8(bytes memory self, uint256 idx) internal pure returns (uint8 ret) {

198  function readUint16(bytes memory self, uint256 idx) internal pure returns (uint16 ret) {

211  function readUint32(bytes memory self, uint256 idx) internal pure returns (uint32 ret) {

224  function readBytes32(bytes memory self, uint256 idx) internal pure returns (bytes32 ret) {

237  function readBytes20(bytes memory self, uint256 idx) internal pure returns (bytes20 ret) {

256  bytes memory self,

285  bytes memory self,

321  bytes memory self,

371   function compareBytes(bytes memory a, bytes memory b) internal pure returns (bool) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L17

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

43  function pkcs1Sha256(
        bytes32 _sha256,
        bytes memory _s,
        bytes memory _e,
        bytes memory _m
    )

191 function pkcs1Sha256Raw(
        bytes memory _data,
        bytes memory _s,
        bytes memory _e,
        bytes memory _m
    )

212 function pkcs1Sha1(
        bytes20 _sha1,
        bytes memory _s,
        bytes memory _e,
        bytes memory _m
    )

307  function pkcs1Sha1Raw(
        bytes memory _data,
        bytes memory _s,
        bytes memory _e,
        bytes memory _m
    )
    
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L43-L48

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

24  function verifyAttStmtSignature(
        bytes memory tbs,
        bytes memory signature,
        PublicKey memory publicKey,
        Algorithm alg
    )

54 function verifyCertificateSignature(
        bytes memory tbs,
        bytes memory signature,
        PublicKey memory publicKey,
        CertSigAlgorithm alg
    )

79 function verifyRS256Signature(
        bytes memory tbs,
        bytes memory signature,
        bytes memory publicKey
    )

96 function verifyRS1Signature(
        bytes memory tbs,
        bytes memory signature,
        bytes memory publicKey
    )'

113 function verifyES256Signature(
        bytes memory tbs,
        bytes memory signature,
        bytes memory publicKey
    )

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L24-L29

```solidity
file: blob/main/packages/protocol/contracts/bridge/Bridge.sol


449   function hashMessage(Message memory _message) public pure returns (bytes32) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L449

```solidity
file: blob/main/packages/protocol/contracts/bridge/IBridge.sol

155  function hashMessage(Message memory _message) external pure returns (bytes32);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L155


```solidity
file: blob/main/packages/protocol/contracts/L1/provers/Guardians.sol
 
54  address[] memory _newGuardians,

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L54


```solidity
file: blob/main/packages/protocol/contracts/libs/Lib4844.sol

30   function evaluatePoint(
        bytes32 _blobHash,
        uint256 _x,
        uint256 _y,
        bytes1[48] memory _commitment,
        bytes1[48] memory _pointProof
    )

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L30-L37

```solidity
file: blob/main/packages/protocol/contracts/libs/LibTrieProof.sol

34   function verifyMerkleProof(
        bytes32 _rootHash,
        address _addr,
        bytes32 _slot,
        bytes32 _value,
        bytes[] memory _accountProof,
        bytes[] memory _storageProof
    )

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L34-L41

```solidity
file:  blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol

135  function grant(address _recipient, Grant memory _grant) external onlyOwner {

168  function withdraw(address _to, bytes memory _sig) external {

235  function _getAmountOwned(Grant memory _grant) private view returns (uint128) {

239  function _getAmountUnlocked(Grant memory _grant) private view returns (uint128) {

267  function _validateGrant(Grant memory _grant) private pure {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L135

```solidity
file: blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol

91  function slice(bytes memory _bytes, uint256 _start) internal pure returns (bytes memory) {

102 function toNibbles(bytes memory _bytes) internal pure returns (bytes memory) {

149  function equal(bytes memory _bytes, bytes memory _other) internal pure returns (bool) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L91

```solidity
file: blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

35  function toRLPItem(bytes memory _in) internal pure returns (RLPItem memory out_) {

53  function readList(RLPItem memory _in) internal pure returns (RLPItem[] memory out_) {

102 function readList(bytes memory _in) internal pure returns (RLPItem[] memory out_) {

109 function readBytes(RLPItem memory _in) internal pure returns (bytes memory out_) {

128 function readBytes(bytes memory _in) internal pure returns (bytes memory out_) {

135 function readRawBytes(RLPItem memory _in) internal pure returns (bytes memory out_) {

144 function _decodeLength(RLPItem memory _in)

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L35


```solidity
file: blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

50 function verifyInclusionProof(
        bytes memory _key,
        bytes memory _value,
        bytes[] memory _proof,
        bytes32 _root
    )

68 function get(
        bytes memory _key,
        bytes[] memory _proof,
        bytes32 _root
    )

205 function _parseProof(bytes[] memory _proof) private pure returns (TrieNode[] memory proof_) {

220 function _getNodeID(RLPReader.RLPItem memory _node) private pure returns (bytes memory id_) {

227 function _getNodePath(TrieNode memory _node) private pure returns (bytes memory nibbles_) {

235 function _getSharedNibbleLength(
        bytes memory _a,
        bytes memory _b
    )

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L50-L55

```solidity
file: blob/main/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol

19  function verifyInclusionProof(
        bytes memory _key,
        bytes memory _value,
        bytes[] memory _proof,
        bytes32 _root
    )

38  function get(
        bytes memory _key,
        bytes[] memory _proof,
        bytes32 _root
    )

54 function _getSecureKey(bytes memory _key) private pure returns (bytes memory hash_) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L19-L24

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol
  
38  function init(
        address _owner,
        address _addressManager,
        address _srcToken,
        uint256 _srcChainId,
        string memory _symbol,
        string memory _name
    )

83  function mintBatch(
        address _to,
        uint256[] memory _tokenIds,
        uint256[] memory _amounts
    )

125 function _beforeTokenTransfer(
        address, /*_operator*/
        address, /*_from*/
        address _to,
        uint256[] memory, /*_ids*/
        uint256[] memory, /*_amounts*/
        bytes memory /*_data*/
    )

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L38-L45


```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol

160  function _transferTokens(
        CanonicalNFT memory _ctoken,
        address _to,
        uint256[] memory _tokenIds
    )

187  function _handleMessage(
        address _user,
        BridgeTransferOp memory _op
    )

240  function _deployBridgedToken(CanonicalNFT memory _ctoken) private returns (address btoken_) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L160-L164

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol

214  function _transferTokens(
        CanonicalNFT memory ctoken,
        address to,
        uint256[] memory tokenIds,
        uint256[] memory amounts
    )

240  function _handleMessage(
        address _user,
        BridgeTransferOp memory _op
    )

288  function _getOrDeployBridgedToken(CanonicalNFT memory _ctoken)

303 function _deployBridgedToken(CanonicalNFT memory _ctoken) private returns (address btoken_) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L214-L220

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol

11  function validateInputs(
        address _srcToken,
        uint256 _srcChainId,
        string memory _symbol,
        string memory _name
    )\

28 function buildName(
        string memory _name,
        uint256 _srcChainId
    )

39  function buildSymbol(string memory _symbol) internal pure returns (string memory) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L11-L16

```solidity
file: blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol

172  TaikoData.Transition memory _tran,

196  address[] memory _instances,

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L172

</details>

## [G-14] Using bytes32 is cheaper than using string.

Storing and manipulating data in bytes32 is more gas-efficient than using string, which involves dynamic storage allocation. bytes32 is a fixed-size type, whereas string can have variable length, resulting in higher gas costs.

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol

22  string private __symbol;

25  string private __name;

43  string memory _symbol,

44  string memory _name

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L22


```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

17   string internal constant HEADER = "-----BEGIN CERTIFICATE-----";

18   string internal constant FOOTER = "-----END CERTIFICATE-----";

22   string internal constant PCK_COMMON_NAME = "Intel SGX PCK Certificate";

23   string internal constant PLATFORM_ISSUER_NAME = "Intel SGX PCK Platform CA";

24   string internal constant PROCESSOR_ISSUER_NAME = "Intel SGX PCK Processor CA";

49   string memory pemChainStr = string(pemChain);

55   string memory input;

216  function _removeHeadersAndFooters(string memory pemData)

240  string memory contentSlice = LibString.slice(pemData, contentStart, endPos);

242  string memory contentStr;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L17

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

49   mapping(string fmspc => TCBInfoStruct.TCBInfo tcbInfo) public tcbInfo;

104  string calldata fmspc,

435  string memory parsedFmspc = parsedQuoteCerts[0].pck.sgxExtension.fmspc;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L49


```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol

19  string commonName;

20  string issuerName;

25  string pceid;

26  string fmspc;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L19

```solidity
file: blob/main/packages/protocol/contracts/L1/TaikoToken.sol

27    string calldata _name,

28    string calldata _symbol

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L27


```solidity
file: blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol

52   string memory _description

74   string memory _description

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L52

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol

17  string symbol;

19  string name;

43  string memo;

73  string ctokenSymbol,

74  string ctokenName 

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L17


```solidity
file: blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol

58   string memory _symbol,

59   string memory _name

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L58

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol

36    string memory _symbol,

37    string memory _name

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L36


```solidity
file: blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol

14   string memory _symbol,

15   string memory _name

29   string memory _name,

39   function buildSymbol(string memory _symbol) internal pure returns (string memory) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L14

## [G-15] Avoid Unnecessary Use of Storage

Writing data to storage is one of the most expensive operations in Solidity. Reduce gas costs by avoiding unnecessary writes. For example, move constant values to memory:

<details>

```solidity

// Expensive
string public constant NAME = "MyContract"; 

// Cheaper
string memory NAME = "MyContract";

```

</details>

Also be careful about storing large pieces of data on-chain. Use alternative patterns like IPFS for larger data.
Storing data costs 20,000 gas versus 3 gas for memory.
Minimize storage by using memory for fixed constants and temporary values.
Store large data like files off-chain (IPFS) and put hash on-chain.

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

17   string internal constant HEADER = "-----BEGIN CERTIFICATE-----";

18   string internal constant FOOTER = "-----END CERTIFICATE-----";

22   string internal constant PCK_COMMON_NAME = "Intel SGX PCK Certificate";

23   string internal constant PLATFORM_ISSUER_NAME = "Intel SGX PCK Platform CA";

24   string internal constant PROCESSOR_ISSUER_NAME = "Intel SGX PCK Processor CA";

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L17

## [G-16] Precompute Off-Chain When Possible

Computing values in advance outside the blockchain is cheaper than doing it inside smart contracts:

<details>

```solidity
// On-chain computation
function verify(uint numA, uint numB) {
  require(numA * numB < 1000);
}

// Precomputed off-chain
function verify(uint result) {
  require(result < 1000); 
}
```

</details>

Do computations like hashes, signatures outside.
Pass in precomputed values to save on-chain gas.

```solidity
file: blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol

98   if (b.numBlocks >= b.lastVerifiedBlockId + _config.blockMaxProposals + 1) {

171  if (uint256(params.txListByteOffset) + params.txListByteSize > MAX_BYTES_PER_BLOB) {

268  if (tko.balanceOf(address(this)) != tkoBalance + _config.livenessBond) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L98

```solidity
file: blob/main/packages/protocol/contracts/bridge/Bridge.sol

189   if (block.timestamp >= invocationDelay + receivedAt) {

258   if (block.timestamp >= invocationDelay + receivedAt) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L189

```solidity
file: blob/main/packages/protocol/contracts/L2/TaikoL2.sol

145  if (_l1BlockId > lastSyncedBlock + BLOCK_SYNC_THRESHOLD) {

202  if (_blockId + 256 >= block.number) return blockhash(_blockId);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L145


```solidity
file: blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

40  if (claimEnd > block.timestamp || claimEnd + withdrawalWindow < block.timestamp) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L40

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

261    if (i == n - 1) {

266    if (i == n - 2) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L261


```solidity
file: blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol

260  if (block.timestamp >= _start + _period) return _amount;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L260

```solidity
file: blob/main/packages/protocol/contracts/L1/provers/Guardians.sol

68  if (_minGuardians < (_newGuardians.length + 1) >> 1 || _minGuardians > _newGuardians.length)

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L68


```solidity
file: blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol

68    if (_rand % 1000 == 0) return LibTiers.TIER_SGX_ZKVM;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L68

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

25    require(offset + len <= self.length, "invalid offset");

199   require(idx + 2 <= self.length, "invalid idx");

212   require(idx + 4 <= self.length, "unexpected idx");

225   require(idx + 32 <= self.length, "unexpected idx");

238   require(idx + 20 <= self.length, "unexpected idx");

265   require(idx + len <= self.length, "unexpected idx");

293   require(offset + len <= self.length, "unexpected offset");

345   if (len % 8 == 0) {

348   } else if (len % 8 == 2) {

352   } else if (len % 8 == 4) {

356   } else if (len % 8 == 5) {

360   } else if (len % 8 == 7) {
     
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L25

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

72    if (year % 4 != 0) return false;

73    if (year % 100 != 0) return true;

74    if (year % 400 != 0) return false;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L72

```solidity
file: blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol

25   require(_length + 31 >= _length, "slice_overflow");

26   require(_start + _length >= _start, "slice_overflow");

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L25

```solidity
file: blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

61   require(
            listOffset + listLength == _in.length,
            "RLPReader: list item has an invalid data remainder"
        );

117  require(
            _in.length == itemOffset + itemLength,
            "RLPReader: bytes value contains an invalid remainder"
        );

263  require(
                _in.length > lenOfListLen + listLen,
                "RLPReader: length of content must be greater than total length (long list)"
            );            
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L61-L64

## [G-17] abi.encode() is less efficient than abi.encodePacked()

See for more information: https://github.com/ConnorBlockchain/Solidity-Encode-Gas-Comparison

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol
 
482  retData = abi.encodePacked(sha256(abi.encode(v3quote)), tcbStatus);\

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L482

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

136  bytes memory args = abi.encode(sha256(tbs), r, s, gx, gy);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L136

```solidity
file: blob/main/packages/protocol/contracts/bridge/Bridge.sol

450   return keccak256(abi.encode("TAIKO_MESSAGE", _message));

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L450

```solidity
file: blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol

147  abi.encode(

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L147

```solidity
file: blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol

126  depositsHash: keccak256(abi.encode(deposits_)),

213  metaHash: keccak256(abi.encode(meta_)),

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L126

```solidity
file: blob/main/packages/protocol/contracts/L1/libs/LibProving.sol

121  if (blk.blockId != _meta.id || blk.metaHash != keccak256(abi.encode(_meta))) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L121

```solidity
file: blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol

46   bytes32 hash = keccak256(abi.encode(_meta, _tran));

51   ITaikoL1(resolve("taiko", false)).proveBlock(_meta.id, abi.encode(_meta, _tran, _proof));

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L46

```solidity
file: blob/main/packages/protocol/contracts/signal/SignalService.sol

186   return keccak256(abi.encode(_chainId, _kind, _blockId));

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L186


```solidity
file: blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

60   _verifyClaim(abi.encode(user, amount), proof);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L60

```solidity
file: blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

80  _verifyClaim(abi.encode(user, amount), proof);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L80

```solidity
file: blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

56    _verifyClaim(abi.encode(user, tokenIds), proof);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L56

```solidity
file: blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

68  bytes32 hash = keccak256(abi.encode("CLAIM_TAIKO_AIRDROP", data));

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L68


```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol

384    this.onMessageInvocation, abi.encode(ctoken_, _user, _to, balanceChange_)

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L384

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol

217  this.onMessageInvocation, abi.encode(ctoken_, _user, _op.to, _op.tokenIds)

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L217

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol

281   this.onMessageInvocation, abi.encode(ctoken_, _user, _op.to, _op.tokenIds, _op.amounts)

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L281

```solidity
file: blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol

182   abi.encode(

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L182


## [G-18] Alternative Solady library can be used instead of OpenZeppelin to save gas

The following OpenZeppelin imports have a Solady(https://github.com/Vectorized/solady) equivalent, as such they can be used to save GAS as Solady modules have been specifically designed to be as GAS efficient as possible.

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

13  import { Base64 } from "solady/src/utils/Base64.sol";

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L13

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

4  import { Base64 } from "solady/src/utils/Base64.sol";

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L4


## [G-19] Avoid unnecessary public variables

Public state variables in Solidity automatically generate getter functions, increasing contract size and potentially leading to higher deployment and interaction costs. To optimize gas usage and contract efficiency, minimize the use of public variables unless external access is necessary. Instead, use internal or private visibility combined with explicit getter functions when required. This practice not only reduces contract size but also provides better control over data access and manipulation, enhancing security and readability. Prioritize lean, efficient contracts to ensure cost-effectiveness and better performance on the blockchain.

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

25    ISigVerifyLib public immutable sigVerifyLib;

26    IPEMCertChainLib public immutable pemCertLib;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L25


## [G-20] Consider pre-calculating the address of address(this)

It can be more gas-efficient to use a hardcoded address instead of the address(this) expression, especially if you need to use the same address multiple times in your contract.

The reason for this, is that using address(this) requires an additional EXTCODESIZE operation to retrieve the contract’s address from its bytecode, which can increase the gas cost of your contract. By pre-calculating and using a hardcoded address, you can avoid this additional operation and reduce the overall gas cost of your contract.

```solidity
file: blob/main/packages/protocol/contracts/bridge/Bridge.sol

174  if (!ISignalService(signalService).isSignalSent(address(this), msgHash)) {

196  _storeContext(msgHash, address(this), _message.srcChainId);

270  _message.to == address(0) || _message.to == address(this)

343  _app: address(this),

486  assert(_message.from != address(this));

```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L174

```solidity
file: blob/main/packages/protocol/contracts/L1/TaikoToken.sol

61   if (_to == address(this)) revert TKO_INVALID_ADDR();

79   if (_to == address(this)) revert TKO_INVALID_ADDR();

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L61

```solidity
file: blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol
 
125   if (address(this).balance > 0) {

126   taikoL1Address.sendEther(address(this).balance);

151   address(this),

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L125

```solidity
file: blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol

238  uint256 tkoBalance = tko.balanceOf(address(this));

253  IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }(

260  if (address(this).balance != 0) {

261   msg.sender.sendEther(address(this).balance);

268  if (tko.balanceOf(address(this)) != tkoBalance + _config.livenessBond) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L238

```solidity
file: blob/main/packages/protocol/contracts/L1/libs/LibProving.sol

242  tko.transferFrom(msg.sender, address(this), tier.contestBond);

384  _tko.transferFrom(msg.sender, address(this), _tier.validityBond - reward);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L242


```solidity
file: blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol

50  (bool success,) = address(this).call(txdata);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L50

```solidity
file: blob/main/packages/protocol/contracts/L2/TaikoL2.sol

174  _to.sendEther(address(this).balance);

176   IERC20(_token).safeTransfer(_to, IERC20(_token).balanceOf(address(this)));

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L174


```solidity
file: blob/main/packages/protocol/contracts/signal/SignalService.sol

112  signalService = address(this);

131  if (value == 0 || value != _loadSignalValue(address(this), signal)) {

149  return _loadSignalValue(address(this), signal) == _chainData;

171  chainData_ = _loadSignalValue(address(this), signal);

245  _sendSignal(address(this), signal_, _chainData);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L112


```solidity
file: blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol

147  if (_to == address(this)) revert BTOKEN_CANNOT_RECEIVE();

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L147

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol

125   if (_to == address(this)) revert BTOKEN_CANNOT_RECEIVE();

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L125

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol

137  if (_to == address(this)) revert BTOKEN_CANNOT_RECEIVE();

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L137

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol

267  if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

378  uint256 _balance = t.balanceOf(address(this));

379  t.safeTransferFrom({ from: msg.sender, to: address(this), value: _amount });

380  balanceChange_ = t.balanceOf(address(this)) - _balance;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L267

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol

91  if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

171  IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);

211  t.safeTransferFrom(_user, address(this), _op.tokenIds[i]);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L91

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol

108  if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

226  IERC1155(token).safeBatchTransferFrom(address(this), to, tokenIds, amounts, "");

272  to: address(this),

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L108

```solidity 
file: blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

48   usdc.transferFrom(_from, address(this), _amount);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L48


```solidity
file: blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol
 
186   address(this),

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L186


## [G-21] Counting down in for statements is more gas efficient

Counting down is more gas efficient than counting up because neither we are making zero variable to non-zero variable and also we will get gas refund in the last transaction when making non-zero to zero variable. 

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

80  for (uint256 i; i < serialNumBatch.length; ++i) {

95  for (uint256 i; i < serialNumBatch.length; ++i) {

191 for (uint256 i; i < enclaveId.tcbLevels.length; ++i) {

214 for (uint256 i; i < tcb.tcbLevels.length; ++i) {

240 for (uint256 i; i < CPUSVN_LENGTH; ++i) {

259 for (uint256 i; i < n; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L80

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

54   for (uint256 i; i < size; ++i) {

244  for (uint256 i; i < split.length; ++i) {

354  for (uint256 i; i < SGX_TCB_CPUSVN_SIZE + 1; ++i) 

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L54

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

153  for (uint256 i; i < encoded.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L153

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

80   for (uint256 idx = 0; idx < shortest; idx += 32) {

333  for (uint256 i; i < len; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L80

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

140  for (uint256 i = 2; i < 2 + paddingLen; ++i) {

152  for (uint256 i; i < digestAlgoWithParamLen; ++i) {

158  for (uint256 i; i < digestAlgoWithParamLen; ++i) {

174  for (uint256 i; i < _sha256.length; ++i) {

273  for (uint256 i = 2; i < 2 + paddingLen; ++i) {

283  for (uint256 i; i < sha1Prefix.length; ++i) {

290  for (uint256 i; i < _sha1.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L140


```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

48  for (uint16 i = 1970; i < year; ++i) {

59  for (uint8 i = 1; i < month; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L48

```solidity
file: blob/main/packages/protocol/contracts/bridge/Bridge.sol

90   for (uint256 i; i < _msgHashes.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L90

```solidity
file: blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol

172   for (uint256 i; i < _tierFees.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L172

```solidity
file: blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol

86   for (uint256 i; i < deposits_.length;) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L86

```solidity
file: blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol

244  for (uint256 i; i < params.hookCalls.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L244


```solidity
file: blob/main/packages/protocol/contracts/L1/provers/Guardians.sol

74  for (uint256 i; i < guardians.length; ++i) {

80  for (uint256 i = 0; i < _newGuardians.length; ++i) {

133 for (uint256 i; i < guardiansLength; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L74

```solidity
file: blob/main/packages/protocol/contracts/L2/TaikoL2.sol

234  for (uint256 i; i < 255 && _blockId >= i + 1; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L234


```solidity
file: blob/main/packages/protocol/contracts/signal/SignalService.sol

104  for (uint256 i; i < hopProofs.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L104

```solidity
file: blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

59  for (uint256 i; i < tokenIds.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59

```solidity
file: blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

85   for (uint256 i = 0; i < proof.length; i++) {

208  for (uint256 i = 0; i < length;) {

244  for (; shared_ < max && _a[shared_] == _b[shared_];) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol

34   for (uint256 i; i < _op.tokenIds.length; ++i) {

170  for (uint256 i; i < _tokenIds.length; ++i) {

175  for (uint256 i; i < _tokenIds.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L34

```solidity
file:  blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol

104  for (uint256 i; i < _ids.length; ++i) {

210  for (uint256 i; i < _instances.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L104


## [G-22] Do not calculate constants

Due to how constant variables are implemented (replacements at compile-time), an expression assigned to a constant variable is recomputed each time that the variable is used, which wastes some gas.

```solidity
file: blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol

21  uint256 public constant MAX_BYTES_PER_BLOB = 4096 * 32;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L21

```solidity
file: blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

24  uint256 internal constant BRANCH_NODE_LENGTH = TREE_RADIX + 1;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L24

## [G-23] do-while is cheaper than for-loops when the initial check can be skipped

Using do-while loops instead of for loops can be more gas-efficient. Even if you add an if condition to account for the case where the loop doesn't execute at all, a do-while loop can still be cheaper in terms of gas.

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

80  for (uint256 i; i < serialNumBatch.length; ++i) {

95  for (uint256 i; i < serialNumBatch.length; ++i) {

191 for (uint256 i; i < enclaveId.tcbLevels.length; ++i) {

214 for (uint256 i; i < tcb.tcbLevels.length; ++i) {

240 for (uint256 i; i < CPUSVN_LENGTH; ++i) {

259 for (uint256 i; i < n; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L80

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

54   for (uint256 i; i < size; ++i) {

244  for (uint256 i; i < split.length; ++i) {

354  for (uint256 i; i < SGX_TCB_CPUSVN_SIZE + 1; ++i) 

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L54

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

153  for (uint256 i; i < encoded.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L153

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

80   for (uint256 idx = 0; idx < shortest; idx += 32) {

333  for (uint256 i; i < len; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L80

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

140  for (uint256 i = 2; i < 2 + paddingLen; ++i) {

152  for (uint256 i; i < digestAlgoWithParamLen; ++i) {

158  for (uint256 i; i < digestAlgoWithParamLen; ++i) {

174  for (uint256 i; i < _sha256.length; ++i) {

273  for (uint256 i = 2; i < 2 + paddingLen; ++i) {

283  for (uint256 i; i < sha1Prefix.length; ++i) {

290  for (uint256 i; i < _sha1.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L140


```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

48  for (uint16 i = 1970; i < year; ++i) {

59  for (uint8 i = 1; i < month; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L48

```solidity
file: blob/main/packages/protocol/contracts/bridge/Bridge.sol

90   for (uint256 i; i < _msgHashes.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L90

```solidity
file: blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol

172   for (uint256 i; i < _tierFees.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L172

```solidity
file: blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol

86   for (uint256 i; i < deposits_.length;) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L86

```solidity
file: blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol

244  for (uint256 i; i < params.hookCalls.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L244


```solidity
file: blob/main/packages/protocol/contracts/L1/provers/Guardians.sol

74  for (uint256 i; i < guardians.length; ++i) {

80  for (uint256 i = 0; i < _newGuardians.length; ++i) {

133 for (uint256 i; i < guardiansLength; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L74

```solidity
file: blob/main/packages/protocol/contracts/L2/TaikoL2.sol

234  for (uint256 i; i < 255 && _blockId >= i + 1; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L234


```solidity
file: blob/main/packages/protocol/contracts/signal/SignalService.sol

104  for (uint256 i; i < hopProofs.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L104

```solidity
file: blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

59  for (uint256 i; i < tokenIds.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59

```solidity
file: blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

85   for (uint256 i = 0; i < proof.length; i++) {

208  for (uint256 i = 0; i < length;) {

244  for (; shared_ < max && _a[shared_] == _b[shared_];) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol

34   for (uint256 i; i < _op.tokenIds.length; ++i) {

170  for (uint256 i; i < _tokenIds.length; ++i) {

175  for (uint256 i; i < _tokenIds.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L34

```solidity
file:  blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol

104  for (uint256 i; i < _ids.length; ++i) {

210  for (uint256 i; i < _instances.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L104


## [G-24] Empty blocks should be removed or emit something

Some functions don't have a body: consider commenting why, or add some logic. Otherwise, refactor the code and remove these functions.

```solidity
file: blob/main/packages/protocol/contracts/bridge/Bridge.sol

70  receive() external payable { }

461 function _authorizePause(address)
        internal
        view
        virtual
        override
        onlyFromOwnerOrNamed("bridge_pauser")
    { }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L70

```solidity
file: blob/main/packages/protocol/contracts/common/EssentialContract.sol
 
114  function _authorizeUpgrade(address) internal virtual override onlyOwner { }

116  function _authorizePause(address) internal virtual onlyOwner { }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L114

```solidity
file: blob/main/packages/protocol/contracts/L1/TaikoL1.sol

220  function _authorizePause(address)
        internal
        view
        virtual
        override
        onlyFromOwnerOrNamed("chain_pauser")
    { }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L220

## [G-25] Nesting if-statements is cheaper than using &&

Using a double if statement instead of logical AND (&&) can provide similar short-circuiting behavior whereas double if is slightly more efficient.

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

220   if (pceSvnIsHigherOrGreater && cpuSvnsAreHigherOrGreater) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L220

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

335   require(char >= 0x30 && char <= 0x7A, "invalid char");

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L335


```solidity
file: blob/main/packages/protocol/contracts/bridge/Bridge.sol

250   if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) {

260   if (_message.gasLimit == 0 && msg.sender != _message.destOwner) {

439   } else if (block.chainid >= 32_300 && block.chainid <= 32_400) {

490   if (
            _message.data.length >= 4 // msg can be empty
                && bytes4(_message.data) != IMessageInvocable.onMessageInvocation.selector
                && _message.to.isContract()
        ) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L250

```solidity
file: blob/main/packages/protocol/contracts/common/AddressResolver.sol

85  if (!_allowZeroAddress && addr_ == address(0)) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L85

```solidity
file: blob/main/packages/protocol/contracts/common/EssentialContract.sol

42   if (msg.sender != owner() && msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L42

```solidity
file: blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol

81  if (
            block.timestamp > assignment.expiry
                || assignment.metaHash != 0 && _blk.metaHash != assignment.metaHash
                || assignment.parentMetaHash != 0 && _meta.parentMetaHash != assignment.parentMetaHash
                || assignment.maxBlockId != 0 && _meta.id > assignment.maxBlockId
                || assignment.maxProposedIn != 0 && block.number > assignment.maxProposedIn
        ) {

120  if (input.tip != 0 && block.coinbase != address(0)) {
    
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L81-L87

```solidity
file: blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol

108  if (params.parentMetaHash != 0 && parentMetaHash != params.parentMetaHash) {

164  if (_config.blobReuseEnabled && params.cacheBlobForReuse) {

310  if (proposerOne != address(0) && msg.sender != proposerOne) {
    
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L108

```solidity
file: blob/main/packages/protocol/contracts/L1/libs/LibProving.sol
 
419   if (_tid == 1 && _ts.tier == 0 && inProvingWindow) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L419

```solidity
file: blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol

127  while (blockId < b.numBlocks && numBlocksVerified < _maxBlocksToVerify) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L127

```solidity
file: blob/main/packages/protocol/contracts/L2/TaikoL2.sol

116  if (
            _l1BlockHash == 0 || _l1StateRoot == 0 || _l1BlockId == 0
                || (block.number != 1 && _parentGasUsed == 0)
        ) 

141  if (!skipFeeCheck() && block.basefee != basefee) {

275  if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {
    
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L116-L119

```solidity
file: blob/main/packages/protocol/contracts/signal/SignalService.sol

285  if (cacheStateRoot && _isFullProof && !_isLastHop) {

293  if (cacheSignalRoot && (_isFullProof || !_isLastHop)) {
    
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L285

```solidity
file: blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol

277 if (_cliff > 0 && _cliff <= _start) revert INVALID_GRANT();

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L277

```solidity
file: blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

14  if (_in.length == 1 && uint8(_in[0]) < 128) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L14


```solidity
file: blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol

38    if (msg.sender != owner() && msg.sender != snapshooter) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L38

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

45  if (_migratingAddress == migratingAddress && _migratingInbound == migratingInbound) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L45


## [G-26] Struct can be reordered to fit into fewer storage slots

In Solidity, data type packing within struct variables is a recommended practice to optimize gas usage and efficiency in smart contracts.

This technique leverages the fact that Ethereum’s storage model stores variables in slots, with each slot offering a capacity of 32 bytes. When data types that consume less than 32 bytes, such as uint8, bool, or address, are declared individually, each occupies a whole storage slot. However, when these smaller variables are grouped into a struct, they can share a storage slot, resulting in a significant reduction in storage requirements and, by extension, gas costs.

```solidity
file: blob/main/packages/protocol/contracts/bridge/IBridge.sol

17   struct Message {
        // Message ID whose value is automatically assigned.
        uint128 id;
        // The address, EOA or contract, that interacts with this bridge.
        // The value is automatically assigned.
        address from;
        // Source chain ID whose value is automatically assigned.
        uint64 srcChainId;
        // Destination chain ID where the `to` address lives.
        uint64 destChainId;
        // The owner of the message on the source chain.
        address srcOwner;
        // The owner of the message on the destination chain.
        address destOwner;
        // The destination address on the destination chain.
        address to;
        // Alternate address to send any refund on the destination chain.
        // If blank, defaults to destOwner.
        address refundTo;
        // value to invoke on the destination chain.
        uint256 value;
        // Processing fee for the relayer. Zero if owner will process themself.
        uint256 fee;
        // gasLimit to invoke on the destination chain.
        uint256 gasLimit;
        // callData to invoke on the destination chain.
        bytes data;
        // Optional memo.
        string memo;
    }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L17-L46

```solidity
file: blob/main/packages/protocol/contracts/L1/TaikoData.sol

10  struct Config {
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
        uint8 blockSyncThreshold;
    }

78  struct BlockParams {
        address assignedProver;
        address coinbase;
        bytes32 extraData;
        bytes32 blobHash;
        uint24 txListByteOffset;
        uint24 txListByteSize;
        bool cacheBlobForReuse;
        bytes32 parentMetaHash;
        HookCall[] hookCalls;
    }

94  struct BlockMetadata {
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
        bool blobUsed;
        bytes32 parentMetaHash; // slot 8
    }

122 struct TransitionState {
        bytes32 key; // slot 1, only written/read for the 1st state transition.
        bytes32 blockHash; // slot 2
        bytes32 stateRoot; // slot 3
        address prover; // slot 4
        uint96 validityBond;
        address contester; // slot 5
        uint96 contestBond;
        uint64 timestamp; // slot 6 (90 bits)
        uint16 tier;
        uint8 contestations;
    }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L10-L60

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol

23  struct BridgeTransferOp {
        // Destination chain ID.
        uint64 destChainId;
        // The owner of the bridge message on the destination chain.
        address destOwner;
        // Recipient address.
        address to;
        // Address of the token.
        address token;
        // IDs of the tokens to transfer.
        uint256[] tokenIds;
        // Amounts of tokens to transfer.
        uint256[] amounts;
        // Gas limit for the operation.
        uint256 gasLimit;
        // Processing fee for the relayer.
        uint256 fee;
        // Address for refund, if needed.
        address refundTo;
        // Optional memo.
        string memo;
    }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L23-L44

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol

23  struct CanonicalERC20 {
        uint64 chainId;
        address addr;
        uint8 decimals;
        string symbol;
        string name;
    }

32  struct BridgeTransferOp {
        uint64 destChainId;
        address destOwner;
        address to;
        address token;
        uint256 amount;
        uint256 gasLimit;
        uint256 fee;
        address refundTo;
        string memo;
    }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L23-L29

```solidity
file: blob/main/packages/protocol/contracts/verifiers/IVerifier.sol

10  struct Context {
        bytes32 metaHash;
        bytes32 blobHash;
        address prover;
        uint64 blockId;
        bool isContesting;
        bool blobUsed;
        address msgSender;
    }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/IVerifier.sol#L10-L18


## [G-27] Use assembly for small keccak256 hashes, in order to save gas

The assembly version of the keccak256 hashing function can be more gas efficient than the high-level Solidity version.

```solidity
file: blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol

146  return keccak256(
            abi.encode(
                "PROVER_ASSIGNMENT",
                ITaikoL1(_taikoL1Address).getConfig().chainId,
                _taikoL1Address,
                address(this),
                _assignment.metaHash,
                _assignment.parentMetaHash,
                _blobHash,
                _assignment.feeToken,
                _assignment.expiry,
                _assignment.maxBlockId,
                _assignment.maxProposedIn,
                _assignment.tierFees
            )

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L146-L160

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

292  bytes32 issuerPubKeyHash = keccak256(issuer.pubKey);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L292

```solidity
file: blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol

204  meta_.difficulty = keccak256(abi.encodePacked(block.prevrandao, b.numBlocks, block.number));

213  metaHash: keccak256(abi.encode(meta_)),

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L204

```solidity
file: blob/main/packages/protocol/contracts/L1/libs/LibProving.sol

121  if (blk.blockId != _meta.id || blk.metaHash != keccak256(abi.encode(_meta))) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L121

```solidity
file: blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol

170   bytes32 hash = keccak256(abi.encodePacked("Withdraw unlocked Taiko token to: ", _to));

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L170

```solidity
file: blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

93  require(
                    Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
                    "MerkleTrie: invalid root hash"
                );
99  require(
                    Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
                    "MerkleTrie: invalid large internal hash"
                );

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L93-L96

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol

174  if (
                ctoken.decimals != _ctoken.decimals
                    || keccak256(bytes(ctoken.symbol)) != keccak256(bytes(_ctoken.symbol))
                    || keccak256(bytes(ctoken.name)) != keccak256(bytes(_ctoken.name))
            ) revert VAULT_CTOKEN_MISMATCH();

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L174-L178

```solidity
file: blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol

182  return keccak256(
            abi.encode(
                "VERIFY_PROOF",
                ITaikoL1(taikoL1).getConfig().chainId,
                address(this),
                _tran,
                _newInstance,
                _prover,
                _metaHash
            )
        );

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L182-L192

## [G-28] Use assembly in place of abi.decode to save gas

Instead of using abi.decode, we can use assembly to decode our desired calldata values directly. This will allow us to avoid decoding calldata values that we will not use.

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

140   return abi.decode(ret, (uint256)) == 1;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L140

```solidity
file: blob/main/packages/protocol/contracts/L1/TaikoL1.sol

88  ) = abi.decode(_input, (TaikoData.BlockMetadata, TaikoData.Transition, TaikoData.TierProof));

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L88

```solidity
file: blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol

77  Input memory input = abi.decode(_data, (Input));

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L77

```solidity
file: blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol

78  TaikoData.BlockParams memory params = abi.decode(_data, (TaikoData.BlockParams));

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L78

```solidity
file: blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol

42  (uint64 txId, bytes memory txdata) = abi.decode(_data, (uint64, bytes));

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L42

```solidity
file: blob/main/packages/protocol/contracts/signal/SignalService.sol

94   HopProof[] memory hopProofs = abi.decode(_proof, (HopProof[]));

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L94

```solidity
file: blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

70   abi.decode(delegationData, (address, uint256, uint256, uint8, bytes32, bytes32));

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L70

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol

260  abi.decode(_data, (CanonicalERC20, address, address, uint256));

298  (bytes memory data) = abi.decode(_message.data[4:], (bytes));

300  abi.decode(data, (CanonicalERC20, address, address, uint256));

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L260

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol

84  abi.decode(_data, (CanonicalNFT, address, address, uint256[]));

123 (bytes memory data) = abi.decode(_message.data[4:], (bytes));

125 abi.decode(data, (CanonicalNFT, address, address, uint256[]));

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L84

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol

100  ) = abi.decode(data, (CanonicalNFT, address, address, uint256[], uint256[]));

140  (bytes memory data) = abi.decode(message.data[4:], (bytes));

142  abi.decode(data, (CanonicalNFT, address, address, uint256[], uint256[]));

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L100

## [G-29] Use assembly to validate msg.sender

We can use assembly to efficiently validate msg.sender with the least amount of opcodes necessary. For more details check the following report(https://code4rena.com/reports/2023-05-juicebox#g-06-use-assembly-to-validate-msgsender)

```solidity
file: blob/main/packages/protocol/contracts/bridge/Bridge.sol

250   if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) {

260   if (_message.gasLimit == 0 && msg.sender != _message.destOwner) {

294   if (msg.sender == refundTo) {

322   if (msg.sender != _message.destOwner) revert B_PERMISSION_DENIED();

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L250

```solidity
file: blob/main/packages/protocol/contracts/common/AddressResolver.sol

25  if (msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L25

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

61   require(msg.sender == owner, "onlyOwner");

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L61

```solidity
file: blob/main/packages/protocol/contracts/common/EssentialContract.sol

42   if (msg.sender != owner() && msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L42

```solidity
file: blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol

310  if (proposerOne != address(0) && msg.sender != proposerOne) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L310

```solidity
file: blob/main/packages/protocol/contracts/L2/TaikoL2.sol

123  if (msg.sender != GOLDEN_TOUCH_ADDRESS) revert L2_INVALID_SENDER();

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L123

```solidity
file: blob/main/packages/protocol/contracts/signal/SignalService.sol

77  if (!isAuthorized[msg.sender]) revert SS_UNAUTHORIZED();

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L77

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol

23  if (msg.sender != resolve("bridge", false)) {

65  if (ctx_.from != msg.sender) revert VAULT_PERMISSION_DENIED();

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L23

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol

38  if (msg.sender != owner() && msg.sender != snapshooter) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L38

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

61  if (msg.sender == migratingAddress) {

64  } else if (msg.sender != resolve("erc20_vault", true)) {

78  if (msg.sender != _account) revert BB_PERMISSION_DENIED();

83   } else if (msg.sender != resolve("erc20_vault", true)) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L61


## [G-30] Use assembly to write address/contract storage values

```solidity
file: blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol

122  taikoToken = _taikoToken;

125   costToken = _costToken;

128   sharedVault = _sharedVault;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L122

```solidity
file: blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

41   token = _token;

42   vault = _vault;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L41

```solidity
file: blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

69  token = _token;

70  vault = _vault;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L69

```solidity
file: blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

39  token = _token;

40  vault = _vault;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L39

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol

73   srcToken = _srcToken;

81   snapshooter = _snapshooter;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L73

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

49  migratingAddress = _migratingAddress;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L49

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol

47  srcToken = _srcToken;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L47

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol

56   srcToken = _srcToken;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L56


## [G-31] Use selfbalance() instead of address(this).balance

Use assembly when getting a contract's balance of ETH.

You can use selfbalance() instead of address(this).balance when getting your contract's balance of ETH to save gas. Additionally, you can use balance(address) instead of address().balance when getting an external contract's balance of ETH.

```solidity
file: blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol
 
125   if (address(this).balance > 0) {

126   taikoL1Address.sendEther(address(this).balance);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L125

```solidity
file: blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol

253  IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }(

260  if (address(this).balance != 0) {

261   msg.sender.sendEther(address(this).balance);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L253

## [G-32] Use uint256(1)/uint256(2) instead of true/false to save gas for changes

Use uint256(1) and uint256(2) for true/false to avoid a Gwarmaccess (100 gas), and to avoid Gsset (20000 gas) when changing from ‘false’ to ‘true’, after having been ‘true’ in the past. Refer to the(https://github.com/OpenZeppelin/openzeppelin-contracts/blob/5ae630684a0f57de400ef69499addab4c32ac8fb/contracts/security/ReentrancyGuard.sol#L23-L27)

```solidity 
file: blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

39   mapping(bytes32 enclave => bool trusted) private _trustedUserMrEnclave;

40   mapping(bytes32 signer => bool trusted) private _trustedUserMrSigner;

38   bool private _checkLocalEnclaveReport;

47   mapping(uint256 idx => mapping(bytes serialNum => bool revoked)) private _serialNumIsRevoked;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L39


```solidity
file: blob/main/packages/protocol/contracts/bridge/Bridge.sol

42   mapping(address addr => bool banned) public addressBanned;

84   bool _suspend

103  bool _ban

169  bool isMessageProven = receivedAt != 0;

231  bool isMessageProven = receivedAt != 0;

312  bool _isLastAttempt

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L42

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

14  bool public migratingInbound;

38  bool _migratingInbound

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L14

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol

52  mapping(address btoken => bool blacklisted) public btokenBlacklist;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L52

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

65  function setMrSigner(bytes32 _mrSigner, bool _trusted) external onlyOwner {

69  function setMrEnclave(bytes32 _mrEnclave, bool _trusted) external onlyOwner {

130 returns (bool valid)

139 (bool success,) = _verify(data);

181  bool miscselectMatched =

184  bool attributesMatched =

186  bool mrsignerMatched = quoteEnclaveReport.mrSigner == enclaveId.mrsigner;

188  bool isvprodidMatched = quoteEnclaveReport.isvProdId == enclaveId.isvprodid;

190  bool tcbFound;

216  bool pceSvnIsHigherOrGreater = pck.sgxExtension.pcesvn >= current.pcesvn;

217  bool cpuSvnsAreHigherOrGreater = _isCpuSvnHigherOrGreater(

222  bool tcbIsRevoked = status == TCBInfoStruct.TCBStatus.TCB_REVOKED;

254  bool certRevoked;

255  bool certNotExpired;

256  bool verified;

257  bool certChainCanBeTrusted;

318  bool qeReportDataIsValid = expectedAuthDataHash == computedAuthDataHash;

322  bool qeSigVerified = sigVerifyLib.verifyES256Signature(

325  bool quoteSigVerified = sigVerifyLib.verifyES256Signature(

373  bool successful,

387  bool mrEnclaveIsTrusted =

389  bool mrSignerIsTrusted = _trustedUserMrSigner[v3quote.localEnclaveReport.mrSigner];

400  bool verifiedEnclaveIdSuccessfully;

421  bool isPckCert = i == 0; // additional parsing for PCKCert

422  bool certDecodedSuccessfully;

437  bool tcbConfigured = LibString.eq(parsedFmspc, fetchedTcbInfo.fmspc);

443  bool pceidMatched = LibString.eq(pckCert.pck.sgxExtension.pceid, fetchedTcbInfo.pceid);

453  bool tcbVerified;

463  bool pckCertChainVerified = _verifyCertChain(parsedQuoteCerts);

471  bool enclaveReportSigsVerified = _enclaveReportSigVerification(

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L65

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

35   bool fmspcFound;

36   bool pceidFound;

37   bool tcbFound;

76   bool isPckCert

120  bool issuerNameIsValid = LibString.eq(cert.pck.issuerName, PLATFORM_ISSUER_NAME)

196  bool sgxExtnTraversedSuccessfully;

225  bool headerFound = beginPos != LibString.NOT_FOUND;

226  bool footerFound = endPos != LibString.NOT_FOUND;

277  bool success,

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L35

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

122  bool hasNullParam;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L122

```solidity
file: blob/main/packages/protocol/contracts/common/AddressResolver.sol

32   bool _allowZeroAddress

46   bool _allowZeroAddress

75   bool _allowZeroAddress

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L32

```solidity
file: blob/main/packages/protocol/contracts/common/IAddressResolver.sol

21   bool _allowZeroAddress

37   bool _allowZeroAddress

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressResolver.sol#L21

```solidity
file: blob/main/packages/protocol/contracts/L1/TaikoData.sol

32  bool blobAllowedForDA;

34  bool blobReuseEnabled;

85  bool cacheBlobForReuse;

108 bool blobUsed;

171  bool provingPaused;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L32

```solidity
file: blob/main/packages/protocol/contracts/L1/libs/LibProving.sol

164  bool isContesting = _proof.tier == ts.tier && tier.contestBond != 0;

186  bool isTopTier = tier.contestBond == 0;

192  bool returnLivenessBond = blk.livenessBond > 0 && _proof.data.length == 32

201  bool sameTransition = _tran.blockHash == ts.blockHash && _tran.stateRoot == ts.stateRoot;

414  bool inProvingWindow = uint256(_ts.timestamp).max(_state.slotB.lastUnpausedAt)

416  bool isAssignedPover = msg.sender == _blk.assignedProver;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L164

```solidity
file: blob/main/packages/protocol/contracts/signal/SignalService.sol

21   mapping(address addr => bool authorized) public isAuthorized;

56  function authorize(address _addr, bool _authorize) external onlyOwner {

108  bool isLastHop = i == hopProofs.length - 1;

120  bool isFullProof = hop.accountProof.length > 0;

276  bool _isFullProof,

277  bool _isLastHop

282  bool cacheStateRoot = _hop.cacheOption == CacheOption.CACHE_BOTH

290  bool cacheSignalRoot = _hop.cacheOption == CacheOption.CACHE_BOTH

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L21

```solidity
file: blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

12  mapping(bytes32 hash => bool claimed) public isClaimed;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L12

```solidity
file: blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol

55  mapping(address instanceAddress => bool alreadyAttested) public addressRegistered;

197 bool instantValid

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L55

## [G-33] Using storage instead of memory for structs/arrays saves gas

When fetching data from a storage location, assigning the data to a memory variable causes all fields of the struct/array to be read from storage, which incurs a Gcoldsload (2100 gas) for each field of the struct/array. If the fields are read from the new memory variable, they incur an additional MLOAD rather than a cheap stack read. Instead of declearing the variable with the memory keyword, declaring the variable with the storage keyword and caching any fields that need to be re-read in stack variables, will be much cheaper, only incuring the Gcoldsload for the fields actually read. The only time it makes sense to read the whole struct/array into a memory variable, is if the full struct/array is being returned by the function, is being passed to a function that requires memory, or if the array/struct is being read from another memory array/struct

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

299  PCKTCBFlags memory flags;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L299

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

52   V3Struct.EnclaveReport memory localEnclaveReport = parseEnclaveReport(rawLocalEnclaveReport);

75   V3Struct.EnclaveReport memory pckSignedQeReport = v3Quote.v3AuthData.pckSignedQeReport;

276  IPEMCertChainLib.ECSha256Certificate[] memory parsedQuoteCerts;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L52

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

56   uint8[12] memory monthDays = [31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31];

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L56

```solidity
file: blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol

17   address[] memory nil = new address[](0);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L17

```solidity
file: blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol

77   Input memory input = abi.decode(_data, (Input));

78   ProverAssignment memory assignment = input.assignment

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L77

```solidity
file: blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol

78   TaikoData.BlockParams memory params = abi.decode(_data, (TaikoData.BlockParams));

93   TaikoData.SlotB memory b = _state.slotB;

212  TaikoData.Block memory blk = TaikoData.Block({

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L78

```solidity
file: blob/main/packages/protocol/contracts/L1/libs/LibProving.sol

110  TaikoData.SlotB memory b = _state.slotB;

140  ITierProvider.Tier memory tier =

166  IVerifier.Context memory ctx = IVerifier.Context({

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L110

```solidity
file: blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol

33   TaikoData.SlotB memory b = _state.slotB;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L33

```solidity
file: blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol

45   IBridge.Context memory ctx = IBridge(msg.sender).context();

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L45

```solidity
file: blob/main/packages/protocol/contracts/L2/TaikoL2.sol

136  Config memory config = getConfig();

228  bytes32[256] memory inputs;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L136

```solidity
file: blob/main/packages/protocol/contracts/signal/SignalService.sol

94    HopProof[] memory hopProofs = abi.decode(_proof, (HopProof[]));

103   HopProof memory hop;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L94

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol

44  IBridge.Message memory message = IBridge.Message({

87  IBridge.Context memory ctx = checkProcessMessageContext();

```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L44


```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

180   EnclaveIdStruct.EnclaveId memory enclaveId = qeIdentity;

192   EnclaveIdStruct.TcbLevel memory tcb = enclaveId.tcbLevels[i];

215   TCBInfoStruct.TCBLevelObj memory current = tcb.tcbLevels[i];

260   IPEMCertChainLib.ECSha256Certificate memory issuer;

377   V3Struct.ECDSAQuoteV3AuthData memory authDataV3

415   IPEMCertChainLib.ECSha256Certificate[] memory parsedQuoteCerts;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L180

## [G-34] State variables can be packed into fewer storage slots

Each slot saved can avoid an extra Gsset (20000 gas). Reads and writes (if two variables that occupy the same slot are written by the same function) will have a cheaper gas consumption.

```solidity
file: blob/main/packages/protocol/contracts/L2/TaikoL2.sol
 
32      address public constant GOLDEN_TOUCH_ADDRESS = 0x0000777735367b36bC9B61C50022d9D0700dB4Ec;

    /// @notice The number of L2 blocks to wait before syncing L1 block details.
    uint8 public constant BLOCK_SYNC_THRESHOLD = 5;

    /// @notice Mapping from L2 block numbers to their block hashes. All L2 block hashes will
    /// be saved in this mapping.
    mapping(uint256 blockId => bytes32 blockHash) public l2Hashes;

    /// @notice A hash to check the integrity of public inputs.
    /// @dev Slot 2.
    bytes32 public publicInputHash;

    /// @notice The gas excess value used to calculate the base fee.
    /// @dev Slot 3.
    uint64 public gasExcess;

    /// @notice The last synced L1 block height.
    uint64 public lastSyncedBlock;

    uint256[47] private __gap;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L32-L52


```solidity
file: blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol

22     address public srcToken;

    uint8 private __srcDecimals;

    /// @dev Slot 2.
    uint256 public srcChainId;

    /// @dev Slot 3.
    address public snapshooter;

    uint256[47] private __gap;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L22-L32

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol

16  address public srcToken;

    /// @notice Source chain ID where the token originates.
    uint256 public srcChainId;

    /// @dev Symbol of the bridged token.
    string private __symbol;

    /// @dev Name of the bridged token.
    string private __name;

    uint256[46] private __gap;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L16-L27

## [G-35] Multiple mappings that share an ID can be combined into a single mapping of ID / struct

This can avoid a Gsset (20000 Gas) per mapping combined. Reads and writes will also be cheaper when a function requires both values as they both can fit in the same storage slot.

Finally, if both fields are accessed in the same function, this can save ~42 gas per access due to not having to recalculate the key's keccak256 hash (Gkeccak256 - 30 Gas) and that calculation's associated stack operations.

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

39    mapping(bytes32 enclave => bool trusted) private _trustedUserMrEnclave;

40    mapping(bytes32 signer => bool trusted) private _trustedUserMrSigner;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L39-L40

```solidity
file: blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

22     mapping(address addr => uint256 amountClaimed) public claimedAmount;

     /// @notice Represents the already withdrawn amount.
      mapping(address addr => uint256 amountWithdrawn) public withdrawnAmount;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L22-L25


## [G-36] Cache state variables outside of loop to avoid reading storage on every iteration

Reading from storage should always try to be avoided within loops. In the following instances, we are able to cache state variables outside of the loop to save a Gwarmaccess (100 gas) per loop iteration.

### Cache minGuardians outside the loop

```solidity
file: blob/main/packages/protocol/contracts/L1/provers/Guardians.sol

133 for (uint256 i; i < guardiansLength; ++i) {
                if (bits & 1 == 1) ++count;
                if (count == minGuardians) return true;
                bits >>= 1;
            }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L133-L137

### Cache vault outside the loop

```solidity
file: blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

59   for (uint256 i; i < tokenIds.length; ++i) {
            IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);
        }
``` 
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59-L61

### Cache nextInstanceId outside the loop

```solidity
file: blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol

210   for (uint256 i; i < _instances.length; ++i) {
            if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();

            addressRegistered[_instances[i]] = true;

            if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();

            instances[nextInstanceId] = Instance(_instances[i], validSince);
            ids[i] = nextInstanceId;

            emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);

            nextInstanceId++;
        }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210-L223

## [G-37] Pre-calculate keccak256 for constant variables 

```solidity
file: blob/main/packages/protocol/contracts/L1/libs/LibProving.sol

20  bytes32 public constant RETURN_LIVENESS_BOND = keccak256("RETURN_LIVENESS_BOND");

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L20

```solidity
file: blob/main/packages/protocol/contracts/signal/LibSignals.sol

8   bytes32 public constant STATE_ROOT = keccak256("STATE_ROOT");

11  bytes32 public constant SIGNAL_ROOT = keccak256("SIGNAL_ROOT");
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/LibSignals.sol#L8

## [G-38] Use constants instead of type(uintX).max

```solidity
file: blob/main/packages/protocol/contracts/bridge/Bridge.sol

27  uint256 internal constant PLACEHOLDER = type(uint256).max;

89  uint64 _timestamp = _suspend ? type(uint64).max : uint64(block.timestamp);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L27

```solidity
file: blob/main/packages/protocol/contracts/common/AddressResolver.sol

59  if (block.chainid > type(uint64).max) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L59


```solidity 
file: blob/main/packages/protocol/contracts/L1/TaikoL1.sol

70  LibVerifying.verifyBlocks(state, config, this, config.maxBlocksToVerifyPerProposal);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L70

```solidity
file: blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol

150  if (_amount > type(uint96).max) revert L1_INVALID_ETH_DEPOSIT();

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L150

```solidity
file: blob/main/packages/protocol/contracts/L1/libs/LibProving.sol

414  bool inProvingWindow = uint256(_ts.timestamp).max(_state.slotB.lastUnpausedAt)

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L414


```solidity
file: blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol

153   + uint256(ts.timestamp).max(_state.slotB.lastUnpausedAt) > block.timestamp

260   || _config.ethDepositMaxAmount > type(uint96).max || _config.ethDepositGas == 0

262   || _config.ethDepositMaxFee > type(uint96).max / _config.ethDepositMaxCountPerBlock

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L153

```solidity
file: blob/main/packages/protocol/contracts/L1/provers/Guardians.sol

63   if (_newGuardians.length < MIN_NUM_GUARDIANS || _newGuardians.length > type(uint8).max) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L63

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

91  mask = type(uint256).max; // aka 0xffffff....

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L91


```solidity
file: blob/main/packages/protocol/contracts/L2/TaikoL2.sol
 
82  if (block.chainid <= 1 || block.chainid > type(uint64).max) {

284  gasExcess_ = uint64(excess.min(type(uint64).max));

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L82


## [G-39] Use of emit inside a loop

Emitting an event inside a loop performs a LOG op N times, where N is the loop length. This can lead to significant gas costs.


```solidity
file: blob/main/packages/protocol/contracts/bridge/Bridge.sol

93  emit MessageSuspended(msgHash, _suspend);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#93


```solidity
file: blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol

220  emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220

## [G-40] Consider Merge Sequential For-Loops

Detects instances where multiple for-loops appear sequentially in the same function. This may indicate an opportunity for loop fusion, a code optimization technique that merges multiple loops into a single one.

```solidity
file:

/// @audit the same condation is used in line 158

152  for (uint256 i; i < digestAlgoWithParamLen; ++i) {

```

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol

/// @audit the same condation is used in line 175

170  for (uint256 i; i < _tokenIds.length; ++i) {

/// @audit the same condation is used in line 210

197  for (uint256 i; i < _op.tokenIds.length; ++i) {
    
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L170


```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol
 
/// @audit the same condation is used in line 269

251  for (uint256 i; i < _op.tokenIds.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L251


## [G-41] Mappings not used externally/internally can be marked private

The below mappings from the MaxHeap.sol contract can be marked private since they’re not used by any other contracts.

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol

56  mapping(address btoken => CanonicalNFT canonical) public bridgedToCanonical;

59  mapping(uint256 chainId => mapping(address ctoken => address btoken)) public canonicalToBridged;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L56       


## [G-42] Redundant state variable getters

Getters for public state variables are automatically generated by the solidity compiler so there is no need to code them manually as this increases deployment cost.

### Make recipients mapping variable private or internal since a getter function was defined for it.

The solidity compiler would automatically create a getter function for the recipients mapping since it is declared as a public variable but a getter function getMyGrant() was also declared in the contract for the same variable thereby making it two getter functions for the same variable in the contract. We could rectify this issue by making the recipients variable private or internal (if the variable is to be inherited).

```solidity
file: blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol

80  mapping(address recipient => Recipient receipt) public recipients;

204  function getMyGrant(address _recipient) public view returns (Grant memory) {
        return recipients[_recipient].grant;
    }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L204-L206


## [G-43] Use assembly for loops

In the following instances, assembly is used for more gas efficient loops. The only memory slots that are manually used in the loops are scratch space (0x00-0x20), the free memory pointer (0x40), and the zero slot (0x60). This allows us to avoid using the free memory pointer to allocate new memory, which may result in memory expansion costs.

Note that in order to do this optimization safely we will need to cache and restore the free memory pointer after the loop. We will also set the zero slot (0x60) back to 0.


```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

240  for (uint256 i; i < CPUSVN_LENGTH; ++i) {
            if (pckCpuSvns[i] < tcbCpuSvns[i]) {
                return false;
            }
        }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L240-L244

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

244  for (uint256 i; i < split.length; ++i) {
            contentStr = LibString.concat(contentStr, split[i]);
        }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L244-L246

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

281  for (uint256 i; i < 3; ++i) {
            quoteCerts[i] = Base64.decode(string(quoteCerts[i]));
        }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L281-L283

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

140   for (uint256 i = 2; i < 2 + paddingLen; ++i) {
            if (decipher[i] != 0xff) {
                return false;
            }
        }

152   for (uint256 i; i < digestAlgoWithParamLen; ++i) {
                if (decipher[3 + paddingLen + i] != bytes1(sha256ExplicitNullParam[i])) {
                    return false;
                }
            }

158   for (uint256 i; i < digestAlgoWithParamLen; ++i) {
                if (decipher[3 + paddingLen + i] != bytes1(sha256ImplicitNullParam[i])) {
                    return false;
                }
            }
174   for (uint256 i; i < _sha256.length; ++i) {
            if (decipher[5 + paddingLen + digestAlgoWithParamLen + i] != _sha256[i]) {
                return false;
            }
        }

273  for (uint256 i = 2; i < 2 + paddingLen; ++i) {
            if (decipher[i] != 0xff) {
                return false;
            }
        }

283  for (uint256 i; i < sha1Prefix.length; ++i) {
            if (decipher[3 + paddingLen + i] != bytes1(sha1Prefix[i])) {
                return false;
            }
        }

290  for (uint256 i; i < _sha1.length; ++i) {
            if (decipher[3 + paddingLen + sha1Prefix.length + i] != _sha1[i]) {
                return false;
            }
        }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L140-L144

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

59  for (uint8 i = 1; i < month; ++i) {
            timestamp += uint256(monthDays[i - 1]) * 86_400; // Days in seconds
        }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L59

```solidity
file: blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol

172  for (uint256 i; i < _tierFees.length; ++i) {
            if (_tierFees[i].tier == _tierId) return _tierFees[i].fee;
        }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L172-L174

```solidity
file: blob/main/packages/protocol/contracts/L1/provers/Guardians.sol

74  for (uint256 i; i < guardians.length; ++i) {
            delete guardianIds[guardians[i]];
        }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L74-L76


```solidity
file: blob/main/packages/protocol/contracts/L2/TaikoL2.sol
 
234  for (uint256 i; i < 255 && _blockId >= i + 1; ++i) {
                uint256 j = _blockId - i - 1;
                inputs[j % 255] = blockhash(j);
            }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L234-L237

```solidity
file: blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

59  for (uint256 i; i < tokenIds.length; ++i) {
            IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);
        }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59-L60

```solidity
file: blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

66   for (uint256 j = 0; j < out_.length; j++) {
            out_[j] = b[i++];
        }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66-L68


```solidity
file: blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

208  for (uint256 i = 0; i < length;) {
            proof_[i] = TrieNode({ encoded: _proof[i], decoded: RLPReader.readList(_proof[i]) });
            unchecked {
                ++i;
            }
        }

244  for (; shared_ < max && _a[shared_] == _b[shared_];) {
            unchecked {
                ++shared_;
            }
        }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L208-L213


```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol

34  for (uint256 i; i < _op.tokenIds.length; ++i) {
            if (_op.amounts[i] != 0) revert VAULT_INVALID_AMOUNT();
        }

170  for (uint256 i; i < _tokenIds.length; ++i) {
                IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);
            }

175  for (uint256 i; i < _tokenIds.length; ++i) {
                BridgedERC721(token_).mint(_to, _tokenIds[i]);
            }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L34-L36

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol

47  for (uint256 i; i < _op.amounts.length; ++i) {
            if (_op.amounts[i] == 0) revert VAULT_INVALID_AMOUNT();
        }

251 for (uint256 i; i < _op.tokenIds.length; ++i) {
                    BridgedERC1155(_op.token).burn(_user, _op.tokenIds[i], _op.amounts[i]);
                }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L47-L49

## [G‑44] require()/revert() strings longer than 32 bytes cost extra gas

```solidity
file:  blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

37  require(
            _in.length > 0,
            "RLPReader: length of an RLP item must be greater than zero to be decodable"
        );

56  require(
            itemType == RLPItemType.LIST_ITEM,
            "RLPReader: decoded item type for list is not a list item"
        );

61  require(
            listOffset + listLength == _in.length,
            "RLPReader: list item has an invalid data remainder"
        );

112  require(
            itemType == RLPItemType.DATA_ITEM,
            "RLPReader: decoded item type for bytes is not a data item"
        );

117  require(
            _in.length == itemOffset + itemLength,
            "RLPReader: bytes value contains an invalid remainder"
        );

152  require(
            _in.length > 0,
            "RLPReader: length of an RLP item must be greater than zero to be decodable"
        );

172  require(
                _in.length > strLen,
                "RLPReader: length of content must be greater than string length (short string)"
            );

182  require(
                strLen != 1 || firstByteOfContent >= 0x80,
                "RLPReader: invalid prefix, single byte < 0x80 are not prefixed (short string)"
            );

192  require(
                _in.length > lenOfStrLen,
                "RLPReader: length of content must be > than length of string length (long string)"
            );

202  require(
                firstByteOfContent != 0x00,
                "RLPReader: length of content must not have any leading zeros (long string)"
            );

212  require(
                strLen > 55,
                "RLPReader: length of content must be greater than 55 bytes (long string)"
            );

217  require(
                _in.length > lenOfStrLen + strLen,
                "RLPReader: length of content must be greater than total length (long string)"
            );

228  require(
                _in.length > listLen,
                "RLPReader: length of content must be greater than list length (short list)"
            );

238  require(
                _in.length > lenOfListLen,
                "RLPReader: length of content must be > than length of list length (long list)"
            );

248  require(
                firstByteOfContent != 0x00,
                "RLPReader: length of content must not have any leading zeros (long list)"
            );

258  require(
                listLen > 55,
                "RLPReader: length of content must be greater than 55 bytes (long list)"
            );

263  require(
                _in.length > lenOfListLen + listLen,
                "RLPReader: length of content must be greater than total length (long list)"
            );

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L37-L40

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol
 
77  require(
            localEnclaveReport.reserved3.length == 96 && localEnclaveReport.reserved4.length == 60
                && localEnclaveReport.reportData.length == 64,
            "local QE report has wrong length"
        );

82  require(
            pckSignedQeReport.reserved3.length == 96 && pckSignedQeReport.reserved4.length == 60
                && pckSignedQeReport.reportData.length == 64,
            "QE report has wrong length"
        );

87  require(
            v3Quote.v3AuthData.certification.certType == 5,
            "certType must be 5: Concatenated PCK Cert Chain (PEM formatted)"
        );

94  require(
            v3Quote.v3AuthData.ecdsa256BitSignature.length == 64
                && v3Quote.v3AuthData.ecdsaAttestationKey.length == 64
                && v3Quote.v3AuthData.qeReportSignature.length == 64,
            "Invalid ECDSA signature format"
        );

100  require(
            v3Quote.v3AuthData.qeAuthData.parsedDataSize
                == v3Quote.v3AuthData.qeAuthData.data.length,
            "Invalid QEAuthData size"
        );

116   require(totalQuoteSize >= MINIMUM_QUOTE_LENGTH, "Invalid quote size");

279   require(certParsedSuccessfully, "splitCertificateChain failed");

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L77-L81


```solidity
file: blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

77  require(_key.length > 0, "MerkleTrie: empty key");

89  require(currentKeyIndex <= key.length, "MerkleTrie: key index exceeds total key length");

93  require(
                    Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
                    "MerkleTrie: invalid root hash"
                );

99  require(
                    Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
                    "MerkleTrie: invalid large internal hash"
                );

105  require(
                    Bytes.equal(currentNode.encoded, currentNodeID),
                    "MerkleTrie: invalid internal node hash"
                );

119  require(
                        value_.length > 0,
                        "MerkleTrie: value length must be greater than zero (branch)"
                    );

125  require(
                        i == proof.length - 1,
                        "MerkleTrie: value node must be last node in proof (branch)"
                    );

150  require(
                    pathRemainder.length == sharedNibbleLength,
                    "MerkleTrie: path remainder must share all nibbles with key"
                );

162  require(
                        keyRemainder.length == sharedNibbleLength,
                        "MerkleTrie: key remainder must be identical to path remainder"
                    );

172  require(
                        value_.length > 0,
                        "MerkleTrie: value length must be greater than zero (leaf)"
                    );

178  require(
                        i == proof.length - 1,
                        "MerkleTrie: value node must be last node in proof (leaf)"
                    );

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L77

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

57   require(der[ptr.ixs()] == 0x03, "Not type BIT STRING");

67   require(der[ptr.ixs()] == 0x04, "Not type OCTET STRING");

88   require(der[ptr.ixs()] & 0x20 == 0x20, "Not a constructed type");

142  require(der[ptr.ixs()] == 0x02, "Not type INTEGER");

155  require(der[ptr.ixs()] == 0x02, "Not type INTEGER");

180  require(der[ptr.ixs()] == 0x03, "ixs Not type BIT STRING 0x03");

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L57

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

25  require(offset + len <= self.length, "invalid offset");

293 require(offset + len <= self.length, "unexpected offset");

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L25

```solidity
file: blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol

25  require(_length + 31 >= _length, "slice_overflow");

26  require(_start + _length >= _start, "slice_overflow");

27  require(_bytes.length >= _start + _length, "slice_outOfBounds");

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L25