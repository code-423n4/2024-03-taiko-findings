## Summary

### Gas Optimizations

| |Issue|Instances|Total Gas Saved|
|-|:-|:-:|:-:|
| [[G&#x2011;01](#g01-abiencode-is-less-efficient-than-abiencodepacked-for-non-address-arguments)] | `abi.encode()` is less efficient than `abi.encodepacked()` for non-address arguments | 10 |  - |
| [[G&#x2011;02](#g02-do-while-is-cheaper-than-for-loops-when-the-initial-check-can-be-skipped)] | `do`-`while` is cheaper than `for`-loops when the initial check can be skipped | 40 |  - |
| [[G&#x2011;03](#g03-enums-cost-more-gas-to-use-than-uint256s)] | `enum`s cost more gas to use than `uint256`s | 9 |  - |
| [[G&#x2011;04](#g04-argument-validation-should-be-at-the-top-of-the-functionblock)] | Argument validation should be at the top of the function/block | 6 |  - |
| [[G&#x2011;05](#g05-state-variable-written-in-a-loop)] | State variable written in a loop | 1 |  5794 |
| [[G&#x2011;06](#g06-mappings-are-cheaper-to-use-than-storage-arrays)] | Mappings are cheaper to use than storage arrays | 35 |  73500 |
| [[G&#x2011;07](#g07-use-arrayunsafeaccess-to-avoid-repeated-array-length-checks)] | Use `Array.unsafeAccess()` to avoid repeated array length checks | 4 |  8400 |
| [[G&#x2011;08](#g08-events-should-be-emitted-outside-of-loops)] | Events should be emitted outside of loops | 7 |  2625 |
| [[G&#x2011;09](#g09-emitting-indexed-constants-wastes-gas)] | Emitting `index`ed `constant`s wastes gas | 4 |  1500 |
| [[G&#x2011;10](#g10-superfluous-event-fields)] | Superfluous event fields | 1 |  256 |
| [[G&#x2011;11](#g11-assembly-use-scratch-space-for-building-calldata)] | Assembly: Use scratch space for building calldata | 21 |  4620 |
| [[G&#x2011;12](#g12-assembly-avoid-fetching-a-low-level-calls-return-data-by-using-assembly)] | Assembly: Avoid fetching a low-level call's return data by using assembly | 2 |  318 |
| [[G&#x2011;13](#g13-using-calldata-instead-of-memory-for-read-only-arguments-in-publicexternal-functions-saves-gas)] | Using `calldata` instead of `memory` for read-only arguments in `public`/`external` functions saves gas | 27 |  3240 |
| [[G&#x2011;14](#g14-state-variable-read-in-a-loop)] | State variable read in a loop | 8 |  776 |
| [[G&#x2011;15](#g15-multiple-accesses-of-a-mappingarray-should-use-a-local-variable-cache)] | Multiple accesses of a mapping/array should use a local variable cache | 25 |  1050 |
| [[G&#x2011;16](#g16-combine-mappings-referenced-in-the-same-function-by-the-same-key)] | Combine `mapping`s referenced in the same function by the same key | 7 |  294 |
| [[G&#x2011;17](#g17-assigning-state-variables-directly-with-struct-constructors-wastes-gas)] | Assigning state variables directly with `struct` constructors wastes gas | 4 |  168 |
| [[G&#x2011;18](#g18-constructors-can-be-marked-payable)] | Constructors can be marked `payable` | 3 |  63 |
| [[G&#x2011;19](#g19-private-functions-only-called-once-can-be-inlined-to-save-gas)] | `private` functions only called once can be inlined to save gas | 25 |  500 |
| [[G&#x2011;20](#g20-unchecked---can-be-used-on-the-division-of-two-uints-in-order-to-save-gas)] | `unchecked {}`  can be used on the division of two `uint`s in order to save gas | 11 |  220 |
| [[G&#x2011;21](#g21-internal-functions-only-called-once-can-be-inlined-to-save-gas)] | `internal` functions only called once can be inlined to save gas | 4 |  80 |
| [[G&#x2011;22](#g22-assembly-use-scratch-space-when-building-emitted-events-with-two-data-arguments)] | Assembly: Use scratch space when building emitted events with two data arguments | 6 |  90 |
| [[G&#x2011;23](#g23-nesting-if-statements-is-cheaper-than-using-)] | Nesting `if`-statements is cheaper than using `&&` | 16 |  96 |
| [[G&#x2011;24](#g24--costs-less-gas-than-)] | `>=` costs less gas than `>` | 130 |  390 |
| [[G&#x2011;25](#g25-requirerevert-strings-longer-than-32-bytes-cost-extra-gas)] | `require()`/`revert()` strings longer than 32 bytes cost extra gas | 31 |  93 |
| [[G&#x2011;26](#g26-a-memory-arrays-length-should-not-be-looked-up-in-every-iteration-of-a-forwhile-loop)] | A `memory` array's `length` should not be looked up in every iteration of a `for`/`while`-loop | 1 |  3 |
| [[G&#x2011;27](#g27-assembly-check-msgsender-using-xor-and-the-scratch-space)] | Assembly: Check `msg.sender` using `xor` and the scratch space | 22 |  - |
| [[G&#x2011;28](#g28-avoid-transferring-amounts-of-zero-in-order-to-save-gas)] | Avoid transferring amounts of zero in order to save gas | 12 |  1200 |
| [[G&#x2011;29](#g29-assembly-checks-for-address0x0-are-more-efficient-in-assembly)] | Assembly: Checks for `address(0x0)` are more efficient in assembly | 55 |  990 |
| [[G&#x2011;30](#g30-consider-merging-consecutive-loops-over-the-same-data)] | Consider merging consecutive loops over the same data | 8 |  - |
| [[G&#x2011;31](#g31-consider-using-bytes32-rather-than-a-string)] | Consider using `bytes32` rather than a `string` | 5 |  - |
| [[G&#x2011;32](#g32-consider-using-erc721a-over-erc721)] | Consider using `ERC721A` over `ERC721` | 1 |  - |
| [[G&#x2011;33](#g33-consider-using-soladys-token-contracts-to-save-gas)] | Consider using `solady`'s token contracts to save gas | 11 |  - |
| [[G&#x2011;34](#g34-consider-using-soladys-fixedpointmathlib)] | Consider using solady's `FixedPointMathLib` | 3 |  - |
| [[G&#x2011;35](#g35-counting-down-when-iterating-saves-gas)] | Counting down when iterating, saves gas | 46 |  552 |
| [[G&#x2011;36](#g36-duplicated-requirerevert-checks-should-be-refactored-to-a-modifier-or-function-to-save-deployment-gas)] | Duplicated `require()`/`revert()` checks should be refactored to a modifier or function to save deployment gas | 6 |  - |
| [[G&#x2011;37](#g37-emitting-constants-wastes-gas)] | Emitting constants wastes gas | 5 |  40 |
| [[G&#x2011;38](#g38-initializers-can-be-marked-payable)] | Initializers can be marked `payable` | 24 |  - |
| [[G&#x2011;39](#g39-inverting-the-condition-of-an-if-else-statement-wastes-gas)] | Inverting the condition of an `if`-`else`-statement wastes gas | 2 |  - |
| [[G&#x2011;40](#g40-memory-safe-annotation-missing)] | Memory-safe annotation missing | 24 |  - |
| [[G&#x2011;41](#g41-multiple-addressid-mappings-can-be-combined-into-a-single-mapping-of-an-addressid-to-a-struct)] | Multiple `address`/ID mappings can be combined into a single `mapping` of an `address`/ID to a `struct` | 4 |  - |
| [[G&#x2011;42](#g42-multiple-accesses-of-a-memorycalldata-array-should-use-a-local-variable-cache)] | Multiple accesses of a `memory`/`calldata` array should use a local variable cache | 15 |  - |
| [[G&#x2011;43](#g43-optimize-names-to-save-gas)] | Optimize names to save gas | 31 |  - |
| [[G&#x2011;44](#g44-reduce-deployment-costs-by-tweaking-contracts-metadata)] | Reduce deployment costs by tweaking contracts' metadata | 28 |  - |
| [[G&#x2011;45](#g45-state-variables-only-set-in-the-constructor-should-be-declared-immutable)] | State variables only set in the constructor should be declared `immutable` | 6 |  12582 |
| [[G&#x2011;46](#g46-functions-guaranteed-to-revert-when-called-by-normal-users-can-be-marked-payable)] | Functions guaranteed to revert when called by normal users can be marked `payable` | 23 |  483 |
| [[G&#x2011;47](#g47-use-local-variables-for-emitting-packed-storage-variables)] | Use local variables for emitting packed storage variables | 11 |  154 |
| [[G&#x2011;48](#g48-stack-variable-is-only-used-once)] | Stack variable is only used once | 126 |  378 |
| [[G&#x2011;49](#g49-splitting-require-statements-that-use--saves-gas)] | Splitting `require()` statements that use `&&` saves gas | 4 |  12 |
| [[G&#x2011;50](#g50-split-revert-checks-to-save-gas)] | Split `revert` checks to save gas | 26 |  52 |
| [[G&#x2011;51](#g51-update-openzeppelin-dependency-to-save-gas)] | Update OpenZeppelin dependency to save gas | 47 |  - |
| [[G&#x2011;52](#g52-use-bitwise-operators-rather-than-boolean-operators-to-save-gas)] | Use bitwise operators rather than boolean operators, to save gas | 8 |  - |
| [[G&#x2011;53](#g53-use-custom-errors-rather-than-revertrequire-strings-to-save-gas)] | Use custom errors rather than `revert()`/`require()` strings to save gas | 17 |  - |
| [[G&#x2011;54](#g54-use-gas-efficient-version-of-minmax)] | Use gas-efficient version of `min()`/`max()` | 2 |  - |
| [[G&#x2011;55](#g55-use-internal-functions-inside-modifiers-to-save-gas)] | Use internal functions inside modifiers to save gas | 1 |  - |
| [[G&#x2011;56](#g56-use-short-circuit-evaluation-to-avoid-reading-state-variables)] | Use short-circuit evaluation to avoid reading state variables | 5 |  - |
| [[G&#x2011;57](#g57-using-msg-globals-directly-rather-than-caching-the-value-saves-gas)] | Using `msg` globals directly, rather than caching the value, saves gas | 3 |  15 |
| [[G&#x2011;58](#g58-using-private-rather-than-public-saves-gas)] | Using `private` rather than `public`, saves gas | 52 |  - |
| [[G&#x2011;59](#g59-yul-variable-is-only-used-once)] | Yul variable is only used once | 3 |  9 |

Total: 1074 instances over 59 issues with **120543 gas** saved

Gas totals are estimates based on data from the Ethereum Yellowpaper. The estimates use the lower bounds of ranges and count two iterations of each `for`-loop. All values above are runtime, not deployment, values; deployment values are listed in the individual issue descriptions. The table above as well as its gas numbers do not include any of the excluded findings.





## Gas Optimizations


### [G&#x2011;01] `abi.encode()` is less efficient than `abi.encodepacked()` for non-address arguments


*There are 10 instances of this issue:*

<details>
<summary>see instances</summary>


```solidity
File: contracts/L1/libs/LibProposing.sol

126:                 depositsHash: keccak256(abi.encode(deposits_)),

213:             metaHash: keccak256(abi.encode(meta_)),

```
*GitHub*: [126](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L126-L126), [213](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L213-L213)

```solidity
File: contracts/L1/libs/LibProving.sol

121:         if (blk.blockId != _meta.id || blk.metaHash != keccak256(abi.encode(_meta))) {

```
*GitHub*: [121](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L121-L121)

```solidity
File: contracts/L1/provers/GuardianProver.sol

46:          bytes32 hash = keccak256(abi.encode(_meta, _tran));

51:              ITaikoL1(resolve("taiko", false)).proveBlock(_meta.id, abi.encode(_meta, _tran, _proof));

```
*GitHub*: [46](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/GuardianProver.sol#L46-L46), [51](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/GuardianProver.sol#L51-L51)

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

482:         retData = abi.encodePacked(sha256(abi.encode(v3quote)), tcbStatus);

```
*GitHub*: [482](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L482-L482)

```solidity
File: contracts/automata-attestation/utils/SigVerifyLib.sol

136:         bytes memory args = abi.encode(sha256(tbs), r, s, gx, gy);

```
*GitHub*: [136](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L136-L136)

```solidity
File: contracts/bridge/Bridge.sol

450:         return keccak256(abi.encode("TAIKO_MESSAGE", _message));

```
*GitHub*: [450](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L450-L450)

```solidity
File: contracts/signal/SignalService.sol

186:         return keccak256(abi.encode(_chainId, _kind, _blockId));

```
*GitHub*: [186](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L186-L186)

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol

68:          bytes32 hash = keccak256(abi.encode("CLAIM_TAIKO_AIRDROP", data));

```
*GitHub*: [68](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L68-L68)

</details>





### [G&#x2011;02] `do`-`while` is cheaper than `for`-loops when the initial check can be skipped
`for (uint256 i; i < len; ++i){ ... }` -> `do { ...; ++i } while (i < len);`

*There are 40 instances of this issue:*

<details>
<summary>see instances</summary>


```solidity
File: contracts/L1/hooks/AssignmentHook.sol

172:         for (uint256 i; i < _tierFees.length; ++i) {

```
*GitHub*: [172](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L172-L172)

```solidity
File: contracts/L1/libs/LibDepositing.sol

86:              for (uint256 i; i < deposits_.length;) {

```
*GitHub*: [86](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L86-L86)

```solidity
File: contracts/L1/libs/LibProposing.sol

244:             for (uint256 i; i < params.hookCalls.length; ++i) {

```
*GitHub*: [244](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L244-L244)

```solidity
File: contracts/L1/provers/Guardians.sol

74:          for (uint256 i; i < guardians.length; ++i) {

80:          for (uint256 i = 0; i < _newGuardians.length; ++i) {

133:             for (uint256 i; i < guardiansLength; ++i) {

```
*GitHub*: [74](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L74-L74), [80](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L80-L80), [133](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L133-L133)

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

80:          for (uint256 i; i < serialNumBatch.length; ++i) {

95:          for (uint256 i; i < serialNumBatch.length; ++i) {

191:         for (uint256 i; i < enclaveId.tcbLevels.length; ++i) {

214:         for (uint256 i; i < tcb.tcbLevels.length; ++i) {

240:         for (uint256 i; i < CPUSVN_LENGTH; ++i) {

259:         for (uint256 i; i < n; ++i) {

```
*GitHub*: [80](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L80-L80), [95](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L95-L95), [191](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L191-L191), [214](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L214-L214), [240](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L240-L240), [259](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L259-L259)

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol

54:          for (uint256 i; i < size; ++i) {

244:         for (uint256 i; i < split.length; ++i) {

```
*GitHub*: [54](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L54-L54), [244](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L244-L244)

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

153:         for (uint256 i; i < encoded.length; ++i) {

```
*GitHub*: [153](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L153-L153)

```solidity
File: contracts/automata-attestation/utils/BytesUtils.sol

80:          for (uint256 idx = 0; idx < shortest; idx += 32) {

333:         for (uint256 i; i < len; ++i) {

```
*GitHub*: [80](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L80-L80), [333](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L333-L333)

```solidity
File: contracts/automata-attestation/utils/RsaVerify.sol

152:             for (uint256 i; i < digestAlgoWithParamLen; ++i) {

158:             for (uint256 i; i < digestAlgoWithParamLen; ++i) {

174:         for (uint256 i; i < _sha256.length; ++i) {

283:         for (uint256 i; i < sha1Prefix.length; ++i) {

290:         for (uint256 i; i < _sha1.length; ++i) {

```
*GitHub*: [152](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L152-L152), [158](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L158-L158), [174](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L174-L174), [283](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L283-L283), [290](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L290-L290)

```solidity
File: contracts/automata-attestation/utils/X509DateUtils.sol

48:          for (uint16 i = 1970; i < year; ++i) {

59:          for (uint8 i = 1; i < month; ++i) {

```
*GitHub*: [48](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L48-L48), [59](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L59-L59)

```solidity
File: contracts/bridge/Bridge.sol

90:          for (uint256 i; i < _msgHashes.length; ++i) {

```
*GitHub*: [90](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L90-L90)

```solidity
File: contracts/signal/SignalService.sol

104:         for (uint256 i; i < hopProofs.length; ++i) {

```
*GitHub*: [104](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L104-L104)

```solidity
File: contracts/team/airdrop/ERC721Airdrop.sol

59:          for (uint256 i; i < tokenIds.length; ++i) {

```
*GitHub*: [59](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59-L59)

```solidity
File: contracts/thirdparty/optimism/rlp/RLPWriter.sol

66:          for (uint256 j = 0; j < out_.length; j++) {

```
*GitHub*: [66](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66-L66)

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

85:          for (uint256 i = 0; i < proof.length; i++) {

208:         for (uint256 i = 0; i < length;) {

```
*GitHub*: [85](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85-L85), [208](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L208-L208)

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

47:          for (uint256 i; i < _op.amounts.length; ++i) {

251:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

269:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

```
*GitHub*: [47](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L47-L47), [251](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L251-L251), [269](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L269-L269)

```solidity
File: contracts/tokenvault/ERC721Vault.sol

34:          for (uint256 i; i < _op.tokenIds.length; ++i) {

170:             for (uint256 i; i < _tokenIds.length; ++i) {

175:             for (uint256 i; i < _tokenIds.length; ++i) {

197:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

210:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

```
*GitHub*: [34](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L34-L34), [170](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L170-L170), [175](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L175-L175), [197](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L197-L197), [210](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L210-L210)

```solidity
File: contracts/verifiers/SgxVerifier.sol

104:         for (uint256 i; i < _ids.length; ++i) {

210:         for (uint256 i; i < _instances.length; ++i) {

```
*GitHub*: [104](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L104-L104), [210](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210-L210)

</details>





### [G&#x2011;03] `enum`s cost more gas to use than `uint256`s
Enums are equivalent in size to `uint8`s, which the overhead of having to clear the upper bits.

*There are 9 instances of this issue:*

<details>
<summary>see instances</summary>


```solidity
File: contracts/automata-attestation/interfaces/ISigVerifyLib.sol

7        enum KeyType {
8            RSA,
9            ECDSA
10:      }

19       enum CertSigAlgorithm {
20           Sha256WithRSAEncryption,
21           Sha1WithRSAEncryption
22:      }

32       enum Algorithm {
33           RS256,
34           ES256,
35           RS1
36:      }

```
*GitHub*: [7](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L7-L10), [19](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L19-L22), [32](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L32-L36)

```solidity
File: contracts/automata-attestation/lib/EnclaveIdStruct.sol

26       enum EnclaveIdStatus {
27           OK,
28           SGX_ENCLAVE_REPORT_ISVSVN_REVOKED
29:      }

```
*GitHub*: [26](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/EnclaveIdStruct.sol#L26-L29)

```solidity
File: contracts/automata-attestation/lib/TCBInfoStruct.sol

19       enum TCBStatus {
20           OK,
21           TCB_SW_HARDENING_NEEDED,
22           TCB_CONFIGURATION_AND_SW_HARDENING_NEEDED,
23           TCB_CONFIGURATION_NEEDED,
24           TCB_OUT_OF_DATE,
25           TCB_OUT_OF_DATE_CONFIGURATION_NEEDED,
26           TCB_REVOKED,
27           TCB_UNRECOGNIZED
28:      }

```
*GitHub*: [19](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol#L19-L28)

```solidity
File: contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol

31       enum CRL {
32           PCK,
33           ROOT
34:      }

```
*GitHub*: [31](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L31-L34)

```solidity
File: contracts/bridge/IBridge.sol

9        enum Status {
10           NEW,
11           RETRIABLE,
12           DONE,
13           FAILED,
14           RECALLED
15:      }

```
*GitHub*: [9](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/IBridge.sol#L9-L15)

```solidity
File: contracts/signal/ISignalService.sol

13       enum CacheOption {
14           CACHE_NOTHING,
15           CACHE_SIGNAL_ROOT,
16           CACHE_STATE_ROOT,
17           CACHE_BOTH
18:      }

```
*GitHub*: [13](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/ISignalService.sol#L13-L18)

```solidity
File: contracts/thirdparty/optimism/rlp/RLPReader.sol

16       enum RLPItemType {
17           DATA_ITEM,
18           LIST_ITEM
19:      }

```
*GitHub*: [16](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L16-L19)

</details>





### [G&#x2011;04] Argument validation should be at the top of the function/block
Checks that involve constants should come before checks that involve state variables, function calls, and calculations. By doing these checks first, the function is able to revert before wasting a Gcoldsload (**2100 gas**) in a function that may ultimately revert in the unhappy case.

*There are 6 instances of this issue:*

```solidity
File: contracts/L2/CrossChainOwned.sol

70           if (_ownerChainId == 0 || _ownerChainId == block.chainid) {
71               revert XCO_INVALID_OWNER_CHAINID();
72:          }

```
*GitHub*: [70](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L70-L72)

```solidity
File: contracts/bridge/Bridge.sol

133          if (_message.destChainId == block.chainid) {
134              revert B_INVALID_CHAINID();
135:         }

```
*GitHub*: [133](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L133-L135)

```solidity
File: contracts/common/EssentialContract.sol

105:         if (_addressManager == address(0)) revert ZERO_ADDR_MANAGER();

```
*GitHub*: [105](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L105-L105)

```solidity
File: contracts/team/TimelockTokenPool.sol

121:         if (_taikoToken == address(0)) revert INVALID_PARAM();

124:         if (_costToken == address(0)) revert INVALID_PARAM();

127:         if (_sharedVault == address(0)) revert INVALID_PARAM();

```
*GitHub*: [121](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L121-L121), [124](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L124-L124), [127](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L127-L127)



### [G&#x2011;05] State variable written in a loop
The code should be refactored such that updates made to the state variable are instead accumulated/tracked in a local variable, then be written a single time outside the loop, converting a Gsreset (**2900 gas**) to a stack write for each iteration

*There is one instance of this issue:*

```solidity
File: contracts/L1/libs/LibVerifying.sol

/// @audit blk
127              while (blockId < b.numBlocks && numBlocksVerified < _maxBlocksToVerify) {
128                  slot = blockId % _config.blockRingBufferSize;
129  
130                  blk = _state.blocks[slot];
131                  if (blk.blockId != blockId) revert L1_BLOCK_MISMATCH();
132  
133                  tid = LibUtils.getTransitionId(_state, blk, slot, blockHash);
134                  // When `tid` is 0, it indicates that there is no proven
135                  // transition with its parentHash equal to the blockHash of the
136                  // most recently verified block.
137                  if (tid == 0) break;
138  
139                  // A transition with the correct `parentHash` has been located.
140                  TaikoData.TransitionState storage ts = _state.transitions[slot][tid];
141  
142                  // It's not possible to verify this block if either the
143                  // transition is contested and awaiting higher-tier proof or if
144                  // the transition is still within its cooldown period.
145                  if (ts.contester != address(0)) {
146                      break;
147                  } else {
148                      if (tierProvider == address(0)) {
149                          tierProvider = _resolver.resolve("tier_provider", false);
150                      }
151                      if (
152                          uint256(ITierProvider(tierProvider).getTier(ts.tier).cooldownWindow) * 60
153                              + uint256(ts.timestamp).max(_state.slotB.lastUnpausedAt) > block.timestamp
154                      ) {
155                          // If cooldownWindow is 0, the block can theoretically
156                          // be proved and verified within the same L1 block.
157                          break;
158                      }
159                  }
160  
161                  // Mark this block as verified
162                  blk.verifiedTransitionId = tid;
163  
164                  // Update variables
165                  blockHash = ts.blockHash;
166                  stateRoot = ts.stateRoot;
167  
168                  // We consistently return the liveness bond and the validity
169                  // bond to the actual prover of the transition utilized for
170                  // block verification. If the actual prover happens to be the
171                  // block's assigned prover, he will receive both deposits,
172                  // ultimately earning the proving fee paid during block
173                  // proposal. In contrast, if the actual prover is different from
174                  // the block's assigned prover, the liveness bond serves as a
175                  // reward to the actual prover, while the assigned prover
176                  // forfeits his liveness bond due to failure to fulfill their
177                  // commitment.
178                  uint256 bondToReturn = uint256(ts.validityBond) + blk.livenessBond;
179  
180                  // Nevertheless, it's possible for the actual prover to be the
181                  // same individual or entity as the block's assigned prover.
182                  // Consequently, we have chosen to grant the actual prover only
183                  // half of the liveness bond as a reward.
184                  if (ts.prover != blk.assignedProver) {
185                      bondToReturn -= blk.livenessBond >> 1;
186                  }
187  
188                  IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));
189                  tko.transfer(ts.prover, bondToReturn);
190  
191                  // Note: We exclusively address the bonds linked to the
192                  // transition used for verification. While there may exist
193                  // other transitions for this block, we disregard them entirely.
194                  // The bonds for these other transitions are burned either when
195                  // the transitions are generated or proven. In such cases, both
196                  // the provers and contesters of those transitions forfeit their bonds.
197  
198                  emit BlockVerified({
199                      blockId: blockId,
200                      assignedProver: blk.assignedProver,
201                      prover: ts.prover,
202                      blockHash: blockHash,
203                      stateRoot: stateRoot,
204                      tier: ts.tier,
205                      contestations: ts.contestations
206                  });
207  
208                  ++blockId;
209                  ++numBlocksVerified;
210:             }

```
*GitHub*: [127](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L130-L130)



### [G&#x2011;06] Mappings are cheaper to use than storage arrays
When using storage arrays, solidity adds an internal lookup of the array's length (a Gcoldsload **2100 gas**) to ensure you don't read past the array's end. You can avoid this lookup by using a `mapping` and storing the number of entries in a separate storage variable. In cases where you have sentinel values (e.g. 'zero' means invalid), you can avoid length checks

*There are 35 instances of this issue:*

<details>
<summary>see instances</summary>


```solidity
File: contracts/L1/TaikoL1.sol

26:      uint256[50] private __gap;

```
*GitHub*: [26](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L26-L26)

```solidity
File: contracts/L1/TaikoToken.sol

16:      uint256[50] private __gap;

```
*GitHub*: [16](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoToken.sol#L16-L16)

```solidity
File: contracts/L1/gov/TaikoGovernor.sol

23:      uint256[50] private __gap;

```
*GitHub*: [23](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L23-L23)

```solidity
File: contracts/L1/gov/TaikoTimelockController.sol

10:      uint256[50] private __gap;

```
*GitHub*: [10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L10-L10)

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

40:      uint256[50] private __gap;

```
*GitHub*: [40](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L40-L40)

```solidity
File: contracts/L1/provers/GuardianProver.sol

11:      uint256[50] private __gap;

```
*GitHub*: [11](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/GuardianProver.sol#L11-L11)

```solidity
File: contracts/L1/provers/Guardians.sol

23:      address[] public guardians;

32:      uint256[46] private __gap;

```
*GitHub*: [23](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L23-L23), [32](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L32-L32)

```solidity
File: contracts/L1/tiers/DevnetTierProvider.sol

11:      uint256[50] private __gap;

```
*GitHub*: [11](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L11-L11)

```solidity
File: contracts/L1/tiers/MainnetTierProvider.sol

11:      uint256[50] private __gap;

```
*GitHub*: [11](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L11-L11)

```solidity
File: contracts/L2/CrossChainOwned.sol

21:      uint256[49] private __gap;

```
*GitHub*: [21](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L21-L21)

```solidity
File: contracts/L2/TaikoL2.sol

52:      uint256[47] private __gap;

```
*GitHub*: [52](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L52-L52)

```solidity
File: contracts/L2/TaikoL2EIP1559Configurable.sol

13:      uint256[49] private __gap;

```
*GitHub*: [13](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L13-L13)

```solidity
File: contracts/bridge/Bridge.sol

48:      uint256[43] private __gap;

```
*GitHub*: [48](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L48-L48)

```solidity
File: contracts/common/AddressManager.sol

14:      uint256[49] private __gap;

```
*GitHub*: [14](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressManager.sol#L14-L14)

```solidity
File: contracts/common/AddressResolver.sol

14:      uint256[49] private __gap;

```
*GitHub*: [14](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressResolver.sol#L14-L14)

```solidity
File: contracts/common/EssentialContract.sol

25:      uint256[49] private __gap;

```
*GitHub*: [25](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L25-L25)

```solidity
File: contracts/signal/SignalService.sol

23:      uint256[48] private __gap;

```
*GitHub*: [23](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L23-L23)

```solidity
File: contracts/team/TimelockTokenPool.sol

82:      uint128[44] private __gap;

```
*GitHub*: [82](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L82-L82)

```solidity
File: contracts/team/airdrop/ERC20Airdrop.sol

18:      uint256[48] private __gap;

```
*GitHub*: [18](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L18-L18)

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol

30:      uint256[45] private __gap;

```
*GitHub*: [30](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L30-L30)

```solidity
File: contracts/team/airdrop/ERC721Airdrop.sol

16:      uint256[48] private __gap;

```
*GitHub*: [16](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L16-L16)

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol

23:      uint256[47] private __gap;

```
*GitHub*: [23](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L23-L23)

```solidity
File: contracts/tokenvault/BaseNFTVault.sol

61:      uint256[48] private __gap;

```
*GitHub*: [61](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L61-L61)

```solidity
File: contracts/tokenvault/BaseVault.sol

18:      uint256[50] private __gap;

```
*GitHub*: [18](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseVault.sol#L18-L18)

```solidity
File: contracts/tokenvault/BridgedERC1155.sol

27:      uint256[46] private __gap;

```
*GitHub*: [27](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L27-L27)

```solidity
File: contracts/tokenvault/BridgedERC20.sol

32:      uint256[47] private __gap;

```
*GitHub*: [32](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L32-L32)

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol

16:      uint256[49] private __gap;

```
*GitHub*: [16](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L16-L16)

```solidity
File: contracts/tokenvault/BridgedERC721.sol

19:      uint256[48] private __gap;

```
*GitHub*: [19](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L19-L19)

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

32:      uint256[50] private __gap;

```
*GitHub*: [32](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L32-L32)

```solidity
File: contracts/tokenvault/ERC20Vault.sol

54:      uint256[47] private __gap;

```
*GitHub*: [54](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L54-L54)

```solidity
File: contracts/tokenvault/ERC721Vault.sol

19:      uint256[50] private __gap;

```
*GitHub*: [19](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L19-L19)

```solidity
File: contracts/tokenvault/adapters/USDCAdapter.sol

32:      uint256[49] private __gap;

```
*GitHub*: [32](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L32-L32)

```solidity
File: contracts/verifiers/GuardianVerifier.sol

11:      uint256[50] private __gap;

```
*GitHub*: [11](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L11-L11)

```solidity
File: contracts/verifiers/SgxVerifier.sol

57:      uint256[47] private __gap;

```
*GitHub*: [57](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L57-L57)

</details>





### [G&#x2011;07] Use `Array.unsafeAccess()` to avoid repeated array length checks
When using storage arrays, solidity adds an internal lookup of the array's length (a Gcoldsload **2100 gas**) to ensure you don't read past the array's end. You can avoid this lookup by using [`Array.unsafeAccess()`](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/94697be8a3f0dfcd95dfb13ffbd39b5973f5c65d/contracts/utils/Arrays.sol#L57) in cases where the length has already been checked, as is the case with the instances below

*There are 4 instances of this issue:*

```solidity
File: contracts/L1/provers/Guardians.sol

74:          for (uint256 i; i < guardians.length; ++i) {

75:              delete guardianIds[guardians[i]];

87:              guardians.push(guardian);

88:              guardianIds[guardian] = guardians.length;

```
*GitHub*: [74](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L74-L74), [75](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L75-L75), [87](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L87-L87), [88](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L88-L88)



### [G&#x2011;08] Events should be emitted outside of loops
Emitting an event has an overhead of **375 gas**, which will be incurred on every iteration of the loop. It is cheaper to `emit` only [once](https://github.com/ethereum/EIPs/blob/adad5968fd6de29902174e0cb51c8fc3dceb9ab5/EIPS/eip-1155.md?plain=1#L68) after the loop has finished.

*There are 7 instances of this issue:*

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

/// @audit  onBlockProposed(), proposeBlock()
129:         emit BlockAssigned(_blk.assignedProver, _meta, assignment);

```
*GitHub*: [129](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L129-L129)

```solidity
File: contracts/L1/libs/LibVerifying.sol

/// @audit  verifyBlocks()
198                  emit BlockVerified({
199                      blockId: blockId,
200                      assignedProver: blk.assignedProver,
201                      prover: ts.prover,
202                      blockHash: blockHash,
203                      stateRoot: stateRoot,
204                      tier: ts.tier,
205                      contestations: ts.contestations
206:                 });

```
*GitHub*: [198](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L198-L206)

```solidity
File: contracts/bridge/Bridge.sol

/// @audit  suspendMessages()
93:              emit MessageSuspended(msgHash, _suspend);

```
*GitHub*: [93](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L93-L93)

```solidity
File: contracts/signal/SignalService.sol

/// @audit  _syncChainData(), _cacheChainData(), proveSignalReceived()
250:         emit ChainDataSynced(_chainId, _blockId, _kind, _chainData, signal_);

/// @audit  _sendSignal(), _syncChainData(), _cacheChainData(), proveSignalReceived()
268:         emit SignalSent(_app, _signal, slot_, _value);

```
*GitHub*: [250](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L250-L250), [268](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L268-L268)

```solidity
File: contracts/verifiers/SgxVerifier.sol

/// @audit  deleteInstances()
109:             emit InstanceDeleted(idx, instances[idx].addr);

/// @audit  _addInstances()
220:             emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);

```
*GitHub*: [109](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L109-L109), [220](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220-L220)



### [G&#x2011;09] Emitting `index`ed `constant`s wastes gas
Every `indexed` event parameter adds an extra `Glogtopic` (**375 gas**). You can avoid this extra cost, in cases where you're emitting a constant, by creating a second version of the event, which doesn't have the indexed parameter (and have users look to the contract's variables for its value instead), and using the new event in the cases shown below.

*There are 4 instances of this issue:*

```solidity
File: contracts/L1/libs/LibVerifying.sol

/// @audit arg0 is `indexed blockId`
74:              blockId: 0,

/// @audit arg0 is `indexed blockId`
75:              assignedProver: address(0),

/// @audit arg0 is `indexed blockId`
76:              prover: address(0),

```
*GitHub*: [74](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L74-L74), [75](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L75-L75), [76](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L76-L76)

```solidity
File: contracts/verifiers/SgxVerifier.sol

/// @audit arg0 is `indexed id`
220:             emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);

```
*GitHub*: [220](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220-L220)



### [G&#x2011;10] Superfluous event fields
`block.timestamp` and `block.number` are added to event information by default so adding them manually wastes Glogdata (**8 gas**) times the number of bytes

*There is one instance of this issue:*

```solidity
File: contracts/verifiers/SgxVerifier.sol

230:         emit InstanceAdded(id, newInstance, oldInstance, block.timestamp);

```
*GitHub*: [230](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L230-L230)



### [G&#x2011;11] Assembly: Use scratch space for building calldata
If an external call's calldata can fit into two or fewer words, use the scratch space to build the calldata, rather than allowing Solidity to do a memory expansion.

*There are 21 instances of this issue:*

<details>
<summary>see instances</summary>


```solidity
File: contracts/L1/libs/LibProposing.sol

238:             uint256 tkoBalance = tko.balanceOf(address(this));

268:             if (tko.balanceOf(address(this)) != tkoBalance + _config.livenessBond) {

```
*GitHub*: [238](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L238-L238), [268](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L268-L268)

```solidity
File: contracts/L1/libs/LibProving.sol

196:                 tko.transfer(blk.assignedProver, blk.livenessBond);

367:                 _tko.transfer(_ts.prover, _ts.validityBond + reward);

371:                 _tko.transfer(_ts.contester, _ts.contestBond + reward);

382:                 _tko.transfer(msg.sender, reward - _tier.validityBond);

```
*GitHub*: [196](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L196-L196), [367](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L367-L367), [371](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L371-L371), [382](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L382-L382)

```solidity
File: contracts/L1/libs/LibVerifying.sol

152:                         uint256(ITierProvider(tierProvider).getTier(ts.tier).cooldownWindow) * 60

189:                 tko.transfer(ts.prover, bondToReturn);

```
*GitHub*: [152](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L152-L152), [189](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L189-L189)

```solidity
File: contracts/L2/TaikoL2.sol

176:             IERC20(_token).safeTransfer(_to, IERC20(_token).balanceOf(address(this)));

```
*GitHub*: [176](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L176-L176)

```solidity
File: contracts/bridge/Bridge.sol

174:             if (!ISignalService(signalService).isSignalSent(address(this), msgHash)) {

```
*GitHub*: [174](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L174-L174)

```solidity
File: contracts/common/AddressResolver.sol

83:          addr_ = payable(IAddressManager(addressManager).getAddress(_chainId, _name));

```
*GitHub*: [83](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressResolver.sol#L83-L83)

```solidity
File: contracts/libs/LibAddress.sol

56           try IERC165(_addr).supportsInterface(_interfaceId) returns (bool _result) {
57               result_ = _result;
58:          } catch { }

```
*GitHub*: [56](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibAddress.sol#L56-L58)

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol

82:              IBridgedERC20(migratingAddress).mint(_account, _amount);

```
*GitHub*: [82](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L82-L82)

```solidity
File: contracts/tokenvault/ERC20Vault.sol

333:             IBridgedERC20(token_).mint(_to, _amount);

360:             IBridgedERC20(_token).burn(msg.sender, _amount);

378:             uint256 _balance = t.balanceOf(address(this));

380:             balanceChange_ = t.balanceOf(address(this)) - _balance;

```
*GitHub*: [333](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L333-L333), [360](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L360-L360), [378](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L378-L378), [380](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L380-L380)

```solidity
File: contracts/tokenvault/ERC721Vault.sol

176:                 BridgedERC721(token_).mint(_to, _tokenIds[i]);

198:                     BridgedERC721(_op.token).burn(_user, _op.tokenIds[i]);

```
*GitHub*: [176](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L176-L176), [198](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L198-L198)

```solidity
File: contracts/tokenvault/adapters/USDCAdapter.sol

44:          usdc.mint(_account, _amount);

49:          usdc.burn(_amount);

```
*GitHub*: [44](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L44-L44), [49](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L49-L49)

</details>





### [G&#x2011;12] Assembly: Avoid fetching a low-level call's return data by using assembly
Even if you don't assign the call's second return value, it still gets copied to memory. Use assembly instead to prevent this and save **159 [gas](https://gist.github.com/IllIllI000/0e18a40f3afb0b83f9a347b10ee89ad2)**:

`(bool success,) = payable(receiver).call{gas: gas, value: value}("");` -> `bool success; assembly { success := call(gas, receiver, value, 0, 0, 0, 0) }`

*There are 2 instances of this issue:*

```solidity
File: contracts/L2/CrossChainOwned.sol

50:          (bool success,) = address(this).call(txdata);

```
*GitHub*: [50](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L50-L50)

```solidity
File: contracts/bridge/Bridge.sol

591:         (success_,) = _signalService.staticcall(data);

```
*GitHub*: [591](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L591-L591)



### [G&#x2011;13] Using `calldata` instead of `memory` for read-only arguments in `public`/`external` functions saves gas
When a function with a `memory` array is called externally, the `abi.decode()` step has to copy read each index of the `calldata` to `memory`. **Each copy costs at least 60 gas** (i.e. `60 * <mem_array>.length`). Using `calldata` directly, obviates the need for copies of words of the struct/array not being read. Note that even if an interface defines a function as having `memory` arguments, it's still valid for implementation contracts to use `calldata` arguments instead. 

If the array is passed to an `internal` function which passes the array to another internal function where the array is modified and therefore `memory` is used in the `external` call, it's still more gass-efficient to use `calldata` when the `external` function uses modifiers, since the modifiers may prevent the internal functions from being called. Structs have the same overhead as an array of length one

Note that I've also flagged instances where the function is `public` but can be marked as `external` since it's not called by the contract (you may have to change the visibility of the `interface`'s version of the function to `external` [first](https://docs.soliditylang.org/en/v0.8.20/contracts.html#function-overriding)), and cases where a constructor is involved

*There are 27 instances of this issue:*

<details>
<summary>see instances</summary>


```solidity
File: contracts/L1/hooks/AssignmentHook.sol

/// @audit _blk
/// @audit _meta
/// @audit _data
62       function onBlockProposed(
63           TaikoData.Block memory _blk,
64           TaikoData.BlockMetadata memory _meta,
65           bytes memory _data
66       )
67           external
68           payable
69           nonReentrant
70           onlyFromNamed("taiko")
71:      {

```
*GitHub*: [62](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L63-L63), [62](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L64-L64), [62](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L65-L65)

```solidity
File: contracts/L2/TaikoL2EIP1559Configurable.sol

/// @audit _newConfig
25       function setConfigAndExcess(
26           Config memory _newConfig,
27           uint64 _newGasExcess
28       )
29           external
30           virtual
31           onlyOwner
32:      {

```
*GitHub*: [25](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L26-L26)

```solidity
File: contracts/automata-attestation/utils/SigVerifyLib.sol

/// @audit tbs
/// @audit signature
/// @audit publicKey
24       function verifyAttStmtSignature(
25           bytes memory tbs,
26           bytes memory signature,
27           PublicKey memory publicKey,
28           Algorithm alg
29       )
30           public
31           view
32           returns (bool)
33:      {

/// @audit tbs
/// @audit signature
/// @audit publicKey
54       function verifyCertificateSignature(
55           bytes memory tbs,
56           bytes memory signature,
57           PublicKey memory publicKey,
58           CertSigAlgorithm alg
59       )
60           public
61           view
62           returns (bool)
63:      {

/// @audit tbs
/// @audit signature
/// @audit publicKey
79       function verifyRS256Signature(
80           bytes memory tbs,
81           bytes memory signature,
82           bytes memory publicKey
83       )
84           public
85           view
86           returns (bool sigValid)
87:      {

/// @audit tbs
/// @audit signature
/// @audit publicKey
96       function verifyRS1Signature(
97           bytes memory tbs,
98           bytes memory signature,
99           bytes memory publicKey
100      )
101          public
102          view
103          returns (bool sigValid)
104:     {

```
*GitHub*: [24](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L25-L25), [24](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L26-L26), [24](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L27-L27), [54](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L55-L55), [54](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L56-L56), [54](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L57-L57), [79](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L80-L80), [79](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L81-L81), [79](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L82-L82), [96](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L97-L97), [96](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L98-L98), [96](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L99-L99)

```solidity
File: contracts/bridge/Bridge.sol

/// @audit _message
449:     function hashMessage(Message memory _message) public pure returns (bytes32) {

```
*GitHub*: [449](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L449-L449)

```solidity
File: contracts/team/TimelockTokenPool.sol

/// @audit _grant
135:     function grant(address _recipient, Grant memory _grant) external onlyOwner {

/// @audit _sig
168:     function withdraw(address _to, bytes memory _sig) external {

```
*GitHub*: [135](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L135-L135), [168](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L168-L168)

```solidity
File: contracts/tokenvault/BridgedERC1155.sol

/// @audit _symbol
/// @audit _name
38       function init(
39           address _owner,
40           address _addressManager,
41           address _srcToken,
42           uint256 _srcChainId,
43           string memory _symbol,
44           string memory _name
45       )
46           external
47           initializer
48:      {

```
*GitHub*: [38](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L43-L43), [38](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L44-L44)

```solidity
File: contracts/tokenvault/BridgedERC20.sol

/// @audit _symbol
/// @audit _name
52       function init(
53           address _owner,
54           address _addressManager,
55           address _srcToken,
56           uint256 _srcChainId,
57           uint8 _decimals,
58           string memory _symbol,
59           string memory _name
60       )
61           external
62           initializer
63:      {

```
*GitHub*: [52](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L58-L58), [52](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L59-L59)

```solidity
File: contracts/tokenvault/BridgedERC721.sol

/// @audit _symbol
/// @audit _name
31       function init(
32           address _owner,
33           address _addressManager,
34           address _srcToken,
35           uint256 _srcChainId,
36           string memory _symbol,
37           string memory _name
38       )
39           external
40           initializer
41:      {

```
*GitHub*: [31](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L36-L36), [31](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L37-L37)

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

/// @audit _op
39       function sendToken(BridgeTransferOp memory _op)
40           external
41           payable
42           nonReentrant
43           whenNotPaused
44           withValidOperation(_op)
45           returns (IBridge.Message memory message_)
46:      {

```
*GitHub*: [39](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L39-L39)

```solidity
File: contracts/tokenvault/ERC721Vault.sol

/// @audit _op
26       function sendToken(BridgeTransferOp memory _op)
27           external
28           payable
29           nonReentrant
30           whenNotPaused
31           withValidOperation(_op)
32           returns (IBridge.Message memory message_)
33:      {

```
*GitHub*: [26](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L26-L26)

</details>





### [G&#x2011;14] State variable read in a loop
The state variable should be cached in and read from a local variable, or accumulated in a local variable then written to storage once outside of the loop, rather than reading/updating it on every iteration of the loop, which will replace each Gwarmaccess (**100 gas**) with a much cheaper stack read.

*There are 8 instances of this issue:*

```solidity
File: contracts/L1/provers/Guardians.sol

/// @audit guardians
/// @audit guardians
80           for (uint256 i = 0; i < _newGuardians.length; ++i) {
81               address guardian = _newGuardians[i];
82               if (guardian == address(0)) revert INVALID_GUARDIAN();
83               // This makes sure there are not duplicate addresses
84               if (guardianIds[guardian] != 0) revert INVALID_GUARDIAN_SET();
85   
86               // Save and index the guardian
87               guardians.push(guardian);
88               guardianIds[guardian] = guardians.length;
89:          }

/// @audit minGuardians
133              for (uint256 i; i < guardiansLength; ++i) {
134                  if (bits & 1 == 1) ++count;
135                  if (count == minGuardians) return true;
136                  bits >>= 1;
137:             }

```
*GitHub*: [80](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L87-L87), [80](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L88-L88), [133](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L135-L135)

```solidity
File: contracts/team/airdrop/ERC721Airdrop.sol

/// @audit token
/// @audit vault
59           for (uint256 i; i < tokenIds.length; ++i) {
60               IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);
61:          }

```
*GitHub*: [59](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L60-L60), [59](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L60-L60)

```solidity
File: contracts/verifiers/SgxVerifier.sol

/// @audit nextInstanceId
/// @audit nextInstanceId
/// @audit nextInstanceId
210          for (uint256 i; i < _instances.length; ++i) {
211              if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();
212  
213              addressRegistered[_instances[i]] = true;
214  
215              if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();
216  
217              instances[nextInstanceId] = Instance(_instances[i], validSince);
218              ids[i] = nextInstanceId;
219  
220              emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);
221  
222              nextInstanceId++;
223:         }

```
*GitHub*: [210](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L218-L218), [210](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220-L220), [210](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L222-L222)



### [G&#x2011;15] Multiple accesses of a mapping/array should use a local variable cache
The instances below point to the second+ access of a value inside a mapping/array, within a function. Caching a mapping's value in a local `storage` or `calldata` variable when the value is accessed [multiple times](https://gist.github.com/IllIllI000/ec23a57daa30a8f8ca8b9681c8ccefb0), saves **~42 gas per access** due to not having to recalculate the key's keccak256 hash (`Gkeccak256` - **30 gas**) and that calculation's associated stack operations. Caching an array's struct avoids recalculating the array offsets into memory/calldata

*There are 25 instances of this issue:*

<details>
<summary>see instances</summary>


```solidity
File: contracts/L1/libs/LibVerifying.sol

/// @audit blocks...[]
130:                 blk = _state.blocks[slot];

/// @audit transitions...[]
140:                 TaikoData.TransitionState storage ts = _state.transitions[slot][tid];

```
*GitHub*: [130](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L130-L130), [140](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L140-L140)

```solidity
File: contracts/L1/provers/Guardians.sol

/// @audit guardianIds...[]
88:              guardianIds[guardian] = guardians.length;

/// @audit _approvals...[]
119:         uint256 _approval = _approvals[version][_hash];

```
*GitHub*: [88](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L88-L88), [119](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L119-L119)

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

/// @audit _serialNumIsRevoked...[]
84:              _serialNumIsRevoked[index][serialNumBatch[i]] = true;

/// @audit _serialNumIsRevoked...[]
99:              delete _serialNumIsRevoked[index][serialNumBatch[i]];

```
*GitHub*: [84](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L84-L84), [99](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L99-L99)

```solidity
File: contracts/bridge/Bridge.sol

/// @audit addressBanned...[]
110:         addressBanned[_addr] = _ban;

/// @audit proofReceipt...[]
184:             proofReceipt[msgHash].receivedAt = receivedAt;

/// @audit proofReceipt...[]
190:             delete proofReceipt[msgHash];

/// @audit messageStatus...[]
191:             messageStatus[msgHash] = Status.RECALLED;

/// @audit proofReceipt...[]
243:                 proofReceipt[msgHash] = ProofReceipt({

/// @audit proofReceipt...[]
250:         if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) {

/// @audit proofReceipt...[]
264:             delete proofReceipt[msgHash];

/// @audit messageStatus...[]
518:         messageStatus[_msgHash] = _status;

```
*GitHub*: [110](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L110-L110), [184](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L184-L184), [190](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L190-L190), [191](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L191-L191), [243](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L243-L243), [250](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L250-L250), [264](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L264-L264), [518](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L518-L518)

```solidity
File: contracts/common/AddressManager.sol

/// @audit __addresses...[]
49:          __addresses[_chainId][_name] = _newAddress;

```
*GitHub*: [49](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressManager.sol#L49-L49)

```solidity
File: contracts/signal/SignalService.sol

/// @audit isAuthorized...[]
58:          isAuthorized[_addr] = _authorize;

```
*GitHub*: [58](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L58-L58)

```solidity
File: contracts/team/TimelockTokenPool.sol

/// @audit recipients...[]
142:         recipients[_recipient].grant = _grant;

```
*GitHub*: [142](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L142-L142)

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol

/// @audit isClaimed...[]
73:          isClaimed[hash] = true;

```
*GitHub*: [73](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L73-L73)

```solidity
File: contracts/tokenvault/ERC20Vault.sol

/// @audit bridgedToCanonical...[]
180:             delete bridgedToCanonical[_btokenNew];

/// @audit bridgedToCanonical...[]
188:         bridgedToCanonical[_btokenNew] = _ctoken;

/// @audit canonicalToBridged...[]
189:         canonicalToBridged[_ctoken.chainId][_ctoken.addr] = _btokenNew;

```
*GitHub*: [180](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L180-L180), [188](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L188-L188), [189](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L189-L189)

```solidity
File: contracts/verifiers/SgxVerifier.sol

/// @audit instances...[]
109:             emit InstanceDeleted(idx, instances[idx].addr);

/// @audit instances...[]
111:             delete instances[idx];

/// @audit instances...[]
236:         return instances[id].validSince <= block.timestamp

/// @audit instances...[]
237:             && block.timestamp <= instances[id].validSince + INSTANCE_EXPIRY;

```
*GitHub*: [109](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L109-L109), [111](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L111-L111), [236](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L236-L236), [237](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L237-L237)

</details>





### [G&#x2011;16] Combine `mapping`s referenced in the same function by the same key
Reads and subsequent writes can also be cheaper when a function requires both values and they both fit in the same storage slot (i.e. runtime gas savings). Even if the values can't be packed, if both fields are accessed in the same function (as is the case for these instances), combining them can save **~42 gas per access** due to [not having to recalculate the key's keccak256 hash](https://gist.github.com/IllIllI000/639032d73e35d7e968ff58d8784bc445) (Gkeccak256 - 30 gas) and that calculation's associated stack operations.

*There are 7 instances of this issue:*

```solidity
File: contracts/L1/libs/LibUtils.sol

/// @audit combine into a `struct`: blocks,transitions
23       function getTransition(
24           TaikoData.State storage _state,
25           TaikoData.Config memory _config,
26           uint64 _blockId,
27           bytes32 _parentHash
28       )
29           external
30           view
31           returns (TaikoData.TransitionState storage)
32       {
33           TaikoData.SlotB memory b = _state.slotB;
34           if (_blockId < b.lastVerifiedBlockId || _blockId >= b.numBlocks) {
35               revert L1_INVALID_BLOCK_ID();
36           }
37   
38           uint64 slot = _blockId % _config.blockRingBufferSize;
39           TaikoData.Block storage blk = _state.blocks[slot];
40           if (blk.blockId != _blockId) revert L1_BLOCK_MISMATCH();
41   
42           uint32 tid = getTransitionId(_state, blk, slot, _parentHash);
43           if (tid == 0) revert L1_TRANSITION_NOT_FOUND();
44   
45           return _state.transitions[slot][tid];
46:      }

```
*GitHub*: [23](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibUtils.sol#L23-L46)

```solidity
File: contracts/L1/libs/LibVerifying.sol

/// @audit combine into a `struct`: blocks,transitions
47       function init(
48           TaikoData.State storage _state,
49           TaikoData.Config memory _config,
50           bytes32 _genesisBlockHash
51       )
52           external
53       {
54           if (!_isConfigValid(_config)) revert L1_INVALID_CONFIG();
55   
56           // Init state
57           _state.slotA.genesisHeight = uint64(block.number);
58           _state.slotA.genesisTimestamp = uint64(block.timestamp);
59           _state.slotB.numBlocks = 1;
60   
61           // Init the genesis block
62           TaikoData.Block storage blk = _state.blocks[0];
63           blk.nextTransitionId = 2;
64           blk.proposedAt = uint64(block.timestamp);
65           blk.verifiedTransitionId = 1;
66   
67           // Init the first state transition
68           TaikoData.TransitionState storage ts = _state.transitions[0][1];
69           ts.blockHash = _genesisBlockHash;
70           ts.prover = address(0);
71           ts.timestamp = uint64(block.timestamp);
72   
73           emit BlockVerified({
74               blockId: 0,
75               assignedProver: address(0),
76               prover: address(0),
77               blockHash: _genesisBlockHash,
78               stateRoot: 0,
79               tier: 0,
80               contestations: 0
81           });
82:      }

/// @audit combine into a `struct`: blocks,transitions
85       function verifyBlocks(
86           TaikoData.State storage _state,
87           TaikoData.Config memory _config,
88           IAddressResolver _resolver,
89           uint64 _maxBlocksToVerify
90       )
91           internal
92       {
93           if (_maxBlocksToVerify == 0) {
94               return;
95           }
96   
97           // Retrieve the latest verified block and the associated transition used
98           // for its verification.
99           TaikoData.SlotB memory b = _state.slotB;
100          uint64 blockId = b.lastVerifiedBlockId;
101  
102          uint64 slot = blockId % _config.blockRingBufferSize;
103  
104          TaikoData.Block storage blk = _state.blocks[slot];
105          if (blk.blockId != blockId) revert L1_BLOCK_MISMATCH();
106  
107          uint32 tid = blk.verifiedTransitionId;
108  
109          // The following scenario should never occur but is included as a
110          // precaution.
111          if (tid == 0) revert L1_TRANSITION_ID_ZERO();
112  
113          // The `blockHash` variable represents the most recently trusted
114          // blockHash on L2.
115          bytes32 blockHash = _state.transitions[slot][tid].blockHash;
116          bytes32 stateRoot;
117          uint64 numBlocksVerified;
118          address tierProvider;
119  
120          // Unchecked is safe:
121          // - assignment is within ranges
122          // - blockId and numBlocksVerified values incremented will still be OK in the
123          // next 584K years if we verifying one block per every second
124          unchecked {
125              ++blockId;
126  
127              while (blockId < b.numBlocks && numBlocksVerified < _maxBlocksToVerify) {
128                  slot = blockId % _config.blockRingBufferSize;
129  
130                  blk = _state.blocks[slot];
131                  if (blk.blockId != blockId) revert L1_BLOCK_MISMATCH();
132  
133                  tid = LibUtils.getTransitionId(_state, blk, slot, blockHash);
134                  // When `tid` is 0, it indicates that there is no proven
135                  // transition with its parentHash equal to the blockHash of the
136                  // most recently verified block.
137                  if (tid == 0) break;
138  
139                  // A transition with the correct `parentHash` has been located.
140                  TaikoData.TransitionState storage ts = _state.transitions[slot][tid];
141  
142                  // It's not possible to verify this block if either the
143                  // transition is contested and awaiting higher-tier proof or if
144                  // the transition is still within its cooldown period.
145                  if (ts.contester != address(0)) {
146                      break;
147                  } else {
148                      if (tierProvider == address(0)) {
149                          tierProvider = _resolver.resolve("tier_provider", false);
150                      }
151                      if (
152                          uint256(ITierProvider(tierProvider).getTier(ts.tier).cooldownWindow) * 60
153                              + uint256(ts.timestamp).max(_state.slotB.lastUnpausedAt) > block.timestamp
154                      ) {
155                          // If cooldownWindow is 0, the block can theoretically
156                          // be proved and verified within the same L1 block.
157                          break;
158                      }
159                  }
160  
161                  // Mark this block as verified
162                  blk.verifiedTransitionId = tid;
163  
164                  // Update variables
165                  blockHash = ts.blockHash;
166                  stateRoot = ts.stateRoot;
167  
168                  // We consistently return the liveness bond and the validity
169                  // bond to the actual prover of the transition utilized for
170                  // block verification. If the actual prover happens to be the
171                  // block's assigned prover, he will receive both deposits,
172                  // ultimately earning the proving fee paid during block
173                  // proposal. In contrast, if the actual prover is different from
174                  // the block's assigned prover, the liveness bond serves as a
175                  // reward to the actual prover, while the assigned prover
176                  // forfeits his liveness bond due to failure to fulfill their
177                  // commitment.
178                  uint256 bondToReturn = uint256(ts.validityBond) + blk.livenessBond;
179  
180                  // Nevertheless, it's possible for the actual prover to be the
181                  // same individual or entity as the block's assigned prover.
182                  // Consequently, we have chosen to grant the actual prover only
183                  // half of the liveness bond as a reward.
184                  if (ts.prover != blk.assignedProver) {
185                      bondToReturn -= blk.livenessBond >> 1;
186                  }
187  
188                  IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));
189                  tko.transfer(ts.prover, bondToReturn);
190  
191                  // Note: We exclusively address the bonds linked to the
192                  // transition used for verification. While there may exist
193                  // other transitions for this block, we disregard them entirely.
194                  // The bonds for these other transitions are burned either when
195                  // the transitions are generated or proven. In such cases, both
196                  // the provers and contesters of those transitions forfeit their bonds.
197  
198                  emit BlockVerified({
199                      blockId: blockId,
200                      assignedProver: blk.assignedProver,
201                      prover: ts.prover,
202                      blockHash: blockHash,
203                      stateRoot: stateRoot,
204                      tier: ts.tier,
205                      contestations: ts.contestations
206                  });
207  
208                  ++blockId;
209                  ++numBlocksVerified;
210              }
211  
212              if (numBlocksVerified > 0) {
213                  uint64 lastVerifiedBlockId = b.lastVerifiedBlockId + numBlocksVerified;
214  
215                  // Update protocol level state variables
216                  _state.slotB.lastVerifiedBlockId = lastVerifiedBlockId;
217  
218                  // sync chain data
219                  _syncChainData(_config, _resolver, lastVerifiedBlockId, stateRoot);
220              }
221          }
222:     }

```
*GitHub*: [47](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L47-L82), [85](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L85-L222)

```solidity
File: contracts/bridge/Bridge.sol

/// @audit combine into a `struct`: messageStatus,proofReceipt
155      function recallMessage(
156          Message calldata _message,
157          bytes calldata _proof
158      )
159          external
160          nonReentrant
161          whenNotPaused
162          sameChain(_message.srcChainId)
163      {
164          bytes32 msgHash = hashMessage(_message);
165  
166          if (messageStatus[msgHash] != Status.NEW) revert B_STATUS_MISMATCH();
167  
168          uint64 receivedAt = proofReceipt[msgHash].receivedAt;
169          bool isMessageProven = receivedAt != 0;
170  
171          if (!isMessageProven) {
172              address signalService = resolve("signal_service", false);
173  
174              if (!ISignalService(signalService).isSignalSent(address(this), msgHash)) {
175                  revert B_MESSAGE_NOT_SENT();
176              }
177  
178              bytes32 failureSignal = signalForFailedMessage(msgHash);
179              if (!_proveSignalReceived(signalService, failureSignal, _message.destChainId, _proof)) {
180                  revert B_NOT_FAILED();
181              }
182  
183              receivedAt = uint64(block.timestamp);
184              proofReceipt[msgHash].receivedAt = receivedAt;
185          }
186  
187          (uint256 invocationDelay,) = getInvocationDelays();
188  
189          if (block.timestamp >= invocationDelay + receivedAt) {
190              delete proofReceipt[msgHash];
191              messageStatus[msgHash] = Status.RECALLED;
192  
193              // Execute the recall logic based on the contract's support for the
194              // IRecallableSender interface
195              if (_message.from.supportsInterface(type(IRecallableSender).interfaceId)) {
196                  _storeContext(msgHash, address(this), _message.srcChainId);
197  
198                  // Perform recall
199                  IRecallableSender(_message.from).onMessageRecalled{ value: _message.value }(
200                      _message, msgHash
201                  );
202  
203                  // Must reset the context after the message call
204                  _resetContext();
205              } else {
206                  _message.srcOwner.sendEther(_message.value);
207              }
208              emit MessageRecalled(msgHash);
209          } else if (!isMessageProven) {
210              emit MessageReceived(msgHash, _message, true);
211          } else {
212              revert B_INVOCATION_TOO_EARLY();
213          }
214:     }

/// @audit combine into a `struct`: messageStatus,proofReceipt
217      function processMessage(
218          Message calldata _message,
219          bytes calldata _proof
220      )
221          external
222          nonReentrant
223          whenNotPaused
224          sameChain(_message.destChainId)
225      {
226          bytes32 msgHash = hashMessage(_message);
227          if (messageStatus[msgHash] != Status.NEW) revert B_STATUS_MISMATCH();
228  
229          address signalService = resolve("signal_service", false);
230          uint64 receivedAt = proofReceipt[msgHash].receivedAt;
231          bool isMessageProven = receivedAt != 0;
232  
233          (uint256 invocationDelay, uint256 invocationExtraDelay) = getInvocationDelays();
234  
235          if (!isMessageProven) {
236              if (!_proveSignalReceived(signalService, msgHash, _message.srcChainId, _proof)) {
237                  revert B_NOT_RECEIVED();
238              }
239  
240              receivedAt = uint64(block.timestamp);
241  
242              if (invocationDelay != 0) {
243                  proofReceipt[msgHash] = ProofReceipt({
244                      receivedAt: receivedAt,
245                      preferredExecutor: _message.gasLimit == 0 ? _message.destOwner : msg.sender
246                  });
247              }
248          }
249  
250          if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) {
251              // If msg.sender is not the one that proved the message, then there
252              // is an extra delay.
253              unchecked {
254                  invocationDelay += invocationExtraDelay;
255              }
256          }
257  
258          if (block.timestamp >= invocationDelay + receivedAt) {
259              // If the gas limit is set to zero, only the owner can process the message.
260              if (_message.gasLimit == 0 && msg.sender != _message.destOwner) {
261                  revert B_PERMISSION_DENIED();
262              }
263  
264              delete proofReceipt[msgHash];
265  
266              uint256 refundAmount;
267  
268              // Process message differently based on the target address
269              if (
270                  _message.to == address(0) || _message.to == address(this)
271                      || _message.to == signalService || addressBanned[_message.to]
272              ) {
273                  // Handle special addresses that don't require actual invocation but
274                  // mark message as DONE
275                  refundAmount = _message.value;
276                  _updateMessageStatus(msgHash, Status.DONE);
277              } else {
278                  // Use the specified message gas limit if called by the owner, else
279                  // use remaining gas
280                  uint256 gasLimit = msg.sender == _message.destOwner ? gasleft() : _message.gasLimit;
281  
282                  if (_invokeMessageCall(_message, msgHash, gasLimit)) {
283                      _updateMessageStatus(msgHash, Status.DONE);
284                  } else {
285                      _updateMessageStatus(msgHash, Status.RETRIABLE);
286                  }
287              }
288  
289              // Determine the refund recipient
290              address refundTo =
291                  _message.refundTo == address(0) ? _message.destOwner : _message.refundTo;
292  
293              // Refund the processing fee
294              if (msg.sender == refundTo) {
295                  refundTo.sendEther(_message.fee + refundAmount);
296              } else {
297                  // If sender is another address, reward it and refund the rest
298                  msg.sender.sendEther(_message.fee);
299                  refundTo.sendEther(refundAmount);
300              }
301              emit MessageExecuted(msgHash);
302          } else if (!isMessageProven) {
303              emit MessageReceived(msgHash, _message, false);
304          } else {
305              revert B_INVOCATION_TOO_EARLY();
306          }
307:     }

```
*GitHub*: [155](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L155-L214), [217](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L217-L307)

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol

/// @audit combine into a `struct`: claimedAmount,withdrawnAmount
104      function getBalance(address user)
105          public
106          view
107          returns (uint256 balance, uint256 withdrawableAmount)
108      {
109          balance = claimedAmount[user];
110          // If balance is 0 then there is no balance and withdrawable amount
111          if (balance == 0) return (0, 0);
112          // Balance might be positive before end of claiming (claimEnd - if claimed already) but
113          // withdrawable is 0.
114          if (block.timestamp < claimEnd) return (balance, 0);
115  
116          // Hard cap timestamp - so range cannot go over - to get more allocation over time.
117          uint256 timeBasedAllowance = balance
118              * (block.timestamp.min(claimEnd + withdrawalWindow) - claimEnd) / withdrawalWindow;
119  
120          withdrawableAmount = timeBasedAllowance - withdrawnAmount[user];
121:     }

```
*GitHub*: [104](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L104-L121)

```solidity
File: contracts/tokenvault/ERC20Vault.sol

/// @audit combine into a `struct`: bridgedToCanonical,btokenBlacklist
148      function changeBridgedToken(
149          CanonicalERC20 calldata _ctoken,
150          address _btokenNew
151      )
152          external
153          nonReentrant
154          whenNotPaused
155          onlyOwner
156          returns (address btokenOld_)
157      {
158          if (_btokenNew == address(0) || bridgedToCanonical[_btokenNew].addr != address(0)) {
159              revert VAULT_INVALID_NEW_BTOKEN();
160          }
161  
162          if (btokenBlacklist[_btokenNew]) revert VAULT_BTOKEN_BLACKLISTED();
163  
164          if (IBridgedERC20(_btokenNew).owner() != owner()) {
165              revert VAULT_NOT_SAME_OWNER();
166          }
167  
168          btokenOld_ = canonicalToBridged[_ctoken.chainId][_ctoken.addr];
169  
170          if (btokenOld_ != address(0)) {
171              CanonicalERC20 memory ctoken = bridgedToCanonical[btokenOld_];
172  
173              // The ctoken must match the saved one.
174              if (
175                  ctoken.decimals != _ctoken.decimals
176                      || keccak256(bytes(ctoken.symbol)) != keccak256(bytes(_ctoken.symbol))
177                      || keccak256(bytes(ctoken.name)) != keccak256(bytes(_ctoken.name))
178              ) revert VAULT_CTOKEN_MISMATCH();
179  
180              delete bridgedToCanonical[_btokenNew];
181              btokenBlacklist[btokenOld_] = true;
182  
183              // Start the migration
184              IBridgedERC20(btokenOld_).changeMigrationStatus(_btokenNew, false);
185              IBridgedERC20(_btokenNew).changeMigrationStatus(btokenOld_, true);
186          }
187  
188          bridgedToCanonical[_btokenNew] = _ctoken;
189          canonicalToBridged[_ctoken.chainId][_ctoken.addr] = _btokenNew;
190  
191          emit BridgedTokenChanged({
192              srcChainId: _ctoken.chainId,
193              ctoken: _ctoken.addr,
194              btokenOld: btokenOld_,
195              btokenNew: _btokenNew,
196              ctokenSymbol: _ctoken.symbol,
197              ctokenName: _ctoken.name,
198              ctokenDecimal: _ctoken.decimals
199          });
200:     }

```
*GitHub*: [148](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L148-L200)



### [G&#x2011;17] Assigning state variables directly with `struct` constructors wastes gas
Using constructors for struct means that the compiler needs to organize the fields in memory before doing the assignment, which wastes gas. Set each field directly in storage (use dot-notation) to save **~21 gas** per [member](https://gist.github.com/IllIllI000/b9c534a83c2d8c3e7eab7ed9dfeee9c1)

*There are 4 instances of this issue:*

```solidity
File: contracts/bridge/Bridge.sol

243                  proofReceipt[msgHash] = ProofReceipt({
244                      receivedAt: receivedAt,
245                      preferredExecutor: _message.gasLimit == 0 ? _message.destOwner : msg.sender
246:                 });

549:             __ctx = Context(_msgHash, _from, _srcChainId);

```
*GitHub*: [243](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L243-L246), [549](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L549-L549)

```solidity
File: contracts/verifiers/SgxVerifier.sol

217:             instances[nextInstanceId] = Instance(_instances[i], validSince);

229:         instances[id] = Instance(newInstance, uint64(block.timestamp));

```
*GitHub*: [217](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L217-L217), [229](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L229-L229)



### [G&#x2011;18] Constructors can be marked `payable`
Payable functions cost less gas to execute, since the compiler does not have to add extra checks to ensure that a payment wasn't provided. A constructor can safely be marked as payable, since only the deployer would be able to pass funds, and the project itself would not pass any funds.

*There are 3 instances of this issue:*

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

54:       constructor(address sigVerifyLibAddr, address pemCertLibAddr) {

```
*GitHub*: [54](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L54)

```solidity
File: contracts/automata-attestation/utils/SigVerifyLib.sol

20:       constructor(address es256Verifier) {

```
*GitHub*: [20](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L20)

```solidity
File: contracts/common/EssentialContract.sol

64        constructor() {
65:           _disableInitializers();

```
*GitHub*: [64](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L64-L65)



### [G&#x2011;19] `private` functions only called once can be inlined to save gas
Not inlining costs **20 to 40 gas** because of two extra `JUMP` instructions and additional stack operations needed for function calls. The inliner can do it only for 'simple' cases:
> Now to get back to the point why we require the routine to be simple: As soon as you do more complicated things like for example branching, calling external contracts, the Common Subexpression Eliminator cannot re-construct the code anymore or does not do full symbolic evaluation of the expressions. 

https://soliditylang.org/blog/2021/03/02/saving-gas-with-simple-inliner/

Therefore, the instances below contain branching or use op-codes with side-effects

*There are 25 instances of this issue:*

<details>
<summary>see instances</summary>


```solidity
File: contracts/L1/hooks/AssignmentHook.sol

164      function _getProverFee(
165          TaikoData.TierFee[] memory _tierFees,
166          uint16 _tierId
167      )
168          private
169          pure
170          returns (uint256)
171:     {

```
*GitHub*: [164](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L164-L171)

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

162:     function _verify(bytes calldata quote) private view returns (bool, bytes memory) {

175      function _verifyQEReportWithIdentity(V3Struct.EnclaveReport memory quoteEnclaveReport)
176          private
177          view
178          returns (bool, EnclaveIdStruct.EnclaveIdStatus status)
179:     {

206      function _checkTcbLevels(
207          IPEMCertChainLib.PCKCertificateField memory pck,
208          TCBInfoStruct.TCBInfo memory tcb
209      )
210          private
211          pure
212          returns (bool, TCBInfoStruct.TCBStatus status)
213:     {

229      function _isCpuSvnHigherOrGreater(
230          uint256[] memory pckCpuSvns,
231          uint8[] memory tcbCpuSvns
232      )
233          private
234          pure
235          returns (bool)
236:     {

248      function _verifyCertChain(IPEMCertChainLib.ECSha256Certificate[] memory certs)
249          private
250          view
251          returns (bool)
252:     {

303      function _enclaveReportSigVerification(
304          bytes memory pckCertPubKey,
305          bytes memory signedQuoteData,
306          V3Struct.ECDSAQuoteV3AuthData memory authDataV3,
307          V3Struct.EnclaveReport memory qeEnclaveReport
308      )
309          private
310          view
311          returns (bool)
312:     {

```
*GitHub*: [162](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L162-L162), [175](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L175-L179), [206](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L206-L213), [229](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L229-L236), [248](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L248-L252), [303](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L303-L312)

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol

216      function _removeHeadersAndFooters(string memory pemData)
217          private
218          pure
219          returns (bool success, bytes memory extracted, uint256 endIndex)
220:     {

269      function _findPckTcbInfo(
270          bytes memory der,
271          uint256 tbsPtr,
272          uint256 tbsParentPtr
273      )
274          private
275          pure
276          returns (
277              bool success,
278              uint256 pcesvn,
279              uint256[] memory cpusvns,
280              bytes memory fmspcBytes,
281              bytes memory pceidBytes
282          )
283:     {

341      function _findTcb(
342          bytes memory der,
343          uint256 oidPtr
344      )
345          private
346          pure
347          returns (bool success, uint256 pcesvn, uint256[] memory cpusvns)
348:     {

```
*GitHub*: [216](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L216-L220), [269](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L269-L283), [341](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L341-L348)

```solidity
File: contracts/bridge/Bridge.sol

555:     function _loadContext() private view returns (Context memory) {

```
*GitHub*: [555](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L555-L555)

```solidity
File: contracts/signal/SignalService.sol

271      function _cacheChainData(
272          HopProof memory _hop,
273          uint64 _chainId,
274          uint64 _blockId,
275          bytes32 _signalRoot,
276          bool _isFullProof,
277          bool _isLastHop
278      )
279          private
280:     {

```
*GitHub*: [271](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L271-L280)

```solidity
File: contracts/team/TimelockTokenPool.sol

225:     function _voidGrant(Grant storage _grant) private returns (uint128 amountVoided) {

267:     function _validateGrant(Grant memory _grant) private pure {

```
*GitHub*: [225](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L225-L225), [267](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L267-L267)

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

240      function _handleMessage(
241          address _user,
242          BridgeTransferOp memory _op
243      )
244          private
245          returns (bytes memory msgData_, CanonicalNFT memory ctoken_)
246:     {

288      function _getOrDeployBridgedToken(CanonicalNFT memory _ctoken)
289          private
290          returns (address btoken_)
291:     {

303:     function _deployBridgedToken(CanonicalNFT memory _ctoken) private returns (address btoken_) {

```
*GitHub*: [240](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L240-L246), [288](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L288-L291), [303](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L303-L303)

```solidity
File: contracts/tokenvault/ERC20Vault.sol

348      function _handleMessage(
349          address _user,
350          address _token,
351          address _to,
352          uint256 _amount
353      )
354          private
355          returns (bytes memory msgData_, CanonicalERC20 memory ctoken_, uint256 balanceChange_)
356:     {

391      function _getOrDeployBridgedToken(CanonicalERC20 memory ctoken)
392          private
393          returns (address btoken)
394:     {

407:     function _deployBridgedToken(CanonicalERC20 memory ctoken) private returns (address btoken) {

```
*GitHub*: [348](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L348-L356), [391](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L391-L394), [407](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L407-L407)

```solidity
File: contracts/tokenvault/ERC721Vault.sol

187      function _handleMessage(
188          address _user,
189          BridgeTransferOp memory _op
190      )
191          private
192          returns (bytes memory msgData_, CanonicalNFT memory ctoken_)
193:     {

224      function _getOrDeployBridgedToken(CanonicalNFT memory _ctoken)
225          private
226          returns (address btoken_)
227:     {

240:     function _deployBridgedToken(CanonicalNFT memory _ctoken) private returns (address btoken_) {

```
*GitHub*: [187](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L187-L193), [224](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L224-L227), [240](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L240-L240)

```solidity
File: contracts/verifiers/SgxVerifier.sol

226:     function _replaceInstance(uint256 id, address oldInstance, address newInstance) private {

233:     function _isInstanceValid(uint256 id, address instance) private view returns (bool) {

```
*GitHub*: [226](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L226-L226), [233](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L233-L233)

</details>





### [G&#x2011;20] `unchecked {}`  can be used on the division of two `uint`s in order to save gas
The division cannot overflow, since both the numerator and the denominator are non-negative

*There are 11 instances of this issue:*

<details>
<summary>see instances</summary>


```solidity
File: contracts/L1/libs/LibVerifying.sol

262:                 || _config.ethDepositMaxFee > type(uint96).max / _config.ethDepositMaxCountPerBlock

```
*GitHub*: [262](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L262-L262)

```solidity
File: contracts/L2/Lib1559Math.sol

28:          return _ethQty(_gasExcess, _adjustmentFactor) / LibFixedPointMath.SCALING_FACTOR

28           return _ethQty(_gasExcess, _adjustmentFactor) / LibFixedPointMath.SCALING_FACTOR
29:              / _adjustmentFactor;

41:          uint256 input = _gasExcess * LibFixedPointMath.SCALING_FACTOR / _adjustmentFactor;

```
*GitHub*: [28](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/Lib1559Math.sol#L28-L28), [28](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/Lib1559Math.sol#L28-L29), [41](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/Lib1559Math.sol#L41-L41)

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol

359:                 ? uint16(bytes2(svnValueBytes)) / 256

```
*GitHub*: [359](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L359-L359)

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

155:             uint256 upperDigit = digits / 16;

```
*GitHub*: [155](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L155-L155)

```solidity
File: contracts/team/TimelockTokenPool.sol

197:         uint128 _amountUnlocked = amountUnlocked / 1e18; // divide first

264:         return _amount * uint64(block.timestamp - _start) / _period;

```
*GitHub*: [197](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L197-L197), [264](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L264-L264)

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol

117          uint256 timeBasedAllowance = balance
118:             * (block.timestamp.min(claimEnd + withdrawalWindow) - claimEnd) / withdrawalWindow;

```
*GitHub*: [117](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L117-L118)

```solidity
File: contracts/thirdparty/optimism/rlp/RLPWriter.sol

39:              while (_len / i != 0) {

47:                  out_[i] = bytes1(uint8((_len / (256 ** (lenLen - i))) % 256));

```
*GitHub*: [39](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L39-L39), [47](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L47-L47)

</details>





### [G&#x2011;21] `internal` functions only called once can be inlined to save gas
Not inlining costs **20 to 40 gas** because of two extra `JUMP` instructions and additional stack operations needed for function calls. The inliner can do it only for 'simple' cases:
> Now to get back to the point why we require the routine to be simple: As soon as you do more complicated things like for example branching, calling external contracts, the Common Subexpression Eliminator cannot re-construct the code anymore or does not do full symbolic evaluation of the expressions. 

https://soliditylang.org/blog/2021/03/02/saving-gas-with-simple-inliner/

Therefore, the instances below contain branching or use op-codes with side-effects

*There are 4 instances of this issue:*

```solidity
File: contracts/L1/provers/Guardians.sol

111:     function approve(uint256 _operationId, bytes32 _hash) internal returns (bool approved_) {

124:     function deleteApproval(bytes32 _hash) internal {

```
*GitHub*: [111](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L111-L111), [124](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L124-L124)

```solidity
File: contracts/tokenvault/adapters/USDCAdapter.sol

43:      function _mintToken(address _account, uint256 _amount) internal override {

47:      function _burnToken(address _from, uint256 _amount) internal override {

```
*GitHub*: [43](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L43-L43), [47](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L47-L47)



### [G&#x2011;22] Assembly: Use scratch space when building emitted events with two data arguments
Using the [scratch space](https://gist.github.com/IllIllI000/87c4f03139fa03780fa548b8e4b02b5b) for more than one, but at most two words worth of data (non-indexed arguments) will save gas over needing Solidity's abi memory expansion used for emitting normally.

*There are 6 instances of this issue:*

```solidity
File: contracts/L2/TaikoL2.sol

157:         emit Anchored(blockhash(parentId), gasExcess);

```
*GitHub*: [157](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L157-L157)

```solidity
File: contracts/common/AddressManager.sol

50:          emit AddressSet(_chainId, _name, _newAddress, oldAddress);

```
*GitHub*: [50](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressManager.sol#L50-L50)

```solidity
File: contracts/signal/SignalService.sol

250:         emit ChainDataSynced(_chainId, _blockId, _kind, _chainData, signal_);

```
*GitHub*: [250](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L250-L250)

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol

93:          emit Withdrawn(user, amount);

```
*GitHub*: [93](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L93-L93)

```solidity
File: contracts/verifiers/SgxVerifier.sol

220:             emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);

230:         emit InstanceAdded(id, newInstance, oldInstance, block.timestamp);

```
*GitHub*: [220](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220-L220), [230](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L230-L230)



### [G&#x2011;23] Nesting `if`-statements is cheaper than using `&&`
Nesting `if`-statements avoids the stack operations of setting up and using an extra `jumpdest`, and saves **6 [gas](https://gist.github.com/IllIllI000/7f3b818abecfadbef93b894481ae7d19)**

*There are 16 instances of this issue:*

<details>
<summary>see instances</summary>


```solidity
File: contracts/L1/hooks/AssignmentHook.sol

120          if (input.tip != 0 && block.coinbase != address(0)) {
121              address(block.coinbase).sendEther(input.tip);
122:         }

```
*GitHub*: [120](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L120-L122)

```solidity
File: contracts/L1/libs/LibProposing.sol

108          if (params.parentMetaHash != 0 && parentMetaHash != params.parentMetaHash) {
109              revert L1_UNEXPECTED_PARENT();
110:         }

164                  if (_config.blobReuseEnabled && params.cacheBlobForReuse) {
165                      _state.reusableBlobs[meta_.blobHash] = block.timestamp;
166                      emit BlobCached(meta_.blobHash);
167:                 }

310              if (proposerOne != address(0) && msg.sender != proposerOne) {
311                  return false;
312:             }

```
*GitHub*: [108](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L108-L110), [164](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L164-L167), [310](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L310-L312)

```solidity
File: contracts/L2/TaikoL2.sol

141          if (!skipFeeCheck() && block.basefee != basefee) {
142              revert L2_BASEFEE_MISMATCH();
143:         }

275              if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {
276                  numL1Blocks = _l1BlockId - lastSyncedBlock;
277:             }

```
*GitHub*: [141](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L141-L143), [275](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L275-L277)

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

220              if (pceSvnIsHigherOrGreater && cpuSvnsAreHigherOrGreater) {
221                  status = current.status;
222                  bool tcbIsRevoked = status == TCBInfoStruct.TCBStatus.TCB_REVOKED;
223                  return (!tcbIsRevoked, status);
224:             }

```
*GitHub*: [220](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L220-L224)

```solidity
File: contracts/bridge/Bridge.sol

250          if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) {
251              // If msg.sender is not the one that proved the message, then there
252              // is an extra delay.
253              unchecked {
254                  invocationDelay += invocationExtraDelay;
255              }
256:         }

260              if (_message.gasLimit == 0 && msg.sender != _message.destOwner) {
261                  revert B_PERMISSION_DENIED();
262:             }

```
*GitHub*: [250](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L250-L256), [260](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L260-L262)

```solidity
File: contracts/common/AddressResolver.sol

85           if (!_allowZeroAddress && addr_ == address(0)) {
86               revert RESOLVER_ZERO_ADDR(_chainId, _name);
87:          }

```
*GitHub*: [85](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressResolver.sol#L85-L87)

```solidity
File: contracts/common/EssentialContract.sol

42:          if (msg.sender != owner() && msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();

```
*GitHub*: [42](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L42-L42)

```solidity
File: contracts/signal/SignalService.sol

285          if (cacheStateRoot && _isFullProof && !_isLastHop) {
286              _syncChainData(_chainId, LibSignals.STATE_ROOT, _blockId, _hop.rootHash);
287:         }

293          if (cacheSignalRoot && (_isFullProof || !_isLastHop)) {
294              _syncChainData(_chainId, LibSignals.SIGNAL_ROOT, _blockId, _signalRoot);
295:         }

```
*GitHub*: [285](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L285-L287), [293](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L293-L295)

```solidity
File: contracts/team/TimelockTokenPool.sol

277:             if (_cliff > 0 && _cliff <= _start) revert INVALID_GRANT();

```
*GitHub*: [277](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L277-L277)

```solidity
File: contracts/tokenvault/BridgedERC20.sol

38           if (msg.sender != owner() && msg.sender != snapshooter) {
39               revert BTOKEN_UNAUTHORIZED();
40:          }

```
*GitHub*: [38](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L38-L40)

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol

45           if (_migratingAddress == migratingAddress && _migratingInbound == migratingInbound) {
46               revert BB_INVALID_PARAMS();
47:          }

```
*GitHub*: [45](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L45-L47)

</details>





### [G&#x2011;24] `>=` costs less gas than `>`
The compiler uses opcodes `GT` and `ISZERO` for solidity code that uses `>`, but only requires `LT` for `>=`, [which saves **3 gas**](https://gist.github.com/IllIllI000/3dc79d25acccfa16dee4e83ffdc6ffde). If `<` is being used, the condition can be inverted. In cases where a for-loop is being used, one can count down rather than up, in order to use the optimal operator (e.g. `for (i = len-1; i >= 1; --i)`)

*There are 130 instances of this issue:*

<details>
<summary>see instances</summary>


```solidity
File: contracts/L1/hooks/AssignmentHook.sol

82:              block.timestamp > assignment.expiry

85:                  || assignment.maxBlockId != 0 && _meta.id > assignment.maxBlockId

86:                  || assignment.maxProposedIn != 0 && block.number > assignment.maxProposedIn

125:         if (address(this).balance > 0) {

172:         for (uint256 i; i < _tierFees.length; ++i) {

```
*GitHub*: [82](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L82-L82), [85](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L85-L85), [86](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L86-L86), [125](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L125-L125), [172](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L172-L172)

```solidity
File: contracts/L1/libs/LibDepositing.sol

78:          if (numPending < _config.ethDepositMinCountPerBlock) {

86:              for (uint256 i; i < deposits_.length;) {

93:                  uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount;

140                  && _state.slotA.numEthDeposits - _state.slotA.nextEthDepositToProcess
141:                     < _config.ethDepositRingBufferSize - 1;

150:         if (_amount > type(uint96).max) revert L1_INVALID_ETH_DEPOSIT();

```
*GitHub*: [78](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L78-L78), [86](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L86-L86), [93](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L93-L93), [140](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L140-L141), [150](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L150-L150)

```solidity
File: contracts/L1/libs/LibProposing.sol

171:             if (uint256(params.txListByteOffset) + params.txListByteSize > MAX_BYTES_PER_BLOB) {

195:         if (meta_.txListByteSize == 0 || meta_.txListByteSize > _config.blockMaxTxListBytes) {

244:             for (uint256 i; i < params.hookCalls.length; ++i) {

296:         return _state.reusableBlobs[_blobHash] + _config.blobExpiry > block.timestamp;

```
*GitHub*: [171](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L171-L171), [195](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L195-L195), [244](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L244-L244), [296](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L296-L296)

```solidity
File: contracts/L1/libs/LibProving.sol

134:         if (_proof.tier == 0 || _proof.tier < _meta.minTier || _proof.tier < ts.tier) {

134:         if (_proof.tier == 0 || _proof.tier < _meta.minTier || _proof.tier < ts.tier) {

192:             bool returnLivenessBond = blk.livenessBond > 0 && _proof.data.length == 32

203:         if (_proof.tier > ts.tier) {

381:             if (reward > _tier.validityBond) {

```
*GitHub*: [134](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L134-L134), [134](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L134-L134), [192](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L192-L192), [203](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L203-L203), [381](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L381-L381)

```solidity
File: contracts/L1/libs/LibUtils.sol

34:          if (_blockId < b.lastVerifiedBlockId || _blockId >= b.numBlocks) {

```
*GitHub*: [34](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibUtils.sol#L34-L34)

```solidity
File: contracts/L1/libs/LibVerifying.sol

127:             while (blockId < b.numBlocks && numBlocksVerified < _maxBlocksToVerify) {

127:             while (blockId < b.numBlocks && numBlocksVerified < _maxBlocksToVerify) {

152                          uint256(ITierProvider(tierProvider).getTier(ts.tier).cooldownWindow) * 60
153:                             + uint256(ts.timestamp).max(_state.slotB.lastUnpausedAt) > block.timestamp

212:             if (numBlocksVerified > 0) {

238:         if (_lastVerifiedBlockId > lastSyncedBlock + _config.blockSyncThreshold) {

251:                 || _config.blockMaxTxListBytes > 128 * 1024 // calldata up to 128K

256:             || _config.ethDepositMaxCountPerBlock > 32

257:                 || _config.ethDepositMaxCountPerBlock < _config.ethDepositMinCountPerBlock

260:                 || _config.ethDepositMaxAmount > type(uint96).max || _config.ethDepositGas == 0

262:                 || _config.ethDepositMaxFee > type(uint96).max / _config.ethDepositMaxCountPerBlock

```
*GitHub*: [127](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L127-L127), [127](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L127-L127), [152](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L152-L153), [212](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L212-L212), [238](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L238-L238), [251](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L251-L251), [256](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L256-L256), [257](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L257-L257), [260](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L260-L260), [262](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L262-L262)

```solidity
File: contracts/L1/provers/Guardians.sol

63:          if (_newGuardians.length < MIN_NUM_GUARDIANS || _newGuardians.length > type(uint8).max) {

63:          if (_newGuardians.length < MIN_NUM_GUARDIANS || _newGuardians.length > type(uint8).max) {

68:          if (_minGuardians < (_newGuardians.length + 1) >> 1 || _minGuardians > _newGuardians.length)

68:          if (_minGuardians < (_newGuardians.length + 1) >> 1 || _minGuardians > _newGuardians.length)

74:          for (uint256 i; i < guardians.length; ++i) {

80:          for (uint256 i = 0; i < _newGuardians.length; ++i) {

133:             for (uint256 i; i < guardiansLength; ++i) {

```
*GitHub*: [63](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L63-L63), [63](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L63-L63), [68](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L68-L68), [68](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L68-L68), [74](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L74-L74), [80](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L80-L80), [133](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L133-L133)

```solidity
File: contracts/L2/Lib1559Math.sol

42:          if (input > LibFixedPointMath.MAX_EXP_INPUT) {

```
*GitHub*: [42](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/Lib1559Math.sol#L42-L42)

```solidity
File: contracts/L2/TaikoL2.sol

82:          if (block.chainid <= 1 || block.chainid > type(uint64).max) {

145:         if (_l1BlockId > lastSyncedBlock + BLOCK_SYNC_THRESHOLD) {

234:             for (uint256 i; i < 255 && _blockId >= i + 1; ++i) {

262:         if (gasExcess > 0) {

275:             if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {

275:             if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {

279:             if (numL1Blocks > 0) {

281:                 excess = excess > issuance ? excess - issuance : 1;

```
*GitHub*: [82](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L82-L82), [145](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L145-L145), [234](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L234-L234), [262](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L262-L262), [275](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L275-L275), [275](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L275-L275), [279](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L279-L279), [281](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L281-L281)

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

80:          for (uint256 i; i < serialNumBatch.length; ++i) {

95:          for (uint256 i; i < serialNumBatch.length; ++i) {

191:         for (uint256 i; i < enclaveId.tcbLevels.length; ++i) {

214:         for (uint256 i; i < tcb.tcbLevels.length; ++i) {

240:         for (uint256 i; i < CPUSVN_LENGTH; ++i) {

241:             if (pckCpuSvns[i] < tcbCpuSvns[i]) {

259:         for (uint256 i; i < n; ++i) {

280:                 block.timestamp > certs[i].notBefore && block.timestamp < certs[i].notAfter;

280:                 block.timestamp > certs[i].notBefore && block.timestamp < certs[i].notAfter;

420:             for (uint256 i; i < 3; ++i) {

```
*GitHub*: [80](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L80-L80), [95](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L95-L95), [191](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L191-L191), [214](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L214-L214), [240](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L240-L240), [241](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L241-L241), [259](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L259-L259), [280](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L280-L280), [280](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L280-L280), [420](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L420-L420)

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol

54:          for (uint256 i; i < size; ++i) {

56:              if (i > 0) {

244:         for (uint256 i; i < split.length; ++i) {

323:                     if (extnValuePtr.ixl() < extnValueParentPtr.ixl()) {

333:             if (tbsPtr.ixl() < tbsParentPtr.ixl()) {

354:         for (uint256 i; i < SGX_TCB_CPUSVN_SIZE + 1; ++i) {

358:             uint16 svnValue = svnValueBytes.length < 2

```
*GitHub*: [54](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L54-L54), [56](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L56-L56), [244](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L244-L244), [323](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L323-L323), [333](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L333-L333), [354](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L354-L354), [358](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L358-L358)

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

153:         for (uint256 i; i < encoded.length; ++i) {

218:         if (cert.certType < 1 || cert.certType > 5) {

218:         if (cert.certType < 1 || cert.certType > 5) {

281:         for (uint256 i; i < 3; ++i) {

```
*GitHub*: [153](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L153-L153), [218](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L218-L218), [218](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L218-L218), [281](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L281-L281)

```solidity
File: contracts/automata-attestation/utils/BytesUtils.sol

69:          if (otherlen < len) {

80:          for (uint256 idx = 0; idx < shortest; idx += 32) {

90:                  if (shortest > 32) {

333:         for (uint256 i; i < len; ++i) {

```
*GitHub*: [69](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L69-L69), [80](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L80-L80), [90](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L90-L90), [333](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L333-L333)

```solidity
File: contracts/automata-attestation/utils/RsaVerify.sol

140:         for (uint256 i = 2; i < 2 + paddingLen; ++i) {

152:             for (uint256 i; i < digestAlgoWithParamLen; ++i) {

158:             for (uint256 i; i < digestAlgoWithParamLen; ++i) {

174:         for (uint256 i; i < _sha256.length; ++i) {

273:         for (uint256 i = 2; i < 2 + paddingLen; ++i) {

283:         for (uint256 i; i < sha1Prefix.length; ++i) {

290:         for (uint256 i; i < _sha1.length; ++i) {

```
*GitHub*: [140](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L140-L140), [152](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L152-L152), [158](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L158-L158), [174](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L174-L174), [273](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L273-L273), [283](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L283-L283), [290](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L290-L290)

```solidity
File: contracts/automata-attestation/utils/X509DateUtils.sol

18:              if (uint8(x509Time[0]) - 48 < 5) yrs += 2000;

48:          for (uint16 i = 1970; i < year; ++i) {

59:          for (uint8 i = 1; i < month; ++i) {

```
*GitHub*: [18](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L18-L18), [48](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L48-L48), [59](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L59-L59)

```solidity
File: contracts/bridge/Bridge.sol

90:          for (uint256 i; i < _msgHashes.length; ++i) {

```
*GitHub*: [90](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L90-L90)

```solidity
File: contracts/common/AddressResolver.sol

59:          if (block.chainid > type(uint64).max) {

```
*GitHub*: [59](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressResolver.sol#L59-L59)

```solidity
File: contracts/libs/LibMath.sol

13:          return _a > _b ? _b : _a;

21:          return _a > _b ? _a : _b;

```
*GitHub*: [13](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibMath.sol#L13-L13), [21](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibMath.sol#L21-L21)

```solidity
File: contracts/signal/SignalService.sol

104:         for (uint256 i; i < hopProofs.length; ++i) {

120:             bool isFullProof = hop.accountProof.length > 0;

247:         if (topBlockId[_chainId][_kind] < _blockId) {

```
*GitHub*: [104](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L104-L104), [120](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L120-L120), [247](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L247-L247)

```solidity
File: contracts/team/TimelockTokenPool.sol

275:             if (_cliff > 0) revert INVALID_GRANT();

277:             if (_cliff > 0 && _cliff <= _start) revert INVALID_GRANT();

```
*GitHub*: [275](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L275-L275), [277](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L277-L277)

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol

40:          if (claimEnd > block.timestamp || claimEnd + withdrawalWindow < block.timestamp) {

40:          if (claimEnd > block.timestamp || claimEnd + withdrawalWindow < block.timestamp) {

114:         if (block.timestamp < claimEnd) return (balance, 0);

```
*GitHub*: [40](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L40-L40), [40](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L40-L40), [114](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L114-L114)

```solidity
File: contracts/team/airdrop/ERC721Airdrop.sol

59:          for (uint256 i; i < tokenIds.length; ++i) {

```
*GitHub*: [59](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59-L59)

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol

35:              merkleRoot == 0x0 || claimStart == 0 || claimEnd == 0 || claimStart > block.timestamp

36:                  || claimEnd < block.timestamp

```
*GitHub*: [35](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L35-L35), [36](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L36-L36)

```solidity
File: contracts/thirdparty/optimism/rlp/RLPReader.sol

38:              _in.length > 0,

74:          while (offset < _in.length) {

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
*GitHub*: [38](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L38-L38), [74](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L74-L74), [153](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L153-L153), [173](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L173-L173), [193](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L193-L193), [213](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L213-L213), [218](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L218-L218), [229](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L229-L229), [239](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L239-L239), [259](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L259-L259), [264](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L264-L264)

```solidity
File: contracts/thirdparty/optimism/rlp/RLPWriter.sol

14:          if (_in.length == 1 && uint8(_in[0]) < 128) {

33:          if (_len < 56) {

59:          for (; i < 32; i++) {

66:          for (uint256 j = 0; j < out_.length; j++) {

```
*GitHub*: [14](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L14-L14), [33](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L33-L33), [59](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L59-L59), [66](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66-L66)

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

77:          require(_key.length > 0, "MerkleTrie: empty key");

85:          for (uint256 i = 0; i < proof.length; i++) {

120:                         value_.length > 0,

173:                         value_.length > 0,

208:         for (uint256 i = 0; i < length;) {

221:         id_ = _node.length < 32 ? RLPReader.readRawBytes(_node) : RLPReader.readBytes(_node);

243:         uint256 max = (_a.length < _b.length) ? _a.length : _b.length;

244:         for (; shared_ < max && _a[shared_] == _b[shared_];) {

```
*GitHub*: [77](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L77-L77), [85](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85-L85), [120](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L120-L120), [173](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L173-L173), [208](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L208-L208), [221](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L221-L221), [243](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L243-L243), [244](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L244-L244)

```solidity
File: contracts/tokenvault/BaseNFTVault.sol

145:         if (_op.tokenIds.length > MAX_TOKEN_PER_TXN) {

```
*GitHub*: [145](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L145-L145)

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

47:          for (uint256 i; i < _op.amounts.length; ++i) {

251:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

269:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

```
*GitHub*: [47](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L47-L47), [251](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L251-L251), [269](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L269-L269)

```solidity
File: contracts/tokenvault/ERC721Vault.sol

34:          for (uint256 i; i < _op.tokenIds.length; ++i) {

170:             for (uint256 i; i < _tokenIds.length; ++i) {

175:             for (uint256 i; i < _tokenIds.length; ++i) {

197:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

210:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

```
*GitHub*: [34](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L34-L34), [170](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L170-L170), [175](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L175-L175), [197](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L197-L197), [210](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L210-L210)

```solidity
File: contracts/verifiers/SgxVerifier.sol

104:         for (uint256 i; i < _ids.length; ++i) {

210:         for (uint256 i; i < _instances.length; ++i) {

```
*GitHub*: [104](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L104-L104), [210](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210-L210)

</details>





### [G&#x2011;25] `require()`/`revert()` strings longer than 32 bytes cost extra gas
Each extra memory word of bytes past the original 32 [incurs an MSTORE](https://gist.github.com/hrkrshnn/ee8fabd532058307229d65dcd5836ddc#consider-having-short-revert-strings) which costs **3 gas**

*There are 31 instances of this issue:*

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

77            require(
78                localEnclaveReport.reserved3.length == 96 && localEnclaveReport.reserved4.length == 60
79                    && localEnclaveReport.reportData.length == 64,
80                "local QE report has wrong length"
81:           );

87            require(
88                v3Quote.v3AuthData.certification.certType == 5,
89                "certType must be 5: Concatenated PCK Cert Chain (PEM formatted)"
90:           );

```
*GitHub*: [77](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L77-L81), [87](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L87-L90)

```solidity
File: contracts/thirdparty/optimism/rlp/RLPReader.sol

37            require(
38                _in.length > 0,
39                "RLPReader: length of an RLP item must be greater than zero to be decodable"
40:           );

56            require(
57                itemType == RLPItemType.LIST_ITEM,
58                "RLPReader: decoded item type for list is not a list item"
59:           );

61            require(
62                listOffset + listLength == _in.length,
63                "RLPReader: list item has an invalid data remainder"
64:           );

112           require(
113               itemType == RLPItemType.DATA_ITEM,
114               "RLPReader: decoded item type for bytes is not a data item"
115:          );

117           require(
118               _in.length == itemOffset + itemLength,
119               "RLPReader: bytes value contains an invalid remainder"
120:          );

152           require(
153               _in.length > 0,
154               "RLPReader: length of an RLP item must be greater than zero to be decodable"
155:          );

172               require(
173                   _in.length > strLen,
174                   "RLPReader: length of content must be greater than string length (short string)"
175:              );

182               require(
183                   strLen != 1 || firstByteOfContent >= 0x80,
184                   "RLPReader: invalid prefix, single byte < 0x80 are not prefixed (short string)"
185:              );

192               require(
193                   _in.length > lenOfStrLen,
194                   "RLPReader: length of content must be > than length of string length (long string)"
195:              );

202               require(
203                   firstByteOfContent != 0x00,
204                   "RLPReader: length of content must not have any leading zeros (long string)"
205:              );

212               require(
213                   strLen > 55,
214                   "RLPReader: length of content must be greater than 55 bytes (long string)"
215:              );

217               require(
218                   _in.length > lenOfStrLen + strLen,
219                   "RLPReader: length of content must be greater than total length (long string)"
220:              );

228               require(
229                   _in.length > listLen,
230                   "RLPReader: length of content must be greater than list length (short list)"
231:              );

238               require(
239                   _in.length > lenOfListLen,
240                   "RLPReader: length of content must be > than length of list length (long list)"
241:              );

248               require(
249                   firstByteOfContent != 0x00,
250                   "RLPReader: length of content must not have any leading zeros (long list)"
251:              );

258               require(
259                   listLen > 55,
260                   "RLPReader: length of content must be greater than 55 bytes (long list)"
261:              );

263               require(
264                   _in.length > lenOfListLen + listLen,
265                   "RLPReader: length of content must be greater than total length (long list)"
266:              );

```
*GitHub*: [37](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L37-L40), [56](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L56-L59), [61](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L61-L64), [112](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L112-L115), [117](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L117-L120), [152](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L152-L155), [172](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L172-L175), [182](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L182-L185), [192](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L192-L195), [202](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L202-L205), [212](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L212-L215), [217](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L217-L220), [228](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L228-L231), [238](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L238-L241), [248](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L248-L251), [258](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L258-L261), [263](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L263-L266)

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

89:               require(currentKeyIndex <= key.length, "MerkleTrie: key index exceeds total key length");

99                    require(
100                       Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
101                       "MerkleTrie: invalid large internal hash"
102:                  );

105                   require(
106                       Bytes.equal(currentNode.encoded, currentNodeID),
107                       "MerkleTrie: invalid internal node hash"
108:                  );

119                       require(
120                           value_.length > 0,
121                           "MerkleTrie: value length must be greater than zero (branch)"
122:                      );

125                       require(
126                           i == proof.length - 1,
127                           "MerkleTrie: value node must be last node in proof (branch)"
128:                      );

150                   require(
151                       pathRemainder.length == sharedNibbleLength,
152                       "MerkleTrie: path remainder must share all nibbles with key"
153:                  );

162                       require(
163                           keyRemainder.length == sharedNibbleLength,
164                           "MerkleTrie: key remainder must be identical to path remainder"
165:                      );

172                       require(
173                           value_.length > 0,
174                           "MerkleTrie: value length must be greater than zero (leaf)"
175:                      );

178                       require(
179                           i == proof.length - 1,
180                           "MerkleTrie: value node must be last node in proof (leaf)"
181:                      );

191:                      revert("MerkleTrie: received a node with an unknown prefix");

194:                  revert("MerkleTrie: received an unparseable node");

198:          revert("MerkleTrie: ran out of proof elements");

```
*GitHub*: [89](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L89), [99](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L99-L102), [105](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L105-L108), [119](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L119-L122), [125](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L125-L128), [150](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L150-L153), [162](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L162-L165), [172](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L172-L175), [178](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L178-L181), [191](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L191), [194](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L194), [198](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L198)



### [G&#x2011;26] A `memory` array's `length` should not be looked up in every iteration of a `for`/`while`-loop
Caching the length of `memory` arrays changes each length lookup (i.e. on every iteration) from an `MLOAD` to a `DUP<N>` (**3 gas**), and gets rid of the extra `DUP<N>` needed to store the stack offset, saving **3 [gas](https://gist.github.com/IllIllI000/6f2891c6393fbbbd7dd83d62d839dc5e)**.

*There is one instance of this issue:*

```solidity
File: contracts/thirdparty/optimism/rlp/RLPReader.sol

74:          while (offset < _in.length) {

```
*GitHub*: [74](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L74-L74)



### [G&#x2011;27] Assembly: Check `msg.sender` using `xor` and the scratch space
See [this](https://code4rena.com/reports/2023-05-juicebox#g-06-use-assembly-to-validate-msgsender) prior finding for details on the conversion

*There are 22 instances of this issue:*

<details>
<summary>see instances</summary>


```solidity
File: contracts/L1/libs/LibProposing.sol

310:             if (proposerOne != address(0) && msg.sender != proposerOne) {

316:         return proposer == address(0) || msg.sender == proposer;

```
*GitHub*: [310](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L310-L310), [316](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L316-L316)

```solidity
File: contracts/L1/libs/LibProving.sol

416:         bool isAssignedPover = msg.sender == _blk.assignedProver;

```
*GitHub*: [416](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L416-L416)

```solidity
File: contracts/L2/TaikoL2.sol

123:         if (msg.sender != GOLDEN_TOUCH_ADDRESS) revert L2_INVALID_SENDER();

```
*GitHub*: [123](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L123-L123)

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

61:          require(msg.sender == owner, "onlyOwner");

```
*GitHub*: [61](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L61-L61)

```solidity
File: contracts/bridge/Bridge.sol

250:         if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) {

260:             if (_message.gasLimit == 0 && msg.sender != _message.destOwner) {

280:                 uint256 gasLimit = msg.sender == _message.destOwner ? gasleft() : _message.gasLimit;

294:             if (msg.sender == refundTo) {

322:             if (msg.sender != _message.destOwner) revert B_PERMISSION_DENIED();

```
*GitHub*: [250](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L250-L250), [260](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L260-L260), [280](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L280-L280), [294](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L294-L294), [322](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L322-L322)

```solidity
File: contracts/common/AddressResolver.sol

25:          if (msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();

```
*GitHub*: [25](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressResolver.sol#L25-L25)

```solidity
File: contracts/common/EssentialContract.sol

42:          if (msg.sender != owner() && msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();

42:          if (msg.sender != owner() && msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();

```
*GitHub*: [42](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L42-L42), [42](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L42-L42)

```solidity
File: contracts/libs/LibAddress.sol

78:          return msg.sender == tx.origin;

```
*GitHub*: [78](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibAddress.sol#L78-L78)

```solidity
File: contracts/tokenvault/BaseVault.sol

23:          if (msg.sender != resolve("bridge", false)) {

65:          if (ctx_.from != msg.sender) revert VAULT_PERMISSION_DENIED();

```
*GitHub*: [23](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseVault.sol#L23-L23), [65](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseVault.sol#L65-L65)

```solidity
File: contracts/tokenvault/BridgedERC20.sol

38:          if (msg.sender != owner() && msg.sender != snapshooter) {

38:          if (msg.sender != owner() && msg.sender != snapshooter) {

```
*GitHub*: [38](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L38-L38), [38](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L38-L38)

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol

61:          if (msg.sender == migratingAddress) {

64:          } else if (msg.sender != resolve("erc20_vault", true)) {

78:              if (msg.sender != _account) revert BB_PERMISSION_DENIED();

83:          } else if (msg.sender != resolve("erc20_vault", true)) {

```
*GitHub*: [61](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L61-L61), [64](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L64-L64), [78](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L78-L78), [83](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L83-L83)

</details>





### [G&#x2011;28] Avoid transferring amounts of zero in order to save gas
Skipping the external call when nothing will be transferred, will save at least **100 gas**

*There are 12 instances of this issue:*

<details>
<summary>see instances</summary>


```solidity
File: contracts/L1/TaikoToken.sol

62:          return super.transfer(_to, _amount);

80:          return super.transferFrom(_from, _to, _amount);

```
*GitHub*: [62](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoToken.sol#L62-L62), [80](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoToken.sol#L80-L80)

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

102:         tko.transferFrom(_blk.assignedProver, taikoL1Address, _blk.livenessBond);

114              IERC20(assignment.feeToken).safeTransferFrom(
115                  _meta.coinbase, _blk.assignedProver, proverFee
116:             );

```
*GitHub*: [102](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L102-L102), [114](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L114-L116)

```solidity
File: contracts/L1/libs/LibVerifying.sol

189:                 tko.transfer(ts.prover, bondToReturn);

```
*GitHub*: [189](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L189-L189)

```solidity
File: contracts/team/TimelockTokenPool.sol

219:         IERC20(taikoToken).transferFrom(sharedVault, _to, amountToWithdraw);

220:         IERC20(costToken).safeTransferFrom(_recipient, sharedVault, costToWithdraw);

```
*GitHub*: [219](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L219-L219), [220](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L220-L220)

```solidity
File: contracts/team/airdrop/ERC20Airdrop.sol

63:          IERC20(token).transferFrom(vault, user, amount);

```
*GitHub*: [63](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L63-L63)

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol

91:          IERC20(token).transferFrom(vault, user, amount);

```
*GitHub*: [91](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L91-L91)

```solidity
File: contracts/tokenvault/ERC20Vault.sol

330:             IERC20(token_).safeTransfer(_to, _amount);

379:             t.safeTransferFrom({ from: msg.sender, to: address(this), value: _amount });

```
*GitHub*: [330](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L330-L330), [379](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L379-L379)

```solidity
File: contracts/tokenvault/adapters/USDCAdapter.sol

48:          usdc.transferFrom(_from, address(this), _amount);

```
*GitHub*: [48](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L48-L48)

</details>





### [G&#x2011;29] Assembly: Checks for `address(0x0)` are more efficient in assembly
Using assembly allows you to [skip](https://gist.github.com/IllIllI000/d6b4b26af2fcd19827093a121e7e3f78) the clearing of the higher-order bits before performing the check for equality.

*There are 55 instances of this issue:*

<details>
<summary>see instances</summary>


```solidity
File: contracts/L1/hooks/AssignmentHook.sol

109:         if (assignment.feeToken == address(0)) {

120:         if (input.tip != 0 && block.coinbase != address(0)) {

```
*GitHub*: [109](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L109-L109), [120](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L120-L120)

```solidity
File: contracts/L1/libs/LibDepositing.sol

44:          address recipient_ = _recipient == address(0) ? msg.sender : _recipient;

```
*GitHub*: [44](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L44-L44)

```solidity
File: contracts/L1/libs/LibProposing.sol

81:          if (params.assignedProver == address(0)) {

85:          if (params.coinbase == address(0)) {

310:             if (proposerOne != address(0) && msg.sender != proposerOne) {

316:         return proposer == address(0) || msg.sender == proposer;

```
*GitHub*: [81](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L81-L81), [85](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L85-L85), [310](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L310-L310), [316](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L316-L316)

```solidity
File: contracts/L1/libs/LibProving.sol

163:             if (verifier != address(0)) {

224:                 assert(ts.validityBond == 0 && ts.contestBond == 0 && ts.contester == address(0));

239:                 if (ts.contester != address(0)) revert L1_ALREADY_CONTESTED();

363:         if (_ts.contester != address(0)) {

```
*GitHub*: [163](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L163-L163), [224](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L224-L224), [239](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L239-L239), [363](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L363-L363)

```solidity
File: contracts/L1/libs/LibVerifying.sol

145:                 if (ts.contester != address(0)) {

148:                     if (tierProvider == address(0)) {

```
*GitHub*: [145](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L145-L145), [148](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L148-L148)

```solidity
File: contracts/L1/provers/Guardians.sol

82:              if (guardian == address(0)) revert INVALID_GUARDIAN();

```
*GitHub*: [82](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L82-L82)

```solidity
File: contracts/L2/TaikoL2.sol

172:         if (_to == address(0)) revert L2_INVALID_PARAM();

173:         if (_token == address(0)) {

```
*GitHub*: [172](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L172-L172), [173](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L173-L173)

```solidity
File: contracts/bridge/Bridge.sol

124:         if (_message.srcOwner == address(0) || _message.destOwner == address(0)) {

124:         if (_message.srcOwner == address(0) || _message.destOwner == address(0)) {

270:                 _message.to == address(0) || _message.to == address(this)

291:                 _message.refundTo == address(0) ? _message.destOwner : _message.refundTo;

398:         enabled_ = destBridge_ != address(0);

```
*GitHub*: [124](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L124-L124), [124](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L124-L124), [270](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L270-L270), [291](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L291-L291), [398](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L398-L398)

```solidity
File: contracts/common/AddressResolver.sol

81:          if (addressManager == address(0)) revert RESOLVER_INVALID_MANAGER();

85:          if (!_allowZeroAddress && addr_ == address(0)) {

```
*GitHub*: [81](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressResolver.sol#L81-L81), [85](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressResolver.sol#L85-L85)

```solidity
File: contracts/common/EssentialContract.sol

105:         if (_addressManager == address(0)) revert ZERO_ADDR_MANAGER();

110:         _transferOwnership(_owner == address(0) ? msg.sender : _owner);

```
*GitHub*: [105](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L105-L105), [110](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L110-L110)

```solidity
File: contracts/libs/LibAddress.sol

24:          if (_to == address(0)) revert ETH_TRANSFER_FAILED();

```
*GitHub*: [24](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibAddress.sol#L24-L24)

```solidity
File: contracts/signal/SignalService.sol

36:          if (_app == address(0)) revert SS_INVALID_SENDER();

```
*GitHub*: [36](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L36-L36)

```solidity
File: contracts/team/TimelockTokenPool.sol

121:         if (_taikoToken == address(0)) revert INVALID_PARAM();

124:         if (_costToken == address(0)) revert INVALID_PARAM();

127:         if (_sharedVault == address(0)) revert INVALID_PARAM();

136:         if (_recipient == address(0)) revert INVALID_PARAM();

169:         if (_to == address(0)) revert INVALID_PARAM();

```
*GitHub*: [121](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L121-L121), [124](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L124-L124), [127](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L127-L127), [136](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L136-L136), [169](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L169-L169)

```solidity
File: contracts/tokenvault/BaseNFTVault.sol

149:         if (_op.token == address(0)) revert VAULT_INVALID_TOKEN();

```
*GitHub*: [149](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L149-L149)

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol

102:         return migratingAddress != address(0) && !migratingInbound;

```
*GitHub*: [102](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L102-L102)

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

64:              destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,

108:         if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

249:             if (bridgedToCanonical[_op.token].addr != address(0)) {

293:         if (btoken_ == address(0)) {

```
*GitHub*: [64](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L64-L64), [108](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L108-L108), [249](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L249-L249), [293](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L293-L293)

```solidity
File: contracts/tokenvault/ERC20Vault.sol

158:         if (_btokenNew == address(0) || bridgedToCanonical[_btokenNew].addr != address(0)) {

158:         if (_btokenNew == address(0) || bridgedToCanonical[_btokenNew].addr != address(0)) {

170:         if (btokenOld_ != address(0)) {

215:         if (_op.token == address(0)) revert VAULT_INVALID_TOKEN();

227:             destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,

267:         if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

358:         if (bridgedToCanonical[_token].addr != address(0)) {

397:         if (btoken == address(0)) {

```
*GitHub*: [158](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L158-L158), [158](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L158-L158), [170](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L170-L170), [215](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L215-L215), [227](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L227-L227), [267](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L267-L267), [358](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L358-L358), [397](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L397-L397)

```solidity
File: contracts/tokenvault/ERC721Vault.sol

50:              destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,

91:          if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

195:             if (bridgedToCanonical[_op.token].addr != address(0)) {

230:         if (btoken_ == address(0)) {

```
*GitHub*: [50](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L50-L50), [91](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L91-L91), [195](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L195-L195), [230](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L230-L230)

```solidity
File: contracts/tokenvault/LibBridgedToken.sol

21:              _srcToken == address(0) || _srcChainId == 0 || _srcChainId == block.chainid

```
*GitHub*: [21](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L21-L21)

```solidity
File: contracts/verifiers/SgxVerifier.sol

107:             if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();

124:         if (automataDcapAttestation == address(0)) {

215:             if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();

234:         if (instance == address(0)) return false;

```
*GitHub*: [107](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L107-L107), [124](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L124-L124), [215](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L215-L215), [234](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L234-L234)

</details>





### [G&#x2011;30] Consider merging consecutive loops over the same data
Merging the loops will save gas in the happy path, at the expense of the unhappy path

*There are 8 instances of this issue:*

```solidity
File: contracts/automata-attestation/utils/RsaVerify.sol

152              for (uint256 i; i < digestAlgoWithParamLen; ++i) {
153                  if (decipher[3 + paddingLen + i] != bytes1(sha256ExplicitNullParam[i])) {
154                      return false;
155                  }
156:             }

158              for (uint256 i; i < digestAlgoWithParamLen; ++i) {
159                  if (decipher[3 + paddingLen + i] != bytes1(sha256ImplicitNullParam[i])) {
160                      return false;
161                  }
162:             }

```
*GitHub*: [152](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L152-L152), [158](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L158-L158)

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

251                  for (uint256 i; i < _op.tokenIds.length; ++i) {
252                      BridgedERC1155(_op.token).burn(_user, _op.tokenIds[i], _op.amounts[i]);
253:                 }

269                  for (uint256 i; i < _op.tokenIds.length; ++i) {
270                      IERC1155(_op.token).safeTransferFrom({
271                          from: msg.sender,
272                          to: address(this),
273                          id: _op.tokenIds[i],
274                          amount: _op.amounts[i],
275                          data: ""
276                      });
277:                 }

```
*GitHub*: [251](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L251-L251), [269](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L269-L269)

```solidity
File: contracts/tokenvault/ERC721Vault.sol

170              for (uint256 i; i < _tokenIds.length; ++i) {
171                  IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);
172:             }

175              for (uint256 i; i < _tokenIds.length; ++i) {
176                  BridgedERC721(token_).mint(_to, _tokenIds[i]);
177:             }

197                  for (uint256 i; i < _op.tokenIds.length; ++i) {
198                      BridgedERC721(_op.token).burn(_user, _op.tokenIds[i]);
199:                 }

210                  for (uint256 i; i < _op.tokenIds.length; ++i) {
211                      t.safeTransferFrom(_user, address(this), _op.tokenIds[i]);
212:                 }

```
*GitHub*: [170](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L170-L170), [175](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L175-L175), [197](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L197-L197), [210](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L210-L210)



### [G&#x2011;31] Consider using `bytes32` rather than a `string`
Using the `bytes32` type for fixed-length strings is more efficient than having the EVM have to incur the overhead of string processing. Consider whether the value _needs_ to be a `string`. A good reason to keep it as a `string` would be if the variable is defined in an interface that this project does not own.

*There are 5 instances of this issue:*

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol

17:      string internal constant HEADER = "-----BEGIN CERTIFICATE-----";

18:      string internal constant FOOTER = "-----END CERTIFICATE-----";

22:      string internal constant PCK_COMMON_NAME = "Intel SGX PCK Certificate";

23:      string internal constant PLATFORM_ISSUER_NAME = "Intel SGX PCK Platform CA";

24:      string internal constant PROCESSOR_ISSUER_NAME = "Intel SGX PCK Processor CA";

```
*GitHub*: [17](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L17-L17), [18](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L18-L18), [22](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L22-L22), [23](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L23-L23), [24](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L24-L24)



### [G&#x2011;32] Consider using `ERC721A` over `ERC721`
[ERC721A](https://www.azuki.com/erc721a) is much more gas-efficient for minting multiple NFTs in the same transaction

*There is one instance of this issue:*

```solidity
File: contracts/tokenvault/BridgedERC721.sol

12   contract BridgedERC721 is EssentialContract, ERC721Upgradeable {
13:      /// @notice Address of the source token contract.

```
*GitHub*: [12](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L12-L13)



### [G&#x2011;33] Consider using `solady`'s token contracts to save gas
They're written using heavily-optimized assembly, and will your users a lot of gas

*There are 11 instances of this issue:*

```solidity
File: contracts/L1/TaikoToken.sol

/// @audit ERC20VotesUpgradeable
/// @audit ERC20PermitUpgradeable
/// @audit ERC20SnapshotUpgradeable
/// @audit ERC20Upgradeable
15:  contract TaikoToken is EssentialContract, ERC20SnapshotUpgradeable, ERC20VotesUpgradeable {

```
*GitHub*: [15](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoToken.sol#L15-L15), [15](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoToken.sol#L15-L15), [15](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoToken.sol#L15-L15), [15](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoToken.sol#L15-L15)

```solidity
File: contracts/tokenvault/BridgedERC1155.sol

/// @audit ERC1155Upgradeable
14   contract BridgedERC1155 is EssentialContract, IERC1155MetadataURIUpgradeable, ERC1155Upgradeable {
15:      /// @notice Address of the source token contract.

```
*GitHub*: [14](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L14-L15)

```solidity
File: contracts/tokenvault/BridgedERC20.sol

/// @audit ERC20VotesUpgradeable
/// @audit ERC20PermitUpgradeable
/// @audit ERC20SnapshotUpgradeable
/// @audit ERC20Upgradeable
15   contract BridgedERC20 is
16       BridgedERC20Base,
17       IERC20MetadataUpgradeable,
18       ERC20SnapshotUpgradeable,
19       ERC20VotesUpgradeable
20   {
21:      /// @dev Slot 1.

```
*GitHub*: [15](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L15-L21), [15](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L15-L21), [15](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L15-L21), [15](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L15-L21)

```solidity
File: contracts/tokenvault/BridgedERC721.sol

/// @audit ERC721Upgradeable
12   contract BridgedERC721 is EssentialContract, ERC721Upgradeable {
13:      /// @notice Address of the source token contract.

```
*GitHub*: [12](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L12-L13)

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

/// @audit ERC1155ReceiverUpgradeable
29:  contract ERC1155Vault is BaseNFTVault, ERC1155ReceiverUpgradeable {

```
*GitHub*: [29](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L29-L29)



### [G&#x2011;34] Consider using solady's `FixedPointMathLib`
Saves gas, and works to avoid unnecessary [overflows](https://github.com/Vectorized/solady/blob/6cce088e69d6e46671f2f622318102bd5db77a65/src/utils/FixedPointMathLib.sol#L267).

*There are 3 instances of this issue:*

```solidity
File: contracts/thirdparty/optimism/rlp/RLPWriter.sol

47:                  out_[i] = bytes1(uint8((_len / (256 ** (lenLen - i))) % 256));

```
*GitHub*: [47](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L47-L47)

```solidity
File: contracts/thirdparty/solmate/LibFixedPointMath.sol

33:              x = (x << 78) / 5 ** 18;

39:              int256 k = ((x << 96) / 54_916_777_467_707_473_351_141_471_128 + 2 ** 95) >> 96;

```
*GitHub*: [33](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L33-L33), [39](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L39-L39)



### [G&#x2011;35] Counting down when iterating, saves gas
Counting down saves **6 [gas](https://gist.github.com/IllIllI000/764476152f228f8a25a41f1ca14003f5)** _per loop_, since checks for zero are more efficient than checks against any other value

*There are 46 instances of this issue:*

<details>
<summary>see instances</summary>


```solidity
File: contracts/L1/hooks/AssignmentHook.sol

172:         for (uint256 i; i < _tierFees.length; ++i) {

```
*GitHub*: [172](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L172-L172)

```solidity
File: contracts/L1/libs/LibProposing.sol

244:             for (uint256 i; i < params.hookCalls.length; ++i) {

```
*GitHub*: [244](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L244-L244)

```solidity
File: contracts/L1/provers/Guardians.sol

74:          for (uint256 i; i < guardians.length; ++i) {

80:          for (uint256 i = 0; i < _newGuardians.length; ++i) {

133:             for (uint256 i; i < guardiansLength; ++i) {

```
*GitHub*: [74](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L74-L74), [80](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L80-L80), [133](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L133-L133)

```solidity
File: contracts/L2/TaikoL2.sol

234:             for (uint256 i; i < 255 && _blockId >= i + 1; ++i) {

```
*GitHub*: [234](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L234-L234)

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

80:          for (uint256 i; i < serialNumBatch.length; ++i) {

95:          for (uint256 i; i < serialNumBatch.length; ++i) {

191:         for (uint256 i; i < enclaveId.tcbLevels.length; ++i) {

214:         for (uint256 i; i < tcb.tcbLevels.length; ++i) {

240:         for (uint256 i; i < CPUSVN_LENGTH; ++i) {

259:         for (uint256 i; i < n; ++i) {

420:             for (uint256 i; i < 3; ++i) {

```
*GitHub*: [80](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L80-L80), [95](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L95-L95), [191](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L191-L191), [214](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L214-L214), [240](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L240-L240), [259](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L259-L259), [420](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L420-L420)

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol

54:          for (uint256 i; i < size; ++i) {

244:         for (uint256 i; i < split.length; ++i) {

354:         for (uint256 i; i < SGX_TCB_CPUSVN_SIZE + 1; ++i) {

```
*GitHub*: [54](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L54-L54), [244](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L244-L244), [354](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L354-L354)

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

153:         for (uint256 i; i < encoded.length; ++i) {

281:         for (uint256 i; i < 3; ++i) {

```
*GitHub*: [153](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L153-L153), [281](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L281-L281)

```solidity
File: contracts/automata-attestation/utils/BytesUtils.sol

80:          for (uint256 idx = 0; idx < shortest; idx += 32) {

333:         for (uint256 i; i < len; ++i) {

```
*GitHub*: [80](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L80-L80), [333](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L333-L333)

```solidity
File: contracts/automata-attestation/utils/RsaVerify.sol

140:         for (uint256 i = 2; i < 2 + paddingLen; ++i) {

152:             for (uint256 i; i < digestAlgoWithParamLen; ++i) {

158:             for (uint256 i; i < digestAlgoWithParamLen; ++i) {

174:         for (uint256 i; i < _sha256.length; ++i) {

273:         for (uint256 i = 2; i < 2 + paddingLen; ++i) {

283:         for (uint256 i; i < sha1Prefix.length; ++i) {

290:         for (uint256 i; i < _sha1.length; ++i) {

```
*GitHub*: [140](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L140-L140), [152](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L152-L152), [158](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L158-L158), [174](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L174-L174), [273](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L273-L273), [283](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L283-L283), [290](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L290-L290)

```solidity
File: contracts/automata-attestation/utils/X509DateUtils.sol

48:          for (uint16 i = 1970; i < year; ++i) {

59:          for (uint8 i = 1; i < month; ++i) {

```
*GitHub*: [48](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L48-L48), [59](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L59-L59)

```solidity
File: contracts/bridge/Bridge.sol

90:          for (uint256 i; i < _msgHashes.length; ++i) {

```
*GitHub*: [90](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L90-L90)

```solidity
File: contracts/signal/SignalService.sol

104:         for (uint256 i; i < hopProofs.length; ++i) {

```
*GitHub*: [104](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L104-L104)

```solidity
File: contracts/team/airdrop/ERC721Airdrop.sol

59:          for (uint256 i; i < tokenIds.length; ++i) {

```
*GitHub*: [59](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59-L59)

```solidity
File: contracts/thirdparty/optimism/rlp/RLPWriter.sol

46:              for (i = 1; i <= lenLen; i++) {

59:          for (; i < 32; i++) {

66:          for (uint256 j = 0; j < out_.length; j++) {

```
*GitHub*: [46](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L46-L46), [59](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L59-L59), [66](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66-L66)

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

85:          for (uint256 i = 0; i < proof.length; i++) {

```
*GitHub*: [85](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85-L85)

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

47:          for (uint256 i; i < _op.amounts.length; ++i) {

251:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

269:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

```
*GitHub*: [47](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L47-L47), [251](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L251-L251), [269](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L269-L269)

```solidity
File: contracts/tokenvault/ERC721Vault.sol

34:          for (uint256 i; i < _op.tokenIds.length; ++i) {

170:             for (uint256 i; i < _tokenIds.length; ++i) {

175:             for (uint256 i; i < _tokenIds.length; ++i) {

197:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

210:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

```
*GitHub*: [34](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L34-L34), [170](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L170-L170), [175](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L175-L175), [197](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L197-L197), [210](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L210-L210)

```solidity
File: contracts/verifiers/SgxVerifier.sol

104:         for (uint256 i; i < _ids.length; ++i) {

210:         for (uint256 i; i < _instances.length; ++i) {

```
*GitHub*: [104](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L104-L104), [210](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210-L210)

</details>





### [G&#x2011;36] Duplicated `require()`/`revert()` checks should be refactored to a modifier or function to save deployment gas
This will cost more runtime gas, but will reduce deployment gas when the function is (optionally called via a modifier) called more than once as is the case for the examples below. Most projects do not make this trade-off, but it's available nonetheless.

*There are 6 instances of this issue:*

```solidity
File: contracts/automata-attestation/utils/Asn1Decode.sol

142:         require(der[ptr.ixs()] == 0x02, "Not type INTEGER");

143:         require(der[ptr.ixf()] & 0x80 == 0, "Not positive");

155:         require(der[ptr.ixs()] == 0x02, "Not type INTEGER");

156:         require(der[ptr.ixf()] & 0x80 == 0, "Not positive");

```
*GitHub*: [142](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L142-L142), [143](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L143-L143), [155](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L155-L155), [156](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L156-L156)

```solidity
File: contracts/automata-attestation/utils/SigVerifyLib.sol

50:              revert("Unsupported algorithm");

75:              revert("Unsupported algorithm");

```
*GitHub*: [50](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L50-L50), [75](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L75-L75)



### [G&#x2011;37] Emitting constants wastes gas
Every event parameter costs `Glogdata` (**8 gas**) per byte. You can avoid this extra cost, in cases where you're emitting a constant, by creating a second version of the event, which doesn't have the parameter (and have users look to the contract's variables for its value instead), and using the new event in the cases shown below.

*There are 5 instances of this issue:*

```solidity
File: contracts/L1/libs/LibProving.sol

230                  emit TransitionProved({
231                      blockId: blk.blockId,
232                      tran: _tran,
233                      prover: msg.sender,
234                      validityBond: 0,
235                      tier: _proof.tier
236:                 });

```
*GitHub*: [230](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L230-L236)

```solidity
File: contracts/L1/libs/LibVerifying.sol

73           emit BlockVerified({
74               blockId: 0,
75               assignedProver: address(0),
76               prover: address(0),
77               blockHash: _genesisBlockHash,
78               stateRoot: 0,
79               tier: 0,
80               contestations: 0
81:          });

```
*GitHub*: [73](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L73-L81)

```solidity
File: contracts/bridge/Bridge.sol

210:             emit MessageReceived(msgHash, _message, true);

303:             emit MessageReceived(msgHash, _message, false);

```
*GitHub*: [210](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L210-L210), [303](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L303-L303)

```solidity
File: contracts/verifiers/SgxVerifier.sol

220:             emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);

```
*GitHub*: [220](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220-L220)



### [G&#x2011;38] Initializers can be marked `payable`
Payable functions cost less gas to execute, since the compiler does not have to add extra checks to ensure that a payment wasn't provided. An initializer can safely be marked as payable, since only the deployer would be able to pass funds, and the project itself would not pass any funds.

*There are 24 instances of this issue:*

<details>
<summary>see instances</summary>


```solidity
File: contracts/L1/TaikoL1.sol

42       function init(
43           address _owner,
44           address _addressManager,
45           bytes32 _genesisBlockHash
46       )
47           external
48           initializer
49:      {

```
*GitHub*: [42](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L42-L49)

```solidity
File: contracts/L1/TaikoToken.sol

25       function init(
26           address _owner,
27           string calldata _name,
28           string calldata _symbol,
29           address _recipient
30       )
31           public
32           initializer
33:      {

```
*GitHub*: [25](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoToken.sol#L25-L33)

```solidity
File: contracts/L1/gov/TaikoGovernor.sol

31       function init(
32           address _owner,
33           IVotesUpgradeable _token,
34           TimelockControllerUpgradeable _timelock
35       )
36           external
37           initializer
38:      {

```
*GitHub*: [31](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L31-L38)

```solidity
File: contracts/L1/gov/TaikoTimelockController.sol

15:      function init(address _owner, uint256 _minDelay) external initializer {

```
*GitHub*: [15](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L15-L15)

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

57:      function init(address _owner, address _addressManager) external initializer {

```
*GitHub*: [57](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L57-L57)

```solidity
File: contracts/L1/libs/LibVerifying.sol

47       function init(
48           TaikoData.State storage _state,
49           TaikoData.Config memory _config,
50           bytes32 _genesisBlockHash
51       )
52           external
53:      {

```
*GitHub*: [47](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L47-L53)

```solidity
File: contracts/L1/provers/GuardianProver.sol

25:      function init(address _owner, address _addressManager) external initializer {

```
*GitHub*: [25](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/GuardianProver.sol#L25-L25)

```solidity
File: contracts/L1/tiers/DevnetTierProvider.sol

15:      function init(address _owner) external initializer {

```
*GitHub*: [15](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L15-L15)

```solidity
File: contracts/L1/tiers/MainnetTierProvider.sol

15:      function init(address _owner) external initializer {

```
*GitHub*: [15](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L15-L15)

```solidity
File: contracts/L2/TaikoL2.sol

71       function init(
72           address _owner,
73           address _addressManager,
74           uint64 _l1ChainId,
75           uint64 _gasExcess
76       )
77           external
78           initializer
79:      {

```
*GitHub*: [71](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L71-L79)

```solidity
File: contracts/bridge/Bridge.sol

75:      function init(address _owner, address _addressManager) external initializer {

```
*GitHub*: [75](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L75-L75)

```solidity
File: contracts/common/AddressManager.sol

30:      function init(address _owner) external initializer {

```
*GitHub*: [30](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressManager.sol#L30-L30)

```solidity
File: contracts/signal/SignalService.sol

48:      function init(address _owner, address _addressManager) external initializer {

```
*GitHub*: [48](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L48-L48)

```solidity
File: contracts/team/TimelockTokenPool.sol

111      function init(
112          address _owner,
113          address _taikoToken,
114          address _costToken,
115          address _sharedVault
116      )
117          external
118          initializer
119:     {

```
*GitHub*: [111](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L111-L119)

```solidity
File: contracts/team/airdrop/ERC20Airdrop.sol

27       function init(
28           address _owner,
29           uint64 _claimStart,
30           uint64 _claimEnd,
31           bytes32 _merkleRoot,
32           address _token,
33           address _vault
34       )
35           external
36           initializer
37:      {

```
*GitHub*: [27](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L27-L37)

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol

54       function init(
55           address _owner,
56           uint64 _claimStart,
57           uint64 _claimEnd,
58           bytes32 _merkleRoot,
59           address _token,
60           address _vault,
61           uint64 _withdrawalWindow
62       )
63           external
64           initializer
65:      {

```
*GitHub*: [54](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L54-L65)

```solidity
File: contracts/team/airdrop/ERC721Airdrop.sol

25       function init(
26           address _owner,
27           uint64 _claimStart,
28           uint64 _claimEnd,
29           bytes32 _merkleRoot,
30           address _token,
31           address _vault
32       )
33           external
34           initializer
35:      {

```
*GitHub*: [25](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L25-L35)

```solidity
File: contracts/tokenvault/BaseVault.sol

32:      function init(address _owner, address _addressManager) external initializer {

```
*GitHub*: [32](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseVault.sol#L32-L32)

```solidity
File: contracts/tokenvault/BridgedERC1155.sol

38       function init(
39           address _owner,
40           address _addressManager,
41           address _srcToken,
42           uint256 _srcChainId,
43           string memory _symbol,
44           string memory _name
45       )
46           external
47           initializer
48:      {

```
*GitHub*: [38](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L38-L48)

```solidity
File: contracts/tokenvault/BridgedERC20.sol

52       function init(
53           address _owner,
54           address _addressManager,
55           address _srcToken,
56           uint256 _srcChainId,
57           uint8 _decimals,
58           string memory _symbol,
59           string memory _name
60       )
61           external
62           initializer
63:      {

```
*GitHub*: [52](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L52-L63)

```solidity
File: contracts/tokenvault/BridgedERC721.sol

31       function init(
32           address _owner,
33           address _addressManager,
34           address _srcToken,
35           uint256 _srcChainId,
36           string memory _symbol,
37           string memory _name
38       )
39           external
40           initializer
41:      {

```
*GitHub*: [31](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L31-L41)

```solidity
File: contracts/tokenvault/adapters/USDCAdapter.sol

38:      function init(address _owner, address _addressManager, IUSDC _usdc) external initializer {

```
*GitHub*: [38](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L38-L38)

```solidity
File: contracts/verifiers/GuardianVerifier.sol

18:      function init(address _owner, address _addressManager) external initializer {

```
*GitHub*: [18](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L18-L18)

```solidity
File: contracts/verifiers/SgxVerifier.sol

83:      function init(address _owner, address _addressManager) external initializer {

```
*GitHub*: [83](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L83-L83)

</details>





### [G&#x2011;39] Inverting the condition of an `if`-`else`-statement wastes gas
Flipping the `true` and `false` blocks instead saves ***[3 gas](https://gist.github.com/IllIllI000/44da6fbe9d12b9ab21af82f14add56b9)***

*There are 2 instances of this issue:*

```solidity
File: contracts/bridge/Bridge.sol

209           } else if (!isMessageProven) {
210               emit MessageReceived(msgHash, _message, true);
211           } else {
212               revert B_INVOCATION_TOO_EARLY();
213:          }

302           } else if (!isMessageProven) {
303               emit MessageReceived(msgHash, _message, false);
304           } else {
305               revert B_INVOCATION_TOO_EARLY();
306:          }

```
*GitHub*: [209](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L209-L213), [302](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L302-L306)



### [G&#x2011;40] Memory-safe annotation missing
Use `assembly ("memory-safe") { ... }` for the assembly blocks below since they dont't read or modify memory, and therefore are [memory-safe](https://docs.soliditylang.org/en/latest/assembly.html#memory-safety). This will help the optimizer to create more optimal gas-efficient code. Use the comment variant if prior to Solidity version 0.8.13

*There are 24 instances of this issue:*

<details>
<summary>see instances</summary>


```solidity
File: contracts/L2/TaikoL2.sol

241  
242          assembly {
243              publicInputHashOld := keccak256(inputs, 8192 /*mul(256, 32)*/ )
244:         }

246          inputs[_blockId % 255] = blockhash(_blockId);
247          assembly {
248              publicInputHashNew := keccak256(inputs, 8192 /*mul(256, 32)*/ )
249:         }

```
*GitHub*: [241](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L241-L244), [246](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L246-L249)

```solidity
File: contracts/automata-attestation/utils/BytesUtils.sol

25           require(offset + len <= self.length, "invalid offset");
26           assembly {
27               ret := keccak256(add(add(self, 32), offset), len)
28:          }

82               uint256 b;
83               assembly {
84                   a := mload(selfptr)
85                   b := mload(otherptr)
86:              }

199          require(idx + 2 <= self.length, "invalid idx");
200          assembly {
201              ret := and(mload(add(add(self, 2), idx)), 0xFFFF)
202:         }

212          require(idx + 4 <= self.length, "unexpected idx");
213          assembly {
214              ret := and(mload(add(add(self, 4), idx)), 0xFFFFFFFF)
215:         }

225          require(idx + 32 <= self.length, "unexpected idx");
226          assembly {
227              ret := mload(add(add(self, 32), idx))
228:         }

238          require(idx + 20 <= self.length, "unexpected idx");
239          assembly {
240              ret :=
241                  and(
242                      mload(add(add(self, 32), idx)),
243                      0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF000000000000000000000000
244                  )
245:         }

265          require(idx + len <= self.length, "unexpected idx");
266          assembly {
267              let mask := not(sub(exp(256, sub(32, len)), 1))
268              ret := and(mload(add(add(self, 32), idx)), mask)
269:         }

```
*GitHub*: [25](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L25-L28), [82](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L82-L86), [199](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L199-L202), [212](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L212-L215), [225](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L225-L228), [238](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L238-L245), [265](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L265-L269)

```solidity
File: contracts/automata-attestation/utils/RsaVerify.sol

98           bytes memory decipher = new bytes(decipherlen);
99           assembly {
100              pop(
101                  staticcall(
102                      sub(gas(), 2000),
103                      5,
104                      add(input, 0x20),
105                      inputlen,
106                      add(decipher, 0x20),
107                      decipherlen
108                  )
109              )
110:         }

246          bytes memory decipher = new bytes(decipherlen);
247          assembly {
248              pop(
249                  staticcall(
250                      sub(gas(), 2000),
251                      5,
252                      add(input, 0x20),
253                      inputlen,
254                      add(decipher, 0x20),
255                      decipherlen
256                  )
257              )
258:         }

```
*GitHub*: [98](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L98-L110), [246](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L246-L258)

```solidity
File: contracts/automata-attestation/utils/SHA1.sol

11       function sha1(bytes memory data) internal pure returns (bytes20 ret) {
12           assembly {
13               // Get a safe scratch location
14               let scratch := mload(0x40)
15   
16               // Get the data length, and point data at the first byte
17               let len := mload(data)
18               data := add(data, 32)
19   
20               // Find the length after padding
21               let totallen := add(and(add(len, 1), 0xFFFFFFFFFFFFFFC0), 64)
22               switch lt(sub(totallen, len), 9)
23               case 1 { totallen := add(totallen, 64) }
24   
25               let h := 0x6745230100EFCDAB890098BADCFE001032547600C3D2E1F0
26   
27               function readword(ptr, off, count) -> result {
28                   result := 0
29                   if lt(off, count) {
30                       result := mload(add(ptr, off))
31                       count := sub(count, off)
32                       if lt(count, 32) {
33                           let mask := not(sub(exp(256, sub(32, count)), 1))
34                           result := and(result, mask)
35                       }
36                   }
37               }
38   
39               for { let i := 0 } lt(i, totallen) { i := add(i, 64) } {
40                   mstore(scratch, readword(data, i, len))
41                   mstore(add(scratch, 32), readword(data, add(i, 32), len))
42   
43                   // If we loaded the last byte, store the terminator byte
44                   switch lt(sub(len, i), 64)
45                   case 1 { mstore8(add(scratch, sub(len, i)), 0x80) }
46   
47                   // If this is the last block, store the length
48                   switch eq(i, sub(totallen, 64))
49                   case 1 { mstore(add(scratch, 32), or(mload(add(scratch, 32)), mul(len, 8))) }
50   
51                   // Expand the 16 32-bit words into 80
52                   for { let j := 64 } lt(j, 128) { j := add(j, 12) } {
53                       let temp :=
54                           xor(
55                               xor(mload(add(scratch, sub(j, 12))), mload(add(scratch, sub(j, 32)))),
56                               xor(mload(add(scratch, sub(j, 56))), mload(add(scratch, sub(j, 64))))
57                           )
58                       temp :=
59                           or(
60                               and(
61                                   mul(temp, 2),
62                                   0xFFFFFFFEFFFFFFFEFFFFFFFEFFFFFFFEFFFFFFFEFFFFFFFEFFFFFFFEFFFFFFFE
63                               ),
64                               and(
65                                   div(temp, 0x80000000),
66                                   0x0000000100000001000000010000000100000001000000010000000100000001
67                               )
68                           )
69                       mstore(add(scratch, j), temp)
70                   }
71                   for { let j := 128 } lt(j, 320) { j := add(j, 24) } {
72                       let temp :=
73                           xor(
74                               xor(mload(add(scratch, sub(j, 24))), mload(add(scratch, sub(j, 64)))),
75                               xor(mload(add(scratch, sub(j, 112))), mload(add(scratch, sub(j, 128))))
76                           )
77                       temp :=
78                           or(
79                               and(
80                                   mul(temp, 4),
81                                   0xFFFFFFFCFFFFFFFCFFFFFFFCFFFFFFFCFFFFFFFCFFFFFFFCFFFFFFFCFFFFFFFC
82                               ),
83                               and(
84                                   div(temp, 0x40000000),
85                                   0x0000000300000003000000030000000300000003000000030000000300000003
86                               )
87                           )
88                       mstore(add(scratch, j), temp)
89                   }
90   
91                   let x := h
92                   let f := 0
93                   let k := 0
94                   for { let j := 0 } lt(j, 80) { j := add(j, 1) } {
95                       switch div(j, 20)
96                       case 0 {
97                           // f = d xor (b and (c xor d))
98                           f := xor(div(x, 0x100000000000000000000), div(x, 0x10000000000))
99                           f := and(div(x, 0x1000000000000000000000000000000), f)
100                          f := xor(div(x, 0x10000000000), f)
101                          k := 0x5A827999
102                      }
103                      case 1 {
104                          // f = b xor c xor d
105                          f :=
106                              xor(
107                                  div(x, 0x1000000000000000000000000000000),
108                                  div(x, 0x100000000000000000000)
109                              )
110                          f := xor(div(x, 0x10000000000), f)
111                          k := 0x6ED9EBA1
112                      }
113                      case 2 {
114                          // f = (b and c) or (d and (b or c))
115                          f :=
116                              or(
117                                  div(x, 0x1000000000000000000000000000000),
118                                  div(x, 0x100000000000000000000)
119                              )
120                          f := and(div(x, 0x10000000000), f)
121                          f :=
122                              or(
123                                  and(
124                                      div(x, 0x1000000000000000000000000000000),
125                                      div(x, 0x100000000000000000000)
126                                  ),
127                                  f
128                              )
129                          k := 0x8F1BBCDC
130                      }
131                      case 3 {
132                          // f = b xor c xor d
133                          f :=
134                              xor(
135                                  div(x, 0x1000000000000000000000000000000),
136                                  div(x, 0x100000000000000000000)
137                              )
138                          f := xor(div(x, 0x10000000000), f)
139                          k := 0xCA62C1D6
140                      }
141                      // temp = (a leftrotate 5) + f + e + k + w[i]
142                      let temp := and(div(x, 0x80000000000000000000000000000000000000000000000), 0x1F)
143                      temp :=
144                          or(and(div(x, 0x800000000000000000000000000000000000000), 0xFFFFFFE0), temp)
145                      temp := add(f, temp)
146                      temp := add(and(x, 0xFFFFFFFF), temp)
147                      temp := add(k, temp)
148                      temp :=
149                          add(
150                              div(
151                                  mload(add(scratch, mul(j, 4))),
152                                  0x100000000000000000000000000000000000000000000000000000000
153                              ),
154                              temp
155                          )
156                      x :=
157                          or(
158                              div(x, 0x10000000000),
159                              mul(temp, 0x10000000000000000000000000000000000000000)
160                          )
161                      x :=
162                          or(
163                              and(x, 0xFFFFFFFF00FFFFFFFF000000000000FFFFFFFF00FFFFFFFF),
164                              mul(
165                                  or(
166                                      and(div(x, 0x4000000000000), 0xC0000000),
167                                      and(div(x, 0x400000000000000000000), 0x3FFFFFFF)
168                                  ),
169                                  0x100000000000000000000
170                              )
171                          )
172                  }
173  
174                  h := and(add(h, x), 0xFFFFFFFF00FFFFFFFF00FFFFFFFF00FFFFFFFF00FFFFFFFF)
175              }
176              ret :=
177                  mul(
178                      or(
179                          or(
180                              or(
181                                  or(
182                                      and(div(h, 0x100000000), 0xFFFFFFFF00000000000000000000000000000000),
183                                      and(div(h, 0x1000000), 0xFFFFFFFF000000000000000000000000)
184                                  ),
185                                  and(div(h, 0x10000), 0xFFFFFFFF0000000000000000)
186                              ),
187                              and(div(h, 0x100), 0xFFFFFFFF00000000)
188                          ),
189                          and(h, 0xFFFFFFFF)
190                      ),
191                      0x1000000000000000000000000
192                  )
193:         }

```
*GitHub*: [11](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SHA1.sol#L11-L193)

```solidity
File: contracts/libs/Lib4844.sol

52           bytes32 second;
53           assembly {
54               first := mload(add(ret, 32))
55               second := mload(add(ret, 64))
56:          }

```
*GitHub*: [52](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/Lib4844.sol#L52-L56)

```solidity
File: contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol

42           // returned by a malicious contract
43           assembly {
44               _success :=
45                   call(
46                       _gas, // gas
47                       _target, // recipient
48                       _value, // ether value
49                       add(_calldata, 0x20), // inloc
50                       mload(_calldata), // inlen
51                       0, // outloc
52                       0 // outlen
53                   )
54               // limit our copy to 256 bytes
55               _toCopy := returndatasize()
56               if gt(_toCopy, _maxCopy) { _toCopy := _maxCopy }
57               // Store the length of the copied bytes
58               mstore(_returnData, _toCopy)
59               // copy the bytes from returndata[0:_toCopy]
60               returndatacopy(add(_returnData, 0x20), 0, _toCopy)
61:          }

```
*GitHub*: [42](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L42-L61)

```solidity
File: contracts/thirdparty/optimism/Bytes.sol

31   
32           assembly {
33               switch iszero(_length)
34               case 0 {
35                   // Get a location of some free memory and store it in tempBytes as
36                   // Solidity does for memory variables.
37                   tempBytes := mload(0x40)
38   
39                   // The first word of the slice result is potentially a partial
40                   // word read from the original array. To read it, we calculate
41                   // the length of that partial word and start copying that many
42                   // bytes into the array. The first word we copy will start with
43                   // data we don't care about, but the last `lengthmod` bytes will
44                   // land at the beginning of the contents of the new array. When
45                   // we're done copying, we overwrite the full first word with
46                   // the actual length of the slice.
47                   let lengthmod := and(_length, 31)
48   
49                   // The multiplication in the next line is necessary
50                   // because when slicing multiples of 32 bytes (lengthmod == 0)
51                   // the following copy loop was copying the origin's length
52                   // and then ending prematurely not copying everything it should.
53                   let mc := add(add(tempBytes, lengthmod), mul(0x20, iszero(lengthmod)))
54                   let end := add(mc, _length)
55   
56                   for {
57                       // The multiplication in the next line has the same exact purpose
58                       // as the one above.
59                       let cc := add(add(add(_bytes, lengthmod), mul(0x20, iszero(lengthmod))), _start)
60                   } lt(mc, end) {
61                       mc := add(mc, 0x20)
62                       cc := add(cc, 0x20)
63                   } { mstore(mc, mload(cc)) }
64   
65                   mstore(tempBytes, _length)
66   
67                   //update free-memory pointer
68                   //allocating the array padded to 32 bytes like the compiler does now
69                   mstore(0x40, and(add(mc, 31), not(31)))
70               }
71               //if we want a zero-length slice let's just return a zero-length array
72               default {
73                   tempBytes := mload(0x40)
74   
75                   //zero out the 32 bytes slice we are about to return
76                   //we need to do it because Solidity does not garbage collect
77                   mstore(tempBytes, 0)
78   
79                   mstore(0x40, add(tempBytes, 0x20))
80               }
81:          }

103          bytes memory _nibbles;
104          assembly {
105              // Grab a free memory offset for the new array
106              _nibbles := mload(0x40)
107  
108              // Load the length of the passed bytes array from memory
109              let bytesLength := mload(_bytes)
110  
111              // Calculate the length of the new nibble array
112              // This is the length of the input array times 2
113              let nibblesLength := shl(0x01, bytesLength)
114  
115              // Update the free memory pointer to allocate memory for the new array.
116              // To do this, we add the length of the new array + 32 bytes for the array length
117              // rounded up to the nearest 32 byte boundary to the current free memory pointer.
118              mstore(0x40, add(_nibbles, and(not(0x1F), add(nibblesLength, 0x3F))))
119  
120              // Store the length of the new array in memory
121              mstore(_nibbles, nibblesLength)
122  
123              // Store the memory offset of the _bytes array's contents on the stack
124              let bytesStart := add(_bytes, 0x20)
125  
126              // Store the memory offset of the nibbles array's contents on the stack
127              let nibblesStart := add(_nibbles, 0x20)
128  
129              // Loop through each byte in the input array
130              for { let i := 0x00 } lt(i, bytesLength) { i := add(i, 0x01) } {
131                  // Get the starting offset of the next 2 bytes in the nibbles array
132                  let offset := add(nibblesStart, shl(0x01, i))
133                  // Load the byte at the current index within the `_bytes` array
134                  let b := byte(0x00, mload(add(bytesStart, i)))
135  
136                  // Pull out the first nibble and store it in the new array
137                  mstore8(offset, shr(0x04, b))
138                  // Pull out the second nibble and store it in the new array
139                  mstore8(add(offset, 0x01), and(b, 0x0F))
140              }
141:         }

```
*GitHub*: [31](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L31-L81), [103](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L103-L141)

```solidity
File: contracts/thirdparty/optimism/rlp/RLPReader.sol

93           // Decrease the array size to match the actual item count.
94           assembly {
95               mstore(out_, itemCount)
96:          }

158          uint256 prefix;
159          assembly {
160              prefix := byte(0, mload(ptr))
161:         }

177              bytes1 firstByteOfContent;
178              assembly {
179                  firstByteOfContent := and(mload(add(ptr, 1)), shl(248, 0xff))
180:             }

197              bytes1 firstByteOfContent;
198              assembly {
199                  firstByteOfContent := and(mload(add(ptr, 1)), shl(248, 0xff))
200:             }

207              uint256 strLen;
208              assembly {
209                  strLen := shr(sub(256, mul(8, lenOfStrLen)), mload(add(ptr, 1)))
210:             }

243              bytes1 firstByteOfContent;
244              assembly {
245                  firstByteOfContent := and(mload(add(ptr, 1)), shl(248, 0xff))
246:             }

253              uint256 listLen;
254              assembly {
255                  listLen := shr(sub(256, mul(8, lenOfListLen)), mload(add(ptr, 1)))
256:             }

294          uint256 src = MemoryPointer.unwrap(_src) + _offset;
295          assembly {
296              let dest := add(out_, 32)
297              let i := 0
298              for { } lt(i, _length) { i := add(i, 32) } { mstore(add(dest, i), mload(add(src, i))) }
299  
300              if gt(i, _length) { mstore(add(dest, _length), 0) }
301:         }

```
*GitHub*: [93](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L93-L96), [158](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L158-L161), [177](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L177-L180), [197](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L197-L200), [207](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L207-L210), [243](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L243-L246), [253](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L253-L256), [294](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L294-L301)

</details>





### [G&#x2011;41] Multiple `address`/ID mappings can be combined into a single `mapping` of an `address`/ID to a `struct`
Saves a storage slot for each of the removed mappings (i.e. this finding is not about runtime savings). The instances below refer to both mappings using the same key in the same function, so the mappings are related.

*There are 4 instances of this issue:*

```solidity
File: contracts/L1/libs/LibVerifying.sol

/// @audit combine into a `struct`: blocks,transitions
16:  library LibVerifying {

```
*GitHub*: [16](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L16-L16)

```solidity
File: contracts/bridge/Bridge.sol

/// @audit combine into a `struct`: messageStatus,proofReceipt
16:  contract Bridge is EssentialContract, IBridge {

```
*GitHub*: [16](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L16-L16)

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol

/// @audit combine into a `struct`: claimedAmount,withdrawnAmount
12:  contract ERC20Airdrop2 is MerkleClaimable {

```
*GitHub*: [12](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L12-L12)

```solidity
File: contracts/tokenvault/ERC20Vault.sol

/// @audit combine into a `struct`: bridgedToCanonical,btokenBlacklist
18:  contract ERC20Vault is BaseVault {

```
*GitHub*: [18](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L18-L18)



### [G&#x2011;42] Multiple accesses of a `memory`/`calldata` array should use a local variable cache
The instances below point to the second+ access of a value inside a `memory`/`calldata` array, within a function. Caching avoids recalculating the array offsets into `memory`/`calldata`

*There are 15 instances of this issue:*

```solidity
File: contracts/L1/libs/LibDepositing.sol

/// @audit deposits_...[]
/// @audit deposits_...[]
93:                  uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount;

/// @audit deposits_...[]
101:                     deposits_[i].amount -= _fee;

```
*GitHub*: [93](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L93-L93), [93](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L93-L93), [101](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L101-L101)

```solidity
File: contracts/L1/libs/LibProposing.sol

/// @audit hookCalls...[]
253:                 IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }(

/// @audit hookCalls...[]
254:                     blk, meta_, params.hookCalls[i].data

/// @audit hookCalls...[]
257:                 prevHook = params.hookCalls[i].hook;

```
*GitHub*: [253](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L253-L253), [254](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L254-L254), [257](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L257-L257)

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

/// @audit serialNumBatch...[]
84:              _serialNumIsRevoked[index][serialNumBatch[i]] = true;

/// @audit serialNumBatch...[]
99:              delete _serialNumIsRevoked[index][serialNumBatch[i]];

/// @audit certs...[]
/// @audit certs...[]
286:                 certs[i].tbsCertificate, certs[i].signature, issuer.pubKey

/// @audit parsedQuoteCerts...[]
442:             IPEMCertChainLib.ECSha256Certificate memory pckCert = parsedQuoteCerts[0];

```
*GitHub*: [84](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L84-L84), [99](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L99-L99), [286](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L286-L286), [286](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L286-L286), [442](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L442-L442)

```solidity
File: contracts/verifiers/SgxVerifier.sol

/// @audit _instances...[]
213:             addressRegistered[_instances[i]] = true;

/// @audit _instances...[]
215:             if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();

/// @audit _instances...[]
217:             instances[nextInstanceId] = Instance(_instances[i], validSince);

/// @audit _instances...[]
220:             emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);

```
*GitHub*: [213](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L213-L213), [215](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L215-L215), [217](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L217-L217), [220](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220-L220)



### [G&#x2011;43] Optimize names to save gas
`public`/`external` function names and `public` member variable names can be optimized to save gas. See [this](https://gist.github.com/IllIllI000/a5d8b486a8259f9f77891a919febd1a9) link for an example of how it works. Below are the interfaces/abstract contracts that can be optimized so that the most frequently-called functions use the least amount of gas possible during method lookup. Method IDs that have two leading zero bytes can save **128 gas** each during deployment, and renaming functions to have lower method IDs will save **22 gas** per call, [per sorted position shifted](https://medium.com/joyso/solidity-how-does-function-name-affect-gas-consumption-in-smart-contract-47d270d8ac92)

*There are 31 instances of this issue:*

<details>
<summary>see instances</summary>


```solidity
File: contracts/L1/TaikoL1.sol

/// @audit  proposeBlock(), getConfig(), getStateVariables(), proveBlock(), getBlock(), init(), getTransition(), unpause(), isBlobReusable(), canDepositEthToL2(), pauseProving(), verifyBlocks(), depositEtherToL2()
22   contract TaikoL1 is EssentialContract, ITaikoL1, TaikoEvents, TaikoErrors {
23:      /// @notice The TaikoL1 state.

```
*GitHub*: [22](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L22-L23)

```solidity
File: contracts/L1/TaikoToken.sol

/// @audit  init(), snapshot(), burn()
15:  contract TaikoToken is EssentialContract, ERC20SnapshotUpgradeable, ERC20VotesUpgradeable {

```
*GitHub*: [15](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoToken.sol#L15-L15)

```solidity
File: contracts/L1/gov/TaikoGovernor.sol

/// @audit  init()
16   contract TaikoGovernor is
17       EssentialContract,
18       GovernorCompatibilityBravoUpgradeable,
19       GovernorVotesUpgradeable,
20       GovernorVotesQuorumFractionUpgradeable,
21       GovernorTimelockControlUpgradeable
22:  {

```
*GitHub*: [16](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L16-L22)

```solidity
File: contracts/L1/gov/TaikoTimelockController.sol

/// @audit  init()
9:   contract TaikoTimelockController is EssentialContract, TimelockControllerUpgradeable {

```
*GitHub*: [9](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L9-L9)

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

/// @audit  init(), onBlockProposed(), hashAssignment()
14:  contract AssignmentHook is EssentialContract, IHook {

```
*GitHub*: [14](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L14-L14)

```solidity
File: contracts/L1/libs/LibProving.sol

/// @audit  pauseProving()
16:  library LibProving {

```
*GitHub*: [16](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L16-L16)

```solidity
File: contracts/L1/libs/LibUtils.sol

/// @audit  getTransition(), getBlock()
9    library LibUtils {
10:      // Warning: Any errors defined here must also be defined in TaikoErrors.sol.

```
*GitHub*: [9](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibUtils.sol#L9-L10)

```solidity
File: contracts/L1/libs/LibVerifying.sol

/// @audit  init()
16:  library LibVerifying {

```
*GitHub*: [16](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L16-L16)

```solidity
File: contracts/L1/provers/GuardianProver.sol

/// @audit  init(), approve()
10:  contract GuardianProver is Guardians {

```
*GitHub*: [10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/GuardianProver.sol#L10-L10)

```solidity
File: contracts/L1/provers/Guardians.sol

/// @audit  isApproved(), numGuardians(), setGuardians()
9    abstract contract Guardians is EssentialContract {
10:      /// @notice The minimum number of guardians

```
*GitHub*: [9](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L9-L10)

```solidity
File: contracts/L1/tiers/DevnetTierProvider.sol

/// @audit  init(), getTier(), getTierIds(), getMinTier()
10:  contract DevnetTierProvider is EssentialContract, ITierProvider {

```
*GitHub*: [10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L10-L10)

```solidity
File: contracts/L1/tiers/MainnetTierProvider.sol

/// @audit  init(), getTier(), getTierIds(), getMinTier()
10:  contract MainnetTierProvider is EssentialContract, ITierProvider {

```
*GitHub*: [10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L10-L10)

```solidity
File: contracts/L2/CrossChainOwned.sol

/// @audit  onMessageInvocation()
14   abstract contract CrossChainOwned is EssentialContract, IMessageInvocable {
15:      /// @notice The owner chain ID.

```
*GitHub*: [14](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L14-L15)

```solidity
File: contracts/L2/TaikoL2.sol

/// @audit  getBasefee(), getBlockHash(), getConfig(), init(), anchor(), withdraw(), skipFeeCheck()
21:  contract TaikoL2 is CrossChainOwned {

```
*GitHub*: [21](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L21-L21)

```solidity
File: contracts/L2/TaikoL2EIP1559Configurable.sol

/// @audit  getConfig()
9    contract TaikoL2EIP1559Configurable is TaikoL2 {
10:      /// @notice EIP-1559 configuration.

```
*GitHub*: [9](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L9-L10)

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

/// @audit  setMrSigner(), configureTcbInfoJson(), configureQeIdentityJson(), toggleLocalReportCheck(), setMrEnclave(), addRevokedCertSerialNum(), removeRevokedCertSerialNum(), verifyAttestation(), verifyParsedQuote()
22:  contract AutomataDcapV3Attestation is IAttestation {

```
*GitHub*: [22](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L22-L22)

```solidity
File: contracts/automata-attestation/utils/SigVerifyLib.sol

/// @audit  verifyRS1Signature(), verifyRS256Signature(), verifyCertificateSignature(), verifyAttStmtSignature(), verifyES256Signature()
15:  contract SigVerifyLib is ISigVerifyLib {

```
*GitHub*: [15](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L15-L15)

```solidity
File: contracts/bridge/Bridge.sol

/// @audit  sendMessage(), banAddress(), suspendMessages(), retryMessage(), processMessage(), recallMessage(), proveMessageFailed(), isMessageSent(), context(), isDestChainEnabled(), proveMessageReceived(), signalForFailedMessage(), hashMessage(), getInvocationDelays(), init()
16:  contract Bridge is EssentialContract, IBridge {

```
*GitHub*: [16](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L16-L16)

```solidity
File: contracts/common/AddressManager.sol

/// @audit  setAddress(), init(), getAddress()
10   contract AddressManager is EssentialContract, IAddressManager {
11:      /// @dev Mapping of chainId to mapping of name to address.

```
*GitHub*: [10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressManager.sol#L10-L11)

```solidity
File: contracts/common/AddressResolver.sol

/// @audit  resolve(), resolve()
11   abstract contract AddressResolver is IAddressResolver, Initializable {
12:      /// @notice Address of the AddressManager.

```
*GitHub*: [11](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressResolver.sol#L11-L12)

```solidity
File: contracts/common/EssentialContract.sol

/// @audit  unpause(), pause(), paused()
10:  abstract contract EssentialContract is UUPSUpgradeable, Ownable2StepUpgradeable, AddressResolver {

```
*GitHub*: [10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L10-L10)

```solidity
File: contracts/signal/SignalService.sol

/// @audit  sendSignal(), authorize(), init(), proveSignalReceived(), syncChainData(), getSyncedChainData(), isSignalSent(), isChainDataSynced(), getSignalSlot(), signalForChainData()
14   contract SignalService is EssentialContract, ISignalService {
15       /// @notice Mapping to store the top blockId.
16:      /// @dev Slot 1.

```
*GitHub*: [14](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L14-L16)

```solidity
File: contracts/team/TimelockTokenPool.sol

/// @audit  void(), grant(), getMyGrantSummary(), withdraw(), withdraw(), getMyGrant(), init()
25:  contract TimelockTokenPool is EssentialContract {

```
*GitHub*: [25](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L25-L25)

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol

/// @audit  setConfig()
10   abstract contract MerkleClaimable is EssentialContract {
11:      /// @notice Mapping of hashes and their claim status

```
*GitHub*: [10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L10-L11)

```solidity
File: contracts/tokenvault/BaseVault.sol

/// @audit  init(), name()
12   abstract contract BaseVault is
13       EssentialContract,
14       IRecallableSender,
15       IMessageInvocable,
16       IERC165Upgradeable
17:  {

```
*GitHub*: [12](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseVault.sol#L12-L17)

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

/// @audit  onMessageRecalled(), onMessageInvocation(), name()
29:  contract ERC1155Vault is BaseNFTVault, ERC1155ReceiverUpgradeable {

```
*GitHub*: [29](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L29-L29)

```solidity
File: contracts/tokenvault/ERC20Vault.sol

/// @audit  onMessageInvocation(), onMessageRecalled(), name()
18:  contract ERC20Vault is BaseVault {

```
*GitHub*: [18](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L18-L18)

```solidity
File: contracts/tokenvault/ERC721Vault.sol

/// @audit  onMessageInvocation(), onMessageRecalled(), name()
16:  contract ERC721Vault is BaseNFTVault, IERC721Receiver {

```
*GitHub*: [16](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L16-L16)

```solidity
File: contracts/tokenvault/adapters/USDCAdapter.sol

/// @audit  init()
28   contract USDCAdapter is BridgedERC20Base {
29       /// @notice The USDC instance.
30:      /// @dev Slot 1.

```
*GitHub*: [28](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L28-L30)

```solidity
File: contracts/verifiers/GuardianVerifier.sol

/// @audit  verifyProof(), init()
10:  contract GuardianVerifier is EssentialContract, IVerifier {

```
*GitHub*: [10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L10-L10)

```solidity
File: contracts/verifiers/SgxVerifier.sol

/// @audit  init(), addInstances(), registerInstance(), deleteInstances(), verifyProof(), getSignedHash()
19   contract SgxVerifier is EssentialContract, IVerifier {
20       /// @dev Each public-private key pair (Ethereum address) is generated within
21       /// the SGX program when it boots up. The off-chain remote attestation
22       /// ensures the validity of the program hash and has the capability of
23:      /// bootstrapping the network with trustworthy instances.

```
*GitHub*: [19](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L19-L23)

</details>





### [G&#x2011;44] Reduce deployment costs by tweaking contracts' metadata
See [this](https://www.rareskills.io/post/solidity-metadata) link, at its bottom, for full details

*There are 28 instances of this issue:*

<details>
<summary>see instances</summary>


```solidity
File: contracts/L1/TaikoL1.sol

22   contract TaikoL1 is EssentialContract, ITaikoL1, TaikoEvents, TaikoErrors {
23:      /// @notice The TaikoL1 state.

```
*GitHub*: [22](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L22-L23)

```solidity
File: contracts/L1/TaikoToken.sol

15:  contract TaikoToken is EssentialContract, ERC20SnapshotUpgradeable, ERC20VotesUpgradeable {

```
*GitHub*: [15](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoToken.sol#L15-L15)

```solidity
File: contracts/L1/gov/TaikoGovernor.sol

16   contract TaikoGovernor is
17       EssentialContract,
18       GovernorCompatibilityBravoUpgradeable,
19       GovernorVotesUpgradeable,
20       GovernorVotesQuorumFractionUpgradeable,
21       GovernorTimelockControlUpgradeable
22:  {

```
*GitHub*: [16](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L16-L22)

```solidity
File: contracts/L1/gov/TaikoTimelockController.sol

9:   contract TaikoTimelockController is EssentialContract, TimelockControllerUpgradeable {

```
*GitHub*: [9](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L9-L9)

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

14:  contract AssignmentHook is EssentialContract, IHook {

```
*GitHub*: [14](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L14-L14)

```solidity
File: contracts/L1/provers/GuardianProver.sol

10:  contract GuardianProver is Guardians {

```
*GitHub*: [10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/GuardianProver.sol#L10-L10)

```solidity
File: contracts/L1/tiers/DevnetTierProvider.sol

10:  contract DevnetTierProvider is EssentialContract, ITierProvider {

```
*GitHub*: [10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L10-L10)

```solidity
File: contracts/L1/tiers/MainnetTierProvider.sol

10:  contract MainnetTierProvider is EssentialContract, ITierProvider {

```
*GitHub*: [10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L10-L10)

```solidity
File: contracts/L2/TaikoL2EIP1559Configurable.sol

9    contract TaikoL2EIP1559Configurable is TaikoL2 {
10:      /// @notice EIP-1559 configuration.

```
*GitHub*: [9](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L9-L10)

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

22:  contract AutomataDcapV3Attestation is IAttestation {

```
*GitHub*: [22](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L22-L22)

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol

12:  contract PEMCertChainLib is IPEMCertChainLib {

```
*GitHub*: [12](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L12-L12)

```solidity
File: contracts/automata-attestation/utils/SigVerifyLib.sol

15:  contract SigVerifyLib is ISigVerifyLib {

```
*GitHub*: [15](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L15-L15)

```solidity
File: contracts/bridge/Bridge.sol

16:  contract Bridge is EssentialContract, IBridge {

```
*GitHub*: [16](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L16-L16)

```solidity
File: contracts/common/AddressManager.sol

10   contract AddressManager is EssentialContract, IAddressManager {
11:      /// @dev Mapping of chainId to mapping of name to address.

```
*GitHub*: [10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressManager.sol#L10-L11)

```solidity
File: contracts/signal/SignalService.sol

14   contract SignalService is EssentialContract, ISignalService {
15       /// @notice Mapping to store the top blockId.
16:      /// @dev Slot 1.

```
*GitHub*: [14](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L14-L16)

```solidity
File: contracts/team/TimelockTokenPool.sol

25:  contract TimelockTokenPool is EssentialContract {

```
*GitHub*: [25](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L25-L25)

```solidity
File: contracts/team/airdrop/ERC20Airdrop.sol

11   contract ERC20Airdrop is MerkleClaimable {
12:      /// @notice The address of the token contract.

```
*GitHub*: [11](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L11-L12)

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol

12:  contract ERC20Airdrop2 is MerkleClaimable {

```
*GitHub*: [12](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L12-L12)

```solidity
File: contracts/team/airdrop/ERC721Airdrop.sol

9    contract ERC721Airdrop is MerkleClaimable {
10:      /// @notice The address of the token contract.

```
*GitHub*: [9](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L9-L10)

```solidity
File: contracts/tokenvault/BridgedERC1155.sol

14   contract BridgedERC1155 is EssentialContract, IERC1155MetadataURIUpgradeable, ERC1155Upgradeable {
15:      /// @notice Address of the source token contract.

```
*GitHub*: [14](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L14-L15)

```solidity
File: contracts/tokenvault/BridgedERC20.sol

15   contract BridgedERC20 is
16       BridgedERC20Base,
17       IERC20MetadataUpgradeable,
18       ERC20SnapshotUpgradeable,
19       ERC20VotesUpgradeable
20   {
21:      /// @dev Slot 1.

```
*GitHub*: [15](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L15-L21)

```solidity
File: contracts/tokenvault/BridgedERC721.sol

12   contract BridgedERC721 is EssentialContract, ERC721Upgradeable {
13:      /// @notice Address of the source token contract.

```
*GitHub*: [12](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L12-L13)

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

29:  contract ERC1155Vault is BaseNFTVault, ERC1155ReceiverUpgradeable {

```
*GitHub*: [29](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L29-L29)

```solidity
File: contracts/tokenvault/ERC20Vault.sol

18:  contract ERC20Vault is BaseVault {

```
*GitHub*: [18](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L18-L18)

```solidity
File: contracts/tokenvault/ERC721Vault.sol

16:  contract ERC721Vault is BaseNFTVault, IERC721Receiver {

```
*GitHub*: [16](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L16-L16)

```solidity
File: contracts/tokenvault/adapters/USDCAdapter.sol

28   contract USDCAdapter is BridgedERC20Base {
29       /// @notice The USDC instance.
30:      /// @dev Slot 1.

```
*GitHub*: [28](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L28-L30)

```solidity
File: contracts/verifiers/GuardianVerifier.sol

10:  contract GuardianVerifier is EssentialContract, IVerifier {

```
*GitHub*: [10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L10-L10)

```solidity
File: contracts/verifiers/SgxVerifier.sol

19   contract SgxVerifier is EssentialContract, IVerifier {
20       /// @dev Each public-private key pair (Ethereum address) is generated within
21       /// the SGX program when it boots up. The off-chain remote attestation
22       /// ensures the validity of the program hash and has the capability of
23:      /// bootstrapping the network with trustworthy instances.

```
*GitHub*: [19](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L19-L23)

</details>





### [G&#x2011;45] State variables only set in the constructor should be declared `immutable`
Avoids a Gsset (**20000 gas**) in the constructor, and replaces the first access in each transaction (Gcoldsload - **2100 gas**) and each access thereafter (Gwarmacces - **100 gas**) with a `PUSH32` (**3 gas**). 

While `string`s are not value types, and therefore cannot be `immutable`/`constant` if not hard-coded outside of the constructor, the same behavior can be achieved by making the current contract `abstract` with `virtual` functions for the `string` accessors, and having a child contract override the functions with the hard-coded implementation-specific values.

*There are 6 instances of this issue:*

```solidity
File: contracts/L1/provers/Guardians.sol

27:      uint32 public version;

```
*GitHub*: [27](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L27-L27)

```solidity
File: contracts/L2/CrossChainOwned.sol

19:      uint64 public nextTxId;

```
*GitHub*: [19](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L19-L19)

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

52:      address public owner;

```
*GitHub*: [52](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L52-L52)

```solidity
File: contracts/automata-attestation/utils/SigVerifyLib.sol

18:      address private ES256VERIFIER;

```
*GitHub*: [18](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L18-L18)

```solidity
File: contracts/bridge/Bridge.sol

31:      uint128 public nextMessageId;

```
*GitHub*: [31](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L31-L31)

```solidity
File: contracts/verifiers/SgxVerifier.sol

39:      uint256 public nextInstanceId;

```
*GitHub*: [39](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L39-L39)



### [G&#x2011;46] Functions guaranteed to revert when called by normal users can be marked `payable`
If a function modifier such as `onlyOwner` is used, or a function checks `msg.sender` some other way, the function will revert if a normal user tries to pay the function. Marking the function as `payable` will lower the gas cost for legitimate callers because the compiler will not include checks for whether a payment was provided. The extra opcodes avoided are `CALLVALUE`(2),`DUP1`(3),`ISZERO`(3),`PUSH2`(3),`JUMPI`(10),`PUSH1`(3),`DUP1`(3),`REVERT`(0),`JUMPDEST`(1),`POP`(2), which costs an average of about **21 gas per call** to the function, in addition to the extra deployment cost

*There are 23 instances of this issue:*

<details>
<summary>see instances</summary>


```solidity
File: contracts/L1/TaikoL1.sol

111:     function pauseProving(bool _pause) external {

```
*GitHub*: [111](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L111-L111)

```solidity
File: contracts/L1/provers/Guardians.sol

53       function setGuardians(
54           address[] memory _newGuardians,
55           uint8 _minGuardians
56       )
57           external
58           onlyOwner
59           nonReentrant
60:      {

```
*GitHub*: [53](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L53-L60)

```solidity
File: contracts/L2/TaikoL2.sol

107      function anchor(
108          bytes32 _l1BlockHash,
109          bytes32 _l1StateRoot,
110          uint64 _l1BlockId,
111          uint32 _parentGasUsed
112      )
113          external
114          nonReentrant
115:     {

163      function withdraw(
164          address _token,
165          address _to
166      )
167          external
168          onlyFromOwnerOrNamed("withdrawer")
169          nonReentrant
170          whenNotPaused
171:     {

```
*GitHub*: [107](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L107-L115), [163](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L163-L171)

```solidity
File: contracts/L2/TaikoL2EIP1559Configurable.sol

25       function setConfigAndExcess(
26           Config memory _newConfig,
27           uint64 _newGasExcess
28       )
29           external
30           virtual
31           onlyOwner
32:      {

```
*GitHub*: [25](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L25-L32)

```solidity
File: contracts/bridge/Bridge.sol

82       function suspendMessages(
83           bytes32[] calldata _msgHashes,
84           bool _suspend
85       )
86           external
87           onlyFromOwnerOrNamed("bridge_watchdog")
88:      {

101      function banAddress(
102          address _addr,
103          bool _ban
104      )
105          external
106          onlyFromOwnerOrNamed("bridge_watchdog")
107          nonReentrant
108:     {

217      function processMessage(
218          Message calldata _message,
219          bytes calldata _proof
220      )
221          external
222          nonReentrant
223          whenNotPaused
224          sameChain(_message.destChainId)
225:     {

310      function retryMessage(
311          Message calldata _message,
312          bool _isLastAttempt
313      )
314          external
315          nonReentrant
316          whenNotPaused
317          sameChain(_message.destChainId)
318:     {

```
*GitHub*: [82](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L82-L88), [101](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L101-L108), [217](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L217-L225), [310](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L310-L318)

```solidity
File: contracts/common/AddressManager.sol

38       function setAddress(
39           uint64 _chainId,
40           bytes32 _name,
41           address _newAddress
42       )
43           external
44           virtual
45           onlyOwner
46:      {

```
*GitHub*: [38](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressManager.sol#L38-L46)

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol

45       function setConfig(
46           uint64 _claimStart,
47           uint64 _claimEnd,
48           bytes32 _merkleRoot
49       )
50           external
51           onlyOwner
52:      {

```
*GitHub*: [45](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L45-L52)

```solidity
File: contracts/tokenvault/BridgedERC1155.sol

66       function mint(
67           address _to,
68           uint256 _tokenId,
69           uint256 _amount
70       )
71           public
72           nonReentrant
73           whenNotPaused
74           onlyFromNamed("erc1155_vault")
75:      {

83       function mintBatch(
84           address _to,
85           uint256[] memory _tokenIds,
86           uint256[] memory _amounts
87       )
88           public
89           nonReentrant
90           whenNotPaused
91           onlyFromNamed("erc1155_vault")
92:      {

100      function burn(
101          address _account,
102          uint256 _tokenId,
103          uint256 _amount
104      )
105          public
106          nonReentrant
107          whenNotPaused
108          onlyFromNamed("erc1155_vault")
109:     {

```
*GitHub*: [66](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L66-L75), [83](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L83-L92), [100](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L100-L109)

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol

36       function changeMigrationStatus(
37           address _migratingAddress,
38           bool _migratingInbound
39       )
40           external
41           nonReentrant
42           whenNotPaused
43           onlyFromOwnerOrNamed("erc20_vault")
44:      {

57:      function mint(address _account, uint256 _amount) public nonReentrant whenNotPaused {

75:      function burn(address _account, uint256 _amount) public nonReentrant whenNotPaused {

```
*GitHub*: [36](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L36-L44), [57](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L57-L57), [75](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L75-L75)

```solidity
File: contracts/tokenvault/BridgedERC721.sol

54       function mint(
55           address _account,
56           uint256 _tokenId
57       )
58           public
59           nonReentrant
60           whenNotPaused
61           onlyFromNamed("erc721_vault")
62:      {

69       function burn(
70           address _account,
71           uint256 _tokenId
72       )
73           public
74           nonReentrant
75           whenNotPaused
76           onlyFromNamed("erc721_vault")
77:      {

```
*GitHub*: [54](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L54-L62), [69](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L69-L77)

```solidity
File: contracts/tokenvault/ERC20Vault.sol

148      function changeBridgedToken(
149          CanonicalERC20 calldata _ctoken,
150          address _btokenNew
151      )
152          external
153          nonReentrant
154          whenNotPaused
155          onlyOwner
156          returns (address btokenOld_)
157:     {

```
*GitHub*: [148](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L148-L157)

```solidity
File: contracts/verifiers/SgxVerifier.sol

90       function addInstances(address[] calldata _instances)
91           external
92           onlyOwner
93           returns (uint256[] memory)
94:      {

100      function deleteInstances(uint256[] calldata _ids)
101          external
102          onlyFromOwnerOrNamed("rollup_watchdog")
103:     {

139      function verifyProof(
140          Context calldata _ctx,
141          TaikoData.Transition calldata _tran,
142          TaikoData.TierProof calldata _proof
143      )
144          external
145          onlyFromNamed("taiko")
146:     {

```
*GitHub*: [90](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L90-L94), [100](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L100-L103), [139](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L139-L146)

</details>





### [G&#x2011;47] Use local variables for emitting packed storage variables
Saves **14 gas** due to not having to clear the other bits of the [slot](https://gist.github.com/IllIllI000/f9cf10ee73bfd02d736beeab348c7441).

*There are 11 instances of this issue:*

<details>
<summary>see instances</summary>


```solidity
File: contracts/L1/libs/LibProving.sol

/// @audit blk
209              emit TransitionProved({
210                  blockId: blk.blockId,
211                  tran: _tran,
212                  prover: msg.sender,
213                  validityBond: tier.validityBond,
214                  tier: _proof.tier
215:             });

/// @audit blk
230                  emit TransitionProved({
231                      blockId: blk.blockId,
232                      tran: _tran,
233                      prover: msg.sender,
234                      validityBond: 0,
235                      tier: _proof.tier
236:                 });

/// @audit blk
254                  emit TransitionContested({
255                      blockId: blk.blockId,
256                      tran: _tran,
257                      contester: msg.sender,
258                      contestBond: tier.contestBond,
259                      tier: _proof.tier
260:                 });

```
*GitHub*: [209](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L209-L215), [230](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L230-L236), [254](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L254-L260)

```solidity
File: contracts/L1/libs/LibVerifying.sol

/// @audit ts
/// @audit blk
198                  emit BlockVerified({
199                      blockId: blockId,
200                      assignedProver: blk.assignedProver,
201                      prover: ts.prover,
202                      blockHash: blockHash,
203                      stateRoot: stateRoot,
204                      tier: ts.tier,
205                      contestations: ts.contestations
206:                 });

```
*GitHub*: [198](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L198-L206), [198](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L198-L206)

```solidity
File: contracts/L1/provers/Guardians.sol

/// @audit version
95:          emit GuardiansUpdated(version, _newGuardians);

```
*GitHub*: [95](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L95-L95)

```solidity
File: contracts/L2/CrossChainOwned.sol

/// @audit nextTxId
53:          emit TransactionExecuted(nextTxId++, bytes4(txdata));

```
*GitHub*: [53](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L53-L53)

```solidity
File: contracts/L2/TaikoL2.sol

/// @audit gasExcess
157:         emit Anchored(blockhash(parentId), gasExcess);

```
*GitHub*: [157](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L157-L157)

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol

/// @audit migratingAddress
63:              emit MigratedTo(migratingAddress, _account, _amount);

/// @audit migratingAddress
80:              emit MigratedTo(migratingAddress, _account, _amount);

```
*GitHub*: [63](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L63-L63), [80](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L80-L80)

```solidity
File: contracts/verifiers/SgxVerifier.sol

/// @audit instances
109:             emit InstanceDeleted(idx, instances[idx].addr);

```
*GitHub*: [109](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L109-L109)

</details>





### [G&#x2011;48] Stack variable is only used once
If the variable is only accessed once, it's cheaper to use the assigned value directly that one time, and save the **3 gas** the extra stack assignment would spend

*There are 126 instances of this issue:*

<details>
<summary>see instances</summary>


```solidity
File: contracts/L1/TaikoL1.sol

84           (
85               TaikoData.BlockMetadata memory meta,
86               TaikoData.Transition memory tran,
87               TaikoData.TierProof memory proof
88:          ) = abi.decode(_input, (TaikoData.BlockMetadata, TaikoData.Transition, TaikoData.TierProof));

94:          uint8 maxBlocksToVerify = LibProving.proveBlock(state, config, this, meta, tran, proof);

```
*GitHub*: [84](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L84-L88), [94](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L94-L94)

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

94:          bytes32 hash = hashAssignment(assignment, taikoL1Address, _meta.blobHash);

101:         IERC20 tko = IERC20(resolve("taiko_token", false));

```
*GitHub*: [94](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L94-L94), [101](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L101-L101)

```solidity
File: contracts/L1/libs/LibDepositing.sol

45:          uint256 slot = _state.slotA.numEthDeposits % _config.ethDepositRingBufferSize;

```
*GitHub*: [45](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L45-L45)

```solidity
File: contracts/L1/libs/LibProposing.sol

238:             uint256 tkoBalance = tko.balanceOf(address(this));

```
*GitHub*: [238](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L238-L238)

```solidity
File: contracts/L1/libs/LibProving.sol

129          (uint32 tid, TaikoData.TransitionState storage ts) =
130:             _createTransition(_state, blk, _tran, slot);

164:                 bool isContesting = _proof.tier == ts.tier && tier.contestBond != 0;

166                  IVerifier.Context memory ctx = IVerifier.Context({
167                      metaHash: blk.metaHash,
168                      blobHash: _meta.blobHash,
169                      // Separate msgSender to allow the prover to be any address in the future.
170                      prover: msg.sender,
171                      msgSender: msg.sender,
172                      blockId: blk.blockId,
173                      isContesting: isContesting,
174                      blobUsed: _meta.blobUsed
175:                 });

192              bool returnLivenessBond = blk.livenessBond > 0 && _proof.data.length == 32
193:                 && bytes32(_proof.data) == RETURN_LIVENESS_BOND;

414          bool inProvingWindow = uint256(_ts.timestamp).max(_state.slotB.lastUnpausedAt)
415:             + _tier.provingWindow * 60 >= block.timestamp;

```
*GitHub*: [129](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L129-L130), [164](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L164-L164), [166](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L166-L175), [192](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L192-L193), [414](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L414-L415)

```solidity
File: contracts/L1/libs/LibVerifying.sol

234          (uint64 lastSyncedBlock,) = signalService.getSyncedChainData(
235              _config.chainId, LibSignals.STATE_ROOT, 0 /* latest block Id*/
236:         );

```
*GitHub*: [234](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L234-L236)

```solidity
File: contracts/L2/CrossChainOwned.sol

42:          (uint64 txId, bytes memory txdata) = abi.decode(_data, (uint64, bytes));

50:          (bool success,) = address(this).call(txdata);

```
*GitHub*: [42](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L42-L42), [50](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L50-L50)

```solidity
File: contracts/L2/TaikoL2.sol

131:         (bytes32 publicInputHashOld, bytes32 publicInputHashNew) = _calcPublicInputHash(parentId);

136:         Config memory config = getConfig();

```
*GitHub*: [131](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L131-L131), [136](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L136-L136)

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

139:         (bool success,) = _verify(data);

163:         bytes memory retData = abi.encodePacked(INVALID_EXIT_CODE);

166          (bool successful, V3Struct.ParsedV3QuoteStruct memory parsedV3Quote) =
167:             V3Parser.parseInput(quote, address(pemCertLib));

181          bool miscselectMatched =
182:             quoteEnclaveReport.miscSelect & enclaveId.miscselectMask == enclaveId.miscselect;

184          bool attributesMatched =
185:             quoteEnclaveReport.attributes & enclaveId.attributesMask == enclaveId.attributes;

186:         bool mrsignerMatched = quoteEnclaveReport.mrSigner == enclaveId.mrsigner;

188:         bool isvprodidMatched = quoteEnclaveReport.isvProdId == enclaveId.isvprodid;

313:         bytes32 expectedAuthDataHash = bytes32(qeEnclaveReport.reportData.substring(0, 32));

314          bytes memory concatOfAttestKeyAndQeAuthData =
315:             abi.encodePacked(authDataV3.ecdsaAttestationKey, authDataV3.qeAuthData.data);

316:         bytes32 computedAuthDataHash = sha256(concatOfAttestKeyAndQeAuthData);

318:         bool qeReportDataIsValid = expectedAuthDataHash == computedAuthDataHash;

320              bytes memory pckSignedQeReportBytes =
321:                 V3Parser.packQEReport(authDataV3.pckSignedQeReport);

322              bool qeSigVerified = sigVerifyLib.verifyES256Signature(
323                  pckSignedQeReportBytes, authDataV3.qeReportSignature, pckCertPubKey
324:             );

325              bool quoteSigVerified = sigVerifyLib.verifyES256Signature(
326                  signedQuoteData, authDataV3.ecdsa256BitSignature, authDataV3.ecdsaAttestationKey
327:             );

372          (
373              bool successful,
374              ,
375              ,
376              bytes memory signedQuoteData,
377              V3Struct.ECDSAQuoteV3AuthData memory authDataV3
378:         ) = V3Parser.validateParsedInput(v3quote);

387                  bool mrEnclaveIsTrusted =
388:                     _trustedUserMrEnclave[v3quote.localEnclaveReport.mrEnclave];

389:                 bool mrSignerIsTrusted = _trustedUserMrSigner[v3quote.localEnclaveReport.mrSigner];

437:             bool tcbConfigured = LibString.eq(parsedFmspc, fetchedTcbInfo.fmspc);

442:             IPEMCertChainLib.ECSha256Certificate memory pckCert = parsedQuoteCerts[0];

443:             bool pceidMatched = LibString.eq(pckCert.pck.sgxExtension.pceid, fetchedTcbInfo.pceid);

463:             bool pckCertChainVerified = _verifyCertChain(parsedQuoteCerts);

471              bool enclaveReportSigsVerified = _enclaveReportSigVerification(
472                  parsedQuoteCerts[0].pubKey,
473                  signedQuoteData,
474                  authDataV3,
475                  v3quote.v3AuthData.pckSignedQeReport
476:             );

```
*GitHub*: [139](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L139-L139), [163](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L163-L163), [166](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L166-L167), [181](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L181-L182), [184](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L184-L185), [186](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L186-L186), [188](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L188-L188), [313](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L313-L313), [314](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L314-L315), [316](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L316-L316), [318](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L318-L318), [320](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L320-L321), [322](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L322-L324), [325](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L325-L327), [372](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L372-L378), [387](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L387-L388), [389](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L389-L389), [437](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L437-L437), [442](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L442-L442), [443](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L443-L443), [463](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L463-L463), [471](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L471-L476)

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol

82:          uint256 root = der.root();

107:             bytes memory serialNumBytes = der.bytesAt(tbsPtr);

120              bool issuerNameIsValid = LibString.eq(cert.pck.issuerName, PLATFORM_ISSUER_NAME)
121:                 || LibString.eq(cert.pck.issuerName, PROCESSOR_ISSUER_NAME);

174:             bytes memory sigX = _trimBytes(der.bytesAt(sigPtr), 32);

177:             bytes memory sigY = _trimBytes(der.bytesAt(sigPtr), 32);

225:         bool headerFound = beginPos != LibString.NOT_FOUND;

226:         bool footerFound = endPos != LibString.NOT_FOUND;

233:         uint256 contentStart = beginPos + HEADER_LENGTH;

239:         bytes memory delimiter = hex"0a";

240:         string memory contentSlice = LibString.slice(pemData, contentStart, endPos);

265:         uint256 lengthDiff = n - expectedLength;

350:         uint256 tcbPtr = der.nextSiblingOf(oidPtr);

```
*GitHub*: [82](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L82-L82), [107](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L107-L107), [120](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L120-L121), [174](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L174-L174), [177](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L177-L177), [225](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L225-L225), [226](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L226-L226), [233](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L233-L233), [239](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L239-L239), [240](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L240-L240), [265](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L265-L265), [350](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L350-L350)

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

38:          bytes memory rawHeader = quote.substring(0, 48);

39           (bool headerVerifiedSuccessfully, V3Struct.Header memory header) =
40:              parseAndVerifyHeader(rawHeader);

45           (bool authDataVerifiedSuccessfully, V3Struct.ECDSAQuoteV3AuthData memory authDataV3) =
46:              parseAuthDataAndVerifyCertType(quote.substring(436, localAuthDataSize), pemCertLibAddr);

51:          bytes memory rawLocalEnclaveReport = quote.substring(48, 384);

52:          V3Struct.EnclaveReport memory localEnclaveReport = parseEnclaveReport(rawLocalEnclaveReport);

106          uint32 totalQuoteSize = 48 // header
107              + 384 // local QE report
108              + 64 // ecdsa256BitSignature
109              + 64 // ecdsaAttestationKey
110              + 384 // QE report
111              + 64 // qeReportSignature
112              + 2 // sizeof(v3Quote.v3AuthData.qeAuthData.parsedDataSize)
113              + v3Quote.v3AuthData.qeAuthData.parsedDataSize + 2 // sizeof(v3Quote.v3AuthData.certification.certType)
114              + 4 // sizeof(v3Quote.v3AuthData.certification.certDataSize)
115:             + v3Quote.v3AuthData.certification.certDataSize;

119          bytes memory headerBytes = abi.encodePacked(
120              header.version,
121              header.attestationKeyType,
122              header.teeType,
123              header.qeSvn,
124              header.pceSvn,
125              header.qeVendorId,
126              header.userData
127:         );

224:         bytes memory certData = rawAuthData.substring(offset, cert.certDataSize);

229:         bytes memory rawQeReport = rawAuthData.substring(128, 384);

249:         uint16 isvProdIdPackBE = (enclaveReport.isvProdId >> 8) | (enclaveReport.isvProdId << 8);

250:         uint16 isvSvnPackBE = (enclaveReport.isvSvn >> 8) | (enclaveReport.isvSvn << 8);

275:         IPEMCertChainLib pemCertLib = PEMCertChainLib(pemCertLibAddr);

276:         IPEMCertChainLib.ECSha256Certificate[] memory parsedQuoteCerts;

277          (bool certParsedSuccessfully, bytes[] memory quoteCerts) =
278:             pemCertLib.splitCertificateChain(certBytes, 3);

```
*GitHub*: [38](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L38-L38), [39](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L39-L40), [45](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L45-L46), [51](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L51-L51), [52](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L52-L52), [106](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L106-L115), [119](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L119-L127), [224](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L224-L224), [229](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L229-L229), [249](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L249-L249), [250](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L250-L250), [275](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L275-L275), [276](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L276-L276), [277](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L277-L278)

```solidity
File: contracts/automata-attestation/utils/Asn1Decode.sol

183:         uint256 valueLength = ptr.ixl() + 1 - ptr.ixf();

```
*GitHub*: [183](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L183-L183)

```solidity
File: contracts/automata-attestation/utils/SigVerifyLib.sol

89:          bytes memory exponent = publicKey.substring(0, 3);

90:          bytes memory modulus = publicKey.substring(3, publicKey.length - 3);

106:         bytes memory exponent = publicKey.substring(0, 3);

107:         bytes memory modulus = publicKey.substring(3, publicKey.length - 3);

126:         uint256 r = uint256(bytes32(signature.substring(0, 32)));

127:         uint256 s = uint256(bytes32(signature.substring(32, 32)));

132:         uint256 gx = uint256(bytes32(publicKey.substring(0, 32)));

133:         uint256 gy = uint256(bytes32(publicKey.substring(32, 32)));

136:         bytes memory args = abi.encode(sha256(tbs), r, s, gx, gy);

137:         (bool success, bytes memory ret) = ES256VERIFIER.staticcall(args);

```
*GitHub*: [89](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L89-L89), [90](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L90-L90), [106](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L106-L106), [107](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L107-L107), [126](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L126-L126), [127](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L127-L127), [132](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L132-L132), [133](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L133-L133), [136](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L136-L136), [137](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L137-L137)

```solidity
File: contracts/bridge/Bridge.sol

129:         (bool destChainEnabled,) = isDestChainEnabled(_message.destChainId);

138:         uint256 expectedAmount = _message.value + _message.fee;

178:             bytes32 failureSignal = signalForFailedMessage(msgHash);

187:         (uint256 invocationDelay,) = getInvocationDelays();

233:         (uint256 invocationDelay, uint256 invocationExtraDelay) = getInvocationDelays();

280:                 uint256 gasLimit = msg.sender == _message.destOwner ? gasleft() : _message.gasLimit;

587          bytes memory data = abi.encodeCall(
588              ISignalService.proveSignalReceived,
589              (_chainId, resolve(_chainId, "bridge", false), _signal, _proof)
590:         );

```
*GitHub*: [129](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L129-L129), [138](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L138-L138), [178](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L178-L178), [187](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L187-L187), [233](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L233-L233), [280](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L280-L280), [587](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L587-L590)

```solidity
File: contracts/libs/Lib4844.sol

43           (bool ok, bytes memory ret) = POINT_EVALUATION_PRECOMPILE_ADDRESS.staticcall(
44               abi.encodePacked(_blobHash, _x, _y, _commitment, _pointProof)
45:          );

```
*GitHub*: [43](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/Lib4844.sol#L43-L45)

```solidity
File: contracts/libs/LibAddress.sol

27           (bool success,) = ExcessivelySafeCall.excessivelySafeCall(
28               _to,
29               _gasLimit,
30               _amount,
31               64, // return max 64 bytes
32               ""
33:          );

```
*GitHub*: [27](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibAddress.sol#L27-L33)

```solidity
File: contracts/libs/LibTrieProof.sol

52:              RLPReader.RLPItem[] memory accountState = RLPReader.readList(rlpAccount);

60           bool verified = SecureMerkleTrie.verifyInclusionProof(
61               bytes.concat(_slot), RLPWriter.writeUint(uint256(_value)), _storageProof, storageRoot_
62:          );

```
*GitHub*: [52](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibTrieProof.sol#L52-L52), [60](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibTrieProof.sol#L60-L62)

```solidity
File: contracts/signal/SignalService.sol

148:         bytes32 signal = signalForChainData(_chainId, _kind, _blockId);

170:             bytes32 signal = signalForChainData(_chainId, _kind, blockId_);

282          bool cacheStateRoot = _hop.cacheOption == CacheOption.CACHE_BOTH
283:             || _hop.cacheOption == CacheOption.CACHE_STATE_ROOT;

290          bool cacheSignalRoot = _hop.cacheOption == CacheOption.CACHE_BOTH
291:             || _hop.cacheOption == CacheOption.CACHE_SIGNAL_ROOT;

```
*GitHub*: [148](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L148-L148), [170](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L170-L170), [282](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L282-L283), [290](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L290-L291)

```solidity
File: contracts/team/TimelockTokenPool.sol

151:         Recipient storage r = recipients[_recipient];

170:         bytes32 hash = keccak256(abi.encodePacked("Withdraw unlocked Taiko token to: ", _to));

171:         address recipient = ECDSA.recover(hash, _sig);

197:         uint128 _amountUnlocked = amountUnlocked / 1e18; // divide first

```
*GitHub*: [151](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L151-L151), [170](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L170-L170), [171](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L171-L171), [197](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L197-L197)

```solidity
File: contracts/team/airdrop/ERC20Airdrop.sol

69           (address delegatee, uint256 nonce, uint256 expiry, uint8 v, bytes32 r, bytes32 s) =
70:              abi.decode(delegationData, (address, uint256, uint256, uint8, bytes32, bytes32));

```
*GitHub*: [69](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L69-L70)

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol

117          uint256 timeBasedAllowance = balance
118:             * (block.timestamp.min(claimEnd + withdrawalWindow) - claimEnd) / withdrawalWindow;

```
*GitHub*: [117](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L117-L118)

```solidity
File: contracts/thirdparty/optimism/rlp/RLPReader.sol

54:          (uint256 listOffset, uint256 listLength, RLPItemType itemType) = _decodeLength(_in);

110:         (uint256 itemOffset, uint256 itemLength, RLPItemType itemType) = _decodeLength(_in);

```
*GitHub*: [54](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L54-L54), [110](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L110-L110)

```solidity
File: contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol

29:          bytes memory key = _getSecureKey(_key);

47:          bytes memory key = _getSecureKey(_key);

```
*GitHub*: [29](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L29-L29), [47](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L47-L47)

```solidity
File: contracts/tokenvault/BaseVault.sol

54:          address selfOnSourceChain = resolve(ctx_.srcChainId, name(), false);

```
*GitHub*: [54](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseVault.sol#L54-L54)

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

55:          (bytes memory data, CanonicalNFT memory ctoken) = _handleMessage(msg.sender, _op);

58           IBridge.Message memory message = IBridge.Message({
59               id: 0, // will receive a new value
60               from: address(0), // will receive a new value
61               srcChainId: 0, // will receive a new value
62               destChainId: _op.destChainId,
63               srcOwner: msg.sender,
64               destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,
65               to: resolve(_op.destChainId, name(), false),
66               refundTo: _op.refundTo,
67               value: msg.value - _op.fee,
68               fee: _op.fee,
69               gasLimit: _op.gasLimit,
70               data: data,
71               memo: _op.memo
72:          });

94           (
95               CanonicalNFT memory ctoken,
96               address from,
97               address to,
98               uint256[] memory tokenIds,
99               uint256[] memory amounts
100:         ) = abi.decode(data, (CanonicalNFT, address, address, uint256[], uint256[]));

111:         address token = _transferTokens(ctoken, to, tokenIds, amounts);

140:         (bytes memory data) = abi.decode(message.data[4:], (bytes));

145:         address token = _transferTokens(ctoken, message.srcOwner, tokenIds, amounts);

304          bytes memory data = abi.encodeCall(
305              BridgedERC1155.init,
306              (owner(), addressManager, _ctoken.addr, _ctoken.chainId, _ctoken.symbol, _ctoken.name)
307:         );

```
*GitHub*: [55](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L55-L55), [58](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L58-L72), [94](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L94-L100), [111](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L111-L111), [140](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L140-L140), [145](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L145-L145), [304](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L304-L307)

```solidity
File: contracts/tokenvault/ERC20Vault.sol

218          (bytes memory data, CanonicalERC20 memory ctoken, uint256 balanceChange) =
219:             _handleMessage(msg.sender, _op.token, _op.to, _op.amount);

221          IBridge.Message memory message = IBridge.Message({
222              id: 0, // will receive a new value
223              from: address(0), // will receive a new value
224              srcChainId: 0, // will receive a new value
225              destChainId: _op.destChainId,
226              srcOwner: msg.sender,
227              destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,
228              to: resolve(_op.destChainId, name(), false),
229              refundTo: _op.refundTo,
230              value: msg.value - _op.fee,
231              fee: _op.fee,
232              gasLimit: _op.gasLimit,
233              data: data,
234              memo: _op.memo
235:         });

259          (CanonicalERC20 memory ctoken, address from, address to, uint256 amount) =
260:             abi.decode(_data, (CanonicalERC20, address, address, uint256));

270:         address token = _transferTokens(ctoken, to, amount);

298:         (bytes memory data) = abi.decode(_message.data[4:], (bytes));

303:         address token = _transferTokens(ctoken, _message.srcOwner, amount);

378:             uint256 _balance = t.balanceOf(address(this));

408          bytes memory data = abi.encodeCall(
409              BridgedERC20.init,
410              (
411                  owner(),
412                  addressManager,
413                  ctoken.addr,
414                  ctoken.chainId,
415                  ctoken.decimals,
416                  ctoken.symbol,
417                  ctoken.name
418              )
419:         );

```
*GitHub*: [218](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L218-L219), [221](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L221-L235), [259](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L259-L260), [270](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L270-L270), [298](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L298-L298), [303](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L303-L303), [378](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L378-L378), [408](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L408-L419)

```solidity
File: contracts/tokenvault/ERC721Vault.sol

42:          (bytes memory data, CanonicalNFT memory ctoken) = _handleMessage(msg.sender, _op);

44           IBridge.Message memory message = IBridge.Message({
45               id: 0, // will receive a new value
46               from: address(0), // will receive a new value
47               srcChainId: 0, // will receive a new value
48               destChainId: _op.destChainId,
49               srcOwner: msg.sender,
50               destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,
51               to: resolve(_op.destChainId, name(), false),
52               refundTo: _op.refundTo,
53               value: msg.value - _op.fee,
54               fee: _op.fee,
55               gasLimit: _op.gasLimit,
56               data: data,
57               memo: _op.memo
58:          });

83           (CanonicalNFT memory ctoken, address from, address to, uint256[] memory tokenIds) =
84:              abi.decode(_data, (CanonicalNFT, address, address, uint256[]));

94:          address token = _transferTokens(ctoken, to, tokenIds);

123:         (bytes memory data) = abi.decode(_message.data[4:], (bytes));

128:         address token = _transferTokens(ctoken, _message.srcOwner, tokenIds);

241          bytes memory data = abi.encodeCall(
242              BridgedERC721.init,
243              (owner(), addressManager, _ctoken.addr, _ctoken.chainId, _ctoken.symbol, _ctoken.name)
244:         );

```
*GitHub*: [42](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L42-L42), [44](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L44-L58), [83](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L83-L84), [94](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L94-L94), [123](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L123-L123), [128](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L128-L128), [241](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L241-L244)

```solidity
File: contracts/verifiers/SgxVerifier.sol

128:         (bool verified,) = IAttestation(automataDcapAttestation).verifyParsedQuote(_attestation);

156:         bytes memory signature = Bytes.slice(_proof.data, 24);

181:         address taikoL1 = resolve("taiko", false);

```
*GitHub*: [128](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L128-L128), [156](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L156-L156), [181](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L181-L181)

</details>





### [G&#x2011;49] Splitting `require()` statements that use `&&` saves gas
See [this issue](https://github.com/code-423n4/2022-01-xdefi-findings/issues/128) which describes the fact that there is a larger deployment gas cost, but with enough runtime calls, the change ends up being cheaper by **3 gas**

*There are 4 instances of this issue:*

```solidity
File: contracts/L1/libs/LibProving.sol

224:                 assert(ts.validityBond == 0 && ts.contestBond == 0 && ts.contester == address(0));

```
*GitHub*: [224](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L224-L224)

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

77           require(
78               localEnclaveReport.reserved3.length == 96 && localEnclaveReport.reserved4.length == 60
79                   && localEnclaveReport.reportData.length == 64,
80               "local QE report has wrong length"
81:          );

82           require(
83               pckSignedQeReport.reserved3.length == 96 && pckSignedQeReport.reserved4.length == 60
84                   && pckSignedQeReport.reportData.length == 64,
85               "QE report has wrong length"
86:          );

94           require(
95               v3Quote.v3AuthData.ecdsa256BitSignature.length == 64
96                   && v3Quote.v3AuthData.ecdsaAttestationKey.length == 64
97                   && v3Quote.v3AuthData.qeReportSignature.length == 64,
98               "Invalid ECDSA signature format"
99:          );

```
*GitHub*: [77](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L77-L81), [82](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L82-L86), [94](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L94-L99)



### [G&#x2011;50] Split `revert` checks to save gas
Splitting the conditions into two separate checks [saves](https://gist.github.com/IllIllI000/7e25b0fca6bd9d57d9b9bcb9d2018959) **2 gas**

*There are 26 instances of this issue:*

<details>
<summary>see instances</summary>


```solidity
File: contracts/L1/hooks/AssignmentHook.sol

81           if (
82               block.timestamp > assignment.expiry
83                   || assignment.metaHash != 0 && _blk.metaHash != assignment.metaHash
84                   || assignment.parentMetaHash != 0 && _meta.parentMetaHash != assignment.parentMetaHash
85                   || assignment.maxBlockId != 0 && _meta.id > assignment.maxBlockId
86                   || assignment.maxProposedIn != 0 && block.number > assignment.maxProposedIn
87           ) {
88               revert HOOK_ASSIGNMENT_EXPIRED();
89:          }

```
*GitHub*: [81](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L81-L89)

```solidity
File: contracts/L1/libs/LibProposing.sol

195          if (meta_.txListByteSize == 0 || meta_.txListByteSize > _config.blockMaxTxListBytes) {
196              revert L1_TXLIST_SIZE();
197:         }

```
*GitHub*: [195](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L195-L197)

```solidity
File: contracts/L1/libs/LibProving.sol

105          if (_tran.parentHash == 0 || _tran.blockHash == 0 || _tran.stateRoot == 0) {
106              revert L1_INVALID_TRANSITION();
107:         }

111          if (_meta.id <= b.lastVerifiedBlockId || _meta.id >= b.numBlocks) {
112              revert L1_INVALID_BLOCK_ID();
113:         }

121          if (blk.blockId != _meta.id || blk.metaHash != keccak256(abi.encode(_meta))) {
122              revert L1_BLOCK_MISMATCH();
123:         }

134          if (_proof.tier == 0 || _proof.tier < _meta.minTier || _proof.tier < ts.tier) {
135              revert L1_INVALID_TIER();
136:         }

```
*GitHub*: [105](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L105-L107), [111](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L111-L113), [121](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L121-L123), [134](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L134-L136)

```solidity
File: contracts/L1/libs/LibUtils.sol

34           if (_blockId < b.lastVerifiedBlockId || _blockId >= b.numBlocks) {
35               revert L1_INVALID_BLOCK_ID();
36:          }

```
*GitHub*: [34](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibUtils.sol#L34-L36)

```solidity
File: contracts/L1/provers/Guardians.sol

63           if (_newGuardians.length < MIN_NUM_GUARDIANS || _newGuardians.length > type(uint8).max) {
64               revert INVALID_GUARDIAN_SET();
65:          }

68           if (_minGuardians < (_newGuardians.length + 1) >> 1 || _minGuardians > _newGuardians.length)
69           {
70               revert INVALID_MIN_GUARDIANS();
71:          }

```
*GitHub*: [63](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L63-L65), [68](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L68-L71)

```solidity
File: contracts/L2/CrossChainOwned.sol

46           if (ctx.srcChainId != ownerChainId || ctx.from != owner()) {
47               revert XCO_PERMISSION_DENIED();
48:          }

70           if (_ownerChainId == 0 || _ownerChainId == block.chainid) {
71               revert XCO_INVALID_OWNER_CHAINID();
72:          }

```
*GitHub*: [46](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L46-L48), [70](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L70-L72)

```solidity
File: contracts/L2/TaikoL2.sol

82           if (block.chainid <= 1 || block.chainid > type(uint64).max) {
83               revert L2_INVALID_CHAIN_ID();
84:          }

116          if (
117              _l1BlockHash == 0 || _l1StateRoot == 0 || _l1BlockId == 0
118                  || (block.number != 1 && _parentGasUsed == 0)
119          ) {
120              revert L2_INVALID_PARAM();
121:         }

```
*GitHub*: [82](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L82-L84), [116](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L116-L121)

```solidity
File: contracts/bridge/Bridge.sol

124          if (_message.srcOwner == address(0) || _message.destOwner == address(0)) {
125              revert B_INVALID_USER();
126:         }

405          if (ctx_.msgHash == 0 || ctx_.msgHash == bytes32(PLACEHOLDER)) {
406              revert B_INVALID_CONTEXT();
407:         }

```
*GitHub*: [124](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L124-L126), [405](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L405-L407)

```solidity
File: contracts/libs/Lib4844.sol

57           if (uint256(first) != FIELD_ELEMENTS_PER_BLOB || uint256(second) != BLS_MODULUS) {
58               revert EVAL_FAILED_2();
59:          }

```
*GitHub*: [57](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/Lib4844.sol#L57-L59)

```solidity
File: contracts/signal/SignalService.sol

114                  if (hop.chainId == 0 || hop.chainId == block.chainid) {
115                      revert SS_INVALID_MID_HOP_CHAINID();
116:                 }

131          if (value == 0 || value != _loadSignalValue(address(this), signal)) {
132              revert SS_SIGNAL_NOT_FOUND();
133:         }

```
*GitHub*: [114](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L114-L116), [131](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L131-L133)

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol

40           if (claimEnd > block.timestamp || claimEnd + withdrawalWindow < block.timestamp) {
41               revert WITHDRAWALS_NOT_ONGOING();
42:          }

```
*GitHub*: [40](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L40-L42)

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol

34           if (
35               merkleRoot == 0x0 || claimStart == 0 || claimEnd == 0 || claimStart > block.timestamp
36                   || claimEnd < block.timestamp
37:          ) revert CLAIM_NOT_ONGOING();

```
*GitHub*: [34](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L34-L37)

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

108:         if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

```
*GitHub*: [108](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L108-L108)

```solidity
File: contracts/tokenvault/ERC20Vault.sol

158          if (_btokenNew == address(0) || bridgedToCanonical[_btokenNew].addr != address(0)) {
159              revert VAULT_INVALID_NEW_BTOKEN();
160:         }

174              if (
175                  ctoken.decimals != _ctoken.decimals
176                      || keccak256(bytes(ctoken.symbol)) != keccak256(bytes(_ctoken.symbol))
177                      || keccak256(bytes(ctoken.name)) != keccak256(bytes(_ctoken.name))
178:             ) revert VAULT_CTOKEN_MISMATCH();

267:         if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

```
*GitHub*: [158](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L158-L160), [174](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L174-L178), [267](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L267-L267)

```solidity
File: contracts/tokenvault/ERC721Vault.sol

91:          if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

```
*GitHub*: [91](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L91-L91)

```solidity
File: contracts/tokenvault/LibBridgedToken.sol

20           if (
21               _srcToken == address(0) || _srcChainId == 0 || _srcChainId == block.chainid
22                   || bytes(_symbol).length == 0 || bytes(_name).length == 0
23           ) {
24               revert BTOKEN_INVALID_PARAMS();
25:          }

```
*GitHub*: [20](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L20-L25)

</details>





### [G&#x2011;51] Update OpenZeppelin dependency to save gas
Every release contains new gas optimizations. Use the latest version to take advantage of this

*There are 47 instances of this issue:*

<details>
<summary>see instances</summary>


```solidity
File: contracts/L1/TaikoToken.sol

4:   import "@openzeppelin/contracts-upgradeable/token/ERC20/ERC20Upgradeable.sol";

5:   import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20SnapshotUpgradeable.sol";

6:   import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20VotesUpgradeable.sol";

```
*GitHub*: [4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoToken.sol#L4-L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoToken.sol#L5-L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoToken.sol#L6-L6)

```solidity
File: contracts/L1/gov/TaikoGovernor.sol

4:   import "@openzeppelin/contracts-upgradeable/governance/GovernorUpgradeable.sol";

5    import
6:       "@openzeppelin/contracts-upgradeable/governance/compatibility/GovernorCompatibilityBravoUpgradeable.sol";

7:   import "@openzeppelin/contracts-upgradeable/governance/extensions/GovernorVotesUpgradeable.sol";

8    import
9:       "@openzeppelin/contracts-upgradeable/governance/extensions/GovernorVotesQuorumFractionUpgradeable.sol";

10   import
11:      "@openzeppelin/contracts-upgradeable/governance/extensions/GovernorTimelockControlUpgradeable.sol";

```
*GitHub*: [4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L4-L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L5-L6), [7](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L7-L7), [8](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L8-L9), [10](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L10-L11)

```solidity
File: contracts/L1/gov/TaikoTimelockController.sol

4:   import "@openzeppelin/contracts-upgradeable/governance/TimelockControllerUpgradeable.sol";

```
*GitHub*: [4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L4-L4)

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

4:   import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

5:   import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";

```
*GitHub*: [4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L4-L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L5-L5)

```solidity
File: contracts/L1/libs/LibProposing.sol

4:   import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

```
*GitHub*: [4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L4-L4)

```solidity
File: contracts/L1/libs/LibProving.sol

4:   import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

```
*GitHub*: [4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L4-L4)

```solidity
File: contracts/L1/libs/LibVerifying.sol

4:   import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

```
*GitHub*: [4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L4-L4)

```solidity
File: contracts/L2/CrossChainOwned.sol

4:   import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

```
*GitHub*: [4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L4-L4)

```solidity
File: contracts/L2/TaikoL2.sol

4:   import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

5:   import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";

```
*GitHub*: [4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L4-L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L5-L5)

```solidity
File: contracts/bridge/Bridge.sol

4:   import "@openzeppelin/contracts/utils/Address.sol";

```
*GitHub*: [4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L4-L4)

```solidity
File: contracts/common/AddressResolver.sol

4:   import "@openzeppelin/contracts-upgradeable/proxy/utils/Initializable.sol";

```
*GitHub*: [4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressResolver.sol#L4-L4)

```solidity
File: contracts/common/EssentialContract.sol

4:   import "@openzeppelin/contracts/proxy/utils/UUPSUpgradeable.sol";

5:   import "@openzeppelin/contracts-upgradeable/access/Ownable2StepUpgradeable.sol";

```
*GitHub*: [4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L4-L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L5-L5)

```solidity
File: contracts/libs/LibAddress.sol

4:   import "@openzeppelin/contracts/utils/Address.sol";

5:   import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol";

```
*GitHub*: [4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibAddress.sol#L4-L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibAddress.sol#L5-L5)

```solidity
File: contracts/signal/SignalService.sol

4:   import "@openzeppelin/contracts/utils/math/SafeCast.sol";

```
*GitHub*: [4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L4-L4)

```solidity
File: contracts/team/TimelockTokenPool.sol

4:   import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol";

5:   import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

6:   import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";

```
*GitHub*: [4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L4-L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L5-L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L6-L6)

```solidity
File: contracts/team/airdrop/ERC20Airdrop.sol

4:   import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

5:   import "@openzeppelin/contracts/governance/utils/IVotes.sol";

```
*GitHub*: [4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L4-L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L5-L5)

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol

4:   import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

```
*GitHub*: [4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L4-L4)

```solidity
File: contracts/team/airdrop/ERC721Airdrop.sol

4:   import "@openzeppelin/contracts/token/ERC721/IERC721.sol";

```
*GitHub*: [4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L4-L4)

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol

4:   import "@openzeppelin/contracts/utils/cryptography/MerkleProof.sol";

```
*GitHub*: [4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L4-L4)

```solidity
File: contracts/tokenvault/BaseVault.sol

5:   import "@openzeppelin/contracts/proxy/ERC1967/ERC1967Proxy.sol";

```
*GitHub*: [5](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseVault.sol#L5-L5)

```solidity
File: contracts/tokenvault/BridgedERC1155.sol

4:   import "@openzeppelin/contracts/utils/Strings.sol";

5:   import "@openzeppelin/contracts-upgradeable/token/ERC1155/ERC1155Upgradeable.sol";

```
*GitHub*: [4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L4-L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L5-L5)

```solidity
File: contracts/tokenvault/BridgedERC20.sol

5:   import "@openzeppelin/contracts/utils/Strings.sol";

6:   import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20SnapshotUpgradeable.sol";

7:   import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20VotesUpgradeable.sol";

```
*GitHub*: [5](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L5-L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L6-L6), [7](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L7-L7)

```solidity
File: contracts/tokenvault/BridgedERC721.sol

4:   import "@openzeppelin/contracts-upgradeable/token/ERC721/ERC721Upgradeable.sol";

5:   import "@openzeppelin/contracts/utils/Strings.sol";

```
*GitHub*: [4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L4-L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L5-L5)

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

4:   import "@openzeppelin/contracts/token/ERC1155/IERC1155.sol";

```
*GitHub*: [4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L4-L4)

```solidity
File: contracts/tokenvault/ERC20Vault.sol

4:   import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

6:   import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";

```
*GitHub*: [4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L4-L4), [6](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L6-L6)

```solidity
File: contracts/tokenvault/ERC721Vault.sol

4:   import "@openzeppelin/contracts/token/ERC721/IERC721.sol";

5:   import "@openzeppelin/contracts/token/ERC721/IERC721Receiver.sol";

```
*GitHub*: [4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L4-L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L5-L5)

```solidity
File: contracts/tokenvault/LibBridgedToken.sol

4:   import "@openzeppelin/contracts/utils/Strings.sol";

```
*GitHub*: [4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L4-L4)

```solidity
File: contracts/verifiers/SgxVerifier.sol

4:   import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol";

```
*GitHub*: [4](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L4-L4)

</details>





### [G&#x2011;52] Use bitwise operators rather than boolean operators, to save gas
`((a != b) || (c != d))` => `((a ^ b) | (c ^ d))`

*There are 8 instances of this issue:*

```solidity
File: contracts/L1/libs/LibProving.sol

121:         if (blk.blockId != _meta.id || blk.metaHash != keccak256(abi.encode(_meta))) {

```
*GitHub*: [121](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L121-L121)

```solidity
File: contracts/L2/CrossChainOwned.sol

46:          if (ctx.srcChainId != ownerChainId || ctx.from != owner()) {

```
*GitHub*: [46](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L46-L46)

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

237:         if (pckCpuSvns.length != CPUSVN_LENGTH || tcbCpuSvns.length != CPUSVN_LENGTH) {

```
*GitHub*: [237](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L237-L237)

```solidity
File: contracts/automata-attestation/utils/RsaVerify.sol

137:         if (decipher[0] != 0 || decipher[1] != 0x01) {

168              decipher[3 + paddingLen + digestAlgoWithParamLen] != 0x04
169:                 || decipher[4 + paddingLen + digestAlgoWithParamLen] != 0x20

270:         if (decipher[0] != 0 || decipher[1] != 0x01) {

```
*GitHub*: [137](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L137-L137), [168](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L168-L169), [270](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L270-L270)

```solidity
File: contracts/libs/Lib4844.sol

57:          if (uint256(first) != FIELD_ELEMENTS_PER_BLOB || uint256(second) != BLS_MODULUS) {

```
*GitHub*: [57](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/Lib4844.sol#L57-L57)

```solidity
File: contracts/tokenvault/ERC20Vault.sol

175                  ctoken.decimals != _ctoken.decimals
176:                     || keccak256(bytes(ctoken.symbol)) != keccak256(bytes(_ctoken.symbol))

```
*GitHub*: [175](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L175-L176)



### [G&#x2011;53] Use custom errors rather than `revert()`/`require()` strings to save gas
Custom errors are available from solidity version 0.8.4. Custom errors save [**~50 gas**](https://gist.github.com/IllIllI000/ad1bd0d29a0101b25e57c293b4b0c746) each time they're hit by [avoiding having to allocate and store the revert string](https://blog.soliditylang.org/2021/04/21/custom-errors/#errors-in-depth). Not defining the strings also save deployment gas

*There are 17 instances of this issue:*

```solidity
File: contracts/thirdparty/optimism/rlp/RLPReader.sol

37           require(
38               _in.length > 0,
39               "RLPReader: length of an RLP item must be greater than zero to be decodable"
40:          );

56           require(
57               itemType == RLPItemType.LIST_ITEM,
58               "RLPReader: decoded item type for list is not a list item"
59:          );

61           require(
62               listOffset + listLength == _in.length,
63               "RLPReader: list item has an invalid data remainder"
64:          );

112          require(
113              itemType == RLPItemType.DATA_ITEM,
114              "RLPReader: decoded item type for bytes is not a data item"
115:         );

117          require(
118              _in.length == itemOffset + itemLength,
119              "RLPReader: bytes value contains an invalid remainder"
120:         );

152          require(
153              _in.length > 0,
154              "RLPReader: length of an RLP item must be greater than zero to be decodable"
155:         );

172              require(
173                  _in.length > strLen,
174                  "RLPReader: length of content must be greater than string length (short string)"
175:             );

182              require(
183                  strLen != 1 || firstByteOfContent >= 0x80,
184                  "RLPReader: invalid prefix, single byte < 0x80 are not prefixed (short string)"
185:             );

192              require(
193                  _in.length > lenOfStrLen,
194                  "RLPReader: length of content must be > than length of string length (long string)"
195:             );

202              require(
203                  firstByteOfContent != 0x00,
204                  "RLPReader: length of content must not have any leading zeros (long string)"
205:             );

212              require(
213                  strLen > 55,
214                  "RLPReader: length of content must be greater than 55 bytes (long string)"
215:             );

217              require(
218                  _in.length > lenOfStrLen + strLen,
219                  "RLPReader: length of content must be greater than total length (long string)"
220:             );

228              require(
229                  _in.length > listLen,
230                  "RLPReader: length of content must be greater than list length (short list)"
231:             );

238              require(
239                  _in.length > lenOfListLen,
240                  "RLPReader: length of content must be > than length of list length (long list)"
241:             );

248              require(
249                  firstByteOfContent != 0x00,
250                  "RLPReader: length of content must not have any leading zeros (long list)"
251:             );

258              require(
259                  listLen > 55,
260                  "RLPReader: length of content must be greater than 55 bytes (long list)"
261:             );

263              require(
264                  _in.length > lenOfListLen + listLen,
265                  "RLPReader: length of content must be greater than total length (long list)"
266:             );

```
*GitHub*: [37](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L37-L40), [56](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L56-L59), [61](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L61-L64), [112](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L112-L115), [117](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L117-L120), [152](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L152-L155), [172](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L172-L175), [182](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L182-L185), [192](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L192-L195), [202](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L202-L205), [212](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L212-L215), [217](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L217-L220), [228](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L228-L231), [238](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L238-L241), [248](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L248-L251), [258](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L258-L261), [263](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L263-L266)



### [G&#x2011;54] Use gas-efficient version of `min()`/`max()`
`a > b ? a : b` -> `xor(a, mul(xor(a, b), gt(b, a)))`

*There are 2 instances of this issue:*

```solidity
File: contracts/libs/LibMath.sol

12       function min(uint256 _a, uint256 _b) internal pure returns (uint256) {
13           return _a > _b ? _b : _a;
14:      }

20       function max(uint256 _a, uint256 _b) internal pure returns (uint256) {
21           return _a > _b ? _a : _b;
22:      }

```
*GitHub*: [12](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibMath.sol#L12-L14), [20](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibMath.sol#L20-L22)



### [G&#x2011;55] Use internal functions inside modifiers to save gas
This will cost more runtime gas, but will reduce deployment gas when the modifier is called more than once as is the case for the examples below. Most projects do not make this trade-off, but it's available nonetheless.

*There is one instance of this issue:*

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

60       modifier onlyOwner() {
61           require(msg.sender == owner, "onlyOwner");
62           _;
63:      }

```
*GitHub*: [60](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L60-L63)



### [G&#x2011;56] Use short-circuit evaluation to avoid reading state variables
By evaluating expressions involving constants, literals, and local variables before ones involving storage variables, you can avoid unnecessarily reading the storage variables in the unhappy path.

*There are 5 instances of this issue:*

```solidity
File: contracts/L1/libs/LibProving.sol

/// @audit move the expression involving `ts` to the right
164:                 bool isContesting = _proof.tier == ts.tier && tier.contestBond != 0;

/// @audit move the expression involving `blk` to the right
192:             bool returnLivenessBond = blk.livenessBond > 0 && _proof.data.length == 32

/// @audit move the expression involving `blk` to the right
192              bool returnLivenessBond = blk.livenessBond > 0 && _proof.data.length == 32
193:                 && bytes32(_proof.data) == RETURN_LIVENESS_BOND;

/// @audit move the expression involving `_ts` to the right
419:         if (_tid == 1 && _ts.tier == 0 && inProvingWindow) {

```
*GitHub*: [164](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L164-L164), [192](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L192-L192), [192](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L192-L193), [419](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L419-L419)

```solidity
File: contracts/L2/CrossChainOwned.sol

/// @audit move the expression involving `ownerChainId` to the right
46:          if (ctx.srcChainId != ownerChainId || ctx.from != owner()) {

```
*GitHub*: [46](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L46-L46)



### [G&#x2011;57] Using `msg` globals directly, rather than caching the value, saves gas
Using the [global](https://docs.soliditylang.org/en/v0.8.14/cheatsheet.html#global-variables) directly saves **5 [gas](https://gist.github.com/IllIllI000/0a38d74d0af20412471a43f1e4fcf8be)**

*There are 3 instances of this issue:*

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

/// @audit taikoL1Address
94:          bytes32 hash = hashAssignment(assignment, taikoL1Address, _meta.blobHash);

/// @audit taikoL1Address
102:         tko.transferFrom(_blk.assignedProver, taikoL1Address, _blk.livenessBond);

/// @audit taikoL1Address
126:             taikoL1Address.sendEther(address(this).balance);

```
*GitHub*: [94](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L94-L94), [102](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L102-L102), [126](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L126-L126)



### [G&#x2011;58] Using `private` rather than `public`, saves gas
For constants, the values can be read from the verified contract source code, or if there are multiple values there can be a single getter function that [returns a tuple](https://github.com/code-423n4/2022-08-frax/blob/90f55a9ce4e25bceed3a74290b854341d8de6afa/src/contracts/FraxlendPair.sol#L156-L178) of the values of all currently-public constants. Saves **3406-3606 gas** in deployment gas due to the compiler not having to create non-payable getter functions for deployment calldata, not having to store the bytes of the value outside of where it's used, and not adding another entry to the method ID table

*There are 52 instances of this issue:*

<details>
<summary>see instances</summary>


```solidity
File: contracts/L1/TaikoL1.sol

24:      TaikoData.State public state;

```
*GitHub*: [24](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L24-L24)

```solidity
File: contracts/L2/CrossChainOwned.sol

16:      uint64 public ownerChainId;

19:      uint64 public nextTxId;

```
*GitHub*: [16](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L16-L16), [19](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L19-L19)

```solidity
File: contracts/L2/TaikoL2EIP1559Configurable.sol

11:      Config public customConfig;

```
*GitHub*: [11](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L11-L11)

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

25:      ISigVerifyLib public immutable sigVerifyLib;

26:      IPEMCertChainLib public immutable pemCertLib;

49:      mapping(string fmspc => TCBInfoStruct.TCBInfo tcbInfo) public tcbInfo;

50:      EnclaveIdStruct.EnclaveId public qeIdentity;

52:      address public owner;

```
*GitHub*: [25](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L25-L25), [26](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L26-L26), [49](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L49-L49), [50](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L50-L50), [52](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L52-L52)

```solidity
File: contracts/bridge/Bridge.sol

31:      uint128 public nextMessageId;

35:      mapping(bytes32 msgHash => Status status) public messageStatus;

42:      mapping(address addr => bool banned) public addressBanned;

46:      mapping(bytes32 msgHash => ProofReceipt receipt) public proofReceipt;

```
*GitHub*: [31](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L31-L31), [35](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L35-L35), [42](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L42-L42), [46](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L46-L46)

```solidity
File: contracts/common/AddressResolver.sol

13:      address public addressManager;

```
*GitHub*: [13](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressResolver.sol#L13-L13)

```solidity
File: contracts/signal/SignalService.sol

17:      mapping(uint64 chainId => mapping(bytes32 kind => uint64 blockId)) public topBlockId;

21:      mapping(address addr => bool authorized) public isAuthorized;

```
*GitHub*: [17](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L17-L17), [21](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L21-L21)

```solidity
File: contracts/team/TimelockTokenPool.sol

59:      address public taikoToken;

62:      address public costToken;

65:      address public sharedVault;

68:      uint128 public totalAmountGranted;

71:      uint128 public totalAmountVoided;

74:      uint128 public totalAmountWithdrawn;

77:      uint128 public totalCostPaid;

80:      mapping(address recipient => Recipient receipt) public recipients;

```
*GitHub*: [59](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L59-L59), [62](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L62-L62), [65](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L65-L65), [68](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L68-L68), [71](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L71-L71), [74](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L74-L74), [77](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L77-L77), [80](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L80-L80)

```solidity
File: contracts/team/airdrop/ERC20Airdrop.sol

13:      address public token;

16:      address public vault;

```
*GitHub*: [13](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L13-L13), [16](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L16-L16)

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol

16:      address public token;

19:      address public vault;

22:      mapping(address addr => uint256 amountClaimed) public claimedAmount;

25:      mapping(address addr => uint256 amountWithdrawn) public withdrawnAmount;

28:      uint64 public withdrawalWindow;

```
*GitHub*: [16](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L16-L16), [19](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L19-L19), [22](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L22-L22), [25](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L25-L25), [28](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L28-L28)

```solidity
File: contracts/team/airdrop/ERC721Airdrop.sol

11:      address public token;

14:      address public vault;

```
*GitHub*: [11](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L11-L11), [14](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L14-L14)

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol

12:      mapping(bytes32 hash => bool claimed) public isClaimed;

15:      bytes32 public merkleRoot;

18:      uint64 public claimStart;

21:      uint64 public claimEnd;

```
*GitHub*: [12](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L12-L12), [15](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L15-L15), [18](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L18-L18), [21](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L21-L21)

```solidity
File: contracts/thirdparty/solmate/LibFixedPointMath.sol

7:       uint128 public constant MAX_EXP_INPUT = 135_305_999_368_893_231_588;

8:       uint256 public constant SCALING_FACTOR = 1e18; // For fixed point representation factor

```
*GitHub*: [7](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L7-L7), [8](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L8-L8)

```solidity
File: contracts/tokenvault/BridgedERC1155.sol

16:      address public srcToken;

19:      uint256 public srcChainId;

```
*GitHub*: [16](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L16-L16), [19](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L19-L19)

```solidity
File: contracts/tokenvault/BridgedERC20.sol

22:      address public srcToken;

27:      uint256 public srcChainId;

30:      address public snapshooter;

```
*GitHub*: [22](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L22-L22), [27](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L27-L27), [30](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L30-L30)

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol

11:      address public migratingAddress;

14:      bool public migratingInbound;

```
*GitHub*: [11](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L11-L11), [14](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L14-L14)

```solidity
File: contracts/tokenvault/BridgedERC721.sol

14:      address public srcToken;

17:      uint256 public srcChainId;

```
*GitHub*: [14](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L14-L14), [17](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L17-L17)

```solidity
File: contracts/tokenvault/ERC20Vault.sol

45:      mapping(address btoken => CanonicalERC20 canonical) public bridgedToCanonical;

49:      mapping(uint256 chainId => mapping(address ctoken => address btoken)) public canonicalToBridged;

52:      mapping(address btoken => bool blacklisted) public btokenBlacklist;

```
*GitHub*: [45](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L45-L45), [49](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L49-L49), [52](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L52-L52)

```solidity
File: contracts/tokenvault/adapters/USDCAdapter.sol

31:      IUSDC public usdc;

```
*GitHub*: [31](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L31-L31)

</details>





### [G&#x2011;59] Yul variable is only used once
If the variable is only accessed once, it's cheaper to use the assigned value directly that one time, and save the **3 gas** the extra stack assignment would spend

*There are 3 instances of this issue:*

```solidity
File: contracts/automata-attestation/utils/BytesUtils.sol

/// @audit mask
266          assembly {
267              let mask := not(sub(exp(256, sub(32, len)), 1))
268              ret := and(mload(add(add(self, 32), idx)), mask)
269:         }

```
*GitHub*: [266](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L266-L269)

```solidity
File: contracts/automata-attestation/utils/SHA1.sol

/// @audit ptr
/// @audit mask
12           assembly {
13               // Get a safe scratch location
14               let scratch := mload(0x40)
15   
16               // Get the data length, and point data at the first byte
17               let len := mload(data)
18               data := add(data, 32)
19   
20               // Find the length after padding
21               let totallen := add(and(add(len, 1), 0xFFFFFFFFFFFFFFC0), 64)
22               switch lt(sub(totallen, len), 9)
23               case 1 { totallen := add(totallen, 64) }
24   
25               let h := 0x6745230100EFCDAB890098BADCFE001032547600C3D2E1F0
26   
27               function readword(ptr, off, count) -> result {
28                   result := 0
29                   if lt(off, count) {
30                       result := mload(add(ptr, off))
31                       count := sub(count, off)
32                       if lt(count, 32) {
33                           let mask := not(sub(exp(256, sub(32, count)), 1))
34                           result := and(result, mask)
35                       }
36                   }
37               }
38   
39               for { let i := 0 } lt(i, totallen) { i := add(i, 64) } {
40                   mstore(scratch, readword(data, i, len))
41                   mstore(add(scratch, 32), readword(data, add(i, 32), len))
42   
43                   // If we loaded the last byte, store the terminator byte
44                   switch lt(sub(len, i), 64)
45                   case 1 { mstore8(add(scratch, sub(len, i)), 0x80) }
46   
47                   // If this is the last block, store the length
48                   switch eq(i, sub(totallen, 64))
49                   case 1 { mstore(add(scratch, 32), or(mload(add(scratch, 32)), mul(len, 8))) }
50   
51                   // Expand the 16 32-bit words into 80
52                   for { let j := 64 } lt(j, 128) { j := add(j, 12) } {
53                       let temp :=
54                           xor(
55                               xor(mload(add(scratch, sub(j, 12))), mload(add(scratch, sub(j, 32)))),
56                               xor(mload(add(scratch, sub(j, 56))), mload(add(scratch, sub(j, 64))))
57                           )
58                       temp :=
59                           or(
60                               and(
61                                   mul(temp, 2),
62                                   0xFFFFFFFEFFFFFFFEFFFFFFFEFFFFFFFEFFFFFFFEFFFFFFFEFFFFFFFEFFFFFFFE
63                               ),
64                               and(
65                                   div(temp, 0x80000000),
66                                   0x0000000100000001000000010000000100000001000000010000000100000001
67                               )
68                           )
69                       mstore(add(scratch, j), temp)
70                   }
71                   for { let j := 128 } lt(j, 320) { j := add(j, 24) } {
72                       let temp :=
73                           xor(
74                               xor(mload(add(scratch, sub(j, 24))), mload(add(scratch, sub(j, 64)))),
75                               xor(mload(add(scratch, sub(j, 112))), mload(add(scratch, sub(j, 128))))
76                           )
77                       temp :=
78                           or(
79                               and(
80                                   mul(temp, 4),
81                                   0xFFFFFFFCFFFFFFFCFFFFFFFCFFFFFFFCFFFFFFFCFFFFFFFCFFFFFFFCFFFFFFFC
82                               ),
83                               and(
84                                   div(temp, 0x40000000),
85                                   0x0000000300000003000000030000000300000003000000030000000300000003
86                               )
87                           )
88                       mstore(add(scratch, j), temp)
89                   }
90   
91                   let x := h
92                   let f := 0
93                   let k := 0
94                   for { let j := 0 } lt(j, 80) { j := add(j, 1) } {
95                       switch div(j, 20)
96                       case 0 {
97                           // f = d xor (b and (c xor d))
98                           f := xor(div(x, 0x100000000000000000000), div(x, 0x10000000000))
99                           f := and(div(x, 0x1000000000000000000000000000000), f)
100                          f := xor(div(x, 0x10000000000), f)
101                          k := 0x5A827999
102                      }
103                      case 1 {
104                          // f = b xor c xor d
105                          f :=
106                              xor(
107                                  div(x, 0x1000000000000000000000000000000),
108                                  div(x, 0x100000000000000000000)
109                              )
110                          f := xor(div(x, 0x10000000000), f)
111                          k := 0x6ED9EBA1
112                      }
113                      case 2 {
114                          // f = (b and c) or (d and (b or c))
115                          f :=
116                              or(
117                                  div(x, 0x1000000000000000000000000000000),
118                                  div(x, 0x100000000000000000000)
119                              )
120                          f := and(div(x, 0x10000000000), f)
121                          f :=
122                              or(
123                                  and(
124                                      div(x, 0x1000000000000000000000000000000),
125                                      div(x, 0x100000000000000000000)
126                                  ),
127                                  f
128                              )
129                          k := 0x8F1BBCDC
130                      }
131                      case 3 {
132                          // f = b xor c xor d
133                          f :=
134                              xor(
135                                  div(x, 0x1000000000000000000000000000000),
136                                  div(x, 0x100000000000000000000)
137                              )
138                          f := xor(div(x, 0x10000000000), f)
139                          k := 0xCA62C1D6
140                      }
141                      // temp = (a leftrotate 5) + f + e + k + w[i]
142                      let temp := and(div(x, 0x80000000000000000000000000000000000000000000000), 0x1F)
143                      temp :=
144                          or(and(div(x, 0x800000000000000000000000000000000000000), 0xFFFFFFE0), temp)
145                      temp := add(f, temp)
146                      temp := add(and(x, 0xFFFFFFFF), temp)
147                      temp := add(k, temp)
148                      temp :=
149                          add(
150                              div(
151                                  mload(add(scratch, mul(j, 4))),
152                                  0x100000000000000000000000000000000000000000000000000000000
153                              ),
154                              temp
155                          )
156                      x :=
157                          or(
158                              div(x, 0x10000000000),
159                              mul(temp, 0x10000000000000000000000000000000000000000)
160                          )
161                      x :=
162                          or(
163                              and(x, 0xFFFFFFFF00FFFFFFFF000000000000FFFFFFFF00FFFFFFFF),
164                              mul(
165                                  or(
166                                      and(div(x, 0x4000000000000), 0xC0000000),
167                                      and(div(x, 0x400000000000000000000), 0x3FFFFFFF)
168                                  ),
169                                  0x100000000000000000000
170                              )
171                          )
172                  }
173  
174                  h := and(add(h, x), 0xFFFFFFFF00FFFFFFFF00FFFFFFFF00FFFFFFFF00FFFFFFFF)
175              }
176              ret :=
177                  mul(
178                      or(
179                          or(
180                              or(
181                                  or(
182                                      and(div(h, 0x100000000), 0xFFFFFFFF00000000000000000000000000000000),
183                                      and(div(h, 0x1000000), 0xFFFFFFFF000000000000000000000000)
184                                  ),
185                                  and(div(h, 0x10000), 0xFFFFFFFF0000000000000000)
186                              ),
187                              and(div(h, 0x100), 0xFFFFFFFF00000000)
188                          ),
189                          and(h, 0xFFFFFFFF)
190                      ),
191                      0x1000000000000000000000000
192                  )
193:         }

```
*GitHub*: [12](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SHA1.sol#L12-L193), [12](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SHA1.sol#L12-L193)
