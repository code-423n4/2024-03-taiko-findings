> Please note: this report has been reviewed to ensure it *does not* contain automated findings from 4naly3er

# Summary

## Gas Optimizations
| # | Title | Instances |
| - | - | - |
| G-01 | [Assembly: Check `msg.sender` using `xor` and the scratch space](#g-01-assembly-check-msgsender-using-xor-and-the-scratch-space) | 16 |
| G-02 | [Assembly: Checks for `address(0x0)` are more efficient in assembly](#g-02-assembly-checks-for-address0x0-are-more-efficient-in-assembly) | 55 |
| G-03 | [Assembly: Use scratch space for building calldata](#g-03-assembly-use-scratch-space-for-building-calldata) | 63 |
| G-04 | [Assembly: Use scratch space when building emitted events with two data arguments](#g-04-assembly-use-scratch-space-when-building-emitted-events-with-two-data-arguments) | 6 |
| G-05 | [Assigning to structs can be more efficient](#g-05-assigning-to-structs-can-be-more-efficient) | 31 |
| G-06 | [Avoid updating storage when the value hasn't changed](#g-06-avoid-updating-storage-when-the-value-hasnt-changed) | 20 |
| G-07 | [Cache multiple accesses of mapping/array values](#g-07-cache-multiple-accesses-of-mappingarray-values) | 84 |
| G-08 | [Cache state variables accessed multiple times in the same function](#g-08-cache-state-variables-accessed-multiple-times-in-the-same-function) | 69 |
| G-09 | [Calculation results within a function can be cached to save gas](#g-09-calculation-results-within-a-function-can-be-cached-to-save-gas) | 11 |
| G-10 | [Consider changing some `public` variables to `private`/`internal`](#g-10-consider-changing-some-public-variables-to-privateinternal) | 86 |
| G-11 | [Consider merging sequential for loops](#g-11-consider-merging-sequential-for-loops) | 8 |
| G-12 | [Consider pre-calculating the address of `address(this)` to save gas](#g-12-consider-pre-calculating-the-address-of-addressthis-to-save-gas) | 42 |
| G-13 | [Consider using OpenZeppelin `EnumerateSet` in place of nested mappings](#g-13-consider-using-openzeppelin-enumerateset-in-place-of-nested-mappings) | 8 |
| G-14 | [Consider using `ERC721A` over `ERC721`](#g-14-consider-using-erc721a-over-erc721) | 2 |
| G-15 | [Constructors can be marked `payable`](#g-15-constructors-can-be-marked-payable) | 3 |
| G-16 | [Declare variables outside loops to save gas](#g-16-declare-variables-outside-loops-to-save-gas) | 58 |
| G-17 | [Default bool values are manually reset](#g-17-default-bool-values-are-manually-reset) | 2 |
| G-18 | [Default int values are manually reset](#g-18-default-int-values-are-manually-reset) | 10 |
| G-19 | [Detect zero value transfers to save gas](#g-19-detect-zero-value-transfers-to-save-gas) | 18 |
| G-20 | [Divisions can be `unchecked` to save gas](#g-20-divisions-can-be-unchecked-to-save-gas) | 15 |
| G-21 | [Duplicated `require()`/`revert()` checks should be refactored to a modifier or function to save deployment gas](#g-21-duplicated-requirerevert-checks-should-be-refactored-to-a-modifier-or-function-to-save-deployment-gas) | 15 |
| G-22 | [Emitting constants wastes gas](#g-22-emitting-constants-wastes-gas) | 5 |
| G-23 | [Enable IR-based code generation](#g-23-enable-ir-based-code-generation) | 81 |
| G-24 | [Events should be emitted outside of loops](#g-24-events-should-be-emitted-outside-of-loops) | 3 |
| G-25 | [Function names can be optimized to save gas](#g-25-function-names-can-be-optimized-to-save-gas) | 40 |
| G-26 | [Function result should be cached](#g-26-function-result-should-be-cached) | 4 |
| G-27 | [Inline `internal` functions that are only called once](#g-27-inline-internal-functions-that-are-only-called-once) | 27 |
| G-28 | [Inline `modifier`s that are only used once, to save gas](#g-28-inline-modifiers-that-are-only-used-once-to-save-gas) | 61 |
| G-29 | [It costs more gas to initialize non-`constant`/non-`immutable` state variables to zero/false than to let the default of zero/false be applied](#g-29-it-costs-more-gas-to-initialize-non-constantnon-immutable-state-variables-to-zerofalse-than-to-let-the-default-of-zerofalse-be-applied) | 6 |
| G-30 | [Iterating backwards in a `for` statement saves gas](#g-30-iterating-backwards-in-a-for-statement-saves-gas) | 45 |
| G-31 | [Mappings are cheaper to use than storage arrays](#g-31-mappings-are-cheaper-to-use-than-storage-arrays) | 36 |
| G-32 | [Merge events to save gas](#g-32-merge-events-to-save-gas) | 9 |
| G-33 | [Multiple `address`/ID mappings can be combined into a single `mapping` of an `address`/ID to a `struct`](#g-33-multiple-addressid-mappings-can-be-combined-into-a-single-mapping-of-an-addressid-to-a-struct) | 2 |
| G-34 | [Multiple accesses of a mapping/array should use a local variable cache](#g-34-multiple-accesses-of-a-mappingarray-should-use-a-local-variable-cache) | 54 |
| G-35 | [Nesting `if`-statements is cheaper than using `&&`](#g-35-nesting-if-statements-is-cheaper-than-using-) | 20 |
| G-36 | [Not using the named return variable is confusing and can waste gas](#g-36-not-using-the-named-return-variable-is-confusing-and-can-waste-gas) | 10 |
| G-37 | [Only emit event in setter function if the state variable was changed](#g-37-only-emit-event-in-setter-function-if-the-state-variable-was-changed) | 4 |
| G-38 | [Operator `>=`/`<=` costs less gas than operator `>`/`<`](#g-38-operator--costs-less-gas-than-operator-) | 99 |
| G-39 | [Public functions not used internally can be marked as external to save gas](#g-39-public-functions-not-used-internally-can-be-marked-as-external-to-save-gas) | 69 |
| G-40 | [Reduce deployment gas costs by fine-tuning IPFS file hashes](#g-40-reduce-deployment-gas-costs-by-fine-tuning-ipfs-file-hashes) | 87 |
| G-41 | [Redundant state variable getters](#g-41-redundant-state-variable-getters) | 1 |
| G-42 | [Redundant type conversion](#g-42-redundant-type-conversion) | 1 |
| G-43 | [Refactor modifiers to call a local function](#g-43-refactor-modifiers-to-call-a-local-function) | 15 |
| G-44 | [Remove empty functions to save gas](#g-44-remove-empty-functions-to-save-gas) | 4 |
| G-45 | [Replace OpenZeppelin components with Solady equivalents to save gas](#g-45-replace-openzeppelin-components-with-solady-equivalents-to-save-gas) | 10 |
| G-46 | [Same cast is done multiple times](#g-46-same-cast-is-done-multiple-times) | 19 |
| G-47 | [Simple checks for zero can be done using assembly to save gas](#g-47-simple-checks-for-zero-can-be-done-using-assembly-to-save-gas) | 81 |
| G-48 | [Split `revert` checks to save gas](#g-48-split-revert-checks-to-save-gas) | 7 |
| G-49 | [Splitting `require()` statements that use `&&` saves gas](#g-49-splitting-require-statements-that-use--saves-gas) | 4 |
| G-50 | [Stack variable is only used once](#g-50-stack-variable-is-only-used-once) | 99 |
| G-51 | [Structs can be packed into fewer storage slots](#g-51-structs-can-be-packed-into-fewer-storage-slots) | 6 |
| G-52 | [Subtraction can potentially be marked `unchecked` to save gas](#g-52-subtraction-can-potentially-be-marked-unchecked-to-save-gas) | 97 |
| G-53 | [The result of function calls should be cached rather than re-calling the function](#g-53-the-result-of-function-calls-should-be-cached-rather-than-re-calling-the-function) | 92 |
| G-54 | [Usage of non-`uint256`/`int256` types uses more gas](#g-54-usage-of-non-uint256int256-types-uses-more-gas) | 99 |
| G-55 | [Use Solady library where possible to save gas](#g-55-use-solady-library-where-possible-to-save-gas) | 13 |
| G-56 | [Use `<<` to efficiently multiple by powers of `2`](#g-56-use--to-efficiently-multiple-by-powers-of-2) | 10 |
| G-57 | [Use `Array.unsafeAccess()` to avoid repeated array length checks](#g-57-use-arrayunsafeaccess-to-avoid-repeated-array-length-checks) | 28 |
| G-58 | [Use `bytes32` in place of string](#g-58-use-bytes32-in-place-of-string) | 7 |
| G-59 | [Use `calldata` instead of `memory` for function arguments that are read only](#g-59-use-calldata-instead-of-memory-for-function-arguments-that-are-read-only) | 99 |
| G-60 | [Use `uint256(1)`/`uint256(2)` instead of `true`/`false` to save gas for changes](#g-60-use-uint2561uint2562-instead-of-truefalse-to-save-gas-for-changes) | 10 |
| G-61 | [Use assembly to calculate hashes](#g-61-use-assembly-to-calculate-hashes) | 28 |
| G-62 | [Use assembly to perform external calls, in order to save gas](#g-62-use-assembly-to-perform-external-calls-in-order-to-save-gas) | 3 |
| G-63 | [Use assembly to write storage values](#g-63-use-assembly-to-write-storage-values) | 85 |
| G-64 | [Use custom errors rather than `revert()`/`require()` strings to save gas](#g-64-use-custom-errors-rather-than-revertrequire-strings-to-save-gas) | 66 |
| G-65 | [Use local variables for emitting](#g-65-use-local-variables-for-emitting) | 7 |
| G-66 | [Use more recent OpenZeppelin version for gas boost](#g-66-use-more-recent-openzeppelin-version-for-gas-boost) | 47 |
| G-67 | [Use named `return` parameters](#g-67-use-named-return-parameters) | 99 |
| G-68 | [Use nested `if`s instead of `&&`](#g-68-use-nested-ifs-instead-of-) | 16 |
| G-69 | [Use of low-level `call()` can be optimized with assembly](#g-69-use-of-low-level-call-can-be-optimized-with-assembly) | 1 |
| G-70 | [Using `storage` instead of `memory` for structs/arrays saves gas](#g-70-using-storage-instead-of-memory-for-structsarrays-saves-gas) | 22 |
| G-71 | [Using assembly's `selfbalance()` is cheaper than `address(this).balance`](#g-71-using-assemblys-selfbalance-is-cheaper-than-addressthisbalance) | 7 |
| G-72 | [`++i` costs less gas than `i++`, especially when it's used in `for`-loops (`--i`/`i--` too)](#g-72-i-costs-less-gas-than-i-especially-when-its-used-in-for-loops---ii---too) | 12 |
| G-73 | [`++i`/`i++` should be `unchecked{++i}`/`unchecked{i++}` when it is not possible for them to overflow, as is the case when used in `for`- and `while`-loops](#g-73-ii-should-be-uncheckediuncheckedi-when-it-is-not-possible-for-them-to-overflow-as-is-the-case-when-used-in-for--and-while-loops) | 45 |
| G-74 | [`<x> += <y>` costs more gas than `<x> = <x> + <y>` for state variables](#g-74-x--y-costs-more-gas-than-x--x--y-for-state-variables) | 6 |
| G-75 | [`abi.encode()` is less efficient than `abi.encodepacked()` for non-address arguments](#g-75-abiencode-is-less-efficient-than-abiencodepacked-for-non-address-arguments) | 18 |
| G-76 | [`do`-`while` is cheaper than `for`-loops when the initial check can be skipped](#g-76-do-while-is-cheaper-than-for-loops-when-the-initial-check-can-be-skipped) | 49 |
| G-77 | [require()`/`revert()` strings longer than 32 bytes cost extra gas](#g-77-requirerevert-strings-longer-than-32-bytes-cost-extra-gas) | 1 |

# Gas Optimizations

## [G-01] Assembly: Check `msg.sender` using `xor` and the scratch space

We can use assembly to efficiently validate `msg.sender` with the least amount of opcodes necessary. For more details check the following report [here](https://code4rena.com/reports/2023-05-juicebox#g-06-use-assembly-to-validate-msgsender).

*Instances: 16*

```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

  25 |  if (msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();
```
GitHub: [25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L25)


```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

  42 |  if (msg.sender != owner() && msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();
```
GitHub: [42](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L42)


```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

 310 |  if (proposerOne != address(0) && msg.sender != proposerOne) {
```
GitHub: [310](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L310)


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

 123 |  if (msg.sender != GOLDEN_TOUCH_ADDRESS) revert L2_INVALID_SENDER();
```
GitHub: [123](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L123)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 250 |  if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) {

 260 |  if (_message.gasLimit == 0 && msg.sender != _message.destOwner) {

 294 |  if (msg.sender == refundTo) {

 322 |  if (msg.sender != _message.destOwner) revert B_PERMISSION_DENIED();
```
GitHub: [250](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L250), [260](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L260), [294](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L294), [322](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L322)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

  38 |  if (msg.sender != owner() && msg.sender != snapshooter) {
```
GitHub: [38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L38)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

  61 |  if (msg.sender == migratingAddress) {

  64 |  } else if (msg.sender != resolve("erc20_vault", true)) {

  78 |  if (msg.sender != _account) revert BB_PERMISSION_DENIED();

  83 |  } else if (msg.sender != resolve("erc20_vault", true)) {
```
GitHub: [61](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L61), [64](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L64), [78](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L78), [83](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L83)


```solidity
File: packages/protocol/contracts/tokenvault/BaseVault.sol

  23 |  if (msg.sender != resolve("bridge", false)) {

  65 |  if (ctx_.from != msg.sender) revert VAULT_PERMISSION_DENIED();
```
GitHub: [23](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L23), [65](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L65)


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

  61 |  require(msg.sender == owner, "onlyOwner");
```
GitHub: [61](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L61)


## [G-02] Assembly: Checks for `address(0x0)` are more efficient in assembly

Using assembly to check for zero can save gas by allowing more direct access to the evm and reducing some of the overhead associated with high-level operations in solidity.

*Instances: 55*

```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

  81 |  if (addressManager == address(0)) revert RESOLVER_INVALID_MANAGER();

  85 |  if (!_allowZeroAddress && addr_ == address(0)) {
```
GitHub: [81](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L81), [85](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L85)


```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

 105 |  if (_addressManager == address(0)) revert ZERO_ADDR_MANAGER();

 110 |  _transferOwnership(_owner == address(0) ? msg.sender : _owner);
```
GitHub: [105](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L105), [110](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L110)


```solidity
File: packages/protocol/contracts/libs/LibAddress.sol

  24 |  if (_to == address(0)) revert ETH_TRANSFER_FAILED();
```
GitHub: [24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L24)


```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

 109 |  if (assignment.feeToken == address(0)) {

 120 |  if (input.tip != 0 && block.coinbase != address(0)) {
```
GitHub: [109](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L109), [120](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L120)


```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

  44 |  address recipient_ = _recipient == address(0) ? msg.sender : _recipient;
```
GitHub: [44](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L44)


```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

  81 |  if (params.assignedProver == address(0)) {

  85 |  if (params.coinbase == address(0)) {

 310 |  if (proposerOne != address(0) && msg.sender != proposerOne) {

 316 |  return proposer == address(0) || msg.sender == proposer;
```
GitHub: [81](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L81), [85](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L85), [310](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L310), [316](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L316)


```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

 163 |  if (verifier != address(0)) {

 224 |  assert(ts.validityBond == 0 && ts.contestBond == 0 && ts.contester == address(0));

 239 |  if (ts.contester != address(0)) revert L1_ALREADY_CONTESTED();

 363 |  if (_ts.contester != address(0)) {
```
GitHub: [163](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L163), [224](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L224), [239](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L239), [363](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L363)


```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

 145 |  if (ts.contester != address(0)) {

 148 |  if (tierProvider == address(0)) {
```
GitHub: [145](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L145), [148](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L148)


```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

  82 |  if (guardian == address(0)) revert INVALID_GUARDIAN();
```
GitHub: [82](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L82)


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

 172 |  if (_to == address(0)) revert L2_INVALID_PARAM();

 173 |  if (_token == address(0)) {
```
GitHub: [172](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L172), [173](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L173)


```solidity
File: packages/protocol/contracts/signal/SignalService.sol

  36 |  if (_app == address(0)) revert SS_INVALID_SENDER();
```
GitHub: [36](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L36)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 124 |  if (_message.srcOwner == address(0) || _message.destOwner == address(0)) {

 124 |  if (_message.srcOwner == address(0) || _message.destOwner == address(0)) {

 270 |  _message.to == address(0) || _message.to == address(this)

 291 |  _message.refundTo == address(0) ? _message.destOwner : _message.refundTo;

 398 |  enabled_ = destBridge_ != address(0);
```
GitHub: [124](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L124), [124](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L124), [270](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L270), [291](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L291), [398](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L398)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

 102 |  return migratingAddress != address(0) && !migratingInbound;
```
GitHub: [102](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L102)


```solidity
File: packages/protocol/contracts/tokenvault/BaseNFTVault.sol

 149 |  if (_op.token == address(0)) revert VAULT_INVALID_TOKEN();
```
GitHub: [149](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L149)


```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

  64 |  destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,

 108 |  if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

 249 |  if (bridgedToCanonical[_op.token].addr != address(0)) {

 293 |  if (btoken_ == address(0)) {
```
GitHub: [64](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L64), [108](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L108), [249](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L249), [293](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L293)


```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

 158 |  if (_btokenNew == address(0) || bridgedToCanonical[_btokenNew].addr != address(0)) {

 158 |  if (_btokenNew == address(0) || bridgedToCanonical[_btokenNew].addr != address(0)) {

 170 |  if (btokenOld_ != address(0)) {

 215 |  if (_op.token == address(0)) revert VAULT_INVALID_TOKEN();

 227 |  destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,

 267 |  if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

 358 |  if (bridgedToCanonical[_token].addr != address(0)) {

 397 |  if (btoken == address(0)) {
```
GitHub: [158](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L158), [158](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L158), [170](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L170), [215](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L215), [227](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L227), [267](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L267), [358](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L358), [397](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L397)


```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

  50 |  destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,

  91 |  if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

 195 |  if (bridgedToCanonical[_op.token].addr != address(0)) {

 230 |  if (btoken_ == address(0)) {
```
GitHub: [50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L50), [91](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L91), [195](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L195), [230](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L230)


```solidity
File: packages/protocol/contracts/tokenvault/LibBridgedToken.sol

  21 |  _srcToken == address(0) || _srcChainId == 0 || _srcChainId == block.chainid
```
GitHub: [21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L21)


```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

 107 |  if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();

 124 |  if (automataDcapAttestation == address(0)) {

 215 |  if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();

 234 |  if (instance == address(0)) return false;
```
GitHub: [107](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L107), [124](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L124), [215](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L215), [234](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L234)


```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

 121 |  if (_taikoToken == address(0)) revert INVALID_PARAM();

 124 |  if (_costToken == address(0)) revert INVALID_PARAM();

 127 |  if (_sharedVault == address(0)) revert INVALID_PARAM();

 136 |  if (_recipient == address(0)) revert INVALID_PARAM();

 169 |  if (_to == address(0)) revert INVALID_PARAM();
```
GitHub: [121](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L121), [124](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L124), [127](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L127), [136](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L136), [169](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L169)


## [G-03] Assembly: Use scratch space for building calldata

If an external call's calldata can fit into two or fewer words, use the scratch space to build the calldata, rather than allowing Solidity to do a memory expansion.

*Instances: 63*

```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

  83 |  addr_ = payable(IAddressManager(addressManager).getAddress(_chainId, _name));
```
GitHub: [83](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L83)


```solidity
File: packages/protocol/contracts/libs/LibAddress.sol

  56 |  try IERC165(_addr).supportsInterface(_interfaceId) returns (bool _result) {

  71 |  return IERC1271(_addr).isValidSignature(_hash, _sig) == _EIP1271_MAGICVALUE;
```
GitHub: [56](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L56), [71](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L71)


```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

 149 |  ITaikoL1(_taikoL1Address).getConfig().chainId,
```
GitHub: [149](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L149)


```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

  41 |  _resolver.resolve("bridge", false).sendEther(msg.value);
```
GitHub: [41](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L41)


```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

 207 |  meta_.minTier = ITierProvider(_resolver.resolve("tier_provider", false)).getMinTier(
 208 |      uint256(meta_.difficulty)
 209 |  );

 207 |  meta_.minTier = ITierProvider(_resolver.resolve("tier_provider", false)).getMinTier(

 237 |  IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));

 238 |  uint256 tkoBalance = tko.balanceOf(address(this));

 268 |  if (tko.balanceOf(address(this)) != tkoBalance + _config.livenessBond) {

 309 |  address proposerOne = _resolver.resolve("proposer_one", true);

 315 |  address proposer = _resolver.resolve("proposer", true);
```
GitHub: [207-209](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L207-L209), [207](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L207), [237](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L237), [238](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L238), [268](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L268), [309](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L309), [315](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L315)


```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

 141 |  ITierProvider(_resolver.resolve("tier_provider", false)).getTier(_proof.tier);

 141 |  ITierProvider(_resolver.resolve("tier_provider", false)).getTier(_proof.tier);

 161 |  address verifier = _resolver.resolve(tier.verifierName, true);

 187 |  IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));

 196 |  tko.transfer(blk.assignedProver, blk.livenessBond);

 367 |  _tko.transfer(_ts.prover, _ts.validityBond + reward);

 371 |  _tko.transfer(_ts.contester, _ts.contestBond + reward);

 382 |  _tko.transfer(msg.sender, reward - _tier.validityBond);
```
GitHub: [141](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L141), [141](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L141), [161](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L161), [187](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L187), [196](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L196), [367](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L367), [371](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L371), [382](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L382)


```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

 149 |  tierProvider = _resolver.resolve("tier_provider", false);

 152 |  uint256(ITierProvider(tierProvider).getTier(ts.tier).cooldownWindow) * 60

 188 |  IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));

 189 |  tko.transfer(ts.prover, bondToReturn);

 232 |  ISignalService signalService = ISignalService(_resolver.resolve("signal_service", false));
```
GitHub: [149](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L149), [152](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L152), [188](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L188), [189](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L189), [232](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L232)


```solidity
File: packages/protocol/contracts/L1/provers/GuardianProver.sol

  51 |  ITaikoL1(resolve("taiko", false)).proveBlock(_meta.id, abi.encode(_meta, _tran, _proof));
```
GitHub: [51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/GuardianProver.sol#L51)


```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

  45 |  IBridge.Context memory ctx = IBridge(msg.sender).context();
```
GitHub: [45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L45)


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

 176 |  IERC20(_token).safeTransfer(_to, IERC20(_token).balanceOf(address(this)));

 176 |  IERC20(_token).safeTransfer(_to, IERC20(_token).balanceOf(address(this)));
```
GitHub: [176](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L176), [176](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L176)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 150 |  ISignalService(resolve("signal_service", false)).sendSignal(msgHash_);

 174 |  if (!ISignalService(signalService).isSignalSent(address(this), msgHash)) {

 199 |  IRecallableSender(_message.from).onMessageRecalled{ value: _message.value }(
 200 |      _message, msgHash
 201 |  );

 342 |  return ISignalService(resolve("signal_service", false)).isSignalSent({
 343 |      _app: address(this),
 344 |      _signal: hashMessage(_message)
 345 |  });

 522 |  ISignalService(resolve("signal_service", false)).sendSignal(
 523 |      signalForFailedMessage(_msgHash)
 524 |  );
```
GitHub: [150](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L150), [174](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L174), [199-201](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L199-L201), [342-345](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L342-L345), [522-524](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L522-L524)


```solidity
File: packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

  44 |  usdc.mint(_account, _amount);

  49 |  usdc.burn(_amount);
```
GitHub: [44](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L44), [49](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L49)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

  82 |  IBridgedERC20(migratingAddress).mint(_account, _amount);
```
GitHub: [82](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L82)


```solidity
File: packages/protocol/contracts/tokenvault/BaseVault.sol

  53 |  ctx_ = IBridge(msg.sender).context();

  64 |  ctx_ = IBridge(msg.sender).context();
```
GitHub: [53](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L53), [64](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L64)


```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

  77 |  IBridge(resolve("bridge", false)).sendMessage{ value: msg.value }(message);

 263 |  try t.name() returns (string memory _name) {

 266 |  try t.symbol() returns (string memory _symbol) {
```
GitHub: [77](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L77), [263](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L263), [266](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L266)


```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

 164 |  if (IBridgedERC20(_btokenNew).owner() != owner()) {

 184 |  IBridgedERC20(btokenOld_).changeMigrationStatus(_btokenNew, false);

 185 |  IBridgedERC20(_btokenNew).changeMigrationStatus(btokenOld_, true);

 239 |  IBridge(resolve("bridge", false)).sendMessage{ value: msg.value }(message);

 330 |  IERC20(token_).safeTransfer(_to, _amount);

 333 |  IBridgedERC20(token_).mint(_to, _amount);

 360 |  IBridgedERC20(_token).burn(msg.sender, _amount);

 368 |  decimals: meta.decimals(),

 369 |  symbol: meta.symbol(),

 370 |  name: meta.name()

 378 |  uint256 _balance = t.balanceOf(address(this));

 380 |  balanceChange_ = t.balanceOf(address(this)) - _balance;
```
GitHub: [164](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L164), [184](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L184), [185](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L185), [239](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L239), [330](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L330), [333](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L333), [360](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L360), [368](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L368), [369](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L369), [370](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L370), [378](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L378), [380](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L380)


```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

  62 |  IBridge(resolve("bridge", false)).sendMessage{ value: msg.value }(message);

 176 |  BridgedERC721(token_).mint(_to, _tokenIds[i]);

 198 |  BridgedERC721(_op.token).burn(_user, _op.tokenIds[i]);

 206 |  symbol: t.symbol(),

 207 |  name: t.name()
```
GitHub: [62](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L62), [176](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L176), [198](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L198), [206](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L206), [207](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L207)


```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

 128 |  (bool verified,) = IAttestation(automataDcapAttestation).verifyParsedQuote(_attestation);

 185 |  ITaikoL1(taikoL1).getConfig().chainId,
```
GitHub: [128](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L128), [185](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L185)


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

 424 |  (certDecodedSuccessfully, parsedQuoteCerts[i]) = pemCertLib.decodeCert(
 425 |      authDataV3.certification.decodedCertDataArray[i], isPckCert
 426 |  );
```
GitHub: [424-426](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L424-L426)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

 278 |  pemCertLib.splitCertificateChain(certBytes, 3);
```
GitHub: [278](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L278)


## [G-04] Assembly: Use scratch space when building emitted events with two data arguments

To efficiently emit events, it's possible to utilize assembly by making use of scratch space and the free memory pointer. This approach has the advantage of potentially avoiding the costs associated with memory expansion.

However, it's important to note that in order to safely optimize this process, it is preferable to cache and restore the free memory pointer.

A good example of such practice can be seen in [Solady's](https://github.com/Vectorized/solady/blob/main/src/tokens/ERC1155.sol#L167) codebase.

*Instances: 6*

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

  59 |  emit Authorized(_addr, _authorize);
```
GitHub: [59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L59)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 111 |  emit AddressBanned(_addr, _ban);
```
GitHub: [111](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L111)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

  51 |  emit MigrationStatusChanged(_migratingAddress, _migratingInbound);
```
GitHub: [51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L51)


```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

 109 |  emit InstanceDeleted(idx, instances[idx].addr);
```
GitHub: [109](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L109)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

  93 |  emit Withdrawn(user, amount);
```
GitHub: [93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L93)


```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

 157 |  emit Voided(_recipient, amountVoided);
```
GitHub: [157](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L157)


## [G-05] Assigning to structs can be more efficient

By changing the pattern of assigning value to the structure, gas savings of ~130 per instance are achieved. In addition, this use will provide significant savings in distribution costs.  

Instead of:

```solidity     
MyStruct memory myStruct = MyStruct(_a, _b, _c); 
```

write  

```solidity     
MyStruct memory myStruct;     
myStruct.a = _a;     
myStruct.b = _b;     
myStruct.c = _c; 
```


*Instances: 31*

```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

     |  // @audit-issue Assign struct fields individually to save gas
  51 |  TaikoData.EthDeposit({
  52 |      recipient: recipient_,
  53 |      amount: uint96(msg.value),
  54 |      id: _state.slotA.numEthDeposits
  55 |  })

     |  // @audit-issue Assign struct fields individually to save gas
  88 |  deposits_[i] = TaikoData.EthDeposit({
  89 |      recipient: address(uint160(data >> 96)),
  90 |      amount: uint96(data),
  91 |      id: j
  92 |  });
```
GitHub: [51-55](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L51-L55), [88-92](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L88-L92)


```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

     |  // @audit-issue Assign struct fields individually to save gas
 121 |  meta_ = TaikoData.BlockMetadata({
 122 |      l1Hash: blockhash(block.number - 1),
 123 |      difficulty: 0, // to be initialized below
 124 |      blobHash: 0, // to be initialized below
 125 |      extraData: params.extraData,
 126 |      depositsHash: keccak256(abi.encode(deposits_)),
 127 |      coinbase: params.coinbase,
 128 |      id: b.numBlocks,
 129 |      gasLimit: _config.blockMaxGasLimit,
 130 |      timestamp: uint64(block.timestamp),
 131 |      l1Height: uint64(block.number - 1),
 132 |      txListByteOffset: 0, // to be initialized below
 133 |      txListByteSize: 0, // to be initialized below
 134 |      minTier: 0, // to be initialized below
 135 |      blobUsed: _txList.length == 0,
 136 |      parentMetaHash: parentMetaHash
 137 |  });

     |  // @audit-issue Assign struct fields individually to save gas
 212 |  TaikoData.Block memory blk = TaikoData.Block({
 213 |      metaHash: keccak256(abi.encode(meta_)),
 214 |      // Safeguard the liveness bond to ensure its preservation,
 215 |      // particularly in scenarios where it might be altered after the
 216 |      // block's proposal but before it has been proven or verified.
 217 |      livenessBond: _config.livenessBond,
 218 |      blockId: b.numBlocks,
 219 |      proposedAt: meta_.timestamp,
 220 |      proposedIn: uint64(block.number),
 221 |      // For a new block, the next transition ID is always 1, not 0.
 222 |      nextTransitionId: 1,
 223 |      // For unverified block, its verifiedTransitionId is always 0.
 224 |      verifiedTransitionId: 0,
 225 |      assignedProver: params.assignedProver
 226 |  });
```
GitHub: [121-137](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L121-L137), [212-226](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L212-L226)


```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

     |  // @audit-issue Assign struct fields individually to save gas
 166 |  IVerifier.Context memory ctx = IVerifier.Context({
 167 |      metaHash: blk.metaHash,
 168 |      blobHash: _meta.blobHash,
 169 |      // Separate msgSender to allow the prover to be any address in the future.
 170 |      prover: msg.sender,
 171 |      msgSender: msg.sender,
 172 |      blockId: blk.blockId,
 173 |      isContesting: isContesting,
 174 |      blobUsed: _meta.blobUsed
 175 |  });
```
GitHub: [166-175](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L166-L175)


```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

     |  // @audit-issue Assign struct fields individually to save gas
 191 |  return TaikoData.Config({
 192 |      chainId: 167_008,
 193 |      // Assume the block time is 3s, the protocol will allow ~1 month of
 194 |      // new blocks without any verification.
 195 |      blockMaxProposals: 864_000,
 196 |      blockRingBufferSize: 864_100,
 197 |      // Can be overridden by the tier config.
 198 |      maxBlocksToVerifyPerProposal: 10,
 199 |      blockMaxGasLimit: 15_000_000,
 200 |      // Each go-ethereum transaction has a size limit of 128KB,
 201 |      // and right now txList is still saved in calldata, so we set it
 202 |      // to 120KB.
 203 |      blockMaxTxListBytes: 120_000,
 204 |      blobExpiry: 24 hours,
 205 |      blobAllowedForDA: false,
 206 |      blobReuseEnabled: false,
 207 |      livenessBond: 250e18, // 250 Taiko token
 208 |      // ETH deposit related.
 209 |      ethDepositRingBufferSize: 1024,
 210 |      ethDepositMinCountPerBlock: 8,
 211 |      ethDepositMaxCountPerBlock: 32,
 212 |      ethDepositMinAmount: 1 ether,
 213 |      ethDepositMaxAmount: 10_000 ether,
 214 |      ethDepositGas: 21_000,
 215 |      ethDepositMaxFee: 1 ether / 10,
 216 |      blockSyncThreshold: 16
 217 |  });
```
GitHub: [191-217](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L191-L217)


```solidity
File: packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol

     |  // @audit-issue Assign struct fields individually to save gas
  22 |  return ITierProvider.Tier({
  23 |      verifierName: "tier_optimistic",
  24 |      validityBond: 250 ether, // TKO
  25 |      contestBond: 500 ether, // TKO
  26 |      cooldownWindow: 1440, //24 hours
  27 |      provingWindow: 120, // 2 hours
  28 |      maxBlocksToVerifyPerProof: 16
  29 |  });

     |  // @audit-issue Assign struct fields individually to save gas
  33 |  return ITierProvider.Tier({
  34 |      verifierName: "tier_guardian",
  35 |      validityBond: 0, // must be 0 for top tier
  36 |      contestBond: 0, // must be 0 for top tier
  37 |      cooldownWindow: 60, //1 hours
  38 |      provingWindow: 2880, // 48 hours
  39 |      maxBlocksToVerifyPerProof: 16
  40 |  });
```
GitHub: [22-29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L22-L29), [33-40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L33-L40)


```solidity
File: packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol

     |  // @audit-issue Assign struct fields individually to save gas
  22 |  return ITierProvider.Tier({
  23 |      verifierName: "tier_sgx",
  24 |      validityBond: 250 ether, // TKO
  25 |      contestBond: 500 ether, // TKO
  26 |      cooldownWindow: 1440, //24 hours
  27 |      provingWindow: 60, // 1 hours
  28 |      maxBlocksToVerifyPerProof: 8
  29 |  });

     |  // @audit-issue Assign struct fields individually to save gas
  33 |  return ITierProvider.Tier({
  34 |      verifierName: "tier_sgx_zkvm",
  35 |      validityBond: 500 ether, // TKO
  36 |      contestBond: 1000 ether, // TKO
  37 |      cooldownWindow: 1440, //24 hours
  38 |      provingWindow: 240, // 4 hours
  39 |      maxBlocksToVerifyPerProof: 4
  40 |  });

     |  // @audit-issue Assign struct fields individually to save gas
  44 |  return ITierProvider.Tier({
  45 |      verifierName: "tier_guardian",
  46 |      validityBond: 0, // must be 0 for top tier
  47 |      contestBond: 0, // must be 0 for top tier
  48 |      cooldownWindow: 60, //1 hours
  49 |      provingWindow: 2880, // 48 hours
  50 |      maxBlocksToVerifyPerProof: 16
  51 |  });
```
GitHub: [22-29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L22-L29), [33-40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L33-L40), [44-51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L44-L51)


```solidity
File: packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol

     |  // @audit-issue Assign struct fields individually to save gas
  22 |  return ITierProvider.Tier({
  23 |      verifierName: "tier_optimistic",
  24 |      validityBond: 250 ether, // TKO
  25 |      contestBond: 500 ether, // TKO
  26 |      cooldownWindow: 1440, //24 hours
  27 |      provingWindow: 30, // 0.5 hours
  28 |      maxBlocksToVerifyPerProof: 12
  29 |  });

     |  // @audit-issue Assign struct fields individually to save gas
  33 |  return ITierProvider.Tier({
  34 |      verifierName: "tier_sgx",
  35 |      validityBond: 500 ether, // TKO
  36 |      contestBond: 1000 ether, // TKO
  37 |      cooldownWindow: 1440, //24 hours
  38 |      provingWindow: 60, // 1 hours
  39 |      maxBlocksToVerifyPerProof: 8
  40 |  });

     |  // @audit-issue Assign struct fields individually to save gas
  44 |  return ITierProvider.Tier({
  45 |      verifierName: "tier_guardian",
  46 |      validityBond: 0, // must be 0 for top tier
  47 |      contestBond: 0, // must be 0 for top tier
  48 |      cooldownWindow: 60, //1 hours
  49 |      provingWindow: 2880, // 48 hours
  50 |      maxBlocksToVerifyPerProof: 16
  51 |  });
```
GitHub: [22-29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L22-L29), [33-40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L33-L40), [44-51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L44-L51)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

     |  // @audit-issue Assign struct fields individually to save gas
 243 |  proofReceipt[msgHash] = ProofReceipt({
 244 |      receivedAt: receivedAt,
 245 |      preferredExecutor: _message.gasLimit == 0 ? _message.destOwner : msg.sender
 246 |  });

     |  // @audit-issue Assign struct fields individually to save gas
 549 |  __ctx = Context(_msgHash, _from, _srcChainId);

     |  // @audit-issue Assign struct fields individually to save gas
 565 |  return Context(msgHash, from, srcChainId);
```
GitHub: [243-246](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L243-L246), [549](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L549), [565](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L565)


```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

     |  // @audit-issue Assign struct fields individually to save gas
  58 |  IBridge.Message memory message = IBridge.Message({
  59 |      id: 0, // will receive a new value
  60 |      from: address(0), // will receive a new value
  61 |      srcChainId: 0, // will receive a new value
  62 |      destChainId: _op.destChainId,
  63 |      srcOwner: msg.sender,
  64 |      destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,
  65 |      to: resolve(_op.destChainId, name(), false),
  66 |      refundTo: _op.refundTo,
  67 |      value: msg.value - _op.fee,
  68 |      fee: _op.fee,
  69 |      gasLimit: _op.gasLimit,
  70 |      data: data,
  71 |      memo: _op.memo
  72 |  });

     |  // @audit-issue Assign struct fields individually to save gas
 256 |  ctoken_ = CanonicalNFT({
 257 |      chainId: uint64(block.chainid),
 258 |      addr: _op.token,
 259 |      symbol: "",
 260 |      name: ""
 261 |  });
```
GitHub: [58-72](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L58-L72), [256-261](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L256-L261)


```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

     |  // @audit-issue Assign struct fields individually to save gas
 221 |  IBridge.Message memory message = IBridge.Message({
 222 |      id: 0, // will receive a new value
 223 |      from: address(0), // will receive a new value
 224 |      srcChainId: 0, // will receive a new value
 225 |      destChainId: _op.destChainId,
 226 |      srcOwner: msg.sender,
 227 |      destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,
 228 |      to: resolve(_op.destChainId, name(), false),
 229 |      refundTo: _op.refundTo,
 230 |      value: msg.value - _op.fee,
 231 |      fee: _op.fee,
 232 |      gasLimit: _op.gasLimit,
 233 |      data: data,
 234 |      memo: _op.memo
 235 |  });

     |  // @audit-issue Assign struct fields individually to save gas
 365 |  ctoken_ = CanonicalERC20({
 366 |      chainId: uint64(block.chainid),
 367 |      addr: _token,
 368 |      decimals: meta.decimals(),
 369 |      symbol: meta.symbol(),
 370 |      name: meta.name()
 371 |  });
```
GitHub: [221-235](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L221-L235), [365-371](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L365-L371)


```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

     |  // @audit-issue Assign struct fields individually to save gas
  44 |  IBridge.Message memory message = IBridge.Message({
  45 |      id: 0, // will receive a new value
  46 |      from: address(0), // will receive a new value
  47 |      srcChainId: 0, // will receive a new value
  48 |      destChainId: _op.destChainId,
  49 |      srcOwner: msg.sender,
  50 |      destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,
  51 |      to: resolve(_op.destChainId, name(), false),
  52 |      refundTo: _op.refundTo,
  53 |      value: msg.value - _op.fee,
  54 |      fee: _op.fee,
  55 |      gasLimit: _op.gasLimit,
  56 |      data: data,
  57 |      memo: _op.memo
  58 |  });

     |  // @audit-issue Assign struct fields individually to save gas
 203 |  ctoken_ = CanonicalNFT({
 204 |      chainId: uint64(block.chainid),
 205 |      addr: _op.token,
 206 |      symbol: t.symbol(),
 207 |      name: t.name()
 208 |  });
```
GitHub: [44-58](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L44-L58), [203-208](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L203-L208)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

     |  // @audit-issue Assign struct fields individually to save gas
  47 |  out_ = RLPItem({ length: _in.length, ptr: ptr });

     |  // @audit-issue Assign struct fields individually to save gas
  76 |  RLPItem({
  77 |      length: _in.length - offset,
  78 |      ptr: MemoryPointer.wrap(MemoryPointer.unwrap(_in.ptr) + offset)
  79 |  })

     |  // @audit-issue Assign struct fields individually to save gas
  84 |  out_[itemCount] = RLPItem({
  85 |      length: itemLength + itemOffset,
  86 |      ptr: MemoryPointer.wrap(MemoryPointer.unwrap(_in.ptr) + offset)
  87 |  });
```
GitHub: [47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L47), [76-79](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L76-L79), [84-87](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L84-L87)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

     |  // @audit-issue Assign struct fields individually to save gas
 209 |  proof_[i] = TrieNode({ encoded: _proof[i], decoded: RLPReader.readList(_proof[i]) });
```
GitHub: [209](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L209)


```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

     |  // @audit-issue Assign struct fields individually to save gas
 217 |  instances[nextInstanceId] = Instance(_instances[i], validSince);

     |  // @audit-issue Assign struct fields individually to save gas
 229 |  instances[id] = Instance(newInstance, uint64(block.timestamp));
```
GitHub: [217](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L217), [229](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L229)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

     |  // @audit-issue Assign struct fields individually to save gas
  54 |  v3ParsedQuote = V3Struct.ParsedV3QuoteStruct({
  55 |      header: header,
  56 |      localEnclaveReport: localEnclaveReport,
  57 |      v3AuthData: authDataV3
  58 |  });

     |  // @audit-issue Assign struct fields individually to save gas
 190 |  header = V3Struct.Header({
 191 |      version: version,
 192 |      attestationKeyType: attestationKeyType,
 193 |      teeType: teeType,
 194 |      qeSvn: bytes2(rawHeader.substring(8, 2)),
 195 |      pceSvn: bytes2(rawHeader.substring(10, 2)),
 196 |      qeVendorId: qeVendorId,
 197 |      userData: bytes20(rawHeader.substring(28, 20))
 198 |  });
```
GitHub: [54-58](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L54-L58), [190-198](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L190-L198)


## [G-06] Avoid updating storage when the value hasn't changed

If the old value is equal to the new value, not re-storing the value will avoid a `Gsreset` (2900 gas), potentially at the expense of a `Gcoldsload` (2100 gas) or a `Gwarmaccess` (100 gas). Min = `Gsreset` - `Gcoldsload`, Max = `Gsreset` - `Gwarmaccess`.

*Instances: 20*

```solidity
File: packages/protocol/contracts/common/AddressManager.sol

     |  // @audit-info Contains state variable assignments
  38 |  function setAddress(
  39 |      uint64 _chainId,
  40 |      bytes32 _name,
  41 |      address _newAddress
  42 |  )
  43 |      external
  44 |      virtual
  45 |      onlyOwner
  :  |
     |      // @audit-issue Consider checking if the value has changed first
  49 |      __addresses[_chainId][_name] = _newAddress;
```
GitHub: [49](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L49)


```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

     |  // @audit-info Contains state variable assignments
  53 |  function setGuardians(
  54 |      address[] memory _newGuardians,
  55 |      uint8 _minGuardians
  56 |  )
  57 |      external
  58 |      onlyOwner
  59 |      nonReentrant
  :  |
     |          // @audit-issue Consider checking if the value has changed first
  88 |          guardianIds[guardian] = guardians.length;
  :  |
     |      // @audit-issue Consider checking if the value has changed first
  94 |      minGuardians = _minGuardians;
```
GitHub: [88](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L88), [94](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L94)


```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

     |  // @audit-info Contains state variable assignments
  25 |  function setConfigAndExcess(
  26 |      Config memory _newConfig,
  27 |      uint64 _newGasExcess
  28 |  )
  29 |      external
  30 |      virtual
  31 |      onlyOwner
  :  |
     |      // @audit-issue Consider checking if the value has changed first
  36 |      customConfig = _newConfig;
     |      // @audit-issue Consider checking if the value has changed first
  37 |      gasExcess = _newGasExcess;
```
GitHub: [36](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L36), [37](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L37)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

     |  // @audit-info Contains state variable assignments
 515 |  function _updateMessageStatus(bytes32 _msgHash, Status _status) private {
  :  |
     |      // @audit-issue Consider checking if the value has changed first
 518 |      messageStatus[_msgHash] = _status;
```
GitHub: [518](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L518)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

     |  // @audit-info Contains state variable assignments
  80 |  function setSnapshoter(address _snapshooter) external onlyOwner {
     |      // @audit-issue Consider checking if the value has changed first
  81 |      snapshooter = _snapshooter;
```
GitHub: [81](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L81)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

     |  // @audit-info Contains state variable assignments
  36 |  function changeMigrationStatus(
  37 |      address _migratingAddress,
  38 |      bool _migratingInbound
  39 |  )
  40 |      external
  41 |      nonReentrant
  42 |      whenNotPaused
  43 |      onlyFromOwnerOrNamed("erc20_vault")
  :  |
     |      // @audit-issue Consider checking if the value has changed first
  49 |      migratingAddress = _migratingAddress;
     |      // @audit-issue Consider checking if the value has changed first
  50 |      migratingInbound = _migratingInbound;
```
GitHub: [49](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L49), [50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L50)


```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

     |  // @audit-info Contains state variable assignments
 148 |  function changeBridgedToken(
 149 |      CanonicalERC20 calldata _ctoken,
 150 |      address _btokenNew
 151 |  )
 152 |      external
 153 |      nonReentrant
 154 |      whenNotPaused
 155 |      onlyOwner
 156 |      returns (address btokenOld_)
  :  |
     |          // @audit-issue Consider checking if the value has changed first
 181 |          btokenBlacklist[btokenOld_] = true;
  :  |
     |      // @audit-issue Consider checking if the value has changed first
 188 |      bridgedToCanonical[_btokenNew] = _ctoken;
     |      // @audit-issue Consider checking if the value has changed first
 189 |      canonicalToBridged[_ctoken.chainId][_ctoken.addr] = _btokenNew;
```
GitHub: [181](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L181), [188](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L188), [189](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L189)


```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

     |  // @audit-info Contains state variable assignments
 195 |  function _addInstances(
 196 |      address[] memory _instances,
 197 |      bool instantValid
 198 |  )
 199 |      private
 200 |      returns (uint256[] memory ids)
  :  |
     |          // @audit-issue Consider checking if the value has changed first
 213 |          addressRegistered[_instances[i]] = true;
  :  |
     |          // @audit-issue Consider checking if the value has changed first
 217 |          instances[nextInstanceId] = Instance(_instances[i], validSince);
```
GitHub: [213](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L213), [217](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L217)


```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

     |  // @audit-info Contains state variable assignments
  90 |  function _setConfig(uint64 _claimStart, uint64 _claimEnd, bytes32 _merkleRoot) private {
     |      // @audit-issue Consider checking if the value has changed first
  91 |      claimStart = _claimStart;
     |      // @audit-issue Consider checking if the value has changed first
  92 |      claimEnd = _claimEnd;
     |      // @audit-issue Consider checking if the value has changed first
  93 |      merkleRoot = _merkleRoot;
```
GitHub: [91](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L91), [92](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L92), [93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L93)


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

     |  // @audit-info Contains state variable assignments
  65 |  function setMrSigner(bytes32 _mrSigner, bool _trusted) external onlyOwner {
     |      // @audit-issue Consider checking if the value has changed first
  66 |      _trustedUserMrSigner[_mrSigner] = _trusted;

     |  // @audit-info Contains state variable assignments
  69 |  function setMrEnclave(bytes32 _mrEnclave, bool _trusted) external onlyOwner {
     |      // @audit-issue Consider checking if the value has changed first
  70 |      _trustedUserMrEnclave[_mrEnclave] = _trusted;

     |  // @audit-info Contains state variable assignments
  73 |  function addRevokedCertSerialNum(
  74 |      uint256 index,
  75 |      bytes[] calldata serialNumBatch
  76 |  )
  77 |      external
  78 |      onlyOwner
  :  |
     |          // @audit-issue Consider checking if the value has changed first
  84 |          _serialNumIsRevoked[index][serialNumBatch[i]] = true;
```
GitHub: [66](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L66), [70](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L70), [84](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L84)


## [G-07] Cache multiple accesses of mapping/array values

Caching a mapping's value in a local `storage` or `calldata` variable when the value is accessed multiple times, saves ~42 gas per access due to not having to recalculate the key's keccak256 hash (Gkeccak256 - 30 gas) and that calculation's associated stack operations. Caching an array's struct avoids recalculating the array offsets into memory/calldata.

*Instances: 84*

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

     |  // @audit-info Contains multiple accesses to state
 164 |  function _getProverFee(
 165 |      TaikoData.TierFee[] memory _tierFees,
 166 |      uint16 _tierId
 167 |  )
 168 |      private
 169 |      pure
 170 |      returns (uint256)
  :  |
     |          // @audit-issue Cache this value
     |          // @audit-issue Cache this value
 173 |          if (_tierFees[i].tier == _tierId) return _tierFees[i].fee;
```
GitHub: [173](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L173), [173](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L173)


```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

     |  // @audit-info Contains multiple accesses to state
  67 |  function processDeposits(
  68 |      TaikoData.State storage _state,
  69 |      TaikoData.Config memory _config,
  70 |      address _feeRecipient
  71 |  )
  72 |      internal
  73 |      returns (TaikoData.EthDeposit[] memory deposits_)
  :  |
     |              // @audit-issue Cache this value
     |              // @audit-issue Cache this value
  93 |              uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount;
```
GitHub: [93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L93), [93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L93)


```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

     |  // @audit-info Contains multiple accesses to state
  68 |  function proposeBlock(
  69 |      TaikoData.State storage _state,
  70 |      TaikoData.Config memory _config,
  71 |      IAddressResolver _resolver,
  72 |      bytes calldata _data,
  73 |      bytes calldata _txList
  74 |  )
  75 |      internal
  76 |      returns (TaikoData.BlockMetadata memory meta_, TaikoData.EthDeposit[] memory deposits_)
  :  |
     |              // @audit-issue Cache this value
 245 |              if (uint160(prevHook) >= uint160(params.hookCalls[i].hook)) {
  :  |
     |              // @audit-issue Cache this value
 253 |              IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }(
     |                  // @audit-issue Cache this value
 254 |                  blk, meta_, params.hookCalls[i].data
  :  |
     |              // @audit-issue Cache this value
 257 |              prevHook = params.hookCalls[i].hook;
```
GitHub: [245](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L245), [253](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L253), [254](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L254), [257](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L257)


```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

     |  // @audit-info Contains multiple accesses to state
 269 |  function _createTransition(
 270 |      TaikoData.State storage _state,
 271 |      TaikoData.Block storage _blk,
 272 |      TaikoData.Transition memory _tran,
 273 |      uint64 slot
 274 |  )
 275 |      private
 276 |      returns (uint32 tid_, TaikoData.TransitionState storage ts_)
  :  |
     |          // @audit-issue Cache this value
 299 |          ts_ = _state.transitions[slot][tid_];
  :  |
     |          // @audit-issue Cache this value
 345 |          ts_ = _state.transitions[slot][tid_];
  :  |
     |          // @audit-issue Cache this value
 299 |          ts_ = _state.transitions[slot][tid_];
  :  |
     |          // @audit-issue Cache this value
 345 |          ts_ = _state.transitions[slot][tid_];
```
GitHub: [299](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L299), [345](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L345), [299](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L299), [345](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L345)


```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

     |  // @audit-info Contains multiple accesses to state
  85 |  function verifyBlocks(
  86 |      TaikoData.State storage _state,
  87 |      TaikoData.Config memory _config,
  88 |      IAddressResolver _resolver,
  89 |      uint64 _maxBlocksToVerify
  90 |  )
  91 |      internal
  :  |
     |      // @audit-issue Cache this value
 104 |      TaikoData.Block storage blk = _state.blocks[slot];
  :  |
     |              // @audit-issue Cache this value
 130 |              blk = _state.blocks[slot];
  :  |
     |      // @audit-issue Cache this value
 115 |      bytes32 blockHash = _state.transitions[slot][tid].blockHash;
  :  |
     |              // @audit-issue Cache this value
 140 |              TaikoData.TransitionState storage ts = _state.transitions[slot][tid];
  :  |
     |      // @audit-issue Cache this value
 115 |      bytes32 blockHash = _state.transitions[slot][tid].blockHash;
  :  |
     |              // @audit-issue Cache this value
 140 |              TaikoData.TransitionState storage ts = _state.transitions[slot][tid];
```
GitHub: [104](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L104), [130](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L130), [115](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L115), [140](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L140), [115](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L115), [140](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L140)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

     |  // @audit-info Contains multiple accesses to state
 155 |  function recallMessage(
 156 |      Message calldata _message,
 157 |      bytes calldata _proof
 158 |  )
 159 |      external
 160 |      nonReentrant
 161 |      whenNotPaused
 162 |      sameChain(_message.srcChainId)
  :  |
     |      // @audit-issue Cache this value
 168 |      uint64 receivedAt = proofReceipt[msgHash].receivedAt;
  :  |
     |          // @audit-issue Cache this value
 190 |          delete proofReceipt[msgHash];

     |  // @audit-info Contains multiple accesses to state
 217 |  function processMessage(
 218 |      Message calldata _message,
 219 |      bytes calldata _proof
 220 |  )
 221 |      external
 222 |      nonReentrant
 223 |      whenNotPaused
 224 |      sameChain(_message.destChainId)
  :  |
     |      // @audit-issue Cache this value
 230 |      uint64 receivedAt = proofReceipt[msgHash].receivedAt;
  :  |
     |      // @audit-issue Cache this value
 250 |      if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) {
  :  |
     |          // @audit-issue Cache this value
 264 |          delete proofReceipt[msgHash];
```
GitHub: [168](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L168), [190](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L190), [230](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L230), [250](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L250), [264](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L264)


```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

     |  // @audit-info Contains multiple accesses to state
  93 |  function onMessageInvocation(bytes calldata data) external payable nonReentrant whenNotPaused {
  :  |
     |      // @audit-issue Cache this value
     |      // @audit-issue Cache this value
 100 |      ) = abi.decode(data, (CanonicalNFT, address, address, uint256[], uint256[]));

     |  // @audit-info Contains multiple accesses to state
 127 |  function onMessageRecalled(
 128 |      IBridge.Message calldata message,
 129 |      bytes32 msgHash
 130 |  )
 131 |      external
 132 |      payable
 133 |      override
 134 |      nonReentrant
 135 |      whenNotPaused
  :  |
     |          // @audit-issue Cache this value
     |          // @audit-issue Cache this value
 142 |          abi.decode(data, (CanonicalNFT, address, address, uint256[], uint256[]));

     |  // @audit-info Contains multiple accesses to state
 240 |  function _handleMessage(
 241 |      address _user,
 242 |      BridgeTransferOp memory _op
 243 |  )
 244 |      private
 245 |      returns (bytes memory msgData_, CanonicalNFT memory ctoken_)
  :  |
     |          // @audit-issue Cache this value
 249 |          if (bridgedToCanonical[_op.token].addr != address(0)) {
     |              // @audit-issue Cache this value
 250 |              ctoken_ = bridgedToCanonical[_op.token];
  :  |
     |                  // @audit-issue Cache this value
 252 |                  BridgedERC1155(_op.token).burn(_user, _op.tokenIds[i], _op.amounts[i]);
  :  |
     |                      // @audit-issue Cache this value
 273 |                      id: _op.tokenIds[i],
  :  |
     |                  // @audit-issue Cache this value
 252 |                  BridgedERC1155(_op.token).burn(_user, _op.tokenIds[i], _op.amounts[i]);
  :  |
     |                      // @audit-issue Cache this value
 274 |                      amount: _op.amounts[i],
```
GitHub: [100](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L100), [100](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L100), [142](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L142), [142](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L142), [249](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L249), [250](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L250), [252](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L252), [273](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L273), [252](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L252), [274](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L274)


```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

     |  // @audit-info Contains multiple accesses to state
 148 |  function changeBridgedToken(
 149 |      CanonicalERC20 calldata _ctoken,
 150 |      address _btokenNew
 151 |  )
 152 |      external
 153 |      nonReentrant
 154 |      whenNotPaused
 155 |      onlyOwner
 156 |      returns (address btokenOld_)
     |      // @audit-issue Cache this value
 158 |      if (_btokenNew == address(0) || bridgedToCanonical[_btokenNew].addr != address(0)) {
  :  |
     |          // @audit-issue Cache this value
 180 |          delete bridgedToCanonical[_btokenNew];

     |  // @audit-info Contains multiple accesses to state
 348 |  function _handleMessage(
 349 |      address _user,
 350 |      address _token,
 351 |      address _to,
 352 |      uint256 _amount
 353 |  )
 354 |      private
 355 |      returns (bytes memory msgData_, CanonicalERC20 memory ctoken_, uint256 balanceChange_)
  :  |
     |      // @audit-issue Cache this value
 358 |      if (bridgedToCanonical[_token].addr != address(0)) {
     |          // @audit-issue Cache this value
 359 |          ctoken_ = bridgedToCanonical[_token];
```
GitHub: [158](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L158), [180](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L180), [358](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L358), [359](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L359)


```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

     |  // @audit-info Contains multiple accesses to state
 160 |  function _transferTokens(
 161 |      CanonicalNFT memory _ctoken,
 162 |      address _to,
 163 |      uint256[] memory _tokenIds
 164 |  )
 165 |      private
 166 |      returns (address token_)
  :  |
     |              // @audit-issue Cache this value
 171 |              IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);
  :  |
     |              // @audit-issue Cache this value
 176 |              BridgedERC721(token_).mint(_to, _tokenIds[i]);

     |  // @audit-info Contains multiple accesses to state
 187 |  function _handleMessage(
 188 |      address _user,
 189 |      BridgeTransferOp memory _op
 190 |  )
 191 |      private
 192 |      returns (bytes memory msgData_, CanonicalNFT memory ctoken_)
  :  |
     |          // @audit-issue Cache this value
 195 |          if (bridgedToCanonical[_op.token].addr != address(0)) {
     |              // @audit-issue Cache this value
 196 |              ctoken_ = bridgedToCanonical[_op.token];
  :  |
     |                  // @audit-issue Cache this value
 198 |                  BridgedERC721(_op.token).burn(_user, _op.tokenIds[i]);
  :  |
     |                  // @audit-issue Cache this value
 211 |                  t.safeTransferFrom(_user, address(this), _op.tokenIds[i]);
```
GitHub: [171](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L171), [176](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L176), [195](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L195), [196](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L196), [198](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L198), [211](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L211)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

     |  // @audit-info Contains multiple accesses to state
  68 |  function get(
  69 |      bytes memory _key,
  70 |      bytes[] memory _proof,
  71 |      bytes32 _root
  72 |  )
  73 |      internal
  74 |      pure
  75 |      returns (bytes memory value_)
  :  |
     |                  // @audit-issue Cache this value
 171 |                  value_ = RLPReader.readBytes(currentNode.decoded[1]);
  :  |
     |                  // @audit-issue Cache this value
 188 |                  currentNodeID = _getNodeID(currentNode.decoded[1]);

     |  // @audit-info Contains multiple accesses to state
 205 |  function _parseProof(bytes[] memory _proof) private pure returns (TrieNode[] memory proof_) {
  :  |
     |          // @audit-issue Cache this value
     |          // @audit-issue Cache this value
 209 |          proof_[i] = TrieNode({ encoded: _proof[i], decoded: RLPReader.readList(_proof[i]) });
```
GitHub: [171](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L171), [188](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L188), [209](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L209), [209](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L209)


```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

     |  // @audit-info Contains multiple accesses to state
 100 |  function deleteInstances(uint256[] calldata _ids)
 101 |      external
 102 |      onlyFromOwnerOrNamed("rollup_watchdog")
  :  |
     |          // @audit-issue Cache this value
 107 |          if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();
  :  |
     |          // @audit-issue Cache this value
 109 |          emit InstanceDeleted(idx, instances[idx].addr);
  :  |
     |          // @audit-issue Cache this value
 111 |          delete instances[idx];

     |  // @audit-info Contains multiple accesses to state
 195 |  function _addInstances(
 196 |      address[] memory _instances,
 197 |      bool instantValid
 198 |  )
 199 |      private
 200 |      returns (uint256[] memory ids)
  :  |
     |          // @audit-issue Cache this value
 211 |          if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();
  :  |
     |          // @audit-issue Cache this value
 215 |          if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();
  :  |
     |          // @audit-issue Cache this value
 217 |          instances[nextInstanceId] = Instance(_instances[i], validSince);
  :  |
     |          // @audit-issue Cache this value
 220 |          emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);

     |  // @audit-info Contains multiple accesses to state
 233 |  function _isInstanceValid(uint256 id, address instance) private view returns (bool) {
  :  |
     |      // @audit-issue Cache this value
 235 |      if (instance != instances[id].addr) return false;
     |      // @audit-issue Cache this value
 236 |      return instances[id].validSince <= block.timestamp
     |          // @audit-issue Cache this value
 237 |          && block.timestamp <= instances[id].validSince + INSTANCE_EXPIRY;
```
GitHub: [107](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L107), [109](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L109), [111](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L111), [211](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L211), [215](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L215), [217](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L217), [220](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220), [235](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L235), [236](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L236), [237](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L237)


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

     |  // @audit-info Contains multiple accesses to state
  88 |  function removeRevokedCertSerialNum(
  89 |      uint256 index,
  90 |      bytes[] calldata serialNumBatch
  91 |  )
  92 |      external
  93 |      onlyOwner
  :  |
     |          // @audit-issue Cache this value
  96 |          if (!_serialNumIsRevoked[index][serialNumBatch[i]]) {
  :  |
     |          // @audit-issue Cache this value
  99 |          delete _serialNumIsRevoked[index][serialNumBatch[i]];
  :  |
     |          // @audit-issue Cache this value
  96 |          if (!_serialNumIsRevoked[index][serialNumBatch[i]]) {
  :  |
     |          // @audit-issue Cache this value
  99 |          delete _serialNumIsRevoked[index][serialNumBatch[i]];
  :  |
     |          // @audit-issue Cache this value
  96 |          if (!_serialNumIsRevoked[index][serialNumBatch[i]]) {
  :  |
     |          // @audit-issue Cache this value
  99 |          delete _serialNumIsRevoked[index][serialNumBatch[i]];

     |  // @audit-info Contains multiple accesses to state
 248 |  function _verifyCertChain(IPEMCertChainLib.ECSha256Certificate[] memory certs)
 249 |      private
 250 |      view
 251 |      returns (bool)
  :  |
     |              // @audit-issue Cache this value
 263 |              issuer = certs[i];
  :  |
     |                  // @audit-issue Cache this value
 268 |                  certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.ROOT)][certs[i]
  :  |
     |              // @audit-issue Cache this value
 270 |              } else if (certs[i].isPck) {
     |                  // @audit-issue Cache this value
 271 |                  certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.PCK)][certs[i]
  :  |
     |              // @audit-issue Cache this value
     |              // @audit-issue Cache this value
 280 |              block.timestamp > certs[i].notBefore && block.timestamp < certs[i].notAfter;
  :  |
     |              // @audit-issue Cache this value
     |              // @audit-issue Cache this value
 286 |              certs[i].tbsCertificate, certs[i].signature, issuer.pubKey

     |  // @audit-info Contains multiple accesses to state
 364 |  function _verifyParsedQuote(V3Struct.ParsedV3QuoteStruct memory v3quote)
 365 |      internal
 366 |      view
 367 |      returns (bool, bytes memory)
  :  |
     |          // @audit-issue Cache this value
 435 |          string memory parsedFmspc = parsedQuoteCerts[0].pck.sgxExtension.fmspc;
  :  |
     |          // @audit-issue Cache this value
 442 |          IPEMCertChainLib.ECSha256Certificate memory pckCert = parsedQuoteCerts[0];
  :  |
     |          // @audit-issue Cache this value
 454 |          (tcbVerified, tcbStatus) = _checkTcbLevels(parsedQuoteCerts[0].pck, fetchedTcbInfo);
  :  |
     |              // @audit-issue Cache this value
 472 |              parsedQuoteCerts[0].pubKey,
```
GitHub: [96](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L96), [99](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L99), [96](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L96), [99](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L99), [96](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L96), [99](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L99), [263](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L263), [268](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L268), [270](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L270), [271](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L271), [280](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L280), [280](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L280), [286](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L286), [286](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L286), [435](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L435), [442](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L442), [454](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L454), [472](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L472)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

     |  // @audit-info Contains multiple accesses to state
 154 |  function uintBytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes memory) {
  :  |
     |      // @audit-issue Cache this value
 156 |      require(der[ptr.ixf()] & 0x80 == 0, "Not positive");
  :  |
     |      // @audit-issue Cache this value
 158 |      if (der[ptr.ixf()] == 0) {

     |  // @audit-info Contains multiple accesses to state
 187 |  function _readNodeLength(bytes memory der, uint256 ix) private pure returns (uint256) {
  :  |
     |      // @audit-issue Cache this value
 191 |      if ((der[ix + 1] & 0x80) == 0) {
     |          // @audit-issue Cache this value
 192 |          length = uint8(der[ix + 1]);
  :  |
     |          // @audit-issue Cache this value
 196 |          uint8 lengthbytesLength = uint8(der[ix + 1] & 0x7F);
```
GitHub: [156](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L156), [158](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L158), [191](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L191), [192](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L192), [196](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L196)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

     |  // @audit-info Contains multiple accesses to state
  43 |  function pkcs1Sha256(
  44 |      bytes32 _sha256,
  45 |      bytes memory _s,
  46 |      bytes memory _e,
  47 |      bytes memory _m
  48 |  )
  49 |      internal
  50 |      view
  51 |      returns (bool)
  :  |
     |              // @audit-issue Cache this value
 153 |              if (decipher[3 + paddingLen + i] != bytes1(sha256ExplicitNullParam[i])) {
  :  |
     |              // @audit-issue Cache this value
 159 |              if (decipher[3 + paddingLen + i] != bytes1(sha256ImplicitNullParam[i])) {
```
GitHub: [153](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L153), [159](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L159)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

     |  // @audit-info Contains multiple accesses to state
   8 |  function toTimestamp(bytes memory x509Time) internal pure returns (uint256) {
  :  |
     |          // @audit-issue Cache this value
  18 |          if (uint8(x509Time[0]) - 48 < 5) yrs += 2000;
  :  |
     |          // @audit-issue Cache this value
  21 |          yrs += (uint8(x509Time[0]) - 48) * 1000 + (uint8(x509Time[1]) - 48) * 100;
```
GitHub: [18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L18), [21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L21)


## [G-08] Cache state variables accessed multiple times in the same function

The instances below point to the second+ access of a state variable within a function. Caching of a state variable replaces each Gwarmaccess (100 gas) with a much cheaper stack read. Other less obvious fixes/optimizations include having local memory caches of state variable structs, or having local caches of state variable contracts/addresses.

*Instances: 69*

```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

  72 |  function _resolve(
  73 |      uint64 _chainId,
  74 |      bytes32 _name,
  75 |      bool _allowZeroAddress
  76 |  )
  77 |      private
  78 |      view
  79 |      returns (address payable addr_)
     |      // @audit-issue addressManager read #1
  81 |      if (addressManager == address(0)) revert RESOLVER_INVALID_MANAGER();
  :  |
     |      // @audit-issue addressManager read #2
  83 |      addr_ = payable(IAddressManager(addressManager).getAddress(_chainId, _name));
```
GitHub: [81](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L81), [83](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L83)


```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

  53 |  function setGuardians(
  54 |      address[] memory _newGuardians,
  55 |      uint8 _minGuardians
  56 |  )
  57 |      external
  58 |      onlyOwner
  59 |      nonReentrant
  :  |
     |      // @audit-issue guardians read #1
  74 |      for (uint256 i; i < guardians.length; ++i) {
     |          // @audit-issue guardians read #2
     |          // @audit-issue guardianIds read #1
  75 |          delete guardianIds[guardians[i]];
  :  |
     |      // @audit-issue guardians read #3
  77 |      delete guardians;
  :  |
     |          // @audit-issue guardianIds read #2
  84 |          if (guardianIds[guardian] != 0) revert INVALID_GUARDIAN_SET();
  :  |
     |          // @audit-issue guardians read #4
  87 |          guardians.push(guardian);
     |          // @audit-issue guardians read #5
  88 |          guardianIds[guardian] = guardians.length;
  :  |
     |      // @audit-issue version read #1
  92 |      ++version;
  :  |
     |      // @audit-issue version read #2
  95 |      emit GuardiansUpdated(version, _newGuardians);
```
GitHub: [74](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L74), [75](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L75), [75](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L75), [77](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L77), [84](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L84), [87](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L87), [88](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L88), [92](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L92), [95](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L95)


```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

  55 |  function proposeBlock(
  56 |      bytes calldata _params,
  57 |      bytes calldata _txList
  58 |  )
  59 |      external
  60 |      payable
  61 |      nonReentrant
  62 |      whenNotPaused
  63 |      returns (TaikoData.BlockMetadata memory meta_, TaikoData.EthDeposit[] memory deposits_)
  :  |
     |      // @audit-issue state read #1
  67 |      (meta_, deposits_) = LibProposing.proposeBlock(state, config, this, _params, _txList);
  :  |
     |      // @audit-issue state read #2
  69 |      if (!state.slotB.provingPaused) {
     |          // @audit-issue state read #3
  70 |          LibVerifying.verifyBlocks(state, config, this, config.maxBlocksToVerifyPerProposal);

  75 |  function proveBlock(
  76 |      uint64 _blockId,
  77 |      bytes calldata _input
  78 |  )
  79 |      external
  80 |      nonReentrant
  81 |      whenNotPaused
  82 |      whenProvingNotPaused
  :  |
     |      // @audit-issue state read #1
  94 |      uint8 maxBlocksToVerify = LibProving.proveBlock(state, config, this, meta, tran, proof);
  :  |
     |      // @audit-issue state read #2
  96 |      LibVerifying.verifyBlocks(state, config, this, maxBlocksToVerify);

 145 |  function getBlock(uint64 _blockId)
 146 |      public
 147 |      view
 148 |      returns (TaikoData.Block memory blk_, TaikoData.TransitionState memory ts_)
  :  |
     |      // @audit-issue state read #1
 151 |      (blk_, slot) = LibUtils.getBlock(state, getConfig(), _blockId);
  :  |
     |          // @audit-issue state read #2
 154 |          ts_ = state.transitions[slot][blk_.verifiedTransitionId];

 176 |  function getStateVariables()
 177 |      public
 178 |      view
 179 |      returns (TaikoData.SlotA memory a_, TaikoData.SlotB memory b_)
     |      // @audit-issue state read #1
 181 |      a_ = state.slotA;
     |      // @audit-issue state read #2
 182 |      b_ = state.slotB;
```
GitHub: [67](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L67), [69](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L69), [70](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L70), [94](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L94), [96](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L96), [151](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L151), [154](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L154), [181](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L181), [182](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L182)


```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

  36 |  function onMessageInvocation(bytes calldata _data)
  37 |      external
  38 |      payable
  39 |      whenNotPaused
  40 |      onlyFromNamed("bridge")
  :  |
     |      // @audit-issue nextTxId read #1
  43 |      if (txId != nextTxId) revert XCO_INVALID_TX_ID();
  :  |
     |      // @audit-issue nextTxId read #2
  53 |      emit TransactionExecuted(nextTxId++, bytes4(txdata));
```
GitHub: [43](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L43), [53](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L53)


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

 252 |  function _calc1559BaseFee(
 253 |      Config memory _config,
 254 |      uint64 _l1BlockId,
 255 |      uint32 _parentGasUsed
 256 |  )
 257 |      private
 258 |      view
 259 |      returns (uint256 basefee_, uint64 gasExcess_)
  :  |
     |      // @audit-issue gasExcess read #1
 262 |      if (gasExcess > 0) {
  :  |
     |          // @audit-issue gasExcess read #2
 265 |          uint256 excess = uint256(gasExcess) + _parentGasUsed;
  :  |
     |          // @audit-issue lastSyncedBlock read #1
     |          // @audit-issue lastSyncedBlock read #2
 275 |          if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {
     |              // @audit-issue lastSyncedBlock read #3
 276 |              numL1Blocks = _l1BlockId - lastSyncedBlock;
```
GitHub: [262](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L262), [265](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L265), [275](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L275), [275](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L275), [276](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L276)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 155 |  function recallMessage(
 156 |      Message calldata _message,
 157 |      bytes calldata _proof
 158 |  )
 159 |      external
 160 |      nonReentrant
 161 |      whenNotPaused
 162 |      sameChain(_message.srcChainId)
  :  |
     |      // @audit-issue proofReceipt read #1
 168 |      uint64 receivedAt = proofReceipt[msgHash].receivedAt;
  :  |
     |          // @audit-issue proofReceipt read #2
 190 |          delete proofReceipt[msgHash];

 217 |  function processMessage(
 218 |      Message calldata _message,
 219 |      bytes calldata _proof
 220 |  )
 221 |      external
 222 |      nonReentrant
 223 |      whenNotPaused
 224 |      sameChain(_message.destChainId)
  :  |
     |      // @audit-issue proofReceipt read #1
 230 |      uint64 receivedAt = proofReceipt[msgHash].receivedAt;
  :  |
     |      // @audit-issue proofReceipt read #2
 250 |      if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) {
  :  |
     |          // @audit-issue proofReceipt read #3
 264 |          delete proofReceipt[msgHash];
```
GitHub: [168](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L168), [190](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L190), [230](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L230), [250](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L250), [264](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L264)


```solidity
File: packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

  47 |  function _burnToken(address _from, uint256 _amount) internal override {
     |      // @audit-issue usdc read #1
  48 |      usdc.transferFrom(_from, address(this), _amount);
     |      // @audit-issue usdc read #2
  49 |      usdc.burn(_amount);
```
GitHub: [48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L48), [49](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L49)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

  57 |  function mint(address _account, uint256 _amount) public nonReentrant whenNotPaused {
  :  |
     |      // @audit-issue migratingAddress read #1
  61 |      if (msg.sender == migratingAddress) {
  :  |
     |          // @audit-issue migratingAddress read #2
  63 |          emit MigratedTo(migratingAddress, _account, _amount);

  75 |  function burn(address _account, uint256 _amount) public nonReentrant whenNotPaused {
  :  |
     |          // @audit-issue migratingAddress read #1
  80 |          emit MigratedTo(migratingAddress, _account, _amount);
  :  |
     |          // @audit-issue migratingAddress read #2
  82 |          IBridgedERC20(migratingAddress).mint(_account, _amount);
```
GitHub: [61](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L61), [63](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L63), [80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L80), [82](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L82)


```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

 240 |  function _handleMessage(
 241 |      address _user,
 242 |      BridgeTransferOp memory _op
 243 |  )
 244 |      private
 245 |      returns (bytes memory msgData_, CanonicalNFT memory ctoken_)
  :  |
     |          // @audit-issue bridgedToCanonical read #1
 249 |          if (bridgedToCanonical[_op.token].addr != address(0)) {
     |              // @audit-issue bridgedToCanonical read #2
 250 |              ctoken_ = bridgedToCanonical[_op.token];
```
GitHub: [249](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L249), [250](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L250)


```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

 148 |  function changeBridgedToken(
 149 |      CanonicalERC20 calldata _ctoken,
 150 |      address _btokenNew
 151 |  )
 152 |      external
 153 |      nonReentrant
 154 |      whenNotPaused
 155 |      onlyOwner
 156 |      returns (address btokenOld_)
     |      // @audit-issue bridgedToCanonical read #1
 158 |      if (_btokenNew == address(0) || bridgedToCanonical[_btokenNew].addr != address(0)) {
  :  |
     |          // @audit-issue bridgedToCanonical read #2
 171 |          CanonicalERC20 memory ctoken = bridgedToCanonical[btokenOld_];
  :  |
     |          // @audit-issue bridgedToCanonical read #3
 180 |          delete bridgedToCanonical[_btokenNew];

 348 |  function _handleMessage(
 349 |      address _user,
 350 |      address _token,
 351 |      address _to,
 352 |      uint256 _amount
 353 |  )
 354 |      private
 355 |      returns (bytes memory msgData_, CanonicalERC20 memory ctoken_, uint256 balanceChange_)
  :  |
     |      // @audit-issue bridgedToCanonical read #1
 358 |      if (bridgedToCanonical[_token].addr != address(0)) {
     |          // @audit-issue bridgedToCanonical read #2
 359 |          ctoken_ = bridgedToCanonical[_token];
```
GitHub: [158](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L158), [171](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L171), [180](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L180), [358](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L358), [359](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L359)


```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

 187 |  function _handleMessage(
 188 |      address _user,
 189 |      BridgeTransferOp memory _op
 190 |  )
 191 |      private
 192 |      returns (bytes memory msgData_, CanonicalNFT memory ctoken_)
  :  |
     |          // @audit-issue bridgedToCanonical read #1
 195 |          if (bridgedToCanonical[_op.token].addr != address(0)) {
     |              // @audit-issue bridgedToCanonical read #2
 196 |              ctoken_ = bridgedToCanonical[_op.token];
```
GitHub: [195](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L195), [196](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L196)


```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

 100 |  function deleteInstances(uint256[] calldata _ids)
 101 |      external
 102 |      onlyFromOwnerOrNamed("rollup_watchdog")
  :  |
     |          // @audit-issue instances read #1
 107 |          if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();
  :  |
     |          // @audit-issue instances read #2
 109 |          emit InstanceDeleted(idx, instances[idx].addr);
  :  |
     |          // @audit-issue instances read #3
 111 |          delete instances[idx];

 195 |  function _addInstances(
 196 |      address[] memory _instances,
 197 |      bool instantValid
 198 |  )
 199 |      private
 200 |      returns (uint256[] memory ids)
  :  |
     |          // @audit-issue nextInstanceId read #1
 218 |          ids[i] = nextInstanceId;
  :  |
     |          // @audit-issue nextInstanceId read #2
 220 |          emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);
  :  |
     |          // @audit-issue nextInstanceId read #3
 222 |          nextInstanceId++;

 233 |  function _isInstanceValid(uint256 id, address instance) private view returns (bool) {
  :  |
     |      // @audit-issue instances read #1
 235 |      if (instance != instances[id].addr) return false;
     |      // @audit-issue instances read #2
 236 |      return instances[id].validSince <= block.timestamp
     |          // @audit-issue instances read #3
 237 |          && block.timestamp <= instances[id].validSince + INSTANCE_EXPIRY;
```
GitHub: [107](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L107), [109](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L109), [111](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L111), [218](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L218), [220](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220), [222](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L222), [235](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L235), [236](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L236), [237](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L237)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

  50 |  function claimAndDelegate(
  51 |      address user,
  52 |      uint256 amount,
  53 |      bytes32[] calldata proof,
  54 |      bytes calldata delegationData
  55 |  )
  56 |      external
  57 |      nonReentrant
  :  |
     |      // @audit-issue token read #1
  63 |      IERC20(token).transferFrom(vault, user, amount);
  :  |
     |      // @audit-issue token read #2
  71 |      IVotes(token).delegateBySig(delegatee, nonce, expiry, v, r, s);
```
GitHub: [63](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L63), [71](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L71)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

 104 |  function getBalance(address user)
 105 |      public
 106 |      view
 107 |      returns (uint256 balance, uint256 withdrawableAmount)
  :  |
     |      // @audit-issue claimEnd read #1
 114 |      if (block.timestamp < claimEnd) return (balance, 0);
  :  |
     |          // @audit-issue claimEnd read #2
     |          // @audit-issue claimEnd read #3
     |          // @audit-issue withdrawalWindow read #1
     |          // @audit-issue withdrawalWindow read #2
 118 |          * (block.timestamp.min(claimEnd + withdrawalWindow) - claimEnd) / withdrawalWindow;
```
GitHub: [114](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L114), [118](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L118), [118](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L118), [118](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L118), [118](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L118)


```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

 208 |  function _withdraw(address _recipient, address _to) private {
  :  |
     |      // @audit-issue sharedVault read #1
 219 |      IERC20(taikoToken).transferFrom(sharedVault, _to, amountToWithdraw);
     |      // @audit-issue sharedVault read #2
 220 |      IERC20(costToken).safeTransferFrom(_recipient, sharedVault, costToWithdraw);
```
GitHub: [219](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L219), [220](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L220)


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

  88 |  function removeRevokedCertSerialNum(
  89 |      uint256 index,
  90 |      bytes[] calldata serialNumBatch
  91 |  )
  92 |      external
  93 |      onlyOwner
  :  |
     |          // @audit-issue _serialNumIsRevoked read #1
  96 |          if (!_serialNumIsRevoked[index][serialNumBatch[i]]) {
  :  |
     |          // @audit-issue _serialNumIsRevoked read #2
  99 |          delete _serialNumIsRevoked[index][serialNumBatch[i]];

 248 |  function _verifyCertChain(IPEMCertChainLib.ECSha256Certificate[] memory certs)
 249 |      private
 250 |      view
 251 |      returns (bool)
  :  |
     |                  // @audit-issue _serialNumIsRevoked read #1
 268 |                  certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.ROOT)][certs[i]
  :  |
     |                  // @audit-issue _serialNumIsRevoked read #2
 271 |                  certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.PCK)][certs[i]
```
GitHub: [96](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L96), [99](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L99), [268](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L268), [271](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L271)


## [G-09] Calculation results within a function can be cached to save gas

Cache the results of calculations within a function rather than repeating them.

*Instances: 11*

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

     |  // @audit-info Duplicates of this operation were detected
 105 |  if (blk.blockId != blockId) revert L1_BLOCK_MISMATCH();
  :  |
     |          // @audit-issue First seen at packages/protocol/contracts/L1/libs/LibVerifying.sol:105
 131 |          if (blk.blockId != blockId) revert L1_BLOCK_MISMATCH();
```
GitHub: [131](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L131)


```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

     |  // @audit-info Duplicates of this operation were detected
 251 |  for (uint256 i; i < _op.tokenIds.length; ++i) {
  :  |
     |  // @audit-issue First seen at packages/protocol/contracts/tokenvault/ERC1155Vault.sol:251
 269 |  for (uint256 i; i < _op.tokenIds.length; ++i) {
```
GitHub: [269](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L269)


```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

     |  // @audit-info Duplicates of this operation were detected
 170 |  for (uint256 i; i < _tokenIds.length; ++i) {
  :  |
     |  // @audit-issue First seen at packages/protocol/contracts/tokenvault/ERC721Vault.sol:170
 175 |  for (uint256 i; i < _tokenIds.length; ++i) {
```
GitHub: [175](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L175)


```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

     |  // @audit-info Duplicates of this operation were detected
 197 |  for (uint256 i; i < _op.tokenIds.length; ++i) {
  :  |
     |  // @audit-issue First seen at packages/protocol/contracts/tokenvault/ERC721Vault.sol:197
 210 |  for (uint256 i; i < _op.tokenIds.length; ++i) {
```
GitHub: [210](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L210)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

     |      // @audit-info Duplicates of this operation were detected
  78 |      ptr: MemoryPointer.wrap(MemoryPointer.unwrap(_in.ptr) + offset)
  :  |
     |  // @audit-issue First seen at packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol:78
  86 |  ptr: MemoryPointer.wrap(MemoryPointer.unwrap(_in.ptr) + offset)
```
GitHub: [86](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L86)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

     |  // @audit-info Duplicates of this operation were detected
 120 |  value_.length > 0,
  :  |
     |  // @audit-issue First seen at packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol:120
 173 |  value_.length > 0,
```
GitHub: [173](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L173)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

     |  // @audit-info Duplicates of this operation were detected
 126 |  i == proof.length - 1,
  :  |
     |  // @audit-issue First seen at packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol:126
 179 |  i == proof.length - 1,
```
GitHub: [179](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L179)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

     |  // @audit-info Duplicates of this operation were detected
 194 |  ixLastContentByte = uint80(ixFirstContentByte + length - 1);
  :  |
     |  // @audit-issue First seen at packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol:194
 207 |  ixLastContentByte = uint80(ixFirstContentByte + length - 1);
```
GitHub: [207](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L207)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

     |  // @audit-info Duplicates of this operation were detected
 341 |  ret = (ret << 5) | decoded;
  :  |
     |  // @audit-issue First seen at packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol:341
 347 |  ret = (ret << 5) | decoded;
```
GitHub: [347](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L347)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

     |  // @audit-info Duplicates of this operation were detected
  35 |  if (publicKey.keyType != KeyType.RSA) {
  :  |
     |  // @audit-issue First seen at packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol:35
  45 |  if (publicKey.keyType != KeyType.RSA) {
```
GitHub: [45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L45)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

     |  // @audit-info Duplicates of this operation were detected
  65 |  if (publicKey.keyType != KeyType.RSA) {
  :  |
     |  // @audit-issue First seen at packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol:65
  70 |  if (publicKey.keyType != KeyType.RSA) {
```
GitHub: [70](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L70)


## [G-10] Consider changing some `public` variables to `private`/`internal`

Public state variables in Solidity automatically generate getter functions, increasing deployment costs.
                    
Examples of variables that probably don't need to be public - anybody who needs to inspect them can check the on-chain contract storage:

* Factories
* Controllers
* Governance
* Owner, roles, etc.



*Instances: 86*

```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

     |  // @audit-issue Reconsider whether this variable has to be public
  13 |  address public addressManager;
```
GitHub: [13](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L13)


```solidity
File: packages/protocol/contracts/libs/Lib4844.sol

     |  // @audit-issue Reconsider whether this variable has to be public
  10 |  address public constant POINT_EVALUATION_PRECOMPILE_ADDRESS = address(0x0A);

     |  // @audit-issue Reconsider whether this variable has to be public
  13 |  uint32 public constant FIELD_ELEMENTS_PER_BLOB = 4096;

     |  // @audit-issue Reconsider whether this variable has to be public
  16 |  uint256 public constant BLS_MODULUS =
  17 |      52_435_875_175_126_190_479_447_740_508_185_965_837_690_552_500_527_637_822_603_658_699_938_581_184_513;
```
GitHub: [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/Lib4844.sol#L10), [13](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/Lib4844.sol#L13), [16-17](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/Lib4844.sol#L16-L17)


```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

     |  // @audit-issue Reconsider whether this variable has to be public
  38 |  uint256 public constant MAX_GAS_PAYING_PROVER = 50_000;
```
GitHub: [38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L38)


```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

     |  // @audit-issue Reconsider whether this variable has to be public
  21 |  uint256 public constant MAX_BYTES_PER_BLOB = 4096 * 32;
```
GitHub: [21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L21)


```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

     |  // @audit-issue Reconsider whether this variable has to be public
  20 |  bytes32 public constant RETURN_LIVENESS_BOND = keccak256("RETURN_LIVENESS_BOND");

     |  // @audit-issue Reconsider whether this variable has to be public
  23 |  bytes32 public constant TIER_OP = bytes32("tier_optimistic");
```
GitHub: [20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L20), [23](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L23)


```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

     |  // @audit-issue Reconsider whether this variable has to be public
  11 |  uint256 public constant MIN_NUM_GUARDIANS = 5;

     |  // @audit-issue Reconsider whether this variable has to be public
  16 |  mapping(address guardian => uint256 id) public guardianIds;

     |  // @audit-issue Reconsider whether this variable has to be public
  23 |  address[] public guardians;

     |  // @audit-issue Reconsider whether this variable has to be public
  27 |  uint32 public version;

     |  // @audit-issue Reconsider whether this variable has to be public
  30 |  uint32 public minGuardians;
```
GitHub: [11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L11), [16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L16), [23](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L23), [27](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L27), [30](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L30)


```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

     |  // @audit-issue Reconsider whether this variable has to be public
  24 |  TaikoData.State public state;
```
GitHub: [24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L24)


```solidity
File: packages/protocol/contracts/L1/tiers/ITierProvider.sol

     |  // @audit-issue Reconsider whether this variable has to be public
  39 |  uint16 public constant TIER_OPTIMISTIC = 100;

     |  // @audit-issue Reconsider whether this variable has to be public
  42 |  uint16 public constant TIER_SGX = 200;

     |  // @audit-issue Reconsider whether this variable has to be public
  45 |  uint16 public constant TIER_SGX_ZKVM = 300;

     |  // @audit-issue Reconsider whether this variable has to be public
  48 |  uint16 public constant TIER_GUARDIAN = 1000;
```
GitHub: [39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L39), [42](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L42), [45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L45), [48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L48)


```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

     |  // @audit-issue Reconsider whether this variable has to be public
  16 |  uint64 public ownerChainId;

     |  // @audit-issue Reconsider whether this variable has to be public
  19 |  uint64 public nextTxId;
```
GitHub: [16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L16), [19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L19)


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

     |  // @audit-issue Reconsider whether this variable has to be public
  32 |  address public constant GOLDEN_TOUCH_ADDRESS = 0x0000777735367b36bC9B61C50022d9D0700dB4Ec;

     |  // @audit-issue Reconsider whether this variable has to be public
  35 |  uint8 public constant BLOCK_SYNC_THRESHOLD = 5;

     |  // @audit-issue Reconsider whether this variable has to be public
  39 |  mapping(uint256 blockId => bytes32 blockHash) public l2Hashes;

     |  // @audit-issue Reconsider whether this variable has to be public
  43 |  bytes32 public publicInputHash;

     |  // @audit-issue Reconsider whether this variable has to be public
  47 |  uint64 public gasExcess;

     |  // @audit-issue Reconsider whether this variable has to be public
  50 |  uint64 public lastSyncedBlock;
```
GitHub: [32](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L32), [35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L35), [39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L39), [43](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L43), [47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L47), [50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L50)


```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

     |  // @audit-issue Reconsider whether this variable has to be public
  11 |  Config public customConfig;
```
GitHub: [11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L11)


```solidity
File: packages/protocol/contracts/signal/LibSignals.sol

     |  // @audit-issue Reconsider whether this variable has to be public
   8 |  bytes32 public constant STATE_ROOT = keccak256("STATE_ROOT");

     |  // @audit-issue Reconsider whether this variable has to be public
  11 |  bytes32 public constant SIGNAL_ROOT = keccak256("SIGNAL_ROOT");
```
GitHub: [8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/LibSignals.sol#L8), [11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/LibSignals.sol#L11)


```solidity
File: packages/protocol/contracts/signal/SignalService.sol

     |  // @audit-issue Reconsider whether this variable has to be public
  17 |  mapping(uint64 chainId => mapping(bytes32 kind => uint64 blockId)) public topBlockId;

     |  // @audit-issue Reconsider whether this variable has to be public
  21 |  mapping(address addr => bool authorized) public isAuthorized;
```
GitHub: [17](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L17), [21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L21)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

     |  // @audit-issue Reconsider whether this variable has to be public
  31 |  uint128 public nextMessageId;

     |  // @audit-issue Reconsider whether this variable has to be public
  35 |  mapping(bytes32 msgHash => Status status) public messageStatus;

     |  // @audit-issue Reconsider whether this variable has to be public
  42 |  mapping(address addr => bool banned) public addressBanned;

     |  // @audit-issue Reconsider whether this variable has to be public
  46 |  mapping(bytes32 msgHash => ProofReceipt receipt) public proofReceipt;
```
GitHub: [31](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L31), [35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L35), [42](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L42), [46](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L46)


```solidity
File: packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

     |  // @audit-issue Reconsider whether this variable has to be public
  31 |  IUSDC public usdc;
```
GitHub: [31](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L31)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

     |  // @audit-issue Reconsider whether this variable has to be public
  22 |  address public srcToken;

     |  // @audit-issue Reconsider whether this variable has to be public
  27 |  uint256 public srcChainId;

     |  // @audit-issue Reconsider whether this variable has to be public
  30 |  address public snapshooter;
```
GitHub: [22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L22), [27](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L27), [30](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L30)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

     |  // @audit-issue Reconsider whether this variable has to be public
  11 |  address public migratingAddress;

     |  // @audit-issue Reconsider whether this variable has to be public
  14 |  bool public migratingInbound;
```
GitHub: [11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L11), [14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L14)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

     |  // @audit-issue Reconsider whether this variable has to be public
  14 |  address public srcToken;

     |  // @audit-issue Reconsider whether this variable has to be public
  17 |  uint256 public srcChainId;
```
GitHub: [14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L14), [17](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L17)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

     |  // @audit-issue Reconsider whether this variable has to be public
  16 |  address public srcToken;

     |  // @audit-issue Reconsider whether this variable has to be public
  19 |  uint256 public srcChainId;
```
GitHub: [16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L16), [19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L19)


```solidity
File: packages/protocol/contracts/tokenvault/BaseNFTVault.sol

     |  // @audit-issue Reconsider whether this variable has to be public
  47 |  bytes4 public constant ERC1155_INTERFACE_ID = 0xd9b67a26;

     |  // @audit-issue Reconsider whether this variable has to be public
  50 |  bytes4 public constant ERC721_INTERFACE_ID = 0x80ac58cd;

     |  // @audit-issue Reconsider whether this variable has to be public
  53 |  uint256 public constant MAX_TOKEN_PER_TXN = 10;

     |  // @audit-issue Reconsider whether this variable has to be public
  56 |  mapping(address btoken => CanonicalNFT canonical) public bridgedToCanonical;

     |  // @audit-issue Reconsider whether this variable has to be public
  59 |  mapping(uint256 chainId => mapping(address ctoken => address btoken)) public canonicalToBridged;
```
GitHub: [47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L47), [50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L50), [53](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L53), [56](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L56), [59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L59)


```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

     |  // @audit-issue Reconsider whether this variable has to be public
  45 |  mapping(address btoken => CanonicalERC20 canonical) public bridgedToCanonical;

     |  // @audit-issue Reconsider whether this variable has to be public
  49 |  mapping(uint256 chainId => mapping(address ctoken => address btoken)) public canonicalToBridged;

     |  // @audit-issue Reconsider whether this variable has to be public
  52 |  mapping(address btoken => bool blacklisted) public btokenBlacklist;
```
GitHub: [45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L45), [49](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L49), [52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L52)


```solidity
File: packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol

     |  // @audit-issue Reconsider whether this variable has to be public
   7 |  uint128 public constant MAX_EXP_INPUT = 135_305_999_368_893_231_588;

     |  // @audit-issue Reconsider whether this variable has to be public
   8 |  uint256 public constant SCALING_FACTOR = 1e18; // For fixed point representation factor
```
GitHub: [7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L7), [8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L8)


```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

     |  // @audit-issue Reconsider whether this variable has to be public
  30 |  uint64 public constant INSTANCE_EXPIRY = 180 days;

     |  // @audit-issue Reconsider whether this variable has to be public
  34 |  uint64 public constant INSTANCE_VALIDITY_DELAY = 1 days;

     |  // @audit-issue Reconsider whether this variable has to be public
  39 |  uint256 public nextInstanceId;

     |  // @audit-issue Reconsider whether this variable has to be public
  47 |  mapping(uint256 instanceId => Instance instance) public instances;

     |  // @audit-issue Reconsider whether this variable has to be public
  55 |  mapping(address instanceAddress => bool alreadyAttested) public addressRegistered;
```
GitHub: [30](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L30), [34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L34), [39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L39), [47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L47), [55](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L55)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

     |  // @audit-issue Reconsider whether this variable has to be public
  13 |  address public token;

     |  // @audit-issue Reconsider whether this variable has to be public
  16 |  address public vault;
```
GitHub: [13](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L13), [16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L16)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

     |  // @audit-issue Reconsider whether this variable has to be public
  16 |  address public token;

     |  // @audit-issue Reconsider whether this variable has to be public
  19 |  address public vault;

     |  // @audit-issue Reconsider whether this variable has to be public
  22 |  mapping(address addr => uint256 amountClaimed) public claimedAmount;

     |  // @audit-issue Reconsider whether this variable has to be public
  25 |  mapping(address addr => uint256 amountWithdrawn) public withdrawnAmount;

     |  // @audit-issue Reconsider whether this variable has to be public
  28 |  uint64 public withdrawalWindow;
```
GitHub: [16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L16), [19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L19), [22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L22), [25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L25), [28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L28)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

     |  // @audit-issue Reconsider whether this variable has to be public
  11 |  address public token;

     |  // @audit-issue Reconsider whether this variable has to be public
  14 |  address public vault;
```
GitHub: [11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L11), [14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L14)


```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

     |  // @audit-issue Reconsider whether this variable has to be public
  12 |  mapping(bytes32 hash => bool claimed) public isClaimed;

     |  // @audit-issue Reconsider whether this variable has to be public
  15 |  bytes32 public merkleRoot;

     |  // @audit-issue Reconsider whether this variable has to be public
  18 |  uint64 public claimStart;

     |  // @audit-issue Reconsider whether this variable has to be public
  21 |  uint64 public claimEnd;
```
GitHub: [12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L12), [15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L15), [18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L18), [21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L21)


```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

     |  // @audit-issue Reconsider whether this variable has to be public
  59 |  address public taikoToken;

     |  // @audit-issue Reconsider whether this variable has to be public
  62 |  address public costToken;

     |  // @audit-issue Reconsider whether this variable has to be public
  65 |  address public sharedVault;

     |  // @audit-issue Reconsider whether this variable has to be public
  68 |  uint128 public totalAmountGranted;

     |  // @audit-issue Reconsider whether this variable has to be public
  71 |  uint128 public totalAmountVoided;

     |  // @audit-issue Reconsider whether this variable has to be public
  74 |  uint128 public totalAmountWithdrawn;

     |  // @audit-issue Reconsider whether this variable has to be public
  77 |  uint128 public totalCostPaid;

     |  // @audit-issue Reconsider whether this variable has to be public
  80 |  mapping(address recipient => Recipient receipt) public recipients;
```
GitHub: [59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L59), [62](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L62), [65](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L65), [68](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L68), [71](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L71), [74](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L74), [77](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L77), [80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L80)


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

     |  // @audit-issue Reconsider whether this variable has to be public
  25 |  ISigVerifyLib public immutable sigVerifyLib;

     |  // @audit-issue Reconsider whether this variable has to be public
  26 |  IPEMCertChainLib public immutable pemCertLib;

     |  // @audit-issue Reconsider whether this variable has to be public
  49 |  mapping(string fmspc => TCBInfoStruct.TCBInfo tcbInfo) public tcbInfo;

     |  // @audit-issue Reconsider whether this variable has to be public
  50 |  EnclaveIdStruct.EnclaveId public qeIdentity;

     |  // @audit-issue Reconsider whether this variable has to be public
  52 |  address public owner;
```
GitHub: [25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L25), [26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L26), [49](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L49), [50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L50), [52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L52)


## [G-11] Consider merging sequential for loops

Merging multiple `for` loops within a function in Solidity can enhance efficiency and reduce gas costs, especially when they share a common iterating variable or perform related operations. By minimizing redundant iterations over the same data set, execution becomes more cost-effective. However, while merging can optimize gas usage and simplify logic, it may also increase code complexity. Therefore, careful balance between optimization and maintainability is essential, along with thorough testing to ensure the refactored code behaves as expected.

*Instances: 8*

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

     |  // @audit-info Context
 240 |  function _handleMessage(
 241 |      address _user,
 242 |      BridgeTransferOp memory _op
 243 |  )
 244 |      private
 245 |      returns (bytes memory msgData_, CanonicalNFT memory ctoken_)
  :  |
     |              // @audit-issue Duplicated loop control structure
 251 |              for (uint256 i; i < _op.tokenIds.length; ++i) {
 252 |                  BridgedERC1155(_op.token).burn(_user, _op.tokenIds[i], _op.amounts[i]);
 253 |              }
  :  |
     |              // @audit-issue Duplicated loop control structure
 269 |              for (uint256 i; i < _op.tokenIds.length; ++i) {
 270 |                  IERC1155(_op.token).safeTransferFrom({
 271 |                      from: msg.sender,
 272 |                      to: address(this),
 273 |                      id: _op.tokenIds[i],
 274 |                      amount: _op.amounts[i],
 275 |                      data: ""
 276 |                  });
 277 |              }
```
GitHub: [251-253](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L251-L253), [269-277](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L269-L277)


```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

     |  // @audit-info Context
 160 |  function _transferTokens(
 161 |      CanonicalNFT memory _ctoken,
 162 |      address _to,
 163 |      uint256[] memory _tokenIds
 164 |  )
 165 |      private
 166 |      returns (address token_)
  :  |
     |          // @audit-issue Duplicated loop control structure
 170 |          for (uint256 i; i < _tokenIds.length; ++i) {
 171 |              IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);
 172 |          }
  :  |
     |          // @audit-issue Duplicated loop control structure
 175 |          for (uint256 i; i < _tokenIds.length; ++i) {
 176 |              BridgedERC721(token_).mint(_to, _tokenIds[i]);
 177 |          }

     |  // @audit-info Context
 187 |  function _handleMessage(
 188 |      address _user,
 189 |      BridgeTransferOp memory _op
 190 |  )
 191 |      private
 192 |      returns (bytes memory msgData_, CanonicalNFT memory ctoken_)
  :  |
     |              // @audit-issue Duplicated loop control structure
 197 |              for (uint256 i; i < _op.tokenIds.length; ++i) {
 198 |                  BridgedERC721(_op.token).burn(_user, _op.tokenIds[i]);
 199 |              }
  :  |
     |              // @audit-issue Duplicated loop control structure
 210 |              for (uint256 i; i < _op.tokenIds.length; ++i) {
 211 |                  t.safeTransferFrom(_user, address(this), _op.tokenIds[i]);
 212 |              }
```
GitHub: [170-172](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L170-L172), [175-177](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L175-L177), [197-199](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L197-L199), [210-212](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L210-L212)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

     |  // @audit-info Context
  43 |  function pkcs1Sha256(
  44 |      bytes32 _sha256,
  45 |      bytes memory _s,
  46 |      bytes memory _e,
  47 |      bytes memory _m
  48 |  )
  49 |      internal
  50 |      view
  51 |      returns (bool)
  :  |
     |          // @audit-issue Duplicated loop control structure
 152 |          for (uint256 i; i < digestAlgoWithParamLen; ++i) {
 153 |              if (decipher[3 + paddingLen + i] != bytes1(sha256ExplicitNullParam[i])) {
 154 |                  return false;
 155 |              }
 156 |          }
  :  |
     |          // @audit-issue Duplicated loop control structure
 158 |          for (uint256 i; i < digestAlgoWithParamLen; ++i) {
 159 |              if (decipher[3 + paddingLen + i] != bytes1(sha256ImplicitNullParam[i])) {
 160 |                  return false;
 161 |              }
 162 |          }
```
GitHub: [152-156](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L152-L156), [158-162](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L158-L162)


## [G-12] Consider pre-calculating the address of `address(this)` to save gas

Instead of using `address(this)`, it is more gas-efficient to pre-calculate and use the hardcoded address. Foundry's `script.sol` and solmate's `LibRlp.sol` contracts can help achieve this.
Refrences:-[book.getfoundry](https://book.getfoundry.sh/reference/forge-std/compute-create-address)-[twitter](https://twitter.com/transmissions11/status/1518507047943245824).

*Instances: 42*

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

     |  // @audit-issue Pre-calculate & hardcode instead
 125 |  if (address(this).balance > 0) {

     |  // @audit-issue Pre-calculate & hardcode instead
 126 |  taikoL1Address.sendEther(address(this).balance);

     |  // @audit-issue Pre-calculate & hardcode instead
 151 |  address(this),
```
GitHub: [125](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L125), [126](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L126), [151](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L151)


```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

     |  // @audit-issue Pre-calculate & hardcode instead
 238 |  uint256 tkoBalance = tko.balanceOf(address(this));

     |  // @audit-issue Pre-calculate & hardcode instead
 241 |  // Note that address(this).balance has been updated with msg.value,

     |  // @audit-issue Pre-calculate & hardcode instead
 253 |  IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }(

     |  // @audit-issue Pre-calculate & hardcode instead
 260 |  if (address(this).balance != 0) {

     |  // @audit-issue Pre-calculate & hardcode instead
 261 |  msg.sender.sendEther(address(this).balance);

     |  // @audit-issue Pre-calculate & hardcode instead
 268 |  if (tko.balanceOf(address(this)) != tkoBalance + _config.livenessBond) {
```
GitHub: [238](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L238), [241](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L241), [253](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L253), [260](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L260), [261](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L261), [268](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L268)


```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

     |  // @audit-issue Pre-calculate & hardcode instead
 242 |  tko.transferFrom(msg.sender, address(this), tier.contestBond);

     |  // @audit-issue Pre-calculate & hardcode instead
 384 |  _tko.transferFrom(msg.sender, address(this), _tier.validityBond - reward);
```
GitHub: [242](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L242), [384](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L384)


```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

     |  // @audit-issue Pre-calculate & hardcode instead
  61 |  if (_to == address(this)) revert TKO_INVALID_ADDR();

     |  // @audit-issue Pre-calculate & hardcode instead
  79 |  if (_to == address(this)) revert TKO_INVALID_ADDR();
```
GitHub: [61](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L61), [79](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L79)


```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

     |  // @audit-issue Pre-calculate & hardcode instead
  35 |  /// represents calls to address(this).

     |  // @audit-issue Pre-calculate & hardcode instead
  50 |  (bool success,) = address(this).call(txdata);
```
GitHub: [35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L35), [50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L50)


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

     |  // @audit-issue Pre-calculate & hardcode instead
 174 |  _to.sendEther(address(this).balance);

     |  // @audit-issue Pre-calculate & hardcode instead
 176 |  IERC20(_token).safeTransfer(_to, IERC20(_token).balanceOf(address(this)));
```
GitHub: [174](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L174), [176](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L176)


```solidity
File: packages/protocol/contracts/signal/SignalService.sol

     |  // @audit-issue Pre-calculate & hardcode instead
 112 |  signalService = address(this);

     |  // @audit-issue Pre-calculate & hardcode instead
 131 |  if (value == 0 || value != _loadSignalValue(address(this), signal)) {

     |  // @audit-issue Pre-calculate & hardcode instead
 149 |  return _loadSignalValue(address(this), signal) == _chainData;

     |  // @audit-issue Pre-calculate & hardcode instead
 171 |  chainData_ = _loadSignalValue(address(this), signal);

     |  // @audit-issue Pre-calculate & hardcode instead
 245 |  _sendSignal(address(this), signal_, _chainData);
```
GitHub: [112](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L112), [131](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L131), [149](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L149), [171](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L171), [245](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L245)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

     |  // @audit-issue Pre-calculate & hardcode instead
 174 |  if (!ISignalService(signalService).isSignalSent(address(this), msgHash)) {

     |  // @audit-issue Pre-calculate & hardcode instead
 196 |  _storeContext(msgHash, address(this), _message.srcChainId);

     |  // @audit-issue Pre-calculate & hardcode instead
 270 |  _message.to == address(0) || _message.to == address(this)

     |  // @audit-issue Pre-calculate & hardcode instead
 343 |  _app: address(this),

     |  // @audit-issue Pre-calculate & hardcode instead
 486 |  assert(_message.from != address(this));
```
GitHub: [174](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L174), [196](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L196), [270](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L270), [343](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L343), [486](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L486)


```solidity
File: packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

     |  // @audit-issue Pre-calculate & hardcode instead
  48 |  usdc.transferFrom(_from, address(this), _amount);
```
GitHub: [48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L48)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

     |  // @audit-issue Pre-calculate & hardcode instead
 147 |  if (_to == address(this)) revert BTOKEN_CANNOT_RECEIVE();
```
GitHub: [147](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L147)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

     |  // @audit-issue Pre-calculate & hardcode instead
 125 |  if (_to == address(this)) revert BTOKEN_CANNOT_RECEIVE();
```
GitHub: [125](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L125)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

     |  // @audit-issue Pre-calculate & hardcode instead
 137 |  if (_to == address(this)) revert BTOKEN_CANNOT_RECEIVE();
```
GitHub: [137](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L137)


```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

     |  // @audit-issue Pre-calculate & hardcode instead
 108 |  if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

     |  // @audit-issue Pre-calculate & hardcode instead
 226 |  IERC1155(token).safeBatchTransferFrom(address(this), to, tokenIds, amounts, "");

     |  // @audit-issue Pre-calculate & hardcode instead
 272 |  to: address(this),
```
GitHub: [108](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L108), [226](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L226), [272](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L272)


```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

     |  // @audit-issue Pre-calculate & hardcode instead
 267 |  if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

     |  // @audit-issue Pre-calculate & hardcode instead
 378 |  uint256 _balance = t.balanceOf(address(this));

     |  // @audit-issue Pre-calculate & hardcode instead
 379 |  t.safeTransferFrom({ from: msg.sender, to: address(this), value: _amount });

     |  // @audit-issue Pre-calculate & hardcode instead
 380 |  balanceChange_ = t.balanceOf(address(this)) - _balance;
```
GitHub: [267](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L267), [378](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L378), [379](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L379), [380](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L380)


```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

     |  // @audit-issue Pre-calculate & hardcode instead
  91 |  if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

     |  // @audit-issue Pre-calculate & hardcode instead
 171 |  IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);

     |  // @audit-issue Pre-calculate & hardcode instead
 211 |  t.safeTransferFrom(_user, address(this), _op.tokenIds[i]);
```
GitHub: [91](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L91), [171](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L171), [211](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L211)


```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

     |  // @audit-issue Pre-calculate & hardcode instead
 186 |  address(this),
```
GitHub: [186](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L186)


## [G-13] Consider using OpenZeppelin `EnumerateSet` in place of nested mappings

Nested mappings and multi-dimensional arrays in Solidity operate through a process of double hashing, wherein the original storage slot and the first key are concatenated and hashed, and then this hash is again concatenated with the second key and hashed. This process can be quite gas expensive due to the double-hashing operation and subsequent storage operation (sstore).

A possible optimization involves manually concatenating the keys followed by a single hash operation and an sstore. However, this technique introduces the risk of storage collision, especially when there are other nested hash maps in the contract that use the same key types. Because Solidity is unaware of the number and structure of nested hash maps in a contract, it follows a conservative approach in computing the storage slot to avoid possible collisions.

OpenZeppelin's EnumerableSet provides a potential solution to this problem. It creates a data structure that combines the benefits of set operations with the ability to enumerate stored elements, which is not natively available in Solidity. EnumerableSet handles the element uniqueness internally and can therefore provide a more gas-efficient and collision-resistant alternative to nested mappings or multi-dimensional arrays in certain scenarios.

*Instances: 8*

```solidity
File: packages/protocol/contracts/common/AddressManager.sol

     |  // @audit-issue Consider replacing with OZ `EnumerateSet`
  12 |  mapping(uint256 chainId => mapping(bytes32 name => address addr)) private __addresses;
```
GitHub: [12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L12)


```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

     |  // @audit-issue Consider replacing with OZ `EnumerateSet`
  19 |  mapping(uint32 version => mapping(bytes32 hash => uint256 approvalBits)) internal _approvals;
```
GitHub: [19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L19)


```solidity
File: packages/protocol/contracts/L1/TaikoData.sol

     |  // @audit-issue Consider replacing with OZ `EnumerateSet`
 183 |  mapping(uint64 blockId => mapping(bytes32 parentHash => uint32 transitionId)) transitionIds;

     |  // @audit-issue Consider replacing with OZ `EnumerateSet`
 185 |  mapping(
 186 |      uint64 blockId_mod_blockRingBufferSize
 187 |          => mapping(uint32 transitionId => TransitionState ts)
 188 |      ) transitions;
```
GitHub: [183](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L183), [185-188](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L185-L188)


```solidity
File: packages/protocol/contracts/signal/SignalService.sol

     |  // @audit-issue Consider replacing with OZ `EnumerateSet`
  17 |  mapping(uint64 chainId => mapping(bytes32 kind => uint64 blockId)) public topBlockId;
```
GitHub: [17](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L17)


```solidity
File: packages/protocol/contracts/tokenvault/BaseNFTVault.sol

     |  // @audit-issue Consider replacing with OZ `EnumerateSet`
  59 |  mapping(uint256 chainId => mapping(address ctoken => address btoken)) public canonicalToBridged;
```
GitHub: [59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L59)


```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

     |  // @audit-issue Consider replacing with OZ `EnumerateSet`
  49 |  mapping(uint256 chainId => mapping(address ctoken => address btoken)) public canonicalToBridged;
```
GitHub: [49](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L49)


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

     |  // @audit-issue Consider replacing with OZ `EnumerateSet`
  47 |  mapping(uint256 idx => mapping(bytes serialNum => bool revoked)) private _serialNumIsRevoked;
```
GitHub: [47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L47)


## [G-14] Consider using `ERC721A` over `ERC721`

`ERC721A` is an improvement standard for `ERC721` tokens. It was proposed by the Azuki team and used for developing their NFT collection. Compared with `ERC721`, `ERC721A` is a more gas-efficient standard to mint a lot of of NFTs simultaneously. It allows developers to mint multiple NFTs at the same gas price. This has been a great improvement due to Ethereum’s sky-rocketing gas fee. Reference: https://nextrope.com/erc721-vs-erc721a-2/.

*Instances: 2*

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

     |  // @audit-issue Consider switching to ERC721A
   4 |  import "@openzeppelin/contracts/token/ERC721/IERC721.sol";
```
GitHub: [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L4)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

     |  // @audit-issue Consider switching to ERC721A
   4 |  import "@openzeppelin/contracts/token/ERC721/IERC721.sol";
```
GitHub: [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L4)


## [G-15] Constructors can be marked `payable`

Payable functions cost less gas to execute, since the compiler does not have to add extra checks to ensure that a payment wasn't provided. A constructor can safely be marked as payable, since only the deployer would be able to pass funds, and the project itself would not pass any funds.

*Instances: 3*

```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

     |  // @audit-issue Consider marking payable to save gas
  64 |  constructor() {
```
GitHub: [64](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L64)


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

     |  // @audit-issue Consider marking payable to save gas
  54 |  constructor(address sigVerifyLibAddr, address pemCertLibAddr) {
```
GitHub: [54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L54)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

     |  // @audit-issue Consider marking payable to save gas
  20 |  constructor(address es256Verifier) {
```
GitHub: [20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L20)


## [G-16] Declare variables outside loops to save gas

In some cases, it is possible to save gas by declaring variables outside a loop. Careful testing will be necessary to determine if these instances will save gas in this contracts typical usage scenarios.

*Instances: 58*

```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

     |  // @audit-info Context
  86 |  for (uint256 i; i < deposits_.length;) {
     |      // @audit-issue Measure gas with variable declared outside loop
  87 |      uint256 data = _state.ethDeposits[j % _config.ethDepositRingBufferSize];
  :  |
     |      // @audit-issue Measure gas with variable declared outside loop
  93 |      uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount;
```
GitHub: [87](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L87), [93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L93)


```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

     |  // @audit-info Context
 127 |  while (blockId < b.numBlocks && numBlocksVerified < _maxBlocksToVerify) {
  :  |
     |      // @audit-issue Measure gas with variable declared outside loop
 140 |      TaikoData.TransitionState storage ts = _state.transitions[slot][tid];
  :  |
     |      // @audit-issue Measure gas with variable declared outside loop
 178 |      uint256 bondToReturn = uint256(ts.validityBond) + blk.livenessBond;
  :  |
     |      // @audit-issue Measure gas with variable declared outside loop
 188 |      IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));
```
GitHub: [140](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L140), [178](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L178), [188](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L188)


```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

     |  // @audit-info Context
  80 |  for (uint256 i = 0; i < _newGuardians.length; ++i) {
     |      // @audit-issue Measure gas with variable declared outside loop
  81 |      address guardian = _newGuardians[i];
```
GitHub: [81](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L81)


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

     |  // @audit-info Context
 234 |  for (uint256 i; i < 255 && _blockId >= i + 1; ++i) {
     |      // @audit-issue Measure gas with variable declared outside loop
 235 |      uint256 j = _blockId - i - 1;
```
GitHub: [235](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L235)


```solidity
File: packages/protocol/contracts/signal/SignalService.sol

     |  // @audit-info Context
 104 |  for (uint256 i; i < hopProofs.length; ++i) {
  :  |
     |      // @audit-issue Measure gas with variable declared outside loop
 107 |      bytes32 signalRoot = _verifyHopProof(chainId, app, signal, value, hop, signalService);
     |      // @audit-issue Measure gas with variable declared outside loop
 108 |      bool isLastHop = i == hopProofs.length - 1;
  :  |
     |      // @audit-issue Measure gas with variable declared outside loop
 120 |      bool isFullProof = hop.accountProof.length > 0;
  :  |
     |      // @audit-issue Measure gas with variable declared outside loop
 124 |      bytes32 kind = isFullProof ? LibSignals.STATE_ROOT : LibSignals.SIGNAL_ROOT;
```
GitHub: [107](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L107), [108](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L108), [120](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L120), [124](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L124)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

     |  // @audit-info Context
  90 |  for (uint256 i; i < _msgHashes.length; ++i) {
     |      // @audit-issue Measure gas with variable declared outside loop
  91 |      bytes32 msgHash = _msgHashes[i];
```
GitHub: [91](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L91)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

     |  // @audit-info Context
  74 |  while (offset < _in.length) {
     |      // @audit-issue Measure gas with variable declared outside loop
  75 |      (uint256 itemOffset, uint256 itemLength,) = _decodeLength(
  76 |          RLPItem({
  77 |              length: _in.length - offset,
  78 |              ptr: MemoryPointer.wrap(MemoryPointer.unwrap(_in.ptr) + offset)
  79 |          })
  80 |      );
```
GitHub: [75-80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L75-L80)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

     |  // @audit-info Context
  85 |  for (uint256 i = 0; i < proof.length; i++) {
     |      // @audit-issue Measure gas with variable declared outside loop
  86 |      TrieNode memory currentNode = proof[i];
  :  |
     |              // @audit-issue Measure gas with variable declared outside loop
 134 |              uint8 branchKey = uint8(key[currentKeyIndex]);
     |              // @audit-issue Measure gas with variable declared outside loop
 135 |              RLPReader.RLPItem memory nextNode = currentNode.decoded[branchKey];
  :  |
     |          // @audit-issue Measure gas with variable declared outside loop
 140 |          bytes memory path = _getNodePath(currentNode);
     |          // @audit-issue Measure gas with variable declared outside loop
 141 |          uint8 prefix = uint8(path[0]);
     |          // @audit-issue Measure gas with variable declared outside loop
 142 |          uint8 offset = 2 - (prefix % 2);
     |          // @audit-issue Measure gas with variable declared outside loop
 143 |          bytes memory pathRemainder = Bytes.slice(path, offset);
     |          // @audit-issue Measure gas with variable declared outside loop
 144 |          bytes memory keyRemainder = Bytes.slice(key, currentKeyIndex);
     |          // @audit-issue Measure gas with variable declared outside loop
 145 |          uint256 sharedNibbleLength = _getSharedNibbleLength(pathRemainder, keyRemainder);
```
GitHub: [86](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L86), [134](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L134), [135](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L135), [140](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L140), [141](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L141), [142](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L142), [143](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L143), [144](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L144), [145](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L145)


```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

     |  // @audit-info Context
 104 |  for (uint256 i; i < _ids.length; ++i) {
     |      // @audit-issue Measure gas with variable declared outside loop
 105 |      uint256 idx = _ids[i];
```
GitHub: [105](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L105)


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

     |  // @audit-info Context
 191 |  for (uint256 i; i < enclaveId.tcbLevels.length; ++i) {
     |      // @audit-issue Measure gas with variable declared outside loop
 192 |      EnclaveIdStruct.TcbLevel memory tcb = enclaveId.tcbLevels[i];

     |  // @audit-info Context
 214 |  for (uint256 i; i < tcb.tcbLevels.length; ++i) {
     |      // @audit-issue Measure gas with variable declared outside loop
 215 |      TCBInfoStruct.TCBLevelObj memory current = tcb.tcbLevels[i];
     |      // @audit-issue Measure gas with variable declared outside loop
 216 |      bool pceSvnIsHigherOrGreater = pck.sgxExtension.pcesvn >= current.pcesvn;
     |      // @audit-issue Measure gas with variable declared outside loop
 217 |      bool cpuSvnsAreHigherOrGreater = _isCpuSvnHigherOrGreater(
 218 |          pck.sgxExtension.sgxTcbCompSvnArr, current.sgxTcbCompSvnArr
 219 |      );
  :  |
     |          // @audit-issue Measure gas with variable declared outside loop
 222 |          bool tcbIsRevoked = status == TCBInfoStruct.TCBStatus.TCB_REVOKED;

     |  // @audit-info Context
 259 |  for (uint256 i; i < n; ++i) {
     |      // @audit-issue Measure gas with variable declared outside loop
 260 |      IPEMCertChainLib.ECSha256Certificate memory issuer;
  :  |
     |      // @audit-issue Measure gas with variable declared outside loop
 292 |      bytes32 issuerPubKeyHash = keccak256(issuer.pubKey);

     |  // @audit-info Context
 420 |  for (uint256 i; i < 3; ++i) {
     |      // @audit-issue Measure gas with variable declared outside loop
 421 |      bool isPckCert = i == 0; // additional parsing for PCKCert
     |      // @audit-issue Measure gas with variable declared outside loop
 422 |      bool certDecodedSuccessfully;
```
GitHub: [192](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L192), [215](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L215), [216](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L216), [217-219](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L217-L219), [222](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L222), [260](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L260), [292](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L292), [421](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L421), [422](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L422)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

     |  // @audit-info Context
  54 |  for (uint256 i; i < size; ++i) {
     |      // @audit-issue Measure gas with variable declared outside loop
  55 |      string memory input;
  :  |
     |      // @audit-issue Measure gas with variable declared outside loop
  61 |      uint256 increment;

     |  // @audit-info Context
 354 |  for (uint256 i; i < SGX_TCB_CPUSVN_SIZE + 1; ++i) {
     |      // @audit-issue Measure gas with variable declared outside loop
 355 |      uint256 svnPtr = der.firstChildOf(svnParentPtr); // OID
     |      // @audit-issue Measure gas with variable declared outside loop
 356 |      uint256 svnValuePtr = der.nextSiblingOf(svnPtr); // value
     |      // @audit-issue Measure gas with variable declared outside loop
 357 |      bytes memory svnValueBytes = der.bytesAt(svnValuePtr);
     |      // @audit-issue Measure gas with variable declared outside loop
 358 |      uint16 svnValue = svnValueBytes.length < 2
 359 |          ? uint16(bytes2(svnValueBytes)) / 256
 360 |          : uint16(bytes2(svnValueBytes));
  :  |
     |          // @audit-issue Measure gas with variable declared outside loop
 366 |          uint256 cpusvn = uint256(svnValue);

     |  // @audit-info Context
 286 |  while (tbsPtr != 0) {
     |      // @audit-issue Measure gas with variable declared outside loop
 287 |      uint256 internalPtr = der.firstChildOf(tbsPtr);
  :  |
     |          // @audit-issue Measure gas with variable declared outside loop
 295 |          uint256 extnValueParentPtr = der.rootOfOctetStringAt(internalPtr);
     |          // @audit-issue Measure gas with variable declared outside loop
 296 |          uint256 extnValuePtr = der.firstChildOf(extnValueParentPtr);
  :  |
     |          // @audit-issue Measure gas with variable declared outside loop
 299 |          PCKTCBFlags memory flags;
  :  |
     |              // @audit-issue Measure gas with variable declared outside loop
 302 |              uint256 extnValueOidPtr = der.firstChildOf(extnValuePtr);
  :  |
     |                  // @audit-issue Measure gas with variable declared outside loop
 312 |                  uint256 pceidPtr = der.nextSiblingOf(extnValueOidPtr);
  :  |
     |                  // @audit-issue Measure gas with variable declared outside loop
 318 |                  uint256 fmspcPtr = der.nextSiblingOf(extnValueOidPtr);

     |  // @audit-info Context
 301 |  while (!(flags.fmspcFound && flags.pceidFound && flags.tcbFound)) {
     |      // @audit-issue Measure gas with variable declared outside loop
 302 |      uint256 extnValueOidPtr = der.firstChildOf(extnValuePtr);
  :  |
     |          // @audit-issue Measure gas with variable declared outside loop
 312 |          uint256 pceidPtr = der.nextSiblingOf(extnValueOidPtr);
  :  |
     |          // @audit-issue Measure gas with variable declared outside loop
 318 |          uint256 fmspcPtr = der.nextSiblingOf(extnValueOidPtr);
```
GitHub: [55](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L55), [61](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L61), [355](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L355), [356](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L356), [357](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L357), [358-360](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L358-L360), [366](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L366), [287](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L287), [295](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L295), [296](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L296), [299](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L299), [302](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L302), [312](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L312), [318](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L318), [302](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L302), [312](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L312), [318](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L318)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

     |  // @audit-info Context
 153 |  for (uint256 i; i < encoded.length; ++i) {
     |      // @audit-issue Measure gas with variable declared outside loop
 154 |      uint256 digits = uint256(uint8(bytes1(encoded[i])));
     |      // @audit-issue Measure gas with variable declared outside loop
 155 |      uint256 upperDigit = digits / 16;
     |      // @audit-issue Measure gas with variable declared outside loop
 156 |      uint256 lowerDigit = digits % 16;
  :  |
     |      // @audit-issue Measure gas with variable declared outside loop
 158 |      uint256 acc = lowerDigit * (16 ** (2 * i));
```
GitHub: [154](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L154), [155](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L155), [156](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L156), [158](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L158)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

     |  // @audit-info Context
  80 |  for (uint256 idx = 0; idx < shortest; idx += 32) {
     |      // @audit-issue Measure gas with variable declared outside loop
  81 |      uint256 a;
     |      // @audit-issue Measure gas with variable declared outside loop
  82 |      uint256 b;
  :  |
     |          // @audit-issue Measure gas with variable declared outside loop
  89 |          uint256 mask;
  :  |
     |          // @audit-issue Measure gas with variable declared outside loop
  95 |          uint256 diff = (a & mask) - (b & mask);

     |  // @audit-info Context
 333 |  for (uint256 i; i < len; ++i) {
     |      // @audit-issue Measure gas with variable declared outside loop
 334 |      bytes1 char = self[off + i];
```
GitHub: [81](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L81), [82](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L82), [89](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L89), [95](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L95), [334](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L334)


## [G-17] Default bool values are manually reset

Using .delete is better than resetting a Solidity variable to its default value manually because it frees up storage space on the Ethereum blockchain, resulting in gas cost savings.

*Instances: 2*

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

     |  // @audit-issue Consider using delete
 495 |  success_ = false;
```
GitHub: [495](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L495)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

     |  // @audit-issue Consider using delete
 129 |  hasNullParam = false;
```
GitHub: [129](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L129)


## [G-18] Default int values are manually reset

Using .delete is better than resetting a Solidity variable to its default value manually because it frees up storage space on the Ethereum blockchain, resulting in gas cost savings.

*Instances: 10*

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

     |  // @audit-issue Consider using delete
 190 |  meta_.txListByteOffset = 0;
```
GitHub: [190](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L190)


```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

     |  // @audit-issue Consider using delete
 197 |  blk.livenessBond = 0;

     |  // @audit-issue Consider using delete
 300 |  ts_.blockHash = 0;

     |  // @audit-issue Consider using delete
 301 |  ts_.stateRoot = 0;

     |  // @audit-issue Consider using delete
 302 |  ts_.validityBond = 0;

     |  // @audit-issue Consider using delete
 306 |  ts_.tier = 0;

     |  // @audit-issue Consider using delete
 307 |  ts_.contestations = 0;
```
GitHub: [197](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L197), [300](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L300), [301](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L301), [302](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L302), [306](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L306), [307](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L307)


```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

     |  // @audit-issue Consider using delete
 231 |  _grant.grantStart = 0;

     |  // @audit-issue Consider using delete
 232 |  _grant.grantPeriod = 0;
```
GitHub: [231](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L231), [232](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L232)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

     |  // @audit-issue Consider using delete
 336 |  tbsPtr = 0; // exit
```
GitHub: [336](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L336)


## [G-19] Detect zero value transfers to save gas

Detecting and aborting zero value transfers will save at least 100 gas.

*Instances: 18*

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

 102 |  tko.transferFrom(_blk.assignedProver, taikoL1Address, _blk.livenessBond);

 114 |  IERC20(assignment.feeToken).safeTransferFrom(
 115 |      _meta.coinbase, _blk.assignedProver, proverFee
 116 |  );
```
GitHub: [102](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L102), [114-116](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L114-L116)


```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

 196 |  tko.transfer(blk.assignedProver, blk.livenessBond);

 242 |  tko.transferFrom(msg.sender, address(this), tier.contestBond);

 367 |  _tko.transfer(_ts.prover, _ts.validityBond + reward);

 371 |  _tko.transfer(_ts.contester, _ts.contestBond + reward);

 382 |  _tko.transfer(msg.sender, reward - _tier.validityBond);

 384 |  _tko.transferFrom(msg.sender, address(this), _tier.validityBond - reward);
```
GitHub: [196](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L196), [242](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L242), [367](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L367), [371](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L371), [382](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L382), [384](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L384)


```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

 189 |  tko.transfer(ts.prover, bondToReturn);
```
GitHub: [189](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L189)


```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

  62 |  return super.transfer(_to, _amount);

  80 |  return super.transferFrom(_from, _to, _amount);
```
GitHub: [62](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L62), [80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L80)


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

 176 |  IERC20(_token).safeTransfer(_to, IERC20(_token).balanceOf(address(this)));
```
GitHub: [176](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L176)


```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

 330 |  IERC20(token_).safeTransfer(_to, _amount);

 379 |  t.safeTransferFrom({ from: msg.sender, to: address(this), value: _amount });
```
GitHub: [330](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L330), [379](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L379)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

  63 |  IERC20(token).transferFrom(vault, user, amount);
```
GitHub: [63](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L63)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

  91 |  IERC20(token).transferFrom(vault, user, amount);
```
GitHub: [91](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L91)


```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

 219 |  IERC20(taikoToken).transferFrom(sharedVault, _to, amountToWithdraw);

 220 |  IERC20(costToken).safeTransferFrom(_recipient, sharedVault, costToWithdraw);
```
GitHub: [219](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L219), [220](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L220)


## [G-20] Divisions can be `unchecked` to save gas

The expression `type(int).min/(-1)` is the only case where division causes an overflow. Therefore, uncheck can be used to save gas in scenarios where it is certain that such an overflow will not occur.

*Instances: 15*

```solidity
File: packages/protocol/contracts/L1/gov/TaikoGovernor.sol

     |  // @audit-issue Use unchecked to save gas, if possible
 124 |  return 1_000_000_000 ether / 10_000; // 0.01% of Taiko Token
```
GitHub: [124](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L124)


```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

     |  // @audit-issue Use unchecked to save gas, if possible
 262 |  || _config.ethDepositMaxFee > type(uint96).max / _config.ethDepositMaxCountPerBlock
```
GitHub: [262](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L262)


```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

     |  // @audit-issue Use unchecked to save gas, if possible
 215 |  ethDepositMaxFee: 1 ether / 10,
```
GitHub: [215](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L215)


```solidity
File: packages/protocol/contracts/L2/Lib1559Math.sol

     |  // @audit-issue Use unchecked to save gas, if possible
  28 |  return _ethQty(_gasExcess, _adjustmentFactor) / LibFixedPointMath.SCALING_FACTOR
  29 |      / _adjustmentFactor;

     |  // @audit-issue Use unchecked to save gas, if possible
  28 |  return _ethQty(_gasExcess, _adjustmentFactor) / LibFixedPointMath.SCALING_FACTOR

     |  // @audit-issue Use unchecked to save gas, if possible
  41 |  uint256 input = _gasExcess * LibFixedPointMath.SCALING_FACTOR / _adjustmentFactor;
```
GitHub: [28-29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/Lib1559Math.sol#L28-L29), [28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/Lib1559Math.sol#L28), [41](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/Lib1559Math.sol#L41)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

     |  // @audit-issue Use unchecked to save gas, if possible
  39 |  while (_len / i != 0) {

     |  // @audit-issue Use unchecked to save gas, if possible
  47 |  out_[i] = bytes1(uint8((_len / (256 ** (lenLen - i))) % 256));
```
GitHub: [39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L39), [47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L47)


```solidity
File: packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol

     |  // @audit-issue Use unchecked to save gas, if possible
  33 |  x = (x << 78) / 5 ** 18;

     |  // @audit-issue Use unchecked to save gas, if possible
  39 |  int256 k = ((x << 96) / 54_916_777_467_707_473_351_141_471_128 + 2 ** 95) >> 96;
```
GitHub: [33](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L33), [39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L39)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

     |  // @audit-issue Use unchecked to save gas, if possible
 117 |  uint256 timeBasedAllowance = balance
 118 |      * (block.timestamp.min(claimEnd + withdrawalWindow) - claimEnd) / withdrawalWindow;
```
GitHub: [117-118](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L117-L118)


```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

     |  // @audit-issue Use unchecked to save gas, if possible
 197 |  uint128 _amountUnlocked = amountUnlocked / 1e18; // divide first

     |  // @audit-issue Use unchecked to save gas, if possible
 264 |  return _amount * uint64(block.timestamp - _start) / _period;
```
GitHub: [197](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L197), [264](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L264)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

     |  // @audit-issue Use unchecked to save gas, if possible
 359 |  ? uint16(bytes2(svnValueBytes)) / 256
```
GitHub: [359](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L359)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

     |  // @audit-issue Use unchecked to save gas, if possible
 155 |  uint256 upperDigit = digits / 16;
```
GitHub: [155](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L155)


## [G-21] Duplicated `require()`/`revert()` checks should be refactored to a modifier or function to save deployment gas

This will cost more runtime gas, but will reduce deployment gas when the function is (optionally called via a modifier) called more than once as is the case for the examples below. Most projects do not make this trade-off, but it's available nonetheless.

*Instances: 15*

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

     |  // @audit-info Duplicates of this require()/revert() were detected
  37 |  require(
  38 |      _in.length > 0,
  39 |      "RLPReader: length of an RLP item must be greater than zero to be decodable"
  40 |  );
  :  |
     |  // @audit-issue First seen at packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol:37
 152 |  require(
 153 |      _in.length > 0,
 154 |      "RLPReader: length of an RLP item must be greater than zero to be decodable"
 155 |  );
```
GitHub: [152-155](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L152-L155)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

     |  // @audit-info Duplicates of this require()/revert() were detected
 142 |  require(der[ptr.ixs()] == 0x02, "Not type INTEGER");
  :  |
     |  // @audit-issue First seen at packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol:142
 155 |  require(der[ptr.ixs()] == 0x02, "Not type INTEGER");
```
GitHub: [155](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L155)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

     |  // @audit-info Duplicates of this require()/revert() were detected
 143 |  require(der[ptr.ixf()] & 0x80 == 0, "Not positive");
  :  |
     |  // @audit-issue First seen at packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol:143
 156 |  require(der[ptr.ixf()] & 0x80 == 0, "Not positive");
```
GitHub: [156](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L156)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

     |  // @audit-info Duplicates of this require()/revert() were detected
  50 |  revert("Unsupported algorithm");
  :  |
     |  // @audit-issue First seen at packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol:50
  75 |  revert("Unsupported algorithm");
```
GitHub: [75](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L75)


```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

     |  // @audit-info Duplicates of this conditional revert statement were detected
  59 |  if (paused()) revert INVALID_PAUSE_STATUS();

File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol
     |  // @audit-issue First seen at packages/protocol/contracts/common/EssentialContract.sol:59
 138 |  if (paused()) revert INVALID_PAUSE_STATUS();

File: packages/protocol/contracts/tokenvault/BridgedERC20.sol
     |  // @audit-issue First seen at packages/protocol/contracts/common/EssentialContract.sol:59
 148 |  if (paused()) revert INVALID_PAUSE_STATUS();

File: packages/protocol/contracts/tokenvault/BridgedERC721.sol
     |  // @audit-issue First seen at packages/protocol/contracts/common/EssentialContract.sol:59
 126 |  if (paused()) revert INVALID_PAUSE_STATUS();
```
GitHub: [138](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L138), [148](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L148), [126](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L126)


```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

     |  // @audit-info Duplicates of this conditional revert statement were detected
 105 |  if (blk.blockId != blockId) revert L1_BLOCK_MISMATCH();
  :  |
     |          // @audit-issue First seen at packages/protocol/contracts/L1/libs/LibVerifying.sol:105
 131 |          if (blk.blockId != blockId) revert L1_BLOCK_MISMATCH();
```
GitHub: [131](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L131)


```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

     |  // @audit-info Duplicates of this conditional revert statement were detected
  61 |  if (_to == address(this)) revert TKO_INVALID_ADDR();
  :  |
     |  // @audit-issue First seen at packages/protocol/contracts/L1/TaikoToken.sol:61
  79 |  if (_to == address(this)) revert TKO_INVALID_ADDR();
```
GitHub: [79](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L79)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

     |  // @audit-info Duplicates of this conditional revert statement were detected
 166 |  if (messageStatus[msgHash] != Status.NEW) revert B_STATUS_MISMATCH();
  :  |
     |  // @audit-issue First seen at packages/protocol/contracts/bridge/Bridge.sol:166
 227 |  if (messageStatus[msgHash] != Status.NEW) revert B_STATUS_MISMATCH();
```
GitHub: [227](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L227)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

     |  // @audit-info Duplicates of this conditional revert statement were detected
 137 |  if (_to == address(this)) revert BTOKEN_CANNOT_RECEIVE();

File: packages/protocol/contracts/tokenvault/BridgedERC20.sol
     |  // @audit-issue First seen at packages/protocol/contracts/tokenvault/BridgedERC1155.sol:137
 147 |  if (_to == address(this)) revert BTOKEN_CANNOT_RECEIVE();

File: packages/protocol/contracts/tokenvault/BridgedERC721.sol
     |  // @audit-issue First seen at packages/protocol/contracts/tokenvault/BridgedERC1155.sol:137
 125 |  if (_to == address(this)) revert BTOKEN_CANNOT_RECEIVE();
```
GitHub: [147](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L147), [125](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L125)


```solidity
File: packages/protocol/contracts/tokenvault/BaseNFTVault.sol

     |  // @audit-info Duplicates of this conditional revert statement were detected
 149 |  if (_op.token == address(0)) revert VAULT_INVALID_TOKEN();

File: packages/protocol/contracts/tokenvault/ERC20Vault.sol
     |  // @audit-issue First seen at packages/protocol/contracts/tokenvault/BaseNFTVault.sol:149
 215 |  if (_op.token == address(0)) revert VAULT_INVALID_TOKEN();
```
GitHub: [215](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L215)


```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

     |  // @audit-info Duplicates of this conditional revert statement were detected
 108 |  if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

File: packages/protocol/contracts/tokenvault/ERC20Vault.sol
     |  // @audit-issue First seen at packages/protocol/contracts/tokenvault/ERC1155Vault.sol:108
 267 |  if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

File: packages/protocol/contracts/tokenvault/ERC721Vault.sol
     |  // @audit-issue First seen at packages/protocol/contracts/tokenvault/ERC1155Vault.sol:108
  91 |  if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();
```
GitHub: [267](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L267), [91](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L91)


## [G-22] Emitting constants wastes gas

Every event parameter costs `Glogdata` (**8 gas**) per byte. You can avoid this extra cost, in cases where you're emitting a constant, by creating a new version of the event which doesn't have the parameter (and have users look to the contract's variables for its value instead). Alternatively, in the case of boolean constants, two events can be created - one representing the `true` case and one representing the `false` case.

*Instances: 5*

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

 230 |  emit TransitionProved({
 231 |      blockId: blk.blockId,
 232 |      tran: _tran,
 233 |      prover: msg.sender,
 234 |      validityBond: 0,
 235 |      tier: _proof.tier
 236 |  });
```
GitHub: [230-236](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L230-L236)


```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

  73 |  emit BlockVerified({
  74 |      blockId: 0,
  75 |      assignedProver: address(0),
  76 |      prover: address(0),
  77 |      blockHash: _genesisBlockHash,
  78 |      stateRoot: 0,
  79 |      tier: 0,
  80 |      contestations: 0
  81 |  });
```
GitHub: [73-81](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L73-L81)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 210 |  emit MessageReceived(msgHash, _message, true);

 303 |  emit MessageReceived(msgHash, _message, false);
```
GitHub: [210](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L210), [303](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L303)


```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

 220 |  emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);
```
GitHub: [220](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220)


## [G-23] Enable IR-based code generation

By using `--via-ir` or `{"viaIR": true}`, the compiler is able to use more advanced [multi-function optimizations](https://docs.soliditylang.org/en/v0.8.17/ir-breaking-changes.html#solidity-ir-based-codegen-changes), for extra gas savings.

> 🔴 IR-based code generation was not observed to be enabled in the configuration.


*Instances: 81*

```solidity
File: packages/protocol/contracts/common/IAddressManager.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/IAddressManager.sol#L1)


```solidity
File: packages/protocol/contracts/common/AddressManager.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L1)


```solidity
File: packages/protocol/contracts/common/IAddressResolver.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/IAddressResolver.sol#L1)


```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L1)


```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L1)


```solidity
File: packages/protocol/contracts/libs/Lib4844.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/Lib4844.sol#L1)


```solidity
File: packages/protocol/contracts/libs/LibAddress.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L1)


```solidity
File: packages/protocol/contracts/libs/LibMath.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibMath.sol#L1)


```solidity
File: packages/protocol/contracts/libs/LibTrieProof.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibTrieProof.sol#L1)


```solidity
File: packages/protocol/contracts/L1/gov/TaikoGovernor.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L1)


```solidity
File: packages/protocol/contracts/L1/gov/TaikoTimelockController.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L1)


```solidity
File: packages/protocol/contracts/L1/hooks/IHook.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/IHook.sol#L1)


```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L1)


```solidity
File: packages/protocol/contracts/L1/ITaikoL1.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/ITaikoL1.sol#L1)


```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L1)


```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L1)


```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L1)


```solidity
File: packages/protocol/contracts/L1/libs/LibUtils.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L1)


```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L1)


```solidity
File: packages/protocol/contracts/L1/provers/GuardianProver.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/GuardianProver.sol#L1)


```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L1)


```solidity
File: packages/protocol/contracts/L1/TaikoData.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L1)


```solidity
File: packages/protocol/contracts/L1/TaikoErrors.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L1)


```solidity
File: packages/protocol/contracts/L1/TaikoEvents.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoEvents.sol#L1)


```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L1)


```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L1)


```solidity
File: packages/protocol/contracts/L1/tiers/ITierProvider.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L1)


```solidity
File: packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L1)


```solidity
File: packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L1)


```solidity
File: packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L1)


```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L1)


```solidity
File: packages/protocol/contracts/L2/Lib1559Math.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/Lib1559Math.sol#L1)


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L1)


```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L1)


```solidity
File: packages/protocol/contracts/signal/ISignalService.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/ISignalService.sol#L1)


```solidity
File: packages/protocol/contracts/signal/LibSignals.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/LibSignals.sol#L1)


```solidity
File: packages/protocol/contracts/signal/SignalService.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L1)


```solidity
File: packages/protocol/contracts/bridge/IBridge.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/IBridge.sol#L1)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L1)


```solidity
File: packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L1)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L1)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L1)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L1)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L1)


```solidity
File: packages/protocol/contracts/tokenvault/BaseNFTVault.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L1)


```solidity
File: packages/protocol/contracts/tokenvault/BaseVault.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L1)


```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L1)


```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L1)


```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L1)


```solidity
File: packages/protocol/contracts/tokenvault/IBridgedERC20.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/IBridgedERC20.sol#L1)


```solidity
File: packages/protocol/contracts/tokenvault/LibBridgedToken.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L1)


```solidity
File: packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT OR Apache-2.0
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L1)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/Bytes.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L1)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L1)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L1)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L1)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L1)


```solidity
File: packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L1)


```solidity
File: packages/protocol/contracts/verifiers/IVerifier.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/IVerifier.sol#L1)


```solidity
File: packages/protocol/contracts/verifiers/GuardianVerifier.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L1)


```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L1)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L1)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L1)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L1)


```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L1)


```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L1)


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  //SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L1)


```solidity
File: packages/protocol/contracts/automata-attestation/interfaces/IAttestation.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  //SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/interfaces/IAttestation.sol#L1)


```solidity
File: packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  //SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L1)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/EnclaveIdStruct.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  //SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/EnclaveIdStruct.sol#L1)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L1)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L1)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  //SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L1)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  //SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L1)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  //SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol#L1)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L1)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: BSD 2-Clause License
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L1)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: GPL-3.0
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L1)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/SHA1.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: BSD 2-Clause License
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SHA1.sol#L1)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: GPL-3.0
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L1)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

     |  // @audit-issue Enable viaIR for this file
   1 |  // SPDX-License-Identifier: MIT
```
GitHub: [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L1)


## [G-24] Events should be emitted outside of loops

Emitting an event has an overhead of **375 gas**, which will be incurred on every iteration of the loop. It is cheaper to `emit` only [once](https://github.com/ethereum/EIPs/blob/adad5968fd6de29902174e0cb51c8fc3dceb9ab5/EIPS/eip-1155.md?plain=1#L68) after the loop has finished.

*Instances: 3*

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

     |  // @audit-info Contains emits
  90 |  for (uint256 i; i < _msgHashes.length; ++i) {
  :  |
     |      // @audit-issue Save gas by emitting this outside the loop
  93 |      emit MessageSuspended(msgHash, _suspend);
```
GitHub: [93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L93)


```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

     |  // @audit-info Contains emits
 104 |  for (uint256 i; i < _ids.length; ++i) {
  :  |
     |      // @audit-issue Save gas by emitting this outside the loop
 109 |      emit InstanceDeleted(idx, instances[idx].addr);

     |  // @audit-info Contains emits
 210 |  for (uint256 i; i < _instances.length; ++i) {
  :  |
     |      // @audit-issue Save gas by emitting this outside the loop
 220 |      emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);
```
GitHub: [109](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L109), [220](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220)


## [G-25] Function names can be optimized to save gas

Function that are `public`/`external` and `public` state variable names can be optimized to save gas.

Method IDs that have two leading zero bytes can save **128 gas** each during deployment, and renaming functions to have lower method IDs will save **22 gas** per call, per sorted position shifted. [Reference](https://blog.emn178.cc/en/post/solidity-gas-optimization-function-name/).

You can use the [Function Name Optimizer Tool](https://emn178.github.io/solidity-optimize-name/) to find new function names.

*Instances: 40*

```solidity
File: packages/protocol/contracts/common/AddressManager.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0x19ab453c: init()
     |  // 0xd8f4648f: setAddress()
     |  // 0x28f713cc: getAddress()
  10 |  contract AddressManager is EssentialContract, IAddressManager {
```
GitHub: [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L10)


```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0xa86f9d9e: resolve()
     |  // 0x3eb6b8cf: resolve()
  11 |  abstract contract AddressResolver is IAddressResolver, Initializable {
```
GitHub: [11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L11)


```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0x8456cb59: pause()
     |  // 0x3f4ba83a: unpause()
     |  // 0x5c975abb: paused()
  10 |  abstract contract EssentialContract is UUPSUpgradeable, Ownable2StepUpgradeable, AddressResolver {
```
GitHub: [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L10)


```solidity
File: packages/protocol/contracts/L1/gov/TaikoGovernor.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0x184b9559: init()
     |  // 0x7d5e81e2: propose()
     |  // 0xda95691a: propose()
     |  // 0x01ffc9a7: supportsInterface()
     |  // 0x3e4f49e6: state()
     |  // 0x3932abb1: votingDelay()
     |  // 0x02a251a3: votingPeriod()
     |  // 0xb58131b0: proposalThreshold()
  16 |  contract TaikoGovernor is
```
GitHub: [16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L16)


```solidity
File: packages/protocol/contracts/L1/gov/TaikoTimelockController.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0x399ae724: init()
     |  // 0xf27a0c92: getMinDelay()
   9 |  contract TaikoTimelockController is EssentialContract, TimelockControllerUpgradeable {
```
GitHub: [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L9)


```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0xf09a4016: init()
     |  // 0x4a697ba4: onBlockProposed()
     |  // 0xbab50685: hashAssignment()
  14 |  contract AssignmentHook is EssentialContract, IHook {
```
GitHub: [14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L14)


```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0xc69ee7c0: pauseProving()
  16 |  library LibProving {
```
GitHub: [16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L16)


```solidity
File: packages/protocol/contracts/L1/libs/LibUtils.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0x2c1023fc: getTransition()
     |  // 0xb2cba4a7: getBlock()
   9 |  library LibUtils {
```
GitHub: [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L9)


```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0x8b2fbcb4: init()
  16 |  library LibVerifying {
```
GitHub: [16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L16)


```solidity
File: packages/protocol/contracts/L1/provers/GuardianProver.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0xf09a4016: init()
     |  // 0x492d2474: approve()
  10 |  contract GuardianProver is Guardians {
```
GitHub: [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/GuardianProver.sol#L10)


```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0xe94e9e99: setGuardians()
     |  // 0x48aefc32: isApproved()
     |  // 0xd13cbca3: numGuardians()
   9 |  abstract contract Guardians is EssentialContract {
```
GitHub: [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L9)


```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0x347258aa: init()
     |  // 0xef16e845: proposeBlock()
     |  // 0x10d008bd: proveBlock()
     |  // 0x8778209d: verifyBlocks()
     |  // 0xff00c391: pauseProving()
     |  // 0x047a289d: depositEtherToL2()
     |  // 0x3f4ba83a: unpause()
     |  // 0xcf151d9a: canDepositEthToL2()
     |  // 0xb67d7638: isBlobReusable()
     |  // 0x5fa15e79: getBlock()
     |  // 0xfd257e29: getTransition()
     |  // 0xdde89cf5: getStateVariables()
     |  // 0xc3f909d4: getConfig()
  22 |  contract TaikoL1 is EssentialContract, ITaikoL1, TaikoEvents, TaikoErrors {
```
GitHub: [22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L22)


```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0xef2423fa: init()
     |  // 0x9dc29fac: burn()
     |  // 0x9711715a: snapshot()
     |  // 0xa9059cbb: transfer()
     |  // 0x23b872dd: transferFrom()
  15 |  contract TaikoToken is EssentialContract, ERC20SnapshotUpgradeable, ERC20VotesUpgradeable {
```
GitHub: [15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L15)


```solidity
File: packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0x19ab453c: init()
     |  // 0x576c3de7: getTier()
     |  // 0xd8cde1c6: getTierIds()
     |  // 0x59ab4e23: getMinTier()
  10 |  contract DevnetTierProvider is EssentialContract, ITierProvider {
```
GitHub: [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L10)


```solidity
File: packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0x19ab453c: init()
     |  // 0x576c3de7: getTier()
     |  // 0xd8cde1c6: getTierIds()
     |  // 0x59ab4e23: getMinTier()
  10 |  contract MainnetTierProvider is EssentialContract, ITierProvider {
```
GitHub: [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L10)


```solidity
File: packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0x19ab453c: init()
     |  // 0x576c3de7: getTier()
     |  // 0xd8cde1c6: getTierIds()
     |  // 0x59ab4e23: getMinTier()
  10 |  contract TestnetTierProvider is EssentialContract, ITierProvider {
```
GitHub: [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L10)


```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0x7f07c947: onMessageInvocation()
  14 |  abstract contract CrossChainOwned is EssentialContract, IMessageInvocable {
```
GitHub: [14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L14)


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0x5950f9f1: init()
     |  // 0xda69d3db: anchor()
     |  // 0xf940e385: withdraw()
     |  // 0xa7e022d1: getBasefee()
     |  // 0x23ac7136: getBlockHash()
     |  // 0xc3f909d4: getConfig()
     |  // 0x2f980473: skipFeeCheck()
  21 |  contract TaikoL2 is CrossChainOwned {
```
GitHub: [21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L21)


```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0xc3f909d4: getConfig()
   9 |  contract TaikoL2EIP1559Configurable is TaikoL2 {
```
GitHub: [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L9)


```solidity
File: packages/protocol/contracts/signal/SignalService.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0xf09a4016: init()
     |  // 0x2d1fb389: authorize()
     |  // 0x66ca2bc0: sendSignal()
     |  // 0x4f90a674: syncChainData()
     |  // 0x910af6ed: proveSignalReceived()
     |  // 0x3ced0e08: isChainDataSynced()
     |  // 0x32676bc6: isSignalSent()
     |  // 0xdfc8ff1d: getSyncedChainData()
     |  // 0x9b527cfa: signalForChainData()
     |  // 0x91f3f74b: getSignalSlot()
  14 |  contract SignalService is EssentialContract, ISignalService {
```
GitHub: [14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L14)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0xf09a4016: init()
     |  // 0x48548f25: suspendMessages()
     |  // 0x57209f48: banAddress()
     |  // 0x6c334e2e: sendMessage()
     |  // 0xd6ba38b2: recallMessage()
     |  // 0x16b205c1: processMessage()
     |  // 0xb916a0be: retryMessage()
     |  // 0x9939a2dc: isMessageSent()
     |  // 0x324c058e: proveMessageFailed()
     |  // 0x6be4eb55: proveMessageReceived()
     |  // 0x8e3881a9: isDestChainEnabled()
     |  // 0xd0496d6a: context()
     |  // 0x7844845b: getInvocationDelays()
     |  // 0x302ac399: hashMessage()
     |  // 0xd1aaa5df: signalForFailedMessage()
  16 |  contract Bridge is EssentialContract, IBridge {
```
GitHub: [16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L16)


```solidity
File: packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0x184b9559: init()
  28 |  contract USDCAdapter is BridgedERC20Base {
```
GitHub: [28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L28)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0xbb86ef93: init()
     |  // 0x2e74eb2d: setSnapshoter()
     |  // 0x9711715a: snapshot()
     |  // 0x06fdde03: name()
     |  // 0x95d89b41: symbol()
     |  // 0x313ce567: decimals()
     |  // 0x26afaadd: canonical()
  15 |  contract BridgedERC20 is
```
GitHub: [15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L15)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0xb8f2e0c5: changeMigrationStatus()
     |  // 0x40c10f19: mint()
     |  // 0x9dc29fac: burn()
     |  // 0x8da5cb5b: owner()
   9 |  abstract contract BridgedERC20Base is EssentialContract, IBridgedERC20 {
```
GitHub: [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L9)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0xef8c4ae6: init()
     |  // 0x40c10f19: mint()
     |  // 0x9dc29fac: burn()
     |  // 0x06fdde03: name()
     |  // 0x95d89b41: symbol()
     |  // 0x67e828bf: source()
     |  // 0xc87b56dd: tokenURI()
  12 |  contract BridgedERC721 is EssentialContract, ERC721Upgradeable {
```
GitHub: [12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L12)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0xef8c4ae6: init()
     |  // 0x156e29f6: mint()
     |  // 0xd81d0a15: mintBatch()
     |  // 0xf5298aca: burn()
     |  // 0x06fdde03: name()
     |  // 0x95d89b41: symbol()
  14 |  contract BridgedERC1155 is EssentialContract, IERC1155MetadataURIUpgradeable, ERC1155Upgradeable {
```
GitHub: [14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L14)


```solidity
File: packages/protocol/contracts/tokenvault/BaseVault.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0xf09a4016: init()
     |  // 0x01ffc9a7: supportsInterface()
  12 |  abstract contract BaseVault is
```
GitHub: [12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L12)


```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0x1507cc47: sendToken()
     |  // 0x7f07c947: onMessageInvocation()
     |  // 0x3c6f5de2: onMessageRecalled()
     |  // 0xbc197c81: onERC1155BatchReceived()
     |  // 0xf23a6e61: onERC1155Received()
     |  // 0x01ffc9a7: supportsInterface()
     |  // 0x06fdde03: name()
  29 |  contract ERC1155Vault is BaseNFTVault, ERC1155ReceiverUpgradeable {
```
GitHub: [29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L29)


```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0x0ecd8be9: changeBridgedToken()
     |  // 0xfa233d0c: sendToken()
     |  // 0x7f07c947: onMessageInvocation()
     |  // 0x3c6f5de2: onMessageRecalled()
     |  // 0x06fdde03: name()
  18 |  contract ERC20Vault is BaseVault {
```
GitHub: [18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L18)


```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0x1507cc47: sendToken()
     |  // 0x7f07c947: onMessageInvocation()
     |  // 0x3c6f5de2: onMessageRecalled()
     |  // 0x150b7a02: onERC721Received()
     |  // 0x06fdde03: name()
  16 |  contract ERC721Vault is BaseNFTVault, IERC721Receiver {
```
GitHub: [16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L16)


```solidity
File: packages/protocol/contracts/verifiers/GuardianVerifier.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0xf09a4016: init()
     |  // 0x21e89968: verifyProof()
  10 |  contract GuardianVerifier is EssentialContract, IVerifier {
```
GitHub: [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L10)


```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0xf09a4016: init()
     |  // 0x16107290: addInstances()
     |  // 0x4ef36a56: deleteInstances()
     |  // 0xa91951a2: registerInstance()
     |  // 0x21e89968: verifyProof()
     |  // 0x01763903: getSignedHash()
  19 |  contract SgxVerifier is EssentialContract, IVerifier {
```
GitHub: [19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L19)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0xaed956d6: init()
     |  // 0x1690cbd2: claimAndDelegate()
  11 |  contract ERC20Airdrop is MerkleClaimable {
```
GitHub: [11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L11)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0xf087dd97: init()
     |  // 0x3d13f874: claim()
     |  // 0x51cff8d9: withdraw()
     |  // 0xf8b2cb4f: getBalance()
  12 |  contract ERC20Airdrop2 is MerkleClaimable {
```
GitHub: [12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L12)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0xaed956d6: init()
     |  // 0x4d0698eb: claim()
   9 |  contract ERC721Airdrop is MerkleClaimable {
```
GitHub: [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L9)


```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0xd03e9b36: setConfig()
  10 |  abstract contract MerkleClaimable is EssentialContract {
```
GitHub: [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L10)


```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0x06552ff3: init()
     |  // 0x4478f8fd: grant()
     |  // 0xddc99477: void()
     |  // 0x3ccfd60b: withdraw()
     |  // 0x4bb78b14: withdraw()
     |  // 0xdefff842: getMyGrantSummary()
     |  // 0xcddcb2b5: getMyGrant()
  25 |  contract TimelockTokenPool is EssentialContract {
```
GitHub: [25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L25)


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0xe2e28294: setMrSigner()
     |  // 0x3a343014: setMrEnclave()
     |  // 0x610de480: addRevokedCertSerialNum()
     |  // 0x1f3be096: removeRevokedCertSerialNum()
     |  // 0x4bc7eea4: configureTcbInfoJson()
     |  // 0x123ac29e: configureQeIdentityJson()
     |  // 0x83801580: toggleLocalReportCheck()
     |  // 0x769d87e7: verifyAttestation()
     |  // 0x089a168f: verifyParsedQuote()
  22 |  contract AutomataDcapV3Attestation is IAttestation {
```
GitHub: [22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L22)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0xb6e656fa: splitCertificateChain()
     |  // 0xc1c1d5c1: decodeCert()
  12 |  contract PEMCertChainLib is IPEMCertChainLib {
```
GitHub: [12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L12)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

     |  // @audit-issue Can be optimized to two leading zeros:
     |  // 0x973c7f15: verifyAttStmtSignature()
     |  // 0x848f4caf: verifyCertificateSignature()
     |  // 0x8c8f6b6e: verifyRS256Signature()
     |  // 0x66843c4b: verifyRS1Signature()
     |  // 0x9a657054: verifyES256Signature()
  15 |  contract SigVerifyLib is ISigVerifyLib {
```
GitHub: [15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L15)


## [G-26] Function result should be cached

The instances below show multiple calls to a single function within the same function.

*Instances: 4*

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

     |  // @audit-info Contains multiple external contract reads
  68 |  function proposeBlock(
  69 |      TaikoData.State storage _state,
  70 |      TaikoData.Config memory _config,
  71 |      IAddressResolver _resolver,
  72 |      bytes calldata _data,
  73 |      bytes calldata _txList
  74 |  )
  75 |      internal
  76 |      returns (TaikoData.BlockMetadata memory meta_, TaikoData.EthDeposit[] memory deposits_)
  :  |
     |          // @audit-issue Cache this value
 238 |          uint256 tkoBalance = tko.balanceOf(address(this));
  :  |
     |          // @audit-issue Cache this value
 268 |          if (tko.balanceOf(address(this)) != tkoBalance + _config.livenessBond) {
```
GitHub: [238](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L238), [268](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L268)


```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

     |  // @audit-info Contains multiple external contract reads
 348 |  function _handleMessage(
 349 |      address _user,
 350 |      address _token,
 351 |      address _to,
 352 |      uint256 _amount
 353 |  )
 354 |      private
 355 |      returns (bytes memory msgData_, CanonicalERC20 memory ctoken_, uint256 balanceChange_)
  :  |
     |          // @audit-issue Cache this value
 378 |          uint256 _balance = t.balanceOf(address(this));
  :  |
     |          // @audit-issue Cache this value
 380 |          balanceChange_ = t.balanceOf(address(this)) - _balance;
```
GitHub: [378](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L378), [380](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L380)


## [G-27] Inline `internal` functions that are only called once

Saves 20-40 gas per instance. See https://blog.soliditylang.org/2021/03/02/saving-gas-with-simple-inliner/ for more details.

*Instances: 27*

```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

     |  // @audit-issue Inline this function, it's only used once
 109 |  function __Essential_init(address _owner) internal virtual {
```
GitHub: [109](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L109)


```solidity
File: packages/protocol/contracts/libs/LibAddress.sol

     |  // @audit-issue Inline this function, it's only used once
  22 |  function sendEther(address _to, uint256 _amount, uint256 _gasLimit) internal {
```
GitHub: [22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L22)


```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

     |  // @audit-issue Inline this function, it's only used once
 122 |  function canDepositEthToL2(
 123 |      TaikoData.State storage _state,
 124 |      TaikoData.Config memory _config,
 125 |      uint256 _amount
 126 |  )
 127 |      internal
 128 |      view
 129 |      returns (bool)
```
GitHub: [122-130](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L122-L130)


```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

     |  // @audit-issue Inline this function, it's only used once
 287 |  function isBlobReusable(
 288 |      TaikoData.State storage _state,
 289 |      TaikoData.Config memory _config,
 290 |      bytes32 _blobHash
 291 |  )
 292 |      internal
 293 |      view
 294 |      returns (bool)
```
GitHub: [287-295](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L287-L295)


```solidity
File: packages/protocol/contracts/L1/libs/LibUtils.sol

     |  // @audit-issue Inline this function, it's only used once
  70 |  function getTransitionId(
  71 |      TaikoData.State storage _state,
  72 |      TaikoData.Block storage _blk,
  73 |      uint64 _slot,
  74 |      bytes32 _parentHash
  75 |  )
  76 |      internal
  77 |      view
  78 |      returns (uint32 tid_)
```
GitHub: [70-79](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L70-L79)


```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

     |  // @audit-issue Inline this function, it's only used once
 220 |  function _authorizePause(address)
 221 |      internal
 222 |      view
 223 |      virtual
 224 |      override
 225 |      onlyFromOwnerOrNamed("chain_pauser")
 226 |  { }
```
GitHub: [220-226](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L220-L226)


```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

     |  // @audit-issue Inline this function, it's only used once
 105 |  function _mint(
 106 |      address _to,
 107 |      uint256 _amount
 108 |  )
 109 |      internal
 110 |      override(ERC20Upgradeable, ERC20VotesUpgradeable)

     |  // @audit-issue Inline this function, it's only used once
 115 |  function _burn(
 116 |      address _from,
 117 |      uint256 _amount
 118 |  )
 119 |      internal
 120 |      override(ERC20Upgradeable, ERC20VotesUpgradeable)
```
GitHub: [105-111](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L105-L111), [115-121](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L115-L121)


```solidity
File: packages/protocol/contracts/signal/SignalService.sol

     |  // @audit-issue Inline this function, it's only used once
 206 |  function _verifyHopProof(
 207 |      uint64 _chainId,
 208 |      address _app,
 209 |      bytes32 _signal,
 210 |      bytes32 _value,
 211 |      HopProof memory _hop,
 212 |      address _signalService
 213 |  )
 214 |      internal
 215 |      virtual
 216 |      validSender(_app)
 217 |      nonZeroValue(_signal)
 218 |      nonZeroValue(_value)
 219 |      returns (bytes32)
```
GitHub: [206-220](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L206-L220)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

     |  // @audit-issue Inline this function, it's only used once
 163 |  function _mint(
 164 |      address _to,
 165 |      uint256 _amount
 166 |  )
 167 |      internal
 168 |      override(ERC20Upgradeable, ERC20VotesUpgradeable)

     |  // @audit-issue Inline this function, it's only used once
 173 |  function _burn(
 174 |      address _from,
 175 |      uint256 _amount
 176 |  )
 177 |      internal
 178 |      override(ERC20Upgradeable, ERC20VotesUpgradeable)
```
GitHub: [163-169](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L163-L169), [173-179](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L173-L179)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

     |  // @audit-issue Inline this function, it's only used once
  97 |  function _mintToken(address _account, uint256 _amount) internal virtual;

     |  // @audit-issue Inline this function, it's only used once
  99 |  function _burnToken(address _from, uint256 _amount) internal virtual;
```
GitHub: [97](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L97), [99](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L99)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/Bytes.sol

     |  // @audit-issue Inline this function, it's only used once
  15 |  function slice(
  16 |      bytes memory _bytes,
  17 |      uint256 _start,
  18 |      uint256 _length
  19 |  )
  20 |      internal
  21 |      pure
  22 |      returns (bytes memory)
```
GitHub: [15-23](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L15-L23)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

     |  // @audit-issue Inline this function, it's only used once
  53 |  function readList(RLPItem memory _in) internal pure returns (RLPItem[] memory out_) {

     |  // @audit-issue Inline this function, it's only used once
 109 |  function readBytes(RLPItem memory _in) internal pure returns (bytes memory out_) {
```
GitHub: [53](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L53), [109](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L109)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

     |  // @audit-issue Inline this function, it's only used once
  13 |  function writeBytes(bytes memory _in) internal pure returns (bytes memory out_) {
```
GitHub: [13](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L13)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

     |  // @audit-issue Inline this function, it's only used once
  68 |  function get(
  69 |      bytes memory _key,
  70 |      bytes[] memory _proof,
  71 |      bytes32 _root
  72 |  )
  73 |      internal
  74 |      pure
  75 |      returns (bytes memory value_)
```
GitHub: [68-76](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L68-L76)


```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

     |  // @audit-issue Inline this function, it's only used once
  77 |  function _verifyMerkleProof(
  78 |      bytes32[] calldata _proof,
  79 |      bytes32 _merkleRoot,
  80 |      bytes32 _value
  81 |  )
  82 |      internal
  83 |      pure
  84 |      virtual
  85 |      returns (bool)
```
GitHub: [77-86](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L77-L86)


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

     |  // @audit-issue Inline this function, it's only used once
 126 |  function _attestationTcbIsValid(TCBInfoStruct.TCBStatus status)
 127 |      internal
 128 |      pure
 129 |      virtual
 130 |      returns (bool valid)
```
GitHub: [126-131](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L126-L131)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

     |  // @audit-issue Inline this function, it's only used once
 244 |  function packQEReport(V3Struct.EnclaveReport memory enclaveReport)
 245 |      internal
 246 |      pure
 247 |      returns (bytes memory packedQEReport)

     |  // @audit-issue Inline this function, it's only used once
 267 |  function parseCerificationChainBytes(
 268 |      bytes memory certBytes,
 269 |      address pemCertLibAddr
 270 |  )
 271 |      internal
 272 |      pure
 273 |      returns (bytes[3] memory certChainData)
```
GitHub: [244-248](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L244-L248), [267-274](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L267-L274)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

     |  // @audit-issue Inline this function, it's only used once
  29 |  function getPtr(uint256 _ixs, uint256 _ixf, uint256 _ixl) internal pure returns (uint256) {
```
GitHub: [29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L29)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

     |  // @audit-issue Inline this function, it's only used once
  56 |  function compare(
  57 |      bytes memory self,
  58 |      uint256 offset,
  59 |      uint256 len,
  60 |      bytes memory other,
  61 |      uint256 otheroffset,
  62 |      uint256 otherlen
  63 |  )
  64 |      internal
  65 |      pure
  66 |      returns (int256)
```
GitHub: [56-67](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L56-L67)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

     |  // @audit-issue Inline this function, it's only used once
  43 |  function pkcs1Sha256(
  44 |      bytes32 _sha256,
  45 |      bytes memory _s,
  46 |      bytes memory _e,
  47 |      bytes memory _m
  48 |  )
  49 |      internal
  50 |      view
  51 |      returns (bool)

     |  // @audit-issue Inline this function, it's only used once
 212 |  function pkcs1Sha1(
 213 |      bytes20 _sha1,
 214 |      bytes memory _s,
 215 |      bytes memory _e,
 216 |      bytes memory _m
 217 |  )
 218 |      internal
 219 |      view
 220 |      returns (bool)
```
GitHub: [43-52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L43-L52), [212-221](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L212-L221)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

     |  // @audit-issue Inline this function, it's only used once
  34 |  function toUnixTimestamp(
  35 |      uint16 year,
  36 |      uint8 month,
  37 |      uint8 day,
  38 |      uint8 hour,
  39 |      uint8 minute,
  40 |      uint8 second
  41 |  )
  42 |      internal
  43 |      pure
  44 |      returns (uint256)
```
GitHub: [34-45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L34-L45)


## [G-28] Inline `modifier`s that are only used once, to save gas

Inline `modifier`s that are only used once, to save gas.

*Instances: 61*

```solidity
File: packages/protocol/contracts/common/AddressManager.sol

     |  // @audit-info Contains redundant modifiers
  10 |  contract AddressManager is EssentialContract, IAddressManager {
  :  |
     |      // @audit-issue This is the only invocation of this modifier
  30 |      function init(address _owner) external initializer {
  :  |
     |          // @audit-issue This is the only invocation of this modifier
  45 |          onlyOwner
```
GitHub: [30](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L30), [45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L45)


```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

     |  // @audit-info Contains redundant modifiers
  11 |  abstract contract AddressResolver is IAddressResolver, Initializable {
  :  |
     |      // @audit-issue This is the only invocation of this modifier
  58 |      function __AddressResolver_init(address _addressManager) internal virtual onlyInitializing {
```
GitHub: [58](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L58)


```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

     |  // @audit-info Contains redundant modifiers
  10 |  abstract contract EssentialContract is UUPSUpgradeable, Ownable2StepUpgradeable, AddressResolver {
  :  |
     |      // @audit-issue This is the only invocation of this modifier
  69 |      function pause() public virtual whenNotPaused {
  :  |
     |      // @audit-issue This is the only invocation of this modifier
  78 |      function unpause() public virtual whenPaused {
  :  |
     |          // @audit-issue This is the only invocation of this modifier
 101 |          onlyInitializing
```
GitHub: [69](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L69), [78](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L78), [101](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L101)


```solidity
File: packages/protocol/contracts/L1/gov/TaikoGovernor.sol

     |  // @audit-info Contains redundant modifiers
  16 |  contract TaikoGovernor is
  :  |
     |          // @audit-issue This is the only invocation of this modifier
  37 |          initializer
```
GitHub: [37](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L37)


```solidity
File: packages/protocol/contracts/L1/gov/TaikoTimelockController.sol

     |  // @audit-info Contains redundant modifiers
   9 |  contract TaikoTimelockController is EssentialContract, TimelockControllerUpgradeable {
  :  |
     |      // @audit-issue This is the only invocation of this modifier
  15 |      function init(address _owner, uint256 _minDelay) external initializer {
```
GitHub: [15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L15)


```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

     |  // @audit-info Contains redundant modifiers
  14 |  contract AssignmentHook is EssentialContract, IHook {
  :  |
     |      // @audit-issue This is the only invocation of this modifier
  57 |      function init(address _owner, address _addressManager) external initializer {
  :  |
     |          // @audit-issue This is the only invocation of this modifier
  69 |          nonReentrant
     |          // @audit-issue This is the only invocation of this modifier
  70 |          onlyFromNamed("taiko")
```
GitHub: [57](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L57), [69](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L69), [70](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L70)


```solidity
File: packages/protocol/contracts/L1/provers/GuardianProver.sol

     |  // @audit-info Contains redundant modifiers
  10 |  contract GuardianProver is Guardians {
  :  |
     |      // @audit-issue This is the only invocation of this modifier
  25 |      function init(address _owner, address _addressManager) external initializer {
  :  |
     |          // @audit-issue This is the only invocation of this modifier
  41 |          whenNotPaused
     |          // @audit-issue This is the only invocation of this modifier
  42 |          nonReentrant
```
GitHub: [25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/GuardianProver.sol#L25), [41](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/GuardianProver.sol#L41), [42](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/GuardianProver.sol#L42)


```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

     |  // @audit-info Contains redundant modifiers
   9 |  abstract contract Guardians is EssentialContract {
  :  |
     |          // @audit-issue This is the only invocation of this modifier
  58 |          onlyOwner
     |          // @audit-issue This is the only invocation of this modifier
  59 |          nonReentrant
```
GitHub: [58](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L58), [59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L59)


```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

     |  // @audit-info Contains redundant modifiers
  22 |  contract TaikoL1 is EssentialContract, ITaikoL1, TaikoEvents, TaikoErrors {
  :  |
     |          // @audit-issue This is the only invocation of this modifier
  48 |          initializer
  :  |
     |          // @audit-issue This is the only invocation of this modifier
 225 |          onlyFromOwnerOrNamed("chain_pauser")
```
GitHub: [48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L48), [225](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L225)


```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

     |  // @audit-info Contains redundant modifiers
  15 |  contract TaikoToken is EssentialContract, ERC20SnapshotUpgradeable, ERC20VotesUpgradeable {
  :  |
     |          // @audit-issue This is the only invocation of this modifier
  32 |          initializer
  :  |
     |      // @audit-issue This is the only invocation of this modifier
  47 |      function burn(address _from, uint256 _amount) public onlyOwner {
  :  |
     |      // @audit-issue This is the only invocation of this modifier
  52 |      function snapshot() public onlyFromOwnerOrNamed("snapshooter") {
```
GitHub: [32](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L32), [47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L47), [52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L52)


```solidity
File: packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol

     |  // @audit-info Contains redundant modifiers
  10 |  contract DevnetTierProvider is EssentialContract, ITierProvider {
  :  |
     |      // @audit-issue This is the only invocation of this modifier
  15 |      function init(address _owner) external initializer {
```
GitHub: [15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L15)


```solidity
File: packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol

     |  // @audit-info Contains redundant modifiers
  10 |  contract MainnetTierProvider is EssentialContract, ITierProvider {
  :  |
     |      // @audit-issue This is the only invocation of this modifier
  15 |      function init(address _owner) external initializer {
```
GitHub: [15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L15)


```solidity
File: packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol

     |  // @audit-info Contains redundant modifiers
  10 |  contract TestnetTierProvider is EssentialContract, ITierProvider {
  :  |
     |      // @audit-issue This is the only invocation of this modifier
  15 |      function init(address _owner) external initializer {
```
GitHub: [15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L15)


```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

     |  // @audit-info Contains redundant modifiers
  14 |  abstract contract CrossChainOwned is EssentialContract, IMessageInvocable {
  :  |
     |          // @audit-issue This is the only invocation of this modifier
  39 |          whenNotPaused
     |          // @audit-issue This is the only invocation of this modifier
  40 |          onlyFromNamed("bridge")
  :  |
     |          // @audit-issue This is the only invocation of this modifier
  67 |          onlyInitializing
```
GitHub: [39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L39), [40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L40), [67](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L67)


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

     |  // @audit-info Contains redundant modifiers
  21 |  contract TaikoL2 is CrossChainOwned {
  :  |
     |          // @audit-issue This is the only invocation of this modifier
  78 |          initializer
  :  |
     |          // @audit-issue This is the only invocation of this modifier
 168 |          onlyFromOwnerOrNamed("withdrawer")
  :  |
     |          // @audit-issue This is the only invocation of this modifier
 170 |          whenNotPaused
```
GitHub: [78](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L78), [168](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L168), [170](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L170)


```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

     |  // @audit-info Contains redundant modifiers
   9 |  contract TaikoL2EIP1559Configurable is TaikoL2 {
  :  |
     |          // @audit-issue This is the only invocation of this modifier
  31 |          onlyOwner
```
GitHub: [31](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L31)


```solidity
File: packages/protocol/contracts/signal/SignalService.sol

     |  // @audit-info Contains redundant modifiers
  14 |  contract SignalService is EssentialContract, ISignalService {
  :  |
     |      // @audit-issue This is the only invocation of this modifier
  48 |      function init(address _owner, address _addressManager) external initializer {
  :  |
     |      // @audit-issue This is the only invocation of this modifier
  56 |      function authorize(address _addr, bool _authorize) external onlyOwner {
```
GitHub: [48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L48), [56](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L56)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

     |  // @audit-info Contains redundant modifiers
  16 |  contract Bridge is EssentialContract, IBridge {
  :  |
     |      // @audit-issue This is the only invocation of this modifier
  75 |      function init(address _owner, address _addressManager) external initializer {
```
GitHub: [75](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L75)


```solidity
File: packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

     |  // @audit-info Contains redundant modifiers
  28 |  contract USDCAdapter is BridgedERC20Base {
  :  |
     |      // @audit-issue This is the only invocation of this modifier
  38 |      function init(address _owner, address _addressManager, IUSDC _usdc) external initializer {
```
GitHub: [38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L38)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

     |  // @audit-info Contains redundant modifiers
  15 |  contract BridgedERC20 is
  :  |
     |          // @audit-issue This is the only invocation of this modifier
  62 |          initializer
  :  |
     |      // @audit-issue This is the only invocation of this modifier
  80 |      function setSnapshoter(address _snapshooter) external onlyOwner {
  :  |
     |      // @audit-issue This is the only invocation of this modifier
  85 |      function snapshot() external onlyOwnerOrSnapshooter {
```
GitHub: [62](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L62), [80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L80), [85](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L85)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

     |  // @audit-info Contains redundant modifiers
   9 |  abstract contract BridgedERC20Base is EssentialContract, IBridgedERC20 {
  :  |
     |          // @audit-issue This is the only invocation of this modifier
  43 |          onlyFromOwnerOrNamed("erc20_vault")
```
GitHub: [43](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L43)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

     |  // @audit-info Contains redundant modifiers
  12 |  contract BridgedERC721 is EssentialContract, ERC721Upgradeable {
  :  |
     |          // @audit-issue This is the only invocation of this modifier
  40 |          initializer
```
GitHub: [40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L40)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

     |  // @audit-info Contains redundant modifiers
  14 |  contract BridgedERC1155 is EssentialContract, IERC1155MetadataURIUpgradeable, ERC1155Upgradeable {
  :  |
     |          // @audit-issue This is the only invocation of this modifier
  47 |          initializer
```
GitHub: [47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L47)


```solidity
File: packages/protocol/contracts/tokenvault/BaseVault.sol

     |  // @audit-info Contains redundant modifiers
  12 |  abstract contract BaseVault is
  :  |
     |      // @audit-issue This is the only invocation of this modifier
  32 |      function init(address _owner, address _addressManager) external initializer {
```
GitHub: [32](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L32)


```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

     |  // @audit-info Contains redundant modifiers
  29 |  contract ERC1155Vault is BaseNFTVault, ERC1155ReceiverUpgradeable {
  :  |
     |          // @audit-issue This is the only invocation of this modifier
  44 |          withValidOperation(_op)
```
GitHub: [44](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L44)


```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

     |  // @audit-info Contains redundant modifiers
  18 |  contract ERC20Vault is BaseVault {
  :  |
     |          // @audit-issue This is the only invocation of this modifier
 155 |          onlyOwner
```
GitHub: [155](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L155)


```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

     |  // @audit-info Contains redundant modifiers
  16 |  contract ERC721Vault is BaseNFTVault, IERC721Receiver {
  :  |
     |          // @audit-issue This is the only invocation of this modifier
  31 |          withValidOperation(_op)
```
GitHub: [31](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L31)


```solidity
File: packages/protocol/contracts/verifiers/GuardianVerifier.sol

     |  // @audit-info Contains redundant modifiers
  10 |  contract GuardianVerifier is EssentialContract, IVerifier {
  :  |
     |      // @audit-issue This is the only invocation of this modifier
  18 |      function init(address _owner, address _addressManager) external initializer {
```
GitHub: [18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L18)


```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

     |  // @audit-info Contains redundant modifiers
  19 |  contract SgxVerifier is EssentialContract, IVerifier {
  :  |
     |      // @audit-issue This is the only invocation of this modifier
  83 |      function init(address _owner, address _addressManager) external initializer {
  :  |
     |          // @audit-issue This is the only invocation of this modifier
  92 |          onlyOwner
  :  |
     |          // @audit-issue This is the only invocation of this modifier
 102 |          onlyFromOwnerOrNamed("rollup_watchdog")
  :  |
     |          // @audit-issue This is the only invocation of this modifier
 145 |          onlyFromNamed("taiko")
```
GitHub: [83](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L83), [92](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L92), [102](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L102), [145](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L145)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

     |  // @audit-info Contains redundant modifiers
  11 |  contract ERC20Airdrop is MerkleClaimable {
  :  |
     |          // @audit-issue This is the only invocation of this modifier
  36 |          initializer
  :  |
     |          // @audit-issue This is the only invocation of this modifier
  57 |          nonReentrant
```
GitHub: [36](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L36), [57](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L57)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

     |  // @audit-info Contains redundant modifiers
  12 |  contract ERC20Airdrop2 is MerkleClaimable {
  :  |
     |          // @audit-issue This is the only invocation of this modifier
  64 |          initializer
  :  |
     |      // @audit-issue This is the only invocation of this modifier
  78 |      function claim(address user, uint256 amount, bytes32[] calldata proof) external nonReentrant {
  :  |
     |      // @audit-issue This is the only invocation of this modifier
  88 |      function withdraw(address user) external ongoingWithdrawals {
```
GitHub: [64](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L64), [78](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L78), [88](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L88)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

     |  // @audit-info Contains redundant modifiers
   9 |  contract ERC721Airdrop is MerkleClaimable {
  :  |
     |          // @audit-issue This is the only invocation of this modifier
  34 |          initializer
  :  |
     |          // @audit-issue This is the only invocation of this modifier
  53 |          nonReentrant
```
GitHub: [34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L34), [53](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L53)


```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

     |  // @audit-info Contains redundant modifiers
  10 |  abstract contract MerkleClaimable is EssentialContract {
  :  |
     |          // @audit-issue This is the only invocation of this modifier
  51 |          onlyOwner
  :  |
     |          // @audit-issue This is the only invocation of this modifier
  62 |          onlyInitializing
  :  |
     |      // @audit-issue This is the only invocation of this modifier
  67 |      function _verifyClaim(bytes memory data, bytes32[] calldata proof) internal ongoingClaim {
```
GitHub: [51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L51), [62](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L62), [67](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L67)


```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

     |  // @audit-info Contains redundant modifiers
  25 |  contract TimelockTokenPool is EssentialContract {
  :  |
     |          // @audit-issue This is the only invocation of this modifier
 118 |          initializer
```
GitHub: [118](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L118)


## [G-29] It costs more gas to initialize non-`constant`/non-`immutable` state variables to zero/false than to let the default of zero/false be applied

The default value for variables is zero, so initializing them to zero is superfluous. This will also save gas if the variable is a mutable state variable.

*Instances: 6*

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

     |  // @audit-issue Initial value is unnecessary
  72 |  uint256 itemCount = 0;
```
GitHub: [72](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L72)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

     |  // @audit-issue Initial value is unnecessary
  58 |  uint256 i = 0;
```
GitHub: [58](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L58)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

     |  // @audit-issue Initial value is unnecessary
  82 |  uint256 currentKeyIndex = 0;
```
GitHub: [82](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L82)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

     |  // @audit-issue Initial value is unnecessary
  51 |  uint256 index = 0;
```
GitHub: [51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L51)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

     |  // @audit-issue Initial value is unnecessary
 331 |  uint256 ret = 0;
```
GitHub: [331](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L331)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

     |  // @audit-issue Initial value is unnecessary
  46 |  uint256 timestamp = 0;
```
GitHub: [46](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L46)


## [G-30] Iterating backwards in a `for` statement saves gas

Iterating backwards allows you to specify your loop termination condition using `0`, and comparisons with `0` are more gas efficient than with arbitrary integers.

*Instances: 45*

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

     |  // @audit-issue Consider looping backwards
 172 |  for (uint256 i; i < _tierFees.length; ++i) {
```
GitHub: [172](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L172)


```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

     |  // @audit-issue Consider looping backwards
 244 |  for (uint256 i; i < params.hookCalls.length; ++i) {
```
GitHub: [244](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L244)


```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

     |  // @audit-issue Consider looping backwards
  74 |  for (uint256 i; i < guardians.length; ++i) {

     |  // @audit-issue Consider looping backwards
  80 |  for (uint256 i = 0; i < _newGuardians.length; ++i) {

     |  // @audit-issue Consider looping backwards
 133 |  for (uint256 i; i < guardiansLength; ++i) {
```
GitHub: [74](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L74), [80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L80), [133](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L133)


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

     |  // @audit-issue Consider looping backwards
 234 |  for (uint256 i; i < 255 && _blockId >= i + 1; ++i) {
```
GitHub: [234](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L234)


```solidity
File: packages/protocol/contracts/signal/SignalService.sol

     |  // @audit-issue Consider looping backwards
 104 |  for (uint256 i; i < hopProofs.length; ++i) {
```
GitHub: [104](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L104)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

     |  // @audit-issue Consider looping backwards
  90 |  for (uint256 i; i < _msgHashes.length; ++i) {
```
GitHub: [90](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L90)


```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

     |  // @audit-issue Consider looping backwards
  47 |  for (uint256 i; i < _op.amounts.length; ++i) {

     |  // @audit-issue Consider looping backwards
 251 |  for (uint256 i; i < _op.tokenIds.length; ++i) {

     |  // @audit-issue Consider looping backwards
 269 |  for (uint256 i; i < _op.tokenIds.length; ++i) {
```
GitHub: [47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L47), [251](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L251), [269](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L269)


```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

     |  // @audit-issue Consider looping backwards
  34 |  for (uint256 i; i < _op.tokenIds.length; ++i) {

     |  // @audit-issue Consider looping backwards
 170 |  for (uint256 i; i < _tokenIds.length; ++i) {

     |  // @audit-issue Consider looping backwards
 175 |  for (uint256 i; i < _tokenIds.length; ++i) {

     |  // @audit-issue Consider looping backwards
 197 |  for (uint256 i; i < _op.tokenIds.length; ++i) {

     |  // @audit-issue Consider looping backwards
 210 |  for (uint256 i; i < _op.tokenIds.length; ++i) {
```
GitHub: [34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L34), [170](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L170), [175](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L175), [197](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L197), [210](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L210)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

     |  // @audit-issue Consider looping backwards
  46 |  for (i = 1; i <= lenLen; i++) {

     |  // @audit-issue Consider looping backwards
  59 |  for (; i < 32; i++) {

     |  // @audit-issue Consider looping backwards
  66 |  for (uint256 j = 0; j < out_.length; j++) {
```
GitHub: [46](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L46), [59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L59), [66](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

     |  // @audit-issue Consider looping backwards
  85 |  for (uint256 i = 0; i < proof.length; i++) {
```
GitHub: [85](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85)


```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

     |  // @audit-issue Consider looping backwards
 104 |  for (uint256 i; i < _ids.length; ++i) {

     |  // @audit-issue Consider looping backwards
 210 |  for (uint256 i; i < _instances.length; ++i) {
```
GitHub: [104](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L104), [210](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

     |  // @audit-issue Consider looping backwards
  59 |  for (uint256 i; i < tokenIds.length; ++i) {
```
GitHub: [59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59)


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

     |  // @audit-issue Consider looping backwards
  80 |  for (uint256 i; i < serialNumBatch.length; ++i) {

     |  // @audit-issue Consider looping backwards
  95 |  for (uint256 i; i < serialNumBatch.length; ++i) {

     |  // @audit-issue Consider looping backwards
 191 |  for (uint256 i; i < enclaveId.tcbLevels.length; ++i) {

     |  // @audit-issue Consider looping backwards
 214 |  for (uint256 i; i < tcb.tcbLevels.length; ++i) {

     |  // @audit-issue Consider looping backwards
 240 |  for (uint256 i; i < CPUSVN_LENGTH; ++i) {

     |  // @audit-issue Consider looping backwards
 259 |  for (uint256 i; i < n; ++i) {

     |  // @audit-issue Consider looping backwards
 420 |  for (uint256 i; i < 3; ++i) {
```
GitHub: [80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L80), [95](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L95), [191](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L191), [214](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L214), [240](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L240), [259](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L259), [420](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L420)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

     |  // @audit-issue Consider looping backwards
  54 |  for (uint256 i; i < size; ++i) {

     |  // @audit-issue Consider looping backwards
 244 |  for (uint256 i; i < split.length; ++i) {

     |  // @audit-issue Consider looping backwards
 354 |  for (uint256 i; i < SGX_TCB_CPUSVN_SIZE + 1; ++i) {
```
GitHub: [54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L54), [244](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L244), [354](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L354)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

     |  // @audit-issue Consider looping backwards
 153 |  for (uint256 i; i < encoded.length; ++i) {

     |  // @audit-issue Consider looping backwards
 281 |  for (uint256 i; i < 3; ++i) {
```
GitHub: [153](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L153), [281](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L281)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

     |  // @audit-issue Consider looping backwards
 333 |  for (uint256 i; i < len; ++i) {
```
GitHub: [333](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L333)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

     |  // @audit-issue Consider looping backwards
 140 |  for (uint256 i = 2; i < 2 + paddingLen; ++i) {

     |  // @audit-issue Consider looping backwards
 152 |  for (uint256 i; i < digestAlgoWithParamLen; ++i) {

     |  // @audit-issue Consider looping backwards
 158 |  for (uint256 i; i < digestAlgoWithParamLen; ++i) {

     |  // @audit-issue Consider looping backwards
 174 |  for (uint256 i; i < _sha256.length; ++i) {

     |  // @audit-issue Consider looping backwards
 273 |  for (uint256 i = 2; i < 2 + paddingLen; ++i) {

     |  // @audit-issue Consider looping backwards
 283 |  for (uint256 i; i < sha1Prefix.length; ++i) {

     |  // @audit-issue Consider looping backwards
 290 |  for (uint256 i; i < _sha1.length; ++i) {
```
GitHub: [140](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L140), [152](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L152), [158](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L158), [174](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L174), [273](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L273), [283](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L283), [290](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L290)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

     |  // @audit-issue Consider looping backwards
  48 |  for (uint16 i = 1970; i < year; ++i) {

     |  // @audit-issue Consider looping backwards
  59 |  for (uint8 i = 1; i < month; ++i) {
```
GitHub: [48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L48), [59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L59)


## [G-31] Mappings are cheaper to use than storage arrays

When using storage arrays, solidity adds an internal lookup of the array's length (a Gcoldsload **2100 gas**) to ensure you don't read past the array's end. You can avoid this lookup by using a `mapping` and storing the number of entries in a separate storage variable. In cases where you have sentinel values (e.g. 'zero' means invalid), you can avoid length checks.

*Instances: 36*

```solidity
File: packages/protocol/contracts/common/AddressManager.sol

  14 |  uint256[49] private __gap;
```
GitHub: [14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L14)


```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

  14 |  uint256[49] private __gap;
```
GitHub: [14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L14)


```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

  25 |  uint256[49] private __gap;
```
GitHub: [25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L25)


```solidity
File: packages/protocol/contracts/L1/gov/TaikoGovernor.sol

  23 |  uint256[50] private __gap;
```
GitHub: [23](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L23)


```solidity
File: packages/protocol/contracts/L1/gov/TaikoTimelockController.sol

  10 |  uint256[50] private __gap;
```
GitHub: [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L10)


```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

  40 |  uint256[50] private __gap;
```
GitHub: [40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L40)


```solidity
File: packages/protocol/contracts/L1/provers/GuardianProver.sol

  11 |  uint256[50] private __gap;
```
GitHub: [11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/GuardianProver.sol#L11)


```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

  23 |  address[] public guardians;

  32 |  uint256[46] private __gap;
```
GitHub: [23](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L23), [32](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L32)


```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

  26 |  uint256[50] private __gap;
```
GitHub: [26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L26)


```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

  16 |  uint256[50] private __gap;
```
GitHub: [16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L16)


```solidity
File: packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol

  11 |  uint256[50] private __gap;
```
GitHub: [11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L11)


```solidity
File: packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol

  11 |  uint256[50] private __gap;
```
GitHub: [11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L11)


```solidity
File: packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol

  11 |  uint256[50] private __gap;
```
GitHub: [11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L11)


```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

  21 |  uint256[49] private __gap;
```
GitHub: [21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L21)


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

  52 |  uint256[47] private __gap;
```
GitHub: [52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L52)


```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

  13 |  uint256[49] private __gap;
```
GitHub: [13](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L13)


```solidity
File: packages/protocol/contracts/signal/SignalService.sol

  23 |  uint256[48] private __gap;
```
GitHub: [23](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L23)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

  48 |  uint256[43] private __gap;
```
GitHub: [48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L48)


```solidity
File: packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

  32 |  uint256[49] private __gap;
```
GitHub: [32](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L32)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

  32 |  uint256[47] private __gap;
```
GitHub: [32](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L32)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

  16 |  uint256[49] private __gap;
```
GitHub: [16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L16)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

  19 |  uint256[48] private __gap;
```
GitHub: [19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L19)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

  27 |  uint256[46] private __gap;
```
GitHub: [27](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L27)


```solidity
File: packages/protocol/contracts/tokenvault/BaseNFTVault.sol

  61 |  uint256[48] private __gap;
```
GitHub: [61](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L61)


```solidity
File: packages/protocol/contracts/tokenvault/BaseVault.sol

  18 |  uint256[50] private __gap;
```
GitHub: [18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L18)


```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

  32 |  uint256[50] private __gap;
```
GitHub: [32](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L32)


```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

  54 |  uint256[47] private __gap;
```
GitHub: [54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L54)


```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

  19 |  uint256[50] private __gap;
```
GitHub: [19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L19)


```solidity
File: packages/protocol/contracts/verifiers/GuardianVerifier.sol

  11 |  uint256[50] private __gap;
```
GitHub: [11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L11)


```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

  57 |  uint256[47] private __gap;
```
GitHub: [57](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L57)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

  18 |  uint256[48] private __gap;
```
GitHub: [18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L18)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

  30 |  uint256[45] private __gap;
```
GitHub: [30](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L30)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

  16 |  uint256[48] private __gap;
```
GitHub: [16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L16)


```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

  23 |  uint256[47] private __gap;
```
GitHub: [23](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L23)


```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

  82 |  uint128[44] private __gap;
```
GitHub: [82](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L82)


## [G-32] Merge events to save gas

Consolidating multiple event emissions into a single event in Solidity can result in significant gas savings. Each event emission in Ethereum involves a gas cost, specifically for the topics logged with the event. By merging sequential events into a singular event, you can save on the Glogtopic cost, which is incurred for each topic of each event. This approach can save around 375 gas per additional topic. This strategy is particularly beneficial in functions where multiple related events are emitted in sequence. However, it's crucial to balance gas optimization with the clarity and utility of the event data for off-chain consumers.

*Instances: 9*

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

  68 |  function proposeBlock(
  69 |      TaikoData.State storage _state,
  70 |      TaikoData.Config memory _config,
  71 |      IAddressResolver _resolver,
  72 |      bytes calldata _data,
  73 |      bytes calldata _txList
  74 |  )
  75 |      internal
  76 |      returns (TaikoData.BlockMetadata memory meta_, TaikoData.EthDeposit[] memory deposits_)
  :  |
 166 |                  emit BlobCached(meta_.blobHash);
  :  |
 273 |      emit BlockProposed({
 274 |          blockId: blk.blockId,
 275 |          assignedProver: blk.assignedProver,
 276 |          livenessBond: _config.livenessBond,
 277 |          meta: meta_,
 278 |          depositsProcessed: deposits_
 279 |      });
```
GitHub: [166](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L166), [273-279](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L273-L279)


```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

  91 |  function proveBlock(
  92 |      TaikoData.State storage _state,
  93 |      TaikoData.Config memory _config,
  94 |      IAddressResolver _resolver,
  95 |      TaikoData.BlockMetadata memory _meta,
  96 |      TaikoData.Transition memory _tran,
  97 |      TaikoData.TierProof memory _proof
  98 |  )
  99 |      internal
 100 |      returns (uint8 maxBlocksToVerify_)
  :  |
 209 |          emit TransitionProved({
 210 |              blockId: blk.blockId,
 211 |              tran: _tran,
 212 |              prover: msg.sender,
 213 |              validityBond: tier.validityBond,
 214 |              tier: _proof.tier
 215 |          });
  :  |
 230 |              emit TransitionProved({
 231 |                  blockId: blk.blockId,
 232 |                  tran: _tran,
 233 |                  prover: msg.sender,
 234 |                  validityBond: 0,
 235 |                  tier: _proof.tier
 236 |              });
  :  |
 254 |              emit TransitionContested({
 255 |                  blockId: blk.blockId,
 256 |                  tran: _tran,
 257 |                  contester: msg.sender,
 258 |                  contestBond: tier.contestBond,
 259 |                  tier: _proof.tier
 260 |              });
```
GitHub: [209-215](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L209-L215), [230-236](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L230-L236), [254-260](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L254-L260)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 155 |  function recallMessage(
 156 |      Message calldata _message,
 157 |      bytes calldata _proof
 158 |  )
 159 |      external
 160 |      nonReentrant
 161 |      whenNotPaused
 162 |      sameChain(_message.srcChainId)
  :  |
 208 |          emit MessageRecalled(msgHash);
  :  |
 210 |          emit MessageReceived(msgHash, _message, true);

 217 |  function processMessage(
 218 |      Message calldata _message,
 219 |      bytes calldata _proof
 220 |  )
 221 |      external
 222 |      nonReentrant
 223 |      whenNotPaused
 224 |      sameChain(_message.destChainId)
  :  |
 301 |          emit MessageExecuted(msgHash);
  :  |
 303 |          emit MessageReceived(msgHash, _message, false);
```
GitHub: [208](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L208), [210](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L210), [301](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L301), [303](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L303)


## [G-33] Multiple `address`/ID mappings can be combined into a single `mapping` of an `address`/ID to a `struct`

Saves a storage slot for the mapping. Depending on the circumstances and sizes of types, can avoid a Gsset (20000 gas) per mapping combined. Reads and subsequent writes can also be cheaper when a function requires both values and they both fit in the same storage slot. Finally, if both fields are accessed in the same function, can save ~42 gas per access due to [not having to recalculate the key's keccak256 hash](https://gist.github.com/IllIllI000/ec23a57daa30a8f8ca8b9681c8ccefb0) (Gkeccak256 - 30 gas) and that calculation's associated stack operations.

*Instances: 2*

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

     |  // @audit-issue Consider whether multiple mappings can be merged into a single struct mapping
  39 |  mapping(bytes32 enclave => bool trusted) private _trustedUserMrEnclave;

     |  // @audit-issue Consider whether multiple mappings can be merged into a single struct mapping
  40 |  mapping(bytes32 signer => bool trusted) private _trustedUserMrSigner;
```
GitHub: [39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L39), [40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L40)


## [G-34] Multiple accesses of a mapping/array should use a local variable cache

The instances below point to multiple accesses of a value inside a mapping/array, within a function. Caching a mapping's value in a local `storage` or `calldata` variable when the value is accessed [multiple times](https://gist.github.com/IllIllI000/ec23a57daa30a8f8ca8b9681c8ccefb0), saves **~42 gas per access** due to not having to recalculate the key's keccak256 hash (Gkeccak256 - **30 gas**) and that calculation's associated stack operations. Caching an array's struct avoids recalculating the array offsets into memory/calldata

*Instances: 54*

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

     |  // @audit-info Context
 164 |  function _getProverFee(
 165 |      TaikoData.TierFee[] memory _tierFees,
 166 |      uint16 _tierId
 167 |  )
 168 |      private
 169 |      pure
 170 |      returns (uint256)
  :  |
     |          // @audit-issue `_tierFees[i]` usage #1
     |          // @audit-issue `_tierFees[i]` usage #2
 173 |          if (_tierFees[i].tier == _tierId) return _tierFees[i].fee;
```
GitHub: [173](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L173), [173](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L173)


```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

     |  // @audit-info Context
  67 |  function processDeposits(
  68 |      TaikoData.State storage _state,
  69 |      TaikoData.Config memory _config,
  70 |      address _feeRecipient
  71 |  )
  72 |      internal
  73 |      returns (TaikoData.EthDeposit[] memory deposits_)
  :  |
     |              // @audit-issue `deposits_[i]` usage #1
  88 |              deposits_[i] = TaikoData.EthDeposit({
  :  |
     |              // @audit-issue `deposits_[i]` usage #2
     |              // @audit-issue `deposits_[i]` usage #3
  93 |              uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount;
  :  |
     |                  // @audit-issue `deposits_[i]` usage #4
 101 |                  deposits_[i].amount -= _fee;
```
GitHub: [88](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L88), [93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L93), [93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L93), [101](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L101)


```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

     |  // @audit-info Context
  68 |  function proposeBlock(
  69 |      TaikoData.State storage _state,
  70 |      TaikoData.Config memory _config,
  71 |      IAddressResolver _resolver,
  72 |      bytes calldata _data,
  73 |      bytes calldata _txList
  74 |  )
  75 |      internal
  76 |      returns (TaikoData.BlockMetadata memory meta_, TaikoData.EthDeposit[] memory deposits_)
  :  |
     |              // @audit-issue `params.hookCalls[i]` usage #1
 245 |              if (uint160(prevHook) >= uint160(params.hookCalls[i].hook)) {
  :  |
     |              // @audit-issue `params.hookCalls[i]` usage #2
 253 |              IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }(
     |                  // @audit-issue `params.hookCalls[i]` usage #3
 254 |                  blk, meta_, params.hookCalls[i].data
  :  |
     |              // @audit-issue `params.hookCalls[i]` usage #4
 257 |              prevHook = params.hookCalls[i].hook;
```
GitHub: [245](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L245), [253](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L253), [254](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L254), [257](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L257)


```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

     |  // @audit-info Context
 269 |  function _createTransition(
 270 |      TaikoData.State storage _state,
 271 |      TaikoData.Block storage _blk,
 272 |      TaikoData.Transition memory _tran,
 273 |      uint64 slot
 274 |  )
 275 |      private
 276 |      returns (uint32 tid_, TaikoData.TransitionState storage ts_)
  :  |
     |          // @audit-issue `_state.transitions[slot][tid_]` usage #1
 299 |          ts_ = _state.transitions[slot][tid_];
  :  |
     |          // @audit-issue `_state.transitions[slot][tid_]` usage #2
 345 |          ts_ = _state.transitions[slot][tid_];
```
GitHub: [299](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L299), [345](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L345)


```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

     |  // @audit-info Context
  85 |  function verifyBlocks(
  86 |      TaikoData.State storage _state,
  87 |      TaikoData.Config memory _config,
  88 |      IAddressResolver _resolver,
  89 |      uint64 _maxBlocksToVerify
  90 |  )
  91 |      internal
  :  |
     |      // @audit-issue `_state.blocks[slot]` usage #1
 104 |      TaikoData.Block storage blk = _state.blocks[slot];
  :  |
     |              // @audit-issue `_state.blocks[slot]` usage #2
 130 |              blk = _state.blocks[slot];

     |  // @audit-info Context
  85 |  function verifyBlocks(
  86 |      TaikoData.State storage _state,
  87 |      TaikoData.Config memory _config,
  88 |      IAddressResolver _resolver,
  89 |      uint64 _maxBlocksToVerify
  90 |  )
  91 |      internal
  :  |
     |      // @audit-issue `_state.transitions[slot][tid]` usage #1
 115 |      bytes32 blockHash = _state.transitions[slot][tid].blockHash;
  :  |
     |              // @audit-issue `_state.transitions[slot][tid]` usage #2
 140 |              TaikoData.TransitionState storage ts = _state.transitions[slot][tid];
```
GitHub: [104](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L104), [130](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L130), [115](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L115), [140](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L140)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

     |  // @audit-info Context
 155 |  function recallMessage(
 156 |      Message calldata _message,
 157 |      bytes calldata _proof
 158 |  )
 159 |      external
 160 |      nonReentrant
 161 |      whenNotPaused
 162 |      sameChain(_message.srcChainId)
  :  |
     |      // @audit-issue `proofReceipt[msgHash]` usage #1
 168 |      uint64 receivedAt = proofReceipt[msgHash].receivedAt;
  :  |
     |          // @audit-issue `proofReceipt[msgHash]` usage #2
 184 |          proofReceipt[msgHash].receivedAt = receivedAt;
  :  |
     |          // @audit-issue `proofReceipt[msgHash]` usage #3
 190 |          delete proofReceipt[msgHash];

     |  // @audit-info Context
 217 |  function processMessage(
 218 |      Message calldata _message,
 219 |      bytes calldata _proof
 220 |  )
 221 |      external
 222 |      nonReentrant
 223 |      whenNotPaused
 224 |      sameChain(_message.destChainId)
  :  |
     |      // @audit-issue `proofReceipt[msgHash]` usage #1
 230 |      uint64 receivedAt = proofReceipt[msgHash].receivedAt;
  :  |
     |              // @audit-issue `proofReceipt[msgHash]` usage #2
 243 |              proofReceipt[msgHash] = ProofReceipt({
  :  |
     |      // @audit-issue `proofReceipt[msgHash]` usage #3
 250 |      if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) {
  :  |
     |          // @audit-issue `proofReceipt[msgHash]` usage #4
 264 |          delete proofReceipt[msgHash];
```
GitHub: [168](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L168), [184](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L184), [190](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L190), [230](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L230), [243](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L243), [250](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L250), [264](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L264)


```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

     |  // @audit-info Context
 240 |  function _handleMessage(
 241 |      address _user,
 242 |      BridgeTransferOp memory _op
 243 |  )
 244 |      private
 245 |      returns (bytes memory msgData_, CanonicalNFT memory ctoken_)
  :  |
     |          // @audit-issue `bridgedToCanonical[_op.token]` usage #1
 249 |          if (bridgedToCanonical[_op.token].addr != address(0)) {
     |              // @audit-issue `bridgedToCanonical[_op.token]` usage #2
 250 |              ctoken_ = bridgedToCanonical[_op.token];
```
GitHub: [249](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L249), [250](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L250)


```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

     |  // @audit-info Context
 148 |  function changeBridgedToken(
 149 |      CanonicalERC20 calldata _ctoken,
 150 |      address _btokenNew
 151 |  )
 152 |      external
 153 |      nonReentrant
 154 |      whenNotPaused
 155 |      onlyOwner
 156 |      returns (address btokenOld_)
     |      // @audit-issue `bridgedToCanonical[_btokenNew]` usage #1
 158 |      if (_btokenNew == address(0) || bridgedToCanonical[_btokenNew].addr != address(0)) {
  :  |
     |          // @audit-issue `bridgedToCanonical[_btokenNew]` usage #2
 180 |          delete bridgedToCanonical[_btokenNew];
  :  |
     |      // @audit-issue `bridgedToCanonical[_btokenNew]` usage #3
 188 |      bridgedToCanonical[_btokenNew] = _ctoken;

     |  // @audit-info Context
 348 |  function _handleMessage(
 349 |      address _user,
 350 |      address _token,
 351 |      address _to,
 352 |      uint256 _amount
 353 |  )
 354 |      private
 355 |      returns (bytes memory msgData_, CanonicalERC20 memory ctoken_, uint256 balanceChange_)
  :  |
     |      // @audit-issue `bridgedToCanonical[_token]` usage #1
 358 |      if (bridgedToCanonical[_token].addr != address(0)) {
     |          // @audit-issue `bridgedToCanonical[_token]` usage #2
 359 |          ctoken_ = bridgedToCanonical[_token];
```
GitHub: [158](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L158), [180](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L180), [188](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L188), [358](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L358), [359](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L359)


```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

     |  // @audit-info Context
 187 |  function _handleMessage(
 188 |      address _user,
 189 |      BridgeTransferOp memory _op
 190 |  )
 191 |      private
 192 |      returns (bytes memory msgData_, CanonicalNFT memory ctoken_)
  :  |
     |          // @audit-issue `bridgedToCanonical[_op.token]` usage #1
 195 |          if (bridgedToCanonical[_op.token].addr != address(0)) {
     |              // @audit-issue `bridgedToCanonical[_op.token]` usage #2
 196 |              ctoken_ = bridgedToCanonical[_op.token];
```
GitHub: [195](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L195), [196](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L196)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

     |  // @audit-info Context
  68 |  function get(
  69 |      bytes memory _key,
  70 |      bytes[] memory _proof,
  71 |      bytes32 _root
  72 |  )
  73 |      internal
  74 |      pure
  75 |      returns (bytes memory value_)
  :  |
     |                  // @audit-issue `currentNode.decoded[1]` usage #1
 171 |                  value_ = RLPReader.readBytes(currentNode.decoded[1]);
  :  |
     |                  // @audit-issue `currentNode.decoded[1]` usage #2
 188 |                  currentNodeID = _getNodeID(currentNode.decoded[1]);
```
GitHub: [171](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L171), [188](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L188)


```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

     |  // @audit-info Context
 100 |  function deleteInstances(uint256[] calldata _ids)
 101 |      external
 102 |      onlyFromOwnerOrNamed("rollup_watchdog")
  :  |
     |          // @audit-issue `instances[idx]` usage #1
 107 |          if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();
  :  |
     |          // @audit-issue `instances[idx]` usage #2
 109 |          emit InstanceDeleted(idx, instances[idx].addr);
  :  |
     |          // @audit-issue `instances[idx]` usage #3
 111 |          delete instances[idx];

     |  // @audit-info Context
 233 |  function _isInstanceValid(uint256 id, address instance) private view returns (bool) {
  :  |
     |      // @audit-issue `instances[id]` usage #1
 235 |      if (instance != instances[id].addr) return false;
     |      // @audit-issue `instances[id]` usage #2
 236 |      return instances[id].validSince <= block.timestamp
     |          // @audit-issue `instances[id]` usage #3
 237 |          && block.timestamp <= instances[id].validSince + INSTANCE_EXPIRY;
```
GitHub: [107](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L107), [109](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L109), [111](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L111), [235](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L235), [236](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L236), [237](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L237)


```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

     |  // @audit-info Context
 135 |  function grant(address _recipient, Grant memory _grant) external onlyOwner {
  :  |
     |      // @audit-issue `recipients[_recipient]` usage #1
 137 |      if (recipients[_recipient].grant.amount != 0) revert ALREADY_GRANTED();
  :  |
     |      // @audit-issue `recipients[_recipient]` usage #2
 142 |      recipients[_recipient].grant = _grant;
```
GitHub: [137](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L137), [142](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L142)


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

     |  // @audit-info Context
 248 |  function _verifyCertChain(IPEMCertChainLib.ECSha256Certificate[] memory certs)
 249 |      private
 250 |      view
 251 |      returns (bool)
  :  |
     |              // @audit-issue `certs[i]` usage #1
 263 |              issuer = certs[i];
  :  |
     |                  // @audit-issue `certs[i]` usage #2
 268 |                  certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.ROOT)][certs[i]
  :  |
     |              // @audit-issue `certs[i]` usage #3
 270 |              } else if (certs[i].isPck) {
     |                  // @audit-issue `certs[i]` usage #4
 271 |                  certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.PCK)][certs[i]
  :  |
     |              // @audit-issue `certs[i]` usage #5
     |              // @audit-issue `certs[i]` usage #6
 280 |              block.timestamp > certs[i].notBefore && block.timestamp < certs[i].notAfter;
  :  |
     |              // @audit-issue `certs[i]` usage #7
     |              // @audit-issue `certs[i]` usage #8
 286 |              certs[i].tbsCertificate, certs[i].signature, issuer.pubKey

     |  // @audit-info Context
 364 |  function _verifyParsedQuote(V3Struct.ParsedV3QuoteStruct memory v3quote)
 365 |      internal
 366 |      view
 367 |      returns (bool, bytes memory)
  :  |
     |          // @audit-issue `parsedQuoteCerts[0]` usage #1
 435 |          string memory parsedFmspc = parsedQuoteCerts[0].pck.sgxExtension.fmspc;
  :  |
     |          // @audit-issue `parsedQuoteCerts[0]` usage #2
 442 |          IPEMCertChainLib.ECSha256Certificate memory pckCert = parsedQuoteCerts[0];
  :  |
     |          // @audit-issue `parsedQuoteCerts[0]` usage #3
 454 |          (tcbVerified, tcbStatus) = _checkTcbLevels(parsedQuoteCerts[0].pck, fetchedTcbInfo);
  :  |
     |              // @audit-issue `parsedQuoteCerts[0]` usage #4
 472 |              parsedQuoteCerts[0].pubKey,
```
GitHub: [263](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L263), [268](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L268), [270](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L270), [271](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L271), [280](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L280), [280](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L280), [286](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L286), [286](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L286), [435](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L435), [442](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L442), [454](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L454), [472](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L472)


## [G-35] Nesting `if`-statements is cheaper than using `&&`

Nesting `if`-statements avoids the stack operations of setting up and using an extra `jumpdest`, and saves **6 [gas](https://gist.github.com/IllIllI000/7f3b818abecfadbef93b894481ae7d19)**

*Instances: 20*

```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

     |  // @audit-issue Consider using nested ifs instead of && to save gas
  85 |  if (!_allowZeroAddress && addr_ == address(0)) {
```
GitHub: [85](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L85)


```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

     |  // @audit-issue Consider using nested ifs instead of && to save gas
  42 |  if (msg.sender != owner() && msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();
```
GitHub: [42](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L42)


```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

     |  // @audit-issue Consider using nested ifs instead of && to save gas
 120 |  if (input.tip != 0 && block.coinbase != address(0)) {
```
GitHub: [120](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L120)


```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

     |  // @audit-issue Consider using nested ifs instead of && to save gas
 108 |  if (params.parentMetaHash != 0 && parentMetaHash != params.parentMetaHash) {

     |  // @audit-issue Consider using nested ifs instead of && to save gas
 164 |  if (_config.blobReuseEnabled && params.cacheBlobForReuse) {

     |  // @audit-issue Consider using nested ifs instead of && to save gas
 310 |  if (proposerOne != address(0) && msg.sender != proposerOne) {
```
GitHub: [108](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L108), [164](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L164), [310](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L310)


```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

     |  // @audit-issue Consider using nested ifs instead of && to save gas
 419 |  if (_tid == 1 && _ts.tier == 0 && inProvingWindow) {
```
GitHub: [419](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L419)


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

     |  // @audit-issue Consider using nested ifs instead of && to save gas
 141 |  if (!skipFeeCheck() && block.basefee != basefee) {

     |  // @audit-issue Consider using nested ifs instead of && to save gas
 275 |  if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {
```
GitHub: [141](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L141), [275](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L275)


```solidity
File: packages/protocol/contracts/signal/SignalService.sol

     |  // @audit-issue Consider using nested ifs instead of && to save gas
 285 |  if (cacheStateRoot && _isFullProof && !_isLastHop) {

     |  // @audit-issue Consider using nested ifs instead of && to save gas
 293 |  if (cacheSignalRoot && (_isFullProof || !_isLastHop)) {
```
GitHub: [285](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L285), [293](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L293)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

     |  // @audit-issue Consider using nested ifs instead of && to save gas
 250 |  if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) {

     |  // @audit-issue Consider using nested ifs instead of && to save gas
 260 |  if (_message.gasLimit == 0 && msg.sender != _message.destOwner) {

     |  // @audit-issue Consider using nested ifs instead of && to save gas
 439 |  } else if (block.chainid >= 32_300 && block.chainid <= 32_400) {

     |  // @audit-issue Consider using nested ifs instead of && to save gas
 490 |  if (
 491 |      _message.data.length >= 4 // msg can be empty
 492 |          && bytes4(_message.data) != IMessageInvocable.onMessageInvocation.selector
 493 |          && _message.to.isContract()
 494 |  ) {
```
GitHub: [250](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L250), [260](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L260), [439](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L439), [490-494](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L490-L494)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

     |  // @audit-issue Consider using nested ifs instead of && to save gas
  38 |  if (msg.sender != owner() && msg.sender != snapshooter) {
```
GitHub: [38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L38)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

     |  // @audit-issue Consider using nested ifs instead of && to save gas
  45 |  if (_migratingAddress == migratingAddress && _migratingInbound == migratingInbound) {
```
GitHub: [45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L45)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

     |  // @audit-issue Consider using nested ifs instead of && to save gas
  14 |  if (_in.length == 1 && uint8(_in[0]) < 128) {
```
GitHub: [14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L14)


```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

     |  // @audit-issue Consider using nested ifs instead of && to save gas
 277 |  if (_cliff > 0 && _cliff <= _start) revert INVALID_GRANT();
```
GitHub: [277](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L277)


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

     |  // @audit-issue Consider using nested ifs instead of && to save gas
 220 |  if (pceSvnIsHigherOrGreater && cpuSvnsAreHigherOrGreater) {
```
GitHub: [220](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L220)


## [G-36] Not using the named return variable is confusing and can waste gas

Consider changing the variable to be an unnamed one, since the variable is never assigned, nor is it returned by name. If the optimizer is not turned on, leaving the code as it is will also waste gas for the stack variable.

*Instances: 10*

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

     |  // @audit-issue Remove unused variable `maxBlocksToVerify_` to save gas
 100 |  returns (uint8 maxBlocksToVerify_)
```
GitHub: [100](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L100)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

     |  // @audit-issue Remove unused variable `invocationDelay_` to save gas
     |  // @audit-issue Remove unused variable `invocationExtraDelay_` to save gas
 421 |  returns (uint256 invocationDelay_, uint256 invocationExtraDelay_)
```
GitHub: [421](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L421), [421](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L421)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

     |  // @audit-issue Remove unused variable `offset_` to save gas
     |  // @audit-issue Remove unused variable `length_` to save gas
     |  // @audit-issue Remove unused variable `type_` to save gas
 147 |  returns (uint256 offset_, uint256 length_, RLPItemType type_)
```
GitHub: [147](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L147), [147](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L147), [147](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L147)


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

     |  // @audit-issue Remove unused variable `valid` to save gas
 130 |  returns (bool valid)
```
GitHub: [130](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L130)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

     |  // @audit-issue Remove unused variable `success` to save gas
 219 |  returns (bool success, bytes memory extracted, uint256 endIndex)
```
GitHub: [219](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L219)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

     |  // @audit-issue Remove unused variable `ret` to save gas
 188 |  function readUint8(bytes memory self, uint256 idx) internal pure returns (uint8 ret) {
```
GitHub: [188](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L188)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

     |  // @audit-issue Remove unused variable `sigValid` to save gas
 120 |  returns (bool sigValid)
```
GitHub: [120](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L120)


## [G-37] Only emit event in setter function if the state variable was changed

Emitting events in setter functions of smart contracts only when state variables change saves gas. This is because emitting events consumes gas, and unnecessary events, where no actual state change occurs, lead to wasteful consumption.

*Instances: 4*

```solidity
File: packages/protocol/contracts/common/AddressManager.sol

     |  // @audit-info Unvalidated: _newAddress
  38 |  function setAddress(
  39 |      uint64 _chainId,
  40 |      bytes32 _name,
  41 |      address _newAddress
  42 |  )
  43 |      external
  44 |      virtual
  45 |      onlyOwner
  :  |
     |      // @audit-issue Potentially redundant emit
  50 |      emit AddressSet(_chainId, _name, _newAddress, oldAddress);
```
GitHub: [50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L50)


```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

     |  // @audit-info Unvalidated: _minGuardians
  53 |  function setGuardians(
  54 |      address[] memory _newGuardians,
  55 |      uint8 _minGuardians
  56 |  )
  57 |      external
  58 |      onlyOwner
  59 |      nonReentrant
  :  |
     |      // @audit-issue Potentially redundant emit
  95 |      emit GuardiansUpdated(version, _newGuardians);
```
GitHub: [95](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L95)


```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

     |  // @audit-info Unvalidated: _newConfig, _newGasExcess
  25 |  function setConfigAndExcess(
  26 |      Config memory _newConfig,
  27 |      uint64 _newGasExcess
  28 |  )
  29 |      external
  30 |      virtual
  31 |      onlyOwner
  :  |
     |      // @audit-issue Potentially redundant emit
  39 |      emit ConfigAndExcessChanged(_newConfig, _newGasExcess);
```
GitHub: [39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L39)


```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

     |  // @audit-info Unvalidated: _ctoken, _btokenNew
 148 |  function changeBridgedToken(
 149 |      CanonicalERC20 calldata _ctoken,
 150 |      address _btokenNew
 151 |  )
 152 |      external
 153 |      nonReentrant
 154 |      whenNotPaused
 155 |      onlyOwner
 156 |      returns (address btokenOld_)
  :  |
     |      // @audit-issue Potentially redundant emit
 191 |      emit BridgedTokenChanged({
 192 |          srcChainId: _ctoken.chainId,
 193 |          ctoken: _ctoken.addr,
 194 |          btokenOld: btokenOld_,
 195 |          btokenNew: _btokenNew,
 196 |          ctokenSymbol: _ctoken.symbol,
 197 |          ctokenName: _ctoken.name,
 198 |          ctokenDecimal: _ctoken.decimals
 199 |      });
```
GitHub: [191-199](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L191-L199)


## [G-38] Operator `>=`/`<=` costs less gas than operator `>`/`<`

The compiler uses opcodes `GT` and `ISZERO` for solidity code that uses `>`, but only requires `LT` for `>=`, [which saves **3 gas**](https://gist.github.com/IllIllI000/3dc79d25acccfa16dee4e83ffdc6ffde). If `<` is being used, the condition can be inverted.

*Instances: 99*

```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

     |  // @audit-issue Switch > to >= and < to <=
  59 |  if (block.chainid > type(uint64).max) {
```
GitHub: [59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L59)


```solidity
File: packages/protocol/contracts/libs/LibMath.sol

     |  // @audit-issue Switch > to >= and < to <=
  13 |  return _a > _b ? _b : _a;

     |  // @audit-issue Switch > to >= and < to <=
  21 |  return _a > _b ? _a : _b;
```
GitHub: [13](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibMath.sol#L13), [21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibMath.sol#L21)


```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

     |  // @audit-issue Switch > to >= and < to <=
  82 |  block.timestamp > assignment.expiry

     |  // @audit-issue Switch > to >= and < to <=
  85 |  || assignment.maxBlockId != 0 && _meta.id > assignment.maxBlockId

     |  // @audit-issue Switch > to >= and < to <=
  86 |  || assignment.maxProposedIn != 0 && block.number > assignment.maxProposedIn

     |  // @audit-issue Switch > to >= and < to <=
 125 |  if (address(this).balance > 0) {

     |  // @audit-issue Switch > to >= and < to <=
 172 |  for (uint256 i; i < _tierFees.length; ++i) {
```
GitHub: [82](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L82), [85](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L85), [86](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L86), [125](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L125), [172](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L172)


```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

     |  // @audit-issue Switch > to >= and < to <=
  78 |  if (numPending < _config.ethDepositMinCountPerBlock) {

     |  // @audit-issue Switch > to >= and < to <=
  86 |  for (uint256 i; i < deposits_.length;) {

     |  // @audit-issue Switch > to >= and < to <=
  93 |  uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount;

     |  // @audit-issue Switch > to >= and < to <=
 140 |  && _state.slotA.numEthDeposits - _state.slotA.nextEthDepositToProcess
 141 |      < _config.ethDepositRingBufferSize - 1;

     |  // @audit-issue Switch > to >= and < to <=
 150 |  if (_amount > type(uint96).max) revert L1_INVALID_ETH_DEPOSIT();
```
GitHub: [78](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L78), [86](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L86), [93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L93), [140-141](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L140-L141), [150](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L150)


```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

     |  // @audit-issue Switch > to >= and < to <=
 171 |  if (uint256(params.txListByteOffset) + params.txListByteSize > MAX_BYTES_PER_BLOB) {

     |  // @audit-issue Switch > to >= and < to <=
 195 |  if (meta_.txListByteSize == 0 || meta_.txListByteSize > _config.blockMaxTxListBytes) {

     |  // @audit-issue Switch > to >= and < to <=
 244 |  for (uint256 i; i < params.hookCalls.length; ++i) {

     |  // @audit-issue Switch > to >= and < to <=
 296 |  return _state.reusableBlobs[_blobHash] + _config.blobExpiry > block.timestamp;
```
GitHub: [171](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L171), [195](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L195), [244](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L244), [296](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L296)


```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

     |  // @audit-issue Switch > to >= and < to <=
 134 |  if (_proof.tier == 0 || _proof.tier < _meta.minTier || _proof.tier < ts.tier) {

     |  // @audit-issue Switch > to >= and < to <=
 134 |  if (_proof.tier == 0 || _proof.tier < _meta.minTier || _proof.tier < ts.tier) {

     |  // @audit-issue Switch > to >= and < to <=
 192 |  bool returnLivenessBond = blk.livenessBond > 0 && _proof.data.length == 32

     |  // @audit-issue Switch > to >= and < to <=
 203 |  if (_proof.tier > ts.tier) {

     |  // @audit-issue Switch > to >= and < to <=
 381 |  if (reward > _tier.validityBond) {
```
GitHub: [134](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L134), [134](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L134), [192](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L192), [203](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L203), [381](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L381)


```solidity
File: packages/protocol/contracts/L1/libs/LibUtils.sol

     |  // @audit-issue Switch > to >= and < to <=
  34 |  if (_blockId < b.lastVerifiedBlockId || _blockId >= b.numBlocks) {
```
GitHub: [34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L34)


```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

     |  // @audit-issue Switch > to >= and < to <=
 127 |  while (blockId < b.numBlocks && numBlocksVerified < _maxBlocksToVerify) {

     |  // @audit-issue Switch > to >= and < to <=
 127 |  while (blockId < b.numBlocks && numBlocksVerified < _maxBlocksToVerify) {

     |  // @audit-issue Switch > to >= and < to <=
 152 |  uint256(ITierProvider(tierProvider).getTier(ts.tier).cooldownWindow) * 60
 153 |      + uint256(ts.timestamp).max(_state.slotB.lastUnpausedAt) > block.timestamp

     |  // @audit-issue Switch > to >= and < to <=
 212 |  if (numBlocksVerified > 0) {

     |  // @audit-issue Switch > to >= and < to <=
 238 |  if (_lastVerifiedBlockId > lastSyncedBlock + _config.blockSyncThreshold) {

     |  // @audit-issue Switch > to >= and < to <=
 251 |  || _config.blockMaxTxListBytes > 128 * 1024 // calldata up to 128K

     |  // @audit-issue Switch > to >= and < to <=
 256 |  || _config.ethDepositMaxCountPerBlock > 32

     |  // @audit-issue Switch > to >= and < to <=
 257 |  || _config.ethDepositMaxCountPerBlock < _config.ethDepositMinCountPerBlock

     |  // @audit-issue Switch > to >= and < to <=
 260 |  || _config.ethDepositMaxAmount > type(uint96).max || _config.ethDepositGas == 0

     |  // @audit-issue Switch > to >= and < to <=
 262 |  || _config.ethDepositMaxFee > type(uint96).max / _config.ethDepositMaxCountPerBlock
```
GitHub: [127](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L127), [127](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L127), [152-153](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L152-L153), [212](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L212), [238](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L238), [251](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L251), [256](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L256), [257](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L257), [260](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L260), [262](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L262)


```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

     |  // @audit-issue Switch > to >= and < to <=
  63 |  if (_newGuardians.length < MIN_NUM_GUARDIANS || _newGuardians.length > type(uint8).max) {

     |  // @audit-issue Switch > to >= and < to <=
  63 |  if (_newGuardians.length < MIN_NUM_GUARDIANS || _newGuardians.length > type(uint8).max) {

     |  // @audit-issue Switch > to >= and < to <=
  68 |  if (_minGuardians < (_newGuardians.length + 1) >> 1 || _minGuardians > _newGuardians.length)

     |  // @audit-issue Switch > to >= and < to <=
  68 |  if (_minGuardians < (_newGuardians.length + 1) >> 1 || _minGuardians > _newGuardians.length)

     |  // @audit-issue Switch > to >= and < to <=
  74 |  for (uint256 i; i < guardians.length; ++i) {

     |  // @audit-issue Switch > to >= and < to <=
  80 |  for (uint256 i = 0; i < _newGuardians.length; ++i) {

     |  // @audit-issue Switch > to >= and < to <=
 133 |  for (uint256 i; i < guardiansLength; ++i) {
```
GitHub: [63](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L63), [63](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L63), [68](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L68), [68](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L68), [74](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L74), [80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L80), [133](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L133)


```solidity
File: packages/protocol/contracts/L2/Lib1559Math.sol

     |  // @audit-issue Switch > to >= and < to <=
  42 |  if (input > LibFixedPointMath.MAX_EXP_INPUT) {
```
GitHub: [42](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/Lib1559Math.sol#L42)


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

     |  // @audit-issue Switch > to >= and < to <=
  82 |  if (block.chainid <= 1 || block.chainid > type(uint64).max) {

     |  // @audit-issue Switch > to >= and < to <=
 145 |  if (_l1BlockId > lastSyncedBlock + BLOCK_SYNC_THRESHOLD) {

     |  // @audit-issue Switch > to >= and < to <=
 234 |  for (uint256 i; i < 255 && _blockId >= i + 1; ++i) {

     |  // @audit-issue Switch > to >= and < to <=
 262 |  if (gasExcess > 0) {

     |  // @audit-issue Switch > to >= and < to <=
 275 |  if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {

     |  // @audit-issue Switch > to >= and < to <=
 275 |  if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {

     |  // @audit-issue Switch > to >= and < to <=
 279 |  if (numL1Blocks > 0) {

     |  // @audit-issue Switch > to >= and < to <=
 281 |  excess = excess > issuance ? excess - issuance : 1;
```
GitHub: [82](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L82), [145](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L145), [234](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L234), [262](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L262), [275](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L275), [275](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L275), [279](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L279), [281](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L281)


```solidity
File: packages/protocol/contracts/signal/SignalService.sol

     |  // @audit-issue Switch > to >= and < to <=
 104 |  for (uint256 i; i < hopProofs.length; ++i) {

     |  // @audit-issue Switch > to >= and < to <=
 120 |  bool isFullProof = hop.accountProof.length > 0;

     |  // @audit-issue Switch > to >= and < to <=
 247 |  if (topBlockId[_chainId][_kind] < _blockId) {
```
GitHub: [104](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L104), [120](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L120), [247](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L247)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

     |  // @audit-issue Switch > to >= and < to <=
  90 |  for (uint256 i; i < _msgHashes.length; ++i) {
```
GitHub: [90](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L90)


```solidity
File: packages/protocol/contracts/tokenvault/BaseNFTVault.sol

     |  // @audit-issue Switch > to >= and < to <=
 145 |  if (_op.tokenIds.length > MAX_TOKEN_PER_TXN) {
```
GitHub: [145](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L145)


```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

     |  // @audit-issue Switch > to >= and < to <=
  47 |  for (uint256 i; i < _op.amounts.length; ++i) {

     |  // @audit-issue Switch > to >= and < to <=
 251 |  for (uint256 i; i < _op.tokenIds.length; ++i) {

     |  // @audit-issue Switch > to >= and < to <=
 269 |  for (uint256 i; i < _op.tokenIds.length; ++i) {
```
GitHub: [47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L47), [251](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L251), [269](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L269)


```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

     |  // @audit-issue Switch > to >= and < to <=
  34 |  for (uint256 i; i < _op.tokenIds.length; ++i) {

     |  // @audit-issue Switch > to >= and < to <=
 170 |  for (uint256 i; i < _tokenIds.length; ++i) {

     |  // @audit-issue Switch > to >= and < to <=
 175 |  for (uint256 i; i < _tokenIds.length; ++i) {

     |  // @audit-issue Switch > to >= and < to <=
 197 |  for (uint256 i; i < _op.tokenIds.length; ++i) {

     |  // @audit-issue Switch > to >= and < to <=
 210 |  for (uint256 i; i < _op.tokenIds.length; ++i) {
```
GitHub: [34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L34), [170](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L170), [175](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L175), [197](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L197), [210](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L210)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

     |  // @audit-issue Switch > to >= and < to <=
  38 |  _in.length > 0,

     |  // @audit-issue Switch > to >= and < to <=
  74 |  while (offset < _in.length) {

     |  // @audit-issue Switch > to >= and < to <=
 153 |  _in.length > 0,

     |  // @audit-issue Switch > to >= and < to <=
 173 |  _in.length > strLen,

     |  // @audit-issue Switch > to >= and < to <=
 193 |  _in.length > lenOfStrLen,

     |  // @audit-issue Switch > to >= and < to <=
 213 |  strLen > 55,

     |  // @audit-issue Switch > to >= and < to <=
 218 |  _in.length > lenOfStrLen + strLen,

     |  // @audit-issue Switch > to >= and < to <=
 229 |  _in.length > listLen,

     |  // @audit-issue Switch > to >= and < to <=
 239 |  _in.length > lenOfListLen,

     |  // @audit-issue Switch > to >= and < to <=
 259 |  listLen > 55,

     |  // @audit-issue Switch > to >= and < to <=
 264 |  _in.length > lenOfListLen + listLen,
```
GitHub: [38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L38), [74](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L74), [153](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L153), [173](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L173), [193](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L193), [213](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L213), [218](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L218), [229](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L229), [239](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L239), [259](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L259), [264](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L264)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

     |  // @audit-issue Switch > to >= and < to <=
  14 |  if (_in.length == 1 && uint8(_in[0]) < 128) {

     |  // @audit-issue Switch > to >= and < to <=
  33 |  if (_len < 56) {

     |  // @audit-issue Switch > to >= and < to <=
  59 |  for (; i < 32; i++) {

     |  // @audit-issue Switch > to >= and < to <=
  66 |  for (uint256 j = 0; j < out_.length; j++) {
```
GitHub: [14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L14), [33](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L33), [59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L59), [66](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

     |  // @audit-issue Switch > to >= and < to <=
  77 |  require(_key.length > 0, "MerkleTrie: empty key");

     |  // @audit-issue Switch > to >= and < to <=
  85 |  for (uint256 i = 0; i < proof.length; i++) {

     |  // @audit-issue Switch > to >= and < to <=
 120 |  value_.length > 0,

     |  // @audit-issue Switch > to >= and < to <=
 173 |  value_.length > 0,

     |  // @audit-issue Switch > to >= and < to <=
 208 |  for (uint256 i = 0; i < length;) {

     |  // @audit-issue Switch > to >= and < to <=
 221 |  id_ = _node.length < 32 ? RLPReader.readRawBytes(_node) : RLPReader.readBytes(_node);

     |  // @audit-issue Switch > to >= and < to <=
 243 |  uint256 max = (_a.length < _b.length) ? _a.length : _b.length;

     |  // @audit-issue Switch > to >= and < to <=
 244 |  for (; shared_ < max && _a[shared_] == _b[shared_];) {
```
GitHub: [77](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L77), [85](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85), [120](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L120), [173](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L173), [208](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L208), [221](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L221), [243](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L243), [244](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L244)


```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

     |  // @audit-issue Switch > to >= and < to <=
 104 |  for (uint256 i; i < _ids.length; ++i) {

     |  // @audit-issue Switch > to >= and < to <=
 210 |  for (uint256 i; i < _instances.length; ++i) {
```
GitHub: [104](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L104), [210](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

     |  // @audit-issue Switch > to >= and < to <=
  40 |  if (claimEnd > block.timestamp || claimEnd + withdrawalWindow < block.timestamp) {

     |  // @audit-issue Switch > to >= and < to <=
  40 |  if (claimEnd > block.timestamp || claimEnd + withdrawalWindow < block.timestamp) {

     |  // @audit-issue Switch > to >= and < to <=
 114 |  if (block.timestamp < claimEnd) return (balance, 0);
```
GitHub: [40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L40), [40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L40), [114](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L114)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

     |  // @audit-issue Switch > to >= and < to <=
  59 |  for (uint256 i; i < tokenIds.length; ++i) {
```
GitHub: [59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59)


```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

     |  // @audit-issue Switch > to >= and < to <=
  35 |  merkleRoot == 0x0 || claimStart == 0 || claimEnd == 0 || claimStart > block.timestamp

     |  // @audit-issue Switch > to >= and < to <=
  36 |  || claimEnd < block.timestamp
```
GitHub: [35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L35), [36](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L36)


```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

     |  // @audit-issue Switch > to >= and < to <=
 275 |  if (_cliff > 0) revert INVALID_GRANT();

     |  // @audit-issue Switch > to >= and < to <=
 277 |  if (_cliff > 0 && _cliff <= _start) revert INVALID_GRANT();
```
GitHub: [275](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L275), [277](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L277)


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

     |  // @audit-issue Switch > to >= and < to <=
  80 |  for (uint256 i; i < serialNumBatch.length; ++i) {

     |  // @audit-issue Switch > to >= and < to <=
  95 |  for (uint256 i; i < serialNumBatch.length; ++i) {

     |  // @audit-issue Switch > to >= and < to <=
 191 |  for (uint256 i; i < enclaveId.tcbLevels.length; ++i) {

     |  // @audit-issue Switch > to >= and < to <=
 214 |  for (uint256 i; i < tcb.tcbLevels.length; ++i) {
```
GitHub: [80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L80), [95](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L95), [191](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L191), [214](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L214)


## [G-39] Public functions not used internally can be marked as external to save gas

Public functions that aren't used internally in Solidity contracts should be made external to optimize gas usage and improve contract efficiency. External functions can only be called from outside the contract, and their arguments are directly read from the calldata, which is more gas-efficient than loading them into memory, as is the case for public functions. By using external visibility, developers can reduce gas consumption for external calls and ensure that the contract operates more cost-effectively for users. Moreover, setting the appropriate visibility level for functions also enhances code readability and maintainability, promoting a more secure and well-structured contract design. 

*Instances: 69*

```solidity
File: packages/protocol/contracts/common/AddressManager.sol

     |  // @audit-info Context
  10 |  contract AddressManager is EssentialContract, IAddressManager {
  :  |
     |      // @audit-issue Not called internally by this contract
  54 |      function getAddress(uint64 _chainId, bytes32 _name) public view override returns (address) {
```
GitHub: [54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L54)


```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

     |  // @audit-info Context
  11 |  abstract contract AddressResolver is IAddressResolver, Initializable {
  :  |
     |      // @audit-issue Not called internally by this contract
  43 |      function resolve(
  44 |          uint64 _chainId,
  45 |          bytes32 _name,
  46 |          bool _allowZeroAddress
  47 |      )
  48 |          public
  49 |          view
  50 |          virtual
  51 |          returns (address payable)
```
GitHub: [43-52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L43-L52)


```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

     |  // @audit-info Context
  10 |  abstract contract EssentialContract is UUPSUpgradeable, Ownable2StepUpgradeable, AddressResolver {
  :  |
     |      // @audit-issue Not called internally by this contract
  69 |      function pause() public virtual whenNotPaused {
  :  |
     |      // @audit-issue Not called internally by this contract
  78 |      function unpause() public virtual whenPaused {
```
GitHub: [69](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L69), [78](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L78)


```solidity
File: packages/protocol/contracts/L1/gov/TaikoGovernor.sol

     |  // @audit-info Context
  16 |  contract TaikoGovernor is
  :  |
     |      // @audit-issue Not called internally by this contract
  48 |      function propose(
  49 |          address[] memory _targets,
  50 |          uint256[] memory _values,
  51 |          bytes[] memory _calldatas,
  52 |          string memory _description
  53 |      )
  54 |          public
  55 |          override(IGovernorUpgradeable, GovernorUpgradeable, GovernorCompatibilityBravoUpgradeable)
  56 |          returns (uint256)
  :  |
     |      // @audit-issue Not called internally by this contract
  69 |      function propose(
  70 |          address[] memory _targets,
  71 |          uint256[] memory _values,
  72 |          string[] memory _signatures,
  73 |          bytes[] memory _calldatas,
  74 |          string memory _description
  75 |      )
  76 |          public
  77 |          virtual
  78 |          override(GovernorCompatibilityBravoUpgradeable)
  79 |          returns (uint256)
  :  |
     |      // @audit-issue Not called internally by this contract
  89 |      function supportsInterface(bytes4 _interfaceId)
  90 |          public
  91 |          view
  92 |          override(GovernorUpgradeable, GovernorTimelockControlUpgradeable, IERC165Upgradeable)
  93 |          returns (bool)
  :  |
     |      // @audit-issue Not called internally by this contract
  99 |      function state(uint256 _proposalId)
 100 |          public
 101 |          view
 102 |          override(IGovernorUpgradeable, GovernorUpgradeable, GovernorTimelockControlUpgradeable)
 103 |          returns (ProposalState)
  :  |
     |      // @audit-issue Not called internally by this contract
 111 |      function votingDelay() public pure override returns (uint256) {
  :  |
     |      // @audit-issue Not called internally by this contract
 117 |      function votingPeriod() public pure override returns (uint256) {
  :  |
     |      // @audit-issue Not called internally by this contract
 123 |      function proposalThreshold() public pure override returns (uint256) {
```
GitHub: [48-57](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L48-L57), [69-80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L69-L80), [89-94](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L89-L94), [99-104](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L99-L104), [111](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L111), [117](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L117), [123](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L123)


```solidity
File: packages/protocol/contracts/L1/gov/TaikoTimelockController.sol

     |  // @audit-info Context
   9 |  contract TaikoTimelockController is EssentialContract, TimelockControllerUpgradeable {
  :  |
     |      // @audit-issue Not called internally by this contract
  24 |      function getMinDelay() public view override returns (uint256) {
```
GitHub: [24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L24)


```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

     |  // @audit-info Context
   9 |  abstract contract Guardians is EssentialContract {
  :  |
     |      // @audit-issue Not called internally by this contract
 101 |      function isApproved(bytes32 _hash) public view returns (bool) {
  :  |
     |      // @audit-issue Not called internally by this contract
 107 |      function numGuardians() public view returns (uint256) {
```
GitHub: [101](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L101), [107](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L107)


```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

     |  // @audit-info Context
  22 |  contract TaikoL1 is EssentialContract, ITaikoL1, TaikoEvents, TaikoErrors {
  :  |
     |      // @audit-issue Not called internally by this contract
 124 |      function unpause() public override {
  :  |
     |      // @audit-issue Not called internally by this contract
 132 |      function canDepositEthToL2(uint256 _amount) public view returns (bool) {
  :  |
     |      // @audit-issue Not called internally by this contract
 137 |      function isBlobReusable(bytes32 _blobHash) public view returns (bool) {
  :  |
     |      // @audit-issue Not called internally by this contract
 145 |      function getBlock(uint64 _blockId)
 146 |          public
 147 |          view
 148 |          returns (TaikoData.Block memory blk_, TaikoData.TransitionState memory ts_)
  :  |
     |      // @audit-issue Not called internally by this contract
 162 |      function getTransition(
 163 |          uint64 _blockId,
 164 |          bytes32 _parentHash
 165 |      )
 166 |          public
 167 |          view
 168 |          returns (TaikoData.TransitionState memory)
  :  |
     |      // @audit-issue Not called internally by this contract
 176 |      function getStateVariables()
 177 |          public
 178 |          view
 179 |          returns (TaikoData.SlotA memory a_, TaikoData.SlotB memory b_)
```
GitHub: [124](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L124), [132](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L132), [137](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L137), [145-149](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L145-L149), [162-169](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L162-L169), [176-180](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L176-L180)


```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

     |  // @audit-info Context
  15 |  contract TaikoToken is EssentialContract, ERC20SnapshotUpgradeable, ERC20VotesUpgradeable {
  :  |
     |      // @audit-issue Not called internally by this contract
  25 |      function init(
  26 |          address _owner,
  27 |          string calldata _name,
  28 |          string calldata _symbol,
  29 |          address _recipient
  30 |      )
  31 |          public
  32 |          initializer
  :  |
     |      // @audit-issue Not called internally by this contract
  47 |      function burn(address _from, uint256 _amount) public onlyOwner {
  :  |
     |      // @audit-issue Not called internally by this contract
  52 |      function snapshot() public onlyFromOwnerOrNamed("snapshooter") {
  :  |
     |      // @audit-issue Not called internally by this contract
  60 |      function transfer(address _to, uint256 _amount) public override returns (bool) {
  :  |
     |      // @audit-issue Not called internally by this contract
  70 |      function transferFrom(
  71 |          address _from,
  72 |          address _to,
  73 |          uint256 _amount
  74 |      )
  75 |          public
  76 |          override
  77 |          returns (bool)
```
GitHub: [25-33](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L25-L33), [47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L47), [52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L52), [60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L60), [70-78](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L70-L78)


```solidity
File: packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol

     |  // @audit-info Context
  10 |  contract DevnetTierProvider is EssentialContract, ITierProvider {
  :  |
     |      // @audit-issue Not called internally by this contract
  20 |      function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {
  :  |
     |      // @audit-issue Not called internally by this contract
  47 |      function getTierIds() public pure override returns (uint16[] memory tiers_) {
  :  |
     |      // @audit-issue Not called internally by this contract
  54 |      function getMinTier(uint256) public pure override returns (uint16) {
```
GitHub: [20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L20), [47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L47), [54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L54)


```solidity
File: packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol

     |  // @audit-info Context
  10 |  contract MainnetTierProvider is EssentialContract, ITierProvider {
  :  |
     |      // @audit-issue Not called internally by this contract
  20 |      function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {
  :  |
     |      // @audit-issue Not called internally by this contract
  58 |      function getTierIds() public pure override returns (uint16[] memory tiers_) {
  :  |
     |      // @audit-issue Not called internally by this contract
  66 |      function getMinTier(uint256 _rand) public pure override returns (uint16) {
```
GitHub: [20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L20), [58](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L58), [66](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L66)


```solidity
File: packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol

     |  // @audit-info Context
  10 |  contract TestnetTierProvider is EssentialContract, ITierProvider {
  :  |
     |      // @audit-issue Not called internally by this contract
  20 |      function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {
  :  |
     |      // @audit-issue Not called internally by this contract
  58 |      function getTierIds() public pure override returns (uint16[] memory tiers_) {
  :  |
     |      // @audit-issue Not called internally by this contract
  66 |      function getMinTier(uint256 _rand) public pure override returns (uint16) {
```
GitHub: [20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L20), [58](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L58), [66](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L66)


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

     |  // @audit-info Context
  21 |  contract TaikoL2 is CrossChainOwned {
  :  |
     |      // @audit-issue Not called internally by this contract
 185 |      function getBasefee(
 186 |          uint64 _l1BlockId,
 187 |          uint32 _parentGasUsed
 188 |      )
 189 |          public
 190 |          view
 191 |          returns (uint256 basefee_)
  :  |
     |      // @audit-issue Not called internally by this contract
 200 |      function getBlockHash(uint64 _blockId) public view returns (bytes32) {
```
GitHub: [185-192](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L185-L192), [200](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L200)


```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

     |  // @audit-info Context
   9 |  contract TaikoL2EIP1559Configurable is TaikoL2 {
  :  |
     |      // @audit-issue Not called internally by this contract
  43 |      function getConfig() public view override returns (Config memory) {
```
GitHub: [43](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L43)


```solidity
File: packages/protocol/contracts/signal/SignalService.sol

     |  // @audit-info Context
  14 |  contract SignalService is EssentialContract, ISignalService {
  :  |
     |      // @audit-issue Not called internally by this contract
  83 |      function proveSignalReceived(
  84 |          uint64 _chainId,
  85 |          address _app,
  86 |          bytes32 _signal,
  87 |          bytes calldata _proof
  88 |      )
  89 |          public
  90 |          virtual
  91 |          validSender(_app)
  92 |          nonZeroValue(_signal)
  :  |
     |      // @audit-issue Not called internally by this contract
 137 |      function isChainDataSynced(
 138 |          uint64 _chainId,
 139 |          bytes32 _kind,
 140 |          uint64 _blockId,
 141 |          bytes32 _chainData
 142 |      )
 143 |          public
 144 |          view
 145 |          nonZeroValue(_chainData)
 146 |          returns (bool)
  :  |
     |      // @audit-issue Not called internally by this contract
 153 |      function isSignalSent(address _app, bytes32 _signal) public view returns (bool) {
  :  |
     |      // @audit-issue Not called internally by this contract
 158 |      function getSyncedChainData(
 159 |          uint64 _chainId,
 160 |          bytes32 _kind,
 161 |          uint64 _blockId
 162 |      )
 163 |          public
 164 |          view
 165 |          returns (uint64 blockId_, bytes32 chainData_)
```
GitHub: [83-93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L83-L93), [137-147](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L137-L147), [153](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L153), [158-166](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L158-L166)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

     |  // @audit-info Context
  16 |  contract Bridge is EssentialContract, IBridge {
  :  |
     |      // @audit-issue Not called internally by this contract
 340 |      function isMessageSent(Message calldata _message) public view returns (bool) {
  :  |
     |      // @audit-issue Not called internally by this contract
 352 |      function proveMessageFailed(
 353 |          Message calldata _message,
 354 |          bytes calldata _proof
 355 |      )
 356 |          public
 357 |          view
 358 |          returns (bool)
  :  |
     |      // @audit-issue Not called internally by this contract
 374 |      function proveMessageReceived(
 375 |          Message calldata _message,
 376 |          bytes calldata _proof
 377 |      )
 378 |          public
 379 |          view
 380 |          returns (bool)
  :  |
     |      // @audit-issue Not called internally by this contract
 403 |      function context() public view returns (Context memory ctx_) {
```
GitHub: [340](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L340), [352-359](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L352-L359), [374-381](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L374-L381), [403](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L403)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

     |  // @audit-info Context
  15 |  contract BridgedERC20 is
  :  |
     |      // @audit-issue Not called internally by this contract
  91 |      function name()
  92 |          public
  93 |          view
  94 |          override(ERC20Upgradeable, IERC20MetadataUpgradeable)
  95 |          returns (string memory)
  :  |
     |      // @audit-issue Not called internally by this contract
 102 |      function symbol()
 103 |          public
 104 |          view
 105 |          override(ERC20Upgradeable, IERC20MetadataUpgradeable)
 106 |          returns (string memory)
  :  |
     |      // @audit-issue Not called internally by this contract
 113 |      function decimals()
 114 |          public
 115 |          view
 116 |          override(ERC20Upgradeable, IERC20MetadataUpgradeable)
 117 |          returns (uint8)
  :  |
     |      // @audit-issue Not called internally by this contract
 125 |      function canonical() public view returns (address, uint256) {
```
GitHub: [91-96](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L91-L96), [102-107](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L102-L107), [113-118](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L113-L118), [125](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L125)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

     |  // @audit-info Context
   9 |  abstract contract BridgedERC20Base is EssentialContract, IBridgedERC20 {
  :  |
     |      // @audit-issue Not called internally by this contract
  57 |      function mint(address _account, uint256 _amount) public nonReentrant whenNotPaused {
  :  |
     |      // @audit-issue Not called internally by this contract
  75 |      function burn(address _account, uint256 _amount) public nonReentrant whenNotPaused {
  :  |
     |      // @audit-issue Not called internally by this contract
  93 |      function owner() public view override(IBridgedERC20, OwnableUpgradeable) returns (address) {
```
GitHub: [57](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L57), [75](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L75), [93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L93)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

     |  // @audit-info Context
  12 |  contract BridgedERC721 is EssentialContract, ERC721Upgradeable {
  :  |
     |      // @audit-issue Not called internally by this contract
  54 |      function mint(
  55 |          address _account,
  56 |          uint256 _tokenId
  57 |      )
  58 |          public
  59 |          nonReentrant
  60 |          whenNotPaused
  61 |          onlyFromNamed("erc721_vault")
  :  |
     |      // @audit-issue Not called internally by this contract
  69 |      function burn(
  70 |          address _account,
  71 |          uint256 _tokenId
  72 |      )
  73 |          public
  74 |          nonReentrant
  75 |          whenNotPaused
  76 |          onlyFromNamed("erc721_vault")
  :  |
     |      // @audit-issue Not called internally by this contract
  87 |      function name() public view override(ERC721Upgradeable) returns (string memory) {
  :  |
     |      // @audit-issue Not called internally by this contract
  93 |      function symbol() public view override(ERC721Upgradeable) returns (string memory) {
  :  |
     |      // @audit-issue Not called internally by this contract
 100 |      function source() public view returns (address, uint256) {
  :  |
     |      // @audit-issue Not called internally by this contract
 107 |      function tokenURI(uint256 _tokenId) public view virtual override returns (string memory) {
```
GitHub: [54-62](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L54-L62), [69-77](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L69-L77), [87](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L87), [93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L93), [100](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L100), [107](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L107)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

     |  // @audit-info Context
  14 |  contract BridgedERC1155 is EssentialContract, IERC1155MetadataURIUpgradeable, ERC1155Upgradeable {
  :  |
     |      // @audit-issue Not called internally by this contract
  66 |      function mint(
  67 |          address _to,
  68 |          uint256 _tokenId,
  69 |          uint256 _amount
  70 |      )
  71 |          public
  72 |          nonReentrant
  73 |          whenNotPaused
  74 |          onlyFromNamed("erc1155_vault")
  :  |
     |      // @audit-issue Not called internally by this contract
  83 |      function mintBatch(
  84 |          address _to,
  85 |          uint256[] memory _tokenIds,
  86 |          uint256[] memory _amounts
  87 |      )
  88 |          public
  89 |          nonReentrant
  90 |          whenNotPaused
  91 |          onlyFromNamed("erc1155_vault")
  :  |
     |      // @audit-issue Not called internally by this contract
 100 |      function burn(
 101 |          address _account,
 102 |          uint256 _tokenId,
 103 |          uint256 _amount
 104 |      )
 105 |          public
 106 |          nonReentrant
 107 |          whenNotPaused
 108 |          onlyFromNamed("erc1155_vault")
  :  |
     |      // @audit-issue Not called internally by this contract
 115 |      function name() public view returns (string memory) {
  :  |
     |      // @audit-issue Not called internally by this contract
 121 |      function symbol() public view returns (string memory) {
```
GitHub: [66-75](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L66-L75), [83-92](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L83-L92), [100-109](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L100-L109), [115](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L115), [121](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L121)


```solidity
File: packages/protocol/contracts/tokenvault/BaseVault.sol

     |  // @audit-info Context
  12 |  abstract contract BaseVault is
  :  |
     |      // @audit-issue Not called internally by this contract
  39 |      function supportsInterface(bytes4 _interfaceId) public view virtual override returns (bool) {
```
GitHub: [39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L39)


```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

     |  // @audit-info Context
  29 |  contract ERC1155Vault is BaseNFTVault, ERC1155ReceiverUpgradeable {
  :  |
     |      // @audit-issue Not called internally by this contract
 192 |      function supportsInterface(bytes4 interfaceId)
 193 |          public
 194 |          view
 195 |          virtual
 196 |          override(BaseVault, ERC1155ReceiverUpgradeable)
 197 |          returns (bool)
```
GitHub: [192-198](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L192-L198)


```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

     |  // @audit-info Context
  25 |  contract TimelockTokenPool is EssentialContract {
  :  |
     |      // @audit-issue Not called internally by this contract
 204 |      function getMyGrant(address _recipient) public view returns (Grant memory) {
```
GitHub: [204](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L204)


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

     |  // @audit-info Context
  22 |  contract AutomataDcapV3Attestation is IAttestation {
  :  |
     |      // @audit-issue Not called internally by this contract
 103 |      function configureTcbInfoJson(
 104 |          string calldata fmspc,
 105 |          TCBInfoStruct.TCBInfo calldata tcbInfoInput
 106 |      )
 107 |          public
 108 |          onlyOwner
```
GitHub: [103-109](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L103-L109)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

     |  // @audit-info Context
  15 |  contract SigVerifyLib is ISigVerifyLib {
  :  |
     |      // @audit-issue Not called internally by this contract
  24 |      function verifyAttStmtSignature(
  25 |          bytes memory tbs,
  26 |          bytes memory signature,
  27 |          PublicKey memory publicKey,
  28 |          Algorithm alg
  29 |      )
  30 |          public
  31 |          view
  32 |          returns (bool)
  :  |
     |      // @audit-issue Not called internally by this contract
  54 |      function verifyCertificateSignature(
  55 |          bytes memory tbs,
  56 |          bytes memory signature,
  57 |          PublicKey memory publicKey,
  58 |          CertSigAlgorithm alg
  59 |      )
  60 |          public
  61 |          view
  62 |          returns (bool)
```
GitHub: [24-33](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L24-L33), [54-63](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L54-L63)


## [G-40] Reduce deployment gas costs by fine-tuning IPFS file hashes

Solc [currently by default](https://docs.soliditylang.org/en/v0.8.23/metadata.html#encoding-of-the-metadata-hash-in-the-bytecode) appends the IPFS hash (in CID v0) of the canonical metadata file and the compiler version to the end of the bytecode. This value is variable-length [CBOR-encoded](https://tools.ietf.org/html/rfc7049) i.e. it can be optimized in order to reduce deployment gas costs. See [this article] for more information (https://www.rareskills.io/post/solidity-metadata).
                    
*Note:* multiple contracts in the same file will share the same hash.

*Instances: 87*

```solidity
File: packages/protocol/contracts/common/IAddressManager.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmZZEmQww2DMyCQ6v7nqAKwun4XjRvgUXtfkbUTJ2cZkty
   7 |  interface IAddressManager {
```
GitHub: [7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/IAddressManager.sol#L7)


```solidity
File: packages/protocol/contracts/common/AddressManager.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmeuSMVRKNN2eBk6LDng28u3rvJKUSCpQ7SPffXVhCtXzE
  10 |  contract AddressManager is EssentialContract, IAddressManager {
```
GitHub: [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L10)


```solidity
File: packages/protocol/contracts/common/IAddressResolver.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmSmGCW2zvjueMUpoVmyC4BdEyHVns4TCd3GLfMjyoCcch
  13 |  interface IAddressResolver {
```
GitHub: [13](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/IAddressResolver.sol#L13)


```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmTQAGYWaSgHX6AS8b4QfidEUMEhKiZdy3vXVuD1i7ghaP
  11 |  abstract contract AddressResolver is IAddressResolver, Initializable {
```
GitHub: [11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L11)


```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/Qmc2pakVtiuJU7okgvRjcutsJAv5VgDXqszAdJufa6gfzV
  10 |  abstract contract EssentialContract is UUPSUpgradeable, Ownable2StepUpgradeable, AddressResolver {
```
GitHub: [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L10)


```solidity
File: packages/protocol/contracts/libs/Lib4844.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmYJHSoc1dJEvvjzbXnRTanNrE7mnjD1YiaxuB7664Dw5U
   8 |  library Lib4844 {
```
GitHub: [8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/Lib4844.sol#L8)


```solidity
File: packages/protocol/contracts/libs/LibAddress.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmcA1deThnLvsqDATug5ggNpHWbgCs85ZnRniot6KDVxv6
  13 |  library LibAddress {
```
GitHub: [13](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L13)


```solidity
File: packages/protocol/contracts/libs/LibMath.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmX48SmLEp3vFi8BfxyqWob8fLJTZhCkHG3wSSQhddFcvJ
   7 |  library LibMath {
```
GitHub: [7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibMath.sol#L7)


```solidity
File: packages/protocol/contracts/libs/LibTrieProof.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmUEGbXmjjsV9YTGh94RzoqksfPZgpbMpPfqffQBecMUTm
  15 |  library LibTrieProof {
```
GitHub: [15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibTrieProof.sol#L15)


```solidity
File: packages/protocol/contracts/L1/gov/TaikoGovernor.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmcvZafhZEh9SN5FsYcYwHEuySuK26EfeVeJhxqBVa1Gxz
  16 |  contract TaikoGovernor is
```
GitHub: [16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L16)


```solidity
File: packages/protocol/contracts/L1/gov/TaikoTimelockController.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmNxZfgqkfVxPyKWnLCDzx52sN3ynpqbwo7BxaktusXPXi
   9 |  contract TaikoTimelockController is EssentialContract, TimelockControllerUpgradeable {
```
GitHub: [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L9)


```solidity
File: packages/protocol/contracts/L1/hooks/IHook.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmQmn4wCEKJTZ7LF2hHixDN9rUMghqvSTDidahjYVmEgNw
   8 |  interface IHook {
```
GitHub: [8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/IHook.sol#L8)


```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmWLJxx6c5nEyo15poofZozDAo5Gp9QNHzGVWRYUmmb3R8
  14 |  contract AssignmentHook is EssentialContract, IHook {
```
GitHub: [14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L14)


```solidity
File: packages/protocol/contracts/L1/ITaikoL1.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmXeJZugspP4cUDgXThQcpFqyxr5sPGPGDHunfbBtfbUsN
   8 |  interface ITaikoL1 {
```
GitHub: [8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/ITaikoL1.sol#L8)


```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmTTCpt9pDMHt97zXbnVNTRQAmQW6bNsi1eWQAb7tiDF24
  12 |  library LibDepositing {
```
GitHub: [12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L12)


```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmZbtFSRWZZk84y1ikSKZ9FZgGcXUuZ57R2DH9xGjfangx
  15 |  library LibProposing {
```
GitHub: [15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L15)


```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmRzxEj8DgcQ9FJViNBgRsv1FrDKbkugvAWWh81CscnbBq
  16 |  library LibProving {
```
GitHub: [16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L16)


```solidity
File: packages/protocol/contracts/L1/libs/LibUtils.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmXoGHZL5x7fjxH932A2VAjaUHpZ1SUStfobVJ2pvw5GwX
   9 |  library LibUtils {
```
GitHub: [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L9)


```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmPwZiUqC5KtTrHmZMqJEwZ1gHPkRLtehHuWmhHS8Z7Hx5
  16 |  library LibVerifying {
```
GitHub: [16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L16)


```solidity
File: packages/protocol/contracts/L1/provers/GuardianProver.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmShcpCW3tdWaTfhbJofeRwSgpHf5hebCRwsVqNwSGxe9b
  10 |  contract GuardianProver is Guardians {
```
GitHub: [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/GuardianProver.sol#L10)


```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmR9N61frFBi117JZ6yfhjEMhKo9LsR5AzPg9Jz7Zz8kyy
   9 |  abstract contract Guardians is EssentialContract {
```
GitHub: [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L9)


```solidity
File: packages/protocol/contracts/L1/TaikoData.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmZXxtrfcrDPR7rf4oEs6hYNkTeffdr8kApGj4mHsFGgoJ
   8 |  library TaikoData {
```
GitHub: [8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L8)


```solidity
File: packages/protocol/contracts/L1/TaikoErrors.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmeRrGSxMq2m2oMMaH1UpC9hRwo8s8XdsemGnJRX6rkJX4
  11 |  abstract contract TaikoErrors {
```
GitHub: [11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L11)


```solidity
File: packages/protocol/contracts/L1/TaikoEvents.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmRSo69XfkjzpZFpa2q27deAaP5twXoauESqMc1h43BZ4K
  13 |  abstract contract TaikoEvents {
```
GitHub: [13](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoEvents.sol#L13)


```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmRniDh4rJGtkMAqEFeEAEjeWk1nJAtPZYbLjyXjznDhdw
  22 |  contract TaikoL1 is EssentialContract, ITaikoL1, TaikoEvents, TaikoErrors {
```
GitHub: [22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L22)


```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmZmAAHEdUWxQU7tFHwztmX6JzY2XA5bc1wpB9KEL92k87
  15 |  contract TaikoToken is EssentialContract, ERC20SnapshotUpgradeable, ERC20VotesUpgradeable {
```
GitHub: [15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L15)


```solidity
File: packages/protocol/contracts/L1/tiers/ITierProvider.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmX9p3h2Zv5tHGugnejijAiiAxmxwcKWmjoLsaU3mPsqk3
   7 |  interface ITierProvider {

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmX9p3h2Zv5tHGugnejijAiiAxmxwcKWmjoLsaU3mPsqk3
  37 |  library LibTiers {
```
GitHub: [7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L7), [37](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L37)


```solidity
File: packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmTy3LVuE44uYWgY1tU69twJgBn2BbmVNoQx8VU9KH8vLn
  10 |  contract DevnetTierProvider is EssentialContract, ITierProvider {
```
GitHub: [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L10)


```solidity
File: packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmNPByoYtWi9GoLKuUB6XKihCKyBPNuDJ3vgRoQHWcPN4a
  10 |  contract MainnetTierProvider is EssentialContract, ITierProvider {
```
GitHub: [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L10)


```solidity
File: packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmPkZQ7EXe8netjMg9uMG7v7KxJnj6w3RLZRLx76Vx9P9t
  10 |  contract TestnetTierProvider is EssentialContract, ITierProvider {
```
GitHub: [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L10)


```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmZSwGxQSg8KcYhG2sG8XoWwL1r32HRaPAV8YjLMV2ueJ9
  14 |  abstract contract CrossChainOwned is EssentialContract, IMessageInvocable {
```
GitHub: [14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L14)


```solidity
File: packages/protocol/contracts/L2/Lib1559Math.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmQtvFDhP8tSziQ7VSeZDXdHwK4cwZRVAxZuZqpD4w5FbE
  10 |  library Lib1559Math {
```
GitHub: [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/Lib1559Math.sol#L10)


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmTVaKTNdWqeu4as1wsMh7LYcQZiEs2rzyQsq8W9pspF6y
  21 |  contract TaikoL2 is CrossChainOwned {
```
GitHub: [21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L21)


```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmXAh2i1mj2UcDcrgNW5yt4MgHPrVpuLoC3LYLuxGPczEj
   9 |  contract TaikoL2EIP1559Configurable is TaikoL2 {
```
GitHub: [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L9)


```solidity
File: packages/protocol/contracts/signal/ISignalService.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmWx6KUackmWzG1oQ55hPVivp6XPbXX6DLR18RBU5bxW7s
  12 |  interface ISignalService {
```
GitHub: [12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/ISignalService.sol#L12)


```solidity
File: packages/protocol/contracts/signal/LibSignals.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/Qmdgz9fB2ydD9p2yVEg9VVGCtnJ2vWuX6hNyp15ow84xwG
   6 |  library LibSignals {
```
GitHub: [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/LibSignals.sol#L6)


```solidity
File: packages/protocol/contracts/signal/SignalService.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmTfQu9LqmnTUygdTbmKqh3SNVj5VbeuS4bAVYfErNhtbQ
  14 |  contract SignalService is EssentialContract, ISignalService {
```
GitHub: [14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L14)


```solidity
File: packages/protocol/contracts/bridge/IBridge.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmVPP51pub6D1CpCrchVcTFZUYhw7Cv5HFPKZCudSBwx3C
   8 |  interface IBridge {

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmVPP51pub6D1CpCrchVcTFZUYhw7Cv5HFPKZCudSBwx3C
 160 |  interface IRecallableSender {

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmVPP51pub6D1CpCrchVcTFZUYhw7Cv5HFPKZCudSBwx3C
 174 |  interface IMessageInvocable {
```
GitHub: [8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/IBridge.sol#L8), [160](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/IBridge.sol#L160), [174](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/IBridge.sol#L174)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmQQDRN5abJa9EpuWCACvxV9cb73TPk4H6TgjusgmpRDiY
  16 |  contract Bridge is EssentialContract, IBridge {
```
GitHub: [16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L16)


```solidity
File: packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmUQH48GVArNnmG13eGcgmQpC9bsoU99WVGKx65DZ1jAJN
   8 |  interface IUSDC {

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmUQH48GVArNnmG13eGcgmQpC9bsoU99WVGKx65DZ1jAJN
  28 |  contract USDCAdapter is BridgedERC20Base {
```
GitHub: [8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L8), [28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L28)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmdoQ2ismXNphbtqLxsZtuL31fsHNM48XxSWHj6P6caPwK
  15 |  contract BridgedERC20 is
```
GitHub: [15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L15)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmcbhHFVcPLHZF5LBwLW3NyS7A1HXREVJubbRwLvQBrEM1
   9 |  abstract contract BridgedERC20Base is EssentialContract, IBridgedERC20 {
```
GitHub: [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L9)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmcwsURFRjWJtz9Nw81p5dfAcxKhQJnq3SbgXmtxkicTbN
  12 |  contract BridgedERC721 is EssentialContract, ERC721Upgradeable {
```
GitHub: [12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L12)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmUMjpZon2wDLSFJDNqQMtu6fQ3NTMNcp1wKskWgL9u146
  14 |  contract BridgedERC1155 is EssentialContract, IERC1155MetadataURIUpgradeable, ERC1155Upgradeable {
```
GitHub: [14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L14)


```solidity
File: packages/protocol/contracts/tokenvault/BaseNFTVault.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmNvtFWM18QLRsg5UfPjSfsm79N8AtvrLzSHzgCNPfaMj4
   9 |  abstract contract BaseNFTVault is BaseVault {
```
GitHub: [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L9)


```solidity
File: packages/protocol/contracts/tokenvault/BaseVault.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmYdV9ikxW5QSXeScbrUVZ7fT7ztaryev8sWDMfZmvhC6H
  12 |  abstract contract BaseVault is
```
GitHub: [12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L12)


```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmNtVfV9xXGoi8ahgtvAYRqn4LsGXywGt4AWDzUP2XGUB2
  16 |  interface IERC1155NameAndSymbol {

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmNtVfV9xXGoi8ahgtvAYRqn4LsGXywGt4AWDzUP2XGUB2
  29 |  contract ERC1155Vault is BaseNFTVault, ERC1155ReceiverUpgradeable {
```
GitHub: [16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L16), [29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L29)


```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmerZd1UXiXQNhMWGRK6zvyWnw4KK8TJhtV8VcNvpBm14w
  18 |  contract ERC20Vault is BaseVault {
```
GitHub: [18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L18)


```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmbmuFn9fTvsyHZG45R2SBcvT4qrD7arFCAibk1TSuG47M
  16 |  contract ERC721Vault is BaseNFTVault, IERC721Receiver {
```
GitHub: [16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L16)


```solidity
File: packages/protocol/contracts/tokenvault/IBridgedERC20.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmVG4zv3kMaaTizA16rUJprLBdJM9G6YxmFZx7jqo8t3vg
  10 |  interface IBridgedERC20 {
```
GitHub: [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/IBridgedERC20.sol#L10)


```solidity
File: packages/protocol/contracts/tokenvault/LibBridgedToken.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmZAGYNCue5vV5quQHQPZETTjApS71dzARkVFhs3GRduVJ
   8 |  library LibBridgedToken {
```
GitHub: [8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L8)


```solidity
File: packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmddxXH1AqaAL1woupF55aUcSUneSjp4jiGNzzX1aX7giq
   5 |  library ExcessivelySafeCall {
```
GitHub: [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L5)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/Bytes.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmQR6JBrWZfRRqw7QVqBp9rMSFczKzLVKSmvVpC8W2xpkA
   6 |  library Bytes {
```
GitHub: [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L6)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmS27Hh6sJHtWbMBhPdP131usExWQ29oBayEackLY81mkE
   9 |  library RLPReader {
```
GitHub: [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L9)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmZQ47LY91DsiFiFAiqMtAHNAusF2X7KH3pWLJSBzRFgty
   9 |  library RLPWriter {
```
GitHub: [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L9)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmS3kjFX4Umaz84aVsBdf8sD1S7mnjFMA8pZGYx4DcUa6Y
  11 |  library MerkleTrie {
```
GitHub: [11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L11)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmbD2WhvHS5CSaPP2zNqtum5JK9mbHkHuypwNkvvPhFPXE
   9 |  library SecureMerkleTrie {
```
GitHub: [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L9)


```solidity
File: packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmZ2d7g6sSCpGYNQ2hZStv7auA5pd5Wr8EXpsS2Ro1zLRG
   6 |  library LibFixedPointMath {
```
GitHub: [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L6)


```solidity
File: packages/protocol/contracts/verifiers/IVerifier.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmRJLqszAspjMuHTsDwqVmT1nQkPkgEbqdQ8xgnX2U2o31
   9 |  interface IVerifier {
```
GitHub: [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/IVerifier.sol#L9)


```solidity
File: packages/protocol/contracts/verifiers/GuardianVerifier.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmbozPBZCJW5o2iE1XN1SoeW72g9SqePPjRuXgtJSdhHGi
  10 |  contract GuardianVerifier is EssentialContract, IVerifier {
```
GitHub: [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L10)


```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmQGdnTHZi4h8SmehkUvY5uW8MCJWakqe9n2FW1swWSeMF
  19 |  contract SgxVerifier is EssentialContract, IVerifier {
```
GitHub: [19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L19)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmPQ39dMEFUpdXJfu5u7bkveQ4kW1ujHGAov6XKK6baPpJ
  11 |  contract ERC20Airdrop is MerkleClaimable {
```
GitHub: [11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L11)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmcQ6i3m7rg6Wt6E8hZgxv5UHBZVAt7RGossEwRnnLki9F
  12 |  contract ERC20Airdrop2 is MerkleClaimable {
```
GitHub: [12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L12)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmRCAiN1xF3Pbf6KFPonNNDJV6d44ByRF1HHmsaD3A7TsT
   9 |  contract ERC721Airdrop is MerkleClaimable {
```
GitHub: [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L9)


```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmPCH1kaCB7Pny4xQzoLFnkk7X3WXour9ZqTrWWDCY4Ja3
  10 |  abstract contract MerkleClaimable is EssentialContract {
```
GitHub: [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L10)


```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmVPHCXpahwp5e6tUh5tTU5EMWPfPYoN3UzzAuGnxqF87z
  25 |  contract TimelockTokenPool is EssentialContract {
```
GitHub: [25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L25)


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmWq3H8nKvGQDg8spGRWY8v1cfXdb8pqX1NvMGmSbRT4a2
  22 |  contract AutomataDcapV3Attestation is IAttestation {
```
GitHub: [22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L22)


```solidity
File: packages/protocol/contracts/automata-attestation/interfaces/IAttestation.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/Qmbi9eeHsTDAaNAKtj1KRyK5WWRQuvP7qSpwZ1vG37EKvq
   8 |  interface IAttestation {
```
GitHub: [8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/interfaces/IAttestation.sol#L8)


```solidity
File: packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmPbgPBDSHBr3DcXu1MAJWVwGnXydBJrwoPsMX12pEUHBu
   6 |  interface ISigVerifyLib {
```
GitHub: [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L6)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/EnclaveIdStruct.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmUv1gu2NskE1S7C4HuSXYDD2RQ8kicATVuhck8otE8wDM
   6 |  library EnclaveIdStruct {
```
GitHub: [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/EnclaveIdStruct.sol#L6)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmbwmCEpibVaKWHT9MieXkJmEZj97Pjjr7TbuPHEAWPK8m
   6 |  interface IPEMCertChainLib {
```
GitHub: [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L6)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmVo2FL4z6P2YJQNr4BzqNWdiwRQikJyYJHHYkkLkXWUXu
  12 |  contract PEMCertChainLib is IPEMCertChainLib {
```
GitHub: [12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L12)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmembRTf1AqTkYYcfMcUABBeZtPTWrkDw4QuYLssiHqHG1
  11 |  library V3Parser {
```
GitHub: [11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L11)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmYtg8a4swicPgoapb28u71MHVmL2mqx2oD27u2NgeQfVY
   6 |  library V3Struct {
```
GitHub: [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L6)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmVuSF5KoBsVsHsVJvVWGxUSuEB9zsRmHRoBBPMoNA3SWJ
   6 |  library TCBInfoStruct {
```
GitHub: [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol#L6)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmZ3HVEMCtknPBUHTLdqiYcceVpzHuutxoqWPuSdP5zjhd
  12 |  library NodePtr {

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmZ3HVEMCtknPBUHTLdqiYcceVpzHuutxoqWPuSdP5zjhd
  38 |  library Asn1Decode {
```
GitHub: [12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L12), [38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L38)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmUciXGfqRSHCnMJ5P7z4TEMyrA6JEqjLgN6beqsP7ebeU
   8 |  library BytesUtils {
```
GitHub: [8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L8)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmNySDy15CnX29PKbasLk5kegBHMjVpL4n7YrsU5AGoNuw
  34 |  library RsaVerify {
```
GitHub: [34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L34)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/SHA1.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmRDvE6jW41AG42DAyeLYsDCHnrkw2ARrCri5iFukxUvgG
  10 |  library SHA1 {
```
GitHub: [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SHA1.sol#L10)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmX4NcUNrhFMZ2Dhsxyy58TAvrD8MorotJTUhqBfXapASF
  15 |  contract SigVerifyLib is ISigVerifyLib {
```
GitHub: [15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L15)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

     |  // @audit-issue IPFS hash is dweb:/ipfs/QmdksjR7NxJajXFDxzmstyxcEhG3Mn7ukXqHbcTeVqY8FL
   7 |  library X509DateUtils {
```
GitHub: [7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L7)


## [G-41] Redundant state variable getters

Getters for public state variables are automatically generated so there is no need to code them manually and lose gas

*Instances: 1*

```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

  43 |  function getConfig() public view override returns (Config memory) {
  44 |      return customConfig;
  45 |  }
```
GitHub: [43-45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L43-L45)


## [G-42] Redundant type conversion

Casting a variable to its own type is redundant and a waste of gas.

*Instances: 1*

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

     |  // @audit-issue `bytes1(encoded[i])` is a redundant type cast
 154 |  uint256 digits = uint256(uint8(bytes1(encoded[i])));
```
GitHub: [154](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L154)


## [G-43] Refactor modifiers to call a local function

Modifiers code is copied in all instances where it's used, increasing bytecode size. If deployment gas costs are a concern for this contract, refactoring modifiers into functions can reduce bytecode size significantly at the cost of one JUMP.

*Instances: 15*

```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

     |  // @audit-issue Refactor to a function to save gas
  24 |  modifier onlyFromNamed(bytes32 _name) {
```
GitHub: [24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L24)


```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

     |  // @audit-issue Refactor to a function to save gas
  41 |  modifier onlyFromOwnerOrNamed(bytes32 _name) {

     |  // @audit-issue Refactor to a function to save gas
  46 |  modifier nonReentrant() {

     |  // @audit-issue Refactor to a function to save gas
  53 |  modifier whenPaused() {

     |  // @audit-issue Refactor to a function to save gas
  58 |  modifier whenNotPaused() {
```
GitHub: [41](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L41), [46](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L46), [53](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L53), [58](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L58)


```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

     |  // @audit-issue Refactor to a function to save gas
  28 |  modifier whenProvingNotPaused() {
```
GitHub: [28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L28)


```solidity
File: packages/protocol/contracts/signal/SignalService.sol

     |  // @audit-issue Refactor to a function to save gas
  35 |  modifier validSender(address _app) {

     |  // @audit-issue Refactor to a function to save gas
  40 |  modifier nonZeroValue(bytes32 _input) {
```
GitHub: [35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L35), [40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L40)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

     |  // @audit-issue Refactor to a function to save gas
  64 |  modifier sameChain(uint64 _chainId) {
```
GitHub: [64](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L64)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

     |  // @audit-issue Refactor to a function to save gas
  37 |  modifier onlyOwnerOrSnapshooter() {
```
GitHub: [37](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L37)


```solidity
File: packages/protocol/contracts/tokenvault/BaseNFTVault.sol

     |  // @audit-issue Refactor to a function to save gas
 140 |  modifier withValidOperation(BridgeTransferOp memory _op) {
```
GitHub: [140](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L140)


```solidity
File: packages/protocol/contracts/tokenvault/BaseVault.sol

     |  // @audit-issue Refactor to a function to save gas
  22 |  modifier onlyFromBridge() {
```
GitHub: [22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L22)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

     |  // @audit-issue Refactor to a function to save gas
  39 |  modifier ongoingWithdrawals() {
```
GitHub: [39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L39)


```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

     |  // @audit-issue Refactor to a function to save gas
  33 |  modifier ongoingClaim() {
```
GitHub: [33](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L33)


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

     |  // @audit-issue Refactor to a function to save gas
  60 |  modifier onlyOwner() {
```
GitHub: [60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L60)


## [G-44] Remove empty functions to save gas

Empty function body in solidity is not recommended, removing it can not only save deployment gas but save execution gas in the function selector code by shifting other functions up.

*Instances: 4*

```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

     |  // @audit-issue Consider removing this empty function
 114 |  function _authorizeUpgrade(address) internal virtual override onlyOwner { }

     |  // @audit-issue Consider removing this empty function
 116 |  function _authorizePause(address) internal virtual onlyOwner { }
```
GitHub: [114](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L114), [116](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L116)


```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

     |  // @audit-issue Consider removing this empty function
 220 |  function _authorizePause(address)
 221 |      internal
 222 |      view
 223 |      virtual
 224 |      override
 225 |      onlyFromOwnerOrNamed("chain_pauser")
 226 |  { }
```
GitHub: [220-226](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L220-L226)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

     |  // @audit-issue Consider removing this empty function
 461 |  function _authorizePause(address)
 462 |      internal
 463 |      view
 464 |      virtual
 465 |      override
 466 |      onlyFromOwnerOrNamed("bridge_pauser")
 467 |  { }
```
GitHub: [461-467](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L461-L467)


## [G-45] Replace OpenZeppelin components with Solady equivalents to save gas

The following OpenZeppelin imports have a [Solady](https://github.com/Vectorized/solady/tree/main) equivalent, as such they can be used to save GAS as Solady modules have been specifically designed to be as GAS efficient as possible.

*Instances: 10*

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

     |  // @audit-issue Consider using the Solady implementation
   4 |  import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```
GitHub: [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L4)


```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

     |  // @audit-issue Consider using the Solady implementation
   4 |  import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```
GitHub: [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L4)


```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

     |  // @audit-issue Consider using the Solady implementation
   4 |  import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```
GitHub: [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L4)


```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

     |  // @audit-issue Consider using the Solady implementation
   4 |  import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```
GitHub: [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L4)


```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

     |  // @audit-issue Consider using the Solady implementation
   4 |  import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```
GitHub: [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L4)


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

     |  // @audit-issue Consider using the Solady implementation
   4 |  import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```
GitHub: [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L4)


```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

     |  // @audit-issue Consider using the Solady implementation
   4 |  import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```
GitHub: [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L4)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

     |  // @audit-issue Consider using the Solady implementation
   4 |  import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```
GitHub: [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L4)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

     |  // @audit-issue Consider using the Solady implementation
   4 |  import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```
GitHub: [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L4)


```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

     |  // @audit-issue Consider using the Solady implementation
   5 |  import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```
GitHub: [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L5)


## [G-46] Same cast is done multiple times

It's cheaper to do it once, and store the result to a variable.

*Instances: 19*

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

     |  // @audit-info Contains redundant type conversions
  47 |  function init(
  48 |      TaikoData.State storage _state,
  49 |      TaikoData.Config memory _config,
  50 |      bytes32 _genesisBlockHash
  51 |  )
  52 |      external
  :  |
     |      // @audit-issue Cache this type conversion result that is used in multiple locations
  58 |      _state.slotA.genesisTimestamp = uint64(block.timestamp);
  :  |
     |      // @audit-issue Cache this type conversion result that is used in multiple locations
  64 |      blk.proposedAt = uint64(block.timestamp);
  :  |
     |      // @audit-issue Cache this type conversion result that is used in multiple locations
  71 |      ts.timestamp = uint64(block.timestamp);
```
GitHub: [58](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L58), [64](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L64), [71](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L71)


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

     |  // @audit-info Contains redundant type conversions
 163 |  function withdraw(
 164 |      address _token,
 165 |      address _to
 166 |  )
 167 |      external
 168 |      onlyFromOwnerOrNamed("withdrawer")
 169 |      nonReentrant
 170 |      whenNotPaused
  :  |
     |          // @audit-issue Cache this type conversion result that is used in multiple locations
     |          // @audit-issue Cache this type conversion result that is used in multiple locations
 176 |          IERC20(_token).safeTransfer(_to, IERC20(_token).balanceOf(address(this)));
```
GitHub: [176](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L176), [176](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L176)


```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

     |  // @audit-info Contains redundant type conversions
 148 |  function changeBridgedToken(
 149 |      CanonicalERC20 calldata _ctoken,
 150 |      address _btokenNew
 151 |  )
 152 |      external
 153 |      nonReentrant
 154 |      whenNotPaused
 155 |      onlyOwner
 156 |      returns (address btokenOld_)
  :  |
     |      // @audit-issue Cache this type conversion result that is used in multiple locations
 164 |      if (IBridgedERC20(_btokenNew).owner() != owner()) {
  :  |
     |          // @audit-issue Cache this type conversion result that is used in multiple locations
 185 |          IBridgedERC20(_btokenNew).changeMigrationStatus(btokenOld_, true);
```
GitHub: [164](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L164), [185](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L185)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

     |  // @audit-info Contains redundant type conversions
  32 |  function _writeLength(uint256 _len, uint256 _offset) private pure returns (bytes memory out_) {
  :  |
     |          // @audit-issue Cache this type conversion result that is used in multiple locations
  35 |          out_[0] = bytes1(uint8(_len) + uint8(_offset));
  :  |
     |          // @audit-issue Cache this type conversion result that is used in multiple locations
  45 |          out_[0] = bytes1(uint8(lenLen) + uint8(_offset) + 55);
```
GitHub: [35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L35), [45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L45)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

     |  // @audit-info Contains redundant type conversions
 341 |  function _findTcb(
 342 |      bytes memory der,
 343 |      uint256 oidPtr
 344 |  )
 345 |      private
 346 |      pure
 347 |      returns (bool success, uint256 pcesvn, uint256[] memory cpusvns)
  :  |
     |              // @audit-issue Cache this type conversion result that is used in multiple locations
 359 |              ? uint16(bytes2(svnValueBytes)) / 256
     |              // @audit-issue Cache this type conversion result that is used in multiple locations
 360 |              : uint16(bytes2(svnValueBytes));
  :  |
     |              // @audit-issue Cache this type conversion result that is used in multiple locations
 359 |              ? uint16(bytes2(svnValueBytes)) / 256
     |              // @audit-issue Cache this type conversion result that is used in multiple locations
 360 |              : uint16(bytes2(svnValueBytes));
  :  |
     |              // @audit-issue Cache this type conversion result that is used in multiple locations
 363 |              pcesvn = uint256(svnValue);
  :  |
     |              // @audit-issue Cache this type conversion result that is used in multiple locations
 366 |              uint256 cpusvn = uint256(svnValue);
```
GitHub: [359](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L359), [360](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L360), [359](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L359), [360](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L360), [363](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L363), [366](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L366)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

     |  // @audit-info Contains redundant type conversions
 187 |  function _readNodeLength(bytes memory der, uint256 ix) private pure returns (uint256) {
  :  |
     |          // @audit-issue Cache this type conversion result that is used in multiple locations
 194 |          ixLastContentByte = uint80(ixFirstContentByte + length - 1);
  :  |
     |          // @audit-issue Cache this type conversion result that is used in multiple locations
 207 |          ixLastContentByte = uint80(ixFirstContentByte + length - 1);
```
GitHub: [194](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L194), [207](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L207)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

     |  // @audit-info Contains redundant type conversions
   8 |  function toTimestamp(bytes memory x509Time) internal pure returns (uint256) {
  :  |
     |          // @audit-issue Cache this type conversion result that is used in multiple locations
  18 |          if (uint8(x509Time[0]) - 48 < 5) yrs += 2000;
  :  |
     |          // @audit-issue Cache this type conversion result that is used in multiple locations
  21 |          yrs += (uint8(x509Time[0]) - 48) * 1000 + (uint8(x509Time[1]) - 48) * 100;
```
GitHub: [18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L18), [21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L21)


## [G-47] Simple checks for zero can be done using assembly to save gas

Using assembly for simple zero checks on unsigned integers can save gas due to lower-level, optimized operations. 

*Instances: 81*

```solidity
File: packages/protocol/contracts/libs/LibTrieProof.sol

  46 |  if (_accountProof.length != 0) {

  50 |  if (rlpAccount.length == 0) revert LTP_INVALID_ACCOUNT_PROOF();
```
GitHub: [46](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibTrieProof.sol#L46), [50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibTrieProof.sol#L50)


```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

  85 |  || assignment.maxBlockId != 0 && _meta.id > assignment.maxBlockId

  86 |  || assignment.maxProposedIn != 0 && block.number > assignment.maxProposedIn

 120 |  if (input.tip != 0 && block.coinbase != address(0)) {
```
GitHub: [85](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L85), [86](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L86), [120](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L120)


```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

 135 |  blobUsed: _txList.length == 0,

 185 |  if (params.txListByteOffset != 0) {

 195 |  if (meta_.txListByteSize == 0 || meta_.txListByteSize > _config.blockMaxTxListBytes) {

 260 |  if (address(this).balance != 0) {
```
GitHub: [135](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L135), [185](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L185), [195](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L195), [260](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L260)


```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

 134 |  if (_proof.tier == 0 || _proof.tier < _meta.minTier || _proof.tier < ts.tier) {

 164 |  bool isContesting = _proof.tier == ts.tier && tier.contestBond != 0;

 186 |  bool isTopTier = tier.contestBond == 0;

 223 |  assert(tier.validityBond == 0);

 224 |  assert(ts.validityBond == 0 && ts.contestBond == 0 && ts.contester == address(0));

 224 |  assert(ts.validityBond == 0 && ts.contestBond == 0 && ts.contester == address(0));

 280 |  if (tid_ == 0) {

 412 |  if (_tier.contestBond == 0) return;

 419 |  if (_tid == 1 && _ts.tier == 0 && inProvingWindow) {
```
GitHub: [134](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L134), [164](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L164), [186](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L186), [223](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L223), [224](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L224), [224](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L224), [280](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L280), [412](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L412), [419](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L419)


```solidity
File: packages/protocol/contracts/L1/libs/LibUtils.sol

  43 |  if (tid == 0) revert L1_TRANSITION_NOT_FOUND();
```
GitHub: [43](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L43)


```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

  93 |  if (_maxBlocksToVerify == 0) {

 111 |  if (tid == 0) revert L1_TRANSITION_ID_ZERO();

 137 |  if (tid == 0) break;

 250 |  || _config.blockMaxGasLimit == 0 || _config.blockMaxTxListBytes == 0

 250 |  || _config.blockMaxGasLimit == 0 || _config.blockMaxTxListBytes == 0

 252 |  || _config.livenessBond == 0 || _config.ethDepositRingBufferSize <= 1

 253 |  || _config.ethDepositMinCountPerBlock == 0

 258 |  || _config.ethDepositMinAmount == 0

 260 |  || _config.ethDepositMaxAmount > type(uint96).max || _config.ethDepositGas == 0

 261 |  || _config.ethDepositMaxFee == 0
```
GitHub: [93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L93), [111](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L111), [137](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L137), [250](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L250), [250](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L250), [252](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L252), [253](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L253), [258](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L258), [260](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L260), [261](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L261)


```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

  84 |  if (guardianIds[guardian] != 0) revert INVALID_GUARDIAN_SET();

 113 |  if (id == 0) revert INVALID_GUARDIAN();
```
GitHub: [84](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L84), [113](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L113)


```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

 153 |  if (blk_.verifiedTransitionId != 0) {
```
GitHub: [153](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L153)


```solidity
File: packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol

  68 |  if (_rand % 1000 == 0) return LibTiers.TIER_SGX_ZKVM;
```
GitHub: [68](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L68)


```solidity
File: packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol

  68 |  if (_rand % 10 == 0) return LibTiers.TIER_SGX;
```
GitHub: [68](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L68)


```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

  70 |  if (_ownerChainId == 0 || _ownerChainId == block.chainid) {
```
GitHub: [70](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L70)


```solidity
File: packages/protocol/contracts/L2/Lib1559Math.sol

  24 |  if (_adjustmentFactor == 0) {
```
GitHub: [24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/Lib1559Math.sol#L24)


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

  86 |  if (block.number == 0) {

 117 |  _l1BlockHash == 0 || _l1StateRoot == 0 || _l1BlockId == 0

 118 |  || (block.number != 1 && _parentGasUsed == 0)

 296 |  if (basefee_ == 0) basefee_ = 1;
```
GitHub: [86](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L86), [117](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L117), [118](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L118), [296](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L296)


```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

  33 |  if (_newConfig.gasTargetPerL1Block == 0) revert L2_INVALID_CONFIG();

  34 |  if (_newConfig.basefeeAdjustmentQuotient == 0) revert L2_INVALID_CONFIG();
```
GitHub: [33](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L33), [34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L34)


```solidity
File: packages/protocol/contracts/signal/SignalService.sol

  95 |  if (hopProofs.length == 0) revert SS_EMPTY_PROOF();

 114 |  if (hop.chainId == 0 || hop.chainId == block.chainid) {

 167 |  blockId_ = _blockId != 0 ? _blockId : topBlockId[_chainId][_kind];

 169 |  if (blockId_ != 0) {
```
GitHub: [95](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L95), [114](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L114), [167](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L167), [169](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L169)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 169 |  bool isMessageProven = receivedAt != 0;

 231 |  bool isMessageProven = receivedAt != 0;

 242 |  if (invocationDelay != 0) {

 245 |  preferredExecutor: _message.gasLimit == 0 ? _message.destOwner : msg.sender

 250 |  if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) {

 260 |  if (_message.gasLimit == 0 && msg.sender != _message.destOwner) {

 321 |  if (_message.gasLimit == 0 || _isLastAttempt) {

 485 |  if (_gasLimit == 0) revert B_INVALID_GAS_LIMIT();
```
GitHub: [169](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L169), [231](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L231), [242](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L242), [245](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L245), [250](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L250), [260](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L260), [321](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L321), [485](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L485)


```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

  48 |  if (_op.amounts[i] == 0) revert VAULT_INVALID_AMOUNT();
```
GitHub: [48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L48)


```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

 214 |  if (_op.amount == 0) revert VAULT_INVALID_AMOUNT();
```
GitHub: [214](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L214)


```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

  35 |  if (_op.amounts[i] != 0) revert VAULT_INVALID_AMOUNT();
```
GitHub: [35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L35)


```solidity
File: packages/protocol/contracts/tokenvault/LibBridgedToken.sol

  21 |  _srcToken == address(0) || _srcChainId == 0 || _srcChainId == block.chainid

  22 |  || bytes(_symbol).length == 0 || bytes(_name).length == 0

  22 |  || bytes(_symbol).length == 0 || bytes(_name).length == 0
```
GitHub: [21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L21), [22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L22), [22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L22)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

 287 |  if (_length == 0) {
```
GitHub: [287](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L287)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

  39 |  while (_len / i != 0) {
```
GitHub: [39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L39)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

  91 |  if (currentKeyIndex == 0) {
```
GitHub: [91](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L91)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

 111 |  if (balance == 0) return (0, 0);
```
GitHub: [111](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L111)


```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

  35 |  merkleRoot == 0x0 || claimStart == 0 || claimEnd == 0 || claimStart > block.timestamp

  35 |  merkleRoot == 0x0 || claimStart == 0 || claimEnd == 0 || claimStart > block.timestamp
```
GitHub: [35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L35), [35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L35)


```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

 137 |  if (recipients[_recipient].grant.amount != 0) revert ALREADY_GRANTED();

 154 |  if (amountVoided == 0) revert NOTHING_TO_VOID();

 255 |  if (_amount == 0) return 0;

 256 |  if (_start == 0) return _amount;

 259 |  if (_period == 0) return _amount;

 268 |  if (_grant.amount == 0) revert INVALID_GRANT();

 274 |  if (_start == 0 || _period == 0) {

 274 |  if (_start == 0 || _period == 0) {
```
GitHub: [137](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L137), [154](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L154), [255](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L255), [256](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L256), [259](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L259), [268](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L268), [274](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L274), [274](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L274)


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

 421 |  bool isPckCert = i == 0; // additional parsing for PCKCert
```
GitHub: [421](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L421)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

 286 |  while (tbsPtr != 0) {
```
GitHub: [286](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L286)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

  96 |  if (diff != 0) {

 345 |  if (len % 8 == 0) {
```
GitHub: [96](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L96), [345](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L345)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

  72 |  if (year % 4 != 0) return false;

  73 |  if (year % 100 != 0) return true;

  74 |  if (year % 400 != 0) return false;
```
GitHub: [72](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L72), [73](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L73), [74](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L74)


## [G-48] Split `revert` checks to save gas

Splitting logical `&&` (and)/`||` (or) conditions into two separate checks will save 2 gas.

*Instances: 7*

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

  81 |  if (
  82 |      block.timestamp > assignment.expiry
  83 |          || assignment.metaHash != 0 && _blk.metaHash != assignment.metaHash
  84 |          || assignment.parentMetaHash != 0 && _meta.parentMetaHash != assignment.parentMetaHash
  85 |          || assignment.maxBlockId != 0 && _meta.id > assignment.maxBlockId
  86 |          || assignment.maxProposedIn != 0 && block.number > assignment.maxProposedIn
  87 |  ) {
  88 |      revert HOOK_ASSIGNMENT_EXPIRED();
  89 |  }
```
GitHub: [81-89](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L81-L89)


```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

 105 |  if (_tran.parentHash == 0 || _tran.blockHash == 0 || _tran.stateRoot == 0) {
 106 |      revert L1_INVALID_TRANSITION();
 107 |  }

 134 |  if (_proof.tier == 0 || _proof.tier < _meta.minTier || _proof.tier < ts.tier) {
 135 |      revert L1_INVALID_TIER();
 136 |  }
```
GitHub: [105-107](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L105-L107), [134-136](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L134-L136)


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

 116 |  if (
 117 |      _l1BlockHash == 0 || _l1StateRoot == 0 || _l1BlockId == 0
 118 |          || (block.number != 1 && _parentGasUsed == 0)
 119 |  ) {
 120 |      revert L2_INVALID_PARAM();
 121 |  }
```
GitHub: [116-121](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L116-L121)


```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

 174 |  if (
 175 |      ctoken.decimals != _ctoken.decimals
 176 |          || keccak256(bytes(ctoken.symbol)) != keccak256(bytes(_ctoken.symbol))
 177 |          || keccak256(bytes(ctoken.name)) != keccak256(bytes(_ctoken.name))
 178 |  ) revert VAULT_CTOKEN_MISMATCH();
```
GitHub: [174-178](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L174-L178)


```solidity
File: packages/protocol/contracts/tokenvault/LibBridgedToken.sol

  20 |  if (
  21 |      _srcToken == address(0) || _srcChainId == 0 || _srcChainId == block.chainid
  22 |          || bytes(_symbol).length == 0 || bytes(_name).length == 0
  23 |  ) {
  24 |      revert BTOKEN_INVALID_PARAMS();
  25 |  }
```
GitHub: [20-25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L20-L25)


```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

  34 |  if (
  35 |      merkleRoot == 0x0 || claimStart == 0 || claimEnd == 0 || claimStart > block.timestamp
  36 |          || claimEnd < block.timestamp
  37 |  ) revert CLAIM_NOT_ONGOING();
```
GitHub: [34-37](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L34-L37)


## [G-49] Splitting `require()` statements that use `&&` saves gas

See [this issue](https://github.com/code-423n4/2022-01-xdefi-findings/issues/128) which describes the fact that there is a larger deployment gas cost, but with enough runtime calls, the change ends up being cheaper by **3 gas**.

*Instances: 4*

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

  77 |  require(
  78 |      localEnclaveReport.reserved3.length == 96 && localEnclaveReport.reserved4.length == 60
  79 |          && localEnclaveReport.reportData.length == 64,
  80 |      "local QE report has wrong length"
  81 |  );

  82 |  require(
  83 |      pckSignedQeReport.reserved3.length == 96 && pckSignedQeReport.reserved4.length == 60
  84 |          && pckSignedQeReport.reportData.length == 64,
  85 |      "QE report has wrong length"
  86 |  );

  94 |  require(
  95 |      v3Quote.v3AuthData.ecdsa256BitSignature.length == 64
  96 |          && v3Quote.v3AuthData.ecdsaAttestationKey.length == 64
  97 |          && v3Quote.v3AuthData.qeReportSignature.length == 64,
  98 |      "Invalid ECDSA signature format"
  99 |  );
```
GitHub: [77-81](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L77-L81), [82-86](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L82-L86), [94-99](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L94-L99)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

 335 |  require(char >= 0x30 && char <= 0x7A, "invalid char");
```
GitHub: [335](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L335)


## [G-50] Stack variable is only used once

If the variable is only accessed once, it's cheaper to use the assigned value directly that one time, and save the **3 gas** the extra stack assignment would spend.

*Instances: 99*

```solidity
File: packages/protocol/contracts/libs/Lib4844.sol

     |  // @audit-issue Used once: _commitment
  34 |  bytes1[48] memory _commitment,
     |  // @audit-issue Used once: _pointProof
  35 |  bytes1[48] memory _pointProof
  :  |
     |  // @audit-issue Used once: ret
  43 |  (bool ok, bytes memory ret) = POINT_EVALUATION_PRECOMPILE_ADDRESS.staticcall(
```
GitHub: [34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/Lib4844.sol#L34), [35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/Lib4844.sol#L35), [43](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/Lib4844.sol#L43)


```solidity
File: packages/protocol/contracts/libs/LibTrieProof.sol

     |  // @audit-issue Used once: _storageProof
  40 |  bytes[] memory _storageProof
  :  |
     |      // @audit-issue Used once: accountState
  52 |      RLPReader.RLPItem[] memory accountState = RLPReader.readList(rlpAccount);
```
GitHub: [40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibTrieProof.sol#L40), [52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibTrieProof.sol#L52)


```solidity
File: packages/protocol/contracts/L1/gov/TaikoGovernor.sol

     |  // @audit-issue Used once: _targets
  49 |  address[] memory _targets,
     |  // @audit-issue Used once: _values
  50 |  uint256[] memory _values,
     |  // @audit-issue Used once: _calldatas
  51 |  bytes[] memory _calldatas,
     |  // @audit-issue Used once: _description
  52 |  string memory _description

     |  // @audit-issue Used once: _targets
  70 |  address[] memory _targets,
     |  // @audit-issue Used once: _values
  71 |  uint256[] memory _values,
  :  |
     |  // @audit-issue Used once: _description
  74 |  string memory _description

     |  // @audit-issue Used once: _targets
 129 |  address[] memory _targets,
     |  // @audit-issue Used once: _values
 130 |  uint256[] memory _values,
     |  // @audit-issue Used once: _calldatas
 131 |  bytes[] memory _calldatas,

     |  // @audit-issue Used once: _targets
 141 |  address[] memory _targets,
     |  // @audit-issue Used once: _values
 142 |  uint256[] memory _values,
     |  // @audit-issue Used once: _calldatas
 143 |  bytes[] memory _calldatas,
```
GitHub: [49](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L49), [50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L50), [51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L51), [52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L52), [70](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L70), [71](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L71), [74](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L74), [129](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L129), [130](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L130), [131](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L131), [141](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L141), [142](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L142), [143](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L143)


```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

     |  // @audit-issue Used once: _data
  65 |  bytes memory _data
```
GitHub: [65](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L65)


```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

     |  // @audit-issue Used once: _config
 289 |  TaikoData.Config memory _config,

     |  // @audit-issue Used once: _slotB
 300 |  TaikoData.SlotB memory _slotB,
```
GitHub: [289](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L289), [300](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L300)


```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

     |  // @audit-issue Used once: _config
  93 |  TaikoData.Config memory _config,
  :  |
     |          // @audit-issue Used once: ctx
 166 |          IVerifier.Context memory ctx = IVerifier.Context({

     |  // @audit-issue Used once: _proof
 353 |  TaikoData.TierProof memory _proof,
```
GitHub: [93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L93), [166](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L166), [353](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L353)


```solidity
File: packages/protocol/contracts/L1/libs/LibUtils.sol

     |  // @audit-issue Used once: _config
  25 |  TaikoData.Config memory _config,

     |  // @audit-issue Used once: _config
  54 |  TaikoData.Config memory _config,
```
GitHub: [25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L25), [54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L54)


```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

     |  // @audit-issue Used once: _config
  49 |  TaikoData.Config memory _config,
```
GitHub: [49](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L49)


```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

     |  // @audit-issue Used once: meta_
     |  // @audit-issue Used once: deposits_
  63 |  returns (TaikoData.BlockMetadata memory meta_, TaikoData.EthDeposit[] memory deposits_)

     |  // @audit-issue Used once: tran
  86 |  TaikoData.Transition memory tran,
     |  // @audit-issue Used once: proof
  87 |  TaikoData.TierProof memory proof

     |  // @audit-issue Used once: ts_
 148 |  returns (TaikoData.Block memory blk_, TaikoData.TransitionState memory ts_)

     |  // @audit-issue Used once: a_
     |  // @audit-issue Used once: b_
 179 |  returns (TaikoData.SlotA memory a_, TaikoData.SlotB memory b_)
```
GitHub: [63](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L63), [63](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L63), [86](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L86), [87](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L87), [148](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L148), [179](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L179), [179](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L179)


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

     |  // @audit-issue Used once: config
 136 |  Config memory config = getConfig();
```
GitHub: [136](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L136)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

     |  // @audit-issue Used once: _message
 449 |  function hashMessage(Message memory _message) public pure returns (bytes32) {

     |  // @audit-issue Used once: data
 587 |  bytes memory data = abi.encodeCall(
```
GitHub: [449](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L449), [587](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L587)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

     |  // @audit-issue Used once: _symbol
  43 |  string memory _symbol,
     |  // @audit-issue Used once: _name
  44 |  string memory _name

     |  // @audit-issue Used once: _tokenIds
  85 |  uint256[] memory _tokenIds,
     |  // @audit-issue Used once: _amounts
  86 |  uint256[] memory _amounts
```
GitHub: [43](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L43), [44](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L44), [85](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L85), [86](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L86)


```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

     |  // @audit-issue Used once: data
     |  // @audit-issue Used once: ctoken
  55 |  (bytes memory data, CanonicalNFT memory ctoken) = _handleMessage(msg.sender, _op);
  :  |
     |  // @audit-issue Used once: message
  58 |  IBridge.Message memory message = IBridge.Message({

     |  // @audit-issue Used once: data
 140 |  (bytes memory data) = abi.decode(message.data[4:], (bytes));

     |  // @audit-issue Used once: msgData_
 245 |  returns (bytes memory msgData_, CanonicalNFT memory ctoken_)
  :  |
     |          // @audit-issue Used once: _name
 263 |          try t.name() returns (string memory _name) {
  :  |
     |          // @audit-issue Used once: _symbol
 266 |          try t.symbol() returns (string memory _symbol) {

     |  // @audit-issue Used once: data
 304 |  bytes memory data = abi.encodeCall(
```
GitHub: [55](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L55), [55](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L55), [58](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L58), [140](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L140), [245](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L245), [263](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L263), [266](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L266), [304](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L304)


```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

     |  // @audit-issue Used once: data
     |  // @audit-issue Used once: ctoken
 218 |  (bytes memory data, CanonicalERC20 memory ctoken, uint256 balanceChange) =
  :  |
     |  // @audit-issue Used once: message
 221 |  IBridge.Message memory message = IBridge.Message({

     |  // @audit-issue Used once: data
 298 |  (bytes memory data) = abi.decode(_message.data[4:], (bytes));

     |  // @audit-issue Used once: msgData_
 355 |  returns (bytes memory msgData_, CanonicalERC20 memory ctoken_, uint256 balanceChange_)

     |  // @audit-issue Used once: data
 408 |  bytes memory data = abi.encodeCall(
```
GitHub: [218](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L218), [218](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L218), [221](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L221), [298](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L298), [355](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L355), [408](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L408)


```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

     |  // @audit-issue Used once: data
     |  // @audit-issue Used once: ctoken
  42 |  (bytes memory data, CanonicalNFT memory ctoken) = _handleMessage(msg.sender, _op);
  :  |
     |  // @audit-issue Used once: message
  44 |  IBridge.Message memory message = IBridge.Message({

     |  // @audit-issue Used once: data
 123 |  (bytes memory data) = abi.decode(_message.data[4:], (bytes));

     |  // @audit-issue Used once: msgData_
 192 |  returns (bytes memory msgData_, CanonicalNFT memory ctoken_)

     |  // @audit-issue Used once: data
 241 |  bytes memory data = abi.encodeCall(
```
GitHub: [42](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L42), [42](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L42), [44](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L44), [123](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L123), [192](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L192), [241](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L241)


```solidity
File: packages/protocol/contracts/tokenvault/LibBridgedToken.sol

     |  // @audit-issue Used once: _symbol
  14 |  string memory _symbol,
     |  // @audit-issue Used once: _name
  15 |  string memory _name

     |  // @audit-issue Used once: _name
  29 |  string memory _name,

     |  // @audit-issue Used once: _symbol
  39 |  function buildSymbol(string memory _symbol) internal pure returns (string memory) {
```
GitHub: [14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L14), [15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L15), [29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L29), [39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L39)


```solidity
File: packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol

     |  // @audit-issue Used once: _returnData
  38 |  bytes memory _returnData = new bytes(_maxCopy);
```
GitHub: [38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L38)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/Bytes.sol

     |  // @audit-issue Used once: _bytes
  16 |  bytes memory _bytes,
  :  |
     |  // @audit-issue Used once: tempBytes
  30 |  bytes memory tempBytes;

     |  // @audit-issue Used once: _nibbles
 103 |  bytes memory _nibbles;

     |  // @audit-issue Used once: _bytes
     |  // @audit-issue Used once: _other
 149 |  function equal(bytes memory _bytes, bytes memory _other) internal pure returns (bool) {
```
GitHub: [16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L16), [30](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L30), [103](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L103), [149](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L149), [149](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L149)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

     |  // @audit-issue Used once: out_
  35 |  function toRLPItem(bytes memory _in) internal pure returns (RLPItem memory out_) {

     |  // @audit-issue Used once: out_
     |  // @audit-issue Used once: _in
 102 |  function readList(bytes memory _in) internal pure returns (RLPItem[] memory out_) {

     |  // @audit-issue Used once: out_
 109 |  function readBytes(RLPItem memory _in) internal pure returns (bytes memory out_) {

     |  // @audit-issue Used once: out_
     |  // @audit-issue Used once: _in
 128 |  function readBytes(bytes memory _in) internal pure returns (bytes memory out_) {

     |  // @audit-issue Used once: out_
 135 |  function readRawBytes(RLPItem memory _in) internal pure returns (bytes memory out_) {
```
GitHub: [35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L35), [102](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L102), [102](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L102), [109](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L109), [128](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L128), [128](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L128), [135](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L135)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

     |  // @audit-issue Used once: out_
  24 |  function writeUint(uint256 _in) internal pure returns (bytes memory out_) {
```
GitHub: [24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L24)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

     |  // @audit-issue Used once: _key
  51 |  bytes memory _key,
     |  // @audit-issue Used once: _value
  52 |  bytes memory _value,
     |  // @audit-issue Used once: _proof
  53 |  bytes[] memory _proof,

     |  // @audit-issue Used once: _proof
  70 |  bytes[] memory _proof,
  :  |
     |              // @audit-issue Used once: nextNode
 135 |              RLPReader.RLPItem memory nextNode = currentNode.decoded[branchKey];

     |  // @audit-issue Used once: id_
 220 |  function _getNodeID(RLPReader.RLPItem memory _node) private pure returns (bytes memory id_) {

     |  // @audit-issue Used once: nibbles_
     |  // @audit-issue Used once: _node
 227 |  function _getNodePath(TrieNode memory _node) private pure returns (bytes memory nibbles_) {
```
GitHub: [51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L51), [52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L52), [53](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L53), [70](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L70), [135](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L135), [220](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L220), [227](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L227), [227](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L227)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol

     |  // @audit-issue Used once: _key
  20 |  bytes memory _key,
     |  // @audit-issue Used once: _value
  21 |  bytes memory _value,
     |  // @audit-issue Used once: _proof
  22 |  bytes[] memory _proof,
  :  |
     |  // @audit-issue Used once: key
  29 |  bytes memory key = _getSecureKey(_key);

     |  // @audit-issue Used once: _key
  39 |  bytes memory _key,
     |  // @audit-issue Used once: _proof
  40 |  bytes[] memory _proof,
  :  |
     |  // @audit-issue Used once: value_
  45 |  returns (bytes memory value_)
  :  |
     |  // @audit-issue Used once: key
  47 |  bytes memory key = _getSecureKey(_key);

     |  // @audit-issue Used once: hash_
     |  // @audit-issue Used once: _key
  54 |  function _getSecureKey(bytes memory _key) private pure returns (bytes memory hash_) {
```
GitHub: [20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L20), [21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L21), [22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L22), [29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L29), [39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L39), [40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L40), [45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L45), [47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L47), [54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L54), [54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L54)


```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

     |  // @audit-issue Used once: signature
 156 |  bytes memory signature = Bytes.slice(_proof.data, 24);

     |  // @audit-issue Used once: _tran
 172 |  TaikoData.Transition memory _tran,
```
GitHub: [156](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L156), [172](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L172)


## [G-51] Structs can be packed into fewer storage slots

Each slot saved can avoid an extra Gsset (20000 gas) for the first setting of the struct. Subsequent reads as well as writes have smaller gas savings

*Instances: 6*

```solidity
File: packages/protocol/contracts/L1/TaikoData.sol
Struct Config

     |  // @audit-issue Can improve from 8 to 7 slots:
     |  // slot[0] = blockSyncThreshold (uint8/1 bytes)
     |  // slot[1] = blobAllowedForDA (bool/1 bytes), blockMaxTxListBytes (uint24/3 bytes), blockMaxGasLimit (uint32/4 bytes), ethDepositMaxCountPerBlock (uint64/8 bytes), ethDepositMinCountPerBlock (uint64/8 bytes), maxBlocksToVerifyPerProposal (uint64/8 bytes)
     |  // slot[2] = blobReuseEnabled (bool/1 bytes), blobExpiry (uint24/3 bytes), blockMaxProposals (uint64/8 bytes), chainId (uint64/8 bytes), ethDepositMaxAmount (uint96/12 bytes)
     |  // slot[3] = blockRingBufferSize (uint64/8 bytes), ethDepositMinAmount (uint96/12 bytes), livenessBond (uint96/12 bytes)
     |  // slot[4] = ethDepositMaxFee (uint256/32 bytes)
     |  // slot[5] = ethDepositGas (uint256/32 bytes)
     |  // slot[6] = ethDepositRingBufferSize (uint256/32 bytes)
  10 |  struct Config {
  11 |      // ---------------------------------------------------------------------
  12 |      // Group 1: General configs
  13 |      // ---------------------------------------------------------------------
  14 |      // The chain ID of the network where Taiko contracts are deployed.
  15 |      uint64 chainId;
  16 |      // ---------------------------------------------------------------------
  17 |      // Group 2: Block level configs
  18 |      // ---------------------------------------------------------------------
  19 |      // The maximum number of proposals allowed in a single block.
  20 |      uint64 blockMaxProposals;
  21 |      // Size of the block ring buffer, allowing extra space for proposals.
  22 |      uint64 blockRingBufferSize;
  23 |      // The maximum number of verifications allowed when a block is proposed.
  24 |      uint64 maxBlocksToVerifyPerProposal;
  25 |      // The maximum gas limit allowed for a block.
  26 |      uint32 blockMaxGasLimit;
  27 |      // The maximum allowed bytes for the proposed transaction list calldata.
  28 |      uint24 blockMaxTxListBytes;
  29 |      // The max period in seconds that a blob can be reused for DA.
  30 |      uint24 blobExpiry;
  31 |      // True if EIP-4844 is enabled for DA
  32 |      bool blobAllowedForDA;
  33 |      // True if blob can be reused
  34 |      bool blobReuseEnabled;
  35 |      // ---------------------------------------------------------------------
  36 |      // Group 3: Proof related configs
  37 |      // ---------------------------------------------------------------------
  38 |      // The amount of Taiko token as a prover liveness bond
  39 |      uint96 livenessBond;
  40 |      // ---------------------------------------------------------------------
  41 |      // Group 4: ETH deposit related configs
  42 |      // ---------------------------------------------------------------------
  43 |      // The size of the ETH deposit ring buffer.
  44 |      uint256 ethDepositRingBufferSize;
  45 |      // The minimum number of ETH deposits allowed per block.
  46 |      uint64 ethDepositMinCountPerBlock;
  47 |      // The maximum number of ETH deposits allowed per block.
  48 |      uint64 ethDepositMaxCountPerBlock;
  49 |      // The minimum amount of ETH required for a deposit.
  50 |      uint96 ethDepositMinAmount;
  51 |      // The maximum amount of ETH allowed for a deposit.
  52 |      uint96 ethDepositMaxAmount;
  53 |      // The gas cost for processing an ETH deposit.
  54 |      uint256 ethDepositGas;
  55 |      // The maximum fee allowed for an ETH deposit.
  56 |      uint256 ethDepositMaxFee;
  57 |      // The max number of L2 blocks that can stay unsynced on L1 (a value of zero disables
  58 |      // syncing)
  59 |      uint8 blockSyncThreshold;
  60 |  }
```
GitHub: [10-60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L10-L60)


```solidity
File: packages/protocol/contracts/L1/TaikoData.sol
Struct BlockParams

     |  // @audit-issue Can improve from 7 to 6 slots:
     |  // slot[0] = cacheBlobForReuse (bool/1 bytes), txListByteSize (uint24/3 bytes), txListByteOffset (uint24/3 bytes), coinbase (address/20 bytes)
     |  // slot[1] = assignedProver (address/20 bytes)
     |  // slot[2] = hookCalls ([]/32 bytes)
     |  // slot[3] = parentMetaHash (bytes32/32 bytes)
     |  // slot[4] = blobHash (bytes32/32 bytes)
     |  // slot[5] = extraData (bytes32/32 bytes)
  78 |  struct BlockParams {
  79 |      address assignedProver;
  80 |      address coinbase;
  81 |      bytes32 extraData;
  82 |      bytes32 blobHash;
  83 |      uint24 txListByteOffset;
  84 |      uint24 txListByteSize;
  85 |      bool cacheBlobForReuse;
  86 |      bytes32 parentMetaHash;
  87 |      HookCall[] hookCalls;
  88 |  }
```
GitHub: [78-88](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L78-L88)


```solidity
File: packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol
Struct Certificate

     |  // @audit-issue Can improve from 4 to 5 slots:
     |  // slot[0] = sigAlg (enum/32 bytes)
     |  // slot[1] = signature (bytes/32 bytes)
     |  // slot[2] = publicKey (struct/64 bytes)
     |  // slot[3] = publicKey (struct/64 bytes)
     |  // slot[4] = tbsCertificate (bytes/32 bytes)
  24 |  struct Certificate {
  25 |      // Asn.1 DER encoding of the to-be-signed certificate
  26 |      bytes tbsCertificate;
  27 |      PublicKey publicKey;
  28 |      bytes signature;
  29 |      CertSigAlgorithm sigAlg;
  30 |  }
```
GitHub: [24-30](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L24-L30)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol
Struct EnclaveReport

     |  // @audit-issue Can improve from 10 to 9 slots:
     |  // slot[0] = isvSvn (uint16/2 bytes), isvProdId (uint16/2 bytes)
     |  // slot[1] = attributes (bytes16/16 bytes), cpuSvn (bytes16/16 bytes)
     |  // slot[2] = miscSelect (bytes4/4 bytes), reserved1 (bytes28/28 bytes)
     |  // slot[3] = reportData (bytes/32 bytes)
     |  // slot[4] = reserved4 (bytes/32 bytes)
     |  // slot[5] = reserved3 (bytes/32 bytes)
     |  // slot[6] = mrSigner (bytes32/32 bytes)
     |  // slot[7] = reserved2 (bytes32/32 bytes)
     |  // slot[8] = mrEnclave (bytes32/32 bytes)
  17 |  struct EnclaveReport {
  18 |      bytes16 cpuSvn;
  19 |      bytes4 miscSelect;
  20 |      bytes28 reserved1;
  21 |      bytes16 attributes;
  22 |      bytes32 mrEnclave;
  23 |      bytes32 reserved2;
  24 |      bytes32 mrSigner;
  25 |      bytes reserved3; // 96 bytes
  26 |      uint16 isvProdId;
  27 |      uint16 isvSvn;
  28 |      bytes reserved4; // 60 bytes
  29 |      bytes reportData; // 64 bytes - For QEReports, this contains the hash of the concatenation
  30 |          // of attestation key and QEAuthData
  31 |  }
```
GitHub: [17-31](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L17-L31)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol
Struct ECDSAQuoteV3AuthData

     |  // @audit-issue Can improve from 17 to 18 slots:
     |  // slot[0] = qeReportSignature (bytes/32 bytes)
     |  // slot[1] = ecdsaAttestationKey (bytes/32 bytes)
     |  // slot[2] = qeAuthData (struct/64 bytes)
     |  // slot[3] = qeAuthData (struct/64 bytes)
     |  // slot[4] = certification (struct/128 bytes)
     |  // slot[5] = certification (struct/128 bytes)
     |  // slot[6] = certification (struct/128 bytes)
     |  // slot[7] = certification (struct/128 bytes)
     |  // slot[8] = pckSignedQeReport (struct/288 bytes)
     |  // slot[9] = pckSignedQeReport (struct/288 bytes)
     |  // slot[10] = pckSignedQeReport (struct/288 bytes)
     |  // slot[11] = pckSignedQeReport (struct/288 bytes)
     |  // slot[12] = pckSignedQeReport (struct/288 bytes)
     |  // slot[13] = pckSignedQeReport (struct/288 bytes)
     |  // slot[14] = pckSignedQeReport (struct/288 bytes)
     |  // slot[15] = pckSignedQeReport (struct/288 bytes)
     |  // slot[16] = pckSignedQeReport (struct/288 bytes)
     |  // slot[17] = ecdsa256BitSignature (bytes/32 bytes)
  47 |  struct ECDSAQuoteV3AuthData {
  48 |      bytes ecdsa256BitSignature; // 64 bytes
  49 |      bytes ecdsaAttestationKey; // 64 bytes
  50 |      EnclaveReport pckSignedQeReport; // 384 bytes
  51 |      bytes qeReportSignature; // 64 bytes
  52 |      QEAuthData qeAuthData;
  53 |      CertificationData certification;
  54 |  }
```
GitHub: [47-54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L47-L54)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol
Struct ParsedV3QuoteStruct

     |  // @audit-issue Can improve from 30 to 29 slots:
     |  // slot[0] = header (struct/64 bytes)
     |  // slot[1] = header (struct/64 bytes)
     |  // slot[2] = localEnclaveReport (struct/288 bytes)
     |  // slot[3] = localEnclaveReport (struct/288 bytes)
     |  // slot[4] = localEnclaveReport (struct/288 bytes)
     |  // slot[5] = localEnclaveReport (struct/288 bytes)
     |  // slot[6] = localEnclaveReport (struct/288 bytes)
     |  // slot[7] = localEnclaveReport (struct/288 bytes)
     |  // slot[8] = localEnclaveReport (struct/288 bytes)
     |  // slot[9] = localEnclaveReport (struct/288 bytes)
     |  // slot[10] = localEnclaveReport (struct/288 bytes)
     |  // slot[11] = v3AuthData (struct/576 bytes)
     |  // slot[12] = v3AuthData (struct/576 bytes)
     |  // slot[13] = v3AuthData (struct/576 bytes)
     |  // slot[14] = v3AuthData (struct/576 bytes)
     |  // slot[15] = v3AuthData (struct/576 bytes)
     |  // slot[16] = v3AuthData (struct/576 bytes)
     |  // slot[17] = v3AuthData (struct/576 bytes)
     |  // slot[18] = v3AuthData (struct/576 bytes)
     |  // slot[19] = v3AuthData (struct/576 bytes)
     |  // slot[20] = v3AuthData (struct/576 bytes)
     |  // slot[21] = v3AuthData (struct/576 bytes)
     |  // slot[22] = v3AuthData (struct/576 bytes)
     |  // slot[23] = v3AuthData (struct/576 bytes)
     |  // slot[24] = v3AuthData (struct/576 bytes)
     |  // slot[25] = v3AuthData (struct/576 bytes)
     |  // slot[26] = v3AuthData (struct/576 bytes)
     |  // slot[27] = v3AuthData (struct/576 bytes)
     |  // slot[28] = v3AuthData (struct/576 bytes)
  56 |  struct ParsedV3QuoteStruct {
  57 |      Header header;
  58 |      EnclaveReport localEnclaveReport;
  59 |      ECDSAQuoteV3AuthData v3AuthData;
  60 |  }
```
GitHub: [56-60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L56-L60)


## [G-52] Subtraction can potentially be marked `unchecked` to save gas

In Solidity 0.8.x and above, arithmetic operations like subtraction automatically check for underflows and overflows, and revert the transaction if such a condition is met. This built-in safety feature provides a layer of security against potential numerical errors. However, these automatic checks also come with additional gas costs.

In some situations, you may already have a guard condition, like a require() statement or an if statement, that ensures the safety of the arithmetic operation. In such cases, the automatic check becomes redundant and leads to unnecessary gas expenditure.

For example, you may have a function that subtracts a smaller number from a larger one, and you may have already verified that the smaller number is indeed smaller. In this case, you're already sure that the subtraction operation won't underflow, so there's no need for the automatic check.

In these situations, you can use the unchecked { } block around the subtraction operation to skip the automatic check. This will reduce gas costs and make your contract more efficient, without sacrificing security. However, it's critical to use unchecked { } only when you're absolutely sure that the operation is safe.

*Instances: 97*

```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

     |  // @audit-issue Use unchecked to save gas, if possible
  76 |  uint256 numPending = _state.slotA.numEthDeposits - _state.slotA.nextEthDepositToProcess;

     |  // @audit-issue Use unchecked to save gas, if possible
 140 |  && _state.slotA.numEthDeposits - _state.slotA.nextEthDepositToProcess

     |  // @audit-issue Use unchecked to save gas, if possible
 141 |  < _config.ethDepositRingBufferSize - 1;
```
GitHub: [76](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L76), [140](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L140), [141](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L141)


```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

     |  // @audit-issue Use unchecked to save gas, if possible
 103 |  _state.blocks[(b.numBlocks - 1) % _config.blockRingBufferSize].metaHash;

     |  // @audit-issue Use unchecked to save gas, if possible
 122 |  l1Hash: blockhash(block.number - 1),

     |  // @audit-issue Use unchecked to save gas, if possible
 131 |  l1Height: uint64(block.number - 1),
```
GitHub: [103](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L103), [122](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L122), [131](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L131)


```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

     |  // @audit-issue Use unchecked to save gas, if possible
 382 |  _tko.transfer(msg.sender, reward - _tier.validityBond);

     |  // @audit-issue Use unchecked to save gas, if possible
 384 |  _tko.transferFrom(msg.sender, address(this), _tier.validityBond - reward);
```
GitHub: [382](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L382), [384](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L384)


```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

     |  // @audit-issue Use unchecked to save gas, if possible
 116 |  _approvals[version][_hash] |= 1 << (id - 1);
```
GitHub: [116](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L116)


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

     |  // @audit-issue Use unchecked to save gas, if possible
  90 |  uint256 parentHeight = block.number - 1;

     |  // @audit-issue Use unchecked to save gas, if possible
 127 |  parentId = block.number - 1;

     |  // @audit-issue Use unchecked to save gas, if possible
 235 |  uint256 j = _blockId - i - 1;

     |  // @audit-issue Use unchecked to save gas, if possible
 235 |  uint256 j = _blockId - i - 1;

     |  // @audit-issue Use unchecked to save gas, if possible
 276 |  numL1Blocks = _l1BlockId - lastSyncedBlock;

     |  // @audit-issue Use unchecked to save gas, if possible
 281 |  excess = excess > issuance ? excess - issuance : 1;
```
GitHub: [90](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L90), [127](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L127), [235](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L235), [235](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L235), [276](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L276), [281](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L281)


```solidity
File: packages/protocol/contracts/signal/SignalService.sol

     |  // @audit-issue Use unchecked to save gas, if possible
 108 |  bool isLastHop = i == hopProofs.length - 1;
```
GitHub: [108](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L108)


```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

     |  // @audit-issue Use unchecked to save gas, if possible
  67 |  value: msg.value - _op.fee,
```
GitHub: [67](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L67)


```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

     |  // @audit-issue Use unchecked to save gas, if possible
 230 |  value: msg.value - _op.fee,

     |  // @audit-issue Use unchecked to save gas, if possible
 380 |  balanceChange_ = t.balanceOf(address(this)) - _balance;
```
GitHub: [230](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L230), [380](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L380)


```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

     |  // @audit-issue Use unchecked to save gas, if possible
  53 |  value: msg.value - _op.fee,
```
GitHub: [53](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L53)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/Bytes.sol

     |  // @audit-issue Use unchecked to save gas, if possible
  95 |  return slice(_bytes, _start, _bytes.length - _start);
```
GitHub: [95](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L95)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

     |  // @audit-issue Use unchecked to save gas, if possible
  77 |  length: _in.length - offset,

     |  // @audit-issue Use unchecked to save gas, if possible
 170 |  uint256 strLen = prefix - 0x80;

     |  // @audit-issue Use unchecked to save gas, if possible
 190 |  uint256 lenOfStrLen = prefix - 0xb7;

     |  // @audit-issue Use unchecked to save gas, if possible
 226 |  uint256 listLen = prefix - 0xc0;

     |  // @audit-issue Use unchecked to save gas, if possible
 236 |  uint256 lenOfListLen = prefix - 0xf7;
```
GitHub: [77](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L77), [170](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L170), [190](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L190), [226](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L226), [236](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L236)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

     |  // @audit-issue Use unchecked to save gas, if possible
  47 |  out_[i] = bytes1(uint8((_len / (256 ** (lenLen - i))) % 256));

     |  // @audit-issue Use unchecked to save gas, if possible
  65 |  out_ = new bytes(32 - i);
```
GitHub: [47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L47), [65](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L65)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

     |  // @audit-issue Use unchecked to save gas, if possible
 126 |  i == proof.length - 1,

     |  // @audit-issue Use unchecked to save gas, if possible
 142 |  uint8 offset = 2 - (prefix % 2);

     |  // @audit-issue Use unchecked to save gas, if possible
 179 |  i == proof.length - 1,
```
GitHub: [126](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L126), [142](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L142), [179](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L179)


```solidity
File: packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol

     |  // @audit-issue Use unchecked to save gas, if possible
  40 |  x = x - k * 54_916_777_467_707_473_351_141_471_128;

     |  // @audit-issue Use unchecked to save gas, if possible
  47 |  int256 p = y + x - 94_201_549_194_550_492_254_356_042_504_812;

     |  // @audit-issue Use unchecked to save gas, if possible
  53 |  int256 q = x - 2_855_989_394_907_223_263_936_484_059_900;

     |  // @audit-issue Use unchecked to save gas, if possible
  55 |  q = ((q * x) >> 96) - 533_845_033_583_426_703_283_633_433_725_380;

     |  // @audit-issue Use unchecked to save gas, if possible
  57 |  q = ((q * x) >> 96) - 14_423_608_567_350_463_180_887_372_962_807_573;

     |  // @audit-issue Use unchecked to save gas, if possible
  78 |  >> uint256(195 - k)
```
GitHub: [40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L40), [47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L47), [53](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L53), [55](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L55), [57](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L57), [78](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L78)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

     |  // @audit-issue Use unchecked to save gas, if possible
 118 |  * (block.timestamp.min(claimEnd + withdrawalWindow) - claimEnd) / withdrawalWindow;

     |  // @audit-issue Use unchecked to save gas, if possible
 120 |  withdrawableAmount = timeBasedAllowance - withdrawnAmount[user];
```
GitHub: [118](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L118), [120](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L120)


```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

     |  // @audit-issue Use unchecked to save gas, if possible
 193 |  amountToWithdraw = amountUnlocked - amountWithdrawn;

     |  // @audit-issue Use unchecked to save gas, if possible
 198 |  costToWithdraw = _amountUnlocked * r.grant.costPerToken - r.costPaid;

     |  // @audit-issue Use unchecked to save gas, if possible
 228 |  amountVoided = _grant.amount - amountOwned;

     |  // @audit-issue Use unchecked to save gas, if possible
 264 |  return _amount * uint64(block.timestamp - _start) / _period;
```
GitHub: [193](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L193), [198](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L198), [228](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L228), [264](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L264)


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

     |  // @audit-issue Use unchecked to save gas, if possible
 261 |  if (i == n - 1) {

     |  // @audit-issue Use unchecked to save gas, if possible
 266 |  if (i == n - 2) {
```
GitHub: [261](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L261), [266](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L266)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

     |  // @audit-issue Use unchecked to save gas, if possible
 265 |  uint256 lengthDiff = n - expectedLength;
```
GitHub: [265](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L265)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

     |  // @audit-issue Use unchecked to save gas, if possible
  34 |  if (quote.length - 436 != localAuthDataSize) {
```
GitHub: [34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L34)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

     |  // @audit-issue Use unchecked to save gas, if possible
 112 |  return der.substring(ptr.ixf(), ptr.ixl() + 1 - ptr.ixf());

     |  // @audit-issue Use unchecked to save gas, if possible
 122 |  return der.substring(ptr.ixs(), ptr.ixl() + 1 - ptr.ixs());

     |  // @audit-issue Use unchecked to save gas, if possible
 132 |  return der.readBytesN(ptr.ixf(), ptr.ixl() + 1 - ptr.ixf());

     |  // @audit-issue Use unchecked to save gas, if possible
 144 |  uint256 len = ptr.ixl() + 1 - ptr.ixf();

     |  // @audit-issue Use unchecked to save gas, if possible
 145 |  return uint256(der.readBytesN(ptr.ixf(), len) >> (32 - len) * 8);

     |  // @audit-issue Use unchecked to save gas, if possible
 157 |  uint256 valueLength = ptr.ixl() + 1 - ptr.ixf();

     |  // @audit-issue Use unchecked to save gas, if possible
 159 |  return der.substring(ptr.ixf() + 1, valueLength - 1);

     |  // @audit-issue Use unchecked to save gas, if possible
 166 |  return der.keccak(ptr.ixf(), ptr.ixl() + 1 - ptr.ixf());

     |  // @audit-issue Use unchecked to save gas, if possible
 170 |  return der.keccak(ptr.ixs(), ptr.ixl() + 1 - ptr.ixs());

     |  // @audit-issue Use unchecked to save gas, if possible
 183 |  uint256 valueLength = ptr.ixl() + 1 - ptr.ixf();

     |  // @audit-issue Use unchecked to save gas, if possible
 184 |  return der.substring(ptr.ixf() + 1, valueLength - 1);

     |  // @audit-issue Use unchecked to save gas, if possible
 194 |  ixLastContentByte = uint80(ixFirstContentByte + length - 1);

     |  // @audit-issue Use unchecked to save gas, if possible
 203 |  der.readBytesN(ix + 2, lengthbytesLength) >> (32 - lengthbytesLength) * 8

     |  // @audit-issue Use unchecked to save gas, if possible
 207 |  ixLastContentByte = uint80(ixFirstContentByte + length - 1);
```
GitHub: [112](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L112), [122](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L122), [132](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L132), [144](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L144), [145](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L145), [157](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L157), [159](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L159), [166](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L166), [170](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L170), [183](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L183), [184](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L184), [194](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L194), [203](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L203), [207](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L207)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

     |  // @audit-issue Use unchecked to save gas, if possible
  93 |  mask = ~(2 ** (8 * (32 - shortest + idx)) - 1);

     |  // @audit-issue Use unchecked to save gas, if possible
  93 |  mask = ~(2 ** (8 * (32 - shortest + idx)) - 1);

     |  // @audit-issue Use unchecked to save gas, if possible
  95 |  uint256 diff = (a & mask) - (b & mask);

     |  // @audit-issue Use unchecked to save gas, if possible
 104 |  return int256(len) - int256(otherlen);

     |  // @audit-issue Use unchecked to save gas, if possible
 148 |  return keccak(self, offset, self.length - offset)

     |  // @audit-issue Use unchecked to save gas, if possible
 149 |  == keccak(other, otherOffset, other.length - otherOffset);

     |  // @audit-issue Use unchecked to save gas, if possible
 336 |  decoded = uint8(BASE32_HEX_TABLE[uint256(uint8(char)) - 0x30]);

     |  // @audit-issue Use unchecked to save gas, if possible
 338 |  if (i == len - 1) {

     |  // @audit-issue Use unchecked to save gas, if possible
 368 |  return bytes32(ret << (256 - bitlen));
```
GitHub: [93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L93), [93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L93), [95](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L95), [104](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L104), [148](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L148), [149](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L149), [336](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L336), [338](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L338), [368](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L368)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

     |  // @audit-issue Use unchecked to save gas, if possible
 125 |  if (uint8(decipher[decipherlen - 50]) == 0x31) {

     |  // @audit-issue Use unchecked to save gas, if possible
 128 |  } else if (uint8(decipher[decipherlen - 48]) == 0x2f) {

     |  // @audit-issue Use unchecked to save gas, if possible
 135 |  uint256 paddingLen = decipherlen - 5 - digestAlgoWithParamLen - 32;

     |  // @audit-issue Use unchecked to save gas, if possible
 135 |  uint256 paddingLen = decipherlen - 5 - digestAlgoWithParamLen - 32;

     |  // @audit-issue Use unchecked to save gas, if possible
 135 |  uint256 paddingLen = decipherlen - 5 - digestAlgoWithParamLen - 32;

     |  // @audit-issue Use unchecked to save gas, if possible
 268 |  uint256 paddingLen = decipherlen - 3 - sha1Prefix.length - 20;

     |  // @audit-issue Use unchecked to save gas, if possible
 268 |  uint256 paddingLen = decipherlen - 3 - sha1Prefix.length - 20;

     |  // @audit-issue Use unchecked to save gas, if possible
 268 |  uint256 paddingLen = decipherlen - 3 - sha1Prefix.length - 20;
```
GitHub: [125](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L125), [128](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L128), [135](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L135), [135](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L135), [135](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L135), [268](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L268), [268](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L268), [268](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L268)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

     |  // @audit-issue Use unchecked to save gas, if possible
  90 |  bytes memory modulus = publicKey.substring(3, publicKey.length - 3);

     |  // @audit-issue Use unchecked to save gas, if possible
 107 |  bytes memory modulus = publicKey.substring(3, publicKey.length - 3);
```
GitHub: [90](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L90), [107](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L107)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

     |  // @audit-issue Use unchecked to save gas, if possible
  18 |  if (uint8(x509Time[0]) - 48 < 5) yrs += 2000;

     |  // @audit-issue Use unchecked to save gas, if possible
  21 |  yrs += (uint8(x509Time[0]) - 48) * 1000 + (uint8(x509Time[1]) - 48) * 100;

     |  // @audit-issue Use unchecked to save gas, if possible
  21 |  yrs += (uint8(x509Time[0]) - 48) * 1000 + (uint8(x509Time[1]) - 48) * 100;

     |  // @audit-issue Use unchecked to save gas, if possible
  24 |  yrs += (uint8(x509Time[offset + 0]) - 48) * 10 + uint8(x509Time[offset + 1]) - 48;

     |  // @audit-issue Use unchecked to save gas, if possible
  24 |  yrs += (uint8(x509Time[offset + 0]) - 48) * 10 + uint8(x509Time[offset + 1]) - 48;

     |  // @audit-issue Use unchecked to save gas, if possible
  25 |  mnths = (uint8(x509Time[offset + 2]) - 48) * 10 + uint8(x509Time[offset + 3]) - 48;

     |  // @audit-issue Use unchecked to save gas, if possible
  25 |  mnths = (uint8(x509Time[offset + 2]) - 48) * 10 + uint8(x509Time[offset + 3]) - 48;

     |  // @audit-issue Use unchecked to save gas, if possible
  26 |  dys += (uint8(x509Time[offset + 4]) - 48) * 10 + uint8(x509Time[offset + 5]) - 48;

     |  // @audit-issue Use unchecked to save gas, if possible
  26 |  dys += (uint8(x509Time[offset + 4]) - 48) * 10 + uint8(x509Time[offset + 5]) - 48;

     |  // @audit-issue Use unchecked to save gas, if possible
  27 |  hrs += (uint8(x509Time[offset + 6]) - 48) * 10 + uint8(x509Time[offset + 7]) - 48;

     |  // @audit-issue Use unchecked to save gas, if possible
  27 |  hrs += (uint8(x509Time[offset + 6]) - 48) * 10 + uint8(x509Time[offset + 7]) - 48;

     |  // @audit-issue Use unchecked to save gas, if possible
  28 |  mins += (uint8(x509Time[offset + 8]) - 48) * 10 + uint8(x509Time[offset + 9]) - 48;

     |  // @audit-issue Use unchecked to save gas, if possible
  28 |  mins += (uint8(x509Time[offset + 8]) - 48) * 10 + uint8(x509Time[offset + 9]) - 48;

     |  // @audit-issue Use unchecked to save gas, if possible
  29 |  secs += (uint8(x509Time[offset + 10]) - 48) * 10 + uint8(x509Time[offset + 11]) - 48;

     |  // @audit-issue Use unchecked to save gas, if possible
  29 |  secs += (uint8(x509Time[offset + 10]) - 48) * 10 + uint8(x509Time[offset + 11]) - 48;

     |  // @audit-issue Use unchecked to save gas, if possible
  60 |  timestamp += uint256(monthDays[i - 1]) * 86_400; // Days in seconds

     |  // @audit-issue Use unchecked to save gas, if possible
  63 |  timestamp += uint256(day - 1) * 86_400; // Days in seconds
```
GitHub: [18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L18), [21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L21), [21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L21), [24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L24), [24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L24), [25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L25), [25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L25), [26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L26), [26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L26), [27](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L27), [27](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L27), [28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L28), [28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L28), [29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L29), [29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L29), [60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L60), [63](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L63)


## [G-53] The result of function calls should be cached rather than re-calling the function

The instances below point to the second+ call of the function within a single function.

*Instances: 92*

```solidity
File: packages/protocol/contracts/libs/Lib4844.sol

     |  // @audit-issue Called 2 times in evaluatePoint()
  49 |  if (ret.length != 64) revert EVAL_FAILED_2();

     |  // @audit-issue Called 2 times in evaluatePoint()
  58 |  revert EVAL_FAILED_2();
```
GitHub: [49](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/Lib4844.sol#L49), [58](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/Lib4844.sol#L58)


```solidity
File: packages/protocol/contracts/libs/LibAddress.sol

     |  // @audit-issue Called 2 times in sendEther()
  24 |  if (_to == address(0)) revert ETH_TRANSFER_FAILED();

     |  // @audit-issue Called 2 times in sendEther()
  36 |  if (!success) revert ETH_TRANSFER_FAILED();
```
GitHub: [24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L24), [36](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L36)


```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

     |  // @audit-issue Called 2 times in proposeBlock()
 238 |  uint256 tkoBalance = tko.balanceOf(address(this));

     |  // @audit-issue Called 2 times in proposeBlock()
 268 |  if (tko.balanceOf(address(this)) != tkoBalance + _config.livenessBond) {
```
GitHub: [238](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L238), [268](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L268)


```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

     |  // @audit-issue Called 2 times in verifyBlocks()
 105 |  if (blk.blockId != blockId) revert L1_BLOCK_MISMATCH();

     |  // @audit-issue Called 2 times in verifyBlocks()
 131 |  if (blk.blockId != blockId) revert L1_BLOCK_MISMATCH();

     |  // @audit-issue Called 2 times in _isConfigValid()
 260 |  || _config.ethDepositMaxAmount > type(uint96).max || _config.ethDepositGas == 0

     |  // @audit-issue Called 2 times in _isConfigValid()
 262 |  || _config.ethDepositMaxFee > type(uint96).max / _config.ethDepositMaxCountPerBlock
```
GitHub: [105](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L105), [131](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L131), [260](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L260), [262](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L262)


```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

     |  // @audit-issue Called 2 times in setGuardians()
  64 |  revert INVALID_GUARDIAN_SET();

     |  // @audit-issue Called 2 times in setGuardians()
  84 |  if (guardianIds[guardian] != 0) revert INVALID_GUARDIAN_SET();
```
GitHub: [64](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L64), [84](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L84)


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

     |  // @audit-issue Called 2 times in anchor()
 154 |  l2Hashes[parentId] = blockhash(parentId);

     |  // @audit-issue Called 2 times in anchor()
 157 |  emit Anchored(blockhash(parentId), gasExcess);
```
GitHub: [154](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L154), [157](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L157)


```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

     |  // @audit-issue Called 2 times in setConfigAndExcess()
  33 |  if (_newConfig.gasTargetPerL1Block == 0) revert L2_INVALID_CONFIG();

     |  // @audit-issue Called 2 times in setConfigAndExcess()
  34 |  if (_newConfig.basefeeAdjustmentQuotient == 0) revert L2_INVALID_CONFIG();
```
GitHub: [33](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L33), [34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L34)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

     |  // @audit-issue Called 2 times in sendMessage()
 132 |  if (!destChainEnabled) revert B_INVALID_CHAINID();

     |  // @audit-issue Called 2 times in sendMessage()
 134 |  revert B_INVALID_CHAINID();

     |  // @audit-issue Called 2 times in processMessage()
 276 |  _updateMessageStatus(msgHash, Status.DONE);

     |  // @audit-issue Called 2 times in processMessage()
 283 |  _updateMessageStatus(msgHash, Status.DONE);
```
GitHub: [132](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L132), [134](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L134), [276](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L276), [283](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L283)


```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

     |  // @audit-issue Called 2 times in changeBridgedToken()
 164 |  if (IBridgedERC20(_btokenNew).owner() != owner()) {

     |  // @audit-issue Called 2 times in _handleMessage()
 378 |  uint256 _balance = t.balanceOf(address(this));

     |  // @audit-issue Called 2 times in _handleMessage()
 380 |  balanceChange_ = t.balanceOf(address(this)) - _balance;
```
GitHub: [164](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L164), [378](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L378), [380](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L380)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

     |  // @audit-issue Called 2 times in readList()
  78 |  ptr: MemoryPointer.wrap(MemoryPointer.unwrap(_in.ptr) + offset)

     |  // @audit-issue Called 2 times in readList()
  78 |  ptr: MemoryPointer.wrap(MemoryPointer.unwrap(_in.ptr) + offset)

     |  // @audit-issue Called 2 times in readList()
  86 |  ptr: MemoryPointer.wrap(MemoryPointer.unwrap(_in.ptr) + offset)

     |  // @audit-issue Called 2 times in readList()
  86 |  ptr: MemoryPointer.wrap(MemoryPointer.unwrap(_in.ptr) + offset)
```
GitHub: [78](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L78), [78](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L78), [86](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L86), [86](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L86)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

     |  // @audit-issue Called 2 times in get()
  94 |  Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),

     |  // @audit-issue Called 2 times in get()
  94 |  Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),

     |  // @audit-issue Called 2 times in get()
  94 |  Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),

     |  // @audit-issue Called 2 times in get()
 100 |  Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),

     |  // @audit-issue Called 2 times in get()
 100 |  Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),

     |  // @audit-issue Called 2 times in get()
 100 |  Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
```
GitHub: [94](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L94), [94](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L94), [94](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L94), [100](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L100), [100](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L100), [100](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L100)


```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

     |  // @audit-issue Called 3 times in init()
 121 |  if (_taikoToken == address(0)) revert INVALID_PARAM();

     |  // @audit-issue Called 3 times in init()
 124 |  if (_costToken == address(0)) revert INVALID_PARAM();

     |  // @audit-issue Called 3 times in init()
 127 |  if (_sharedVault == address(0)) revert INVALID_PARAM();

     |  // @audit-issue Called 3 times in _validateCliff()
 275 |  if (_cliff > 0) revert INVALID_GRANT();

     |  // @audit-issue Called 3 times in _validateCliff()
 277 |  if (_cliff > 0 && _cliff <= _start) revert INVALID_GRANT();

     |  // @audit-issue Called 3 times in _validateCliff()
 278 |  if (_cliff >= _start + _period) revert INVALID_GRANT();
```
GitHub: [121](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L121), [124](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L124), [127](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L127), [275](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L275), [277](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L277), [278](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L278)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

     |  // @audit-issue Called 7 times in decodeCert()
 104 |  tbsPtr = der.nextSiblingOf(tbsPtr);

     |  // @audit-issue Called 7 times in decodeCert()
 111 |  tbsPtr = der.nextSiblingOf(tbsPtr);

     |  // @audit-issue Called 7 times in decodeCert()
 112 |  tbsPtr = der.nextSiblingOf(tbsPtr);

     |  // @audit-issue Called 6 times in decodeCert()
 115 |  uint256 issuerPtr = der.firstChildOf(tbsPtr);

     |  // @audit-issue Called 2 times in decodeCert()
 116 |  issuerPtr = der.firstChildOf(issuerPtr);

     |  // @audit-issue Called 2 times in decodeCert()
 117 |  issuerPtr = der.firstChildOf(issuerPtr);

     |  // @audit-issue Called 7 times in decodeCert()
 127 |  tbsPtr = der.nextSiblingOf(tbsPtr);

     |  // @audit-issue Called 6 times in decodeCert()
 130 |  uint256 notBeforePtr = der.firstChildOf(tbsPtr);

     |  // @audit-issue Called 7 times in decodeCert()
 144 |  tbsPtr = der.nextSiblingOf(tbsPtr);

     |  // @audit-issue Called 6 times in decodeCert()
 147 |  uint256 subjectPtr = der.firstChildOf(tbsPtr);

     |  // @audit-issue Called 2 times in decodeCert()
 148 |  subjectPtr = der.firstChildOf(subjectPtr);

     |  // @audit-issue Called 2 times in decodeCert()
 149 |  subjectPtr = der.firstChildOf(subjectPtr);

     |  // @audit-issue Called 7 times in decodeCert()
 157 |  tbsPtr = der.nextSiblingOf(tbsPtr);

     |  // @audit-issue Called 6 times in decodeCert()
 161 |  uint256 subjectPublicKeyInfoPtr = der.firstChildOf(tbsPtr);

     |  // @audit-issue Called 2 times in decodeCert()
 167 |  sigPtr = der.nextSiblingOf(sigPtr);

     |  // @audit-issue Called 2 times in decodeCert()
 174 |  bytes memory sigX = _trimBytes(der.bytesAt(sigPtr), 32);

     |  // @audit-issue Called 2 times in decodeCert()
 174 |  bytes memory sigX = _trimBytes(der.bytesAt(sigPtr), 32);

     |  // @audit-issue Called 2 times in decodeCert()
 176 |  sigPtr = der.nextSiblingOf(sigPtr);

     |  // @audit-issue Called 2 times in decodeCert()
 177 |  bytes memory sigY = _trimBytes(der.bytesAt(sigPtr), 32);

     |  // @audit-issue Called 2 times in decodeCert()
 177 |  bytes memory sigY = _trimBytes(der.bytesAt(sigPtr), 32);

     |  // @audit-issue Called 7 times in decodeCert()
 186 |  tbsPtr = der.nextSiblingOf(tbsPtr);

     |  // @audit-issue Called 6 times in decodeCert()
 193 |  tbsPtr = der.firstChildOf(tbsPtr);

     |  // @audit-issue Called 6 times in decodeCert()
 194 |  tbsPtr = der.firstChildOf(tbsPtr);

     |  // @audit-issue Called 3 times in _findPckTcbInfo()
 306 |  if (BytesUtils.compareBytes(der.bytesAt(extnValueOidPtr), TCB_OID)) {

     |  // @audit-issue Called 3 times in _findPckTcbInfo()
 310 |  if (BytesUtils.compareBytes(der.bytesAt(extnValueOidPtr), PCEID_OID)) {

     |  // @audit-issue Called 2 times in _findPckTcbInfo()
 312 |  uint256 pceidPtr = der.nextSiblingOf(extnValueOidPtr);

     |  // @audit-issue Called 3 times in _findPckTcbInfo()
 316 |  if (BytesUtils.compareBytes(der.bytesAt(extnValueOidPtr), FMSPC_OID)) {

     |  // @audit-issue Called 2 times in _findPckTcbInfo()
 318 |  uint256 fmspcPtr = der.nextSiblingOf(extnValueOidPtr);
```
GitHub: [104](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L104), [111](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L111), [112](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L112), [115](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L115), [116](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L116), [117](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L117), [127](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L127), [130](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L130), [144](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L144), [147](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L147), [148](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L148), [149](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L149), [157](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L157), [161](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L161), [167](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L167), [174](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L174), [174](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L174), [176](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L176), [177](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L177), [177](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L177), [186](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L186), [193](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L193), [194](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L194), [306](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L306), [310](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L310), [312](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L312), [316](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L316), [318](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L318)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

     |  // @audit-issue Called 2 times in isChildOf()
 100 |  ((i.ixf() <= j.ixs()) && (j.ixl() <= i.ixl()))

     |  // @audit-issue Called 2 times in isChildOf()
 100 |  ((i.ixf() <= j.ixs()) && (j.ixl() <= i.ixl()))

     |  // @audit-issue Called 2 times in isChildOf()
 101 |  || ((j.ixf() <= i.ixs()) && (i.ixl() <= j.ixl()))

     |  // @audit-issue Called 2 times in isChildOf()
 101 |  || ((j.ixf() <= i.ixs()) && (i.ixl() <= j.ixl()))

     |  // @audit-issue Called 2 times in bytesAt()
 112 |  return der.substring(ptr.ixf(), ptr.ixl() + 1 - ptr.ixf());

     |  // @audit-issue Called 2 times in bytesAt()
 112 |  return der.substring(ptr.ixf(), ptr.ixl() + 1 - ptr.ixf());

     |  // @audit-issue Called 2 times in allBytesAt()
 122 |  return der.substring(ptr.ixs(), ptr.ixl() + 1 - ptr.ixs());

     |  // @audit-issue Called 2 times in allBytesAt()
 122 |  return der.substring(ptr.ixs(), ptr.ixl() + 1 - ptr.ixs());

     |  // @audit-issue Called 2 times in bytes32At()
 132 |  return der.readBytesN(ptr.ixf(), ptr.ixl() + 1 - ptr.ixf());

     |  // @audit-issue Called 2 times in bytes32At()
 132 |  return der.readBytesN(ptr.ixf(), ptr.ixl() + 1 - ptr.ixf());

     |  // @audit-issue Called 3 times in uintAt()
 143 |  require(der[ptr.ixf()] & 0x80 == 0, "Not positive");

     |  // @audit-issue Called 3 times in uintAt()
 144 |  uint256 len = ptr.ixl() + 1 - ptr.ixf();

     |  // @audit-issue Called 3 times in uintAt()
 145 |  return uint256(der.readBytesN(ptr.ixf(), len) >> (32 - len) * 8);

     |  // @audit-issue Called 5 times in uintBytesAt()
 156 |  require(der[ptr.ixf()] & 0x80 == 0, "Not positive");

     |  // @audit-issue Called 5 times in uintBytesAt()
 157 |  uint256 valueLength = ptr.ixl() + 1 - ptr.ixf();

     |  // @audit-issue Called 5 times in uintBytesAt()
 158 |  if (der[ptr.ixf()] == 0) {

     |  // @audit-issue Called 5 times in uintBytesAt()
 159 |  return der.substring(ptr.ixf() + 1, valueLength - 1);

     |  // @audit-issue Called 5 times in uintBytesAt()
 161 |  return der.substring(ptr.ixf(), valueLength);

     |  // @audit-issue Called 2 times in keccakOfBytesAt()
 166 |  return der.keccak(ptr.ixf(), ptr.ixl() + 1 - ptr.ixf());

     |  // @audit-issue Called 2 times in keccakOfBytesAt()
 166 |  return der.keccak(ptr.ixf(), ptr.ixl() + 1 - ptr.ixf());

     |  // @audit-issue Called 2 times in keccakOfAllBytesAt()
 170 |  return der.keccak(ptr.ixs(), ptr.ixl() + 1 - ptr.ixs());

     |  // @audit-issue Called 2 times in keccakOfAllBytesAt()
 170 |  return der.keccak(ptr.ixs(), ptr.ixl() + 1 - ptr.ixs());

     |  // @audit-issue Called 3 times in bitstringAt()
 182 |  require(der[ptr.ixf()] == 0x00, "ixf Not 0");

     |  // @audit-issue Called 3 times in bitstringAt()
 183 |  uint256 valueLength = ptr.ixl() + 1 - ptr.ixf();

     |  // @audit-issue Called 3 times in bitstringAt()
 184 |  return der.substring(ptr.ixf() + 1, valueLength - 1);
```
GitHub: [100](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L100), [100](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L100), [101](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L101), [101](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L101), [112](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L112), [112](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L112), [122](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L122), [122](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L122), [132](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L132), [132](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L132), [143](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L143), [144](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L144), [145](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L145), [156](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L156), [157](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L157), [158](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L158), [159](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L159), [161](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L161), [166](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L166), [166](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L166), [170](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L170), [170](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L170), [182](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L182), [183](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L183), [184](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L184)


## [G-54] Usage of non-`uint256`/`int256` types uses more gas

When using a smaller int/uint type it first needs to be converted to it's 256 bit counterpart to be operated upon, this increases the gas cost and thus should be avoided. However it does make sense to use smaller int/uint values within structs provided you pack the struct properly. 

*Instances: 99*

```solidity
File: packages/protocol/contracts/common/IAddressManager.sol

     |  // @audit-issue Consider u/int256
  14 |  function getAddress(uint64 _chainId, bytes32 _name) external view returns (address);
```
GitHub: [14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/IAddressManager.sol#L14)


```solidity
File: packages/protocol/contracts/common/AddressManager.sol

     |  // @audit-issue Consider u/int256
  22 |  uint64 indexed chainId, bytes32 indexed name, address newAddress, address oldAddress

     |  // @audit-issue Consider u/int256
  39 |  uint64 _chainId,

     |  // @audit-issue Consider u/int256
  54 |  function getAddress(uint64 _chainId, bytes32 _name) public view override returns (address) {
```
GitHub: [22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L22), [39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L39), [54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L54)


```solidity
File: packages/protocol/contracts/common/IAddressResolver.sol

     |  // @audit-issue Consider u/int256
  35 |  uint64 _chainId,
```
GitHub: [35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/IAddressResolver.sol#L35)


```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

     |  // @audit-issue Consider u/int256
  19 |  error RESOLVER_ZERO_ADDR(uint64 chainId, bytes32 name);

     |  // @audit-issue Consider u/int256
  44 |  uint64 _chainId,

     |  // @audit-issue Consider u/int256
  73 |  uint64 _chainId,
```
GitHub: [19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L19), [44](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L44), [73](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L73)


```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

     |  // @audit-issue Consider u/int256
  11 |  uint8 private constant _FALSE = 1;

     |  // @audit-issue Consider u/int256
  13 |  uint8 private constant _TRUE = 2;

     |  // @audit-issue Consider u/int256
  21 |  uint8 private __reentry;

     |  // @audit-issue Consider u/int256
  23 |  uint8 private __paused;

     |  // @audit-issue Consider u/int256
 119 |  function _storeReentryLock(uint8 _reentry) internal virtual {

     |  // @audit-issue Consider u/int256
 130 |  function _loadReentryLock() internal view virtual returns (uint8 reentry_) {
```
GitHub: [11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L11), [13](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L13), [21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L21), [23](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L23), [119](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L119), [130](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L130)


```solidity
File: packages/protocol/contracts/libs/Lib4844.sol

     |  // @audit-issue Consider u/int256
  13 |  uint32 public constant FIELD_ELEMENTS_PER_BLOB = 4096;
```
GitHub: [13](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/Lib4844.sol#L13)


```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

     |  // @audit-issue Consider u/int256
  20 |  uint64 expiry;

     |  // @audit-issue Consider u/int256
  21 |  uint64 maxBlockId;

     |  // @audit-issue Consider u/int256
  22 |  uint64 maxProposedIn;

     |  // @audit-issue Consider u/int256
 166 |  uint16 _tierId
```
GitHub: [20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L20), [21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L21), [22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L22), [166](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L166)


```solidity
File: packages/protocol/contracts/L1/ITaikoL1.sol

     |  // @audit-issue Consider u/int256
  27 |  function proveBlock(uint64 _blockId, bytes calldata _input) external;

     |  // @audit-issue Consider u/int256
  31 |  function verifyBlocks(uint64 _maxBlocksToVerify) external;
```
GitHub: [27](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/ITaikoL1.sol#L27), [31](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/ITaikoL1.sol#L31)


```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

     |  // @audit-issue Consider u/int256
  83 |  uint96 fee = uint96(_config.ethDepositMaxFee.min(block.basefee * _config.ethDepositGas));

     |  // @audit-issue Consider u/int256
  84 |  uint64 j = _state.slotA.nextEthDepositToProcess;

     |  // @audit-issue Consider u/int256
  85 |  uint96 totalFee;

     |  // @audit-issue Consider u/int256
  93 |  uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount;
```
GitHub: [83](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L83), [84](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L84), [85](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L85), [93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L93)


```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

     |  // @audit-issue Consider u/int256
  34 |  uint96 livenessBond,
```
GitHub: [34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L34)


```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

     |  // @audit-issue Consider u/int256
  36 |  uint96 validityBond,

     |  // @audit-issue Consider u/int256
  37 |  uint16 tier

     |  // @audit-issue Consider u/int256
  50 |  uint96 contestBond,

     |  // @audit-issue Consider u/int256
  51 |  uint16 tier

     |  // @audit-issue Consider u/int256
 100 |  returns (uint8 maxBlocksToVerify_)

     |  // @audit-issue Consider u/int256
 115 |  uint64 slot = _meta.id % _config.blockRingBufferSize;

     |  // @audit-issue Consider u/int256
 129 |  (uint32 tid, TaikoData.TransitionState storage ts) =

     |  // @audit-issue Consider u/int256
 273 |  uint64 slot

     |  // @audit-issue Consider u/int256
 276 |  returns (uint32 tid_, TaikoData.TransitionState storage ts_)

     |  // @audit-issue Consider u/int256
 405 |  uint32 _tid,
```
GitHub: [36](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L36), [37](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L37), [50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L50), [51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L51), [100](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L100), [115](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L115), [129](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L129), [273](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L273), [276](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L276), [405](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L405)


```solidity
File: packages/protocol/contracts/L1/libs/LibUtils.sol

     |  // @audit-issue Consider u/int256
  26 |  uint64 _blockId,

     |  // @audit-issue Consider u/int256
  38 |  uint64 slot = _blockId % _config.blockRingBufferSize;

     |  // @audit-issue Consider u/int256
  42 |  uint32 tid = getTransitionId(_state, blk, slot, _parentHash);

     |  // @audit-issue Consider u/int256
  55 |  uint64 _blockId

     |  // @audit-issue Consider u/int256
  59 |  returns (TaikoData.Block storage blk_, uint64 slot_)

     |  // @audit-issue Consider u/int256
  73 |  uint64 _slot,

     |  // @audit-issue Consider u/int256
  78 |  returns (uint32 tid_)
```
GitHub: [26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L26), [38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L38), [42](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L42), [55](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L55), [59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L59), [73](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L73), [78](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L78)


```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

     |  // @audit-issue Consider u/int256
  34 |  uint16 tier,

     |  // @audit-issue Consider u/int256
  35 |  uint8 contestations

     |  // @audit-issue Consider u/int256
  89 |  uint64 _maxBlocksToVerify

     |  // @audit-issue Consider u/int256
 100 |  uint64 blockId = b.lastVerifiedBlockId;

     |  // @audit-issue Consider u/int256
 102 |  uint64 slot = blockId % _config.blockRingBufferSize;

     |  // @audit-issue Consider u/int256
 107 |  uint32 tid = blk.verifiedTransitionId;

     |  // @audit-issue Consider u/int256
 117 |  uint64 numBlocksVerified;

     |  // @audit-issue Consider u/int256
 213 |  uint64 lastVerifiedBlockId = b.lastVerifiedBlockId + numBlocksVerified;

     |  // @audit-issue Consider u/int256
 227 |  uint64 _lastVerifiedBlockId,

     |  // @audit-issue Consider u/int256
 234 |  (uint64 lastSyncedBlock,) = signalService.getSyncedChainData(
```
GitHub: [34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L34), [35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L35), [89](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L89), [100](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L100), [102](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L102), [107](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L107), [117](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L117), [213](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L213), [227](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L227), [234](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L234)


```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

     |  // @audit-issue Consider u/int256
  27 |  uint32 public version;

     |  // @audit-issue Consider u/int256
  30 |  uint32 public minGuardians;

     |  // @audit-issue Consider u/int256
  37 |  event GuardiansUpdated(uint32 version, address[] guardians);

     |  // @audit-issue Consider u/int256
  55 |  uint8 _minGuardians
```
GitHub: [27](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L27), [30](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L30), [37](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L37), [55](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L55)


```solidity
File: packages/protocol/contracts/L1/TaikoData.sol

     |  // @audit-issue Consider u/int256
  15 |  uint64 chainId;

     |  // @audit-issue Consider u/int256
  20 |  uint64 blockMaxProposals;

     |  // @audit-issue Consider u/int256
  22 |  uint64 blockRingBufferSize;

     |  // @audit-issue Consider u/int256
  24 |  uint64 maxBlocksToVerifyPerProposal;

     |  // @audit-issue Consider u/int256
  26 |  uint32 blockMaxGasLimit;

     |  // @audit-issue Consider u/int256
  28 |  uint24 blockMaxTxListBytes;

     |  // @audit-issue Consider u/int256
  30 |  uint24 blobExpiry;

     |  // @audit-issue Consider u/int256
  39 |  uint96 livenessBond;

     |  // @audit-issue Consider u/int256
  46 |  uint64 ethDepositMinCountPerBlock;

     |  // @audit-issue Consider u/int256
  48 |  uint64 ethDepositMaxCountPerBlock;

     |  // @audit-issue Consider u/int256
  50 |  uint96 ethDepositMinAmount;

     |  // @audit-issue Consider u/int256
  52 |  uint96 ethDepositMaxAmount;

     |  // @audit-issue Consider u/int256
  59 |  uint8 blockSyncThreshold;

     |  // @audit-issue Consider u/int256
  64 |  uint16 tier;

     |  // @audit-issue Consider u/int256
  65 |  uint128 fee;

     |  // @audit-issue Consider u/int256
  69 |  uint16 tier;

     |  // @audit-issue Consider u/int256
  83 |  uint24 txListByteOffset;

     |  // @audit-issue Consider u/int256
  84 |  uint24 txListByteSize;

     |  // @audit-issue Consider u/int256
 101 |  uint64 id;

     |  // @audit-issue Consider u/int256
 102 |  uint32 gasLimit;

     |  // @audit-issue Consider u/int256
 103 |  uint64 timestamp; // slot 7

     |  // @audit-issue Consider u/int256
 104 |  uint64 l1Height;

     |  // @audit-issue Consider u/int256
 105 |  uint24 txListByteOffset;

     |  // @audit-issue Consider u/int256
 106 |  uint24 txListByteSize;

     |  // @audit-issue Consider u/int256
 107 |  uint16 minTier;

     |  // @audit-issue Consider u/int256
 127 |  uint96 validityBond;

     |  // @audit-issue Consider u/int256
 129 |  uint96 contestBond;

     |  // @audit-issue Consider u/int256
 130 |  uint64 timestamp; // slot 6 (90 bits)

     |  // @audit-issue Consider u/int256
 131 |  uint16 tier;

     |  // @audit-issue Consider u/int256
 132 |  uint8 contestations;

     |  // @audit-issue Consider u/int256
 140 |  uint96 livenessBond;

     |  // @audit-issue Consider u/int256
 141 |  uint64 blockId; // slot 3

     |  // @audit-issue Consider u/int256
 142 |  uint64 proposedAt; // timestamp

     |  // @audit-issue Consider u/int256
 143 |  uint64 proposedIn; // L1 block number

     |  // @audit-issue Consider u/int256
 144 |  uint32 nextTransitionId;

     |  // @audit-issue Consider u/int256
 145 |  uint32 verifiedTransitionId;

     |  // @audit-issue Consider u/int256
 152 |  uint96 amount;

     |  // @audit-issue Consider u/int256
 153 |  uint64 id;

     |  // @audit-issue Consider u/int256
 162 |  uint64 genesisHeight;

     |  // @audit-issue Consider u/int256
 163 |  uint64 genesisTimestamp;

     |  // @audit-issue Consider u/int256
 164 |  uint64 numEthDeposits;

     |  // @audit-issue Consider u/int256
 165 |  uint64 nextEthDepositToProcess;
```
GitHub: [15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L15), [20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L20), [22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L22), [24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L24), [26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L26), [28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L28), [30](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L30), [39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L39), [46](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L46), [48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L48), [50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L50), [52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L52), [59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L59), [64](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L64), [65](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L65), [69](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L69), [83](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L83), [84](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L84), [101](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L101), [102](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L102), [103](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L103), [104](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L104), [105](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L105), [106](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L106), [107](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L107), [127](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L127), [129](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L129), [130](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L130), [131](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L131), [132](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L132), [140](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L140), [141](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L141), [142](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L142), [143](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L143), [144](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L144), [145](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L145), [152](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L152), [153](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L153), [162](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L162), [163](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L163), [164](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L164), [165](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L165)


## [G-55] Use Solady library where possible to save gas

Utilizing gas-optimized math functions from libraries like [Solady](https://github.com/Vectorized/solady/blob/main/src/utils/FixedPointMathLib.sol) can lead to more efficient smart contracts.
This is particularly beneficial in contracts where these operations are frequently used.

For example, `(x * WAD) / y` can be replaced with Solady's `divWad()`.


*Instances: 13*

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

     |  // @audit-issue Consider using the Solady library for this arithmetic
 246 |  if (
 247 |      _config.chainId <= 1 || _config.chainId == block.chainid //
 248 |          || _config.blockMaxProposals == 1
 249 |          || _config.blockRingBufferSize <= _config.blockMaxProposals + 1
 250 |          || _config.blockMaxGasLimit == 0 || _config.blockMaxTxListBytes == 0
 251 |          || _config.blockMaxTxListBytes > 128 * 1024 // calldata up to 128K
 252 |          || _config.livenessBond == 0 || _config.ethDepositRingBufferSize <= 1
 253 |          || _config.ethDepositMinCountPerBlock == 0
 254 |      // Audit recommendation, and gas tested. Processing 32 deposits (as initially set in
 255 |      // TaikoL1.sol) costs 72_502 gas.
 256 |      || _config.ethDepositMaxCountPerBlock > 32
 257 |          || _config.ethDepositMaxCountPerBlock < _config.ethDepositMinCountPerBlock
 258 |          || _config.ethDepositMinAmount == 0
 259 |          || _config.ethDepositMaxAmount <= _config.ethDepositMinAmount
 260 |          || _config.ethDepositMaxAmount > type(uint96).max || _config.ethDepositGas == 0
 261 |          || _config.ethDepositMaxFee == 0
 262 |          || _config.ethDepositMaxFee > type(uint96).max / _config.ethDepositMaxCountPerBlock
 263 |  ) return false;
```
GitHub: [246-263](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L246-L263)


```solidity
File: packages/protocol/contracts/L2/Lib1559Math.sol

     |  // @audit-issue Consider using the Solady library for this arithmetic
  28 |  return _ethQty(_gasExcess, _adjustmentFactor) / LibFixedPointMath.SCALING_FACTOR
  29 |      / _adjustmentFactor;

     |  // @audit-issue Consider using the Solady library for this arithmetic
  41 |  uint256 input = _gasExcess * LibFixedPointMath.SCALING_FACTOR / _adjustmentFactor;
```
GitHub: [28-29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/Lib1559Math.sol#L28-L29), [41](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/Lib1559Math.sol#L41)


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

     |  // @audit-issue Consider using the Solady library for this arithmetic
 213 |  config_.gasTargetPerL1Block = 15 * 1e6 * 4;

     |  // @audit-issue Consider using the Solady library for this arithmetic
 262 |          if (gasExcess > 0) {
 263 |              // We always add the gas used by parent block to the gas excess
 264 |              // value as this has already happened
 265 |              uint256 excess = uint256(gasExcess) + _parentGasUsed;
 267 |              // Calculate how much more gas to issue to offset gas excess.
 268 |              // after each L1 block time, config.gasTarget more gas is issued,
 269 |              // the gas excess will be reduced accordingly.
 270 |              // Note that when lastSyncedBlock is zero, we skip this step
 271 |              // because that means this is the first time calculating the basefee
 272 |              // and the difference between the L1 height would be extremely big,
 273 |              // reverting the initial gas excess value back to 0.
 274 |              uint256 numL1Blocks;
 275 |              if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {
 276 |                  numL1Blocks = _l1BlockId - lastSyncedBlock;
 277 |              }
 279 |              if (numL1Blocks > 0) {
 280 |                  uint256 issuance = numL1Blocks * _config.gasTargetPerL1Block;
 281 |                  excess = excess > issuance ? excess - issuance : 1;
 282 |              }
 284 |              gasExcess_ = uint64(excess.min(type(uint64).max));
 286 |              // The base fee per gas used by this block is the spot price at the
 287 |              // bonding curve, regardless the actual amount of gas used by this
 288 |              // block, however, this block's gas used will affect the next
 289 |              // block's base fee.
 290 |              basefee_ = Lib1559Math.basefee(
 291 |                  gasExcess_, uint256(_config.basefeeAdjustmentQuotient) * _config.gasTargetPerL1Block
 292 |              );
 293 |          }
```
GitHub: [213](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L213), [262-293](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L262-L293)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

     |  // @audit-issue Consider using the Solady library for this arithmetic
  33 |          if (_len < 56) {
  34 |              out_ = new bytes(1);
  35 |              out_[0] = bytes1(uint8(_len) + uint8(_offset));
  36 |          } else {
  37 |              uint256 lenLen;
  38 |              uint256 i = 1;
  39 |              while (_len / i != 0) {
  40 |                  lenLen++;
  41 |                  i *= 256;
  42 |              }
  44 |              out_ = new bytes(lenLen + 1);
  45 |              out_[0] = bytes1(uint8(lenLen) + uint8(_offset) + 55);
  46 |              for (i = 1; i <= lenLen; i++) {
  47 |                  out_[i] = bytes1(uint8((_len / (256 ** (lenLen - i))) % 256));
  48 |              }
  49 |          }
```
GitHub: [33-49](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L33-L49)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

     |  // @audit-issue Consider using the Solady library for this arithmetic
 117 |  uint256 timeBasedAllowance = balance
 118 |      * (block.timestamp.min(claimEnd + withdrawalWindow) - claimEnd) / withdrawalWindow;
```
GitHub: [117-118](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L117-L118)


```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

     |  // @audit-issue Consider using the Solady library for this arithmetic
 264 |  return _amount * uint64(block.timestamp - _start) / _period;
```
GitHub: [264](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L264)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

     |  // @audit-issue Consider using the Solady library for this arithmetic
 153 |          for (uint256 i; i < encoded.length; ++i) {
 154 |              uint256 digits = uint256(uint8(bytes1(encoded[i])));
 155 |              uint256 upperDigit = digits / 16;
 156 |              uint256 lowerDigit = digits % 16;
 158 |              uint256 acc = lowerDigit * (16 ** (2 * i));
 159 |              acc += upperDigit * (16 ** ((2 * i) + 1));
 161 |              decoded += acc;
 162 |          }

     |  // @audit-issue Consider using the Solady library for this arithmetic
 158 |  uint256 acc = lowerDigit * (16 ** (2 * i));

     |  // @audit-issue Consider using the Solady library for this arithmetic
 159 |  acc += upperDigit * (16 ** ((2 * i) + 1));
```
GitHub: [153-162](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L153-L162), [158](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L158), [159](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L159)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

     |  // @audit-issue Consider using the Solady library for this arithmetic
  17 |  if (x509Time.length == 13) {
  18 |      if (uint8(x509Time[0]) - 48 < 5) yrs += 2000;
  19 |      else yrs += 1900;
  20 |  } else {
  21 |      yrs += (uint8(x509Time[0]) - 48) * 1000 + (uint8(x509Time[1]) - 48) * 100;
  22 |      offset = 2;
  23 |  }

     |  // @audit-issue Consider using the Solady library for this arithmetic
  21 |  yrs += (uint8(x509Time[0]) - 48) * 1000 + (uint8(x509Time[1]) - 48) * 100;
```
GitHub: [17-23](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L17-L23), [21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L21)


## [G-56] Use `<<` to efficiently multiple by powers of `2`

Multiplication by a power of `2` can be accomplished more efficiently using a left bit shift.

*Instances: 10*

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

     |  // @audit-issue Use `<<` to multiply because `32` is a power of 2
  21 |  uint256 public constant MAX_BYTES_PER_BLOB = 4096 * 32;

     |  // @audit-issue Use `<<` to multiply because `4096` is a power of 2
  21 |  uint256 public constant MAX_BYTES_PER_BLOB = 4096 * 32;
```
GitHub: [21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L21), [21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L21)


```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

     |  // @audit-issue Use `<<` to multiply because `1024` is a power of 2
 251 |  || _config.blockMaxTxListBytes > 128 * 1024 // calldata up to 128K

     |  // @audit-issue Use `<<` to multiply because `128` is a power of 2
 251 |  || _config.blockMaxTxListBytes > 128 * 1024 // calldata up to 128K
```
GitHub: [251](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L251), [251](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L251)


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

     |  // @audit-issue Use `<<` to multiply because `4` is a power of 2
 213 |  config_.gasTargetPerL1Block = 15 * 1e6 * 4;
```
GitHub: [213](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L213)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

     |  // @audit-issue Use `<<` to multiply because `2` is a power of 2
 158 |  uint256 acc = lowerDigit * (16 ** (2 * i));

     |  // @audit-issue Use `<<` to multiply because `2` is a power of 2
 159 |  acc += upperDigit * (16 ** ((2 * i) + 1));
```
GitHub: [158](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L158), [159](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L159)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

     |  // @audit-issue Use `<<` to multiply because `8` is a power of 2
 145 |  return uint256(der.readBytesN(ptr.ixf(), len) >> (32 - len) * 8);

     |  // @audit-issue Use `<<` to multiply because `8` is a power of 2
 203 |  der.readBytesN(ix + 2, lengthbytesLength) >> (32 - lengthbytesLength) * 8
```
GitHub: [145](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L145), [203](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L203)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

     |  // @audit-issue Use `<<` to multiply because `8` is a power of 2
  93 |  mask = ~(2 ** (8 * (32 - shortest + idx)) - 1);
```
GitHub: [93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L93)


## [G-57] Use `Array.unsafeAccess()` to avoid repeated array length checks

When using storage arrays, solidity adds an internal lookup of the array's length (a Gcoldsload **2100 gas**) to ensure you don't read past the array's end. You can avoid this lookup by using [`Array.unsafeAccess()`](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/94697be8a3f0dfcd95dfb13ffbd39b5973f5c65d/contracts/utils/Arrays.sol#L57) in cases where the length has already been checked, as is the case with the instances below.

*Instances: 28*

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

 173 |  if (_tierFees[i].tier == _tierId) return _tierFees[i].fee;
```
GitHub: [173](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L173), [173](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L173)


```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

  88 |  deposits_[i] = TaikoData.EthDeposit({
  :  |
  93 |  uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount;
  :  |
 101 |      deposits_[i].amount -= _fee;
```
GitHub: [88](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L88), [93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L93), [93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L93), [101](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L101)


```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

  75 |  delete guardianIds[guardians[i]];

  81 |  address guardian = _newGuardians[i];
```
GitHub: [75](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L75), [81](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L81)


```solidity
File: packages/protocol/contracts/signal/SignalService.sol

 105 |  hop = hopProofs[i];
```
GitHub: [105](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L105)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

  91 |  bytes32 msgHash = _msgHashes[i];
```
GitHub: [91](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L91)


```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

 171 |  IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);

 176 |  BridgedERC721(token_).mint(_to, _tokenIds[i]);
```
GitHub: [171](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L171), [176](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L176)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

  67 |  out_[j] = b[i++];
```
GitHub: [67](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L67)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

  86 |  TrieNode memory currentNode = proof[i];
```
GitHub: [86](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L86)


```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

 105 |  uint256 idx = _ids[i];

 211 |  if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();
  :  |
 213 |  addressRegistered[_instances[i]] = true;
  :  |
 215 |  if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();
  :  |
 217 |  instances[nextInstanceId] = Instance(_instances[i], validSince);
  :  |
 220 |  emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);
```
GitHub: [105](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L105), [211](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L211), [213](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L213), [215](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L215), [217](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L217), [220](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

  60 |  IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);
```
GitHub: [60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L60)


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

  81 |  if (_serialNumIsRevoked[index][serialNumBatch[i]]) {
  :  |
  84 |  _serialNumIsRevoked[index][serialNumBatch[i]] = true;

  96 |  if (!_serialNumIsRevoked[index][serialNumBatch[i]]) {
  :  |
  99 |  delete _serialNumIsRevoked[index][serialNumBatch[i]];
```
GitHub: [81](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L81), [84](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L84), [96](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L96), [99](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L99)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

 245 |  contentStr = LibString.concat(contentStr, split[i]);
```
GitHub: [245](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L245)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

 154 |  uint256 digits = uint256(uint8(bytes1(encoded[i])));
```
GitHub: [154](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L154)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

 284 |  if (decipher[3 + paddingLen + i] != bytes1(sha1Prefix[i])) {
```
GitHub: [284](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L284)


## [G-58] Use `bytes32` in place of string

For `string`s of up to `32` characters you can use `bytes32` instead as it's more gas efficient.

*Instances: 7*

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

     |  // @audit-issue Consider `bytes32` type
 108 |  return string(
 109 |      abi.encodePacked(
 110 |          LibBridgedToken.buildURI(srcToken, srcChainId), Strings.toString(_tokenId)
 111 |      )
 112 |  );
```
GitHub: [108-112](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L108-L112)


```solidity
File: packages/protocol/contracts/tokenvault/LibBridgedToken.sol

     |  // @audit-issue Consider `bytes32` type
  53 |  return string(
  54 |      abi.encodePacked(
  55 |          "ethereum:",
  56 |          Strings.toHexString(uint160(_srcToken), 20),
  57 |          "@",
  58 |          Strings.toString(_srcChainId),
  59 |          "/tokenURI?uint256="
  60 |      )
  61 |  );
```
GitHub: [53-61](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L53-L61)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

     |  // @audit-issue Consider `bytes32` type
  49 |  string memory pemChainStr = string(pemChain);

     |  // @audit-issue Consider `bytes32` type
 119 |  cert.pck.issuerName = string(der.bytesAt(issuerPtr));

     |  // @audit-issue Consider `bytes32` type
 151 |  cert.pck.commonName = string(der.bytesAt(subjectPtr));

     |  // @audit-issue Consider `bytes32` type
 241 |  string[] memory split = LibString.split(contentSlice, string(delimiter));
```
GitHub: [49](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L49), [119](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L119), [151](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L151), [241](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L241)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

     |  // @audit-issue Consider `bytes32` type
 282 |  quoteCerts[i] = Base64.decode(string(quoteCerts[i]));
```
GitHub: [282](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L282)


## [G-59] Use `calldata` instead of `memory` for function arguments that are read only

When a function with a `memory` array is called externally, the `abi.decode()` step has to use a for-loop to copy each index of the `calldata` to the `memory` index. Each iteration of this for-loop costs at least 60 gas (i.e. 60 * `<mem_array>.length`). Using calldata directly, removes the need for such a loop in the contract code and runtime execution.  
                    
If the array is passed to an `internal` function which passes the array to another `internal` function where the array is modified and therefore `memory` is used in the `external` call, it's still more gas-efficient to use `calldata` when the external function uses modifiers, since the modifiers may prevent the `internal` functions from being called. `Structs` have the same overhead as an array of length one.

*Instances: 99*

```solidity
File: packages/protocol/contracts/libs/Lib4844.sol

     |  // @audit-issue Consider switching `_commitment` param to `calldata`
  34 |  bytes1[48] memory _commitment,
     |  // @audit-issue Consider switching `_pointProof` param to `calldata`
  35 |  bytes1[48] memory _pointProof
```
GitHub: [34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/Lib4844.sol#L34), [35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/Lib4844.sol#L35)


```solidity
File: packages/protocol/contracts/libs/LibTrieProof.sol

     |  // @audit-issue Consider switching `_accountProof` param to `calldata`
  39 |  bytes[] memory _accountProof,
     |  // @audit-issue Consider switching `_storageProof` param to `calldata`
  40 |  bytes[] memory _storageProof
```
GitHub: [39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibTrieProof.sol#L39), [40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibTrieProof.sol#L40)


```solidity
File: packages/protocol/contracts/L1/gov/TaikoGovernor.sol

     |  // @audit-issue Consider switching `_targets` param to `calldata`
  49 |  address[] memory _targets,
     |  // @audit-issue Consider switching `_values` param to `calldata`
  50 |  uint256[] memory _values,
     |  // @audit-issue Consider switching `_calldatas` param to `calldata`
  51 |  bytes[] memory _calldatas,

     |  // @audit-issue Consider switching `_targets` param to `calldata`
  70 |  address[] memory _targets,
     |  // @audit-issue Consider switching `_values` param to `calldata`
  71 |  uint256[] memory _values,
     |  // @audit-issue Consider switching `_signatures` param to `calldata`
  72 |  string[] memory _signatures,
     |  // @audit-issue Consider switching `_calldatas` param to `calldata`
  73 |  bytes[] memory _calldatas,

     |  // @audit-issue Consider switching `_targets` param to `calldata`
 129 |  address[] memory _targets,
     |  // @audit-issue Consider switching `_values` param to `calldata`
 130 |  uint256[] memory _values,
     |  // @audit-issue Consider switching `_calldatas` param to `calldata`
 131 |  bytes[] memory _calldatas,

     |  // @audit-issue Consider switching `_targets` param to `calldata`
 141 |  address[] memory _targets,
     |  // @audit-issue Consider switching `_values` param to `calldata`
 142 |  uint256[] memory _values,
     |  // @audit-issue Consider switching `_calldatas` param to `calldata`
 143 |  bytes[] memory _calldatas,
```
GitHub: [49](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L49), [50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L50), [51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L51), [70](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L70), [71](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L71), [72](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L72), [73](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L73), [129](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L129), [130](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L130), [131](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L131), [141](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L141), [142](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L142), [143](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L143)


```solidity
File: packages/protocol/contracts/L1/hooks/IHook.sol

     |  // @audit-issue Consider switching `_blk` param to `calldata`
  14 |  TaikoData.Block memory _blk,
     |  // @audit-issue Consider switching `_meta` param to `calldata`
  15 |  TaikoData.BlockMetadata memory _meta,
```
GitHub: [14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/IHook.sol#L14), [15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/IHook.sol#L15)


```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

     |  // @audit-issue Consider switching `_blk` param to `calldata`
  63 |  TaikoData.Block memory _blk,
     |  // @audit-issue Consider switching `_meta` param to `calldata`
  64 |  TaikoData.BlockMetadata memory _meta,

     |  // @audit-issue Consider switching `_assignment` param to `calldata`
 138 |  ProverAssignment memory _assignment,

     |  // @audit-issue Consider switching `_tierFees` param to `calldata`
 165 |  TaikoData.TierFee[] memory _tierFees,
```
GitHub: [63](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L63), [64](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L64), [138](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L138), [165](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L165)


```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

     |  // @audit-issue Consider switching `_config` param to `calldata`
  31 |  TaikoData.Config memory _config,

     |  // @audit-issue Consider switching `_config` param to `calldata`
  69 |  TaikoData.Config memory _config,

     |  // @audit-issue Consider switching `_config` param to `calldata`
 124 |  TaikoData.Config memory _config,
```
GitHub: [31](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L31), [69](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L69), [124](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L124)


```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

     |  // @audit-issue Consider switching `_config` param to `calldata`
  70 |  TaikoData.Config memory _config,

     |  // @audit-issue Consider switching `_config` param to `calldata`
 289 |  TaikoData.Config memory _config,

     |  // @audit-issue Consider switching `_slotB` param to `calldata`
 300 |  TaikoData.SlotB memory _slotB,
```
GitHub: [70](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L70), [289](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L289), [300](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L300)


```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

     |  // @audit-issue Consider switching `_config` param to `calldata`
  93 |  TaikoData.Config memory _config,
  :  |
     |  // @audit-issue Consider switching `_meta` param to `calldata`
  95 |  TaikoData.BlockMetadata memory _meta,
     |  // @audit-issue Consider switching `_tran` param to `calldata`
  96 |  TaikoData.Transition memory _tran,
     |  // @audit-issue Consider switching `_proof` param to `calldata`
  97 |  TaikoData.TierProof memory _proof

     |  // @audit-issue Consider switching `_tran` param to `calldata`
 272 |  TaikoData.Transition memory _tran,

     |  // @audit-issue Consider switching `_tran` param to `calldata`
 352 |  TaikoData.Transition memory _tran,
     |  // @audit-issue Consider switching `_proof` param to `calldata`
 353 |  TaikoData.TierProof memory _proof,
     |  // @audit-issue Consider switching `_tier` param to `calldata`
 354 |  ITierProvider.Tier memory _tier,

     |  // @audit-issue Consider switching `_tier` param to `calldata`
 406 |  ITierProvider.Tier memory _tier
```
GitHub: [93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L93), [95](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L95), [96](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L96), [97](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L97), [272](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L272), [352](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L352), [353](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L353), [354](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L354), [406](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L406)


```solidity
File: packages/protocol/contracts/L1/libs/LibUtils.sol

     |  // @audit-issue Consider switching `_config` param to `calldata`
  25 |  TaikoData.Config memory _config,

     |  // @audit-issue Consider switching `_config` param to `calldata`
  54 |  TaikoData.Config memory _config,
```
GitHub: [25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L25), [54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L54)


```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

     |  // @audit-issue Consider switching `_config` param to `calldata`
  49 |  TaikoData.Config memory _config,

     |  // @audit-issue Consider switching `_config` param to `calldata`
  87 |  TaikoData.Config memory _config,

     |  // @audit-issue Consider switching `_config` param to `calldata`
 225 |  TaikoData.Config memory _config,

     |  // @audit-issue Consider switching `_config` param to `calldata`
 245 |  function _isConfigValid(TaikoData.Config memory _config) private view returns (bool) {
```
GitHub: [49](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L49), [87](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L87), [225](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L225), [245](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L245)


```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

     |  // @audit-issue Consider switching `_newGuardians` param to `calldata`
  54 |  address[] memory _newGuardians,
```
GitHub: [54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L54)


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

     |  // @audit-issue Consider switching `_config` param to `calldata`
 253 |  Config memory _config,
```
GitHub: [253](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L253)


```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

     |  // @audit-issue Consider switching `_newConfig` param to `calldata`
  26 |  Config memory _newConfig,
```
GitHub: [26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L26)


```solidity
File: packages/protocol/contracts/signal/SignalService.sol

     |  // @audit-issue Consider switching `_hop` param to `calldata`
 211 |  HopProof memory _hop,

     |  // @audit-issue Consider switching `_hop` param to `calldata`
 272 |  HopProof memory _hop,
```
GitHub: [211](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L211), [272](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L272)


```solidity
File: packages/protocol/contracts/bridge/IBridge.sol

     |  // @audit-issue Consider switching `_message` param to `calldata`
 155 |  function hashMessage(Message memory _message) external pure returns (bytes32);
```
GitHub: [155](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/IBridge.sol#L155)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

     |  // @audit-issue Consider switching `_message` param to `calldata`
 449 |  function hashMessage(Message memory _message) public pure returns (bytes32) {
```
GitHub: [449](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L449)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

     |  // @audit-issue Consider switching `_tokenIds` param to `calldata`
  85 |  uint256[] memory _tokenIds,
     |  // @audit-issue Consider switching `_amounts` param to `calldata`
  86 |  uint256[] memory _amounts

     |  // @audit-issue Consider switching `` param to `calldata`
 129 |  uint256[] memory, /*_ids*/
     |  // @audit-issue Consider switching `` param to `calldata`
 130 |  uint256[] memory, /*_amounts*/
```
GitHub: [85](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L85), [86](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L86), [129](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L129), [130](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L130)


```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

     |  // @audit-issue Consider switching `_op` param to `calldata`
  39 |  function sendToken(BridgeTransferOp memory _op)

     |  // @audit-issue Consider switching `ctoken` param to `calldata`
 215 |  CanonicalNFT memory ctoken,
  :  |
     |  // @audit-issue Consider switching `tokenIds` param to `calldata`
 217 |  uint256[] memory tokenIds,
     |  // @audit-issue Consider switching `amounts` param to `calldata`
 218 |  uint256[] memory amounts

     |  // @audit-issue Consider switching `_op` param to `calldata`
 242 |  BridgeTransferOp memory _op

     |  // @audit-issue Consider switching `_ctoken` param to `calldata`
 288 |  function _getOrDeployBridgedToken(CanonicalNFT memory _ctoken)

     |  // @audit-issue Consider switching `_ctoken` param to `calldata`
 303 |  function _deployBridgedToken(CanonicalNFT memory _ctoken) private returns (address btoken_) {
```
GitHub: [39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L39), [215](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L215), [217](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L217), [218](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L218), [242](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L242), [288](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L288), [303](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L303)


```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

     |  // @audit-issue Consider switching `_ctoken` param to `calldata`
 321 |  CanonicalERC20 memory _ctoken,

     |  // @audit-issue Consider switching `ctoken` param to `calldata`
 391 |  function _getOrDeployBridgedToken(CanonicalERC20 memory ctoken)

     |  // @audit-issue Consider switching `ctoken` param to `calldata`
 407 |  function _deployBridgedToken(CanonicalERC20 memory ctoken) private returns (address btoken) {
```
GitHub: [321](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L321), [391](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L391), [407](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L407)


```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

     |  // @audit-issue Consider switching `_op` param to `calldata`
  26 |  function sendToken(BridgeTransferOp memory _op)

     |  // @audit-issue Consider switching `_ctoken` param to `calldata`
 161 |  CanonicalNFT memory _ctoken,
  :  |
     |  // @audit-issue Consider switching `_tokenIds` param to `calldata`
 163 |  uint256[] memory _tokenIds

     |  // @audit-issue Consider switching `_op` param to `calldata`
 189 |  BridgeTransferOp memory _op

     |  // @audit-issue Consider switching `_ctoken` param to `calldata`
 224 |  function _getOrDeployBridgedToken(CanonicalNFT memory _ctoken)

     |  // @audit-issue Consider switching `_ctoken` param to `calldata`
 240 |  function _deployBridgedToken(CanonicalNFT memory _ctoken) private returns (address btoken_) {
```
GitHub: [26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L26), [161](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L161), [163](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L163), [189](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L189), [224](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L224), [240](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L240)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

     |  // @audit-issue Consider switching `_in` param to `calldata`
  53 |  function readList(RLPItem memory _in) internal pure returns (RLPItem[] memory out_) {

     |  // @audit-issue Consider switching `_in` param to `calldata`
 109 |  function readBytes(RLPItem memory _in) internal pure returns (bytes memory out_) {

     |  // @audit-issue Consider switching `_in` param to `calldata`
 135 |  function readRawBytes(RLPItem memory _in) internal pure returns (bytes memory out_) {

     |  // @audit-issue Consider switching `_in` param to `calldata`
 144 |  function _decodeLength(RLPItem memory _in)
```
GitHub: [53](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L53), [109](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L109), [135](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L135), [144](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L144)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

     |  // @audit-issue Consider switching `_proof` param to `calldata`
  53 |  bytes[] memory _proof,

     |  // @audit-issue Consider switching `_proof` param to `calldata`
  70 |  bytes[] memory _proof,

     |  // @audit-issue Consider switching `_proof` param to `calldata`
 205 |  function _parseProof(bytes[] memory _proof) private pure returns (TrieNode[] memory proof_) {

     |  // @audit-issue Consider switching `_node` param to `calldata`
 220 |  function _getNodeID(RLPReader.RLPItem memory _node) private pure returns (bytes memory id_) {

     |  // @audit-issue Consider switching `_node` param to `calldata`
 227 |  function _getNodePath(TrieNode memory _node) private pure returns (bytes memory nibbles_) {
```
GitHub: [53](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L53), [70](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L70), [205](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L205), [220](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L220), [227](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L227)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol

     |  // @audit-issue Consider switching `_proof` param to `calldata`
  22 |  bytes[] memory _proof,

     |  // @audit-issue Consider switching `_proof` param to `calldata`
  40 |  bytes[] memory _proof,
```
GitHub: [22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L22), [40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L40)


```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

     |  // @audit-issue Consider switching `_tran` param to `calldata`
 172 |  TaikoData.Transition memory _tran,

     |  // @audit-issue Consider switching `_instances` param to `calldata`
 196 |  address[] memory _instances,
```
GitHub: [172](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L172), [196](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L196)


```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

     |  // @audit-issue Consider switching `_grant` param to `calldata`
 135 |  function grant(address _recipient, Grant memory _grant) external onlyOwner {

     |  // @audit-issue Consider switching `_grant` param to `calldata`
 235 |  function _getAmountOwned(Grant memory _grant) private view returns (uint128) {

     |  // @audit-issue Consider switching `_grant` param to `calldata`
 239 |  function _getAmountUnlocked(Grant memory _grant) private view returns (uint128) {

     |  // @audit-issue Consider switching `_grant` param to `calldata`
 267 |  function _validateGrant(Grant memory _grant) private pure {
```
GitHub: [135](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L135), [235](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L235), [239](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L239), [267](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L267)


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

     |  // @audit-issue Consider switching `quoteEnclaveReport` param to `calldata`
 175 |  function _verifyQEReportWithIdentity(V3Struct.EnclaveReport memory quoteEnclaveReport)

     |  // @audit-issue Consider switching `pck` param to `calldata`
 207 |  IPEMCertChainLib.PCKCertificateField memory pck,
     |  // @audit-issue Consider switching `tcb` param to `calldata`
 208 |  TCBInfoStruct.TCBInfo memory tcb

     |  // @audit-issue Consider switching `pckCpuSvns` param to `calldata`
 230 |  uint256[] memory pckCpuSvns,
     |  // @audit-issue Consider switching `tcbCpuSvns` param to `calldata`
 231 |  uint8[] memory tcbCpuSvns

     |  // @audit-issue Consider switching `certs` param to `calldata`
 248 |  function _verifyCertChain(IPEMCertChainLib.ECSha256Certificate[] memory certs)

     |  // @audit-issue Consider switching `authDataV3` param to `calldata`
 306 |  V3Struct.ECDSAQuoteV3AuthData memory authDataV3,
     |  // @audit-issue Consider switching `qeEnclaveReport` param to `calldata`
 307 |  V3Struct.EnclaveReport memory qeEnclaveReport

     |  // @audit-issue Consider switching `v3quote` param to `calldata`
 364 |  function _verifyParsedQuote(V3Struct.ParsedV3QuoteStruct memory v3quote)
```
GitHub: [175](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L175), [207](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L207), [208](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L208), [230](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L230), [231](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L231), [248](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L248), [306](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L306), [307](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L307), [364](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L364)


```solidity
File: packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol

     |  // @audit-issue Consider switching `publicKey` param to `calldata`
  41 |  PublicKey memory publicKey,

     |  // @audit-issue Consider switching `publicKey` param to `calldata`
  51 |  PublicKey memory publicKey,
```
GitHub: [41](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L41), [51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L51)


## [G-60] Use `uint256(1)`/`uint256(2)` instead of `true`/`false` to save gas for changes

Avoids a Gsset (**20000 gas**) when changing from `false` to `true`, after having been `true` in the past. Since most of the bools aren't changed twice in one transaction, I've counted the amount of gas as half of the full amount, for each variable.

*Instances: 10*

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

  21 |  mapping(address addr => bool authorized) public isAuthorized;
```
GitHub: [21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L21)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

  42 |  mapping(address addr => bool banned) public addressBanned;
```
GitHub: [42](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L42)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

  14 |  bool public migratingInbound;
```
GitHub: [14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L14)


```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

  52 |  mapping(address btoken => bool blacklisted) public btokenBlacklist;
```
GitHub: [52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L52)


```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

  55 |  mapping(address instanceAddress => bool alreadyAttested) public addressRegistered;
```
GitHub: [55](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L55)


```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

  12 |  mapping(bytes32 hash => bool claimed) public isClaimed;
```
GitHub: [12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L12)


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

  38 |  bool private _checkLocalEnclaveReport;

  39 |  mapping(bytes32 enclave => bool trusted) private _trustedUserMrEnclave;

  40 |  mapping(bytes32 signer => bool trusted) private _trustedUserMrSigner;

  47 |  mapping(uint256 idx => mapping(bytes serialNum => bool revoked)) private _serialNumIsRevoked;
```
GitHub: [38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L38), [39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L39), [40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L40), [47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L47)


## [G-61] Use assembly to calculate hashes

If the arguments to the encode call can fit into the scratch space (two words or fewer), then it's more efficient to use assembly to generate the hash (**80 gas**):
                    
```solidity
    keccak256(abi.encodePacked(a, b)); }
```

to

```solidity 
    assembly {
        mstore(0x00, a)
        mstore(0x20, b)
        let result := keccak256(0x00, 0x40)
    }
```

*Instances: 28*

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

     |  // @audit-issue Use assembly to calcuate hashes
 146 |  return keccak256(
 147 |      abi.encode(
 148 |          "PROVER_ASSIGNMENT",
 149 |          ITaikoL1(_taikoL1Address).getConfig().chainId,
 150 |          _taikoL1Address,
 151 |          address(this),
 152 |          _assignment.metaHash,
 153 |          _assignment.parentMetaHash,
 154 |          _blobHash,
 155 |          _assignment.feeToken,
 156 |          _assignment.expiry,
 157 |          _assignment.maxBlockId,
 158 |          _assignment.maxProposedIn,
 159 |          _assignment.tierFees
 160 |      )
 161 |  );
```
GitHub: [146-161](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L146-L161)


```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

     |  // @audit-issue Use assembly to calcuate hashes
 126 |  depositsHash: keccak256(abi.encode(deposits_)),

     |  // @audit-issue Use assembly to calcuate hashes
 189 |  meta_.blobHash = keccak256(_txList);

     |  // @audit-issue Use assembly to calcuate hashes
 204 |  meta_.difficulty = keccak256(abi.encodePacked(block.prevrandao, b.numBlocks, block.number));

     |  // @audit-issue Use assembly to calcuate hashes
 213 |  metaHash: keccak256(abi.encode(meta_)),
```
GitHub: [126](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L126), [189](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L189), [204](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L204), [213](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L213)


```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

     |  // @audit-issue Use assembly to calcuate hashes
  20 |  bytes32 public constant RETURN_LIVENESS_BOND = keccak256("RETURN_LIVENESS_BOND");

     |  // @audit-issue Use assembly to calcuate hashes
 121 |  if (blk.blockId != _meta.id || blk.metaHash != keccak256(abi.encode(_meta))) {
```
GitHub: [20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L20), [121](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L121)


```solidity
File: packages/protocol/contracts/L1/provers/GuardianProver.sol

     |  // @audit-issue Use assembly to calcuate hashes
  46 |  bytes32 hash = keccak256(abi.encode(_meta, _tran));
```
GitHub: [46](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/GuardianProver.sol#L46)


```solidity
File: packages/protocol/contracts/signal/LibSignals.sol

     |  // @audit-issue Use assembly to calcuate hashes
   8 |  bytes32 public constant STATE_ROOT = keccak256("STATE_ROOT");

     |  // @audit-issue Use assembly to calcuate hashes
  11 |  bytes32 public constant SIGNAL_ROOT = keccak256("SIGNAL_ROOT");
```
GitHub: [8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/LibSignals.sol#L8), [11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/LibSignals.sol#L11)


```solidity
File: packages/protocol/contracts/signal/SignalService.sol

     |  // @audit-issue Use assembly to calcuate hashes
 186 |  return keccak256(abi.encode(_chainId, _kind, _blockId));

     |  // @audit-issue Use assembly to calcuate hashes
 203 |  return keccak256(abi.encodePacked("SIGNAL", _chainId, _app, _signal));
```
GitHub: [186](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L186), [203](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L203)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

     |  // @audit-issue Use assembly to calcuate hashes
 450 |  return keccak256(abi.encode("TAIKO_MESSAGE", _message));
```
GitHub: [450](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L450)


```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

     |  // @audit-issue Use assembly to calcuate hashes
 176 |  || keccak256(bytes(ctoken.symbol)) != keccak256(bytes(_ctoken.symbol))

     |  // @audit-issue Use assembly to calcuate hashes
 176 |  || keccak256(bytes(ctoken.symbol)) != keccak256(bytes(_ctoken.symbol))

     |  // @audit-issue Use assembly to calcuate hashes
 177 |  || keccak256(bytes(ctoken.name)) != keccak256(bytes(_ctoken.name))

     |  // @audit-issue Use assembly to calcuate hashes
 177 |  || keccak256(bytes(ctoken.name)) != keccak256(bytes(_ctoken.name))
```
GitHub: [176](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L176), [176](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L176), [177](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L177), [177](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L177)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/Bytes.sol

     |  // @audit-issue Use assembly to calcuate hashes
 150 |  return keccak256(_bytes) == keccak256(_other);

     |  // @audit-issue Use assembly to calcuate hashes
 150 |  return keccak256(_bytes) == keccak256(_other);
```
GitHub: [150](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L150), [150](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L150)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

     |  // @audit-issue Use assembly to calcuate hashes
  94 |  Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),

     |  // @audit-issue Use assembly to calcuate hashes
 100 |  Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
```
GitHub: [94](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L94), [100](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L100)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol

     |  // @audit-issue Use assembly to calcuate hashes
  55 |  hash_ = abi.encodePacked(keccak256(_key));
```
GitHub: [55](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L55)


```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

     |  // @audit-issue Use assembly to calcuate hashes
 182 |  return keccak256(
 183 |      abi.encode(
 184 |          "VERIFY_PROOF",
 185 |          ITaikoL1(taikoL1).getConfig().chainId,
 186 |          address(this),
 187 |          _tran,
 188 |          _newInstance,
 189 |          _prover,
 190 |          _metaHash
 191 |      )
 192 |  );
```
GitHub: [182-192](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L182-L192)


```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

     |  // @audit-issue Use assembly to calcuate hashes
  68 |  bytes32 hash = keccak256(abi.encode("CLAIM_TAIKO_AIRDROP", data));
```
GitHub: [68](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L68)


```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

     |  // @audit-issue Use assembly to calcuate hashes
 170 |  bytes32 hash = keccak256(abi.encodePacked("Withdraw unlocked Taiko token to: ", _to));
```
GitHub: [170](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L170)


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

     |  // @audit-issue Use assembly to calcuate hashes
 292 |  bytes32 issuerPubKeyHash = keccak256(issuer.pubKey);
```
GitHub: [292](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L292)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

     |  // @audit-issue Use assembly to calcuate hashes
 372 |  return keccak256(a) == keccak256(b);

     |  // @audit-issue Use assembly to calcuate hashes
 372 |  return keccak256(a) == keccak256(b);
```
GitHub: [372](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L372), [372](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L372)


## [G-62] Use assembly to perform external calls, in order to save gas

Using Solidity's assembly scratch space for constructing calldata in external calls with one or two arguments can be a gas-efficient approach. This method leverages the designated memory area (the first 64 bytes of memory) for temporary data storage during assembly operations. By directly writing arguments into this scratch space, it eliminates the need for additional memory allocation typically required for calldata preparation. This technique can lead to notable gas savings, especially in high-frequency or gas-sensitive operations. However, it requires careful implementation to avoid data corruption and should be used with a thorough understanding of low-level EVM operations and memory handling. Proper testing and validation are crucial when employing such optimizations.

*Instances: 3*

```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

     |  // @audit-issue Save gas by call this in assembly
  83 |  addr_ = payable(IAddressManager(addressManager).getAddress(_chainId, _name));
```
GitHub: [83](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L83)


```solidity
File: packages/protocol/contracts/libs/LibAddress.sol

     |  // @audit-issue Save gas by call this in assembly
  56 |  try IERC165(_addr).supportsInterface(_interfaceId) returns (bool _result) {

     |  // @audit-issue Save gas by call this in assembly
  71 |  return IERC1271(_addr).isValidSignature(_hash, _sig) == _EIP1271_MAGICVALUE;
```
GitHub: [56](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L56), [71](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L71)


## [G-63] Use assembly to write storage values

Instead of:
                    
```solidity
owner = _newOwner
```

write:

```solidity
assembly { sstore(owner.slot, _newOwner) }
```


*Instances: 85*

```solidity
File: packages/protocol/contracts/common/AddressManager.sol

     |  // @audit-issue Use assembly `sstore` to save gas
  49 |  __addresses[_chainId][_name] = _newAddress;
```
GitHub: [49](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L49)


```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

     |  // @audit-issue Use assembly `sstore` to save gas
  62 |  addressManager = _addressManager;
```
GitHub: [62](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L62)


```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

     |  // @audit-issue Use assembly `sstore` to save gas
  70 |  __paused = _TRUE;

     |  // @audit-issue Use assembly `sstore` to save gas
  79 |  __paused = _FALSE;

     |  // @audit-issue Use assembly `sstore` to save gas
 111 |  __paused = _FALSE;

     |  // @audit-issue Use assembly `sstore` to save gas
 125 |  __reentry = _reentry;
```
GitHub: [70](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L70), [79](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L79), [111](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L111), [125](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L125)


```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

     |  // @audit-issue Use assembly `sstore` to save gas
  88 |  guardianIds[guardian] = guardians.length;

     |  // @audit-issue Use assembly `sstore` to save gas
  94 |  minGuardians = _minGuardians;

     |  // @audit-issue Use assembly `sstore` to save gas
 116 |  _approvals[version][_hash] |= 1 << (id - 1);
```
GitHub: [88](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L88), [94](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L94), [116](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L116)


```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

     |  // @audit-issue Use assembly `sstore` to save gas
 126 |  state.slotB.lastUnpausedAt = uint64(block.timestamp);
```
GitHub: [126](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L126)


```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

     |  // @audit-issue Use assembly `sstore` to save gas
  73 |  ownerChainId = _ownerChainId;
```
GitHub: [73](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L73)


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

     |  // @audit-issue Use assembly `sstore` to save gas
  91 |  l2Hashes[parentHeight] = blockhash(parentHeight);

     |  // @audit-issue Use assembly `sstore` to save gas
  96 |  gasExcess = _gasExcess;

     |  // @audit-issue Use assembly `sstore` to save gas
  97 |  (publicInputHash,) = _calcPublicInputHash(block.number);

     |  // @audit-issue Use assembly `sstore` to save gas
 140 |  (basefee, gasExcess) = _calc1559BaseFee(config, _l1BlockId, _parentGasUsed);

     |  // @audit-issue Use assembly `sstore` to save gas
 151 |  lastSyncedBlock = _l1BlockId;

     |  // @audit-issue Use assembly `sstore` to save gas
 154 |  l2Hashes[parentId] = blockhash(parentId);

     |  // @audit-issue Use assembly `sstore` to save gas
 155 |  publicInputHash = publicInputHashNew;
```
GitHub: [91](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L91), [96](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L96), [97](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L97), [140](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L140), [151](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L151), [154](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L154), [155](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L155)


```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

     |  // @audit-issue Use assembly `sstore` to save gas
  36 |  customConfig = _newConfig;

     |  // @audit-issue Use assembly `sstore` to save gas
  37 |  gasExcess = _newGasExcess;
```
GitHub: [36](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L36), [37](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L37)


```solidity
File: packages/protocol/contracts/signal/SignalService.sol

     |  // @audit-issue Use assembly `sstore` to save gas
  58 |  isAuthorized[_addr] = _authorize;

     |  // @audit-issue Use assembly `sstore` to save gas
 248 |  topBlockId[_chainId][_kind] = _blockId;
```
GitHub: [58](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L58), [248](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L248)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

     |  // @audit-issue Use assembly `sstore` to save gas
  92 |  proofReceipt[msgHash].receivedAt = _timestamp;

     |  // @audit-issue Use assembly `sstore` to save gas
 110 |  addressBanned[_addr] = _ban;

     |  // @audit-issue Use assembly `sstore` to save gas
 184 |  proofReceipt[msgHash].receivedAt = receivedAt;

     |  // @audit-issue Use assembly `sstore` to save gas
 191 |  messageStatus[msgHash] = Status.RECALLED;

     |  // @audit-issue Use assembly `sstore` to save gas
 243 |  proofReceipt[msgHash] = ProofReceipt({
 244 |      receivedAt: receivedAt,
 245 |      preferredExecutor: _message.gasLimit == 0 ? _message.destOwner : msg.sender
 246 |  });

     |  // @audit-issue Use assembly `sstore` to save gas
 518 |  messageStatus[_msgHash] = _status;

     |  // @audit-issue Use assembly `sstore` to save gas
 549 |  __ctx = Context(_msgHash, _from, _srcChainId);
```
GitHub: [92](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L92), [110](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L110), [184](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L184), [191](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L191), [243-246](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L243-L246), [518](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L518), [549](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L549)


```solidity
File: packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

     |  // @audit-issue Use assembly `sstore` to save gas
  40 |  usdc = _usdc;
```
GitHub: [40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L40)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

     |  // @audit-issue Use assembly `sstore` to save gas
  73 |  srcToken = _srcToken;

     |  // @audit-issue Use assembly `sstore` to save gas
  74 |  srcChainId = _srcChainId;

     |  // @audit-issue Use assembly `sstore` to save gas
  75 |  __srcDecimals = _decimals;

     |  // @audit-issue Use assembly `sstore` to save gas
  81 |  snapshooter = _snapshooter;
```
GitHub: [73](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L73), [74](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L74), [75](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L75), [81](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L81)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

     |  // @audit-issue Use assembly `sstore` to save gas
  49 |  migratingAddress = _migratingAddress;

     |  // @audit-issue Use assembly `sstore` to save gas
  50 |  migratingInbound = _migratingInbound;
```
GitHub: [49](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L49), [50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L50)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

     |  // @audit-issue Use assembly `sstore` to save gas
  47 |  srcToken = _srcToken;

     |  // @audit-issue Use assembly `sstore` to save gas
  48 |  srcChainId = _srcChainId;
```
GitHub: [47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L47), [48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L48)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

     |  // @audit-issue Use assembly `sstore` to save gas
  56 |  srcToken = _srcToken;

     |  // @audit-issue Use assembly `sstore` to save gas
  57 |  srcChainId = _srcChainId;

     |  // @audit-issue Use assembly `sstore` to save gas
  58 |  __symbol = _symbol;

     |  // @audit-issue Use assembly `sstore` to save gas
  59 |  __name = _name;
```
GitHub: [56](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L56), [57](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L57), [58](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L58), [59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L59)


```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

     |  // @audit-issue Use assembly `sstore` to save gas
 311 |  bridgedToCanonical[btoken_] = _ctoken;

     |  // @audit-issue Use assembly `sstore` to save gas
 312 |  canonicalToBridged[_ctoken.chainId][_ctoken.addr] = btoken_;
```
GitHub: [311](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L311), [312](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L312)


```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

     |  // @audit-issue Use assembly `sstore` to save gas
 181 |  btokenBlacklist[btokenOld_] = true;

     |  // @audit-issue Use assembly `sstore` to save gas
 188 |  bridgedToCanonical[_btokenNew] = _ctoken;

     |  // @audit-issue Use assembly `sstore` to save gas
 189 |  canonicalToBridged[_ctoken.chainId][_ctoken.addr] = _btokenNew;

     |  // @audit-issue Use assembly `sstore` to save gas
 422 |  bridgedToCanonical[btoken] = ctoken;

     |  // @audit-issue Use assembly `sstore` to save gas
 423 |  canonicalToBridged[ctoken.chainId][ctoken.addr] = btoken;
```
GitHub: [181](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L181), [188](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L188), [189](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L189), [422](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L422), [423](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L423)


```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

     |  // @audit-issue Use assembly `sstore` to save gas
 247 |  bridgedToCanonical[btoken_] = _ctoken;

     |  // @audit-issue Use assembly `sstore` to save gas
 248 |  canonicalToBridged[_ctoken.chainId][_ctoken.addr] = btoken_;
```
GitHub: [247](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L247), [248](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L248)


```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

     |  // @audit-issue Use assembly `sstore` to save gas
 213 |  addressRegistered[_instances[i]] = true;

     |  // @audit-issue Use assembly `sstore` to save gas
 217 |  instances[nextInstanceId] = Instance(_instances[i], validSince);

     |  // @audit-issue Use assembly `sstore` to save gas
 229 |  instances[id] = Instance(newInstance, uint64(block.timestamp));
```
GitHub: [213](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L213), [217](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L217), [229](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L229)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

     |  // @audit-issue Use assembly `sstore` to save gas
  41 |  token = _token;

     |  // @audit-issue Use assembly `sstore` to save gas
  42 |  vault = _vault;
```
GitHub: [41](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L41), [42](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L42)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

     |  // @audit-issue Use assembly `sstore` to save gas
  69 |  token = _token;

     |  // @audit-issue Use assembly `sstore` to save gas
  70 |  vault = _vault;

     |  // @audit-issue Use assembly `sstore` to save gas
  71 |  withdrawalWindow = _withdrawalWindow;

     |  // @audit-issue Use assembly `sstore` to save gas
  83 |  claimedAmount[user] += amount;

     |  // @audit-issue Use assembly `sstore` to save gas
  90 |  withdrawnAmount[user] += amount;
```
GitHub: [69](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L69), [70](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L70), [71](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L71), [83](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L83), [90](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L90)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

     |  // @audit-issue Use assembly `sstore` to save gas
  39 |  token = _token;

     |  // @audit-issue Use assembly `sstore` to save gas
  40 |  vault = _vault;
```
GitHub: [39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L39), [40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L40)


```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

     |  // @audit-issue Use assembly `sstore` to save gas
  73 |  isClaimed[hash] = true;

     |  // @audit-issue Use assembly `sstore` to save gas
  91 |  claimStart = _claimStart;

     |  // @audit-issue Use assembly `sstore` to save gas
  92 |  claimEnd = _claimEnd;

     |  // @audit-issue Use assembly `sstore` to save gas
  93 |  merkleRoot = _merkleRoot;
```
GitHub: [73](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L73), [91](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L91), [92](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L92), [93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L93)


```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

     |  // @audit-issue Use assembly `sstore` to save gas
 122 |  taikoToken = _taikoToken;

     |  // @audit-issue Use assembly `sstore` to save gas
 125 |  costToken = _costToken;

     |  // @audit-issue Use assembly `sstore` to save gas
 128 |  sharedVault = _sharedVault;

     |  // @audit-issue Use assembly `sstore` to save gas
 141 |  totalAmountGranted += _grant.amount;

     |  // @audit-issue Use assembly `sstore` to save gas
 142 |  recipients[_recipient].grant = _grant;

     |  // @audit-issue Use assembly `sstore` to save gas
 156 |  totalAmountVoided += amountVoided;

     |  // @audit-issue Use assembly `sstore` to save gas
 216 |  totalAmountWithdrawn += amountToWithdraw;

     |  // @audit-issue Use assembly `sstore` to save gas
 217 |  totalCostPaid += costToWithdraw;
```
GitHub: [122](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L122), [125](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L125), [128](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L128), [141](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L141), [142](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L142), [156](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L156), [216](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L216), [217](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L217)


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

     |  // @audit-issue Use assembly `sstore` to save gas
  55 |  sigVerifyLib = ISigVerifyLib(sigVerifyLibAddr);

     |  // @audit-issue Use assembly `sstore` to save gas
  56 |  pemCertLib = PEMCertChainLib(pemCertLibAddr);

     |  // @audit-issue Use assembly `sstore` to save gas
  57 |  owner = msg.sender;

     |  // @audit-issue Use assembly `sstore` to save gas
  66 |  _trustedUserMrSigner[_mrSigner] = _trusted;

     |  // @audit-issue Use assembly `sstore` to save gas
  70 |  _trustedUserMrEnclave[_mrEnclave] = _trusted;

     |  // @audit-issue Use assembly `sstore` to save gas
  84 |  _serialNumIsRevoked[index][serialNumBatch[i]] = true;

     |  // @audit-issue Use assembly `sstore` to save gas
 111 |  tcbInfo[fmspc] = tcbInfoInput;

     |  // @audit-issue Use assembly `sstore` to save gas
 119 |  qeIdentity = qeIdentityInput;

     |  // @audit-issue Use assembly `sstore` to save gas
 123 |  _checkLocalEnclaveReport = !_checkLocalEnclaveReport;
```
GitHub: [55](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L55), [56](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L56), [57](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L57), [66](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L66), [70](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L70), [84](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L84), [111](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L111), [119](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L119), [123](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L123)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

     |  // @audit-issue Use assembly `sstore` to save gas
  21 |  ES256VERIFIER = es256Verifier;
```
GitHub: [21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L21)


## [G-64] Use custom errors rather than `revert()`/`require()` strings to save gas

Custom errors are available from solidity version 0.8.4. Custom errors save [**~50 gas**](https://gist.github.com/IllIllI000/ad1bd0d29a0101b25e57c293b4b0c746) each time they're hit by [avoiding having to allocate and store the revert string](https://blog.soliditylang.org/2021/04/21/custom-errors/#errors-in-depth). Not defining the strings also save deployment gas.

*Instances: 66*

```solidity
File: packages/protocol/contracts/thirdparty/optimism/Bytes.sol

     |  // @audit-issue Use custom errors
  25 |  require(_length + 31 >= _length, "slice_overflow");

     |  // @audit-issue Use custom errors
  26 |  require(_start + _length >= _start, "slice_overflow");

     |  // @audit-issue Use custom errors
  27 |  require(_bytes.length >= _start + _length, "slice_outOfBounds");
```
GitHub: [25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L25), [26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L26), [27](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L27)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

     |  // @audit-issue Use custom errors
  37 |  require(
  38 |      _in.length > 0,
  39 |      "RLPReader: length of an RLP item must be greater than zero to be decodable"
  40 |  );

     |  // @audit-issue Use custom errors
  56 |  require(
  57 |      itemType == RLPItemType.LIST_ITEM,
  58 |      "RLPReader: decoded item type for list is not a list item"
  59 |  );

     |  // @audit-issue Use custom errors
  61 |  require(
  62 |      listOffset + listLength == _in.length,
  63 |      "RLPReader: list item has an invalid data remainder"
  64 |  );

     |  // @audit-issue Use custom errors
 112 |  require(
 113 |      itemType == RLPItemType.DATA_ITEM,
 114 |      "RLPReader: decoded item type for bytes is not a data item"
 115 |  );

     |  // @audit-issue Use custom errors
 117 |  require(
 118 |      _in.length == itemOffset + itemLength,
 119 |      "RLPReader: bytes value contains an invalid remainder"
 120 |  );

     |  // @audit-issue Use custom errors
 152 |  require(
 153 |      _in.length > 0,
 154 |      "RLPReader: length of an RLP item must be greater than zero to be decodable"
 155 |  );

     |  // @audit-issue Use custom errors
 172 |  require(
 173 |      _in.length > strLen,
 174 |      "RLPReader: length of content must be greater than string length (short string)"
 175 |  );

     |  // @audit-issue Use custom errors
 182 |  require(
 183 |      strLen != 1 || firstByteOfContent >= 0x80,
 184 |      "RLPReader: invalid prefix, single byte < 0x80 are not prefixed (short string)"
 185 |  );

     |  // @audit-issue Use custom errors
 192 |  require(
 193 |      _in.length > lenOfStrLen,
 194 |      "RLPReader: length of content must be > than length of string length (long string)"
 195 |  );

     |  // @audit-issue Use custom errors
 202 |  require(
 203 |      firstByteOfContent != 0x00,
 204 |      "RLPReader: length of content must not have any leading zeros (long string)"
 205 |  );

     |  // @audit-issue Use custom errors
 212 |  require(
 213 |      strLen > 55,
 214 |      "RLPReader: length of content must be greater than 55 bytes (long string)"
 215 |  );

     |  // @audit-issue Use custom errors
 217 |  require(
 218 |      _in.length > lenOfStrLen + strLen,
 219 |      "RLPReader: length of content must be greater than total length (long string)"
 220 |  );

     |  // @audit-issue Use custom errors
 228 |  require(
 229 |      _in.length > listLen,
 230 |      "RLPReader: length of content must be greater than list length (short list)"
 231 |  );

     |  // @audit-issue Use custom errors
 238 |  require(
 239 |      _in.length > lenOfListLen,
 240 |      "RLPReader: length of content must be > than length of list length (long list)"
 241 |  );

     |  // @audit-issue Use custom errors
 248 |  require(
 249 |      firstByteOfContent != 0x00,
 250 |      "RLPReader: length of content must not have any leading zeros (long list)"
 251 |  );

     |  // @audit-issue Use custom errors
 258 |  require(
 259 |      listLen > 55,
 260 |      "RLPReader: length of content must be greater than 55 bytes (long list)"
 261 |  );

     |  // @audit-issue Use custom errors
 263 |  require(
 264 |      _in.length > lenOfListLen + listLen,
 265 |      "RLPReader: length of content must be greater than total length (long list)"
 266 |  );
```
GitHub: [37-40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L37-L40), [56-59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L56-L59), [61-64](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L61-L64), [112-115](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L112-L115), [117-120](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L117-L120), [152-155](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L152-L155), [172-175](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L172-L175), [182-185](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L182-L185), [192-195](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L192-L195), [202-205](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L202-L205), [212-215](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L212-L215), [217-220](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L217-L220), [228-231](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L228-L231), [238-241](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L238-L241), [248-251](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L248-L251), [258-261](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L258-L261), [263-266](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L263-L266)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

     |  // @audit-issue Use custom errors
  77 |  require(_key.length > 0, "MerkleTrie: empty key");

     |  // @audit-issue Use custom errors
  89 |  require(currentKeyIndex <= key.length, "MerkleTrie: key index exceeds total key length");

     |  // @audit-issue Use custom errors
  93 |  require(
  94 |      Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
  95 |      "MerkleTrie: invalid root hash"
  96 |  );

     |  // @audit-issue Use custom errors
  99 |  require(
 100 |      Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
 101 |      "MerkleTrie: invalid large internal hash"
 102 |  );

     |  // @audit-issue Use custom errors
 105 |  require(
 106 |      Bytes.equal(currentNode.encoded, currentNodeID),
 107 |      "MerkleTrie: invalid internal node hash"
 108 |  );

     |  // @audit-issue Use custom errors
 119 |  require(
 120 |      value_.length > 0,
 121 |      "MerkleTrie: value length must be greater than zero (branch)"
 122 |  );

     |  // @audit-issue Use custom errors
 125 |  require(
 126 |      i == proof.length - 1,
 127 |      "MerkleTrie: value node must be last node in proof (branch)"
 128 |  );

     |  // @audit-issue Use custom errors
 150 |  require(
 151 |      pathRemainder.length == sharedNibbleLength,
 152 |      "MerkleTrie: path remainder must share all nibbles with key"
 153 |  );

     |  // @audit-issue Use custom errors
 162 |  require(
 163 |      keyRemainder.length == sharedNibbleLength,
 164 |      "MerkleTrie: key remainder must be identical to path remainder"
 165 |  );

     |  // @audit-issue Use custom errors
 172 |  require(
 173 |      value_.length > 0,
 174 |      "MerkleTrie: value length must be greater than zero (leaf)"
 175 |  );

     |  // @audit-issue Use custom errors
 178 |  require(
 179 |      i == proof.length - 1,
 180 |      "MerkleTrie: value node must be last node in proof (leaf)"
 181 |  );

     |  // @audit-issue Use custom errors
 191 |  revert("MerkleTrie: received a node with an unknown prefix");

     |  // @audit-issue Use custom errors
 194 |  revert("MerkleTrie: received an unparseable node");

     |  // @audit-issue Use custom errors
 198 |  revert("MerkleTrie: ran out of proof elements");
```
GitHub: [77](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L77), [89](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L89), [93-96](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L93-L96), [99-102](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L99-L102), [105-108](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L105-L108), [119-122](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L119-L122), [125-128](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L125-L128), [150-153](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L150-L153), [162-165](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L162-L165), [172-175](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L172-L175), [178-181](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L178-L181), [191](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L191), [194](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L194), [198](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L198)


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

     |  // @audit-issue Use custom errors
  61 |  require(msg.sender == owner, "onlyOwner");
```
GitHub: [61](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L61)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

     |  // @audit-issue Use custom errors
  77 |  require(
  78 |      localEnclaveReport.reserved3.length == 96 && localEnclaveReport.reserved4.length == 60
  79 |          && localEnclaveReport.reportData.length == 64,
  80 |      "local QE report has wrong length"
  81 |  );

     |  // @audit-issue Use custom errors
  82 |  require(
  83 |      pckSignedQeReport.reserved3.length == 96 && pckSignedQeReport.reserved4.length == 60
  84 |          && pckSignedQeReport.reportData.length == 64,
  85 |      "QE report has wrong length"
  86 |  );

     |  // @audit-issue Use custom errors
  87 |  require(
  88 |      v3Quote.v3AuthData.certification.certType == 5,
  89 |      "certType must be 5: Concatenated PCK Cert Chain (PEM formatted)"
  90 |  );

     |  // @audit-issue Use custom errors
  91 |  require(
  92 |      v3Quote.v3AuthData.certification.decodedCertDataArray.length == 3, "3 certs in chain"
  93 |  );

     |  // @audit-issue Use custom errors
  94 |  require(
  95 |      v3Quote.v3AuthData.ecdsa256BitSignature.length == 64
  96 |          && v3Quote.v3AuthData.ecdsaAttestationKey.length == 64
  97 |          && v3Quote.v3AuthData.qeReportSignature.length == 64,
  98 |      "Invalid ECDSA signature format"
  99 |  );

     |  // @audit-issue Use custom errors
 100 |  require(
 101 |      v3Quote.v3AuthData.qeAuthData.parsedDataSize
 102 |          == v3Quote.v3AuthData.qeAuthData.data.length,
 103 |      "Invalid QEAuthData size"
 104 |  );

     |  // @audit-issue Use custom errors
 116 |  require(totalQuoteSize >= MINIMUM_QUOTE_LENGTH, "Invalid quote size");

     |  // @audit-issue Use custom errors
 279 |  require(certParsedSuccessfully, "splitCertificateChain failed");
```
GitHub: [77-81](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L77-L81), [82-86](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L82-L86), [87-90](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L87-L90), [91-93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L91-L93), [94-99](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L94-L99), [100-104](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L100-L104), [116](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L116), [279](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L279)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

     |  // @audit-issue Use custom errors
  57 |  require(der[ptr.ixs()] == 0x03, "Not type BIT STRING");

     |  // @audit-issue Use custom errors
  67 |  require(der[ptr.ixs()] == 0x04, "Not type OCTET STRING");

     |  // @audit-issue Use custom errors
  88 |  require(der[ptr.ixs()] & 0x20 == 0x20, "Not a constructed type");

     |  // @audit-issue Use custom errors
 142 |  require(der[ptr.ixs()] == 0x02, "Not type INTEGER");

     |  // @audit-issue Use custom errors
 143 |  require(der[ptr.ixf()] & 0x80 == 0, "Not positive");

     |  // @audit-issue Use custom errors
 155 |  require(der[ptr.ixs()] == 0x02, "Not type INTEGER");

     |  // @audit-issue Use custom errors
 156 |  require(der[ptr.ixf()] & 0x80 == 0, "Not positive");

     |  // @audit-issue Use custom errors
 180 |  require(der[ptr.ixs()] == 0x03, "ixs Not type BIT STRING 0x03");

     |  // @audit-issue Use custom errors
 182 |  require(der[ptr.ixf()] == 0x00, "ixf Not 0");
```
GitHub: [57](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L57), [67](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L67), [88](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L88), [142](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L142), [143](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L143), [155](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L155), [156](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L156), [180](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L180), [182](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L182)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

     |  // @audit-issue Use custom errors
  25 |  require(offset + len <= self.length, "invalid offset");

     |  // @audit-issue Use custom errors
 199 |  require(idx + 2 <= self.length, "invalid idx");

     |  // @audit-issue Use custom errors
 212 |  require(idx + 4 <= self.length, "unexpected idx");

     |  // @audit-issue Use custom errors
 225 |  require(idx + 32 <= self.length, "unexpected idx");

     |  // @audit-issue Use custom errors
 238 |  require(idx + 20 <= self.length, "unexpected idx");

     |  // @audit-issue Use custom errors
 264 |  require(len <= 32, "unexpected len");

     |  // @audit-issue Use custom errors
 265 |  require(idx + len <= self.length, "unexpected idx");

     |  // @audit-issue Use custom errors
 293 |  require(offset + len <= self.length, "unexpected offset");

     |  // @audit-issue Use custom errors
 329 |  require(len <= 52, "unexpected len");

     |  // @audit-issue Use custom errors
 335 |  require(char >= 0x30 && char <= 0x7A, "invalid char");

     |  // @audit-issue Use custom errors
 337 |  require(decoded <= 0x20, "invalid decoded");

     |  // @audit-issue Use custom errors
 365 |  revert("unexpected len");
```
GitHub: [25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L25), [199](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L199), [212](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L212), [225](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L225), [238](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L238), [264](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L264), [265](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L265), [293](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L293), [329](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L329), [335](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L335), [337](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L337), [365](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L365)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

     |  // @audit-issue Use custom errors
  50 |  revert("Unsupported algorithm");

     |  // @audit-issue Use custom errors
  75 |  revert("Unsupported algorithm");
```
GitHub: [50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L50), [75](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L75)


## [G-65] Use local variables for emitting

Using a state variable will incur a `Gwarmaccess`. It is unlikely that a variable would be emitted in an `event` unless used in the enclosing `function`/`modifier` scope. Therefore, use a local stack variable copy of the state variable when emitting the event. If the state variable hasn't been used, reconsider whether it makes sense to include it in the event.

*Instances: 7*

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

     |  // @audit-issue `version` is a state variable
  95 |  emit GuardiansUpdated(version, _newGuardians);
```
GitHub: [95](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L95)


```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

     |  // @audit-issue `nextTxId` is a state variable
  53 |  emit TransactionExecuted(nextTxId++, bytes4(txdata));
```
GitHub: [53](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L53)


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

     |  // @audit-issue `gasExcess` is a state variable
 157 |  emit Anchored(blockhash(parentId), gasExcess);
```
GitHub: [157](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L157)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

     |  // @audit-issue `migratingAddress` is a state variable
  63 |  emit MigratedTo(migratingAddress, _account, _amount);

     |  // @audit-issue `migratingAddress` is a state variable
  80 |  emit MigratedTo(migratingAddress, _account, _amount);
```
GitHub: [63](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L63), [80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L80)


```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

     |  // @audit-issue `instances` is a state variable
 109 |  emit InstanceDeleted(idx, instances[idx].addr);

     |  // @audit-issue `nextInstanceId` is a state variable
 220 |  emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);
```
GitHub: [109](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L109), [220](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220)


## [G-66] Use more recent OpenZeppelin version for gas boost

OpenZeppelin version 4.9.0+ provides many small gas optimizations, see [here](https://github.com/OpenZeppelin/openzeppelin-contracts/releases/tag/v4.9.0) for more info.

*Instances: 47*

```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

     |  // @audit-issue OpenZeppelin 4.8.1 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.8.1) (proxy/utils/Initializable.sol)"
   4 |  import "@openzeppelin/contracts-upgradeable/proxy/utils/Initializable.sol";
```
GitHub: [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L4)


```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

     |  // @audit-issue OpenZeppelin 4.8.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.8.0) (proxy/utils/UUPSUpgradeable.sol)"
   4 |  import "@openzeppelin/contracts/proxy/utils/UUPSUpgradeable.sol";

     |  // @audit-issue OpenZeppelin 4.8.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.8.0) (access/Ownable2Step.sol)"
   5 |  import "@openzeppelin/contracts-upgradeable/access/Ownable2StepUpgradeable.sol";
```
GitHub: [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L5)


```solidity
File: packages/protocol/contracts/libs/LibAddress.sol

     |  // @audit-issue OpenZeppelin 4.8.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.8.0) (utils/Address.sol)"
   4 |  import "@openzeppelin/contracts/utils/Address.sol";

     |  // @audit-issue OpenZeppelin 4.8.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.8.0) (utils/cryptography/ECDSA.sol)"
   5 |  import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol";
```
GitHub: [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L5)


```solidity
File: packages/protocol/contracts/L1/gov/TaikoGovernor.sol

     |  // @audit-issue OpenZeppelin 4.8.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.8.0) (governance/Governor.sol)"
   4 |  import "@openzeppelin/contracts-upgradeable/governance/GovernorUpgradeable.sol";

     |  // @audit-issue OpenZeppelin 4.8.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.8.0) (governance/compatibility/GovernorCompatibilityBravo.sol)"
   5 |  import
   6 |      "@openzeppelin/contracts-upgradeable/governance/compatibility/GovernorCompatibilityBravoUpgradeable.sol";

     |  // @audit-issue OpenZeppelin 4.6.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.6.0) (governance/extensions/GovernorVotes.sol)"
   7 |  import "@openzeppelin/contracts-upgradeable/governance/extensions/GovernorVotesUpgradeable.sol";

     |  // @audit-issue OpenZeppelin 4.8.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.8.0) (governance/extensions/GovernorVotesQuorumFraction.sol)"
   8 |  import
   9 |      "@openzeppelin/contracts-upgradeable/governance/extensions/GovernorVotesQuorumFractionUpgradeable.sol";

     |  // @audit-issue OpenZeppelin 4.6.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.6.0) (governance/extensions/GovernorTimelockControl.sol)"
  10 |  import
  11 |      "@openzeppelin/contracts-upgradeable/governance/extensions/GovernorTimelockControlUpgradeable.sol";
```
GitHub: [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L4), [5-6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L5-L6), [7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L7), [8-9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L8-L9), [10-11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L10-L11)


```solidity
File: packages/protocol/contracts/L1/gov/TaikoTimelockController.sol

     |  // @audit-issue OpenZeppelin 4.8.2 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.8.2) (governance/TimelockController.sol)"
   4 |  import "@openzeppelin/contracts-upgradeable/governance/TimelockControllerUpgradeable.sol";
```
GitHub: [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L4)


```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

     |  // @audit-issue OpenZeppelin 4.6.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.6.0) (token/ERC20/IERC20.sol)"
   4 |  import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

     |  // @audit-issue OpenZeppelin 4.8.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.8.0) (token/ERC20/utils/SafeERC20.sol)"
   5 |  import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```
GitHub: [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L5)


```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

     |  // @audit-issue OpenZeppelin 4.6.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.6.0) (token/ERC20/IERC20.sol)"
   4 |  import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```
GitHub: [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L4)


```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

     |  // @audit-issue OpenZeppelin 4.6.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.6.0) (token/ERC20/IERC20.sol)"
   4 |  import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```
GitHub: [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L4)


```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

     |  // @audit-issue OpenZeppelin 4.6.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.6.0) (token/ERC20/IERC20.sol)"
   4 |  import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```
GitHub: [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L4)


```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

     |  // @audit-issue OpenZeppelin 4.8.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.8.0) (token/ERC20/ERC20.sol)"
   4 |  import "@openzeppelin/contracts-upgradeable/token/ERC20/ERC20Upgradeable.sol";

     |  // @audit-issue OpenZeppelin 4.7.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.7.0) (token/ERC20/extensions/ERC20Snapshot.sol)"
   5 |  import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20SnapshotUpgradeable.sol";

     |  // @audit-issue OpenZeppelin 4.8.1 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.8.1) (token/ERC20/extensions/ERC20Votes.sol)"
   6 |  import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20VotesUpgradeable.sol";
```
GitHub: [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L6)


```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

     |  // @audit-issue OpenZeppelin 4.6.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.6.0) (token/ERC20/IERC20.sol)"
   4 |  import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```
GitHub: [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L4)


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

     |  // @audit-issue OpenZeppelin 4.6.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.6.0) (token/ERC20/IERC20.sol)"
   4 |  import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

     |  // @audit-issue OpenZeppelin 4.8.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.8.0) (token/ERC20/utils/SafeERC20.sol)"
   5 |  import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```
GitHub: [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L5)


```solidity
File: packages/protocol/contracts/signal/SignalService.sol

     |  // @audit-issue OpenZeppelin 4.8.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.8.0) (utils/math/SafeCast.sol)"
   4 |  import "@openzeppelin/contracts/utils/math/SafeCast.sol";
```
GitHub: [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L4)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

     |  // @audit-issue OpenZeppelin 4.8.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.8.0) (utils/Address.sol)"
   4 |  import "@openzeppelin/contracts/utils/Address.sol";
```
GitHub: [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L4)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

     |  // @audit-issue OpenZeppelin 4.8.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.8.0) (utils/Strings.sol)"
   5 |  import "@openzeppelin/contracts/utils/Strings.sol";

     |  // @audit-issue OpenZeppelin 4.7.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.7.0) (token/ERC20/extensions/ERC20Snapshot.sol)"
   6 |  import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20SnapshotUpgradeable.sol";

     |  // @audit-issue OpenZeppelin 4.8.1 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.8.1) (token/ERC20/extensions/ERC20Votes.sol)"
   7 |  import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20VotesUpgradeable.sol";
```
GitHub: [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L6), [7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L7)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

     |  // @audit-issue OpenZeppelin 4.8.2 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.8.2) (token/ERC721/ERC721.sol)"
   4 |  import "@openzeppelin/contracts-upgradeable/token/ERC721/ERC721Upgradeable.sol";

     |  // @audit-issue OpenZeppelin 4.8.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.8.0) (utils/Strings.sol)"
   5 |  import "@openzeppelin/contracts/utils/Strings.sol";
```
GitHub: [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L5)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

     |  // @audit-issue OpenZeppelin 4.8.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.8.0) (utils/Strings.sol)"
   4 |  import "@openzeppelin/contracts/utils/Strings.sol";

     |  // @audit-issue OpenZeppelin 4.8.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.8.0) (token/ERC1155/ERC1155.sol)"
   5 |  import "@openzeppelin/contracts-upgradeable/token/ERC1155/ERC1155Upgradeable.sol";
```
GitHub: [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L5)


```solidity
File: packages/protocol/contracts/tokenvault/BaseVault.sol

     |  // @audit-issue OpenZeppelin 4.7.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.7.0) (proxy/ERC1967/ERC1967Proxy.sol)"
   5 |  import "@openzeppelin/contracts/proxy/ERC1967/ERC1967Proxy.sol";
```
GitHub: [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L5)


```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

     |  // @audit-issue OpenZeppelin 4.7.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.7.0) (token/ERC1155/IERC1155.sol)"
   4 |  import "@openzeppelin/contracts/token/ERC1155/IERC1155.sol";
```
GitHub: [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L4)


```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

     |  // @audit-issue OpenZeppelin 4.6.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.6.0) (token/ERC20/IERC20.sol)"
   4 |  import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

     |  // @audit-issue OpenZeppelin 4.8.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.8.0) (token/ERC20/utils/SafeERC20.sol)"
   6 |  import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```
GitHub: [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L4), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L6)


```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

     |  // @audit-issue OpenZeppelin 4.8.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.8.0) (token/ERC721/IERC721.sol)"
   4 |  import "@openzeppelin/contracts/token/ERC721/IERC721.sol";

     |  // @audit-issue OpenZeppelin 4.6.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.6.0) (token/ERC721/IERC721Receiver.sol)"
   5 |  import "@openzeppelin/contracts/token/ERC721/IERC721Receiver.sol";
```
GitHub: [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L5)


```solidity
File: packages/protocol/contracts/tokenvault/LibBridgedToken.sol

     |  // @audit-issue OpenZeppelin 4.8.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.8.0) (utils/Strings.sol)"
   4 |  import "@openzeppelin/contracts/utils/Strings.sol";
```
GitHub: [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L4)


```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

     |  // @audit-issue OpenZeppelin 4.8.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.8.0) (utils/cryptography/ECDSA.sol)"
   4 |  import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol";
```
GitHub: [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L4)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

     |  // @audit-issue OpenZeppelin 4.6.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.6.0) (token/ERC20/IERC20.sol)"
   4 |  import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

     |  // @audit-issue OpenZeppelin 4.5.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.5.0) (governance/utils/IVotes.sol)"
   5 |  import "@openzeppelin/contracts/governance/utils/IVotes.sol";
```
GitHub: [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L5)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

     |  // @audit-issue OpenZeppelin 4.6.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.6.0) (token/ERC20/IERC20.sol)"
   4 |  import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```
GitHub: [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L4)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

     |  // @audit-issue OpenZeppelin 4.8.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.8.0) (token/ERC721/IERC721.sol)"
   4 |  import "@openzeppelin/contracts/token/ERC721/IERC721.sol";
```
GitHub: [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L4)


```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

     |  // @audit-issue OpenZeppelin 4.8.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.8.0) (utils/cryptography/MerkleProof.sol)"
   4 |  import "@openzeppelin/contracts/utils/cryptography/MerkleProof.sol";
```
GitHub: [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L4)


```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

     |  // @audit-issue OpenZeppelin 4.8.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.8.0) (utils/cryptography/ECDSA.sol)"
   4 |  import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol";

     |  // @audit-issue OpenZeppelin 4.6.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.6.0) (token/ERC20/IERC20.sol)"
   5 |  import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

     |  // @audit-issue OpenZeppelin 4.8.0 can be updated to 4.9.5
     |  // "// OpenZeppelin Contracts (last updated v4.8.0) (token/ERC20/utils/SafeERC20.sol)"
   6 |  import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```
GitHub: [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L6)


## [G-67] Use named `return` parameters

Using named return values instead of explicitly calling `return` saves ~13 execution gas per call and >1000 deployment gas per instance.

*Instances: 99*

```solidity
File: packages/protocol/contracts/common/IAddressManager.sol

     |  // @audit-issue Provide names for all return parameters
  14 |  function getAddress(uint64 _chainId, bytes32 _name) external view returns (address);
```
GitHub: [14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/IAddressManager.sol#L14)


```solidity
File: packages/protocol/contracts/common/AddressManager.sol

     |  // @audit-issue Provide names for all return parameters
  54 |  function getAddress(uint64 _chainId, bytes32 _name) public view override returns (address) {
```
GitHub: [54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L54)


```solidity
File: packages/protocol/contracts/common/IAddressResolver.sol

     |  // @audit-issue Provide names for all return parameters
  19 |  function resolve(
  20 |      bytes32 _name,
  21 |      bool _allowZeroAddress
  22 |  )
  23 |      external
  24 |      view
  25 |      returns (address payable);

     |  // @audit-issue Provide names for all return parameters
  34 |  function resolve(
  35 |      uint64 _chainId,
  36 |      bytes32 _name,
  37 |      bool _allowZeroAddress
  38 |  )
  39 |      external
  40 |      view
  41 |      returns (address payable);
```
GitHub: [19-25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/IAddressResolver.sol#L19-L25), [34-41](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/IAddressResolver.sol#L34-L41)


```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

     |  // @audit-issue Provide names for all return parameters
  30 |  function resolve(
  31 |      bytes32 _name,
  32 |      bool _allowZeroAddress
  33 |  )
  34 |      public
  35 |      view
  36 |      virtual
  37 |      returns (address payable)

     |  // @audit-issue Provide names for all return parameters
  43 |  function resolve(
  44 |      uint64 _chainId,
  45 |      bytes32 _name,
  46 |      bool _allowZeroAddress
  47 |  )
  48 |      public
  49 |      view
  50 |      virtual
  51 |      returns (address payable)
```
GitHub: [30-38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L30-L38), [43-52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L43-L52)


```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

     |  // @audit-issue Provide names for all return parameters
  88 |  function paused() public view returns (bool) {

     |  // @audit-issue Provide names for all return parameters
 140 |  function _inNonReentrant() internal view returns (bool) {
```
GitHub: [88](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L88), [140](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L140)


```solidity
File: packages/protocol/contracts/libs/LibAddress.sol

     |  // @audit-issue Provide names for all return parameters
  61 |  function isValidSignature(
  62 |      address _addr,
  63 |      bytes32 _hash,
  64 |      bytes memory _sig
  65 |  )
  66 |      internal
  67 |      view
  68 |      returns (bool)

     |  // @audit-issue Provide names for all return parameters
  77 |  function isSenderEOA() internal view returns (bool) {
```
GitHub: [61-69](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L61-L69), [77](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L77)


```solidity
File: packages/protocol/contracts/libs/LibMath.sol

     |  // @audit-issue Provide names for all return parameters
  12 |  function min(uint256 _a, uint256 _b) internal pure returns (uint256) {

     |  // @audit-issue Provide names for all return parameters
  20 |  function max(uint256 _a, uint256 _b) internal pure returns (uint256) {
```
GitHub: [12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibMath.sol#L12), [20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibMath.sol#L20)


```solidity
File: packages/protocol/contracts/L1/gov/TaikoGovernor.sol

     |  // @audit-issue Provide names for all return parameters
  48 |  function propose(
  49 |      address[] memory _targets,
  50 |      uint256[] memory _values,
  51 |      bytes[] memory _calldatas,
  52 |      string memory _description
  53 |  )
  54 |      public
  55 |      override(IGovernorUpgradeable, GovernorUpgradeable, GovernorCompatibilityBravoUpgradeable)
  56 |      returns (uint256)

     |  // @audit-issue Provide names for all return parameters
  69 |  function propose(
  70 |      address[] memory _targets,
  71 |      uint256[] memory _values,
  72 |      string[] memory _signatures,
  73 |      bytes[] memory _calldatas,
  74 |      string memory _description
  75 |  )
  76 |      public
  77 |      virtual
  78 |      override(GovernorCompatibilityBravoUpgradeable)
  79 |      returns (uint256)

     |  // @audit-issue Provide names for all return parameters
  89 |  function supportsInterface(bytes4 _interfaceId)
  90 |      public
  91 |      view
  92 |      override(GovernorUpgradeable, GovernorTimelockControlUpgradeable, IERC165Upgradeable)
  93 |      returns (bool)

     |  // @audit-issue Provide names for all return parameters
  99 |  function state(uint256 _proposalId)
 100 |      public
 101 |      view
 102 |      override(IGovernorUpgradeable, GovernorUpgradeable, GovernorTimelockControlUpgradeable)
 103 |      returns (ProposalState)

     |  // @audit-issue Provide names for all return parameters
 111 |  function votingDelay() public pure override returns (uint256) {

     |  // @audit-issue Provide names for all return parameters
 117 |  function votingPeriod() public pure override returns (uint256) {

     |  // @audit-issue Provide names for all return parameters
 123 |  function proposalThreshold() public pure override returns (uint256) {

     |  // @audit-issue Provide names for all return parameters
 140 |  function _cancel(
 141 |      address[] memory _targets,
 142 |      uint256[] memory _values,
 143 |      bytes[] memory _calldatas,
 144 |      bytes32 _descriptionHash
 145 |  )
 146 |      internal
 147 |      override(GovernorUpgradeable, GovernorTimelockControlUpgradeable)
 148 |      returns (uint256)

     |  // @audit-issue Provide names for all return parameters
 153 |  function _executor()
 154 |      internal
 155 |      view
 156 |      override(GovernorUpgradeable, GovernorTimelockControlUpgradeable)
 157 |      returns (address)
```
GitHub: [48-57](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L48-L57), [69-80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L69-L80), [89-94](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L89-L94), [99-104](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L99-L104), [111](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L111), [117](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L117), [123](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L123), [140-149](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L140-L149), [153-158](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L153-L158)


```solidity
File: packages/protocol/contracts/L1/gov/TaikoTimelockController.sol

     |  // @audit-issue Provide names for all return parameters
  24 |  function getMinDelay() public view override returns (uint256) {
```
GitHub: [24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L24)


```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

     |  // @audit-issue Provide names for all return parameters
 137 |  function hashAssignment(
 138 |      ProverAssignment memory _assignment,
 139 |      address _taikoL1Address,
 140 |      bytes32 _blobHash
 141 |  )
 142 |      public
 143 |      view
 144 |      returns (bytes32)

     |  // @audit-issue Provide names for all return parameters
 164 |  function _getProverFee(
 165 |      TaikoData.TierFee[] memory _tierFees,
 166 |      uint16 _tierId
 167 |  )
 168 |      private
 169 |      pure
 170 |      returns (uint256)
```
GitHub: [137-145](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L137-L145), [164-171](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L164-L171)


```solidity
File: packages/protocol/contracts/L1/ITaikoL1.sol

     |  // @audit-issue Provide names for all return parameters
  35 |  function getConfig() external view returns (TaikoData.Config memory);
```
GitHub: [35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/ITaikoL1.sol#L35)


```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

     |  // @audit-issue Provide names for all return parameters
 122 |  function canDepositEthToL2(
 123 |      TaikoData.State storage _state,
 124 |      TaikoData.Config memory _config,
 125 |      uint256 _amount
 126 |  )
 127 |      internal
 128 |      view
 129 |      returns (bool)

     |  // @audit-issue Provide names for all return parameters
 149 |  function _encodeEthDeposit(address _addr, uint256 _amount) private pure returns (uint256) {
```
GitHub: [122-130](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L122-L130), [149](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L149)


```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

     |  // @audit-issue Provide names for all return parameters
 287 |  function isBlobReusable(
 288 |      TaikoData.State storage _state,
 289 |      TaikoData.Config memory _config,
 290 |      bytes32 _blobHash
 291 |  )
 292 |      internal
 293 |      view
 294 |      returns (bool)

     |  // @audit-issue Provide names for all return parameters
 299 |  function _isProposerPermitted(
 300 |      TaikoData.SlotB memory _slotB,
 301 |      IAddressResolver _resolver
 302 |  )
 303 |      private
 304 |      view
 305 |      returns (bool)
```
GitHub: [287-295](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L287-L295), [299-306](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L299-L306)


```solidity
File: packages/protocol/contracts/L1/libs/LibUtils.sol

     |  // @audit-issue Provide names for all return parameters
  23 |  function getTransition(
  24 |      TaikoData.State storage _state,
  25 |      TaikoData.Config memory _config,
  26 |      uint64 _blockId,
  27 |      bytes32 _parentHash
  28 |  )
  29 |      external
  30 |      view
  31 |      returns (TaikoData.TransitionState storage)
```
GitHub: [23-32](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L23-L32)


```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

     |  // @audit-issue Provide names for all return parameters
 245 |  function _isConfigValid(TaikoData.Config memory _config) private view returns (bool) {
```
GitHub: [245](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L245)


```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

     |  // @audit-issue Provide names for all return parameters
 101 |  function isApproved(bytes32 _hash) public view returns (bool) {

     |  // @audit-issue Provide names for all return parameters
 107 |  function numGuardians() public view returns (uint256) {

     |  // @audit-issue Provide names for all return parameters
 128 |  function isApproved(uint256 _approvalBits) internal view returns (bool) {
```
GitHub: [101](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L101), [107](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L107), [128](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L128)


```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

     |  // @audit-issue Provide names for all return parameters
 132 |  function canDepositEthToL2(uint256 _amount) public view returns (bool) {

     |  // @audit-issue Provide names for all return parameters
 137 |  function isBlobReusable(bytes32 _blobHash) public view returns (bool) {

     |  // @audit-issue Provide names for all return parameters
 162 |  function getTransition(
 163 |      uint64 _blockId,
 164 |      bytes32 _parentHash
 165 |  )
 166 |      public
 167 |      view
 168 |      returns (TaikoData.TransitionState memory)

     |  // @audit-issue Provide names for all return parameters
 186 |  function getConfig() public view virtual override returns (TaikoData.Config memory) {
```
GitHub: [132](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L132), [137](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L137), [162-169](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L162-L169), [186](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L186)


```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

     |  // @audit-issue Provide names for all return parameters
  60 |  function transfer(address _to, uint256 _amount) public override returns (bool) {

     |  // @audit-issue Provide names for all return parameters
  70 |  function transferFrom(
  71 |      address _from,
  72 |      address _to,
  73 |      uint256 _amount
  74 |  )
  75 |      public
  76 |      override
  77 |      returns (bool)
```
GitHub: [60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L60), [70-78](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L70-L78)


```solidity
File: packages/protocol/contracts/L1/tiers/ITierProvider.sol

     |  // @audit-issue Provide names for all return parameters
  22 |  function getTier(uint16 tierId) external view returns (Tier memory);

     |  // @audit-issue Provide names for all return parameters
  28 |  function getTierIds() external view returns (uint16[] memory);

     |  // @audit-issue Provide names for all return parameters
  33 |  function getMinTier(uint256 rand) external view returns (uint16);
```
GitHub: [22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L22), [28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L28), [33](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L33)


```solidity
File: packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol

     |  // @audit-issue Provide names for all return parameters
  20 |  function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {

     |  // @audit-issue Provide names for all return parameters
  54 |  function getMinTier(uint256) public pure override returns (uint16) {
```
GitHub: [20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L20), [54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L54)


```solidity
File: packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol

     |  // @audit-issue Provide names for all return parameters
  20 |  function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {

     |  // @audit-issue Provide names for all return parameters
  66 |  function getMinTier(uint256 _rand) public pure override returns (uint16) {
```
GitHub: [20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L20), [66](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L66)


```solidity
File: packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol

     |  // @audit-issue Provide names for all return parameters
  20 |  function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {

     |  // @audit-issue Provide names for all return parameters
  66 |  function getMinTier(uint256 _rand) public pure override returns (uint16) {
```
GitHub: [20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L20), [66](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L66)


```solidity
File: packages/protocol/contracts/L2/Lib1559Math.sol

     |  // @audit-issue Provide names for all return parameters
  16 |  function basefee(
  17 |      uint256 _gasExcess,
  18 |      uint256 _adjustmentFactor
  19 |  )
  20 |      internal
  21 |      pure
  22 |      returns (uint256)

     |  // @audit-issue Provide names for all return parameters
  33 |  function _ethQty(
  34 |      uint256 _gasExcess,
  35 |      uint256 _adjustmentFactor
  36 |  )
  37 |      private
  38 |      pure
  39 |      returns (uint256)
```
GitHub: [16-23](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/Lib1559Math.sol#L16-L23), [33-40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/Lib1559Math.sol#L33-L40)


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

     |  // @audit-issue Provide names for all return parameters
 200 |  function getBlockHash(uint64 _blockId) public view returns (bytes32) {

     |  // @audit-issue Provide names for all return parameters
 219 |  function skipFeeCheck() public pure virtual returns (bool) {
```
GitHub: [200](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L200), [219](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L219)


```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

     |  // @audit-issue Provide names for all return parameters
  43 |  function getConfig() public view override returns (Config memory) {
```
GitHub: [43](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L43)


```solidity
File: packages/protocol/contracts/signal/ISignalService.sol

     |  // @audit-issue Provide names for all return parameters
  96 |  function isSignalSent(address _app, bytes32 _signal) external view returns (bool);

     |  // @audit-issue Provide names for all return parameters
 105 |  function isChainDataSynced(
 106 |      uint64 _chainId,
 107 |      bytes32 _kind,
 108 |      uint64 _blockId,
 109 |      bytes32 _chainData
 110 |  )
 111 |      external
 112 |      view
 113 |      returns (bool);
```
GitHub: [96](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/ISignalService.sol#L96), [105-113](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/ISignalService.sol#L105-L113)


```solidity
File: packages/protocol/contracts/signal/SignalService.sol

     |  // @audit-issue Provide names for all return parameters
  63 |  function sendSignal(bytes32 _signal) external returns (bytes32) {

     |  // @audit-issue Provide names for all return parameters
  68 |  function syncChainData(
  69 |      uint64 _chainId,
  70 |      bytes32 _kind,
  71 |      uint64 _blockId,
  72 |      bytes32 _chainData
  73 |  )
  74 |      external
  75 |      returns (bytes32)

     |  // @audit-issue Provide names for all return parameters
 137 |  function isChainDataSynced(
 138 |      uint64 _chainId,
 139 |      bytes32 _kind,
 140 |      uint64 _blockId,
 141 |      bytes32 _chainData
 142 |  )
 143 |      public
 144 |      view
 145 |      nonZeroValue(_chainData)
 146 |      returns (bool)

     |  // @audit-issue Provide names for all return parameters
 153 |  function isSignalSent(address _app, bytes32 _signal) public view returns (bool) {

     |  // @audit-issue Provide names for all return parameters
 177 |  function signalForChainData(
 178 |      uint64 _chainId,
 179 |      bytes32 _kind,
 180 |      uint64 _blockId
 181 |  )
 182 |      public
 183 |      pure
 184 |      returns (bytes32)

     |  // @audit-issue Provide names for all return parameters
 194 |  function getSignalSlot(
 195 |      uint64 _chainId,
 196 |      address _app,
 197 |      bytes32 _signal
 198 |  )
 199 |      public
 200 |      pure
 201 |      returns (bytes32)

     |  // @audit-issue Provide names for all return parameters
 206 |  function _verifyHopProof(
 207 |      uint64 _chainId,
 208 |      address _app,
 209 |      bytes32 _signal,
 210 |      bytes32 _value,
 211 |      HopProof memory _hop,
 212 |      address _signalService
 213 |  )
 214 |      internal
 215 |      virtual
 216 |      validSender(_app)
 217 |      nonZeroValue(_signal)
 218 |      nonZeroValue(_value)
 219 |      returns (bytes32)
```
GitHub: [63](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L63), [68-76](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L68-L76), [137-147](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L137-L147), [153](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L153), [177-185](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L177-L185), [194-202](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L194-L202), [206-220](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L206-L220)


```solidity
File: packages/protocol/contracts/bridge/IBridge.sol

     |  // @audit-issue Provide names for all return parameters
 150 |  function isMessageSent(Message calldata _message) external view returns (bool);

     |  // @audit-issue Provide names for all return parameters
 155 |  function hashMessage(Message memory _message) external pure returns (bytes32);
```
GitHub: [150](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/IBridge.sol#L150), [155](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/IBridge.sol#L155)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

     |  // @audit-issue Provide names for all return parameters
 340 |  function isMessageSent(Message calldata _message) public view returns (bool) {

     |  // @audit-issue Provide names for all return parameters
 352 |  function proveMessageFailed(
 353 |      Message calldata _message,
 354 |      bytes calldata _proof
 355 |  )
 356 |      public
 357 |      view
 358 |      returns (bool)

     |  // @audit-issue Provide names for all return parameters
 374 |  function proveMessageReceived(
 375 |      Message calldata _message,
 376 |      bytes calldata _proof
 377 |  )
 378 |      public
 379 |      view
 380 |      returns (bool)

     |  // @audit-issue Provide names for all return parameters
 449 |  function hashMessage(Message memory _message) public pure returns (bytes32) {

     |  // @audit-issue Provide names for all return parameters
 456 |  function signalForFailedMessage(bytes32 _msgHash) public pure returns (bytes32) {

     |  // @audit-issue Provide names for all return parameters
 555 |  function _loadContext() private view returns (Context memory) {
```
GitHub: [340](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L340), [352-359](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L352-L359), [374-381](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L374-L381), [449](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L449), [456](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L456), [555](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L555)


```solidity
File: packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

     |  // @audit-issue Provide names for all return parameters
  23 |  function transferFrom(address from, address _to, uint256 _amount) external returns (bool);
```
GitHub: [23](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L23)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

     |  // @audit-issue Provide names for all return parameters
  91 |  function name()
  92 |      public
  93 |      view
  94 |      override(ERC20Upgradeable, IERC20MetadataUpgradeable)
  95 |      returns (string memory)

     |  // @audit-issue Provide names for all return parameters
 102 |  function symbol()
 103 |      public
 104 |      view
 105 |      override(ERC20Upgradeable, IERC20MetadataUpgradeable)
 106 |      returns (string memory)

     |  // @audit-issue Provide names for all return parameters
 113 |  function decimals()
 114 |      public
 115 |      view
 116 |      override(ERC20Upgradeable, IERC20MetadataUpgradeable)
 117 |      returns (uint8)

     |  // @audit-issue Provide names for all return parameters
 125 |  function canonical() public view returns (address, uint256) {
```
GitHub: [91-96](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L91-L96), [102-107](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L102-L107), [113-118](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L113-L118), [125](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L125)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

     |  // @audit-issue Provide names for all return parameters
  93 |  function owner() public view override(IBridgedERC20, OwnableUpgradeable) returns (address) {

     |  // @audit-issue Provide names for all return parameters
 101 |  function _isMigratingOut() internal view returns (bool) {
```
GitHub: [93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L93), [101](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L101)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

     |  // @audit-issue Provide names for all return parameters
  87 |  function name() public view override(ERC721Upgradeable) returns (string memory) {

     |  // @audit-issue Provide names for all return parameters
  93 |  function symbol() public view override(ERC721Upgradeable) returns (string memory) {

     |  // @audit-issue Provide names for all return parameters
 100 |  function source() public view returns (address, uint256) {

     |  // @audit-issue Provide names for all return parameters
 107 |  function tokenURI(uint256 _tokenId) public view virtual override returns (string memory) {
```
GitHub: [87](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L87), [93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L93), [100](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L100), [107](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L107)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

     |  // @audit-issue Provide names for all return parameters
 115 |  function name() public view returns (string memory) {

     |  // @audit-issue Provide names for all return parameters
 121 |  function symbol() public view returns (string memory) {
```
GitHub: [115](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L115), [121](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L121)


```solidity
File: packages/protocol/contracts/tokenvault/BaseVault.sol

     |  // @audit-issue Provide names for all return parameters
  39 |  function supportsInterface(bytes4 _interfaceId) public view virtual override returns (bool) {

     |  // @audit-issue Provide names for all return parameters
  45 |  function name() public pure virtual returns (bytes32);
```
GitHub: [39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L39), [45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L45)


```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

     |  // @audit-issue Provide names for all return parameters
  18 |  function name() external view returns (string memory);

     |  // @audit-issue Provide names for all return parameters
  21 |  function symbol() external view returns (string memory);

     |  // @audit-issue Provide names for all return parameters
 160 |  function onERC1155BatchReceived(
 161 |      address,
 162 |      address,
 163 |      uint256[] calldata,
 164 |      uint256[] calldata,
 165 |      bytes calldata
 166 |  )
 167 |      external
 168 |      pure
 169 |      returns (bytes4)

     |  // @audit-issue Provide names for all return parameters
 175 |  function onERC1155Received(
 176 |      address,
 177 |      address,
 178 |      uint256,
 179 |      uint256,
 180 |      bytes calldata
 181 |  )
 182 |      external
 183 |      pure
 184 |      returns (bytes4)

     |  // @audit-issue Provide names for all return parameters
 192 |  function supportsInterface(bytes4 interfaceId)
 193 |      public
 194 |      view
 195 |      virtual
 196 |      override(BaseVault, ERC1155ReceiverUpgradeable)
 197 |      returns (bool)

     |  // @audit-issue Provide names for all return parameters
 204 |  function name() public pure override returns (bytes32) {
```
GitHub: [18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L18), [21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L21), [160-170](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L160-L170), [175-185](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L175-L185), [192-198](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L192-L198), [204](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L204)


```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

     |  // @audit-issue Provide names for all return parameters
 316 |  function name() public pure override returns (bytes32) {
```
GitHub: [316](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L316)


```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

     |  // @audit-issue Provide names for all return parameters
 142 |  function onERC721Received(
 143 |      address,
 144 |      address,
 145 |      uint256,
 146 |      bytes calldata
 147 |  )
 148 |      external
 149 |      pure
 150 |      returns (bytes4)

     |  // @audit-issue Provide names for all return parameters
 156 |  function name() public pure override returns (bytes32) {
```
GitHub: [142-151](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L142-L151), [156](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L156)


```solidity
File: packages/protocol/contracts/tokenvault/IBridgedERC20.sol

     |  // @audit-issue Provide names for all return parameters
  28 |  function owner() external view returns (address);
```
GitHub: [28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/IBridgedERC20.sol#L28)


```solidity
File: packages/protocol/contracts/tokenvault/LibBridgedToken.sol

     |  // @audit-issue Provide names for all return parameters
  28 |  function buildName(
  29 |      string memory _name,
  30 |      uint256 _srcChainId
  31 |  )
  32 |      internal
  33 |      pure
  34 |      returns (string memory)

     |  // @audit-issue Provide names for all return parameters
  39 |  function buildSymbol(string memory _symbol) internal pure returns (string memory) {

     |  // @audit-issue Provide names for all return parameters
  43 |  function buildURI(
  44 |      address _srcToken,
  45 |      uint256 _srcChainId
  46 |  )
  47 |      internal
  48 |      pure
  49 |      returns (string memory)
```
GitHub: [28-35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L28-L35), [39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L39), [43-50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L43-L50)


## [G-68] Use nested `if`s instead of `&&`

Optimization of condition checks in your smart contract is a crucial aspect in ensuring gas efficiency. Specifically, substituting multiple `&&` checks with nested `if` statements can lead to substantial gas savings.

When evaluating multiple conditions within a single `if` statement using the `&&` operator, each condition will consume gas even if a preceding condition fails. However, if these checks are broken down into nested `if` statements, execution halts as soon as a condition fails, saving the gas that would have been consumed by subsequent checks.

This practice is especially beneficial in scenarios where the `if` statement isn't followed by an `else` statement. The reason being, when an `else` statement is present, all conditions must be checked regardless to determine the correct branch of execution.

By reworking your code to utilize nested `if` statements, you can optimize gas usage, reduce execution cost, and enhance your contract's performance.

*Instances: 16*

```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

     |  // @audit-issue Save gas by using nested `if`
  85 |  if (!_allowZeroAddress && addr_ == address(0)) {
```
GitHub: [85](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L85)


```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

     |  // @audit-issue Save gas by using nested `if`
  42 |  if (msg.sender != owner() && msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();
```
GitHub: [42](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L42)


```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

     |  // @audit-issue Save gas by using nested `if`
 120 |  if (input.tip != 0 && block.coinbase != address(0)) {
```
GitHub: [120](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L120)


```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

     |  // @audit-issue Save gas by using nested `if`
 108 |  if (params.parentMetaHash != 0 && parentMetaHash != params.parentMetaHash) {

     |  // @audit-issue Save gas by using nested `if`
 164 |  if (_config.blobReuseEnabled && params.cacheBlobForReuse) {

     |  // @audit-issue Save gas by using nested `if`
 310 |  if (proposerOne != address(0) && msg.sender != proposerOne) {
```
GitHub: [108](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L108), [164](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L164), [310](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L310)


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

     |  // @audit-issue Save gas by using nested `if`
 141 |  if (!skipFeeCheck() && block.basefee != basefee) {

     |  // @audit-issue Save gas by using nested `if`
 275 |  if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {
```
GitHub: [141](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L141), [275](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L275)


```solidity
File: packages/protocol/contracts/signal/SignalService.sol

     |  // @audit-issue Save gas by using nested `if`
 285 |  if (cacheStateRoot && _isFullProof && !_isLastHop) {

     |  // @audit-issue Save gas by using nested `if`
 293 |  if (cacheSignalRoot && (_isFullProof || !_isLastHop)) {
```
GitHub: [285](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L285), [293](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L293)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

     |  // @audit-issue Save gas by using nested `if`
 250 |  if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) {

     |  // @audit-issue Save gas by using nested `if`
 260 |  if (_message.gasLimit == 0 && msg.sender != _message.destOwner) {
```
GitHub: [250](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L250), [260](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L260)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

     |  // @audit-issue Save gas by using nested `if`
  38 |  if (msg.sender != owner() && msg.sender != snapshooter) {
```
GitHub: [38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L38)


```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

     |  // @audit-issue Save gas by using nested `if`
  45 |  if (_migratingAddress == migratingAddress && _migratingInbound == migratingInbound) {
```
GitHub: [45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L45)


```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

     |  // @audit-issue Save gas by using nested `if`
 277 |  if (_cliff > 0 && _cliff <= _start) revert INVALID_GRANT();
```
GitHub: [277](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L277)


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

     |  // @audit-issue Save gas by using nested `if`
 220 |  if (pceSvnIsHigherOrGreater && cpuSvnsAreHigherOrGreater) {
```
GitHub: [220](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L220)


## [G-69] Use of low-level `call()` can be optimized with assembly

Low-level calls, when optimized with assembly, can save gas by avoiding unnecessary operations related to unused returndata. In a typical `.call`, Solidity automatically allocates memory and handles returndata even if it's not used, incurring extra gas costs. By using assembly, a developer can precisely control the execution, selectively ignoring or handling returndata, thereby optimizing gas usage. This specific control over the EVM allows for more efficient execution of calls by eliminating unnecessary memory operations, providing a more gas-efficient method when unused returndata is a concern. However, such optimization should be handled with care, as improper use of assembly might lead to vulnerabilities.

*Instances: 1*

```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

     |  // @audit-issue Consider using call in assembly for gas savings
  50 |  (bool success,) = address(this).call(txdata);
```
GitHub: [50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L50)


## [G-70] Using `storage` instead of `memory` for structs/arrays saves gas

When fetching data from a storage location, assigning the data to a `memory` variable causes all fields of the struct/array to be read from storage, which incurs a Gcoldsload (**2100 gas**) for *each* field of the struct/array. If the fields are read from the new memory variable, they incur an additional `MLOAD` rather than a cheap stack read. Instead of declearing the variable with the `memory` keyword, declaring the variable with the `storage` keyword and caching any fields that need to be re-read in stack variables, will be much cheaper, only incuring the Gcoldsload for the fields actually read. The only time it makes sense to read the whole struct/array into a `memory` variable, is if the full struct/array is being returned by the function, is being passed to a function that requires `memory`, or if the array/struct is being read from another `memory` array/struct.

*Instances: 22*

```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

  67 |  (meta_, deposits_) = LibProposing.proposeBlock(state, config, this, _params, _txList);

 151 |  (blk_, slot) = LibUtils.getBlock(state, getConfig(), _blockId);

 154 |  ts_ = state.transitions[slot][blk_.verifiedTransitionId];

 181 |  a_ = state.slotA;

 182 |  b_ = state.slotB;
```
GitHub: [67](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L67), [151](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L151), [154](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L154), [181](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L181), [182](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L182)


```solidity
File: packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol

  49 |  tiers_[0] = LibTiers.TIER_OPTIMISTIC;

  50 |  tiers_[1] = LibTiers.TIER_GUARDIAN;
```
GitHub: [49](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L49), [50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L50)


```solidity
File: packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol

  60 |  tiers_[0] = LibTiers.TIER_SGX;

  61 |  tiers_[1] = LibTiers.TIER_SGX_ZKVM;

  62 |  tiers_[2] = LibTiers.TIER_GUARDIAN;
```
GitHub: [60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L60), [61](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L61), [62](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L62)


```solidity
File: packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol

  60 |  tiers_[0] = LibTiers.TIER_OPTIMISTIC;

  61 |  tiers_[1] = LibTiers.TIER_SGX;

  62 |  tiers_[2] = LibTiers.TIER_GUARDIAN;
```
GitHub: [60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L60), [61](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L61), [62](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L62)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 144 |  message_.id = nextMessageId++;
```
GitHub: [144](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L144)


```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

 250 |  ctoken_ = bridgedToCanonical[_op.token];
```
GitHub: [250](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L250)


```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

 359 |  ctoken_ = bridgedToCanonical[_token];
```
GitHub: [359](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L359)


```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

 196 |  ctoken_ = bridgedToCanonical[_op.token];
```
GitHub: [196](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L196)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

  70 |  out_ = new RLPItem[](MAX_LIST_LENGTH);
```
GitHub: [70](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L70)


```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

 218 |  ids[i] = nextInstanceId;
```
GitHub: [218](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L218)


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

 424 |  (certDecodedSuccessfully, parsedQuoteCerts[i]) = pemCertLib.decodeCert(
 425 |      authDataV3.certification.decodedCertDataArray[i], isPckCert
 426 |  );

 436 |  fetchedTcbInfo = tcbInfo[parsedFmspc];
```
GitHub: [424-426](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L424-L426), [436](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L436)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

 353 |  cpusvns = new uint256[](SGX_TCB_CPUSVN_SIZE);
```
GitHub: [353](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L353)


## [G-71] Using assembly's `selfbalance()` is cheaper than `address(this).balance`

Saves 159 gas per instance:
```solidity
    assembly {
        mstore(0x00, selfbalance())
        return(0x00, 0x20)
    }
```

*Instances: 7*

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

     |  // @audit-issue Use assembly selfbalance()
 125 |  if (address(this).balance > 0) {

     |  // @audit-issue Use assembly selfbalance()
 126 |  taikoL1Address.sendEther(address(this).balance);
```
GitHub: [125](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L125), [126](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L126)


```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

     |  // @audit-issue Use assembly selfbalance()
 241 |  // Note that address(this).balance has been updated with msg.value,

     |  // @audit-issue Use assembly selfbalance()
 253 |  IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }(

     |  // @audit-issue Use assembly selfbalance()
 260 |  if (address(this).balance != 0) {

     |  // @audit-issue Use assembly selfbalance()
 261 |  msg.sender.sendEther(address(this).balance);
```
GitHub: [241](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L241), [253](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L253), [260](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L260), [261](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L261)


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

     |  // @audit-issue Use assembly selfbalance()
 174 |  _to.sendEther(address(this).balance);
```
GitHub: [174](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L174)


## [G-72] `++i` costs less gas than `i++`, especially when it's used in `for`-loops (`--i`/`i--` too)

Try pre-increment (`++i`) or pre-decrement (`--i`).

*Instances: 12*

```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

     |  // @audit-issue Switch to the pre-increment/decrement form
  62 |  _state.slotA.numEthDeposits++;

     |  // @audit-issue Switch to the pre-increment/decrement form
 116 |  _state.slotA.numEthDeposits++;
```
GitHub: [62](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L62), [116](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L116)


```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

     |  // @audit-issue Switch to the pre-increment/decrement form
 293 |  tid_ = _blk.nextTransitionId++;
```
GitHub: [293](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L293)


```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

     |  // @audit-issue Switch to the pre-increment/decrement form
  53 |  emit TransactionExecuted(nextTxId++, bytes4(txdata));
```
GitHub: [53](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L53)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

     |  // @audit-issue Switch to the pre-increment/decrement form
 144 |  message_.id = nextMessageId++;
```
GitHub: [144](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L144)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

     |  // @audit-issue Switch to the pre-increment/decrement form
  40 |  lenLen++;

     |  // @audit-issue Switch to the pre-increment/decrement form
  46 |  for (i = 1; i <= lenLen; i++) {

     |  // @audit-issue Switch to the pre-increment/decrement form
  59 |  for (; i < 32; i++) {

     |  // @audit-issue Switch to the pre-increment/decrement form
  66 |  for (uint256 j = 0; j < out_.length; j++) {

     |  // @audit-issue Switch to the pre-increment/decrement form
  67 |  out_[j] = b[i++];
```
GitHub: [40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L40), [46](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L46), [59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L59), [66](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66), [67](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L67)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

     |  // @audit-issue Switch to the pre-increment/decrement form
  85 |  for (uint256 i = 0; i < proof.length; i++) {
```
GitHub: [85](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85)


```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

     |  // @audit-issue Switch to the pre-increment/decrement form
 222 |  nextInstanceId++;
```
GitHub: [222](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L222)


## [G-73] `++i`/`i++` should be `unchecked{++i}`/`unchecked{i++}` when it is not possible for them to overflow, as is the case when used in `for`- and `while`-loops

The `unchecked` keyword is new in solidity version 0.8.0, so this only applies to that version or higher, which these instances are. This saves **30-40 gas [per loop](https://gist.github.com/hrkrshnn/ee8fabd532058307229d65dcd5836ddc#the-increment-in-for-loop-post-condition-can-be-made-unchecked)**

*Instances: 45*

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
 172 |  for (uint256 i; i < _tierFees.length; ++i) {
```
GitHub: [172](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L172)


```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
 244 |  for (uint256 i; i < params.hookCalls.length; ++i) {
```
GitHub: [244](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L244)


```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
  74 |  for (uint256 i; i < guardians.length; ++i) {

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
  80 |  for (uint256 i = 0; i < _newGuardians.length; ++i) {

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
 133 |  for (uint256 i; i < guardiansLength; ++i) {
```
GitHub: [74](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L74), [80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L80), [133](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L133)


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
 234 |  for (uint256 i; i < 255 && _blockId >= i + 1; ++i) {
```
GitHub: [234](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L234)


```solidity
File: packages/protocol/contracts/signal/SignalService.sol

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
 104 |  for (uint256 i; i < hopProofs.length; ++i) {
```
GitHub: [104](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L104)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
  90 |  for (uint256 i; i < _msgHashes.length; ++i) {
```
GitHub: [90](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L90)


```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
  47 |  for (uint256 i; i < _op.amounts.length; ++i) {

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
 251 |  for (uint256 i; i < _op.tokenIds.length; ++i) {

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
 269 |  for (uint256 i; i < _op.tokenIds.length; ++i) {
```
GitHub: [47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L47), [251](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L251), [269](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L269)


```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
  34 |  for (uint256 i; i < _op.tokenIds.length; ++i) {

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
 170 |  for (uint256 i; i < _tokenIds.length; ++i) {

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
 175 |  for (uint256 i; i < _tokenIds.length; ++i) {

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
 197 |  for (uint256 i; i < _op.tokenIds.length; ++i) {

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
 210 |  for (uint256 i; i < _op.tokenIds.length; ++i) {
```
GitHub: [34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L34), [170](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L170), [175](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L175), [197](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L197), [210](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L210)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
  46 |  for (i = 1; i <= lenLen; i++) {

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
  59 |  for (; i < 32; i++) {

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
  66 |  for (uint256 j = 0; j < out_.length; j++) {
```
GitHub: [46](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L46), [59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L59), [66](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
  85 |  for (uint256 i = 0; i < proof.length; i++) {
```
GitHub: [85](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85)


```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
 104 |  for (uint256 i; i < _ids.length; ++i) {

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
 210 |  for (uint256 i; i < _instances.length; ++i) {
```
GitHub: [104](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L104), [210](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
  59 |  for (uint256 i; i < tokenIds.length; ++i) {
```
GitHub: [59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59)


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
  80 |  for (uint256 i; i < serialNumBatch.length; ++i) {

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
  95 |  for (uint256 i; i < serialNumBatch.length; ++i) {

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
 191 |  for (uint256 i; i < enclaveId.tcbLevels.length; ++i) {

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
 214 |  for (uint256 i; i < tcb.tcbLevels.length; ++i) {

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
 240 |  for (uint256 i; i < CPUSVN_LENGTH; ++i) {

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
 259 |  for (uint256 i; i < n; ++i) {

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
 420 |  for (uint256 i; i < 3; ++i) {
```
GitHub: [80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L80), [95](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L95), [191](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L191), [214](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L214), [240](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L240), [259](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L259), [420](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L420)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
  54 |  for (uint256 i; i < size; ++i) {

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
 244 |  for (uint256 i; i < split.length; ++i) {

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
 354 |  for (uint256 i; i < SGX_TCB_CPUSVN_SIZE + 1; ++i) {
```
GitHub: [54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L54), [244](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L244), [354](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L354)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
 153 |  for (uint256 i; i < encoded.length; ++i) {

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
 281 |  for (uint256 i; i < 3; ++i) {
```
GitHub: [153](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L153), [281](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L281)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
 333 |  for (uint256 i; i < len; ++i) {
```
GitHub: [333](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L333)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
 140 |  for (uint256 i = 2; i < 2 + paddingLen; ++i) {

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
 152 |  for (uint256 i; i < digestAlgoWithParamLen; ++i) {

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
 158 |  for (uint256 i; i < digestAlgoWithParamLen; ++i) {

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
 174 |  for (uint256 i; i < _sha256.length; ++i) {

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
 273 |  for (uint256 i = 2; i < 2 + paddingLen; ++i) {

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
 283 |  for (uint256 i; i < sha1Prefix.length; ++i) {

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
 290 |  for (uint256 i; i < _sha1.length; ++i) {
```
GitHub: [140](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L140), [152](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L152), [158](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L158), [174](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L174), [273](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L273), [283](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L283), [290](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L290)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
  48 |  for (uint16 i = 1970; i < year; ++i) {

     |  // @audit-issue Consider incrementing loop variable in an `unchecked` block
  59 |  for (uint8 i = 1; i < month; ++i) {
```
GitHub: [48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L48), [59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L59)


## [G-74] `<x> += <y>` costs more gas than `<x> = <x> + <y>` for state variables

Using the addition operator instead of plus-equals saves **[113 gas](https://gist.github.com/IllIllI000/cbbfb267425b898e5be734d4008d4fe8)**

*Instances: 6*

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

     |  // @audit-issue Switch to <x> + <y> and <x> - <y>
  83 |  claimedAmount[user] += amount;

     |  // @audit-issue Switch to <x> + <y> and <x> - <y>
  90 |  withdrawnAmount[user] += amount;
```
GitHub: [83](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L83), [90](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L90)


```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

     |  // @audit-issue Switch to <x> + <y> and <x> - <y>
 141 |  totalAmountGranted += _grant.amount;

     |  // @audit-issue Switch to <x> + <y> and <x> - <y>
 156 |  totalAmountVoided += amountVoided;

     |  // @audit-issue Switch to <x> + <y> and <x> - <y>
 216 |  totalAmountWithdrawn += amountToWithdraw;

     |  // @audit-issue Switch to <x> + <y> and <x> - <y>
 217 |  totalCostPaid += costToWithdraw;
```
GitHub: [141](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L141), [156](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L156), [216](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L216), [217](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L217)


## [G-75] `abi.encode()` is less efficient than `abi.encodepacked()` for non-address arguments

See for more information: https://github.com/ConnorBlockchain/Solidity-Encode-Gas-Comparison

*Instances: 18*

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

     |  // @audit-issue Consider `abi.encodePacked()`
 147 |  abi.encode(
 148 |      "PROVER_ASSIGNMENT",
 149 |      ITaikoL1(_taikoL1Address).getConfig().chainId,
 150 |      _taikoL1Address,
 151 |      address(this),
 152 |      _assignment.metaHash,
 153 |      _assignment.parentMetaHash,
 154 |      _blobHash,
 155 |      _assignment.feeToken,
 156 |      _assignment.expiry,
 157 |      _assignment.maxBlockId,
 158 |      _assignment.maxProposedIn,
 159 |      _assignment.tierFees
 160 |  )
```
GitHub: [147-160](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L147-L160)


```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

     |  // @audit-issue Consider `abi.encodePacked()`
 126 |  depositsHash: keccak256(abi.encode(deposits_)),

     |  // @audit-issue Consider `abi.encodePacked()`
 213 |  metaHash: keccak256(abi.encode(meta_)),
```
GitHub: [126](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L126), [213](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L213)


```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

     |  // @audit-issue Consider `abi.encodePacked()`
 121 |  if (blk.blockId != _meta.id || blk.metaHash != keccak256(abi.encode(_meta))) {
```
GitHub: [121](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L121)


```solidity
File: packages/protocol/contracts/L1/provers/GuardianProver.sol

     |  // @audit-issue Consider `abi.encodePacked()`
  46 |  bytes32 hash = keccak256(abi.encode(_meta, _tran));

     |  // @audit-issue Consider `abi.encodePacked()`
  51 |  ITaikoL1(resolve("taiko", false)).proveBlock(_meta.id, abi.encode(_meta, _tran, _proof));
```
GitHub: [46](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/GuardianProver.sol#L46), [51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/GuardianProver.sol#L51)


```solidity
File: packages/protocol/contracts/signal/SignalService.sol

     |  // @audit-issue Consider `abi.encodePacked()`
 186 |  return keccak256(abi.encode(_chainId, _kind, _blockId));
```
GitHub: [186](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L186)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

     |  // @audit-issue Consider `abi.encodePacked()`
 450 |  return keccak256(abi.encode("TAIKO_MESSAGE", _message));
```
GitHub: [450](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L450)


```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

     |  // @audit-issue Consider `abi.encodePacked()`
 281 |  this.onMessageInvocation, abi.encode(ctoken_, _user, _op.to, _op.tokenIds, _op.amounts)
```
GitHub: [281](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L281)


```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

     |  // @audit-issue Consider `abi.encodePacked()`
 384 |  this.onMessageInvocation, abi.encode(ctoken_, _user, _to, balanceChange_)
```
GitHub: [384](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L384)


```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

     |  // @audit-issue Consider `abi.encodePacked()`
 217 |  this.onMessageInvocation, abi.encode(ctoken_, _user, _op.to, _op.tokenIds)
```
GitHub: [217](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L217)


```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

     |  // @audit-issue Consider `abi.encodePacked()`
 183 |  abi.encode(
 184 |      "VERIFY_PROOF",
 185 |      ITaikoL1(taikoL1).getConfig().chainId,
 186 |      address(this),
 187 |      _tran,
 188 |      _newInstance,
 189 |      _prover,
 190 |      _metaHash
 191 |  )
```
GitHub: [183-191](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L183-L191)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

     |  // @audit-issue Consider `abi.encodePacked()`
  60 |  _verifyClaim(abi.encode(user, amount), proof);
```
GitHub: [60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L60)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

     |  // @audit-issue Consider `abi.encodePacked()`
  80 |  _verifyClaim(abi.encode(user, amount), proof);
```
GitHub: [80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L80)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

     |  // @audit-issue Consider `abi.encodePacked()`
  56 |  _verifyClaim(abi.encode(user, tokenIds), proof);
```
GitHub: [56](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L56)


```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

     |  // @audit-issue Consider `abi.encodePacked()`
  68 |  bytes32 hash = keccak256(abi.encode("CLAIM_TAIKO_AIRDROP", data));
```
GitHub: [68](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L68)


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

     |  // @audit-issue Consider `abi.encodePacked()`
 482 |  retData = abi.encodePacked(sha256(abi.encode(v3quote)), tcbStatus);
```
GitHub: [482](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L482)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

     |  // @audit-issue Consider `abi.encodePacked()`
 136 |  bytes memory args = abi.encode(sha256(tbs), r, s, gx, gy);
```
GitHub: [136](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L136)


## [G-76] `do`-`while` is cheaper than `for`-loops when the initial check can be skipped

A `do while` loop will cost less gas if the condition does not need to be checked in the first iteration:

```solidity
for (uint256 i; i < len; ++i) { ... } // when 'len' is known to be > 0
```
  
could be written as:

```solidity
do { ...; ++i } while (i < len);
```


*Instances: 49*

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

     |  // @audit-issue Save gas by switching to a do-while loop
 172 |  for (uint256 i; i < _tierFees.length; ++i) {
```
GitHub: [172](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L172)


```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

     |  // @audit-issue Save gas by switching to a do-while loop
  86 |  for (uint256 i; i < deposits_.length;) {
```
GitHub: [86](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L86)


```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

     |  // @audit-issue Save gas by switching to a do-while loop
 244 |  for (uint256 i; i < params.hookCalls.length; ++i) {
```
GitHub: [244](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L244)


```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

     |  // @audit-issue Save gas by switching to a do-while loop
  74 |  for (uint256 i; i < guardians.length; ++i) {

     |  // @audit-issue Save gas by switching to a do-while loop
  80 |  for (uint256 i = 0; i < _newGuardians.length; ++i) {

     |  // @audit-issue Save gas by switching to a do-while loop
 133 |  for (uint256 i; i < guardiansLength; ++i) {
```
GitHub: [74](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L74), [80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L80), [133](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L133)


```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

     |  // @audit-issue Save gas by switching to a do-while loop
 234 |  for (uint256 i; i < 255 && _blockId >= i + 1; ++i) {
```
GitHub: [234](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L234)


```solidity
File: packages/protocol/contracts/signal/SignalService.sol

     |  // @audit-issue Save gas by switching to a do-while loop
 104 |  for (uint256 i; i < hopProofs.length; ++i) {
```
GitHub: [104](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L104)


```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

     |  // @audit-issue Save gas by switching to a do-while loop
  90 |  for (uint256 i; i < _msgHashes.length; ++i) {
```
GitHub: [90](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L90)


```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

     |  // @audit-issue Save gas by switching to a do-while loop
  47 |  for (uint256 i; i < _op.amounts.length; ++i) {

     |  // @audit-issue Save gas by switching to a do-while loop
 251 |  for (uint256 i; i < _op.tokenIds.length; ++i) {

     |  // @audit-issue Save gas by switching to a do-while loop
 269 |  for (uint256 i; i < _op.tokenIds.length; ++i) {
```
GitHub: [47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L47), [251](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L251), [269](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L269)


```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

     |  // @audit-issue Save gas by switching to a do-while loop
  34 |  for (uint256 i; i < _op.tokenIds.length; ++i) {

     |  // @audit-issue Save gas by switching to a do-while loop
 170 |  for (uint256 i; i < _tokenIds.length; ++i) {

     |  // @audit-issue Save gas by switching to a do-while loop
 175 |  for (uint256 i; i < _tokenIds.length; ++i) {

     |  // @audit-issue Save gas by switching to a do-while loop
 197 |  for (uint256 i; i < _op.tokenIds.length; ++i) {

     |  // @audit-issue Save gas by switching to a do-while loop
 210 |  for (uint256 i; i < _op.tokenIds.length; ++i) {
```
GitHub: [34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L34), [170](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L170), [175](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L175), [197](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L197), [210](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L210)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

     |  // @audit-issue Save gas by switching to a do-while loop
  46 |  for (i = 1; i <= lenLen; i++) {

     |  // @audit-issue Save gas by switching to a do-while loop
  59 |  for (; i < 32; i++) {

     |  // @audit-issue Save gas by switching to a do-while loop
  66 |  for (uint256 j = 0; j < out_.length; j++) {
```
GitHub: [46](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L46), [59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L59), [66](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66)


```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

     |  // @audit-issue Save gas by switching to a do-while loop
  85 |  for (uint256 i = 0; i < proof.length; i++) {

     |  // @audit-issue Save gas by switching to a do-while loop
 208 |  for (uint256 i = 0; i < length;) {

     |  // @audit-issue Save gas by switching to a do-while loop
 244 |  for (; shared_ < max && _a[shared_] == _b[shared_];) {
```
GitHub: [85](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85), [208](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L208), [244](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L244)


```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

     |  // @audit-issue Save gas by switching to a do-while loop
 104 |  for (uint256 i; i < _ids.length; ++i) {

     |  // @audit-issue Save gas by switching to a do-while loop
 210 |  for (uint256 i; i < _instances.length; ++i) {
```
GitHub: [104](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L104), [210](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210)


```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

     |  // @audit-issue Save gas by switching to a do-while loop
  59 |  for (uint256 i; i < tokenIds.length; ++i) {
```
GitHub: [59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59)


```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

     |  // @audit-issue Save gas by switching to a do-while loop
  80 |  for (uint256 i; i < serialNumBatch.length; ++i) {

     |  // @audit-issue Save gas by switching to a do-while loop
  95 |  for (uint256 i; i < serialNumBatch.length; ++i) {

     |  // @audit-issue Save gas by switching to a do-while loop
 191 |  for (uint256 i; i < enclaveId.tcbLevels.length; ++i) {

     |  // @audit-issue Save gas by switching to a do-while loop
 214 |  for (uint256 i; i < tcb.tcbLevels.length; ++i) {

     |  // @audit-issue Save gas by switching to a do-while loop
 240 |  for (uint256 i; i < CPUSVN_LENGTH; ++i) {

     |  // @audit-issue Save gas by switching to a do-while loop
 259 |  for (uint256 i; i < n; ++i) {

     |  // @audit-issue Save gas by switching to a do-while loop
 420 |  for (uint256 i; i < 3; ++i) {
```
GitHub: [80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L80), [95](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L95), [191](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L191), [214](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L214), [240](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L240), [259](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L259), [420](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L420)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

     |  // @audit-issue Save gas by switching to a do-while loop
  54 |  for (uint256 i; i < size; ++i) {

     |  // @audit-issue Save gas by switching to a do-while loop
 244 |  for (uint256 i; i < split.length; ++i) {

     |  // @audit-issue Save gas by switching to a do-while loop
 354 |  for (uint256 i; i < SGX_TCB_CPUSVN_SIZE + 1; ++i) {
```
GitHub: [54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L54), [244](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L244), [354](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L354)


```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

     |  // @audit-issue Save gas by switching to a do-while loop
 153 |  for (uint256 i; i < encoded.length; ++i) {

     |  // @audit-issue Save gas by switching to a do-while loop
 281 |  for (uint256 i; i < 3; ++i) {
```
GitHub: [153](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L153), [281](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L281)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

     |  // @audit-issue Save gas by switching to a do-while loop
  80 |  for (uint256 idx = 0; idx < shortest; idx += 32) {

     |  // @audit-issue Save gas by switching to a do-while loop
 333 |  for (uint256 i; i < len; ++i) {
```
GitHub: [80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L80), [333](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L333)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

     |  // @audit-issue Save gas by switching to a do-while loop
 140 |  for (uint256 i = 2; i < 2 + paddingLen; ++i) {

     |  // @audit-issue Save gas by switching to a do-while loop
 152 |  for (uint256 i; i < digestAlgoWithParamLen; ++i) {

     |  // @audit-issue Save gas by switching to a do-while loop
 158 |  for (uint256 i; i < digestAlgoWithParamLen; ++i) {

     |  // @audit-issue Save gas by switching to a do-while loop
 174 |  for (uint256 i; i < _sha256.length; ++i) {

     |  // @audit-issue Save gas by switching to a do-while loop
 273 |  for (uint256 i = 2; i < 2 + paddingLen; ++i) {

     |  // @audit-issue Save gas by switching to a do-while loop
 283 |  for (uint256 i; i < sha1Prefix.length; ++i) {

     |  // @audit-issue Save gas by switching to a do-while loop
 290 |  for (uint256 i; i < _sha1.length; ++i) {
```
GitHub: [140](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L140), [152](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L152), [158](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L158), [174](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L174), [273](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L273), [283](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L283), [290](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L290)


```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

     |  // @audit-issue Save gas by switching to a do-while loop
  48 |  for (uint16 i = 1970; i < year; ++i) {

     |  // @audit-issue Save gas by switching to a do-while loop
  59 |  for (uint8 i = 1; i < month; ++i) {
```
GitHub: [48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L48), [59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L59)


## [G-77] require()`/`revert()` strings longer than 32 bytes cost extra gas

Each extra memory word of bytes past the original 32 [incurs an MSTORE](https://gist.github.com/hrkrshnn/ee8fabd532058307229d65dcd5836ddc#consider-having-short-revert-strings) which costs **3 gas**

*Instances: 1*

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

     |  // @audit-issue @audit-issue Literal string here uses 1 additional words(s)
  89 |  require(currentKeyIndex <= key.length, "MerkleTrie: key index exceeds total key length");
```
GitHub: [89](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L89)
