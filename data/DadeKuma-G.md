## Summary

---

### Gas Optimizations
|Id|Title|Instances|Gas Saved|
|:--:|:------|:--:|---:|
|[[G-01]](#g-01-use-arrayunsafeaccess-to-avoid-repeated-array-length-checks)| Use `Array.unsafeAccess` to avoid repeated array length checks | 80 | 168,000 |
|[[G-02]](#g-02-state-variables-can-be-packed-into-fewer-storage-slots)| State variables can be packed into fewer storage slots | 2 | 40,000 |
|[[G-03]](#g-03-structs-can-be-packed-into-fewer-storage-slots)| Structs can be packed into fewer storage slots | 3 | 60,000 |
|[[G-04]](#g-04-multiple-mappings-that-share-an-id-can-be-combined-into-a-single-mapping-of-id--struct)| Multiple `mapping`s that share an ID can be combined into a single `mapping` of ID / `struct` | 1 | 20,084 |
|[[G-05]](#g-05-use-of-memory-instead-of-storage-for-structarray-state-variables)| Use of `memory` instead of `storage` for struct/array state variables | 2 | 12,600 |
|[[G-06]](#g-06-state-variables-access-within-a-loop)| State variables access within a loop | 4 | 1,060 |
|[[G-07]](#g-07-unused-non-constant-state-variables-waste-gas)| Unused non-constant state variables waste gas | 2 | - |
|[[G-08]](#g-08-state-variables-only-set-in-the-constructor-should-be-declared-immutable)| State variables only set in the constructor should be declared `immutable` | 2 | 40,000 |
|[[G-09]](#g-09-cache-state-variables-with-stack-variables)| Cache state variables with stack variables | 17 | 4,400 |
|[[G-10]](#g-10-modifiers-order-should-be-changed)| Modifiers order should be changed | 5 | - |
|[[G-11]](#g-11-low-level-call-can-be-optimized-with-assembly)| Low level `call` can be optimized with assembly | 1 | 248 |
|[[G-12]](#g-12-use-of-memory-instead-of-calldata-for-immutable-arguments)| Use of `memory` instead of `calldata` for immutable arguments | 116 | 41,658 |
|[[G-13]](#g-13-avoid-updating-storage-when-the-value-hasnt-changed)| Avoid updating storage when the value hasn't changed | 12 | 8,400 |
|[[G-14]](#g-14-use-of-emit-inside-a-loop)| Use of `emit` inside a loop | 4 | 4,104 |
|[[G-15]](#g-15-use-uint2561uint2562-instead-of-truefalse-to-save-gas-for-changes)| Use `uint256(1)/uint256(2)` instead of `true/false` to save gas for changes | 10 | 170,000 |
|[[G-16]](#g-16-shortcircuit-rules-can-be-be-used-to-optimize-some-gas-usage)| Shortcircuit rules can be be used to optimize some gas usage | 1 | 2,100 |
|[[G-17]](#g-17-cache-multiple-accesses-of-a-mappingarray)| Cache multiple accesses of a mapping/array | 13 | 672 |
|[[G-18]](#g-18-redundant-state-variable-getters)| Redundant state variable getters | 2 | - |
|[[G-19]](#g-19-using-private-for-constants-saves-gas)| Using `private` for constants saves gas | 14 | 117,684 |
|[[G-20]](#g-20-require-or-revert-statements-that-check-input-arguments-should-be-at-the-top-of-the-function)| require() or revert() statements that check input arguments should be at the top of the function | 4 | - |
|[[G-21]](#g-21-consider-activating-via-ir-for-deploying)| Consider activating `via-ir` for deploying | - | - |
|[[G-22]](#g-22-function-calls-should-be-cached-instead-of-re-calling-the-function)| Function calls should be cached instead of re-calling the function | 12 | - |
|[[G-23]](#g-23-functions-that-revert-when-called-by-normal-users-can-be-payable)| Functions that revert when called by normal users can be `payable` | 37 | 777 |
|[[G-24]](#g-24-caching-global-variables-is-more-expensive-than-using-the-actual-variable)| Caching global variables is more expensive than using the actual variable | 1 | 12 |
|[[G-25]](#g-25-add-unchecked-blocks-for-subtractions-where-the-operands-cannot-underflow)| Add `unchecked` blocks for subtractions where the operands cannot underflow | 7 | 595 |
|[[G-26]](#g-26-add-unchecked-blocks-for-divisions-where-the-operands-cannot-overflow)| Add `unchecked` blocks for divisions where the operands cannot overflow | 13 | 2,067 |
|[[G-27]](#g-27-empty-blocks-should-be-removed-or-emit-something)| Empty blocks should be removed or emit something | 1 | 4,006 |
|[[G-28]](#g-28-usage-of-uintsints-smaller-than-32-bytes-256-bits-incurs-overhead)| Usage of `uints`/`ints` smaller than 32 bytes (256 bits) incurs overhead | 322 | 1,932 |
|[[G-29]](#g-29-stack-variable-cost-less-while-used-in-emitting-event)| Stack variable cost less while used in emitting event | 7 | 63 |
|[[G-30]](#g-30-redundant-event-fields-can-be-removed)| Redundant `event` fields can be removed | 1 | 358 |
|[[G-31]](#g-31-using-pre-instead-of-post-incrementsdecrements)| Using pre instead of post increments/decrements | 7 | 5 |
|[[G-32]](#g-32--costs-less-gas-than)| `>=`/`<=` costs less gas than `>`/`<` | 130 | 390 |
|[[G-33]](#g-33-internal-functions-only-called-once-can-be-inlined-to-save-gas)| `internal` functions only called once can be inlined to save gas | 20 | 400 |
|[[G-34]](#g-34-inline-modifiers-that-are-only-used-once-to-save-gas)| Inline `modifiers` that are only used once, to save gas | 5 | - |
|[[G-35]](#g-35-private-functions-only-called-once-can-be-inlined-to-save-gas)| `private` functions only called once can be inlined to save gas | 41 | 820 |
|[[G-36]](#g-36-use-multiple-revert-checks-to-save-gas)| Use multiple revert checks to save gas | 37 | 74 |
|[[G-37]](#g-37-abiencode-is-less-efficient-than-abiencodepacked-for-non-address-arguments)| `abi.encode()` is less efficient than `abi.encodepacked()` for non-address arguments | 16 | 80 |
|[[G-38]](#g-38-unused-named-return-variables-without-optimizer-waste-gas)| Unused named return variables without optimizer waste gas | 20 | 54 |
|[[G-39]](#g-39-consider-pre-calculating-the-address-of-addressthis-to-save-gas)| Consider pre-calculating the address of `address(this)` to save gas | 40 | - |
|[[G-40]](#g-40-consider-using-soladys-fixedpointmathlib)| Consider using Solady's `FixedPointMathLib` | 4 | - |
|[[G-41]](#g-41-reduce-deployment-costs-by-tweaking-contracts-metadata)| Reduce deployment costs by tweaking contracts' metadata | 86 | - |
|[[G-42]](#g-42-emitting-constants-wastes-gas)| Emitting constants wastes gas | 4 | 32 |
|[[G-43]](#g-43-update-openzeppelin-dependency-to-save-gas)| Update OpenZeppelin dependency to save gas | 54 | - |
|[[G-44]](#g-44-function-names-can-be-optimized)| Function names can be optimized | 56 | 1,232 |
|[[G-45]](#g-45-avoid-zero-transfers-calls)| Avoid zero transfers calls | 10 | - |
|[[G-46]](#g-46-using-delete-instead-of-setting-mappingstruct-to-0-saves-gas)| Using `delete` instead of setting mapping/struct to 0 saves gas | 10 | 50 |
|[[G-47]](#g-47-using-bool-for-storage-incurs-overhead)| Using `bool` for storage incurs overhead | 10 | 1,000 |
|[[G-48]](#g-48-mappings-are-cheaper-to-use-than-storage-arrays)| Mappings are cheaper to use than storage arrays | 36 | 75,600 |
|[[G-49]](#g-49-bytes-constants-are-more-efficient-than-string-constants)| Bytes constants are more efficient than string constants | 5 | 1,890 |
|[[G-50]](#g-50-constructors-can-be-marked-payable)| Constructors can be marked `payable` | 3 | 63 |
|[[G-51]](#g-51-inverting-the-if-condition-wastes-gas)| Inverting the `if` condition wastes gas | 2 | 6 |
|[[G-52]](#g-52-long-revert-strings)| Long revert strings | 27 | 720 |
|[[G-53]](#g-53-nesting-if-statements-that-use--saves-gas)| Nesting `if` statements that use `&&` saves gas | 23 | 690 |
|[[G-54]](#g-54-counting-down-when-iterating-saves-gas)| Counting down when iterating, saves gas | 45 | 270 |
|[[G-55]](#g-55-do-while-is-cheaper-than-for-loops-when-the-initial-check-can-be-skipped)| `do-while` is cheaper than `for`-loops when the initial check can be skipped | 49 | - |
|[[G-56]](#g-56-lack-of-unchecked-in-loops)| Lack of `unchecked` in loops | 39 | 2,340 |
|[[G-57]](#g-57-uint-comparison-with-zero-can-be-cheaper)| `uint` comparison with zero can be cheaper | 15 | 60 |
|[[G-58]](#g-58-use-assembly-to-check-for-address0)| Use assembly to check for `address(0)` | 74 | 444 |
|[[G-59]](#g-59-use-scratch-space-for-building-calldata-with-assembly)| Use scratch space for building calldata with assembly | 333 | 73,260 |
|[[G-60]](#g-60-use-assembly-to-write-hashes)| Use assembly to write hashes | 25 | 3,000 |
|[[G-61]](#g-61-use-assembly-to-validate-msgsender)| Use assembly to validate `msg.sender` | 17 | 204 |
|[[G-62]](#g-62-use-assembly-to-write-address-storage-values)| Use assembly to write `address` storage values | 18 | 1,332 |
|[[G-63]](#g-63-use-assembly-to-emit-an-event)| Use assembly to emit an `event` | 55 | 2,090 |

Total: 2012 instances over 63 issues with an estimate of **866,926 gas** saved.

---

## Gas Optimizations

---

### [G-01] Use `Array.unsafeAccess` to avoid repeated array length checks

When using storage arrays, solidity adds an internal lookup of the array's length (a **Gcoldsload 2100 gas**) to ensure it doesn't read past the array's end.

It's possible to avoid this lookup by using `Array.unsafeAccess` in cases where the length has already been checked.

*There are 80 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

81: 		            if (_serialNumIsRevoked[index][serialNumBatch[i]]) {

84: 		            _serialNumIsRevoked[index][serialNumBatch[i]] = true;

96: 		            if (!_serialNumIsRevoked[index][serialNumBatch[i]]) {

99: 		            delete _serialNumIsRevoked[index][serialNumBatch[i]];

192: 		            EnclaveIdStruct.TcbLevel memory tcb = enclaveId.tcbLevels[i];

215: 		            TCBInfoStruct.TCBLevelObj memory current = tcb.tcbLevels[i];

241: 		            if (pckCpuSvns[i] < tcbCpuSvns[i]) {

263: 		                issuer = certs[i];

265: 		                issuer = certs[i + 1];

268: 		                    certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.ROOT)][certs[i]
269: 		                        .serialNumber];

270: 		                } else if (certs[i].isPck) {

271: 		                    certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.PCK)][certs[i]
272: 		                        .serialNumber];

280: 		                block.timestamp > certs[i].notBefore && block.timestamp < certs[i].notAfter;

286: 		                certs[i].tbsCertificate, certs[i].signature, issuer.pubKey

424: 		                (certDecodedSuccessfully, parsedQuoteCerts[i]) = pemCertLib.decodeCert(

425: 		                    authDataV3.certification.decodedCertDataArray[i], isPckCert
```
[[81](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L81), [84](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L84), [96](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L96), [99](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L99), [192](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L192), [215](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L215), [241](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L241), [263](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L263), [265](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L265), [268-269](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L268-L269), [270](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L270), [271-272](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L271-L272), [280](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L280), [286](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L286), [424](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L424), [425](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L425)]



```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

91: 		            bytes32 msgHash = _msgHashes[i];

92: 		            proofReceipt[msgHash].receivedAt = _timestamp;
```
[[91](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L91), [92](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L92)]



```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

236: 		                inputs[j % 255] = blockhash(j);
```
[[236](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L236)]



```solidity
File: packages/protocol/contracts/signal/SignalService.sol

105: 		            hop = hopProofs[i];
```
[[105](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L105)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

48: 		            if (_op.amounts[i] == 0) revert VAULT_INVALID_AMOUNT();

252: 		                    BridgedERC1155(_op.token).burn(_user, _op.tokenIds[i], _op.amounts[i]);

273: 		                        id: _op.tokenIds[i],

274: 		                        amount: _op.amounts[i],
```
[[48](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L48), [252](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L252), [273](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L273), [274](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L274)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

35: 		            if (_op.amounts[i] != 0) revert VAULT_INVALID_AMOUNT();

171: 		                IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);

176: 		                BridgedERC721(token_).mint(_to, _tokenIds[i]);

198: 		                    BridgedERC721(_op.token).burn(_user, _op.tokenIds[i]);

211: 		                    t.safeTransferFrom(_user, address(this), _op.tokenIds[i]);
```
[[35](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L35), [171](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L171), [176](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L176), [198](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L198), [211](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L211)]



```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

105: 		            uint256 idx = _ids[i];

107: 		            if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();

109: 		            emit InstanceDeleted(idx, instances[idx].addr);

111: 		            delete instances[idx];

211: 		            if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();

213: 		            addressRegistered[_instances[i]] = true;

215: 		            if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();

217: 		            instances[nextInstanceId] = Instance(_instances[i], validSince);

218: 		            ids[i] = nextInstanceId;

220: 		            emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);
```
[[105](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L105), [107](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L107), [109](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L109), [111](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L111), [211](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L211), [213](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L213), [215](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L215), [217](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L217), [218](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L218), [220](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

62: 		            (success, certs[i], increment) = _removeHeadersAndFooters(input);

245: 		            contentStr = LibString.concat(contentStr, split[i]);

367: 		                cpusvns[i] = cpusvn;
```
[[62](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L62), [245](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L245), [367](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L367)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

334: 		            bytes1 char = self[off + i];

336: 		            decoded = uint8(BASE32_HEX_TABLE[uint256(uint8(char)) - 0x30]);
```
[[334](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L334), [336](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L336)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

141: 		            if (decipher[i] != 0xff) {

153: 		                if (decipher[3 + paddingLen + i] != bytes1(sha256ExplicitNullParam[i])) {

159: 		                if (decipher[3 + paddingLen + i] != bytes1(sha256ImplicitNullParam[i])) {

175: 		            if (decipher[5 + paddingLen + digestAlgoWithParamLen + i] != _sha256[i]) {

274: 		            if (decipher[i] != 0xff) {

284: 		            if (decipher[3 + paddingLen + i] != bytes1(sha1Prefix[i])) {

291: 		            if (decipher[3 + paddingLen + sha1Prefix.length + i] != _sha1[i]) {
```
[[141](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L141), [153](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L153), [159](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L159), [175](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L175), [274](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L274), [284](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L284), [291](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L291)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

60: 		            timestamp += uint256(monthDays[i - 1]) * 86_400; // Days in seconds
```
[[60](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L60)]



```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

173: 		            if (_tierFees[i].tier == _tierId) return _tierFees[i].fee;
```
[[173](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L173)]



```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

87: 		                uint256 data = _state.ethDeposits[j % _config.ethDepositRingBufferSize];

88: 		                deposits_[i] = TaikoData.EthDeposit({

93: 		                uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount;

101: 		                    deposits_[i].amount -= _fee;
```
[[87](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L87), [88](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L88), [93](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L93), [101](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L101)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

245: 		                if (uint160(prevHook) >= uint160(params.hookCalls[i].hook)) {

253: 		                IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }(

254: 		                    blk, meta_, params.hookCalls[i].data

257: 		                prevHook = params.hookCalls[i].hook;
```
[[245](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L245), [253](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L253), [254](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L254), [257](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L257)]



```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

75: 		            delete guardianIds[guardians[i]];

81: 		            address guardian = _newGuardians[i];

84: 		            if (guardianIds[guardian] != 0) revert INVALID_GUARDIAN_SET();

88: 		            guardianIds[guardian] = guardians.length;
```
[[75](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L75), [81](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L81), [84](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L84), [88](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L88)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

60: 		            IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);
```
[[60](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L60)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

154: 		            uint256 digits = uint256(uint8(bytes1(encoded[i])));

282: 		            quoteCerts[i] = Base64.decode(string(quoteCerts[i]));
```
[[154](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L154), [282](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L282)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

47: 		                out_[i] = bytes1(uint8((_len / (256 ** (lenLen - i))) % 256));

60: 		            if (b[i] != 0) {

67: 		            out_[j] = b[i++];
```
[[47](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L47), [60](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L60), [67](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L67)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

86: 		            TrieNode memory currentNode = proof[i];

118: 		                    value_ = RLPReader.readBytes(currentNode.decoded[TREE_RADIX]);

134: 		                    uint8 branchKey = uint8(key[currentKeyIndex]);

135: 		                    RLPReader.RLPItem memory nextNode = currentNode.decoded[branchKey];

141: 		                uint8 prefix = uint8(path[0]);

171: 		                    value_ = RLPReader.readBytes(currentNode.decoded[1]);

188: 		                    currentNodeID = _getNodeID(currentNode.decoded[1]);

209: 		            proof_[i] = TrieNode({ encoded: _proof[i], decoded: RLPReader.readList(_proof[i]) });

244: 		        for (; shared_ < max && _a[shared_] == _b[shared_];) {
```
[[86](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L86), [118](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L118), [134](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L134), [135](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L135), [141](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L141), [171](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L171), [188](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L188), [209](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L209), [244](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L244)]

</details>

---

### [G-02] State variables can be packed into fewer storage slots

Each slot saved can avoid an extra Gsset (**20000 gas**). Reads and writes (if two variables that occupy the same slot are written by the same function) will have a cheaper gas consumption.

*There are 2 instances of this issue.*


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

// @audit Can save 1 storage slot (from 7 to 6) 
// @audit Consider using the following order:
/*
  *	mapping(bytes32 => bool) _trustedUserMrEnclave (32)
  *	mapping(bytes32 => bool) _trustedUserMrSigner (32)
  *	mapping(uint256 => mapping(bytes => bool)) _serialNumIsRevoked (32)
  *	mapping(string => TCBInfoStruct.TCBInfo) tcbInfo (32)
  *	EnclaveIdStruct.EnclaveId qeIdentity (20)
  *	bool _checkLocalEnclaveReport (1)
  *	address owner (20)
*/
22: 		contract AutomataDcapV3Attestation is IAttestation {
```
[[22](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L22)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

// @audit Can save 1 storage slot (from 6 to 5) 
// @audit Consider using the following order:
/*
  *	mapping(address => uint256) claimedAmount (32)
  *	mapping(address => uint256) withdrawnAmount (32)
  *	uint256[] __gap (32)
  *	address token (20)
  *	uint64 withdrawalWindow (8)
  *	address vault (20)
*/
12: 		contract ERC20Airdrop2 is MerkleClaimable {
```
[[12](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L12)]


---

### [G-03] Structs can be packed into fewer storage slots

Each slot saved can avoid an extra Gsset (**20000 gas**) for the first setting of the struct. Subsequent reads as well as writes have smaller gas savings.

*There are 3 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: packages/protocol/contracts/L1/TaikoData.sol

// @audit Can save 1 storage slot (from 8 to 7) 
// @audit Consider using the following order:
/*
  *	uint256 ethDepositRingBufferSize (32)
  *	uint256 ethDepositGas (32)
  *	uint256 ethDepositMaxFee (32)
  *	uint96 livenessBond (12)
  *	uint96 ethDepositMinAmount (12)
  *	uint64 chainId (8)
  *	uint96 ethDepositMaxAmount (12)
  *	uint64 blockMaxProposals (8)
  *	uint64 blockRingBufferSize (8)
  *	uint32 blockMaxGasLimit (4)
  *	uint64 maxBlocksToVerifyPerProposal (8)
  *	uint64 ethDepositMinCountPerBlock (8)
  *	uint64 ethDepositMaxCountPerBlock (8)
  *	uint24 blockMaxTxListBytes (3)
  *	uint24 blobExpiry (3)
  *	bool blobAllowedForDA (1)
  *	bool blobReuseEnabled (1)
  *	uint8 blockSyncThreshold (1)
*/
10: 		    struct Config {
11: 		        // ---------------------------------------------------------------------
12: 		        // Group 1: General configs
13: 		        // ---------------------------------------------------------------------
14: 		        // The chain ID of the network where Taiko contracts are deployed.
15: 		        uint64 chainId;
16: 		        // ---------------------------------------------------------------------
17: 		        // Group 2: Block level configs
18: 		        // ---------------------------------------------------------------------
19: 		        // The maximum number of proposals allowed in a single block.
20: 		        uint64 blockMaxProposals;
21: 		        // Size of the block ring buffer, allowing extra space for proposals.
22: 		        uint64 blockRingBufferSize;
23: 		        // The maximum number of verifications allowed when a block is proposed.
24: 		        uint64 maxBlocksToVerifyPerProposal;
25: 		        // The maximum gas limit allowed for a block.
26: 		        uint32 blockMaxGasLimit;
27: 		        // The maximum allowed bytes for the proposed transaction list calldata.
28: 		        uint24 blockMaxTxListBytes;
29: 		        // The max period in seconds that a blob can be reused for DA.
30: 		        uint24 blobExpiry;
31: 		        // True if EIP-4844 is enabled for DA
32: 		        bool blobAllowedForDA;
33: 		        // True if blob can be reused
34: 		        bool blobReuseEnabled;
35: 		        // ---------------------------------------------------------------------
36: 		        // Group 3: Proof related configs
37: 		        // ---------------------------------------------------------------------
38: 		        // The amount of Taiko token as a prover liveness bond
39: 		        uint96 livenessBond;
40: 		        // ---------------------------------------------------------------------
41: 		        // Group 4: ETH deposit related configs
42: 		        // ---------------------------------------------------------------------
43: 		        // The size of the ETH deposit ring buffer.
44: 		        uint256 ethDepositRingBufferSize;
45: 		        // The minimum number of ETH deposits allowed per block.
46: 		        uint64 ethDepositMinCountPerBlock;
47: 		        // The maximum number of ETH deposits allowed per block.
48: 		        uint64 ethDepositMaxCountPerBlock;
49: 		        // The minimum amount of ETH required for a deposit.
50: 		        uint96 ethDepositMinAmount;
51: 		        // The maximum amount of ETH allowed for a deposit.
52: 		        uint96 ethDepositMaxAmount;
53: 		        // The gas cost for processing an ETH deposit.
54: 		        uint256 ethDepositGas;
55: 		        // The maximum fee allowed for an ETH deposit.
56: 		        uint256 ethDepositMaxFee;
57: 		        // The max number of L2 blocks that can stay unsynced on L1 (a value of zero disables
58: 		        // syncing)
59: 		        uint8 blockSyncThreshold;
60: 		    }

// @audit Can save 1 storage slot (from 7 to 6) 
// @audit Consider using the following order:
/*
  *	bytes32 extraData (32)
  *	bytes32 blobHash (32)
  *	bytes32 parentMetaHash (32)
  *	HookCall[] hookCalls (32)
  *	address assignedProver (20)
  *	uint24 txListByteOffset (3)
  *	uint24 txListByteSize (3)
  *	bool cacheBlobForReuse (1)
  *	address coinbase (20)
*/
78: 		    struct BlockParams {
79: 		        address assignedProver;
80: 		        address coinbase;
81: 		        bytes32 extraData;
82: 		        bytes32 blobHash;
83: 		        uint24 txListByteOffset;
84: 		        uint24 txListByteSize;
85: 		        bool cacheBlobForReuse;
86: 		        bytes32 parentMetaHash;
87: 		        HookCall[] hookCalls;
88: 		    }
```
[[10-60](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L10-L60), [78-88](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L78-L88)]



```solidity
File: packages/protocol/contracts/signal/ISignalService.sol

// @audit Can save 1 storage slot (from 5 to 4) 
// @audit Consider using the following order:
/*
  *	bytes32 rootHash (32)
  *	bytes[] accountProof (32)
  *	bytes[] storageProof (32)
  *	uint64 chainId (8)
  *	uint64 blockId (8)
  *	CacheOption cacheOption (1)
*/
20: 		    struct HopProof {
21: 		        uint64 chainId;
22: 		        uint64 blockId;
23: 		        bytes32 rootHash;
24: 		        CacheOption cacheOption;
25: 		        bytes[] accountProof;
26: 		        bytes[] storageProof;
27: 		    }
```
[[20-27](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/ISignalService.sol#L20-L27)]

</details>

---

### [G-04] Multiple `mapping`s that share an ID can be combined into a single `mapping` of ID / `struct`

This can avoid a Gsset (**20000 Gas**) per mapping combined. Reads and writes will also be cheaper when a function requires both values as they both can fit in the same storage slot.

Finally, if both fields are accessed in the same function, this can save **~42 gas** per access due to not having to recalculate the key's `keccak256` hash (Gkeccak256 - **30 Gas**) and that calculation's associated stack operations.

*There is 1 instance of this issue.*


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

// @audit consider merging _trustedUserMrEnclave, _trustedUserMrSigner
39: 		    mapping(bytes32 enclave => bool trusted) private _trustedUserMrEnclave;
40: 		    mapping(bytes32 signer => bool trusted) private _trustedUserMrSigner;
```
[[39](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L39)]


---

### [G-05] Use of `memory` instead of `storage` for struct/array state variables

When fetching data from `storage`, using the `memory` keyword to assign it to a variable reads all fields of the struct/array and incurs a Gcoldsload (**2100 gas**) for each field.

This can be avoided by declaring the variable with the `storage` keyword and caching the necessary fields in stack variables.

The `memory` keyword should only be used if the entire struct/array is being returned or passed to a function that requires `memory`, or if it is being read from another `memory` array/struct.

*There are 2 instances of this issue.*


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

180: 		        EnclaveIdStruct.EnclaveId memory enclaveId = qeIdentity;
```
[[180](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L180)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

171: 		            CanonicalERC20 memory ctoken = bridgedToCanonical[btokenOld_];
```
[[171](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L171)]


---

### [G-06] State variables access within a loop

State variable reads and writes are more expensive than local variable reads and writes. Therefore, it is recommended to replace state variable reads and writes within loops with a local variable. Gas savings should be multiplied by the average loop length.

*There are 4 instances of this issue.*


```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

// @audit nextInstanceId
218: 		            ids[i] = nextInstanceId;
```
[[218](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L218)]



```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

// @audit guardians
87: 		            guardians.push(guardian);

// @audit guardians
88: 		            guardianIds[guardian] = guardians.length;

// @audit minGuardians
135: 		                if (count == minGuardians) return true;
```
[[87](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L87), [88](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L88), [135](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L135)]


---

### [G-07] Unused non-constant state variables waste gas

If the variable is assigned a non-zero value, saves Gsset (20000 gas). If it's assigned a zero value, saves Gsreset (2900 gas).

If the variable remains unassigned, there is no gas savings unless the variable is public, in which case the compiler-generated non-payable getter deployment cost is saved.

If the state variable is overriding an interface's public function, mark the variable as constant or immutable so that it does not use a storage slot.

*There are 2 instances of this issue.*


```solidity
File: packages/protocol/contracts/tokenvault/BaseNFTVault.sol

56: 		    mapping(address btoken => CanonicalNFT canonical) public bridgedToCanonical;

59: 		    mapping(uint256 chainId => mapping(address ctoken => address btoken)) public canonicalToBridged;
```
[[56](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L56), [59](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L59)]


---

### [G-08] State variables only set in the constructor should be declared `immutable`

Accessing state variables within a function involves an SLOAD operation, but `immutable` variables can be accessed directly without the need of it, thus reducing gas costs. As these state variables are assigned only in the constructor, consider declaring them `immutable`.

*There are 2 instances of this issue.*


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

52: 		    address public owner;
```
[[52](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L52)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

18: 		    address private ES256VERIFIER;
```
[[18](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L18)]


---

### [G-09] Cache state variables with stack variables

Caching of a state variable replaces each Gwarmaccess (**100 gas**) with a cheaper stack read. Other less obvious fixes/optimizations include having local memory caches of state variable structs, or having local caches of state variable contracts/addresses.

*There are 17 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

// @audit addressManager on line 83
81: 		        if (addressManager == address(0)) revert RESOLVER_INVALID_MANAGER();
```
[[81](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressResolver.sol#L81)]



```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

// @audit state on lines 67, 70
69: 		        if (!state.slotB.provingPaused) {

// @audit state on line 94
96: 		        LibVerifying.verifyBlocks(state, config, this, maxBlocksToVerify);

// @audit state on line 151
154: 		            ts_ = state.transitions[slot][blk_.verifiedTransitionId];

// @audit state on line 181
182: 		        b_ = state.slotB;
```
[[69](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L69), [96](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L96), [154](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L154), [182](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L182)]



```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

// @audit nextTxId on line 53
43: 		        if (txId != nextTxId) revert XCO_INVALID_TX_ID();
```
[[43](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L43)]



```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

// @audit gasExcess on line 265
262: 		        if (gasExcess > 0) {

// @audit lastSyncedBlock on line 275
276: 		                numL1Blocks = _l1BlockId - lastSyncedBlock;
```
[[262](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L262), [276](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L276)]



```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

// @audit sharedVault on line 219
220: 		        IERC20(costToken).safeTransferFrom(_recipient, sharedVault, costToWithdraw);
```
[[220](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L220)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

// @audit migratingAddress on line 63
61: 		        if (msg.sender == migratingAddress) {

// @audit migratingAddress on line 80
80: 		            emit MigratedTo(migratingAddress, _account, _amount);
```
[[61](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L61), [80](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L80)]



```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

// @audit nextInstanceId on lines 218, 220, 222
217: 		            instances[nextInstanceId] = Instance(_instances[i], validSince);
```
[[217](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L217)]



```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

// @audit version on line 95
92: 		        ++version;

// @audit guardians on lines 74, 87, 88
77: 		        delete guardians;

// @audit version on line 116
119: 		        uint256 _approval = _approvals[version][_hash];
```
[[92](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L92), [77](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L77), [119](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L119)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

// @audit token on line 63
71: 		        IVotes(token).delegateBySig(delegatee, nonce, expiry, v, r, s);
```
[[71](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L71)]



```solidity
File: packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

// @audit usdc on line 48
49: 		        usdc.burn(_amount);
```
[[49](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L49)]

</details>

---

### [G-10] Modifiers order should be changed

According to solidity docs, modifiers are executed in the order they are presented, so the order can be improved to avoid unnecessary `SLOAD`s and/or external calls by prioritizing cheaper modifiers first.

*There are 5 instances of this issue.*


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

155: 		    function recallMessage(
156: 		        Message calldata _message,
157: 		        bytes calldata _proof
158: 		    )
159: 		        external
160: 		        nonReentrant
161: 		        whenNotPaused
162: 		        sameChain(_message.srcChainId)

217: 		    function processMessage(
218: 		        Message calldata _message,
219: 		        bytes calldata _proof
220: 		    )
221: 		        external
222: 		        nonReentrant
223: 		        whenNotPaused
224: 		        sameChain(_message.destChainId)

310: 		    function retryMessage(
311: 		        Message calldata _message,
312: 		        bool _isLastAttempt
313: 		    )
314: 		        external
315: 		        nonReentrant
316: 		        whenNotPaused
317: 		        sameChain(_message.destChainId)
```
[[155-162](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L155-L162), [217-224](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L217-L224), [310-317](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L310-L317)]



```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

75: 		    function proveBlock(
76: 		        uint64 _blockId,
77: 		        bytes calldata _input
78: 		    )
79: 		        external
80: 		        nonReentrant
81: 		        whenNotPaused
82: 		        whenProvingNotPaused

100: 		    function verifyBlocks(uint64 _maxBlocksToVerify)
101: 		        external
102: 		        nonReentrant
103: 		        whenNotPaused
104: 		        whenProvingNotPaused
```
[[75-82](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L75-L82), [100-104](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L100-L104)]


---

### [G-11] Low level `call` can be optimized with assembly

`returnData` is copied to memory even if the variable is not utilized: the proper way to handle this is through a low level assembly call.

```solidity
// before
(bool success,) = payable(receiver).call{gas: gas, value: value}("");

//after
bool success;
assembly {
    success := call(gas, receiver, value, 0, 0, 0, 0)
}
```

*There is 1 instance of this issue.*


```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

50: 		        (bool success,) = address(this).call(txdata);
```
[[50](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L50)]


---

### [G-12] Use of `memory` instead of `calldata` for immutable arguments

Consider refactoring the function arguments from `memory` to `calldata` when they are immutable, as `calldata` is cheaper.

*There are 116 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

// @audit quoteEnclaveReport
175: 		    function _verifyQEReportWithIdentity(V3Struct.EnclaveReport memory quoteEnclaveReport)

// @audit pck, tcb
206: 		    function _checkTcbLevels(
207: 		        IPEMCertChainLib.PCKCertificateField memory pck,
208: 		        TCBInfoStruct.TCBInfo memory tcb

// @audit pckCpuSvns, tcbCpuSvns
229: 		    function _isCpuSvnHigherOrGreater(
230: 		        uint256[] memory pckCpuSvns,
231: 		        uint8[] memory tcbCpuSvns

// @audit certs
248: 		    function _verifyCertChain(IPEMCertChainLib.ECSha256Certificate[] memory certs)

// @audit pckCertPubKey, signedQuoteData, authDataV3, qeEnclaveReport
303: 		    function _enclaveReportSigVerification(
304: 		        bytes memory pckCertPubKey,
305: 		        bytes memory signedQuoteData,
306: 		        V3Struct.ECDSAQuoteV3AuthData memory authDataV3,
307: 		        V3Struct.EnclaveReport memory qeEnclaveReport
```
[[175](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L175), [206-208](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L206-L208), [229-231](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L229-L231), [248](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L248), [303-307](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L303-L307)]



```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

// @audit _config
252: 		    function _calc1559BaseFee(
253: 		        Config memory _config,
254: 		        uint64 _l1BlockId,
255: 		        uint32 _parentGasUsed
```
[[252-255](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L252-L255)]



```solidity
File: packages/protocol/contracts/libs/LibAddress.sol

// @audit _sig
61: 		    function isValidSignature(
62: 		        address _addr,
63: 		        bytes32 _hash,
64: 		        bytes memory _sig
```
[[61-64](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibAddress.sol#L61-L64)]



```solidity
File: packages/protocol/contracts/signal/SignalService.sol

// @audit _hop
206: 		    function _verifyHopProof(
207: 		        uint64 _chainId,
208: 		        address _app,
209: 		        bytes32 _signal,
210: 		        bytes32 _value,
211: 		        HopProof memory _hop,
212: 		        address _signalService

// @audit _hop
271: 		    function _cacheChainData(
272: 		        HopProof memory _hop,
273: 		        uint64 _chainId,
274: 		        uint64 _blockId,
275: 		        bytes32 _signalRoot,
276: 		        bool _isFullProof,
277: 		        bool _isLastHop
```
[[206-212](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L206-L212), [271-277](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L271-L277)]



```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

// @audit _sig
168: 		    function withdraw(address _to, bytes memory _sig) external {

// @audit _grant
235: 		    function _getAmountOwned(Grant memory _grant) private view returns (uint128) {

// @audit _grant
267: 		    function _validateGrant(Grant memory _grant) private pure {
```
[[168](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L168), [235](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L235), [267](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L267)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

// @audit _symbol, _name
38: 		    function init(
39: 		        address _owner,
40: 		        address _addressManager,
41: 		        address _srcToken,
42: 		        uint256 _srcChainId,
43: 		        string memory _symbol,
44: 		        string memory _name
```
[[38-44](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L38-L44)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

// @audit _symbol, _name
52: 		    function init(
53: 		        address _owner,
54: 		        address _addressManager,
55: 		        address _srcToken,
56: 		        uint256 _srcChainId,
57: 		        uint8 _decimals,
58: 		        string memory _symbol,
59: 		        string memory _name
```
[[52-59](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L52-L59)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

// @audit _symbol, _name
31: 		    function init(
32: 		        address _owner,
33: 		        address _addressManager,
34: 		        address _srcToken,
35: 		        uint256 _srcChainId,
36: 		        string memory _symbol,
37: 		        string memory _name
```
[[31-37](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L31-L37)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

// @audit _op
240: 		    function _handleMessage(
241: 		        address _user,
242: 		        BridgeTransferOp memory _op

// @audit _ctoken
303: 		    function _deployBridgedToken(CanonicalNFT memory _ctoken) private returns (address btoken_) {
```
[[240-242](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L240-L242), [303](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L303)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

// @audit ctoken
407: 		    function _deployBridgedToken(CanonicalERC20 memory ctoken) private returns (address btoken) {
```
[[407](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L407)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

// @audit _tokenIds
160: 		    function _transferTokens(
161: 		        CanonicalNFT memory _ctoken,
162: 		        address _to,
163: 		        uint256[] memory _tokenIds

// @audit _op
187: 		    function _handleMessage(
188: 		        address _user,
189: 		        BridgeTransferOp memory _op

// @audit _ctoken
240: 		    function _deployBridgedToken(CanonicalNFT memory _ctoken) private returns (address btoken_) {
```
[[160-163](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L160-L163), [187-189](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L187-L189), [240](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L240)]



```solidity
File: packages/protocol/contracts/tokenvault/LibBridgedToken.sol

// @audit _symbol, _name
11: 		    function validateInputs(
12: 		        address _srcToken,
13: 		        uint256 _srcChainId,
14: 		        string memory _symbol,
15: 		        string memory _name

// @audit _name
28: 		    function buildName(
29: 		        string memory _name,
30: 		        uint256 _srcChainId

// @audit _symbol
39: 		    function buildSymbol(string memory _symbol) internal pure returns (string memory) {
```
[[11-15](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L11-L15), [28-30](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L28-L30), [39](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L39)]



```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

// @audit _instances
195: 		    function _addInstances(
196: 		        address[] memory _instances,
197: 		        bool instantValid
```
[[195-197](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L195-L197)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

// @audit pemChain
40: 		    function splitCertificateChain(
41: 		        bytes memory pemChain,
42: 		        uint256 size

// @audit der
74: 		    function decodeCert(
75: 		        bytes memory der,
76: 		        bool isPckCert

// @audit pemData
216: 		    function _removeHeadersAndFooters(string memory pemData)

// @audit input
252: 		    function _trimBytes(
253: 		        bytes memory input,
254: 		        uint256 expectedLength

// @audit der
269: 		    function _findPckTcbInfo(
270: 		        bytes memory der,
271: 		        uint256 tbsPtr,
272: 		        uint256 tbsParentPtr

// @audit der
341: 		    function _findTcb(
342: 		        bytes memory der,
343: 		        uint256 oidPtr
```
[[40-42](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L40-L42), [74-76](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L74-L76), [216](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L216), [252-254](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L252-L254), [269-272](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L269-L272), [341-343](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L341-L343)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

// @audit der
47: 		    function root(bytes memory der) internal pure returns (uint256) {

// @audit der
56: 		    function rootOfBitStringAt(bytes memory der, uint256 ptr) internal pure returns (uint256) {

// @audit der
66: 		    function rootOfOctetStringAt(bytes memory der, uint256 ptr) internal pure returns (uint256) {

// @audit der
77: 		    function nextSiblingOf(bytes memory der, uint256 ptr) internal pure returns (uint256) {

// @audit der
87: 		    function firstChildOf(bytes memory der, uint256 ptr) internal pure returns (uint256) {

// @audit der
111: 		    function bytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes memory) {

// @audit der
121: 		    function allBytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes memory) {

// @audit der
131: 		    function bytes32At(bytes memory der, uint256 ptr) internal pure returns (bytes32) {

// @audit der
141: 		    function uintAt(bytes memory der, uint256 ptr) internal pure returns (uint256) {

// @audit der
154: 		    function uintBytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes memory) {

// @audit der
165: 		    function keccakOfBytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes32) {

// @audit der
169: 		    function keccakOfAllBytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes32) {

// @audit der
179: 		    function bitstringAt(bytes memory der, uint256 ptr) internal pure returns (bytes memory) {

// @audit der
187: 		    function _readNodeLength(bytes memory der, uint256 ix) private pure returns (uint256) {
```
[[47](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L47), [56](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L56), [66](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L66), [77](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L77), [87](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L87), [111](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L111), [121](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L121), [131](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L131), [141](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L141), [154](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L154), [165](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L165), [169](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L169), [179](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L179), [187](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L187)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

// @audit self
16: 		    function keccak(
17: 		        bytes memory self,
18: 		        uint256 offset,
19: 		        uint256 len

// @audit self, other
39: 		    function compare(bytes memory self, bytes memory other) internal pure returns (int256) {

// @audit self, other
56: 		    function compare(
57: 		        bytes memory self,
58: 		        uint256 offset,
59: 		        uint256 len,
60: 		        bytes memory other,
61: 		        uint256 otheroffset,
62: 		        uint256 otherlen

// @audit self, other
116: 		    function equals(
117: 		        bytes memory self,
118: 		        uint256 offset,
119: 		        bytes memory other,
120: 		        uint256 otherOffset,
121: 		        uint256 len

// @audit self, other
138: 		    function equals(
139: 		        bytes memory self,
140: 		        uint256 offset,
141: 		        bytes memory other,
142: 		        uint256 otherOffset

// @audit self, other
160: 		    function equals(
161: 		        bytes memory self,
162: 		        uint256 offset,
163: 		        bytes memory other

// @audit self, other
178: 		    function equals(bytes memory self, bytes memory other) internal pure returns (bool) {

// @audit self
188: 		    function readUint8(bytes memory self, uint256 idx) internal pure returns (uint8 ret) {

// @audit self
198: 		    function readUint16(bytes memory self, uint256 idx) internal pure returns (uint16 ret) {

// @audit self
211: 		    function readUint32(bytes memory self, uint256 idx) internal pure returns (uint32 ret) {

// @audit self
224: 		    function readBytes32(bytes memory self, uint256 idx) internal pure returns (bytes32 ret) {

// @audit self
237: 		    function readBytes20(bytes memory self, uint256 idx) internal pure returns (bytes20 ret) {

// @audit self
255: 		    function readBytesN(
256: 		        bytes memory self,
257: 		        uint256 idx,
258: 		        uint256 len

// @audit self
284: 		    function substring(
285: 		        bytes memory self,
286: 		        uint256 offset,
287: 		        uint256 len

// @audit self
320: 		    function base32HexDecodeWord(
321: 		        bytes memory self,
322: 		        uint256 off,
323: 		        uint256 len

// @audit a, b
371: 		    function compareBytes(bytes memory a, bytes memory b) internal pure returns (bool) {
```
[[16-19](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L16-L19), [39](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L39), [56-62](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L56-L62), [116-121](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L116-L121), [138-142](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L138-L142), [160-163](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L160-L163), [178](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L178), [188](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L188), [198](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L198), [211](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L211), [224](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L224), [237](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L237), [255-258](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L255-L258), [284-287](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L284-L287), [320-323](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L320-L323), [371](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L371)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

// @audit _s, _e, _m
43: 		    function pkcs1Sha256(
44: 		        bytes32 _sha256,
45: 		        bytes memory _s,
46: 		        bytes memory _e,
47: 		        bytes memory _m

// @audit _data, _s, _e, _m
191: 		    function pkcs1Sha256Raw(
192: 		        bytes memory _data,
193: 		        bytes memory _s,
194: 		        bytes memory _e,
195: 		        bytes memory _m

// @audit _s, _e, _m
212: 		    function pkcs1Sha1(
213: 		        bytes20 _sha1,
214: 		        bytes memory _s,
215: 		        bytes memory _e,
216: 		        bytes memory _m

// @audit _data, _s, _e, _m
307: 		    function pkcs1Sha1Raw(
308: 		        bytes memory _data,
309: 		        bytes memory _s,
310: 		        bytes memory _e,
311: 		        bytes memory _m
```
[[43-47](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L43-L47), [191-195](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L191-L195), [212-216](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L212-L216), [307-311](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L307-L311)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/SHA1.sol

// @audit data
11: 		    function sha1(bytes memory data) internal pure returns (bytes20 ret) {
```
[[11](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SHA1.sol#L11)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

// @audit tbs, signature, publicKey
24: 		    function verifyAttStmtSignature(
25: 		        bytes memory tbs,
26: 		        bytes memory signature,
27: 		        PublicKey memory publicKey,
28: 		        Algorithm alg

// @audit tbs, signature, publicKey
54: 		    function verifyCertificateSignature(
55: 		        bytes memory tbs,
56: 		        bytes memory signature,
57: 		        PublicKey memory publicKey,
58: 		        CertSigAlgorithm alg

// @audit tbs, signature, publicKey
79: 		    function verifyRS256Signature(
80: 		        bytes memory tbs,
81: 		        bytes memory signature,
82: 		        bytes memory publicKey

// @audit tbs, signature, publicKey
96: 		    function verifyRS1Signature(
97: 		        bytes memory tbs,
98: 		        bytes memory signature,
99: 		        bytes memory publicKey

// @audit tbs, signature, publicKey
113: 		    function verifyES256Signature(
114: 		        bytes memory tbs,
115: 		        bytes memory signature,
116: 		        bytes memory publicKey
```
[[24-28](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L24-L28), [54-58](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L54-L58), [79-82](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L79-L82), [96-99](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L96-L99), [113-116](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L113-L116)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

// @audit x509Time
8: 		    function toTimestamp(bytes memory x509Time) internal pure returns (uint256) {
```
[[8](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L8)]



```solidity
File: packages/protocol/contracts/L1/gov/TaikoGovernor.sol

// @audit _description
48: 		    function propose(
49: 		        address[] memory _targets,
50: 		        uint256[] memory _values,
51: 		        bytes[] memory _calldatas,
52: 		        string memory _description

// @audit _description
69: 		    function propose(
70: 		        address[] memory _targets,
71: 		        uint256[] memory _values,
72: 		        string[] memory _signatures,
73: 		        bytes[] memory _calldatas,
74: 		        string memory _description
```
[[48-52](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L48-L52), [69-74](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L69-L74)]



```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

// @audit _blk, _data
62: 		    function onBlockProposed(
63: 		        TaikoData.Block memory _blk,
64: 		        TaikoData.BlockMetadata memory _meta,
65: 		        bytes memory _data

// @audit _assignment
137: 		    function hashAssignment(
138: 		        ProverAssignment memory _assignment,
139: 		        address _taikoL1Address,
140: 		        bytes32 _blobHash

// @audit _tierFees
164: 		    function _getProverFee(
165: 		        TaikoData.TierFee[] memory _tierFees,
166: 		        uint16 _tierId
```
[[62-65](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L62-L65), [137-140](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L137-L140), [164-166](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L164-L166)]



```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

// @audit _config
67: 		    function processDeposits(
68: 		        TaikoData.State storage _state,
69: 		        TaikoData.Config memory _config,
70: 		        address _feeRecipient

// @audit _config
122: 		    function canDepositEthToL2(
123: 		        TaikoData.State storage _state,
124: 		        TaikoData.Config memory _config,
125: 		        uint256 _amount
```
[[67-70](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L67-L70), [122-125](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L122-L125)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

// @audit _config
287: 		    function isBlobReusable(
288: 		        TaikoData.State storage _state,
289: 		        TaikoData.Config memory _config,
290: 		        bytes32 _blobHash

// @audit _slotB
299: 		    function _isProposerPermitted(
300: 		        TaikoData.SlotB memory _slotB,
301: 		        IAddressResolver _resolver
```
[[287-290](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L287-L290), [299-301](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L299-L301)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

// @audit _config
91: 		    function proveBlock(
92: 		        TaikoData.State storage _state,
93: 		        TaikoData.Config memory _config,
94: 		        IAddressResolver _resolver,
95: 		        TaikoData.BlockMetadata memory _meta,
96: 		        TaikoData.Transition memory _tran,
97: 		        TaikoData.TierProof memory _proof

// @audit _tran
269: 		    function _createTransition(
270: 		        TaikoData.State storage _state,
271: 		        TaikoData.Block storage _blk,
272: 		        TaikoData.Transition memory _tran,
273: 		        uint64 slot

// @audit _tran, _proof, _tier
350: 		    function _overrideWithHigherProof(
351: 		        TaikoData.TransitionState storage _ts,
352: 		        TaikoData.Transition memory _tran,
353: 		        TaikoData.TierProof memory _proof,
354: 		        ITierProvider.Tier memory _tier,
355: 		        IERC20 _tko,
356: 		        bool _sameTransition

// @audit _tier
401: 		    function _checkProverPermission(
402: 		        TaikoData.State storage _state,
403: 		        TaikoData.Block storage _blk,
404: 		        TaikoData.TransitionState storage _ts,
405: 		        uint32 _tid,
406: 		        ITierProvider.Tier memory _tier
```
[[91-97](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L91-L97), [269-273](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L269-L273), [350-356](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L350-L356), [401-406](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L401-L406)]



```solidity
File: packages/protocol/contracts/L1/libs/LibUtils.sol

// @audit _config
23: 		    function getTransition(
24: 		        TaikoData.State storage _state,
25: 		        TaikoData.Config memory _config,
26: 		        uint64 _blockId,
27: 		        bytes32 _parentHash

// @audit _config
52: 		    function getBlock(
53: 		        TaikoData.State storage _state,
54: 		        TaikoData.Config memory _config,
55: 		        uint64 _blockId
```
[[23-27](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibUtils.sol#L23-L27), [52-55](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibUtils.sol#L52-L55)]



```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

// @audit _config
224: 		    function _syncChainData(
225: 		        TaikoData.Config memory _config,
226: 		        IAddressResolver _resolver,
227: 		        uint64 _lastVerifiedBlockId,
228: 		        bytes32 _stateRoot

// @audit _config
245: 		    function _isConfigValid(TaikoData.Config memory _config) private view returns (bool) {
```
[[224-228](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L224-L228), [245](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L245)]



```solidity
File: packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol

// @audit _calldata
25: 		    function excessivelySafeCall(
26: 		        address _target,
27: 		        uint256 _gas,
28: 		        uint256 _value,
29: 		        uint16 _maxCopy,
30: 		        bytes memory _calldata
```
[[25-30](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L25-L30)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/Bytes.sol

// @audit _bytes
15: 		    function slice(
16: 		        bytes memory _bytes,
17: 		        uint256 _start,
18: 		        uint256 _length

// @audit _bytes
91: 		    function slice(bytes memory _bytes, uint256 _start) internal pure returns (bytes memory) {

// @audit _bytes
102: 		    function toNibbles(bytes memory _bytes) internal pure returns (bytes memory) {

// @audit _bytes, _other
149: 		    function equal(bytes memory _bytes, bytes memory _other) internal pure returns (bool) {
```
[[15-18](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L15-L18), [91](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L91), [102](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L102), [149](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L149)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

// @audit quote
21: 		    function parseInput(
22: 		        bytes memory quote,
23: 		        address pemCertLibAddr

// @audit v3Quote
62: 		    function validateParsedInput(V3Struct.ParsedV3QuoteStruct memory v3Quote)

// @audit rawEnclaveReport
133: 		    function parseEnclaveReport(bytes memory rawEnclaveReport)

// @audit encoded
152: 		    function littleEndianDecode(bytes memory encoded) private pure returns (uint256 decoded) {

// @audit rawHeader
165: 		    function parseAndVerifyHeader(bytes memory rawHeader)

// @audit rawAuthData
203: 		    function parseAuthDataAndVerifyCertType(
204: 		        bytes memory rawAuthData,
205: 		        address pemCertLibAddr

// @audit enclaveReport
244: 		    function packQEReport(V3Struct.EnclaveReport memory enclaveReport)

// @audit certBytes
267: 		    function parseCerificationChainBytes(
268: 		        bytes memory certBytes,
269: 		        address pemCertLibAddr
```
[[21-23](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L21-L23), [62](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L62), [133](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L133), [152](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L152), [165](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L165), [203-205](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L203-L205), [244](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L244), [267-269](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L267-L269)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

// @audit _in
35: 		    function toRLPItem(bytes memory _in) internal pure returns (RLPItem memory out_) {

// @audit _in
102: 		    function readList(bytes memory _in) internal pure returns (RLPItem[] memory out_) {

// @audit _in
128: 		    function readBytes(bytes memory _in) internal pure returns (bytes memory out_) {

// @audit _in
135: 		    function readRawBytes(RLPItem memory _in) internal pure returns (bytes memory out_) {

// @audit _in
144: 		    function _decodeLength(RLPItem memory _in)
```
[[35](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L35), [102](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L102), [128](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L128), [135](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L135), [144](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L144)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

// @audit _in
13: 		    function writeBytes(bytes memory _in) internal pure returns (bytes memory out_) {
```
[[13](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L13)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

// @audit _key, _value
50: 		    function verifyInclusionProof(
51: 		        bytes memory _key,
52: 		        bytes memory _value,
53: 		        bytes[] memory _proof,
54: 		        bytes32 _root

// @audit _key
68: 		    function get(
69: 		        bytes memory _key,
70: 		        bytes[] memory _proof,
71: 		        bytes32 _root

// @audit _proof
205: 		    function _parseProof(bytes[] memory _proof) private pure returns (TrieNode[] memory proof_) {

// @audit _node
227: 		    function _getNodePath(TrieNode memory _node) private pure returns (bytes memory nibbles_) {

// @audit _a, _b
235: 		    function _getSharedNibbleLength(
236: 		        bytes memory _a,
237: 		        bytes memory _b
```
[[50-54](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L50-L54), [68-71](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L68-L71), [205](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L205), [227](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L227), [235-237](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L235-L237)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol

// @audit _key, _value
19: 		    function verifyInclusionProof(
20: 		        bytes memory _key,
21: 		        bytes memory _value,
22: 		        bytes[] memory _proof,
23: 		        bytes32 _root

// @audit _key
38: 		    function get(
39: 		        bytes memory _key,
40: 		        bytes[] memory _proof,
41: 		        bytes32 _root

// @audit _key
54: 		    function _getSecureKey(bytes memory _key) private pure returns (bytes memory hash_) {
```
[[19-23](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L19-L23), [38-41](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L38-L41), [54](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L54)]

</details>

---

### [G-13] Avoid updating storage when the value hasn't changed

If the old value is equal to the new value, not re-storing the value will avoid a Gsreset (**2900 gas**), potentially at the expense of a Gcoldsload (**2100 gas**) or a Gwarmaccess (**100 gas**)

*There are 12 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

// @audit _trustedUserMrSigner
65: 		    function setMrSigner(bytes32 _mrSigner, bool _trusted) external onlyOwner {

// @audit _trustedUserMrEnclave
69: 		    function setMrEnclave(bytes32 _mrEnclave, bool _trusted) external onlyOwner {

// @audit tcbInfo
103: 		    function configureTcbInfoJson(

// @audit qeIdentity
114: 		    function configureQeIdentityJson(EnclaveIdStruct.EnclaveId calldata qeIdentityInput)
```
[[65](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L65), [69](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L69), [103](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L103), [114](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L114)]



```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

// @audit messageStatus
515: 		    function _updateMessageStatus(bytes32 _msgHash, Status _status) private {
```
[[515](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L515)]



```solidity
File: packages/protocol/contracts/common/AddressManager.sol

// @audit __addresses
38: 		    function setAddress(
```
[[38](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressManager.sol#L38)]



```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

// @audit customConfig
25: 		    function setConfigAndExcess(
```
[[25](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L25)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

// @audit snapshooter
80: 		    function setSnapshoter(address _snapshooter) external onlyOwner {
```
[[80](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L80)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

// @audit migratingAddress, migratingInbound
36: 		    function changeMigrationStatus(
```
[[36](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L36)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

// @audit btokenBlacklist, bridgedToCanonical, canonicalToBridged
148: 		    function changeBridgedToken(
```
[[148](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L148)]



```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

// @audit guardianIds, minGuardians
53: 		    function setGuardians(
```
[[53](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L53)]



```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

// @audit claimStart, claimEnd, merkleRoot
90: 		    function _setConfig(uint64 _claimStart, uint64 _claimEnd, bytes32 _merkleRoot) private {
```
[[90](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L90)]

</details>

---

### [G-14] Use of `emit` inside a loop

Emitting an event inside a loop performs a `LOG` op N times, where N is the loop length. Consider refactoring the code to emit the event only once at the end of loop. Gas savings should be multiplied by the average loop length.

*There are 4 instances of this issue.*


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

93: 		            emit MessageSuspended(msgHash, _suspend);
```
[[93](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L93)]



```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

109: 		            emit InstanceDeleted(idx, instances[idx].addr);

220: 		            emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);
```
[[109](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L109), [220](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220)]



```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

198: 		                emit BlockVerified({
199: 		                    blockId: blockId,
200: 		                    assignedProver: blk.assignedProver,
201: 		                    prover: ts.prover,
202: 		                    blockHash: blockHash,
203: 		                    stateRoot: stateRoot,
204: 		                    tier: ts.tier,
205: 		                    contestations: ts.contestations
206: 		                });
```
[[198-206](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L198-L206)]


---

### [G-15] Use `uint256(1)/uint256(2)` instead of `true/false` to save gas for changes

Use `uint256(1)` and `uint256(2)` for `true`/`false` to avoid a Gsset (20000 gas) when changing from `false` to `true`, after having been `true` in the past. See [source](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/58f635312aa21f947cae5f8578638a85aa2519f5/contracts/security/ReentrancyGuard.sol#L23-L27).

*There are 10 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

38: 		    bool private _checkLocalEnclaveReport;

39: 		    mapping(bytes32 enclave => bool trusted) private _trustedUserMrEnclave;

40: 		    mapping(bytes32 signer => bool trusted) private _trustedUserMrSigner;

47: 		    mapping(uint256 idx => mapping(bytes serialNum => bool revoked)) private _serialNumIsRevoked;
```
[[38](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L38), [39](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L39), [40](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L40), [47](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L47)]



```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

42: 		    mapping(address addr => bool banned) public addressBanned;
```
[[42](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L42)]



```solidity
File: packages/protocol/contracts/signal/SignalService.sol

21: 		    mapping(address addr => bool authorized) public isAuthorized;
```
[[21](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L21)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

14: 		    bool public migratingInbound;
```
[[14](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L14)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

52: 		    mapping(address btoken => bool blacklisted) public btokenBlacklist;
```
[[52](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L52)]



```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

55: 		    mapping(address instanceAddress => bool alreadyAttested) public addressRegistered;
```
[[55](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L55)]



```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

12: 		    mapping(bytes32 hash => bool claimed) public isClaimed;
```
[[12](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L12)]

</details>

---

### [G-16] Shortcircuit rules can be be used to optimize some gas usage

Some conditions may be reordered to save an `SLOAD` (**2100 gas**), as we avoid reading state variables when the first part of the condition fails (with `&&`), or succeeds (with `||`).

*There is 1 instance of this issue.*


```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

// @audit switch with this condition
// ctx.from != owner() || ctx.srcChainId != ownerChainId
46: 		        if (ctx.srcChainId != ownerChainId || ctx.from != owner()) {
```
[[46](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L46)]


---

### [G-17] Cache multiple accesses of a mapping/array

Consider using a local `storage` or `calldata` variable when accessing a mapping/array value multiple times.

This can be useful to avoid recalculating the mapping hash and/or the array offsets.

*There are 13 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

// @audit _serialNumIsRevoked on line 81
84: 		            _serialNumIsRevoked[index][serialNumBatch[i]] = true;

// @audit _serialNumIsRevoked[index] on line 96
99: 		            delete _serialNumIsRevoked[index][serialNumBatch[i]];

// @audit _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.PCK)] on line 268
271: 		                    certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.PCK)][certs[i]
272: 		                        .serialNumber];
```
[[84](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L84), [99](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L99), [271-272](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L271-L272)]



```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

// @audit proofReceipt on lines 168, 184
190: 		            delete proofReceipt[msgHash];
```
[[190](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L190)]



```solidity
File: packages/protocol/contracts/common/AddressManager.sol

// @audit __addresses on line 47
49: 		        __addresses[_chainId][_name] = _newAddress;
```
[[49](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressManager.sol#L49)]



```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

// @audit state.transitions on line 154
154: 		            ts_ = state.transitions[slot][blk_.verifiedTransitionId];
```
[[154](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L154)]



```solidity
File: packages/protocol/contracts/signal/SignalService.sol

// @audit topBlockId on line 247
248: 		            topBlockId[_chainId][_kind] = _blockId;
```
[[248](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L248)]



```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

// @audit recipients on line 137
142: 		        recipients[_recipient].grant = _grant;
```
[[142](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L142)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

// @audit canonicalToBridged on line 168
189: 		        canonicalToBridged[_ctoken.chainId][_ctoken.addr] = _btokenNew;

// @audit bridgedToCanonical on line 358
359: 		            ctoken_ = bridgedToCanonical[_token];
```
[[189](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L189), [359](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L359)]



```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

// @audit instances on lines 107, 109
111: 		            delete instances[idx];

// @audit instances on lines 235, 236
237: 		            && block.timestamp <= instances[id].validSince + INSTANCE_EXPIRY;
```
[[111](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L111), [237](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L237)]



```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

// @audit _approvals on line 116
119: 		        uint256 _approval = _approvals[version][_hash];
```
[[119](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L119)]

</details>

---

### [G-18] Redundant state variable getters

Getters for public state variables are automatically generated with public variables, so there is no need to code them manually, as it adds an unnecessary overhead.

*There are 2 instances of this issue.*


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

200: 		    function getBlockHash(uint64 _blockId) public view returns (bytes32) {
201: 		        if (_blockId >= block.number) return 0;
202: 		        if (_blockId + 256 >= block.number) return blockhash(_blockId);
203: 		        return l2Hashes[_blockId];
204: 		    }
```
[[200-204](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L200-L204)]



```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

43: 		    function getConfig() public view override returns (Config memory) {
44: 		        return customConfig;
45: 		    }
```
[[43-45](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L43-L45)]


---

### [G-19] Using `private` for constants saves gas

Saves deployment gas due to the compiler not having to create non-payable getter functions for deployment calldata, not having to store the bytes of the value outside of where it's used, and not adding another entry to the method ID table.

*There are 14 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

35: 		    uint8 public constant BLOCK_SYNC_THRESHOLD = 5;
```
[[35](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L35)]



```solidity
File: packages/protocol/contracts/libs/Lib4844.sol

10: 		    address public constant POINT_EVALUATION_PRECOMPILE_ADDRESS = address(0x0A);

13: 		    uint32 public constant FIELD_ELEMENTS_PER_BLOB = 4096;

16: 		    uint256 public constant BLS_MODULUS =
17: 		        52_435_875_175_126_190_479_447_740_508_185_965_837_690_552_500_527_637_822_603_658_699_938_581_184_513;
```
[[10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/Lib4844.sol#L10), [13](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/Lib4844.sol#L13), [16-17](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/Lib4844.sol#L16-L17)]



```solidity
File: packages/protocol/contracts/tokenvault/BaseNFTVault.sol

47: 		    bytes4 public constant ERC1155_INTERFACE_ID = 0xd9b67a26;

50: 		    bytes4 public constant ERC721_INTERFACE_ID = 0x80ac58cd;

53: 		    uint256 public constant MAX_TOKEN_PER_TXN = 10;
```
[[47](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L47), [50](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L50), [53](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L53)]



```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

30: 		    uint64 public constant INSTANCE_EXPIRY = 180 days;

34: 		    uint64 public constant INSTANCE_VALIDITY_DELAY = 1 days;
```
[[30](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L30), [34](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L34)]



```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

38: 		    uint256 public constant MAX_GAS_PAYING_PROVER = 50_000;
```
[[38](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L38)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

21: 		    uint256 public constant MAX_BYTES_PER_BLOB = 4096 * 32;
```
[[21](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L21)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

20: 		    bytes32 public constant RETURN_LIVENESS_BOND = keccak256("RETURN_LIVENESS_BOND");

23: 		    bytes32 public constant TIER_OP = bytes32("tier_optimistic");
```
[[20](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L20), [23](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L23)]



```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

11: 		    uint256 public constant MIN_NUM_GUARDIANS = 5;
```
[[11](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L11)]

</details>

---

### [G-20] require() or revert() statements that check input arguments should be at the top of the function

Checks that can be performed earlier should come before checks that involve state variables, function calls, and calculations. By doing these checks first, the function is able to revert before wasting a Gcoldsload (*2100 gas*) in a function that may ultimately revert.

*There are 4 instances of this issue.*


```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

// @audit expensive op on line 103
105: 		        if (_addressManager == address(0)) revert ZERO_ADDR_MANAGER();
```
[[105](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L105)]



```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

// @audit expensive op on line 120
121: 		        if (_taikoToken == address(0)) revert INVALID_PARAM();

// @audit expensive op on line 120
124: 		        if (_costToken == address(0)) revert INVALID_PARAM();

// @audit expensive op on line 120
127: 		        if (_sharedVault == address(0)) revert INVALID_PARAM();
```
[[121](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L121), [124](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L124), [127](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L127)]


---

### [G-21] Consider activating `via-ir` for deploying

The IR-based code generator was developed to make code generation more performant by enabling optimization passes that can be applied across functions.

It is possible to activate the IR-based code generator through the command line by using the flag `--via-ir` or by including the option `{"viaIR": true}`.

Keep in mind that compiling with this option may take longer. However, you can simply test it before deploying your code. If you find that it provides better performance, you can add the `--via-ir` flag to your deploy command.



---

### [G-22] Function calls should be cached instead of re-calling the function

Consider caching the result instead of re-calling the function when possible. Note: this also includes casts, which cost between 42-46 gas, depending on the type.

*There are 12 instances of this issue.*


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

// @audit blockhash(parentId) is duplicated on line 157
154: 		        l2Hashes[parentId] = blockhash(parentId);
```
[[154](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L154)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

// @audit der.nextSiblingOf(tbsPtr) is duplicated on line 111, 112, 127, 144, 157, 186
104: 		        tbsPtr = der.nextSiblingOf(tbsPtr);

// @audit der.firstChildOf(tbsPtr) is duplicated on line 130, 147, 161, 193, 194
115: 		            uint256 issuerPtr = der.firstChildOf(tbsPtr);

// @audit der.firstChildOf(issuerPtr) is duplicated on line 117
116: 		            issuerPtr = der.firstChildOf(issuerPtr);

// @audit der.firstChildOf(subjectPtr) is duplicated on line 149
148: 		            subjectPtr = der.firstChildOf(subjectPtr);

// @audit der.nextSiblingOf(sigPtr) is duplicated on line 176
167: 		            sigPtr = der.nextSiblingOf(sigPtr);

// @audit _trimBytes(der.bytesAt(sigPtr), 32) is duplicated on line 177
174: 		            bytes memory sigX = _trimBytes(der.bytesAt(sigPtr), 32);

// @audit der.bytesAt(sigPtr) is duplicated on line 177
174: 		            bytes memory sigX = _trimBytes(der.bytesAt(sigPtr), 32);

// @audit der.nextSiblingOf(extnValueOidPtr) is duplicated on line 318
312: 		                        uint256 pceidPtr = der.nextSiblingOf(extnValueOidPtr);

// @audit bytes2(svnValueBytes) is duplicated on line 360
359: 		                ? uint16(bytes2(svnValueBytes)) / 256
```
[[104](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L104), [115](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L115), [116](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L116), [148](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L148), [167](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L167), [174](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L174), [174](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L174), [312](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L312), [359](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L359)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

// @audit MemoryPointer.wrap(MemoryPointer.unwrap(_in.ptr) + offset) is duplicated on line 86
78: 		                    ptr: MemoryPointer.wrap(MemoryPointer.unwrap(_in.ptr) + offset)

// @audit MemoryPointer.unwrap(_in.ptr) is duplicated on line 86
78: 		                    ptr: MemoryPointer.wrap(MemoryPointer.unwrap(_in.ptr) + offset)
```
[[78](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L78), [78](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L78)]


---

### [G-23] Functions that revert when called by normal users can be `payable`

If a function modifier such as `onlyOwner` is used, the function will revert if a normal user tries to pay the function.

Marking the function as `payable` will lower the gas for legitimate callers, as the compiler will not include checks for whether a payment was provided.

The extra opcodes avoided are:

`CALLVALUE(2), DUP1(3), ISZERO(3), PUSH2(3), JUMPI(10), PUSH1(3), DUP1(3), REVERT(0), JUMPDEST(1), POP(2)`

which cost an average of about 21 gas per call to the function, in addition to the extra deployment cost.

*There are 37 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

65: 		    function setMrSigner(bytes32 _mrSigner, bool _trusted) external onlyOwner {

69: 		    function setMrEnclave(bytes32 _mrEnclave, bool _trusted) external onlyOwner {

73: 		    function addRevokedCertSerialNum(
74: 		        uint256 index,
75: 		        bytes[] calldata serialNumBatch
76: 		    )
77: 		        external
78: 		        onlyOwner

88: 		    function removeRevokedCertSerialNum(
89: 		        uint256 index,
90: 		        bytes[] calldata serialNumBatch
91: 		    )
92: 		        external
93: 		        onlyOwner

103: 		    function configureTcbInfoJson(
104: 		        string calldata fmspc,
105: 		        TCBInfoStruct.TCBInfo calldata tcbInfoInput
106: 		    )
107: 		        public
108: 		        onlyOwner

114: 		    function configureQeIdentityJson(EnclaveIdStruct.EnclaveId calldata qeIdentityInput)
115: 		        external
116: 		        onlyOwner

122: 		    function toggleLocalReportCheck() external onlyOwner {
```
[[65](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L65), [69](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L69), [73-78](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L73-L78), [88-93](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L88-L93), [103-108](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L103-L108), [114-116](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L114-L116), [122](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L122)]



```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

82: 		    function suspendMessages(
83: 		        bytes32[] calldata _msgHashes,
84: 		        bool _suspend
85: 		    )
86: 		        external
87: 		        onlyFromOwnerOrNamed("bridge_watchdog")

101: 		    function banAddress(
102: 		        address _addr,
103: 		        bool _ban
104: 		    )
105: 		        external
106: 		        onlyFromOwnerOrNamed("bridge_watchdog")
107: 		        nonReentrant
```
[[82-87](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L82-L87), [101-107](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L101-L107)]



```solidity
File: packages/protocol/contracts/common/AddressManager.sol

38: 		    function setAddress(
39: 		        uint64 _chainId,
40: 		        bytes32 _name,
41: 		        address _newAddress
42: 		    )
43: 		        external
44: 		        virtual
45: 		        onlyOwner
```
[[38-45](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressManager.sol#L38-L45)]



```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

58: 		    function __AddressResolver_init(address _addressManager) internal virtual onlyInitializing {
```
[[58](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressResolver.sol#L58)]



```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

95: 		    function __Essential_init(
96: 		        address _owner,
97: 		        address _addressManager
98: 		    )
99: 		        internal
100: 		        virtual
101: 		        onlyInitializing

114: 		    function _authorizeUpgrade(address) internal virtual override onlyOwner { }

116: 		    function _authorizePause(address) internal virtual onlyOwner { }
```
[[95-101](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L95-L101), [114](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L114), [116](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L116)]



```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

47: 		    function burn(address _from, uint256 _amount) public onlyOwner {

52: 		    function snapshot() public onlyFromOwnerOrNamed("snapshooter") {
```
[[47](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoToken.sol#L47), [52](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoToken.sol#L52)]



```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

60: 		    function __CrossChainOwned_init(
61: 		        address _owner,
62: 		        address _addressManager,
63: 		        uint64 _ownerChainId
64: 		    )
65: 		        internal
66: 		        virtual
67: 		        onlyInitializing
```
[[60-67](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L60-L67)]



```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

163: 		    function withdraw(
164: 		        address _token,
165: 		        address _to
166: 		    )
167: 		        external
168: 		        onlyFromOwnerOrNamed("withdrawer")
169: 		        nonReentrant
170: 		        whenNotPaused
```
[[163-170](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L163-L170)]



```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

25: 		    function setConfigAndExcess(
26: 		        Config memory _newConfig,
27: 		        uint64 _newGasExcess
28: 		    )
29: 		        external
30: 		        virtual
31: 		        onlyOwner
```
[[25-31](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L25-L31)]



```solidity
File: packages/protocol/contracts/signal/SignalService.sol

56: 		    function authorize(address _addr, bool _authorize) external onlyOwner {
```
[[56](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L56)]



```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

135: 		    function grant(address _recipient, Grant memory _grant) external onlyOwner {

150: 		    function void(address _recipient) external onlyOwner {
```
[[135](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L135), [150](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L150)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

66: 		    function mint(
67: 		        address _to,
68: 		        uint256 _tokenId,
69: 		        uint256 _amount
70: 		    )
71: 		        public
72: 		        nonReentrant
73: 		        whenNotPaused
74: 		        onlyFromNamed("erc1155_vault")

83: 		    function mintBatch(
84: 		        address _to,
85: 		        uint256[] memory _tokenIds,
86: 		        uint256[] memory _amounts
87: 		    )
88: 		        public
89: 		        nonReentrant
90: 		        whenNotPaused
91: 		        onlyFromNamed("erc1155_vault")

100: 		    function burn(
101: 		        address _account,
102: 		        uint256 _tokenId,
103: 		        uint256 _amount
104: 		    )
105: 		        public
106: 		        nonReentrant
107: 		        whenNotPaused
108: 		        onlyFromNamed("erc1155_vault")
```
[[66-74](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L66-L74), [83-91](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L83-L91), [100-108](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L100-L108)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

80: 		    function setSnapshoter(address _snapshooter) external onlyOwner {

85: 		    function snapshot() external onlyOwnerOrSnapshooter {
```
[[80](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L80), [85](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L85)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

36: 		    function changeMigrationStatus(
37: 		        address _migratingAddress,
38: 		        bool _migratingInbound
39: 		    )
40: 		        external
41: 		        nonReentrant
42: 		        whenNotPaused
43: 		        onlyFromOwnerOrNamed("erc20_vault")
```
[[36-43](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L36-L43)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

54: 		    function mint(
55: 		        address _account,
56: 		        uint256 _tokenId
57: 		    )
58: 		        public
59: 		        nonReentrant
60: 		        whenNotPaused
61: 		        onlyFromNamed("erc721_vault")

69: 		    function burn(
70: 		        address _account,
71: 		        uint256 _tokenId
72: 		    )
73: 		        public
74: 		        nonReentrant
75: 		        whenNotPaused
76: 		        onlyFromNamed("erc721_vault")
```
[[54-61](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L54-L61), [69-76](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L69-L76)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

148: 		    function changeBridgedToken(
149: 		        CanonicalERC20 calldata _ctoken,
150: 		        address _btokenNew
151: 		    )
152: 		        external
153: 		        nonReentrant
154: 		        whenNotPaused
155: 		        onlyOwner
```
[[148-155](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L148-L155)]



```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

90: 		    function addInstances(address[] calldata _instances)
91: 		        external
92: 		        onlyOwner

100: 		    function deleteInstances(uint256[] calldata _ids)
101: 		        external
102: 		        onlyFromOwnerOrNamed("rollup_watchdog")

139: 		    function verifyProof(
140: 		        Context calldata _ctx,
141: 		        TaikoData.Transition calldata _tran,
142: 		        TaikoData.TierProof calldata _proof
143: 		    )
144: 		        external
145: 		        onlyFromNamed("taiko")
```
[[90-92](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L90-L92), [100-102](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L100-L102), [139-145](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L139-L145)]



```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

53: 		    function setGuardians(
54: 		        address[] memory _newGuardians,
55: 		        uint8 _minGuardians
56: 		    )
57: 		        external
58: 		        onlyOwner
59: 		        nonReentrant
```
[[53-59](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L53-L59)]



```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

45: 		    function setConfig(
46: 		        uint64 _claimStart,
47: 		        uint64 _claimEnd,
48: 		        bytes32 _merkleRoot
49: 		    )
50: 		        external
51: 		        onlyOwner

56: 		    function __MerkleClaimable_init(
57: 		        uint64 _claimStart,
58: 		        uint64 _claimEnd,
59: 		        bytes32 _merkleRoot
60: 		    )
61: 		        internal
62: 		        onlyInitializing
```
[[45-51](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L45-L51), [56-62](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L56-L62)]

</details>

---

### [G-24] Caching global variables is more expensive than using the actual variable

It's better to not cache global variables, as their direct usage is cheaper (e.g. `msg.sender`).

*There is 1 instance of this issue.*


```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

93: 		        address taikoL1Address = msg.sender;
```
[[93](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L93)]


---

### [G-25] Add `unchecked` blocks for subtractions where the operands cannot underflow

There are some checks to avoid an underflow, so it's safe to use `unchecked` to have some gas savings.

*There are 7 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

// @audit check on line 275
276: 		                numL1Blocks = _l1BlockId - lastSyncedBlock;
```
[[276](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L276)]



```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

// @audit check on line 257
264: 		        return _amount * uint64(block.timestamp - _start) / _period;
```
[[264](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L264)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

// @audit check on line 262
265: 		        uint256 lengthDiff = n - expectedLength;
```
[[265](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L265)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

// @audit check on line 90
93: 		                    mask = ~(2 ** (8 * (32 - shortest + idx)) - 1);
```
[[93](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L93)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/Bytes.sol

// @audit check on line 92
95: 		        return slice(_bytes, _start, _bytes.length - _start);
```
[[95](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L95)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

// @audit check on line 166
190: 		            uint256 lenOfStrLen = prefix - 0xb7;

// @audit check on line 223
236: 		            uint256 lenOfListLen = prefix - 0xf7;
```
[[190](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L190), [236](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L236)]

</details>

---

### [G-26] Add `unchecked` blocks for divisions where the operands cannot overflow

`uint` divisions can't overflow, while `int` divisions can overflow only in [one specific case](https://docs.soliditylang.org/en/latest/types.html#division).

Consider adding an `unchecked` block to have some [gas savings](https://gist.github.com/DadeKuma/3bc597338ae774b8b3bd43280d55271f).

*There are 13 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

215: 		            ethDepositMaxFee: 1 ether / 10,
```
[[215](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L215)]



```solidity
File: packages/protocol/contracts/L2/Lib1559Math.sol

28: 		        return _ethQty(_gasExcess, _adjustmentFactor) / LibFixedPointMath.SCALING_FACTOR
29: 		            / _adjustmentFactor;

28: 		        return _ethQty(_gasExcess, _adjustmentFactor) / LibFixedPointMath.SCALING_FACTOR

41: 		        uint256 input = _gasExcess * LibFixedPointMath.SCALING_FACTOR / _adjustmentFactor;
```
[[28-29](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/Lib1559Math.sol#L28-L29), [28](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/Lib1559Math.sol#L28), [41](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/Lib1559Math.sol#L41)]



```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

197: 		        uint128 _amountUnlocked = amountUnlocked / 1e18; // divide first

264: 		        return _amount * uint64(block.timestamp - _start) / _period;
```
[[197](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L197), [264](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L264)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

359: 		                ? uint16(bytes2(svnValueBytes)) / 256
```
[[359](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L359)]



```solidity
File: packages/protocol/contracts/L1/gov/TaikoGovernor.sol

124: 		        return 1_000_000_000 ether / 10_000; // 0.01% of Taiko Token
```
[[124](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L124)]



```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

262: 		                || _config.ethDepositMaxFee > type(uint96).max / _config.ethDepositMaxCountPerBlock
```
[[262](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L262)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

117: 		        uint256 timeBasedAllowance = balance
118: 		            * (block.timestamp.min(claimEnd + withdrawalWindow) - claimEnd) / withdrawalWindow;
```
[[117-118](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L117-L118)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

155: 		            uint256 upperDigit = digits / 16;
```
[[155](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L155)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

39: 		            while (_len / i != 0) {

47: 		                out_[i] = bytes1(uint8((_len / (256 ** (lenLen - i))) % 256));
```
[[39](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L39), [47](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L47)]

</details>

---

### [G-27] Empty blocks should be removed or emit something

Some functions don't have a body: consider commenting why, or add some logic. Otherwise, refactor the code and remove these functions.

*There is 1 instance of this issue.*


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

70: 		    receive() external payable { }
```
[[70](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L70)]


---

### [G-28] Usage of `uints`/`ints` smaller than 32 bytes (256 bits) incurs overhead

Citing the [documentation](https://docs.soliditylang.org/en/latest/internals/layout_in_storage.html):

> When using elements that are smaller than 32 bytes, your contract’s gas usage may be higher.This is because the EVM operates on 32 bytes at a time.Therefore, if the element is smaller than that, the EVM must use more operations in order to reduce the size of the element from 32 bytes to the desired size.

For example, each operation involving a `uint8` costs an extra ** 22 - 28 gas ** (depending on whether the other operand is also a variable of type `uint8`) as compared to ones involving`uint256`, due to the compiler having to clear the higher bits of the memory word before operating on the`uint8`, as well as the associated stack operations of doing so.

Note that it might be beneficial to use reduced-size types when dealing with storage values because the compiler will pack multiple elements into one storage slot, but if not, it will have the opposite effect.

*There are 322 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

36: 		    uint8 internal constant INVALID_EXIT_CODE = 255;
```
[[36](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L36)]



```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

31: 		    uint128 public nextMessageId;

64: 		    modifier sameChain(uint64 _chainId) {

89: 		        uint64 _timestamp = _suspend ? type(uint64).max : uint64(block.timestamp);

168: 		        uint64 receivedAt = proofReceipt[msgHash].receivedAt;

230: 		        uint64 receivedAt = proofReceipt[msgHash].receivedAt;

392: 		    function isDestChainEnabled(uint64 _chainId)

541: 		    function _storeContext(bytes32 _msgHash, address _from, uint64 _srcChainId) private {

559: 		            uint64 srcChainId;

580: 		        uint64 _chainId,
```
[[31](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L31), [64](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L64), [89](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L89), [168](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L168), [230](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L230), [392](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L392), [541](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L541), [559](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L559), [580](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L580)]



```solidity
File: packages/protocol/contracts/bridge/IBridge.sol

19: 		        uint128 id;

24: 		        uint64 srcChainId;

26: 		        uint64 destChainId;

51: 		        uint64 receivedAt;

63: 		        uint64 srcChainId; // Source chain ID.
```
[[19](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/IBridge.sol#L19), [24](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/IBridge.sol#L24), [26](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/IBridge.sol#L26), [51](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/IBridge.sol#L51), [63](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/IBridge.sol#L63)]



```solidity
File: packages/protocol/contracts/common/AddressManager.sol

22: 		        uint64 indexed chainId, bytes32 indexed name, address newAddress, address oldAddress

39: 		        uint64 _chainId,

54: 		    function getAddress(uint64 _chainId, bytes32 _name) public view override returns (address) {
```
[[22](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressManager.sol#L22), [39](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressManager.sol#L39), [54](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressManager.sol#L54)]



```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

19: 		    error RESOLVER_ZERO_ADDR(uint64 chainId, bytes32 name);

44: 		        uint64 _chainId,

73: 		        uint64 _chainId,
```
[[19](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressResolver.sol#L19), [44](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressResolver.sol#L44), [73](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressResolver.sol#L73)]



```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

11: 		    uint8 private constant _FALSE = 1;

13: 		    uint8 private constant _TRUE = 2;

21: 		    uint8 private __reentry;

23: 		    uint8 private __paused;

119: 		    function _storeReentryLock(uint8 _reentry) internal virtual {

130: 		    function _loadReentryLock() internal view virtual returns (uint8 reentry_) {
```
[[11](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L11), [13](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L13), [21](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L21), [23](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L23), [119](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L119), [130](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L130)]



```solidity
File: packages/protocol/contracts/common/IAddressManager.sol

14: 		    function getAddress(uint64 _chainId, bytes32 _name) external view returns (address);
```
[[14](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/IAddressManager.sol#L14)]



```solidity
File: packages/protocol/contracts/common/IAddressResolver.sol

35: 		        uint64 _chainId,
```
[[35](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/IAddressResolver.sol#L35)]



```solidity
File: packages/protocol/contracts/L1/ITaikoL1.sol

27: 		    function proveBlock(uint64 _blockId, bytes calldata _input) external;

31: 		    function verifyBlocks(uint64 _maxBlocksToVerify) external;
```
[[27](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/ITaikoL1.sol#L27), [31](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/ITaikoL1.sol#L31)]



```solidity
File: packages/protocol/contracts/L1/TaikoData.sol

15: 		        uint64 chainId;

20: 		        uint64 blockMaxProposals;

22: 		        uint64 blockRingBufferSize;

24: 		        uint64 maxBlocksToVerifyPerProposal;

26: 		        uint32 blockMaxGasLimit;

28: 		        uint24 blockMaxTxListBytes;

30: 		        uint24 blobExpiry;

39: 		        uint96 livenessBond;

46: 		        uint64 ethDepositMinCountPerBlock;

48: 		        uint64 ethDepositMaxCountPerBlock;

50: 		        uint96 ethDepositMinAmount;

52: 		        uint96 ethDepositMaxAmount;

59: 		        uint8 blockSyncThreshold;

64: 		        uint16 tier;

65: 		        uint128 fee;

69: 		        uint16 tier;

83: 		        uint24 txListByteOffset;

84: 		        uint24 txListByteSize;

101: 		        uint64 id;

102: 		        uint32 gasLimit;

103: 		        uint64 timestamp; // slot 7

104: 		        uint64 l1Height;

105: 		        uint24 txListByteOffset;

106: 		        uint24 txListByteSize;

107: 		        uint16 minTier;

127: 		        uint96 validityBond;

129: 		        uint96 contestBond;

130: 		        uint64 timestamp; // slot 6 (90 bits)

131: 		        uint16 tier;

132: 		        uint8 contestations;

140: 		        uint96 livenessBond;

141: 		        uint64 blockId; // slot 3

142: 		        uint64 proposedAt; // timestamp

143: 		        uint64 proposedIn; // L1 block number

144: 		        uint32 nextTransitionId;

145: 		        uint32 verifiedTransitionId;

152: 		        uint96 amount;

153: 		        uint64 id;

162: 		        uint64 genesisHeight;

163: 		        uint64 genesisTimestamp;

164: 		        uint64 numEthDeposits;

165: 		        uint64 nextEthDepositToProcess;

169: 		        uint64 numBlocks;

170: 		        uint64 lastVerifiedBlockId;

172: 		        uint8 __reserved1;

173: 		        uint16 __reserved2;

174: 		        uint32 __reserved3;

175: 		        uint64 lastUnpausedAt;
```
[[15](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L15), [20](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L20), [22](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L22), [24](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L24), [26](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L26), [28](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L28), [30](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L30), [39](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L39), [46](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L46), [48](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L48), [50](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L50), [52](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L52), [59](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L59), [64](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L64), [65](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L65), [69](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L69), [83](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L83), [84](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L84), [101](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L101), [102](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L102), [103](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L103), [104](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L104), [105](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L105), [106](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L106), [107](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L107), [127](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L127), [129](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L129), [130](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L130), [131](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L131), [132](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L132), [140](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L140), [141](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L141), [142](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L142), [143](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L143), [144](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L144), [145](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L145), [152](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L152), [153](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L153), [162](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L162), [163](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L163), [164](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L164), [165](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L165), [169](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L169), [170](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L170), [172](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L172), [173](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L173), [174](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L174), [175](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L175)]



```solidity
File: packages/protocol/contracts/L1/TaikoEvents.sol

24: 		        uint96 livenessBond,

43: 		        uint16 tier,

44: 		        uint8 contestations

57: 		        uint96 validityBond,

58: 		        uint16 tier

71: 		        uint96 contestBond,

72: 		        uint16 tier
```
[[24](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoEvents.sol#L24), [43](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoEvents.sol#L43), [44](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoEvents.sol#L44), [57](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoEvents.sol#L57), [58](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoEvents.sol#L58), [71](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoEvents.sol#L71), [72](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoEvents.sol#L72)]



```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

76: 		        uint64 _blockId,

94: 		        uint8 maxBlocksToVerify = LibProving.proveBlock(state, config, this, meta, tran, proof);

100: 		    function verifyBlocks(uint64 _maxBlocksToVerify)

145: 		    function getBlock(uint64 _blockId)

150: 		        uint64 slot;

163: 		        uint64 _blockId,
```
[[76](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L76), [94](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L94), [100](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L100), [145](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L145), [150](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L150), [163](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L163)]



```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

16: 		    uint64 public ownerChainId;

19: 		    uint64 public nextTxId;

26: 		    event TransactionExecuted(uint64 indexed txId, bytes4 indexed selector);

42: 		        (uint64 txId, bytes memory txdata) = abi.decode(_data, (uint64, bytes));

63: 		        uint64 _ownerChainId
```
[[16](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L16), [19](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L19), [26](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L26), [42](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L42), [63](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L63)]



```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

27: 		        uint32 gasTargetPerL1Block;

28: 		        uint8 basefeeAdjustmentQuotient;

35: 		    uint8 public constant BLOCK_SYNC_THRESHOLD = 5;

47: 		    uint64 public gasExcess;

50: 		    uint64 public lastSyncedBlock;

57: 		    event Anchored(bytes32 parentHash, uint64 gasExcess);

74: 		        uint64 _l1ChainId,

75: 		        uint64 _gasExcess

110: 		        uint64 _l1BlockId,

111: 		        uint32 _parentGasUsed

186: 		        uint64 _l1BlockId,

187: 		        uint32 _parentGasUsed

200: 		    function getBlockHash(uint64 _blockId) public view returns (bytes32) {

254: 		        uint64 _l1BlockId,

255: 		        uint32 _parentGasUsed

259: 		        returns (uint256 basefee_, uint64 gasExcess_)
```
[[27](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L27), [28](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L28), [35](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L35), [47](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L47), [50](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L50), [57](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L57), [74](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L74), [75](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L75), [110](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L110), [111](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L111), [186](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L186), [187](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L187), [200](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L200), [254](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L254), [255](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L255), [259](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L259)]



```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

18: 		    event ConfigAndExcessChanged(Config config, uint64 gasExcess);

27: 		        uint64 _newGasExcess
```
[[18](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L18), [27](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L27)]



```solidity
File: packages/protocol/contracts/libs/Lib4844.sol

13: 		    uint32 public constant FIELD_ELEMENTS_PER_BLOB = 4096;
```
[[13](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/Lib4844.sol#L13)]



```solidity
File: packages/protocol/contracts/signal/ISignalService.sol

21: 		        uint64 chainId;

22: 		        uint64 blockId;

37: 		        uint64 indexed chainId,

38: 		        uint64 indexed blockId,

69: 		        uint64 _chainId,

71: 		        uint64 _blockId,

85: 		        uint64 _chainId,

106: 		        uint64 _chainId,

108: 		        uint64 _blockId,

123: 		        uint64 _chainId,

125: 		        uint64 _blockId

129: 		        returns (uint64 blockId_, bytes32 chainData_);

138: 		        uint64 _chainId,

140: 		        uint64 _blockId
```
[[21](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/ISignalService.sol#L21), [22](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/ISignalService.sol#L22), [37](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/ISignalService.sol#L37), [38](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/ISignalService.sol#L38), [69](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/ISignalService.sol#L69), [71](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/ISignalService.sol#L71), [85](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/ISignalService.sol#L85), [106](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/ISignalService.sol#L106), [108](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/ISignalService.sol#L108), [123](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/ISignalService.sol#L123), [125](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/ISignalService.sol#L125), [129](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/ISignalService.sol#L129), [138](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/ISignalService.sol#L138), [140](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/ISignalService.sol#L140)]



```solidity
File: packages/protocol/contracts/signal/SignalService.sol

69: 		        uint64 _chainId,

71: 		        uint64 _blockId,

84: 		        uint64 _chainId,

97: 		        uint64 chainId = _chainId;

138: 		        uint64 _chainId,

140: 		        uint64 _blockId,

159: 		        uint64 _chainId,

161: 		        uint64 _blockId

165: 		        returns (uint64 blockId_, bytes32 chainData_)

178: 		        uint64 _chainId,

180: 		        uint64 _blockId

195: 		        uint64 _chainId,

207: 		        uint64 _chainId,

236: 		        uint64 _chainId,

238: 		        uint64 _blockId,

273: 		        uint64 _chainId,

274: 		        uint64 _blockId,
```
[[69](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L69), [71](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L71), [84](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L84), [97](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L97), [138](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L138), [140](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L140), [159](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L159), [161](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L161), [165](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L165), [178](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L178), [180](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L180), [195](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L195), [207](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L207), [236](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L236), [238](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L238), [273](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L273), [274](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L274)]



```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

29: 		        uint128 amount;

31: 		        uint128 costPerToken;

34: 		        uint64 grantStart;

37: 		        uint64 grantCliff;

40: 		        uint32 grantPeriod;

43: 		        uint64 unlockStart;

46: 		        uint64 unlockCliff;

49: 		        uint32 unlockPeriod;

53: 		        uint128 amountWithdrawn;

54: 		        uint128 costPaid;

68: 		    uint128 public totalAmountGranted;

71: 		    uint128 public totalAmountVoided;

74: 		    uint128 public totalAmountWithdrawn;

77: 		    uint128 public totalCostPaid;

92: 		    event Voided(address indexed recipient, uint128 amount);

99: 		    event Withdrawn(address indexed recipient, address to, uint128 amount, uint128 cost);

99: 		    event Withdrawn(address indexed recipient, address to, uint128 amount, uint128 cost);

152: 		        uint128 amountVoided = _voidGrant(r.grant);

180: 		            uint128 amountOwned,

181: 		            uint128 amountUnlocked,

182: 		            uint128 amountWithdrawn,

183: 		            uint128 amountToWithdraw,

184: 		            uint128 costToWithdraw

197: 		        uint128 _amountUnlocked = amountUnlocked / 1e18; // divide first

211: 		        (,,, uint128 amountToWithdraw, uint128 costToWithdraw) = getMyGrantSummary(_recipient);

211: 		        (,,, uint128 amountToWithdraw, uint128 costToWithdraw) = getMyGrantSummary(_recipient);

225: 		    function _voidGrant(Grant storage _grant) private returns (uint128 amountVoided) {

226: 		        uint128 amountOwned = _getAmountOwned(_grant);

235: 		    function _getAmountOwned(Grant memory _grant) private view returns (uint128) {

239: 		    function _getAmountUnlocked(Grant memory _grant) private view returns (uint128) {

246: 		        uint128 _amount,

247: 		        uint64 _start,

248: 		        uint64 _cliff,

249: 		        uint64 _period

253: 		        returns (uint128)

273: 		    function _validateCliff(uint64 _start, uint64 _cliff, uint32 _period) private pure {

273: 		    function _validateCliff(uint64 _start, uint64 _cliff, uint32 _period) private pure {

273: 		    function _validateCliff(uint64 _start, uint64 _cliff, uint32 _period) private pure {
```
[[29](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L29), [31](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L31), [34](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L34), [37](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L37), [40](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L40), [43](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L43), [46](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L46), [49](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L49), [53](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L53), [54](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L54), [68](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L68), [71](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L71), [74](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L74), [77](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L77), [92](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L92), [99](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L99), [99](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L99), [152](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L152), [180](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L180), [181](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L181), [182](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L182), [183](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L183), [184](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L184), [197](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L197), [211](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L211), [211](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L211), [225](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L225), [226](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L226), [235](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L235), [239](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L239), [246](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L246), [247](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L247), [248](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L248), [249](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L249), [253](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L253), [273](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L273), [273](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L273), [273](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L273)]



```solidity
File: packages/protocol/contracts/tokenvault/BaseNFTVault.sol

13: 		        uint64 chainId;

25: 		        uint64 destChainId;

70: 		        uint64 indexed chainId,

90: 		        uint64 destChainId,

126: 		        uint64 srcChainId,
```
[[13](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L13), [25](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L25), [70](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L70), [90](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L90), [126](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L126)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

24: 		    uint8 private __srcDecimals;

57: 		        uint8 _decimals,

117: 		        returns (uint8)
```
[[24](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L24), [57](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L57), [117](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L117)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

24: 		        uint64 chainId;

26: 		        uint8 decimals;

33: 		        uint64 destChainId;

69: 		        uint8 ctokenDecimal

87: 		        uint8 ctokenDecimal

102: 		        uint64 destChainId,

130: 		        uint64 srcChainId,
```
[[24](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L24), [26](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L26), [33](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L33), [69](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L69), [87](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L87), [102](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L102), [130](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L130)]



```solidity
File: packages/protocol/contracts/verifiers/IVerifier.sol

14: 		        uint64 blockId;
```
[[14](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/IVerifier.sol#L14)]



```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

26: 		        uint64 validSince;

30: 		    uint64 public constant INSTANCE_EXPIRY = 180 days;

34: 		    uint64 public constant INSTANCE_VALIDITY_DELAY = 1 days;

154: 		        uint32 id = uint32(bytes4(Bytes.slice(_proof.data, 0, 4)));

204: 		        uint64 validSince = uint64(block.timestamp);
```
[[26](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L26), [30](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L30), [34](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L34), [154](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L154), [204](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L204)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/EnclaveIdStruct.sol

10: 		        uint16 isvprodid;

23: 		        uint16 isvsvn;
```
[[10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/EnclaveIdStruct.sol#L10), [23](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/EnclaveIdStruct.sol#L23)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

358: 		            uint16 svnValue = svnValueBytes.length < 2
```
[[358](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L358)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

189: 		        uint80 ixFirstContentByte;

190: 		        uint80 ixLastContentByte;

196: 		            uint8 lengthbytesLength = uint8(der[ix + 1] & 0x7F);
```
[[189](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L189), [190](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L190), [196](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L196)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

188: 		    function readUint8(bytes memory self, uint256 idx) internal pure returns (uint8 ret) {

198: 		    function readUint16(bytes memory self, uint256 idx) internal pure returns (uint16 ret) {

211: 		    function readUint32(bytes memory self, uint256 idx) internal pure returns (uint32 ret) {

332: 		        uint8 decoded;
```
[[188](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L188), [198](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L198), [211](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L211), [332](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L332)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

9: 		        uint16 yrs;

10: 		        uint8 mnths;

11: 		        uint8 dys;

12: 		        uint8 hrs;

13: 		        uint8 mins;

14: 		        uint8 secs;

15: 		        uint8 offset;

35: 		        uint16 year,

36: 		        uint8 month,

37: 		        uint8 day,

38: 		        uint8 hour,

39: 		        uint8 minute,

40: 		        uint8 second

48: 		        for (uint16 i = 1970; i < year; ++i) {

59: 		        for (uint8 i = 1; i < month; ++i) {

71: 		    function isLeapYear(uint16 year) internal pure returns (bool) {
```
[[9](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L9), [10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L10), [11](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L11), [12](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L12), [13](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L13), [14](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L14), [15](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L15), [35](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L35), [36](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L36), [37](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L37), [38](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L38), [39](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L39), [40](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L40), [48](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L48), [59](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L59), [71](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L71)]



```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

20: 		        uint64 expiry;

21: 		        uint64 maxBlockId;

22: 		        uint64 maxProposedIn;

166: 		        uint16 _tierId
```
[[20](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L20), [21](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L21), [22](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L22), [166](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L166)]



```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

83: 		            uint96 fee = uint96(_config.ethDepositMaxFee.min(block.basefee * _config.ethDepositGas));

84: 		            uint64 j = _state.slotA.nextEthDepositToProcess;

85: 		            uint96 totalFee;

93: 		                uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount;
```
[[83](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L83), [84](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L84), [85](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L85), [93](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L93)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

34: 		        uint96 livenessBond,
```
[[34](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L34)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

36: 		        uint96 validityBond,

37: 		        uint16 tier

50: 		        uint96 contestBond,

51: 		        uint16 tier

100: 		        returns (uint8 maxBlocksToVerify_)

115: 		        uint64 slot = _meta.id % _config.blockRingBufferSize;

129: 		        (uint32 tid, TaikoData.TransitionState storage ts) =

273: 		        uint64 slot

276: 		        returns (uint32 tid_, TaikoData.TransitionState storage ts_)

405: 		        uint32 _tid,
```
[[36](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L36), [37](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L37), [50](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L50), [51](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L51), [100](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L100), [115](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L115), [129](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L129), [273](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L273), [276](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L276), [405](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L405)]



```solidity
File: packages/protocol/contracts/L1/libs/LibUtils.sol

26: 		        uint64 _blockId,

38: 		        uint64 slot = _blockId % _config.blockRingBufferSize;

42: 		        uint32 tid = getTransitionId(_state, blk, slot, _parentHash);

55: 		        uint64 _blockId

59: 		        returns (TaikoData.Block storage blk_, uint64 slot_)

73: 		        uint64 _slot,

78: 		        returns (uint32 tid_)
```
[[26](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibUtils.sol#L26), [38](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibUtils.sol#L38), [42](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibUtils.sol#L42), [55](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibUtils.sol#L55), [59](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibUtils.sol#L59), [73](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibUtils.sol#L73), [78](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibUtils.sol#L78)]



```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

34: 		        uint16 tier,

35: 		        uint8 contestations

89: 		        uint64 _maxBlocksToVerify

100: 		        uint64 blockId = b.lastVerifiedBlockId;

102: 		        uint64 slot = blockId % _config.blockRingBufferSize;

107: 		        uint32 tid = blk.verifiedTransitionId;

117: 		        uint64 numBlocksVerified;

213: 		                uint64 lastVerifiedBlockId = b.lastVerifiedBlockId + numBlocksVerified;

227: 		        uint64 _lastVerifiedBlockId,

234: 		        (uint64 lastSyncedBlock,) = signalService.getSyncedChainData(
```
[[34](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L34), [35](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L35), [89](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L89), [100](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L100), [102](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L102), [107](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L107), [117](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L117), [213](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L213), [227](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L227), [234](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L234)]



```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

27: 		    uint32 public version;

30: 		    uint32 public minGuardians;

37: 		    event GuardiansUpdated(uint32 version, address[] guardians);

55: 		        uint8 _minGuardians
```
[[27](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L27), [30](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L30), [37](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L37), [55](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L55)]



```solidity
File: packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol

20: 		    function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {

54: 		    function getMinTier(uint256) public pure override returns (uint16) {
```
[[20](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L20), [54](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L54)]



```solidity
File: packages/protocol/contracts/L1/tiers/ITierProvider.sol

10: 		        uint96 validityBond;

11: 		        uint96 contestBond;

12: 		        uint24 cooldownWindow; // in minutes

13: 		        uint16 provingWindow; // in minutes

14: 		        uint8 maxBlocksToVerifyPerProof;

22: 		    function getTier(uint16 tierId) external view returns (Tier memory);

33: 		    function getMinTier(uint256 rand) external view returns (uint16);

39: 		    uint16 public constant TIER_OPTIMISTIC = 100;

42: 		    uint16 public constant TIER_SGX = 200;

45: 		    uint16 public constant TIER_SGX_ZKVM = 300;

48: 		    uint16 public constant TIER_GUARDIAN = 1000;
```
[[10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L10), [11](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L11), [12](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L12), [13](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L13), [14](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L14), [22](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L22), [33](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L33), [39](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L39), [42](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L42), [45](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L45), [48](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L48)]



```solidity
File: packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol

20: 		    function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {

66: 		    function getMinTier(uint256 _rand) public pure override returns (uint16) {
```
[[20](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L20), [66](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L66)]



```solidity
File: packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol

20: 		    function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {

66: 		    function getMinTier(uint256 _rand) public pure override returns (uint16) {
```
[[20](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L20), [66](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L66)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

29: 		        uint64 _claimStart,

30: 		        uint64 _claimEnd,

69: 		        (address delegatee, uint256 nonce, uint256 expiry, uint8 v, bytes32 r, bytes32 s) =
```
[[29](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L29), [30](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L30), [69](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L69)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

28: 		    uint64 public withdrawalWindow;

56: 		        uint64 _claimStart,

57: 		        uint64 _claimEnd,

61: 		        uint64 _withdrawalWindow
```
[[28](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L28), [56](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L56), [57](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L57), [61](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L61)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

27: 		        uint64 _claimStart,

28: 		        uint64 _claimEnd,
```
[[27](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L27), [28](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L28)]



```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

18: 		    uint64 public claimStart;

21: 		    uint64 public claimEnd;

46: 		        uint64 _claimStart,

47: 		        uint64 _claimEnd,

57: 		        uint64 _claimStart,

58: 		        uint64 _claimEnd,

90: 		    function _setConfig(uint64 _claimStart, uint64 _claimEnd, bytes32 _merkleRoot) private {

90: 		    function _setConfig(uint64 _claimStart, uint64 _claimEnd, bytes32 _merkleRoot) private {
```
[[18](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L18), [21](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L21), [46](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L46), [47](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L47), [57](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L57), [58](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L58), [90](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L90), [90](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L90)]



```solidity
File: packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol

29: 		        uint16 _maxCopy,
```
[[29](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L29)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

106: 		        uint32 totalQuoteSize = 48 // header

249: 		        uint16 isvProdIdPackBE = (enclaveReport.isvProdId >> 8) | (enclaveReport.isvProdId << 8);

250: 		        uint16 isvSvnPackBE = (enclaveReport.isvSvn >> 8) | (enclaveReport.isvSvn << 8);
```
[[106](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L106), [249](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L249), [250](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L250)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol

26: 		        uint16 isvProdId;

27: 		        uint16 isvSvn;

34: 		        uint16 parsedDataSize;

39: 		        uint16 certType;

43: 		        uint32 certDataSize;
```
[[26](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L26), [27](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L27), [34](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L34), [39](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L39), [43](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L43)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

30: 		    uint8 internal constant PREFIX_EXTENSION_EVEN = 0;

33: 		    uint8 internal constant PREFIX_EXTENSION_ODD = 1;

36: 		    uint8 internal constant PREFIX_LEAF_EVEN = 2;

39: 		    uint8 internal constant PREFIX_LEAF_ODD = 3;

134: 		                    uint8 branchKey = uint8(key[currentKeyIndex]);

141: 		                uint8 prefix = uint8(path[0]);

142: 		                uint8 offset = 2 - (prefix % 2);
```
[[30](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L30), [33](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L33), [36](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L36), [39](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L39), [134](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L134), [141](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L141), [142](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L142)]

</details>

---

### [G-29] Stack variable cost less while used in emitting event

Using a stack variable instead of a state variable is cheaper when emitting an event.

*There are 7 instances of this issue.*


```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

// @audit nextTxId++
53: 		        emit TransactionExecuted(nextTxId++, bytes4(txdata));
```
[[53](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L53)]



```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

// @audit gasExcess
157: 		        emit Anchored(blockhash(parentId), gasExcess);
```
[[157](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L157)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

// @audit migratingAddress
63: 		            emit MigratedTo(migratingAddress, _account, _amount);

// @audit migratingAddress
80: 		            emit MigratedTo(migratingAddress, _account, _amount);
```
[[63](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L63), [80](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L80)]



```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

// @audit instances[idx].addr
109: 		            emit InstanceDeleted(idx, instances[idx].addr);

// @audit nextInstanceId
220: 		            emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);
```
[[109](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L109), [220](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220)]



```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

// @audit version
95: 		        emit GuardiansUpdated(version, _newGuardians);
```
[[95](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L95)]


---

### [G-30] Redundant `event` fields can be removed

Some parameters (`block.timestamp` and `block.number`) are added to event information by default so re-adding them wastes gas, as they are already included.

*There is 1 instance of this issue.*


```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

230: 		        emit InstanceAdded(id, newInstance, oldInstance, block.timestamp);
```
[[230](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L230)]


---

### [G-31] Using pre instead of post increments/decrements

Pre increments/decrements (`++i/--i`) are cheaper than post increments/decrements (`i++/i--`): it saves 6 gas per expression.

*There are 7 instances of this issue.*


```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

222: 		            nextInstanceId++;
```
[[222](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L222)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

46: 		            for (i = 1; i <= lenLen; i++) {

59: 		        for (; i < 32; i++) {

66: 		        for (uint256 j = 0; j < out_.length; j++) {

67: 		            out_[j] = b[i++];

40: 		                lenLen++;
```
[[46](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L46), [59](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L59), [66](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66), [67](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L67), [40](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L40)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

85: 		        for (uint256 i = 0; i < proof.length; i++) {
```
[[85](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85)]


---

### [G-32] `>=`/`<=` costs less gas than `>`/`<`

The compiler uses opcodes `GT` and `ISZERO` for code that uses `>`, but only requires `LT` for `>=`. A similar behaviour applies for `>`, which uses opcodes `LT` and `ISZERO`, but only requires `GT` for `<=`.

*There are 130 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

80: 		        for (uint256 i; i < serialNumBatch.length; ++i) {

95: 		        for (uint256 i; i < serialNumBatch.length; ++i) {

191: 		        for (uint256 i; i < enclaveId.tcbLevels.length; ++i) {

214: 		        for (uint256 i; i < tcb.tcbLevels.length; ++i) {

240: 		        for (uint256 i; i < CPUSVN_LENGTH; ++i) {

241: 		            if (pckCpuSvns[i] < tcbCpuSvns[i]) {

259: 		        for (uint256 i; i < n; ++i) {

280: 		                block.timestamp > certs[i].notBefore && block.timestamp < certs[i].notAfter;

280: 		                block.timestamp > certs[i].notBefore && block.timestamp < certs[i].notAfter;

420: 		            for (uint256 i; i < 3; ++i) {
```
[[80](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L80), [95](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L95), [191](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L191), [214](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L214), [240](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L240), [241](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L241), [259](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L259), [280](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L280), [280](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L280), [420](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L420)]



```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

90: 		        for (uint256 i; i < _msgHashes.length; ++i) {
```
[[90](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L90)]



```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

59: 		        if (block.chainid > type(uint64).max) {
```
[[59](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressResolver.sol#L59)]



```solidity
File: packages/protocol/contracts/L2/Lib1559Math.sol

42: 		        if (input > LibFixedPointMath.MAX_EXP_INPUT) {
```
[[42](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/Lib1559Math.sol#L42)]



```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

82: 		        if (block.chainid <= 1 || block.chainid > type(uint64).max) {

145: 		        if (_l1BlockId > lastSyncedBlock + BLOCK_SYNC_THRESHOLD) {

234: 		            for (uint256 i; i < 255 && _blockId >= i + 1; ++i) {

262: 		        if (gasExcess > 0) {

275: 		            if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {

275: 		            if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {

279: 		            if (numL1Blocks > 0) {

281: 		                excess = excess > issuance ? excess - issuance : 1;
```
[[82](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L82), [145](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L145), [234](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L234), [262](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L262), [275](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L275), [275](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L275), [279](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L279), [281](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L281)]



```solidity
File: packages/protocol/contracts/libs/LibMath.sol

13: 		        return _a > _b ? _b : _a;

21: 		        return _a > _b ? _a : _b;
```
[[13](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibMath.sol#L13), [21](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibMath.sol#L21)]



```solidity
File: packages/protocol/contracts/signal/SignalService.sol

104: 		        for (uint256 i; i < hopProofs.length; ++i) {

120: 		            bool isFullProof = hop.accountProof.length > 0;

247: 		        if (topBlockId[_chainId][_kind] < _blockId) {
```
[[104](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L104), [120](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L120), [247](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L247)]



```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

275: 		            if (_cliff > 0) revert INVALID_GRANT();

277: 		            if (_cliff > 0 && _cliff <= _start) revert INVALID_GRANT();
```
[[275](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L275), [277](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L277)]



```solidity
File: packages/protocol/contracts/tokenvault/BaseNFTVault.sol

145: 		        if (_op.tokenIds.length > MAX_TOKEN_PER_TXN) {
```
[[145](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L145)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

47: 		        for (uint256 i; i < _op.amounts.length; ++i) {

251: 		                for (uint256 i; i < _op.tokenIds.length; ++i) {

269: 		                for (uint256 i; i < _op.tokenIds.length; ++i) {
```
[[47](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L47), [251](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L251), [269](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L269)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

34: 		        for (uint256 i; i < _op.tokenIds.length; ++i) {

170: 		            for (uint256 i; i < _tokenIds.length; ++i) {

175: 		            for (uint256 i; i < _tokenIds.length; ++i) {

197: 		                for (uint256 i; i < _op.tokenIds.length; ++i) {

210: 		                for (uint256 i; i < _op.tokenIds.length; ++i) {
```
[[34](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L34), [170](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L170), [175](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L175), [197](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L197), [210](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L210)]



```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

104: 		        for (uint256 i; i < _ids.length; ++i) {

210: 		        for (uint256 i; i < _instances.length; ++i) {
```
[[104](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L104), [210](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

54: 		        for (uint256 i; i < size; ++i) {

56: 		            if (i > 0) {

244: 		        for (uint256 i; i < split.length; ++i) {

323: 		                    if (extnValuePtr.ixl() < extnValueParentPtr.ixl()) {

333: 		            if (tbsPtr.ixl() < tbsParentPtr.ixl()) {

354: 		        for (uint256 i; i < SGX_TCB_CPUSVN_SIZE + 1; ++i) {

358: 		            uint16 svnValue = svnValueBytes.length < 2
```
[[54](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L54), [56](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L56), [244](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L244), [323](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L323), [333](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L333), [354](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L354), [358](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L358)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

69: 		        if (otherlen < len) {

80: 		        for (uint256 idx = 0; idx < shortest; idx += 32) {

90: 		                if (shortest > 32) {

333: 		        for (uint256 i; i < len; ++i) {
```
[[69](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L69), [80](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L80), [90](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L90), [333](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L333)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

140: 		        for (uint256 i = 2; i < 2 + paddingLen; ++i) {

152: 		            for (uint256 i; i < digestAlgoWithParamLen; ++i) {

158: 		            for (uint256 i; i < digestAlgoWithParamLen; ++i) {

174: 		        for (uint256 i; i < _sha256.length; ++i) {

273: 		        for (uint256 i = 2; i < 2 + paddingLen; ++i) {

283: 		        for (uint256 i; i < sha1Prefix.length; ++i) {

290: 		        for (uint256 i; i < _sha1.length; ++i) {
```
[[140](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L140), [152](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L152), [158](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L158), [174](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L174), [273](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L273), [283](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L283), [290](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L290)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

18: 		            if (uint8(x509Time[0]) - 48 < 5) yrs += 2000;

48: 		        for (uint16 i = 1970; i < year; ++i) {

59: 		        for (uint8 i = 1; i < month; ++i) {
```
[[18](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L18), [48](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L48), [59](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L59)]



```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

82: 		            block.timestamp > assignment.expiry

85: 		                || assignment.maxBlockId != 0 && _meta.id > assignment.maxBlockId

86: 		                || assignment.maxProposedIn != 0 && block.number > assignment.maxProposedIn

125: 		        if (address(this).balance > 0) {

172: 		        for (uint256 i; i < _tierFees.length; ++i) {
```
[[82](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L82), [85](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L85), [86](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L86), [125](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L125), [172](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L172)]



```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

78: 		        if (numPending < _config.ethDepositMinCountPerBlock) {

86: 		            for (uint256 i; i < deposits_.length;) {

93: 		                uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount;

140: 		                && _state.slotA.numEthDeposits - _state.slotA.nextEthDepositToProcess
141: 		                    < _config.ethDepositRingBufferSize - 1;

150: 		        if (_amount > type(uint96).max) revert L1_INVALID_ETH_DEPOSIT();
```
[[78](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L78), [86](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L86), [93](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L93), [140-141](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L140-L141), [150](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L150)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

171: 		            if (uint256(params.txListByteOffset) + params.txListByteSize > MAX_BYTES_PER_BLOB) {

195: 		        if (meta_.txListByteSize == 0 || meta_.txListByteSize > _config.blockMaxTxListBytes) {

244: 		            for (uint256 i; i < params.hookCalls.length; ++i) {

296: 		        return _state.reusableBlobs[_blobHash] + _config.blobExpiry > block.timestamp;
```
[[171](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L171), [195](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L195), [244](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L244), [296](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L296)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

134: 		        if (_proof.tier == 0 || _proof.tier < _meta.minTier || _proof.tier < ts.tier) {

134: 		        if (_proof.tier == 0 || _proof.tier < _meta.minTier || _proof.tier < ts.tier) {

192: 		            bool returnLivenessBond = blk.livenessBond > 0 && _proof.data.length == 32

203: 		        if (_proof.tier > ts.tier) {

381: 		            if (reward > _tier.validityBond) {
```
[[134](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L134), [134](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L134), [192](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L192), [203](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L203), [381](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L381)]



```solidity
File: packages/protocol/contracts/L1/libs/LibUtils.sol

34: 		        if (_blockId < b.lastVerifiedBlockId || _blockId >= b.numBlocks) {
```
[[34](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibUtils.sol#L34)]



```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

127: 		            while (blockId < b.numBlocks && numBlocksVerified < _maxBlocksToVerify) {

127: 		            while (blockId < b.numBlocks && numBlocksVerified < _maxBlocksToVerify) {

152: 		                        uint256(ITierProvider(tierProvider).getTier(ts.tier).cooldownWindow) * 60
153: 		                            + uint256(ts.timestamp).max(_state.slotB.lastUnpausedAt) > block.timestamp

212: 		            if (numBlocksVerified > 0) {

238: 		        if (_lastVerifiedBlockId > lastSyncedBlock + _config.blockSyncThreshold) {

251: 		                || _config.blockMaxTxListBytes > 128 * 1024 // calldata up to 128K

256: 		            || _config.ethDepositMaxCountPerBlock > 32

257: 		                || _config.ethDepositMaxCountPerBlock < _config.ethDepositMinCountPerBlock

260: 		                || _config.ethDepositMaxAmount > type(uint96).max || _config.ethDepositGas == 0

262: 		                || _config.ethDepositMaxFee > type(uint96).max / _config.ethDepositMaxCountPerBlock
```
[[127](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L127), [127](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L127), [152-153](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L152-L153), [212](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L212), [238](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L238), [251](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L251), [256](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L256), [257](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L257), [260](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L260), [262](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L262)]



```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

63: 		        if (_newGuardians.length < MIN_NUM_GUARDIANS || _newGuardians.length > type(uint8).max) {

63: 		        if (_newGuardians.length < MIN_NUM_GUARDIANS || _newGuardians.length > type(uint8).max) {

68: 		        if (_minGuardians < (_newGuardians.length + 1) >> 1 || _minGuardians > _newGuardians.length)

68: 		        if (_minGuardians < (_newGuardians.length + 1) >> 1 || _minGuardians > _newGuardians.length)

74: 		        for (uint256 i; i < guardians.length; ++i) {

80: 		        for (uint256 i = 0; i < _newGuardians.length; ++i) {

133: 		            for (uint256 i; i < guardiansLength; ++i) {
```
[[63](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L63), [63](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L63), [68](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L68), [68](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L68), [74](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L74), [80](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L80), [133](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L133)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

40: 		        if (claimEnd > block.timestamp || claimEnd + withdrawalWindow < block.timestamp) {

40: 		        if (claimEnd > block.timestamp || claimEnd + withdrawalWindow < block.timestamp) {

114: 		        if (block.timestamp < claimEnd) return (balance, 0);
```
[[40](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L40), [40](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L40), [114](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L114)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

59: 		        for (uint256 i; i < tokenIds.length; ++i) {
```
[[59](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59)]



```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

35: 		            merkleRoot == 0x0 || claimStart == 0 || claimEnd == 0 || claimStart > block.timestamp

36: 		                || claimEnd < block.timestamp
```
[[35](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L35), [36](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L36)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

153: 		        for (uint256 i; i < encoded.length; ++i) {

218: 		        if (cert.certType < 1 || cert.certType > 5) {

218: 		        if (cert.certType < 1 || cert.certType > 5) {

281: 		        for (uint256 i; i < 3; ++i) {
```
[[153](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L153), [218](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L218), [218](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L218), [281](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L281)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

38: 		            _in.length > 0,

74: 		        while (offset < _in.length) {

153: 		            _in.length > 0,

173: 		                _in.length > strLen,

193: 		                _in.length > lenOfStrLen,

213: 		                strLen > 55,

218: 		                _in.length > lenOfStrLen + strLen,

229: 		                _in.length > listLen,

239: 		                _in.length > lenOfListLen,

259: 		                listLen > 55,

264: 		                _in.length > lenOfListLen + listLen,
```
[[38](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L38), [74](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L74), [153](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L153), [173](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L173), [193](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L193), [213](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L213), [218](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L218), [229](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L229), [239](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L239), [259](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L259), [264](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L264)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

14: 		        if (_in.length == 1 && uint8(_in[0]) < 128) {

33: 		        if (_len < 56) {

59: 		        for (; i < 32; i++) {

66: 		        for (uint256 j = 0; j < out_.length; j++) {
```
[[14](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L14), [33](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L33), [59](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L59), [66](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

77: 		        require(_key.length > 0, "MerkleTrie: empty key");

85: 		        for (uint256 i = 0; i < proof.length; i++) {

120: 		                        value_.length > 0,

173: 		                        value_.length > 0,

208: 		        for (uint256 i = 0; i < length;) {

221: 		        id_ = _node.length < 32 ? RLPReader.readRawBytes(_node) : RLPReader.readBytes(_node);

243: 		        uint256 max = (_a.length < _b.length) ? _a.length : _b.length;

244: 		        for (; shared_ < max && _a[shared_] == _b[shared_];) {
```
[[77](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L77), [85](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85), [120](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L120), [173](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L173), [208](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L208), [221](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L221), [243](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L243), [244](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L244)]

</details>

---

### [G-33] `internal` functions only called once can be inlined to save gas

Consider removing the following internal functions, and put the logic directly where they are called, as they are called only once.

*There are 20 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

126: 		    function _attestationTcbIsValid(TCBInfoStruct.TCBStatus status)
```
[[126](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L126)]



```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

109: 		    function __Essential_init(address _owner) internal virtual {
```
[[109](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L109)]



```solidity
File: packages/protocol/contracts/libs/LibAddress.sol

42: 		    function sendEther(address _to, uint256 _amount) internal {
```
[[42](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibAddress.sol#L42)]



```solidity
File: packages/protocol/contracts/signal/SignalService.sol

206: 		    function _verifyHopProof(
```
[[206](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L206)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

97: 		    function _mintToken(address _account, uint256 _amount) internal virtual;

99: 		    function _burnToken(address _from, uint256 _amount) internal virtual;
```
[[97](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L97), [99](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L99)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

56: 		    function compare(
```
[[56](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L56)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

43: 		    function pkcs1Sha256(

212: 		    function pkcs1Sha1(
```
[[43](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L43), [212](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L212)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

34: 		    function toUnixTimestamp(
```
[[34](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L34)]



```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

122: 		    function canDepositEthToL2(
```
[[122](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L122)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

287: 		    function isBlobReusable(
```
[[287](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L287)]



```solidity
File: packages/protocol/contracts/L1/libs/LibUtils.sol

70: 		    function getTransitionId(
```
[[70](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibUtils.sol#L70)]



```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

77: 		    function _verifyMerkleProof(
```
[[77](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L77)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/Bytes.sol

91: 		    function slice(bytes memory _bytes, uint256 _start) internal pure returns (bytes memory) {
```
[[91](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L91)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

267: 		    function parseCerificationChainBytes(
```
[[267](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L267)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

102: 		    function readList(bytes memory _in) internal pure returns (RLPItem[] memory out_) {

128: 		    function readBytes(bytes memory _in) internal pure returns (bytes memory out_) {
```
[[102](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L102), [128](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L128)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

13: 		    function writeBytes(bytes memory _in) internal pure returns (bytes memory out_) {
```
[[13](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L13)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

68: 		    function get(
```
[[68](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L68)]

</details>

---

### [G-34] Inline `modifiers` that are only used once, to save gas

Consider removing the following modifiers, and put the logic directly in the function where they are used, as they are used only once.

*There are 5 instances of this issue.*


```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

53: 		    modifier whenPaused() {
54: 		        if (!paused()) revert INVALID_PAUSE_STATUS();
55: 		        _;
56: 		    }

58: 		    modifier whenNotPaused() {
59: 		        if (paused()) revert INVALID_PAUSE_STATUS();
60: 		        _;
61: 		    }
```
[[53-56](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L53-L56), [58-61](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L58-L61)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

37: 		    modifier onlyOwnerOrSnapshooter() {
38: 		        if (msg.sender != owner() && msg.sender != snapshooter) {
39: 		            revert BTOKEN_UNAUTHORIZED();
40: 		        }
41: 		        _;
42: 		    }
```
[[37-42](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L37-L42)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

39: 		    modifier ongoingWithdrawals() {
40: 		        if (claimEnd > block.timestamp || claimEnd + withdrawalWindow < block.timestamp) {
41: 		            revert WITHDRAWALS_NOT_ONGOING();
42: 		        }
43: 		        _;
44: 		    }
```
[[39-44](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L39-L44)]



```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

33: 		    modifier ongoingClaim() {
34: 		        if (
35: 		            merkleRoot == 0x0 || claimStart == 0 || claimEnd == 0 || claimStart > block.timestamp
36: 		                || claimEnd < block.timestamp
37: 		        ) revert CLAIM_NOT_ONGOING();
38: 		        _;
39: 		    }
```
[[33-39](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L33-L39)]


---

### [G-35] `private` functions only called once can be inlined to save gas

Consider removing the following private functions, and put the logic directly where they are called, as they are called only once.

*There are 41 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

162: 		    function _verify(bytes calldata quote) private view returns (bool, bytes memory) {

175: 		    function _verifyQEReportWithIdentity(V3Struct.EnclaveReport memory quoteEnclaveReport)

206: 		    function _checkTcbLevels(

229: 		    function _isCpuSvnHigherOrGreater(

248: 		    function _verifyCertChain(IPEMCertChainLib.ECSha256Certificate[] memory certs)

303: 		    function _enclaveReportSigVerification(
```
[[162](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L162), [175](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L175), [206](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L206), [229](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L229), [248](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L248), [303](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L303)]



```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

555: 		    function _loadContext() private view returns (Context memory) {
```
[[555](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L555)]



```solidity
File: packages/protocol/contracts/L2/Lib1559Math.sol

33: 		    function _ethQty(
```
[[33](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/Lib1559Math.sol#L33)]



```solidity
File: packages/protocol/contracts/signal/SignalService.sol

271: 		    function _cacheChainData(
```
[[271](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L271)]



```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

225: 		    function _voidGrant(Grant storage _grant) private returns (uint128 amountVoided) {

239: 		    function _getAmountUnlocked(Grant memory _grant) private view returns (uint128) {

267: 		    function _validateGrant(Grant memory _grant) private pure {
```
[[225](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L225), [239](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L239), [267](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L267)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

240: 		    function _handleMessage(

288: 		    function _getOrDeployBridgedToken(CanonicalNFT memory _ctoken)

303: 		    function _deployBridgedToken(CanonicalNFT memory _ctoken) private returns (address btoken_) {
```
[[240](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L240), [288](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L288), [303](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L303)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

348: 		    function _handleMessage(

391: 		    function _getOrDeployBridgedToken(CanonicalERC20 memory ctoken)

407: 		    function _deployBridgedToken(CanonicalERC20 memory ctoken) private returns (address btoken) {
```
[[348](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L348), [391](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L391), [407](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L407)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

187: 		    function _handleMessage(

224: 		    function _getOrDeployBridgedToken(CanonicalNFT memory _ctoken)

240: 		    function _deployBridgedToken(CanonicalNFT memory _ctoken) private returns (address btoken_) {
```
[[187](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L187), [224](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L224), [240](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L240)]



```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

226: 		    function _replaceInstance(uint256 id, address oldInstance, address newInstance) private {

233: 		    function _isInstanceValid(uint256 id, address instance) private view returns (bool) {
```
[[226](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L226), [233](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L233)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

216: 		    function _removeHeadersAndFooters(string memory pemData)

269: 		    function _findPckTcbInfo(

341: 		    function _findTcb(
```
[[216](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L216), [269](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L269), [341](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L341)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

272: 		    function memcpy(uint256 dest, uint256 src, uint256 len) private pure {
```
[[272](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L272)]



```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

164: 		    function _getProverFee(
```
[[164](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L164)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

299: 		    function _isProposerPermitted(
```
[[299](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L299)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

269: 		    function _createTransition(

350: 		    function _overrideWithHigherProof(

401: 		    function _checkProverPermission(
```
[[269](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L269), [350](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L350), [401](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L401)]



```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

224: 		    function _syncChainData(

245: 		    function _isConfigValid(TaikoData.Config memory _config) private view returns (bool) {
```
[[224](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L224), [245](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L245)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

165: 		    function parseAndVerifyHeader(bytes memory rawHeader)

203: 		    function parseAuthDataAndVerifyCertType(
```
[[165](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L165), [203](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L203)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

32: 		    function _writeLength(uint256 _len, uint256 _offset) private pure returns (bytes memory out_) {

55: 		    function _toBinary(uint256 _x) private pure returns (bytes memory out_) {
```
[[32](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L32), [55](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L55)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

205: 		    function _parseProof(bytes[] memory _proof) private pure returns (TrieNode[] memory proof_) {

227: 		    function _getNodePath(TrieNode memory _node) private pure returns (bytes memory nibbles_) {

235: 		    function _getSharedNibbleLength(
```
[[205](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L205), [227](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L227), [235](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L235)]

</details>

---

### [G-36] Use multiple revert checks to save gas

Splitting the conditions into two separate checks [saves](https://gist.github.com/IllIllI000/7e25b0fca6bd9d57d9b9bcb9d2018959) 2 gas per split.

*There are 37 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

124: 		        if (_message.srcOwner == address(0) || _message.destOwner == address(0)) {
125: 		            revert B_INVALID_USER();
126: 		        }

260: 		            if (_message.gasLimit == 0 && msg.sender != _message.destOwner) {
261: 		                revert B_PERMISSION_DENIED();
262: 		            }

321: 		        if (_message.gasLimit == 0 || _isLastAttempt) {
322: 		            if (msg.sender != _message.destOwner) revert B_PERMISSION_DENIED();
323: 		        }

405: 		        if (ctx_.msgHash == 0 || ctx_.msgHash == bytes32(PLACEHOLDER)) {
406: 		            revert B_INVALID_CONTEXT();
407: 		        }
```
[[124-126](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L124-L126), [260-262](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L260-L262), [321-323](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L321-L323), [405-407](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L405-L407)]



```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

85: 		        if (!_allowZeroAddress && addr_ == address(0)) {
86: 		            revert RESOLVER_ZERO_ADDR(_chainId, _name);
87: 		        }
```
[[85-87](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressResolver.sol#L85-L87)]



```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

42: 		        if (msg.sender != owner() && msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();
```
[[42](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L42)]



```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

46: 		        if (ctx.srcChainId != ownerChainId || ctx.from != owner()) {
47: 		            revert XCO_PERMISSION_DENIED();
48: 		        }

70: 		        if (_ownerChainId == 0 || _ownerChainId == block.chainid) {
71: 		            revert XCO_INVALID_OWNER_CHAINID();
72: 		        }
```
[[46-48](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L46-L48), [70-72](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L70-L72)]



```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

82: 		        if (block.chainid <= 1 || block.chainid > type(uint64).max) {
83: 		            revert L2_INVALID_CHAIN_ID();
84: 		        }

116: 		        if (
117: 		            _l1BlockHash == 0 || _l1StateRoot == 0 || _l1BlockId == 0
118: 		                || (block.number != 1 && _parentGasUsed == 0)
119: 		        ) {
120: 		            revert L2_INVALID_PARAM();
121: 		        }

141: 		        if (!skipFeeCheck() && block.basefee != basefee) {
142: 		            revert L2_BASEFEE_MISMATCH();
143: 		        }
```
[[82-84](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L82-L84), [116-121](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L116-L121), [141-143](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L141-L143)]



```solidity
File: packages/protocol/contracts/libs/Lib4844.sol

57: 		        if (uint256(first) != FIELD_ELEMENTS_PER_BLOB || uint256(second) != BLS_MODULUS) {
58: 		            revert EVAL_FAILED_2();
59: 		        }
```
[[57-59](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/Lib4844.sol#L57-L59)]



```solidity
File: packages/protocol/contracts/signal/SignalService.sol

114: 		                if (hop.chainId == 0 || hop.chainId == block.chainid) {
115: 		                    revert SS_INVALID_MID_HOP_CHAINID();
116: 		                }

131: 		        if (value == 0 || value != _loadSignalValue(address(this), signal)) {
132: 		            revert SS_SIGNAL_NOT_FOUND();
133: 		        }
```
[[114-116](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L114-L116), [131-133](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L131-L133)]



```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

274: 		        if (_start == 0 || _period == 0) {
275: 		            if (_cliff > 0) revert INVALID_GRANT();
276: 		        } else {
277: 		            if (_cliff > 0 && _cliff <= _start) revert INVALID_GRANT();
278: 		            if (_cliff >= _start + _period) revert INVALID_GRANT();
279: 		        }

277: 		            if (_cliff > 0 && _cliff <= _start) revert INVALID_GRANT();
```
[[274-279](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L274-L279), [277](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L277)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

38: 		        if (msg.sender != owner() && msg.sender != snapshooter) {
39: 		            revert BTOKEN_UNAUTHORIZED();
40: 		        }
```
[[38-40](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L38-L40)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

45: 		        if (_migratingAddress == migratingAddress && _migratingInbound == migratingInbound) {
46: 		            revert BB_INVALID_PARAMS();
47: 		        }
```
[[45-47](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L45-L47)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

108: 		        if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();
```
[[108](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L108)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

158: 		        if (_btokenNew == address(0) || bridgedToCanonical[_btokenNew].addr != address(0)) {
159: 		            revert VAULT_INVALID_NEW_BTOKEN();
160: 		        }

174: 		            if (
175: 		                ctoken.decimals != _ctoken.decimals
176: 		                    || keccak256(bytes(ctoken.symbol)) != keccak256(bytes(_ctoken.symbol))
177: 		                    || keccak256(bytes(ctoken.name)) != keccak256(bytes(_ctoken.name))
178: 		            ) revert VAULT_CTOKEN_MISMATCH();

267: 		        if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();
```
[[158-160](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L158-L160), [174-178](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L174-L178), [267](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L267)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

91: 		        if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();
```
[[91](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L91)]



```solidity
File: packages/protocol/contracts/tokenvault/LibBridgedToken.sol

20: 		        if (
21: 		            _srcToken == address(0) || _srcChainId == 0 || _srcChainId == block.chainid
22: 		                || bytes(_symbol).length == 0 || bytes(_name).length == 0
23: 		        ) {
24: 		            revert BTOKEN_INVALID_PARAMS();
25: 		        }
```
[[20-25](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L20-L25)]



```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

81: 		        if (
82: 		            block.timestamp > assignment.expiry
83: 		                || assignment.metaHash != 0 && _blk.metaHash != assignment.metaHash
84: 		                || assignment.parentMetaHash != 0 && _meta.parentMetaHash != assignment.parentMetaHash
85: 		                || assignment.maxBlockId != 0 && _meta.id > assignment.maxBlockId
86: 		                || assignment.maxProposedIn != 0 && block.number > assignment.maxProposedIn
87: 		        ) {
88: 		            revert HOOK_ASSIGNMENT_EXPIRED();
89: 		        }
```
[[81-89](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L81-L89)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

108: 		        if (params.parentMetaHash != 0 && parentMetaHash != params.parentMetaHash) {
109: 		            revert L1_UNEXPECTED_PARENT();
110: 		        }

195: 		        if (meta_.txListByteSize == 0 || meta_.txListByteSize > _config.blockMaxTxListBytes) {
196: 		            revert L1_TXLIST_SIZE();
197: 		        }
```
[[108-110](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L108-L110), [195-197](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L195-L197)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

105: 		        if (_tran.parentHash == 0 || _tran.blockHash == 0 || _tran.stateRoot == 0) {
106: 		            revert L1_INVALID_TRANSITION();
107: 		        }

111: 		        if (_meta.id <= b.lastVerifiedBlockId || _meta.id >= b.numBlocks) {
112: 		            revert L1_INVALID_BLOCK_ID();
113: 		        }

121: 		        if (blk.blockId != _meta.id || blk.metaHash != keccak256(abi.encode(_meta))) {
122: 		            revert L1_BLOCK_MISMATCH();
123: 		        }

134: 		        if (_proof.tier == 0 || _proof.tier < _meta.minTier || _proof.tier < ts.tier) {
135: 		            revert L1_INVALID_TIER();
136: 		        }

419: 		        if (_tid == 1 && _ts.tier == 0 && inProvingWindow) {
420: 		            if (!isAssignedPover) revert L1_NOT_ASSIGNED_PROVER();
421: 		        } else {
422: 		            // Disallow the same address to prove the block so that we can detect that the
423: 		            // assigned prover should not receive his liveness bond back
424: 		            if (isAssignedPover) revert L1_ASSIGNED_PROVER_NOT_ALLOWED();
425: 		        }
```
[[105-107](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L105-L107), [111-113](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L111-L113), [121-123](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L121-L123), [134-136](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L134-L136), [419-425](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L419-L425)]



```solidity
File: packages/protocol/contracts/L1/libs/LibUtils.sol

34: 		        if (_blockId < b.lastVerifiedBlockId || _blockId >= b.numBlocks) {
35: 		            revert L1_INVALID_BLOCK_ID();
36: 		        }
```
[[34-36](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibUtils.sol#L34-L36)]



```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

63: 		        if (_newGuardians.length < MIN_NUM_GUARDIANS || _newGuardians.length > type(uint8).max) {
64: 		            revert INVALID_GUARDIAN_SET();
65: 		        }

68: 		        if (_minGuardians < (_newGuardians.length + 1) >> 1 || _minGuardians > _newGuardians.length)
69: 		        {
70: 		            revert INVALID_MIN_GUARDIANS();
71: 		        }
```
[[63-65](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L63-L65), [68-71](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L68-L71)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

40: 		        if (claimEnd > block.timestamp || claimEnd + withdrawalWindow < block.timestamp) {
41: 		            revert WITHDRAWALS_NOT_ONGOING();
42: 		        }
```
[[40-42](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L40-L42)]



```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

34: 		        if (
35: 		            merkleRoot == 0x0 || claimStart == 0 || claimEnd == 0 || claimStart > block.timestamp
36: 		                || claimEnd < block.timestamp
37: 		        ) revert CLAIM_NOT_ONGOING();
```
[[34-37](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L34-L37)]

</details>

---

### [G-37] `abi.encode()` is less efficient than `abi.encodepacked()` for non-address arguments

Consider refactoring the code by using `abi.encodepacked` instead of `abi.encode`, as the former is cheaper when used with non-address arguments.

*There are 16 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

482: 		        retData = abi.encodePacked(sha256(abi.encode(v3quote)), tcbStatus);
```
[[482](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L482)]



```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

450: 		        return keccak256(abi.encode("TAIKO_MESSAGE", _message));
```
[[450](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L450)]



```solidity
File: packages/protocol/contracts/signal/SignalService.sol

186: 		        return keccak256(abi.encode(_chainId, _kind, _blockId));
```
[[186](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L186)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

281: 		            this.onMessageInvocation, abi.encode(ctoken_, _user, _op.to, _op.tokenIds, _op.amounts)
```
[[281](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L281)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

384: 		            this.onMessageInvocation, abi.encode(ctoken_, _user, _to, balanceChange_)
```
[[384](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L384)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

217: 		            this.onMessageInvocation, abi.encode(ctoken_, _user, _op.to, _op.tokenIds)
```
[[217](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L217)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

136: 		        bytes memory args = abi.encode(sha256(tbs), r, s, gx, gy);
```
[[136](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L136)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

126: 		                depositsHash: keccak256(abi.encode(deposits_)),

213: 		            metaHash: keccak256(abi.encode(meta_)),
```
[[126](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L126), [213](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L213)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

121: 		        if (blk.blockId != _meta.id || blk.metaHash != keccak256(abi.encode(_meta))) {
```
[[121](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L121)]



```solidity
File: packages/protocol/contracts/L1/provers/GuardianProver.sol

46: 		        bytes32 hash = keccak256(abi.encode(_meta, _tran));

51: 		            ITaikoL1(resolve("taiko", false)).proveBlock(_meta.id, abi.encode(_meta, _tran, _proof));
```
[[46](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/GuardianProver.sol#L46), [51](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/GuardianProver.sol#L51)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

60: 		        _verifyClaim(abi.encode(user, amount), proof);
```
[[60](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L60)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

80: 		        _verifyClaim(abi.encode(user, amount), proof);
```
[[80](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L80)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

56: 		        _verifyClaim(abi.encode(user, tokenIds), proof);
```
[[56](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L56)]



```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

68: 		        bytes32 hash = keccak256(abi.encode("CLAIM_TAIKO_AIRDROP", data));
```
[[68](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L68)]

</details>

---

### [G-38] Unused named return variables without optimizer waste gas

Consider changing the variable to be an unnamed one, since the variable is never assigned, nor is it returned by name. If the optimizer is not turned on, leaving the code as it is will also waste gas for the stack variable.

*There are 20 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

// @audit bool valid
130: 		        returns (bool valid)

// @audit bool
178: 		        returns (bool, EnclaveIdStruct.EnclaveIdStatus status)

// @audit bool
212: 		        returns (bool, TCBInfoStruct.TCBStatus status)
```
[[130](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L130), [178](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L178), [212](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L212)]



```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

// @audit uint256 invocationDelay_, uint256 invocationExtraDelay_
421: 		        returns (uint256 invocationDelay_, uint256 invocationExtraDelay_)
```
[[421](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L421)]



```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

// @audit address payable
37: 		        returns (address payable)

// @audit address payable
51: 		        returns (address payable)
```
[[37](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressResolver.sol#L37), [51](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressResolver.sol#L51)]



```solidity
File: packages/protocol/contracts/libs/LibAddress.sol

// @audit 
52: 		        returns (bool result_)
```
[[52](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibAddress.sol#L52)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

// @audit 
46: 		        returns (bool success, bytes[] memory certs)

// @audit 
80: 		        returns (bool success, ECSha256Certificate memory cert)

// @audit bool success, bytes memory extracted, uint256 endIndex
219: 		        returns (bool success, bytes memory extracted, uint256 endIndex)

// @audit 
258: 		        returns (bytes memory output)

// @audit uint256 pcesvn, uint256[] memory cpusvns
277: 		            bool success,
```
[[46](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L46), [80](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L80), [219](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L219), [258](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L258), [277](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L277)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

// @audit uint8 ret
188: 		    function readUint8(bytes memory self, uint256 idx) internal pure returns (uint8 ret) {
```
[[188](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L188)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

// @audit bool sigValid
120: 		        returns (bool sigValid)
```
[[120](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L120)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

// @audit uint8 maxBlocksToVerify_
100: 		        returns (uint8 maxBlocksToVerify_)
```
[[100](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L100)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

// @audit 
107: 		        returns (uint256 balance, uint256 withdrawableAmount)
```
[[107](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L107)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

// @audit 
27: 		        returns (bool success, V3Struct.ParsedV3QuoteStruct memory v3ParsedQuote)

// @audit 
168: 		        returns (bool success, V3Struct.Header memory header)

// @audit 
209: 		        returns (bool success, V3Struct.ECDSAQuoteV3AuthData memory authDataV3)
```
[[27](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L27), [168](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L168), [209](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L209)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

// @audit uint256 offset_, uint256 length_, RLPItemType type_
147: 		        returns (uint256 offset_, uint256 length_, RLPItemType type_)
```
[[147](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L147)]

</details>

---

### [G-39] Consider pre-calculating the address of `address(this)` to save gas

Use Foundry's [`script.sol`](https://book.getfoundry.sh/reference/forge-std/compute-create-address) or Solady's [`LibRlp.sol`](https://github.com/Vectorized/solady/blob/main/src/utils/LibRLP.sol) to save the value in a constant, which will avoid having to spend gas to push the value on the stack every time it's used.

*There are 40 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

174: 		            if (!ISignalService(signalService).isSignalSent(address(this), msgHash)) {

196: 		                _storeContext(msgHash, address(this), _message.srcChainId);

270: 		                _message.to == address(0) || _message.to == address(this)

343: 		            _app: address(this),

486: 		        assert(_message.from != address(this));
```
[[174](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L174), [196](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L196), [270](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L270), [343](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L343), [486](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L486)]



```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

61: 		        if (_to == address(this)) revert TKO_INVALID_ADDR();

79: 		        if (_to == address(this)) revert TKO_INVALID_ADDR();
```
[[61](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoToken.sol#L61), [79](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoToken.sol#L79)]



```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

50: 		        (bool success,) = address(this).call(txdata);
```
[[50](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L50)]



```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

174: 		            _to.sendEther(address(this).balance);

176: 		            IERC20(_token).safeTransfer(_to, IERC20(_token).balanceOf(address(this)));
```
[[174](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L174), [176](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L176)]



```solidity
File: packages/protocol/contracts/signal/SignalService.sol

112: 		                signalService = address(this);

131: 		        if (value == 0 || value != _loadSignalValue(address(this), signal)) {

149: 		        return _loadSignalValue(address(this), signal) == _chainData;

171: 		            chainData_ = _loadSignalValue(address(this), signal);

245: 		        _sendSignal(address(this), signal_, _chainData);
```
[[112](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L112), [131](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L131), [149](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L149), [171](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L171), [245](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L245)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

137: 		        if (_to == address(this)) revert BTOKEN_CANNOT_RECEIVE();
```
[[137](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L137)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

147: 		        if (_to == address(this)) revert BTOKEN_CANNOT_RECEIVE();
```
[[147](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L147)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

125: 		        if (_to == address(this)) revert BTOKEN_CANNOT_RECEIVE();
```
[[125](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L125)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

108: 		        if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

226: 		            IERC1155(token).safeBatchTransferFrom(address(this), to, tokenIds, amounts, "");

272: 		                        to: address(this),
```
[[108](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L108), [226](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L226), [272](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L272)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

267: 		        if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

378: 		            uint256 _balance = t.balanceOf(address(this));

379: 		            t.safeTransferFrom({ from: msg.sender, to: address(this), value: _amount });

380: 		            balanceChange_ = t.balanceOf(address(this)) - _balance;
```
[[267](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L267), [378](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L378), [379](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L379), [380](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L380)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

91: 		        if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

171: 		                IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);

211: 		                    t.safeTransferFrom(_user, address(this), _op.tokenIds[i]);
```
[[91](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L91), [171](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L171), [211](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L211)]



```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

186: 		                address(this),
```
[[186](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L186)]



```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

125: 		        if (address(this).balance > 0) {

126: 		            taikoL1Address.sendEther(address(this).balance);

151: 		                address(this),
```
[[125](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L125), [126](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L126), [151](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L151)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

238: 		            uint256 tkoBalance = tko.balanceOf(address(this));

253: 		                IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }(

260: 		            if (address(this).balance != 0) {

261: 		                msg.sender.sendEther(address(this).balance);

268: 		            if (tko.balanceOf(address(this)) != tkoBalance + _config.livenessBond) {
```
[[238](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L238), [253](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L253), [260](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L260), [261](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L261), [268](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L268)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

242: 		                tko.transferFrom(msg.sender, address(this), tier.contestBond);

384: 		                _tko.transferFrom(msg.sender, address(this), _tier.validityBond - reward);
```
[[242](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L242), [384](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L384)]



```solidity
File: packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

48: 		        usdc.transferFrom(_from, address(this), _amount);
```
[[48](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L48)]

</details>

---

### [G-40] Consider using Solady's `FixedPointMathLib`

Saves gas, and works to avoid unnecessary [overflows](https://github.com/Vectorized/solady/blob/6cce088e69d6e46671f2f622318102bd5db77a65/src/utils/FixedPointMathLib.sol#L267).

*There are 4 instances of this issue.*


```solidity
File: packages/protocol/contracts/L2/Lib1559Math.sol

41: 		        uint256 input = _gasExcess * LibFixedPointMath.SCALING_FACTOR / _adjustmentFactor;
```
[[41](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/Lib1559Math.sol#L41)]



```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

264: 		        return _amount * uint64(block.timestamp - _start) / _period;
```
[[264](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L264)]



```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

247: 		            _config.chainId <= 1 || _config.chainId == block.chainid //
248: 		                || _config.blockMaxProposals == 1
249: 		                || _config.blockRingBufferSize <= _config.blockMaxProposals + 1
250: 		                || _config.blockMaxGasLimit == 0 || _config.blockMaxTxListBytes == 0
251: 		                || _config.blockMaxTxListBytes > 128 * 1024 // calldata up to 128K
252: 		                || _config.livenessBond == 0 || _config.ethDepositRingBufferSize <= 1
253: 		                || _config.ethDepositMinCountPerBlock == 0
254: 		            // Audit recommendation, and gas tested. Processing 32 deposits (as initially set in
255: 		            // TaikoL1.sol) costs 72_502 gas.
256: 		            || _config.ethDepositMaxCountPerBlock > 32
257: 		                || _config.ethDepositMaxCountPerBlock < _config.ethDepositMinCountPerBlock
258: 		                || _config.ethDepositMinAmount == 0
259: 		                || _config.ethDepositMaxAmount <= _config.ethDepositMinAmount
260: 		                || _config.ethDepositMaxAmount > type(uint96).max || _config.ethDepositGas == 0
261: 		                || _config.ethDepositMaxFee == 0
262: 		                || _config.ethDepositMaxFee > type(uint96).max / _config.ethDepositMaxCountPerBlock
```
[[247-262](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L247-L262)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

117: 		        uint256 timeBasedAllowance = balance
118: 		            * (block.timestamp.min(claimEnd + withdrawalWindow) - claimEnd) / withdrawalWindow;
```
[[117-118](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L117-L118)]


---

### [G-41] Reduce deployment costs by tweaking contracts' metadata

When solidity generates the bytecode for the smart contract to be deployed, it appends metadata about the compilation at the end of the bytecode.

By default, the solidity compiler appends metadata at the end of the “actual” initcode, which gets stored to the blockchain when the constructor finishes executing.

Consider tweaking the metadata to avoid this unnecessary allocation. A full guide can be found [here](https://www.rareskills.io/post/solidity-metadata).

*There are 86 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

22: 		contract AutomataDcapV3Attestation is IAttestation {
```
[[22](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L22)]



```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

16: 		contract Bridge is EssentialContract, IBridge {
```
[[16](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L16)]



```solidity
File: packages/protocol/contracts/bridge/IBridge.sol

8: 		interface IBridge {

160: 		interface IRecallableSender {

174: 		interface IMessageInvocable {
```
[[8](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/IBridge.sol#L8), [160](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/IBridge.sol#L160), [174](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/IBridge.sol#L174)]



```solidity
File: packages/protocol/contracts/common/AddressManager.sol

10: 		contract AddressManager is EssentialContract, IAddressManager {
```
[[10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressManager.sol#L10)]



```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

11: 		abstract contract AddressResolver is IAddressResolver, Initializable {
```
[[11](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressResolver.sol#L11)]



```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

10: 		abstract contract EssentialContract is UUPSUpgradeable, Ownable2StepUpgradeable, AddressResolver {
```
[[10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L10)]



```solidity
File: packages/protocol/contracts/common/IAddressManager.sol

7: 		interface IAddressManager {
```
[[7](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/IAddressManager.sol#L7)]



```solidity
File: packages/protocol/contracts/common/IAddressResolver.sol

13: 		interface IAddressResolver {
```
[[13](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/IAddressResolver.sol#L13)]



```solidity
File: packages/protocol/contracts/L1/ITaikoL1.sol

8: 		interface ITaikoL1 {
```
[[8](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/ITaikoL1.sol#L8)]



```solidity
File: packages/protocol/contracts/L1/TaikoData.sol

8: 		library TaikoData {
```
[[8](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L8)]



```solidity
File: packages/protocol/contracts/L1/TaikoErrors.sol

11: 		abstract contract TaikoErrors {
```
[[11](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoErrors.sol#L11)]



```solidity
File: packages/protocol/contracts/L1/TaikoEvents.sol

13: 		abstract contract TaikoEvents {
```
[[13](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoEvents.sol#L13)]



```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

22: 		contract TaikoL1 is EssentialContract, ITaikoL1, TaikoEvents, TaikoErrors {
```
[[22](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L22)]



```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

15: 		contract TaikoToken is EssentialContract, ERC20SnapshotUpgradeable, ERC20VotesUpgradeable {
```
[[15](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoToken.sol#L15)]



```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

14: 		abstract contract CrossChainOwned is EssentialContract, IMessageInvocable {
```
[[14](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L14)]



```solidity
File: packages/protocol/contracts/L2/Lib1559Math.sol

10: 		library Lib1559Math {
```
[[10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/Lib1559Math.sol#L10)]



```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

21: 		contract TaikoL2 is CrossChainOwned {
```
[[21](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L21)]



```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

9: 		contract TaikoL2EIP1559Configurable is TaikoL2 {
```
[[9](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L9)]



```solidity
File: packages/protocol/contracts/libs/Lib4844.sol

8: 		library Lib4844 {
```
[[8](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/Lib4844.sol#L8)]



```solidity
File: packages/protocol/contracts/libs/LibAddress.sol

13: 		library LibAddress {
```
[[13](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibAddress.sol#L13)]



```solidity
File: packages/protocol/contracts/libs/LibMath.sol

7: 		library LibMath {
```
[[7](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibMath.sol#L7)]



```solidity
File: packages/protocol/contracts/libs/LibTrieProof.sol

15: 		library LibTrieProof {
```
[[15](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibTrieProof.sol#L15)]



```solidity
File: packages/protocol/contracts/signal/ISignalService.sol

12: 		interface ISignalService {
```
[[12](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/ISignalService.sol#L12)]



```solidity
File: packages/protocol/contracts/signal/LibSignals.sol

6: 		library LibSignals {
```
[[6](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/LibSignals.sol#L6)]



```solidity
File: packages/protocol/contracts/signal/SignalService.sol

14: 		contract SignalService is EssentialContract, ISignalService {
```
[[14](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L14)]



```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

25: 		contract TimelockTokenPool is EssentialContract {
```
[[25](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L25)]



```solidity
File: packages/protocol/contracts/tokenvault/BaseNFTVault.sol

9: 		abstract contract BaseNFTVault is BaseVault {
```
[[9](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L9)]



```solidity
File: packages/protocol/contracts/tokenvault/BaseVault.sol

12: 		abstract contract BaseVault is
```
[[12](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseVault.sol#L12)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

14: 		contract BridgedERC1155 is EssentialContract, IERC1155MetadataURIUpgradeable, ERC1155Upgradeable {
```
[[14](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L14)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

15: 		contract BridgedERC20 is
```
[[15](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L15)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

9: 		abstract contract BridgedERC20Base is EssentialContract, IBridgedERC20 {
```
[[9](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L9)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

12: 		contract BridgedERC721 is EssentialContract, ERC721Upgradeable {
```
[[12](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L12)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

16: 		interface IERC1155NameAndSymbol {

29: 		contract ERC1155Vault is BaseNFTVault, ERC1155ReceiverUpgradeable {
```
[[16](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L16), [29](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L29)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

18: 		contract ERC20Vault is BaseVault {
```
[[18](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L18)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

16: 		contract ERC721Vault is BaseNFTVault, IERC721Receiver {
```
[[16](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L16)]



```solidity
File: packages/protocol/contracts/tokenvault/IBridgedERC20.sol

10: 		interface IBridgedERC20 {
```
[[10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/IBridgedERC20.sol#L10)]



```solidity
File: packages/protocol/contracts/tokenvault/LibBridgedToken.sol

8: 		library LibBridgedToken {
```
[[8](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L8)]



```solidity
File: packages/protocol/contracts/verifiers/GuardianVerifier.sol

10: 		contract GuardianVerifier is EssentialContract, IVerifier {
```
[[10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L10)]



```solidity
File: packages/protocol/contracts/verifiers/IVerifier.sol

9: 		interface IVerifier {
```
[[9](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/IVerifier.sol#L9)]



```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

19: 		contract SgxVerifier is EssentialContract, IVerifier {
```
[[19](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L19)]



```solidity
File: packages/protocol/contracts/automata-attestation/interfaces/IAttestation.sol

8: 		interface IAttestation {
```
[[8](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/interfaces/IAttestation.sol#L8)]



```solidity
File: packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol

6: 		interface ISigVerifyLib {
```
[[6](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L6)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/EnclaveIdStruct.sol

6: 		library EnclaveIdStruct {
```
[[6](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/EnclaveIdStruct.sol#L6)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

12: 		contract PEMCertChainLib is IPEMCertChainLib {
```
[[12](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L12)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol

6: 		library TCBInfoStruct {
```
[[6](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol#L6)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

12: 		library NodePtr {

38: 		library Asn1Decode {
```
[[12](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L12), [38](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L38)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

8: 		library BytesUtils {
```
[[8](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L8)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

34: 		library RsaVerify {
```
[[34](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L34)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/SHA1.sol

10: 		library SHA1 {
```
[[10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SHA1.sol#L10)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

15: 		contract SigVerifyLib is ISigVerifyLib {
```
[[15](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L15)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

7: 		library X509DateUtils {
```
[[7](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L7)]



```solidity
File: packages/protocol/contracts/L1/gov/TaikoGovernor.sol

16: 		contract TaikoGovernor is
```
[[16](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L16)]



```solidity
File: packages/protocol/contracts/L1/gov/TaikoTimelockController.sol

9: 		contract TaikoTimelockController is EssentialContract, TimelockControllerUpgradeable {
```
[[9](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L9)]



```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

14: 		contract AssignmentHook is EssentialContract, IHook {
```
[[14](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L14)]



```solidity
File: packages/protocol/contracts/L1/hooks/IHook.sol

8: 		interface IHook {
```
[[8](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/IHook.sol#L8)]



```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

12: 		library LibDepositing {
```
[[12](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L12)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

15: 		library LibProposing {
```
[[15](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L15)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

16: 		library LibProving {
```
[[16](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L16)]



```solidity
File: packages/protocol/contracts/L1/libs/LibUtils.sol

9: 		library LibUtils {
```
[[9](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibUtils.sol#L9)]



```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

16: 		library LibVerifying {
```
[[16](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L16)]



```solidity
File: packages/protocol/contracts/L1/provers/GuardianProver.sol

10: 		contract GuardianProver is Guardians {
```
[[10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/GuardianProver.sol#L10)]



```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

9: 		abstract contract Guardians is EssentialContract {
```
[[9](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L9)]



```solidity
File: packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol

10: 		contract DevnetTierProvider is EssentialContract, ITierProvider {
```
[[10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L10)]



```solidity
File: packages/protocol/contracts/L1/tiers/ITierProvider.sol

7: 		interface ITierProvider {

37: 		library LibTiers {
```
[[7](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L7), [37](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L37)]



```solidity
File: packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol

10: 		contract MainnetTierProvider is EssentialContract, ITierProvider {
```
[[10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L10)]



```solidity
File: packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol

10: 		contract TestnetTierProvider is EssentialContract, ITierProvider {
```
[[10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L10)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

11: 		contract ERC20Airdrop is MerkleClaimable {
```
[[11](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L11)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

12: 		contract ERC20Airdrop2 is MerkleClaimable {
```
[[12](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L12)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

9: 		contract ERC721Airdrop is MerkleClaimable {
```
[[9](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L9)]



```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

10: 		abstract contract MerkleClaimable is EssentialContract {
```
[[10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L10)]



```solidity
File: packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol

5: 		library ExcessivelySafeCall {
```
[[5](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L5)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/Bytes.sol

6: 		library Bytes {
```
[[6](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L6)]



```solidity
File: packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

8: 		interface IUSDC {

28: 		contract USDCAdapter is BridgedERC20Base {
```
[[8](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L8), [28](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L28)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol

6: 		interface IPEMCertChainLib {
```
[[6](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L6)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

11: 		library V3Parser {
```
[[11](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L11)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol

6: 		library V3Struct {
```
[[6](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L6)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

9: 		library RLPReader {
```
[[9](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L9)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

9: 		library RLPWriter {
```
[[9](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L9)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

11: 		library MerkleTrie {
```
[[11](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L11)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol

9: 		library SecureMerkleTrie {
```
[[9](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L9)]

</details>

---

### [G-42] Emitting constants wastes gas

Every event parameter costs `Glogdata` (**8 gas**) per byte. You can avoid this extra cost, in cases where you're emitting a constant, by creating a second version of the event, which doesn't have the parameter (and have users look to the contract's variables for its value instead), and using the new event in the cases shown below.

*There are 4 instances of this issue.*


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

// @audit true
210: 		            emit MessageReceived(msgHash, _message, true);

// @audit false
303: 		            emit MessageReceived(msgHash, _message, false);
```
[[210](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L210), [303](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L303)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

// @audit 0
230: 		                emit TransitionProved({
231: 		                    blockId: blk.blockId,
232: 		                    tran: _tran,
233: 		                    prover: msg.sender,
234: 		                    validityBond: 0,
235: 		                    tier: _proof.tier
236: 		                });
```
[[230-236](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L230-L236)]



```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

// @audit 0, 0, 0, 0
73: 		        emit BlockVerified({
74: 		            blockId: 0,
75: 		            assignedProver: address(0),
76: 		            prover: address(0),
77: 		            blockHash: _genesisBlockHash,
78: 		            stateRoot: 0,
79: 		            tier: 0,
80: 		            contestations: 0
81: 		        });
```
[[73-81](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L73-L81)]


---

### [G-43] Update OpenZeppelin dependency to save gas

Every release contains new gas optimizations, use the latest version to take advantage of this.

*There are 54 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

4: 		import "@openzeppelin/contracts/utils/Address.sol";
```
[[4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L4)]



```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

4: 		import "@openzeppelin/contracts-upgradeable/proxy/utils/Initializable.sol";
```
[[4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressResolver.sol#L4)]



```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

4: 		import "@openzeppelin/contracts/proxy/utils/UUPSUpgradeable.sol";

5: 		import "@openzeppelin/contracts-upgradeable/access/Ownable2StepUpgradeable.sol";
```
[[4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L5)]



```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

4: 		import "@openzeppelin/contracts-upgradeable/token/ERC20/ERC20Upgradeable.sol";

5: 		import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20SnapshotUpgradeable.sol";

6: 		import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20VotesUpgradeable.sol";
```
[[4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoToken.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoToken.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoToken.sol#L6)]



```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

4: 		import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```
[[4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L4)]



```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

4: 		import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

5: 		import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```
[[4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L5)]



```solidity
File: packages/protocol/contracts/libs/LibAddress.sol

4: 		import "@openzeppelin/contracts/utils/Address.sol";

5: 		import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol";

6: 		import "@openzeppelin/contracts/utils/introspection/IERC165.sol";

7: 		import "@openzeppelin/contracts/interfaces/IERC1271.sol";
```
[[4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibAddress.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibAddress.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibAddress.sol#L6), [7](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibAddress.sol#L7)]



```solidity
File: packages/protocol/contracts/signal/SignalService.sol

4: 		import "@openzeppelin/contracts/utils/math/SafeCast.sol";
```
[[4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L4)]



```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

4: 		import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol";

5: 		import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

6: 		import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```
[[4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L6)]



```solidity
File: packages/protocol/contracts/tokenvault/BaseVault.sol

4: 		import "@openzeppelin/contracts-upgradeable/utils/introspection/IERC165Upgradeable.sol";

5: 		import "@openzeppelin/contracts/proxy/ERC1967/ERC1967Proxy.sol";
```
[[4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseVault.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseVault.sol#L5)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

4: 		import "@openzeppelin/contracts/utils/Strings.sol";

5: 		import "@openzeppelin/contracts-upgradeable/token/ERC1155/ERC1155Upgradeable.sol";

6: 		import
7: 		    "@openzeppelin/contracts-upgradeable/token/ERC1155/extensions/IERC1155MetadataURIUpgradeable.sol";
```
[[4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L5), [6-7](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L6-L7)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

4: 		import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/IERC20MetadataUpgradeable.sol";

5: 		import "@openzeppelin/contracts/utils/Strings.sol";

6: 		import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20SnapshotUpgradeable.sol";

7: 		import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20VotesUpgradeable.sol";
```
[[4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L6), [7](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L7)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

4: 		import "@openzeppelin/contracts-upgradeable/token/ERC721/ERC721Upgradeable.sol";

5: 		import "@openzeppelin/contracts/utils/Strings.sol";
```
[[4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L5)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

4: 		import "@openzeppelin/contracts/token/ERC1155/IERC1155.sol";

5: 		import "@openzeppelin/contracts-upgradeable/token/ERC1155/utils/ERC1155ReceiverUpgradeable.sol";
```
[[4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L5)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

4: 		import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

5: 		import "@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol";

6: 		import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```
[[4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L6)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

4: 		import "@openzeppelin/contracts/token/ERC721/IERC721.sol";

5: 		import "@openzeppelin/contracts/token/ERC721/IERC721Receiver.sol";
```
[[4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L5)]



```solidity
File: packages/protocol/contracts/tokenvault/LibBridgedToken.sol

4: 		import "@openzeppelin/contracts/utils/Strings.sol";
```
[[4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L4)]



```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

4: 		import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol";
```
[[4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L4)]



```solidity
File: packages/protocol/contracts/L1/gov/TaikoGovernor.sol

4: 		import "@openzeppelin/contracts-upgradeable/governance/GovernorUpgradeable.sol";

5: 		import
6: 		    "@openzeppelin/contracts-upgradeable/governance/compatibility/GovernorCompatibilityBravoUpgradeable.sol";

7: 		import "@openzeppelin/contracts-upgradeable/governance/extensions/GovernorVotesUpgradeable.sol";

8: 		import
9: 		    "@openzeppelin/contracts-upgradeable/governance/extensions/GovernorVotesQuorumFractionUpgradeable.sol";

10: 		import
11: 		    "@openzeppelin/contracts-upgradeable/governance/extensions/GovernorTimelockControlUpgradeable.sol";
```
[[4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L4), [5-6](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L5-L6), [7](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L7), [8-9](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L8-L9), [10-11](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L10-L11)]



```solidity
File: packages/protocol/contracts/L1/gov/TaikoTimelockController.sol

4: 		import "@openzeppelin/contracts-upgradeable/governance/TimelockControllerUpgradeable.sol";
```
[[4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L4)]



```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

4: 		import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

5: 		import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```
[[4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L5)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

4: 		import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```
[[4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L4)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

4: 		import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```
[[4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L4)]



```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

4: 		import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```
[[4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L4)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

4: 		import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

5: 		import "@openzeppelin/contracts/governance/utils/IVotes.sol";
```
[[4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L5)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

4: 		import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```
[[4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L4)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

4: 		import "@openzeppelin/contracts/token/ERC721/IERC721.sol";
```
[[4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L4)]



```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

4: 		import "@openzeppelin/contracts/utils/cryptography/MerkleProof.sol";
```
[[4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L4)]

</details>

---

### [G-44] Function names can be optimized

Function that are `public`/`external` and `public` state variable names can be optimized to save gas.

Method IDs that have two leading zero bytes can save **128 gas** each during deployment, and renaming functions to have lower method IDs will save **22 gas** per call, per sorted position shifted. [Reference](https://blog.emn178.cc/en/post/solidity-gas-optimization-function-name/)

*There are 56 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

22: 		contract AutomataDcapV3Attestation is IAttestation {
```
[[22](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L22)]



```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

16: 		contract Bridge is EssentialContract, IBridge {
```
[[16](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L16)]



```solidity
File: packages/protocol/contracts/bridge/IBridge.sol

8: 		interface IBridge {

160: 		interface IRecallableSender {

174: 		interface IMessageInvocable {
```
[[8](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/IBridge.sol#L8), [160](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/IBridge.sol#L160), [174](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/IBridge.sol#L174)]



```solidity
File: packages/protocol/contracts/common/AddressManager.sol

10: 		contract AddressManager is EssentialContract, IAddressManager {
```
[[10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressManager.sol#L10)]



```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

11: 		abstract contract AddressResolver is IAddressResolver, Initializable {
```
[[11](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressResolver.sol#L11)]



```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

10: 		abstract contract EssentialContract is UUPSUpgradeable, Ownable2StepUpgradeable, AddressResolver {
```
[[10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L10)]



```solidity
File: packages/protocol/contracts/common/IAddressManager.sol

7: 		interface IAddressManager {
```
[[7](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/IAddressManager.sol#L7)]



```solidity
File: packages/protocol/contracts/common/IAddressResolver.sol

13: 		interface IAddressResolver {
```
[[13](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/IAddressResolver.sol#L13)]



```solidity
File: packages/protocol/contracts/L1/ITaikoL1.sol

8: 		interface ITaikoL1 {
```
[[8](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/ITaikoL1.sol#L8)]



```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

22: 		contract TaikoL1 is EssentialContract, ITaikoL1, TaikoEvents, TaikoErrors {
```
[[22](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L22)]



```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

15: 		contract TaikoToken is EssentialContract, ERC20SnapshotUpgradeable, ERC20VotesUpgradeable {
```
[[15](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoToken.sol#L15)]



```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

14: 		abstract contract CrossChainOwned is EssentialContract, IMessageInvocable {
```
[[14](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L14)]



```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

21: 		contract TaikoL2 is CrossChainOwned {
```
[[21](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L21)]



```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

9: 		contract TaikoL2EIP1559Configurable is TaikoL2 {
```
[[9](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L9)]



```solidity
File: packages/protocol/contracts/signal/ISignalService.sol

12: 		interface ISignalService {
```
[[12](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/ISignalService.sol#L12)]



```solidity
File: packages/protocol/contracts/signal/SignalService.sol

14: 		contract SignalService is EssentialContract, ISignalService {
```
[[14](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L14)]



```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

25: 		contract TimelockTokenPool is EssentialContract {
```
[[25](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L25)]



```solidity
File: packages/protocol/contracts/tokenvault/BaseVault.sol

12: 		abstract contract BaseVault is
```
[[12](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseVault.sol#L12)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

14: 		contract BridgedERC1155 is EssentialContract, IERC1155MetadataURIUpgradeable, ERC1155Upgradeable {
```
[[14](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L14)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

15: 		contract BridgedERC20 is
```
[[15](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L15)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

9: 		abstract contract BridgedERC20Base is EssentialContract, IBridgedERC20 {
```
[[9](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L9)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

12: 		contract BridgedERC721 is EssentialContract, ERC721Upgradeable {
```
[[12](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L12)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

16: 		interface IERC1155NameAndSymbol {

29: 		contract ERC1155Vault is BaseNFTVault, ERC1155ReceiverUpgradeable {
```
[[16](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L16), [29](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L29)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

18: 		contract ERC20Vault is BaseVault {
```
[[18](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L18)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

16: 		contract ERC721Vault is BaseNFTVault, IERC721Receiver {
```
[[16](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L16)]



```solidity
File: packages/protocol/contracts/tokenvault/IBridgedERC20.sol

10: 		interface IBridgedERC20 {
```
[[10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/IBridgedERC20.sol#L10)]



```solidity
File: packages/protocol/contracts/verifiers/GuardianVerifier.sol

10: 		contract GuardianVerifier is EssentialContract, IVerifier {
```
[[10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L10)]



```solidity
File: packages/protocol/contracts/verifiers/IVerifier.sol

9: 		interface IVerifier {
```
[[9](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/IVerifier.sol#L9)]



```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

19: 		contract SgxVerifier is EssentialContract, IVerifier {
```
[[19](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L19)]



```solidity
File: packages/protocol/contracts/automata-attestation/interfaces/IAttestation.sol

8: 		interface IAttestation {
```
[[8](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/interfaces/IAttestation.sol#L8)]



```solidity
File: packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol

6: 		interface ISigVerifyLib {
```
[[6](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L6)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

12: 		contract PEMCertChainLib is IPEMCertChainLib {
```
[[12](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L12)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

15: 		contract SigVerifyLib is ISigVerifyLib {
```
[[15](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L15)]



```solidity
File: packages/protocol/contracts/L1/gov/TaikoGovernor.sol

16: 		contract TaikoGovernor is
```
[[16](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L16)]



```solidity
File: packages/protocol/contracts/L1/gov/TaikoTimelockController.sol

9: 		contract TaikoTimelockController is EssentialContract, TimelockControllerUpgradeable {
```
[[9](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L9)]



```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

14: 		contract AssignmentHook is EssentialContract, IHook {
```
[[14](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L14)]



```solidity
File: packages/protocol/contracts/L1/hooks/IHook.sol

8: 		interface IHook {
```
[[8](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/IHook.sol#L8)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

16: 		library LibProving {
```
[[16](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L16)]



```solidity
File: packages/protocol/contracts/L1/libs/LibUtils.sol

9: 		library LibUtils {
```
[[9](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibUtils.sol#L9)]



```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

16: 		library LibVerifying {
```
[[16](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L16)]



```solidity
File: packages/protocol/contracts/L1/provers/GuardianProver.sol

10: 		contract GuardianProver is Guardians {
```
[[10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/GuardianProver.sol#L10)]



```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

9: 		abstract contract Guardians is EssentialContract {
```
[[9](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L9)]



```solidity
File: packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol

10: 		contract DevnetTierProvider is EssentialContract, ITierProvider {
```
[[10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L10)]



```solidity
File: packages/protocol/contracts/L1/tiers/ITierProvider.sol

7: 		interface ITierProvider {
```
[[7](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L7)]



```solidity
File: packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol

10: 		contract MainnetTierProvider is EssentialContract, ITierProvider {
```
[[10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L10)]



```solidity
File: packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol

10: 		contract TestnetTierProvider is EssentialContract, ITierProvider {
```
[[10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L10)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

11: 		contract ERC20Airdrop is MerkleClaimable {
```
[[11](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L11)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

12: 		contract ERC20Airdrop2 is MerkleClaimable {
```
[[12](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L12)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

9: 		contract ERC721Airdrop is MerkleClaimable {
```
[[9](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L9)]



```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

10: 		abstract contract MerkleClaimable is EssentialContract {
```
[[10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L10)]



```solidity
File: packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

8: 		interface IUSDC {

28: 		contract USDCAdapter is BridgedERC20Base {
```
[[8](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L8), [28](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L28)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol

6: 		interface IPEMCertChainLib {
```
[[6](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L6)]

</details>

---

### [G-45] Avoid zero transfers calls

Emit any transfer events if the EIP requires it, but avoid doing the actual call when the amount is zero.

*There are 10 instances of this issue.*


```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

219: 		        IERC20(taikoToken).transferFrom(sharedVault, _to, amountToWithdraw);
```
[[219](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L219)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

196: 		                tko.transfer(blk.assignedProver, blk.livenessBond);

242: 		                tko.transferFrom(msg.sender, address(this), tier.contestBond);

367: 		                _tko.transfer(_ts.prover, _ts.validityBond + reward);

371: 		                _tko.transfer(_ts.contester, _ts.contestBond + reward);

382: 		                _tko.transfer(msg.sender, reward - _tier.validityBond);

384: 		                _tko.transferFrom(msg.sender, address(this), _tier.validityBond - reward);
```
[[196](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L196), [242](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L242), [367](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L367), [371](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L371), [382](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L382), [384](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L384)]



```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

189: 		                tko.transfer(ts.prover, bondToReturn);
```
[[189](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L189)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

63: 		        IERC20(token).transferFrom(vault, user, amount);
```
[[63](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L63)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

91: 		        IERC20(token).transferFrom(vault, user, amount);
```
[[91](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L91)]


---

### [G-46] Using `delete` instead of setting mapping/struct to 0 saves gas

Avoid an assignment by deleting the value instead of setting it to zero, as it's [cheaper](https://gist.github.com/DadeKuma/ea874815202fc77e9d81f81a047c1e5e).

*There are 10 instances of this issue.*


```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

231: 		        _grant.grantStart = 0;

232: 		        _grant.grantPeriod = 0;
```
[[231](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L231), [232](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L232)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

336: 		                tbsPtr = 0; // exit
```
[[336](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L336)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

190: 		            meta_.txListByteOffset = 0;
```
[[190](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L190)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

197: 		                blk.livenessBond = 0;

300: 		            ts_.blockHash = 0;

301: 		            ts_.stateRoot = 0;

302: 		            ts_.validityBond = 0;

306: 		            ts_.tier = 0;

307: 		            ts_.contestations = 0;
```
[[197](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L197), [300](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L300), [301](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L301), [302](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L302), [306](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L306), [307](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L307)]


---

### [G-47] Using `bool` for storage incurs overhead

Booleans are more expensive than `uint256` or any type that takes up a full word because each write operation emits an extra SLOAD to first read the slot's contents, replace the bits taken up by the boolean, and then write back.

This is the compiler's defense against contract upgrades and pointer aliasing, and it cannot be disabled. Use `uint256(0) and uint256(1)` for `true/false` to avoid a Gwarmaccess (**100 gas**) for the extra `SLOAD`.

*There are 10 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

38: 		    bool private _checkLocalEnclaveReport;

39: 		    mapping(bytes32 enclave => bool trusted) private _trustedUserMrEnclave;

40: 		    mapping(bytes32 signer => bool trusted) private _trustedUserMrSigner;

47: 		    mapping(uint256 idx => mapping(bytes serialNum => bool revoked)) private _serialNumIsRevoked;
```
[[38](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L38), [39](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L39), [40](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L40), [47](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L47)]



```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

42: 		    mapping(address addr => bool banned) public addressBanned;
```
[[42](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L42)]



```solidity
File: packages/protocol/contracts/signal/SignalService.sol

21: 		    mapping(address addr => bool authorized) public isAuthorized;
```
[[21](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L21)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

14: 		    bool public migratingInbound;
```
[[14](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L14)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

52: 		    mapping(address btoken => bool blacklisted) public btokenBlacklist;
```
[[52](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L52)]



```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

55: 		    mapping(address instanceAddress => bool alreadyAttested) public addressRegistered;
```
[[55](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L55)]



```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

12: 		    mapping(bytes32 hash => bool claimed) public isClaimed;
```
[[12](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L12)]

</details>

---

### [G-48] Mappings are cheaper to use than storage arrays

When using storage arrays, solidity adds an internal lookup of the array's length (a **Gcoldsload 2100 gas**) to ensure you don't read past the array's end.

You can avoid this lookup by using a mapping and storing the number of entries in a separate storage variable. In cases where you have sentinel values (e.g. 'zero' means invalid), you can avoid length checks.

*There are 36 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

48: 		    uint256[43] private __gap;
```
[[48](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L48)]



```solidity
File: packages/protocol/contracts/common/AddressManager.sol

14: 		    uint256[49] private __gap;
```
[[14](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressManager.sol#L14)]



```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

14: 		    uint256[49] private __gap;
```
[[14](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressResolver.sol#L14)]



```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

25: 		    uint256[49] private __gap;
```
[[25](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L25)]



```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

26: 		    uint256[50] private __gap;
```
[[26](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L26)]



```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

16: 		    uint256[50] private __gap;
```
[[16](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoToken.sol#L16)]



```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

21: 		    uint256[49] private __gap;
```
[[21](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L21)]



```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

52: 		    uint256[47] private __gap;
```
[[52](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L52)]



```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

13: 		    uint256[49] private __gap;
```
[[13](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L13)]



```solidity
File: packages/protocol/contracts/signal/SignalService.sol

23: 		    uint256[48] private __gap;
```
[[23](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L23)]



```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

82: 		    uint128[44] private __gap;
```
[[82](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L82)]



```solidity
File: packages/protocol/contracts/tokenvault/BaseNFTVault.sol

61: 		    uint256[48] private __gap;
```
[[61](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L61)]



```solidity
File: packages/protocol/contracts/tokenvault/BaseVault.sol

18: 		    uint256[50] private __gap;
```
[[18](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseVault.sol#L18)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

27: 		    uint256[46] private __gap;
```
[[27](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L27)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

32: 		    uint256[47] private __gap;
```
[[32](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L32)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

16: 		    uint256[49] private __gap;
```
[[16](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L16)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

19: 		    uint256[48] private __gap;
```
[[19](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L19)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

32: 		    uint256[50] private __gap;
```
[[32](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L32)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

54: 		    uint256[47] private __gap;
```
[[54](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L54)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

19: 		    uint256[50] private __gap;
```
[[19](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L19)]



```solidity
File: packages/protocol/contracts/verifiers/GuardianVerifier.sol

11: 		    uint256[50] private __gap;
```
[[11](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L11)]



```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

57: 		    uint256[47] private __gap;
```
[[57](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L57)]



```solidity
File: packages/protocol/contracts/L1/gov/TaikoGovernor.sol

23: 		    uint256[50] private __gap;
```
[[23](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L23)]



```solidity
File: packages/protocol/contracts/L1/gov/TaikoTimelockController.sol

10: 		    uint256[50] private __gap;
```
[[10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L10)]



```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

40: 		    uint256[50] private __gap;
```
[[40](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L40)]



```solidity
File: packages/protocol/contracts/L1/provers/GuardianProver.sol

11: 		    uint256[50] private __gap;
```
[[11](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/GuardianProver.sol#L11)]



```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

23: 		    address[] public guardians;

32: 		    uint256[46] private __gap;
```
[[23](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L23), [32](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L32)]



```solidity
File: packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol

11: 		    uint256[50] private __gap;
```
[[11](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L11)]



```solidity
File: packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol

11: 		    uint256[50] private __gap;
```
[[11](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L11)]



```solidity
File: packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol

11: 		    uint256[50] private __gap;
```
[[11](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L11)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

18: 		    uint256[48] private __gap;
```
[[18](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L18)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

30: 		    uint256[45] private __gap;
```
[[30](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L30)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

16: 		    uint256[48] private __gap;
```
[[16](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L16)]



```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

23: 		    uint256[47] private __gap;
```
[[23](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L23)]



```solidity
File: packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

32: 		    uint256[49] private __gap;
```
[[32](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L32)]

</details>

---

### [G-49] Bytes constants are more efficient than string constants

If a string can fit in 32 bytes is it better to use `bytes32` instead of `string`, as it is cheaper.

```solidity
// @audit avoid this
string constant stringVariable = "LessThan32Bytes";

// @audit as this is cheaper
bytes32 constant stringVariable = "LessThan32Bytes";
```

*There are 5 instances of this issue.*


```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

17: 		    string internal constant HEADER = "-----BEGIN CERTIFICATE-----";

18: 		    string internal constant FOOTER = "-----END CERTIFICATE-----";

22: 		    string internal constant PCK_COMMON_NAME = "Intel SGX PCK Certificate";

23: 		    string internal constant PLATFORM_ISSUER_NAME = "Intel SGX PCK Platform CA";

24: 		    string internal constant PROCESSOR_ISSUER_NAME = "Intel SGX PCK Processor CA";
```
[[17](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L17), [18](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L18), [22](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L22), [23](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L23), [24](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L24)]


---

### [G-50] Constructors can be marked `payable`

`payable` functions cost less gas to execute, since the compiler does not have to add extra checks to ensure that a payment wasn't provided.

A `constructor` can safely be marked as `payable`, since only the deployer would be able to pass funds, and the project itself would not pass any funds.

*There are 3 instances of this issue.*


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

54: 		    constructor(address sigVerifyLibAddr, address pemCertLibAddr) {
```
[[54](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L54)]



```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

64: 		    constructor() {
```
[[64](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L64)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

20: 		    constructor(address es256Verifier) {
```
[[20](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L20)]


---

### [G-51] Inverting the `if` condition wastes gas

Flipping the `true` and `false` blocks instead saves 3 gas.

*There are 2 instances of this issue.*


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

209: 		        } else if (!isMessageProven) {
210: 		            emit MessageReceived(msgHash, _message, true);
211: 		        } else {
212: 		            revert B_INVOCATION_TOO_EARLY();
213: 		        }

302: 		        } else if (!isMessageProven) {
303: 		            emit MessageReceived(msgHash, _message, false);
304: 		        } else {
305: 		            revert B_INVOCATION_TOO_EARLY();
306: 		        }
```
[[209-213](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L209-L213), [302-306](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L302-L306)]


---

### [G-52] Long revert strings

Considering refactoring the revert message to fit in 32 bytes to avoid using more than one memory slot.

*There are 27 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

87: 		        require(
88: 		            v3Quote.v3AuthData.certification.certType == 5,
89: 		            "certType must be 5: Concatenated PCK Cert Chain (PEM formatted)"
90: 		        );
```
[[87-90](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L87-L90)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

37: 		        require(
38: 		            _in.length > 0,
39: 		            "RLPReader: length of an RLP item must be greater than zero to be decodable"
40: 		        );

56: 		        require(
57: 		            itemType == RLPItemType.LIST_ITEM,
58: 		            "RLPReader: decoded item type for list is not a list item"
59: 		        );

61: 		        require(
62: 		            listOffset + listLength == _in.length,
63: 		            "RLPReader: list item has an invalid data remainder"
64: 		        );

112: 		        require(
113: 		            itemType == RLPItemType.DATA_ITEM,
114: 		            "RLPReader: decoded item type for bytes is not a data item"
115: 		        );

117: 		        require(
118: 		            _in.length == itemOffset + itemLength,
119: 		            "RLPReader: bytes value contains an invalid remainder"
120: 		        );

152: 		        require(
153: 		            _in.length > 0,
154: 		            "RLPReader: length of an RLP item must be greater than zero to be decodable"
155: 		        );

172: 		            require(
173: 		                _in.length > strLen,
174: 		                "RLPReader: length of content must be greater than string length (short string)"
175: 		            );

182: 		            require(
183: 		                strLen != 1 || firstByteOfContent >= 0x80,
184: 		                "RLPReader: invalid prefix, single byte < 0x80 are not prefixed (short string)"
185: 		            );

192: 		            require(
193: 		                _in.length > lenOfStrLen,
194: 		                "RLPReader: length of content must be > than length of string length (long string)"
195: 		            );

202: 		            require(
203: 		                firstByteOfContent != 0x00,
204: 		                "RLPReader: length of content must not have any leading zeros (long string)"
205: 		            );

212: 		            require(
213: 		                strLen > 55,
214: 		                "RLPReader: length of content must be greater than 55 bytes (long string)"
215: 		            );

217: 		            require(
218: 		                _in.length > lenOfStrLen + strLen,
219: 		                "RLPReader: length of content must be greater than total length (long string)"
220: 		            );

228: 		            require(
229: 		                _in.length > listLen,
230: 		                "RLPReader: length of content must be greater than list length (short list)"
231: 		            );

238: 		            require(
239: 		                _in.length > lenOfListLen,
240: 		                "RLPReader: length of content must be > than length of list length (long list)"
241: 		            );

248: 		            require(
249: 		                firstByteOfContent != 0x00,
250: 		                "RLPReader: length of content must not have any leading zeros (long list)"
251: 		            );

258: 		            require(
259: 		                listLen > 55,
260: 		                "RLPReader: length of content must be greater than 55 bytes (long list)"
261: 		            );

263: 		            require(
264: 		                _in.length > lenOfListLen + listLen,
265: 		                "RLPReader: length of content must be greater than total length (long list)"
266: 		            );
```
[[37-40](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L37-L40), [56-59](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L56-L59), [61-64](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L61-L64), [112-115](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L112-L115), [117-120](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L117-L120), [152-155](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L152-L155), [172-175](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L172-L175), [182-185](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L182-L185), [192-195](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L192-L195), [202-205](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L202-L205), [212-215](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L212-L215), [217-220](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L217-L220), [228-231](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L228-L231), [238-241](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L238-L241), [248-251](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L248-L251), [258-261](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L258-L261), [263-266](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L263-L266)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

89: 		            require(currentKeyIndex <= key.length, "MerkleTrie: key index exceeds total key length");

99: 		                require(
100: 		                    Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
101: 		                    "MerkleTrie: invalid large internal hash"
102: 		                );

105: 		                require(
106: 		                    Bytes.equal(currentNode.encoded, currentNodeID),
107: 		                    "MerkleTrie: invalid internal node hash"
108: 		                );

119: 		                    require(
120: 		                        value_.length > 0,
121: 		                        "MerkleTrie: value length must be greater than zero (branch)"
122: 		                    );

125: 		                    require(
126: 		                        i == proof.length - 1,
127: 		                        "MerkleTrie: value node must be last node in proof (branch)"
128: 		                    );

150: 		                require(
151: 		                    pathRemainder.length == sharedNibbleLength,
152: 		                    "MerkleTrie: path remainder must share all nibbles with key"
153: 		                );

162: 		                    require(
163: 		                        keyRemainder.length == sharedNibbleLength,
164: 		                        "MerkleTrie: key remainder must be identical to path remainder"
165: 		                    );

172: 		                    require(
173: 		                        value_.length > 0,
174: 		                        "MerkleTrie: value length must be greater than zero (leaf)"
175: 		                    );

178: 		                    require(
179: 		                        i == proof.length - 1,
180: 		                        "MerkleTrie: value node must be last node in proof (leaf)"
181: 		                    );
```
[[89](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L89), [99-102](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L99-L102), [105-108](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L105-L108), [119-122](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L119-L122), [125-128](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L125-L128), [150-153](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L150-L153), [162-165](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L162-L165), [172-175](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L172-L175), [178-181](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L178-L181)]

</details>

---

### [G-53] Nesting `if` statements that use `&&` saves gas

Using the `&&` operator on a single `if` [costs more gas](https://gist.github.com/DadeKuma/931ce6794a050201ec6544dbcc31316c) than using two nested `if`.

*There are 23 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

220: 		            if (pceSvnIsHigherOrGreater && cpuSvnsAreHigherOrGreater) {
```
[[220](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L220)]



```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

250: 		        if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) {

260: 		            if (_message.gasLimit == 0 && msg.sender != _message.destOwner) {

439: 		        } else if (block.chainid >= 32_300 && block.chainid <= 32_400) {

491: 		            _message.data.length >= 4 // msg can be empty
492: 		                && bytes4(_message.data) != IMessageInvocable.onMessageInvocation.selector
493: 		                && _message.to.isContract()
```
[[250](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L250), [260](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L260), [439](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L439), [491-493](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L491-L493)]



```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

85: 		        if (!_allowZeroAddress && addr_ == address(0)) {
```
[[85](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressResolver.sol#L85)]



```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

42: 		        if (msg.sender != owner() && msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();
```
[[42](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L42)]



```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

117: 		            _l1BlockHash == 0 || _l1StateRoot == 0 || _l1BlockId == 0
118: 		                || (block.number != 1 && _parentGasUsed == 0)

141: 		        if (!skipFeeCheck() && block.basefee != basefee) {

275: 		            if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {
```
[[117-118](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L117-L118), [141](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L141), [275](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L275)]



```solidity
File: packages/protocol/contracts/signal/SignalService.sol

285: 		        if (cacheStateRoot && _isFullProof && !_isLastHop) {

293: 		        if (cacheSignalRoot && (_isFullProof || !_isLastHop)) {
```
[[285](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L285), [293](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L293)]



```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

277: 		            if (_cliff > 0 && _cliff <= _start) revert INVALID_GRANT();
```
[[277](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L277)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

38: 		        if (msg.sender != owner() && msg.sender != snapshooter) {
```
[[38](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L38)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

45: 		        if (_migratingAddress == migratingAddress && _migratingInbound == migratingInbound) {
```
[[45](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L45)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

135: 		                (notBeforeTag != 0x17 && notBeforeTag == 0x18)
136: 		                    || (notAfterTag != 0x17 && notAfterTag != 0x18)
```
[[135-136](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L135-L136)]



```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

82: 		            block.timestamp > assignment.expiry
83: 		                || assignment.metaHash != 0 && _blk.metaHash != assignment.metaHash
84: 		                || assignment.parentMetaHash != 0 && _meta.parentMetaHash != assignment.parentMetaHash
85: 		                || assignment.maxBlockId != 0 && _meta.id > assignment.maxBlockId
86: 		                || assignment.maxProposedIn != 0 && block.number > assignment.maxProposedIn

120: 		        if (input.tip != 0 && block.coinbase != address(0)) {
```
[[82-86](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L82-L86), [120](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L120)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

108: 		        if (params.parentMetaHash != 0 && parentMetaHash != params.parentMetaHash) {

164: 		                if (_config.blobReuseEnabled && params.cacheBlobForReuse) {

310: 		            if (proposerOne != address(0) && msg.sender != proposerOne) {
```
[[108](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L108), [164](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L164), [310](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L310)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

419: 		        if (_tid == 1 && _ts.tier == 0 && inProvingWindow) {
```
[[419](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L419)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

14: 		        if (_in.length == 1 && uint8(_in[0]) < 128) {
```
[[14](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L14)]

</details>

---

### [G-54] Counting down when iterating, saves gas

Counting down saves **6 gas** per loop, since checks for zero are more efficient than checks against any other value.

*There are 45 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

80: 		        for (uint256 i; i < serialNumBatch.length; ++i) {

95: 		        for (uint256 i; i < serialNumBatch.length; ++i) {

191: 		        for (uint256 i; i < enclaveId.tcbLevels.length; ++i) {

214: 		        for (uint256 i; i < tcb.tcbLevels.length; ++i) {

240: 		        for (uint256 i; i < CPUSVN_LENGTH; ++i) {

259: 		        for (uint256 i; i < n; ++i) {

420: 		            for (uint256 i; i < 3; ++i) {
```
[[80](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L80), [95](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L95), [191](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L191), [214](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L214), [240](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L240), [259](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L259), [420](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L420)]



```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

90: 		        for (uint256 i; i < _msgHashes.length; ++i) {
```
[[90](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L90)]



```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

234: 		            for (uint256 i; i < 255 && _blockId >= i + 1; ++i) {
```
[[234](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L234)]



```solidity
File: packages/protocol/contracts/signal/SignalService.sol

104: 		        for (uint256 i; i < hopProofs.length; ++i) {
```
[[104](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L104)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

47: 		        for (uint256 i; i < _op.amounts.length; ++i) {

251: 		                for (uint256 i; i < _op.tokenIds.length; ++i) {

269: 		                for (uint256 i; i < _op.tokenIds.length; ++i) {
```
[[47](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L47), [251](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L251), [269](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L269)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

34: 		        for (uint256 i; i < _op.tokenIds.length; ++i) {

170: 		            for (uint256 i; i < _tokenIds.length; ++i) {

175: 		            for (uint256 i; i < _tokenIds.length; ++i) {

197: 		                for (uint256 i; i < _op.tokenIds.length; ++i) {

210: 		                for (uint256 i; i < _op.tokenIds.length; ++i) {
```
[[34](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L34), [170](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L170), [175](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L175), [197](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L197), [210](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L210)]



```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

104: 		        for (uint256 i; i < _ids.length; ++i) {

210: 		        for (uint256 i; i < _instances.length; ++i) {
```
[[104](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L104), [210](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

54: 		        for (uint256 i; i < size; ++i) {

244: 		        for (uint256 i; i < split.length; ++i) {

354: 		        for (uint256 i; i < SGX_TCB_CPUSVN_SIZE + 1; ++i) {
```
[[54](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L54), [244](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L244), [354](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L354)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

333: 		        for (uint256 i; i < len; ++i) {
```
[[333](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L333)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

140: 		        for (uint256 i = 2; i < 2 + paddingLen; ++i) {

152: 		            for (uint256 i; i < digestAlgoWithParamLen; ++i) {

158: 		            for (uint256 i; i < digestAlgoWithParamLen; ++i) {

174: 		        for (uint256 i; i < _sha256.length; ++i) {

273: 		        for (uint256 i = 2; i < 2 + paddingLen; ++i) {

283: 		        for (uint256 i; i < sha1Prefix.length; ++i) {

290: 		        for (uint256 i; i < _sha1.length; ++i) {
```
[[140](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L140), [152](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L152), [158](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L158), [174](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L174), [273](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L273), [283](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L283), [290](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L290)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

48: 		        for (uint16 i = 1970; i < year; ++i) {

59: 		        for (uint8 i = 1; i < month; ++i) {
```
[[48](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L48), [59](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L59)]



```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

172: 		        for (uint256 i; i < _tierFees.length; ++i) {
```
[[172](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L172)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

244: 		            for (uint256 i; i < params.hookCalls.length; ++i) {
```
[[244](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L244)]



```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

74: 		        for (uint256 i; i < guardians.length; ++i) {

80: 		        for (uint256 i = 0; i < _newGuardians.length; ++i) {

133: 		            for (uint256 i; i < guardiansLength; ++i) {
```
[[74](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L74), [80](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L80), [133](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L133)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

59: 		        for (uint256 i; i < tokenIds.length; ++i) {
```
[[59](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

153: 		        for (uint256 i; i < encoded.length; ++i) {

281: 		        for (uint256 i; i < 3; ++i) {
```
[[153](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L153), [281](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L281)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

46: 		            for (i = 1; i <= lenLen; i++) {

59: 		        for (; i < 32; i++) {

66: 		        for (uint256 j = 0; j < out_.length; j++) {
```
[[46](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L46), [59](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L59), [66](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

85: 		        for (uint256 i = 0; i < proof.length; i++) {
```
[[85](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85)]

</details>

---

### [G-55] `do-while` is cheaper than `for`-loops when the initial check can be skipped

Example:

```solidity
for (uint256 i; i < len; ++i){ ... } -> do { ...; ++i } while (i < len);
```

*There are 49 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

80: 		        for (uint256 i; i < serialNumBatch.length; ++i) {

95: 		        for (uint256 i; i < serialNumBatch.length; ++i) {

191: 		        for (uint256 i; i < enclaveId.tcbLevels.length; ++i) {

214: 		        for (uint256 i; i < tcb.tcbLevels.length; ++i) {

240: 		        for (uint256 i; i < CPUSVN_LENGTH; ++i) {

259: 		        for (uint256 i; i < n; ++i) {

420: 		            for (uint256 i; i < 3; ++i) {
```
[[80](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L80), [95](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L95), [191](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L191), [214](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L214), [240](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L240), [259](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L259), [420](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L420)]



```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

90: 		        for (uint256 i; i < _msgHashes.length; ++i) {
```
[[90](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L90)]



```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

234: 		            for (uint256 i; i < 255 && _blockId >= i + 1; ++i) {
```
[[234](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L234)]



```solidity
File: packages/protocol/contracts/signal/SignalService.sol

104: 		        for (uint256 i; i < hopProofs.length; ++i) {
```
[[104](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L104)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

47: 		        for (uint256 i; i < _op.amounts.length; ++i) {

251: 		                for (uint256 i; i < _op.tokenIds.length; ++i) {

269: 		                for (uint256 i; i < _op.tokenIds.length; ++i) {
```
[[47](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L47), [251](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L251), [269](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L269)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

34: 		        for (uint256 i; i < _op.tokenIds.length; ++i) {

170: 		            for (uint256 i; i < _tokenIds.length; ++i) {

175: 		            for (uint256 i; i < _tokenIds.length; ++i) {

197: 		                for (uint256 i; i < _op.tokenIds.length; ++i) {

210: 		                for (uint256 i; i < _op.tokenIds.length; ++i) {
```
[[34](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L34), [170](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L170), [175](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L175), [197](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L197), [210](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L210)]



```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

104: 		        for (uint256 i; i < _ids.length; ++i) {

210: 		        for (uint256 i; i < _instances.length; ++i) {
```
[[104](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L104), [210](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

54: 		        for (uint256 i; i < size; ++i) {

244: 		        for (uint256 i; i < split.length; ++i) {

354: 		        for (uint256 i; i < SGX_TCB_CPUSVN_SIZE + 1; ++i) {
```
[[54](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L54), [244](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L244), [354](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L354)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

80: 		        for (uint256 idx = 0; idx < shortest; idx += 32) {

333: 		        for (uint256 i; i < len; ++i) {
```
[[80](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L80), [333](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L333)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

140: 		        for (uint256 i = 2; i < 2 + paddingLen; ++i) {

152: 		            for (uint256 i; i < digestAlgoWithParamLen; ++i) {

158: 		            for (uint256 i; i < digestAlgoWithParamLen; ++i) {

174: 		        for (uint256 i; i < _sha256.length; ++i) {

273: 		        for (uint256 i = 2; i < 2 + paddingLen; ++i) {

283: 		        for (uint256 i; i < sha1Prefix.length; ++i) {

290: 		        for (uint256 i; i < _sha1.length; ++i) {
```
[[140](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L140), [152](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L152), [158](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L158), [174](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L174), [273](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L273), [283](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L283), [290](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L290)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

48: 		        for (uint16 i = 1970; i < year; ++i) {

59: 		        for (uint8 i = 1; i < month; ++i) {
```
[[48](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L48), [59](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L59)]



```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

172: 		        for (uint256 i; i < _tierFees.length; ++i) {
```
[[172](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L172)]



```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

86: 		            for (uint256 i; i < deposits_.length;) {
```
[[86](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L86)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

244: 		            for (uint256 i; i < params.hookCalls.length; ++i) {
```
[[244](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L244)]



```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

74: 		        for (uint256 i; i < guardians.length; ++i) {

80: 		        for (uint256 i = 0; i < _newGuardians.length; ++i) {

133: 		            for (uint256 i; i < guardiansLength; ++i) {
```
[[74](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L74), [80](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L80), [133](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L133)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

59: 		        for (uint256 i; i < tokenIds.length; ++i) {
```
[[59](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

153: 		        for (uint256 i; i < encoded.length; ++i) {

281: 		        for (uint256 i; i < 3; ++i) {
```
[[153](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L153), [281](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L281)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

46: 		            for (i = 1; i <= lenLen; i++) {

59: 		        for (; i < 32; i++) {

66: 		        for (uint256 j = 0; j < out_.length; j++) {
```
[[46](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L46), [59](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L59), [66](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

85: 		        for (uint256 i = 0; i < proof.length; i++) {

208: 		        for (uint256 i = 0; i < length;) {

244: 		        for (; shared_ < max && _a[shared_] == _b[shared_];) {
```
[[85](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85), [208](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L208), [244](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L244)]

</details>

---

### [G-56] Lack of `unchecked` in loops

Use `unchecked` to increment the loop variable as it can save gas:

```solidity
for(uint256 i; i < length;) {
	unchecked{
		++i;
	}
}
```

*There are 39 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

80: 		        for (uint256 i; i < serialNumBatch.length; ++i) {

95: 		        for (uint256 i; i < serialNumBatch.length; ++i) {

191: 		        for (uint256 i; i < enclaveId.tcbLevels.length; ++i) {

214: 		        for (uint256 i; i < tcb.tcbLevels.length; ++i) {

240: 		        for (uint256 i; i < CPUSVN_LENGTH; ++i) {

259: 		        for (uint256 i; i < n; ++i) {

420: 		            for (uint256 i; i < 3; ++i) {
```
[[80](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L80), [95](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L95), [191](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L191), [214](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L214), [240](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L240), [259](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L259), [420](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L420)]



```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

90: 		        for (uint256 i; i < _msgHashes.length; ++i) {
```
[[90](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L90)]



```solidity
File: packages/protocol/contracts/signal/SignalService.sol

104: 		        for (uint256 i; i < hopProofs.length; ++i) {
```
[[104](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L104)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

47: 		        for (uint256 i; i < _op.amounts.length; ++i) {
```
[[47](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L47)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

34: 		        for (uint256 i; i < _op.tokenIds.length; ++i) {

170: 		            for (uint256 i; i < _tokenIds.length; ++i) {

175: 		            for (uint256 i; i < _tokenIds.length; ++i) {
```
[[34](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L34), [170](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L170), [175](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L175)]



```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

104: 		        for (uint256 i; i < _ids.length; ++i) {

210: 		        for (uint256 i; i < _instances.length; ++i) {
```
[[104](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L104), [210](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

54: 		        for (uint256 i; i < size; ++i) {

244: 		        for (uint256 i; i < split.length; ++i) {

354: 		        for (uint256 i; i < SGX_TCB_CPUSVN_SIZE + 1; ++i) {
```
[[54](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L54), [244](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L244), [354](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L354)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

333: 		        for (uint256 i; i < len; ++i) {
```
[[333](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L333)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

140: 		        for (uint256 i = 2; i < 2 + paddingLen; ++i) {

152: 		            for (uint256 i; i < digestAlgoWithParamLen; ++i) {

158: 		            for (uint256 i; i < digestAlgoWithParamLen; ++i) {

174: 		        for (uint256 i; i < _sha256.length; ++i) {

273: 		        for (uint256 i = 2; i < 2 + paddingLen; ++i) {

283: 		        for (uint256 i; i < sha1Prefix.length; ++i) {

290: 		        for (uint256 i; i < _sha1.length; ++i) {
```
[[140](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L140), [152](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L152), [158](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L158), [174](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L174), [273](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L273), [283](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L283), [290](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L290)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

48: 		        for (uint16 i = 1970; i < year; ++i) {

59: 		        for (uint8 i = 1; i < month; ++i) {
```
[[48](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L48), [59](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L59)]



```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

172: 		        for (uint256 i; i < _tierFees.length; ++i) {
```
[[172](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L172)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

244: 		            for (uint256 i; i < params.hookCalls.length; ++i) {
```
[[244](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L244)]



```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

74: 		        for (uint256 i; i < guardians.length; ++i) {

80: 		        for (uint256 i = 0; i < _newGuardians.length; ++i) {
```
[[74](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L74), [80](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L80)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

59: 		        for (uint256 i; i < tokenIds.length; ++i) {
```
[[59](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

153: 		        for (uint256 i; i < encoded.length; ++i) {

281: 		        for (uint256 i; i < 3; ++i) {
```
[[153](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L153), [281](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L281)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

46: 		            for (i = 1; i <= lenLen; i++) {

59: 		        for (; i < 32; i++) {

66: 		        for (uint256 j = 0; j < out_.length; j++) {
```
[[46](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L46), [59](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L59), [66](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

85: 		        for (uint256 i = 0; i < proof.length; i++) {
```
[[85](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85)]

</details>

---

### [G-57] `uint` comparison with zero can be cheaper

Checking for `!= 0` is cheaper than `> 0` for unsigned integers.

*There are 15 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

262: 		        if (gasExcess > 0) {

275: 		            if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {

279: 		            if (numL1Blocks > 0) {
```
[[262](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L262), [275](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L275), [279](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L279)]



```solidity
File: packages/protocol/contracts/signal/SignalService.sol

120: 		            bool isFullProof = hop.accountProof.length > 0;
```
[[120](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L120)]



```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

275: 		            if (_cliff > 0) revert INVALID_GRANT();

277: 		            if (_cliff > 0 && _cliff <= _start) revert INVALID_GRANT();
```
[[275](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L275), [277](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L277)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

56: 		            if (i > 0) {
```
[[56](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L56)]



```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

125: 		        if (address(this).balance > 0) {
```
[[125](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L125)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

192: 		            bool returnLivenessBond = blk.livenessBond > 0 && _proof.data.length == 32
```
[[192](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L192)]



```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

212: 		            if (numBlocksVerified > 0) {
```
[[212](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L212)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

38: 		            _in.length > 0,

153: 		            _in.length > 0,
```
[[38](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L38), [153](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L153)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

77: 		        require(_key.length > 0, "MerkleTrie: empty key");

120: 		                        value_.length > 0,

173: 		                        value_.length > 0,
```
[[77](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L77), [120](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L120), [173](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L173)]

</details>

---

### [G-58] Use assembly to check for `address(0)`

[A simple zero address check](https://medium.com/@kalexotsu/solidity-assembly-checking-if-an-address-is-0-efficiently-d2bfe071331) can be written in assembly to save some gas.

*There are 74 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

124: 		        if (_message.srcOwner == address(0) || _message.destOwner == address(0)) {

124: 		        if (_message.srcOwner == address(0) || _message.destOwner == address(0)) {

124: 		        if (_message.srcOwner == address(0) || _message.destOwner == address(0)) {

270: 		                _message.to == address(0) || _message.to == address(this)
271: 		                    || _message.to == signalService || addressBanned[_message.to]

270: 		                _message.to == address(0) || _message.to == address(this)
271: 		                    || _message.to == signalService || addressBanned[_message.to]

270: 		                _message.to == address(0) || _message.to == address(this)

270: 		                _message.to == address(0) || _message.to == address(this)

291: 		                _message.refundTo == address(0) ? _message.destOwner : _message.refundTo;

398: 		        enabled_ = destBridge_ != address(0);

398: 		        enabled_ = destBridge_ != address(0);
```
[[124](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L124), [124](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L124), [124](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L124), [270-271](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L270-L271), [270-271](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L270-L271), [270](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L270), [270](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L270), [291](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L291), [398](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L398), [398](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L398)]



```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

81: 		        if (addressManager == address(0)) revert RESOLVER_INVALID_MANAGER();

85: 		        if (!_allowZeroAddress && addr_ == address(0)) {

85: 		        if (!_allowZeroAddress && addr_ == address(0)) {
```
[[81](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressResolver.sol#L81), [85](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressResolver.sol#L85), [85](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressResolver.sol#L85)]



```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

105: 		        if (_addressManager == address(0)) revert ZERO_ADDR_MANAGER();

110: 		        _transferOwnership(_owner == address(0) ? msg.sender : _owner);
```
[[105](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L105), [110](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L110)]



```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

172: 		        if (_to == address(0)) revert L2_INVALID_PARAM();

173: 		        if (_token == address(0)) {
```
[[172](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L172), [173](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L173)]



```solidity
File: packages/protocol/contracts/libs/LibAddress.sol

24: 		        if (_to == address(0)) revert ETH_TRANSFER_FAILED();
```
[[24](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibAddress.sol#L24)]



```solidity
File: packages/protocol/contracts/signal/SignalService.sol

36: 		        if (_app == address(0)) revert SS_INVALID_SENDER();
```
[[36](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L36)]



```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

121: 		        if (_taikoToken == address(0)) revert INVALID_PARAM();

124: 		        if (_costToken == address(0)) revert INVALID_PARAM();

127: 		        if (_sharedVault == address(0)) revert INVALID_PARAM();

136: 		        if (_recipient == address(0)) revert INVALID_PARAM();

169: 		        if (_to == address(0)) revert INVALID_PARAM();
```
[[121](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L121), [124](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L124), [127](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L127), [136](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L136), [169](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L169)]



```solidity
File: packages/protocol/contracts/tokenvault/BaseNFTVault.sol

149: 		        if (_op.token == address(0)) revert VAULT_INVALID_TOKEN();
```
[[149](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L149)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

102: 		        return migratingAddress != address(0) && !migratingInbound;

102: 		        return migratingAddress != address(0) && !migratingInbound;
```
[[102](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L102), [102](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L102)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

64: 		            destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,

108: 		        if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

108: 		        if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

249: 		            if (bridgedToCanonical[_op.token].addr != address(0)) {

293: 		        if (btoken_ == address(0)) {
```
[[64](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L64), [108](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L108), [108](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L108), [249](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L249), [293](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L293)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

158: 		        if (_btokenNew == address(0) || bridgedToCanonical[_btokenNew].addr != address(0)) {

158: 		        if (_btokenNew == address(0) || bridgedToCanonical[_btokenNew].addr != address(0)) {

158: 		        if (_btokenNew == address(0) || bridgedToCanonical[_btokenNew].addr != address(0)) {

170: 		        if (btokenOld_ != address(0)) {

215: 		        if (_op.token == address(0)) revert VAULT_INVALID_TOKEN();

227: 		            destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,

267: 		        if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

267: 		        if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

358: 		        if (bridgedToCanonical[_token].addr != address(0)) {

397: 		        if (btoken == address(0)) {
```
[[158](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L158), [158](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L158), [158](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L158), [170](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L170), [215](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L215), [227](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L227), [267](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L267), [267](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L267), [358](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L358), [397](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L397)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

50: 		            destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,

91: 		        if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

91: 		        if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

195: 		            if (bridgedToCanonical[_op.token].addr != address(0)) {

230: 		        if (btoken_ == address(0)) {
```
[[50](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L50), [91](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L91), [91](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L91), [195](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L195), [230](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L230)]



```solidity
File: packages/protocol/contracts/tokenvault/LibBridgedToken.sol

21: 		            _srcToken == address(0) || _srcChainId == 0 || _srcChainId == block.chainid
22: 		                || bytes(_symbol).length == 0 || bytes(_name).length == 0

21: 		            _srcToken == address(0) || _srcChainId == 0 || _srcChainId == block.chainid
22: 		                || bytes(_symbol).length == 0 || bytes(_name).length == 0

21: 		            _srcToken == address(0) || _srcChainId == 0 || _srcChainId == block.chainid

21: 		            _srcToken == address(0) || _srcChainId == 0 || _srcChainId == block.chainid

21: 		            _srcToken == address(0) || _srcChainId == 0 || _srcChainId == block.chainid
```
[[21-22](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L21-L22), [21-22](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L21-L22), [21](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L21), [21](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L21), [21](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L21)]



```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

107: 		            if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();

124: 		        if (automataDcapAttestation == address(0)) {

215: 		            if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();

234: 		        if (instance == address(0)) return false;
```
[[107](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L107), [124](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L124), [215](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L215), [234](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L234)]



```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

109: 		        if (assignment.feeToken == address(0)) {

120: 		        if (input.tip != 0 && block.coinbase != address(0)) {

120: 		        if (input.tip != 0 && block.coinbase != address(0)) {
```
[[109](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L109), [120](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L120), [120](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L120)]



```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

44: 		        address recipient_ = _recipient == address(0) ? msg.sender : _recipient;
```
[[44](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L44)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

81: 		        if (params.assignedProver == address(0)) {

85: 		        if (params.coinbase == address(0)) {

310: 		            if (proposerOne != address(0) && msg.sender != proposerOne) {

310: 		            if (proposerOne != address(0) && msg.sender != proposerOne) {

316: 		        return proposer == address(0) || msg.sender == proposer;

316: 		        return proposer == address(0) || msg.sender == proposer;
```
[[81](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L81), [85](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L85), [310](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L310), [310](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L310), [316](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L316), [316](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L316)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

163: 		            if (verifier != address(0)) {

224: 		                assert(ts.validityBond == 0 && ts.contestBond == 0 && ts.contester == address(0));

224: 		                assert(ts.validityBond == 0 && ts.contestBond == 0 && ts.contester == address(0));

239: 		                if (ts.contester != address(0)) revert L1_ALREADY_CONTESTED();

363: 		        if (_ts.contester != address(0)) {
```
[[163](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L163), [224](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L224), [224](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L224), [239](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L239), [363](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L363)]



```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

145: 		                if (ts.contester != address(0)) {

148: 		                    if (tierProvider == address(0)) {
```
[[145](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L145), [148](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L148)]



```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

82: 		            if (guardian == address(0)) revert INVALID_GUARDIAN();
```
[[82](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L82)]

</details>

---

### [G-59] Use scratch space for building calldata with assembly

If an external call's calldata can fit into two or fewer words, use the scratch space to build the calldata, rather than allowing Solidity to do a memory expansion.

*There are 333 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

167: 		            V3Parser.parseInput(quote, address(pemCertLib));

313: 		        bytes32 expectedAuthDataHash = bytes32(qeEnclaveReport.reportData.substring(0, 32));

321: 		                V3Parser.packQEReport(authDataV3.pckSignedQeReport);

378: 		        ) = V3Parser.validateParsedInput(v3quote);

424: 		                (certDecodedSuccessfully, parsedQuoteCerts[i]) = pemCertLib.decodeCert(
425: 		                    authDataV3.certification.decodedCertDataArray[i], isPckCert
426: 		                );

437: 		            bool tcbConfigured = LibString.eq(parsedFmspc, fetchedTcbInfo.fmspc);

443: 		            bool pceidMatched = LibString.eq(pckCert.pck.sgxExtension.pceid, fetchedTcbInfo.pceid);
```
[[167](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L167), [313](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L313), [321](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L321), [378](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L378), [424-426](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L424-L426), [437](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L437), [443](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L443)]



```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

150: 		        ISignalService(resolve("signal_service", false)).sendSignal(msgHash_);

174: 		            if (!ISignalService(signalService).isSignalSent(address(this), msgHash)) {

195: 		            if (_message.from.supportsInterface(type(IRecallableSender).interfaceId)) {

206: 		                _message.srcOwner.sendEther(_message.value);

295: 		                refundTo.sendEther(_message.fee + refundAmount);

298: 		                msg.sender.sendEther(_message.fee);

299: 		                refundTo.sendEther(refundAmount);

342: 		        return ISignalService(resolve("signal_service", false)).isSignalSent({
343: 		            _app: address(this),
344: 		            _signal: hashMessage(_message)
345: 		        });

493: 		                && _message.to.isContract()

522: 		            ISignalService(resolve("signal_service", false)).sendSignal(
523: 		                signalForFailedMessage(_msgHash)
524: 		            );

591: 		        (success_,) = _signalService.staticcall(data);
```
[[150](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L150), [174](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L174), [195](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L195), [206](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L206), [295](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L295), [298](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L298), [299](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L299), [342-345](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L342-L345), [493](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L493), [522-524](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L522-L524), [591](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L591)]



```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

83: 		        addr_ = payable(IAddressManager(addressManager).getAddress(_chainId, _name));
```
[[83](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressResolver.sol#L83)]



```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

113: 		        LibProving.pauseProving(state, _pause);
```
[[113](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L113)]



```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

45: 		        IBridge.Context memory ctx = IBridge(msg.sender).context();

50: 		        (bool success,) = address(this).call(txdata);
```
[[45](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L45), [50](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L50)]



```solidity
File: packages/protocol/contracts/L2/Lib1559Math.sol

45: 		        return uint256(LibFixedPointMath.exp(int256(input)));
```
[[45](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/Lib1559Math.sol#L45)]



```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

174: 		            _to.sendEther(address(this).balance);

176: 		            IERC20(_token).safeTransfer(_to, IERC20(_token).balanceOf(address(this)));

176: 		            IERC20(_token).safeTransfer(_to, IERC20(_token).balanceOf(address(this)));

284: 		            gasExcess_ = uint64(excess.min(type(uint64).max));

290: 		            basefee_ = Lib1559Math.basefee(
291: 		                gasExcess_, uint256(_config.basefeeAdjustmentQuotient) * _config.gasTargetPerL1Block
292: 		            );
```
[[174](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L174), [176](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L176), [176](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L176), [284](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L284), [290-292](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L290-L292)]



```solidity
File: packages/protocol/contracts/libs/Lib4844.sol

43: 		        (bool ok, bytes memory ret) = POINT_EVALUATION_PRECOMPILE_ADDRESS.staticcall(
44: 		            abi.encodePacked(_blobHash, _x, _y, _commitment, _pointProof)
45: 		        );
```
[[43-45](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/Lib4844.sol#L43-L45)]



```solidity
File: packages/protocol/contracts/libs/LibAddress.sol

54: 		        if (!Address.isContract(_addr)) return false;

56: 		        try IERC165(_addr).supportsInterface(_interfaceId) returns (bool _result) {

70: 		        if (Address.isContract(_addr)) {

71: 		            return IERC1271(_addr).isValidSignature(_hash, _sig) == _EIP1271_MAGICVALUE;

73: 		            return ECDSA.recover(_hash, _sig) == _addr;
```
[[54](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibAddress.sol#L54), [56](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibAddress.sol#L56), [70](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibAddress.sol#L70), [71](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibAddress.sol#L71), [73](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibAddress.sol#L73)]



```solidity
File: packages/protocol/contracts/libs/LibTrieProof.sol

52: 		            RLPReader.RLPItem[] memory accountState = RLPReader.readList(rlpAccount);

55: 		                bytes32(RLPReader.readBytes(accountState[_ACCOUNT_FIELD_INDEX_STORAGE_HASH]));

61: 		            bytes.concat(_slot), RLPWriter.writeUint(uint256(_value)), _storageProof, storageRoot_

61: 		            bytes.concat(_slot), RLPWriter.writeUint(uint256(_value)), _storageProof, storageRoot_
```
[[52](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibTrieProof.sol#L52), [55](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibTrieProof.sol#L55), [61](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibTrieProof.sol#L61), [61](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibTrieProof.sol#L61)]



```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

171: 		        address recipient = ECDSA.recover(hash, _sig);
```
[[171](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L171)]



```solidity
File: packages/protocol/contracts/tokenvault/BaseVault.sol

53: 		        ctx_ = IBridge(msg.sender).context();

64: 		        ctx_ = IBridge(msg.sender).context();
```
[[53](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseVault.sol#L53), [64](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseVault.sol#L64)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

54: 		        __ERC1155_init(LibBridgedToken.buildURI(_srcToken, _srcChainId));

116: 		        return LibBridgedToken.buildName(__name, srcChainId);

122: 		        return LibBridgedToken.buildSymbol(__symbol);
```
[[54](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L54), [116](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L116), [122](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L122)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

97: 		        return LibBridgedToken.buildName(super.name(), srcChainId);

108: 		        return LibBridgedToken.buildSymbol(super.symbol());
```
[[97](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L97), [108](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L108)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

82: 		            IBridgedERC20(migratingAddress).mint(_account, _amount);
```
[[82](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L82)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

88: 		        return LibBridgedToken.buildName(super.name(), srcChainId);

94: 		        return LibBridgedToken.buildSymbol(super.symbol());

110: 		                LibBridgedToken.buildURI(srcToken, srcChainId), Strings.toString(_tokenId)

110: 		                LibBridgedToken.buildURI(srcToken, srcChainId), Strings.toString(_tokenId)
```
[[88](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L88), [94](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L94), [110](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L110), [110](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L110)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

51: 		        if (!_op.token.supportsInterface(ERC1155_INTERFACE_ID)) {

112: 		        to.sendEther(msg.value);

146: 		        message.srcOwner.sendEther(message.value);

200: 		            || BaseVault.supportsInterface(interfaceId);

263: 		                try t.name() returns (string memory _name) {

266: 		                try t.symbol() returns (string memory _symbol) {
```
[[51](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L51), [112](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L112), [146](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L146), [200](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L200), [263](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L263), [266](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L266)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

164: 		        if (IBridgedERC20(_btokenNew).owner() != owner()) {

184: 		            IBridgedERC20(btokenOld_).changeMigrationStatus(_btokenNew, false);

185: 		            IBridgedERC20(_btokenNew).changeMigrationStatus(btokenOld_, true);

271: 		        to.sendEther(msg.value);

304: 		        _message.srcOwner.sendEther(_message.value);

330: 		            IERC20(token_).safeTransfer(_to, _amount);

333: 		            IBridgedERC20(token_).mint(_to, _amount);

360: 		            IBridgedERC20(_token).burn(msg.sender, _amount);

368: 		                decimals: meta.decimals(),

369: 		                symbol: meta.symbol(),

370: 		                name: meta.name()

378: 		            uint256 _balance = t.balanceOf(address(this));

380: 		            balanceChange_ = t.balanceOf(address(this)) - _balance;
```
[[164](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L164), [184](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L184), [185](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L185), [271](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L271), [304](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L304), [330](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L330), [333](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L333), [360](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L360), [368](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L368), [369](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L369), [370](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L370), [378](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L378), [380](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L380)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

38: 		        if (!_op.token.supportsInterface(ERC721_INTERFACE_ID)) {

95: 		        to.sendEther(msg.value);

129: 		        _message.srcOwner.sendEther(_message.value);

176: 		                BridgedERC721(token_).mint(_to, _tokenIds[i]);

198: 		                    BridgedERC721(_op.token).burn(_user, _op.tokenIds[i]);

206: 		                    symbol: t.symbol(),

207: 		                    name: t.name()
```
[[38](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L38), [95](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L95), [129](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L129), [176](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L176), [198](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L198), [206](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L206), [207](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L207)]



```solidity
File: packages/protocol/contracts/tokenvault/LibBridgedToken.sol

36: 		        return string.concat("Bridged ", _name, unicode" (⭀", Strings.toString(_srcChainId), ")");

40: 		        return string.concat(_symbol, ".t");

56: 		                Strings.toHexString(uint160(_srcToken), 20),

58: 		                Strings.toString(_srcChainId),
```
[[36](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L36), [40](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L40), [56](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L56), [58](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L58)]



```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

128: 		        (bool verified,) = IAttestation(automataDcapAttestation).verifyParsedQuote(_attestation);

156: 		        bytes memory signature = Bytes.slice(_proof.data, 24);

159: 		            ECDSA.recover(getSignedHash(_tran, newInstance, _ctx.prover, _ctx.metaHash), signature);

185: 		                ITaikoL1(taikoL1).getConfig().chainId,
```
[[128](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L128), [156](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L156), [159](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L159), [185](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L185)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

82: 		        uint256 root = der.root();

85: 		        uint256 tbsParentPtr = der.firstChildOf(root);

88: 		        uint256 tbsPtr = der.firstChildOf(tbsParentPtr);

104: 		        tbsPtr = der.nextSiblingOf(tbsPtr);

107: 		            bytes memory serialNumBytes = der.bytesAt(tbsPtr);

111: 		        tbsPtr = der.nextSiblingOf(tbsPtr);

112: 		        tbsPtr = der.nextSiblingOf(tbsPtr);

115: 		            uint256 issuerPtr = der.firstChildOf(tbsPtr);

116: 		            issuerPtr = der.firstChildOf(issuerPtr);

117: 		            issuerPtr = der.firstChildOf(issuerPtr);

118: 		            issuerPtr = der.nextSiblingOf(issuerPtr);

119: 		            cert.pck.issuerName = string(der.bytesAt(issuerPtr));

120: 		            bool issuerNameIsValid = LibString.eq(cert.pck.issuerName, PLATFORM_ISSUER_NAME)

121: 		                || LibString.eq(cert.pck.issuerName, PROCESSOR_ISSUER_NAME);

127: 		        tbsPtr = der.nextSiblingOf(tbsPtr);

130: 		            uint256 notBeforePtr = der.firstChildOf(tbsPtr);

131: 		            uint256 notAfterPtr = der.nextSiblingOf(notBeforePtr);

132: 		            bytes1 notBeforeTag = der[notBeforePtr.ixs()];

133: 		            bytes1 notAfterTag = der[notAfterPtr.ixs()];

140: 		            cert.notBefore = X509DateUtils.toTimestamp(der.bytesAt(notBeforePtr));

140: 		            cert.notBefore = X509DateUtils.toTimestamp(der.bytesAt(notBeforePtr));

141: 		            cert.notAfter = X509DateUtils.toTimestamp(der.bytesAt(notAfterPtr));

141: 		            cert.notAfter = X509DateUtils.toTimestamp(der.bytesAt(notAfterPtr));

144: 		        tbsPtr = der.nextSiblingOf(tbsPtr);

147: 		            uint256 subjectPtr = der.firstChildOf(tbsPtr);

148: 		            subjectPtr = der.firstChildOf(subjectPtr);

149: 		            subjectPtr = der.firstChildOf(subjectPtr);

150: 		            subjectPtr = der.nextSiblingOf(subjectPtr);

151: 		            cert.pck.commonName = string(der.bytesAt(subjectPtr));

152: 		            if (!LibString.eq(cert.pck.commonName, PCK_COMMON_NAME)) {

157: 		        tbsPtr = der.nextSiblingOf(tbsPtr);

161: 		            uint256 subjectPublicKeyInfoPtr = der.firstChildOf(tbsPtr);

162: 		            subjectPublicKeyInfoPtr = der.nextSiblingOf(subjectPublicKeyInfoPtr);

166: 		            uint256 sigPtr = der.nextSiblingOf(tbsParentPtr);

167: 		            sigPtr = der.nextSiblingOf(sigPtr);

171: 		            sigPtr = NodePtr.getPtr(sigPtr.ixs() + 3, sigPtr.ixf() + 3, sigPtr.ixl());

171: 		            sigPtr = NodePtr.getPtr(sigPtr.ixs() + 3, sigPtr.ixf() + 3, sigPtr.ixl());

171: 		            sigPtr = NodePtr.getPtr(sigPtr.ixs() + 3, sigPtr.ixf() + 3, sigPtr.ixl());

173: 		            sigPtr = der.firstChildOf(sigPtr);

174: 		            bytes memory sigX = _trimBytes(der.bytesAt(sigPtr), 32);

176: 		            sigPtr = der.nextSiblingOf(sigPtr);

177: 		            bytes memory sigY = _trimBytes(der.bytesAt(sigPtr), 32);

179: 		            cert.tbsCertificate = der.allBytesAt(tbsParentPtr);

180: 		            cert.pubKey = _trimBytes(der.bytesAt(subjectPublicKeyInfoPtr), 64);

186: 		            tbsPtr = der.nextSiblingOf(tbsPtr);

189: 		            if (der[tbsPtr.ixs()] != 0xA3) {

193: 		            tbsPtr = der.firstChildOf(tbsPtr);

194: 		            tbsPtr = der.firstChildOf(tbsPtr);

208: 		            cert.pck.sgxExtension.pceid = LibString.toHexStringNoPrefix(pceidBytes);

209: 		            cert.pck.sgxExtension.fmspc = LibString.toHexStringNoPrefix(fmspcBytes);

222: 		        uint256 beginPos = LibString.indexOf(pemData, HEADER);

223: 		        uint256 endPos = LibString.indexOf(pemData, FOOTER);

241: 		        string[] memory split = LibString.split(contentSlice, string(delimiter));

245: 		            contentStr = LibString.concat(contentStr, split[i]);

266: 		        output = input.substring(lengthDiff, expectedLength);

287: 		            uint256 internalPtr = der.firstChildOf(tbsPtr);

288: 		            if (der[internalPtr.ixs()] != 0x06) {

292: 		            if (BytesUtils.compareBytes(der.bytesAt(internalPtr), SGX_EXTENSION_OID)) {

292: 		            if (BytesUtils.compareBytes(der.bytesAt(internalPtr), SGX_EXTENSION_OID)) {

294: 		                internalPtr = der.nextSiblingOf(internalPtr);

295: 		                uint256 extnValueParentPtr = der.rootOfOctetStringAt(internalPtr);

296: 		                uint256 extnValuePtr = der.firstChildOf(extnValueParentPtr);

302: 		                    uint256 extnValueOidPtr = der.firstChildOf(extnValuePtr);

303: 		                    if (der[extnValueOidPtr.ixs()] != 0x06) {

306: 		                    if (BytesUtils.compareBytes(der.bytesAt(extnValueOidPtr), TCB_OID)) {

306: 		                    if (BytesUtils.compareBytes(der.bytesAt(extnValueOidPtr), TCB_OID)) {

310: 		                    if (BytesUtils.compareBytes(der.bytesAt(extnValueOidPtr), PCEID_OID)) {

310: 		                    if (BytesUtils.compareBytes(der.bytesAt(extnValueOidPtr), PCEID_OID)) {

312: 		                        uint256 pceidPtr = der.nextSiblingOf(extnValueOidPtr);

313: 		                        pceidBytes = der.bytesAt(pceidPtr);

316: 		                    if (BytesUtils.compareBytes(der.bytesAt(extnValueOidPtr), FMSPC_OID)) {

316: 		                    if (BytesUtils.compareBytes(der.bytesAt(extnValueOidPtr), FMSPC_OID)) {

318: 		                        uint256 fmspcPtr = der.nextSiblingOf(extnValueOidPtr);

319: 		                        fmspcBytes = der.bytesAt(fmspcPtr);

323: 		                    if (extnValuePtr.ixl() < extnValueParentPtr.ixl()) {

323: 		                    if (extnValuePtr.ixl() < extnValueParentPtr.ixl()) {

324: 		                        extnValuePtr = der.nextSiblingOf(extnValuePtr);

333: 		            if (tbsPtr.ixl() < tbsParentPtr.ixl()) {

333: 		            if (tbsPtr.ixl() < tbsParentPtr.ixl()) {

334: 		                tbsPtr = der.nextSiblingOf(tbsPtr);

350: 		        uint256 tcbPtr = der.nextSiblingOf(oidPtr);

352: 		        uint256 svnParentPtr = der.firstChildOf(tcbPtr);

355: 		            uint256 svnPtr = der.firstChildOf(svnParentPtr); // OID

356: 		            uint256 svnValuePtr = der.nextSiblingOf(svnPtr); // value

357: 		            bytes memory svnValueBytes = der.bytesAt(svnValuePtr);

361: 		            if (BytesUtils.compareBytes(der.bytesAt(svnPtr), PCESVN_OID)) {

361: 		            if (BytesUtils.compareBytes(der.bytesAt(svnPtr), PCESVN_OID)) {

371: 		            svnParentPtr = der.nextSiblingOf(svnParentPtr);
```
[[82](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L82), [85](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L85), [88](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L88), [104](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L104), [107](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L107), [111](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L111), [112](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L112), [115](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L115), [116](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L116), [117](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L117), [118](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L118), [119](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L119), [120](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L120), [121](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L121), [127](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L127), [130](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L130), [131](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L131), [132](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L132), [133](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L133), [140](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L140), [140](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L140), [141](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L141), [141](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L141), [144](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L144), [147](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L147), [148](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L148), [149](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L149), [150](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L150), [151](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L151), [152](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L152), [157](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L157), [161](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L161), [162](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L162), [166](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L166), [167](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L167), [171](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L171), [171](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L171), [171](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L171), [173](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L173), [174](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L174), [176](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L176), [177](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L177), [179](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L179), [180](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L180), [186](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L186), [189](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L189), [193](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L193), [194](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L194), [208](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L208), [209](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L209), [222](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L222), [223](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L223), [241](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L241), [245](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L245), [266](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L266), [287](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L287), [288](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L288), [292](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L292), [292](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L292), [294](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L294), [295](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L295), [296](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L296), [302](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L302), [303](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L303), [306](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L306), [306](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L306), [310](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L310), [310](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L310), [312](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L312), [313](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L313), [316](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L316), [316](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L316), [318](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L318), [319](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L319), [323](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L323), [323](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L323), [324](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L324), [333](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L333), [333](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L333), [334](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L334), [350](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L350), [352](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L352), [355](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L355), [356](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L356), [357](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L357), [361](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L361), [361](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L361), [371](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L371)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

57: 		        require(der[ptr.ixs()] == 0x03, "Not type BIT STRING");

58: 		        return _readNodeLength(der, ptr.ixf() + 1);

67: 		        require(der[ptr.ixs()] == 0x04, "Not type OCTET STRING");

68: 		        return _readNodeLength(der, ptr.ixf());

78: 		        return _readNodeLength(der, ptr.ixl() + 1);

88: 		        require(der[ptr.ixs()] & 0x20 == 0x20, "Not a constructed type");

89: 		        return _readNodeLength(der, ptr.ixf());

100: 		            ((i.ixf() <= j.ixs()) && (j.ixl() <= i.ixl()))

100: 		            ((i.ixf() <= j.ixs()) && (j.ixl() <= i.ixl()))

100: 		            ((i.ixf() <= j.ixs()) && (j.ixl() <= i.ixl()))

100: 		            ((i.ixf() <= j.ixs()) && (j.ixl() <= i.ixl()))

101: 		                || ((j.ixf() <= i.ixs()) && (i.ixl() <= j.ixl()))

101: 		                || ((j.ixf() <= i.ixs()) && (i.ixl() <= j.ixl()))

101: 		                || ((j.ixf() <= i.ixs()) && (i.ixl() <= j.ixl()))

101: 		                || ((j.ixf() <= i.ixs()) && (i.ixl() <= j.ixl()))

112: 		        return der.substring(ptr.ixf(), ptr.ixl() + 1 - ptr.ixf());

112: 		        return der.substring(ptr.ixf(), ptr.ixl() + 1 - ptr.ixf());

112: 		        return der.substring(ptr.ixf(), ptr.ixl() + 1 - ptr.ixf());

112: 		        return der.substring(ptr.ixf(), ptr.ixl() + 1 - ptr.ixf());

122: 		        return der.substring(ptr.ixs(), ptr.ixl() + 1 - ptr.ixs());

122: 		        return der.substring(ptr.ixs(), ptr.ixl() + 1 - ptr.ixs());

122: 		        return der.substring(ptr.ixs(), ptr.ixl() + 1 - ptr.ixs());

122: 		        return der.substring(ptr.ixs(), ptr.ixl() + 1 - ptr.ixs());

132: 		        return der.readBytesN(ptr.ixf(), ptr.ixl() + 1 - ptr.ixf());

132: 		        return der.readBytesN(ptr.ixf(), ptr.ixl() + 1 - ptr.ixf());

132: 		        return der.readBytesN(ptr.ixf(), ptr.ixl() + 1 - ptr.ixf());

132: 		        return der.readBytesN(ptr.ixf(), ptr.ixl() + 1 - ptr.ixf());

142: 		        require(der[ptr.ixs()] == 0x02, "Not type INTEGER");

143: 		        require(der[ptr.ixf()] & 0x80 == 0, "Not positive");

144: 		        uint256 len = ptr.ixl() + 1 - ptr.ixf();

144: 		        uint256 len = ptr.ixl() + 1 - ptr.ixf();

145: 		        return uint256(der.readBytesN(ptr.ixf(), len) >> (32 - len) * 8);

145: 		        return uint256(der.readBytesN(ptr.ixf(), len) >> (32 - len) * 8);

155: 		        require(der[ptr.ixs()] == 0x02, "Not type INTEGER");

156: 		        require(der[ptr.ixf()] & 0x80 == 0, "Not positive");

157: 		        uint256 valueLength = ptr.ixl() + 1 - ptr.ixf();

157: 		        uint256 valueLength = ptr.ixl() + 1 - ptr.ixf();

158: 		        if (der[ptr.ixf()] == 0) {

159: 		            return der.substring(ptr.ixf() + 1, valueLength - 1);

159: 		            return der.substring(ptr.ixf() + 1, valueLength - 1);

161: 		            return der.substring(ptr.ixf(), valueLength);

161: 		            return der.substring(ptr.ixf(), valueLength);

166: 		        return der.keccak(ptr.ixf(), ptr.ixl() + 1 - ptr.ixf());

166: 		        return der.keccak(ptr.ixf(), ptr.ixl() + 1 - ptr.ixf());

166: 		        return der.keccak(ptr.ixf(), ptr.ixl() + 1 - ptr.ixf());

166: 		        return der.keccak(ptr.ixf(), ptr.ixl() + 1 - ptr.ixf());

170: 		        return der.keccak(ptr.ixs(), ptr.ixl() + 1 - ptr.ixs());

170: 		        return der.keccak(ptr.ixs(), ptr.ixl() + 1 - ptr.ixs());

170: 		        return der.keccak(ptr.ixs(), ptr.ixl() + 1 - ptr.ixs());

170: 		        return der.keccak(ptr.ixs(), ptr.ixl() + 1 - ptr.ixs());

180: 		        require(der[ptr.ixs()] == 0x03, "ixs Not type BIT STRING 0x03");

182: 		        require(der[ptr.ixf()] == 0x00, "ixf Not 0");

183: 		        uint256 valueLength = ptr.ixl() + 1 - ptr.ixf();

183: 		        uint256 valueLength = ptr.ixl() + 1 - ptr.ixf();

184: 		        return der.substring(ptr.ixf() + 1, valueLength - 1);

184: 		        return der.substring(ptr.ixf() + 1, valueLength - 1);

198: 		                length = der.readUint8(ix + 2);

200: 		                length = der.readUint16(ix + 2);

203: 		                    der.readBytesN(ix + 2, lengthbytesLength) >> (32 - lengthbytesLength) * 8
```
[[57](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L57), [58](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L58), [67](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L67), [68](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L68), [78](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L78), [88](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L88), [89](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L89), [100](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L100), [100](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L100), [100](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L100), [100](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L100), [101](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L101), [101](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L101), [101](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L101), [101](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L101), [112](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L112), [112](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L112), [112](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L112), [112](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L112), [122](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L122), [122](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L122), [122](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L122), [122](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L122), [132](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L132), [132](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L132), [132](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L132), [132](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L132), [142](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L142), [143](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L143), [144](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L144), [144](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L144), [145](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L145), [145](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L145), [155](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L155), [156](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L156), [157](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L157), [157](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L157), [158](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L158), [159](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L159), [159](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L159), [161](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L161), [161](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L161), [166](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L166), [166](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L166), [166](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L166), [166](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L166), [170](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L170), [170](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L170), [170](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L170), [170](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L170), [180](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L180), [182](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L182), [183](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L183), [183](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L183), [184](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L184), [184](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L184), [198](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L198), [200](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L200), [203](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L203)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

317: 		        return pkcs1Sha1(SHA1.sha1(_data), _s, _e, _m);
```
[[317](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L317)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

89: 		        bytes memory exponent = publicKey.substring(0, 3);

90: 		        bytes memory modulus = publicKey.substring(3, publicKey.length - 3);

106: 		        bytes memory exponent = publicKey.substring(0, 3);

107: 		        bytes memory modulus = publicKey.substring(3, publicKey.length - 3);

126: 		        uint256 r = uint256(bytes32(signature.substring(0, 32)));

127: 		        uint256 s = uint256(bytes32(signature.substring(32, 32)));

132: 		        uint256 gx = uint256(bytes32(publicKey.substring(0, 32)));

133: 		        uint256 gy = uint256(bytes32(publicKey.substring(32, 32)));

137: 		        (bool success, bytes memory ret) = ES256VERIFIER.staticcall(args);
```
[[89](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L89), [90](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L90), [106](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L106), [107](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L107), [126](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L126), [127](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L127), [132](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L132), [133](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L133), [137](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L137)]



```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

96: 		        if (!_blk.assignedProver.isValidSignature(hash, assignment.signature)) {

111: 		            _blk.assignedProver.sendEther(proverFee, MAX_GAS_PAYING_PROVER);

121: 		            address(block.coinbase).sendEther(input.tip);

126: 		            taikoL1Address.sendEther(address(this).balance);

149: 		                ITaikoL1(_taikoL1Address).getConfig().chainId,
```
[[96](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L96), [111](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L111), [121](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L121), [126](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L126), [149](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L149)]



```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

41: 		        _resolver.resolve("bridge", false).sendEther(msg.value);

41: 		        _resolver.resolve("bridge", false).sendEther(msg.value);

82: 		                new TaikoData.EthDeposit[](numPending.min(_config.ethDepositMaxCountPerBlock));

83: 		            uint96 fee = uint96(_config.ethDepositMaxFee.min(block.basefee * _config.ethDepositGas));
```
[[41](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L41), [41](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L41), [82](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L82), [83](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L83)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

182: 		            if (!LibAddress.isSenderEOA()) revert L1_PROPOSER_NOT_EOA();

207: 		        meta_.minTier = ITierProvider(_resolver.resolve("tier_provider", false)).getMinTier(
208: 		            uint256(meta_.difficulty)
209: 		        );

207: 		        meta_.minTier = ITierProvider(_resolver.resolve("tier_provider", false)).getMinTier(

237: 		            IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));

238: 		            uint256 tkoBalance = tko.balanceOf(address(this));

261: 		                msg.sender.sendEther(address(this).balance);

268: 		            if (tko.balanceOf(address(this)) != tkoBalance + _config.livenessBond) {

309: 		            address proposerOne = _resolver.resolve("proposer_one", true);

315: 		        address proposer = _resolver.resolve("proposer", true);
```
[[182](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L182), [207-209](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L207-L209), [207](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L207), [237](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L237), [238](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L238), [261](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L261), [268](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L268), [309](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L309), [315](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L315)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

141: 		            ITierProvider(_resolver.resolve("tier_provider", false)).getTier(_proof.tier);

141: 		            ITierProvider(_resolver.resolve("tier_provider", false)).getTier(_proof.tier);

161: 		            address verifier = _resolver.resolve(tier.verifierName, true);

187: 		        IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));

196: 		                tko.transfer(blk.assignedProver, blk.livenessBond);

367: 		                _tko.transfer(_ts.prover, _ts.validityBond + reward);

371: 		                _tko.transfer(_ts.contester, _ts.contestBond + reward);

382: 		                _tko.transfer(msg.sender, reward - _tier.validityBond);

414: 		        bool inProvingWindow = uint256(_ts.timestamp).max(_state.slotB.lastUnpausedAt)
```
[[141](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L141), [141](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L141), [161](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L161), [187](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L187), [196](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L196), [367](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L367), [371](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L371), [382](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L382), [414](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L414)]



```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

149: 		                        tierProvider = _resolver.resolve("tier_provider", false);

152: 		                        uint256(ITierProvider(tierProvider).getTier(ts.tier).cooldownWindow) * 60

153: 		                            + uint256(ts.timestamp).max(_state.slotB.lastUnpausedAt) > block.timestamp

188: 		                IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));

189: 		                tko.transfer(ts.prover, bondToReturn);

232: 		        ISignalService signalService = ISignalService(_resolver.resolve("signal_service", false));
```
[[149](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L149), [152](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L152), [153](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L153), [188](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L188), [189](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L189), [232](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L232)]



```solidity
File: packages/protocol/contracts/L1/provers/GuardianProver.sol

51: 		            ITaikoL1(resolve("taiko", false)).proveBlock(_meta.id, abi.encode(_meta, _tran, _proof));
```
[[51](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/GuardianProver.sol#L51)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

118: 		            * (block.timestamp.min(claimEnd + withdrawalWindow) - claimEnd) / withdrawalWindow;
```
[[118](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L118)]



```solidity
File: packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

44: 		        usdc.mint(_account, _amount);

49: 		        usdc.burn(_amount);
```
[[44](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L44), [49](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L49)]



```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

33: 		        uint256 localAuthDataSize = littleEndianDecode(quote.substring(432, 4));

38: 		        bytes memory rawHeader = quote.substring(0, 48);

46: 		            parseAuthDataAndVerifyCertType(quote.substring(436, localAuthDataSize), pemCertLibAddr);

51: 		        bytes memory rawLocalEnclaveReport = quote.substring(48, 384);

129: 		        signedQuoteData = abi.encodePacked(headerBytes, V3Parser.packQEReport(localEnclaveReport));

138: 		        enclaveReport.cpuSvn = bytes16(rawEnclaveReport.substring(0, 16));

139: 		        enclaveReport.miscSelect = bytes4(rawEnclaveReport.substring(16, 4));

140: 		        enclaveReport.reserved1 = bytes28(rawEnclaveReport.substring(20, 28));

141: 		        enclaveReport.attributes = bytes16(rawEnclaveReport.substring(48, 16));

142: 		        enclaveReport.mrEnclave = bytes32(rawEnclaveReport.substring(64, 32));

143: 		        enclaveReport.reserved2 = bytes32(rawEnclaveReport.substring(96, 32));

144: 		        enclaveReport.mrSigner = bytes32(rawEnclaveReport.substring(128, 32));

145: 		        enclaveReport.reserved3 = rawEnclaveReport.substring(160, 96);

146: 		        enclaveReport.isvProdId = uint16(littleEndianDecode(rawEnclaveReport.substring(256, 2)));

147: 		        enclaveReport.isvSvn = uint16(littleEndianDecode(rawEnclaveReport.substring(258, 2)));

148: 		        enclaveReport.reserved4 = rawEnclaveReport.substring(260, 60);

149: 		        enclaveReport.reportData = rawEnclaveReport.substring(320, 64);

170: 		        bytes2 version = bytes2(rawHeader.substring(0, 2));

175: 		        bytes2 attestationKeyType = bytes2(rawHeader.substring(2, 2));

180: 		        bytes4 teeType = bytes4(rawHeader.substring(4, 4));

185: 		        bytes16 qeVendorId = bytes16(rawHeader.substring(12, 16));

194: 		            qeSvn: bytes2(rawHeader.substring(8, 2)),

195: 		            pceSvn: bytes2(rawHeader.substring(10, 2)),

197: 		            userData: bytes20(rawHeader.substring(28, 20))

212: 		        qeAuthData.parsedDataSize = uint16(littleEndianDecode(rawAuthData.substring(576, 2)));

213: 		        qeAuthData.data = rawAuthData.substring(578, qeAuthData.parsedDataSize);

217: 		        cert.certType = uint16(littleEndianDecode(rawAuthData.substring(offset, 2)));

222: 		        cert.certDataSize = uint32(littleEndianDecode(rawAuthData.substring(offset, 4)));

224: 		        bytes memory certData = rawAuthData.substring(offset, cert.certDataSize);

227: 		        authDataV3.ecdsa256BitSignature = rawAuthData.substring(0, 64);

228: 		        authDataV3.ecdsaAttestationKey = rawAuthData.substring(64, 64);

229: 		        bytes memory rawQeReport = rawAuthData.substring(128, 384);

231: 		        authDataV3.qeReportSignature = rawAuthData.substring(512, 64);

278: 		            pemCertLib.splitCertificateChain(certBytes, 3);

282: 		            quoteCerts[i] = Base64.decode(string(quoteCerts[i]));
```
[[33](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L33), [38](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L38), [46](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L46), [51](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L51), [129](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L129), [138](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L138), [139](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L139), [140](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L140), [141](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L141), [142](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L142), [143](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L143), [144](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L144), [145](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L145), [146](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L146), [147](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L147), [148](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L148), [149](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L149), [170](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L170), [175](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L175), [180](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L180), [185](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L185), [194](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L194), [195](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L195), [197](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L197), [212](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L212), [213](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L213), [217](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L217), [222](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L222), [224](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L224), [227](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L227), [228](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L228), [229](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L229), [231](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L231), [278](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L278), [282](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L282)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

78: 		                    ptr: MemoryPointer.wrap(MemoryPointer.unwrap(_in.ptr) + offset)

78: 		                    ptr: MemoryPointer.wrap(MemoryPointer.unwrap(_in.ptr) + offset)

86: 		                ptr: MemoryPointer.wrap(MemoryPointer.unwrap(_in.ptr) + offset)

86: 		                ptr: MemoryPointer.wrap(MemoryPointer.unwrap(_in.ptr) + offset)

294: 		        uint256 src = MemoryPointer.unwrap(_src) + _offset;
```
[[78](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L78), [78](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L78), [86](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L86), [86](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L86), [294](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L294)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

60: 		        valid_ = Bytes.equal(_value, get(_key, _proof, _root));

80: 		        bytes memory key = Bytes.toNibbles(_key);

94: 		                    Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),

100: 		                    Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),

106: 		                    Bytes.equal(currentNode.encoded, currentNodeID),

118: 		                    value_ = RLPReader.readBytes(currentNode.decoded[TREE_RADIX]);

143: 		                bytes memory pathRemainder = Bytes.slice(path, offset);

144: 		                bytes memory keyRemainder = Bytes.slice(key, currentKeyIndex);

171: 		                    value_ = RLPReader.readBytes(currentNode.decoded[1]);

209: 		            proof_[i] = TrieNode({ encoded: _proof[i], decoded: RLPReader.readList(_proof[i]) });

221: 		        id_ = _node.length < 32 ? RLPReader.readRawBytes(_node) : RLPReader.readBytes(_node);

221: 		        id_ = _node.length < 32 ? RLPReader.readRawBytes(_node) : RLPReader.readBytes(_node);

228: 		        nibbles_ = Bytes.toNibbles(RLPReader.readBytes(_node.decoded[0]));

228: 		        nibbles_ = Bytes.toNibbles(RLPReader.readBytes(_node.decoded[0]));
```
[[60](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L60), [80](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L80), [94](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L94), [100](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L100), [106](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L106), [118](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L118), [143](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L143), [144](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L144), [171](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L171), [209](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L209), [221](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L221), [221](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L221), [228](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L228), [228](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L228)]

</details>

---

### [G-60] Use assembly to write hashes

Considering using [assembly](https://medium.com/@kalexotsu/understanding-solidity-assembly-hashing-a-string-from-calldata-fbd2ece82263) to write hashes, as it's possible to save a considerable amount of gas.

*There are 25 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

292: 		            bytes32 issuerPubKeyHash = keccak256(issuer.pubKey);
```
[[292](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L292)]



```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

450: 		        return keccak256(abi.encode("TAIKO_MESSAGE", _message));
```
[[450](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L450)]



```solidity
File: packages/protocol/contracts/signal/SignalService.sol

186: 		        return keccak256(abi.encode(_chainId, _kind, _blockId));

203: 		        return keccak256(abi.encodePacked("SIGNAL", _chainId, _app, _signal));
```
[[186](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L186), [203](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L203)]



```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

170: 		        bytes32 hash = keccak256(abi.encodePacked("Withdraw unlocked Taiko token to: ", _to));
```
[[170](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L170)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

176: 		                    || keccak256(bytes(ctoken.symbol)) != keccak256(bytes(_ctoken.symbol))

176: 		                    || keccak256(bytes(ctoken.symbol)) != keccak256(bytes(_ctoken.symbol))

177: 		                    || keccak256(bytes(ctoken.name)) != keccak256(bytes(_ctoken.name))

177: 		                    || keccak256(bytes(ctoken.name)) != keccak256(bytes(_ctoken.name))
```
[[176](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L176), [176](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L176), [177](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L177), [177](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L177)]



```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

182: 		        return keccak256(
183: 		            abi.encode(
184: 		                "VERIFY_PROOF",
185: 		                ITaikoL1(taikoL1).getConfig().chainId,
186: 		                address(this),
187: 		                _tran,
188: 		                _newInstance,
189: 		                _prover,
190: 		                _metaHash
191: 		            )
192: 		        );
```
[[182-192](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L182-L192)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

372: 		        return keccak256(a) == keccak256(b);

372: 		        return keccak256(a) == keccak256(b);
```
[[372](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L372), [372](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L372)]



```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

146: 		        return keccak256(
147: 		            abi.encode(
148: 		                "PROVER_ASSIGNMENT",
149: 		                ITaikoL1(_taikoL1Address).getConfig().chainId,
150: 		                _taikoL1Address,
151: 		                address(this),
152: 		                _assignment.metaHash,
153: 		                _assignment.parentMetaHash,
154: 		                _blobHash,
155: 		                _assignment.feeToken,
156: 		                _assignment.expiry,
157: 		                _assignment.maxBlockId,
158: 		                _assignment.maxProposedIn,
159: 		                _assignment.tierFees
160: 		            )
161: 		        );
```
[[146-161](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L146-L161)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

126: 		                depositsHash: keccak256(abi.encode(deposits_)),

189: 		            meta_.blobHash = keccak256(_txList);

204: 		        meta_.difficulty = keccak256(abi.encodePacked(block.prevrandao, b.numBlocks, block.number));

213: 		            metaHash: keccak256(abi.encode(meta_)),
```
[[126](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L126), [189](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L189), [204](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L204), [213](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L213)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

121: 		        if (blk.blockId != _meta.id || blk.metaHash != keccak256(abi.encode(_meta))) {
```
[[121](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L121)]



```solidity
File: packages/protocol/contracts/L1/provers/GuardianProver.sol

46: 		        bytes32 hash = keccak256(abi.encode(_meta, _tran));
```
[[46](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/GuardianProver.sol#L46)]



```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

68: 		        bytes32 hash = keccak256(abi.encode("CLAIM_TAIKO_AIRDROP", data));
```
[[68](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L68)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/Bytes.sol

150: 		        return keccak256(_bytes) == keccak256(_other);

150: 		        return keccak256(_bytes) == keccak256(_other);
```
[[150](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L150), [150](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L150)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

94: 		                    Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),

100: 		                    Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
```
[[94](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L94), [100](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L100)]



```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol

55: 		        hash_ = abi.encodePacked(keccak256(_key));
```
[[55](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L55)]

</details>

---

### [G-61] Use assembly to validate `msg.sender`

It is possible to use assembly to efficiently validate `msg.sender` with the least amount of opcodes. For more details check the [following report](https://code4rena.com/reports/2023-05-juicebox#g-06-use-assembly-to-validate-msgsender).

*There are 17 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

61: 		        require(msg.sender == owner, "onlyOwner");
```
[[61](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L61)]



```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

250: 		        if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) {

260: 		            if (_message.gasLimit == 0 && msg.sender != _message.destOwner) {

294: 		            if (msg.sender == refundTo) {

322: 		            if (msg.sender != _message.destOwner) revert B_PERMISSION_DENIED();
```
[[250](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L250), [260](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L260), [294](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L294), [322](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L322)]



```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

25: 		        if (msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();
```
[[25](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressResolver.sol#L25)]



```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

42: 		        if (msg.sender != owner() && msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();
```
[[42](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L42)]



```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

123: 		        if (msg.sender != GOLDEN_TOUCH_ADDRESS) revert L2_INVALID_SENDER();
```
[[123](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L123)]



```solidity
File: packages/protocol/contracts/signal/SignalService.sol

77: 		        if (!isAuthorized[msg.sender]) revert SS_UNAUTHORIZED();
```
[[77](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L77)]



```solidity
File: packages/protocol/contracts/tokenvault/BaseVault.sol

23: 		        if (msg.sender != resolve("bridge", false)) {

65: 		        if (ctx_.from != msg.sender) revert VAULT_PERMISSION_DENIED();
```
[[23](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseVault.sol#L23), [65](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseVault.sol#L65)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

38: 		        if (msg.sender != owner() && msg.sender != snapshooter) {
```
[[38](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L38)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

61: 		        if (msg.sender == migratingAddress) {

64: 		        } else if (msg.sender != resolve("erc20_vault", true)) {

78: 		            if (msg.sender != _account) revert BB_PERMISSION_DENIED();

83: 		        } else if (msg.sender != resolve("erc20_vault", true)) {
```
[[61](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L61), [64](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L64), [78](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L78), [83](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L83)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

310: 		            if (proposerOne != address(0) && msg.sender != proposerOne) {
```
[[310](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L310)]

</details>

---

### [G-62] Use assembly to write `address` storage values

Using assembly `{ sstore(state.slot, addr)` instead of `state = addr` can save gas.

*There are 18 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

55: 		        sigVerifyLib = ISigVerifyLib(sigVerifyLibAddr);

57: 		        owner = msg.sender;
```
[[55](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L55), [57](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L57)]



```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

62: 		        addressManager = _addressManager;
```
[[62](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressResolver.sol#L62)]



```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

122: 		        taikoToken = _taikoToken;

125: 		        costToken = _costToken;

128: 		        sharedVault = _sharedVault;
```
[[122](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L122), [125](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L125), [128](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L128)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

56: 		        srcToken = _srcToken;
```
[[56](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L56)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

73: 		        srcToken = _srcToken;

81: 		        snapshooter = _snapshooter;
```
[[73](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L73), [81](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L81)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

49: 		        migratingAddress = _migratingAddress;
```
[[49](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L49)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

47: 		        srcToken = _srcToken;
```
[[47](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L47)]



```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

21: 		        ES256VERIFIER = es256Verifier;
```
[[21](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L21)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

41: 		        token = _token;

42: 		        vault = _vault;
```
[[41](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L41), [42](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L42)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

69: 		        token = _token;

70: 		        vault = _vault;
```
[[69](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L69), [70](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L70)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

39: 		        token = _token;

40: 		        vault = _vault;
```
[[39](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L39), [40](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L40)]

</details>

---

### [G-63] Use assembly to emit an `event`

To efficiently emit events, it's possible to utilize assembly by making use of scratch space and the free memory pointer. This approach has the advantage of potentially avoiding the costs associated with memory expansion.

However, it's important to note that in order to safely optimize this process, it is preferable to cache and restore the free memory pointer.

A good example of such practice can be seen in [Solady's](https://github.com/Vectorized/solady/blob/main/src/tokens/ERC1155.sol#L167) codebase.

*There are 55 instances of this issue.*

<details>
<summary>Expand findings</summary>


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

93: 		            emit MessageSuspended(msgHash, _suspend);

111: 		        emit AddressBanned(_addr, _ban);

151: 		        emit MessageSent(msgHash_, message_);

208: 		            emit MessageRecalled(msgHash);

210: 		            emit MessageReceived(msgHash, _message, true);

301: 		            emit MessageExecuted(msgHash);

303: 		            emit MessageReceived(msgHash, _message, false);

336: 		        emit MessageRetried(msgHash);

519: 		        emit MessageStatusChanged(_msgHash, _status);
```
[[93](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L93), [111](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L111), [151](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L151), [208](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L208), [210](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L210), [301](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L301), [303](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L303), [336](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L336), [519](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L519)]



```solidity
File: packages/protocol/contracts/common/AddressManager.sol

50: 		        emit AddressSet(_chainId, _name, _newAddress, oldAddress);
```
[[50](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressManager.sol#L50)]



```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

71: 		        emit Paused(msg.sender);

80: 		        emit Unpaused(msg.sender);
```
[[71](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L71), [80](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L80)]



```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

53: 		        emit TransactionExecuted(nextTxId++, bytes4(txdata));
```
[[53](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L53)]



```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

157: 		        emit Anchored(blockhash(parentId), gasExcess);
```
[[157](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L157)]



```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

39: 		        emit ConfigAndExcessChanged(_newConfig, _newGasExcess);
```
[[39](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L39)]



```solidity
File: packages/protocol/contracts/signal/SignalService.sol

59: 		        emit Authorized(_addr, _authorize);

250: 		        emit ChainDataSynced(_chainId, _blockId, _kind, _chainData, signal_);

268: 		        emit SignalSent(_app, _signal, slot_, _value);
```
[[59](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L59), [250](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L250), [268](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L268)]



```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

143: 		        emit Granted(_recipient, _grant);

157: 		        emit Voided(_recipient, amountVoided);

222: 		        emit Withdrawn(_recipient, _to, amountToWithdraw, costToWithdraw);
```
[[143](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L143), [157](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L157), [222](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L222)]



```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

51: 		        emit MigrationStatusChanged(_migratingAddress, _migratingInbound);

63: 		            emit MigratedTo(migratingAddress, _account, _amount);

80: 		            emit MigratedTo(migratingAddress, _account, _amount);
```
[[51](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L51), [63](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L63), [80](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L80)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

80: 		        emit TokenSent({
81: 		            msgHash: msgHash,
82: 		            from: message_.srcOwner,
83: 		            to: _op.to,
84: 		            destChainId: message_.destChainId,
85: 		            ctoken: ctoken.addr,
86: 		            token: _op.token,
87: 		            tokenIds: _op.tokenIds,
88: 		            amounts: _op.amounts
89: 		        });

114: 		        emit TokenReceived({
115: 		            msgHash: ctx.msgHash,
116: 		            from: from,
117: 		            to: to,
118: 		            srcChainId: ctx.srcChainId,
119: 		            ctoken: ctoken.addr,
120: 		            token: token,
121: 		            tokenIds: tokenIds,
122: 		            amounts: amounts
123: 		        });

149: 		        emit TokenReleased({
150: 		            msgHash: msgHash,
151: 		            from: message.srcOwner,
152: 		            ctoken: ctoken.addr,
153: 		            token: token,
154: 		            tokenIds: tokenIds,
155: 		            amounts: amounts
156: 		        });

314: 		        emit BridgedTokenDeployed({
315: 		            chainId: _ctoken.chainId,
316: 		            ctoken: _ctoken.addr,
317: 		            btoken: btoken_,
318: 		            ctokenSymbol: _ctoken.symbol,
319: 		            ctokenName: _ctoken.name
320: 		        });
```
[[80-89](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L80-L89), [114-123](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L114-L123), [149-156](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L149-L156), [314-320](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L314-L320)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

191: 		        emit BridgedTokenChanged({
192: 		            srcChainId: _ctoken.chainId,
193: 		            ctoken: _ctoken.addr,
194: 		            btokenOld: btokenOld_,
195: 		            btokenNew: _btokenNew,
196: 		            ctokenSymbol: _ctoken.symbol,
197: 		            ctokenName: _ctoken.name,
198: 		            ctokenDecimal: _ctoken.decimals
199: 		        });

241: 		        emit TokenSent({
242: 		            msgHash: msgHash,
243: 		            from: message_.srcOwner,
244: 		            to: _op.to,
245: 		            destChainId: _op.destChainId,
246: 		            ctoken: ctoken.addr,
247: 		            token: _op.token,
248: 		            amount: balanceChange
249: 		        });

273: 		        emit TokenReceived({
274: 		            msgHash: ctx.msgHash,
275: 		            from: from,
276: 		            to: to,
277: 		            srcChainId: ctx.srcChainId,
278: 		            ctoken: ctoken.addr,
279: 		            token: token,
280: 		            amount: amount
281: 		        });

306: 		        emit TokenReleased({
307: 		            msgHash: _msgHash,
308: 		            from: _message.srcOwner,
309: 		            ctoken: ctoken.addr,
310: 		            token: token,
311: 		            amount: amount
312: 		        });

425: 		        emit BridgedTokenDeployed({
426: 		            srcChainId: ctoken.chainId,
427: 		            ctoken: ctoken.addr,
428: 		            btoken: btoken,
429: 		            ctokenSymbol: ctoken.symbol,
430: 		            ctokenName: ctoken.name,
431: 		            ctokenDecimal: ctoken.decimals
432: 		        });
```
[[191-199](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L191-L199), [241-249](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L241-L249), [273-281](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L273-L281), [306-312](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L306-L312), [425-432](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L425-L432)]



```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

64: 		        emit TokenSent({
65: 		            msgHash: msgHash,
66: 		            from: message_.srcOwner,
67: 		            to: _op.to,
68: 		            destChainId: message_.destChainId,
69: 		            ctoken: ctoken.addr,
70: 		            token: _op.token,
71: 		            tokenIds: _op.tokenIds,
72: 		            amounts: _op.amounts
73: 		        });

97: 		        emit TokenReceived({
98: 		            msgHash: ctx.msgHash,
99: 		            from: from,
100: 		            to: to,
101: 		            srcChainId: ctx.srcChainId,
102: 		            ctoken: ctoken.addr,
103: 		            token: token,
104: 		            tokenIds: tokenIds,
105: 		            amounts: new uint256[](tokenIds.length)
106: 		        });

131: 		        emit TokenReleased({
132: 		            msgHash: _msgHash,
133: 		            from: _message.srcOwner,
134: 		            ctoken: ctoken.addr,
135: 		            token: token,
136: 		            tokenIds: tokenIds,
137: 		            amounts: new uint256[](tokenIds.length)
138: 		        });

250: 		        emit BridgedTokenDeployed({
251: 		            chainId: _ctoken.chainId,
252: 		            ctoken: _ctoken.addr,
253: 		            btoken: btoken_,
254: 		            ctokenSymbol: _ctoken.symbol,
255: 		            ctokenName: _ctoken.name
256: 		        });
```
[[64-73](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L64-L73), [97-106](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L97-L106), [131-138](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L131-L138), [250-256](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L250-L256)]



```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

109: 		            emit InstanceDeleted(idx, instances[idx].addr);

220: 		            emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);

230: 		        emit InstanceAdded(id, newInstance, oldInstance, block.timestamp);
```
[[109](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L109), [220](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220), [230](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L230)]



```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

129: 		        emit BlockAssigned(_blk.assignedProver, _meta, assignment);
```
[[129](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L129)]



```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

50: 		        emit EthDeposited(
51: 		            TaikoData.EthDeposit({
52: 		                recipient: recipient_,
53: 		                amount: uint96(msg.value),
54: 		                id: _state.slotA.numEthDeposits
55: 		            })
56: 		        );
```
[[50-56](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L50-L56)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

166: 		                    emit BlobCached(meta_.blobHash);

273: 		        emit BlockProposed({
274: 		            blockId: blk.blockId,
275: 		            assignedProver: blk.assignedProver,
276: 		            livenessBond: _config.livenessBond,
277: 		            meta: meta_,
278: 		            depositsProcessed: deposits_
279: 		        });
```
[[166](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L166), [273-279](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L273-L279)]



```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

80: 		        emit ProvingPaused(_pause);

209: 		            emit TransitionProved({
210: 		                blockId: blk.blockId,
211: 		                tran: _tran,
212: 		                prover: msg.sender,
213: 		                validityBond: tier.validityBond,
214: 		                tier: _proof.tier
215: 		            });

230: 		                emit TransitionProved({
231: 		                    blockId: blk.blockId,
232: 		                    tran: _tran,
233: 		                    prover: msg.sender,
234: 		                    validityBond: 0,
235: 		                    tier: _proof.tier
236: 		                });

254: 		                emit TransitionContested({
255: 		                    blockId: blk.blockId,
256: 		                    tran: _tran,
257: 		                    contester: msg.sender,
258: 		                    contestBond: tier.contestBond,
259: 		                    tier: _proof.tier
260: 		                });
```
[[80](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L80), [209-215](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L209-L215), [230-236](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L230-L236), [254-260](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L254-L260)]



```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

73: 		        emit BlockVerified({
74: 		            blockId: 0,
75: 		            assignedProver: address(0),
76: 		            prover: address(0),
77: 		            blockHash: _genesisBlockHash,
78: 		            stateRoot: 0,
79: 		            tier: 0,
80: 		            contestations: 0
81: 		        });

198: 		                emit BlockVerified({
199: 		                    blockId: blockId,
200: 		                    assignedProver: blk.assignedProver,
201: 		                    prover: ts.prover,
202: 		                    blockHash: blockHash,
203: 		                    stateRoot: stateRoot,
204: 		                    tier: ts.tier,
205: 		                    contestations: ts.contestations
206: 		                });
```
[[73-81](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L73-L81), [198-206](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L198-L206)]



```solidity
File: packages/protocol/contracts/L1/provers/GuardianProver.sol

54: 		        emit GuardianApproval(msg.sender, _meta.id, _tran.blockHash, approved_);
```
[[54](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/GuardianProver.sol#L54)]



```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

95: 		        emit GuardiansUpdated(version, _newGuardians);

121: 		        emit Approved(_operationId, _approval, approved_);
```
[[95](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L95), [121](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L121)]



```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

93: 		        emit Withdrawn(user, amount);
```
[[93](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L93)]



```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

74: 		        emit Claimed(hash);
```
[[74](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L74)]

</details>