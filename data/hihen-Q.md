# QA Report

## Summary

### Low Issues

Total **379 instances** over **36 issues**:

|ID|Issue|Instances|
|:--:|:---|:--:|
| [[L-01]](#l-01-function-decimals-is-not-a-part-of-the-erc-20-standard) | Function `decimals()` is not a part of the ERC-20 standard | 1 |
| [[L-02]](#l-02-direct-supportsinterface-calls-may-cause-caller-to-revert) | Direct `supportsInterface()` calls may cause caller to revert | 3 |
| [[L-03]](#l-03-use-increaseallowancedecreaseallowance-instead-of-approvesafeapprove) | Use `increaseAllowance()`/`decreaseAllowance()` instead of `approve()`/`safeApprove()` | 1 |
| [[L-04]](#l-04-events-may-be-emitted-out-of-order-due-to-reentrancy) | Events may be emitted out of order due to reentrancy | 27 |
| [[L-05]](#l-05-nft-doesnt-handle-hard-forks) | NFT doesn't handle hard forks | 1 |
| [[L-06]](#l-06-variables-shadowing-other-definitions) | Variables shadowing other definitions | 35 |
| [[L-07]](#l-07-missing-zero-address-check-in-constructor) | Missing zero address check in constructor | 3 |
| [[L-08]](#l-08-missing-zero-address-check-in-initializer) | Missing zero address check in initializer | 47 |
| [[L-09]](#l-09-owner-can-renounce-while-system-is-paused) | Owner can renounce while system is paused | 1 |
| [[L-10]](#l-10-function-receivepayable-fallback-does-not-authorize-sender) | Function `receive()`/`payable fallback()` does not authorize sender | 2 |
| [[L-11]](#l-11-revert-on-transfer-to-the-zero-address) | Revert on transfer to the zero address | 8 |
| [[L-12]](#l-12-array-is-pushed-but-not-poped) | Array is `push()`ed but not `pop()`ed | 1 |
| [[L-13]](#l-13-state-variables-not-limited-to-reasonable-values) | State variables not limited to reasonable values | 2 |
| [[L-14]](#l-14-function-symbol-is-not-a-part-of-the-erc-20-standard) | Function `symbol()` is not a part of the ERC-20 standard | 3 |
| [[L-15]](#l-15-tokenuri-does-not-follow-eip-721) | `tokenURI()` does not follow EIP-721 | 1 |
| [[L-16]](#l-16-consider-implementing-two-step-procedure-for-updating-protocol-addresses) | Consider implementing two-step procedure for updating protocol addresses | 4 |
| [[L-17]](#l-17-unsafe-conversion-from-unsigned-to-signed-values) | Unsafe conversion from unsigned to signed values | 5 |
| [[L-18]](#l-18-downcasting-other-types-to-an-address-can-cause-collisions) | Downcasting other types to an address can cause collisions | 3 |
| [[L-19]](#l-19-upgradeable-contract-not-initialized) | Upgradeable contract not initialized | 3 |
| [[L-20]](#l-20-vulnerable-versions-of-packages-are-being-used) | Vulnerable versions of packages are being used | 6 |
| [[L-21]](#l-21-inappropriate-storage-gap-size) | Inappropriate storage gap size | 1 |
| [[L-22]](#l-22-constructor--initialization-function-lacks-parameter-validation) | Constructor / initialization function lacks parameter validation | 19 |
| [[L-23]](#l-23-missing-checks-for-address0-when-setting-address-state-variables) | Missing checks for `address(0)` when setting address state variables | 2 |
| [[L-24]](#l-24-unsafe-solidity-low-level-call-can-cause-gas-grief-attack) | Unsafe solidity low-level call can cause gas grief attack | 3 |
| [[L-25]](#l-25-minting-in-a-loop-may-lead-to-a-dos) | Minting in a loop may lead to a DOS | 1 |
| [[L-26]](#l-26-owner-can-renounce-ownership) | Owner can renounce Ownership | 34 |
| [[L-27]](#l-27-functions-calling-contractsaddresses-with-transfer-hooks-should-be-protected-by-reentrancy-guard) | Functions calling contracts/addresses with transfer hooks should be protected by reentrancy guard | 15 |
| [[L-28]](#l-28-critical-functions-should-be-controlled-by-time-locks) | Critical functions should be controlled by time locks | 19 |
| [[L-29]](#l-29-external-function-calls-within-loops) | External function calls within loops | 9 |
| [[L-30]](#l-30-tokens-may-be-minted-to-the-zero-address) | Tokens may be minted to the zero address | 12 |
| [[L-31]](#l-31-sending-tokens-within-loops) | Sending tokens within loops | 5 |
| [[L-32]](#l-32-use-safecast-to-downcast-safely) | Use `SafeCast` to downcast safely | 37 |
| [[L-33]](#l-33-use-descriptive-constant-instead-of-0-as-a-parameter) | Use descriptive constant instead of 0 as a parameter | 22 |
| [[L-34]](#l-34-loss-of-precision-in-divisions) | Loss of precision in divisions | 4 |
| [[L-35]](#l-35-code-does-not-follow-the-best-practice-of-check-effects-interaction) | Code does not follow the best practice of check-effects-interaction | 23 |
| [[L-36]](#l-36-unchecked-blocks-with-subtractions-may-underflow) | `unchecked` blocks with subtractions may underflow | 16 |

### Non Critical Issues

Total **3366 instances** over **100 issues**:

|ID|Issue|Instances|
|:--:|:---|:--:|
| [[N-01]](#n-01-abiencodepacked-should-be-replaced-with-bytesconcat) | `abi.encodePacked()` should be replaced with `bytes.concat()` | 11 |
| [[N-02]](#n-02-abiencodepacked-on-strings-should-be-replaced-with-stringconcat) | `abi.encodePacked()` on strings should be replaced with `string.concat()` | 2 |
| [[N-03]](#n-03-custom-errors-has-no-error-details) | Custom errors has no error details | 160 |
| [[N-04]](#n-04-import-declarations-should-import-specific-identifiers-rather-than-the-whole-file) | Import declarations should import specific identifiers, rather than the whole file | 179 |
| [[N-05]](#n-05-visibility-of-state-variables-is-not-explicitly-defined) | Visibility of state variables is not explicitly defined | 3 |
| [[N-06]](#n-06-there-is-no-need-to-initialize-variables-with-0) | There is no need to initialize variables with 0 | 13 |
| [[N-07]](#n-07-names-of-privateinternal-functions-should-be-prefixed-with-an-underscore) | Names of `private`/`internal` functions should be prefixed with an underscore | 96 |
| [[N-08]](#n-08-names-of-privateinternal-state-variables-should-be-prefixed-with-an-underscore) | Names of `private`/`internal` state variables should be prefixed with an underscore | 18 |
| [[N-09]](#n-09-order-of-functions-does-not-follow-the-solidity-style-guide) | Order of functions does not follow the Solidity Style Guide | 29 |
| [[N-10]](#n-10-the-nonreentrant-modifier-should-occur-before-all-other-modifiers) | The `nonReentrant` `modifier` should occur before all other modifiers | 4 |
| [[N-11]](#n-11-redundant-inheritance-specifier) | Redundant inheritance specifier | 3 |
| [[N-12]](#n-12-use-of-override-is-unnecessary) | Use of `override` is unnecessary | 43 |
| [[N-13]](#n-13-unused-errors) | Unused errors | 1 |
| [[N-14]](#n-14-unused-structs) | Unused `struct`s | 1 |
| [[N-15]](#n-15-custom-errors-should-be-used-rather-than-revertrequire) | Custom errors should be used rather than `revert()`/`require()` | 66 |
| [[N-16]](#n-16-large-numeric-literals-should-use-underscores-for-readability) | Large numeric literals should use underscores for readability | 18 |
| [[N-17]](#n-17-add-inline-comments-for-unnamed-parameters) | Add inline comments for unnamed parameters | 11 |
| [[N-18]](#n-18-consider-providing-a-ranged-getter-for-array-state-variables) | Consider providing a ranged getter for array state variables | 1 |
| [[N-19]](#n-19-assembly-blocks-should-have-extensive-comments) | Assembly blocks should have extensive comments | 31 |
| [[N-20]](#n-20-consider-splitting-complex-checks-into-multiple-steps) | Consider splitting complex checks into multiple steps | 1 |
| [[N-21]](#n-21-cast-is-more-restrictive-than-the-type-of-the-variable-being-assigned) | Cast is more restrictive than the type of the variable being assigned | 2 |
| [[N-22]](#n-22-consider-moving-msgsender-checks-to-modifiers) | Consider moving `msg.sender` checks to `modifier`s | 8 |
| [[N-23]](#n-23-missing-checks-for-empty-bytes-when-updating-bytes-state-variables) | Missing checks for empty bytes when updating bytes state variables | 1 |
| [[N-24]](#n-24-complex-casting) | Complex casting | 2 |
| [[N-25]](#n-25-complex-math-should-be-split-into-multiple-steps) | Complex math should be split into multiple steps | 14 |
| [[N-26]](#n-26-consider-adding-a-blockdeny-list) | Consider adding a block/deny-list | 11 |
| [[N-27]](#n-27-convert-simple-if-statements-to-ternary-expressions) | Convert simple `if`-statements to ternary expressions | 8 |
| [[N-28]](#n-28-contracts-should-each-be-defined-in-separate-files) | Contracts should each be defined in separate files | 5 |
| [[N-29]](#n-29-upper_case-names-should-be-reserved-for-constantimmutable-variables) | UPPER_CASE names should be reserved for `constant`/`immutable` variables | 1 |
| [[N-30]](#n-30-do-not-use-literal-numbers-for-array-indexes) | Do not use literal numbers for array indexes | 37 |
| [[N-31]](#n-31-consider-emitting-an-event-at-the-end-of-the-constructor) | Consider emitting an event at the end of the constructor | 3 |
| [[N-32]](#n-32-empty-function-body-without-comments) | Empty function body without comments | 5 |
| [[N-33]](#n-33-events-are-emitted-without-the-sender-information) | Events are emitted without the sender information | 26 |
| [[N-34]](#n-34-event-is-missing-indexed-fields) | Event is missing `indexed` fields | 28 |
| [[N-35]](#n-35-contract-implements-interface-without-extending-the-interface) | Contract implements interface without extending the interface | 2 |
| [[N-36]](#n-36-imports-could-be-organized-more-systematically) | Imports could be organized more systematically | 31 |
| [[N-37]](#n-37-openzeppelincontracts-should-be-upgraded-to-a-newer-version) | @openzeppelin/contracts should be upgraded to a newer version | 54 |
| [[N-38]](#n-38-lib-openzeppelincontracts-upgradeable-should-be-upgraded-to-a-newer-version) | Lib @openzeppelin/contracts-upgradeable should be upgraded to a newer version | 19 |
| [[N-39]](#n-39-lines-are-too-long) | Lines are too long | 6 |
| [[N-40]](#n-40-magic-numbers-should-be-replaced-with-constants) | Magic numbers should be replaced with constants | 480 |
| [[N-41]](#n-41-expressions-for-constant-values-should-use-immutable-rather-than-constant) | Expressions for constant values should use `immutable` rather than `constant` | 3 |
| [[N-42]](#n-42-consider-moving-duplicated-strings-to-constants) | Consider moving duplicated strings to constants | 69 |
| [[N-43]](#n-43-functions-not-used-internally-could-be-marked-external) | Functions not used internally could be marked external | 65 |
| [[N-44]](#n-44-contracts-containing-only-utility-functions-should-be-made-into-libraries) | Contracts containing only utility functions should be made into libraries | 3 |
| [[N-45]](#n-45-error-names-should-use-capwords-style) | Error names should use CapWords style | 160 |
| [[N-46]](#n-46-functions-should-be-named-in-mixedcase-style) | Functions should be named in mixedCase style | 16 |
| [[N-47]](#n-47-variable-names-for-immutables-should-use-upper_case_with_underscores) | Variable names for `immutable`s should use UPPER_CASE_WITH_UNDERSCORES | 2 |
| [[N-48]](#n-48-order-of-contract-layout-does-not-follow-the-solidity-style-guide) | Order of contract layout does not follow the Solidity Style Guide | 2 |
| [[N-49]](#n-49-consider-adding-validation-of-user-inputs) | Consider adding validation of user inputs | 20 |
| [[N-50]](#n-50-named-imports-of-parent-contracts-are-missing) | Named imports of parent contracts are missing | 71 |
| [[N-51]](#n-51-each-interfaces-should-be-defined-in-a-separate-file) | Each interfaces should be defined in a separate file | 6 |
| [[N-52]](#n-52-libraries-should-be-defined-in-separate-files) | Libraries should be defined in separate files | 3 |
| [[N-53]](#n-53-put-all-system-wide-constants-in-one-file) | Put all system-wide constants in one file | 23 |
| [[N-54]](#n-54-else-block-not-required) | `else`-block not required | 20 |
| [[N-55]](#n-55-assertshould-be-replaced-with-require-or-revert) | `assert()` should be replaced with `require()` or `revert()` | 4 |
| [[N-56]](#n-56-large-multiples-of-ten-should-use-scientific-notation) | Large multiples of ten should use scientific notation | 19 |
| [[N-57]](#n-57-high-cyclomatic-complexity) | High cyclomatic complexity | 2 |
| [[N-58]](#n-58-typos) | Typos | 7 |
| [[N-59]](#n-59-consider-bounding-input-array-length) | Consider bounding input array length | 13 |
| [[N-60]](#n-60-unnecessary-casting) | Unnecessary casting | 1 |
| [[N-61]](#n-61-unused-import) | Unused import | 9 |
| [[N-62]](#n-62-unused-named-return) | Unused named return | 10 |
| [[N-63]](#n-63-use-delete-instead-of-assigning-values-to-false) | Use delete instead of assigning values to `false` | 2 |
| [[N-64]](#n-64-consider-using-delete-rather-than-assigning-zero-to-clear-values) | Consider using `delete` rather than assigning zero to clear values | 14 |
| [[N-65]](#n-65-use-the-latest-solidity-version) | Use the latest Solidity version | 81 |
| [[N-66]](#n-66-consider-using-named-function-arguments) | Consider using named function arguments | 23 |
| [[N-67]](#n-67-named-mappings-are-recommended) | Named mappings are recommended | 8 |
| [[N-68]](#n-68-named-returns-are-recommended) | Named returns are recommended | 143 |
| [[N-69]](#n-69-use-typexmax-instead-of-constant-formulas-like-2n) | Use `type(X).max` instead of constant formulas like `2**n` | 2 |
| [[N-70]](#n-70-consider-using-the-using-for-syntax) | Consider using the `using`-`for` syntax | 96 |
| [[N-71]](#n-71-using-underscore-at-the-end-of-variable-name) | Using underscore at the end of variable name | 95 |
| [[N-72]](#n-72-use-a-struct-to-encapsulate-multiple-function-parameters) | Use a struct to encapsulate multiple function parameters | 8 |
| [[N-73]](#n-73-returning-a-struct-instead-of-a-bunch-of-variables-is-better) | Returning a struct instead of a bunch of variables is better | 15 |
| [[N-74]](#n-74-events-that-mark-critical-parameter-changes-should-contain-both-the-old-and-the-new-value) | Events that mark critical parameter changes should contain both the old and the new value | 4 |
| [[N-75]](#n-75-contract-variables-should-have-comments) | Contract variables should have comments | 41 |
| [[N-76]](#n-76-missing-event-when-a-state-variables-is-set-in-constructor) | Missing event when a state variables is set in constructor | 2 |
| [[N-77]](#n-77-empty-bytes-check-is-missing) | Empty bytes check is missing | 13 |
| [[N-78]](#n-78-dont-define-functions-with-the-same-name-in-a-contract) | Don't define functions with the same name in a contract | 14 |
| [[N-79]](#n-79-interface-files-should-not-use-fixed-compiler-versions) | Interface files should not use fixed compiler versions | 11 |
| [[N-80]](#n-80-addresses-shouldnt-be-hard-coded) | Addresses shouldn't be hard-coded | 2 |
| [[N-81]](#n-81-assembly-block-creates-dirty-bits) | Assembly block creates dirty bits | 5 |
| [[N-82]](#n-82-multiple-mappings-with-same-keys-can-be-combined-into-a-single-struct-mapping-for-readability) | Multiple mappings with same keys can be combined into a single struct mapping for readability | 8 |
| [[N-83]](#n-83-control-structures-do-not-follow-the-solidity-style-guide) | Control structures do not follow the Solidity Style Guide | 362 |
| [[N-84]](#n-84-too-long-functions-should-be-refactored) | Too long functions should be refactored | 9 |
| [[N-85]](#n-85-inconsistent-spacing-in-comments) | Inconsistent spacing in comments | 44 |
| [[N-86]](#n-86-missing-event-for-critical-changes) | Missing event for critical changes | 7 |
| [[N-87]](#n-87-non-assembly-method-available) | Non-assembly method available | 3 |
| [[N-88]](#n-88-duplicated-requirerevert-checks-should-be-refactored) | Duplicated `require()`/`revert()` checks should be refactored | 23 |
| [[N-89]](#n-89-consider-adding-emergency-stop-functionality) | Consider adding emergency-stop functionality | 27 |
| [[N-90]](#n-90-avoid-the-use-of-sensitive-terms) | Avoid the use of sensitive terms | 12 |
| [[N-91]](#n-91-missing-checks-for-uint-state-variable-assignments) | Missing checks for uint state variable assignments | 8 |
| [[N-92]](#n-92-use-the-modern-upgradeable-contract-paradigm) | Use the Modern Upgradeable Contract Paradigm | 3 |
| [[N-93]](#n-93-large-or-complicated-code-bases-should-implement-invariant-tests) | Large or complicated code bases should implement invariant tests | 1 |
| [[N-94]](#n-94-the-default-value-is-manually-set-when-it-is-declared) | The default value is manually set when it is declared | 13 |
| [[N-95]](#n-95-contracts-should-have-all-publicexternal-functions-exposed-by-interfaces) | Contracts should have all `public`/`external` functions exposed by `interface`s | 28 |
| [[N-96]](#n-96-top-level-declarations-should-be-separated-by-at-least-two-lines) | Top-level declarations should be separated by at least two lines | 167 |
| [[N-97]](#n-97-consider-adding-formal-verification-proofs) | Consider adding formal verification proofs | 81 |
| [[N-98]](#n-98-use-scopes-sparingly) | Use scopes sparingly | 12 |
| [[N-99]](#n-99-prevent-re-setting-a-state-variable-with-the-same-value) | Prevent re-setting a state variable with the same value | 13 |
| [[N-100]](#n-100-numeric-values-having-to-do-with-time-should-use-time-units-for-readability) | Numeric values having to do with time should use time units for readability | 4 |

## Low Issues

### [L-01] Function `decimals()` is not a part of the ERC-20 standard

The `symbol()` function is not a part of the [ERC-20 standard](https://eips.ethereum.org/EIPS/eip-20), and was added later as an [optional extension](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC20/extensions/IERC20Metadata.sol). As such, some valid ERC20 tokens do not support this interface, so it is unsafe to blindly cast all tokens to this interface, and then call this function.

There is 1 instance:

- *ERC20Vault.sol* ( [368-368](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L368-L368) ):

```solidity
368:                 decimals: meta.decimals(),
```

### [L-02] Direct `supportsInterface()` calls may cause caller to revert

Calling `supportsInterface()` on a contract that doesn't implement the ERC-165 standard will result in the call reverting. Even if the caller does support the function, the contract may be malicious and consume all of the transaction's available gas.

Call it via a low-level [staticcall()](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/f959d7e4e6ee0b022b41e5b644c79369869d8411/contracts/utils/introspection/ERC165Checker.sol#L119), with a fixed amount of gas, and check the return code, or use OpenZeppelin's [`ERC165Checker.supportsInterface()`](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/f959d7e4e6ee0b022b41e5b644c79369869d8411/contracts/utils/introspection/ERC165Checker.sol#L36-L39).

There are 3 instances:

- *Bridge.sol* ( [195-195](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L195-L195) ):

```solidity
195:             if (_message.from.supportsInterface(type(IRecallableSender).interfaceId)) {
```

- *ERC1155Vault.sol* ( [51-51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L51-L51) ):

```solidity
51:         if (!_op.token.supportsInterface(ERC1155_INTERFACE_ID)) {
```

- *ERC721Vault.sol* ( [38-38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L38-L38) ):

```solidity
38:         if (!_op.token.supportsInterface(ERC721_INTERFACE_ID)) {
```

### [L-03] Use `increaseAllowance()`/`decreaseAllowance()` instead of `approve()`/`safeApprove()`

Changing an allowance with `approve()` brings the risk that someone may use both the old and the new allowance by unfortunate transaction ordering. Refer to [ERC20 API: An Attack Vector on the Approve/TransferFrom Methods](https://docs.google.com/document/d/1YLPtQxZu1UAvO9cZ1O2RPXBbT0mooh4DYKjA_jp-RLM).
It is recommended to use the `increaseAllowance()`/`decreaseAllowance()` to avoid ths problem.

There is 1 instance:

- *GuardianProver.sol* ( [47-47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/GuardianProver.sol#L47-L47) ):

```solidity
47:         approved_ = approve(_meta.id, hash);
```

### [L-04] Events may be emitted out of order due to reentrancy

Ensure that events follow the best practice of check-effects-interaction, and are emitted before external calls.

<details>
<summary>There are 27 instances (click to show):</summary>

- *AssignmentHook.sol* ( [129-129](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L129-L129) ):

```solidity
/// @audit transferFrom() is called prior to this emission in onBlockProposed()
129:         emit BlockAssigned(_blk.assignedProver, _meta, assignment);
```

- *LibProposing.sol* ( [273-279](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L273-L279) ):

```solidity
/// @audit onBlockProposed() is called prior to this emission in proposeBlock()
273:         emit BlockProposed({
274:             blockId: blk.blockId,
275:             assignedProver: blk.assignedProver,
276:             livenessBond: _config.livenessBond,
277:             meta: meta_,
278:             depositsProcessed: deposits_
279:         });
```

- *LibProving.sol* ( [209-215](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L209-L215), [230-236](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L230-L236), [254-260](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L254-L260) ):

```solidity
/// @audit _overrideWithHigherProof() is called prior to this emission in proveBlock(), which will call `transferFrom()`
209:             emit TransitionProved({
210:                 blockId: blk.blockId,
211:                 tran: _tran,
212:                 prover: msg.sender,
213:                 validityBond: tier.validityBond,
214:                 tier: _proof.tier
215:             });

/// @audit _overrideWithHigherProof() is called prior to this emission in proveBlock(), which will call `transferFrom()`
230:                 emit TransitionProved({
231:                     blockId: blk.blockId,
232:                     tran: _tran,
233:                     prover: msg.sender,
234:                     validityBond: 0,
235:                     tier: _proof.tier
236:                 });

/// @audit _overrideWithHigherProof() is called prior to this emission in proveBlock(), which will call `transferFrom()`
254:                 emit TransitionContested({
255:                     blockId: blk.blockId,
256:                     tran: _tran,
257:                     contester: msg.sender,
258:                     contestBond: tier.contestBond,
259:                     tier: _proof.tier
260:                 });
```

- *LibVerifying.sol* ( [198-206](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L198-L206) ):

```solidity
/// @audit transfer() is called prior to this emission in verifyBlocks()
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

- *GuardianProver.sol* ( [54-54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/GuardianProver.sol#L54-L54) ):

```solidity
/// @audit proveBlock() is called prior to this emission in approve()
54:         emit GuardianApproval(msg.sender, _meta.id, _tran.blockHash, approved_);
```

- *CrossChainOwned.sol* ( [53-53](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L53-L53) ):

```solidity
/// @audit call() is called prior to this emission in onMessageInvocation()
53:         emit TransactionExecuted(nextTxId++, bytes4(txdata));
```

- *TaikoL2.sol* ( [157-157](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L157-L157) ):

```solidity
/// @audit syncChainData() is called prior to this emission in anchor()
157:         emit Anchored(blockhash(parentId), gasExcess);
```

- *Bridge.sol* ( [151-151](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L151-L151), [208-208](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L208-L208), [210-210](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L210-L210), [301-301](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L301-L301), [303-303](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L303-L303), [336-336](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L336-L336) ):

```solidity
/// @audit sendSignal() is called prior to this emission in sendMessage()
151:         emit MessageSent(msgHash_, message_);

/// @audit _proveSignalReceived() is called prior to this emission in recallMessage(), which will call `staticcall()`
208:             emit MessageRecalled(msgHash);

/// @audit _proveSignalReceived() is called prior to this emission in recallMessage(), which will call `staticcall()`
210:             emit MessageReceived(msgHash, _message, true);

/// @audit _proveSignalReceived() is called prior to this emission in processMessage(), which will call `staticcall()`
301:             emit MessageExecuted(msgHash);

/// @audit _proveSignalReceived() is called prior to this emission in processMessage(), which will call `staticcall()`
303:             emit MessageReceived(msgHash, _message, false);

/// @audit _updateMessageStatus() is called prior to this emission in retryMessage(), which will call `sendSignal()`
336:         emit MessageRetried(msgHash);
```

- *TimelockTokenPool.sol* ( [222-222](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L222-L222) ):

```solidity
/// @audit transferFrom() is called prior to this emission in _withdraw()
222:         emit Withdrawn(_recipient, _to, amountToWithdraw, costToWithdraw);
```

- *ERC20Airdrop2.sol* ( [93-93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L93-L93) ):

```solidity
/// @audit transferFrom() is called prior to this emission in withdraw()
93:         emit Withdrawn(user, amount);
```

- *ERC1155Vault.sol* ( [80-89](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L80-L89), [114-123](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L114-L123), [149-156](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L149-L156) ):

```solidity
/// @audit _handleMessage() is called prior to this emission in sendToken(), which will call `safeTransferFrom()`
80:         emit TokenSent({
81:             msgHash: msgHash,
82:             from: message_.srcOwner,
83:             to: _op.to,
84:             destChainId: message_.destChainId,
85:             ctoken: ctoken.addr,
86:             token: _op.token,
87:             tokenIds: _op.tokenIds,
88:             amounts: _op.amounts
89:         });

/// @audit _transferTokens() is called prior to this emission in onMessageInvocation(), which will call `mintBatch()`
114:         emit TokenReceived({
115:             msgHash: ctx.msgHash,
116:             from: from,
117:             to: to,
118:             srcChainId: ctx.srcChainId,
119:             ctoken: ctoken.addr,
120:             token: token,
121:             tokenIds: tokenIds,
122:             amounts: amounts
123:         });

/// @audit _transferTokens() is called prior to this emission in onMessageRecalled(), which will call `mintBatch()`
149:         emit TokenReleased({
150:             msgHash: msgHash,
151:             from: message.srcOwner,
152:             ctoken: ctoken.addr,
153:             token: token,
154:             tokenIds: tokenIds,
155:             amounts: amounts
156:         });
```

- *ERC20Vault.sol* ( [191-199](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L191-L199), [241-249](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L241-L249), [273-281](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L273-L281), [306-312](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L306-L312) ):

```solidity
/// @audit changeMigrationStatus() is called prior to this emission in changeBridgedToken()
191:         emit BridgedTokenChanged({
192:             srcChainId: _ctoken.chainId,
193:             ctoken: _ctoken.addr,
194:             btokenOld: btokenOld_,
195:             btokenNew: _btokenNew,
196:             ctokenSymbol: _ctoken.symbol,
197:             ctokenName: _ctoken.name,
198:             ctokenDecimal: _ctoken.decimals
199:         });

/// @audit _handleMessage() is called prior to this emission in sendToken(), which will call `safeTransferFrom()`
241:         emit TokenSent({
242:             msgHash: msgHash,
243:             from: message_.srcOwner,
244:             to: _op.to,
245:             destChainId: _op.destChainId,
246:             ctoken: ctoken.addr,
247:             token: _op.token,
248:             amount: balanceChange
249:         });

/// @audit _transferTokens() is called prior to this emission in onMessageInvocation(), which will call `mint()`
273:         emit TokenReceived({
274:             msgHash: ctx.msgHash,
275:             from: from,
276:             to: to,
277:             srcChainId: ctx.srcChainId,
278:             ctoken: ctoken.addr,
279:             token: token,
280:             amount: amount
281:         });

/// @audit _transferTokens() is called prior to this emission in onMessageRecalled(), which will call `mint()`
306:         emit TokenReleased({
307:             msgHash: _msgHash,
308:             from: _message.srcOwner,
309:             ctoken: ctoken.addr,
310:             token: token,
311:             amount: amount
312:         });
```

- *ERC721Vault.sol* ( [64-73](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L64-L73), [97-106](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L97-L106), [131-138](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L131-L138) ):

```solidity
/// @audit _handleMessage() is called prior to this emission in sendToken(), which will call `safeTransferFrom()`
64:         emit TokenSent({
65:             msgHash: msgHash,
66:             from: message_.srcOwner,
67:             to: _op.to,
68:             destChainId: message_.destChainId,
69:             ctoken: ctoken.addr,
70:             token: _op.token,
71:             tokenIds: _op.tokenIds,
72:             amounts: _op.amounts
73:         });

/// @audit _transferTokens() is called prior to this emission in onMessageInvocation(), which will call `mint()`
97:         emit TokenReceived({
98:             msgHash: ctx.msgHash,
99:             from: from,
100:             to: to,
101:             srcChainId: ctx.srcChainId,
102:             ctoken: ctoken.addr,
103:             token: token,
104:             tokenIds: tokenIds,
105:             amounts: new uint256[](tokenIds.length)
106:         });

/// @audit _transferTokens() is called prior to this emission in onMessageRecalled(), which will call `mint()`
131:         emit TokenReleased({
132:             msgHash: _msgHash,
133:             from: _message.srcOwner,
134:             ctoken: ctoken.addr,
135:             token: token,
136:             tokenIds: tokenIds,
137:             amounts: new uint256[](tokenIds.length)
138:         });
```

</details>

### [L-05] NFT doesn't handle hard forks

When there are hard forks, users often have to go through [many hoops](https://twitter.com/elerium115/status/1558471934924431363) to ensure that they control ownership on every fork. Consider adding `require(1 == chain.chainId)`, or the chain ID of whichever chain you prefer, to the functions below, or at least include the chain ID in the URI, so that there is no confusion about which chain is the owner of the NFT.

There is 1 instance:

- *BridgedERC721.sol* ( [107-113](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L107-L113) ):

```solidity
107:     function tokenURI(uint256 _tokenId) public view virtual override returns (string memory) {
108:         return string(
109:             abi.encodePacked(
110:                 LibBridgedToken.buildURI(srcToken, srcChainId), Strings.toString(_tokenId)
111:             )
112:         );
113:     }
```

### [L-06] Variables shadowing other definitions

A variable declaration shadowing any other existing definition is error-prone. It can cause confusion for developers, potentially introduce bugs, and reduce the readability and maintainability.

<details>
<summary>There are 35 instances (click to show):</summary>

- *TaikoL1.sol* ( [43-43](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L43-L43) ):

```solidity
/// @audit Shadows `state variable _owner`
43:         address _owner,
```

- *TaikoToken.sol* ( [26-26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L26-L26), [27-27](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L27-L27), [28-28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L28-L28) ):

```solidity
/// @audit Shadows `state variable _owner`
26:         address _owner,

/// @audit Shadows `state variable _name`
27:         string calldata _name,

/// @audit Shadows `state variable _symbol`
28:         string calldata _symbol,
```

- *TaikoGovernor.sol* ( [32-32](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L32-L32), [34-34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L34-L34) ):

```solidity
/// @audit Shadows `state variable _owner`
32:         address _owner,

/// @audit Shadows `state variable _timelock`
34:         TimelockControllerUpgradeable _timelock
```

- *TaikoTimelockController.sol* ( [15-15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L15-L15), [15-15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L15-L15) ):

```solidity
/// @audit Shadows `state variable _owner`
15:     function init(address _owner, uint256 _minDelay) external initializer {

/// @audit Shadows `state variable _minDelay`
15:     function init(address _owner, uint256 _minDelay) external initializer {
```

- *AssignmentHook.sol* ( [57-57](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L57-L57) ):

```solidity
/// @audit Shadows `state variable _owner`
57:     function init(address _owner, address _addressManager) external initializer {
```

- *GuardianProver.sol* ( [25-25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/GuardianProver.sol#L25-L25) ):

```solidity
/// @audit Shadows `state variable _owner`
25:     function init(address _owner, address _addressManager) external initializer {
```

- *DevnetTierProvider.sol* ( [15-15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L15-L15) ):

```solidity
/// @audit Shadows `state variable _owner`
15:     function init(address _owner) external initializer {
```

- *MainnetTierProvider.sol* ( [15-15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L15-L15) ):

```solidity
/// @audit Shadows `state variable _owner`
15:     function init(address _owner) external initializer {
```

- *TestnetTierProvider.sol* ( [15-15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L15-L15) ):

```solidity
/// @audit Shadows `state variable _owner`
15:     function init(address _owner) external initializer {
```

- *CrossChainOwned.sol* ( [61-61](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L61-L61) ):

```solidity
/// @audit Shadows `state variable _owner`
61:         address _owner,
```

- *TaikoL2.sol* ( [72-72](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L72-L72) ):

```solidity
/// @audit Shadows `state variable _owner`
72:         address _owner,
```

- *Bridge.sol* ( [75-75](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L75-L75) ):

```solidity
/// @audit Shadows `state variable _owner`
75:     function init(address _owner, address _addressManager) external initializer {
```

- *AddressManager.sol* ( [30-30](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L30-L30) ):

```solidity
/// @audit Shadows `state variable _owner`
30:     function init(address _owner) external initializer {
```

- *EssentialContract.sol* ( [96-96](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L96-L96), [109-109](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L109-L109) ):

```solidity
/// @audit Shadows `state variable _owner`
96:         address _owner,

/// @audit Shadows `state variable _owner`
109:     function __Essential_init(address _owner) internal virtual {
```

- *SignalService.sol* ( [48-48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L48-L48) ):

```solidity
/// @audit Shadows `state variable _owner`
48:     function init(address _owner, address _addressManager) external initializer {
```

- *TimelockTokenPool.sol* ( [112-112](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L112-L112) ):

```solidity
/// @audit Shadows `state variable _owner`
112:         address _owner,
```

- *ERC20Airdrop.sol* ( [28-28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L28-L28) ):

```solidity
/// @audit Shadows `state variable _owner`
28:         address _owner,
```

- *ERC20Airdrop2.sol* ( [55-55](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L55-L55) ):

```solidity
/// @audit Shadows `state variable _owner`
55:         address _owner,
```

- *ERC721Airdrop.sol* ( [26-26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L26-L26) ):

```solidity
/// @audit Shadows `state variable _owner`
26:         address _owner,
```

- *BaseVault.sol* ( [32-32](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L32-L32) ):

```solidity
/// @audit Shadows `state variable _owner`
32:     function init(address _owner, address _addressManager) external initializer {
```

- *BridgedERC1155.sol* ( [39-39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L39-L39) ):

```solidity
/// @audit Shadows `state variable _owner`
39:         address _owner,
```

- *BridgedERC20.sol* ( [53-53](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L53-L53), [58-58](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L58-L58), [59-59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L59-L59) ):

```solidity
/// @audit Shadows `state variable _owner`
53:         address _owner,

/// @audit Shadows `state variable _symbol`
58:         string memory _symbol,

/// @audit Shadows `state variable _name`
59:         string memory _name
```

- *BridgedERC721.sol* ( [32-32](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L32-L32), [36-36](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L36-L36), [37-37](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L37-L37) ):

```solidity
/// @audit Shadows `state variable _owner`
32:         address _owner,

/// @audit Shadows `state variable _symbol`
36:         string memory _symbol,

/// @audit Shadows `state variable _name`
37:         string memory _name
```

- *USDCAdapter.sol* ( [38-38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L38-L38) ):

```solidity
/// @audit Shadows `state variable _owner`
38:     function init(address _owner, address _addressManager, IUSDC _usdc) external initializer {
```

- *GuardianVerifier.sol* ( [18-18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L18-L18) ):

```solidity
/// @audit Shadows `state variable _owner`
18:     function init(address _owner, address _addressManager) external initializer {
```

- *SgxVerifier.sol* ( [83-83](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L83-L83) ):

```solidity
/// @audit Shadows `state variable _owner`
83:     function init(address _owner, address _addressManager) external initializer {
```

</details>

### [L-07] Missing zero address check in constructor

Constructors often take address parameters to initialize important components of a contract, such as owner or linked contracts. However, without a checking, there's a risk that an address parameter could be mistakenly set to the zero address (0x0). This could be due to an error or oversight during contract deployment. A zero address in a crucial role can cause serious issues, as it cannot perform actions like a normal address, and any funds sent to it will be irretrievable. It's therefore crucial to include a zero address check in constructors to prevent such potential problems. If a zero address is detected, the constructor should revert the transaction.

There are 3 instances:

- *AutomataDcapV3Attestation.sol* ( [54-54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L54-L54) ):

```solidity
/// @audit `sigVerifyLibAddr not checked`
/// @audit `pemCertLibAddr not checked`
54:     constructor(address sigVerifyLibAddr, address pemCertLibAddr) {
```

- *SigVerifyLib.sol* ( [20-20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L20-L20) ):

```solidity
/// @audit `es256Verifier not checked`
20:     constructor(address es256Verifier) {
```

### [L-08] Missing zero address check in initializer

Consider adding a zero address check for each address type parameter in initializer.

<details>
<summary>There are 47 instances (click to show):</summary>

- *TaikoL1.sol* ( [42-46](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L42-L46) ):

```solidity
/// @audit `_owner not checked`
/// @audit `_addressManager not checked`
42:     function init(
43:         address _owner,
44:         address _addressManager,
45:         bytes32 _genesisBlockHash
46:     )
```

- *TaikoToken.sol* ( [25-30](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L25-L30) ):

```solidity
/// @audit `_owner not checked`
/// @audit `_recipient not checked`
25:     function init(
26:         address _owner,
27:         string calldata _name,
28:         string calldata _symbol,
29:         address _recipient
30:     )
```

- *TaikoGovernor.sol* ( [31-35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L31-L35) ):

```solidity
/// @audit `_owner not checked`
/// @audit `_token not checked`
/// @audit `_timelock not checked`
31:     function init(
32:         address _owner,
33:         IVotesUpgradeable _token,
34:         TimelockControllerUpgradeable _timelock
35:     )
```

- *TaikoTimelockController.sol* ( [15-15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L15-L15) ):

```solidity
/// @audit `_owner not checked`
15:     function init(address _owner, uint256 _minDelay) external initializer {
```

- *AssignmentHook.sol* ( [57-57](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L57-L57) ):

```solidity
/// @audit `_owner not checked`
/// @audit `_addressManager not checked`
57:     function init(address _owner, address _addressManager) external initializer {
```

- *GuardianProver.sol* ( [25-25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/GuardianProver.sol#L25-L25) ):

```solidity
/// @audit `_owner not checked`
/// @audit `_addressManager not checked`
25:     function init(address _owner, address _addressManager) external initializer {
```

- *DevnetTierProvider.sol* ( [15-15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L15-L15) ):

```solidity
/// @audit `_owner not checked`
15:     function init(address _owner) external initializer {
```

- *MainnetTierProvider.sol* ( [15-15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L15-L15) ):

```solidity
/// @audit `_owner not checked`
15:     function init(address _owner) external initializer {
```

- *TestnetTierProvider.sol* ( [15-15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L15-L15) ):

```solidity
/// @audit `_owner not checked`
15:     function init(address _owner) external initializer {
```

- *TaikoL2.sol* ( [71-76](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L71-L76) ):

```solidity
/// @audit `_owner not checked`
/// @audit `_addressManager not checked`
71:     function init(
72:         address _owner,
73:         address _addressManager,
74:         uint64 _l1ChainId,
75:         uint64 _gasExcess
76:     )
```

- *Bridge.sol* ( [75-75](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L75-L75) ):

```solidity
/// @audit `_owner not checked`
/// @audit `_addressManager not checked`
75:     function init(address _owner, address _addressManager) external initializer {
```

- *AddressManager.sol* ( [30-30](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L30-L30) ):

```solidity
/// @audit `_owner not checked`
30:     function init(address _owner) external initializer {
```

- *SignalService.sol* ( [48-48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L48-L48) ):

```solidity
/// @audit `_owner not checked`
/// @audit `_addressManager not checked`
48:     function init(address _owner, address _addressManager) external initializer {
```

- *TimelockTokenPool.sol* ( [111-116](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L111-L116) ):

```solidity
/// @audit `_owner not checked`
111:     function init(
112:         address _owner,
113:         address _taikoToken,
114:         address _costToken,
115:         address _sharedVault
116:     )
```

- *ERC20Airdrop.sol* ( [27-34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L27-L34) ):

```solidity
/// @audit `_owner not checked`
/// @audit `_token not checked`
/// @audit `_vault not checked`
27:     function init(
28:         address _owner,
29:         uint64 _claimStart,
30:         uint64 _claimEnd,
31:         bytes32 _merkleRoot,
32:         address _token,
33:         address _vault
34:     )
```

- *ERC20Airdrop2.sol* ( [54-62](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L54-L62) ):

```solidity
/// @audit `_owner not checked`
/// @audit `_token not checked`
/// @audit `_vault not checked`
54:     function init(
55:         address _owner,
56:         uint64 _claimStart,
57:         uint64 _claimEnd,
58:         bytes32 _merkleRoot,
59:         address _token,
60:         address _vault,
61:         uint64 _withdrawalWindow
62:     )
```

- *ERC721Airdrop.sol* ( [25-32](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L25-L32) ):

```solidity
/// @audit `_owner not checked`
/// @audit `_token not checked`
/// @audit `_vault not checked`
25:     function init(
26:         address _owner,
27:         uint64 _claimStart,
28:         uint64 _claimEnd,
29:         bytes32 _merkleRoot,
30:         address _token,
31:         address _vault
32:     )
```

- *BaseVault.sol* ( [32-32](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L32-L32) ):

```solidity
/// @audit `_owner not checked`
/// @audit `_addressManager not checked`
32:     function init(address _owner, address _addressManager) external initializer {
```

- *BridgedERC1155.sol* ( [38-45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L38-L45) ):

```solidity
/// @audit `_owner not checked`
/// @audit `_addressManager not checked`
38:     function init(
39:         address _owner,
40:         address _addressManager,
41:         address _srcToken,
42:         uint256 _srcChainId,
43:         string memory _symbol,
44:         string memory _name
45:     )
```

- *BridgedERC20.sol* ( [52-60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L52-L60) ):

```solidity
/// @audit `_owner not checked`
/// @audit `_addressManager not checked`
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
/// @audit `_owner not checked`
/// @audit `_addressManager not checked`
31:     function init(
32:         address _owner,
33:         address _addressManager,
34:         address _srcToken,
35:         uint256 _srcChainId,
36:         string memory _symbol,
37:         string memory _name
38:     )
```

- *USDCAdapter.sol* ( [38-38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L38-L38) ):

```solidity
/// @audit `_owner not checked`
/// @audit `_addressManager not checked`
/// @audit `_usdc not checked`
38:     function init(address _owner, address _addressManager, IUSDC _usdc) external initializer {
```

- *GuardianVerifier.sol* ( [18-18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L18-L18) ):

```solidity
/// @audit `_owner not checked`
/// @audit `_addressManager not checked`
18:     function init(address _owner, address _addressManager) external initializer {
```

- *SgxVerifier.sol* ( [83-83](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L83-L83) ):

```solidity
/// @audit `_owner not checked`
/// @audit `_addressManager not checked`
83:     function init(address _owner, address _addressManager) external initializer {
```

</details>

### [L-09] Owner can renounce while system is paused

The contract owner or pauser with a role is not prevented from renouncing the role/ownership while the contract is paused, which would cause any user assets stored in the protocol, to be locked indefinitely.

There is 1 instance:

- *EssentialContract.sol* ( [69-75](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L69-L75) ):

```solidity
69:     function pause() public virtual whenNotPaused {
70:         __paused = _TRUE;
71:         emit Paused(msg.sender);
72:         // We call the authorize function here to avoid:
73:         // Warning (5740): Unreachable code.
74:         _authorizePause(msg.sender);
75:     }
```

### [L-10] Function `receive()`/`payable fallback()` does not authorize sender

Users may send ETH by mistake to these contracts. As there is no access control on these functions, the funds will be permanently lost.

There are 2 instances:

- *TaikoL1.sol* ( [34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L34) ):

```solidity
34:     receive() external payable {
```

- *Bridge.sol* ( [70](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L70) ):

```solidity
70:     receive() external payable { }
```

### [L-11] Revert on transfer to the zero address

It's good practice to revert a token transfer transaction if the recipient's address is the zero address. This can prevent unintentional transfers to the zero address due to accidental operations or programming errors. Many token contracts implement such a safeguard, such as [OpenZeppelin - ERC20](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/9e3f4d60c581010c4a3979480e07cc7752f124cc/contracts/token/ERC20/ERC20.sol#L232), [OpenZeppelin - ERC721](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/9e3f4d60c581010c4a3979480e07cc7752f124cc/contracts/token/ERC721/ERC721.sol#L142).

<details>
<summary>There are 8 instances (click to show):</summary>

- *AssignmentHook.sol* ( [102-102](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L102-L102) ):

```solidity
102:         tko.transferFrom(_blk.assignedProver, taikoL1Address, _blk.livenessBond);
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

- *ERC721Airdrop.sol* ( [60-60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L60-L60) ):

```solidity
60:             IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);
```

- *ERC20Vault.sol* ( [330-330](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L330-L330) ):

```solidity
330:             IERC20(token_).safeTransfer(_to, _amount);
```

- *ERC721Vault.sol* ( [171-171](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L171-L171) ):

```solidity
171:                 IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);
```

</details>

### [L-12] Array is `push()`ed but not `pop()`ed

Array entries are added but are never removed. Consider whether this should be the case, or whether there should be a maximum, or whether old entries should be removed. Cases where there are specific potential problems will be flagged separately under a different issue.

There is 1 instance:

- *Guardians.sol* ( [87-87](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L87-L87) ):

```solidity
87:             guardians.push(guardian);
```

### [L-13] State variables not limited to reasonable values

Consider adding appropriate minimum/maximum value checks to ensure that the following state variables can never be used to excessively harm users, including via griefing.

There are 2 instances:

- *MerkleClaimable.sol* ( [91-91](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L91-L91), [92-92](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L92-L92) ):

```solidity
91:         claimStart = _claimStart;

92:         claimEnd = _claimEnd;
```

### [L-14] Function `symbol()` is not a part of the ERC-20 standard

The `symbol()` function is not a part of the [ERC-20 standard](https://eips.ethereum.org/EIPS/eip-20), and was added later as an [optional extension](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC20/extensions/IERC20Metadata.sol). As such, some valid ERC20 tokens do not support this interface, so it is unsafe to blindly cast all tokens to this interface, and then call this function.

There are 3 instances:

- *ERC1155Vault.sol* ( [266-266](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L266-L266) ):

```solidity
266:                 try t.symbol() returns (string memory _symbol) {
```

- *ERC20Vault.sol* ( [369-369](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L369-L369) ):

```solidity
369:                 symbol: meta.symbol(),
```

- *ERC721Vault.sol* ( [206-206](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L206-L206) ):

```solidity
206:                     symbol: t.symbol(),
```

### [L-15] `tokenURI()` does not follow EIP-721

The [EIP-721](https://github.com/ethereum/EIPs/blob/7500ac4fc1bbdfaf684e7ef851f798f6b667b2fe/EIPS/eip-721.md?plain=1#L189-L193) states that `tokenURI()` should "Throws if `_tokenId` is not a valid NFT", which the code below does not do. If the NFT has not yet been minted, `tokenURI()` should revert.

There is 1 instance:

- *BridgedERC721.sol* ( [107-113](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L107-L113) ):

```solidity
107:     function tokenURI(uint256 _tokenId) public view virtual override returns (string memory) {
108:         return string(
109:             abi.encodePacked(
110:                 LibBridgedToken.buildURI(srcToken, srcChainId), Strings.toString(_tokenId)
111:             )
112:         );
113:     }
```

### [L-16] Consider implementing two-step procedure for updating protocol addresses

A copy-paste error or a typo may end up bricking protocol functionality, or sending tokens to an address with no known private key. Consider implementing a two-step procedure for updating protocol addresses, where the recipient is set as pending, and must 'accept' the assignment by making an affirmative call. A straight forward way of doing this would be to have the target contracts implement [EIP-165](https://eips.ethereum.org/EIPS/eip-165), and to have the 'set' functions ensure that the recipient is of the right interface type.

<details>
<summary>There are 4 instances (click to show):</summary>

- *AddressManager.sol* ( [38-51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L38-L51) ):

```solidity
38:     function setAddress(
39:         uint64 _chainId,
40:         bytes32 _name,
41:         address _newAddress
42:     )
43:         external
44:         virtual
45:         onlyOwner
46:     {
47:         address oldAddress = __addresses[_chainId][_name];
48:         if (_newAddress == oldAddress) revert AM_INVALID_PARAMS();
49:         __addresses[_chainId][_name] = _newAddress;
50:         emit AddressSet(_chainId, _name, _newAddress, oldAddress);
51:     }
```

- *BridgedERC20.sol* ( [80-82](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L80-L82) ):

```solidity
80:     function setSnapshoter(address _snapshooter) external onlyOwner {
81:         snapshooter = _snapshooter;
82:     }
```

- *BridgedERC20Base.sol* ( [36-52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L36-L52) ):

```solidity
36:     function changeMigrationStatus(
37:         address _migratingAddress,
38:         bool _migratingInbound
39:     )
40:         external
41:         nonReentrant
42:         whenNotPaused
43:         onlyFromOwnerOrNamed("erc20_vault")
44:     {
45:         if (_migratingAddress == migratingAddress && _migratingInbound == migratingInbound) {
46:             revert BB_INVALID_PARAMS();
47:         }
48: 
49:         migratingAddress = _migratingAddress;
50:         migratingInbound = _migratingInbound;
51:         emit MigrationStatusChanged(_migratingAddress, _migratingInbound);
52:     }
```

- *ERC20Vault.sol* ( [148-200](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L148-L200) ):

```solidity
148:     function changeBridgedToken(
149:         CanonicalERC20 calldata _ctoken,
150:         address _btokenNew
151:     )
152:         external
153:         nonReentrant
154:         whenNotPaused
155:         onlyOwner
156:         returns (address btokenOld_)
157:     {
158:         if (_btokenNew == address(0) || bridgedToCanonical[_btokenNew].addr != address(0)) {
159:             revert VAULT_INVALID_NEW_BTOKEN();
160:         }
161: 
162:         if (btokenBlacklist[_btokenNew]) revert VAULT_BTOKEN_BLACKLISTED();
163: 
164:         if (IBridgedERC20(_btokenNew).owner() != owner()) {
165:             revert VAULT_NOT_SAME_OWNER();
166:         }
167: 
168:         btokenOld_ = canonicalToBridged[_ctoken.chainId][_ctoken.addr];
169: 
170:         if (btokenOld_ != address(0)) {
171:             CanonicalERC20 memory ctoken = bridgedToCanonical[btokenOld_];
172: 
...... OMITTED ......
176:                     || keccak256(bytes(ctoken.symbol)) != keccak256(bytes(_ctoken.symbol))
177:                     || keccak256(bytes(ctoken.name)) != keccak256(bytes(_ctoken.name))
178:             ) revert VAULT_CTOKEN_MISMATCH();
179: 
180:             delete bridgedToCanonical[_btokenNew];
181:             btokenBlacklist[btokenOld_] = true;
182: 
183:             // Start the migration
184:             IBridgedERC20(btokenOld_).changeMigrationStatus(_btokenNew, false);
185:             IBridgedERC20(_btokenNew).changeMigrationStatus(btokenOld_, true);
186:         }
187: 
188:         bridgedToCanonical[_btokenNew] = _ctoken;
189:         canonicalToBridged[_ctoken.chainId][_ctoken.addr] = _btokenNew;
190: 
191:         emit BridgedTokenChanged({
192:             srcChainId: _ctoken.chainId,
193:             ctoken: _ctoken.addr,
194:             btokenOld: btokenOld_,
195:             btokenNew: _btokenNew,
196:             ctokenSymbol: _ctoken.symbol,
197:             ctokenName: _ctoken.name,
198:             ctokenDecimal: _ctoken.decimals
199:         });
200:     }
```

</details>

### [L-17] Unsafe conversion from unsigned to signed values

The `int` type in Solidity uses the [two's complement system](https://en.wikipedia.org/wiki/Two%27s_complement), so it is possible to accidentally overflow a very large `uint` to an `int`, even if they share the same number of bytes (e.g. a `uint256 number > type(uint128).max` will overflow a `int256` cast).

Consider using the [SafeCast](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/utils/math/SafeCast.sol) library to prevent any overflows.

There are 5 instances:

- *Lib1559Math.sol* ( [45-45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/Lib1559Math.sol#L45-L45) ):

```solidity
/// @audit uint -> int
45:         return uint256(LibFixedPointMath.exp(int256(input)));
```

- *BytesUtils.sol* ( [97-97](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L97-L97), [104-104](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L104-L104), [104-104](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L104-L104) ):

```solidity
/// @audit uint -> int
97:                     return int256(diff);

/// @audit uint -> int
104:         return int256(len) - int256(otherlen);

/// @audit uint -> int
104:         return int256(len) - int256(otherlen);
```

- *LibFixedPointMath.sol* ( [76-79](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L76-L79) ):

```solidity
/// @audit uint -> int
76:             r = int256(
77:                 (uint256(r) * 3_822_833_074_963_236_453_042_738_258_902_158_003_155_416_615_667)
78:                     >> uint256(195 - k)
79:             );
```

### [L-18] Downcasting other types to an address can cause collisions

Downcasting other types to an address will truncates the upper bytes, which means that multiple values can be mapped to an address, i.e. address collisions can occur.

There are 3 instances:

- *LibDepositing.sol* ( [89-89](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L89-L89) ):

```solidity
89:                     recipient: address(uint160(data >> 96)),
```

- *SgxVerifier.sol* ( [133-133](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L133-L133), [155-155](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L155-L155) ):

```solidity
133:         _address[0] = address(bytes20(_attestation.localEnclaveReport.reportData));

155:         address newInstance = address(bytes20(Bytes.slice(_proof.data, 4, 20)));
```

### [L-19] Upgradeable contract not initialized

Upgradeable contracts are initialized via an initializer function rather than by a constructor. Leaving such a contract uninitialized may lead to it being taken over by a malicious user.

There are 3 instances:

- *BaseVault.sol* ( [12-16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L12-L16) ):

```solidity
/// @audit __IERC165_init()
12: abstract contract BaseVault is
13:     EssentialContract,
14:     IRecallableSender,
15:     IMessageInvocable,
16:     IERC165Upgradeable
```

- *BridgedERC1155.sol* ( [14-14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L14-L14) ):

```solidity
/// @audit __IERC1155MetadataURI_init()
14: contract BridgedERC1155 is EssentialContract, IERC1155MetadataURIUpgradeable, ERC1155Upgradeable {
```

- *BridgedERC20.sol* ( [15-19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L15-L19) ):

```solidity
/// @audit __IERC20Metadata_init()
15: contract BridgedERC20 is
16:     BridgedERC20Base,
17:     IERC20MetadataUpgradeable,
18:     ERC20SnapshotUpgradeable,
19:     ERC20VotesUpgradeable
```

### [L-20] Vulnerable versions of packages are being used

This project is using specific package versions which are vulnerable to the specific CVEs listed below. Consider switching to more recent versions of these packages that don't have these vulnerabilities.
- [CVE-2023-40014](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-40014) - **MEDIUM** - (`@openzeppelin/contracts >=4.0.0 <4.9.3`): OpenZeppelin Contracts is a library for secure smart contract development. Starting in version 4.0.0 and prior to version 4.9.3, contracts using `ERC2771Context` along with a custom trusted forwarder may see `_msgSender` return `address(0)` in calls that originate from the forwarder with calldata shorter than 20 bytes. This combination of circumstances does not appear to be common, in particular it is not the case for `MinimalForwarder` from OpenZeppelin Contracts, or any deployed forwarder the team is aware of, given that the signer address is appended to all calls that originate from these forwarders. The problem has been patched in v4.9.3.

- [CVE-2023-40014](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-40014) - **MEDIUM** - (`@openzeppelin/contracts-upgradeable >=4.0.0 <4.9.3`): OpenZeppelin Contracts is a library for secure smart contract development. Starting in version 4.0.0 and prior to version 4.9.3, contracts using `ERC2771Context` along with a custom trusted forwarder may see `_msgSender` return `address(0)` in calls that originate from the forwarder with calldata shorter than 20 bytes. This combination of circumstances does not appear to be common, in particular it is not the case for `MinimalForwarder` from OpenZeppelin Contracts, or any deployed forwarder the team is aware of, given that the signer address is appended to all calls that originate from these forwarders. The problem has been patched in v4.9.3.

- [CVE-2023-34459](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-34459) - **MEDIUM** - (`@openzeppelin/contracts >=4.7.0 <4.9.2`): OpenZeppelin Contracts is a library for smart contract development. Starting in version 4.7.0 and prior to version 4.9.2, when the `verifyMultiProof`, `verifyMultiProofCalldata`, `procesprocessMultiProof`, or `processMultiProofCalldat` functions are in use, it is possible to construct merkle trees that allow forging a valid multiproof for an arbitrary set of leaves. A contract may be vulnerable if it uses multiproofs for verification and the merkle tree that is processed includes a node with value 0 at depth 1 (just under the root). This could happen inadvertedly for balanced trees with 3 leaves or less, if the leaves are not hashed. This could happen deliberately if a malicious tree builder includes such a node in the tree. A contract is not vulnerable if it uses single-leaf proving (`verify`, `verifyCalldata`, `processProof`, or `processProofCalldata`), or if it uses multiproofs with a known tree that has hashed leaves. Standard merkle trees produced or validated with the @openzeppelin/merkle-tree library are safe. The problem has been patched in version 4.9.2. Some workarounds are available. For those using multiproofs: When constructing merkle trees hash the leaves and do not insert empty nodes in your trees. Using the @openzeppelin/merkle-tree package eliminates this issue. Do not accept user-provided merkle roots without reconstructing at least the first level of the tree. Verify the merkle tree structure by reconstructing it from the leaves.

- [CVE-2023-34459](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-34459) - **MEDIUM** - (`@openzeppelin/contracts-upgradeable >=4.7.0 <4.9.2`): OpenZeppelin Contracts is a library for smart contract development. Starting in version 4.7.0 and prior to version 4.9.2, when the `verifyMultiProof`, `verifyMultiProofCalldata`, `procesprocessMultiProof`, or `processMultiProofCalldat` functions are in use, it is possible to construct merkle trees that allow forging a valid multiproof for an arbitrary set of leaves. A contract may be vulnerable if it uses multiproofs for verification and the merkle tree that is processed includes a node with value 0 at depth 1 (just under the root). This could happen inadvertedly for balanced trees with 3 leaves or less, if the leaves are not hashed. This could happen deliberately if a malicious tree builder includes such a node in the tree. A contract is not vulnerable if it uses single-leaf proving (`verify`, `verifyCalldata`, `processProof`, or `processProofCalldata`), or if it uses multiproofs with a known tree that has hashed leaves. Standard merkle trees produced or validated with the @openzeppelin/merkle-tree library are safe. The problem has been patched in version 4.9.2. Some workarounds are available. For those using multiproofs: When constructing merkle trees hash the leaves and do not insert empty nodes in your trees. Using the @openzeppelin/merkle-tree package eliminates this issue. Do not accept user-provided merkle roots without reconstructing at least the first level of the tree. Verify the merkle tree structure by reconstructing it from the leaves.

- [CVE-2023-30541](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-30541) - **MEDIUM** - (`@openzeppelin/contracts >=3.2.0 <4.8.3`): OpenZeppelin Contracts is a library for secure smart contract development. A function in the implementation contract may be inaccessible if its selector clashes with one of the proxy's own selectors. Specifically, if the clashing function has a different signature with incompatible ABI encoding, the proxy could revert while attempting to decode the arguments from calldata. The probability of an accidental clash is negligible, but one could be caused deliberately and could cause a reduction in availability. The issue has been fixed in version 4.8.3. As a workaround if a function appears to be inaccessible for this reason, it may be possible to craft the calldata such that ABI decoding does not fail at the proxy and the function is properly proxied through.

- [CVE-2023-30541](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-30541) - **MEDIUM** - (`@openzeppelin/contracts-upgradeable >=3.2.0 <4.8.3`): OpenZeppelin Contracts is a library for secure smart contract development. A function in the implementation contract may be inaccessible if its selector clashes with one of the proxy's own selectors. Specifically, if the clashing function has a different signature with incompatible ABI encoding, the proxy could revert while attempting to decode the arguments from calldata. The probability of an accidental clash is negligible, but one could be caused deliberately and could cause a reduction in availability. The issue has been fixed in version 4.8.3. As a workaround if a function appears to be inaccessible for this reason, it may be possible to craft the calldata such that ABI decoding does not fail at the proxy and the function is properly proxied through.

There are 6 instances:

- Global finding

### [L-21] Inappropriate storage gap size

Each upgradeable contract should include a storage gap(`__gap`). The size of the `__gap` array is calculated so that the amount of storage used by a contract always adds up to the same number (a fixed number of [**50** slots](https://docs.openzeppelin.com/upgrades-plugins/1.x/writing-upgradeable#storage-gaps) is recommended). Consistency of this value improves the maintainability of the contract and reduces the likelihood of incompatibilities in future upgrades.

There is 1 instance:

- *Bridge.sol* ( [48-48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L48-L48) ):

```solidity
/// @audit Should be 44
48:     uint256[43] private __gap;
```

### [L-22] Constructor / initialization function lacks parameter validation

Constructors and initialization functions play a critical role in contracts by setting important initial states when the contract is first deployed before the system starts. The parameters passed to the constructor and initialization functions directly affect the behavior of the contract / protocol. If incorrect parameters are provided, the system may fail to run, behave abnormally, be unstable, or lack security. Therefore, it's crucial to carefully check each parameter in the constructor and initialization functions. If an exception is found, the transaction should be rolled back.

<details>
<summary>There are 19 instances (click to show):</summary>

- *TaikoL1.sol* ( [42-49](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L42-L49) ):

```solidity
/// @audit `_genesisBlockHash`
42:     function init(
43:         address _owner,
44:         address _addressManager,
45:         bytes32 _genesisBlockHash
46:     )
47:         external
48:         initializer
49:     {
```

- *TaikoToken.sol* ( [25-33](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L25-L33) ):

```solidity
/// @audit `_name`
/// @audit `_symbol`
25:     function init(
26:         address _owner,
27:         string calldata _name,
28:         string calldata _symbol,
29:         address _recipient
30:     )
31:         public
32:         initializer
33:     {
```

- *TaikoTimelockController.sol* ( [15-15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L15-L15) ):

```solidity
/// @audit `_minDelay`
15:     function init(address _owner, uint256 _minDelay) external initializer {
```

- *TaikoL2.sol* ( [71-79](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L71-L79) ):

```solidity
/// @audit `_l1ChainId`
/// @audit `_gasExcess`
71:     function init(
72:         address _owner,
73:         address _addressManager,
74:         uint64 _l1ChainId,
75:         uint64 _gasExcess
76:     )
77:         external
78:         initializer
79:     {
```

- *ERC20Airdrop.sol* ( [27-37](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L27-L37) ):

```solidity
/// @audit `_claimStart`
/// @audit `_claimEnd`
/// @audit `_merkleRoot`
27:     function init(
28:         address _owner,
29:         uint64 _claimStart,
30:         uint64 _claimEnd,
31:         bytes32 _merkleRoot,
32:         address _token,
33:         address _vault
34:     )
35:         external
36:         initializer
37:     {
```

- *ERC20Airdrop2.sol* ( [54-65](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L54-L65) ):

```solidity
/// @audit `_claimStart`
/// @audit `_claimEnd`
/// @audit `_merkleRoot`
/// @audit `_withdrawalWindow`
54:     function init(
55:         address _owner,
56:         uint64 _claimStart,
57:         uint64 _claimEnd,
58:         bytes32 _merkleRoot,
59:         address _token,
60:         address _vault,
61:         uint64 _withdrawalWindow
62:     )
63:         external
64:         initializer
65:     {
```

- *ERC721Airdrop.sol* ( [25-35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L25-L35) ):

```solidity
/// @audit `_claimStart`
/// @audit `_claimEnd`
/// @audit `_merkleRoot`
25:     function init(
26:         address _owner,
27:         uint64 _claimStart,
28:         uint64 _claimEnd,
29:         bytes32 _merkleRoot,
30:         address _token,
31:         address _vault
32:     )
33:         external
34:         initializer
35:     {
```

- *BridgedERC1155.sol* ( [38-48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L38-L48) ):

```solidity
/// @audit `_symbol`
/// @audit `_name`
38:     function init(
39:         address _owner,
40:         address _addressManager,
41:         address _srcToken,
42:         uint256 _srcChainId,
43:         string memory _symbol,
44:         string memory _name
45:     )
46:         external
47:         initializer
48:     {
```

- *BridgedERC20.sol* ( [52-63](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L52-L63) ):

```solidity
/// @audit `_decimals`
52:     function init(
53:         address _owner,
54:         address _addressManager,
55:         address _srcToken,
56:         uint256 _srcChainId,
57:         uint8 _decimals,
58:         string memory _symbol,
59:         string memory _name
60:     )
61:         external
62:         initializer
63:     {
```

</details>

### [L-23] Missing checks for `address(0)` when setting address state variables

Consider adding a zero address check when setting address state variables.

There are 2 instances:

- *AddressResolver.sol* ( [62-62](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L62-L62) ):

```solidity
62:         addressManager = _addressManager;
```

- *BridgedERC20.sol* ( [81-81](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L81-L81) ):

```solidity
81:         snapshooter = _snapshooter;
```

### [L-24] Unsafe solidity low-level call can cause gas grief attack

Using the low-level calls of a solidity address can leave the contract open to gas grief attacks. These attacks occur when the called contract returns a large amount of data.
So when calling an external contract, it is necessary to check the length of the return data before reading/copying it (using `returndatasize()`).

There are 3 instances:

- *SigVerifyLib.sol* ( [137-137](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L137-L137) ):

```solidity
137:         (bool success, bytes memory ret) = ES256VERIFIER.staticcall(args);
```

- *Bridge.sol* ( [591-591](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L591-L591) ):

```solidity
591:         (success_,) = _signalService.staticcall(data);
```

- *Lib4844.sol* ( [43-45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/Lib4844.sol#L43-L45) ):

```solidity
43:         (bool ok, bytes memory ret) = POINT_EVALUATION_PRECOMPILE_ADDRESS.staticcall(
44:             abi.encodePacked(_blobHash, _x, _y, _commitment, _pointProof)
45:         );
```

### [L-25] Minting in a loop may lead to a DOS

The signature used seems to require all the minting operations to be done at once. If there are a lot of them, there may be too many to mint in one block.

There is 1 instance:

- *ERC721Vault.sol* ( [175-177](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L175-L177) ):

```solidity
/// @audit mint by mint()
175:             for (uint256 i; i < _tokenIds.length; ++i) {
176:                 BridgedERC721(token_).mint(_to, _tokenIds[i]);
177:             }
```

### [L-26] Owner can renounce Ownership

Each of the following contracts implements or inherits the `renounceOwnership()` function. This can represent a certain risk if the ownership is renounced for any other reason than by design. Renouncing ownership will leave the contract without an owner, thereby removing any functionality that is only available to the owner.

<details>
<summary>There are 34 instances (click to show):</summary>

- *TaikoL1.sol* ( [22-23](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L22-L23) ):

```solidity
22: contract TaikoL1 is EssentialContract, ITaikoL1, TaikoEvents, TaikoErrors {
23:     /// @notice The TaikoL1 state.
```

- *TaikoToken.sol* ( [15-15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L15-L15) ):

```solidity
15: contract TaikoToken is EssentialContract, ERC20SnapshotUpgradeable, ERC20VotesUpgradeable {
```

- *TaikoGovernor.sol* ( [16-22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L16-L22) ):

```solidity
16: contract TaikoGovernor is
17:     EssentialContract,
18:     GovernorCompatibilityBravoUpgradeable,
19:     GovernorVotesUpgradeable,
20:     GovernorVotesQuorumFractionUpgradeable,
21:     GovernorTimelockControlUpgradeable
22: {
```

- *TaikoTimelockController.sol* ( [9-9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L9-L9) ):

```solidity
9: contract TaikoTimelockController is EssentialContract, TimelockControllerUpgradeable {
```

- *AssignmentHook.sol* ( [14-14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L14-L14) ):

```solidity
14: contract AssignmentHook is EssentialContract, IHook {
```

- *GuardianProver.sol* ( [10-10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/GuardianProver.sol#L10-L10) ):

```solidity
10: contract GuardianProver is Guardians {
```

- *Guardians.sol* ( [9-10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L9-L10) ):

```solidity
9: abstract contract Guardians is EssentialContract {
10:     /// @notice The minimum number of guardians
```

- *DevnetTierProvider.sol* ( [10-10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L10-L10) ):

```solidity
10: contract DevnetTierProvider is EssentialContract, ITierProvider {
```

- *MainnetTierProvider.sol* ( [10-10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L10-L10) ):

```solidity
10: contract MainnetTierProvider is EssentialContract, ITierProvider {
```

- *TestnetTierProvider.sol* ( [10-10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L10-L10) ):

```solidity
10: contract TestnetTierProvider is EssentialContract, ITierProvider {
```

- *CrossChainOwned.sol* ( [14-15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L14-L15) ):

```solidity
14: abstract contract CrossChainOwned is EssentialContract, IMessageInvocable {
15:     /// @notice The owner chain ID.
```

- *TaikoL2.sol* ( [21-21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L21-L21) ):

```solidity
21: contract TaikoL2 is CrossChainOwned {
```

- *TaikoL2EIP1559Configurable.sol* ( [9-10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L9-L10) ):

```solidity
9: contract TaikoL2EIP1559Configurable is TaikoL2 {
10:     /// @notice EIP-1559 configuration.
```

- *Bridge.sol* ( [16-16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L16-L16) ):

```solidity
16: contract Bridge is EssentialContract, IBridge {
```

- *AddressManager.sol* ( [10-11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L10-L11) ):

```solidity
10: contract AddressManager is EssentialContract, IAddressManager {
11:     /// @dev Mapping of chainId to mapping of name to address.
```

- *EssentialContract.sol* ( [10-10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L10-L10) ):

```solidity
10: abstract contract EssentialContract is UUPSUpgradeable, Ownable2StepUpgradeable, AddressResolver {
```

- *SignalService.sol* ( [14-16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L14-L16) ):

```solidity
14: contract SignalService is EssentialContract, ISignalService {
15:     /// @notice Mapping to store the top blockId.
16:     /// @dev Slot 1.
```

- *TimelockTokenPool.sol* ( [25-25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L25-L25) ):

```solidity
25: contract TimelockTokenPool is EssentialContract {
```

- *ERC20Airdrop.sol* ( [11-12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L11-L12) ):

```solidity
11: contract ERC20Airdrop is MerkleClaimable {
12:     /// @notice The address of the token contract.
```

- *ERC20Airdrop2.sol* ( [12-12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L12-L12) ):

```solidity
12: contract ERC20Airdrop2 is MerkleClaimable {
```

- *ERC721Airdrop.sol* ( [9-10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L9-L10) ):

```solidity
9: contract ERC721Airdrop is MerkleClaimable {
10:     /// @notice The address of the token contract.
```

- *MerkleClaimable.sol* ( [10-11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L10-L11) ):

```solidity
10: abstract contract MerkleClaimable is EssentialContract {
11:     /// @notice Mapping of hashes and their claim status
```

- *BaseNFTVault.sol* ( [9-10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L9-L10) ):

```solidity
9: abstract contract BaseNFTVault is BaseVault {
10:     // Struct representing the canonical NFT on another chain.
```

- *BaseVault.sol* ( [12-17](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L12-L17) ):

```solidity
12: abstract contract BaseVault is
13:     EssentialContract,
14:     IRecallableSender,
15:     IMessageInvocable,
16:     IERC165Upgradeable
17: {
```

- *BridgedERC1155.sol* ( [14-15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L14-L15) ):

```solidity
14: contract BridgedERC1155 is EssentialContract, IERC1155MetadataURIUpgradeable, ERC1155Upgradeable {
15:     /// @notice Address of the source token contract.
```

- *BridgedERC20.sol* ( [15-21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L15-L21) ):

```solidity
15: contract BridgedERC20 is
16:     BridgedERC20Base,
17:     IERC20MetadataUpgradeable,
18:     ERC20SnapshotUpgradeable,
19:     ERC20VotesUpgradeable
20: {
21:     /// @dev Slot 1.
```

- *BridgedERC20Base.sol* ( [9-10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L9-L10) ):

```solidity
9: abstract contract BridgedERC20Base is EssentialContract, IBridgedERC20 {
10:     /// @notice The address of the contract to migrate tokens to or from.
```

- *BridgedERC721.sol* ( [12-13](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L12-L13) ):

```solidity
12: contract BridgedERC721 is EssentialContract, ERC721Upgradeable {
13:     /// @notice Address of the source token contract.
```

- *ERC1155Vault.sol* ( [29-29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L29-L29) ):

```solidity
29: contract ERC1155Vault is BaseNFTVault, ERC1155ReceiverUpgradeable {
```

- *ERC20Vault.sol* ( [18-18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L18-L18) ):

```solidity
18: contract ERC20Vault is BaseVault {
```

- *ERC721Vault.sol* ( [16-16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L16-L16) ):

```solidity
16: contract ERC721Vault is BaseNFTVault, IERC721Receiver {
```

- *USDCAdapter.sol* ( [28-30](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L28-L30) ):

```solidity
28: contract USDCAdapter is BridgedERC20Base {
29:     /// @notice The USDC instance.
30:     /// @dev Slot 1.
```

- *GuardianVerifier.sol* ( [10-10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L10-L10) ):

```solidity
10: contract GuardianVerifier is EssentialContract, IVerifier {
```

- *SgxVerifier.sol* ( [19-23](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L19-L23) ):

```solidity
19: contract SgxVerifier is EssentialContract, IVerifier {
20:     /// @dev Each public-private key pair (Ethereum address) is generated within
21:     /// the SGX program when it boots up. The off-chain remote attestation
22:     /// ensures the validity of the program hash and has the capability of
23:     /// bootstrapping the network with trustworthy instances.
```

</details>

### [L-27] Functions calling contracts/addresses with transfer hooks should be protected by reentrancy guard

Even if the function follows the best practice of check-effects-interaction, not using a reentrancy guard when there may be transfer hooks opens the users of this protocol up to [read-only reentrancy vulnerability](https://chainsecurity.com/curve-lp-oracle-manipulation-post-mortem/) with no way to protect them except by block-listing the entire protocol.

<details>
<summary>There are 15 instances (click to show):</summary>

- *LibProving.sol* ( [196-196](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L196-L196), [242-242](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L242-L242), [367-367](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L367-L367), [371-371](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L371-L371), [382-382](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L382-L382), [384-384](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L384-L384) ):

```solidity
196:                 tko.transfer(blk.assignedProver, blk.livenessBond);

242:                 tko.transferFrom(msg.sender, address(this), tier.contestBond);

367:                 _tko.transfer(_ts.prover, _ts.validityBond + reward);

371:                 _tko.transfer(_ts.contester, _ts.contestBond + reward);

382:                 _tko.transfer(msg.sender, reward - _tier.validityBond);

384:                 _tko.transferFrom(msg.sender, address(this), _tier.validityBond - reward);
```

- *LibVerifying.sol* ( [189-189](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L189-L189) ):

```solidity
189:                 tko.transfer(ts.prover, bondToReturn);
```

- *TimelockTokenPool.sol* ( [219-219](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L219-L219), [220-220](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L220-L220) ):

```solidity
219:         IERC20(taikoToken).transferFrom(sharedVault, _to, amountToWithdraw);

220:         IERC20(costToken).safeTransferFrom(_recipient, sharedVault, costToWithdraw);
```

- *ERC20Airdrop2.sol* ( [91-91](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L91-L91) ):

```solidity
91:         IERC20(token).transferFrom(vault, user, amount);
```

- *ERC1155Vault.sol* ( [270-276](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L270-L276) ):

```solidity
270:                     IERC1155(_op.token).safeTransferFrom({
271:                         from: msg.sender,
272:                         to: address(this),
273:                         id: _op.tokenIds[i],
274:                         amount: _op.amounts[i],
275:                         data: ""
276:                     });
```

- *ERC20Vault.sol* ( [330-330](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L330-L330), [379-379](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L379-L379) ):

```solidity
330:             IERC20(token_).safeTransfer(_to, _amount);

379:             t.safeTransferFrom({ from: msg.sender, to: address(this), value: _amount });
```

- *ERC721Vault.sol* ( [171-171](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L171-L171), [211-211](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L211-L211) ):

```solidity
171:                 IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);

211:                     t.safeTransferFrom(_user, address(this), _op.tokenIds[i]);
```

</details>

### [L-28] Critical functions should be controlled by time locks

It is a good practice to give time for users to react and adjust to critical changes. A timelock provides more guarantees and reduces the level of trust required, thus decreasing risk for users. It also indicates that the project is legitimate (less risk of a malicious owner making a sandwich attack on a user).

<details>
<summary>There are 19 instances (click to show):</summary>

- *TaikoL1.sol* ( [111-111](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L111-L111) ):

```solidity
111:     function pauseProving(bool _pause) external {
```

- *Guardians.sol* ( [53-60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L53-L60) ):

```solidity
53:     function setGuardians(
54:         address[] memory _newGuardians,
55:         uint8 _minGuardians
56:     )
57:         external
58:         onlyOwner
59:         nonReentrant
60:     {
```

- *TaikoL2EIP1559Configurable.sol* ( [25-32](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L25-L32) ):

```solidity
25:     function setConfigAndExcess(
26:         Config memory _newConfig,
27:         uint64 _newGasExcess
28:     )
29:         external
30:         virtual
31:         onlyOwner
32:     {
```

- *AutomataDcapV3Attestation.sol* ( [65-65](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L65-L65), [69-69](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L69-L69), [73-79](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L73-L79), [88-94](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L88-L94), [103-109](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L103-L109), [114-117](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L114-L117), [122-122](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L122-L122) ):

```solidity
65:     function setMrSigner(bytes32 _mrSigner, bool _trusted) external onlyOwner {

69:     function setMrEnclave(bytes32 _mrEnclave, bool _trusted) external onlyOwner {

73:     function addRevokedCertSerialNum(
74:         uint256 index,
75:         bytes[] calldata serialNumBatch
76:     )
77:         external
78:         onlyOwner
79:     {

88:     function removeRevokedCertSerialNum(
89:         uint256 index,
90:         bytes[] calldata serialNumBatch
91:     )
92:         external
93:         onlyOwner
94:     {

103:     function configureTcbInfoJson(
104:         string calldata fmspc,
105:         TCBInfoStruct.TCBInfo calldata tcbInfoInput
106:     )
107:         public
108:         onlyOwner
109:     {

114:     function configureQeIdentityJson(EnclaveIdStruct.EnclaveId calldata qeIdentityInput)
115:         external
116:         onlyOwner
117:     {

122:     function toggleLocalReportCheck() external onlyOwner {
```

- *AddressManager.sol* ( [38-46](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L38-L46) ):

```solidity
38:     function setAddress(
39:         uint64 _chainId,
40:         bytes32 _name,
41:         address _newAddress
42:     )
43:         external
44:         virtual
45:         onlyOwner
46:     {
```

- *EssentialContract.sol* ( [114-114](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L114-L114), [116-116](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L116-L116) ):

```solidity
114:     function _authorizeUpgrade(address) internal virtual override onlyOwner { }

116:     function _authorizePause(address) internal virtual onlyOwner { }
```

- *MerkleClaimable.sol* ( [45-52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L45-L52) ):

```solidity
45:     function setConfig(
46:         uint64 _claimStart,
47:         uint64 _claimEnd,
48:         bytes32 _merkleRoot
49:     )
50:         external
51:         onlyOwner
52:     {
```

- *BridgedERC20.sol* ( [80-80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L80-L80) ):

```solidity
80:     function setSnapshoter(address _snapshooter) external onlyOwner {
```

- *BridgedERC20Base.sol* ( [36-44](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L36-L44) ):

```solidity
36:     function changeMigrationStatus(
37:         address _migratingAddress,
38:         bool _migratingInbound
39:     )
40:         external
41:         nonReentrant
42:         whenNotPaused
43:         onlyFromOwnerOrNamed("erc20_vault")
44:     {
```

- *ERC20Vault.sol* ( [148-156](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L148-L156) ):

```solidity
148:     function changeBridgedToken(
149:         CanonicalERC20 calldata _ctoken,
150:         address _btokenNew
151:     )
152:         external
153:         nonReentrant
154:         whenNotPaused
155:         onlyOwner
156:         returns (address btokenOld_)
```

- *SgxVerifier.sol* ( [90-93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L90-L93), [100-103](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L100-L103) ):

```solidity
90:     function addInstances(address[] calldata _instances)
91:         external
92:         onlyOwner
93:         returns (uint256[] memory)

100:     function deleteInstances(uint256[] calldata _ids)
101:         external
102:         onlyFromOwnerOrNamed("rollup_watchdog")
103:     {
```

</details>

### [L-29] External function calls within loops

Calling external functions within loops can easily result in insufficient gas. This greatly increases the likelihood of transaction failures, DOS attacks, and other unexpected actions. It is recommended to limit the number of loops within loops that call external functions, and to limit the gas line for each external call.

<details>
<summary>There are 9 instances (click to show):</summary>

- *LibProposing.sol* ( [253-255](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L253-L255) ):

```solidity
/// @audit Calling `onBlockProposed()` within `for` loop
253:                 IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }(
254:                     blk, meta_, params.hookCalls[i].data
255:                 );
```

- *LibVerifying.sol* ( [189-189](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L189-L189) ):

```solidity
/// @audit Calling `transfer()` within `while` loop
189:                 tko.transfer(ts.prover, bondToReturn);
```

- *ERC721Airdrop.sol* ( [60-60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L60-L60) ):

```solidity
/// @audit Calling `safeTransferFrom()` within `for` loop
60:             IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);
```

- *ERC1155Vault.sol* ( [252-252](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L252-L252), [270-276](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L270-L276) ):

```solidity
/// @audit Calling `burn()` within `for` loop
252:                     BridgedERC1155(_op.token).burn(_user, _op.tokenIds[i], _op.amounts[i]);

/// @audit Calling `safeTransferFrom()` within `for` loop
270:                     IERC1155(_op.token).safeTransferFrom({
271:                         from: msg.sender,
272:                         to: address(this),
273:                         id: _op.tokenIds[i],
274:                         amount: _op.amounts[i],
275:                         data: ""
276:                     });
```

- *ERC721Vault.sol* ( [171-171](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L171-L171), [176-176](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L176-L176), [198-198](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L198-L198), [211-211](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L211-L211) ):

```solidity
/// @audit Calling `safeTransferFrom()` within `for` loop
171:                 IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);

/// @audit Calling `mint()` within `for` loop
176:                 BridgedERC721(token_).mint(_to, _tokenIds[i]);

/// @audit Calling `burn()` within `for` loop
198:                     BridgedERC721(_op.token).burn(_user, _op.tokenIds[i]);

/// @audit Calling `safeTransferFrom()` within `for` loop
211:                     t.safeTransferFrom(_user, address(this), _op.tokenIds[i]);
```

</details>

### [L-30] Tokens may be minted to the zero address

Neither the listed functions, nor `_mint()` prevent minting to `address(0x0)`

<details>
<summary>There are 12 instances (click to show):</summary>

- *TaikoToken.sol* ( [41-41](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L41-L41), [105-111](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L105-L111) ):

```solidity
41:         _mint(_recipient, 1_000_000_000 ether);

105:     function _mint(
106:         address _to,
107:         uint256 _amount
108:     )
109:         internal
110:         override(ERC20Upgradeable, ERC20VotesUpgradeable)
111:     {
```

- *BridgedERC1155.sol* ( [66-75](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L66-L75), [83-92](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L83-L92) ):

```solidity
66:     function mint(
67:         address _to,
68:         uint256 _tokenId,
69:         uint256 _amount
70:     )
71:         public
72:         nonReentrant
73:         whenNotPaused
74:         onlyFromNamed("erc1155_vault")
75:     {

83:     function mintBatch(
84:         address _to,
85:         uint256[] memory _tokenIds,
86:         uint256[] memory _amounts
87:     )
88:         public
89:         nonReentrant
90:         whenNotPaused
91:         onlyFromNamed("erc1155_vault")
92:     {
```

- *BridgedERC20.sol* ( [129-129](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L129-L129), [163-169](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L163-L169) ):

```solidity
129:     function _mintToken(address _account, uint256 _amount) internal override {

163:     function _mint(
164:         address _to,
165:         uint256 _amount
166:     )
167:         internal
168:         override(ERC20Upgradeable, ERC20VotesUpgradeable)
169:     {
```

- *BridgedERC20Base.sol* ( [57-57](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L57-L57) ):

```solidity
57:     function mint(address _account, uint256 _amount) public nonReentrant whenNotPaused {
```

- *BridgedERC721.sol* ( [54-62](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L54-L62) ):

```solidity
54:     function mint(
55:         address _account,
56:         uint256 _tokenId
57:     )
58:         public
59:         nonReentrant
60:         whenNotPaused
61:         onlyFromNamed("erc721_vault")
62:     {
```

- *ERC1155Vault.sol* ( [230-230](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L230-L230) ):

```solidity
230:             BridgedERC1155(token).mintBatch(to, tokenIds, amounts);
```

- *ERC20Vault.sol* ( [333-333](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L333-L333) ):

```solidity
333:             IBridgedERC20(token_).mint(_to, _amount);
```

- *ERC721Vault.sol* ( [176-176](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L176-L176) ):

```solidity
176:                 BridgedERC721(token_).mint(_to, _tokenIds[i]);
```

- *USDCAdapter.sol* ( [43-43](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L43-L43) ):

```solidity
43:     function _mintToken(address _account, uint256 _amount) internal override {
```

</details>

### [L-31] Sending tokens within loops

Performing token transfers in a loop is not recommended due to the "Fail-Silently" issue. If one transfer fails, the entire transaction fails, which can be problematic when dealing with multiple transfers. This can prevent subsequent recipients from receiving their transfers. Additionally, it can be exploited by malicious contracts to disrupt transfers. To mitigate this, the "withdraw pattern" is recommended, where each recipient triggers their own payment, separating transfer operations and reducing the chance of interference.

<details>
<summary>There are 5 instances (click to show):</summary>

- *LibVerifying.sol* ( [127-210](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L127-L210) ):

```solidity
127:             while (blockId < b.numBlocks && numBlocksVerified < _maxBlocksToVerify) {
128:                 slot = blockId % _config.blockRingBufferSize;
129: 
130:                 blk = _state.blocks[slot];
131:                 if (blk.blockId != blockId) revert L1_BLOCK_MISMATCH();
132: 
133:                 tid = LibUtils.getTransitionId(_state, blk, slot, blockHash);
134:                 // When `tid` is 0, it indicates that there is no proven
135:                 // transition with its parentHash equal to the blockHash of the
136:                 // most recently verified block.
137:                 if (tid == 0) break;
138: 
139:                 // A transition with the correct `parentHash` has been located.
140:                 TaikoData.TransitionState storage ts = _state.transitions[slot][tid];
141: 
142:                 // It's not possible to verify this block if either the
143:                 // transition is contested and awaiting higher-tier proof or if
144:                 // the transition is still within its cooldown period.
145:                 if (ts.contester != address(0)) {
146:                     break;
147:                 } else {
148:                     if (tierProvider == address(0)) {
149:                         tierProvider = _resolver.resolve("tier_provider", false);
150:                     }
151:                     if (
...... OMITTED ......
186:                 }
187: 
188:                 IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));
189:                 tko.transfer(ts.prover, bondToReturn);
190: 
191:                 // Note: We exclusively address the bonds linked to the
192:                 // transition used for verification. While there may exist
193:                 // other transitions for this block, we disregard them entirely.
194:                 // The bonds for these other transitions are burned either when
195:                 // the transitions are generated or proven. In such cases, both
196:                 // the provers and contesters of those transitions forfeit their bonds.
197: 
198:                 emit BlockVerified({
199:                     blockId: blockId,
200:                     assignedProver: blk.assignedProver,
201:                     prover: ts.prover,
202:                     blockHash: blockHash,
203:                     stateRoot: stateRoot,
204:                     tier: ts.tier,
205:                     contestations: ts.contestations
206:                 });
207: 
208:                 ++blockId;
209:                 ++numBlocksVerified;
210:             }
```

- *ERC721Airdrop.sol* ( [59-61](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59-L61) ):

```solidity
59:         for (uint256 i; i < tokenIds.length; ++i) {
60:             IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);
61:         }
```

- *ERC1155Vault.sol* ( [269-277](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L269-L277) ):

```solidity
269:                 for (uint256 i; i < _op.tokenIds.length; ++i) {
270:                     IERC1155(_op.token).safeTransferFrom({
271:                         from: msg.sender,
272:                         to: address(this),
273:                         id: _op.tokenIds[i],
274:                         amount: _op.amounts[i],
275:                         data: ""
276:                     });
277:                 }
```

- *ERC721Vault.sol* ( [170-172](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L170-L172), [210-212](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L210-L212) ):

```solidity
170:             for (uint256 i; i < _tokenIds.length; ++i) {
171:                 IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);
172:             }

210:                 for (uint256 i; i < _op.tokenIds.length; ++i) {
211:                     t.safeTransferFrom(_user, address(this), _op.tokenIds[i]);
212:                 }
```

</details>

### [L-32] Use `SafeCast` to downcast safely

When a type is downcast to a smaller type, the higher order bits are truncated, effectively applying a modulo to the original value. The loss of data may cause incorrect calculations, unexpected state changes, or other unexpected behavior.
It is recommended to use the [SafeCast library](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/utils/math/SafeCast.sol).

<details>
<summary>There are 37 instances (click to show):</summary>

- *TaikoL1.sol* ( [126-126](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L126-L126) ):

```solidity
/// @audit uint256 -> uint64
126:         state.slotB.lastUnpausedAt = uint64(block.timestamp);
```

- *LibDepositing.sol* ( [53-53](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L53-L53), [90-90](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L90-L90) ):

```solidity
/// @audit uint256 -> uint96
53:                 amount: uint96(msg.value),

/// @audit uint256 -> uint96
90:                     amount: uint96(data),
```

- *LibProposing.sol* ( [130-130](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L130-L130), [131-131](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L131-L131), [220-220](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L220-L220) ):

```solidity
/// @audit uint256 -> uint64
130:                 timestamp: uint64(block.timestamp),

/// @audit uint256 -> uint64
131:                 l1Height: uint64(block.number - 1),

/// @audit uint256 -> uint64
220:             proposedIn: uint64(block.number),
```

- *LibProving.sol* ( [78-78](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L78-L78), [264-264](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L264-L264) ):

```solidity
/// @audit uint256 -> uint64
78:             _state.slotB.lastUnpausedAt = uint64(block.timestamp);

/// @audit uint256 -> uint64
264:         ts.timestamp = uint64(block.timestamp);
```

- *LibVerifying.sol* ( [57-57](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L57-L57), [58-58](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L58-L58), [64-64](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L64-L64), [71-71](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L71-L71) ):

```solidity
/// @audit uint256 -> uint64
57:         _state.slotA.genesisHeight = uint64(block.number);

/// @audit uint256 -> uint64
58:         _state.slotA.genesisTimestamp = uint64(block.timestamp);

/// @audit uint256 -> uint64
64:         blk.proposedAt = uint64(block.timestamp);

/// @audit uint256 -> uint64
71:         ts.timestamp = uint64(block.timestamp);
```

- *V3Parser.sol* ( [146-146](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L146-L146), [147-147](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L147-L147), [212-212](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L212-L212), [217-217](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L217-L217), [222-222](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L222-L222) ):

```solidity
/// @audit uint256 -> uint16
146:         enclaveReport.isvProdId = uint16(littleEndianDecode(rawEnclaveReport.substring(256, 2)));

/// @audit uint256 -> uint16
147:         enclaveReport.isvSvn = uint16(littleEndianDecode(rawEnclaveReport.substring(258, 2)));

/// @audit uint256 -> uint16
212:         qeAuthData.parsedDataSize = uint16(littleEndianDecode(rawAuthData.substring(576, 2)));

/// @audit uint256 -> uint16
217:         cert.certType = uint16(littleEndianDecode(rawAuthData.substring(offset, 2)));

/// @audit uint256 -> uint32
222:         cert.certDataSize = uint32(littleEndianDecode(rawAuthData.substring(offset, 4)));
```

- *Asn1Decode.sol* ( [15-15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L15-L15), [20-20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L20-L20), [25-25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L25-L25), [193-193](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L193-L193), [194-194](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L194-L194), [206-206](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L206-L206), [207-207](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L207-L207) ):

```solidity
/// @audit uint256 -> uint80
15:         return uint80(self);

/// @audit uint256 -> uint80
20:         return uint80(self >> 80);

/// @audit uint256 -> uint80
25:         return uint80(self >> 160);

/// @audit uint256 -> uint80
193:             ixFirstContentByte = uint80(ix + 2);

/// @audit uint256 -> uint80
194:             ixLastContentByte = uint80(ixFirstContentByte + length - 1);

/// @audit uint256 -> uint80
206:             ixFirstContentByte = uint80(ix + 2 + lengthbytesLength);

/// @audit uint256 -> uint80
207:             ixLastContentByte = uint80(ixFirstContentByte + length - 1);
```

- *Bridge.sol* ( [89-89](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L89-L89) ):

```solidity
/// @audit uint256 -> uint64
89:         uint64 _timestamp = _suspend ? type(uint64).max : uint64(block.timestamp);
```

- *AddressResolver.sol* ( [39-39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L39-L39) ):

```solidity
/// @audit uint256 -> uint64
39:         return _resolve(uint64(block.chainid), _name, _allowZeroAddress);
```

- *SignalService.sol* ( [264-264](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L264-L264), [308-308](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L308-L308) ):

```solidity
/// @audit uint256 -> uint64
264:         slot_ = getSignalSlot(uint64(block.chainid), _app, _signal);

/// @audit uint256 -> uint64
308:         bytes32 slot = getSignalSlot(uint64(block.chainid), _app, _signal);
```

- *TimelockTokenPool.sol* ( [264-264](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L264-L264) ):

```solidity
/// @audit uint256 -> uint64
264:         return _amount * uint64(block.timestamp - _start) / _period;
```

- *RLPWriter.sol* ( [35-35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L35-L35), [45-45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L45-L45), [47-47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L47-L47) ):

```solidity
/// @audit uint256 -> uint8
35:             out_[0] = bytes1(uint8(_len) + uint8(_offset));

/// @audit uint256 -> uint8
45:             out_[0] = bytes1(uint8(lenLen) + uint8(_offset) + 55);

/// @audit uint256 -> uint8
47:                 out_[i] = bytes1(uint8((_len / (256 ** (lenLen - i))) % 256));
```

- *ERC1155Vault.sol* ( [257-257](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L257-L257) ):

```solidity
/// @audit uint256 -> uint64
257:                     chainId: uint64(block.chainid),
```

- *ERC20Vault.sol* ( [366-366](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L366-L366) ):

```solidity
/// @audit uint256 -> uint64
366:                 chainId: uint64(block.chainid),
```

- *ERC721Vault.sol* ( [204-204](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L204-L204) ):

```solidity
/// @audit uint256 -> uint64
204:                     chainId: uint64(block.chainid),
```

- *SgxVerifier.sol* ( [204-204](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L204-L204), [229-229](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L229-L229) ):

```solidity
/// @audit uint256 -> uint64
204:         uint64 validSince = uint64(block.timestamp);

/// @audit uint256 -> uint64
229:         instances[id] = Instance(newInstance, uint64(block.timestamp));
```

</details>

### [L-33] Use descriptive constant instead of 0 as a parameter

Passing `0` or `0x0` as a function argument can sometimes result in a security issue(e.g. passing zero as the slippage parameter). A historical example is the infamous `0x0` address bug where numerous tokens were lost. This happens because `0` can be interpreted as an uninitialized `address`, leading to transfers to the `0x0` `address`, effectively burning tokens. Moreover, `0` as a denominator in division operations would cause a runtime exception. It's also often indicative of a logical error in the caller's code.

Consider using a constant variable with a descriptive name, so it's clear that the argument is intentionally being used, and for the right reasons.

<details>
<summary>There are 22 instances (click to show):</summary>

- *LibProposing.sol* ( [157-157](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L157-L157) ):

```solidity
157:                 meta_.blobHash = blobhash(0);
```

- *LibVerifying.sol* ( [234-236](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L234-L236) ):

```solidity
234:         (uint64 lastSyncedBlock,) = signalService.getSyncedChainData(
235:             _config.chainId, LibSignals.STATE_ROOT, 0 /* latest block Id*/
236:         );
```

- *AutomataDcapV3Attestation.sol* ( [313-313](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L313-L313) ):

```solidity
313:         bytes32 expectedAuthDataHash = bytes32(qeEnclaveReport.reportData.substring(0, 32));
```

- *V3Parser.sol* ( [38-38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L38-L38), [138-138](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L138-L138), [170-170](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L170-L170), [227-227](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L227-L227) ):

```solidity
38:         bytes memory rawHeader = quote.substring(0, 48);

138:         enclaveReport.cpuSvn = bytes16(rawEnclaveReport.substring(0, 16));

170:         bytes2 version = bytes2(rawHeader.substring(0, 2));

227:         authDataV3.ecdsa256BitSignature = rawAuthData.substring(0, 64);
```

- *Asn1Decode.sol* ( [48-48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L48-L48) ):

```solidity
48:         return _readNodeLength(der, 0);
```

- *BytesUtils.sol* ( [40-40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L40-L40), [169-169](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L169-L169), [179-179](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L179-L179) ):

```solidity
40:         return compare(self, 0, self.length, other, 0, other.length);

169:         return self.length >= offset + other.length && equals(self, offset, other, 0, other.length);

179:         return self.length == other.length && equals(self, 0, other, 0, self.length);
```

- *SigVerifyLib.sol* ( [89-89](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L89-L89), [106-106](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L106-L106), [126-126](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L126-L126), [132-132](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L132-L132) ):

```solidity
89:         bytes memory exponent = publicKey.substring(0, 3);

106:         bytes memory exponent = publicKey.substring(0, 3);

126:         uint256 r = uint256(bytes32(signature.substring(0, 32)));

132:         uint256 gx = uint256(bytes32(publicKey.substring(0, 32)));
```

- *Bridge.sol* ( [531-531](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L531-L531) ):

```solidity
531:             _storeContext(bytes32(0), address(0), uint64(0));
```

- *RLPReader.sol* ( [136-136](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L136-L136) ):

```solidity
136:         out_ = _copy(_in.ptr, 0, _in.length);
```

- *SgxVerifier.sol* ( [154-154](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L154-L154) ):

```solidity
154:         uint32 id = uint32(bytes4(Bytes.slice(_proof.data, 0, 4)));
```

</details>

### [L-34] Loss of precision in divisions

Division by large numbers may result in the result being zero, due to solidity not supporting fractions. Consider requiring a minimum amount for the numerator to ensure that it is always larger than the denominator.

There are 4 instances:

- *LibVerifying.sol* ( [262-262](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L262-L262) ):

```solidity
262:                 || _config.ethDepositMaxFee > type(uint96).max / _config.ethDepositMaxCountPerBlock
```

- *Lib1559Math.sol* ( [28-28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/Lib1559Math.sol#L28-L28) ):

```solidity
28:         return _ethQty(_gasExcess, _adjustmentFactor) / LibFixedPointMath.SCALING_FACTOR
```

- *RLPWriter.sol* ( [47-47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L47-L47) ):

```solidity
47:                 out_[i] = bytes1(uint8((_len / (256 ** (lenLen - i))) % 256));
```

- *LibFixedPointMath.sol* ( [33-33](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L33-L33) ):

```solidity
33:             x = (x << 78) / 5 ** 18;
```

### [L-35] Code does not follow the best practice of check-effects-interaction

Code should follow the best-practice of [check-effects-interaction](https://blockchain-academy.hs-mittweida.de/courses/solidity-coding-beginners-to-intermediate/lessons/solidity-11-coding-patterns/topic/checks-effects-interactions/), where state variables are updated before any external calls are made. Doing so prevents a large class of reentrancy bugs.

<details>
<summary>There are 23 instances (click to show):</summary>

- *CrossChainOwned.sol* ( [53-53](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L53-L53) ):

```solidity
/// @audit `context()` is called on line 45
53:         emit TransactionExecuted(nextTxId++, bytes4(txdata));
```

- *TaikoL2.sol* ( [151-151](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L151-L151), [154-154](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L154-L154), [155-155](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L155-L155) ):

```solidity
/// @audit `syncChainData()` is called on line 148
151:             lastSyncedBlock = _l1BlockId;

/// @audit `syncChainData()` is called on line 148
154:         l2Hashes[parentId] = blockhash(parentId);

/// @audit `syncChainData()` is called on line 148
155:         publicInputHash = publicInputHashNew;
```

- *Bridge.sol* ( [183-183](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L183-L183), [184-184](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L184-L184), [190-190](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L190-L190), [191-191](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L191-L191), [240-240](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L240-L240), [243-246](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L243-L246), [254-254](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L254-L254), [264-264](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L264-L264), [275-275](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L275-L275) ):

```solidity
/// @audit `resolve()` is called on line 172, triggering an external call - `getAddress()`
183:             receivedAt = uint64(block.timestamp);

/// @audit `resolve()` is called on line 172, triggering an external call - `getAddress()`
184:             proofReceipt[msgHash].receivedAt = receivedAt;

/// @audit `resolve()` is called on line 172, triggering an external call - `getAddress()`
190:             delete proofReceipt[msgHash];

/// @audit `resolve()` is called on line 172, triggering an external call - `getAddress()`
191:             messageStatus[msgHash] = Status.RECALLED;

/// @audit `resolve()` is called on line 229, triggering an external call - `getAddress()`
240:             receivedAt = uint64(block.timestamp);

/// @audit `resolve()` is called on line 229, triggering an external call - `getAddress()`
243:                 proofReceipt[msgHash] = ProofReceipt({
244:                     receivedAt: receivedAt,
245:                     preferredExecutor: _message.gasLimit == 0 ? _message.destOwner : msg.sender
246:                 });

/// @audit `resolve()` is called on line 229, triggering an external call - `getAddress()`
254:                 invocationDelay += invocationExtraDelay;

/// @audit `resolve()` is called on line 229, triggering an external call - `getAddress()`
264:             delete proofReceipt[msgHash];

/// @audit `resolve()` is called on line 229, triggering an external call - `getAddress()`
275:                 refundAmount = _message.value;
```

- *ERC1155Vault.sol* ( [76-77](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L76-L77), [280-282](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L280-L282) ):

```solidity
/// @audit `_handleMessage()` is called on line 55, triggering an external call - `name()`
76:         (msgHash, message_) =
77:             IBridge(resolve("bridge", false)).sendMessage{ value: msg.value }(message);

/// @audit `name()` is called on line 263
280:         msgData_ = abi.encodeCall(
281:             this.onMessageInvocation, abi.encode(ctoken_, _user, _op.to, _op.tokenIds, _op.amounts)
282:         );
```

- *ERC20Vault.sol* ( [188-188](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L188-L188), [189-189](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L189-L189), [238-239](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L238-L239), [380-380](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L380-L380), [383-385](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L383-L385) ):

```solidity
/// @audit `owner()` is called on line 164
188:         bridgedToCanonical[_btokenNew] = _ctoken;

/// @audit `owner()` is called on line 164
189:         canonicalToBridged[_ctoken.chainId][_ctoken.addr] = _btokenNew;

/// @audit `_handleMessage()` is called on line 219, triggering an external call - `balanceOf()`
238:         (msgHash, message_) =
239:             IBridge(resolve("bridge", false)).sendMessage{ value: msg.value }(message);

/// @audit `balanceOf()` is called on line 378
380:             balanceChange_ = t.balanceOf(address(this)) - _balance;

/// @audit `balanceOf()` is called on line 378
383:         msgData_ = abi.encodeCall(
384:             this.onMessageInvocation, abi.encode(ctoken_, _user, _to, balanceChange_)
385:         );
```

- *ERC721Vault.sol* ( [61-62](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L61-L62), [216-218](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L216-L218) ):

```solidity
/// @audit `_handleMessage()` is called on line 42, triggering an external call - `name()`
61:         (msgHash, message_) =
62:             IBridge(resolve("bridge", false)).sendMessage{ value: msg.value }(message);

/// @audit `name()` is called on line 207
216:         msgData_ = abi.encodeCall(
217:             this.onMessageInvocation, abi.encode(ctoken_, _user, _op.to, _op.tokenIds)
218:         );
```

- *SgxVerifier.sol* ( [133-133](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L133-L133) ):

```solidity
/// @audit `verifyParsedQuote()` is called on line 128
133:         _address[0] = address(bytes20(_attestation.localEnclaveReport.reportData));
```

</details>

### [L-36] `unchecked` blocks with subtractions may underflow

There aren't any checks to avoid an underflow which can happen inside an `unchecked` block, so the following subtractions may underflow silently.

<details>
<summary>There are 16 instances (click to show):</summary>

- *LibDepositing.sol* ( [101-101](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L101-L101), [140-140](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L140-L140), [141-141](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L141-L141) ):

```solidity
101:                     deposits_[i].amount -= _fee;

140:                 && _state.slotA.numEthDeposits - _state.slotA.nextEthDepositToProcess

141:                     < _config.ethDepositRingBufferSize - 1;
```

- *LibProposing.sol* ( [122-122](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L122-L122), [131-131](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L131-L131) ):

```solidity
122:                 l1Hash: blockhash(block.number - 1),

131:                 l1Height: uint64(block.number - 1),
```

- *LibVerifying.sol* ( [185-185](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L185-L185) ):

```solidity
185:                     bondToReturn -= blk.livenessBond >> 1;
```

- *Guardians.sol* ( [116-116](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L116-L116) ):

```solidity
116:             _approvals[version][_hash] |= 1 << (id - 1);
```

- *TaikoL2.sol* ( [127-127](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L127-L127), [235-235](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L235-L235), [235-235](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L235-L235) ):

```solidity
127:             parentId = block.number - 1;

235:                 uint256 j = _blockId - i - 1;

235:                 uint256 j = _blockId - i - 1;
```

- *LibFixedPointMath.sol* ( [40-40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L40-L40), [47-47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L47-L47), [53-53](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L53-L53), [55-55](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L55-L55), [57-57](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L57-L57), [78-78](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L78-L78) ):

```solidity
40:             x = x - k * 54_916_777_467_707_473_351_141_471_128;

47:             int256 p = y + x - 94_201_549_194_550_492_254_356_042_504_812;

53:             int256 q = x - 2_855_989_394_907_223_263_936_484_059_900;

55:             q = ((q * x) >> 96) - 533_845_033_583_426_703_283_633_433_725_380;

57:             q = ((q * x) >> 96) - 14_423_608_567_350_463_180_887_372_962_807_573;

78:                     >> uint256(195 - k)
```

</details>

## Non Critical Issues

### [N-01] `abi.encodePacked()` should be replaced with `bytes.concat()`

Solidity version 0.8.4 introduces `bytes.concat()`, which can be used to replace `abi.encodePacked()` on bytes/strings. It can make the intended operation clearer, leading to less reviewer confusion.

<details>
<summary>There are 11 instances (click to show):</summary>

- *AutomataDcapV3Attestation.sol* ( [315-315](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L315-L315) ):

```solidity
315:             abi.encodePacked(authDataV3.ecdsaAttestationKey, authDataV3.qeAuthData.data);
```

- *PEMCertChainLib.sol* ( [181-181](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L181-L181) ):

```solidity
181:             cert.signature = abi.encodePacked(sigX, sigY);
```

- *V3Parser.sol* ( [119-127](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L119-L127), [129-129](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L129-L129) ):

```solidity
119:         bytes memory headerBytes = abi.encodePacked(
120:             header.version,
121:             header.attestationKeyType,
122:             header.teeType,
123:             header.qeSvn,
124:             header.pceSvn,
125:             header.qeVendorId,
126:             header.userData
127:         );

129:         signedQuoteData = abi.encodePacked(headerBytes, V3Parser.packQEReport(localEnclaveReport));
```

- *RLPWriter.sol* ( [17-17](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L17-L17) ):

```solidity
17:             out_ = abi.encodePacked(_writeLength(_in.length, 128), _in);
```

- *MerkleTrie.sol* ( [81-81](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L81-L81), [94-94](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L94-L94), [100-100](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L100-L100) ):

```solidity
81:         bytes memory currentNodeID = abi.encodePacked(_root);

94:                     Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),

100:                     Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
```

- *SecureMerkleTrie.sol* ( [55-55](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L55-L55) ):

```solidity
55:         hash_ = abi.encodePacked(keccak256(_key));
```

- *BridgedERC721.sol* ( [109-111](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L109-L111) ):

```solidity
109:             abi.encodePacked(
110:                 LibBridgedToken.buildURI(srcToken, srcChainId), Strings.toString(_tokenId)
111:             )
```

- *LibBridgedToken.sol* ( [54-60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L54-L60) ):

```solidity
54:             abi.encodePacked(
55:                 "ethereum:",
56:                 Strings.toHexString(uint160(_srcToken), 20),
57:                 "@",
58:                 Strings.toString(_srcChainId),
59:                 "/tokenURI?uint256="
60:             )
```

</details>

### [N-02] `abi.encodePacked()` on strings should be replaced with `string.concat()`

Solidity version 0.8.12 introduces `string.concat()`, which can be used to replace `abi.encodePacked()` on strings and makes the intended operation clearer, leading to less reviewer confusion.

There are 2 instances:

- *BridgedERC721.sol* ( [109-111](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L109-L111) ):

```solidity
109:             abi.encodePacked(
110:                 LibBridgedToken.buildURI(srcToken, srcChainId), Strings.toString(_tokenId)
111:             )
```

- *LibBridgedToken.sol* ( [54-60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L54-L60) ):

```solidity
54:             abi.encodePacked(
55:                 "ethereum:",
56:                 Strings.toHexString(uint160(_srcToken), 20),
57:                 "@",
58:                 Strings.toString(_srcChainId),
59:                 "/tokenURI?uint256="
60:             )
```

### [N-03] Custom errors has no error details

Consider adding parameters to the error to indicate which user or values caused the failure.

<details>
<summary>There are 160 instances (click to show):</summary>

- *TaikoErrors.sol* ( [12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L12), [13](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L13), [14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L14), [15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L15), [16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L16), [17](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L17), [18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L18), [19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L19), [20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L20), [21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L21), [22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L22), [23](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L23), [24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L24), [25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L25), [26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L26), [27](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L27), [28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L28), [29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L29), [30](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L30), [31](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L31), [32](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L32), [33](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L33), [34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L34), [35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L35), [36](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L36), [37](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L37), [38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L38), [39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L39), [40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L40), [41](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L41), [42](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L42) ):

```solidity
12:     error L1_ALREADY_CONTESTED();

13:     error L1_ALREADY_PROVED();

14:     error L1_ASSIGNED_PROVER_NOT_ALLOWED();

15:     error L1_BLOB_FOR_DA_DISABLED();

16:     error L1_BLOB_NOT_FOUND();

17:     error L1_BLOB_NOT_REUSABLE();

18:     error L1_BLOB_REUSE_DISABLED();

19:     error L1_BLOCK_MISMATCH();

20:     error L1_INVALID_BLOCK_ID();

21:     error L1_INVALID_CONFIG();

22:     error L1_INVALID_ETH_DEPOSIT();

23:     error L1_INVALID_HOOK();

24:     error L1_INVALID_PARAM();

25:     error L1_INVALID_PAUSE_STATUS();

26:     error L1_INVALID_PROVER();

27:     error L1_INVALID_TIER();

28:     error L1_INVALID_TRANSITION();

29:     error L1_LIVENESS_BOND_NOT_RECEIVED();

30:     error L1_NOT_ASSIGNED_PROVER();

31:     error L1_PROPOSER_NOT_EOA();

32:     error L1_PROVING_PAUSED();

33:     error L1_RECEIVE_DISABLED();

34:     error L1_MISSING_VERIFIER();

35:     error L1_TOO_MANY_BLOCKS();

36:     error L1_TOO_MANY_TIERS();

37:     error L1_TRANSITION_ID_ZERO();

38:     error L1_TRANSITION_NOT_FOUND();

39:     error L1_TXLIST_SIZE();

40:     error L1_UNAUTHORIZED();

41:     error L1_UNEXPECTED_PARENT();

42:     error L1_UNEXPECTED_TRANSITION_ID();
```

- *TaikoToken.sol* ( [18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L18) ):

```solidity
18:     error TKO_INVALID_ADDR();
```

- *TaikoGovernor.sol* ( [25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L25) ):

```solidity
25:     error TG_INVALID_SIGNATURES_LENGTH();
```

- *AssignmentHook.sol* ( [50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L50), [51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L51), [52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L52) ):

```solidity
50:     error HOOK_ASSIGNMENT_EXPIRED();

51:     error HOOK_ASSIGNMENT_INVALID_SIG();

52:     error HOOK_TIER_NOT_FOUND();
```

- *LibDepositing.sol* ( [22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L22) ):

```solidity
22:     error L1_INVALID_ETH_DEPOSIT();
```

- *LibProposing.sol* ( [44](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L44), [45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L45), [46](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L46), [47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L47), [48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L48), [49](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L49), [50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L50), [51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L51), [52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L52), [53](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L53), [54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L54), [55](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L55), [56](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L56), [57](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L57) ):

```solidity
44:     error L1_BLOB_FOR_DA_DISABLED();

45:     error L1_BLOB_NOT_FOUND();

46:     error L1_BLOB_NOT_REUSABLE();

47:     error L1_BLOB_REUSE_DISABLED();

48:     error L1_INVALID_HOOK();

49:     error L1_INVALID_PARAM();

50:     error L1_INVALID_PROVER();

51:     error L1_LIVENESS_BOND_NOT_RECEIVED();

52:     error L1_PROPOSER_NOT_EOA();

53:     error L1_TOO_MANY_BLOCKS();

54:     error L1_TXLIST_OFFSET();

55:     error L1_TXLIST_SIZE();

56:     error L1_UNAUTHORIZED();

57:     error L1_UNEXPECTED_PARENT();
```

- *LibProving.sol* ( [59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L59), [60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L60), [61](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L61), [62](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L62), [63](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L63), [64](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L64), [65](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L65), [66](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L66), [67](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L67), [68](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L68) ):

```solidity
59:     error L1_ALREADY_CONTESTED();

60:     error L1_ALREADY_PROVED();

61:     error L1_ASSIGNED_PROVER_NOT_ALLOWED();

62:     error L1_BLOCK_MISMATCH();

63:     error L1_INVALID_BLOCK_ID();

64:     error L1_INVALID_PAUSE_STATUS();

65:     error L1_INVALID_TIER();

66:     error L1_INVALID_TRANSITION();

67:     error L1_MISSING_VERIFIER();

68:     error L1_NOT_ASSIGNED_PROVER();
```

- *LibUtils.sol* ( [11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L11), [12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L12), [13](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L13), [14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L14) ):

```solidity
11:     error L1_BLOCK_MISMATCH();

12:     error L1_INVALID_BLOCK_ID();

13:     error L1_TRANSITION_NOT_FOUND();

14:     error L1_UNEXPECTED_TRANSITION_ID();
```

- *LibVerifying.sol* ( [39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L39), [40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L40), [41](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L41) ):

```solidity
39:     error L1_BLOCK_MISMATCH();

40:     error L1_INVALID_CONFIG();

41:     error L1_TRANSITION_ID_ZERO();
```

- *Guardians.sol* ( [45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L45), [46](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L46), [47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L47), [48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L48) ):

```solidity
45:     error INVALID_GUARDIAN();

46:     error INVALID_GUARDIAN_SET();

47:     error INVALID_MIN_GUARDIANS();

48:     error INVALID_PROOF();
```

- *ITierProvider.sol* ( [17](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L17) ):

```solidity
17:     error TIER_NOT_FOUND();
```

- *CrossChainOwned.sol* ( [28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L28), [29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L29), [30](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L30), [31](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L31) ):

```solidity
28:     error XCO_INVALID_OWNER_CHAINID();

29:     error XCO_INVALID_TX_ID();

30:     error XCO_PERMISSION_DENIED();

31:     error XCO_TX_REVERTED();
```

- *Lib1559Math.sol* ( [11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/Lib1559Math.sol#L11) ):

```solidity
11:     error EIP1559_INVALID_PARAMS();
```

- *TaikoL2.sol* ( [59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L59), [60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L60), [61](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L61), [62](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L62), [63](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L63), [64](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L64) ):

```solidity
59:     error L2_BASEFEE_MISMATCH();

60:     error L2_INVALID_CHAIN_ID();

61:     error L2_INVALID_PARAM();

62:     error L2_INVALID_SENDER();

63:     error L2_PUBLIC_INPUT_HASH_MISMATCH();

64:     error L2_TOO_LATE();
```

- *TaikoL2EIP1559Configurable.sol* ( [20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L20) ):

```solidity
20:     error L2_INVALID_CONFIG();
```

- *Bridge.sol* ( [50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L50), [51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L51), [52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L52), [53](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L53), [54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L54), [55](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L55), [56](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L56), [57](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L57), [58](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L58), [59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L59), [60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L60), [61](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L61), [62](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L62) ):

```solidity
50:     error B_INVALID_CHAINID();

51:     error B_INVALID_CONTEXT();

52:     error B_INVALID_GAS_LIMIT();

53:     error B_INVALID_STATUS();

54:     error B_INVALID_USER();

55:     error B_INVALID_VALUE();

56:     error B_MESSAGE_NOT_SENT();

57:     error B_NON_RETRIABLE();

58:     error B_NOT_FAILED();

59:     error B_NOT_RECEIVED();

60:     error B_PERMISSION_DENIED();

61:     error B_STATUS_MISMATCH();

62:     error B_INVOCATION_TOO_EARLY();
```

- *AddressManager.sol* ( [25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L25), [26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L26) ):

```solidity
25:     error AM_INVALID_PARAMS();

26:     error AM_UNSUPPORTED();
```

- *AddressResolver.sol* ( [16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L16), [17](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L17), [18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L18) ):

```solidity
16:     error RESOLVER_DENIED();

17:     error RESOLVER_INVALID_MANAGER();

18:     error RESOLVER_UNEXPECTED_CHAINID();
```

- *EssentialContract.sol* ( [35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L35), [36](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L36), [37](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L37) ):

```solidity
35:     error REENTRANT_CALL();

36:     error INVALID_PAUSE_STATUS();

37:     error ZERO_ADDR_MANAGER();
```

- *Lib4844.sol* ( [19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/Lib4844.sol#L19), [20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/Lib4844.sol#L20), [21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/Lib4844.sol#L21), [22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/Lib4844.sol#L22) ):

```solidity
19:     error EVAL_FAILED_1();

20:     error EVAL_FAILED_2();

21:     error POINT_X_TOO_LARGE();

22:     error POINT_Y_TOO_LARGE();
```

- *LibAddress.sol* ( [16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L16) ):

```solidity
16:     error ETH_TRANSFER_FAILED();
```

- *LibTrieProof.sol* ( [20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibTrieProof.sol#L20), [21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibTrieProof.sol#L21) ):

```solidity
20:     error LTP_INVALID_ACCOUNT_PROOF();

21:     error LTP_INVALID_INCLUSION_PROOF();
```

- *SignalService.sol* ( [25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L25), [26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L26), [27](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L27), [28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L28), [29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L29), [30](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L30), [31](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L31), [32](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L32), [33](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L33) ):

```solidity
25:     error SS_EMPTY_PROOF();

26:     error SS_INVALID_SENDER();

27:     error SS_INVALID_LAST_HOP_CHAINID();

28:     error SS_INVALID_MID_HOP_CHAINID();

29:     error SS_INVALID_STATE();

30:     error SS_INVALID_VALUE();

31:     error SS_SIGNAL_NOT_FOUND();

32:     error SS_UNAUTHORIZED();

33:     error SS_UNSUPPORTED();
```

- *TimelockTokenPool.sol* ( [101](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L101), [102](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L102), [103](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L103), [104](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L104) ):

```solidity
101:     error ALREADY_GRANTED();

102:     error INVALID_GRANT();

103:     error INVALID_PARAM();

104:     error NOTHING_TO_VOID();
```

- *ERC20Airdrop2.sol* ( [37](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L37) ):

```solidity
37:     error WITHDRAWALS_NOT_ONGOING();
```

- *MerkleClaimable.sol* ( [29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L29), [30](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L30), [31](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L31) ):

```solidity
29:     error CLAIM_NOT_ONGOING();

30:     error CLAIMED_ALREADY();

31:     error INVALID_PROOF();
```

- *LibFixedPointMath.sol* ( [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L10) ):

```solidity
10:     error Overflow();
```

- *BaseNFTVault.sol* ( [133](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L133), [134](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L134), [135](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L135), [136](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L136), [137](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L137), [138](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L138) ):

```solidity
133:     error VAULT_INVALID_TOKEN();

134:     error VAULT_INVALID_AMOUNT();

135:     error VAULT_INVALID_TO();

136:     error VAULT_INTERFACE_NOT_SUPPORTED();

137:     error VAULT_TOKEN_ARRAY_MISMATCH();

138:     error VAULT_MAX_TOKEN_PER_TXN_EXCEEDED();
```

- *BaseVault.sol* ( [20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L20) ):

```solidity
20:     error VAULT_PERMISSION_DENIED();
```

- *BridgedERC1155.sol* ( [29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L29) ):

```solidity
29:     error BTOKEN_CANNOT_RECEIVE();
```

- *BridgedERC20.sol* ( [34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L34), [35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L35) ):

```solidity
34:     error BTOKEN_CANNOT_RECEIVE();

35:     error BTOKEN_UNAUTHORIZED();
```

- *BridgedERC20Base.sol* ( [29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L29), [30](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L30), [31](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L31) ):

```solidity
29:     error BB_PERMISSION_DENIED();

30:     error BB_INVALID_PARAMS();

31:     error BB_MINT_DISALLOWED();
```

- *BridgedERC721.sol* ( [21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L21), [22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L22) ):

```solidity
21:     error BTOKEN_CANNOT_RECEIVE();

22:     error BTOKEN_INVALID_BURN();
```

- *ERC20Vault.sol* ( [136](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L136), [137](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L137), [138](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L138), [139](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L139), [140](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L140), [141](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L141), [142](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L142) ):

```solidity
136:     error VAULT_BTOKEN_BLACKLISTED();

137:     error VAULT_CTOKEN_MISMATCH();

138:     error VAULT_INVALID_TOKEN();

139:     error VAULT_INVALID_AMOUNT();

140:     error VAULT_INVALID_NEW_BTOKEN();

141:     error VAULT_INVALID_TO();

142:     error VAULT_NOT_SAME_OWNER();
```

- *LibBridgedToken.sol* ( [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L9) ):

```solidity
9:     error BTOKEN_INVALID_PARAMS();
```

- *GuardianVerifier.sol* ( [13](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L13) ):

```solidity
13:     error PERMISSION_DENIED();
```

- *SgxVerifier.sol* ( [74](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L74), [75](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L75), [76](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L76), [77](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L77), [78](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L78) ):

```solidity
74:     error SGX_ALREADY_ATTESTED();

75:     error SGX_INVALID_ATTESTATION();

76:     error SGX_INVALID_INSTANCE();

77:     error SGX_INVALID_PROOF();

78:     error SGX_RA_NOT_SUPPORTED();
```

</details>

### [N-04] Import declarations should import specific identifiers, rather than the whole file

Using import declarations of the form `import {<identifier_name>} from "some/file.sol"` avoids polluting the symbol namespace making flattened files smaller, and speeds up compilation (but does not save any gas).

<details>
<summary>There are 179 instances (click to show):</summary>

- *ITaikoL1.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/ITaikoL1.sol#L4) ):

```solidity
4: import "./TaikoData.sol";
```

- *TaikoEvents.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoEvents.sol#L4) ):

```solidity
4: import "./TaikoData.sol";
```

- *TaikoL1.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L6), [7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L7), [8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L8), [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L9), [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L10), [11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L11) ):

```solidity
4: import "../common/EssentialContract.sol";

5: import "./libs/LibDepositing.sol";

6: import "./libs/LibProposing.sol";

7: import "./libs/LibProving.sol";

8: import "./libs/LibVerifying.sol";

9: import "./ITaikoL1.sol";

10: import "./TaikoErrors.sol";

11: import "./TaikoEvents.sol";
```

- *TaikoToken.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L6), [7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L7) ):

```solidity
4: import "@openzeppelin/contracts-upgradeable/token/ERC20/ERC20Upgradeable.sol";

5: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20SnapshotUpgradeable.sol";

6: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20VotesUpgradeable.sol";

7: import "../common/EssentialContract.sol";
```

- *TaikoGovernor.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L5), [7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L7), [8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L8), [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L10), [12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L12) ):

```solidity
4: import "@openzeppelin/contracts-upgradeable/governance/GovernorUpgradeable.sol";

5: import

7: import "@openzeppelin/contracts-upgradeable/governance/extensions/GovernorVotesUpgradeable.sol";

8: import

10: import

12: import "../../common/EssentialContract.sol";
```

- *TaikoTimelockController.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L5) ):

```solidity
4: import "@openzeppelin/contracts-upgradeable/governance/TimelockControllerUpgradeable.sol";

5: import "../../common/EssentialContract.sol";
```

- *AssignmentHook.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L6), [7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L7), [8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L8), [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L9) ):

```solidity
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

5: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";

6: import "../../common/EssentialContract.sol";

7: import "../../libs/LibAddress.sol";

8: import "../ITaikoL1.sol";

9: import "./IHook.sol";
```

- *IHook.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/IHook.sol#L4) ):

```solidity
4: import "../TaikoData.sol";
```

- *LibDepositing.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L6), [7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L7) ):

```solidity
4: import "../../common/IAddressResolver.sol";

5: import "../../libs/LibAddress.sol";

6: import "../../libs/LibMath.sol";

7: import "../TaikoData.sol";
```

- *LibProposing.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L6), [7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L7), [8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L8), [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L9), [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L10) ):

```solidity
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

5: import "../../common/IAddressResolver.sol";

6: import "../../libs/LibAddress.sol";

7: import "../hooks/IHook.sol";

8: import "../tiers/ITierProvider.sol";

9: import "../TaikoData.sol";

10: import "./LibDepositing.sol";
```

- *LibProving.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L6), [7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L7), [8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L8), [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L9), [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L10) ):

```solidity
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

5: import "../../common/IAddressResolver.sol";

6: import "../../libs/LibMath.sol";

7: import "../../verifiers/IVerifier.sol";

8: import "../tiers/ITierProvider.sol";

9: import "../TaikoData.sol";

10: import "./LibUtils.sol";
```

- *LibUtils.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L4) ):

```solidity
4: import "../TaikoData.sol";
```

- *LibVerifying.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L6), [7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L7), [8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L8), [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L9), [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L10), [11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L11) ):

```solidity
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

5: import "../../common/IAddressResolver.sol";

6: import "../../libs/LibMath.sol";

7: import "../../signal/ISignalService.sol";

8: import "../../signal/LibSignals.sol";

9: import "../tiers/ITierProvider.sol";

10: import "../TaikoData.sol";

11: import "./LibUtils.sol";
```

- *GuardianProver.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/GuardianProver.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/GuardianProver.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/GuardianProver.sol#L6) ):

```solidity
4: import "../tiers/ITierProvider.sol";

5: import "../ITaikoL1.sol";

6: import "./Guardians.sol";
```

- *Guardians.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L4) ):

```solidity
4: import "../../common/EssentialContract.sol";
```

- *DevnetTierProvider.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L5) ):

```solidity
4: import "../../common/EssentialContract.sol";

5: import "./ITierProvider.sol";
```

- *MainnetTierProvider.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L5) ):

```solidity
4: import "../../common/EssentialContract.sol";

5: import "./ITierProvider.sol";
```

- *TestnetTierProvider.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L5) ):

```solidity
4: import "../../common/EssentialContract.sol";

5: import "./ITierProvider.sol";
```

- *CrossChainOwned.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L6) ):

```solidity
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

5: import "../common/EssentialContract.sol";

6: import "../bridge/IBridge.sol";
```

- *Lib1559Math.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/Lib1559Math.sol#L4) ):

```solidity
4: import "../thirdparty/solmate/LibFixedPointMath.sol";
```

- *TaikoL2.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L5), [7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L7), [8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L8), [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L9), [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L10), [11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L11), [12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L12) ):

```solidity
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

5: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";

7: import "../libs/LibAddress.sol";

8: import "../libs/LibMath.sol";

9: import "../signal/ISignalService.sol";

10: import "../signal/LibSignals.sol";

11: import "./Lib1559Math.sol";

12: import "./CrossChainOwned.sol";
```

- *TaikoL2EIP1559Configurable.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L4) ):

```solidity
4: import "./TaikoL2.sol";
```

- *Asn1Decode.sol* ( [8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L8) ):

```solidity
8: import "./BytesUtils.sol";
```

- *RsaVerify.sol* ( [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L5) ):

```solidity
5: import "./SHA1.sol";
```

- *SigVerifyLib.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L6) ):

```solidity
4: import "../interfaces/ISigVerifyLib.sol";

5: import "./RsaVerify.sol";

6: import "./BytesUtils.sol";
```

- *Bridge.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L6), [7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L7), [8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L8), [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L9) ):

```solidity
4: import "@openzeppelin/contracts/utils/Address.sol";

5: import "../common/EssentialContract.sol";

6: import "../libs/LibAddress.sol";

7: import "../signal/ISignalService.sol";

8: import "../thirdparty/nomad-xyz/ExcessivelySafeCall.sol";

9: import "./IBridge.sol";
```

- *AddressManager.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L5) ):

```solidity
4: import "./IAddressManager.sol";

5: import "./EssentialContract.sol";
```

- *AddressResolver.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L6) ):

```solidity
4: import "@openzeppelin/contracts-upgradeable/proxy/utils/Initializable.sol";

5: import "./IAddressManager.sol";

6: import "./IAddressResolver.sol";
```

- *EssentialContract.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L6) ):

```solidity
4: import "@openzeppelin/contracts/proxy/utils/UUPSUpgradeable.sol";

5: import "@openzeppelin/contracts-upgradeable/access/Ownable2StepUpgradeable.sol";

6: import "./AddressResolver.sol";
```

- *LibAddress.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L6), [7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L7), [8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L8) ):

```solidity
4: import "@openzeppelin/contracts/utils/Address.sol";

5: import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol";

6: import "@openzeppelin/contracts/utils/introspection/IERC165.sol";

7: import "@openzeppelin/contracts/interfaces/IERC1271.sol";

8: import "../thirdparty/nomad-xyz/ExcessivelySafeCall.sol";
```

- *LibTrieProof.sol* ( [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibTrieProof.sol#L9), [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibTrieProof.sol#L10), [11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibTrieProof.sol#L11) ):

```solidity
9: import "../thirdparty/optimism/rlp/RLPReader.sol";

10: import "../thirdparty/optimism/rlp/RLPWriter.sol";

11: import "../thirdparty/optimism/trie/SecureMerkleTrie.sol";
```

- *SignalService.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L6), [7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L7), [8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L8) ):

```solidity
4: import "@openzeppelin/contracts/utils/math/SafeCast.sol";

5: import "../common/EssentialContract.sol";

6: import "../libs/LibTrieProof.sol";

7: import "./ISignalService.sol";

8: import "./LibSignals.sol";
```

- *TimelockTokenPool.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L6), [7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L7) ):

```solidity
4: import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol";

5: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

6: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";

7: import "../common/EssentialContract.sol";
```

- *ERC20Airdrop.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L6) ):

```solidity
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

5: import "@openzeppelin/contracts/governance/utils/IVotes.sol";

6: import "./MerkleClaimable.sol";
```

- *ERC20Airdrop2.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L6) ):

```solidity
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

5: import "../../libs/LibMath.sol";

6: import "./MerkleClaimable.sol";
```

- *ERC721Airdrop.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L5) ):

```solidity
4: import "@openzeppelin/contracts/token/ERC721/IERC721.sol";

5: import "./MerkleClaimable.sol";
```

- *MerkleClaimable.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L5) ):

```solidity
4: import "@openzeppelin/contracts/utils/cryptography/MerkleProof.sol";

5: import "../../common/EssentialContract.sol";
```

- *BaseNFTVault.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L4) ):

```solidity
4: import "./BaseVault.sol";
```

- *BaseVault.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L6), [7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L7) ):

```solidity
4: import "@openzeppelin/contracts-upgradeable/utils/introspection/IERC165Upgradeable.sol";

5: import "@openzeppelin/contracts/proxy/ERC1967/ERC1967Proxy.sol";

6: import "../bridge/IBridge.sol";

7: import "../common/EssentialContract.sol";
```

- *BridgedERC1155.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L6), [8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L8), [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L9) ):

```solidity
4: import "@openzeppelin/contracts/utils/Strings.sol";

5: import "@openzeppelin/contracts-upgradeable/token/ERC1155/ERC1155Upgradeable.sol";

6: import

8: import "../common/EssentialContract.sol";

9: import "./LibBridgedToken.sol";
```

- *BridgedERC20.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L6), [7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L7), [8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L8), [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L9) ):

```solidity
4: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/IERC20MetadataUpgradeable.sol";

5: import "@openzeppelin/contracts/utils/Strings.sol";

6: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20SnapshotUpgradeable.sol";

7: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20VotesUpgradeable.sol";

8: import "./LibBridgedToken.sol";

9: import "./BridgedERC20Base.sol";
```

- *BridgedERC20Base.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L5) ):

```solidity
4: import "../common/EssentialContract.sol";

5: import "./IBridgedERC20.sol";
```

- *BridgedERC721.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L6), [7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L7) ):

```solidity
4: import "@openzeppelin/contracts-upgradeable/token/ERC721/ERC721Upgradeable.sol";

5: import "@openzeppelin/contracts/utils/Strings.sol";

6: import "../common/EssentialContract.sol";

7: import "./LibBridgedToken.sol";
```

- *ERC1155Vault.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L6), [7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L7), [8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L8), [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L9) ):

```solidity
4: import "@openzeppelin/contracts/token/ERC1155/IERC1155.sol";

5: import "@openzeppelin/contracts-upgradeable/token/ERC1155/utils/ERC1155ReceiverUpgradeable.sol";

6: import "../bridge/IBridge.sol";

7: import "../libs/LibAddress.sol";

8: import "./BaseNFTVault.sol";

9: import "./BridgedERC1155.sol";
```

- *ERC20Vault.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L6), [7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L7), [8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L8), [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L9), [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L10) ):

```solidity
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

5: import "@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol";

6: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";

7: import "../bridge/IBridge.sol";

8: import "../libs/LibAddress.sol";

9: import "./BridgedERC20.sol";

10: import "./BaseVault.sol";
```

- *ERC721Vault.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L6), [7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L7), [8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L8), [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L9) ):

```solidity
4: import "@openzeppelin/contracts/token/ERC721/IERC721.sol";

5: import "@openzeppelin/contracts/token/ERC721/IERC721Receiver.sol";

6: import "../bridge/IBridge.sol";

7: import "../libs/LibAddress.sol";

8: import "./BaseNFTVault.sol";

9: import "./BridgedERC721.sol";
```

- *LibBridgedToken.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L4) ):

```solidity
4: import "@openzeppelin/contracts/utils/Strings.sol";
```

- *USDCAdapter.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L4) ):

```solidity
4: import "../BridgedERC20Base.sol";
```

- *GuardianVerifier.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L6) ):

```solidity
4: import "../common/EssentialContract.sol";

5: import "../L1/TaikoData.sol";

6: import "./IVerifier.sol";
```

- *IVerifier.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/IVerifier.sol#L4) ):

```solidity
4: import "../L1/TaikoData.sol";
```

- *SgxVerifier.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L6), [7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L7), [8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L8), [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L9), [10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L10) ):

```solidity
4: import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol";

5: import "../L1/ITaikoL1.sol";

6: import "../common/EssentialContract.sol";

7: import "../thirdparty/optimism/Bytes.sol";

8: import "../automata-attestation/interfaces/IAttestation.sol";

9: import "../automata-attestation/lib/QuoteV3Auth/V3Struct.sol";

10: import "./IVerifier.sol";
```

</details>

### [N-05] Visibility of state variables is not explicitly defined

To avoid misunderstandings and unexpected state accesses, it is recommended to explicitly define the visibility of each state variable.

There are 3 instances:

- *PEMCertChainLib.sol* ( [32-32](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L32-L32) ):

```solidity
32:     uint256 constant SGX_TCB_CPUSVN_SIZE = 16;
```

- *BytesUtils.sol* ( [310-311](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L310-L311) ):

```solidity
310:     bytes constant BASE32_HEX_TABLE =
311:         hex"00010203040506070809FFFFFFFFFFFFFF0A0B0C0D0E0F101112131415161718191A1B1C1D1E1FFFFFFFFFFFFFFFFFFFFF0A0B0C0D0E0F101112131415161718191A1B1C1D1E1F";
```

- *ExcessivelySafeCall.sol* ( [6-7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L6-L7) ):

```solidity
6:     uint256 constant LOW_28_MASK =
7:         0x00000000ffffffffffffffffffffffffffffffffffffffffffffffffffffffff;
```

### [N-06] There is no need to initialize variables with 0

Since the variables are automatically set to 0 when created, it is redundant to initialize it with 0 again.

<details>
<summary>There are 13 instances (click to show):</summary>

- *Guardians.sol* ( [80-80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L80-L80) ):

```solidity
80:         for (uint256 i = 0; i < _newGuardians.length; ++i) {
```

- *PEMCertChainLib.sol* ( [51-51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L51-L51) ):

```solidity
51:         uint256 index = 0;
```

- *V3Parser.sol* ( [18-18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L18-L18) ):

```solidity
18:     bytes4 internal constant SUPPORTED_TEE_TYPE = 0;
```

- *BytesUtils.sol* ( [80-80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L80-L80), [331-331](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L331-L331) ):

```solidity
80:         for (uint256 idx = 0; idx < shortest; idx += 32) {

331:         uint256 ret = 0;
```

- *X509DateUtils.sol* ( [46-46](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L46-L46) ):

```solidity
46:         uint256 timestamp = 0;
```

- *RLPReader.sol* ( [72-72](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L72-L72) ):

```solidity
72:         uint256 itemCount = 0;
```

- *RLPWriter.sol* ( [58-58](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L58-L58), [66-66](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66-L66) ):

```solidity
58:         uint256 i = 0;

66:         for (uint256 j = 0; j < out_.length; j++) {
```

- *MerkleTrie.sol* ( [30-30](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L30-L30), [82-82](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L82-L82), [85-85](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85-L85), [208-208](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L208-L208) ):

```solidity
30:     uint8 internal constant PREFIX_EXTENSION_EVEN = 0;

82:         uint256 currentKeyIndex = 0;

85:         for (uint256 i = 0; i < proof.length; i++) {

208:         for (uint256 i = 0; i < length;) {
```

</details>

### [N-07] Names of `private`/`internal` functions should be prefixed with an underscore

It is recommended by the [Solidity Style Guide](https://docs.soliditylang.org/en/v0.8.20/style-guide.html#underscore-prefix-for-non-external-functions-and-variables).

<details>
<summary>There are 96 instances (click to show):</summary>

- *LibDepositing.sol* ( [29-36](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L29-L36), [67-73](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L67-L73), [122-129](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L122-L129) ):

```solidity
29:     function depositEtherToL2(
30:         TaikoData.State storage _state,
31:         TaikoData.Config memory _config,
32:         IAddressResolver _resolver,
33:         address _recipient
34:     )
35:         internal
36:     {

67:     function processDeposits(
68:         TaikoData.State storage _state,
69:         TaikoData.Config memory _config,
70:         address _feeRecipient
71:     )
72:         internal
73:         returns (TaikoData.EthDeposit[] memory deposits_)

122:     function canDepositEthToL2(
123:         TaikoData.State storage _state,
124:         TaikoData.Config memory _config,
125:         uint256 _amount
126:     )
127:         internal
128:         view
129:         returns (bool)
```

- *LibProposing.sol* ( [68-76](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L68-L76), [287-294](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L287-L294) ):

```solidity
68:     function proposeBlock(
69:         TaikoData.State storage _state,
70:         TaikoData.Config memory _config,
71:         IAddressResolver _resolver,
72:         bytes calldata _data,
73:         bytes calldata _txList
74:     )
75:         internal
76:         returns (TaikoData.BlockMetadata memory meta_, TaikoData.EthDeposit[] memory deposits_)

287:     function isBlobReusable(
288:         TaikoData.State storage _state,
289:         TaikoData.Config memory _config,
290:         bytes32 _blobHash
291:     )
292:         internal
293:         view
294:         returns (bool)
```

- *LibProving.sol* ( [91-100](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L91-L100) ):

```solidity
91:     function proveBlock(
92:         TaikoData.State storage _state,
93:         TaikoData.Config memory _config,
94:         IAddressResolver _resolver,
95:         TaikoData.BlockMetadata memory _meta,
96:         TaikoData.Transition memory _tran,
97:         TaikoData.TierProof memory _proof
98:     )
99:         internal
100:         returns (uint8 maxBlocksToVerify_)
```

- *LibUtils.sol* ( [70-78](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L70-L78) ):

```solidity
70:     function getTransitionId(
71:         TaikoData.State storage _state,
72:         TaikoData.Block storage _blk,
73:         uint64 _slot,
74:         bytes32 _parentHash
75:     )
76:         internal
77:         view
78:         returns (uint32 tid_)
```

- *LibVerifying.sol* ( [85-92](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L85-L92) ):

```solidity
85:     function verifyBlocks(
86:         TaikoData.State storage _state,
87:         TaikoData.Config memory _config,
88:         IAddressResolver _resolver,
89:         uint64 _maxBlocksToVerify
90:     )
91:         internal
92:     {
```

- *Guardians.sol* ( [111-111](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L111-L111), [124-124](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L124-L124), [128-128](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L128-L128) ):

```solidity
111:     function approve(uint256 _operationId, bytes32 _hash) internal returns (bool approved_) {

124:     function deleteApproval(bytes32 _hash) internal {

128:     function isApproved(uint256 _approvalBits) internal view returns (bool) {
```

- *Lib1559Math.sol* ( [16-22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/Lib1559Math.sol#L16-L22) ):

```solidity
16:     function basefee(
17:         uint256 _gasExcess,
18:         uint256 _adjustmentFactor
19:     )
20:         internal
21:         pure
22:         returns (uint256)
```

- *V3Parser.sol* ( [21-27](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L21-L27), [62-71](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L62-L71), [133-136](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L133-L136), [152-152](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L152-L152), [165-168](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L165-L168), [203-209](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L203-L209), [244-247](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L244-L247), [267-273](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L267-L273) ):

```solidity
21:     function parseInput(
22:         bytes memory quote,
23:         address pemCertLibAddr
24:     )
25:         internal
26:         pure
27:         returns (bool success, V3Struct.ParsedV3QuoteStruct memory v3ParsedQuote)

62:     function validateParsedInput(V3Struct.ParsedV3QuoteStruct memory v3Quote)
63:         internal
64:         pure
65:         returns (
66:             bool success,
67:             V3Struct.Header memory header,
68:             V3Struct.EnclaveReport memory localEnclaveReport,
69:             bytes memory signedQuoteData, // concatenation of header and local enclave report bytes
70:             V3Struct.ECDSAQuoteV3AuthData memory authDataV3
71:         )

133:     function parseEnclaveReport(bytes memory rawEnclaveReport)
134:         internal
135:         pure
136:         returns (V3Struct.EnclaveReport memory enclaveReport)

152:     function littleEndianDecode(bytes memory encoded) private pure returns (uint256 decoded) {

165:     function parseAndVerifyHeader(bytes memory rawHeader)
166:         private
167:         pure
168:         returns (bool success, V3Struct.Header memory header)

203:     function parseAuthDataAndVerifyCertType(
204:         bytes memory rawAuthData,
205:         address pemCertLibAddr
206:     )
207:         private
208:         pure
209:         returns (bool success, V3Struct.ECDSAQuoteV3AuthData memory authDataV3)

244:     function packQEReport(V3Struct.EnclaveReport memory enclaveReport)
245:         internal
246:         pure
247:         returns (bytes memory packedQEReport)

267:     function parseCerificationChainBytes(
268:         bytes memory certBytes,
269:         address pemCertLibAddr
270:     )
271:         internal
272:         pure
273:         returns (bytes[3] memory certChainData)
```

- *Asn1Decode.sol* ( [14-14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L14-L14), [19-19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L19-L19), [24-24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L24-L24), [29-29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L29-L29), [47-47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L47-L47), [56-56](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L56-L56), [66-66](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L66-L66), [77-77](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L77-L77), [87-87](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L87-L87), [98-98](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L98-L98), [111-111](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L111-L111), [121-121](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L121-L121), [131-131](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L131-L131), [141-141](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L141-L141), [154-154](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L154-L154), [165-165](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L165-L165), [169-169](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L169-L169), [179-179](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L179-L179) ):

```solidity
14:     function ixs(uint256 self) internal pure returns (uint256) {

19:     function ixf(uint256 self) internal pure returns (uint256) {

24:     function ixl(uint256 self) internal pure returns (uint256) {

29:     function getPtr(uint256 _ixs, uint256 _ixf, uint256 _ixl) internal pure returns (uint256) {

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

- *BytesUtils.sol* ( [16-23](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L16-L23), [39-39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L39-L39), [56-66](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L56-L66), [116-125](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L116-L125), [138-146](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L138-L146), [160-167](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L160-L167), [178-178](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L178-L178), [188-188](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L188-L188), [198-198](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L198-L198), [211-211](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L211-L211), [224-224](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L224-L224), [237-237](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L237-L237), [255-262](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L255-L262), [272-272](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L272-L272), [284-291](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L284-L291), [320-327](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L320-L327), [371-371](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L371-L371) ):

```solidity
16:     function keccak(
17:         bytes memory self,
18:         uint256 offset,
19:         uint256 len
20:     )
21:         internal
22:         pure
23:         returns (bytes32 ret)

39:     function compare(bytes memory self, bytes memory other) internal pure returns (int256) {

56:     function compare(
57:         bytes memory self,
58:         uint256 offset,
59:         uint256 len,
60:         bytes memory other,
61:         uint256 otheroffset,
62:         uint256 otherlen
63:     )
64:         internal
65:         pure
66:         returns (int256)

116:     function equals(
117:         bytes memory self,
118:         uint256 offset,
119:         bytes memory other,
120:         uint256 otherOffset,
121:         uint256 len
122:     )
123:         internal
124:         pure
125:         returns (bool)

138:     function equals(
139:         bytes memory self,
140:         uint256 offset,
141:         bytes memory other,
142:         uint256 otherOffset
143:     )
144:         internal
145:         pure
146:         returns (bool)

160:     function equals(
161:         bytes memory self,
162:         uint256 offset,
163:         bytes memory other
164:     )
165:         internal
166:         pure
167:         returns (bool)

178:     function equals(bytes memory self, bytes memory other) internal pure returns (bool) {

188:     function readUint8(bytes memory self, uint256 idx) internal pure returns (uint8 ret) {

198:     function readUint16(bytes memory self, uint256 idx) internal pure returns (uint16 ret) {

211:     function readUint32(bytes memory self, uint256 idx) internal pure returns (uint32 ret) {

224:     function readBytes32(bytes memory self, uint256 idx) internal pure returns (bytes32 ret) {

237:     function readBytes20(bytes memory self, uint256 idx) internal pure returns (bytes20 ret) {

255:     function readBytesN(
256:         bytes memory self,
257:         uint256 idx,
258:         uint256 len
259:     )
260:         internal
261:         pure
262:         returns (bytes32 ret)

272:     function memcpy(uint256 dest, uint256 src, uint256 len) private pure {

284:     function substring(
285:         bytes memory self,
286:         uint256 offset,
287:         uint256 len
288:     )
289:         internal
290:         pure
291:         returns (bytes memory)

320:     function base32HexDecodeWord(
321:         bytes memory self,
322:         uint256 off,
323:         uint256 len
324:     )
325:         internal
326:         pure
327:         returns (bytes32)

371:     function compareBytes(bytes memory a, bytes memory b) internal pure returns (bool) {
```

- *RsaVerify.sol* ( [43-51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L43-L51), [191-199](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L191-L199), [212-220](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L212-L220), [307-315](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L307-L315) ):

```solidity
43:     function pkcs1Sha256(
44:         bytes32 _sha256,
45:         bytes memory _s,
46:         bytes memory _e,
47:         bytes memory _m
48:     )
49:         internal
50:         view
51:         returns (bool)

191:     function pkcs1Sha256Raw(
192:         bytes memory _data,
193:         bytes memory _s,
194:         bytes memory _e,
195:         bytes memory _m
196:     )
197:         internal
198:         view
199:         returns (bool)

212:     function pkcs1Sha1(
213:         bytes20 _sha1,
214:         bytes memory _s,
215:         bytes memory _e,
216:         bytes memory _m
217:     )
218:         internal
219:         view
220:         returns (bool)

307:     function pkcs1Sha1Raw(
308:         bytes memory _data,
309:         bytes memory _s,
310:         bytes memory _e,
311:         bytes memory _m
312:     )
313:         internal
314:         view
315:         returns (bool)
```

- *SHA1.sol* ( [11-11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SHA1.sol#L11-L11) ):

```solidity
11:     function sha1(bytes memory data) internal pure returns (bytes20 ret) {
```

- *X509DateUtils.sol* ( [8-8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L8-L8), [34-44](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L34-L44), [71-71](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L71-L71) ):

```solidity
8:     function toTimestamp(bytes memory x509Time) internal pure returns (uint256) {

34:     function toUnixTimestamp(
35:         uint16 year,
36:         uint8 month,
37:         uint8 day,
38:         uint8 hour,
39:         uint8 minute,
40:         uint8 second
41:     )
42:         internal
43:         pure
44:         returns (uint256)

71:     function isLeapYear(uint16 year) internal pure returns (bool) {
```

- *Lib4844.sol* ( [30-39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/Lib4844.sol#L30-L39) ):

```solidity
30:     function evaluatePoint(
31:         bytes32 _blobHash,
32:         uint256 _x,
33:         uint256 _y,
34:         bytes1[48] memory _commitment,
35:         bytes1[48] memory _pointProof
36:     )
37:         internal
38:         view
39:     {
```

- *LibAddress.sol* ( [22-22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L22-L22), [42-42](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L42-L42), [46-52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L46-L52), [61-68](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L61-L68), [77-77](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L77-L77) ):

```solidity
22:     function sendEther(address _to, uint256 _amount, uint256 _gasLimit) internal {

42:     function sendEther(address _to, uint256 _amount) internal {

46:     function supportsInterface(
47:         address _addr,
48:         bytes4 _interfaceId
49:     )
50:         internal
51:         view
52:         returns (bool result_)

61:     function isValidSignature(
62:         address _addr,
63:         bytes32 _hash,
64:         bytes memory _sig
65:     )
66:         internal
67:         view
68:         returns (bool)

77:     function isSenderEOA() internal view returns (bool) {
```

- *LibMath.sol* ( [12-12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibMath.sol#L12-L12), [20-20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibMath.sol#L20-L20) ):

```solidity
12:     function min(uint256 _a, uint256 _b) internal pure returns (uint256) {

20:     function max(uint256 _a, uint256 _b) internal pure returns (uint256) {
```

- *LibTrieProof.sol* ( [34-44](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibTrieProof.sol#L34-L44) ):

```solidity
34:     function verifyMerkleProof(
35:         bytes32 _rootHash,
36:         address _addr,
37:         bytes32 _slot,
38:         bytes32 _value,
39:         bytes[] memory _accountProof,
40:         bytes[] memory _storageProof
41:     )
42:         internal
43:         pure
44:         returns (bytes32 storageRoot_)
```

- *ExcessivelySafeCall.sol* ( [25-33](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L25-L33) ):

```solidity
25:     function excessivelySafeCall(
26:         address _target,
27:         uint256 _gas,
28:         uint256 _value,
29:         uint16 _maxCopy,
30:         bytes memory _calldata
31:     )
32:         internal
33:         returns (bool, bytes memory)
```

- *Bytes.sol* ( [15-22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L15-L22), [91-91](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L91-L91), [102-102](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L102-L102), [149-149](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L149-L149) ):

```solidity
15:     function slice(
16:         bytes memory _bytes,
17:         uint256 _start,
18:         uint256 _length
19:     )
20:         internal
21:         pure
22:         returns (bytes memory)

91:     function slice(bytes memory _bytes, uint256 _start) internal pure returns (bytes memory) {

102:     function toNibbles(bytes memory _bytes) internal pure returns (bytes memory) {

149:     function equal(bytes memory _bytes, bytes memory _other) internal pure returns (bool) {
```

- *RLPReader.sol* ( [35-35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L35-L35), [53-53](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L53-L53), [102-102](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L102-L102), [109-109](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L109-L109), [128-128](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L128-L128), [135-135](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L135-L135) ):

```solidity
35:     function toRLPItem(bytes memory _in) internal pure returns (RLPItem memory out_) {

53:     function readList(RLPItem memory _in) internal pure returns (RLPItem[] memory out_) {

102:     function readList(bytes memory _in) internal pure returns (RLPItem[] memory out_) {

109:     function readBytes(RLPItem memory _in) internal pure returns (bytes memory out_) {

128:     function readBytes(bytes memory _in) internal pure returns (bytes memory out_) {

135:     function readRawBytes(RLPItem memory _in) internal pure returns (bytes memory out_) {
```

- *RLPWriter.sol* ( [13-13](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L13-L13), [24-24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L24-L24) ):

```solidity
13:     function writeBytes(bytes memory _in) internal pure returns (bytes memory out_) {

24:     function writeUint(uint256 _in) internal pure returns (bytes memory out_) {
```

- *MerkleTrie.sol* ( [50-58](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L50-L58), [68-75](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L68-L75) ):

```solidity
50:     function verifyInclusionProof(
51:         bytes memory _key,
52:         bytes memory _value,
53:         bytes[] memory _proof,
54:         bytes32 _root
55:     )
56:         internal
57:         pure
58:         returns (bool valid_)

68:     function get(
69:         bytes memory _key,
70:         bytes[] memory _proof,
71:         bytes32 _root
72:     )
73:         internal
74:         pure
75:         returns (bytes memory value_)
```

- *SecureMerkleTrie.sol* ( [19-27](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L19-L27), [38-45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L38-L45) ):

```solidity
19:     function verifyInclusionProof(
20:         bytes memory _key,
21:         bytes memory _value,
22:         bytes[] memory _proof,
23:         bytes32 _root
24:     )
25:         internal
26:         pure
27:         returns (bool valid_)

38:     function get(
39:         bytes memory _key,
40:         bytes[] memory _proof,
41:         bytes32 _root
42:     )
43:         internal
44:         pure
45:         returns (bytes memory value_)
```

- *LibFixedPointMath.sol* ( [13-13](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L13-L13) ):

```solidity
13:     function exp(int256 x) internal pure returns (int256 r) {
```

- *BaseVault.sol* ( [47-51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L47-L51), [58-62](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L58-L62) ):

```solidity
47:     function checkProcessMessageContext()
48:         internal
49:         view
50:         onlyFromBridge
51:         returns (IBridge.Context memory ctx_)

58:     function checkRecallMessageContext()
59:         internal
60:         view
61:         onlyFromBridge
62:         returns (IBridge.Context memory ctx_)
```

- *LibBridgedToken.sol* ( [11-19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L11-L19), [28-34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L28-L34), [39-39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L39-L39), [43-49](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L43-L49) ):

```solidity
11:     function validateInputs(
12:         address _srcToken,
13:         uint256 _srcChainId,
14:         string memory _symbol,
15:         string memory _name
16:     )
17:         internal
18:         view
19:     {

28:     function buildName(
29:         string memory _name,
30:         uint256 _srcChainId
31:     )
32:         internal
33:         pure
34:         returns (string memory)

39:     function buildSymbol(string memory _symbol) internal pure returns (string memory) {

43:     function buildURI(
44:         address _srcToken,
45:         uint256 _srcChainId
46:     )
47:         internal
48:         pure
49:         returns (string memory)
```

</details>

### [N-08] Names of `private`/`internal` state variables should be prefixed with an underscore

It is recommended by the [Solidity Style Guide](https://docs.soliditylang.org/en/v0.8.20/style-guide.html#underscore-prefix-for-non-external-functions-and-variables).

<details>
<summary>There are 18 instances (click to show):</summary>

- *AutomataDcapV3Attestation.sol* ( [29-29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L29-L29), [33-34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L33-L34), [36-36](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L36-L36) ):

```solidity
29:     uint256 internal constant CPUSVN_LENGTH = 16;

33:     bytes32 internal constant ROOTCA_PUBKEY_HASH =
34:         0x89f72d7c488e5b53a77c23ebcb36970ef7eb5bcf6658e9b8292cfbe4703a8473;

36:     uint8 internal constant INVALID_EXIT_CODE = 255;
```

- *PEMCertChainLib.sol* ( [17-17](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L17-L17), [18-18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L18-L18), [19-19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L19-L19), [20-20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L20-L20), [22-22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L22-L22), [23-23](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L23-L23), [24-24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L24-L24), [25-25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L25-L25), [26-26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L26-L26), [27-27](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L27-L27), [28-28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L28-L28), [29-29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L29-L29), [32-32](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L32-L32) ):

```solidity
17:     string internal constant HEADER = "-----BEGIN CERTIFICATE-----";

18:     string internal constant FOOTER = "-----END CERTIFICATE-----";

19:     uint256 internal constant HEADER_LENGTH = 27;

20:     uint256 internal constant FOOTER_LENGTH = 25;

22:     string internal constant PCK_COMMON_NAME = "Intel SGX PCK Certificate";

23:     string internal constant PLATFORM_ISSUER_NAME = "Intel SGX PCK Platform CA";

24:     string internal constant PROCESSOR_ISSUER_NAME = "Intel SGX PCK Processor CA";

25:     bytes internal constant SGX_EXTENSION_OID = hex"2A864886F84D010D01";

26:     bytes internal constant TCB_OID = hex"2A864886F84D010D0102";

27:     bytes internal constant PCESVN_OID = hex"2A864886F84D010D010211";

28:     bytes internal constant PCEID_OID = hex"2A864886F84D010D0103";

29:     bytes internal constant FMSPC_OID = hex"2A864886F84D010D0104";

32:     uint256 constant SGX_TCB_CPUSVN_SIZE = 16;
```

- *SigVerifyLib.sol* ( [18-18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L18-L18) ):

```solidity
18:     address private ES256VERIFIER;
```

- *Bridge.sol* ( [27-27](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L27-L27) ):

```solidity
27:     uint256 internal constant PLACEHOLDER = type(uint256).max;
```

</details>

### [N-09] Order of functions does not follow the Solidity Style Guide

According to the [Solidity Style Guide](https://docs.soliditylang.org/en/v0.8.20/style-guide.html#order-of-functions), functions should be grouped according to their visibility and ordered: `constructor`, `receive`, `fallback`, `external`, `public`, `internal`, `private`. Within a grouping, place the view and pure functions last.

<details>
<summary>There are 29 instances (click to show):</summary>

- *TaikoGovernor.sol* ( [127-136](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L127-L136), [140-148](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L140-L148) ):

```solidity
/// @audit ↓↓ Out of order with `_cancel()`
127:     function _execute(
128:         uint256 _proposalId,
129:         address[] memory _targets,
130:         uint256[] memory _values,
131:         bytes[] memory _calldatas,
132:         bytes32 _descriptionHash
133:     )
134:         internal
135:         override(GovernorUpgradeable, GovernorTimelockControlUpgradeable)
136:     {

/// @audit ↑↑ Out of order with `_execute()`
140:     function _cancel(
141:         address[] memory _targets,
142:         uint256[] memory _values,
143:         bytes[] memory _calldatas,
144:         bytes32 _descriptionHash
145:     )
146:         internal
147:         override(GovernorUpgradeable, GovernorTimelockControlUpgradeable)
148:         returns (uint256)
```

- *Guardians.sol* ( [111-111](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L111-L111), [124-124](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L124-L124) ):

```solidity
/// @audit ↓↓ Out of order with `deleteApproval()`
111:     function approve(uint256 _operationId, bytes32 _hash) internal returns (bool approved_) {

/// @audit ↑↑ Out of order with `approve()`
124:     function deleteApproval(bytes32 _hash) internal {
```

- *AutomataDcapV3Attestation.sol* ( [103-109](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L103-L109), [114-117](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L114-L117), [126-130](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L126-L130), [138-138](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L138-L138), [303-311](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L303-L311), [355-359](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L355-L359) ):

```solidity
/// @audit ↓↓ Out of order with `configureQeIdentityJson()`
103:     function configureTcbInfoJson(
104:         string calldata fmspc,
105:         TCBInfoStruct.TCBInfo calldata tcbInfoInput
106:     )
107:         public
108:         onlyOwner
109:     {

/// @audit ↑↑ Out of order with `configureTcbInfoJson()`
114:     function configureQeIdentityJson(EnclaveIdStruct.EnclaveId calldata qeIdentityInput)
115:         external
116:         onlyOwner
117:     {

/// @audit ↓↓ Out of order with `verifyAttestation()`
126:     function _attestationTcbIsValid(TCBInfoStruct.TCBStatus status)
127:         internal
128:         pure
129:         virtual
130:         returns (bool valid)

/// @audit ↑↑ Out of order with `_attestationTcbIsValid()`
138:     function verifyAttestation(bytes calldata data) external view override returns (bool) {

/// @audit ↓↓ Out of order with `verifyParsedQuote()`
303:     function _enclaveReportSigVerification(
304:         bytes memory pckCertPubKey,
305:         bytes memory signedQuoteData,
306:         V3Struct.ECDSAQuoteV3AuthData memory authDataV3,
307:         V3Struct.EnclaveReport memory qeEnclaveReport
308:     )
309:         private
310:         view
311:         returns (bool)

/// @audit ↑↑ Out of order with `_enclaveReportSigVerification()`
355:     function verifyParsedQuote(V3Struct.ParsedV3QuoteStruct calldata v3quote)
356:         external
357:         view
358:         override
359:         returns (bool, bytes memory)
```

- *V3Parser.sol* ( [203-209](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L203-L209), [244-247](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L244-L247) ):

```solidity
/// @audit ↓↓ Out of order with `packQEReport()`
203:     function parseAuthDataAndVerifyCertType(
204:         bytes memory rawAuthData,
205:         address pemCertLibAddr
206:     )
207:         private
208:         pure
209:         returns (bool success, V3Struct.ECDSAQuoteV3AuthData memory authDataV3)

/// @audit ↑↑ Out of order with `parseAuthDataAndVerifyCertType()`
244:     function packQEReport(V3Struct.EnclaveReport memory enclaveReport)
245:         internal
246:         pure
247:         returns (bytes memory packedQEReport)
```

- *BytesUtils.sol* ( [272-272](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L272-L272), [284-291](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L284-L291) ):

```solidity
/// @audit ↓↓ Out of order with `substring()`
272:     function memcpy(uint256 dest, uint256 src, uint256 len) private pure {

/// @audit ↑↑ Out of order with `memcpy()`
284:     function substring(
285:         bytes memory self,
286:         uint256 offset,
287:         uint256 len
288:     )
289:         internal
290:         pure
291:         returns (bytes memory)
```

- *Bridge.sol* ( [477-483](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L477-L483), [515-515](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L515-L515), [529-529](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L529-L529), [541-541](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L541-L541) ):

```solidity
/// @audit ↓↓ Out of order with `_updateMessageStatus()`
477:     function _invokeMessageCall(
478:         Message calldata _message,
479:         bytes32 _msgHash,
480:         uint256 _gasLimit
481:     )
482:         private
483:         returns (bool success_)

/// @audit ↑↑ Out of order with `_invokeMessageCall()`
515:     function _updateMessageStatus(bytes32 _msgHash, Status _status) private {

/// @audit ↑↑ Out of order with `_updateMessageStatus()`
529:     function _resetContext() private {

/// @audit ↑↑ Out of order with `_resetContext()`
541:     function _storeContext(bytes32 _msgHash, address _from, uint64 _srcChainId) private {
```

- *EssentialContract.sol* ( [95-102](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L95-L102), [109-109](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L109-L109), [114-114](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L114-L114), [116-116](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L116-L116), [119-119](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L119-L119) ):

```solidity
/// @audit ↓↓ Out of order with `__Essential_init()`
95:     function __Essential_init(
96:         address _owner,
97:         address _addressManager
98:     )
99:         internal
100:         virtual
101:         onlyInitializing
102:     {

/// @audit ↑↑ Out of order with `__Essential_init()`
109:     function __Essential_init(address _owner) internal virtual {

/// @audit ↑↑ Out of order with `__Essential_init()`
114:     function _authorizeUpgrade(address) internal virtual override onlyOwner { }

/// @audit ↑↑ Out of order with `_authorizeUpgrade()`
116:     function _authorizePause(address) internal virtual onlyOwner { }

/// @audit ↑↑ Out of order with `_authorizePause()`
119:     function _storeReentryLock(uint8 _reentry) internal virtual {
```

- *SignalService.sol* ( [235-242](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L235-L242), [253-262](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L253-L262), [271-280](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L271-L280) ):

```solidity
/// @audit ↓↓ Out of order with `_sendSignal()`
235:     function _syncChainData(
236:         uint64 _chainId,
237:         bytes32 _kind,
238:         uint64 _blockId,
239:         bytes32 _chainData
240:     )
241:         private
242:         returns (bytes32 signal_)

/// @audit ↑↑ Out of order with `_syncChainData()`
253:     function _sendSignal(
254:         address _app,
255:         bytes32 _signal,
256:         bytes32 _value
257:     )
258:         private
259:         validSender(_app)
260:         nonZeroValue(_signal)
261:         nonZeroValue(_value)
262:         returns (bytes32 slot_)

/// @audit ↑↑ Out of order with `_sendSignal()`
271:     function _cacheChainData(
272:         HopProof memory _hop,
273:         uint64 _chainId,
274:         uint64 _blockId,
275:         bytes32 _signalRoot,
276:         bool _isFullProof,
277:         bool _isLastHop
278:     )
279:         private
280:     {
```

- *TimelockTokenPool.sol* ( [208-208](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L208-L208), [225-225](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L225-L225) ):

```solidity
/// @audit ↓↓ Out of order with `_voidGrant()`
208:     function _withdraw(address _recipient, address _to) private {

/// @audit ↑↑ Out of order with `_withdraw()`
225:     function _voidGrant(Grant storage _grant) private returns (uint128 amountVoided) {
```

- *BridgedERC20.sol* ( [129-129](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L129-L129), [133-133](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L133-L133), [139-146](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L139-L146), [152-159](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L152-L159), [163-169](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L163-L169), [173-179](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L173-L179) ):

```solidity
/// @audit ↓↓ Out of order with `_burnToken()`
129:     function _mintToken(address _account, uint256 _amount) internal override {

/// @audit ↑↑ Out of order with `_mintToken()`
133:     function _burnToken(address _from, uint256 _amount) internal override {

/// @audit ↑↑ Out of order with `_burnToken()`
139:     function _beforeTokenTransfer(
140:         address _from,
141:         address _to,
142:         uint256 _amount
143:     )
144:         internal
145:         override(ERC20Upgradeable, ERC20SnapshotUpgradeable)
146:     {

/// @audit ↑↑ Out of order with `_beforeTokenTransfer()`
152:     function _afterTokenTransfer(
153:         address _from,
154:         address _to,
155:         uint256 _amount
156:     )
157:         internal
158:         override(ERC20Upgradeable, ERC20VotesUpgradeable)
159:     {

/// @audit ↑↑ Out of order with `_afterTokenTransfer()`
163:     function _mint(
164:         address _to,
165:         uint256 _amount
166:     )
167:         internal
168:         override(ERC20Upgradeable, ERC20VotesUpgradeable)
169:     {

/// @audit ↑↑ Out of order with `_mint()`
173:     function _burn(
174:         address _from,
175:         uint256 _amount
176:     )
177:         internal
178:         override(ERC20Upgradeable, ERC20VotesUpgradeable)
179:     {
```

- *BridgedERC20Base.sol* ( [97-97](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L97-L97), [99-99](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L99-L99) ):

```solidity
/// @audit ↓↓ Out of order with `_burnToken()`
97:     function _mintToken(address _account, uint256 _amount) internal virtual;

/// @audit ↑↑ Out of order with `_mintToken()`
99:     function _burnToken(address _from, uint256 _amount) internal virtual;
```

- *ERC1155Vault.sol* ( [214-221](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L214-L221), [240-245](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L240-L245), [288-290](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L288-L290), [303-303](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L303-L303) ):

```solidity
/// @audit ↓↓ Out of order with `_handleMessage()`
214:     function _transferTokens(
215:         CanonicalNFT memory ctoken,
216:         address to,
217:         uint256[] memory tokenIds,
218:         uint256[] memory amounts
219:     )
220:         private
221:         returns (address token)

/// @audit ↑↑ Out of order with `_transferTokens()`
240:     function _handleMessage(
241:         address _user,
242:         BridgeTransferOp memory _op
243:     )
244:         private
245:         returns (bytes memory msgData_, CanonicalNFT memory ctoken_)

/// @audit ↑↑ Out of order with `_handleMessage()`
288:     function _getOrDeployBridgedToken(CanonicalNFT memory _ctoken)
289:         private
290:         returns (address btoken_)

/// @audit ↑↑ Out of order with `_getOrDeployBridgedToken()`
303:     function _deployBridgedToken(CanonicalNFT memory _ctoken) private returns (address btoken_) {
```

- *ERC721Vault.sol* ( [160-166](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L160-L166), [187-192](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L187-L192), [224-226](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L224-L226), [240-240](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L240-L240) ):

```solidity
/// @audit ↓↓ Out of order with `_handleMessage()`
160:     function _transferTokens(
161:         CanonicalNFT memory _ctoken,
162:         address _to,
163:         uint256[] memory _tokenIds
164:     )
165:         private
166:         returns (address token_)

/// @audit ↑↑ Out of order with `_transferTokens()`
187:     function _handleMessage(
188:         address _user,
189:         BridgeTransferOp memory _op
190:     )
191:         private
192:         returns (bytes memory msgData_, CanonicalNFT memory ctoken_)

/// @audit ↑↑ Out of order with `_handleMessage()`
224:     function _getOrDeployBridgedToken(CanonicalNFT memory _ctoken)
225:         private
226:         returns (address btoken_)

/// @audit ↑↑ Out of order with `_getOrDeployBridgedToken()`
240:     function _deployBridgedToken(CanonicalNFT memory _ctoken) private returns (address btoken_) {
```

</details>

### [N-10] The `nonReentrant` `modifier` should occur before all other modifiers

This is a best-practice to protect against reentrancy in other modifiers

<details>
<summary>There are 4 instances (click to show):</summary>

- *GuardianProver.sol* ( [35-42](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/GuardianProver.sol#L35-L42) ):

```solidity
35:     function approve(
36:         TaikoData.BlockMetadata calldata _meta,
37:         TaikoData.Transition calldata _tran,
38:         TaikoData.TierProof calldata _proof
39:     )
40:         external
41:         whenNotPaused
42:         nonReentrant
```

- *Guardians.sol* ( [53-59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L53-L59) ):

```solidity
53:     function setGuardians(
54:         address[] memory _newGuardians,
55:         uint8 _minGuardians
56:     )
57:         external
58:         onlyOwner
59:         nonReentrant
```

- *TaikoL2.sol* ( [163-169](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L163-L169) ):

```solidity
163:     function withdraw(
164:         address _token,
165:         address _to
166:     )
167:         external
168:         onlyFromOwnerOrNamed("withdrawer")
169:         nonReentrant
```

- *Bridge.sol* ( [101-107](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L101-L107) ):

```solidity
101:     function banAddress(
102:         address _addr,
103:         bool _ban
104:     )
105:         external
106:         onlyFromOwnerOrNamed("bridge_watchdog")
107:         nonReentrant
```

</details>

### [N-11] Redundant inheritance specifier

The contracts below already extend the specified contract, so there is no need to list it in the inheritance list again.

There are 3 instances:

- *TaikoGovernor.sol* ( [16-21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L16-L21) ):

```solidity
/// @audit GovernorVotesQuorumFractionUpgradeable already extends GovernorVotesUpgradeable
16: contract TaikoGovernor is
17:     EssentialContract,
18:     GovernorCompatibilityBravoUpgradeable,
19:     GovernorVotesUpgradeable,
20:     GovernorVotesQuorumFractionUpgradeable,
21:     GovernorTimelockControlUpgradeable
```

- *BridgedERC1155.sol* ( [14-14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L14-L14) ):

```solidity
/// @audit ERC1155Upgradeable already extends IERC1155MetadataURIUpgradeable
14: contract BridgedERC1155 is EssentialContract, IERC1155MetadataURIUpgradeable, ERC1155Upgradeable {
```

- *BridgedERC20.sol* ( [15-19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L15-L19) ):

```solidity
/// @audit ERC20SnapshotUpgradeable already extends IERC20MetadataUpgradeable
15: contract BridgedERC20 is
16:     BridgedERC20Base,
17:     IERC20MetadataUpgradeable,
18:     ERC20SnapshotUpgradeable,
19:     ERC20VotesUpgradeable
```

### [N-12] Use of `override` is unnecessary

[Starting from Solidity 0.8.8](https://docs.soliditylang.org/en/v0.8.20/contracts.html#function-overriding), the override keyword is not required when overriding an interface function, except for the case where the function is defined in multiple bases.

<details>
<summary>There are 43 instances (click to show):</summary>

- *TaikoL1.sol* ( [124-124](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L124-L124), [186-186](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L186-L186), [220-226](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L220-L226) ):

```solidity
124:     function unpause() public override {

186:     function getConfig() public view virtual override returns (TaikoData.Config memory) {

220:     function _authorizePause(address)
221:         internal
222:         view
223:         virtual
224:         override
225:         onlyFromOwnerOrNamed("chain_pauser")
226:     { }
```

- *TaikoToken.sol* ( [60-60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L60-L60), [70-77](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L70-L77) ):

```solidity
60:     function transfer(address _to, uint256 _amount) public override returns (bool) {

70:     function transferFrom(
71:         address _from,
72:         address _to,
73:         uint256 _amount
74:     )
75:         public
76:         override
77:         returns (bool)
```

- *TaikoGovernor.sol* ( [111-111](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L111-L111), [117-117](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L117-L117), [123-123](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L123-L123) ):

```solidity
111:     function votingDelay() public pure override returns (uint256) {

117:     function votingPeriod() public pure override returns (uint256) {

123:     function proposalThreshold() public pure override returns (uint256) {
```

- *TaikoTimelockController.sol* ( [24-24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L24-L24) ):

```solidity
24:     function getMinDelay() public view override returns (uint256) {
```

- *DevnetTierProvider.sol* ( [20-20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L20-L20), [47-47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L47-L47), [54-54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L54-L54) ):

```solidity
20:     function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {

47:     function getTierIds() public pure override returns (uint16[] memory tiers_) {

54:     function getMinTier(uint256) public pure override returns (uint16) {
```

- *MainnetTierProvider.sol* ( [20-20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L20-L20), [58-58](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L58-L58), [66-66](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L66-L66) ):

```solidity
20:     function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {

58:     function getTierIds() public pure override returns (uint16[] memory tiers_) {

66:     function getMinTier(uint256 _rand) public pure override returns (uint16) {
```

- *TestnetTierProvider.sol* ( [20-20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L20-L20), [58-58](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L58-L58), [66-66](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L66-L66) ):

```solidity
20:     function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {

58:     function getTierIds() public pure override returns (uint16[] memory tiers_) {

66:     function getMinTier(uint256 _rand) public pure override returns (uint16) {
```

- *TaikoL2EIP1559Configurable.sol* ( [43-43](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L43-L43) ):

```solidity
43:     function getConfig() public view override returns (Config memory) {
```

- *AutomataDcapV3Attestation.sol* ( [138-138](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L138-L138), [355-359](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L355-L359) ):

```solidity
138:     function verifyAttestation(bytes calldata data) external view override returns (bool) {

355:     function verifyParsedQuote(V3Struct.ParsedV3QuoteStruct calldata v3quote)
356:         external
357:         view
358:         override
359:         returns (bool, bytes memory)
```

- *Bridge.sol* ( [115-121](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L115-L121), [461-467](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L461-L467) ):

```solidity
115:     function sendMessage(Message calldata _message)
116:         external
117:         payable
118:         override
119:         nonReentrant
120:         whenNotPaused
121:         returns (bytes32 msgHash_, Message memory message_)

461:     function _authorizePause(address)
462:         internal
463:         view
464:         virtual
465:         override
466:         onlyFromOwnerOrNamed("bridge_pauser")
467:     { }
```

- *AddressManager.sol* ( [54-54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L54-L54), [58-58](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L58-L58) ):

```solidity
54:     function getAddress(uint64 _chainId, bytes32 _name) public view override returns (address) {

58:     function _authorizePause(address) internal pure override {
```

- *EssentialContract.sol* ( [114-114](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L114-L114) ):

```solidity
114:     function _authorizeUpgrade(address) internal virtual override onlyOwner { }
```

- *SignalService.sol* ( [231-231](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L231-L231) ):

```solidity
231:     function _authorizePause(address) internal pure override {
```

- *BaseVault.sol* ( [39-39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L39-L39) ):

```solidity
39:     function supportsInterface(bytes4 _interfaceId) public view virtual override returns (bool) {
```

- *BridgedERC1155.sol* ( [125-136](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L125-L136) ):

```solidity
125:     function _beforeTokenTransfer(
126:         address, /*_operator*/
127:         address, /*_from*/
128:         address _to,
129:         uint256[] memory, /*_ids*/
130:         uint256[] memory, /*_amounts*/
131:         bytes memory /*_data*/
132:     )
133:         internal
134:         virtual
135:         override
136:     {
```

- *BridgedERC20.sol* ( [129-129](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L129-L129), [133-133](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L133-L133) ):

```solidity
129:     function _mintToken(address _account, uint256 _amount) internal override {

133:     function _burnToken(address _from, uint256 _amount) internal override {
```

- *BridgedERC721.sol* ( [87-87](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L87-L87), [93-93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L93-L93), [107-107](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L107-L107), [115-124](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L115-L124) ):

```solidity
87:     function name() public view override(ERC721Upgradeable) returns (string memory) {

93:     function symbol() public view override(ERC721Upgradeable) returns (string memory) {

107:     function tokenURI(uint256 _tokenId) public view virtual override returns (string memory) {

115:     function _beforeTokenTransfer(
116:         address, /*_from*/
117:         address _to,
118:         uint256, /*_firstTokenId*/
119:         uint256 /*_batchSize*/
120:     )
121:         internal
122:         virtual
123:         override
124:     {
```

- *ERC1155Vault.sol* ( [127-136](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L127-L136), [204-204](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L204-L204) ):

```solidity
127:     function onMessageRecalled(
128:         IBridge.Message calldata message,
129:         bytes32 msgHash
130:     )
131:         external
132:         payable
133:         override
134:         nonReentrant
135:         whenNotPaused
136:     {

204:     function name() public pure override returns (bytes32) {
```

- *ERC20Vault.sol* ( [285-294](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L285-L294), [316-316](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L316-L316) ):

```solidity
285:     function onMessageRecalled(
286:         IBridge.Message calldata _message,
287:         bytes32 _msgHash
288:     )
289:         external
290:         payable
291:         override
292:         nonReentrant
293:         whenNotPaused
294:     {

316:     function name() public pure override returns (bytes32) {
```

- *ERC721Vault.sol* ( [110-119](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L110-L119), [156-156](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L156-L156) ):

```solidity
110:     function onMessageRecalled(
111:         IBridge.Message calldata _message,
112:         bytes32 _msgHash
113:     )
114:         external
115:         payable
116:         override
117:         nonReentrant
118:         whenNotPaused
119:     {

156:     function name() public pure override returns (bytes32) {
```

- *USDCAdapter.sol* ( [43-43](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L43-L43), [47-47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L47-L47) ):

```solidity
43:     function _mintToken(address _account, uint256 _amount) internal override {

47:     function _burnToken(address _from, uint256 _amount) internal override {
```

</details>

### [N-13] Unused errors

The following `error`s are defined but not used. It is recommended to check the code for logical omissions that cause them not to be used. If it's determined that they are not needed anywhere, it's best to remove them from the codebase to improve code clarity and minimize confusion.
Note that there may be cases where an error appears to be used because it has multiple definitions in different files. In such cases, the definitions should be moved to a separate file.

There is 1 instance:

- *TaikoErrors.sol* ( [36-36](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L36-L36) ):

```solidity
36:     error L1_TOO_MANY_TIERS();
```

### [N-14] Unused `struct`s

Note that there may be cases where a struct superficially appears to be used, but this is only because there are multiple definitions of the struct in different files. In such cases, the struct definition should be moved into a separate file. The instances below are the unused definitions.

There is 1 instance:

- *ISigVerifyLib.sol* ( [24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L24) ):

```solidity
24:     struct Certificate {
```

### [N-15] Custom errors should be used rather than `revert()`/`require()`

Custom errors are available from solidity version 0.8.4. Custom errors are more easily processed in try-catch blocks, and are easier to re-use and maintain.

<details>
<summary>There are 66 instances (click to show):</summary>

- *AutomataDcapV3Attestation.sol* ( [61-61](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L61-L61) ):

```solidity
61:         require(msg.sender == owner, "onlyOwner");
```

- *V3Parser.sol* ( [77-81](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L77-L81), [82-86](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L82-L86), [87-90](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L87-L90), [91-93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L91-L93), [94-99](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L94-L99), [100-104](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L100-L104), [116-116](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L116-L116), [279-279](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L279-L279) ):

```solidity
77:         require(
78:             localEnclaveReport.reserved3.length == 96 && localEnclaveReport.reserved4.length == 60
79:                 && localEnclaveReport.reportData.length == 64,
80:             "local QE report has wrong length"
81:         );

82:         require(
83:             pckSignedQeReport.reserved3.length == 96 && pckSignedQeReport.reserved4.length == 60
84:                 && pckSignedQeReport.reportData.length == 64,
85:             "QE report has wrong length"
86:         );

87:         require(
88:             v3Quote.v3AuthData.certification.certType == 5,
89:             "certType must be 5: Concatenated PCK Cert Chain (PEM formatted)"
90:         );

91:         require(
92:             v3Quote.v3AuthData.certification.decodedCertDataArray.length == 3, "3 certs in chain"
93:         );

94:         require(
95:             v3Quote.v3AuthData.ecdsa256BitSignature.length == 64
96:                 && v3Quote.v3AuthData.ecdsaAttestationKey.length == 64
97:                 && v3Quote.v3AuthData.qeReportSignature.length == 64,
98:             "Invalid ECDSA signature format"
99:         );

100:         require(
101:             v3Quote.v3AuthData.qeAuthData.parsedDataSize
102:                 == v3Quote.v3AuthData.qeAuthData.data.length,
103:             "Invalid QEAuthData size"
104:         );

116:         require(totalQuoteSize >= MINIMUM_QUOTE_LENGTH, "Invalid quote size");

279:         require(certParsedSuccessfully, "splitCertificateChain failed");
```

- *Asn1Decode.sol* ( [57-57](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L57-L57), [67-67](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L67-L67), [88-88](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L88-L88), [142-142](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L142-L142), [143-143](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L143-L143), [155-155](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L155-L155), [156-156](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L156-L156), [180-180](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L180-L180), [182-182](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L182-L182) ):

```solidity
57:         require(der[ptr.ixs()] == 0x03, "Not type BIT STRING");

67:         require(der[ptr.ixs()] == 0x04, "Not type OCTET STRING");

88:         require(der[ptr.ixs()] & 0x20 == 0x20, "Not a constructed type");

142:         require(der[ptr.ixs()] == 0x02, "Not type INTEGER");

143:         require(der[ptr.ixf()] & 0x80 == 0, "Not positive");

155:         require(der[ptr.ixs()] == 0x02, "Not type INTEGER");

156:         require(der[ptr.ixf()] & 0x80 == 0, "Not positive");

180:         require(der[ptr.ixs()] == 0x03, "ixs Not type BIT STRING 0x03");

182:         require(der[ptr.ixf()] == 0x00, "ixf Not 0");
```

- *BytesUtils.sol* ( [25-25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L25-L25), [199-199](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L199-L199), [212-212](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L212-L212), [225-225](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L225-L225), [238-238](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L238-L238), [264-264](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L264-L264), [265-265](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L265-L265), [293-293](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L293-L293), [329-329](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L329-L329), [335-335](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L335-L335), [337-337](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L337-L337), [365-365](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L365-L365) ):

```solidity
25:         require(offset + len <= self.length, "invalid offset");

199:         require(idx + 2 <= self.length, "invalid idx");

212:         require(idx + 4 <= self.length, "unexpected idx");

225:         require(idx + 32 <= self.length, "unexpected idx");

238:         require(idx + 20 <= self.length, "unexpected idx");

264:         require(len <= 32, "unexpected len");

265:         require(idx + len <= self.length, "unexpected idx");

293:         require(offset + len <= self.length, "unexpected offset");

329:         require(len <= 52, "unexpected len");

335:             require(char >= 0x30 && char <= 0x7A, "invalid char");

337:             require(decoded <= 0x20, "invalid decoded");

365:             revert("unexpected len");
```

- *SigVerifyLib.sol* ( [50-50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L50-L50), [75-75](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L75-L75) ):

```solidity
50:             revert("Unsupported algorithm");

75:             revert("Unsupported algorithm");
```

- *Bytes.sol* ( [25-25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L25-L25), [26-26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L26-L26), [27-27](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L27-L27) ):

```solidity
25:             require(_length + 31 >= _length, "slice_overflow");

26:             require(_start + _length >= _start, "slice_overflow");

27:             require(_bytes.length >= _start + _length, "slice_outOfBounds");
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

- *MerkleTrie.sol* ( [77-77](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L77-L77), [89-89](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L89-L89), [93-96](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L93-L96), [99-102](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L99-L102), [105-108](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L105-L108), [119-122](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L119-L122), [125-128](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L125-L128), [150-153](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L150-L153), [162-165](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L162-L165), [172-175](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L172-L175), [178-181](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L178-L181), [191-191](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L191-L191), [194-194](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L194-L194), [198-198](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L198-L198) ):

```solidity
77:         require(_key.length > 0, "MerkleTrie: empty key");

89:             require(currentKeyIndex <= key.length, "MerkleTrie: key index exceeds total key length");

93:                 require(
94:                     Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
95:                     "MerkleTrie: invalid root hash"
96:                 );

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

### [N-16] Large numeric literals should use underscores for readability

Large hardcoded numbers in code can be difficult to read. Consider using underscores for number literals to improve readability (e.g `1234567` -> `1_234_567`). Consider using an underscore for every third digit from the right.

<details>
<summary>There are 18 instances (click to show):</summary>

- *TaikoL1.sol* ( [209-209](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L209-L209) ):

```solidity
209:             ethDepositRingBufferSize: 1024,
```

- *TaikoGovernor.sol* ( [112-112](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L112-L112) ):

```solidity
112:         return 7200; // 1 day
```

- *LibProposing.sol* ( [21-21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L21-L21) ):

```solidity
21:     uint256 public constant MAX_BYTES_PER_BLOB = 4096 * 32;
```

- *LibVerifying.sol* ( [251-251](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L251-L251) ):

```solidity
251:                 || _config.blockMaxTxListBytes > 128 * 1024 // calldata up to 128K
```

- *DevnetTierProvider.sol* ( [26-26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L26-L26), [38-38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L38-L38) ):

```solidity
26:                 cooldownWindow: 1440, //24 hours

38:                 provingWindow: 2880, // 48 hours
```

- *MainnetTierProvider.sol* ( [26-26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L26-L26), [37-37](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L37-L37), [49-49](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L49-L49) ):

```solidity
26:                 cooldownWindow: 1440, //24 hours

37:                 cooldownWindow: 1440, //24 hours

49:                 provingWindow: 2880, // 48 hours
```

- *TestnetTierProvider.sol* ( [26-26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L26-L26), [37-37](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L37-L37), [49-49](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L49-L49) ):

```solidity
26:                 cooldownWindow: 1440, //24 hours

37:                 cooldownWindow: 1440, //24 hours

49:                 provingWindow: 2880, // 48 hours
```

- *V3Parser.sol* ( [14-14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L14-L14) ):

```solidity
14:     uint256 internal constant MINIMUM_QUOTE_LENGTH = 1020;
```

- *X509DateUtils.sol* ( [18-18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L18-L18), [19-19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L19-L19), [48-48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L48-L48), [64-64](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L64-L64) ):

```solidity
18:             if (uint8(x509Time[0]) - 48 < 5) yrs += 2000;

19:             else yrs += 1900;

48:         for (uint16 i = 1970; i < year; ++i) {

64:         timestamp += uint256(hour) * 3600; // Hours in seconds
```

- *Lib4844.sol* ( [13-13](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/Lib4844.sol#L13-L13) ):

```solidity
13:     uint32 public constant FIELD_ELEMENTS_PER_BLOB = 4096;
```

</details>

### [N-17] Add inline comments for unnamed parameters

`function func(address a, address)` -> `function func(address a, address /* b */)`

<details>
<summary>There are 11 instances (click to show):</summary>

- *TaikoL1.sol* ( [220-220](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L220-L220) ):

```solidity
220:     function _authorizePause(address)
```

- *DevnetTierProvider.sol* ( [54-54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L54-L54) ):

```solidity
54:     function getMinTier(uint256) public pure override returns (uint16) {
```

- *Bridge.sol* ( [461-461](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L461-L461) ):

```solidity
461:     function _authorizePause(address)
```

- *AddressManager.sol* ( [58-58](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L58-L58) ):

```solidity
58:     function _authorizePause(address) internal pure override {
```

- *EssentialContract.sol* ( [114-114](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L114-L114), [116-116](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L116-L116) ):

```solidity
114:     function _authorizeUpgrade(address) internal virtual override onlyOwner { }

116:     function _authorizePause(address) internal virtual onlyOwner { }
```

- *SignalService.sol* ( [231-231](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L231-L231) ):

```solidity
231:     function _authorizePause(address) internal pure override {
```

- *ERC1155Vault.sol* ( [160-166](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L160-L166), [175-181](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L175-L181) ):

```solidity
160:     function onERC1155BatchReceived(
161:         address,
162:         address,
163:         uint256[] calldata,
164:         uint256[] calldata,
165:         bytes calldata
166:     )

175:     function onERC1155Received(
176:         address,
177:         address,
178:         uint256,
179:         uint256,
180:         bytes calldata
181:     )
```

- *ERC721Vault.sol* ( [142-147](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L142-L147) ):

```solidity
142:     function onERC721Received(
143:         address,
144:         address,
145:         uint256,
146:         bytes calldata
147:     )
```

- *GuardianVerifier.sol* ( [23-27](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L23-L27) ):

```solidity
23:     function verifyProof(
24:         Context calldata _ctx,
25:         TaikoData.Transition calldata,
26:         TaikoData.TierProof calldata
27:     )
```

</details>

### [N-18] Consider providing a ranged getter for array state variables

While the compiler automatically provides a getter for accessing single elements within a public state variable array, it doesn't provide a way to fetch the whole array, or subsets thereof. Consider adding a function to allow the fetching of slices of the array, especially if the contract doesn't already have multicall functionality.

There is 1 instance:

- *Guardians.sol* ( [23-23](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L23-L23) ):

```solidity
23:     address[] public guardians;
```

### [N-19] Assembly blocks should have extensive comments

Assembly blocks take a lot more time to audit than normal Solidity code, and often have gotchas and side-effects that the Solidity versions of the same code do not. Consider adding more comments explaining what is being done in every step of the assembly code, and describe why assembly is being used instead of Solidity.

<details>
<summary>There are 31 instances (click to show):</summary>

- *TaikoL2.sol* ( [242-244](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L242-L244), [247-249](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L247-L249) ):

```solidity
242:         assembly {
243:             publicInputHashOld := keccak256(inputs, 8192 /*mul(256, 32)*/ )
244:         }

247:         assembly {
248:             publicInputHashNew := keccak256(inputs, 8192 /*mul(256, 32)*/ )
249:         }
```

- *BytesUtils.sol* ( [26-28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L26-L28), [76-79](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L76-L79), [83-86](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L83-L86), [200-202](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L200-L202), [213-215](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L213-L215), [226-228](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L226-L228), [239-245](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L239-L245), [266-269](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L266-L269), [273-275](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L273-L275), [299-302](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L299-L302) ):

```solidity
26:         assembly {
27:             ret := keccak256(add(add(self, 32), offset), len)
28:         }

76:         assembly {
77:             selfptr := add(self, add(offset, 32))
78:             otherptr := add(other, add(otheroffset, 32))
79:         }

83:             assembly {
84:                 a := mload(selfptr)
85:                 b := mload(otherptr)
86:             }

200:         assembly {
201:             ret := and(mload(add(add(self, 2), idx)), 0xFFFF)
202:         }

213:         assembly {
214:             ret := and(mload(add(add(self, 4), idx)), 0xFFFFFFFF)
215:         }

226:         assembly {
227:             ret := mload(add(add(self, 32), idx))
228:         }

239:         assembly {
240:             ret :=
241:                 and(
242:                     mload(add(add(self, 32), idx)),
243:                     0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF000000000000000000000000
244:                 )
245:         }

266:         assembly {
267:             let mask := not(sub(exp(256, sub(32, len)), 1))
268:             ret := and(mload(add(add(self, 32), idx)), mask)
269:         }

273:         assembly {
274:             mcopy(dest, src, len)
275:         }

299:         assembly {
300:             dest := add(ret, 32)
301:             src := add(add(self, 32), offset)
302:         }
```

- *RsaVerify.sol* ( [99](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L99), [247](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L247) ):

```solidity
99:         assembly {

247:         assembly {
```

- *SHA1.sol* ( [12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SHA1.sol#L12) ):

```solidity
12:         assembly {
```

- *Bridge.sol* ( [543-547](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L543-L547), [560-564](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L560-L564) ):

```solidity
543:             assembly {
544:                 tstore(_CTX_SLOT, _msgHash)
545:                 tstore(add(_CTX_SLOT, 1), _from)
546:                 tstore(add(_CTX_SLOT, 2), _srcChainId)
547:             }

560:             assembly {
561:                 msgHash := tload(_CTX_SLOT)
562:                 from := tload(add(_CTX_SLOT, 1))
563:                 srcChainId := tload(add(_CTX_SLOT, 2))
564:             }
```

- *EssentialContract.sol* ( [121-123](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L121-L123), [132-134](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L132-L134) ):

```solidity
121:             assembly {
122:                 tstore(_REENTRY_SLOT, _reentry)
123:             }

132:             assembly {
133:                 reentry_ := tload(_REENTRY_SLOT)
134:             }
```

- *Lib4844.sol* ( [53-56](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/Lib4844.sol#L53-L56) ):

```solidity
53:         assembly {
54:             first := mload(add(ret, 32))
55:             second := mload(add(ret, 64))
56:         }
```

- *SignalService.sol* ( [265-267](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L265-L267), [309-311](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L309-L311) ):

```solidity
265:         assembly {
266:             sstore(slot_, _value)
267:         }

309:         assembly {
310:             value_ := sload(slot)
311:         }
```

- *RLPReader.sol* ( [43-45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L43-L45), [94-96](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L94-L96), [159-161](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L159-L161), [178-180](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L178-L180), [198-200](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L198-L200), [208-210](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L208-L210), [244-246](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L244-L246), [254-256](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L254-L256), [295-301](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L295-L301) ):

```solidity
43:         assembly {
44:             ptr := add(_in, 32)
45:         }

94:         assembly {
95:             mstore(out_, itemCount)
96:         }

159:         assembly {
160:             prefix := byte(0, mload(ptr))
161:         }

178:             assembly {
179:                 firstByteOfContent := and(mload(add(ptr, 1)), shl(248, 0xff))
180:             }

198:             assembly {
199:                 firstByteOfContent := and(mload(add(ptr, 1)), shl(248, 0xff))
200:             }

208:             assembly {
209:                 strLen := shr(sub(256, mul(8, lenOfStrLen)), mload(add(ptr, 1)))
210:             }

244:             assembly {
245:                 firstByteOfContent := and(mload(add(ptr, 1)), shl(248, 0xff))
246:             }

254:             assembly {
255:                 listLen := shr(sub(256, mul(8, lenOfListLen)), mload(add(ptr, 1)))
256:             }

295:         assembly {
296:             let dest := add(out_, 32)
297:             let i := 0
298:             for { } lt(i, _length) { i := add(i, 32) } { mstore(add(dest, i), mload(add(src, i))) }
299: 
300:             if gt(i, _length) { mstore(add(dest, _length), 0) }
301:         }
```

</details>

### [N-20] Consider splitting complex checks into multiple steps

Assign the expression's parts to intermediate local variables, and check against those instead.

There is 1 instance:

- *Bridge.sol* ( [270-271](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L270-L271) ):

```solidity
270:                 _message.to == address(0) || _message.to == address(this)
271:                     || _message.to == signalService || addressBanned[_message.to]
```

### [N-21] Cast is more restrictive than the type of the variable being assigned

If `address foo` is being used in an expression such as `IERC20 token = FooToken(foo)`, then the more specific cast to `FooToken` is a waste because the only thing the compiler will check for is that `FooToken` extends `IERC20` - it won't check any of the function signatures. Therefore, it makes more sense to do `IERC20 token = IERC20(token)` or better yet `FooToken token = FooToken(foo)`. The former may allow the file in which it's used to remove the import for `FooToken`.

There are 2 instances:

- *AutomataDcapV3Attestation.sol* ( [56-56](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L56-L56) ):

```solidity
/// @audit contract IPEMCertChainLib <- type(contract PEMCertChainLib)
56:         pemCertLib = PEMCertChainLib(pemCertLibAddr);
```

- *V3Parser.sol* ( [275-275](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L275-L275) ):

```solidity
/// @audit contract IPEMCertChainLib <- type(contract PEMCertChainLib)
275:         IPEMCertChainLib pemCertLib = PEMCertChainLib(pemCertLibAddr);
```

### [N-22] Consider moving `msg.sender` checks to `modifier`s

If some functions are only allowed to be called by some specific users, consider using a modifier instead of checking with a require statement, especially if this check is done in multiple functions.

<details>
<summary>There are 8 instances (click to show):</summary>

- *TaikoL2.sol* ( [123-123](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L123-L123) ):

```solidity
123:         if (msg.sender != GOLDEN_TOUCH_ADDRESS) revert L2_INVALID_SENDER();
```

- *Bridge.sol* ( [260-262](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L260-L262), [322-322](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L322-L322) ):

```solidity
260:             if (_message.gasLimit == 0 && msg.sender != _message.destOwner) {
261:                 revert B_PERMISSION_DENIED();
262:             }

322:             if (msg.sender != _message.destOwner) revert B_PERMISSION_DENIED();
```

- *SignalService.sol* ( [77-77](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L77-L77) ):

```solidity
77:         if (!isAuthorized[msg.sender]) revert SS_UNAUTHORIZED();
```

- *BaseVault.sol* ( [65-65](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L65-L65) ):

```solidity
65:         if (ctx_.from != msg.sender) revert VAULT_PERMISSION_DENIED();
```

- *BridgedERC20Base.sol* ( [64-67](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L64-L67), [78-78](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L78-L78), [83-86](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L83-L86) ):

```solidity
64:         } else if (msg.sender != resolve("erc20_vault", true)) {
65:             // Bridging from vault
66:             revert BB_PERMISSION_DENIED();
67:         }

78:             if (msg.sender != _account) revert BB_PERMISSION_DENIED();

83:         } else if (msg.sender != resolve("erc20_vault", true)) {
84:             // Only the vault can burn tokens when not migrating out
85:             revert RESOLVER_DENIED();
86:         }
```

</details>

### [N-23] Missing checks for empty bytes when updating bytes state variables

Unless the code is attempting to `delete` the state variable, the caller shouldn't have to write `""` to the state variable

There is 1 instance:

- *MerkleClaimable.sol* ( [93-93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L93-L93) ):

```solidity
93:         merkleRoot = _merkleRoot;
```

### [N-24] Complex casting

Consider whether the number of casts is really necessary, or whether using a different type would be more appropriate. Alternatively, add comments to explain in detail why the casts are necessary, and any implicit reasons why the cast does not introduce an overflow.

There are 2 instances:

- *BytesUtils.sol* ( [336-336](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L336-L336) ):

```solidity
336:             decoded = uint8(BASE32_HEX_TABLE[uint256(uint8(char)) - 0x30]);
```

- *LibFixedPointMath.sol* ( [76-79](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L76-L79) ):

```solidity
76:             r = int256(
77:                 (uint256(r) * 3_822_833_074_963_236_453_042_738_258_902_158_003_155_416_615_667)
78:                     >> uint256(195 - k)
79:             );
```

### [N-25] Complex math should be split into multiple steps

Consider splitting long arithmetic calculations into multiple steps to improve the code readability.

<details>
<summary>There are 14 instances (click to show):</summary>

- *V3Parser.sol* ( [106-115](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L106-L115), [159-159](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L159-L159) ):

```solidity
106:         uint32 totalQuoteSize = 48 // header
107:             + 384 // local QE report
108:             + 64 // ecdsa256BitSignature
109:             + 64 // ecdsaAttestationKey
110:             + 384 // QE report
111:             + 64 // qeReportSignature
112:             + 2 // sizeof(v3Quote.v3AuthData.qeAuthData.parsedDataSize)
113:             + v3Quote.v3AuthData.qeAuthData.parsedDataSize + 2 // sizeof(v3Quote.v3AuthData.certification.certType)
114:             + 4 // sizeof(v3Quote.v3AuthData.certification.certDataSize)
115:             + v3Quote.v3AuthData.certification.certDataSize;

159:             acc += upperDigit * (16 ** ((2 * i) + 1));
```

- *Asn1Decode.sol* ( [202-204](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L202-L204) ):

```solidity
202:                 length = uint256(
203:                     der.readBytesN(ix + 2, lengthbytesLength) >> (32 - lengthbytesLength) * 8
204:                 );
```

- *BytesUtils.sol* ( [93-93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L93-L93) ):

```solidity
93:                     mask = ~(2 ** (8 * (32 - shortest + idx)) - 1);
```

- *X509DateUtils.sol* ( [21-21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L21-L21), [24-24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L24-L24), [25-25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L25-L25), [26-26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L26-L26), [27-27](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L27-L27), [28-28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L28-L28), [29-29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L29-L29) ):

```solidity
21:             yrs += (uint8(x509Time[0]) - 48) * 1000 + (uint8(x509Time[1]) - 48) * 100;

24:         yrs += (uint8(x509Time[offset + 0]) - 48) * 10 + uint8(x509Time[offset + 1]) - 48;

25:         mnths = (uint8(x509Time[offset + 2]) - 48) * 10 + uint8(x509Time[offset + 3]) - 48;

26:         dys += (uint8(x509Time[offset + 4]) - 48) * 10 + uint8(x509Time[offset + 5]) - 48;

27:         hrs += (uint8(x509Time[offset + 6]) - 48) * 10 + uint8(x509Time[offset + 7]) - 48;

28:         mins += (uint8(x509Time[offset + 8]) - 48) * 10 + uint8(x509Time[offset + 9]) - 48;

29:         secs += (uint8(x509Time[offset + 10]) - 48) * 10 + uint8(x509Time[offset + 11]) - 48;
```

- *ERC20Airdrop2.sol* ( [117-118](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L117-L118) ):

```solidity
117:         uint256 timeBasedAllowance = balance
118:             * (block.timestamp.min(claimEnd + withdrawalWindow) - claimEnd) / withdrawalWindow;
```

- *RLPWriter.sol* ( [47-47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L47-L47) ):

```solidity
47:                 out_[i] = bytes1(uint8((_len / (256 ** (lenLen - i))) % 256));
```

- *LibFixedPointMath.sol* ( [39-39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L39-L39) ):

```solidity
39:             int256 k = ((x << 96) / 54_916_777_467_707_473_351_141_471_128 + 2 ** 95) >> 96;
```

</details>

### [N-26] Consider adding a block/deny-list

Doing so will significantly increase centralization, but will help to prevent hackers from using stolen tokens

<details>
<summary>There are 11 instances (click to show):</summary>

- *TaikoToken.sol* ( [15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L15) ):

```solidity
15: contract TaikoToken is EssentialContract, ERC20SnapshotUpgradeable, ERC20VotesUpgradeable {
```

- *AssignmentHook.sol* ( [14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L14) ):

```solidity
14: contract AssignmentHook is EssentialContract, IHook {
```

- *TaikoL2.sol* ( [21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L21) ):

```solidity
21: contract TaikoL2 is CrossChainOwned {
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

</details>

### [N-27] Convert simple `if`-statements to ternary expressions

Converting some if statements to ternaries (such as `z = (a < b) ? x : y`) can make the code more concise and easier to read.

<details>
<summary>There are 8 instances (click to show):</summary>

- *LibUtils.sol* ( [80-84](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L80-L84) ):

```solidity
80:         if (_state.transitions[_slot][1].key == _parentHash) {
81:             tid_ = 1;
82:         } else {
83:             tid_ = _state.transitionIds[_blk.blockId][_parentHash];
84:         }
```

- *PEMCertChainLib.sol* ( [56-60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L56-L60), [333-337](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L333-L337) ):

```solidity
56:             if (i > 0) {
57:                 input = LibString.slice(pemChainStr, index, index + len);
58:             } else {
59:                 input = pemChainStr;
60:             }

333:             if (tbsPtr.ixl() < tbsParentPtr.ixl()) {
334:                 tbsPtr = der.nextSiblingOf(tbsPtr);
335:             } else {
336:                 tbsPtr = 0; // exit
337:             }
```

- *Asn1Decode.sol* ( [199-205](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L199-L205) ):

```solidity
199:             } else if (lengthbytesLength == 2) {
200:                 length = der.readUint16(ix + 2);
201:             } else {
202:                 length = uint256(
203:                     der.readBytesN(ix + 2, lengthbytesLength) >> (32 - lengthbytesLength) * 8
204:                 );
205:             }
```

- *BytesUtils.sol* ( [90-94](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L90-L94) ):

```solidity
90:                 if (shortest > 32) {
91:                     mask = type(uint256).max; // aka 0xffffff....
92:                 } else {
93:                     mask = ~(2 ** (8 * (32 - shortest + idx)) - 1);
94:                 }
```

- *X509DateUtils.sol* ( [18-19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L18-L19), [49-53](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L49-L53) ):

```solidity
18:             if (uint8(x509Time[0]) - 48 < 5) yrs += 2000;
19:             else yrs += 1900;

49:             if (isLeapYear(i)) {
50:                 timestamp += 31_622_400; // Leap year in seconds
51:             } else {
52:                 timestamp += 31_536_000; // Normal year in seconds
53:             }
```

- *RLPWriter.sol* ( [14-18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L14-L18) ):

```solidity
14:         if (_in.length == 1 && uint8(_in[0]) < 128) {
15:             out_ = _in;
16:         } else {
17:             out_ = abi.encodePacked(_writeLength(_in.length, 128), _in);
18:         }
```

</details>

### [N-28] Contracts should each be defined in separate files

Keeping each contract in a separate file makes it easier to work with multiple people, makes the code easier to maintain, and is a common practice on most projects. The following files each contains more than one contract/library/interface.

There are 5 instances:

- [*ITierProvider.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/ITierProvider.sol)

- [*Asn1Decode.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol)

- [*IBridge.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/IBridge.sol)

- [*ERC1155Vault.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol)

- [*USDCAdapter.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol)

### [N-29] UPPER_CASE names should be reserved for `constant`/`immutable` variables

If the variable needs to be different based on which class it comes from, a `view`/`pure` _function_ should be used instead (e.g. like [this](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/76eee35971c2541585e05cbf258510dda7b2fbc6/contracts/token/ERC20/extensions/draft-IERC20Permit.sol#L59)).

There is 1 instance:

- *SigVerifyLib.sol* ( [18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L18) ):

```solidity
18:     address private ES256VERIFIER;
```

### [N-30] Do not use literal numbers for array indexes

Indexing arrays using enums or meaningfully named constants instead of literals can make code easier to read and maintain.

<details>
<summary>There are 37 instances (click to show):</summary>

- *LibUtils.sol* ( [80-80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L80-L80) ):

```solidity
80:         if (_state.transitions[_slot][1].key == _parentHash) {
```

- *LibVerifying.sol* ( [62-62](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L62-L62), [68-68](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L68-L68), [68-68](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L68-L68) ):

```solidity
62:         TaikoData.Block storage blk = _state.blocks[0];

68:         TaikoData.TransitionState storage ts = _state.transitions[0][1];

68:         TaikoData.TransitionState storage ts = _state.transitions[0][1];
```

- *DevnetTierProvider.sol* ( [49-49](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L49-L49), [50-50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L50-L50) ):

```solidity
49:         tiers_[0] = LibTiers.TIER_OPTIMISTIC;

50:         tiers_[1] = LibTiers.TIER_GUARDIAN;
```

- *MainnetTierProvider.sol* ( [60-60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L60-L60), [61-61](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L61-L61), [62-62](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L62-L62) ):

```solidity
60:         tiers_[0] = LibTiers.TIER_SGX;

61:         tiers_[1] = LibTiers.TIER_SGX_ZKVM;

62:         tiers_[2] = LibTiers.TIER_GUARDIAN;
```

- *TestnetTierProvider.sol* ( [60-60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L60-L60), [61-61](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L61-L61), [62-62](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L62-L62) ):

```solidity
60:         tiers_[0] = LibTiers.TIER_OPTIMISTIC;

61:         tiers_[1] = LibTiers.TIER_SGX;

62:         tiers_[2] = LibTiers.TIER_GUARDIAN;
```

- *TaikoL2.sol* ( [240-240](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L240-L240) ):

```solidity
240:         inputs[255] = bytes32(block.chainid);
```

- *AutomataDcapV3Attestation.sol* ( [435-435](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L435-L435), [442-442](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L442-L442), [454-454](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L454-L454), [472-472](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L472-L472) ):

```solidity
435:             string memory parsedFmspc = parsedQuoteCerts[0].pck.sgxExtension.fmspc;

442:             IPEMCertChainLib.ECSha256Certificate memory pckCert = parsedQuoteCerts[0];

454:             (tcbVerified, tcbStatus) = _checkTcbLevels(parsedQuoteCerts[0].pck, fetchedTcbInfo);

472:                 parsedQuoteCerts[0].pubKey,
```

- *V3Parser.sol* ( [285-285](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L285-L285), [285-285](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L285-L285), [285-285](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L285-L285) ):

```solidity
285:         certChainData = [quoteCerts[0], quoteCerts[1], quoteCerts[2]];

285:         certChainData = [quoteCerts[0], quoteCerts[1], quoteCerts[2]];

285:         certChainData = [quoteCerts[0], quoteCerts[1], quoteCerts[2]];
```

- *RsaVerify.sol* ( [137-137](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L137-L137), [137-137](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L137-L137), [270-270](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L270-L270), [270-270](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L270-L270) ):

```solidity
137:         if (decipher[0] != 0 || decipher[1] != 0x01) {

137:         if (decipher[0] != 0 || decipher[1] != 0x01) {

270:         if (decipher[0] != 0 || decipher[1] != 0x01) {

270:         if (decipher[0] != 0 || decipher[1] != 0x01) {
```

- *X509DateUtils.sol* ( [18-18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L18-L18), [21-21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L21-L21), [21-21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L21-L21), [57-57](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L57-L57) ):

```solidity
18:             if (uint8(x509Time[0]) - 48 < 5) yrs += 2000;

21:             yrs += (uint8(x509Time[0]) - 48) * 1000 + (uint8(x509Time[1]) - 48) * 100;

21:             yrs += (uint8(x509Time[0]) - 48) * 1000 + (uint8(x509Time[1]) - 48) * 100;

57:         if (isLeapYear(year)) monthDays[1] = 29;
```

- *RLPWriter.sol* ( [14-14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L14-L14), [35-35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L35-L35), [45-45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L45-L45) ):

```solidity
14:         if (_in.length == 1 && uint8(_in[0]) < 128) {

35:             out_[0] = bytes1(uint8(_len) + uint8(_offset));

45:             out_[0] = bytes1(uint8(lenLen) + uint8(_offset) + 55);
```

- *MerkleTrie.sol* ( [141-141](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L141-L141), [171-171](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L171-L171), [188-188](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L188-L188), [228-228](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L228-L228) ):

```solidity
141:                 uint8 prefix = uint8(path[0]);

171:                     value_ = RLPReader.readBytes(currentNode.decoded[1]);

188:                     currentNodeID = _getNodeID(currentNode.decoded[1]);

228:         nibbles_ = Bytes.toNibbles(RLPReader.readBytes(_node.decoded[0]));
```

- *SgxVerifier.sol* ( [133-133](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L133-L133), [135-135](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L135-L135) ):

```solidity
133:         _address[0] = address(bytes20(_attestation.localEnclaveReport.reportData));

135:         return _addInstances(_address, false)[0];
```

</details>

### [N-31] Consider emitting an event at the end of the constructor

This will allow users to easily exactly pinpoint when and by whom a contract was constructed.

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

### [N-32] Empty function body without comments

Empty function body in solidity is not recommended, consider adding some comments to the body.

<details>
<summary>There are 5 instances (click to show):</summary>

- *TaikoL1.sol* ( [220-226](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L220-L226) ):

```solidity
220:     function _authorizePause(address)
221:         internal
222:         view
223:         virtual
224:         override
225:         onlyFromOwnerOrNamed("chain_pauser")
226:     { }
```

- *Bridge.sol* ( [70-70](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L70-L70), [461-467](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L461-L467) ):

```solidity
70:     receive() external payable { }

461:     function _authorizePause(address)
462:         internal
463:         view
464:         virtual
465:         override
466:         onlyFromOwnerOrNamed("bridge_pauser")
467:     { }
```

- *EssentialContract.sol* ( [114-114](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L114-L114), [116-116](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L116-L116) ):

```solidity
114:     function _authorizeUpgrade(address) internal virtual override onlyOwner { }

116:     function _authorizePause(address) internal virtual onlyOwner { }
```

</details>

### [N-33] Events are emitted without the sender information

When an action is triggered based on a user's action, not being able to filter based on who triggered the action makes event processing a lot more cumbersome. Including the `msg.sender` the events of these types of action will make events much more useful to end users, especially when `msg.sender` is not `tx.origin`.

<details>
<summary>There are 26 instances (click to show):</summary>

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

- *LibProposing.sol* ( [166-166](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L166-L166), [273-279](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L273-L279) ):

```solidity
166:                     emit BlobCached(meta_.blobHash);

273:         emit BlockProposed({
274:             blockId: blk.blockId,
275:             assignedProver: blk.assignedProver,
276:             livenessBond: _config.livenessBond,
277:             meta: meta_,
278:             depositsProcessed: deposits_
279:         });
```

- *LibProving.sol* ( [80-80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L80-L80) ):

```solidity
80:         emit ProvingPaused(_pause);
```

- *Guardians.sol* ( [121-121](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L121-L121) ):

```solidity
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

- *Bridge.sol* ( [151-151](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L151-L151), [208-208](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L208-L208), [210-210](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L210-L210), [301-301](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L301-L301), [303-303](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L303-L303), [336-336](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L336-L336) ):

```solidity
151:         emit MessageSent(msgHash_, message_);

208:             emit MessageRecalled(msgHash);

210:             emit MessageReceived(msgHash, _message, true);

301:             emit MessageExecuted(msgHash);

303:             emit MessageReceived(msgHash, _message, false);

336:         emit MessageRetried(msgHash);
```

- *ERC20Airdrop2.sol* ( [93-93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L93-L93) ):

```solidity
93:         emit Withdrawn(user, amount);
```

- *BridgedERC20Base.sol* ( [63-63](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L63-L63), [80-80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L80-L80) ):

```solidity
63:             emit MigratedTo(migratingAddress, _account, _amount);

80:             emit MigratedTo(migratingAddress, _account, _amount);
```

- *ERC1155Vault.sol* ( [80-89](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L80-L89), [114-123](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L114-L123), [149-156](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L149-L156) ):

```solidity
80:         emit TokenSent({
81:             msgHash: msgHash,
82:             from: message_.srcOwner,
83:             to: _op.to,
84:             destChainId: message_.destChainId,
85:             ctoken: ctoken.addr,
86:             token: _op.token,
87:             tokenIds: _op.tokenIds,
88:             amounts: _op.amounts
89:         });

114:         emit TokenReceived({
115:             msgHash: ctx.msgHash,
116:             from: from,
117:             to: to,
118:             srcChainId: ctx.srcChainId,
119:             ctoken: ctoken.addr,
120:             token: token,
121:             tokenIds: tokenIds,
122:             amounts: amounts
123:         });

149:         emit TokenReleased({
150:             msgHash: msgHash,
151:             from: message.srcOwner,
152:             ctoken: ctoken.addr,
153:             token: token,
154:             tokenIds: tokenIds,
155:             amounts: amounts
156:         });
```

- *ERC20Vault.sol* ( [241-249](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L241-L249), [273-281](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L273-L281), [306-312](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L306-L312) ):

```solidity
241:         emit TokenSent({
242:             msgHash: msgHash,
243:             from: message_.srcOwner,
244:             to: _op.to,
245:             destChainId: _op.destChainId,
246:             ctoken: ctoken.addr,
247:             token: _op.token,
248:             amount: balanceChange
249:         });

273:         emit TokenReceived({
274:             msgHash: ctx.msgHash,
275:             from: from,
276:             to: to,
277:             srcChainId: ctx.srcChainId,
278:             ctoken: ctoken.addr,
279:             token: token,
280:             amount: amount
281:         });

306:         emit TokenReleased({
307:             msgHash: _msgHash,
308:             from: _message.srcOwner,
309:             ctoken: ctoken.addr,
310:             token: token,
311:             amount: amount
312:         });
```

- *ERC721Vault.sol* ( [64-73](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L64-L73), [97-106](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L97-L106), [131-138](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L131-L138) ):

```solidity
64:         emit TokenSent({
65:             msgHash: msgHash,
66:             from: message_.srcOwner,
67:             to: _op.to,
68:             destChainId: message_.destChainId,
69:             ctoken: ctoken.addr,
70:             token: _op.token,
71:             tokenIds: _op.tokenIds,
72:             amounts: _op.amounts
73:         });

97:         emit TokenReceived({
98:             msgHash: ctx.msgHash,
99:             from: from,
100:             to: to,
101:             srcChainId: ctx.srcChainId,
102:             ctoken: ctoken.addr,
103:             token: token,
104:             tokenIds: tokenIds,
105:             amounts: new uint256[](tokenIds.length)
106:         });

131:         emit TokenReleased({
132:             msgHash: _msgHash,
133:             from: _message.srcOwner,
134:             ctoken: ctoken.addr,
135:             token: token,
136:             tokenIds: tokenIds,
137:             amounts: new uint256[](tokenIds.length)
138:         });
```

</details>

### [N-34] Event is missing `indexed` fields

Index event fields makes the field more quickly accessible to [off-chain tools](https://ethereum.stackexchange.com/questions/40396/can-somebody-please-explain-the-concept-of-event-indexing) that parse events. However, note that each indexed field costs extra gas during emission, so it's not necessarily best to index the maximum allowed per event (three fields). Each event should use three indexed fields if there are three or more fields, and gas usage is not particularly of concern for the events in question. If there are fewer than three fields, all of the fields should be indexed.

<details>
<summary>There are 28 instances (click to show):</summary>

- *TaikoEvents.sol* ( [53-59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoEvents.sol#L53-L59), [67-73](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoEvents.sol#L67-L73), [77-77](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoEvents.sol#L77-L77), [81-81](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoEvents.sol#L81-L81) ):

```solidity
53:     event TransitionProved(
54:         uint256 indexed blockId,
55:         TaikoData.Transition tran,
56:         address prover,
57:         uint96 validityBond,
58:         uint16 tier
59:     );

67:     event TransitionContested(
68:         uint256 indexed blockId,
69:         TaikoData.Transition tran,
70:         address contester,
71:         uint96 contestBond,
72:         uint16 tier
73:     );

77:     event BlobCached(bytes32 blobHash);

81:     event ProvingPaused(bool paused);
```

- *LibProposing.sol* ( [41-41](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L41-L41) ):

```solidity
41:     event BlobCached(bytes32 blobHash);
```

- *LibProving.sol* ( [32-38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L32-L38), [46-52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L46-L52), [56-56](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L56-L56) ):

```solidity
32:     event TransitionProved(
33:         uint256 indexed blockId,
34:         TaikoData.Transition tran,
35:         address prover,
36:         uint96 validityBond,
37:         uint16 tier
38:     );

46:     event TransitionContested(
47:         uint256 indexed blockId,
48:         TaikoData.Transition tran,
49:         address contester,
50:         uint96 contestBond,
51:         uint16 tier
52:     );

56:     event ProvingPaused(bool paused);
```

- *GuardianProver.sol* ( [18-20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/GuardianProver.sol#L18-L20) ):

```solidity
18:     event GuardianApproval(
19:         address indexed addr, uint256 indexed blockId, bytes32 blockHash, bool approved
20:     );
```

- *Guardians.sol* ( [43-43](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L43-L43) ):

```solidity
43:     event Approved(uint256 indexed operationId, uint256 approvalBits, bool proofSubmitted);
```

- *TaikoL2.sol* ( [57-57](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L57-L57) ):

```solidity
57:     event Anchored(bytes32 parentHash, uint64 gasExcess);
```

- *IBridge.sol* ( [75-75](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/IBridge.sol#L75-L75), [92-92](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/IBridge.sol#L92-L92), [97-97](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/IBridge.sol#L97-L97), [102-102](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/IBridge.sol#L102-L102) ):

```solidity
75:     event MessageReceived(bytes32 indexed msgHash, Message message, bool isRecall);

92:     event MessageStatusChanged(bytes32 indexed msgHash, Status status);

97:     event MessageSuspended(bytes32 msgHash, bool suspended);

102:     event AddressBanned(address indexed addr, bool banned);
```

- *AddressManager.sol* ( [21-23](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L21-L23) ):

```solidity
21:     event AddressSet(
22:         uint64 indexed chainId, bytes32 indexed name, address newAddress, address oldAddress
23:     );
```

- *EssentialContract.sol* ( [29-29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L29-L29), [33-33](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L33-L33) ):

```solidity
29:     event Paused(address account);

33:     event Unpaused(address account);
```

- *ISignalService.sol* ( [49-49](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/ISignalService.sol#L49-L49), [54-54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/ISignalService.sol#L54-L54) ):

```solidity
49:     event SignalSent(address app, bytes32 signal, bytes32 slot, bytes32 value);

54:     event Authorized(address indexed addr, bool authrized);
```

- *TimelockTokenPool.sol* ( [99-99](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L99-L99) ):

```solidity
99:     event Withdrawn(address indexed recipient, address to, uint128 amount, uint128 cost);
```

- *ERC20Airdrop2.sol* ( [35-35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L35-L35) ):

```solidity
35:     event Withdrawn(address user, uint256 amount);
```

- *MerkleClaimable.sol* ( [27-27](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L27-L27) ):

```solidity
27:     event Claimed(bytes32 hash);
```

- *BaseNFTVault.sol* ( [104-111](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L104-L111) ):

```solidity
104:     event TokenReleased(
105:         bytes32 indexed msgHash,
106:         address indexed from,
107:         address ctoken,
108:         address token,
109:         uint256[] tokenIds,
110:         uint256[] amounts
111:     );
```

- *BridgedERC20Base.sol* ( [21-21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L21-L21) ):

```solidity
21:     event MigrationStatusChanged(address addr, bool inbound);
```

- *ERC20Vault.sol* ( [80-88](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L80-L88), [114-116](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L114-L116) ):

```solidity
80:     event BridgedTokenChanged(
81:         uint256 indexed srcChainId,
82:         address indexed ctoken,
83:         address btokenOld,
84:         address btokenNew,
85:         string ctokenSymbol,
86:         string ctokenName,
87:         uint8 ctokenDecimal
88:     );

114:     event TokenReleased(
115:         bytes32 indexed msgHash, address indexed from, address ctoken, address token, uint256 amount
116:     );
```

- *SgxVerifier.sol* ( [65-67](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L65-L67) ):

```solidity
65:     event InstanceAdded(
66:         uint256 indexed id, address indexed instance, address replaced, uint256 validSince
67:     );
```

</details>

### [N-35] Contract implements interface without extending the interface

Not extending the interface may lead to the wrong function signature being used, leading to unexpected behavior. If the interface is in fact being implemented, use the `override` keyword to indicate that fact.

There are 2 instances:

- *ERC1155Vault.sol* ( [29-29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L29-L29) ):

```solidity
/// @audit IERC1155Receiver
29: contract ERC1155Vault is BaseNFTVault, ERC1155ReceiverUpgradeable {
```

- *ERC721Vault.sol* ( [16-16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L16-L16) ):

```solidity
/// @audit IERC721TokenReceiver
16: contract ERC721Vault is BaseNFTVault, IERC721Receiver {
```

### [N-36] Imports could be organized more systematically

The contract's interface should be imported first, followed by each of the interfaces it uses, followed by all other files. The examples below do not follow this layout.

<details>
<summary>There are 31 instances (click to show):</summary>

- *TaikoL1.sol* ( [9-9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L9-L9) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
9: import "./ITaikoL1.sol";
```

- *AssignmentHook.sol* ( [8-8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L8-L8) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
8: import "../ITaikoL1.sol";
```

- *LibProposing.sol* ( [7-7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L7-L7) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
7: import "../hooks/IHook.sol";
```

- *LibProving.sol* ( [7-7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L7-L7) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
7: import "../../verifiers/IVerifier.sol";
```

- *LibVerifying.sol* ( [7-7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L7-L7), [9-9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L9-L9) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
7: import "../../signal/ISignalService.sol";

/// @audit Out of order with the prev import️ ⬆
9: import "../tiers/ITierProvider.sol";
```

- *DevnetTierProvider.sol* ( [5-5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L5-L5) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
5: import "./ITierProvider.sol";
```

- *MainnetTierProvider.sol* ( [5-5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L5-L5) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
5: import "./ITierProvider.sol";
```

- *TestnetTierProvider.sol* ( [5-5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L5-L5) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
5: import "./ITierProvider.sol";
```

- *CrossChainOwned.sol* ( [6-6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L6-L6) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
6: import "../bridge/IBridge.sol";
```

- *TaikoL2.sol* ( [9-9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L9-L9) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
9: import "../signal/ISignalService.sol";
```

- *AutomataDcapV3Attestation.sol* ( [6-6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L6-L6), [10-10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L10-L10), [18-18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L18-L18) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
6: import { IPEMCertChainLib } from "./lib/interfaces/IPEMCertChainLib.sol";

/// @audit Out of order with the prev import️ ⬆
10: import { IAttestation } from "./interfaces/IAttestation.sol";

/// @audit Out of order with the prev import️ ⬆
18: import { ISigVerifyLib } from "./interfaces/ISigVerifyLib.sol";
```

- *PEMCertChainLib.sol* ( [8-8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L8-L8) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
8: import { IPEMCertChainLib } from "./interfaces/IPEMCertChainLib.sol";
```

- *V3Parser.sol* ( [6-6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L6-L6) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
6: import { IPEMCertChainLib, PEMCertChainLib } from "../../lib/PEMCertChainLib.sol";
```

- *Bridge.sol* ( [7-7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L7-L7), [9-9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L9-L9) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
7: import "../signal/ISignalService.sol";

/// @audit Out of order with the prev import️ ⬆
9: import "./IBridge.sol";
```

- *AddressResolver.sol* ( [5-5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L5-L5) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
5: import "./IAddressManager.sol";
```

- *LibAddress.sol* ( [6-6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L6-L6) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
6: import "@openzeppelin/contracts/utils/introspection/IERC165.sol";
```

- *SignalService.sol* ( [7-7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L7-L7) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
7: import "./ISignalService.sol";
```

- *TimelockTokenPool.sol* ( [5-5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L5-L5) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
5: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```

- *BaseVault.sol* ( [6-6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L6-L6) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
6: import "../bridge/IBridge.sol";
```

- *BridgedERC1155.sol* ( [6-7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L6-L7) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
6: import
7:     "@openzeppelin/contracts-upgradeable/token/ERC1155/extensions/IERC1155MetadataURIUpgradeable.sol";
```

- *BridgedERC20Base.sol* ( [5-5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L5-L5) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
5: import "./IBridgedERC20.sol";
```

- *ERC1155Vault.sol* ( [6-6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L6-L6) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
6: import "../bridge/IBridge.sol";
```

- *ERC20Vault.sol* ( [7-7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L7-L7) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
7: import "../bridge/IBridge.sol";
```

- *GuardianVerifier.sol* ( [6-6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L6-L6) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
6: import "./IVerifier.sol";
```

- *SgxVerifier.sol* ( [5-5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L5-L5), [8-8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L8-L8), [10-10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L10-L10) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
5: import "../L1/ITaikoL1.sol";

/// @audit Out of order with the prev import️ ⬆
8: import "../automata-attestation/interfaces/IAttestation.sol";

/// @audit Out of order with the prev import️ ⬆
10: import "./IVerifier.sol";
```

</details>

### [N-37] @openzeppelin/contracts should be upgraded to a newer version

These contracts import contracts from `@openzeppelin/contracts`, but they are not using [the latest version](https://github.com/OpenZeppelin/openzeppelin-contracts/releases). Using the latest version ensures contract security with fixes for known vulnerabilities, access to the latest feature updates, and enhanced community support and engagement.

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

### [N-38] Lib @openzeppelin/contracts-upgradeable should be upgraded to a newer version

These contracts import contracts from `@openzeppelin/contracts-upgradeable`, but they are not using [the latest version](https://github.com/OpenZeppelin/openzeppelin-contracts-upgradeable/releases). Using the latest version ensures contract security with fixes for known vulnerabilities, access to the latest feature updates, and enhanced community support and engagement.

The imported version is `4.8.2`.

<details>
<summary>There are 19 instances (click to show):</summary>

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

- *AddressResolver.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L4) ):

```solidity
4: import "@openzeppelin/contracts-upgradeable/proxy/utils/Initializable.sol";
```

- *EssentialContract.sol* ( [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L5) ):

```solidity
5: import "@openzeppelin/contracts-upgradeable/access/Ownable2StepUpgradeable.sol";
```

- *BaseVault.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L4) ):

```solidity
4: import "@openzeppelin/contracts-upgradeable/utils/introspection/IERC165Upgradeable.sol";
```

- *BridgedERC1155.sol* ( [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L6) ):

```solidity
5: import "@openzeppelin/contracts-upgradeable/token/ERC1155/ERC1155Upgradeable.sol";

6: import
```

- *BridgedERC20.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L4), [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L6), [7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L7) ):

```solidity
4: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/IERC20MetadataUpgradeable.sol";

6: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20SnapshotUpgradeable.sol";

7: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20VotesUpgradeable.sol";
```

- *BridgedERC721.sol* ( [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L4) ):

```solidity
4: import "@openzeppelin/contracts-upgradeable/token/ERC721/ERC721Upgradeable.sol";
```

- *ERC1155Vault.sol* ( [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L5) ):

```solidity
5: import "@openzeppelin/contracts-upgradeable/token/ERC1155/utils/ERC1155ReceiverUpgradeable.sol";
```

</details>

### [N-39] Lines are too long

The [solidity style guide](https://docs.soliditylang.org/en/v0.8.17/style-guide.html#maximum-line-length) recommends a maximum line length of 120 characters. Lines of code that are longer than 120 should be wrapped.

<details>
<summary>There are 6 instances (click to show):</summary>

- *AutomataDcapV3Attestation.sol* ( [28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L28), [31](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L31) ):

```solidity
28:     // https://github.com/intel/SGXDataCenterAttestationPrimitives/blob/e7604e02331b3377f3766ed3653250e03af72d45/QuoteVerification/QVL/Src/AttestationLibrary/src/CertVerification/X509Constants.h#L64

31:     // keccak256(hex"0ba9c4c0c0c86193a3fe23d6b02cda10a8bbd4e88e48b4458561a36e705525f567918e2edc88e40d860bd0cc4ee26aacc988e505a953558c453f6b0904ae7394")
```

- *PEMCertChainLib.sol* ( [31](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L31) ):

```solidity
31:     // https://github.com/intel/SGXDataCenterAttestationPrimitives/blob/e7604e02331b3377f3766ed3653250e03af72d45/QuoteVerification/QVL/Src/AttestationLibrary/src/CertVerification/X509Constants.h#L64
```

- *BytesUtils.sol* ( [311](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L311) ):

```solidity
311:         hex"00010203040506070809FFFFFFFFFFFFFF0A0B0C0D0E0F101112131415161718191A1B1C1D1E1FFFFFFFFFFFFFFFFFFFFF0A0B0C0D0E0F101112131415161718191A1B1C1D1E1F";
```

- *RsaVerify.sol* ( [27](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L27) ):

```solidity
27: https://csrc.nist.gov/CSRC/media/Projects/Cryptographic-Algorithm-Validation-Program/documents/dss/186-2rsatestvectors.zip
```

- *RLPReader.sol* ( [293](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L293) ):

```solidity
293:         // https://github.com/ethereum/solidity/blob/34dd30d71b4da730488be72ff6af7083cf2a91f6/libsolidity/codegen/YulUtilFunctions.cpp#L102-L114
```

</details>

### [N-40] Magic numbers should be replaced with constants

Magic numbers are hard-coded values in code that can make it difficult for developers and maintainers to understand the code, and can also cause confusion or errors. To improve the readability and maintainability of code, it is recommended to replace magic numbers with constants that have good readability.

<details>
<summary>There are 480 instances (click to show):</summary>

- *TaikoData.sol* ( [195-195](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L195-L195) ):

```solidity
195:         uint256[43] __gap;
```

- *TaikoL1.sol* ( [26-26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L26-L26), [192-192](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L192-L192), [195-195](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L195-L195), [196-196](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L196-L196), [199-199](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L199-L199), [203-203](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L203-L203), [204-204](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L204-L204), [207-207](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L207-L207), [209-209](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L209-L209), [210-210](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L210-L210), [211-211](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L211-L211), [213-213](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L213-L213), [214-214](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L214-L214), [216-216](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L216-L216) ):

```solidity
26:     uint256[50] private __gap;

192:             chainId: 167_008,

195:             blockMaxProposals: 864_000,

196:             blockRingBufferSize: 864_100,

199:             blockMaxGasLimit: 15_000_000,

203:             blockMaxTxListBytes: 120_000,

204:             blobExpiry: 24 hours,

207:             livenessBond: 250e18, // 250 Taiko token

209:             ethDepositRingBufferSize: 1024,

210:             ethDepositMinCountPerBlock: 8,

211:             ethDepositMaxCountPerBlock: 32,

213:             ethDepositMaxAmount: 10_000 ether,

214:             ethDepositGas: 21_000,

216:             blockSyncThreshold: 16
```

- *TaikoToken.sol* ( [16-16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L16-L16), [41-41](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L41-L41) ):

```solidity
16:     uint256[50] private __gap;

41:         _mint(_recipient, 1_000_000_000 ether);
```

- *TaikoGovernor.sol* ( [23-23](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L23-L23), [43-43](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L43-L43), [112-112](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L112-L112), [118-118](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L118-L118), [124-124](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L124-L124) ):

```solidity
23:     uint256[50] private __gap;

43:         __GovernorVotesQuorumFraction_init(4);

112:         return 7200; // 1 day

118:         return 50_400; // 1 week

124:         return 1_000_000_000 ether / 10_000; // 0.01% of Taiko Token
```

- *TaikoTimelockController.sol* ( [10-10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L10-L10) ):

```solidity
10:     uint256[50] private __gap;
```

- *AssignmentHook.sol* ( [40-40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L40-L40) ):

```solidity
40:     uint256[50] private __gap;
```

- *LibDepositing.sol* ( [89-89](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L89-L89), [151-151](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L151-L151) ):

```solidity
89:                     recipient: address(uint160(data >> 96)),

151:         return (uint256(uint160(_addr)) << 96) | _amount;
```

- *LibProving.sol* ( [192-192](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L192-L192), [415-415](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L415-L415) ):

```solidity
192:             bool returnLivenessBond = blk.livenessBond > 0 && _proof.data.length == 32

415:             + _tier.provingWindow * 60 >= block.timestamp;
```

- *LibVerifying.sol* ( [152-152](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L152-L152), [251-251](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L251-L251), [256-256](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L256-L256) ):

```solidity
152:                         uint256(ITierProvider(tierProvider).getTier(ts.tier).cooldownWindow) * 60

251:                 || _config.blockMaxTxListBytes > 128 * 1024 // calldata up to 128K

256:             || _config.ethDepositMaxCountPerBlock > 32
```

- *GuardianProver.sol* ( [11-11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/GuardianProver.sol#L11-L11) ):

```solidity
11:     uint256[50] private __gap;
```

- *Guardians.sol* ( [32-32](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L32-L32) ):

```solidity
32:     uint256[46] private __gap;
```

- *DevnetTierProvider.sol* ( [11-11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L11-L11), [24-24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L24-L24), [25-25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L25-L25), [26-26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L26-L26), [27-27](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L27-L27), [28-28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L28-L28), [37-37](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L37-L37), [38-38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L38-L38), [39-39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L39-L39) ):

```solidity
11:     uint256[50] private __gap;

24:                 validityBond: 250 ether, // TKO

25:                 contestBond: 500 ether, // TKO

26:                 cooldownWindow: 1440, //24 hours

27:                 provingWindow: 120, // 2 hours

28:                 maxBlocksToVerifyPerProof: 16

37:                 cooldownWindow: 60, //1 hours

38:                 provingWindow: 2880, // 48 hours

39:                 maxBlocksToVerifyPerProof: 16
```

- *MainnetTierProvider.sol* ( [11-11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L11-L11), [24-24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L24-L24), [25-25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L25-L25), [26-26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L26-L26), [27-27](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L27-L27), [28-28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L28-L28), [35-35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L35-L35), [36-36](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L36-L36), [37-37](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L37-L37), [38-38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L38-L38), [39-39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L39-L39), [48-48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L48-L48), [49-49](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L49-L49), [50-50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L50-L50), [59-59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L59-L59), [68-68](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L68-L68) ):

```solidity
11:     uint256[50] private __gap;

24:                 validityBond: 250 ether, // TKO

25:                 contestBond: 500 ether, // TKO

26:                 cooldownWindow: 1440, //24 hours

27:                 provingWindow: 60, // 1 hours

28:                 maxBlocksToVerifyPerProof: 8

35:                 validityBond: 500 ether, // TKO

36:                 contestBond: 1000 ether, // TKO

37:                 cooldownWindow: 1440, //24 hours

38:                 provingWindow: 240, // 4 hours

39:                 maxBlocksToVerifyPerProof: 4

48:                 cooldownWindow: 60, //1 hours

49:                 provingWindow: 2880, // 48 hours

50:                 maxBlocksToVerifyPerProof: 16

59:         tiers_ = new uint16[](3);

68:         if (_rand % 1000 == 0) return LibTiers.TIER_SGX_ZKVM;
```

- *TestnetTierProvider.sol* ( [11-11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L11-L11), [24-24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L24-L24), [25-25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L25-L25), [26-26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L26-L26), [27-27](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L27-L27), [28-28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L28-L28), [35-35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L35-L35), [36-36](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L36-L36), [37-37](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L37-L37), [38-38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L38-L38), [39-39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L39-L39), [48-48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L48-L48), [49-49](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L49-L49), [50-50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L50-L50), [59-59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L59-L59) ):

```solidity
11:     uint256[50] private __gap;

24:                 validityBond: 250 ether, // TKO

25:                 contestBond: 500 ether, // TKO

26:                 cooldownWindow: 1440, //24 hours

27:                 provingWindow: 30, // 0.5 hours

28:                 maxBlocksToVerifyPerProof: 12

35:                 validityBond: 500 ether, // TKO

36:                 contestBond: 1000 ether, // TKO

37:                 cooldownWindow: 1440, //24 hours

38:                 provingWindow: 60, // 1 hours

39:                 maxBlocksToVerifyPerProof: 8

48:                 cooldownWindow: 60, //1 hours

49:                 provingWindow: 2880, // 48 hours

50:                 maxBlocksToVerifyPerProof: 16

59:         tiers_ = new uint16[](3);
```

- *CrossChainOwned.sol* ( [21-21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L21-L21) ):

```solidity
21:     uint256[49] private __gap;
```

- *TaikoL2.sol* ( [52-52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L52-L52), [202-202](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L202-L202), [213-213](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L213-L213), [214-214](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L214-L214), [228-228](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L228-L228), [234-234](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L234-L234), [236-236](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L236-L236), [240-240](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L240-L240), [246-246](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L246-L246) ):

```solidity
52:     uint256[47] private __gap;

202:         if (_blockId + 256 >= block.number) return blockhash(_blockId);

213:         config_.gasTargetPerL1Block = 15 * 1e6 * 4;

214:         config_.basefeeAdjustmentQuotient = 8;

228:         bytes32[256] memory inputs;

234:             for (uint256 i; i < 255 && _blockId >= i + 1; ++i) {

236:                 inputs[j % 255] = blockhash(j);

240:         inputs[255] = bytes32(block.chainid);

246:         inputs[_blockId % 255] = blockhash(_blockId);
```

- *TaikoL2EIP1559Configurable.sol* ( [13-13](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L13-L13) ):

```solidity
13:     uint256[49] private __gap;
```

- *AutomataDcapV3Attestation.sol* ( [313-313](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L313-L313), [419-419](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L419-L419), [420-420](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L420-L420) ):

```solidity
313:         bytes32 expectedAuthDataHash = bytes32(qeEnclaveReport.reportData.substring(0, 32));

419:             parsedQuoteCerts = new IPEMCertChainLib.ECSha256Certificate[](3);

420:             for (uint256 i; i < 3; ++i) {
```

- *PEMCertChainLib.sol* ( [135-135](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L135-L135), [136-136](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L136-L136), [171-171](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L171-L171), [174-174](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L174-L174), [177-177](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L177-L177), [180-180](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L180-L180), [189-189](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L189-L189), [288-288](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L288-L288), [303-303](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L303-L303), [359-359](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L359-L359) ):

```solidity
135:                 (notBeforeTag != 0x17 && notBeforeTag == 0x18)

136:                     || (notAfterTag != 0x17 && notAfterTag != 0x18)

171:             sigPtr = NodePtr.getPtr(sigPtr.ixs() + 3, sigPtr.ixf() + 3, sigPtr.ixl());

174:             bytes memory sigX = _trimBytes(der.bytesAt(sigPtr), 32);

177:             bytes memory sigY = _trimBytes(der.bytesAt(sigPtr), 32);

180:             cert.pubKey = _trimBytes(der.bytesAt(subjectPublicKeyInfoPtr), 64);

189:             if (der[tbsPtr.ixs()] != 0xA3) {

288:             if (der[internalPtr.ixs()] != 0x06) {

303:                     if (der[extnValueOidPtr.ixs()] != 0x06) {

359:                 ? uint16(bytes2(svnValueBytes)) / 256
```

- *V3Parser.sol* ( [33-33](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L33-L33), [34-34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L34-L34), [38-38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L38-L38), [46-46](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L46-L46), [51-51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L51-L51), [78-78](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L78-L78), [79-79](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L79-L79), [83-83](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L83-L83), [84-84](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L84-L84), [88-88](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L88-L88), [92-92](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L92-L92), [95-95](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L95-L95), [96-96](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L96-L96), [97-97](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L97-L97), [106-106](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L106-L106), [107-107](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L107-L107), [108-108](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L108-L108), [109-109](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L109-L109), [110-110](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L110-L110), [111-111](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L111-L111), [114-114](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L114-L114), [138-138](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L138-L138), [139-139](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L139-L139), [140-140](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L140-L140), [141-141](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L141-L141), [142-142](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L142-L142), [143-143](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L143-L143), [144-144](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L144-L144), [145-145](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L145-L145), [146-146](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L146-L146), [147-147](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L147-L147), [148-148](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L148-L148), [149-149](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L149-L149), [155-155](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L155-L155), [156-156](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L156-L156), [158-158](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L158-L158), [159-159](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L159-L159), [180-180](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L180-L180), [185-185](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L185-L185), [194-194](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L194-L194), [197-197](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L197-L197), [212-212](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L212-L212), [213-213](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L213-L213), [215-215](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L215-L215), [218-218](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L218-L218), [222-222](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L222-L222), [223-223](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L223-L223), [227-227](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L227-L227), [228-228](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L228-L228), [229-229](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L229-L229), [231-231](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L231-L231), [249-249](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L249-L249), [250-250](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L250-L250), [273-273](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L273-L273), [278-278](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L278-L278), [280-280](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L280-L280), [281-281](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L281-L281) ):

```solidity
33:         uint256 localAuthDataSize = littleEndianDecode(quote.substring(432, 4));

34:         if (quote.length - 436 != localAuthDataSize) {

38:         bytes memory rawHeader = quote.substring(0, 48);

46:             parseAuthDataAndVerifyCertType(quote.substring(436, localAuthDataSize), pemCertLibAddr);

51:         bytes memory rawLocalEnclaveReport = quote.substring(48, 384);

78:             localEnclaveReport.reserved3.length == 96 && localEnclaveReport.reserved4.length == 60

79:                 && localEnclaveReport.reportData.length == 64,

83:             pckSignedQeReport.reserved3.length == 96 && pckSignedQeReport.reserved4.length == 60

84:                 && pckSignedQeReport.reportData.length == 64,

88:             v3Quote.v3AuthData.certification.certType == 5,

92:             v3Quote.v3AuthData.certification.decodedCertDataArray.length == 3, "3 certs in chain"

95:             v3Quote.v3AuthData.ecdsa256BitSignature.length == 64

96:                 && v3Quote.v3AuthData.ecdsaAttestationKey.length == 64

97:                 && v3Quote.v3AuthData.qeReportSignature.length == 64,

106:         uint32 totalQuoteSize = 48 // header

107:             + 384 // local QE report

108:             + 64 // ecdsa256BitSignature

109:             + 64 // ecdsaAttestationKey

110:             + 384 // QE report

111:             + 64 // qeReportSignature

114:             + 4 // sizeof(v3Quote.v3AuthData.certification.certDataSize)

138:         enclaveReport.cpuSvn = bytes16(rawEnclaveReport.substring(0, 16));

139:         enclaveReport.miscSelect = bytes4(rawEnclaveReport.substring(16, 4));

140:         enclaveReport.reserved1 = bytes28(rawEnclaveReport.substring(20, 28));

141:         enclaveReport.attributes = bytes16(rawEnclaveReport.substring(48, 16));

142:         enclaveReport.mrEnclave = bytes32(rawEnclaveReport.substring(64, 32));

143:         enclaveReport.reserved2 = bytes32(rawEnclaveReport.substring(96, 32));

144:         enclaveReport.mrSigner = bytes32(rawEnclaveReport.substring(128, 32));

145:         enclaveReport.reserved3 = rawEnclaveReport.substring(160, 96);

146:         enclaveReport.isvProdId = uint16(littleEndianDecode(rawEnclaveReport.substring(256, 2)));

147:         enclaveReport.isvSvn = uint16(littleEndianDecode(rawEnclaveReport.substring(258, 2)));

148:         enclaveReport.reserved4 = rawEnclaveReport.substring(260, 60);

149:         enclaveReport.reportData = rawEnclaveReport.substring(320, 64);

155:             uint256 upperDigit = digits / 16;

156:             uint256 lowerDigit = digits % 16;

158:             uint256 acc = lowerDigit * (16 ** (2 * i));

159:             acc += upperDigit * (16 ** ((2 * i) + 1));

180:         bytes4 teeType = bytes4(rawHeader.substring(4, 4));

185:         bytes16 qeVendorId = bytes16(rawHeader.substring(12, 16));

194:             qeSvn: bytes2(rawHeader.substring(8, 2)),

197:             userData: bytes20(rawHeader.substring(28, 20))

212:         qeAuthData.parsedDataSize = uint16(littleEndianDecode(rawAuthData.substring(576, 2)));

213:         qeAuthData.data = rawAuthData.substring(578, qeAuthData.parsedDataSize);

215:         uint256 offset = 578 + qeAuthData.parsedDataSize;

218:         if (cert.certType < 1 || cert.certType > 5) {

222:         cert.certDataSize = uint32(littleEndianDecode(rawAuthData.substring(offset, 4)));

223:         offset += 4;

227:         authDataV3.ecdsa256BitSignature = rawAuthData.substring(0, 64);

228:         authDataV3.ecdsaAttestationKey = rawAuthData.substring(64, 64);

229:         bytes memory rawQeReport = rawAuthData.substring(128, 384);

231:         authDataV3.qeReportSignature = rawAuthData.substring(512, 64);

249:         uint16 isvProdIdPackBE = (enclaveReport.isvProdId >> 8) | (enclaveReport.isvProdId << 8);

250:         uint16 isvSvnPackBE = (enclaveReport.isvSvn >> 8) | (enclaveReport.isvSvn << 8);

273:         returns (bytes[3] memory certChainData)

278:             pemCertLib.splitCertificateChain(certBytes, 3);

280:         parsedQuoteCerts = new IPEMCertChainLib.ECSha256Certificate[](3);

281:         for (uint256 i; i < 3; ++i) {
```

- *V3Struct.sol* ( [44-44](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L44-L44) ):

```solidity
44:         bytes[3] decodedCertDataArray; // base64 decoded cert bytes array
```

- *Asn1Decode.sol* ( [20-20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L20-L20), [25-25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L25-L25), [30-30](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L30-L30), [31-31](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L31-L31), [57-57](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L57-L57), [67-67](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L67-L67), [88-88](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L88-L88), [142-142](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L142-L142), [143-143](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L143-L143), [145-145](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L145-L145), [155-155](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L155-L155), [156-156](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L156-L156), [180-180](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L180-L180), [182-182](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L182-L182), [191-191](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L191-L191), [196-196](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L196-L196), [203-203](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L203-L203) ):

```solidity
20:         return uint80(self >> 80);

25:         return uint80(self >> 160);

30:         _ixs |= _ixf << 80;

31:         _ixs |= _ixl << 160;

57:         require(der[ptr.ixs()] == 0x03, "Not type BIT STRING");

67:         require(der[ptr.ixs()] == 0x04, "Not type OCTET STRING");

88:         require(der[ptr.ixs()] & 0x20 == 0x20, "Not a constructed type");

142:         require(der[ptr.ixs()] == 0x02, "Not type INTEGER");

143:         require(der[ptr.ixf()] & 0x80 == 0, "Not positive");

145:         return uint256(der.readBytesN(ptr.ixf(), len) >> (32 - len) * 8);

155:         require(der[ptr.ixs()] == 0x02, "Not type INTEGER");

156:         require(der[ptr.ixf()] & 0x80 == 0, "Not positive");

180:         require(der[ptr.ixs()] == 0x03, "ixs Not type BIT STRING 0x03");

182:         require(der[ptr.ixf()] == 0x00, "ixf Not 0");

191:         if ((der[ix + 1] & 0x80) == 0) {

196:             uint8 lengthbytesLength = uint8(der[ix + 1] & 0x7F);

203:                     der.readBytesN(ix + 2, lengthbytesLength) >> (32 - lengthbytesLength) * 8
```

</details>

### [N-41] Expressions for constant values should use `immutable` rather than `constant`

While it doesn't save any gas because the compiler knows that developers often make this mistake, it's still best to use the right tool for the task at hand. There is a difference between `constant` variables and `immutable` variables, and they should each be used in their appropriate contexts. `constants` should be used for literal values written into the code, and `immutable` variables should be used for expressions, or values calculated in, or passed into the constructor.

There are 3 instances:

- *LibProving.sol* ( [20-20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L20-L20) ):

```solidity
20:     bytes32 public constant RETURN_LIVENESS_BOND = keccak256("RETURN_LIVENESS_BOND");
```

- *LibSignals.sol* ( [8-8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/LibSignals.sol#L8-L8), [11-11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/LibSignals.sol#L11-L11) ):

```solidity
8:     bytes32 public constant STATE_ROOT = keccak256("STATE_ROOT");

11:     bytes32 public constant SIGNAL_ROOT = keccak256("SIGNAL_ROOT");
```

### [N-42] Consider moving duplicated strings to constants

Moving duplicate strings to constants can improve code maintainability and readability.

<details>
<summary>There are 69 instances (click to show):</summary>

- *AssignmentHook.sol* ( [70-70](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L70-L70), [101-101](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L101-L101) ):

```solidity
70:         onlyFromNamed("taiko")

101:         IERC20 tko = IERC20(resolve("taiko_token", false));
```

- *LibDepositing.sol* ( [41-41](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L41-L41) ):

```solidity
41:         _resolver.resolve("bridge", false).sendEther(msg.value);
```

- *LibProposing.sol* ( [207-207](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L207-L207), [237-237](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L237-L237) ):

```solidity
207:         meta_.minTier = ITierProvider(_resolver.resolve("tier_provider", false)).getMinTier(

237:             IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));
```

- *LibProving.sol* ( [141-141](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L141-L141), [187-187](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L187-L187) ):

```solidity
141:             ITierProvider(_resolver.resolve("tier_provider", false)).getTier(_proof.tier);

187:         IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));
```

- *LibVerifying.sol* ( [149-149](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L149-L149), [188-188](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L188-L188), [232-232](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L232-L232) ):

```solidity
149:                         tierProvider = _resolver.resolve("tier_provider", false);

188:                 IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));

232:         ISignalService signalService = ISignalService(_resolver.resolve("signal_service", false));
```

- *GuardianProver.sol* ( [51-51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/GuardianProver.sol#L51-L51) ):

```solidity
51:             ITaikoL1(resolve("taiko", false)).proveBlock(_meta.id, abi.encode(_meta, _tran, _proof));
```

- *DevnetTierProvider.sol* ( [23-23](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L23-L23), [34-34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L34-L34) ):

```solidity
23:                 verifierName: "tier_optimistic",

34:                 verifierName: "tier_guardian",
```

- *MainnetTierProvider.sol* ( [23-23](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L23-L23), [45-45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L45-L45) ):

```solidity
23:                 verifierName: "tier_sgx",

45:                 verifierName: "tier_guardian",
```

- *TestnetTierProvider.sol* ( [23-23](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L23-L23), [34-34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L34-L34), [45-45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L45-L45) ):

```solidity
23:                 verifierName: "tier_optimistic",

34:                 verifierName: "tier_sgx",

45:                 verifierName: "tier_guardian",
```

- *CrossChainOwned.sol* ( [40-40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L40-L40) ):

```solidity
40:         onlyFromNamed("bridge")
```

- *TaikoL2.sol* ( [148-148](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L148-L148) ):

```solidity
148:             ISignalService(resolve("signal_service", false)).syncChainData(
```

- *Asn1Decode.sol* ( [142-142](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L142-L142), [143-143](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L143-L143), [155-155](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L155-L155), [156-156](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L156-L156) ):

```solidity
142:         require(der[ptr.ixs()] == 0x02, "Not type INTEGER");

143:         require(der[ptr.ixf()] & 0x80 == 0, "Not positive");

155:         require(der[ptr.ixs()] == 0x02, "Not type INTEGER");

156:         require(der[ptr.ixf()] & 0x80 == 0, "Not positive");
```

- *BytesUtils.sol* ( [212-212](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L212-L212), [225-225](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L225-L225), [238-238](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L238-L238), [264-264](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L264-L264), [265-265](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L265-L265), [329-329](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L329-L329), [365-365](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L365-L365) ):

```solidity
212:         require(idx + 4 <= self.length, "unexpected idx");

225:         require(idx + 32 <= self.length, "unexpected idx");

238:         require(idx + 20 <= self.length, "unexpected idx");

264:         require(len <= 32, "unexpected len");

265:         require(idx + len <= self.length, "unexpected idx");

329:         require(len <= 52, "unexpected len");

365:             revert("unexpected len");
```

- *SigVerifyLib.sol* ( [50-50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L50-L50), [75-75](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L75-L75) ):

```solidity
50:             revert("Unsupported algorithm");

75:             revert("Unsupported algorithm");
```

- *Bridge.sol* ( [87-87](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L87-L87), [106-106](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L106-L106), [150-150](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L150-L150), [172-172](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L172-L172), [229-229](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L229-L229), [342-342](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L342-L342), [363-363](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L363-L363), [384-384](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L384-L384), [397-397](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L397-L397), [522-522](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L522-L522), [589-589](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L589-L589) ):

```solidity
87:         onlyFromOwnerOrNamed("bridge_watchdog")

106:         onlyFromOwnerOrNamed("bridge_watchdog")

150:         ISignalService(resolve("signal_service", false)).sendSignal(msgHash_);

172:             address signalService = resolve("signal_service", false);

229:         address signalService = resolve("signal_service", false);

342:         return ISignalService(resolve("signal_service", false)).isSignalSent({

363:             resolve("signal_service", false),

384:             resolve("signal_service", false), hashMessage(_message), _message.srcChainId, _proof

397:         destBridge_ = resolve(_chainId, "bridge", true);

522:             ISignalService(resolve("signal_service", false)).sendSignal(

589:             (_chainId, resolve(_chainId, "bridge", false), _signal, _proof)
```

- *SignalService.sol* ( [101-101](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L101-L101), [117-117](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L117-L117) ):

```solidity
101:         address signalService = resolve(chainId, "signal_service", false);

117:                 signalService = resolve(hop.chainId, "signal_service", false);
```

- *Bytes.sol* ( [25-25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L25-L25), [26-26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L26-L26) ):

```solidity
25:             require(_length + 31 >= _length, "slice_overflow");

26:             require(_start + _length >= _start, "slice_overflow");
```

- *RLPReader.sol* ( [39-39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L39-L39), [154-154](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L154-L154) ):

```solidity
39:             "RLPReader: length of an RLP item must be greater than zero to be decodable"

154:             "RLPReader: length of an RLP item must be greater than zero to be decodable"
```

- *BaseVault.sol* ( [23-23](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L23-L23) ):

```solidity
23:         if (msg.sender != resolve("bridge", false)) {
```

- *BridgedERC1155.sol* ( [52-52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L52-L52), [52-52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L52-L52), [74-74](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L74-L74), [91-91](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L91-L91), [108-108](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L108-L108) ):

```solidity
52:         LibBridgedToken.validateInputs(_srcToken, _srcChainId, "foo", "foo");

52:         LibBridgedToken.validateInputs(_srcToken, _srcChainId, "foo", "foo");

74:         onlyFromNamed("erc1155_vault")

91:         onlyFromNamed("erc1155_vault")

108:         onlyFromNamed("erc1155_vault")
```

- *BridgedERC20Base.sol* ( [43-43](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L43-L43), [64-64](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L64-L64), [83-83](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L83-L83) ):

```solidity
43:         onlyFromOwnerOrNamed("erc20_vault")

64:         } else if (msg.sender != resolve("erc20_vault", true)) {

83:         } else if (msg.sender != resolve("erc20_vault", true)) {
```

- *BridgedERC721.sol* ( [61-61](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L61-L61), [76-76](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L76-L76) ):

```solidity
61:         onlyFromNamed("erc721_vault")

76:         onlyFromNamed("erc721_vault")
```

- *ERC1155Vault.sol* ( [77-77](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L77-L77), [205-205](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L205-L205) ):

```solidity
77:             IBridge(resolve("bridge", false)).sendMessage{ value: msg.value }(message);

205:         return "erc1155_vault";
```

- *ERC20Vault.sol* ( [239-239](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L239-L239), [317-317](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L317-L317) ):

```solidity
239:             IBridge(resolve("bridge", false)).sendMessage{ value: msg.value }(message);

317:         return "erc20_vault";
```

- *ERC721Vault.sol* ( [62-62](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L62-L62), [157-157](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L157-L157) ):

```solidity
62:             IBridge(resolve("bridge", false)).sendMessage{ value: msg.value }(message);

157:         return "erc721_vault";
```

- *SgxVerifier.sol* ( [145-145](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L145-L145), [181-181](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L181-L181) ):

```solidity
145:         onlyFromNamed("taiko")

181:         address taikoL1 = resolve("taiko", false);
```

</details>

### [N-43] Functions not used internally could be marked external

If desired, sub contracts can change the visibility from `external` to `public` by [overriding](https://docs.soliditylang.org/en/v0.8.20/contracts.html#function-overriding) the functions of their parents.

<details>
<summary>There are 65 instances (click to show):</summary>

- *TaikoL1.sol* ( [124-124](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L124-L124), [132-132](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L132-L132), [137-137](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L137-L137), [145-148](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L145-L148), [162-168](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L162-L168), [176-179](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L176-L179) ):

```solidity
124:     function unpause() public override {

132:     function canDepositEthToL2(uint256 _amount) public view returns (bool) {

137:     function isBlobReusable(bytes32 _blobHash) public view returns (bool) {

145:     function getBlock(uint64 _blockId)
146:         public
147:         view
148:         returns (TaikoData.Block memory blk_, TaikoData.TransitionState memory ts_)

162:     function getTransition(
163:         uint64 _blockId,
164:         bytes32 _parentHash
165:     )
166:         public
167:         view
168:         returns (TaikoData.TransitionState memory)

176:     function getStateVariables()
177:         public
178:         view
179:         returns (TaikoData.SlotA memory a_, TaikoData.SlotB memory b_)
```

- *TaikoToken.sol* ( [25-33](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L25-L33), [47-47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L47-L47), [52-52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L52-L52), [60-60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L60-L60), [70-77](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L70-L77) ):

```solidity
25:     function init(
26:         address _owner,
27:         string calldata _name,
28:         string calldata _symbol,
29:         address _recipient
30:     )
31:         public
32:         initializer
33:     {

47:     function burn(address _from, uint256 _amount) public onlyOwner {

52:     function snapshot() public onlyFromOwnerOrNamed("snapshooter") {

60:     function transfer(address _to, uint256 _amount) public override returns (bool) {

70:     function transferFrom(
71:         address _from,
72:         address _to,
73:         uint256 _amount
74:     )
75:         public
76:         override
77:         returns (bool)
```

- *TaikoGovernor.sol* ( [48-56](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L48-L56), [69-79](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L69-L79), [89-93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L89-L93), [99-103](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L99-L103), [111-111](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L111-L111), [117-117](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L117-L117), [123-123](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L123-L123) ):

```solidity
48:     function propose(
49:         address[] memory _targets,
50:         uint256[] memory _values,
51:         bytes[] memory _calldatas,
52:         string memory _description
53:     )
54:         public
55:         override(IGovernorUpgradeable, GovernorUpgradeable, GovernorCompatibilityBravoUpgradeable)
56:         returns (uint256)

69:     function propose(
70:         address[] memory _targets,
71:         uint256[] memory _values,
72:         string[] memory _signatures,
73:         bytes[] memory _calldatas,
74:         string memory _description
75:     )
76:         public
77:         virtual
78:         override(GovernorCompatibilityBravoUpgradeable)
79:         returns (uint256)

89:     function supportsInterface(bytes4 _interfaceId)
90:         public
91:         view
92:         override(GovernorUpgradeable, GovernorTimelockControlUpgradeable, IERC165Upgradeable)
93:         returns (bool)

99:     function state(uint256 _proposalId)
100:         public
101:         view
102:         override(IGovernorUpgradeable, GovernorUpgradeable, GovernorTimelockControlUpgradeable)
103:         returns (ProposalState)

111:     function votingDelay() public pure override returns (uint256) {

117:     function votingPeriod() public pure override returns (uint256) {

123:     function proposalThreshold() public pure override returns (uint256) {
```

- *TaikoTimelockController.sol* ( [24-24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L24-L24) ):

```solidity
24:     function getMinDelay() public view override returns (uint256) {
```

- *Guardians.sol* ( [107-107](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L107-L107) ):

```solidity
107:     function numGuardians() public view returns (uint256) {
```

- *DevnetTierProvider.sol* ( [20-20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L20-L20), [47-47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L47-L47), [54-54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L54-L54) ):

```solidity
20:     function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {

47:     function getTierIds() public pure override returns (uint16[] memory tiers_) {

54:     function getMinTier(uint256) public pure override returns (uint16) {
```

- *MainnetTierProvider.sol* ( [20-20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L20-L20), [58-58](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L58-L58), [66-66](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L66-L66) ):

```solidity
20:     function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {

58:     function getTierIds() public pure override returns (uint16[] memory tiers_) {

66:     function getMinTier(uint256 _rand) public pure override returns (uint16) {
```

- *TestnetTierProvider.sol* ( [20-20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L20-L20), [58-58](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L58-L58), [66-66](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L66-L66) ):

```solidity
20:     function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {

58:     function getTierIds() public pure override returns (uint16[] memory tiers_) {

66:     function getMinTier(uint256 _rand) public pure override returns (uint16) {
```

- *TaikoL2.sol* ( [185-191](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L185-L191), [200-200](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L200-L200) ):

```solidity
185:     function getBasefee(
186:         uint64 _l1BlockId,
187:         uint32 _parentGasUsed
188:     )
189:         public
190:         view
191:         returns (uint256 basefee_)

200:     function getBlockHash(uint64 _blockId) public view returns (bytes32) {
```

- *TaikoL2EIP1559Configurable.sol* ( [43-43](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L43-L43) ):

```solidity
43:     function getConfig() public view override returns (Config memory) {
```

- *AutomataDcapV3Attestation.sol* ( [103-109](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L103-L109) ):

```solidity
103:     function configureTcbInfoJson(
104:         string calldata fmspc,
105:         TCBInfoStruct.TCBInfo calldata tcbInfoInput
106:     )
107:         public
108:         onlyOwner
109:     {
```

- *SigVerifyLib.sol* ( [24-32](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L24-L32), [54-62](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L54-L62) ):

```solidity
24:     function verifyAttStmtSignature(
25:         bytes memory tbs,
26:         bytes memory signature,
27:         PublicKey memory publicKey,
28:         Algorithm alg
29:     )
30:         public
31:         view
32:         returns (bool)

54:     function verifyCertificateSignature(
55:         bytes memory tbs,
56:         bytes memory signature,
57:         PublicKey memory publicKey,
58:         CertSigAlgorithm alg
59:     )
60:         public
61:         view
62:         returns (bool)
```

- *Bridge.sol* ( [340-340](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L340-L340), [352-358](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L352-L358), [374-380](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L374-L380), [403-403](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L403-L403) ):

```solidity
340:     function isMessageSent(Message calldata _message) public view returns (bool) {

352:     function proveMessageFailed(
353:         Message calldata _message,
354:         bytes calldata _proof
355:     )
356:         public
357:         view
358:         returns (bool)

374:     function proveMessageReceived(
375:         Message calldata _message,
376:         bytes calldata _proof
377:     )
378:         public
379:         view
380:         returns (bool)

403:     function context() public view returns (Context memory ctx_) {
```

- *AddressManager.sol* ( [54-54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L54-L54) ):

```solidity
54:     function getAddress(uint64 _chainId, bytes32 _name) public view override returns (address) {
```

- *EssentialContract.sol* ( [69-69](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L69-L69) ):

```solidity
69:     function pause() public virtual whenNotPaused {
```

- *SignalService.sol* ( [83-93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L83-L93), [137-146](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L137-L146), [153-153](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L153-L153), [158-165](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L158-L165) ):

```solidity
83:     function proveSignalReceived(
84:         uint64 _chainId,
85:         address _app,
86:         bytes32 _signal,
87:         bytes calldata _proof
88:     )
89:         public
90:         virtual
91:         validSender(_app)
92:         nonZeroValue(_signal)
93:     {

137:     function isChainDataSynced(
138:         uint64 _chainId,
139:         bytes32 _kind,
140:         uint64 _blockId,
141:         bytes32 _chainData
142:     )
143:         public
144:         view
145:         nonZeroValue(_chainData)
146:         returns (bool)

153:     function isSignalSent(address _app, bytes32 _signal) public view returns (bool) {

158:     function getSyncedChainData(
159:         uint64 _chainId,
160:         bytes32 _kind,
161:         uint64 _blockId
162:     )
163:         public
164:         view
165:         returns (uint64 blockId_, bytes32 chainData_)
```

- *TimelockTokenPool.sol* ( [204-204](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L204-L204) ):

```solidity
204:     function getMyGrant(address _recipient) public view returns (Grant memory) {
```

- *BaseVault.sol* ( [39-39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L39-L39) ):

```solidity
39:     function supportsInterface(bytes4 _interfaceId) public view virtual override returns (bool) {
```

- *BridgedERC1155.sol* ( [66-75](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L66-L75), [83-92](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L83-L92), [100-109](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L100-L109), [115-115](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L115-L115), [121-121](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L121-L121) ):

```solidity
66:     function mint(
67:         address _to,
68:         uint256 _tokenId,
69:         uint256 _amount
70:     )
71:         public
72:         nonReentrant
73:         whenNotPaused
74:         onlyFromNamed("erc1155_vault")
75:     {

83:     function mintBatch(
84:         address _to,
85:         uint256[] memory _tokenIds,
86:         uint256[] memory _amounts
87:     )
88:         public
89:         nonReentrant
90:         whenNotPaused
91:         onlyFromNamed("erc1155_vault")
92:     {

100:     function burn(
101:         address _account,
102:         uint256 _tokenId,
103:         uint256 _amount
104:     )
105:         public
106:         nonReentrant
107:         whenNotPaused
108:         onlyFromNamed("erc1155_vault")
109:     {

115:     function name() public view returns (string memory) {

121:     function symbol() public view returns (string memory) {
```

- *BridgedERC20.sol* ( [91-95](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L91-L95), [102-106](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L102-L106), [113-117](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L113-L117), [125-125](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L125-L125) ):

```solidity
91:     function name()
92:         public
93:         view
94:         override(ERC20Upgradeable, IERC20MetadataUpgradeable)
95:         returns (string memory)

102:     function symbol()
103:         public
104:         view
105:         override(ERC20Upgradeable, IERC20MetadataUpgradeable)
106:         returns (string memory)

113:     function decimals()
114:         public
115:         view
116:         override(ERC20Upgradeable, IERC20MetadataUpgradeable)
117:         returns (uint8)

125:     function canonical() public view returns (address, uint256) {
```

- *BridgedERC20Base.sol* ( [57-57](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L57-L57), [75-75](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L75-L75) ):

```solidity
57:     function mint(address _account, uint256 _amount) public nonReentrant whenNotPaused {

75:     function burn(address _account, uint256 _amount) public nonReentrant whenNotPaused {
```

- *BridgedERC721.sol* ( [54-62](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L54-L62), [69-77](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L69-L77), [87-87](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L87-L87), [93-93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L93-L93), [100-100](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L100-L100), [107-107](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L107-L107) ):

```solidity
54:     function mint(
55:         address _account,
56:         uint256 _tokenId
57:     )
58:         public
59:         nonReentrant
60:         whenNotPaused
61:         onlyFromNamed("erc721_vault")
62:     {

69:     function burn(
70:         address _account,
71:         uint256 _tokenId
72:     )
73:         public
74:         nonReentrant
75:         whenNotPaused
76:         onlyFromNamed("erc721_vault")
77:     {

87:     function name() public view override(ERC721Upgradeable) returns (string memory) {

93:     function symbol() public view override(ERC721Upgradeable) returns (string memory) {

100:     function source() public view returns (address, uint256) {

107:     function tokenURI(uint256 _tokenId) public view virtual override returns (string memory) {
```

- *ERC1155Vault.sol* ( [192-197](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L192-L197) ):

```solidity
192:     function supportsInterface(bytes4 interfaceId)
193:         public
194:         view
195:         virtual
196:         override(BaseVault, ERC1155ReceiverUpgradeable)
197:         returns (bool)
```

</details>

### [N-44] Contracts containing only utility functions should be made into libraries

Consider using a `library` instead of a `contract` to provide utility functions.

There are 3 instances:

- *TaikoErrors.sol* ( [11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L11) ):

```solidity
11: abstract contract TaikoErrors {
```

- *TaikoEvents.sol* ( [13](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoEvents.sol#L13) ):

```solidity
13: abstract contract TaikoEvents {
```

- *PEMCertChainLib.sol* ( [12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L12) ):

```solidity
12: contract PEMCertChainLib is IPEMCertChainLib {
```

### [N-45] Error names should use CapWords style

It is recommended by the [Solidity Style Guide](https://docs.soliditylang.org/en/latest/style-guide.html)

<details>
<summary>There are 160 instances (click to show):</summary>

- *TaikoErrors.sol* ( [12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L12), [13](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L13), [14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L14), [15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L15), [16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L16), [17](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L17), [18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L18), [19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L19), [20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L20), [21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L21), [22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L22), [23](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L23), [24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L24), [25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L25), [26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L26), [27](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L27), [28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L28), [29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L29), [30](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L30), [31](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L31), [32](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L32), [33](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L33), [34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L34), [35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L35), [36](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L36), [37](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L37), [38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L38), [39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L39), [40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L40), [41](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L41), [42](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol#L42) ):

```solidity
12:     error L1_ALREADY_CONTESTED();

13:     error L1_ALREADY_PROVED();

14:     error L1_ASSIGNED_PROVER_NOT_ALLOWED();

15:     error L1_BLOB_FOR_DA_DISABLED();

16:     error L1_BLOB_NOT_FOUND();

17:     error L1_BLOB_NOT_REUSABLE();

18:     error L1_BLOB_REUSE_DISABLED();

19:     error L1_BLOCK_MISMATCH();

20:     error L1_INVALID_BLOCK_ID();

21:     error L1_INVALID_CONFIG();

22:     error L1_INVALID_ETH_DEPOSIT();

23:     error L1_INVALID_HOOK();

24:     error L1_INVALID_PARAM();

25:     error L1_INVALID_PAUSE_STATUS();

26:     error L1_INVALID_PROVER();

27:     error L1_INVALID_TIER();

28:     error L1_INVALID_TRANSITION();

29:     error L1_LIVENESS_BOND_NOT_RECEIVED();

30:     error L1_NOT_ASSIGNED_PROVER();

31:     error L1_PROPOSER_NOT_EOA();

32:     error L1_PROVING_PAUSED();

33:     error L1_RECEIVE_DISABLED();

34:     error L1_MISSING_VERIFIER();

35:     error L1_TOO_MANY_BLOCKS();

36:     error L1_TOO_MANY_TIERS();

37:     error L1_TRANSITION_ID_ZERO();

38:     error L1_TRANSITION_NOT_FOUND();

39:     error L1_TXLIST_SIZE();

40:     error L1_UNAUTHORIZED();

41:     error L1_UNEXPECTED_PARENT();

42:     error L1_UNEXPECTED_TRANSITION_ID();
```

- *TaikoToken.sol* ( [18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L18) ):

```solidity
18:     error TKO_INVALID_ADDR();
```

- *TaikoGovernor.sol* ( [25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L25) ):

```solidity
25:     error TG_INVALID_SIGNATURES_LENGTH();
```

- *AssignmentHook.sol* ( [50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L50), [51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L51), [52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L52) ):

```solidity
50:     error HOOK_ASSIGNMENT_EXPIRED();

51:     error HOOK_ASSIGNMENT_INVALID_SIG();

52:     error HOOK_TIER_NOT_FOUND();
```

- *LibDepositing.sol* ( [22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L22) ):

```solidity
22:     error L1_INVALID_ETH_DEPOSIT();
```

- *LibProposing.sol* ( [44](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L44), [45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L45), [46](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L46), [47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L47), [48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L48), [49](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L49), [50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L50), [51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L51), [52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L52), [53](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L53), [54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L54), [55](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L55), [56](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L56), [57](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L57) ):

```solidity
44:     error L1_BLOB_FOR_DA_DISABLED();

45:     error L1_BLOB_NOT_FOUND();

46:     error L1_BLOB_NOT_REUSABLE();

47:     error L1_BLOB_REUSE_DISABLED();

48:     error L1_INVALID_HOOK();

49:     error L1_INVALID_PARAM();

50:     error L1_INVALID_PROVER();

51:     error L1_LIVENESS_BOND_NOT_RECEIVED();

52:     error L1_PROPOSER_NOT_EOA();

53:     error L1_TOO_MANY_BLOCKS();

54:     error L1_TXLIST_OFFSET();

55:     error L1_TXLIST_SIZE();

56:     error L1_UNAUTHORIZED();

57:     error L1_UNEXPECTED_PARENT();
```

- *LibProving.sol* ( [59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L59), [60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L60), [61](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L61), [62](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L62), [63](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L63), [64](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L64), [65](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L65), [66](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L66), [67](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L67), [68](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L68) ):

```solidity
59:     error L1_ALREADY_CONTESTED();

60:     error L1_ALREADY_PROVED();

61:     error L1_ASSIGNED_PROVER_NOT_ALLOWED();

62:     error L1_BLOCK_MISMATCH();

63:     error L1_INVALID_BLOCK_ID();

64:     error L1_INVALID_PAUSE_STATUS();

65:     error L1_INVALID_TIER();

66:     error L1_INVALID_TRANSITION();

67:     error L1_MISSING_VERIFIER();

68:     error L1_NOT_ASSIGNED_PROVER();
```

- *LibUtils.sol* ( [11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L11), [12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L12), [13](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L13), [14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L14) ):

```solidity
11:     error L1_BLOCK_MISMATCH();

12:     error L1_INVALID_BLOCK_ID();

13:     error L1_TRANSITION_NOT_FOUND();

14:     error L1_UNEXPECTED_TRANSITION_ID();
```

- *LibVerifying.sol* ( [39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L39), [40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L40), [41](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L41) ):

```solidity
39:     error L1_BLOCK_MISMATCH();

40:     error L1_INVALID_CONFIG();

41:     error L1_TRANSITION_ID_ZERO();
```

- *Guardians.sol* ( [45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L45), [46](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L46), [47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L47), [48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L48) ):

```solidity
45:     error INVALID_GUARDIAN();

46:     error INVALID_GUARDIAN_SET();

47:     error INVALID_MIN_GUARDIANS();

48:     error INVALID_PROOF();
```

- *ITierProvider.sol* ( [17](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L17) ):

```solidity
17:     error TIER_NOT_FOUND();
```

- *CrossChainOwned.sol* ( [28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L28), [29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L29), [30](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L30), [31](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L31) ):

```solidity
28:     error XCO_INVALID_OWNER_CHAINID();

29:     error XCO_INVALID_TX_ID();

30:     error XCO_PERMISSION_DENIED();

31:     error XCO_TX_REVERTED();
```

- *Lib1559Math.sol* ( [11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/Lib1559Math.sol#L11) ):

```solidity
11:     error EIP1559_INVALID_PARAMS();
```

- *TaikoL2.sol* ( [59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L59), [60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L60), [61](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L61), [62](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L62), [63](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L63), [64](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L64) ):

```solidity
59:     error L2_BASEFEE_MISMATCH();

60:     error L2_INVALID_CHAIN_ID();

61:     error L2_INVALID_PARAM();

62:     error L2_INVALID_SENDER();

63:     error L2_PUBLIC_INPUT_HASH_MISMATCH();

64:     error L2_TOO_LATE();
```

- *TaikoL2EIP1559Configurable.sol* ( [20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L20) ):

```solidity
20:     error L2_INVALID_CONFIG();
```

- *Bridge.sol* ( [50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L50), [51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L51), [52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L52), [53](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L53), [54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L54), [55](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L55), [56](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L56), [57](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L57), [58](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L58), [59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L59), [60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L60), [61](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L61), [62](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L62) ):

```solidity
50:     error B_INVALID_CHAINID();

51:     error B_INVALID_CONTEXT();

52:     error B_INVALID_GAS_LIMIT();

53:     error B_INVALID_STATUS();

54:     error B_INVALID_USER();

55:     error B_INVALID_VALUE();

56:     error B_MESSAGE_NOT_SENT();

57:     error B_NON_RETRIABLE();

58:     error B_NOT_FAILED();

59:     error B_NOT_RECEIVED();

60:     error B_PERMISSION_DENIED();

61:     error B_STATUS_MISMATCH();

62:     error B_INVOCATION_TOO_EARLY();
```

- *AddressManager.sol* ( [25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L25), [26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L26) ):

```solidity
25:     error AM_INVALID_PARAMS();

26:     error AM_UNSUPPORTED();
```

- *AddressResolver.sol* ( [16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L16), [17](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L17), [18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L18), [19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L19) ):

```solidity
16:     error RESOLVER_DENIED();

17:     error RESOLVER_INVALID_MANAGER();

18:     error RESOLVER_UNEXPECTED_CHAINID();

19:     error RESOLVER_ZERO_ADDR(uint64 chainId, bytes32 name);
```

- *EssentialContract.sol* ( [35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L35), [36](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L36), [37](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L37) ):

```solidity
35:     error REENTRANT_CALL();

36:     error INVALID_PAUSE_STATUS();

37:     error ZERO_ADDR_MANAGER();
```

- *Lib4844.sol* ( [19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/Lib4844.sol#L19), [20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/Lib4844.sol#L20), [21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/Lib4844.sol#L21), [22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/Lib4844.sol#L22) ):

```solidity
19:     error EVAL_FAILED_1();

20:     error EVAL_FAILED_2();

21:     error POINT_X_TOO_LARGE();

22:     error POINT_Y_TOO_LARGE();
```

- *LibAddress.sol* ( [16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L16) ):

```solidity
16:     error ETH_TRANSFER_FAILED();
```

- *LibTrieProof.sol* ( [20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibTrieProof.sol#L20), [21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibTrieProof.sol#L21) ):

```solidity
20:     error LTP_INVALID_ACCOUNT_PROOF();

21:     error LTP_INVALID_INCLUSION_PROOF();
```

- *SignalService.sol* ( [25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L25), [26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L26), [27](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L27), [28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L28), [29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L29), [30](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L30), [31](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L31), [32](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L32), [33](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L33) ):

```solidity
25:     error SS_EMPTY_PROOF();

26:     error SS_INVALID_SENDER();

27:     error SS_INVALID_LAST_HOP_CHAINID();

28:     error SS_INVALID_MID_HOP_CHAINID();

29:     error SS_INVALID_STATE();

30:     error SS_INVALID_VALUE();

31:     error SS_SIGNAL_NOT_FOUND();

32:     error SS_UNAUTHORIZED();

33:     error SS_UNSUPPORTED();
```

- *TimelockTokenPool.sol* ( [101](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L101), [102](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L102), [103](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L103), [104](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L104) ):

```solidity
101:     error ALREADY_GRANTED();

102:     error INVALID_GRANT();

103:     error INVALID_PARAM();

104:     error NOTHING_TO_VOID();
```

- *ERC20Airdrop2.sol* ( [37](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L37) ):

```solidity
37:     error WITHDRAWALS_NOT_ONGOING();
```

- *MerkleClaimable.sol* ( [29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L29), [30](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L30), [31](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L31) ):

```solidity
29:     error CLAIM_NOT_ONGOING();

30:     error CLAIMED_ALREADY();

31:     error INVALID_PROOF();
```

- *BaseNFTVault.sol* ( [133](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L133), [134](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L134), [135](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L135), [136](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L136), [137](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L137), [138](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L138) ):

```solidity
133:     error VAULT_INVALID_TOKEN();

134:     error VAULT_INVALID_AMOUNT();

135:     error VAULT_INVALID_TO();

136:     error VAULT_INTERFACE_NOT_SUPPORTED();

137:     error VAULT_TOKEN_ARRAY_MISMATCH();

138:     error VAULT_MAX_TOKEN_PER_TXN_EXCEEDED();
```

- *BaseVault.sol* ( [20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L20) ):

```solidity
20:     error VAULT_PERMISSION_DENIED();
```

- *BridgedERC1155.sol* ( [29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L29) ):

```solidity
29:     error BTOKEN_CANNOT_RECEIVE();
```

- *BridgedERC20.sol* ( [34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L34), [35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L35) ):

```solidity
34:     error BTOKEN_CANNOT_RECEIVE();

35:     error BTOKEN_UNAUTHORIZED();
```

- *BridgedERC20Base.sol* ( [29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L29), [30](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L30), [31](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L31) ):

```solidity
29:     error BB_PERMISSION_DENIED();

30:     error BB_INVALID_PARAMS();

31:     error BB_MINT_DISALLOWED();
```

- *BridgedERC721.sol* ( [21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L21), [22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L22) ):

```solidity
21:     error BTOKEN_CANNOT_RECEIVE();

22:     error BTOKEN_INVALID_BURN();
```

- *ERC20Vault.sol* ( [136](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L136), [137](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L137), [138](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L138), [139](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L139), [140](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L140), [141](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L141), [142](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L142) ):

```solidity
136:     error VAULT_BTOKEN_BLACKLISTED();

137:     error VAULT_CTOKEN_MISMATCH();

138:     error VAULT_INVALID_TOKEN();

139:     error VAULT_INVALID_AMOUNT();

140:     error VAULT_INVALID_NEW_BTOKEN();

141:     error VAULT_INVALID_TO();

142:     error VAULT_NOT_SAME_OWNER();
```

- *LibBridgedToken.sol* ( [9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L9) ):

```solidity
9:     error BTOKEN_INVALID_PARAMS();
```

- *GuardianVerifier.sol* ( [13](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L13) ):

```solidity
13:     error PERMISSION_DENIED();
```

- *SgxVerifier.sol* ( [74](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L74), [75](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L75), [76](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L76), [77](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L77), [78](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L78) ):

```solidity
74:     error SGX_ALREADY_ATTESTED();

75:     error SGX_INVALID_ATTESTATION();

76:     error SGX_INVALID_INSTANCE();

77:     error SGX_INVALID_PROOF();

78:     error SGX_RA_NOT_SUPPORTED();
```

</details>

### [N-46] Functions should be named in mixedCase style

As the [Solidity Style Guide](https://docs.soliditylang.org/en/v0.8.21/style-guide.html#function-names) suggests: functions should be named in mixedCase style.

<details>
<summary>There are 16 instances (click to show):</summary>

- *CrossChainOwned.sol* ( [60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L60) ):

```solidity
60:     function __CrossChainOwned_init(
```

- *AutomataDcapV3Attestation.sol* ( [175](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L175) ):

```solidity
175:     function _verifyQEReportWithIdentity(V3Struct.EnclaveReport memory quoteEnclaveReport)
```

- *ISigVerifyLib.sol* ( [58](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L58), [67](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L67), [76](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L76) ):

```solidity
58:     function verifyRS256Signature(

67:     function verifyRS1Signature(

76:     function verifyES256Signature(
```

- *V3Parser.sol* ( [244](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L244) ):

```solidity
244:     function packQEReport(V3Struct.EnclaveReport memory enclaveReport)
```

- *BytesUtils.sol* ( [255](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L255) ):

```solidity
255:     function readBytesN(
```

- *SigVerifyLib.sol* ( [79](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L79), [96](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L96), [113](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L113) ):

```solidity
79:     function verifyRS256Signature(

96:     function verifyRS1Signature(

113:     function verifyES256Signature(
```

- *AddressResolver.sol* ( [58](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L58) ):

```solidity
58:     function __AddressResolver_init(address _addressManager) internal virtual onlyInitializing {
```

- *EssentialContract.sol* ( [95](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L95), [109](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L109) ):

```solidity
95:     function __Essential_init(

109:     function __Essential_init(address _owner) internal virtual {
```

- *LibAddress.sol* ( [77](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L77) ):

```solidity
77:     function isSenderEOA() internal view returns (bool) {
```

- *MerkleClaimable.sol* ( [56](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L56) ):

```solidity
56:     function __MerkleClaimable_init(
```

- *RLPReader.sol* ( [35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L35) ):

```solidity
35:     function toRLPItem(bytes memory _in) internal pure returns (RLPItem memory out_) {
```

</details>

### [N-47] Variable names for `immutable`s should use UPPER_CASE_WITH_UNDERSCORES

For `immutable` variable names, each word should use all capital letters, with underscores separating each word (UPPER_CASE_WITH_UNDERSCORES)

There are 2 instances:

- *AutomataDcapV3Attestation.sol* ( [25-25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L25-L25), [26-26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L26-L26) ):

```solidity
25:     ISigVerifyLib public immutable sigVerifyLib;

26:     IPEMCertChainLib public immutable pemCertLib;
```

### [N-48] Order of contract layout does not follow the Solidity Style Guide

As suggested by the [Solidity Style Guide](https://docs.soliditylang.org/en/v0.8.20/style-guide.html#order-of-layout):
- Layout contract elements in the following order: `pragma statements`, `import statements`, `interfaces`, `libraries`, `contracts`.
- Inside each contract, library or interface, use the following order: `type declarations`, `state variables`, `events`, `errors`, `modifiers`, `functions`.

There are 2 instances:

- *AutomataDcapV3Attestation.sol* ( [60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L60) ):

```solidity
/// @audit ↑ Out of order with constructor ()
60:     modifier onlyOwner() {
```

- *BytesUtils.sol* ( [310](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L310) ):

```solidity
/// @audit ↑ Out of order with function substring()
310:     bytes constant BASE32_HEX_TABLE =
```

### [N-49] Consider adding validation of user inputs

There are no validations done on the arguments below. Consider that the Solidity [documentation](https://docs.soliditylang.org/en/latest/control-structures.html#panic-via-assert-and-error-via-require) states that `Properly functioning code should never create a Panic, not even on invalid external input. If this happens, then there is a bug in your contract which you should fix`. This means that there should be explicit checks for expected ranges of inputs. Underflows/overflows result in panics should not be used as range checks, and allowing funds to be sent to  `0x0`, which is the default value of address variables and has many gotchas, should be avoided.

<details>
<summary>There are 20 instances (click to show):</summary>

- *TaikoL1.sol* ( [119-119](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L119-L119) ):

```solidity
/// @audit `_recipient not checked`
119:     function depositEtherToL2(address _recipient) external payable nonReentrant whenNotPaused {
```

- *TaikoToken.sol* ( [47-47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L47-L47), [70-74](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L70-L74) ):

```solidity
/// @audit `_from not checked`
47:     function burn(address _from, uint256 _amount) public onlyOwner {

/// @audit `_from not checked`
70:     function transferFrom(
71:         address _from,
72:         address _to,
73:         uint256 _amount
74:     )
```

- *TaikoGovernor.sol* ( [48-53](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L48-L53), [69-75](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L69-L75) ):

```solidity
/// @audit `_targets not checked`
48:     function propose(
49:         address[] memory _targets,
50:         uint256[] memory _values,
51:         bytes[] memory _calldatas,
52:         string memory _description
53:     )

/// @audit `_targets not checked`
69:     function propose(
70:         address[] memory _targets,
71:         uint256[] memory _values,
72:         string[] memory _signatures,
73:         bytes[] memory _calldatas,
74:         string memory _description
75:     )
```

- *Guardians.sol* ( [53-56](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L53-L56) ):

```solidity
/// @audit `_newGuardians not checked`
53:     function setGuardians(
54:         address[] memory _newGuardians,
55:         uint8 _minGuardians
56:     )
```

- *Bridge.sol* ( [101-104](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L101-L104) ):

```solidity
/// @audit `_addr not checked`
101:     function banAddress(
102:         address _addr,
103:         bool _ban
104:     )
```

- *SignalService.sol* ( [56-56](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L56-L56) ):

```solidity
/// @audit `_addr not checked`
56:     function authorize(address _addr, bool _authorize) external onlyOwner {
```

- *TimelockTokenPool.sol* ( [150-150](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L150-L150) ):

```solidity
/// @audit `_recipient not checked`
150:     function void(address _recipient) external onlyOwner {
```

- *ERC20Airdrop.sol* ( [50-55](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L50-L55) ):

```solidity
/// @audit `user not checked`
50:     function claimAndDelegate(
51:         address user,
52:         uint256 amount,
53:         bytes32[] calldata proof,
54:         bytes calldata delegationData
55:     )
```

- *ERC20Airdrop2.sol* ( [78-78](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L78-L78), [88-88](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L88-L88) ):

```solidity
/// @audit `user not checked`
78:     function claim(address user, uint256 amount, bytes32[] calldata proof) external nonReentrant {

/// @audit `user not checked`
88:     function withdraw(address user) external ongoingWithdrawals {
```

- *ERC721Airdrop.sol* ( [47-51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L47-L51) ):

```solidity
/// @audit `user not checked`
47:     function claim(
48:         address user,
49:         uint256[] calldata tokenIds,
50:         bytes32[] calldata proof
51:     )
```

- *BridgedERC1155.sol* ( [66-70](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L66-L70), [83-87](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L83-L87), [100-104](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L100-L104) ):

```solidity
/// @audit `_to not checked`
66:     function mint(
67:         address _to,
68:         uint256 _tokenId,
69:         uint256 _amount
70:     )

/// @audit `_to not checked`
83:     function mintBatch(
84:         address _to,
85:         uint256[] memory _tokenIds,
86:         uint256[] memory _amounts
87:     )

/// @audit `_account not checked`
100:     function burn(
101:         address _account,
102:         uint256 _tokenId,
103:         uint256 _amount
104:     )
```

- *BridgedERC20.sol* ( [80-80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L80-L80) ):

```solidity
/// @audit `_snapshooter not checked`
80:     function setSnapshoter(address _snapshooter) external onlyOwner {
```

- *BridgedERC20Base.sol* ( [57-57](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L57-L57) ):

```solidity
/// @audit `_account not checked`
57:     function mint(address _account, uint256 _amount) public nonReentrant whenNotPaused {
```

- *BridgedERC721.sol* ( [54-57](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L54-L57) ):

```solidity
/// @audit `_account not checked`
54:     function mint(
55:         address _account,
56:         uint256 _tokenId
57:     )
```

- *SgxVerifier.sol* ( [90-90](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L90-L90) ):

```solidity
/// @audit `_instances not checked`
90:     function addInstances(address[] calldata _instances)
```

</details>

### [N-50] Named imports of parent contracts are missing

Consider adding named imports for all parent contracts.

<details>
<summary>There are 71 instances (click to show):</summary>

- *TaikoL1.sol* ( [22-22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L22-L22) ):

```solidity
/// @audit EssentialContract
/// @audit ITaikoL1
/// @audit TaikoEvents
/// @audit TaikoErrors
22: contract TaikoL1 is EssentialContract, ITaikoL1, TaikoEvents, TaikoErrors {
```

- *TaikoToken.sol* ( [15-15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L15-L15) ):

```solidity
/// @audit EssentialContract
/// @audit ERC20SnapshotUpgradeable
/// @audit ERC20VotesUpgradeable
15: contract TaikoToken is EssentialContract, ERC20SnapshotUpgradeable, ERC20VotesUpgradeable {
```

- *TaikoGovernor.sol* ( [16-21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L16-L21) ):

```solidity
/// @audit EssentialContract
/// @audit GovernorCompatibilityBravoUpgradeable
/// @audit GovernorVotesUpgradeable
/// @audit GovernorVotesQuorumFractionUpgradeable
/// @audit GovernorTimelockControlUpgradeable
16: contract TaikoGovernor is
17:     EssentialContract,
18:     GovernorCompatibilityBravoUpgradeable,
19:     GovernorVotesUpgradeable,
20:     GovernorVotesQuorumFractionUpgradeable,
21:     GovernorTimelockControlUpgradeable
```

- *TaikoTimelockController.sol* ( [9-9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L9-L9) ):

```solidity
/// @audit EssentialContract
/// @audit TimelockControllerUpgradeable
9: contract TaikoTimelockController is EssentialContract, TimelockControllerUpgradeable {
```

- *AssignmentHook.sol* ( [14-14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L14-L14) ):

```solidity
/// @audit EssentialContract
/// @audit IHook
14: contract AssignmentHook is EssentialContract, IHook {
```

- *GuardianProver.sol* ( [10-10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/GuardianProver.sol#L10-L10) ):

```solidity
/// @audit Guardians
10: contract GuardianProver is Guardians {
```

- *Guardians.sol* ( [9-9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L9-L9) ):

```solidity
/// @audit EssentialContract
9: abstract contract Guardians is EssentialContract {
```

- *DevnetTierProvider.sol* ( [10-10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L10-L10) ):

```solidity
/// @audit EssentialContract
/// @audit ITierProvider
10: contract DevnetTierProvider is EssentialContract, ITierProvider {
```

- *MainnetTierProvider.sol* ( [10-10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L10-L10) ):

```solidity
/// @audit EssentialContract
/// @audit ITierProvider
10: contract MainnetTierProvider is EssentialContract, ITierProvider {
```

- *TestnetTierProvider.sol* ( [10-10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L10-L10) ):

```solidity
/// @audit EssentialContract
/// @audit ITierProvider
10: contract TestnetTierProvider is EssentialContract, ITierProvider {
```

- *CrossChainOwned.sol* ( [14-14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L14-L14) ):

```solidity
/// @audit EssentialContract
/// @audit IMessageInvocable
14: abstract contract CrossChainOwned is EssentialContract, IMessageInvocable {
```

- *TaikoL2.sol* ( [21-21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L21-L21) ):

```solidity
/// @audit CrossChainOwned
21: contract TaikoL2 is CrossChainOwned {
```

- *TaikoL2EIP1559Configurable.sol* ( [9-9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L9-L9) ):

```solidity
/// @audit TaikoL2
9: contract TaikoL2EIP1559Configurable is TaikoL2 {
```

- *SigVerifyLib.sol* ( [15-15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L15-L15) ):

```solidity
/// @audit ISigVerifyLib
15: contract SigVerifyLib is ISigVerifyLib {
```

- *Bridge.sol* ( [16-16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L16-L16) ):

```solidity
/// @audit EssentialContract
/// @audit IBridge
16: contract Bridge is EssentialContract, IBridge {
```

- *AddressManager.sol* ( [10-10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L10-L10) ):

```solidity
/// @audit EssentialContract
/// @audit IAddressManager
10: contract AddressManager is EssentialContract, IAddressManager {
```

- *AddressResolver.sol* ( [11-11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L11-L11) ):

```solidity
/// @audit IAddressResolver
/// @audit Initializable
11: abstract contract AddressResolver is IAddressResolver, Initializable {
```

- *EssentialContract.sol* ( [10-10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L10-L10) ):

```solidity
/// @audit UUPSUpgradeable
/// @audit Ownable2StepUpgradeable
/// @audit AddressResolver
10: abstract contract EssentialContract is UUPSUpgradeable, Ownable2StepUpgradeable, AddressResolver {
```

- *SignalService.sol* ( [14-14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L14-L14) ):

```solidity
/// @audit EssentialContract
/// @audit ISignalService
14: contract SignalService is EssentialContract, ISignalService {
```

- *TimelockTokenPool.sol* ( [25-25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L25-L25) ):

```solidity
/// @audit EssentialContract
25: contract TimelockTokenPool is EssentialContract {
```

- *ERC20Airdrop.sol* ( [11-11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L11-L11) ):

```solidity
/// @audit MerkleClaimable
11: contract ERC20Airdrop is MerkleClaimable {
```

- *ERC20Airdrop2.sol* ( [12-12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L12-L12) ):

```solidity
/// @audit MerkleClaimable
12: contract ERC20Airdrop2 is MerkleClaimable {
```

- *ERC721Airdrop.sol* ( [9-9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L9-L9) ):

```solidity
/// @audit MerkleClaimable
9: contract ERC721Airdrop is MerkleClaimable {
```

- *MerkleClaimable.sol* ( [10-10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L10-L10) ):

```solidity
/// @audit EssentialContract
10: abstract contract MerkleClaimable is EssentialContract {
```

- *BaseNFTVault.sol* ( [9-9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L9-L9) ):

```solidity
/// @audit BaseVault
9: abstract contract BaseNFTVault is BaseVault {
```

- *BaseVault.sol* ( [12-16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L12-L16) ):

```solidity
/// @audit EssentialContract
/// @audit IRecallableSender
/// @audit IMessageInvocable
/// @audit IERC165Upgradeable
12: abstract contract BaseVault is
13:     EssentialContract,
14:     IRecallableSender,
15:     IMessageInvocable,
16:     IERC165Upgradeable
```

- *BridgedERC1155.sol* ( [14-14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L14-L14) ):

```solidity
/// @audit EssentialContract
/// @audit IERC1155MetadataURIUpgradeable
/// @audit ERC1155Upgradeable
14: contract BridgedERC1155 is EssentialContract, IERC1155MetadataURIUpgradeable, ERC1155Upgradeable {
```

- *BridgedERC20.sol* ( [15-19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L15-L19) ):

```solidity
/// @audit BridgedERC20Base
/// @audit IERC20MetadataUpgradeable
/// @audit ERC20SnapshotUpgradeable
/// @audit ERC20VotesUpgradeable
15: contract BridgedERC20 is
16:     BridgedERC20Base,
17:     IERC20MetadataUpgradeable,
18:     ERC20SnapshotUpgradeable,
19:     ERC20VotesUpgradeable
```

- *BridgedERC20Base.sol* ( [9-9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L9-L9) ):

```solidity
/// @audit EssentialContract
/// @audit IBridgedERC20
9: abstract contract BridgedERC20Base is EssentialContract, IBridgedERC20 {
```

- *BridgedERC721.sol* ( [12-12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L12-L12) ):

```solidity
/// @audit EssentialContract
/// @audit ERC721Upgradeable
12: contract BridgedERC721 is EssentialContract, ERC721Upgradeable {
```

- *ERC1155Vault.sol* ( [29-29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L29-L29) ):

```solidity
/// @audit BaseNFTVault
/// @audit ERC1155ReceiverUpgradeable
29: contract ERC1155Vault is BaseNFTVault, ERC1155ReceiverUpgradeable {
```

- *ERC20Vault.sol* ( [18-18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L18-L18) ):

```solidity
/// @audit BaseVault
18: contract ERC20Vault is BaseVault {
```

- *ERC721Vault.sol* ( [16-16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L16-L16) ):

```solidity
/// @audit BaseNFTVault
/// @audit IERC721Receiver
16: contract ERC721Vault is BaseNFTVault, IERC721Receiver {
```

- *USDCAdapter.sol* ( [28-28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L28-L28) ):

```solidity
/// @audit BridgedERC20Base
28: contract USDCAdapter is BridgedERC20Base {
```

- *GuardianVerifier.sol* ( [10-10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L10-L10) ):

```solidity
/// @audit EssentialContract
/// @audit IVerifier
10: contract GuardianVerifier is EssentialContract, IVerifier {
```

- *SgxVerifier.sol* ( [19-19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L19-L19) ):

```solidity
/// @audit EssentialContract
/// @audit IVerifier
19: contract SgxVerifier is EssentialContract, IVerifier {
```

</details>

### [N-51] Each interfaces should be defined in a separate file

Each interface should be defined in a separate file, making it easier to import, and easier to develop and maintain. This is the strategy adopted by most popular libraries.

There are 6 instances:

- *ITierProvider.sol* ( [7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L7) ):

```solidity
7: interface ITierProvider {
```

- *IBridge.sol* ( [8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/IBridge.sol#L8), [160](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/IBridge.sol#L160), [174](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/IBridge.sol#L174) ):

```solidity
8: interface IBridge {

160: interface IRecallableSender {

174: interface IMessageInvocable {
```

- *ERC1155Vault.sol* ( [16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L16) ):

```solidity
16: interface IERC1155NameAndSymbol {
```

- *USDCAdapter.sol* ( [8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L8) ):

```solidity
8: interface IUSDC {
```

### [N-52] Libraries should be defined in separate files

The libraries below should be defined in separate files, so that it's easier for future projects to import them, and to avoid duplication later on if they need to be used elsewhere in the project.

There are 3 instances:

- *ITierProvider.sol* ( [37](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L37) ):

```solidity
37: library LibTiers {
```

- *Asn1Decode.sol* ( [12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L12), [38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L38) ):

```solidity
12: library NodePtr {

38: library Asn1Decode {
```

### [N-53] Put all system-wide constants in one file

Putting all the system-wide constants in a single file improves code readability, makes it easier to understand the basic configuration and limitations of the system, and makes maintenance easier.

<details>
<summary>There are 23 instances (click to show):</summary>

- *AssignmentHook.sol* ( [38-38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L38-L38) ):

```solidity
38:     uint256 public constant MAX_GAS_PAYING_PROVER = 50_000;
```

- *LibProposing.sol* ( [21-21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L21-L21) ):

```solidity
21:     uint256 public constant MAX_BYTES_PER_BLOB = 4096 * 32;
```

- *LibProving.sol* ( [20-20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L20-L20), [23-23](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L23-L23) ):

```solidity
20:     bytes32 public constant RETURN_LIVENESS_BOND = keccak256("RETURN_LIVENESS_BOND");

23:     bytes32 public constant TIER_OP = bytes32("tier_optimistic");
```

- *Guardians.sol* ( [11-11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L11-L11) ):

```solidity
11:     uint256 public constant MIN_NUM_GUARDIANS = 5;
```

- *ITierProvider.sol* ( [39-39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L39-L39), [42-42](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L42-L42), [45-45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L45-L45), [48-48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L48-L48) ):

```solidity
39:     uint16 public constant TIER_OPTIMISTIC = 100;

42:     uint16 public constant TIER_SGX = 200;

45:     uint16 public constant TIER_SGX_ZKVM = 300;

48:     uint16 public constant TIER_GUARDIAN = 1000;
```

- *TaikoL2.sol* ( [32-32](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L32-L32), [35-35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L35-L35) ):

```solidity
32:     address public constant GOLDEN_TOUCH_ADDRESS = 0x0000777735367b36bC9B61C50022d9D0700dB4Ec;

35:     uint8 public constant BLOCK_SYNC_THRESHOLD = 5;
```

- *Lib4844.sol* ( [10-10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/Lib4844.sol#L10-L10), [13-13](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/Lib4844.sol#L13-L13), [16-17](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/Lib4844.sol#L16-L17) ):

```solidity
10:     address public constant POINT_EVALUATION_PRECOMPILE_ADDRESS = address(0x0A);

13:     uint32 public constant FIELD_ELEMENTS_PER_BLOB = 4096;

16:     uint256 public constant BLS_MODULUS =
17:         52_435_875_175_126_190_479_447_740_508_185_965_837_690_552_500_527_637_822_603_658_699_938_581_184_513;
```

- *LibSignals.sol* ( [8-8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/LibSignals.sol#L8-L8), [11-11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/LibSignals.sol#L11-L11) ):

```solidity
8:     bytes32 public constant STATE_ROOT = keccak256("STATE_ROOT");

11:     bytes32 public constant SIGNAL_ROOT = keccak256("SIGNAL_ROOT");
```

- *LibFixedPointMath.sol* ( [7-7](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L7-L7), [8-8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L8-L8) ):

```solidity
7:     uint128 public constant MAX_EXP_INPUT = 135_305_999_368_893_231_588;

8:     uint256 public constant SCALING_FACTOR = 1e18; // For fixed point representation factor
```

- *BaseNFTVault.sol* ( [47-47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L47-L47), [50-50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L50-L50), [53-53](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L53-L53) ):

```solidity
47:     bytes4 public constant ERC1155_INTERFACE_ID = 0xd9b67a26;

50:     bytes4 public constant ERC721_INTERFACE_ID = 0x80ac58cd;

53:     uint256 public constant MAX_TOKEN_PER_TXN = 10;
```

- *SgxVerifier.sol* ( [30-30](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L30-L30), [34-34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L34-L34) ):

```solidity
30:     uint64 public constant INSTANCE_EXPIRY = 180 days;

34:     uint64 public constant INSTANCE_VALIDITY_DELAY = 1 days;
```

</details>

### [N-54] `else`-block not required

One level of nesting can be removed by not having an `else` block when the `if`-block always jumps at the end. For example:
```solidity
if (condition) {
    body1...
    return x;
} else {
    body2...
}
```
can be changed to:
```solidity
if (condition) {
    body1...
    return x;
}
body2...
```

<details>
<summary>There are 20 instances (click to show):</summary>

- *LibVerifying.sol* ( [145-147](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L145-L147) ):

```solidity
145:                 if (ts.contester != address(0)) {
146:                     break;
147:                 } else {
```

- *MainnetTierProvider.sol* ( [68-69](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L68-L69) ):

```solidity
68:         if (_rand % 1000 == 0) return LibTiers.TIER_SGX_ZKVM;
69:         else return LibTiers.TIER_SGX;
```

- *AutomataDcapV3Attestation.sol* ( [319-329](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L319-L329) ):

```solidity
319:         if (qeReportDataIsValid) {
320:             bytes memory pckSignedQeReportBytes =
321:                 V3Parser.packQEReport(authDataV3.pckSignedQeReport);
322:             bool qeSigVerified = sigVerifyLib.verifyES256Signature(
323:                 pckSignedQeReportBytes, authDataV3.qeReportSignature, pckCertPubKey
324:             );
325:             bool quoteSigVerified = sigVerifyLib.verifyES256Signature(
326:                 signedQuoteData, authDataV3.ecdsa256BitSignature, authDataV3.ecdsaAttestationKey
327:             );
328:             return qeSigVerified && quoteSigVerified;
329:         } else {
```

- *Asn1Decode.sol* ( [158-160](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L158-L160) ):

```solidity
158:         if (der[ptr.ixf()] == 0) {
159:             return der.substring(ptr.ixf() + 1, valueLength - 1);
160:         } else {
```

- *SigVerifyLib.sol* ( [34-39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L34-L39), [39-44](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L39-L44), [44-49](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L44-L49), [64-69](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L64-L69), [69-74](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L69-L74) ):

```solidity
34:         if (alg == Algorithm.RS256) {
35:             if (publicKey.keyType != KeyType.RSA) {
36:                 return false;
37:             }
38:             return verifyRS256Signature(tbs, signature, publicKey.pubKey);
39:         } else if (alg == Algorithm.ES256) {

39:         } else if (alg == Algorithm.ES256) {
40:             if (publicKey.keyType != KeyType.ECDSA) {
41:                 return false;
42:             }
43:             return verifyES256Signature(tbs, signature, publicKey.pubKey);
44:         } else if (alg == Algorithm.RS1) {

44:         } else if (alg == Algorithm.RS1) {
45:             if (publicKey.keyType != KeyType.RSA) {
46:                 return false;
47:             }
48:             return verifyRS1Signature(tbs, signature, publicKey.pubKey);
49:         } else {

64:         if (alg == CertSigAlgorithm.Sha256WithRSAEncryption) {
65:             if (publicKey.keyType != KeyType.RSA) {
66:                 return false;
67:             }
68:             return verifyRS256Signature(tbs, signature, publicKey.pubKey);
69:         } else if (alg == CertSigAlgorithm.Sha1WithRSAEncryption) {

69:         } else if (alg == CertSigAlgorithm.Sha1WithRSAEncryption) {
70:             if (publicKey.keyType != KeyType.RSA) {
71:                 return false;
72:             }
73:             return verifyRS1Signature(tbs, signature, publicKey.pubKey);
74:         } else {
```

- *Bridge.sol* ( [423-429](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L423-L429), [429-439](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L429-L439), [439-442](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L439-L442), [556-566](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L556-L566) ):

```solidity
423:         if (
424:             block.chainid == 1 // Ethereum mainnet
425:         ) {
426:             // For Taiko mainnet
427:             // 384 seconds = 6.4 minutes = one ethereum epoch
428:             return (1 hours, 384 seconds);
429:         } else if (

429:         } else if (
430:             block.chainid == 2 // Ropsten
431:                 || block.chainid == 4 // Rinkeby
432:                 || block.chainid == 5 // Goerli
433:                 || block.chainid == 42 // Kovan
434:                 || block.chainid == 17_000 // Holesky
435:                 || block.chainid == 11_155_111 // Sepolia
436:         ) {
437:             // For all Taiko public testnets
438:             return (30 minutes, 384 seconds);
439:         } else if (block.chainid >= 32_300 && block.chainid <= 32_400) {

439:         } else if (block.chainid >= 32_300 && block.chainid <= 32_400) {
440:             // For all Taiko internal devnets
441:             return (5 minutes, 384 seconds);
442:         } else {

556:         if (block.chainid == 1) {
557:             bytes32 msgHash;
558:             address from;
559:             uint64 srcChainId;
560:             assembly {
561:                 msgHash := tload(_CTX_SLOT)
562:                 from := tload(add(_CTX_SLOT, 1))
563:                 srcChainId := tload(add(_CTX_SLOT, 2))
564:             }
565:             return Context(msgHash, from, srcChainId);
566:         } else {
```

- *LibAddress.sol* ( [70-72](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L70-L72) ):

```solidity
70:         if (Address.isContract(_addr)) {
71:             return IERC1271(_addr).isValidSignature(_hash, _sig) == _EIP1271_MAGICVALUE;
72:         } else {
```

- *RLPReader.sol* ( [163-166](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L163-L166), [166-188](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L166-L188), [188-223](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L188-L223), [223-234](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L223-L234) ):

```solidity
163:         if (prefix <= 0x7f) {
164:             // Single byte.
165:             return (0, 1, RLPItemType.DATA_ITEM);
166:         } else if (prefix <= 0xb7) {

166:         } else if (prefix <= 0xb7) {
167:             // Short string.
168: 
169:             // slither-disable-next-line variable-scope
170:             uint256 strLen = prefix - 0x80;
171: 
172:             require(
173:                 _in.length > strLen,
174:                 "RLPReader: length of content must be greater than string length (short string)"
175:             );
176: 
177:             bytes1 firstByteOfContent;
178:             assembly {
179:                 firstByteOfContent := and(mload(add(ptr, 1)), shl(248, 0xff))
180:             }
181: 
182:             require(
183:                 strLen != 1 || firstByteOfContent >= 0x80,
184:                 "RLPReader: invalid prefix, single byte < 0x80 are not prefixed (short string)"
185:             );
186: 
187:             return (1, strLen, RLPItemType.DATA_ITEM);
188:         } else if (prefix <= 0xbf) {

188:         } else if (prefix <= 0xbf) {
189:             // Long string.
190:             uint256 lenOfStrLen = prefix - 0xb7;
191: 
192:             require(
193:                 _in.length > lenOfStrLen,
194:                 "RLPReader: length of content must be > than length of string length (long string)"
195:             );
196: 
197:             bytes1 firstByteOfContent;
198:             assembly {
199:                 firstByteOfContent := and(mload(add(ptr, 1)), shl(248, 0xff))
200:             }
201: 
202:             require(
203:                 firstByteOfContent != 0x00,
204:                 "RLPReader: length of content must not have any leading zeros (long string)"
205:             );
206: 
207:             uint256 strLen;
208:             assembly {
209:                 strLen := shr(sub(256, mul(8, lenOfStrLen)), mload(add(ptr, 1)))
210:             }
211: 
212:             require(
213:                 strLen > 55,
214:                 "RLPReader: length of content must be greater than 55 bytes (long string)"
215:             );
216: 
217:             require(
218:                 _in.length > lenOfStrLen + strLen,
219:                 "RLPReader: length of content must be greater than total length (long string)"
220:             );
221: 
222:             return (1 + lenOfStrLen, strLen, RLPItemType.DATA_ITEM);
223:         } else if (prefix <= 0xf7) {

223:         } else if (prefix <= 0xf7) {
224:             // Short list.
225:             // slither-disable-next-line variable-scope
226:             uint256 listLen = prefix - 0xc0;
227: 
228:             require(
229:                 _in.length > listLen,
230:                 "RLPReader: length of content must be greater than list length (short list)"
231:             );
232: 
233:             return (1, listLen, RLPItemType.LIST_ITEM);
234:         } else {
```

- *MerkleTrie.sol* ( [112-131](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L112-L131), [155-184](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L155-L184) ):

```solidity
112:                 if (currentKeyIndex == key.length) {
113:                     // Value is the last element of the decoded list (for branch nodes). There's
114:                     // some ambiguity in the Merkle trie specification because bytes(0) is a
115:                     // valid value to place into the trie, but for branch nodes bytes(0) can exist
116:                     // even when the value wasn't explicitly placed there. Geth treats a value of
117:                     // bytes(0) as "key does not exist" and so we do the same.
118:                     value_ = RLPReader.readBytes(currentNode.decoded[TREE_RADIX]);
119:                     require(
120:                         value_.length > 0,
121:                         "MerkleTrie: value length must be greater than zero (branch)"
122:                     );
123: 
124:                     // Extra proof elements are not allowed.
125:                     require(
126:                         i == proof.length - 1,
127:                         "MerkleTrie: value node must be last node in proof (branch)"
128:                     );
129: 
130:                     return value_;
131:                 } else {

155:                 if (prefix == PREFIX_LEAF_EVEN || prefix == PREFIX_LEAF_ODD) {
156:                     // Prefix of 2 or 3 means this is a leaf node. For the leaf node to be valid,
157:                     // the key remainder must be exactly equal to the path remainder. We already
158:                     // did the necessary byte comparison, so it's more efficient here to check that
159:                     // the key remainder length equals the shared nibble length, which implies
160:                     // equality with the path remainder (since we already did the same check with
161:                     // the path remainder and the shared nibble length).
162:                     require(
163:                         keyRemainder.length == sharedNibbleLength,
164:                         "MerkleTrie: key remainder must be identical to path remainder"
165:                     );
166: 
167:                     // Our Merkle Trie is designed specifically for the purposes of the Ethereum
168:                     // state trie. Empty values are not allowed in the state trie, so we can safely
169:                     // say that if the value is empty, the key should not exist and the proof is
170:                     // invalid.
171:                     value_ = RLPReader.readBytes(currentNode.decoded[1]);
172:                     require(
173:                         value_.length > 0,
174:                         "MerkleTrie: value length must be greater than zero (leaf)"
175:                     );
176: 
177:                     // Extra proof elements are not allowed.
178:                     require(
179:                         i == proof.length - 1,
180:                         "MerkleTrie: value node must be last node in proof (leaf)"
181:                     );
182: 
183:                     return value_;
184:                 } else if (prefix == PREFIX_EXTENSION_EVEN || prefix == PREFIX_EXTENSION_ODD) {
```

</details>

### [N-55] `assert()` should be replaced with `require()` or `revert()`

In versions of Solidity prior to 0.8.0, when encountering an assert all the remaining gas will be consumed.
Even after solidity 0.8.0, the assert function is still not recommended, as described in the [documentation](https://docs.soliditylang.org/en/v0.8.20/control-structures.html#panic-via-assert-and-error-via-require):
> Assert should only be used to test for internal errors, and to check invariants. Properly functioning code should never create a Panic, not even on invalid external input. If this happens, then there is a bug in your contract which you should fix.

There are 4 instances:

- *LibProving.sol* ( [223](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L223), [224](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L224) ):

```solidity
223:                 assert(tier.validityBond == 0);

224:                 assert(ts.validityBond == 0 && ts.contestBond == 0 && ts.contester == address(0));
```

- *SigVerifyLib.sol* ( [138](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L138) ):

```solidity
138:         assert(success); // never reverts, always returns 0 or 1
```

- *Bridge.sol* ( [486](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L486) ):

```solidity
486:         assert(_message.from != address(this));
```

### [N-56] Large multiples of ten should use scientific notation

Use a scientific notation rather than decimal literals (e.g. `1e6` instead of `1000000`), for better code readability.

<details>
<summary>There are 19 instances (click to show):</summary>

- *TaikoL1.sol* ( [195-195](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L195-L195), [199-199](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L199-L199), [203-203](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L203-L203), [213-213](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L213-L213), [214-214](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L214-L214) ):

```solidity
/// @audit 864_000 -> 864e3
195:             blockMaxProposals: 864_000,

/// @audit 15_000_000 -> 15e6
199:             blockMaxGasLimit: 15_000_000,

/// @audit 120_000 -> 12e4
203:             blockMaxTxListBytes: 120_000,

/// @audit 10_000 -> 1e4
213:             ethDepositMaxAmount: 10_000 ether,

/// @audit 21_000 -> 21e3
214:             ethDepositGas: 21_000,
```

- *TaikoToken.sol* ( [41-41](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L41-L41) ):

```solidity
/// @audit 1_000_000_000 -> 1e9
41:         _mint(_recipient, 1_000_000_000 ether);
```

- *TaikoGovernor.sol* ( [124-124](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L124-L124) ):

```solidity
/// @audit 1_000_000_000 -> 1e9
/// @audit 10_000 -> 1e4
124:         return 1_000_000_000 ether / 10_000; // 0.01% of Taiko Token
```

- *AssignmentHook.sol* ( [38-38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L38-L38) ):

```solidity
/// @audit 50_000 -> 5e4
38:     uint256 public constant MAX_GAS_PAYING_PROVER = 50_000;
```

- *ITierProvider.sol* ( [48-48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L48-L48) ):

```solidity
/// @audit 1000 -> 1e3
48:     uint16 public constant TIER_GUARDIAN = 1000;
```

- *MainnetTierProvider.sol* ( [36-36](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L36-L36), [68-68](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L68-L68) ):

```solidity
/// @audit 1000 -> 1e3
36:                 contestBond: 1000 ether, // TKO

/// @audit 1000 -> 1e3
68:         if (_rand % 1000 == 0) return LibTiers.TIER_SGX_ZKVM;
```

- *TestnetTierProvider.sol* ( [36-36](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L36-L36) ):

```solidity
/// @audit 1000 -> 1e3
36:                 contestBond: 1000 ether, // TKO
```

- *RsaVerify.sol* ( [102-102](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L102-L102), [250-250](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L250-L250) ):

```solidity
/// @audit 2000 -> 2e3
102:                     sub(gas(), 2000),

/// @audit 2000 -> 2e3
250:                     sub(gas(), 2000),
```

- *X509DateUtils.sol* ( [18-18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L18-L18), [21-21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L21-L21), [52-52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L52-L52) ):

```solidity
/// @audit 2000 -> 2e3
18:             if (uint8(x509Time[0]) - 48 < 5) yrs += 2000;

/// @audit 1000 -> 1e3
21:             yrs += (uint8(x509Time[0]) - 48) * 1000 + (uint8(x509Time[1]) - 48) * 100;

/// @audit 31_536_000 -> 31_536e3
52:                 timestamp += 31_536_000; // Normal year in seconds
```

- *Bridge.sol* ( [434-434](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L434-L434) ):

```solidity
/// @audit 17_000 -> 17e3
434:                 || block.chainid == 17_000 // Holesky
```

</details>

### [N-57] High cyclomatic complexity

Consider breaking down these blocks into more manageable units, by splitting things into utility functions, by reducing nesting, and by using early returns.

<details>
<summary>There are 2 instances (click to show):</summary>

- *SigVerifyLib.sol* ( [24-52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L24-L52) ):

```solidity
24:     function verifyAttStmtSignature(
25:         bytes memory tbs,
26:         bytes memory signature,
27:         PublicKey memory publicKey,
28:         Algorithm alg
29:     )
30:         public
31:         view
32:         returns (bool)
33:     {
34:         if (alg == Algorithm.RS256) {
35:             if (publicKey.keyType != KeyType.RSA) {
36:                 return false;
37:             }
38:             return verifyRS256Signature(tbs, signature, publicKey.pubKey);
39:         } else if (alg == Algorithm.ES256) {
40:             if (publicKey.keyType != KeyType.ECDSA) {
41:                 return false;
42:             }
43:             return verifyES256Signature(tbs, signature, publicKey.pubKey);
44:         } else if (alg == Algorithm.RS1) {
45:             if (publicKey.keyType != KeyType.RSA) {
46:                 return false;
47:             }
48:             return verifyRS1Signature(tbs, signature, publicKey.pubKey);
49:         } else {
50:             revert("Unsupported algorithm");
51:         }
52:     }
```

- *SignalService.sol* ( [83-134](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L83-L134) ):

```solidity
83:     function proveSignalReceived(
84:         uint64 _chainId,
85:         address _app,
86:         bytes32 _signal,
87:         bytes calldata _proof
88:     )
89:         public
90:         virtual
91:         validSender(_app)
92:         nonZeroValue(_signal)
93:     {
94:         HopProof[] memory hopProofs = abi.decode(_proof, (HopProof[]));
95:         if (hopProofs.length == 0) revert SS_EMPTY_PROOF();
96: 
97:         uint64 chainId = _chainId;
98:         address app = _app;
99:         bytes32 signal = _signal;
100:         bytes32 value = _signal;
101:         address signalService = resolve(chainId, "signal_service", false);
102: 
103:         HopProof memory hop;
104:         for (uint256 i; i < hopProofs.length; ++i) {
105:             hop = hopProofs[i];
106: 
107:             bytes32 signalRoot = _verifyHopProof(chainId, app, signal, value, hop, signalService);
...... OMITTED ......
110:             if (isLastHop) {
111:                 if (hop.chainId != block.chainid) revert SS_INVALID_LAST_HOP_CHAINID();
112:                 signalService = address(this);
113:             } else {
114:                 if (hop.chainId == 0 || hop.chainId == block.chainid) {
115:                     revert SS_INVALID_MID_HOP_CHAINID();
116:                 }
117:                 signalService = resolve(hop.chainId, "signal_service", false);
118:             }
119: 
120:             bool isFullProof = hop.accountProof.length > 0;
121: 
122:             _cacheChainData(hop, chainId, hop.blockId, signalRoot, isFullProof, isLastHop);
123: 
124:             bytes32 kind = isFullProof ? LibSignals.STATE_ROOT : LibSignals.SIGNAL_ROOT;
125:             signal = signalForChainData(chainId, kind, hop.blockId);
126:             value = hop.rootHash;
127:             chainId = hop.chainId;
128:             app = signalService;
129:         }
130: 
131:         if (value == 0 || value != _loadSignalValue(address(this), signal)) {
132:             revert SS_SIGNAL_NOT_FOUND();
133:         }
134:     }
```

</details>

### [N-58] Typos

All typos should be corrected.

<details>
<summary>There are 7 instances (click to show):</summary>

- *PEMCertChainLib.sol* ( [98](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L98), [349](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L349) ):

```solidity
/// @audit comman
98:         // The subject commanName value is contained in the Subject sequence

/// @audit sibiling
349:         // sibiling of tcbOid
```

- *V3Parser.sol* ( [225](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L225), [267](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L267) ):

```solidity
/// @audit Cerification
225:         cert.decodedCertDataArray = parseCerificationChainBytes(certData, pemCertLibAddr);

/// @audit Cerification
267:     function parseCerificationChainBytes(
```

- *Bytes.sol* ( [87](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L87) ):

```solidity
/// @audit rathern
87:     ///         array. Returns a new array rathern than a pointer to the original.
```

- *MerkleTrie.sol* ( [194](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L194) ):

```solidity
/// @audit unparseable
194:                 revert("MerkleTrie: received an unparseable node");
```

- *LibFixedPointMath.sol* ( [72](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L72) ):

```solidity
/// @audit converison
72:             //  * the 1e18 / 2**96 factor for base converison.
```

</details>

### [N-59] Consider bounding input array length

The functions below take in an unbounded array, and make function calls for entries in the array. While the function will revert if it eventually runs out of gas, it may be a nicer user experience to require() that the length of the array is below some reasonable maximum, so that the user doesn't have to use up a full transaction's gas only to see that the transaction reverts.

<details>
<summary>There are 13 instances (click to show):</summary>

- *AssignmentHook.sol* ( [172](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L172) ):

```solidity
172:         for (uint256 i; i < _tierFees.length; ++i) {
```

- *Guardians.sol* ( [74](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L74), [80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L80) ):

```solidity
74:         for (uint256 i; i < guardians.length; ++i) {

80:         for (uint256 i = 0; i < _newGuardians.length; ++i) {
```

- *AutomataDcapV3Attestation.sol* ( [80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L80), [95](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L95), [240](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L240), [259](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L259) ):

```solidity
80:         for (uint256 i; i < serialNumBatch.length; ++i) {

95:         for (uint256 i; i < serialNumBatch.length; ++i) {

240:         for (uint256 i; i < CPUSVN_LENGTH; ++i) {

259:         for (uint256 i; i < n; ++i) {
```

- *Bridge.sol* ( [90](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L90) ):

```solidity
90:         for (uint256 i; i < _msgHashes.length; ++i) {
```

- *ERC721Airdrop.sol* ( [59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59) ):

```solidity
59:         for (uint256 i; i < tokenIds.length; ++i) {
```

- *ERC721Vault.sol* ( [170](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L170), [175](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L175) ):

```solidity
170:             for (uint256 i; i < _tokenIds.length; ++i) {

175:             for (uint256 i; i < _tokenIds.length; ++i) {
```

- *SgxVerifier.sol* ( [104](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L104), [210](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210) ):

```solidity
104:         for (uint256 i; i < _ids.length; ++i) {

210:         for (uint256 i; i < _instances.length; ++i) {
```

</details>

### [N-60] Unnecessary casting

Unnecessary castings can be removed.

There is 1 instance:

- *V3Parser.sol* ( [154-154](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L154-L154) ):

```solidity
/// @audit bytes1(encoded[i])
154:             uint256 digits = uint256(uint8(bytes1(encoded[i])));
```

### [N-61] Unused import

The identifier is imported but never used within the file.

<details>
<summary>There are 9 instances (click to show):</summary>

- *AutomataDcapV3Attestation.sol* ( [4-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L4-L4), [10-10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L10-L10), [13-13](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L13-L13), [15-15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L15-L15) ):

```solidity
/// @audit V3Struct
4: import { V3Struct } from "./lib/QuoteV3Auth/V3Struct.sol";

/// @audit IAttestation
10: import { IAttestation } from "./interfaces/IAttestation.sol";

/// @audit Base64
13: import { Base64 } from "solady/src/utils/Base64.sol";

/// @audit BytesUtils
15: import { BytesUtils } from "./utils/BytesUtils.sol";
```

- *IAttestation.sol* ( [4-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/interfaces/IAttestation.sol#L4-L4) ):

```solidity
/// @audit V3Struct
4: import { V3Struct } from "../lib/QuoteV3Auth/V3Struct.sol";
```

- *PEMCertChainLib.sol* ( [5-5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L5-L5), [8-8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L8-L8) ):

```solidity
/// @audit Asn1Decode
5: import { Asn1Decode, NodePtr } from "../utils/Asn1Decode.sol";

/// @audit IPEMCertChainLib
8: import { IPEMCertChainLib } from "./interfaces/IPEMCertChainLib.sol";
```

- *V3Parser.sol* ( [5-5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L5-L5), [6-6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L6-L6) ):

```solidity
/// @audit BytesUtils
5: import { BytesUtils } from "../../utils/BytesUtils.sol";

/// @audit IPEMCertChainLib
6: import { IPEMCertChainLib, PEMCertChainLib } from "../../lib/PEMCertChainLib.sol";
```

</details>

### [N-62] Unused named return

Declaring named returns, but not using them, is confusing to the reader. Consider either completely removing them (by declaring just the type without a name), or remove the return statement and do a variable assignment. This would improve the readability of the code, and it may also help reduce regressions during future code refactors.

<details>
<summary>There are 10 instances (click to show):</summary>

- *LibProving.sol* ( [91-100](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L91-L100) ):

```solidity
/// @audit maxBlocksToVerify_
91:     function proveBlock(
92:         TaikoData.State storage _state,
93:         TaikoData.Config memory _config,
94:         IAddressResolver _resolver,
95:         TaikoData.BlockMetadata memory _meta,
96:         TaikoData.Transition memory _tran,
97:         TaikoData.TierProof memory _proof
98:     )
99:         internal
100:         returns (uint8 maxBlocksToVerify_)
```

- *AutomataDcapV3Attestation.sol* ( [126-130](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L126-L130) ):

```solidity
/// @audit valid
126:     function _attestationTcbIsValid(TCBInfoStruct.TCBStatus status)
127:         internal
128:         pure
129:         virtual
130:         returns (bool valid)
```

- *PEMCertChainLib.sol* ( [216-219](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L216-L219) ):

```solidity
/// @audit success
216:     function _removeHeadersAndFooters(string memory pemData)
217:         private
218:         pure
219:         returns (bool success, bytes memory extracted, uint256 endIndex)
```

- *BytesUtils.sol* ( [188-188](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L188-L188) ):

```solidity
/// @audit ret
188:     function readUint8(bytes memory self, uint256 idx) internal pure returns (uint8 ret) {
```

- *SigVerifyLib.sol* ( [113-120](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L113-L120) ):

```solidity
/// @audit sigValid
113:     function verifyES256Signature(
114:         bytes memory tbs,
115:         bytes memory signature,
116:         bytes memory publicKey
117:     )
118:         public
119:         view
120:         returns (bool sigValid)
```

- *Bridge.sol* ( [417-421](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L417-L421) ):

```solidity
/// @audit invocationDelay_
/// @audit invocationExtraDelay_
417:     function getInvocationDelays()
418:         public
419:         view
420:         virtual
421:         returns (uint256 invocationDelay_, uint256 invocationExtraDelay_)
```

- *RLPReader.sol* ( [144-147](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L144-L147) ):

```solidity
/// @audit offset_
/// @audit length_
/// @audit type_
144:     function _decodeLength(RLPItem memory _in)
145:         private
146:         pure
147:         returns (uint256 offset_, uint256 length_, RLPItemType type_)
```

</details>

### [N-63] Use delete instead of assigning values to `false`

The `delete` keyword more closely matches the semantics of what is being done, and draws more attention to the changing of state, which may lead to a more thorough audit of its associated logic.

There are 2 instances:

- *RsaVerify.sol* ( [129-129](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L129-L129) ):

```solidity
129:             hasNullParam = false;
```

- *Bridge.sol* ( [495-495](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L495-L495) ):

```solidity
495:             success_ = false;
```

### [N-64] Consider using `delete` rather than assigning zero to clear values

The `delete` keyword more closely matches the semantics of what is being done, and draws more attention to the changing of state, which may lead to a more thorough audit of its associated logic.

<details>
<summary>There are 14 instances (click to show):</summary>

- *LibProposing.sol* ( [190-190](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L190-L190) ):

```solidity
190:             meta_.txListByteOffset = 0;
```

- *LibProving.sol* ( [197-197](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L197-L197), [300-300](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L300-L300), [301-301](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L301-L301), [302-302](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L302-L302), [303-303](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L303-L303), [306-306](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L306-L306), [307-307](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L307-L307), [332-332](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L332-L332), [390-390](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L390-L390) ):

```solidity
197:                 blk.livenessBond = 0;

300:             ts_.blockHash = 0;

301:             ts_.stateRoot = 0;

302:             ts_.validityBond = 0;

303:             ts_.contester = address(0);

306:             ts_.tier = 0;

307:             ts_.contestations = 0;

332:                 ts_.prover = address(0);

390:         _ts.contester = address(0);
```

- *LibVerifying.sol* ( [70-70](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L70-L70) ):

```solidity
70:         ts.prover = address(0);
```

- *PEMCertChainLib.sol* ( [336-336](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L336-L336) ):

```solidity
336:                 tbsPtr = 0; // exit
```

- *TimelockTokenPool.sol* ( [231-231](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L231-L231), [232-232](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L232-L232) ):

```solidity
231:         _grant.grantStart = 0;

232:         _grant.grantPeriod = 0;
```

</details>

### [N-65] Use the latest Solidity version

Upgrading to the [latest solidity version](https://github.com/ethereum/solc-js/tags) (0.8.19 for L2s) can optimize gas usage, take advantage of new features and improve overall contract efficiency. Where possible, based on compatibility requirements, it is recommended to use newer/latest solidity version to take advantage of the latest optimizations and features.

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

### [N-66] Consider using named function arguments

When calling functions with multiple arguments, consider using [named function parameters](https://docs.soliditylang.org/en/latest/control-structures.html#function-calls-with-named-parameters), rather than positional ones.

<details>
<summary>There are 23 instances (click to show):</summary>

- *AssignmentHook.sol* ( [102-102](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L102-L102) ):

```solidity
102:         tko.transferFrom(_blk.assignedProver, taikoL1Address, _blk.livenessBond);
```

- *LibProposing.sol* ( [253-255](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L253-L255) ):

```solidity
253:                 IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }(
254:                     blk, meta_, params.hookCalls[i].data
255:                 );
```

- *LibProving.sol* ( [177-177](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L177-L177), [242-242](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L242-L242), [384-384](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L384-L384) ):

```solidity
177:                 IVerifier(verifier).verifyProof(ctx, _tran, _proof);

242:                 tko.transferFrom(msg.sender, address(this), tier.contestBond);

384:                 _tko.transferFrom(msg.sender, address(this), _tier.validityBond - reward);
```

- *LibVerifying.sol* ( [234-236](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L234-L236), [239-241](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L239-L241) ):

```solidity
234:         (uint64 lastSyncedBlock,) = signalService.getSyncedChainData(
235:             _config.chainId, LibSignals.STATE_ROOT, 0 /* latest block Id*/
236:         );

239:             signalService.syncChainData(
240:                 _config.chainId, LibSignals.STATE_ROOT, _lastVerifiedBlockId, _stateRoot
241:             );
```

- *TaikoL2.sol* ( [148-150](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L148-L150) ):

```solidity
148:             ISignalService(resolve("signal_service", false)).syncChainData(
149:                 ownerChainId, LibSignals.STATE_ROOT, _l1BlockId, _l1StateRoot
150:             );
```

- *AutomataDcapV3Attestation.sol* ( [285-287](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L285-L287), [322-324](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L322-L324), [325-327](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L325-L327) ):

```solidity
285:             verified = sigVerifyLib.verifyES256Signature(
286:                 certs[i].tbsCertificate, certs[i].signature, issuer.pubKey
287:             );

322:             bool qeSigVerified = sigVerifyLib.verifyES256Signature(
323:                 pckSignedQeReportBytes, authDataV3.qeReportSignature, pckCertPubKey
324:             );

325:             bool quoteSigVerified = sigVerifyLib.verifyES256Signature(
326:                 signedQuoteData, authDataV3.ecdsa256BitSignature, authDataV3.ecdsaAttestationKey
327:             );
```

- *TimelockTokenPool.sol* ( [219-219](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L219-L219) ):

```solidity
219:         IERC20(taikoToken).transferFrom(sharedVault, _to, amountToWithdraw);
```

- *ERC20Airdrop.sol* ( [63-63](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L63-L63), [71-71](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L71-L71) ):

```solidity
63:         IERC20(token).transferFrom(vault, user, amount);

71:         IVotes(token).delegateBySig(delegatee, nonce, expiry, v, r, s);
```

- *ERC20Airdrop2.sol* ( [91-91](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L91-L91) ):

```solidity
91:         IERC20(token).transferFrom(vault, user, amount);
```

- *ERC721Airdrop.sol* ( [60-60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L60-L60) ):

```solidity
60:             IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);
```

- *ERC1155Vault.sol* ( [226-226](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L226-L226), [230-230](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L230-L230), [252-252](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L252-L252), [270-276](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L270-L276) ):

```solidity
226:             IERC1155(token).safeBatchTransferFrom(address(this), to, tokenIds, amounts, "");

230:             BridgedERC1155(token).mintBatch(to, tokenIds, amounts);

252:                     BridgedERC1155(_op.token).burn(_user, _op.tokenIds[i], _op.amounts[i]);

270:                     IERC1155(_op.token).safeTransferFrom({
271:                         from: msg.sender,
272:                         to: address(this),
273:                         id: _op.tokenIds[i],
274:                         amount: _op.amounts[i],
275:                         data: ""
276:                     });
```

- *ERC721Vault.sol* ( [171-171](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L171-L171), [211-211](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L211-L211) ):

```solidity
171:                 IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);

211:                     t.safeTransferFrom(_user, address(this), _op.tokenIds[i]);
```

- *USDCAdapter.sol* ( [48-48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L48-L48) ):

```solidity
48:         usdc.transferFrom(_from, address(this), _amount);
```

</details>

### [N-67] Named mappings are recommended

[Named mappings](https://docs.soliditylang.org/en/v0.8.18/types.html#mapping-types) (with syntax `mapping(KeyType KeyName? => ValueType ValueName?)`) are recommended.It can make the mapping variables clearer, more readable and easier to maintain.

<details>
<summary>There are 8 instances (click to show):</summary>

- *TaikoData.sol* ( [183-183](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L183-L183), [185-188](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L185-L188) ):

```solidity
183:         mapping(uint64 blockId => mapping(bytes32 parentHash => uint32 transitionId)) transitionIds;

185:         mapping(
186:             uint64 blockId_mod_blockRingBufferSize
187:                 => mapping(uint32 transitionId => TransitionState ts)
188:             ) transitions;
```

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

### [N-68] Named returns are recommended

Using named returns makes the code more self-documenting, makes it easier to fill out NatSpec, and in some cases can save gas. The cases below are where there currently is at most one return statement, which is ideal for named returns.

<details>
<summary>There are 143 instances (click to show):</summary>

- *TaikoL1.sol* ( [132-132](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L132-L132), [137-137](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L137-L137), [162-168](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L162-L168), [186-186](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L186-L186) ):

```solidity
132:     function canDepositEthToL2(uint256 _amount) public view returns (bool) {

137:     function isBlobReusable(bytes32 _blobHash) public view returns (bool) {

162:     function getTransition(
163:         uint64 _blockId,
164:         bytes32 _parentHash
165:     )
166:         public
167:         view
168:         returns (TaikoData.TransitionState memory)

186:     function getConfig() public view virtual override returns (TaikoData.Config memory) {
```

- *TaikoToken.sol* ( [60-60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L60-L60), [70-77](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L70-L77) ):

```solidity
60:     function transfer(address _to, uint256 _amount) public override returns (bool) {

70:     function transferFrom(
71:         address _from,
72:         address _to,
73:         uint256 _amount
74:     )
75:         public
76:         override
77:         returns (bool)
```

- *TaikoGovernor.sol* ( [48-56](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L48-L56), [69-79](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L69-L79), [89-93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L89-L93), [99-103](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L99-L103), [111-111](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L111-L111), [117-117](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L117-L117), [123-123](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L123-L123), [140-148](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L140-L148), [153-157](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L153-L157) ):

```solidity
48:     function propose(
49:         address[] memory _targets,
50:         uint256[] memory _values,
51:         bytes[] memory _calldatas,
52:         string memory _description
53:     )
54:         public
55:         override(IGovernorUpgradeable, GovernorUpgradeable, GovernorCompatibilityBravoUpgradeable)
56:         returns (uint256)

69:     function propose(
70:         address[] memory _targets,
71:         uint256[] memory _values,
72:         string[] memory _signatures,
73:         bytes[] memory _calldatas,
74:         string memory _description
75:     )
76:         public
77:         virtual
78:         override(GovernorCompatibilityBravoUpgradeable)
79:         returns (uint256)

89:     function supportsInterface(bytes4 _interfaceId)
90:         public
91:         view
92:         override(GovernorUpgradeable, GovernorTimelockControlUpgradeable, IERC165Upgradeable)
93:         returns (bool)

99:     function state(uint256 _proposalId)
100:         public
101:         view
102:         override(IGovernorUpgradeable, GovernorUpgradeable, GovernorTimelockControlUpgradeable)
103:         returns (ProposalState)

111:     function votingDelay() public pure override returns (uint256) {

117:     function votingPeriod() public pure override returns (uint256) {

123:     function proposalThreshold() public pure override returns (uint256) {

140:     function _cancel(
141:         address[] memory _targets,
142:         uint256[] memory _values,
143:         bytes[] memory _calldatas,
144:         bytes32 _descriptionHash
145:     )
146:         internal
147:         override(GovernorUpgradeable, GovernorTimelockControlUpgradeable)
148:         returns (uint256)

153:     function _executor()
154:         internal
155:         view
156:         override(GovernorUpgradeable, GovernorTimelockControlUpgradeable)
157:         returns (address)
```

- *TaikoTimelockController.sol* ( [24-24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L24-L24) ):

```solidity
24:     function getMinDelay() public view override returns (uint256) {
```

- *AssignmentHook.sol* ( [137-144](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L137-L144), [164-170](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L164-L170) ):

```solidity
137:     function hashAssignment(
138:         ProverAssignment memory _assignment,
139:         address _taikoL1Address,
140:         bytes32 _blobHash
141:     )
142:         public
143:         view
144:         returns (bytes32)

164:     function _getProverFee(
165:         TaikoData.TierFee[] memory _tierFees,
166:         uint16 _tierId
167:     )
168:         private
169:         pure
170:         returns (uint256)
```

- *LibDepositing.sol* ( [122-129](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L122-L129), [149-149](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L149-L149) ):

```solidity
122:     function canDepositEthToL2(
123:         TaikoData.State storage _state,
124:         TaikoData.Config memory _config,
125:         uint256 _amount
126:     )
127:         internal
128:         view
129:         returns (bool)

149:     function _encodeEthDeposit(address _addr, uint256 _amount) private pure returns (uint256) {
```

- *LibProposing.sol* ( [287-294](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L287-L294), [299-305](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L299-L305) ):

```solidity
287:     function isBlobReusable(
288:         TaikoData.State storage _state,
289:         TaikoData.Config memory _config,
290:         bytes32 _blobHash
291:     )
292:         internal
293:         view
294:         returns (bool)

299:     function _isProposerPermitted(
300:         TaikoData.SlotB memory _slotB,
301:         IAddressResolver _resolver
302:     )
303:         private
304:         view
305:         returns (bool)
```

- *LibUtils.sol* ( [23-31](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L23-L31) ):

```solidity
23:     function getTransition(
24:         TaikoData.State storage _state,
25:         TaikoData.Config memory _config,
26:         uint64 _blockId,
27:         bytes32 _parentHash
28:     )
29:         external
30:         view
31:         returns (TaikoData.TransitionState storage)
```

- *LibVerifying.sol* ( [245-245](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L245-L245) ):

```solidity
245:     function _isConfigValid(TaikoData.Config memory _config) private view returns (bool) {
```

- *Guardians.sol* ( [101-101](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L101-L101), [107-107](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L107-L107), [128-128](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L128-L128) ):

```solidity
101:     function isApproved(bytes32 _hash) public view returns (bool) {

107:     function numGuardians() public view returns (uint256) {

128:     function isApproved(uint256 _approvalBits) internal view returns (bool) {
```

- *DevnetTierProvider.sol* ( [20-20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L20-L20), [54-54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L54-L54) ):

```solidity
20:     function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {

54:     function getMinTier(uint256) public pure override returns (uint16) {
```

- *MainnetTierProvider.sol* ( [20-20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L20-L20), [66-66](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L66-L66) ):

```solidity
20:     function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {

66:     function getMinTier(uint256 _rand) public pure override returns (uint16) {
```

- *TestnetTierProvider.sol* ( [20-20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L20-L20), [66-66](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L66-L66) ):

```solidity
20:     function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {

66:     function getMinTier(uint256 _rand) public pure override returns (uint16) {
```

- *Lib1559Math.sol* ( [16-22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/Lib1559Math.sol#L16-L22), [33-39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/Lib1559Math.sol#L33-L39) ):

```solidity
16:     function basefee(
17:         uint256 _gasExcess,
18:         uint256 _adjustmentFactor
19:     )
20:         internal
21:         pure
22:         returns (uint256)

33:     function _ethQty(
34:         uint256 _gasExcess,
35:         uint256 _adjustmentFactor
36:     )
37:         private
38:         pure
39:         returns (uint256)
```

- *TaikoL2.sol* ( [200-200](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L200-L200), [219-219](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L219-L219) ):

```solidity
200:     function getBlockHash(uint64 _blockId) public view returns (bytes32) {

219:     function skipFeeCheck() public pure virtual returns (bool) {
```

- *TaikoL2EIP1559Configurable.sol* ( [43-43](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L43-L43) ):

```solidity
43:     function getConfig() public view override returns (Config memory) {
```

- *AutomataDcapV3Attestation.sol* ( [138-138](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L138-L138), [162-162](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L162-L162), [175-178](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L175-L178), [206-212](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L206-L212), [229-235](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L229-L235), [248-251](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L248-L251), [303-311](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L303-L311), [355-359](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L355-L359), [364-367](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L364-L367) ):

```solidity
138:     function verifyAttestation(bytes calldata data) external view override returns (bool) {

162:     function _verify(bytes calldata quote) private view returns (bool, bytes memory) {

175:     function _verifyQEReportWithIdentity(V3Struct.EnclaveReport memory quoteEnclaveReport)
176:         private
177:         view
178:         returns (bool, EnclaveIdStruct.EnclaveIdStatus status)

206:     function _checkTcbLevels(
207:         IPEMCertChainLib.PCKCertificateField memory pck,
208:         TCBInfoStruct.TCBInfo memory tcb
209:     )
210:         private
211:         pure
212:         returns (bool, TCBInfoStruct.TCBStatus status)

229:     function _isCpuSvnHigherOrGreater(
230:         uint256[] memory pckCpuSvns,
231:         uint8[] memory tcbCpuSvns
232:     )
233:         private
234:         pure
235:         returns (bool)

248:     function _verifyCertChain(IPEMCertChainLib.ECSha256Certificate[] memory certs)
249:         private
250:         view
251:         returns (bool)

303:     function _enclaveReportSigVerification(
304:         bytes memory pckCertPubKey,
305:         bytes memory signedQuoteData,
306:         V3Struct.ECDSAQuoteV3AuthData memory authDataV3,
307:         V3Struct.EnclaveReport memory qeEnclaveReport
308:     )
309:         private
310:         view
311:         returns (bool)

355:     function verifyParsedQuote(V3Struct.ParsedV3QuoteStruct calldata v3quote)
356:         external
357:         view
358:         override
359:         returns (bool, bytes memory)

364:     function _verifyParsedQuote(V3Struct.ParsedV3QuoteStruct memory v3quote)
365:         internal
366:         view
367:         returns (bool, bytes memory)
```

- *Asn1Decode.sol* ( [14-14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L14-L14), [19-19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L19-L19), [24-24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L24-L24), [29-29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L29-L29), [47-47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L47-L47), [56-56](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L56-L56), [66-66](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L66-L66), [77-77](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L77-L77), [87-87](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L87-L87), [98-98](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L98-L98), [111-111](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L111-L111), [121-121](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L121-L121), [131-131](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L131-L131), [141-141](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L141-L141), [154-154](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L154-L154), [165-165](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L165-L165), [169-169](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L169-L169), [179-179](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L179-L179), [187-187](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L187-L187) ):

```solidity
14:     function ixs(uint256 self) internal pure returns (uint256) {

19:     function ixf(uint256 self) internal pure returns (uint256) {

24:     function ixl(uint256 self) internal pure returns (uint256) {

29:     function getPtr(uint256 _ixs, uint256 _ixf, uint256 _ixl) internal pure returns (uint256) {

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

187:     function _readNodeLength(bytes memory der, uint256 ix) private pure returns (uint256) {
```

- *BytesUtils.sol* ( [39-39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L39-L39), [56-66](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L56-L66), [116-125](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L116-L125), [138-146](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L138-L146), [160-167](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L160-L167), [178-178](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L178-L178), [284-291](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L284-L291), [320-327](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L320-L327), [371-371](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L371-L371) ):

```solidity
39:     function compare(bytes memory self, bytes memory other) internal pure returns (int256) {

56:     function compare(
57:         bytes memory self,
58:         uint256 offset,
59:         uint256 len,
60:         bytes memory other,
61:         uint256 otheroffset,
62:         uint256 otherlen
63:     )
64:         internal
65:         pure
66:         returns (int256)

116:     function equals(
117:         bytes memory self,
118:         uint256 offset,
119:         bytes memory other,
120:         uint256 otherOffset,
121:         uint256 len
122:     )
123:         internal
124:         pure
125:         returns (bool)

138:     function equals(
139:         bytes memory self,
140:         uint256 offset,
141:         bytes memory other,
142:         uint256 otherOffset
143:     )
144:         internal
145:         pure
146:         returns (bool)

160:     function equals(
161:         bytes memory self,
162:         uint256 offset,
163:         bytes memory other
164:     )
165:         internal
166:         pure
167:         returns (bool)

178:     function equals(bytes memory self, bytes memory other) internal pure returns (bool) {

284:     function substring(
285:         bytes memory self,
286:         uint256 offset,
287:         uint256 len
288:     )
289:         internal
290:         pure
291:         returns (bytes memory)

320:     function base32HexDecodeWord(
321:         bytes memory self,
322:         uint256 off,
323:         uint256 len
324:     )
325:         internal
326:         pure
327:         returns (bytes32)

371:     function compareBytes(bytes memory a, bytes memory b) internal pure returns (bool) {
```

- *RsaVerify.sol* ( [43-51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L43-L51), [191-199](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L191-L199), [212-220](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L212-L220), [307-315](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L307-L315) ):

```solidity
43:     function pkcs1Sha256(
44:         bytes32 _sha256,
45:         bytes memory _s,
46:         bytes memory _e,
47:         bytes memory _m
48:     )
49:         internal
50:         view
51:         returns (bool)

191:     function pkcs1Sha256Raw(
192:         bytes memory _data,
193:         bytes memory _s,
194:         bytes memory _e,
195:         bytes memory _m
196:     )
197:         internal
198:         view
199:         returns (bool)

212:     function pkcs1Sha1(
213:         bytes20 _sha1,
214:         bytes memory _s,
215:         bytes memory _e,
216:         bytes memory _m
217:     )
218:         internal
219:         view
220:         returns (bool)

307:     function pkcs1Sha1Raw(
308:         bytes memory _data,
309:         bytes memory _s,
310:         bytes memory _e,
311:         bytes memory _m
312:     )
313:         internal
314:         view
315:         returns (bool)
```

- *SigVerifyLib.sol* ( [24-32](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L24-L32), [54-62](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L54-L62) ):

```solidity
24:     function verifyAttStmtSignature(
25:         bytes memory tbs,
26:         bytes memory signature,
27:         PublicKey memory publicKey,
28:         Algorithm alg
29:     )
30:         public
31:         view
32:         returns (bool)

54:     function verifyCertificateSignature(
55:         bytes memory tbs,
56:         bytes memory signature,
57:         PublicKey memory publicKey,
58:         CertSigAlgorithm alg
59:     )
60:         public
61:         view
62:         returns (bool)
```

- *X509DateUtils.sol* ( [8-8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L8-L8), [34-44](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L34-L44), [71-71](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L71-L71) ):

```solidity
8:     function toTimestamp(bytes memory x509Time) internal pure returns (uint256) {

34:     function toUnixTimestamp(
35:         uint16 year,
36:         uint8 month,
37:         uint8 day,
38:         uint8 hour,
39:         uint8 minute,
40:         uint8 second
41:     )
42:         internal
43:         pure
44:         returns (uint256)

71:     function isLeapYear(uint16 year) internal pure returns (bool) {
```

- *Bridge.sol* ( [340-340](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L340-L340), [352-358](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L352-L358), [374-380](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L374-L380), [449-449](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L449-L449), [456-456](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L456-L456), [555-555](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L555-L555) ):

```solidity
340:     function isMessageSent(Message calldata _message) public view returns (bool) {

352:     function proveMessageFailed(
353:         Message calldata _message,
354:         bytes calldata _proof
355:     )
356:         public
357:         view
358:         returns (bool)

374:     function proveMessageReceived(
375:         Message calldata _message,
376:         bytes calldata _proof
377:     )
378:         public
379:         view
380:         returns (bool)

449:     function hashMessage(Message memory _message) public pure returns (bytes32) {

456:     function signalForFailedMessage(bytes32 _msgHash) public pure returns (bytes32) {

555:     function _loadContext() private view returns (Context memory) {
```

- *AddressManager.sol* ( [54-54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L54-L54) ):

```solidity
54:     function getAddress(uint64 _chainId, bytes32 _name) public view override returns (address) {
```

- *AddressResolver.sol* ( [30-37](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L30-L37), [43-51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L43-L51) ):

```solidity
30:     function resolve(
31:         bytes32 _name,
32:         bool _allowZeroAddress
33:     )
34:         public
35:         view
36:         virtual
37:         returns (address payable)

43:     function resolve(
44:         uint64 _chainId,
45:         bytes32 _name,
46:         bool _allowZeroAddress
47:     )
48:         public
49:         view
50:         virtual
51:         returns (address payable)
```

- *EssentialContract.sol* ( [88-88](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L88-L88), [140-140](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L140-L140) ):

```solidity
88:     function paused() public view returns (bool) {

140:     function _inNonReentrant() internal view returns (bool) {
```

- *LibAddress.sol* ( [61-68](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L61-L68), [77-77](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L77-L77) ):

```solidity
61:     function isValidSignature(
62:         address _addr,
63:         bytes32 _hash,
64:         bytes memory _sig
65:     )
66:         internal
67:         view
68:         returns (bool)

77:     function isSenderEOA() internal view returns (bool) {
```

- *LibMath.sol* ( [12-12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibMath.sol#L12-L12), [20-20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibMath.sol#L20-L20) ):

```solidity
12:     function min(uint256 _a, uint256 _b) internal pure returns (uint256) {

20:     function max(uint256 _a, uint256 _b) internal pure returns (uint256) {
```

- *SignalService.sol* ( [63-63](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L63-L63), [68-75](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L68-L75), [137-146](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L137-L146), [153-153](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L153-L153), [177-184](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L177-L184), [194-201](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L194-L201), [206-219](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L206-L219) ):

```solidity
63:     function sendSignal(bytes32 _signal) external returns (bytes32) {

68:     function syncChainData(
69:         uint64 _chainId,
70:         bytes32 _kind,
71:         uint64 _blockId,
72:         bytes32 _chainData
73:     )
74:         external
75:         returns (bytes32)

137:     function isChainDataSynced(
138:         uint64 _chainId,
139:         bytes32 _kind,
140:         uint64 _blockId,
141:         bytes32 _chainData
142:     )
143:         public
144:         view
145:         nonZeroValue(_chainData)
146:         returns (bool)

153:     function isSignalSent(address _app, bytes32 _signal) public view returns (bool) {

177:     function signalForChainData(
178:         uint64 _chainId,
179:         bytes32 _kind,
180:         uint64 _blockId
181:     )
182:         public
183:         pure
184:         returns (bytes32)

194:     function getSignalSlot(
195:         uint64 _chainId,
196:         address _app,
197:         bytes32 _signal
198:     )
199:         public
200:         pure
201:         returns (bytes32)

206:     function _verifyHopProof(
207:         uint64 _chainId,
208:         address _app,
209:         bytes32 _signal,
210:         bytes32 _value,
211:         HopProof memory _hop,
212:         address _signalService
213:     )
214:         internal
215:         virtual
216:         validSender(_app)
217:         nonZeroValue(_signal)
218:         nonZeroValue(_value)
219:         returns (bytes32)
```

- *TimelockTokenPool.sol* ( [204-204](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L204-L204), [235-235](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L235-L235), [239-239](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L239-L239), [245-253](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L245-L253) ):

```solidity
204:     function getMyGrant(address _recipient) public view returns (Grant memory) {

235:     function _getAmountOwned(Grant memory _grant) private view returns (uint128) {

239:     function _getAmountUnlocked(Grant memory _grant) private view returns (uint128) {

245:     function _calcAmount(
246:         uint128 _amount,
247:         uint64 _start,
248:         uint64 _cliff,
249:         uint64 _period
250:     )
251:         private
252:         view
253:         returns (uint128)
```

- *MerkleClaimable.sol* ( [77-85](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L77-L85) ):

```solidity
77:     function _verifyMerkleProof(
78:         bytes32[] calldata _proof,
79:         bytes32 _merkleRoot,
80:         bytes32 _value
81:     )
82:         internal
83:         pure
84:         virtual
85:         returns (bool)
```

- *ExcessivelySafeCall.sol* ( [25-33](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L25-L33) ):

```solidity
25:     function excessivelySafeCall(
26:         address _target,
27:         uint256 _gas,
28:         uint256 _value,
29:         uint16 _maxCopy,
30:         bytes memory _calldata
31:     )
32:         internal
33:         returns (bool, bytes memory)
```

- *Bytes.sol* ( [15-22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L15-L22), [91-91](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L91-L91), [102-102](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L102-L102), [149-149](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L149-L149) ):

```solidity
15:     function slice(
16:         bytes memory _bytes,
17:         uint256 _start,
18:         uint256 _length
19:     )
20:         internal
21:         pure
22:         returns (bytes memory)

91:     function slice(bytes memory _bytes, uint256 _start) internal pure returns (bytes memory) {

102:     function toNibbles(bytes memory _bytes) internal pure returns (bytes memory) {

149:     function equal(bytes memory _bytes, bytes memory _other) internal pure returns (bool) {
```

- *BaseVault.sol* ( [39-39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L39-L39) ):

```solidity
39:     function supportsInterface(bytes4 _interfaceId) public view virtual override returns (bool) {
```

- *BridgedERC1155.sol* ( [115-115](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L115-L115), [121-121](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L121-L121) ):

```solidity
115:     function name() public view returns (string memory) {

121:     function symbol() public view returns (string memory) {
```

- *BridgedERC20.sol* ( [91-95](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L91-L95), [102-106](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L102-L106), [113-117](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L113-L117), [125-125](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L125-L125) ):

```solidity
91:     function name()
92:         public
93:         view
94:         override(ERC20Upgradeable, IERC20MetadataUpgradeable)
95:         returns (string memory)

102:     function symbol()
103:         public
104:         view
105:         override(ERC20Upgradeable, IERC20MetadataUpgradeable)
106:         returns (string memory)

113:     function decimals()
114:         public
115:         view
116:         override(ERC20Upgradeable, IERC20MetadataUpgradeable)
117:         returns (uint8)

125:     function canonical() public view returns (address, uint256) {
```

- *BridgedERC20Base.sol* ( [93-93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L93-L93), [101-101](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L101-L101) ):

```solidity
93:     function owner() public view override(IBridgedERC20, OwnableUpgradeable) returns (address) {

101:     function _isMigratingOut() internal view returns (bool) {
```

- *BridgedERC721.sol* ( [87-87](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L87-L87), [93-93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L93-L93), [100-100](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L100-L100), [107-107](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L107-L107) ):

```solidity
87:     function name() public view override(ERC721Upgradeable) returns (string memory) {

93:     function symbol() public view override(ERC721Upgradeable) returns (string memory) {

100:     function source() public view returns (address, uint256) {

107:     function tokenURI(uint256 _tokenId) public view virtual override returns (string memory) {
```

- *ERC1155Vault.sol* ( [160-169](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L160-L169), [175-184](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L175-L184), [192-197](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L192-L197), [204-204](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L204-L204) ):

```solidity
160:     function onERC1155BatchReceived(
161:         address,
162:         address,
163:         uint256[] calldata,
164:         uint256[] calldata,
165:         bytes calldata
166:     )
167:         external
168:         pure
169:         returns (bytes4)

175:     function onERC1155Received(
176:         address,
177:         address,
178:         uint256,
179:         uint256,
180:         bytes calldata
181:     )
182:         external
183:         pure
184:         returns (bytes4)

192:     function supportsInterface(bytes4 interfaceId)
193:         public
194:         view
195:         virtual
196:         override(BaseVault, ERC1155ReceiverUpgradeable)
197:         returns (bool)

204:     function name() public pure override returns (bytes32) {
```

- *ERC20Vault.sol* ( [316-316](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L316-L316) ):

```solidity
316:     function name() public pure override returns (bytes32) {
```

- *ERC721Vault.sol* ( [142-150](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L142-L150), [156-156](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L156-L156) ):

```solidity
142:     function onERC721Received(
143:         address,
144:         address,
145:         uint256,
146:         bytes calldata
147:     )
148:         external
149:         pure
150:         returns (bytes4)

156:     function name() public pure override returns (bytes32) {
```

- *LibBridgedToken.sol* ( [28-34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L28-L34), [39-39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L39-L39), [43-49](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L43-L49) ):

```solidity
28:     function buildName(
29:         string memory _name,
30:         uint256 _srcChainId
31:     )
32:         internal
33:         pure
34:         returns (string memory)

39:     function buildSymbol(string memory _symbol) internal pure returns (string memory) {

43:     function buildURI(
44:         address _srcToken,
45:         uint256 _srcChainId
46:     )
47:         internal
48:         pure
49:         returns (string memory)
```

- *SgxVerifier.sol* ( [90-93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L90-L93), [118-120](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L118-L120), [171-179](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L171-L179), [233-233](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L233-L233) ):

```solidity
90:     function addInstances(address[] calldata _instances)
91:         external
92:         onlyOwner
93:         returns (uint256[] memory)

118:     function registerInstance(V3Struct.ParsedV3QuoteStruct calldata _attestation)
119:         external
120:         returns (uint256)

171:     function getSignedHash(
172:         TaikoData.Transition memory _tran,
173:         address _newInstance,
174:         address _prover,
175:         bytes32 _metaHash
176:     )
177:         public
178:         view
179:         returns (bytes32)

233:     function _isInstanceValid(uint256 id, address instance) private view returns (bool) {
```

</details>

### [N-69] Use `type(X).max` instead of constant formulas like `2**n`

Earlier versions of solidity can use `uint<n>(-1)` instead. Expressions `2**n -1` can often be rewritten to accommodate the change (e.g. by using a `>` instead of a `>=`, which will also saves gas).

There are 2 instances:

- *BytesUtils.sol* ( [93-93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L93-L93) ):

```solidity
93:                     mask = ~(2 ** (8 * (32 - shortest + idx)) - 1);
```

- *LibFixedPointMath.sol* ( [39-39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L39-L39) ):

```solidity
39:             int256 k = ((x << 96) / 54_916_777_467_707_473_351_141_471_128 + 2 ** 95) >> 96;
```

### [N-70] Consider using the `using`-`for` syntax

The `using`-`for` [syntax](https://docs.soliditylang.org/en/latest/contracts.html#using-for) is the more common way of calling library functions.

<details>
<summary>There are 96 instances (click to show):</summary>

- *TaikoL1.sol* ( [51-51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L51-L51), [67-67](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L67-L67), [70-70](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L70-L70), [94-94](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L94-L94), [96-96](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L96-L96), [106-106](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L106-L106), [113-113](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L113-L113), [120-120](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L120-L120), [133-133](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L133-L133), [138-138](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L138-L138), [151-151](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L151-L151), [170-170](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L170-L170) ):

```solidity
51:         LibVerifying.init(state, getConfig(), _genesisBlockHash);

67:         (meta_, deposits_) = LibProposing.proposeBlock(state, config, this, _params, _txList);

70:             LibVerifying.verifyBlocks(state, config, this, config.maxBlocksToVerifyPerProposal);

94:         uint8 maxBlocksToVerify = LibProving.proveBlock(state, config, this, meta, tran, proof);

96:         LibVerifying.verifyBlocks(state, config, this, maxBlocksToVerify);

106:         LibVerifying.verifyBlocks(state, getConfig(), this, _maxBlocksToVerify);

113:         LibProving.pauseProving(state, _pause);

120:         LibDepositing.depositEtherToL2(state, getConfig(), this, _recipient);

133:         return LibDepositing.canDepositEthToL2(state, getConfig(), _amount);

138:         return LibProposing.isBlobReusable(state, getConfig(), _blobHash);

151:         (blk_, slot) = LibUtils.getBlock(state, getConfig(), _blockId);

170:         return LibUtils.getTransition(state, getConfig(), _blockId, _parentHash);
```

- *LibProposing.sol* ( [114-114](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L114-L114), [182-182](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L182-L182) ):

```solidity
114:         deposits_ = LibDepositing.processDeposits(_state, _config, params.coinbase);

182:             if (!LibAddress.isSenderEOA()) revert L1_PROPOSER_NOT_EOA();
```

- *LibProving.sol* ( [278-278](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L278-L278) ):

```solidity
278:         tid_ = LibUtils.getTransitionId(_state, _blk, slot, _tran.parentHash);
```

- *LibVerifying.sol* ( [133-133](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L133-L133) ):

```solidity
133:                 tid = LibUtils.getTransitionId(_state, blk, slot, blockHash);
```

- *Lib1559Math.sol* ( [45-45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/Lib1559Math.sol#L45-L45) ):

```solidity
45:         return uint256(LibFixedPointMath.exp(int256(input)));
```

- *TaikoL2.sol* ( [290-292](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L290-L292) ):

```solidity
290:             basefee_ = Lib1559Math.basefee(
291:                 gasExcess_, uint256(_config.basefeeAdjustmentQuotient) * _config.gasTargetPerL1Block
292:             );
```

- *AutomataDcapV3Attestation.sol* ( [167-167](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L167-L167), [321-321](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L321-L321), [378-378](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L378-L378), [437-437](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L437-L437), [443-443](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L443-L443) ):

```solidity
167:             V3Parser.parseInput(quote, address(pemCertLib));

321:                 V3Parser.packQEReport(authDataV3.pckSignedQeReport);

378:         ) = V3Parser.validateParsedInput(v3quote);

437:             bool tcbConfigured = LibString.eq(parsedFmspc, fetchedTcbInfo.fmspc);

443:             bool pceidMatched = LibString.eq(pckCert.pck.sgxExtension.pceid, fetchedTcbInfo.pceid);
```

- *PEMCertChainLib.sol* ( [57-57](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L57-L57), [120-120](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L120-L120), [121-121](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L121-L121), [140-140](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L140-L140), [141-141](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L141-L141), [152-152](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L152-L152), [171-171](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L171-L171), [208-208](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L208-L208), [209-209](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L209-L209), [222-222](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L222-L222), [223-223](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L223-L223), [240-240](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L240-L240), [241-241](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L241-L241), [245-245](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L245-L245), [292-292](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L292-L292), [306-306](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L306-L306), [310-310](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L310-L310), [316-316](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L316-L316), [361-361](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L361-L361) ):

```solidity
57:                 input = LibString.slice(pemChainStr, index, index + len);

120:             bool issuerNameIsValid = LibString.eq(cert.pck.issuerName, PLATFORM_ISSUER_NAME)

121:                 || LibString.eq(cert.pck.issuerName, PROCESSOR_ISSUER_NAME);

140:             cert.notBefore = X509DateUtils.toTimestamp(der.bytesAt(notBeforePtr));

141:             cert.notAfter = X509DateUtils.toTimestamp(der.bytesAt(notAfterPtr));

152:             if (!LibString.eq(cert.pck.commonName, PCK_COMMON_NAME)) {

171:             sigPtr = NodePtr.getPtr(sigPtr.ixs() + 3, sigPtr.ixf() + 3, sigPtr.ixl());

208:             cert.pck.sgxExtension.pceid = LibString.toHexStringNoPrefix(pceidBytes);

209:             cert.pck.sgxExtension.fmspc = LibString.toHexStringNoPrefix(fmspcBytes);

222:         uint256 beginPos = LibString.indexOf(pemData, HEADER);

223:         uint256 endPos = LibString.indexOf(pemData, FOOTER);

240:         string memory contentSlice = LibString.slice(pemData, contentStart, endPos);

241:         string[] memory split = LibString.split(contentSlice, string(delimiter));

245:             contentStr = LibString.concat(contentStr, split[i]);

292:             if (BytesUtils.compareBytes(der.bytesAt(internalPtr), SGX_EXTENSION_OID)) {

306:                     if (BytesUtils.compareBytes(der.bytesAt(extnValueOidPtr), TCB_OID)) {

310:                     if (BytesUtils.compareBytes(der.bytesAt(extnValueOidPtr), PCEID_OID)) {

316:                     if (BytesUtils.compareBytes(der.bytesAt(extnValueOidPtr), FMSPC_OID)) {

361:             if (BytesUtils.compareBytes(der.bytesAt(svnPtr), PCESVN_OID)) {
```

- *V3Parser.sol* ( [129-129](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L129-L129), [282-282](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L282-L282) ):

```solidity
129:         signedQuoteData = abi.encodePacked(headerBytes, V3Parser.packQEReport(localEnclaveReport));

282:             quoteCerts[i] = Base64.decode(string(quoteCerts[i]));
```

- *Asn1Decode.sol* ( [209-209](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L209-L209) ):

```solidity
209:         return NodePtr.getPtr(ix, ixFirstContentByte, ixLastContentByte);
```

- *RsaVerify.sol* ( [317-317](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L317-L317) ):

```solidity
317:         return pkcs1Sha1(SHA1.sha1(_data), _s, _e, _m);
```

- *SigVerifyLib.sol* ( [93-93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L93-L93), [110-110](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L110-L110) ):

```solidity
93:         sigValid = RsaVerify.pkcs1Sha256Raw(tbs, signature, exponent, modulus);

110:         sigValid = RsaVerify.pkcs1Sha1Raw(tbs, signature, exponent, modulus);
```

- *Bridge.sol* ( [497-503](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L497-L503) ):

```solidity
497:             (success_,) = ExcessivelySafeCall.excessivelySafeCall(
498:                 _message.to,
499:                 _gasLimit,
500:                 _message.value,
501:                 64, // return max 64 bytes
502:                 _message.data
503:             );
```

- *LibAddress.sol* ( [27-33](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L27-L33), [54-54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L54-L54), [70-70](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L70-L70), [73-73](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L73-L73) ):

```solidity
27:         (bool success,) = ExcessivelySafeCall.excessivelySafeCall(
28:             _to,
29:             _gasLimit,
30:             _amount,
31:             64, // return max 64 bytes
32:             ""
33:         );

54:         if (!Address.isContract(_addr)) return false;

70:         if (Address.isContract(_addr)) {

73:             return ECDSA.recover(_hash, _sig) == _addr;
```

- *LibTrieProof.sol* ( [48-48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibTrieProof.sol#L48-L48), [52-52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibTrieProof.sol#L52-L52), [55-55](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibTrieProof.sol#L55-L55), [60-62](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibTrieProof.sol#L60-L62), [61-61](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibTrieProof.sol#L61-L61) ):

```solidity
48:                 SecureMerkleTrie.get(abi.encodePacked(_addr), _accountProof, _rootHash);

52:             RLPReader.RLPItem[] memory accountState = RLPReader.readList(rlpAccount);

55:                 bytes32(RLPReader.readBytes(accountState[_ACCOUNT_FIELD_INDEX_STORAGE_HASH]));

60:         bool verified = SecureMerkleTrie.verifyInclusionProof(
61:             bytes.concat(_slot), RLPWriter.writeUint(uint256(_value)), _storageProof, storageRoot_
62:         );

61:             bytes.concat(_slot), RLPWriter.writeUint(uint256(_value)), _storageProof, storageRoot_
```

- *SignalService.sol* ( [221-228](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L221-L228) ):

```solidity
221:         return LibTrieProof.verifyMerkleProof(
222:             _hop.rootHash,
223:             _signalService,
224:             getSignalSlot(_chainId, _app, _signal),
225:             _value,
226:             _hop.accountProof,
227:             _hop.storageProof
228:         );
```

- *TimelockTokenPool.sol* ( [171-171](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L171-L171) ):

```solidity
171:         address recipient = ECDSA.recover(hash, _sig);
```

- *MerkleClaimable.sol* ( [87-87](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L87-L87) ):

```solidity
87:         return MerkleProof.verify(_proof, _merkleRoot, _value);
```

- *MerkleTrie.sol* ( [60-60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L60-L60), [80-80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L80-L80), [94-94](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L94-L94), [100-100](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L100-L100), [106-106](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L106-L106), [118-118](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L118-L118), [143-143](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L143-L143), [144-144](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L144-L144), [171-171](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L171-L171), [209-209](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L209-L209), [221-221](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L221-L221), [221-221](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L221-L221), [228-228](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L228-L228), [228-228](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L228-L228) ):

```solidity
60:         valid_ = Bytes.equal(_value, get(_key, _proof, _root));

80:         bytes memory key = Bytes.toNibbles(_key);

94:                     Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),

100:                     Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),

106:                     Bytes.equal(currentNode.encoded, currentNodeID),

118:                     value_ = RLPReader.readBytes(currentNode.decoded[TREE_RADIX]);

143:                 bytes memory pathRemainder = Bytes.slice(path, offset);

144:                 bytes memory keyRemainder = Bytes.slice(key, currentKeyIndex);

171:                     value_ = RLPReader.readBytes(currentNode.decoded[1]);

209:             proof_[i] = TrieNode({ encoded: _proof[i], decoded: RLPReader.readList(_proof[i]) });

221:         id_ = _node.length < 32 ? RLPReader.readRawBytes(_node) : RLPReader.readBytes(_node);

221:         id_ = _node.length < 32 ? RLPReader.readRawBytes(_node) : RLPReader.readBytes(_node);

228:         nibbles_ = Bytes.toNibbles(RLPReader.readBytes(_node.decoded[0]));

228:         nibbles_ = Bytes.toNibbles(RLPReader.readBytes(_node.decoded[0]));
```

- *SecureMerkleTrie.sol* ( [30-30](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L30-L30), [48-48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L48-L48) ):

```solidity
30:         valid_ = MerkleTrie.verifyInclusionProof(key, _value, _proof, _root);

48:         value_ = MerkleTrie.get(key, _proof, _root);
```

- *BridgedERC1155.sol* ( [52-52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L52-L52), [54-54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L54-L54), [116-116](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L116-L116), [122-122](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L122-L122) ):

```solidity
52:         LibBridgedToken.validateInputs(_srcToken, _srcChainId, "foo", "foo");

54:         __ERC1155_init(LibBridgedToken.buildURI(_srcToken, _srcChainId));

116:         return LibBridgedToken.buildName(__name, srcChainId);

122:         return LibBridgedToken.buildSymbol(__symbol);
```

- *BridgedERC20.sol* ( [65-65](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L65-L65), [97-97](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L97-L97), [108-108](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L108-L108) ):

```solidity
65:         LibBridgedToken.validateInputs(_srcToken, _srcChainId, _symbol, _name);

97:         return LibBridgedToken.buildName(super.name(), srcChainId);

108:         return LibBridgedToken.buildSymbol(super.symbol());
```

- *BridgedERC721.sol* ( [43-43](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L43-L43), [88-88](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L88-L88), [94-94](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L94-L94), [110-110](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L110-L110), [110-110](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L110-L110) ):

```solidity
43:         LibBridgedToken.validateInputs(_srcToken, _srcChainId, _symbol, _name);

88:         return LibBridgedToken.buildName(super.name(), srcChainId);

94:         return LibBridgedToken.buildSymbol(super.symbol());

110:                 LibBridgedToken.buildURI(srcToken, srcChainId), Strings.toString(_tokenId)

110:                 LibBridgedToken.buildURI(srcToken, srcChainId), Strings.toString(_tokenId)
```

- *LibBridgedToken.sol* ( [36-36](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L36-L36), [56-56](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L56-L56), [58-58](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L58-L58) ):

```solidity
36:         return string.concat("Bridged ", _name, unicode" (⭀", Strings.toString(_srcChainId), ")");

56:                 Strings.toHexString(uint160(_srcToken), 20),

58:                 Strings.toString(_srcChainId),
```

- *SgxVerifier.sol* ( [154-154](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L154-L154), [155-155](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L155-L155), [156-156](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L156-L156), [159-159](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L159-L159) ):

```solidity
154:         uint32 id = uint32(bytes4(Bytes.slice(_proof.data, 0, 4)));

155:         address newInstance = address(bytes20(Bytes.slice(_proof.data, 4, 20)));

156:         bytes memory signature = Bytes.slice(_proof.data, 24);

159:             ECDSA.recover(getSignedHash(_tran, newInstance, _ctx.prover, _ctx.metaHash), signature);
```

</details>

### [N-71] Using underscore at the end of variable name

The use of the underscore at the end of the variable name is unusual, consider refactoring it.

<details>
<summary>There are 95 instances (click to show):</summary>

- *ITaikoL1.sol* ( [20-20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/ITaikoL1.sol#L20-L20), [20-20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/ITaikoL1.sol#L20-L20) ):

```solidity
/// @audit meta_
20:         returns (TaikoData.BlockMetadata memory meta_, TaikoData.EthDeposit[] memory deposits_);

/// @audit deposits_
20:         returns (TaikoData.BlockMetadata memory meta_, TaikoData.EthDeposit[] memory deposits_);
```

- *TaikoL1.sol* ( [63-63](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L63-L63), [63-63](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L63-L63), [148-148](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L148-L148), [148-148](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L148-L148), [179-179](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L179-L179), [179-179](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L179-L179) ):

```solidity
/// @audit meta_
63:         returns (TaikoData.BlockMetadata memory meta_, TaikoData.EthDeposit[] memory deposits_)

/// @audit deposits_
63:         returns (TaikoData.BlockMetadata memory meta_, TaikoData.EthDeposit[] memory deposits_)

/// @audit blk_
148:         returns (TaikoData.Block memory blk_, TaikoData.TransitionState memory ts_)

/// @audit ts_
148:         returns (TaikoData.Block memory blk_, TaikoData.TransitionState memory ts_)

/// @audit a_
179:         returns (TaikoData.SlotA memory a_, TaikoData.SlotB memory b_)

/// @audit b_
179:         returns (TaikoData.SlotA memory a_, TaikoData.SlotB memory b_)
```

- *LibDepositing.sol* ( [44-44](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L44-L44), [73-73](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L73-L73) ):

```solidity
/// @audit recipient_
44:         address recipient_ = _recipient == address(0) ? msg.sender : _recipient;

/// @audit deposits_
73:         returns (TaikoData.EthDeposit[] memory deposits_)
```

- *LibProposing.sol* ( [76-76](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L76-L76), [76-76](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L76-L76) ):

```solidity
/// @audit meta_
76:         returns (TaikoData.BlockMetadata memory meta_, TaikoData.EthDeposit[] memory deposits_)

/// @audit deposits_
76:         returns (TaikoData.BlockMetadata memory meta_, TaikoData.EthDeposit[] memory deposits_)
```

- *LibProving.sol* ( [100-100](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L100-L100), [276-276](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L276-L276), [276-276](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L276-L276) ):

```solidity
/// @audit maxBlocksToVerify_
100:         returns (uint8 maxBlocksToVerify_)

/// @audit tid_
276:         returns (uint32 tid_, TaikoData.TransitionState storage ts_)

/// @audit ts_
276:         returns (uint32 tid_, TaikoData.TransitionState storage ts_)
```

- *LibUtils.sol* ( [59-59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L59-L59), [59-59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L59-L59), [78-78](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L78-L78) ):

```solidity
/// @audit blk_
59:         returns (TaikoData.Block storage blk_, uint64 slot_)

/// @audit slot_
59:         returns (TaikoData.Block storage blk_, uint64 slot_)

/// @audit tid_
78:         returns (uint32 tid_)
```

- *GuardianProver.sol* ( [43-43](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/GuardianProver.sol#L43-L43) ):

```solidity
/// @audit approved_
43:         returns (bool approved_)
```

- *Guardians.sol* ( [111-111](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L111-L111) ):

```solidity
/// @audit approved_
111:     function approve(uint256 _operationId, bytes32 _hash) internal returns (bool approved_) {
```

- *DevnetTierProvider.sol* ( [47-47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L47-L47) ):

```solidity
/// @audit tiers_
47:     function getTierIds() public pure override returns (uint16[] memory tiers_) {
```

- *MainnetTierProvider.sol* ( [58-58](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L58-L58) ):

```solidity
/// @audit tiers_
58:     function getTierIds() public pure override returns (uint16[] memory tiers_) {
```

- *TestnetTierProvider.sol* ( [58-58](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L58-L58) ):

```solidity
/// @audit tiers_
58:     function getTierIds() public pure override returns (uint16[] memory tiers_) {
```

- *TaikoL2.sol* ( [191-191](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L191-L191), [208-208](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L208-L208), [259-259](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L259-L259), [259-259](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L259-L259) ):

```solidity
/// @audit basefee_
191:         returns (uint256 basefee_)

/// @audit config_
208:     function getConfig() public view virtual returns (Config memory config_) {

/// @audit basefee_
259:         returns (uint256 basefee_, uint64 gasExcess_)

/// @audit gasExcess_
259:         returns (uint256 basefee_, uint64 gasExcess_)
```

- *Bridge.sol* ( [121-121](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L121-L121), [121-121](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L121-L121), [395-395](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L395-L395), [395-395](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L395-L395), [403-403](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L403-L403), [421-421](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L421-L421), [421-421](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L421-L421), [483-483](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L483-L483), [585-585](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L585-L585) ):

```solidity
/// @audit msgHash_
121:         returns (bytes32 msgHash_, Message memory message_)

/// @audit message_
121:         returns (bytes32 msgHash_, Message memory message_)

/// @audit enabled_
395:         returns (bool enabled_, address destBridge_)

/// @audit destBridge_
395:         returns (bool enabled_, address destBridge_)

/// @audit ctx_
403:     function context() public view returns (Context memory ctx_) {

/// @audit invocationDelay_
421:         returns (uint256 invocationDelay_, uint256 invocationExtraDelay_)

/// @audit invocationExtraDelay_
421:         returns (uint256 invocationDelay_, uint256 invocationExtraDelay_)

/// @audit success_
483:         returns (bool success_)

/// @audit success_
585:         returns (bool success_)
```

- *IBridge.sol* ( [112-112](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/IBridge.sol#L112-L112), [112-112](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/IBridge.sol#L112-L112), [145-145](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/IBridge.sol#L145-L145) ):

```solidity
/// @audit msgHash_
112:         returns (bytes32 msgHash_, Message memory message_);

/// @audit message_
112:         returns (bytes32 msgHash_, Message memory message_);

/// @audit ctx_
145:     function context() external view returns (Context memory ctx_);
```

- *AddressResolver.sol* ( [79-79](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L79-L79) ):

```solidity
/// @audit addr_
79:         returns (address payable addr_)
```

- *EssentialContract.sol* ( [130-130](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L130-L130) ):

```solidity
/// @audit reentry_
130:     function _loadReentryLock() internal view virtual returns (uint8 reentry_) {
```

- *LibAddress.sol* ( [52-52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L52-L52) ):

```solidity
/// @audit result_
52:         returns (bool result_)
```

- *LibTrieProof.sol* ( [44-44](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibTrieProof.sol#L44-L44) ):

```solidity
/// @audit storageRoot_
44:         returns (bytes32 storageRoot_)
```

- *ISignalService.sol* ( [59-59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/ISignalService.sol#L59-L59), [75-75](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/ISignalService.sol#L75-L75), [129-129](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/ISignalService.sol#L129-L129), [129-129](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/ISignalService.sol#L129-L129), [144-144](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/ISignalService.sol#L144-L144) ):

```solidity
/// @audit slot_
59:     function sendSignal(bytes32 _signal) external returns (bytes32 slot_);

/// @audit signal_
75:         returns (bytes32 signal_);

/// @audit blockId_
129:         returns (uint64 blockId_, bytes32 chainData_);

/// @audit chainData_
129:         returns (uint64 blockId_, bytes32 chainData_);

/// @audit signal_
144:         returns (bytes32 signal_);
```

- *SignalService.sol* ( [165-165](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L165-L165), [165-165](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L165-L165), [242-242](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L242-L242), [262-262](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L262-L262), [306-306](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L306-L306) ):

```solidity
/// @audit blockId_
165:         returns (uint64 blockId_, bytes32 chainData_)

/// @audit chainData_
165:         returns (uint64 blockId_, bytes32 chainData_)

/// @audit signal_
242:         returns (bytes32 signal_)

/// @audit slot_
262:         returns (bytes32 slot_)

/// @audit value_
306:         returns (bytes32 value_)
```

- *RLPReader.sol* ( [35-35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L35-L35), [53-53](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L53-L53), [102-102](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L102-L102), [109-109](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L109-L109), [128-128](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L128-L128), [135-135](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L135-L135), [147-147](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L147-L147), [147-147](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L147-L147), [147-147](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L147-L147), [284-284](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L284-L284) ):

```solidity
/// @audit out_
35:     function toRLPItem(bytes memory _in) internal pure returns (RLPItem memory out_) {

/// @audit out_
53:     function readList(RLPItem memory _in) internal pure returns (RLPItem[] memory out_) {

/// @audit out_
102:     function readList(bytes memory _in) internal pure returns (RLPItem[] memory out_) {

/// @audit out_
109:     function readBytes(RLPItem memory _in) internal pure returns (bytes memory out_) {

/// @audit out_
128:     function readBytes(bytes memory _in) internal pure returns (bytes memory out_) {

/// @audit out_
135:     function readRawBytes(RLPItem memory _in) internal pure returns (bytes memory out_) {

/// @audit offset_
147:         returns (uint256 offset_, uint256 length_, RLPItemType type_)

/// @audit length_
147:         returns (uint256 offset_, uint256 length_, RLPItemType type_)

/// @audit type_
147:         returns (uint256 offset_, uint256 length_, RLPItemType type_)

/// @audit out_
284:         returns (bytes memory out_)
```

- *RLPWriter.sol* ( [13-13](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L13-L13), [24-24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L24-L24), [32-32](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L32-L32), [55-55](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L55-L55) ):

```solidity
/// @audit out_
13:     function writeBytes(bytes memory _in) internal pure returns (bytes memory out_) {

/// @audit out_
24:     function writeUint(uint256 _in) internal pure returns (bytes memory out_) {

/// @audit out_
32:     function _writeLength(uint256 _len, uint256 _offset) private pure returns (bytes memory out_) {

/// @audit out_
55:     function _toBinary(uint256 _x) private pure returns (bytes memory out_) {
```

- *MerkleTrie.sol* ( [58-58](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L58-L58), [75-75](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L75-L75), [205-205](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L205-L205), [220-220](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L220-L220), [227-227](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L227-L227), [241-241](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L241-L241) ):

```solidity
/// @audit valid_
58:         returns (bool valid_)

/// @audit value_
75:         returns (bytes memory value_)

/// @audit proof_
205:     function _parseProof(bytes[] memory _proof) private pure returns (TrieNode[] memory proof_) {

/// @audit id_
220:     function _getNodeID(RLPReader.RLPItem memory _node) private pure returns (bytes memory id_) {

/// @audit nibbles_
227:     function _getNodePath(TrieNode memory _node) private pure returns (bytes memory nibbles_) {

/// @audit shared_
241:         returns (uint256 shared_)
```

- *SecureMerkleTrie.sol* ( [27-27](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L27-L27), [45-45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L45-L45), [54-54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L54-L54) ):

```solidity
/// @audit valid_
27:         returns (bool valid_)

/// @audit value_
45:         returns (bytes memory value_)

/// @audit hash_
54:     function _getSecureKey(bytes memory _key) private pure returns (bytes memory hash_) {
```

- *BaseVault.sol* ( [51-51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L51-L51), [62-62](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L62-L62) ):

```solidity
/// @audit ctx_
51:         returns (IBridge.Context memory ctx_)

/// @audit ctx_
62:         returns (IBridge.Context memory ctx_)
```

- *ERC1155Vault.sol* ( [45-45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L45-L45), [245-245](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L245-L245), [245-245](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L245-L245), [290-290](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L290-L290), [303-303](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L303-L303) ):

```solidity
/// @audit message_
45:         returns (IBridge.Message memory message_)

/// @audit msgData_
245:         returns (bytes memory msgData_, CanonicalNFT memory ctoken_)

/// @audit ctoken_
245:         returns (bytes memory msgData_, CanonicalNFT memory ctoken_)

/// @audit btoken_
290:         returns (address btoken_)

/// @audit btoken_
303:     function _deployBridgedToken(CanonicalNFT memory _ctoken) private returns (address btoken_) {
```

- *ERC20Vault.sol* ( [156-156](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L156-L156), [212-212](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L212-L212), [326-326](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L326-L326), [355-355](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L355-L355), [355-355](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L355-L355), [355-355](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L355-L355) ):

```solidity
/// @audit btokenOld_
156:         returns (address btokenOld_)

/// @audit message_
212:         returns (IBridge.Message memory message_)

/// @audit token_
326:         returns (address token_)

/// @audit msgData_
355:         returns (bytes memory msgData_, CanonicalERC20 memory ctoken_, uint256 balanceChange_)

/// @audit ctoken_
355:         returns (bytes memory msgData_, CanonicalERC20 memory ctoken_, uint256 balanceChange_)

/// @audit balanceChange_
355:         returns (bytes memory msgData_, CanonicalERC20 memory ctoken_, uint256 balanceChange_)
```

- *ERC721Vault.sol* ( [32-32](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L32-L32), [166-166](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L166-L166), [192-192](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L192-L192), [192-192](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L192-L192), [226-226](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L226-L226), [240-240](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L240-L240) ):

```solidity
/// @audit message_
32:         returns (IBridge.Message memory message_)

/// @audit token_
166:         returns (address token_)

/// @audit msgData_
192:         returns (bytes memory msgData_, CanonicalNFT memory ctoken_)

/// @audit ctoken_
192:         returns (bytes memory msgData_, CanonicalNFT memory ctoken_)

/// @audit btoken_
226:         returns (address btoken_)

/// @audit btoken_
240:     function _deployBridgedToken(CanonicalNFT memory _ctoken) private returns (address btoken_) {
```

</details>

### [N-72] Use a struct to encapsulate multiple function parameters

If a function has too many parameters, replacing them with a struct can improve code readability and maintainability, increase reusability, and reduce the likelihood of errors when passing the parameters.

<details>
<summary>There are 8 instances (click to show):</summary>

- *TaikoGovernor.sol* ( [69-79](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L69-L79), [127-136](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L127-L136) ):

```solidity
69:     function propose(
70:         address[] memory _targets,
71:         uint256[] memory _values,
72:         string[] memory _signatures,
73:         bytes[] memory _calldatas,
74:         string memory _description
75:     )
76:         public
77:         virtual
78:         override(GovernorCompatibilityBravoUpgradeable)
79:         returns (uint256)

127:     function _execute(
128:         uint256 _proposalId,
129:         address[] memory _targets,
130:         uint256[] memory _values,
131:         bytes[] memory _calldatas,
132:         bytes32 _descriptionHash
133:     )
134:         internal
135:         override(GovernorUpgradeable, GovernorTimelockControlUpgradeable)
136:     {
```

- *SignalService.sol* ( [206-219](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L206-L219), [271-280](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L271-L280) ):

```solidity
206:     function _verifyHopProof(
207:         uint64 _chainId,
208:         address _app,
209:         bytes32 _signal,
210:         bytes32 _value,
211:         HopProof memory _hop,
212:         address _signalService
213:     )
214:         internal
215:         virtual
216:         validSender(_app)
217:         nonZeroValue(_signal)
218:         nonZeroValue(_value)
219:         returns (bytes32)

271:     function _cacheChainData(
272:         HopProof memory _hop,
273:         uint64 _chainId,
274:         uint64 _blockId,
275:         bytes32 _signalRoot,
276:         bool _isFullProof,
277:         bool _isLastHop
278:     )
279:         private
280:     {
```

- *BridgedERC1155.sol* ( [38-48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L38-L48), [125-136](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L125-L136) ):

```solidity
38:     function init(
39:         address _owner,
40:         address _addressManager,
41:         address _srcToken,
42:         uint256 _srcChainId,
43:         string memory _symbol,
44:         string memory _name
45:     )
46:         external
47:         initializer
48:     {

125:     function _beforeTokenTransfer(
126:         address, /*_operator*/
127:         address, /*_from*/
128:         address _to,
129:         uint256[] memory, /*_ids*/
130:         uint256[] memory, /*_amounts*/
131:         bytes memory /*_data*/
132:     )
133:         internal
134:         virtual
135:         override
136:     {
```

- *BridgedERC20.sol* ( [52-63](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L52-L63) ):

```solidity
52:     function init(
53:         address _owner,
54:         address _addressManager,
55:         address _srcToken,
56:         uint256 _srcChainId,
57:         uint8 _decimals,
58:         string memory _symbol,
59:         string memory _name
60:     )
61:         external
62:         initializer
63:     {
```

- *BridgedERC721.sol* ( [31-41](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L31-L41) ):

```solidity
31:     function init(
32:         address _owner,
33:         address _addressManager,
34:         address _srcToken,
35:         uint256 _srcChainId,
36:         string memory _symbol,
37:         string memory _name
38:     )
39:         external
40:         initializer
41:     {
```

</details>

### [N-73] Returning a struct instead of a bunch of variables is better

If a function returns [too many variables](https://docs.soliditylang.org/en/v0.8.21/contracts.html#returning-multiple-values), replacing them with a struct can improve code readability, maintainability and reusability.

<details>
<summary>There are 15 instances (click to show):</summary>

- *ITaikoL1.sol* ( [14-20](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/ITaikoL1.sol#L14-L20) ):

```solidity
14:     function proposeBlock(
15:         bytes calldata _params,
16:         bytes calldata _txList
17:     )
18:         external
19:         payable
20:         returns (TaikoData.BlockMetadata memory meta_, TaikoData.EthDeposit[] memory deposits_);
```

- *TaikoL1.sol* ( [55-63](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L55-L63), [145-148](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L145-L148), [176-179](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L176-L179) ):

```solidity
55:     function proposeBlock(
56:         bytes calldata _params,
57:         bytes calldata _txList
58:     )
59:         external
60:         payable
61:         nonReentrant
62:         whenNotPaused
63:         returns (TaikoData.BlockMetadata memory meta_, TaikoData.EthDeposit[] memory deposits_)

145:     function getBlock(uint64 _blockId)
146:         public
147:         view
148:         returns (TaikoData.Block memory blk_, TaikoData.TransitionState memory ts_)

176:     function getStateVariables()
177:         public
178:         view
179:         returns (TaikoData.SlotA memory a_, TaikoData.SlotB memory b_)
```

- *TaikoL2.sol* ( [223-226](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L223-L226), [252-259](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L252-L259) ):

```solidity
223:     function _calcPublicInputHash(uint256 _blockId)
224:         private
225:         view
226:         returns (bytes32 publicInputHashOld, bytes32 publicInputHashNew)

252:     function _calc1559BaseFee(
253:         Config memory _config,
254:         uint64 _l1BlockId,
255:         uint32 _parentGasUsed
256:     )
257:         private
258:         view
259:         returns (uint256 basefee_, uint64 gasExcess_)
```

- *Bridge.sol* ( [115-121](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L115-L121), [392-395](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L392-L395), [417-421](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L417-L421) ):

```solidity
115:     function sendMessage(Message calldata _message)
116:         external
117:         payable
118:         override
119:         nonReentrant
120:         whenNotPaused
121:         returns (bytes32 msgHash_, Message memory message_)

392:     function isDestChainEnabled(uint64 _chainId)
393:         public
394:         view
395:         returns (bool enabled_, address destBridge_)

417:     function getInvocationDelays()
418:         public
419:         view
420:         virtual
421:         returns (uint256 invocationDelay_, uint256 invocationExtraDelay_)
```

- *IBridge.sol* ( [109-112](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/IBridge.sol#L109-L112) ):

```solidity
109:     function sendMessage(Message calldata _message)
110:         external
111:         payable
112:         returns (bytes32 msgHash_, Message memory message_);
```

- *ISignalService.sol* ( [122-129](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/ISignalService.sol#L122-L129) ):

```solidity
122:     function getSyncedChainData(
123:         uint64 _chainId,
124:         bytes32 _kind,
125:         uint64 _blockId
126:     )
127:         external
128:         view
129:         returns (uint64 blockId_, bytes32 chainData_);
```

- *SignalService.sol* ( [158-165](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L158-L165) ):

```solidity
158:     function getSyncedChainData(
159:         uint64 _chainId,
160:         bytes32 _kind,
161:         uint64 _blockId
162:     )
163:         public
164:         view
165:         returns (uint64 blockId_, bytes32 chainData_)
```

- *BridgedERC20.sol* ( [125-125](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L125-L125) ):

```solidity
125:     function canonical() public view returns (address, uint256) {
```

- *BridgedERC721.sol* ( [100-100](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L100-L100) ):

```solidity
100:     function source() public view returns (address, uint256) {
```

- *ERC1155Vault.sol* ( [240-245](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L240-L245) ):

```solidity
240:     function _handleMessage(
241:         address _user,
242:         BridgeTransferOp memory _op
243:     )
244:         private
245:         returns (bytes memory msgData_, CanonicalNFT memory ctoken_)
```

</details>

### [N-74] Events that mark critical parameter changes should contain both the old and the new value

This should especially be done if the new value is not required to be different from the old value.

There are 4 instances:

- *Guardians.sol* ( [95-95](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L95-L95) ):

```solidity
95:         emit GuardiansUpdated(version, _newGuardians);
```

- *TaikoL2EIP1559Configurable.sol* ( [39-39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L39-L39) ):

```solidity
39:         emit ConfigAndExcessChanged(_newConfig, _newGasExcess);
```

- *Bridge.sol* ( [519-519](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L519-L519) ):

```solidity
519:         emit MessageStatusChanged(_msgHash, _status);
```

- *BridgedERC20Base.sol* ( [51-51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L51-L51) ):

```solidity
51:         emit MigrationStatusChanged(_migratingAddress, _migratingInbound);
```

### [N-75] Contract variables should have comments

Consider adding some comments on non-public contract variables to explain what they are supposed to do. This will help for future code reviews.

<details>
<summary>There are 41 instances (click to show):</summary>

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

- *Guardians.sol* ( [32-32](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L32-L32) ):

```solidity
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

- *AutomataDcapV3Attestation.sol* ( [38-38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L38-L38), [39-39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L39-L39), [40-40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L40-L40) ):

```solidity
38:     bool private _checkLocalEnclaveReport;

39:     mapping(bytes32 enclave => bool trusted) private _trustedUserMrEnclave;

40:     mapping(bytes32 signer => bool trusted) private _trustedUserMrSigner;
```

- *SigVerifyLib.sol* ( [18-18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L18-L18) ):

```solidity
18:     address private ES256VERIFIER;
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

- *EssentialContract.sol* ( [23-23](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L23-L23), [25-25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L25-L25) ):

```solidity
23:     uint8 private __paused;

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

- *BridgedERC20.sol* ( [24-24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L24-L24), [32-32](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L32-L32) ):

```solidity
24:     uint8 private __srcDecimals;

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

### [N-76] Missing event when a state variables is set in constructor

The initial states set in a constructor are important and should be recorded in the event.

There are 2 instances:

- *AutomataDcapV3Attestation.sol* ( [57](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L57) ):

```solidity
57:         owner = msg.sender;
```

- *SigVerifyLib.sol* ( [21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L21) ):

```solidity
21:         ES256VERIFIER = es256Verifier;
```

### [N-77] Empty bytes check is missing

Passing empty bytes to a function can cause unexpected behavior, such as certain operations failing, producing incorrect results, or wasting gas. It is recommended to check that all byte parameters are not empty.

<details>
<summary>There are 13 instances (click to show):</summary>

- *TaikoL1.sol* ( [55-64](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L55-L64), [75-83](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L75-L83) ):

```solidity
/// @audit _params
/// @audit _txList
55:     function proposeBlock(
56:         bytes calldata _params,
57:         bytes calldata _txList
58:     )
59:         external
60:         payable
61:         nonReentrant
62:         whenNotPaused
63:         returns (TaikoData.BlockMetadata memory meta_, TaikoData.EthDeposit[] memory deposits_)
64:     {

/// @audit _input
75:     function proveBlock(
76:         uint64 _blockId,
77:         bytes calldata _input
78:     )
79:         external
80:         nonReentrant
81:         whenNotPaused
82:         whenProvingNotPaused
83:     {
```

- *AssignmentHook.sol* ( [62-71](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L62-L71) ):

```solidity
/// @audit _data
62:     function onBlockProposed(
63:         TaikoData.Block memory _blk,
64:         TaikoData.BlockMetadata memory _meta,
65:         bytes memory _data
66:     )
67:         external
68:         payable
69:         nonReentrant
70:         onlyFromNamed("taiko")
71:     {
```

- *CrossChainOwned.sol* ( [36-41](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L36-L41) ):

```solidity
/// @audit _data
36:     function onMessageInvocation(bytes calldata _data)
37:         external
38:         payable
39:         whenNotPaused
40:         onlyFromNamed("bridge")
41:     {
```

- *Bridge.sol* ( [155-163](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L155-L163), [217-225](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L217-L225) ):

```solidity
/// @audit _proof
155:     function recallMessage(
156:         Message calldata _message,
157:         bytes calldata _proof
158:     )
159:         external
160:         nonReentrant
161:         whenNotPaused
162:         sameChain(_message.srcChainId)
163:     {

/// @audit _proof
217:     function processMessage(
218:         Message calldata _message,
219:         bytes calldata _proof
220:     )
221:         external
222:         nonReentrant
223:         whenNotPaused
224:         sameChain(_message.destChainId)
225:     {
```

- *SignalService.sol* ( [83-93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L83-L93) ):

```solidity
/// @audit _proof
83:     function proveSignalReceived(
84:         uint64 _chainId,
85:         address _app,
86:         bytes32 _signal,
87:         bytes calldata _proof
88:     )
89:         public
90:         virtual
91:         validSender(_app)
92:         nonZeroValue(_signal)
93:     {
```

- *TimelockTokenPool.sol* ( [168-168](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L168-L168) ):

```solidity
/// @audit _sig
168:     function withdraw(address _to, bytes memory _sig) external {
```

- *ERC20Airdrop.sol* ( [50-58](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L50-L58) ):

```solidity
/// @audit delegationData
50:     function claimAndDelegate(
51:         address user,
52:         uint256 amount,
53:         bytes32[] calldata proof,
54:         bytes calldata delegationData
55:     )
56:         external
57:         nonReentrant
58:     {
```

- *ERC1155Vault.sol* ( [93-93](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L93-L93) ):

```solidity
/// @audit data
93:     function onMessageInvocation(bytes calldata data) external payable nonReentrant whenNotPaused {
```

- *ERC20Vault.sol* ( [253-258](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L253-L258) ):

```solidity
/// @audit _data
253:     function onMessageInvocation(bytes calldata _data)
254:         external
255:         payable
256:         nonReentrant
257:         whenNotPaused
258:     {
```

- *ERC721Vault.sol* ( [77-82](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L77-L82) ):

```solidity
/// @audit _data
77:     function onMessageInvocation(bytes calldata _data)
78:         external
79:         payable
80:         nonReentrant
81:         whenNotPaused
82:     {
```

</details>

### [N-78] Don't define functions with the same name in a contract

In Solidity, while function overriding allows for functions with the same name to coexist, it is advisable to avoid this practice to enhance code readability and maintainability. Having multiple functions with the same name, even with different parameters or in inherited contracts, can cause confusion and increase the likelihood of errors during development, testing, and debugging. Using distinct and descriptive function names not only clarifies the purpose and behavior of each function, but also helps prevent unintended function calls or incorrect overriding. By adopting a clear and consistent naming convention, developers can create more comprehensible and maintainable smart contracts.

<details>
<summary>There are 14 instances (click to show):</summary>

- *TaikoGovernor.sol* ( [69](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L69) ):

```solidity
/// @audit Different function with same name found on line 48
69:     function propose(
```

- *Guardians.sol* ( [128](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L128) ):

```solidity
/// @audit Different function with same name found on line 101
128:     function isApproved(uint256 _approvalBits) internal view returns (bool) {
```

- *BytesUtils.sol* ( [56](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L56), [138](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L138), [160](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L160), [178](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L178) ):

```solidity
/// @audit Different function with same name found on line 39
56:     function compare(

/// @audit Different function with same name found on line 116
138:     function equals(

/// @audit Different function with same name found on line 116
160:     function equals(

/// @audit Different function with same name found on line 116
178:     function equals(bytes memory self, bytes memory other) internal pure returns (bool) {
```

- *AddressResolver.sol* ( [43](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L43) ):

```solidity
/// @audit Different function with same name found on line 30
43:     function resolve(
```

- *EssentialContract.sol* ( [109](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L109) ):

```solidity
/// @audit Different function with same name found on line 95
109:     function __Essential_init(address _owner) internal virtual {
```

- *IAddressResolver.sol* ( [34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/IAddressResolver.sol#L34) ):

```solidity
/// @audit Different function with same name found on line 19
34:     function resolve(
```

- *LibAddress.sol* ( [42](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L42) ):

```solidity
/// @audit Different function with same name found on line 22
42:     function sendEther(address _to, uint256 _amount) internal {
```

- *TimelockTokenPool.sol* ( [168](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L168) ):

```solidity
/// @audit Different function with same name found on line 161
168:     function withdraw(address _to, bytes memory _sig) external {
```

- *Bytes.sol* ( [91](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L91) ):

```solidity
/// @audit Different function with same name found on line 15
91:     function slice(bytes memory _bytes, uint256 _start) internal pure returns (bytes memory) {
```

- *RLPReader.sol* ( [102](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L102), [128](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L128) ):

```solidity
/// @audit Different function with same name found on line 53
102:     function readList(bytes memory _in) internal pure returns (RLPItem[] memory out_) {

/// @audit Different function with same name found on line 109
128:     function readBytes(bytes memory _in) internal pure returns (bytes memory out_) {
```

</details>

### [N-79] Interface files should not use fixed compiler versions

Interfaces should not use fixed compiler versions, since they may be used by projects using a different version.

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

### [N-80] Addresses shouldn't be hard-coded

It is often better to declare `address`es as `constant` or `immutable` which can be assigned in constructor. This allows the code to remain the same across deployments on different networks, and avoids recompilation when addresses need to change.

There are 2 instances:

- *TaikoL2.sol* ( [32](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L32) ):

```solidity
32:     address public constant GOLDEN_TOUCH_ADDRESS = 0x0000777735367b36bC9B61C50022d9D0700dB4Ec;
```

- *SHA1.sol* ( [182](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SHA1.sol#L182) ):

```solidity
182:                                     and(div(h, 0x100000000), 0xFFFFFFFF00000000000000000000000000000000),
```

### [N-81] Assembly block creates dirty bits

Writing data to the free memory pointer without later updating the free memory pointer will cause there to be dirty bits at that memory location. Not updating the free memory pointer will make it [harder](https://docs.soliditylang.org/en/latest/ir-breaking-changes.html#cleanup) for the optimizer to reason about whether the memory needs to be cleaned before use, which will lead to worse optimizations. Update the free memory pointer and annotate the block (`assembly ("memory-safe") { ... }`) to avoid this issue.

<details>
<summary>There are 5 instances (click to show):</summary>

- *SHA1.sol* ( [12-193](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SHA1.sol#L12-L193) ):

```solidity
12:         assembly {
13:             // Get a safe scratch location
14:             let scratch := mload(0x40)
15: 
16:             // Get the data length, and point data at the first byte
17:             let len := mload(data)
18:             data := add(data, 32)
19: 
20:             // Find the length after padding
21:             let totallen := add(and(add(len, 1), 0xFFFFFFFFFFFFFFC0), 64)
22:             switch lt(sub(totallen, len), 9)
23:             case 1 { totallen := add(totallen, 64) }
24: 
25:             let h := 0x6745230100EFCDAB890098BADCFE001032547600C3D2E1F0
26: 
27:             function readword(ptr, off, count) -> result {
28:                 result := 0
29:                 if lt(off, count) {
30:                     result := mload(add(ptr, off))
31:                     count := sub(count, off)
32:                     if lt(count, 32) {
33:                         let mask := not(sub(exp(256, sub(32, count)), 1))
34:                         result := and(result, mask)
35:                     }
36:                 }
...... OMITTED ......
169:                                 0x100000000000000000000
170:                             )
171:                         )
172:                 }
173: 
174:                 h := and(add(h, x), 0xFFFFFFFF00FFFFFFFF00FFFFFFFF00FFFFFFFF00FFFFFFFF)
175:             }
176:             ret :=
177:                 mul(
178:                     or(
179:                         or(
180:                             or(
181:                                 or(
182:                                     and(div(h, 0x100000000), 0xFFFFFFFF00000000000000000000000000000000),
183:                                     and(div(h, 0x1000000), 0xFFFFFFFF000000000000000000000000)
184:                                 ),
185:                                 and(div(h, 0x10000), 0xFFFFFFFF0000000000000000)
186:                             ),
187:                             and(div(h, 0x100), 0xFFFFFFFF00000000)
188:                         ),
189:                         and(h, 0xFFFFFFFF)
190:                     ),
191:                     0x1000000000000000000000000
192:                 )
193:         }
```

- *Bytes.sol* ( [32-81](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L32-L81), [34-70](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L34-L70), [72-80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L72-L80), [104-141](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L104-L141) ):

```solidity
32:         assembly {
33:             switch iszero(_length)
34:             case 0 {
35:                 // Get a location of some free memory and store it in tempBytes as
36:                 // Solidity does for memory variables.
37:                 tempBytes := mload(0x40)
38: 
39:                 // The first word of the slice result is potentially a partial
40:                 // word read from the original array. To read it, we calculate
41:                 // the length of that partial word and start copying that many
42:                 // bytes into the array. The first word we copy will start with
43:                 // data we don't care about, but the last `lengthmod` bytes will
44:                 // land at the beginning of the contents of the new array. When
45:                 // we're done copying, we overwrite the full first word with
46:                 // the actual length of the slice.
47:                 let lengthmod := and(_length, 31)
48: 
49:                 // The multiplication in the next line is necessary
50:                 // because when slicing multiples of 32 bytes (lengthmod == 0)
51:                 // the following copy loop was copying the origin's length
52:                 // and then ending prematurely not copying everything it should.
53:                 let mc := add(add(tempBytes, lengthmod), mul(0x20, iszero(lengthmod)))
54:                 let end := add(mc, _length)
55: 
56:                 for {
57:                     // The multiplication in the next line has the same exact purpose
58:                     // as the one above.
59:                     let cc := add(add(add(_bytes, lengthmod), mul(0x20, iszero(lengthmod))), _start)
60:                 } lt(mc, end) {
61:                     mc := add(mc, 0x20)
62:                     cc := add(cc, 0x20)
63:                 } { mstore(mc, mload(cc)) }
64: 
65:                 mstore(tempBytes, _length)
66: 
67:                 //update free-memory pointer
68:                 //allocating the array padded to 32 bytes like the compiler does now
69:                 mstore(0x40, and(add(mc, 31), not(31)))
70:             }
71:             //if we want a zero-length slice let's just return a zero-length array
72:             default {
73:                 tempBytes := mload(0x40)
74: 
75:                 //zero out the 32 bytes slice we are about to return
76:                 //we need to do it because Solidity does not garbage collect
77:                 mstore(tempBytes, 0)
78: 
79:                 mstore(0x40, add(tempBytes, 0x20))
80:             }
81:         }

34:             case 0 {
35:                 // Get a location of some free memory and store it in tempBytes as
36:                 // Solidity does for memory variables.
37:                 tempBytes := mload(0x40)
38: 
39:                 // The first word of the slice result is potentially a partial
40:                 // word read from the original array. To read it, we calculate
41:                 // the length of that partial word and start copying that many
42:                 // bytes into the array. The first word we copy will start with
43:                 // data we don't care about, but the last `lengthmod` bytes will
44:                 // land at the beginning of the contents of the new array. When
45:                 // we're done copying, we overwrite the full first word with
46:                 // the actual length of the slice.
47:                 let lengthmod := and(_length, 31)
48: 
49:                 // The multiplication in the next line is necessary
50:                 // because when slicing multiples of 32 bytes (lengthmod == 0)
51:                 // the following copy loop was copying the origin's length
52:                 // and then ending prematurely not copying everything it should.
53:                 let mc := add(add(tempBytes, lengthmod), mul(0x20, iszero(lengthmod)))
54:                 let end := add(mc, _length)
55: 
56:                 for {
57:                     // The multiplication in the next line has the same exact purpose
58:                     // as the one above.
59:                     let cc := add(add(add(_bytes, lengthmod), mul(0x20, iszero(lengthmod))), _start)
60:                 } lt(mc, end) {
61:                     mc := add(mc, 0x20)
62:                     cc := add(cc, 0x20)
63:                 } { mstore(mc, mload(cc)) }
64: 
65:                 mstore(tempBytes, _length)
66: 
67:                 //update free-memory pointer
68:                 //allocating the array padded to 32 bytes like the compiler does now
69:                 mstore(0x40, and(add(mc, 31), not(31)))
70:             }

72:             default {
73:                 tempBytes := mload(0x40)
74: 
75:                 //zero out the 32 bytes slice we are about to return
76:                 //we need to do it because Solidity does not garbage collect
77:                 mstore(tempBytes, 0)
78: 
79:                 mstore(0x40, add(tempBytes, 0x20))
80:             }

104:         assembly {
105:             // Grab a free memory offset for the new array
106:             _nibbles := mload(0x40)
107: 
108:             // Load the length of the passed bytes array from memory
109:             let bytesLength := mload(_bytes)
110: 
111:             // Calculate the length of the new nibble array
112:             // This is the length of the input array times 2
113:             let nibblesLength := shl(0x01, bytesLength)
114: 
115:             // Update the free memory pointer to allocate memory for the new array.
116:             // To do this, we add the length of the new array + 32 bytes for the array length
117:             // rounded up to the nearest 32 byte boundary to the current free memory pointer.
118:             mstore(0x40, add(_nibbles, and(not(0x1F), add(nibblesLength, 0x3F))))
119: 
120:             // Store the length of the new array in memory
121:             mstore(_nibbles, nibblesLength)
122: 
123:             // Store the memory offset of the _bytes array's contents on the stack
124:             let bytesStart := add(_bytes, 0x20)
125: 
126:             // Store the memory offset of the nibbles array's contents on the stack
127:             let nibblesStart := add(_nibbles, 0x20)
128: 
129:             // Loop through each byte in the input array
130:             for { let i := 0x00 } lt(i, bytesLength) { i := add(i, 0x01) } {
131:                 // Get the starting offset of the next 2 bytes in the nibbles array
132:                 let offset := add(nibblesStart, shl(0x01, i))
133:                 // Load the byte at the current index within the `_bytes` array
134:                 let b := byte(0x00, mload(add(bytesStart, i)))
135: 
136:                 // Pull out the first nibble and store it in the new array
137:                 mstore8(offset, shr(0x04, b))
138:                 // Pull out the second nibble and store it in the new array
139:                 mstore8(add(offset, 0x01), and(b, 0x0F))
140:             }
141:         }
```

</details>

### [N-82] Multiple mappings with same keys can be combined into a single struct mapping for readability

Well-organized data structures make code reviews easier, which may lead to fewer bugs. Consider combining related mappings into mappings to structs, so it's clear what data is related.

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

### [N-83] Control structures do not follow the Solidity Style Guide

Refer to the [Solidity style guide - Control Structures](https://docs.soliditylang.org/en/v0.8.20/style-guide.html#control-structures).

<details>
<summary>There are 362 instances (click to show):</summary>

- *TaikoL1.sol* ( [29-29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L29-L29), [35-35](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L35-L35), [42-49](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L42-L49), [55-64](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L55-L64), [75-83](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L75-L83), [90-90](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L90-L90), [100-105](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L100-L105), [145-149](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L145-L149), [162-169](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L162-L169), [176-180](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L176-L180), [220-226](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L220-L226) ):

```solidity
29:         if (state.slotB.provingPaused) revert L1_PROVING_PAUSED();

35:         if (!_inNonReentrant()) revert L1_RECEIVE_DISABLED();

42:     function init(
43:         address _owner,
44:         address _addressManager,
45:         bytes32 _genesisBlockHash
46:     )
47:         external
48:         initializer
49:     {

55:     function proposeBlock(
56:         bytes calldata _params,
57:         bytes calldata _txList
58:     )
59:         external
60:         payable
61:         nonReentrant
62:         whenNotPaused
63:         returns (TaikoData.BlockMetadata memory meta_, TaikoData.EthDeposit[] memory deposits_)
64:     {

75:     function proveBlock(
76:         uint64 _blockId,
77:         bytes calldata _input
78:     )
79:         external
80:         nonReentrant
81:         whenNotPaused
82:         whenProvingNotPaused
83:     {

90:         if (_blockId != meta.id) revert L1_INVALID_BLOCK_ID();

100:     function verifyBlocks(uint64 _maxBlocksToVerify)
101:         external
102:         nonReentrant
103:         whenNotPaused
104:         whenProvingNotPaused
105:     {

145:     function getBlock(uint64 _blockId)
146:         public
147:         view
148:         returns (TaikoData.Block memory blk_, TaikoData.TransitionState memory ts_)
149:     {

162:     function getTransition(
163:         uint64 _blockId,
164:         bytes32 _parentHash
165:     )
166:         public
167:         view
168:         returns (TaikoData.TransitionState memory)
169:     {

176:     function getStateVariables()
177:         public
178:         view
179:         returns (TaikoData.SlotA memory a_, TaikoData.SlotB memory b_)
180:     {

220:     function _authorizePause(address)
221:         internal
222:         view
223:         virtual
224:         override
225:         onlyFromOwnerOrNamed("chain_pauser")
226:     { }
```

- *TaikoToken.sol* ( [25-33](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L25-L33), [61-61](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L61-L61), [70-78](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L70-L78), [79-79](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L79-L79), [83-90](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L83-L90), [94-101](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L94-L101), [105-111](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L105-L111), [115-121](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L115-L121) ):

```solidity
25:     function init(
26:         address _owner,
27:         string calldata _name,
28:         string calldata _symbol,
29:         address _recipient
30:     )
31:         public
32:         initializer
33:     {

61:         if (_to == address(this)) revert TKO_INVALID_ADDR();

70:     function transferFrom(
71:         address _from,
72:         address _to,
73:         uint256 _amount
74:     )
75:         public
76:         override
77:         returns (bool)
78:     {

79:         if (_to == address(this)) revert TKO_INVALID_ADDR();

83:     function _beforeTokenTransfer(
84:         address _from,
85:         address _to,
86:         uint256 _amount
87:     )
88:         internal
89:         override(ERC20Upgradeable, ERC20SnapshotUpgradeable)
90:     {

94:     function _afterTokenTransfer(
95:         address _from,
96:         address _to,
97:         uint256 _amount
98:     )
99:         internal
100:         override(ERC20Upgradeable, ERC20VotesUpgradeable)
101:     {

105:     function _mint(
106:         address _to,
107:         uint256 _amount
108:     )
109:         internal
110:         override(ERC20Upgradeable, ERC20VotesUpgradeable)
111:     {

115:     function _burn(
116:         address _from,
117:         uint256 _amount
118:     )
119:         internal
120:         override(ERC20Upgradeable, ERC20VotesUpgradeable)
121:     {
```

- *TaikoGovernor.sol* ( [16-22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L16-L22), [31-38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L31-L38), [48-57](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L48-L57), [69-80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L69-L80), [81-81](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L81-L81), [89-94](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L89-L94), [99-104](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L99-L104), [127-136](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L127-L136), [140-149](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L140-L149), [153-158](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L153-L158) ):

```solidity
16: contract TaikoGovernor is
17:     EssentialContract,
18:     GovernorCompatibilityBravoUpgradeable,
19:     GovernorVotesUpgradeable,
20:     GovernorVotesQuorumFractionUpgradeable,
21:     GovernorTimelockControlUpgradeable
22: {

31:     function init(
32:         address _owner,
33:         IVotesUpgradeable _token,
34:         TimelockControllerUpgradeable _timelock
35:     )
36:         external
37:         initializer
38:     {

48:     function propose(
49:         address[] memory _targets,
50:         uint256[] memory _values,
51:         bytes[] memory _calldatas,
52:         string memory _description
53:     )
54:         public
55:         override(IGovernorUpgradeable, GovernorUpgradeable, GovernorCompatibilityBravoUpgradeable)
56:         returns (uint256)
57:     {

69:     function propose(
70:         address[] memory _targets,
71:         uint256[] memory _values,
72:         string[] memory _signatures,
73:         bytes[] memory _calldatas,
74:         string memory _description
75:     )
76:         public
77:         virtual
78:         override(GovernorCompatibilityBravoUpgradeable)
79:         returns (uint256)
80:     {

81:         if (_signatures.length != _calldatas.length) revert TG_INVALID_SIGNATURES_LENGTH();

89:     function supportsInterface(bytes4 _interfaceId)
90:         public
91:         view
92:         override(GovernorUpgradeable, GovernorTimelockControlUpgradeable, IERC165Upgradeable)
93:         returns (bool)
94:     {

99:     function state(uint256 _proposalId)
100:         public
101:         view
102:         override(IGovernorUpgradeable, GovernorUpgradeable, GovernorTimelockControlUpgradeable)
103:         returns (ProposalState)
104:     {

127:     function _execute(
128:         uint256 _proposalId,
129:         address[] memory _targets,
130:         uint256[] memory _values,
131:         bytes[] memory _calldatas,
132:         bytes32 _descriptionHash
133:     )
134:         internal
135:         override(GovernorUpgradeable, GovernorTimelockControlUpgradeable)
136:     {

140:     function _cancel(
141:         address[] memory _targets,
142:         uint256[] memory _values,
143:         bytes[] memory _calldatas,
144:         bytes32 _descriptionHash
145:     )
146:         internal
147:         override(GovernorUpgradeable, GovernorTimelockControlUpgradeable)
148:         returns (uint256)
149:     {

153:     function _executor()
154:         internal
155:         view
156:         override(GovernorUpgradeable, GovernorTimelockControlUpgradeable)
157:         returns (address)
158:     {
```

- *AssignmentHook.sol* ( [62-71](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L62-L71), [81-81](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L81-L81), [137-145](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L137-L145), [164-171](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L164-L171), [173-173](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L173-L173) ):

```solidity
62:     function onBlockProposed(
63:         TaikoData.Block memory _blk,
64:         TaikoData.BlockMetadata memory _meta,
65:         bytes memory _data
66:     )
67:         external
68:         payable
69:         nonReentrant
70:         onlyFromNamed("taiko")
71:     {

81:         if (

137:     function hashAssignment(
138:         ProverAssignment memory _assignment,
139:         address _taikoL1Address,
140:         bytes32 _blobHash
141:     )
142:         public
143:         view
144:         returns (bytes32)
145:     {

164:     function _getProverFee(
165:         TaikoData.TierFee[] memory _tierFees,
166:         uint16 _tierId
167:     )
168:         private
169:         pure
170:         returns (uint256)
171:     {

173:             if (_tierFees[i].tier == _tierId) return _tierFees[i].fee;
```

- *LibDepositing.sol* ( [29-36](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L29-L36), [67-74](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L67-L74), [122-130](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L122-L130), [150-150](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L150-L150) ):

```solidity
29:     function depositEtherToL2(
30:         TaikoData.State storage _state,
31:         TaikoData.Config memory _config,
32:         IAddressResolver _resolver,
33:         address _recipient
34:     )
35:         internal
36:     {

67:     function processDeposits(
68:         TaikoData.State storage _state,
69:         TaikoData.Config memory _config,
70:         address _feeRecipient
71:     )
72:         internal
73:         returns (TaikoData.EthDeposit[] memory deposits_)
74:     {

122:     function canDepositEthToL2(
123:         TaikoData.State storage _state,
124:         TaikoData.Config memory _config,
125:         uint256 _amount
126:     )
127:         internal
128:         view
129:         returns (bool)
130:     {

150:         if (_amount > type(uint96).max) revert L1_INVALID_ETH_DEPOSIT();
```

- *LibProposing.sol* ( [68-77](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L68-L77), [94-94](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L94-L94), [142-142](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L142-L142), [145-145](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L145-L145), [159-159](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L159-L159), [182-182](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L182-L182), [287-295](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L287-L295), [299-306](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L299-L306) ):

```solidity
68:     function proposeBlock(
69:         TaikoData.State storage _state,
70:         TaikoData.Config memory _config,
71:         IAddressResolver _resolver,
72:         bytes calldata _data,
73:         bytes calldata _txList
74:     )
75:         internal
76:         returns (TaikoData.BlockMetadata memory meta_, TaikoData.EthDeposit[] memory deposits_)
77:     {

94:         if (!_isProposerPermitted(b, _resolver)) revert L1_UNAUTHORIZED();

142:             if (!_config.blobAllowedForDA) revert L1_BLOB_FOR_DA_DISABLED();

145:                 if (!_config.blobReuseEnabled) revert L1_BLOB_REUSE_DISABLED();

159:                 if (meta_.blobHash == 0) revert L1_BLOB_NOT_FOUND();

182:             if (!LibAddress.isSenderEOA()) revert L1_PROPOSER_NOT_EOA();

287:     function isBlobReusable(
288:         TaikoData.State storage _state,
289:         TaikoData.Config memory _config,
290:         bytes32 _blobHash
291:     )
292:         internal
293:         view
294:         returns (bool)
295:     {

299:     function _isProposerPermitted(
300:         TaikoData.SlotB memory _slotB,
301:         IAddressResolver _resolver
302:     )
303:         private
304:         view
305:         returns (bool)
306:     {
```

- *LibProving.sol* ( [74-74](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L74-L74), [91-101](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L91-L101), [219-219](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L219-L219), [239-239](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L239-L239), [269-277](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L269-L277), [350-359](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L350-L359), [374-374](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L374-L374), [401-410](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L401-L410), [412-412](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L412-L412), [420-420](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L420-L420), [424-424](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L424-L424) ):

```solidity
74:         if (_state.slotB.provingPaused == _pause) revert L1_INVALID_PAUSE_STATUS();

91:     function proveBlock(
92:         TaikoData.State storage _state,
93:         TaikoData.Config memory _config,
94:         IAddressResolver _resolver,
95:         TaikoData.BlockMetadata memory _meta,
96:         TaikoData.Transition memory _tran,
97:         TaikoData.TierProof memory _proof
98:     )
99:         internal
100:         returns (uint8 maxBlocksToVerify_)
101:     {

219:             if (sameTransition) revert L1_ALREADY_PROVED();

239:                 if (ts.contester != address(0)) revert L1_ALREADY_CONTESTED();

269:     function _createTransition(
270:         TaikoData.State storage _state,
271:         TaikoData.Block storage _blk,
272:         TaikoData.Transition memory _tran,
273:         uint64 slot
274:     )
275:         private
276:         returns (uint32 tid_, TaikoData.TransitionState storage ts_)
277:     {

350:     function _overrideWithHigherProof(
351:         TaikoData.TransitionState storage _ts,
352:         TaikoData.Transition memory _tran,
353:         TaikoData.TierProof memory _proof,
354:         ITierProvider.Tier memory _tier,
355:         IERC20 _tko,
356:         bool _sameTransition
357:     )
358:         private
359:     {

374:             if (_sameTransition) revert L1_ALREADY_PROVED();

401:     function _checkProverPermission(
402:         TaikoData.State storage _state,
403:         TaikoData.Block storage _blk,
404:         TaikoData.TransitionState storage _ts,
405:         uint32 _tid,
406:         ITierProvider.Tier memory _tier
407:     )
408:         private
409:         view
410:     {

412:         if (_tier.contestBond == 0) return;

420:             if (!isAssignedPover) revert L1_NOT_ASSIGNED_PROVER();

424:             if (isAssignedPover) revert L1_ASSIGNED_PROVER_NOT_ALLOWED();
```

- *LibUtils.sol* ( [23-32](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L23-L32), [40-40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L40-L40), [43-43](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L43-L43), [52-60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L52-L60), [70-79](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L70-L79), [86-86](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L86-L86) ):

```solidity
23:     function getTransition(
24:         TaikoData.State storage _state,
25:         TaikoData.Config memory _config,
26:         uint64 _blockId,
27:         bytes32 _parentHash
28:     )
29:         external
30:         view
31:         returns (TaikoData.TransitionState storage)
32:     {

40:         if (blk.blockId != _blockId) revert L1_BLOCK_MISMATCH();

43:         if (tid == 0) revert L1_TRANSITION_NOT_FOUND();

52:     function getBlock(
53:         TaikoData.State storage _state,
54:         TaikoData.Config memory _config,
55:         uint64 _blockId
56:     )
57:         external
58:         view
59:         returns (TaikoData.Block storage blk_, uint64 slot_)
60:     {

70:     function getTransitionId(
71:         TaikoData.State storage _state,
72:         TaikoData.Block storage _blk,
73:         uint64 _slot,
74:         bytes32 _parentHash
75:     )
76:         internal
77:         view
78:         returns (uint32 tid_)
79:     {

86:         if (tid_ >= _blk.nextTransitionId) revert L1_UNEXPECTED_TRANSITION_ID();
```

- *LibVerifying.sol* ( [47-53](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L47-L53), [54-54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L54-L54), [85-92](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L85-L92), [105-105](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L105-L105), [111-111](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L111-L111), [131-131](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L131-L131), [137-137](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L137-L137), [151-151](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L151-L151), [224-231](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L224-L231), [246-246](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L246-L246) ):

```solidity
47:     function init(
48:         TaikoData.State storage _state,
49:         TaikoData.Config memory _config,
50:         bytes32 _genesisBlockHash
51:     )
52:         external
53:     {

54:         if (!_isConfigValid(_config)) revert L1_INVALID_CONFIG();

85:     function verifyBlocks(
86:         TaikoData.State storage _state,
87:         TaikoData.Config memory _config,
88:         IAddressResolver _resolver,
89:         uint64 _maxBlocksToVerify
90:     )
91:         internal
92:     {

105:         if (blk.blockId != blockId) revert L1_BLOCK_MISMATCH();

111:         if (tid == 0) revert L1_TRANSITION_ID_ZERO();

131:                 if (blk.blockId != blockId) revert L1_BLOCK_MISMATCH();

137:                 if (tid == 0) break;

151:                     if (

224:     function _syncChainData(
225:         TaikoData.Config memory _config,
226:         IAddressResolver _resolver,
227:         uint64 _lastVerifiedBlockId,
228:         bytes32 _stateRoot
229:     )
230:         private
231:     {

246:         if (
```

- *GuardianProver.sol* ( [35-44](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/GuardianProver.sol#L35-L44), [45-45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/GuardianProver.sol#L45-L45) ):

```solidity
35:     function approve(
36:         TaikoData.BlockMetadata calldata _meta,
37:         TaikoData.Transition calldata _tran,
38:         TaikoData.TierProof calldata _proof
39:     )
40:         external
41:         whenNotPaused
42:         nonReentrant
43:         returns (bool approved_)
44:     {

45:         if (_proof.tier != LibTiers.TIER_GUARDIAN) revert INVALID_PROOF();
```

- *Guardians.sol* ( [53-60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L53-L60), [68-68](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L68-L68), [82-82](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L82-L82), [84-84](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L84-L84), [113-113](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L113-L113), [134-134](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L134-L134), [135-135](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L135-L135) ):

```solidity
53:     function setGuardians(
54:         address[] memory _newGuardians,
55:         uint8 _minGuardians
56:     )
57:         external
58:         onlyOwner
59:         nonReentrant
60:     {

68:         if (_minGuardians < (_newGuardians.length + 1) >> 1 || _minGuardians > _newGuardians.length)

82:             if (guardian == address(0)) revert INVALID_GUARDIAN();

84:             if (guardianIds[guardian] != 0) revert INVALID_GUARDIAN_SET();

113:         if (id == 0) revert INVALID_GUARDIAN();

134:                 if (bits & 1 == 1) ++count;

135:                 if (count == minGuardians) return true;
```

- *MainnetTierProvider.sol* ( [68-68](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L68-L68), [69-69](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L69-L69) ):

```solidity
68:         if (_rand % 1000 == 0) return LibTiers.TIER_SGX_ZKVM;

69:         else return LibTiers.TIER_SGX;
```

- *TestnetTierProvider.sol* ( [68-68](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L68-L68) ):

```solidity
68:         if (_rand % 10 == 0) return LibTiers.TIER_SGX;
```

- *CrossChainOwned.sol* ( [36-41](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L36-L41), [43-43](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L43-L43), [51-51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L51-L51), [60-68](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L60-L68) ):

```solidity
36:     function onMessageInvocation(bytes calldata _data)
37:         external
38:         payable
39:         whenNotPaused
40:         onlyFromNamed("bridge")
41:     {

43:         if (txId != nextTxId) revert XCO_INVALID_TX_ID();

51:         if (!success) revert XCO_TX_REVERTED();

60:     function __CrossChainOwned_init(
61:         address _owner,
62:         address _addressManager,
63:         uint64 _ownerChainId
64:     )
65:         internal
66:         virtual
67:         onlyInitializing
68:     {
```

- *Lib1559Math.sol* ( [16-23](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/Lib1559Math.sol#L16-L23), [33-40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/Lib1559Math.sol#L33-L40) ):

```solidity
16:     function basefee(
17:         uint256 _gasExcess,
18:         uint256 _adjustmentFactor
19:     )
20:         internal
21:         pure
22:         returns (uint256)
23:     {

33:     function _ethQty(
34:         uint256 _gasExcess,
35:         uint256 _adjustmentFactor
36:     )
37:         private
38:         pure
39:         returns (uint256)
40:     {
```

- *TaikoL2.sol* ( [71-79](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L71-L79), [107-115](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L107-L115), [116-116](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L116-L116), [123-123](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L123-L123), [163-171](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L163-L171), [172-172](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L172-L172), [185-192](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L185-L192), [201-201](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L201-L201), [202-202](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L202-L202), [223-227](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L223-L227), [252-260](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L252-L260), [296-296](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L296-L296) ):

```solidity
71:     function init(
72:         address _owner,
73:         address _addressManager,
74:         uint64 _l1ChainId,
75:         uint64 _gasExcess
76:     )
77:         external
78:         initializer
79:     {

107:     function anchor(
108:         bytes32 _l1BlockHash,
109:         bytes32 _l1StateRoot,
110:         uint64 _l1BlockId,
111:         uint32 _parentGasUsed
112:     )
113:         external
114:         nonReentrant
115:     {

116:         if (

123:         if (msg.sender != GOLDEN_TOUCH_ADDRESS) revert L2_INVALID_SENDER();

163:     function withdraw(
164:         address _token,
165:         address _to
166:     )
167:         external
168:         onlyFromOwnerOrNamed("withdrawer")
169:         nonReentrant
170:         whenNotPaused
171:     {

172:         if (_to == address(0)) revert L2_INVALID_PARAM();

185:     function getBasefee(
186:         uint64 _l1BlockId,
187:         uint32 _parentGasUsed
188:     )
189:         public
190:         view
191:         returns (uint256 basefee_)
192:     {

201:         if (_blockId >= block.number) return 0;

202:         if (_blockId + 256 >= block.number) return blockhash(_blockId);

223:     function _calcPublicInputHash(uint256 _blockId)
224:         private
225:         view
226:         returns (bytes32 publicInputHashOld, bytes32 publicInputHashNew)
227:     {

252:     function _calc1559BaseFee(
253:         Config memory _config,
254:         uint64 _l1BlockId,
255:         uint32 _parentGasUsed
256:     )
257:         private
258:         view
259:         returns (uint256 basefee_, uint64 gasExcess_)
260:     {

296:         if (basefee_ == 0) basefee_ = 1;
```

- *TaikoL2EIP1559Configurable.sol* ( [25-32](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L25-L32), [33-33](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L33-L33), [34-34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L34-L34) ):

```solidity
25:     function setConfigAndExcess(
26:         Config memory _newConfig,
27:         uint64 _newGasExcess
28:     )
29:         external
30:         virtual
31:         onlyOwner
32:     {

33:         if (_newConfig.gasTargetPerL1Block == 0) revert L2_INVALID_CONFIG();

34:         if (_newConfig.basefeeAdjustmentQuotient == 0) revert L2_INVALID_CONFIG();
```

- *AutomataDcapV3Attestation.sol* ( [73-79](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L73-L79), [88-94](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L88-L94), [103-109](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L103-L109), [114-117](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L114-L117), [126-131](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L126-L131), [175-179](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L175-L179), [206-213](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L206-L213), [229-236](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L229-L236), [248-252](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L248-L252), [303-312](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L303-L312), [355-360](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L355-L360), [364-368](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L364-L368), [406-406](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L406-L406) ):

```solidity
73:     function addRevokedCertSerialNum(
74:         uint256 index,
75:         bytes[] calldata serialNumBatch
76:     )
77:         external
78:         onlyOwner
79:     {

88:     function removeRevokedCertSerialNum(
89:         uint256 index,
90:         bytes[] calldata serialNumBatch
91:     )
92:         external
93:         onlyOwner
94:     {

103:     function configureTcbInfoJson(
104:         string calldata fmspc,
105:         TCBInfoStruct.TCBInfo calldata tcbInfoInput
106:     )
107:         public
108:         onlyOwner
109:     {

114:     function configureQeIdentityJson(EnclaveIdStruct.EnclaveId calldata qeIdentityInput)
115:         external
116:         onlyOwner
117:     {

126:     function _attestationTcbIsValid(TCBInfoStruct.TCBStatus status)
127:         internal
128:         pure
129:         virtual
130:         returns (bool valid)
131:     {

175:     function _verifyQEReportWithIdentity(V3Struct.EnclaveReport memory quoteEnclaveReport)
176:         private
177:         view
178:         returns (bool, EnclaveIdStruct.EnclaveIdStatus status)
179:     {

206:     function _checkTcbLevels(
207:         IPEMCertChainLib.PCKCertificateField memory pck,
208:         TCBInfoStruct.TCBInfo memory tcb
209:     )
210:         private
211:         pure
212:         returns (bool, TCBInfoStruct.TCBStatus status)
213:     {

229:     function _isCpuSvnHigherOrGreater(
230:         uint256[] memory pckCpuSvns,
231:         uint8[] memory tcbCpuSvns
232:     )
233:         private
234:         pure
235:         returns (bool)
236:     {

248:     function _verifyCertChain(IPEMCertChainLib.ECSha256Certificate[] memory certs)
249:         private
250:         view
251:         returns (bool)
252:     {

303:     function _enclaveReportSigVerification(
304:         bytes memory pckCertPubKey,
305:         bytes memory signedQuoteData,
306:         V3Struct.ECDSAQuoteV3AuthData memory authDataV3,
307:         V3Struct.EnclaveReport memory qeEnclaveReport
308:     )
309:         private
310:         view
311:         returns (bool)
312:     {

355:     function verifyParsedQuote(V3Struct.ParsedV3QuoteStruct calldata v3quote)
356:         external
357:         view
358:         override
359:         returns (bool, bytes memory)
360:     {

364:     function _verifyParsedQuote(V3Struct.ParsedV3QuoteStruct memory v3quote)
365:         internal
366:         view
367:         returns (bool, bytes memory)
368:     {

406:             if (
```

- *PEMCertChainLib.sol* ( [40-47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L40-L47), [74-81](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L74-L81), [134-134](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L134-L134), [216-220](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L216-L220), [252-259](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L252-L259), [269-283](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L269-L283), [341-348](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L341-L348) ):

```solidity
40:     function splitCertificateChain(
41:         bytes memory pemChain,
42:         uint256 size
43:     )
44:         external
45:         pure
46:         returns (bool success, bytes[] memory certs)
47:     {

74:     function decodeCert(
75:         bytes memory der,
76:         bool isPckCert
77:     )
78:         external
79:         pure
80:         returns (bool success, ECSha256Certificate memory cert)
81:     {

134:             if (

216:     function _removeHeadersAndFooters(string memory pemData)
217:         private
218:         pure
219:         returns (bool success, bytes memory extracted, uint256 endIndex)
220:     {

252:     function _trimBytes(
253:         bytes memory input,
254:         uint256 expectedLength
255:     )
256:         private
257:         pure
258:         returns (bytes memory output)
259:     {

269:     function _findPckTcbInfo(
270:         bytes memory der,
271:         uint256 tbsPtr,
272:         uint256 tbsParentPtr
273:     )
274:         private
275:         pure
276:         returns (
277:             bool success,
278:             uint256 pcesvn,
279:             uint256[] memory cpusvns,
280:             bytes memory fmspcBytes,
281:             bytes memory pceidBytes
282:         )
283:     {

341:     function _findTcb(
342:         bytes memory der,
343:         uint256 oidPtr
344:     )
345:         private
346:         pure
347:         returns (bool success, uint256 pcesvn, uint256[] memory cpusvns)
348:     {
```

- *V3Parser.sol* ( [21-28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L21-L28), [62-72](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L62-L72), [133-137](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L133-L137), [165-169](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L165-L169), [203-210](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L203-L210), [244-248](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L244-L248), [267-274](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L267-L274) ):

```solidity
21:     function parseInput(
22:         bytes memory quote,
23:         address pemCertLibAddr
24:     )
25:         internal
26:         pure
27:         returns (bool success, V3Struct.ParsedV3QuoteStruct memory v3ParsedQuote)
28:     {

62:     function validateParsedInput(V3Struct.ParsedV3QuoteStruct memory v3Quote)
63:         internal
64:         pure
65:         returns (
66:             bool success,
67:             V3Struct.Header memory header,
68:             V3Struct.EnclaveReport memory localEnclaveReport,
69:             bytes memory signedQuoteData, // concatenation of header and local enclave report bytes
70:             V3Struct.ECDSAQuoteV3AuthData memory authDataV3
71:         )
72:     {

133:     function parseEnclaveReport(bytes memory rawEnclaveReport)
134:         internal
135:         pure
136:         returns (V3Struct.EnclaveReport memory enclaveReport)
137:     {

165:     function parseAndVerifyHeader(bytes memory rawHeader)
166:         private
167:         pure
168:         returns (bool success, V3Struct.Header memory header)
169:     {

203:     function parseAuthDataAndVerifyCertType(
204:         bytes memory rawAuthData,
205:         address pemCertLibAddr
206:     )
207:         private
208:         pure
209:         returns (bool success, V3Struct.ECDSAQuoteV3AuthData memory authDataV3)
210:     {

244:     function packQEReport(V3Struct.EnclaveReport memory enclaveReport)
245:         internal
246:         pure
247:         returns (bytes memory packedQEReport)
248:     {

267:     function parseCerificationChainBytes(
268:         bytes memory certBytes,
269:         address pemCertLibAddr
270:     )
271:         internal
272:         pure
273:         returns (bytes[3] memory certChainData)
274:     {
```

- *BytesUtils.sol* ( [16-24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L16-L24), [56-67](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L56-L67), [116-126](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L116-L126), [138-147](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L138-L147), [160-168](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L160-L168), [255-263](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L255-L263), [284-292](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L284-L292), [320-328](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L320-L328) ):

```solidity
16:     function keccak(
17:         bytes memory self,
18:         uint256 offset,
19:         uint256 len
20:     )
21:         internal
22:         pure
23:         returns (bytes32 ret)
24:     {

56:     function compare(
57:         bytes memory self,
58:         uint256 offset,
59:         uint256 len,
60:         bytes memory other,
61:         uint256 otheroffset,
62:         uint256 otherlen
63:     )
64:         internal
65:         pure
66:         returns (int256)
67:     {

116:     function equals(
117:         bytes memory self,
118:         uint256 offset,
119:         bytes memory other,
120:         uint256 otherOffset,
121:         uint256 len
122:     )
123:         internal
124:         pure
125:         returns (bool)
126:     {

138:     function equals(
139:         bytes memory self,
140:         uint256 offset,
141:         bytes memory other,
142:         uint256 otherOffset
143:     )
144:         internal
145:         pure
146:         returns (bool)
147:     {

160:     function equals(
161:         bytes memory self,
162:         uint256 offset,
163:         bytes memory other
164:     )
165:         internal
166:         pure
167:         returns (bool)
168:     {

255:     function readBytesN(
256:         bytes memory self,
257:         uint256 idx,
258:         uint256 len
259:     )
260:         internal
261:         pure
262:         returns (bytes32 ret)
263:     {

284:     function substring(
285:         bytes memory self,
286:         uint256 offset,
287:         uint256 len
288:     )
289:         internal
290:         pure
291:         returns (bytes memory)
292:     {

320:     function base32HexDecodeWord(
321:         bytes memory self,
322:         uint256 off,
323:         uint256 len
324:     )
325:         internal
326:         pure
327:         returns (bytes32)
328:     {
```

- *RsaVerify.sol* ( [43-52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L43-L52), [167-167](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L167-L167), [191-200](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L191-L200), [212-221](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L212-L221), [307-316](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L307-L316) ):

```solidity
43:     function pkcs1Sha256(
44:         bytes32 _sha256,
45:         bytes memory _s,
46:         bytes memory _e,
47:         bytes memory _m
48:     )
49:         internal
50:         view
51:         returns (bool)
52:     {

167:         if (

191:     function pkcs1Sha256Raw(
192:         bytes memory _data,
193:         bytes memory _s,
194:         bytes memory _e,
195:         bytes memory _m
196:     )
197:         internal
198:         view
199:         returns (bool)
200:     {

212:     function pkcs1Sha1(
213:         bytes20 _sha1,
214:         bytes memory _s,
215:         bytes memory _e,
216:         bytes memory _m
217:     )
218:         internal
219:         view
220:         returns (bool)
221:     {

307:     function pkcs1Sha1Raw(
308:         bytes memory _data,
309:         bytes memory _s,
310:         bytes memory _e,
311:         bytes memory _m
312:     )
313:         internal
314:         view
315:         returns (bool)
316:     {
```

- *SigVerifyLib.sol* ( [24-33](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L24-L33), [54-63](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L54-L63), [79-87](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L79-L87), [96-104](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L96-L104), [113-121](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L113-L121) ):

```solidity
24:     function verifyAttStmtSignature(
25:         bytes memory tbs,
26:         bytes memory signature,
27:         PublicKey memory publicKey,
28:         Algorithm alg
29:     )
30:         public
31:         view
32:         returns (bool)
33:     {

54:     function verifyCertificateSignature(
55:         bytes memory tbs,
56:         bytes memory signature,
57:         PublicKey memory publicKey,
58:         CertSigAlgorithm alg
59:     )
60:         public
61:         view
62:         returns (bool)
63:     {

79:     function verifyRS256Signature(
80:         bytes memory tbs,
81:         bytes memory signature,
82:         bytes memory publicKey
83:     )
84:         public
85:         view
86:         returns (bool sigValid)
87:     {

96:     function verifyRS1Signature(
97:         bytes memory tbs,
98:         bytes memory signature,
99:         bytes memory publicKey
100:     )
101:         public
102:         view
103:         returns (bool sigValid)
104:     {

113:     function verifyES256Signature(
114:         bytes memory tbs,
115:         bytes memory signature,
116:         bytes memory publicKey
117:     )
118:         public
119:         view
120:         returns (bool sigValid)
121:     {
```

- *X509DateUtils.sol* ( [18-18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L18-L18), [19-19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L19-L19), [34-45](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L34-L45), [57-57](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L57-L57), [72-72](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L72-L72), [73-73](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L73-L73), [74-74](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L74-L74) ):

```solidity
18:             if (uint8(x509Time[0]) - 48 < 5) yrs += 2000;

19:             else yrs += 1900;

34:     function toUnixTimestamp(
35:         uint16 year,
36:         uint8 month,
37:         uint8 day,
38:         uint8 hour,
39:         uint8 minute,
40:         uint8 second
41:     )
42:         internal
43:         pure
44:         returns (uint256)
45:     {

57:         if (isLeapYear(year)) monthDays[1] = 29;

72:         if (year % 4 != 0) return false;

73:         if (year % 100 != 0) return true;

74:         if (year % 400 != 0) return false;
```

- *Bridge.sol* ( [65-65](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L65-L65), [82-88](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L82-L88), [101-108](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L101-L108), [109-109](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L109-L109), [115-122](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L115-L122), [132-132](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L132-L132), [139-139](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L139-L139), [155-163](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L155-L163), [166-166](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L166-L166), [217-225](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L217-L225), [227-227](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L227-L227), [269-269](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L269-L269), [310-318](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L310-L318), [322-322](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L322-L322), [341-341](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L341-L341), [352-359](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L352-L359), [360-360](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L360-L360), [374-381](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L374-L381), [382-382](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L382-L382), [392-396](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L392-L396), [417-422](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L417-L422), [423-423](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L423-L423), [461-467](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L461-L467), [477-484](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L477-L484), [485-485](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L485-L485), [490-490](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L490-L490), [516-516](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L516-L516), [577-586](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L577-L586) ):

```solidity
65:         if (_chainId != block.chainid) revert B_INVALID_CHAINID();

82:     function suspendMessages(
83:         bytes32[] calldata _msgHashes,
84:         bool _suspend
85:     )
86:         external
87:         onlyFromOwnerOrNamed("bridge_watchdog")
88:     {

101:     function banAddress(
102:         address _addr,
103:         bool _ban
104:     )
105:         external
106:         onlyFromOwnerOrNamed("bridge_watchdog")
107:         nonReentrant
108:     {

109:         if (addressBanned[_addr] == _ban) revert B_INVALID_STATUS();

115:     function sendMessage(Message calldata _message)
116:         external
117:         payable
118:         override
119:         nonReentrant
120:         whenNotPaused
121:         returns (bytes32 msgHash_, Message memory message_)
122:     {

132:         if (!destChainEnabled) revert B_INVALID_CHAINID();

139:         if (expectedAmount != msg.value) revert B_INVALID_VALUE();

155:     function recallMessage(
156:         Message calldata _message,
157:         bytes calldata _proof
158:     )
159:         external
160:         nonReentrant
161:         whenNotPaused
162:         sameChain(_message.srcChainId)
163:     {

166:         if (messageStatus[msgHash] != Status.NEW) revert B_STATUS_MISMATCH();

217:     function processMessage(
218:         Message calldata _message,
219:         bytes calldata _proof
220:     )
221:         external
222:         nonReentrant
223:         whenNotPaused
224:         sameChain(_message.destChainId)
225:     {

227:         if (messageStatus[msgHash] != Status.NEW) revert B_STATUS_MISMATCH();

269:             if (

310:     function retryMessage(
311:         Message calldata _message,
312:         bool _isLastAttempt
313:     )
314:         external
315:         nonReentrant
316:         whenNotPaused
317:         sameChain(_message.destChainId)
318:     {

322:             if (msg.sender != _message.destOwner) revert B_PERMISSION_DENIED();

341:         if (_message.srcChainId != block.chainid) return false;

352:     function proveMessageFailed(
353:         Message calldata _message,
354:         bytes calldata _proof
355:     )
356:         public
357:         view
358:         returns (bool)
359:     {

360:         if (_message.srcChainId != block.chainid) return false;

374:     function proveMessageReceived(
375:         Message calldata _message,
376:         bytes calldata _proof
377:     )
378:         public
379:         view
380:         returns (bool)
381:     {

382:         if (_message.destChainId != block.chainid) return false;

392:     function isDestChainEnabled(uint64 _chainId)
393:         public
394:         view
395:         returns (bool enabled_, address destBridge_)
396:     {

417:     function getInvocationDelays()
418:         public
419:         view
420:         virtual
421:         returns (uint256 invocationDelay_, uint256 invocationExtraDelay_)
422:     {

423:         if (

461:     function _authorizePause(address)
462:         internal
463:         view
464:         virtual
465:         override
466:         onlyFromOwnerOrNamed("bridge_pauser")
467:     { }

477:     function _invokeMessageCall(
478:         Message calldata _message,
479:         bytes32 _msgHash,
480:         uint256 _gasLimit
481:     )
482:         private
483:         returns (bool success_)
484:     {

485:         if (_gasLimit == 0) revert B_INVALID_GAS_LIMIT();

490:         if (

516:         if (messageStatus[_msgHash] == _status) return;

577:     function _proveSignalReceived(
578:         address _signalService,
579:         bytes32 _signal,
580:         uint64 _chainId,
581:         bytes calldata _proof
582:     )
583:         private
584:         view
585:         returns (bool success_)
586:     {
```

- *AddressManager.sol* ( [38-46](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L38-L46), [48-48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L48-L48) ):

```solidity
38:     function setAddress(
39:         uint64 _chainId,
40:         bytes32 _name,
41:         address _newAddress
42:     )
43:         external
44:         virtual
45:         onlyOwner
46:     {

48:         if (_newAddress == oldAddress) revert AM_INVALID_PARAMS();
```

- *AddressResolver.sol* ( [25-25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L25-L25), [30-38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L30-L38), [43-52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L43-L52), [72-80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L72-L80), [81-81](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L81-L81) ):

```solidity
25:         if (msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();

30:     function resolve(
31:         bytes32 _name,
32:         bool _allowZeroAddress
33:     )
34:         public
35:         view
36:         virtual
37:         returns (address payable)
38:     {

43:     function resolve(
44:         uint64 _chainId,
45:         bytes32 _name,
46:         bool _allowZeroAddress
47:     )
48:         public
49:         view
50:         virtual
51:         returns (address payable)
52:     {

72:     function _resolve(
73:         uint64 _chainId,
74:         bytes32 _name,
75:         bool _allowZeroAddress
76:     )
77:         private
78:         view
79:         returns (address payable addr_)
80:     {

81:         if (addressManager == address(0)) revert RESOLVER_INVALID_MANAGER();
```

- *EssentialContract.sol* ( [42-42](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L42-L42), [47-47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L47-L47), [54-54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L54-L54), [59-59](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L59-L59), [95-102](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L95-L102), [105-105](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L105-L105), [114-114](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L114-L114), [116-116](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L116-L116) ):

```solidity
42:         if (msg.sender != owner() && msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();

47:         if (_loadReentryLock() == _TRUE) revert REENTRANT_CALL();

54:         if (!paused()) revert INVALID_PAUSE_STATUS();

59:         if (paused()) revert INVALID_PAUSE_STATUS();

95:     function __Essential_init(
96:         address _owner,
97:         address _addressManager
98:     )
99:         internal
100:         virtual
101:         onlyInitializing
102:     {

105:         if (_addressManager == address(0)) revert ZERO_ADDR_MANAGER();

114:     function _authorizeUpgrade(address) internal virtual override onlyOwner { }

116:     function _authorizePause(address) internal virtual onlyOwner { }
```

</details>

### [N-84] Too long functions should be refactored

Functions with too many lines are difficult to understand. It is recommended to refactor complex functions into multiple shorter and easier to understand functions.

<details>
<summary>There are 9 instances (click to show):</summary>

- *LibProposing.sol* ( [68](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L68) ):

```solidity
/// @audit 213 lines
68:     function proposeBlock(
```

- *LibProving.sol* ( [91](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L91) ):

```solidity
/// @audit 176 lines
91:     function proveBlock(
```

- *LibVerifying.sol* ( [85](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L85) ):

```solidity
/// @audit 138 lines
85:     function verifyBlocks(
```

- *AutomataDcapV3Attestation.sol* ( [364](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L364) ):

```solidity
/// @audit 122 lines
364:     function _verifyParsedQuote(V3Struct.ParsedV3QuoteStruct memory v3quote)
```

- *PEMCertChainLib.sol* ( [74](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L74) ):

```solidity
/// @audit 141 lines
74:     function decodeCert(
```

- *RsaVerify.sol* ( [43](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L43) ):

```solidity
/// @audit 139 lines
43:     function pkcs1Sha256(
```

- *SHA1.sol* ( [11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SHA1.sol#L11) ):

```solidity
/// @audit 184 lines
11:     function sha1(bytes memory data) internal pure returns (bytes20 ret) {
```

- *RLPReader.sol* ( [144](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L144) ):

```solidity
/// @audit 127 lines
144:     function _decodeLength(RLPItem memory _in)
```

- *MerkleTrie.sol* ( [68](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L68) ):

```solidity
/// @audit 132 lines
68:     function get(
```

</details>

### [N-85] Inconsistent spacing in comments

The comments below are in the `//x` format, which differs from the commonly used idiomatic comment syntax of `//<space>x`. It is recommended to use a consistent comment syntax throughout.

<details>
<summary>There are 44 instances (click to show):</summary>

- *TaikoData.sol* ( [97](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol#L97) ):

```solidity
97:         bytes32 blobHash; //or txListHash (if Blob not yet supported), // slot 3
```

- *LibProving.sol* ( [148](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L148), [157](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L157), [247](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L247), [285](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L285), [324](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L324) ):

```solidity
148:         //

157:         //

247:                 //

285:             //

324:                 //
```

- *LibVerifying.sol* ( [247](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L247) ):

```solidity
247:             _config.chainId <= 1 || _config.chainId == block.chainid //
```

- *DevnetTierProvider.sol* ( [26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L26), [37](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L37) ):

```solidity
26:                 cooldownWindow: 1440, //24 hours

37:                 cooldownWindow: 60, //1 hours
```

- *MainnetTierProvider.sol* ( [26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L26), [37](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L37), [48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L48) ):

```solidity
26:                 cooldownWindow: 1440, //24 hours

37:                 cooldownWindow: 1440, //24 hours

48:                 cooldownWindow: 60, //1 hours
```

- *TestnetTierProvider.sol* ( [26](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L26), [37](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L37), [48](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L48) ):

```solidity
26:                 cooldownWindow: 1440, //24 hours

37:                 cooldownWindow: 1440, //24 hours

48:                 cooldownWindow: 60, //1 hours
```

- *AutomataDcapV3Attestation.sol* ( [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L1), [152](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L152), [345](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L345) ):

```solidity
1: //SPDX-License-Identifier: MIT

152:     ///

345:     ///
```

- *IAttestation.sol* ( [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/interfaces/IAttestation.sol#L1) ):

```solidity
1: //SPDX-License-Identifier: MIT
```

- *ISigVerifyLib.sol* ( [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L1) ):

```solidity
1: //SPDX-License-Identifier: MIT
```

- *EnclaveIdStruct.sol* ( [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/EnclaveIdStruct.sol#L1) ):

```solidity
1: //SPDX-License-Identifier: MIT
```

- *V3Parser.sol* ( [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L1) ):

```solidity
1: //SPDX-License-Identifier: MIT
```

- *V3Struct.sol* ( [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L1) ):

```solidity
1: //SPDX-License-Identifier: MIT
```

- *TCBInfoStruct.sol* ( [1](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol#L1) ):

```solidity
1: //SPDX-License-Identifier: MIT
```

- *RsaVerify.sol* ( [113](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L113), [117](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L117), [118](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L118), [119](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L119), [264](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L264), [265](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L265) ):

```solidity
113:         //

117:         //    digestAlgorithm AlgorithmIdentifier,

118:         //      [optional algorithm parameters]

119:         //    digest OCTET STRING

264:         //    digestAlgorithm AlgorithmIdentifier,

265:         //    digest OCTET STRING
```

- *LibTrieProof.sol* ( [2](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibTrieProof.sol#L2), [4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibTrieProof.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibTrieProof.sol#L5), [24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibTrieProof.sol#L24) ):

```solidity
2: //  _____     _ _         _         _

4: //   | |/ _` | | / / _ \ | |__/ _` | '_ (_-<

5: //   |_|\__,_|_|_\_\___/ |____\__,_|_.__/__/

24:     ///
```

- *TimelockTokenPool.sol* ( [12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L12), [19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L19) ):

```solidity
12: ///

19: ///
```

- *Bytes.sol* ( [67](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L67), [68](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L68), [71](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L71), [75](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L75), [76](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L76) ):

```solidity
67:                 //update free-memory pointer

68:                 //allocating the array padded to 32 bytes like the compiler does now

71:             //if we want a zero-length slice let's just return a zero-length array

75:                 //zero out the 32 bytes slice we are about to return

76:                 //we need to do it because Solidity does not garbage collect
```

- *LibFixedPointMath.sol* ( [70](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L70), [71](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L71), [72](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L72) ):

```solidity
70:             //  * the scale factor s = ~6.031367120...,

71:             //  * the 2**k factor from the range reduction, and

72:             //  * the 1e18 / 2**96 factor for base converison.
```

</details>

### [N-86] Missing event for critical changes

Events should be emitted when critical changes are made to the contracts.

<details>
<summary>There are 7 instances (click to show):</summary>

- *AutomataDcapV3Attestation.sol* ( [65-67](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L65-L67), [69-71](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L69-L71), [73-86](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L73-L86), [103-112](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L103-L112), [114-120](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L114-L120), [122-124](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L122-L124) ):

```solidity
65:     function setMrSigner(bytes32 _mrSigner, bool _trusted) external onlyOwner {
66:         _trustedUserMrSigner[_mrSigner] = _trusted;
67:     }

69:     function setMrEnclave(bytes32 _mrEnclave, bool _trusted) external onlyOwner {
70:         _trustedUserMrEnclave[_mrEnclave] = _trusted;
71:     }

73:     function addRevokedCertSerialNum(
74:         uint256 index,
75:         bytes[] calldata serialNumBatch
76:     )
77:         external
78:         onlyOwner
79:     {
80:         for (uint256 i; i < serialNumBatch.length; ++i) {
81:             if (_serialNumIsRevoked[index][serialNumBatch[i]]) {
82:                 continue;
83:             }
84:             _serialNumIsRevoked[index][serialNumBatch[i]] = true;
85:         }
86:     }

103:     function configureTcbInfoJson(
104:         string calldata fmspc,
105:         TCBInfoStruct.TCBInfo calldata tcbInfoInput
106:     )
107:         public
108:         onlyOwner
109:     {
110:         // 2.2M gas
111:         tcbInfo[fmspc] = tcbInfoInput;
112:     }

114:     function configureQeIdentityJson(EnclaveIdStruct.EnclaveId calldata qeIdentityInput)
115:         external
116:         onlyOwner
117:     {
118:         // 250k gas
119:         qeIdentity = qeIdentityInput;
120:     }

122:     function toggleLocalReportCheck() external onlyOwner {
123:         _checkLocalEnclaveReport = !_checkLocalEnclaveReport;
124:     }
```

- *BridgedERC20.sol* ( [80-82](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L80-L82) ):

```solidity
80:     function setSnapshoter(address _snapshooter) external onlyOwner {
81:         snapshooter = _snapshooter;
82:     }
```

</details>

### [N-87] Non-assembly method available

There are some automated tools that will flag a project as having higher complexity if there is inline-assembly, so it's best to avoid using it where it's not necessary. In addition, most assembly methods can be replaced by non-assembly methods, for example:
- `assembly{ g := gas() }` => `uint256 g = gasleft()`
- `assembly{ id := chainid() }` => `uint256 id = block.chainid`
- `assembly { r := mulmod(a, b, d) }` => `uint256 m = mulmod(x, y, k)`
- `assembly { size := extcodesize() }` => `uint256 size = address(a).code.length`
- etc.

There are 3 instances:

- *TaikoL2.sol* ( [243-243](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L243-L243), [248-248](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L248-L248) ):

```solidity
243:             publicInputHashOld := keccak256(inputs, 8192 /*mul(256, 32)*/ )

248:             publicInputHashNew := keccak256(inputs, 8192 /*mul(256, 32)*/ )
```

- *BytesUtils.sol* ( [27-27](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L27-L27) ):

```solidity
27:             ret := keccak256(add(add(self, 32), offset), len)
```

### [N-88] Duplicated `require()`/`revert()` checks should be refactored

Refactoring duplicate `require()`/`revert()` checks into a modifier or function can make the code more concise, readable and maintainable, and less likely to make errors or omissions when modifying the `require()` or `revert()`.

<details>
<summary>There are 23 instances (click to show):</summary>

- *TaikoToken.sol* ( [61-61](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L61-L61) ):

```solidity
/// @audit Duplicated on line 79
61:         if (_to == address(this)) revert TKO_INVALID_ADDR();
```

- *Guardians.sol* ( [64-64](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L64-L64), [82-82](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L82-L82) ):

```solidity
/// @audit Duplicated on line 84
64:             revert INVALID_GUARDIAN_SET();

/// @audit Duplicated on line 113
82:             if (guardian == address(0)) revert INVALID_GUARDIAN();
```

- *TaikoL2.sol* ( [120-120](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L120-L120) ):

```solidity
/// @audit Duplicated on line 172
120:             revert L2_INVALID_PARAM();
```

- *TaikoL2EIP1559Configurable.sol* ( [33-33](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L33-L33) ):

```solidity
/// @audit Duplicated on line 34
33:         if (_newConfig.gasTargetPerL1Block == 0) revert L2_INVALID_CONFIG();
```

- *SigVerifyLib.sol* ( [50-50](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L50-L50) ):

```solidity
/// @audit Duplicated on line 75
50:             revert("Unsupported algorithm");
```

- *Bridge.sol* ( [132-132](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L132-L132), [166-166](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L166-L166), [212-212](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L212-L212), [261-261](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L261-L261) ):

```solidity
/// @audit Duplicated on line 134
132:         if (!destChainEnabled) revert B_INVALID_CHAINID();

/// @audit Duplicated on line 227
166:         if (messageStatus[msgHash] != Status.NEW) revert B_STATUS_MISMATCH();

/// @audit Duplicated on line 305
212:             revert B_INVOCATION_TOO_EARLY();

/// @audit Duplicated on line 322
261:                 revert B_PERMISSION_DENIED();
```

- *SignalService.sol* ( [132-132](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L132-L132) ):

```solidity
/// @audit Duplicated on line 172
132:             revert SS_SIGNAL_NOT_FOUND();
```

- *TimelockTokenPool.sol* ( [121-121](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L121-L121), [268-268](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L268-L268) ):

```solidity
/// @audit Duplicated on line 124, 127, 136, 169
121:         if (_taikoToken == address(0)) revert INVALID_PARAM();

/// @audit Duplicated on line 277, 278, 275
268:         if (_grant.amount == 0) revert INVALID_GRANT();
```

- *BaseVault.sol* ( [55-55](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L55-L55) ):

```solidity
/// @audit Duplicated on line 65
55:         if (ctx_.from != selfOnSourceChain) revert VAULT_PERMISSION_DENIED();
```

- *BridgedERC20Base.sol* ( [66-66](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L66-L66) ):

```solidity
/// @audit Duplicated on line 78
66:             revert BB_PERMISSION_DENIED();
```

- *ERC20Vault.sol* ( [162-162](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L162-L162) ):

```solidity
/// @audit Duplicated on line 216
162:         if (btokenBlacklist[_btokenNew]) revert VAULT_BTOKEN_BLACKLISTED();
```

- *SgxVerifier.sol* ( [107-107](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L107-L107) ):

```solidity
/// @audit Duplicated on line 161, 215
107:             if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();
```

</details>

### [N-89] Consider adding emergency-stop functionality

Adding a way to quickly halt protocol functionality in an emergency, rather than having to pause individual contracts one-by-one, will make in-progress hack mitigation faster and much less stressful.

<details>
<summary>There are 27 instances (click to show):</summary>

- *TaikoL1.sol* ( [22-22](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L22-L22) ):

```solidity
22: contract TaikoL1 is EssentialContract, ITaikoL1, TaikoEvents, TaikoErrors {
```

- *TaikoToken.sol* ( [15-15](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L15-L15) ):

```solidity
15: contract TaikoToken is EssentialContract, ERC20SnapshotUpgradeable, ERC20VotesUpgradeable {
```

- *TaikoGovernor.sol* ( [16-21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L16-L21) ):

```solidity
16: contract TaikoGovernor is
17:     EssentialContract,
18:     GovernorCompatibilityBravoUpgradeable,
19:     GovernorVotesUpgradeable,
20:     GovernorVotesQuorumFractionUpgradeable,
21:     GovernorTimelockControlUpgradeable
```

- *TaikoTimelockController.sol* ( [9-9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L9-L9) ):

```solidity
9: contract TaikoTimelockController is EssentialContract, TimelockControllerUpgradeable {
```

- *AssignmentHook.sol* ( [14-14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L14-L14) ):

```solidity
14: contract AssignmentHook is EssentialContract, IHook {
```

- *GuardianProver.sol* ( [10-10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/GuardianProver.sol#L10-L10) ):

```solidity
10: contract GuardianProver is Guardians {
```

- *DevnetTierProvider.sol* ( [10-10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L10-L10) ):

```solidity
10: contract DevnetTierProvider is EssentialContract, ITierProvider {
```

- *MainnetTierProvider.sol* ( [10-10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L10-L10) ):

```solidity
10: contract MainnetTierProvider is EssentialContract, ITierProvider {
```

- *TestnetTierProvider.sol* ( [10-10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L10-L10) ):

```solidity
10: contract TestnetTierProvider is EssentialContract, ITierProvider {
```

- *TaikoL2.sol* ( [21-21](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L21-L21) ):

```solidity
21: contract TaikoL2 is CrossChainOwned {
```

- *TaikoL2EIP1559Configurable.sol* ( [9-9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L9-L9) ):

```solidity
9: contract TaikoL2EIP1559Configurable is TaikoL2 {
```

- *Bridge.sol* ( [16-16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L16-L16) ):

```solidity
16: contract Bridge is EssentialContract, IBridge {
```

- *AddressManager.sol* ( [10-10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L10-L10) ):

```solidity
10: contract AddressManager is EssentialContract, IAddressManager {
```

- *SignalService.sol* ( [14-14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L14-L14) ):

```solidity
14: contract SignalService is EssentialContract, ISignalService {
```

- *TimelockTokenPool.sol* ( [25-25](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L25-L25) ):

```solidity
25: contract TimelockTokenPool is EssentialContract {
```

- *ERC20Airdrop.sol* ( [11-11](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L11-L11) ):

```solidity
11: contract ERC20Airdrop is MerkleClaimable {
```

- *ERC20Airdrop2.sol* ( [12-12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L12-L12) ):

```solidity
12: contract ERC20Airdrop2 is MerkleClaimable {
```

- *ERC721Airdrop.sol* ( [9-9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L9-L9) ):

```solidity
9: contract ERC721Airdrop is MerkleClaimable {
```

- *BridgedERC1155.sol* ( [14-14](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L14-L14) ):

```solidity
14: contract BridgedERC1155 is EssentialContract, IERC1155MetadataURIUpgradeable, ERC1155Upgradeable {
```

- *BridgedERC20.sol* ( [15-19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L15-L19) ):

```solidity
15: contract BridgedERC20 is
16:     BridgedERC20Base,
17:     IERC20MetadataUpgradeable,
18:     ERC20SnapshotUpgradeable,
19:     ERC20VotesUpgradeable
```

- *BridgedERC721.sol* ( [12-12](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L12-L12) ):

```solidity
12: contract BridgedERC721 is EssentialContract, ERC721Upgradeable {
```

- *ERC1155Vault.sol* ( [29-29](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L29-L29) ):

```solidity
29: contract ERC1155Vault is BaseNFTVault, ERC1155ReceiverUpgradeable {
```

- *ERC20Vault.sol* ( [18-18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L18-L18) ):

```solidity
18: contract ERC20Vault is BaseVault {
```

- *ERC721Vault.sol* ( [16-16](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L16-L16) ):

```solidity
16: contract ERC721Vault is BaseNFTVault, IERC721Receiver {
```

- *USDCAdapter.sol* ( [28-28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L28-L28) ):

```solidity
28: contract USDCAdapter is BridgedERC20Base {
```

- *GuardianVerifier.sol* ( [10-10](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L10-L10) ):

```solidity
10: contract GuardianVerifier is EssentialContract, IVerifier {
```

- *SgxVerifier.sol* ( [19-19](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L19-L19) ):

```solidity
19: contract SgxVerifier is EssentialContract, IVerifier {
```

</details>

### [N-90] Avoid the use of sensitive terms

Use [alternative variants](https://www.zdnet.com/article/mysql-drops-master-slave-and-blacklist-whitelist-terminology/), e.g. allowlist/denylist instead of whitelist/blacklist.

<details>
<summary>There are 12 instances (click to show):</summary>

- *BytesUtils.sol* ( [5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L5) ):

```solidity
5: // https://github.com/ensdomains/dnssec-oracle/blob/master/contracts/BytesUtils.sol
```

- *RsaVerify.sol* ( [8](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L8) ):

```solidity
8: // https://github.com/adria0/SolRsaVerify/blob/master/src/RsaVerify.sol
```

- *SHA1.sol* ( [6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SHA1.sol#L6) ):

```solidity
6: // https://github.com/ensdomains/solsha1/blob/master/contracts/SHA1.sol
```

- *ERC20Vault.sol* ( [51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L51), [52](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L52), [136](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L136), [162](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L162), [181](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L181), [216](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L216) ):

```solidity
51:     /// @notice Mappings from bridged tokens to their blacklist status.

52:     mapping(address btoken => bool blacklisted) public btokenBlacklist;

136:     error VAULT_BTOKEN_BLACKLISTED();

162:         if (btokenBlacklist[_btokenNew]) revert VAULT_BTOKEN_BLACKLISTED();

181:             btokenBlacklist[btokenOld_] = true;

216:         if (btokenBlacklist[_op.token]) revert VAULT_BTOKEN_BLACKLISTED();
```

</details>

### [N-91] Missing checks for uint state variable assignments

Consider whether reasonable bounds checks for variables would be useful.

<details>
<summary>There are 8 instances (click to show):</summary>

- *CrossChainOwned.sol* ( [73-73](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L73-L73) ):

```solidity
73:         ownerChainId = _ownerChainId;
```

- *TaikoL2.sol* ( [96-96](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L96-L96) ):

```solidity
96:         gasExcess = _gasExcess;
```

- *TaikoL2EIP1559Configurable.sol* ( [37-37](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L37-L37) ):

```solidity
37:         gasExcess = _newGasExcess;
```

- *EssentialContract.sol* ( [125-125](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L125-L125) ):

```solidity
125:             __reentry = _reentry;
```

- *ERC20Airdrop2.sol* ( [71-71](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L71-L71) ):

```solidity
71:         withdrawalWindow = _withdrawalWindow;
```

- *MerkleClaimable.sol* ( [91-91](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L91-L91), [92-92](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L92-L92) ):

```solidity
91:         claimStart = _claimStart;

92:         claimEnd = _claimEnd;
```

- *BridgedERC20.sol* ( [75-75](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L75-L75) ):

```solidity
75:         __srcDecimals = _decimals;
```

</details>

### [N-92] Use the Modern Upgradeable Contract Paradigm

Modern smart contract development often employs upgradeable contract structures, utilizing proxy patterns like OpenZeppelin’s Upgradeable Contracts. This paradigm separates logic and state, allowing developers to amend and enhance the contract's functionality without altering its state or the deployed contract address. Transitioning to this approach enhances long-term maintainability.
Resolution: Adopt a well-established proxy pattern for upgradeability, ensuring proper initialization and employing transparent proxies to mitigate potential risks. Embrace comprehensive testing and audit practices, particularly when updating contract logic, to ensure state consistency and security are preserved across upgrades. This ensures your contract remains robust and adaptable to future requirements.

There are 3 instances:

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

### [N-93] Large or complicated code bases should implement invariant tests

This includes: large code bases, or code with lots of inline-assembly, complicated math, or complicated interactions between multiple contracts.
Invariant fuzzers such as Echidna require the test writer to come up with invariants which should not be violated under any circumstances, and the fuzzer tests various inputs and function calls to ensure that the invariants always hold.
Even code with 100% code coverage can still have bugs due to the order of the operations a user performs, and invariant fuzzers may help significantly.

There is 1 instance:

- Global finding

### [N-94] The default value is manually set when it is declared

In instances where a new variable is defined, there is no need to set it to it's default value.

<details>
<summary>There are 13 instances (click to show):</summary>

- *Guardians.sol* ( [80-80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L80-L80) ):

```solidity
80:         for (uint256 i = 0; i < _newGuardians.length; ++i) {
```

- *PEMCertChainLib.sol* ( [51-51](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L51-L51) ):

```solidity
51:         uint256 index = 0;
```

- *V3Parser.sol* ( [18-18](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L18-L18) ):

```solidity
18:     bytes4 internal constant SUPPORTED_TEE_TYPE = 0;
```

- *BytesUtils.sol* ( [80-80](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L80-L80), [331-331](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L331-L331) ):

```solidity
80:         for (uint256 idx = 0; idx < shortest; idx += 32) {

331:         uint256 ret = 0;
```

- *X509DateUtils.sol* ( [46-46](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L46-L46) ):

```solidity
46:         uint256 timestamp = 0;
```

- *RLPReader.sol* ( [72-72](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L72-L72) ):

```solidity
72:         uint256 itemCount = 0;
```

- *RLPWriter.sol* ( [58-58](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L58-L58), [66-66](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66-L66) ):

```solidity
58:         uint256 i = 0;

66:         for (uint256 j = 0; j < out_.length; j++) {
```

- *MerkleTrie.sol* ( [30-30](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L30-L30), [82-82](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L82-L82), [85-85](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85-L85), [208-208](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L208-L208) ):

```solidity
30:     uint8 internal constant PREFIX_EXTENSION_EVEN = 0;

82:         uint256 currentKeyIndex = 0;

85:         for (uint256 i = 0; i < proof.length; i++) {

208:         for (uint256 i = 0; i < length;) {
```

</details>

### [N-95] Contracts should have all `public`/`external` functions exposed by `interface`s

All `external`/`public` functions should extend an `interface`. This is useful to ensure that the whole API is extracted and can be more easily integrated by other projects.

<details>
<summary>There are 28 instances (click to show):</summary>

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

### [N-96] Top-level declarations should be separated by at least two lines

-

<details>
<summary>There are 167 instances (click to show):</summary>

- *ITaikoL1.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/ITaikoL1.sol#L2-L4) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "./TaikoData.sol";
```

- *TaikoEvents.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoEvents.sol#L2-L4) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "./TaikoData.sol";
```

- *TaikoL1.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L2-L4), [218-220](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L218-L220) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "../common/EssentialContract.sol";

218:     }
219: 
220:     function _authorizePause(address)
```

- *TaikoToken.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L2-L4), [81-83](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L81-L83), [92-94](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L92-L94), [103-105](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L103-L105), [113-115](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol#L113-L115) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "@openzeppelin/contracts-upgradeable/token/ERC20/ERC20Upgradeable.sol";

81:     }
82: 
83:     function _beforeTokenTransfer(

92:     }
93: 
94:     function _afterTokenTransfer(

103:     }
104: 
105:     function _mint(

113:     }
114: 
115:     function _burn(
```

- *TaikoGovernor.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L2-L4), [125-127](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L125-L127), [138-140](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L138-L140), [151-153](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L151-L153) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "@openzeppelin/contracts-upgradeable/governance/GovernorUpgradeable.sol";

125:     }
126: 
127:     function _execute(

138:     }
139: 
140:     function _cancel(

151:     }
152: 
153:     function _executor()
```

- *TaikoTimelockController.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L2-L4) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "@openzeppelin/contracts-upgradeable/governance/TimelockControllerUpgradeable.sol";
```

- *AssignmentHook.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L2-L4), [162-164](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L162-L164) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

162:     }
163: 
164:     function _getProverFee(
```

- *IHook.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/IHook.sol#L2-L4) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "../TaikoData.sol";
```

- *LibDepositing.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol#L2-L4) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "../../common/IAddressResolver.sol";
```

- *LibProposing.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L2-L4), [297-299](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L297-L299) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

297:     }
298: 
299:     function _isProposerPermitted(
```

- *LibProving.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L2-L4) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```

- *LibUtils.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol#L2-L4) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "../TaikoData.sol";
```

- *LibVerifying.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L2-L4), [222-224](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L222-L224), [243-245](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol#L243-L245) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

222:     }
223: 
224:     function _syncChainData(

243:     }
244: 
245:     function _isConfigValid(TaikoData.Config memory _config) private view returns (bool) {
```

- *GuardianProver.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/GuardianProver.sol#L2-L4) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "../tiers/ITierProvider.sol";
```

- *Guardians.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L2-L4), [109-111](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L109-L111), [122-124](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L122-L124), [126-128](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L126-L128) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "../../common/EssentialContract.sol";

109:     }
110: 
111:     function approve(uint256 _operationId, bytes32 _hash) internal returns (bool approved_) {

122:     }
123: 
124:     function deleteApproval(bytes32 _hash) internal {

126:     }
127: 
128:     function isApproved(uint256 _approvalBits) internal view returns (bool) {
```

- *DevnetTierProvider.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L2-L4) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "../../common/EssentialContract.sol";
```

- *MainnetTierProvider.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L2-L4) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "../../common/EssentialContract.sol";
```

- *TestnetTierProvider.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L2-L4) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "../../common/EssentialContract.sol";
```

- *CrossChainOwned.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L2-L4) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```

- *Lib1559Math.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/Lib1559Math.sol#L2-L4) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "../thirdparty/solmate/LibFixedPointMath.sol";
```

- *TaikoL2.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L2-L4), [221-223](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L221-L223), [250-252](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L250-L252) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

221:     }
222: 
223:     function _calcPublicInputHash(uint256 _blockId)

250:     }
251: 
252:     function _calc1559BaseFee(
```

- *TaikoL2EIP1559Configurable.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L2-L4) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "./TaikoL2.sol";
```

- *AutomataDcapV3Attestation.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L2-L4), [58-60](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L58-L60), [63-65](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L63-L65), [67-69](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L67-L69), [71-73](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L71-L73), [86-88](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L86-L88), [101-103](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L101-L103), [112-114](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L112-L114), [120-122](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L120-L122), [124-126](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L124-L126), [136-138](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L136-L138), [173-175](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L173-L175), [204-206](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L204-L206), [227-229](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L227-L229), [246-248](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L246-L248), [301-303](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L301-L303), [362-364](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L362-L364) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import { V3Struct } from "./lib/QuoteV3Auth/V3Struct.sol";

58:     }
59: 
60:     modifier onlyOwner() {

63:     }
64: 
65:     function setMrSigner(bytes32 _mrSigner, bool _trusted) external onlyOwner {

67:     }
68: 
69:     function setMrEnclave(bytes32 _mrEnclave, bool _trusted) external onlyOwner {

71:     }
72: 
73:     function addRevokedCertSerialNum(

86:     }
87: 
88:     function removeRevokedCertSerialNum(

101:     }
102: 
103:     function configureTcbInfoJson(

112:     }
113: 
114:     function configureQeIdentityJson(EnclaveIdStruct.EnclaveId calldata qeIdentityInput)

120:     }
121: 
122:     function toggleLocalReportCheck() external onlyOwner {

124:     }
125: 
126:     function _attestationTcbIsValid(TCBInfoStruct.TCBStatus status)

136:     }
137: 
138:     function verifyAttestation(bytes calldata data) external view override returns (bool) {

173:     }
174: 
175:     function _verifyQEReportWithIdentity(V3Struct.EnclaveReport memory quoteEnclaveReport)

204:     }
205: 
206:     function _checkTcbLevels(

227:     }
228: 
229:     function _isCpuSvnHigherOrGreater(

246:     }
247: 
248:     function _verifyCertChain(IPEMCertChainLib.ECSha256Certificate[] memory certs)

301:     }
302: 
303:     function _enclaveReportSigVerification(

362:     }
363: 
364:     function _verifyParsedQuote(V3Struct.ParsedV3QuoteStruct memory v3quote)
```

- *IAttestation.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/interfaces/IAttestation.sol#L2-L4) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import { V3Struct } from "../lib/QuoteV3Auth/V3Struct.sol";
```

- *ISigVerifyLib.sol* ( [36-38](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L36-L38) ):

```solidity
36:     }
37: 
38:     function verifyAttStmtSignature(
```

- *PEMCertChainLib.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L2-L4), [38-40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L38-L40), [72-74](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L72-L74), [214-216](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L214-L216), [250-252](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L250-L252), [267-269](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L267-L269), [339-341](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L339-L341) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import { LibString } from "solady/src/utils/LibString.sol";

38:     }
39: 
40:     function splitCertificateChain(

72:     }
73: 
74:     function decodeCert(

214:     }
215: 
216:     function _removeHeadersAndFooters(string memory pemData)

250:     }
251: 
252:     function _trimBytes(

267:     }
268: 
269:     function _findPckTcbInfo(

339:     }
340: 
341:     function _findTcb(
```

- *V3Parser.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L2-L4), [60-62](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L60-L62), [131-133](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L131-L133), [150-152](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L150-L152), [163-165](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L163-L165), [201-203](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L201-L203), [265-267](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L265-L267) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import { Base64 } from "solady/src/utils/Base64.sol";

60:     }
61: 
62:     function validateParsedInput(V3Struct.ParsedV3QuoteStruct memory v3Quote)

131:     }
132: 
133:     function parseEnclaveReport(bytes memory rawEnclaveReport)

150:     }
151: 
152:     function littleEndianDecode(bytes memory encoded) private pure returns (uint256 decoded) {

163:     }
164: 
165:     function parseAndVerifyHeader(bytes memory rawHeader)

201:     }
202: 
203:     function parseAuthDataAndVerifyCertType(

265:     }
266: 
267:     function parseCerificationChainBytes(
```

- *IPEMCertChainLib.sol* ( [34-36](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L34-L36) ):

```solidity
34:     }
35: 
36:     function splitCertificateChain(
```

- *Asn1Decode.sol* ( [163-165](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L163-L165), [167-169](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L167-L169), [185-187](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L185-L187) ):

```solidity
163:     }
164: 
165:     function keccakOfBytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes32) {

167:     }
168: 
169:     function keccakOfAllBytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes32) {

185:     }
186: 
187:     function _readNodeLength(bytes memory der, uint256 ix) private pure returns (uint256) {
```

- *BytesUtils.sol* ( [270-272](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L270-L272), [369-371](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L369-L371) ):

```solidity
270:     }
271: 
272:     function memcpy(uint256 dest, uint256 src, uint256 len) private pure {

369:     }
370: 
371:     function compareBytes(bytes memory a, bytes memory b) internal pure returns (bool) {
```

- *RsaVerify.sol* ( [3-5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L3-L5) ):

```solidity
3: pragma solidity 0.8.24;
4: 
5: import "./SHA1.sol";
```

- *SigVerifyLib.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L2-L4), [22-24](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L22-L24), [52-54](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L52-L54), [77-79](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L77-L79), [94-96](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L94-L96), [111-113](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L111-L113) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "../interfaces/ISigVerifyLib.sol";

22:     }
23: 
24:     function verifyAttStmtSignature(

52:     }
53: 
54:     function verifyCertificateSignature(

77:     }
78: 
79:     function verifyRS256Signature(

94:     }
95: 
96:     function verifyRS1Signature(

111:     }
112: 
113:     function verifyES256Signature(
```

- *X509DateUtils.sol* ( [32-34](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L32-L34), [69-71](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L69-L71) ):

```solidity
32:     }
33: 
34:     function toUnixTimestamp(

69:     }
70: 
71:     function isLeapYear(uint16 year) internal pure returns (bool) {
```

- *Bridge.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L2-L4) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "@openzeppelin/contracts/utils/Address.sol";
```

- *AddressManager.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L2-L4), [56-58](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol#L56-L58) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "./IAddressManager.sol";

56:     }
57: 
58:     function _authorizePause(address) internal pure override {
```

- *AddressResolver.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol#L2-L4) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "@openzeppelin/contracts-upgradeable/proxy/utils/Initializable.sol";
```

- *EssentialContract.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L2-L4), [44-46](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L44-L46), [51-53](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L51-L53), [56-58](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L56-L58), [107-109](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L107-L109), [112-114](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L112-L114), [114-116](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L114-L116), [138-140](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol#L138-L140) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "@openzeppelin/contracts/proxy/utils/UUPSUpgradeable.sol";

44:     }
45: 
46:     modifier nonReentrant() {

51:     }
52: 
53:     modifier whenPaused() {

56:     }
57: 
58:     modifier whenNotPaused() {

107:     }
108: 
109:     function __Essential_init(address _owner) internal virtual {

112:     }
113: 
114:     function _authorizeUpgrade(address) internal virtual override onlyOwner { }

114:     function _authorizeUpgrade(address) internal virtual override onlyOwner { }
115: 
116:     function _authorizePause(address) internal virtual onlyOwner { }

138:     }
139: 
140:     function _inNonReentrant() internal view returns (bool) {
```

- *LibAddress.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L2-L4), [44-46](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L44-L46), [59-61](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L59-L61), [75-77](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol#L75-L77) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "@openzeppelin/contracts/utils/Address.sol";

44:     }
45: 
46:     function supportsInterface(

59:     }
60: 
61:     function isValidSignature(

75:     }
76: 
77:     function isSenderEOA() internal view returns (bool) {
```

- *LibTrieProof.sol* ( [7-9](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibTrieProof.sol#L7-L9) ):

```solidity
7: pragma solidity 0.8.24;
8: 
9: import "../thirdparty/optimism/rlp/RLPReader.sol";
```

- *SignalService.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L2-L4), [38-40](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L38-L40), [204-206](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L204-L206), [229-231](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L229-L231), [233-235](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L233-L235), [251-253](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L251-L253), [269-271](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L269-L271), [296-298](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol#L296-L298) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "@openzeppelin/contracts/utils/math/SafeCast.sol";

38:     }
39: 
40:     modifier nonZeroValue(bytes32 _input) {

204:     }
205: 
206:     function _verifyHopProof(

229:     }
230: 
231:     function _authorizePause(address) internal pure override {

233:     }
234: 
235:     function _syncChainData(

251:     }
252: 
253:     function _sendSignal(

269:     }
270: 
271:     function _cacheChainData(

296:     }
297: 
298:     function _loadSignalValue(
```

- *TimelockTokenPool.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L2-L4), [206-208](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L206-L208), [223-225](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L223-L225), [233-235](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L233-L235), [237-239](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L237-L239), [243-245](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L243-L245), [265-267](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L265-L267), [271-273](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol#L271-L273) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol";

206:     }
207: 
208:     function _withdraw(address _recipient, address _to) private {

223:     }
224: 
225:     function _voidGrant(Grant storage _grant) private returns (uint128 amountVoided) {

233:     }
234: 
235:     function _getAmountOwned(Grant memory _grant) private view returns (uint128) {

237:     }
238: 
239:     function _getAmountUnlocked(Grant memory _grant) private view returns (uint128) {

243:     }
244: 
245:     function _calcAmount(

265:     }
266: 
267:     function _validateGrant(Grant memory _grant) private pure {

271:     }
272: 
273:     function _validateCliff(uint64 _start, uint64 _cliff, uint32 _period) private pure {
```

- *ERC20Airdrop.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L2-L4) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```

- *ERC20Airdrop2.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L2-L4) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```

- *ERC721Airdrop.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L2-L4) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "@openzeppelin/contracts/token/ERC721/IERC721.sol";
```

- *MerkleClaimable.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L2-L4), [54-56](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L54-L56), [65-67](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L65-L67), [75-77](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L75-L77), [88-90](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L88-L90) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "@openzeppelin/contracts/utils/cryptography/MerkleProof.sol";

54:     }
55: 
56:     function __MerkleClaimable_init(

65:     }
66: 
67:     function _verifyClaim(bytes memory data, bytes32[] calldata proof) internal ongoingClaim {

75:     }
76: 
77:     function _verifyMerkleProof(

88:     }
89: 
90:     function _setConfig(uint64 _claimStart, uint64 _claimEnd, bytes32 _merkleRoot) private {
```

- *ExcessivelySafeCall.sol* ( [3-5](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L3-L5) ):

```solidity
3: pragma solidity 0.8.24;
4: 
5: library ExcessivelySafeCall {
```

- *MerkleTrie.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L2-L4) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import { Bytes } from "../Bytes.sol";
```

- *SecureMerkleTrie.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L2-L4) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import { MerkleTrie } from "./MerkleTrie.sol";
```

- *LibFixedPointMath.sol* ( [4-6](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L4-L6) ):

```solidity
4: pragma solidity 0.8.24;
5: 
6: library LibFixedPointMath {
```

- *BaseNFTVault.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L2-L4) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "./BaseVault.sol";
```

- *BaseVault.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L2-L4), [56-58](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol#L56-L58) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "@openzeppelin/contracts-upgradeable/utils/introspection/IERC165Upgradeable.sol";

56:     }
57: 
58:     function checkRecallMessageContext()
```

- *BridgedERC1155.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L2-L4), [123-125](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L123-L125) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "@openzeppelin/contracts/utils/Strings.sol";

123:     }
124: 
125:     function _beforeTokenTransfer(
```

- *BridgedERC20.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L2-L4), [127-129](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L127-L129), [131-133](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L131-L133), [150-152](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L150-L152), [161-163](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L161-L163), [171-173](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L171-L173) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/IERC20MetadataUpgradeable.sol";

127:     }
128: 
129:     function _mintToken(address _account, uint256 _amount) internal override {

131:     }
132: 
133:     function _burnToken(address _from, uint256 _amount) internal override {

150:     }
151: 
152:     function _afterTokenTransfer(

161:     }
162: 
163:     function _mint(

171:     }
172: 
173:     function _burn(
```

- *BridgedERC20Base.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L2-L4), [95-97](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L95-L97) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "../common/EssentialContract.sol";

95:     }
96: 
97:     function _mintToken(address _account, uint256 _amount) internal virtual;
```

- *BridgedERC721.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L2-L4), [113-115](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L113-L115) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "@openzeppelin/contracts-upgradeable/token/ERC721/ERC721Upgradeable.sol";

113:     }
114: 
115:     function _beforeTokenTransfer(
```

- *ERC1155Vault.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L2-L4) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "@openzeppelin/contracts/token/ERC1155/IERC1155.sol";
```

- *ERC20Vault.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L2-L4), [318-320](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L318-L320) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

318:     }
319: 
320:     function _transferTokens(
```

- *ERC721Vault.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L2-L4), [158-160](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L158-L160) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "@openzeppelin/contracts/token/ERC721/IERC721.sol";

158:     }
159: 
160:     function _transferTokens(
```

- *LibBridgedToken.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L2-L4), [26-28](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L26-L28), [37-39](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L37-L39), [41-43](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L41-L43) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "@openzeppelin/contracts/utils/Strings.sol";

26:     }
27: 
28:     function buildName(

37:     }
38: 
39:     function buildSymbol(string memory _symbol) internal pure returns (string memory) {

41:     }
42: 
43:     function buildURI(
```

- *USDCAdapter.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L2-L4), [41-43](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L41-L43), [45-47](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L45-L47) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "../BridgedERC20Base.sol";

41:     }
42: 
43:     function _mintToken(address _account, uint256 _amount) internal override {

45:     }
46: 
47:     function _burnToken(address _from, uint256 _amount) internal override {
```

- *GuardianVerifier.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L2-L4) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "../common/EssentialContract.sol";
```

- *IVerifier.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/IVerifier.sol#L2-L4) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "../L1/TaikoData.sol";
```

- *SgxVerifier.sol* ( [2-4](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L2-L4), [193-195](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L193-L195), [224-226](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L224-L226), [231-233](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol#L231-L233) ):

```solidity
2: pragma solidity 0.8.24;
3: 
4: import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol";

193:     }
194: 
195:     function _addInstances(

224:     }
225: 
226:     function _replaceInstance(uint256 id, address oldInstance, address newInstance) private {

231:     }
232: 
233:     function _isInstanceValid(uint256 id, address instance) private view returns (bool) {
```

</details>

### [N-97] Consider adding formal verification proofs

Formal verification is the act of proving or disproving the correctness of intended algorithms underlying a system with respect to a certain formal specification/property/invariant, using formal methods of mathematics.

Some tools that are currently available to perform these tests on smart contracts are [SMTChecker](https://docs.soliditylang.org/en/latest/smtchecker.html) and [Certora Prover](https://www.certora.com/).

<details>
<summary>There are 81 instances (click to show):</summary>

- [*ITaikoL1.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/ITaikoL1.sol)

- [*TaikoData.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoData.sol)

- [*TaikoErrors.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoErrors.sol)

- [*TaikoEvents.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoEvents.sol)

- [*TaikoL1.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol)

- [*TaikoToken.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoToken.sol)

- [*TaikoGovernor.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol)

- [*TaikoTimelockController.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol)

- [*AssignmentHook.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/AssignmentHook.sol)

- [*IHook.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/hooks/IHook.sol)

- [*LibDepositing.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibDepositing.sol)

- [*LibProposing.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol)

- [*LibProving.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol)

- [*LibUtils.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibUtils.sol)

- [*LibVerifying.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibVerifying.sol)

- [*GuardianProver.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/GuardianProver.sol)

- [*Guardians.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol)

- [*DevnetTierProvider.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol)

- [*ITierProvider.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/ITierProvider.sol)

- [*MainnetTierProvider.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol)

- [*TestnetTierProvider.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol)

- [*CrossChainOwned.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol)

- [*Lib1559Math.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/Lib1559Math.sol)

- [*TaikoL2.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol)

- [*TaikoL2EIP1559Configurable.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol)

- [*AutomataDcapV3Attestation.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol)

- [*IAttestation.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/interfaces/IAttestation.sol)

- [*ISigVerifyLib.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol)

- [*EnclaveIdStruct.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/EnclaveIdStruct.sol)

- [*PEMCertChainLib.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol)

- [*V3Parser.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol)

- [*V3Struct.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol)

- [*TCBInfoStruct.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol)

- [*IPEMCertChainLib.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol)

- [*Asn1Decode.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol)

- [*BytesUtils.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol)

- [*RsaVerify.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol)

- [*SHA1.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SHA1.sol)

- [*SigVerifyLib.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol)

- [*X509DateUtils.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol)

- [*Bridge.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol)

- [*IBridge.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/IBridge.sol)

- [*AddressManager.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressManager.sol)

- [*AddressResolver.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/AddressResolver.sol)

- [*EssentialContract.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/EssentialContract.sol)

- [*IAddressManager.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/IAddressManager.sol)

- [*IAddressResolver.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/common/IAddressResolver.sol)

- [*Lib4844.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/Lib4844.sol)

- [*LibAddress.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibAddress.sol)

- [*LibMath.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibMath.sol)

- [*LibTrieProof.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/libs/LibTrieProof.sol)

- [*ISignalService.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/ISignalService.sol)

- [*LibSignals.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/LibSignals.sol)

- [*SignalService.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/signal/SignalService.sol)

- [*TimelockTokenPool.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/TimelockTokenPool.sol)

- [*ERC20Airdrop.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol)

- [*ERC20Airdrop2.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol)

- [*ERC721Airdrop.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol)

- [*MerkleClaimable.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol)

- [*ExcessivelySafeCall.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol)

- [*Bytes.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/Bytes.sol)

- [*RLPReader.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol)

- [*RLPWriter.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol)

- [*MerkleTrie.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol)

- [*SecureMerkleTrie.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol)

- [*LibFixedPointMath.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol)

- [*BaseNFTVault.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseNFTVault.sol)

- [*BaseVault.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BaseVault.sol)

- [*BridgedERC1155.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC1155.sol)

- [*BridgedERC20.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20.sol)

- [*BridgedERC20Base.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol)

- [*BridgedERC721.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol)

- [*ERC1155Vault.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol)

- [*ERC20Vault.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol)

- [*ERC721Vault.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC721Vault.sol)

- [*IBridgedERC20.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/IBridgedERC20.sol)

- [*LibBridgedToken.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/LibBridgedToken.sol)

- [*USDCAdapter.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol)

- [*GuardianVerifier.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/GuardianVerifier.sol)

- [*IVerifier.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/IVerifier.sol)

- [*SgxVerifier.sol*](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/verifiers/SgxVerifier.sol)

</details>

### [N-98] Use scopes sparingly

The use of scoped blocks, denoted by `{}` without a preceding control structure like `if`, `for`, etc., allows for the creation of isolated scopes within a function. While this can be useful for managing memory and preventing naming conflicts, it should be used sparingly. Excessive use of these scope blocks can obscure the code's logic flow and make it more difficult to understand, impeding code maintainability. As a best practice, only employ scoped blocks when necessary for memory management or to avoid clear naming conflicts. Otherwise, aim for clarity and simplicity in your code structure for optimal readability and maintainability.

<details>
<summary>There are 12 instances (click to show):</summary>

- *LibProposing.sol* ( [236-237](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProposing.sol#L236-L237) ):

```solidity
236:         {
237:             IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));
```

- *LibProving.sol* ( [160-161](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/libs/LibProving.sol#L160-L161) ):

```solidity
160:         {
161:             address verifier = _resolver.resolve(tier.verifierName, true);
```

- *AutomataDcapV3Attestation.sol* ( [384-385](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L384-L385), [399-400](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L399-L400), [417-418](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L417-L418), [434-435](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L434-L435), [451-452](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L451-L452), [461-462](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L461-L462), [470-471](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L470-L471) ):

```solidity
384:         {
385:             if (_checkLocalEnclaveReport) {

399:         {
400:             bool verifiedEnclaveIdSuccessfully;

417:         {
418:             // 536k gas

434:         {
435:             string memory parsedFmspc = parsedQuoteCerts[0].pck.sgxExtension.fmspc;

451:         {
452:             // 4k gas

461:         {
462:             // 660k gas (rootCA pubkey is trusted)

470:         {
471:             bool enclaveReportSigsVerified = _enclaveReportSigVerification(
```

- *PEMCertChainLib.sol* ( [106-107](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L106-L107), [129-130](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L129-L130), [159-160](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L159-L160) ):

```solidity
106:         {
107:             bytes memory serialNumBytes = der.bytesAt(tbsPtr);

129:         {
130:             uint256 notBeforePtr = der.firstChildOf(tbsPtr);

159:         {
160:             // Entering subjectPublicKeyInfo sequence
```

</details>

### [N-99] Prevent re-setting a state variable with the same value

This especially problematic when the setter also emits the same value, which may be confusing to offline parsers.

<details>
<summary>There are 13 instances (click to show):</summary>

- *Guardians.sol* ( [94-94](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/provers/Guardians.sol#L94-L94) ):

```solidity
94:         minGuardians = _minGuardians;
```

- *CrossChainOwned.sol* ( [73-73](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/CrossChainOwned.sol#L73-L73) ):

```solidity
73:         ownerChainId = _ownerChainId;
```

- *TaikoL2.sol* ( [151-151](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L151-L151), [155-155](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2.sol#L155-L155) ):

```solidity
151:             lastSyncedBlock = _l1BlockId;

155:         publicInputHash = publicInputHashNew;
```

- *TaikoL2EIP1559Configurable.sol* ( [37-37](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L37-L37) ):

```solidity
37:         gasExcess = _newGasExcess;
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

</details>

### [N-100] Numeric values having to do with time should use time units for readability

There are [time units](https://docs.soliditylang.org/en/latest/units-and-global-variables.html#time-units) for seconds, minutes, hours, days, and weeks, and since they're defined, they should be used.

There are 4 instances:

- *TaikoL1.sol* ( [195-195](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/TaikoL1.sol#L195-L195) ):

```solidity
/// @audit 864_000
195:             blockMaxProposals: 864_000,
```

- *TaikoGovernor.sol* ( [112-112](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L112-L112), [118-118](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L118-L118) ):

```solidity
/// @audit 7200
112:         return 7200; // 1 day

/// @audit 50_400
118:         return 50_400; // 1 week
```

- *Bridge.sol* ( [439-439](https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L439-L439) ):

```solidity
/// @audit 32_400
439:         } else if (block.chainid >= 32_300 && block.chainid <= 32_400) {
```

