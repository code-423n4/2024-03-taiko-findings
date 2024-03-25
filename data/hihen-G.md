# Gas Report

Issues in [4naly3er-report](https://github.com/code-423n4/2024-03-taiko/blob/main/4naly3er-report.md) have been excluded.

## Summary

Total **1580 instances** over **68 issues**with **1637624** gas saved:

|ID|Issue|Instances|Gas|
|:--:|:---|:--:|:--:|
| [[G-01]](#g-01-use-storage-instead-of-memory-for-structsarrays) | Use `storage` instead of `memory` for structs/arrays | 6 | 25200 |
| [[G-02]](#g-02-constructors-can-be-marked-as-payable-to-save-deployment-gas) | Constructors can be marked as payable to save deployment gas | 3 | 63 |
| [[G-03]](#g-03-state-variables-only-set-in-the-constructor-should-be-declared-immutable) | State variables only set in the constructor should be declared `immutable` | 2 | 4194 |
| [[G-04]](#g-04-unnecessary-event-parameters-should-be-removed) | Unnecessary event parameters should be removed | 1 | 358 |
| [[G-05]](#g-05-abiencode-is-less-efficient-than-abiencodepacked-for-non-address-arguments) | `abi.encode()` is less efficient than `abi.encodePacked()` for non-address arguments | 4 | - |
| [[G-06]](#g-06-counting-down-in-for-statements-is-more-gas-efficient) | Counting down in for statements is more gas efficient | 45 | - |
| [[G-07]](#g-07-using-msg-globals-directly-rather-than-caching-the-value-saves-gas) | Using `msg` globals directly, rather than caching the value, saves gas | 1 | 10 |
| [[G-08]](#g-08-stack-variable-is-only-used-once) | Stack variable is only used once | 70 | 210 |
| [[G-09]](#g-09-do-not-cache-state-variables-that-are-used-only-once) | Do not cache state variables that are used only once | 3 | 9 |
| [[G-10]](#g-10-do-not-calculate-constants) | Do not calculate constants | 2 | - |
| [[G-11]](#g-11-use-of-emit-inside-a-loop) | Use of `emit` inside a loop | 4 | 1500 |
| [[G-12]](#g-12-emitting-literals-or-constants-wastes-gas) | Emitting literals or constants wastes gas | 5 | 40 |
| [[G-13]](#g-13-use-local-variables-for-emitting) | Use local variables for emitting | 7 | 700 |
| [[G-14]](#g-14-contract-storage-can-use-fewer-slots-by-changing-the-order-of-state-variables) | Contract storage can use fewer slots by changing the order of state variables | 2 | 40000 |
| [[G-15]](#g-15-structs-can-use-fewer-slots-by-changing-the-order-of-fields) | Structs can use fewer slots by changing the order of fields | 4 | 80000 |
| [[G-16]](#g-16-internal-functions-only-called-once-can-be-inlined-to-save-gas) | `internal` functions only called once can be inlined to save gas | 2 | 60 |
| [[G-17]](#g-17-inline-modifiers-that-are-only-used-once-to-save-gas) | Inline `modifier`s that are only used once to save gas | 4 | - |
| [[G-18]](#g-18-private-functions-only-used-once-can-be-inlined-to-save-gas) | Private functions only used once can be inlined to save gas | 4 | 120 |
| [[G-19]](#g-19-inverting-the-condition-of-an-if-else-statement-wastes-gas) | Inverting the condition of an `if`-`else`-statement wastes gas | 2 | 6 |
| [[G-20]](#g-20-update-openzeppelin-dependency-to-save-gas) | Update OpenZeppelin dependency to save gas | 54 | - |
| [[G-21]](#g-21-mappings-are-cheaper-to-use-than-storage-arrays) | Mappings are cheaper to use than storage arrays | 36 | 75600 |
| [[G-22]](#g-22-operator--costs-less-gas-than-operator-) | Operator `>=`/`<=` costs less gas than operator `>`/`<` | 41 | 123 |
| [[G-23]](#g-23-consider-pre-calculating-the-address-of-addressthis-to-save-gas) | Consider pre-calculating the address of `address(this)` to save gas | 40 | - |
| [[G-24]](#g-24-empty-code-blocks-can-be-removed-to-save-gas) | Empty code blocks can be removed to save gas | 1 | - |
| [[G-25]](#g-25-remove-empty-functions-to-save-gas) | Remove empty functions to save gas | 4 | - |
| [[G-26]](#g-26-usage-of-intsuints-smaller-than-32-bytes-incurs-overhead) | Usage of `int`s/`uint`s smaller than 32 bytes incurs overhead | 323 | 17765 |
| [[G-27]](#g-27-using-a-double-if-statement-instead-of-a-logical-and) | Using a double `if` statement instead of a logical AND(`&&`) | 16 | 480 |
| [[G-28]](#g-28-requirerevert-strings-longer-than-32-bytes-cost-extra-gas) | `require()`/`revert()` strings longer than 32 bytes cost extra gas | 30 | 90 |
| [[G-29]](#g-29-reduce-deployment-costs-by-tweaking-contracts-metadata) | Reduce deployment costs by tweaking contracts' metadata | 30 | - |
| [[G-30]](#g-30-divisions-can-be-unchecked-to-save-gas) | Divisions can be unchecked to save gas | 13 | 260 |
| [[G-31]](#g-31-use-assembly-to-validate-msgsender) | Use assembly to validate `msg.sender` | 22 | 264 |
| [[G-32]](#g-32-using-assembly-to-check-for-zero-can-save-gas) | Using assembly to check for zero can save gas | 93 | 558 |
| [[G-33]](#g-33-low-level-call-can-be-optimized-with-assembly) | Low level `call` can be optimized with assembly | 1 | 248 |
| [[G-34]](#g-34-consider-using-oz-enumerateset-in-place-of-nested-mappings) | Consider using OZ EnumerateSet in place of nested mappings | 6 | 6000 |
| [[G-35]](#g-35-consider-using-soladys-fixedpointmathlib) | Consider using solady's `FixedPointMathLib` | 3 | - |
| [[G-36]](#g-36-use-selfbalance-instead-of-addressxbalance) | Use `selfbalance()` instead of `address(x).balance` | 6 | 90 |
| [[G-37]](#g-37-assigning-state-variables-directly-with-named-struct-constructors-wastes-gas) | Assigning state variables directly with named struct constructors wastes gas | 4 | 112 |
| [[G-38]](#g-38-avoid-zero-transfer-to-save-gas) | Avoid zero transfer to save gas | 17 | 1700 |
| [[G-39]](#g-39-cache-addressthis-when-used-more-than-once) | Cache address(this) when used more than once | 16 | - |
| [[G-40]](#g-40-checking-constants-first-can-save-gas) | Checking constants first can save gas | 3 | - |
| [[G-41]](#g-41-state-variable-read-in-a-loop) | State variable read in a loop | 6 | 582 |
| [[G-42]](#g-42-state-variable-written-in-a-loop) | State variable written in a loop | 1 | 2897 |
| [[G-43]](#g-43-unlimited-gas-consumption-risk-due-to-external-call-recipients) | Unlimited gas consumption risk due to external call recipients | 2 | - |
| [[G-44]](#g-44-optimize-names-to-save-gas) | Optimize names to save gas | 46 | 1012 |
| [[G-45]](#g-45-reduce-gas-usage-by-moving-to-solidity-0819-or-later) | Reduce gas usage by moving to Solidity 0.8.19 or later | 11 | - |
| [[G-46]](#g-46-newer-versions-of-solidity-are-more-gas-efficient) | Newer versions of solidity are more gas efficient | 81 | - |
| [[G-47]](#g-47-avoid-updating-storage-when-the-value-hasnt-changed) | Avoid updating storage when the value hasn't changed | 19 | 15200 |
| [[G-48]](#g-48-same-cast-is-done-multiple-times) | Same cast is done multiple times | 8 | - |
| [[G-49]](#g-49-state-variables-that-are-used-multiple-times-in-a-function-should-be-cached-in-stack-variables) | State variables that are used multiple times in a function should be cached in stack variables | 24 | 5432 |
| [[G-50]](#g-50-use-solady-library-where-possible-to-save-gas) | Use solady library where possible to save gas | 54 | 54000 |
| [[G-51]](#g-51-use-the-inputsresults-of-assignments-rather-than-re-reading-state-variables) | Use the inputs/results of assignments rather than re-reading state variables | 1 | 97 |
| [[G-52]](#g-52-structs-can-be-packed-into-fewer-storage-slots-by-truncating-fields) | Structs can be packed into fewer storage slots by truncating fields | 2 | 40000 |
| [[G-53]](#g-53-redundant-state-variable-getters) | Redundant state variable getters | 1 | - |
| [[G-54]](#g-54-using-constants-instead-of-enum-can-save-gas) | Using `constant`s instead of `enum` can save gas | 9 | - |
| [[G-55]](#g-55-use-arrayunsafeaccess-to-avoid-repeated-array-length-checks) | Use `Array.unsafeAccess()` to avoid repeated array length checks | 1 | 2100 |
| [[G-56]](#g-56-assembly-use-scratch-space-for-building-calldata) | Assembly: Use scratch space for building calldata | 61 | 13420 |
| [[G-57]](#g-57-use-assembly-to-emit-events) | Use assembly to emit events | 36 | 1368 |
| [[G-58]](#g-58-use-assembly-to-compute-hashes-to-save-gas) | Use assembly to compute hashes to save gas | 2 | 160 |
| [[G-59]](#g-59-use-calldata-instead-of-memory-for-immutable-arguments) | Use `calldata` instead of `memory` for immutable arguments | 70 | 21000 |
| [[G-60]](#g-60-consider-using-soladys-gas-optimized-lib-for-math) | Consider Using Solady's Gas Optimized Lib for Math | 6 | - |
| [[G-61]](#g-61-do-while-is-cheaper-than-for-loops-when-the-initial-check-can-be-skipped) | `do`-`while` is cheaper than `for`-loops when the initial check can be skipped | 49 | - |
| [[G-62]](#g-62-avoid-unnecessary-public-variables) | Avoid Unnecessary Public Variables | 41 | 902000 |
| [[G-63]](#g-63-optimize-deployment-size-by-fine-tuning-ipfs-hash) | Optimize Deployment Size by Fine-tuning IPFS Hash | 30 | 318000 |
| [[G-64]](#g-64-the-result-of-a-function-call-should-be-cached-rather-than-re-calling-the-function) | The result of a function call should be cached rather than re-calling the function | 38 | 3800 |
| [[G-65]](#g-65-multiple-accesses-of-a-memorycalldata-array-should-use-a-local-variable-cache) | Multiple accesses of a `memory`/`calldata` array should use a local variable cache | 25 | - |
| [[G-66]](#g-66-multiple-accesses-of-the-same-mapping-key-should-be-cached) | Multiple accesses of the same mapping key should be cached | 11 | 462 |
| [[G-67]](#g-67-multiple-mappings-can-be-replaced-with-a-single-struct-mapping) | Multiple mappings can be replaced with a single struct mapping | 8 | 336 |
| [[G-68]](#g-68-consider-using-bytes32-rather-than-a-string) | Consider using `bytes32` rather than a `string` | 7 | - |

## Gas Optimizations

### [G-01] Use `storage` instead of `memory` for structs/arrays

When fetching data from a storage location, assigning the data to a `memory` variable causes all fields of the struct/array to be read from storage, which incurs a Gcoldsload (**2100 gas**) for *each* field of the struct/array. If the fields are read from the new memory variable, they incur an additional `MLOAD` rather than a cheap stack read. Instead of declaring the variable with the `memory` keyword, declaring the variable with the `storage` keyword and caching any fields that need to be re-read in stack variables, will be much cheaper, only incurring the Gcoldsload for the fields actually read. The only time it makes sense to read the whole struct/array into a `memory` variable, is if the full struct/array is being returned by the function, is being passed to a function that requires `memory`, or if the array/struct is being read from another `memory` array/struct.

<details>
<summary>There are 6 instances (click to show):</summary>

- *LibProposing.sol* ( [93-93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L93-L93) ):

```solidity
93:         TaikoData.SlotB memory b = _state.slotB;
```

- *LibProving.sol* ( [110-110](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L110-L110) ):

```solidity
110:         TaikoData.SlotB memory b = _state.slotB;
```

- *LibUtils.sol* ( [33-33](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L33-L33) ):

```solidity
33:         TaikoData.SlotB memory b = _state.slotB;
```

- *LibVerifying.sol* ( [99-99](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L99-L99) ):

```solidity
99:         TaikoData.SlotB memory b = _state.slotB;
```

- *AutomataDcapV3Attestation.sol* ( [180-180](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L180-L180) ):

```solidity
180:         EnclaveIdStruct.EnclaveId memory enclaveId = qeIdentity;
```

- *ERC20Vault.sol* ( [171-171](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L171-L171) ):

```solidity
171:             CanonicalERC20 memory ctoken = bridgedToCanonical[btokenOld_];
```

</details>

### [G-02] Constructors can be marked as payable to save deployment gas

Payable functions cost less gas to execute, because the compiler does not have to add extra checks to ensure that no payment is provided. A constructor can be safely marked as payable, because only the deployer would be able to pass funds, and the project itself would not pass any funds.

There are 3 instances:

- *AutomataDcapV3Attestation.sol* ( [54-54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L54-L54) ):

```solidity
54:     constructor(address sigVerifyLibAddr, address pemCertLibAddr) {
```

- *SigVerifyLib.sol* ( [20-20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L20-L20) ):

```solidity
20:     constructor(address es256Verifier) {
```

- *EssentialContract.sol* ( [64-64](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L64-L64) ):

```solidity
64:     constructor() {
```

### [G-03] State variables only set in the constructor should be declared `immutable`

This can avoid a Gsset (**20000 gas**) on deployment (in constructor), and replaces the first access in each transaction (Gcoldsload - **2100 gas**) and each access thereafter (Gwarmacces - **100 gas**) with a `PUSH32` (**3 gas**).
While `string`s are not value types, and therefore cannot be `immutable`/`constant` if not hard-coded outside of the constructor, the same behavior can be achieved by making the current contract `abstract` with `virtual` functions for the `string` accessors, and having a child contract override the functions with the hard-coded implementation-specific values.

There are 2 instances:

- *AutomataDcapV3Attestation.sol* ( [57-57](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L57-L57) ):

```solidity
57:         owner = msg.sender;
```

- *SigVerifyLib.sol* ( [21-21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L21-L21) ):

```solidity
21:         ES256VERIFIER = es256Verifier;
```

### [G-04] Unnecessary event parameters should be removed

Data that can be obtained from off-chain data and event log details should not be added as event parameters to save gas.

There is 1 instance:

- *SgxVerifier.sol* ( [230-230](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L230-L230) ):

```solidity
/// @audit `block.timestamp`
230:         emit InstanceAdded(id, newInstance, oldInstance, block.timestamp);
```

### [G-05] `abi.encode()` is less efficient than `abi.encodePacked()` for non-address arguments

There are 4 instances:

- *LibProposing.sol* ( [126-126](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L126-L126), [213-213](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L213-L213) ):

```solidity
126:                 depositsHash: keccak256(abi.encode(deposits_)),

213:             metaHash: keccak256(abi.encode(meta_)),
```

- *LibProving.sol* ( [121-121](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L121-L121) ):

```solidity
121:         if (blk.blockId != _meta.id || blk.metaHash != keccak256(abi.encode(_meta))) {
```

- *AutomataDcapV3Attestation.sol* ( [482-482](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L482-L482) ):

```solidity
482:         retData = abi.encodePacked(sha256(abi.encode(v3quote)), tcbStatus);
```

### [G-06] Counting down in for statements is more gas efficient

Looping downwards is more gas efficient because of how the EVM compares variables. When using a 'for' loop that counts down, comparing the end condition with zero is cheaper than comparing with another number. Therefore, it is recommended to restructure loops to count downwards whenever possible.

<details>
<summary>There are 45 instances (click to show):</summary>

- *AssignmentHook.sol* ( [172-172](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L172-L172) ):

```solidity
172:         for (uint256 i; i < _tierFees.length; ++i) {
```

- *LibProposing.sol* ( [244-244](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L244-L244) ):

```solidity
244:             for (uint256 i; i < params.hookCalls.length; ++i) {
```

- *Guardians.sol* ( [74-74](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L74-L74), [80-80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L80-L80), [133-133](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L133-L133) ):

```solidity
74:         for (uint256 i; i < guardians.length; ++i) {

80:         for (uint256 i = 0; i < _newGuardians.length; ++i) {

133:             for (uint256 i; i < guardiansLength; ++i) {
```

- *TaikoL2.sol* ( [234-234](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L234-L234) ):

```solidity
234:             for (uint256 i; i < 255 && _blockId >= i + 1; ++i) {
```

- *AutomataDcapV3Attestation.sol* ( [80-80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L80-L80), [95-95](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L95-L95), [191-191](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L191-L191), [214-214](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L214-L214), [240-240](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L240-L240), [259-259](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L259-L259), [420-420](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L420-L420) ):

```solidity
80:         for (uint256 i; i < serialNumBatch.length; ++i) {

95:         for (uint256 i; i < serialNumBatch.length; ++i) {

191:         for (uint256 i; i < enclaveId.tcbLevels.length; ++i) {

214:         for (uint256 i; i < tcb.tcbLevels.length; ++i) {

240:         for (uint256 i; i < CPUSVN_LENGTH; ++i) {

259:         for (uint256 i; i < n; ++i) {

420:             for (uint256 i; i < 3; ++i) {
```

- *PEMCertChainLib.sol* ( [54-54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L54-L54), [244-244](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L244-L244), [354-354](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L354-L354) ):

```solidity
54:         for (uint256 i; i < size; ++i) {

244:         for (uint256 i; i < split.length; ++i) {

354:         for (uint256 i; i < SGX_TCB_CPUSVN_SIZE + 1; ++i) {
```

- *V3Parser.sol* ( [153-153](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L153-L153), [281-281](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L281-L281) ):

```solidity
153:         for (uint256 i; i < encoded.length; ++i) {

281:         for (uint256 i; i < 3; ++i) {
```

- *BytesUtils.sol* ( [333-333](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L333-L333) ):

```solidity
333:         for (uint256 i; i < len; ++i) {
```

- *RsaVerify.sol* ( [140-140](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L140-L140), [152-152](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L152-L152), [158-158](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L158-L158), [174-174](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L174-L174), [273-273](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L273-L273), [283-283](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L283-L283), [290-290](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L290-L290) ):

```solidity
140:         for (uint256 i = 2; i < 2 + paddingLen; ++i) {

152:             for (uint256 i; i < digestAlgoWithParamLen; ++i) {

158:             for (uint256 i; i < digestAlgoWithParamLen; ++i) {

174:         for (uint256 i; i < _sha256.length; ++i) {

273:         for (uint256 i = 2; i < 2 + paddingLen; ++i) {

283:         for (uint256 i; i < sha1Prefix.length; ++i) {

290:         for (uint256 i; i < _sha1.length; ++i) {
```

- *X509DateUtils.sol* ( [48-48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L48-L48), [59-59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L59-L59) ):

```solidity
48:         for (uint16 i = 1970; i < year; ++i) {

59:         for (uint8 i = 1; i < month; ++i) {
```

- *Bridge.sol* ( [90-90](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L90-L90) ):

```solidity
90:         for (uint256 i; i < _msgHashes.length; ++i) {
```

- *SignalService.sol* ( [104-104](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L104-L104) ):

```solidity
104:         for (uint256 i; i < hopProofs.length; ++i) {
```

- *ERC721Airdrop.sol* ( [59-59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59-L59) ):

```solidity
59:         for (uint256 i; i < tokenIds.length; ++i) {
```

- *RLPWriter.sol* ( [46-46](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L46-L46), [59-59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L59-L59), [66-66](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66-L66) ):

```solidity
46:             for (i = 1; i <= lenLen; i++) {

59:         for (; i < 32; i++) {

66:         for (uint256 j = 0; j < out_.length; j++) {
```

- *MerkleTrie.sol* ( [85-85](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85-L85) ):

```solidity
85:         for (uint256 i = 0; i < proof.length; i++) {
```

- *ERC1155Vault.sol* ( [47-47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L47-L47), [251-251](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L251-L251), [269-269](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L269-L269) ):

```solidity
47:         for (uint256 i; i < _op.amounts.length; ++i) {

251:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

269:                 for (uint256 i; i < _op.tokenIds.length; ++i) {
```

- *ERC721Vault.sol* ( [34-34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L34-L34), [170-170](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L170-L170), [175-175](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L175-L175), [197-197](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L197-L197), [210-210](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L210-L210) ):

```solidity
34:         for (uint256 i; i < _op.tokenIds.length; ++i) {

170:             for (uint256 i; i < _tokenIds.length; ++i) {

175:             for (uint256 i; i < _tokenIds.length; ++i) {

197:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

210:                 for (uint256 i; i < _op.tokenIds.length; ++i) {
```

- *SgxVerifier.sol* ( [104-104](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L104-L104), [210-210](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210-L210) ):

```solidity
104:         for (uint256 i; i < _ids.length; ++i) {

210:         for (uint256 i; i < _instances.length; ++i) {
```

</details>

### [G-07] Using `msg` globals directly, rather than caching the value, saves gas

For example, use `msg.sender` directly rather than storing it to a local variable.

There is 1 instance:

- *AssignmentHook.sol* ( [93-93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L93-L93) ):

```solidity
93:         address taikoL1Address = msg.sender;
```

### [G-08] Stack variable is only used once

If the variable is only accessed once, it's cheaper to use the assigned value directly that one time, and save the 3 gas the extra stack assignment would spend.

<details>
<summary>There are 70 instances (click to show):</summary>

- *AssignmentHook.sol* ( [101-101](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L101-L101) ):

```solidity
/// @audit tko
101:         IERC20 tko = IERC20(resolve("taiko_token", false));
```

- *LibProposing.sol* ( [238-238](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L238-L238) ):

```solidity
/// @audit tkoBalance
238:             uint256 tkoBalance = tko.balanceOf(address(this));
```

- *Guardians.sol* ( [131-131](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L131-L131) ):

```solidity
/// @audit guardiansLength
131:         uint256 guardiansLength = guardians.length;
```

- *CrossChainOwned.sol* ( [50-50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L50-L50) ):

```solidity
/// @audit success
50:         (bool success,) = address(this).call(txdata);
```

- *TaikoL2.sol* ( [136-136](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L136-L136) ):

```solidity
/// @audit config
136:         Config memory config = getConfig();
```

- *AutomataDcapV3Attestation.sol* ( [139-139](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L139-L139), [163-163](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L163-L163), [292-292](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L292-L292), [421-421](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L421-L421) ):

```solidity
/// @audit success
139:         (bool success,) = _verify(data);

/// @audit retData
163:         bytes memory retData = abi.encodePacked(INVALID_EXIT_CODE);

/// @audit issuerPubKeyHash
292:             bytes32 issuerPubKeyHash = keccak256(issuer.pubKey);

/// @audit isPckCert
421:                 bool isPckCert = i == 0; // additional parsing for PCKCert
```

- *PEMCertChainLib.sol* ( [52-52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L52-L52), [82-82](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L82-L82), [107-107](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L107-L107), [174-174](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L174-L174), [177-177](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L177-L177), [225-225](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L225-L225), [226-226](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L226-L226), [233-233](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L233-L233), [239-239](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L239-L239), [265-265](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L265-L265), [312-312](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L312-L312), [318-318](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L318-L318), [350-350](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L350-L350), [356-356](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L356-L356), [366-366](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L366-L366) ):

```solidity
/// @audit len
52:         uint256 len = pemChain.length;

/// @audit root
82:         uint256 root = der.root();

/// @audit serialNumBytes
107:             bytes memory serialNumBytes = der.bytesAt(tbsPtr);

/// @audit sigX
174:             bytes memory sigX = _trimBytes(der.bytesAt(sigPtr), 32);

/// @audit sigY
177:             bytes memory sigY = _trimBytes(der.bytesAt(sigPtr), 32);

/// @audit headerFound
225:         bool headerFound = beginPos != LibString.NOT_FOUND;

/// @audit footerFound
226:         bool footerFound = endPos != LibString.NOT_FOUND;

/// @audit contentStart
233:         uint256 contentStart = beginPos + HEADER_LENGTH;

/// @audit delimiter
239:         bytes memory delimiter = hex"0a";

/// @audit lengthDiff
265:         uint256 lengthDiff = n - expectedLength;

/// @audit pceidPtr
312:                         uint256 pceidPtr = der.nextSiblingOf(extnValueOidPtr);

/// @audit fmspcPtr
318:                         uint256 fmspcPtr = der.nextSiblingOf(extnValueOidPtr);

/// @audit tcbPtr
350:         uint256 tcbPtr = der.nextSiblingOf(oidPtr);

/// @audit svnValuePtr
356:             uint256 svnValuePtr = der.nextSiblingOf(svnPtr); // value

/// @audit cpusvn
366:                 uint256 cpusvn = uint256(svnValue);
```

- *V3Parser.sol* ( [38-38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L38-L38), [155-155](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L155-L155), [156-156](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L156-L156), [229-229](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L229-L229) ):

```solidity
/// @audit rawHeader
38:         bytes memory rawHeader = quote.substring(0, 48);

/// @audit upperDigit
155:             uint256 upperDigit = digits / 16;

/// @audit lowerDigit
156:             uint256 lowerDigit = digits % 16;

/// @audit rawQeReport
229:         bytes memory rawQeReport = rawAuthData.substring(128, 384);
```

- *Asn1Decode.sol* ( [183-183](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L183-L183) ):

```solidity
/// @audit valueLength
183:         uint256 valueLength = ptr.ixl() + 1 - ptr.ixf();
```

- *BytesUtils.sol* ( [73-73](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L73-L73), [74-74](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L74-L74), [295-295](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L295-L295), [296-296](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L296-L296), [297-297](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L297-L297) ):

```solidity
/// @audit selfptr
73:         uint256 selfptr;

/// @audit otherptr
74:         uint256 otherptr;

/// @audit ret
295:         bytes memory ret = new bytes(len);

/// @audit dest
296:         uint256 dest;

/// @audit src
297:         uint256 src;
```

- *SigVerifyLib.sol* ( [89-89](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L89-L89), [106-106](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L106-L106), [126-126](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L126-L126), [127-127](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L127-L127), [132-132](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L132-L132), [133-133](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L133-L133), [136-136](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L136-L136) ):

```solidity
/// @audit exponent
89:         bytes memory exponent = publicKey.substring(0, 3);

/// @audit exponent
106:         bytes memory exponent = publicKey.substring(0, 3);

/// @audit r
126:         uint256 r = uint256(bytes32(signature.substring(0, 32)));

/// @audit s
127:         uint256 s = uint256(bytes32(signature.substring(32, 32)));

/// @audit gx
132:         uint256 gx = uint256(bytes32(publicKey.substring(0, 32)));

/// @audit gy
133:         uint256 gy = uint256(bytes32(publicKey.substring(32, 32)));

/// @audit args
136:         bytes memory args = abi.encode(sha256(tbs), r, s, gx, gy);
```

- *Bridge.sol* ( [138-138](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L138-L138), [178-178](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L178-L178), [187-187](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L187-L187), [557-557](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L557-L557), [558-558](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L558-L558), [559-559](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L559-L559) ):

```solidity
/// @audit expectedAmount
138:         uint256 expectedAmount = _message.value + _message.fee;

/// @audit failureSignal
178:             bytes32 failureSignal = signalForFailedMessage(msgHash);

/// @audit invocationDelay
187:         (uint256 invocationDelay,) = getInvocationDelays();

/// @audit msgHash
557:             bytes32 msgHash;

/// @audit from
558:             address from;

/// @audit srcChainId
559:             uint64 srcChainId;
```

- *Lib4844.sol* ( [51-51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/Lib4844.sol#L51-L51), [52-52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/Lib4844.sol#L52-L52) ):

```solidity
/// @audit first
51:         bytes32 first;

/// @audit second
52:         bytes32 second;
```

- *TimelockTokenPool.sol* ( [151-151](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L151-L151), [171-171](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L171-L171), [197-197](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L197-L197) ):

```solidity
/// @audit r
151:         Recipient storage r = recipients[_recipient];

/// @audit recipient
171:         address recipient = ECDSA.recover(hash, _sig);

/// @audit _amountUnlocked
197:         uint128 _amountUnlocked = amountUnlocked / 1e18; // divide first
```

- *ExcessivelySafeCall.sol* ( [37-37](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L37-L37), [38-38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L38-L38) ):

```solidity
/// @audit _success
37:         bool _success;

/// @audit _returnData
38:         bytes memory _returnData = new bytes(_maxCopy);
```

- *Bytes.sol* ( [30-30](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L30-L30), [103-103](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L103-L103) ):

```solidity
/// @audit tempBytes
30:         bytes memory tempBytes;

/// @audit _nibbles
103:         bytes memory _nibbles;
```

- *RLPReader.sol* ( [42-42](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L42-L42), [177-177](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L177-L177), [197-197](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L197-L197), [243-243](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L243-L243) ):

```solidity
/// @audit ptr
42:         MemoryPointer ptr;

/// @audit firstByteOfContent
177:             bytes1 firstByteOfContent;

/// @audit firstByteOfContent
197:             bytes1 firstByteOfContent;

/// @audit firstByteOfContent
243:             bytes1 firstByteOfContent;
```

- *MerkleTrie.sol* ( [134-134](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L134-L134), [142-142](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L142-L142) ):

```solidity
/// @audit branchKey
134:                     uint8 branchKey = uint8(key[currentKeyIndex]);

/// @audit offset
142:                 uint8 offset = 2 - (prefix % 2);
```

- *SecureMerkleTrie.sol* ( [29-29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L29-L29), [47-47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L47-L47) ):

```solidity
/// @audit key
29:         bytes memory key = _getSecureKey(_key);

/// @audit key
47:         bytes memory key = _getSecureKey(_key);
```

- *ERC1155Vault.sol* ( [140-140](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L140-L140) ):

```solidity
/// @audit data
140:         (bytes memory data) = abi.decode(message.data[4:], (bytes));
```

- *ERC20Vault.sol* ( [270-270](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L270-L270), [378-378](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L378-L378) ):

```solidity
/// @audit token
270:         address token = _transferTokens(ctoken, to, amount);

/// @audit _balance
378:             uint256 _balance = t.balanceOf(address(this));
```

- *ERC721Vault.sol* ( [94-94](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L94-L94) ):

```solidity
/// @audit token
94:         address token = _transferTokens(ctoken, to, tokenIds);
```

- *SgxVerifier.sol* ( [156-156](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L156-L156), [181-181](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L181-L181) ):

```solidity
/// @audit signature
156:         bytes memory signature = Bytes.slice(_proof.data, 24);

/// @audit taikoL1
181:         address taikoL1 = resolve("taiko", false);
```

</details>

### [G-09] Do not cache state variables that are used only once

It's cheaper to access the state variable directly if it is accessed only once. This can save some gas cost of the extra stack allocation.

There are 3 instances:

- *AutomataDcapV3Attestation.sol* ( [387-388](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L387-L388), [389-389](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L389-L389) ):

```solidity
387:                 bool mrEnclaveIsTrusted =
388:                     _trustedUserMrEnclave[v3quote.localEnclaveReport.mrEnclave];

389:                 bool mrSignerIsTrusted = _trustedUserMrSigner[v3quote.localEnclaveReport.mrSigner];
```

- *TimelockTokenPool.sol* ( [151-151](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L151-L151) ):

```solidity
151:         Recipient storage r = recipients[_recipient];
```

### [G-10] Do not calculate constants

Due to how constant variables are implemented (replacements at compile-time), an expression assigned to a constant variable is recomputed each time that the variable is used, which wastes some gas.

There are 2 instances:

- *LibProposing.sol* ( [21-21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L21-L21) ):

```solidity
21:     uint256 public constant MAX_BYTES_PER_BLOB = 4096 * 32;
```

- *MerkleTrie.sol* ( [24-24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L24-L24) ):

```solidity
24:     uint256 internal constant BRANCH_NODE_LENGTH = TREE_RADIX + 1;
```

### [G-11] Use of `emit` inside a loop

Emitting an event inside a loop performs a `LOG` op N times, where N is the loop length. Consider refactoring the code to emit the event only once at the end of loop. Gas savings should be multiplied by the average loop length.

There are 4 instances:

- *LibVerifying.sol* ( [198-206](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L198-L206) ):

```solidity
198:                 emit BlockVerified({
199:                     blockId: blockId,
200:                     assignedProver: blk.assignedProver,
201:                     prover: ts.prover,
202:                     blockHash: blockHash,
203:                     stateRoot: stateRoot,
204:                     tier: ts.tier,
205:                     contestations: ts.contestations
206:                 });
```

- *Bridge.sol* ( [93-93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L93-L93) ):

```solidity
93:             emit MessageSuspended(msgHash, _suspend);
```

- *SgxVerifier.sol* ( [109-109](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L109-L109), [220-220](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220-L220) ):

```solidity
109:             emit InstanceDeleted(idx, instances[idx].addr);

220:             emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);
```

### [G-12] Emitting literals or constants wastes gas

Every event parameter costs `Glogdata` (**8 gas**) per byte. You can avoid this extra cost, in cases where you're emitting a literal or constant, by creating a second version of the event, which doesn't have the parameter (and have users look to the contract's variables for its value instead), and using the new event in the cases shown below.

<details>
<summary>There are 5 instances (click to show):</summary>

- *LibProving.sol* ( [230-236](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L230-L236) ):

```solidity
230:                 emit TransitionProved({
231:                     blockId: blk.blockId,
232:                     tran: _tran,
233:                     prover: msg.sender,
234:                     validityBond: 0,
235:                     tier: _proof.tier
236:                 });
```

- *LibVerifying.sol* ( [73-81](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L73-L81) ):

```solidity
73:         emit BlockVerified({
74:             blockId: 0,
75:             assignedProver: address(0),
76:             prover: address(0),
77:             blockHash: _genesisBlockHash,
78:             stateRoot: 0,
79:             tier: 0,
80:             contestations: 0
81:         });
```

- *Bridge.sol* ( [210-210](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L210-L210), [303-303](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L303-L303) ):

```solidity
210:             emit MessageReceived(msgHash, _message, true);

303:             emit MessageReceived(msgHash, _message, false);
```

- *SgxVerifier.sol* ( [220-220](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220-L220) ):

```solidity
220:             emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);
```

</details>

### [G-13] Use local variables for emitting

Use the function/modifier's local copy of the state variable, rather than incurring an extra Gwarmaccess (**100 gas**). In the unlikely event that the state variable hasn't already been used by the function/modifier, consider whether it is really necessary to include it in the event, given the fact that it incurs a Gcoldsload (**2100 gas**), or whether it can be passed in to or back out of the functions that _do_ use it.

<details>
<summary>There are 7 instances (click to show):</summary>

- *Guardians.sol* ( [95-95](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L95-L95) ):

```solidity
/// @audit version
95:         emit GuardiansUpdated(version, _newGuardians);
```

- *CrossChainOwned.sol* ( [53-53](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L53-L53) ):

```solidity
/// @audit nextTxId
53:         emit TransactionExecuted(nextTxId++, bytes4(txdata));
```

- *TaikoL2.sol* ( [157-157](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L157-L157) ):

```solidity
/// @audit gasExcess
157:         emit Anchored(blockhash(parentId), gasExcess);
```

- *BridgedERC20Base.sol* ( [63-63](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L63-L63), [80-80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L80-L80) ):

```solidity
/// @audit migratingAddress
63:             emit MigratedTo(migratingAddress, _account, _amount);

/// @audit migratingAddress
80:             emit MigratedTo(migratingAddress, _account, _amount);
```

- *SgxVerifier.sol* ( [109-109](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L109-L109), [220-220](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220-L220) ):

```solidity
/// @audit instances
109:             emit InstanceDeleted(idx, instances[idx].addr);

/// @audit nextInstanceId
220:             emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);
```

</details>

### [G-14] Contract storage can use fewer slots by changing the order of state variables

The reduction of slots can reduce the gas consumption of each storage read/write operation. If variables occupying the same slot are written within the same transaction, avoids a separate Gsset (**20000 gas**). Reads of the variables can also be cheaper.

There are 2 instances:

- *AutomataDcapV3Attestation.sol* ( [22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L22) ):

```solidity
/// @audit 10 slots -> 9 slots by new order:
///        128 B: EnclaveIdStruct.EnclaveId qeIdentity
///        32 B: mapping(bytes32 enclave => bool trusted) _trustedUserMrEnclave
///        32 B: mapping(bytes32 signer => bool trusted) _trustedUserMrSigner
///        32 B: mapping(uint256 idx => mapping(bytes serialNum => bool revoked)) _serialNumIsRevoked
///        32 B: mapping(string fmspc => TCBInfoStruct.TCBInfo tcbInfo) tcbInfo
///        20 B: address owner
///        1 B: bool _checkLocalEnclaveReport
22: contract AutomataDcapV3Attestation is IAttestation {
```

- *ERC20Airdrop2.sol* ( [12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L12) ):

```solidity
/// @audit 50 slots -> 49 slots by new order:
///        1440 B: uint256[45] __gap
///        32 B: mapping(address addr => uint256 amountClaimed) claimedAmount
///        32 B: mapping(address addr => uint256 amountWithdrawn) withdrawnAmount
///        20 B: address token
///        8 B: uint64 withdrawalWindow
///        20 B: address vault
12: contract ERC20Airdrop2 is MerkleClaimable {
```

### [G-15] Structs can use fewer slots by changing the order of fields

The reduction of slots can reduce the gas consumption of each storage read/write operation. Each slot saved can avoid an extra Gsset (**20000 gas**) for the first setting of the struct. Subsequent reads as well as writes have smaller gas savings.

<details>
<summary>There are 4 instances (click to show):</summary>

- *TaikoData.sol* ( [10-60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L10-L60), [78-88](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L78-L88) ):

```solidity
/// @audit 8 slots -> 7 slots by new order:
///        32 B: uint256 ethDepositRingBufferSize
///        32 B: uint256 ethDepositGas
///        32 B: uint256 ethDepositMaxFee
///        12 B: uint96 livenessBond
///        12 B: uint96 ethDepositMinAmount
///        8 B: uint64 chainId
///        12 B: uint96 ethDepositMaxAmount
///        8 B: uint64 blockMaxProposals
///        8 B: uint64 blockRingBufferSize
///        4 B: uint32 blockMaxGasLimit
///        8 B: uint64 maxBlocksToVerifyPerProposal
///        8 B: uint64 ethDepositMinCountPerBlock
///        8 B: uint64 ethDepositMaxCountPerBlock
///        3 B: uint24 blockMaxTxListBytes
///        3 B: uint24 blobExpiry
///        1 B: bool blobAllowedForDA
///        1 B: bool blobReuseEnabled
///        1 B: uint8 blockSyncThreshold
10:     struct Config {
11:         // ---------------------------------------------------------------------
12:         // Group 1: General configs
13:         // ---------------------------------------------------------------------
14:         // The chain ID of the network where Taiko contracts are deployed.
15:         uint64 chainId;
16:         // ---------------------------------------------------------------------
17:         // Group 2: Block level configs
18:         // ---------------------------------------------------------------------
19:         // The maximum number of proposals allowed in a single block.
20:         uint64 blockMaxProposals;
21:         // Size of the block ring buffer, allowing extra space for proposals.
22:         uint64 blockRingBufferSize;
23:         // The maximum number of verifications allowed when a block is proposed.
24:         uint64 maxBlocksToVerifyPerProposal;
25:         // The maximum gas limit allowed for a block.
26:         uint32 blockMaxGasLimit;
27:         // The maximum allowed bytes for the proposed transaction list calldata.
28:         uint24 blockMaxTxListBytes;
29:         // The max period in seconds that a blob can be reused for DA.
30:         uint24 blobExpiry;
31:         // True if EIP-4844 is enabled for DA
32:         bool blobAllowedForDA;
33:         // True if blob can be reused
34:         bool blobReuseEnabled;
...... OMITTED ......
36:         // Group 3: Proof related configs
37:         // ---------------------------------------------------------------------
38:         // The amount of Taiko token as a prover liveness bond
39:         uint96 livenessBond;
40:         // ---------------------------------------------------------------------
41:         // Group 4: ETH deposit related configs
42:         // ---------------------------------------------------------------------
43:         // The size of the ETH deposit ring buffer.
44:         uint256 ethDepositRingBufferSize;
45:         // The minimum number of ETH deposits allowed per block.
46:         uint64 ethDepositMinCountPerBlock;
47:         // The maximum number of ETH deposits allowed per block.
48:         uint64 ethDepositMaxCountPerBlock;
49:         // The minimum amount of ETH required for a deposit.
50:         uint96 ethDepositMinAmount;
51:         // The maximum amount of ETH allowed for a deposit.
52:         uint96 ethDepositMaxAmount;
53:         // The gas cost for processing an ETH deposit.
54:         uint256 ethDepositGas;
55:         // The maximum fee allowed for an ETH deposit.
56:         uint256 ethDepositMaxFee;
57:         // The max number of L2 blocks that can stay unsynced on L1 (a value of zero disables
58:         // syncing)
59:         uint8 blockSyncThreshold;
60:     }

/// @audit 7 slots -> 6 slots by new order:
///        32 B: bytes32 extraData
///        32 B: bytes32 blobHash
///        32 B: bytes32 parentMetaHash
///        32 B: HookCall[] hookCalls
///        20 B: address assignedProver
///        3 B: uint24 txListByteOffset
///        3 B: uint24 txListByteSize
///        1 B: bool cacheBlobForReuse
///        20 B: address coinbase
78:     struct BlockParams {
79:         address assignedProver;
80:         address coinbase;
81:         bytes32 extraData;
82:         bytes32 blobHash;
83:         uint24 txListByteOffset;
84:         uint24 txListByteSize;
85:         bool cacheBlobForReuse;
86:         bytes32 parentMetaHash;
87:         HookCall[] hookCalls;
88:     }
```

- *V3Struct.sol* ( [17-31](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L17-L31) ):

```solidity
/// @audit 10 slots -> 9 slots by new order:
///        32 B: bytes32 mrEnclave
///        32 B: bytes32 reserved2
///        32 B: bytes32 mrSigner
///        32 B: bytes reserved3
///        32 B: bytes reserved4
///        32 B: bytes reportData
///        28 B: bytes28 reserved1
///        4 B: bytes4 miscSelect
///        16 B: bytes16 cpuSvn
///        16 B: bytes16 attributes
///        2 B: uint16 isvProdId
///        2 B: uint16 isvSvn
17:     struct EnclaveReport {
18:         bytes16 cpuSvn;
19:         bytes4 miscSelect;
20:         bytes28 reserved1;
21:         bytes16 attributes;
22:         bytes32 mrEnclave;
23:         bytes32 reserved2;
24:         bytes32 mrSigner;
25:         bytes reserved3; // 96 bytes
26:         uint16 isvProdId;
27:         uint16 isvSvn;
28:         bytes reserved4; // 60 bytes
29:         bytes reportData; // 64 bytes - For QEReports, this contains the hash of the concatenation
30:             // of attestation key and QEAuthData
31:     }
```

- *ISignalService.sol* ( [20-27](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/ISignalService.sol#L20-L27) ):

```solidity
/// @audit 5 slots -> 4 slots by new order:
///        32 B: bytes32 rootHash
///        32 B: bytes[] accountProof
///        32 B: bytes[] storageProof
///        8 B: uint64 chainId
///        8 B: uint64 blockId
///        1 B: CacheOption cacheOption
20:     struct HopProof {
21:         uint64 chainId;
22:         uint64 blockId;
23:         bytes32 rootHash;
24:         CacheOption cacheOption;
25:         bytes[] accountProof;
26:         bytes[] storageProof;
27:     }
```

</details>

### [G-16] `internal` functions only called once can be inlined to save gas

If an `internal` function is only used once, there is no need to modularize it, unless the function calling it would otherwise be too long and complex. Not inlining costs 20 to 40 gas because of two extra JUMP instructions and additional stack operations needed for function calls.

There are 2 instances:

- *Guardians.sol* ( [124-124](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L124-L124) ):

```solidity
124:     function deleteApproval(bytes32 _hash) internal {
```

- *EssentialContract.sol* ( [140-140](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L140-L140) ):

```solidity
140:     function _inNonReentrant() internal view returns (bool) {
```

### [G-17] Inline `modifier`s that are only used once to save gas

Inline `modifier`s that are only used once can save gas.

There are 4 instances:

- *EssentialContract.sol* ( [53](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L53) ):

```solidity
53:     modifier whenPaused() {
```

- *ERC20Airdrop2.sol* ( [39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L39) ):

```solidity
39:     modifier ongoingWithdrawals() {
```

- *MerkleClaimable.sol* ( [33](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L33) ):

```solidity
33:     modifier ongoingClaim() {
```

- *BridgedERC20.sol* ( [37](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L37) ):

```solidity
37:     modifier onlyOwnerOrSnapshooter() {
```

### [G-18] Private functions only used once can be inlined to save gas

If a `private` function is only used once, there is no need to modularize it, unless the function calling it would otherwise be too long and complex.

There are 4 instances:

- *BytesUtils.sol* ( [272-272](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L272-L272) ):

```solidity
272:     function memcpy(uint256 dest, uint256 src, uint256 len) private pure {
```

- *TimelockTokenPool.sol* ( [239-239](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L239-L239), [267-267](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L267-L267) ):

```solidity
239:     function _getAmountUnlocked(Grant memory _grant) private view returns (uint128) {

267:     function _validateGrant(Grant memory _grant) private pure {
```

- *MerkleTrie.sol* ( [227-227](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L227-L227) ):

```solidity
227:     function _getNodePath(TrieNode memory _node) private pure returns (bytes memory nibbles_) {
```

### [G-19] Inverting the condition of an `if`-`else`-statement wastes gas

Flipping the `true` and `false` blocks instead saves ***[3 gas](https://gist.github.com/IllIllI000/44da6fbe9d12b9ab21af82f14add56b9)***.

There are 2 instances:

- *Bridge.sol* ( [209-211](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L209-L211), [302-304](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L302-L304) ):

```solidity
209:         } else if (!isMessageProven) {
210:             emit MessageReceived(msgHash, _message, true);
211:         } else {

302:         } else if (!isMessageProven) {
303:             emit MessageReceived(msgHash, _message, false);
304:         } else {
```

### [G-20] Update OpenZeppelin dependency to save gas

Every release contains new gas optimizations. Use the latest version to take advantage of this.

The imported version is `4.8.2`.

<details>
<summary>There are 54 instances (click to show):</summary>

- *TaikoToken.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L6) ):

```solidity
4: import "@openzeppelin/contracts-upgradeable/token/ERC20/ERC20Upgradeable.sol";

5: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20SnapshotUpgradeable.sol";

6: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20VotesUpgradeable.sol";
```

- *TaikoGovernor.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L5), [7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L7), [8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L8), [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L10) ):

```solidity
4: import "@openzeppelin/contracts-upgradeable/governance/GovernorUpgradeable.sol";

5: import

7: import "@openzeppelin/contracts-upgradeable/governance/extensions/GovernorVotesUpgradeable.sol";

8: import

10: import
```

- *TaikoTimelockController.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L4) ):

```solidity
4: import "@openzeppelin/contracts-upgradeable/governance/TimelockControllerUpgradeable.sol";
```

- *AssignmentHook.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L5) ):

```solidity
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

5: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```

- *LibProposing.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L4) ):

```solidity
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```

- *LibProving.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L4) ):

```solidity
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```

- *LibVerifying.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L4) ):

```solidity
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```

- *CrossChainOwned.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L4) ):

```solidity
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```

- *TaikoL2.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L5) ):

```solidity
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

5: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```

- *Bridge.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L4) ):

```solidity
4: import "@openzeppelin/contracts/utils/Address.sol";
```

- *AddressResolver.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L4) ):

```solidity
4: import "@openzeppelin/contracts-upgradeable/proxy/utils/Initializable.sol";
```

- *EssentialContract.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L5) ):

```solidity
4: import "@openzeppelin/contracts/proxy/utils/UUPSUpgradeable.sol";

5: import "@openzeppelin/contracts-upgradeable/access/Ownable2StepUpgradeable.sol";
```

- *LibAddress.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L6), [7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L7) ):

```solidity
4: import "@openzeppelin/contracts/utils/Address.sol";

5: import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol";

6: import "@openzeppelin/contracts/utils/introspection/IERC165.sol";

7: import "@openzeppelin/contracts/interfaces/IERC1271.sol";
```

- *SignalService.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L4) ):

```solidity
4: import "@openzeppelin/contracts/utils/math/SafeCast.sol";
```

- *TimelockTokenPool.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L6) ):

```solidity
4: import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol";

5: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

6: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```

- *ERC20Airdrop.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L5) ):

```solidity
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

5: import "@openzeppelin/contracts/governance/utils/IVotes.sol";
```

- *ERC20Airdrop2.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L4) ):

```solidity
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```

- *ERC721Airdrop.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L4) ):

```solidity
4: import "@openzeppelin/contracts/token/ERC721/IERC721.sol";
```

- *MerkleClaimable.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L4) ):

```solidity
4: import "@openzeppelin/contracts/utils/cryptography/MerkleProof.sol";
```

- *BaseVault.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L5) ):

```solidity
4: import "@openzeppelin/contracts-upgradeable/utils/introspection/IERC165Upgradeable.sol";

5: import "@openzeppelin/contracts/proxy/ERC1967/ERC1967Proxy.sol";
```

- *BridgedERC1155.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L6) ):

```solidity
4: import "@openzeppelin/contracts/utils/Strings.sol";

5: import "@openzeppelin/contracts-upgradeable/token/ERC1155/ERC1155Upgradeable.sol";

6: import
```

- *BridgedERC20.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L6), [7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L7) ):

```solidity
4: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/IERC20MetadataUpgradeable.sol";

5: import "@openzeppelin/contracts/utils/Strings.sol";

6: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20SnapshotUpgradeable.sol";

7: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20VotesUpgradeable.sol";
```

- *BridgedERC721.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L5) ):

```solidity
4: import "@openzeppelin/contracts-upgradeable/token/ERC721/ERC721Upgradeable.sol";

5: import "@openzeppelin/contracts/utils/Strings.sol";
```

- *ERC1155Vault.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L5) ):

```solidity
4: import "@openzeppelin/contracts/token/ERC1155/IERC1155.sol";

5: import "@openzeppelin/contracts-upgradeable/token/ERC1155/utils/ERC1155ReceiverUpgradeable.sol";
```

- *ERC20Vault.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L6) ):

```solidity
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

5: import "@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol";

6: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```

- *ERC721Vault.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L5) ):

```solidity
4: import "@openzeppelin/contracts/token/ERC721/IERC721.sol";

5: import "@openzeppelin/contracts/token/ERC721/IERC721Receiver.sol";
```

- *LibBridgedToken.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L4) ):

```solidity
4: import "@openzeppelin/contracts/utils/Strings.sol";
```

- *SgxVerifier.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L4) ):

```solidity
4: import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol";
```

</details>

### [G-21] Mappings are cheaper to use than storage arrays

When using storage arrays, solidity adds an internal lookup of the array's length (a Gcoldsload **2100 gas**) to ensure you don't read past the array's end. You can avoid this lookup by using a `mapping` and storing the number of entries in a separate storage variable. In cases where you have sentinel values (e.g. 'zero' means invalid), you can avoid length checks.

<details>
<summary>There are 36 instances (click to show):</summary>

- *TaikoL1.sol* ( [26-26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L26-L26) ):

```solidity
26:     uint256[50] private __gap;
```

- *TaikoToken.sol* ( [16-16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L16-L16) ):

```solidity
16:     uint256[50] private __gap;
```

- *TaikoGovernor.sol* ( [23-23](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L23-L23) ):

```solidity
23:     uint256[50] private __gap;
```

- *TaikoTimelockController.sol* ( [10-10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L10-L10) ):

```solidity
10:     uint256[50] private __gap;
```

- *AssignmentHook.sol* ( [40-40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L40-L40) ):

```solidity
40:     uint256[50] private __gap;
```

- *GuardianProver.sol* ( [11-11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/GuardianProver.sol#L11-L11) ):

```solidity
11:     uint256[50] private __gap;
```

- *Guardians.sol* ( [23-23](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L23-L23), [32-32](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L32-L32) ):

```solidity
23:     address[] public guardians;

32:     uint256[46] private __gap;
```

- *DevnetTierProvider.sol* ( [11-11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L11-L11) ):

```solidity
11:     uint256[50] private __gap;
```

- *MainnetTierProvider.sol* ( [11-11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L11-L11) ):

```solidity
11:     uint256[50] private __gap;
```

- *TestnetTierProvider.sol* ( [11-11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L11-L11) ):

```solidity
11:     uint256[50] private __gap;
```

- *CrossChainOwned.sol* ( [21-21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L21-L21) ):

```solidity
21:     uint256[49] private __gap;
```

- *TaikoL2.sol* ( [52-52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L52-L52) ):

```solidity
52:     uint256[47] private __gap;
```

- *TaikoL2EIP1559Configurable.sol* ( [13-13](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L13-L13) ):

```solidity
13:     uint256[49] private __gap;
```

- *Bridge.sol* ( [48-48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L48-L48) ):

```solidity
48:     uint256[43] private __gap;
```

- *AddressManager.sol* ( [14-14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L14-L14) ):

```solidity
14:     uint256[49] private __gap;
```

- *AddressResolver.sol* ( [14-14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L14-L14) ):

```solidity
14:     uint256[49] private __gap;
```

- *EssentialContract.sol* ( [25-25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L25-L25) ):

```solidity
25:     uint256[49] private __gap;
```

- *SignalService.sol* ( [23-23](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L23-L23) ):

```solidity
23:     uint256[48] private __gap;
```

- *TimelockTokenPool.sol* ( [82-82](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L82-L82) ):

```solidity
82:     uint128[44] private __gap;
```

- *ERC20Airdrop.sol* ( [18-18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L18-L18) ):

```solidity
18:     uint256[48] private __gap;
```

- *ERC20Airdrop2.sol* ( [30-30](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L30-L30) ):

```solidity
30:     uint256[45] private __gap;
```

- *ERC721Airdrop.sol* ( [16-16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L16-L16) ):

```solidity
16:     uint256[48] private __gap;
```

- *MerkleClaimable.sol* ( [23-23](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L23-L23) ):

```solidity
23:     uint256[47] private __gap;
```

- *BaseNFTVault.sol* ( [61-61](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L61-L61) ):

```solidity
61:     uint256[48] private __gap;
```

- *BaseVault.sol* ( [18-18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L18-L18) ):

```solidity
18:     uint256[50] private __gap;
```

- *BridgedERC1155.sol* ( [27-27](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L27-L27) ):

```solidity
27:     uint256[46] private __gap;
```

- *BridgedERC20.sol* ( [32-32](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L32-L32) ):

```solidity
32:     uint256[47] private __gap;
```

- *BridgedERC20Base.sol* ( [16-16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L16-L16) ):

```solidity
16:     uint256[49] private __gap;
```

- *BridgedERC721.sol* ( [19-19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L19-L19) ):

```solidity
19:     uint256[48] private __gap;
```

- *ERC1155Vault.sol* ( [32-32](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L32-L32) ):

```solidity
32:     uint256[50] private __gap;
```

- *ERC20Vault.sol* ( [54-54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L54-L54) ):

```solidity
54:     uint256[47] private __gap;
```

- *ERC721Vault.sol* ( [19-19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L19-L19) ):

```solidity
19:     uint256[50] private __gap;
```

- *USDCAdapter.sol* ( [32-32](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L32-L32) ):

```solidity
32:     uint256[49] private __gap;
```

- *GuardianVerifier.sol* ( [11-11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L11-L11) ):

```solidity
11:     uint256[50] private __gap;
```

- *SgxVerifier.sol* ( [57-57](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L57-L57) ):

```solidity
57:     uint256[47] private __gap;
```

</details>

### [G-22] Operator `>=`/`<=` costs less gas than operator `>`/`<`

The compiler uses opcodes `GT` and `ISZERO` for code that uses `>`, but only requires `LT` for `>=`. A similar behavior applies for `>`, which uses opcodes `LT` and `ISZERO`, but only requires `GT` for `<=`. It can [save **3 gas**](https://gist.github.com/IllIllI000/3dc79d25acccfa16dee4e83ffdc6ffde) for each.
It should be converted to the `<=`/`>=` equivalent when comparing against integer literals. In cases where a for-loop is being used, one can count down rather than up, in order to use the optimal operator.

<details>
<summary>There are 41 instances (click to show):</summary>

- *AssignmentHook.sol* ( [125-125](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L125-L125) ):

```solidity
125:         if (address(this).balance > 0) {
```

- *LibDepositing.sol* ( [150-150](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L150-L150) ):

```solidity
150:         if (_amount > type(uint96).max) revert L1_INVALID_ETH_DEPOSIT();
```

- *LibProposing.sol* ( [171-171](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L171-L171) ):

```solidity
171:             if (uint256(params.txListByteOffset) + params.txListByteSize > MAX_BYTES_PER_BLOB) {
```

- *LibProving.sol* ( [192-192](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L192-L192) ):

```solidity
192:             bool returnLivenessBond = blk.livenessBond > 0 && _proof.data.length == 32
```

- *LibVerifying.sol* ( [212-212](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L212-L212), [251-251](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L251-L251), [256-256](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L256-L256), [260-260](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L260-L260) ):

```solidity
212:             if (numBlocksVerified > 0) {

251:                 || _config.blockMaxTxListBytes > 128 * 1024 // calldata up to 128K

256:             || _config.ethDepositMaxCountPerBlock > 32

260:                 || _config.ethDepositMaxAmount > type(uint96).max || _config.ethDepositGas == 0
```

- *Guardians.sol* ( [63-63](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L63-L63), [63-63](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L63-L63) ):

```solidity
63:         if (_newGuardians.length < MIN_NUM_GUARDIANS || _newGuardians.length > type(uint8).max) {

63:         if (_newGuardians.length < MIN_NUM_GUARDIANS || _newGuardians.length > type(uint8).max) {
```

- *TaikoL2.sol* ( [82-82](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L82-L82), [234-234](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L234-L234), [262-262](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L262-L262), [275-275](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L275-L275), [279-279](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L279-L279) ):

```solidity
82:         if (block.chainid <= 1 || block.chainid > type(uint64).max) {

234:             for (uint256 i; i < 255 && _blockId >= i + 1; ++i) {

262:         if (gasExcess > 0) {

275:             if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {

279:             if (numL1Blocks > 0) {
```

- *AutomataDcapV3Attestation.sol* ( [240-240](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L240-L240), [420-420](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L420-L420) ):

```solidity
240:         for (uint256 i; i < CPUSVN_LENGTH; ++i) {

420:             for (uint256 i; i < 3; ++i) {
```

- *PEMCertChainLib.sol* ( [56-56](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L56-L56), [354-354](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L354-L354), [358-358](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L358-L358) ):

```solidity
56:             if (i > 0) {

354:         for (uint256 i; i < SGX_TCB_CPUSVN_SIZE + 1; ++i) {

358:             uint16 svnValue = svnValueBytes.length < 2
```

- *V3Parser.sol* ( [218-218](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L218-L218), [218-218](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L218-L218), [281-281](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L281-L281) ):

```solidity
218:         if (cert.certType < 1 || cert.certType > 5) {

218:         if (cert.certType < 1 || cert.certType > 5) {

281:         for (uint256 i; i < 3; ++i) {
```

- *BytesUtils.sol* ( [90-90](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L90-L90) ):

```solidity
90:                 if (shortest > 32) {
```

- *X509DateUtils.sol* ( [18-18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L18-L18) ):

```solidity
18:             if (uint8(x509Time[0]) - 48 < 5) yrs += 2000;
```

- *AddressResolver.sol* ( [59-59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L59-L59) ):

```solidity
59:         if (block.chainid > type(uint64).max) {
```

- *SignalService.sol* ( [120-120](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L120-L120) ):

```solidity
120:             bool isFullProof = hop.accountProof.length > 0;
```

- *TimelockTokenPool.sol* ( [275-275](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L275-L275), [277-277](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L277-L277) ):

```solidity
275:             if (_cliff > 0) revert INVALID_GRANT();

277:             if (_cliff > 0 && _cliff <= _start) revert INVALID_GRANT();
```

- *RLPReader.sol* ( [38-38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L38-L38), [153-153](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L153-L153), [213-213](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L213-L213), [259-259](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L259-L259) ):

```solidity
38:             _in.length > 0,

153:             _in.length > 0,

213:                 strLen > 55,

259:                 listLen > 55,
```

- *RLPWriter.sol* ( [14-14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L14-L14), [33-33](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L33-L33), [59-59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L59-L59) ):

```solidity
14:         if (_in.length == 1 && uint8(_in[0]) < 128) {

33:         if (_len < 56) {

59:         for (; i < 32; i++) {
```

- *MerkleTrie.sol* ( [77-77](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L77-L77), [120-120](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L120-L120), [173-173](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L173-L173), [221-221](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L221-L221) ):

```solidity
77:         require(_key.length > 0, "MerkleTrie: empty key");

120:                         value_.length > 0,

173:                         value_.length > 0,

221:         id_ = _node.length < 32 ? RLPReader.readRawBytes(_node) : RLPReader.readBytes(_node);
```

- *BaseNFTVault.sol* ( [145-145](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L145-L145) ):

```solidity
145:         if (_op.tokenIds.length > MAX_TOKEN_PER_TXN) {
```

</details>

### [G-23] Consider pre-calculating the address of `address(this)` to save gas

Use `foundry`'s [`script.sol`](https://book.getfoundry.sh/reference/forge-std/compute-create-address) or `solady`'s [`LibRlp.sol`](https://github.com/Vectorized/solady/blob/main/src/utils/LibRLP.sol) to save the value in a constant, which will avoid having to spend gas to push the value on the stack every time it's used.

<details>
<summary>There are 40 instances (click to show):</summary>

- *TaikoToken.sol* ( [61-61](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L61-L61), [79-79](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L79-L79) ):

```solidity
61:         if (_to == address(this)) revert TKO_INVALID_ADDR();

79:         if (_to == address(this)) revert TKO_INVALID_ADDR();
```

- *AssignmentHook.sol* ( [125-125](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L125-L125), [126-126](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L126-L126), [151-151](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L151-L151) ):

```solidity
125:         if (address(this).balance > 0) {

126:             taikoL1Address.sendEther(address(this).balance);

151:                 address(this),
```

- *LibProposing.sol* ( [238-238](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L238-L238), [253-253](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L253-L253), [260-260](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L260-L260), [261-261](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L261-L261), [268-268](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L268-L268) ):

```solidity
238:             uint256 tkoBalance = tko.balanceOf(address(this));

253:                 IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }(

260:             if (address(this).balance != 0) {

261:                 msg.sender.sendEther(address(this).balance);

268:             if (tko.balanceOf(address(this)) != tkoBalance + _config.livenessBond) {
```

- *LibProving.sol* ( [242-242](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L242-L242), [384-384](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L384-L384) ):

```solidity
242:                 tko.transferFrom(msg.sender, address(this), tier.contestBond);

384:                 _tko.transferFrom(msg.sender, address(this), _tier.validityBond - reward);
```

- *CrossChainOwned.sol* ( [50-50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L50-L50) ):

```solidity
50:         (bool success,) = address(this).call(txdata);
```

- *TaikoL2.sol* ( [174-174](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L174-L174), [176-176](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L176-L176) ):

```solidity
174:             _to.sendEther(address(this).balance);

176:             IERC20(_token).safeTransfer(_to, IERC20(_token).balanceOf(address(this)));
```

- *Bridge.sol* ( [174-174](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L174-L174), [196-196](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L196-L196), [270-270](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L270-L270), [343-343](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L343-L343), [486-486](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L486-L486) ):

```solidity
174:             if (!ISignalService(signalService).isSignalSent(address(this), msgHash)) {

196:                 _storeContext(msgHash, address(this), _message.srcChainId);

270:                 _message.to == address(0) || _message.to == address(this)

343:             _app: address(this),

486:         assert(_message.from != address(this));
```

- *SignalService.sol* ( [112-112](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L112-L112), [131-131](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L131-L131), [149-149](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L149-L149), [171-171](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L171-L171), [245-245](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L245-L245) ):

```solidity
112:                 signalService = address(this);

131:         if (value == 0 || value != _loadSignalValue(address(this), signal)) {

149:         return _loadSignalValue(address(this), signal) == _chainData;

171:             chainData_ = _loadSignalValue(address(this), signal);

245:         _sendSignal(address(this), signal_, _chainData);
```

- *BridgedERC1155.sol* ( [137-137](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L137-L137) ):

```solidity
137:         if (_to == address(this)) revert BTOKEN_CANNOT_RECEIVE();
```

- *BridgedERC20.sol* ( [147-147](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L147-L147) ):

```solidity
147:         if (_to == address(this)) revert BTOKEN_CANNOT_RECEIVE();
```

- *BridgedERC721.sol* ( [125-125](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L125-L125) ):

```solidity
125:         if (_to == address(this)) revert BTOKEN_CANNOT_RECEIVE();
```

- *ERC1155Vault.sol* ( [108-108](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L108-L108), [226-226](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L226-L226), [272-272](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L272-L272) ):

```solidity
108:         if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

226:             IERC1155(token).safeBatchTransferFrom(address(this), to, tokenIds, amounts, "");

272:                         to: address(this),
```

- *ERC20Vault.sol* ( [267-267](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L267-L267), [378-378](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L378-L378), [379-379](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L379-L379), [380-380](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L380-L380) ):

```solidity
267:         if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

378:             uint256 _balance = t.balanceOf(address(this));

379:             t.safeTransferFrom({ from: msg.sender, to: address(this), value: _amount });

380:             balanceChange_ = t.balanceOf(address(this)) - _balance;
```

- *ERC721Vault.sol* ( [91-91](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L91-L91), [171-171](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L171-L171), [211-211](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L211-L211) ):

```solidity
91:         if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

171:                 IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);

211:                     t.safeTransferFrom(_user, address(this), _op.tokenIds[i]);
```

- *USDCAdapter.sol* ( [48-48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L48-L48) ):

```solidity
48:         usdc.transferFrom(_from, address(this), _amount);
```

- *SgxVerifier.sol* ( [186-186](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L186-L186) ):

```solidity
186:                 address(this),
```

</details>

### [G-24] Empty code blocks can be removed to save gas

The following empty code blocks can be removed or refactored to save gas.

There is 1 instance:

- *TaikoL2.sol* ( [86-88](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L86-L88) ):

```solidity
86:         if (block.number == 0) {
87:             // This is the case in real L2 genesis
88:         } else if (block.number == 1) {
```

### [G-25] Remove empty functions to save gas

Empty function body in solidity is not recommended, remove it can save gas.

There are 4 instances:

- *TaikoL1.sol* ( [220](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L220) ):

```solidity
220:     function _authorizePause(address)
```

- *Bridge.sol* ( [461](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L461) ):

```solidity
461:     function _authorizePause(address)
```

- *EssentialContract.sol* ( [114](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L114), [116](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L116) ):

```solidity
114:     function _authorizeUpgrade(address) internal virtual override onlyOwner { }

116:     function _authorizePause(address) internal virtual onlyOwner { }
```

### [G-26] Usage of `int`s/`uint`s smaller than 32 bytes incurs overhead

Using `ints`/`uints` smaller than 32 bytes may cost more gas. This is because the EVM operates on 32 bytes at a time, so if an element is smaller than 32 bytes, the EVM must perform more operations to reduce the size of the element from 32 bytes to the desired size.

<details>
<summary>There are 323 instances (click to show):</summary>

- *ITaikoL1.sol* ( [27-27](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/ITaikoL1.sol#L27-L27), [31-31](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/ITaikoL1.sol#L31-L31) ):

```solidity
/// @audit uint64
27:     function proveBlock(uint64 _blockId, bytes calldata _input) external;

/// @audit uint64
31:     function verifyBlocks(uint64 _maxBlocksToVerify) external;
```

- *TaikoData.sol* ( [15-15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L15-L15), [20-20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L20-L20), [22-22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L22-L22), [24-24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L24-L24), [26-26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L26-L26), [28-28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L28-L28), [30-30](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L30-L30), [39-39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L39-L39), [46-46](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L46-L46), [48-48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L48-L48), [50-50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L50-L50), [52-52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L52-L52), [59-59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L59-L59), [64-64](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L64-L64), [65-65](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L65-L65), [69-69](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L69-L69), [83-83](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L83-L83), [84-84](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L84-L84), [101-101](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L101-L101), [102-102](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L102-L102), [103-103](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L103-L103), [104-104](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L104-L104), [105-105](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L105-L105), [106-106](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L106-L106), [107-107](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L107-L107), [127-127](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L127-L127), [129-129](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L129-L129), [130-130](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L130-L130), [131-131](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L131-L131), [132-132](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L132-L132), [140-140](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L140-L140), [141-141](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L141-L141), [142-142](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L142-L142), [143-143](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L143-L143), [144-144](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L144-L144), [145-145](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L145-L145), [152-152](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L152-L152), [153-153](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L153-L153), [162-162](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L162-L162), [163-163](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L163-L163), [164-164](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L164-L164), [165-165](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L165-L165), [169-169](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L169-L169), [170-170](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L170-L170), [172-172](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L172-L172), [173-173](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L173-L173), [174-174](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L174-L174), [175-175](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L175-L175) ):

```solidity
/// @audit uint64
15:         uint64 chainId;

/// @audit uint64
20:         uint64 blockMaxProposals;

/// @audit uint64
22:         uint64 blockRingBufferSize;

/// @audit uint64
24:         uint64 maxBlocksToVerifyPerProposal;

/// @audit uint32
26:         uint32 blockMaxGasLimit;

/// @audit uint24
28:         uint24 blockMaxTxListBytes;

/// @audit uint24
30:         uint24 blobExpiry;

/// @audit uint96
39:         uint96 livenessBond;

/// @audit uint64
46:         uint64 ethDepositMinCountPerBlock;

/// @audit uint64
48:         uint64 ethDepositMaxCountPerBlock;

/// @audit uint96
50:         uint96 ethDepositMinAmount;

/// @audit uint96
52:         uint96 ethDepositMaxAmount;

/// @audit uint8
59:         uint8 blockSyncThreshold;

/// @audit uint16
64:         uint16 tier;

/// @audit uint128
65:         uint128 fee;

/// @audit uint16
69:         uint16 tier;

/// @audit uint24
83:         uint24 txListByteOffset;

/// @audit uint24
84:         uint24 txListByteSize;

/// @audit uint64
101:         uint64 id;

/// @audit uint32
102:         uint32 gasLimit;

/// @audit uint64
103:         uint64 timestamp; // slot 7

/// @audit uint64
104:         uint64 l1Height;

/// @audit uint24
105:         uint24 txListByteOffset;

/// @audit uint24
106:         uint24 txListByteSize;

/// @audit uint16
107:         uint16 minTier;

/// @audit uint96
127:         uint96 validityBond;

/// @audit uint96
129:         uint96 contestBond;

/// @audit uint64
130:         uint64 timestamp; // slot 6 (90 bits)

/// @audit uint16
131:         uint16 tier;

/// @audit uint8
132:         uint8 contestations;

/// @audit uint96
140:         uint96 livenessBond;

/// @audit uint64
141:         uint64 blockId; // slot 3

/// @audit uint64
142:         uint64 proposedAt; // timestamp

/// @audit uint64
143:         uint64 proposedIn; // L1 block number

/// @audit uint32
144:         uint32 nextTransitionId;

/// @audit uint32
145:         uint32 verifiedTransitionId;

/// @audit uint96
152:         uint96 amount;

/// @audit uint64
153:         uint64 id;

/// @audit uint64
162:         uint64 genesisHeight;

/// @audit uint64
163:         uint64 genesisTimestamp;

/// @audit uint64
164:         uint64 numEthDeposits;

/// @audit uint64
165:         uint64 nextEthDepositToProcess;

/// @audit uint64
169:         uint64 numBlocks;

/// @audit uint64
170:         uint64 lastVerifiedBlockId;

/// @audit uint8
172:         uint8 __reserved1;

/// @audit uint16
173:         uint16 __reserved2;

/// @audit uint32
174:         uint32 __reserved3;

/// @audit uint64
175:         uint64 lastUnpausedAt;
```

- *TaikoEvents.sol* ( [24-24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoEvents.sol#L24-L24), [43-43](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoEvents.sol#L43-L43), [44-44](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoEvents.sol#L44-L44), [57-57](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoEvents.sol#L57-L57), [58-58](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoEvents.sol#L58-L58), [71-71](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoEvents.sol#L71-L71), [72-72](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoEvents.sol#L72-L72) ):

```solidity
/// @audit uint96
24:         uint96 livenessBond,

/// @audit uint16
43:         uint16 tier,

/// @audit uint8
44:         uint8 contestations

/// @audit uint96
57:         uint96 validityBond,

/// @audit uint16
58:         uint16 tier

/// @audit uint96
71:         uint96 contestBond,

/// @audit uint16
72:         uint16 tier
```

- *TaikoL1.sol* ( [76-76](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L76-L76), [94-94](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L94-L94), [100-100](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L100-L100), [145-145](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L145-L145), [150-150](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L150-L150), [163-163](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L163-L163) ):

```solidity
/// @audit uint64
76:         uint64 _blockId,

/// @audit uint8
94:         uint8 maxBlocksToVerify = LibProving.proveBlock(state, config, this, meta, tran, proof);

/// @audit uint64
100:     function verifyBlocks(uint64 _maxBlocksToVerify)

/// @audit uint64
145:     function getBlock(uint64 _blockId)

/// @audit uint64
150:         uint64 slot;

/// @audit uint64
163:         uint64 _blockId,
```

- *AssignmentHook.sol* ( [20-20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L20-L20), [21-21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L21-L21), [22-22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L22-L22), [166-166](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L166-L166) ):

```solidity
/// @audit uint64
20:         uint64 expiry;

/// @audit uint64
21:         uint64 maxBlockId;

/// @audit uint64
22:         uint64 maxProposedIn;

/// @audit uint16
166:         uint16 _tierId
```

- *LibDepositing.sol* ( [83-83](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L83-L83), [84-84](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L84-L84), [85-85](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L85-L85), [93-93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L93-L93) ):

```solidity
/// @audit uint96
83:             uint96 fee = uint96(_config.ethDepositMaxFee.min(block.basefee * _config.ethDepositGas));

/// @audit uint64
84:             uint64 j = _state.slotA.nextEthDepositToProcess;

/// @audit uint96
85:             uint96 totalFee;

/// @audit uint96
93:                 uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount;
```

- *LibProposing.sol* ( [34-34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L34-L34) ):

```solidity
/// @audit uint96
34:         uint96 livenessBond,
```

- *LibProving.sol* ( [36-36](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L36-L36), [37-37](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L37-L37), [50-50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L50-L50), [51-51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L51-L51), [100-100](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L100-L100), [115-115](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L115-L115), [129-129](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L129-L129), [273-273](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L273-L273), [276-276](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L276-L276), [405-405](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L405-L405) ):

```solidity
/// @audit uint96
36:         uint96 validityBond,

/// @audit uint16
37:         uint16 tier

/// @audit uint96
50:         uint96 contestBond,

/// @audit uint16
51:         uint16 tier

/// @audit uint8
100:         returns (uint8 maxBlocksToVerify_)

/// @audit uint64
115:         uint64 slot = _meta.id % _config.blockRingBufferSize;

/// @audit uint32
129:         (uint32 tid, TaikoData.TransitionState storage ts) =

/// @audit uint64
273:         uint64 slot

/// @audit uint32
276:         returns (uint32 tid_, TaikoData.TransitionState storage ts_)

/// @audit uint32
405:         uint32 _tid,
```

- *LibUtils.sol* ( [26-26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L26-L26), [38-38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L38-L38), [42-42](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L42-L42), [55-55](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L55-L55), [59-59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L59-L59), [73-73](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L73-L73), [78-78](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L78-L78) ):

```solidity
/// @audit uint64
26:         uint64 _blockId,

/// @audit uint64
38:         uint64 slot = _blockId % _config.blockRingBufferSize;

/// @audit uint32
42:         uint32 tid = getTransitionId(_state, blk, slot, _parentHash);

/// @audit uint64
55:         uint64 _blockId

/// @audit uint64
59:         returns (TaikoData.Block storage blk_, uint64 slot_)

/// @audit uint64
73:         uint64 _slot,

/// @audit uint32
78:         returns (uint32 tid_)
```

- *LibVerifying.sol* ( [34-34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L34-L34), [35-35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L35-L35), [89-89](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L89-L89), [100-100](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L100-L100), [102-102](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L102-L102), [107-107](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L107-L107), [117-117](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L117-L117), [213-213](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L213-L213), [227-227](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L227-L227), [234-234](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L234-L234) ):

```solidity
/// @audit uint16
34:         uint16 tier,

/// @audit uint8
35:         uint8 contestations

/// @audit uint64
89:         uint64 _maxBlocksToVerify

/// @audit uint64
100:         uint64 blockId = b.lastVerifiedBlockId;

/// @audit uint64
102:         uint64 slot = blockId % _config.blockRingBufferSize;

/// @audit uint32
107:         uint32 tid = blk.verifiedTransitionId;

/// @audit uint64
117:         uint64 numBlocksVerified;

/// @audit uint64
213:                 uint64 lastVerifiedBlockId = b.lastVerifiedBlockId + numBlocksVerified;

/// @audit uint64
227:         uint64 _lastVerifiedBlockId,

/// @audit uint64
234:         (uint64 lastSyncedBlock,) = signalService.getSyncedChainData(
```

- *Guardians.sol* ( [27-27](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L27-L27), [30-30](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L30-L30), [37-37](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L37-L37), [55-55](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L55-L55) ):

```solidity
/// @audit uint32
27:     uint32 public version;

/// @audit uint32
30:     uint32 public minGuardians;

/// @audit uint32
37:     event GuardiansUpdated(uint32 version, address[] guardians);

/// @audit uint8
55:         uint8 _minGuardians
```

- *DevnetTierProvider.sol* ( [20-20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L20-L20), [54-54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L54-L54) ):

```solidity
/// @audit uint16
20:     function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {

/// @audit uint16
54:     function getMinTier(uint256) public pure override returns (uint16) {
```

- *ITierProvider.sol* ( [10-10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L10-L10), [11-11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L11-L11), [12-12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L12-L12), [13-13](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L13-L13), [14-14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L14-L14), [22-22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L22-L22), [33-33](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L33-L33), [39-39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L39-L39), [42-42](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L42-L42), [45-45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L45-L45), [48-48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L48-L48) ):

```solidity
/// @audit uint96
10:         uint96 validityBond;

/// @audit uint96
11:         uint96 contestBond;

/// @audit uint24
12:         uint24 cooldownWindow; // in minutes

/// @audit uint16
13:         uint16 provingWindow; // in minutes

/// @audit uint8
14:         uint8 maxBlocksToVerifyPerProof;

/// @audit uint16
22:     function getTier(uint16 tierId) external view returns (Tier memory);

/// @audit uint16
33:     function getMinTier(uint256 rand) external view returns (uint16);

/// @audit uint16
39:     uint16 public constant TIER_OPTIMISTIC = 100;

/// @audit uint16
42:     uint16 public constant TIER_SGX = 200;

/// @audit uint16
45:     uint16 public constant TIER_SGX_ZKVM = 300;

/// @audit uint16
48:     uint16 public constant TIER_GUARDIAN = 1000;
```

- *MainnetTierProvider.sol* ( [20-20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L20-L20), [66-66](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L66-L66) ):

```solidity
/// @audit uint16
20:     function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {

/// @audit uint16
66:     function getMinTier(uint256 _rand) public pure override returns (uint16) {
```

- *TestnetTierProvider.sol* ( [20-20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L20-L20), [66-66](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L66-L66) ):

```solidity
/// @audit uint16
20:     function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {

/// @audit uint16
66:     function getMinTier(uint256 _rand) public pure override returns (uint16) {
```

- *CrossChainOwned.sol* ( [16-16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L16-L16), [19-19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L19-L19), [26-26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L26-L26), [42-42](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L42-L42), [63-63](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L63-L63) ):

```solidity
/// @audit uint64
16:     uint64 public ownerChainId;

/// @audit uint64
19:     uint64 public nextTxId;

/// @audit uint64
26:     event TransactionExecuted(uint64 indexed txId, bytes4 indexed selector);

/// @audit uint64
42:         (uint64 txId, bytes memory txdata) = abi.decode(_data, (uint64, bytes));

/// @audit uint64
63:         uint64 _ownerChainId
```

- *TaikoL2.sol* ( [27-27](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L27-L27), [28-28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L28-L28), [35-35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L35-L35), [47-47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L47-L47), [50-50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L50-L50), [57-57](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L57-L57), [74-74](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L74-L74), [75-75](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L75-L75), [110-110](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L110-L110), [111-111](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L111-L111), [186-186](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L186-L186), [187-187](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L187-L187), [200-200](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L200-L200), [254-254](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L254-L254), [255-255](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L255-L255), [259-259](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L259-L259) ):

```solidity
/// @audit uint32
27:         uint32 gasTargetPerL1Block;

/// @audit uint8
28:         uint8 basefeeAdjustmentQuotient;

/// @audit uint8
35:     uint8 public constant BLOCK_SYNC_THRESHOLD = 5;

/// @audit uint64
47:     uint64 public gasExcess;

/// @audit uint64
50:     uint64 public lastSyncedBlock;

/// @audit uint64
57:     event Anchored(bytes32 parentHash, uint64 gasExcess);

/// @audit uint64
74:         uint64 _l1ChainId,

/// @audit uint64
75:         uint64 _gasExcess

/// @audit uint64
110:         uint64 _l1BlockId,

/// @audit uint32
111:         uint32 _parentGasUsed

/// @audit uint64
186:         uint64 _l1BlockId,

/// @audit uint32
187:         uint32 _parentGasUsed

/// @audit uint64
200:     function getBlockHash(uint64 _blockId) public view returns (bytes32) {

/// @audit uint64
254:         uint64 _l1BlockId,

/// @audit uint32
255:         uint32 _parentGasUsed

/// @audit uint64
259:         returns (uint256 basefee_, uint64 gasExcess_)
```

- *TaikoL2EIP1559Configurable.sol* ( [18-18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L18-L18), [27-27](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L27-L27) ):

```solidity
/// @audit uint64
18:     event ConfigAndExcessChanged(Config config, uint64 gasExcess);

/// @audit uint64
27:         uint64 _newGasExcess
```

- *AutomataDcapV3Attestation.sol* ( [36-36](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L36-L36) ):

```solidity
/// @audit uint8
36:     uint8 internal constant INVALID_EXIT_CODE = 255;
```

- *EnclaveIdStruct.sol* ( [10-10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/EnclaveIdStruct.sol#L10-L10), [23-23](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/EnclaveIdStruct.sol#L23-L23) ):

```solidity
/// @audit uint16
10:         uint16 isvprodid;

/// @audit uint16
23:         uint16 isvsvn;
```

- *PEMCertChainLib.sol* ( [358-358](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L358-L358) ):

```solidity
/// @audit uint16
358:             uint16 svnValue = svnValueBytes.length < 2
```

- *V3Parser.sol* ( [106-106](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L106-L106), [249-249](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L249-L249), [250-250](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L250-L250) ):

```solidity
/// @audit uint32
106:         uint32 totalQuoteSize = 48 // header

/// @audit uint16
249:         uint16 isvProdIdPackBE = (enclaveReport.isvProdId >> 8) | (enclaveReport.isvProdId << 8);

/// @audit uint16
250:         uint16 isvSvnPackBE = (enclaveReport.isvSvn >> 8) | (enclaveReport.isvSvn << 8);
```

- *V3Struct.sol* ( [26-26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L26-L26), [27-27](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L27-L27), [34-34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L34-L34), [39-39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L39-L39), [43-43](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L43-L43) ):

```solidity
/// @audit uint16
26:         uint16 isvProdId;

/// @audit uint16
27:         uint16 isvSvn;

/// @audit uint16
34:         uint16 parsedDataSize;

/// @audit uint16
39:         uint16 certType;

/// @audit uint32
43:         uint32 certDataSize;
```

- *Asn1Decode.sol* ( [189-189](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L189-L189), [190-190](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L190-L190), [196-196](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L196-L196) ):

```solidity
/// @audit uint80
189:         uint80 ixFirstContentByte;

/// @audit uint80
190:         uint80 ixLastContentByte;

/// @audit uint8
196:             uint8 lengthbytesLength = uint8(der[ix + 1] & 0x7F);
```

- *BytesUtils.sol* ( [188-188](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L188-L188), [198-198](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L198-L198), [211-211](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L211-L211), [332-332](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L332-L332) ):

```solidity
/// @audit uint8
188:     function readUint8(bytes memory self, uint256 idx) internal pure returns (uint8 ret) {

/// @audit uint16
198:     function readUint16(bytes memory self, uint256 idx) internal pure returns (uint16 ret) {

/// @audit uint32
211:     function readUint32(bytes memory self, uint256 idx) internal pure returns (uint32 ret) {

/// @audit uint8
332:         uint8 decoded;
```

- *X509DateUtils.sol* ( [9-9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L9-L9), [10-10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L10-L10), [11-11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L11-L11), [12-12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L12-L12), [13-13](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L13-L13), [14-14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L14-L14), [15-15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L15-L15), [35-35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L35-L35), [36-36](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L36-L36), [37-37](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L37-L37), [38-38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L38-L38), [39-39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L39-L39), [40-40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L40-L40), [48-48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L48-L48), [59-59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L59-L59), [71-71](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L71-L71) ):

```solidity
/// @audit uint16
9:         uint16 yrs;

/// @audit uint8
10:         uint8 mnths;

/// @audit uint8
11:         uint8 dys;

/// @audit uint8
12:         uint8 hrs;

/// @audit uint8
13:         uint8 mins;

/// @audit uint8
14:         uint8 secs;

/// @audit uint8
15:         uint8 offset;

/// @audit uint16
35:         uint16 year,

/// @audit uint8
36:         uint8 month,

/// @audit uint8
37:         uint8 day,

/// @audit uint8
38:         uint8 hour,

/// @audit uint8
39:         uint8 minute,

/// @audit uint8
40:         uint8 second

/// @audit uint16
48:         for (uint16 i = 1970; i < year; ++i) {

/// @audit uint8
59:         for (uint8 i = 1; i < month; ++i) {

/// @audit uint16
71:     function isLeapYear(uint16 year) internal pure returns (bool) {
```

- *Bridge.sol* ( [31-31](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L31-L31), [64-64](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L64-L64), [89-89](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L89-L89), [168-168](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L168-L168), [230-230](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L230-L230), [392-392](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L392-L392), [541-541](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L541-L541), [559-559](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L559-L559), [580-580](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L580-L580) ):

```solidity
/// @audit uint128
31:     uint128 public nextMessageId;

/// @audit uint64
64:     modifier sameChain(uint64 _chainId) {

/// @audit uint64
89:         uint64 _timestamp = _suspend ? type(uint64).max : uint64(block.timestamp);

/// @audit uint64
168:         uint64 receivedAt = proofReceipt[msgHash].receivedAt;

/// @audit uint64
230:         uint64 receivedAt = proofReceipt[msgHash].receivedAt;

/// @audit uint64
392:     function isDestChainEnabled(uint64 _chainId)

/// @audit uint64
541:     function _storeContext(bytes32 _msgHash, address _from, uint64 _srcChainId) private {

/// @audit uint64
559:             uint64 srcChainId;

/// @audit uint64
580:         uint64 _chainId,
```

- *IBridge.sol* ( [19-19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/IBridge.sol#L19-L19), [24-24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/IBridge.sol#L24-L24), [26-26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/IBridge.sol#L26-L26), [51-51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/IBridge.sol#L51-L51), [63-63](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/IBridge.sol#L63-L63) ):

```solidity
/// @audit uint128
19:         uint128 id;

/// @audit uint64
24:         uint64 srcChainId;

/// @audit uint64
26:         uint64 destChainId;

/// @audit uint64
51:         uint64 receivedAt;

/// @audit uint64
63:         uint64 srcChainId; // Source chain ID.
```

- *AddressManager.sol* ( [22-22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L22-L22), [39-39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L39-L39), [54-54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L54-L54) ):

```solidity
/// @audit uint64
22:         uint64 indexed chainId, bytes32 indexed name, address newAddress, address oldAddress

/// @audit uint64
39:         uint64 _chainId,

/// @audit uint64
54:     function getAddress(uint64 _chainId, bytes32 _name) public view override returns (address) {
```

- *AddressResolver.sol* ( [19-19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L19-L19), [44-44](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L44-L44), [73-73](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L73-L73) ):

```solidity
/// @audit uint64
19:     error RESOLVER_ZERO_ADDR(uint64 chainId, bytes32 name);

/// @audit uint64
44:         uint64 _chainId,

/// @audit uint64
73:         uint64 _chainId,
```

- *EssentialContract.sol* ( [11-11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L11-L11), [13-13](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L13-L13), [21-21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L21-L21), [23-23](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L23-L23), [119-119](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L119-L119), [130-130](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L130-L130) ):

```solidity
/// @audit uint8
11:     uint8 private constant _FALSE = 1;

/// @audit uint8
13:     uint8 private constant _TRUE = 2;

/// @audit uint8
21:     uint8 private __reentry;

/// @audit uint8
23:     uint8 private __paused;

/// @audit uint8
119:     function _storeReentryLock(uint8 _reentry) internal virtual {

/// @audit uint8
130:     function _loadReentryLock() internal view virtual returns (uint8 reentry_) {
```

</details>

### [G-27] Using a double `if` statement instead of a logical AND(`&&`)

Using a double `if` statement instead of a logical AND (`&&`) can provide similar short-circuiting behavior whereas double if is slightly [more gas efficient](https://gist.github.com/DadeKuma/931ce6794a050201ec6544dbcc31316c).

<details>
<summary>There are 16 instances (click to show):</summary>

- *AssignmentHook.sol* ( [120-120](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L120-L120) ):

```solidity
120:         if (input.tip != 0 && block.coinbase != address(0)) {
```

- *LibProposing.sol* ( [108-108](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L108-L108), [164-164](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L164-L164), [310-310](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L310-L310) ):

```solidity
108:         if (params.parentMetaHash != 0 && parentMetaHash != params.parentMetaHash) {

164:                 if (_config.blobReuseEnabled && params.cacheBlobForReuse) {

310:             if (proposerOne != address(0) && msg.sender != proposerOne) {
```

- *TaikoL2.sol* ( [141-141](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L141-L141), [275-275](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L275-L275) ):

```solidity
141:         if (!skipFeeCheck() && block.basefee != basefee) {

275:             if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {
```

- *AutomataDcapV3Attestation.sol* ( [220-220](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L220-L220) ):

```solidity
220:             if (pceSvnIsHigherOrGreater && cpuSvnsAreHigherOrGreater) {
```

- *Bridge.sol* ( [250-250](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L250-L250), [260-260](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L260-L260) ):

```solidity
250:         if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) {

260:             if (_message.gasLimit == 0 && msg.sender != _message.destOwner) {
```

- *AddressResolver.sol* ( [85-85](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L85-L85) ):

```solidity
85:         if (!_allowZeroAddress && addr_ == address(0)) {
```

- *EssentialContract.sol* ( [42-42](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L42-L42) ):

```solidity
42:         if (msg.sender != owner() && msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();
```

- *SignalService.sol* ( [285-285](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L285-L285), [293-293](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L293-L293) ):

```solidity
285:         if (cacheStateRoot && _isFullProof && !_isLastHop) {

293:         if (cacheSignalRoot && (_isFullProof || !_isLastHop)) {
```

- *TimelockTokenPool.sol* ( [277-277](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L277-L277) ):

```solidity
277:             if (_cliff > 0 && _cliff <= _start) revert INVALID_GRANT();
```

- *BridgedERC20.sol* ( [38-38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L38-L38) ):

```solidity
38:         if (msg.sender != owner() && msg.sender != snapshooter) {
```

- *BridgedERC20Base.sol* ( [45-45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L45-L45) ):

```solidity
45:         if (_migratingAddress == migratingAddress && _migratingInbound == migratingInbound) {
```

</details>

### [G-28] `require()`/`revert()` strings longer than 32 bytes cost extra gas

Each extra memory word of bytes past the original 32 [incurs an MSTORE](https://gist.github.com/hrkrshnn/ee8fabd532058307229d65dcd5836ddc#consider-having-short-revert-strings) which costs **3 gas**

<details>
<summary>There are 30 instances (click to show):</summary>

- *V3Parser.sol* ( [87-90](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L87-L90) ):

```solidity
87:         require(
88:             v3Quote.v3AuthData.certification.certType == 5,
89:             "certType must be 5: Concatenated PCK Cert Chain (PEM formatted)"
90:         );
```

- *RLPReader.sol* ( [37-40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L37-L40), [56-59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L56-L59), [61-64](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L61-L64), [112-115](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L112-L115), [117-120](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L117-L120), [152-155](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L152-L155), [172-175](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L172-L175), [182-185](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L182-L185), [192-195](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L192-L195), [202-205](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L202-L205), [212-215](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L212-L215), [217-220](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L217-L220), [228-231](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L228-L231), [238-241](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L238-L241), [248-251](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L248-L251), [258-261](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L258-L261), [263-266](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L263-L266) ):

```solidity
37:         require(
38:             _in.length > 0,
39:             "RLPReader: length of an RLP item must be greater than zero to be decodable"
40:         );

56:         require(
57:             itemType == RLPItemType.LIST_ITEM,
58:             "RLPReader: decoded item type for list is not a list item"
59:         );

61:         require(
62:             listOffset + listLength == _in.length,
63:             "RLPReader: list item has an invalid data remainder"
64:         );

112:         require(
113:             itemType == RLPItemType.DATA_ITEM,
114:             "RLPReader: decoded item type for bytes is not a data item"
115:         );

117:         require(
118:             _in.length == itemOffset + itemLength,
119:             "RLPReader: bytes value contains an invalid remainder"
120:         );

152:         require(
153:             _in.length > 0,
154:             "RLPReader: length of an RLP item must be greater than zero to be decodable"
155:         );

172:             require(
173:                 _in.length > strLen,
174:                 "RLPReader: length of content must be greater than string length (short string)"
175:             );

182:             require(
183:                 strLen != 1 || firstByteOfContent >= 0x80,
184:                 "RLPReader: invalid prefix, single byte < 0x80 are not prefixed (short string)"
185:             );

192:             require(
193:                 _in.length > lenOfStrLen,
194:                 "RLPReader: length of content must be > than length of string length (long string)"
195:             );

202:             require(
203:                 firstByteOfContent != 0x00,
204:                 "RLPReader: length of content must not have any leading zeros (long string)"
205:             );

212:             require(
213:                 strLen > 55,
214:                 "RLPReader: length of content must be greater than 55 bytes (long string)"
215:             );

217:             require(
218:                 _in.length > lenOfStrLen + strLen,
219:                 "RLPReader: length of content must be greater than total length (long string)"
220:             );

228:             require(
229:                 _in.length > listLen,
230:                 "RLPReader: length of content must be greater than list length (short list)"
231:             );

238:             require(
239:                 _in.length > lenOfListLen,
240:                 "RLPReader: length of content must be > than length of list length (long list)"
241:             );

248:             require(
249:                 firstByteOfContent != 0x00,
250:                 "RLPReader: length of content must not have any leading zeros (long list)"
251:             );

258:             require(
259:                 listLen > 55,
260:                 "RLPReader: length of content must be greater than 55 bytes (long list)"
261:             );

263:             require(
264:                 _in.length > lenOfListLen + listLen,
265:                 "RLPReader: length of content must be greater than total length (long list)"
266:             );
```

- *MerkleTrie.sol* ( [89-89](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L89-L89), [99-102](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L99-L102), [105-108](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L105-L108), [119-122](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L119-L122), [125-128](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L125-L128), [150-153](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L150-L153), [162-165](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L162-L165), [172-175](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L172-L175), [178-181](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L178-L181), [191-191](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L191-L191), [194-194](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L194-L194), [198-198](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L198-L198) ):

```solidity
89:             require(currentKeyIndex <= key.length, "MerkleTrie: key index exceeds total key length");

99:                 require(
100:                     Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
101:                     "MerkleTrie: invalid large internal hash"
102:                 );

105:                 require(
106:                     Bytes.equal(currentNode.encoded, currentNodeID),
107:                     "MerkleTrie: invalid internal node hash"
108:                 );

119:                     require(
120:                         value_.length > 0,
121:                         "MerkleTrie: value length must be greater than zero (branch)"
122:                     );

125:                     require(
126:                         i == proof.length - 1,
127:                         "MerkleTrie: value node must be last node in proof (branch)"
128:                     );

150:                 require(
151:                     pathRemainder.length == sharedNibbleLength,
152:                     "MerkleTrie: path remainder must share all nibbles with key"
153:                 );

162:                     require(
163:                         keyRemainder.length == sharedNibbleLength,
164:                         "MerkleTrie: key remainder must be identical to path remainder"
165:                     );

172:                     require(
173:                         value_.length > 0,
174:                         "MerkleTrie: value length must be greater than zero (leaf)"
175:                     );

178:                     require(
179:                         i == proof.length - 1,
180:                         "MerkleTrie: value node must be last node in proof (leaf)"
181:                     );

191:                     revert("MerkleTrie: received a node with an unknown prefix");

194:                 revert("MerkleTrie: received an unparseable node");

198:         revert("MerkleTrie: ran out of proof elements");
```

</details>

### [G-29] Reduce deployment costs by tweaking contracts' metadata

See [this](https://www.rareskills.io/post/solidity-metadata) link, at its bottom, for full details.

<details>
<summary>There are 30 instances (click to show):</summary>

- *TaikoL1.sol* ( [22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L22) ):

```solidity
22: contract TaikoL1 is EssentialContract, ITaikoL1, TaikoEvents, TaikoErrors {
```

- *TaikoToken.sol* ( [15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L15) ):

```solidity
15: contract TaikoToken is EssentialContract, ERC20SnapshotUpgradeable, ERC20VotesUpgradeable {
```

- *TaikoGovernor.sol* ( [16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L16) ):

```solidity
16: contract TaikoGovernor is
```

- *TaikoTimelockController.sol* ( [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L9) ):

```solidity
9: contract TaikoTimelockController is EssentialContract, TimelockControllerUpgradeable {
```

- *AssignmentHook.sol* ( [14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L14) ):

```solidity
14: contract AssignmentHook is EssentialContract, IHook {
```

- *GuardianProver.sol* ( [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/GuardianProver.sol#L10) ):

```solidity
10: contract GuardianProver is Guardians {
```

- *DevnetTierProvider.sol* ( [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L10) ):

```solidity
10: contract DevnetTierProvider is EssentialContract, ITierProvider {
```

- *MainnetTierProvider.sol* ( [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L10) ):

```solidity
10: contract MainnetTierProvider is EssentialContract, ITierProvider {
```

- *TestnetTierProvider.sol* ( [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L10) ):

```solidity
10: contract TestnetTierProvider is EssentialContract, ITierProvider {
```

- *TaikoL2.sol* ( [21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L21) ):

```solidity
21: contract TaikoL2 is CrossChainOwned {
```

- *TaikoL2EIP1559Configurable.sol* ( [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L9) ):

```solidity
9: contract TaikoL2EIP1559Configurable is TaikoL2 {
```

- *AutomataDcapV3Attestation.sol* ( [22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L22) ):

```solidity
22: contract AutomataDcapV3Attestation is IAttestation {
```

- *PEMCertChainLib.sol* ( [12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L12) ):

```solidity
12: contract PEMCertChainLib is IPEMCertChainLib {
```

- *SigVerifyLib.sol* ( [15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L15) ):

```solidity
15: contract SigVerifyLib is ISigVerifyLib {
```

- *Bridge.sol* ( [16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L16) ):

```solidity
16: contract Bridge is EssentialContract, IBridge {
```

- *AddressManager.sol* ( [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L10) ):

```solidity
10: contract AddressManager is EssentialContract, IAddressManager {
```

- *SignalService.sol* ( [14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L14) ):

```solidity
14: contract SignalService is EssentialContract, ISignalService {
```

- *TimelockTokenPool.sol* ( [25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L25) ):

```solidity
25: contract TimelockTokenPool is EssentialContract {
```

- *ERC20Airdrop.sol* ( [11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L11) ):

```solidity
11: contract ERC20Airdrop is MerkleClaimable {
```

- *ERC20Airdrop2.sol* ( [12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L12) ):

```solidity
12: contract ERC20Airdrop2 is MerkleClaimable {
```

- *ERC721Airdrop.sol* ( [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L9) ):

```solidity
9: contract ERC721Airdrop is MerkleClaimable {
```

- *BridgedERC1155.sol* ( [14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L14) ):

```solidity
14: contract BridgedERC1155 is EssentialContract, IERC1155MetadataURIUpgradeable, ERC1155Upgradeable {
```

- *BridgedERC20.sol* ( [15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L15) ):

```solidity
15: contract BridgedERC20 is
```

- *BridgedERC721.sol* ( [12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L12) ):

```solidity
12: contract BridgedERC721 is EssentialContract, ERC721Upgradeable {
```

- *ERC1155Vault.sol* ( [29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L29) ):

```solidity
29: contract ERC1155Vault is BaseNFTVault, ERC1155ReceiverUpgradeable {
```

- *ERC20Vault.sol* ( [18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L18) ):

```solidity
18: contract ERC20Vault is BaseVault {
```

- *ERC721Vault.sol* ( [16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L16) ):

```solidity
16: contract ERC721Vault is BaseNFTVault, IERC721Receiver {
```

- *USDCAdapter.sol* ( [28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L28) ):

```solidity
28: contract USDCAdapter is BridgedERC20Base {
```

- *GuardianVerifier.sol* ( [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L10) ):

```solidity
10: contract GuardianVerifier is EssentialContract, IVerifier {
```

- *SgxVerifier.sol* ( [19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L19) ):

```solidity
19: contract SgxVerifier is EssentialContract, IVerifier {
```

</details>

### [G-30] Divisions can be unchecked to save gas

The expression `type(int).min/(-1)` is the only case where division causes an overflow. Therefore, uncheck can be used to [save gas](https://gist.github.com/DadeKuma/3bc597338ae774b8b3bd43280d55271f) in scenarios where it is certain that such an overflow will not occur.

<details>
<summary>There are 13 instances (click to show):</summary>

- *TaikoL1.sol* ( [215-215](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L215-L215) ):

```solidity
215:             ethDepositMaxFee: 1 ether / 10,
```

- *TaikoGovernor.sol* ( [124-124](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L124-L124) ):

```solidity
124:         return 1_000_000_000 ether / 10_000; // 0.01% of Taiko Token
```

- *LibVerifying.sol* ( [262-262](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L262-L262) ):

```solidity
262:                 || _config.ethDepositMaxFee > type(uint96).max / _config.ethDepositMaxCountPerBlock
```

- *Lib1559Math.sol* ( [28-28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/Lib1559Math.sol#L28-L28), [28-29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/Lib1559Math.sol#L28-L29), [41-41](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/Lib1559Math.sol#L41-L41) ):

```solidity
28:         return _ethQty(_gasExcess, _adjustmentFactor) / LibFixedPointMath.SCALING_FACTOR

28:         return _ethQty(_gasExcess, _adjustmentFactor) / LibFixedPointMath.SCALING_FACTOR
29:             / _adjustmentFactor;

41:         uint256 input = _gasExcess * LibFixedPointMath.SCALING_FACTOR / _adjustmentFactor;
```

- *PEMCertChainLib.sol* ( [359-359](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L359-L359) ):

```solidity
359:                 ? uint16(bytes2(svnValueBytes)) / 256
```

- *V3Parser.sol* ( [155-155](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L155-L155) ):

```solidity
155:             uint256 upperDigit = digits / 16;
```

- *TimelockTokenPool.sol* ( [197-197](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L197-L197), [264-264](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L264-L264) ):

```solidity
197:         uint128 _amountUnlocked = amountUnlocked / 1e18; // divide first

264:         return _amount * uint64(block.timestamp - _start) / _period;
```

- *ERC20Airdrop2.sol* ( [117-118](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L117-L118) ):

```solidity
117:         uint256 timeBasedAllowance = balance
118:             * (block.timestamp.min(claimEnd + withdrawalWindow) - claimEnd) / withdrawalWindow;
```

- *RLPWriter.sol* ( [39-39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L39-L39), [47-47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L47-L47) ):

```solidity
39:             while (_len / i != 0) {

47:                 out_[i] = bytes1(uint8((_len / (256 ** (lenLen - i))) % 256));
```

</details>

### [G-31] Use assembly to validate `msg.sender`

We can use assembly to efficiently validate msg.sender with the least amount of opcodes necessary. For more details check the following report [Here](https://code4rena.com/reports/2023-05-juicebox#g-06-use-assembly-to-validate-msgsender)

<details>
<summary>There are 22 instances (click to show):</summary>

- *LibProposing.sol* ( [310-310](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L310-L310), [316-316](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L316-L316) ):

```solidity
310:             if (proposerOne != address(0) && msg.sender != proposerOne) {

316:         return proposer == address(0) || msg.sender == proposer;
```

- *LibProving.sol* ( [416-416](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L416-L416) ):

```solidity
416:         bool isAssignedPover = msg.sender == _blk.assignedProver;
```

- *TaikoL2.sol* ( [123-123](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L123-L123) ):

```solidity
123:         if (msg.sender != GOLDEN_TOUCH_ADDRESS) revert L2_INVALID_SENDER();
```

- *AutomataDcapV3Attestation.sol* ( [61-61](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L61-L61) ):

```solidity
61:         require(msg.sender == owner, "onlyOwner");
```

- *Bridge.sol* ( [250-250](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L250-L250), [260-260](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L260-L260), [280-280](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L280-L280), [294-294](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L294-L294), [322-322](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L322-L322) ):

```solidity
250:         if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) {

260:             if (_message.gasLimit == 0 && msg.sender != _message.destOwner) {

280:                 uint256 gasLimit = msg.sender == _message.destOwner ? gasleft() : _message.gasLimit;

294:             if (msg.sender == refundTo) {

322:             if (msg.sender != _message.destOwner) revert B_PERMISSION_DENIED();
```

- *AddressResolver.sol* ( [25-25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L25-L25) ):

```solidity
25:         if (msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();
```

- *EssentialContract.sol* ( [42-42](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L42-L42), [42-42](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L42-L42) ):

```solidity
42:         if (msg.sender != owner() && msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();

42:         if (msg.sender != owner() && msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();
```

- *LibAddress.sol* ( [78-78](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L78-L78) ):

```solidity
78:         return msg.sender == tx.origin;
```

- *BaseVault.sol* ( [23-23](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L23-L23), [65-65](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L65-L65) ):

```solidity
23:         if (msg.sender != resolve("bridge", false)) {

65:         if (ctx_.from != msg.sender) revert VAULT_PERMISSION_DENIED();
```

- *BridgedERC20.sol* ( [38-38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L38-L38), [38-38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L38-L38) ):

```solidity
38:         if (msg.sender != owner() && msg.sender != snapshooter) {

38:         if (msg.sender != owner() && msg.sender != snapshooter) {
```

- *BridgedERC20Base.sol* ( [61-61](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L61-L61), [64-64](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L64-L64), [78-78](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L78-L78), [83-83](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L83-L83) ):

```solidity
61:         if (msg.sender == migratingAddress) {

64:         } else if (msg.sender != resolve("erc20_vault", true)) {

78:             if (msg.sender != _account) revert BB_PERMISSION_DENIED();

83:         } else if (msg.sender != resolve("erc20_vault", true)) {
```

</details>

### [G-32] Using assembly to check for zero can save gas

Using assembly to check for zero can save gas by allowing more direct access to the evm and reducing some of the overhead associated with high-level operations in solidity.

<details>
<summary>There are 93 instances (click to show):</summary>

- *TaikoL1.sol* ( [153-153](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L153-L153) ):

```solidity
153:         if (blk_.verifiedTransitionId != 0) {
```

- *AssignmentHook.sol* ( [109-109](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L109-L109) ):

```solidity
109:         if (assignment.feeToken == address(0)) {
```

- *LibDepositing.sol* ( [44-44](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L44-L44) ):

```solidity
44:         address recipient_ = _recipient == address(0) ? msg.sender : _recipient;
```

- *LibProposing.sol* ( [81-81](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L81-L81), [85-85](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L85-L85), [144-144](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L144-L144), [159-159](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L159-L159), [185-185](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L185-L185), [260-260](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L260-L260) ):

```solidity
81:         if (params.assignedProver == address(0)) {

85:         if (params.coinbase == address(0)) {

144:             if (params.blobHash != 0) {

159:                 if (meta_.blobHash == 0) revert L1_BLOB_NOT_FOUND();

185:             if (params.txListByteOffset != 0) {

260:             if (address(this).balance != 0) {
```

- *LibProving.sol* ( [163-163](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L163-L163), [239-239](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L239-L239), [280-280](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L280-L280), [363-363](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L363-L363), [412-412](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L412-L412) ):

```solidity
163:             if (verifier != address(0)) {

239:                 if (ts.contester != address(0)) revert L1_ALREADY_CONTESTED();

280:         if (tid_ == 0) {

363:         if (_ts.contester != address(0)) {

412:         if (_tier.contestBond == 0) return;
```

- *LibUtils.sol* ( [43-43](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L43-L43) ):

```solidity
43:         if (tid == 0) revert L1_TRANSITION_NOT_FOUND();
```

- *LibVerifying.sol* ( [93-93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L93-L93), [111-111](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L111-L111), [137-137](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L137-L137), [145-145](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L145-L145), [148-148](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L148-L148) ):

```solidity
93:         if (_maxBlocksToVerify == 0) {

111:         if (tid == 0) revert L1_TRANSITION_ID_ZERO();

137:                 if (tid == 0) break;

145:                 if (ts.contester != address(0)) {

148:                     if (tierProvider == address(0)) {
```

- *Guardians.sol* ( [82-82](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L82-L82), [84-84](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L84-L84), [113-113](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L113-L113) ):

```solidity
82:             if (guardian == address(0)) revert INVALID_GUARDIAN();

84:             if (guardianIds[guardian] != 0) revert INVALID_GUARDIAN_SET();

113:         if (id == 0) revert INVALID_GUARDIAN();
```

- *MainnetTierProvider.sol* ( [68-68](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L68-L68) ):

```solidity
68:         if (_rand % 1000 == 0) return LibTiers.TIER_SGX_ZKVM;
```

- *TestnetTierProvider.sol* ( [68-68](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L68-L68) ):

```solidity
68:         if (_rand % 10 == 0) return LibTiers.TIER_SGX;
```

- *Lib1559Math.sol* ( [24-24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/Lib1559Math.sol#L24-L24) ):

```solidity
24:         if (_adjustmentFactor == 0) {
```

- *TaikoL2.sol* ( [86-86](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L86-L86), [172-172](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L172-L172), [173-173](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L173-L173), [296-296](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L296-L296) ):

```solidity
86:         if (block.number == 0) {

172:         if (_to == address(0)) revert L2_INVALID_PARAM();

173:         if (_token == address(0)) {

296:         if (basefee_ == 0) basefee_ = 1;
```

- *TaikoL2EIP1559Configurable.sol* ( [33-33](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L33-L33), [34-34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L34-L34) ):

```solidity
33:         if (_newConfig.gasTargetPerL1Block == 0) revert L2_INVALID_CONFIG();

34:         if (_newConfig.basefeeAdjustmentQuotient == 0) revert L2_INVALID_CONFIG();
```

- *Asn1Decode.sol* ( [143-143](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L143-L143), [156-156](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L156-L156), [158-158](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L158-L158), [191-191](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L191-L191) ):

```solidity
143:         require(der[ptr.ixf()] & 0x80 == 0, "Not positive");

156:         require(der[ptr.ixf()] & 0x80 == 0, "Not positive");

158:         if (der[ptr.ixf()] == 0) {

191:         if ((der[ix + 1] & 0x80) == 0) {
```

- *BytesUtils.sol* ( [96-96](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L96-L96), [345-345](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L345-L345) ):

```solidity
96:                 if (diff != 0) {

345:         if (len % 8 == 0) {
```

- *RsaVerify.sol* ( [145-145](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L145-L145), [278-278](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L278-L278) ):

```solidity
145:         if (decipher[2 + paddingLen] != 0) {

278:         if (decipher[2 + paddingLen] != 0) {
```

- *X509DateUtils.sol* ( [72-72](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L72-L72), [73-73](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L73-L73), [74-74](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L74-L74) ):

```solidity
72:         if (year % 4 != 0) return false;

73:         if (year % 100 != 0) return true;

74:         if (year % 400 != 0) return false;
```

- *Bridge.sol* ( [242-242](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L242-L242), [245-245](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L245-L245), [291-291](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L291-L291), [485-485](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L485-L485) ):

```solidity
242:             if (invocationDelay != 0) {

245:                     preferredExecutor: _message.gasLimit == 0 ? _message.destOwner : msg.sender

291:                 _message.refundTo == address(0) ? _message.destOwner : _message.refundTo;

485:         if (_gasLimit == 0) revert B_INVALID_GAS_LIMIT();
```

- *AddressResolver.sol* ( [81-81](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L81-L81) ):

```solidity
81:         if (addressManager == address(0)) revert RESOLVER_INVALID_MANAGER();
```

- *EssentialContract.sol* ( [105-105](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L105-L105), [110-110](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L110-L110) ):

```solidity
105:         if (_addressManager == address(0)) revert ZERO_ADDR_MANAGER();

110:         _transferOwnership(_owner == address(0) ? msg.sender : _owner);
```

- *LibAddress.sol* ( [24-24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L24-L24) ):

```solidity
24:         if (_to == address(0)) revert ETH_TRANSFER_FAILED();
```

- *LibTrieProof.sol* ( [46-46](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibTrieProof.sol#L46-L46), [50-50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibTrieProof.sol#L50-L50) ):

```solidity
46:         if (_accountProof.length != 0) {

50:             if (rlpAccount.length == 0) revert LTP_INVALID_ACCOUNT_PROOF();
```

- *SignalService.sol* ( [36-36](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L36-L36), [41-41](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L41-L41), [95-95](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L95-L95), [167-167](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L167-L167), [169-169](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L169-L169), [172-172](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L172-L172) ):

```solidity
36:         if (_app == address(0)) revert SS_INVALID_SENDER();

41:         if (_input == 0) revert SS_INVALID_VALUE();

95:         if (hopProofs.length == 0) revert SS_EMPTY_PROOF();

167:         blockId_ = _blockId != 0 ? _blockId : topBlockId[_chainId][_kind];

169:         if (blockId_ != 0) {

172:             if (chainData_ == 0) revert SS_SIGNAL_NOT_FOUND();
```

- *TimelockTokenPool.sol* ( [121-121](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L121-L121), [124-124](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L124-L124), [127-127](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L127-L127), [136-136](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L136-L136), [137-137](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L137-L137), [154-154](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L154-L154), [169-169](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L169-L169), [255-255](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L255-L255), [256-256](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L256-L256), [259-259](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L259-L259), [268-268](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L268-L268) ):

```solidity
121:         if (_taikoToken == address(0)) revert INVALID_PARAM();

124:         if (_costToken == address(0)) revert INVALID_PARAM();

127:         if (_sharedVault == address(0)) revert INVALID_PARAM();

136:         if (_recipient == address(0)) revert INVALID_PARAM();

137:         if (recipients[_recipient].grant.amount != 0) revert ALREADY_GRANTED();

154:         if (amountVoided == 0) revert NOTHING_TO_VOID();

169:         if (_to == address(0)) revert INVALID_PARAM();

255:         if (_amount == 0) return 0;

256:         if (_start == 0) return _amount;

259:         if (_period == 0) return _amount;

268:         if (_grant.amount == 0) revert INVALID_GRANT();
```

- *ERC20Airdrop2.sol* ( [111-111](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L111-L111) ):

```solidity
111:         if (balance == 0) return (0, 0);
```

- *RLPReader.sol* ( [287-287](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L287-L287) ):

```solidity
287:         if (_length == 0) {
```

- *RLPWriter.sol* ( [60-60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L60-L60) ):

```solidity
60:             if (b[i] != 0) {
```

- *MerkleTrie.sol* ( [91-91](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L91-L91) ):

```solidity
91:             if (currentKeyIndex == 0) {
```

- *BaseNFTVault.sol* ( [149-149](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L149-L149) ):

```solidity
149:         if (_op.token == address(0)) revert VAULT_INVALID_TOKEN();
```

- *ERC1155Vault.sol* ( [48-48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L48-L48), [64-64](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L64-L64), [249-249](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L249-L249), [293-293](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L293-L293) ):

```solidity
48:             if (_op.amounts[i] == 0) revert VAULT_INVALID_AMOUNT();

64:             destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,

249:             if (bridgedToCanonical[_op.token].addr != address(0)) {

293:         if (btoken_ == address(0)) {
```

- *ERC20Vault.sol* ( [170-170](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L170-L170), [214-214](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L214-L214), [215-215](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L215-L215), [227-227](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L227-L227), [358-358](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L358-L358), [397-397](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L397-L397) ):

```solidity
170:         if (btokenOld_ != address(0)) {

214:         if (_op.amount == 0) revert VAULT_INVALID_AMOUNT();

215:         if (_op.token == address(0)) revert VAULT_INVALID_TOKEN();

227:             destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,

358:         if (bridgedToCanonical[_token].addr != address(0)) {

397:         if (btoken == address(0)) {
```

- *ERC721Vault.sol* ( [35-35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L35-L35), [50-50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L50-L50), [195-195](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L195-L195), [230-230](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L230-L230) ):

```solidity
35:             if (_op.amounts[i] != 0) revert VAULT_INVALID_AMOUNT();

50:             destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,

195:             if (bridgedToCanonical[_op.token].addr != address(0)) {

230:         if (btoken_ == address(0)) {
```

- *SgxVerifier.sol* ( [107-107](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L107-L107), [124-124](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L124-L124), [215-215](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L215-L215), [234-234](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L234-L234) ):

```solidity
107:             if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();

124:         if (automataDcapAttestation == address(0)) {

215:             if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();

234:         if (instance == address(0)) return false;
```

</details>

### [G-33] Low level `call` can be optimized with assembly

When using low-level calls, the `returnData` is copied to memory even if the variable is not utilized. The proper way to handle this is through a low level assembly call.
For example:
```solidity
(bool success,) = payable(receiver).call{gas: gas, value: value}("");
```
can be optimized to:
```solidity
bool success;
assembly {
    success := call(gas, receiver, value, 0, 0, 0, 0)
}
```


There is 1 instance:

- *CrossChainOwned.sol* ( [50-50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L50-L50) ):

```solidity
50:         (bool success,) = address(this).call(txdata);
```

### [G-34] Consider using OZ EnumerateSet in place of nested mappings

Nested mappings and multi-dimensional arrays involve a double hashing process, which can be costly in terms of gas due to the repeated hashing and storage operations. An optimization approach is to manually concatenate keys and perform a single hash and storage operation, but this increases the risk of storage collisions, especially when there are other nested hash maps using the same key types. OpenZeppelin's EnumerableSet offers a solution by combining set operations with element enumeration, providing a gas-efficient and collision-resistant alternative for certain scenarios where nested mappings or multi-dimensional arrays are used in Solidity.

<details>
<summary>There are 6 instances (click to show):</summary>

- *Guardians.sol* ( [19-19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L19-L19) ):

```solidity
19:     mapping(uint32 version => mapping(bytes32 hash => uint256 approvalBits)) internal _approvals;
```

- *AutomataDcapV3Attestation.sol* ( [47-47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L47-L47) ):

```solidity
47:     mapping(uint256 idx => mapping(bytes serialNum => bool revoked)) private _serialNumIsRevoked;
```

- *AddressManager.sol* ( [12-12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L12-L12) ):

```solidity
12:     mapping(uint256 chainId => mapping(bytes32 name => address addr)) private __addresses;
```

- *SignalService.sol* ( [17-17](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L17-L17) ):

```solidity
17:     mapping(uint64 chainId => mapping(bytes32 kind => uint64 blockId)) public topBlockId;
```

- *BaseNFTVault.sol* ( [59-59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L59-L59) ):

```solidity
59:     mapping(uint256 chainId => mapping(address ctoken => address btoken)) public canonicalToBridged;
```

- *ERC20Vault.sol* ( [49-49](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L49-L49) ):

```solidity
49:     mapping(uint256 chainId => mapping(address ctoken => address btoken)) public canonicalToBridged;
```

</details>

### [G-35] Consider using solady's `FixedPointMathLib`

Saves gas, and works to avoid unnecessary [overflows](https://github.com/Vectorized/solady/blob/9deb9ed36a27261a8745db5b7cd7f4cdc3b1cd4e/src/utils/FixedPointMathLib.sol#L436).

There are 3 instances:

- *Lib1559Math.sol* ( [41-41](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/Lib1559Math.sol#L41-L41) ):

```solidity
41:         uint256 input = _gasExcess * LibFixedPointMath.SCALING_FACTOR / _adjustmentFactor;
```

- *TimelockTokenPool.sol* ( [264-264](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L264-L264) ):

```solidity
264:         return _amount * uint64(block.timestamp - _start) / _period;
```

- *ERC20Airdrop2.sol* ( [117-118](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L117-L118) ):

```solidity
117:         uint256 timeBasedAllowance = balance
118:             * (block.timestamp.min(claimEnd + withdrawalWindow) - claimEnd) / withdrawalWindow;
```

### [G-36] Use `selfbalance()` instead of `address(x).balance`

Use assembly when getting a contract's balance of ETH.
You can use `selfbalance()` instead of `address(x).balance` when getting your contract's balance of ETH to save gas.
Additionally, you can use `balance(address)` instead of `address.balance()` when getting an external contract's balance of ETH.
*Saves 15 gas when checking internal balance, 6 for external*.

There are 6 instances:

- *AssignmentHook.sol* ( [125](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L125), [126](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L126) ):

```solidity
125:         if (address(this).balance > 0) {

126:             taikoL1Address.sendEther(address(this).balance);
```

- *LibProposing.sol* ( [253](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L253), [260](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L260), [261](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L261) ):

```solidity
253:                 IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }(

260:             if (address(this).balance != 0) {

261:                 msg.sender.sendEther(address(this).balance);
```

- *TaikoL2.sol* ( [174](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L174) ):

```solidity
174:             _to.sendEther(address(this).balance);
```

### [G-37] Assigning state variables directly with named struct constructors wastes gas

Using named arguments for struct means that the compiler needs to organize the fields in memory before doing the assignment, which wastes gas. Set each field directly in storage (use dot-notation), or use the unnamed version of the constructor.

There are 4 instances:

- *Bridge.sol* ( [243-246](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L243-L246), [549-549](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L549-L549) ):

```solidity
243:                 proofReceipt[msgHash] = ProofReceipt({
244:                     receivedAt: receivedAt,
245:                     preferredExecutor: _message.gasLimit == 0 ? _message.destOwner : msg.sender
246:                 });

549:             __ctx = Context(_msgHash, _from, _srcChainId);
```

- *SgxVerifier.sol* ( [217-217](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L217-L217), [229-229](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L229-L229) ):

```solidity
217:             instances[nextInstanceId] = Instance(_instances[i], validSince);

229:         instances[id] = Instance(newInstance, uint64(block.timestamp));
```

### [G-38] Avoid zero transfer to save gas

In Solidity, unnecessary operations can waste gas. For example, a transfer function without a zero amount check uses gas even if called with a zero amount, since the contract state remains unchanged. Implementing a zero amount check avoids these unnecessary function calls, saving gas and improving efficiency.

<details>
<summary>There are 17 instances (click to show):</summary>

- *TaikoToken.sol* ( [62-62](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L62-L62), [80-80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L80-L80) ):

```solidity
62:         return super.transfer(_to, _amount);

80:         return super.transferFrom(_from, _to, _amount);
```

- *AssignmentHook.sol* ( [102-102](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L102-L102), [114-116](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L114-L116) ):

```solidity
102:         tko.transferFrom(_blk.assignedProver, taikoL1Address, _blk.livenessBond);

114:             IERC20(assignment.feeToken).safeTransferFrom(
115:                 _meta.coinbase, _blk.assignedProver, proverFee
116:             );
```

- *LibProving.sol* ( [367-367](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L367-L367), [371-371](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L371-L371), [382-382](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L382-L382), [384-384](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L384-L384) ):

```solidity
367:                 _tko.transfer(_ts.prover, _ts.validityBond + reward);

371:                 _tko.transfer(_ts.contester, _ts.contestBond + reward);

382:                 _tko.transfer(msg.sender, reward - _tier.validityBond);

384:                 _tko.transferFrom(msg.sender, address(this), _tier.validityBond - reward);
```

- *LibVerifying.sol* ( [189-189](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L189-L189) ):

```solidity
189:                 tko.transfer(ts.prover, bondToReturn);
```

- *TaikoL2.sol* ( [176-176](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L176-L176) ):

```solidity
176:             IERC20(_token).safeTransfer(_to, IERC20(_token).balanceOf(address(this)));
```

- *TimelockTokenPool.sol* ( [219-219](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L219-L219), [220-220](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L220-L220) ):

```solidity
219:         IERC20(taikoToken).transferFrom(sharedVault, _to, amountToWithdraw);

220:         IERC20(costToken).safeTransferFrom(_recipient, sharedVault, costToWithdraw);
```

- *ERC20Airdrop.sol* ( [63-63](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L63-L63) ):

```solidity
63:         IERC20(token).transferFrom(vault, user, amount);
```

- *ERC20Airdrop2.sol* ( [91-91](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L91-L91) ):

```solidity
91:         IERC20(token).transferFrom(vault, user, amount);
```

- *ERC20Vault.sol* ( [330-330](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L330-L330), [379-379](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L379-L379) ):

```solidity
330:             IERC20(token_).safeTransfer(_to, _amount);

379:             t.safeTransferFrom({ from: msg.sender, to: address(this), value: _amount });
```

- *USDCAdapter.sol* ( [48-48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L48-L48) ):

```solidity
48:         usdc.transferFrom(_from, address(this), _amount);
```

</details>

### [G-39] Cache address(this) when used more than once

Caching address(this) when used more than once can save gas.

<details>
<summary>There are 16 instances (click to show):</summary>

- *AssignmentHook.sol* ( [125-125](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L125-L125), [126-126](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L126-L126) ):

```solidity
125:         if (address(this).balance > 0) {

126:             taikoL1Address.sendEther(address(this).balance);
```

- *LibProposing.sol* ( [238-238](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L238-L238), [253-253](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L253-L253), [260-260](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L260-L260), [261-261](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L261-L261), [268-268](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L268-L268) ):

```solidity
238:             uint256 tkoBalance = tko.balanceOf(address(this));

253:                 IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }(

260:             if (address(this).balance != 0) {

261:                 msg.sender.sendEther(address(this).balance);

268:             if (tko.balanceOf(address(this)) != tkoBalance + _config.livenessBond) {
```

- *TaikoL2.sol* ( [174-174](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L174-L174), [176-176](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L176-L176) ):

```solidity
174:             _to.sendEther(address(this).balance);

176:             IERC20(_token).safeTransfer(_to, IERC20(_token).balanceOf(address(this)));
```

- *Bridge.sol* ( [174-174](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L174-L174), [196-196](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L196-L196) ):

```solidity
174:             if (!ISignalService(signalService).isSignalSent(address(this), msgHash)) {

196:                 _storeContext(msgHash, address(this), _message.srcChainId);
```

- *SignalService.sol* ( [112-112](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L112-L112), [131-131](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L131-L131) ):

```solidity
112:                 signalService = address(this);

131:         if (value == 0 || value != _loadSignalValue(address(this), signal)) {
```

- *ERC20Vault.sol* ( [378-378](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L378-L378), [379-379](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L379-L379), [380-380](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L380-L380) ):

```solidity
378:             uint256 _balance = t.balanceOf(address(this));

379:             t.safeTransferFrom({ from: msg.sender, to: address(this), value: _amount });

380:             balanceChange_ = t.balanceOf(address(this)) - _balance;
```

</details>

### [G-40] Checking constants first can save gas

Checks that involve constants should come before checks that involve state variables, function calls, and calculations. By doing these checks first, the function is able to revert before wasting a Gcoldsload (**2100 gas***) in a function that may ultimately revert in the unhappy case.

There are 3 instances:

- *V3Parser.sol* ( [87-90](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L87-L90), [91-93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L91-L93), [100-104](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L100-L104) ):

```solidity
/// @audit should check before line 75
87:         require(
88:             v3Quote.v3AuthData.certification.certType == 5,
89:             "certType must be 5: Concatenated PCK Cert Chain (PEM formatted)"
90:         );

/// @audit should check before line 75
91:         require(
92:             v3Quote.v3AuthData.certification.decodedCertDataArray.length == 3, "3 certs in chain"
93:         );

/// @audit should check before line 75
100:         require(
101:             v3Quote.v3AuthData.qeAuthData.parsedDataSize
102:                 == v3Quote.v3AuthData.qeAuthData.data.length,
103:             "Invalid QEAuthData size"
104:         );
```

### [G-41] State variable read in a loop

The state variable should be cached in and read from a local variable, or accumulated in a local variable then written to storage once outside of the loop, rather than reading/updating it on every iteration of the loop, which will replace each Gwarmaccess (**100 gas**) with a much cheaper stack read.

<details>
<summary>There are 6 instances (click to show):</summary>

- *Guardians.sol* ( [133-137](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L133-L137) ):

```solidity
/// @audit minGuardians
133:             for (uint256 i; i < guardiansLength; ++i) {
134:                 if (bits & 1 == 1) ++count;
135:                 if (count == minGuardians) return true;
136:                 bits >>= 1;
137:             }
```

- *ERC721Airdrop.sol* ( [59-61](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59-L61) ):

```solidity
/// @audit token
/// @audit vault
59:         for (uint256 i; i < tokenIds.length; ++i) {
60:             IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);
61:         }
```

- *SgxVerifier.sol* ( [210-223](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210-L223) ):

```solidity
/// @audit nextInstanceId
/// @audit nextInstanceId
/// @audit nextInstanceId
210:         for (uint256 i; i < _instances.length; ++i) {
211:             if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();
212: 
213:             addressRegistered[_instances[i]] = true;
214: 
215:             if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();
216: 
217:             instances[nextInstanceId] = Instance(_instances[i], validSince);
218:             ids[i] = nextInstanceId;
219: 
220:             emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);
221: 
222:             nextInstanceId++;
223:         }
```

</details>

### [G-42] State variable written in a loop

The code should be refactored such that updates made to the state variable are instead accumulated/tracked in a local variable, then be written a single time outside the loop, converting a Gsreset (**2900 gas**) to a stack write for each iteration.

There is 1 instance:

- *SgxVerifier.sol* ( [210-223](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210-L223) ):

```solidity
/// @audit nextInstanceId
210:         for (uint256 i; i < _instances.length; ++i) {
211:             if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();
212: 
213:             addressRegistered[_instances[i]] = true;
214: 
215:             if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();
216: 
217:             instances[nextInstanceId] = Instance(_instances[i], validSince);
218:             ids[i] = nextInstanceId;
219: 
220:             emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);
221: 
222:             nextInstanceId++;
223:         }
```

### [G-43] Unlimited gas consumption risk due to external call recipients

When calling an external function without specifying a gas limit , the called contract may consume all the remaining gas, causing the tx to be reverted. To mitigate this, it is recommended to explicitly set a gas limit when making low level external calls.

There are 2 instances:

- *SigVerifyLib.sol* ( [137-137](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L137-L137) ):

```solidity
137:         (bool success, bytes memory ret) = ES256VERIFIER.staticcall(args);
```

- *Bridge.sol* ( [591-591](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L591-L591) ):

```solidity
591:         (success_,) = _signalService.staticcall(data);
```

### [G-44] Optimize names to save gas

`public`/`external` function names and `public` member variable names can be optimized to save gas. Below are the interfaces/abstract contracts that can be optimized so that the most frequently-called functions use the least amount of gas possible during method lookup. Method IDs that have two leading zero bytes can save 128 gas each during deployment, and renaming functions to have lower method IDs will save 22 gas per call, [per sorted position shifted](https://medium.com/joyso/solidity-how-does-function-name-affect-gas-consumption-in-smart-contract-47d270d8ac92).

<details>
<summary>There are 46 instances (click to show):</summary>

- *ITaikoL1.sol* ( [8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/ITaikoL1.sol#L8) ):

```solidity
/// @audit proposeBlock(), proveBlock(), verifyBlocks(), getConfig()
8: interface ITaikoL1 {
```

- *TaikoL1.sol* ( [22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L22) ):

```solidity
/// @audit init(), proposeBlock(), proveBlock(), verifyBlocks(), pauseProving(), depositEtherToL2(), unpause(), canDepositEthToL2(), isBlobReusable(), getBlock(), getTransition(), getStateVariables(), getConfig(), state
22: contract TaikoL1 is EssentialContract, ITaikoL1, TaikoEvents, TaikoErrors {
```

- *TaikoToken.sol* ( [15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L15) ):

```solidity
/// @audit init(), burn(), snapshot()
15: contract TaikoToken is EssentialContract, ERC20SnapshotUpgradeable, ERC20VotesUpgradeable {
```

- *TaikoGovernor.sol* ( [16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L16) ):

```solidity
/// @audit init(), propose(), propose(), state(), votingDelay(), votingPeriod(), proposalThreshold()
16: contract TaikoGovernor is
```

- *TaikoTimelockController.sol* ( [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L9) ):

```solidity
/// @audit init(), getMinDelay()
9: contract TaikoTimelockController is EssentialContract, TimelockControllerUpgradeable {
```

- *AssignmentHook.sol* ( [14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L14) ):

```solidity
/// @audit init(), onBlockProposed(), hashAssignment(), MAX_GAS_PAYING_PROVER
14: contract AssignmentHook is EssentialContract, IHook {
```

- *Guardians.sol* ( [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L9) ):

```solidity
/// @audit setGuardians(), isApproved(), numGuardians(), MIN_NUM_GUARDIANS, guardianIds, guardians, version, minGuardians
9: abstract contract Guardians is EssentialContract {
```

- *DevnetTierProvider.sol* ( [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L10) ):

```solidity
/// @audit init(), getTier(), getTierIds(), getMinTier()
10: contract DevnetTierProvider is EssentialContract, ITierProvider {
```

- *ITierProvider.sol* ( [7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L7) ):

```solidity
/// @audit getTier(), getTierIds(), getMinTier()
7: interface ITierProvider {
```

- *MainnetTierProvider.sol* ( [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L10) ):

```solidity
/// @audit init(), getTier(), getTierIds(), getMinTier()
10: contract MainnetTierProvider is EssentialContract, ITierProvider {
```

- *TestnetTierProvider.sol* ( [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L10) ):

```solidity
/// @audit init(), getTier(), getTierIds(), getMinTier()
10: contract TestnetTierProvider is EssentialContract, ITierProvider {
```

- *CrossChainOwned.sol* ( [14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L14) ):

```solidity
/// @audit onMessageInvocation(), ownerChainId, nextTxId
14: abstract contract CrossChainOwned is EssentialContract, IMessageInvocable {
```

- *TaikoL2.sol* ( [21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L21) ):

```solidity
/// @audit init(), anchor(), withdraw(), getBasefee(), getBlockHash(), getConfig(), skipFeeCheck(), GOLDEN_TOUCH_ADDRESS, BLOCK_SYNC_THRESHOLD, l2Hashes, publicInputHash, gasExcess, lastSyncedBlock
21: contract TaikoL2 is CrossChainOwned {
```

- *TaikoL2EIP1559Configurable.sol* ( [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L9) ):

```solidity
/// @audit setConfigAndExcess(), getConfig(), customConfig
9: contract TaikoL2EIP1559Configurable is TaikoL2 {
```

- *AutomataDcapV3Attestation.sol* ( [22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L22) ):

```solidity
/// @audit setMrSigner(), setMrEnclave(), addRevokedCertSerialNum(), removeRevokedCertSerialNum(), configureTcbInfoJson(), configureQeIdentityJson(), toggleLocalReportCheck(), verifyAttestation(), verifyParsedQuote(), sigVerifyLib, pemCertLib, tcbInfo, qeIdentity, owner
22: contract AutomataDcapV3Attestation is IAttestation {
```

- *IAttestation.sol* ( [8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/interfaces/IAttestation.sol#L8) ):

```solidity
/// @audit verifyAttestation(), verifyParsedQuote()
8: interface IAttestation {
```

- *ISigVerifyLib.sol* ( [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L6) ):

```solidity
/// @audit verifyAttStmtSignature(), verifyCertificateSignature(), verifyRS256Signature(), verifyRS1Signature(), verifyES256Signature()
6: interface ISigVerifyLib {
```

- *PEMCertChainLib.sol* ( [12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L12) ):

```solidity
/// @audit splitCertificateChain(), decodeCert()
12: contract PEMCertChainLib is IPEMCertChainLib {
```

- *IPEMCertChainLib.sol* ( [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L6) ):

```solidity
/// @audit splitCertificateChain(), decodeCert()
6: interface IPEMCertChainLib {
```

- *SigVerifyLib.sol* ( [15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L15) ):

```solidity
/// @audit verifyAttStmtSignature(), verifyCertificateSignature(), verifyRS256Signature(), verifyRS1Signature(), verifyES256Signature()
15: contract SigVerifyLib is ISigVerifyLib {
```

- *Bridge.sol* ( [16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L16) ):

```solidity
/// @audit init(), suspendMessages(), banAddress(), sendMessage(), recallMessage(), processMessage(), retryMessage(), isMessageSent(), proveMessageFailed(), proveMessageReceived(), isDestChainEnabled(), context(), getInvocationDelays(), hashMessage(), signalForFailedMessage(), nextMessageId, messageStatus, addressBanned, proofReceipt
16: contract Bridge is EssentialContract, IBridge {
```

- *IBridge.sol* ( [8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/IBridge.sol#L8) ):

```solidity
/// @audit sendMessage(), recallMessage(), processMessage(), retryMessage(), context(), isMessageSent(), hashMessage()
8: interface IBridge {
```

- *AddressManager.sol* ( [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L10) ):

```solidity
/// @audit init(), setAddress(), getAddress()
10: contract AddressManager is EssentialContract, IAddressManager {
```

- *AddressResolver.sol* ( [11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L11) ):

```solidity
/// @audit resolve(), resolve(), addressManager
11: abstract contract AddressResolver is IAddressResolver, Initializable {
```

- *EssentialContract.sol* ( [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L10) ):

```solidity
/// @audit pause(), unpause(), paused()
10: abstract contract EssentialContract is UUPSUpgradeable, Ownable2StepUpgradeable, AddressResolver {
```

- *IAddressResolver.sol* ( [13](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/IAddressResolver.sol#L13) ):

```solidity
/// @audit resolve(), resolve()
13: interface IAddressResolver {
```

- *ISignalService.sol* ( [12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/ISignalService.sol#L12) ):

```solidity
/// @audit sendSignal(), syncChainData(), proveSignalReceived(), isSignalSent(), isChainDataSynced(), getSyncedChainData(), signalForChainData()
12: interface ISignalService {
```

- *SignalService.sol* ( [14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L14) ):

```solidity
/// @audit init(), authorize(), sendSignal(), syncChainData(), proveSignalReceived(), isChainDataSynced(), isSignalSent(), getSyncedChainData(), signalForChainData(), getSignalSlot(), topBlockId, isAuthorized
14: contract SignalService is EssentialContract, ISignalService {
```

- *TimelockTokenPool.sol* ( [25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L25) ):

```solidity
/// @audit init(), grant(), void(), withdraw(), withdraw(), getMyGrantSummary(), getMyGrant(), taikoToken, costToken, sharedVault, totalAmountGranted, totalAmountVoided, totalAmountWithdrawn, totalCostPaid, recipients
25: contract TimelockTokenPool is EssentialContract {
```

- *ERC20Airdrop.sol* ( [11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L11) ):

```solidity
/// @audit init(), claimAndDelegate(), token, vault
11: contract ERC20Airdrop is MerkleClaimable {
```

- *ERC20Airdrop2.sol* ( [12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L12) ):

```solidity
/// @audit init(), claim(), withdraw(), getBalance(), token, vault, claimedAmount, withdrawnAmount, withdrawalWindow
12: contract ERC20Airdrop2 is MerkleClaimable {
```

- *ERC721Airdrop.sol* ( [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L9) ):

```solidity
/// @audit init(), claim(), token, vault
9: contract ERC721Airdrop is MerkleClaimable {
```

- *MerkleClaimable.sol* ( [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L10) ):

```solidity
/// @audit setConfig(), isClaimed, merkleRoot, claimStart, claimEnd
10: abstract contract MerkleClaimable is EssentialContract {
```

- *BaseNFTVault.sol* ( [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L9) ):

```solidity
/// @audit ERC1155_INTERFACE_ID, ERC721_INTERFACE_ID, MAX_TOKEN_PER_TXN, bridgedToCanonical, canonicalToBridged
9: abstract contract BaseNFTVault is BaseVault {
```

- *BridgedERC1155.sol* ( [14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L14) ):

```solidity
/// @audit init(), mint(), mintBatch(), burn(), srcToken, srcChainId
14: contract BridgedERC1155 is EssentialContract, IERC1155MetadataURIUpgradeable, ERC1155Upgradeable {
```

- *BridgedERC20.sol* ( [15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L15) ):

```solidity
/// @audit init(), setSnapshoter(), snapshot(), canonical(), srcToken, srcChainId, snapshooter
15: contract BridgedERC20 is
```

- *BridgedERC20Base.sol* ( [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L9) ):

```solidity
/// @audit changeMigrationStatus(), mint(), burn(), owner(), migratingAddress, migratingInbound
9: abstract contract BridgedERC20Base is EssentialContract, IBridgedERC20 {
```

- *BridgedERC721.sol* ( [12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L12) ):

```solidity
/// @audit init(), mint(), burn(), source(), srcToken, srcChainId
12: contract BridgedERC721 is EssentialContract, ERC721Upgradeable {
```

- *ERC1155Vault.sol* ( [29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L29) ):

```solidity
/// @audit sendToken(), onMessageInvocation(), onMessageRecalled()
29: contract ERC1155Vault is BaseNFTVault, ERC1155ReceiverUpgradeable {
```

- *ERC20Vault.sol* ( [18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L18) ):

```solidity
/// @audit changeBridgedToken(), sendToken(), onMessageInvocation(), onMessageRecalled(), bridgedToCanonical, canonicalToBridged, btokenBlacklist
18: contract ERC20Vault is BaseVault {
```

- *ERC721Vault.sol* ( [16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L16) ):

```solidity
/// @audit sendToken(), onMessageInvocation(), onMessageRecalled()
16: contract ERC721Vault is BaseNFTVault, IERC721Receiver {
```

- *IBridgedERC20.sol* ( [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/IBridgedERC20.sol#L10) ):

```solidity
/// @audit mint(), burn(), changeMigrationStatus(), owner()
10: interface IBridgedERC20 {
```

- *USDCAdapter.sol* ( [8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L8), [28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L28) ):

```solidity
/// @audit burn(), mint()
8: interface IUSDC {

/// @audit init(), usdc
28: contract USDCAdapter is BridgedERC20Base {
```

- *GuardianVerifier.sol* ( [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L10) ):

```solidity
/// @audit init(), verifyProof()
10: contract GuardianVerifier is EssentialContract, IVerifier {
```

- *SgxVerifier.sol* ( [19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L19) ):

```solidity
/// @audit init(), addInstances(), deleteInstances(), registerInstance(), verifyProof(), getSignedHash(), INSTANCE_EXPIRY, INSTANCE_VALIDITY_DELAY, nextInstanceId, instances, addressRegistered
19: contract SgxVerifier is EssentialContract, IVerifier {
```

</details>

### [G-45] Reduce gas usage by moving to Solidity 0.8.19 or later

Solidity version 0.8.19 introduced a number of gas optimizations, refer to the [Solidity 0.8.19 Release Announcement](https://soliditylang.org/blog/2023/02/22/solidity-0.8.19-release-announcement) for details.

<details>
<summary>There are 11 instances (click to show):</summary>

- *ITaikoL1.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/ITaikoL1.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *IHook.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/IHook.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *IAttestation.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/interfaces/IAttestation.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *ISigVerifyLib.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *IPEMCertChainLib.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *IBridge.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/IBridge.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *IAddressManager.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/IAddressManager.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *IAddressResolver.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/IAddressResolver.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *ISignalService.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/ISignalService.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *IBridgedERC20.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/IBridgedERC20.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *IVerifier.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/IVerifier.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

</details>

### [G-46] Newer versions of solidity are more gas efficient

The solidity language continues to pursue more efficient gas optimization schemes. Adopting a [newer version of solidity](https://github.com/ethereum/solc-js/tags) can be more gas efficient.

<details>
<summary>There are 81 instances (click to show):</summary>

- *ITaikoL1.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/ITaikoL1.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *TaikoData.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *TaikoErrors.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *TaikoEvents.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoEvents.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *TaikoL1.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *TaikoToken.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *TaikoGovernor.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *TaikoTimelockController.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *AssignmentHook.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *IHook.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/IHook.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *LibDepositing.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *LibProposing.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *LibProving.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *LibUtils.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *LibVerifying.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *GuardianProver.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/GuardianProver.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *Guardians.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *DevnetTierProvider.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *ITierProvider.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *MainnetTierProvider.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *TestnetTierProvider.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *CrossChainOwned.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *Lib1559Math.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/Lib1559Math.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *TaikoL2.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *TaikoL2EIP1559Configurable.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *AutomataDcapV3Attestation.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *IAttestation.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/interfaces/IAttestation.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *ISigVerifyLib.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *EnclaveIdStruct.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/EnclaveIdStruct.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *PEMCertChainLib.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *V3Parser.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *V3Struct.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *TCBInfoStruct.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *IPEMCertChainLib.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *Asn1Decode.sol* ( [3](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L3) ):

```solidity
3: pragma solidity 0.8.24;
```

- *BytesUtils.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *RsaVerify.sol* ( [3](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L3) ):

```solidity
3: pragma solidity 0.8.24;
```

- *SHA1.sol* ( [3](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SHA1.sol#L3) ):

```solidity
3: pragma solidity 0.8.24;
```

- *SigVerifyLib.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *X509DateUtils.sol* ( [3](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L3) ):

```solidity
3: pragma solidity 0.8.24;
```

- *Bridge.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *IBridge.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/IBridge.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *AddressManager.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *AddressResolver.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *EssentialContract.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *IAddressManager.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/IAddressManager.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *IAddressResolver.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/IAddressResolver.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *Lib4844.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/Lib4844.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *LibAddress.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *LibMath.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibMath.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *LibTrieProof.sol* ( [7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibTrieProof.sol#L7) ):

```solidity
7: pragma solidity 0.8.24;
```

- *ISignalService.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/ISignalService.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *LibSignals.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/LibSignals.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *SignalService.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *TimelockTokenPool.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *ERC20Airdrop.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *ERC20Airdrop2.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *ERC721Airdrop.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *MerkleClaimable.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *ExcessivelySafeCall.sol* ( [3](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L3) ):

```solidity
3: pragma solidity 0.8.24;
```

- *Bytes.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *RLPReader.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *RLPWriter.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *MerkleTrie.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *SecureMerkleTrie.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *LibFixedPointMath.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L4) ):

```solidity
4: pragma solidity 0.8.24;
```

- *BaseNFTVault.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *BaseVault.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *BridgedERC1155.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *BridgedERC20.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *BridgedERC20Base.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *BridgedERC721.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *ERC1155Vault.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *ERC20Vault.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *ERC721Vault.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *IBridgedERC20.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/IBridgedERC20.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *LibBridgedToken.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *USDCAdapter.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *GuardianVerifier.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *IVerifier.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/IVerifier.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

- *SgxVerifier.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L2) ):

```solidity
2: pragma solidity 0.8.24;
```

</details>

### [G-47] Avoid updating storage when the value hasn't changed

Manipulating storage in solidity is gas-intensive. It can be optimized by avoiding unnecessary storage updates when the new value equals the existing value.
If the old value is equal to the new value, not re-storing the value will avoid a Gsreset (**2900 gas**), potentially at the expense of a Gcoldsload (**2100 gas**) or a Gwarmaccess (**100 gas**).

<details>
<summary>There are 19 instances (click to show):</summary>

- *Guardians.sol* ( [94-94](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L94-L94) ):

```solidity
94:         minGuardians = _minGuardians;
```

- *CrossChainOwned.sol* ( [73-73](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L73-L73) ):

```solidity
73:         ownerChainId = _ownerChainId;
```

- *TaikoL2.sol* ( [151-151](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L151-L151), [154-154](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L154-L154), [155-155](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L155-L155) ):

```solidity
151:             lastSyncedBlock = _l1BlockId;

154:         l2Hashes[parentId] = blockhash(parentId);

155:         publicInputHash = publicInputHashNew;
```

- *TaikoL2EIP1559Configurable.sol* ( [37-37](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L37-L37) ):

```solidity
37:         gasExcess = _newGasExcess;
```

- *AutomataDcapV3Attestation.sol* ( [66-66](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L66-L66), [70-70](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L70-L70) ):

```solidity
66:         _trustedUserMrSigner[_mrSigner] = _trusted;

70:         _trustedUserMrEnclave[_mrEnclave] = _trusted;
```

- *AddressResolver.sol* ( [62-62](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L62-L62) ):

```solidity
62:         addressManager = _addressManager;
```

- *EssentialContract.sol* ( [125-125](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L125-L125) ):

```solidity
125:             __reentry = _reentry;
```

- *MerkleClaimable.sol* ( [91-91](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L91-L91), [92-92](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L92-L92), [93-93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L93-L93) ):

```solidity
91:         claimStart = _claimStart;

92:         claimEnd = _claimEnd;

93:         merkleRoot = _merkleRoot;
```

- *BridgedERC20.sol* ( [81-81](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L81-L81) ):

```solidity
81:         snapshooter = _snapshooter;
```

- *BridgedERC20Base.sol* ( [49-49](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L49-L49), [50-50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L50-L50) ):

```solidity
49:         migratingAddress = _migratingAddress;

50:         migratingInbound = _migratingInbound;
```

- *ERC1155Vault.sol* ( [312-312](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L312-L312) ):

```solidity
312:         canonicalToBridged[_ctoken.chainId][_ctoken.addr] = btoken_;
```

- *ERC20Vault.sol* ( [423-423](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L423-L423) ):

```solidity
423:         canonicalToBridged[ctoken.chainId][ctoken.addr] = btoken;
```

- *ERC721Vault.sol* ( [248-248](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L248-L248) ):

```solidity
248:         canonicalToBridged[_ctoken.chainId][_ctoken.addr] = btoken_;
```

</details>

### [G-48] Same cast is done multiple times

It's cheaper to do it once, and store the result to a variable. The examples below are the second+ instance of a given cast of the variable.

<details>
<summary>There are 8 instances (click to show):</summary>

- *LibVerifying.sol* ( [64](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L64), [71](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L71) ):

```solidity
64:         blk.proposedAt = uint64(block.timestamp);

71:         ts.timestamp = uint64(block.timestamp);
```

- *PEMCertChainLib.sol* ( [359](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L359), [359](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L359), [363](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L363) ):

```solidity
359:                 ? uint16(bytes2(svnValueBytes)) / 256

359:                 ? uint16(bytes2(svnValueBytes)) / 256

363:                 pcesvn = uint256(svnValue);
```

- *Asn1Decode.sol* ( [194](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L194) ):

```solidity
194:             ixLastContentByte = uint80(ixFirstContentByte + length - 1);
```

- *X509DateUtils.sol* ( [21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L21) ):

```solidity
21:             yrs += (uint8(x509Time[0]) - 48) * 1000 + (uint8(x509Time[1]) - 48) * 100;
```

- *RLPWriter.sol* ( [45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L45) ):

```solidity
45:             out_[0] = bytes1(uint8(lenLen) + uint8(_offset) + 55);
```

</details>

### [G-49] State variables that are used multiple times in a function should be cached in stack variables

When performing multiple operations on a state variable in a function, it is recommended to cache it first. Either multiple reads or multiple writes to a state variable can save gas by caching it on the stack.
Caching of a state variable replaces each Gwarmaccess (100 gas) with a much cheaper stack read. Other less obvious fixes/optimizations include having local memory caches of state variable structs, or having local caches of state variable contracts/addresses.
*Saves 100 gas per instance*.

<details>
<summary>There are 24 instances (click to show):</summary>

- *TaikoToken.sol* ( [25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L25) ):

```solidity
/// @audit _name: 2 reads
25:     function init(
```

- *Guardians.sol* ( [53](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L53), [111](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L111) ):

```solidity
/// @audit guardians.length: 2 reads
/// @audit version: 2 reads 1 writes
53:     function setGuardians(

/// @audit version: 2 reads
111:     function approve(uint256 _operationId, bytes32 _hash) internal returns (bool approved_) {
```

- *CrossChainOwned.sol* ( [36](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L36) ):

```solidity
/// @audit nextTxId: 2 reads 1 writes
36:     function onMessageInvocation(bytes calldata _data)
```

- *TaikoL2.sol* ( [107](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L107), [252](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L252) ):

```solidity
/// @audit gasExcess: 2 reads
107:     function anchor(

/// @audit gasExcess: 2 reads
/// @audit lastSyncedBlock: 3 reads
252:     function _calc1559BaseFee(
```

- *AddressResolver.sol* ( [72](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L72) ):

```solidity
/// @audit addressManager: 2 reads
72:     function _resolve(
```

- *EssentialContract.sol* ( [109](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L109) ):

```solidity
/// @audit _owner: 2 reads
109:     function __Essential_init(address _owner) internal virtual {
```

- *TimelockTokenPool.sol* ( [208](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L208) ):

```solidity
/// @audit sharedVault: 2 reads
208:     function _withdraw(address _recipient, address _to) private {
```

- *ERC20Airdrop.sol* ( [50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L50) ):

```solidity
/// @audit token: 2 reads
50:     function claimAndDelegate(
```

- *ERC20Airdrop2.sol* ( [104](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L104) ):

```solidity
/// @audit claimEnd: 3 reads
/// @audit withdrawalWindow: 2 reads
104:     function getBalance(address user)
```

- *BridgedERC20.sol* ( [52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L52) ):

```solidity
/// @audit _symbol: 2 reads
/// @audit _name: 3 reads
52:     function init(
```

- *BridgedERC20Base.sol* ( [57](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L57), [75](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L75) ):

```solidity
/// @audit migratingAddress: 2 reads
57:     function mint(address _account, uint256 _amount) public nonReentrant whenNotPaused {

/// @audit migratingAddress: 2 reads
75:     function burn(address _account, uint256 _amount) public nonReentrant whenNotPaused {
```

- *BridgedERC721.sol* ( [31](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L31) ):

```solidity
/// @audit _symbol: 2 reads
/// @audit _name: 2 reads
31:     function init(
```

- *USDCAdapter.sol* ( [47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L47) ):

```solidity
/// @audit usdc: 2 reads
47:     function _burnToken(address _from, uint256 _amount) internal override {
```

- *SgxVerifier.sol* ( [100](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L100), [195](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L195), [233](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L233) ):

```solidity
/// @audit instances[idx].addr: 2 reads
100:     function deleteInstances(uint256[] calldata _ids)

/// @audit nextInstanceId: 4 reads 1 writes
195:     function _addInstances(

/// @audit instances[id].validSince: 2 reads
233:     function _isInstanceValid(uint256 id, address instance) private view returns (bool) {
```

</details>

### [G-50] Use solady library where possible to save gas

The following OpenZeppelin imports have a Solady equivalent, as such they can be used to save GAS as Solady modules have been specifically designed to be as GAS efficient as possible.

<details>
<summary>There are 54 instances (click to show):</summary>

- *TaikoToken.sol* ( [4-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L4-L4), [5-5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L5-L5), [6-6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L6-L6) ):

```solidity
4: import "@openzeppelin/contracts-upgradeable/token/ERC20/ERC20Upgradeable.sol";

5: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20SnapshotUpgradeable.sol";

6: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20VotesUpgradeable.sol";
```

- *TaikoGovernor.sol* ( [4-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L4-L4), [5-6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L5-L6), [7-7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L7-L7), [8-9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L8-L9), [10-11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L10-L11) ):

```solidity
4: import "@openzeppelin/contracts-upgradeable/governance/GovernorUpgradeable.sol";

5: import
6:     "@openzeppelin/contracts-upgradeable/governance/compatibility/GovernorCompatibilityBravoUpgradeable.sol";

7: import "@openzeppelin/contracts-upgradeable/governance/extensions/GovernorVotesUpgradeable.sol";

8: import
9:     "@openzeppelin/contracts-upgradeable/governance/extensions/GovernorVotesQuorumFractionUpgradeable.sol";

10: import
11:     "@openzeppelin/contracts-upgradeable/governance/extensions/GovernorTimelockControlUpgradeable.sol";
```

- *TaikoTimelockController.sol* ( [4-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L4-L4) ):

```solidity
4: import "@openzeppelin/contracts-upgradeable/governance/TimelockControllerUpgradeable.sol";
```

- *AssignmentHook.sol* ( [4-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L4-L4), [5-5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L5-L5) ):

```solidity
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

5: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```

- *LibProposing.sol* ( [4-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L4-L4) ):

```solidity
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```

- *LibProving.sol* ( [4-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L4-L4) ):

```solidity
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```

- *LibVerifying.sol* ( [4-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L4-L4) ):

```solidity
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```

- *CrossChainOwned.sol* ( [4-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L4-L4) ):

```solidity
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```

- *TaikoL2.sol* ( [4-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L4-L4), [5-5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L5-L5) ):

```solidity
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

5: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```

- *Bridge.sol* ( [4-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L4-L4) ):

```solidity
4: import "@openzeppelin/contracts/utils/Address.sol";
```

- *AddressResolver.sol* ( [4-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L4-L4) ):

```solidity
4: import "@openzeppelin/contracts-upgradeable/proxy/utils/Initializable.sol";
```

- *EssentialContract.sol* ( [4-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L4-L4), [5-5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L5-L5) ):

```solidity
4: import "@openzeppelin/contracts/proxy/utils/UUPSUpgradeable.sol";

5: import "@openzeppelin/contracts-upgradeable/access/Ownable2StepUpgradeable.sol";
```

- *LibAddress.sol* ( [4-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L4-L4), [5-5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L5-L5), [6-6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L6-L6), [7-7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L7-L7) ):

```solidity
4: import "@openzeppelin/contracts/utils/Address.sol";

5: import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol";

6: import "@openzeppelin/contracts/utils/introspection/IERC165.sol";

7: import "@openzeppelin/contracts/interfaces/IERC1271.sol";
```

- *SignalService.sol* ( [4-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L4-L4) ):

```solidity
4: import "@openzeppelin/contracts/utils/math/SafeCast.sol";
```

- *TimelockTokenPool.sol* ( [4-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L4-L4), [5-5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L5-L5), [6-6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L6-L6) ):

```solidity
4: import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol";

5: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

6: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```

- *ERC20Airdrop.sol* ( [4-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L4-L4), [5-5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L5-L5) ):

```solidity
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

5: import "@openzeppelin/contracts/governance/utils/IVotes.sol";
```

- *ERC20Airdrop2.sol* ( [4-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L4-L4) ):

```solidity
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```

- *ERC721Airdrop.sol* ( [4-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L4-L4) ):

```solidity
4: import "@openzeppelin/contracts/token/ERC721/IERC721.sol";
```

- *MerkleClaimable.sol* ( [4-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L4-L4) ):

```solidity
4: import "@openzeppelin/contracts/utils/cryptography/MerkleProof.sol";
```

- *BaseVault.sol* ( [4-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L4-L4), [5-5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L5-L5) ):

```solidity
4: import "@openzeppelin/contracts-upgradeable/utils/introspection/IERC165Upgradeable.sol";

5: import "@openzeppelin/contracts/proxy/ERC1967/ERC1967Proxy.sol";
```

- *BridgedERC1155.sol* ( [4-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L4-L4), [5-5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L5-L5), [6-7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L6-L7) ):

```solidity
4: import "@openzeppelin/contracts/utils/Strings.sol";

5: import "@openzeppelin/contracts-upgradeable/token/ERC1155/ERC1155Upgradeable.sol";

6: import
7:     "@openzeppelin/contracts-upgradeable/token/ERC1155/extensions/IERC1155MetadataURIUpgradeable.sol";
```

- *BridgedERC20.sol* ( [4-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L4-L4), [5-5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L5-L5), [6-6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L6-L6), [7-7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L7-L7) ):

```solidity
4: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/IERC20MetadataUpgradeable.sol";

5: import "@openzeppelin/contracts/utils/Strings.sol";

6: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20SnapshotUpgradeable.sol";

7: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20VotesUpgradeable.sol";
```

- *BridgedERC721.sol* ( [4-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L4-L4), [5-5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L5-L5) ):

```solidity
4: import "@openzeppelin/contracts-upgradeable/token/ERC721/ERC721Upgradeable.sol";

5: import "@openzeppelin/contracts/utils/Strings.sol";
```

- *ERC1155Vault.sol* ( [4-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L4-L4), [5-5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L5-L5) ):

```solidity
4: import "@openzeppelin/contracts/token/ERC1155/IERC1155.sol";

5: import "@openzeppelin/contracts-upgradeable/token/ERC1155/utils/ERC1155ReceiverUpgradeable.sol";
```

- *ERC20Vault.sol* ( [4-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L4-L4), [5-5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L5-L5), [6-6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L6-L6) ):

```solidity
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

5: import "@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol";

6: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```

- *ERC721Vault.sol* ( [4-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L4-L4), [5-5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L5-L5) ):

```solidity
4: import "@openzeppelin/contracts/token/ERC721/IERC721.sol";

5: import "@openzeppelin/contracts/token/ERC721/IERC721Receiver.sol";
```

- *LibBridgedToken.sol* ( [4-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L4-L4) ):

```solidity
4: import "@openzeppelin/contracts/utils/Strings.sol";
```

- *SgxVerifier.sol* ( [4-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L4-L4) ):

```solidity
4: import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol";
```

</details>

### [G-51] Use the inputs/results of assignments rather than re-reading state variables

When a state variable is assigned, it saves gas to use the value being assigned, later in the function, rather than re-reading the state variable itself. If needed, it can also be stored to a local variable, and be used in that way. Both options avoid a Gwarmaccess (**100 gas**). Note that if the operation is, say `+=`, the assignment also results in a value which can be used. The instances below point to the first reference after the assignment, since later references are already covered by issues describing the caching of state variable values.

There is 1 instance:

- *AutomataDcapV3Attestation.sol* ( [123-123](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L123-L123) ):

```solidity
/// @audit use result of assignment of _checkLocalEnclaveReport
123:         _checkLocalEnclaveReport = !_checkLocalEnclaveReport;
```

### [G-52] Structs can be packed into fewer storage slots by truncating fields

Some struct fields  can be safely modified so that the struct variable uses fewer storage slots. Each saved slot can avoid an extra Gsset (20000 gas) for the first setting of the struct. Subsequent reads as well as writes have smaller gas savings.

<details>
<summary>There are 2 instances (click to show):</summary>

- *TaikoData.sol* ( [10-60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L10-L60) ):

```solidity
/// @audit Truncate `blockMaxProposals` to `uint64`
/// @audit Truncate `blockRingBufferSize` to `uint64`
/// @audit Truncate `blockMaxGasLimit` to `uint64`
/// @audit Truncate `blockMaxTxListBytes` to `uint64`
/// @audit Truncate `blobExpiry` to `uint32`
/// @audit Truncate `ethDepositMinCountPerBlock` to `uint64`
/// @audit Truncate `ethDepositMaxCountPerBlock` to `uint64`
/// @audit Truncate `blockSyncThreshold` to `uint64`
/// @audit Fewer storage usage (8 slots -> 7 slots):
///        32 B: uint256 ethDepositRingBufferSize
///        32 B: uint256 ethDepositGas
///        32 B: uint256 ethDepositMaxFee
///        12 B: uint96 livenessBond
///        12 B: uint96 ethDepositMinAmount
///        8 B: uint64 chainId
///        12 B: uint96 ethDepositMaxAmount
///        8 B: uint64 blockMaxProposals
///        8 B: uint64 blockRingBufferSize
///        4 B: uint32 blobExpiry
///        8 B: uint64 maxBlocksToVerifyPerProposal
///        8 B: uint64 blockMaxGasLimit
///        8 B: uint64 blockMaxTxListBytes
///        8 B: uint64 ethDepositMinCountPerBlock
///        8 B: uint64 ethDepositMaxCountPerBlock
///        8 B: uint64 blockSyncThreshold
///        1 B: bool blobAllowedForDA
///        1 B: bool blobReuseEnabled
10:     struct Config {
11:         // ---------------------------------------------------------------------
12:         // Group 1: General configs
13:         // ---------------------------------------------------------------------
14:         // The chain ID of the network where Taiko contracts are deployed.
15:         uint64 chainId;
16:         // ---------------------------------------------------------------------
17:         // Group 2: Block level configs
18:         // ---------------------------------------------------------------------
19:         // The maximum number of proposals allowed in a single block.
20:         uint64 blockMaxProposals;
21:         // Size of the block ring buffer, allowing extra space for proposals.
22:         uint64 blockRingBufferSize;
23:         // The maximum number of verifications allowed when a block is proposed.
24:         uint64 maxBlocksToVerifyPerProposal;
25:         // The maximum gas limit allowed for a block.
26:         uint32 blockMaxGasLimit;
27:         // The maximum allowed bytes for the proposed transaction list calldata.
28:         uint24 blockMaxTxListBytes;
29:         // The max period in seconds that a blob can be reused for DA.
30:         uint24 blobExpiry;
31:         // True if EIP-4844 is enabled for DA
32:         bool blobAllowedForDA;
33:         // True if blob can be reused
34:         bool blobReuseEnabled;
...... OMITTED ......
36:         // Group 3: Proof related configs
37:         // ---------------------------------------------------------------------
38:         // The amount of Taiko token as a prover liveness bond
39:         uint96 livenessBond;
40:         // ---------------------------------------------------------------------
41:         // Group 4: ETH deposit related configs
42:         // ---------------------------------------------------------------------
43:         // The size of the ETH deposit ring buffer.
44:         uint256 ethDepositRingBufferSize;
45:         // The minimum number of ETH deposits allowed per block.
46:         uint64 ethDepositMinCountPerBlock;
47:         // The maximum number of ETH deposits allowed per block.
48:         uint64 ethDepositMaxCountPerBlock;
49:         // The minimum amount of ETH required for a deposit.
50:         uint96 ethDepositMinAmount;
51:         // The maximum amount of ETH allowed for a deposit.
52:         uint96 ethDepositMaxAmount;
53:         // The gas cost for processing an ETH deposit.
54:         uint256 ethDepositGas;
55:         // The maximum fee allowed for an ETH deposit.
56:         uint256 ethDepositMaxFee;
57:         // The max number of L2 blocks that can stay unsynced on L1 (a value of zero disables
58:         // syncing)
59:         uint8 blockSyncThreshold;
60:     }
```

- *ISignalService.sol* ( [20-27](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/ISignalService.sol#L20-L27) ):

```solidity
/// @audit Truncate `blockId` to `uint64`
/// @audit Fewer storage usage (5 slots -> 4 slots):
///        32 B: bytes32 rootHash
///        32 B: bytes[] accountProof
///        32 B: bytes[] storageProof
///        8 B: uint64 chainId
///        8 B: uint64 blockId
///        1 B: CacheOption cacheOption
20:     struct HopProof {
21:         uint64 chainId;
22:         uint64 blockId;
23:         bytes32 rootHash;
24:         CacheOption cacheOption;
25:         bytes[] accountProof;
26:         bytes[] storageProof;
27:     }
```

</details>

### [G-53] Redundant state variable getters

Getters for public state variables are automatically generated so there is no need to code them manually and waste gas.

There is 1 instance:

- *TaikoL2EIP1559Configurable.sol* ( [43-45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L43-L45) ):

```solidity
43:     function getConfig() public view override returns (Config memory) {
44:         return customConfig;
45:     }
```

### [G-54] Using `constant`s instead of `enum` can save gas

`Enum` is expensive and it is [more efficient to use constants](https://www.codehawks.com/finding/clm84992q02j9w9ruebun36d9) instead. An illustrative example of this approach can be found in the [ReentrancyGuard.sol](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/181d518609a9f006fcb97af63e6952e603cf100e/contracts/utils/ReentrancyGuard.sol#L34-L35).

<details>
<summary>There are 9 instances (click to show):</summary>

- *ISigVerifyLib.sol* ( [7-10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L7-L10), [19-22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L19-L22), [32-36](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L32-L36) ):

```solidity
7:     enum KeyType {
8:         RSA,
9:         ECDSA
10:     }

19:     enum CertSigAlgorithm {
20:         Sha256WithRSAEncryption,
21:         Sha1WithRSAEncryption
22:     }

32:     enum Algorithm {
33:         RS256,
34:         ES256,
35:         RS1
36:     }
```

- *EnclaveIdStruct.sol* ( [26-29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/EnclaveIdStruct.sol#L26-L29) ):

```solidity
26:     enum EnclaveIdStatus {
27:         OK,
28:         SGX_ENCLAVE_REPORT_ISVSVN_REVOKED
29:     }
```

- *TCBInfoStruct.sol* ( [19-28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol#L19-L28) ):

```solidity
19:     enum TCBStatus {
20:         OK,
21:         TCB_SW_HARDENING_NEEDED,
22:         TCB_CONFIGURATION_AND_SW_HARDENING_NEEDED,
23:         TCB_CONFIGURATION_NEEDED,
24:         TCB_OUT_OF_DATE,
25:         TCB_OUT_OF_DATE_CONFIGURATION_NEEDED,
26:         TCB_REVOKED,
27:         TCB_UNRECOGNIZED
28:     }
```

- *IPEMCertChainLib.sol* ( [31-34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L31-L34) ):

```solidity
31:     enum CRL {
32:         PCK,
33:         ROOT
34:     }
```

- *IBridge.sol* ( [9-15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/IBridge.sol#L9-L15) ):

```solidity
9:     enum Status {
10:         NEW,
11:         RETRIABLE,
12:         DONE,
13:         FAILED,
14:         RECALLED
15:     }
```

- *ISignalService.sol* ( [13-18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/ISignalService.sol#L13-L18) ):

```solidity
13:     enum CacheOption {
14:         CACHE_NOTHING,
15:         CACHE_SIGNAL_ROOT,
16:         CACHE_STATE_ROOT,
17:         CACHE_BOTH
18:     }
```

- *RLPReader.sol* ( [16-19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L16-L19) ):

```solidity
16:     enum RLPItemType {
17:         DATA_ITEM,
18:         LIST_ITEM
19:     }
```

</details>

### [G-55] Use `Array.unsafeAccess()` to avoid repeated array length checks

When using storage arrays, solidity adds an internal lookup of the array's length (a Gcoldsload **2100 gas**) to ensure you don't read past the array's end. You can avoid this lookup by using [`Array.unsafeAccess()`](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/94697be8a3f0dfcd95dfb13ffbd39b5973f5c65d/contracts/utils/Arrays.sol#L57) in cases where the length has already been checked, as is the case with the instances below.

There is 1 instance:

- *Guardians.sol* ( [75-75](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L75-L75) ):

```solidity
75:             delete guardianIds[guardians[i]];
```

### [G-56] Assembly: Use scratch space for building calldata

If an external call's calldata can fit into two or fewer words, use the scratch space to build the calldata, rather than allowing Solidity to do a memory expansion.

<details>
<summary>There are 61 instances (click to show):</summary>

- *AssignmentHook.sol* ( [149-149](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L149-L149) ):

```solidity
149:                 ITaikoL1(_taikoL1Address).getConfig().chainId,
```

- *LibDepositing.sol* ( [41-41](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L41-L41) ):

```solidity
41:         _resolver.resolve("bridge", false).sendEther(msg.value);
```

- *LibProposing.sol* ( [207-207](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L207-L207), [207-209](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L207-L209), [237-237](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L237-L237), [238-238](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L238-L238), [268-268](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L268-L268), [309-309](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L309-L309), [315-315](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L315-L315) ):

```solidity
207:         meta_.minTier = ITierProvider(_resolver.resolve("tier_provider", false)).getMinTier(

207:         meta_.minTier = ITierProvider(_resolver.resolve("tier_provider", false)).getMinTier(
208:             uint256(meta_.difficulty)
209:         );

237:             IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));

238:             uint256 tkoBalance = tko.balanceOf(address(this));

268:             if (tko.balanceOf(address(this)) != tkoBalance + _config.livenessBond) {

309:             address proposerOne = _resolver.resolve("proposer_one", true);

315:         address proposer = _resolver.resolve("proposer", true);
```

- *LibProving.sol* ( [141-141](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L141-L141), [141-141](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L141-L141), [161-161](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L161-L161), [187-187](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L187-L187), [196-196](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L196-L196), [367-367](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L367-L367), [371-371](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L371-L371), [382-382](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L382-L382) ):

```solidity
141:             ITierProvider(_resolver.resolve("tier_provider", false)).getTier(_proof.tier);

141:             ITierProvider(_resolver.resolve("tier_provider", false)).getTier(_proof.tier);

161:             address verifier = _resolver.resolve(tier.verifierName, true);

187:         IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));

196:                 tko.transfer(blk.assignedProver, blk.livenessBond);

367:                 _tko.transfer(_ts.prover, _ts.validityBond + reward);

371:                 _tko.transfer(_ts.contester, _ts.contestBond + reward);

382:                 _tko.transfer(msg.sender, reward - _tier.validityBond);
```

- *LibVerifying.sol* ( [149-149](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L149-L149), [152-152](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L152-L152), [188-188](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L188-L188), [189-189](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L189-L189), [232-232](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L232-L232) ):

```solidity
149:                         tierProvider = _resolver.resolve("tier_provider", false);

152:                         uint256(ITierProvider(tierProvider).getTier(ts.tier).cooldownWindow) * 60

188:                 IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));

189:                 tko.transfer(ts.prover, bondToReturn);

232:         ISignalService signalService = ISignalService(_resolver.resolve("signal_service", false));
```

- *GuardianProver.sol* ( [51-51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/GuardianProver.sol#L51-L51) ):

```solidity
51:             ITaikoL1(resolve("taiko", false)).proveBlock(_meta.id, abi.encode(_meta, _tran, _proof));
```

- *CrossChainOwned.sol* ( [45-45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L45-L45) ):

```solidity
45:         IBridge.Context memory ctx = IBridge(msg.sender).context();
```

- *TaikoL2.sol* ( [176-176](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L176-L176) ):

```solidity
176:             IERC20(_token).safeTransfer(_to, IERC20(_token).balanceOf(address(this)));
```

- *AutomataDcapV3Attestation.sol* ( [424-426](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L424-L426) ):

```solidity
424:                 (certDecodedSuccessfully, parsedQuoteCerts[i]) = pemCertLib.decodeCert(
425:                     authDataV3.certification.decodedCertDataArray[i], isPckCert
426:                 );
```

- *V3Parser.sol* ( [278-278](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L278-L278) ):

```solidity
278:             pemCertLib.splitCertificateChain(certBytes, 3);
```

- *Bridge.sol* ( [150-150](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L150-L150), [174-174](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L174-L174), [199-201](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L199-L201), [342-345](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L342-L345), [522-524](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L522-L524) ):

```solidity
150:         ISignalService(resolve("signal_service", false)).sendSignal(msgHash_);

174:             if (!ISignalService(signalService).isSignalSent(address(this), msgHash)) {

199:                 IRecallableSender(_message.from).onMessageRecalled{ value: _message.value }(
200:                     _message, msgHash
201:                 );

342:         return ISignalService(resolve("signal_service", false)).isSignalSent({
343:             _app: address(this),
344:             _signal: hashMessage(_message)
345:         });

522:             ISignalService(resolve("signal_service", false)).sendSignal(
523:                 signalForFailedMessage(_msgHash)
524:             );
```

- *AddressResolver.sol* ( [83-83](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L83-L83) ):

```solidity
83:         addr_ = payable(IAddressManager(addressManager).getAddress(_chainId, _name));
```

- *LibAddress.sol* ( [56-56](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L56-L56), [71-71](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L71-L71) ):

```solidity
56:         try IERC165(_addr).supportsInterface(_interfaceId) returns (bool _result) {

71:             return IERC1271(_addr).isValidSignature(_hash, _sig) == _EIP1271_MAGICVALUE;
```

- *BaseVault.sol* ( [53-53](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L53-L53), [64-64](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L64-L64) ):

```solidity
53:         ctx_ = IBridge(msg.sender).context();

64:         ctx_ = IBridge(msg.sender).context();
```

- *BridgedERC20Base.sol* ( [82-82](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L82-L82) ):

```solidity
82:             IBridgedERC20(migratingAddress).mint(_account, _amount);
```

- *ERC1155Vault.sol* ( [77-77](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L77-L77), [263-263](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L263-L263), [266-266](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L266-L266) ):

```solidity
77:             IBridge(resolve("bridge", false)).sendMessage{ value: msg.value }(message);

263:                 try t.name() returns (string memory _name) {

266:                 try t.symbol() returns (string memory _symbol) {
```

- *ERC20Vault.sol* ( [164-164](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L164-L164), [184-184](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L184-L184), [185-185](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L185-L185), [239-239](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L239-L239), [333-333](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L333-L333), [360-360](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L360-L360), [368-368](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L368-L368), [369-369](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L369-L369), [370-370](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L370-L370), [378-378](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L378-L378), [380-380](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L380-L380) ):

```solidity
164:         if (IBridgedERC20(_btokenNew).owner() != owner()) {

184:             IBridgedERC20(btokenOld_).changeMigrationStatus(_btokenNew, false);

185:             IBridgedERC20(_btokenNew).changeMigrationStatus(btokenOld_, true);

239:             IBridge(resolve("bridge", false)).sendMessage{ value: msg.value }(message);

333:             IBridgedERC20(token_).mint(_to, _amount);

360:             IBridgedERC20(_token).burn(msg.sender, _amount);

368:                 decimals: meta.decimals(),

369:                 symbol: meta.symbol(),

370:                 name: meta.name()

378:             uint256 _balance = t.balanceOf(address(this));

380:             balanceChange_ = t.balanceOf(address(this)) - _balance;
```

- *ERC721Vault.sol* ( [62-62](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L62-L62), [176-176](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L176-L176), [198-198](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L198-L198), [206-206](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L206-L206), [207-207](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L207-L207) ):

```solidity
62:             IBridge(resolve("bridge", false)).sendMessage{ value: msg.value }(message);

176:                 BridgedERC721(token_).mint(_to, _tokenIds[i]);

198:                     BridgedERC721(_op.token).burn(_user, _op.tokenIds[i]);

206:                     symbol: t.symbol(),

207:                     name: t.name()
```

- *USDCAdapter.sol* ( [44-44](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L44-L44), [49-49](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L49-L49) ):

```solidity
44:         usdc.mint(_account, _amount);

49:         usdc.burn(_amount);
```

- *SgxVerifier.sol* ( [128-128](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L128-L128), [185-185](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L185-L185) ):

```solidity
128:         (bool verified,) = IAttestation(automataDcapAttestation).verifyParsedQuote(_attestation);

185:                 ITaikoL1(taikoL1).getConfig().chainId,
```

</details>

### [G-57] Use assembly to emit events

To efficiently emit events, it's possible to utilize assembly by making use of scratch space and the free memory pointer. This approach has the advantage of potentially avoiding the costs associated with memory expansion.

However, it's important to note that in order to safely optimize this process, it is preferable to cache and restore the free memory pointer.

A good example of such practice can be seen in [Solady's](https://github.com/Vectorized/solady/blob/main/src/tokens/ERC1155.sol#L167) codebase.

<details>
<summary>There are 36 instances (click to show):</summary>

- *AssignmentHook.sol* ( [129-129](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L129-L129) ):

```solidity
129:         emit BlockAssigned(_blk.assignedProver, _meta, assignment);
```

- *LibDepositing.sol* ( [50-56](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L50-L56) ):

```solidity
50:         emit EthDeposited(
51:             TaikoData.EthDeposit({
52:                 recipient: recipient_,
53:                 amount: uint96(msg.value),
54:                 id: _state.slotA.numEthDeposits
55:             })
56:         );
```

- *LibProposing.sol* ( [166-166](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L166-L166) ):

```solidity
166:                     emit BlobCached(meta_.blobHash);
```

- *LibProving.sol* ( [80-80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L80-L80) ):

```solidity
80:         emit ProvingPaused(_pause);
```

- *GuardianProver.sol* ( [54-54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/GuardianProver.sol#L54-L54) ):

```solidity
54:         emit GuardianApproval(msg.sender, _meta.id, _tran.blockHash, approved_);
```

- *Guardians.sol* ( [95-95](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L95-L95), [121-121](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L121-L121) ):

```solidity
95:         emit GuardiansUpdated(version, _newGuardians);

121:         emit Approved(_operationId, _approval, approved_);
```

- *CrossChainOwned.sol* ( [53-53](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L53-L53) ):

```solidity
53:         emit TransactionExecuted(nextTxId++, bytes4(txdata));
```

- *TaikoL2.sol* ( [157-157](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L157-L157) ):

```solidity
157:         emit Anchored(blockhash(parentId), gasExcess);
```

- *TaikoL2EIP1559Configurable.sol* ( [39-39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L39-L39) ):

```solidity
39:         emit ConfigAndExcessChanged(_newConfig, _newGasExcess);
```

- *Bridge.sol* ( [93-93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L93-L93), [111-111](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L111-L111), [151-151](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L151-L151), [208-208](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L208-L208), [210-210](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L210-L210), [301-301](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L301-L301), [303-303](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L303-L303), [336-336](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L336-L336), [519-519](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L519-L519) ):

```solidity
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

- *AddressManager.sol* ( [50-50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L50-L50) ):

```solidity
50:         emit AddressSet(_chainId, _name, _newAddress, oldAddress);
```

- *EssentialContract.sol* ( [71-71](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L71-L71), [80-80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L80-L80) ):

```solidity
71:         emit Paused(msg.sender);

80:         emit Unpaused(msg.sender);
```

- *SignalService.sol* ( [59-59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L59-L59), [250-250](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L250-L250) ):

```solidity
59:         emit Authorized(_addr, _authorize);

250:         emit ChainDataSynced(_chainId, _blockId, _kind, _chainData, signal_);
```

- *TimelockTokenPool.sol* ( [143-143](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L143-L143), [157-157](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L157-L157) ):

```solidity
143:         emit Granted(_recipient, _grant);

157:         emit Voided(_recipient, amountVoided);
```

- *ERC20Airdrop2.sol* ( [93-93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L93-L93) ):

```solidity
93:         emit Withdrawn(user, amount);
```

- *MerkleClaimable.sol* ( [74-74](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L74-L74) ):

```solidity
74:         emit Claimed(hash);
```

- *BridgedERC20Base.sol* ( [51-51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L51-L51), [63-63](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L63-L63), [80-80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L80-L80) ):

```solidity
51:         emit MigrationStatusChanged(_migratingAddress, _migratingInbound);

63:             emit MigratedTo(migratingAddress, _account, _amount);

80:             emit MigratedTo(migratingAddress, _account, _amount);
```

- *ERC1155Vault.sol* ( [314-320](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L314-L320) ):

```solidity
314:         emit BridgedTokenDeployed({
315:             chainId: _ctoken.chainId,
316:             ctoken: _ctoken.addr,
317:             btoken: btoken_,
318:             ctokenSymbol: _ctoken.symbol,
319:             ctokenName: _ctoken.name
320:         });
```

- *ERC721Vault.sol* ( [250-256](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L250-L256) ):

```solidity
250:         emit BridgedTokenDeployed({
251:             chainId: _ctoken.chainId,
252:             ctoken: _ctoken.addr,
253:             btoken: btoken_,
254:             ctokenSymbol: _ctoken.symbol,
255:             ctokenName: _ctoken.name
256:         });
```

- *SgxVerifier.sol* ( [109-109](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L109-L109), [220-220](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220-L220), [230-230](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L230-L230) ):

```solidity
109:             emit InstanceDeleted(idx, instances[idx].addr);

220:             emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);

230:         emit InstanceAdded(id, newInstance, oldInstance, block.timestamp);
```

</details>

### [G-58] Use assembly to compute hashes to save gas

If the arguments to the encode call can fit into the scratch space (two words or fewer), then it's more efficient to use assembly to generate the hash (**80 gas**):

`keccak256(abi.encodePacked(x, y))` -> `assembly {mstore(0x00, a); mstore(0x20, b); let hash := keccak256(0x00, 0x40); }`

There are 2 instances:

- *SignalService.sol* ( [186-186](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L186-L186) ):

```solidity
186:         return keccak256(abi.encode(_chainId, _kind, _blockId));
```

- *TimelockTokenPool.sol* ( [170-170](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L170-L170) ):

```solidity
170:         bytes32 hash = keccak256(abi.encodePacked("Withdraw unlocked Taiko token to: ", _to));
```

### [G-59] Use `calldata` instead of `memory` for immutable arguments

Mark data types as `calldata` instead of `memory` where possible. This makes it so that the data is not automatically loaded into memory. If the data passed into the function does not need to be changed (like updating values in an array), it can be passed in as `calldata`. The one exception to this is if the argument must later be passed into another function that takes an argument that specifies `memory` storage.

<details>
<summary>There are 70 instances (click to show):</summary>

- *TaikoGovernor.sol* ( [48-53](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L48-L53), [69-75](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L69-L75) ):

```solidity
/// @audit _targets
/// @audit _values
/// @audit _calldatas
/// @audit _description
48:     function propose(
49:         address[] memory _targets,
50:         uint256[] memory _values,
51:         bytes[] memory _calldatas,
52:         string memory _description
53:     )

/// @audit _targets
/// @audit _values
/// @audit _signatures
/// @audit _calldatas
/// @audit _description
69:     function propose(
70:         address[] memory _targets,
71:         uint256[] memory _values,
72:         string[] memory _signatures,
73:         bytes[] memory _calldatas,
74:         string memory _description
75:     )
```

- *AssignmentHook.sol* ( [62-66](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L62-L66), [137-141](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L137-L141) ):

```solidity
/// @audit _blk
/// @audit _meta
/// @audit _data
62:     function onBlockProposed(
63:         TaikoData.Block memory _blk,
64:         TaikoData.BlockMetadata memory _meta,
65:         bytes memory _data
66:     )

/// @audit _assignment
137:     function hashAssignment(
138:         ProverAssignment memory _assignment,
139:         address _taikoL1Address,
140:         bytes32 _blobHash
141:     )
```

- *IHook.sol* ( [13-17](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/IHook.sol#L13-L17) ):

```solidity
/// @audit _blk
/// @audit _meta
/// @audit _data
13:     function onBlockProposed(
14:         TaikoData.Block memory _blk,
15:         TaikoData.BlockMetadata memory _meta,
16:         bytes memory _data
17:     )
```

- *LibUtils.sol* ( [23-28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L23-L28), [52-56](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L52-L56) ):

```solidity
/// @audit _config
23:     function getTransition(
24:         TaikoData.State storage _state,
25:         TaikoData.Config memory _config,
26:         uint64 _blockId,
27:         bytes32 _parentHash
28:     )

/// @audit _config
52:     function getBlock(
53:         TaikoData.State storage _state,
54:         TaikoData.Config memory _config,
55:         uint64 _blockId
56:     )
```

- *LibVerifying.sol* ( [47-51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L47-L51) ):

```solidity
/// @audit _config
47:     function init(
48:         TaikoData.State storage _state,
49:         TaikoData.Config memory _config,
50:         bytes32 _genesisBlockHash
51:     )
```

- *Guardians.sol* ( [53-56](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L53-L56) ):

```solidity
/// @audit _newGuardians
53:     function setGuardians(
54:         address[] memory _newGuardians,
55:         uint8 _minGuardians
56:     )
```

- *TaikoL2EIP1559Configurable.sol* ( [25-28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L25-L28) ):

```solidity
/// @audit _newConfig
25:     function setConfigAndExcess(
26:         Config memory _newConfig,
27:         uint64 _newGasExcess
28:     )
```

- *ISigVerifyLib.sol* ( [38-43](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L38-L43), [48-53](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L48-L53), [58-62](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L58-L62), [67-71](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L67-L71), [76-80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L76-L80) ):

```solidity
/// @audit tbs
/// @audit signature
/// @audit publicKey
38:     function verifyAttStmtSignature(
39:         bytes memory tbs,
40:         bytes memory signature,
41:         PublicKey memory publicKey,
42:         Algorithm alg
43:     )

/// @audit tbs
/// @audit signature
/// @audit publicKey
48:     function verifyCertificateSignature(
49:         bytes memory tbs,
50:         bytes memory signature,
51:         PublicKey memory publicKey,
52:         CertSigAlgorithm alg
53:     )

/// @audit tbs
/// @audit signature
/// @audit publicKey
58:     function verifyRS256Signature(
59:         bytes memory tbs,
60:         bytes memory signature,
61:         bytes memory publicKey
62:     )

/// @audit tbs
/// @audit signature
/// @audit publicKey
67:     function verifyRS1Signature(
68:         bytes memory tbs,
69:         bytes memory signature,
70:         bytes memory publicKey
71:     )

/// @audit tbs
/// @audit signature
/// @audit publicKey
76:     function verifyES256Signature(
77:         bytes memory tbs,
78:         bytes memory signature,
79:         bytes memory publicKey
80:     )
```

- *PEMCertChainLib.sol* ( [40-43](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L40-L43), [74-77](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L74-L77) ):

```solidity
/// @audit pemChain
40:     function splitCertificateChain(
41:         bytes memory pemChain,
42:         uint256 size
43:     )

/// @audit der
74:     function decodeCert(
75:         bytes memory der,
76:         bool isPckCert
77:     )
```

- *IPEMCertChainLib.sol* ( [36-39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L36-L39), [44-47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L44-L47) ):

```solidity
/// @audit pemChain
36:     function splitCertificateChain(
37:         bytes memory pemChain,
38:         uint256 size
39:     )

/// @audit der
44:     function decodeCert(
45:         bytes memory der,
46:         bool isPckCert
47:     )
```

- *SigVerifyLib.sol* ( [24-29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L24-L29), [54-59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L54-L59), [79-83](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L79-L83), [96-100](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L96-L100), [113-117](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L113-L117) ):

```solidity
/// @audit tbs
/// @audit signature
/// @audit publicKey
24:     function verifyAttStmtSignature(
25:         bytes memory tbs,
26:         bytes memory signature,
27:         PublicKey memory publicKey,
28:         Algorithm alg
29:     )

/// @audit tbs
/// @audit signature
/// @audit publicKey
54:     function verifyCertificateSignature(
55:         bytes memory tbs,
56:         bytes memory signature,
57:         PublicKey memory publicKey,
58:         CertSigAlgorithm alg
59:     )

/// @audit tbs
/// @audit signature
/// @audit publicKey
79:     function verifyRS256Signature(
80:         bytes memory tbs,
81:         bytes memory signature,
82:         bytes memory publicKey
83:     )

/// @audit tbs
/// @audit signature
/// @audit publicKey
96:     function verifyRS1Signature(
97:         bytes memory tbs,
98:         bytes memory signature,
99:         bytes memory publicKey
100:     )

/// @audit tbs
/// @audit signature
/// @audit publicKey
113:     function verifyES256Signature(
114:         bytes memory tbs,
115:         bytes memory signature,
116:         bytes memory publicKey
117:     )
```

- *Bridge.sol* ( [449-449](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L449-L449) ):

```solidity
/// @audit _message
449:     function hashMessage(Message memory _message) public pure returns (bytes32) {
```

- *IBridge.sol* ( [155-155](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/IBridge.sol#L155-L155) ):

```solidity
/// @audit _message
155:     function hashMessage(Message memory _message) external pure returns (bytes32);
```

- *TimelockTokenPool.sol* ( [135-135](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L135-L135), [168-168](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L168-L168) ):

```solidity
/// @audit _grant
135:     function grant(address _recipient, Grant memory _grant) external onlyOwner {

/// @audit _sig
168:     function withdraw(address _to, bytes memory _sig) external {
```

- *BridgedERC1155.sol* ( [38-45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L38-L45), [83-87](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L83-L87) ):

```solidity
/// @audit _symbol
/// @audit _name
38:     function init(
39:         address _owner,
40:         address _addressManager,
41:         address _srcToken,
42:         uint256 _srcChainId,
43:         string memory _symbol,
44:         string memory _name
45:     )

/// @audit _tokenIds
/// @audit _amounts
83:     function mintBatch(
84:         address _to,
85:         uint256[] memory _tokenIds,
86:         uint256[] memory _amounts
87:     )
```

- *BridgedERC20.sol* ( [52-60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L52-L60) ):

```solidity
/// @audit _symbol
/// @audit _name
52:     function init(
53:         address _owner,
54:         address _addressManager,
55:         address _srcToken,
56:         uint256 _srcChainId,
57:         uint8 _decimals,
58:         string memory _symbol,
59:         string memory _name
60:     )
```

- *BridgedERC721.sol* ( [31-38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L31-L38) ):

```solidity
/// @audit _symbol
/// @audit _name
31:     function init(
32:         address _owner,
33:         address _addressManager,
34:         address _srcToken,
35:         uint256 _srcChainId,
36:         string memory _symbol,
37:         string memory _name
38:     )
```

- *ERC1155Vault.sol* ( [39-39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L39-L39) ):

```solidity
/// @audit _op
39:     function sendToken(BridgeTransferOp memory _op)
```

- *ERC721Vault.sol* ( [26-26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L26-L26) ):

```solidity
/// @audit _op
26:     function sendToken(BridgeTransferOp memory _op)
```

- *SgxVerifier.sol* ( [171-176](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L171-L176) ):

```solidity
/// @audit _tran
171:     function getSignedHash(
172:         TaikoData.Transition memory _tran,
173:         address _newInstance,
174:         address _prover,
175:         bytes32 _metaHash
176:     )
```

</details>

### [G-60] Consider Using Solady's Gas Optimized Lib for Math

In instances where many similar mathematical operations are performed, consider using Solady's math lib to benefit from the gas saving it can introduce.

<details>
<summary>There are 6 instances (click to show):</summary>

- *TaikoL2.sol* ( [213-213](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L213-L213) ):

```solidity
213:         config_.gasTargetPerL1Block = 15 * 1e6 * 4;
```

- *V3Parser.sol* ( [159-159](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L159-L159) ):

```solidity
159:             acc += upperDigit * (16 ** ((2 * i) + 1));
```

- *BytesUtils.sol* ( [93-93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L93-L93) ):

```solidity
93:                     mask = ~(2 ** (8 * (32 - shortest + idx)) - 1);
```

- *X509DateUtils.sol* ( [21-21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L21-L21) ):

```solidity
21:             yrs += (uint8(x509Time[0]) - 48) * 1000 + (uint8(x509Time[1]) - 48) * 100;
```

- *RLPWriter.sol* ( [47-47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L47-L47) ):

```solidity
47:                 out_[i] = bytes1(uint8((_len / (256 ** (lenLen - i))) % 256));
```

- *LibFixedPointMath.sol* ( [33-33](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L33-L33) ):

```solidity
33:             x = (x << 78) / 5 ** 18;
```

</details>

### [G-61] `do`-`while` is cheaper than `for`-loops when the initial check can be skipped

`for (uint256 i; i < len; ++i){ ... }` -> `do { ...; ++i } while (i < len);`

<details>
<summary>There are 49 instances (click to show):</summary>

- *AssignmentHook.sol* ( [172](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L172) ):

```solidity
172:         for (uint256 i; i < _tierFees.length; ++i) {
```

- *LibDepositing.sol* ( [86](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L86) ):

```solidity
86:             for (uint256 i; i < deposits_.length;) {
```

- *LibProposing.sol* ( [244](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L244) ):

```solidity
244:             for (uint256 i; i < params.hookCalls.length; ++i) {
```

- *Guardians.sol* ( [74](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L74), [80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L80), [133](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L133) ):

```solidity
74:         for (uint256 i; i < guardians.length; ++i) {

80:         for (uint256 i = 0; i < _newGuardians.length; ++i) {

133:             for (uint256 i; i < guardiansLength; ++i) {
```

- *TaikoL2.sol* ( [234](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L234) ):

```solidity
234:             for (uint256 i; i < 255 && _blockId >= i + 1; ++i) {
```

- *AutomataDcapV3Attestation.sol* ( [80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L80), [95](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L95), [191](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L191), [214](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L214), [240](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L240), [259](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L259), [420](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L420) ):

```solidity
80:         for (uint256 i; i < serialNumBatch.length; ++i) {

95:         for (uint256 i; i < serialNumBatch.length; ++i) {

191:         for (uint256 i; i < enclaveId.tcbLevels.length; ++i) {

214:         for (uint256 i; i < tcb.tcbLevels.length; ++i) {

240:         for (uint256 i; i < CPUSVN_LENGTH; ++i) {

259:         for (uint256 i; i < n; ++i) {

420:             for (uint256 i; i < 3; ++i) {
```

- *PEMCertChainLib.sol* ( [54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L54), [244](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L244), [354](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L354) ):

```solidity
54:         for (uint256 i; i < size; ++i) {

244:         for (uint256 i; i < split.length; ++i) {

354:         for (uint256 i; i < SGX_TCB_CPUSVN_SIZE + 1; ++i) {
```

- *V3Parser.sol* ( [153](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L153), [281](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L281) ):

```solidity
153:         for (uint256 i; i < encoded.length; ++i) {

281:         for (uint256 i; i < 3; ++i) {
```

- *BytesUtils.sol* ( [80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L80), [333](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L333) ):

```solidity
80:         for (uint256 idx = 0; idx < shortest; idx += 32) {

333:         for (uint256 i; i < len; ++i) {
```

- *RsaVerify.sol* ( [140](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L140), [152](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L152), [158](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L158), [174](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L174), [273](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L273), [283](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L283), [290](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L290) ):

```solidity
140:         for (uint256 i = 2; i < 2 + paddingLen; ++i) {

152:             for (uint256 i; i < digestAlgoWithParamLen; ++i) {

158:             for (uint256 i; i < digestAlgoWithParamLen; ++i) {

174:         for (uint256 i; i < _sha256.length; ++i) {

273:         for (uint256 i = 2; i < 2 + paddingLen; ++i) {

283:         for (uint256 i; i < sha1Prefix.length; ++i) {

290:         for (uint256 i; i < _sha1.length; ++i) {
```

- *X509DateUtils.sol* ( [48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L48), [59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L59) ):

```solidity
48:         for (uint16 i = 1970; i < year; ++i) {

59:         for (uint8 i = 1; i < month; ++i) {
```

- *Bridge.sol* ( [90](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L90) ):

```solidity
90:         for (uint256 i; i < _msgHashes.length; ++i) {
```

- *SignalService.sol* ( [104](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L104) ):

```solidity
104:         for (uint256 i; i < hopProofs.length; ++i) {
```

- *ERC721Airdrop.sol* ( [59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59) ):

```solidity
59:         for (uint256 i; i < tokenIds.length; ++i) {
```

- *RLPWriter.sol* ( [46](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L46), [59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L59), [66](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66) ):

```solidity
46:             for (i = 1; i <= lenLen; i++) {

59:         for (; i < 32; i++) {

66:         for (uint256 j = 0; j < out_.length; j++) {
```

- *MerkleTrie.sol* ( [85](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85), [208](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L208), [244](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L244) ):

```solidity
85:         for (uint256 i = 0; i < proof.length; i++) {

208:         for (uint256 i = 0; i < length;) {

244:         for (; shared_ < max && _a[shared_] == _b[shared_];) {
```

- *ERC1155Vault.sol* ( [47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L47), [251](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L251), [269](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L269) ):

```solidity
47:         for (uint256 i; i < _op.amounts.length; ++i) {

251:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

269:                 for (uint256 i; i < _op.tokenIds.length; ++i) {
```

- *ERC721Vault.sol* ( [34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L34), [170](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L170), [175](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L175), [197](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L197), [210](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L210) ):

```solidity
34:         for (uint256 i; i < _op.tokenIds.length; ++i) {

170:             for (uint256 i; i < _tokenIds.length; ++i) {

175:             for (uint256 i; i < _tokenIds.length; ++i) {

197:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

210:                 for (uint256 i; i < _op.tokenIds.length; ++i) {
```

- *SgxVerifier.sol* ( [104](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L104), [210](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210) ):

```solidity
104:         for (uint256 i; i < _ids.length; ++i) {

210:         for (uint256 i; i < _instances.length; ++i) {
```

</details>

### [G-62] Avoid Unnecessary Public Variables

Public state variables automatically generate getter functions, increasing contract size and potentially leading to higher deployment and interaction costs. To optimize gas usage and contract efficiency, minimize the use of public variables unless external access is necessary. Instead, use internal or private visibility combined with explicit getter functions when required. This practice not only reduces contract size but also provides better control over data access and manipulation, enhancing security and readability. Prioritize lean, efficient contracts to ensure cost-effectiveness and better performance on the blockchain.

<details>
<summary>There are 41 instances (click to show):</summary>

- *TaikoL1.sol* ( [24-24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L24-L24) ):

```solidity
24:     TaikoData.State public state;
```

- *Guardians.sol* ( [27-27](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L27-L27), [30-30](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L30-L30) ):

```solidity
27:     uint32 public version;

30:     uint32 public minGuardians;
```

- *CrossChainOwned.sol* ( [16-16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L16-L16), [19-19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L19-L19) ):

```solidity
16:     uint64 public ownerChainId;

19:     uint64 public nextTxId;
```

- *TaikoL2.sol* ( [43-43](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L43-L43), [47-47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L47-L47), [50-50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L50-L50) ):

```solidity
43:     bytes32 public publicInputHash;

47:     uint64 public gasExcess;

50:     uint64 public lastSyncedBlock;
```

- *TaikoL2EIP1559Configurable.sol* ( [11-11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L11-L11) ):

```solidity
11:     Config public customConfig;
```

- *AutomataDcapV3Attestation.sol* ( [50-50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L50-L50), [52-52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L52-L52) ):

```solidity
50:     EnclaveIdStruct.EnclaveId public qeIdentity;

52:     address public owner;
```

- *Bridge.sol* ( [31-31](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L31-L31) ):

```solidity
31:     uint128 public nextMessageId;
```

- *AddressResolver.sol* ( [13-13](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L13-L13) ):

```solidity
13:     address public addressManager;
```

- *TimelockTokenPool.sol* ( [59-59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L59-L59), [62-62](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L62-L62), [65-65](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L65-L65), [68-68](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L68-L68), [71-71](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L71-L71), [74-74](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L74-L74), [77-77](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L77-L77) ):

```solidity
59:     address public taikoToken;

62:     address public costToken;

65:     address public sharedVault;

68:     uint128 public totalAmountGranted;

71:     uint128 public totalAmountVoided;

74:     uint128 public totalAmountWithdrawn;

77:     uint128 public totalCostPaid;
```

- *ERC20Airdrop.sol* ( [13-13](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L13-L13), [16-16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L16-L16) ):

```solidity
13:     address public token;

16:     address public vault;
```

- *ERC20Airdrop2.sol* ( [16-16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L16-L16), [19-19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L19-L19), [28-28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L28-L28) ):

```solidity
16:     address public token;

19:     address public vault;

28:     uint64 public withdrawalWindow;
```

- *ERC721Airdrop.sol* ( [11-11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L11-L11), [14-14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L14-L14) ):

```solidity
11:     address public token;

14:     address public vault;
```

- *MerkleClaimable.sol* ( [15-15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L15-L15), [18-18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L18-L18), [21-21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L21-L21) ):

```solidity
15:     bytes32 public merkleRoot;

18:     uint64 public claimStart;

21:     uint64 public claimEnd;
```

- *BridgedERC1155.sol* ( [16-16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L16-L16), [19-19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L19-L19) ):

```solidity
16:     address public srcToken;

19:     uint256 public srcChainId;
```

- *BridgedERC20.sol* ( [22-22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L22-L22), [27-27](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L27-L27), [30-30](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L30-L30) ):

```solidity
22:     address public srcToken;

27:     uint256 public srcChainId;

30:     address public snapshooter;
```

- *BridgedERC20Base.sol* ( [11-11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L11-L11), [14-14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L14-L14) ):

```solidity
11:     address public migratingAddress;

14:     bool public migratingInbound;
```

- *BridgedERC721.sol* ( [14-14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L14-L14), [17-17](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L17-L17) ):

```solidity
14:     address public srcToken;

17:     uint256 public srcChainId;
```

- *USDCAdapter.sol* ( [31-31](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L31-L31) ):

```solidity
31:     IUSDC public usdc;
```

- *SgxVerifier.sol* ( [39-39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L39-L39) ):

```solidity
39:     uint256 public nextInstanceId;
```

</details>

### [G-63] Optimize Deployment Size by Fine-tuning IPFS Hash

Optimizing the deployment size of a smart contract is vital to minimize gas costs, and one way to achieve this is by fine-tuning the IPFS hash appended by the Solidity compiler as metadata. This metadata, consisting of 53 bytes, increases the gas required for contract deployment by approximately 10,600 gas due to bytecode costs, and additionally, up to 848 gas due to calldata costs, depending on the proportion of zero and non-zero bytes. Utilize the --no-cbor-metadata compiler flag to prevent the compiler from appending metadata. However, this approach has a drawback as it can complicate the contract verification process on block explorers like Etherscan, potentially reducing transparency.

<details>
<summary>There are 30 instances (click to show):</summary>

- *TaikoL1.sol* ( [22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L22) ):

```solidity
22: contract TaikoL1 is EssentialContract, ITaikoL1, TaikoEvents, TaikoErrors {
```

- *TaikoToken.sol* ( [15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L15) ):

```solidity
15: contract TaikoToken is EssentialContract, ERC20SnapshotUpgradeable, ERC20VotesUpgradeable {
```

- *TaikoGovernor.sol* ( [16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L16) ):

```solidity
16: contract TaikoGovernor is
```

- *TaikoTimelockController.sol* ( [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L9) ):

```solidity
9: contract TaikoTimelockController is EssentialContract, TimelockControllerUpgradeable {
```

- *AssignmentHook.sol* ( [14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L14) ):

```solidity
14: contract AssignmentHook is EssentialContract, IHook {
```

- *GuardianProver.sol* ( [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/GuardianProver.sol#L10) ):

```solidity
10: contract GuardianProver is Guardians {
```

- *DevnetTierProvider.sol* ( [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L10) ):

```solidity
10: contract DevnetTierProvider is EssentialContract, ITierProvider {
```

- *MainnetTierProvider.sol* ( [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L10) ):

```solidity
10: contract MainnetTierProvider is EssentialContract, ITierProvider {
```

- *TestnetTierProvider.sol* ( [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L10) ):

```solidity
10: contract TestnetTierProvider is EssentialContract, ITierProvider {
```

- *TaikoL2.sol* ( [21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L21) ):

```solidity
21: contract TaikoL2 is CrossChainOwned {
```

- *TaikoL2EIP1559Configurable.sol* ( [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L9) ):

```solidity
9: contract TaikoL2EIP1559Configurable is TaikoL2 {
```

- *AutomataDcapV3Attestation.sol* ( [22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L22) ):

```solidity
22: contract AutomataDcapV3Attestation is IAttestation {
```

- *PEMCertChainLib.sol* ( [12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L12) ):

```solidity
12: contract PEMCertChainLib is IPEMCertChainLib {
```

- *SigVerifyLib.sol* ( [15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L15) ):

```solidity
15: contract SigVerifyLib is ISigVerifyLib {
```

- *Bridge.sol* ( [16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L16) ):

```solidity
16: contract Bridge is EssentialContract, IBridge {
```

- *AddressManager.sol* ( [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L10) ):

```solidity
10: contract AddressManager is EssentialContract, IAddressManager {
```

- *SignalService.sol* ( [14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L14) ):

```solidity
14: contract SignalService is EssentialContract, ISignalService {
```

- *TimelockTokenPool.sol* ( [25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L25) ):

```solidity
25: contract TimelockTokenPool is EssentialContract {
```

- *ERC20Airdrop.sol* ( [11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L11) ):

```solidity
11: contract ERC20Airdrop is MerkleClaimable {
```

- *ERC20Airdrop2.sol* ( [12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L12) ):

```solidity
12: contract ERC20Airdrop2 is MerkleClaimable {
```

- *ERC721Airdrop.sol* ( [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L9) ):

```solidity
9: contract ERC721Airdrop is MerkleClaimable {
```

- *BridgedERC1155.sol* ( [14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L14) ):

```solidity
14: contract BridgedERC1155 is EssentialContract, IERC1155MetadataURIUpgradeable, ERC1155Upgradeable {
```

- *BridgedERC20.sol* ( [15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L15) ):

```solidity
15: contract BridgedERC20 is
```

- *BridgedERC721.sol* ( [12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L12) ):

```solidity
12: contract BridgedERC721 is EssentialContract, ERC721Upgradeable {
```

- *ERC1155Vault.sol* ( [29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L29) ):

```solidity
29: contract ERC1155Vault is BaseNFTVault, ERC1155ReceiverUpgradeable {
```

- *ERC20Vault.sol* ( [18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L18) ):

```solidity
18: contract ERC20Vault is BaseVault {
```

- *ERC721Vault.sol* ( [16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L16) ):

```solidity
16: contract ERC721Vault is BaseNFTVault, IERC721Receiver {
```

- *USDCAdapter.sol* ( [28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L28) ):

```solidity
28: contract USDCAdapter is BridgedERC20Base {
```

- *GuardianVerifier.sol* ( [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L10) ):

```solidity
10: contract GuardianVerifier is EssentialContract, IVerifier {
```

- *SgxVerifier.sol* ( [19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L19) ):

```solidity
19: contract SgxVerifier is EssentialContract, IVerifier {
```

</details>

### [G-64] The result of a function call should be cached rather than re-calling the function

The function calls in solidity are expensive. If the same result of the same function calls are to be used several times, the result should be cached to reduce the gas consumption of repeated calls.

<details>
<summary>There are 38 instances (click to show):</summary>

- *LibProposing.sol* ( [68](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L68) ):

```solidity
/// @audit `tko.balanceOf(address(this))` called on lines: 238, 268
68:     function proposeBlock(
```

- *PEMCertChainLib.sol* ( [74](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L74), [269](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L269) ):

```solidity
/// @audit `der.nextSiblingOf(tbsPtr)` called on lines: 104, 111, 112, 127, 144, 157, 186
/// @audit `der.firstChildOf(tbsPtr)` called on lines: 115, 130, 147, 161, 193, 194
/// @audit `der.firstChildOf(issuerPtr)` called on lines: 116, 117
/// @audit `der.firstChildOf(subjectPtr)` called on lines: 148, 149
/// @audit `der.nextSiblingOf(sigPtr)` called on lines: 167, 176
/// @audit `_trimBytes(der.bytesAt(sigPtr),32)` called on lines: 174, 177
/// @audit `der.bytesAt(sigPtr)` called on lines: 174, 177
74:     function decodeCert(

/// @audit `der.bytesAt(extnValueOidPtr)` called on lines: 306, 310, 316
/// @audit `der.nextSiblingOf(extnValueOidPtr)` called on lines: 312, 318
269:     function _findPckTcbInfo(
```

- *Asn1Decode.sol* ( [98](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L98), [111](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L111), [121](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L121), [131](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L131), [141](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L141), [154](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L154), [165](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L165), [169](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L169), [179](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L179) ):

```solidity
/// @audit `j.ixl()` called on lines: 100, 101
/// @audit `i.ixl()` called on lines: 100, 101
98:     function isChildOf(uint256 i, uint256 j) internal pure returns (bool) {

/// @audit `ptr.ixf()` called on lines: 112, 112
111:     function bytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes memory) {

/// @audit `ptr.ixs()` called on lines: 122, 122
121:     function allBytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes memory) {

/// @audit `ptr.ixf()` called on lines: 132, 132
131:     function bytes32At(bytes memory der, uint256 ptr) internal pure returns (bytes32) {

/// @audit `ptr.ixf()` called on lines: 143, 144, 145
141:     function uintAt(bytes memory der, uint256 ptr) internal pure returns (uint256) {

/// @audit `ptr.ixf()` called on lines: 156, 157, 158, 159, 161
154:     function uintBytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes memory) {

/// @audit `ptr.ixf()` called on lines: 166, 166
165:     function keccakOfBytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes32) {

/// @audit `ptr.ixs()` called on lines: 170, 170
169:     function keccakOfAllBytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes32) {

/// @audit `ptr.ixf()` called on lines: 182, 183, 184
179:     function bitstringAt(bytes memory der, uint256 ptr) internal pure returns (bytes memory) {
```

- *RLPReader.sol* ( [53](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L53) ):

```solidity
/// @audit `MemoryPointer.wrap(MemoryPointer.unwrap(_in.ptr)+offset)` called on lines: 78, 86
/// @audit `MemoryPointer.unwrap(_in.ptr)` called on lines: 78, 86
53:     function readList(RLPItem memory _in) internal pure returns (RLPItem[] memory out_) {
```

- *ERC20Vault.sol* ( [348](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L348) ):

```solidity
/// @audit `t.balanceOf(address(this))` called on lines: 378, 380
348:     function _handleMessage(
```

</details>

### [G-65] Multiple accesses of a `memory`/`calldata` array should use a local variable cache

The instances below point to the second+ access of a value inside a storage array, within a function. Caching an array index value in a local `storage` or `calldata` variable when the value is accessed [multiple times](https://gist.github.com/IllIllI000/ec23a57daa30a8f8ca8b9681c8ccefb0), saves **~42 gas per access** due to not having to recalculate the array's keccak256 hash (`Gkeccak256` - **30 gas**) and that calculation's associated stack operations.

<details>
<summary>There are 25 instances (click to show):</summary>

- *AssignmentHook.sol* ( [173-173](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L173-L173), [173-173](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L173-L173) ):

```solidity
/// @audit _tierFees...[]
173:             if (_tierFees[i].tier == _tierId) return _tierFees[i].fee;

/// @audit _tierFees...[]
173:             if (_tierFees[i].tier == _tierId) return _tierFees[i].fee;
```

- *AutomataDcapV3Attestation.sol* ( [81-81](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L81-L81), [84-84](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L84-L84), [96-96](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L96-L96), [99-99](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L99-L99), [263-263](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L263-L263), [268-268](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L268-L268), [270-270](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L270-L270), [271-271](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L271-L271), [280-280](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L280-L280), [280-280](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L280-L280), [286-286](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L286-L286), [286-286](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L286-L286), [435-435](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L435-L435), [442-442](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L442-L442), [454-454](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L454-L454), [472-472](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L472-L472) ):

```solidity
/// @audit serialNumBatch...[]
81:             if (_serialNumIsRevoked[index][serialNumBatch[i]]) {

/// @audit serialNumBatch...[]
84:             _serialNumIsRevoked[index][serialNumBatch[i]] = true;

/// @audit serialNumBatch...[]
96:             if (!_serialNumIsRevoked[index][serialNumBatch[i]]) {

/// @audit serialNumBatch...[]
99:             delete _serialNumIsRevoked[index][serialNumBatch[i]];

/// @audit certs...[]
263:                 issuer = certs[i];

/// @audit certs...[]
268:                     certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.ROOT)][certs[i]

/// @audit certs...[]
270:                 } else if (certs[i].isPck) {

/// @audit certs...[]
271:                     certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.PCK)][certs[i]

/// @audit certs...[]
280:                 block.timestamp > certs[i].notBefore && block.timestamp < certs[i].notAfter;

/// @audit certs...[]
280:                 block.timestamp > certs[i].notBefore && block.timestamp < certs[i].notAfter;

/// @audit certs...[]
286:                 certs[i].tbsCertificate, certs[i].signature, issuer.pubKey

/// @audit certs...[]
286:                 certs[i].tbsCertificate, certs[i].signature, issuer.pubKey

/// @audit parsedQuoteCerts...[]
435:             string memory parsedFmspc = parsedQuoteCerts[0].pck.sgxExtension.fmspc;

/// @audit parsedQuoteCerts...[]
442:             IPEMCertChainLib.ECSha256Certificate memory pckCert = parsedQuoteCerts[0];

/// @audit parsedQuoteCerts...[]
454:             (tcbVerified, tcbStatus) = _checkTcbLevels(parsedQuoteCerts[0].pck, fetchedTcbInfo);

/// @audit parsedQuoteCerts...[]
472:                 parsedQuoteCerts[0].pubKey,
```

- *ERC721Vault.sol* ( [171-171](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L171-L171), [176-176](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L176-L176) ):

```solidity
/// @audit _tokenIds...[]
171:                 IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);

/// @audit _tokenIds...[]
176:                 BridgedERC721(token_).mint(_to, _tokenIds[i]);
```

- *SgxVerifier.sol* ( [211-211](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L211-L211), [213-213](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L213-L213), [215-215](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L215-L215), [217-217](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L217-L217), [220-220](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220-L220) ):

```solidity
/// @audit _instances...[]
211:             if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();

/// @audit _instances...[]
213:             addressRegistered[_instances[i]] = true;

/// @audit _instances...[]
215:             if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();

/// @audit _instances...[]
217:             instances[nextInstanceId] = Instance(_instances[i], validSince);

/// @audit _instances...[]
220:             emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);
```

</details>

### [G-66] Multiple accesses of the same mapping key should be cached

Reads and subsequent writes can also be cheaper when a function requires both values and they both fit in the same storage slot. Even if the values can't be packed, if both fields are accessed in the same function (as is the case for these instances), combining them can save **~42 gas per access** due to [not having to recalculate the key's keccak256 hash](https://gist.github.com/IllIllI000/639032d73e35d7e968ff58d8784bc445) (Gkeccak256 - 30 gas) and that calculation's associated stack operations.

There are 11 instances:

- *Bridge.sol* ( [168-168](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L168-L168), [230-230](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L230-L230) ):

```solidity
/// @audit `proofReceipt[msgHash]` is accessed on line 168, 190, 184
168:         uint64 receivedAt = proofReceipt[msgHash].receivedAt;

/// @audit `proofReceipt[msgHash]` is accessed on line 230, 250, 264, 243
230:         uint64 receivedAt = proofReceipt[msgHash].receivedAt;
```

- *ERC20Vault.sol* ( [188-188](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L188-L188) ):

```solidity
/// @audit `bridgedToCanonical[_btokenNew]` is accessed on line 188, 158, 180
188:         bridgedToCanonical[_btokenNew] = _ctoken;
```

- *SgxVerifier.sol* ( [111-111](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L111-L111), [235-235](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L235-L235) ):

```solidity
/// @audit `instances[idx]` is accessed on line 111, 107, 109
111:             delete instances[idx];

/// @audit `instances[id]` is accessed on line 235, 236, 237
235:         if (instance != instances[id].addr) return false;
```

### [G-67] Multiple mappings can be replaced with a single struct mapping

Saves a storage slot for the mapping. Depending on the circumstances and sizes of types, can avoid a Gsset (**20000 gas**) per mapping combined. Reads and subsequent writes can also be cheaper when a function requires both values and they both fit in the same storage slot. Finally, if both fields are accessed in the same function, can save **~42 gas per access** due to [not having to recalculate the key's keccak256 hash](https://gist.github.com/IllIllI000/ec23a57daa30a8f8ca8b9681c8ccefb0) (Gkeccak256 - 30 gas) and that calculation's associated stack operations.

<details>
<summary>There are 8 instances (click to show):</summary>

- *AutomataDcapV3Attestation.sol* ( [39-39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L39-L39), [40-40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L40-L40) ):

```solidity
39:     mapping(bytes32 enclave => bool trusted) private _trustedUserMrEnclave;

40:     mapping(bytes32 signer => bool trusted) private _trustedUserMrSigner;
```

- *Bridge.sol* ( [35-35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L35-L35), [46-46](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L46-L46) ):

```solidity
35:     mapping(bytes32 msgHash => Status status) public messageStatus;

46:     mapping(bytes32 msgHash => ProofReceipt receipt) public proofReceipt;
```

- *ERC20Airdrop2.sol* ( [22-22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L22-L22), [25-25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L25-L25) ):

```solidity
22:     mapping(address addr => uint256 amountClaimed) public claimedAmount;

25:     mapping(address addr => uint256 amountWithdrawn) public withdrawnAmount;
```

- *ERC20Vault.sol* ( [45-45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L45-L45), [52-52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L52-L52) ):

```solidity
45:     mapping(address btoken => CanonicalERC20 canonical) public bridgedToCanonical;

52:     mapping(address btoken => bool blacklisted) public btokenBlacklist;
```

</details>

### [G-68] Consider using `bytes32` rather than a `string`

Using the `bytes` types for fixed-length strings is more efficient than having the EVM have to incur the overhead of string processing. Consider whether the value _needs_ to be a `string`. A good reason to keep it as a `string` would be if the variable is defined in an interface that this project does not own.

There are 7 instances:

- *PEMCertChainLib.sol* ( [17-17](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L17-L17), [18-18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L18-L18), [22-22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L22-L22), [23-23](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L23-L23), [24-24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L24-L24) ):

```solidity
17:     string internal constant HEADER = "-----BEGIN CERTIFICATE-----";

18:     string internal constant FOOTER = "-----END CERTIFICATE-----";

22:     string internal constant PCK_COMMON_NAME = "Intel SGX PCK Certificate";

23:     string internal constant PLATFORM_ISSUER_NAME = "Intel SGX PCK Platform CA";

24:     string internal constant PROCESSOR_ISSUER_NAME = "Intel SGX PCK Processor CA";
```

- *BridgedERC1155.sol* ( [22-22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L22-L22), [25-25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L25-L25) ):

```solidity
22:     string private __symbol;

25:     string private __name;
```
