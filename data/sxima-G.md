|Number|Issue|Instances|Average Gas Saved|
|-|:-|:-:|:-:|
| [GAS&#x2011;001](#GAS001-++i-costs-less-gas-than-i++/i-+=-1-especially-when-its-used-in-for-loops---i/i---too) | `++i` costs less gas than `i++`/`i += 1`, especially when it's used in `for`-loops (`--i`/`i--` too) | 13 | 78 |
| [GAS&#x2011;002](#GAS002-++i/i++-should-be-unchecked{++i}/unchecked{i++}-when-it-is-not-possible-for-them-to-overflow) | `++i`/`i++` should be `unchecked{++i}`/`unchecked{i++}` when it is not possible for them to overflow | 40 | 2,400 |
| [GAS&#x2011;003](#GAS003-operator->=/<=-costs-less-gas-than-operator->/<) | Operator `>=`/`<=` costs less gas than operator `>`/`<` | 40 | 120 |
| [GAS&#x2011;004](#GAS004-abiencode-is-less-efficient-than-abiencodepacked) | `abi.encode()` is less efficient than `abi.encodePacked()` | 18 | - |
| [GAS&#x2011;005](#GAS005-cache-addressthis-when-used-more-than-twice) | Cache address(this) when used more than twice | 2 | - |
| [GAS&#x2011;006](#GAS006-use-solady-library-where-possible-to-save-gas) | Use solady library where possible to save gas | 16 | 16,000 |
| [GAS&#x2011;007](#GAS007-assembly-let-var-only-used-on-once) | Assembly let var only used on once | 9 | - |
| [GAS&#x2011;008](#GAS008-assigning-state-variables-directly-with-named-struct-constructors-wastes-gas) | Assigning state variables directly with named struct constructors wastes gas | 16 | 448 |
| [GAS&#x2011;009](#GAS009-avoid-contract-existence-checks-by-using-low-level-calls) | Avoid contract existence checks by using low-level calls | 40 | 4,000 |
| [GAS&#x2011;010](#GAS010-avoid-unnecessary-public-variables) | Avoid Unnecessary Public Variables | 40 | 880,000 |
| [GAS&#x2011;011](#GAS011-avoid-updating-storage-when-the-value-hasnt-changed) | Avoid updating storage when the value hasn't changed | 6 | 10,200 |
| [GAS&#x2011;012](#GAS012-reduce-zero-to-non-zero-storage-updates-when-you-can) | Reduce Zero-to-Non-Zero Storage Updates When You Can | 27 | 596,700 |
| [GAS&#x2011;013](#GAS013-bytes-constants-are-more-efficient-than-string-constants) | Bytes constants are more efficient than string constants | 5 | 1,890 |
| [GAS&#x2011;014](#GAS014-bytesconcat-can-be-used-in-place-of-abiencodepacked) | `bytes.concat()` can be used in place of `abi.encodePacked` | 11 | - |
| [GAS&#x2011;015](#GAS015-<array>length-should-not-be-looked-up-in-every-loop-of-a-for-loop) | `<array>.length` should not be looked up in every loop of a `for`-loop | 29 | 116 |
| [GAS&#x2011;016](#GAS016-enable-ir-based-code-generation) | Enable IR-based code generation | 0 | 250 |
| [GAS&#x2011;017](#GAS017-combine-sequential-for-loops) | Combine Sequential For Loops | 6 | - |
| [GAS&#x2011;018](#GAS018-small-uints-can-be-packed-to-save-gas) | Small `uint`s can be packed to save gas | 40 | 832,000 |
| [GAS&#x2011;019](#GAS019-use-hardcode-address-instead-addressthis) | Use hardcode address instead address(this) | 40 | - |
| [GAS&#x2011;020](#GAS020-some-checks-should-be-done-outside-of-the-loop) | Some checks should be done outside of the loop | 8 | - |
| [GAS&#x2011;021](#GAS021-consider-using-oz-enumerateset-in-place-of-nested-mappings) | Consider using OZ EnumerateSet in place of nested mappings | 8 | 8,000 |
| [GAS&#x2011;022](#GAS022-consider-using-soladys-gas-optimized-lib-for-math) | Consider using Solady's gas optimized lib for Math | 40 | - |
| [GAS&#x2011;023](#GAS023-constructors-can-be-marked-payable) | Constructors can be marked `payable` | 3 | 63 |
| [GAS&#x2011;024](#GAS024-counting-down-in-for-statements-is-more-gas-efficient) | Counting down in `for` statements is more gas efficient | 40 | - |
| [GAS&#x2011;025](#GAS025-variables-should-be-declared-outside-of-loops) | Variables should be declared outside of loops | 40 | 600 |
| [GAS&#x2011;026](#GAS026-do-not-calculate-constants) | Do not calculate constants | 2 | - |
| [GAS&#x2011;027](#GAS027-optimize-gas-by-using-do-while-loops) | Optimize gas by using Do-While loops | 40 | 10,200 |
| [GAS&#x2011;028](#GAS028-avoid-transferring-amounts-of-zero-in-order-to-save-gas) | Avoid transferring amounts of zero in order to save gas | 11 | 220 |
| [GAS&#x2011;029](#GAS029-consider-moving-duplicated-require/revert-checks-to-a-modifier-or-function) | Consider moving duplicated `require()/revert()` checks to a modifier or function | 40 | - |
| [GAS&#x2011;030](#GAS030-emitting-constants-wastes-gas) | Emitting constants wastes gas | 4 | 32 |
| [GAS&#x2011;031](#GAS031-empty-blocks-should-be-removed-or-emit-something) | Empty blocks should be removed or emit something | 5 | - |
| [GAS&#x2011;032](#GAS032-fixed-size-arrays-are-cheaper-than-dynamic-size-arrays) | Fixed-size arrays are cheaper than dynamic-size arrays | 40 | - |
| [GAS&#x2011;033](#GAS033-optimize-names-to-save-gas) | Optimize names to save gas | 38 | 4,864 |
| [GAS&#x2011;034](#GAS034-functions-guaranteed-to-revert-when-called-by-normal-users-can-be-marked-payable) | Functions guaranteed to revert when called by normal users can be marked `payable` | 40 | 840 |
| [GAS&#x2011;035](#GAS035-initializers-can-be-marked-payable) | Initializers can be marked `payable` | 24 | 504 |
| [GAS&#x2011;036](#GAS036-inline-modifiers-that-are-only-used-once-to-save-gas) | Inline `modifier`s that are only used once, to save gas | 40 | - |
| [GAS&#x2011;037](#GAS037-integer-increments-by-one-can-be-unchecked) | Integer increments by one can be unchecked | 40 | 2,400 |
| [GAS&#x2011;038](#GAS038-low-level-call-can-be-optimized-with-assembly) | Low-level `call` can be optimized with assembly | 3 | 477 |
| [GAS&#x2011;039](#GAS039-mappings-are-cheaper-to-use-than-storage-arrays) | Mappings are cheaper to use than storage arrays | 40 | 84,000 |
| [GAS&#x2011;040](#GAS040-memory-safe-annotation-missing) | Memory-safe annotation missing | 20 | - |
| [GAS&#x2011;041](#GAS041-merge-events-to-save-gas) | Merge events to save gas | 5 | 1,875 |
| [GAS&#x2011;042](#GAS042-multiple-accesses-of-the-same-mapping/array-key/index-should-be-cached) | Multiple accesses of the same mapping/array key/index should be cached | 29 | 1,218 |
| [GAS&#x2011;043](#GAS043-multiple-mappings-can-be-replaced-with-a-single-struct-mapping) | Multiple mappings can be replaced with a single struct mapping | 10 | 200,000 |
| [GAS&#x2011;044](#GAS044-nested-for-loops-should-be-avoided-due-to-high-gas-costs-resulting-from-o^2-time-complexity) | Nested for loops should be avoided due to high gas costs resulting from O^2 time complexity | 1 | - |
| [GAS&#x2011;045](#GAS045-the-use-of-a-logical-and-in-place-of-double-if-is-slightly-less-gas-efficient-in-instances-where-there-isnt-a-corresponding-else-statement-for-the-given-if-statement) | The use of a logical AND in place of double if is slightly less gas efficient in instances where there isn't a corresponding else statement for the given if statement | 27 | 810 |
| [GAS&#x2011;046](#GAS046-not-using-the-named-return-variables) | Not using the named return variables | 40 | - |
| [GAS&#x2011;047](#GAS047-optimize-deployment-size-by-fine-tuning-ipfs-hash) | Optimize Deployment Size by Fine-tuning IPFS Hash | 40 | 424,000 |
| [GAS&#x2011;048](#GAS048-pre-increments/pre-decrements-are-cheaper-than-+1/-1) | Pre-increments/pre-decrements are cheaper than `+1`/`-1` | 17 | 102 |
| [GAS&#x2011;049](#GAS049-using-storage-instead-of-memory-for-state-variables-saves-gas) | Using `storage` instead of `memory` for state variables saves gas | 6 | 12,600 |
| [GAS&#x2011;050](#GAS050-private-functions-used-once-can-be-inlined) | `private` functions used once can be inlined | 40 | 1,200 |
| [GAS&#x2011;051](#GAS051-redundant-state-variable-getters) | Redundant state variable getters | 2 | 6,000 |
| [GAS&#x2011;052](#GAS052-remove-or-replace-unused-state-variables) | Remove or replace unused state variables | 29 | 332,050 |
| [GAS&#x2011;053](#GAS053-require/revert-strings-longer-than-32-bytes-cost-extra-gas) | `require()`/`revert()` strings longer than 32 bytes cost extra gas | 27 | 81 |
| [GAS&#x2011;054](#GAS054-same-cast-is-done-multiple-times) | Same cast is done multiple times | 4 | - |
| [GAS&#x2011;055](#GAS055-shortcircuit-rules-can-be-be-used-to-optimize-some-gas-usage) | Shortcircuit rules can be be used to optimize some gas usage | 2 | 4,200 |
| [GAS&#x2011;056](#GAS056-simple-checks-for-zero-can-be-done-using-assembly-to-save-gas) | Simple checks for zero can be done using assembly to save gas | 40 | 240 |
| [GAS&#x2011;057](#GAS057-use-short-circuit-mode-for-conditions) | Use short-circuit mode for conditions | 40 | - |
| [GAS&#x2011;058](#GAS058-split-require-checks-to-save-gas) | Split require checks to save gas | 4 | 12 |
| [GAS&#x2011;059](#GAS059-split-if-revert-checks-to-save-gas) | Split if-revert checks to save gas | 5 | 10 |
| [GAS&#x2011;060](#GAS060-stack-variable-is-only-used-once) | Stack variable is only used once | 40 | 120 |
| [GAS&#x2011;061](#GAS061-state-variable-access-within-a-loop) | State variable access within a loop | 8 | 776 |
| [GAS&#x2011;062](#GAS062-state-variables-can-be-packed-into-fewer-storage-slots) | State variables can be packed into fewer storage slots | 2 | 40,000 |
| [GAS&#x2011;063](#GAS063-state-variables-only-set-in-the-constructor-should-be-declared-immutable) | State variables only set in the constructor should be declared `immutable` | 2 | 4,194 |
| [GAS&#x2011;064](#GAS064-state-variables-should-be-cached-in-stack-variables-rather-than-re-reading-them-from-storage) | State variables should be cached in stack variables rather than re-reading them from storage | 40 | 4,000 |
| [GAS&#x2011;065](#GAS065-structs-can-be-packed-into-fewer-storage-slots) | Structs can be packed into fewer storage slots | 4 | 80,000 |
| [GAS&#x2011;066](#GAS066-structs-can-be-assigned-more-efficiently) | Structs can be assigned more efficiently | 22 | 2,860 |
| [GAS&#x2011;067](#GAS067-structs-can-be-packed-into-fewer-storage-slots-by-truncating-timestamp-bytes) | Structs can be packed into fewer storage slots by truncating timestamp bytes | 1 | 20,000 |
| [GAS&#x2011;068](#GAS068-unnecessary-event-parameters-should-be-removed) | Unnecessary event parameters should be removed | 10 | 350 |
| [GAS&#x2011;069](#GAS069-the-result-of-a-function-call-should-be-cached-rather-than-re-calling-the-function) | The result of a function call should be cached rather than re-calling the function | 10 | 1,000 |
| [GAS&#x2011;070](#GAS070-divisions-can-be-unchecked-to-save-gas) | Divisions can be `unchecked` to save gas | 8 | 480 |
| [GAS&#x2011;071](#GAS071-nonreentrant-modifier-in-certain-functions-is-redundant) | `nonReentrant` modifier in certain functions is redundant | 5 | 123,500 |
| [GAS&#x2011;072](#GAS072-uints/ints-smaller-than-uint256/int256-increase-gas-cost) | `uints`/`ints` smaller than `uint256`/`int256` increase gas cost | 40 | 240 |
| [GAS&#x2011;073](#GAS073-use-arrayunsafeaccess-to-avoid-repeated-array-length-checks) | Use `Array.unsafeAccess()` to avoid repeated array length checks | 40 | 84,000 |
| [GAS&#x2011;074](#GAS074-use-assembly-for-small-keccak256-hashes-in-order-to-save-gas) | Use assembly for small `keccak256` hashes, in order to save gas | 23 | 1,840 |
| [GAS&#x2011;075](#GAS075-use-assembly-in-place-of-abidecode-to-save-gas) | Use assembly in place of `abi.decode` to save gas | 16 | 1,792 |
| [GAS&#x2011;076](#GAS076-use-assembly-scratch-space-to-build-calldata-for-event-emits) | Use assembly scratch space to build calldata for event emits | 23 | 5,060 |
| [GAS&#x2011;077](#GAS077-use-assembly-scratch-space-to-build-calldata-for-external-calls) | Use assembly scratch space to build calldata for external calls | 40 | 8,800 |
| [GAS&#x2011;078](#GAS078-use-assembly-to-perform-efficient-back-to-back-calls) | Use assembly to perform efficient back-to-back calls | 2 | 520 |
| [GAS&#x2011;079](#GAS079-msgsender-checks-can-be-optimized-with-assembly) | `msg.sender` checks can be optimized with assembly | 12 | 144 |
| [GAS&#x2011;080](#GAS080-use-assembly-to-write-address/contract-storage-values) | Use `assembly` to write address/contract storage values | 40 | 2,000 |
| [GAS&#x2011;081](#GAS081-using-calldata-instead-of-memory-for-read-only-arguments-in-external-functions-saves-gas) | Using `calldata` instead of `memory` for read-only arguments in `external` functions saves gas | 40 | 12,000 |
| [GAS&#x2011;082](#GAS082-using-hardcoded-constants-instead-of-typeuintmax-is-cheaper) | Using hardcoded constants instead of `type(uint).max` is cheaper | 10 | 40 |
| [GAS&#x2011;083](#GAS083-use-custom-errors-rather-than-revert/require-strings-to-save-gas) | Use custom errors rather than `revert()`/`require()` strings to save gas | 40 | 1,160 |
| [GAS&#x2011;084](#GAS084-consider-using-if-statements-over-ternary-operators) | Consider using `if` statements over ternary operators | 14 | - |
| [GAS&#x2011;085](#GAS085-use-immutable-when-you-have-storage-variable-that-is-not-going-to-change) | Use immutable when you have storage variable that is not going to change | 5 | - |
| [GAS&#x2011;086](#GAS086-use-local-variables-for-emitting) | Use local variables for emitting | 7 | 700 |
| [GAS&#x2011;087](#GAS087-consider-using-modifiers-rather-than-invoking-functions-to-perform-checks) | Consider using modifiers rather than invoking functions to perform checks | 4 | 160 |
| [GAS&#x2011;088](#GAS088-events-should-be-emitted-outside-of-loops) | Events should be emitted outside of loops | 3 | 1,125 |
| [GAS&#x2011;089](#GAS089-replace-sx-+=-y-with-sx-=-sx-+-y-for-memory-structs) | Replace `s.x += y` with `s.x = s.x + y` for memory structs | 6 | 600 |
| [GAS&#x2011;090](#GAS090-use-assembly-to-emit-events-in-order-to-save-gas) | Use assembly to emit events, in order to save gas | 24 | 912 |
| [GAS&#x2011;091](#GAS091-use-selfbalance-instead-of-addressthisbalance) | Use `selfbalance()` instead of `address(this).balance` | 6 | - |
| [GAS&#x2011;092](#GAS092-division-by-powers-of-two-should-use-bit-shifting) | Division by powers of two should use bit shifting | 2 | 40 |
| [GAS&#x2011;093](#GAS093-use-the-inputs/results-of-assignments-rather-than-re-reading-state-variables) | Use the inputs/results of assignments rather than re-reading state variables | 10 | 970 |
| [GAS&#x2011;094](#GAS094-optimize-boolean-states-with-uint2561/2) | Optimize Boolean States with `uint256(1/2)` | 10 | 171,000 |
| [GAS&#x2011;095](#GAS095-using->-0-costs-more-gas-than-!=-0-when-used-on-a-uint-in-a-require-statement) | Using `> 0` costs more gas than `!= 0` when used on a `uint` in a `require()` statement | 5 | 30 |
| [GAS&#x2011;096](#GAS096-using-bools-for-storage-incurs-overhead) | Using bools for storage incurs overhead | 24 | 410,400 |
| [GAS&#x2011;097](#GAS097-using-constants-instead-of-enum-can-save-gas) | Using `constant`s instead of `enum` can save gas | 9 | - |
| [GAS&#x2011;098](#GAS098-using-globals-directly-is-cheaper-than-assigning-them-to-variables) | Using globals directly is cheaper than assigning them to variables | 1 | 5 |
| [GAS&#x2011;099](#GAS099-using-msg-globals-directly-rather-than-caching-the-value-saves-gas) | Using `msg` globals directly, rather than caching the value, saves gas | 3 | - |
| [GAS&#x2011;100](#GAS100-using-private-rather-than-public-saves-gas) | Using `private` rather than `public`, saves gas | 40 | 136,240 |
| [GAS&#x2011;101](#GAS101-using-storage-instead-of-memory-for-structs/arrays-saves-gas) | Using `storage` instead of `memory` for structs/arrays saves gas | 40 | 84,000 |
| [GAS&#x2011;102](#GAS102-using-this-to-access-functions-results-in-an-external-call-wasting-gas) | Using `this` to access functions results in an external call, wasting gas | 1 | 100 |
| [GAS&#x2011;103](#GAS103-<x>-+=-<y>-costs-more-gas-than-<x>-=-<x>-+-<y>-for-basic-typed-state-variables) | `<x> += <y>` costs more gas than `<x> = <x> + <y>` for basic-typed state variables | 5 | 1,240 |


### [GAS&#x2011;001] `++i` costs less gas than `i++`/`i += 1`, especially when it's used in `for`-loops (`--i`/`i--` too)
<details>
<summary><i>There are 13 instances (click to view)</i></summary>

```solidity
File: contracts/L1/libs/LibDepositing.sol

62             _state.slotA.numEthDeposits++; 

116                 _state.slotA.numEthDeposits++; 
```
([62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L62), [116](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L116))

```solidity
File: contracts/L1/libs/LibProving.sol

252                 ts.contestations += 1; 

377             _ts.contestations += 1; 
```
([252](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L252), [377](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L377))

```solidity
File: contracts/automata-attestation/utils/BytesUtils.sol

359             bitlen -= 1; 
```
([359](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L359))

```solidity
File: contracts/thirdparty/optimism/rlp/RLPReader.sol

89             itemCount += 1; 
```
([89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L89))

```solidity
File: contracts/thirdparty/optimism/rlp/RLPWriter.sol

40                 lenLen++; 

46             for (i = 1; i <= lenLen; i++) { 

59         for (; i < 32; i++) { 

66         for (uint256 j = 0; j < out_.length; j++) { 
```
([40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L40), [46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L46), [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L59), [66](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66))

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

85         for (uint256 i = 0; i < proof.length; i++) { 

137                     currentKeyIndex += 1; 
```
([85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85), [137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L137))

```solidity
File: contracts/verifiers/SgxVerifier.sol

222             nextInstanceId++; 
```
([222](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L222))

</details>

### [GAS&#x2011;002] `++i`/`i++` should be `unchecked{++i}`/`unchecked{i++}` when it is not possible for them to overflow
The `unchecked` keyword is new in solidity version 0.8.0, so this only applies to that version or higher, which these instances are. This saves **30-40 gas [per loop](https://gist.github.com/hrkrshnn/ee8fabd532058307229d65dcd5836ddc#the-increment-in-for-loop-post-condition-can-be-made-unchecked)**

<details>
<summary><i>There are 40 instances (click to view)</i></summary>

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

172         for (uint256 i; i < _tierFees.length; ++i) { 
```
([172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L172))

```solidity
File: contracts/L1/libs/LibProposing.sol

244             for (uint256 i; i < params.hookCalls.length; ++i) { 
```
([244](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L244))

```solidity
File: contracts/L1/provers/Guardians.sol

74         for (uint256 i; i < guardians.length; ++i) { 

80         for (uint256 i = 0; i < _newGuardians.length; ++i) { 
```
([74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L74), [80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L80))

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

80         for (uint256 i; i < serialNumBatch.length; ++i) { 

95         for (uint256 i; i < serialNumBatch.length; ++i) { 

191         for (uint256 i; i < enclaveId.tcbLevels.length; ++i) { 

214         for (uint256 i; i < tcb.tcbLevels.length; ++i) { 

240         for (uint256 i; i < CPUSVN_LENGTH; ++i) { 

259         for (uint256 i; i < n; ++i) { 

420             for (uint256 i; i < 3; ++i) { 
```
([80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L80), [95](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L95), [191](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L191), [214](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L214), [240](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L240), [259](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L259), [420](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L420))

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol

54         for (uint256 i; i < size; ++i) { 

244         for (uint256 i; i < split.length; ++i) { 

354         for (uint256 i; i < SGX_TCB_CPUSVN_SIZE + 1; ++i) { 
```
([54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L54), [244](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L244), [354](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L354))

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

153         for (uint256 i; i < encoded.length; ++i) { 

281         for (uint256 i; i < 3; ++i) { 
```
([153](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L153), [281](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L281))

```solidity
File: contracts/automata-attestation/utils/BytesUtils.sol

333         for (uint256 i; i < len; ++i) { 
```
([333](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L333))

```solidity
File: contracts/automata-attestation/utils/RsaVerify.sol

140         for (uint256 i = 2; i < 2 + paddingLen; ++i) { 

152             for (uint256 i; i < digestAlgoWithParamLen; ++i) { 

158             for (uint256 i; i < digestAlgoWithParamLen; ++i) { 

174         for (uint256 i; i < _sha256.length; ++i) { 

273         for (uint256 i = 2; i < 2 + paddingLen; ++i) { 

283         for (uint256 i; i < sha1Prefix.length; ++i) { 

290         for (uint256 i; i < _sha1.length; ++i) { 
```
([140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L140), [152](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L152), [158](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L158), [174](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L174), [273](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L273), [283](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L283), [290](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L290))

```solidity
File: contracts/automata-attestation/utils/X509DateUtils.sol

48         for (uint16 i = 1970; i < year; ++i) { 

59         for (uint8 i = 1; i < month; ++i) { 
```
([48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L48), [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L59))

```solidity
File: contracts/bridge/Bridge.sol

90         for (uint256 i; i < _msgHashes.length; ++i) { 
```
([90](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L90))

```solidity
File: contracts/signal/SignalService.sol

104         for (uint256 i; i < hopProofs.length; ++i) { 
```
([104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L104))

```solidity
File: contracts/team/airdrop/ERC721Airdrop.sol

59         for (uint256 i; i < tokenIds.length; ++i) { 
```
([59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59))

```solidity
File: contracts/thirdparty/optimism/rlp/RLPWriter.sol

46             for (i = 1; i <= lenLen; i++) { 

59         for (; i < 32; i++) { 

66         for (uint256 j = 0; j < out_.length; j++) { 
67             out_[j] = b[i++];
```
([46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L46), [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L59), [66](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66-L67))

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

85         for (uint256 i = 0; i < proof.length; i++) { 
```
([85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85))

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

47         for (uint256 i; i < _op.amounts.length; ++i) { 
```
([47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L47))

```solidity
File: contracts/tokenvault/ERC721Vault.sol

34         for (uint256 i; i < _op.tokenIds.length; ++i) { 

170             for (uint256 i; i < _tokenIds.length; ++i) { 

175             for (uint256 i; i < _tokenIds.length; ++i) { 
```
([34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L34), [170](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L170), [175](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L175))

```solidity
File: contracts/verifiers/SgxVerifier.sol

104         for (uint256 i; i < _ids.length; ++i) { 

210         for (uint256 i; i < _instances.length; ++i) { 
```
([104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L104), [210](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210))

</details>

### [GAS&#x2011;003] Operator `>=`/`<=` costs less gas than operator `>`/`<`
The compiler uses opcodes `GT` and `ISZERO` for code that uses `>`, but only requires `LT` for `>=`. A similar behaviour applies for `>`, which uses opcodes `LT` and `ISZERO`, but only requires `GT` for `<=`.

<details>
<summary><i>There are 40 instances (click to view)</i></summary>

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

82             block.timestamp > assignment.expiry 

85                 || assignment.maxBlockId != 0 && _meta.id > assignment.maxBlockId 
86                 || assignment.maxProposedIn != 0 && block.number > assignment.maxProposedIn

125         if (address(this).balance > 0) { 

172         for (uint256 i; i < _tierFees.length; ++i) { 
```
([82](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L82), [85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L85-L86), [125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L125), [172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L172))

```solidity
File: contracts/L1/libs/LibDepositing.sol

78         if (numPending < _config.ethDepositMinCountPerBlock) { 

86             for (uint256 i; i < deposits_.length;) { 

93                 uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount; 

140                 && _state.slotA.numEthDeposits - _state.slotA.nextEthDepositToProcess 
141                     < _config.ethDepositRingBufferSize - 1;

150         if (_amount > type(uint96).max) revert L1_INVALID_ETH_DEPOSIT(); 
```
([78](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L78), [86](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L86), [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L93), [140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L140-L141), [150](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L150))

```solidity
File: contracts/L1/libs/LibProposing.sol

171             if (uint256(params.txListByteOffset) + params.txListByteSize > MAX_BYTES_PER_BLOB) { 

195         if (meta_.txListByteSize == 0 || meta_.txListByteSize > _config.blockMaxTxListBytes) { 

244             for (uint256 i; i < params.hookCalls.length; ++i) { 

296         return _state.reusableBlobs[_blobHash] + _config.blobExpiry > block.timestamp; 
```
([171](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L171), [195](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L195), [244](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L244), [296](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L296))

```solidity
File: contracts/L1/libs/LibProving.sol

134         if (_proof.tier == 0 || _proof.tier < _meta.minTier || _proof.tier < ts.tier) { 

192             bool returnLivenessBond = blk.livenessBond > 0 && _proof.data.length == 32 

203         if (_proof.tier > ts.tier) { 

381             if (reward > _tier.validityBond) { 
```
([134](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L134), [192](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L192), [203](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L203), [381](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L381))

```solidity
File: contracts/L1/libs/LibUtils.sol

34         if (_blockId < b.lastVerifiedBlockId || _blockId >= b.numBlocks) { 
```
([34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L34))

```solidity
File: contracts/L1/libs/LibVerifying.sol

127             while (blockId < b.numBlocks && numBlocksVerified < _maxBlocksToVerify) { 

152                         uint256(ITierProvider(tierProvider).getTier(ts.tier).cooldownWindow) * 60 
153                             + uint256(ts.timestamp).max(_state.slotB.lastUnpausedAt) > block.timestamp

212             if (numBlocksVerified > 0) { 

238         if (_lastVerifiedBlockId > lastSyncedBlock + _config.blockSyncThreshold) { 

251                 || _config.blockMaxTxListBytes > 128 * 1024 // calldata up to 128K 

256             || _config.ethDepositMaxCountPerBlock > 32 
257                 || _config.ethDepositMaxCountPerBlock < _config.ethDepositMinCountPerBlock

260                 || _config.ethDepositMaxAmount > type(uint96).max || _config.ethDepositGas == 0 

262                 || _config.ethDepositMaxFee > type(uint96).max / _config.ethDepositMaxCountPerBlock 
```
([127](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L127), [152](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L152-L153), [212](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L212), [238](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L238), [251](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L251), [256](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L256-L257), [260](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L260), [262](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L262))

```solidity
File: contracts/L1/provers/Guardians.sol

63         if (_newGuardians.length < MIN_NUM_GUARDIANS || _newGuardians.length > type(uint8).max) { 

68         if (_minGuardians < (_newGuardians.length + 1) >> 1 || _minGuardians > _newGuardians.length) 

74         for (uint256 i; i < guardians.length; ++i) { 

80         for (uint256 i = 0; i < _newGuardians.length; ++i) { 

133             for (uint256 i; i < guardiansLength; ++i) { 
```
([63](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L63), [68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L68), [74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L74), [80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L80), [133](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L133))

```solidity
File: contracts/common/AddressResolver.sol

59         if (block.chainid > type(uint64).max) { 
```
([59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L59))

```solidity
File: contracts/libs/LibMath.sol

13         return _a > _b ? _b : _a; 

21         return _a > _b ? _a : _b; 
```
([13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibMath.sol#L13), [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibMath.sol#L21))

</details>

### [GAS&#x2011;004] `abi.encode()` is less efficient than `abi.encodePacked()`
See for more information: https://github.com/ConnorBlockchain/Solidity-Encode-Gas-Comparison

<details>
<summary><i>There are 18 instances (click to view)</i></summary>

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

147             abi.encode( 
```
([147](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L147))

```solidity
File: contracts/L1/libs/LibProposing.sol

126                 depositsHash: keccak256(abi.encode(deposits_)), 

213             metaHash: keccak256(abi.encode(meta_)), 
```
([126](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L126), [213](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L213))

```solidity
File: contracts/L1/libs/LibProving.sol

121         if (blk.blockId != _meta.id || blk.metaHash != keccak256(abi.encode(_meta))) { 
```
([121](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L121))

```solidity
File: contracts/L1/provers/GuardianProver.sol

46         bytes32 hash = keccak256(abi.encode(_meta, _tran)); 

51             ITaikoL1(resolve("taiko", false)).proveBlock(_meta.id, abi.encode(_meta, _tran, _proof)); 
```
([46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L46), [51](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L51))

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

482         retData = abi.encodePacked(sha256(abi.encode(v3quote)), tcbStatus); 
```
([482](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L482))

```solidity
File: contracts/automata-attestation/utils/SigVerifyLib.sol

136         bytes memory args = abi.encode(sha256(tbs), r, s, gx, gy); 
```
([136](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L136))

```solidity
File: contracts/bridge/Bridge.sol

450         return keccak256(abi.encode("TAIKO_MESSAGE", _message)); 
```
([450](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L450))

```solidity
File: contracts/signal/SignalService.sol

186         return keccak256(abi.encode(_chainId, _kind, _blockId)); 
```
([186](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L186))

```solidity
File: contracts/team/airdrop/ERC20Airdrop.sol

60         _verifyClaim(abi.encode(user, amount), proof); 
```
([60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L60))

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol

80         _verifyClaim(abi.encode(user, amount), proof); 
```
([80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L80))

```solidity
File: contracts/team/airdrop/ERC721Airdrop.sol

56         _verifyClaim(abi.encode(user, tokenIds), proof); 
```
([56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L56))

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol

68         bytes32 hash = keccak256(abi.encode("CLAIM_TAIKO_AIRDROP", data)); 
```
([68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L68))

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

281             this.onMessageInvocation, abi.encode(ctoken_, _user, _op.to, _op.tokenIds, _op.amounts) 
```
([281](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L281))

```solidity
File: contracts/tokenvault/ERC20Vault.sol

384             this.onMessageInvocation, abi.encode(ctoken_, _user, _to, balanceChange_) 
```
([384](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L384))

```solidity
File: contracts/tokenvault/ERC721Vault.sol

217             this.onMessageInvocation, abi.encode(ctoken_, _user, _op.to, _op.tokenIds) 
```
([217](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L217))

```solidity
File: contracts/verifiers/SgxVerifier.sol

183             abi.encode( 
```
([183](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L183))

</details>

### [GAS&#x2011;005] Cache address(this) when used more than twice
<details>
<summary><i>There are 2 instances (click to view)</i></summary>

```solidity
File: contracts/L1/libs/LibProposing.sol

// @audit L238, L260, L268, L261, L253
68     function proposeBlock( 
69         TaikoData.State storage _state,
70         TaikoData.Config memory _config,
71         IAddressResolver _resolver,
72         bytes calldata _data,
73         bytes calldata _txList
74     )
75         internal
76         returns (TaikoData.BlockMetadata memory meta_, TaikoData.EthDeposit[] memory deposits_)
77     {
```
([68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L68-L77))

```solidity
File: contracts/tokenvault/ERC20Vault.sol

// @audit L378, L379, L380
348     function _handleMessage( 
349         address _user,
350         address _token,
351         address _to,
352         uint256 _amount
353     )
354         private
355         returns (bytes memory msgData_, CanonicalERC20 memory ctoken_, uint256 balanceChange_)
356     {
```
([348](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L348-L356))

</details>

### [GAS&#x2011;006] Use solady library where possible to save gas
The following OpenZeppelin imports have a Solady equivalent, as such they can be used to save GAS as Solady modules have been specifically designed to be as GAS efficient as possible.

<details>
<summary><i>There are 16 instances (click to view)</i></summary>

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

5 import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol"; 
```
([5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L5))

```solidity
File: contracts/L2/TaikoL2.sol

5 import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol"; 
```
([5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L5))

```solidity
File: contracts/common/AddressResolver.sol

4 import "@openzeppelin/contracts-upgradeable/proxy/utils/Initializable.sol"; 
```
([4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L4))

```solidity
File: contracts/common/EssentialContract.sol

4 import "@openzeppelin/contracts/proxy/utils/UUPSUpgradeable.sol"; 
```
([4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L4))

```solidity
File: contracts/libs/LibAddress.sol

5 import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol"; 
```
([5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L5))

```solidity
File: contracts/signal/SignalService.sol

4 import "@openzeppelin/contracts/utils/math/SafeCast.sol"; 
```
([4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L4))

```solidity
File: contracts/team/TimelockTokenPool.sol

4 import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol"; 

6 import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol"; 
```
([4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L4), [6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L6))

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol

4 import "@openzeppelin/contracts/utils/cryptography/MerkleProof.sol"; 
```
([4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L4))

```solidity
File: contracts/tokenvault/BridgedERC1155.sol

4 import "@openzeppelin/contracts/utils/Strings.sol"; 
```
([4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L4))

```solidity
File: contracts/tokenvault/BridgedERC20.sol

5 import "@openzeppelin/contracts/utils/Strings.sol"; 
```
([5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L5))

```solidity
File: contracts/tokenvault/BridgedERC721.sol

5 import "@openzeppelin/contracts/utils/Strings.sol"; 
```
([5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L5))

```solidity
File: contracts/tokenvault/ERC20Vault.sol

6 import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol"; 
```
([6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L6))

```solidity
File: contracts/tokenvault/ERC721Vault.sol

5 import "@openzeppelin/contracts/token/ERC721/IERC721Receiver.sol"; 
```
([5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L5))

```solidity
File: contracts/tokenvault/LibBridgedToken.sol

4 import "@openzeppelin/contracts/utils/Strings.sol"; 
```
([4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L4))

```solidity
File: contracts/verifiers/SgxVerifier.sol

4 import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol"; 
```
([4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L4))

</details>

### [GAS&#x2011;007] Assembly let var only used on once
If a variable is only once, it makes more sense to use the value the variable holds directly.

<details>
<summary><i>There are 9 instances (click to view)</i></summary>

```solidity
File: contracts/automata-attestation/utils/BytesUtils.sol

267             let mask := not(sub(exp(256, sub(32, len)), 1)) 
```
([267](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L267))

```solidity
File: contracts/automata-attestation/utils/SHA1.sol

33                         let mask := not(sub(exp(256, sub(32, count)), 1)) 
```
([33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SHA1.sol#L33))

```solidity
File: contracts/thirdparty/optimism/Bytes.sol

54                 let end := add(mc, _length) 

124             let bytesStart := add(_bytes, 0x20) 

127             let nibblesStart := add(_nibbles, 0x20) 
```
([54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L54), [124](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L124), [127](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L127))

</details>

### [GAS&#x2011;008] Assigning state variables directly with named struct constructors wastes gas
Using named arguments for struct means that the compiler needs to organize the fields in memory before doing the assignment, which wastes gas. Set each field directly in storage (use dot-notation), or use the unnamed version of the constructor.

<details>
<summary><i>There are 16 instances (click to view)</i></summary>

```solidity
File: contracts/L1/libs/LibDepositing.sol

88                 deposits_[i] = TaikoData.EthDeposit({ 
89                     recipient: address(uint160(data >> 96)),
90                     amount: uint96(data),
91                     id: j
92                 });
```
([88](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L88-L92))

```solidity
File: contracts/L1/libs/LibProposing.sol

121             meta_ = TaikoData.BlockMetadata({ 
122                 l1Hash: blockhash(block.number - 1),
123                 difficulty: 0, // to be initialized below
124                 blobHash: 0, // to be initialized below
125                 extraData: params.extraData,
126                 depositsHash: keccak256(abi.encode(deposits_)),
127                 coinbase: params.coinbase,
128                 id: b.numBlocks,
129                 gasLimit: _config.blockMaxGasLimit,
130                 timestamp: uint64(block.timestamp),
131                 l1Height: uint64(block.number - 1),
132                 txListByteOffset: 0, // to be initialized below
133                 txListByteSize: 0, // to be initialized below
134                 minTier: 0, // to be initialized below
135                 blobUsed: _txList.length == 0,
136                 parentMetaHash: parentMetaHash
137             });

212         TaikoData.Block memory blk = TaikoData.Block({ 
213             metaHash: keccak256(abi.encode(meta_)),
214             // Safeguard the liveness bond to ensure its preservation,
215             // particularly in scenarios where it might be altered after the
216             // block's proposal but before it has been proven or verified.
217             livenessBond: _config.livenessBond,
218             blockId: b.numBlocks,
219             proposedAt: meta_.timestamp,
220             proposedIn: uint64(block.number),
221             // For a new block, the next transition ID is always 1, not 0.
222             nextTransitionId: 1,
223             // For unverified block, its verifiedTransitionId is always 0.
224             verifiedTransitionId: 0,
225             assignedProver: params.assignedProver
226         });
```
([121](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L121-L137), [212](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L212-L226))

```solidity
File: contracts/L1/libs/LibProving.sol

166                 IVerifier.Context memory ctx = IVerifier.Context({ 
167                     metaHash: blk.metaHash,
168                     blobHash: _meta.blobHash,
169                     // Separate msgSender to allow the prover to be any address in the future.
170                     prover: msg.sender,
171                     msgSender: msg.sender,
172                     blockId: blk.blockId,
173                     isContesting: isContesting,
174                     blobUsed: _meta.blobUsed
175                 });
```
([166](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L166-L175))

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

54         v3ParsedQuote = V3Struct.ParsedV3QuoteStruct({ 
55             header: header,
56             localEnclaveReport: localEnclaveReport,
57             v3AuthData: authDataV3
58         });

190         header = V3Struct.Header({ 
191             version: version,
192             attestationKeyType: attestationKeyType,
193             teeType: teeType,
194             qeSvn: bytes2(rawHeader.substring(8, 2)),
195             pceSvn: bytes2(rawHeader.substring(10, 2)),
196             qeVendorId: qeVendorId,
197             userData: bytes20(rawHeader.substring(28, 20))
198         });
```
([54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L54-L58), [190](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L190-L198))

```solidity
File: contracts/bridge/Bridge.sol

243                 proofReceipt[msgHash] = ProofReceipt({ 
244                     receivedAt: receivedAt,
245                     preferredExecutor: _message.gasLimit == 0 ? _message.destOwner : msg.sender
246                 });
```
([243](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L243-L246))

```solidity
File: contracts/thirdparty/optimism/rlp/RLPReader.sol

47         out_ = RLPItem({ length: _in.length, ptr: ptr }); 

84             out_[itemCount] = RLPItem({ 
85                 length: itemLength + itemOffset,
86                 ptr: MemoryPointer.wrap(MemoryPointer.unwrap(_in.ptr) + offset)
87             });
```
([47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L47), [84](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L84-L87))

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

209             proof_[i] = TrieNode({ encoded: _proof[i], decoded: RLPReader.readList(_proof[i]) }); 
```
([209](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L209))

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

58         IBridge.Message memory message = IBridge.Message({ 
59             id: 0, // will receive a new value
60             from: address(0), // will receive a new value
61             srcChainId: 0, // will receive a new value
62             destChainId: _op.destChainId,
63             srcOwner: msg.sender,
64             destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,
65             to: resolve(_op.destChainId, name(), false),
66             refundTo: _op.refundTo,
67             value: msg.value - _op.fee,
68             fee: _op.fee,
69             gasLimit: _op.gasLimit,
70             data: data,
71             memo: _op.memo
72         });

256                 ctoken_ = CanonicalNFT({ 
257                     chainId: uint64(block.chainid),
258                     addr: _op.token,
259                     symbol: "",
260                     name: ""
261                 });
```
([58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L58-L72), [256](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L256-L261))

```solidity
File: contracts/tokenvault/ERC20Vault.sol

221         IBridge.Message memory message = IBridge.Message({ 
222             id: 0, // will receive a new value
223             from: address(0), // will receive a new value
224             srcChainId: 0, // will receive a new value
225             destChainId: _op.destChainId,
226             srcOwner: msg.sender,
227             destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,
228             to: resolve(_op.destChainId, name(), false),
229             refundTo: _op.refundTo,
230             value: msg.value - _op.fee,
231             fee: _op.fee,
232             gasLimit: _op.gasLimit,
233             data: data,
234             memo: _op.memo
235         });

365             ctoken_ = CanonicalERC20({ 
366                 chainId: uint64(block.chainid),
367                 addr: _token,
368                 decimals: meta.decimals(),
369                 symbol: meta.symbol(),
370                 name: meta.name()
371             });
```
([221](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L221-L235), [365](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L365-L371))

```solidity
File: contracts/tokenvault/ERC721Vault.sol

44         IBridge.Message memory message = IBridge.Message({ 
45             id: 0, // will receive a new value
46             from: address(0), // will receive a new value
47             srcChainId: 0, // will receive a new value
48             destChainId: _op.destChainId,
49             srcOwner: msg.sender,
50             destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,
51             to: resolve(_op.destChainId, name(), false),
52             refundTo: _op.refundTo,
53             value: msg.value - _op.fee,
54             fee: _op.fee,
55             gasLimit: _op.gasLimit,
56             data: data,
57             memo: _op.memo
58         });

203                 ctoken_ = CanonicalNFT({ 
204                     chainId: uint64(block.chainid),
205                     addr: _op.token,
206                     symbol: t.symbol(),
207                     name: t.name()
208                 });
```
([44](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L44-L58), [203](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L203-L208))

</details>

### [GAS&#x2011;009] Avoid contract existence checks by using low-level calls
Prior to 0.8.10 the compiler inserted extra code, including `EXTCODESIZE` (**100 gas**), to check for contract existence for external function calls. In more recent solidity versions, the compiler will not insert these checks if the external call has a return value. Similar behavior can be achieved in earlier versions by using low-level calls, since low-level calls never check for contract existence

<details>
<summary><i>There are 40 instances (click to view)</i></summary>

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

114             IERC20(assignment.feeToken).safeTransferFrom( 

149                 ITaikoL1(_taikoL1Address).getConfig().chainId, 
```
([114](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L114), [149](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L149))

```solidity
File: contracts/L1/libs/LibProposing.sol

207         meta_.minTier = ITierProvider(_resolver.resolve("tier_provider", false)).getMinTier( 

253                 IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }( 
```
([207](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L207), [253](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L253))

```solidity
File: contracts/L1/libs/LibProving.sol

141             ITierProvider(_resolver.resolve("tier_provider", false)).getTier(_proof.tier); 

177                 IVerifier(verifier).verifyProof(ctx, _tran, _proof); 
```
([141](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L141), [177](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L177))

```solidity
File: contracts/L1/libs/LibVerifying.sol

152                         uint256(ITierProvider(tierProvider).getTier(ts.tier).cooldownWindow) * 60 
```
([152](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L152))

```solidity
File: contracts/L1/provers/GuardianProver.sol

51             ITaikoL1(resolve("taiko", false)).proveBlock(_meta.id, abi.encode(_meta, _tran, _proof)); 
```
([51](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L51))

```solidity
File: contracts/L2/CrossChainOwned.sol

45         IBridge.Context memory ctx = IBridge(msg.sender).context(); 
```
([45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L45))

```solidity
File: contracts/L2/TaikoL2.sol

148             ISignalService(resolve("signal_service", false)).syncChainData( 

176             IERC20(_token).safeTransfer(_to, IERC20(_token).balanceOf(address(this))); 
```
([148](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L148), [176](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L176))

```solidity
File: contracts/bridge/Bridge.sol

150         ISignalService(resolve("signal_service", false)).sendSignal(msgHash_); 

174             if (!ISignalService(signalService).isSignalSent(address(this), msgHash)) { 

199                 IRecallableSender(_message.from).onMessageRecalled{ value: _message.value }( 

342         return ISignalService(resolve("signal_service", false)).isSignalSent({ 

522             ISignalService(resolve("signal_service", false)).sendSignal( 
```
([150](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L150), [174](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L174), [199](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L199), [342](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L342), [522](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L522))

```solidity
File: contracts/common/AddressResolver.sol

83         addr_ = payable(IAddressManager(addressManager).getAddress(_chainId, _name)); 
```
([83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L83))

```solidity
File: contracts/libs/LibAddress.sol

56         try IERC165(_addr).supportsInterface(_interfaceId) returns (bool _result) { 

71             return IERC1271(_addr).isValidSignature(_hash, _sig) == _EIP1271_MAGICVALUE; 
```
([56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L56), [71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L71))

```solidity
File: contracts/tokenvault/BaseVault.sol

53         ctx_ = IBridge(msg.sender).context(); 

64         ctx_ = IBridge(msg.sender).context(); 
```
([53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L53), [64](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L64))

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol

82             IBridgedERC20(migratingAddress).mint(_account, _amount); 
```
([82](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L82))

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

77             IBridge(resolve("bridge", false)).sendMessage{ value: msg.value }(message); 

226             IERC1155(token).safeBatchTransferFrom(address(this), to, tokenIds, amounts, ""); 

230             BridgedERC1155(token).mintBatch(to, tokenIds, amounts); 

252                     BridgedERC1155(_op.token).burn(_user, _op.tokenIds[i], _op.amounts[i]); 

270                     IERC1155(_op.token).safeTransferFrom({ 
```
([77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L77), [226](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L226), [230](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L230), [252](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L252), [270](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L270))

```solidity
File: contracts/tokenvault/ERC20Vault.sol

164         if (IBridgedERC20(_btokenNew).owner() != owner()) { 

184             IBridgedERC20(btokenOld_).changeMigrationStatus(_btokenNew, false); 
185             IBridgedERC20(_btokenNew).changeMigrationStatus(btokenOld_, true);

239             IBridge(resolve("bridge", false)).sendMessage{ value: msg.value }(message); 

330             IERC20(token_).safeTransfer(_to, _amount); 

333             IBridgedERC20(token_).mint(_to, _amount); 

360             IBridgedERC20(_token).burn(msg.sender, _amount); 
```
([164](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L164), [184](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L184-L185), [239](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L239), [330](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L330), [333](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L333), [360](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L360))

```solidity
File: contracts/tokenvault/ERC721Vault.sol

62             IBridge(resolve("bridge", false)).sendMessage{ value: msg.value }(message); 

171                 IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]); 

176                 BridgedERC721(token_).mint(_to, _tokenIds[i]); 

198                     BridgedERC721(_op.token).burn(_user, _op.tokenIds[i]); 
```
([62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L62), [171](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L171), [176](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L176), [198](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L198))

```solidity
File: contracts/verifiers/SgxVerifier.sol

128         (bool verified,) = IAttestation(automataDcapAttestation).verifyParsedQuote(_attestation); 
```
([128](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L128))

</details>

### [GAS&#x2011;010] Avoid Unnecessary Public Variables
Automated getter functions are automatically created for public state variables in Solidity, contributing to larger contract sizes and potentially escalating deployment and interaction expenses. To enhance gas efficiency and overall contract performance, it is advisable to restrict the usage of public variables unless external accessibility is essential. Favor the utilization of internal or private visibility, and employ explicit getter functions only when necessary. This approach not only diminishes contract size but also affords improved oversight over data access and manipulation, thereby bolstering security and code readability. Emphasize the development of streamlined and efficient contracts to ensure cost-effectiveness and optimal performance within the blockchain environment.

<details>
<summary><i>There are 40 instances (click to view)</i></summary>

```solidity
File: contracts/L1/TaikoL1.sol

24     TaikoData.State public state; 
```
([24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L24))

```solidity
File: contracts/L1/provers/Guardians.sol

23     address[] public guardians; 

27     uint32 public version; 

30     uint32 public minGuardians; 
```
([23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L23), [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L27), [30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L30))

```solidity
File: contracts/L2/CrossChainOwned.sol

16     uint64 public ownerChainId; 

19     uint64 public nextTxId; 
```
([16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L16), [19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L19))

```solidity
File: contracts/L2/TaikoL2.sol

43     bytes32 public publicInputHash; 

47     uint64 public gasExcess; 

50     uint64 public lastSyncedBlock; 
```
([43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L43), [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L47), [50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L50))

```solidity
File: contracts/L2/TaikoL2EIP1559Configurable.sol

11     Config public customConfig; 
```
([11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L11))

```solidity
File: contracts/bridge/Bridge.sol

31     uint128 public nextMessageId; 
```
([31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L31))

```solidity
File: contracts/common/AddressResolver.sol

13     address public addressManager; 
```
([13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L13))

```solidity
File: contracts/team/TimelockTokenPool.sol

59     address public taikoToken; 

62     address public costToken; 

65     address public sharedVault; 

68     uint128 public totalAmountGranted; 

71     uint128 public totalAmountVoided; 

74     uint128 public totalAmountWithdrawn; 

77     uint128 public totalCostPaid; 
```
([59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L59), [62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L62), [65](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L65), [68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L68), [71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L71), [74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L74), [77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L77))

```solidity
File: contracts/team/airdrop/ERC20Airdrop.sol

13     address public token; 

16     address public vault; 
```
([13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L13), [16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L16))

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol

16     address public token; 

19     address public vault; 

28     uint64 public withdrawalWindow; 
```
([16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L16), [19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L19), [28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L28))

```solidity
File: contracts/team/airdrop/ERC721Airdrop.sol

11     address public token; 

14     address public vault; 
```
([11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L11), [14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L14))

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol

15     bytes32 public merkleRoot; 

18     uint64 public claimStart; 

21     uint64 public claimEnd; 
```
([15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L15), [18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L18), [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L21))

```solidity
File: contracts/tokenvault/BridgedERC1155.sol

16     address public srcToken; 

19     uint256 public srcChainId; 
```
([16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L16), [19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L19))

```solidity
File: contracts/tokenvault/BridgedERC20.sol

22     address public srcToken; 

27     uint256 public srcChainId; 

30     address public snapshooter; 
```
([22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L22), [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L27), [30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L30))

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol

11     address public migratingAddress; 

14     bool public migratingInbound; 
```
([11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L11), [14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L14))

```solidity
File: contracts/tokenvault/BridgedERC721.sol

14     address public srcToken; 

17     uint256 public srcChainId; 
```
([14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L14), [17](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L17))

```solidity
File: contracts/tokenvault/adapters/USDCAdapter.sol

31     IUSDC public usdc; 
```
([31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L31))

```solidity
File: contracts/verifiers/SgxVerifier.sol

39     uint256 public nextInstanceId; 
```
([39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L39))

</details>

### [GAS&#x2011;011] Avoid updating storage when the value hasn't changed
If the old value is equal to the new value, not re-storing the value will avoid a Gsreset (2900 gas), potentially at the expense of a Gcoldsload (2100 gas) or a Gwarmaccess (100 gas)

<details>
<summary><i>There are 6 instances (click to view)</i></summary>

```solidity
File: contracts/L2/TaikoL2EIP1559Configurable.sol

25     function setConfigAndExcess( 
26         Config memory _newConfig,
27         uint64 _newGasExcess
28     )
29         external
30         virtual
31         onlyOwner
32     {
33         if (_newConfig.gasTargetPerL1Block == 0) revert L2_INVALID_CONFIG();
34         if (_newConfig.basefeeAdjustmentQuotient == 0) revert L2_INVALID_CONFIG();
35 
36         customConfig = _newConfig;
37         gasExcess = _newGasExcess;
38 
39         emit ConfigAndExcessChanged(_newConfig, _newGasExcess);
40     }
```
([25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L25-L40))

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

114     function configureQeIdentityJson(EnclaveIdStruct.EnclaveId calldata qeIdentityInput) 
115         external
116         onlyOwner
117     {
118         // 250k gas
119         qeIdentity = qeIdentityInput;
120     }
```
([114](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L114-L120))

```solidity
File: contracts/common/AddressResolver.sol

58     function __AddressResolver_init(address _addressManager) internal virtual onlyInitializing { 
59         if (block.chainid > type(uint64).max) {
60             revert RESOLVER_UNEXPECTED_CHAINID();
61         }
62         addressManager = _addressManager;
63     }
```
([58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L58-L63))

```solidity
File: contracts/common/EssentialContract.sol

119     function _storeReentryLock(uint8 _reentry) internal virtual { 
120         if (block.chainid == 1) {
121             assembly {
122                 tstore(_REENTRY_SLOT, _reentry)
123             }
124         } else {
125             __reentry = _reentry;
126         }
127     }
```
([119](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L119-L127))

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol

90     function _setConfig(uint64 _claimStart, uint64 _claimEnd, bytes32 _merkleRoot) private { 
91         claimStart = _claimStart;
92         claimEnd = _claimEnd;
93         merkleRoot = _merkleRoot;
94     }
```
([90](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L90-L94))

```solidity
File: contracts/tokenvault/BridgedERC20.sol

80     function setSnapshoter(address _snapshooter) external onlyOwner { 
81         snapshooter = _snapshooter;
82     }
```
([80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L80-L82))

</details>

### [GAS&#x2011;012] Reduce Zero-to-Non-Zero Storage Updates When You Can
Transitioning a storage variable from zero to a non-zero value incurs a total gas cost of 22,100, with 20,000 gas allocated for the write operation from zero to non-zero, and an additional 2,100 gas for cold storage access. To mitigate the high gas expenses associated with zero to non-zero storage writes, it's advisable to contemplate implementing a non-zero architecture.

<details>
<summary><i>There are 27 instances (click to view)</i></summary>

```solidity
File: contracts/L1/provers/Guardians.sol

94         minGuardians = _minGuardians; 

116             _approvals[version][_hash] |= 1 << (id - 1); 
```
([94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L94), [116](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L116))

```solidity
File: contracts/L2/CrossChainOwned.sol

73         ownerChainId = _ownerChainId; 
```
([73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L73))

```solidity
File: contracts/L2/TaikoL2.sol

96         gasExcess = _gasExcess; 

140         (basefee, gasExcess) = _calc1559BaseFee(config, _l1BlockId, _parentGasUsed); 

151             lastSyncedBlock = _l1BlockId; 
```
([96](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L96), [140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L140), [151](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L151))

```solidity
File: contracts/L2/TaikoL2EIP1559Configurable.sol

37         gasExcess = _newGasExcess; 
```
([37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L37))

```solidity
File: contracts/bridge/Bridge.sol

183             receivedAt = uint64(block.timestamp); 

240             receivedAt = uint64(block.timestamp); 
```
([183](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L183), [240](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L240))

```solidity
File: contracts/common/EssentialContract.sol

70         __paused = _TRUE; 

79         __paused = _FALSE; 

111         __paused = _FALSE; 

125             __reentry = _reentry; 
```
([70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L70), [79](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L79), [111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L111), [125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L125))

```solidity
File: contracts/signal/SignalService.sol

127             chainId = hop.chainId; 
```
([127](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L127))

```solidity
File: contracts/team/TimelockTokenPool.sol

141         totalAmountGranted += _grant.amount; 

156         totalAmountVoided += amountVoided; 

216         totalAmountWithdrawn += amountToWithdraw; 
217         totalCostPaid += costToWithdraw;
```
([141](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L141), [156](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L156), [216](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L216-L217))

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol

71         withdrawalWindow = _withdrawalWindow; 
```
([71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L71))

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol

91         claimStart = _claimStart; 
92         claimEnd = _claimEnd;
```
([91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L91-L92))

```solidity
File: contracts/tokenvault/BridgedERC1155.sol

57         srcChainId = _srcChainId; 
```
([57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L57))

```solidity
File: contracts/tokenvault/BridgedERC20.sol

74         srcChainId = _srcChainId; 
75         __srcDecimals = _decimals;
```
([74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L74-L75))

```solidity
File: contracts/tokenvault/BridgedERC721.sol

48         srcChainId = _srcChainId; 
```
([48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L48))

```solidity
File: contracts/verifiers/SgxVerifier.sol

207             validSince += INSTANCE_VALIDITY_DELAY; 

217             instances[nextInstanceId] = Instance(_instances[i], validSince); 
```
([207](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L207), [217](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L217))

</details>

### [GAS&#x2011;013] Bytes constants are more efficient than string constants
If a string can fit in 32 bytes is it better to use `bytes32` instead of `string`, as it is cheaper.


<i>There are 5 instaces of this issue:</i>

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol

17     string internal constant HEADER = "-----BEGIN CERTIFICATE-----"; 
18     string internal constant FOOTER = "-----END CERTIFICATE-----";

22     string internal constant PCK_COMMON_NAME = "Intel SGX PCK Certificate"; 
23     string internal constant PLATFORM_ISSUER_NAME = "Intel SGX PCK Platform CA";
24     string internal constant PROCESSOR_ISSUER_NAME = "Intel SGX PCK Processor CA";
```
([17](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L17-L18), [22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L22-L24))

### [GAS&#x2011;014] `bytes.concat()` can be used in place of `abi.encodePacked`
Given concatenation is not going to be used for hashing `bytes.concat` is the preferred method to use as its more gas efficient

<details>
<summary><i>There are 11 instances (click to view)</i></summary>

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

315             abi.encodePacked(authDataV3.ecdsaAttestationKey, authDataV3.qeAuthData.data); 
```
([315](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L315))

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol

181             cert.signature = abi.encodePacked(sigX, sigY); 
```
([181](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L181))

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

119         bytes memory headerBytes = abi.encodePacked( 
120             header.version,
121             header.attestationKeyType,
122             header.teeType,
123             header.qeSvn,
124             header.pceSvn,
125             header.qeVendorId,
126             header.userData
127         );

129         signedQuoteData = abi.encodePacked(headerBytes, V3Parser.packQEReport(localEnclaveReport)); 
```
([119](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L119-L127), [129](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L129))

```solidity
File: contracts/thirdparty/optimism/rlp/RLPWriter.sol

17             out_ = abi.encodePacked(_writeLength(_in.length, 128), _in); 
```
([17](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L17))

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

81         bytes memory currentNodeID = abi.encodePacked(_root); 

94                     Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID), 

100                     Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID), 
```
([81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L81), [94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L94), [100](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L100))

```solidity
File: contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol

55         hash_ = abi.encodePacked(keccak256(_key)); 
```
([55](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L55))

```solidity
File: contracts/tokenvault/BridgedERC721.sol

109             abi.encodePacked( 
110                 LibBridgedToken.buildURI(srcToken, srcChainId), Strings.toString(_tokenId)
111             )
```
([109](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L109-L111))

```solidity
File: contracts/tokenvault/LibBridgedToken.sol

54             abi.encodePacked( 
55                 "ethereum:",
56                 Strings.toHexString(uint160(_srcToken), 20),
57                 "@",
58                 Strings.toString(_srcChainId),
59                 "/tokenURI?uint256="
60             )
```
([54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L54-L60))

</details>

### [GAS&#x2011;015] `<array>.length` should not be looked up in every loop of a `for`-loop
If not cached, the solidity compiler will always read the length of the array during each iteration. That is, if it is a storage array, this is an extra sload operation (100 additional extra gas for each iteration except for the first) and if it is a memory array, this is an extra mload operation (3 additional gas for each iteration except for the first).

<details>
<summary><i>There are 29 instances (click to view)</i></summary>

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

172         for (uint256 i; i < _tierFees.length; ++i) { 
```
([172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L172))

```solidity
File: contracts/L1/libs/LibDepositing.sol

86             for (uint256 i; i < deposits_.length;) { 
```
([86](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L86))

```solidity
File: contracts/L1/libs/LibProposing.sol

244             for (uint256 i; i < params.hookCalls.length; ++i) { 
```
([244](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L244))

```solidity
File: contracts/L1/provers/Guardians.sol

74         for (uint256 i; i < guardians.length; ++i) { 

80         for (uint256 i = 0; i < _newGuardians.length; ++i) { 
```
([74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L74), [80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L80))

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

80         for (uint256 i; i < serialNumBatch.length; ++i) { 

95         for (uint256 i; i < serialNumBatch.length; ++i) { 

191         for (uint256 i; i < enclaveId.tcbLevels.length; ++i) { 

214         for (uint256 i; i < tcb.tcbLevels.length; ++i) { 
```
([80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L80), [95](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L95), [191](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L191), [214](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L214))

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol

244         for (uint256 i; i < split.length; ++i) { 
```
([244](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L244))

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

153         for (uint256 i; i < encoded.length; ++i) { 
```
([153](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L153))

```solidity
File: contracts/automata-attestation/utils/RsaVerify.sol

174         for (uint256 i; i < _sha256.length; ++i) { 

283         for (uint256 i; i < sha1Prefix.length; ++i) { 

290         for (uint256 i; i < _sha1.length; ++i) { 
```
([174](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L174), [283](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L283), [290](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L290))

```solidity
File: contracts/bridge/Bridge.sol

90         for (uint256 i; i < _msgHashes.length; ++i) { 
```
([90](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L90))

```solidity
File: contracts/signal/SignalService.sol

104         for (uint256 i; i < hopProofs.length; ++i) { 
```
([104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L104))

```solidity
File: contracts/team/airdrop/ERC721Airdrop.sol

59         for (uint256 i; i < tokenIds.length; ++i) { 
```
([59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59))

```solidity
File: contracts/thirdparty/optimism/rlp/RLPWriter.sol

66         for (uint256 j = 0; j < out_.length; j++) { 
```
([66](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66))

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

85         for (uint256 i = 0; i < proof.length; i++) { 
```
([85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85))

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

47         for (uint256 i; i < _op.amounts.length; ++i) { 

251                 for (uint256 i; i < _op.tokenIds.length; ++i) { 

269                 for (uint256 i; i < _op.tokenIds.length; ++i) { 
```
([47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L47), [251](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L251), [269](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L269))

```solidity
File: contracts/tokenvault/ERC721Vault.sol

34         for (uint256 i; i < _op.tokenIds.length; ++i) { 

170             for (uint256 i; i < _tokenIds.length; ++i) { 

175             for (uint256 i; i < _tokenIds.length; ++i) { 

197                 for (uint256 i; i < _op.tokenIds.length; ++i) { 

210                 for (uint256 i; i < _op.tokenIds.length; ++i) { 
```
([34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L34), [170](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L170), [175](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L175), [197](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L197), [210](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L210))

```solidity
File: contracts/verifiers/SgxVerifier.sol

104         for (uint256 i; i < _ids.length; ++i) { 

210         for (uint256 i; i < _instances.length; ++i) { 
```
([104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L104), [210](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210))

</details>

### [GAS&#x2011;016] Enable IR-based code generation
The IR-based code generator was introduced with an aim to not only allow code generation to be more transparent and auditable but also to enable more powerful optimization passes that span across functions.You can enable it on the command line using `--via-ir` or with the option `{"viaIR": true}`.This will take longer to compile, but you can just simple test it before deploying and if you got a better benchmark then you can add --via-ir to your deploy commandMore on: https://docs.soliditylang.org/en/v0.8.17/ir-breaking-changes.html

### [GAS&#x2011;017] Combine Sequential For Loops
Merging multiple `for` loops within a function in Solidity can enhance efficiency and reduce gas costs, especially when they share a common iterating variable or perform related operations. By minimizing redundant iterations over the same data set, execution becomes more cost-effective. However, while merging can optimize gas usage and simplify logic, it may also increase code complexity. Therefore, careful balance between optimization and maintainability is essential, along with thorough testing to ensure the refactored code behaves as expected.

<details>
<summary><i>There are 6 instances (click to view)</i></summary>

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

// @audit mergeable with L269, L251
251                 for (uint256 i; i < _op.tokenIds.length; ++i) { 

// @audit mergeable with L269, L251
269                 for (uint256 i; i < _op.tokenIds.length; ++i) { 
```
([251](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L251), [269](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L269))

```solidity
File: contracts/tokenvault/ERC721Vault.sol

// @audit mergeable with L175, L170
170             for (uint256 i; i < _tokenIds.length; ++i) { 

// @audit mergeable with L175, L170
175             for (uint256 i; i < _tokenIds.length; ++i) { 

// @audit mergeable with L210, L197
197                 for (uint256 i; i < _op.tokenIds.length; ++i) { 

// @audit mergeable with L210, L197
210                 for (uint256 i; i < _op.tokenIds.length; ++i) { 
```
([170](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L170), [175](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L175), [197](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L197), [210](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L210))

</details>

### [GAS&#x2011;018] Small `uint`s can be packed to save gas
Packing small `uint`s into the same storage slot can save gas. This is particularly useful when storing or reading multiple smaller `uint`s (e.g., `uint80`) in a single transaction.Consider using bit manipulation to pack these variables. If you pack two `uint` variables into a single `uint` storage slot, you'd perform only one `SLOAD` operation (800 gas) instead of two (1,600 gas) when you read them. This saves 800 gas for each read operation involving the two variables.Similarly, when you need to update both variables, a single `SSTORE` operation would cost you 20,000 gas instead of 40,000 gas, saving you another 20,000 gas.

<details>
<summary><i>There are 40 instances (click to view)</i></summary>

```solidity
File: contracts/L1/TaikoData.sol

15         uint64 chainId; 

20         uint64 blockMaxProposals; 

22         uint64 blockRingBufferSize; 

24         uint64 maxBlocksToVerifyPerProposal; 

26         uint32 blockMaxGasLimit; 

28         uint24 blockMaxTxListBytes; 

30         uint24 blobExpiry; 

39         uint96 livenessBond; 

46         uint64 ethDepositMinCountPerBlock; 

48         uint64 ethDepositMaxCountPerBlock; 

50         uint96 ethDepositMinAmount; 

52         uint96 ethDepositMaxAmount; 

59         uint8 blockSyncThreshold; 

64         uint16 tier; 
65         uint128 fee;

69         uint16 tier; 

83         uint24 txListByteOffset; 
84         uint24 txListByteSize;

101         uint64 id; 
102         uint32 gasLimit;
103         uint64 timestamp; // slot 7
104         uint64 l1Height;
105         uint24 txListByteOffset;
106         uint24 txListByteSize;
107         uint16 minTier;

127         uint96 validityBond; 

129         uint96 contestBond; 
130         uint64 timestamp; // slot 6 (90 bits)
131         uint16 tier;
132         uint8 contestations;

140         uint96 livenessBond; 
141         uint64 blockId; // slot 3
142         uint64 proposedAt; // timestamp
```
([15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L15), [20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L20), [22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L22), [24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L24), [26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L26), [28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L28), [30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L30), [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L39), [46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L46), [48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L48), [50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L50), [52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L52), [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L59), [64](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L64-L65), [69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L69), [83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L83-L84), [101](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L101-L107), [127](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L127), [129](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L129-L132), [140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L140-L142))

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

20         uint64 expiry; 
21         uint64 maxBlockId;
22         uint64 maxProposedIn;
```
([20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L20-L22))

```solidity
File: contracts/L1/provers/Guardians.sol

27     uint32 public version; 

30     uint32 public minGuardians; 
```
([27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L27), [30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L30))

```solidity
File: contracts/common/EssentialContract.sol

21     uint8 private __reentry; 

23     uint8 private __paused; 
```
([21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L21), [23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L23))

</details>

### [GAS&#x2011;019] Use hardcode address instead address(this)
Utilizing a hardcoded address instead of the expression address(this) can lead to better gas efficiency, particularly if the same address is employed multiple times within your contract.

This is attributed to the fact that address(this) necessitates an extra EXTCODESIZE operation to obtain the contract's address from its bytecode, thereby escalating the gas expenditure of your contract. By pre-determining and employing a hardcoded address, this additional operation can be bypassed, lowering the overall gas expense of your contract.


<details>
<summary><i>There are 40 instances (click to view)</i></summary>

```solidity
File: contracts/L1/TaikoToken.sol

61         if (_to == address(this)) revert TKO_INVALID_ADDR(); 

79         if (_to == address(this)) revert TKO_INVALID_ADDR(); 
```
([61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L61), [79](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L79))

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

125         if (address(this).balance > 0) { 
126             taikoL1Address.sendEther(address(this).balance);

151                 address(this), 
```
([125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L125-L126), [151](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L151))

```solidity
File: contracts/L1/libs/LibProposing.sol

238             uint256 tkoBalance = tko.balanceOf(address(this)); 

253                 IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }( 

260             if (address(this).balance != 0) { 
261                 msg.sender.sendEther(address(this).balance);

268             if (tko.balanceOf(address(this)) != tkoBalance + _config.livenessBond) { 
```
([238](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L238), [253](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L253), [260](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L260-L261), [268](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L268))

```solidity
File: contracts/L1/libs/LibProving.sol

242                 tko.transferFrom(msg.sender, address(this), tier.contestBond); 

384                 _tko.transferFrom(msg.sender, address(this), _tier.validityBond - reward); 
```
([242](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L242), [384](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L384))

```solidity
File: contracts/L2/CrossChainOwned.sol

50         (bool success,) = address(this).call(txdata); 
```
([50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L50))

```solidity
File: contracts/L2/TaikoL2.sol

174             _to.sendEther(address(this).balance); 

176             IERC20(_token).safeTransfer(_to, IERC20(_token).balanceOf(address(this))); 
```
([174](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L174), [176](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L176))

```solidity
File: contracts/bridge/Bridge.sol

174             if (!ISignalService(signalService).isSignalSent(address(this), msgHash)) { 

196                 _storeContext(msgHash, address(this), _message.srcChainId); 

270                 _message.to == address(0) || _message.to == address(this) 

343             _app: address(this), 

486         assert(_message.from != address(this)); 
```
([174](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L174), [196](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L196), [270](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L270), [343](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L343), [486](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L486))

```solidity
File: contracts/signal/SignalService.sol

112                 signalService = address(this); 

131         if (value == 0 || value != _loadSignalValue(address(this), signal)) { 

149         return _loadSignalValue(address(this), signal) == _chainData; 

171             chainData_ = _loadSignalValue(address(this), signal); 

245         _sendSignal(address(this), signal_, _chainData); 
```
([112](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L112), [131](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L131), [149](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L149), [171](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L171), [245](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L245))

```solidity
File: contracts/tokenvault/BridgedERC1155.sol

137         if (_to == address(this)) revert BTOKEN_CANNOT_RECEIVE(); 
```
([137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L137))

```solidity
File: contracts/tokenvault/BridgedERC20.sol

147         if (_to == address(this)) revert BTOKEN_CANNOT_RECEIVE(); 
```
([147](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L147))

```solidity
File: contracts/tokenvault/BridgedERC721.sol

125         if (_to == address(this)) revert BTOKEN_CANNOT_RECEIVE(); 
```
([125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L125))

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

108         if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO(); 

226             IERC1155(token).safeBatchTransferFrom(address(this), to, tokenIds, amounts, ""); 

272                         to: address(this), 
```
([108](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L108), [226](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L226), [272](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L272))

```solidity
File: contracts/tokenvault/ERC20Vault.sol

267         if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO(); 

378             uint256 _balance = t.balanceOf(address(this)); 
379             t.safeTransferFrom({ from: msg.sender, to: address(this), value: _amount });
380             balanceChange_ = t.balanceOf(address(this)) - _balance;
```
([267](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L267), [378](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L378-L380))

```solidity
File: contracts/tokenvault/ERC721Vault.sol

91         if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO(); 

171                 IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]); 

211                     t.safeTransferFrom(_user, address(this), _op.tokenIds[i]); 
```
([91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L91), [171](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L171), [211](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L211))

```solidity
File: contracts/tokenvault/adapters/USDCAdapter.sol

48         usdc.transferFrom(_from, address(this), _amount); 
```
([48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L48))

```solidity
File: contracts/verifiers/SgxVerifier.sol

186                 address(this), 
```
([186](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L186))

</details>

### [GAS&#x2011;020] Some checks should be done outside of the loop
Performing the same check in every iteration of the loop is expnsive in gas and unnecessary as the check remains constant throughout the loop iterations.

<details>
<summary><i>There are 8 instances (click to view)</i></summary>

```solidity
File: contracts/L1/libs/LibVerifying.sol

// @audit L145
// @audit L151
127             while (blockId < b.numBlocks && numBlocksVerified < _maxBlocksToVerify) { 
128                 slot = blockId % _config.blockRingBufferSize;
129 
130                 blk = _state.blocks[slot];
131                 if (blk.blockId != blockId) revert L1_BLOCK_MISMATCH();
132 
133                 tid = LibUtils.getTransitionId(_state, blk, slot, blockHash);
134                 // When `tid` is 0, it indicates that there is no proven
135                 // transition with its parentHash equal to the blockHash of the
136                 // most recently verified block.
137                 if (tid == 0) break;
138 
139                 // A transition with the correct `parentHash` has been located.
140                 TaikoData.TransitionState storage ts = _state.transitions[slot][tid];
141 
142                 // It's not possible to verify this block if either the
143                 // transition is contested and awaiting higher-tier proof or if
144                 // the transition is still within its cooldown period.
145                 if (ts.contester != address(0)) {
146                     break;
147                 } else {
148                     if (tierProvider == address(0)) {
149                         tierProvider = _resolver.resolve("tier_provider", false);
150                     }
151                     if (
152                         uint256(ITierProvider(tierProvider).getTier(ts.tier).cooldownWindow) * 60
153                             + uint256(ts.timestamp).max(_state.slotB.lastUnpausedAt) > block.timestamp
154                     ) {
155                         // If cooldownWindow is 0, the block can theoretically
156                         // be proved and verified within the same L1 block.
157                         break;
158                     }
159                 }
160 
161                 // Mark this block as verified
162                 blk.verifiedTransitionId = tid;
163 
164                 // Update variables
165                 blockHash = ts.blockHash;
166                 stateRoot = ts.stateRoot;
167 
168                 // We consistently return the liveness bond and the validity
169                 // bond to the actual prover of the transition utilized for
170                 // block verification. If the actual prover happens to be the
171                 // block's assigned prover, he will receive both deposits,
172                 // ultimately earning the proving fee paid during block
173                 // proposal. In contrast, if the actual prover is different from
174                 // the block's assigned prover, the liveness bond serves as a
175                 // reward to the actual prover, while the assigned prover
176                 // forfeits his liveness bond due to failure to fulfill their
177                 // commitment.
178                 uint256 bondToReturn = uint256(ts.validityBond) + blk.livenessBond;
179 
180                 // Nevertheless, it's possible for the actual prover to be the
181                 // same individual or entity as the block's assigned prover.
182                 // Consequently, we have chosen to grant the actual prover only
183                 // half of the liveness bond as a reward.
184                 if (ts.prover != blk.assignedProver) {
185                     bondToReturn -= blk.livenessBond >> 1;
186                 }
187 
188                 IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));
189                 tko.transfer(ts.prover, bondToReturn);
190 
191                 // Note: We exclusively address the bonds linked to the
192                 // transition used for verification. While there may exist
193                 // other transitions for this block, we disregard them entirely.
194                 // The bonds for these other transitions are burned either when
195                 // the transitions are generated or proven. In such cases, both
196                 // the provers and contesters of those transitions forfeit their bonds.
197 
198                 emit BlockVerified({
199                     blockId: blockId,
200                     assignedProver: blk.assignedProver,
201                     prover: ts.prover,
202                     blockHash: blockHash,
203                     stateRoot: stateRoot,
204                     tier: ts.tier,
205                     contestations: ts.contestations
206                 });
207 
208                 ++blockId;
209                 ++numBlocksVerified;
210             }
```
([127](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L127-L210))

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol

// @audit L288
// @audit L333
// @audit L303
// @audit L323
286         while (tbsPtr != 0) { 
287             uint256 internalPtr = der.firstChildOf(tbsPtr);
288             if (der[internalPtr.ixs()] != 0x06) {
289                 return (false, pcesvn, cpusvns, fmspcBytes, pceidBytes);
290             }
291 
292             if (BytesUtils.compareBytes(der.bytesAt(internalPtr), SGX_EXTENSION_OID)) {
293                 // 1.2.840.113741.1.13.1
294                 internalPtr = der.nextSiblingOf(internalPtr);
295                 uint256 extnValueParentPtr = der.rootOfOctetStringAt(internalPtr);
296                 uint256 extnValuePtr = der.firstChildOf(extnValueParentPtr);
297 
298                 // Copy flags to memory to avoid stack too deep
299                 PCKTCBFlags memory flags;
300 
// @audit L303
// @audit L323
301                 while (!(flags.fmspcFound && flags.pceidFound && flags.tcbFound)) {
302                     uint256 extnValueOidPtr = der.firstChildOf(extnValuePtr);
303                     if (der[extnValueOidPtr.ixs()] != 0x06) {
304                         return (false, pcesvn, cpusvns, fmspcBytes, pceidBytes);
305                     }
306                     if (BytesUtils.compareBytes(der.bytesAt(extnValueOidPtr), TCB_OID)) {
307                         // 1.2.840.113741.1.13.1.2
308                         (flags.tcbFound, pcesvn, cpusvns) = _findTcb(der, extnValueOidPtr);
309                     }
310                     if (BytesUtils.compareBytes(der.bytesAt(extnValueOidPtr), PCEID_OID)) {
311                         // 1.2.840.113741.1.13.1.3
312                         uint256 pceidPtr = der.nextSiblingOf(extnValueOidPtr);
313                         pceidBytes = der.bytesAt(pceidPtr);
314                         flags.pceidFound = true;
315                     }
316                     if (BytesUtils.compareBytes(der.bytesAt(extnValueOidPtr), FMSPC_OID)) {
317                         // 1.2.840.113741.1.13.1.4
318                         uint256 fmspcPtr = der.nextSiblingOf(extnValueOidPtr);
319                         fmspcBytes = der.bytesAt(fmspcPtr);
320                         flags.fmspcFound = true;
321                     }
322 
323                     if (extnValuePtr.ixl() < extnValueParentPtr.ixl()) {
324                         extnValuePtr = der.nextSiblingOf(extnValuePtr);
325                     } else {
326                         break;
327                     }
328                 }
329                 success = flags.fmspcFound && flags.pceidFound && flags.tcbFound;
330                 break;
331             }
332 
333             if (tbsPtr.ixl() < tbsParentPtr.ixl()) {
334                 tbsPtr = der.nextSiblingOf(tbsPtr);
335             } else {
336                 tbsPtr = 0; // exit
337             }
338         }
```
([286](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L286-L338))

</details>

### [GAS&#x2011;021] Consider using OZ EnumerateSet in place of nested mappings
Nested mappings and multi-dimensional arrays in Solidity operate through a process of double hashing, wherein the original storage slot and the first key are concatenated and hashed, and then this hash is again concatenated with the second key and hashed. This process can be quite gas expensive due to the double-hashing operation and subsequent storage operation (sstore).

OZ EnumerableSet provides a potential solution to this problem. It creates a data structure that combines the benefits of set operations with the ability to enumerate stored elements, which is not natively available in Solidity. EnumerableSet handles the element uniqueness internally and can therefore provide a more gas-efficient and collision-resistant alternative to nested mappings or multi-dimensional arrays in certain scenarios.

<details>
<summary><i>There are 8 instances (click to view)</i></summary>

```solidity
File: contracts/L1/TaikoData.sol

183         mapping(uint64 blockId => mapping(bytes32 parentHash => uint32 transitionId)) transitionIds; 

185         mapping( 
186             uint64 blockId_mod_blockRingBufferSize
187                 => mapping(uint32 transitionId => TransitionState ts)
188             ) transitions;
```
([183](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L183), [185](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L185-L188))

```solidity
File: contracts/L1/provers/Guardians.sol

19     mapping(uint32 version => mapping(bytes32 hash => uint256 approvalBits)) internal _approvals; 
```
([19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L19))

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

47     mapping(uint256 idx => mapping(bytes serialNum => bool revoked)) private _serialNumIsRevoked; 
```
([47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L47))

```solidity
File: contracts/common/AddressManager.sol

12     mapping(uint256 chainId => mapping(bytes32 name => address addr)) private __addresses; 
```
([12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L12))

```solidity
File: contracts/signal/SignalService.sol

17     mapping(uint64 chainId => mapping(bytes32 kind => uint64 blockId)) public topBlockId; 
```
([17](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L17))

```solidity
File: contracts/tokenvault/BaseNFTVault.sol

59     mapping(uint256 chainId => mapping(address ctoken => address btoken)) public canonicalToBridged; 
```
([59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L59))

```solidity
File: contracts/tokenvault/ERC20Vault.sol

49     mapping(uint256 chainId => mapping(address ctoken => address btoken)) public canonicalToBridged; 
```
([49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L49))

</details>

### [GAS&#x2011;022] Consider using Solady's gas optimized lib for Math
Utilizing gas-optimized math functions from libraries like [Solady](https://github.com/Vectorized/solady/blob/main/src/utils/FixedPointMathLib.sol) can lead to more efficient smart contracts.
This is particularly beneficial in contracts where these operations are frequently used.

<details>
<summary><i>There are 40 instances (click to view)</i></summary>

```solidity
File: contracts/L1/libs/LibDepositing.sol

151         return (uint256(uint160(_addr)) << 96) | _amount; 
```
([151](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L151))

```solidity
File: contracts/L1/libs/LibProposing.sol

98         if (b.numBlocks >= b.lastVerifiedBlockId + _config.blockMaxProposals + 1) { 

103             _state.blocks[(b.numBlocks - 1) % _config.blockRingBufferSize].metaHash; 
```
([98](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L98), [103](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L103))

```solidity
File: contracts/L1/libs/LibProving.sol

414         bool inProvingWindow = uint256(_ts.timestamp).max(_state.slotB.lastUnpausedAt) 
415             + _tier.provingWindow * 60 >= block.timestamp;
```
([414](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L414-L415))

```solidity
File: contracts/L1/libs/LibVerifying.sol

152                         uint256(ITierProvider(tierProvider).getTier(ts.tier).cooldownWindow) * 60 
153                             + uint256(ts.timestamp).max(_state.slotB.lastUnpausedAt) > block.timestamp
```
([152](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L152-L153))

```solidity
File: contracts/L1/provers/Guardians.sol

68         if (_minGuardians < (_newGuardians.length + 1) >> 1 || _minGuardians > _newGuardians.length) 

116             _approvals[version][_hash] |= 1 << (id - 1); 
```
([68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L68), [116](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L116))

```solidity
File: contracts/L2/Lib1559Math.sol

28         return _ethQty(_gasExcess, _adjustmentFactor) / LibFixedPointMath.SCALING_FACTOR 
29             / _adjustmentFactor;

41         uint256 input = _gasExcess * LibFixedPointMath.SCALING_FACTOR / _adjustmentFactor; 
```
([28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L28-L29), [41](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L41))

```solidity
File: contracts/L2/TaikoL2.sol

213         config_.gasTargetPerL1Block = 15 * 1e6 * 4; 

235                 uint256 j = _blockId - i - 1; 
```
([213](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L213), [235](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L235))

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

106         uint32 totalQuoteSize = 48 // header 
107             + 384 // local QE report
108             + 64 // ecdsa256BitSignature
109             + 64 // ecdsaAttestationKey
110             + 384 // QE report
111             + 64 // qeReportSignature
112             + 2 // sizeof(v3Quote.v3AuthData.qeAuthData.parsedDataSize)
113             + v3Quote.v3AuthData.qeAuthData.parsedDataSize + 2 // sizeof(v3Quote.v3AuthData.certification.certType)
114             + 4 // sizeof(v3Quote.v3AuthData.certification.certDataSize)
115             + v3Quote.v3AuthData.certification.certDataSize;

158             uint256 acc = lowerDigit * (16 ** (2 * i)); 
159             acc += upperDigit * (16 ** ((2 * i) + 1));

249         uint16 isvProdIdPackBE = (enclaveReport.isvProdId >> 8) | (enclaveReport.isvProdId << 8); 
250         uint16 isvSvnPackBE = (enclaveReport.isvSvn >> 8) | (enclaveReport.isvSvn << 8);
```
([106](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L106-L115), [158](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L158-L159), [249](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L249-L250))

```solidity
File: contracts/automata-attestation/utils/Asn1Decode.sol

112         return der.substring(ptr.ixf(), ptr.ixl() + 1 - ptr.ixf()); 

122         return der.substring(ptr.ixs(), ptr.ixl() + 1 - ptr.ixs()); 

132         return der.readBytesN(ptr.ixf(), ptr.ixl() + 1 - ptr.ixf()); 

144         uint256 len = ptr.ixl() + 1 - ptr.ixf(); 
145         return uint256(der.readBytesN(ptr.ixf(), len) >> (32 - len) * 8);
```
([112](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L112), [122](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L122), [132](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L132), [144](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L144-L145))

```solidity
File: contracts/team/TimelockTokenPool.sol

198         costToWithdraw = _amountUnlocked * r.grant.costPerToken - r.costPaid; 

264         return _amount * uint64(block.timestamp - _start) / _period; 
```
([198](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L198), [264](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L264))

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol

117         uint256 timeBasedAllowance = balance 
118             * (block.timestamp.min(claimEnd + withdrawalWindow) - claimEnd) / withdrawalWindow;
```
([117](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L117-L118))

```solidity
File: contracts/thirdparty/optimism/rlp/RLPWriter.sol

45             out_[0] = bytes1(uint8(lenLen) + uint8(_offset) + 55); 

47                 out_[i] = bytes1(uint8((_len / (256 ** (lenLen - i))) % 256)); 
```
([45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L45), [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L47))

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

142                 uint8 offset = 2 - (prefix % 2); 
```
([142](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L142))

```solidity
File: contracts/thirdparty/solmate/LibFixedPointMath.sol

33             x = (x << 78) / 5 ** 18; 

39             int256 k = ((x << 96) / 54_916_777_467_707_473_351_141_471_128 + 2 ** 95) >> 96; 
40             x = x - k * 54_916_777_467_707_473_351_141_471_128;

46             y = ((y * x) >> 96) + 57_155_421_227_552_351_082_224_309_758_442; 
47             int256 p = y + x - 94_201_549_194_550_492_254_356_042_504_812;
48             p = ((p * y) >> 96) + 28_719_021_644_029_726_153_956_944_680_412_240;
49             p = p * x + (4_385_272_521_454_847_904_659_076_985_693_276 << 96);

54             q = ((q * x) >> 96) + 50_020_603_652_535_783_019_961_831_881_945; 
55             q = ((q * x) >> 96) - 533_845_033_583_426_703_283_633_433_725_380;
56             q = ((q * x) >> 96) + 3_604_857_256_930_695_427_073_651_918_091_429;
57             q = ((q * x) >> 96) - 14_423_608_567_350_463_180_887_372_962_807_573;
58             q = ((q * x) >> 96) + 26_449_188_498_355_588_339_934_803_723_976_023;

77                 (uint256(r) * 3_822_833_074_963_236_453_042_738_258_902_158_003_155_416_615_667) 
78                     >> uint256(195 - k)
```
([33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L33), [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L39-L40), [46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L46-L49), [54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L54-L58), [77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L77-L78))

</details>

### [GAS&#x2011;023] Constructors can be marked `payable`
Payable functions cost less gas to execute, since the compiler does not have to add extra checks to ensure that a payment wasn't provided. A constructor can safely be marked as payable, since only the deployer would be able to pass funds, and the project itself would not pass any funds.

<details>
<summary><i>There are 3 instances (click to view)</i></summary>

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

54     constructor(address sigVerifyLibAddr, address pemCertLibAddr) { 
```
([54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L54))

```solidity
File: contracts/automata-attestation/utils/SigVerifyLib.sol

20     constructor(address es256Verifier) { 
```
([20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L20))

```solidity
File: contracts/common/EssentialContract.sol

64     constructor() { 
```
([64](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L64))

</details>

### [GAS&#x2011;024] Counting down in `for` statements is more gas efficient
Counting down is more gas-efficient as it avoids creating zero-to-non-zero variables and results in a gas refund when transitioning from non-zero to zero variables in the final transaction.

<details>
<summary><i>There are 40 instances (click to view)</i></summary>

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

172         for (uint256 i; i < _tierFees.length; ++i) { 
```
([172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L172))

```solidity
File: contracts/L1/libs/LibDepositing.sol

// @audit L103
86             for (uint256 i; i < deposits_.length;) { 
87                 uint256 data = _state.ethDeposits[j % _config.ethDepositRingBufferSize];
88                 deposits_[i] = TaikoData.EthDeposit({
89                     recipient: address(uint160(data >> 96)),
90                     amount: uint96(data),
91                     id: j
92                 });
93                 uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount;
94 
95                 // Unchecked is safe:
96                 // - _fee cannot be bigger than deposits_[i].amount
97                 // - all values are in the same range (uint96) except loop
98                 // counter, which obviously cannot be bigger than uint95
99                 // otherwise the function would be gassing out.
100                 unchecked {
101                     deposits_[i].amount -= _fee;
102                     totalFee += _fee;
103                     ++i;
104                     ++j;
105                 }
106             }
```
([86](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L86-L106))

```solidity
File: contracts/L1/libs/LibProposing.sol

244             for (uint256 i; i < params.hookCalls.length; ++i) { 
```
([244](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L244))

```solidity
File: contracts/L1/provers/Guardians.sol

74         for (uint256 i; i < guardians.length; ++i) { 

80         for (uint256 i = 0; i < _newGuardians.length; ++i) { 

133             for (uint256 i; i < guardiansLength; ++i) { 
```
([74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L74), [80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L80), [133](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L133))

```solidity
File: contracts/L2/TaikoL2.sol

234             for (uint256 i; i < 255 && _blockId >= i + 1; ++i) { 
```
([234](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L234))

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

80         for (uint256 i; i < serialNumBatch.length; ++i) { 

95         for (uint256 i; i < serialNumBatch.length; ++i) { 

191         for (uint256 i; i < enclaveId.tcbLevels.length; ++i) { 

214         for (uint256 i; i < tcb.tcbLevels.length; ++i) { 

240         for (uint256 i; i < CPUSVN_LENGTH; ++i) { 

259         for (uint256 i; i < n; ++i) { 

420             for (uint256 i; i < 3; ++i) { 
```
([80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L80), [95](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L95), [191](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L191), [214](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L214), [240](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L240), [259](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L259), [420](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L420))

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol

54         for (uint256 i; i < size; ++i) { 

244         for (uint256 i; i < split.length; ++i) { 

354         for (uint256 i; i < SGX_TCB_CPUSVN_SIZE + 1; ++i) { 
```
([54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L54), [244](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L244), [354](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L354))

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

153         for (uint256 i; i < encoded.length; ++i) { 

281         for (uint256 i; i < 3; ++i) { 
```
([153](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L153), [281](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L281))

```solidity
File: contracts/automata-attestation/utils/BytesUtils.sol

333         for (uint256 i; i < len; ++i) { 
```
([333](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L333))

```solidity
File: contracts/automata-attestation/utils/RsaVerify.sol

140         for (uint256 i = 2; i < 2 + paddingLen; ++i) { 

174         for (uint256 i; i < _sha256.length; ++i) { 
```
([140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L140), [174](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L174))

```solidity
File: contracts/bridge/Bridge.sol

90         for (uint256 i; i < _msgHashes.length; ++i) { 
```
([90](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L90))

```solidity
File: contracts/signal/SignalService.sol

104         for (uint256 i; i < hopProofs.length; ++i) { 
```
([104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L104))

```solidity
File: contracts/team/airdrop/ERC721Airdrop.sol

59         for (uint256 i; i < tokenIds.length; ++i) { 
```
([59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59))

```solidity
File: contracts/thirdparty/optimism/rlp/RLPWriter.sol

46             for (i = 1; i <= lenLen; i++) { 

59         for (; i < 32; i++) { 

66         for (uint256 j = 0; j < out_.length; j++) { 
```
([46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L46), [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L59), [66](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66))

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

85         for (uint256 i = 0; i < proof.length; i++) { 

// @audit L211
208         for (uint256 i = 0; i < length;) { 
209             proof_[i] = TrieNode({ encoded: _proof[i], decoded: RLPReader.readList(_proof[i]) });
210             unchecked {
211                 ++i;
212             }
213         }
```
([85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85), [208](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L208-L213))

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

47         for (uint256 i; i < _op.amounts.length; ++i) { 

251                 for (uint256 i; i < _op.tokenIds.length; ++i) { 

269                 for (uint256 i; i < _op.tokenIds.length; ++i) { 
```
([47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L47), [251](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L251), [269](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L269))

```solidity
File: contracts/tokenvault/ERC721Vault.sol

34         for (uint256 i; i < _op.tokenIds.length; ++i) { 

170             for (uint256 i; i < _tokenIds.length; ++i) { 

175             for (uint256 i; i < _tokenIds.length; ++i) { 

197                 for (uint256 i; i < _op.tokenIds.length; ++i) { 

210                 for (uint256 i; i < _op.tokenIds.length; ++i) { 
```
([34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L34), [170](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L170), [175](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L175), [197](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L197), [210](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L210))

```solidity
File: contracts/verifiers/SgxVerifier.sol

104         for (uint256 i; i < _ids.length; ++i) { 

210         for (uint256 i; i < _instances.length; ++i) { 
```
([104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L104), [210](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210))

</details>

### [GAS&#x2011;025] Variables should be declared outside of loops
By doing so we save gas cost for memory variable declaration in each iteration.

<details>
<summary><i>There are 40 instances (click to view)</i></summary>

```solidity
File: contracts/L1/libs/LibDepositing.sol

87                 uint256 data = _state.ethDeposits[j % _config.ethDepositRingBufferSize]; 

93                 uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount; 
```
([87](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L87), [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L93))

```solidity
File: contracts/L1/libs/LibVerifying.sol

140                 TaikoData.TransitionState storage ts = _state.transitions[slot][tid]; 

178                 uint256 bondToReturn = uint256(ts.validityBond) + blk.livenessBond; 

188                 IERC20 tko = IERC20(_resolver.resolve("taiko_token", false)); 
```
([140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L140), [178](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L178), [188](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L188))

```solidity
File: contracts/L1/provers/Guardians.sol

81             address guardian = _newGuardians[i]; 
```
([81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L81))

```solidity
File: contracts/L2/TaikoL2.sol

235                 uint256 j = _blockId - i - 1; 
```
([235](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L235))

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

192             EnclaveIdStruct.TcbLevel memory tcb = enclaveId.tcbLevels[i]; 

215             TCBInfoStruct.TCBLevelObj memory current = tcb.tcbLevels[i]; 
// @audit 
216             bool pceSvnIsHigherOrGreater = pck.sgxExtension.pcesvn >= current.pcesvn;
// @audit 
217             bool cpuSvnsAreHigherOrGreater = _isCpuSvnHigherOrGreater(

222                 bool tcbIsRevoked = status == TCBInfoStruct.TCBStatus.TCB_REVOKED; 

260             IPEMCertChainLib.ECSha256Certificate memory issuer; 

292             bytes32 issuerPubKeyHash = keccak256(issuer.pubKey); 

421                 bool isPckCert = i == 0; // additional parsing for PCKCert 
// @audit 
422                 bool certDecodedSuccessfully;
```
([192](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L192), [215](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L215-L217), [222](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L222), [260](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L260), [292](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L292), [421](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L421-L422))

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol

55             string memory input; 

61             uint256 increment; 

287             uint256 internalPtr = der.firstChildOf(tbsPtr); 

295                 uint256 extnValueParentPtr = der.rootOfOctetStringAt(internalPtr); 
// @audit 
296                 uint256 extnValuePtr = der.firstChildOf(extnValueParentPtr);

299                 PCKTCBFlags memory flags; 

302                     uint256 extnValueOidPtr = der.firstChildOf(extnValuePtr); 

312                         uint256 pceidPtr = der.nextSiblingOf(extnValueOidPtr); 

318                         uint256 fmspcPtr = der.nextSiblingOf(extnValueOidPtr); 
```
([55](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L55), [61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L61), [287](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L287), [295](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L295-L296), [299](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L299), [302](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L302), [312](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L312), [318](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L318))

```solidity
File: contracts/bridge/Bridge.sol

91             bytes32 msgHash = _msgHashes[i]; 
```
([91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L91))

```solidity
File: contracts/signal/SignalService.sol

107             bytes32 signalRoot = _verifyHopProof(chainId, app, signal, value, hop, signalService); 
// @audit 
108             bool isLastHop = i == hopProofs.length - 1;

120             bool isFullProof = hop.accountProof.length > 0; 

124             bytes32 kind = isFullProof ? LibSignals.STATE_ROOT : LibSignals.SIGNAL_ROOT; 
```
([107](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L107-L108), [120](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L120), [124](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L124))

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

86             TrieNode memory currentNode = proof[i]; 

134                     uint8 branchKey = uint8(key[currentKeyIndex]); 
// @audit 
135                     RLPReader.RLPItem memory nextNode = currentNode.decoded[branchKey];

140                 bytes memory path = _getNodePath(currentNode); 
// @audit 
141                 uint8 prefix = uint8(path[0]);
// @audit 
142                 uint8 offset = 2 - (prefix % 2);
// @audit 
143                 bytes memory pathRemainder = Bytes.slice(path, offset);
// @audit 
144                 bytes memory keyRemainder = Bytes.slice(key, currentKeyIndex);
// @audit 
145                 uint256 sharedNibbleLength = _getSharedNibbleLength(pathRemainder, keyRemainder);
```
([86](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L86), [134](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L134-L135), [140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L140-L145))

```solidity
File: contracts/verifiers/SgxVerifier.sol

105             uint256 idx = _ids[i]; 
```
([105](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L105))

</details>

### [GAS&#x2011;026] Do not calculate constants
Due to how constant variables are implemented (replacements at compile-time), an expression assigned to a constant variable is recomputed each time that the variable is used, which wastes some gas.

<details>
<summary><i>There are 2 instances (click to view)</i></summary>

```solidity
File: contracts/L1/libs/LibProposing.sol

21     uint256 public constant MAX_BYTES_PER_BLOB = 4096 * 32; 
```
([21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L21))

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

24     uint256 internal constant BRANCH_NODE_LENGTH = TREE_RADIX + 1; 
```
([24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L24))

</details>

### [GAS&#x2011;027] Optimize gas by using Do-While loops
Using `do-while` loops instead of `for` loops can be more gas-efficient.
Even if you add an `if` condition to account for the case where the loop doesn't execute at all, a `do-while` loop can still be cheaper in terms of gas.

<details>
<summary><i>There are 40 instances (click to view)</i></summary>

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

172         for (uint256 i; i < _tierFees.length; ++i) { 
173             if (_tierFees[i].tier == _tierId) return _tierFees[i].fee;
174         }
```
([172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L172-L174))

```solidity
File: contracts/L1/libs/LibDepositing.sol

86             for (uint256 i; i < deposits_.length;) { 
87                 uint256 data = _state.ethDeposits[j % _config.ethDepositRingBufferSize];
88                 deposits_[i] = TaikoData.EthDeposit({
89                     recipient: address(uint160(data >> 96)),
90                     amount: uint96(data),
91                     id: j
92                 });
93                 uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount;
94 
95                 // Unchecked is safe:
96                 // - _fee cannot be bigger than deposits_[i].amount
97                 // - all values are in the same range (uint96) except loop
98                 // counter, which obviously cannot be bigger than uint95
99                 // otherwise the function would be gassing out.
100                 unchecked {
101                     deposits_[i].amount -= _fee;
102                     totalFee += _fee;
103                     ++i;
104                     ++j;
105                 }
106             }
```
([86](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L86-L106))

```solidity
File: contracts/L1/libs/LibProposing.sol

244             for (uint256 i; i < params.hookCalls.length; ++i) { 
245                 if (uint160(prevHook) >= uint160(params.hookCalls[i].hook)) {
246                     revert L1_INVALID_HOOK();
247                 }
248 
249                 // When a hook is called, all ether in this contract will be send to the hook.
250                 // If the ether sent to the hook is not used entirely, the hook shall send the Ether
251                 // back to this contract for the next hook to use.
252                 // Proposers shall choose use extra hooks wisely.
253                 IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }(
254                     blk, meta_, params.hookCalls[i].data
255                 );
256 
257                 prevHook = params.hookCalls[i].hook;
258             }
```
([244](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L244-L258))

```solidity
File: contracts/L1/provers/Guardians.sol

74         for (uint256 i; i < guardians.length; ++i) { 
75             delete guardianIds[guardians[i]];
76         }

80         for (uint256 i = 0; i < _newGuardians.length; ++i) { 
81             address guardian = _newGuardians[i];
82             if (guardian == address(0)) revert INVALID_GUARDIAN();
83             // This makes sure there are not duplicate addresses
84             if (guardianIds[guardian] != 0) revert INVALID_GUARDIAN_SET();
85 
86             // Save and index the guardian
87             guardians.push(guardian);
88             guardianIds[guardian] = guardians.length;
89         }

133             for (uint256 i; i < guardiansLength; ++i) { 
134                 if (bits & 1 == 1) ++count;
135                 if (count == minGuardians) return true;
136                 bits >>= 1;
137             }
```
([74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L74-L76), [80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L80-L89), [133](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L133-L137))

```solidity
File: contracts/L2/TaikoL2.sol

234             for (uint256 i; i < 255 && _blockId >= i + 1; ++i) { 
235                 uint256 j = _blockId - i - 1;
236                 inputs[j % 255] = blockhash(j);
237             }
```
([234](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L234-L237))

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

80         for (uint256 i; i < serialNumBatch.length; ++i) { 
81             if (_serialNumIsRevoked[index][serialNumBatch[i]]) {
82                 continue;
83             }
84             _serialNumIsRevoked[index][serialNumBatch[i]] = true;
85         }

95         for (uint256 i; i < serialNumBatch.length; ++i) { 
96             if (!_serialNumIsRevoked[index][serialNumBatch[i]]) {
97                 continue;
98             }
99             delete _serialNumIsRevoked[index][serialNumBatch[i]];
100         }

191         for (uint256 i; i < enclaveId.tcbLevels.length; ++i) { 
192             EnclaveIdStruct.TcbLevel memory tcb = enclaveId.tcbLevels[i];
193             if (tcb.tcb.isvsvn <= quoteEnclaveReport.isvSvn) {
194                 tcbFound = true;
195                 status = tcb.tcbStatus;
196                 break;
197             }
198         }

214         for (uint256 i; i < tcb.tcbLevels.length; ++i) { 
215             TCBInfoStruct.TCBLevelObj memory current = tcb.tcbLevels[i];
216             bool pceSvnIsHigherOrGreater = pck.sgxExtension.pcesvn >= current.pcesvn;
217             bool cpuSvnsAreHigherOrGreater = _isCpuSvnHigherOrGreater(
218                 pck.sgxExtension.sgxTcbCompSvnArr, current.sgxTcbCompSvnArr
219             );
220             if (pceSvnIsHigherOrGreater && cpuSvnsAreHigherOrGreater) {
221                 status = current.status;
222                 bool tcbIsRevoked = status == TCBInfoStruct.TCBStatus.TCB_REVOKED;
223                 return (!tcbIsRevoked, status);
224             }
225         }

240         for (uint256 i; i < CPUSVN_LENGTH; ++i) { 
241             if (pckCpuSvns[i] < tcbCpuSvns[i]) {
242                 return false;
243             }
244         }

259         for (uint256 i; i < n; ++i) { 
260             IPEMCertChainLib.ECSha256Certificate memory issuer;
261             if (i == n - 1) {
262                 // rootCA
263                 issuer = certs[i];
264             } else {
265                 issuer = certs[i + 1];
266                 if (i == n - 2) {
267                     // this cert is expected to be signed by the root
268                     certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.ROOT)][certs[i]
269                         .serialNumber];
270                 } else if (certs[i].isPck) {
271                     certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.PCK)][certs[i]
272                         .serialNumber];
273                 }
274                 if (certRevoked) {
275                     break;
276                 }
277             }
278 
279             certNotExpired =
280                 block.timestamp > certs[i].notBefore && block.timestamp < certs[i].notAfter;
281             if (!certNotExpired) {
282                 break;
283             }
284 
285             verified = sigVerifyLib.verifyES256Signature(
286                 certs[i].tbsCertificate, certs[i].signature, issuer.pubKey
287             );
288             if (!verified) {
289                 break;
290             }
291 
292             bytes32 issuerPubKeyHash = keccak256(issuer.pubKey);
293 
294             if (issuerPubKeyHash == ROOTCA_PUBKEY_HASH) {
295                 certChainCanBeTrusted = true;
296                 break;
297             }
298         }

420             for (uint256 i; i < 3; ++i) { 
421                 bool isPckCert = i == 0; // additional parsing for PCKCert
422                 bool certDecodedSuccessfully;
423                 // todo! move decodeCert offchain
424                 (certDecodedSuccessfully, parsedQuoteCerts[i]) = pemCertLib.decodeCert(
425                     authDataV3.certification.decodedCertDataArray[i], isPckCert
426                 );
427                 if (!certDecodedSuccessfully) {
428                     return (false, retData);
429                 }
430             }
```
([80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L80-L85), [95](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L95-L100), [191](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L191-L198), [214](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L214-L225), [240](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L240-L244), [259](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L259-L298), [420](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L420-L430))

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol

54         for (uint256 i; i < size; ++i) { 
55             string memory input;
56             if (i > 0) {
57                 input = LibString.slice(pemChainStr, index, index + len);
58             } else {
59                 input = pemChainStr;
60             }
61             uint256 increment;
62             (success, certs[i], increment) = _removeHeadersAndFooters(input);
63 
64             if (!success) {
65                 return (false, certs);
66             }
67 
68             index += increment;
69         }

244         for (uint256 i; i < split.length; ++i) { 
245             contentStr = LibString.concat(contentStr, split[i]);
246         }

354         for (uint256 i; i < SGX_TCB_CPUSVN_SIZE + 1; ++i) { 
355             uint256 svnPtr = der.firstChildOf(svnParentPtr); // OID
356             uint256 svnValuePtr = der.nextSiblingOf(svnPtr); // value
357             bytes memory svnValueBytes = der.bytesAt(svnValuePtr);
358             uint16 svnValue = svnValueBytes.length < 2
359                 ? uint16(bytes2(svnValueBytes)) / 256
360                 : uint16(bytes2(svnValueBytes));
361             if (BytesUtils.compareBytes(der.bytesAt(svnPtr), PCESVN_OID)) {
362                 // pcesvn is 4 bytes in size
363                 pcesvn = uint256(svnValue);
364             } else {
365                 // each cpusvn is at maximum two bytes in size
366                 uint256 cpusvn = uint256(svnValue);
367                 cpusvns[i] = cpusvn;
368             }
369 
370             // iterate to the next svn object in the sequence
371             svnParentPtr = der.nextSiblingOf(svnParentPtr);
372         }
```
([54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L54-L69), [244](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L244-L246), [354](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L354-L372))

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

153         for (uint256 i; i < encoded.length; ++i) { 
154             uint256 digits = uint256(uint8(bytes1(encoded[i])));
155             uint256 upperDigit = digits / 16;
156             uint256 lowerDigit = digits % 16;
157 
158             uint256 acc = lowerDigit * (16 ** (2 * i));
159             acc += upperDigit * (16 ** ((2 * i) + 1));
160 
161             decoded += acc;
162         }

281         for (uint256 i; i < 3; ++i) { 
282             quoteCerts[i] = Base64.decode(string(quoteCerts[i]));
283         }
```
([153](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L153-L162), [281](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L281-L283))

```solidity
File: contracts/automata-attestation/utils/BytesUtils.sol

80         for (uint256 idx = 0; idx < shortest; idx += 32) { 
81             uint256 a;
82             uint256 b;
83             assembly {
84                 a := mload(selfptr)
85                 b := mload(otherptr)
86             }
87             if (a != b) {
88                 // Mask out irrelevant bytes and check again
89                 uint256 mask;
90                 if (shortest > 32) {
91                     mask = type(uint256).max; // aka 0xffffff....
92                 } else {
93                     mask = ~(2 ** (8 * (32 - shortest + idx)) - 1);
94                 }
95                 uint256 diff = (a & mask) - (b & mask);
96                 if (diff != 0) {
97                     return int256(diff);
98                 }
99             }
100             selfptr += 32;
101             otherptr += 32;
102         }

333         for (uint256 i; i < len; ++i) { 
334             bytes1 char = self[off + i];
335             require(char >= 0x30 && char <= 0x7A, "invalid char");
336             decoded = uint8(BASE32_HEX_TABLE[uint256(uint8(char)) - 0x30]);
337             require(decoded <= 0x20, "invalid decoded");
338             if (i == len - 1) {
339                 break;
340             }
341             ret = (ret << 5) | decoded;
342         }
```
([80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L80-L102), [333](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L333-L342))

```solidity
File: contracts/bridge/Bridge.sol

90         for (uint256 i; i < _msgHashes.length; ++i) { 
91             bytes32 msgHash = _msgHashes[i];
92             proofReceipt[msgHash].receivedAt = _timestamp;
93             emit MessageSuspended(msgHash, _suspend);
94         }
```
([90](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L90-L94))

```solidity
File: contracts/signal/SignalService.sol

104         for (uint256 i; i < hopProofs.length; ++i) { 
105             hop = hopProofs[i];
106 
107             bytes32 signalRoot = _verifyHopProof(chainId, app, signal, value, hop, signalService);
108             bool isLastHop = i == hopProofs.length - 1;
109 
110             if (isLastHop) {
111                 if (hop.chainId != block.chainid) revert SS_INVALID_LAST_HOP_CHAINID();
112                 signalService = address(this);
113             } else {
114                 if (hop.chainId == 0 || hop.chainId == block.chainid) {
115                     revert SS_INVALID_MID_HOP_CHAINID();
116                 }
117                 signalService = resolve(hop.chainId, "signal_service", false);
118             }
119 
120             bool isFullProof = hop.accountProof.length > 0;
121 
122             _cacheChainData(hop, chainId, hop.blockId, signalRoot, isFullProof, isLastHop);
123 
124             bytes32 kind = isFullProof ? LibSignals.STATE_ROOT : LibSignals.SIGNAL_ROOT;
125             signal = signalForChainData(chainId, kind, hop.blockId);
126             value = hop.rootHash;
127             chainId = hop.chainId;
128             app = signalService;
129         }
```
([104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L104-L129))

```solidity
File: contracts/team/airdrop/ERC721Airdrop.sol

59         for (uint256 i; i < tokenIds.length; ++i) { 
60             IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);
61         }
```
([59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59-L61))

```solidity
File: contracts/thirdparty/optimism/rlp/RLPWriter.sol

46             for (i = 1; i <= lenLen; i++) { 
47                 out_[i] = bytes1(uint8((_len / (256 ** (lenLen - i))) % 256));
48             }

59         for (; i < 32; i++) { 
60             if (b[i] != 0) {
61                 break;
62             }
63         }

66         for (uint256 j = 0; j < out_.length; j++) { 
67             out_[j] = b[i++];
68         }
```
([46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L46-L48), [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L59-L63), [66](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66-L68))

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

85         for (uint256 i = 0; i < proof.length; i++) { 
86             TrieNode memory currentNode = proof[i];
87 
88             // Key index should never exceed total key length or we'll be out of bounds.
89             require(currentKeyIndex <= key.length, "MerkleTrie: key index exceeds total key length");
90 
91             if (currentKeyIndex == 0) {
92                 // First proof element is always the root node.
93                 require(
94                     Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
95                     "MerkleTrie: invalid root hash"
96                 );
97             } else if (currentNode.encoded.length >= 32) {
98                 // Nodes 32 bytes or larger are hashed inside branch nodes.
99                 require(
100                     Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
101                     "MerkleTrie: invalid large internal hash"
102                 );
103             } else {
104                 // Nodes smaller than 32 bytes aren't hashed.
105                 require(
106                     Bytes.equal(currentNode.encoded, currentNodeID),
107                     "MerkleTrie: invalid internal node hash"
108                 );
109             }
110 
111             if (currentNode.decoded.length == BRANCH_NODE_LENGTH) {
112                 if (currentKeyIndex == key.length) {
113                     // Value is the last element of the decoded list (for branch nodes). There's
114                     // some ambiguity in the Merkle trie specification because bytes(0) is a
115                     // valid value to place into the trie, but for branch nodes bytes(0) can exist
116                     // even when the value wasn't explicitly placed there. Geth treats a value of
117                     // bytes(0) as "key does not exist" and so we do the same.
118                     value_ = RLPReader.readBytes(currentNode.decoded[TREE_RADIX]);
119                     require(
120                         value_.length > 0,
121                         "MerkleTrie: value length must be greater than zero (branch)"
122                     );
123 
124                     // Extra proof elements are not allowed.
125                     require(
126                         i == proof.length - 1,
127                         "MerkleTrie: value node must be last node in proof (branch)"
128                     );
129 
130                     return value_;
131                 } else {
132                     // We're not at the end of the key yet.
133                     // Figure out what the next node ID should be and continue.
134                     uint8 branchKey = uint8(key[currentKeyIndex]);
135                     RLPReader.RLPItem memory nextNode = currentNode.decoded[branchKey];
136                     currentNodeID = _getNodeID(nextNode);
137                     currentKeyIndex += 1;
138                 }
139             } else if (currentNode.decoded.length == LEAF_OR_EXTENSION_NODE_LENGTH) {
140                 bytes memory path = _getNodePath(currentNode);
141                 uint8 prefix = uint8(path[0]);
142                 uint8 offset = 2 - (prefix % 2);
143                 bytes memory pathRemainder = Bytes.slice(path, offset);
144                 bytes memory keyRemainder = Bytes.slice(key, currentKeyIndex);
145                 uint256 sharedNibbleLength = _getSharedNibbleLength(pathRemainder, keyRemainder);
146 
147                 // Whether this is a leaf node or an extension node, the path remainder MUST be a
148                 // prefix of the key remainder (or be equal to the key remainder) or the proof is
149                 // considered invalid.
150                 require(
151                     pathRemainder.length == sharedNibbleLength,
152                     "MerkleTrie: path remainder must share all nibbles with key"
153                 );
154 
155                 if (prefix == PREFIX_LEAF_EVEN || prefix == PREFIX_LEAF_ODD) {
156                     // Prefix of 2 or 3 means this is a leaf node. For the leaf node to be valid,
157                     // the key remainder must be exactly equal to the path remainder. We already
158                     // did the necessary byte comparison, so it's more efficient here to check that
159                     // the key remainder length equals the shared nibble length, which implies
160                     // equality with the path remainder (since we already did the same check with
161                     // the path remainder and the shared nibble length).
162                     require(
163                         keyRemainder.length == sharedNibbleLength,
164                         "MerkleTrie: key remainder must be identical to path remainder"
165                     );
166 
167                     // Our Merkle Trie is designed specifically for the purposes of the Ethereum
168                     // state trie. Empty values are not allowed in the state trie, so we can safely
169                     // say that if the value is empty, the key should not exist and the proof is
170                     // invalid.
171                     value_ = RLPReader.readBytes(currentNode.decoded[1]);
172                     require(
173                         value_.length > 0,
174                         "MerkleTrie: value length must be greater than zero (leaf)"
175                     );
176 
177                     // Extra proof elements are not allowed.
178                     require(
179                         i == proof.length - 1,
180                         "MerkleTrie: value node must be last node in proof (leaf)"
181                     );
182 
183                     return value_;
184                 } else if (prefix == PREFIX_EXTENSION_EVEN || prefix == PREFIX_EXTENSION_ODD) {
185                     // Prefix of 0 or 1 means this is an extension node. We move onto the next node
186                     // in the proof and increment the key index by the length of the path remainder
187                     // which is equal to the shared nibble length.
188                     currentNodeID = _getNodeID(currentNode.decoded[1]);
189                     currentKeyIndex += sharedNibbleLength;
190                 } else {
191                     revert("MerkleTrie: received a node with an unknown prefix");
192                 }
193             } else {
194                 revert("MerkleTrie: received an unparseable node");
195             }
196         }

208         for (uint256 i = 0; i < length;) { 
209             proof_[i] = TrieNode({ encoded: _proof[i], decoded: RLPReader.readList(_proof[i]) });
210             unchecked {
211                 ++i;
212             }
213         }

244         for (; shared_ < max && _a[shared_] == _b[shared_];) { 
245             unchecked {
246                 ++shared_;
247             }
248         }
```
([85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85-L196), [208](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L208-L213), [244](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L244-L248))

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

47         for (uint256 i; i < _op.amounts.length; ++i) { 
48             if (_op.amounts[i] == 0) revert VAULT_INVALID_AMOUNT();
49         }

251                 for (uint256 i; i < _op.tokenIds.length; ++i) { 
252                     BridgedERC1155(_op.token).burn(_user, _op.tokenIds[i], _op.amounts[i]);
253                 }

269                 for (uint256 i; i < _op.tokenIds.length; ++i) { 
270                     IERC1155(_op.token).safeTransferFrom({
271                         from: msg.sender,
272                         to: address(this),
273                         id: _op.tokenIds[i],
274                         amount: _op.amounts[i],
275                         data: ""
276                     });
277                 }
```
([47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L47-L49), [251](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L251-L253), [269](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L269-L277))

```solidity
File: contracts/tokenvault/ERC721Vault.sol

34         for (uint256 i; i < _op.tokenIds.length; ++i) { 
35             if (_op.amounts[i] != 0) revert VAULT_INVALID_AMOUNT();
36         }

170             for (uint256 i; i < _tokenIds.length; ++i) { 
171                 IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);
172             }

175             for (uint256 i; i < _tokenIds.length; ++i) { 
176                 BridgedERC721(token_).mint(_to, _tokenIds[i]);
177             }

197                 for (uint256 i; i < _op.tokenIds.length; ++i) { 
198                     BridgedERC721(_op.token).burn(_user, _op.tokenIds[i]);
199                 }

210                 for (uint256 i; i < _op.tokenIds.length; ++i) { 
211                     t.safeTransferFrom(_user, address(this), _op.tokenIds[i]);
212                 }
```
([34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L34-L36), [170](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L170-L172), [175](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L175-L177), [197](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L197-L199), [210](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L210-L212))

```solidity
File: contracts/verifiers/SgxVerifier.sol

104         for (uint256 i; i < _ids.length; ++i) { 
105             uint256 idx = _ids[i];
106 
107             if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();
108 
109             emit InstanceDeleted(idx, instances[idx].addr);
110 
111             delete instances[idx];
112         }

210         for (uint256 i; i < _instances.length; ++i) { 
211             if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();
212 
213             addressRegistered[_instances[i]] = true;
214 
215             if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();
216 
217             instances[nextInstanceId] = Instance(_instances[i], validSince);
218             ids[i] = nextInstanceId;
219 
220             emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);
221 
222             nextInstanceId++;
223         }
```
([104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L104-L112), [210](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210-L223))

</details>

### [GAS&#x2011;028] Avoid transferring amounts of zero in order to save gas
Skipping the external call when nothing will be transferred, will save at least **100 gas**

<details>
<summary><i>There are 11 instances (click to view)</i></summary>

```solidity
File: contracts/L1/TaikoToken.sol

// @audit check _amount
62         return super.transfer(_to, _amount); 

// @audit check _amount
80         return super.transferFrom(_from, _to, _amount); 
```
([62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L62), [80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L80))

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

// @audit check proverFee
114             IERC20(assignment.feeToken).safeTransferFrom( 
115                 _meta.coinbase, _blk.assignedProver, proverFee
116             );
```
([114](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L114-L116))

```solidity
File: contracts/L1/libs/LibVerifying.sol

// @audit check bondToReturn
189                 tko.transfer(ts.prover, bondToReturn); 
```
([189](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L189))

```solidity
File: contracts/team/TimelockTokenPool.sol

// @audit check amountToWithdraw
219         IERC20(taikoToken).transferFrom(sharedVault, _to, amountToWithdraw); 
// @audit check costToWithdraw
220         IERC20(costToken).safeTransferFrom(_recipient, sharedVault, costToWithdraw);
```
([219](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L219-L220))

```solidity
File: contracts/team/airdrop/ERC20Airdrop.sol

// @audit check amount
63         IERC20(token).transferFrom(vault, user, amount); 
```
([63](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L63))

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol

// @audit check amount
91         IERC20(token).transferFrom(vault, user, amount); 
```
([91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L91))

```solidity
File: contracts/tokenvault/ERC20Vault.sol

// @audit check _amount
330             IERC20(token_).safeTransfer(_to, _amount); 

// @audit check _amount
379             t.safeTransferFrom({ from: msg.sender, to: address(this), value: _amount }); 
```
([330](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L330), [379](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L379))

```solidity
File: contracts/tokenvault/adapters/USDCAdapter.sol

// @audit check _amount
48         usdc.transferFrom(_from, address(this), _amount); 
```
([48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L48))

</details>

### [GAS&#x2011;029] Consider moving duplicated `require()/revert()` checks to a modifier or function



<i>There are 40 instaces of this issue:</i>

```solidity
File: contracts/thirdparty/optimism/rlp/RLPReader.sol

37         require( 

56         require( 

61         require( 

112         require( 

117         require( 

152         require( 

172             require( 

182             require( 

192             require( 

202             require( 

212             require( 

217             require( 

228             require( 

238             require( 

248             require( 

258             require( 

263             require( 
```
([37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L37), [56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L56), [61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L61), [112](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L112), [117](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L117), [152](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L152), [172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L172), [182](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L182), [192](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L192), [202](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L202), [212](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L212), [217](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L217), [228](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L228), [238](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L238), [248](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L248), [258](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L258), [263](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L263))

### [GAS&#x2011;030] Emitting constants wastes gas
Every event parameter costs `Glogdata` (**8 gas**) per byte. You can avoid this extra cost, in cases where you're emitting a constant, by creating a second version of the event, which doesn't have the parameter (and have users look to the contract's variables for its value instead), and using the new event in the cases shown below.

<details>
<summary><i>There are 4 instances (click to view)</i></summary>

```solidity
File: contracts/L1/libs/LibProving.sol

230                 emit TransitionProved({ 
231                     blockId: blk.blockId,
232                     tran: _tran,
233                     prover: msg.sender,
234                     validityBond: 0,
235                     tier: _proof.tier
236                 });
```
([230](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L230-L236))

```solidity
File: contracts/L1/libs/LibVerifying.sol

73         emit BlockVerified({ 
74             blockId: 0,
75             assignedProver: address(0),
76             prover: address(0),
77             blockHash: _genesisBlockHash,
78             stateRoot: 0,
79             tier: 0,
80             contestations: 0
81         });
```
([73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L73-L81))

```solidity
File: contracts/bridge/Bridge.sol

210             emit MessageReceived(msgHash, _message, true); 

303             emit MessageReceived(msgHash, _message, false); 
```
([210](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L210), [303](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L303))

</details>

### [GAS&#x2011;031] Empty blocks should be removed or emit something
Some functions don't have a body: consider commenting why, or add some logic. Otherwise, refactor the code and remove these functions.

<details>
<summary><i>There are 5 instances (click to view)</i></summary>

```solidity
File: contracts/L1/TaikoL1.sol

220     function _authorizePause(address) 
221         internal
222         view
223         virtual
224         override
225         onlyFromOwnerOrNamed("chain_pauser")
226     { }
```
([220](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L220-L226))

```solidity
File: contracts/bridge/Bridge.sol

70     receive() external payable { } 

461     function _authorizePause(address) 
462         internal
463         view
464         virtual
465         override
466         onlyFromOwnerOrNamed("bridge_pauser")
467     { }
```
([70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L70), [461](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L461-L467))

```solidity
File: contracts/common/EssentialContract.sol

114     function _authorizeUpgrade(address) internal virtual override onlyOwner { } 

116     function _authorizePause(address) internal virtual onlyOwner { } 
```
([114](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L114), [116](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L116))

</details>

### [GAS&#x2011;032] Fixed-size arrays are cheaper than dynamic-size arrays
Using fixed-size arrays can result in large gas savings.

<details>
<summary><i>There are 40 instances (click to view)</i></summary>

```solidity
File: contracts/L1/TaikoData.sol

87         HookCall[] hookCalls; 
```
([87](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L87))

```solidity
File: contracts/L1/TaikoEvents.sol

26         TaikoData.EthDeposit[] depositsProcessed 
```
([26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L26))

```solidity
File: contracts/L1/gov/TaikoGovernor.sol

49         address[] memory _targets, 
50         uint256[] memory _values,
51         bytes[] memory _calldatas,

70         address[] memory _targets, 
71         uint256[] memory _values,
72         string[] memory _signatures,
73         bytes[] memory _calldatas,

129         address[] memory _targets, 
130         uint256[] memory _values,
131         bytes[] memory _calldatas,

141         address[] memory _targets, 
142         uint256[] memory _values,
143         bytes[] memory _calldatas,
```
([49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L49-L51), [70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L70-L73), [129](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L129-L131), [141](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L141-L143))

```solidity
File: contracts/L1/gov/TaikoTimelockController.sol

17         address[] memory nil = new address[](0); 
```
([17](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L17))

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

25         TaikoData.TierFee[] tierFees; 

165         TaikoData.TierFee[] memory _tierFees, 
```
([25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L25), [165](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L165))

```solidity
File: contracts/L1/libs/LibProposing.sol

36         TaikoData.EthDeposit[] depositsProcessed 
```
([36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L36))

```solidity
File: contracts/L1/provers/Guardians.sol

23     address[] public guardians; 

37     event GuardiansUpdated(uint32 version, address[] guardians); 

54         address[] memory _newGuardians, 
```
([23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L23), [37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L37), [54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L54))

```solidity
File: contracts/bridge/Bridge.sol

83         bytes32[] calldata _msgHashes, 
```
([83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L83))

```solidity
File: contracts/libs/LibTrieProof.sol

39         bytes[] memory _accountProof, 
40         bytes[] memory _storageProof
```
([39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L39-L40))

```solidity
File: contracts/tokenvault/BaseNFTVault.sol

33         uint256[] tokenIds; 

35         uint256[] amounts; 

93         uint256[] tokenIds, 
94         uint256[] amounts

109         uint256[] tokenIds, 
110         uint256[] amounts

129         uint256[] tokenIds, 
130         uint256[] amounts
```
([33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L33), [35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L35), [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L93-L94), [109](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L109-L110), [129](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L129-L130))

```solidity
File: contracts/tokenvault/BridgedERC1155.sol

85         uint256[] memory _tokenIds, 
86         uint256[] memory _amounts

129         uint256[] memory, /*_ids*/ 
130         uint256[] memory, /*_amounts*/
```
([85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L85-L86), [129](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L129-L130))

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

163         uint256[] calldata, 
164         uint256[] calldata,

217         uint256[] memory tokenIds, 
```
([163](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L163-L164), [217](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L217))

</details>

### [GAS&#x2011;033] Optimize names to save gas
`public`/`external` function names and `public` member variable names can be optimized to save gas. See [this](https://gist.github.com/IllIllI000/a5d8b486a8259f9f77891a919febd1a9) link for an example of how it works. Below are the interfaces/abstract contracts that can be optimized so that the most frequently-called functions use the least amount of gas possible during method lookup. Method IDs that have two leading zero bytes can save **128 gas** each during deployment, and renaming functions to have lower method IDs will save **22 gas** per call, [per sorted position shifted](https://medium.com/joyso/solidity-how-does-function-name-affect-gas-consumption-in-smart-contract-47d270d8ac92)

<details>
<summary><i>There are 38 instances (click to view)</i></summary>

```solidity
File: contracts/L1/ITaikoL1.sol

// @audit proposeBlock(), getConfig(), verifyBlocks(), proveBlock()
8 interface ITaikoL1 { 
```
([8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/ITaikoL1.sol#L8))

```solidity
File: contracts/L1/TaikoL1.sol

// @audit pauseProving(), getTransition(), proposeBlock(), getStateVariables(), canDepositEthToL2(), getConfig(), isBlobReusable(), verifyBlocks(), getBlock(), unpause(), init(), proveBlock(), depositEtherToL2(), _authorizePause()
22 contract TaikoL1 is EssentialContract, ITaikoL1, TaikoEvents, TaikoErrors { 
```
([22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L22))

```solidity
File: contracts/L1/TaikoToken.sol

// @audit init(), transfer(), burn(), snapshot(), transferFrom(), _beforeTokenTransfer(), _afterTokenTransfer(), _mint(), _burn()
15 contract TaikoToken is EssentialContract, ERC20SnapshotUpgradeable, ERC20VotesUpgradeable { 
```
([15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L15))

```solidity
File: contracts/L1/gov/TaikoGovernor.sol

// @audit propose(), proposalThreshold(), propose(), state(), votingDelay(), init(), votingPeriod(), supportsInterface(), _execute(), _cancel(), _executor()
16 contract TaikoGovernor is 
```
([16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L16))

```solidity
File: contracts/L1/gov/TaikoTimelockController.sol

// @audit getMinDelay(), init()
9 contract TaikoTimelockController is EssentialContract, TimelockControllerUpgradeable { 
```
([9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L9))

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

// @audit init(), hashAssignment(), onBlockProposed(), _getProverFee()
14 contract AssignmentHook is EssentialContract, IHook { 
```
([14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L14))

```solidity
File: contracts/L1/libs/LibUtils.sol

// @audit getBlock(), getTransition(), getTransitionId()
9 library LibUtils { 
```
([9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L9))

```solidity
File: contracts/L1/provers/Guardians.sol

// @audit setGuardians(), numGuardians(), isApproved(), approve(), deleteApproval(), isApproved()
9 abstract contract Guardians is EssentialContract { 
```
([9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L9))

```solidity
File: contracts/L1/tiers/DevnetTierProvider.sol

// @audit getTierIds(), getMinTier(), getTier(), init()
10 contract DevnetTierProvider is EssentialContract, ITierProvider { 
```
([10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L10))

```solidity
File: contracts/L1/tiers/ITierProvider.sol

// @audit getTierIds(), getMinTier(), getTier()
7 interface ITierProvider { 
```
([7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L7))

```solidity
File: contracts/L1/tiers/MainnetTierProvider.sol

// @audit getTierIds(), getMinTier(), getTier(), init()
10 contract MainnetTierProvider is EssentialContract, ITierProvider { 
```
([10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L10))

```solidity
File: contracts/L1/tiers/TestnetTierProvider.sol

// @audit getTierIds(), getMinTier(), getTier(), init()
10 contract TestnetTierProvider is EssentialContract, ITierProvider { 
```
([10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L10))

```solidity
File: contracts/L2/TaikoL2.sol

// @audit withdraw(), anchor(), getConfig(), getBasefee(), init(), skipFeeCheck(), getBlockHash(), _calcPublicInputHash(), _calc1559BaseFee()
21 contract TaikoL2 is CrossChainOwned { 
```
([21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L21))

```solidity
File: contracts/L2/TaikoL2EIP1559Configurable.sol

// @audit getConfig(), setConfigAndExcess()
9 contract TaikoL2EIP1559Configurable is TaikoL2 { 
```
([9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L9))

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

// @audit setMrSigner(), toggleLocalReportCheck(), verifyAttestation(), addRevokedCertSerialNum(), configureTcbInfoJson(), setMrEnclave(), removeRevokedCertSerialNum(), configureQeIdentityJson(), _attestationTcbIsValid(), _verify(), _verifyQEReportWithIdentity(), _checkTcbLevels(), _isCpuSvnHigherOrGreater(), _verifyCertChain(), _enclaveReportSigVerification(), verifyParsedQuote(), _verifyParsedQuote()
22 contract AutomataDcapV3Attestation is IAttestation { 
```
([22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L22))

```solidity
File: contracts/automata-attestation/interfaces/ISigVerifyLib.sol

// @audit verifyES256Signature(), verifyAttStmtSignature(), verifyRS256Signature(), verifyCertificateSignature(), verifyRS1Signature()
6 interface ISigVerifyLib { 
```
([6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L6))

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol

// @audit decodeCert(), splitCertificateChain(), _removeHeadersAndFooters(), _trimBytes(), _findPckTcbInfo(), _findTcb()
12 contract PEMCertChainLib is IPEMCertChainLib { 
```
([12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L12))

```solidity
File: contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol

// @audit decodeCert(), splitCertificateChain()
6 interface IPEMCertChainLib { 
```
([6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L6))

```solidity
File: contracts/automata-attestation/utils/SigVerifyLib.sol

// @audit verifyES256Signature(), verifyAttStmtSignature(), verifyRS256Signature(), verifyCertificateSignature(), verifyRS1Signature()
15 contract SigVerifyLib is ISigVerifyLib { 
```
([15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L15))

```solidity
File: contracts/bridge/Bridge.sol

// @audit init(), recallMessage(), signalForFailedMessage(), context(), retryMessage(), isMessageSent(), isDestChainEnabled(), getInvocationDelays(), sendMessage(), proveMessageReceived(), banAddress(), suspendMessages(), proveMessageFailed(), hashMessage(), processMessage(), _authorizePause(), _invokeMessageCall(), _updateMessageStatus(), _resetContext(), _storeContext(), _loadContext(), _proveSignalReceived()
16 contract Bridge is EssentialContract, IBridge { 
```
([16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L16))

```solidity
File: contracts/bridge/IBridge.sol

// @audit recallMessage(), context(), retryMessage(), isMessageSent(), sendMessage(), hashMessage(), processMessage()
8 interface IBridge { 
```
([8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L8))

```solidity
File: contracts/common/AddressManager.sol

// @audit setAddress(), getAddress(), init(), _authorizePause()
10 contract AddressManager is EssentialContract, IAddressManager { 
```
([10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L10))

```solidity
File: contracts/common/EssentialContract.sol

// @audit pause(), paused(), unpause(), __Essential_init(), __Essential_init(), _authorizeUpgrade(), _authorizePause(), _storeReentryLock(), _loadReentryLock(), _inNonReentrant()
10 abstract contract EssentialContract is UUPSUpgradeable, Ownable2StepUpgradeable, AddressResolver { 
```
([10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L10))

```solidity
File: contracts/signal/ISignalService.sol

// @audit getSyncedChainData(), signalForChainData(), proveSignalReceived(), sendSignal(), syncChainData(), isChainDataSynced(), isSignalSent()
12 interface ISignalService { 
```
([12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L12))

```solidity
File: contracts/signal/SignalService.sol

// @audit init(), getSyncedChainData(), signalForChainData(), getSignalSlot(), proveSignalReceived(), sendSignal(), syncChainData(), isChainDataSynced(), isSignalSent(), authorize(), _verifyHopProof(), _authorizePause(), _syncChainData(), _sendSignal(), _cacheChainData(), _loadSignalValue()
14 contract SignalService is EssentialContract, ISignalService { 
```
([14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L14))

```solidity
File: contracts/team/TimelockTokenPool.sol

// @audit getMyGrantSummary(), void(), getMyGrant(), withdraw(), grant(), withdraw(), init(), _withdraw(), _voidGrant(), _getAmountOwned(), _getAmountUnlocked(), _calcAmount(), _validateGrant(), _validateCliff()
25 contract TimelockTokenPool is EssentialContract { 
```
([25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L25))

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol

// @audit getBalance(), init(), withdraw(), claim()
12 contract ERC20Airdrop2 is MerkleClaimable { 
```
([12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L12))

```solidity
File: contracts/tokenvault/BaseVault.sol

// @audit init(), name(), supportsInterface(), checkProcessMessageContext(), checkRecallMessageContext()
12 abstract contract BaseVault is 
```
([12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L12))

```solidity
File: contracts/tokenvault/BridgedERC1155.sol

// @audit burn(), init(), mintBatch(), symbol(), mint(), name(), _beforeTokenTransfer()
14 contract BridgedERC1155 is EssentialContract, IERC1155MetadataURIUpgradeable, ERC1155Upgradeable { 
```
([14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L14))

```solidity
File: contracts/tokenvault/BridgedERC20.sol

// @audit init(), snapshot(), symbol(), decimals(), setSnapshoter(), canonical(), name(), _mintToken(), _burnToken(), _beforeTokenTransfer(), _afterTokenTransfer(), _mint(), _burn()
15 contract BridgedERC20 is 
```
([15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L15))

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol

// @audit changeMigrationStatus(), burn(), owner(), mint(), _mintToken(), _burnToken(), _isMigratingOut()
9 abstract contract BridgedERC20Base is EssentialContract, IBridgedERC20 { 
```
([9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L9))

```solidity
File: contracts/tokenvault/BridgedERC721.sol

// @audit init(), tokenURI(), burn(), symbol(), source(), mint(), name(), _beforeTokenTransfer()
12 contract BridgedERC721 is EssentialContract, ERC721Upgradeable { 
```
([12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L12))

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

// @audit symbol(), name()
16 interface IERC1155NameAndSymbol { 

// @audit onERC1155Received(), onERC1155BatchReceived(), onMessageInvocation(), onMessageRecalled(), sendToken(), name(), supportsInterface(), _transferTokens(), _handleMessage(), _getOrDeployBridgedToken(), _deployBridgedToken()
29 contract ERC1155Vault is BaseNFTVault, ERC1155ReceiverUpgradeable { 
```
([16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L16), [29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L29))

```solidity
File: contracts/tokenvault/ERC20Vault.sol

// @audit sendToken(), onMessageInvocation(), onMessageRecalled(), changeBridgedToken(), name(), _transferTokens(), _handleMessage(), _getOrDeployBridgedToken(), _deployBridgedToken()
18 contract ERC20Vault is BaseVault { 
```
([18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L18))

```solidity
File: contracts/tokenvault/ERC721Vault.sol

// @audit onMessageInvocation(), onMessageRecalled(), onERC721Received(), sendToken(), name(), _transferTokens(), _handleMessage(), _getOrDeployBridgedToken(), _deployBridgedToken()
16 contract ERC721Vault is BaseNFTVault, IERC721Receiver { 
```
([16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L16))

```solidity
File: contracts/tokenvault/IBridgedERC20.sol

// @audit changeMigrationStatus(), burn(), owner(), mint()
10 interface IBridgedERC20 { 
```
([10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/IBridgedERC20.sol#L10))

```solidity
File: contracts/verifiers/SgxVerifier.sol

// @audit init(), registerInstance(), deleteInstances(), verifyProof(), addInstances(), getSignedHash(), _addInstances(), _replaceInstance(), _isInstanceValid()
19 contract SgxVerifier is EssentialContract, IVerifier { 
```
([19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L19))

</details>

### [GAS&#x2011;034] Functions guaranteed to revert when called by normal users can be marked `payable`
If a function modifier such as `onlyOwner` is used, the function will revert if a normal user tries to pay the function. Marking the function as `payable` will lower the gas cost for legitimate callers because the compiler will not include checks for whether a payment was provided.

<details>
<summary><i>There are 40 instances (click to view)</i></summary>

```solidity
File: contracts/L1/TaikoL1.sol

220     function _authorizePause(address) 
221         internal
222         view
223         virtual
224         override
225         onlyFromOwnerOrNamed("chain_pauser")
226     { }
```
([220](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L220-L226))

```solidity
File: contracts/L1/TaikoToken.sol

47     function burn(address _from, uint256 _amount) public onlyOwner { 

52     function snapshot() public onlyFromOwnerOrNamed("snapshooter") { 
```
([47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L47), [52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L52))

```solidity
File: contracts/L1/provers/Guardians.sol

53     function setGuardians( 
54         address[] memory _newGuardians,
55         uint8 _minGuardians
56     )
57         external
58         onlyOwner
59         nonReentrant
60     {
```
([53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L53-L60))

```solidity
File: contracts/L2/CrossChainOwned.sol

60     function __CrossChainOwned_init( 
61         address _owner,
62         address _addressManager,
63         uint64 _ownerChainId
64     )
65         internal
66         virtual
67         onlyInitializing
68     {
```
([60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L60-L68))

```solidity
File: contracts/L2/TaikoL2.sol

163     function withdraw( 
164         address _token,
165         address _to
166     )
167         external
168         onlyFromOwnerOrNamed("withdrawer")
169         nonReentrant
170         whenNotPaused
171     {
```
([163](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L163-L171))

```solidity
File: contracts/L2/TaikoL2EIP1559Configurable.sol

25     function setConfigAndExcess( 
26         Config memory _newConfig,
27         uint64 _newGasExcess
28     )
29         external
30         virtual
31         onlyOwner
32     {
```
([25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L25-L32))

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

65     function setMrSigner(bytes32 _mrSigner, bool _trusted) external onlyOwner { 

69     function setMrEnclave(bytes32 _mrEnclave, bool _trusted) external onlyOwner { 

73     function addRevokedCertSerialNum( 
74         uint256 index,
75         bytes[] calldata serialNumBatch
76     )
77         external
78         onlyOwner
79     {

88     function removeRevokedCertSerialNum( 
89         uint256 index,
90         bytes[] calldata serialNumBatch
91     )
92         external
93         onlyOwner
94     {

103     function configureTcbInfoJson( 
104         string calldata fmspc,
105         TCBInfoStruct.TCBInfo calldata tcbInfoInput
106     )
107         public
108         onlyOwner
109     {

114     function configureQeIdentityJson(EnclaveIdStruct.EnclaveId calldata qeIdentityInput) 
115         external
116         onlyOwner
117     {
```
([65](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L65), [69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L69), [73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L73-L79), [88](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L88-L94), [103](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L103-L109), [114](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L114-L117))

```solidity
File: contracts/bridge/Bridge.sol

82     function suspendMessages( 
83         bytes32[] calldata _msgHashes,
84         bool _suspend
85     )
86         external
87         onlyFromOwnerOrNamed("bridge_watchdog")
88     {

101     function banAddress( 
102         address _addr,
103         bool _ban
104     )
105         external
106         onlyFromOwnerOrNamed("bridge_watchdog")
107         nonReentrant
108     {

461     function _authorizePause(address) 
462         internal
463         view
464         virtual
465         override
466         onlyFromOwnerOrNamed("bridge_pauser")
467     { }
```
([82](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L82-L88), [101](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L101-L108), [461](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L461-L467))

```solidity
File: contracts/common/AddressManager.sol

38     function setAddress( 
39         uint64 _chainId,
40         bytes32 _name,
41         address _newAddress
42     )
43         external
44         virtual
45         onlyOwner
46     {
```
([38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L38-L46))

```solidity
File: contracts/common/AddressResolver.sol

58     function __AddressResolver_init(address _addressManager) internal virtual onlyInitializing { 
```
([58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L58))

```solidity
File: contracts/common/EssentialContract.sol

95     function __Essential_init( 
96         address _owner,
97         address _addressManager
98     )
99         internal
100         virtual
101         onlyInitializing
102     {

114     function _authorizeUpgrade(address) internal virtual override onlyOwner { } 

116     function _authorizePause(address) internal virtual onlyOwner { } 
```
([95](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L95-L102), [114](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L114), [116](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L116))

```solidity
File: contracts/signal/SignalService.sol

56     function authorize(address _addr, bool _authorize) external onlyOwner { 
```
([56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L56))

```solidity
File: contracts/team/TimelockTokenPool.sol

135     function grant(address _recipient, Grant memory _grant) external onlyOwner { 

150     function void(address _recipient) external onlyOwner { 
```
([135](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L135), [150](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L150))

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol

45     function setConfig( 
46         uint64 _claimStart,
47         uint64 _claimEnd,
48         bytes32 _merkleRoot
49     )
50         external
51         onlyOwner
52     {

56     function __MerkleClaimable_init( 
57         uint64 _claimStart,
58         uint64 _claimEnd,
59         bytes32 _merkleRoot
60     )
61         internal
62         onlyInitializing
63     {
```
([45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L45-L52), [56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L56-L63))

```solidity
File: contracts/tokenvault/BaseVault.sol

47     function checkProcessMessageContext() 
48         internal
49         view
50         onlyFromBridge
51         returns (IBridge.Context memory ctx_)
52     {

58     function checkRecallMessageContext() 
59         internal
60         view
61         onlyFromBridge
62         returns (IBridge.Context memory ctx_)
63     {
```
([47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L47-L52), [58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L58-L63))

```solidity
File: contracts/tokenvault/BridgedERC1155.sol

66     function mint( 
67         address _to,
68         uint256 _tokenId,
69         uint256 _amount
70     )
71         public
72         nonReentrant
73         whenNotPaused
74         onlyFromNamed("erc1155_vault")
75     {

83     function mintBatch( 
84         address _to,
85         uint256[] memory _tokenIds,
86         uint256[] memory _amounts
87     )
88         public
89         nonReentrant
90         whenNotPaused
91         onlyFromNamed("erc1155_vault")
92     {

100     function burn( 
101         address _account,
102         uint256 _tokenId,
103         uint256 _amount
104     )
105         public
106         nonReentrant
107         whenNotPaused
108         onlyFromNamed("erc1155_vault")
109     {
```
([66](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L66-L75), [83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L83-L92), [100](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L100-L109))

```solidity
File: contracts/tokenvault/BridgedERC20.sol

80     function setSnapshoter(address _snapshooter) external onlyOwner { 

85     function snapshot() external onlyOwnerOrSnapshooter { 
```
([80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L80), [85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L85))

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol

36     function changeMigrationStatus( 
37         address _migratingAddress,
38         bool _migratingInbound
39     )
40         external
41         nonReentrant
42         whenNotPaused
43         onlyFromOwnerOrNamed("erc20_vault")
44     {
```
([36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L36-L44))

```solidity
File: contracts/tokenvault/BridgedERC721.sol

54     function mint( 
55         address _account,
56         uint256 _tokenId
57     )
58         public
59         nonReentrant
60         whenNotPaused
61         onlyFromNamed("erc721_vault")
62     {

69     function burn( 
70         address _account,
71         uint256 _tokenId
72     )
73         public
74         nonReentrant
75         whenNotPaused
76         onlyFromNamed("erc721_vault")
77     {
```
([54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L54-L62), [69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L69-L77))

```solidity
File: contracts/tokenvault/ERC20Vault.sol

148     function changeBridgedToken( 
149         CanonicalERC20 calldata _ctoken,
150         address _btokenNew
151     )
152         external
153         nonReentrant
154         whenNotPaused
155         onlyOwner
156         returns (address btokenOld_)
157     {
```
([148](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L148-L157))

```solidity
File: contracts/verifiers/SgxVerifier.sol

90     function addInstances(address[] calldata _instances) 
91         external
92         onlyOwner
93         returns (uint256[] memory)
94     {

100     function deleteInstances(uint256[] calldata _ids) 
101         external
102         onlyFromOwnerOrNamed("rollup_watchdog")
103     {

139     function verifyProof( 
140         Context calldata _ctx,
141         TaikoData.Transition calldata _tran,
142         TaikoData.TierProof calldata _proof
143     )
144         external
145         onlyFromNamed("taiko")
146     {
```
([90](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L90-L94), [100](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L100-L103), [139](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L139-L146))

</details>

### [GAS&#x2011;035] Initializers can be marked `payable`
<details>
<summary><i>There are 24 instances (click to view)</i></summary>

```solidity
File: contracts/L1/TaikoL1.sol

42     function init( 
43         address _owner,
44         address _addressManager,
45         bytes32 _genesisBlockHash
46     )
47         external
48         initializer
49     {
```
([42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L42-L49))

```solidity
File: contracts/L1/TaikoToken.sol

25     function init( 
26         address _owner,
27         string calldata _name,
28         string calldata _symbol,
29         address _recipient
30     )
31         public
32         initializer
33     {
```
([25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L25-L33))

```solidity
File: contracts/L1/gov/TaikoGovernor.sol

31     function init( 
32         address _owner,
33         IVotesUpgradeable _token,
34         TimelockControllerUpgradeable _timelock
35     )
36         external
37         initializer
38     {
```
([31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L31-L38))

```solidity
File: contracts/L1/gov/TaikoTimelockController.sol

15     function init(address _owner, uint256 _minDelay) external initializer { 
```
([15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L15))

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

57     function init(address _owner, address _addressManager) external initializer { 
```
([57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L57))

```solidity
File: contracts/L1/provers/GuardianProver.sol

25     function init(address _owner, address _addressManager) external initializer { 
```
([25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L25))

```solidity
File: contracts/L1/tiers/DevnetTierProvider.sol

15     function init(address _owner) external initializer { 
```
([15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L15))

```solidity
File: contracts/L1/tiers/MainnetTierProvider.sol

15     function init(address _owner) external initializer { 
```
([15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L15))

```solidity
File: contracts/L1/tiers/TestnetTierProvider.sol

15     function init(address _owner) external initializer { 
```
([15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L15))

```solidity
File: contracts/L2/TaikoL2.sol

71     function init( 
72         address _owner,
73         address _addressManager,
74         uint64 _l1ChainId,
75         uint64 _gasExcess
76     )
77         external
78         initializer
79     {
```
([71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L71-L79))

```solidity
File: contracts/bridge/Bridge.sol

75     function init(address _owner, address _addressManager) external initializer { 
```
([75](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L75))

```solidity
File: contracts/common/AddressManager.sol

30     function init(address _owner) external initializer { 
```
([30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L30))

```solidity
File: contracts/signal/SignalService.sol

48     function init(address _owner, address _addressManager) external initializer { 
```
([48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L48))

```solidity
File: contracts/team/TimelockTokenPool.sol

111     function init( 
112         address _owner,
113         address _taikoToken,
114         address _costToken,
115         address _sharedVault
116     )
117         external
118         initializer
119     {
```
([111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L111-L119))

```solidity
File: contracts/team/airdrop/ERC20Airdrop.sol

27     function init( 
28         address _owner,
29         uint64 _claimStart,
30         uint64 _claimEnd,
31         bytes32 _merkleRoot,
32         address _token,
33         address _vault
34     )
35         external
36         initializer
37     {
```
([27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L27-L37))

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol

54     function init( 
55         address _owner,
56         uint64 _claimStart,
57         uint64 _claimEnd,
58         bytes32 _merkleRoot,
59         address _token,
60         address _vault,
61         uint64 _withdrawalWindow
62     )
63         external
64         initializer
65     {
```
([54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L54-L65))

```solidity
File: contracts/team/airdrop/ERC721Airdrop.sol

25     function init( 
26         address _owner,
27         uint64 _claimStart,
28         uint64 _claimEnd,
29         bytes32 _merkleRoot,
30         address _token,
31         address _vault
32     )
33         external
34         initializer
35     {
```
([25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L25-L35))

```solidity
File: contracts/tokenvault/BaseVault.sol

32     function init(address _owner, address _addressManager) external initializer { 
```
([32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L32))

```solidity
File: contracts/tokenvault/BridgedERC1155.sol

38     function init( 
39         address _owner,
40         address _addressManager,
41         address _srcToken,
42         uint256 _srcChainId,
43         string memory _symbol,
44         string memory _name
45     )
46         external
47         initializer
48     {
```
([38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L38-L48))

```solidity
File: contracts/tokenvault/BridgedERC20.sol

52     function init( 
53         address _owner,
54         address _addressManager,
55         address _srcToken,
56         uint256 _srcChainId,
57         uint8 _decimals,
58         string memory _symbol,
59         string memory _name
60     )
61         external
62         initializer
63     {
```
([52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L52-L63))

```solidity
File: contracts/tokenvault/BridgedERC721.sol

31     function init( 
32         address _owner,
33         address _addressManager,
34         address _srcToken,
35         uint256 _srcChainId,
36         string memory _symbol,
37         string memory _name
38     )
39         external
40         initializer
41     {
```
([31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L31-L41))

```solidity
File: contracts/tokenvault/adapters/USDCAdapter.sol

38     function init(address _owner, address _addressManager, IUSDC _usdc) external initializer { 
```
([38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L38))

```solidity
File: contracts/verifiers/GuardianVerifier.sol

18     function init(address _owner, address _addressManager) external initializer { 
```
([18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L18))

```solidity
File: contracts/verifiers/SgxVerifier.sol

83     function init(address _owner, address _addressManager) external initializer { 
```
([83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L83))

</details>

### [GAS&#x2011;036] Inline `modifier`s that are only used once, to save gas
<details>
<summary><i>There are 40 instances (click to view)</i></summary>

```solidity
File: contracts/common/EssentialContract.sol

// @audit used only once @ contracts/common/EssentialContract.sol#78
53     modifier whenPaused() { 
54         if (!paused()) revert INVALID_PAUSE_STATUS();
55         _;
56     }
```
([53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L53-L56))

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol

// @audit used only once @ contracts/team/airdrop/ERC20Airdrop2.sol#88
39     modifier ongoingWithdrawals() { 
40         if (claimEnd > block.timestamp || claimEnd + withdrawalWindow < block.timestamp) {
41             revert WITHDRAWALS_NOT_ONGOING();
42         }
// @audit used only once @ contracts/team/airdrop/ERC20Airdrop2.sol#88
43         _;
44     }
```
([39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L39-L44))

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol

33     modifier ongoingClaim() { 
34         if (
35             merkleRoot == 0x0 || claimStart == 0 || claimEnd == 0 || claimStart > block.timestamp
36                 || claimEnd < block.timestamp
37         ) revert CLAIM_NOT_ONGOING();
38         _;
39     }
```
([33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L33-L39))

```solidity
File: contracts/tokenvault/BridgedERC20.sol

37     modifier onlyOwnerOrSnapshooter() { 
38         if (msg.sender != owner() && msg.sender != snapshooter) {
39             revert BTOKEN_UNAUTHORIZED();
40         }
41         _;
42     }
```
([37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L37-L42))

</details>

### [GAS&#x2011;037] Integer increments by one can be unchecked
Integer increments by one can be unchecked to save on gas fees

<details>
<summary><i>There are 40 instances (click to view)</i></summary>

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

172         for (uint256 i; i < _tierFees.length; ++i) { 
```
([172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L172))

```solidity
File: contracts/L1/libs/LibProposing.sol

244             for (uint256 i; i < params.hookCalls.length; ++i) { 
```
([244](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L244))

```solidity
File: contracts/L1/libs/LibProving.sol

252                 ts.contestations += 1; 

377             _ts.contestations += 1; 
```
([252](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L252), [377](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L377))

```solidity
File: contracts/L1/provers/Guardians.sol

74         for (uint256 i; i < guardians.length; ++i) { 

80         for (uint256 i = 0; i < _newGuardians.length; ++i) { 

92         ++version; 
```
([74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L74), [80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L80), [92](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L92))

```solidity
File: contracts/L2/CrossChainOwned.sol

53         emit TransactionExecuted(nextTxId++, bytes4(txdata)); 
```
([53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L53))

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

80         for (uint256 i; i < serialNumBatch.length; ++i) { 

95         for (uint256 i; i < serialNumBatch.length; ++i) { 

191         for (uint256 i; i < enclaveId.tcbLevels.length; ++i) { 

214         for (uint256 i; i < tcb.tcbLevels.length; ++i) { 

240         for (uint256 i; i < CPUSVN_LENGTH; ++i) { 

259         for (uint256 i; i < n; ++i) { 

420             for (uint256 i; i < 3; ++i) { 
```
([80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L80), [95](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L95), [191](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L191), [214](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L214), [240](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L240), [259](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L259), [420](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L420))

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol

54         for (uint256 i; i < size; ++i) { 

244         for (uint256 i; i < split.length; ++i) { 

354         for (uint256 i; i < SGX_TCB_CPUSVN_SIZE + 1; ++i) { 
```
([54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L54), [244](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L244), [354](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L354))

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

153         for (uint256 i; i < encoded.length; ++i) { 

281         for (uint256 i; i < 3; ++i) { 
```
([153](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L153), [281](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L281))

```solidity
File: contracts/automata-attestation/utils/BytesUtils.sol

333         for (uint256 i; i < len; ++i) { 
```
([333](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L333))

```solidity
File: contracts/bridge/Bridge.sol

90         for (uint256 i; i < _msgHashes.length; ++i) { 

144         message_.id = nextMessageId++; 
```
([90](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L90), [144](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L144))

```solidity
File: contracts/signal/SignalService.sol

104         for (uint256 i; i < hopProofs.length; ++i) { 
```
([104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L104))

```solidity
File: contracts/team/airdrop/ERC721Airdrop.sol

59         for (uint256 i; i < tokenIds.length; ++i) { 
```
([59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59))

```solidity
File: contracts/thirdparty/optimism/rlp/RLPReader.sol

89             itemCount += 1; 
```
([89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L89))

```solidity
File: contracts/thirdparty/optimism/rlp/RLPWriter.sol

40                 lenLen++; 

46             for (i = 1; i <= lenLen; i++) { 

59         for (; i < 32; i++) { 

66         for (uint256 j = 0; j < out_.length; j++) { 
67             out_[j] = b[i++];
```
([40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L40), [46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L46), [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L59), [66](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66-L67))

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

85         for (uint256 i = 0; i < proof.length; i++) { 

137                     currentKeyIndex += 1; 
```
([85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85), [137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L137))

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

47         for (uint256 i; i < _op.amounts.length; ++i) { 
```
([47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L47))

```solidity
File: contracts/tokenvault/ERC721Vault.sol

34         for (uint256 i; i < _op.tokenIds.length; ++i) { 

170             for (uint256 i; i < _tokenIds.length; ++i) { 

175             for (uint256 i; i < _tokenIds.length; ++i) { 
```
([34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L34), [170](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L170), [175](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L175))

```solidity
File: contracts/verifiers/SgxVerifier.sol

104         for (uint256 i; i < _ids.length; ++i) { 

210         for (uint256 i; i < _instances.length; ++i) { 

222             nextInstanceId++; 
```
([104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L104), [210](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210), [222](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L222))

</details>

### [GAS&#x2011;038] Low-level `call` can be optimized with assembly
`returnData` is copied to memory even if the variable is not utilized: the proper way to handle this is through a low level assembly call and save **159** [gas](https://gist.github.com/IllIllI000/0e18a40f3afb0b83f9a347b10ee89ad2).

```solidity
 // before (bool success,) = payable(receiver).call{gas: gas, value: value}("");
//after bool success; assembly { success := call(gas, receiver, value, 0, 0, 0, 0) }
```


<details>
<summary><i>There are 3 instances (click to view)</i></summary>

```solidity
File: contracts/L2/CrossChainOwned.sol

50         (bool success,) = address(this).call(txdata); 
```
([50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L50))

```solidity
File: contracts/automata-attestation/utils/SigVerifyLib.sol

137         (bool success, bytes memory ret) = ES256VERIFIER.staticcall(args); 
```
([137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L137))

```solidity
File: contracts/bridge/Bridge.sol

591         (success_,) = _signalService.staticcall(data); 
```
([591](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L591))

</details>

### [GAS&#x2011;039] Mappings are cheaper to use than storage arrays
When using storage arrays, solidity adds an internal lookup of the array's length (a Gcoldsload **2100 gas**) to ensure you don't read past the array's end. You can avoid this lookup by using a `mapping` and storing the number of entries in a separate storage variable. In cases where you have sentinel values (e.g. 'zero' means invalid), you can avoid length checks

<details>
<summary><i>There are 40 instances (click to view)</i></summary>

```solidity
File: contracts/L1/TaikoData.sol

87         HookCall[] hookCalls; 

195         uint256[43] __gap; 
```
([87](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L87), [195](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L195))

```solidity
File: contracts/L1/TaikoL1.sol

26     uint256[50] private __gap; 
```
([26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L26))

```solidity
File: contracts/L1/TaikoToken.sol

16     uint256[50] private __gap; 
```
([16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L16))

```solidity
File: contracts/L1/gov/TaikoGovernor.sol

23     uint256[50] private __gap; 
```
([23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L23))

```solidity
File: contracts/L1/gov/TaikoTimelockController.sol

10     uint256[50] private __gap; 
```
([10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L10))

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

25         TaikoData.TierFee[] tierFees; 

40     uint256[50] private __gap; 
```
([25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L25), [40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L40))

```solidity
File: contracts/L1/provers/GuardianProver.sol

11     uint256[50] private __gap; 
```
([11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L11))

```solidity
File: contracts/L1/provers/Guardians.sol

23     address[] public guardians; 

32     uint256[46] private __gap; 
```
([23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L23), [32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L32))

```solidity
File: contracts/L1/tiers/DevnetTierProvider.sol

11     uint256[50] private __gap; 
```
([11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L11))

```solidity
File: contracts/L1/tiers/MainnetTierProvider.sol

11     uint256[50] private __gap; 
```
([11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L11))

```solidity
File: contracts/L1/tiers/TestnetTierProvider.sol

11     uint256[50] private __gap; 
```
([11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L11))

```solidity
File: contracts/L2/CrossChainOwned.sol

21     uint256[49] private __gap; 
```
([21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L21))

```solidity
File: contracts/L2/TaikoL2.sol

52     uint256[47] private __gap; 
```
([52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L52))

```solidity
File: contracts/L2/TaikoL2EIP1559Configurable.sol

13     uint256[49] private __gap; 
```
([13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L13))

```solidity
File: contracts/bridge/Bridge.sol

48     uint256[43] private __gap; 
```
([48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L48))

```solidity
File: contracts/common/AddressManager.sol

14     uint256[49] private __gap; 
```
([14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L14))

```solidity
File: contracts/common/AddressResolver.sol

14     uint256[49] private __gap; 
```
([14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L14))

```solidity
File: contracts/common/EssentialContract.sol

25     uint256[49] private __gap; 
```
([25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L25))

```solidity
File: contracts/signal/ISignalService.sol

25         bytes[] accountProof; 
26         bytes[] storageProof;
```
([25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L25-L26))

```solidity
File: contracts/signal/SignalService.sol

23     uint256[48] private __gap; 
```
([23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L23))

```solidity
File: contracts/team/airdrop/ERC20Airdrop.sol

18     uint256[48] private __gap; 
```
([18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L18))

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

17         RLPReader.RLPItem[] decoded; 
```
([17](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L17))

```solidity
File: contracts/tokenvault/BaseNFTVault.sol

33         uint256[] tokenIds; 

35         uint256[] amounts; 

61     uint256[48] private __gap; 
```
([33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L33), [35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L35), [61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L61))

```solidity
File: contracts/tokenvault/BaseVault.sol

18     uint256[50] private __gap; 
```
([18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L18))

```solidity
File: contracts/tokenvault/BridgedERC1155.sol

27     uint256[46] private __gap; 
```
([27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L27))

```solidity
File: contracts/tokenvault/BridgedERC20.sol

32     uint256[47] private __gap; 
```
([32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L32))

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol

16     uint256[49] private __gap; 
```
([16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L16))

```solidity
File: contracts/tokenvault/BridgedERC721.sol

19     uint256[48] private __gap; 
```
([19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L19))

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

32     uint256[50] private __gap; 
```
([32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L32))

```solidity
File: contracts/tokenvault/ERC20Vault.sol

54     uint256[47] private __gap; 
```
([54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L54))

```solidity
File: contracts/tokenvault/ERC721Vault.sol

19     uint256[50] private __gap; 
```
([19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L19))

```solidity
File: contracts/tokenvault/adapters/USDCAdapter.sol

32     uint256[49] private __gap; 
```
([32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L32))

```solidity
File: contracts/verifiers/GuardianVerifier.sol

11     uint256[50] private __gap; 
```
([11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L11))

```solidity
File: contracts/verifiers/SgxVerifier.sol

57     uint256[47] private __gap; 
```
([57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L57))

</details>

### [GAS&#x2011;040] Memory-safe annotation missing
Use `assembly ("memory-safe") { ... }` for the assembly blocks below since they dont't read or modify memory, and therefore are [memory-safe](https://docs.soliditylang.org/en/latest/assembly.html#memory-safety). This will help the optimizer to create more optimal gas-efficient code. Use the comment variant if prior to Solidity version 0.8.13

<details>
<summary><i>There are 20 instances (click to view)</i></summary>

```solidity
File: contracts/automata-attestation/utils/SHA1.sol

22             switch lt(sub(totallen, len), 9) 
23             case 1 { totallen := add(totallen, 64) }

31                     count := sub(count, off) 
32                     if lt(count, 32) {
33                         let mask := not(sub(exp(256, sub(32, count)), 1))
34                         result := and(result, mask)
35                     }

38  
39             for { let i := 0 } lt(i, totallen) { i := add(i, 64) } {

44                 switch lt(sub(len, i), 64) 
45                 case 1 { mstore8(add(scratch, sub(len, i)), 0x80) }

51                 // Expand the 16 32-bit words into 80 
52                 for { let j := 64 } lt(j, 128) { j := add(j, 12) } {

70                 } 
71                 for { let j := 128 } lt(j, 320) { j := add(j, 24) } {

93                 let k := 0 
94                 for { let j := 0 } lt(j, 80) { j := add(j, 1) } {
95                     switch div(j, 20)
96                     case 0 {
97                         // f = d xor (b and (c xor d))
98                         f := xor(div(x, 0x100000000000000000000), div(x, 0x10000000000))
99                         f := and(div(x, 0x1000000000000000000000000000000), f)
100                         f := xor(div(x, 0x10000000000), f)
101                         k := 0x5A827999
102                     }
103                     case 1 {
104                         // f = b xor c xor d
105                         f :=
106                             xor(
107                                 div(x, 0x1000000000000000000000000000000),
108                                 div(x, 0x100000000000000000000)
109                             )
110                         f := xor(div(x, 0x10000000000), f)
111                         k := 0x6ED9EBA1
112                     }
113                     case 2 {
114                         // f = (b and c) or (d and (b or c))
115                         f :=
116                             or(
117                                 div(x, 0x1000000000000000000000000000000),
118                                 div(x, 0x100000000000000000000)
119                             )
120                         f := and(div(x, 0x10000000000), f)
121                         f :=
122                             or(
123                                 and(
124                                     div(x, 0x1000000000000000000000000000000),
125                                     div(x, 0x100000000000000000000)
126                                 ),
127                                 f
128                             )
129                         k := 0x8F1BBCDC
130                     }
131                     case 3 {
132                         // f = b xor c xor d
133                         f :=
134                             xor(
135                                 div(x, 0x1000000000000000000000000000000),
136                                 div(x, 0x100000000000000000000)
137                             )
138                         f := xor(div(x, 0x10000000000), f)
139                         k := 0xCA62C1D6
140                     }
```
([22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SHA1.sol#L22-L23), [31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SHA1.sol#L31-L35), [38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SHA1.sol#L38-L39), [44](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SHA1.sol#L44-L45), [51](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SHA1.sol#L51-L52), [70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SHA1.sol#L70-L71), [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SHA1.sol#L93-L140))

```solidity
File: contracts/thirdparty/optimism/Bytes.sol

59                     let cc := add(add(add(_bytes, lengthmod), mul(0x20, iszero(lengthmod))), _start) 
60                 } lt(mc, end) {
61                     mc := add(mc, 0x20)
62                     cc := add(cc, 0x20)
63                 } { mstore(mc, mload(cc)) }

129             // Loop through each byte in the input array 
130             for { let i := 0x00 } lt(i, bytesLength) { i := add(i, 0x01) } {
```
([59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L59-L63), [129](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L129-L130))

```solidity
File: contracts/thirdparty/optimism/rlp/RLPReader.sol

297             let i := 0 
298             for { } lt(i, _length) { i := add(i, 32) } { mstore(add(dest, i), mload(add(src, i))) }
```
([297](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L297-L298))

</details>

### [GAS&#x2011;041] Merge events to save gas
Consolidating multiple event emissions into a single event in Solidity saves gas by reducing the cost per topic. This is crucial in functions emitting multiple related events. However, it's important to balance gas optimization with event data clarity for off-chain consumers.

<details>
<summary><i>There are 5 instances (click to view)</i></summary>

```solidity
File: contracts/L1/libs/LibProposing.sol

77     { 
78         TaikoData.BlockParams memory params = abi.decode(_data, (TaikoData.BlockParams));
79 
80         // We need a prover that will submit proofs after the block has been submitted
81         if (params.assignedProver == address(0)) {
82             revert L1_INVALID_PROVER();
83         }
84 
85         if (params.coinbase == address(0)) {
86             params.coinbase = msg.sender;
87         }
88 
89         // Taiko, as a Based Rollup, enables permissionless block proposals.
90         // However, if the "proposer" address is set to a non-zero value, we
91         // ensure that only that specific address has the authority to propose
92         // blocks.
93         TaikoData.SlotB memory b = _state.slotB;
94         if (!_isProposerPermitted(b, _resolver)) revert L1_UNAUTHORIZED();
95 
96         // It's essential to ensure that the ring buffer for proposed blocks
97         // still has space for at least one more block.
98         if (b.numBlocks >= b.lastVerifiedBlockId + _config.blockMaxProposals + 1) {
99             revert L1_TOO_MANY_BLOCKS();
100         }
101 
102         bytes32 parentMetaHash =
103             _state.blocks[(b.numBlocks - 1) % _config.blockRingBufferSize].metaHash;
104 
105         // Check if parent block has the right meta hash
106         // This is to allow the proposer to make sure the block builds on the expected latest chain
107         // state
108         if (params.parentMetaHash != 0 && parentMetaHash != params.parentMetaHash) {
109             revert L1_UNEXPECTED_PARENT();
110         }
111 
112         // Each transaction must handle a specific quantity of L1-to-L2
113         // Ether deposits.
114         deposits_ = LibDepositing.processDeposits(_state, _config, params.coinbase);
115 
116         // Initialize metadata to compute a metaHash, which forms a part of
117         // the block data to be stored on-chain for future integrity checks.
118         // If we choose to persist all data fields in the metadata, it will
119         // require additional storage slots.
120         unchecked {
121             meta_ = TaikoData.BlockMetadata({
122                 l1Hash: blockhash(block.number - 1),
123                 difficulty: 0, // to be initialized below
124                 blobHash: 0, // to be initialized below
125                 extraData: params.extraData,
126                 depositsHash: keccak256(abi.encode(deposits_)),
127                 coinbase: params.coinbase,
128                 id: b.numBlocks,
129                 gasLimit: _config.blockMaxGasLimit,
130                 timestamp: uint64(block.timestamp),
131                 l1Height: uint64(block.number - 1),
132                 txListByteOffset: 0, // to be initialized below
133                 txListByteSize: 0, // to be initialized below
134                 minTier: 0, // to be initialized below
135                 blobUsed: _txList.length == 0,
136                 parentMetaHash: parentMetaHash
137             });
138         }
139 
140         // Update certain meta fields
141         if (meta_.blobUsed) {
142             if (!_config.blobAllowedForDA) revert L1_BLOB_FOR_DA_DISABLED();
143 
144             if (params.blobHash != 0) {
145                 if (!_config.blobReuseEnabled) revert L1_BLOB_REUSE_DISABLED();
146 
147                 // We try to reuse an old blob
148                 if (!isBlobReusable(_state, _config, params.blobHash)) {
149                     revert L1_BLOB_NOT_REUSABLE();
150                 }
151                 meta_.blobHash = params.blobHash;
152             } else {
153                 // Always use the first blob in this transaction. If the
154                 // proposeBlock functions are called more than once in the same
155                 // L1 transaction, these multiple L2 blocks will share the same
156                 // blob.
157                 meta_.blobHash = blockhash(0);
158 
159                 if (meta_.blobHash == 0) revert L1_BLOB_NOT_FOUND();
160 
161                 // Depends on the blob data price, it may not make sense to
162                 // cache the blob which costs 20,000 (sstore) + 631 (event)
163                 // extra gas.
164                 if (_config.blobReuseEnabled && params.cacheBlobForReuse) {
165                     _state.reusableBlobs[meta_.blobHash] = block.timestamp;
166                     emit BlobCached(meta_.blobHash);
167                 }
168             }
169 
170             // Check that the txList data range is within the max size of a blob
171             if (uint256(params.txListByteOffset) + params.txListByteSize > MAX_BYTES_PER_BLOB) {
172                 revert L1_TXLIST_OFFSET();
173             }
174 
175             meta_.txListByteOffset = params.txListByteOffset;
176             meta_.txListByteSize = params.txListByteSize;
177         } else {
178             // The proposer must be an Externally Owned Account (EOA) for
179             // calldata usage. This ensures that the transaction is not an
180             // internal one, making calldata retrieval more straightforward for
181             // Taiko node software.
182             if (!LibAddress.isSenderEOA()) revert L1_PROPOSER_NOT_EOA();
183 
184             // The txList is the full byte array without any offset
185             if (params.txListByteOffset != 0) {
186                 revert L1_INVALID_PARAM();
187             }
188 
189             meta_.blobHash = keccak256(_txList);
190             meta_.txListByteOffset = 0;
191             meta_.txListByteSize = uint24(_txList.length);
192         }
193 
194         // Check that the tx length is non-zero and within the supported range
195         if (meta_.txListByteSize == 0 || meta_.txListByteSize > _config.blockMaxTxListBytes) {
196             revert L1_TXLIST_SIZE();
197         }
198 
199         // Following the Merge, the L1 mixHash incorporates the
200         // prevrandao value from the beacon chain. Given the possibility
201         // of multiple Taiko blocks being proposed within a single
202         // Ethereum block, we choose to introduce a salt to this random
203         // number as the L2 mixHash.
204         meta_.difficulty = keccak256(abi.encodePacked(block.prevrandao, b.numBlocks, block.number));
205 
206         // Use the difficulty as a random number
207         meta_.minTier = ITierProvider(_resolver.resolve("tier_provider", false)).getMinTier(
208             uint256(meta_.difficulty)
209         );
210 
211         // Create the block that will be stored onchain
212         TaikoData.Block memory blk = TaikoData.Block({
213             metaHash: keccak256(abi.encode(meta_)),
214             // Safeguard the liveness bond to ensure its preservation,
215             // particularly in scenarios where it might be altered after the
216             // block's proposal but before it has been proven or verified.
217             livenessBond: _config.livenessBond,
218             blockId: b.numBlocks,
219             proposedAt: meta_.timestamp,
220             proposedIn: uint64(block.number),
221             // For a new block, the next transition ID is always 1, not 0.
222             nextTransitionId: 1,
223             // For unverified block, its verifiedTransitionId is always 0.
224             verifiedTransitionId: 0,
225             assignedProver: params.assignedProver
226         });
227 
228         // Store the block in the ring buffer
229         _state.blocks[b.numBlocks % _config.blockRingBufferSize] = blk;
230 
231         // Increment the counter (cursor) by 1.
232         unchecked {
233             ++_state.slotB.numBlocks;
234         }
235 
236         {
237             IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));
238             uint256 tkoBalance = tko.balanceOf(address(this));
239 
240             // Run all hooks.
241             // Note that address(this).balance has been updated with msg.value,
242             // prior to any code in this function has been executed.
243             address prevHook;
244             for (uint256 i; i < params.hookCalls.length; ++i) {
245                 if (uint160(prevHook) >= uint160(params.hookCalls[i].hook)) {
246                     revert L1_INVALID_HOOK();
247                 }
248 
249                 // When a hook is called, all ether in this contract will be send to the hook.
250                 // If the ether sent to the hook is not used entirely, the hook shall send the Ether
251                 // back to this contract for the next hook to use.
252                 // Proposers shall choose use extra hooks wisely.
253                 IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }(
254                     blk, meta_, params.hookCalls[i].data
255                 );
256 
257                 prevHook = params.hookCalls[i].hook;
258             }
259             // Refund Ether
260             if (address(this).balance != 0) {
261                 msg.sender.sendEther(address(this).balance);
262             }
263 
264             // Check that after hooks, the Taiko Token balance of this contract
265             // have increased by the same amount as _config.livenessBond (to prevent)
266             // multiple draining payments by a malicious proposer nesting the same
267             // hook.
268             if (tko.balanceOf(address(this)) != tkoBalance + _config.livenessBond) {
269                 revert L1_LIVENESS_BOND_NOT_RECEIVED();
270             }
271         }
272 
273         emit BlockProposed({
274             blockId: blk.blockId,
275             assignedProver: blk.assignedProver,
276             livenessBond: _config.livenessBond,
277             meta: meta_,
278             depositsProcessed: deposits_
279         });
280     }
```
([77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L77-L280))

```solidity
File: contracts/L1/libs/LibProving.sol

101     { 
102         // Make sure parentHash is not zero
103         // To contest an existing transition, simply use any non-zero value as
104         // the blockHash and stateRoot.
105         if (_tran.parentHash == 0 || _tran.blockHash == 0 || _tran.stateRoot == 0) {
106             revert L1_INVALID_TRANSITION();
107         }
108 
109         // Check that the block has been proposed but has not yet been verified.
110         TaikoData.SlotB memory b = _state.slotB;
111         if (_meta.id <= b.lastVerifiedBlockId || _meta.id >= b.numBlocks) {
112             revert L1_INVALID_BLOCK_ID();
113         }
114 
115         uint64 slot = _meta.id % _config.blockRingBufferSize;
116         TaikoData.Block storage blk = _state.blocks[slot];
117 
118         // Check the integrity of the block data. It's worth noting that in
119         // theory, this check may be skipped, but it's included for added
120         // caution.
121         if (blk.blockId != _meta.id || blk.metaHash != keccak256(abi.encode(_meta))) {
122             revert L1_BLOCK_MISMATCH();
123         }
124 
125         // Each transition is uniquely identified by the parentHash, with the
126         // blockHash and stateRoot open for later updates as higher-tier proofs
127         // become available. In cases where a transition with the specified
128         // parentHash does not exist, the transition ID (tid) will be set to 0.
129         (uint32 tid, TaikoData.TransitionState storage ts) =
130             _createTransition(_state, blk, _tran, slot);
131 
132         // The new proof must meet or exceed the minimum tier required by the
133         // block or the previous proof; it cannot be on a lower tier.
134         if (_proof.tier == 0 || _proof.tier < _meta.minTier || _proof.tier < ts.tier) {
135             revert L1_INVALID_TIER();
136         }
137 
138         // Retrieve the tier configurations. If the tier is not supported, the
139         // subsequent action will result in a revert.
140         ITierProvider.Tier memory tier =
141             ITierProvider(_resolver.resolve("tier_provider", false)).getTier(_proof.tier);
142 
143         // Check if this prover is allowed to submit a proof for this block
144         _checkProverPermission(_state, blk, ts, tid, tier);
145 
146         // We must verify the proof, and any failure in proof verification will
147         // result in a revert.
148         //
149         // It's crucial to emphasize that the proof can be assessed in two
150         // potential modes: "proving mode" and "contesting mode." However, the
151         // precise verification logic is defined within each tier's IVerifier
152         // contract implementation. We simply specify to the verifier contract
153         // which mode it should utilize - if the new tier is higher than the
154         // previous tier, we employ the proving mode; otherwise, we employ the
155         // contesting mode (the new tier cannot be lower than the previous tier,
156         // this has been checked above).
157         //
158         // It's obvious that proof verification is entirely decoupled from
159         // Taiko's core protocol.
160         {
161             address verifier = _resolver.resolve(tier.verifierName, true);
162 
163             if (verifier != address(0)) {
164                 bool isContesting = _proof.tier == ts.tier && tier.contestBond != 0;
165 
166                 IVerifier.Context memory ctx = IVerifier.Context({
167                     metaHash: blk.metaHash,
168                     blobHash: _meta.blobHash,
169                     // Separate msgSender to allow the prover to be any address in the future.
170                     prover: msg.sender,
171                     msgSender: msg.sender,
172                     blockId: blk.blockId,
173                     isContesting: isContesting,
174                     blobUsed: _meta.blobUsed
175                 });
176 
177                 IVerifier(verifier).verifyProof(ctx, _tran, _proof);
178             } else if (tier.verifierName != TIER_OP) {
179                 // The verifier can be address-zero, signifying that there are no
180                 // proof checks for the tier. In practice, this only applies to
181                 // optimistic proofs.
182                 revert L1_MISSING_VERIFIER();
183             }
184         }
185 
186         bool isTopTier = tier.contestBond == 0;
187         IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));
188 
189         if (isTopTier) {
190             // A special return value from the top tier prover can signal this
191             // contract to return all liveness bond.
192             bool returnLivenessBond = blk.livenessBond > 0 && _proof.data.length == 32
193                 && bytes32(_proof.data) == RETURN_LIVENESS_BOND;
194 
195             if (returnLivenessBond) {
196                 tko.transfer(blk.assignedProver, blk.livenessBond);
197                 blk.livenessBond = 0;
198             }
199         }
200 
201         bool sameTransition = _tran.blockHash == ts.blockHash && _tran.stateRoot == ts.stateRoot;
202 
203         if (_proof.tier > ts.tier) {
204             // Handles the case when an incoming tier is higher than the current transition's tier.
205             // Reverts when the incoming proof tries to prove the same transition
206             // (L1_ALREADY_PROVED).
207             _overrideWithHigherProof(ts, _tran, _proof, tier, tko, sameTransition);
208 
209             emit TransitionProved({
210                 blockId: blk.blockId,
211                 tran: _tran,
212                 prover: msg.sender,
213                 validityBond: tier.validityBond,
214                 tier: _proof.tier
215             });
216         } else {
217             // New transition and old transition on the same tier - and if this transaction tries to
218             // prove the same, it reverts
219             if (sameTransition) revert L1_ALREADY_PROVED();
220 
221             if (isTopTier) {
222                 // The top tier prover re-proves.
223                 assert(tier.validityBond == 0);
224                 assert(ts.validityBond == 0 && ts.contestBond == 0 && ts.contester == address(0));
225 
226                 ts.prover = msg.sender;
227                 ts.blockHash = _tran.blockHash;
228                 ts.stateRoot = _tran.stateRoot;
229 
230                 emit TransitionProved({
231                     blockId: blk.blockId,
232                     tran: _tran,
233                     prover: msg.sender,
234                     validityBond: 0,
235                     tier: _proof.tier
236                 });
237             } else {
238                 // Contesting but not on the highest tier
239                 if (ts.contester != address(0)) revert L1_ALREADY_CONTESTED();
240 
241                 // Burn the contest bond from the prover.
242                 tko.transferFrom(msg.sender, address(this), tier.contestBond);
243 
244                 // We retain the contest bond within the transition, just in
245                 // case this configuration is altered to a different value
246                 // before the contest is resolved.
247                 //
248                 // It's worth noting that the previous value of ts.contestBond
249                 // doesn't have any significance.
250                 ts.contestBond = tier.contestBond;
251                 ts.contester = msg.sender;
252                 ts.contestations += 1;
253 
254                 emit TransitionContested({
255                     blockId: blk.blockId,
256                     tran: _tran,
257                     contester: msg.sender,
258                     contestBond: tier.contestBond,
259                     tier: _proof.tier
260                 });
261             }
262         }
263 
264         ts.timestamp = uint64(block.timestamp);
265         return tier.maxBlocksToVerifyPerProof;
266     }
```
([101](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L101-L266))

```solidity
File: contracts/bridge/Bridge.sol

163     { 
164         bytes32 msgHash = hashMessage(_message);
165 
166         if (messageStatus[msgHash] != Status.NEW) revert B_STATUS_MISMATCH();
167 
168         uint64 receivedAt = proofReceipt[msgHash].receivedAt;
169         bool isMessageProven = receivedAt != 0;
170 
171         if (!isMessageProven) {
172             address signalService = resolve("signal_service", false);
173 
174             if (!ISignalService(signalService).isSignalSent(address(this), msgHash)) {
175                 revert B_MESSAGE_NOT_SENT();
176             }
177 
178             bytes32 failureSignal = signalForFailedMessage(msgHash);
179             if (!_proveSignalReceived(signalService, failureSignal, _message.destChainId, _proof)) {
180                 revert B_NOT_FAILED();
181             }
182 
183             receivedAt = uint64(block.timestamp);
184             proofReceipt[msgHash].receivedAt = receivedAt;
185         }
186 
187         (uint256 invocationDelay,) = getInvocationDelays();
188 
189         if (block.timestamp >= invocationDelay + receivedAt) {
190             delete proofReceipt[msgHash];
191             messageStatus[msgHash] = Status.RECALLED;
192 
193             // Execute the recall logic based on the contract's support for the
194             // IRecallableSender interface
195             if (_message.from.supportsInterface(type(IRecallableSender).interfaceId)) {
196                 _storeContext(msgHash, address(this), _message.srcChainId);
197 
198                 // Perform recall
199                 IRecallableSender(_message.from).onMessageRecalled{ value: _message.value }(
200                     _message, msgHash
201                 );
202 
203                 // Must reset the context after the message call
204                 _resetContext();
205             } else {
206                 _message.srcOwner.sendEther(_message.value);
207             }
208             emit MessageRecalled(msgHash);
209         } else if (!isMessageProven) {
210             emit MessageReceived(msgHash, _message, true);
211         } else {
212             revert B_INVOCATION_TOO_EARLY();
213         }
214     }

225     { 
226         bytes32 msgHash = hashMessage(_message);
227         if (messageStatus[msgHash] != Status.NEW) revert B_STATUS_MISMATCH();
228 
229         address signalService = resolve("signal_service", false);
230         uint64 receivedAt = proofReceipt[msgHash].receivedAt;
231         bool isMessageProven = receivedAt != 0;
232 
233         (uint256 invocationDelay, uint256 invocationExtraDelay) = getInvocationDelays();
234 
235         if (!isMessageProven) {
236             if (!_proveSignalReceived(signalService, msgHash, _message.srcChainId, _proof)) {
237                 revert B_NOT_RECEIVED();
238             }
239 
240             receivedAt = uint64(block.timestamp);
241 
242             if (invocationDelay != 0) {
243                 proofReceipt[msgHash] = ProofReceipt({
244                     receivedAt: receivedAt,
245                     preferredExecutor: _message.gasLimit == 0 ? _message.destOwner : msg.sender
246                 });
247             }
248         }
249 
250         if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) {
251             // If msg.sender is not the one that proved the message, then there
252             // is an extra delay.
253             unchecked {
254                 invocationDelay += invocationExtraDelay;
255             }
256         }
257 
258         if (block.timestamp >= invocationDelay + receivedAt) {
259             // If the gas limit is set to zero, only the owner can process the message.
260             if (_message.gasLimit == 0 && msg.sender != _message.destOwner) {
261                 revert B_PERMISSION_DENIED();
262             }
263 
264             delete proofReceipt[msgHash];
265 
266             uint256 refundAmount;
267 
268             // Process message differently based on the target address
269             if (
270                 _message.to == address(0) || _message.to == address(this)
271                     || _message.to == signalService || addressBanned[_message.to]
272             ) {
273                 // Handle special addresses that don't require actual invocation but
274                 // mark message as DONE
275                 refundAmount = _message.value;
276                 _updateMessageStatus(msgHash, Status.DONE);
277             } else {
278                 // Use the specified message gas limit if called by the owner, else
279                 // use remaining gas
280                 uint256 gasLimit = msg.sender == _message.destOwner ? gasleft() : _message.gasLimit;
281 
282                 if (_invokeMessageCall(_message, msgHash, gasLimit)) {
283                     _updateMessageStatus(msgHash, Status.DONE);
284                 } else {
285                     _updateMessageStatus(msgHash, Status.RETRIABLE);
286                 }
287             }
288 
289             // Determine the refund recipient
290             address refundTo =
291                 _message.refundTo == address(0) ? _message.destOwner : _message.refundTo;
292 
293             // Refund the processing fee
294             if (msg.sender == refundTo) {
295                 refundTo.sendEther(_message.fee + refundAmount);
296             } else {
297                 // If sender is another address, reward it and refund the rest
298                 msg.sender.sendEther(_message.fee);
299                 refundTo.sendEther(refundAmount);
300             }
301             emit MessageExecuted(msgHash);
302         } else if (!isMessageProven) {
303             emit MessageReceived(msgHash, _message, false);
304         } else {
305             revert B_INVOCATION_TOO_EARLY();
306         }
307     }
```
([163](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L163-L214), [225](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L225-L307))

</details>

### [GAS&#x2011;042] Multiple accesses of the same mapping/array key/index should be cached
The instances below point to the second+ access of a value inside a mapping/array key/index, within a function. Caching a mapping's value in a local storage or calldata variable when the value is accessed [multiple times](https://gist.github.com/IllIllI000/ec23a57daa30a8f8ca8b9681c8ccefb0), saves ~42 gas per access due to not having to recalculate the key's keccak256 hash (Gkeccak256 - 30 gas) and that calculation's associated stack operations. Caching an array's struct avoids recalculating the array offsets into memory/calldata

<details>
<summary><i>There are 29 instances (click to view)</i></summary>

```solidity
File: contracts/L1/libs/LibProving.sol

// @audit _state.transitions[slot][tid_]accessed again on line 299
// @audit _state.transitions[slot]accessed again on line 299
345             ts_ = _state.transitions[slot][tid_]; 
```
([345](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L345))

```solidity
File: contracts/L1/libs/LibVerifying.sol

// @audit _state.blocks[slot]accessed again on line 104
130                 blk = _state.blocks[slot]; 

// @audit _state.transitions[slot][tid]accessed again on line 115
// @audit _state.transitions[slot]accessed again on line 115
140                 TaikoData.TransitionState storage ts = _state.transitions[slot][tid]; 
```
([130](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L130), [140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L140))

```solidity
File: contracts/L1/provers/Guardians.sol

// @audit guardianIds[guardian]accessed again on line 84
88             guardianIds[guardian] = guardians.length; 

// @audit _approvals[version][_hash]accessed again on line 116
// @audit _approvals[version]accessed again on line 116
119         uint256 _approval = _approvals[version][_hash]; 
```
([88](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L88), [119](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L119))

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

// @audit _serialNumIsRevoked[index]accessed again on line 81
84             _serialNumIsRevoked[index][serialNumBatch[i]] = true; 

// @audit parsedQuoteCerts[0]accessed again on line 435
// @audit parsedQuoteCerts[0]accessed again on line 442
// @audit parsedQuoteCerts[0]accessed again on line 454
472                 parsedQuoteCerts[0].pubKey, 
```
([84](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L84), [472](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L472))

```solidity
File: contracts/automata-attestation/utils/X509DateUtils.sol

// @audit x509Time[0]accessed again on line 18
21             yrs += (uint8(x509Time[0]) - 48) * 1000 + (uint8(x509Time[1]) - 48) * 100; 
```
([21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L21))

```solidity
File: contracts/bridge/Bridge.sol

// @audit addressBanned[_addr]accessed again on line 109
110         addressBanned[_addr] = _ban; 

// @audit proofReceipt[msgHash]accessed again on line 168
184             proofReceipt[msgHash].receivedAt = receivedAt; 

// @audit messageStatus[msgHash]accessed again on line 166
191             messageStatus[msgHash] = Status.RECALLED; 

// @audit proofReceipt[msgHash]accessed again on line 230
// @audit proofReceipt[msgHash]accessed again on line 243
250         if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) { 

// @audit messageStatus[_msgHash]accessed again on line 516
518         messageStatus[_msgHash] = _status; 
```
([110](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L110), [184](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L184), [191](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L191), [250](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L250), [518](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L518))

```solidity
File: contracts/common/AddressManager.sol

// @audit __addresses[_chainId][_name]accessed again on line 47
// @audit __addresses[_chainId]accessed again on line 47
49         __addresses[_chainId][_name] = _newAddress; 
```
([49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L49))

```solidity
File: contracts/signal/SignalService.sol

// @audit isAuthorized[_addr]accessed again on line 57
58         isAuthorized[_addr] = _authorize; 

// @audit topBlockId[_chainId][_kind]accessed again on line 247
// @audit topBlockId[_chainId]accessed again on line 247
248             topBlockId[_chainId][_kind] = _blockId; 
```
([58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L58), [248](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L248))

```solidity
File: contracts/team/TimelockTokenPool.sol

// @audit recipients[_recipient]accessed again on line 137
142         recipients[_recipient].grant = _grant; 
```
([142](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L142))

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol

// @audit isClaimed[hash]accessed again on line 70
73         isClaimed[hash] = true; 
```
([73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L73))

```solidity
File: contracts/thirdparty/optimism/rlp/RLPWriter.sol

// @audit out_[0]accessed again on line 35
45             out_[0] = bytes1(uint8(lenLen) + uint8(_offset) + 55); 
```
([45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L45))

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

// @audit currentNode.decoded[1]accessed again on line 171
188                     currentNodeID = _getNodeID(currentNode.decoded[1]); 
```
([188](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L188))

```solidity
File: contracts/tokenvault/ERC20Vault.sol

// @audit bridgedToCanonical[_btokenNew]accessed again on line 158
188         bridgedToCanonical[_btokenNew] = _ctoken; 

// @audit bridgedToCanonical[_token]accessed again on line 358
359             ctoken_ = bridgedToCanonical[_token]; 
```
([188](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L188), [359](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L359))

```solidity
File: contracts/verifiers/SgxVerifier.sol

// @audit instances[idx]accessed again on line 107
109             emit InstanceDeleted(idx, instances[idx].addr); 

// @audit instances[id]accessed again on line 235
// @audit instances[id]accessed again on line 236
237             && block.timestamp <= instances[id].validSince + INSTANCE_EXPIRY; 
```
([109](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L109), [237](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L237))

</details>

### [GAS&#x2011;043] Multiple mappings can be replaced with a single struct mapping
Saves a storage slot for the mapping. Depending on the circumstances and sizes of types, can avoid a Gsset (**20000 gas**) per mapping combined. Reads and subsequent writes can also be cheaper when a function requires both values and they both fit in the same storage slot. Finally, if both fields are accessed in the same function, can save **~42 gas per access** due to [not having to recalculate the key's keccak256 hash](https://gist.github.com/IllIllI000/ec23a57daa30a8f8ca8b9681c8ccefb0) (Gkeccak256 - **30 gas**) and that calculation's associated stack operations.

<details>
<summary><i>There are 10 instances (click to view)</i></summary>

```solidity
File: contracts/L1/TaikoData.sol

183         mapping(uint64 blockId => mapping(bytes32 parentHash => uint32 transitionId)) transitionIds; 

190         mapping(uint256 depositId_mod_ethDepositRingBufferSize => uint256 depositAmount) ethDeposits; 
```
([183](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L183), [190](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L190))

```solidity
File: contracts/L1/provers/Guardians.sol

16     mapping(address guardian => uint256 id) public guardianIds; 

19     mapping(uint32 version => mapping(bytes32 hash => uint256 approvalBits)) internal _approvals; 
```
([16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L16), [19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L19))

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol

22     mapping(address addr => uint256 amountClaimed) public claimedAmount; 

25     mapping(address addr => uint256 amountWithdrawn) public withdrawnAmount; 
```
([22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L22), [25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L25))

```solidity
File: contracts/tokenvault/BaseNFTVault.sol

59     mapping(uint256 chainId => mapping(address ctoken => address btoken)) public canonicalToBridged; 
```
([59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L59))

```solidity
File: contracts/tokenvault/ERC20Vault.sol

49     mapping(uint256 chainId => mapping(address ctoken => address btoken)) public canonicalToBridged; 
```
([49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L49))

</details>

### [GAS&#x2011;044] Nested for loops should be avoided due to high gas costs resulting from O^2 time complexity
In Solidity, avoiding nested loops is crucial due to their high gas costs, especially for large datasets. Nested loops can lead to quadratic time complexity, significantly increasing gas costs. Users pay for gas, so minimizing gas usage is vital. To optimize efficiency, limit loop usage, reduce iteration ranges, and minimize computations. Alternative patterns like map/filter/reduce are often cheaper in terms of gas usage.


<i>There is one instance of this issue:</i>

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol

286         while (tbsPtr != 0) { 
```
([286](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L286))

### [GAS&#x2011;045] The use of a logical AND in place of double if is slightly less gas efficient in instances where there isn't a corresponding else statement for the given if statement
Using a double if statement instead of logical AND (&&) can provide similar short-circuiting behavior whereas double if is slightly more efficient.

<details>
<summary><i>There are 27 instances (click to view)</i></summary>

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

120         if (input.tip != 0 && block.coinbase != address(0)) { 
```
([120](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L120))

```solidity
File: contracts/L1/libs/LibProposing.sol

108         if (params.parentMetaHash != 0 && parentMetaHash != params.parentMetaHash) { 

164                 if (_config.blobReuseEnabled && params.cacheBlobForReuse) { 

310             if (proposerOne != address(0) && msg.sender != proposerOne) { 
```
([108](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L108), [164](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L164), [310](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L310))

```solidity
File: contracts/L1/libs/LibProving.sol

419         if (_tid == 1 && _ts.tier == 0 && inProvingWindow) { 
```
([419](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L419))

```solidity
File: contracts/L2/TaikoL2.sol

141         if (!skipFeeCheck() && block.basefee != basefee) { 

275             if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) { 
```
([141](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L141), [275](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L275))

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

220             if (pceSvnIsHigherOrGreater && cpuSvnsAreHigherOrGreater) { 
```
([220](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L220))

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

77         require( 

82         require( 

94         require( 
```
([77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L77), [82](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L82), [94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L94))

```solidity
File: contracts/automata-attestation/utils/BytesUtils.sol

335             require(char >= 0x30 && char <= 0x7A, "invalid char"); 
```
([335](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L335))

```solidity
File: contracts/bridge/Bridge.sol

250         if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) { 

260             if (_message.gasLimit == 0 && msg.sender != _message.destOwner) { 

439         } else if (block.chainid >= 32_300 && block.chainid <= 32_400) { 

490         if ( 
491             _message.data.length >= 4 // msg can be empty
492                 && bytes4(_message.data) != IMessageInvocable.onMessageInvocation.selector
493                 && _message.to.isContract()
```
([250](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L250), [260](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L260), [439](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L439), [490](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L490-L493))

```solidity
File: contracts/common/AddressResolver.sol

85         if (!_allowZeroAddress && addr_ == address(0)) { 
```
([85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L85))

```solidity
File: contracts/common/EssentialContract.sol

42         if (msg.sender != owner() && msg.sender != resolve(_name, true)) revert RESOLVER_DENIED(); 
```
([42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L42))

```solidity
File: contracts/signal/SignalService.sol

285         if (cacheStateRoot && _isFullProof && !_isLastHop) { 

293         if (cacheSignalRoot && (_isFullProof || !_isLastHop)) { 
```
([285](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L285), [293](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L293))

```solidity
File: contracts/team/TimelockTokenPool.sol

277             if (_cliff > 0 && _cliff <= _start) revert INVALID_GRANT(); 
```
([277](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L277))

```solidity
File: contracts/thirdparty/optimism/rlp/RLPWriter.sol

14         if (_in.length == 1 && uint8(_in[0]) < 128) { 
```
([14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L14))

```solidity
File: contracts/tokenvault/BridgedERC20.sol

38         if (msg.sender != owner() && msg.sender != snapshooter) { 
```
([38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L38))

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol

45         if (_migratingAddress == migratingAddress && _migratingInbound == migratingInbound) { 
```
([45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L45))

</details>

### [GAS&#x2011;046] Not using the named return variables
Not using named return variables when a function returns, wastes deployment gas.

<details>
<summary><i>There are 40 instances (click to view)</i></summary>

```solidity
File: contracts/L1/ITaikoL1.sol

14     function proposeBlock( 
15         bytes calldata _params,
16         bytes calldata _txList
17     )
18         external
19         payable
20         returns (TaikoData.BlockMetadata memory meta_, TaikoData.EthDeposit[] memory deposits_);
```
([14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/ITaikoL1.sol#L14-L20))

```solidity
File: contracts/L1/TaikoL1.sol

55     function proposeBlock( 
56         bytes calldata _params,
57         bytes calldata _txList
58     )
59         external
60         payable
61         nonReentrant
62         whenNotPaused
63         returns (TaikoData.BlockMetadata memory meta_, TaikoData.EthDeposit[] memory deposits_)
64     {
65         TaikoData.Config memory config = getConfig();
66 
67         (meta_, deposits_) = LibProposing.proposeBlock(state, config, this, _params, _txList);
68 
69         if (!state.slotB.provingPaused) {
70             LibVerifying.verifyBlocks(state, config, this, config.maxBlocksToVerifyPerProposal);
71         }
72     }

145     function getBlock(uint64 _blockId) 
146         public
147         view
148         returns (TaikoData.Block memory blk_, TaikoData.TransitionState memory ts_)
149     {
150         uint64 slot;
151         (blk_, slot) = LibUtils.getBlock(state, getConfig(), _blockId);
152 
153         if (blk_.verifiedTransitionId != 0) {
154             ts_ = state.transitions[slot][blk_.verifiedTransitionId];
155         }
156     }

176     function getStateVariables() 
177         public
178         view
179         returns (TaikoData.SlotA memory a_, TaikoData.SlotB memory b_)
180     {
181         a_ = state.slotA;
182         b_ = state.slotB;
183     }
```
([55](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L55-L72), [145](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L145-L156), [176](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L176-L183))

```solidity
File: contracts/L1/libs/LibDepositing.sol

67     function processDeposits( 
68         TaikoData.State storage _state,
69         TaikoData.Config memory _config,
70         address _feeRecipient
71     )
72         internal
73         returns (TaikoData.EthDeposit[] memory deposits_)
74     {
75         // Calculate the number of pending deposits.
76         uint256 numPending = _state.slotA.numEthDeposits - _state.slotA.nextEthDepositToProcess;
77 
78         if (numPending < _config.ethDepositMinCountPerBlock) {
79             deposits_ = new TaikoData.EthDeposit[](0);
80         } else {
81             deposits_ =
82                 new TaikoData.EthDeposit[](numPending.min(_config.ethDepositMaxCountPerBlock));
83             uint96 fee = uint96(_config.ethDepositMaxFee.min(block.basefee * _config.ethDepositGas));
84             uint64 j = _state.slotA.nextEthDepositToProcess;
85             uint96 totalFee;
86             for (uint256 i; i < deposits_.length;) {
87                 uint256 data = _state.ethDeposits[j % _config.ethDepositRingBufferSize];
88                 deposits_[i] = TaikoData.EthDeposit({
89                     recipient: address(uint160(data >> 96)),
90                     amount: uint96(data),
91                     id: j
92                 });
93                 uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount;
94 
95                 // Unchecked is safe:
96                 // - _fee cannot be bigger than deposits_[i].amount
97                 // - all values are in the same range (uint96) except loop
98                 // counter, which obviously cannot be bigger than uint95
99                 // otherwise the function would be gassing out.
100                 unchecked {
101                     deposits_[i].amount -= _fee;
102                     totalFee += _fee;
103                     ++i;
104                     ++j;
105                 }
106             }
107             _state.slotA.nextEthDepositToProcess = j;
108             // This is the fee deposit
109             _state.ethDeposits[_state.slotA.numEthDeposits % _config.ethDepositRingBufferSize] =
110                 _encodeEthDeposit(_feeRecipient, totalFee);
111 
112             // Unchecked is safe:
113             // - uint64 can store up to ~1.8 * 1e19, which can represent 584K
114             // years if we are depositing at every second
115             unchecked {
116                 _state.slotA.numEthDeposits++;
117             }
118         }
119     }
```
([67](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L67-L119))

```solidity
File: contracts/L1/libs/LibProposing.sol

68     function proposeBlock( 
69         TaikoData.State storage _state,
70         TaikoData.Config memory _config,
71         IAddressResolver _resolver,
72         bytes calldata _data,
73         bytes calldata _txList
74     )
75         internal
76         returns (TaikoData.BlockMetadata memory meta_, TaikoData.EthDeposit[] memory deposits_)
77     {
78         TaikoData.BlockParams memory params = abi.decode(_data, (TaikoData.BlockParams));
79 
80         // We need a prover that will submit proofs after the block has been submitted
81         if (params.assignedProver == address(0)) {
82             revert L1_INVALID_PROVER();
83         }
84 
85         if (params.coinbase == address(0)) {
86             params.coinbase = msg.sender;
87         }
88 
89         // Taiko, as a Based Rollup, enables permissionless block proposals.
90         // However, if the "proposer" address is set to a non-zero value, we
91         // ensure that only that specific address has the authority to propose
92         // blocks.
93         TaikoData.SlotB memory b = _state.slotB;
94         if (!_isProposerPermitted(b, _resolver)) revert L1_UNAUTHORIZED();
95 
96         // It's essential to ensure that the ring buffer for proposed blocks
97         // still has space for at least one more block.
98         if (b.numBlocks >= b.lastVerifiedBlockId + _config.blockMaxProposals + 1) {
99             revert L1_TOO_MANY_BLOCKS();
100         }
101 
102         bytes32 parentMetaHash =
103             _state.blocks[(b.numBlocks - 1) % _config.blockRingBufferSize].metaHash;
104 
105         // Check if parent block has the right meta hash
106         // This is to allow the proposer to make sure the block builds on the expected latest chain
107         // state
108         if (params.parentMetaHash != 0 && parentMetaHash != params.parentMetaHash) {
109             revert L1_UNEXPECTED_PARENT();
110         }
111 
112         // Each transaction must handle a specific quantity of L1-to-L2
113         // Ether deposits.
114         deposits_ = LibDepositing.processDeposits(_state, _config, params.coinbase);
115 
116         // Initialize metadata to compute a metaHash, which forms a part of
117         // the block data to be stored on-chain for future integrity checks.
118         // If we choose to persist all data fields in the metadata, it will
119         // require additional storage slots.
120         unchecked {
121             meta_ = TaikoData.BlockMetadata({
122                 l1Hash: blockhash(block.number - 1),
123                 difficulty: 0, // to be initialized below
124                 blobHash: 0, // to be initialized below
125                 extraData: params.extraData,
126                 depositsHash: keccak256(abi.encode(deposits_)),
127                 coinbase: params.coinbase,
128                 id: b.numBlocks,
129                 gasLimit: _config.blockMaxGasLimit,
130                 timestamp: uint64(block.timestamp),
131                 l1Height: uint64(block.number - 1),
132                 txListByteOffset: 0, // to be initialized below
133                 txListByteSize: 0, // to be initialized below
134                 minTier: 0, // to be initialized below
135                 blobUsed: _txList.length == 0,
136                 parentMetaHash: parentMetaHash
137             });
138         }
139 
140         // Update certain meta fields
141         if (meta_.blobUsed) {
142             if (!_config.blobAllowedForDA) revert L1_BLOB_FOR_DA_DISABLED();
143 
144             if (params.blobHash != 0) {
145                 if (!_config.blobReuseEnabled) revert L1_BLOB_REUSE_DISABLED();
146 
147                 // We try to reuse an old blob
148                 if (!isBlobReusable(_state, _config, params.blobHash)) {
149                     revert L1_BLOB_NOT_REUSABLE();
150                 }
151                 meta_.blobHash = params.blobHash;
152             } else {
153                 // Always use the first blob in this transaction. If the
154                 // proposeBlock functions are called more than once in the same
155                 // L1 transaction, these multiple L2 blocks will share the same
156                 // blob.
157                 meta_.blobHash = blockhash(0);
158 
159                 if (meta_.blobHash == 0) revert L1_BLOB_NOT_FOUND();
160 
161                 // Depends on the blob data price, it may not make sense to
162                 // cache the blob which costs 20,000 (sstore) + 631 (event)
163                 // extra gas.
164                 if (_config.blobReuseEnabled && params.cacheBlobForReuse) {
165                     _state.reusableBlobs[meta_.blobHash] = block.timestamp;
166                     emit BlobCached(meta_.blobHash);
167                 }
168             }
169 
170             // Check that the txList data range is within the max size of a blob
171             if (uint256(params.txListByteOffset) + params.txListByteSize > MAX_BYTES_PER_BLOB) {
172                 revert L1_TXLIST_OFFSET();
173             }
174 
175             meta_.txListByteOffset = params.txListByteOffset;
176             meta_.txListByteSize = params.txListByteSize;
177         } else {
178             // The proposer must be an Externally Owned Account (EOA) for
179             // calldata usage. This ensures that the transaction is not an
180             // internal one, making calldata retrieval more straightforward for
181             // Taiko node software.
182             if (!LibAddress.isSenderEOA()) revert L1_PROPOSER_NOT_EOA();
183 
184             // The txList is the full byte array without any offset
185             if (params.txListByteOffset != 0) {
186                 revert L1_INVALID_PARAM();
187             }
188 
189             meta_.blobHash = keccak256(_txList);
190             meta_.txListByteOffset = 0;
191             meta_.txListByteSize = uint24(_txList.length);
192         }
193 
194         // Check that the tx length is non-zero and within the supported range
195         if (meta_.txListByteSize == 0 || meta_.txListByteSize > _config.blockMaxTxListBytes) {
196             revert L1_TXLIST_SIZE();
197         }
198 
199         // Following the Merge, the L1 mixHash incorporates the
200         // prevrandao value from the beacon chain. Given the possibility
201         // of multiple Taiko blocks being proposed within a single
202         // Ethereum block, we choose to introduce a salt to this random
203         // number as the L2 mixHash.
204         meta_.difficulty = keccak256(abi.encodePacked(block.prevrandao, b.numBlocks, block.number));
205 
206         // Use the difficulty as a random number
207         meta_.minTier = ITierProvider(_resolver.resolve("tier_provider", false)).getMinTier(
208             uint256(meta_.difficulty)
209         );
210 
211         // Create the block that will be stored onchain
212         TaikoData.Block memory blk = TaikoData.Block({
213             metaHash: keccak256(abi.encode(meta_)),
214             // Safeguard the liveness bond to ensure its preservation,
215             // particularly in scenarios where it might be altered after the
216             // block's proposal but before it has been proven or verified.
217             livenessBond: _config.livenessBond,
218             blockId: b.numBlocks,
219             proposedAt: meta_.timestamp,
220             proposedIn: uint64(block.number),
221             // For a new block, the next transition ID is always 1, not 0.
222             nextTransitionId: 1,
223             // For unverified block, its verifiedTransitionId is always 0.
224             verifiedTransitionId: 0,
225             assignedProver: params.assignedProver
226         });
227 
228         // Store the block in the ring buffer
229         _state.blocks[b.numBlocks % _config.blockRingBufferSize] = blk;
230 
231         // Increment the counter (cursor) by 1.
232         unchecked {
233             ++_state.slotB.numBlocks;
234         }
235 
236         {
237             IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));
238             uint256 tkoBalance = tko.balanceOf(address(this));
239 
240             // Run all hooks.
241             // Note that address(this).balance has been updated with msg.value,
242             // prior to any code in this function has been executed.
243             address prevHook;
244             for (uint256 i; i < params.hookCalls.length; ++i) {
245                 if (uint160(prevHook) >= uint160(params.hookCalls[i].hook)) {
246                     revert L1_INVALID_HOOK();
247                 }
248 
249                 // When a hook is called, all ether in this contract will be send to the hook.
250                 // If the ether sent to the hook is not used entirely, the hook shall send the Ether
251                 // back to this contract for the next hook to use.
252                 // Proposers shall choose use extra hooks wisely.
253                 IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }(
254                     blk, meta_, params.hookCalls[i].data
255                 );
256 
257                 prevHook = params.hookCalls[i].hook;
258             }
259             // Refund Ether
260             if (address(this).balance != 0) {
261                 msg.sender.sendEther(address(this).balance);
262             }
263 
264             // Check that after hooks, the Taiko Token balance of this contract
265             // have increased by the same amount as _config.livenessBond (to prevent)
266             // multiple draining payments by a malicious proposer nesting the same
267             // hook.
268             if (tko.balanceOf(address(this)) != tkoBalance + _config.livenessBond) {
269                 revert L1_LIVENESS_BOND_NOT_RECEIVED();
270             }
271         }
272 
273         emit BlockProposed({
274             blockId: blk.blockId,
275             assignedProver: blk.assignedProver,
276             livenessBond: _config.livenessBond,
277             meta: meta_,
278             depositsProcessed: deposits_
279         });
280     }
```
([68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L68-L280))

```solidity
File: contracts/L1/libs/LibProving.sol

91     function proveBlock( 
92         TaikoData.State storage _state,
93         TaikoData.Config memory _config,
94         IAddressResolver _resolver,
95         TaikoData.BlockMetadata memory _meta,
96         TaikoData.Transition memory _tran,
97         TaikoData.TierProof memory _proof
98     )
99         internal
100         returns (uint8 maxBlocksToVerify_)
101     {
102         // Make sure parentHash is not zero
103         // To contest an existing transition, simply use any non-zero value as
104         // the blockHash and stateRoot.
105         if (_tran.parentHash == 0 || _tran.blockHash == 0 || _tran.stateRoot == 0) {
106             revert L1_INVALID_TRANSITION();
107         }
108 
109         // Check that the block has been proposed but has not yet been verified.
110         TaikoData.SlotB memory b = _state.slotB;
111         if (_meta.id <= b.lastVerifiedBlockId || _meta.id >= b.numBlocks) {
112             revert L1_INVALID_BLOCK_ID();
113         }
114 
115         uint64 slot = _meta.id % _config.blockRingBufferSize;
116         TaikoData.Block storage blk = _state.blocks[slot];
117 
118         // Check the integrity of the block data. It's worth noting that in
119         // theory, this check may be skipped, but it's included for added
120         // caution.
121         if (blk.blockId != _meta.id || blk.metaHash != keccak256(abi.encode(_meta))) {
122             revert L1_BLOCK_MISMATCH();
123         }
124 
125         // Each transition is uniquely identified by the parentHash, with the
126         // blockHash and stateRoot open for later updates as higher-tier proofs
127         // become available. In cases where a transition with the specified
128         // parentHash does not exist, the transition ID (tid) will be set to 0.
129         (uint32 tid, TaikoData.TransitionState storage ts) =
130             _createTransition(_state, blk, _tran, slot);
131 
132         // The new proof must meet or exceed the minimum tier required by the
133         // block or the previous proof; it cannot be on a lower tier.
134         if (_proof.tier == 0 || _proof.tier < _meta.minTier || _proof.tier < ts.tier) {
135             revert L1_INVALID_TIER();
136         }
137 
138         // Retrieve the tier configurations. If the tier is not supported, the
139         // subsequent action will result in a revert.
140         ITierProvider.Tier memory tier =
141             ITierProvider(_resolver.resolve("tier_provider", false)).getTier(_proof.tier);
142 
143         // Check if this prover is allowed to submit a proof for this block
144         _checkProverPermission(_state, blk, ts, tid, tier);
145 
146         // We must verify the proof, and any failure in proof verification will
147         // result in a revert.
148         //
149         // It's crucial to emphasize that the proof can be assessed in two
150         // potential modes: "proving mode" and "contesting mode." However, the
151         // precise verification logic is defined within each tier's IVerifier
152         // contract implementation. We simply specify to the verifier contract
153         // which mode it should utilize - if the new tier is higher than the
154         // previous tier, we employ the proving mode; otherwise, we employ the
155         // contesting mode (the new tier cannot be lower than the previous tier,
156         // this has been checked above).
157         //
158         // It's obvious that proof verification is entirely decoupled from
159         // Taiko's core protocol.
160         {
161             address verifier = _resolver.resolve(tier.verifierName, true);
162 
163             if (verifier != address(0)) {
164                 bool isContesting = _proof.tier == ts.tier && tier.contestBond != 0;
165 
166                 IVerifier.Context memory ctx = IVerifier.Context({
167                     metaHash: blk.metaHash,
168                     blobHash: _meta.blobHash,
169                     // Separate msgSender to allow the prover to be any address in the future.
170                     prover: msg.sender,
171                     msgSender: msg.sender,
172                     blockId: blk.blockId,
173                     isContesting: isContesting,
174                     blobUsed: _meta.blobUsed
175                 });
176 
177                 IVerifier(verifier).verifyProof(ctx, _tran, _proof);
178             } else if (tier.verifierName != TIER_OP) {
179                 // The verifier can be address-zero, signifying that there are no
180                 // proof checks for the tier. In practice, this only applies to
181                 // optimistic proofs.
182                 revert L1_MISSING_VERIFIER();
183             }
184         }
185 
186         bool isTopTier = tier.contestBond == 0;
187         IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));
188 
189         if (isTopTier) {
190             // A special return value from the top tier prover can signal this
191             // contract to return all liveness bond.
192             bool returnLivenessBond = blk.livenessBond > 0 && _proof.data.length == 32
193                 && bytes32(_proof.data) == RETURN_LIVENESS_BOND;
194 
195             if (returnLivenessBond) {
196                 tko.transfer(blk.assignedProver, blk.livenessBond);
197                 blk.livenessBond = 0;
198             }
199         }
200 
201         bool sameTransition = _tran.blockHash == ts.blockHash && _tran.stateRoot == ts.stateRoot;
202 
203         if (_proof.tier > ts.tier) {
204             // Handles the case when an incoming tier is higher than the current transition's tier.
205             // Reverts when the incoming proof tries to prove the same transition
206             // (L1_ALREADY_PROVED).
207             _overrideWithHigherProof(ts, _tran, _proof, tier, tko, sameTransition);
208 
209             emit TransitionProved({
210                 blockId: blk.blockId,
211                 tran: _tran,
212                 prover: msg.sender,
213                 validityBond: tier.validityBond,
214                 tier: _proof.tier
215             });
216         } else {
217             // New transition and old transition on the same tier - and if this transaction tries to
218             // prove the same, it reverts
219             if (sameTransition) revert L1_ALREADY_PROVED();
220 
221             if (isTopTier) {
222                 // The top tier prover re-proves.
223                 assert(tier.validityBond == 0);
224                 assert(ts.validityBond == 0 && ts.contestBond == 0 && ts.contester == address(0));
225 
226                 ts.prover = msg.sender;
227                 ts.blockHash = _tran.blockHash;
228                 ts.stateRoot = _tran.stateRoot;
229 
230                 emit TransitionProved({
231                     blockId: blk.blockId,
232                     tran: _tran,
233                     prover: msg.sender,
234                     validityBond: 0,
235                     tier: _proof.tier
236                 });
237             } else {
238                 // Contesting but not on the highest tier
239                 if (ts.contester != address(0)) revert L1_ALREADY_CONTESTED();
240 
241                 // Burn the contest bond from the prover.
242                 tko.transferFrom(msg.sender, address(this), tier.contestBond);
243 
244                 // We retain the contest bond within the transition, just in
245                 // case this configuration is altered to a different value
246                 // before the contest is resolved.
247                 //
248                 // It's worth noting that the previous value of ts.contestBond
249                 // doesn't have any significance.
250                 ts.contestBond = tier.contestBond;
251                 ts.contester = msg.sender;
252                 ts.contestations += 1;
253 
254                 emit TransitionContested({
255                     blockId: blk.blockId,
256                     tran: _tran,
257                     contester: msg.sender,
258                     contestBond: tier.contestBond,
259                     tier: _proof.tier
260                 });
261             }
262         }
263 
264         ts.timestamp = uint64(block.timestamp);
265         return tier.maxBlocksToVerifyPerProof;
266     }

269     function _createTransition( 
270         TaikoData.State storage _state,
271         TaikoData.Block storage _blk,
272         TaikoData.Transition memory _tran,
273         uint64 slot
274     )
275         private
276         returns (uint32 tid_, TaikoData.TransitionState storage ts_)
277     {
278         tid_ = LibUtils.getTransitionId(_state, _blk, slot, _tran.parentHash);
279 
280         if (tid_ == 0) {
281             // In cases where a transition with the provided parentHash is not
282             // found, we must essentially "create" one and set it to its initial
283             // state. This initial state can be viewed as a special transition
284             // on tier-0.
285             //
286             // Subsequently, we transform this tier-0 transition into a
287             // non-zero-tier transition with a proof. This approach ensures that
288             // the same logic is applicable for both 0-to-non-zero transition
289             // updates and non-zero-to-non-zero transition updates.
290             unchecked {
291                 // Unchecked is safe:  Not realistic 2**32 different fork choice
292                 // per block will be proven and none of them is valid
293                 tid_ = _blk.nextTransitionId++;
294             }
295 
296             // Keep in mind that state.transitions are also reusable storage
297             // slots, so it's necessary to reinitialize all transition fields
298             // below.
299             ts_ = _state.transitions[slot][tid_];
300             ts_.blockHash = 0;
301             ts_.stateRoot = 0;
302             ts_.validityBond = 0;
303             ts_.contester = address(0);
304             ts_.contestBond = 1; // to save gas
305             ts_.timestamp = _blk.proposedAt;
306             ts_.tier = 0;
307             ts_.contestations = 0;
308 
309             if (tid_ == 1) {
310                 // This approach serves as a cost-saving technique for the
311                 // majority of blocks, where the first transition is expected to
312                 // be the correct one. Writing to `tran` is more economical
313                 // since it resides in the ring buffer, whereas writing to
314                 // `transitionIds` is not as cost-effective.
315                 ts_.key = _tran.parentHash;
316 
317                 // In the case of this first transition, the block's assigned
318                 // prover has the privilege to re-prove it, but only when the
319                 // assigned prover matches the previous prover. To ensure this,
320                 // we establish the transition's prover as the block's assigned
321                 // prover. Consequently, when we carry out a 0-to-non-zero
322                 // transition update, the previous prover will consistently be
323                 // the block's assigned prover.
324                 //
325                 // While alternative implementations are possible, introducing
326                 // such changes would require additional if-else logic.
327                 ts_.prover = _blk.assignedProver;
328             } else {
329                 // In scenarios where this transition is not the first one, we
330                 // straightforwardly reset the transition prover to address
331                 // zero.
332                 ts_.prover = address(0);
333 
334                 // Furthermore, we index the transition for future retrieval.
335                 // It's worth emphasizing that this mapping for indexing is not
336                 // reusable. However, given that the majority of blocks will
337                 // only possess one transition — the correct one — we don't need
338                 // to be concerned about the cost in this case.
339                 _state.transitionIds[_blk.blockId][_tran.parentHash] = tid_;
340 
341                 // There is no need to initialize ts.key here because it's only used when tid == 1
342             }
343         } else {
344             // A transition with the provided parentHash has been located.
345             ts_ = _state.transitions[slot][tid_];
346         }
347     }
```
([91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L91-L266), [269](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L269-L347))

```solidity
File: contracts/L1/libs/LibUtils.sol

52     function getBlock( 
53         TaikoData.State storage _state,
54         TaikoData.Config memory _config,
55         uint64 _blockId
56     )
57         external
58         view
59         returns (TaikoData.Block storage blk_, uint64 slot_)
60     {
61         slot_ = _blockId % _config.blockRingBufferSize;
62         blk_ = _state.blocks[slot_];
63         if (blk_.blockId != _blockId) {
64             revert L1_INVALID_BLOCK_ID();
65         }
66     }

70     function getTransitionId( 
71         TaikoData.State storage _state,
72         TaikoData.Block storage _blk,
73         uint64 _slot,
74         bytes32 _parentHash
75     )
76         internal
77         view
78         returns (uint32 tid_)
79     {
80         if (_state.transitions[_slot][1].key == _parentHash) {
81             tid_ = 1;
82         } else {
83             tid_ = _state.transitionIds[_blk.blockId][_parentHash];
84         }
85 
86         if (tid_ >= _blk.nextTransitionId) revert L1_UNEXPECTED_TRANSITION_ID();
87     }
```
([52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L52-L66), [70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L70-L87))

```solidity
File: contracts/L1/provers/GuardianProver.sol

35     function approve( 
36         TaikoData.BlockMetadata calldata _meta,
37         TaikoData.Transition calldata _tran,
38         TaikoData.TierProof calldata _proof
39     )
40         external
41         whenNotPaused
42         nonReentrant
43         returns (bool approved_)
44     {
45         if (_proof.tier != LibTiers.TIER_GUARDIAN) revert INVALID_PROOF();
46         bytes32 hash = keccak256(abi.encode(_meta, _tran));
47         approved_ = approve(_meta.id, hash);
48 
49         if (approved_) {
50             deleteApproval(hash);
51             ITaikoL1(resolve("taiko", false)).proveBlock(_meta.id, abi.encode(_meta, _tran, _proof));
52         }
53 
54         emit GuardianApproval(msg.sender, _meta.id, _tran.blockHash, approved_);
55     }
```
([35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L35-L55))

```solidity
File: contracts/L1/provers/Guardians.sol

111     function approve(uint256 _operationId, bytes32 _hash) internal returns (bool approved_) { 
112         uint256 id = guardianIds[msg.sender];
113         if (id == 0) revert INVALID_GUARDIAN();
114 
115         unchecked {
116             _approvals[version][_hash] |= 1 << (id - 1);
117         }
118 
119         uint256 _approval = _approvals[version][_hash];
120         approved_ = isApproved(_approval);
121         emit Approved(_operationId, _approval, approved_);
122     }
```
([111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L111-L122))

```solidity
File: contracts/L1/tiers/DevnetTierProvider.sol

47     function getTierIds() public pure override returns (uint16[] memory tiers_) { 
48         tiers_ = new uint16[](2);
49         tiers_[0] = LibTiers.TIER_OPTIMISTIC;
50         tiers_[1] = LibTiers.TIER_GUARDIAN;
51     }
```
([47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L47-L51))

```solidity
File: contracts/L1/tiers/MainnetTierProvider.sol

58     function getTierIds() public pure override returns (uint16[] memory tiers_) { 
59         tiers_ = new uint16[](3);
60         tiers_[0] = LibTiers.TIER_SGX;
61         tiers_[1] = LibTiers.TIER_SGX_ZKVM;
62         tiers_[2] = LibTiers.TIER_GUARDIAN;
63     }
```
([58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L58-L63))

```solidity
File: contracts/L1/tiers/TestnetTierProvider.sol

58     function getTierIds() public pure override returns (uint16[] memory tiers_) { 
59         tiers_ = new uint16[](3);
60         tiers_[0] = LibTiers.TIER_OPTIMISTIC;
61         tiers_[1] = LibTiers.TIER_SGX;
62         tiers_[2] = LibTiers.TIER_GUARDIAN;
63     }
```
([58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L58-L63))

```solidity
File: contracts/L2/TaikoL2.sol

185     function getBasefee( 
186         uint64 _l1BlockId,
187         uint32 _parentGasUsed
188     )
189         public
190         view
191         returns (uint256 basefee_)
192     {
193         (basefee_,) = _calc1559BaseFee(getConfig(), _l1BlockId, _parentGasUsed);
194     }

208     function getConfig() public view virtual returns (Config memory config_) { 
209         // 4x Ethereum gas target, if we assume most of the time, L2 block time
210         // is 3s, and each block is full (gasUsed is 15_000_000), then its
211         // ~60_000_000, if the  network is congester than that, the base fee
212         // will increase.
213         config_.gasTargetPerL1Block = 15 * 1e6 * 4;
214         config_.basefeeAdjustmentQuotient = 8;
215     }

223     function _calcPublicInputHash(uint256 _blockId) 
224         private
225         view
226         returns (bytes32 publicInputHashOld, bytes32 publicInputHashNew)
227     {
228         bytes32[256] memory inputs;
229 
230         // Unchecked is safe because it cannot overflow.
231         unchecked {
232             // Put the previous 255 blockhashes (excluding the parent's) into a
233             // ring buffer.
234             for (uint256 i; i < 255 && _blockId >= i + 1; ++i) {
235                 uint256 j = _blockId - i - 1;
236                 inputs[j % 255] = blockhash(j);
237             }
238         }
239 
240         inputs[255] = bytes32(block.chainid);
241 
242         assembly {
243             publicInputHashOld := keccak256(inputs, 8192 /*mul(256, 32)*/ )
244         }
245 
246         inputs[_blockId % 255] = blockhash(_blockId);
247         assembly {
248             publicInputHashNew := keccak256(inputs, 8192 /*mul(256, 32)*/ )
249         }
250     }

252     function _calc1559BaseFee( 
253         Config memory _config,
254         uint64 _l1BlockId,
255         uint32 _parentGasUsed
256     )
257         private
258         view
259         returns (uint256 basefee_, uint64 gasExcess_)
260     {
261         // gasExcess being 0 indicate the dynamic 1559 base fee is disabled.
262         if (gasExcess > 0) {
263             // We always add the gas used by parent block to the gas excess
264             // value as this has already happened
265             uint256 excess = uint256(gasExcess) + _parentGasUsed;
266 
267             // Calculate how much more gas to issue to offset gas excess.
268             // after each L1 block time, config.gasTarget more gas is issued,
269             // the gas excess will be reduced accordingly.
270             // Note that when lastSyncedBlock is zero, we skip this step
271             // because that means this is the first time calculating the basefee
272             // and the difference between the L1 height would be extremely big,
273             // reverting the initial gas excess value back to 0.
274             uint256 numL1Blocks;
275             if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {
276                 numL1Blocks = _l1BlockId - lastSyncedBlock;
277             }
278 
279             if (numL1Blocks > 0) {
280                 uint256 issuance = numL1Blocks * _config.gasTargetPerL1Block;
281                 excess = excess > issuance ? excess - issuance : 1;
282             }
283 
284             gasExcess_ = uint64(excess.min(type(uint64).max));
285 
286             // The base fee per gas used by this block is the spot price at the
287             // bonding curve, regardless the actual amount of gas used by this
288             // block, however, this block's gas used will affect the next
289             // block's base fee.
290             basefee_ = Lib1559Math.basefee(
291                 gasExcess_, uint256(_config.basefeeAdjustmentQuotient) * _config.gasTargetPerL1Block
292             );
293         }
294 
295         // Always make sure basefee is nonzero, this is required by the node.
296         if (basefee_ == 0) basefee_ = 1;
297     }
```
([185](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L185-L194), [208](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L208-L215), [223](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L223-L250), [252](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L252-L297))

```solidity
File: contracts/common/AddressResolver.sol

72     function _resolve( 
73         uint64 _chainId,
74         bytes32 _name,
75         bool _allowZeroAddress
76     )
77         private
78         view
79         returns (address payable addr_)
80     {
81         if (addressManager == address(0)) revert RESOLVER_INVALID_MANAGER();
82 
83         addr_ = payable(IAddressManager(addressManager).getAddress(_chainId, _name));
84 
85         if (!_allowZeroAddress && addr_ == address(0)) {
86             revert RESOLVER_ZERO_ADDR(_chainId, _name);
87         }
88     }
```
([72](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L72-L88))

```solidity
File: contracts/common/EssentialContract.sol

130     function _loadReentryLock() internal view virtual returns (uint8 reentry_) { 
131         if (block.chainid == 1) {
132             assembly {
133                 reentry_ := tload(_REENTRY_SLOT)
134             }
135         } else {
136             reentry_ = __reentry;
137         }
138     }
```
([130](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L130-L138))

```solidity
File: contracts/libs/LibAddress.sol

46     function supportsInterface( 
47         address _addr,
48         bytes4 _interfaceId
49     )
50         internal
51         view
52         returns (bool result_)
53     {
54         if (!Address.isContract(_addr)) return false;
55 
56         try IERC165(_addr).supportsInterface(_interfaceId) returns (bool _result) {
57             result_ = _result;
58         } catch { }
59     }
```
([46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L46-L59))

```solidity
File: contracts/libs/LibTrieProof.sol

34     function verifyMerkleProof( 
35         bytes32 _rootHash,
36         address _addr,
37         bytes32 _slot,
38         bytes32 _value,
39         bytes[] memory _accountProof,
40         bytes[] memory _storageProof
41     )
42         internal
43         pure
44         returns (bytes32 storageRoot_)
45     {
46         if (_accountProof.length != 0) {
47             bytes memory rlpAccount =
48                 SecureMerkleTrie.get(abi.encodePacked(_addr), _accountProof, _rootHash);
49 
50             if (rlpAccount.length == 0) revert LTP_INVALID_ACCOUNT_PROOF();
51 
52             RLPReader.RLPItem[] memory accountState = RLPReader.readList(rlpAccount);
53 
54             storageRoot_ =
55                 bytes32(RLPReader.readBytes(accountState[_ACCOUNT_FIELD_INDEX_STORAGE_HASH]));
56         } else {
57             storageRoot_ = _rootHash;
58         }
59 
60         bool verified = SecureMerkleTrie.verifyInclusionProof(
61             bytes.concat(_slot), RLPWriter.writeUint(uint256(_value)), _storageProof, storageRoot_
62         );
63 
64         if (!verified) revert LTP_INVALID_INCLUSION_PROOF();
65     }
```
([34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L34-L65))

```solidity
File: contracts/signal/ISignalService.sol

59     function sendSignal(bytes32 _signal) external returns (bytes32 slot_); 

68     function syncChainData( 
69         uint64 _chainId,
70         bytes32 _kind,
71         uint64 _blockId,
72         bytes32 _chainData
73     )
74         external
75         returns (bytes32 signal_);

122     function getSyncedChainData( 
123         uint64 _chainId,
124         bytes32 _kind,
125         uint64 _blockId
126     )
127         external
128         view
129         returns (uint64 blockId_, bytes32 chainData_);

137     function signalForChainData( 
138         uint64 _chainId,
139         bytes32 _kind,
140         uint64 _blockId
141     )
142         external
143         pure
144         returns (bytes32 signal_);
```
([59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L59), [68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L68-L75), [122](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L122-L129), [137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L137-L144))

```solidity
File: contracts/signal/SignalService.sol

158     function getSyncedChainData( 
159         uint64 _chainId,
160         bytes32 _kind,
161         uint64 _blockId
162     )
163         public
164         view
165         returns (uint64 blockId_, bytes32 chainData_)
166     {
167         blockId_ = _blockId != 0 ? _blockId : topBlockId[_chainId][_kind];
168 
169         if (blockId_ != 0) {
170             bytes32 signal = signalForChainData(_chainId, _kind, blockId_);
171             chainData_ = _loadSignalValue(address(this), signal);
172             if (chainData_ == 0) revert SS_SIGNAL_NOT_FOUND();
173         }
174     }

235     function _syncChainData( 
236         uint64 _chainId,
237         bytes32 _kind,
238         uint64 _blockId,
239         bytes32 _chainData
240     )
241         private
242         returns (bytes32 signal_)
243     {
244         signal_ = signalForChainData(_chainId, _kind, _blockId);
245         _sendSignal(address(this), signal_, _chainData);
246 
247         if (topBlockId[_chainId][_kind] < _blockId) {
248             topBlockId[_chainId][_kind] = _blockId;
249         }
250         emit ChainDataSynced(_chainId, _blockId, _kind, _chainData, signal_);
251     }
```
([158](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L158-L174), [235](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L235-L251))

</details>

### [GAS&#x2011;047] Optimize Deployment Size by Fine-tuning IPFS Hash
The Solidity compiler appends 53 bytes of metadata to the smart contract code, incurring an extra cost of 10,600 gas. This additional expense arises from 200 gas per bytecode, plus calldata cost, which amounts to 16 gas for non-zero bytes and 4 gas for zero bytes. This results in a maximum of 848 extra gas in calldata cost.

Reducing this cost is crucial for the following reasons:

The metadata's 53-byte addition leads to a deployment cost increase of 10,600 gas.
It can also result in an additional calldata cost of up to 848 gas.
Ways to Minimize Gas Consumption:

Employ the `--no-cbor-metadata` compiler option to exclude metadata. Be cautious as this might impact contract verification.
Search for code comments that yield an IPFS hash with more zeros, thereby reducing calldata costs.

<details>
<summary><i>There are 40 instances (click to view)</i></summary>

```solidity
File: contracts/L1/ITaikoL1.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/ITaikoL1.sol#L1))

```solidity
File: contracts/L1/TaikoData.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L1))

```solidity
File: contracts/L1/TaikoErrors.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoErrors.sol#L1))

```solidity
File: contracts/L1/TaikoEvents.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L1))

```solidity
File: contracts/L1/TaikoL1.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L1))

```solidity
File: contracts/L1/TaikoToken.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L1))

```solidity
File: contracts/L1/gov/TaikoGovernor.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L1))

```solidity
File: contracts/L1/gov/TaikoTimelockController.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L1))

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L1))

```solidity
File: contracts/L1/hooks/IHook.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/IHook.sol#L1))

```solidity
File: contracts/L1/libs/LibDepositing.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L1))

```solidity
File: contracts/L1/libs/LibProposing.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L1))

```solidity
File: contracts/L1/libs/LibProving.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L1))

```solidity
File: contracts/L1/libs/LibUtils.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L1))

```solidity
File: contracts/L1/libs/LibVerifying.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L1))

```solidity
File: contracts/L1/provers/GuardianProver.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L1))

```solidity
File: contracts/L1/provers/Guardians.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L1))

```solidity
File: contracts/L1/tiers/DevnetTierProvider.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L1))

```solidity
File: contracts/L1/tiers/ITierProvider.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L1))

```solidity
File: contracts/L1/tiers/MainnetTierProvider.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L1))

```solidity
File: contracts/L1/tiers/TestnetTierProvider.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L1))

```solidity
File: contracts/L2/CrossChainOwned.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L1))

```solidity
File: contracts/L2/Lib1559Math.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L1))

```solidity
File: contracts/L2/TaikoL2.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L1))

```solidity
File: contracts/L2/TaikoL2EIP1559Configurable.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L1))

```solidity
File: contracts/bridge/Bridge.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L1))

```solidity
File: contracts/bridge/IBridge.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L1))

```solidity
File: contracts/common/AddressManager.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L1))

```solidity
File: contracts/common/AddressResolver.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L1))

```solidity
File: contracts/common/EssentialContract.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L1))

```solidity
File: contracts/common/IAddressManager.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressManager.sol#L1))

```solidity
File: contracts/common/IAddressResolver.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressResolver.sol#L1))

```solidity
File: contracts/libs/Lib4844.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L1))

```solidity
File: contracts/libs/LibAddress.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L1))

```solidity
File: contracts/libs/LibMath.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibMath.sol#L1))

```solidity
File: contracts/libs/LibTrieProof.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L1))

```solidity
File: contracts/signal/ISignalService.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L1))

```solidity
File: contracts/signal/LibSignals.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/LibSignals.sol#L1))

```solidity
File: contracts/signal/SignalService.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L1))

```solidity
File: contracts/tokenvault/adapters/USDCAdapter.sol

1 // SPDX-License-Identifier: MIT 
```
([1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L1))

</details>

### [GAS&#x2011;048] Pre-increments/pre-decrements are cheaper than `+1`/`-1`
<details>
<summary><i>There are 17 instances (click to view)</i></summary>

```solidity
File: contracts/L2/TaikoL2.sol

// @audit ++i
234             for (uint256 i; i < 255 && _blockId >= i + 1; ++i) { 
```
([234](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L234))

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

// @audit --n
261             if (i == n - 1) { 

// @audit ++i
265                 issuer = certs[i + 1]; 
```
([261](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L261), [265](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L265))

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol

// @audit ++SGX_TCB_CPUSVN_SIZE
354         for (uint256 i; i < SGX_TCB_CPUSVN_SIZE + 1; ++i) { 
```
([354](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L354))

```solidity
File: contracts/automata-attestation/utils/Asn1Decode.sol

// @audit --valueLength
159             return der.substring(ptr.ixf() + 1, valueLength - 1); 

// @audit --valueLength
184         return der.substring(ptr.ixf() + 1, valueLength - 1); 

// @audit ++ix
192             length = uint8(der[ix + 1]); 

// @audit ++ix
196             uint8 lengthbytesLength = uint8(der[ix + 1] & 0x7F); 
```
([159](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L159), [184](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L184), [192](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L192), [196](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L196))

```solidity
File: contracts/automata-attestation/utils/BytesUtils.sol

// @audit --len
338             if (i == len - 1) { 

// @audit --bitlen
359             bitlen -= 1; 
```
([338](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L338), [359](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L359))

```solidity
File: contracts/automata-attestation/utils/X509DateUtils.sol

// @audit ++offset
24         yrs += (uint8(x509Time[offset + 0]) - 48) * 10 + uint8(x509Time[offset + 1]) - 48; 

// @audit --i
60             timestamp += uint256(monthDays[i - 1]) * 86_400; // Days in seconds 

// @audit --day
63         timestamp += uint256(day - 1) * 86_400; // Days in seconds 
```
([24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L24), [60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L60), [63](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L63))

```solidity
File: contracts/thirdparty/optimism/rlp/RLPReader.sol

// @audit ++itemCount
89             itemCount += 1; 
```
([89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L89))

```solidity
File: contracts/thirdparty/optimism/rlp/RLPWriter.sol

// @audit ++lenLen
44             out_ = new bytes(lenLen + 1); 
```
([44](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L44))

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

// @audit ++TREE_RADIX
24     uint256 internal constant BRANCH_NODE_LENGTH = TREE_RADIX + 1; 

// @audit ++currentKeyIndex
137                     currentKeyIndex += 1; 
```
([24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L24), [137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L137))

</details>

### [GAS&#x2011;049] Using `storage` instead of `memory` for state variables saves gas
When fetching data from a storage location, assigning the data to a `memory` variable causes all fields of the struct/array to be read from storage, which incurs a Gcoldsload (**2100 gas**) for *each* field of the struct/array. If the fields are read from the new memory variable, they incur an additional `MLOAD` rather than a cheap stack read. Instead of declaring the variable with the `memory` keyword, declaring the variable with the `storage` keyword and caching any fields that need to be re-read in stack variables, will be much cheaper, only incurring the Gcoldsload for the fields actually read. The only time it makes sense to read the whole struct/array into a `memory` variable, is if the full struct/array is being returned by the function, is being passed to a function that requires `memory`, or if the array/struct is being read from another `memory` array/struct

<details>
<summary><i>There are 6 instances (click to view)</i></summary>

```solidity
File: contracts/L1/libs/LibProposing.sol

93         TaikoData.SlotB memory b = _state.slotB; 
```
([93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L93))

```solidity
File: contracts/L1/libs/LibProving.sol

110         TaikoData.SlotB memory b = _state.slotB; 
```
([110](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L110))

```solidity
File: contracts/L1/libs/LibUtils.sol

33         TaikoData.SlotB memory b = _state.slotB; 
```
([33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L33))

```solidity
File: contracts/L1/libs/LibVerifying.sol

99         TaikoData.SlotB memory b = _state.slotB; 
```
([99](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L99))

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

180         EnclaveIdStruct.EnclaveId memory enclaveId = qeIdentity; 
```
([180](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L180))

```solidity
File: contracts/tokenvault/ERC20Vault.sol

171             CanonicalERC20 memory ctoken = bridgedToCanonical[btokenOld_]; 
```
([171](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L171))

</details>

### [GAS&#x2011;050] `private` functions used once can be inlined
<details>
<summary><i>There are 40 instances (click to view)</i></summary>

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

164     function _getProverFee( 
165         TaikoData.TierFee[] memory _tierFees,
166         uint16 _tierId
167     )
168         private
169         pure
170         returns (uint256)
171     {
```
([164](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L164-L171))

```solidity
File: contracts/L1/libs/LibProposing.sol

299     function _isProposerPermitted( 
300         TaikoData.SlotB memory _slotB,
301         IAddressResolver _resolver
302     )
303         private
304         view
305         returns (bool)
306     {
```
([299](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L299-L306))

```solidity
File: contracts/L1/libs/LibProving.sol

269     function _createTransition( 
270         TaikoData.State storage _state,
271         TaikoData.Block storage _blk,
272         TaikoData.Transition memory _tran,
273         uint64 slot
274     )
275         private
276         returns (uint32 tid_, TaikoData.TransitionState storage ts_)
277     {

350     function _overrideWithHigherProof( 
351         TaikoData.TransitionState storage _ts,
352         TaikoData.Transition memory _tran,
353         TaikoData.TierProof memory _proof,
354         ITierProvider.Tier memory _tier,
355         IERC20 _tko,
356         bool _sameTransition
357     )
358         private
359     {

401     function _checkProverPermission( 
402         TaikoData.State storage _state,
403         TaikoData.Block storage _blk,
404         TaikoData.TransitionState storage _ts,
405         uint32 _tid,
406         ITierProvider.Tier memory _tier
407     )
408         private
409         view
410     {
```
([269](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L269-L277), [350](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L350-L359), [401](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L401-L410))

```solidity
File: contracts/L1/libs/LibVerifying.sol

224     function _syncChainData( 
225         TaikoData.Config memory _config,
226         IAddressResolver _resolver,
227         uint64 _lastVerifiedBlockId,
228         bytes32 _stateRoot
229     )
230         private
231     {

245     function _isConfigValid(TaikoData.Config memory _config) private view returns (bool) { 
```
([224](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L224-L231), [245](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L245))

```solidity
File: contracts/L2/Lib1559Math.sol

33     function _ethQty( 
34         uint256 _gasExcess,
35         uint256 _adjustmentFactor
36     )
37         private
38         pure
39         returns (uint256)
40     {
```
([33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L33-L40))

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

162     function _verify(bytes calldata quote) private view returns (bool, bytes memory) { 

175     function _verifyQEReportWithIdentity(V3Struct.EnclaveReport memory quoteEnclaveReport) 
176         private
177         view
178         returns (bool, EnclaveIdStruct.EnclaveIdStatus status)
179     {
```
([162](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L162), [175](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L175-L179))

```solidity
File: contracts/bridge/Bridge.sol

555     function _loadContext() private view returns (Context memory) { 
```
([555](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L555))

```solidity
File: contracts/signal/SignalService.sol

271     function _cacheChainData( 
272         HopProof memory _hop,
273         uint64 _chainId,
274         uint64 _blockId,
275         bytes32 _signalRoot,
276         bool _isFullProof,
277         bool _isLastHop
278     )
279         private
280     {
```
([271](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L271-L280))

```solidity
File: contracts/team/TimelockTokenPool.sol

225     function _voidGrant(Grant storage _grant) private returns (uint128 amountVoided) { 

239     function _getAmountUnlocked(Grant memory _grant) private view returns (uint128) { 

267     function _validateGrant(Grant memory _grant) private pure { 
```
([225](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L225), [239](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L239), [267](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L267))

```solidity
File: contracts/thirdparty/optimism/rlp/RLPWriter.sol

32     function _writeLength(uint256 _len, uint256 _offset) private pure returns (bytes memory out_) { 

55     function _toBinary(uint256 _x) private pure returns (bytes memory out_) { 
```
([32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L32), [55](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L55))

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

205     function _parseProof(bytes[] memory _proof) private pure returns (TrieNode[] memory proof_) { 

227     function _getNodePath(TrieNode memory _node) private pure returns (bytes memory nibbles_) { 

235     function _getSharedNibbleLength( 
236         bytes memory _a,
237         bytes memory _b
238     )
239         private
240         pure
241         returns (uint256 shared_)
242     {
```
([205](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L205), [227](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L227), [235](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L235-L242))

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

240     function _handleMessage( 
241         address _user,
242         BridgeTransferOp memory _op
243     )
244         private
245         returns (bytes memory msgData_, CanonicalNFT memory ctoken_)
246     {

288     function _getOrDeployBridgedToken(CanonicalNFT memory _ctoken) 
289         private
290         returns (address btoken_)
291     {

303     function _deployBridgedToken(CanonicalNFT memory _ctoken) private returns (address btoken_) { 
```
([240](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L240-L246), [288](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L288-L291), [303](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L303))

```solidity
File: contracts/tokenvault/ERC20Vault.sol

221         IBridge.Message memory message = IBridge.Message({ 
222             id: 0, // will receive a new value
223             from: address(0), // will receive a new value
224             srcChainId: 0, // will receive a new value
225             destChainId: _op.destChainId,

276             to: to, 
277             srcChainId: ctx.srcChainId,
278             ctoken: ctoken.addr,
279             token: token,

298         (bytes memory data) = abi.decode(_message.data[4:], (bytes)); 
299         (CanonicalERC20 memory ctoken,,, uint256 amount) =
300             abi.decode(data, (CanonicalERC20, address, address, uint256));

348     function _handleMessage( 
349         address _user,
350         address _token,
351         address _to,
352         uint256 _amount
353     )
354         private
355         returns (bytes memory msgData_, CanonicalERC20 memory ctoken_, uint256 balanceChange_)
356     {

391     function _getOrDeployBridgedToken(CanonicalERC20 memory ctoken) 
392         private
393         returns (address btoken)
394     {

407     function _deployBridgedToken(CanonicalERC20 memory ctoken) private returns (address btoken) { 
```
([221](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L221-L225), [276](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L276-L279), [298](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L298-L300), [348](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L348-L356), [391](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L391-L394), [407](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L407))

```solidity
File: contracts/tokenvault/ERC721Vault.sol

187     function _handleMessage( 
188         address _user,
189         BridgeTransferOp memory _op
190     )
191         private
192         returns (bytes memory msgData_, CanonicalNFT memory ctoken_)
193     {

224     function _getOrDeployBridgedToken(CanonicalNFT memory _ctoken) 
225         private
226         returns (address btoken_)
227     {

240     function _deployBridgedToken(CanonicalNFT memory _ctoken) private returns (address btoken_) { 

242             BridgedERC721.init, 
243             (owner(), addressManager, _ctoken.addr, _ctoken.chainId, _ctoken.symbol, _ctoken.name)
244         );
245 
246         btoken_ = address(new ERC1967Proxy(resolve("bridged_erc721", false), data));

259  
```
([187](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L187-L193), [224](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L224-L227), [240](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L240), [242](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L242-L246), [259](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L259))

```solidity
File: contracts/verifiers/SgxVerifier.sol

226     function _replaceInstance(uint256 id, address oldInstance, address newInstance) private { 

233     function _isInstanceValid(uint256 id, address instance) private view returns (bool) { 
```
([226](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L226), [233](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L233))

</details>

### [GAS&#x2011;051] Redundant state variable getters
Getters for public state variables are automatically generated so there is no need to code them manually and waste gas.

<details>
<summary><i>There are 2 instances (click to view)</i></summary>

```solidity
File: contracts/L2/TaikoL2EIP1559Configurable.sol

43     function getConfig() public view override returns (Config memory) { 
44         return customConfig;
45     }
```
([43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L43-L45))

```solidity
File: contracts/team/TimelockTokenPool.sol

204     function getMyGrant(address _recipient) public view returns (Grant memory) { 
205         return recipients[_recipient].grant;
206     }
```
([204](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L204-L206))

</details>

### [GAS&#x2011;052] Remove or replace unused state variables
Saves a storage slot. If the variable is assigned a non-zero value, saves Gsset (**20000 gas**). If it's assigned a zero value, saves Gsreset (**2900 gas**). If the variable remains unassigned, there is no gas savings unless the variable is `public`, in which case the compiler-generated non-payable getter deployment cost is saved. If the state variable is overriding an interface's public function, mark the variable as `constant` or `immutable` so that it does not use a storage slot

<details>
<summary><i>There are 29 instances (click to view)</i></summary>

```solidity
File: contracts/L1/TaikoL1.sol

26     uint256[50] private __gap; 
```
([26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L26))

```solidity
File: contracts/L1/TaikoToken.sol

16     uint256[50] private __gap; 
```
([16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L16))

```solidity
File: contracts/L1/gov/TaikoGovernor.sol

23     uint256[50] private __gap; 
```
([23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L23))

```solidity
File: contracts/L1/gov/TaikoTimelockController.sol

10     uint256[50] private __gap; 
```
([10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L10))

```solidity
File: contracts/L1/provers/GuardianProver.sol

11     uint256[50] private __gap; 
```
([11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L11))

```solidity
File: contracts/L1/provers/Guardians.sol

32     uint256[46] private __gap; 
```
([32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L32))

```solidity
File: contracts/L1/tiers/DevnetTierProvider.sol

11     uint256[50] private __gap; 
```
([11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L11))

```solidity
File: contracts/L1/tiers/MainnetTierProvider.sol

11     uint256[50] private __gap; 
```
([11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L11))

```solidity
File: contracts/L1/tiers/TestnetTierProvider.sol

11     uint256[50] private __gap; 
```
([11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L11))

```solidity
File: contracts/L2/CrossChainOwned.sol

21     uint256[49] private __gap; 
```
([21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L21))

```solidity
File: contracts/L2/TaikoL2EIP1559Configurable.sol

13     uint256[49] private __gap; 
```
([13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L13))

```solidity
File: contracts/bridge/Bridge.sol

48     uint256[43] private __gap; 
```
([48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L48))

```solidity
File: contracts/common/AddressManager.sol

14     uint256[49] private __gap; 
```
([14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L14))

```solidity
File: contracts/common/AddressResolver.sol

14     uint256[49] private __gap; 
```
([14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L14))

```solidity
File: contracts/common/EssentialContract.sol

25     uint256[49] private __gap; 
```
([25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L25))

```solidity
File: contracts/signal/SignalService.sol

23     uint256[48] private __gap; 
```
([23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L23))

```solidity
File: contracts/team/airdrop/ERC20Airdrop.sol

18     uint256[48] private __gap; 
```
([18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L18))

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol

30     uint256[45] private __gap; 
```
([30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L30))

```solidity
File: contracts/team/airdrop/ERC721Airdrop.sol

16     uint256[48] private __gap; 
```
([16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L16))

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol

23     uint256[47] private __gap; 
```
([23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L23))

```solidity
File: contracts/tokenvault/BaseVault.sol

18     uint256[50] private __gap; 
```
([18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L18))

```solidity
File: contracts/tokenvault/BridgedERC1155.sol

27     uint256[46] private __gap; 
```
([27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L27))

```solidity
File: contracts/tokenvault/BridgedERC20.sol

32     uint256[47] private __gap; 
```
([32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L32))

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol

16     uint256[49] private __gap; 
```
([16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L16))

```solidity
File: contracts/tokenvault/BridgedERC721.sol

19     uint256[48] private __gap; 
```
([19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L19))

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

32     uint256[50] private __gap; 
```
([32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L32))

```solidity
File: contracts/tokenvault/ERC721Vault.sol

19     uint256[50] private __gap; 
```
([19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L19))

```solidity
File: contracts/tokenvault/adapters/USDCAdapter.sol

32     uint256[49] private __gap; 
```
([32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L32))

```solidity
File: contracts/verifiers/GuardianVerifier.sol

11     uint256[50] private __gap; 
```
([11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L11))

</details>

### [GAS&#x2011;053] `require()`/`revert()` strings longer than 32 bytes cost extra gas
Each extra memory word of bytes past the original 32 [incurs an MSTORE](https://gist.github.com/hrkrshnn/ee8fabd532058307229d65dcd5836ddc#consider-having-short-revert-strings) which costs **3 gas**

<details>
<summary><i>There are 27 instances (click to view)</i></summary>

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

// @audit 63
87         require( 
88             v3Quote.v3AuthData.certification.certType == 5,
89             "certType must be 5: Concatenated PCK Cert Chain (PEM formatted)"
90         );
```
([87](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L87-L90))

```solidity
File: contracts/thirdparty/optimism/rlp/RLPReader.sol

// @audit 74
37         require( 
38             _in.length > 0,
39             "RLPReader: length of an RLP item must be greater than zero to be decodable"
40         );

// @audit 56
56         require( 
57             itemType == RLPItemType.LIST_ITEM,
58             "RLPReader: decoded item type for list is not a list item"
59         );

// @audit 50
61         require( 
62             listOffset + listLength == _in.length,
63             "RLPReader: list item has an invalid data remainder"
64         );

// @audit 57
112         require( 
113             itemType == RLPItemType.DATA_ITEM,
114             "RLPReader: decoded item type for bytes is not a data item"
115         );

// @audit 52
117         require( 
118             _in.length == itemOffset + itemLength,
119             "RLPReader: bytes value contains an invalid remainder"
120         );

// @audit 74
152         require( 
153             _in.length > 0,
154             "RLPReader: length of an RLP item must be greater than zero to be decodable"
155         );

// @audit 78
172             require( 
173                 _in.length > strLen,
174                 "RLPReader: length of content must be greater than string length (short string)"
175             );

// @audit 77
182             require( 
183                 strLen != 1 || firstByteOfContent >= 0x80,
184                 "RLPReader: invalid prefix, single byte < 0x80 are not prefixed (short string)"
185             );

// @audit 81
192             require( 
193                 _in.length > lenOfStrLen,
194                 "RLPReader: length of content must be > than length of string length (long string)"
195             );

// @audit 74
202             require( 
203                 firstByteOfContent != 0x00,
204                 "RLPReader: length of content must not have any leading zeros (long string)"
205             );

// @audit 72
212             require( 
213                 strLen > 55,
214                 "RLPReader: length of content must be greater than 55 bytes (long string)"
215             );

// @audit 76
217             require( 
218                 _in.length > lenOfStrLen + strLen,
219                 "RLPReader: length of content must be greater than total length (long string)"
220             );

// @audit 74
228             require( 
229                 _in.length > listLen,
230                 "RLPReader: length of content must be greater than list length (short list)"
231             );

// @audit 77
238             require( 
239                 _in.length > lenOfListLen,
240                 "RLPReader: length of content must be > than length of list length (long list)"
241             );

// @audit 72
248             require( 
249                 firstByteOfContent != 0x00,
250                 "RLPReader: length of content must not have any leading zeros (long list)"
251             );

// @audit 70
258             require( 
259                 listLen > 55,
260                 "RLPReader: length of content must be greater than 55 bytes (long list)"
261             );

// @audit 74
263             require( 
264                 _in.length > lenOfListLen + listLen,
265                 "RLPReader: length of content must be greater than total length (long list)"
266             );
```
([37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L37-L40), [56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L56-L59), [61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L61-L64), [112](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L112-L115), [117](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L117-L120), [152](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L152-L155), [172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L172-L175), [182](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L182-L185), [192](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L192-L195), [202](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L202-L205), [212](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L212-L215), [217](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L217-L220), [228](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L228-L231), [238](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L238-L241), [248](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L248-L251), [258](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L258-L261), [263](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L263-L266))

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

// @audit 46
89             require(currentKeyIndex <= key.length, "MerkleTrie: key index exceeds total key length"); 

// @audit 39
99                 require( 
100                     Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
101                     "MerkleTrie: invalid large internal hash"
102                 );

// @audit 38
105                 require( 
106                     Bytes.equal(currentNode.encoded, currentNodeID),
107                     "MerkleTrie: invalid internal node hash"
108                 );

// @audit 59
119                     require( 
120                         value_.length > 0,
121                         "MerkleTrie: value length must be greater than zero (branch)"
122                     );

// @audit 58
125                     require( 
126                         i == proof.length - 1,
127                         "MerkleTrie: value node must be last node in proof (branch)"
128                     );

// @audit 58
150                 require( 
151                     pathRemainder.length == sharedNibbleLength,
152                     "MerkleTrie: path remainder must share all nibbles with key"
153                 );

// @audit 61
162                     require( 
163                         keyRemainder.length == sharedNibbleLength,
164                         "MerkleTrie: key remainder must be identical to path remainder"
165                     );

// @audit 57
172                     require( 
173                         value_.length > 0,
174                         "MerkleTrie: value length must be greater than zero (leaf)"
175                     );

// @audit 56
178                     require( 
179                         i == proof.length - 1,
180                         "MerkleTrie: value node must be last node in proof (leaf)"
181                     );
```
([89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L89), [99](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L99-L102), [105](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L105-L108), [119](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L119-L122), [125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L125-L128), [150](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L150-L153), [162](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L162-L165), [172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L172-L175), [178](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L178-L181))

</details>

### [GAS&#x2011;054] Same cast is done multiple times
It's cheaper to do it once, and store the result to a variable. The examples below are the second+ instance of a given cast of the variable

<details>
<summary><i>There are 4 instances (click to view)</i></summary>

```solidity
File: contracts/L1/libs/LibVerifying.sol

// @audit uint64(block.timestamp) : 3 times
47     function init( 
```
([47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L47))

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol

// @audit bytes2(svnValueBytes) : 2 times
// @audit uint256(svnValue) : 2 times
341     function _findTcb( 
```
([341](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L341))

```solidity
File: contracts/thirdparty/optimism/rlp/RLPWriter.sol

// @audit uint8(_offset) : 2 times
32     function _writeLength(uint256 _len, uint256 _offset) private pure returns (bytes memory out_) { 
```
([32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L32))

</details>

### [GAS&#x2011;055] Shortcircuit rules can be be used to optimize some gas usage
Some conditions may be reordered to save an `SLOAD` (2100 gas), as we avoid reading state variables when the first part of the condition fails (with `&&`), or succeeds (with `||`).

<details>
<summary><i>There are 2 instances (click to view)</i></summary>

```solidity
File: contracts/L2/CrossChainOwned.sol

46         if (ctx.srcChainId != ownerChainId || ctx.from != owner()) { 
```
([46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L46))

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol

40         if (claimEnd > block.timestamp || claimEnd + withdrawalWindow < block.timestamp) { 
```
([40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L40))

</details>

### [GAS&#x2011;056] Simple checks for zero can be done using assembly to save gas
<details>
<summary><i>There are 40 instances (click to view)</i></summary>

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

81         if ( 
82             block.timestamp > assignment.expiry
83                 || assignment.metaHash != 0 && _blk.metaHash != assignment.metaHash
84                 || assignment.parentMetaHash != 0 && _meta.parentMetaHash != assignment.parentMetaHash
85                 || assignment.maxBlockId != 0 && _meta.id > assignment.maxBlockId
86                 || assignment.maxProposedIn != 0 && block.number > assignment.maxProposedIn

109         if (assignment.feeToken == address(0)) { 

120         if (input.tip != 0 && block.coinbase != address(0)) { 
```
([81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L81-L86), [109](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L109), [120](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L120))

```solidity
File: contracts/L1/libs/LibProposing.sol

81         if (params.assignedProver == address(0)) { 

85         if (params.coinbase == address(0)) { 

108         if (params.parentMetaHash != 0 && parentMetaHash != params.parentMetaHash) { 

141         if (meta_.blobUsed) { 

144             if (params.blobHash != 0) { 

159                 if (meta_.blobHash == 0) revert L1_BLOB_NOT_FOUND(); 

185             if (params.txListByteOffset != 0) { 

195         if (meta_.txListByteSize == 0 || meta_.txListByteSize > _config.blockMaxTxListBytes) { 

260             if (address(this).balance != 0) { 

307         if (_slotB.numBlocks == 1) { 

310             if (proposerOne != address(0) && msg.sender != proposerOne) { 
```
([81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L81), [85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L85), [108](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L108), [141](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L141), [144](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L144), [159](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L159), [185](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L185), [195](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L195), [260](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L260), [307](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L307), [310](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L310))

```solidity
File: contracts/L1/libs/LibProving.sol

105         if (_tran.parentHash == 0 || _tran.blockHash == 0 || _tran.stateRoot == 0) { 

134         if (_proof.tier == 0 || _proof.tier < _meta.minTier || _proof.tier < ts.tier) { 

203         if (_proof.tier > ts.tier) { 

280         if (tid_ == 0) { 

363         if (_ts.contester != address(0)) { 

412         if (_tier.contestBond == 0) return; 
```
([105](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L105), [134](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L134), [203](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L203), [280](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L280), [363](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L363), [412](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L412))

```solidity
File: contracts/common/AddressResolver.sol

81         if (addressManager == address(0)) revert RESOLVER_INVALID_MANAGER(); 

85         if (!_allowZeroAddress && addr_ == address(0)) { 
```
([81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L81), [85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L85))

```solidity
File: contracts/common/EssentialContract.sol

105         if (_addressManager == address(0)) revert ZERO_ADDR_MANAGER(); 
```
([105](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L105))

```solidity
File: contracts/libs/LibAddress.sol

24         if (_to == address(0)) revert ETH_TRANSFER_FAILED(); 
```
([24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L24))

```solidity
File: contracts/libs/LibTrieProof.sol

46         if (_accountProof.length != 0) { 

50             if (rlpAccount.length == 0) revert LTP_INVALID_ACCOUNT_PROOF(); 
```
([46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L46), [50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L50))

</details>

### [GAS&#x2011;057] Use short-circuit mode for conditions
Rearrange expressions to leverage short-circuiting and save gas.

<details>
<summary><i>There are 40 instances (click to view)</i></summary>

```solidity
File: contracts/L1/gov/TaikoGovernor.sol

89     function supportsInterface(bytes4 _interfaceId) 
90         public
91         view
92         override(GovernorUpgradeable, GovernorTimelockControlUpgradeable, IERC165Upgradeable)
93         returns (bool)
94     {
95         return super.supportsInterface(_interfaceId);
```
([89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L89-L95))

```solidity
File: contracts/L1/gov/TaikoTimelockController.sol

28  
```
([28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L28))

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

81         if ( 
82             block.timestamp > assignment.expiry
83                 || assignment.metaHash != 0 && _blk.metaHash != assignment.metaHash
84                 || assignment.parentMetaHash != 0 && _meta.parentMetaHash != assignment.parentMetaHash
85                 || assignment.maxBlockId != 0 && _meta.id > assignment.maxBlockId
86                 || assignment.maxProposedIn != 0 && block.number > assignment.maxProposedIn
87         ) {
88             revert HOOK_ASSIGNMENT_EXPIRED();
89         }

91         // Hash the assignment with the blobHash, this hash will be signed by 
92         // the prover, therefore, we add a string as a prefix.
93         address taikoL1Address = msg.sender;
94         bytes32 hash = hashAssignment(assignment, taikoL1Address, _meta.blobHash);

120         if (input.tip != 0 && block.coinbase != address(0)) { 
121             address(block.coinbase).sendEther(input.tip);
122         }
```
([81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L81-L89), [91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L91-L94), [120](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L120-L122))

```solidity
File: contracts/L1/libs/LibProposing.sol

108         if (params.parentMetaHash != 0 && parentMetaHash != params.parentMetaHash) { 
109             revert L1_UNEXPECTED_PARENT();
110         }

164                 if (_config.blobReuseEnabled && params.cacheBlobForReuse) { 
165                     _state.reusableBlobs[meta_.blobHash] = block.timestamp;
166                     emit BlobCached(meta_.blobHash);
167                 }

195         if (meta_.txListByteSize == 0 || meta_.txListByteSize > _config.blockMaxTxListBytes) { 
196             revert L1_TXLIST_SIZE();
197         }

310             if (proposerOne != address(0) && msg.sender != proposerOne) { 
311                 return false;
312             }
```
([108](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L108-L110), [164](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L164-L167), [195](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L195-L197), [310](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L310-L312))

```solidity
File: contracts/L1/libs/LibProving.sol

105         if (_tran.parentHash == 0 || _tran.blockHash == 0 || _tran.stateRoot == 0) { 
106             revert L1_INVALID_TRANSITION();
107         }

111         if (_meta.id <= b.lastVerifiedBlockId || _meta.id >= b.numBlocks) { 
112             revert L1_INVALID_BLOCK_ID();
113         }

121         if (blk.blockId != _meta.id || blk.metaHash != keccak256(abi.encode(_meta))) { 
122             revert L1_BLOCK_MISMATCH();
123         }

134         if (_proof.tier == 0 || _proof.tier < _meta.minTier || _proof.tier < ts.tier) { 
135             revert L1_INVALID_TIER();
136         }

419         if (_tid == 1 && _ts.tier == 0 && inProvingWindow) { 
420             if (!isAssignedPover) revert L1_NOT_ASSIGNED_PROVER();
421         } else {
422             // Disallow the same address to prove the block so that we can detect that the
423             // assigned prover should not receive his liveness bond back
424             if (isAssignedPover) revert L1_ASSIGNED_PROVER_NOT_ALLOWED();
425         }
```
([105](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L105-L107), [111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L111-L113), [121](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L121-L123), [134](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L134-L136), [419](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L419-L425))

```solidity
File: contracts/L1/libs/LibUtils.sol

34         if (_blockId < b.lastVerifiedBlockId || _blockId >= b.numBlocks) { 
35             revert L1_INVALID_BLOCK_ID();
36         }
```
([34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L34-L36))

```solidity
File: contracts/L1/libs/LibVerifying.sol

246         if ( 
247             _config.chainId <= 1 || _config.chainId == block.chainid //
248                 || _config.blockMaxProposals == 1
249                 || _config.blockRingBufferSize <= _config.blockMaxProposals + 1
250                 || _config.blockMaxGasLimit == 0 || _config.blockMaxTxListBytes == 0
251                 || _config.blockMaxTxListBytes > 128 * 1024 // calldata up to 128K
252                 || _config.livenessBond == 0 || _config.ethDepositRingBufferSize <= 1
253                 || _config.ethDepositMinCountPerBlock == 0
254             // Audit recommendation, and gas tested. Processing 32 deposits (as initially set in
255             // TaikoL1.sol) costs 72_502 gas.
256             || _config.ethDepositMaxCountPerBlock > 32
257                 || _config.ethDepositMaxCountPerBlock < _config.ethDepositMinCountPerBlock
258                 || _config.ethDepositMinAmount == 0
259                 || _config.ethDepositMaxAmount <= _config.ethDepositMinAmount
260                 || _config.ethDepositMaxAmount > type(uint96).max || _config.ethDepositGas == 0
261                 || _config.ethDepositMaxFee == 0
262                 || _config.ethDepositMaxFee > type(uint96).max / _config.ethDepositMaxCountPerBlock
263         ) return false;
```
([246](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L246-L263))

```solidity
File: contracts/common/AddressManager.sol

62  
```
([62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L62))

```solidity
File: contracts/common/AddressResolver.sol

85         if (!_allowZeroAddress && addr_ == address(0)) { 
86             revert RESOLVER_ZERO_ADDR(_chainId, _name);
87         }
```
([85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L85-L87))

```solidity
File: contracts/libs/Lib4844.sol

57         if (uint256(first) != FIELD_ELEMENTS_PER_BLOB || uint256(second) != BLS_MODULUS) { 
58             revert EVAL_FAILED_2();
59         }
```
([57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L57-L59))

</details>

### [GAS&#x2011;058] Split require checks to save gas
See [this issue](https://github.com/code-423n4/2022-01-xdefi-findings/issues/128) which describes the fact that there is a larger deployment gas cost, but with enough runtime calls, the change ends up being cheaper by **3 gas**

<details>
<summary><i>There are 4 instances (click to view)</i></summary>

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

77         require( 
78             localEnclaveReport.reserved3.length == 96 && localEnclaveReport.reserved4.length == 60
79                 && localEnclaveReport.reportData.length == 64,
80             "local QE report has wrong length"
81         );
82         require(
83             pckSignedQeReport.reserved3.length == 96 && pckSignedQeReport.reserved4.length == 60
84                 && pckSignedQeReport.reportData.length == 64,
85             "QE report has wrong length"
86         );

94         require( 
95             v3Quote.v3AuthData.ecdsa256BitSignature.length == 64
96                 && v3Quote.v3AuthData.ecdsaAttestationKey.length == 64
97                 && v3Quote.v3AuthData.qeReportSignature.length == 64,
98             "Invalid ECDSA signature format"
99         );
```
([77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L77-L86), [94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L94-L99))

```solidity
File: contracts/automata-attestation/utils/BytesUtils.sol

335             require(char >= 0x30 && char <= 0x7A, "invalid char"); 
```
([335](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L335))

</details>

### [GAS&#x2011;059] Split if-revert checks to save gas
Splitting the conditions into two separate checks [saves](https://gist.github.com/IllIllI000/7e25b0fca6bd9d57d9b9bcb9d2018959) 2 **gas**

<details>
<summary><i>There are 5 instances (click to view)</i></summary>

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol

34         if ( 
35             merkleRoot == 0x0 || claimStart == 0 || claimEnd == 0 || claimStart > block.timestamp
36                 || claimEnd < block.timestamp
37         ) revert CLAIM_NOT_ONGOING();
```
([34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L34-L37))

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

108         if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO(); 
```
([108](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L108))

```solidity
File: contracts/tokenvault/ERC20Vault.sol

174             if ( 
175                 ctoken.decimals != _ctoken.decimals
176                     || keccak256(bytes(ctoken.symbol)) != keccak256(bytes(_ctoken.symbol))
177                     || keccak256(bytes(ctoken.name)) != keccak256(bytes(_ctoken.name))
178             ) revert VAULT_CTOKEN_MISMATCH();

267         if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO(); 
```
([174](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L174-L178), [267](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L267))

```solidity
File: contracts/tokenvault/ERC721Vault.sol

91         if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO(); 
```
([91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L91))

</details>

### [GAS&#x2011;060] Stack variable is only used once
If the variable is only accessed once, it's cheaper to use the assigned value directly that one time, and save the 3 gas the extra stack assignment would spend.

<details>
<summary><i>There are 40 instances (click to view)</i></summary>

```solidity
File: contracts/L1/TaikoL1.sol

94         uint8 maxBlocksToVerify = LibProving.proveBlock(state, config, this, meta, tran, proof); 
```
([94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L94))

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

94         bytes32 hash = hashAssignment(assignment, taikoL1Address, _meta.blobHash); 

101         IERC20 tko = IERC20(resolve("taiko_token", false)); 
```
([94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L94), [101](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L101))

```solidity
File: contracts/L1/libs/LibDepositing.sol

45         uint256 slot = _state.slotA.numEthDeposits % _config.ethDepositRingBufferSize; 
```
([45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L45))

```solidity
File: contracts/L1/libs/LibProposing.sol

238             uint256 tkoBalance = tko.balanceOf(address(this)); 
```
([238](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L238))

```solidity
File: contracts/L1/libs/LibProving.sol

164                 bool isContesting = _proof.tier == ts.tier && tier.contestBond != 0; 

166                 IVerifier.Context memory ctx = IVerifier.Context({ 

192             bool returnLivenessBond = blk.livenessBond > 0 && _proof.data.length == 32 

414         bool inProvingWindow = uint256(_ts.timestamp).max(_state.slotB.lastUnpausedAt) 
```
([164](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L164), [166](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L166), [192](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L192), [414](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L414))

```solidity
File: contracts/L1/libs/LibVerifying.sol

188                 IERC20 tko = IERC20(_resolver.resolve("taiko_token", false)); 
```
([188](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L188))

```solidity
File: contracts/L2/TaikoL2.sol

136         Config memory config = getConfig(); 
```
([136](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L136))

```solidity
File: contracts/bridge/Bridge.sol

89         uint64 _timestamp = _suspend ? type(uint64).max : uint64(block.timestamp); 

138         uint256 expectedAmount = _message.value + _message.fee; 

178             bytes32 failureSignal = signalForFailedMessage(msgHash); 

280                 uint256 gasLimit = msg.sender == _message.destOwner ? gasleft() : _message.gasLimit; 

557             bytes32 msgHash; 
558             address from;
559             uint64 srcChainId;

587         bytes memory data = abi.encodeCall( 
```
([89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L89), [138](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L138), [178](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L178), [280](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L280), [557](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L557-L559), [587](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L587))

```solidity
File: contracts/libs/Lib4844.sol

51         bytes32 first; 
52         bytes32 second;
```
([51](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L51-L52))

```solidity
File: contracts/libs/LibAddress.sol

56         try IERC165(_addr).supportsInterface(_interfaceId) returns (bool _result) { 
```
([56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L56))

```solidity
File: contracts/libs/LibTrieProof.sol

52             RLPReader.RLPItem[] memory accountState = RLPReader.readList(rlpAccount); 

60         bool verified = SecureMerkleTrie.verifyInclusionProof( 
```
([52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L52), [60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L60))

```solidity
File: contracts/signal/SignalService.sol

107             bytes32 signalRoot = _verifyHopProof(chainId, app, signal, value, hop, signalService); 

124             bytes32 kind = isFullProof ? LibSignals.STATE_ROOT : LibSignals.SIGNAL_ROOT; 

148         bytes32 signal = signalForChainData(_chainId, _kind, _blockId); 

170             bytes32 signal = signalForChainData(_chainId, _kind, blockId_); 

282         bool cacheStateRoot = _hop.cacheOption == CacheOption.CACHE_BOTH 

290         bool cacheSignalRoot = _hop.cacheOption == CacheOption.CACHE_BOTH 
```
([107](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L107), [124](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L124), [148](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L148), [170](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L170), [282](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L282), [290](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L290))

```solidity
File: contracts/tokenvault/BaseVault.sol

54         address selfOnSourceChain = resolve(ctx_.srcChainId, name(), false); 
```
([54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L54))

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

58         IBridge.Message memory message = IBridge.Message({ 

111         address token = _transferTokens(ctoken, to, tokenIds, amounts); 

140         (bytes memory data) = abi.decode(message.data[4:], (bytes)); 

145         address token = _transferTokens(ctoken, message.srcOwner, tokenIds, amounts); 

263                 try t.name() returns (string memory _name) { 

266                 try t.symbol() returns (string memory _symbol) { 

304         bytes memory data = abi.encodeCall( 
```
([58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L58), [111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L111), [140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L140), [145](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L145), [263](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L263), [266](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L266), [304](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L304))

```solidity
File: contracts/tokenvault/ERC20Vault.sol

221         IBridge.Message memory message = IBridge.Message({ 

270         address token = _transferTokens(ctoken, to, amount); 
```
([221](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L221), [270](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L270))

</details>

### [GAS&#x2011;061] State variable access within a loop
The state variable should be cached in and read from a local variable, or accumulated in a local variable then written to storage once outside of the loop, rather than reading/updating it on every iteration of the loop, which will replace each Gwarmaccess (**100 gas**) with a much cheaper stack read.

<details>
<summary><i>There are 8 instances (click to view)</i></summary>

```solidity
File: contracts/L1/provers/Guardians.sol

// @audit guardianIds, guardians
74         for (uint256 i; i < guardians.length; ++i) { 
75             delete guardianIds[guardians[i]];
76         }

// @audit guardians, guardians
80         for (uint256 i = 0; i < _newGuardians.length; ++i) { 
81             address guardian = _newGuardians[i];
82             if (guardian == address(0)) revert INVALID_GUARDIAN();
83             // This makes sure there are not duplicate addresses
84             if (guardianIds[guardian] != 0) revert INVALID_GUARDIAN_SET();
85 
86             // Save and index the guardian
87             guardians.push(guardian);
88             guardianIds[guardian] = guardians.length;
89         }

// @audit minGuardians
133             for (uint256 i; i < guardiansLength; ++i) { 
134                 if (bits & 1 == 1) ++count;
135                 if (count == minGuardians) return true;
136                 bits >>= 1;
137             }
```
([74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L74-L76), [80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L80-L89), [133](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L133-L137))

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

// @audit _serialNumIsRevoked, _serialNumIsRevoked
95         for (uint256 i; i < serialNumBatch.length; ++i) { 
96             if (!_serialNumIsRevoked[index][serialNumBatch[i]]) {
97                 continue;
98             }
99             delete _serialNumIsRevoked[index][serialNumBatch[i]];
100         }

// @audit _serialNumIsRevoked, _serialNumIsRevoked
259         for (uint256 i; i < n; ++i) { 
260             IPEMCertChainLib.ECSha256Certificate memory issuer;
261             if (i == n - 1) {
262                 // rootCA
263                 issuer = certs[i];
264             } else {
265                 issuer = certs[i + 1];
266                 if (i == n - 2) {
267                     // this cert is expected to be signed by the root
268                     certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.ROOT)][certs[i]
269                         .serialNumber];
270                 } else if (certs[i].isPck) {
271                     certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.PCK)][certs[i]
272                         .serialNumber];
273                 }
274                 if (certRevoked) {
275                     break;
276                 }
277             }
278 
279             certNotExpired =
280                 block.timestamp > certs[i].notBefore && block.timestamp < certs[i].notAfter;
281             if (!certNotExpired) {
282                 break;
283             }
284 
285             verified = sigVerifyLib.verifyES256Signature(
286                 certs[i].tbsCertificate, certs[i].signature, issuer.pubKey
287             );
288             if (!verified) {
289                 break;
290             }
291 
292             bytes32 issuerPubKeyHash = keccak256(issuer.pubKey);
293 
294             if (issuerPubKeyHash == ROOTCA_PUBKEY_HASH) {
295                 certChainCanBeTrusted = true;
296                 break;
297             }
298         }
```
([95](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L95-L100), [259](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L259-L298))

```solidity
File: contracts/team/airdrop/ERC721Airdrop.sol

// @audit vault, token
59         for (uint256 i; i < tokenIds.length; ++i) { 
60             IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);
61         }
```
([59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59-L61))

```solidity
File: contracts/verifiers/SgxVerifier.sol

// @audit instances, instances, instances
104         for (uint256 i; i < _ids.length; ++i) { 
105             uint256 idx = _ids[i];
106 
107             if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();
108 
109             emit InstanceDeleted(idx, instances[idx].addr);
110 
111             delete instances[idx];
112         }

// @audit validSince, validSince
210         for (uint256 i; i < _instances.length; ++i) { 
211             if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();
212 
213             addressRegistered[_instances[i]] = true;
214 
215             if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();
216 
217             instances[nextInstanceId] = Instance(_instances[i], validSince);
218             ids[i] = nextInstanceId;
219 
220             emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);
221 
222             nextInstanceId++;
223         }
```
([104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L104-L112), [210](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210-L223))

</details>

### [GAS&#x2011;062] State variables can be packed into fewer storage slots
If variables occupying the same slot are both written the same function or by the constructor, avoids a separate Gsset (**20000 gas**). Reads of the variables can also be cheaper

<details>
<summary><i>There are 2 instances (click to view)</i></summary>

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

// @audit follow this order to use 6 instead of 7 storage slots:
// @audit _trustedUserMrEnclave(32), _trustedUserMrSigner(32), _serialNumIsRevoked(32), tcbInfo(32), qeIdentity(32), owner(20), _checkLocalEnclaveReport(1)
22 contract AutomataDcapV3Attestation is IAttestation { 
```
([22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L22))

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol

// @audit follow this order to use 5 instead of 6 storage slots:
// @audit claimedAmount(32), withdrawnAmount(32), __gap(32), token(20), withdrawalWindow(8), vault(20)
12 contract ERC20Airdrop2 is MerkleClaimable { 
```
([12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L12))

</details>

### [GAS&#x2011;063] State variables only set in the constructor should be declared `immutable`
Avoids a Gsset (**20000 gas**) in the constructor, and replaces the first access in each transaction (Gcoldsload - **2100 gas**) and each access thereafter (Gwarmacces - **100 gas**) with a `PUSH32` (**3 gas**).

While `string`s are not value types, and therefore cannot be `immutable`/`constant` if not hard-coded outside of the constructor, the same behavior can be achieved by making the current contract `abstract` with `virtual` functions for the `string` accessors, and having a child contract override the functions with the hard-coded implementation-specific values.

<details>
<summary><i>There are 2 instances (click to view)</i></summary>

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

52     address public owner; 
```
([52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L52))

```solidity
File: contracts/automata-attestation/utils/SigVerifyLib.sol

18     address private ES256VERIFIER; 
```
([18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L18))

</details>

### [GAS&#x2011;064] State variables should be cached in stack variables rather than re-reading them from storage
When performing multiple operations on a state variable in a function, it is recommended to cache it first. Either multiple reads or multiple writes to a state variable can save gas by caching it on the stack. Caching of a state variable replaces each Gwarmaccess (100 gas) with a much cheaper stack read. Other less obvious fixes/optimizations include having local memory caches of state variable structs, or having local caches of state variable contracts/addresses. *Saves 100 gas per instance*.

<details>
<summary><i>There are 40 instances (click to view)</i></summary>

```solidity
File: contracts/L1/TaikoL1.sol

// @audit _initialized is read 2 times
42     function init( 
43         address _owner,
44         address _addressManager,
45         bytes32 _genesisBlockHash
46     )
47         external
48         initializer
49     {

// @audit state is read 3 times
55     function proposeBlock( 
56         bytes calldata _params,
57         bytes calldata _txList
58     )
59         external
60         payable
61         nonReentrant
62         whenNotPaused
63         returns (TaikoData.BlockMetadata memory meta_, TaikoData.EthDeposit[] memory deposits_)
64     {

// @audit state is read 3 times
75     function proveBlock( 
76         uint64 _blockId,
77         bytes calldata _input
78     )
79         external
80         nonReentrant
81         whenNotPaused
82         whenProvingNotPaused
83     {

// @audit state is read 2 times
100     function verifyBlocks(uint64 _maxBlocksToVerify) 
101         external
102         nonReentrant
103         whenNotPaused
104         whenProvingNotPaused
105     {

// @audit state is read 2 times
145     function getBlock(uint64 _blockId) 
146         public
147         view
148         returns (TaikoData.Block memory blk_, TaikoData.TransitionState memory ts_)
149     {

// @audit state is read 2 times
176     function getStateVariables() 
177         public
178         view
179         returns (TaikoData.SlotA memory a_, TaikoData.SlotB memory b_)
180     {
```
([42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L42-L49), [55](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L55-L64), [75](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L75-L83), [100](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L100-L105), [145](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L145-L149), [176](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L176-L180))

```solidity
File: contracts/L1/TaikoToken.sol

// @audit _initialized is read 2 times
25     function init( 
26         address _owner,
27         string calldata _name,
28         string calldata _symbol,
29         address _recipient
30     )
31         public
32         initializer
33     {
```
([25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L25-L33))

```solidity
File: contracts/L1/gov/TaikoGovernor.sol

// @audit _initialized is read 2 times
31     function init( 
32         address _owner,
33         IVotesUpgradeable _token,
34         TimelockControllerUpgradeable _timelock
35     )
36         external
37         initializer
38     {
```
([31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L31-L38))

```solidity
File: contracts/L1/gov/TaikoTimelockController.sol

// @audit _initialized is read 2 times
15     function init(address _owner, uint256 _minDelay) external initializer { 
```
([15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L15))

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

// @audit _initialized is read 2 times
57     function init(address _owner, address _addressManager) external initializer { 
```
([57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L57))

```solidity
File: contracts/L1/provers/GuardianProver.sol

// @audit _initialized is read 2 times
25     function init(address _owner, address _addressManager) external initializer { 
```
([25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L25))

```solidity
File: contracts/L1/provers/Guardians.sol

// @audit guardianIds is read 2 times
// @audit guardians is read 5 times
// @audit version is read 2 times
53     function setGuardians( 
54         address[] memory _newGuardians,
55         uint8 _minGuardians
56     )
57         external
58         onlyOwner
59         nonReentrant
60     {

// @audit _approvals is read 2 times
// @audit version is read 2 times
111     function approve(uint256 _operationId, bytes32 _hash) internal returns (bool approved_) { 
```
([53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L53-L60), [111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L111))

```solidity
File: contracts/L1/tiers/DevnetTierProvider.sol

// @audit _initialized is read 2 times
15     function init(address _owner) external initializer { 
```
([15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L15))

```solidity
File: contracts/L1/tiers/MainnetTierProvider.sol

// @audit _initialized is read 2 times
15     function init(address _owner) external initializer { 
```
([15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L15))

```solidity
File: contracts/L1/tiers/TestnetTierProvider.sol

// @audit _initialized is read 2 times
15     function init(address _owner) external initializer { 
```
([15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L15))

```solidity
File: contracts/L2/CrossChainOwned.sol

// @audit nextTxId is read 2 times
36     function onMessageInvocation(bytes calldata _data) 
37         external
38         payable
39         whenNotPaused
40         onlyFromNamed("bridge")
41     {
```
([36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L36-L41))

```solidity
File: contracts/L2/TaikoL2.sol

// @audit _initialized is read 2 times
71     function init( 
72         address _owner,
73         address _addressManager,
74         uint64 _l1ChainId,
75         uint64 _gasExcess
76     )
77         external
78         initializer
79     {

// @audit gasExcess is read 2 times
// @audit lastSyncedBlock is read 3 times
252     function _calc1559BaseFee( 
253         Config memory _config,
254         uint64 _l1BlockId,
255         uint32 _parentGasUsed
256     )
257         private
258         view
259         returns (uint256 basefee_, uint64 gasExcess_)
260     {
```
([71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L71-L79), [252](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L252-L260))

```solidity
File: contracts/bridge/Bridge.sol

// @audit _initialized is read 2 times
75     function init(address _owner, address _addressManager) external initializer { 

// @audit proofReceipt is read 2 times
155     function recallMessage( 
156         Message calldata _message,
157         bytes calldata _proof
158     )
159         external
160         nonReentrant
161         whenNotPaused
162         sameChain(_message.srcChainId)
163     {

// @audit proofReceipt is read 3 times
217     function processMessage( 
218         Message calldata _message,
219         bytes calldata _proof
220     )
221         external
222         nonReentrant
223         whenNotPaused
224         sameChain(_message.destChainId)
225     {
```
([75](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L75), [155](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L155-L163), [217](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L217-L225))

```solidity
File: contracts/common/AddressManager.sol

// @audit _initialized is read 2 times
30     function init(address _owner) external initializer { 
```
([30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L30))

```solidity
File: contracts/common/AddressResolver.sol

// @audit addressManager is read 2 times
72     function _resolve( 
73         uint64 _chainId,
74         bytes32 _name,
75         bool _allowZeroAddress
76     )
77         private
78         view
79         returns (address payable addr_)
80     {
```
([72](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L72-L80))

```solidity
File: contracts/signal/SignalService.sol

// @audit _initialized is read 2 times
48     function init(address _owner, address _addressManager) external initializer { 
```
([48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L48))

```solidity
File: contracts/tokenvault/BaseVault.sol

// @audit _initialized is read 2 times
32     function init(address _owner, address _addressManager) external initializer { 
```
([32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L32))

```solidity
File: contracts/tokenvault/BridgedERC1155.sol

// @audit _initialized is read 2 times
38     function init( 
39         address _owner,
40         address _addressManager,
41         address _srcToken,
42         uint256 _srcChainId,
43         string memory _symbol,
44         string memory _name
45     )
46         external
47         initializer
48     {
```
([38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L38-L48))

```solidity
File: contracts/tokenvault/BridgedERC20.sol

// @audit _initialized is read 2 times
52     function init( 
53         address _owner,
54         address _addressManager,
55         address _srcToken,
56         uint256 _srcChainId,
57         uint8 _decimals,
58         string memory _symbol,
59         string memory _name
60     )
61         external
62         initializer
63     {
```
([52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L52-L63))

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol

// @audit migratingAddress is read 2 times
57     function mint(address _account, uint256 _amount) public nonReentrant whenNotPaused { 

// @audit migratingAddress is read 2 times
75     function burn(address _account, uint256 _amount) public nonReentrant whenNotPaused { 
```
([57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L57), [75](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L75))

```solidity
File: contracts/tokenvault/BridgedERC721.sol

// @audit _initialized is read 2 times
31     function init( 
32         address _owner,
33         address _addressManager,
34         address _srcToken,
35         uint256 _srcChainId,
36         string memory _symbol,
37         string memory _name
38     )
39         external
40         initializer
41     {
```
([31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L31-L41))

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

// @audit bridgedToCanonical is read 2 times
240     function _handleMessage( 
241         address _user,
242         BridgeTransferOp memory _op
243     )
244         private
245         returns (bytes memory msgData_, CanonicalNFT memory ctoken_)
246     {
```
([240](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L240-L246))

```solidity
File: contracts/tokenvault/ERC20Vault.sol

// @audit bridgedToCanonical is read 3 times
148     function changeBridgedToken( 
149         CanonicalERC20 calldata _ctoken,
150         address _btokenNew
151     )
152         external
153         nonReentrant
154         whenNotPaused
155         onlyOwner
156         returns (address btokenOld_)
157     {

// @audit bridgedToCanonical is read 2 times
348     function _handleMessage( 
349         address _user,
350         address _token,
351         address _to,
352         uint256 _amount
353     )
354         private
355         returns (bytes memory msgData_, CanonicalERC20 memory ctoken_, uint256 balanceChange_)
356     {
```
([148](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L148-L157), [348](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L348-L356))

```solidity
File: contracts/tokenvault/adapters/USDCAdapter.sol

// @audit _initialized is read 2 times
38     function init(address _owner, address _addressManager, IUSDC _usdc) external initializer { 

// @audit usdc is read 2 times
47     function _burnToken(address _from, uint256 _amount) internal override { 
```
([38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L38), [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L47))

</details>

### [GAS&#x2011;065] Structs can be packed into fewer storage slots
In Solidity, data type packing within struct variables is a recommended practice to optimize gas usage and efficiency in smart contracts.

This technique leverages the fact that Ethereum’s storage model stores variables in slots, with each slot offering a capacity of 32 bytes. When data types that consume less than 32 bytes, such as **uint8**, **bool**, or **address**, are declared individually, each occupies a whole storage slot. However, when these smaller variables are grouped into a struct, they can share a storage slot, resulting in a significant reduction in storage requirements and, by extension, gas costs.

<details>
<summary><i>There are 4 instances (click to view)</i></summary>

```solidity
File: contracts/L1/TaikoData.sol

// @audit follow this order to use 7 instead of 8 storage slots:
// @audit ethDepositRingBufferSize(32), ethDepositGas(32), ethDepositMaxFee(32), livenessBond(12), blobAllowedForDA(1), blobReuseEnabled(1), blockSyncThreshold(1), blockMaxTxListBytes(3), blobExpiry(3), blockMaxGasLimit(4), ethDepositMinCountPerBlock(8), ethDepositMaxCountPerBlock(8), maxBlocksToVerifyPerProposal(8), blockMaxProposals(8), blockRingBufferSize(8), chainId(8), ethDepositMaxAmount(12), ethDepositMinAmount(12)
10     struct Config { 

// @audit follow this order to use 6 instead of 7 storage slots:
// @audit extraData(32), blobHash(32), parentMetaHash(32), hookCalls(32), assignedProver(20), cacheBlobForReuse(1), txListByteOffset(3), txListByteSize(3), coinbase(20)
78     struct BlockParams { 
```
([10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L10), [78](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L78))

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol

// @audit follow this order to use 9 instead of 10 storage slots:
// @audit mrEnclave(32), reserved2(32), mrSigner(32), reserved3(32), reserved4(32), reportData(32), reserved1(28), isvProdId(2), isvSvn(2), miscSelect(4), cpuSvn(16), attributes(16)
17     struct EnclaveReport { 
```
([17](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L17))

```solidity
File: contracts/team/TimelockTokenPool.sol

// @audit follow this order to use 3 instead of 4 storage slots:
// @audit amount(16), grantPeriod(4), unlockPeriod(4), grantCliff(8), unlockStart(8), unlockCliff(8), grantStart(8), costPerToken(16)
28     struct Grant { 
```
([28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L28))

</details>

### [GAS&#x2011;066] Structs can be assigned more efficiently
It's more efficient to declare an empty struct and then assign each struct element individually rather than defining the struct in a single line. This can result in significant gas savings of 130 per instance.

<details>
<summary><i>There are 22 instances (click to view)</i></summary>

```solidity
File: contracts/L1/TaikoL1.sol

191         return TaikoData.Config({ 
192             chainId: 167_008,
193             // Assume the block time is 3s, the protocol will allow ~1 month of
194             // new blocks without any verification.
195             blockMaxProposals: 864_000,
196             blockRingBufferSize: 864_100,
197             // Can be overridden by the tier config.
198             maxBlocksToVerifyPerProposal: 10,
199             blockMaxGasLimit: 15_000_000,
200             // Each go-ethereum transaction has a size limit of 128KB,
201             // and right now txList is still saved in calldata, so we set it
202             // to 120KB.
203             blockMaxTxListBytes: 120_000,
204             blobExpiry: 24 hours,
205             blobAllowedForDA: false,
206             blobReuseEnabled: false,
207             livenessBond: 250e18, // 250 Taiko token
208             // ETH deposit related.
209             ethDepositRingBufferSize: 1024,
210             ethDepositMinCountPerBlock: 8,
211             ethDepositMaxCountPerBlock: 32,
212             ethDepositMinAmount: 1 ether,
213             ethDepositMaxAmount: 10_000 ether,
214             ethDepositGas: 21_000,
215             ethDepositMaxFee: 1 ether / 10,
216             blockSyncThreshold: 16
217         });
```
([191](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L191-L217))

```solidity
File: contracts/L1/libs/LibDepositing.sol

51             TaikoData.EthDeposit({ 
52                 recipient: recipient_,
53                 amount: uint96(msg.value),
54                 id: _state.slotA.numEthDeposits
55             })

88                 deposits_[i] = TaikoData.EthDeposit({ 
89                     recipient: address(uint160(data >> 96)),
90                     amount: uint96(data),
91                     id: j
92                 });
```
([51](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L51-L55), [88](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L88-L92))

```solidity
File: contracts/L1/libs/LibProposing.sol

121             meta_ = TaikoData.BlockMetadata({ 
122                 l1Hash: blockhash(block.number - 1),
123                 difficulty: 0, // to be initialized below
124                 blobHash: 0, // to be initialized below
125                 extraData: params.extraData,
126                 depositsHash: keccak256(abi.encode(deposits_)),
127                 coinbase: params.coinbase,
128                 id: b.numBlocks,
129                 gasLimit: _config.blockMaxGasLimit,
130                 timestamp: uint64(block.timestamp),
131                 l1Height: uint64(block.number - 1),
132                 txListByteOffset: 0, // to be initialized below
133                 txListByteSize: 0, // to be initialized below
134                 minTier: 0, // to be initialized below
135                 blobUsed: _txList.length == 0,
136                 parentMetaHash: parentMetaHash
137             });

212         TaikoData.Block memory blk = TaikoData.Block({ 
213             metaHash: keccak256(abi.encode(meta_)),
214             // Safeguard the liveness bond to ensure its preservation,
215             // particularly in scenarios where it might be altered after the
216             // block's proposal but before it has been proven or verified.
217             livenessBond: _config.livenessBond,
218             blockId: b.numBlocks,
219             proposedAt: meta_.timestamp,
220             proposedIn: uint64(block.number),
221             // For a new block, the next transition ID is always 1, not 0.
222             nextTransitionId: 1,
223             // For unverified block, its verifiedTransitionId is always 0.
224             verifiedTransitionId: 0,
225             assignedProver: params.assignedProver
226         });
```
([121](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L121-L137), [212](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L212-L226))

```solidity
File: contracts/L1/libs/LibProving.sol

166                 IVerifier.Context memory ctx = IVerifier.Context({ 
167                     metaHash: blk.metaHash,
168                     blobHash: _meta.blobHash,
169                     // Separate msgSender to allow the prover to be any address in the future.
170                     prover: msg.sender,
171                     msgSender: msg.sender,
172                     blockId: blk.blockId,
173                     isContesting: isContesting,
174                     blobUsed: _meta.blobUsed
175                 });
```
([166](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L166-L175))

```solidity
File: contracts/L1/tiers/DevnetTierProvider.sol

22             return ITierProvider.Tier({ 
23                 verifierName: "tier_optimistic",
24                 validityBond: 250 ether, // TKO
25                 contestBond: 500 ether, // TKO
26                 cooldownWindow: 1440, //24 hours
27                 provingWindow: 120, // 2 hours
28                 maxBlocksToVerifyPerProof: 16
29             });

33             return ITierProvider.Tier({ 
34                 verifierName: "tier_guardian",
35                 validityBond: 0, // must be 0 for top tier
36                 contestBond: 0, // must be 0 for top tier
37                 cooldownWindow: 60, //1 hours
38                 provingWindow: 2880, // 48 hours
39                 maxBlocksToVerifyPerProof: 16
40             });
```
([22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L22-L29), [33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L33-L40))

```solidity
File: contracts/L1/tiers/MainnetTierProvider.sol

22             return ITierProvider.Tier({ 
23                 verifierName: "tier_sgx",
24                 validityBond: 250 ether, // TKO
25                 contestBond: 500 ether, // TKO
26                 cooldownWindow: 1440, //24 hours
27                 provingWindow: 60, // 1 hours
28                 maxBlocksToVerifyPerProof: 8
29             });

33             return ITierProvider.Tier({ 
34                 verifierName: "tier_sgx_zkvm",
35                 validityBond: 500 ether, // TKO
36                 contestBond: 1000 ether, // TKO
37                 cooldownWindow: 1440, //24 hours
38                 provingWindow: 240, // 4 hours
39                 maxBlocksToVerifyPerProof: 4
40             });

44             return ITierProvider.Tier({ 
45                 verifierName: "tier_guardian",
46                 validityBond: 0, // must be 0 for top tier
47                 contestBond: 0, // must be 0 for top tier
48                 cooldownWindow: 60, //1 hours
49                 provingWindow: 2880, // 48 hours
50                 maxBlocksToVerifyPerProof: 16
51             });
```
([22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L22-L29), [33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L33-L40), [44](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L44-L51))

```solidity
File: contracts/L1/tiers/TestnetTierProvider.sol

22             return ITierProvider.Tier({ 
23                 verifierName: "tier_optimistic",
24                 validityBond: 250 ether, // TKO
25                 contestBond: 500 ether, // TKO
26                 cooldownWindow: 1440, //24 hours
27                 provingWindow: 30, // 0.5 hours
28                 maxBlocksToVerifyPerProof: 12
29             });

33             return ITierProvider.Tier({ 
34                 verifierName: "tier_sgx",
35                 validityBond: 500 ether, // TKO
36                 contestBond: 1000 ether, // TKO
37                 cooldownWindow: 1440, //24 hours
38                 provingWindow: 60, // 1 hours
39                 maxBlocksToVerifyPerProof: 8
40             });

44             return ITierProvider.Tier({ 
45                 verifierName: "tier_guardian",
46                 validityBond: 0, // must be 0 for top tier
47                 contestBond: 0, // must be 0 for top tier
48                 cooldownWindow: 60, //1 hours
49                 provingWindow: 2880, // 48 hours
50                 maxBlocksToVerifyPerProof: 16
51             });
```
([22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L22-L29), [33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L33-L40), [44](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L44-L51))

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

54         v3ParsedQuote = V3Struct.ParsedV3QuoteStruct({ 
55             header: header,
56             localEnclaveReport: localEnclaveReport,
57             v3AuthData: authDataV3
58         });

190         header = V3Struct.Header({ 
191             version: version,
192             attestationKeyType: attestationKeyType,
193             teeType: teeType,
194             qeSvn: bytes2(rawHeader.substring(8, 2)),
195             pceSvn: bytes2(rawHeader.substring(10, 2)),
196             qeVendorId: qeVendorId,
197             userData: bytes20(rawHeader.substring(28, 20))
198         });
```
([54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L54-L58), [190](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L190-L198))

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

58         IBridge.Message memory message = IBridge.Message({ 
59             id: 0, // will receive a new value
60             from: address(0), // will receive a new value
61             srcChainId: 0, // will receive a new value
62             destChainId: _op.destChainId,
63             srcOwner: msg.sender,
64             destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,
65             to: resolve(_op.destChainId, name(), false),
66             refundTo: _op.refundTo,
67             value: msg.value - _op.fee,
68             fee: _op.fee,
69             gasLimit: _op.gasLimit,
70             data: data,
71             memo: _op.memo
72         });

256                 ctoken_ = CanonicalNFT({ 
257                     chainId: uint64(block.chainid),
258                     addr: _op.token,
259                     symbol: "",
260                     name: ""
261                 });
```
([58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L58-L72), [256](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L256-L261))

```solidity
File: contracts/tokenvault/ERC20Vault.sol

221         IBridge.Message memory message = IBridge.Message({ 
222             id: 0, // will receive a new value
223             from: address(0), // will receive a new value
224             srcChainId: 0, // will receive a new value
225             destChainId: _op.destChainId,
226             srcOwner: msg.sender,
227             destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,
228             to: resolve(_op.destChainId, name(), false),
229             refundTo: _op.refundTo,
230             value: msg.value - _op.fee,
231             fee: _op.fee,
232             gasLimit: _op.gasLimit,
233             data: data,
234             memo: _op.memo
235         });

365             ctoken_ = CanonicalERC20({ 
366                 chainId: uint64(block.chainid),
367                 addr: _token,
368                 decimals: meta.decimals(),
369                 symbol: meta.symbol(),
370                 name: meta.name()
371             });
```
([221](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L221-L235), [365](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L365-L371))

```solidity
File: contracts/tokenvault/ERC721Vault.sol

44         IBridge.Message memory message = IBridge.Message({ 
45             id: 0, // will receive a new value
46             from: address(0), // will receive a new value
47             srcChainId: 0, // will receive a new value
48             destChainId: _op.destChainId,
49             srcOwner: msg.sender,
50             destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,
51             to: resolve(_op.destChainId, name(), false),
52             refundTo: _op.refundTo,
53             value: msg.value - _op.fee,
54             fee: _op.fee,
55             gasLimit: _op.gasLimit,
56             data: data,
57             memo: _op.memo
58         });

203                 ctoken_ = CanonicalNFT({ 
204                     chainId: uint64(block.chainid),
205                     addr: _op.token,
206                     symbol: t.symbol(),
207                     name: t.name()
208                 });
```
([44](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L44-L58), [203](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L203-L208))

</details>

### [GAS&#x2011;067] Structs can be packed into fewer storage slots by truncating timestamp bytes
By using a `uint32` rather than a larger type for variables that track timestamps, one can save gas by using fewer storage slots per struct, at the expense of the protocol breaking after the year 2106 (when `uint32` wraps). If this is an acceptable tradeoff, each slot saved can avoid an extra Gsset (**20000 gas**) for the first setting of the struct. Subsequent reads as well as writes have smaller gas savings


<i>There is one instance of this issue:</i>

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

// @audit follow this order to use 6 instead of 7 storage slots:
// @audit metaHash(32), parentMetaHash(32), tierFees(32), signature(32), feeToken(20), expiry(4), maxProposedIn(8), maxBlockId(8)
// @audit change expiry to uint32
18     struct ProverAssignment { 
```
([18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L18))

### [GAS&#x2011;068] Unnecessary event parameters should be removed
`block.number` and `block.timestamp` are added to the event information by default, so adding them manually will waste additional gas.

<details>
<summary><i>There are 10 instances (click to view)</i></summary>

```solidity
File: contracts/L1/TaikoEvents.sol

21     event BlockProposed( 
22         uint256 indexed blockId,
23         address indexed assignedProver,
24         uint96 livenessBond,
25         TaikoData.BlockMetadata meta,
26         TaikoData.EthDeposit[] depositsProcessed
27     );

37     event BlockVerified( 
38         uint256 indexed blockId,
39         address indexed assignedProver,
40         address indexed prover,
41         bytes32 blockHash,
42         bytes32 stateRoot,
43         uint16 tier,
44         uint8 contestations
45     );

53     event TransitionProved( 
54         uint256 indexed blockId,
55         TaikoData.Transition tran,
56         address prover,
57         uint96 validityBond,
58         uint16 tier
59     );

67     event TransitionContested( 
68         uint256 indexed blockId,
69         TaikoData.Transition tran,
70         address contester,
71         uint96 contestBond,
72         uint16 tier
73     );
```
([21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L21-L27), [37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L37-L45), [53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L53-L59), [67](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L67-L73))

```solidity
File: contracts/L1/libs/LibProposing.sol

31     event BlockProposed( 
32         uint256 indexed blockId,
33         address indexed assignedProver,
34         uint96 livenessBond,
35         TaikoData.BlockMetadata meta,
36         TaikoData.EthDeposit[] depositsProcessed
37     );
```
([31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L31-L37))

```solidity
File: contracts/L1/libs/LibProving.sol

32     event TransitionProved( 
33         uint256 indexed blockId,
34         TaikoData.Transition tran,
35         address prover,
36         uint96 validityBond,
37         uint16 tier
38     );

46     event TransitionContested( 
47         uint256 indexed blockId,
48         TaikoData.Transition tran,
49         address contester,
50         uint96 contestBond,
51         uint16 tier
52     );
```
([32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L32-L38), [46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L46-L52))

```solidity
File: contracts/L1/libs/LibVerifying.sol

28     event BlockVerified( 
29         uint256 indexed blockId,
30         address indexed assignedProver,
31         address indexed prover,
32         bytes32 blockHash,
33         bytes32 stateRoot,
34         uint16 tier,
35         uint8 contestations
36     );
```
([28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L28-L36))

```solidity
File: contracts/L1/provers/GuardianProver.sol

18     event GuardianApproval( 
19         address indexed addr, uint256 indexed blockId, bytes32 blockHash, bool approved
20     );
```
([18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L18-L20))

```solidity
File: contracts/signal/ISignalService.sol

36     event ChainDataSynced( 
37         uint64 indexed chainId,
38         uint64 indexed blockId,
39         bytes32 indexed kind,
40         bytes32 data,
41         bytes32 signal
42     );
```
([36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L36-L42))

</details>

### [GAS&#x2011;069] The result of a function call should be cached rather than re-calling the function
External calls are expensive. Results of external function calls should be cached rather than call them multiple times. Consider caching the following:


<i>There are 10 instaces of this issue:</i>

```solidity
File: contracts/automata-attestation/utils/Asn1Decode.sol

// @audit j.ixl() - L100, L101
// @audit i.ixl() - L100, L101
98     function isChildOf(uint256 i, uint256 j) internal pure returns (bool) { 

// @audit ptr.ixf() - L112, L112
111     function bytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes memory) { 

// @audit ptr.ixs() - L122, L122
121     function allBytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes memory) { 

// @audit ptr.ixf() - L132, L132
131     function bytes32At(bytes memory der, uint256 ptr) internal pure returns (bytes32) { 

// @audit ptr.ixf() - L144, L145, L143
141     function uintAt(bytes memory der, uint256 ptr) internal pure returns (uint256) { 

// @audit ptr.ixf() - L157, L158, L161, L156, L159
154     function uintBytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes memory) { 

// @audit ptr.ixf() - L166, L166
165     function keccakOfBytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes32) { 

// @audit ptr.ixs() - L170, L170
169     function keccakOfAllBytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes32) { 

// @audit ptr.ixf() - L183, L184, L182
179     function bitstringAt(bytes memory der, uint256 ptr) internal pure returns (bytes memory) { 
```
([98](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L98), [111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L111), [121](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L121), [131](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L131), [141](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L141), [154](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L154), [165](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L165), [169](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L169), [179](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L179))

### [GAS&#x2011;070] Divisions can be `unchecked` to save gas
The division cannot overflow, since both the numerator and the denominator are non-negative

<details>
<summary><i>There are 8 instances (click to view)</i></summary>

```solidity
File: contracts/L1/libs/LibVerifying.sol

262                 || _config.ethDepositMaxFee > type(uint96).max / _config.ethDepositMaxCountPerBlock 
```
([262](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L262))

```solidity
File: contracts/L2/Lib1559Math.sol

28         return _ethQty(_gasExcess, _adjustmentFactor) / LibFixedPointMath.SCALING_FACTOR 
29             / _adjustmentFactor;

41         uint256 input = _gasExcess * LibFixedPointMath.SCALING_FACTOR / _adjustmentFactor; 
```
([28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L28-L29), [41](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L41))

```solidity
File: contracts/team/TimelockTokenPool.sol

264         return _amount * uint64(block.timestamp - _start) / _period; 
```
([264](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L264))

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol

117         uint256 timeBasedAllowance = balance 
118             * (block.timestamp.min(claimEnd + withdrawalWindow) - claimEnd) / withdrawalWindow;
```
([117](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L117-L118))

```solidity
File: contracts/thirdparty/optimism/rlp/RLPWriter.sol

39             while (_len / i != 0) { 

47                 out_[i] = bytes1(uint8((_len / (256 ** (lenLen - i))) % 256)); 
```
([39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L39), [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L47))

</details>

### [GAS&#x2011;071] `nonReentrant` modifier in certain functions is redundant
Function not calling any external contract can't be in re-entrancy or function can only be called by `onlyOwner`/`onlyMinter` so no chance to re-enter here.

<details>
<summary><i>There are 5 instances (click to view)</i></summary>

```solidity
File: contracts/L1/provers/Guardians.sol

53     function setGuardians( 
54         address[] memory _newGuardians,
55         uint8 _minGuardians
56     )
57         external
58         onlyOwner
59         nonReentrant
60     {
```
([53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L53-L60))

```solidity
File: contracts/L2/TaikoL2.sol

163     function withdraw( 
164         address _token,
165         address _to
166     )
167         external
168         onlyFromOwnerOrNamed("withdrawer")
169         nonReentrant
170         whenNotPaused
171     {
```
([163](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L163-L171))

```solidity
File: contracts/bridge/Bridge.sol

101     function banAddress( 
102         address _addr,
103         bool _ban
104     )
105         external
106         onlyFromOwnerOrNamed("bridge_watchdog")
107         nonReentrant
108     {
```
([101](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L101-L108))

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol

36     function changeMigrationStatus( 
37         address _migratingAddress,
38         bool _migratingInbound
39     )
40         external
41         nonReentrant
42         whenNotPaused
43         onlyFromOwnerOrNamed("erc20_vault")
44     {
```
([36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L36-L44))

```solidity
File: contracts/tokenvault/ERC20Vault.sol

148     function changeBridgedToken( 
149         CanonicalERC20 calldata _ctoken,
150         address _btokenNew
151     )
152         external
153         nonReentrant
154         whenNotPaused
155         onlyOwner
156         returns (address btokenOld_)
157     {
```
([148](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L148-L157))

</details>

### [GAS&#x2011;072] `uints`/`ints` smaller than `uint256`/`int256` increase gas cost
Citing the [documentation](https://docs.soliditylang.org/en/latest/internals/layout_in_storage.html):

> When using elements that are smaller than 32 bytes, your contract’s gas usage may be higher.This is because the EVM operates on 32 bytes at a time.Therefore, if the element is smaller than that, the EVM must use more operations in order to reduce the size of the element from 32 bytes to the desired size.

For example, each operation involving a `uint8` costs an extra ** 22 - 28 gas ** (depending on whether the other operand is also a variable of type `uint8`) as compared to ones involving`uint256`, due to the compiler having to clear the higher bits of the memory word before operating on the`uint8`, as well as the associated stack operations of doing so.

Consider using a larger size, then downcast where needed.

<details>
<summary><i>There are 40 instances (click to view)</i></summary>

```solidity
File: contracts/L1/ITaikoL1.sol

27     function proveBlock(uint64 _blockId, bytes calldata _input) external; 

31     function verifyBlocks(uint64 _maxBlocksToVerify) external; 
```
([27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/ITaikoL1.sol#L27), [31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/ITaikoL1.sol#L31))

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

20         uint64 expiry; 

22         uint64 maxProposedIn; 

166         uint16 _tierId 
```
([20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L20), [22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L22), [166](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L166))

```solidity
File: contracts/L1/libs/LibDepositing.sol

83             uint96 fee = uint96(_config.ethDepositMaxFee.min(block.basefee * _config.ethDepositGas)); 

85             uint96 totalFee; 
```
([83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L83), [85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L85))

```solidity
File: contracts/L1/libs/LibProposing.sol

34         uint96 livenessBond, 
```
([34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L34))

```solidity
File: contracts/L1/libs/LibProving.sol

36         uint96 validityBond, 

50         uint96 contestBond, 

115         uint64 slot = _meta.id % _config.blockRingBufferSize; 

129         (uint32 tid, TaikoData.TransitionState storage ts) = 

273         uint64 slot 

405         uint32 _tid, 
```
([36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L36), [50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L50), [115](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L115), [129](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L129), [273](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L273), [405](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L405))

```solidity
File: contracts/L1/libs/LibUtils.sol

26         uint64 _blockId, 

38         uint64 slot = _blockId % _config.blockRingBufferSize; 

42         uint32 tid = getTransitionId(_state, blk, slot, _parentHash); 

55         uint64 _blockId 

59         returns (TaikoData.Block storage blk_, uint64 slot_) 

73         uint64 _slot, 

78         returns (uint32 tid_) 
```
([26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L26), [38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L38), [42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L42), [55](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L55), [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L59), [73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L73), [78](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L78))

```solidity
File: contracts/L1/libs/LibVerifying.sol

34         uint16 tier, 

89         uint64 _maxBlocksToVerify 

100         uint64 blockId = b.lastVerifiedBlockId; 

107         uint32 tid = blk.verifiedTransitionId; 

117         uint64 numBlocksVerified; 

213                 uint64 lastVerifiedBlockId = b.lastVerifiedBlockId + numBlocksVerified; 

227         uint64 _lastVerifiedBlockId, 

234         (uint64 lastSyncedBlock,) = signalService.getSyncedChainData( 
```
([34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L34), [89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L89), [100](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L100), [107](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L107), [117](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L117), [213](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L213), [227](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L227), [234](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L234))

```solidity
File: contracts/L1/provers/Guardians.sol

27     uint32 public version; 

37     event GuardiansUpdated(uint32 version, address[] guardians); 
```
([27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L27), [37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L37))

```solidity
File: contracts/common/AddressManager.sol

22         uint64 indexed chainId, bytes32 indexed name, address newAddress, address oldAddress 

39         uint64 _chainId, 

54     function getAddress(uint64 _chainId, bytes32 _name) public view override returns (address) { 
```
([22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L22), [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L39), [54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L54))

```solidity
File: contracts/common/AddressResolver.sol

19     error RESOLVER_ZERO_ADDR(uint64 chainId, bytes32 name); 

44         uint64 _chainId, 

73         uint64 _chainId, 
```
([19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L19), [44](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L44), [73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L73))

```solidity
File: contracts/common/IAddressManager.sol

14     function getAddress(uint64 _chainId, bytes32 _name) external view returns (address); 
```
([14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressManager.sol#L14))

```solidity
File: contracts/common/IAddressResolver.sol

35         uint64 _chainId, 
```
([35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressResolver.sol#L35))

```solidity
File: contracts/libs/Lib4844.sol

13     uint32 public constant FIELD_ELEMENTS_PER_BLOB = 4096; 
```
([13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L13))

</details>

### [GAS&#x2011;073] Use `Array.unsafeAccess()` to avoid repeated array length checks
When using storage arrays, solidity adds an internal lookup of the array's length (a Gcoldsload **2100 gas**) to ensure you don't read past the array's end. You can avoid this lookup by using [`Array.unsafeAccess()`](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/94697be8a3f0dfcd95dfb13ffbd39b5973f5c65d/contracts/utils/Arrays.sol#L57) in cases where the length has already been checked, as is the case with the instances below

<details>
<summary><i>There are 40 instances (click to view)</i></summary>

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

173             if (_tierFees[i].tier == _tierId) return _tierFees[i].fee; 
```
([173](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L173))

```solidity
File: contracts/L1/libs/LibDepositing.sol

88                 deposits_[i] = TaikoData.EthDeposit({ 

93                 uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount; 

101                     deposits_[i].amount -= _fee; 
```
([88](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L88), [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L93), [101](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L101))

```solidity
File: contracts/L1/libs/LibProposing.sol

245                 if (uint160(prevHook) >= uint160(params.hookCalls[i].hook)) { 

253                 IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }( 
254                     blk, meta_, params.hookCalls[i].data

257                 prevHook = params.hookCalls[i].hook; 
```
([245](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L245), [253](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L253-L254), [257](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L257))

```solidity
File: contracts/L1/provers/Guardians.sol

75             delete guardianIds[guardians[i]]; 

81             address guardian = _newGuardians[i]; 

88             guardianIds[guardian] = guardians.length; 
```
([75](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L75), [81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L81), [88](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L88))

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

81             if (_serialNumIsRevoked[index][serialNumBatch[i]]) { 

84             _serialNumIsRevoked[index][serialNumBatch[i]] = true; 

96             if (!_serialNumIsRevoked[index][serialNumBatch[i]]) { 

99             delete _serialNumIsRevoked[index][serialNumBatch[i]]; 

192             EnclaveIdStruct.TcbLevel memory tcb = enclaveId.tcbLevels[i]; 

215             TCBInfoStruct.TCBLevelObj memory current = tcb.tcbLevels[i]; 

265                 issuer = certs[i + 1]; 
```
([81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L81), [84](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L84), [96](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L96), [99](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L99), [192](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L192), [215](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L215), [265](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L265))

```solidity
File: contracts/bridge/Bridge.sol

91             bytes32 msgHash = _msgHashes[i]; 
```
([91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L91))

```solidity
File: contracts/signal/SignalService.sol

105             hop = hopProofs[i]; 
```
([105](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L105))

```solidity
File: contracts/team/airdrop/ERC721Airdrop.sol

60             IERC721(token).safeTransferFrom(vault, user, tokenIds[i]); 
```
([60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L60))

```solidity
File: contracts/thirdparty/optimism/rlp/RLPWriter.sol

67             out_[j] = b[i++]; 
```
([67](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L67))

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

86             TrieNode memory currentNode = proof[i]; 

209             proof_[i] = TrieNode({ encoded: _proof[i], decoded: RLPReader.readList(_proof[i]) }); 
```
([86](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L86), [209](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L209))

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

48             if (_op.amounts[i] == 0) revert VAULT_INVALID_AMOUNT(); 

252                     BridgedERC1155(_op.token).burn(_user, _op.tokenIds[i], _op.amounts[i]); 

273                         id: _op.tokenIds[i], 
```
([48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L48), [252](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L252), [273](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L273))

```solidity
File: contracts/tokenvault/ERC721Vault.sol

171                 IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]); 

176                 BridgedERC721(token_).mint(_to, _tokenIds[i]); 

198                     BridgedERC721(_op.token).burn(_user, _op.tokenIds[i]); 

211                     t.safeTransferFrom(_user, address(this), _op.tokenIds[i]); 
```
([171](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L171), [176](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L176), [198](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L198), [211](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L211))

```solidity
File: contracts/verifiers/SgxVerifier.sol

105             uint256 idx = _ids[i]; 

211             if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED(); 

213             addressRegistered[_instances[i]] = true; 

215             if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE(); 

217             instances[nextInstanceId] = Instance(_instances[i], validSince); 

220             emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince); 
```
([105](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L105), [211](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L211), [213](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L213), [215](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L215), [217](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L217), [220](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220))

</details>

### [GAS&#x2011;074] Use assembly for small `keccak256` hashes, in order to save gas
The assembly version of the keccak256 hashing function can be more gas efficient than the high-level Solidity version.

<details>
<summary><i>There are 23 instances (click to view)</i></summary>

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

146         return keccak256( 
147             abi.encode(
148                 "PROVER_ASSIGNMENT",
149                 ITaikoL1(_taikoL1Address).getConfig().chainId,
150                 _taikoL1Address,
151                 address(this),
152                 _assignment.metaHash,
153                 _assignment.parentMetaHash,
154                 _blobHash,
155                 _assignment.feeToken,
156                 _assignment.expiry,
157                 _assignment.maxBlockId,
158                 _assignment.maxProposedIn,
159                 _assignment.tierFees
160             )
161         );
```
([146](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L146-L161))

```solidity
File: contracts/L1/libs/LibProposing.sol

126                 depositsHash: keccak256(abi.encode(deposits_)), 

213             metaHash: keccak256(abi.encode(meta_)), 
```
([126](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L126), [213](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L213))

```solidity
File: contracts/L1/libs/LibProving.sol

121         if (blk.blockId != _meta.id || blk.metaHash != keccak256(abi.encode(_meta))) { 
```
([121](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L121))

```solidity
File: contracts/L1/provers/GuardianProver.sol

46         bytes32 hash = keccak256(abi.encode(_meta, _tran)); 
```
([46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L46))

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

292             bytes32 issuerPubKeyHash = keccak256(issuer.pubKey); 
```
([292](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L292))

```solidity
File: contracts/automata-attestation/utils/BytesUtils.sol

372         return keccak256(a) == keccak256(b); 
```
([372](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L372))

```solidity
File: contracts/bridge/Bridge.sol

450         return keccak256(abi.encode("TAIKO_MESSAGE", _message)); 
```
([450](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L450))

```solidity
File: contracts/signal/SignalService.sol

186         return keccak256(abi.encode(_chainId, _kind, _blockId)); 

203         return keccak256(abi.encodePacked("SIGNAL", _chainId, _app, _signal)); 
```
([186](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L186), [203](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L203))

```solidity
File: contracts/team/TimelockTokenPool.sol

170         bytes32 hash = keccak256(abi.encodePacked("Withdraw unlocked Taiko token to: ", _to)); 
```
([170](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L170))

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol

68         bytes32 hash = keccak256(abi.encode("CLAIM_TAIKO_AIRDROP", data)); 
```
([68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L68))

```solidity
File: contracts/thirdparty/optimism/Bytes.sol

150         return keccak256(_bytes) == keccak256(_other); 
```
([150](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L150))

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

94                     Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID), 

100                     Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID), 
```
([94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L94), [100](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L100))

```solidity
File: contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol

55         hash_ = abi.encodePacked(keccak256(_key)); 
```
([55](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L55))

```solidity
File: contracts/tokenvault/ERC20Vault.sol

176                     || keccak256(bytes(ctoken.symbol)) != keccak256(bytes(_ctoken.symbol)) 
177                     || keccak256(bytes(ctoken.name)) != keccak256(bytes(_ctoken.name))
```
([176](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L176-L177))

```solidity
File: contracts/verifiers/SgxVerifier.sol

182         return keccak256( 
183             abi.encode(
184                 "VERIFY_PROOF",
185                 ITaikoL1(taikoL1).getConfig().chainId,
186                 address(this),
187                 _tran,
188                 _newInstance,
189                 _prover,
190                 _metaHash
191             )
192         );
```
([182](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L182-L192))

</details>

### [GAS&#x2011;075] Use assembly in place of `abi.decode` to save gas
Instead of using abi.decode, we can use assembly to decode our desired calldata values directly. This will allow us to avoid decoding calldata values that we will not use.

<details>
<summary><i>There are 16 instances (click to view)</i></summary>

```solidity
File: contracts/L1/TaikoL1.sol

88         ) = abi.decode(_input, (TaikoData.BlockMetadata, TaikoData.Transition, TaikoData.TierProof)); 
```
([88](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L88))

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

77         Input memory input = abi.decode(_data, (Input)); 
```
([77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L77))

```solidity
File: contracts/L1/libs/LibProposing.sol

78         TaikoData.BlockParams memory params = abi.decode(_data, (TaikoData.BlockParams)); 
```
([78](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L78))

```solidity
File: contracts/L2/CrossChainOwned.sol

42         (uint64 txId, bytes memory txdata) = abi.decode(_data, (uint64, bytes)); 
```
([42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L42))

```solidity
File: contracts/automata-attestation/utils/SigVerifyLib.sol

140         return abi.decode(ret, (uint256)) == 1; 
```
([140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L140))

```solidity
File: contracts/signal/SignalService.sol

94         HopProof[] memory hopProofs = abi.decode(_proof, (HopProof[])); 
```
([94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L94))

```solidity
File: contracts/team/airdrop/ERC20Airdrop.sol

70             abi.decode(delegationData, (address, uint256, uint256, uint8, bytes32, bytes32)); 
```
([70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L70))

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

100         ) = abi.decode(data, (CanonicalNFT, address, address, uint256[], uint256[])); 

140         (bytes memory data) = abi.decode(message.data[4:], (bytes)); 

142             abi.decode(data, (CanonicalNFT, address, address, uint256[], uint256[])); 
```
([100](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L100), [140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L140), [142](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L142))

```solidity
File: contracts/tokenvault/ERC20Vault.sol

260             abi.decode(_data, (CanonicalERC20, address, address, uint256)); 

298         (bytes memory data) = abi.decode(_message.data[4:], (bytes)); 

300             abi.decode(data, (CanonicalERC20, address, address, uint256)); 
```
([260](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L260), [298](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L298), [300](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L300))

```solidity
File: contracts/tokenvault/ERC721Vault.sol

84             abi.decode(_data, (CanonicalNFT, address, address, uint256[])); 

123         (bytes memory data) = abi.decode(_message.data[4:], (bytes)); 

125             abi.decode(data, (CanonicalNFT, address, address, uint256[])); 
```
([84](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L84), [123](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L123), [125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L125))

</details>

### [GAS&#x2011;076] Use assembly scratch space to build calldata for event emits
Utilizing Solidity's assembly scratch space to build calldata for emitting events with just one or two arguments can optimize gas usage. The scratch space, a designated area in the first 64 bytes of memory, is ideal for temporary storage during assembly-level operations. By directly writing the event arguments into this area, developers can bypass the standard memory allocation process required for event emission. This approach results in gas savings, particularly for contracts where events are frequently emitted. However, such low-level optimization requires a deep understanding of Ethereum Virtual Machine (EVM) mechanics and careful coding to prevent data mishandling. Rigorous testing is essential to ensure the integrity and correct functionality of the contract.

<details>
<summary><i>There are 23 instances (click to view)</i></summary>

```solidity
File: contracts/L1/libs/LibDepositing.sol

50         emit EthDeposited( 
51             TaikoData.EthDeposit({
52                 recipient: recipient_,
53                 amount: uint96(msg.value),
54                 id: _state.slotA.numEthDeposits
55             })
56         );
```
([50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L50-L56))

```solidity
File: contracts/L1/libs/LibProposing.sol

166                     emit BlobCached(meta_.blobHash); 
```
([166](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L166))

```solidity
File: contracts/L1/libs/LibProving.sol

80         emit ProvingPaused(_pause); 
```
([80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L80))

```solidity
File: contracts/L1/provers/Guardians.sol

95         emit GuardiansUpdated(version, _newGuardians); 
```
([95](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L95))

```solidity
File: contracts/L2/CrossChainOwned.sol

53         emit TransactionExecuted(nextTxId++, bytes4(txdata)); 
```
([53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L53))

```solidity
File: contracts/L2/TaikoL2.sol

157         emit Anchored(blockhash(parentId), gasExcess); 
```
([157](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L157))

```solidity
File: contracts/L2/TaikoL2EIP1559Configurable.sol

39         emit ConfigAndExcessChanged(_newConfig, _newGasExcess); 
```
([39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L39))

```solidity
File: contracts/bridge/Bridge.sol

93             emit MessageSuspended(msgHash, _suspend); 

111         emit AddressBanned(_addr, _ban); 

151         emit MessageSent(msgHash_, message_); 

208             emit MessageRecalled(msgHash); 

301             emit MessageExecuted(msgHash); 

336         emit MessageRetried(msgHash); 

519         emit MessageStatusChanged(_msgHash, _status); 
```
([93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L93), [111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L111), [151](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L151), [208](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L208), [301](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L301), [336](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L336), [519](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L519))

```solidity
File: contracts/common/EssentialContract.sol

71         emit Paused(msg.sender); 

80         emit Unpaused(msg.sender); 
```
([71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L71), [80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L80))

```solidity
File: contracts/signal/SignalService.sol

59         emit Authorized(_addr, _authorize); 
```
([59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L59))

```solidity
File: contracts/team/TimelockTokenPool.sol

143         emit Granted(_recipient, _grant); 

157         emit Voided(_recipient, amountVoided); 
```
([143](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L143), [157](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L157))

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol

93         emit Withdrawn(user, amount); 
```
([93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L93))

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol

74         emit Claimed(hash); 
```
([74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L74))

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol

51         emit MigrationStatusChanged(_migratingAddress, _migratingInbound); 
```
([51](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L51))

```solidity
File: contracts/verifiers/SgxVerifier.sol

109             emit InstanceDeleted(idx, instances[idx].addr); 
```
([109](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L109))

</details>

### [GAS&#x2011;077] Use assembly scratch space to build calldata for external calls
Using Solidity's assembly scratch space for constructing calldata in external calls with one or two arguments can be a gas-efficient approach. This method leverages the designated memory area (the first 64 bytes of memory) for temporary data storage during assembly operations. By directly writing arguments into this scratch space, it eliminates the need for additional memory allocation typically required for calldata preparation. This technique can lead to notable gas savings, especially in high-frequency or gas-sensitive operations. However, it requires careful implementation to avoid data corruption and should be used with a thorough understanding of low-level EVM operations and memory handling. Proper testing and validation are crucial when employing such optimizations.

<details>
<summary><i>There are 40 instances (click to view)</i></summary>

```solidity
File: contracts/L1/libs/LibDepositing.sol

41         _resolver.resolve("bridge", false).sendEther(msg.value); 
```
([41](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L41))

```solidity
File: contracts/L1/libs/LibProposing.sol

207         meta_.minTier = ITierProvider(_resolver.resolve("tier_provider", false)).getMinTier( 

237             IERC20 tko = IERC20(_resolver.resolve("taiko_token", false)); 
238             uint256 tkoBalance = tko.balanceOf(address(this));

268             if (tko.balanceOf(address(this)) != tkoBalance + _config.livenessBond) { 

309             address proposerOne = _resolver.resolve("proposer_one", true); 

315         address proposer = _resolver.resolve("proposer", true); 
```
([207](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L207), [237](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L237-L238), [268](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L268), [309](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L309), [315](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L315))

```solidity
File: contracts/L1/libs/LibProving.sol

141             ITierProvider(_resolver.resolve("tier_provider", false)).getTier(_proof.tier); 

161             address verifier = _resolver.resolve(tier.verifierName, true); 

187         IERC20 tko = IERC20(_resolver.resolve("taiko_token", false)); 

196                 tko.transfer(blk.assignedProver, blk.livenessBond); 

367                 _tko.transfer(_ts.prover, _ts.validityBond + reward); 

371                 _tko.transfer(_ts.contester, _ts.contestBond + reward); 

382                 _tko.transfer(msg.sender, reward - _tier.validityBond); 
```
([141](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L141), [161](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L161), [187](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L187), [196](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L196), [367](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L367), [371](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L371), [382](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L382))

```solidity
File: contracts/L1/libs/LibVerifying.sol

149                         tierProvider = _resolver.resolve("tier_provider", false); 

152                         uint256(ITierProvider(tierProvider).getTier(ts.tier).cooldownWindow) * 60 

188                 IERC20 tko = IERC20(_resolver.resolve("taiko_token", false)); 
189                 tko.transfer(ts.prover, bondToReturn);

232         ISignalService signalService = ISignalService(_resolver.resolve("signal_service", false)); 
```
([149](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L149), [152](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L152), [188](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L188-L189), [232](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L232))

```solidity
File: contracts/L1/provers/GuardianProver.sol

51             ITaikoL1(resolve("taiko", false)).proveBlock(_meta.id, abi.encode(_meta, _tran, _proof)); 
```
([51](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L51))

```solidity
File: contracts/L2/TaikoL2.sol

176             IERC20(_token).safeTransfer(_to, IERC20(_token).balanceOf(address(this))); 
```
([176](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L176))

```solidity
File: contracts/bridge/Bridge.sol

150         ISignalService(resolve("signal_service", false)).sendSignal(msgHash_); 

174             if (!ISignalService(signalService).isSignalSent(address(this), msgHash)) { 

199                 IRecallableSender(_message.from).onMessageRecalled{ value: _message.value }( 

342         return ISignalService(resolve("signal_service", false)).isSignalSent({ 

522             ISignalService(resolve("signal_service", false)).sendSignal( 
```
([150](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L150), [174](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L174), [199](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L199), [342](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L342), [522](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L522))

```solidity
File: contracts/common/AddressResolver.sol

83         addr_ = payable(IAddressManager(addressManager).getAddress(_chainId, _name)); 
```
([83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L83))

```solidity
File: contracts/libs/LibAddress.sol

56         try IERC165(_addr).supportsInterface(_interfaceId) returns (bool _result) { 

71             return IERC1271(_addr).isValidSignature(_hash, _sig) == _EIP1271_MAGICVALUE; 
```
([56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L56), [71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L71))

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol

82             IBridgedERC20(migratingAddress).mint(_account, _amount); 
```
([82](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L82))

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

77             IBridge(resolve("bridge", false)).sendMessage{ value: msg.value }(message); 

281             this.onMessageInvocation, abi.encode(ctoken_, _user, _op.to, _op.tokenIds, _op.amounts) 
```
([77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L77), [281](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L281))

```solidity
File: contracts/tokenvault/ERC20Vault.sol

184             IBridgedERC20(btokenOld_).changeMigrationStatus(_btokenNew, false); 
185             IBridgedERC20(_btokenNew).changeMigrationStatus(btokenOld_, true);

239             IBridge(resolve("bridge", false)).sendMessage{ value: msg.value }(message); 

384             this.onMessageInvocation, abi.encode(ctoken_, _user, _to, balanceChange_) 
```
([184](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L184-L185), [239](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L239), [384](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L384))

```solidity
File: contracts/tokenvault/adapters/USDCAdapter.sol

44         usdc.mint(_account, _amount); 

49         usdc.burn(_amount); 
```
([44](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L44), [49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L49))

</details>

### [GAS&#x2011;078] Use assembly to perform efficient back-to-back calls
We can potentially avoid memory expansion costs by using assembly to utilize scratch space + free memory pointer memory offsets for the function calls. We will use the same memory space for both function calls.


<i>There are 2 instaces of this issue:</i>

```solidity
File: contracts/bridge/Bridge.sol

295                 refundTo.sendEther(_message.fee + refundAmount); 

299                 refundTo.sendEther(refundAmount); 
```
([295](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L295), [299](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L299))

### [GAS&#x2011;079] `msg.sender` checks can be optimized with assembly
We can use assembly to efficiently validate msg.sender with the least amount of opcodes necessary. For more details check the following report [Here](https://code4rena.com/reports/2023-05-juicebox#g-06-use-assembly-to-validate-msgsender)

<details>
<summary><i>There are 12 instances (click to view)</i></summary>

```solidity
File: contracts/L1/libs/LibProposing.sol

310             if (proposerOne != address(0) && msg.sender != proposerOne) { 
```
([310](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L310))

```solidity
File: contracts/L2/TaikoL2.sol

123         if (msg.sender != GOLDEN_TOUCH_ADDRESS) revert L2_INVALID_SENDER(); 
```
([123](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L123))

```solidity
File: contracts/bridge/Bridge.sol

250         if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) { 

260             if (_message.gasLimit == 0 && msg.sender != _message.destOwner) { 

294             if (msg.sender == refundTo) { 

322             if (msg.sender != _message.destOwner) revert B_PERMISSION_DENIED(); 
```
([250](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L250), [260](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L260), [294](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L294), [322](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L322))

```solidity
File: contracts/signal/SignalService.sol

77         if (!isAuthorized[msg.sender]) revert SS_UNAUTHORIZED(); 
```
([77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L77))

```solidity
File: contracts/tokenvault/BaseVault.sol

65         if (ctx_.from != msg.sender) revert VAULT_PERMISSION_DENIED(); 
```
([65](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L65))

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol

61         if (msg.sender == migratingAddress) { 

64         } else if (msg.sender != resolve("erc20_vault", true)) { 

78             if (msg.sender != _account) revert BB_PERMISSION_DENIED(); 

83         } else if (msg.sender != resolve("erc20_vault", true)) { 
```
([61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L61), [64](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L64), [78](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L78), [83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L83))

</details>

### [GAS&#x2011;080] Use `assembly` to write address/contract storage values
Using `assembly { sstore(state.slot, addr) }` instead of `state = addr` can save gas.

<details>
<summary><i>There are 40 instances (click to view)</i></summary>

```solidity
File: contracts/L1/libs/LibProposing.sol

86             params.coinbase = msg.sender; 

257                 prevHook = params.hookCalls[i].hook; 
```
([86](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L86), [257](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L257))

```solidity
File: contracts/L1/libs/LibProving.sol

226                 ts.prover = msg.sender; 

251                 ts.contester = msg.sender; 

303             ts_.contester = address(0); 

327                 ts_.prover = _blk.assignedProver; 

332                 ts_.prover = address(0); 

390         _ts.contester = address(0); 
391         _ts.prover = msg.sender;
```
([226](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L226), [251](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L251), [303](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L303), [327](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L327), [332](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L332), [390](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L390-L391))

```solidity
File: contracts/L1/libs/LibVerifying.sol

70         ts.prover = address(0); 

149                         tierProvider = _resolver.resolve("tier_provider", false); 
```
([70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L70), [149](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L149))

```solidity
File: contracts/bridge/Bridge.sol

145         message_.from = msg.sender; 

397         destBridge_ = resolve(_chainId, "bridge", true); 
```
([145](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L145), [397](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L397))

```solidity
File: contracts/common/AddressManager.sol

49         __addresses[_chainId][_name] = _newAddress; 
```
([49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L49))

```solidity
File: contracts/common/AddressResolver.sol

62         addressManager = _addressManager; 
```
([62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L62))

```solidity
File: contracts/signal/SignalService.sol

112                 signalService = address(this); 

117                 signalService = resolve(hop.chainId, "signal_service", false); 

128             app = signalService; 
```
([112](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L112), [117](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L117), [128](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L128))

```solidity
File: contracts/tokenvault/BridgedERC1155.sol

56         srcToken = _srcToken; 
```
([56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L56))

```solidity
File: contracts/tokenvault/BridgedERC20.sol

73         srcToken = _srcToken; 

81         snapshooter = _snapshooter; 
```
([73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L73), [81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L81))

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol

49         migratingAddress = _migratingAddress; 
```
([49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L49))

```solidity
File: contracts/tokenvault/BridgedERC721.sol

47         srcToken = _srcToken; 
```
([47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L47))

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

225             token = ctoken.addr; 

229             token = _getOrDeployBridgedToken(ctoken); 

292         btoken_ = canonicalToBridged[_ctoken.chainId][_ctoken.addr]; 

294             btoken_ = _deployBridgedToken(_ctoken); 

309         btoken_ = address(new ERC1967Proxy(resolve("bridged_erc1155", false), data)); 

312         canonicalToBridged[_ctoken.chainId][_ctoken.addr] = btoken_; 
```
([225](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L225), [229](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L229), [292](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L292), [294](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L294), [309](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L309), [312](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L312))

```solidity
File: contracts/tokenvault/ERC20Vault.sol

168         btokenOld_ = canonicalToBridged[_ctoken.chainId][_ctoken.addr]; 

189         canonicalToBridged[_ctoken.chainId][_ctoken.addr] = _btokenNew; 

329             token_ = _ctoken.addr; 

332             token_ = _getOrDeployBridgedToken(_ctoken); 

395         btoken = canonicalToBridged[ctoken.chainId][ctoken.addr]; 

398             btoken = _deployBridgedToken(ctoken); 

421         btoken = address(new ERC1967Proxy(resolve("bridged_erc20", false), data)); 

423         canonicalToBridged[ctoken.chainId][ctoken.addr] = btoken; 
```
([168](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L168), [189](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L189), [329](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L329), [332](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L332), [395](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L395), [398](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L398), [421](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L421), [423](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L423))

```solidity
File: contracts/tokenvault/ERC721Vault.sol

228         btoken_ = canonicalToBridged[_ctoken.chainId][_ctoken.addr]; 

246         btoken_ = address(new ERC1967Proxy(resolve("bridged_erc721", false), data)); 
```
([228](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L228), [246](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L246))

```solidity
File: contracts/tokenvault/adapters/USDCAdapter.sol

40         usdc = _usdc; 
```
([40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L40))

</details>

### [GAS&#x2011;081] Using `calldata` instead of `memory` for read-only arguments in `external` functions saves gas
When a function with a `memory` array is called externally, the `abi.decode()` step has to copy read each index of the `calldata` to `memory`. **Each copy costs at least 60 gas** (i.e. `60 * <mem_array>.length`). Using `calldata` directly, obviates the need for copies of words of the struct/array not being read. Note that even if an interface defines a function as having `memory` arguments, it's still valid for implementation contracts to use `calldata` arguments instead.

If the array is passed to an `internal` function which passes the array to another internal function where the array is modified and therefore `memory` is used in the `external` call, it's still more gass-efficient to use `calldata` when the `external` function uses modifiers, since the modifiers may prevent the internal functions from being called. Structs have the same overhead as an array of length one

<details>
<summary><i>There are 40 instances (click to view)</i></summary>

```solidity
File: contracts/L1/gov/TaikoGovernor.sol

// @audit _targets
// @audit _values
// @audit _calldatas
// @audit _description
48     function propose( 
49         address[] memory _targets,
50         uint256[] memory _values,
51         bytes[] memory _calldatas,
52         string memory _description
53     )
54         public
55         override(IGovernorUpgradeable, GovernorUpgradeable, GovernorCompatibilityBravoUpgradeable)
56         returns (uint256)
57     {

// @audit _targets
// @audit _values
// @audit _signatures
// @audit _calldatas
// @audit _description
69     function propose( 
70         address[] memory _targets,
71         uint256[] memory _values,
72         string[] memory _signatures,
73         bytes[] memory _calldatas,
74         string memory _description
75     )
76         public
77         virtual
78         override(GovernorCompatibilityBravoUpgradeable)
79         returns (uint256)
80     {
```
([48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L48-L57), [69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L69-L80))

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

// @audit _blk
// @audit _meta
// @audit _data
62     function onBlockProposed( 
63         TaikoData.Block memory _blk,
64         TaikoData.BlockMetadata memory _meta,
65         bytes memory _data
66     )
67         external
68         payable
69         nonReentrant
70         onlyFromNamed("taiko")
71     {

// @audit _assignment
137     function hashAssignment( 
138         ProverAssignment memory _assignment,
139         address _taikoL1Address,
140         bytes32 _blobHash
141     )
142         public
143         view
144         returns (bytes32)
145     {
```
([62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L62-L71), [137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L137-L145))

```solidity
File: contracts/L1/hooks/IHook.sol

// @audit _blk
// @audit _meta
// @audit _data
13     function onBlockProposed( 
```
([13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/IHook.sol#L13))

```solidity
File: contracts/L1/libs/LibUtils.sol

// @audit _config
23     function getTransition( 
24         TaikoData.State storage _state,
25         TaikoData.Config memory _config,
26         uint64 _blockId,
27         bytes32 _parentHash
28     )
29         external
30         view
31         returns (TaikoData.TransitionState storage)
32     {

// @audit _config
52     function getBlock( 
53         TaikoData.State storage _state,
54         TaikoData.Config memory _config,
55         uint64 _blockId
56     )
57         external
58         view
59         returns (TaikoData.Block storage blk_, uint64 slot_)
60     {
```
([23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L23-L32), [52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L52-L60))

```solidity
File: contracts/L1/libs/LibVerifying.sol

// @audit _config
47     function init( 
48         TaikoData.State storage _state,
49         TaikoData.Config memory _config,
50         bytes32 _genesisBlockHash
51     )
52         external
53     {
```
([47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L47-L53))

```solidity
File: contracts/L1/provers/Guardians.sol

// @audit _newGuardians
53     function setGuardians( 
54         address[] memory _newGuardians,
55         uint8 _minGuardians
56     )
57         external
58         onlyOwner
59         nonReentrant
60     {
```
([53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L53-L60))

```solidity
File: contracts/L2/TaikoL2EIP1559Configurable.sol

// @audit _newConfig
25     function setConfigAndExcess( 
26         Config memory _newConfig,
27         uint64 _newGasExcess
28     )
29         external
30         virtual
31         onlyOwner
32     {
```
([25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L25-L32))

```solidity
File: contracts/automata-attestation/interfaces/ISigVerifyLib.sol

// @audit tbs
// @audit signature
// @audit publicKey
38     function verifyAttStmtSignature( 

// @audit tbs
48     function verifyCertificateSignature( 
```
([38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L38), [48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L48))

```solidity
File: contracts/bridge/Bridge.sol

// @audit _message
449     function hashMessage(Message memory _message) public pure returns (bytes32) { 
```
([449](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L449))

```solidity
File: contracts/bridge/IBridge.sol

// @audit _message
155     function hashMessage(Message memory _message) external pure returns (bytes32); 
```
([155](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L155))

```solidity
File: contracts/team/TimelockTokenPool.sol

// @audit _grant
135     function grant(address _recipient, Grant memory _grant) external onlyOwner { 

// @audit _sig
168     function withdraw(address _to, bytes memory _sig) external { 
```
([135](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L135), [168](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L168))

```solidity
File: contracts/tokenvault/BridgedERC1155.sol

// @audit _symbol
// @audit _name
38     function init( 
39         address _owner,
40         address _addressManager,
41         address _srcToken,
42         uint256 _srcChainId,
43         string memory _symbol,
44         string memory _name
45     )
46         external
47         initializer
48     {

// @audit _tokenIds
// @audit _amounts
83     function mintBatch( 
84         address _to,
85         uint256[] memory _tokenIds,
86         uint256[] memory _amounts
87     )
88         public
89         nonReentrant
90         whenNotPaused
91         onlyFromNamed("erc1155_vault")
92     {
```
([38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L38-L48), [83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L83-L92))

```solidity
File: contracts/tokenvault/BridgedERC20.sol

// @audit _symbol
// @audit _name
52     function init( 
53         address _owner,
54         address _addressManager,
55         address _srcToken,
56         uint256 _srcChainId,
57         uint8 _decimals,
58         string memory _symbol,
59         string memory _name
60     )
61         external
62         initializer
63     {
```
([52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L52-L63))

```solidity
File: contracts/tokenvault/BridgedERC721.sol

// @audit _symbol
// @audit _name
31     function init( 
32         address _owner,
33         address _addressManager,
34         address _srcToken,
35         uint256 _srcChainId,
36         string memory _symbol,
37         string memory _name
38     )
39         external
40         initializer
41     {
```
([31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L31-L41))

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

// @audit _op
39     function sendToken(BridgeTransferOp memory _op) 
40         external
41         payable
42         nonReentrant
43         whenNotPaused
44         withValidOperation(_op)
45         returns (IBridge.Message memory message_)
46     {
```
([39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L39-L46))

```solidity
File: contracts/tokenvault/ERC721Vault.sol

// @audit _op
26     function sendToken(BridgeTransferOp memory _op) 
27         external
28         payable
29         nonReentrant
30         whenNotPaused
31         withValidOperation(_op)
32         returns (IBridge.Message memory message_)
33     {
```
([26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L26-L33))

```solidity
File: contracts/verifiers/SgxVerifier.sol

// @audit _tran
171     function getSignedHash( 
172         TaikoData.Transition memory _tran,
173         address _newInstance,
174         address _prover,
175         bytes32 _metaHash
176     )
177         public
178         view
179         returns (bytes32)
180     {
```
([171](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L171-L180))

</details>

### [GAS&#x2011;082] Using hardcoded constants instead of `type(uint).max` is cheaper
<details>
<summary><i>There are 10 instances (click to view)</i></summary>

```solidity
File: contracts/L1/libs/LibDepositing.sol

150         if (_amount > type(uint96).max) revert L1_INVALID_ETH_DEPOSIT(); 
```
([150](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L150))

```solidity
File: contracts/L1/libs/LibVerifying.sol

260                 || _config.ethDepositMaxAmount > type(uint96).max || _config.ethDepositGas == 0 

262                 || _config.ethDepositMaxFee > type(uint96).max / _config.ethDepositMaxCountPerBlock 
```
([260](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L260), [262](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L262))

```solidity
File: contracts/L1/provers/Guardians.sol

63         if (_newGuardians.length < MIN_NUM_GUARDIANS || _newGuardians.length > type(uint8).max) { 
```
([63](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L63))

```solidity
File: contracts/L2/TaikoL2.sol

82         if (block.chainid <= 1 || block.chainid > type(uint64).max) { 

284             gasExcess_ = uint64(excess.min(type(uint64).max)); 
```
([82](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L82), [284](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L284))

```solidity
File: contracts/automata-attestation/utils/BytesUtils.sol

91                     mask = type(uint256).max; // aka 0xffffff.... 
```
([91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L91))

```solidity
File: contracts/bridge/Bridge.sol

27     uint256 internal constant PLACEHOLDER = type(uint256).max; 

89         uint64 _timestamp = _suspend ? type(uint64).max : uint64(block.timestamp); 
```
([27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L27), [89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L89))

```solidity
File: contracts/common/AddressResolver.sol

59         if (block.chainid > type(uint64).max) { 
```
([59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L59))

</details>

### [GAS&#x2011;083] Use custom errors rather than `revert()`/`require()` strings to save gas
[Source](https://blog.soliditylang.org/2021/04/21/custom-errors/)
Instead of using error strings, to reduce deployment and runtime cost, you should use Custom Errors. This would save both deployment and runtime cost.

<details>
<summary><i>There are 40 instances (click to view)</i></summary>

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

61         require(msg.sender == owner, "onlyOwner"); 
```
([61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L61))

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

77         require( 
78             localEnclaveReport.reserved3.length == 96 && localEnclaveReport.reserved4.length == 60
79                 && localEnclaveReport.reportData.length == 64,
80             "local QE report has wrong length"
81         );
82         require(
83             pckSignedQeReport.reserved3.length == 96 && pckSignedQeReport.reserved4.length == 60
84                 && pckSignedQeReport.reportData.length == 64,
85             "QE report has wrong length"
86         );
87         require(
88             v3Quote.v3AuthData.certification.certType == 5,
89             "certType must be 5: Concatenated PCK Cert Chain (PEM formatted)"
90         );
91         require(
92             v3Quote.v3AuthData.certification.decodedCertDataArray.length == 3, "3 certs in chain"
93         );
94         require(
95             v3Quote.v3AuthData.ecdsa256BitSignature.length == 64
96                 && v3Quote.v3AuthData.ecdsaAttestationKey.length == 64
97                 && v3Quote.v3AuthData.qeReportSignature.length == 64,
98             "Invalid ECDSA signature format"
99         );
```
([77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L77-L99))

```solidity
File: contracts/thirdparty/optimism/Bytes.sol

25             require(_length + 31 >= _length, "slice_overflow"); 
26             require(_start + _length >= _start, "slice_overflow");
27             require(_bytes.length >= _start + _length, "slice_outOfBounds");
```
([25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L25-L27))

```solidity
File: contracts/thirdparty/optimism/rlp/RLPReader.sol

37         require( 
38             _in.length > 0,
39             "RLPReader: length of an RLP item must be greater than zero to be decodable"
40         );

56         require( 
57             itemType == RLPItemType.LIST_ITEM,
58             "RLPReader: decoded item type for list is not a list item"
59         );

61         require( 
62             listOffset + listLength == _in.length,
63             "RLPReader: list item has an invalid data remainder"
64         );

112         require( 
113             itemType == RLPItemType.DATA_ITEM,
114             "RLPReader: decoded item type for bytes is not a data item"
115         );

117         require( 
118             _in.length == itemOffset + itemLength,
119             "RLPReader: bytes value contains an invalid remainder"
120         );

152         require( 
153             _in.length > 0,
154             "RLPReader: length of an RLP item must be greater than zero to be decodable"
155         );

172             require( 
173                 _in.length > strLen,
174                 "RLPReader: length of content must be greater than string length (short string)"
175             );

182             require( 
183                 strLen != 1 || firstByteOfContent >= 0x80,
184                 "RLPReader: invalid prefix, single byte < 0x80 are not prefixed (short string)"
185             );

192             require( 
193                 _in.length > lenOfStrLen,
194                 "RLPReader: length of content must be > than length of string length (long string)"
195             );

202             require( 
203                 firstByteOfContent != 0x00,
204                 "RLPReader: length of content must not have any leading zeros (long string)"
205             );

212             require( 
213                 strLen > 55,
214                 "RLPReader: length of content must be greater than 55 bytes (long string)"
215             );

217             require( 
218                 _in.length > lenOfStrLen + strLen,
219                 "RLPReader: length of content must be greater than total length (long string)"
220             );

228             require( 
229                 _in.length > listLen,
230                 "RLPReader: length of content must be greater than list length (short list)"
231             );

238             require( 
239                 _in.length > lenOfListLen,
240                 "RLPReader: length of content must be > than length of list length (long list)"
241             );

248             require( 
249                 firstByteOfContent != 0x00,
250                 "RLPReader: length of content must not have any leading zeros (long list)"
251             );

258             require( 
259                 listLen > 55,
260                 "RLPReader: length of content must be greater than 55 bytes (long list)"
261             );

263             require( 
264                 _in.length > lenOfListLen + listLen,
265                 "RLPReader: length of content must be greater than total length (long list)"
266             );
```
([37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L37-L40), [56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L56-L59), [61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L61-L64), [112](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L112-L115), [117](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L117-L120), [152](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L152-L155), [172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L172-L175), [182](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L182-L185), [192](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L192-L195), [202](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L202-L205), [212](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L212-L215), [217](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L217-L220), [228](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L228-L231), [238](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L238-L241), [248](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L248-L251), [258](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L258-L261), [263](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L263-L266))

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

77         require(_key.length > 0, "MerkleTrie: empty key"); 

89             require(currentKeyIndex <= key.length, "MerkleTrie: key index exceeds total key length"); 

93                 require( 
94                     Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
95                     "MerkleTrie: invalid root hash"
96                 );

99                 require( 
100                     Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
101                     "MerkleTrie: invalid large internal hash"
102                 );

105                 require( 
106                     Bytes.equal(currentNode.encoded, currentNodeID),
107                     "MerkleTrie: invalid internal node hash"
108                 );

119                     require( 
120                         value_.length > 0,
121                         "MerkleTrie: value length must be greater than zero (branch)"
122                     );

125                     require( 
126                         i == proof.length - 1,
127                         "MerkleTrie: value node must be last node in proof (branch)"
128                     );

150                 require( 
151                     pathRemainder.length == sharedNibbleLength,
152                     "MerkleTrie: path remainder must share all nibbles with key"
153                 );

162                     require( 
163                         keyRemainder.length == sharedNibbleLength,
164                         "MerkleTrie: key remainder must be identical to path remainder"
165                     );

172                     require( 
173                         value_.length > 0,
174                         "MerkleTrie: value length must be greater than zero (leaf)"
175                     );

178                     require( 
179                         i == proof.length - 1,
180                         "MerkleTrie: value node must be last node in proof (leaf)"
181                     );

191                     revert("MerkleTrie: received a node with an unknown prefix"); 

194                 revert("MerkleTrie: received an unparseable node"); 

198         revert("MerkleTrie: ran out of proof elements"); 
```
([77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L77), [89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L89), [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L93-L96), [99](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L99-L102), [105](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L105-L108), [119](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L119-L122), [125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L125-L128), [150](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L150-L153), [162](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L162-L165), [172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L172-L175), [178](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L178-L181), [191](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L191), [194](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L194), [198](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L198))

</details>

### [GAS&#x2011;084] Consider using `if` statements over ternary operators


<details>
<summary><i>There are 14 instances (click to view)</i></summary>

```solidity
File: contracts/L1/libs/LibDepositing.sol

44         address recipient_ = _recipient == address(0) ? msg.sender : _recipient; 

93                 uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount; 
```
([44](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L44), [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L93))

```solidity
File: contracts/L2/TaikoL2.sol

281                 excess = excess > issuance ? excess - issuance : 1; 
```
([281](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L281))

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol

358             uint16 svnValue = svnValueBytes.length < 2 
359                 ? uint16(bytes2(svnValueBytes)) / 256
360                 : uint16(bytes2(svnValueBytes));
```
([358](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L358-L360))

```solidity
File: contracts/bridge/Bridge.sol

89         uint64 _timestamp = _suspend ? type(uint64).max : uint64(block.timestamp); 

280                 uint256 gasLimit = msg.sender == _message.destOwner ? gasleft() : _message.gasLimit; 

290             address refundTo = 
291                 _message.refundTo == address(0) ? _message.destOwner : _message.refundTo;
```
([89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L89), [280](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L280), [290](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L290-L291))

```solidity
File: contracts/signal/SignalService.sol

124             bytes32 kind = isFullProof ? LibSignals.STATE_ROOT : LibSignals.SIGNAL_ROOT; 

167         blockId_ = _blockId != 0 ? _blockId : topBlockId[_chainId][_kind]; 
```
([124](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L124), [167](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L167))

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

221         id_ = _node.length < 32 ? RLPReader.readRawBytes(_node) : RLPReader.readBytes(_node); 

243         uint256 max = (_a.length < _b.length) ? _a.length : _b.length; 
```
([221](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L221), [243](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L243))

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

58         IBridge.Message memory message = IBridge.Message({ 
59             id: 0, // will receive a new value
60             from: address(0), // will receive a new value
61             srcChainId: 0, // will receive a new value
62             destChainId: _op.destChainId,
63             srcOwner: msg.sender,
64             destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,
65             to: resolve(_op.destChainId, name(), false),
66             refundTo: _op.refundTo,
67             value: msg.value - _op.fee,
68             fee: _op.fee,
69             gasLimit: _op.gasLimit,
70             data: data,
71             memo: _op.memo
72         });
```
([58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L58-L72))

```solidity
File: contracts/tokenvault/ERC20Vault.sol

221         IBridge.Message memory message = IBridge.Message({ 
222             id: 0, // will receive a new value
223             from: address(0), // will receive a new value
224             srcChainId: 0, // will receive a new value
225             destChainId: _op.destChainId,
226             srcOwner: msg.sender,
227             destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,
228             to: resolve(_op.destChainId, name(), false),
229             refundTo: _op.refundTo,
230             value: msg.value - _op.fee,
231             fee: _op.fee,
232             gasLimit: _op.gasLimit,
233             data: data,
234             memo: _op.memo
235         });
```
([221](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L221-L235))

```solidity
File: contracts/tokenvault/ERC721Vault.sol

44         IBridge.Message memory message = IBridge.Message({ 
45             id: 0, // will receive a new value
46             from: address(0), // will receive a new value
47             srcChainId: 0, // will receive a new value
48             destChainId: _op.destChainId,
49             srcOwner: msg.sender,
50             destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,
51             to: resolve(_op.destChainId, name(), false),
52             refundTo: _op.refundTo,
53             value: msg.value - _op.fee,
54             fee: _op.fee,
55             gasLimit: _op.gasLimit,
56             data: data,
57             memo: _op.memo
58         });
```
([44](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L44-L58))

</details>

### [GAS&#x2011;085] Use immutable when you have storage variable that is not going to change
<details>
<summary><i>There are 5 instances (click to view)</i></summary>

```solidity
File: contracts/team/TimelockTokenPool.sol

68     uint128 public totalAmountGranted; 

71     uint128 public totalAmountVoided; 

74     uint128 public totalAmountWithdrawn; 

77     uint128 public totalCostPaid; 
```
([68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L68), [71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L71), [74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L74), [77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L77))

```solidity
File: contracts/tokenvault/BridgedERC1155.sol

16     address public srcToken; 
```
([16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L16))

</details>

### [GAS&#x2011;086] Use local variables for emitting
Emitted values should not be read from storage again. Instead, the existing values from memory should be used.

<details>
<summary><i>There are 7 instances (click to view)</i></summary>

```solidity
File: contracts/L1/provers/Guardians.sol

// @audit version
95         emit GuardiansUpdated(version, _newGuardians); 
```
([95](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L95))

```solidity
File: contracts/L2/CrossChainOwned.sol

// @audit nextTxId
53         emit TransactionExecuted(nextTxId++, bytes4(txdata)); 
```
([53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L53))

```solidity
File: contracts/L2/TaikoL2.sol

// @audit gasExcess
157         emit Anchored(blockhash(parentId), gasExcess); 
```
([157](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L157))

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol

// @audit migratingAddress
63             emit MigratedTo(migratingAddress, _account, _amount); 

// @audit migratingAddress
80             emit MigratedTo(migratingAddress, _account, _amount); 
```
([63](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L63), [80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L80))

```solidity
File: contracts/verifiers/SgxVerifier.sol

// @audit instances
109             emit InstanceDeleted(idx, instances[idx].addr); 

// @audit nextInstanceId
220             emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince); 
```
([109](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L109), [220](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220))

</details>

### [GAS&#x2011;087] Consider using modifiers rather than invoking functions to perform checks
In using modifiers, the solidity compiler would inline the operations of the modifier in the called function. Using functions to perform checks would incur two JUMPI instructions, plus the stack setup, which could cost up to 40 gas.

<details>
<summary><i>There are 4 instances (click to view)</i></summary>

```solidity
File: contracts/libs/LibAddress.sol

42     function sendEther(address _to, uint256 _amount) internal { 
43         sendEther(_to, _amount, gasleft());
```
([42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L42-L43))

```solidity
File: contracts/tokenvault/BridgedERC1155.sol

38     function init( 
39         address _owner,
40         address _addressManager,
41         address _srcToken,
42         uint256 _srcChainId,
43         string memory _symbol,
44         string memory _name
45     )
46         external
47         initializer
48     {
49         // Check if provided parameters are valid.
50         // The symbol and the name can be empty for ERC1155 tokens so we use some placeholder data
51         // for them instead.
52         LibBridgedToken.validateInputs(_srcToken, _srcChainId, "foo", "foo");
```
([38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L38-L52))

```solidity
File: contracts/tokenvault/BridgedERC20.sol

52     function init( 
53         address _owner,
54         address _addressManager,
55         address _srcToken,
56         uint256 _srcChainId,
57         uint8 _decimals,
58         string memory _symbol,
59         string memory _name
60     )
61         external
62         initializer
63     {
64         // Check if provided parameters are valid
65         LibBridgedToken.validateInputs(_srcToken, _srcChainId, _symbol, _name);
```
([52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L52-L65))

```solidity
File: contracts/tokenvault/BridgedERC721.sol

31     function init( 
32         address _owner,
33         address _addressManager,
34         address _srcToken,
35         uint256 _srcChainId,
36         string memory _symbol,
37         string memory _name
38     )
39         external
40         initializer
41     {
42         // Check if provided parameters are valid
43         LibBridgedToken.validateInputs(_srcToken, _srcChainId, _symbol, _name);
```
([31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L31-L43))

</details>

### [GAS&#x2011;088] Events should be emitted outside of loops
Emitting an event inside a loop performs a LOG op N times, where N is the loop length. Consider refactoring the code to emit the event only once at the end of loop. **Gas savings should be multiplied by the average loop length.**

<details>
<summary><i>There are 3 instances (click to view)</i></summary>

```solidity
File: contracts/bridge/Bridge.sol

93             emit MessageSuspended(msgHash, _suspend); 
```
([93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L93))

```solidity
File: contracts/verifiers/SgxVerifier.sol

109             emit InstanceDeleted(idx, instances[idx].addr); 

220             emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince); 
```
([109](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L109), [220](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220))

</details>

### [GAS&#x2011;089] Replace `s.x += y` with `s.x = s.x + y` for memory structs
Using the `s.x = s.x + y` instead of `s.x += y` for structs can save **100 gas**. The same applies to `-=`, `*=`, etc.

<details>
<summary><i>There are 6 instances (click to view)</i></summary>

```solidity
File: contracts/L1/libs/LibDepositing.sol

101                     deposits_[i].amount -= _fee; 
```
([101](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L101))

```solidity
File: contracts/L1/libs/LibProving.sol

252                 ts.contestations += 1; 

377             _ts.contestations += 1; 
```
([252](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L252), [377](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L377))

```solidity
File: contracts/team/TimelockTokenPool.sol

213         r.amountWithdrawn += amountToWithdraw; 
214         r.costPaid += costToWithdraw;
```
([213](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L213-L214))

</details>

### [GAS&#x2011;090] Use assembly to emit events, in order to save gas
We can use assembly to emit events efficiently by utilizing `scratch space` and the `free memory pointer`. This will allow us to potentially avoid memory expansion costs.
Note: In order to do this optimization safely, we will need to cache and restore the free memory pointer.

For example, for a generic `emit` event for `eventSentAmountExample`: 
```solidity
// uint256 id, uint256 value, uint256 amount
emit eventSentAmountExample(id, value, amount);
```


<details>
<summary><i>There are 24 instances (click to view)</i></summary>

```solidity
File: contracts/L1/libs/LibDepositing.sol

50         emit EthDeposited( 
```
([50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L50))

```solidity
File: contracts/L1/libs/LibProposing.sol

166                     emit BlobCached(meta_.blobHash); 
```
([166](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L166))

```solidity
File: contracts/L1/libs/LibProving.sol

80         emit ProvingPaused(_pause); 
```
([80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L80))

```solidity
File: contracts/L1/provers/GuardianProver.sol

54         emit GuardianApproval(msg.sender, _meta.id, _tran.blockHash, approved_); 
```
([54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L54))

```solidity
File: contracts/L1/provers/Guardians.sol

95         emit GuardiansUpdated(version, _newGuardians); 
```
([95](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L95))

```solidity
File: contracts/L2/CrossChainOwned.sol

53         emit TransactionExecuted(nextTxId++, bytes4(txdata)); 
```
([53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L53))

```solidity
File: contracts/L2/TaikoL2.sol

157         emit Anchored(blockhash(parentId), gasExcess); 
```
([157](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L157))

```solidity
File: contracts/L2/TaikoL2EIP1559Configurable.sol

39         emit ConfigAndExcessChanged(_newConfig, _newGasExcess); 
```
([39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L39))

```solidity
File: contracts/bridge/Bridge.sol

93             emit MessageSuspended(msgHash, _suspend); 

111         emit AddressBanned(_addr, _ban); 

151         emit MessageSent(msgHash_, message_); 

208             emit MessageRecalled(msgHash); 

301             emit MessageExecuted(msgHash); 

336         emit MessageRetried(msgHash); 

519         emit MessageStatusChanged(_msgHash, _status); 
```
([93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L93), [111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L111), [151](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L151), [208](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L208), [301](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L301), [336](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L336), [519](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L519))

```solidity
File: contracts/common/EssentialContract.sol

71         emit Paused(msg.sender); 

80         emit Unpaused(msg.sender); 
```
([71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L71), [80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L80))

```solidity
File: contracts/signal/SignalService.sol

59         emit Authorized(_addr, _authorize); 
```
([59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L59))

```solidity
File: contracts/team/TimelockTokenPool.sol

143         emit Granted(_recipient, _grant); 

157         emit Voided(_recipient, amountVoided); 
```
([143](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L143), [157](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L157))

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol

93         emit Withdrawn(user, amount); 
```
([93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L93))

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol

74         emit Claimed(hash); 
```
([74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L74))

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol

51         emit MigrationStatusChanged(_migratingAddress, _migratingInbound); 
```
([51](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L51))

```solidity
File: contracts/verifiers/SgxVerifier.sol

109             emit InstanceDeleted(idx, instances[idx].addr); 
```
([109](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L109))

</details>

### [GAS&#x2011;091] Use `selfbalance()` instead of `address(this).balance`
Use assembly when getting a contract's balance of ETH.

You can use `selfbalance()` instead of `address(this).balance` when getting your contract's balance of ETH to save gas.
Additionally, you can use `balance(address)` instead of `address().balance` when getting an external contract's balance of ETH.

*Saves 15 gas when checking internal balance, 6 for external*

<details>
<summary><i>There are 6 instances (click to view)</i></summary>

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

125         if (address(this).balance > 0) { 
126             taikoL1Address.sendEther(address(this).balance);
```
([125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L125-L126))

```solidity
File: contracts/L1/libs/LibProposing.sol

253                 IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }( 

260             if (address(this).balance != 0) { 
261                 msg.sender.sendEther(address(this).balance);
```
([253](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L253), [260](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L260-L261))

```solidity
File: contracts/L2/TaikoL2.sol

174             _to.sendEther(address(this).balance); 
```
([174](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L174))

</details>

### [GAS&#x2011;092] Division by powers of two should use bit shifting
`<x> * 2` is the same as `<x> << 1`. While the compiler uses the `SHL` opcode to accomplish both, the version that uses multiplication incurs an overhead of **20 gas** due to `JUMP`s to and from a compiler utility function that introduces checks which can be avoided by using `unchecked {}` around the division by two.


<i>There are 2 instaces of this issue:</i>

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

158             uint256 acc = lowerDigit * (16 ** (2 * i)); 
159             acc += upperDigit * (16 ** ((2 * i) + 1));
```
([158](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L158-L159))

### [GAS&#x2011;093] Use the inputs/results of assignments rather than re-reading state variables
When a state variable is assigned, it saves gas to use the value being assigned, later in the function, rather than re-reading the state variable itself. If needed, it can also be stored to a local variable, and be used in that way. Both options avoid a Gwarmaccess (**100 gas**). Note that if the operation is, say `+=`, the assignment also results in a value which can be used. The instances below point to the first reference after the assignment, since later references are already covered by issues describing the caching of state variable values.

<details>
<summary><i>There are 10 instances (click to view)</i></summary>

```solidity
File: contracts/bridge/Bridge.sol

// @audit use result of assignment of receivedAt, here
184             proofReceipt[msgHash].receivedAt = receivedAt; 

// @audit use result of assignment of receivedAt, here
189         if (block.timestamp >= invocationDelay + receivedAt) { 

// @audit use result of assignment of receivedAt, here
244                     receivedAt: receivedAt, 

// @audit use result of assignment of receivedAt, here
258         if (block.timestamp >= invocationDelay + receivedAt) { 
```
([184](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L184), [189](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L189), [244](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L244), [258](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L258))

```solidity
File: contracts/team/TimelockTokenPool.sol

// @audit use result of assignment of amountWithdrawn, here
193         amountToWithdraw = amountUnlocked - amountWithdrawn; 
```
([193](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L193))

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

// @audit use result of assignment of token, here
226             IERC1155(token).safeBatchTransferFrom(address(this), to, tokenIds, amounts, ""); 

// @audit use result of assignment of token, here
229             token = _getOrDeployBridgedToken(ctoken); 
// @audit use result of assignment of token, here
230             BridgedERC1155(token).mintBatch(to, tokenIds, amounts);
```
([226](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L226), [229](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L229-L230))

```solidity
File: contracts/verifiers/SgxVerifier.sol

// @audit use result of assignment of validSince, here
217             instances[nextInstanceId] = Instance(_instances[i], validSince); 

// @audit use result of assignment of validSince, here
220             emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince); 
```
([217](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L217), [220](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220))

</details>

### [GAS&#x2011;094] Optimize Boolean States with `uint256(1/2)`
Use uint256(1) and uint256(2) for true/false to avoid a Gwarmaccess (100 gas), and to avoid Gsset (20000 gas) when changing from ‘false’ to ‘true’, after having been ‘true’ in the past. Refer to the [source](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/5ae630684a0f57de400ef69499addab4c32ac8fb/contracts/security/ReentrancyGuard.sol#L23-L27).

<details>
<summary><i>There are 10 instances (click to view)</i></summary>

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

38     bool private _checkLocalEnclaveReport; 
39     mapping(bytes32 enclave => bool trusted) private _trustedUserMrEnclave;
40     mapping(bytes32 signer => bool trusted) private _trustedUserMrSigner;

47     mapping(uint256 idx => mapping(bytes serialNum => bool revoked)) private _serialNumIsRevoked; 
```
([38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L38-L40), [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L47))

```solidity
File: contracts/bridge/Bridge.sol

42     mapping(address addr => bool banned) public addressBanned; 
```
([42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L42))

```solidity
File: contracts/signal/SignalService.sol

21     mapping(address addr => bool authorized) public isAuthorized; 
```
([21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L21))

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol

12     mapping(bytes32 hash => bool claimed) public isClaimed; 
```
([12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L12))

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol

14     bool public migratingInbound; 
```
([14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L14))

```solidity
File: contracts/tokenvault/ERC20Vault.sol

52     mapping(address btoken => bool blacklisted) public btokenBlacklist; 
```
([52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L52))

```solidity
File: contracts/verifiers/SgxVerifier.sol

55     mapping(address instanceAddress => bool alreadyAttested) public addressRegistered; 
```
([55](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L55))

</details>

### [GAS&#x2011;095] Using `> 0` costs more gas than `!= 0` when used on a `uint` in a `require()` statement
This change saves **[6 gas](https://aws1.discourse-cdn.com/business6/uploads/zeppelin/original/2X/3/363a367d6d68851f27d2679d10706cd16d788b96.png)** per instance. The optimization works until solidity version [0.8.13](https://gist.github.com/IllIllI000/bf2c3120f24a69e489f12b3213c06c94) where there is a regression in gas costs.

<details>
<summary><i>There are 5 instances (click to view)</i></summary>

```solidity
File: contracts/thirdparty/optimism/rlp/RLPReader.sol

// @audit _in.length != 0
38             _in.length > 0, 

// @audit _in.length != 0
153             _in.length > 0, 
```
([38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L38), [153](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L153))

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

// @audit _key.length != 0
77         require(_key.length > 0, "MerkleTrie: empty key"); 

// @audit value_.length != 0
120                         value_.length > 0, 

// @audit value_.length != 0
173                         value_.length > 0, 
```
([77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L77), [120](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L120), [173](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L173))

</details>

### [GAS&#x2011;096] Using bools for storage incurs overhead
Use uint256(1) and uint256(2) for true/false to avoid a Gwarmaccess (100 gas), and to avoid Gsset (20000 gas) when changing from ‘false’ to ‘true’, after having been ‘true’ in the past. See [source](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/58f635312aa21f947cae5f8578638a85aa2519f5/contracts/security/ReentrancyGuard.sol#L23-L27).

<details>
<summary><i>There are 24 instances (click to view)</i></summary>

```solidity
File: contracts/L1/TaikoData.sol

32         bool blobAllowedForDA; 

34         bool blobReuseEnabled; 

85         bool cacheBlobForReuse; 

108         bool blobUsed; 

171         bool provingPaused; 
```
([32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L32), [34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L34), [85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L85), [108](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L108), [171](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L171))

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

38     bool private _checkLocalEnclaveReport; 
```
([38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L38))

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol

35         bool fmspcFound; 
36         bool pceidFound;
37         bool tcbFound;
```
([35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L35-L37))

```solidity
File: contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol

14         bool isPck; 
```
([14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L14))

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol

14     bool public migratingInbound; 
```
([14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L14))

```solidity
File: contracts/verifiers/IVerifier.sol

15         bool isContesting; 
16         bool blobUsed;
```
([15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/IVerifier.sol#L15-L16))

</details>

### [GAS&#x2011;097] Using `constant`s instead of `enum` can save gas
`Enum` is expensive and it is [more efficient to use constants](https://www.codehawks.com/finding/clm84992q02j9w9ruebun36d9) instead. An illustrative example of this approach can be found in the [ReentrancyGuard.sol](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/181d518609a9f006fcb97af63e6952e603cf100e/contracts/utils/ReentrancyGuard.sol#L34-L35).

<details>
<summary><i>There are 9 instances (click to view)</i></summary>

```solidity
File: contracts/automata-attestation/interfaces/ISigVerifyLib.sol

7     enum KeyType { 
8         RSA,
9         ECDSA
10     }

19     enum CertSigAlgorithm { 
20         Sha256WithRSAEncryption,
21         Sha1WithRSAEncryption
22     }

32     enum Algorithm { 
33         RS256,
34         ES256,
35         RS1
36     }
```
([7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L7-L10), [19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L19-L22), [32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L32-L36))

```solidity
File: contracts/automata-attestation/lib/EnclaveIdStruct.sol

26     enum EnclaveIdStatus { 
27         OK,
28         SGX_ENCLAVE_REPORT_ISVSVN_REVOKED
29     }
```
([26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/EnclaveIdStruct.sol#L26-L29))

```solidity
File: contracts/automata-attestation/lib/TCBInfoStruct.sol

19     enum TCBStatus { 
20         OK,
21         TCB_SW_HARDENING_NEEDED,
22         TCB_CONFIGURATION_AND_SW_HARDENING_NEEDED,
23         TCB_CONFIGURATION_NEEDED,
24         TCB_OUT_OF_DATE,
25         TCB_OUT_OF_DATE_CONFIGURATION_NEEDED,
26         TCB_REVOKED,
27         TCB_UNRECOGNIZED
28     }
```
([19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol#L19-L28))

```solidity
File: contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol

31     enum CRL { 
32         PCK,
33         ROOT
34     }
```
([31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L31-L34))

```solidity
File: contracts/bridge/IBridge.sol

9     enum Status { 
10         NEW,
11         RETRIABLE,
12         DONE,
13         FAILED,
14         RECALLED
15     }
```
([9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L9-L15))

```solidity
File: contracts/signal/ISignalService.sol

13     enum CacheOption { 
14         CACHE_NOTHING,
15         CACHE_SIGNAL_ROOT,
16         CACHE_STATE_ROOT,
17         CACHE_BOTH
18     }
```
([13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L13-L18))

```solidity
File: contracts/thirdparty/optimism/rlp/RLPReader.sol

16     enum RLPItemType { 
17         DATA_ITEM,
18         LIST_ITEM
19     }
```
([16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L16-L19))

</details>

### [GAS&#x2011;098] Using globals directly is cheaper than assigning them to variables
Using the [global](https://docs.soliditylang.org/en/v0.8.14/cheatsheet.html#global-variables) directly saves **5 [gas](https://gist.github.com/IllIllI000/0a38d74d0af20412471a43f1e4fcf8be)**


<i>There is one instance of this issue:</i>

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

93         address taikoL1Address = msg.sender; 
```
([93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L93))

### [GAS&#x2011;099] Using `msg` globals directly, rather than caching the value, saves gas
For example, use `msg.sender` directly rather than storing it to a local variable


<i>There are 3 instaces of this issue:</i>

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

// @audit taikoL1Address
94         bytes32 hash = hashAssignment(assignment, taikoL1Address, _meta.blobHash); 

// @audit taikoL1Address
102         tko.transferFrom(_blk.assignedProver, taikoL1Address, _blk.livenessBond); 

// @audit taikoL1Address
126             taikoL1Address.sendEther(address(this).balance); 
```
([94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L94), [102](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L102), [126](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L126))

### [GAS&#x2011;100] Using `private` rather than `public`, saves gas
For constants, the values can be read from the verified contract source code, or if there are multiple values there can be a single getter function that returns a tuple of the values of all currently-public constants. Saves 3406-3606 gas in deployment gas due to the compiler not having to create non-payable getter functions for deployment calldata, not having to store the bytes of the value outside of where it's used, and not adding another entry to the method ID table

<details>
<summary><i>There are 40 instances (click to view)</i></summary>

```solidity
File: contracts/L1/TaikoL1.sol

24     TaikoData.State public state; 
```
([24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L24))

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

38     uint256 public constant MAX_GAS_PAYING_PROVER = 50_000; 
```
([38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L38))

```solidity
File: contracts/L1/libs/LibProposing.sol

21     uint256 public constant MAX_BYTES_PER_BLOB = 4096 * 32; 
```
([21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L21))

```solidity
File: contracts/L1/libs/LibProving.sol

20     bytes32 public constant RETURN_LIVENESS_BOND = keccak256("RETURN_LIVENESS_BOND"); 

23     bytes32 public constant TIER_OP = bytes32("tier_optimistic"); 
```
([20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L20), [23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L23))

```solidity
File: contracts/L1/provers/Guardians.sol

11     uint256 public constant MIN_NUM_GUARDIANS = 5; 

16     mapping(address guardian => uint256 id) public guardianIds; 

23     address[] public guardians; 

27     uint32 public version; 

30     uint32 public minGuardians; 
```
([11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L11), [16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L16), [23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L23), [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L27), [30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L30))

```solidity
File: contracts/L1/tiers/ITierProvider.sol

39     uint16 public constant TIER_OPTIMISTIC = 100; 

42     uint16 public constant TIER_SGX = 200; 

45     uint16 public constant TIER_SGX_ZKVM = 300; 

48     uint16 public constant TIER_GUARDIAN = 1000; 
```
([39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L39), [42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L42), [45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L45), [48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L48))

```solidity
File: contracts/L2/CrossChainOwned.sol

16     uint64 public ownerChainId; 

19     uint64 public nextTxId; 
```
([16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L16), [19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L19))

```solidity
File: contracts/L2/TaikoL2.sol

32     address public constant GOLDEN_TOUCH_ADDRESS = 0x0000777735367b36bC9B61C50022d9D0700dB4Ec; 

35     uint8 public constant BLOCK_SYNC_THRESHOLD = 5; 

39     mapping(uint256 blockId => bytes32 blockHash) public l2Hashes; 

43     bytes32 public publicInputHash; 

47     uint64 public gasExcess; 

50     uint64 public lastSyncedBlock; 
```
([32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L32), [35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L35), [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L39), [43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L43), [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L47), [50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L50))

```solidity
File: contracts/L2/TaikoL2EIP1559Configurable.sol

11     Config public customConfig; 
```
([11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L11))

```solidity
File: contracts/bridge/Bridge.sol

31     uint128 public nextMessageId; 

35     mapping(bytes32 msgHash => Status status) public messageStatus; 

42     mapping(address addr => bool banned) public addressBanned; 

46     mapping(bytes32 msgHash => ProofReceipt receipt) public proofReceipt; 
```
([31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L31), [35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L35), [42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L42), [46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L46))

```solidity
File: contracts/common/AddressResolver.sol

13     address public addressManager; 
```
([13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L13))

```solidity
File: contracts/libs/Lib4844.sol

10     address public constant POINT_EVALUATION_PRECOMPILE_ADDRESS = address(0x0A); 

13     uint32 public constant FIELD_ELEMENTS_PER_BLOB = 4096; 

16     uint256 public constant BLS_MODULUS = 
17         52_435_875_175_126_190_479_447_740_508_185_965_837_690_552_500_527_637_822_603_658_699_938_581_184_513;
```
([10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L10), [13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L13), [16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L16-L17))

```solidity
File: contracts/signal/LibSignals.sol

8     bytes32 public constant STATE_ROOT = keccak256("STATE_ROOT"); 

11     bytes32 public constant SIGNAL_ROOT = keccak256("SIGNAL_ROOT"); 
```
([8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/LibSignals.sol#L8), [11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/LibSignals.sol#L11))

```solidity
File: contracts/signal/SignalService.sol

17     mapping(uint64 chainId => mapping(bytes32 kind => uint64 blockId)) public topBlockId; 

21     mapping(address addr => bool authorized) public isAuthorized; 
```
([17](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L17), [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L21))

```solidity
File: contracts/tokenvault/BridgedERC20.sol

22     address public srcToken; 

27     uint256 public srcChainId; 

30     address public snapshooter; 
```
([22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L22), [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L27), [30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L30))

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol

11     address public migratingAddress; 
```
([11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L11))

```solidity
File: contracts/tokenvault/adapters/USDCAdapter.sol

31     IUSDC public usdc; 
```
([31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L31))

</details>

### [GAS&#x2011;101] Using `storage` instead of `memory` for structs/arrays saves gas
When fetching data from a storage location, assigning the data to a `memory` variable causes all fields of the struct/array to be read from storage, which incurs a Gcoldsload (**2100 gas**) for *each* field of the struct/array. If the fields are read from the new memory variable, they incur an additional `MLOAD` rather than a cheap stack read. Instead of declearing the variable with the `memory` keyword, declaring the variable with the `storage` keyword and caching any fields that need to be re-read in stack variables, will be much cheaper, only incuring the Gcoldsload for the fields actually read. The only time it makes sense to read the whole struct/array into a `memory` variable, is if the full struct/array is being returned by the function, is being passed to a function that requires `memory`, or if the array/struct is being read from another `memory` array/struct

<details>
<summary><i>There are 40 instances (click to view)</i></summary>

```solidity
File: contracts/L1/TaikoL1.sol

65         TaikoData.Config memory config = getConfig(); 

92         TaikoData.Config memory config = getConfig(); 
```
([65](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L65), [92](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L92))

```solidity
File: contracts/L1/gov/TaikoTimelockController.sol

17         address[] memory nil = new address[](0); 
```
([17](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L17))

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

77         Input memory input = abi.decode(_data, (Input)); 
78         ProverAssignment memory assignment = input.assignment;
```
([77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L77-L78))

```solidity
File: contracts/L1/libs/LibProposing.sol

78         TaikoData.BlockParams memory params = abi.decode(_data, (TaikoData.BlockParams)); 

93         TaikoData.SlotB memory b = _state.slotB; 

212         TaikoData.Block memory blk = TaikoData.Block({ 
213             metaHash: keccak256(abi.encode(meta_)),
214             // Safeguard the liveness bond to ensure its preservation,
215             // particularly in scenarios where it might be altered after the
216             // block's proposal but before it has been proven or verified.
217             livenessBond: _config.livenessBond,
218             blockId: b.numBlocks,
219             proposedAt: meta_.timestamp,
220             proposedIn: uint64(block.number),
221             // For a new block, the next transition ID is always 1, not 0.
222             nextTransitionId: 1,
223             // For unverified block, its verifiedTransitionId is always 0.
224             verifiedTransitionId: 0,
225             assignedProver: params.assignedProver
226         });
```
([78](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L78), [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L93), [212](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L212-L226))

```solidity
File: contracts/L1/libs/LibProving.sol

110         TaikoData.SlotB memory b = _state.slotB; 

140         ITierProvider.Tier memory tier = 
141             ITierProvider(_resolver.resolve("tier_provider", false)).getTier(_proof.tier);

166                 IVerifier.Context memory ctx = IVerifier.Context({ 
167                     metaHash: blk.metaHash,
168                     blobHash: _meta.blobHash,
169                     // Separate msgSender to allow the prover to be any address in the future.
170                     prover: msg.sender,
171                     msgSender: msg.sender,
172                     blockId: blk.blockId,
173                     isContesting: isContesting,
174                     blobUsed: _meta.blobUsed
175                 });
```
([110](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L110), [140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L140-L141), [166](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L166-L175))

```solidity
File: contracts/L1/libs/LibUtils.sol

33         TaikoData.SlotB memory b = _state.slotB; 
```
([33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L33))

```solidity
File: contracts/L1/libs/LibVerifying.sol

99         TaikoData.SlotB memory b = _state.slotB; 
```
([99](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L99))

```solidity
File: contracts/L2/CrossChainOwned.sol

45         IBridge.Context memory ctx = IBridge(msg.sender).context(); 
```
([45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L45))

```solidity
File: contracts/L2/TaikoL2.sol

136         Config memory config = getConfig(); 
```
([136](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L136))

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

180         EnclaveIdStruct.EnclaveId memory enclaveId = qeIdentity; 

192             EnclaveIdStruct.TcbLevel memory tcb = enclaveId.tcbLevels[i]; 

215             TCBInfoStruct.TCBLevelObj memory current = tcb.tcbLevels[i]; 

260             IPEMCertChainLib.ECSha256Certificate memory issuer; 

415         IPEMCertChainLib.ECSha256Certificate[] memory parsedQuoteCerts; 
416         TCBInfoStruct.TCBInfo memory fetchedTcbInfo;

442             IPEMCertChainLib.ECSha256Certificate memory pckCert = parsedQuoteCerts[0]; 
```
([180](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L180), [192](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L192), [215](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L215), [260](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L260), [415](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L415-L416), [442](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L442))

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol

198             uint256[] memory cpuSvns; 

241         string[] memory split = LibString.split(contentSlice, string(delimiter)); 

299                 PCKTCBFlags memory flags; 
```
([198](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L198), [241](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L241), [299](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L299))

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

52         V3Struct.EnclaveReport memory localEnclaveReport = parseEnclaveReport(rawLocalEnclaveReport); 
```
([52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L52))

```solidity
File: contracts/libs/LibTrieProof.sol

52             RLPReader.RLPItem[] memory accountState = RLPReader.readList(rlpAccount); 
```
([52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L52))

```solidity
File: contracts/signal/SignalService.sol

94         HopProof[] memory hopProofs = abi.decode(_proof, (HopProof[])); 

103         HopProof memory hop; 
```
([94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L94), [103](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L103))

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

79         TrieNode[] memory proof = _parseProof(_proof); 

86             TrieNode memory currentNode = proof[i]; 

135                     RLPReader.RLPItem memory nextNode = currentNode.decoded[branchKey]; 
```
([79](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L79), [86](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L86), [135](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L135))

```solidity
File: contracts/tokenvault/ERC1155Vault.sol

58         IBridge.Message memory message = IBridge.Message({ 
59             id: 0, // will receive a new value
60             from: address(0), // will receive a new value
61             srcChainId: 0, // will receive a new value
62             destChainId: _op.destChainId,
63             srcOwner: msg.sender,
64             destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,
65             to: resolve(_op.destChainId, name(), false),
66             refundTo: _op.refundTo,
67             value: msg.value - _op.fee,
68             fee: _op.fee,
69             gasLimit: _op.gasLimit,
70             data: data,
71             memo: _op.memo
72         });

104         IBridge.Context memory ctx = checkProcessMessageContext(); 
```
([58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L58-L72), [104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L104))

```solidity
File: contracts/tokenvault/ERC20Vault.sol

171             CanonicalERC20 memory ctoken = bridgedToCanonical[btokenOld_]; 

221         IBridge.Message memory message = IBridge.Message({ 
222             id: 0, // will receive a new value
223             from: address(0), // will receive a new value
224             srcChainId: 0, // will receive a new value
225             destChainId: _op.destChainId,
226             srcOwner: msg.sender,
227             destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,
228             to: resolve(_op.destChainId, name(), false),
229             refundTo: _op.refundTo,
230             value: msg.value - _op.fee,
231             fee: _op.fee,
232             gasLimit: _op.gasLimit,
233             data: data,
234             memo: _op.memo
235         });

263         IBridge.Context memory ctx = checkProcessMessageContext(); 
```
([171](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L171), [221](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L221-L235), [263](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L263))

```solidity
File: contracts/tokenvault/ERC721Vault.sol

44         IBridge.Message memory message = IBridge.Message({ 
45             id: 0, // will receive a new value
46             from: address(0), // will receive a new value
47             srcChainId: 0, // will receive a new value
48             destChainId: _op.destChainId,
49             srcOwner: msg.sender,
50             destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,
51             to: resolve(_op.destChainId, name(), false),
52             refundTo: _op.refundTo,
53             value: msg.value - _op.fee,
54             fee: _op.fee,
55             gasLimit: _op.gasLimit,
56             data: data,
57             memo: _op.memo
58         });

87         IBridge.Context memory ctx = checkProcessMessageContext(); 
```
([44](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L44-L58), [87](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L87))

```solidity
File: contracts/verifiers/SgxVerifier.sol

132         address[] memory _address = new address[](1); 
```
([132](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L132))

</details>

### [GAS&#x2011;102] Using `this` to access functions results in an external call, wasting gas
External calls have an overhead of **100 gas**, which can be avoided by not referencing the function using `this`. Contracts [are allowed](https://docs.soliditylang.org/en/latest/contracts.html#function-overriding) to override their parents' functions and change the visibility from `external` to `public`, so make this change if it's required in order to call the function internally.


<i>There is one instance of this issue:</i>

```solidity
File: contracts/L2/CrossChainOwned.sol

50         (bool success,) = address(this).call(txdata); 
```
([50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L50))

### [GAS&#x2011;103] `<x> += <y>` costs more gas than `<x> = <x> + <y>` for basic-typed state variables
Using the addition operator instead of plus-equals saves **[10 gas](https://gist.github.com/IllIllI000/cbbfb267425b898e5be734d4008d4fe8)** because of extra `PUSH`es and `POP`s associated with the manipulation of the state variable when using `+=` for basic-typed state variables

<details>
<summary><i>There are 5 instances (click to view)</i></summary>

```solidity
File: contracts/team/TimelockTokenPool.sol

141         totalAmountGranted += _grant.amount; 

156         totalAmountVoided += amountVoided; 

216         totalAmountWithdrawn += amountToWithdraw; 
217         totalCostPaid += costToWithdraw;
```
([141](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L141), [156](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L156), [216](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L216-L217))

```solidity
File: contracts/verifiers/SgxVerifier.sol

207             validSince += INSTANCE_VALIDITY_DELAY; 
```
([207](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L207))

</details>
