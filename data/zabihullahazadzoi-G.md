### Gas Optimizations


## [GAS-1] Increments can be unchecked to save gas
Using unchecked increments can save gas by bypassing the built-in overflow checks. This can save 30-40 gas per iteration. So it is recommended to use unchecked increments when overflow is not possible.

**Total Instances:** 45
**Gas per instance:** 60
**Total Gas saved:** 2700

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

 172:         for (uint256 i; i < _tierFees.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L172

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

 244:             for (uint256 i; i < params.hookCalls.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L244

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

 74:         for (uint256 i; i < guardians.length; ++i) {

 80:         for (uint256 i = 0; i < _newGuardians.length; ++i) {

 133:             for (uint256 i; i < guardiansLength; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L74

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

 234:             for (uint256 i; i < 255 && _blockId >= i + 1; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L234

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

 80:         for (uint256 i; i < serialNumBatch.length; ++i) {

 95:         for (uint256 i; i < serialNumBatch.length; ++i) {

 191:         for (uint256 i; i < enclaveId.tcbLevels.length; ++i) {

 214:         for (uint256 i; i < tcb.tcbLevels.length; ++i) {

 240:         for (uint256 i; i < CPUSVN_LENGTH; ++i) {

 259:         for (uint256 i; i < n; ++i) {

 420:             for (uint256 i; i < 3; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L80

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

 54:         for (uint256 i; i < size; ++i) {

 244:         for (uint256 i; i < split.length; ++i) {

 354:         for (uint256 i; i < SGX_TCB_CPUSVN_SIZE + 1; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L54

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

 153:         for (uint256 i; i < encoded.length; ++i) {

 281:         for (uint256 i; i < 3; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L153

```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

 333:         for (uint256 i; i < len; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L333

```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

 140:         for (uint256 i = 2; i < 2 + paddingLen; ++i) {

 152:             for (uint256 i; i < digestAlgoWithParamLen; ++i) {

 158:             for (uint256 i; i < digestAlgoWithParamLen; ++i) {

 174:         for (uint256 i; i < _sha256.length; ++i) {

 273:         for (uint256 i = 2; i < 2 + paddingLen; ++i) {

 283:         for (uint256 i; i < sha1Prefix.length; ++i) {

 290:         for (uint256 i; i < _sha1.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L140

```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

 48:         for (uint16 i = 1970; i < year; ++i) {

 59:         for (uint8 i = 1; i < month; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L48

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 90:         for (uint256 i; i < _msgHashes.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L90

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

 104:         for (uint256 i; i < hopProofs.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L104

```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

 59:         for (uint256 i; i < tokenIds.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

 46:             for (i = 1; i <= lenLen; i++) {

 59:         for (; i < 32; i++) {

 66:         for (uint256 j = 0; j < out_.length; j++) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L46

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

 85:         for (uint256 i = 0; i < proof.length; i++) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

 47:         for (uint256 i; i < _op.amounts.length; ++i) {

 251:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

 269:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L47

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

 34:         for (uint256 i; i < _op.tokenIds.length; ++i) {

 170:             for (uint256 i; i < _tokenIds.length; ++i) {

 175:             for (uint256 i; i < _tokenIds.length; ++i) {

 197:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

 210:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L34

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

 104:         for (uint256 i; i < _ids.length; ++i) {

 210:         for (uint256 i; i < _instances.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210


## [GAS-2] Use `selfbalance()` instead of `address(this).balance`
Use assembly when getting a contract's balance of ETH.

You can use `selfbalance()` instead of `address(this).balance` when getting your contract's balance of ETH to save gas.
Additionally, you can use `balance(address)` instead of `address.balance()` when getting an external contract's balance of ETH.

*Saves 15 gas when checking internal balance, 6 for external*

**Total Instances:** 6

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

 125:         if (address(this).balance > 0) {

 126:             taikoL1Address.sendEther(address(this).balance);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L125

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

 253:                 IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }(

 260:             if (address(this).balance != 0) {

 261:                 msg.sender.sendEther(address(this).balance);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L253

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

 174:             _to.sendEther(address(this).balance);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L174


## [GAS-3] Avoid emitting storage values
Caching of a state variable replaces each Gwarmaccess (100 gas) with a much cheaper stack read. We can avoid unecessary SLOADs by caching storage values that were previously accessed and emitting those cached values.

**Total Instances:** 7

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

 /// @audit  cache version
 95:         emit GuardiansUpdated(version, _newGuardians);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L95

```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

 /// @audit  cache nextTxId
 53:         emit TransactionExecuted(nextTxId++, bytes4(txdata));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L53

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

 /// @audit  cache gasExcess
 157:         emit Anchored(blockhash(parentId), gasExcess);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L157

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

 /// @audit  cache migratingAddress
 63:             emit MigratedTo(migratingAddress, _account, _amount);

 /// @audit  cache migratingAddress
 80:             emit MigratedTo(migratingAddress, _account, _amount);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L63

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

 /// @audit  cache instances
 109:             emit InstanceDeleted(idx, instances[idx].addr);

 /// @audit  cache nextInstanceId
 220:             emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220


## [GAS-4]  Avoid updating storage when the value hasn’t changed
If the old value is equal to the new value, not re-storing the value will avoid a Gsreset (2900 gas), potentially at the expense of a Gcoldsload (2100 gas) or a Gwarmaccess (100 gas)

**Total Instances:** 58
**Gas per instance:** 800
**Total Gas saved:** 46400

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

 94:         minGuardians = _minGuardians;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L94

```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

 73:         ownerChainId = _ownerChainId;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L73

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

 91:             l2Hashes[parentHeight] = blockhash(parentHeight);

 96:         gasExcess = _gasExcess;

 151:             lastSyncedBlock = _l1BlockId;

 154:         l2Hashes[parentId] = blockhash(parentId);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L91

```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

 36:         customConfig = _newConfig;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L36

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

 66:         _trustedUserMrSigner[_mrSigner] = _trusted;

 70:         _trustedUserMrEnclave[_mrEnclave] = _trusted;

 111:         tcbInfo[fmspc] = tcbInfoInput;

 119:         qeIdentity = qeIdentityInput;

 123:         _checkLocalEnclaveReport = !_checkLocalEnclaveReport;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L66

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 92:             proofReceipt[msgHash].receivedAt = _timestamp;

 184:             proofReceipt[msgHash].receivedAt = receivedAt;

 243:                 proofReceipt[msgHash] = ProofReceipt({

 549:             __ctx = Context(_msgHash, _from, _srcChainId);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L92

```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

 70:         __paused = _TRUE;

 79:         __paused = _FALSE;

 111:         __paused = _FALSE;

 125:             __reentry = _reentry;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L70

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

 122:         taikoToken = _taikoToken;

 125:         costToken = _costToken;

 128:         sharedVault = _sharedVault;

 141:         totalAmountGranted += _grant.amount;

 142:         recipients[_recipient].grant = _grant;

 156:         totalAmountVoided += amountVoided;

 216:         totalAmountWithdrawn += amountToWithdraw;

 217:         totalCostPaid += costToWithdraw;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L122

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

 41:         token = _token;

 42:         vault = _vault;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L41

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

 69:         token = _token;

 70:         vault = _vault;

 71:         withdrawalWindow = _withdrawalWindow;

 83:         claimedAmount[user] += amount;

 90:         withdrawnAmount[user] += amount;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L69

```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

 39:         token = _token;

 40:         vault = _vault;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L39

```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

 91:         claimStart = _claimStart;

 92:         claimEnd = _claimEnd;

 93:         merkleRoot = _merkleRoot;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L91

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

 56:         srcToken = _srcToken;

 57:         srcChainId = _srcChainId;

 58:         __symbol = _symbol;

 59:         __name = _name;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L56

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

 73:         srcToken = _srcToken;

 74:         srcChainId = _srcChainId;

 75:         __srcDecimals = _decimals;

 81:         snapshooter = _snapshooter;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L73

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

 49:         migratingAddress = _migratingAddress;

 50:         migratingInbound = _migratingInbound;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L49

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

 47:         srcToken = _srcToken;

 48:         srcChainId = _srcChainId;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L47

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

 181:             btokenBlacklist[btokenOld_] = true;

 188:         bridgedToCanonical[_btokenNew] = _ctoken;

 422:         bridgedToCanonical[btoken] = ctoken;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L181

```solidity
File: packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

 40:         usdc = _usdc;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L40

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

 217:             instances[nextInstanceId] = Instance(_instances[i], validSince);

 229:         instances[id] = Instance(newInstance, uint64(block.timestamp));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L229


## [GAS-6] bytes constants are more efficient than string constants
If the data can fit in 32 bytes, the bytes32 data type can be used instead of bytes or strings, as it is more gas efficient and less robust in terms of robustness.

**Total Instances:** 5

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

 17:     string internal constant HEADER = "-----BEGIN CERTIFICATE-----";

 18:     string internal constant FOOTER = "-----END CERTIFICATE-----";

 22:     string internal constant PCK_COMMON_NAME = "Intel SGX PCK Certificate";

 23:     string internal constant PLATFORM_ISSUER_NAME = "Intel SGX PCK Platform CA";

 24:     string internal constant PROCESSOR_ISSUER_NAME = "Intel SGX PCK Processor CA";

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L24


## [GAS-8] Multiple accesses of the same mapping/array key/index should be cached
The instances below point to the second+ access of a value inside a mapping/array, within a function. Caching a mapping’s value in a local storage or calldata variable when the value is accessed multiple times, saves ~42 gas per access due to not having to recalculate the key’s keccak256 hash (Gkeccak256 - 30 gas) and that calculation’s associated stack operations. Caching an array’s struct avoids recalculating the array offsets into memory/calldata

**Total Instances:** 26
**Gas per instance:** 42
**Total Gas saved:** 1092

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

 173:             if (_tierFees[i].tier == _tierId) return _tierFees[i].fee;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L173

```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

 93:                 uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L93

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

 116:             _approvals[version][_hash] |= 1 << (id - 1);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L116

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

 84:             _serialNumIsRevoked[index][serialNumBatch[i]] = true;

 84:             _serialNumIsRevoked[index][serialNumBatch[i]] = true;

 99:             delete _serialNumIsRevoked[index][serialNumBatch[i]];

 99:             delete _serialNumIsRevoked[index][serialNumBatch[i]];

 286:                 certs[i].tbsCertificate, certs[i].signature, issuer.pubKey

 472:                 parsedQuoteCerts[0].pubKey,

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L84

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

 282:             quoteCerts[i] = Base64.decode(string(quoteCerts[i]));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L282

```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

 21:             yrs += (uint8(x509Time[0]) - 48) * 1000 + (uint8(x509Time[1]) - 48) * 100;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L21

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 190:             delete proofReceipt[msgHash];

 264:             delete proofReceipt[msgHash];

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L190

```solidity
File: packages/protocol/contracts/common/AddressManager.sol

 49:         __addresses[_chainId][_name] = _newAddress;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressManager.sol#L49

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

 248:             topBlockId[_chainId][_kind] = _blockId;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L248

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

 35:             out_[0] = bytes1(uint8(_len) + uint8(_offset));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L35

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

 209:             proof_[i] = TrieNode({ encoded: _proof[i], decoded: RLPReader.readList(_proof[i]) });

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L209

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

 250:                 ctoken_ = bridgedToCanonical[_op.token];

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L250

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

 180:             delete bridgedToCanonical[_btokenNew];

 189:         canonicalToBridged[_ctoken.chainId][_ctoken.addr] = _btokenNew;

 359:             ctoken_ = bridgedToCanonical[_token];

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L180

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

 171:                 IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);

 196:                 ctoken_ = bridgedToCanonical[_op.token];

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L171

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

 107:             if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();

 220:             emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);

 236:         return instances[id].validSince <= block.timestamp

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L236


## [GAS-9] The result of a function call should be cached rather than re-calling the function
The function calls in solidity are expensive. If the same result of the same function calls are to be used several times, the result should be cached to reduce the gas consumption of repeated calls.

**Total Instances:** 6
**Gas per instance:** 100
**Total Gas saved:** 600

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

 260:                 || _config.ethDepositMaxAmount > type(uint96).max || _config.ethDepositGas == 0

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L260

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

 157:         emit Anchored(blockhash(parentId), gasExcess);

 176:             IERC20(_token).safeTransfer(_to, IERC20(_token).balanceOf(address(this)));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L157

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

 177:             bytes memory sigY = _trimBytes(der.bytesAt(sigPtr), 32);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L177

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 283:                     _updateMessageStatus(msgHash, Status.DONE);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L283

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

 100:                     Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L100


## [GAS-10] State variables that are used multiple times in a function should be cached in stack variables
When performing multiple operations on a state variable in a function, it is recommended to cache it first. Either multiple reads or multiple writes to a state variable can save gas by caching it on the stack. Caching of a state variable replaces each Gwarmaccess (100 gas) with a much cheaper stack read. Other less obvious fixes/optimizations include having local memory caches of state variable structs, or having local caches of state variable contracts/addresses. Saves 100 gas per instance.

**Total Instances:** 30
**Gas per instance:** 100
**Total Gas saved:** 3000

```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

 70:             LibVerifying.verifyBlocks(state, config, this, config.maxBlocksToVerifyPerProposal);

 96:         LibVerifying.verifyBlocks(state, config, this, maxBlocksToVerify);

 154:             ts_ = state.transitions[slot][blk_.verifiedTransitionId];

 182:         b_ = state.slotB;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L70

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

 75:             delete guardianIds[guardians[i]];

 116:             _approvals[version][_hash] |= 1 << (id - 1);

 116:             _approvals[version][_hash] |= 1 << (id - 1);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L75

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

 140:         (basefee, gasExcess) = _calc1559BaseFee(config, _l1BlockId, _parentGasUsed);

 265:             uint256 excess = uint256(gasExcess) + _parentGasUsed;

 276:                 numL1Blocks = _l1BlockId - lastSyncedBlock;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L140

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

 84:             _serialNumIsRevoked[index][serialNumBatch[i]] = true;

 99:             delete _serialNumIsRevoked[index][serialNumBatch[i]];

 123:         _checkLocalEnclaveReport = !_checkLocalEnclaveReport;

 237:         if (pckCpuSvns.length != CPUSVN_LENGTH || tcbCpuSvns.length != CPUSVN_LENGTH) {

 271:                     certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.PCK)][certs[i]

 325:             bool quoteSigVerified = sigVerifyLib.verifyES256Signature(

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L84

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

 354:         for (uint256 i; i < SGX_TCB_CPUSVN_SIZE + 1; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L354

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 533:             _storeContext(bytes32(PLACEHOLDER), address(uint160(PLACEHOLDER)), uint64(PLACEHOLDER));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L533

```solidity
File: packages/protocol/contracts/common/AddressManager.sol

 49:         __addresses[_chainId][_name] = _newAddress;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressManager.sol#L49

```solidity
File: packages/protocol/contracts/libs/Lib4844.sol

 57:         if (uint256(first) != FIELD_ELEMENTS_PER_BLOB || uint256(second) != BLS_MODULUS) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/Lib4844.sol#L57

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

 248:             topBlockId[_chainId][_kind] = _blockId;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L248

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

 220:         IERC20(costToken).safeTransferFrom(_recipient, sharedVault, costToWithdraw);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L220

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

 71:         IVotes(token).delegateBySig(delegatee, nonce, expiry, v, r, s);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L71

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

 118:             * (block.timestamp.min(claimEnd + withdrawalWindow) - claimEnd) / withdrawalWindow;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L118

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

 82:             IBridgedERC20(migratingAddress).mint(_account, _amount);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L82

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

 180:             delete bridgedToCanonical[_btokenNew];

 189:         canonicalToBridged[_ctoken.chainId][_ctoken.addr] = _btokenNew;

 359:             ctoken_ = bridgedToCanonical[_token];

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L180

```solidity
File: packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

 49:         usdc.burn(_amount);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L49

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

 237:             && block.timestamp <= instances[id].validSince + INSTANCE_EXPIRY;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L237


## [GAS-11] Use calldata instead of memory for function arguments that do not get mutated
Mark data types as `calldata` instead of `memory` where possible. This makes it so that the data is not automatically loaded into memory. If the data passed into the function does not need to be changed (like updating values in an array), it can be passed in as `calldata`. The one exception to this is if the argument must later be passed into another function that takes an argument that specifies `memory` storage.

**Total Instances:** 35
**Gas per instance:** 300
**Total Gas saved:** 10500

```solidity
File: packages/protocol/contracts/L1/gov/TaikoGovernor.sol

 /// @audit  _targets, _values, _calldatas, _description
 48:     function propose(
            address[] memory _targets,
            uint256[] memory _values,
            bytes[] memory _calldatas,
            string memory _description
        )
            public
            override(IGovernorUpgradeable, GovernorUpgradeable, GovernorCompatibilityBravoUpgradeable)
            returns (uint256)
        {

 /// @audit  _targets, _values, _signatures, _calldatas, _description
 69:     function propose(
            address[] memory _targets,
            uint256[] memory _values,
            string[] memory _signatures,
            bytes[] memory _calldatas,
            string memory _description
        )
            public
            virtual
            override(GovernorCompatibilityBravoUpgradeable)
            returns (uint256)
        {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L48

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

 /// @audit  _blk, _meta, _data
 62:     function onBlockProposed(
            TaikoData.Block memory _blk,
            TaikoData.BlockMetadata memory _meta,
            bytes memory _data
        )
            external
            payable
            nonReentrant
            onlyFromNamed("taiko")
        {

 /// @audit  _assignment
 137:     function hashAssignment(
             ProverAssignment memory _assignment,
             address _taikoL1Address,
             bytes32 _blobHash
         )
             public
             view
             returns (bytes32)
         {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L62

```solidity
File: packages/protocol/contracts/L1/hooks/IHook.sol

 /// @audit  _blk, _meta, _data
 13:     function onBlockProposed(

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/IHook.sol#L13

```solidity
File: packages/protocol/contracts/L1/libs/LibUtils.sol

 /// @audit  _config
 23:     function getTransition(
            TaikoData.State storage _state,
            TaikoData.Config memory _config,
            uint64 _blockId,
            bytes32 _parentHash
        )
            external
            view
            returns (TaikoData.TransitionState storage)
        {

 /// @audit  _config
 52:     function getBlock(
            TaikoData.State storage _state,
            TaikoData.Config memory _config,
            uint64 _blockId
        )
            external
            view
            returns (TaikoData.Block storage blk_, uint64 slot_)
        {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibUtils.sol#L23

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

 /// @audit  _config
 47:     function init(
            TaikoData.State storage _state,
            TaikoData.Config memory _config,
            bytes32 _genesisBlockHash
        )
            external
        {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L47

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

 /// @audit  _newGuardians
 53:     function setGuardians(
            address[] memory _newGuardians,
            uint8 _minGuardians
        )
            external
            onlyOwner
            nonReentrant
        {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L53

```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

 /// @audit  _newConfig
 25:     function setConfigAndExcess(
            Config memory _newConfig,
            uint64 _newGasExcess
        )
            external
            virtual
            onlyOwner
        {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L25

```solidity
File: packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol

 /// @audit  tbs, signature, publicKey
 38:     function verifyAttStmtSignature(

 /// @audit  tbs, signature, publicKey
 48:     function verifyCertificateSignature(

 /// @audit  tbs, signature, publicKey
 58:     function verifyRS256Signature(

 /// @audit  tbs, signature, publicKey
 67:     function verifyRS1Signature(

 /// @audit  tbs, signature, publicKey
 76:     function verifyES256Signature(

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L38

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

 /// @audit  pemChain
 40:     function splitCertificateChain(
            bytes memory pemChain,
            uint256 size
        )
            external
            pure
            returns (bool success, bytes[] memory certs)
        {

 /// @audit  der
 74:     function decodeCert(
            bytes memory der,
            bool isPckCert
        )
            external
            pure
            returns (bool success, ECSha256Certificate memory cert)
        {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L40

```solidity
File: packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol

 /// @audit  pemChain
 36:     function splitCertificateChain(

 /// @audit  der
 44:     function decodeCert(

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L36

```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

 /// @audit  tbs, signature, publicKey
 24:     function verifyAttStmtSignature(
            bytes memory tbs,
            bytes memory signature,
            PublicKey memory publicKey,
            Algorithm alg
        )
            public
            view
            returns (bool)
        {

 /// @audit  tbs, signature, publicKey
 54:     function verifyCertificateSignature(
            bytes memory tbs,
            bytes memory signature,
            PublicKey memory publicKey,
            CertSigAlgorithm alg
        )
            public
            view
            returns (bool)
        {

 /// @audit  tbs, signature, publicKey
 79:     function verifyRS256Signature(
            bytes memory tbs,
            bytes memory signature,
            bytes memory publicKey
        )
            public
            view
            returns (bool sigValid)
        {

 /// @audit  tbs, signature, publicKey
 96:     function verifyRS1Signature(
            bytes memory tbs,
            bytes memory signature,
            bytes memory publicKey
        )
            public
            view
            returns (bool sigValid)
        {

 /// @audit  tbs, signature, publicKey
 113:     function verifyES256Signature(
             bytes memory tbs,
             bytes memory signature,
             bytes memory publicKey
         )
             public
             view
             returns (bool sigValid)
         {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L24

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 /// @audit  _message
 449:     function hashMessage(Message memory _message) public pure returns (bytes32) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L449

```solidity
File: packages/protocol/contracts/bridge/IBridge.sol

 /// @audit  _message
 155:     function hashMessage(Message memory _message) external pure returns (bytes32);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/IBridge.sol#L155

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

 /// @audit  _grant
 135:     function grant(address _recipient, Grant memory _grant) external onlyOwner {

 /// @audit  _sig
 168:     function withdraw(address _to, bytes memory _sig) external {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L135

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

 /// @audit  _symbol, _name
 38:     function init(
            address _owner,
            address _addressManager,
            address _srcToken,
            uint256 _srcChainId,
            string memory _symbol,
            string memory _name
        )
            external
            initializer
        {

 /// @audit  _tokenIds, _amounts
 83:     function mintBatch(
            address _to,
            uint256[] memory _tokenIds,
            uint256[] memory _amounts
        )
            public
            nonReentrant
            whenNotPaused
            onlyFromNamed("erc1155_vault")
        {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L38

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

 /// @audit  _symbol, _name
 52:     function init(
            address _owner,
            address _addressManager,
            address _srcToken,
            uint256 _srcChainId,
            uint8 _decimals,
            string memory _symbol,
            string memory _name
        )
            external
            initializer
        {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L52

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

 /// @audit  _symbol, _name
 31:     function init(
            address _owner,
            address _addressManager,
            address _srcToken,
            uint256 _srcChainId,
            string memory _symbol,
            string memory _name
        )
            external
            initializer
        {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L31

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

 /// @audit  _op
 39:     function sendToken(BridgeTransferOp memory _op)
            external
            payable
            nonReentrant
            whenNotPaused
            withValidOperation(_op)
            returns (IBridge.Message memory message_)
        {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L39

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

 /// @audit  _op
 26:     function sendToken(BridgeTransferOp memory _op)
            external
            payable
            nonReentrant
            whenNotPaused
            withValidOperation(_op)
            returns (IBridge.Message memory message_)
        {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L26

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

 /// @audit  _tran
 171:     function getSignedHash(
             TaikoData.Transition memory _tran,
             address _newInstance,
             address _prover,
             bytes32 _metaHash
         )
             public
             view
             returns (bytes32)
         {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L171


## [GAS-12] Gas savings can be achieved by changing the model for assigning value to the structure
By changing the pattern of assigning value to the structure, gas savings of ~130 per instance are achieved. In addition, this use will provide significant savings in distribution costs. 
 `structure = Structure({parameter1: value1})` 
 can be changed to 
 `structure.parameter1 = value1`

**Total Instances:** 30
**Gas per instance:** 260
**Total Gas saved:** 7800

```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

 191:         return TaikoData.Config({
                 chainId: 167_008,
                 // Assume the block time is 3s, the protocol will allow ~1 month of
                 // new blocks without any verification.
                 blockMaxProposals: 864_000,
                 blockRingBufferSize: 864_100,
                 // Can be overridden by the tier config.
                 maxBlocksToVerifyPerProposal: 10,
                 blockMaxGasLimit: 15_000_000,
                 // Each go-ethereum transaction has a size limit of 128KB,
                 // and right now txList is still saved in calldata, so we set it
                 // to 120KB.
                 blockMaxTxListBytes: 120_000,
                 blobExpiry: 24 hours,
                 blobAllowedForDA: false,
                 blobReuseEnabled: false,
                 livenessBond: 250e18, // 250 Taiko token
                 // ETH deposit related.
                 ethDepositRingBufferSize: 1024,
                 ethDepositMinCountPerBlock: 8,
                 ethDepositMaxCountPerBlock: 32,
                 ethDepositMinAmount: 1 ether,
                 ethDepositMaxAmount: 10_000 ether,
                 ethDepositGas: 21_000,
                 ethDepositMaxFee: 1 ether / 10,
                 blockSyncThreshold: 16

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L191

```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

 88:                 deposits_[i] = TaikoData.EthDeposit({
                        recipient: address(uint160(data >> 96)),
                        amount: uint96(data),
                        id: j

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L88

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

 121:             meta_ = TaikoData.BlockMetadata({
                     l1Hash: blockhash(block.number - 1),
                     difficulty: 0, // to be initialized below
                     blobHash: 0, // to be initialized below
                     extraData: params.extraData,
                     depositsHash: keccak256(abi.encode(deposits_)),
                     coinbase: params.coinbase,
                     id: b.numBlocks,
                     gasLimit: _config.blockMaxGasLimit,
                     timestamp: uint64(block.timestamp),
                     l1Height: uint64(block.number - 1),
                     txListByteOffset: 0, // to be initialized below
                     txListByteSize: 0, // to be initialized below
                     minTier: 0, // to be initialized below
                     blobUsed: _txList.length == 0,
                     parentMetaHash: parentMetaHash

 212:         TaikoData.Block memory blk = TaikoData.Block({
                 metaHash: keccak256(abi.encode(meta_)),
                 // Safeguard the liveness bond to ensure its preservation,
                 // particularly in scenarios where it might be altered after the
                 // block's proposal but before it has been proven or verified.
                 livenessBond: _config.livenessBond,
                 blockId: b.numBlocks,
                 proposedAt: meta_.timestamp,
                 proposedIn: uint64(block.number),
                 // For a new block, the next transition ID is always 1, not 0.
                 nextTransitionId: 1,
                 // For unverified block, its verifiedTransitionId is always 0.
                 verifiedTransitionId: 0,
                 assignedProver: params.assignedProver

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L121

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

 166:                 IVerifier.Context memory ctx = IVerifier.Context({
                         metaHash: blk.metaHash,
                         blobHash: _meta.blobHash,
                         // Separate msgSender to allow the prover to be any address in the future.
                         prover: msg.sender,
                         msgSender: msg.sender,
                         blockId: blk.blockId,
                         isContesting: isContesting,
                         blobUsed: _meta.blobUsed

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L166

```solidity
File: packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol

 22:             return ITierProvider.Tier({
                    verifierName: "tier_optimistic",
                    validityBond: 250 ether, // TKO
                    contestBond: 500 ether, // TKO
                    cooldownWindow: 1440, //24 hours
                    provingWindow: 120, // 2 hours
                    maxBlocksToVerifyPerProof: 16

 33:             return ITierProvider.Tier({
                    verifierName: "tier_guardian",
                    validityBond: 0, // must be 0 for top tier
                    contestBond: 0, // must be 0 for top tier
                    cooldownWindow: 60, //1 hours
                    provingWindow: 2880, // 48 hours
                    maxBlocksToVerifyPerProof: 16

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L22

```solidity
File: packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol

 22:             return ITierProvider.Tier({
                    verifierName: "tier_sgx",
                    validityBond: 250 ether, // TKO
                    contestBond: 500 ether, // TKO
                    cooldownWindow: 1440, //24 hours
                    provingWindow: 60, // 1 hours
                    maxBlocksToVerifyPerProof: 8

 33:             return ITierProvider.Tier({
                    verifierName: "tier_sgx_zkvm",
                    validityBond: 500 ether, // TKO
                    contestBond: 1000 ether, // TKO
                    cooldownWindow: 1440, //24 hours
                    provingWindow: 240, // 4 hours
                    maxBlocksToVerifyPerProof: 4

 44:             return ITierProvider.Tier({
                    verifierName: "tier_guardian",
                    validityBond: 0, // must be 0 for top tier
                    contestBond: 0, // must be 0 for top tier
                    cooldownWindow: 60, //1 hours
                    provingWindow: 2880, // 48 hours
                    maxBlocksToVerifyPerProof: 16

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L22

```solidity
File: packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol

 22:             return ITierProvider.Tier({
                    verifierName: "tier_optimistic",
                    validityBond: 250 ether, // TKO
                    contestBond: 500 ether, // TKO
                    cooldownWindow: 1440, //24 hours
                    provingWindow: 30, // 0.5 hours
                    maxBlocksToVerifyPerProof: 12

 33:             return ITierProvider.Tier({
                    verifierName: "tier_sgx",
                    validityBond: 500 ether, // TKO
                    contestBond: 1000 ether, // TKO
                    cooldownWindow: 1440, //24 hours
                    provingWindow: 60, // 1 hours
                    maxBlocksToVerifyPerProof: 8

 44:             return ITierProvider.Tier({
                    verifierName: "tier_guardian",
                    validityBond: 0, // must be 0 for top tier
                    contestBond: 0, // must be 0 for top tier
                    cooldownWindow: 60, //1 hours
                    provingWindow: 2880, // 48 hours
                    maxBlocksToVerifyPerProof: 16

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L22

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

 54:         v3ParsedQuote = V3Struct.ParsedV3QuoteStruct({
                header: header,
                localEnclaveReport: localEnclaveReport,
                v3AuthData: authDataV3

 190:         header = V3Struct.Header({
                 version: version,
                 attestationKeyType: attestationKeyType,
                 teeType: teeType,
                 qeSvn: bytes2(rawHeader.substring(8, 2)),
                 pceSvn: bytes2(rawHeader.substring(10, 2)),
                 qeVendorId: qeVendorId,
                 userData: bytes20(rawHeader.substring(28, 20))

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L54

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 243:                 proofReceipt[msgHash] = ProofReceipt({
                         receivedAt: receivedAt,
                         preferredExecutor: _message.gasLimit == 0 ? _message.destOwner : msg.sender

 549:             __ctx = Context(_msgHash, _from, _srcChainId);

 565:             return Context(msgHash, from, srcChainId);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L243

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

 47:         out_ = RLPItem({ length: _in.length, ptr: ptr });

 76:                 RLPItem({
                        length: _in.length - offset,
                        ptr: MemoryPointer.wrap(MemoryPointer.unwrap(_in.ptr) + offset)

 84:             out_[itemCount] = RLPItem({
                    length: itemLength + itemOffset,
                    ptr: MemoryPointer.wrap(MemoryPointer.unwrap(_in.ptr) + offset)

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L47

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

 209:             proof_[i] = TrieNode({ encoded: _proof[i], decoded: RLPReader.readList(_proof[i]) });

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L209

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

 58:         IBridge.Message memory message = IBridge.Message({
                id: 0, // will receive a new value
                from: address(0), // will receive a new value
                srcChainId: 0, // will receive a new value
                destChainId: _op.destChainId,
                srcOwner: msg.sender,
                destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,
                to: resolve(_op.destChainId, name(), false),
                refundTo: _op.refundTo,
                value: msg.value - _op.fee,
                fee: _op.fee,
                gasLimit: _op.gasLimit,
                data: data,
                memo: _op.memo

 256:                 ctoken_ = CanonicalNFT({
                         chainId: uint64(block.chainid),
                         addr: _op.token,
                         symbol: "",
                         name: ""

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L58

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

 221:         IBridge.Message memory message = IBridge.Message({
                 id: 0, // will receive a new value
                 from: address(0), // will receive a new value
                 srcChainId: 0, // will receive a new value
                 destChainId: _op.destChainId,
                 srcOwner: msg.sender,
                 destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,
                 to: resolve(_op.destChainId, name(), false),
                 refundTo: _op.refundTo,
                 value: msg.value - _op.fee,
                 fee: _op.fee,
                 gasLimit: _op.gasLimit,
                 data: data,
                 memo: _op.memo

 365:             ctoken_ = CanonicalERC20({
                     chainId: uint64(block.chainid),
                     addr: _token,
                     decimals: meta.decimals(),
                     symbol: meta.symbol(),
                     name: meta.name()

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L221

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

 44:         IBridge.Message memory message = IBridge.Message({
                id: 0, // will receive a new value
                from: address(0), // will receive a new value
                srcChainId: 0, // will receive a new value
                destChainId: _op.destChainId,
                srcOwner: msg.sender,
                destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,
                to: resolve(_op.destChainId, name(), false),
                refundTo: _op.refundTo,
                value: msg.value - _op.fee,
                fee: _op.fee,
                gasLimit: _op.gasLimit,
                data: data,
                memo: _op.memo

 203:                 ctoken_ = CanonicalNFT({
                         chainId: uint64(block.chainid),
                         addr: _op.token,
                         symbol: t.symbol(),
                         name: t.name()

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L44

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

 217:             instances[nextInstanceId] = Instance(_instances[i], validSince);

 229:         instances[id] = Instance(newInstance, uint64(block.timestamp));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L229


## [GAS-13] Multiple address/ID mappings can be combined into a single mapping of an address/ID to a struct, where appropriate
Saves a storage slot for the mapping. Depending on the circumstances and sizes of types, can avoid a Gsset (20000 gas) per mapping combined. Reads and subsequent writes can also be cheaper when a function requires both values and they both fit in the same storage slot. Finally, if both fields are accessed in the same function, can save ~42 gas per access due to not having to recalculate the key keccak256 hash (Gkeccak256 - 30 gas) and that calculations associated stack operations.

**Total Instances:** 4

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

 22:     mapping(address addr => uint256 amountClaimed) public claimedAmount;

 25:     mapping(address addr => uint256 amountWithdrawn) public withdrawnAmount;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L22

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

 45:     mapping(address btoken => CanonicalERC20 canonical) public bridgedToCanonical;

 52:     mapping(address btoken => bool blacklisted) public btokenBlacklist;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L52


## [GAS-14] Consider activating via-ir for deploying
By using --via-ir or {"viaIR": true}, the compiler is able to use more advanced multi-function optimizations, for extra gas savings.

**Total Instances:** 85

```solidity
File: packages/protocol/contracts/L1/ITaikoL1.sol

 8: interface ITaikoL1 {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/ITaikoL1.sol#L8

```solidity
File: packages/protocol/contracts/L1/TaikoData.sol

 8: library TaikoData {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L8

```solidity
File: packages/protocol/contracts/L1/TaikoErrors.sol

 11: abstract contract TaikoErrors {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoErrors.sol#L11

```solidity
File: packages/protocol/contracts/L1/TaikoEvents.sol

 13: abstract contract TaikoEvents {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoEvents.sol#L13

```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

 22: contract TaikoL1 is EssentialContract, ITaikoL1, TaikoEvents, TaikoErrors {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L22

```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

 15: contract TaikoToken is EssentialContract, ERC20SnapshotUpgradeable, ERC20VotesUpgradeable {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoToken.sol#L15

```solidity
File: packages/protocol/contracts/L1/gov/TaikoGovernor.sol

 16: contract TaikoGovernor is

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L16

```solidity
File: packages/protocol/contracts/L1/gov/TaikoTimelockController.sol

 9: contract TaikoTimelockController is EssentialContract, TimelockControllerUpgradeable {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L9

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

 14: contract AssignmentHook is EssentialContract, IHook {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L14

```solidity
File: packages/protocol/contracts/L1/hooks/IHook.sol

 8: interface IHook {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/IHook.sol#L8

```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

 12: library LibDepositing {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L12

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

 15: library LibProposing {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L15

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

 16: library LibProving {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L16

```solidity
File: packages/protocol/contracts/L1/libs/LibUtils.sol

 9: library LibUtils {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibUtils.sol#L9

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

 16: library LibVerifying {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L16

```solidity
File: packages/protocol/contracts/L1/provers/GuardianProver.sol

 10: contract GuardianProver is Guardians {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/GuardianProver.sol#L10

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

 9: abstract contract Guardians is EssentialContract {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L9

```solidity
File: packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol

 10: contract DevnetTierProvider is EssentialContract, ITierProvider {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L10

```solidity
File: packages/protocol/contracts/L1/tiers/ITierProvider.sol

 7: interface ITierProvider {

 37: library LibTiers {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L7

```solidity
File: packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol

 10: contract MainnetTierProvider is EssentialContract, ITierProvider {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L10

```solidity
File: packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol

 10: contract TestnetTierProvider is EssentialContract, ITierProvider {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L10

```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

 14: abstract contract CrossChainOwned is EssentialContract, IMessageInvocable {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L14

```solidity
File: packages/protocol/contracts/L2/Lib1559Math.sol

 10: library Lib1559Math {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/Lib1559Math.sol#L10

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

 21: contract TaikoL2 is CrossChainOwned {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L21

```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

 9: contract TaikoL2EIP1559Configurable is TaikoL2 {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L9

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

 22: contract AutomataDcapV3Attestation is IAttestation {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L22

```solidity
File: packages/protocol/contracts/automata-attestation/interfaces/IAttestation.sol

 8: interface IAttestation {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/interfaces/IAttestation.sol#L8

```solidity
File: packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol

 6: interface ISigVerifyLib {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L6

```solidity
File: packages/protocol/contracts/automata-attestation/lib/EnclaveIdStruct.sol

 6: library EnclaveIdStruct {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/EnclaveIdStruct.sol#L6

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

 12: contract PEMCertChainLib is IPEMCertChainLib {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L12

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

 11: library V3Parser {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L11

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol

 6: library V3Struct {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L6

```solidity
File: packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol

 6: library TCBInfoStruct {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol#L6

```solidity
File: packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol

 6: interface IPEMCertChainLib {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L6

```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

 12: library NodePtr {

 38: library Asn1Decode {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L12

```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

 8: library BytesUtils {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L8

```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

 34: library RsaVerify {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L34

```solidity
File: packages/protocol/contracts/automata-attestation/utils/SHA1.sol

 10: library SHA1 {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SHA1.sol#L10

```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

 15: contract SigVerifyLib is ISigVerifyLib {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L15

```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

 7: library X509DateUtils {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L7

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 16: contract Bridge is EssentialContract, IBridge {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L16

```solidity
File: packages/protocol/contracts/bridge/IBridge.sol

 8: interface IBridge {

 160: interface IRecallableSender {

 174: interface IMessageInvocable {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/IBridge.sol#L8

```solidity
File: packages/protocol/contracts/common/AddressManager.sol

 10: contract AddressManager is EssentialContract, IAddressManager {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressManager.sol#L10

```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

 10: abstract contract EssentialContract is UUPSUpgradeable, Ownable2StepUpgradeable, AddressResolver {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L10

```solidity
File: packages/protocol/contracts/common/IAddressManager.sol

 7: interface IAddressManager {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/IAddressManager.sol#L7

```solidity
File: packages/protocol/contracts/libs/Lib4844.sol

 8: library Lib4844 {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/Lib4844.sol#L8

```solidity
File: packages/protocol/contracts/libs/LibAddress.sol

 13: library LibAddress {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibAddress.sol#L13

```solidity
File: packages/protocol/contracts/libs/LibMath.sol

 7: library LibMath {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibMath.sol#L7

```solidity
File: packages/protocol/contracts/libs/LibTrieProof.sol

 15: library LibTrieProof {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibTrieProof.sol#L15

```solidity
File: packages/protocol/contracts/signal/ISignalService.sol

 12: interface ISignalService {

 12: interface ISignalService {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/ISignalService.sol#L12

```solidity
File: packages/protocol/contracts/signal/LibSignals.sol

 6: library LibSignals {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/LibSignals.sol#L6

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

 14: contract SignalService is EssentialContract, ISignalService {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L14

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

 25: contract TimelockTokenPool is EssentialContract {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L25

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

 11: contract ERC20Airdrop is MerkleClaimable {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L11

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

 12: contract ERC20Airdrop2 is MerkleClaimable {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L12

```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

 9: contract ERC721Airdrop is MerkleClaimable {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L9

```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

 10: abstract contract MerkleClaimable is EssentialContract {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L10

```solidity
File: packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol

 5: library ExcessivelySafeCall {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L5

```solidity
File: packages/protocol/contracts/thirdparty/optimism/Bytes.sol

 6: library Bytes {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L6

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

 9: library RLPReader {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L9

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

 9: library RLPWriter {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L9

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

 11: library MerkleTrie {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L11

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol

 9: library SecureMerkleTrie {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L9

```solidity
File: packages/protocol/contracts/tokenvault/BaseNFTVault.sol

 9: abstract contract BaseNFTVault is BaseVault {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L9

```solidity
File: packages/protocol/contracts/tokenvault/BaseVault.sol

 12: abstract contract BaseVault is

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseVault.sol#L12

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

 14: contract BridgedERC1155 is EssentialContract, IERC1155MetadataURIUpgradeable, ERC1155Upgradeable {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L14

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

 15: contract BridgedERC20 is

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L15

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

 9: abstract contract BridgedERC20Base is EssentialContract, IBridgedERC20 {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L9

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

 12: contract BridgedERC721 is EssentialContract, ERC721Upgradeable {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L12

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

 16: interface IERC1155NameAndSymbol {

 29: contract ERC1155Vault is BaseNFTVault, ERC1155ReceiverUpgradeable {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L16

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

 18: contract ERC20Vault is BaseVault {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L18

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

 16: contract ERC721Vault is BaseNFTVault, IERC721Receiver {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L16

```solidity
File: packages/protocol/contracts/tokenvault/IBridgedERC20.sol

 10: interface IBridgedERC20 {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/IBridgedERC20.sol#L10

```solidity
File: packages/protocol/contracts/tokenvault/LibBridgedToken.sol

 8: library LibBridgedToken {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L8

```solidity
File: packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

 8: interface IUSDC {

 28: contract USDCAdapter is BridgedERC20Base {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L8

```solidity
File: packages/protocol/contracts/verifiers/GuardianVerifier.sol

 10: contract GuardianVerifier is EssentialContract, IVerifier {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L10

```solidity
File: packages/protocol/contracts/verifiers/IVerifier.sol

 9: interface IVerifier {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/IVerifier.sol#L9

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

 19: contract SgxVerifier is EssentialContract, IVerifier {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L19


## [GAS-15] Consider pre-calculating the address of `address(this)` to save gas
'Use `foundry's` [script.sol](https://book.getfoundry.sh/reference/forge-std/compute-create-address) or `solady's` [LibRlp.sol](https://github.com/Vectorized/solady/blob/main/src/utils/LibRLP.sol) to save the value in a constant, which will avoid having to spend gas to push the value on the stack every time it's used.'

**Total Instances:** 38

```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

 61:         if (_to == address(this)) revert TKO_INVALID_ADDR();

 79:         if (_to == address(this)) revert TKO_INVALID_ADDR();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoToken.sol#L61

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

 125:         if (address(this).balance > 0) {

 126:             taikoL1Address.sendEther(address(this).balance);

 151:                 address(this),

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L125

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

 238:             uint256 tkoBalance = tko.balanceOf(address(this));

 253:                 IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }(

 260:             if (address(this).balance != 0) {

 261:                 msg.sender.sendEther(address(this).balance);

 268:             if (tko.balanceOf(address(this)) != tkoBalance + _config.livenessBond) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L238

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

 242:                 tko.transferFrom(msg.sender, address(this), tier.contestBond);

 384:                 _tko.transferFrom(msg.sender, address(this), _tier.validityBond - reward);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L242

```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

 50:         (bool success,) = address(this).call(txdata);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L50

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

 174:             _to.sendEther(address(this).balance);

 176:             IERC20(_token).safeTransfer(_to, IERC20(_token).balanceOf(address(this)));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L174

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 196:                 _storeContext(msgHash, address(this), _message.srcChainId);

 343:             _app: address(this),

 486:         assert(_message.from != address(this));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L196

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

 112:                 signalService = address(this);

 131:         if (value == 0 || value != _loadSignalValue(address(this), signal)) {

 149:         return _loadSignalValue(address(this), signal) == _chainData;

 171:             chainData_ = _loadSignalValue(address(this), signal);

 245:         _sendSignal(address(this), signal_, _chainData);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L112

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

 137:         if (_to == address(this)) revert BTOKEN_CANNOT_RECEIVE();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L137

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

 147:         if (_to == address(this)) revert BTOKEN_CANNOT_RECEIVE();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L147

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

 125:         if (_to == address(this)) revert BTOKEN_CANNOT_RECEIVE();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L125

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

 108:         if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

 226:             IERC1155(token).safeBatchTransferFrom(address(this), to, tokenIds, amounts, "");

 272:                         to: address(this),

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L108

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

 267:         if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

 378:             uint256 _balance = t.balanceOf(address(this));

 379:             t.safeTransferFrom({ from: msg.sender, to: address(this), value: _amount });

 380:             balanceChange_ = t.balanceOf(address(this)) - _balance;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L267

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

 91:         if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

 171:                 IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);

 211:                     t.safeTransferFrom(_user, address(this), _op.tokenIds[i]);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L91

```solidity
File: packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

 48:         usdc.transferFrom(_from, address(this), _amount);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L48

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

 186:                 address(this),

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L186


## [GAS-16] 'Consider using Solady's `FixedPointMathLib`'
Saves gas, and works to avoid unnecessary [overflows](https://github.com/Vectorized/solady/blob/6cce088e69d6e46671f2f622318102bd5db77a65/src/utils/FixedPointMathLib.sol#L267).

**Total Instances:** 6

```solidity
File: packages/protocol/contracts/L2/Lib1559Math.sol

 28:         return _ethQty(_gasExcess, _adjustmentFactor) / LibFixedPointMath.SCALING_FACTOR

 41:         uint256 input = _gasExcess * LibFixedPointMath.SCALING_FACTOR / _adjustmentFactor;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/Lib1559Math.sol#L28

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

 264:         return _amount * uint64(block.timestamp - _start) / _period;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L264

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

 117:         uint256 timeBasedAllowance = balance

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L117

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

 39:             while (_len / i != 0) {

 47:                 out_[i] = bytes1(uint8((_len / (256 ** (lenLen - i))) % 256));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L47


## [GAS-17] 'Consider using `solady's` token contracts to save gas'
They're written using heavily-optimized assembly, and will your users a lot of gas

**Total Instances:** 5

```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

 /// @audit  ERC20SnapshotUpgradeable, ERC20VotesUpgradeable
 15: contract TaikoToken is EssentialContract, ERC20SnapshotUpgradeable, ERC20VotesUpgradeable {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoToken.sol#L15

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

 /// @audit  ERC1155Upgradeable
 14: contract BridgedERC1155 is EssentialContract, IERC1155MetadataURIUpgradeable, ERC1155Upgradeable {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L14

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

 /// @audit  ERC20SnapshotUpgradeable, ERC20VotesUpgradeable
 15: contract BridgedERC20 is
        BridgedERC20Base,
        IERC20MetadataUpgradeable,
        ERC20SnapshotUpgradeable,
        ERC20VotesUpgradeable

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L15

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

 /// @audit  ERC721Upgradeable
 12: contract BridgedERC721 is EssentialContract, ERC721Upgradeable {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L12

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

 /// @audit  ERC1155ReceiverUpgradeable
 29: contract ERC1155Vault is BaseNFTVault, ERC1155ReceiverUpgradeable {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L29


## [GAS-18] Expressions for constant values such as a call to keccak256(), should use immutable rather than constant
The reason for this is that constant variables are evaluated at runtime and their value is included in the bytecode of the contract. This means that any expensive operations performed as part of the constant expression, such as a call to keccak256(), will be executed every time the contract is deployed, even if the result is always the same. This can result in higher gas costs. In contrast, immutable variables are evaluated at compilation time, and their values are included in the bytecode of the contract as constants. This means that any expensive operations performed as part of the immutable expression are only executed once, when the contract is compiled, and the result is reused every time the contract is deployed. This can result in lower gas costs compared to using constant variables.

**Total Instances:** 8

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

 21:     uint256 public constant MAX_BYTES_PER_BLOB = 4096 * 32;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L21

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

 20:     bytes32 public constant RETURN_LIVENESS_BOND = keccak256("RETURN_LIVENESS_BOND");

 23:     bytes32 public constant TIER_OP = bytes32("tier_optimistic");

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L20

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 27:     uint256 internal constant PLACEHOLDER = type(uint256).max;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L27

```solidity
File: packages/protocol/contracts/libs/Lib4844.sol

 10:     address public constant POINT_EVALUATION_PRECOMPILE_ADDRESS = address(0x0A);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/Lib4844.sol#L10

```solidity
File: packages/protocol/contracts/signal/LibSignals.sol

 8:     bytes32 public constant STATE_ROOT = keccak256("STATE_ROOT");

 11:     bytes32 public constant SIGNAL_ROOT = keccak256("SIGNAL_ROOT");

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/LibSignals.sol#L8

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

 24:     uint256 internal constant BRANCH_NODE_LENGTH = TREE_RADIX + 1;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L24


## [GAS-19] Constructors can be marked as payable to save deployment gas
Payable functions cost less gas to execute, because the compiler does not have to add extra checks to ensure that no payment is provided. A constructor can be safely marked as payable, because only the deployer would be able to pass funds, and the project itself would not pass any funds.

**Total Instances:** 3
**Gas per instance:** 21
**Total Gas saved:** 63

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

 54:     constructor(address sigVerifyLibAddr, address pemCertLibAddr) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L54

```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

 20:     constructor(address es256Verifier) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L20

```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

 64:     constructor() {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L64


## [GAS-20] Counting down when iterating, saves gas
Counting down saves 6 gas per loop, since checks for zero are more efficient than checks against any other value

**Total Instances:** 4
**Gas per instance:** 12
**Total Gas saved:** 48

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

 46:             for (i = 1; i <= lenLen; i++) {

 59:         for (; i < 32; i++) {

 66:         for (uint256 j = 0; j < out_.length; j++) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L46

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

 85:         for (uint256 i = 0; i < proof.length; i++) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85


## [GAS-23] Division by powers of two should use bit shifting
<x> / 2 is the same as <x> >> 1. While the compiler uses the SHR opcode to accomplish both, the version that uses division incurs an overhead of 20 gas due to JUMPs to and from a compiler utility function that introduces checks which can be avoided by using unchecked {} around the division by two.

**Total Instances:** 2
**Gas per instance:** 20
**Total Gas saved:** 40

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

 359:                 ? uint16(bytes2(svnValueBytes)) / 256

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L359

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

 155:             uint256 upperDigit = digits / 16;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L155


## [GAS-24] Emitting constants wastes gas
'Every event parameter costs `Glogdata` (8 gas) per byte. You can avoid this extra cost, in cases where you're emitting a constant, by creating a second version of the event, which doesn't have the parameter (and have users look to the contract's variables for its value instead), and using the new event in the cases shown below.'

**Total Instances:** 4
**Gas per instance:** 8
**Total Gas saved:** 32

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

 /// @audit  0
 230:                 emit TransitionProved({

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L230

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

 /// @audit  0, 0, 0, 0
 73:         emit BlockVerified({

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L73

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 /// @audit  true
 210:             emit MessageReceived(msgHash, _message, true);

 /// @audit  false
 303:             emit MessageReceived(msgHash, _message, false);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L303


## [GAS-25] Empty blocks should be removed or emit something
 Removing empty blocks help conserve computational resources on the blockchain network, reducing transaction costs and improving overall efficiency.

**Total Instances:** 1

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 70:     receive() external payable { }

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L70


## [GAS-26] Events should be emitted outside of loops
Emitting an event has an overhead of 375 gas, which will be incurred on every iteration of the loop. It is cheaper to emit only once after the loop has finished.

**Total Instances:** 4
**Gas per instance:** 375
**Total Gas saved:** 1500

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

 198:                 emit BlockVerified({

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L198

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 93:             emit MessageSuspended(msgHash, _suspend);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L93

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

 109:             emit InstanceDeleted(idx, instances[idx].addr);

 220:             emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220


## [GAS-27] >= costs less gas than >
The compiler uses opcodes GT and ISZERO for solidity code that uses `>`, but only requires LT for `>=`, which saves 3 gas. If `<` is being used, the condition can be inverted. In cases where a for-loop is being used, one can count down rather than up, in order to use the optimal operator

**Total Instances:** 123
**Gas per instance:** 3
**Total Gas saved:** 369

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

 82:             block.timestamp > assignment.expiry

 85:                 || assignment.maxBlockId != 0 && _meta.id > assignment.maxBlockId

 86:                 || assignment.maxProposedIn != 0 && block.number > assignment.maxProposedIn

 125:         if (address(this).balance > 0) {

 172:         for (uint256 i; i < _tierFees.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L82

```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

 78:         if (numPending < _config.ethDepositMinCountPerBlock) {

 86:             for (uint256 i; i < deposits_.length;) {

 93:                 uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount;

 140:                 && _state.slotA.numEthDeposits - _state.slotA.nextEthDepositToProcess

 150:         if (_amount > type(uint96).max) revert L1_INVALID_ETH_DEPOSIT();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L78

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

 171:             if (uint256(params.txListByteOffset) + params.txListByteSize > MAX_BYTES_PER_BLOB) {

 195:         if (meta_.txListByteSize == 0 || meta_.txListByteSize > _config.blockMaxTxListBytes) {

 244:             for (uint256 i; i < params.hookCalls.length; ++i) {

 296:         return _state.reusableBlobs[_blobHash] + _config.blobExpiry > block.timestamp;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L171

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

 134:         if (_proof.tier == 0 || _proof.tier < _meta.minTier || _proof.tier < ts.tier) {

 134:         if (_proof.tier == 0 || _proof.tier < _meta.minTier || _proof.tier < ts.tier) {

 192:             bool returnLivenessBond = blk.livenessBond > 0 && _proof.data.length == 32

 203:         if (_proof.tier > ts.tier) {

 381:             if (reward > _tier.validityBond) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L134

```solidity
File: packages/protocol/contracts/L1/libs/LibUtils.sol

 34:         if (_blockId < b.lastVerifiedBlockId || _blockId >= b.numBlocks) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibUtils.sol#L34

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

 127:             while (blockId < b.numBlocks && numBlocksVerified < _maxBlocksToVerify) {

 127:             while (blockId < b.numBlocks && numBlocksVerified < _maxBlocksToVerify) {

 152:                         uint256(ITierProvider(tierProvider).getTier(ts.tier).cooldownWindow) * 60

 212:             if (numBlocksVerified > 0) {

 238:         if (_lastVerifiedBlockId > lastSyncedBlock + _config.blockSyncThreshold) {

 251:                 || _config.blockMaxTxListBytes > 128 * 1024 // calldata up to 128K

 256:             || _config.ethDepositMaxCountPerBlock > 32

 257:                 || _config.ethDepositMaxCountPerBlock < _config.ethDepositMinCountPerBlock

 260:                 || _config.ethDepositMaxAmount > type(uint96).max || _config.ethDepositGas == 0

 262:                 || _config.ethDepositMaxFee > type(uint96).max / _config.ethDepositMaxCountPerBlock

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L127

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

 74:         for (uint256 i; i < guardians.length; ++i) {

 80:         for (uint256 i = 0; i < _newGuardians.length; ++i) {

 133:             for (uint256 i; i < guardiansLength; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L74

```solidity
File: packages/protocol/contracts/L2/Lib1559Math.sol

 42:         if (input > LibFixedPointMath.MAX_EXP_INPUT) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/Lib1559Math.sol#L42

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

 234:             for (uint256 i; i < 255 && _blockId >= i + 1; ++i) {

 262:         if (gasExcess > 0) {

 275:             if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {

 275:             if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {

 279:             if (numL1Blocks > 0) {

 281:                 excess = excess > issuance ? excess - issuance : 1;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L234

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

 80:         for (uint256 i; i < serialNumBatch.length; ++i) {

 95:         for (uint256 i; i < serialNumBatch.length; ++i) {

 191:         for (uint256 i; i < enclaveId.tcbLevels.length; ++i) {

 214:         for (uint256 i; i < tcb.tcbLevels.length; ++i) {

 240:         for (uint256 i; i < CPUSVN_LENGTH; ++i) {

 241:             if (pckCpuSvns[i] < tcbCpuSvns[i]) {

 259:         for (uint256 i; i < n; ++i) {

 280:                 block.timestamp > certs[i].notBefore && block.timestamp < certs[i].notAfter;

 280:                 block.timestamp > certs[i].notBefore && block.timestamp < certs[i].notAfter;

 420:             for (uint256 i; i < 3; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L80

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

 54:         for (uint256 i; i < size; ++i) {

 56:             if (i > 0) {

 244:         for (uint256 i; i < split.length; ++i) {

 323:                     if (extnValuePtr.ixl() < extnValueParentPtr.ixl()) {

 333:             if (tbsPtr.ixl() < tbsParentPtr.ixl()) {

 354:         for (uint256 i; i < SGX_TCB_CPUSVN_SIZE + 1; ++i) {

 358:             uint16 svnValue = svnValueBytes.length < 2

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L54

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

 153:         for (uint256 i; i < encoded.length; ++i) {

 218:         if (cert.certType < 1 || cert.certType > 5) {

 218:         if (cert.certType < 1 || cert.certType > 5) {

 281:         for (uint256 i; i < 3; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L153

```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

 69:         if (otherlen < len) {

 80:         for (uint256 idx = 0; idx < shortest; idx += 32) {

 90:                 if (shortest > 32) {

 333:         for (uint256 i; i < len; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L69

```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

 140:         for (uint256 i = 2; i < 2 + paddingLen; ++i) {

 152:             for (uint256 i; i < digestAlgoWithParamLen; ++i) {

 158:             for (uint256 i; i < digestAlgoWithParamLen; ++i) {

 174:         for (uint256 i; i < _sha256.length; ++i) {

 273:         for (uint256 i = 2; i < 2 + paddingLen; ++i) {

 283:         for (uint256 i; i < sha1Prefix.length; ++i) {

 290:         for (uint256 i; i < _sha1.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L140

```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

 18:             if (uint8(x509Time[0]) - 48 < 5) yrs += 2000;

 48:         for (uint16 i = 1970; i < year; ++i) {

 59:         for (uint8 i = 1; i < month; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L18

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 90:         for (uint256 i; i < _msgHashes.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L90

```solidity
File: packages/protocol/contracts/libs/LibMath.sol

 13:         return _a > _b ? _b : _a;

 21:         return _a > _b ? _a : _b;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibMath.sol#L13

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

 104:         for (uint256 i; i < hopProofs.length; ++i) {

 120:             bool isFullProof = hop.accountProof.length > 0;

 247:         if (topBlockId[_chainId][_kind] < _blockId) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L104

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

 275:             if (_cliff > 0) revert INVALID_GRANT();

 277:             if (_cliff > 0 && _cliff <= _start) revert INVALID_GRANT();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L275

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

 40:         if (claimEnd > block.timestamp || claimEnd + withdrawalWindow < block.timestamp) {

 40:         if (claimEnd > block.timestamp || claimEnd + withdrawalWindow < block.timestamp) {

 114:         if (block.timestamp < claimEnd) return (balance, 0);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L40

```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

 59:         for (uint256 i; i < tokenIds.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59

```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

 35:             merkleRoot == 0x0 || claimStart == 0 || claimEnd == 0 || claimStart > block.timestamp

 36:                 || claimEnd < block.timestamp

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L35

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

 38:             _in.length > 0,

 74:         while (offset < _in.length) {

 153:             _in.length > 0,

 173:                 _in.length > strLen,

 193:                 _in.length > lenOfStrLen,

 213:                 strLen > 55,

 218:                 _in.length > lenOfStrLen + strLen,

 229:                 _in.length > listLen,

 239:                 _in.length > lenOfListLen,

 259:                 listLen > 55,

 264:                 _in.length > lenOfListLen + listLen,

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L38

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

 14:         if (_in.length == 1 && uint8(_in[0]) < 128) {

 33:         if (_len < 56) {

 59:         for (; i < 32; i++) {

 66:         for (uint256 j = 0; j < out_.length; j++) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L14

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

 77:         require(_key.length > 0, "MerkleTrie: empty key");

 85:         for (uint256 i = 0; i < proof.length; i++) {

 120:                         value_.length > 0,

 173:                         value_.length > 0,

 208:         for (uint256 i = 0; i < length;) {

 221:         id_ = _node.length < 32 ? RLPReader.readRawBytes(_node) : RLPReader.readBytes(_node);

 243:         uint256 max = (_a.length < _b.length) ? _a.length : _b.length;

 244:         for (; shared_ < max && _a[shared_] == _b[shared_];) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L77

```solidity
File: packages/protocol/contracts/tokenvault/BaseNFTVault.sol

 145:         if (_op.tokenIds.length > MAX_TOKEN_PER_TXN) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L145

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

 47:         for (uint256 i; i < _op.amounts.length; ++i) {

 251:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

 269:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L47

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

 34:         for (uint256 i; i < _op.tokenIds.length; ++i) {

 170:             for (uint256 i; i < _tokenIds.length; ++i) {

 175:             for (uint256 i; i < _tokenIds.length; ++i) {

 197:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

 210:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L34

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

 104:         for (uint256 i; i < _ids.length; ++i) {

 210:         for (uint256 i; i < _instances.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210


## [GAS-28] keccak256() hash of literals should only be computed once
The result of the hash should be stored in an immutable variable, and the variable should be used instead. If the hash is being used as a part of a function selector, the cast to bytes4 should also only be done once. 

**Total Instances:** 3
**Gas per instance:** 42
**Total Gas saved:** 126

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

 20:     bytes32 public constant RETURN_LIVENESS_BOND = keccak256("RETURN_LIVENESS_BOND");

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L20

```solidity
File: packages/protocol/contracts/signal/LibSignals.sol

 8:     bytes32 public constant STATE_ROOT = keccak256("STATE_ROOT");

 11:     bytes32 public constant SIGNAL_ROOT = keccak256("SIGNAL_ROOT");

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/LibSignals.sol#L11


## [GAS-29] Initializers can be marked as payable to save deployment gas
Payable functions cost less gas to execute, because the compiler does not have to add extra checks to ensure that no payment is provided. Initializers can be safely marked as payable, because only the deployer or the factory contract would call the function without carrying any funds.

**Total Instances:** 24
**Gas per instance:** 21
**Total Gas saved:** 504

```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

 42:     function init(
            address _owner,
            address _addressManager,
            bytes32 _genesisBlockHash
        )
            external
            initializer
        {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L42

```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

 25:     function init(
            address _owner,
            string calldata _name,
            string calldata _symbol,
            address _recipient
        )
            public
            initializer
        {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoToken.sol#L25

```solidity
File: packages/protocol/contracts/L1/gov/TaikoGovernor.sol

 31:     function init(
            address _owner,
            IVotesUpgradeable _token,
            TimelockControllerUpgradeable _timelock
        )
            external
            initializer
        {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L31

```solidity
File: packages/protocol/contracts/L1/gov/TaikoTimelockController.sol

 15:     function init(address _owner, uint256 _minDelay) external initializer {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L15

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

 57:     function init(address _owner, address _addressManager) external initializer {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L57

```solidity
File: packages/protocol/contracts/L1/provers/GuardianProver.sol

 25:     function init(address _owner, address _addressManager) external initializer {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/GuardianProver.sol#L25

```solidity
File: packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol

 15:     function init(address _owner) external initializer {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L15

```solidity
File: packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol

 15:     function init(address _owner) external initializer {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L15

```solidity
File: packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol

 15:     function init(address _owner) external initializer {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L15

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

 71:     function init(
            address _owner,
            address _addressManager,
            uint64 _l1ChainId,
            uint64 _gasExcess
        )
            external
            initializer
        {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L71

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 75:     function init(address _owner, address _addressManager) external initializer {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L75

```solidity
File: packages/protocol/contracts/common/AddressManager.sol

 30:     function init(address _owner) external initializer {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressManager.sol#L30

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

 48:     function init(address _owner, address _addressManager) external initializer {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L48

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

 111:     function init(
             address _owner,
             address _taikoToken,
             address _costToken,
             address _sharedVault
         )
             external
             initializer
         {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L111

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

 27:     function init(
            address _owner,
            uint64 _claimStart,
            uint64 _claimEnd,
            bytes32 _merkleRoot,
            address _token,
            address _vault
        )
            external
            initializer
        {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L27

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

 54:     function init(
            address _owner,
            uint64 _claimStart,
            uint64 _claimEnd,
            bytes32 _merkleRoot,
            address _token,
            address _vault,
            uint64 _withdrawalWindow
        )
            external
            initializer
        {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L54

```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

 25:     function init(
            address _owner,
            uint64 _claimStart,
            uint64 _claimEnd,
            bytes32 _merkleRoot,
            address _token,
            address _vault
        )
            external
            initializer
        {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L25

```solidity
File: packages/protocol/contracts/tokenvault/BaseVault.sol

 32:     function init(address _owner, address _addressManager) external initializer {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseVault.sol#L32

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

 38:     function init(
            address _owner,
            address _addressManager,
            address _srcToken,
            uint256 _srcChainId,
            string memory _symbol,
            string memory _name
        )
            external
            initializer
        {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L38

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

 52:     function init(
            address _owner,
            address _addressManager,
            address _srcToken,
            uint256 _srcChainId,
            uint8 _decimals,
            string memory _symbol,
            string memory _name
        )
            external
            initializer
        {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L52

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

 31:     function init(
            address _owner,
            address _addressManager,
            address _srcToken,
            uint256 _srcChainId,
            string memory _symbol,
            string memory _name
        )
            external
            initializer
        {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L31

```solidity
File: packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

 38:     function init(address _owner, address _addressManager, IUSDC _usdc) external initializer {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L38

```solidity
File: packages/protocol/contracts/verifiers/GuardianVerifier.sol

 18:     function init(address _owner, address _addressManager) external initializer {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L18

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

 83:     function init(address _owner, address _addressManager) external initializer {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L83


## [GAS-30] internal functions only called once can be inlined to save gas
If an internal function is only used once, there is no need to modularize it, unless the function calling it would otherwise be too long and complex. Not inlining costs 20 to 40 gas because of two extra JUMP instructions and additional stack operations needed for function calls.

**Total Instances:** 31
**Gas per instance:** 20
**Total Gas saved:** 620

```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

 220:     function _authorizePause(address)
             internal
             view
             virtual
             override
             onlyFromOwnerOrNamed("chain_pauser")
         { }

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L220

```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

 105:     function _mint(
             address _to,
             uint256 _amount
         )
             internal
             override(ERC20Upgradeable, ERC20VotesUpgradeable)
         {

 115:     function _burn(
             address _from,
             uint256 _amount
         )
             internal
             override(ERC20Upgradeable, ERC20VotesUpgradeable)
         {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoToken.sol#L105

```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

 122:     function canDepositEthToL2(
             TaikoData.State storage _state,
             TaikoData.Config memory _config,
             uint256 _amount
         )
             internal
             view
             returns (bool)
         {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L122

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

 287:     function isBlobReusable(
             TaikoData.State storage _state,
             TaikoData.Config memory _config,
             bytes32 _blobHash
         )
             internal
             view
             returns (bool)
         {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L287

```solidity
File: packages/protocol/contracts/L1/libs/LibUtils.sol

 70:     function getTransitionId(
            TaikoData.State storage _state,
            TaikoData.Block storage _blk,
            uint64 _slot,
            bytes32 _parentHash
        )
            internal
            view
            returns (uint32 tid_)
        {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibUtils.sol#L70

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

 126:     function _attestationTcbIsValid(TCBInfoStruct.TCBStatus status)
             internal
             pure
             virtual
             returns (bool valid)
         {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L126

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

 267:     function parseCerificationChainBytes(
             bytes memory certBytes,
             address pemCertLibAddr
         )
             internal
             pure
             returns (bytes[3] memory certChainData)
         {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L267

```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

 39:     function compare(bytes memory self, bytes memory other) internal pure returns (int256) {

 56:     function compare(
            bytes memory self,
            uint256 offset,
            uint256 len,
            bytes memory other,
            uint256 otheroffset,
            uint256 otherlen
        )
            internal
            pure
            returns (int256)
        {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L39

```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

 43:     function pkcs1Sha256(
            bytes32 _sha256,
            bytes memory _s,
            bytes memory _e,
            bytes memory _m
        )
            internal
            view
            returns (bool)
        {

 212:     function pkcs1Sha1(
             bytes20 _sha1,
             bytes memory _s,
             bytes memory _e,
             bytes memory _m
         )
             internal
             view
             returns (bool)
         {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L43

```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

 34:     function toUnixTimestamp(
            uint16 year,
            uint8 month,
            uint8 day,
            uint8 hour,
            uint8 minute,
            uint8 second
        )
            internal
            pure
            returns (uint256)
        {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L34

```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

 95:     function __Essential_init(
            address _owner,
            address _addressManager
        )
            internal
            virtual
            onlyInitializing
        {

 109:     function __Essential_init(address _owner) internal virtual {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L95

```solidity
File: packages/protocol/contracts/libs/LibAddress.sol

 22:     function sendEther(address _to, uint256 _amount, uint256 _gasLimit) internal {

 42:     function sendEther(address _to, uint256 _amount) internal {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibAddress.sol#L22

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

 206:     function _verifyHopProof(
             uint64 _chainId,
             address _app,
             bytes32 _signal,
             bytes32 _value,
             HopProof memory _hop,
             address _signalService
         )
             internal
             virtual
             validSender(_app)
             nonZeroValue(_signal)
             nonZeroValue(_value)
             returns (bytes32)
         {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L206

```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

 77:     function _verifyMerkleProof(
            bytes32[] calldata _proof,
            bytes32 _merkleRoot,
            bytes32 _value
        )
            internal
            pure
            virtual
            returns (bool)
        {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L77

```solidity
File: packages/protocol/contracts/thirdparty/optimism/Bytes.sol

 15:     function slice(
            bytes memory _bytes,
            uint256 _start,
            uint256 _length
        )
            internal
            pure
            returns (bytes memory)
        {

 91:     function slice(bytes memory _bytes, uint256 _start) internal pure returns (bytes memory) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L15

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

 53:     function readList(RLPItem memory _in) internal pure returns (RLPItem[] memory out_) {

 102:     function readList(bytes memory _in) internal pure returns (RLPItem[] memory out_) {

 109:     function readBytes(RLPItem memory _in) internal pure returns (bytes memory out_) {

 128:     function readBytes(bytes memory _in) internal pure returns (bytes memory out_) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L53

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

 13:     function writeBytes(bytes memory _in) internal pure returns (bytes memory out_) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L13

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

 68:     function get(
            bytes memory _key,
            bytes[] memory _proof,
            bytes32 _root
        )
            internal
            pure
            returns (bytes memory value_)
        {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L68

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

 163:     function _mint(
             address _to,
             uint256 _amount
         )
             internal
             override(ERC20Upgradeable, ERC20VotesUpgradeable)
         {

 173:     function _burn(
             address _from,
             uint256 _amount
         )
             internal
             override(ERC20Upgradeable, ERC20VotesUpgradeable)
         {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L163

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

 97:     function _mintToken(address _account, uint256 _amount) internal virtual;

 99:     function _burnToken(address _from, uint256 _amount) internal virtual;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L99


## [GAS-31] A modifier used only once and not being inherited should be inlined to save gas
When you use a modifier in Solidity, Solidity generates code to check the conditions of the modifier and execute the modified function if the conditions are met. This generated code can consume gas, especially if the modifier is used frequently or if the modified function is called multiple times. By inlining a modifier that is used only once and not being inherited, you can eliminate the overhead of the generated code and reduce the gas cost of your contract.

**Total Instances:** 5

```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

 53:     modifier whenPaused() {

 58:     modifier whenNotPaused() {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L53

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

 39:     modifier ongoingWithdrawals() {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L39

```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

 33:     modifier ongoingClaim() {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L33

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

 37:     modifier onlyOwnerOrSnapshooter() {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L37


## [GAS-32] Private functions only used once can be inlined to save gas
If a private function is only used once, there is no need to modularize it, unless the function calling it would otherwise be too long and complex.

**Total Instances:** 41
**Gas per instance:** 30
**Total Gas saved:** 1230

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

 164:     function _getProverFee(
             TaikoData.TierFee[] memory _tierFees,
             uint16 _tierId
         )
             private
             pure
             returns (uint256)
         {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L164

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

 299:     function _isProposerPermitted(
             TaikoData.SlotB memory _slotB,
             IAddressResolver _resolver
         )
             private
             view
             returns (bool)
         {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L299

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

 269:     function _createTransition(
             TaikoData.State storage _state,
             TaikoData.Block storage _blk,
             TaikoData.Transition memory _tran,
             uint64 slot
         )
             private
             returns (uint32 tid_, TaikoData.TransitionState storage ts_)
         {

 350:     function _overrideWithHigherProof(
             TaikoData.TransitionState storage _ts,
             TaikoData.Transition memory _tran,
             TaikoData.TierProof memory _proof,
             ITierProvider.Tier memory _tier,
             IERC20 _tko,
             bool _sameTransition
         )
             private
         {

 401:     function _checkProverPermission(
             TaikoData.State storage _state,
             TaikoData.Block storage _blk,
             TaikoData.TransitionState storage _ts,
             uint32 _tid,
             ITierProvider.Tier memory _tier
         )
             private
             view
         {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L269

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

 224:     function _syncChainData(
             TaikoData.Config memory _config,
             IAddressResolver _resolver,
             uint64 _lastVerifiedBlockId,
             bytes32 _stateRoot
         )
             private
         {

 245:     function _isConfigValid(TaikoData.Config memory _config) private view returns (bool) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L224

```solidity
File: packages/protocol/contracts/L2/Lib1559Math.sol

 33:     function _ethQty(
            uint256 _gasExcess,
            uint256 _adjustmentFactor
        )
            private
            pure
            returns (uint256)
        {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/Lib1559Math.sol#L33

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

 162:     function _verify(bytes calldata quote) private view returns (bool, bytes memory) {

 175:     function _verifyQEReportWithIdentity(V3Struct.EnclaveReport memory quoteEnclaveReport)
             private
             view
             returns (bool, EnclaveIdStruct.EnclaveIdStatus status)
         {

 206:     function _checkTcbLevels(
             IPEMCertChainLib.PCKCertificateField memory pck,
             TCBInfoStruct.TCBInfo memory tcb
         )
             private
             pure
             returns (bool, TCBInfoStruct.TCBStatus status)
         {

 229:     function _isCpuSvnHigherOrGreater(
             uint256[] memory pckCpuSvns,
             uint8[] memory tcbCpuSvns
         )
             private
             pure
             returns (bool)
         {

 248:     function _verifyCertChain(IPEMCertChainLib.ECSha256Certificate[] memory certs)
             private
             view
             returns (bool)
         {

 303:     function _enclaveReportSigVerification(
             bytes memory pckCertPubKey,
             bytes memory signedQuoteData,
             V3Struct.ECDSAQuoteV3AuthData memory authDataV3,
             V3Struct.EnclaveReport memory qeEnclaveReport
         )
             private
             view
             returns (bool)
         {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L162

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

 216:     function _removeHeadersAndFooters(string memory pemData)
             private
             pure
             returns (bool success, bytes memory extracted, uint256 endIndex)
         {

 269:     function _findPckTcbInfo(
             bytes memory der,
             uint256 tbsPtr,
             uint256 tbsParentPtr
         )
             private
             pure
             returns (
                 bool success,
                 uint256 pcesvn,
                 uint256[] memory cpusvns,
                 bytes memory fmspcBytes,
                 bytes memory pceidBytes
             )
         {

 341:     function _findTcb(
             bytes memory der,
             uint256 oidPtr
         )
             private
             pure
             returns (bool success, uint256 pcesvn, uint256[] memory cpusvns)
         {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L216

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

 165:     function parseAndVerifyHeader(bytes memory rawHeader)
             private
             pure
             returns (bool success, V3Struct.Header memory header)
         {

 203:     function parseAuthDataAndVerifyCertType(
             bytes memory rawAuthData,
             address pemCertLibAddr
         )
             private
             pure
             returns (bool success, V3Struct.ECDSAQuoteV3AuthData memory authDataV3)
         {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L165

```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

 272:     function memcpy(uint256 dest, uint256 src, uint256 len) private pure {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L272

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 555:     function _loadContext() private view returns (Context memory) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L555

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

 271:     function _cacheChainData(
             HopProof memory _hop,
             uint64 _chainId,
             uint64 _blockId,
             bytes32 _signalRoot,
             bool _isFullProof,
             bool _isLastHop
         )
             private
         {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L271

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

 225:     function _voidGrant(Grant storage _grant) private returns (uint128 amountVoided) {

 239:     function _getAmountUnlocked(Grant memory _grant) private view returns (uint128) {

 267:     function _validateGrant(Grant memory _grant) private pure {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L225

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

 32:     function _writeLength(uint256 _len, uint256 _offset) private pure returns (bytes memory out_) {

 55:     function _toBinary(uint256 _x) private pure returns (bytes memory out_) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L32

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

 205:     function _parseProof(bytes[] memory _proof) private pure returns (TrieNode[] memory proof_) {

 227:     function _getNodePath(TrieNode memory _node) private pure returns (bytes memory nibbles_) {

 235:     function _getSharedNibbleLength(
             bytes memory _a,
             bytes memory _b
         )
             private
             pure
             returns (uint256 shared_)
         {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L205

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

 240:     function _handleMessage(
             address _user,
             BridgeTransferOp memory _op
         )
             private
             returns (bytes memory msgData_, CanonicalNFT memory ctoken_)
         {

 288:     function _getOrDeployBridgedToken(CanonicalNFT memory _ctoken)
             private
             returns (address btoken_)
         {

 303:     function _deployBridgedToken(CanonicalNFT memory _ctoken) private returns (address btoken_) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L240

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

 348:     function _handleMessage(
             address _user,
             address _token,
             address _to,
             uint256 _amount
         )
             private
             returns (bytes memory msgData_, CanonicalERC20 memory ctoken_, uint256 balanceChange_)
         {

 391:     function _getOrDeployBridgedToken(CanonicalERC20 memory ctoken)
             private
             returns (address btoken)
         {

 407:     function _deployBridgedToken(CanonicalERC20 memory ctoken) private returns (address btoken) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L348

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

 187:     function _handleMessage(
             address _user,
             BridgeTransferOp memory _op
         )
             private
             returns (bytes memory msgData_, CanonicalNFT memory ctoken_)
         {

 224:     function _getOrDeployBridgedToken(CanonicalNFT memory _ctoken)
             private
             returns (address btoken_)
         {

 240:     function _deployBridgedToken(CanonicalNFT memory _ctoken) private returns (address btoken_) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L187

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

 226:     function _replaceInstance(uint256 id, address oldInstance, address newInstance) private {

 233:     function _isInstanceValid(uint256 id, address instance) private view returns (bool) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L233


## [GAS-33] Usage of ints/uints smaller than 32 bytes incurs overhead
Using ints/uints smaller than 32 bytes may cost more gas. This is because the EVM operates on 32 bytes at a time, so if an element is smaller than 32 bytes, the EVM must perform more operations to reduce the size of the element from 32 bytes to the desired size.

**Total Instances:** 363
**Gas per instance:** 55
**Total Gas saved:** 19965

```solidity
File: packages/protocol/contracts/L1/ITaikoL1.sol

 27:     function proveBlock(uint64 _blockId, bytes calldata _input) external;

 31:     function verifyBlocks(uint64 _maxBlocksToVerify) external;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/ITaikoL1.sol#L27

```solidity
File: packages/protocol/contracts/L1/TaikoData.sol

 15:         uint64 chainId;

 20:         uint64 blockMaxProposals;

 22:         uint64 blockRingBufferSize;

 24:         uint64 maxBlocksToVerifyPerProposal;

 26:         uint32 blockMaxGasLimit;

 28:         uint24 blockMaxTxListBytes;

 30:         uint24 blobExpiry;

 39:         uint96 livenessBond;

 46:         uint64 ethDepositMinCountPerBlock;

 48:         uint64 ethDepositMaxCountPerBlock;

 50:         uint96 ethDepositMinAmount;

 52:         uint96 ethDepositMaxAmount;

 59:         uint8 blockSyncThreshold;

 64:         uint16 tier;

 65:         uint128 fee;

 69:         uint16 tier;

 83:         uint24 txListByteOffset;

 84:         uint24 txListByteSize;

 101:         uint64 id;

 102:         uint32 gasLimit;

 103:         uint64 timestamp; // slot 7

 104:         uint64 l1Height;

 105:         uint24 txListByteOffset;

 106:         uint24 txListByteSize;

 107:         uint16 minTier;

 127:         uint96 validityBond;

 129:         uint96 contestBond;

 130:         uint64 timestamp; // slot 6 (90 bits)

 131:         uint16 tier;

 132:         uint8 contestations;

 140:         uint96 livenessBond;

 141:         uint64 blockId; // slot 3

 142:         uint64 proposedAt; // timestamp

 143:         uint64 proposedIn; // L1 block number

 144:         uint32 nextTransitionId;

 145:         uint32 verifiedTransitionId;

 152:         uint96 amount;

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
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L15

```solidity
File: packages/protocol/contracts/L1/TaikoEvents.sol

 24:         uint96 livenessBond,

 43:         uint16 tier,

 44:         uint8 contestations

 57:         uint96 validityBond,

 58:         uint16 tier

 71:         uint96 contestBond,

 72:         uint16 tier

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoEvents.sol#L24

```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

 76:         uint64 _blockId,

 94:         uint8 maxBlocksToVerify = LibProving.proveBlock(state, config, this, meta, tran, proof);

 100:     function verifyBlocks(uint64 _maxBlocksToVerify)

 145:     function getBlock(uint64 _blockId)

 150:         uint64 slot;

 163:         uint64 _blockId,

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L76

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

 20:         uint64 expiry;

 21:         uint64 maxBlockId;

 22:         uint64 maxProposedIn;

 166:         uint16 _tierId

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L20

```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

 83:             uint96 fee = uint96(_config.ethDepositMaxFee.min(block.basefee * _config.ethDepositGas));

 84:             uint64 j = _state.slotA.nextEthDepositToProcess;

 85:             uint96 totalFee;

 93:                 uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount;

 150:         if (_amount > type(uint96).max) revert L1_INVALID_ETH_DEPOSIT();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L83

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

 34:         uint96 livenessBond,

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L34

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

 36:         uint96 validityBond,

 37:         uint16 tier

 50:         uint96 contestBond,

 51:         uint16 tier

 100:         returns (uint8 maxBlocksToVerify_)

 115:         uint64 slot = _meta.id % _config.blockRingBufferSize;

 129:         (uint32 tid, TaikoData.TransitionState storage ts) =

 273:         uint64 slot

 276:         returns (uint32 tid_, TaikoData.TransitionState storage ts_)

 405:         uint32 _tid,

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L36

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
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibUtils.sol#L26

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

 260:                 || _config.ethDepositMaxAmount > type(uint96).max || _config.ethDepositGas == 0

 262:                 || _config.ethDepositMaxFee > type(uint96).max / _config.ethDepositMaxCountPerBlock

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L34

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

 19:     mapping(uint32 version => mapping(bytes32 hash => uint256 approvalBits)) internal _approvals;

 27:     uint32 public version;

 30:     uint32 public minGuardians;

 37:     event GuardiansUpdated(uint32 version, address[] guardians);

 55:         uint8 _minGuardians

 63:         if (_newGuardians.length < MIN_NUM_GUARDIANS || _newGuardians.length > type(uint8).max) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L19

```solidity
File: packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol

 20:     function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {

 47:     function getTierIds() public pure override returns (uint16[] memory tiers_) {

 48:         tiers_ = new uint16[](2);

 54:     function getMinTier(uint256) public pure override returns (uint16) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L20

```solidity
File: packages/protocol/contracts/L1/tiers/ITierProvider.sol

 10:         uint96 validityBond;

 11:         uint96 contestBond;

 12:         uint24 cooldownWindow; // in minutes

 13:         uint16 provingWindow; // in minutes

 14:         uint8 maxBlocksToVerifyPerProof;

 22:     function getTier(uint16 tierId) external view returns (Tier memory);

 28:     function getTierIds() external view returns (uint16[] memory);

 33:     function getMinTier(uint256 rand) external view returns (uint16);

 39:     uint16 public constant TIER_OPTIMISTIC = 100;

 42:     uint16 public constant TIER_SGX = 200;

 45:     uint16 public constant TIER_SGX_ZKVM = 300;

 48:     uint16 public constant TIER_GUARDIAN = 1000;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L10

```solidity
File: packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol

 20:     function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {

 58:     function getTierIds() public pure override returns (uint16[] memory tiers_) {

 59:         tiers_ = new uint16[](3);

 66:     function getMinTier(uint256 _rand) public pure override returns (uint16) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L20

```solidity
File: packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol

 20:     function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {

 58:     function getTierIds() public pure override returns (uint16[] memory tiers_) {

 59:         tiers_ = new uint16[](3);

 66:     function getMinTier(uint256 _rand) public pure override returns (uint16) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L20

```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

 16:     uint64 public ownerChainId;

 19:     uint64 public nextTxId;

 26:     event TransactionExecuted(uint64 indexed txId, bytes4 indexed selector);

 42:         (uint64 txId, bytes memory txdata) = abi.decode(_data, (uint64, bytes));

 42:         (uint64 txId, bytes memory txdata) = abi.decode(_data, (uint64, bytes));

 63:         uint64 _ownerChainId

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L16

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

 82:         if (block.chainid <= 1 || block.chainid > type(uint64).max) {

 110:         uint64 _l1BlockId,

 111:         uint32 _parentGasUsed

 186:         uint64 _l1BlockId,

 187:         uint32 _parentGasUsed

 200:     function getBlockHash(uint64 _blockId) public view returns (bytes32) {

 254:         uint64 _l1BlockId,

 255:         uint32 _parentGasUsed

 259:         returns (uint256 basefee_, uint64 gasExcess_)

 284:             gasExcess_ = uint64(excess.min(type(uint64).max));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L27

```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

 18:     event ConfigAndExcessChanged(Config config, uint64 gasExcess);

 27:         uint64 _newGasExcess

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L18

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

 36:     uint8 internal constant INVALID_EXIT_CODE = 255;

 231:         uint8[] memory tcbCpuSvns

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L36

```solidity
File: packages/protocol/contracts/automata-attestation/lib/EnclaveIdStruct.sol

 10:         uint16 isvprodid;

 23:         uint16 isvsvn;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/EnclaveIdStruct.sol#L10

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

 358:             uint16 svnValue = svnValueBytes.length < 2

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L358

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

 106:         uint32 totalQuoteSize = 48 // header

 249:         uint16 isvProdIdPackBE = (enclaveReport.isvProdId >> 8) | (enclaveReport.isvProdId << 8);

 250:         uint16 isvSvnPackBE = (enclaveReport.isvSvn >> 8) | (enclaveReport.isvSvn << 8);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L106

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol

 26:         uint16 isvProdId;

 27:         uint16 isvSvn;

 34:         uint16 parsedDataSize;

 39:         uint16 certType;

 43:         uint32 certDataSize;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L26

```solidity
File: packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol

 15:         uint8[] sgxTcbCompSvnArr;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol#L15

```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

 189:         uint80 ixFirstContentByte;

 190:         uint80 ixLastContentByte;

 196:             uint8 lengthbytesLength = uint8(der[ix + 1] & 0x7F);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L189

```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

 188:     function readUint8(bytes memory self, uint256 idx) internal pure returns (uint8 ret) {

 198:     function readUint16(bytes memory self, uint256 idx) internal pure returns (uint16 ret) {

 211:     function readUint32(bytes memory self, uint256 idx) internal pure returns (uint32 ret) {

 332:         uint8 decoded;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L188

```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

 53:         uint8[17] memory sha256ExplicitNullParam = [

 73:         uint8[15] memory sha256ImplicitNullParam = [

 222:         uint8[15] memory sha1Prefix = [

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L53

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

 56:         uint8[12] memory monthDays = [31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31];

 59:         for (uint8 i = 1; i < month; ++i) {

 71:     function isLeapYear(uint16 year) internal pure returns (bool) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L9

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 31:     uint128 public nextMessageId;

 64:     modifier sameChain(uint64 _chainId) {

 89:         uint64 _timestamp = _suspend ? type(uint64).max : uint64(block.timestamp);

 89:         uint64 _timestamp = _suspend ? type(uint64).max : uint64(block.timestamp);

 168:         uint64 receivedAt = proofReceipt[msgHash].receivedAt;

 230:         uint64 receivedAt = proofReceipt[msgHash].receivedAt;

 392:     function isDestChainEnabled(uint64 _chainId)

 541:     function _storeContext(bytes32 _msgHash, address _from, uint64 _srcChainId) private {

 559:             uint64 srcChainId;

 580:         uint64 _chainId,

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L31

```solidity
File: packages/protocol/contracts/bridge/IBridge.sol

 19:         uint128 id;

 24:         uint64 srcChainId;

 26:         uint64 destChainId;

 51:         uint64 receivedAt;

 63:         uint64 srcChainId; // Source chain ID.

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/IBridge.sol#L19

```solidity
File: packages/protocol/contracts/common/AddressManager.sol

 22:         uint64 indexed chainId, bytes32 indexed name, address newAddress, address oldAddress

 39:         uint64 _chainId,

 54:     function getAddress(uint64 _chainId, bytes32 _name) public view override returns (address) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressManager.sol#L22

```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

 11:     uint8 private constant _FALSE = 1;

 13:     uint8 private constant _TRUE = 2;

 21:     uint8 private __reentry;

 23:     uint8 private __paused;

 119:     function _storeReentryLock(uint8 _reentry) internal virtual {

 130:     function _loadReentryLock() internal view virtual returns (uint8 reentry_) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L11

```solidity
File: packages/protocol/contracts/common/IAddressManager.sol

 14:     function getAddress(uint64 _chainId, bytes32 _name) external view returns (address);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/IAddressManager.sol#L14

```solidity
File: packages/protocol/contracts/libs/Lib4844.sol

 13:     uint32 public constant FIELD_ELEMENTS_PER_BLOB = 4096;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/Lib4844.sol#L13

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
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/ISignalService.sol#L21

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

 17:     mapping(uint64 chainId => mapping(bytes32 kind => uint64 blockId)) public topBlockId;

 17:     mapping(uint64 chainId => mapping(bytes32 kind => uint64 blockId)) public topBlockId;

 69:         uint64 _chainId,

 71:         uint64 _blockId,

 84:         uint64 _chainId,

 97:         uint64 chainId = _chainId;

 138:         uint64 _chainId,

 140:         uint64 _blockId,

 159:         uint64 _chainId,

 161:         uint64 _blockId

 165:         returns (uint64 blockId_, bytes32 chainData_)

 178:         uint64 _chainId,

 180:         uint64 _blockId

 195:         uint64 _chainId,

 207:         uint64 _chainId,

 236:         uint64 _chainId,

 238:         uint64 _blockId,

 273:         uint64 _chainId,

 274:         uint64 _blockId,

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L17

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

 82:     uint128[44] private __gap;

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

 235:     function _getAmountOwned(Grant memory _grant) private view returns (uint128) {

 239:     function _getAmountUnlocked(Grant memory _grant) private view returns (uint128) {

 246:         uint128 _amount,

 247:         uint64 _start,

 248:         uint64 _cliff,

 249:         uint64 _period

 253:         returns (uint128)

 273:     function _validateCliff(uint64 _start, uint64 _cliff, uint32 _period) private pure {

 273:     function _validateCliff(uint64 _start, uint64 _cliff, uint32 _period) private pure {

 273:     function _validateCliff(uint64 _start, uint64 _cliff, uint32 _period) private pure {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L29

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

 29:         uint64 _claimStart,

 30:         uint64 _claimEnd,

 69:         (address delegatee, uint256 nonce, uint256 expiry, uint8 v, bytes32 r, bytes32 s) =

 70:             abi.decode(delegationData, (address, uint256, uint256, uint8, bytes32, bytes32));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L29

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

 28:     uint64 public withdrawalWindow;

 56:         uint64 _claimStart,

 57:         uint64 _claimEnd,

 61:         uint64 _withdrawalWindow

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L28

```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

 27:         uint64 _claimStart,

 28:         uint64 _claimEnd,

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L27

```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

 18:     uint64 public claimStart;

 21:     uint64 public claimEnd;

 46:         uint64 _claimStart,

 47:         uint64 _claimEnd,

 57:         uint64 _claimStart,

 58:         uint64 _claimEnd,

 90:     function _setConfig(uint64 _claimStart, uint64 _claimEnd, bytes32 _merkleRoot) private {

 90:     function _setConfig(uint64 _claimStart, uint64 _claimEnd, bytes32 _merkleRoot) private {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L18

```solidity
File: packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol

 29:         uint16 _maxCopy,

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L29

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

 30:     uint8 internal constant PREFIX_EXTENSION_EVEN = 0;

 33:     uint8 internal constant PREFIX_EXTENSION_ODD = 1;

 36:     uint8 internal constant PREFIX_LEAF_EVEN = 2;

 39:     uint8 internal constant PREFIX_LEAF_ODD = 3;

 134:                     uint8 branchKey = uint8(key[currentKeyIndex]);

 141:                 uint8 prefix = uint8(path[0]);

 142:                 uint8 offset = 2 - (prefix % 2);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L30

```solidity
File: packages/protocol/contracts/tokenvault/BaseNFTVault.sol

 13:         uint64 chainId;

 25:         uint64 destChainId;

 70:         uint64 indexed chainId,

 90:         uint64 destChainId,

 126:         uint64 srcChainId,

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L13

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

 24:     uint8 private __srcDecimals;

 57:         uint8 _decimals,

 117:         returns (uint8)

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L24

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

 24:         uint64 chainId;

 26:         uint8 decimals;

 33:         uint64 destChainId;

 69:         uint8 ctokenDecimal

 87:         uint8 ctokenDecimal

 102:         uint64 destChainId,

 130:         uint64 srcChainId,

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L24

```solidity
File: packages/protocol/contracts/verifiers/IVerifier.sol

 14:         uint64 blockId;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/IVerifier.sol#L14

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

 26:         uint64 validSince;

 30:     uint64 public constant INSTANCE_EXPIRY = 180 days;

 34:     uint64 public constant INSTANCE_VALIDITY_DELAY = 1 days;

 154:         uint32 id = uint32(bytes4(Bytes.slice(_proof.data, 0, 4)));

 204:         uint64 validSince = uint64(block.timestamp);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L204


## [GAS-34] Long require/revert strings
require()/revert() strings longer than 32 bytes cost extra gas

**Total Instances:** 27

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

 87:         require(
                v3Quote.v3AuthData.certification.certType == 5,
                "certType must be 5: Concatenated PCK Cert Chain (PEM formatted)"

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L87

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

 37:         require(
                _in.length > 0,
                "RLPReader: length of an RLP item must be greater than zero to be decodable"

 56:         require(
                itemType == RLPItemType.LIST_ITEM,
                "RLPReader: decoded item type for list is not a list item"

 61:         require(
                listOffset + listLength == _in.length,
                "RLPReader: list item has an invalid data remainder"

 112:         require(
                 itemType == RLPItemType.DATA_ITEM,
                 "RLPReader: decoded item type for bytes is not a data item"

 117:         require(
                 _in.length == itemOffset + itemLength,
                 "RLPReader: bytes value contains an invalid remainder"

 152:         require(
                 _in.length > 0,
                 "RLPReader: length of an RLP item must be greater than zero to be decodable"

 172:             require(
                     _in.length > strLen,
                     "RLPReader: length of content must be greater than string length (short string)"

 182:             require(
                     strLen != 1 || firstByteOfContent >= 0x80,
                     "RLPReader: invalid prefix, single byte < 0x80 are not prefixed (short string)"

 192:             require(
                     _in.length > lenOfStrLen,
                     "RLPReader: length of content must be > than length of string length (long string)"

 202:             require(
                     firstByteOfContent != 0x00,
                     "RLPReader: length of content must not have any leading zeros (long string)"

 212:             require(
                     strLen > 55,
                     "RLPReader: length of content must be greater than 55 bytes (long string)"

 217:             require(
                     _in.length > lenOfStrLen + strLen,
                     "RLPReader: length of content must be greater than total length (long string)"

 228:             require(
                     _in.length > listLen,
                     "RLPReader: length of content must be greater than list length (short list)"

 238:             require(
                     _in.length > lenOfListLen,
                     "RLPReader: length of content must be > than length of list length (long list)"

 248:             require(
                     firstByteOfContent != 0x00,
                     "RLPReader: length of content must not have any leading zeros (long list)"

 258:             require(
                     listLen > 55,
                     "RLPReader: length of content must be greater than 55 bytes (long list)"

 263:             require(
                     _in.length > lenOfListLen + listLen,
                     "RLPReader: length of content must be greater than total length (long list)"

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L37

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

 89:             require(currentKeyIndex <= key.length, "MerkleTrie: key index exceeds total key length");

 99:                 require(
                        Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
                        "MerkleTrie: invalid large internal hash"

 105:                 require(
                         Bytes.equal(currentNode.encoded, currentNodeID),
                         "MerkleTrie: invalid internal node hash"

 119:                     require(
                             value_.length > 0,
                             "MerkleTrie: value length must be greater than zero (branch)"

 125:                     require(
                             i == proof.length - 1,
                             "MerkleTrie: value node must be last node in proof (branch)"

 150:                 require(
                         pathRemainder.length == sharedNibbleLength,
                         "MerkleTrie: path remainder must share all nibbles with key"

 162:                     require(
                             keyRemainder.length == sharedNibbleLength,
                             "MerkleTrie: key remainder must be identical to path remainder"

 172:                     require(
                             value_.length > 0,
                             "MerkleTrie: value length must be greater than zero (leaf)"

 178:                     require(
                             i == proof.length - 1,
                             "MerkleTrie: value node must be last node in proof (leaf)"

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L178


## [GAS-35] Using a nesting if statement instead of a logical AND(&&)
Using a nesting if statement instead of a logical AND (&&) can provide similar short-circuiting behavior whereas double if is slightly more gas efficient.

**Total Instances:** 15
**Gas per instance:** 6
**Total Gas saved:** 90

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

 120:         if (input.tip != 0 && block.coinbase != address(0)) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L120

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

 108:         if (params.parentMetaHash != 0 && parentMetaHash != params.parentMetaHash) {

 164:                 if (_config.blobReuseEnabled && params.cacheBlobForReuse) {

 310:             if (proposerOne != address(0) && msg.sender != proposerOne) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L108

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

 141:         if (!skipFeeCheck() && block.basefee != basefee) {

 275:             if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L141

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

 220:             if (pceSvnIsHigherOrGreater && cpuSvnsAreHigherOrGreater) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L220

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 250:         if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) {

 260:             if (_message.gasLimit == 0 && msg.sender != _message.destOwner) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L250

```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

 42:         if (msg.sender != owner() && msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L42

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

 285:         if (cacheStateRoot && _isFullProof && !_isLastHop) {

 293:         if (cacheSignalRoot && (_isFullProof || !_isLastHop)) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L285

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

 277:             if (_cliff > 0 && _cliff <= _start) revert INVALID_GRANT();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L277

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

 38:         if (msg.sender != owner() && msg.sender != snapshooter) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L38

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

 45:         if (_migratingAddress == migratingAddress && _migratingInbound == migratingInbound) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L45


## [GAS-36] Optimize names to save gas
public/external function names and public member variable names can be optimized to save gas. Below are the interfaces/abstract contracts that can be optimized so that the most frequently-called functions use the least amount of gas possible during method lookup. Method IDs that have two leading zero bytes can save 128 gas each during deployment, and renaming functions to have lower method IDs will save 22 gas per call, per sorted position shifted.

**Total Instances:** 53
**Gas per instance:** 22
**Total Gas saved:** 1166

```solidity
File: packages/protocol/contracts/L1/ITaikoL1.sol

 /// @audit  proposeBlock(), proveBlock(), verifyBlocks(), getConfig(), 
 8: interface ITaikoL1 {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/ITaikoL1.sol#L8

```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

 /// @audit  (), init(), proposeBlock(), proveBlock(), verifyBlocks(), pauseProving(), depositEtherToL2(), unpause(), canDepositEthToL2(), isBlobReusable(), getBlock(), getTransition(), getStateVariables(), getConfig(), state, 
 22: contract TaikoL1 is EssentialContract, ITaikoL1, TaikoEvents, TaikoErrors {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L22

```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

 /// @audit  init(), burn(), snapshot(), transfer(), transferFrom(), 
 15: contract TaikoToken is EssentialContract, ERC20SnapshotUpgradeable, ERC20VotesUpgradeable {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoToken.sol#L15

```solidity
File: packages/protocol/contracts/L1/gov/TaikoGovernor.sol

 /// @audit  init(), propose(), propose(), supportsInterface(), state(), votingDelay(), votingPeriod(), proposalThreshold(), 
 16: contract TaikoGovernor is

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L16

```solidity
File: packages/protocol/contracts/L1/gov/TaikoTimelockController.sol

 /// @audit  init(), getMinDelay(), 
 9: contract TaikoTimelockController is EssentialContract, TimelockControllerUpgradeable {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L9

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

 /// @audit  init(), onBlockProposed(), hashAssignment(), MAX_GAS_PAYING_PROVER, 
 14: contract AssignmentHook is EssentialContract, IHook {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L14

```solidity
File: packages/protocol/contracts/L1/hooks/IHook.sol

 /// @audit  onBlockProposed(), 
 8: interface IHook {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/IHook.sol#L8

```solidity
File: packages/protocol/contracts/L1/provers/GuardianProver.sol

 /// @audit  init(), approve(), 
 10: contract GuardianProver is Guardians {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/GuardianProver.sol#L10

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

 /// @audit  setGuardians(), isApproved(), numGuardians(), MIN_NUM_GUARDIANS, guardianIds, guardians, version, minGuardians, 
 9: abstract contract Guardians is EssentialContract {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L9

```solidity
File: packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol

 /// @audit  init(), getTier(), getTierIds(), getMinTier(), 
 10: contract DevnetTierProvider is EssentialContract, ITierProvider {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L10

```solidity
File: packages/protocol/contracts/L1/tiers/ITierProvider.sol

 /// @audit  getTier(), getTierIds(), getMinTier(), 
 7: interface ITierProvider {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L7

```solidity
File: packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol

 /// @audit  init(), getTier(), getTierIds(), getMinTier(), 
 10: contract MainnetTierProvider is EssentialContract, ITierProvider {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L10

```solidity
File: packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol

 /// @audit  init(), getTier(), getTierIds(), getMinTier(), 
 10: contract TestnetTierProvider is EssentialContract, ITierProvider {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L10

```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

 /// @audit  onMessageInvocation(), ownerChainId, nextTxId, 
 14: abstract contract CrossChainOwned is EssentialContract, IMessageInvocable {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L14

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

 /// @audit  init(), anchor(), withdraw(), getBasefee(), getBlockHash(), getConfig(), skipFeeCheck(), GOLDEN_TOUCH_ADDRESS, BLOCK_SYNC_THRESHOLD, l2Hashes, publicInputHash, gasExcess, lastSyncedBlock, 
 21: contract TaikoL2 is CrossChainOwned {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L21

```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

 /// @audit  setConfigAndExcess(), getConfig(), customConfig, 
 9: contract TaikoL2EIP1559Configurable is TaikoL2 {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L9

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

 /// @audit  (), setMrSigner(), setMrEnclave(), addRevokedCertSerialNum(), removeRevokedCertSerialNum(), configureTcbInfoJson(), configureQeIdentityJson(), toggleLocalReportCheck(), verifyAttestation(), verifyParsedQuote(), sigVerifyLib, pemCertLib, tcbInfo, qeIdentity, owner, 
 22: contract AutomataDcapV3Attestation is IAttestation {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L22

```solidity
File: packages/protocol/contracts/automata-attestation/interfaces/IAttestation.sol

 /// @audit  verifyAttestation(), verifyParsedQuote(), 
 8: interface IAttestation {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/interfaces/IAttestation.sol#L8

```solidity
File: packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol

 /// @audit  verifyAttStmtSignature(), verifyCertificateSignature(), verifyRS256Signature(), verifyRS1Signature(), verifyES256Signature(), 
 6: interface ISigVerifyLib {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L6

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

 /// @audit  splitCertificateChain(), decodeCert(), 
 12: contract PEMCertChainLib is IPEMCertChainLib {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L12

```solidity
File: packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol

 /// @audit  splitCertificateChain(), decodeCert(), 
 6: interface IPEMCertChainLib {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L6

```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

 /// @audit  (), verifyAttStmtSignature(), verifyCertificateSignature(), verifyRS256Signature(), verifyRS1Signature(), verifyES256Signature(), 
 15: contract SigVerifyLib is ISigVerifyLib {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L15

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 /// @audit  (), init(), suspendMessages(), banAddress(), sendMessage(), recallMessage(), processMessage(), retryMessage(), isMessageSent(), proveMessageFailed(), proveMessageReceived(), isDestChainEnabled(), context(), getInvocationDelays(), hashMessage(), signalForFailedMessage(), nextMessageId, messageStatus, addressBanned, proofReceipt, 
 16: contract Bridge is EssentialContract, IBridge {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L16

```solidity
File: packages/protocol/contracts/bridge/IBridge.sol

 /// @audit  sendMessage(), recallMessage(), processMessage(), retryMessage(), context(), isMessageSent(), hashMessage(), 
 8: interface IBridge {

 /// @audit  onMessageRecalled(), 
 160: interface IRecallableSender {

 /// @audit  onMessageInvocation(), 
 174: interface IMessageInvocable {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/IBridge.sol#L8

```solidity
File: packages/protocol/contracts/common/AddressManager.sol

 /// @audit  init(), setAddress(), getAddress(), 
 10: contract AddressManager is EssentialContract, IAddressManager {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressManager.sol#L10

```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

 /// @audit  pause(), unpause(), paused(), 
 10: abstract contract EssentialContract is UUPSUpgradeable, Ownable2StepUpgradeable, AddressResolver {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L10

```solidity
File: packages/protocol/contracts/common/IAddressManager.sol

 /// @audit  getAddress(), 
 7: interface IAddressManager {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/IAddressManager.sol#L7

```solidity
File: packages/protocol/contracts/signal/ISignalService.sol

 /// @audit  sendSignal(), syncChainData(), proveSignalReceived(), isSignalSent(), isChainDataSynced(), getSyncedChainData(), signalForChainData(), 
 12: interface ISignalService {

 /// @audit  sendSignal(), syncChainData(), proveSignalReceived(), isSignalSent(), isChainDataSynced(), getSyncedChainData(), signalForChainData(), 
 12: interface ISignalService {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/ISignalService.sol#L12

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

 /// @audit  init(), authorize(), sendSignal(), syncChainData(), proveSignalReceived(), isChainDataSynced(), isSignalSent(), getSyncedChainData(), signalForChainData(), getSignalSlot(), topBlockId, isAuthorized, 
 14: contract SignalService is EssentialContract, ISignalService {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L14

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

 /// @audit  init(), grant(), void(), withdraw(), withdraw(), getMyGrantSummary(), getMyGrant(), taikoToken, costToken, sharedVault, totalAmountGranted, totalAmountVoided, totalAmountWithdrawn, totalCostPaid, recipients, 
 25: contract TimelockTokenPool is EssentialContract {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L25

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

 /// @audit  init(), claimAndDelegate(), token, vault, 
 11: contract ERC20Airdrop is MerkleClaimable {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L11

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

 /// @audit  init(), claim(), withdraw(), getBalance(), token, vault, claimedAmount, withdrawnAmount, withdrawalWindow, 
 12: contract ERC20Airdrop2 is MerkleClaimable {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L12

```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

 /// @audit  init(), claim(), token, vault, 
 9: contract ERC721Airdrop is MerkleClaimable {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L9

```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

 /// @audit  setConfig(), isClaimed, merkleRoot, claimStart, claimEnd, 
 10: abstract contract MerkleClaimable is EssentialContract {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L10

```solidity
File: packages/protocol/contracts/tokenvault/BaseNFTVault.sol

 /// @audit  ERC1155_INTERFACE_ID, ERC721_INTERFACE_ID, MAX_TOKEN_PER_TXN, bridgedToCanonical, canonicalToBridged, 
 9: abstract contract BaseNFTVault is BaseVault {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L9

```solidity
File: packages/protocol/contracts/tokenvault/BaseVault.sol

 /// @audit  init(), supportsInterface(), name(), 
 12: abstract contract BaseVault is

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseVault.sol#L12

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

 /// @audit  init(), mint(), mintBatch(), burn(), name(), symbol(), srcToken, srcChainId, 
 14: contract BridgedERC1155 is EssentialContract, IERC1155MetadataURIUpgradeable, ERC1155Upgradeable {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L14

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

 /// @audit  init(), setSnapshoter(), snapshot(), name(), symbol(), decimals(), canonical(), srcToken, srcChainId, snapshooter, 
 15: contract BridgedERC20 is

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L15

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

 /// @audit  changeMigrationStatus(), mint(), burn(), owner(), migratingAddress, migratingInbound, 
 9: abstract contract BridgedERC20Base is EssentialContract, IBridgedERC20 {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L9

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

 /// @audit  init(), mint(), burn(), name(), symbol(), source(), tokenURI(), srcToken, srcChainId, 
 12: contract BridgedERC721 is EssentialContract, ERC721Upgradeable {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L12

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

 /// @audit  name(), symbol(), 
 16: interface IERC1155NameAndSymbol {

 /// @audit  sendToken(), onMessageInvocation(), onMessageRecalled(), onERC1155BatchReceived(), onERC1155Received(), supportsInterface(), name(), 
 29: contract ERC1155Vault is BaseNFTVault, ERC1155ReceiverUpgradeable {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L16

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

 /// @audit  changeBridgedToken(), sendToken(), onMessageInvocation(), onMessageRecalled(), name(), bridgedToCanonical, canonicalToBridged, btokenBlacklist, 
 18: contract ERC20Vault is BaseVault {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L18

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

 /// @audit  sendToken(), onMessageInvocation(), onMessageRecalled(), onERC721Received(), name(), 
 16: contract ERC721Vault is BaseNFTVault, IERC721Receiver {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L16

```solidity
File: packages/protocol/contracts/tokenvault/IBridgedERC20.sol

 /// @audit  mint(), burn(), changeMigrationStatus(), owner(), 
 10: interface IBridgedERC20 {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/IBridgedERC20.sol#L10

```solidity
File: packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

 /// @audit  burn(), mint(), transferFrom(), 
 8: interface IUSDC {

 /// @audit  init(), usdc, 
 28: contract USDCAdapter is BridgedERC20Base {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L8

```solidity
File: packages/protocol/contracts/verifiers/GuardianVerifier.sol

 /// @audit  init(), verifyProof(), 
 10: contract GuardianVerifier is EssentialContract, IVerifier {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L10

```solidity
File: packages/protocol/contracts/verifiers/IVerifier.sol

 /// @audit  verifyProof(), 
 9: interface IVerifier {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/IVerifier.sol#L9

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

 /// @audit  init(), addInstances(), deleteInstances(), registerInstance(), verifyProof(), getSignedHash(), INSTANCE_EXPIRY, INSTANCE_VALIDITY_DELAY, nextInstanceId, instances, addressRegistered, 
 19: contract SgxVerifier is EssentialContract, IVerifier {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L19



## [GAS-40] Change public state variable visibility to private
its generally a good practice to limit the visibility of state variables to the minimum necessary level. This means that you should use the private visibility modifier for state variables whenever possible, and avoid using the public modifier unless it is absolutely necessary. Public state variables can be more expensive to read and write than private state variables, since Solidity generates additional getter and setter functions for public variables. By using private state variables, you can reduce the gas cost of your contract and improve its efficiency. Public state variables can be more expensive to read and write than private state variables, since Solidity generates additional getter and setter functions for public variables. By using private state variables, you can reduce the gas cost of your contract and improve its efficiency.

**Total Instances:** 58

```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

 24:     TaikoData.State public state;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L24

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

 38:     uint256 public constant MAX_GAS_PAYING_PROVER = 50_000;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L38

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

 21:     uint256 public constant MAX_BYTES_PER_BLOB = 4096 * 32;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L21

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

 20:     bytes32 public constant RETURN_LIVENESS_BOND = keccak256("RETURN_LIVENESS_BOND");

 23:     bytes32 public constant TIER_OP = bytes32("tier_optimistic");

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L20

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

 11:     uint256 public constant MIN_NUM_GUARDIANS = 5;

 16:     mapping(address guardian => uint256 id) public guardianIds;

 23:     address[] public guardians;

 30:     uint32 public minGuardians;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L11

```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

 19:     uint64 public nextTxId;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L19

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

 32:     address public constant GOLDEN_TOUCH_ADDRESS = 0x0000777735367b36bC9B61C50022d9D0700dB4Ec;

 35:     uint8 public constant BLOCK_SYNC_THRESHOLD = 5;

 39:     mapping(uint256 blockId => bytes32 blockHash) public l2Hashes;

 43:     bytes32 public publicInputHash;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L32

```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

 11:     Config public customConfig;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L11

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

 25:     ISigVerifyLib public immutable sigVerifyLib;

 49:     mapping(string fmspc => TCBInfoStruct.TCBInfo tcbInfo) public tcbInfo;

 50:     EnclaveIdStruct.EnclaveId public qeIdentity;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L25

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 31:     uint128 public nextMessageId;

 35:     mapping(bytes32 msgHash => Status status) public messageStatus;

 42:     mapping(address addr => bool banned) public addressBanned;

 46:     mapping(bytes32 msgHash => ProofReceipt receipt) public proofReceipt;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L31

```solidity
File: packages/protocol/contracts/libs/Lib4844.sol

 10:     address public constant POINT_EVALUATION_PRECOMPILE_ADDRESS = address(0x0A);

 13:     uint32 public constant FIELD_ELEMENTS_PER_BLOB = 4096;

 16:     uint256 public constant BLS_MODULUS =

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/Lib4844.sol#L10

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

 17:     mapping(uint64 chainId => mapping(bytes32 kind => uint64 blockId)) public topBlockId;

 21:     mapping(address addr => bool authorized) public isAuthorized;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L17

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

 59:     address public taikoToken;

 62:     address public costToken;

 65:     address public sharedVault;

 68:     uint128 public totalAmountGranted;

 71:     uint128 public totalAmountVoided;

 74:     uint128 public totalAmountWithdrawn;

 77:     uint128 public totalCostPaid;

 80:     mapping(address recipient => Recipient receipt) public recipients;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L59

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

 16:     address public vault;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L16

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

 19:     address public vault;

 22:     mapping(address addr => uint256 amountClaimed) public claimedAmount;

 25:     mapping(address addr => uint256 amountWithdrawn) public withdrawnAmount;

 28:     uint64 public withdrawalWindow;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L19

```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

 14:     address public vault;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L14

```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

 12:     mapping(bytes32 hash => bool claimed) public isClaimed;

 15:     bytes32 public merkleRoot;

 18:     uint64 public claimStart;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L12

```solidity
File: packages/protocol/contracts/tokenvault/BaseNFTVault.sol

 53:     uint256 public constant MAX_TOKEN_PER_TXN = 10;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L53

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

 16:     address public srcToken;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L16

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

 22:     address public srcToken;

 30:     address public snapshooter;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L22

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

 11:     address public migratingAddress;

 14:     bool public migratingInbound;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L11

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

 14:     address public srcToken;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L14

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

 52:     mapping(address btoken => bool blacklisted) public btokenBlacklist;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L52

```solidity
File: packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

 31:     IUSDC public usdc;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L31

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

 30:     uint64 public constant INSTANCE_EXPIRY = 180 days;

 34:     uint64 public constant INSTANCE_VALIDITY_DELAY = 1 days;

 39:     uint256 public nextInstanceId;

 47:     mapping(uint256 instanceId => Instance instance) public instances;

 55:     mapping(address instanceAddress => bool alreadyAttested) public addressRegistered;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L55


## [GAS-41] Redundant state variable getters
Getters for public state variables are automatically generated so there is no need to code them manually and waste gas.

**Total Instances:** 2

```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

 43:     function getConfig() public view override returns (Config memory) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L43

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

 113:     function decimals()

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L113


## [GAS-42] Duplicated require()/revert() checks should be refactored to a modifier Or function to save gas
Saves deployment costs.

**Total Instances:** 26

```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

 79:         if (_to == address(this)) revert TKO_INVALID_ADDR();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoToken.sol#L79

```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

 38:             revert L1_INVALID_ETH_DEPOSIT();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L38

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

 374:             if (_sameTransition) revert L1_ALREADY_PROVED();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L374

```solidity
File: packages/protocol/contracts/L1/libs/LibUtils.sol

 64:             revert L1_INVALID_BLOCK_ID();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibUtils.sol#L64

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

 131:                 if (blk.blockId != blockId) revert L1_BLOCK_MISMATCH();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L131

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

 82:             if (guardian == address(0)) revert INVALID_GUARDIAN();

 84:             if (guardianIds[guardian] != 0) revert INVALID_GUARDIAN_SET();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L82

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

 120:             revert L2_INVALID_PARAM();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L120

```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

 34:         if (_newConfig.basefeeAdjustmentQuotient == 0) revert L2_INVALID_CONFIG();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L34

```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

 155:         require(der[ptr.ixs()] == 0x02, "Not type INTEGER");

 156:         require(der[ptr.ixf()] & 0x80 == 0, "Not positive");

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L155

```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

 50:             revert("Unsupported algorithm");

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L50

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 132:         if (!destChainEnabled) revert B_INVALID_CHAINID();

 227:         if (messageStatus[msgHash] != Status.NEW) revert B_STATUS_MISMATCH();

 261:                 revert B_PERMISSION_DENIED();

 305:             revert B_INVOCATION_TOO_EARLY();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L132

```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

 59:         if (paused()) revert INVALID_PAUSE_STATUS();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L59

```solidity
File: packages/protocol/contracts/libs/Lib4844.sol

 58:             revert EVAL_FAILED_2();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/Lib4844.sol#L58

```solidity
File: packages/protocol/contracts/libs/LibAddress.sol

 36:         if (!success) revert ETH_TRANSFER_FAILED();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibAddress.sol#L36

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

 172:             if (chainData_ == 0) revert SS_SIGNAL_NOT_FOUND();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L172

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

 124:         if (_costToken == address(0)) revert INVALID_PARAM();

 277:             if (_cliff > 0 && _cliff <= _start) revert INVALID_GRANT();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L124

```solidity
File: packages/protocol/contracts/tokenvault/BaseVault.sol

 65:         if (ctx_.from != msg.sender) revert VAULT_PERMISSION_DENIED();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseVault.sol#L65

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

 78:             if (msg.sender != _account) revert BB_PERMISSION_DENIED();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L78

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

 216:         if (btokenBlacklist[_op.token]) revert VAULT_BTOKEN_BLACKLISTED();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L216

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

 107:             if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L107


## [GAS-43] Same cast is done multiple times
It’s cheaper to do it once, and store the result to a variable. The examples below are the second+ instance of a given cast of the variable

**Total Instances:** 8

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

 64:         blk.proposedAt = uint64(block.timestamp);

 71:         ts.timestamp = uint64(block.timestamp);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L64

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

 359:                 ? uint16(bytes2(svnValueBytes)) / 256

 359:                 ? uint16(bytes2(svnValueBytes)) / 256

 363:                 pcesvn = uint256(svnValue);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L359

```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

 194:             ixLastContentByte = uint80(ixFirstContentByte + length - 1);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L194

```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

 21:             yrs += (uint8(x509Time[0]) - 48) * 1000 + (uint8(x509Time[1]) - 48) * 100;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L21

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

 45:             out_[0] = bytes1(uint8(lenLen) + uint8(_offset) + 55);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L45


## [GAS-46] State variable read in a loop
The state variable should be cached in a local variable rather than reading it on every iteration of the for-loop, which will replace each Gwarmaccess (100 gas) with a much cheaper stack read.

**Total Instances:** 39
**Gas per instance:** 97
**Total Gas saved:** 3783

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

 /// @audit  guardians
 74:         for (uint256 i; i < guardians.length; ++i) {

 /// @audit  guardianIds
 75:             delete guardianIds[guardians[i]];

 /// @audit  guardians
 75:             delete guardianIds[guardians[i]];

 /// @audit  guardians
 87:             guardians.push(guardian);

 /// @audit  guardians
 88:             guardianIds[guardian] = guardians.length;

 /// @audit  minGuardians
 135:                 if (count == minGuardians) return true;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L74

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

 /// @audit  _serialNumIsRevoked
 81:             if (_serialNumIsRevoked[index][serialNumBatch[i]]) {

 /// @audit  _serialNumIsRevoked
 84:             _serialNumIsRevoked[index][serialNumBatch[i]] = true;

 /// @audit  _serialNumIsRevoked
 96:             if (!_serialNumIsRevoked[index][serialNumBatch[i]]) {

 /// @audit  _serialNumIsRevoked
 99:             delete _serialNumIsRevoked[index][serialNumBatch[i]];

 /// @audit  CPUSVN_LENGTH
 240:         for (uint256 i; i < CPUSVN_LENGTH; ++i) {

 /// @audit  _serialNumIsRevoked
 268:                     certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.ROOT)][certs[i]

 /// @audit  _serialNumIsRevoked
 271:                     certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.PCK)][certs[i]

 /// @audit  sigVerifyLib
 285:             verified = sigVerifyLib.verifyES256Signature(

 /// @audit  ROOTCA_PUBKEY_HASH
 294:             if (issuerPubKeyHash == ROOTCA_PUBKEY_HASH) {

 /// @audit  pemCertLib
 424:                 (certDecodedSuccessfully, parsedQuoteCerts[i]) = pemCertLib.decodeCert(

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L81

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

 /// @audit  SGX_EXTENSION_OID
 292:             if (BytesUtils.compareBytes(der.bytesAt(internalPtr), SGX_EXTENSION_OID)) {

 /// @audit  TCB_OID
 306:                     if (BytesUtils.compareBytes(der.bytesAt(extnValueOidPtr), TCB_OID)) {

 /// @audit  TCB_OID
 306:                     if (BytesUtils.compareBytes(der.bytesAt(extnValueOidPtr), TCB_OID)) {

 /// @audit  PCEID_OID
 310:                     if (BytesUtils.compareBytes(der.bytesAt(extnValueOidPtr), PCEID_OID)) {

 /// @audit  PCEID_OID
 310:                     if (BytesUtils.compareBytes(der.bytesAt(extnValueOidPtr), PCEID_OID)) {

 /// @audit  FMSPC_OID
 316:                     if (BytesUtils.compareBytes(der.bytesAt(extnValueOidPtr), FMSPC_OID)) {

 /// @audit  FMSPC_OID
 316:                     if (BytesUtils.compareBytes(der.bytesAt(extnValueOidPtr), FMSPC_OID)) {

 /// @audit  SGX_TCB_CPUSVN_SIZE
 354:         for (uint256 i; i < SGX_TCB_CPUSVN_SIZE + 1; ++i) {

 /// @audit  PCESVN_OID
 361:             if (BytesUtils.compareBytes(der.bytesAt(svnPtr), PCESVN_OID)) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L292

```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

 /// @audit  BASE32_HEX_TABLE
 336:             decoded = uint8(BASE32_HEX_TABLE[uint256(uint8(char)) - 0x30]);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L336

```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

 /// @audit  vault
 60:             IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);

 /// @audit  token
 60:             IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L60

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

 /// @audit  BRANCH_NODE_LENGTH
 111:             if (currentNode.decoded.length == BRANCH_NODE_LENGTH) {

 /// @audit  TREE_RADIX
 118:                     value_ = RLPReader.readBytes(currentNode.decoded[TREE_RADIX]);

 /// @audit  LEAF_OR_EXTENSION_NODE_LENGTH
 139:             } else if (currentNode.decoded.length == LEAF_OR_EXTENSION_NODE_LENGTH) {

 /// @audit  PREFIX_LEAF_EVEN
 155:                 if (prefix == PREFIX_LEAF_EVEN || prefix == PREFIX_LEAF_ODD) {

 /// @audit  PREFIX_LEAF_ODD
 155:                 if (prefix == PREFIX_LEAF_EVEN || prefix == PREFIX_LEAF_ODD) {

 /// @audit  PREFIX_EXTENSION_EVEN
 184:                 } else if (prefix == PREFIX_EXTENSION_EVEN || prefix == PREFIX_EXTENSION_ODD) {

 /// @audit  PREFIX_EXTENSION_ODD
 184:                 } else if (prefix == PREFIX_EXTENSION_EVEN || prefix == PREFIX_EXTENSION_ODD) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L111

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

 /// @audit  instances
 107:             if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();

 /// @audit  instances
 111:             delete instances[idx];

 /// @audit  nextInstanceId
 218:             ids[i] = nextInstanceId;

 /// @audit  nextInstanceId
 222:             nextInstanceId++;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L222


## [GAS-47] State variables only set in the constructor should be declared immutable 
Avoids a Gsset (20000 gas) in the constructor, and replaces the first access in each transaction (Gcoldsload - 2100 gas) and each access thereafter (Gwarmacces - 100 gas) with a PUSH32 (3 gas). While strings are not value types, and therefore cannot be immutable/constant if not hard-coded outside of the constructor, the same behavior can be achieved by making the current contract abstract with virtual functions for the string accessors, and having a child contract override the functions with the hard-coded implementation-specific values.

**Total Instances:** 2
**Gas per instance:** 2097
**Total Gas saved:** 4194

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

 57:         owner = msg.sender;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L57

```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

 21:         ES256VERIFIER = es256Verifier;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L21


## [GAS-48] Use uint256(1)/uint256(2) instead of true/false to save gas for changes
Avoids a Gsset (20000 gas) when changing from false to true, after having been true in the past

**Total Instances:** 10
**Gas per instance:** 8550
**Total Gas saved:** 85500

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

 38:     bool private _checkLocalEnclaveReport;

 39:     mapping(bytes32 enclave => bool trusted) private _trustedUserMrEnclave;

 40:     mapping(bytes32 signer => bool trusted) private _trustedUserMrSigner;

 47:     mapping(uint256 idx => mapping(bytes serialNum => bool revoked)) private _serialNumIsRevoked;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L38

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 42:     mapping(address addr => bool banned) public addressBanned;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L42

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

 21:     mapping(address addr => bool authorized) public isAuthorized;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L21

```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

 12:     mapping(bytes32 hash => bool claimed) public isClaimed;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L12

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

 14:     bool public migratingInbound;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L14

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

 52:     mapping(address btoken => bool blacklisted) public btokenBlacklist;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L52

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

 55:     mapping(address instanceAddress => bool alreadyAttested) public addressRegistered;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L55



## [GAS-50] Unused named return variables without optimizer waste gas
Consider changing the variable to be an unnamed one, since the variable is never assigned, nor is it returned by name. If the optimizer is not turned on, leaving the code as it is will also waste gas for the stack variable.

**Total Instances:** 24
**Gas per instance:** 9
**Total Gas saved:** 216

```solidity
File: packages/protocol/contracts/L1/ITaikoL1.sol

 /// @audit  meta_, deposits_
 20:         returns (TaikoData.BlockMetadata memory meta_, TaikoData.EthDeposit[] memory deposits_);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/ITaikoL1.sol#L20

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

 /// @audit  maxBlocksToVerify_
 100:         returns (uint8 maxBlocksToVerify_)

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L100

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

 /// @audit  valid
 130:         returns (bool valid)

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L130

```solidity
File: packages/protocol/contracts/automata-attestation/interfaces/IAttestation.sol

 /// @audit  success, retData
 12:         returns (bool success, bytes memory retData);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/interfaces/IAttestation.sol#L12

```solidity
File: packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol

 /// @audit  sigValid
 65:         returns (bool sigValid);

 /// @audit  sigValid
 74:         returns (bool sigValid);

 /// @audit  sigValid
 83:         returns (bool sigValid);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L65

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

 /// @audit  success
 219:         returns (bool success, bytes memory extracted, uint256 endIndex)

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L219

```solidity
File: packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol

 /// @audit  success, certs
 42:         returns (bool success, bytes[] memory certs);

 /// @audit  success, cert
 50:         returns (bool success, ECSha256Certificate memory cert);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L42

```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

 /// @audit  ret
 188:     function readUint8(bytes memory self, uint256 idx) internal pure returns (uint8 ret) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L188

```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

 /// @audit  sigValid
 120:         returns (bool sigValid)

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L120

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 /// @audit  invocationDelay_, invocationExtraDelay_
 421:         returns (uint256 invocationDelay_, uint256 invocationExtraDelay_)

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L421

```solidity
File: packages/protocol/contracts/bridge/IBridge.sol

 /// @audit  msgHash_, message_
 112:         returns (bytes32 msgHash_, Message memory message_);

 /// @audit  ctx_
 145:     function context() external view returns (Context memory ctx_);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/IBridge.sol#L112

```solidity
File: packages/protocol/contracts/signal/ISignalService.sol

 /// @audit  slot_
 59:     function sendSignal(bytes32 _signal) external returns (bytes32 slot_);

 /// @audit  slot_
 59:     function sendSignal(bytes32 _signal) external returns (bytes32 slot_);

 /// @audit  signal_
 75:         returns (bytes32 signal_);

 /// @audit  signal_
 75:         returns (bytes32 signal_);

 /// @audit  blockId_, chainData_
 129:         returns (uint64 blockId_, bytes32 chainData_);

 /// @audit  blockId_, chainData_
 129:         returns (uint64 blockId_, bytes32 chainData_);

 /// @audit  signal_
 144:         returns (bytes32 signal_);

 /// @audit  signal_
 144:         returns (bytes32 signal_);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/ISignalService.sol#L59

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

 /// @audit  offset_, length_, type_
 147:         returns (uint256 offset_, uint256 length_, RLPItemType type_)

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L147


## [GAS-51] Remove or replace unused state variables
Saves a storage slot. If the variable is assigned a non-zero value, saves Gsset (20000 gas). If it’s assigned a zero value, saves Gsreset (2900 gas). If the variable remains unassigned, there is no gas savings unless the variable is public, in which case the compiler-generated non-payable getter deployment cost is saved. If the state variable is overriding an interface’s public function, mark the variable as constant or immutable so that it does not use a storage slot. Note that there may be cases where a variable superficially appears to be used, but this is only because there are multiple definitions of the variable in different files. In such cases, the variable definition should be moved into a separate file. The instances below are the unused variables.

**Total Instances:** 28

```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

 26:     uint256[50] private __gap;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L26

```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

 16:     uint256[50] private __gap;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoToken.sol#L16

```solidity
File: packages/protocol/contracts/L1/gov/TaikoGovernor.sol

 23:     uint256[50] private __gap;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L23

```solidity
File: packages/protocol/contracts/L1/gov/TaikoTimelockController.sol

 10:     uint256[50] private __gap;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L10

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

 40:     uint256[50] private __gap;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L40

```solidity
File: packages/protocol/contracts/L1/provers/GuardianProver.sol

 11:     uint256[50] private __gap;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/GuardianProver.sol#L11

```solidity
File: packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol

 11:     uint256[50] private __gap;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L11

```solidity
File: packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol

 11:     uint256[50] private __gap;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L11

```solidity
File: packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol

 11:     uint256[50] private __gap;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L11

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

 52:     uint256[47] private __gap;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L52

```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

 13:     uint256[49] private __gap;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L13

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 23:     bytes32 private constant _CTX_SLOT =

 48:     uint256[43] private __gap;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L23

```solidity
File: packages/protocol/contracts/common/AddressManager.sol

 14:     uint256[49] private __gap;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressManager.sol#L14

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

 23:     uint256[48] private __gap;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L23

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

 82:     uint128[44] private __gap;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L82

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

 18:     uint256[48] private __gap;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L18

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

 30:     uint256[45] private __gap;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L30

```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

 16:     uint256[48] private __gap;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L16

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

 27:     uint256[46] private __gap;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L27

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

 32:     uint256[47] private __gap;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L32

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

 19:     uint256[48] private __gap;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L19

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

 32:     uint256[50] private __gap;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L32

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

 54:     uint256[47] private __gap;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L54

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

 19:     uint256[50] private __gap;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L19

```solidity
File: packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

 32:     uint256[49] private __gap;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L32

```solidity
File: packages/protocol/contracts/verifiers/GuardianVerifier.sol

 11:     uint256[50] private __gap;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L11

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

 57:     uint256[47] private __gap;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L57


## [GAS-52] Use `Array.unsafeAccess` to avoid repeated array length checks
When using storage arrays, solidity adds an internal lookup of the array's length (a Gcoldsload 2100 gas) to ensure it doesn't read past the array's end. It's possible to avoid this lookup by using `Array.unsafeAccess `in cases where the length has already been checked.

**Total Instances:** 77
**Gas per instance:** 2100
**Total Gas saved:** 161700

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

 173:             if (_tierFees[i].tier == _tierId) return _tierFees[i].fee;

 173:             if (_tierFees[i].tier == _tierId) return _tierFees[i].fee;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L173

```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

 88:                 deposits_[i] = TaikoData.EthDeposit({

 93:                 uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount;

 93:                 uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount;

 101:                     deposits_[i].amount -= _fee;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L88

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

 245:                 if (uint160(prevHook) >= uint160(params.hookCalls[i].hook)) {

 253:                 IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }(

 254:                     blk, meta_, params.hookCalls[i].data

 257:                 prevHook = params.hookCalls[i].hook;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L245

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

 75:             delete guardianIds[guardians[i]];

 81:             address guardian = _newGuardians[i];

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L75

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

 81:             if (_serialNumIsRevoked[index][serialNumBatch[i]]) {

 81:             if (_serialNumIsRevoked[index][serialNumBatch[i]]) {

 84:             _serialNumIsRevoked[index][serialNumBatch[i]] = true;

 84:             _serialNumIsRevoked[index][serialNumBatch[i]] = true;

 96:             if (!_serialNumIsRevoked[index][serialNumBatch[i]]) {

 96:             if (!_serialNumIsRevoked[index][serialNumBatch[i]]) {

 99:             delete _serialNumIsRevoked[index][serialNumBatch[i]];

 99:             delete _serialNumIsRevoked[index][serialNumBatch[i]];

 192:             EnclaveIdStruct.TcbLevel memory tcb = enclaveId.tcbLevels[i];

 215:             TCBInfoStruct.TCBLevelObj memory current = tcb.tcbLevels[i];

 241:             if (pckCpuSvns[i] < tcbCpuSvns[i]) {

 241:             if (pckCpuSvns[i] < tcbCpuSvns[i]) {

 263:                 issuer = certs[i];

 268:                     certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.ROOT)][certs[i]

 270:                 } else if (certs[i].isPck) {

 271:                     certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.PCK)][certs[i]

 280:                 block.timestamp > certs[i].notBefore && block.timestamp < certs[i].notAfter;

 280:                 block.timestamp > certs[i].notBefore && block.timestamp < certs[i].notAfter;

 286:                 certs[i].tbsCertificate, certs[i].signature, issuer.pubKey

 286:                 certs[i].tbsCertificate, certs[i].signature, issuer.pubKey

 424:                 (certDecodedSuccessfully, parsedQuoteCerts[i]) = pemCertLib.decodeCert(

 425:                     authDataV3.certification.decodedCertDataArray[i], isPckCert

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L81

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

 62:             (success, certs[i], increment) = _removeHeadersAndFooters(input);

 245:             contentStr = LibString.concat(contentStr, split[i]);

 367:                 cpusvns[i] = cpusvn;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L62

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

 154:             uint256 digits = uint256(uint8(bytes1(encoded[i])));

 282:             quoteCerts[i] = Base64.decode(string(quoteCerts[i]));

 282:             quoteCerts[i] = Base64.decode(string(quoteCerts[i]));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L154

```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

 141:             if (decipher[i] != 0xff) {

 153:                 if (decipher[3 + paddingLen + i] != bytes1(sha256ExplicitNullParam[i])) {

 159:                 if (decipher[3 + paddingLen + i] != bytes1(sha256ImplicitNullParam[i])) {

 175:             if (decipher[5 + paddingLen + digestAlgoWithParamLen + i] != _sha256[i]) {

 274:             if (decipher[i] != 0xff) {

 284:             if (decipher[3 + paddingLen + i] != bytes1(sha1Prefix[i])) {

 291:             if (decipher[3 + paddingLen + sha1Prefix.length + i] != _sha1[i]) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L141

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 91:             bytes32 msgHash = _msgHashes[i];

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L91

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

 105:             hop = hopProofs[i];

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L105

```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

 60:             IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L60

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

 47:                 out_[i] = bytes1(uint8((_len / (256 ** (lenLen - i))) % 256));

 60:             if (b[i] != 0) {

 67:             out_[j] = b[i++];

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L47

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

 86:             TrieNode memory currentNode = proof[i];

 118:                     value_ = RLPReader.readBytes(currentNode.decoded[TREE_RADIX]);

 134:                     uint8 branchKey = uint8(key[currentKeyIndex]);

 135:                     RLPReader.RLPItem memory nextNode = currentNode.decoded[branchKey];

 209:             proof_[i] = TrieNode({ encoded: _proof[i], decoded: RLPReader.readList(_proof[i]) });

 209:             proof_[i] = TrieNode({ encoded: _proof[i], decoded: RLPReader.readList(_proof[i]) });

 209:             proof_[i] = TrieNode({ encoded: _proof[i], decoded: RLPReader.readList(_proof[i]) });

 244:         for (; shared_ < max && _a[shared_] == _b[shared_];) {

 244:         for (; shared_ < max && _a[shared_] == _b[shared_];) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L86

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

 48:             if (_op.amounts[i] == 0) revert VAULT_INVALID_AMOUNT();

 252:                     BridgedERC1155(_op.token).burn(_user, _op.tokenIds[i], _op.amounts[i]);

 252:                     BridgedERC1155(_op.token).burn(_user, _op.tokenIds[i], _op.amounts[i]);

 273:                         id: _op.tokenIds[i],

 274:                         amount: _op.amounts[i],

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L48

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

 35:             if (_op.amounts[i] != 0) revert VAULT_INVALID_AMOUNT();

 171:                 IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);

 176:                 BridgedERC721(token_).mint(_to, _tokenIds[i]);

 198:                     BridgedERC721(_op.token).burn(_user, _op.tokenIds[i]);

 211:                     t.safeTransferFrom(_user, address(this), _op.tokenIds[i]);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L35

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

 105:             uint256 idx = _ids[i];

 107:             if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();

 111:             delete instances[idx];

 217:             instances[nextInstanceId] = Instance(_instances[i], validSince);

 218:             ids[i] = nextInstanceId;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L218


## [GAS-53] Use assembly in place of `abi.decode` to save gas
Instead of using `abi.decode`, we can use assembly to decode our desired calldata values directly. This will allow us to avoid decoding calldata values that we will not use.

**Total Instances:** 16
**Gas per instance:** 18
**Total Gas saved:** 288

```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

 88:         ) = abi.decode(_input, (TaikoData.BlockMetadata, TaikoData.Transition, TaikoData.TierProof));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L88

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

 77:         Input memory input = abi.decode(_data, (Input));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L77

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

 78:         TaikoData.BlockParams memory params = abi.decode(_data, (TaikoData.BlockParams));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L78

```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

 42:         (uint64 txId, bytes memory txdata) = abi.decode(_data, (uint64, bytes));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L42

```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

 140:         return abi.decode(ret, (uint256)) == 1;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L140

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

 94:         HopProof[] memory hopProofs = abi.decode(_proof, (HopProof[]));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L94

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

 70:             abi.decode(delegationData, (address, uint256, uint256, uint8, bytes32, bytes32));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L70

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

 100:         ) = abi.decode(data, (CanonicalNFT, address, address, uint256[], uint256[]));

 140:         (bytes memory data) = abi.decode(message.data[4:], (bytes));

 142:             abi.decode(data, (CanonicalNFT, address, address, uint256[], uint256[]));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L100

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

 260:             abi.decode(_data, (CanonicalERC20, address, address, uint256));

 298:         (bytes memory data) = abi.decode(_message.data[4:], (bytes));

 300:             abi.decode(data, (CanonicalERC20, address, address, uint256));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L260

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

 84:             abi.decode(_data, (CanonicalNFT, address, address, uint256[]));

 123:         (bytes memory data) = abi.decode(_message.data[4:], (bytes));

 125:             abi.decode(data, (CanonicalNFT, address, address, uint256[]));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L125


## [GAS-54] Use assembly to validate `msg.sender`
We can use assembly to efficiently validate msg.sender with the least amount of opcodes necessary. For more details check the following report [Here](https://code4rena.com/reports/2023-05-juicebox#g-06-use-assembly-to-validate-msgsender).

**Total Instances:** 16
**Gas per instance:** 12
**Total Gas saved:** 192

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

 310:             if (proposerOne != address(0) && msg.sender != proposerOne) {

 316:         return proposer == address(0) || msg.sender == proposer;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L310

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

 416:         bool isAssignedPover = msg.sender == _blk.assignedProver;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L416

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

 61:         require(msg.sender == owner, "onlyOwner");

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L61

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 280:                 uint256 gasLimit = msg.sender == _message.destOwner ? gasleft() : _message.gasLimit;

 322:             if (msg.sender != _message.destOwner) revert B_PERMISSION_DENIED();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L280

```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

 42:         if (msg.sender != owner() && msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();

 42:         if (msg.sender != owner() && msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L42

```solidity
File: packages/protocol/contracts/libs/LibAddress.sol

 78:         return msg.sender == tx.origin;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibAddress.sol#L78

```solidity
File: packages/protocol/contracts/tokenvault/BaseVault.sol

 23:         if (msg.sender != resolve("bridge", false)) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseVault.sol#L23

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

 38:         if (msg.sender != owner() && msg.sender != snapshooter) {

 38:         if (msg.sender != owner() && msg.sender != snapshooter) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L38

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

 61:         if (msg.sender == migratingAddress) {

 64:         } else if (msg.sender != resolve("erc20_vault", true)) {

 78:             if (msg.sender != _account) revert BB_PERMISSION_DENIED();

 83:         } else if (msg.sender != resolve("erc20_vault", true)) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L83


## [GAS-55] Using bitmap to store bool states can save gas
Using a bitmap instead of a bool array or a bool mapping to store boolean states can save gas fees. This is because the bitmap can store 256 boolean values in a single slot instead of 256 slots, which can save gas when writing bool values or when reading multiple bool values from the same slot.

**Total Instances:** 8

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

 39:     mapping(bytes32 enclave => bool trusted) private _trustedUserMrEnclave;

 40:     mapping(bytes32 signer => bool trusted) private _trustedUserMrSigner;

 47:     mapping(uint256 idx => mapping(bytes serialNum => bool revoked)) private _serialNumIsRevoked;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L39

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 42:     mapping(address addr => bool banned) public addressBanned;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L42

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

 21:     mapping(address addr => bool authorized) public isAuthorized;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L21

```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

 12:     mapping(bytes32 hash => bool claimed) public isClaimed;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L12

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

 52:     mapping(address btoken => bool blacklisted) public btokenBlacklist;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L52

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

 55:     mapping(address instanceAddress => bool alreadyAttested) public addressRegistered;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L55


## [GAS-56] Use constants instead of type(uintx).max
'it's generally more gas-efficient to use constants instead of type(uintX).max when you need to set the maximum value of an unsigned integer type.'

**Total Instances:** 9

```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

 150:         if (_amount > type(uint96).max) revert L1_INVALID_ETH_DEPOSIT();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L150

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

 260:                 || _config.ethDepositMaxAmount > type(uint96).max || _config.ethDepositGas == 0

 262:                 || _config.ethDepositMaxFee > type(uint96).max / _config.ethDepositMaxCountPerBlock

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L260

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

 63:         if (_newGuardians.length < MIN_NUM_GUARDIANS || _newGuardians.length > type(uint8).max) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L63

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

 82:         if (block.chainid <= 1 || block.chainid > type(uint64).max) {

 284:             gasExcess_ = uint64(excess.min(type(uint64).max));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L82

```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

 91:                     mask = type(uint256).max; // aka 0xffffff....

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L91

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 27:     uint256 internal constant PLACEHOLDER = type(uint256).max;

 89:         uint64 _timestamp = _suspend ? type(uint64).max : uint64(block.timestamp);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L89


## [GAS-57] Using delete instead of setting `info` struct to 0 saves gas
using the delete keyword to clear a struct or state variable, instead of manually setting its fields to 0 or default values, can save gas. This is because delete efficiently frees up the storage slot, reducing gas costs, particularly in cases involving large or complex data structures.

**Total Instances:** 9

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

 190:             meta_.txListByteOffset = 0;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L190

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

 197:                 blk.livenessBond = 0;

 300:             ts_.blockHash = 0;

 301:             ts_.stateRoot = 0;

 302:             ts_.validityBond = 0;

 306:             ts_.tier = 0;

 307:             ts_.contestations = 0;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L197

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

 231:         _grant.grantStart = 0;

 232:         _grant.grantPeriod = 0;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L232


## [GAS-58] Use do while loops instead of for loops
A do while loop will cost less gas since the condition is not being checked for the first iteration.

**Total Instances:** 49

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

 172:         for (uint256 i; i < _tierFees.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L172

```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

 86:             for (uint256 i; i < deposits_.length;) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L86

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

 244:             for (uint256 i; i < params.hookCalls.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L244

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

 74:         for (uint256 i; i < guardians.length; ++i) {

 80:         for (uint256 i = 0; i < _newGuardians.length; ++i) {

 133:             for (uint256 i; i < guardiansLength; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L74

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

 234:             for (uint256 i; i < 255 && _blockId >= i + 1; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L234

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

 80:         for (uint256 i; i < serialNumBatch.length; ++i) {

 95:         for (uint256 i; i < serialNumBatch.length; ++i) {

 191:         for (uint256 i; i < enclaveId.tcbLevels.length; ++i) {

 214:         for (uint256 i; i < tcb.tcbLevels.length; ++i) {

 240:         for (uint256 i; i < CPUSVN_LENGTH; ++i) {

 259:         for (uint256 i; i < n; ++i) {

 420:             for (uint256 i; i < 3; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L80

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

 54:         for (uint256 i; i < size; ++i) {

 244:         for (uint256 i; i < split.length; ++i) {

 354:         for (uint256 i; i < SGX_TCB_CPUSVN_SIZE + 1; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L54

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

 153:         for (uint256 i; i < encoded.length; ++i) {

 281:         for (uint256 i; i < 3; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L153

```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

 80:         for (uint256 idx = 0; idx < shortest; idx += 32) {

 333:         for (uint256 i; i < len; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L80

```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

 140:         for (uint256 i = 2; i < 2 + paddingLen; ++i) {

 152:             for (uint256 i; i < digestAlgoWithParamLen; ++i) {

 158:             for (uint256 i; i < digestAlgoWithParamLen; ++i) {

 174:         for (uint256 i; i < _sha256.length; ++i) {

 273:         for (uint256 i = 2; i < 2 + paddingLen; ++i) {

 283:         for (uint256 i; i < sha1Prefix.length; ++i) {

 290:         for (uint256 i; i < _sha1.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L140

```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

 48:         for (uint16 i = 1970; i < year; ++i) {

 59:         for (uint8 i = 1; i < month; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L48

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 90:         for (uint256 i; i < _msgHashes.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L90

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

 104:         for (uint256 i; i < hopProofs.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L104

```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

 59:         for (uint256 i; i < tokenIds.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

 46:             for (i = 1; i <= lenLen; i++) {

 59:         for (; i < 32; i++) {

 66:         for (uint256 j = 0; j < out_.length; j++) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L46

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

 85:         for (uint256 i = 0; i < proof.length; i++) {

 208:         for (uint256 i = 0; i < length;) {

 244:         for (; shared_ < max && _a[shared_] == _b[shared_];) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

 47:         for (uint256 i; i < _op.amounts.length; ++i) {

 251:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

 269:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L47

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

 34:         for (uint256 i; i < _op.tokenIds.length; ++i) {

 170:             for (uint256 i; i < _tokenIds.length; ++i) {

 175:             for (uint256 i; i < _tokenIds.length; ++i) {

 197:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

 210:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L34

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

 104:         for (uint256 i; i < _ids.length; ++i) {

 210:         for (uint256 i; i < _instances.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210


## [GAS-59] Using globals directly is cheaper than assigning them to variables
Using the global directly saves 5 gas

**Total Instances:** 1
**Gas per instance:** 5
**Total Gas saved:** 5

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

 93:         address taikoL1Address = msg.sender;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L93


## [GAS-60] Using msg globals directly, rather than caching the value, saves gas
use msg.sender directly rather than storing it to a local variable

**Total Instances:** 3

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

 /// @audit  taikoL1Address
 94:         bytes32 hash = hashAssignment(assignment, taikoL1Address, _meta.blobHash);

 /// @audit  taikoL1Address
 102:         tko.transferFrom(_blk.assignedProver, taikoL1Address, _blk.livenessBond);

 /// @audit  taikoL1Address
 126:             taikoL1Address.sendEther(address(this).balance);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L126


## [GAS-61] Use storage instead of memory for structs/arrays
When fetching data from a storage location, assigning the data to a memory variable causes all fields of the struct/array to be read from storage, which incurs a Gcoldsload (2100 gas) for each field of the struct/array. If the fields are read from the new memory variable, they incur an additional MLOAD rather than a cheap stack read. Instead of declaring the variable with the memory keyword, declaring the variable with the storage keyword and caching any fields that need to be re-read in stack variables, will be much cheaper, only incurring the Gcoldsload for the fields actually read. The only time it makes sense to read the whole struct/array into a memory variable, is if the full struct/array is being returned by the function, is being passed to a function that requires memory, or if the array/struct is being read from another memory array/struct.

**Total Instances:** 1
**Gas per instance:** 4200
**Total Gas saved:** 4200

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

 171:             CanonicalERC20 memory ctoken = bridgedToCanonical[btokenOld_];

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L171


## [GAS-63] Use unchecked block for safe subtractions
If it can be confirmed that the subtraction operation will not overflow, using an unchecked block can save gas. For example, require(x <= y); z = y - x; can be optimized to require(x <= y); unchecked { z = y - x; }.

**Total Instances:** 10
**Gas per instance:** 85
**Total Gas saved:** 850

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

 /// @audit  checked on line 381
 382:                 _tko.transfer(msg.sender, reward - _tier.validityBond);

 /// @audit  checked on line 381
 384:                 _tko.transferFrom(msg.sender, address(this), _tier.validityBond - reward);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L382

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

 /// @audit  checked on line 275
 276:                 numL1Blocks = _l1BlockId - lastSyncedBlock;

 /// @audit  checked on line 281
 281:                 excess = excess > issuance ? excess - issuance : 1;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L276

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

 /// @audit  checked on line 262
 265:         uint256 lengthDiff = n - expectedLength;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L265

```solidity
File: packages/protocol/contracts/thirdparty/optimism/Bytes.sol

 /// @audit  checked on line 92
 95:         return slice(_bytes, _start, _bytes.length - _start);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L95

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

 /// @audit  checked on line 74
 77:                     length: _in.length - offset,

 /// @audit  checked on line 166
 190:             uint256 lenOfStrLen = prefix - 0xb7;

 /// @audit  checked on line 223
 236:             uint256 lenOfListLen = prefix - 0xf7;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L77

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

 /// @audit  checked on line 59
 65:         out_ = new bytes(32 - i);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L65


## [GAS-64] `internal` functions not called by the contract should be removed
If the functions are required by an interface, the contract should inherit from that interface and use the `override` keyword

**Total Instances:** 31

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

 111:     function approve(uint256 _operationId, bytes32 _hash) internal returns (bool approved_) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L111

```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

 14:     function ixs(uint256 self) internal pure returns (uint256) {

 19:     function ixf(uint256 self) internal pure returns (uint256) {

 24:     function ixl(uint256 self) internal pure returns (uint256) {

 47:     function root(bytes memory der) internal pure returns (uint256) {

 56:     function rootOfBitStringAt(bytes memory der, uint256 ptr) internal pure returns (uint256) {

 66:     function rootOfOctetStringAt(bytes memory der, uint256 ptr) internal pure returns (uint256) {

 77:     function nextSiblingOf(bytes memory der, uint256 ptr) internal pure returns (uint256) {

 87:     function firstChildOf(bytes memory der, uint256 ptr) internal pure returns (uint256) {

 98:     function isChildOf(uint256 i, uint256 j) internal pure returns (bool) {

 111:     function bytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes memory) {

 121:     function allBytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes memory) {

 131:     function bytes32At(bytes memory der, uint256 ptr) internal pure returns (bytes32) {

 141:     function uintAt(bytes memory der, uint256 ptr) internal pure returns (uint256) {

 154:     function uintBytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes memory) {

 165:     function keccakOfBytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes32) {

 169:     function keccakOfAllBytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes32) {

 179:     function bitstringAt(bytes memory der, uint256 ptr) internal pure returns (bytes memory) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L14

```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

 188:     function readUint8(bytes memory self, uint256 idx) internal pure returns (uint8 ret) {

 198:     function readUint16(bytes memory self, uint256 idx) internal pure returns (uint16 ret) {

 211:     function readUint32(bytes memory self, uint256 idx) internal pure returns (uint32 ret) {

 224:     function readBytes32(bytes memory self, uint256 idx) internal pure returns (bytes32 ret) {

 237:     function readBytes20(bytes memory self, uint256 idx) internal pure returns (bytes20 ret) {

 255:     function readBytesN(

 284:     function substring(

 320:     function base32HexDecodeWord(

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L188

```solidity
File: packages/protocol/contracts/libs/Lib4844.sol

 30:     function evaluatePoint(

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/Lib4844.sol#L30

```solidity
File: packages/protocol/contracts/libs/LibAddress.sol

 46:     function supportsInterface(

 61:     function isValidSignature(

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibAddress.sol#L46

```solidity
File: packages/protocol/contracts/libs/LibMath.sol

 12:     function min(uint256 _a, uint256 _b) internal pure returns (uint256) {

 20:     function max(uint256 _a, uint256 _b) internal pure returns (uint256) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibMath.sol#L20


## [GAS-65] Use assembly to write address/contract type storage values
Using `assembly { sstore(state.slot, addr) instead of state = addr` can save gas.

**Total Instances:** 16
**Gas per instance:** 50
**Total Gas saved:** 800

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

 57:         owner = msg.sender;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L57

```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

 21:         ES256VERIFIER = es256Verifier;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L21

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

 122:         taikoToken = _taikoToken;

 125:         costToken = _costToken;

 128:         sharedVault = _sharedVault;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L122

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

 41:         token = _token;

 42:         vault = _vault;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L41

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

 69:         token = _token;

 70:         vault = _vault;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L69

```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

 39:         token = _token;

 40:         vault = _vault;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L39

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

 56:         srcToken = _srcToken;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L56

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

 73:         srcToken = _srcToken;

 81:         snapshooter = _snapshooter;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L73

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

 49:         migratingAddress = _migratingAddress;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L49

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

 47:         srcToken = _srcToken;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L47


## [GAS-66] Use assembly to emit events
To efficiently emit events, it’s possible to utilize assembly by making use of [scratch space](https://github.com/Vectorized/solady/blob/30558f5402f02351b96eeb6eaf32bcea29773841/src/tokens/ERC1155.sol#L501-L504) in order to save gas. This approach has the advantage of potentially avoiding the costs associated with memory expansion. However, it’s important to note that in order to safely optimize this process, it is preferable to cache and restore the free memory pointer.

**Total Instances:** 23
**Gas per instance:** 38
**Total Gas saved:** 874

```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

 50:         emit EthDeposited(

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L50

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

 166:                     emit BlobCached(meta_.blobHash);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L166

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

 80:         emit ProvingPaused(_pause);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L80

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

 95:         emit GuardiansUpdated(version, _newGuardians);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L95

```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

 53:         emit TransactionExecuted(nextTxId++, bytes4(txdata));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L53

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

 157:         emit Anchored(blockhash(parentId), gasExcess);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L157

```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

 39:         emit ConfigAndExcessChanged(_newConfig, _newGasExcess);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L39

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 93:             emit MessageSuspended(msgHash, _suspend);

 111:         emit AddressBanned(_addr, _ban);

 151:         emit MessageSent(msgHash_, message_);

 208:             emit MessageRecalled(msgHash);

 301:             emit MessageExecuted(msgHash);

 336:         emit MessageRetried(msgHash);

 519:         emit MessageStatusChanged(_msgHash, _status);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L93

```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

 71:         emit Paused(msg.sender);

 80:         emit Unpaused(msg.sender);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L71

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

 59:         emit Authorized(_addr, _authorize);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L59

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

 143:         emit Granted(_recipient, _grant);

 157:         emit Voided(_recipient, amountVoided);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L143

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

 93:         emit Withdrawn(user, amount);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L93

```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

 74:         emit Claimed(hash);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L74

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

 51:         emit MigrationStatusChanged(_migratingAddress, _migratingInbound);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L51

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

 109:             emit InstanceDeleted(idx, instances[idx].addr);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L109


## [GAS-67] Use assembly to compute hashes to save gas
If the arguments to the encode call can fit into the scratch space (two words or fewer), then it’s more efficient to use assembly to generate the hash (80 gas): keccak256(abi.encodePacked(x, y)) -> assembly {mstore(0x00, a); mstore(0x20, b); let hash := keccak256(0x00, 0x40); }

**Total Instances:** 18
**Gas per instance:** 80
**Total Gas saved:** 1440

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

 126:                 depositsHash: keccak256(abi.encode(deposits_)),

 189:             meta_.blobHash = keccak256(_txList);

 213:             metaHash: keccak256(abi.encode(meta_)),

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L126

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

 20:     bytes32 public constant RETURN_LIVENESS_BOND = keccak256("RETURN_LIVENESS_BOND");

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L20

```solidity
File: packages/protocol/contracts/L1/provers/GuardianProver.sol

 46:         bytes32 hash = keccak256(abi.encode(_meta, _tran));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/GuardianProver.sol#L46

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

 292:             bytes32 issuerPubKeyHash = keccak256(issuer.pubKey);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L292

```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

 372:         return keccak256(a) == keccak256(b);

 372:         return keccak256(a) == keccak256(b);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L372

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 450:         return keccak256(abi.encode("TAIKO_MESSAGE", _message));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L450

```solidity
File: packages/protocol/contracts/signal/LibSignals.sol

 8:     bytes32 public constant STATE_ROOT = keccak256("STATE_ROOT");

 11:     bytes32 public constant SIGNAL_ROOT = keccak256("SIGNAL_ROOT");

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/LibSignals.sol#L8

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

 170:         bytes32 hash = keccak256(abi.encodePacked("Withdraw unlocked Taiko token to: ", _to));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L170

```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

 68:         bytes32 hash = keccak256(abi.encode("CLAIM_TAIKO_AIRDROP", data));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L68

```solidity
File: packages/protocol/contracts/thirdparty/optimism/Bytes.sol

 150:         return keccak256(_bytes) == keccak256(_other);

 150:         return keccak256(_bytes) == keccak256(_other);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L150

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

 94:                     Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),

 100:                     Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L94

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol

 55:         hash_ = abi.encodePacked(keccak256(_key));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L55


## [GAS-68] Using assembly to check for zero can save gas
Using assembly to check for zero can save gas by allowing more direct access to the evm and reducing some of the overhead associated with high-level operations in solidity.

**Total Instances:** 114
**Gas per instance:** 6
**Total Gas saved:** 684

```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

 153:         if (blk_.verifiedTransitionId != 0) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L153

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

 109:         if (assignment.feeToken == address(0)) {

 120:         if (input.tip != 0 && block.coinbase != address(0)) {

 120:         if (input.tip != 0 && block.coinbase != address(0)) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L109

```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

 44:         address recipient_ = _recipient == address(0) ? msg.sender : _recipient;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L44

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

 81:         if (params.assignedProver == address(0)) {

 85:         if (params.coinbase == address(0)) {

 108:         if (params.parentMetaHash != 0 && parentMetaHash != params.parentMetaHash) {

 135:                 blobUsed: _txList.length == 0,

 144:             if (params.blobHash != 0) {

 159:                 if (meta_.blobHash == 0) revert L1_BLOB_NOT_FOUND();

 185:             if (params.txListByteOffset != 0) {

 195:         if (meta_.txListByteSize == 0 || meta_.txListByteSize > _config.blockMaxTxListBytes) {

 260:             if (address(this).balance != 0) {

 310:             if (proposerOne != address(0) && msg.sender != proposerOne) {

 316:         return proposer == address(0) || msg.sender == proposer;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L81

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

 105:         if (_tran.parentHash == 0 || _tran.blockHash == 0 || _tran.stateRoot == 0) {

 163:             if (verifier != address(0)) {

 164:                 bool isContesting = _proof.tier == ts.tier && tier.contestBond != 0;

 186:         bool isTopTier = tier.contestBond == 0;

 223:                 assert(tier.validityBond == 0);

 224:                 assert(ts.validityBond == 0 && ts.contestBond == 0 && ts.contester == address(0));

 239:                 if (ts.contester != address(0)) revert L1_ALREADY_CONTESTED();

 280:         if (tid_ == 0) {

 363:         if (_ts.contester != address(0)) {

 412:         if (_tier.contestBond == 0) return;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L105

```solidity
File: packages/protocol/contracts/L1/libs/LibUtils.sol

 43:         if (tid == 0) revert L1_TRANSITION_NOT_FOUND();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibUtils.sol#L43

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

 93:         if (_maxBlocksToVerify == 0) {

 111:         if (tid == 0) revert L1_TRANSITION_ID_ZERO();

 137:                 if (tid == 0) break;

 145:                 if (ts.contester != address(0)) {

 148:                     if (tierProvider == address(0)) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L93

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

 113:         if (id == 0) revert INVALID_GUARDIAN();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L113

```solidity
File: packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol

 68:         if (_rand % 1000 == 0) return LibTiers.TIER_SGX_ZKVM;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L68

```solidity
File: packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol

 68:         if (_rand % 10 == 0) return LibTiers.TIER_SGX;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L68

```solidity
File: packages/protocol/contracts/L2/Lib1559Math.sol

 24:         if (_adjustmentFactor == 0) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/Lib1559Math.sol#L24

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

 172:         if (_to == address(0)) revert L2_INVALID_PARAM();

 173:         if (_token == address(0)) {

 296:         if (basefee_ == 0) basefee_ = 1;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L172

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

 421:                 bool isPckCert = i == 0; // additional parsing for PCKCert

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L421

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

 286:         while (tbsPtr != 0) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L286

```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

 143:         require(der[ptr.ixf()] & 0x80 == 0, "Not positive");

 156:         require(der[ptr.ixf()] & 0x80 == 0, "Not positive");

 158:         if (der[ptr.ixf()] == 0) {

 191:         if ((der[ix + 1] & 0x80) == 0) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L143

```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

 96:                 if (diff != 0) {

 345:         if (len % 8 == 0) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L96

```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

 137:         if (decipher[0] != 0 || decipher[1] != 0x01) {

 145:         if (decipher[2 + paddingLen] != 0) {

 270:         if (decipher[0] != 0 || decipher[1] != 0x01) {

 278:         if (decipher[2 + paddingLen] != 0) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L137

```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

 72:         if (year % 4 != 0) return false;

 73:         if (year % 100 != 0) return true;

 74:         if (year % 400 != 0) return false;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L72

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 124:         if (_message.srcOwner == address(0) || _message.destOwner == address(0)) {

 124:         if (_message.srcOwner == address(0) || _message.destOwner == address(0)) {

 169:         bool isMessageProven = receivedAt != 0;

 231:         bool isMessageProven = receivedAt != 0;

 245:                     preferredExecutor: _message.gasLimit == 0 ? _message.destOwner : msg.sender

 291:                 _message.refundTo == address(0) ? _message.destOwner : _message.refundTo;

 321:         if (_message.gasLimit == 0 || _isLastAttempt) {

 398:         enabled_ = destBridge_ != address(0);

 405:         if (ctx_.msgHash == 0 || ctx_.msgHash == bytes32(PLACEHOLDER)) {

 485:         if (_gasLimit == 0) revert B_INVALID_GAS_LIMIT();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L124

```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

 105:         if (_addressManager == address(0)) revert ZERO_ADDR_MANAGER();

 110:         _transferOwnership(_owner == address(0) ? msg.sender : _owner);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L105

```solidity
File: packages/protocol/contracts/libs/LibAddress.sol

 24:         if (_to == address(0)) revert ETH_TRANSFER_FAILED();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibAddress.sol#L24

```solidity
File: packages/protocol/contracts/libs/LibTrieProof.sol

 46:         if (_accountProof.length != 0) {

 50:             if (rlpAccount.length == 0) revert LTP_INVALID_ACCOUNT_PROOF();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibTrieProof.sol#L46

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

 36:         if (_app == address(0)) revert SS_INVALID_SENDER();

 41:         if (_input == 0) revert SS_INVALID_VALUE();

 95:         if (hopProofs.length == 0) revert SS_EMPTY_PROOF();

 114:                 if (hop.chainId == 0 || hop.chainId == block.chainid) {

 131:         if (value == 0 || value != _loadSignalValue(address(this), signal)) {

 154:         return _loadSignalValue(_app, _signal) != 0;

 167:         blockId_ = _blockId != 0 ? _blockId : topBlockId[_chainId][_kind];

 169:         if (blockId_ != 0) {

 172:             if (chainData_ == 0) revert SS_SIGNAL_NOT_FOUND();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L36

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

 169:         if (_to == address(0)) revert INVALID_PARAM();

 255:         if (_amount == 0) return 0;

 256:         if (_start == 0) return _amount;

 259:         if (_period == 0) return _amount;

 268:         if (_grant.amount == 0) revert INVALID_GRANT();

 274:         if (_start == 0 || _period == 0) {

 274:         if (_start == 0 || _period == 0) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L169

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

 111:         if (balance == 0) return (0, 0);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L111

```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

 35:             merkleRoot == 0x0 || claimStart == 0 || claimEnd == 0 || claimStart > block.timestamp

 35:             merkleRoot == 0x0 || claimStart == 0 || claimEnd == 0 || claimStart > block.timestamp

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L35

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

 287:         if (_length == 0) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L287

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

 39:             while (_len / i != 0) {

 60:             if (b[i] != 0) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L39

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

 91:             if (currentKeyIndex == 0) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L91

```solidity
File: packages/protocol/contracts/tokenvault/BaseNFTVault.sol

 149:         if (_op.token == address(0)) revert VAULT_INVALID_TOKEN();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L149

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

 102:         return migratingAddress != address(0) && !migratingInbound;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L102

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

 48:             if (_op.amounts[i] == 0) revert VAULT_INVALID_AMOUNT();

 64:             destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,

 108:         if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

 249:             if (bridgedToCanonical[_op.token].addr != address(0)) {

 293:         if (btoken_ == address(0)) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L48

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

 214:         if (_op.amount == 0) revert VAULT_INVALID_AMOUNT();

 215:         if (_op.token == address(0)) revert VAULT_INVALID_TOKEN();

 227:             destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,

 267:         if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

 358:         if (bridgedToCanonical[_token].addr != address(0)) {

 397:         if (btoken == address(0)) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L214

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

 35:             if (_op.amounts[i] != 0) revert VAULT_INVALID_AMOUNT();

 50:             destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,

 91:         if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

 195:             if (bridgedToCanonical[_op.token].addr != address(0)) {

 230:         if (btoken_ == address(0)) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L35

```solidity
File: packages/protocol/contracts/tokenvault/LibBridgedToken.sol

 22:                 || bytes(_symbol).length == 0 || bytes(_name).length == 0

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L22

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

 107:             if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();

 124:         if (automataDcapAttestation == address(0)) {

 234:         if (instance == address(0)) return false;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L234


## [GAS-69] Amounts should be checked for 0 before calling a transfer
It is generally a good practice to check for zero values before making any transfers in smart contract functions. This can help to avoid unnecessary external calls and can save gas costs. Checking for zero values is especially important when transferring tokens or ether, as sending these assets to an address with a zero value will result in the loss of those assets.

**Total Instances:** 18

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

 114:             IERC20(assignment.feeToken).safeTransferFrom(

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L114

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

 367:                 _tko.transfer(_ts.prover, _ts.validityBond + reward);

 371:                 _tko.transfer(_ts.contester, _ts.contestBond + reward);

 382:                 _tko.transfer(msg.sender, reward - _tier.validityBond);

 384:                 _tko.transferFrom(msg.sender, address(this), _tier.validityBond - reward);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L367

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

 189:                 tko.transfer(ts.prover, bondToReturn);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L189

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

 176:             IERC20(_token).safeTransfer(_to, IERC20(_token).balanceOf(address(this)));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L176

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

 219:         IERC20(taikoToken).transferFrom(sharedVault, _to, amountToWithdraw);

 220:         IERC20(costToken).safeTransferFrom(_recipient, sharedVault, costToWithdraw);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L219

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

 63:         IERC20(token).transferFrom(vault, user, amount);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L63

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

 91:         IERC20(token).transferFrom(vault, user, amount);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L91

```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

 60:             IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L60

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

 270:                     IERC1155(_op.token).safeTransferFrom({

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L270

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

 330:             IERC20(token_).safeTransfer(_to, _amount);

 379:             t.safeTransferFrom({ from: msg.sender, to: address(this), value: _amount });

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L330

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

 171:                 IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);

 211:                     t.safeTransferFrom(_user, address(this), _op.tokenIds[i]);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L171

```solidity
File: packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

 48:         usdc.transferFrom(_from, address(this), _amount);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L48

