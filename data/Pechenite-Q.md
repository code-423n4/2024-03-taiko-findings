### Low

|Number|Issue|Instances|
|-|:-|:-:|
| [L&#x2011;1](#L1-add-to-blacklist-function) | Add to `blacklist` function | 5 |
| [L&#x2011;2](#L2-array-is-pushed-but-not-poped) | Array is `push()`'ed but not `pop()`'ed | 1 |
| [L&#x2011;3](#L3-avoid-shadowing-state-variables) | Avoid shadowing state variables | 35 |
| [L&#x2011;4](#L4-avoid-using-txorigin) | Avoid using `tx.origin` | 1 |
| [L&#x2011;5](#L5-blocknumber-means-different-things-on-different-l2s) | `block.number` means different things on different L2s | 14 |
| [L&#x2011;6](#L6-calling-bytesconcat-with-final-arguments-that-may-differ-in-length-may-cause-hash-collisions) | Calling `bytes.concat()` with final arguments that may differ in length, may cause hash collisions | 3 |
| [L&#x2011;7](#L7-centralization-risk-for-trusted-owners) | Centralization risk for trusted owners | 21 |
| [L&#x2011;8](#L8-consider-bounding-input-array-length) | Consider bounding input array length | 5 |
| [L&#x2011;9](#L9-consider-disabling-renounceownership) | Consider disabling `renounceOwnership()` | 1 |
| [L&#x2011;10](#L10-consider-implementing-two-step-procedure-for-updating-protocol-addresses) | Consider implementing two-step procedure for updating protocol addresses | 2 |
| [L&#x2011;11](#L11-constructor/initialize-function-lacks-parameter-validation) | `constructor`/`initialize` function lacks parameter validation | 2 |
| [L&#x2011;12](#L12-critical-functions-should-be-controlled-by-time-locks) | Critical functions should be controlled by time locks | 3 |
| [L&#x2011;13](#L13-decimals-is-not-a-part-of-the-erc-20-standard) | `decimals()` is not a part of the ERC-20 standard | 1 |
| [L&#x2011;14](#L14-division-by-zero-not-prevented) | Division by zero not prevented | 2 |
| [L&#x2011;15](#L15-external-calls-in-an-un-bounded-for-loop-may-result-in-a-dos) | External calls in an un-bounded `for`-loop may result in a DOS | 9 |
| [L&#x2011;16](#L16-functions-calling-contracts/addresses-with-transfer-hooks-are-missing-reentrancy-guards) | Functions calling contracts/addresses with transfer hooks are missing reentrancy guards | 3 |
| [L&#x2011;17](#L17-int-casting-blocktimestamp-can-reduce-the-lifespan-of-a-contract) | Int casting `block.timestamp` can reduce the lifespan of a contract | 12 |
| [L&#x2011;18](#L18-loss-of-precision) | Loss of precision | 2 |
| [L&#x2011;19](#L19-minting-in-a-loop-may-lead-to-a-dos) | Minting in a loop may lead to a DOS | 1 |
| [L&#x2011;20](#L20-missing-checks-for-address0-when-assigning-values-to-address-state-variables) | Missing checks for `address(0)` when assigning values to address state variables | 12 |
| [L&#x2011;21](#L21-missing-contract-existence-checks-before-yul-call) | Missing contract-existence checks before yul `call()` | 1 |
| [L&#x2011;22](#L22-missing-_disableinitializer-in-upgradeable-constructor-body) | Missing `_disableInitializer()` in upgradeable constructor body | 9 |
| [L&#x2011;23](#L23-missing-zero-address-check-in-functions-with-address-parameters) | Missing zero address check in functions with address parameters | 40 |
| [L&#x2011;24](#L24-name-is-not-a-part-of-the-erc-20-standard) | `name()` is not a part of the ERC-20 standard | 5 |
| [L&#x2011;25](#L25-nft-doesnt-handle-hard-forks) | NFT doesn't handle hard forks | 1 |
| [L&#x2011;26](#L26-numbers-downcast-to-addresses-may-result-in-collisions) | Numbers downcast to `address`es may result in collisions | 2 |
| [L&#x2011;27](#L27-onlyowner-functions-not-accessible-if-owner-renounces-ownership) | `onlyOwner` functions not accessible if `owner` renounces ownership | 2 |
| [L&#x2011;28](#L28-payable-function-does-not-transfer-eth) | `payable` function does not transfer Eth | 2 |
| [L&#x2011;29](#L29-require-should-be-used-instead-of-assert) | `require()` should be used instead of `assert()` | 4 |
| [L&#x2011;30](#L30-return-values-of-transfer/transferfrom-not-checked) | Return values of `transfer()/transferFrom()` not checked | 32 |
| [L&#x2011;31](#L31-setters-should-prevent-re-setting-of-the-same-value) | Setters should prevent re-setting of the same value | 4 |
| [L&#x2011;32](#L32-some-tokens-may-revert-when-zero-value-transfers-are-made) | Some tokens may revert when zero value transfers are made | 5 |
| [L&#x2011;33](#L33-some-tokens-may-revert-when-zero-value-transfers-are-made) | Some tokens may revert when zero value transfers are made | 11 |
| [L&#x2011;34](#L34-state-variables-not-capped-at-reasonable-values) | State variables not capped at reasonable values | 23 |
| [L&#x2011;35](#L35-symbol-is-not-a-part-of-the-erc-20-standard) | `symbol()` is not a part of the ERC-20 standard | 5 |
| [L&#x2011;36](#L36-tokenuri-does-not-follow-eip-721) | `tokenURI()` does not follow EIP-721 | 1 |
| [L&#x2011;37](#L37-unchecked-blocks-with-additions/multiplications-may-overflow) | `unchecked` blocks with additions/multiplications may overflow | 27 |
| [L&#x2011;38](#L38-unchecked-blocks-with-subtractions-may-underflow) | `unchecked` blocks with subtractions may underflow | 15 |
| [L&#x2011;39](#L39-unsafe-conversion-from-unsigned-to-signed-values) | Unsafe conversion from unsigned to signed values | 5 |
| [L&#x2011;40](#L40-unsafe-downcast) | Unsafe downcast | 27 |
| [L&#x2011;41](#L41-unused/empty-receive/fallback-function) | Unused/empty `receive()/fallback()` function | 1 |
| [L&#x2011;42](#L42-upgradable-contracts-should-have-an-initialization-function) | Upgradable contracts should have an initialization function | 1 |
| [L&#x2011;43](#L43-vulnerable-versions-of-packages-are-being-used) | Vulnerable versions of packages are being used | 1 |



### NonCritical

|Number|Issue|Instances|
|-|:-|:-:|
| [NC&#x2011;1](#NC1-add-inline-comments-for-unnamed-variables) | Add inline comments for unnamed variables | 11 |
| [NC&#x2011;2](#NC2-adding-a-return-statement-when-the-function-defines-a-named-return-variable-is-redundant) | Adding a `return` statement when the function defines a named return variable, is redundant | 1 |
| [NC&#x2011;3](#NC3-address-shouldnt-be-hard-coded) | `address` shouldn't be hard-coded | 1 |
| [NC&#x2011;4](#NC4-assembly-block-creates-dirty-bits) | Assembly block creates dirty bits | 1 |
| [NC&#x2011;5](#NC5-assembly-blocks-should-have-extensive-comments) | Assembly blocks should have extensive comments | 33 |
| [NC&#x2011;6](#NC6-avoid-mutating-function/modifier-parameters) | Avoid mutating `function`/`modifier` parameters | 6 |
| [NC&#x2011;7](#NC7-avoid-the-use-of-sensitive-terms) | Avoid the use of sensitive terms | 9 |
| [NC&#x2011;8](#NC8-codebase-should-implement-formal-verification-testing) | Codebase should implement formal verification testing | 1 |
| [NC&#x2011;9](#NC9-common-functions-should-be-refactored-to-a-common-base-contract) | Common functions should be refactored to a common base contract | 3 |
| [NC&#x2011;10](#NC10-complicated-functions-should-have-explicit-comments) | Complicated functions should have explicit comments | 17 |
| [NC&#x2011;11](#NC11-consider-adding-a-block/deny-list) | Consider adding a block/deny-list | 30 |
| [NC&#x2011;12](#NC12-consider-disallowing-transfers-to-addressthis) | Consider disallowing transfers to `address(this)` | 5 |
| [NC&#x2011;13](#NC13-consider-making-contracts-upgradeable) | Consider making contracts `Upgradeable` | 31 |
| [NC&#x2011;14](#NC14-consider-moving-duplicated-strings-to-constants) | Consider moving duplicated strings to constants | 40 |
| [NC&#x2011;15](#NC15-consider-moving-msgsender-checks-to-a-common-authorization-modifier) | Consider moving `msg.sender` checks to a common authorization `modifier` | 5 |
| [NC&#x2011;16](#NC16-consider-providing-a-ranged-getter-for-array-state-variables) | Consider providing a ranged getter for array state variables | 40 |
| [NC&#x2011;17](#NC17-consider-using-delete-rather-than-assigning-zero-to-clear-values) | Consider using `delete` rather than assigning zero to clear values | 14 |
| [NC&#x2011;18](#NC18-consider-using-named-function-arguments) | Consider using named function arguments | 15 |
| [NC&#x2011;19](#NC19-constants-in-comparisons-should-appear-on-the-left-side) | Constants in comparisons should appear on the left side | 40 |
| [NC&#x2011;20](#NC20-constants-should-be-defined-rather-than-using-magic-numbers) | `constant`s should be defined rather than using magic numbers | 40 |
| [NC&#x2011;21](#NC21-constants/immutables-redefined-elsewhere) | `constant`s/`immutable`s redefined elsewhere | 40 |
| [NC&#x2011;22](#NC22-constructor-should-emit-an-event) | `constructor` should emit an event | 3 |
| [NC&#x2011;23](#NC23-contract-implements-interface-without-extending-the-interface) | Contract implements interface without extending the interface | 2 |
| [NC&#x2011;24](#NC24-contracts-containing-only-utility-functions-should-be-made-into-libraries) | Contracts containing only utility functions should be made into libraries | 1 |
| [NC&#x2011;25](#NC25-contracts-should-have-all-public/external-functions-exposed-by-interfaces) | Contracts should have all `public`/`external` functions exposed by `interface`s | 36 |
| [NC&#x2011;26](#NC26-contracts-should-have-full-test-coverage) | Contracts should have full test coverage | 1 |
| [NC&#x2011;27](#NC27-contracts/libraries/interfaces-should-each-be-defined-in-separate-files) | Contracts/libraries/interfaces should each be defined in separate files | 11 |
| [NC&#x2011;28](#NC28-control-structures-do-not-follow-the-solidity-style-guide) | Control structures do not follow the Solidity Style Guide | 40 |
| [NC&#x2011;29](#NC29-custom-error-without-details) | Custom `error` without details | 40 |
| [NC&#x2011;30](#NC30-custom-errors-should-be-used-rather-than-revert/require) | Custom errors should be used rather than `revert()`/`require()` | 40 |
| [NC&#x2011;31](#NC31-do-not-use-underscore-at-the-end-of-variable-name) | Do not use underscore at the end of variable name | 40 |
| [NC&#x2011;32](#NC32-do-not-use-underscore-in-struct-elements-names) | Do not use UNDERSCORE in `struct` elements names | 2 |
| [NC&#x2011;33](#NC33-else-block-not-required) | `else`-block not required | 12 |
| [NC&#x2011;34](#NC34-empty-bytes-check-is-missing) | Empty bytes check is missing | 40 |
| [NC&#x2011;35](#NC35-empty-function-body) | Empty function body | 1 |
| [NC&#x2011;36](#NC36-enum-names-should-be-descriptive-rather-than-cryptic) | `enum` names should be descriptive rather than cryptic | 1 |
| [NC&#x2011;37](#NC37-enum-values-should-be-used-instead-of-constant-array-indexes) | Enum values should be used instead of constant array indexes | 37 |
| [NC&#x2011;38](#NC38-error-messages-should-be-descriptive-rather-than-cryptic) | Error messages should be descriptive rather than cryptic | 2 |
| [NC&#x2011;39](#NC39-event-is-missing-indexed-fields) | Event is missing `indexed` fields | 39 |
| [NC&#x2011;40](#NC40-events-are-missing-sender-information) | Events are missing sender information | 24 |
| [NC&#x2011;41](#NC41-events-should-be-emitted-before-external-calls) | Events should be emitted before external calls | 33 |
| [NC&#x2011;42](#NC42-events-should-use-parameters-to-convey-information) | Events should use parameters to convey information | 2 |
| [NC&#x2011;43](#NC43-expressions-for-constant-values-should-use-immutable-rather-than-constant) | Expressions for `constant` values should use `immutable` rather than constant | 8 |
| [NC&#x2011;44](#NC44-extraneous-whitespace) | Extraneous whitespace | 6 |
| [NC&#x2011;45](#NC45-for-loops-in-public-or-external-functions-should-be-avoided-due-to-high-gas-costs-and-possible-dos) | For loops in `public` or `external` functions should be avoided due to high gas costs and possible DOS | 11 |
| [NC&#x2011;46](#NC46-function-called-does-not-exist-in-the-contract-interface) | Function called does not exist in the contract interface | 5 |
| [NC&#x2011;47](#NC47-function-ordering-in-the-contract-does-not-follow-the-solidity-style-guide) | Function ordering in the contract does not follow the Solidity style guide | 14 |
| [NC&#x2011;48](#NC48-functions-contain-the-same-code) | Functions contain the same code | 16 |
| [NC&#x2011;49](#NC49-functions-not-used-internally-could-be-marked-external) | Functions not used internally could be marked external | 40 |
| [NC&#x2011;50](#NC50-functions-should-be-named-in-mixedcase-style) | Functions should be named in mixedCase style | 16 |
| [NC&#x2011;51](#NC51-high-cyclomatic-complexity) | High cyclomatic complexity | 26 |
| [NC&#x2011;52](#NC52-if-statement-can-be-converted-to-a-ternary) | `if`-statement can be converted to a ternary | 16 |
| [NC&#x2011;53](#NC53-import-declarations-should-import-specific-identifiers-rather-than-the-whole-file) | Import declarations should import specific identifiers, rather than the whole file | 40 |
| [NC&#x2011;54](#NC54-imports-could-be-organized-more-systematically) | Imports could be organized more systematically | 28 |
| [NC&#x2011;55](#NC55-inconsistent-spacing-in-comments) | Inconsistent spacing in comments | 40 |
| [NC&#x2011;56](#NC56-initialisms-should-be-capitalized) | Initialisms should be capitalized | 5 |
| [NC&#x2011;57](#NC57-large-multiples-of-ten-should-use-scientific-notation) | Large multiples of ten should use scientific notation | 21 |
| [NC&#x2011;58](#NC58-large-numeric-literals-should-use-underscores-for-readability) | Large numeric literals should use underscores for readability | 23 |
| [NC&#x2011;59](#NC59-large-or-complicated-code-bases-should-implement-invariant-tests) | Large or complicated code bases should implement invariant tests | 1 |
| [NC&#x2011;60](#NC60-layout-order-does-not-comply-with-best-practices) | Layout order does not comply with best practices | 30 |
| [NC&#x2011;61](#NC61-libraries-should-be-defined-in-separate-files-from-their-usage) | Libraries should be defined in separate files from their usage | 3 |
| [NC&#x2011;62](#NC62-lines-are-too-long) | Lines are too long | 6 |
| [NC&#x2011;63](#NC63-long-functions-should-be-refactored-into-multiple-smaller-functions) | Long functions should be refactored into multiple, smaller, functions | 24 |
| [NC&#x2011;64](#NC64-make-use-of-soliditys-using-keyword) | Make use of Solidity's `using` keyword | 40 |
| [NC&#x2011;65](#NC65-minting-to-the-zero-address-should-be-avoided) | Minting to the zero address should be avoided | 9 |
| [NC&#x2011;66](#NC66-missing-checks-for-address0x0-in-the-constructor) | Missing checks for `address(0x0)` in the constructor | 3 |
| [NC&#x2011;67](#NC67-missing-checks-for-uint-state-variable-assignments) | Missing checks for uint state variable assignments | 7 |
| [NC&#x2011;68](#NC68-multiple-mappings-with-same-keys-can-be-combined-into-a-single-struct-mapping-for-readability) | Multiple mappings with same keys can be combined into a single struct mapping for readability | 10 |
| [NC&#x2011;69](#NC69-multiple-type-casts-create-complexity-within-the-code) | Multiple type casts create complexity within the code | 14 |
| [NC&#x2011;70](#NC70-named-imports-of-parent-contracts-are-missing) | Named imports of parent contracts are missing | 36 |
| [NC&#x2011;71](#NC71-names-of-private/internal-state-variables-should-be-prefixed-with-an-underscore) | Names of private/internal state variables should be prefixed with an underscore | 1 |
| [NC&#x2011;72](#NC72-names-of-structs-events-enums-and-errors-should-use-capwords-style) | Names of structs, events, enums and errors should use CapWords style | 12 |
| [NC&#x2011;73](#NC73-natspec-contract-declarations-should-have-@author-tags) | NatSpec: Contract declarations should have `@author` tags | 40 |
| [NC&#x2011;74](#NC74-natspec-contract-declarations-should-have-@dev-tags) | NatSpec: Contract declarations should have `@dev` tags | 40 |
| [NC&#x2011;75](#NC75-natspec-contract-declarations-should-have-@notice-tags) | NatSpec: Contract declarations should have `@notice` tags | 38 |
| [NC&#x2011;76](#NC76-natspec-contract-declarations-should-have-@title-tags) | NatSpec: Contract declarations should have `@title` tags | 3 |
| [NC&#x2011;77](#NC77-natspec-contract-declarations-should-have-natspec-descriptions) | NatSpec: Contract declarations should have NatSpec descriptions | 2 |
| [NC&#x2011;78](#NC78-natspec-error-declarations-should-have-@notice-tags) | NatSpec: Error declarations should have `@notice` tags | 40 |
| [NC&#x2011;79](#NC79-natspec-error-declarations-should-have-natspec-descriptions) | NatSpec: Error declarations should have NatSpec descriptions | 40 |
| [NC&#x2011;80](#NC80-natspec-error-missing-natspec-@dev-tag) | NatSpec: Error missing NatSpec `@dev` tag | 40 |
| [NC&#x2011;81](#NC81-natspec-error-missing-natspec-@param-tag) | NatSpec: Error missing NatSpec `@param` tag | 1 |
| [NC&#x2011;82](#NC82-natspec-event-declarations-should-have-@notice-tags) | NatSpec: Event declarations should have `@notice` tags | 4 |
| [NC&#x2011;83](#NC83-natspec-event-missing-natspec-@dev-tag) | NatSpec: Event missing NatSpec `@dev` tag | 40 |
| [NC&#x2011;84](#NC84-natspec-event-missing-natspec-@param-tag) | NatSpec: Event missing NatSpec `@param` tag | 37 |
| [NC&#x2011;85](#NC85-natspec-file-is-missing-natspec-documentation) | NatSpec: File is missing NatSpec Documentation | 2 |
| [NC&#x2011;86](#NC86-natspec-function-declarations-should-have-@notice-tags) | NatSpec: Function declarations should have `@notice` tags | 40 |
| [NC&#x2011;87](#NC87-natspec-function-declarations-should-have-natspec-descriptions) | NatSpec: Function declarations should have NatSpec descriptions | 40 |
| [NC&#x2011;88](#NC88-natspec-functions-missing-natspec-@dev-tag) | NatSpec: Functions missing NatSpec `@dev` tag | 40 |
| [NC&#x2011;89](#NC89-natspec-functions-missing-natspec-@param-tag) | NatSpec: Functions missing NatSpec `@param` tag | 40 |
| [NC&#x2011;90](#NC90-natspec-functions-missing-natspec-@return-tag) | NatSpec: Functions missing NatSpec `@return` tag | 40 |
| [NC&#x2011;91](#NC91-natspec-modifier-declarations-should-have-natspec-descriptions) | NatSpec: Modifier declarations should have NatSpec descriptions | 13 |
| [NC&#x2011;92](#NC92-natspec-modifier-missing-natspec-@dev-tag) | NatSpec: Modifier missing NatSpec `@dev` tag | 13 |
| [NC&#x2011;93](#NC93-natspec-modifier-missing-natspec-@param-tag) | NatSpec: Modifier missing NatSpec `@param` tag | 4 |
| [NC&#x2011;94](#NC94-natspec-use-@inheritdoc-rather-than-using-a-non-standard-tags) | Natspec: Use `@inheritdoc` rather than using a non-standard tags | 6 |
| [NC&#x2011;95](#NC95-non-assembly-method-available) | Non-assembly method available | 3 |
| [NC&#x2011;96](#NC96-non-external/public-function-names-should-begin-with-an-underscore) | Non-`external`/`public` function names should begin with an underscore | 40 |
| [NC&#x2011;97](#NC97-non-library/interface-files-should-use-fixed-compiler-versions-not-floating-ones) | Non-library/interface files should use fixed compiler versions, not floating ones | 40 |
| [NC&#x2011;98](#NC98-not-using-the-latest-versions-of-project-dependencies) | Not using the latest versions of project dependencies | 1 |
| [NC&#x2011;99](#NC99-not-using-the-named-return-variables-anywhere-in-the-function-is-confusing) | Not using the named return variables anywhere in the function is confusing | 7 |
| [NC&#x2011;100](#NC100-overly-complicated-arithmetic) | Overly complicated arithmetic | 14 |
| [NC&#x2011;101](#NC101-overridden-function-has-no-body) | Overridden function has no body | 1 |
| [NC&#x2011;102](#NC102-parameter-change-does-not-emit-event) | Parameter change does not emit event | 3 |
| [NC&#x2011;103](#NC103-place-interface-files-into-a-dedicated-folder) | Place `interface` files into a dedicated folder | 13 |
| [NC&#x2011;104](#NC104-polymorphic-functions-make-security-audits-more-time-consuming-and-error-prone) | Polymorphic functions make security audits more time-consuming and error-prone | 26 |
| [NC&#x2011;105](#NC105-prefer-skip-over-revert-model-in-iteration) | Prefer skip over revert model in iteration | 10 |
| [NC&#x2011;106](#NC106-public-functions-not-called-by-the-contract-should-be-declared-external-instead) | `public` functions not called by the contract should be declared `external` instead | 40 |
| [NC&#x2011;107](#NC107-receive/payable-fallback-function-does-not-authorize-requests) | `receive()`/`payable fallback()` function does not authorize requests | 2 |
| [NC&#x2011;108](#NC108-redundant-ierc20-import) | Redundant IERC20 import | 8 |
| [NC&#x2011;109](#NC109-redundant-inheritance-specifier) | Redundant inheritance specifier | 3 |
| [NC&#x2011;110](#NC110-redundant-negation) | Redundant negation | 5 |
| [NC&#x2011;111](#NC111-returning-a-struct-instead-of-a-bunch-of-variables-is-better) | Returning a struct instead of a bunch of variables is better | 5 |
| [NC&#x2011;112](#NC112-simplify-complex-require-statements) | Simplify complex require statements | 3 |
| [NC&#x2011;113](#NC113-some-contracts-can-be-abstract) | Some contracts can be abstract | 6 |
| [NC&#x2011;114](#NC114-some-events-are-never-emitted) | Some events are never emitted | 7 |
| [NC&#x2011;115](#NC115-some-variables-have-a-implicit-default-visibility) | Some variables have a implicit default visibility | 3 |
| [NC&#x2011;116](#NC116-state-variables-should-include-comments) | State variables should include comments | 40 |
| [NC&#x2011;117](#NC117-the-nonreentrant-modifier-should-occur-before-all-other-modifiers) | The `nonReentrant` `modifier` should occur before all other modifiers | 4 |
| [NC&#x2011;118](#NC118-top-level-declarations-should-be-separated-by-at-least-two-lines) | Top-level declarations should be separated by at least two lines | 40 |
| [NC&#x2011;119](#NC119-unnecessary-cast) | Unnecessary cast | 7 |
| [NC&#x2011;120](#NC120-unused-error-definition) | Unused `error` definition | 36 |
| [NC&#x2011;121](#NC121-unused-event-definition) | Unused `event` definition | 7 |
| [NC&#x2011;122](#NC122-unused-modifier-definition) | Unused `modifier` definition | 4 |
| [NC&#x2011;123](#NC123-unused-struct-definition) | Unused `struct` definition | 1 |
| [NC&#x2011;124](#NC124-unusual-loop-variable) | Unusual loop variable | 1 |
| [NC&#x2011;125](#NC125-upgradeable-contract-not-initialized) | Upgradeable contract not initialized | 6 |
| [NC&#x2011;126](#NC126-use-@inheritdoc-for-overridden-functions) | Use `@inheritdoc` for overridden functions | 40 |
| [NC&#x2011;127](#NC127-use-a-single-file-for-system-wide-constants) | Use a single file for system wide constants | 40 |
| [NC&#x2011;128](#NC128-use-a-struct-to-encapsulate-multiple-function-parameters) | Use a struct to encapsulate multiple function parameters | 16 |
| [NC&#x2011;129](#NC129-use-bytesconcat-on-bytes-instead-of-abiencodepacked-for-clearer-semantic-meaning) | Use `bytes.concat()` on bytes instead of `abi.encodePacked()` for clearer semantic meaning | 11 |
| [NC&#x2011;130](#NC130-use-delete-instead-of-assigning-values-to-false) | Use delete instead of assigning values to `false` | 2 |
| [NC&#x2011;131](#NC131-use-openzeppelins-merkleproof-rather-than-rolling-your-own) | Use OpenZeppelin's `MerkleProof` rather than rolling your own | 9 |
| [NC&#x2011;132](#NC132-use-openzeppelins-reentrancyguard/reentrancyguardupgradeable-rather-than-writing-your-own) | Use OpenZeppelin's `ReentrancyGuard`/`ReentrancyGuardUpgradeable` rather than writing your own | 1 |
| [NC&#x2011;133](#NC133-use-upper_case-for-immutable) | Use UPPER_CASE for `immutable` | 2 |
| [NC&#x2011;134](#NC134-variable-names-that-consist-of-all-capital-letters-should-be-reserved-for-constant/immutable-variables) | Variable names that consist of all capital letters should be reserved for `constant`/`immutable` variables | 1 |
| [NC&#x2011;135](#NC135-variable/struct/contract-names-should-be-descriptive-rather-than-cryptic) | `variable`/`struct`/`contract` names should be descriptive rather than cryptic | 40 |
| [NC&#x2011;136](#NC136-variables-need-not-be-initialized-to-zero) | Variables need not be initialized to zero | 12 |
| [NC&#x2011;137](#NC137-variables-should-be-named-in-mixedcase-style) | Variables should be named in mixedCase style | 40 |
| [NC&#x2011;138](#NC138-zero-as-a-function-argument-should-have-a-descriptive-meaning) | Zero as a function argument should have a descriptive meaning | 28 |

## Low


---
### [L&#x2011;1] Add to `blacklist` function
NFT thefts have increased recently, so with the addition of hacked NFTs to the platform, NFTs can be converted into liquidity. To prevent this, I recommend adding the blacklist function.

Marketplaces such as Opensea have a blacklist feature that will not list NFTs that have been reported theft, NFT projects such as Manifold have blacklist functions in their smart contracts.

Here is the project example; Manifold

Manifold Contract https://etherscan.io/address/0xe4e4003afe3765aca8149a82fc064c0b125b9e5a#code

```solidity
     modifier nonBlacklistRequired(address extension) {
         require(!_blacklistedExtensions.contains(extension), "Extension blacklisted");
         _;
     }
```

<details>
<summary><i>There are 5 instances of this issue:</i></summary>

```solidity
📁 File: contracts/team/airdrop/ERC721Airdrop.sol

9: contract ERC721Airdrop is MerkleClaimable { 
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L9)

```solidity
📁 File: contracts/tokenvault/BridgedERC1155.sol

14: contract BridgedERC1155 is EssentialContract, IERC1155MetadataURIUpgradeable, ERC1155Upgradeable { 
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L14)

```solidity
📁 File: contracts/tokenvault/BridgedERC721.sol

12: contract BridgedERC721 is EssentialContract, ERC721Upgradeable { 
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L12)

```solidity
📁 File: contracts/tokenvault/ERC1155Vault.sol

29: contract ERC1155Vault is BaseNFTVault, ERC1155ReceiverUpgradeable { 
```
[29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L29)

```solidity
📁 File: contracts/tokenvault/ERC721Vault.sol

16: contract ERC721Vault is BaseNFTVault, IERC721Receiver { 
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L16)

</details>


---
### [L&#x2011;2] Array is `push()`'ed but not `pop()`'ed
Array entries are added but are never removed. Consider whether this should be the case, or whether there should be a maximum, or whether old entries should be removed. Cases where there are specific potential problems will be flagged separately under a different issue.

It's a good practice to maintain control over the size of array state variables in Solidity, especially if they are dynamically updated. If a contract includes a mechanism to push items into an array, it should ideally also provide a mechanism to remove items. This is because Solidity arrays don't automatically shrink when items are deleted - their length needs to be manually adjusted.
Ignoring this can lead to bloated and inefficient contracts. For instance, iterating over a large array can cause your contract to hit the block gas limit. Additionally, if entries are only marked for deletion but never actually removed, you may end up dealing with stale or irrelevant data, which can cause logical errors.
Therefore, implementing a method to 'pop' items from arrays helps manage contract's state, improve efficiency and prevent potential issues related to gas limits or stale data. Always ensure to handle potential underflow conditions when popping elements from the array.



<i>There is one instance of this issue:</i>

```solidity
📁 File: contracts/L1/provers/Guardians.sol

87:             guardians.push(guardian); 
```
[87](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L87)


---
### [L&#x2011;3] Avoid shadowing state variables
Some state variables are shadowed by local variables/function parameters, this might result in the use of the wrong variable, in some scenarios. Consider renaming these variables with a different name.

<details>
<summary><i>There are 35 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoL1.sol

/// @audit Shadowing _owner from OwnableUpgradeable
43:         address _owner, 
```
[43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L43)

```solidity
📁 File: contracts/L1/TaikoToken.sol

/// @audit Shadowing _owner from OwnableUpgradeable
26:         address _owner, 
/// @audit Shadowing _name from ERC20Upgradeable
27:         string calldata _name,
/// @audit Shadowing _symbol from ERC20Upgradeable
28:         string calldata _symbol,
```
[26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L26-L28)

```solidity
📁 File: contracts/L1/gov/TaikoGovernor.sol

/// @audit Shadowing _owner from OwnableUpgradeable
32:         address _owner, 

/// @audit Shadowing _timelock from GovernorTimelockControlUpgradeable
34:         TimelockControllerUpgradeable _timelock 
```
[32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L32), [34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L34)

```solidity
📁 File: contracts/L1/gov/TaikoTimelockController.sol

/// @audit Shadowing _owner from OwnableUpgradeable
/// @audit Shadowing _minDelay from TimelockControllerUpgradeable
15:     function init(address _owner, uint256 _minDelay) external initializer { 
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L15)

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

/// @audit Shadowing _owner from OwnableUpgradeable
57:     function init(address _owner, address _addressManager) external initializer { 
```
[57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L57)

```solidity
📁 File: contracts/L1/provers/GuardianProver.sol

/// @audit Shadowing _owner from OwnableUpgradeable
25:     function init(address _owner, address _addressManager) external initializer { 
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L25)

```solidity
📁 File: contracts/L1/tiers/DevnetTierProvider.sol

/// @audit Shadowing _owner from OwnableUpgradeable
15:     function init(address _owner) external initializer { 
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L15)

```solidity
📁 File: contracts/L1/tiers/MainnetTierProvider.sol

/// @audit Shadowing _owner from OwnableUpgradeable
15:     function init(address _owner) external initializer { 
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L15)

```solidity
📁 File: contracts/L1/tiers/TestnetTierProvider.sol

/// @audit Shadowing _owner from OwnableUpgradeable
15:     function init(address _owner) external initializer { 
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L15)

```solidity
📁 File: contracts/L2/CrossChainOwned.sol

/// @audit Shadowing _owner from OwnableUpgradeable
61:         address _owner, 
```
[61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L61)

```solidity
📁 File: contracts/L2/TaikoL2.sol

/// @audit Shadowing _owner from OwnableUpgradeable
72:         address _owner, 
```
[72](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L72)

```solidity
📁 File: contracts/bridge/Bridge.sol

/// @audit Shadowing _owner from OwnableUpgradeable
75:     function init(address _owner, address _addressManager) external initializer { 
```
[75](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L75)

```solidity
📁 File: contracts/common/AddressManager.sol

/// @audit Shadowing _owner from OwnableUpgradeable
30:     function init(address _owner) external initializer { 
```
[30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L30)

```solidity
📁 File: contracts/common/EssentialContract.sol

/// @audit Shadowing _owner from OwnableUpgradeable
96:         address _owner, 

/// @audit Shadowing _owner from OwnableUpgradeable
109:     function __Essential_init(address _owner) internal virtual { 
```
[96](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L96), [109](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L109)

```solidity
📁 File: contracts/signal/SignalService.sol

/// @audit Shadowing _owner from OwnableUpgradeable
48:     function init(address _owner, address _addressManager) external initializer { 
```
[48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L48)

```solidity
📁 File: contracts/team/TimelockTokenPool.sol

/// @audit Shadowing _owner from OwnableUpgradeable
112:         address _owner, 
```
[112](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L112)

```solidity
📁 File: contracts/team/airdrop/ERC20Airdrop.sol

/// @audit Shadowing _owner from OwnableUpgradeable
28:         address _owner, 
```
[28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L28)

```solidity
📁 File: contracts/team/airdrop/ERC20Airdrop2.sol

/// @audit Shadowing _owner from OwnableUpgradeable
55:         address _owner, 
```
[55](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L55)

```solidity
📁 File: contracts/team/airdrop/ERC721Airdrop.sol

/// @audit Shadowing _owner from OwnableUpgradeable
26:         address _owner, 
```
[26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L26)

```solidity
📁 File: contracts/tokenvault/BaseVault.sol

/// @audit Shadowing _owner from OwnableUpgradeable
32:     function init(address _owner, address _addressManager) external initializer { 
```
[32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L32)

```solidity
📁 File: contracts/tokenvault/BridgedERC1155.sol

/// @audit Shadowing _owner from OwnableUpgradeable
39:         address _owner, 
```
[39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L39)

```solidity
📁 File: contracts/tokenvault/BridgedERC20.sol

/// @audit Shadowing _owner from OwnableUpgradeable
53:         address _owner, 

/// @audit Shadowing _symbol from ERC20Upgradeable
58:         string memory _symbol, 
/// @audit Shadowing _name from ERC20Upgradeable
59:         string memory _name
```
[53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L53), [58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L58-L59)

```solidity
📁 File: contracts/tokenvault/BridgedERC721.sol

/// @audit Shadowing _owner from OwnableUpgradeable
32:         address _owner, 

/// @audit Shadowing _symbol from ERC721Upgradeable
36:         string memory _symbol, 
/// @audit Shadowing _name from ERC721Upgradeable
37:         string memory _name
```
[32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L32), [36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L36-L37)

```solidity
📁 File: contracts/tokenvault/adapters/USDCAdapter.sol

/// @audit Shadowing _owner from OwnableUpgradeable
38:     function init(address _owner, address _addressManager, IUSDC _usdc) external initializer { 
```
[38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L38)

```solidity
📁 File: contracts/verifiers/GuardianVerifier.sol

/// @audit Shadowing _owner from OwnableUpgradeable
18:     function init(address _owner, address _addressManager) external initializer { 
```
[18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L18)

```solidity
📁 File: contracts/verifiers/SgxVerifier.sol

/// @audit Shadowing _owner from OwnableUpgradeable
83:     function init(address _owner, address _addressManager) external initializer { 
```
[83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L83)

</details>


---
### [L&#x2011;4] Avoid using `tx.origin`
`tx.origin` is a global variable in Solidity that returns the address of the account that sent the transaction.
Using the variable could make a contract vulnerable if an authorized account calls a malicious contract. You can impersonate a user using a third party contract.
This can make it easier to create a vault on behalf of another user with an external administrator (by receiving it as an argument).


<i>There is one instance of this issue:</i>

```solidity
📁 File: contracts/libs/LibAddress.sol

78:         return msg.sender == tx.origin; 
```
[78](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L78)


---
### [L&#x2011;5] `block.number` means different things on different L2s
On Optimism, `block.number` is the L2 block number, but on Arbitrum, it's the L1 block number, and `ArbSys(address(100)).arbBlockNumber()` must be used. Furthermore, L2 block numbers often occur much more frequently than L1 block numbers (any may even occur on a per-transaction basis), so using block numbers for timing results in inconsistencies, especially when voting is involved across multiple chains. As of version 4.9, OpenZeppelin has <a href="https://blog.openzeppelin.com/introducing-openzeppelin-contracts-v4.9#governor">modified</a> their governor code to use a clock rather than block numbers, to avoid these sorts of issues, but this still requires that the project <a href="https://docs.openzeppelin.com/contracts/4.x/governance#token_2">implement</a> a <a href="https://eips.ethereum.org/EIPS/eip-6372">clock</a> for each L2.

<details>
<summary><i>There are 14 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

86:                 || assignment.maxProposedIn != 0 && block.number > assignment.maxProposedIn 
```
[86](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L86)

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

122:                 l1Hash: blockhash(block.number - 1), 

131:                 l1Height: uint64(block.number - 1), 

204:         meta_.difficulty = keccak256(abi.encodePacked(block.prevrandao, b.numBlocks, block.number)); 

220:             proposedIn: uint64(block.number), 
```
[122](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L122), [131](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L131), [204](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L204), [220](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L220)

```solidity
📁 File: contracts/L1/libs/LibVerifying.sol

57:         _state.slotA.genesisHeight = uint64(block.number); 
```
[57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L57)

```solidity
📁 File: contracts/L2/TaikoL2.sol

86:         if (block.number == 0) { 

88:         } else if (block.number == 1) { 

90:             uint256 parentHeight = block.number - 1; 

97:         (publicInputHash,) = _calcPublicInputHash(block.number); 

118:                 || (block.number != 1 && _parentGasUsed == 0) 

127:             parentId = block.number - 1; 

201:         if (_blockId >= block.number) return 0; 
202:         if (_blockId + 256 >= block.number) return blockhash(_blockId);
```
[86](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L86), [88](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L88), [90](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L90), [97](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L97), [118](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L118), [127](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L127), [201](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L201-L202)

</details>


---
### [L&#x2011;6] Calling `bytes.concat()` with final arguments that may differ in length, may cause hash collisions
`bytes3(bytes2(uint16(1)))` and `bytes3(bytes3(uint24(256)))` both are equal to `0x000100`, and if they each were passed to a function used them as the last argument to `bytes.concat()`, which is the case below, the resulting bytes would be equivalent. When this sort of function is a part of a general-purpose library, or is a part of a standard, and is used for e.g. indexing storage slots, it's possible for two byte values to map to the same location. There is no safe way to ensure the caller hasn't cast bytes from a smaller size. The suggested fix is to require that the input be the result of a call to `keccak256(abi.encode(<value>))`, and truncate the extra bytes of entropy if a specific size is absolutely needed.

<details>
<summary><i>There are 3 instances of this issue:</i></summary>

```solidity
📁 File: contracts/automata-attestation/utils/RsaVerify.sol

94:             bytes.concat(bytes32(_s.length), bytes32(_e.length), bytes32(_m.length), _s, _e, _m); 

242:             bytes.concat(bytes32(_s.length), bytes32(_e.length), bytes32(_m.length), _s, _e, _m); 
```
[94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L94), [242](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L242)

```solidity
📁 File: contracts/libs/LibTrieProof.sol

61:             bytes.concat(_slot), RLPWriter.writeUint(uint256(_value)), _storageProof, storageRoot_ 
```
[61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L61)

</details>


---
### [L&#x2011;7] Centralization risk for trusted owners
Contracts have owners with privileged rights to perform admin tasks and need to be trusted to not perform malicious updates or drain funds.

<details>
<summary><i>There are 21 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoToken.sol

/// @audit onlyOwner
47:     function burn(address _from, uint256 _amount) public onlyOwner { 
```
[47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L47)

```solidity
📁 File: contracts/L1/provers/Guardians.sol

/// @audit onlyOwner
53:     function setGuardians( 
54:         address[] memory _newGuardians,
55:         uint8 _minGuardians
56:     )
57:         external
58:         onlyOwner
59:         nonReentrant
60:     {
```
[53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L53-L60)

```solidity
📁 File: contracts/L2/TaikoL2EIP1559Configurable.sol

/// @audit onlyOwner
25:     function setConfigAndExcess( 
26:         Config memory _newConfig,
27:         uint64 _newGasExcess
28:     )
29:         external
30:         virtual
31:         onlyOwner
32:     {
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L25-L32)

```solidity
📁 File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

/// @audit onlyOwner
65:     function setMrSigner(bytes32 _mrSigner, bool _trusted) external onlyOwner { 

/// @audit onlyOwner
69:     function setMrEnclave(bytes32 _mrEnclave, bool _trusted) external onlyOwner { 

/// @audit onlyOwner
73:     function addRevokedCertSerialNum( 
74:         uint256 index,
75:         bytes[] calldata serialNumBatch
76:     )
77:         external
78:         onlyOwner
79:     {

/// @audit onlyOwner
88:     function removeRevokedCertSerialNum( 
89:         uint256 index,
90:         bytes[] calldata serialNumBatch
91:     )
92:         external
93:         onlyOwner
94:     {

/// @audit onlyOwner
103:     function configureTcbInfoJson( 
104:         string calldata fmspc,
105:         TCBInfoStruct.TCBInfo calldata tcbInfoInput
106:     )
107:         public
108:         onlyOwner
109:     {

/// @audit onlyOwner
114:     function configureQeIdentityJson(EnclaveIdStruct.EnclaveId calldata qeIdentityInput) 
115:         external
116:         onlyOwner
117:     {

/// @audit onlyOwner
122:     function toggleLocalReportCheck() external onlyOwner { 
```
[65](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L65), [69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L69), [73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L73-L79), [88](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L88-L94), [103](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L103-L109), [114](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L114-L117), [122](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L122)

```solidity
📁 File: contracts/common/AddressManager.sol

/// @audit onlyOwner
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
[38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L38-L46)

```solidity
📁 File: contracts/common/EssentialContract.sol

/// @audit onlyOwner
114:     function _authorizeUpgrade(address) internal virtual override onlyOwner { } 

/// @audit onlyOwner
116:     function _authorizePause(address) internal virtual onlyOwner { } 
```
[114](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L114), [116](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L116)

```solidity
📁 File: contracts/signal/SignalService.sol

/// @audit onlyOwner
56:     function authorize(address _addr, bool _authorize) external onlyOwner { 
```
[56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L56)

```solidity
📁 File: contracts/team/TimelockTokenPool.sol

/// @audit onlyOwner
135:     function grant(address _recipient, Grant memory _grant) external onlyOwner { 

/// @audit onlyOwner
150:     function void(address _recipient) external onlyOwner { 
```
[135](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L135), [150](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L150)

```solidity
📁 File: contracts/team/airdrop/MerkleClaimable.sol

/// @audit onlyOwner
45:     function setConfig( 
46:         uint64 _claimStart,
47:         uint64 _claimEnd,
48:         bytes32 _merkleRoot
49:     )
50:         external
51:         onlyOwner
52:     {
```
[45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L45-L52)

```solidity
📁 File: contracts/tokenvault/BridgedERC20.sol

/// @audit onlyOwner
80:     function setSnapshoter(address _snapshooter) external onlyOwner { 

/// @audit onlyOwnerOrSnapshooter
85:     function snapshot() external onlyOwnerOrSnapshooter { 
```
[80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L80), [85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L85)

```solidity
📁 File: contracts/tokenvault/ERC20Vault.sol

/// @audit onlyOwner
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
```
[148](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L148-L157)

```solidity
📁 File: contracts/verifiers/SgxVerifier.sol

/// @audit onlyOwner
90:     function addInstances(address[] calldata _instances) 
91:         external
92:         onlyOwner
93:         returns (uint256[] memory)
94:     {
```
[90](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L90-L94)

</details>


---
### [L&#x2011;8] Consider bounding input array length
The functions below take in an unbounded array, and make function calls for entries in the array. While the function will revert if it eventually runs out of gas, it may be a nicer user experience to `require()` that the length of the array is below some reasonable maximum, so that the user doesn't have to use up a full transaction's gas only to see that the transaction reverts.

<details>
<summary><i>There are 5 instances of this issue:</i></summary>

```solidity
📁 File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

/// @audit serialNumBatch.length not bounded
80:         for (uint256 i; i < serialNumBatch.length; ++i) { 
81:             if (_serialNumIsRevoked[index][serialNumBatch[i]]) {
82:                 continue;
83:             }
84:             _serialNumIsRevoked[index][serialNumBatch[i]] = true;
85:         }

/// @audit serialNumBatch.length not bounded
95:         for (uint256 i; i < serialNumBatch.length; ++i) { 
96:             if (!_serialNumIsRevoked[index][serialNumBatch[i]]) {
97:                 continue;
98:             }
99:             delete _serialNumIsRevoked[index][serialNumBatch[i]];
100:         }
```
[80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L80-L85), [95](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L95-L100)

```solidity
📁 File: contracts/bridge/Bridge.sol

/// @audit _msgHashes.length not bounded
90:         for (uint256 i; i < _msgHashes.length; ++i) { 
91:             bytes32 msgHash = _msgHashes[i];
92:             proofReceipt[msgHash].receivedAt = _timestamp;
93:             emit MessageSuspended(msgHash, _suspend);
94:         }
```
[90](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L90-L94)

```solidity
📁 File: contracts/team/airdrop/ERC721Airdrop.sol

/// @audit tokenIds.length not bounded
59:         for (uint256 i; i < tokenIds.length; ++i) { 
60:             IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);
61:         }
```
[59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59-L61)

```solidity
📁 File: contracts/verifiers/SgxVerifier.sol

/// @audit _ids.length not bounded
104:         for (uint256 i; i < _ids.length; ++i) { 
105:             uint256 idx = _ids[i];
106: 
107:             if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();
108: 
109:             emit InstanceDeleted(idx, instances[idx].addr);
110: 
111:             delete instances[idx];
112:         }
```
[104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L104-L112)

</details>


---
### [L&#x2011;9] Consider disabling `renounceOwnership()`
Typically, the contract's owner is the account that deploys the contract. As a result, the owner is able to perform certain privileged activities. The OpenZeppelin's `Ownable` is used in this project contract implements `renounceOwnership`. This can represent a certain risk if the ownership is renounced for any other reason than by design. Renouncing ownership will leave the contract without an owner, thereby removing any functionality that is only available to the owner.


<i>There is one instance of this issue:</i>

```solidity
📁 File: contracts/common/EssentialContract.sol

10: abstract contract EssentialContract is UUPSUpgradeable, Ownable2StepUpgradeable, AddressResolver { 
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L10)


---
### [L&#x2011;10] Consider implementing two-step procedure for updating protocol addresses
A copy-paste error or a typo may end up bricking protocol functionality, or sending tokens to an address with no known private key. Consider implementing a two-step procedure for updating protocol addresses, where the recipient is set as pending, and must 'accept' the assignment by making an affirmative call. A straight forward way of doing this would be to have the target contracts implement [EIP-165](https://eips.ethereum.org/EIPS/eip-165), and to have the 'set' functions ensure that the recipient is of the right interface type.

<details>
<summary><i>There are 2 instances of this issue:</i></summary>

```solidity
📁 File: contracts/common/AddressManager.sol

/// @audit line 49
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
[38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L38-L51)

```solidity
📁 File: contracts/tokenvault/BridgedERC20.sol

/// @audit line 81
80:     function setSnapshoter(address _snapshooter) external onlyOwner { 
81:         snapshooter = _snapshooter;
82:     }
```
[80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L80-L82)

</details>


---
### [L&#x2011;11] `constructor`/`initialize` function lacks parameter validation
Constructors and initialization functions play a critical role in contracts by setting important initial states when the contract is first deployed before the system starts. The parameters passed to the constructor and initialization functions directly affect the behavior of the contract / protocol. If incorrect parameters are provided, the system may fail to run, behave abnormally, be unstable, or lack security. Therefore, it's crucial to carefully check each parameter in the constructor and initialization functions. If an exception is found, the transaction should be rolled back.

<details>
<summary><i>There are 2 instances of this issue:</i></summary>

```solidity
📁 File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

/// @audit sigVerifyLibAddr , pemCertLibAddr 
54:     constructor(address sigVerifyLibAddr, address pemCertLibAddr) { 
```
[54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L54)

```solidity
📁 File: contracts/automata-attestation/utils/SigVerifyLib.sol

/// @audit es256Verifier 
20:     constructor(address es256Verifier) { 
```
[20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L20)

</details>


---
### [L&#x2011;12] Critical functions should be controlled by time locks
It is a good practice to give time for users to react and adjust to critical changes. A timelock provides more guarantees and reduces the level of trust required, thus decreasing risk for users. It also indicates that the project is legitimate (less risk of a malicious owner making a sandwich attack on a user).

<details>
<summary><i>There are 3 instances of this issue:</i></summary>

```solidity
📁 File: contracts/common/AddressResolver.sol

58:     function __AddressResolver_init(address _addressManager) internal virtual onlyInitializing { 
59:         if (block.chainid > type(uint64).max) {
60:             revert RESOLVER_UNEXPECTED_CHAINID();
61:         }
62:         addressManager = _addressManager;
63:     }
```
[58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L58-L63)

```solidity
📁 File: contracts/common/EssentialContract.sol

114:     function _authorizeUpgrade(address) internal virtual override onlyOwner { } 
```
[114](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L114)

```solidity
📁 File: contracts/tokenvault/BridgedERC20.sol

80:     function setSnapshoter(address _snapshooter) external onlyOwner { 
81:         snapshooter = _snapshooter;
82:     }
```
[80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L80-L82)

</details>


---
### [L&#x2011;13] `decimals()` is not a part of the ERC-20 standard
The `decimals()` function is not a part of the [ERC-20 standard](https://eips.ethereum.org/EIPS/eip-20), and was added later as an [optional extension](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC20/extensions/IERC20Metadata.sol). As such, some valid ERC20 tokens do not support this interface, so it is unsafe to blindly cast all tokens to this interface, and then call this function.


<i>There is one instance of this issue:</i>

```solidity
📁 File: contracts/tokenvault/ERC20Vault.sol

368:                 decimals: meta.decimals(), 
```
[368](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L368)


---
### [L&#x2011;14] Division by zero not prevented
The divisions below take an input parameter which does not have any zero-value checks, which may lead to the functions reverting when zero is passed.

<details>
<summary><i>There are 2 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L2/Lib1559Math.sol

41:         uint256 input = _gasExcess * LibFixedPointMath.SCALING_FACTOR / _adjustmentFactor; 
```
[41](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L41)

```solidity
📁 File: contracts/team/TimelockTokenPool.sol

264:         return _amount * uint64(block.timestamp - _start) / _period; 
```
[264](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L264)

</details>


---
### [L&#x2011;15] External calls in an un-bounded `for`-loop may result in a DOS
Consider limiting the number of iterations in `for`-loops that make external calls

<details>
<summary><i>There are 9 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

/// @audit line 253
244:             for (uint256 i; i < params.hookCalls.length; ++i) { 
245:                 if (uint160(prevHook) >= uint160(params.hookCalls[i].hook)) {
246:                     revert L1_INVALID_HOOK();
247:                 }
248: 
249:                 // When a hook is called, all ether in this contract will be send to the hook.
250:                 // If the ether sent to the hook is not used entirely, the hook shall send the Ether
251:                 // back to this contract for the next hook to use.
252:                 // Proposers shall choose use extra hooks wisely.
253:                 IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }(
254:                     blk, meta_, params.hookCalls[i].data
255:                 );
256: 
257:                 prevHook = params.hookCalls[i].hook;
258:             }
```
[244](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L244-L258)

```solidity
📁 File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

/// @audit line 424
420:             for (uint256 i; i < 3; ++i) { 
421:                 bool isPckCert = i == 0; // additional parsing for PCKCert
422:                 bool certDecodedSuccessfully;
423:                 // todo! move decodeCert offchain
424:                 (certDecodedSuccessfully, parsedQuoteCerts[i]) = pemCertLib.decodeCert(
425:                     authDataV3.certification.decodedCertDataArray[i], isPckCert
426:                 );
427:                 if (!certDecodedSuccessfully) {
428:                     return (false, retData);
429:                 }
430:             }
```
[420](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L420-L430)

```solidity
📁 File: contracts/team/airdrop/ERC721Airdrop.sol

/// @audit line 60
59:         for (uint256 i; i < tokenIds.length; ++i) { 
60:             IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);
61:         }
```
[59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59-L61)

```solidity
📁 File: contracts/tokenvault/ERC1155Vault.sol

/// @audit line 252
251:                 for (uint256 i; i < _op.tokenIds.length; ++i) { 
252:                     BridgedERC1155(_op.token).burn(_user, _op.tokenIds[i], _op.amounts[i]);
253:                 }

/// @audit line 270
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
[251](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L251-L253), [269](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L269-L277)

```solidity
📁 File: contracts/tokenvault/ERC721Vault.sol

/// @audit line 171
170:             for (uint256 i; i < _tokenIds.length; ++i) { 
171:                 IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);
172:             }

/// @audit line 176
175:             for (uint256 i; i < _tokenIds.length; ++i) { 
176:                 BridgedERC721(token_).mint(_to, _tokenIds[i]);
177:             }

/// @audit line 198
197:                 for (uint256 i; i < _op.tokenIds.length; ++i) { 
198:                     BridgedERC721(_op.token).burn(_user, _op.tokenIds[i]);
199:                 }

/// @audit line 211
210:                 for (uint256 i; i < _op.tokenIds.length; ++i) { 
211:                     t.safeTransferFrom(_user, address(this), _op.tokenIds[i]);
212:                 }
```
[170](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L170-L172), [175](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L175-L177), [197](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L197-L199), [210](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L210-L212)

</details>


---
### [L&#x2011;16] Functions calling contracts/addresses with transfer hooks are missing reentrancy guards
Adherence to the check-effects-interaction pattern is commendable, but without a reentrancy guard in functions, especially with transfer hooks, users are exposed to read-only reentrancy risks. This can lead to malicious actions without altering the contract state. Adding a reentrancy guard is vital for security, protecting against both traditional and read-only reentrancy attacks, ensuring a robust and safe protocol.

<details>
<summary><i>There are 3 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoToken.sol

/// @audit transfer() on line 62
60:     function transfer(address _to, uint256 _amount) public override returns (bool) { 

/// @audit transferFrom() on line 80
70:     function transferFrom( 
```
[60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L60), [70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L70)

```solidity
📁 File: contracts/team/airdrop/ERC20Airdrop2.sol

/// @audit transferFrom() on line 91
88:     function withdraw(address user) external ongoingWithdrawals { 
```
[88](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L88)

</details>


---
### [L&#x2011;17] Int casting `block.timestamp` can reduce the lifespan of a contract
<details>
<summary><i>There are 12 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoL1.sol

126:         state.slotB.lastUnpausedAt = uint64(block.timestamp); 
```
[126](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L126)

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

130:                 timestamp: uint64(block.timestamp), 
```
[130](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L130)

```solidity
📁 File: contracts/L1/libs/LibProving.sol

78:             _state.slotB.lastUnpausedAt = uint64(block.timestamp); 

264:         ts.timestamp = uint64(block.timestamp); 
```
[78](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L78), [264](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L264)

```solidity
📁 File: contracts/L1/libs/LibVerifying.sol

58:         _state.slotA.genesisTimestamp = uint64(block.timestamp); 

64:         blk.proposedAt = uint64(block.timestamp); 

71:         ts.timestamp = uint64(block.timestamp); 
```
[58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L58), [64](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L64), [71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L71)

```solidity
📁 File: contracts/bridge/Bridge.sol

89:         uint64 _timestamp = _suspend ? type(uint64).max : uint64(block.timestamp); 

183:             receivedAt = uint64(block.timestamp); 

240:             receivedAt = uint64(block.timestamp); 
```
[89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L89), [183](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L183), [240](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L240)

```solidity
📁 File: contracts/verifiers/SgxVerifier.sol

204:         uint64 validSince = uint64(block.timestamp); 

229:         instances[id] = Instance(newInstance, uint64(block.timestamp)); 
```
[204](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L204), [229](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L229)

</details>


---
### [L&#x2011;18] Loss of precision
Division by large numbers may result in the result being zero, due to solidity not supporting fractions. Consider requiring a minimum amount for the numerator to ensure that it is always larger than the denominator

<details>
<summary><i>There are 2 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L2/Lib1559Math.sol

28:         return _ethQty(_gasExcess, _adjustmentFactor) / LibFixedPointMath.SCALING_FACTOR 
```
[28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L28)

```solidity
📁 File: contracts/thirdparty/solmate/LibFixedPointMath.sol

39:             int256 k = ((x << 96) / 54_916_777_467_707_473_351_141_471_128 + 2 ** 95) >> 96; 
```
[39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L39)

</details>


---
### [L&#x2011;19] Minting in a loop may lead to a DOS
The signature being used appears to require that all NFTs be minted at once. If there are a lot of them, the there may be too many to mint in one block


<i>There is one instance of this issue:</i>

```solidity
📁 File: contracts/tokenvault/ERC721Vault.sol

/// @audit mint
175:             for (uint256 i; i < _tokenIds.length; ++i) { 
176:                 BridgedERC721(token_).mint(_to, _tokenIds[i]);
177:             }
```
[175](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L175-L177)


---
### [L&#x2011;20] Missing checks for `address(0)` when assigning values to address state variables
<details>
<summary><i>There are 12 instances of this issue:</i></summary>

```solidity
📁 File: contracts/automata-attestation/utils/SigVerifyLib.sol

21:         ES256VERIFIER = es256Verifier; 
```
[21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L21)

```solidity
📁 File: contracts/common/AddressResolver.sol

62:         addressManager = _addressManager; 
```
[62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L62)

```solidity
📁 File: contracts/team/airdrop/ERC20Airdrop.sol

41:         token = _token; 
42:         vault = _vault;
```
[41](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L41-L42)

```solidity
📁 File: contracts/team/airdrop/ERC20Airdrop2.sol

69:         token = _token; 
70:         vault = _vault;
```
[69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L69-L70)

```solidity
📁 File: contracts/team/airdrop/ERC721Airdrop.sol

39:         token = _token; 
40:         vault = _vault;
```
[39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L39-L40)

```solidity
📁 File: contracts/tokenvault/BridgedERC1155.sol

56:         srcToken = _srcToken; 
```
[56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L56)

```solidity
📁 File: contracts/tokenvault/BridgedERC20.sol

73:         srcToken = _srcToken; 

81:         snapshooter = _snapshooter; 
```
[73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L73), [81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L81)

```solidity
📁 File: contracts/tokenvault/BridgedERC721.sol

47:         srcToken = _srcToken; 
```
[47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L47)

</details>


---
### [L&#x2011;21] Missing contract-existence checks before yul `call()`
Low-level calls return success if there is no code present at the specified address. In addition to the zero-address checks, add a check to verify that `extcodesize()` is non-zero.


<i>There is one instance of this issue:</i>

```solidity
📁 File: contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol

/// @audit call() on line 45
43:         assembly { 
44:             _success :=
45:                 call(
46:                     _gas, // gas
47:                     _target, // recipient
48:                     _value, // ether value
49:                     add(_calldata, 0x20), // inloc
50:                     mload(_calldata), // inlen
51:                     0, // outloc
52:                     0 // outlen
53:                 )
54:             // limit our copy to 256 bytes
55:             _toCopy := returndatasize()
56:             if gt(_toCopy, _maxCopy) { _toCopy := _maxCopy }
57:             // Store the length of the copied bytes
58:             mstore(_returnData, _toCopy)
59:             // copy the bytes from returndata[0:_toCopy]
60:             returndatacopy(add(_returnData, 0x20), 0, _toCopy)
61:         }
```
[43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L43-L61)


---
### [L&#x2011;22] Missing `_disableInitializer()` in upgradeable constructor body
Avoid leaving a contract uninitialized.
An uninitialized contract can be taken over by an attacker. This applies to both a proxy and its implementation contract, which may impact the proxy. To prevent the implementation contract from being used, you should invoke the `_disableInitializers()` function in the constructor to automatically lock it when it is deployed.

<details>
<summary><i>There are 9 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoToken.sol

15: contract TaikoToken is EssentialContract, ERC20SnapshotUpgradeable, ERC20VotesUpgradeable { 
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L15)

```solidity
📁 File: contracts/L1/gov/TaikoGovernor.sol

16: contract TaikoGovernor is 
17:     EssentialContract,
18:     GovernorCompatibilityBravoUpgradeable,
19:     GovernorVotesUpgradeable,
20:     GovernorVotesQuorumFractionUpgradeable,
21:     GovernorTimelockControlUpgradeable
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L16-L21)

```solidity
📁 File: contracts/L1/gov/TaikoTimelockController.sol

9: contract TaikoTimelockController is EssentialContract, TimelockControllerUpgradeable { 
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L9)

```solidity
📁 File: contracts/common/AddressResolver.sol

11: abstract contract AddressResolver is IAddressResolver, Initializable { 
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L11)

```solidity
📁 File: contracts/tokenvault/BaseVault.sol

12: abstract contract BaseVault is 
13:     EssentialContract,
14:     IRecallableSender,
15:     IMessageInvocable,
16:     IERC165Upgradeable
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L12-L16)

```solidity
📁 File: contracts/tokenvault/BridgedERC1155.sol

14: contract BridgedERC1155 is EssentialContract, IERC1155MetadataURIUpgradeable, ERC1155Upgradeable { 
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L14)

```solidity
📁 File: contracts/tokenvault/BridgedERC20.sol

15: contract BridgedERC20 is 
16:     BridgedERC20Base,
17:     IERC20MetadataUpgradeable,
18:     ERC20SnapshotUpgradeable,
19:     ERC20VotesUpgradeable
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L15-L19)

```solidity
📁 File: contracts/tokenvault/BridgedERC721.sol

12: contract BridgedERC721 is EssentialContract, ERC721Upgradeable { 
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L12)

```solidity
📁 File: contracts/tokenvault/ERC1155Vault.sol

29: contract ERC1155Vault is BaseNFTVault, ERC1155ReceiverUpgradeable { 
```
[29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L29)

</details>


---
### [L&#x2011;23] Missing zero address check in functions with address parameters
Adding a zero address check for each address type parameter can prevent errors.

<details>
<summary><i>There are 40 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoL1.sol

/// @audit _owner, _addressManager
42:     function init( 
43:         address _owner,
44:         address _addressManager,
45:         bytes32 _genesisBlockHash
46:     )
47:         external
48:         initializer
49:     {

/// @audit _recipient
119:     function depositEtherToL2(address _recipient) external payable nonReentrant whenNotPaused { 
```
[42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L42-L49), [119](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L119)

```solidity
📁 File: contracts/L1/TaikoToken.sol

/// @audit _owner, _recipient
25:     function init( 
26:         address _owner,
27:         string calldata _name,
28:         string calldata _symbol,
29:         address _recipient
30:     )
31:         public
32:         initializer
33:     {

/// @audit _from
47:     function burn(address _from, uint256 _amount) public onlyOwner { 

/// @audit _to
60:     function transfer(address _to, uint256 _amount) public override returns (bool) { 

/// @audit _from, _to
70:     function transferFrom( 
71:         address _from,
72:         address _to,
73:         uint256 _amount
74:     )
75:         public
76:         override
77:         returns (bool)
78:     {

/// @audit _from, _to
83:     function _beforeTokenTransfer( 
84:         address _from,
85:         address _to,
86:         uint256 _amount
87:     )
88:         internal
89:         override(ERC20Upgradeable, ERC20SnapshotUpgradeable)
90:     {

/// @audit _from, _to
94:     function _afterTokenTransfer( 
95:         address _from,
96:         address _to,
97:         uint256 _amount
98:     )
99:         internal
100:         override(ERC20Upgradeable, ERC20VotesUpgradeable)
101:     {

/// @audit _to
105:     function _mint( 
106:         address _to,
107:         uint256 _amount
108:     )
109:         internal
110:         override(ERC20Upgradeable, ERC20VotesUpgradeable)
111:     {

/// @audit _from
115:     function _burn( 
116:         address _from,
117:         uint256 _amount
118:     )
119:         internal
120:         override(ERC20Upgradeable, ERC20VotesUpgradeable)
121:     {
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L25-L33), [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L47), [60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L60), [70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L70-L78), [83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L83-L90), [94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L94-L101), [105](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L105-L111), [115](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L115-L121)

```solidity
📁 File: contracts/L1/gov/TaikoGovernor.sol

/// @audit _owner
31:     function init( 
32:         address _owner,
33:         IVotesUpgradeable _token,
34:         TimelockControllerUpgradeable _timelock
35:     )
36:         external
37:         initializer
38:     {
```
[31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L31-L38)

```solidity
📁 File: contracts/L1/gov/TaikoTimelockController.sol

/// @audit _owner
15:     function init(address _owner, uint256 _minDelay) external initializer { 
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L15)

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

/// @audit _owner, _addressManager
57:     function init(address _owner, address _addressManager) external initializer { 

/// @audit _taikoL1Address
137:     function hashAssignment( 
138:         ProverAssignment memory _assignment,
139:         address _taikoL1Address,
140:         bytes32 _blobHash
141:     )
142:         public
143:         view
144:         returns (bytes32)
145:     {
```
[57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L57), [137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L137-L145)

```solidity
📁 File: contracts/L1/libs/LibDepositing.sol

/// @audit _recipient
29:     function depositEtherToL2( 
30:         TaikoData.State storage _state,
31:         TaikoData.Config memory _config,
32:         IAddressResolver _resolver,
33:         address _recipient
34:     )
35:         internal
36:     {

/// @audit _feeRecipient
67:     function processDeposits( 
68:         TaikoData.State storage _state,
69:         TaikoData.Config memory _config,
70:         address _feeRecipient
71:     )
72:         internal
73:         returns (TaikoData.EthDeposit[] memory deposits_)
74:     {

/// @audit _addr
149:     function _encodeEthDeposit(address _addr, uint256 _amount) private pure returns (uint256) { 
```
[29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L29-L36), [67](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L67-L74), [149](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L149)

```solidity
📁 File: contracts/L1/provers/GuardianProver.sol

/// @audit _owner, _addressManager
25:     function init(address _owner, address _addressManager) external initializer { 
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L25)

```solidity
📁 File: contracts/L1/tiers/DevnetTierProvider.sol

/// @audit _owner
15:     function init(address _owner) external initializer { 
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L15)

```solidity
📁 File: contracts/L1/tiers/MainnetTierProvider.sol

/// @audit _owner
15:     function init(address _owner) external initializer { 
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L15)

```solidity
📁 File: contracts/L1/tiers/TestnetTierProvider.sol

/// @audit _owner
15:     function init(address _owner) external initializer { 
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L15)

```solidity
📁 File: contracts/L2/CrossChainOwned.sol

/// @audit _owner, _addressManager
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
[60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L60-L68)

```solidity
📁 File: contracts/L2/TaikoL2.sol

/// @audit _owner, _addressManager
71:     function init( 
72:         address _owner,
73:         address _addressManager,
74:         uint64 _l1ChainId,
75:         uint64 _gasExcess
76:     )
77:         external
78:         initializer
79:     {

/// @audit _token, _to
163:     function withdraw( 
164:         address _token,
165:         address _to
166:     )
167:         external
168:         onlyFromOwnerOrNamed("withdrawer")
169:         nonReentrant
170:         whenNotPaused
171:     {
```
[71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L71-L79), [163](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L163-L171)

```solidity
📁 File: contracts/common/AddressManager.sol

/// @audit _owner
30:     function init(address _owner) external initializer { 
```
[30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L30)

```solidity
📁 File: contracts/common/AddressResolver.sol

/// @audit _addressManager
58:     function __AddressResolver_init(address _addressManager) internal virtual onlyInitializing { 
```
[58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L58)

```solidity
📁 File: contracts/common/EssentialContract.sol

/// @audit _owner, _addressManager
95:     function __Essential_init( 
96:         address _owner,
97:         address _addressManager
98:     )
99:         internal
100:         virtual
101:         onlyInitializing
102:     {

/// @audit _owner
109:     function __Essential_init(address _owner) internal virtual { 
```
[95](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L95-L102), [109](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L109)

```solidity
📁 File: contracts/libs/LibAddress.sol

/// @audit _to
22:     function sendEther(address _to, uint256 _amount, uint256 _gasLimit) internal { 

/// @audit _to
42:     function sendEther(address _to, uint256 _amount) internal { 

/// @audit _addr
46:     function supportsInterface( 
47:         address _addr,
48:         bytes4 _interfaceId
49:     )
50:         internal
51:         view
52:         returns (bool result_)
53:     {

/// @audit _addr
61:     function isValidSignature( 
62:         address _addr,
63:         bytes32 _hash,
64:         bytes memory _sig
65:     )
66:         internal
67:         view
68:         returns (bool)
69:     {
```
[22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L22), [42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L42), [46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L46-L53), [61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L61-L69)

```solidity
📁 File: contracts/libs/LibTrieProof.sol

/// @audit _addr
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
45:     {
```
[34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L34-L45)

```solidity
📁 File: contracts/signal/SignalService.sol

/// @audit _owner, _addressManager
48:     function init(address _owner, address _addressManager) external initializer { 

/// @audit _addr
56:     function authorize(address _addr, bool _authorize) external onlyOwner { 

/// @audit _app
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

/// @audit _app
153:     function isSignalSent(address _app, bytes32 _signal) public view returns (bool) { 

/// @audit _app
194:     function getSignalSlot( 
195:         uint64 _chainId,
196:         address _app,
197:         bytes32 _signal
198:     )
199:         public
200:         pure
201:         returns (bytes32)
202:     {

/// @audit _app, _signalService
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
220:     {

/// @audit _app
298:     function _loadSignalValue( 
299:         address _app,
300:         bytes32 _signal
301:     )
302:         private
303:         view
304:         validSender(_app)
305:         nonZeroValue(_signal)
306:         returns (bytes32 value_)
307:     {
```
[48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L48), [56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L56), [83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L83-L93), [153](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L153), [194](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L194-L202), [206](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L206-L220), [298](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L298-L307)

</details>


---
### [L&#x2011;24] `name()` is not a part of the ERC-20 standard
The `name()` function is not a part of the [ERC-20 standard](https://eips.ethereum.org/EIPS/eip-20), and was added later as an [optional extension](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC20/extensions/IERC20Metadata.sol). As such, some valid ERC20 tokens do not support this interface, so it is unsafe to blindly cast all tokens to this interface, and then call this function.

<details>
<summary><i>There are 5 instances of this issue:</i></summary>

```solidity
📁 File: contracts/tokenvault/BridgedERC20.sol

97:         return LibBridgedToken.buildName(super.name(), srcChainId); 
```
[97](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L97)

```solidity
📁 File: contracts/tokenvault/BridgedERC721.sol

88:         return LibBridgedToken.buildName(super.name(), srcChainId); 
```
[88](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L88)

```solidity
📁 File: contracts/tokenvault/ERC1155Vault.sol

263:                 try t.name() returns (string memory _name) { 
```
[263](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L263)

```solidity
📁 File: contracts/tokenvault/ERC20Vault.sol

370:                 name: meta.name() 
```
[370](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L370)

```solidity
📁 File: contracts/tokenvault/ERC721Vault.sol

207:                     name: t.name() 
```
[207](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L207)

</details>


---
### [L&#x2011;25] NFT doesn't handle hard forks
When there are hard forks, users often have to go through [many hoops](https://twitter.com/elerium115/status/1558471934924431363) to ensure that they control ownership on every fork. Consider adding `require(1 == chain.chainId)`, or the chain ID of whichever chain you prefer, to the functions below, or at least include the chain ID in the URI, so that there is no confusion about which chain is the owner of the NFT.


<i>There is one instance of this issue:</i>

```solidity
📁 File: contracts/tokenvault/BridgedERC721.sol

107:     function tokenURI(uint256 _tokenId) public view virtual override returns (string memory) { 
108:         return string(
109:             abi.encodePacked(
110:                 LibBridgedToken.buildURI(srcToken, srcChainId), Strings.toString(_tokenId)
111:             )
112:         );
113:     }
```
[107](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L107-L113)


---
### [L&#x2011;26] Numbers downcast to `address`es may result in collisions
If a number is downcast to an `address` the upper bytes are truncated, which may mean that more than one value will map to the `address`

<details>
<summary><i>There are 2 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/libs/LibDepositing.sol

89:                     recipient: address(uint160(data >> 96)), 
```
[89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L89)

```solidity
📁 File: contracts/bridge/Bridge.sol

533:             _storeContext(bytes32(PLACEHOLDER), address(uint160(PLACEHOLDER)), uint64(PLACEHOLDER)); 
```
[533](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L533)

</details>


---
### [L&#x2011;27] `onlyOwner` functions not accessible if `owner` renounces ownership
The `owner` is able to perform certain privileged activities, but it's possible to set the owner to `address(0)`. This can represent a certain risk if the ownership is renounced for any other reason than by design.

Renouncing ownership will leave the contract without an `owner`, therefore limiting any functionality that needs authority.


<i>There are 2 instaces of this issue:</i>

```solidity
📁 File: contracts/common/EssentialContract.sol

114:     function _authorizeUpgrade(address) internal virtual override onlyOwner { } 

116:     function _authorizePause(address) internal virtual onlyOwner { } 
```
[114](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L114), [116](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L116)


---
### [L&#x2011;28] `payable` function does not transfer Eth
Funds sent along with the call to this function will be lost.

<details>
<summary><i>There are 2 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L2/CrossChainOwned.sol

36:     function onMessageInvocation(bytes calldata _data) 
37:         external
38:         payable
39:         whenNotPaused
40:         onlyFromNamed("bridge")
41:     {
42:         (uint64 txId, bytes memory txdata) = abi.decode(_data, (uint64, bytes));
43:         if (txId != nextTxId) revert XCO_INVALID_TX_ID();
44: 
45:         IBridge.Context memory ctx = IBridge(msg.sender).context();
46:         if (ctx.srcChainId != ownerChainId || ctx.from != owner()) {
47:             revert XCO_PERMISSION_DENIED();
48:         }
49: 
50:         (bool success,) = address(this).call(txdata);
51:         if (!success) revert XCO_TX_REVERTED();
52: 
53:         emit TransactionExecuted(nextTxId++, bytes4(txdata));
54:     }
```
[36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L36-L54)

```solidity
📁 File: contracts/bridge/Bridge.sol

115:     function sendMessage(Message calldata _message) 
116:         external
117:         payable
118:         override
119:         nonReentrant
120:         whenNotPaused
121:         returns (bytes32 msgHash_, Message memory message_)
122:     {
123:         // Ensure the message owner is not null.
124:         if (_message.srcOwner == address(0) || _message.destOwner == address(0)) {
125:             revert B_INVALID_USER();
126:         }
127: 
128:         // Check if the destination chain is enabled.
129:         (bool destChainEnabled,) = isDestChainEnabled(_message.destChainId);
130: 
131:         // Verify destination chain and to address.
132:         if (!destChainEnabled) revert B_INVALID_CHAINID();
133:         if (_message.destChainId == block.chainid) {
134:             revert B_INVALID_CHAINID();
135:         }
136: 
137:         // Ensure the sent value matches the expected amount.
138:         uint256 expectedAmount = _message.value + _message.fee;
139:         if (expectedAmount != msg.value) revert B_INVALID_VALUE();
140: 
141:         message_ = _message;
142: 
143:         // Configure message details and send signal to indicate message sending.
144:         message_.id = nextMessageId++;
145:         message_.from = msg.sender;
146:         message_.srcChainId = uint64(block.chainid);
147: 
148:         msgHash_ = hashMessage(message_);
149: 
150:         ISignalService(resolve("signal_service", false)).sendSignal(msgHash_);
151:         emit MessageSent(msgHash_, message_);
152:     }
```
[115](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L115-L152)

</details>


---
### [L&#x2011;29] `require()` should be used instead of `assert()`
Prior to solidity version 0.8.0, hitting an assert consumes the **remainder of the transaction's available gas** rather than returning it, as `require()`/`revert()` do. `assert()` should be avoided even past solidity version 0.8.0 as its [documentation](https://docs.soliditylang.org/en/v0.8.14/control-structures.html#panic-via-assert-and-error-via-require) states that "The assert function creates an error of type Panic(uint256). ... Properly functioning code should never create a Panic, not even on invalid external input. If this happens, then there is a bug in your contract which you should fix".

<details>
<summary><i>There are 4 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/libs/LibProving.sol

223:                 assert(tier.validityBond == 0); 
224:                 assert(ts.validityBond == 0 && ts.contestBond == 0 && ts.contester == address(0));
```
[223](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L223-L224)

```solidity
📁 File: contracts/automata-attestation/utils/SigVerifyLib.sol

138:         assert(success); // never reverts, always returns 0 or 1 
```
[138](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L138)

```solidity
📁 File: contracts/bridge/Bridge.sol

486:         assert(_message.from != address(this)); 
```
[486](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L486)

</details>


---
### [L&#x2011;30] Return values of `transfer()/transferFrom()` not checked
Some tokens (like USDT) don't correctly implement the EIP20 standard and their transfer/transferFrom function return void instead of a successful boolean. Calling these functions with the correct EIP20 function signatures will always revert.

<details>
<summary><i>There are 32 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

102:         tko.transferFrom(_blk.assignedProver, taikoL1Address, _blk.livenessBond); 
```
[102](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L102)

```solidity
📁 File: contracts/L1/libs/LibProving.sol

196:                 tko.transfer(blk.assignedProver, blk.livenessBond); 

242:                 tko.transferFrom(msg.sender, address(this), tier.contestBond); 

367:                 _tko.transfer(_ts.prover, _ts.validityBond + reward); 

371:                 _tko.transfer(_ts.contester, _ts.contestBond + reward); 

382:                 _tko.transfer(msg.sender, reward - _tier.validityBond); 

384:                 _tko.transferFrom(msg.sender, address(this), _tier.validityBond - reward); 
```
[196](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L196), [242](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L242), [367](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L367), [371](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L371), [382](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L382), [384](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L384)

```solidity
📁 File: contracts/L1/libs/LibVerifying.sol

189:                 tko.transfer(ts.prover, bondToReturn); 
```
[189](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L189)

```solidity
📁 File: contracts/team/TimelockTokenPool.sol

219:         IERC20(taikoToken).transferFrom(sharedVault, _to, amountToWithdraw); 
```
[219](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L219)

```solidity
📁 File: contracts/team/airdrop/ERC20Airdrop.sol

63:         IERC20(token).transferFrom(vault, user, amount); 
```
[63](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L63)

```solidity
📁 File: contracts/team/airdrop/ERC20Airdrop2.sol

91:         IERC20(token).transferFrom(vault, user, amount); 
```
[91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L91)

</details>


---
### [L&#x2011;31] Setters should prevent re-setting of the same value
This especially problematic when the setter also emits the same value, which may be confusing to offline parsers

<details>
<summary><i>There are 4 instances of this issue:</i></summary>

```solidity
📁 File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

65:     function setMrSigner(bytes32 _mrSigner, bool _trusted) external onlyOwner { 
66:         _trustedUserMrSigner[_mrSigner] = _trusted;
67:     }

69:     function setMrEnclave(bytes32 _mrEnclave, bool _trusted) external onlyOwner { 
70:         _trustedUserMrEnclave[_mrEnclave] = _trusted;
71:     }
```
[65](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L65-L67), [69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L69-L71)

```solidity
📁 File: contracts/team/airdrop/MerkleClaimable.sol

90:     function _setConfig(uint64 _claimStart, uint64 _claimEnd, bytes32 _merkleRoot) private { 
91:         claimStart = _claimStart;
92:         claimEnd = _claimEnd;
93:         merkleRoot = _merkleRoot;
94:     }
```
[90](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L90-L94)

```solidity
📁 File: contracts/tokenvault/BridgedERC20.sol

80:     function setSnapshoter(address _snapshooter) external onlyOwner { 
81:         snapshooter = _snapshooter;
82:     }
```
[80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L80-L82)

</details>


---
### [L&#x2011;32] Some tokens may revert when zero value transfers are made
In spite of the fact that EIP-20 [states](https://github.com/ethereum/EIPs/blob/46b9b698815abbfa628cd1097311deee77dd45c5/EIPS/eip-20.md?plain=1#L116) that zero-valued transfers must be accepted, some tokens, such as LEND will revert if this is attempted, which may cause transactions that involve other tokens (such as batch operations) to fully revert. Consider skipping the transfer if the amount is zero, which will also save gas.

<details>
<summary><i>There are 5 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/libs/LibProving.sol

196:                 tko.transfer(blk.assignedProver, blk.livenessBond); 

367:                 _tko.transfer(_ts.prover, _ts.validityBond + reward); 

371:                 _tko.transfer(_ts.contester, _ts.contestBond + reward); 

382:                 _tko.transfer(msg.sender, reward - _tier.validityBond); 
```
[196](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L196), [367](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L367), [371](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L371), [382](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L382)

```solidity
📁 File: contracts/L1/libs/LibVerifying.sol

189:                 tko.transfer(ts.prover, bondToReturn); 
```
[189](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L189)

</details>


---
### [L&#x2011;33] Some tokens may revert when zero value transfers are made
In spite of the fact that EIP-20 [states](https://github.com/ethereum/EIPs/blob/46b9b698815abbfa628cd1097311deee77dd45c5/EIPS/eip-20.md?plain=1#L116) that zero-valued transfers must be accepted, some tokens, such as `LEND` will revert if this is attempted, which may cause transactions that involve other tokens (such as batch operations) to fully revert. Consider skipping the transfer if the amount is zero, which will also save **gas**.

<details>
<summary><i>There are 11 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoToken.sol

62:         return super.transfer(_to, _amount); 

80:         return super.transferFrom(_from, _to, _amount); 
```
[62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L62), [80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L80)

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

114:             IERC20(assignment.feeToken).safeTransferFrom( 
115:                 _meta.coinbase, _blk.assignedProver, proverFee
116:             );
```
[114](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L114-L116)

```solidity
📁 File: contracts/L1/libs/LibVerifying.sol

189:                 tko.transfer(ts.prover, bondToReturn); 
```
[189](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L189)

```solidity
📁 File: contracts/team/TimelockTokenPool.sol

219:         IERC20(taikoToken).transferFrom(sharedVault, _to, amountToWithdraw); 
220:         IERC20(costToken).safeTransferFrom(_recipient, sharedVault, costToWithdraw);
```
[219](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L219-L220)

```solidity
📁 File: contracts/team/airdrop/ERC20Airdrop.sol

63:         IERC20(token).transferFrom(vault, user, amount); 
```
[63](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L63)

```solidity
📁 File: contracts/team/airdrop/ERC20Airdrop2.sol

91:         IERC20(token).transferFrom(vault, user, amount); 
```
[91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L91)

```solidity
📁 File: contracts/tokenvault/ERC20Vault.sol

330:             IERC20(token_).safeTransfer(_to, _amount); 

379:             t.safeTransferFrom({ from: msg.sender, to: address(this), value: _amount }); 
```
[330](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L330), [379](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L379)

```solidity
📁 File: contracts/tokenvault/adapters/USDCAdapter.sol

48:         usdc.transferFrom(_from, address(this), _amount); 
```
[48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L48)

</details>


---
### [L&#x2011;34] State variables not capped at reasonable values
Consider adding minimum/maximum value checks to ensure that the state variables below can never be used to excessively harm users, including via griefing

<details>
<summary><i>There are 23 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L2/TaikoL2.sol

/// @audit gasExcess on line 96
71:     function init( 
72:         address _owner,
73:         address _addressManager,
74:         uint64 _l1ChainId,
75:         uint64 _gasExcess
76:     )
77:         external
78:         initializer
79:     {
80:         __CrossChainOwned_init(_owner, _addressManager, _l1ChainId);
81: 
82:         if (block.chainid <= 1 || block.chainid > type(uint64).max) {
83:             revert L2_INVALID_CHAIN_ID();
84:         }
85: 
86:         if (block.number == 0) {
87:             // This is the case in real L2 genesis
88:         } else if (block.number == 1) {
89:             // This is the case in tests
90:             uint256 parentHeight = block.number - 1;
91:             l2Hashes[parentHeight] = blockhash(parentHeight);
92:         } else {
93:             revert L2_TOO_LATE();
94:         }
95: 
96:         gasExcess = _gasExcess;
97:         (publicInputHash,) = _calcPublicInputHash(block.number);
98:     }
```
[71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L71-L98)

```solidity
📁 File: contracts/L2/TaikoL2EIP1559Configurable.sol

/// @audit customConfig on line 36
/// @audit gasExcess on line 37
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
35: 
36:         customConfig = _newConfig;
37:         gasExcess = _newGasExcess;
38: 
39:         emit ConfigAndExcessChanged(_newConfig, _newGasExcess);
40:     }
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L25-L40)

```solidity
📁 File: contracts/common/EssentialContract.sol

/// @audit __reentry on line 125
119:     function _storeReentryLock(uint8 _reentry) internal virtual { 
120:         if (block.chainid == 1) {
121:             assembly {
122:                 tstore(_REENTRY_SLOT, _reentry)
123:             }
124:         } else {
125:             __reentry = _reentry;
126:         }
127:     }
```
[119](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L119-L127)

```solidity
📁 File: contracts/team/airdrop/ERC20Airdrop.sol

/// @audit token on line 41
/// @audit vault on line 42
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
38:         __Essential_init(_owner);
39:         __MerkleClaimable_init(_claimStart, _claimEnd, _merkleRoot);
40: 
41:         token = _token;
42:         vault = _vault;
43:     }
```
[27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L27-L43)

```solidity
📁 File: contracts/team/airdrop/ERC20Airdrop2.sol

/// @audit token on line 69
/// @audit vault on line 70
/// @audit withdrawalWindow on line 71
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
66:         __Essential_init(_owner);
67:         __MerkleClaimable_init(_claimStart, _claimEnd, _merkleRoot);
68: 
69:         token = _token;
70:         vault = _vault;
71:         withdrawalWindow = _withdrawalWindow;
72:     }
```
[54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L54-L72)

```solidity
📁 File: contracts/team/airdrop/ERC721Airdrop.sol

/// @audit token on line 39
/// @audit vault on line 40
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
36:         __Essential_init(_owner);
37:         __MerkleClaimable_init(_claimStart, _claimEnd, _merkleRoot);
38: 
39:         token = _token;
40:         vault = _vault;
41:     }
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L25-L41)

```solidity
📁 File: contracts/team/airdrop/MerkleClaimable.sol

/// @audit claimStart on line 91
/// @audit claimEnd on line 92
/// @audit merkleRoot on line 93
90:     function _setConfig(uint64 _claimStart, uint64 _claimEnd, bytes32 _merkleRoot) private { 
91:         claimStart = _claimStart;
92:         claimEnd = _claimEnd;
93:         merkleRoot = _merkleRoot;
94:     }
```
[90](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L90-L94)

```solidity
📁 File: contracts/tokenvault/BridgedERC1155.sol

/// @audit srcToken on line 56
/// @audit srcChainId on line 57
/// @audit __symbol on line 58
/// @audit __name on line 59
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
49:         // Check if provided parameters are valid.
50:         // The symbol and the name can be empty for ERC1155 tokens so we use some placeholder data
51:         // for them instead.
52:         LibBridgedToken.validateInputs(_srcToken, _srcChainId, "foo", "foo");
53:         __Essential_init(_owner, _addressManager);
54:         __ERC1155_init(LibBridgedToken.buildURI(_srcToken, _srcChainId));
55: 
56:         srcToken = _srcToken;
57:         srcChainId = _srcChainId;
58:         __symbol = _symbol;
59:         __name = _name;
60:     }
```
[38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L38-L60)

```solidity
📁 File: contracts/tokenvault/BridgedERC20.sol

/// @audit srcToken on line 73
/// @audit srcChainId on line 74
/// @audit __srcDecimals on line 75
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
64:         // Check if provided parameters are valid
65:         LibBridgedToken.validateInputs(_srcToken, _srcChainId, _symbol, _name);
66:         __Essential_init(_owner, _addressManager);
67:         __ERC20_init(_name, _symbol);
68:         __ERC20Snapshot_init();
69:         __ERC20Votes_init();
70:         __ERC20Permit_init(_name);
71: 
72:         // Set contract properties
73:         srcToken = _srcToken;
74:         srcChainId = _srcChainId;
75:         __srcDecimals = _decimals;
76:     }
```
[52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L52-L76)

```solidity
📁 File: contracts/tokenvault/BridgedERC721.sol

/// @audit srcToken on line 47
/// @audit srcChainId on line 48
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
42:         // Check if provided parameters are valid
43:         LibBridgedToken.validateInputs(_srcToken, _srcChainId, _symbol, _name);
44:         __Essential_init(_owner, _addressManager);
45:         __ERC721_init(_name, _symbol);
46: 
47:         srcToken = _srcToken;
48:         srcChainId = _srcChainId;
49:     }
```
[31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L31-L49)

</details>


---
### [L&#x2011;35] `symbol()` is not a part of the ERC-20 standard
The `symbol()` function is not a part of the [ERC-20 standard](https://eips.ethereum.org/EIPS/eip-20), and was added later as an [optional extension](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC20/extensions/IERC20Metadata.sol). As such, some valid ERC20 tokens do not support this interface, so it is unsafe to blindly cast all tokens to this interface, and then call this function.

<details>
<summary><i>There are 5 instances of this issue:</i></summary>

```solidity
📁 File: contracts/tokenvault/BridgedERC20.sol

108:         return LibBridgedToken.buildSymbol(super.symbol()); 
```
[108](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L108)

```solidity
📁 File: contracts/tokenvault/BridgedERC721.sol

94:         return LibBridgedToken.buildSymbol(super.symbol()); 
```
[94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L94)

```solidity
📁 File: contracts/tokenvault/ERC1155Vault.sol

266:                 try t.symbol() returns (string memory _symbol) { 
```
[266](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L266)

```solidity
📁 File: contracts/tokenvault/ERC20Vault.sol

369:                 symbol: meta.symbol(), 
```
[369](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L369)

```solidity
📁 File: contracts/tokenvault/ERC721Vault.sol

206:                     symbol: t.symbol(), 
```
[206](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L206)

</details>


---
### [L&#x2011;36] `tokenURI()` does not follow EIP-721
The [EIP](https://eips.ethereum.org/EIPS/eip-721) states that `tokenURI()` "Throws if `_tokenId` is not a valid NFT", which the code below does not do. If the NFT has not yet been minted, `tokenURI()` should revert


<i>There is one instance of this issue:</i>

```solidity
📁 File: contracts/tokenvault/BridgedERC721.sol

107:     function tokenURI(uint256 _tokenId) public view virtual override returns (string memory) { 
108:         return string(
109:             abi.encodePacked(
110:                 LibBridgedToken.buildURI(srcToken, srcChainId), Strings.toString(_tokenId)
111:             )
112:         );
113:     }
```
[107](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L107-L113)


---
### [L&#x2011;37] `unchecked` blocks with additions/multiplications may overflow
There aren't any checks to avoid an overflow which can happen inside an unchecked block, so the following expressions may overflow silently.

<details>
<summary><i>There are 27 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/libs/LibVerifying.sol

/// @audit unchecked block 124-221
/// @audit unchecked block 124-221
152:                         uint256(ITierProvider(tierProvider).getTier(ts.tier).cooldownWindow) * 60 
153:                             + uint256(ts.timestamp).max(_state.slotB.lastUnpausedAt) > block.timestamp

/// @audit unchecked block 124-221
178:                 uint256 bondToReturn = uint256(ts.validityBond) + blk.livenessBond; 

/// @audit unchecked block 124-221
213:                 uint64 lastVerifiedBlockId = b.lastVerifiedBlockId + numBlocksVerified; 
```
[152](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L152-L153), [178](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L178), [213](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L213)

```solidity
📁 File: contracts/L2/TaikoL2.sol

/// @audit unchecked block 231-238
234:             for (uint256 i; i < 255 && _blockId >= i + 1; ++i) { 
```
[234](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L234)

```solidity
📁 File: contracts/thirdparty/optimism/Bytes.sol

/// @audit unchecked block 24-28
25:             require(_length + 31 >= _length, "slice_overflow"); 
/// @audit unchecked block 24-28
26:             require(_start + _length >= _start, "slice_overflow");
/// @audit unchecked block 24-28
27:             require(_bytes.length >= _start + _length, "slice_outOfBounds");
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L25-L27)

```solidity
📁 File: contracts/thirdparty/solmate/LibFixedPointMath.sol

/// @audit unchecked block 14-80
39:             int256 k = ((x << 96) / 54_916_777_467_707_473_351_141_471_128 + 2 ** 95) >> 96; 
/// @audit unchecked block 14-80
40:             x = x - k * 54_916_777_467_707_473_351_141_471_128;

/// @audit unchecked block 14-80
45:             int256 y = x + 1_346_386_616_545_796_478_920_950_773_328; 
/// @audit unchecked block 14-80
/// @audit unchecked block 14-80
46:             y = ((y * x) >> 96) + 57_155_421_227_552_351_082_224_309_758_442;
/// @audit unchecked block 14-80
47:             int256 p = y + x - 94_201_549_194_550_492_254_356_042_504_812;
/// @audit unchecked block 14-80
/// @audit unchecked block 14-80
48:             p = ((p * y) >> 96) + 28_719_021_644_029_726_153_956_944_680_412_240;
/// @audit unchecked block 14-80
/// @audit unchecked block 14-80
49:             p = p * x + (4_385_272_521_454_847_904_659_076_985_693_276 << 96);

/// @audit unchecked block 14-80
/// @audit unchecked block 14-80
54:             q = ((q * x) >> 96) + 50_020_603_652_535_783_019_961_831_881_945; 
/// @audit unchecked block 14-80
55:             q = ((q * x) >> 96) - 533_845_033_583_426_703_283_633_433_725_380;
/// @audit unchecked block 14-80
/// @audit unchecked block 14-80
56:             q = ((q * x) >> 96) + 3_604_857_256_930_695_427_073_651_918_091_429;
/// @audit unchecked block 14-80
57:             q = ((q * x) >> 96) - 14_423_608_567_350_463_180_887_372_962_807_573;
/// @audit unchecked block 14-80
/// @audit unchecked block 14-80
58:             q = ((q * x) >> 96) + 26_449_188_498_355_588_339_934_803_723_976_023;

/// @audit unchecked block 14-80
77:                 (uint256(r) * 3_822_833_074_963_236_453_042_738_258_902_158_003_155_416_615_667) 
```
[39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L39-L40), [45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L45-L49), [54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L54-L58), [77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L77)

</details>


---
### [L&#x2011;38] `unchecked` blocks with subtractions may underflow
There aren't any checks to avoid an underflow which can happen inside an `unchecked` block, so the following subtractions may underflow silently.

<details>
<summary><i>There are 15 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/libs/LibDepositing.sol

140:                 && _state.slotA.numEthDeposits - _state.slotA.nextEthDepositToProcess 
141:                     < _config.ethDepositRingBufferSize - 1;
```
[140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L140-L141)

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

122:                 l1Hash: blockhash(block.number - 1), 

131:                 l1Height: uint64(block.number - 1), 
```
[122](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L122), [131](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L131)

```solidity
📁 File: contracts/L1/libs/LibProving.sol

382:                 _tko.transfer(msg.sender, reward - _tier.validityBond); 

384:                 _tko.transferFrom(msg.sender, address(this), _tier.validityBond - reward); 
```
[382](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L382), [384](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L384)

```solidity
📁 File: contracts/L1/libs/LibVerifying.sol

185:                     bondToReturn -= blk.livenessBond >> 1; 
```
[185](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L185)

```solidity
📁 File: contracts/L1/provers/Guardians.sol

116:             _approvals[version][_hash] |= 1 << (id - 1); 
```
[116](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L116)

```solidity
📁 File: contracts/L2/TaikoL2.sol

127:             parentId = block.number - 1; 
```
[127](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L127)

```solidity
📁 File: contracts/thirdparty/solmate/LibFixedPointMath.sol

40:             x = x - k * 54_916_777_467_707_473_351_141_471_128; 

47:             int256 p = y + x - 94_201_549_194_550_492_254_356_042_504_812; 

53:             int256 q = x - 2_855_989_394_907_223_263_936_484_059_900; 

55:             q = ((q * x) >> 96) - 533_845_033_583_426_703_283_633_433_725_380; 

57:             q = ((q * x) >> 96) - 14_423_608_567_350_463_180_887_372_962_807_573; 

78:                     >> uint256(195 - k) 
```
[40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L40), [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L47), [53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L53), [55](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L55), [57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L57), [78](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L78)

</details>


---
### [L&#x2011;39] Unsafe conversion from unsigned to signed values
Solidity follows [two's complement](https://en.wikipedia.org/wiki/Two%27s_complement) rules for its integers, meaning that the most significant bit for signed integers is used to denote the sign, and converting between the two requires inverting all of the bits and adding one. Because of this, casting an unsigned integer to a signed one may result in a change of the sign and or magnitude of the value. For example, `int8(type(uint8).max)` is not equal to `type(int8).max`, but is equal to `-1`. `type(uint8).max` in binary is `11111111`, which if cast to a signed value, means the first binary `1` indicates a negative value, and the binary `1`s, invert to all zeroes, and when one is added, it becomes one, but negative, and therefore the decimal value of binary `11111111` is `-1`.

<details>
<summary><i>There are 5 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L2/Lib1559Math.sol

/// @audit uint256 -> int256
45:         return uint256(LibFixedPointMath.exp(int256(input))); 
```
[45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L45)

```solidity
📁 File: contracts/automata-attestation/utils/BytesUtils.sol

/// @audit uint256 -> int256
97:                     return int256(diff); 

/// @audit uint256 -> int256
/// @audit uint256 -> int256
104:         return int256(len) - int256(otherlen); 
```
[97](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L97), [104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L104)

```solidity
📁 File: contracts/thirdparty/solmate/LibFixedPointMath.sol

/// @audit uint256 -> int256
76:             r = int256( 
77:                 (uint256(r) * 3_822_833_074_963_236_453_042_738_258_902_158_003_155_416_615_667)
78:                     >> uint256(195 - k)
79:             );
```
[76](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L76-L79)

</details>


---
### [L&#x2011;40] Unsafe downcast
When a type is downcast to a smaller type, the higher order bits are discarded, resulting in the application of a modulo operation to the original value.

If the downcasted value is large enough, this may result in an overflow that will not revert.

<details>
<summary><i>There are 27 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/libs/LibDepositing.sol

/// @audit uint256 -> uint96
53:                 amount: uint96(msg.value), 

/// @audit uint256 -> uint96
83:             uint96 fee = uint96(_config.ethDepositMaxFee.min(block.basefee * _config.ethDepositGas)); 

/// @audit uint256 -> uint160
89:                     recipient: address(uint160(data >> 96)), 
/// @audit uint256 -> uint96
90:                     amount: uint96(data),
```
[53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L53), [83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L83), [89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L89-L90)

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

/// @audit uint256 -> uint64
131:                 l1Height: uint64(block.number - 1), 

/// @audit uint256 -> uint24
191:             meta_.txListByteSize = uint24(_txList.length); 
```
[131](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L131), [191](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L191)

```solidity
📁 File: contracts/L2/TaikoL2.sol

/// @audit uint256 -> uint64
284:             gasExcess_ = uint64(excess.min(type(uint64).max)); 
```
[284](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L284)

```solidity
📁 File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

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
[146](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L146-L147), [212](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L212), [217](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L217), [222](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L222)

```solidity
📁 File: contracts/automata-attestation/utils/Asn1Decode.sol

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
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L15), [20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L20), [25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L25), [193](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L193-L194), [206](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L206-L207)

```solidity
📁 File: contracts/bridge/Bridge.sol

/// @audit uint256 -> uint64
/// @audit uint256 -> uint160
533:             _storeContext(bytes32(PLACEHOLDER), address(uint160(PLACEHOLDER)), uint64(PLACEHOLDER)); 
```
[533](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L533)

```solidity
📁 File: contracts/team/TimelockTokenPool.sol

/// @audit uint256 -> uint64
264:         return _amount * uint64(block.timestamp - _start) / _period; 
```
[264](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L264)

```solidity
📁 File: contracts/thirdparty/optimism/rlp/RLPWriter.sol

/// @audit uint256 -> uint8
/// @audit uint256 -> uint8
35:             out_[0] = bytes1(uint8(_len) + uint8(_offset)); 

/// @audit uint256 -> uint8
/// @audit uint256 -> uint8
45:             out_[0] = bytes1(uint8(lenLen) + uint8(_offset) + 55); 

/// @audit uint256 -> uint8
47:                 out_[i] = bytes1(uint8((_len / (256 ** (lenLen - i))) % 256)); 
```
[35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L35), [45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L45), [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L47)

</details>


---
### [L&#x2011;41] Unused/empty `receive()/fallback()` function
If the intention is for the Ether to be used, the function should call another function or emit an event, otherwise it should revert.


<i>There is one instance of this issue:</i>

```solidity
📁 File: contracts/bridge/Bridge.sol

70:     receive() external payable { } 
```
[70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L70)


---
### [L&#x2011;42] Upgradable contracts should have an initialization function
Upgradable Solidity contracts utilize a proxy pattern to separate logic from data storage, allowing smooth logic updates without affecting data. To ensure consistency and security, an initialization function is crucial during deployment. This safeguards against vulnerabilities and maintains a proper contract setup.


<i>There is one instance of this issue:</i>

```solidity
📁 File: contracts/tokenvault/ERC1155Vault.sol

/// @audit ERC1155ReceiverUpgradeable on line 29
29: contract ERC1155Vault is BaseNFTVault, ERC1155ReceiverUpgradeable { 
30:     using LibAddress for address;
31: 
32:     uint256[50] private __gap;
```
[29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L29-L32)


---
### [L&#x2011;43] Vulnerable versions of packages are being used
This project's specific package versions are vulnerable to the specific CVEs listed below. Consider switching to more recent versions of these packages that don't have these vulnerabilities.
- `@openzeppelin/contracts-upgradeable` - <b>HIGH</b> - [Link](https://github.com/OpenZeppelin/openzeppelin-contracts/security/advisories/GHSA-93hq-5wgc-jc82) - GovernorCompatibilityBravo may trim proposal calldata

>### Impact
>
>The proposal creation entrypoint (`propose`) in `GovernorCompatibilityBravo` allows the creation of proposals with a `signatures` array shorter than the `calldatas` array. This causes the additional elements of the latter to be ignored, and if the proposal succeeds the corresponding actions would eventually execute without any calldata. The `ProposalCreated` event correctly represents what will eventually execute, but the proposal parameters as queried through `getActions` appear to respect the original intended calldata.
>
>### Patches
>
>This issue has been patched in v4.8.3.
>
>### Workarounds
>
>Ensure that all proposals that pass through governance have equal length `signatures` and `calldatas` parameters.
>
- `@openzeppelin/contracts-upgradeable` - <b>MODERATE</b> - [Link](https://github.com/OpenZeppelin/openzeppelin-contracts/security/advisories/GHSA-g4vp-m682-qqmp) - OpenZeppelin Contracts vulnerable to Improper Escaping of Output

>### Impact
>
>OpenZeppelin Contracts is a library for secure smart contract development. Starting in version 4.0.0 and prior to version 4.9.3, contracts using `ERC2771Context` along with a custom trusted forwarder may see `_msgSender` return `address(0)` in calls that originate from the forwarder with calldata shorter than 20 bytes. This combination of circumstances does not appear to be common, in particular it is not the case for `MinimalForwarder` from OpenZeppelin Contracts, or any deployed forwarder the team is aware of, given that the signer address is appended to all calls that originate from these forwarders.
>
>### Patches
>
>The problem has been patched in v4.9.3.
>
- `@openzeppelin/contracts-upgradeable` - <b>MODERATE</b> - [Link](https://github.com/OpenZeppelin/openzeppelin-contracts/security/advisories/GHSA-wprv-93r4-jj2p) - OpenZeppelin Contracts using MerkleProof multiproofs may allow proving arbitrary leaves for specific trees

>### Impact
>
>When the `verifyMultiProof`, `verifyMultiProofCalldata`, `processMultiProof`, or `processMultiProofCalldata` functions are in use, it is possible to construct merkle trees that allow forging a valid multiproof for an arbitrary set of leaves.
>
>A contract may be vulnerable if it uses multiproofs for verification and the merkle tree that is processed includes a node with value 0 at depth 1 (just under the root). This could happen inadvertently for balanced trees with 3 leaves or less, if the leaves are not hashed. This could happen deliberately if a malicious tree builder includes such a node in the tree.
>
>A contract is not vulnerable if it uses single-leaf proving (`verify`, `verifyCalldata`, `processProof`, or `processProofCalldata`), or if it uses multiproofs with a known tree that has hashed leaves. Standard merkle trees produced or validated with the [@openzeppelin/merkle-tree](https://github.com/OpenZeppelin/merkle-tree) library are safe.
>
>### Patches
>
>The problem has been patched in 4.9.2.
>
>### Workarounds
>
>If you are using multiproofs: When constructing merkle trees hash the leaves and do not insert empty nodes in your trees. Using the [@openzeppelin/merkle-tree](https://www.npmjs.com/package/@openzeppelin/merkle-tree) package eliminates this issue. Do not accept user-provided merkle roots without reconstructing at least the first level of the tree. Verify the merkle tree structure by reconstructing it from the leaves.
- `@openzeppelin/contracts-upgradeable` - <b>MODERATE</b> - [Link](https://github.com/OpenZeppelin/openzeppelin-contracts/security/advisories/GHSA-mx2q-35m2-x2rh) - OpenZeppelin Contracts TransparentUpgradeableProxy clashing selector calls may not be delegated

>### Impact
>
>A function in the implementation contract may be inaccessible if its selector clashes with one of the proxy's own selectors. Specifically, if the clashing function has a different signature with incompatible ABI encoding, the proxy could revert while attempting to decode the arguments from calldata.
>
>The probability of an accidental clash is negligible, but one could be caused deliberately.
>
>### Patches
>
>The issue has been fixed in v4.8.3.
>
>### Workarounds
>
>If a function appears to be inaccessible for this reason, it may be possible to craft the calldata such that ABI decoding does not fail at the proxy and the function is properly proxied through.
>
>### References
>
>https://github.com/OpenZeppelin/openzeppelin-contracts/pull/4154
>
- `@openzeppelin/contracts-upgradeable` - <b>MODERATE</b> - [Link](https://github.com/OpenZeppelin/openzeppelin-contracts/security/advisories/GHSA-5h3x-9wvq-w4m2) - OpenZeppelin Contracts's governor proposal creation may be blocked by frontrunning

>### Impact
>
>By frontrunning the creation of a proposal, an attacker can become the proposer and gain the ability to cancel it. The attacker can do this repeatedly to try to prevent a proposal from being proposed at all.
>
>This impacts the `Governor` contract in v4.9.0 only, and the `GovernorCompatibilityBravo` contract since v4.3.0.
>
>### Patches
>
>The problem has been patched in 4.9.1 by introducing opt-in frontrunning protection.
>
>### Workarounds
>
>Submit the proposal creation transaction to an endpoint with frontrunning protection.
>
>### Credit
>
>Reported by Lior Abadi and Joaquin Pereyra from Coinspect.
>
>### References
>
>https://www.coinspect.com/openzeppelin-governor-dos/


<i>There is one instance of this issue:</i>

```solidity
📁 File: contracts/common/IAddressManager.sol

1: // SPDX-License-Identifier: MIT 
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressManager.sol#L1)


## NonCritical


---
### [NC&#x2011;1] Add inline comments for unnamed variables
`function foo(address x, address)` -> `function foo(address x, address /* y */)`

<details>
<summary><i>There are 11 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoL1.sol

220:     function _authorizePause(address) 
221:         internal
222:         view
223:         virtual
224:         override
225:         onlyFromOwnerOrNamed("chain_pauser")
226:     { }
```
[220](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L220-L226)

```solidity
📁 File: contracts/L1/tiers/DevnetTierProvider.sol

54:     function getMinTier(uint256) public pure override returns (uint16) { 
```
[54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L54)

```solidity
📁 File: contracts/bridge/Bridge.sol

461:     function _authorizePause(address) 
462:         internal
463:         view
464:         virtual
465:         override
466:         onlyFromOwnerOrNamed("bridge_pauser")
467:     { }
```
[461](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L461-L467)

```solidity
📁 File: contracts/common/AddressManager.sol

58:     function _authorizePause(address) internal pure override { 
```
[58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L58)

```solidity
📁 File: contracts/common/EssentialContract.sol

114:     function _authorizeUpgrade(address) internal virtual override onlyOwner { } 

116:     function _authorizePause(address) internal virtual onlyOwner { } 
```
[114](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L114), [116](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L116)

```solidity
📁 File: contracts/signal/SignalService.sol

231:     function _authorizePause(address) internal pure override { 
```
[231](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L231)

```solidity
📁 File: contracts/tokenvault/ERC1155Vault.sol

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
170:     {

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
185:     {
```
[160](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L160-L170), [175](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L175-L185)

```solidity
📁 File: contracts/tokenvault/ERC721Vault.sol

142:     function onERC721Received( 
143:         address,
144:         address,
145:         uint256,
146:         bytes calldata
147:     )
148:         external
149:         pure
150:         returns (bytes4)
151:     {
```
[142](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L142-L151)

```solidity
📁 File: contracts/verifiers/GuardianVerifier.sol

23:     function verifyProof( 
24:         Context calldata _ctx,
25:         TaikoData.Transition calldata,
26:         TaikoData.TierProof calldata
27:     )
28:         external
29:         view
30:     {
```
[23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L23-L30)

</details>


---
### [NC&#x2011;2] Adding a `return` statement when the function defines a named return variable, is redundant
Once the return variable has been assigned (or has its default value), there is no need to explicitly return it at the end of the function, since it's returned automatically.


<i>There is one instance of this issue:</i>

```solidity
📁 File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

/// @audit return statement on lines 130,183
68:     function get( 
69:         bytes memory _key,
70:         bytes[] memory _proof,
71:         bytes32 _root
72:     )
73:         internal
74:         pure
75:         returns (bytes memory value_)
76:     {
```
[68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L68-L76)


---
### [NC&#x2011;3] `address` shouldn't be hard-coded
It is often better to declare `address`es as `immutable` (instead of constant), and assign them via constructor arguments. This allows the code to remain the same across deployments on different networks, and avoids recompilation when addresses need to change.


<i>There is one instance of this issue:</i>

```solidity
📁 File: contracts/L2/TaikoL2.sol

/// @audit 0x0000777735367b36bC9B61C50022d9D0700dB4Ec
32:     address public constant GOLDEN_TOUCH_ADDRESS = 0x0000777735367b36bC9B61C50022d9D0700dB4Ec; 
```
[32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L32)


---
### [NC&#x2011;4] Assembly block creates dirty bits
Writing data to the free memory pointer without later updating the free memory pointer will cause there to be dirty bits at that memory location. Not updating the free memory pointer will make it [harder](https://docs.soliditylang.org/en/latest/ir-breaking-changes.html#cleanup) for the optimizer to reason about whether the memory needs to be cleaned before use, which will lead to worse optimizations.


<i>There is one instance of this issue:</i>

```solidity
📁 File: contracts/automata-attestation/utils/SHA1.sol

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
37:             }
38: 
39:             for { let i := 0 } lt(i, totallen) { i := add(i, 64) } {
40:                 mstore(scratch, readword(data, i, len))
41:                 mstore(add(scratch, 32), readword(data, add(i, 32), len))
42: 
43:                 // If we loaded the last byte, store the terminator byte
44:                 switch lt(sub(len, i), 64)
45:                 case 1 { mstore8(add(scratch, sub(len, i)), 0x80) }
46: 
47:                 // If this is the last block, store the length
48:                 switch eq(i, sub(totallen, 64))
49:                 case 1 { mstore(add(scratch, 32), or(mload(add(scratch, 32)), mul(len, 8))) }
50: 
51:                 // Expand the 16 32-bit words into 80
52:                 for { let j := 64 } lt(j, 128) { j := add(j, 12) } {
53:                     let temp :=
54:                         xor(
55:                             xor(mload(add(scratch, sub(j, 12))), mload(add(scratch, sub(j, 32)))),
56:                             xor(mload(add(scratch, sub(j, 56))), mload(add(scratch, sub(j, 64))))
57:                         )
58:                     temp :=
59:                         or(
60:                             and(
61:                                 mul(temp, 2),
62:                                 0xFFFFFFFEFFFFFFFEFFFFFFFEFFFFFFFEFFFFFFFEFFFFFFFEFFFFFFFEFFFFFFFE
63:                             ),
64:                             and(
65:                                 div(temp, 0x80000000),
66:                                 0x0000000100000001000000010000000100000001000000010000000100000001
67:                             )
68:                         )
69:                     mstore(add(scratch, j), temp)
70:                 }
71:                 for { let j := 128 } lt(j, 320) { j := add(j, 24) } {
72:                     let temp :=
73:                         xor(
74:                             xor(mload(add(scratch, sub(j, 24))), mload(add(scratch, sub(j, 64)))),
75:                             xor(mload(add(scratch, sub(j, 112))), mload(add(scratch, sub(j, 128))))
76:                         )
77:                     temp :=
78:                         or(
79:                             and(
80:                                 mul(temp, 4),
81:                                 0xFFFFFFFCFFFFFFFCFFFFFFFCFFFFFFFCFFFFFFFCFFFFFFFCFFFFFFFCFFFFFFFC
82:                             ),
83:                             and(
84:                                 div(temp, 0x40000000),
85:                                 0x0000000300000003000000030000000300000003000000030000000300000003
86:                             )
87:                         )
88:                     mstore(add(scratch, j), temp)
89:                 }
90: 
91:                 let x := h
92:                 let f := 0
93:                 let k := 0
94:                 for { let j := 0 } lt(j, 80) { j := add(j, 1) } {
95:                     switch div(j, 20)
96:                     case 0 {
97:                         // f = d xor (b and (c xor d))
98:                         f := xor(div(x, 0x100000000000000000000), div(x, 0x10000000000))
99:                         f := and(div(x, 0x1000000000000000000000000000000), f)
100:                         f := xor(div(x, 0x10000000000), f)
101:                         k := 0x5A827999
102:                     }
103:                     case 1 {
104:                         // f = b xor c xor d
105:                         f :=
106:                             xor(
107:                                 div(x, 0x1000000000000000000000000000000),
108:                                 div(x, 0x100000000000000000000)
109:                             )
110:                         f := xor(div(x, 0x10000000000), f)
111:                         k := 0x6ED9EBA1
112:                     }
113:                     case 2 {
114:                         // f = (b and c) or (d and (b or c))
115:                         f :=
116:                             or(
117:                                 div(x, 0x1000000000000000000000000000000),
118:                                 div(x, 0x100000000000000000000)
119:                             )
120:                         f := and(div(x, 0x10000000000), f)
121:                         f :=
122:                             or(
123:                                 and(
124:                                     div(x, 0x1000000000000000000000000000000),
125:                                     div(x, 0x100000000000000000000)
126:                                 ),
127:                                 f
128:                             )
129:                         k := 0x8F1BBCDC
130:                     }
131:                     case 3 {
132:                         // f = b xor c xor d
133:                         f :=
134:                             xor(
135:                                 div(x, 0x1000000000000000000000000000000),
136:                                 div(x, 0x100000000000000000000)
137:                             )
138:                         f := xor(div(x, 0x10000000000), f)
139:                         k := 0xCA62C1D6
140:                     }
141:                     // temp = (a leftrotate 5) + f + e + k + w[i]
142:                     let temp := and(div(x, 0x80000000000000000000000000000000000000000000000), 0x1F)
143:                     temp :=
144:                         or(and(div(x, 0x800000000000000000000000000000000000000), 0xFFFFFFE0), temp)
145:                     temp := add(f, temp)
146:                     temp := add(and(x, 0xFFFFFFFF), temp)
147:                     temp := add(k, temp)
148:                     temp :=
149:                         add(
150:                             div(
151:                                 mload(add(scratch, mul(j, 4))),
152:                                 0x100000000000000000000000000000000000000000000000000000000
153:                             ),
154:                             temp
155:                         )
156:                     x :=
157:                         or(
158:                             div(x, 0x10000000000),
159:                             mul(temp, 0x10000000000000000000000000000000000000000)
160:                         )
161:                     x :=
162:                         or(
163:                             and(x, 0xFFFFFFFF00FFFFFFFF000000000000FFFFFFFF00FFFFFFFF),
164:                             mul(
165:                                 or(
166:                                     and(div(x, 0x4000000000000), 0xC0000000),
167:                                     and(div(x, 0x400000000000000000000), 0x3FFFFFFF)
168:                                 ),
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
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SHA1.sol#L12-L193)


---
### [NC&#x2011;5] Assembly blocks should have extensive comments
Assembly blocks take a lot more time to audit than normal Solidity code, and often have gotchas and side-effects that the Solidity versions of the same code do not. Consider adding more comments explaining what is being done in every step of the assembly code, and describe why assembly is being used instead of Solidity.

<details>
<summary><i>There are 33 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L2/TaikoL2.sol

242:         assembly { 
243:             publicInputHashOld := keccak256(inputs, 8192 /*mul(256, 32)*/ )
244:         }

247:         assembly { 
248:             publicInputHashNew := keccak256(inputs, 8192 /*mul(256, 32)*/ )
249:         }
```
[242](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L242-L244), [247](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L247-L249)

```solidity
📁 File: contracts/automata-attestation/utils/BytesUtils.sol

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
[26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L26-L28), [76](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L76-L79), [83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L83-L86), [200](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L200-L202), [213](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L213-L215), [226](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L226-L228), [239](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L239-L245), [266](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L266-L269), [273](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L273-L275), [299](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L299-L302)

```solidity
📁 File: contracts/automata-attestation/utils/RsaVerify.sol

99:         assembly { 
100:             pop(
101:                 staticcall(
102:                     sub(gas(), 2000),
103:                     5,
104:                     add(input, 0x20),
105:                     inputlen,
106:                     add(decipher, 0x20),
107:                     decipherlen
108:                 )
109:             )
110:         }

247:         assembly { 
248:             pop(
249:                 staticcall(
250:                     sub(gas(), 2000),
251:                     5,
252:                     add(input, 0x20),
253:                     inputlen,
254:                     add(decipher, 0x20),
255:                     decipherlen
256:                 )
257:             )
258:         }
```
[99](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L99-L110), [247](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L247-L258)

```solidity
📁 File: contracts/automata-attestation/utils/SHA1.sol

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
37:             }
38: 
39:             for { let i := 0 } lt(i, totallen) { i := add(i, 64) } {
40:                 mstore(scratch, readword(data, i, len))
41:                 mstore(add(scratch, 32), readword(data, add(i, 32), len))
42: 
43:                 // If we loaded the last byte, store the terminator byte
44:                 switch lt(sub(len, i), 64)
45:                 case 1 { mstore8(add(scratch, sub(len, i)), 0x80) }
46: 
47:                 // If this is the last block, store the length
48:                 switch eq(i, sub(totallen, 64))
49:                 case 1 { mstore(add(scratch, 32), or(mload(add(scratch, 32)), mul(len, 8))) }
50: 
51:                 // Expand the 16 32-bit words into 80
52:                 for { let j := 64 } lt(j, 128) { j := add(j, 12) } {
53:                     let temp :=
54:                         xor(
55:                             xor(mload(add(scratch, sub(j, 12))), mload(add(scratch, sub(j, 32)))),
56:                             xor(mload(add(scratch, sub(j, 56))), mload(add(scratch, sub(j, 64))))
57:                         )
58:                     temp :=
59:                         or(
60:                             and(
61:                                 mul(temp, 2),
62:                                 0xFFFFFFFEFFFFFFFEFFFFFFFEFFFFFFFEFFFFFFFEFFFFFFFEFFFFFFFEFFFFFFFE
63:                             ),
64:                             and(
65:                                 div(temp, 0x80000000),
66:                                 0x0000000100000001000000010000000100000001000000010000000100000001
67:                             )
68:                         )
69:                     mstore(add(scratch, j), temp)
70:                 }
71:                 for { let j := 128 } lt(j, 320) { j := add(j, 24) } {
72:                     let temp :=
73:                         xor(
74:                             xor(mload(add(scratch, sub(j, 24))), mload(add(scratch, sub(j, 64)))),
75:                             xor(mload(add(scratch, sub(j, 112))), mload(add(scratch, sub(j, 128))))
76:                         )
77:                     temp :=
78:                         or(
79:                             and(
80:                                 mul(temp, 4),
81:                                 0xFFFFFFFCFFFFFFFCFFFFFFFCFFFFFFFCFFFFFFFCFFFFFFFCFFFFFFFCFFFFFFFC
82:                             ),
83:                             and(
84:                                 div(temp, 0x40000000),
85:                                 0x0000000300000003000000030000000300000003000000030000000300000003
86:                             )
87:                         )
88:                     mstore(add(scratch, j), temp)
89:                 }
90: 
91:                 let x := h
92:                 let f := 0
93:                 let k := 0
94:                 for { let j := 0 } lt(j, 80) { j := add(j, 1) } {
95:                     switch div(j, 20)
96:                     case 0 {
97:                         // f = d xor (b and (c xor d))
98:                         f := xor(div(x, 0x100000000000000000000), div(x, 0x10000000000))
99:                         f := and(div(x, 0x1000000000000000000000000000000), f)
100:                         f := xor(div(x, 0x10000000000), f)
101:                         k := 0x5A827999
102:                     }
103:                     case 1 {
104:                         // f = b xor c xor d
105:                         f :=
106:                             xor(
107:                                 div(x, 0x1000000000000000000000000000000),
108:                                 div(x, 0x100000000000000000000)
109:                             )
110:                         f := xor(div(x, 0x10000000000), f)
111:                         k := 0x6ED9EBA1
112:                     }
113:                     case 2 {
114:                         // f = (b and c) or (d and (b or c))
115:                         f :=
116:                             or(
117:                                 div(x, 0x1000000000000000000000000000000),
118:                                 div(x, 0x100000000000000000000)
119:                             )
120:                         f := and(div(x, 0x10000000000), f)
121:                         f :=
122:                             or(
123:                                 and(
124:                                     div(x, 0x1000000000000000000000000000000),
125:                                     div(x, 0x100000000000000000000)
126:                                 ),
127:                                 f
128:                             )
129:                         k := 0x8F1BBCDC
130:                     }
131:                     case 3 {
132:                         // f = b xor c xor d
133:                         f :=
134:                             xor(
135:                                 div(x, 0x1000000000000000000000000000000),
136:                                 div(x, 0x100000000000000000000)
137:                             )
138:                         f := xor(div(x, 0x10000000000), f)
139:                         k := 0xCA62C1D6
140:                     }
141:                     // temp = (a leftrotate 5) + f + e + k + w[i]
142:                     let temp := and(div(x, 0x80000000000000000000000000000000000000000000000), 0x1F)
143:                     temp :=
144:                         or(and(div(x, 0x800000000000000000000000000000000000000), 0xFFFFFFE0), temp)
145:                     temp := add(f, temp)
146:                     temp := add(and(x, 0xFFFFFFFF), temp)
147:                     temp := add(k, temp)
148:                     temp :=
149:                         add(
150:                             div(
151:                                 mload(add(scratch, mul(j, 4))),
152:                                 0x100000000000000000000000000000000000000000000000000000000
153:                             ),
154:                             temp
155:                         )
156:                     x :=
157:                         or(
158:                             div(x, 0x10000000000),
159:                             mul(temp, 0x10000000000000000000000000000000000000000)
160:                         )
161:                     x :=
162:                         or(
163:                             and(x, 0xFFFFFFFF00FFFFFFFF000000000000FFFFFFFF00FFFFFFFF),
164:                             mul(
165:                                 or(
166:                                     and(div(x, 0x4000000000000), 0xC0000000),
167:                                     and(div(x, 0x400000000000000000000), 0x3FFFFFFF)
168:                                 ),
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
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SHA1.sol#L12-L193)

```solidity
📁 File: contracts/bridge/Bridge.sol

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
[543](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L543-L547), [560](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L560-L564)

```solidity
📁 File: contracts/common/EssentialContract.sol

121:             assembly { 
122:                 tstore(_REENTRY_SLOT, _reentry)
123:             }

132:             assembly { 
133:                 reentry_ := tload(_REENTRY_SLOT)
134:             }
```
[121](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L121-L123), [132](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L132-L134)

```solidity
📁 File: contracts/libs/Lib4844.sol

53:         assembly { 
54:             first := mload(add(ret, 32))
55:             second := mload(add(ret, 64))
56:         }
```
[53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L53-L56)

```solidity
📁 File: contracts/signal/SignalService.sol

265:         assembly { 
266:             sstore(slot_, _value)
267:         }

309:         assembly { 
310:             value_ := sload(slot)
311:         }
```
[265](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L265-L267), [309](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L309-L311)

```solidity
📁 File: contracts/thirdparty/optimism/Bytes.sol

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
[32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L32-L81), [104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L104-L141)

```solidity
📁 File: contracts/thirdparty/optimism/rlp/RLPReader.sol

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
[43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L43-L45), [94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L94-L96), [159](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L159-L161), [178](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L178-L180), [198](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L198-L200), [208](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L208-L210), [244](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L244-L246), [254](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L254-L256), [295](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L295-L301)

</details>


---
### [NC&#x2011;6] Avoid mutating `function`/`modifier` parameters
Use a local variable instead

<details>
<summary><i>There are 6 instances of this issue:</i></summary>

```solidity
📁 File: contracts/automata-attestation/lib/PEMCertChainLib.sol

/// @audit tbsPtr
334:                 tbsPtr = der.nextSiblingOf(tbsPtr); 

/// @audit tbsPtr
336:                 tbsPtr = 0; // exit 
```
[334](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L334), [336](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L336)

```solidity
📁 File: contracts/automata-attestation/utils/Asn1Decode.sol

/// @audit _ixs
30:         _ixs |= _ixf << 80; 
/// @audit _ixs
31:         _ixs |= _ixl << 160;
```
[30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L30-L31)

```solidity
📁 File: contracts/thirdparty/solmate/LibFixedPointMath.sol

/// @audit x
33:             x = (x << 78) / 5 ** 18; 

/// @audit x
40:             x = x - k * 54_916_777_467_707_473_351_141_471_128; 
```
[33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L33), [40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L40)

</details>


---
### [NC&#x2011;7] Avoid the use of sensitive terms
Use [alternative variants](https://www.zdnet.com/article/mysql-drops-master-slave-and-blacklist-whitelist-terminology/), e.g. allowlist/denylist instead of whitelist/blacklist


<i>There are 9 instaces of this issue:</i>

```solidity
📁 File: contracts/tokenvault/ERC20Vault.sol

51:     /// @notice Mappings from bridged tokens to their blacklist status. 
52:     mapping(address btoken => bool blacklisted) public btokenBlacklist;

136:     error VAULT_BTOKEN_BLACKLISTED(); 

162:         if (btokenBlacklist[_btokenNew]) revert VAULT_BTOKEN_BLACKLISTED(); 

181:             btokenBlacklist[btokenOld_] = true; 

216:         if (btokenBlacklist[_op.token]) revert VAULT_BTOKEN_BLACKLISTED(); 
```
[51](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L51-L52), [136](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L136), [162](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L162), [181](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L181), [216](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L216)


---
### [NC&#x2011;8] Codebase should implement formal verification testing
Formal verification is the act of proving or disproving the correctness of intended algorithms underlying a system with respect to a certain formal specification/property/invariant, using formal methods of mathematics.

Some tools that are currently available to perform these tests on smart contracts are [SMTChecker](https://docs.soliditylang.org/en/latest/smtchecker.html) and [Certora Prover](https://www.certora.com/).


---
### [NC&#x2011;9] Common functions should be refactored to a common base contract
The functions below have the same implementation as is seen in other files. The functions should be refactored into functions of a common base contract

<details>
<summary><i>There are 3 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L2/TaikoL2.sol

/// @audit also seen in contracts/L1/TaikoL1.sol
208:     function getConfig() public view virtual returns (Config memory config_) { 
```
[208](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L208)

```solidity
📁 File: contracts/bridge/Bridge.sol

/// @audit also seen in contracts/common/EssentialContract.sol
/// @audit also seen in contracts/L1/TaikoL1.sol
461:     function _authorizePause(address) 
```
[461](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L461)

```solidity
📁 File: contracts/tokenvault/ERC1155Vault.sol

/// @audit also seen in contracts/tokenvault/BaseVault.sol
192:     function supportsInterface(bytes4 interfaceId) 
```
[192](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L192)

</details>


---
### [NC&#x2011;10] Complicated functions should have explicit comments
Large and/or complex functions should have more comments to better explain the purpose of each logic step.

<details>
<summary><i>There are 17 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

/// @audit function is 68 lines long
62:     function onBlockProposed( 
63:         TaikoData.Block memory _blk,
64:         TaikoData.BlockMetadata memory _meta,
65:         bytes memory _data
66:     )
```
[62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L62-L66)

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

/// @audit function is 212 lines long
68:     function proposeBlock( 
69:         TaikoData.State storage _state,
70:         TaikoData.Config memory _config,
71:         IAddressResolver _resolver,
72:         bytes calldata _data,
73:         bytes calldata _txList
74:     )
```
[68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L68-L74)

```solidity
📁 File: contracts/L1/libs/LibProving.sol

/// @audit function is 175 lines long
91:     function proveBlock( 
92:         TaikoData.State storage _state,
93:         TaikoData.Config memory _config,
94:         IAddressResolver _resolver,
95:         TaikoData.BlockMetadata memory _meta,
96:         TaikoData.Transition memory _tran,
97:         TaikoData.TierProof memory _proof
98:     )

/// @audit function is 78 lines long
269:     function _createTransition( 
270:         TaikoData.State storage _state,
271:         TaikoData.Block storage _blk,
272:         TaikoData.Transition memory _tran,
273:         uint64 slot
274:     )
```
[91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L91-L98), [269](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L269-L274)

```solidity
📁 File: contracts/L1/libs/LibVerifying.sol

/// @audit function is 137 lines long
85:     function verifyBlocks( 
86:         TaikoData.State storage _state,
87:         TaikoData.Config memory _config,
88:         IAddressResolver _resolver,
89:         uint64 _maxBlocksToVerify
90:     )
```
[85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L85-L90)

```solidity
📁 File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

/// @audit function is 121 lines long
364:     function _verifyParsedQuote(V3Struct.ParsedV3QuoteStruct memory v3quote) 
```
[364](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L364)

```solidity
📁 File: contracts/automata-attestation/lib/PEMCertChainLib.sol

/// @audit function is 140 lines long
74:     function decodeCert( 
75:         bytes memory der,
76:         bool isPckCert
77:     )

/// @audit function is 70 lines long
269:     function _findPckTcbInfo( 
270:         bytes memory der,
271:         uint256 tbsPtr,
272:         uint256 tbsParentPtr
273:     )
```
[74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L74-L77), [269](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L269-L273)

```solidity
📁 File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

/// @audit function is 69 lines long
62:     function validateParsedInput(V3Struct.ParsedV3QuoteStruct memory v3Quote) 
```
[62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L62)

```solidity
📁 File: contracts/automata-attestation/utils/RsaVerify.sol

/// @audit function is 138 lines long
43:     function pkcs1Sha256( 
44:         bytes32 _sha256,
45:         bytes memory _s,
46:         bytes memory _e,
47:         bytes memory _m
48:     )

/// @audit function is 85 lines long
212:     function pkcs1Sha1( 
213:         bytes20 _sha1,
214:         bytes memory _s,
215:         bytes memory _e,
216:         bytes memory _m
217:     )
```
[43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L43-L48), [212](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L212-L217)

```solidity
📁 File: contracts/automata-attestation/utils/SHA1.sol

/// @audit function is 183 lines long
11:     function sha1(bytes memory data) internal pure returns (bytes20 ret) { 
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SHA1.sol#L11)

```solidity
📁 File: contracts/bridge/Bridge.sol

/// @audit function is 90 lines long
217:     function processMessage( 
218:         Message calldata _message,
219:         bytes calldata _proof
220:     )
```
[217](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L217-L220)

```solidity
📁 File: contracts/thirdparty/optimism/Bytes.sol

/// @audit function is 69 lines long
15:     function slice( 
16:         bytes memory _bytes,
17:         uint256 _start,
18:         uint256 _length
19:     )
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L15-L19)

```solidity
📁 File: contracts/thirdparty/optimism/rlp/RLPReader.sol

/// @audit function is 126 lines long
144:     function _decodeLength(RLPItem memory _in) 
```
[144](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L144)

```solidity
📁 File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

/// @audit function is 131 lines long
68:     function get( 
69:         bytes memory _key,
70:         bytes[] memory _proof,
71:         bytes32 _root
72:     )
```
[68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L68-L72)

```solidity
📁 File: contracts/thirdparty/solmate/LibFixedPointMath.sol

/// @audit function is 68 lines long
13:     function exp(int256 x) internal pure returns (int256 r) { 
```
[13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L13)

</details>


---
### [NC&#x2011;11] Consider adding a block/deny-list
Doing so will significantly increase centralization, but will help to prevent hackers from using stolen tokens

<details>
<summary><i>There are 30 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoL1.sol

22: contract TaikoL1 is EssentialContract, ITaikoL1, TaikoEvents, TaikoErrors { 
23:     /// @notice The TaikoL1 state.
24:     TaikoData.State public state;
25: 
26:     uint256[50] private __gap;
27: 
28:     modifier whenProvingNotPaused() {
29:         if (state.slotB.provingPaused) revert L1_PROVING_PAUSED();
30:         _;
31:     }
32: 
```
[22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L22-L32)

```solidity
📁 File: contracts/L1/TaikoToken.sol

15: contract TaikoToken is EssentialContract, ERC20SnapshotUpgradeable, ERC20VotesUpgradeable { 
16:     uint256[50] private __gap;
17: 
18:     error TKO_INVALID_ADDR();
19: 
20:     /// @notice Initializes the contract.
21:     /// @param _owner The owner of this contract. msg.sender will be used if this value is zero.
22:     /// @param _name The name of the token.
23:     /// @param _symbol The symbol of the token.
24:     /// @param _recipient The address to receive initial token minting.
25:     function init(
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L15-L25)

```solidity
📁 File: contracts/L1/gov/TaikoGovernor.sol

16: contract TaikoGovernor is 
17:     EssentialContract,
18:     GovernorCompatibilityBravoUpgradeable,
19:     GovernorVotesUpgradeable,
20:     GovernorVotesQuorumFractionUpgradeable,
21:     GovernorTimelockControlUpgradeable
22: {
23:     uint256[50] private __gap;
24: 
25:     error TG_INVALID_SIGNATURES_LENGTH();
26: 
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L16-L26)

```solidity
📁 File: contracts/L1/gov/TaikoTimelockController.sol

9: contract TaikoTimelockController is EssentialContract, TimelockControllerUpgradeable { 
10:     uint256[50] private __gap;
11: 
12:     /// @notice Initializes the contract.
13:     /// @param _owner The owner of this contract. msg.sender will be used if this value is zero.
14:     /// @param _minDelay The minimal delay.
15:     function init(address _owner, uint256 _minDelay) external initializer {
16:         __Essential_init(_owner);
17:         address[] memory nil = new address[](0);
18:         __TimelockController_init(_minDelay, nil, nil, owner());
19:     }
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L9-L19)

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

14: contract AssignmentHook is EssentialContract, IHook { 
15:     using LibAddress for address;
16:     using SafeERC20 for IERC20;
17: 
18:     struct ProverAssignment {
19:         address feeToken;
20:         uint64 expiry;
21:         uint64 maxBlockId;
22:         uint64 maxProposedIn;
23:         bytes32 metaHash;
24:         bytes32 parentMetaHash;
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L14-L24)

```solidity
📁 File: contracts/L1/provers/GuardianProver.sol

10: contract GuardianProver is Guardians { 
11:     uint256[50] private __gap;
12: 
13:     /// @notice Emitted when a guardian proof is approved.
14:     /// @param addr The address of the guardian.
15:     /// @param blockId The block ID.
16:     /// @param blockHash The block hash.
17:     /// @param approved If the proof is approved.
18:     event GuardianApproval(
19:         address indexed addr, uint256 indexed blockId, bytes32 blockHash, bool approved
20:     );
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L10-L20)

```solidity
📁 File: contracts/L1/tiers/DevnetTierProvider.sol

10: contract DevnetTierProvider is EssentialContract, ITierProvider { 
11:     uint256[50] private __gap;
12: 
13:     /// @notice Initializes the contract.
14:     /// @param _owner The owner of this contract. msg.sender will be used if this value is zero.
15:     function init(address _owner) external initializer {
16:         __Essential_init(_owner);
17:     }
18: 
19:     /// @inheritdoc ITierProvider
20:     function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L10-L20)

```solidity
📁 File: contracts/L1/tiers/MainnetTierProvider.sol

10: contract MainnetTierProvider is EssentialContract, ITierProvider { 
11:     uint256[50] private __gap;
12: 
13:     /// @notice Initializes the contract.
14:     /// @param _owner The owner of this contract. msg.sender will be used if this value is zero.
15:     function init(address _owner) external initializer {
16:         __Essential_init(_owner);
17:     }
18: 
19:     /// @inheritdoc ITierProvider
20:     function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L10-L20)

```solidity
📁 File: contracts/L1/tiers/TestnetTierProvider.sol

10: contract TestnetTierProvider is EssentialContract, ITierProvider { 
11:     uint256[50] private __gap;
12: 
13:     /// @notice Initializes the contract.
14:     /// @param _owner The owner of this contract. msg.sender will be used if this value is zero.
15:     function init(address _owner) external initializer {
16:         __Essential_init(_owner);
17:     }
18: 
19:     /// @inheritdoc ITierProvider
20:     function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L10-L20)

```solidity
📁 File: contracts/L2/TaikoL2.sol

21: contract TaikoL2 is CrossChainOwned { 
22:     using LibAddress for address;
23:     using LibMath for uint256;
24:     using SafeERC20 for IERC20;
25: 
26:     struct Config {
27:         uint32 gasTargetPerL1Block;
28:         uint8 basefeeAdjustmentQuotient;
29:     }
30: 
31:     /// @notice Golden touch address is the only address that can do the anchor transaction.
```
[21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L21-L31)

```solidity
📁 File: contracts/L2/TaikoL2EIP1559Configurable.sol

9: contract TaikoL2EIP1559Configurable is TaikoL2 { 
10:     /// @notice EIP-1559 configuration.
11:     Config public customConfig;
12: 
13:     uint256[49] private __gap;
14: 
15:     /// @notice Emits when the EIP-1559 configuration and gas excess are changed.
16:     /// @param config The new EIP-1559 config.
17:     /// @param gasExcess The new gas excess.
18:     event ConfigAndExcessChanged(Config config, uint64 gasExcess);
19: 
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L9-L19)

```solidity
📁 File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

22: contract AutomataDcapV3Attestation is IAttestation { 
23:     using BytesUtils for bytes;
24: 
25:     ISigVerifyLib public immutable sigVerifyLib;
26:     IPEMCertChainLib public immutable pemCertLib;
27: 
28:     // https://github.com/intel/SGXDataCenterAttestationPrimitives/blob/e7604e02331b3377f3766ed3653250e03af72d45/QuoteVerification/QVL/Src/AttestationLibrary/src/CertVerification/X509Constants.h#L64
29:     uint256 internal constant CPUSVN_LENGTH = 16;
30: 
31:     // keccak256(hex"0ba9c4c0c0c86193a3fe23d6b02cda10a8bbd4e88e48b4458561a36e705525f567918e2edc88e40d860bd0cc4ee26aacc988e505a953558c453f6b0904ae7394")
32:     // the uncompressed (0x04) prefix is not included in the pubkey pre-image
```
[22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L22-L32)

```solidity
📁 File: contracts/automata-attestation/lib/PEMCertChainLib.sol

12: contract PEMCertChainLib is IPEMCertChainLib { 
13:     using Asn1Decode for bytes;
14:     using NodePtr for uint256;
15:     using BytesUtils for bytes;
16: 
17:     string internal constant HEADER = "-----BEGIN CERTIFICATE-----";
18:     string internal constant FOOTER = "-----END CERTIFICATE-----";
19:     uint256 internal constant HEADER_LENGTH = 27;
20:     uint256 internal constant FOOTER_LENGTH = 25;
21: 
22:     string internal constant PCK_COMMON_NAME = "Intel SGX PCK Certificate";
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L12-L22)

```solidity
📁 File: contracts/automata-attestation/utils/SigVerifyLib.sol

15: contract SigVerifyLib is ISigVerifyLib { 
16:     using BytesUtils for bytes;
17: 
18:     address private ES256VERIFIER;
19: 
20:     constructor(address es256Verifier) {
21:         ES256VERIFIER = es256Verifier;
22:     }
23: 
24:     function verifyAttStmtSignature(
25:         bytes memory tbs,
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L15-L25)

```solidity
📁 File: contracts/bridge/Bridge.sol

16: contract Bridge is EssentialContract, IBridge { 
17:     using Address for address;
18:     using LibAddress for address;
19:     using LibAddress for address payable;
20: 
21:     /// @dev The slot in transient storage of the call context. This is the keccak256 hash
22:     /// of "bridge.ctx_slot"
23:     bytes32 private constant _CTX_SLOT =
24:         0xe4ece82196de19aabe639620d7f716c433d1348f96ce727c9989a982dbadc2b9;
25: 
26:     /// @dev Place holder value when not using transient storage
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L16-L26)

```solidity
📁 File: contracts/common/AddressManager.sol

10: contract AddressManager is EssentialContract, IAddressManager { 
11:     /// @dev Mapping of chainId to mapping of name to address.
12:     mapping(uint256 chainId => mapping(bytes32 name => address addr)) private __addresses;
13: 
14:     uint256[49] private __gap;
15: 
16:     /// @notice Emitted when an address is set.
17:     /// @param chainId The chainId for the address mapping.
18:     /// @param name The name for the address mapping.
19:     /// @param newAddress The new address.
20:     /// @param oldAddress The old address.
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L10-L20)

```solidity
📁 File: contracts/signal/SignalService.sol

14: contract SignalService is EssentialContract, ISignalService { 
15:     /// @notice Mapping to store the top blockId.
16:     /// @dev Slot 1.
17:     mapping(uint64 chainId => mapping(bytes32 kind => uint64 blockId)) public topBlockId;
18: 
19:     /// @notice Mapping to store the authorized addresses.
20:     /// @dev Slot 2.
21:     mapping(address addr => bool authorized) public isAuthorized;
22: 
23:     uint256[48] private __gap;
24: 
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L14-L24)

```solidity
📁 File: contracts/team/TimelockTokenPool.sol

25: contract TimelockTokenPool is EssentialContract { 
26:     using SafeERC20 for IERC20;
27: 
28:     struct Grant {
29:         uint128 amount;
30:         // If non-zero, each TKO (1E18) will need some USD stable to purchase.
31:         uint128 costPerToken;
32:         // If non-zero, indicates the start time for the recipient to receive
33:         // tokens, subject to an unlocking schedule.
34:         uint64 grantStart;
35:         // If non-zero, indicates the time after which the token to be received
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L25-L35)

```solidity
📁 File: contracts/team/airdrop/ERC20Airdrop.sol

11: contract ERC20Airdrop is MerkleClaimable { 
12:     /// @notice The address of the token contract.
13:     address public token;
14: 
15:     /// @notice The address of the vault contract.
16:     address public vault;
17: 
18:     uint256[48] private __gap;
19: 
20:     /// @notice Initializes the contract.
21:     /// @param _owner The owner of this contract.
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L11-L21)

```solidity
📁 File: contracts/team/airdrop/ERC20Airdrop2.sol

12: contract ERC20Airdrop2 is MerkleClaimable { 
13:     using LibMath for uint256;
14: 
15:     /// @notice The address of the token contract.
16:     address public token;
17: 
18:     /// @notice The address of the vault contract.
19:     address public vault;
20: 
21:     /// @notice Represents the token amount for which the user has claimed.
22:     mapping(address addr => uint256 amountClaimed) public claimedAmount;
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L12-L22)

```solidity
📁 File: contracts/team/airdrop/ERC721Airdrop.sol

9: contract ERC721Airdrop is MerkleClaimable { 
10:     /// @notice The address of the token contract.
11:     address public token;
12: 
13:     /// @notice The address of the vault contract.
14:     address public vault;
15: 
16:     uint256[48] private __gap;
17: 
18:     /// @notice Initializes the contract.
19:     /// @param _owner The owner of this contract.
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L9-L19)

```solidity
📁 File: contracts/tokenvault/BridgedERC1155.sol

14: contract BridgedERC1155 is EssentialContract, IERC1155MetadataURIUpgradeable, ERC1155Upgradeable { 
15:     /// @notice Address of the source token contract.
16:     address public srcToken;
17: 
18:     /// @notice Source chain ID where the token originates.
19:     uint256 public srcChainId;
20: 
21:     /// @dev Symbol of the bridged token.
22:     string private __symbol;
23: 
24:     /// @dev Name of the bridged token.
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L14-L24)

```solidity
📁 File: contracts/tokenvault/BridgedERC20.sol

15: contract BridgedERC20 is 
16:     BridgedERC20Base,
17:     IERC20MetadataUpgradeable,
18:     ERC20SnapshotUpgradeable,
19:     ERC20VotesUpgradeable
20: {
21:     /// @dev Slot 1.
22:     address public srcToken;
23: 
24:     uint8 private __srcDecimals;
25: 
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L15-L25)

```solidity
📁 File: contracts/tokenvault/BridgedERC721.sol

12: contract BridgedERC721 is EssentialContract, ERC721Upgradeable { 
13:     /// @notice Address of the source token contract.
14:     address public srcToken;
15: 
16:     /// @notice Source chain ID where the token originates.
17:     uint256 public srcChainId;
18: 
19:     uint256[48] private __gap;
20: 
21:     error BTOKEN_CANNOT_RECEIVE();
22:     error BTOKEN_INVALID_BURN();
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L12-L22)

```solidity
📁 File: contracts/tokenvault/ERC1155Vault.sol

29: contract ERC1155Vault is BaseNFTVault, ERC1155ReceiverUpgradeable { 
30:     using LibAddress for address;
31: 
32:     uint256[50] private __gap;
33: 
34:     /// @notice Transfers ERC1155 tokens to this vault and sends a message to
35:     /// the destination chain so the user can receive the same (bridged) tokens
36:     /// by invoking the message call.
37:     /// @param _op Option for sending the ERC1155 token.
38:     /// @return message_ The constructed message.
39:     function sendToken(BridgeTransferOp memory _op)
```
[29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L29-L39)

```solidity
📁 File: contracts/tokenvault/ERC20Vault.sol

18: contract ERC20Vault is BaseVault { 
19:     using LibAddress for address;
20:     using SafeERC20 for IERC20;
21: 
22:     /// @dev Represents a canonical ERC20 token.
23:     struct CanonicalERC20 {
24:         uint64 chainId;
25:         address addr;
26:         uint8 decimals;
27:         string symbol;
28:         string name;
```
[18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L18-L28)

```solidity
📁 File: contracts/tokenvault/ERC721Vault.sol

16: contract ERC721Vault is BaseNFTVault, IERC721Receiver { 
17:     using LibAddress for address;
18: 
19:     uint256[50] private __gap;
20: 
21:     /// @notice Transfers ERC721 tokens to this vault and sends a message to the
22:     /// destination chain so the user can receive the same (bridged) tokens
23:     /// by invoking the message call.
24:     /// @param _op Option for sending the ERC721 token.
25:     /// @return message_ The constructed message.
26:     function sendToken(BridgeTransferOp memory _op)
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L16-L26)

```solidity
📁 File: contracts/tokenvault/adapters/USDCAdapter.sol

28: contract USDCAdapter is BridgedERC20Base { 
29:     /// @notice The USDC instance.
30:     /// @dev Slot 1.
31:     IUSDC public usdc;
32:     uint256[49] private __gap;
33: 
34:     /// @notice Initializes the contract.
35:     /// @param _owner The owner of this contract.
36:     /// @param _addressManager The address of the {AddressManager} contract.
37:     /// @param _usdc The USDC instance.
38:     function init(address _owner, address _addressManager, IUSDC _usdc) external initializer {
```
[28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L28-L38)

```solidity
📁 File: contracts/verifiers/GuardianVerifier.sol

10: contract GuardianVerifier is EssentialContract, IVerifier { 
11:     uint256[50] private __gap;
12: 
13:     error PERMISSION_DENIED();
14: 
15:     /// @notice Initializes the contract.
16:     /// @param _owner The owner of this contract. msg.sender will be used if this value is zero.
17:     /// @param _addressManager The address of the {AddressManager} contract.
18:     function init(address _owner, address _addressManager) external initializer {
19:         __Essential_init(_owner, _addressManager);
20:     }
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L10-L20)

```solidity
📁 File: contracts/verifiers/SgxVerifier.sol

19: contract SgxVerifier is EssentialContract, IVerifier { 
20:     /// @dev Each public-private key pair (Ethereum address) is generated within
21:     /// the SGX program when it boots up. The off-chain remote attestation
22:     /// ensures the validity of the program hash and has the capability of
23:     /// bootstrapping the network with trustworthy instances.
24:     struct Instance {
25:         address addr;
26:         uint64 validSince;
27:     }
28: 
29:     /// @notice The expiry time for the SGX instance.
```
[19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L19-L29)

</details>


---
### [NC&#x2011;12] Consider disallowing transfers to `address(this)`
<details>
<summary><i>There are 5 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoToken.sol

60:     function transfer(address _to, uint256 _amount) public override returns (bool) { 

70:     function transferFrom( 
71:         address _from,
72:         address _to,
73:         uint256 _amount
74:     )
75:         public
76:         override
77:         returns (bool)
78:     {
```
[60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L60), [70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L70-L78)

```solidity
📁 File: contracts/L2/TaikoL2.sol

163:     function withdraw( 
164:         address _token,
165:         address _to
166:     )
167:         external
168:         onlyFromOwnerOrNamed("withdrawer")
169:         nonReentrant
170:         whenNotPaused
171:     {
```
[163](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L163-L171)

```solidity
📁 File: contracts/team/TimelockTokenPool.sol

168:     function withdraw(address _to, bytes memory _sig) external { 
```
[168](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L168)

```solidity
📁 File: contracts/team/airdrop/ERC20Airdrop2.sol

88:     function withdraw(address user) external ongoingWithdrawals { 
```
[88](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L88)

</details>


---
### [NC&#x2011;13] Consider making contracts `Upgradeable`
This allows for bugs to be fixed in production, at the expense of *significantly* increasing centralization.

<details>
<summary><i>There are 31 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoErrors.sol

/// @audit contract TaikoErrors is not upgradeable
11: abstract contract TaikoErrors { 
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoErrors.sol#L11)

```solidity
📁 File: contracts/L1/TaikoEvents.sol

/// @audit contract TaikoEvents is not upgradeable
13: abstract contract TaikoEvents { 
```
[13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L13)

```solidity
📁 File: contracts/L1/TaikoL1.sol

/// @audit contract TaikoL1 is not upgradeable
22: contract TaikoL1 is EssentialContract, ITaikoL1, TaikoEvents, TaikoErrors { 
```
[22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L22)

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

/// @audit contract AssignmentHook is not upgradeable
14: contract AssignmentHook is EssentialContract, IHook { 
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L14)

```solidity
📁 File: contracts/L1/provers/GuardianProver.sol

/// @audit contract GuardianProver is not upgradeable
10: contract GuardianProver is Guardians { 
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L10)

```solidity
📁 File: contracts/L1/provers/Guardians.sol

/// @audit contract Guardians is not upgradeable
9: abstract contract Guardians is EssentialContract { 
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L9)

```solidity
📁 File: contracts/L1/tiers/DevnetTierProvider.sol

/// @audit contract DevnetTierProvider is not upgradeable
10: contract DevnetTierProvider is EssentialContract, ITierProvider { 
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L10)

```solidity
📁 File: contracts/L1/tiers/MainnetTierProvider.sol

/// @audit contract MainnetTierProvider is not upgradeable
10: contract MainnetTierProvider is EssentialContract, ITierProvider { 
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L10)

```solidity
📁 File: contracts/L1/tiers/TestnetTierProvider.sol

/// @audit contract TestnetTierProvider is not upgradeable
10: contract TestnetTierProvider is EssentialContract, ITierProvider { 
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L10)

```solidity
📁 File: contracts/L2/CrossChainOwned.sol

/// @audit contract CrossChainOwned is not upgradeable
14: abstract contract CrossChainOwned is EssentialContract, IMessageInvocable { 
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L14)

```solidity
📁 File: contracts/L2/TaikoL2.sol

/// @audit contract TaikoL2 is not upgradeable
21: contract TaikoL2 is CrossChainOwned { 
```
[21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L21)

```solidity
📁 File: contracts/L2/TaikoL2EIP1559Configurable.sol

/// @audit contract TaikoL2EIP1559Configurable is not upgradeable
9: contract TaikoL2EIP1559Configurable is TaikoL2 { 
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L9)

```solidity
📁 File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

/// @audit contract AutomataDcapV3Attestation is not upgradeable
22: contract AutomataDcapV3Attestation is IAttestation { 
```
[22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L22)

```solidity
📁 File: contracts/automata-attestation/lib/PEMCertChainLib.sol

/// @audit contract PEMCertChainLib is not upgradeable
12: contract PEMCertChainLib is IPEMCertChainLib { 
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L12)

```solidity
📁 File: contracts/automata-attestation/utils/SigVerifyLib.sol

/// @audit contract SigVerifyLib is not upgradeable
15: contract SigVerifyLib is ISigVerifyLib { 
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L15)

```solidity
📁 File: contracts/bridge/Bridge.sol

/// @audit contract Bridge is not upgradeable
16: contract Bridge is EssentialContract, IBridge { 
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L16)

```solidity
📁 File: contracts/common/AddressManager.sol

/// @audit contract AddressManager is not upgradeable
10: contract AddressManager is EssentialContract, IAddressManager { 
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L10)

```solidity
📁 File: contracts/common/AddressResolver.sol

/// @audit contract AddressResolver is not upgradeable
11: abstract contract AddressResolver is IAddressResolver, Initializable { 
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L11)

```solidity
📁 File: contracts/signal/SignalService.sol

/// @audit contract SignalService is not upgradeable
14: contract SignalService is EssentialContract, ISignalService { 
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L14)

```solidity
📁 File: contracts/team/TimelockTokenPool.sol

/// @audit contract TimelockTokenPool is not upgradeable
25: contract TimelockTokenPool is EssentialContract { 
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L25)

```solidity
📁 File: contracts/team/airdrop/ERC20Airdrop.sol

/// @audit contract ERC20Airdrop is not upgradeable
11: contract ERC20Airdrop is MerkleClaimable { 
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L11)

```solidity
📁 File: contracts/team/airdrop/ERC20Airdrop2.sol

/// @audit contract ERC20Airdrop2 is not upgradeable
12: contract ERC20Airdrop2 is MerkleClaimable { 
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L12)

```solidity
📁 File: contracts/team/airdrop/ERC721Airdrop.sol

/// @audit contract ERC721Airdrop is not upgradeable
9: contract ERC721Airdrop is MerkleClaimable { 
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L9)

```solidity
📁 File: contracts/team/airdrop/MerkleClaimable.sol

/// @audit contract MerkleClaimable is not upgradeable
10: abstract contract MerkleClaimable is EssentialContract { 
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L10)

```solidity
📁 File: contracts/tokenvault/BaseNFTVault.sol

/// @audit contract BaseNFTVault is not upgradeable
9: abstract contract BaseNFTVault is BaseVault { 
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L9)

```solidity
📁 File: contracts/tokenvault/BridgedERC20Base.sol

/// @audit contract BridgedERC20Base is not upgradeable
9: abstract contract BridgedERC20Base is EssentialContract, IBridgedERC20 { 
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L9)

```solidity
📁 File: contracts/tokenvault/ERC20Vault.sol

/// @audit contract ERC20Vault is not upgradeable
18: contract ERC20Vault is BaseVault { 
```
[18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L18)

```solidity
📁 File: contracts/tokenvault/ERC721Vault.sol

/// @audit contract ERC721Vault is not upgradeable
16: contract ERC721Vault is BaseNFTVault, IERC721Receiver { 
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L16)

```solidity
📁 File: contracts/tokenvault/adapters/USDCAdapter.sol

/// @audit contract USDCAdapter is not upgradeable
28: contract USDCAdapter is BridgedERC20Base { 
```
[28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L28)

```solidity
📁 File: contracts/verifiers/GuardianVerifier.sol

/// @audit contract GuardianVerifier is not upgradeable
10: contract GuardianVerifier is EssentialContract, IVerifier { 
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L10)

```solidity
📁 File: contracts/verifiers/SgxVerifier.sol

/// @audit contract SgxVerifier is not upgradeable
19: contract SgxVerifier is EssentialContract, IVerifier { 
```
[19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L19)

</details>


---
### [NC&#x2011;14] Consider moving duplicated strings to constants
<details>
<summary><i>There are 40 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

/// @audit 'taiko' is seen 4 times
70:         onlyFromNamed("taiko") 

/// @audit 'taiko_token' is seen 4 times
101:         IERC20 tko = IERC20(resolve("taiko_token", false)); 
```
[70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L70), [101](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L101)

```solidity
📁 File: contracts/L1/libs/LibDepositing.sol

/// @audit 'bridge' is seen 8 times
41:         _resolver.resolve("bridge", false).sendEther(msg.value); 
```
[41](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L41)

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

/// @audit 'tier_provider' is seen 3 times
207:         meta_.minTier = ITierProvider(_resolver.resolve("tier_provider", false)).getMinTier( 

/// @audit 'taiko_token' is seen 4 times
237:             IERC20 tko = IERC20(_resolver.resolve("taiko_token", false)); 
```
[207](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L207), [237](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L237)

```solidity
📁 File: contracts/L1/libs/LibProving.sol

/// @audit 'tier_optimistic' is seen 3 times
23:     bytes32 public constant TIER_OP = bytes32("tier_optimistic"); 

/// @audit 'tier_provider' is seen 3 times
141:             ITierProvider(_resolver.resolve("tier_provider", false)).getTier(_proof.tier); 

/// @audit 'taiko_token' is seen 4 times
187:         IERC20 tko = IERC20(_resolver.resolve("taiko_token", false)); 
```
[23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L23), [141](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L141), [187](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L187)

```solidity
📁 File: contracts/L1/libs/LibVerifying.sol

/// @audit 'tier_provider' is seen 3 times
149:                         tierProvider = _resolver.resolve("tier_provider", false); 

/// @audit 'taiko_token' is seen 4 times
188:                 IERC20 tko = IERC20(_resolver.resolve("taiko_token", false)); 

/// @audit 'signal_service' is seen 11 times
232:         ISignalService signalService = ISignalService(_resolver.resolve("signal_service", false)); 
```
[149](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L149), [188](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L188), [232](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L232)

```solidity
📁 File: contracts/L1/provers/GuardianProver.sol

/// @audit 'taiko' is seen 4 times
51:             ITaikoL1(resolve("taiko", false)).proveBlock(_meta.id, abi.encode(_meta, _tran, _proof)); 
```
[51](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L51)

```solidity
📁 File: contracts/L1/tiers/DevnetTierProvider.sol

/// @audit 'tier_optimistic' is seen 3 times
23:                 verifierName: "tier_optimistic", 

/// @audit 'tier_guardian' is seen 3 times
34:                 verifierName: "tier_guardian", 
```
[23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L23), [34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L34)

```solidity
📁 File: contracts/L1/tiers/MainnetTierProvider.sol

/// @audit 'tier_sgx' is seen 2 times
23:                 verifierName: "tier_sgx", 

/// @audit 'tier_guardian' is seen 3 times
45:                 verifierName: "tier_guardian", 
```
[23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L23), [45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L45)

```solidity
📁 File: contracts/L1/tiers/TestnetTierProvider.sol

/// @audit 'tier_optimistic' is seen 3 times
23:                 verifierName: "tier_optimistic", 

/// @audit 'tier_sgx' is seen 2 times
34:                 verifierName: "tier_sgx", 

/// @audit 'tier_guardian' is seen 3 times
45:                 verifierName: "tier_guardian", 
```
[23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L23), [34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L34), [45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L45)

```solidity
📁 File: contracts/L2/CrossChainOwned.sol

/// @audit 'bridge' is seen 8 times
40:         onlyFromNamed("bridge") 
```
[40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L40)

```solidity
📁 File: contracts/L2/TaikoL2.sol

/// @audit 'signal_service' is seen 11 times
148:             ISignalService(resolve("signal_service", false)).syncChainData( 
```
[148](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L148)

```solidity
📁 File: contracts/bridge/Bridge.sol

/// @audit 'bridge_watchdog' is seen 2 times
87:         onlyFromOwnerOrNamed("bridge_watchdog") 

/// @audit 'bridge_watchdog' is seen 2 times
106:         onlyFromOwnerOrNamed("bridge_watchdog") 

/// @audit 'signal_service' is seen 11 times
150:         ISignalService(resolve("signal_service", false)).sendSignal(msgHash_); 

/// @audit 'signal_service' is seen 11 times
172:             address signalService = resolve("signal_service", false); 

/// @audit 'signal_service' is seen 11 times
229:         address signalService = resolve("signal_service", false); 

/// @audit 'signal_service' is seen 11 times
342:         return ISignalService(resolve("signal_service", false)).isSignalSent({ 

/// @audit 'signal_service' is seen 11 times
363:             resolve("signal_service", false), 

/// @audit 'signal_service' is seen 11 times
384:             resolve("signal_service", false), hashMessage(_message), _message.srcChainId, _proof 

/// @audit 'bridge' is seen 8 times
397:         destBridge_ = resolve(_chainId, "bridge", true); 

/// @audit 'signal_service' is seen 11 times
522:             ISignalService(resolve("signal_service", false)).sendSignal( 

/// @audit 'bridge' is seen 8 times
589:             (_chainId, resolve(_chainId, "bridge", false), _signal, _proof) 
```
[87](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L87), [106](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L106), [150](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L150), [172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L172), [229](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L229), [342](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L342), [363](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L363), [384](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L384), [397](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L397), [522](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L522), [589](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L589)

```solidity
📁 File: contracts/signal/SignalService.sol

/// @audit 'signal_service' is seen 11 times
101:         address signalService = resolve(chainId, "signal_service", false); 

/// @audit 'signal_service' is seen 11 times
117:                 signalService = resolve(hop.chainId, "signal_service", false); 
```
[101](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L101), [117](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L117)

```solidity
📁 File: contracts/tokenvault/BaseVault.sol

/// @audit 'bridge' is seen 8 times
23:         if (msg.sender != resolve("bridge", false)) { 
```
[23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L23)

```solidity
📁 File: contracts/tokenvault/ERC1155Vault.sol

/// @audit 'bridge' is seen 8 times
77:             IBridge(resolve("bridge", false)).sendMessage{ value: msg.value }(message); 
```
[77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L77)

```solidity
📁 File: contracts/tokenvault/ERC20Vault.sol

/// @audit 'bridge' is seen 8 times
239:             IBridge(resolve("bridge", false)).sendMessage{ value: msg.value }(message); 
```
[239](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L239)

```solidity
📁 File: contracts/tokenvault/ERC721Vault.sol

/// @audit 'bridge' is seen 8 times
62:             IBridge(resolve("bridge", false)).sendMessage{ value: msg.value }(message); 
```
[62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L62)

```solidity
📁 File: contracts/verifiers/SgxVerifier.sol

/// @audit 'taiko' is seen 4 times
145:         onlyFromNamed("taiko") 

/// @audit 'taiko' is seen 4 times
181:         address taikoL1 = resolve("taiko", false); 
```
[145](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L145), [181](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L181)

</details>


---
### [NC&#x2011;15] Consider moving `msg.sender` checks to a common authorization `modifier`
<details>
<summary><i>There are 5 instances of this issue:</i></summary>

```solidity
📁 File: contracts/bridge/Bridge.sol

260:             if (_message.gasLimit == 0 && msg.sender != _message.destOwner) { 
261:                 revert B_PERMISSION_DENIED();
262:             }

280:                 uint256 gasLimit = msg.sender == _message.destOwner ? gasleft() : _message.gasLimit; 

322:             if (msg.sender != _message.destOwner) revert B_PERMISSION_DENIED(); 
```
[260](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L260-L262), [280](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L280), [322](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L322)

```solidity
📁 File: contracts/tokenvault/BridgedERC20Base.sol

64:         } else if (msg.sender != resolve("erc20_vault", true)) { 
65:             // Bridging from vault
66:             revert BB_PERMISSION_DENIED();
67:         }

83:         } else if (msg.sender != resolve("erc20_vault", true)) { 
84:             // Only the vault can burn tokens when not migrating out
85:             revert RESOLVER_DENIED();
86:         }
```
[64](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L64-L67), [83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L83-L86)

</details>


---
### [NC&#x2011;16] Consider providing a ranged getter for array state variables
While the compiler automatically provides a getter for accessing single elements within a public state variable array, it doesn't provide a way to fetch the whole array, or subsets thereof. Consider adding a function to allow the fetching of slices of the array, especially if the contract doesn't already have multicall functionality.

<details>
<summary><i>There are 40 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoData.sol

87:         HookCall[] hookCalls; 

195:         uint256[43] __gap; 
```
[87](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L87), [195](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L195)

```solidity
📁 File: contracts/L1/TaikoL1.sol

26:     uint256[50] private __gap; 
```
[26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L26)

```solidity
📁 File: contracts/L1/TaikoToken.sol

16:     uint256[50] private __gap; 
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L16)

```solidity
📁 File: contracts/L1/gov/TaikoGovernor.sol

23:     uint256[50] private __gap; 
```
[23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L23)

```solidity
📁 File: contracts/L1/gov/TaikoTimelockController.sol

10:     uint256[50] private __gap; 
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L10)

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

25:         TaikoData.TierFee[] tierFees; 

40:     uint256[50] private __gap; 
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L25), [40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L40)

```solidity
📁 File: contracts/L1/provers/GuardianProver.sol

11:     uint256[50] private __gap; 
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L11)

```solidity
📁 File: contracts/L1/provers/Guardians.sol

23:     address[] public guardians; 

32:     uint256[46] private __gap; 
```
[23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L23), [32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L32)

```solidity
📁 File: contracts/L1/tiers/DevnetTierProvider.sol

11:     uint256[50] private __gap; 
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L11)

```solidity
📁 File: contracts/L1/tiers/MainnetTierProvider.sol

11:     uint256[50] private __gap; 
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L11)

```solidity
📁 File: contracts/L1/tiers/TestnetTierProvider.sol

11:     uint256[50] private __gap; 
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L11)

```solidity
📁 File: contracts/L2/CrossChainOwned.sol

21:     uint256[49] private __gap; 
```
[21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L21)

```solidity
📁 File: contracts/L2/TaikoL2.sol

52:     uint256[47] private __gap; 
```
[52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L52)

```solidity
📁 File: contracts/L2/TaikoL2EIP1559Configurable.sol

13:     uint256[49] private __gap; 
```
[13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L13)

```solidity
📁 File: contracts/bridge/Bridge.sol

48:     uint256[43] private __gap; 
```
[48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L48)

```solidity
📁 File: contracts/common/AddressManager.sol

14:     uint256[49] private __gap; 
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L14)

```solidity
📁 File: contracts/common/AddressResolver.sol

14:     uint256[49] private __gap; 
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L14)

```solidity
📁 File: contracts/common/EssentialContract.sol

25:     uint256[49] private __gap; 
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L25)

```solidity
📁 File: contracts/signal/ISignalService.sol

25:         bytes[] accountProof; 
26:         bytes[] storageProof;
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L25-L26)

```solidity
📁 File: contracts/signal/SignalService.sol

23:     uint256[48] private __gap; 
```
[23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L23)

```solidity
📁 File: contracts/team/airdrop/ERC20Airdrop.sol

18:     uint256[48] private __gap; 
```
[18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L18)

```solidity
📁 File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

17:         RLPReader.RLPItem[] decoded; 
```
[17](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L17)

```solidity
📁 File: contracts/tokenvault/BaseNFTVault.sol

33:         uint256[] tokenIds; 

35:         uint256[] amounts; 

61:     uint256[48] private __gap; 
```
[33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L33), [35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L35), [61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L61)

```solidity
📁 File: contracts/tokenvault/BaseVault.sol

18:     uint256[50] private __gap; 
```
[18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L18)

```solidity
📁 File: contracts/tokenvault/BridgedERC1155.sol

27:     uint256[46] private __gap; 
```
[27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L27)

```solidity
📁 File: contracts/tokenvault/BridgedERC20.sol

32:     uint256[47] private __gap; 
```
[32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L32)

```solidity
📁 File: contracts/tokenvault/BridgedERC20Base.sol

16:     uint256[49] private __gap; 
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L16)

```solidity
📁 File: contracts/tokenvault/BridgedERC721.sol

19:     uint256[48] private __gap; 
```
[19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L19)

```solidity
📁 File: contracts/tokenvault/ERC1155Vault.sol

32:     uint256[50] private __gap; 
```
[32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L32)

```solidity
📁 File: contracts/tokenvault/ERC20Vault.sol

54:     uint256[47] private __gap; 
```
[54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L54)

```solidity
📁 File: contracts/tokenvault/ERC721Vault.sol

19:     uint256[50] private __gap; 
```
[19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L19)

```solidity
📁 File: contracts/tokenvault/adapters/USDCAdapter.sol

32:     uint256[49] private __gap; 
```
[32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L32)

```solidity
📁 File: contracts/verifiers/GuardianVerifier.sol

11:     uint256[50] private __gap; 
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L11)

```solidity
📁 File: contracts/verifiers/SgxVerifier.sol

57:     uint256[47] private __gap; 
```
[57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L57)

</details>


---
### [NC&#x2011;17] Consider using `delete` rather than assigning zero to clear values
The `delete` keyword more closely matches the semantics of what is being done, and draws more attention to the changing of state, which may lead to a more thorough audit of its associated logic.

<details>
<summary><i>There are 14 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

190:             meta_.txListByteOffset = 0; 
```
[190](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L190)

```solidity
📁 File: contracts/L1/libs/LibProving.sol

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
[197](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L197), [300](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L300-L303), [306](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L306-L307), [332](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L332), [390](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L390)

```solidity
📁 File: contracts/L1/libs/LibVerifying.sol

70:         ts.prover = address(0); 
```
[70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L70)

```solidity
📁 File: contracts/automata-attestation/lib/PEMCertChainLib.sol

336:                 tbsPtr = 0; // exit 
```
[336](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L336)

```solidity
📁 File: contracts/team/TimelockTokenPool.sol

231:         _grant.grantStart = 0; 
232:         _grant.grantPeriod = 0;
```
[231](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L231-L232)

</details>


---
### [NC&#x2011;18] Consider using named function arguments
When calling functions in external contracts with multiple arguments, consider using [named](https://docs.soliditylang.org/en/latest/control-structures.html#function-calls-with-named-parameters) function parameters, rather than positional ones.

<details>
<summary><i>There are 15 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/gov/TaikoGovernor.sol

58:         return super.propose(_targets, _values, _calldatas, _description); 

83:         return GovernorCompatibilityBravoUpgradeable.propose( 
84:             _targets, _values, _signatures, _calldatas, _description
85:         );

137:         super._execute(_proposalId, _targets, _values, _calldatas, _descriptionHash); 

150:         return super._cancel(_targets, _values, _calldatas, _descriptionHash); 
```
[58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L58), [83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L83-L85), [137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L137), [150](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L150)

```solidity
📁 File: contracts/L1/libs/LibProving.sol

177:                 IVerifier(verifier).verifyProof(ctx, _tran, _proof); 
```
[177](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L177)

```solidity
📁 File: contracts/L1/libs/LibVerifying.sol

234:         (uint64 lastSyncedBlock,) = signalService.getSyncedChainData( 
235:             _config.chainId, LibSignals.STATE_ROOT, 0 /* latest block Id*/
236:         );

239:             signalService.syncChainData( 
240:                 _config.chainId, LibSignals.STATE_ROOT, _lastVerifiedBlockId, _stateRoot
241:             );
```
[234](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L234-L236), [239](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L239-L241)

```solidity
📁 File: contracts/L2/TaikoL2.sol

148:             ISignalService(resolve("signal_service", false)).syncChainData( 
149:                 ownerChainId, LibSignals.STATE_ROOT, _l1BlockId, _l1StateRoot
150:             );
```
[148](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L148-L150)

```solidity
📁 File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

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
[285](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L285-L287), [322](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L322-L327)

```solidity
📁 File: contracts/team/airdrop/ERC20Airdrop.sol

71:         IVotes(token).delegateBySig(delegatee, nonce, expiry, v, r, s); 
```
[71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L71)

```solidity
📁 File: contracts/tokenvault/ERC1155Vault.sol

226:             IERC1155(token).safeBatchTransferFrom(address(this), to, tokenIds, amounts, ""); 

230:             BridgedERC1155(token).mintBatch(to, tokenIds, amounts); 

252:                     BridgedERC1155(_op.token).burn(_user, _op.tokenIds[i], _op.amounts[i]); 
```
[226](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L226), [230](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L230), [252](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L252)

</details>


---
### [NC&#x2011;19] Constants in comparisons should appear on the left side
Putting constants on the left side of comparison statements is a best practice known as [Yoda conditions](https://en.wikipedia.org/wiki/Yoda_conditions). Although solidity's static typing system prevents accidental assignments within conditionals, adopting this practice can improve code readability and consistency, especially when working across multiple languages.

<details>
<summary><i>There are 40 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

/// @audit move 0 to the left
/// @audit move 0 to the left
/// @audit move 0 to the left
/// @audit move 0 to the left
81:         if ( 
82:             block.timestamp > assignment.expiry
83:                 || assignment.metaHash != 0 && _blk.metaHash != assignment.metaHash
84:                 || assignment.parentMetaHash != 0 && _meta.parentMetaHash != assignment.parentMetaHash
85:                 || assignment.maxBlockId != 0 && _meta.id > assignment.maxBlockId
86:                 || assignment.maxProposedIn != 0 && block.number > assignment.maxProposedIn

/// @audit move 0 to the left
120:         if (input.tip != 0 && block.coinbase != address(0)) { 
```
[81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L81-L86), [120](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L120)

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

/// @audit move 0 to the left
108:         if (params.parentMetaHash != 0 && parentMetaHash != params.parentMetaHash) { 

/// @audit move 0 to the left
144:             if (params.blobHash != 0) { 

/// @audit move 0 to the left
159:                 if (meta_.blobHash == 0) revert L1_BLOB_NOT_FOUND(); 

/// @audit move 0 to the left
185:             if (params.txListByteOffset != 0) { 

/// @audit move 0 to the left
195:         if (meta_.txListByteSize == 0 || meta_.txListByteSize > _config.blockMaxTxListBytes) { 

/// @audit move 0 to the left
260:             if (address(this).balance != 0) { 

/// @audit move 1 to the left
307:         if (_slotB.numBlocks == 1) { 
```
[108](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L108), [144](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L144), [159](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L159), [185](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L185), [195](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L195), [260](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L260), [307](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L307)

```solidity
📁 File: contracts/L1/libs/LibProving.sol

/// @audit move 0 to the left
/// @audit move 0 to the left
/// @audit move 0 to the left
105:         if (_tran.parentHash == 0 || _tran.blockHash == 0 || _tran.stateRoot == 0) { 

/// @audit move 0 to the left
134:         if (_proof.tier == 0 || _proof.tier < _meta.minTier || _proof.tier < ts.tier) { 

/// @audit move 0 to the left
186:         bool isTopTier = tier.contestBond == 0; 

/// @audit move 32 to the left
192:             bool returnLivenessBond = blk.livenessBond > 0 && _proof.data.length == 32 

/// @audit move 0 to the left
280:         if (tid_ == 0) { 

/// @audit move 1 to the left
309:             if (tid_ == 1) { 

/// @audit move 0 to the left
412:         if (_tier.contestBond == 0) return; 

/// @audit move 1 to the left
/// @audit move 0 to the left
419:         if (_tid == 1 && _ts.tier == 0 && inProvingWindow) { 
```
[105](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L105), [134](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L134), [186](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L186), [192](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L192), [280](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L280), [309](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L309), [412](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L412), [419](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L419)

```solidity
📁 File: contracts/L1/libs/LibUtils.sol

/// @audit move 0 to the left
43:         if (tid == 0) revert L1_TRANSITION_NOT_FOUND(); 
```
[43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L43)

```solidity
📁 File: contracts/L1/libs/LibVerifying.sol

/// @audit move 0 to the left
93:         if (_maxBlocksToVerify == 0) { 

/// @audit move 0 to the left
111:         if (tid == 0) revert L1_TRANSITION_ID_ZERO(); 

/// @audit move 0 to the left
137:                 if (tid == 0) break; 

/// @audit move 0 to the left
/// @audit move 0 to the left
/// @audit move 0 to the left
/// @audit move 0 to the left
/// @audit move 0 to the left
/// @audit move 0 to the left
/// @audit move 0 to the left
/// @audit move 1 to the left
246:         if ( 
247:             _config.chainId <= 1 || _config.chainId == block.chainid //
248:                 || _config.blockMaxProposals == 1
249:                 || _config.blockRingBufferSize <= _config.blockMaxProposals + 1
250:                 || _config.blockMaxGasLimit == 0 || _config.blockMaxTxListBytes == 0
251:                 || _config.blockMaxTxListBytes > 128 * 1024 // calldata up to 128K
252:                 || _config.livenessBond == 0 || _config.ethDepositRingBufferSize <= 1
253:                 || _config.ethDepositMinCountPerBlock == 0
254:             // Audit recommendation, and gas tested. Processing 32 deposits (as initially set in
255:             // TaikoL1.sol) costs 72_502 gas.
256:             || _config.ethDepositMaxCountPerBlock > 32
257:                 || _config.ethDepositMaxCountPerBlock < _config.ethDepositMinCountPerBlock
258:                 || _config.ethDepositMinAmount == 0
259:                 || _config.ethDepositMaxAmount <= _config.ethDepositMinAmount
260:                 || _config.ethDepositMaxAmount > type(uint96).max || _config.ethDepositGas == 0
261:                 || _config.ethDepositMaxFee == 0
262:                 || _config.ethDepositMaxFee > type(uint96).max / _config.ethDepositMaxCountPerBlock
```
[93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L93), [111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L111), [137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L137), [246](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L246-L262)

```solidity
📁 File: contracts/common/EssentialContract.sol

/// @audit move 1 to the left
120:         if (block.chainid == 1) { 

/// @audit move 1 to the left
131:         if (block.chainid == 1) { 
```
[120](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L120), [131](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L131)

```solidity
📁 File: contracts/libs/Lib4844.sol

/// @audit move 64 to the left
49:         if (ret.length != 64) revert EVAL_FAILED_2(); 
```
[49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L49)

```solidity
📁 File: contracts/libs/LibTrieProof.sol

/// @audit move 0 to the left
46:         if (_accountProof.length != 0) { 

/// @audit move 0 to the left
50:             if (rlpAccount.length == 0) revert LTP_INVALID_ACCOUNT_PROOF(); 
```
[46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L46), [50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L50)

</details>


---
### [NC&#x2011;20] `constant`s should be defined rather than using magic numbers
Even [assembly](https://github.com/code-423n4/2022-05-opensea-seaport/blob/9d7ce4d08bf3c3010304a0476a785c70c0e90ae7/contracts/lib/TokenTransferrer.sol#L35-L39) can benefit from using readable constants instead of hex/numeric literals

<details>
<summary><i>There are 40 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoL1.sol

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
[192](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L192), [195](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L195-L196), [199](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L199), [203](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L203-L204), [207](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L207), [209](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L209-L211), [213](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L213-L214), [216](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L216)

```solidity
📁 File: contracts/L1/TaikoToken.sol

41:         _mint(_recipient, 1_000_000_000 ether); 
```
[41](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L41)

```solidity
📁 File: contracts/L1/gov/TaikoGovernor.sol

43:         __GovernorVotesQuorumFraction_init(4); 

112:         return 7200; // 1 day 

118:         return 50_400; // 1 week 

124:         return 1_000_000_000 ether / 10_000; // 0.01% of Taiko Token 
```
[43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L43), [112](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L112), [118](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L118), [124](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L124)

```solidity
📁 File: contracts/L1/libs/LibDepositing.sol

89:                     recipient: address(uint160(data >> 96)), 

151:         return (uint256(uint160(_addr)) << 96) | _amount; 
```
[89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L89), [151](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L151)

```solidity
📁 File: contracts/L1/libs/LibProving.sol

192:             bool returnLivenessBond = blk.livenessBond > 0 && _proof.data.length == 32 

415:             + _tier.provingWindow * 60 >= block.timestamp; 
```
[192](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L192), [415](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L415)

```solidity
📁 File: contracts/L1/libs/LibVerifying.sol

152:                         uint256(ITierProvider(tierProvider).getTier(ts.tier).cooldownWindow) * 60 

251:                 || _config.blockMaxTxListBytes > 128 * 1024 // calldata up to 128K 

256:             || _config.ethDepositMaxCountPerBlock > 32 
```
[152](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L152), [251](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L251), [256](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L256)

```solidity
📁 File: contracts/L1/tiers/DevnetTierProvider.sol

24:                 validityBond: 250 ether, // TKO 
25:                 contestBond: 500 ether, // TKO
26:                 cooldownWindow: 1440, //24 hours
27:                 provingWindow: 120, // 2 hours
28:                 maxBlocksToVerifyPerProof: 16

37:                 cooldownWindow: 60, //1 hours 
38:                 provingWindow: 2880, // 48 hours
39:                 maxBlocksToVerifyPerProof: 16
```
[24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L24-L28), [37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L37-L39)

```solidity
📁 File: contracts/L1/tiers/MainnetTierProvider.sol

24:                 validityBond: 250 ether, // TKO 
```
[24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L24)

```solidity
📁 File: contracts/libs/Lib4844.sol

34:         bytes1[48] memory _commitment, 
35:         bytes1[48] memory _pointProof

49:         if (ret.length != 64) revert EVAL_FAILED_2(); 
```
[34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L34-L35), [49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L49)

```solidity
📁 File: contracts/libs/LibAddress.sol

31:             64, // return max 64 bytes 
```
[31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L31)

</details>


---
### [NC&#x2011;21] `constant`s/`immutable`s redefined elsewhere
Consider defining each of these in only one contract so that values cannot become out of sync when only one location is updated (i.e. having `ContA.X`,`ContB.Y` is fine since they're different constant names in different files, but `ContA.X`, `ContB.X` is not since it's the same constant defined in multiple files with the same value). Even things like `decimals` and `VERSION` can employ file-level constants such as `PREFERRED_DECIMALS = 18` and `INITIAL_VERSION = "1.0.0"`

<details>
<summary><i>There are 40 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

21:     uint256 public constant MAX_BYTES_PER_BLOB = 4096 * 32; 
```
[21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L21)

```solidity
📁 File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

25:     ISigVerifyLib public immutable sigVerifyLib; 
26:     IPEMCertChainLib public immutable pemCertLib;

29:     uint256 internal constant CPUSVN_LENGTH = 16; 

33:     bytes32 internal constant ROOTCA_PUBKEY_HASH = 
34:         0x89f72d7c488e5b53a77c23ebcb36970ef7eb5bcf6658e9b8292cfbe4703a8473;

36:     uint8 internal constant INVALID_EXIT_CODE = 255; 
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L25-L26), [29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L29), [33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L33-L34), [36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L36)

```solidity
📁 File: contracts/automata-attestation/lib/PEMCertChainLib.sol

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
[17](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L17-L20), [22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L22-L29), [32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L32)

```solidity
📁 File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

14:     uint256 internal constant MINIMUM_QUOTE_LENGTH = 1020; 
15:     bytes2 internal constant SUPPORTED_QUOTE_VERSION = 0x0300;
16:     bytes2 internal constant SUPPORTED_ATTESTATION_KEY_TYPE = 0x0200;

18:     bytes4 internal constant SUPPORTED_TEE_TYPE = 0; 
19:     bytes16 internal constant VALID_QE_VENDOR_ID = 0x939a7233f79c4ca9940a0db3957f0607;
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L14-L16), [18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L18-L19)

```solidity
📁 File: contracts/automata-attestation/utils/BytesUtils.sol

310:     bytes constant BASE32_HEX_TABLE = 
311:         hex"00010203040506070809FFFFFFFFFFFFFF0A0B0C0D0E0F101112131415161718191A1B1C1D1E1FFFFFFFFFFFFFFFFFFFFF0A0B0C0D0E0F101112131415161718191A1B1C1D1E1F";
```
[310](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L310-L311)

```solidity
📁 File: contracts/common/EssentialContract.sol

11:     uint8 private constant _FALSE = 1; 

13:     uint8 private constant _TRUE = 2; 
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L11), [13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L13)

```solidity
📁 File: contracts/libs/LibTrieProof.sol

18:     uint256 private constant _ACCOUNT_FIELD_INDEX_STORAGE_HASH = 2; 
```
[18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L18)

```solidity
📁 File: contracts/thirdparty/optimism/rlp/RLPReader.sol

30:     uint256 internal constant MAX_LIST_LENGTH = 32; 
```
[30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L30)

```solidity
📁 File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

21:     uint256 internal constant TREE_RADIX = 16; 

24:     uint256 internal constant BRANCH_NODE_LENGTH = TREE_RADIX + 1; 

27:     uint256 internal constant LEAF_OR_EXTENSION_NODE_LENGTH = 2; 

30:     uint8 internal constant PREFIX_EXTENSION_EVEN = 0; 

33:     uint8 internal constant PREFIX_EXTENSION_ODD = 1; 

36:     uint8 internal constant PREFIX_LEAF_EVEN = 2; 

39:     uint8 internal constant PREFIX_LEAF_ODD = 3; 
```
[21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L21), [24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L24), [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L27), [30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L30), [33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L33), [36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L36), [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L39)

```solidity
📁 File: contracts/thirdparty/solmate/LibFixedPointMath.sol

7:     uint128 public constant MAX_EXP_INPUT = 135_305_999_368_893_231_588; 
8:     uint256 public constant SCALING_FACTOR = 1e18; // For fixed point representation factor
```
[7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L7-L8)

```solidity
📁 File: contracts/verifiers/SgxVerifier.sol

30:     uint64 public constant INSTANCE_EXPIRY = 180 days; 

34:     uint64 public constant INSTANCE_VALIDITY_DELAY = 1 days; 
```
[30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L30), [34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L34)

</details>


---
### [NC&#x2011;22] `constructor` should emit an event
Use events to signal significant changes to off-chain monitoring tools.

<details>
<summary><i>There are 3 instances of this issue:</i></summary>

```solidity
📁 File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

54:     constructor(address sigVerifyLibAddr, address pemCertLibAddr) { 
```
[54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L54)

```solidity
📁 File: contracts/automata-attestation/utils/SigVerifyLib.sol

20:     constructor(address es256Verifier) { 
```
[20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L20)

```solidity
📁 File: contracts/common/EssentialContract.sol

64:     constructor() { 
```
[64](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L64)

</details>


---
### [NC&#x2011;23] Contract implements interface without extending the interface
Not extending the interface may lead to the wrong function signature being used, leading to unexpected behavior. If the interface is in fact being implemented, use the `override` keyword to indicate that fact.

<details>
<summary><i>There are 2 instances of this issue:</i></summary>

```solidity
📁 File: contracts/tokenvault/BaseVault.sol

/// @audit IMessageInvocable.onMessageInvocation()
/// @audit IRecallableSender.onMessageRecalled()
12: abstract contract BaseVault is 
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L12)

```solidity
📁 File: contracts/tokenvault/BridgedERC1155.sol

/// @audit IERC1155MetadataURIUpgradeable.uri()
14: contract BridgedERC1155 is EssentialContract, IERC1155MetadataURIUpgradeable, ERC1155Upgradeable { 
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L14)

</details>


---
### [NC&#x2011;24] Contracts containing only utility functions should be made into libraries

<i>There is one instance of this issue:</i>

```solidity
📁 File: contracts/automata-attestation/lib/PEMCertChainLib.sol

12: contract PEMCertChainLib is IPEMCertChainLib { 
13:     using Asn1Decode for bytes;
14:     using NodePtr for uint256;
15:     using BytesUtils for bytes;
16: 
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L12-L16)


---
### [NC&#x2011;25] Contracts should have all `public`/`external` functions exposed by `interface`s
The `contract`s should expose an `interface` so that other projects can more easily integrate with it, without having to develop their own non-standard variants.

<details>
<summary><i>There are 36 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoL1.sol

/// @audit init, proposeBlock, proveBlock, verifyBlocks, pauseProving, depositEtherToL2, unpause, canDepositEthToL2, isBlobReusable, getBlock, getTransition, getStateVariables
22: contract TaikoL1 is EssentialContract, ITaikoL1, TaikoEvents, TaikoErrors { 
23:     /// @notice The TaikoL1 state.
24:     TaikoData.State public state;
```
[22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L22-L24)

```solidity
📁 File: contracts/L1/TaikoToken.sol

/// @audit init, burn, snapshot, transfer, transferFrom
15: contract TaikoToken is EssentialContract, ERC20SnapshotUpgradeable, ERC20VotesUpgradeable { 
16:     uint256[50] private __gap;
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L15-L16)

```solidity
📁 File: contracts/L1/gov/TaikoGovernor.sol

/// @audit init, propose, supportsInterface, state, votingDelay, votingPeriod, proposalThreshold
16: contract TaikoGovernor is 
17:     EssentialContract,
18:     GovernorCompatibilityBravoUpgradeable,
19:     GovernorVotesUpgradeable,
20:     GovernorVotesQuorumFractionUpgradeable,
21:     GovernorTimelockControlUpgradeable
22: {
23:     uint256[50] private __gap;
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L16-L23)

```solidity
📁 File: contracts/L1/gov/TaikoTimelockController.sol

/// @audit init, getMinDelay
9: contract TaikoTimelockController is EssentialContract, TimelockControllerUpgradeable { 
10:     uint256[50] private __gap;
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L9-L10)

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

/// @audit init, onBlockProposed, hashAssignment
14: contract AssignmentHook is EssentialContract, IHook { 
15:     using LibAddress for address;
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L14-L15)

```solidity
📁 File: contracts/L1/provers/GuardianProver.sol

/// @audit init, approve
10: contract GuardianProver is Guardians { 
11:     uint256[50] private __gap;
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L10-L11)

```solidity
📁 File: contracts/L1/provers/Guardians.sol

/// @audit setGuardians, isApproved, numGuardians
9: abstract contract Guardians is EssentialContract { 
10:     /// @notice The minimum number of guardians
11:     uint256 public constant MIN_NUM_GUARDIANS = 5;
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L9-L11)

```solidity
📁 File: contracts/L1/tiers/DevnetTierProvider.sol

/// @audit init, getTier, getTierIds, getMinTier
10: contract DevnetTierProvider is EssentialContract, ITierProvider { 
11:     uint256[50] private __gap;
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L10-L11)

```solidity
📁 File: contracts/L1/tiers/MainnetTierProvider.sol

/// @audit init, getTier, getTierIds, getMinTier
10: contract MainnetTierProvider is EssentialContract, ITierProvider { 
11:     uint256[50] private __gap;
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L10-L11)

```solidity
📁 File: contracts/L1/tiers/TestnetTierProvider.sol

/// @audit init, getTier, getTierIds, getMinTier
10: contract TestnetTierProvider is EssentialContract, ITierProvider { 
11:     uint256[50] private __gap;
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L10-L11)

```solidity
📁 File: contracts/L2/CrossChainOwned.sol

/// @audit onMessageInvocation
14: abstract contract CrossChainOwned is EssentialContract, IMessageInvocable { 
15:     /// @notice The owner chain ID.
16:     uint64 public ownerChainId;
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L14-L16)

```solidity
📁 File: contracts/L2/TaikoL2.sol

/// @audit init, anchor, withdraw, getBasefee, getBlockHash
21: contract TaikoL2 is CrossChainOwned { 
22:     using LibAddress for address;
```
[21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L21-L22)

```solidity
📁 File: contracts/L2/TaikoL2EIP1559Configurable.sol

/// @audit getConfig
9: contract TaikoL2EIP1559Configurable is TaikoL2 { 
10:     /// @notice EIP-1559 configuration.
11:     Config public customConfig;
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L9-L11)

```solidity
📁 File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

/// @audit setMrSigner, setMrEnclave, addRevokedCertSerialNum, removeRevokedCertSerialNum, configureTcbInfoJson, configureQeIdentityJson, toggleLocalReportCheck, verifyAttestation, verifyParsedQuote
22: contract AutomataDcapV3Attestation is IAttestation { 
23:     using BytesUtils for bytes;
```
[22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L22-L23)

```solidity
📁 File: contracts/automata-attestation/lib/PEMCertChainLib.sol

/// @audit splitCertificateChain, decodeCert
12: contract PEMCertChainLib is IPEMCertChainLib { 
13:     using Asn1Decode for bytes;
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L12-L13)

```solidity
📁 File: contracts/automata-attestation/utils/SigVerifyLib.sol

/// @audit verifyAttStmtSignature, verifyCertificateSignature, verifyRS256Signature, verifyRS1Signature, verifyES256Signature
15: contract SigVerifyLib is ISigVerifyLib { 
16:     using BytesUtils for bytes;
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L15-L16)

```solidity
📁 File: contracts/bridge/Bridge.sol

/// @audit init, suspendMessages, banAddress, sendMessage, recallMessage, processMessage, retryMessage, isMessageSent, proveMessageFailed, proveMessageReceived, isDestChainEnabled, context, hashMessage, signalForFailedMessage
16: contract Bridge is EssentialContract, IBridge { 
17:     using Address for address;
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L16-L17)

```solidity
📁 File: contracts/common/AddressManager.sol

/// @audit init, getAddress
10: contract AddressManager is EssentialContract, IAddressManager { 
11:     /// @dev Mapping of chainId to mapping of name to address.
12:     mapping(uint256 chainId => mapping(bytes32 name => address addr)) private __addresses;
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L10-L12)

```solidity
📁 File: contracts/common/EssentialContract.sol

/// @audit paused
10: abstract contract EssentialContract is UUPSUpgradeable, Ownable2StepUpgradeable, AddressResolver { 
11:     uint8 private constant _FALSE = 1;
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L10-L11)

```solidity
📁 File: contracts/signal/SignalService.sol

/// @audit init, authorize, sendSignal, syncChainData, isChainDataSynced, isSignalSent, getSyncedChainData, signalForChainData, getSignalSlot
14: contract SignalService is EssentialContract, ISignalService { 
15:     /// @notice Mapping to store the top blockId.
16:     /// @dev Slot 1.
17:     mapping(uint64 chainId => mapping(bytes32 kind => uint64 blockId)) public topBlockId;
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L14-L17)

```solidity
📁 File: contracts/team/TimelockTokenPool.sol

/// @audit init, grant, void, withdraw, withdraw, getMyGrantSummary, getMyGrant
25: contract TimelockTokenPool is EssentialContract { 
26:     using SafeERC20 for IERC20;
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L25-L26)

```solidity
📁 File: contracts/team/airdrop/ERC20Airdrop.sol

/// @audit init, claimAndDelegate
11: contract ERC20Airdrop is MerkleClaimable { 
12:     /// @notice The address of the token contract.
13:     address public token;
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L11-L13)

```solidity
📁 File: contracts/team/airdrop/ERC20Airdrop2.sol

/// @audit init, claim, withdraw, getBalance
12: contract ERC20Airdrop2 is MerkleClaimable { 
13:     using LibMath for uint256;
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L12-L13)

```solidity
📁 File: contracts/team/airdrop/ERC721Airdrop.sol

/// @audit init, claim
9: contract ERC721Airdrop is MerkleClaimable { 
10:     /// @notice The address of the token contract.
11:     address public token;
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L9-L11)

```solidity
📁 File: contracts/team/airdrop/MerkleClaimable.sol

/// @audit setConfig
10: abstract contract MerkleClaimable is EssentialContract { 
11:     /// @notice Mapping of hashes and their claim status
12:     mapping(bytes32 hash => bool claimed) public isClaimed;
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L10-L12)

```solidity
📁 File: contracts/tokenvault/BaseVault.sol

/// @audit init
12: abstract contract BaseVault is 
13:     EssentialContract,
14:     IRecallableSender,
15:     IMessageInvocable,
16:     IERC165Upgradeable
17: {
18:     uint256[50] private __gap;
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L12-L18)

```solidity
📁 File: contracts/tokenvault/BridgedERC1155.sol

/// @audit init, mint, mintBatch, burn, name, symbol
14: contract BridgedERC1155 is EssentialContract, IERC1155MetadataURIUpgradeable, ERC1155Upgradeable { 
15:     /// @notice Address of the source token contract.
16:     address public srcToken;
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L14-L16)

```solidity
📁 File: contracts/tokenvault/BridgedERC20.sol

/// @audit init, setSnapshoter, snapshot, name, symbol, decimals, canonical
15: contract BridgedERC20 is 
16:     BridgedERC20Base,
17:     IERC20MetadataUpgradeable,
18:     ERC20SnapshotUpgradeable,
19:     ERC20VotesUpgradeable
20: {
21:     /// @dev Slot 1.
22:     address public srcToken;
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L15-L22)

```solidity
📁 File: contracts/tokenvault/BridgedERC20Base.sol

/// @audit changeMigrationStatus, mint, burn, owner
9: abstract contract BridgedERC20Base is EssentialContract, IBridgedERC20 { 
10:     /// @notice The address of the contract to migrate tokens to or from.
11:     address public migratingAddress;
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L9-L11)

```solidity
📁 File: contracts/tokenvault/BridgedERC721.sol

/// @audit init, mint, burn, name, symbol, source
12: contract BridgedERC721 is EssentialContract, ERC721Upgradeable { 
13:     /// @notice Address of the source token contract.
14:     address public srcToken;
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L12-L14)

```solidity
📁 File: contracts/tokenvault/ERC1155Vault.sol

/// @audit sendToken, onMessageInvocation, onMessageRecalled, onERC1155BatchReceived, onERC1155Received, name
29: contract ERC1155Vault is BaseNFTVault, ERC1155ReceiverUpgradeable { 
30:     using LibAddress for address;
```
[29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L29-L30)

```solidity
📁 File: contracts/tokenvault/ERC20Vault.sol

/// @audit changeBridgedToken, sendToken, onMessageInvocation, onMessageRecalled, name
18: contract ERC20Vault is BaseVault { 
19:     using LibAddress for address;
```
[18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L18-L19)

```solidity
📁 File: contracts/tokenvault/ERC721Vault.sol

/// @audit sendToken, onMessageInvocation, onMessageRecalled, onERC721Received, name
16: contract ERC721Vault is BaseNFTVault, IERC721Receiver { 
17:     using LibAddress for address;
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L16-L17)

```solidity
📁 File: contracts/tokenvault/adapters/USDCAdapter.sol

/// @audit init
28: contract USDCAdapter is BridgedERC20Base { 
29:     /// @notice The USDC instance.
30:     /// @dev Slot 1.
31:     IUSDC public usdc;
```
[28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L28-L31)

```solidity
📁 File: contracts/verifiers/GuardianVerifier.sol

/// @audit init, verifyProof
10: contract GuardianVerifier is EssentialContract, IVerifier { 
11:     uint256[50] private __gap;
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L10-L11)

```solidity
📁 File: contracts/verifiers/SgxVerifier.sol

/// @audit init, addInstances, deleteInstances, registerInstance, verifyProof, getSignedHash
19: contract SgxVerifier is EssentialContract, IVerifier { 
20:     /// @dev Each public-private key pair (Ethereum address) is generated within
21:     /// the SGX program when it boots up. The off-chain remote attestation
22:     /// ensures the validity of the program hash and has the capability of
23:     /// bootstrapping the network with trustworthy instances.
24:     struct Instance {
```
[19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L19-L24)

</details>


---
### [NC&#x2011;26] Contracts should have full test coverage
A 100% test coverage is not foolproof, but it helps immensely in reducing the amount of bugs that may occur.


---
### [NC&#x2011;27] Contracts/libraries/interfaces should each be defined in separate files
This helps to make tracking changes across commits easier, among other reasons. They can be combined into a single file later by importing multiple contracts, and using that file as the common import.

<details>
<summary><i>There are 11 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/tiers/ITierProvider.sol

/// @audit ITierProvider, LibTiers
7: interface ITierProvider { 

/// @audit ITierProvider, LibTiers
37: library LibTiers { 
```
[7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L7), [37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L37)

```solidity
📁 File: contracts/automata-attestation/utils/Asn1Decode.sol

/// @audit NodePtr, Asn1Decode
12: library NodePtr { 

/// @audit NodePtr, Asn1Decode
38: library Asn1Decode { 
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L12), [38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L38)

```solidity
📁 File: contracts/bridge/IBridge.sol

/// @audit IBridge, IRecallableSender, IMessageInvocable
8: interface IBridge { 

/// @audit IBridge, IRecallableSender, IMessageInvocable
160: interface IRecallableSender { 

/// @audit IBridge, IRecallableSender, IMessageInvocable
174: interface IMessageInvocable { 
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L8), [160](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L160), [174](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L174)

```solidity
📁 File: contracts/tokenvault/ERC1155Vault.sol

/// @audit IERC1155NameAndSymbol, ERC1155Vault
16: interface IERC1155NameAndSymbol { 

/// @audit IERC1155NameAndSymbol, ERC1155Vault
29: contract ERC1155Vault is BaseNFTVault, ERC1155ReceiverUpgradeable { 
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L16), [29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L29)

```solidity
📁 File: contracts/tokenvault/adapters/USDCAdapter.sol

/// @audit IUSDC, USDCAdapter
8: interface IUSDC { 

/// @audit IUSDC, USDCAdapter
28: contract USDCAdapter is BridgedERC20Base { 
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L8), [28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L28)

</details>


---
### [NC&#x2011;28] Control structures do not follow the Solidity Style Guide
See the [control structures](https://docs.soliditylang.org/en/latest/style-guide.html#control-structures) section of the Solidity Style Guide

<details>
<summary><i>There are 40 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/gov/TaikoGovernor.sol

/// @audit opening brace should be on the same line as the declaration
/// @audit opening brace should be preceded by a single space
31:     function init( 
32:         address _owner,
33:         IVotesUpgradeable _token,
34:         TimelockControllerUpgradeable _timelock
35:     )
36:         external
37:         initializer
38:     {

/// @audit opening brace should be on the same line as the declaration
/// @audit opening brace should be preceded by a single space
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

/// @audit opening brace should be on the same line as the declaration
/// @audit opening brace should be preceded by a single space
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

/// @audit opening brace should be on the same line as the declaration
/// @audit opening brace should be preceded by a single space
89:     function supportsInterface(bytes4 _interfaceId) 
90:         public
91:         view
92:         override(GovernorUpgradeable, GovernorTimelockControlUpgradeable, IERC165Upgradeable)
93:         returns (bool)
94:     {

/// @audit opening brace should be on the same line as the declaration
/// @audit opening brace should be preceded by a single space
99:     function state(uint256 _proposalId) 
100:         public
101:         view
102:         override(IGovernorUpgradeable, GovernorUpgradeable, GovernorTimelockControlUpgradeable)
103:         returns (ProposalState)
104:     {

/// @audit opening brace should be on the same line as the declaration
/// @audit opening brace should be preceded by a single space
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

/// @audit opening brace should be on the same line as the declaration
/// @audit opening brace should be preceded by a single space
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

/// @audit opening brace should be on the same line as the declaration
/// @audit opening brace should be preceded by a single space
153:     function _executor() 
154:         internal
155:         view
156:         override(GovernorUpgradeable, GovernorTimelockControlUpgradeable)
157:         returns (address)
158:     {
```
[31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L31-L38), [48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L48-L57), [69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L69-L80), [89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L89-L94), [99](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L99-L104), [127](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L127-L136), [140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L140-L149), [153](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L153-L158)

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

/// @audit opening brace should be on the same line as the declaration
/// @audit opening brace should be preceded by a single space
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

/// @audit opening brace should be on the same line as the declaration
/// @audit opening brace should be preceded by a single space
137:     function hashAssignment( 
138:         ProverAssignment memory _assignment,
139:         address _taikoL1Address,
140:         bytes32 _blobHash
141:     )
142:         public
143:         view
144:         returns (bytes32)
145:     {

/// @audit opening brace should be on the same line as the declaration
/// @audit opening brace should be preceded by a single space
164:     function _getProverFee( 
165:         TaikoData.TierFee[] memory _tierFees,
166:         uint16 _tierId
167:     )
168:         private
169:         pure
170:         returns (uint256)
171:     {
```
[62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L62-L71), [137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L137-L145), [164](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L164-L171)

```solidity
📁 File: contracts/common/AddressManager.sol

/// @audit opening brace should be on the same line as the declaration
/// @audit opening brace should be preceded by a single space
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
[38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L38-L46)

```solidity
📁 File: contracts/common/AddressResolver.sol

/// @audit opening brace should be on the same line as the declaration
/// @audit opening brace should be preceded by a single space
30:     function resolve( 
31:         bytes32 _name,
32:         bool _allowZeroAddress
33:     )
34:         public
35:         view
36:         virtual
37:         returns (address payable)
38:     {

/// @audit opening brace should be on the same line as the declaration
/// @audit opening brace should be preceded by a single space
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

/// @audit opening brace should be on the same line as the declaration
/// @audit opening brace should be preceded by a single space
72:     function _resolve( 
73:         uint64 _chainId,
74:         bytes32 _name,
75:         bool _allowZeroAddress
76:     )
77:         private
78:         view
79:         returns (address payable addr_)
80:     {
```
[30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L30-L38), [43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L43-L52), [72](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L72-L80)

```solidity
📁 File: contracts/common/EssentialContract.sol

/// @audit opening brace should be on the same line as the declaration
/// @audit opening brace should be preceded by a single space
95:     function __Essential_init( 
96:         address _owner,
97:         address _addressManager
98:     )
99:         internal
100:         virtual
101:         onlyInitializing
102:     {
```
[95](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L95-L102)

```solidity
📁 File: contracts/libs/Lib4844.sol

/// @audit opening brace should be on the same line as the declaration
/// @audit opening brace should be preceded by a single space
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
[30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L30-L39)

```solidity
📁 File: contracts/libs/LibAddress.sol

/// @audit opening brace should be on the same line as the declaration
/// @audit opening brace should be preceded by a single space
46:     function supportsInterface( 
47:         address _addr,
48:         bytes4 _interfaceId
49:     )
50:         internal
51:         view
52:         returns (bool result_)
53:     {

/// @audit opening brace should be on the same line as the declaration
/// @audit opening brace should be preceded by a single space
61:     function isValidSignature( 
62:         address _addr,
63:         bytes32 _hash,
64:         bytes memory _sig
65:     )
66:         internal
67:         view
68:         returns (bool)
69:     {
```
[46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L46-L53), [61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L61-L69)

```solidity
📁 File: contracts/libs/LibTrieProof.sol

/// @audit opening brace should be on the same line as the declaration
/// @audit opening brace should be preceded by a single space
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
45:     {
```
[34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L34-L45)

</details>


---
### [NC&#x2011;29] Custom `error` without details
Consider adding some parameters to the error to indicate which user or values caused the failure.

<details>
<summary><i>There are 40 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/gov/TaikoGovernor.sol

25:     error TG_INVALID_SIGNATURES_LENGTH(); 
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L25)

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

50:     error HOOK_ASSIGNMENT_EXPIRED(); 
51:     error HOOK_ASSIGNMENT_INVALID_SIG();
52:     error HOOK_TIER_NOT_FOUND();
```
[50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L50-L52)

```solidity
📁 File: contracts/L1/libs/LibDepositing.sol

22:     error L1_INVALID_ETH_DEPOSIT(); 
```
[22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L22)

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

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
[44](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L44-L57)

```solidity
📁 File: contracts/L1/libs/LibProving.sol

59:     error L1_ALREADY_CONTESTED(); 
60:     error L1_ALREADY_PROVED();
61:     error L1_ASSIGNED_PROVER_NOT_ALLOWED();
62:     error L1_BLOCK_MISMATCH();
63:     error L1_INVALID_BLOCK_ID();
64:     error L1_INVALID_PAUSE_STATUS();
```
[59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L59-L64)

```solidity
📁 File: contracts/common/AddressManager.sol

25:     error AM_INVALID_PARAMS(); 
26:     error AM_UNSUPPORTED();
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L25-L26)

```solidity
📁 File: contracts/common/AddressResolver.sol

16:     error RESOLVER_DENIED(); 
17:     error RESOLVER_INVALID_MANAGER();
18:     error RESOLVER_UNEXPECTED_CHAINID();
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L16-L18)

```solidity
📁 File: contracts/common/EssentialContract.sol

35:     error REENTRANT_CALL(); 
36:     error INVALID_PAUSE_STATUS();
37:     error ZERO_ADDR_MANAGER();
```
[35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L35-L37)

```solidity
📁 File: contracts/libs/Lib4844.sol

19:     error EVAL_FAILED_1(); 
20:     error EVAL_FAILED_2();
21:     error POINT_X_TOO_LARGE();
22:     error POINT_Y_TOO_LARGE();
```
[19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L19-L22)

```solidity
📁 File: contracts/libs/LibAddress.sol

16:     error ETH_TRANSFER_FAILED(); 
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L16)

```solidity
📁 File: contracts/libs/LibTrieProof.sol

20:     error LTP_INVALID_ACCOUNT_PROOF(); 
21:     error LTP_INVALID_INCLUSION_PROOF();
```
[20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L20-L21)

</details>


---
### [NC&#x2011;30] Custom errors should be used rather than `revert()`/`require()`
Custom errors are available from solidity version 0.8.4. Custom errors are more easily processed in try-catch blocks, and are easier to re-use and maintain.

<details>
<summary><i>There are 40 instances of this issue:</i></summary>

```solidity
📁 File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

61:         require(msg.sender == owner, "onlyOwner"); 
```
[61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L61)

```solidity
📁 File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

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
```
[77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L77-L99)

```solidity
📁 File: contracts/thirdparty/optimism/Bytes.sol

25:             require(_length + 31 >= _length, "slice_overflow"); 
26:             require(_start + _length >= _start, "slice_overflow");
27:             require(_bytes.length >= _start + _length, "slice_outOfBounds");
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L25-L27)

```solidity
📁 File: contracts/thirdparty/optimism/rlp/RLPReader.sol

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
[37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L37-L40), [56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L56-L59), [61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L61-L64), [112](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L112-L115), [117](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L117-L120), [152](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L152-L155), [172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L172-L175), [182](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L182-L185), [192](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L192-L195), [202](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L202-L205), [212](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L212-L215), [217](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L217-L220), [228](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L228-L231), [238](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L238-L241), [248](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L248-L251), [258](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L258-L261), [263](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L263-L266)

```solidity
📁 File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

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
[77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L77), [89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L89), [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L93-L96), [99](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L99-L102), [105](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L105-L108), [119](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L119-L122), [125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L125-L128), [150](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L150-L153), [162](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L162-L165), [172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L172-L175), [178](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L178-L181), [191](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L191), [194](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L194), [198](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L198)

</details>


---
### [NC&#x2011;31] Do not use underscore at the end of variable name
The style guide says to add a trailing underscore to a variable name in order to prevent the shadowing of [another variable](https://docs.soliditylang.org/en/latest/style-guide.html#avoiding-naming-collisions) or function name, the examples below do not shadow variables.

<details>
<summary><i>There are 40 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoL1.sol

/// @audit meta_
/// @audit deposits_
63:         returns (TaikoData.BlockMetadata memory meta_, TaikoData.EthDeposit[] memory deposits_) 

/// @audit blk_
/// @audit ts_
148:         returns (TaikoData.Block memory blk_, TaikoData.TransitionState memory ts_) 

/// @audit a_
/// @audit b_
179:         returns (TaikoData.SlotA memory a_, TaikoData.SlotB memory b_) 
```
[63](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L63), [148](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L148), [179](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L179)

```solidity
📁 File: contracts/L1/libs/LibDepositing.sol

/// @audit recipient_
44:         address recipient_ = _recipient == address(0) ? msg.sender : _recipient; 

/// @audit deposits_
73:         returns (TaikoData.EthDeposit[] memory deposits_) 
```
[44](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L44), [73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L73)

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

/// @audit meta_
/// @audit deposits_
76:         returns (TaikoData.BlockMetadata memory meta_, TaikoData.EthDeposit[] memory deposits_) 
```
[76](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L76)

```solidity
📁 File: contracts/L1/libs/LibProving.sol

/// @audit maxBlocksToVerify_
100:         returns (uint8 maxBlocksToVerify_) 

/// @audit tid_
276:         returns (uint32 tid_, TaikoData.TransitionState storage ts_) 
```
[100](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L100), [276](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L276)

```solidity
📁 File: contracts/L1/libs/LibUtils.sol

/// @audit slot_
59:         returns (TaikoData.Block storage blk_, uint64 slot_) 

/// @audit tid_
78:         returns (uint32 tid_) 
```
[59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L59), [78](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L78)

```solidity
📁 File: contracts/L1/provers/GuardianProver.sol

/// @audit approved_
43:         returns (bool approved_) 
```
[43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L43)

```solidity
📁 File: contracts/L1/provers/Guardians.sol

/// @audit approved_
111:     function approve(uint256 _operationId, bytes32 _hash) internal returns (bool approved_) { 
```
[111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L111)

```solidity
📁 File: contracts/L1/tiers/DevnetTierProvider.sol

/// @audit tiers_
47:     function getTierIds() public pure override returns (uint16[] memory tiers_) { 
```
[47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L47)

```solidity
📁 File: contracts/L1/tiers/MainnetTierProvider.sol

/// @audit tiers_
58:     function getTierIds() public pure override returns (uint16[] memory tiers_) { 
```
[58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L58)

```solidity
📁 File: contracts/L1/tiers/TestnetTierProvider.sol

/// @audit tiers_
58:     function getTierIds() public pure override returns (uint16[] memory tiers_) { 
```
[58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L58)

```solidity
📁 File: contracts/L2/TaikoL2.sol

/// @audit basefee_
191:         returns (uint256 basefee_) 

/// @audit config_
208:     function getConfig() public view virtual returns (Config memory config_) { 

/// @audit basefee_
259:         returns (uint256 basefee_, uint64 gasExcess_) 
```
[191](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L191), [208](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L208), [259](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L259)

```solidity
📁 File: contracts/bridge/Bridge.sol

/// @audit msgHash_
/// @audit message_
121:         returns (bytes32 msgHash_, Message memory message_) 

/// @audit enabled_
/// @audit destBridge_
395:         returns (bool enabled_, address destBridge_) 

/// @audit ctx_
403:     function context() public view returns (Context memory ctx_) { 

/// @audit invocationDelay_
/// @audit invocationExtraDelay_
421:         returns (uint256 invocationDelay_, uint256 invocationExtraDelay_) 

/// @audit success_
483:         returns (bool success_) 

/// @audit success_
585:         returns (bool success_) 
```
[121](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L121), [395](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L395), [403](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L403), [421](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L421), [483](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L483), [585](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L585)

```solidity
📁 File: contracts/common/AddressResolver.sol

/// @audit addr_
79:         returns (address payable addr_) 
```
[79](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L79)

```solidity
📁 File: contracts/common/EssentialContract.sol

/// @audit reentry_
130:     function _loadReentryLock() internal view virtual returns (uint8 reentry_) { 
```
[130](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L130)

```solidity
📁 File: contracts/libs/LibAddress.sol

/// @audit result_
52:         returns (bool result_) 
```
[52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L52)

```solidity
📁 File: contracts/libs/LibTrieProof.sol

/// @audit storageRoot_
44:         returns (bytes32 storageRoot_) 
```
[44](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L44)

```solidity
📁 File: contracts/signal/SignalService.sol

/// @audit blockId_
/// @audit chainData_
165:         returns (uint64 blockId_, bytes32 chainData_) 

/// @audit signal_
242:         returns (bytes32 signal_) 

/// @audit slot_
262:         returns (bytes32 slot_) 

/// @audit value_
306:         returns (bytes32 value_) 
```
[165](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L165), [242](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L242), [262](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L262), [306](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L306)

</details>


---
### [NC&#x2011;32] Do not use UNDERSCORE in `struct` elements names

<i>There are 2 instaces of this issue:</i>

```solidity
📁 File: contracts/L1/TaikoData.sol

/// @audit __reserved1, __reserved2, __reserved3
168:     struct SlotB { 
169:         uint64 numBlocks;
170:         uint64 lastVerifiedBlockId;
171:         bool provingPaused;
172:         uint8 __reserved1;
173:         uint16 __reserved2;
174:         uint32 __reserved3;
175:         uint64 lastUnpausedAt;
176:     }

/// @audit __gap
179:     struct State { 
180:         // Ring buffer for proposed blocks and a some recent verified blocks.
181:         mapping(uint64 blockId_mod_blockRingBufferSize => Block blk) blocks;
182:         // Indexing to transition ids (ring buffer not possible)
183:         mapping(uint64 blockId => mapping(bytes32 parentHash => uint32 transitionId)) transitionIds;
184:         // Ring buffer for transitions
185:         mapping(
186:             uint64 blockId_mod_blockRingBufferSize
187:                 => mapping(uint32 transitionId => TransitionState ts)
188:             ) transitions;
189:         // Ring buffer for Ether deposits
190:         mapping(uint256 depositId_mod_ethDepositRingBufferSize => uint256 depositAmount) ethDeposits;
191:         // Reusable blobs
192:         mapping(bytes32 blobHash => uint256 since) reusableBlobs;
193:         SlotA slotA; // slot 6
194:         SlotB slotB; // slot 7
195:         uint256[43] __gap;
196:     }
```
[168](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L168-L176), [179](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L179-L196)


---
### [NC&#x2011;33] `else`-block not required
One level of nesting can be removed by not having an `else` block when the `if`-block returns, and `if (foo) { return 1; } else { return 2; }` becomes `if (foo) { return 1; } return 2;`

<details>
<summary><i>There are 12 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/tiers/MainnetTierProvider.sol

68:         if (_rand % 1000 == 0) return LibTiers.TIER_SGX_ZKVM; 
69:         else return LibTiers.TIER_SGX;
```
[68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L68-L69)

```solidity
📁 File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

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
330:             return false;
331:         }
```
[319](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L319-L331)

```solidity
📁 File: contracts/automata-attestation/utils/Asn1Decode.sol

158:         if (der[ptr.ixf()] == 0) { 
159:             return der.substring(ptr.ixf() + 1, valueLength - 1);
160:         } else {
161:             return der.substring(ptr.ixf(), valueLength);
162:         }
```
[158](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L158-L162)

```solidity
📁 File: contracts/automata-attestation/utils/RsaVerify.sol

151:         if (digestAlgoWithParamLen == sha256ExplicitNullParam.length) { 
152:             for (uint256 i; i < digestAlgoWithParamLen; ++i) {
153:                 if (decipher[3 + paddingLen + i] != bytes1(sha256ExplicitNullParam[i])) {
154:                     return false;
155:                 }
156:             }
157:         } else {
158:             for (uint256 i; i < digestAlgoWithParamLen; ++i) {
159:                 if (decipher[3 + paddingLen + i] != bytes1(sha256ImplicitNullParam[i])) {
160:                     return false;
161:                 }
162:             }
163:         }
```
[151](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L151-L163)

```solidity
📁 File: contracts/automata-attestation/utils/SigVerifyLib.sol

44:         } else if (alg == Algorithm.RS1) { 
45:             if (publicKey.keyType != KeyType.RSA) {
46:                 return false;
47:             }
48:             return verifyRS1Signature(tbs, signature, publicKey.pubKey);
49:         } else {
50:             revert("Unsupported algorithm");
51:         }

69:         } else if (alg == CertSigAlgorithm.Sha1WithRSAEncryption) { 
70:             if (publicKey.keyType != KeyType.RSA) {
71:                 return false;
72:             }
73:             return verifyRS1Signature(tbs, signature, publicKey.pubKey);
74:         } else {
75:             revert("Unsupported algorithm");
76:         }
```
[44](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L44-L51), [69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L69-L76)

```solidity
📁 File: contracts/bridge/Bridge.sol

439:         } else if (block.chainid >= 32_300 && block.chainid <= 32_400) { 
440:             // For all Taiko internal devnets
441:             return (5 minutes, 384 seconds);
442:         } else {
443:             // This is a Taiko L2 chain where no deleys are applied.
444:             return (0, 0);
445:         }

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
567:             return __ctx;
568:         }
```
[439](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L439-L445), [556](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L556-L568)

```solidity
📁 File: contracts/libs/LibAddress.sol

70:         if (Address.isContract(_addr)) { 
71:             return IERC1271(_addr).isValidSignature(_hash, _sig) == _EIP1271_MAGICVALUE;
72:         } else {
73:             return ECDSA.recover(_hash, _sig) == _addr;
74:         }
```
[70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L70-L74)

```solidity
📁 File: contracts/thirdparty/optimism/rlp/RLPReader.sol

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
235:             // Long list.
236:             uint256 lenOfListLen = prefix - 0xf7;
237: 
238:             require(
239:                 _in.length > lenOfListLen,
240:                 "RLPReader: length of content must be > than length of list length (long list)"
241:             );
242: 
243:             bytes1 firstByteOfContent;
244:             assembly {
245:                 firstByteOfContent := and(mload(add(ptr, 1)), shl(248, 0xff))
246:             }
247: 
248:             require(
249:                 firstByteOfContent != 0x00,
250:                 "RLPReader: length of content must not have any leading zeros (long list)"
251:             );
252: 
253:             uint256 listLen;
254:             assembly {
255:                 listLen := shr(sub(256, mul(8, lenOfListLen)), mload(add(ptr, 1)))
256:             }
257: 
258:             require(
259:                 listLen > 55,
260:                 "RLPReader: length of content must be greater than 55 bytes (long list)"
261:             );
262: 
263:             require(
264:                 _in.length > lenOfListLen + listLen,
265:                 "RLPReader: length of content must be greater than total length (long list)"
266:             );
267: 
268:             return (1 + lenOfListLen, listLen, RLPItemType.LIST_ITEM);
269:         }
```
[223](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L223-L269)

```solidity
📁 File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

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
132:                     // We're not at the end of the key yet.
133:                     // Figure out what the next node ID should be and continue.
134:                     uint8 branchKey = uint8(key[currentKeyIndex]);
135:                     RLPReader.RLPItem memory nextNode = currentNode.decoded[branchKey];
136:                     currentNodeID = _getNodeID(nextNode);
137:                     currentKeyIndex += 1;
138:                 }
139:             } else if (currentNode.decoded.length == LEAF_OR_EXTENSION_NODE_LENGTH) {
140:                 bytes memory path = _getNodePath(currentNode);
141:                 uint8 prefix = uint8(path[0]);
142:                 uint8 offset = 2 - (prefix % 2);
143:                 bytes memory pathRemainder = Bytes.slice(path, offset);
144:                 bytes memory keyRemainder = Bytes.slice(key, currentKeyIndex);
145:                 uint256 sharedNibbleLength = _getSharedNibbleLength(pathRemainder, keyRemainder);
146: 
147:                 // Whether this is a leaf node or an extension node, the path remainder MUST be a
148:                 // prefix of the key remainder (or be equal to the key remainder) or the proof is
149:                 // considered invalid.
150:                 require(
151:                     pathRemainder.length == sharedNibbleLength,
152:                     "MerkleTrie: path remainder must share all nibbles with key"
153:                 );
154: 
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
185:                     // Prefix of 0 or 1 means this is an extension node. We move onto the next node
186:                     // in the proof and increment the key index by the length of the path remainder
187:                     // which is equal to the shared nibble length.
188:                     currentNodeID = _getNodeID(currentNode.decoded[1]);
189:                     currentKeyIndex += sharedNibbleLength;
190:                 } else {
191:                     revert("MerkleTrie: received a node with an unknown prefix");
192:                 }
193:             } else {
194:                 revert("MerkleTrie: received an unparseable node");
195:             }
```
[112](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L112-L195)

</details>


---
### [NC&#x2011;34] Empty bytes check is missing
Passing empty bytes to a function can cause unexpected behavior, such as certain operations failing, producing incorrect results, or wasting gas. It is recommended to check that all byte parameters are not empty.

<details>
<summary><i>There are 40 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoL1.sol

/// @audit _genesisBlockHash
42:     function init( 
43:         address _owner,
44:         address _addressManager,
45:         bytes32 _genesisBlockHash
46:     )
47:         external
48:         initializer
49:     {

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
[42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L42-L49), [55](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L55-L64), [75](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L75-L83)

```solidity
📁 File: contracts/L1/gov/TaikoGovernor.sol

/// @audit _descriptionHash
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

/// @audit _descriptionHash
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
```
[127](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L127-L136), [140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L140-L149)

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

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
[62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L62-L71)

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

/// @audit _data
/// @audit _txList
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
```
[68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L68-L77)

```solidity
📁 File: contracts/L1/libs/LibVerifying.sol

/// @audit _genesisBlockHash
47:     function init( 
48:         TaikoData.State storage _state,
49:         TaikoData.Config memory _config,
50:         bytes32 _genesisBlockHash
51:     )
52:         external
53:     {

/// @audit _stateRoot
224:     function _syncChainData( 
225:         TaikoData.Config memory _config,
226:         IAddressResolver _resolver,
227:         uint64 _lastVerifiedBlockId,
228:         bytes32 _stateRoot
229:     )
230:         private
231:     {
```
[47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L47-L53), [224](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L224-L231)

```solidity
📁 File: contracts/L1/provers/Guardians.sol

/// @audit _hash
111:     function approve(uint256 _operationId, bytes32 _hash) internal returns (bool approved_) { 

/// @audit _hash
124:     function deleteApproval(bytes32 _hash) internal { 
```
[111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L111), [124](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L124)

```solidity
📁 File: contracts/L2/CrossChainOwned.sol

/// @audit _data
36:     function onMessageInvocation(bytes calldata _data) 
37:         external
38:         payable
39:         whenNotPaused
40:         onlyFromNamed("bridge")
41:     {
```
[36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L36-L41)

```solidity
📁 File: contracts/L2/TaikoL2.sol

/// @audit _l1BlockHash
/// @audit _l1StateRoot
107:     function anchor( 
108:         bytes32 _l1BlockHash,
109:         bytes32 _l1StateRoot,
110:         uint64 _l1BlockId,
111:         uint32 _parentGasUsed
112:     )
113:         external
114:         nonReentrant
115:     {
```
[107](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L107-L115)

```solidity
📁 File: contracts/bridge/Bridge.sol

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

/// @audit _msgHash
477:     function _invokeMessageCall( 
478:         Message calldata _message,
479:         bytes32 _msgHash,
480:         uint256 _gasLimit
481:     )
482:         private
483:         returns (bool success_)
484:     {

/// @audit _msgHash
515:     function _updateMessageStatus(bytes32 _msgHash, Status _status) private { 

/// @audit _msgHash
541:     function _storeContext(bytes32 _msgHash, address _from, uint64 _srcChainId) private { 
```
[155](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L155-L163), [217](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L217-L225), [477](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L477-L484), [515](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L515), [541](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L541)

```solidity
📁 File: contracts/common/AddressManager.sol

/// @audit _name
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
[38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L38-L46)

```solidity
📁 File: contracts/signal/SignalService.sol

/// @audit _signal
63:     function sendSignal(bytes32 _signal) external returns (bytes32) { 

/// @audit _kind
/// @audit _chainData
68:     function syncChainData( 
69:         uint64 _chainId,
70:         bytes32 _kind,
71:         uint64 _blockId,
72:         bytes32 _chainData
73:     )
74:         external
75:         returns (bytes32)
76:     {

/// @audit _signal
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

/// @audit _signal
/// @audit _value
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
220:     {

/// @audit _kind
/// @audit _chainData
235:     function _syncChainData( 
236:         uint64 _chainId,
237:         bytes32 _kind,
238:         uint64 _blockId,
239:         bytes32 _chainData
240:     )
241:         private
242:         returns (bytes32 signal_)
243:     {

/// @audit _signal
/// @audit _value
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
263:     {

/// @audit _signalRoot
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
[63](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L63), [68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L68-L76), [83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L83-L93), [206](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L206-L220), [235](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L235-L243), [253](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L253-L263), [271](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L271-L280)

```solidity
📁 File: contracts/tokenvault/BridgedERC1155.sol

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
[125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L125-L136)

```solidity
📁 File: contracts/tokenvault/ERC1155Vault.sol

/// @audit data
93:     function onMessageInvocation(bytes calldata data) external payable nonReentrant whenNotPaused { 

/// @audit msgHash
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
```
[93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L93), [127](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L127-L136)

```solidity
📁 File: contracts/tokenvault/ERC20Vault.sol

/// @audit _data
253:     function onMessageInvocation(bytes calldata _data) 
254:         external
255:         payable
256:         nonReentrant
257:         whenNotPaused
258:     {

/// @audit _msgHash
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
```
[253](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L253-L258), [285](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L285-L294)

```solidity
📁 File: contracts/tokenvault/ERC721Vault.sol

/// @audit _data
77:     function onMessageInvocation(bytes calldata _data) 
78:         external
79:         payable
80:         nonReentrant
81:         whenNotPaused
82:     {
```
[77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L77-L82)

</details>


---
### [NC&#x2011;35] Empty function body
Empty function body in solidity is not recommended, consider adding some comments to the body.


<i>There is one instance of this issue:</i>

```solidity
📁 File: contracts/bridge/Bridge.sol

70:     receive() external payable { } 
```
[70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L70)


---
### [NC&#x2011;36] `enum` names should be descriptive rather than cryptic

<i>There is one instance of this issue:</i>

```solidity
📁 File: contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol

31:     enum CRL { 
32:         PCK,
33:         ROOT
34:     }
```
[31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L31-L34)


---
### [NC&#x2011;37] Enum values should be used instead of constant array indexes
Create a commented enum value to use instead of constant array indexes, this makes the code far easier to understand.

<details>
<summary><i>There are 37 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/libs/LibUtils.sol

/// @audit 1
80:         if (_state.transitions[_slot][1].key == _parentHash) { 
```
[80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L80)

```solidity
📁 File: contracts/L1/libs/LibVerifying.sol

/// @audit 0
62:         TaikoData.Block storage blk = _state.blocks[0]; 

/// @audit 1
/// @audit 0
68:         TaikoData.TransitionState storage ts = _state.transitions[0][1]; 
```
[62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L62), [68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L68)

```solidity
📁 File: contracts/L1/tiers/DevnetTierProvider.sol

/// @audit 0
49:         tiers_[0] = LibTiers.TIER_OPTIMISTIC; 
/// @audit 1
50:         tiers_[1] = LibTiers.TIER_GUARDIAN;
```
[49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L49-L50)

```solidity
📁 File: contracts/L1/tiers/MainnetTierProvider.sol

/// @audit 0
60:         tiers_[0] = LibTiers.TIER_SGX; 
/// @audit 1
61:         tiers_[1] = LibTiers.TIER_SGX_ZKVM;
/// @audit 2
62:         tiers_[2] = LibTiers.TIER_GUARDIAN;
```
[60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L60-L62)

```solidity
📁 File: contracts/L1/tiers/TestnetTierProvider.sol

/// @audit 0
60:         tiers_[0] = LibTiers.TIER_OPTIMISTIC; 
/// @audit 1
61:         tiers_[1] = LibTiers.TIER_SGX;
/// @audit 2
62:         tiers_[2] = LibTiers.TIER_GUARDIAN;
```
[60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L60-L62)

```solidity
📁 File: contracts/L2/TaikoL2.sol

/// @audit 255
240:         inputs[255] = bytes32(block.chainid); 
```
[240](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L240)

```solidity
📁 File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

/// @audit 0
435:             string memory parsedFmspc = parsedQuoteCerts[0].pck.sgxExtension.fmspc; 

/// @audit 0
442:             IPEMCertChainLib.ECSha256Certificate memory pckCert = parsedQuoteCerts[0]; 

/// @audit 0
454:             (tcbVerified, tcbStatus) = _checkTcbLevels(parsedQuoteCerts[0].pck, fetchedTcbInfo); 

/// @audit 0
472:                 parsedQuoteCerts[0].pubKey, 
```
[435](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L435), [442](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L442), [454](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L454), [472](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L472)

```solidity
📁 File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

/// @audit 0
/// @audit 1
/// @audit 2
285:         certChainData = [quoteCerts[0], quoteCerts[1], quoteCerts[2]]; 
```
[285](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L285)

```solidity
📁 File: contracts/automata-attestation/utils/RsaVerify.sol

/// @audit 0
/// @audit 1
137:         if (decipher[0] != 0 || decipher[1] != 0x01) { 

/// @audit 0
/// @audit 1
270:         if (decipher[0] != 0 || decipher[1] != 0x01) { 
```
[137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L137), [270](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L270)

```solidity
📁 File: contracts/automata-attestation/utils/X509DateUtils.sol

/// @audit 0
18:             if (uint8(x509Time[0]) - 48 < 5) yrs += 2000; 

/// @audit 0
/// @audit 1
21:             yrs += (uint8(x509Time[0]) - 48) * 1000 + (uint8(x509Time[1]) - 48) * 100; 

/// @audit 1
57:         if (isLeapYear(year)) monthDays[1] = 29; 
```
[18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L18), [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L21), [57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L57)

```solidity
📁 File: contracts/thirdparty/optimism/rlp/RLPWriter.sol

/// @audit 0
14:         if (_in.length == 1 && uint8(_in[0]) < 128) { 

/// @audit 0
35:             out_[0] = bytes1(uint8(_len) + uint8(_offset)); 

/// @audit 0
45:             out_[0] = bytes1(uint8(lenLen) + uint8(_offset) + 55); 
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L14), [35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L35), [45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L45)

```solidity
📁 File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

/// @audit 0
141:                 uint8 prefix = uint8(path[0]); 

/// @audit 1
171:                     value_ = RLPReader.readBytes(currentNode.decoded[1]); 

/// @audit 1
188:                     currentNodeID = _getNodeID(currentNode.decoded[1]); 

/// @audit 0
228:         nibbles_ = Bytes.toNibbles(RLPReader.readBytes(_node.decoded[0])); 
```
[141](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L141), [171](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L171), [188](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L188), [228](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L228)

```solidity
📁 File: contracts/verifiers/SgxVerifier.sol

/// @audit 0
133:         _address[0] = address(bytes20(_attestation.localEnclaveReport.reportData)); 

/// @audit 0
135:         return _addInstances(_address, false)[0]; 
```
[133](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L133), [135](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L135)

</details>


---
### [NC&#x2011;38] Error messages should be descriptive rather than cryptic

<i>There are 2 instaces of this issue:</i>

```solidity
📁 File: contracts/thirdparty/optimism/Bytes.sol

25:             require(_length + 31 >= _length, "slice_overflow"); 
26:             require(_start + _length >= _start, "slice_overflow");
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L25-L26)


---
### [NC&#x2011;39] Event is missing `indexed` fields
Index event fields make the field more quickly accessible to off-chain tools that parse events. However, note that each index field costs extra gas during emission, so it's not necessarily best to index the maximum allowed per event (three fields). Each event should use three indexed fields if there are three or more fields, and gas usage is not particularly of concern for the events in question. If there are fewer than three fields, all of the fields should be indexed.

<details>
<summary><i>There are 39 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoEvents.sol

21:     event BlockProposed( 
22:         uint256 indexed blockId,
23:         address indexed assignedProver,
24:         uint96 livenessBond,
25:         TaikoData.BlockMetadata meta,
26:         TaikoData.EthDeposit[] depositsProcessed
27:     );

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

86:     event EthDeposited(TaikoData.EthDeposit deposit); 
```
[21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L21-L27), [53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L53-L59), [67](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L67-L73), [77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L77), [81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L81), [86](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L86)

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

46:     event BlockAssigned( 
47:         address indexed assignedProver, TaikoData.BlockMetadata meta, ProverAssignment assignment
48:     );
```
[46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L46-L48)

```solidity
📁 File: contracts/L1/libs/LibDepositing.sol

19:     event EthDeposited(TaikoData.EthDeposit deposit); 
```
[19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L19)

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

31:     event BlockProposed( 
32:         uint256 indexed blockId,
33:         address indexed assignedProver,
34:         uint96 livenessBond,
35:         TaikoData.BlockMetadata meta,
36:         TaikoData.EthDeposit[] depositsProcessed
37:     );

41:     event BlobCached(bytes32 blobHash); 
```
[31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L31-L37), [41](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L41)

```solidity
📁 File: contracts/L1/libs/LibProving.sol

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
[32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L32-L38), [46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L46-L52), [56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L56)

```solidity
📁 File: contracts/L1/provers/GuardianProver.sol

18:     event GuardianApproval( 
19:         address indexed addr, uint256 indexed blockId, bytes32 blockHash, bool approved
20:     );
```
[18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L18-L20)

```solidity
📁 File: contracts/L1/provers/Guardians.sol

37:     event GuardiansUpdated(uint32 version, address[] guardians); 

43:     event Approved(uint256 indexed operationId, uint256 approvalBits, bool proofSubmitted); 
```
[37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L37), [43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L43)

```solidity
📁 File: contracts/L2/TaikoL2.sol

57:     event Anchored(bytes32 parentHash, uint64 gasExcess); 
```
[57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L57)

```solidity
📁 File: contracts/L2/TaikoL2EIP1559Configurable.sol

18:     event ConfigAndExcessChanged(Config config, uint64 gasExcess); 
```
[18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L18)

```solidity
📁 File: contracts/bridge/IBridge.sol

69:     event MessageSent(bytes32 indexed msgHash, Message message); 

75:     event MessageReceived(bytes32 indexed msgHash, Message message, bool isRecall); 

92:     event MessageStatusChanged(bytes32 indexed msgHash, Status status); 

97:     event MessageSuspended(bytes32 msgHash, bool suspended); 

102:     event AddressBanned(address indexed addr, bool banned); 
```
[69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L69), [75](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L75), [92](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L92), [97](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L97), [102](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L102)

```solidity
📁 File: contracts/common/AddressManager.sol

21:     event AddressSet( 
22:         uint64 indexed chainId, bytes32 indexed name, address newAddress, address oldAddress
23:     );
```
[21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L21-L23)

```solidity
📁 File: contracts/common/EssentialContract.sol

29:     event Paused(address account); 

33:     event Unpaused(address account); 
```
[29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L29), [33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L33)

```solidity
📁 File: contracts/signal/ISignalService.sol

49:     event SignalSent(address app, bytes32 signal, bytes32 slot, bytes32 value); 

54:     event Authorized(address indexed addr, bool authrized); 
```
[49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L49), [54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L54)

```solidity
📁 File: contracts/team/TimelockTokenPool.sol

87:     event Granted(address indexed recipient, Grant grant); 

92:     event Voided(address indexed recipient, uint128 amount); 

99:     event Withdrawn(address indexed recipient, address to, uint128 amount, uint128 cost); 
```
[87](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L87), [92](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L92), [99](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L99)

```solidity
📁 File: contracts/team/airdrop/ERC20Airdrop2.sol

35:     event Withdrawn(address user, uint256 amount); 
```
[35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L35)

```solidity
📁 File: contracts/team/airdrop/MerkleClaimable.sol

27:     event Claimed(bytes32 hash); 
```
[27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L27)

```solidity
📁 File: contracts/tokenvault/BaseNFTVault.sol

104:     event TokenReleased( 
105:         bytes32 indexed msgHash,
106:         address indexed from,
107:         address ctoken,
108:         address token,
109:         uint256[] tokenIds,
110:         uint256[] amounts
111:     );
```
[104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L104-L111)

```solidity
📁 File: contracts/tokenvault/BridgedERC20Base.sol

21:     event MigrationStatusChanged(address addr, bool inbound); 

27:     event MigratedTo(address indexed fromToken, address indexed account, uint256 amount); 
```
[21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L21), [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L27)

```solidity
📁 File: contracts/tokenvault/ERC20Vault.sol

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
[80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L80-L88), [114](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L114-L116)

```solidity
📁 File: contracts/verifiers/SgxVerifier.sol

65:     event InstanceAdded( 
66:         uint256 indexed id, address indexed instance, address replaced, uint256 validSince
67:     );
```
[65](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L65-L67)

</details>


---
### [NC&#x2011;40] Events are missing sender information
When an action is triggered based on a user's action, not being able to filter based on who triggered the action makes event processing a lot more cumbersome. Including the msg.sender the events of these types of action will make events much more useful to end users, especially when `msg.sender` is not `tx.origin`.

<details>
<summary><i>There are 24 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/libs/LibProving.sol

80:         emit ProvingPaused(_pause); 
```
[80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L80)

```solidity
📁 File: contracts/L1/provers/Guardians.sol

95:         emit GuardiansUpdated(version, _newGuardians); 
```
[95](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L95)

```solidity
📁 File: contracts/L2/CrossChainOwned.sol

53:         emit TransactionExecuted(nextTxId++, bytes4(txdata)); 
```
[53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L53)

```solidity
📁 File: contracts/L2/TaikoL2EIP1559Configurable.sol

39:         emit ConfigAndExcessChanged(_newConfig, _newGasExcess); 
```
[39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L39)

```solidity
📁 File: contracts/bridge/Bridge.sol

111:         emit AddressBanned(_addr, _ban); 

151:         emit MessageSent(msgHash_, message_); 

210:             emit MessageReceived(msgHash, _message, true); 

301:             emit MessageExecuted(msgHash); 

303:             emit MessageReceived(msgHash, _message, false); 

519:         emit MessageStatusChanged(_msgHash, _status); 
```
[111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L111), [151](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L151), [210](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L210), [301](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L301), [303](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L303), [519](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L519)

```solidity
📁 File: contracts/common/AddressManager.sol

50:         emit AddressSet(_chainId, _name, _newAddress, oldAddress); 
```
[50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L50)

```solidity
📁 File: contracts/signal/SignalService.sol

268:         emit SignalSent(_app, _signal, slot_, _value); 
```
[268](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L268)

```solidity
📁 File: contracts/team/TimelockTokenPool.sol

222:         emit Withdrawn(_recipient, _to, amountToWithdraw, costToWithdraw); 
```
[222](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L222)

```solidity
📁 File: contracts/team/airdrop/ERC20Airdrop2.sol

93:         emit Withdrawn(user, amount); 
```
[93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L93)

```solidity
📁 File: contracts/tokenvault/BridgedERC20Base.sol

51:         emit MigrationStatusChanged(_migratingAddress, _migratingInbound); 
```
[51](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L51)

```solidity
📁 File: contracts/tokenvault/ERC1155Vault.sol

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
```
[80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L80-L89), [114](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L114-L123)

```solidity
📁 File: contracts/tokenvault/ERC20Vault.sol

191:         emit BridgedTokenChanged({ 
192:             srcChainId: _ctoken.chainId,
193:             ctoken: _ctoken.addr,
194:             btokenOld: btokenOld_,
195:             btokenNew: _btokenNew,
196:             ctokenSymbol: _ctoken.symbol,
197:             ctokenName: _ctoken.name,
198:             ctokenDecimal: _ctoken.decimals
199:         });

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
```
[191](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L191-L199), [241](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L241-L249), [273](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L273-L281)

```solidity
📁 File: contracts/tokenvault/ERC721Vault.sol

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
```
[64](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L64-L73), [97](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L97-L106)

```solidity
📁 File: contracts/verifiers/SgxVerifier.sol

220:             emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince); 

230:         emit InstanceAdded(id, newInstance, oldInstance, block.timestamp); 
```
[220](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220), [230](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L230)

</details>


---
### [NC&#x2011;41] Events should be emitted before external calls
Ensure that events follow the best practice of check-effects-interaction, and are emitted before external calls.

<details>
<summary><i>There are 33 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

/// @audit sendEther() on line 126
129:         emit BlockAssigned(_blk.assignedProver, _meta, assignment); 
```
[129](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L129)

```solidity
📁 File: contracts/L1/libs/LibDepositing.sol

/// @audit sendEther() on line 41
50:         emit EthDeposited( 
51:             TaikoData.EthDeposit({
52:                 recipient: recipient_,
53:                 amount: uint96(msg.value),
54:                 id: _state.slotA.numEthDeposits
55:             })
56:         );
```
[50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L50-L56)

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

/// @audit encode() on line 126
166:                     emit BlobCached(meta_.blobHash); 

/// @audit sendEther() on line 261
273:         emit BlockProposed({ 
274:             blockId: blk.blockId,
275:             assignedProver: blk.assignedProver,
276:             livenessBond: _config.livenessBond,
277:             meta: meta_,
278:             depositsProcessed: deposits_
279:         });
```
[166](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L166), [273](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L273-L279)

```solidity
📁 File: contracts/L1/libs/LibProving.sol

/// @audit transfer() on line 196
209:             emit TransitionProved({ 
210:                 blockId: blk.blockId,
211:                 tran: _tran,
212:                 prover: msg.sender,
213:                 validityBond: tier.validityBond,
214:                 tier: _proof.tier
215:             });

/// @audit transfer() on line 196
230:                 emit TransitionProved({ 
231:                     blockId: blk.blockId,
232:                     tran: _tran,
233:                     prover: msg.sender,
234:                     validityBond: 0,
235:                     tier: _proof.tier
236:                 });

/// @audit transferFrom() on line 242
254:                 emit TransitionContested({ 
255:                     blockId: blk.blockId,
256:                     tran: _tran,
257:                     contester: msg.sender,
258:                     contestBond: tier.contestBond,
259:                     tier: _proof.tier
260:                 });
```
[209](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L209-L215), [230](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L230-L236), [254](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L254-L260)

```solidity
📁 File: contracts/L1/libs/LibVerifying.sol

/// @audit transfer() on line 189
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
[198](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L198-L206)

```solidity
📁 File: contracts/L1/provers/GuardianProver.sol

/// @audit proveBlock() on line 51
54:         emit GuardianApproval(msg.sender, _meta.id, _tran.blockHash, approved_); 
```
[54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L54)

```solidity
📁 File: contracts/L1/provers/Guardians.sol

/// @audit push() on line 87
95:         emit GuardiansUpdated(version, _newGuardians); 
```
[95](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L95)

```solidity
📁 File: contracts/L2/CrossChainOwned.sol

/// @audit call() on line 50
53:         emit TransactionExecuted(nextTxId++, bytes4(txdata)); 
```
[53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L53)

```solidity
📁 File: contracts/L2/TaikoL2.sol

/// @audit syncChainData() on line 148
157:         emit Anchored(blockhash(parentId), gasExcess); 
```
[157](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L157)

```solidity
📁 File: contracts/bridge/Bridge.sol

/// @audit sendSignal() on line 150
151:         emit MessageSent(msgHash_, message_); 

/// @audit sendEther() on line 206
208:             emit MessageRecalled(msgHash); 

/// @audit sendEther() on line 206
210:             emit MessageReceived(msgHash, _message, true); 

/// @audit sendEther() on line 299
301:             emit MessageExecuted(msgHash); 

/// @audit sendEther() on line 299
303:             emit MessageReceived(msgHash, _message, false); 
```
[151](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L151), [208](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L208), [210](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L210), [301](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L301), [303](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L303)

```solidity
📁 File: contracts/team/TimelockTokenPool.sol

/// @audit safeTransferFrom() on line 220
222:         emit Withdrawn(_recipient, _to, amountToWithdraw, costToWithdraw); 
```
[222](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L222)

```solidity
📁 File: contracts/team/airdrop/ERC20Airdrop2.sol

/// @audit transferFrom() on line 91
93:         emit Withdrawn(user, amount); 
```
[93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L93)

```solidity
📁 File: contracts/team/airdrop/MerkleClaimable.sol

/// @audit encode() on line 68
74:         emit Claimed(hash); 
```
[74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L74)

```solidity
📁 File: contracts/tokenvault/ERC1155Vault.sol

/// @audit sendMessage() on line 77
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

/// @audit sendEther() on line 112
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

/// @audit sendEther() on line 146
149:         emit TokenReleased({ 
150:             msgHash: msgHash,
151:             from: message.srcOwner,
152:             ctoken: ctoken.addr,
153:             token: token,
154:             tokenIds: tokenIds,
155:             amounts: amounts
156:         });

/// @audit init() on line 305
314:         emit BridgedTokenDeployed({ 
315:             chainId: _ctoken.chainId,
316:             ctoken: _ctoken.addr,
317:             btoken: btoken_,
318:             ctokenSymbol: _ctoken.symbol,
319:             ctokenName: _ctoken.name
320:         });
```
[80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L80-L89), [114](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L114-L123), [149](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L149-L156), [314](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L314-L320)

```solidity
📁 File: contracts/tokenvault/ERC20Vault.sol

/// @audit changeMigrationStatus() on line 185
191:         emit BridgedTokenChanged({ 
192:             srcChainId: _ctoken.chainId,
193:             ctoken: _ctoken.addr,
194:             btokenOld: btokenOld_,
195:             btokenNew: _btokenNew,
196:             ctokenSymbol: _ctoken.symbol,
197:             ctokenName: _ctoken.name,
198:             ctokenDecimal: _ctoken.decimals
199:         });

/// @audit sendMessage() on line 239
241:         emit TokenSent({ 
242:             msgHash: msgHash,
243:             from: message_.srcOwner,
244:             to: _op.to,
245:             destChainId: _op.destChainId,
246:             ctoken: ctoken.addr,
247:             token: _op.token,
248:             amount: balanceChange
249:         });

/// @audit sendEther() on line 271
273:         emit TokenReceived({ 
274:             msgHash: ctx.msgHash,
275:             from: from,
276:             to: to,
277:             srcChainId: ctx.srcChainId,
278:             ctoken: ctoken.addr,
279:             token: token,
280:             amount: amount
281:         });

/// @audit sendEther() on line 304
306:         emit TokenReleased({ 
307:             msgHash: _msgHash,
308:             from: _message.srcOwner,
309:             ctoken: ctoken.addr,
310:             token: token,
311:             amount: amount
312:         });

/// @audit init() on line 409
425:         emit BridgedTokenDeployed({ 
426:             srcChainId: ctoken.chainId,
427:             ctoken: ctoken.addr,
428:             btoken: btoken,
429:             ctokenSymbol: ctoken.symbol,
430:             ctokenName: ctoken.name,
431:             ctokenDecimal: ctoken.decimals
432:         });
```
[191](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L191-L199), [241](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L241-L249), [273](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L273-L281), [306](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L306-L312), [425](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L425-L432)

```solidity
📁 File: contracts/tokenvault/ERC721Vault.sol

/// @audit sendMessage() on line 62
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

/// @audit sendEther() on line 95
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

/// @audit sendEther() on line 129
131:         emit TokenReleased({ 
132:             msgHash: _msgHash,
133:             from: _message.srcOwner,
134:             ctoken: ctoken.addr,
135:             token: token,
136:             tokenIds: tokenIds,
137:             amounts: new uint256[](tokenIds.length)
138:         });

/// @audit init() on line 242
250:         emit BridgedTokenDeployed({ 
251:             chainId: _ctoken.chainId,
252:             ctoken: _ctoken.addr,
253:             btoken: btoken_,
254:             ctokenSymbol: _ctoken.symbol,
255:             ctokenName: _ctoken.name
256:         });
```
[64](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L64-L73), [97](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L97-L106), [131](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L131-L138), [250](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L250-L256)

</details>


---
### [NC&#x2011;42] Events should use parameters to convey information
For example, rather than using `event Paused()` and `event Unpaused()`, use `event PauseState(address indexed whoChangedIt, bool wasPaused, bool isNowPaused)`


<i>There are 2 instaces of this issue:</i>

```solidity
📁 File: contracts/common/EssentialContract.sol

29:     event Paused(address account); 

33:     event Unpaused(address account); 
```
[29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L29), [33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L33)


---
### [NC&#x2011;43] Expressions for `constant` values should use `immutable` rather than constant
While it does not save gas for some simple binary expressions because the compiler knows that developers often make this mistake, it's still best to use the right tool for the task at hand. There is a difference between `constant` variables and `immutable` variables, and they should each be used in their appropriate contexts. `constants` should be used for literal values written into the code, and `immutable` variables should be used for expressions, or values calculated in, or passed into the constructor.

<details>
<summary><i>There are 8 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

21:     uint256 public constant MAX_BYTES_PER_BLOB = 4096 * 32; 
```
[21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L21)

```solidity
📁 File: contracts/L1/libs/LibProving.sol

20:     bytes32 public constant RETURN_LIVENESS_BOND = keccak256("RETURN_LIVENESS_BOND"); 

23:     bytes32 public constant TIER_OP = bytes32("tier_optimistic"); 
```
[20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L20), [23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L23)

```solidity
📁 File: contracts/bridge/Bridge.sol

27:     uint256 internal constant PLACEHOLDER = type(uint256).max; 
```
[27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L27)

```solidity
📁 File: contracts/libs/Lib4844.sol

10:     address public constant POINT_EVALUATION_PRECOMPILE_ADDRESS = address(0x0A); 
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L10)

```solidity
📁 File: contracts/signal/LibSignals.sol

8:     bytes32 public constant STATE_ROOT = keccak256("STATE_ROOT"); 

11:     bytes32 public constant SIGNAL_ROOT = keccak256("SIGNAL_ROOT"); 
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/LibSignals.sol#L8), [11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/LibSignals.sol#L11)

```solidity
📁 File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

24:     uint256 internal constant BRANCH_NODE_LENGTH = TREE_RADIX + 1; 
```
[24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L24)

</details>


---
### [NC&#x2011;44] Extraneous whitespace
See the [whitespace](https://docs.soliditylang.org/en/v0.8.16/style-guide.html#whitespace-in-expressions) section of the Solidity Style Guide

<details>
<summary><i>There are 6 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

253:                 IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }( 
```
[253](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L253)

```solidity
📁 File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

372:         ( 
373:             bool successful,
374:             ,
375:             ,
376:             bytes memory signedQuoteData,
377:             V3Struct.ECDSAQuoteV3AuthData memory authDataV3
378:         ) = V3Parser.validateParsedInput(v3quote);
```
[372](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L372-L378)

```solidity
📁 File: contracts/bridge/Bridge.sol

199:                 IRecallableSender(_message.from).onMessageRecalled{ value: _message.value }( 
```
[199](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L199)

```solidity
📁 File: contracts/tokenvault/ERC1155Vault.sol

77:             IBridge(resolve("bridge", false)).sendMessage{ value: msg.value }(message); 
```
[77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L77)

```solidity
📁 File: contracts/tokenvault/ERC20Vault.sol

239:             IBridge(resolve("bridge", false)).sendMessage{ value: msg.value }(message); 
```
[239](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L239)

```solidity
📁 File: contracts/tokenvault/ERC721Vault.sol

62:             IBridge(resolve("bridge", false)).sendMessage{ value: msg.value }(message); 
```
[62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L62)

</details>


---
### [NC&#x2011;45] For loops in `public` or `external` functions should be avoided due to high gas costs and possible DOS
In Solidity, for loops can potentially cause Denial of Service (DoS) attacks if not handled carefully. DoS attacks can occur when an attacker intentionally exploits the gas cost of a function, causing it to run out of gas or making it too expensive for other users to call. Below are some scenarios where for loops can lead to DoS attacks: Nested for loops can become exceptionally gas expensive and should be used sparingly.

<details>
<summary><i>There are 11 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/provers/Guardians.sol

/// @audit line 74
/// @audit line 80
53:     function setGuardians( 
54:         address[] memory _newGuardians,
55:         uint8 _minGuardians
56:     )
57:         external
58:         onlyOwner
59:         nonReentrant
60:     {
61:         // We need at least MIN_NUM_GUARDIANS and at most 255 guardians (so the approval bits fit in
62:         // a uint256)
63:         if (_newGuardians.length < MIN_NUM_GUARDIANS || _newGuardians.length > type(uint8).max) {
64:             revert INVALID_GUARDIAN_SET();
65:         }
66:         // Minimum number of guardians to approve is at least equal or greater than half the
67:         // guardians (rounded up) and less or equal than the total number of guardians
68:         if (_minGuardians < (_newGuardians.length + 1) >> 1 || _minGuardians > _newGuardians.length)
69:         {
70:             revert INVALID_MIN_GUARDIANS();
71:         }
72: 
73:         // Delete the current guardians
74:         for (uint256 i; i < guardians.length; ++i) {
75:             delete guardianIds[guardians[i]];
76:         }
77:         delete guardians;
78: 
79:         // Set the new guardians
80:         for (uint256 i = 0; i < _newGuardians.length; ++i) {
81:             address guardian = _newGuardians[i];
82:             if (guardian == address(0)) revert INVALID_GUARDIAN();
83:             // This makes sure there are not duplicate addresses
84:             if (guardianIds[guardian] != 0) revert INVALID_GUARDIAN_SET();
85: 
86:             // Save and index the guardian
87:             guardians.push(guardian);
88:             guardianIds[guardian] = guardians.length;
89:         }
90: 
91:         // Bump the version so previous approvals get invalidated
92:         ++version;
93: 
94:         minGuardians = _minGuardians;
95:         emit GuardiansUpdated(version, _newGuardians);
96:     }
```
[53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L53-L96)

```solidity
📁 File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

/// @audit line 80
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

/// @audit line 95
88:     function removeRevokedCertSerialNum( 
89:         uint256 index,
90:         bytes[] calldata serialNumBatch
91:     )
92:         external
93:         onlyOwner
94:     {
95:         for (uint256 i; i < serialNumBatch.length; ++i) {
96:             if (!_serialNumIsRevoked[index][serialNumBatch[i]]) {
97:                 continue;
98:             }
99:             delete _serialNumIsRevoked[index][serialNumBatch[i]];
100:         }
101:     }
```
[73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L73-L86), [88](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L88-L101)

```solidity
📁 File: contracts/automata-attestation/lib/PEMCertChainLib.sol

/// @audit line 54
40:     function splitCertificateChain( 
41:         bytes memory pemChain,
42:         uint256 size
43:     )
44:         external
45:         pure
46:         returns (bool success, bytes[] memory certs)
47:     {
48:         certs = new bytes[](size);
49:         string memory pemChainStr = string(pemChain);
50: 
51:         uint256 index = 0;
52:         uint256 len = pemChain.length;
53: 
54:         for (uint256 i; i < size; ++i) {
55:             string memory input;
56:             if (i > 0) {
57:                 input = LibString.slice(pemChainStr, index, index + len);
58:             } else {
59:                 input = pemChainStr;
60:             }
61:             uint256 increment;
62:             (success, certs[i], increment) = _removeHeadersAndFooters(input);
63: 
64:             if (!success) {
65:                 return (false, certs);
66:             }
67: 
68:             index += increment;
69:         }
70: 
71:         success = true;
72:     }
```
[40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L40-L72)

```solidity
📁 File: contracts/bridge/Bridge.sol

/// @audit line 90
82:     function suspendMessages( 
83:         bytes32[] calldata _msgHashes,
84:         bool _suspend
85:     )
86:         external
87:         onlyFromOwnerOrNamed("bridge_watchdog")
88:     {
89:         uint64 _timestamp = _suspend ? type(uint64).max : uint64(block.timestamp);
90:         for (uint256 i; i < _msgHashes.length; ++i) {
91:             bytes32 msgHash = _msgHashes[i];
92:             proofReceipt[msgHash].receivedAt = _timestamp;
93:             emit MessageSuspended(msgHash, _suspend);
94:         }
95:     }
```
[82](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L82-L95)

```solidity
📁 File: contracts/signal/SignalService.sol

/// @audit line 104
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
108:             bool isLastHop = i == hopProofs.length - 1;
109: 
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
[83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L83-L134)

```solidity
📁 File: contracts/team/airdrop/ERC721Airdrop.sol

/// @audit line 59
47:     function claim( 
48:         address user,
49:         uint256[] calldata tokenIds,
50:         bytes32[] calldata proof
51:     )
52:         external
53:         nonReentrant
54:     {
55:         // Check if this can be claimed
56:         _verifyClaim(abi.encode(user, tokenIds), proof);
57: 
58:         // Transfer the tokens
59:         for (uint256 i; i < tokenIds.length; ++i) {
60:             IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);
61:         }
62:     }
```
[47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L47-L62)

```solidity
📁 File: contracts/tokenvault/ERC1155Vault.sol

/// @audit line 47
39:     function sendToken(BridgeTransferOp memory _op) 
40:         external
41:         payable
42:         nonReentrant
43:         whenNotPaused
44:         withValidOperation(_op)
45:         returns (IBridge.Message memory message_)
46:     {
47:         for (uint256 i; i < _op.amounts.length; ++i) {
48:             if (_op.amounts[i] == 0) revert VAULT_INVALID_AMOUNT();
49:         }
50:         // Check token interface support
51:         if (!_op.token.supportsInterface(ERC1155_INTERFACE_ID)) {
52:             revert VAULT_INTERFACE_NOT_SUPPORTED();
53:         }
54: 
55:         (bytes memory data, CanonicalNFT memory ctoken) = _handleMessage(msg.sender, _op);
56: 
57:         // Create a message to send to the destination chain
58:         IBridge.Message memory message = IBridge.Message({
59:             id: 0, // will receive a new value
60:             from: address(0), // will receive a new value
61:             srcChainId: 0, // will receive a new value
62:             destChainId: _op.destChainId,
63:             srcOwner: msg.sender,
64:             destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,
65:             to: resolve(_op.destChainId, name(), false),
66:             refundTo: _op.refundTo,
67:             value: msg.value - _op.fee,
68:             fee: _op.fee,
69:             gasLimit: _op.gasLimit,
70:             data: data,
71:             memo: _op.memo
72:         });
73: 
74:         // Send the message and obtain the message hash
75:         bytes32 msgHash;
76:         (msgHash, message_) =
77:             IBridge(resolve("bridge", false)).sendMessage{ value: msg.value }(message);
78: 
79:         // Emit TokenSent event
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
90:     }
```
[39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L39-L90)

```solidity
📁 File: contracts/tokenvault/ERC721Vault.sol

/// @audit line 34
26:     function sendToken(BridgeTransferOp memory _op) 
27:         external
28:         payable
29:         nonReentrant
30:         whenNotPaused
31:         withValidOperation(_op)
32:         returns (IBridge.Message memory message_)
33:     {
34:         for (uint256 i; i < _op.tokenIds.length; ++i) {
35:             if (_op.amounts[i] != 0) revert VAULT_INVALID_AMOUNT();
36:         }
37: 
38:         if (!_op.token.supportsInterface(ERC721_INTERFACE_ID)) {
39:             revert VAULT_INTERFACE_NOT_SUPPORTED();
40:         }
41: 
42:         (bytes memory data, CanonicalNFT memory ctoken) = _handleMessage(msg.sender, _op);
43: 
44:         IBridge.Message memory message = IBridge.Message({
45:             id: 0, // will receive a new value
46:             from: address(0), // will receive a new value
47:             srcChainId: 0, // will receive a new value
48:             destChainId: _op.destChainId,
49:             srcOwner: msg.sender,
50:             destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,
51:             to: resolve(_op.destChainId, name(), false),
52:             refundTo: _op.refundTo,
53:             value: msg.value - _op.fee,
54:             fee: _op.fee,
55:             gasLimit: _op.gasLimit,
56:             data: data,
57:             memo: _op.memo
58:         });
59: 
60:         bytes32 msgHash;
61:         (msgHash, message_) =
62:             IBridge(resolve("bridge", false)).sendMessage{ value: msg.value }(message);
63: 
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
74:     }
```
[26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L26-L74)

```solidity
📁 File: contracts/verifiers/SgxVerifier.sol

/// @audit line 104
100:     function deleteInstances(uint256[] calldata _ids) 
101:         external
102:         onlyFromOwnerOrNamed("rollup_watchdog")
103:     {
104:         for (uint256 i; i < _ids.length; ++i) {
105:             uint256 idx = _ids[i];
106: 
107:             if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();
108: 
109:             emit InstanceDeleted(idx, instances[idx].addr);
110: 
111:             delete instances[idx];
112:         }
113:     }
```
[100](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L100-L113)

</details>


---
### [NC&#x2011;46] Function called does not exist in the contract interface
<details>
<summary><i>There are 5 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

114:             IERC20(assignment.feeToken).safeTransferFrom( 
```
[114](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L114)

```solidity
📁 File: contracts/L2/TaikoL2.sol

176:             IERC20(_token).safeTransfer(_to, IERC20(_token).balanceOf(address(this))); 
```
[176](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L176)

```solidity
📁 File: contracts/team/TimelockTokenPool.sol

220:         IERC20(costToken).safeTransferFrom(_recipient, sharedVault, costToWithdraw); 
```
[220](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L220)

```solidity
📁 File: contracts/tokenvault/ERC20Vault.sol

330:             IERC20(token_).safeTransfer(_to, _amount); 

379:             t.safeTransferFrom({ from: msg.sender, to: address(this), value: _amount }); 
```
[330](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L330), [379](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L379)

</details>


---
### [NC&#x2011;47] Function ordering in the contract does not follow the Solidity style guide
Source: [https://docs.soliditylang.org/en/v0.8.17/style-guide.html#order-of-layout](https://docs.soliditylang.org/en/v0.8.17/style-guide.html#order-of-layout)

<details>
<summary><i>There are 14 instances of this issue:</i></summary>

```solidity
📁 File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

65:     function setMrSigner(bytes32 _mrSigner, bool _trusted) external onlyOwner { 

69:     function setMrEnclave(bytes32 _mrEnclave, bool _trusted) external onlyOwner { 

73:     function addRevokedCertSerialNum( 

88:     function removeRevokedCertSerialNum( 

114:     function configureQeIdentityJson(EnclaveIdStruct.EnclaveId calldata qeIdentityInput) 

122:     function toggleLocalReportCheck() external onlyOwner { 

138:     function verifyAttestation(bytes calldata data) external view override returns (bool) { 

248:     function _verifyCertChain(IPEMCertChainLib.ECSha256Certificate[] memory certs) 

303:     function _enclaveReportSigVerification( 

355:     function verifyParsedQuote(V3Struct.ParsedV3QuoteStruct calldata v3quote) 

364:     function _verifyParsedQuote(V3Struct.ParsedV3QuoteStruct memory v3quote) 
```
[65](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L65), [69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L69), [73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L73), [88](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L88), [114](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L114), [122](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L122), [138](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L138), [248](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L248), [303](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L303), [355](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L355), [364](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L364)

```solidity
📁 File: contracts/common/EssentialContract.sol

69:     function pause() public virtual whenNotPaused { 

78:     function unpause() public virtual whenPaused { 

88:     function paused() public view returns (bool) { 
```
[69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L69), [78](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L78), [88](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L88)

</details>


---
### [NC&#x2011;48] Functions contain the same code
The functions below have the same implementation as is seen in other files. The functions should be refactored into functions of a common base contract.

<details>
<summary><i>There are 16 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoToken.sol

47:     function burn(address _from, uint256 _amount) public onlyOwner { 
48:         _burn(_from, _amount);
49:     }

52:     function snapshot() public onlyFromOwnerOrNamed("snapshooter") { 
53:         _snapshot();
54:     }

94:     function _afterTokenTransfer( 
95:         address _from,
96:         address _to,
97:         uint256 _amount
98:     )
99:         internal
100:         override(ERC20Upgradeable, ERC20VotesUpgradeable)
101:     {
102:         super._afterTokenTransfer(_from, _to, _amount);
103:     }

105:     function _mint( 
106:         address _to,
107:         uint256 _amount
108:     )
109:         internal
110:         override(ERC20Upgradeable, ERC20VotesUpgradeable)
111:     {
112:         super._mint(_to, _amount);
113:     }

115:     function _burn( 
116:         address _from,
117:         uint256 _amount
118:     )
119:         internal
120:         override(ERC20Upgradeable, ERC20VotesUpgradeable)
121:     {
122:         super._burn(_from, _amount);
123:     }
```
[47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L47-L49), [52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L52-L54), [94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L94-L103), [105](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L105-L113), [115](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L115-L123)

```solidity
📁 File: contracts/team/airdrop/MerkleClaimable.sol

45:     function setConfig( 
46:         uint64 _claimStart,
47:         uint64 _claimEnd,
48:         bytes32 _merkleRoot
49:     )
50:         external
51:         onlyOwner
52:     {
53:         _setConfig(_claimStart, _claimEnd, _merkleRoot);
54:     }

56:     function __MerkleClaimable_init( 
57:         uint64 _claimStart,
58:         uint64 _claimEnd,
59:         bytes32 _merkleRoot
60:     )
61:         internal
62:         onlyInitializing
63:     {
64:         _setConfig(_claimStart, _claimEnd, _merkleRoot);
65:     }
```
[45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L45-L54), [56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L56-L65)

```solidity
📁 File: contracts/tokenvault/BridgedERC1155.sol

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
137:         if (_to == address(this)) revert BTOKEN_CANNOT_RECEIVE();
138:         if (paused()) revert INVALID_PAUSE_STATUS();
139:     }
```
[125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L125-L139)

```solidity
📁 File: contracts/tokenvault/BridgedERC20.sol

85:     function snapshot() external onlyOwnerOrSnapshooter { 
86:         _snapshot();
87:     }

133:     function _burnToken(address _from, uint256 _amount) internal override { 
134:         _burn(_from, _amount);
135:     }

152:     function _afterTokenTransfer( 
153:         address _from,
154:         address _to,
155:         uint256 _amount
156:     )
157:         internal
158:         override(ERC20Upgradeable, ERC20VotesUpgradeable)
159:     {
160:         super._afterTokenTransfer(_from, _to, _amount);
161:     }

163:     function _mint( 
164:         address _to,
165:         uint256 _amount
166:     )
167:         internal
168:         override(ERC20Upgradeable, ERC20VotesUpgradeable)
169:     {
170:         super._mint(_to, _amount);
171:     }

173:     function _burn( 
174:         address _from,
175:         uint256 _amount
176:     )
177:         internal
178:         override(ERC20Upgradeable, ERC20VotesUpgradeable)
179:     {
180:         super._burn(_from, _amount);
181:     }
```
[85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L85-L87), [133](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L133-L135), [152](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L152-L161), [163](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L163-L171), [173](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L173-L181)

```solidity
📁 File: contracts/tokenvault/BridgedERC721.sol

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
125:         if (_to == address(this)) revert BTOKEN_CANNOT_RECEIVE();
126:         if (paused()) revert INVALID_PAUSE_STATUS();
127:     }
```
[115](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L115-L127)

```solidity
📁 File: contracts/tokenvault/ERC1155Vault.sol

288:     function _getOrDeployBridgedToken(CanonicalNFT memory _ctoken) 
289:         private
290:         returns (address btoken_)
291:     {
292:         btoken_ = canonicalToBridged[_ctoken.chainId][_ctoken.addr];
293:         if (btoken_ == address(0)) {
294:             btoken_ = _deployBridgedToken(_ctoken);
295:         }
296:     }
```
[288](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L288-L296)

```solidity
📁 File: contracts/tokenvault/ERC721Vault.sol

224:     function _getOrDeployBridgedToken(CanonicalNFT memory _ctoken) 
225:         private
226:         returns (address btoken_)
227:     {
228:         btoken_ = canonicalToBridged[_ctoken.chainId][_ctoken.addr];
229: 
230:         if (btoken_ == address(0)) {
231:             btoken_ = _deployBridgedToken(_ctoken);
232:         }
233:     }
```
[224](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L224-L233)

</details>


---
### [NC&#x2011;49] Functions not used internally could be marked external
Contracts [are allowed](https://docs.soliditylang.org/en/latest/contracts.html#function-overriding) to override their parents' functions and change the visibility from `external` to `public`.

<details>
<summary><i>There are 40 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoL1.sol

124:     function unpause() public override { 

132:     function canDepositEthToL2(uint256 _amount) public view returns (bool) { 

137:     function isBlobReusable(bytes32 _blobHash) public view returns (bool) { 

145:     function getBlock(uint64 _blockId) 

162:     function getTransition( 
163:         uint64 _blockId,
164:         bytes32 _parentHash
165:     )

176:     function getStateVariables() 
```
[124](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L124), [132](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L132), [137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L137), [145](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L145), [162](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L162-L165), [176](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L176)

```solidity
📁 File: contracts/L1/TaikoToken.sol

25:     function init( 
26:         address _owner,
27:         string calldata _name,
28:         string calldata _symbol,
29:         address _recipient
30:     )

47:     function burn(address _from, uint256 _amount) public onlyOwner { 

52:     function snapshot() public onlyFromOwnerOrNamed("snapshooter") { 

60:     function transfer(address _to, uint256 _amount) public override returns (bool) { 

70:     function transferFrom( 
71:         address _from,
72:         address _to,
73:         uint256 _amount
74:     )
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L25-L30), [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L47), [52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L52), [60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L60), [70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L70-L74)

```solidity
📁 File: contracts/L1/gov/TaikoGovernor.sol

48:     function propose( 
49:         address[] memory _targets,
50:         uint256[] memory _values,
51:         bytes[] memory _calldatas,
52:         string memory _description
53:     )

89:     function supportsInterface(bytes4 _interfaceId) 

99:     function state(uint256 _proposalId) 

111:     function votingDelay() public pure override returns (uint256) { 

117:     function votingPeriod() public pure override returns (uint256) { 

123:     function proposalThreshold() public pure override returns (uint256) { 
```
[48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L48-L53), [89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L89), [99](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L99), [111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L111), [117](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L117), [123](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L123)

```solidity
📁 File: contracts/L1/gov/TaikoTimelockController.sol

24:     function getMinDelay() public view override returns (uint256) { 
```
[24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L24)

```solidity
📁 File: contracts/L1/provers/Guardians.sol

107:     function numGuardians() public view returns (uint256) { 
```
[107](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L107)

```solidity
📁 File: contracts/L1/tiers/DevnetTierProvider.sol

20:     function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) { 

47:     function getTierIds() public pure override returns (uint16[] memory tiers_) { 

54:     function getMinTier(uint256) public pure override returns (uint16) { 
```
[20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L20), [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L47), [54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L54)

```solidity
📁 File: contracts/L1/tiers/MainnetTierProvider.sol

20:     function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) { 

58:     function getTierIds() public pure override returns (uint16[] memory tiers_) { 

66:     function getMinTier(uint256 _rand) public pure override returns (uint16) { 
```
[20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L20), [58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L58), [66](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L66)

```solidity
📁 File: contracts/L1/tiers/TestnetTierProvider.sol

20:     function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) { 

58:     function getTierIds() public pure override returns (uint16[] memory tiers_) { 

66:     function getMinTier(uint256 _rand) public pure override returns (uint16) { 
```
[20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L20), [58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L58), [66](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L66)

```solidity
📁 File: contracts/L2/TaikoL2.sol

185:     function getBasefee( 
186:         uint64 _l1BlockId,
187:         uint32 _parentGasUsed
188:     )

200:     function getBlockHash(uint64 _blockId) public view returns (bytes32) { 
```
[185](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L185-L188), [200](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L200)

```solidity
📁 File: contracts/L2/TaikoL2EIP1559Configurable.sol

43:     function getConfig() public view override returns (Config memory) { 
```
[43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L43)

```solidity
📁 File: contracts/bridge/Bridge.sol

340:     function isMessageSent(Message calldata _message) public view returns (bool) { 

352:     function proveMessageFailed( 
353:         Message calldata _message,
354:         bytes calldata _proof
355:     )

374:     function proveMessageReceived( 
375:         Message calldata _message,
376:         bytes calldata _proof
377:     )

403:     function context() public view returns (Context memory ctx_) { 
```
[340](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L340), [352](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L352-L355), [374](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L374-L377), [403](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L403)

```solidity
📁 File: contracts/common/AddressManager.sol

54:     function getAddress(uint64 _chainId, bytes32 _name) public view override returns (address) { 
```
[54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L54)

```solidity
📁 File: contracts/signal/SignalService.sol

137:     function isChainDataSynced( 
138:         uint64 _chainId,
139:         bytes32 _kind,
140:         uint64 _blockId,
141:         bytes32 _chainData
142:     )

153:     function isSignalSent(address _app, bytes32 _signal) public view returns (bool) { 

158:     function getSyncedChainData( 
159:         uint64 _chainId,
160:         bytes32 _kind,
161:         uint64 _blockId
162:     )
```
[137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L137-L142), [153](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L153), [158](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L158-L162)

```solidity
📁 File: contracts/tokenvault/BridgedERC20.sol

91:     function name() 
```
[91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L91)

</details>


---
### [NC&#x2011;50] Functions should be named in mixedCase style
According to the Solidity [style guide](https://docs.soliditylang.org/en/latest/style-guide.html#function-names) function names should be in `mixedCase` (lowerCamelCase)Rule exceptions
- Allow `_` at the beginning of the mixedCase match for `private`/`internal` functions.

<details>
<summary><i>There are 16 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L2/CrossChainOwned.sol

/// @audit __CrossChainOwned_init
60:     function __CrossChainOwned_init( 
```
[60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L60)

```solidity
📁 File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

/// @audit _verifyQEReportWithIdentity
175:     function _verifyQEReportWithIdentity(V3Struct.EnclaveReport memory quoteEnclaveReport) 
```
[175](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L175)

```solidity
📁 File: contracts/automata-attestation/interfaces/ISigVerifyLib.sol

/// @audit verifyRS256Signature
58:     function verifyRS256Signature( 

/// @audit verifyRS1Signature
67:     function verifyRS1Signature( 

/// @audit verifyES256Signature
76:     function verifyES256Signature( 
```
[58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L58), [67](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L67), [76](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L76)

```solidity
📁 File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

/// @audit packQEReport
244:     function packQEReport(V3Struct.EnclaveReport memory enclaveReport) 
```
[244](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L244)

```solidity
📁 File: contracts/automata-attestation/utils/SigVerifyLib.sol

/// @audit verifyRS256Signature
79:     function verifyRS256Signature( 

/// @audit verifyRS1Signature
96:     function verifyRS1Signature( 

/// @audit verifyES256Signature
113:     function verifyES256Signature( 
```
[79](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L79), [96](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L96), [113](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L113)

```solidity
📁 File: contracts/common/AddressResolver.sol

/// @audit __AddressResolver_init
58:     function __AddressResolver_init(address _addressManager) internal virtual onlyInitializing { 
```
[58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L58)

```solidity
📁 File: contracts/common/EssentialContract.sol

/// @audit __Essential_init
95:     function __Essential_init( 

/// @audit __Essential_init
109:     function __Essential_init(address _owner) internal virtual { 
```
[95](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L95), [109](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L109)

```solidity
📁 File: contracts/libs/LibAddress.sol

/// @audit isSenderEOA
77:     function isSenderEOA() internal view returns (bool) { 
```
[77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L77)

```solidity
📁 File: contracts/team/airdrop/MerkleClaimable.sol

/// @audit __MerkleClaimable_init
56:     function __MerkleClaimable_init( 
```
[56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L56)

```solidity
📁 File: contracts/thirdparty/optimism/rlp/RLPReader.sol

/// @audit toRLPItem
35:     function toRLPItem(bytes memory _in) internal pure returns (RLPItem memory out_) { 
```
[35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L35)

```solidity
📁 File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

/// @audit _getNodeID
220:     function _getNodeID(RLPReader.RLPItem memory _node) private pure returns (bytes memory id_) { 
```
[220](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L220)

</details>


---
### [NC&#x2011;51] High cyclomatic complexity
Functions with high cyclomatic complexity are harder to understand, test, and maintain. Consider breaking down these blocks into more manageable units, by splitting things into utility functions, by reducing nesting, and by using early returns.

[Learn More About Cyclomatic Complexity](https://en.wikipedia.org/wiki/Cyclomatic_complexity)

<details>
<summary><i>There are 26 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

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
[62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L62-L71)

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

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
```
[68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L68-L77)

```solidity
📁 File: contracts/L1/libs/LibProving.sol

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
```
[91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L91-L101), [350](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L350-L359)

```solidity
📁 File: contracts/L1/libs/LibVerifying.sol

85:     function verifyBlocks( 
86:         TaikoData.State storage _state,
87:         TaikoData.Config memory _config,
88:         IAddressResolver _resolver,
89:         uint64 _maxBlocksToVerify
90:     )
91:         internal
92:     {
```
[85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L85-L92)

```solidity
📁 File: contracts/L2/TaikoL2.sol

107:     function anchor( 
108:         bytes32 _l1BlockHash,
109:         bytes32 _l1StateRoot,
110:         uint64 _l1BlockId,
111:         uint32 _parentGasUsed
112:     )
113:         external
114:         nonReentrant
115:     {

252:     function _calc1559BaseFee( 
253:         Config memory _config,
254:         uint64 _l1BlockId,
255:         uint32 _parentGasUsed
256:     )
257:         private
258:         view
259:         returns (uint256 basefee_, uint64 gasExcess_)
260:     {
```
[107](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L107-L115), [252](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L252-L260)

```solidity
📁 File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

248:     function _verifyCertChain(IPEMCertChainLib.ECSha256Certificate[] memory certs) 
249:         private
250:         view
251:         returns (bool)
252:     {

364:     function _verifyParsedQuote(V3Struct.ParsedV3QuoteStruct memory v3quote) 
365:         internal
366:         view
367:         returns (bool, bytes memory)
368:     {
```
[248](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L248-L252), [364](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L364-L368)

```solidity
📁 File: contracts/automata-attestation/lib/PEMCertChainLib.sol

74:     function decodeCert( 
75:         bytes memory der,
76:         bool isPckCert
77:     )
78:         external
79:         pure
80:         returns (bool success, ECSha256Certificate memory cert)
81:     {

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
```
[74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L74-L81), [269](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L269-L283)

```solidity
📁 File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

21:     function parseInput( 
22:         bytes memory quote,
23:         address pemCertLibAddr
24:     )
25:         internal
26:         pure
27:         returns (bool success, V3Struct.ParsedV3QuoteStruct memory v3ParsedQuote)
28:     {

165:     function parseAndVerifyHeader(bytes memory rawHeader) 
166:         private
167:         pure
168:         returns (bool success, V3Struct.Header memory header)
169:     {
```
[21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L21-L28), [165](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L165-L169)

```solidity
📁 File: contracts/automata-attestation/utils/BytesUtils.sol

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
[56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L56-L67), [320](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L320-L328)

```solidity
📁 File: contracts/automata-attestation/utils/RsaVerify.sol

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
```
[43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L43-L52), [212](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L212-L221)

```solidity
📁 File: contracts/automata-attestation/utils/SigVerifyLib.sol

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
```
[24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L24-L33), [54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L54-L63)

```solidity
📁 File: contracts/bridge/Bridge.sol

155:     function recallMessage( 
156:         Message calldata _message,
157:         bytes calldata _proof
158:     )
159:         external
160:         nonReentrant
161:         whenNotPaused
162:         sameChain(_message.srcChainId)
163:     {

217:     function processMessage( 
218:         Message calldata _message,
219:         bytes calldata _proof
220:     )
221:         external
222:         nonReentrant
223:         whenNotPaused
224:         sameChain(_message.destChainId)
225:     {

310:     function retryMessage( 
311:         Message calldata _message,
312:         bool _isLastAttempt
313:     )
314:         external
315:         nonReentrant
316:         whenNotPaused
317:         sameChain(_message.destChainId)
318:     {
```
[155](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L155-L163), [217](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L217-L225), [310](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L310-L318)

```solidity
📁 File: contracts/signal/SignalService.sol

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
[83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L83-L93)

```solidity
📁 File: contracts/team/TimelockTokenPool.sol

245:     function _calcAmount( 
246:         uint128 _amount,
247:         uint64 _start,
248:         uint64 _cliff,
249:         uint64 _period
250:     )
251:         private
252:         view
253:         returns (uint128)
254:     {
```
[245](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L245-L254)

```solidity
📁 File: contracts/thirdparty/optimism/rlp/RLPReader.sol

144:     function _decodeLength(RLPItem memory _in) 
145:         private
146:         pure
147:         returns (uint256 offset_, uint256 length_, RLPItemType type_)
148:     {
```
[144](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L144-L148)

```solidity
📁 File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

68:     function get( 
69:         bytes memory _key,
70:         bytes[] memory _proof,
71:         bytes32 _root
72:     )
73:         internal
74:         pure
75:         returns (bytes memory value_)
76:     {
```
[68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L68-L76)

</details>


---
### [NC&#x2011;52] `if`-statement can be converted to a ternary
The code can be made more compact while also increasing readability by converting the following `if`-statements to ternaries (e.g. `foo += (x > y) ? a : b`)

<details>
<summary><i>There are 16 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

109:         if (assignment.feeToken == address(0)) { 
110:             // Paying Ether
111:             _blk.assignedProver.sendEther(proverFee, MAX_GAS_PAYING_PROVER);
112:         } else {
113:             // Paying ERC20 tokens
114:             IERC20(assignment.feeToken).safeTransferFrom(
115:                 _meta.coinbase, _blk.assignedProver, proverFee
116:             );
117:         }
```
[109](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L109-L117)

```solidity
📁 File: contracts/L1/libs/LibProving.sol

381:             if (reward > _tier.validityBond) { 
382:                 _tko.transfer(msg.sender, reward - _tier.validityBond);
383:             } else {
384:                 _tko.transferFrom(msg.sender, address(this), _tier.validityBond - reward);
385:             }
```
[381](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L381-L385)

```solidity
📁 File: contracts/L1/libs/LibUtils.sol

80:         if (_state.transitions[_slot][1].key == _parentHash) { 
81:             tid_ = 1;
82:         } else {
83:             tid_ = _state.transitionIds[_blk.blockId][_parentHash];
84:         }
```
[80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L80-L84)

```solidity
📁 File: contracts/L1/tiers/MainnetTierProvider.sol

68:         if (_rand % 1000 == 0) return LibTiers.TIER_SGX_ZKVM; 
69:         else return LibTiers.TIER_SGX;
```
[68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L68-L69)

```solidity
📁 File: contracts/L2/TaikoL2.sol

173:         if (_token == address(0)) { 
174:             _to.sendEther(address(this).balance);
175:         } else {
176:             IERC20(_token).safeTransfer(_to, IERC20(_token).balanceOf(address(this)));
177:         }
```
[173](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L173-L177)

```solidity
📁 File: contracts/automata-attestation/lib/PEMCertChainLib.sol

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
[56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L56-L60), [333](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L333-L337)

```solidity
📁 File: contracts/automata-attestation/utils/Asn1Decode.sol

158:         if (der[ptr.ixf()] == 0) { 
159:             return der.substring(ptr.ixf() + 1, valueLength - 1);
160:         } else {
161:             return der.substring(ptr.ixf(), valueLength);
162:         }
```
[158](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L158-L162)

```solidity
📁 File: contracts/automata-attestation/utils/BytesUtils.sol

90:                 if (shortest > 32) { 
91:                     mask = type(uint256).max; // aka 0xffffff....
92:                 } else {
93:                     mask = ~(2 ** (8 * (32 - shortest + idx)) - 1);
94:                 }
```
[90](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L90-L94)

```solidity
📁 File: contracts/automata-attestation/utils/RsaVerify.sol

151:         if (digestAlgoWithParamLen == sha256ExplicitNullParam.length) { 
152:             for (uint256 i; i < digestAlgoWithParamLen; ++i) {
153:                 if (decipher[3 + paddingLen + i] != bytes1(sha256ExplicitNullParam[i])) {
154:                     return false;
155:                 }
156:             }
157:         } else {
158:             for (uint256 i; i < digestAlgoWithParamLen; ++i) {
159:                 if (decipher[3 + paddingLen + i] != bytes1(sha256ImplicitNullParam[i])) {
160:                     return false;
161:                 }
162:             }
163:         }
```
[151](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L151-L163)

```solidity
📁 File: contracts/automata-attestation/utils/X509DateUtils.sol

18:             if (uint8(x509Time[0]) - 48 < 5) yrs += 2000; 
19:             else yrs += 1900;

49:             if (isLeapYear(i)) { 
50:                 timestamp += 31_622_400; // Leap year in seconds
51:             } else {
52:                 timestamp += 31_536_000; // Normal year in seconds
53:             }
```
[18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L18-L19), [49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L49-L53)

```solidity
📁 File: contracts/bridge/Bridge.sol

282:                 if (_invokeMessageCall(_message, msgHash, gasLimit)) { 
283:                     _updateMessageStatus(msgHash, Status.DONE);
284:                 } else {
285:                     _updateMessageStatus(msgHash, Status.RETRIABLE);
286:                 }

530:         if (block.chainid == 1) { 
531:             _storeContext(bytes32(0), address(0), uint64(0));
532:         } else {
533:             _storeContext(bytes32(PLACEHOLDER), address(uint160(PLACEHOLDER)), uint64(PLACEHOLDER));
534:         }
```
[282](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L282-L286), [530](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L530-L534)

```solidity
📁 File: contracts/libs/LibAddress.sol

70:         if (Address.isContract(_addr)) { 
71:             return IERC1271(_addr).isValidSignature(_hash, _sig) == _EIP1271_MAGICVALUE;
72:         } else {
73:             return ECDSA.recover(_hash, _sig) == _addr;
74:         }
```
[70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L70-L74)

```solidity
📁 File: contracts/thirdparty/optimism/rlp/RLPWriter.sol

14:         if (_in.length == 1 && uint8(_in[0]) < 128) { 
15:             out_ = _in;
16:         } else {
17:             out_ = abi.encodePacked(_writeLength(_in.length, 128), _in);
18:         }
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L14-L18)

</details>


---
### [NC&#x2011;53] Import declarations should import specific identifiers, rather than the whole file
Using import declarations of the form `import {<identifier_name>} from "some/file.sol"` avoids polluting the symbol namespace making flattened files smaller, and speeds up compilation (but does not save any gas)

<details>
<summary><i>There are 40 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/ITaikoL1.sol

4: import "./TaikoData.sol"; 
```
[4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/ITaikoL1.sol#L4)

```solidity
📁 File: contracts/L1/gov/TaikoGovernor.sol

4: import "@openzeppelin/contracts-upgradeable/governance/GovernorUpgradeable.sol"; 
5: import

7: import "@openzeppelin/contracts-upgradeable/governance/extensions/GovernorVotesUpgradeable.sol"; 
8: import

10: import 

12: import "../../common/EssentialContract.sol"; 
```
[4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L4-L5), [7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L7-L8), [10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L10), [12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L12)

```solidity
📁 File: contracts/L1/gov/TaikoTimelockController.sol

4: import "@openzeppelin/contracts-upgradeable/governance/TimelockControllerUpgradeable.sol"; 
5: import "../../common/EssentialContract.sol";
```
[4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L4-L5)

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol"; 
5: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
6: import "../../common/EssentialContract.sol";
7: import "../../libs/LibAddress.sol";
8: import "../ITaikoL1.sol";
9: import "./IHook.sol";
```
[4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L4-L9)

```solidity
📁 File: contracts/L1/hooks/IHook.sol

4: import "../TaikoData.sol"; 
```
[4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/IHook.sol#L4)

```solidity
📁 File: contracts/L1/libs/LibDepositing.sol

4: import "../../common/IAddressResolver.sol"; 
5: import "../../libs/LibAddress.sol";
6: import "../../libs/LibMath.sol";
7: import "../TaikoData.sol";
```
[4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L4-L7)

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol"; 
5: import "../../common/IAddressResolver.sol";
6: import "../../libs/LibAddress.sol";
7: import "../hooks/IHook.sol";
```
[4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L4-L7)

```solidity
📁 File: contracts/common/AddressManager.sol

4: import "./IAddressManager.sol"; 
5: import "./EssentialContract.sol";
```
[4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L4-L5)

```solidity
📁 File: contracts/common/AddressResolver.sol

4: import "@openzeppelin/contracts-upgradeable/proxy/utils/Initializable.sol"; 
5: import "./IAddressManager.sol";
6: import "./IAddressResolver.sol";
```
[4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L4-L6)

```solidity
📁 File: contracts/common/EssentialContract.sol

4: import "@openzeppelin/contracts/proxy/utils/UUPSUpgradeable.sol"; 
5: import "@openzeppelin/contracts-upgradeable/access/Ownable2StepUpgradeable.sol";
6: import "./AddressResolver.sol";
```
[4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L4-L6)

```solidity
📁 File: contracts/libs/LibAddress.sol

4: import "@openzeppelin/contracts/utils/Address.sol"; 
5: import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol";
6: import "@openzeppelin/contracts/utils/introspection/IERC165.sol";
7: import "@openzeppelin/contracts/interfaces/IERC1271.sol";
8: import "../thirdparty/nomad-xyz/ExcessivelySafeCall.sol";
```
[4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L4-L8)

```solidity
📁 File: contracts/libs/LibTrieProof.sol

9: import "../thirdparty/optimism/rlp/RLPReader.sol"; 
10: import "../thirdparty/optimism/rlp/RLPWriter.sol";
11: import "../thirdparty/optimism/trie/SecureMerkleTrie.sol";
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L9-L11)

</details>


---
### [NC&#x2011;54] Imports could be organized more systematically
The contract's interface should be imported first, followed by each of the interfaces it uses, followed by all other files. The examples below do not follow this layout.

<details>
<summary><i>There are 28 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoL1.sol

2: pragma solidity ^0.8.0; 
3: 
4: import "../common/EssentialContract.sol";
5: import "./libs/LibDepositing.sol";
6: import "./libs/LibProposing.sol";
7: import "./libs/LibProving.sol";
8: import "./libs/LibVerifying.sol";
9: import "./ITaikoL1.sol";
10: import "./TaikoErrors.sol";
11: import "./TaikoEvents.sol";
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L2-L11)

```solidity
📁 File: contracts/L1/TaikoToken.sol

2: pragma solidity ^0.8.0; 
3: 
4: import "@openzeppelin/contracts-upgradeable/token/ERC20/ERC20Upgradeable.sol";
5: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20SnapshotUpgradeable.sol";
6: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20VotesUpgradeable.sol";
7: import "../common/EssentialContract.sol";
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L2-L7)

```solidity
📁 File: contracts/L1/gov/TaikoGovernor.sol

2: pragma solidity ^0.8.0; 
3: 
4: import "@openzeppelin/contracts-upgradeable/governance/GovernorUpgradeable.sol";
5: import
6:     "@openzeppelin/contracts-upgradeable/governance/compatibility/GovernorCompatibilityBravoUpgradeable.sol";
7: import "@openzeppelin/contracts-upgradeable/governance/extensions/GovernorVotesUpgradeable.sol";
8: import
9:     "@openzeppelin/contracts-upgradeable/governance/extensions/GovernorVotesQuorumFractionUpgradeable.sol";
10: import
11:     "@openzeppelin/contracts-upgradeable/governance/extensions/GovernorTimelockControlUpgradeable.sol";
12: import "../../common/EssentialContract.sol";
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L2-L12)

```solidity
📁 File: contracts/L1/gov/TaikoTimelockController.sol

2: pragma solidity ^0.8.0; 
3: 
4: import "@openzeppelin/contracts-upgradeable/governance/TimelockControllerUpgradeable.sol";
5: import "../../common/EssentialContract.sol";
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L2-L5)

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

2: pragma solidity ^0.8.0; 
3: 
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
5: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
6: import "../../common/EssentialContract.sol";
7: import "../../libs/LibAddress.sol";
8: import "../ITaikoL1.sol";
9: import "./IHook.sol";
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L2-L9)

```solidity
📁 File: contracts/L1/provers/GuardianProver.sol

2: pragma solidity ^0.8.0; 
3: 
4: import "../tiers/ITierProvider.sol";
5: import "../ITaikoL1.sol";
6: import "./Guardians.sol";
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L2-L6)

```solidity
📁 File: contracts/L2/CrossChainOwned.sol

2: pragma solidity ^0.8.0; 
3: 
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
5: import "../common/EssentialContract.sol";
6: import "../bridge/IBridge.sol";
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L2-L6)

```solidity
📁 File: contracts/L2/TaikoL2.sol

2: pragma solidity ^0.8.0; 
3: 
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
5: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
6: 
7: import "../libs/LibAddress.sol";
8: import "../libs/LibMath.sol";
9: import "../signal/ISignalService.sol";
10: import "../signal/LibSignals.sol";
11: import "./Lib1559Math.sol";
12: import "./CrossChainOwned.sol";
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L2-L12)

```solidity
📁 File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

2: pragma solidity ^0.8.0; 
3: 
4: import { V3Struct } from "./lib/QuoteV3Auth/V3Struct.sol";
5: import { V3Parser } from "./lib/QuoteV3Auth/V3Parser.sol";
6: import { IPEMCertChainLib } from "./lib/interfaces/IPEMCertChainLib.sol";
7: import { PEMCertChainLib } from "./lib/PEMCertChainLib.sol";
8: import { TCBInfoStruct } from "./lib/TCBInfoStruct.sol";
9: import { EnclaveIdStruct } from "./lib/EnclaveIdStruct.sol";
10: import { IAttestation } from "./interfaces/IAttestation.sol";
11: 
12: // Internal Libraries
13: import { Base64 } from "solady/src/utils/Base64.sol";
14: import { LibString } from "solady/src/utils/LibString.sol";
15: import { BytesUtils } from "./utils/BytesUtils.sol";
16: 
17: // External Libraries
18: import { ISigVerifyLib } from "./interfaces/ISigVerifyLib.sol";
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L2-L18)

```solidity
📁 File: contracts/automata-attestation/lib/PEMCertChainLib.sol

2: pragma solidity ^0.8.0; 
3: 
4: import { LibString } from "solady/src/utils/LibString.sol";
5: import { Asn1Decode, NodePtr } from "../utils/Asn1Decode.sol";
6: import { BytesUtils } from "../utils/BytesUtils.sol";
7: import { X509DateUtils } from "../utils/X509DateUtils.sol";
8: import { IPEMCertChainLib } from "./interfaces/IPEMCertChainLib.sol";
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L2-L8)

```solidity
📁 File: contracts/bridge/Bridge.sol

2: pragma solidity ^0.8.0; 
3: 
4: import "@openzeppelin/contracts/utils/Address.sol";
5: import "../common/EssentialContract.sol";
6: import "../libs/LibAddress.sol";
7: import "../signal/ISignalService.sol";
8: import "../thirdparty/nomad-xyz/ExcessivelySafeCall.sol";
9: import "./IBridge.sol";
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L2-L9)

```solidity
📁 File: contracts/common/AddressManager.sol

2: pragma solidity ^0.8.0; 
3: 
4: import "./IAddressManager.sol";
5: import "./EssentialContract.sol";
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L2-L5)

```solidity
📁 File: contracts/common/AddressResolver.sol

2: pragma solidity ^0.8.0; 
3: 
4: import "@openzeppelin/contracts-upgradeable/proxy/utils/Initializable.sol";
5: import "./IAddressManager.sol";
6: import "./IAddressResolver.sol";
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L2-L6)

```solidity
📁 File: contracts/signal/SignalService.sol

2: pragma solidity ^0.8.0; 
3: 
4: import "@openzeppelin/contracts/utils/math/SafeCast.sol";
5: import "../common/EssentialContract.sol";
6: import "../libs/LibTrieProof.sol";
7: import "./ISignalService.sol";
8: import "./LibSignals.sol";
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L2-L8)

```solidity
📁 File: contracts/team/TimelockTokenPool.sol

2: pragma solidity ^0.8.0; 
3: 
4: import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol";
5: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
6: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
7: import "../common/EssentialContract.sol";
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L2-L7)

```solidity
📁 File: contracts/team/airdrop/ERC20Airdrop.sol

2: pragma solidity ^0.8.0; 
3: 
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
5: import "@openzeppelin/contracts/governance/utils/IVotes.sol";
6: import "./MerkleClaimable.sol";
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L2-L6)

```solidity
📁 File: contracts/team/airdrop/ERC20Airdrop2.sol

2: pragma solidity ^0.8.0; 
3: 
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
5: import "../../libs/LibMath.sol";
6: import "./MerkleClaimable.sol";
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L2-L6)

```solidity
📁 File: contracts/team/airdrop/ERC721Airdrop.sol

2: pragma solidity ^0.8.0; 
3: 
4: import "@openzeppelin/contracts/token/ERC721/IERC721.sol";
5: import "./MerkleClaimable.sol";
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L2-L5)

```solidity
📁 File: contracts/team/airdrop/MerkleClaimable.sol

2: pragma solidity ^0.8.0; 
3: 
4: import "@openzeppelin/contracts/utils/cryptography/MerkleProof.sol";
5: import "../../common/EssentialContract.sol";
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L2-L5)

```solidity
📁 File: contracts/tokenvault/BaseVault.sol

2: pragma solidity ^0.8.0; 
3: 
4: import "@openzeppelin/contracts-upgradeable/utils/introspection/IERC165Upgradeable.sol";
5: import "@openzeppelin/contracts/proxy/ERC1967/ERC1967Proxy.sol";
6: import "../bridge/IBridge.sol";
7: import "../common/EssentialContract.sol";
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L2-L7)

```solidity
📁 File: contracts/tokenvault/BridgedERC1155.sol

2: pragma solidity ^0.8.0; 
3: 
4: import "@openzeppelin/contracts/utils/Strings.sol";
5: import "@openzeppelin/contracts-upgradeable/token/ERC1155/ERC1155Upgradeable.sol";
6: import
7:     "@openzeppelin/contracts-upgradeable/token/ERC1155/extensions/IERC1155MetadataURIUpgradeable.sol";
8: import "../common/EssentialContract.sol";
9: import "./LibBridgedToken.sol";
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L2-L9)

```solidity
📁 File: contracts/tokenvault/BridgedERC20.sol

2: pragma solidity ^0.8.0; 
3: 
4: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/IERC20MetadataUpgradeable.sol";
5: import "@openzeppelin/contracts/utils/Strings.sol";
6: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20SnapshotUpgradeable.sol";
7: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20VotesUpgradeable.sol";
8: import "./LibBridgedToken.sol";
9: import "./BridgedERC20Base.sol";
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L2-L9)

```solidity
📁 File: contracts/tokenvault/BridgedERC721.sol

2: pragma solidity ^0.8.0; 
3: 
4: import "@openzeppelin/contracts-upgradeable/token/ERC721/ERC721Upgradeable.sol";
5: import "@openzeppelin/contracts/utils/Strings.sol";
6: import "../common/EssentialContract.sol";
7: import "./LibBridgedToken.sol";
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L2-L7)

```solidity
📁 File: contracts/tokenvault/ERC1155Vault.sol

2: pragma solidity ^0.8.0; 
3: 
4: import "@openzeppelin/contracts/token/ERC1155/IERC1155.sol";
5: import "@openzeppelin/contracts-upgradeable/token/ERC1155/utils/ERC1155ReceiverUpgradeable.sol";
6: import "../bridge/IBridge.sol";
7: import "../libs/LibAddress.sol";
8: import "./BaseNFTVault.sol";
9: import "./BridgedERC1155.sol";
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L2-L9)

```solidity
📁 File: contracts/tokenvault/ERC20Vault.sol

2: pragma solidity ^0.8.0; 
3: 
4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
5: import "@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol";
6: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
7: import "../bridge/IBridge.sol";
8: import "../libs/LibAddress.sol";
9: import "./BridgedERC20.sol";
10: import "./BaseVault.sol";
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L2-L10)

```solidity
📁 File: contracts/tokenvault/ERC721Vault.sol

2: pragma solidity ^0.8.0; 
3: 
4: import "@openzeppelin/contracts/token/ERC721/IERC721.sol";
5: import "@openzeppelin/contracts/token/ERC721/IERC721Receiver.sol";
6: import "../bridge/IBridge.sol";
7: import "../libs/LibAddress.sol";
8: import "./BaseNFTVault.sol";
9: import "./BridgedERC721.sol";
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L2-L9)

```solidity
📁 File: contracts/verifiers/GuardianVerifier.sol

2: pragma solidity ^0.8.0; 
3: 
4: import "../common/EssentialContract.sol";
5: import "../L1/TaikoData.sol";
6: import "./IVerifier.sol";
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L2-L6)

```solidity
📁 File: contracts/verifiers/SgxVerifier.sol

2: pragma solidity ^0.8.0; 
3: 
4: import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol";
5: import "../L1/ITaikoL1.sol";
6: import "../common/EssentialContract.sol";
7: import "../thirdparty/optimism/Bytes.sol";
8: import "../automata-attestation/interfaces/IAttestation.sol";
9: import "../automata-attestation/lib/QuoteV3Auth/V3Struct.sol";
10: import "./IVerifier.sol";
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L2-L10)

</details>


---
### [NC&#x2011;55] Inconsistent spacing in comments
Some lines use `// x` and some use `//x`. The instances below point out the usages that don't follow the majority, within each file

<details>
<summary><i>There are 40 instances of this issue:</i></summary>

```solidity
📁 File: contracts/common/AddressManager.sol

/// @audit Space: `3`
/// @audit No space: `13`
1: // SPDX-License-Identifier: MIT 

7: /// @title AddressManager 
8: /// @notice See the documentation in {IAddressManager}.
9: /// @custom:security-contact security@taiko.xyz
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L1), [7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L7-L9)

```solidity
📁 File: contracts/common/AddressResolver.sol

/// @audit Space: `3`
/// @audit No space: `15`
1: // SPDX-License-Identifier: MIT 

8: /// @title AddressResolver 
9: /// @notice See the documentation in {IAddressResolver}.
10: /// @custom:security-contact security@taiko.xyz
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L1), [8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L8-L10)

```solidity
📁 File: contracts/common/EssentialContract.sol

/// @audit Space: `2`
/// @audit No space: `23`
1: // SPDX-License-Identifier: MIT 

8: /// @title EssentialContract 
9: /// @custom:security-contact security@taiko.xyz
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L1), [8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L8-L9)

```solidity
📁 File: contracts/common/IAddressManager.sol

/// @audit Space: `3`
/// @audit No space: `6`
1: // SPDX-License-Identifier: MIT 

4: /// @title IAddressManager 
5: /// @notice Manages a mapping of (chainId, name) pairs to Ethereum addresses.
6: /// @custom:security-contact security@taiko.xyz
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressManager.sol#L1), [4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressManager.sol#L4-L6)

```solidity
📁 File: contracts/common/IAddressResolver.sol

/// @audit Space: `9`
/// @audit No space: `12`
1: // SPDX-License-Identifier: MIT 

4: /// @title IAddressResolver 
5: /// @notice This contract acts as a bridge for name-to-address resolution.
6: /// It delegates the resolution to the AddressManager. By separating the logic,
7: /// we can maintain flexibility in address management without affecting the
8: /// resolving process.
9: /// @dev Note that the address manager should be changed using upgradability, there
10: /// is no setAddressManager() function to guarantee atomicity across all
11: /// contracts that are resolvers.
12: /// @custom:security-contact security@taiko.xyz
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressResolver.sol#L1), [4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressResolver.sol#L4-L12)

```solidity
📁 File: contracts/libs/Lib4844.sol

/// @audit Space: `4`
/// @audit No space: `9`
1: // SPDX-License-Identifier: MIT 

4: /// @title Lib4844 
5: /// @notice A library for handling EIP-4844 blobs
6: /// @dev `solc contracts/libs/Lib4844.sol --ir > contracts/libs/Lib4844.yul`
7: /// @custom:security-contact security@taiko.xyz
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L1), [4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L4-L7)

```solidity
📁 File: contracts/libs/LibAddress.sol

/// @audit Space: `3`
/// @audit No space: `10`
1: // SPDX-License-Identifier: MIT 

10: /// @title LibAddress 
11: /// @dev Provides utilities for address-related operations.
12: /// @custom:security-contact security@taiko.xyz
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L1), [10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L10-L12)

```solidity
📁 File: contracts/libs/LibMath.sol

/// @audit Space: `3`
/// @audit No space: `8`
1: // SPDX-License-Identifier: MIT 

4: /// @title LibMath 
5: /// @dev This library offers additional math functions for uint256.
6: /// @custom:security-contact security@taiko.xyz
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibMath.sol#L1), [4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibMath.sol#L4-L6)

```solidity
📁 File: contracts/libs/LibTrieProof.sol

3: // |_   _|_ _(_) |_____  | |   __ _| |__ ___ 

13: /// @title LibTrieProof 
```
[3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L3), [13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L13)

</details>


---
### [NC&#x2011;56] Initialisms should be capitalized
According to the Solidity [style guide](https://docs.soliditylang.org/en/latest/style-guide.html#naming-styles) initialisms such as "NFT", "ERC", etc should be capitalized.

<details>
<summary><i>There are 5 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoData.sol

44:         uint256 ethDepositRingBufferSize; 
```
[44](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L44)

```solidity
📁 File: contracts/L1/libs/LibDepositing.sol

45:         uint256 slot = _state.slotA.numEthDeposits % _config.ethDepositRingBufferSize; 
```
[45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L45)

```solidity
📁 File: contracts/tokenvault/BridgedERC20Base.sol

43:         onlyFromOwnerOrNamed("erc20_vault") 
```
[43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L43)

```solidity
📁 File: contracts/tokenvault/BridgedERC721.sol

61:         onlyFromNamed("erc721_vault") 
```
[61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L61)

```solidity
📁 File: contracts/tokenvault/adapters/USDCAdapter.sol

31:     IUSDC public usdc; 
```
[31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L31)

</details>


---
### [NC&#x2011;57] Large multiples of ten should use scientific notation
Use a scientific notation rather than decimal literals (e.g. `1e6` instead of `1000000`), for better code readability.

<details>
<summary><i>There are 21 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoL1.sol

/// @audit Use 8e3
195:             blockMaxProposals: 864_000, 
/// @audit Use 8e2
196:             blockRingBufferSize: 864_100,

/// @audit Use 1e4
203:             blockMaxTxListBytes: 120_000, 

/// @audit Use 1e4
213:             ethDepositMaxAmount: 10_000 ether, 
/// @audit Use 2e3
214:             ethDepositGas: 21_000,
```
[195](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L195-L196), [203](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L203), [213](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L213-L214)

```solidity
📁 File: contracts/L1/gov/TaikoGovernor.sol

/// @audit Use 7e2
112:         return 7200; // 1 day 

/// @audit Use 1e4
124:         return 1_000_000_000 ether / 10_000; // 0.01% of Taiko Token 
```
[112](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L112), [124](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L124)

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

/// @audit Use 5e4
38:     uint256 public constant MAX_GAS_PAYING_PROVER = 50_000; 
```
[38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L38)

```solidity
📁 File: contracts/L1/tiers/ITierProvider.sol

/// @audit Use 1e3
48:     uint16 public constant TIER_GUARDIAN = 1000; 
```
[48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L48)

```solidity
📁 File: contracts/L1/tiers/MainnetTierProvider.sol

/// @audit Use 1e3
36:                 contestBond: 1000 ether, // TKO 

/// @audit Use 1e3
68:         if (_rand % 1000 == 0) return LibTiers.TIER_SGX_ZKVM; 
```
[36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L36), [68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L68)

```solidity
📁 File: contracts/L1/tiers/TestnetTierProvider.sol

/// @audit Use 1e3
36:                 contestBond: 1000 ether, // TKO 
```
[36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L36)

```solidity
📁 File: contracts/automata-attestation/utils/X509DateUtils.sol

/// @audit Use 2e3
18:             if (uint8(x509Time[0]) - 48 < 5) yrs += 2000; 
/// @audit Use 1e2
19:             else yrs += 1900;

/// @audit Use 1e3
21:             yrs += (uint8(x509Time[0]) - 48) * 1000 + (uint8(x509Time[1]) - 48) * 100; 

/// @audit Use 8e2
60:             timestamp += uint256(monthDays[i - 1]) * 86_400; // Days in seconds 

/// @audit Use 8e2
63:         timestamp += uint256(day - 1) * 86_400; // Days in seconds 
/// @audit Use 3e2
64:         timestamp += uint256(hour) * 3600; // Hours in seconds
```
[18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L18-L19), [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L21), [60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L60), [63](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L63-L64)

```solidity
📁 File: contracts/bridge/Bridge.sol

/// @audit Use 1e3
434:                 || block.chainid == 17_000 // Holesky 

/// @audit Use 3e2
/// @audit Use 3e2
439:         } else if (block.chainid >= 32_300 && block.chainid <= 32_400) { 
```
[434](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L434), [439](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L439)

</details>


---
### [NC&#x2011;58] Large numeric literals should use underscores for readability
<details>
<summary><i>There are 23 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoL1.sol

209:             ethDepositRingBufferSize: 1024, 
```
[209](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L209)

```solidity
📁 File: contracts/L1/gov/TaikoGovernor.sol

112:         return 7200; // 1 day 
```
[112](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L112)

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

21:     uint256 public constant MAX_BYTES_PER_BLOB = 4096 * 32; 
```
[21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L21)

```solidity
📁 File: contracts/L1/libs/LibVerifying.sol

251:                 || _config.blockMaxTxListBytes > 128 * 1024 // calldata up to 128K 
```
[251](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L251)

```solidity
📁 File: contracts/L1/tiers/DevnetTierProvider.sol

26:                 cooldownWindow: 1440, //24 hours 

38:                 provingWindow: 2880, // 48 hours 
```
[26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L26), [38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L38)

```solidity
📁 File: contracts/L1/tiers/ITierProvider.sol

48:     uint16 public constant TIER_GUARDIAN = 1000; 
```
[48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L48)

```solidity
📁 File: contracts/L1/tiers/MainnetTierProvider.sol

26:                 cooldownWindow: 1440, //24 hours 

36:                 contestBond: 1000 ether, // TKO 
37:                 cooldownWindow: 1440, //24 hours

49:                 provingWindow: 2880, // 48 hours 

68:         if (_rand % 1000 == 0) return LibTiers.TIER_SGX_ZKVM; 
```
[26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L26), [36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L36-L37), [49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L49), [68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L68)

```solidity
📁 File: contracts/L1/tiers/TestnetTierProvider.sol

26:                 cooldownWindow: 1440, //24 hours 

36:                 contestBond: 1000 ether, // TKO 
37:                 cooldownWindow: 1440, //24 hours

49:                 provingWindow: 2880, // 48 hours 
```
[26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L26), [36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L36-L37), [49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L49)

```solidity
📁 File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

14:     uint256 internal constant MINIMUM_QUOTE_LENGTH = 1020; 
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L14)

```solidity
📁 File: contracts/automata-attestation/utils/X509DateUtils.sol

18:             if (uint8(x509Time[0]) - 48 < 5) yrs += 2000; 
19:             else yrs += 1900;

21:             yrs += (uint8(x509Time[0]) - 48) * 1000 + (uint8(x509Time[1]) - 48) * 100; 

48:         for (uint16 i = 1970; i < year; ++i) { 

64:         timestamp += uint256(hour) * 3600; // Hours in seconds 
```
[18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L18-L19), [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L21), [48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L48), [64](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L64)

```solidity
📁 File: contracts/libs/Lib4844.sol

13:     uint32 public constant FIELD_ELEMENTS_PER_BLOB = 4096; 
```
[13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L13)

</details>


---
### [NC&#x2011;59] Large or complicated code bases should implement invariant tests
Large code bases, or code with lots of inline-assembly, complicated math, or complicated interactions between multiple contracts, should implement [invariant fuzzing tests](https://medium.com/coinmonks/smart-contract-fuzzing-d9b88e0b0a05). Invariant fuzzers such as Echidna require the test writer to come up with invariants which should not be violated under any circumstances, and the fuzzer tests various inputs and function calls to ensure that the invariants always hold. Even code with 100% code coverage can still have bugs due to the order of the operations a user performs, and invariant fuzzers, with properly and extensively-written invariants, can close this testing gap significantly.


---
### [NC&#x2011;60] Layout order does not comply with best practices
This is a [best practice](https://docs.soliditylang.org/en/latest/style-guide.html#order-of-layout) that should be followed.

Inside each contract, library or interface, use the following order:

1. Type declarations
2. State variables
3. Events
4. Errors
5. Modifiers
6. Functions

<details>
<summary><i>There are 30 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoData.sol

/// @audit struct declaration `TierFee` after variable declaration
/// @audit struct declaration `TierProof` after variable declaration
/// @audit struct declaration `HookCall` after variable declaration
/// @audit struct declaration `BlockParams` after variable declaration
/// @audit struct declaration `BlockMetadata` after variable declaration
/// @audit struct declaration `Transition` after variable declaration
/// @audit struct declaration `TransitionState` after variable declaration
/// @audit struct declaration `Block` after variable declaration
/// @audit struct declaration `EthDeposit` after variable declaration
/// @audit struct declaration `SlotA` after variable declaration
/// @audit struct declaration `SlotB` after variable declaration
/// @audit struct declaration `State` after variable declaration
8: library TaikoData { 
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L8)

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

/// @audit struct declaration `Input` after variable declaration
14: contract AssignmentHook is EssentialContract, IHook { 
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L14)

```solidity
📁 File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

/// @audit modifier definition `onlyOwner` after function definition
22: contract AutomataDcapV3Attestation is IAttestation { 
```
[22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L22)

```solidity
📁 File: contracts/automata-attestation/interfaces/ISigVerifyLib.sol

/// @audit struct declaration `Certificate` after variable declaration
6: interface ISigVerifyLib { 
```
[6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L6)

```solidity
📁 File: contracts/automata-attestation/lib/EnclaveIdStruct.sol

/// @audit struct declaration `TcbLevel` after variable declaration
/// @audit struct declaration `TcbObj` after variable declaration
6: library EnclaveIdStruct { 
```
[6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/EnclaveIdStruct.sol#L6)

```solidity
📁 File: contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol

/// @audit struct declaration `EnclaveReport` after variable declaration
/// @audit struct declaration `QEAuthData` after variable declaration
/// @audit struct declaration `CertificationData` after variable declaration
/// @audit struct declaration `ECDSAQuoteV3AuthData` after variable declaration
/// @audit struct declaration `ParsedV3QuoteStruct` after variable declaration
6: library V3Struct { 
```
[6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L6)

```solidity
📁 File: contracts/automata-attestation/lib/TCBInfoStruct.sol

/// @audit struct declaration `TCBLevelObj` after variable declaration
6: library TCBInfoStruct { 
```
[6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol#L6)

```solidity
📁 File: contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol

/// @audit struct declaration `PCKCertificateField` after variable declaration
/// @audit struct declaration `PCKTCBInfo` after variable declaration
6: interface IPEMCertChainLib { 
```
[6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L6)

```solidity
📁 File: contracts/bridge/IBridge.sol

/// @audit struct declaration `ProofReceipt` after variable declaration
/// @audit struct declaration `Context` after variable declaration
8: interface IBridge { 
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L8)

```solidity
📁 File: contracts/team/TimelockTokenPool.sol

/// @audit struct declaration `Recipient` after variable declaration
25: contract TimelockTokenPool is EssentialContract { 
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L25)

```solidity
📁 File: contracts/tokenvault/BaseNFTVault.sol

/// @audit struct declaration `BridgeTransferOp` after variable declaration
9: abstract contract BaseNFTVault is BaseVault { 
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L9)

```solidity
📁 File: contracts/tokenvault/ERC20Vault.sol

/// @audit struct declaration `BridgeTransferOp` after variable declaration
18: contract ERC20Vault is BaseVault { 
```
[18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L18)

</details>


---
### [NC&#x2011;61] Libraries should be defined in separate files from their usage
The libraries below should be defined in separate files, so that it's easier for future projects to import them, and to avoid duplication later on if they need to be used elsewhere in the project


<i>There are 3 instaces of this issue:</i>

```solidity
📁 File: contracts/automata-attestation/utils/Asn1Decode.sol

12: library NodePtr { 

39:     using NodePtr for uint256; 

209:         return NodePtr.getPtr(ix, ixFirstContentByte, ixLastContentByte); 
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L12), [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L39), [209](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L209)


---
### [NC&#x2011;62] Lines are too long
Usually lines in source code are limited to 80 characters. Today's screens are much larger so it's reasonable to stretch this in some cases. Since the files will most likely reside in GitHub, and GitHub starts using a scroll bar in all cases when the length is over 164 characters, the lines below should be split when they reach that length Reference: https://docs.soliditylang.org/en/v0.8.10/style-guide.html#maximum-line-length

<details>
<summary><i>There are 6 instances of this issue:</i></summary>

```solidity
📁 File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

/// @audit 198 chars long
28:     // https://github.com/intel/SGXDataCenterAttestationPrimitives/blob/e7604e02331b3377f3766ed3653250e03af72d45/QuoteVerification/QVL/Src/AttestationLibrary/src/CertVerification/X509Constants.h#L64 

/// @audit 151 chars long
31:     // keccak256(hex"0ba9c4c0c0c86193a3fe23d6b02cda10a8bbd4e88e48b4458561a36e705525f567918e2edc88e40d860bd0cc4ee26aacc988e505a953558c453f6b0904ae7394") 
```
[28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L28), [31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L31)

```solidity
📁 File: contracts/automata-attestation/lib/PEMCertChainLib.sol

/// @audit 198 chars long
31:     // https://github.com/intel/SGXDataCenterAttestationPrimitives/blob/e7604e02331b3377f3766ed3653250e03af72d45/QuoteVerification/QVL/Src/AttestationLibrary/src/CertVerification/X509Constants.h#L64 
```
[31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L31)

```solidity
📁 File: contracts/automata-attestation/utils/BytesUtils.sol

/// @audit 156 chars long
311:         hex"00010203040506070809FFFFFFFFFFFFFF0A0B0C0D0E0F101112131415161718191A1B1C1D1E1FFFFFFFFFFFFFFFFFFFFF0A0B0C0D0E0F101112131415161718191A1B1C1D1E1F"; 
```
[311](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L311)

```solidity
📁 File: contracts/automata-attestation/utils/RsaVerify.sol

/// @audit 122 chars long
27: https://csrc.nist.gov/CSRC/media/Projects/Cryptographic-Algorithm-Validation-Program/documents/dss/186-2rsatestvectors.zip 
```
[27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L27)

```solidity
📁 File: contracts/thirdparty/optimism/rlp/RLPReader.sol

/// @audit 144 chars long
293:         // https://github.com/ethereum/solidity/blob/34dd30d71b4da730488be72ff6af7083cf2a91f6/libsolidity/codegen/YulUtilFunctions.cpp#L102-L114 
```
[293](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L293)

</details>


---
### [NC&#x2011;63] Long functions should be refactored into multiple, smaller, functions
Functions with too many lines are difficult to understand. It is recommended to refactor complex functions into multiple shorter and easier to understand functions.

<details>
<summary><i>There are 24 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

/// @audit 68 lines long
62:     function onBlockProposed( 
63:         TaikoData.Block memory _blk,
64:         TaikoData.BlockMetadata memory _meta,
65:         bytes memory _data
66:     )
```
[62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L62-L66)

```solidity
📁 File: contracts/L1/libs/LibDepositing.sol

/// @audit 52 lines long
67:     function processDeposits( 
68:         TaikoData.State storage _state,
69:         TaikoData.Config memory _config,
70:         address _feeRecipient
71:     )
```
[67](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L67-L71)

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

/// @audit 212 lines long
68:     function proposeBlock( 
69:         TaikoData.State storage _state,
70:         TaikoData.Config memory _config,
71:         IAddressResolver _resolver,
72:         bytes calldata _data,
73:         bytes calldata _txList
74:     )
```
[68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L68-L74)

```solidity
📁 File: contracts/L1/libs/LibProving.sol

/// @audit 175 lines long
91:     function proveBlock( 
92:         TaikoData.State storage _state,
93:         TaikoData.Config memory _config,
94:         IAddressResolver _resolver,
95:         TaikoData.BlockMetadata memory _meta,
96:         TaikoData.Transition memory _tran,
97:         TaikoData.TierProof memory _proof
98:     )

/// @audit 78 lines long
269:     function _createTransition( 
270:         TaikoData.State storage _state,
271:         TaikoData.Block storage _blk,
272:         TaikoData.Transition memory _tran,
273:         uint64 slot
274:     )
```
[91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L91-L98), [269](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L269-L274)

```solidity
📁 File: contracts/L1/libs/LibVerifying.sol

/// @audit 137 lines long
85:     function verifyBlocks( 
86:         TaikoData.State storage _state,
87:         TaikoData.Config memory _config,
88:         IAddressResolver _resolver,
89:         uint64 _maxBlocksToVerify
90:     )
```
[85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L85-L90)

```solidity
📁 File: contracts/L2/TaikoL2.sol

/// @audit 51 lines long
107:     function anchor( 
108:         bytes32 _l1BlockHash,
109:         bytes32 _l1StateRoot,
110:         uint64 _l1BlockId,
111:         uint32 _parentGasUsed
112:     )
```
[107](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L107-L112)

```solidity
📁 File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

/// @audit 53 lines long
248:     function _verifyCertChain(IPEMCertChainLib.ECSha256Certificate[] memory certs) 

/// @audit 121 lines long
364:     function _verifyParsedQuote(V3Struct.ParsedV3QuoteStruct memory v3quote) 
```
[248](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L248), [364](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L364)

```solidity
📁 File: contracts/automata-attestation/lib/PEMCertChainLib.sol

/// @audit 140 lines long
74:     function decodeCert( 
75:         bytes memory der,
76:         bool isPckCert
77:     )

/// @audit 70 lines long
269:     function _findPckTcbInfo( 
270:         bytes memory der,
271:         uint256 tbsPtr,
272:         uint256 tbsParentPtr
273:     )
```
[74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L74-L77), [269](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L269-L273)

```solidity
📁 File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

/// @audit 69 lines long
62:     function validateParsedInput(V3Struct.ParsedV3QuoteStruct memory v3Quote) 
```
[62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L62)

```solidity
📁 File: contracts/automata-attestation/utils/RsaVerify.sol

/// @audit 138 lines long
43:     function pkcs1Sha256( 
44:         bytes32 _sha256,
45:         bytes memory _s,
46:         bytes memory _e,
47:         bytes memory _m
48:     )

/// @audit 85 lines long
212:     function pkcs1Sha1( 
213:         bytes20 _sha1,
214:         bytes memory _s,
215:         bytes memory _e,
216:         bytes memory _m
217:     )
```
[43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L43-L48), [212](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L212-L217)

```solidity
📁 File: contracts/automata-attestation/utils/SHA1.sol

/// @audit 183 lines long
11:     function sha1(bytes memory data) internal pure returns (bytes20 ret) { 
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SHA1.sol#L11)

```solidity
📁 File: contracts/bridge/Bridge.sol

/// @audit 59 lines long
155:     function recallMessage( 
156:         Message calldata _message,
157:         bytes calldata _proof
158:     )

/// @audit 90 lines long
217:     function processMessage( 
218:         Message calldata _message,
219:         bytes calldata _proof
220:     )
```
[155](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L155-L158), [217](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L217-L220)

```solidity
📁 File: contracts/signal/SignalService.sol

/// @audit 51 lines long
83:     function proveSignalReceived( 
84:         uint64 _chainId,
85:         address _app,
86:         bytes32 _signal,
87:         bytes calldata _proof
88:     )
```
[83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L83-L88)

```solidity
📁 File: contracts/thirdparty/optimism/Bytes.sol

/// @audit 69 lines long
15:     function slice( 
16:         bytes memory _bytes,
17:         uint256 _start,
18:         uint256 _length
19:     )
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L15-L19)

```solidity
📁 File: contracts/thirdparty/optimism/rlp/RLPReader.sol

/// @audit 126 lines long
144:     function _decodeLength(RLPItem memory _in) 
```
[144](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L144)

```solidity
📁 File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

/// @audit 131 lines long
68:     function get( 
69:         bytes memory _key,
70:         bytes[] memory _proof,
71:         bytes32 _root
72:     )
```
[68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L68-L72)

```solidity
📁 File: contracts/thirdparty/solmate/LibFixedPointMath.sol

/// @audit 68 lines long
13:     function exp(int256 x) internal pure returns (int256 r) { 
```
[13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L13)

```solidity
📁 File: contracts/tokenvault/ERC1155Vault.sol

/// @audit 51 lines long
39:     function sendToken(BridgeTransferOp memory _op) 
```
[39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L39)

```solidity
📁 File: contracts/tokenvault/ERC20Vault.sol

/// @audit 52 lines long
148:     function changeBridgedToken( 
149:         CanonicalERC20 calldata _ctoken,
150:         address _btokenNew
151:     )
```
[148](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L148-L151)

</details>


---
### [NC&#x2011;64] Make use of Solidity's `using` keyword
The `using`-`for` [syntax](https://docs.soliditylang.org/en/latest/contracts.html#using-for) is the more common way of calling library functions.

<details>
<summary><i>There are 40 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoL1.sol

/// @audit LibVerifying
51:         LibVerifying.init(state, getConfig(), _genesisBlockHash); 

/// @audit LibProposing
67:         (meta_, deposits_) = LibProposing.proposeBlock(state, config, this, _params, _txList); 

/// @audit LibVerifying
70:             LibVerifying.verifyBlocks(state, config, this, config.maxBlocksToVerifyPerProposal); 

/// @audit LibProving
94:         uint8 maxBlocksToVerify = LibProving.proveBlock(state, config, this, meta, tran, proof); 

/// @audit LibVerifying
96:         LibVerifying.verifyBlocks(state, config, this, maxBlocksToVerify); 

/// @audit LibVerifying
106:         LibVerifying.verifyBlocks(state, getConfig(), this, _maxBlocksToVerify); 

/// @audit LibProving
113:         LibProving.pauseProving(state, _pause); 

/// @audit LibDepositing
120:         LibDepositing.depositEtherToL2(state, getConfig(), this, _recipient); 

/// @audit LibDepositing
133:         return LibDepositing.canDepositEthToL2(state, getConfig(), _amount); 

/// @audit LibProposing
138:         return LibProposing.isBlobReusable(state, getConfig(), _blobHash); 

/// @audit LibUtils
151:         (blk_, slot) = LibUtils.getBlock(state, getConfig(), _blockId); 

/// @audit LibUtils
170:         return LibUtils.getTransition(state, getConfig(), _blockId, _parentHash); 

/// @audit TaikoData
191:         return TaikoData.Config({ 
192:             chainId: 167_008,
193:             // Assume the block time is 3s, the protocol will allow ~1 month of
194:             // new blocks without any verification.
195:             blockMaxProposals: 864_000,
196:             blockRingBufferSize: 864_100,
197:             // Can be overridden by the tier config.
198:             maxBlocksToVerifyPerProposal: 10,
199:             blockMaxGasLimit: 15_000_000,
200:             // Each go-ethereum transaction has a size limit of 128KB,
201:             // and right now txList is still saved in calldata, so we set it
202:             // to 120KB.
203:             blockMaxTxListBytes: 120_000,
204:             blobExpiry: 24 hours,
205:             blobAllowedForDA: false,
206:             blobReuseEnabled: false,
207:             livenessBond: 250e18, // 250 Taiko token
208:             // ETH deposit related.
209:             ethDepositRingBufferSize: 1024,
210:             ethDepositMinCountPerBlock: 8,
211:             ethDepositMaxCountPerBlock: 32,
212:             ethDepositMinAmount: 1 ether,
213:             ethDepositMaxAmount: 10_000 ether,
214:             ethDepositGas: 21_000,
215:             ethDepositMaxFee: 1 ether / 10,
216:             blockSyncThreshold: 16
217:         });
```
[51](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L51), [67](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L67), [70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L70), [94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L94), [96](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L96), [106](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L106), [113](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L113), [120](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L120), [133](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L133), [138](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L138), [151](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L151), [170](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L170), [191](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L191-L217)

```solidity
📁 File: contracts/L1/libs/LibDepositing.sol

/// @audit TaikoData
51:             TaikoData.EthDeposit({ 
52:                 recipient: recipient_,
53:                 amount: uint96(msg.value),
54:                 id: _state.slotA.numEthDeposits
55:             })

/// @audit TaikoData
88:                 deposits_[i] = TaikoData.EthDeposit({ 
89:                     recipient: address(uint160(data >> 96)),
90:                     amount: uint96(data),
91:                     id: j
92:                 });
```
[51](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L51-L55), [88](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L88-L92)

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

/// @audit LibDepositing
114:         deposits_ = LibDepositing.processDeposits(_state, _config, params.coinbase); 

/// @audit TaikoData
121:             meta_ = TaikoData.BlockMetadata({ 
122:                 l1Hash: blockhash(block.number - 1),
123:                 difficulty: 0, // to be initialized below
124:                 blobHash: 0, // to be initialized below
125:                 extraData: params.extraData,
126:                 depositsHash: keccak256(abi.encode(deposits_)),
127:                 coinbase: params.coinbase,
128:                 id: b.numBlocks,
129:                 gasLimit: _config.blockMaxGasLimit,
130:                 timestamp: uint64(block.timestamp),
131:                 l1Height: uint64(block.number - 1),
132:                 txListByteOffset: 0, // to be initialized below
133:                 txListByteSize: 0, // to be initialized below
134:                 minTier: 0, // to be initialized below
135:                 blobUsed: _txList.length == 0,
136:                 parentMetaHash: parentMetaHash
137:             });

/// @audit LibAddress
182:             if (!LibAddress.isSenderEOA()) revert L1_PROPOSER_NOT_EOA(); 

/// @audit TaikoData
212:         TaikoData.Block memory blk = TaikoData.Block({ 
213:             metaHash: keccak256(abi.encode(meta_)),
214:             // Safeguard the liveness bond to ensure its preservation,
215:             // particularly in scenarios where it might be altered after the
216:             // block's proposal but before it has been proven or verified.
217:             livenessBond: _config.livenessBond,
218:             blockId: b.numBlocks,
219:             proposedAt: meta_.timestamp,
220:             proposedIn: uint64(block.number),
221:             // For a new block, the next transition ID is always 1, not 0.
222:             nextTransitionId: 1,
223:             // For unverified block, its verifiedTransitionId is always 0.
224:             verifiedTransitionId: 0,
225:             assignedProver: params.assignedProver
226:         });
```
[114](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L114), [121](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L121-L137), [182](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L182), [212](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L212-L226)

```solidity
📁 File: contracts/L1/libs/LibProving.sol

/// @audit LibUtils
278:         tid_ = LibUtils.getTransitionId(_state, _blk, slot, _tran.parentHash); 
```
[278](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L278)

```solidity
📁 File: contracts/L1/libs/LibVerifying.sol

/// @audit LibUtils
133:                 tid = LibUtils.getTransitionId(_state, blk, slot, blockHash); 
```
[133](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L133)

```solidity
📁 File: contracts/L2/Lib1559Math.sol

/// @audit LibFixedPointMath
45:         return uint256(LibFixedPointMath.exp(int256(input))); 
```
[45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L45)

```solidity
📁 File: contracts/L2/TaikoL2.sol

/// @audit Lib1559Math
290:             basefee_ = Lib1559Math.basefee( 
291:                 gasExcess_, uint256(_config.basefeeAdjustmentQuotient) * _config.gasTargetPerL1Block
292:             );
```
[290](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L290-L292)

```solidity
📁 File: contracts/bridge/Bridge.sol

/// @audit ExcessivelySafeCall
497:             (success_,) = ExcessivelySafeCall.excessivelySafeCall( 
498:                 _message.to,
499:                 _gasLimit,
500:                 _message.value,
501:                 64, // return max 64 bytes
502:                 _message.data
503:             );
```
[497](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L497-L503)

```solidity
📁 File: contracts/libs/LibAddress.sol

/// @audit ExcessivelySafeCall
27:         (bool success,) = ExcessivelySafeCall.excessivelySafeCall( 
28:             _to,
29:             _gasLimit,
30:             _amount,
31:             64, // return max 64 bytes
32:             ""
33:         );

/// @audit Address
54:         if (!Address.isContract(_addr)) return false; 

/// @audit Address
70:         if (Address.isContract(_addr)) { 

/// @audit ECDSA
73:             return ECDSA.recover(_hash, _sig) == _addr; 
```
[27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L27-L33), [54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L54), [70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L70), [73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L73)

```solidity
📁 File: contracts/libs/LibTrieProof.sol

/// @audit SecureMerkleTrie
48:                 SecureMerkleTrie.get(abi.encodePacked(_addr), _accountProof, _rootHash); 

/// @audit RLPReader
52:             RLPReader.RLPItem[] memory accountState = RLPReader.readList(rlpAccount); 

/// @audit RLPReader
55:                 bytes32(RLPReader.readBytes(accountState[_ACCOUNT_FIELD_INDEX_STORAGE_HASH])); 

/// @audit SecureMerkleTrie
60:         bool verified = SecureMerkleTrie.verifyInclusionProof( 
/// @audit RLPWriter
61:             bytes.concat(_slot), RLPWriter.writeUint(uint256(_value)), _storageProof, storageRoot_
62:         );
```
[48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L48), [52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L52), [55](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L55), [60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L60-L62)

```solidity
📁 File: contracts/signal/SignalService.sol

/// @audit LibTrieProof
221:         return LibTrieProof.verifyMerkleProof( 
222:             _hop.rootHash,
223:             _signalService,
224:             getSignalSlot(_chainId, _app, _signal),
225:             _value,
226:             _hop.accountProof,
227:             _hop.storageProof
228:         );
```
[221](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L221-L228)

```solidity
📁 File: contracts/tokenvault/BridgedERC20.sol

/// @audit LibBridgedToken
65:         LibBridgedToken.validateInputs(_srcToken, _srcChainId, _symbol, _name); 

/// @audit LibBridgedToken
97:         return LibBridgedToken.buildName(super.name(), srcChainId); 

/// @audit LibBridgedToken
108:         return LibBridgedToken.buildSymbol(super.symbol()); 
```
[65](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L65), [97](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L97), [108](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L108)

```solidity
📁 File: contracts/tokenvault/BridgedERC721.sol

/// @audit LibBridgedToken
43:         LibBridgedToken.validateInputs(_srcToken, _srcChainId, _symbol, _name); 

/// @audit LibBridgedToken
88:         return LibBridgedToken.buildName(super.name(), srcChainId); 

/// @audit LibBridgedToken
94:         return LibBridgedToken.buildSymbol(super.symbol()); 
```
[43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L43), [88](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L88), [94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L94)

</details>


---
### [NC&#x2011;65] Minting to the zero address should be avoided
Minting tokens to the zero address in Solidity is a potential pitfall. The zero address (0x0) is commonly used as a default value and sending tokens there effectively burns them, leading to unintended token loss. To prevent this, include a check in the minting function to ensure the target address is not zero. Using OpenZeppelin's Address library with the requireNonZero function simplifies this check and enhances security.

<details>
<summary><i>There are 9 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoToken.sol

105:     function _mint( 
106:         address _to,
107:         uint256 _amount
108:     )
109:         internal
110:         override(ERC20Upgradeable, ERC20VotesUpgradeable)
111:     {
112:         super._mint(_to, _amount);
113:     }
```
[105](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L105-L113)

```solidity
📁 File: contracts/tokenvault/BridgedERC1155.sol

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
76:         _mint(_to, _tokenId, _amount, "");
77:     }

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
93:         _mintBatch(_to, _tokenIds, _amounts, "");
94:     }
```
[66](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L66-L77), [83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L83-L94)

```solidity
📁 File: contracts/tokenvault/BridgedERC20.sol

129:     function _mintToken(address _account, uint256 _amount) internal override { 
130:         _mint(_account, _amount);
131:     }

163:     function _mint( 
164:         address _to,
165:         uint256 _amount
166:     )
167:         internal
168:         override(ERC20Upgradeable, ERC20VotesUpgradeable)
169:     {
170:         super._mint(_to, _amount);
171:     }
```
[129](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L129-L131), [163](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L163-L171)

```solidity
📁 File: contracts/tokenvault/BridgedERC20Base.sol

57:     function mint(address _account, uint256 _amount) public nonReentrant whenNotPaused { 
58:         // mint is disabled while migrating outbound.
59:         if (_isMigratingOut()) revert BB_MINT_DISALLOWED();
60: 
61:         if (msg.sender == migratingAddress) {
62:             // Inbound migration
63:             emit MigratedTo(migratingAddress, _account, _amount);
64:         } else if (msg.sender != resolve("erc20_vault", true)) {
65:             // Bridging from vault
66:             revert BB_PERMISSION_DENIED();
67:         }
68: 
69:         _mintToken(_account, _amount);
70:     }

97:     function _mintToken(address _account, uint256 _amount) internal virtual; 
```
[57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L57-L70), [97](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L97)

```solidity
📁 File: contracts/tokenvault/BridgedERC721.sol

54:     function mint( 
55:         address _account,
56:         uint256 _tokenId
57:     )
58:         public
59:         nonReentrant
60:         whenNotPaused
61:         onlyFromNamed("erc721_vault")
62:     {
63:         _safeMint(_account, _tokenId);
64:     }
```
[54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L54-L64)

```solidity
📁 File: contracts/tokenvault/adapters/USDCAdapter.sol

43:     function _mintToken(address _account, uint256 _amount) internal override { 
44:         usdc.mint(_account, _amount);
45:     }
```
[43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L43-L45)

</details>


---
### [NC&#x2011;66] Missing checks for `address(0x0)` in the constructor
<details>
<summary><i>There are 3 instances of this issue:</i></summary>

```solidity
📁 File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

/// @audit sigVerifyLibAddr missing zero address validation
/// @audit pemCertLibAddr missing zero address validation
54:     constructor(address sigVerifyLibAddr, address pemCertLibAddr) { 
```
[54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L54)

```solidity
📁 File: contracts/automata-attestation/utils/SigVerifyLib.sol

/// @audit es256Verifier missing zero address validation
20:     constructor(address es256Verifier) { 
```
[20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L20)

</details>


---
### [NC&#x2011;67] Missing checks for uint state variable assignments
<details>
<summary><i>There are 7 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/provers/Guardians.sol

94:         minGuardians = _minGuardians; 
```
[94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L94)

```solidity
📁 File: contracts/L2/TaikoL2EIP1559Configurable.sol

37:         gasExcess = _newGasExcess; 
```
[37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L37)

```solidity
📁 File: contracts/common/EssentialContract.sol

125:             __reentry = _reentry; 
```
[125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L125)

```solidity
📁 File: contracts/signal/SignalService.sol

248:             topBlockId[_chainId][_kind] = _blockId; 
```
[248](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L248)

```solidity
📁 File: contracts/team/airdrop/ERC20Airdrop2.sol

83:         claimedAmount[user] += amount; 
```
[83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L83)

```solidity
📁 File: contracts/team/airdrop/MerkleClaimable.sol

91:         claimStart = _claimStart; 
92:         claimEnd = _claimEnd;
```
[91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L91-L92)

</details>


---
### [NC&#x2011;68] Multiple mappings with same keys can be combined into a single struct mapping for readability
Well-organized data structures make code reviews easier, which may lead to fewer bugs. Consider combining related mappings into mappings to structs, so it's clear what data is related

<details>
<summary><i>There are 10 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoData.sol

183:         mapping(uint64 blockId => mapping(bytes32 parentHash => uint32 transitionId)) transitionIds; 

190:         mapping(uint256 depositId_mod_ethDepositRingBufferSize => uint256 depositAmount) ethDeposits; 
```
[183](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L183), [190](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L190)

```solidity
📁 File: contracts/L1/provers/Guardians.sol

16:     mapping(address guardian => uint256 id) public guardianIds; 

19:     mapping(uint32 version => mapping(bytes32 hash => uint256 approvalBits)) internal _approvals; 
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L16), [19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L19)

```solidity
📁 File: contracts/team/airdrop/ERC20Airdrop2.sol

22:     mapping(address addr => uint256 amountClaimed) public claimedAmount; 

25:     mapping(address addr => uint256 amountWithdrawn) public withdrawnAmount; 
```
[22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L22), [25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L25)

```solidity
📁 File: contracts/tokenvault/BaseNFTVault.sol

59:     mapping(uint256 chainId => mapping(address ctoken => address btoken)) public canonicalToBridged; 
```
[59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L59)

```solidity
📁 File: contracts/tokenvault/ERC20Vault.sol

49:     mapping(uint256 chainId => mapping(address ctoken => address btoken)) public canonicalToBridged; 
```
[49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L49)

</details>


---
### [NC&#x2011;69] Multiple type casts create complexity within the code
To ensure reliable and precise data handling in Solidity contracts, developers should avoid double type casting. Multiple type casts can lead to unintended consequences, such as truncation, rounding errors, or loss of precision. This compromises the contract's functionality and readability, making debugging more challenging. Instead, its crucial to use appropriate data types and minimize unnecessary type casting for a more dependable and robust contract execution.

<details>
<summary><i>There are 14 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/libs/LibDepositing.sol

/// @audit address(uint160)
89:                     recipient: address(uint160(data >> 96)), 

/// @audit uint256(uint160)
151:         return (uint256(uint160(_addr)) << 96) | _amount; 
```
[89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L89), [151](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L151)

```solidity
📁 File: contracts/automata-attestation/lib/PEMCertChainLib.sol

/// @audit uint16(bytes2)
359:                 ? uint16(bytes2(svnValueBytes)) / 256 
/// @audit uint16(bytes2)
360:                 : uint16(bytes2(svnValueBytes));
```
[359](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L359-L360)

```solidity
📁 File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

/// @audit uint256(uint8(bytes1))
/// @audit uint8(bytes1)
154:             uint256 digits = uint256(uint8(bytes1(encoded[i]))); 
```
[154](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L154)

```solidity
📁 File: contracts/automata-attestation/utils/BytesUtils.sol

/// @audit uint256(uint8)
336:             decoded = uint8(BASE32_HEX_TABLE[uint256(uint8(char)) - 0x30]); 
```
[336](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L336)

```solidity
📁 File: contracts/automata-attestation/utils/SigVerifyLib.sol

/// @audit uint256(bytes32)
126:         uint256 r = uint256(bytes32(signature.substring(0, 32))); 

/// @audit uint256(bytes32)
132:         uint256 gx = uint256(bytes32(publicKey.substring(0, 32))); 
```
[126](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L126), [132](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L132)

```solidity
📁 File: contracts/bridge/Bridge.sol

/// @audit bytes32(uint256)
457:         return _msgHash ^ bytes32(uint256(Status.FAILED)); 

/// @audit address(uint160)
533:             _storeContext(bytes32(PLACEHOLDER), address(uint160(PLACEHOLDER)), uint64(PLACEHOLDER)); 
```
[457](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L457), [533](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L533)

```solidity
📁 File: contracts/thirdparty/optimism/rlp/RLPWriter.sol

/// @audit bytes1(uint8)
47:                 out_[i] = bytes1(uint8((_len / (256 ** (lenLen - i))) % 256)); 
```
[47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L47)

```solidity
📁 File: contracts/verifiers/SgxVerifier.sol

/// @audit address(bytes20)
133:         _address[0] = address(bytes20(_attestation.localEnclaveReport.reportData)); 

/// @audit uint32(bytes4)
154:         uint32 id = uint32(bytes4(Bytes.slice(_proof.data, 0, 4))); 
```
[133](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L133), [154](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L154)

</details>


---
### [NC&#x2011;70] Named imports of parent contracts are missing
<details>
<summary><i>There are 36 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoL1.sol

/// @audit EssentialContract ,ITaikoL1 ,TaikoEvents ,TaikoErrors 
22: contract TaikoL1 is EssentialContract, ITaikoL1, TaikoEvents, TaikoErrors { 
```
[22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L22)

```solidity
📁 File: contracts/L1/TaikoToken.sol

/// @audit EssentialContract ,ERC20SnapshotUpgradeable ,ERC20VotesUpgradeable 
15: contract TaikoToken is EssentialContract, ERC20SnapshotUpgradeable, ERC20VotesUpgradeable { 
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L15)

```solidity
📁 File: contracts/L1/gov/TaikoGovernor.sol

/// @audit EssentialContract ,GovernorCompatibilityBravoUpgradeable ,GovernorVotesUpgradeable ,GovernorVotesQuorumFractionUpgradeable ,GovernorTimelockControlUpgradeable 
16: contract TaikoGovernor is 
17:     EssentialContract,
18:     GovernorCompatibilityBravoUpgradeable,
19:     GovernorVotesUpgradeable,
20:     GovernorVotesQuorumFractionUpgradeable,
21:     GovernorTimelockControlUpgradeable
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L16-L21)

```solidity
📁 File: contracts/L1/gov/TaikoTimelockController.sol

/// @audit EssentialContract ,TimelockControllerUpgradeable 
9: contract TaikoTimelockController is EssentialContract, TimelockControllerUpgradeable { 
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L9)

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

/// @audit EssentialContract ,IHook 
14: contract AssignmentHook is EssentialContract, IHook { 
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L14)

```solidity
📁 File: contracts/L1/provers/GuardianProver.sol

/// @audit Guardians 
10: contract GuardianProver is Guardians { 
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L10)

```solidity
📁 File: contracts/L1/provers/Guardians.sol

/// @audit EssentialContract 
9: abstract contract Guardians is EssentialContract { 
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L9)

```solidity
📁 File: contracts/L1/tiers/DevnetTierProvider.sol

/// @audit EssentialContract ,ITierProvider 
10: contract DevnetTierProvider is EssentialContract, ITierProvider { 
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L10)

```solidity
📁 File: contracts/L1/tiers/MainnetTierProvider.sol

/// @audit EssentialContract ,ITierProvider 
10: contract MainnetTierProvider is EssentialContract, ITierProvider { 
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L10)

```solidity
📁 File: contracts/L1/tiers/TestnetTierProvider.sol

/// @audit EssentialContract ,ITierProvider 
10: contract TestnetTierProvider is EssentialContract, ITierProvider { 
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L10)

```solidity
📁 File: contracts/L2/CrossChainOwned.sol

/// @audit EssentialContract ,IMessageInvocable 
14: abstract contract CrossChainOwned is EssentialContract, IMessageInvocable { 
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L14)

```solidity
📁 File: contracts/L2/TaikoL2.sol

/// @audit CrossChainOwned 
21: contract TaikoL2 is CrossChainOwned { 
```
[21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L21)

```solidity
📁 File: contracts/L2/TaikoL2EIP1559Configurable.sol

/// @audit TaikoL2 
9: contract TaikoL2EIP1559Configurable is TaikoL2 { 
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L9)

```solidity
📁 File: contracts/automata-attestation/utils/SigVerifyLib.sol

/// @audit ISigVerifyLib 
15: contract SigVerifyLib is ISigVerifyLib { 
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L15)

```solidity
📁 File: contracts/bridge/Bridge.sol

/// @audit EssentialContract ,IBridge 
16: contract Bridge is EssentialContract, IBridge { 
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L16)

```solidity
📁 File: contracts/common/AddressManager.sol

/// @audit EssentialContract ,IAddressManager 
10: contract AddressManager is EssentialContract, IAddressManager { 
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L10)

```solidity
📁 File: contracts/common/AddressResolver.sol

/// @audit IAddressResolver ,Initializable 
11: abstract contract AddressResolver is IAddressResolver, Initializable { 
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L11)

```solidity
📁 File: contracts/common/EssentialContract.sol

/// @audit UUPSUpgradeable ,Ownable2StepUpgradeable ,AddressResolver 
10: abstract contract EssentialContract is UUPSUpgradeable, Ownable2StepUpgradeable, AddressResolver { 
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L10)

```solidity
📁 File: contracts/signal/SignalService.sol

/// @audit EssentialContract ,ISignalService 
14: contract SignalService is EssentialContract, ISignalService { 
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L14)

```solidity
📁 File: contracts/team/TimelockTokenPool.sol

/// @audit EssentialContract 
25: contract TimelockTokenPool is EssentialContract { 
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L25)

```solidity
📁 File: contracts/team/airdrop/ERC20Airdrop.sol

/// @audit MerkleClaimable 
11: contract ERC20Airdrop is MerkleClaimable { 
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L11)

```solidity
📁 File: contracts/team/airdrop/ERC20Airdrop2.sol

/// @audit MerkleClaimable 
12: contract ERC20Airdrop2 is MerkleClaimable { 
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L12)

```solidity
📁 File: contracts/team/airdrop/ERC721Airdrop.sol

/// @audit MerkleClaimable 
9: contract ERC721Airdrop is MerkleClaimable { 
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L9)

```solidity
📁 File: contracts/team/airdrop/MerkleClaimable.sol

/// @audit EssentialContract 
10: abstract contract MerkleClaimable is EssentialContract { 
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L10)

```solidity
📁 File: contracts/tokenvault/BaseNFTVault.sol

/// @audit BaseVault 
9: abstract contract BaseNFTVault is BaseVault { 
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L9)

```solidity
📁 File: contracts/tokenvault/BaseVault.sol

/// @audit EssentialContract ,IRecallableSender ,IMessageInvocable ,IERC165Upgradeable 
12: abstract contract BaseVault is 
13:     EssentialContract,
14:     IRecallableSender,
15:     IMessageInvocable,
16:     IERC165Upgradeable
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L12-L16)

```solidity
📁 File: contracts/tokenvault/BridgedERC1155.sol

/// @audit EssentialContract ,IERC1155MetadataURIUpgradeable ,ERC1155Upgradeable 
14: contract BridgedERC1155 is EssentialContract, IERC1155MetadataURIUpgradeable, ERC1155Upgradeable { 
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L14)

```solidity
📁 File: contracts/tokenvault/BridgedERC20.sol

/// @audit BridgedERC20Base ,IERC20MetadataUpgradeable ,ERC20SnapshotUpgradeable ,ERC20VotesUpgradeable 
15: contract BridgedERC20 is 
16:     BridgedERC20Base,
17:     IERC20MetadataUpgradeable,
18:     ERC20SnapshotUpgradeable,
19:     ERC20VotesUpgradeable
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L15-L19)

```solidity
📁 File: contracts/tokenvault/BridgedERC20Base.sol

/// @audit EssentialContract ,IBridgedERC20 
9: abstract contract BridgedERC20Base is EssentialContract, IBridgedERC20 { 
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L9)

```solidity
📁 File: contracts/tokenvault/BridgedERC721.sol

/// @audit EssentialContract ,ERC721Upgradeable 
12: contract BridgedERC721 is EssentialContract, ERC721Upgradeable { 
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L12)

```solidity
📁 File: contracts/tokenvault/ERC1155Vault.sol

/// @audit BaseNFTVault ,ERC1155ReceiverUpgradeable 
29: contract ERC1155Vault is BaseNFTVault, ERC1155ReceiverUpgradeable { 
```
[29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L29)

```solidity
📁 File: contracts/tokenvault/ERC20Vault.sol

/// @audit BaseVault 
18: contract ERC20Vault is BaseVault { 
```
[18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L18)

```solidity
📁 File: contracts/tokenvault/ERC721Vault.sol

/// @audit BaseNFTVault ,IERC721Receiver 
16: contract ERC721Vault is BaseNFTVault, IERC721Receiver { 
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L16)

```solidity
📁 File: contracts/tokenvault/adapters/USDCAdapter.sol

/// @audit BridgedERC20Base 
28: contract USDCAdapter is BridgedERC20Base { 
```
[28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L28)

```solidity
📁 File: contracts/verifiers/GuardianVerifier.sol

/// @audit EssentialContract ,IVerifier 
10: contract GuardianVerifier is EssentialContract, IVerifier { 
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L10)

```solidity
📁 File: contracts/verifiers/SgxVerifier.sol

/// @audit EssentialContract ,IVerifier 
19: contract SgxVerifier is EssentialContract, IVerifier { 
```
[19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L19)

</details>


---
### [NC&#x2011;71] Names of private/internal state variables should be prefixed with an underscore
According to the Solidity Style Guide, Names of private/internal state variables should be prefixed with an <a href="https://docs.soliditylang.org/en/latest/style-guide.html#underscore-prefix-for-non-external-functions-and-variables">underscore</a>.


<i>There is one instance of this issue:</i>

```solidity
📁 File: contracts/automata-attestation/utils/SigVerifyLib.sol

/// @audit _ES256VERIFIER
18:     address private ES256VERIFIER; 
```
[18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L18)


---
### [NC&#x2011;72] Names of structs, events, enums and errors should use CapWords style
According to the Solidity [style guide](https://docs.soliditylang.org/en/latest/style-guide.html#event-names) names of structs, events and errors should be in `CapWords style` (CamelCase).

<details>
<summary><i>There are 12 instances of this issue:</i></summary>

```solidity
📁 File: contracts/automata-attestation/lib/PEMCertChainLib.sol

/// @audit PCKTCBFlags
34:     struct PCKTCBFlags { 
35:         bool fmspcFound;
36:         bool pceidFound;
37:         bool tcbFound;
38:     }
```
[34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L34-L38)

```solidity
📁 File: contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol

/// @audit QEAuthData
33:     struct QEAuthData { 
34:         uint16 parsedDataSize;
35:         bytes data;
36:     }

/// @audit ECDSAQuoteV3AuthData
47:     struct ECDSAQuoteV3AuthData { 
48:         bytes ecdsa256BitSignature; // 64 bytes
49:         bytes ecdsaAttestationKey; // 64 bytes
50:         EnclaveReport pckSignedQeReport; // 384 bytes
51:         bytes qeReportSignature; // 64 bytes
52:         QEAuthData qeAuthData;
53:         CertificationData certification;
54:     }
```
[33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L33-L36), [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L47-L54)

```solidity
📁 File: contracts/automata-attestation/lib/TCBInfoStruct.sol

/// @audit TCBInfo
7:     struct TCBInfo { 
8:         string pceid;
9:         string fmspc;
10:         TCBLevelObj[] tcbLevels;
11:     }

/// @audit TCBLevelObj
13:     struct TCBLevelObj { 
14:         uint256 pcesvn;
15:         uint8[] sgxTcbCompSvnArr;
16:         TCBStatus status;
17:     }

/// @audit TCBStatus
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
[7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol#L7-L11), [13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol#L13-L17), [19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol#L19-L28)

```solidity
📁 File: contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol

/// @audit ECSha256Certificate
7:     struct ECSha256Certificate { 
8:         uint256 notBefore;
9:         uint256 notAfter;
10:         bytes serialNumber;
11:         bytes tbsCertificate;
12:         bytes pubKey;
13:         bytes signature;
14:         bool isPck;
15:         PCKCertificateField pck;
16:     }

/// @audit PCKCertificateField
18:     struct PCKCertificateField { 
19:         string commonName;
20:         string issuerName;
21:         PCKTCBInfo sgxExtension;
22:     }

/// @audit PCKTCBInfo
24:     struct PCKTCBInfo { 
25:         string pceid;
26:         string fmspc;
27:         uint256 pcesvn;
28:         uint256[] sgxTcbCompSvnArr;
29:     }

/// @audit CRL
31:     enum CRL { 
32:         PCK,
33:         ROOT
34:     }
```
[7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L7-L16), [18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L18-L22), [24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L24-L29), [31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L31-L34)

```solidity
📁 File: contracts/thirdparty/optimism/rlp/RLPReader.sol

/// @audit RLPItemType
16:     enum RLPItemType { 
17:         DATA_ITEM,
18:         LIST_ITEM
19:     }

/// @audit RLPItem
24:     struct RLPItem { 
25:         uint256 length;
26:         MemoryPointer ptr;
27:     }
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L16-L19), [24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L24-L27)

</details>


---
### [NC&#x2011;73] NatSpec: Contract declarations should have `@author` tags
<details>
<summary><i>There are 40 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/ITaikoL1.sol

7: /// @custom:security-contact security@taiko.xyz 
8: interface ITaikoL1 {
9:     /// @notice Proposes a Taiko L2 block.
```
[7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/ITaikoL1.sol#L7-L9)

```solidity
📁 File: contracts/L1/TaikoData.sol

7: /// @custom:security-contact security@taiko.xyz 
8: library TaikoData {
9:     /// @dev Struct holding Taiko configuration parameters. See {TaikoConfig}.
```
[7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L7-L9)

```solidity
📁 File: contracts/L1/TaikoErrors.sol

10: /// @custom:security-contact security@taiko.xyz 
11: abstract contract TaikoErrors {
12:     error L1_ALREADY_CONTESTED();
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoErrors.sol#L10-L12)

```solidity
📁 File: contracts/L1/TaikoEvents.sol

12: /// @custom:security-contact security@taiko.xyz 
13: abstract contract TaikoEvents {
14:     /// @dev Emitted when a block is proposed.
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L12-L14)

```solidity
📁 File: contracts/L1/TaikoL1.sol

21: /// @custom:security-contact security@taiko.xyz 
22: contract TaikoL1 is EssentialContract, ITaikoL1, TaikoEvents, TaikoErrors {
23:     /// @notice The TaikoL1 state.
```
[21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L21-L23)

```solidity
📁 File: contracts/L1/TaikoToken.sol

14: /// @custom:security-contact security@taiko.xyz 
15: contract TaikoToken is EssentialContract, ERC20SnapshotUpgradeable, ERC20VotesUpgradeable {
16:     uint256[50] private __gap;
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L14-L16)

```solidity
📁 File: contracts/L1/gov/TaikoGovernor.sol

15: /// @custom:security-contact security@taiko.xyz 
16: contract TaikoGovernor is
17:     EssentialContract,
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L15-L17)

```solidity
📁 File: contracts/L1/gov/TaikoTimelockController.sol

8: /// @custom:security-contact security@taiko.xyz 
9: contract TaikoTimelockController is EssentialContract, TimelockControllerUpgradeable {
10:     uint256[50] private __gap;
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L8-L10)

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

13: /// @custom:security-contact security@taiko.xyz 
14: contract AssignmentHook is EssentialContract, IHook {
15:     using LibAddress for address;
```
[13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L13-L15)

```solidity
📁 File: contracts/L1/hooks/IHook.sol

7: /// @custom:security-contact security@taiko.xyz 
8: interface IHook {
9:     /// @notice Called when a block is proposed.
```
[7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/IHook.sol#L7-L9)

```solidity
📁 File: contracts/L1/libs/LibDepositing.sol

11: /// @custom:security-contact security@taiko.xyz 
12: library LibDepositing {
13:     using LibAddress for address;
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L11-L13)

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

14: /// @custom:security-contact security@taiko.xyz 
15: library LibProposing {
16:     using LibAddress for address;
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L14-L16)

```solidity
📁 File: contracts/L1/libs/LibProving.sol

15: /// @custom:security-contact security@taiko.xyz 
16: library LibProving {
17:     using LibMath for uint256;
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L15-L17)

```solidity
📁 File: contracts/L1/libs/LibUtils.sol

8: /// @custom:security-contact security@taiko.xyz 
9: library LibUtils {
10:     // Warning: Any errors defined here must also be defined in TaikoErrors.sol.
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L8-L10)

```solidity
📁 File: contracts/L1/libs/LibVerifying.sol

15: /// @custom:security-contact security@taiko.xyz 
16: library LibVerifying {
17:     using LibMath for uint256;
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L15-L17)

```solidity
📁 File: contracts/L1/provers/GuardianProver.sol

9: /// @custom:security-contact security@taiko.xyz 
10: contract GuardianProver is Guardians {
11:     uint256[50] private __gap;
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L9-L11)

```solidity
📁 File: contracts/L1/provers/Guardians.sol

8: /// @custom:security-contact security@taiko.xyz 
9: abstract contract Guardians is EssentialContract {
10:     /// @notice The minimum number of guardians
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L8-L10)

```solidity
📁 File: contracts/L1/tiers/DevnetTierProvider.sol

9: /// @custom:security-contact security@taiko.xyz 
10: contract DevnetTierProvider is EssentialContract, ITierProvider {
11:     uint256[50] private __gap;
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L9-L11)

```solidity
📁 File: contracts/L1/tiers/ITierProvider.sol

6: /// @custom:security-contact security@taiko.xyz 
7: interface ITierProvider {
8:     struct Tier {

36: /// @dev Tier ID cannot be zero! 
37: library LibTiers {
38:     /// @notice Optimistic tier ID.
```
[6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L6-L8), [36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L36-L38)

```solidity
📁 File: contracts/L1/tiers/MainnetTierProvider.sol

9: /// @custom:security-contact security@taiko.xyz 
10: contract MainnetTierProvider is EssentialContract, ITierProvider {
11:     uint256[50] private __gap;
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L9-L11)

```solidity
📁 File: contracts/L1/tiers/TestnetTierProvider.sol

9: /// @custom:security-contact security@taiko.xyz 
10: contract TestnetTierProvider is EssentialContract, ITierProvider {
11:     uint256[50] private __gap;
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L9-L11)

```solidity
📁 File: contracts/L2/CrossChainOwned.sol

13: /// @custom:security-contact security@taiko.xyz 
14: abstract contract CrossChainOwned is EssentialContract, IMessageInvocable {
15:     /// @notice The owner chain ID.
```
[13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L13-L15)

```solidity
📁 File: contracts/L2/Lib1559Math.sol

9: /// @custom:security-contact security@taiko.xyz 
10: library Lib1559Math {
11:     error EIP1559_INVALID_PARAMS();
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L9-L11)

```solidity
📁 File: contracts/L2/TaikoL2.sol

20: /// @custom:security-contact security@taiko.xyz 
21: contract TaikoL2 is CrossChainOwned {
22:     using LibAddress for address;
```
[20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L20-L22)

```solidity
📁 File: contracts/L2/TaikoL2EIP1559Configurable.sol

8: /// @custom:security-contact security@taiko.xyz 
9: contract TaikoL2EIP1559Configurable is TaikoL2 {
10:     /// @notice EIP-1559 configuration.
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L8-L10)

```solidity
📁 File: contracts/bridge/IBridge.sol

7: /// @custom:security-contact security@taiko.xyz 
8: interface IBridge {
9:     enum Status {

159: /// @notice An interface that all recallable message senders shall implement. 
160: interface IRecallableSender {
161:     /// @notice Called when a message is recalled.
```
[7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L7-L9), [159](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L159-L161)

```solidity
📁 File: contracts/common/AddressManager.sol

9: /// @custom:security-contact security@taiko.xyz 
10: contract AddressManager is EssentialContract, IAddressManager {
11:     /// @dev Mapping of chainId to mapping of name to address.
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L9-L11)

```solidity
📁 File: contracts/common/AddressResolver.sol

10: /// @custom:security-contact security@taiko.xyz 
11: abstract contract AddressResolver is IAddressResolver, Initializable {
12:     /// @notice Address of the AddressManager.
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L10-L12)

```solidity
📁 File: contracts/common/EssentialContract.sol

9: /// @custom:security-contact security@taiko.xyz 
10: abstract contract EssentialContract is UUPSUpgradeable, Ownable2StepUpgradeable, AddressResolver {
11:     uint8 private constant _FALSE = 1;
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L9-L11)

```solidity
📁 File: contracts/common/IAddressManager.sol

6: /// @custom:security-contact security@taiko.xyz 
7: interface IAddressManager {
8:     /// @notice Gets the address mapped to a specific chainId-name pair.
```
[6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressManager.sol#L6-L8)

```solidity
📁 File: contracts/common/IAddressResolver.sol

12: /// @custom:security-contact security@taiko.xyz 
13: interface IAddressResolver {
14:     /// @notice Resolves a name to its address deployed on this chain.
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressResolver.sol#L12-L14)

```solidity
📁 File: contracts/libs/Lib4844.sol

7: /// @custom:security-contact security@taiko.xyz 
8: library Lib4844 {
9:     /// @notice The address of the point evaluation precompile
```
[7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L7-L9)

```solidity
📁 File: contracts/libs/LibAddress.sol

12: /// @custom:security-contact security@taiko.xyz 
13: library LibAddress {
14:     bytes4 private constant _EIP1271_MAGICVALUE = 0x1626ba7e;
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L12-L14)

```solidity
📁 File: contracts/libs/LibMath.sol

6: /// @custom:security-contact security@taiko.xyz 
7: library LibMath {
8:     /// @dev Returns the smaller of the two given values.
```
[6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibMath.sol#L6-L8)

```solidity
📁 File: contracts/libs/LibTrieProof.sol

14: /// @custom:security-contact security@taiko.xyz 
15: library LibTrieProof {
16:     // The consensus format representing account is RLP encoded in the
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L14-L16)

```solidity
📁 File: contracts/signal/ISignalService.sol

11: /// @custom:security-contact security@taiko.xyz 
12: interface ISignalService {
13:     enum CacheOption {
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L11-L13)

```solidity
📁 File: contracts/signal/LibSignals.sol

5: /// @custom:security-contact security@taiko.xyz 
6: library LibSignals {
7:     /// @notice Keccak hash of the string "STATE_ROOT".
```
[5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/LibSignals.sol#L5-L7)

```solidity
📁 File: contracts/signal/SignalService.sol

13: /// @custom:security-contact security@taiko.xyz 
14: contract SignalService is EssentialContract, ISignalService {
15:     /// @notice Mapping to store the top blockId.
```
[13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L13-L15)

</details>


---
### [NC&#x2011;74] NatSpec: Contract declarations should have `@dev` tags
<details>
<summary><i>There are 40 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/ITaikoL1.sol

7: /// @custom:security-contact security@taiko.xyz 
8: interface ITaikoL1 {
9:     /// @notice Proposes a Taiko L2 block.
```
[7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/ITaikoL1.sol#L7-L9)

```solidity
📁 File: contracts/L1/TaikoData.sol

7: /// @custom:security-contact security@taiko.xyz 
8: library TaikoData {
9:     /// @dev Struct holding Taiko configuration parameters. See {TaikoConfig}.
```
[7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L7-L9)

```solidity
📁 File: contracts/L1/gov/TaikoGovernor.sol

15: /// @custom:security-contact security@taiko.xyz 
16: contract TaikoGovernor is
17:     EssentialContract,
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L15-L17)

```solidity
📁 File: contracts/L1/gov/TaikoTimelockController.sol

8: /// @custom:security-contact security@taiko.xyz 
9: contract TaikoTimelockController is EssentialContract, TimelockControllerUpgradeable {
10:     uint256[50] private __gap;
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L8-L10)

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

13: /// @custom:security-contact security@taiko.xyz 
14: contract AssignmentHook is EssentialContract, IHook {
15:     using LibAddress for address;
```
[13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L13-L15)

```solidity
📁 File: contracts/L1/hooks/IHook.sol

7: /// @custom:security-contact security@taiko.xyz 
8: interface IHook {
9:     /// @notice Called when a block is proposed.
```
[7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/IHook.sol#L7-L9)

```solidity
📁 File: contracts/L1/libs/LibDepositing.sol

11: /// @custom:security-contact security@taiko.xyz 
12: library LibDepositing {
13:     using LibAddress for address;
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L11-L13)

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

14: /// @custom:security-contact security@taiko.xyz 
15: library LibProposing {
16:     using LibAddress for address;
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L14-L16)

```solidity
📁 File: contracts/L1/libs/LibProving.sol

15: /// @custom:security-contact security@taiko.xyz 
16: library LibProving {
17:     using LibMath for uint256;
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L15-L17)

```solidity
📁 File: contracts/L1/libs/LibUtils.sol

8: /// @custom:security-contact security@taiko.xyz 
9: library LibUtils {
10:     // Warning: Any errors defined here must also be defined in TaikoErrors.sol.
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L8-L10)

```solidity
📁 File: contracts/L1/libs/LibVerifying.sol

15: /// @custom:security-contact security@taiko.xyz 
16: library LibVerifying {
17:     using LibMath for uint256;
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L15-L17)

```solidity
📁 File: contracts/L1/provers/GuardianProver.sol

9: /// @custom:security-contact security@taiko.xyz 
10: contract GuardianProver is Guardians {
11:     uint256[50] private __gap;
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L9-L11)

```solidity
📁 File: contracts/L1/provers/Guardians.sol

8: /// @custom:security-contact security@taiko.xyz 
9: abstract contract Guardians is EssentialContract {
10:     /// @notice The minimum number of guardians
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L8-L10)

```solidity
📁 File: contracts/L1/tiers/ITierProvider.sol

6: /// @custom:security-contact security@taiko.xyz 
7: interface ITierProvider {
8:     struct Tier {
```
[6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L6-L8)

```solidity
📁 File: contracts/L2/TaikoL2.sol

20: /// @custom:security-contact security@taiko.xyz 
21: contract TaikoL2 is CrossChainOwned {
22:     using LibAddress for address;
```
[20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L20-L22)

```solidity
📁 File: contracts/L2/TaikoL2EIP1559Configurable.sol

8: /// @custom:security-contact security@taiko.xyz 
9: contract TaikoL2EIP1559Configurable is TaikoL2 {
10:     /// @notice EIP-1559 configuration.
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L8-L10)

```solidity
📁 File: contracts/bridge/IBridge.sol

159: /// @notice An interface that all recallable message senders shall implement. 
160: interface IRecallableSender {
161:     /// @notice Called when a message is recalled.

173: /// @notice An interface that all bridge message receiver shall implement 
174: interface IMessageInvocable {
175:     /// @notice Called when this contract is the bridge target.
```
[159](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L159-L161), [173](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L173-L175)

```solidity
📁 File: contracts/common/AddressManager.sol

9: /// @custom:security-contact security@taiko.xyz 
10: contract AddressManager is EssentialContract, IAddressManager {
11:     /// @dev Mapping of chainId to mapping of name to address.
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L9-L11)

```solidity
📁 File: contracts/common/AddressResolver.sol

10: /// @custom:security-contact security@taiko.xyz 
11: abstract contract AddressResolver is IAddressResolver, Initializable {
12:     /// @notice Address of the AddressManager.
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L10-L12)

```solidity
📁 File: contracts/common/EssentialContract.sol

9: /// @custom:security-contact security@taiko.xyz 
10: abstract contract EssentialContract is UUPSUpgradeable, Ownable2StepUpgradeable, AddressResolver {
11:     uint8 private constant _FALSE = 1;
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L9-L11)

```solidity
📁 File: contracts/common/IAddressManager.sol

6: /// @custom:security-contact security@taiko.xyz 
7: interface IAddressManager {
8:     /// @notice Gets the address mapped to a specific chainId-name pair.
```
[6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressManager.sol#L6-L8)

```solidity
📁 File: contracts/libs/LibTrieProof.sol

14: /// @custom:security-contact security@taiko.xyz 
15: library LibTrieProof {
16:     // The consensus format representing account is RLP encoded in the
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L14-L16)

```solidity
📁 File: contracts/signal/ISignalService.sol

11: /// @custom:security-contact security@taiko.xyz 
12: interface ISignalService {
13:     enum CacheOption {
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L11-L13)

```solidity
📁 File: contracts/signal/LibSignals.sol

5: /// @custom:security-contact security@taiko.xyz 
6: library LibSignals {
7:     /// @notice Keccak hash of the string "STATE_ROOT".
```
[5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/LibSignals.sol#L5-L7)

```solidity
📁 File: contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol

4:  
5: library ExcessivelySafeCall {
6:     uint256 constant LOW_28_MASK =
```
[4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L4-L6)

```solidity
📁 File: contracts/thirdparty/optimism/Bytes.sol

5: /// @notice Bytes is a library for manipulating byte arrays. 
6: library Bytes {
7:     /// @custom:attribution https://github.com/GNSPS/solidity-bytes-utils
```
[5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L5-L7)

```solidity
📁 File: contracts/thirdparty/optimism/rlp/RLPReader.sol

8: ///         various tweaks to improve readability. 
9: library RLPReader {
10:     /// @notice Custom pointer type to avoid confusion between pointers and uint256s.
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L8-L10)

```solidity
📁 File: contracts/thirdparty/optimism/rlp/RLPWriter.sol

8: ///         modifications to improve legibility. 
9: library RLPWriter {
10:     /// @notice RLP encodes a byte string.
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L8-L10)

```solidity
📁 File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

10: ///         trie radix constant to support other trie radixes. 
11: library MerkleTrie {
12:     /// @notice Struct representing a node in the trie.
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L10-L12)

```solidity
📁 File: contracts/tokenvault/BaseNFTVault.sol

8: /// @custom:security-contact security@taiko.xyz 
9: abstract contract BaseNFTVault is BaseVault {
10:     // Struct representing the canonical NFT on another chain.
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L8-L10)

```solidity
📁 File: contracts/tokenvault/BaseVault.sol

11: /// @custom:security-contact security@taiko.xyz 
12: abstract contract BaseVault is
13:     EssentialContract,
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L11-L13)

```solidity
📁 File: contracts/tokenvault/BridgedERC1155.sol

13: /// @custom:security-contact security@taiko.xyz 
14: contract BridgedERC1155 is EssentialContract, IERC1155MetadataURIUpgradeable, ERC1155Upgradeable {
15:     /// @notice Address of the source token contract.
```
[13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L13-L15)

```solidity
📁 File: contracts/tokenvault/BridgedERC20.sol

14: /// @custom:security-contact security@taiko.xyz 
15: contract BridgedERC20 is
16:     BridgedERC20Base,
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L14-L16)

```solidity
📁 File: contracts/tokenvault/BridgedERC20Base.sol

8: /// @custom:security-contact security@taiko.xyz 
9: abstract contract BridgedERC20Base is EssentialContract, IBridgedERC20 {
10:     /// @notice The address of the contract to migrate tokens to or from.
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L8-L10)

```solidity
📁 File: contracts/tokenvault/BridgedERC721.sol

11: /// @custom:security-contact security@taiko.xyz 
12: contract BridgedERC721 is EssentialContract, ERC721Upgradeable {
13:     /// @notice Address of the source token contract.
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L11-L13)

```solidity
📁 File: contracts/tokenvault/ERC1155Vault.sol

15: /// @custom:security-contact security@taiko.xyz 
16: interface IERC1155NameAndSymbol {
17:     /// @notice Returns the name of the token.
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L15-L17)

```solidity
📁 File: contracts/tokenvault/LibBridgedToken.sol

7: /// @custom:security-contact security@taiko.xyz 
8: library LibBridgedToken {
9:     error BTOKEN_INVALID_PARAMS();
```
[7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L7-L9)

```solidity
📁 File: contracts/tokenvault/adapters/USDCAdapter.sol

7: /// @custom:security-contact security@taiko.xyz 
8: interface IUSDC {
9:     /// @notice Burns a specific amount of tokens.

27: /// @custom:security-contact security@taiko.xyz 
28: contract USDCAdapter is BridgedERC20Base {
29:     /// @notice The USDC instance.
```
[7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L7-L9), [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L27-L29)

</details>


---
### [NC&#x2011;75] NatSpec: Contract declarations should have `@notice` tags
`@notice` is used to explain to end users what the contract does, and the compiler interprets `///` or `/**` comments as this tag if one was't explicitly provided

<details>
<summary><i>There are 38 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/ITaikoL1.sol

8: interface ITaikoL1 { 
9:     /// @notice Proposes a Taiko L2 block.
10:     /// @param _params Block parameters, currently an encoded BlockParams object.
11:     /// @param _txList txList data if calldata is used for DA.
12:     /// @return meta_ The metadata of the proposed L2 block.
13:     /// @return deposits_ The Ether deposits processed.
14:     function proposeBlock(
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/ITaikoL1.sol#L8-L14)

```solidity
📁 File: contracts/L1/gov/TaikoGovernor.sol

16: contract TaikoGovernor is 
17:     EssentialContract,
18:     GovernorCompatibilityBravoUpgradeable,
19:     GovernorVotesUpgradeable,
20:     GovernorVotesQuorumFractionUpgradeable,
21:     GovernorTimelockControlUpgradeable
22: {
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L16-L22)

```solidity
📁 File: contracts/L1/gov/TaikoTimelockController.sol

9: contract TaikoTimelockController is EssentialContract, TimelockControllerUpgradeable { 
10:     uint256[50] private __gap;
11: 
12:     /// @notice Initializes the contract.
13:     /// @param _owner The owner of this contract. msg.sender will be used if this value is zero.
14:     /// @param _minDelay The minimal delay.
15:     function init(address _owner, uint256 _minDelay) external initializer {
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L9-L15)

```solidity
📁 File: contracts/L1/hooks/IHook.sol

8: interface IHook { 
9:     /// @notice Called when a block is proposed.
10:     /// @param _blk The proposed block.
11:     /// @param _meta The metadata of the proposed block.
12:     /// @param _data The data of the proposed block.
13:     function onBlockProposed(
14:         TaikoData.Block memory _blk,
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/IHook.sol#L8-L14)

```solidity
📁 File: contracts/L1/provers/GuardianProver.sol

10: contract GuardianProver is Guardians { 
11:     uint256[50] private __gap;
12: 
13:     /// @notice Emitted when a guardian proof is approved.
14:     /// @param addr The address of the guardian.
15:     /// @param blockId The block ID.
16:     /// @param blockHash The block hash.
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L10-L16)

```solidity
📁 File: contracts/L1/tiers/DevnetTierProvider.sol

10: contract DevnetTierProvider is EssentialContract, ITierProvider { 
11:     uint256[50] private __gap;
12: 
13:     /// @notice Initializes the contract.
14:     /// @param _owner The owner of this contract. msg.sender will be used if this value is zero.
15:     function init(address _owner) external initializer {
16:         __Essential_init(_owner);
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L10-L16)

```solidity
📁 File: contracts/L1/tiers/ITierProvider.sol

37: library LibTiers { 
38:     /// @notice Optimistic tier ID.
39:     uint16 public constant TIER_OPTIMISTIC = 100;
40: 
41:     /// @notice SGX tier ID.
42:     uint16 public constant TIER_SGX = 200;
43: 
```
[37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L37-L43)

```solidity
📁 File: contracts/L1/tiers/MainnetTierProvider.sol

10: contract MainnetTierProvider is EssentialContract, ITierProvider { 
11:     uint256[50] private __gap;
12: 
13:     /// @notice Initializes the contract.
14:     /// @param _owner The owner of this contract. msg.sender will be used if this value is zero.
15:     function init(address _owner) external initializer {
16:         __Essential_init(_owner);
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L10-L16)

```solidity
📁 File: contracts/L1/tiers/TestnetTierProvider.sol

10: contract TestnetTierProvider is EssentialContract, ITierProvider { 
11:     uint256[50] private __gap;
12: 
13:     /// @notice Initializes the contract.
14:     /// @param _owner The owner of this contract. msg.sender will be used if this value is zero.
15:     function init(address _owner) external initializer {
16:         __Essential_init(_owner);
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L10-L16)

```solidity
📁 File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

22: contract AutomataDcapV3Attestation is IAttestation { 
23:     using BytesUtils for bytes;
24: 
25:     ISigVerifyLib public immutable sigVerifyLib;
26:     IPEMCertChainLib public immutable pemCertLib;
27: 
28:     // https://github.com/intel/SGXDataCenterAttestationPrimitives/blob/e7604e02331b3377f3766ed3653250e03af72d45/QuoteVerification/QVL/Src/AttestationLibrary/src/CertVerification/X509Constants.h#L64
```
[22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L22-L28)

```solidity
📁 File: contracts/automata-attestation/interfaces/IAttestation.sol

8: interface IAttestation { 
9:     function verifyAttestation(bytes calldata data) external returns (bool);
10:     function verifyParsedQuote(V3Struct.ParsedV3QuoteStruct calldata v3quote)
11:         external
12:         returns (bool success, bytes memory retData);
13: }
14: 
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/interfaces/IAttestation.sol#L8-L14)

```solidity
📁 File: contracts/automata-attestation/interfaces/ISigVerifyLib.sol

6: interface ISigVerifyLib { 
7:     enum KeyType {
8:         RSA,
9:         ECDSA
10:     }
11: 
12:     struct PublicKey {
```
[6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L6-L12)

```solidity
📁 File: contracts/automata-attestation/lib/EnclaveIdStruct.sol

6: library EnclaveIdStruct { 
7:     struct EnclaveId {
8:         bytes4 miscselect;
9:         bytes4 miscselectMask;
10:         uint16 isvprodid;
11:         bytes16 attributes;
12:         bytes16 attributesMask;
```
[6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/EnclaveIdStruct.sol#L6-L12)

```solidity
📁 File: contracts/automata-attestation/lib/PEMCertChainLib.sol

12: contract PEMCertChainLib is IPEMCertChainLib { 
13:     using Asn1Decode for bytes;
14:     using NodePtr for uint256;
15:     using BytesUtils for bytes;
16: 
17:     string internal constant HEADER = "-----BEGIN CERTIFICATE-----";
18:     string internal constant FOOTER = "-----END CERTIFICATE-----";
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L12-L18)

```solidity
📁 File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

11: library V3Parser { 
12:     using BytesUtils for bytes;
13: 
14:     uint256 internal constant MINIMUM_QUOTE_LENGTH = 1020;
15:     bytes2 internal constant SUPPORTED_QUOTE_VERSION = 0x0300;
16:     bytes2 internal constant SUPPORTED_ATTESTATION_KEY_TYPE = 0x0200;
17:     // SGX only
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L11-L17)

```solidity
📁 File: contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol

6: library V3Struct { 
7:     struct Header {
8:         bytes2 version;
9:         bytes2 attestationKeyType;
10:         bytes4 teeType;
11:         bytes2 qeSvn;
12:         bytes2 pceSvn;
```
[6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L6-L12)

```solidity
📁 File: contracts/automata-attestation/lib/TCBInfoStruct.sol

6: library TCBInfoStruct { 
7:     struct TCBInfo {
8:         string pceid;
9:         string fmspc;
10:         TCBLevelObj[] tcbLevels;
11:     }
12: 
```
[6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol#L6-L12)

```solidity
📁 File: contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol

6: interface IPEMCertChainLib { 
7:     struct ECSha256Certificate {
8:         uint256 notBefore;
9:         uint256 notAfter;
10:         bytes serialNumber;
11:         bytes tbsCertificate;
12:         bytes pubKey;
```
[6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L6-L12)

```solidity
📁 File: contracts/automata-attestation/utils/Asn1Decode.sol

12: library NodePtr { 
13:     // Unpack first byte index
14:     function ixs(uint256 self) internal pure returns (uint256) {
15:         return uint80(self);
16:     }
17:     // Unpack first content byte index
18: 

38: library Asn1Decode { 
39:     using NodePtr for uint256;
40:     using BytesUtils for bytes;
41: 
42:     /*
43:     * @dev Get the root node. First step in traversing an ASN1 structure
44:     * @param der The DER-encoded ASN1 structure
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L12-L18), [38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L38-L44)

```solidity
📁 File: contracts/automata-attestation/utils/BytesUtils.sol

8: library BytesUtils { 
9:     /*
10:     * @dev Returns the keccak-256 hash of a byte range.
11:     * @param self The byte string to hash.
12:     * @param offset The position to start hashing at.
13:     * @param len The number of bytes to hash.
14:     * @return The hash of the byte range.
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L8-L14)

```solidity
📁 File: contracts/automata-attestation/utils/RsaVerify.sol

34: library RsaVerify { 
35:     /**
36:      * @dev Verifies a PKCSv1.5 SHA256 signature
37:      * @param _sha256 is the sha256 of the data
38:      * @param _s is the signature
39:      * @param _e is the exponent
40:      * @param _m is the modulus
```
[34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L34-L40)

```solidity
📁 File: contracts/automata-attestation/utils/SHA1.sol

10: library SHA1 { 
11:     function sha1(bytes memory data) internal pure returns (bytes20 ret) {
12:         assembly {
13:             // Get a safe scratch location
14:             let scratch := mload(0x40)
15: 
16:             // Get the data length, and point data at the first byte
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SHA1.sol#L10-L16)

```solidity
📁 File: contracts/automata-attestation/utils/SigVerifyLib.sol

15: contract SigVerifyLib is ISigVerifyLib { 
16:     using BytesUtils for bytes;
17: 
18:     address private ES256VERIFIER;
19: 
20:     constructor(address es256Verifier) {
21:         ES256VERIFIER = es256Verifier;
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L15-L21)

```solidity
📁 File: contracts/automata-attestation/utils/X509DateUtils.sol

7: library X509DateUtils { 
8:     function toTimestamp(bytes memory x509Time) internal pure returns (uint256) {
9:         uint16 yrs;
10:         uint8 mnths;
11:         uint8 dys;
12:         uint8 hrs;
13:         uint8 mins;
```
[7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L7-L13)

```solidity
📁 File: contracts/common/EssentialContract.sol

10: abstract contract EssentialContract is UUPSUpgradeable, Ownable2StepUpgradeable, AddressResolver { 
11:     uint8 private constant _FALSE = 1;
12: 
13:     uint8 private constant _TRUE = 2;
14: 
15:     /// @dev The slot in transient storage of the reentry lock. This is the keccak256 hash
16:     /// of "ownerUUPS.reentry_slot"
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L10-L16)

```solidity
📁 File: contracts/libs/LibAddress.sol

13: library LibAddress { 
14:     bytes4 private constant _EIP1271_MAGICVALUE = 0x1626ba7e;
15: 
16:     error ETH_TRANSFER_FAILED();
17: 
18:     /// @dev Sends Ether to the specified address.
19:     /// @param _to The recipient address.
```
[13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L13-L19)

```solidity
📁 File: contracts/libs/LibMath.sol

7: library LibMath { 
8:     /// @dev Returns the smaller of the two given values.
9:     /// @param _a The first number to compare.
10:     /// @param _b The second number to compare.
11:     /// @return The smaller of the two numbers.
12:     function min(uint256 _a, uint256 _b) internal pure returns (uint256) {
13:         return _a > _b ? _b : _a;
```
[7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibMath.sol#L7-L13)

```solidity
📁 File: contracts/libs/LibTrieProof.sol

15: library LibTrieProof { 
16:     // The consensus format representing account is RLP encoded in the
17:     // following order: nonce, balance, storageHash, codeHash.
18:     uint256 private constant _ACCOUNT_FIELD_INDEX_STORAGE_HASH = 2;
19: 
20:     error LTP_INVALID_ACCOUNT_PROOF();
21:     error LTP_INVALID_INCLUSION_PROOF();
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L15-L21)

```solidity
📁 File: contracts/signal/LibSignals.sol

6: library LibSignals { 
7:     /// @notice Keccak hash of the string "STATE_ROOT".
8:     bytes32 public constant STATE_ROOT = keccak256("STATE_ROOT");
9: 
10:     /// @notice Keccak hash of the string "SIGNAL_ROOT".
11:     bytes32 public constant SIGNAL_ROOT = keccak256("SIGNAL_ROOT");
12: }
```
[6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/LibSignals.sol#L6-L12)

```solidity
📁 File: contracts/team/airdrop/ERC721Airdrop.sol

9: contract ERC721Airdrop is MerkleClaimable { 
10:     /// @notice The address of the token contract.
11:     address public token;
12: 
13:     /// @notice The address of the vault contract.
14:     address public vault;
15: 
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L9-L15)

```solidity
📁 File: contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol

5: library ExcessivelySafeCall { 
6:     uint256 constant LOW_28_MASK =
7:         0x00000000ffffffffffffffffffffffffffffffffffffffffffffffffffffffff;
8: 
9:     /// @notice Use when you _really_ really _really_ don't trust the called
10:     /// contract. This prevents the called contract from causing reversion of
11:     /// the caller in as many ways as we can.
```
[5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L5-L11)

```solidity
📁 File: contracts/thirdparty/solmate/LibFixedPointMath.sol

6: library LibFixedPointMath { 
7:     uint128 public constant MAX_EXP_INPUT = 135_305_999_368_893_231_588;
8:     uint256 public constant SCALING_FACTOR = 1e18; // For fixed point representation factor
9: 
10:     error Overflow();
11: 
12:     // Computes e^x in 1e18 fixed point.
```
[6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L6-L12)

```solidity
📁 File: contracts/tokenvault/BridgedERC20Base.sol

9: abstract contract BridgedERC20Base is EssentialContract, IBridgedERC20 { 
10:     /// @notice The address of the contract to migrate tokens to or from.
11:     address public migratingAddress;
12: 
13:     /// @notice If true, signals migrating 'to', false if migrating 'from'.
14:     bool public migratingInbound;
15: 
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L9-L15)

```solidity
📁 File: contracts/tokenvault/LibBridgedToken.sol

8: library LibBridgedToken { 
9:     error BTOKEN_INVALID_PARAMS();
10: 
11:     function validateInputs(
12:         address _srcToken,
13:         uint256 _srcChainId,
14:         string memory _symbol,
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L8-L14)

```solidity
📁 File: contracts/tokenvault/adapters/USDCAdapter.sol

8: interface IUSDC { 
9:     /// @notice Burns a specific amount of tokens.
10:     /// @param _amount The amount of token to be burned.
11:     function burn(uint256 _amount) external;
12: 
13:     /// @notice Mints a specific amount of new tokens to an address.
14:     /// @param _to The address that will receive the minted tokens.

28: contract USDCAdapter is BridgedERC20Base { 
29:     /// @notice The USDC instance.
30:     /// @dev Slot 1.
31:     IUSDC public usdc;
32:     uint256[49] private __gap;
33: 
34:     /// @notice Initializes the contract.
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L8-L14), [28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L28-L34)

```solidity
📁 File: contracts/verifiers/GuardianVerifier.sol

10: contract GuardianVerifier is EssentialContract, IVerifier { 
11:     uint256[50] private __gap;
12: 
13:     error PERMISSION_DENIED();
14: 
15:     /// @notice Initializes the contract.
16:     /// @param _owner The owner of this contract. msg.sender will be used if this value is zero.
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L10-L16)

</details>


---
### [NC&#x2011;76] NatSpec: Contract declarations should have `@title` tags
<details>
<summary><i>There are 3 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/tiers/ITierProvider.sol

36: /// @dev Tier ID cannot be zero! 
37: library LibTiers {
38:     /// @notice Optimistic tier ID.
```
[36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L36-L38)

```solidity
📁 File: contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol

4:  
5: library ExcessivelySafeCall {
6:     uint256 constant LOW_28_MASK =
```
[4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L4-L6)

```solidity
📁 File: contracts/thirdparty/solmate/LibFixedPointMath.sol

5:  
6: library LibFixedPointMath {
7:     uint128 public constant MAX_EXP_INPUT = 135_305_999_368_893_231_588;
```
[5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L5-L7)

</details>


---
### [NC&#x2011;77] NatSpec: Contract declarations should have NatSpec descriptions
It is recommended that Solidity libraries and contracts are fully annotated using NatSpec for all public interfaces (everything in the ABI). It is clearly stated in the Solidity official documentation. In complex projects such as DeFi, the interpretation of all functions and their arguments and returns is important for code readability and auditability.

<details>
<summary><i>There are 2 instances of this issue:</i></summary>

```solidity
📁 File: contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol

5: library ExcessivelySafeCall { 
6:     uint256 constant LOW_28_MASK =
7:         0x00000000ffffffffffffffffffffffffffffffffffffffffffffffffffffffff;
8: 
9:     /// @notice Use when you _really_ really _really_ don't trust the called
10:     /// contract. This prevents the called contract from causing reversion of
11:     /// the caller in as many ways as we can.
```
[5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L5-L11)

```solidity
📁 File: contracts/thirdparty/solmate/LibFixedPointMath.sol

6: library LibFixedPointMath { 
7:     uint128 public constant MAX_EXP_INPUT = 135_305_999_368_893_231_588;
8:     uint256 public constant SCALING_FACTOR = 1e18; // For fixed point representation factor
9: 
10:     error Overflow();
11: 
12:     // Computes e^x in 1e18 fixed point.
```
[6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L6-L12)

</details>


---
### [NC&#x2011;78] NatSpec: Error declarations should have `@notice` tags
`@notice` is used to explain to end users what the error does, and the compiler interprets `///` or `/**` comments as this tag if one was't explicitly provided

<details>
<summary><i>There are 40 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/gov/TaikoGovernor.sol

25:     error TG_INVALID_SIGNATURES_LENGTH(); 
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L25)

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

50:     error HOOK_ASSIGNMENT_EXPIRED(); 
51:     error HOOK_ASSIGNMENT_INVALID_SIG();
52:     error HOOK_TIER_NOT_FOUND();
```
[50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L50-L52)

```solidity
📁 File: contracts/L1/libs/LibDepositing.sol

22:     error L1_INVALID_ETH_DEPOSIT(); 
```
[22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L22)

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

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
[44](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L44-L57)

```solidity
📁 File: contracts/L1/libs/LibProving.sol

59:     error L1_ALREADY_CONTESTED(); 
60:     error L1_ALREADY_PROVED();
61:     error L1_ASSIGNED_PROVER_NOT_ALLOWED();
62:     error L1_BLOCK_MISMATCH();
63:     error L1_INVALID_BLOCK_ID();
```
[59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L59-L63)

```solidity
📁 File: contracts/common/AddressManager.sol

25:     error AM_INVALID_PARAMS(); 
26:     error AM_UNSUPPORTED();
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L25-L26)

```solidity
📁 File: contracts/common/AddressResolver.sol

16:     error RESOLVER_DENIED(); 
17:     error RESOLVER_INVALID_MANAGER();
18:     error RESOLVER_UNEXPECTED_CHAINID();
19:     error RESOLVER_ZERO_ADDR(uint64 chainId, bytes32 name);
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L16-L19)

```solidity
📁 File: contracts/common/EssentialContract.sol

35:     error REENTRANT_CALL(); 
36:     error INVALID_PAUSE_STATUS();
37:     error ZERO_ADDR_MANAGER();
```
[35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L35-L37)

```solidity
📁 File: contracts/libs/Lib4844.sol

19:     error EVAL_FAILED_1(); 
20:     error EVAL_FAILED_2();
21:     error POINT_X_TOO_LARGE();
22:     error POINT_Y_TOO_LARGE();
```
[19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L19-L22)

```solidity
📁 File: contracts/libs/LibAddress.sol

16:     error ETH_TRANSFER_FAILED(); 
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L16)

```solidity
📁 File: contracts/libs/LibTrieProof.sol

20:     error LTP_INVALID_ACCOUNT_PROOF(); 
21:     error LTP_INVALID_INCLUSION_PROOF();
```
[20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L20-L21)

</details>


---
### [NC&#x2011;79] NatSpec: Error declarations should have NatSpec descriptions
It is recommended that errors are fully annotated using NatSpec. It is clearly stated in the Solidity official documentation.

<details>
<summary><i>There are 40 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/gov/TaikoGovernor.sol

25:     error TG_INVALID_SIGNATURES_LENGTH(); 
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L25)

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

50:     error HOOK_ASSIGNMENT_EXPIRED(); 
51:     error HOOK_ASSIGNMENT_INVALID_SIG();
52:     error HOOK_TIER_NOT_FOUND();
```
[50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L50-L52)

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

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
[44](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L44-L57)

```solidity
📁 File: contracts/L1/libs/LibProving.sol

59:     error L1_ALREADY_CONTESTED(); 
60:     error L1_ALREADY_PROVED();
61:     error L1_ASSIGNED_PROVER_NOT_ALLOWED();
62:     error L1_BLOCK_MISMATCH();
63:     error L1_INVALID_BLOCK_ID();
64:     error L1_INVALID_PAUSE_STATUS();
```
[59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L59-L64)

```solidity
📁 File: contracts/common/AddressManager.sol

25:     error AM_INVALID_PARAMS(); 
26:     error AM_UNSUPPORTED();
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L25-L26)

```solidity
📁 File: contracts/common/AddressResolver.sol

16:     error RESOLVER_DENIED(); 
17:     error RESOLVER_INVALID_MANAGER();
18:     error RESOLVER_UNEXPECTED_CHAINID();
19:     error RESOLVER_ZERO_ADDR(uint64 chainId, bytes32 name);
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L16-L19)

```solidity
📁 File: contracts/common/EssentialContract.sol

35:     error REENTRANT_CALL(); 
36:     error INVALID_PAUSE_STATUS();
37:     error ZERO_ADDR_MANAGER();
```
[35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L35-L37)

```solidity
📁 File: contracts/libs/Lib4844.sol

19:     error EVAL_FAILED_1(); 
20:     error EVAL_FAILED_2();
21:     error POINT_X_TOO_LARGE();
22:     error POINT_Y_TOO_LARGE();
```
[19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L19-L22)

```solidity
📁 File: contracts/libs/LibAddress.sol

16:     error ETH_TRANSFER_FAILED(); 
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L16)

```solidity
📁 File: contracts/libs/LibTrieProof.sol

20:     error LTP_INVALID_ACCOUNT_PROOF(); 
21:     error LTP_INVALID_INCLUSION_PROOF();
```
[20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L20-L21)

</details>


---
### [NC&#x2011;80] NatSpec: Error missing NatSpec `@dev` tag
<details>
<summary><i>There are 40 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/gov/TaikoGovernor.sol

24:  
25:     error TG_INVALID_SIGNATURES_LENGTH();
26: 
```
[24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L24-L26)

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

49:  
50:     error HOOK_ASSIGNMENT_EXPIRED();
51:     error HOOK_ASSIGNMENT_INVALID_SIG();
52:     error HOOK_TIER_NOT_FOUND();
53: 
```
[49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L49-L53)

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

43:     // Warning: Any errors defined here must also be defined in TaikoErrors.sol. 
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
58: 
```
[43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L43-L58)

```solidity
📁 File: contracts/L1/libs/LibProving.sol

58:     // Warning: Any errors defined here must also be defined in TaikoErrors.sol. 
59:     error L1_ALREADY_CONTESTED();
60:     error L1_ALREADY_PROVED();
61:     error L1_ASSIGNED_PROVER_NOT_ALLOWED();
62:     error L1_BLOCK_MISMATCH();
63:     error L1_INVALID_BLOCK_ID();
64:     error L1_INVALID_PAUSE_STATUS();
65:     error L1_INVALID_TIER();
```
[58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L58-L65)

```solidity
📁 File: contracts/common/AddressManager.sol

24:  
25:     error AM_INVALID_PARAMS();
26:     error AM_UNSUPPORTED();
27: 
```
[24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L24-L27)

```solidity
📁 File: contracts/common/AddressResolver.sol

15:  
16:     error RESOLVER_DENIED();
17:     error RESOLVER_INVALID_MANAGER();
18:     error RESOLVER_UNEXPECTED_CHAINID();
19:     error RESOLVER_ZERO_ADDR(uint64 chainId, bytes32 name);
20: 
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L15-L20)

```solidity
📁 File: contracts/common/EssentialContract.sol

34:  
35:     error REENTRANT_CALL();
36:     error INVALID_PAUSE_STATUS();
37:     error ZERO_ADDR_MANAGER();
38: 
```
[34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L34-L38)

```solidity
📁 File: contracts/libs/Lib4844.sol

18:  
19:     error EVAL_FAILED_1();
20:     error EVAL_FAILED_2();
21:     error POINT_X_TOO_LARGE();
22:     error POINT_Y_TOO_LARGE();
23: 
```
[18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L18-L23)

```solidity
📁 File: contracts/libs/LibAddress.sol

15:  
16:     error ETH_TRANSFER_FAILED();
17: 
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L15-L17)

```solidity
📁 File: contracts/libs/LibTrieProof.sol

19:  
20:     error LTP_INVALID_ACCOUNT_PROOF();
21:     error LTP_INVALID_INCLUSION_PROOF();
22: 
```
[19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L19-L22)

</details>


---
### [NC&#x2011;81] NatSpec: Error missing NatSpec `@param` tag

<i>There is one instance of this issue:</i>

```solidity
📁 File: contracts/common/AddressResolver.sol

/// @audit Missing @param for all error parameters
19:     error RESOLVER_ZERO_ADDR(uint64 chainId, bytes32 name); 
```
[19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L19)


---
### [NC&#x2011;82] NatSpec: Event declarations should have `@notice` tags
`@notice` is used to explain to end users what the event emits, and the compiler interprets `///` or `/**` comments as this tag if one was't explicitly provided


<i>There are 4 instaces of this issue:</i>

```solidity
📁 File: contracts/L1/TaikoEvents.sol

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
[53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L53-L59), [67](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L67-L73), [77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L77), [81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L81)


---
### [NC&#x2011;83] NatSpec: Event missing NatSpec `@dev` tag
<details>
<summary><i>There are 40 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

45:     /// @param assignment The prover assignment. 
46:     event BlockAssigned(
47:         address indexed assignedProver, TaikoData.BlockMetadata meta, ProverAssignment assignment
```
[45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L45-L47)

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

30:     /// block. 
31:     event BlockProposed(
32:         uint256 indexed blockId,

40:     /// @param blobHash The hash of the cached blob. 
41:     event BlobCached(bytes32 blobHash);
42: 
```
[30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L30-L32), [40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L40-L42)

```solidity
📁 File: contracts/L1/libs/LibProving.sol

31:     /// @param tier The tier of the proof. 
32:     event TransitionProved(
33:         uint256 indexed blockId,

45:     /// @param tier The tier of the proof. 
46:     event TransitionContested(
47:         uint256 indexed blockId,

55:     /// @param paused The pause status. 
56:     event ProvingPaused(bool paused);
57: 
```
[31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L31-L33), [45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L45-L47), [55](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L55-L57)

```solidity
📁 File: contracts/L1/libs/LibVerifying.sol

27:     /// @param contestations The number of contestations. 
28:     event BlockVerified(
29:         uint256 indexed blockId,
```
[27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L27-L29)

```solidity
📁 File: contracts/L1/provers/GuardianProver.sol

17:     /// @param approved If the proof is approved. 
18:     event GuardianApproval(
19:         address indexed addr, uint256 indexed blockId, bytes32 blockHash, bool approved
```
[17](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L17-L19)

```solidity
📁 File: contracts/L1/provers/Guardians.sol

36:     /// @param guardians The new set of guardians 
37:     event GuardiansUpdated(uint32 version, address[] guardians);
38: 

42:     /// @param proofSubmitted If the proof was submitted 
43:     event Approved(uint256 indexed operationId, uint256 approvalBits, bool proofSubmitted);
44: 
```
[36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L36-L38), [42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L42-L44)

```solidity
📁 File: contracts/L2/CrossChainOwned.sol

25:     /// @param selector The function selector. 
26:     event TransactionExecuted(uint64 indexed txId, bytes4 indexed selector);
27: 
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L25-L27)

```solidity
📁 File: contracts/L2/TaikoL2.sol

56:     /// @param gasExcess The gas excess value used to calculate the base fee. 
57:     event Anchored(bytes32 parentHash, uint64 gasExcess);
58: 
```
[56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L56-L58)

```solidity
📁 File: contracts/L2/TaikoL2EIP1559Configurable.sol

17:     /// @param gasExcess The new gas excess. 
18:     event ConfigAndExcessChanged(Config config, uint64 gasExcess);
19: 
```
[17](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L17-L19)

```solidity
📁 File: contracts/bridge/IBridge.sol

68:     /// @param message The message. 
69:     event MessageSent(bytes32 indexed msgHash, Message message);
70: 

74:     /// @param isRecall True if the message is a recall. 
75:     event MessageReceived(bytes32 indexed msgHash, Message message, bool isRecall);
76: 

78:     /// @param msgHash The hash of the message. 
79:     event MessageRecalled(bytes32 indexed msgHash);
80: 

82:     /// @param msgHash The hash of the message. 
83:     event MessageExecuted(bytes32 indexed msgHash);
84: 

86:     /// @param msgHash The hash of the message. 
87:     event MessageRetried(bytes32 indexed msgHash);
88: 

91:     /// @param status The new status of the message. 
92:     event MessageStatusChanged(bytes32 indexed msgHash, Status status);
93: 

96:     /// @param suspended True if the message is suspended. 
97:     event MessageSuspended(bytes32 msgHash, bool suspended);
98: 

101:     /// @param banned True if the address is banned. 
102:     event AddressBanned(address indexed addr, bool banned);
103: 
```
[68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L68-L70), [74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L74-L76), [78](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L78-L80), [82](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L82-L84), [86](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L86-L88), [91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L91-L93), [96](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L96-L98), [101](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L101-L103)

```solidity
📁 File: contracts/common/AddressManager.sol

20:     /// @param oldAddress The old address. 
21:     event AddressSet(
22:         uint64 indexed chainId, bytes32 indexed name, address newAddress, address oldAddress
```
[20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L20-L22)

```solidity
📁 File: contracts/common/EssentialContract.sol

28:     /// @param account The account that paused the contract. 
29:     event Paused(address account);
30: 

32:     /// @param account The account that unpaused the contract. 
33:     event Unpaused(address account);
34: 
```
[28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L28-L30), [32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L32-L34)

```solidity
📁 File: contracts/signal/ISignalService.sol

35:     /// @param signal The signal for this chain data. 
36:     event ChainDataSynced(
37:         uint64 indexed chainId,

48:     /// @param value The value of the signal. 
49:     event SignalSent(address app, bytes32 signal, bytes32 slot, bytes32 value);
50: 

53:     /// @param authrized True if authorized, false otherwise. 
54:     event Authorized(address indexed addr, bool authrized);
55: 
```
[35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L35-L37), [48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L48-L50), [53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L53-L55)

```solidity
📁 File: contracts/tokenvault/BaseNFTVault.sol

68:     /// @param ctokenName The name of the canonical token. 
69:     event BridgedTokenDeployed(
70:         uint64 indexed chainId,

85:     /// @param amounts The amounts of the tokens. 
86:     event TokenSent(
87:         bytes32 indexed msgHash,

103:     /// @param amounts The amounts of the tokens. 
104:     event TokenReleased(
105:         bytes32 indexed msgHash,

121:     /// @param amounts The amounts of the tokens. 
122:     event TokenReceived(
123:         bytes32 indexed msgHash,
```
[68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L68-L70), [85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L85-L87), [103](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L103-L105), [121](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L121-L123)

```solidity
📁 File: contracts/tokenvault/BridgedERC20Base.sol

20:     /// @param inbound If false then signals migrating 'from', true if migrating 'into'. 
21:     event MigrationStatusChanged(address addr, bool inbound);
22: 

26:     /// @param amount The amount of tokens migrated. 
27:     event MigratedTo(address indexed fromToken, address indexed account, uint256 amount);
28: 
```
[20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L20-L22), [26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L26-L28)

```solidity
📁 File: contracts/tokenvault/ERC20Vault.sol

62:     /// @param ctokenDecimal The decimal of the canonical token. 
63:     event BridgedTokenDeployed(
64:         uint256 indexed srcChainId,

79:     /// @param ctokenDecimal The decimal of the canonical token. 
80:     event BridgedTokenChanged(
81:         uint256 indexed srcChainId,

97:     /// @param amount The amount of tokens sent. 
98:     event TokenSent(
99:         bytes32 indexed msgHash,

113:     /// @param amount The amount of tokens released. 
114:     event TokenReleased(
115:         bytes32 indexed msgHash, address indexed from, address ctoken, address token, uint256 amount

125:     /// @param amount The amount of tokens received. 
126:     event TokenReceived(
127:         bytes32 indexed msgHash,
```
[62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L62-L64), [79](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L79-L81), [97](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L97-L99), [113](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L113-L115), [125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L125-L127)

```solidity
📁 File: contracts/verifiers/SgxVerifier.sol

64:     /// @param validSince The time since the instance is valid. 
65:     event InstanceAdded(
66:         uint256 indexed id, address indexed instance, address replaced, uint256 validSince

71:     /// @param instance The address of the SGX instance. 
72:     event InstanceDeleted(uint256 indexed id, address indexed instance);
73: 
```
[64](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L64-L66), [71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L71-L73)

</details>


---
### [NC&#x2011;84] NatSpec: Event missing NatSpec `@param` tag
<details>
<summary><i>There are 37 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoEvents.sol

/// @audit Missing @param for `blockId`, `assignedProver`, `livenessBond`, `depositsProcessed`
21:     event BlockProposed( 
22:         uint256 indexed blockId,
23:         address indexed assignedProver,
24:         uint96 livenessBond,
25:         TaikoData.BlockMetadata meta,
26:         TaikoData.EthDeposit[] depositsProcessed
27:     );

/// @audit Missing @param for `blockId`, `assignedProver`, `blockHash`, `stateRoot`
37:     event BlockVerified( 
38:         uint256 indexed blockId,
39:         address indexed assignedProver,
40:         address indexed prover,
41:         bytes32 blockHash,
42:         bytes32 stateRoot,
43:         uint16 tier,
44:         uint8 contestations
45:     );

/// @audit Missing @param for `blockId`, `validityBond`
53:     event TransitionProved( 
54:         uint256 indexed blockId,
55:         TaikoData.Transition tran,
56:         address prover,
57:         uint96 validityBond,
58:         uint16 tier
59:     );

/// @audit Missing @param for `blockId`, `contestBond`
67:     event TransitionContested( 
68:         uint256 indexed blockId,
69:         TaikoData.Transition tran,
70:         address contester,
71:         uint96 contestBond,
72:         uint16 tier
73:     );

/// @audit Missing @param for all event parameters
77:     event BlobCached(bytes32 blobHash); 
```
[21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L21-L27), [37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L37-L45), [53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L53-L59), [67](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L67-L73), [77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L77)

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

/// @audit Missing @param for `assignedProver`
46:     event BlockAssigned( 
47:         address indexed assignedProver, TaikoData.BlockMetadata meta, ProverAssignment assignment
48:     );
```
[46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L46-L48)

```solidity
📁 File: contracts/L1/libs/LibDepositing.sol

/// @audit Missing @param for all event parameters
19:     event EthDeposited(TaikoData.EthDeposit deposit); 
```
[19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L19)

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

/// @audit Missing @param for `blockId`, `assignedProver`, `livenessBond`, `depositsProcessed`
31:     event BlockProposed( 
32:         uint256 indexed blockId,
33:         address indexed assignedProver,
34:         uint96 livenessBond,
35:         TaikoData.BlockMetadata meta,
36:         TaikoData.EthDeposit[] depositsProcessed
37:     );

/// @audit Missing @param for all event parameters
41:     event BlobCached(bytes32 blobHash); 
```
[31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L31-L37), [41](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L41)

```solidity
📁 File: contracts/L1/libs/LibProving.sol

/// @audit Missing @param for `blockId`, `validityBond`
32:     event TransitionProved( 
33:         uint256 indexed blockId,
34:         TaikoData.Transition tran,
35:         address prover,
36:         uint96 validityBond,
37:         uint16 tier
38:     );

/// @audit Missing @param for `blockId`, `contestBond`
46:     event TransitionContested( 
47:         uint256 indexed blockId,
48:         TaikoData.Transition tran,
49:         address contester,
50:         uint96 contestBond,
51:         uint16 tier
52:     );
```
[32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L32-L38), [46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L46-L52)

```solidity
📁 File: contracts/L1/libs/LibVerifying.sol

/// @audit Missing @param for `blockId`, `assignedProver`, `blockHash`, `stateRoot`
28:     event BlockVerified( 
29:         uint256 indexed blockId,
30:         address indexed assignedProver,
31:         address indexed prover,
32:         bytes32 blockHash,
33:         bytes32 stateRoot,
34:         uint16 tier,
35:         uint8 contestations
36:     );
```
[28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L28-L36)

```solidity
📁 File: contracts/L1/provers/GuardianProver.sol

/// @audit Missing @param for `blockId`, `blockHash`
18:     event GuardianApproval( 
19:         address indexed addr, uint256 indexed blockId, bytes32 blockHash, bool approved
20:     );
```
[18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L18-L20)

```solidity
📁 File: contracts/L1/provers/Guardians.sol

/// @audit Missing @param for all event parameters
43:     event Approved(uint256 indexed operationId, uint256 approvalBits, bool proofSubmitted); 
```
[43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L43)

```solidity
📁 File: contracts/L2/CrossChainOwned.sol

/// @audit Missing @param for `txId`
26:     event TransactionExecuted(uint64 indexed txId, bytes4 indexed selector); 
```
[26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L26)

```solidity
📁 File: contracts/L2/TaikoL2.sol

/// @audit Missing @param for all event parameters
57:     event Anchored(bytes32 parentHash, uint64 gasExcess); 
```
[57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L57)

```solidity
📁 File: contracts/L2/TaikoL2EIP1559Configurable.sol

/// @audit Missing @param for `gasExcess`
18:     event ConfigAndExcessChanged(Config config, uint64 gasExcess); 
```
[18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L18)

```solidity
📁 File: contracts/bridge/IBridge.sol

/// @audit Missing @param for `msgHash`
69:     event MessageSent(bytes32 indexed msgHash, Message message); 

/// @audit Missing @param for `msgHash`, `isRecall`
75:     event MessageReceived(bytes32 indexed msgHash, Message message, bool isRecall); 

/// @audit Missing @param for all event parameters
79:     event MessageRecalled(bytes32 indexed msgHash); 

/// @audit Missing @param for all event parameters
83:     event MessageExecuted(bytes32 indexed msgHash); 

/// @audit Missing @param for all event parameters
87:     event MessageRetried(bytes32 indexed msgHash); 

/// @audit Missing @param for `msgHash`
92:     event MessageStatusChanged(bytes32 indexed msgHash, Status status); 

/// @audit Missing @param for `msgHash`
97:     event MessageSuspended(bytes32 msgHash, bool suspended); 
```
[69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L69), [75](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L75), [79](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L79), [83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L83), [87](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L87), [92](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L92), [97](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L97)

```solidity
📁 File: contracts/common/AddressManager.sol

/// @audit Missing @param for `chainId`, `newAddress`, `oldAddress`
21:     event AddressSet( 
22:         uint64 indexed chainId, bytes32 indexed name, address newAddress, address oldAddress
23:     );
```
[21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L21-L23)

```solidity
📁 File: contracts/signal/ISignalService.sol

/// @audit Missing @param for `chainId`, `blockId`
36:     event ChainDataSynced( 
37:         uint64 indexed chainId,
38:         uint64 indexed blockId,
39:         bytes32 indexed kind,
40:         bytes32 data,
41:         bytes32 signal
42:     );
```
[36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L36-L42)

```solidity
📁 File: contracts/tokenvault/BaseNFTVault.sol

/// @audit Missing @param for `chainId`, `ctokenSymbol`, `ctokenName`
69:     event BridgedTokenDeployed( 
70:         uint64 indexed chainId,
71:         address indexed ctoken,
72:         address indexed btoken,
73:         string ctokenSymbol,
74:         string ctokenName
75:     );

/// @audit Missing @param for `msgHash`, `destChainId`, `tokenIds`
86:     event TokenSent( 
87:         bytes32 indexed msgHash,
88:         address indexed from,
89:         address indexed to,
90:         uint64 destChainId,
91:         address ctoken,
92:         address token,
93:         uint256[] tokenIds,
94:         uint256[] amounts
95:     );

/// @audit Missing @param for `msgHash`, `tokenIds`
104:     event TokenReleased( 
105:         bytes32 indexed msgHash,
106:         address indexed from,
107:         address ctoken,
108:         address token,
109:         uint256[] tokenIds,
110:         uint256[] amounts
111:     );

/// @audit Missing @param for `msgHash`, `srcChainId`, `tokenIds`
122:     event TokenReceived( 
123:         bytes32 indexed msgHash,
124:         address indexed from,
125:         address indexed to,
126:         uint64 srcChainId,
127:         address ctoken,
128:         address token,
129:         uint256[] tokenIds,
130:         uint256[] amounts
131:     );
```
[69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L69-L75), [86](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L86-L95), [104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L104-L111), [122](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L122-L131)

```solidity
📁 File: contracts/tokenvault/BridgedERC20Base.sol

/// @audit Missing @param for `fromToken`
27:     event MigratedTo(address indexed fromToken, address indexed account, uint256 amount); 
```
[27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L27)

```solidity
📁 File: contracts/tokenvault/ERC20Vault.sol

/// @audit Missing @param for `srcChainId`, `ctokenSymbol`, `ctokenName`, `ctokenDecimal`
63:     event BridgedTokenDeployed( 
64:         uint256 indexed srcChainId,
65:         address indexed ctoken,
66:         address indexed btoken,
67:         string ctokenSymbol,
68:         string ctokenName,
69:         uint8 ctokenDecimal
70:     );

/// @audit Missing @param for `srcChainId`, `btokenOld`, `btokenNew`, `ctokenSymbol`, `ctokenName`, `ctokenDecimal`
80:     event BridgedTokenChanged( 
81:         uint256 indexed srcChainId,
82:         address indexed ctoken,
83:         address btokenOld,
84:         address btokenNew,
85:         string ctokenSymbol,
86:         string ctokenName,
87:         uint8 ctokenDecimal
88:     );

/// @audit Missing @param for `msgHash`, `destChainId`
98:     event TokenSent( 
99:         bytes32 indexed msgHash,
100:         address indexed from,
101:         address indexed to,
102:         uint64 destChainId,
103:         address ctoken,
104:         address token,
105:         uint256 amount
106:     );

/// @audit Missing @param for `msgHash`
114:     event TokenReleased( 
115:         bytes32 indexed msgHash, address indexed from, address ctoken, address token, uint256 amount
116:     );

/// @audit Missing @param for `msgHash`, `srcChainId`
126:     event TokenReceived( 
127:         bytes32 indexed msgHash,
128:         address indexed from,
129:         address indexed to,
130:         uint64 srcChainId,
131:         address ctoken,
132:         address token,
133:         uint256 amount
134:     );
```
[63](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L63-L70), [80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L80-L88), [98](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L98-L106), [114](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L114-L116), [126](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L126-L134)

```solidity
📁 File: contracts/verifiers/SgxVerifier.sol

/// @audit Missing @param for `validSince`
65:     event InstanceAdded( 
66:         uint256 indexed id, address indexed instance, address replaced, uint256 validSince
67:     );
```
[65](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L65-L67)

</details>


---
### [NC&#x2011;85] NatSpec: File is missing NatSpec Documentation
<details>
<summary><i>There are 2 instances of this issue:</i></summary>

```solidity
📁 File: contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol

1: // SPDX-License-Identifier: MIT OR Apache-2.0 
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L1)

```solidity
📁 File: contracts/thirdparty/solmate/LibFixedPointMath.sol

1: // SPDX-License-Identifier: MIT 
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L1)

</details>


---
### [NC&#x2011;86] NatSpec: Function declarations should have `@notice` tags
`@notice` is used to explain to end users what the function does, and the compiler interprets `///` or `/**` comments as this tag if one was't explicitly provided

<details>
<summary><i>There are 40 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoL1.sol

220:     function _authorizePause(address) 
221:         internal
222:         view
223:         virtual
224:         override
225:         onlyFromOwnerOrNamed("chain_pauser")
226:     { }
```
[220](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L220-L226)

```solidity
📁 File: contracts/L1/TaikoToken.sol

83:     function _beforeTokenTransfer( 
84:         address _from,
85:         address _to,
86:         uint256 _amount
87:     )
88:         internal
89:         override(ERC20Upgradeable, ERC20SnapshotUpgradeable)
90:     {
```
[83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L83-L90)

```solidity
📁 File: contracts/L1/gov/TaikoGovernor.sol

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
[48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L48-L57), [89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L89-L94), [99](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L99-L104), [127](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L127-L136), [140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L140-L149), [153](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L153-L158)

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

164:     function _getProverFee( 
165:         TaikoData.TierFee[] memory _tierFees,
166:         uint16 _tierId
167:     )
168:         private
169:         pure
170:         returns (uint256)
171:     {
```
[164](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L164-L171)

```solidity
📁 File: contracts/L1/libs/LibDepositing.sol

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

149:     function _encodeEthDeposit(address _addr, uint256 _amount) private pure returns (uint256) { 
```
[29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L29-L36), [67](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L67-L74), [122](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L122-L130), [149](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L149)

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

299:     function _isProposerPermitted( 
300:         TaikoData.SlotB memory _slotB,
301:         IAddressResolver _resolver
302:     )
303:         private
304:         view
305:         returns (bool)
306:     {
```
[299](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L299-L306)

```solidity
📁 File: contracts/L1/libs/LibProving.sol

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
```
[91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L91-L101), [269](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L269-L277), [350](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L350-L359), [401](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L401-L410)

```solidity
📁 File: contracts/L1/libs/LibUtils.sol

52:     function getBlock( 
53:         TaikoData.State storage _state,
54:         TaikoData.Config memory _config,
55:         uint64 _blockId
56:     )
57:         external
58:         view
59:         returns (TaikoData.Block storage blk_, uint64 slot_)
60:     {
```
[52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L52-L60)

```solidity
📁 File: contracts/L1/libs/LibVerifying.sol

85:     function verifyBlocks( 
86:         TaikoData.State storage _state,
87:         TaikoData.Config memory _config,
88:         IAddressResolver _resolver,
89:         uint64 _maxBlocksToVerify
90:     )
91:         internal
92:     {

224:     function _syncChainData( 
225:         TaikoData.Config memory _config,
226:         IAddressResolver _resolver,
227:         uint64 _lastVerifiedBlockId,
228:         bytes32 _stateRoot
229:     )
230:         private
231:     {

245:     function _isConfigValid(TaikoData.Config memory _config) private view returns (bool) { 
```
[85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L85-L92), [224](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L224-L231), [245](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L245)

```solidity
📁 File: contracts/L1/provers/Guardians.sol

111:     function approve(uint256 _operationId, bytes32 _hash) internal returns (bool approved_) { 

124:     function deleteApproval(bytes32 _hash) internal { 

128:     function isApproved(uint256 _approvalBits) internal view returns (bool) { 
```
[111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L111), [124](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L124), [128](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L128)

```solidity
📁 File: contracts/common/AddressManager.sol

58:     function _authorizePause(address) internal pure override { 
```
[58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L58)

```solidity
📁 File: contracts/common/AddressResolver.sol

58:     function __AddressResolver_init(address _addressManager) internal virtual onlyInitializing { 
```
[58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L58)

```solidity
📁 File: contracts/common/EssentialContract.sol

109:     function __Essential_init(address _owner) internal virtual { 

114:     function _authorizeUpgrade(address) internal virtual override onlyOwner { } 

116:     function _authorizePause(address) internal virtual onlyOwner { } 

119:     function _storeReentryLock(uint8 _reentry) internal virtual { 

130:     function _loadReentryLock() internal view virtual returns (uint8 reentry_) { 

140:     function _inNonReentrant() internal view returns (bool) { 
```
[109](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L109), [114](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L114), [116](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L116), [119](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L119), [130](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L130), [140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L140)

```solidity
📁 File: contracts/libs/LibAddress.sol

22:     function sendEther(address _to, uint256 _amount, uint256 _gasLimit) internal { 

42:     function sendEther(address _to, uint256 _amount) internal { 

46:     function supportsInterface( 
47:         address _addr,
48:         bytes4 _interfaceId
49:     )
50:         internal
51:         view
52:         returns (bool result_)
53:     {

61:     function isValidSignature( 
62:         address _addr,
63:         bytes32 _hash,
64:         bytes memory _sig
65:     )
66:         internal
67:         view
68:         returns (bool)
69:     {

77:     function isSenderEOA() internal view returns (bool) { 
```
[22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L22), [42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L42), [46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L46-L53), [61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L61-L69), [77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L77)

```solidity
📁 File: contracts/libs/LibMath.sol

12:     function min(uint256 _a, uint256 _b) internal pure returns (uint256) { 

20:     function max(uint256 _a, uint256 _b) internal pure returns (uint256) { 
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibMath.sol#L12), [20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibMath.sol#L20)

</details>


---
### [NC&#x2011;87] NatSpec: Function declarations should have NatSpec descriptions
It is recommended that Solidity contracts are fully annotated using NatSpec for all public interfaces (everything in the ABI). It is clearly stated in the Solidity official documentation. In complex projects such as DeFi, the interpretation of all functions and their arguments and returns is important for code readability and auditability.

<details>
<summary><i>There are 40 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoL1.sol

220:     function _authorizePause(address) 
```
[220](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L220)

```solidity
📁 File: contracts/L1/TaikoToken.sol

83:     function _beforeTokenTransfer( 

94:     function _afterTokenTransfer( 

105:     function _mint( 

115:     function _burn( 
```
[83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L83), [94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L94), [105](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L105), [115](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L115)

```solidity
📁 File: contracts/L1/gov/TaikoGovernor.sol

127:     function _execute( 

140:     function _cancel( 

153:     function _executor() 
```
[127](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L127), [140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L140), [153](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L153)

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

164:     function _getProverFee( 
```
[164](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L164)

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

299:     function _isProposerPermitted( 
```
[299](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L299)

```solidity
📁 File: contracts/L1/libs/LibVerifying.sol

224:     function _syncChainData( 

245:     function _isConfigValid(TaikoData.Config memory _config) private view returns (bool) { 
```
[224](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L224), [245](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L245)

```solidity
📁 File: contracts/L1/provers/Guardians.sol

111:     function approve(uint256 _operationId, bytes32 _hash) internal returns (bool approved_) { 

124:     function deleteApproval(bytes32 _hash) internal { 

128:     function isApproved(uint256 _approvalBits) internal view returns (bool) { 
```
[111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L111), [124](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L124), [128](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L128)

```solidity
📁 File: contracts/L2/TaikoL2.sol

223:     function _calcPublicInputHash(uint256 _blockId) 

252:     function _calc1559BaseFee( 
```
[223](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L223), [252](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L252)

```solidity
📁 File: contracts/common/AddressManager.sol

58:     function _authorizePause(address) internal pure override { 
```
[58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L58)

```solidity
📁 File: contracts/common/EssentialContract.sol

109:     function __Essential_init(address _owner) internal virtual { 

114:     function _authorizeUpgrade(address) internal virtual override onlyOwner { } 

116:     function _authorizePause(address) internal virtual onlyOwner { } 

119:     function _storeReentryLock(uint8 _reentry) internal virtual { 

130:     function _loadReentryLock() internal view virtual returns (uint8 reentry_) { 

140:     function _inNonReentrant() internal view returns (bool) { 
```
[109](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L109), [114](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L114), [116](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L116), [119](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L119), [130](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L130), [140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L140)

```solidity
📁 File: contracts/libs/LibAddress.sol

46:     function supportsInterface( 

61:     function isValidSignature( 

77:     function isSenderEOA() internal view returns (bool) { 
```
[46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L46), [61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L61), [77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L77)

```solidity
📁 File: contracts/signal/SignalService.sol

206:     function _verifyHopProof( 

231:     function _authorizePause(address) internal pure override { 

235:     function _syncChainData( 

253:     function _sendSignal( 

271:     function _cacheChainData( 

298:     function _loadSignalValue( 
```
[206](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L206), [231](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L231), [235](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L235), [253](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L253), [271](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L271), [298](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L298)

```solidity
📁 File: contracts/tokenvault/BridgedERC20.sol

129:     function _mintToken(address _account, uint256 _amount) internal override { 

133:     function _burnToken(address _from, uint256 _amount) internal override { 

152:     function _afterTokenTransfer( 

163:     function _mint( 

173:     function _burn( 
```
[129](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L129), [133](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L133), [152](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L152), [163](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L163), [173](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L173)

```solidity
📁 File: contracts/tokenvault/adapters/USDCAdapter.sol

43:     function _mintToken(address _account, uint256 _amount) internal override { 

47:     function _burnToken(address _from, uint256 _amount) internal override { 
```
[43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L43), [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L47)

</details>


---
### [NC&#x2011;88] NatSpec: Functions missing NatSpec `@dev` tag
<details>
<summary><i>There are 40 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/ITaikoL1.sol

13:     /// @return deposits_ The Ether deposits processed. 
14:     function proposeBlock(
15:         bytes calldata _params,

26:     /// TaikoData.TierProof) tuple. 
27:     function proveBlock(uint64 _blockId, bytes calldata _input) external;
28: 

30:     /// @param _maxBlocksToVerify Max number of blocks to verify. 
31:     function verifyBlocks(uint64 _maxBlocksToVerify) external;
32: 
```
[13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/ITaikoL1.sol#L13-L15), [26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/ITaikoL1.sol#L26-L28), [30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/ITaikoL1.sol#L30-L32)

```solidity
📁 File: contracts/L1/gov/TaikoGovernor.sol

30:     /// @param _timelock The timelock contract address. 
31:     function init(
32:         address _owner,

110:     /// @return The duration of the voting delay. 
111:     function votingDelay() public pure override returns (uint256) {
112:         return 7200; // 1 day

116:     /// @return The duration of the voting period. 
117:     function votingPeriod() public pure override returns (uint256) {
118:         return 50_400; // 1 week

122:     /// @return The number of votes required. 
123:     function proposalThreshold() public pure override returns (uint256) {
124:         return 1_000_000_000 ether / 10_000; // 0.01% of Taiko Token

126:  
127:     function _execute(
128:         uint256 _proposalId,

139:  
140:     function _cancel(
141:         address[] memory _targets,

152:  
153:     function _executor()
154:         internal
```
[30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L30-L32), [110](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L110-L112), [116](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L116-L118), [122](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L122-L124), [126](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L126-L128), [139](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L139-L141), [152](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L152-L154)

```solidity
📁 File: contracts/L1/gov/TaikoTimelockController.sol

14:     /// @param _minDelay The minimal delay. 
15:     function init(address _owner, uint256 _minDelay) external initializer {
16:         __Essential_init(_owner);
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L14-L16)

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

56:     /// @param _addressManager The address of the {AddressManager} contract. 
57:     function init(address _owner, address _addressManager) external initializer {
58:         __Essential_init(_owner, _addressManager);

61:     /// @inheritdoc IHook 
62:     function onBlockProposed(
63:         TaikoData.Block memory _blk,

136:     /// @return The hash of the prover assignment. 
137:     function hashAssignment(
138:         ProverAssignment memory _assignment,

163:  
164:     function _getProverFee(
165:         TaikoData.TierFee[] memory _tierFees,
```
[56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L56-L58), [61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L61-L63), [136](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L136-L138), [163](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L163-L165)

```solidity
📁 File: contracts/L1/hooks/IHook.sol

12:     /// @param _data The data of the proposed block. 
13:     function onBlockProposed(
14:         TaikoData.Block memory _blk,
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/IHook.sol#L12-L14)

```solidity
📁 File: contracts/common/AddressManager.sol

29:     /// @param _owner The owner of this contract. msg.sender will be used if this value is zero. 
30:     function init(address _owner) external initializer {
31:         __Essential_init(_owner);

37:     /// @param _newAddress The Ethereum address to be mapped. 
38:     function setAddress(
39:         uint64 _chainId,

53:     /// @inheritdoc IAddressManager 
54:     function getAddress(uint64 _chainId, bytes32 _name) public view override returns (address) {
55:         return __addresses[_chainId][_name];

57:  
58:     function _authorizePause(address) internal pure override {
59:         revert AM_UNSUPPORTED();
```
[29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L29-L31), [37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L37-L39), [53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L53-L55), [57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L57-L59)

```solidity
📁 File: contracts/common/AddressResolver.sol

29:     /// @inheritdoc IAddressResolver 
30:     function resolve(
31:         bytes32 _name,

42:     /// @inheritdoc IAddressResolver 
43:     function resolve(
44:         uint64 _chainId,
```
[29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L29-L31), [42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L42-L44)

```solidity
📁 File: contracts/common/EssentialContract.sol

63:     /// @custom:oz-upgrades-unsafe-allow constructor 
64:     constructor() {
65:         _disableInitializers();

68:     /// @notice Pauses the contract. 
69:     function pause() public virtual whenNotPaused {
70:         __paused = _TRUE;

77:     /// @notice Unpauses the contract. 
78:     function unpause() public virtual whenPaused {
79:         __paused = _FALSE;

87:     /// @return True if paused, false otherwise. 
88:     function paused() public view returns (bool) {
89:         return __paused == _TRUE;

94:     /// @param _addressManager The address of the {AddressManager} contract. 
95:     function __Essential_init(
96:         address _owner,

108:  
109:     function __Essential_init(address _owner) internal virtual {
110:         _transferOwnership(_owner == address(0) ? msg.sender : _owner);

113:  
114:     function _authorizeUpgrade(address) internal virtual override onlyOwner { }
115: 
116:     function _authorizePause(address) internal virtual onlyOwner { }
117: 
118:     // Stores the reentry lock
119:     function _storeReentryLock(uint8 _reentry) internal virtual {
120:         if (block.chainid == 1) {

129:     // Loads the reentry lock 
130:     function _loadReentryLock() internal view virtual returns (uint8 reentry_) {
131:         if (block.chainid == 1) {

139:  
140:     function _inNonReentrant() internal view returns (bool) {
141:         return _loadReentryLock() == _TRUE;
```
[63](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L63-L65), [68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L68-L70), [77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L77-L79), [87](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L87-L89), [94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L94-L96), [108](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L108-L110), [113](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L113-L120), [129](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L129-L131), [139](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L139-L141)

```solidity
📁 File: contracts/common/IAddressResolver.sol

18:     /// @return Address associated with the given name. 
19:     function resolve(
20:         bytes32 _name,

33:     /// chain. 
34:     function resolve(
35:         uint64 _chainId,
```
[18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressResolver.sol#L18-L20), [33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressResolver.sol#L33-L35)

```solidity
📁 File: contracts/libs/Lib4844.sol

29:     /// @param _pointProof The quotient kzg 
30:     function evaluatePoint(
31:         bytes32 _blobHash,
```
[29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L29-L31)

```solidity
📁 File: contracts/libs/LibAddress.sol

45:  
46:     function supportsInterface(
47:         address _addr,

60:  
61:     function isValidSignature(
62:         address _addr,

76:  
77:     function isSenderEOA() internal view returns (bool) {
78:         return msg.sender == tx.origin;
```
[45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L45-L47), [60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L60-L62), [76](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L76-L78)

```solidity
📁 File: contracts/libs/LibTrieProof.sol

33:     /// @return storageRoot_ The account's storage root 
34:     function verifyMerkleProof(
35:         bytes32 _rootHash,
```
[33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L33-L35)

</details>


---
### [NC&#x2011;89] NatSpec: Functions missing NatSpec `@param` tag
It is recommended that Solidity contracts are fully annotated using NatSpec for all public interfaces (everything in the ABI). It is clearly stated in the Solidity official documentation. In complex projects such as DeFi, the interpretation of all functions and their arguments and returns is important for code readability and auditability.

<details>
<summary><i>There are 40 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/ITaikoL1.sol

/// @audit Missing @param for `_txList`
14:     function proposeBlock( 

/// @audit Missing @param for `_blockId`
27:     function proveBlock(uint64 _blockId, bytes calldata _input) external; 

/// @audit Missing @param for all function parameters
31:     function verifyBlocks(uint64 _maxBlocksToVerify) external; 
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/ITaikoL1.sol#L14), [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/ITaikoL1.sol#L27), [31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/ITaikoL1.sol#L31)

```solidity
📁 File: contracts/L1/gov/TaikoGovernor.sol

/// @audit Missing @param for all function parameters
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

/// @audit Missing @param for all function parameters
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

/// @audit Missing @param for all function parameters
89:     function supportsInterface(bytes4 _interfaceId) 
90:         public
91:         view
92:         override(GovernorUpgradeable, GovernorTimelockControlUpgradeable, IERC165Upgradeable)
93:         returns (bool)
94:     {

/// @audit Missing @param for all function parameters
99:     function state(uint256 _proposalId) 
100:         public
101:         view
102:         override(IGovernorUpgradeable, GovernorUpgradeable, GovernorTimelockControlUpgradeable)
103:         returns (ProposalState)
104:     {

/// @audit Missing @param for all function parameters
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

/// @audit Missing @param for all function parameters
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
```
[48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L48-L57), [69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L69-L80), [89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L89-L94), [99](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L99-L104), [127](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L127-L136), [140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L140-L149)

```solidity
📁 File: contracts/L1/gov/TaikoTimelockController.sol

/// @audit Missing @param for `_minDelay`
15:     function init(address _owner, uint256 _minDelay) external initializer { 
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L15)

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

/// @audit Missing @param for `_addressManager`
57:     function init(address _owner, address _addressManager) external initializer { 

/// @audit Missing @param for `_taikoL1Address`, `_blobHash`
137:     function hashAssignment( 
138:         ProverAssignment memory _assignment,
139:         address _taikoL1Address,
140:         bytes32 _blobHash
141:     )
142:         public
143:         view
144:         returns (bytes32)
145:     {

/// @audit Missing @param for all function parameters
164:     function _getProverFee( 
165:         TaikoData.TierFee[] memory _tierFees,
166:         uint16 _tierId
167:     )
168:         private
169:         pure
170:         returns (uint256)
171:     {
```
[57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L57), [137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L137-L145), [164](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L164-L171)

```solidity
📁 File: contracts/L1/libs/LibDepositing.sol

/// @audit Missing @param for all function parameters
67:     function processDeposits( 
68:         TaikoData.State storage _state,
69:         TaikoData.Config memory _config,
70:         address _feeRecipient
71:     )
72:         internal
73:         returns (TaikoData.EthDeposit[] memory deposits_)
74:     {

/// @audit Missing @param for all function parameters
122:     function canDepositEthToL2( 
123:         TaikoData.State storage _state,
124:         TaikoData.Config memory _config,
125:         uint256 _amount
126:     )
127:         internal
128:         view
129:         returns (bool)
130:     {
```
[67](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L67-L74), [122](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L122-L130)

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

/// @audit Missing @param for `_txList`
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

/// @audit Missing @param for `_blobHash`
287:     function isBlobReusable( 
288:         TaikoData.State storage _state,
289:         TaikoData.Config memory _config,
290:         bytes32 _blobHash
291:     )
292:         internal
293:         view
294:         returns (bool)
295:     {

/// @audit Missing @param for all function parameters
299:     function _isProposerPermitted( 
300:         TaikoData.SlotB memory _slotB,
301:         IAddressResolver _resolver
302:     )
303:         private
304:         view
305:         returns (bool)
306:     {
```
[68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L68-L77), [287](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L287-L295), [299](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L299-L306)

```solidity
📁 File: contracts/L1/libs/LibProving.sol

/// @audit Missing @param for all function parameters
269:     function _createTransition( 
270:         TaikoData.State storage _state,
271:         TaikoData.Block storage _blk,
272:         TaikoData.Transition memory _tran,
273:         uint64 slot
274:     )
275:         private
276:         returns (uint32 tid_, TaikoData.TransitionState storage ts_)
277:     {

/// @audit Missing @param for all function parameters
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

/// @audit Missing @param for all function parameters
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
```
[269](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L269-L277), [350](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L350-L359), [401](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L401-L410)

```solidity
📁 File: contracts/L1/libs/LibUtils.sol

/// @audit Missing @param for `_blockId`, `_parentHash`
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

/// @audit Missing @param for `_blockId`
52:     function getBlock( 
53:         TaikoData.State storage _state,
54:         TaikoData.Config memory _config,
55:         uint64 _blockId
56:     )
57:         external
58:         view
59:         returns (TaikoData.Block storage blk_, uint64 slot_)
60:     {
```
[23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L23-L32), [52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L52-L60)

```solidity
📁 File: contracts/common/AddressManager.sol

/// @audit Missing @param for `_chainId`, `_newAddress`
38:     function setAddress( 
39:         uint64 _chainId,
40:         bytes32 _name,
41:         address _newAddress
42:     )
43:         external
44:         virtual
45:         onlyOwner
46:     {

/// @audit Missing @param for all function parameters
58:     function _authorizePause(address) internal pure override { 
```
[38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L38-L46), [58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L58)

```solidity
📁 File: contracts/common/AddressResolver.sol

/// @audit Missing @param for all function parameters
58:     function __AddressResolver_init(address _addressManager) internal virtual onlyInitializing { 

/// @audit Missing @param for `_chainId`, `_allowZeroAddress`
72:     function _resolve( 
73:         uint64 _chainId,
74:         bytes32 _name,
75:         bool _allowZeroAddress
76:     )
77:         private
78:         view
79:         returns (address payable addr_)
80:     {
```
[58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L58), [72](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L72-L80)

```solidity
📁 File: contracts/common/EssentialContract.sol

/// @audit Missing @param for `_addressManager`
95:     function __Essential_init( 
96:         address _owner,
97:         address _addressManager
98:     )
99:         internal
100:         virtual
101:         onlyInitializing
102:     {

/// @audit Missing @param for all function parameters
109:     function __Essential_init(address _owner) internal virtual { 

/// @audit Missing @param for all function parameters
114:     function _authorizeUpgrade(address) internal virtual override onlyOwner { } 

/// @audit Missing @param for all function parameters
116:     function _authorizePause(address) internal virtual onlyOwner { } 

/// @audit Missing @param for all function parameters
119:     function _storeReentryLock(uint8 _reentry) internal virtual { 
```
[95](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L95-L102), [109](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L109), [114](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L114), [116](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L116), [119](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L119)

```solidity
📁 File: contracts/common/IAddressManager.sol

/// @audit Missing @param for `_chainId`
14:     function getAddress(uint64 _chainId, bytes32 _name) external view returns (address); 
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressManager.sol#L14)

```solidity
📁 File: contracts/common/IAddressResolver.sol

/// @audit Missing @param for `_allowZeroAddress`
19:     function resolve( 

/// @audit Missing @param for `_chainId`, `_allowZeroAddress`
34:     function resolve( 
```
[19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressResolver.sol#L19), [34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressResolver.sol#L34)

```solidity
📁 File: contracts/libs/Lib4844.sol

/// @audit Missing @param for `_blobHash`, `_pointProof`
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
[30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L30-L39)

```solidity
📁 File: contracts/libs/LibAddress.sol

/// @audit Missing @param for `_gasLimit`
22:     function sendEther(address _to, uint256 _amount, uint256 _gasLimit) internal { 

/// @audit Missing @param for all function parameters
46:     function supportsInterface( 
47:         address _addr,
48:         bytes4 _interfaceId
49:     )
50:         internal
51:         view
52:         returns (bool result_)
53:     {

/// @audit Missing @param for all function parameters
61:     function isValidSignature( 
62:         address _addr,
63:         bytes32 _hash,
64:         bytes memory _sig
65:     )
66:         internal
67:         view
68:         returns (bool)
69:     {
```
[22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L22), [46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L46-L53), [61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L61-L69)

```solidity
📁 File: contracts/libs/LibTrieProof.sol

/// @audit Missing @param for `_rootHash`, `_accountProof`, `_storageProof`
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
45:     {
```
[34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L34-L45)

</details>


---
### [NC&#x2011;90] NatSpec: Functions missing NatSpec `@return` tag
It is recommended that Solidity contracts are fully annotated using NatSpec for all public interfaces (everything in the ABI). It is clearly stated in the Solidity official documentation. In complex projects such as DeFi, the interpretation of all functions and their arguments and returns is important for code readability and auditability.

<details>
<summary><i>There are 40 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoL1.sol

/// @audit Missing @return for all function parameters
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

/// @audit Missing @return for all function parameters
137:     function isBlobReusable(bytes32 _blobHash) public view returns (bool) { 

/// @audit Missing @return for all function parameters
186:     function getConfig() public view virtual override returns (TaikoData.Config memory) { 
```
[55](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L55-L64), [137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L137), [186](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L186)

```solidity
📁 File: contracts/L1/gov/TaikoGovernor.sol

/// @audit Missing @return for all function parameters
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

/// @audit Missing @return for all function parameters
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

/// @audit Missing @return for all function parameters
89:     function supportsInterface(bytes4 _interfaceId) 
90:         public
91:         view
92:         override(GovernorUpgradeable, GovernorTimelockControlUpgradeable, IERC165Upgradeable)
93:         returns (bool)
94:     {

/// @audit Missing @return for all function parameters
99:     function state(uint256 _proposalId) 
100:         public
101:         view
102:         override(IGovernorUpgradeable, GovernorUpgradeable, GovernorTimelockControlUpgradeable)
103:         returns (ProposalState)
104:     {

/// @audit Missing @return for all function parameters
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

/// @audit Missing @return for all function parameters
153:     function _executor() 
154:         internal
155:         view
156:         override(GovernorUpgradeable, GovernorTimelockControlUpgradeable)
157:         returns (address)
158:     {
```
[48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L48-L57), [69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L69-L80), [89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L89-L94), [99](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L99-L104), [140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L140-L149), [153](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L153-L158)

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

/// @audit Missing @return for all function parameters
164:     function _getProverFee( 
165:         TaikoData.TierFee[] memory _tierFees,
166:         uint16 _tierId
167:     )
168:         private
169:         pure
170:         returns (uint256)
171:     {
```
[164](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L164-L171)

```solidity
📁 File: contracts/L1/libs/LibDepositing.sol

/// @audit Missing @return for all function parameters
67:     function processDeposits( 
68:         TaikoData.State storage _state,
69:         TaikoData.Config memory _config,
70:         address _feeRecipient
71:     )
72:         internal
73:         returns (TaikoData.EthDeposit[] memory deposits_)
74:     {

/// @audit Missing @return for all function parameters
122:     function canDepositEthToL2( 
123:         TaikoData.State storage _state,
124:         TaikoData.Config memory _config,
125:         uint256 _amount
126:     )
127:         internal
128:         view
129:         returns (bool)
130:     {
```
[67](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L67-L74), [122](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L122-L130)

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

/// @audit Missing @return for all function parameters
299:     function _isProposerPermitted( 
300:         TaikoData.SlotB memory _slotB,
301:         IAddressResolver _resolver
302:     )
303:         private
304:         view
305:         returns (bool)
306:     {
```
[299](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L299-L306)

```solidity
📁 File: contracts/L1/libs/LibProving.sol

/// @audit Missing @return for all function parameters
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

/// @audit Missing @return for all function parameters
269:     function _createTransition( 
270:         TaikoData.State storage _state,
271:         TaikoData.Block storage _blk,
272:         TaikoData.Transition memory _tran,
273:         uint64 slot
274:     )
275:         private
276:         returns (uint32 tid_, TaikoData.TransitionState storage ts_)
277:     {
```
[91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L91-L101), [269](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L269-L277)

```solidity
📁 File: contracts/L1/libs/LibUtils.sol

/// @audit Missing @return for all function parameters
52:     function getBlock( 
53:         TaikoData.State storage _state,
54:         TaikoData.Config memory _config,
55:         uint64 _blockId
56:     )
57:         external
58:         view
59:         returns (TaikoData.Block storage blk_, uint64 slot_)
60:     {

/// @audit Missing @return for all function parameters
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
```
[52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L52-L60), [70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L70-L79)

```solidity
📁 File: contracts/L1/libs/LibVerifying.sol

/// @audit Missing @return for all function parameters
245:     function _isConfigValid(TaikoData.Config memory _config) private view returns (bool) { 
```
[245](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L245)

```solidity
📁 File: contracts/L1/provers/Guardians.sol

/// @audit Missing @return for all function parameters
111:     function approve(uint256 _operationId, bytes32 _hash) internal returns (bool approved_) { 

/// @audit Missing @return for all function parameters
128:     function isApproved(uint256 _approvalBits) internal view returns (bool) { 
```
[111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L111), [128](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L128)

```solidity
📁 File: contracts/L1/tiers/DevnetTierProvider.sol

/// @audit Missing @return for all function parameters
20:     function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) { 

/// @audit Missing @return for all function parameters
47:     function getTierIds() public pure override returns (uint16[] memory tiers_) { 

/// @audit Missing @return for all function parameters
54:     function getMinTier(uint256) public pure override returns (uint16) { 
```
[20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L20), [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L47), [54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L54)

```solidity
📁 File: contracts/L1/tiers/MainnetTierProvider.sol

/// @audit Missing @return for all function parameters
20:     function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) { 

/// @audit Missing @return for all function parameters
58:     function getTierIds() public pure override returns (uint16[] memory tiers_) { 

/// @audit Missing @return for all function parameters
66:     function getMinTier(uint256 _rand) public pure override returns (uint16) { 
```
[20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L20), [58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L58), [66](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L66)

```solidity
📁 File: contracts/L1/tiers/TestnetTierProvider.sol

/// @audit Missing @return for all function parameters
20:     function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) { 

/// @audit Missing @return for all function parameters
58:     function getTierIds() public pure override returns (uint16[] memory tiers_) { 

/// @audit Missing @return for all function parameters
66:     function getMinTier(uint256 _rand) public pure override returns (uint16) { 
```
[20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L20), [58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L58), [66](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L66)

```solidity
📁 File: contracts/L2/Lib1559Math.sol

/// @audit Missing @return for all function parameters
16:     function basefee( 
17:         uint256 _gasExcess,
18:         uint256 _adjustmentFactor
19:     )
20:         internal
21:         pure
22:         returns (uint256)
23:     {

/// @audit Missing @return for all function parameters
33:     function _ethQty( 
34:         uint256 _gasExcess,
35:         uint256 _adjustmentFactor
36:     )
37:         private
38:         pure
39:         returns (uint256)
40:     {
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L16-L23), [33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L33-L40)

```solidity
📁 File: contracts/common/AddressManager.sol

/// @audit Missing @return for all function parameters
54:     function getAddress(uint64 _chainId, bytes32 _name) public view override returns (address) { 
```
[54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L54)

```solidity
📁 File: contracts/common/AddressResolver.sol

/// @audit Missing @return for all function parameters
30:     function resolve( 
31:         bytes32 _name,
32:         bool _allowZeroAddress
33:     )
34:         public
35:         view
36:         virtual
37:         returns (address payable)
38:     {

/// @audit Missing @return for all function parameters
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
```
[30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L30-L38), [43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L43-L52)

```solidity
📁 File: contracts/common/EssentialContract.sol

/// @audit Missing @return for all function parameters
130:     function _loadReentryLock() internal view virtual returns (uint8 reentry_) { 

/// @audit Missing @return for all function parameters
140:     function _inNonReentrant() internal view returns (bool) { 
```
[130](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L130), [140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L140)

```solidity
📁 File: contracts/libs/LibAddress.sol

/// @audit Missing @return for all function parameters
46:     function supportsInterface( 
47:         address _addr,
48:         bytes4 _interfaceId
49:     )
50:         internal
51:         view
52:         returns (bool result_)
53:     {

/// @audit Missing @return for all function parameters
61:     function isValidSignature( 
62:         address _addr,
63:         bytes32 _hash,
64:         bytes memory _sig
65:     )
66:         internal
67:         view
68:         returns (bool)
69:     {

/// @audit Missing @return for all function parameters
77:     function isSenderEOA() internal view returns (bool) { 
```
[46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L46-L53), [61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L61-L69), [77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L77)

```solidity
📁 File: contracts/libs/LibTrieProof.sol

/// @audit Missing @return for all function parameters
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
45:     {
```
[34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L34-L45)

</details>


---
### [NC&#x2011;91] NatSpec: Modifier declarations should have NatSpec descriptions
It is recommended that modifiers are fully annotated using NatSpec.

<details>
<summary><i>There are 13 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoL1.sol

28:     modifier whenProvingNotPaused() { 
```
[28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L28)

```solidity
📁 File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

60:     modifier onlyOwner() { 
```
[60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L60)

```solidity
📁 File: contracts/bridge/Bridge.sol

64:     modifier sameChain(uint64 _chainId) { 
```
[64](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L64)

```solidity
📁 File: contracts/common/EssentialContract.sol

46:     modifier nonReentrant() { 

53:     modifier whenPaused() { 

58:     modifier whenNotPaused() { 
```
[46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L46), [53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L53), [58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L58)

```solidity
📁 File: contracts/signal/SignalService.sol

35:     modifier validSender(address _app) { 

40:     modifier nonZeroValue(bytes32 _input) { 
```
[35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L35), [40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L40)

```solidity
📁 File: contracts/team/airdrop/ERC20Airdrop2.sol

39:     modifier ongoingWithdrawals() { 
```
[39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L39)

```solidity
📁 File: contracts/team/airdrop/MerkleClaimable.sol

33:     modifier ongoingClaim() { 
```
[33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L33)

```solidity
📁 File: contracts/tokenvault/BaseNFTVault.sol

140:     modifier withValidOperation(BridgeTransferOp memory _op) { 
```
[140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L140)

```solidity
📁 File: contracts/tokenvault/BaseVault.sol

22:     modifier onlyFromBridge() { 
```
[22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L22)

```solidity
📁 File: contracts/tokenvault/BridgedERC20.sol

37:     modifier onlyOwnerOrSnapshooter() { 
```
[37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L37)

</details>


---
### [NC&#x2011;92] NatSpec: Modifier missing NatSpec `@dev` tag
<details>
<summary><i>There are 13 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoL1.sol

27:  
28:     modifier whenProvingNotPaused() {
29:         if (state.slotB.provingPaused) revert L1_PROVING_PAUSED();
```
[27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L27-L29)

```solidity
📁 File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

59:  
60:     modifier onlyOwner() {
61:         require(msg.sender == owner, "onlyOwner");
```
[59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L59-L61)

```solidity
📁 File: contracts/bridge/Bridge.sol

63:  
64:     modifier sameChain(uint64 _chainId) {
65:         if (_chainId != block.chainid) revert B_INVALID_CHAINID();
```
[63](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L63-L65)

```solidity
📁 File: contracts/common/EssentialContract.sol

45:  
46:     modifier nonReentrant() {
47:         if (_loadReentryLock() == _TRUE) revert REENTRANT_CALL();

52:  
53:     modifier whenPaused() {
54:         if (!paused()) revert INVALID_PAUSE_STATUS();

57:  
58:     modifier whenNotPaused() {
59:         if (paused()) revert INVALID_PAUSE_STATUS();
```
[45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L45-L47), [52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L52-L54), [57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L57-L59)

```solidity
📁 File: contracts/signal/SignalService.sol

34:  
35:     modifier validSender(address _app) {
36:         if (_app == address(0)) revert SS_INVALID_SENDER();

39:  
40:     modifier nonZeroValue(bytes32 _input) {
41:         if (_input == 0) revert SS_INVALID_VALUE();
```
[34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L34-L36), [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L39-L41)

```solidity
📁 File: contracts/team/airdrop/ERC20Airdrop2.sol

38:  
39:     modifier ongoingWithdrawals() {
40:         if (claimEnd > block.timestamp || claimEnd + withdrawalWindow < block.timestamp) {
```
[38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L38-L40)

```solidity
📁 File: contracts/team/airdrop/MerkleClaimable.sol

32:  
33:     modifier ongoingClaim() {
34:         if (
```
[32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L32-L34)

```solidity
📁 File: contracts/tokenvault/BaseNFTVault.sol

139:  
140:     modifier withValidOperation(BridgeTransferOp memory _op) {
141:         if (_op.tokenIds.length != _op.amounts.length) {
```
[139](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L139-L141)

```solidity
📁 File: contracts/tokenvault/BaseVault.sol

21:  
22:     modifier onlyFromBridge() {
23:         if (msg.sender != resolve("bridge", false)) {
```
[21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L21-L23)

```solidity
📁 File: contracts/tokenvault/BridgedERC20.sol

36:  
37:     modifier onlyOwnerOrSnapshooter() {
38:         if (msg.sender != owner() && msg.sender != snapshooter) {
```
[36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L36-L38)

</details>


---
### [NC&#x2011;93] NatSpec: Modifier missing NatSpec `@param` tag
It is recommended that Solidity contracts are fully annotated using NatSpec for all public interfaces (everything in the ABI). It is clearly stated in the Solidity official documentation. In complex projects such as DeFi, the interpretation of all functions and their arguments and returns is important for code readability and auditability.

<details>
<summary><i>There are 4 instances of this issue:</i></summary>

```solidity
📁 File: contracts/bridge/Bridge.sol

/// @audit Missing @param for all modifier parameters
64:     modifier sameChain(uint64 _chainId) { 
```
[64](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L64)

```solidity
📁 File: contracts/signal/SignalService.sol

/// @audit Missing @param for all modifier parameters
35:     modifier validSender(address _app) { 

/// @audit Missing @param for all modifier parameters
40:     modifier nonZeroValue(bytes32 _input) { 
```
[35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L35), [40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L40)

```solidity
📁 File: contracts/tokenvault/BaseNFTVault.sol

/// @audit Missing @param for all modifier parameters
140:     modifier withValidOperation(BridgeTransferOp memory _op) { 
```
[140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L140)

</details>


---
### [NC&#x2011;94] Natspec: Use `@inheritdoc` rather than using a non-standard tags
Using non-standard annotations like `@dev see Ellipsis` can lead to inconsistencies and lack of clarity in your smart contract documentation. It's recommended to use the `@inheritdoc` annotation for enhanced clarity and uniformity in smart contract development.

<details>
<summary><i>There are 6 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/gov/TaikoGovernor.sol

47:     /// @dev See {IGovernor-propose} 
48:     function propose(

61:     /// @notice An overwrite of GovernorCompatibilityBravoUpgradeable's propose() as that one does 
62:     /// not check that the length of signatures equal the calldata.
63:     /// @dev See vulnerability description here:
64:     /// https://github.com/taikoxyz/taiko-mono/security/dependabot/114

88:     /// @dev See {GovernorUpgradeable-supportsInterface} 
89:     function supportsInterface(bytes4 _interfaceId)

98:     /// @dev See {GovernorUpgradeable-state} 
99:     function state(uint256 _proposalId)
```
[47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L47-L48), [61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L61-L64), [88](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L88-L89), [98](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L98-L99)

```solidity
📁 File: contracts/L2/Lib1559Math.sol

6: /// @title Lib1559Math 
7: /// @notice Implements e^(x) based bonding curve for EIP-1559
8: /// @dev See https://ethresear.ch/t/make-eip-1559-more-like-an-amm-curve/9082
9: /// @custom:security-contact security@taiko.xyz
```
[6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L6-L9)

```solidity
📁 File: contracts/tokenvault/ERC1155Vault.sol

189:     /// @dev See {BaseVault-supportsInterface}. 
190:     /// @param interfaceId The interface identifier.
```
[189](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L189-L190)

</details>


---
### [NC&#x2011;95] Non-assembly method available
`assembly{ id := chainid() }` => `uint256 id = block.chainid`, `assembly { size := extcodesize() }` => `uint256 size = address().code.length`, `assembly { hash := extcodehash() }` => `bytes32 hash = address().codehash`
 There are some automated tools that will flag a project as having higher complexity if there is inline-assembly, so it's best to avoid using it where it's not necessary

<details>
<summary><i>There are 3 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L2/TaikoL2.sol

243:             publicInputHashOld := keccak256(inputs, 8192 /*mul(256, 32)*/ ) 

248:             publicInputHashNew := keccak256(inputs, 8192 /*mul(256, 32)*/ ) 
```
[243](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L243), [248](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L248)

```solidity
📁 File: contracts/automata-attestation/utils/BytesUtils.sol

27:             ret := keccak256(add(add(self, 32), offset), len) 
```
[27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L27)

</details>


---
### [NC&#x2011;96] Non-`external`/`public` function names should begin with an underscore
According to the Solidity Style Guide, Non-`external`/`public` function names should begin with an <a href="https://docs.soliditylang.org/en/latest/style-guide.html#underscore-prefix-for-non-external-functions-and-variables">underscore</a>.

<details>
<summary><i>There are 40 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/libs/LibDepositing.sol

/// @audit _depositEtherToL2
29:     function depositEtherToL2( 
30:         TaikoData.State storage _state,
31:         TaikoData.Config memory _config,
32:         IAddressResolver _resolver,
33:         address _recipient
34:     )
35:         internal
36:     {

/// @audit _processDeposits
67:     function processDeposits( 
68:         TaikoData.State storage _state,
69:         TaikoData.Config memory _config,
70:         address _feeRecipient
71:     )
72:         internal
73:         returns (TaikoData.EthDeposit[] memory deposits_)
74:     {

/// @audit _canDepositEthToL2
122:     function canDepositEthToL2( 
123:         TaikoData.State storage _state,
124:         TaikoData.Config memory _config,
125:         uint256 _amount
126:     )
127:         internal
128:         view
129:         returns (bool)
130:     {
```
[29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L29-L36), [67](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L67-L74), [122](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L122-L130)

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

/// @audit _proposeBlock
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

/// @audit _isBlobReusable
287:     function isBlobReusable( 
288:         TaikoData.State storage _state,
289:         TaikoData.Config memory _config,
290:         bytes32 _blobHash
291:     )
292:         internal
293:         view
294:         returns (bool)
295:     {
```
[68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L68-L77), [287](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L287-L295)

```solidity
📁 File: contracts/L1/libs/LibProving.sol

/// @audit _proveBlock
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
```
[91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L91-L101)

```solidity
📁 File: contracts/L1/libs/LibUtils.sol

/// @audit _getTransitionId
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
```
[70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L70-L79)

```solidity
📁 File: contracts/L1/libs/LibVerifying.sol

/// @audit _verifyBlocks
85:     function verifyBlocks( 
86:         TaikoData.State storage _state,
87:         TaikoData.Config memory _config,
88:         IAddressResolver _resolver,
89:         uint64 _maxBlocksToVerify
90:     )
91:         internal
92:     {
```
[85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L85-L92)

```solidity
📁 File: contracts/L1/provers/Guardians.sol

/// @audit _approve
111:     function approve(uint256 _operationId, bytes32 _hash) internal returns (bool approved_) { 

/// @audit _deleteApproval
124:     function deleteApproval(bytes32 _hash) internal { 

/// @audit _isApproved
128:     function isApproved(uint256 _approvalBits) internal view returns (bool) { 
```
[111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L111), [124](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L124), [128](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L128)

```solidity
📁 File: contracts/L2/Lib1559Math.sol

/// @audit _basefee
16:     function basefee( 
17:         uint256 _gasExcess,
18:         uint256 _adjustmentFactor
19:     )
20:         internal
21:         pure
22:         returns (uint256)
23:     {
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L16-L23)

```solidity
📁 File: contracts/libs/Lib4844.sol

/// @audit _evaluatePoint
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
[30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L30-L39)

```solidity
📁 File: contracts/libs/LibAddress.sol

/// @audit _sendEther
22:     function sendEther(address _to, uint256 _amount, uint256 _gasLimit) internal { 

/// @audit _sendEther
42:     function sendEther(address _to, uint256 _amount) internal { 

/// @audit _supportsInterface
46:     function supportsInterface( 
47:         address _addr,
48:         bytes4 _interfaceId
49:     )
50:         internal
51:         view
52:         returns (bool result_)
53:     {

/// @audit _isValidSignature
61:     function isValidSignature( 
62:         address _addr,
63:         bytes32 _hash,
64:         bytes memory _sig
65:     )
66:         internal
67:         view
68:         returns (bool)
69:     {

/// @audit _isSenderEOA
77:     function isSenderEOA() internal view returns (bool) { 
```
[22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L22), [42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L42), [46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L46-L53), [61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L61-L69), [77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L77)

```solidity
📁 File: contracts/libs/LibMath.sol

/// @audit _min
12:     function min(uint256 _a, uint256 _b) internal pure returns (uint256) { 

/// @audit _max
20:     function max(uint256 _a, uint256 _b) internal pure returns (uint256) { 
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibMath.sol#L12), [20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibMath.sol#L20)

```solidity
📁 File: contracts/libs/LibTrieProof.sol

/// @audit _verifyMerkleProof
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
45:     {
```
[34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L34-L45)

```solidity
📁 File: contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol

/// @audit _excessivelySafeCall
25:     function excessivelySafeCall( 
26:         address _target,
27:         uint256 _gas,
28:         uint256 _value,
29:         uint16 _maxCopy,
30:         bytes memory _calldata
31:     )
32:         internal
33:         returns (bool, bytes memory)
34:     {
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L25-L34)

```solidity
📁 File: contracts/thirdparty/optimism/Bytes.sol

/// @audit _slice
15:     function slice( 
16:         bytes memory _bytes,
17:         uint256 _start,
18:         uint256 _length
19:     )
20:         internal
21:         pure
22:         returns (bytes memory)
23:     {

/// @audit _slice
91:     function slice(bytes memory _bytes, uint256 _start) internal pure returns (bytes memory) { 

/// @audit _toNibbles
102:     function toNibbles(bytes memory _bytes) internal pure returns (bytes memory) { 

/// @audit _equal
149:     function equal(bytes memory _bytes, bytes memory _other) internal pure returns (bool) { 
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L15-L23), [91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L91), [102](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L102), [149](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L149)

```solidity
📁 File: contracts/thirdparty/optimism/rlp/RLPReader.sol

/// @audit _toRLPItem
35:     function toRLPItem(bytes memory _in) internal pure returns (RLPItem memory out_) { 

/// @audit _readList
53:     function readList(RLPItem memory _in) internal pure returns (RLPItem[] memory out_) { 

/// @audit _readList
102:     function readList(bytes memory _in) internal pure returns (RLPItem[] memory out_) { 

/// @audit _readBytes
109:     function readBytes(RLPItem memory _in) internal pure returns (bytes memory out_) { 

/// @audit _readBytes
128:     function readBytes(bytes memory _in) internal pure returns (bytes memory out_) { 

/// @audit _readRawBytes
135:     function readRawBytes(RLPItem memory _in) internal pure returns (bytes memory out_) { 
```
[35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L35), [53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L53), [102](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L102), [109](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L109), [128](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L128), [135](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L135)

```solidity
📁 File: contracts/thirdparty/optimism/rlp/RLPWriter.sol

/// @audit _writeBytes
13:     function writeBytes(bytes memory _in) internal pure returns (bytes memory out_) { 

/// @audit _writeUint
24:     function writeUint(uint256 _in) internal pure returns (bytes memory out_) { 
```
[13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L13), [24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L24)

```solidity
📁 File: contracts/tokenvault/BaseVault.sol

/// @audit _checkProcessMessageContext
47:     function checkProcessMessageContext() 
48:         internal
49:         view
50:         onlyFromBridge
51:         returns (IBridge.Context memory ctx_)
52:     {

/// @audit _checkRecallMessageContext
58:     function checkRecallMessageContext() 
59:         internal
60:         view
61:         onlyFromBridge
62:         returns (IBridge.Context memory ctx_)
63:     {
```
[47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L47-L52), [58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L58-L63)

```solidity
📁 File: contracts/tokenvault/LibBridgedToken.sol

/// @audit _validateInputs
11:     function validateInputs( 
12:         address _srcToken,
13:         uint256 _srcChainId,
14:         string memory _symbol,
15:         string memory _name
16:     )
17:         internal
18:         view
19:     {

/// @audit _buildName
28:     function buildName( 
29:         string memory _name,
30:         uint256 _srcChainId
31:     )
32:         internal
33:         pure
34:         returns (string memory)
35:     {

/// @audit _buildSymbol
39:     function buildSymbol(string memory _symbol) internal pure returns (string memory) { 

/// @audit _buildURI
43:     function buildURI( 
44:         address _srcToken,
45:         uint256 _srcChainId
46:     )
47:         internal
48:         pure
49:         returns (string memory)
50:     {
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L11-L19), [28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L28-L35), [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L39), [43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L43-L50)

</details>


---
### [NC&#x2011;97] Non-library/interface files should use fixed compiler versions, not floating ones
To prevent the actual contracts being deployed from behaving differently depending on the compiler version, it is recommended to use fixed solidity versions for contracts and libraries.

Although we can configure a specific version through config (like hardhat, forge config files), it is recommended to **set the fixed version in the solidity pragma directly** before deploying to the mainnet.

<details>
<summary><i>There are 40 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoErrors.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoErrors.sol#L2)

```solidity
📁 File: contracts/L1/TaikoEvents.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L2)

```solidity
📁 File: contracts/L1/TaikoL1.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L2)

```solidity
📁 File: contracts/L1/TaikoToken.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L2)

```solidity
📁 File: contracts/L1/gov/TaikoGovernor.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L2)

```solidity
📁 File: contracts/L1/gov/TaikoTimelockController.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L2)

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L2)

```solidity
📁 File: contracts/L1/provers/GuardianProver.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L2)

```solidity
📁 File: contracts/L1/provers/Guardians.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L2)

```solidity
📁 File: contracts/L1/tiers/DevnetTierProvider.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L2)

```solidity
📁 File: contracts/L1/tiers/MainnetTierProvider.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L2)

```solidity
📁 File: contracts/L1/tiers/TestnetTierProvider.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L2)

```solidity
📁 File: contracts/L2/CrossChainOwned.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L2)

```solidity
📁 File: contracts/L2/TaikoL2.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L2)

```solidity
📁 File: contracts/L2/TaikoL2EIP1559Configurable.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L2)

```solidity
📁 File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L2)

```solidity
📁 File: contracts/automata-attestation/lib/PEMCertChainLib.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L2)

```solidity
📁 File: contracts/automata-attestation/utils/SigVerifyLib.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L2)

```solidity
📁 File: contracts/bridge/Bridge.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L2)

```solidity
📁 File: contracts/common/AddressManager.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L2)

```solidity
📁 File: contracts/common/AddressResolver.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L2)

```solidity
📁 File: contracts/common/EssentialContract.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L2)

```solidity
📁 File: contracts/signal/SignalService.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L2)

```solidity
📁 File: contracts/team/TimelockTokenPool.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L2)

```solidity
📁 File: contracts/team/airdrop/ERC20Airdrop.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L2)

```solidity
📁 File: contracts/team/airdrop/ERC20Airdrop2.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L2)

```solidity
📁 File: contracts/team/airdrop/ERC721Airdrop.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L2)

```solidity
📁 File: contracts/team/airdrop/MerkleClaimable.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L2)

```solidity
📁 File: contracts/tokenvault/BaseNFTVault.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L2)

```solidity
📁 File: contracts/tokenvault/BaseVault.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L2)

```solidity
📁 File: contracts/tokenvault/BridgedERC1155.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L2)

```solidity
📁 File: contracts/tokenvault/BridgedERC20.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L2)

```solidity
📁 File: contracts/tokenvault/BridgedERC20Base.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L2)

```solidity
📁 File: contracts/tokenvault/BridgedERC721.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L2)

```solidity
📁 File: contracts/tokenvault/ERC1155Vault.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L2)

```solidity
📁 File: contracts/tokenvault/ERC20Vault.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L2)

```solidity
📁 File: contracts/tokenvault/ERC721Vault.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L2)

```solidity
📁 File: contracts/tokenvault/adapters/USDCAdapter.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L2)

```solidity
📁 File: contracts/verifiers/GuardianVerifier.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L2)

```solidity
📁 File: contracts/verifiers/SgxVerifier.sol

2: pragma solidity ^0.8.0; 
```
[2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L2)

</details>


---
### [NC&#x2011;98] Not using the latest versions of project dependencies
Update the project dependencies to their latest versions wherever possible.

Use tools such as `retire.js`, `npm audit`, and `yarn audit` to confirm that no vulnerable dependencies remain.

|Dependency|Current Version|Latest Version|
|:-:|:-:|:-:|
|`openzeppelin-contracts`|4.8.2|5.0.2|
|`openzeppelin-contracts-upgradeable`|4.8.2|5.0.2|
|`forge-std`|github:foundry-rs/forge-std#v1.7.5|1.8.1|
|`solady`|github:Vectorized/solady#v0.0.167|0.0.168|



<i>There is one instance of this issue:</i>

```solidity
📁 File: contracts/common/IAddressManager.sol

1: // SPDX-License-Identifier: MIT 
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressManager.sol#L1)


---
### [NC&#x2011;99] Not using the named return variables anywhere in the function is confusing
Declaring named returns, but not using them, is confusing to the reader. Consider either completely removing them (by declaring just the type without a name), or remove the return statement and do a variable assignment.

This would improve the readability of the code, and it may also help reduce regressions during future code refactors.

If the optimizer is not turned on, leaving the code as it is will also waste gas for the stack variable.

<details>
<summary><i>There are 7 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/libs/LibProving.sol

/// @audit maxBlocksToVerify_ is unused
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
102:         // Make sure parentHash is not zero
103:         // To contest an existing transition, simply use any non-zero value as
104:         // the blockHash and stateRoot.
105:         if (_tran.parentHash == 0 || _tran.blockHash == 0 || _tran.stateRoot == 0) {
106:             revert L1_INVALID_TRANSITION();
107:         }
108: 
109:         // Check that the block has been proposed but has not yet been verified.
110:         TaikoData.SlotB memory b = _state.slotB;
111:         if (_meta.id <= b.lastVerifiedBlockId || _meta.id >= b.numBlocks) {
112:             revert L1_INVALID_BLOCK_ID();
113:         }
114: 
115:         uint64 slot = _meta.id % _config.blockRingBufferSize;
116:         TaikoData.Block storage blk = _state.blocks[slot];
117: 
118:         // Check the integrity of the block data. It's worth noting that in
119:         // theory, this check may be skipped, but it's included for added
120:         // caution.
121:         if (blk.blockId != _meta.id || blk.metaHash != keccak256(abi.encode(_meta))) {
122:             revert L1_BLOCK_MISMATCH();
123:         }
124: 
125:         // Each transition is uniquely identified by the parentHash, with the
126:         // blockHash and stateRoot open for later updates as higher-tier proofs
127:         // become available. In cases where a transition with the specified
128:         // parentHash does not exist, the transition ID (tid) will be set to 0.
129:         (uint32 tid, TaikoData.TransitionState storage ts) =
130:             _createTransition(_state, blk, _tran, slot);
131: 
132:         // The new proof must meet or exceed the minimum tier required by the
133:         // block or the previous proof; it cannot be on a lower tier.
134:         if (_proof.tier == 0 || _proof.tier < _meta.minTier || _proof.tier < ts.tier) {
135:             revert L1_INVALID_TIER();
136:         }
137: 
138:         // Retrieve the tier configurations. If the tier is not supported, the
139:         // subsequent action will result in a revert.
140:         ITierProvider.Tier memory tier =
141:             ITierProvider(_resolver.resolve("tier_provider", false)).getTier(_proof.tier);
142: 
143:         // Check if this prover is allowed to submit a proof for this block
144:         _checkProverPermission(_state, blk, ts, tid, tier);
145: 
146:         // We must verify the proof, and any failure in proof verification will
147:         // result in a revert.
148:         //
149:         // It's crucial to emphasize that the proof can be assessed in two
150:         // potential modes: "proving mode" and "contesting mode." However, the
151:         // precise verification logic is defined within each tier's IVerifier
152:         // contract implementation. We simply specify to the verifier contract
153:         // which mode it should utilize - if the new tier is higher than the
154:         // previous tier, we employ the proving mode; otherwise, we employ the
155:         // contesting mode (the new tier cannot be lower than the previous tier,
156:         // this has been checked above).
157:         //
158:         // It's obvious that proof verification is entirely decoupled from
159:         // Taiko's core protocol.
160:         {
161:             address verifier = _resolver.resolve(tier.verifierName, true);
162: 
163:             if (verifier != address(0)) {
164:                 bool isContesting = _proof.tier == ts.tier && tier.contestBond != 0;
165: 
166:                 IVerifier.Context memory ctx = IVerifier.Context({
167:                     metaHash: blk.metaHash,
168:                     blobHash: _meta.blobHash,
169:                     // Separate msgSender to allow the prover to be any address in the future.
170:                     prover: msg.sender,
171:                     msgSender: msg.sender,
172:                     blockId: blk.blockId,
173:                     isContesting: isContesting,
174:                     blobUsed: _meta.blobUsed
175:                 });
176: 
177:                 IVerifier(verifier).verifyProof(ctx, _tran, _proof);
178:             } else if (tier.verifierName != TIER_OP) {
179:                 // The verifier can be address-zero, signifying that there are no
180:                 // proof checks for the tier. In practice, this only applies to
181:                 // optimistic proofs.
182:                 revert L1_MISSING_VERIFIER();
183:             }
184:         }
185: 
186:         bool isTopTier = tier.contestBond == 0;
187:         IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));
188: 
189:         if (isTopTier) {
190:             // A special return value from the top tier prover can signal this
191:             // contract to return all liveness bond.
192:             bool returnLivenessBond = blk.livenessBond > 0 && _proof.data.length == 32
193:                 && bytes32(_proof.data) == RETURN_LIVENESS_BOND;
194: 
195:             if (returnLivenessBond) {
196:                 tko.transfer(blk.assignedProver, blk.livenessBond);
197:                 blk.livenessBond = 0;
198:             }
199:         }
200: 
201:         bool sameTransition = _tran.blockHash == ts.blockHash && _tran.stateRoot == ts.stateRoot;
202: 
203:         if (_proof.tier > ts.tier) {
204:             // Handles the case when an incoming tier is higher than the current transition's tier.
205:             // Reverts when the incoming proof tries to prove the same transition
206:             // (L1_ALREADY_PROVED).
207:             _overrideWithHigherProof(ts, _tran, _proof, tier, tko, sameTransition);
208: 
209:             emit TransitionProved({
210:                 blockId: blk.blockId,
211:                 tran: _tran,
212:                 prover: msg.sender,
213:                 validityBond: tier.validityBond,
214:                 tier: _proof.tier
215:             });
216:         } else {
217:             // New transition and old transition on the same tier - and if this transaction tries to
218:             // prove the same, it reverts
219:             if (sameTransition) revert L1_ALREADY_PROVED();
220: 
221:             if (isTopTier) {
222:                 // The top tier prover re-proves.
223:                 assert(tier.validityBond == 0);
224:                 assert(ts.validityBond == 0 && ts.contestBond == 0 && ts.contester == address(0));
225: 
226:                 ts.prover = msg.sender;
227:                 ts.blockHash = _tran.blockHash;
228:                 ts.stateRoot = _tran.stateRoot;
229: 
230:                 emit TransitionProved({
231:                     blockId: blk.blockId,
232:                     tran: _tran,
233:                     prover: msg.sender,
234:                     validityBond: 0,
235:                     tier: _proof.tier
236:                 });
237:             } else {
238:                 // Contesting but not on the highest tier
239:                 if (ts.contester != address(0)) revert L1_ALREADY_CONTESTED();
240: 
241:                 // Burn the contest bond from the prover.
242:                 tko.transferFrom(msg.sender, address(this), tier.contestBond);
243: 
244:                 // We retain the contest bond within the transition, just in
245:                 // case this configuration is altered to a different value
246:                 // before the contest is resolved.
247:                 //
248:                 // It's worth noting that the previous value of ts.contestBond
249:                 // doesn't have any significance.
250:                 ts.contestBond = tier.contestBond;
251:                 ts.contester = msg.sender;
252:                 ts.contestations += 1;
253: 
254:                 emit TransitionContested({
255:                     blockId: blk.blockId,
256:                     tran: _tran,
257:                     contester: msg.sender,
258:                     contestBond: tier.contestBond,
259:                     tier: _proof.tier
260:                 });
261:             }
262:         }
263: 
264:         ts.timestamp = uint64(block.timestamp);
265:         return tier.maxBlocksToVerifyPerProof;
266:     }
```
[91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L91-L266)

```solidity
📁 File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

/// @audit valid is unused
126:     function _attestationTcbIsValid(TCBInfoStruct.TCBStatus status) 
127:         internal
128:         pure
129:         virtual
130:         returns (bool valid)
131:     {
132:         return status == TCBInfoStruct.TCBStatus.OK
133:             || status == TCBInfoStruct.TCBStatus.TCB_SW_HARDENING_NEEDED
134:             || status == TCBInfoStruct.TCBStatus.TCB_CONFIGURATION_AND_SW_HARDENING_NEEDED
135:             || status == TCBInfoStruct.TCBStatus.TCB_OUT_OF_DATE_CONFIGURATION_NEEDED;
136:     }
```
[126](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L126-L136)

```solidity
📁 File: contracts/automata-attestation/lib/PEMCertChainLib.sol

/// @audit success is unused
216:     function _removeHeadersAndFooters(string memory pemData) 
217:         private
218:         pure
219:         returns (bool success, bytes memory extracted, uint256 endIndex)
220:     {
221:         // Check if the input contains the "BEGIN" and "END" headers
222:         uint256 beginPos = LibString.indexOf(pemData, HEADER);
223:         uint256 endPos = LibString.indexOf(pemData, FOOTER);
224: 
225:         bool headerFound = beginPos != LibString.NOT_FOUND;
226:         bool footerFound = endPos != LibString.NOT_FOUND;
227: 
228:         if (!headerFound || !footerFound) {
229:             return (false, extracted, endIndex);
230:         }
231: 
232:         // Extract the content between the headers
233:         uint256 contentStart = beginPos + HEADER_LENGTH;
234: 
235:         // Extract and return the content
236:         bytes memory contentBytes;
237: 
238:         // do not include newline
239:         bytes memory delimiter = hex"0a";
240:         string memory contentSlice = LibString.slice(pemData, contentStart, endPos);
241:         string[] memory split = LibString.split(contentSlice, string(delimiter));
242:         string memory contentStr;
243: 
244:         for (uint256 i; i < split.length; ++i) {
245:             contentStr = LibString.concat(contentStr, split[i]);
246:         }
247: 
248:         contentBytes = bytes(contentStr);
249:         return (true, contentBytes, endPos + FOOTER_LENGTH);
250:     }
```
[216](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L216-L250)

```solidity
📁 File: contracts/automata-attestation/utils/BytesUtils.sol

/// @audit ret is unused
188:     function readUint8(bytes memory self, uint256 idx) internal pure returns (uint8 ret) { 
189:         return uint8(self[idx]);
190:     }
```
[188](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L188-L190)

```solidity
📁 File: contracts/automata-attestation/utils/SigVerifyLib.sol

/// @audit sigValid is unused
113:     function verifyES256Signature( 
114:         bytes memory tbs,
115:         bytes memory signature,
116:         bytes memory publicKey
117:     )
118:         public
119:         view
120:         returns (bool sigValid)
121:     {
122:         // Parse signature
123:         if (signature.length != 64) {
124:             return false;
125:         }
126:         uint256 r = uint256(bytes32(signature.substring(0, 32)));
127:         uint256 s = uint256(bytes32(signature.substring(32, 32)));
128:         // Parse public key
129:         if (publicKey.length != 64) {
130:             return false;
131:         }
132:         uint256 gx = uint256(bytes32(publicKey.substring(0, 32)));
133:         uint256 gy = uint256(bytes32(publicKey.substring(32, 32)));
134: 
135:         // Verify signature
136:         bytes memory args = abi.encode(sha256(tbs), r, s, gx, gy);
137:         (bool success, bytes memory ret) = ES256VERIFIER.staticcall(args);
138:         assert(success); // never reverts, always returns 0 or 1
139: 
140:         return abi.decode(ret, (uint256)) == 1;
141:     }
```
[113](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L113-L141)

```solidity
📁 File: contracts/bridge/Bridge.sol

/// @audit invocationDelay_ is unused
/// @audit invocationExtraDelay_ is unused
417:     function getInvocationDelays() 
418:         public
419:         view
420:         virtual
421:         returns (uint256 invocationDelay_, uint256 invocationExtraDelay_)
422:     {
423:         if (
424:             block.chainid == 1 // Ethereum mainnet
425:         ) {
426:             // For Taiko mainnet
427:             // 384 seconds = 6.4 minutes = one ethereum epoch
428:             return (1 hours, 384 seconds);
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
440:             // For all Taiko internal devnets
441:             return (5 minutes, 384 seconds);
442:         } else {
443:             // This is a Taiko L2 chain where no deleys are applied.
444:             return (0, 0);
445:         }
446:     }
```
[417](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L417-L446)

```solidity
📁 File: contracts/thirdparty/optimism/rlp/RLPReader.sol

/// @audit offset_ is unused
/// @audit length_ is unused
/// @audit type_ is unused
144:     function _decodeLength(RLPItem memory _in) 
145:         private
146:         pure
147:         returns (uint256 offset_, uint256 length_, RLPItemType type_)
148:     {
149:         // Short-circuit if there's nothing to decode, note that we perform this check when
150:         // the user creates an RLP item via toRLPItem, but it's always possible for them to bypass
151:         // that function and create an RLP item directly. So we need to check this anyway.
152:         require(
153:             _in.length > 0,
154:             "RLPReader: length of an RLP item must be greater than zero to be decodable"
155:         );
156: 
157:         MemoryPointer ptr = _in.ptr;
158:         uint256 prefix;
159:         assembly {
160:             prefix := byte(0, mload(ptr))
161:         }
162: 
163:         if (prefix <= 0x7f) {
164:             // Single byte.
165:             return (0, 1, RLPItemType.DATA_ITEM);
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
235:             // Long list.
236:             uint256 lenOfListLen = prefix - 0xf7;
237: 
238:             require(
239:                 _in.length > lenOfListLen,
240:                 "RLPReader: length of content must be > than length of list length (long list)"
241:             );
242: 
243:             bytes1 firstByteOfContent;
244:             assembly {
245:                 firstByteOfContent := and(mload(add(ptr, 1)), shl(248, 0xff))
246:             }
247: 
248:             require(
249:                 firstByteOfContent != 0x00,
250:                 "RLPReader: length of content must not have any leading zeros (long list)"
251:             );
252: 
253:             uint256 listLen;
254:             assembly {
255:                 listLen := shr(sub(256, mul(8, lenOfListLen)), mload(add(ptr, 1)))
256:             }
257: 
258:             require(
259:                 listLen > 55,
260:                 "RLPReader: length of content must be greater than 55 bytes (long list)"
261:             );
262: 
263:             require(
264:                 _in.length > lenOfListLen + listLen,
265:                 "RLPReader: length of content must be greater than total length (long list)"
266:             );
267: 
268:             return (1 + lenOfListLen, listLen, RLPItemType.LIST_ITEM);
269:         }
270:     }
```
[144](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L144-L270)

</details>


---
### [NC&#x2011;100] Overly complicated arithmetic
To maintain readability in code, particularly in Solidity which can involve complex mathematical operations, it is often recommended to limit the number of arithmetic operations to a maximum of 2-3 per line. Too many operations in a single line can make the code difficult to read and understand, increase the likelihood of mistakes, and complicate the process of debugging and reviewing the code.

<details>
<summary><i>There are 14 instances of this issue:</i></summary>

```solidity
📁 File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

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
[106](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L106-L115), [159](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L159)

```solidity
📁 File: contracts/automata-attestation/utils/Asn1Decode.sol

203:                     der.readBytesN(ix + 2, lengthbytesLength) >> (32 - lengthbytesLength) * 8 
```
[203](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L203)

```solidity
📁 File: contracts/automata-attestation/utils/BytesUtils.sol

93:                     mask = ~(2 ** (8 * (32 - shortest + idx)) - 1); 
```
[93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L93)

```solidity
📁 File: contracts/automata-attestation/utils/X509DateUtils.sol

21:             yrs += (uint8(x509Time[0]) - 48) * 1000 + (uint8(x509Time[1]) - 48) * 100; 

24:         yrs += (uint8(x509Time[offset + 0]) - 48) * 10 + uint8(x509Time[offset + 1]) - 48; 
25:         mnths = (uint8(x509Time[offset + 2]) - 48) * 10 + uint8(x509Time[offset + 3]) - 48;
26:         dys += (uint8(x509Time[offset + 4]) - 48) * 10 + uint8(x509Time[offset + 5]) - 48;
27:         hrs += (uint8(x509Time[offset + 6]) - 48) * 10 + uint8(x509Time[offset + 7]) - 48;
28:         mins += (uint8(x509Time[offset + 8]) - 48) * 10 + uint8(x509Time[offset + 9]) - 48;
29:         secs += (uint8(x509Time[offset + 10]) - 48) * 10 + uint8(x509Time[offset + 11]) - 48;
```
[21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L21), [24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L24-L29)

```solidity
📁 File: contracts/team/airdrop/ERC20Airdrop2.sol

117:         uint256 timeBasedAllowance = balance 
118:             * (block.timestamp.min(claimEnd + withdrawalWindow) - claimEnd) / withdrawalWindow;
```
[117](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L117-L118)

```solidity
📁 File: contracts/thirdparty/optimism/rlp/RLPWriter.sol

47:                 out_[i] = bytes1(uint8((_len / (256 ** (lenLen - i))) % 256)); 
```
[47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L47)

```solidity
📁 File: contracts/thirdparty/solmate/LibFixedPointMath.sol

39:             int256 k = ((x << 96) / 54_916_777_467_707_473_351_141_471_128 + 2 ** 95) >> 96; 
```
[39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L39)

</details>


---
### [NC&#x2011;101] Overridden function has no body
Consider adding a NatSpec comment describing why the function doesn't need a body and or the purpose it serves


<i>There is one instance of this issue:</i>

```solidity
📁 File: contracts/common/EssentialContract.sol

116:     function _authorizePause(address) internal virtual onlyOwner { } 
```
[116](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L116)


---
### [NC&#x2011;102] Parameter change does not emit event
Events help non-contract tools to track changes

<details>
<summary><i>There are 3 instances of this issue:</i></summary>

```solidity
📁 File: contracts/common/AddressResolver.sol

58:     function __AddressResolver_init(address _addressManager) internal virtual onlyInitializing { 
59:         if (block.chainid > type(uint64).max) {
60:             revert RESOLVER_UNEXPECTED_CHAINID();
61:         }
62:         addressManager = _addressManager;
63:     }
```
[58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L58-L63)

```solidity
📁 File: contracts/common/EssentialContract.sol

114:     function _authorizeUpgrade(address) internal virtual override onlyOwner { } 
```
[114](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L114)

```solidity
📁 File: contracts/tokenvault/BridgedERC20.sol

80:     function setSnapshoter(address _snapshooter) external onlyOwner { 
81:         snapshooter = _snapshooter;
82:     }
```
[80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L80-L82)

</details>


---
### [NC&#x2011;103] Place `interface` files into a dedicated folder
Using a separate folder for interfaces keeps the codebase organised and helps to facilitate security audits as well as future development.

<details>
<summary><i>There are 13 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/ITaikoL1.sol

8: interface ITaikoL1 { 
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/ITaikoL1.sol#L8)

```solidity
📁 File: contracts/L1/hooks/IHook.sol

8: interface IHook { 
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/IHook.sol#L8)

```solidity
📁 File: contracts/L1/tiers/ITierProvider.sol

7: interface ITierProvider { 
```
[7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L7)

```solidity
📁 File: contracts/bridge/IBridge.sol

8: interface IBridge { 

160: interface IRecallableSender { 

174: interface IMessageInvocable { 
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L8), [160](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L160), [174](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L174)

```solidity
📁 File: contracts/common/IAddressManager.sol

7: interface IAddressManager { 
```
[7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressManager.sol#L7)

```solidity
📁 File: contracts/common/IAddressResolver.sol

13: interface IAddressResolver { 
```
[13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressResolver.sol#L13)

```solidity
📁 File: contracts/signal/ISignalService.sol

12: interface ISignalService { 
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L12)

```solidity
📁 File: contracts/tokenvault/ERC1155Vault.sol

16: interface IERC1155NameAndSymbol { 
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L16)

```solidity
📁 File: contracts/tokenvault/IBridgedERC20.sol

10: interface IBridgedERC20 { 
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/IBridgedERC20.sol#L10)

```solidity
📁 File: contracts/tokenvault/adapters/USDCAdapter.sol

8: interface IUSDC { 
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L8)

```solidity
📁 File: contracts/verifiers/IVerifier.sol

9: interface IVerifier { 
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/IVerifier.sol#L9)

</details>


---
### [NC&#x2011;104] Polymorphic functions make security audits more time-consuming and error-prone
The instances below point to one of two functions with the same name. Consider naming each function differently, in order to make code navigation and analysis easier.

<details>
<summary><i>There are 26 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/gov/TaikoGovernor.sol

/// @audit propose(address[] memory _targets, uint256[] memory _values, bytes[] memory _calldatas, string memory _description)
/// @audit propose(address[] memory _targets, uint256[] memory _values, string[] memory _signatures, bytes[] memory _calldatas, string memory _description)
16: contract TaikoGovernor is 
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L16)

```solidity
📁 File: contracts/L1/provers/Guardians.sol

/// @audit isApproved(bytes32 _hash)
/// @audit isApproved(uint256 _approvalBits)
9: abstract contract Guardians is EssentialContract { 
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L9)

```solidity
📁 File: contracts/automata-attestation/utils/BytesUtils.sol

/// @audit compare(bytes memory self, bytes memory other)
/// @audit compare(bytes memory self, uint256 offset, uint256 len, bytes memory other, uint256 otheroffset, uint256 otherlen)
/// @audit equals(bytes memory self, uint256 offset, bytes memory other, uint256 otherOffset, uint256 len)
/// @audit equals(bytes memory self, uint256 offset, bytes memory other, uint256 otherOffset)
/// @audit equals(bytes memory self, uint256 offset, bytes memory other)
/// @audit equals(bytes memory self, bytes memory other)
8: library BytesUtils { 
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L8)

```solidity
📁 File: contracts/common/AddressResolver.sol

/// @audit resolve(bytes32 _name, bool _allowZeroAddress)
/// @audit resolve(uint64 _chainId, bytes32 _name, bool _allowZeroAddress)
11: abstract contract AddressResolver is IAddressResolver, Initializable { 
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L11)

```solidity
📁 File: contracts/common/EssentialContract.sol

/// @audit __Essential_init(address _owner, address _addressManager)
/// @audit __Essential_init(address _owner)
10: abstract contract EssentialContract is UUPSUpgradeable, Ownable2StepUpgradeable, AddressResolver { 
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L10)

```solidity
📁 File: contracts/common/IAddressResolver.sol

/// @audit resolve()
/// @audit resolve(bytes32 _name, bool _allowZeroAddress)
13: interface IAddressResolver { 
```
[13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressResolver.sol#L13)

```solidity
📁 File: contracts/libs/LibAddress.sol

/// @audit sendEther(address _to, uint256 _amount, uint256 _gasLimit)
/// @audit sendEther(address _to, uint256 _amount)
13: library LibAddress { 
```
[13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L13)

```solidity
📁 File: contracts/team/TimelockTokenPool.sol

/// @audit withdraw()
/// @audit withdraw(address _to, bytes memory _sig)
25: contract TimelockTokenPool is EssentialContract { 
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L25)

```solidity
📁 File: contracts/thirdparty/optimism/Bytes.sol

/// @audit slice(bytes memory _bytes, uint256 _start, uint256 _length)
/// @audit slice(bytes memory _bytes, uint256 _start)
6: library Bytes { 
```
[6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L6)

```solidity
📁 File: contracts/thirdparty/optimism/rlp/RLPReader.sol

/// @audit readList(RLPItem memory _in)
/// @audit readList(bytes memory _in)
/// @audit readBytes(RLPItem memory _in)
/// @audit readBytes(bytes memory _in)
9: library RLPReader { 
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L9)

</details>


---
### [NC&#x2011;105] Prefer skip over revert model in iteration
It is preferable to skip operations on an array index when a condition is not met rather than reverting the whole transaction as reverting can introduce the possiblity of malicous actors purposefully introducing array objects which fail conditional checks within for/while loops so group operations fail. As such it is recommended to simply skip such array indices over reverting unless there is a valid security or logic reason behind not doing so.

<details>
<summary><i>There are 10 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

/// @audit reverts on line: 246
244:             for (uint256 i; i < params.hookCalls.length; ++i) { 
```
[244](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L244)

```solidity
📁 File: contracts/L1/libs/LibVerifying.sol

/// @audit reverts on line: 131
127:             while (blockId < b.numBlocks && numBlocksVerified < _maxBlocksToVerify) { 
```
[127](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L127)

```solidity
📁 File: contracts/L1/provers/Guardians.sol

/// @audit reverts on line: 82, 84
80:         for (uint256 i = 0; i < _newGuardians.length; ++i) { 
```
[80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L80)

```solidity
📁 File: contracts/automata-attestation/utils/BytesUtils.sol

/// @audit reverts on line: 335, 337
333:         for (uint256 i; i < len; ++i) { 
```
[333](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L333)

```solidity
📁 File: contracts/signal/SignalService.sol

/// @audit reverts on line: 111, 115
104:         for (uint256 i; i < hopProofs.length; ++i) { 
```
[104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L104)

```solidity
📁 File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

/// @audit reverts on line: 89, 93, 105, 99, 150, 119, 125, 162, 172, 178
85:         for (uint256 i = 0; i < proof.length; i++) { 
```
[85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85)

```solidity
📁 File: contracts/tokenvault/ERC1155Vault.sol

/// @audit reverts on line: 48
47:         for (uint256 i; i < _op.amounts.length; ++i) { 
```
[47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L47)

```solidity
📁 File: contracts/tokenvault/ERC721Vault.sol

/// @audit reverts on line: 35
34:         for (uint256 i; i < _op.tokenIds.length; ++i) { 
```
[34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L34)

```solidity
📁 File: contracts/verifiers/SgxVerifier.sol

/// @audit reverts on line: 107
104:         for (uint256 i; i < _ids.length; ++i) { 

/// @audit reverts on line: 211, 215
210:         for (uint256 i; i < _instances.length; ++i) { 
```
[104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L104), [210](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210)

</details>


---
### [NC&#x2011;106] `public` functions not called by the contract should be declared `external` instead
Contracts are allowed to override their parents’ functions and change the visibility from public to external.

<details>
<summary><i>There are 40 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoL1.sol

124:     function unpause() public override { 

132:     function canDepositEthToL2(uint256 _amount) public view returns (bool) { 

137:     function isBlobReusable(bytes32 _blobHash) public view returns (bool) { 

145:     function getBlock(uint64 _blockId) 

162:     function getTransition( 

176:     function getStateVariables() 
```
[124](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L124), [132](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L132), [137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L137), [145](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L145), [162](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L162), [176](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L176)

```solidity
📁 File: contracts/L1/TaikoToken.sol

25:     function init( 

47:     function burn(address _from, uint256 _amount) public onlyOwner { 

52:     function snapshot() public onlyFromOwnerOrNamed("snapshooter") { 

60:     function transfer(address _to, uint256 _amount) public override returns (bool) { 

70:     function transferFrom( 
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L25), [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L47), [52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L52), [60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L60), [70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L70)

```solidity
📁 File: contracts/L1/gov/TaikoGovernor.sol

48:     function propose( 

69:     function propose( 

89:     function supportsInterface(bytes4 _interfaceId) 

99:     function state(uint256 _proposalId) 

111:     function votingDelay() public pure override returns (uint256) { 

117:     function votingPeriod() public pure override returns (uint256) { 

123:     function proposalThreshold() public pure override returns (uint256) { 
```
[48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L48), [69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L69), [89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L89), [99](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L99), [111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L111), [117](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L117), [123](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L123)

```solidity
📁 File: contracts/L1/gov/TaikoTimelockController.sol

24:     function getMinDelay() public view override returns (uint256) { 
```
[24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L24)

```solidity
📁 File: contracts/L1/provers/Guardians.sol

107:     function numGuardians() public view returns (uint256) { 
```
[107](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L107)

```solidity
📁 File: contracts/L1/tiers/DevnetTierProvider.sol

20:     function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) { 

47:     function getTierIds() public pure override returns (uint16[] memory tiers_) { 

54:     function getMinTier(uint256) public pure override returns (uint16) { 
```
[20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L20), [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L47), [54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L54)

```solidity
📁 File: contracts/L1/tiers/MainnetTierProvider.sol

20:     function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) { 

58:     function getTierIds() public pure override returns (uint16[] memory tiers_) { 

66:     function getMinTier(uint256 _rand) public pure override returns (uint16) { 
```
[20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L20), [58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L58), [66](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L66)

```solidity
📁 File: contracts/L1/tiers/TestnetTierProvider.sol

20:     function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) { 

58:     function getTierIds() public pure override returns (uint16[] memory tiers_) { 

66:     function getMinTier(uint256 _rand) public pure override returns (uint16) { 
```
[20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L20), [58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L58), [66](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L66)

```solidity
📁 File: contracts/L2/TaikoL2.sol

185:     function getBasefee( 

200:     function getBlockHash(uint64 _blockId) public view returns (bytes32) { 
```
[185](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L185), [200](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L200)

```solidity
📁 File: contracts/L2/TaikoL2EIP1559Configurable.sol

43:     function getConfig() public view override returns (Config memory) { 
```
[43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L43)

```solidity
📁 File: contracts/common/AddressManager.sol

54:     function getAddress(uint64 _chainId, bytes32 _name) public view override returns (address) { 
```
[54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L54)

```solidity
📁 File: contracts/common/AddressResolver.sol

43:     function resolve( 
```
[43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L43)

```solidity
📁 File: contracts/common/EssentialContract.sol

69:     function pause() public virtual whenNotPaused { 

78:     function unpause() public virtual whenPaused { 
```
[69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L69), [78](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L78)

```solidity
📁 File: contracts/signal/SignalService.sol

83:     function proveSignalReceived( 

137:     function isChainDataSynced( 

153:     function isSignalSent(address _app, bytes32 _signal) public view returns (bool) { 

158:     function getSyncedChainData( 
```
[83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L83), [137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L137), [153](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L153), [158](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L158)

</details>


---
### [NC&#x2011;107] `receive()`/`payable fallback()` function does not authorize requests
If the intention is for the Ether to be used, the function should call another function, otherwise it should revert (e.g. `require(msg.sender == address(weth))`). Having no access control on the function means that someone may send Ether to the contract, and have no way to get anything back out, which is a loss of funds. If the concern is having to spend a small amount of gas to check the sender against an immutable address, the code should at least have a function to rescue unused Ether.

<details>
<summary><i>There are 2 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoL1.sol

34:     receive() external payable { 
35:         if (!_inNonReentrant()) revert L1_RECEIVE_DISABLED();
36:     }
```
[34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L34-L36)

```solidity
📁 File: contracts/bridge/Bridge.sol

70:     receive() external payable { } 
```
[70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L70)

</details>


---
### [NC&#x2011;108] Redundant IERC20 import
IERC20 is already present in SafeERC20 or ERC20, no need to import it twice

Replace
```solidity
import { IERC20 } from "@openzeppelin/contracts/token/ERC20/IERC20.sol";
import { SafeERC20 } from "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```
with
```solidity
import { SafeERC20, IERC20 } from "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```

<details>
<summary><i>There are 8 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol"; 
5: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```
[4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L4-L5)

```solidity
📁 File: contracts/L2/TaikoL2.sol

4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol"; 
5: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```
[4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L4-L5)

```solidity
📁 File: contracts/team/TimelockTokenPool.sol

5: import "@openzeppelin/contracts/token/ERC20/IERC20.sol"; 
6: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```
[5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L5-L6)

```solidity
📁 File: contracts/tokenvault/ERC20Vault.sol

4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol"; 

6: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol"; 
```
[4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L4), [6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L6)

</details>


---
### [NC&#x2011;109] Redundant inheritance specifier
The contracts below already extend the specified contract, so there is no need to list it in the inheritance list again.

<details>
<summary><i>There are 3 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/gov/TaikoGovernor.sol

/// @audit GovernorVotesQuorumFractionUpgradeable already extends GovernorVotesUpgradeable
16: contract TaikoGovernor is 
17:     EssentialContract,
18:     GovernorCompatibilityBravoUpgradeable,
19:     GovernorVotesUpgradeable,
20:     GovernorVotesQuorumFractionUpgradeable,
21:     GovernorTimelockControlUpgradeable
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L16-L21)

```solidity
📁 File: contracts/tokenvault/BridgedERC1155.sol

/// @audit ERC1155Upgradeable already extends IERC1155MetadataURIUpgradeable
14: contract BridgedERC1155 is EssentialContract, IERC1155MetadataURIUpgradeable, ERC1155Upgradeable { 
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L14)

```solidity
📁 File: contracts/tokenvault/BridgedERC20.sol

/// @audit ERC20Upgradeable already extends IERC20MetadataUpgradeable
15: contract BridgedERC20 is 
16:     BridgedERC20Base,
17:     IERC20MetadataUpgradeable,
18:     ERC20SnapshotUpgradeable,
19:     ERC20VotesUpgradeable
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L15-L19)

</details>


---
### [NC&#x2011;110] Redundant negation
The check below can just use `==`/`!=` instead of negating twice

<details>
<summary><i>There are 5 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/libs/LibProving.sol

/// @audit remove redundant '!' and refactor variable's value to 'msg.sender != _blk.assignedProver'
420:             if (!isAssignedPover) revert L1_NOT_ASSIGNED_PROVER(); 
```
[420](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L420)

```solidity
📁 File: contracts/bridge/Bridge.sol

/// @audit remove redundant '!' and refactor variable's value to 'receivedAt == 0'
171:         if (!isMessageProven) { 

/// @audit remove redundant '!' and refactor variable's value to 'receivedAt == 0'
209:         } else if (!isMessageProven) { 

/// @audit remove redundant '!' and refactor variable's value to 'receivedAt == 0'
235:         if (!isMessageProven) { 

/// @audit remove redundant '!' and refactor variable's value to 'receivedAt == 0'
302:         } else if (!isMessageProven) { 
```
[171](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L171), [209](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L209), [235](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L235), [302](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L302)

</details>


---
### [NC&#x2011;111] Returning a struct instead of a bunch of variables is better
If a function returns [too many variables](https://docs.soliditylang.org/en/v0.8.21/contracts.html#returning-multiple-values), replacing them with a struct can improve code readability, maintainability and reusability.

<details>
<summary><i>There are 5 instances of this issue:</i></summary>

```solidity
📁 File: contracts/automata-attestation/lib/PEMCertChainLib.sol

216:     function _removeHeadersAndFooters(string memory pemData) 
217:         private
218:         pure
219:         returns (bool success, bytes memory extracted, uint256 endIndex)
220:     {

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
[216](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L216-L220), [269](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L269-L283), [341](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L341-L348)

```solidity
📁 File: contracts/team/TimelockTokenPool.sol

176:     function getMyGrantSummary(address _recipient) 
177:         public
178:         view
179:         returns (
180:             uint128 amountOwned,
181:             uint128 amountUnlocked,
182:             uint128 amountWithdrawn,
183:             uint128 amountToWithdraw,
184:             uint128 costToWithdraw
185:         )
186:     {
```
[176](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L176-L186)

```solidity
📁 File: contracts/thirdparty/optimism/rlp/RLPReader.sol

144:     function _decodeLength(RLPItem memory _in) 
145:         private
146:         pure
147:         returns (uint256 offset_, uint256 length_, RLPItemType type_)
148:     {
```
[144](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L144-L148)

</details>


---
### [NC&#x2011;112] Simplify complex require statements
Simplifying complex `require` statements with local variables and `if`(or `revert`) statements can improve readability, make debugging easier, and promote modularity and reusability in the code.


<i>There are 3 instaces of this issue:</i>

```solidity
📁 File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

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

94:         require( 
95:             v3Quote.v3AuthData.ecdsa256BitSignature.length == 64
96:                 && v3Quote.v3AuthData.ecdsaAttestationKey.length == 64
97:                 && v3Quote.v3AuthData.qeReportSignature.length == 64,
98:             "Invalid ECDSA signature format"
99:         );
```
[77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L77-L86), [94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L94-L99)


---
### [NC&#x2011;113] Some contracts can be abstract
In Solidity, a contract that's not meant to be deployed on its own but is intended to be inherited by other contracts should be marked `abstract`. This ensures that developers recognize the contract's incomplete or intended-to-be-extended nature. If a contract has unimplemented functions or is designed with the intention that another contract should extend its functionality, it should be explicitly labeled as `abstract`. This helps prevent inadvertent deployments and clearly communicates the contract's purpose to other developers. Resolution: Review the contract, and if it's not supposed to function standalone, mark it as `abstract` to make the intention clear.

<details>
<summary><i>There are 6 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoData.sol

8: library TaikoData { 
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L8)

```solidity
📁 File: contracts/L1/tiers/ITierProvider.sol

37: library LibTiers { 
```
[37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L37)

```solidity
📁 File: contracts/automata-attestation/lib/EnclaveIdStruct.sol

6: library EnclaveIdStruct { 
```
[6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/EnclaveIdStruct.sol#L6)

```solidity
📁 File: contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol

6: library V3Struct { 
```
[6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L6)

```solidity
📁 File: contracts/automata-attestation/lib/TCBInfoStruct.sol

6: library TCBInfoStruct { 
```
[6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol#L6)

```solidity
📁 File: contracts/signal/LibSignals.sol

6: library LibSignals { 
```
[6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/LibSignals.sol#L6)

</details>


---
### [NC&#x2011;114] Some events are never emitted
The following events are never emitted, consider to remove them.


<i>There are 7 instaces of this issue:</i>

```solidity
📁 File: contracts/L1/TaikoEvents.sol

21:     event BlockProposed( 

37:     event BlockVerified( 

53:     event TransitionProved( 

67:     event TransitionContested( 

77:     event BlobCached(bytes32 blobHash); 

81:     event ProvingPaused(bool paused); 

86:     event EthDeposited(TaikoData.EthDeposit deposit); 
```
[21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L21), [37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L37), [53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L53), [67](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L67), [77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L77), [81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L81), [86](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L86)


---
### [NC&#x2011;115] Some variables have a implicit default visibility
Consider always adding an explicit visibility modifier for variables, as the default is `internal`.

<details>
<summary><i>There are 3 instances of this issue:</i></summary>

```solidity
📁 File: contracts/automata-attestation/lib/PEMCertChainLib.sol

32:     uint256 constant SGX_TCB_CPUSVN_SIZE = 16; 
```
[32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L32)

```solidity
📁 File: contracts/automata-attestation/utils/BytesUtils.sol

310:     bytes constant BASE32_HEX_TABLE = 
```
[310](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L310)

```solidity
📁 File: contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol

6:     uint256 constant LOW_28_MASK = 
```
[6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L6)

</details>


---
### [NC&#x2011;116] State variables should include comments
Consider adding some comments on critical state variables to explain what they are supposed to do: this will help for future code reviews.

<details>
<summary><i>There are 40 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoData.sol

64:         uint16 tier; 
65:         uint128 fee;

69:         uint16 tier; 
70:         bytes data;

74:         address hook; 
75:         bytes data;

79:         address assignedProver; 
80:         address coinbase;
81:         bytes32 extraData;
82:         bytes32 blobHash;
83:         uint24 txListByteOffset;
84:         uint24 txListByteSize;
85:         bool cacheBlobForReuse;
86:         bytes32 parentMetaHash;
87:         HookCall[] hookCalls;

102:         uint32 gasLimit; 

105:         uint24 txListByteOffset; 
106:         uint24 txListByteSize;
107:         uint16 minTier;
```
[64](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L64-L65), [69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L69-L70), [74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L74-L75), [79](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L79-L87), [102](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L102), [105](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L105-L107)

```solidity
📁 File: contracts/L1/gov/TaikoGovernor.sol

23:     uint256[50] private __gap; 
```
[23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L23)

```solidity
📁 File: contracts/L1/gov/TaikoTimelockController.sol

10:     uint256[50] private __gap; 
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L10)

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

19:         address feeToken; 
20:         uint64 expiry;
21:         uint64 maxBlockId;
22:         uint64 maxProposedIn;
23:         bytes32 metaHash;
24:         bytes32 parentMetaHash;
25:         TaikoData.TierFee[] tierFees;
26:         bytes signature;

30:         ProverAssignment assignment; 

40:     uint256[50] private __gap; 
```
[19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L19-L26), [30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L30), [40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L40)

```solidity
📁 File: contracts/L1/provers/GuardianProver.sol

11:     uint256[50] private __gap; 
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L11)

```solidity
📁 File: contracts/L1/provers/Guardians.sol

32:     uint256[46] private __gap; 
```
[32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L32)

```solidity
📁 File: contracts/common/AddressManager.sol

14:     uint256[49] private __gap; 
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L14)

```solidity
📁 File: contracts/common/AddressResolver.sol

14:     uint256[49] private __gap; 
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L14)

```solidity
📁 File: contracts/common/EssentialContract.sol

11:     uint8 private constant _FALSE = 1; 

13:     uint8 private constant _TRUE = 2; 

23:     uint8 private __paused; 

25:     uint256[49] private __gap; 
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L11), [13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L13), [23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L23), [25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L25)

```solidity
📁 File: contracts/libs/LibAddress.sol

14:     bytes4 private constant _EIP1271_MAGICVALUE = 0x1626ba7e; 
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L14)

</details>


---
### [NC&#x2011;117] The `nonReentrant` `modifier` should occur before all other modifiers
This is a best-practice to protect against reentrancy in other modifiers

<details>
<summary><i>There are 4 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/provers/GuardianProver.sol

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
```
[35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L35-L44)

```solidity
📁 File: contracts/L1/provers/Guardians.sol

53:     function setGuardians( 
54:         address[] memory _newGuardians,
55:         uint8 _minGuardians
56:     )
57:         external
58:         onlyOwner
59:         nonReentrant
60:     {
```
[53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L53-L60)

```solidity
📁 File: contracts/L2/TaikoL2.sol

163:     function withdraw( 
164:         address _token,
165:         address _to
166:     )
167:         external
168:         onlyFromOwnerOrNamed("withdrawer")
169:         nonReentrant
170:         whenNotPaused
171:     {
```
[163](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L163-L171)

```solidity
📁 File: contracts/bridge/Bridge.sol

101:     function banAddress( 
102:         address _addr,
103:         bool _ban
104:     )
105:         external
106:         onlyFromOwnerOrNamed("bridge_watchdog")
107:         nonReentrant
108:     {
```
[101](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L101-L108)

</details>


---
### [NC&#x2011;118] Top-level declarations should be separated by at least two lines
<details>
<summary><i>There are 40 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/ITaikoL1.sol

8: interface ITaikoL1 { 
9:     /// @notice Proposes a Taiko L2 block.
10:     /// @param _params Block parameters, currently an encoded BlockParams object.
11:     /// @param _txList txList data if calldata is used for DA.
12:     /// @return meta_ The metadata of the proposed L2 block.
13:     /// @return deposits_ The Ether deposits processed.
14:     function proposeBlock(
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/ITaikoL1.sol#L8-L14)

```solidity
📁 File: contracts/L1/gov/TaikoGovernor.sol

21:     GovernorTimelockControlUpgradeable 
22: {
23:     uint256[50] private __gap;
24: 
25:     error TG_INVALID_SIGNATURES_LENGTH();

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
[21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L21-L25), [125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L125-L127), [138](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L138-L140), [151](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L151-L153)

```solidity
📁 File: contracts/L1/gov/TaikoTimelockController.sol

9: contract TaikoTimelockController is EssentialContract, TimelockControllerUpgradeable { 
10:     uint256[50] private __gap;
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L9-L10)

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

14: contract AssignmentHook is EssentialContract, IHook { 
15:     using LibAddress for address;
16:     using SafeERC20 for IERC20;
17: 
18:     struct ProverAssignment {

48:     ); 
49: 
50:     error HOOK_ASSIGNMENT_EXPIRED();

162:     } 
163: 
164:     function _getProverFee(
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L14-L18), [48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L48-L50), [162](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L162-L164)

```solidity
📁 File: contracts/L1/hooks/IHook.sol

8: interface IHook { 
9:     /// @notice Called when a block is proposed.
10:     /// @param _blk The proposed block.
11:     /// @param _meta The metadata of the proposed block.
12:     /// @param _data The data of the proposed block.
13:     function onBlockProposed(
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/IHook.sol#L8-L13)

```solidity
📁 File: contracts/L1/libs/LibDepositing.sol

12: library LibDepositing { 
13:     using LibAddress for address;
14:     using LibAddress for address payable;
15:     using LibMath for uint256;
16: 
17:     /// @notice Emitted when Ether is deposited.
18:     /// @dev Any events defined here must also be defined in TaikoEvents.sol.
19:     event EthDeposited(TaikoData.EthDeposit deposit);
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L12-L19)

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

15: library LibProposing { 
16:     using LibAddress for address;
17: 
18:     /// @notice The maximum number of bytes allowed per blob.
19:     /// @dev According to EIP4844, each blob has up to 4096 field elements, and each
20:     /// field element has 32 bytes.
21:     uint256 public constant MAX_BYTES_PER_BLOB = 4096 * 32;

297:     } 
298: 
299:     function _isProposerPermitted(
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L15-L21), [297](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L297-L299)

```solidity
📁 File: contracts/L1/libs/LibProving.sol

16: library LibProving { 
17:     using LibMath for uint256;
18: 
19:     /// @notice Keccak hash of the string "RETURN_LIVENESS_BOND".
20:     bytes32 public constant RETURN_LIVENESS_BOND = keccak256("RETURN_LIVENESS_BOND");
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L16-L20)

```solidity
📁 File: contracts/L1/libs/LibUtils.sol

9: library LibUtils { 
10:     // Warning: Any errors defined here must also be defined in TaikoErrors.sol.
11:     error L1_BLOCK_MISMATCH();
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L9-L11)

```solidity
📁 File: contracts/L1/libs/LibVerifying.sol

16: library LibVerifying { 
17:     using LibMath for uint256;
18: 
19:     // Warning: Any events defined here must also be defined in TaikoEvents.sol.
20:     /// @notice Emitted when a block is verified.
21:     /// @param blockId The block ID.
22:     /// @param assignedProver The assigned prover of the block.
23:     /// @param prover The actual prover of the block.
24:     /// @param blockHash The block hash.
25:     /// @param stateRoot The state root.
26:     /// @param tier The tier of the transition used for verification.
27:     /// @param contestations The number of contestations.
28:     event BlockVerified(

222:     } 
223: 
224:     function _syncChainData(

243:     } 
244: 
245:     function _isConfigValid(TaikoData.Config memory _config) private view returns (bool) {
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L16-L28), [222](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L222-L224), [243](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L243-L245)

```solidity
📁 File: contracts/common/AddressManager.sol

10: contract AddressManager is EssentialContract, IAddressManager { 
11:     /// @dev Mapping of chainId to mapping of name to address.
12:     mapping(uint256 chainId => mapping(bytes32 name => address addr)) private __addresses;

23:     ); 
24: 
25:     error AM_INVALID_PARAMS();

56:     } 
57: 
58:     function _authorizePause(address) internal pure override {

60:     } 
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L10-L12), [23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L23-L25), [56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L56-L58), [60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L60-L12)

```solidity
📁 File: contracts/common/AddressResolver.sol

11: abstract contract AddressResolver is IAddressResolver, Initializable { 
12:     /// @notice Address of the AddressManager.
13:     address public addressManager;
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L11-L13)

```solidity
📁 File: contracts/common/EssentialContract.sol

10: abstract contract EssentialContract is UUPSUpgradeable, Ownable2StepUpgradeable, AddressResolver { 
11:     uint8 private constant _FALSE = 1;

107:     } 
108: 
109:     function __Essential_init(address _owner) internal virtual {

112:     } 
113: 
114:     function _authorizeUpgrade(address) internal virtual override onlyOwner { }
115: 
116:     function _authorizePause(address) internal virtual onlyOwner { }

138:     } 
139: 
140:     function _inNonReentrant() internal view returns (bool) {
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L10-L11), [107](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L107-L109), [112](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L112-L116), [138](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L138-L140)

```solidity
📁 File: contracts/common/IAddressManager.sol

7: interface IAddressManager { 
8:     /// @notice Gets the address mapped to a specific chainId-name pair.
9:     /// @dev Note that in production, this method shall be a pure function
10:     /// without any storage access.
11:     /// @param _chainId The chainId for which the address needs to be fetched.
12:     /// @param _name The name for which the address needs to be fetched.
13:     /// @return Address associated with the chainId-name pair.
14:     function getAddress(uint64 _chainId, bytes32 _name) external view returns (address);
```
[7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressManager.sol#L7-L14)

```solidity
📁 File: contracts/common/IAddressResolver.sol

13: interface IAddressResolver { 
14:     /// @notice Resolves a name to its address deployed on this chain.
15:     /// @param _name Name whose address is to be resolved.
16:     /// @param _allowZeroAddress If set to true, does not throw if the resolved
17:     /// address is `address(0)`.
18:     /// @return Address associated with the given name.
19:     function resolve(
```
[13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressResolver.sol#L13-L19)

```solidity
📁 File: contracts/libs/Lib4844.sol

8: library Lib4844 { 
9:     /// @notice The address of the point evaluation precompile
10:     address public constant POINT_EVALUATION_PRECOMPILE_ADDRESS = address(0x0A);
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L8-L10)

```solidity
📁 File: contracts/libs/LibAddress.sol

13: library LibAddress { 
14:     bytes4 private constant _EIP1271_MAGICVALUE = 0x1626ba7e;
15: 
16:     error ETH_TRANSFER_FAILED();

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
[13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L13-L16), [44](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L44-L46), [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L59-L61), [75](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L75-L77)

```solidity
📁 File: contracts/libs/LibMath.sol

7: library LibMath { 
8:     /// @dev Returns the smaller of the two given values.
9:     /// @param _a The first number to compare.
10:     /// @param _b The second number to compare.
11:     /// @return The smaller of the two numbers.
12:     function min(uint256 _a, uint256 _b) internal pure returns (uint256) {
```
[7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibMath.sol#L7-L12)

```solidity
📁 File: contracts/libs/LibTrieProof.sol

15: library LibTrieProof { 
16:     // The consensus format representing account is RLP encoded in the
17:     // following order: nonce, balance, storageHash, codeHash.
18:     uint256 private constant _ACCOUNT_FIELD_INDEX_STORAGE_HASH = 2;
19: 
20:     error LTP_INVALID_ACCOUNT_PROOF();
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L15-L20)

</details>


---
### [NC&#x2011;119] Unnecessary cast
The variable is being cast to its own type

<details>
<summary><i>There are 7 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

/// @audit block.coinbase
121:             address(block.coinbase).sendEther(input.tip); 
```
[121](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L121)

```solidity
📁 File: contracts/L2/Lib1559Math.sol

/// @audit input
45:         return uint256(LibFixedPointMath.exp(int256(input))); 
```
[45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L45)

```solidity
📁 File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

/// @audit encoded[i]
154:             uint256 digits = uint256(uint8(bytes1(encoded[i]))); 
```
[154](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L154)

```solidity
📁 File: contracts/automata-attestation/utils/BytesUtils.sol

/// @audit diff
97:                     return int256(diff); 

/// @audit len
/// @audit otherlen
104:         return int256(len) - int256(otherlen); 
```
[97](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L97), [104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L104)

```solidity
📁 File: contracts/thirdparty/solmate/LibFixedPointMath.sol

76:             r = int256( 
77:                 (uint256(r) * 3_822_833_074_963_236_453_042_738_258_902_158_003_155_416_615_667)
78:                     >> uint256(195 - k)
79:             );
```
[76](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L76-L79)

</details>


---
### [NC&#x2011;120] Unused `error` definition
The following errors are never used, consider to remove them.

<details>
<summary><i>There are 36 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoErrors.sol

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
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoErrors.sol#L12-L42)

```solidity
📁 File: contracts/L1/provers/Guardians.sol

48:     error INVALID_PROOF(); 
```
[48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L48)

```solidity
📁 File: contracts/L1/tiers/ITierProvider.sol

17:     error TIER_NOT_FOUND(); 
```
[17](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L17)

```solidity
📁 File: contracts/tokenvault/BaseNFTVault.sol

134:     error VAULT_INVALID_AMOUNT(); 
135:     error VAULT_INVALID_TO();
136:     error VAULT_INTERFACE_NOT_SUPPORTED();
```
[134](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L134-L136)

</details>


---
### [NC&#x2011;121] Unused `event` definition
The following events are never used, consider to remove them.


<i>There are 7 instaces of this issue:</i>

```solidity
📁 File: contracts/L1/TaikoEvents.sol

21:     event BlockProposed( 
22:         uint256 indexed blockId,
23:         address indexed assignedProver,
24:         uint96 livenessBond,
25:         TaikoData.BlockMetadata meta,
26:         TaikoData.EthDeposit[] depositsProcessed
27:     );

37:     event BlockVerified( 
38:         uint256 indexed blockId,
39:         address indexed assignedProver,
40:         address indexed prover,
41:         bytes32 blockHash,
42:         bytes32 stateRoot,
43:         uint16 tier,
44:         uint8 contestations
45:     );

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

86:     event EthDeposited(TaikoData.EthDeposit deposit); 
```
[21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L21-L27), [37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L37-L45), [53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L53-L59), [67](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L67-L73), [77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L77), [81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L81), [86](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L86)


---
### [NC&#x2011;122] Unused `modifier` definition
The following modifier are never used, consider to remove them.

<details>
<summary><i>There are 4 instances of this issue:</i></summary>

```solidity
📁 File: contracts/common/AddressResolver.sol

24:     modifier onlyFromNamed(bytes32 _name) { 
25:         if (msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();
26:         _;
27:     }
```
[24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L24-L27)

```solidity
📁 File: contracts/common/EssentialContract.sol

41:     modifier onlyFromOwnerOrNamed(bytes32 _name) { 
42:         if (msg.sender != owner() && msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();
43:         _;
44:     }

46:     modifier nonReentrant() { 
47:         if (_loadReentryLock() == _TRUE) revert REENTRANT_CALL();
48:         _storeReentryLock(_TRUE);
49:         _;
50:         _storeReentryLock(_FALSE);
51:     }
```
[41](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L41-L44), [46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L46-L51)

```solidity
📁 File: contracts/tokenvault/BaseNFTVault.sol

140:     modifier withValidOperation(BridgeTransferOp memory _op) { 
141:         if (_op.tokenIds.length != _op.amounts.length) {
142:             revert VAULT_TOKEN_ARRAY_MISMATCH();
143:         }
144: 
145:         if (_op.tokenIds.length > MAX_TOKEN_PER_TXN) {
146:             revert VAULT_MAX_TOKEN_PER_TXN_EXCEEDED();
147:         }
148: 
149:         if (_op.token == address(0)) revert VAULT_INVALID_TOKEN();
150:         _;
151:     }
```
[140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L140-L151)

</details>


---
### [NC&#x2011;123] Unused `struct` definition
Note that there may be cases where a struct superficially appears to be used, but this is only because there are multiple definitions of the struct in different files. In such cases, the struct definition should be moved into a separate file. The instances below are the unused definitions.


<i>There is one instance of this issue:</i>

```solidity
📁 File: contracts/automata-attestation/interfaces/ISigVerifyLib.sol

24:     struct Certificate { 
25:         // Asn.1 DER encoding of the to-be-signed certificate
26:         bytes tbsCertificate;
27:         PublicKey publicKey;
28:         bytes signature;
29:         CertSigAlgorithm sigAlg;
30:     }
```
[24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L24-L30)


---
### [NC&#x2011;124] Unusual loop variable
The normal name for loop variables is `i`, and when there is a nested loop, to use `j`. Not following this convention may lead to some reviewer confusion


<i>There is one instance of this issue:</i>

```solidity
📁 File: contracts/automata-attestation/utils/BytesUtils.sol

80:         for (uint256 idx = 0; idx < shortest; idx += 32) { 
```
[80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L80)


---
### [NC&#x2011;125] Upgradeable contract not initialized
Upgradeable contracts are initialized via an initializer function rather than by a constructor. Leaving such a contract uninitialized may lead to it being taken over by a malicious user.

<details>
<summary><i>There are 6 instances of this issue:</i></summary>

```solidity
📁 File: contracts/common/EssentialContract.sol

/// @audit __UUPS_init();
/// @audit __Ownable2Step_init();
10: abstract contract EssentialContract is UUPSUpgradeable, Ownable2StepUpgradeable, AddressResolver { 
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L10)

```solidity
📁 File: contracts/tokenvault/BaseVault.sol

/// @audit __IERC165_init();
12: abstract contract BaseVault is 
13:     EssentialContract,
14:     IRecallableSender,
15:     IMessageInvocable,
16:     IERC165Upgradeable
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L12-L16)

```solidity
📁 File: contracts/tokenvault/BridgedERC1155.sol

/// @audit __IERC1155MetadataURI_init();
14: contract BridgedERC1155 is EssentialContract, IERC1155MetadataURIUpgradeable, ERC1155Upgradeable { 
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L14)

```solidity
📁 File: contracts/tokenvault/BridgedERC20.sol

/// @audit __IERC20Metadata_init();
15: contract BridgedERC20 is 
16:     BridgedERC20Base,
17:     IERC20MetadataUpgradeable,
18:     ERC20SnapshotUpgradeable,
19:     ERC20VotesUpgradeable
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L15-L19)

```solidity
📁 File: contracts/tokenvault/ERC1155Vault.sol

/// @audit __ERC1155Receiver_init();
29: contract ERC1155Vault is BaseNFTVault, ERC1155ReceiverUpgradeable { 
```
[29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L29)

</details>


---
### [NC&#x2011;126] Use `@inheritdoc` for overridden functions
<details>
<summary><i>There are 40 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/TaikoL1.sol

220:     function _authorizePause(address) 
221:         internal
222:         view
223:         virtual
224:         override
225:         onlyFromOwnerOrNamed("chain_pauser")
226:     { }
```
[220](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L220-L226)

```solidity
📁 File: contracts/L1/TaikoToken.sol

60:     function transfer(address _to, uint256 _amount) public override returns (bool) { 

70:     function transferFrom( 
71:         address _from,
72:         address _to,
73:         uint256 _amount
74:     )
75:         public
76:         override
77:         returns (bool)
78:     {

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
[60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L60), [70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L70-L78), [83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L83-L90), [94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L94-L101), [105](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L105-L111), [115](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L115-L121)

```solidity
📁 File: contracts/L1/gov/TaikoGovernor.sol

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

111:     function votingDelay() public pure override returns (uint256) { 

117:     function votingPeriod() public pure override returns (uint256) { 

123:     function proposalThreshold() public pure override returns (uint256) { 

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
[48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L48-L57), [69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L69-L80), [89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L89-L94), [99](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L99-L104), [111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L111), [117](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L117), [123](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L123), [127](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L127-L136), [140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L140-L149), [153](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L153-L158)

```solidity
📁 File: contracts/L1/gov/TaikoTimelockController.sol

24:     function getMinDelay() public view override returns (uint256) { 
```
[24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L24)

```solidity
📁 File: contracts/bridge/Bridge.sol

461:     function _authorizePause(address) 
462:         internal
463:         view
464:         virtual
465:         override
466:         onlyFromOwnerOrNamed("bridge_pauser")
467:     { }
```
[461](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L461-L467)

```solidity
📁 File: contracts/common/AddressManager.sol

58:     function _authorizePause(address) internal pure override { 
```
[58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L58)

```solidity
📁 File: contracts/common/EssentialContract.sol

114:     function _authorizeUpgrade(address) internal virtual override onlyOwner { } 
```
[114](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L114)

```solidity
📁 File: contracts/signal/SignalService.sol

231:     function _authorizePause(address) internal pure override { 
```
[231](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L231)

```solidity
📁 File: contracts/tokenvault/BaseVault.sol

39:     function supportsInterface(bytes4 _interfaceId) public view virtual override returns (bool) { 
```
[39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L39)

```solidity
📁 File: contracts/tokenvault/BridgedERC1155.sol

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
[125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L125-L136)

```solidity
📁 File: contracts/tokenvault/BridgedERC20.sol

91:     function name() 
92:         public
93:         view
94:         override(ERC20Upgradeable, IERC20MetadataUpgradeable)
95:         returns (string memory)
96:     {

102:     function symbol() 
103:         public
104:         view
105:         override(ERC20Upgradeable, IERC20MetadataUpgradeable)
106:         returns (string memory)
107:     {

113:     function decimals() 
114:         public
115:         view
116:         override(ERC20Upgradeable, IERC20MetadataUpgradeable)
117:         returns (uint8)
118:     {

129:     function _mintToken(address _account, uint256 _amount) internal override { 

133:     function _burnToken(address _from, uint256 _amount) internal override { 

139:     function _beforeTokenTransfer( 
140:         address _from,
141:         address _to,
142:         uint256 _amount
143:     )
144:         internal
145:         override(ERC20Upgradeable, ERC20SnapshotUpgradeable)
146:     {

152:     function _afterTokenTransfer( 
153:         address _from,
154:         address _to,
155:         uint256 _amount
156:     )
157:         internal
158:         override(ERC20Upgradeable, ERC20VotesUpgradeable)
159:     {

163:     function _mint( 
164:         address _to,
165:         uint256 _amount
166:     )
167:         internal
168:         override(ERC20Upgradeable, ERC20VotesUpgradeable)
169:     {

173:     function _burn( 
174:         address _from,
175:         uint256 _amount
176:     )
177:         internal
178:         override(ERC20Upgradeable, ERC20VotesUpgradeable)
179:     {
```
[91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L91-L96), [102](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L102-L107), [113](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L113-L118), [129](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L129), [133](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L133), [139](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L139-L146), [152](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L152-L159), [163](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L163-L169), [173](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L173-L179)

```solidity
📁 File: contracts/tokenvault/BridgedERC20Base.sol

93:     function owner() public view override(IBridgedERC20, OwnableUpgradeable) returns (address) { 
```
[93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L93)

```solidity
📁 File: contracts/tokenvault/BridgedERC721.sol

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
[87](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L87), [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L93), [107](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L107), [115](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L115-L124)

```solidity
📁 File: contracts/tokenvault/adapters/USDCAdapter.sol

43:     function _mintToken(address _account, uint256 _amount) internal override { 

47:     function _burnToken(address _from, uint256 _amount) internal override { 
```
[43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L43), [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L47)

</details>


---
### [NC&#x2011;127] Use a single file for system wide constants
Consider grouping all the system constants under a single file. This finding shows only the first constant for each file, for brevity.

<details>
<summary><i>There are 40 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

21:     uint256 public constant MAX_BYTES_PER_BLOB = 4096 * 32; 
```
[21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L21)

```solidity
📁 File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

29:     uint256 internal constant CPUSVN_LENGTH = 16; 

33:     bytes32 internal constant ROOTCA_PUBKEY_HASH = 
34:         0x89f72d7c488e5b53a77c23ebcb36970ef7eb5bcf6658e9b8292cfbe4703a8473;

36:     uint8 internal constant INVALID_EXIT_CODE = 255; 
```
[29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L29), [33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L33-L34), [36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L36)

```solidity
📁 File: contracts/automata-attestation/lib/PEMCertChainLib.sol

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
[17](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L17-L20), [22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L22-L29), [32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L32)

```solidity
📁 File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

14:     uint256 internal constant MINIMUM_QUOTE_LENGTH = 1020; 
15:     bytes2 internal constant SUPPORTED_QUOTE_VERSION = 0x0300;
16:     bytes2 internal constant SUPPORTED_ATTESTATION_KEY_TYPE = 0x0200;

18:     bytes4 internal constant SUPPORTED_TEE_TYPE = 0; 
19:     bytes16 internal constant VALID_QE_VENDOR_ID = 0x939a7233f79c4ca9940a0db3957f0607;
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L14-L16), [18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L18-L19)

```solidity
📁 File: contracts/automata-attestation/utils/BytesUtils.sol

310:     bytes constant BASE32_HEX_TABLE = 
311:         hex"00010203040506070809FFFFFFFFFFFFFF0A0B0C0D0E0F101112131415161718191A1B1C1D1E1FFFFFFFFFFFFFFFFFFFFF0A0B0C0D0E0F101112131415161718191A1B1C1D1E1F";
```
[310](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L310-L311)

```solidity
📁 File: contracts/common/EssentialContract.sol

11:     uint8 private constant _FALSE = 1; 

13:     uint8 private constant _TRUE = 2; 
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L11), [13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L13)

```solidity
📁 File: contracts/libs/LibTrieProof.sol

18:     uint256 private constant _ACCOUNT_FIELD_INDEX_STORAGE_HASH = 2; 
```
[18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L18)

```solidity
📁 File: contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol

6:     uint256 constant LOW_28_MASK = 
7:         0x00000000ffffffffffffffffffffffffffffffffffffffffffffffffffffffff;
```
[6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L6-L7)

```solidity
📁 File: contracts/thirdparty/optimism/rlp/RLPReader.sol

30:     uint256 internal constant MAX_LIST_LENGTH = 32; 
```
[30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L30)

```solidity
📁 File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

21:     uint256 internal constant TREE_RADIX = 16; 

24:     uint256 internal constant BRANCH_NODE_LENGTH = TREE_RADIX + 1; 

27:     uint256 internal constant LEAF_OR_EXTENSION_NODE_LENGTH = 2; 

30:     uint8 internal constant PREFIX_EXTENSION_EVEN = 0; 

33:     uint8 internal constant PREFIX_EXTENSION_ODD = 1; 

36:     uint8 internal constant PREFIX_LEAF_EVEN = 2; 

39:     uint8 internal constant PREFIX_LEAF_ODD = 3; 
```
[21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L21), [24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L24), [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L27), [30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L30), [33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L33), [36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L36), [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L39)

```solidity
📁 File: contracts/thirdparty/solmate/LibFixedPointMath.sol

7:     uint128 public constant MAX_EXP_INPUT = 135_305_999_368_893_231_588; 
8:     uint256 public constant SCALING_FACTOR = 1e18; // For fixed point representation factor
```
[7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L7-L8)

```solidity
📁 File: contracts/tokenvault/BaseNFTVault.sol

53:     uint256 public constant MAX_TOKEN_PER_TXN = 10; 
```
[53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L53)

```solidity
📁 File: contracts/verifiers/SgxVerifier.sol

30:     uint64 public constant INSTANCE_EXPIRY = 180 days; 

34:     uint64 public constant INSTANCE_VALIDITY_DELAY = 1 days; 
```
[30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L30), [34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L34)

</details>


---
### [NC&#x2011;128] Use a struct to encapsulate multiple function parameters
If a function has too many parameters, replacing them with a struct can improve code readability and maintainability, increase reusability, and reduce the likelihood of errors when passing the parameters.

<details>
<summary><i>There are 16 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/gov/TaikoGovernor.sol

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
[69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L69-L80), [127](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L127-L136)

```solidity
📁 File: contracts/automata-attestation/utils/BytesUtils.sol

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
```
[56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L56-L67), [116](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L116-L126)

```solidity
📁 File: contracts/automata-attestation/utils/X509DateUtils.sol

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
```
[34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L34-L45)

```solidity
📁 File: contracts/libs/Lib4844.sol

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
[30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L30-L39)

```solidity
📁 File: contracts/libs/LibTrieProof.sol

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
45:     {
```
[34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L34-L45)

```solidity
📁 File: contracts/team/airdrop/ERC20Airdrop.sol

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
[27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L27-L37)

```solidity
📁 File: contracts/team/airdrop/ERC20Airdrop2.sol

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
[54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L54-L65)

```solidity
📁 File: contracts/team/airdrop/ERC721Airdrop.sol

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
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L25-L35)

```solidity
📁 File: contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol

25:     function excessivelySafeCall( 
26:         address _target,
27:         uint256 _gas,
28:         uint256 _value,
29:         uint16 _maxCopy,
30:         bytes memory _calldata
31:     )
32:         internal
33:         returns (bool, bytes memory)
34:     {
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L25-L34)

```solidity
📁 File: contracts/tokenvault/BridgedERC1155.sol

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
[38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L38-L48), [125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L125-L136)

```solidity
📁 File: contracts/tokenvault/BridgedERC20.sol

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
[52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L52-L63)

```solidity
📁 File: contracts/tokenvault/BridgedERC721.sol

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
[31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L31-L41)

```solidity
📁 File: contracts/tokenvault/ERC1155Vault.sol

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
170:     {
```
[160](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L160-L170)

</details>


---
### [NC&#x2011;129] Use `bytes.concat()` on bytes instead of `abi.encodePacked()` for clearer semantic meaning
Starting with version 0.8.4, Solidity has the `bytes.concat()` function, which allows one to concatenate a list of bytes/strings, without extra padding. Using this function rather than `abi.encodePacked()` makes the intended operation more clear, leading to less reviewer confusion.

<details>
<summary><i>There are 11 instances of this issue:</i></summary>

```solidity
📁 File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

315:             abi.encodePacked(authDataV3.ecdsaAttestationKey, authDataV3.qeAuthData.data); 
```
[315](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L315)

```solidity
📁 File: contracts/automata-attestation/lib/PEMCertChainLib.sol

181:             cert.signature = abi.encodePacked(sigX, sigY); 
```
[181](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L181)

```solidity
📁 File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

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
[119](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L119-L127), [129](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L129)

```solidity
📁 File: contracts/thirdparty/optimism/rlp/RLPWriter.sol

17:             out_ = abi.encodePacked(_writeLength(_in.length, 128), _in); 
```
[17](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L17)

```solidity
📁 File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

81:         bytes memory currentNodeID = abi.encodePacked(_root); 

94:                     Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID), 

100:                     Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID), 
```
[81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L81), [94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L94), [100](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L100)

```solidity
📁 File: contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol

55:         hash_ = abi.encodePacked(keccak256(_key)); 
```
[55](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L55)

```solidity
📁 File: contracts/tokenvault/BridgedERC721.sol

109:             abi.encodePacked( 
110:                 LibBridgedToken.buildURI(srcToken, srcChainId), Strings.toString(_tokenId)
111:             )
```
[109](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L109-L111)

```solidity
📁 File: contracts/tokenvault/LibBridgedToken.sol

54:             abi.encodePacked( 
55:                 "ethereum:",
56:                 Strings.toHexString(uint160(_srcToken), 20),
57:                 "@",
58:                 Strings.toString(_srcChainId),
59:                 "/tokenURI?uint256="
60:             )
```
[54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L54-L60)

</details>


---
### [NC&#x2011;130] Use delete instead of assigning values to `false`
The `delete` keyword more closely matches the semantics of what is being done, and draws more attention to the changing of state, which may lead to a more thorough audit of its associated logic.

<details>
<summary><i>There are 2 instances of this issue:</i></summary>

```solidity
📁 File: contracts/automata-attestation/utils/RsaVerify.sol

129:             hasNullParam = false; 
```
[129](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L129)

```solidity
📁 File: contracts/bridge/Bridge.sol

495:             success_ = false; 
```
[495](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L495)

</details>


---
### [NC&#x2011;131] Use OpenZeppelin's `MerkleProof` rather than rolling your own
Use [MerkleProof](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/8b2ed0f5706fe1a7ab6ade84b27bf875dc611fda/contracts/utils/cryptography/MerkleProof.sol#L6-L20) for handling Merkle tree proofs, since the general advice is "don't roll your own crypto".

<details>
<summary><i>There are 9 instances of this issue:</i></summary>

```solidity
📁 File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

50:     function verifyInclusionProof( 
51:         bytes memory _key,
52:         bytes memory _value,
53:         bytes[] memory _proof,
54:         bytes32 _root
55:     )
56:         internal
57:         pure
58:         returns (bool valid_)
59:     {
60:         valid_ = Bytes.equal(_value, get(_key, _proof, _root));
61:     }

68:     function get( 
69:         bytes memory _key,
70:         bytes[] memory _proof,
71:         bytes32 _root
72:     )
73:         internal
74:         pure
75:         returns (bytes memory value_)
76:     {
77:         require(_key.length > 0, "MerkleTrie: empty key");
78: 
79:         TrieNode[] memory proof = _parseProof(_proof);
80:         bytes memory key = Bytes.toNibbles(_key);
81:         bytes memory currentNodeID = abi.encodePacked(_root);
82:         uint256 currentKeyIndex = 0;
83: 
84:         // Proof is top-down, so we start at the first element (root).
85:         for (uint256 i = 0; i < proof.length; i++) {
86:             TrieNode memory currentNode = proof[i];
87: 
88:             // Key index should never exceed total key length or we'll be out of bounds.
89:             require(currentKeyIndex <= key.length, "MerkleTrie: key index exceeds total key length");
90: 
91:             if (currentKeyIndex == 0) {
92:                 // First proof element is always the root node.
93:                 require(
94:                     Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
95:                     "MerkleTrie: invalid root hash"
96:                 );
97:             } else if (currentNode.encoded.length >= 32) {
98:                 // Nodes 32 bytes or larger are hashed inside branch nodes.
99:                 require(
100:                     Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
101:                     "MerkleTrie: invalid large internal hash"
102:                 );
103:             } else {
104:                 // Nodes smaller than 32 bytes aren't hashed.
105:                 require(
106:                     Bytes.equal(currentNode.encoded, currentNodeID),
107:                     "MerkleTrie: invalid internal node hash"
108:                 );
109:             }
110: 
111:             if (currentNode.decoded.length == BRANCH_NODE_LENGTH) {
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
132:                     // We're not at the end of the key yet.
133:                     // Figure out what the next node ID should be and continue.
134:                     uint8 branchKey = uint8(key[currentKeyIndex]);
135:                     RLPReader.RLPItem memory nextNode = currentNode.decoded[branchKey];
136:                     currentNodeID = _getNodeID(nextNode);
137:                     currentKeyIndex += 1;
138:                 }
139:             } else if (currentNode.decoded.length == LEAF_OR_EXTENSION_NODE_LENGTH) {
140:                 bytes memory path = _getNodePath(currentNode);
141:                 uint8 prefix = uint8(path[0]);
142:                 uint8 offset = 2 - (prefix % 2);
143:                 bytes memory pathRemainder = Bytes.slice(path, offset);
144:                 bytes memory keyRemainder = Bytes.slice(key, currentKeyIndex);
145:                 uint256 sharedNibbleLength = _getSharedNibbleLength(pathRemainder, keyRemainder);
146: 
147:                 // Whether this is a leaf node or an extension node, the path remainder MUST be a
148:                 // prefix of the key remainder (or be equal to the key remainder) or the proof is
149:                 // considered invalid.
150:                 require(
151:                     pathRemainder.length == sharedNibbleLength,
152:                     "MerkleTrie: path remainder must share all nibbles with key"
153:                 );
154: 
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
185:                     // Prefix of 0 or 1 means this is an extension node. We move onto the next node
186:                     // in the proof and increment the key index by the length of the path remainder
187:                     // which is equal to the shared nibble length.
188:                     currentNodeID = _getNodeID(currentNode.decoded[1]);
189:                     currentKeyIndex += sharedNibbleLength;
190:                 } else {
191:                     revert("MerkleTrie: received a node with an unknown prefix");
192:                 }
193:             } else {
194:                 revert("MerkleTrie: received an unparseable node");
195:             }
196:         }
197: 
198:         revert("MerkleTrie: ran out of proof elements");
199:     }

205:     function _parseProof(bytes[] memory _proof) private pure returns (TrieNode[] memory proof_) { 
206:         uint256 length = _proof.length;
207:         proof_ = new TrieNode[](length);
208:         for (uint256 i = 0; i < length;) {
209:             proof_[i] = TrieNode({ encoded: _proof[i], decoded: RLPReader.readList(_proof[i]) });
210:             unchecked {
211:                 ++i;
212:             }
213:         }
214:     }

220:     function _getNodeID(RLPReader.RLPItem memory _node) private pure returns (bytes memory id_) { 
221:         id_ = _node.length < 32 ? RLPReader.readRawBytes(_node) : RLPReader.readBytes(_node);
222:     }

227:     function _getNodePath(TrieNode memory _node) private pure returns (bytes memory nibbles_) { 
228:         nibbles_ = Bytes.toNibbles(RLPReader.readBytes(_node.decoded[0]));
229:     }

235:     function _getSharedNibbleLength( 
236:         bytes memory _a,
237:         bytes memory _b
238:     )
239:         private
240:         pure
241:         returns (uint256 shared_)
242:     {
243:         uint256 max = (_a.length < _b.length) ? _a.length : _b.length;
244:         for (; shared_ < max && _a[shared_] == _b[shared_];) {
245:             unchecked {
246:                 ++shared_;
247:             }
248:         }
249:     }
```
[50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L50-L61), [68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L68-L199), [205](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L205-L214), [220](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L220-L222), [227](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L227-L229), [235](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L235-L249)

```solidity
📁 File: contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol

19:     function verifyInclusionProof( 
20:         bytes memory _key,
21:         bytes memory _value,
22:         bytes[] memory _proof,
23:         bytes32 _root
24:     )
25:         internal
26:         pure
27:         returns (bool valid_)
28:     {
29:         bytes memory key = _getSecureKey(_key);
30:         valid_ = MerkleTrie.verifyInclusionProof(key, _value, _proof, _root);
31:     }

38:     function get( 
39:         bytes memory _key,
40:         bytes[] memory _proof,
41:         bytes32 _root
42:     )
43:         internal
44:         pure
45:         returns (bytes memory value_)
46:     {
47:         bytes memory key = _getSecureKey(_key);
48:         value_ = MerkleTrie.get(key, _proof, _root);
49:     }

54:     function _getSecureKey(bytes memory _key) private pure returns (bytes memory hash_) { 
55:         hash_ = abi.encodePacked(keccak256(_key));
56:     }
```
[19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L19-L31), [38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L38-L49), [54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L54-L56)

</details>


---
### [NC&#x2011;132] Use OpenZeppelin's `ReentrancyGuard`/`ReentrancyGuardUpgradeable` rather than writing your own
The OpenZeppelin version has been gas-optimized, and thoroughly test, so consider using it rather than writing your own.


<i>There is one instance of this issue:</i>

```solidity
📁 File: contracts/common/EssentialContract.sol

46:     modifier nonReentrant() { 
47:         if (_loadReentryLock() == _TRUE) revert REENTRANT_CALL();
48:         _storeReentryLock(_TRUE);
49:         _;
50:         _storeReentryLock(_FALSE);
51:     }
```
[46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L46-L51)


---
### [NC&#x2011;133] Use UPPER_CASE for `immutable`
Immutables should be in uppercase as stated [Solidity style guide](https://docs.soliditylang.org/en/latest/style-guide.html#constants).


<i>There are 2 instaces of this issue:</i>

```solidity
📁 File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

25:     ISigVerifyLib public immutable sigVerifyLib; 
26:     IPEMCertChainLib public immutable pemCertLib;
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L25-L26)


---
### [NC&#x2011;134] Variable names that consist of all capital letters should be reserved for `constant`/`immutable` variables
Variable names with all capital letters should be restricted to be used only with `constant` or `immutable` variables. 
If the variable needs to be different based on which class it comes from, a `view`/`pure` function should be used instead (e.g. like <a href="https://github.com/OpenZeppelin/openzeppelin-contracts/blob/76eee35971c2541585e05cbf258510dda7b2fbc6/contracts/token/ERC20/extensions/draft-IERC20Permit.sol#L59">this</a>).


<i>There is one instance of this issue:</i>

```solidity
📁 File: contracts/automata-attestation/utils/SigVerifyLib.sol

18:     address private ES256VERIFIER; 
```
[18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L18)


---
### [NC&#x2011;135] `variable`/`struct`/`contract` names should be descriptive rather than cryptic
<details>
<summary><i>There are 40 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/gov/TaikoTimelockController.sol

17:         address[] memory nil = new address[](0); 
```
[17](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L17)

```solidity
📁 File: contracts/L1/hooks/AssignmentHook.sol

101:         IERC20 tko = IERC20(resolve("taiko_token", false)); 
```
[101](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L101)

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

93:         TaikoData.SlotB memory b = _state.slotB; 

212:         TaikoData.Block memory blk = TaikoData.Block({ 
213:             metaHash: keccak256(abi.encode(meta_)),
214:             // Safeguard the liveness bond to ensure its preservation,
215:             // particularly in scenarios where it might be altered after the
216:             // block's proposal but before it has been proven or verified.
217:             livenessBond: _config.livenessBond,
218:             blockId: b.numBlocks,
219:             proposedAt: meta_.timestamp,
220:             proposedIn: uint64(block.number),
221:             // For a new block, the next transition ID is always 1, not 0.
222:             nextTransitionId: 1,
223:             // For unverified block, its verifiedTransitionId is always 0.
224:             verifiedTransitionId: 0,
225:             assignedProver: params.assignedProver
226:         });

237:             IERC20 tko = IERC20(_resolver.resolve("taiko_token", false)); 
```
[93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L93), [212](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L212-L226), [237](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L237)

```solidity
📁 File: contracts/L1/libs/LibProving.sol

110:         TaikoData.SlotB memory b = _state.slotB; 

116:         TaikoData.Block storage blk = _state.blocks[slot]; 

/// @audit tid
/// @audit ts
129:         (uint32 tid, TaikoData.TransitionState storage ts) = 
130:             _createTransition(_state, blk, _tran, slot);

166:                 IVerifier.Context memory ctx = IVerifier.Context({ 
167:                     metaHash: blk.metaHash,
168:                     blobHash: _meta.blobHash,
169:                     // Separate msgSender to allow the prover to be any address in the future.
170:                     prover: msg.sender,
171:                     msgSender: msg.sender,
172:                     blockId: blk.blockId,
173:                     isContesting: isContesting,
174:                     blobUsed: _meta.blobUsed
175:                 });

187:         IERC20 tko = IERC20(_resolver.resolve("taiko_token", false)); 
```
[110](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L110), [116](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L116), [129](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L129-L130), [166](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L166-L175), [187](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L187)

```solidity
📁 File: contracts/L1/libs/LibUtils.sol

33:         TaikoData.SlotB memory b = _state.slotB; 

39:         TaikoData.Block storage blk = _state.blocks[slot]; 

42:         uint32 tid = getTransitionId(_state, blk, slot, _parentHash); 
```
[33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L33), [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L39), [42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L42)

```solidity
📁 File: contracts/L1/libs/LibVerifying.sol

62:         TaikoData.Block storage blk = _state.blocks[0]; 

68:         TaikoData.TransitionState storage ts = _state.transitions[0][1]; 

99:         TaikoData.SlotB memory b = _state.slotB; 

104:         TaikoData.Block storage blk = _state.blocks[slot]; 

107:         uint32 tid = blk.verifiedTransitionId; 

140:                 TaikoData.TransitionState storage ts = _state.transitions[slot][tid]; 

188:                 IERC20 tko = IERC20(_resolver.resolve("taiko_token", false)); 
```
[62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L62), [68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L68), [99](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L99), [104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L104), [107](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L107), [140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L140), [188](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L188)

```solidity
📁 File: contracts/L2/CrossChainOwned.sol

45:         IBridge.Context memory ctx = IBridge(msg.sender).context(); 
```
[45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L45)

```solidity
📁 File: contracts/libs/Lib4844.sol

/// @audit ok
/// @audit ret
43:         (bool ok, bytes memory ret) = POINT_EVALUATION_PRECOMPILE_ADDRESS.staticcall( 
44:             abi.encodePacked(_blobHash, _x, _y, _commitment, _pointProof)
45:         );
```
[43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L43-L45)

```solidity
📁 File: contracts/signal/SignalService.sol

98:         address app = _app; 

103:         HopProof memory hop; 
```
[98](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L98), [103](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L103)

```solidity
📁 File: contracts/thirdparty/optimism/rlp/RLPReader.sol

42:         MemoryPointer ptr; 

157:         MemoryPointer ptr = _in.ptr; 

294:         uint256 src = MemoryPointer.unwrap(_src) + _offset; 
```
[42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L42), [157](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L157), [294](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L294)

```solidity
📁 File: contracts/thirdparty/optimism/rlp/RLPWriter.sol

56:         bytes memory b = abi.encodePacked(_x); 
```
[56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L56)

```solidity
📁 File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

80:         bytes memory key = Bytes.toNibbles(_key); 

243:         uint256 max = (_a.length < _b.length) ? _a.length : _b.length; 
```
[80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L80), [243](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L243)

```solidity
📁 File: contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol

29:         bytes memory key = _getSecureKey(_key); 

47:         bytes memory key = _getSecureKey(_key); 
```
[29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L29), [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L47)

```solidity
📁 File: contracts/tokenvault/ERC1155Vault.sol

104:         IBridge.Context memory ctx = checkProcessMessageContext(); 

262:                 IERC1155NameAndSymbol t = IERC1155NameAndSymbol(_op.token); 
```
[104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L104), [262](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L262)

```solidity
📁 File: contracts/tokenvault/ERC20Vault.sol

263:         IBridge.Context memory ctx = checkProcessMessageContext(); 

377:             IERC20 t = IERC20(_token); 
```
[263](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L263), [377](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L377)

```solidity
📁 File: contracts/tokenvault/ERC721Vault.sol

87:         IBridge.Context memory ctx = checkProcessMessageContext(); 

201:                 ERC721Upgradeable t = ERC721Upgradeable(_op.token); 
```
[87](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L87), [201](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L201)

</details>


---
### [NC&#x2011;136] Variables need not be initialized to zero
The default value for variables is zero, so initializing them to zero is superfluous.

<details>
<summary><i>There are 12 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/provers/Guardians.sol

80:         for (uint256 i = 0; i < _newGuardians.length; ++i) { 
```
[80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L80)

```solidity
📁 File: contracts/automata-attestation/lib/PEMCertChainLib.sol

51:         uint256 index = 0; 
```
[51](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L51)

```solidity
📁 File: contracts/automata-attestation/utils/BytesUtils.sol

80:         for (uint256 idx = 0; idx < shortest; idx += 32) { 

331:         uint256 ret = 0; 
```
[80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L80), [331](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L331)

```solidity
📁 File: contracts/automata-attestation/utils/X509DateUtils.sol

46:         uint256 timestamp = 0; 
```
[46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L46)

```solidity
📁 File: contracts/thirdparty/optimism/rlp/RLPReader.sol

72:         uint256 itemCount = 0; 
```
[72](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L72)

```solidity
📁 File: contracts/thirdparty/optimism/rlp/RLPWriter.sol

58:         uint256 i = 0; 

66:         for (uint256 j = 0; j < out_.length; j++) { 
```
[58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L58), [66](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66)

```solidity
📁 File: contracts/thirdparty/optimism/trie/MerkleTrie.sol

30:     uint8 internal constant PREFIX_EXTENSION_EVEN = 0; 

82:         uint256 currentKeyIndex = 0; 

85:         for (uint256 i = 0; i < proof.length; i++) { 

208:         for (uint256 i = 0; i < length;) { 
```
[30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L30), [82](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L82), [85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85), [208](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L208)

</details>


---
### [NC&#x2011;137] Variables should be named in mixedCase style
As the [Solidity Style Guide](https://docs.soliditylang.org/en/latest/style-guide.html#naming-styles) suggests: arguments, local variables and mutable state variables should be named in mixedCase style.

Rule exceptions
- Allow constant variable name/symbol/decimals to be lowercase (ERC20).
- Allow `_` at the beginning of the mixedCase match for `private variables` and `unused parameters`.

<details>
<summary><i>There are 40 instances of this issue:</i></summary>

```solidity
📁 File: contracts/common/AddressManager.sol

/// @audit _owner
30:     function init(address _owner) external initializer { 

/// @audit _chainId
39:         uint64 _chainId, 
/// @audit _name
40:         bytes32 _name,
/// @audit _newAddress
41:         address _newAddress

/// @audit _chainId
/// @audit _name
54:     function getAddress(uint64 _chainId, bytes32 _name) public view override returns (address) { 
```
[30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L30), [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L39-L41), [54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L54)

```solidity
📁 File: contracts/common/AddressResolver.sol

/// @audit _name
31:         bytes32 _name, 
/// @audit _allowZeroAddress
32:         bool _allowZeroAddress

/// @audit _chainId
44:         uint64 _chainId, 
/// @audit _name
45:         bytes32 _name,
/// @audit _allowZeroAddress
46:         bool _allowZeroAddress

/// @audit _addressManager
58:     function __AddressResolver_init(address _addressManager) internal virtual onlyInitializing { 

/// @audit _chainId
73:         uint64 _chainId, 
/// @audit _name
74:         bytes32 _name,
/// @audit _allowZeroAddress
75:         bool _allowZeroAddress

/// @audit addr_
79:         returns (address payable addr_) 
```
[31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L31-L32), [44](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L44-L46), [58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L58), [73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L73-L75), [79](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L79)

```solidity
📁 File: contracts/common/EssentialContract.sol

/// @audit _owner
96:         address _owner, 
/// @audit _addressManager
97:         address _addressManager

/// @audit _owner
109:     function __Essential_init(address _owner) internal virtual { 

/// @audit _reentry
119:     function _storeReentryLock(uint8 _reentry) internal virtual { 

/// @audit reentry_
130:     function _loadReentryLock() internal view virtual returns (uint8 reentry_) { 
```
[96](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L96-L97), [109](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L109), [119](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L119), [130](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L130)

```solidity
📁 File: contracts/libs/Lib4844.sol

/// @audit _blobHash
31:         bytes32 _blobHash, 
/// @audit _x
32:         uint256 _x,
/// @audit _y
33:         uint256 _y,
/// @audit _commitment
34:         bytes1[48] memory _commitment,
/// @audit _pointProof
35:         bytes1[48] memory _pointProof
```
[31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L31-L35)

```solidity
📁 File: contracts/libs/LibAddress.sol

/// @audit _to
/// @audit _amount
/// @audit _gasLimit
22:     function sendEther(address _to, uint256 _amount, uint256 _gasLimit) internal { 

/// @audit _to
/// @audit _amount
42:     function sendEther(address _to, uint256 _amount) internal { 

/// @audit _addr
47:         address _addr, 
/// @audit _interfaceId
48:         bytes4 _interfaceId

/// @audit result_
52:         returns (bool result_) 

/// @audit _addr
62:         address _addr, 
/// @audit _hash
63:         bytes32 _hash,
/// @audit _sig
64:         bytes memory _sig
```
[22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L22), [42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L42), [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L47-L48), [52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L52), [62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L62-L64)

```solidity
📁 File: contracts/libs/LibMath.sol

/// @audit _a
/// @audit _b
12:     function min(uint256 _a, uint256 _b) internal pure returns (uint256) { 

/// @audit _a
20:     function max(uint256 _a, uint256 _b) internal pure returns (uint256) { 
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibMath.sol#L12), [20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibMath.sol#L20)

</details>


---
### [NC&#x2011;138] Zero as a function argument should have a descriptive meaning
Consider using descriptive constants or an enum instead of passing zero directly on function calls, as that might be error-prone, to fully describe the caller's intention.

<details>
<summary><i>There are 28 instances of this issue:</i></summary>

```solidity
📁 File: contracts/L1/gov/TaikoTimelockController.sol

17:         address[] memory nil = new address[](0); 
```
[17](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L17)

```solidity
📁 File: contracts/L1/libs/LibDepositing.sol

79:             deposits_ = new TaikoData.EthDeposit[](0); 
```
[79](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L79)

```solidity
📁 File: contracts/L1/libs/LibProposing.sol

121:             meta_ = TaikoData.BlockMetadata({ 
122:                 l1Hash: blockhash(block.number - 1),
123:                 difficulty: 0, // to be initialized below
124:                 blobHash: 0, // to be initialized below
125:                 extraData: params.extraData,
126:                 depositsHash: keccak256(abi.encode(deposits_)),
127:                 coinbase: params.coinbase,
128:                 id: b.numBlocks,
129:                 gasLimit: _config.blockMaxGasLimit,
130:                 timestamp: uint64(block.timestamp),
131:                 l1Height: uint64(block.number - 1),
132:                 txListByteOffset: 0, // to be initialized below
133:                 txListByteSize: 0, // to be initialized below
134:                 minTier: 0, // to be initialized below
135:                 blobUsed: _txList.length == 0,
136:                 parentMetaHash: parentMetaHash
137:             });

157:                 meta_.blobHash = blockhash(0); 

212:         TaikoData.Block memory blk = TaikoData.Block({ 
213:             metaHash: keccak256(abi.encode(meta_)),
214:             // Safeguard the liveness bond to ensure its preservation,
215:             // particularly in scenarios where it might be altered after the
216:             // block's proposal but before it has been proven or verified.
217:             livenessBond: _config.livenessBond,
218:             blockId: b.numBlocks,
219:             proposedAt: meta_.timestamp,
220:             proposedIn: uint64(block.number),
221:             // For a new block, the next transition ID is always 1, not 0.
222:             nextTransitionId: 1,
223:             // For unverified block, its verifiedTransitionId is always 0.
224:             verifiedTransitionId: 0,
225:             assignedProver: params.assignedProver
226:         });
```
[121](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L121-L137), [157](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L157), [212](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L212-L226)

```solidity
📁 File: contracts/L1/libs/LibProving.sol

230:                 emit TransitionProved({ 
231:                     blockId: blk.blockId,
232:                     tran: _tran,
233:                     prover: msg.sender,
234:                     validityBond: 0,
235:                     tier: _proof.tier
236:                 });
```
[230](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L230-L236)

```solidity
📁 File: contracts/L1/libs/LibVerifying.sol

73:         emit BlockVerified({ 
74:             blockId: 0,
75:             assignedProver: address(0),
76:             prover: address(0),
77:             blockHash: _genesisBlockHash,
78:             stateRoot: 0,
79:             tier: 0,
80:             contestations: 0
81:         });

234:         (uint64 lastSyncedBlock,) = signalService.getSyncedChainData( 
235:             _config.chainId, LibSignals.STATE_ROOT, 0 /* latest block Id*/
236:         );
```
[73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L73-L81), [234](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L234-L236)

```solidity
📁 File: contracts/L1/tiers/DevnetTierProvider.sol

33:             return ITierProvider.Tier({ 
34:                 verifierName: "tier_guardian",
35:                 validityBond: 0, // must be 0 for top tier
36:                 contestBond: 0, // must be 0 for top tier
37:                 cooldownWindow: 60, //1 hours
38:                 provingWindow: 2880, // 48 hours
39:                 maxBlocksToVerifyPerProof: 16
40:             });
```
[33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L33-L40)

```solidity
📁 File: contracts/L1/tiers/MainnetTierProvider.sol

44:             return ITierProvider.Tier({ 
45:                 verifierName: "tier_guardian",
46:                 validityBond: 0, // must be 0 for top tier
47:                 contestBond: 0, // must be 0 for top tier
48:                 cooldownWindow: 60, //1 hours
49:                 provingWindow: 2880, // 48 hours
50:                 maxBlocksToVerifyPerProof: 16
51:             });
```
[44](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L44-L51)

```solidity
📁 File: contracts/L1/tiers/TestnetTierProvider.sol

44:             return ITierProvider.Tier({ 
45:                 verifierName: "tier_guardian",
46:                 validityBond: 0, // must be 0 for top tier
47:                 contestBond: 0, // must be 0 for top tier
48:                 cooldownWindow: 60, //1 hours
49:                 provingWindow: 2880, // 48 hours
50:                 maxBlocksToVerifyPerProof: 16
51:             });
```
[44](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L44-L51)

```solidity
📁 File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

313:         bytes32 expectedAuthDataHash = bytes32(qeEnclaveReport.reportData.substring(0, 32)); 
```
[313](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L313)

```solidity
📁 File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

38:         bytes memory rawHeader = quote.substring(0, 48); 

138:         enclaveReport.cpuSvn = bytes16(rawEnclaveReport.substring(0, 16)); 

170:         bytes2 version = bytes2(rawHeader.substring(0, 2)); 

227:         authDataV3.ecdsa256BitSignature = rawAuthData.substring(0, 64); 
```
[38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L38), [138](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L138), [170](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L170), [227](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L227)

```solidity
📁 File: contracts/automata-attestation/utils/Asn1Decode.sol

48:         return _readNodeLength(der, 0); 
```
[48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L48)

```solidity
📁 File: contracts/automata-attestation/utils/BytesUtils.sol

40:         return compare(self, 0, self.length, other, 0, other.length); 

179:         return self.length == other.length && equals(self, 0, other, 0, self.length); 
```
[40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L40), [179](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L179)

```solidity
📁 File: contracts/automata-attestation/utils/SigVerifyLib.sol

89:         bytes memory exponent = publicKey.substring(0, 3); 

106:         bytes memory exponent = publicKey.substring(0, 3); 

126:         uint256 r = uint256(bytes32(signature.substring(0, 32))); 

132:         uint256 gx = uint256(bytes32(publicKey.substring(0, 32))); 
```
[89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L89), [106](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L106), [126](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L126), [132](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L132)

```solidity
📁 File: contracts/thirdparty/optimism/rlp/RLPReader.sol

136:         out_ = _copy(_in.ptr, 0, _in.length); 
```
[136](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L136)

```solidity
📁 File: contracts/tokenvault/ERC1155Vault.sol

58:         IBridge.Message memory message = IBridge.Message({ 
59:             id: 0, // will receive a new value
60:             from: address(0), // will receive a new value
61:             srcChainId: 0, // will receive a new value
62:             destChainId: _op.destChainId,
63:             srcOwner: msg.sender,
64:             destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,
65:             to: resolve(_op.destChainId, name(), false),
66:             refundTo: _op.refundTo,
67:             value: msg.value - _op.fee,
68:             fee: _op.fee,
69:             gasLimit: _op.gasLimit,
70:             data: data,
71:             memo: _op.memo
72:         });
```
[58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L58-L72)

```solidity
📁 File: contracts/tokenvault/ERC20Vault.sol

221:         IBridge.Message memory message = IBridge.Message({ 
222:             id: 0, // will receive a new value
223:             from: address(0), // will receive a new value
224:             srcChainId: 0, // will receive a new value
225:             destChainId: _op.destChainId,
226:             srcOwner: msg.sender,
227:             destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,
228:             to: resolve(_op.destChainId, name(), false),
229:             refundTo: _op.refundTo,
230:             value: msg.value - _op.fee,
231:             fee: _op.fee,
232:             gasLimit: _op.gasLimit,
233:             data: data,
234:             memo: _op.memo
235:         });
```
[221](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L221-L235)

```solidity
📁 File: contracts/tokenvault/ERC721Vault.sol

44:         IBridge.Message memory message = IBridge.Message({ 
45:             id: 0, // will receive a new value
46:             from: address(0), // will receive a new value
47:             srcChainId: 0, // will receive a new value
48:             destChainId: _op.destChainId,
49:             srcOwner: msg.sender,
50:             destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,
51:             to: resolve(_op.destChainId, name(), false),
52:             refundTo: _op.refundTo,
53:             value: msg.value - _op.fee,
54:             fee: _op.fee,
55:             gasLimit: _op.gasLimit,
56:             data: data,
57:             memo: _op.memo
58:         });
```
[44](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L44-L58)

```solidity
📁 File: contracts/verifiers/SgxVerifier.sol

154:         uint32 id = uint32(bytes4(Bytes.slice(_proof.data, 0, 4))); 
```
[154](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L154)

</details>
