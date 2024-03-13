## Summary
## Gas Optimizations


| |Issue|Instances|Gas Saved|
|-|:-|:-:|-:|
| [GAS-1](#GAS-1-1705424649) | Consider using OZ EnumerateSet in place of nested mappings | 6 | 6000 |
| [GAS-2](#GAS-2-1706546944) | Optimize Deployment Size by Fine-tuning IPFS Hash | 85 | 901000 |
| [GAS-3](#GAS-3-1706545887) | Trade-offs Between Modifiers and Internal Functions | 127 | 3937 |
| [GAS-4](#GAS-4-1705426850) | Avoid emitting event on every iteration | 4 | 1500 |
| [GAS-5](#GAS-5-1693311630) | Use assembly to check for `address(0)` | 53 | 318 |
| [GAS-6](#GAS-6-1693311540) | Multiple accesses of a mapping/array should use a local variable cache | 44 | 1848 |
| [GAS-7](#GAS-7-1706548063) | Use assembly scratch space to build calldata for external calls | 53 | 11660 |
| [GAS-8](#GAS-8-1693311599) | Use assembly to calculate hashes to save gas | 28 | 2240 |
| [GAS-9](#GAS-9-1693311663) | Use assembly in place of `abi.decode` to extract `calldata` values more efficiently | 6 | - |
| [GAS-10](#GAS-10-1693311695) | Optimize Address Storage Value Management with `assembly` | 7 | - |
| [GAS-11](#GAS-11-1693311732) | Use assembly to emit events | 55 | 2090 |
| [GAS-12](#GAS-12-1693311770) | Avoid contract existence checks by using low level calls | 1 | 100 |
| [GAS-13](#GAS-13-1693311856) | Using bools for storage incurs overhead | 17 | 1700 |
| [GAS-14](#GAS-14-1693311879) | Use byte32 in place of string | 2 | - |
| [GAS-15](#GAS-15-1693311904) | Cache array length outside of loop | 29 | 2813 |
| [GAS-16](#GAS-16-1693311936) | State variables should be cached in stack variables rather than re-reading them from storage | 6 | 582 |
| [GAS-17](#GAS-17-1699447317) | Avoid caching global special variables | 1 | 12 |
| [GAS-18](#GAS-18-1693311951) | Use calldata instead of memory for function arguments that do not get mutated | 12 | - |
| [GAS-19](#GAS-19-1693312015) | Add `unchecked {}` for subtractions where the operands cannot underflow because of a previous `require()` or `if`-statement | 4 | 340 |
| [GAS-20](#GAS-20-1693312028) | `x += y` costs more gas than `x = x + y` for state variables | 4 | 452 |
| [GAS-21](#GAS-21-1699456351) | Gas savings can be achieved by changing the model for assigning value to the structure ***123 gas*** | 19 | 2337 |
| [GAS-22](#GAS-22-1696084432) | Simple checks for zero `uint` can be done using assembly to save gas | 58 | 348 |
| [GAS-23](#GAS-23-1708173673) | Combine `mapping`s referenced in the same function by the same key | 1 | 42 |
| [GAS-24](#GAS-24-1706544439) | Counting down in for statements is more gas efficient | 45 | - |
| [GAS-25](#GAS-25-1693312067) | Use custom errors rather than `revert()`/`require()` strings to save gas | 66 | - |
| [GAS-26](#GAS-26-1693312114) | Divisions which do not divide by -X cannot overflow or overflow so such operations can be unchecked to save gas | 13 | - |
| [GAS-27](#GAS-27-1693312130) | Do not calculate constants | 2 | 800 |
| [GAS-28](#GAS-28-1694877823) | Use `do while` loops instead of `for` loops | 49 | 5929 |
| [GAS-29](#GAS-29-1693312160) | Stack variable cost less while used in emiting event | 13 | 1300 |
| [GAS-30](#GAS-30-1693312222) | Events should be emitted outside of loops | 3 | 1125 |
| [GAS-31](#GAS-31-1693312189) | Superfluous event fields | 1 | - |
| [GAS-32](#GAS-32-1693312238) | Empty blocks should be removed or emit something | 1 | - |
| [GAS-33](#GAS-33-1693312400) | Don't initialize `uint` variables with default value | 11 | - |
| [GAS-34](#GAS-34-1693312433) | `internal` functions only called once can be inlined to save gas | 12 | 240 |
| [GAS-35](#GAS-35-1693312466) | Inverting the condition of an `if`-`else`-statement wastes gas | 2 | - |
| [GAS-36](#GAS-36-1693312497) | `require()`/`revert()` strings longer than 32 bytes cost extra gas | 30 | 540 |
| [GAS-37](#GAS-37-1709385160) | Memory-safe annotation missing | 34 | - |
| [GAS-38](#GAS-38-1693312508) | Consider merging sequential for loops | 6 | - |
| [GAS-39](#GAS-39-1709377588) | Avoid emitting event on every iteration | 4 | 1500 |
| [GAS-40](#GAS-40-1702129464) | Refactor modifiers to call a local function | 7 | 7000 |
| [GAS-41](#GAS-41-1696084349) | A `modifier` used only once and not being inherited should be inlined to save gas | 2 | - |
| [GAS-42](#GAS-42-1693312642) | Multiple `address`/ID mappings can be combined into a single `mapping` of an `address`/ID to a `struct`, where appropriate | 7 | - |
| [GAS-43](#GAS-43-1693312655) | Optimize names to save gas | 39 | 858 |
| [GAS-44](#GAS-44-1693312684) | Not using the named return variables anywhere in the function wast gas | 7 | 21 |
| [GAS-45](#GAS-45-1707917994) | Use more recent OpenZeppelin version for gas boost | 71 | - |
| [GAS-46](#GAS-46-1694875070) | State variables can be packed into fewer storage slots | 5 | 10000 |
| [GAS-47](#GAS-47-1693312720) | Structs can be packed into fewer storage slots | 6 | 12000 |
| [GAS-48](#GAS-48-1693312741) | Constructors can be marked `payable` | 3 | 63 |
| [GAS-49](#GAS-49-1699444393) | Initializer can be marked `payable` | 24 | 504 |
| [GAS-50](#GAS-50-1693316170) | `++i` costs less gas than `i++`, especially when it's used in `for`-loops (`--i`/`i--` too) | 11 | - |
| [GAS-51](#GAS-51-1696084477) | `++i`/`i++` should be `unchecked{++i}`/`unchecked{i++}` when it is not possible for them to overflow, as is the case when used in `for`- and `while`-loops | 39 | - |
| [GAS-52](#GAS-52-1709377106) | Consider pre-calculating the address of `address(this)` to save gas | 40 | - |
| [GAS-53](#GAS-53-1693312824) | Using `private` rather than `public` for constants, saves gas | 21 | - |
| [GAS-54](#GAS-54-1693312893) | `private` functions only called once can be inlined to save gas | 26 | - |
| [GAS-55](#GAS-55-1699451217) | Redundant state variable getters | 1 | - |
| [GAS-56](#GAS-56-1709385583) | Reduce deployment costs by tweaking contracts' metadata | 85 | - |
| [GAS-57](#GAS-57-1693312940) | Redundant else statement | 12 | - |
| [GAS-58](#GAS-58-1693312958) | Functions guaranteed to revert when called by normal users can be marked `payable` | 49 | 1029 |
| [GAS-59](#GAS-59-1693312972) | Avoid updating storage when the value hasn't changed to save gas | 4 | 3200 |
| [GAS-60](#GAS-60-1693312999) | Use shift Left instead of multiplication if possible to save gas | 6 | - |
| [GAS-61](#GAS-61-1693313015) | Usage of `uints`/`ints` smaller than 32 bytes (256 bits) incurs overhead | 174 | - |
| [GAS-62](#GAS-62-1693313026) | The use of a logical AND in place of double if is slightly less gas efficient in instances where there isn't a corresponding else statement for the given if statement | 15 | 225 |
| [GAS-63](#GAS-63-1693313038) | Splitting `require()` statements that use `&&` saves gas | 4 | 12 |
| [GAS-64](#GAS-64-1709389408) | Split `revert` checks to save gas | 26 | 52 |
| [GAS-65](#GAS-65-1693313099) | Cache state variables outside of loop to avoid reading storage on every iteration | 7 | - |
| [GAS-66](#GAS-66-1693311457) | State variable read in a loop | 7 | - |
| [GAS-67](#GAS-67-1693313054) | State variables only set in the constructor should be declared `immutable` | 2 | 4194 |
| [GAS-68](#GAS-68-1693313071) | Stack variable used as a cheaper cache for a state variable is only used once | 170 | 510 |
| [GAS-69](#GAS-69-1693313108) | Using `storage` instead of `memory` for structs/arrays saves gas | 13 | 54600 |
| [GAS-70](#GAS-70-1693313130) | `>=`/`<=` costs less gas than `>`/`<` | 81 | 243 |
| [GAS-71](#GAS-71-1695857615) | Avoid transferring amounts of zero in order to save gas | 19 | - |
| [GAS-72](#GAS-72-1693313275) | Use assembly to validate `msg.sender` | 20 | 240 |
| [GAS-73](#GAS-73-1699451597) | Using `constant`s instead of `enum` can save gas | 10 | - |
| [GAS-74](#GAS-74-1696083995) | When no `addresses` are used `abi.encodepacked()` Outperforms `abi.encode()` in Efficiency | 10 | 610 |
| [GAS-75](#GAS-75-1705427608) | Consider using solady's 'FixedPointMathLib' | 46 | - |
| [GAS-76](#GAS-76-1694794906) | Using mappings instead of arrays to avoid length checks save gas | 1 | - |
| [GAS-77](#GAS-77-1699443465) | Using `private` for constants saves gas | 23 | - |
| [GAS-78](#GAS-78-1702131709) | Use `solady` library where possible to save gas | 11 | - |
| [GAS-79](#GAS-79-1707922603) | Use Array.unsafeAccess() to avoid repeated array length checks | 64 | 134400 |
| [GAS-80](#GAS-80-1693313317) | Can make the variable outside the loop to save gas | 59 | - |
| [GAS-81](#GAS-81-1693313355) | Consider activating via-ir for deploying | 1 | 250 |

Total: 2142 instances over 81 issues with ** 1180764 gas ** saved


### <a name="GAS-1-1705424649"></a>[GAS-1] Consider using OZ EnumerateSet in place of nested mappings
Nested mappings and multi-dimensional arrays in Solidity operate through a process of double hashing, wherein the original storage slot and the first key are concatenated and hashed, and then this hash is again concatenated with the second key and hashed. This process can be quite gas expensive due to the double-hashing operation and subsequent storage operation (sstore).

A possible optimization involves manually concatenating the keys followed by a single hash operation and an sstore.However, this technique introduces the risk of storage collision, especially when there are other nested hash maps in the contract that use the same key types.Because Solidity is unaware of the number and structure of nested hash maps in a contract, it follows a conservative approach in computing the storage slot to avoid possible collisions.

OpenZeppelin's EnumerableSet provides a potential solution to this problem. It creates a data structure that combines the benefits of set operations with the ability to enumerate stored elements, which is not natively available in Solidity. EnumerableSet handles the element uniqueness internally and can therefore provide a more gas-efficient and collision-resistant alternative to nested mappings or multi-dimensional arrays in certain scenarios.

*Instances (6)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/provers/Guardians.sol

19:     mapping(uint32 version => mapping(bytes32 hash => uint256 approvalBits)) internal _approvals;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/provers/Guardians.sol#L19-L19)

```solidity
File: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

47:     mapping(uint256 idx => mapping(bytes serialNum => bool revoked)) private _serialNumIsRevoked;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/AutomataDcapV3Attestation.sol#L47-L47)

```solidity
File: /contracts/common/AddressManager.sol

12:     mapping(uint256 chainId => mapping(bytes32 name => address addr)) private __addresses;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/common/AddressManager.sol#L12-L12)

```solidity
File: /contracts/signal/SignalService.sol

17:     mapping(uint64 chainId => mapping(bytes32 kind => uint64 blockId)) public topBlockId;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/SignalService.sol#L17-L17)

```solidity
File: /contracts/tokenvault/BaseNFTVault.sol

59:     mapping(uint256 chainId => mapping(address ctoken => address btoken)) public canonicalToBridged;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BaseNFTVault.sol#L59-L59)

```solidity
File: /contracts/tokenvault/ERC20Vault.sol

49:     mapping(uint256 chainId => mapping(address ctoken => address btoken)) public canonicalToBridged;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC20Vault.sol#L49-L49)

</details>

### <a name="GAS-2-1706546944"></a>[GAS-2] Optimize Deployment Size by Fine-tuning IPFS Hash
Optimizing the deployment size of a smart contract is vital to minimize gas costs, and one way to achieve this is by fine-tuning the IPFS hash appended by the Solidity compiler as metadata. This metadata, consisting of 53 bytes, increases the gas required for contract deployment by approximately 10,600 gas due to bytecode costs, and additionally, up to 848 gas due to calldata costs, depending on the proportion of zero and non-zero bytes. Utilize the --no-cbor-metadata compiler flag to prevent the compiler from appending metadata. However, this approach has a drawback as it can complicate the contract verification process on block explorers like Etherscan, potentially reducing transparency.

*Instances (85)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/ITaikoL1.sol

8: interface ITaikoL1 {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/ITaikoL1.sol#L8)

```solidity
File: /contracts/L1/TaikoData.sol

8: library TaikoData {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/TaikoData.sol#L8)

```solidity
File: /contracts/L1/TaikoErrors.sol

11: abstract contract TaikoErrors {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/TaikoErrors.sol#L11)

```solidity
File: /contracts/L1/TaikoEvents.sol

13: abstract contract TaikoEvents {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/TaikoEvents.sol#L13)

```solidity
File: /contracts/L1/TaikoL1.sol

22: contract TaikoL1 is EssentialContract, ITaikoL1, TaikoEvents, TaikoErrors {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/TaikoL1.sol#L22)

```solidity
File: /contracts/L1/TaikoToken.sol

15: contract TaikoToken is EssentialContract, ERC20SnapshotUpgradeable, ERC20VotesUpgradeable {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/TaikoToken.sol#L15)

```solidity
File: /contracts/L1/gov/TaikoGovernor.sol

16: contract TaikoGovernor is

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/gov/TaikoGovernor.sol#L16)

```solidity
File: /contracts/L1/gov/TaikoTimelockController.sol

9: contract TaikoTimelockController is EssentialContract, TimelockControllerUpgradeable {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/gov/TaikoTimelockController.sol#L9)

```solidity
File: /contracts/L1/hooks/AssignmentHook.sol

14: contract AssignmentHook is EssentialContract, IHook {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/hooks/AssignmentHook.sol#L14)

```solidity
File: /contracts/L1/hooks/IHook.sol

8: interface IHook {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/hooks/IHook.sol#L8)

```solidity
File: /contracts/L1/libs/LibDepositing.sol

12: library LibDepositing {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibDepositing.sol#L12)

```solidity
File: /contracts/L1/libs/LibProposing.sol

15: library LibProposing {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProposing.sol#L15)

```solidity
File: /contracts/L1/libs/LibProving.sol

16: library LibProving {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProving.sol#L16)

```solidity
File: /contracts/L1/libs/LibUtils.sol

9: library LibUtils {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibUtils.sol#L9)

```solidity
File: /contracts/L1/libs/LibVerifying.sol

16: library LibVerifying {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibVerifying.sol#L16)

```solidity
File: /contracts/L1/provers/GuardianProver.sol

10: contract GuardianProver is Guardians {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/provers/GuardianProver.sol#L10)

```solidity
File: /contracts/L1/provers/Guardians.sol

9: abstract contract Guardians is EssentialContract {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/provers/Guardians.sol#L9)

```solidity
File: /contracts/L1/tiers/DevnetTierProvider.sol

10: contract DevnetTierProvider is EssentialContract, ITierProvider {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/tiers/DevnetTierProvider.sol#L10)

```solidity
File: /contracts/L1/tiers/ITierProvider.sol

7: interface ITierProvider {

37: library LibTiers {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/tiers/ITierProvider.sol#L37)

```solidity
File: /contracts/L1/tiers/MainnetTierProvider.sol

10: contract MainnetTierProvider is EssentialContract, ITierProvider {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/tiers/MainnetTierProvider.sol#L10)

```solidity
File: /contracts/L1/tiers/TestnetTierProvider.sol

10: contract TestnetTierProvider is EssentialContract, ITierProvider {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/tiers/TestnetTierProvider.sol#L10)

```solidity
File: /contracts/L2/CrossChainOwned.sol

14: abstract contract CrossChainOwned is EssentialContract, IMessageInvocable {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/CrossChainOwned.sol#L14)

```solidity
File: /contracts/L2/Lib1559Math.sol

10: library Lib1559Math {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/Lib1559Math.sol#L10)

```solidity
File: /contracts/L2/TaikoL2.sol

21: contract TaikoL2 is CrossChainOwned {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/TaikoL2.sol#L21)

```solidity
File: /contracts/L2/TaikoL2EIP1559Configurable.sol

9: contract TaikoL2EIP1559Configurable is TaikoL2 {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/TaikoL2EIP1559Configurable.sol#L9)

```solidity
File: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

22: contract AutomataDcapV3Attestation is IAttestation {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/AutomataDcapV3Attestation.sol#L22)

```solidity
File: /contracts/automata-attestation/interfaces/IAttestation.sol

8: interface IAttestation {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/interfaces/IAttestation.sol#L8)

```solidity
File: /contracts/automata-attestation/interfaces/ISigVerifyLib.sol

6: interface ISigVerifyLib {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L6)

```solidity
File: /contracts/automata-attestation/lib/EnclaveIdStruct.sol

6: library EnclaveIdStruct {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/EnclaveIdStruct.sol#L6)

```solidity
File: /contracts/automata-attestation/lib/PEMCertChainLib.sol

12: contract PEMCertChainLib is IPEMCertChainLib {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/PEMCertChainLib.sol#L12)

```solidity
File: /contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

11: library V3Parser {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L11)

```solidity
File: /contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol

6: library V3Struct {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L6)

```solidity
File: /contracts/automata-attestation/lib/TCBInfoStruct.sol

6: library TCBInfoStruct {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/TCBInfoStruct.sol#L6)

```solidity
File: /contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol

6: interface IPEMCertChainLib {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L6)

```solidity
File: /contracts/automata-attestation/utils/Asn1Decode.sol

12: library NodePtr {

38: library Asn1Decode {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/Asn1Decode.sol#L38)

```solidity
File: /contracts/automata-attestation/utils/BytesUtils.sol

8: library BytesUtils {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/BytesUtils.sol#L8)

```solidity
File: /contracts/automata-attestation/utils/RsaVerify.sol

34: library RsaVerify {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/RsaVerify.sol#L34)

```solidity
File: /contracts/automata-attestation/utils/SHA1.sol

10: library SHA1 {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/SHA1.sol#L10)

```solidity
File: /contracts/automata-attestation/utils/SigVerifyLib.sol

15: contract SigVerifyLib is ISigVerifyLib {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/SigVerifyLib.sol#L15)

```solidity
File: /contracts/automata-attestation/utils/X509DateUtils.sol

7: library X509DateUtils {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/X509DateUtils.sol#L7)

```solidity
File: /contracts/bridge/Bridge.sol

16: contract Bridge is EssentialContract, IBridge {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L16)

```solidity
File: /contracts/bridge/IBridge.sol

8: interface IBridge {

160: interface IRecallableSender {

174: interface IMessageInvocable {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/IBridge.sol#L174)

```solidity
File: /contracts/common/AddressManager.sol

10: contract AddressManager is EssentialContract, IAddressManager {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/common/AddressManager.sol#L10)

```solidity
File: /contracts/common/EssentialContract.sol

10: abstract contract EssentialContract is UUPSUpgradeable, Ownable2StepUpgradeable, AddressResolver {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/common/EssentialContract.sol#L10)

```solidity
File: /contracts/common/IAddressManager.sol

7: interface IAddressManager {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/common/IAddressManager.sol#L7)

```solidity
File: /contracts/libs/Lib4844.sol

8: library Lib4844 {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/libs/Lib4844.sol#L8)

```solidity
File: /contracts/libs/LibAddress.sol

13: library LibAddress {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/libs/LibAddress.sol#L13)

```solidity
File: /contracts/libs/LibMath.sol

7: library LibMath {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/libs/LibMath.sol#L7)

```solidity
File: /contracts/libs/LibTrieProof.sol

15: library LibTrieProof {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/libs/LibTrieProof.sol#L15)

```solidity
File: /contracts/signal/ISignalService.sol

12: interface ISignalService {

12: interface ISignalService {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/ISignalService.sol#L12)

```solidity
File: /contracts/signal/LibSignals.sol

6: library LibSignals {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/LibSignals.sol#L6)

```solidity
File: /contracts/signal/SignalService.sol

14: contract SignalService is EssentialContract, ISignalService {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/SignalService.sol#L14)

```solidity
File: /contracts/team/TimelockTokenPool.sol

25: contract TimelockTokenPool is EssentialContract {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/TimelockTokenPool.sol#L25)

```solidity
File: /contracts/team/airdrop/ERC20Airdrop.sol

11: contract ERC20Airdrop is MerkleClaimable {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC20Airdrop.sol#L11)

```solidity
File: /contracts/team/airdrop/ERC20Airdrop2.sol

12: contract ERC20Airdrop2 is MerkleClaimable {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC20Airdrop2.sol#L12)

```solidity
File: /contracts/team/airdrop/ERC721Airdrop.sol

9: contract ERC721Airdrop is MerkleClaimable {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC721Airdrop.sol#L9)

```solidity
File: /contracts/team/airdrop/MerkleClaimable.sol

10: abstract contract MerkleClaimable is EssentialContract {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/MerkleClaimable.sol#L10)

```solidity
File: /contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol

5: library ExcessivelySafeCall {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L5)

```solidity
File: /contracts/thirdparty/optimism/Bytes.sol

6: library Bytes {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/Bytes.sol#L6)

```solidity
File: /contracts/thirdparty/optimism/rlp/RLPReader.sol

9: library RLPReader {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/rlp/RLPReader.sol#L9)

```solidity
File: /contracts/thirdparty/optimism/rlp/RLPWriter.sol

9: library RLPWriter {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/rlp/RLPWriter.sol#L9)

```solidity
File: /contracts/thirdparty/optimism/trie/MerkleTrie.sol

11: library MerkleTrie {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/trie/MerkleTrie.sol#L11)

```solidity
File: /contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol

9: library SecureMerkleTrie {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L9)

```solidity
File: /contracts/tokenvault/BaseNFTVault.sol

9: abstract contract BaseNFTVault is BaseVault {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BaseNFTVault.sol#L9)

```solidity
File: /contracts/tokenvault/BaseVault.sol

12: abstract contract BaseVault is

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BaseVault.sol#L12)

```solidity
File: /contracts/tokenvault/BridgedERC1155.sol

14: contract BridgedERC1155 is EssentialContract, IERC1155MetadataURIUpgradeable, ERC1155Upgradeable {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC1155.sol#L14)

```solidity
File: /contracts/tokenvault/BridgedERC20.sol

15: contract BridgedERC20 is

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC20.sol#L15)

```solidity
File: /contracts/tokenvault/BridgedERC20Base.sol

9: abstract contract BridgedERC20Base is EssentialContract, IBridgedERC20 {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC20Base.sol#L9)

```solidity
File: /contracts/tokenvault/BridgedERC721.sol

12: contract BridgedERC721 is EssentialContract, ERC721Upgradeable {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC721.sol#L12)

```solidity
File: /contracts/tokenvault/ERC1155Vault.sol

16: interface IERC1155NameAndSymbol {

29: contract ERC1155Vault is BaseNFTVault, ERC1155ReceiverUpgradeable {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC1155Vault.sol#L29)

```solidity
File: /contracts/tokenvault/ERC20Vault.sol

18: contract ERC20Vault is BaseVault {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC20Vault.sol#L18)

```solidity
File: /contracts/tokenvault/ERC721Vault.sol

16: contract ERC721Vault is BaseNFTVault, IERC721Receiver {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC721Vault.sol#L16)

```solidity
File: /contracts/tokenvault/IBridgedERC20.sol

10: interface IBridgedERC20 {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/IBridgedERC20.sol#L10)

```solidity
File: /contracts/tokenvault/LibBridgedToken.sol

8: library LibBridgedToken {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/LibBridgedToken.sol#L8)

```solidity
File: /contracts/tokenvault/adapters/USDCAdapter.sol

8: interface IUSDC {

28: contract USDCAdapter is BridgedERC20Base {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/adapters/USDCAdapter.sol#L28)

```solidity
File: /contracts/verifiers/GuardianVerifier.sol

10: contract GuardianVerifier is EssentialContract, IVerifier {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/GuardianVerifier.sol#L10)

```solidity
File: /contracts/verifiers/IVerifier.sol

9: interface IVerifier {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/IVerifier.sol#L9)

```solidity
File: /contracts/verifiers/SgxVerifier.sol

19: contract SgxVerifier is EssentialContract, IVerifier {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/SgxVerifier.sol#L19)

</details>

### <a name="GAS-3-1706545887"></a>[GAS-3] Trade-offs Between Modifiers and Internal Functions
In Solidity, both modifiers and internal functions can be used to modularize and reuse code, but they have different trade-offs.

Modifiers are primarily used to augment the behavior of functions, often for checks or validations.They can access parameters of the function they modify and are integrated into the functionâ€™s code at compile time.This makes them syntactically cleaner for repetitive precondition checks.However, modifiers can sometimes lead to less readable code, especially when the logic is complex or when multiple modifiers are used on a single function.

Internal functions, on the other hand, offer more flexibility.They can contain complex logic, return values, and be called from other functions.This makes them more suitable for reusable chunks of business logic.Since internal functions are separate entities, they can be more readable and easier to test in isolation compared to modifiers.

Using internal functions can result in slightly more gas consumption, as it involves an internal function call.However, this cost is usually minimal and can be a worthwhile trade- off for increased code clarity and maintainability.

In summary, while modifiers offer a concise way to include checks and simple logic across multiple functions, internal functions provide more flexibility and are better suited for complex and reusable code.The choice between the two should be based on the specific use case, considering factors like code complexity, readability, and gas efficiency.

*Instances (127)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/TaikoL1.sol

220:     function _authorizePause(address)

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/TaikoL1.sol#L220)

```solidity
File: /contracts/L1/TaikoToken.sol

83:     function _beforeTokenTransfer(

94:     function _afterTokenTransfer(

105:     function _mint(

115:     function _burn(

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/TaikoToken.sol#L115)

```solidity
File: /contracts/L1/gov/TaikoGovernor.sol

127:     function _execute(

140:     function _cancel(

153:     function _executor()

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/gov/TaikoGovernor.sol#L153)

```solidity
File: /contracts/L1/libs/LibDepositing.sol

29:     function depositEtherToL2(

67:     function processDeposits(

122:     function canDepositEthToL2(

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibDepositing.sol#L122)

```solidity
File: /contracts/L1/libs/LibProposing.sol

68:     function proposeBlock(

287:     function isBlobReusable(

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProposing.sol#L287)

```solidity
File: /contracts/L1/libs/LibProving.sol

91:     function proveBlock(

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProving.sol#L91)

```solidity
File: /contracts/L1/libs/LibUtils.sol

70:     function getTransitionId(

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibUtils.sol#L70)

```solidity
File: /contracts/L1/libs/LibVerifying.sol

85:     function verifyBlocks(

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibVerifying.sol#L85)

```solidity
File: /contracts/L1/provers/Guardians.sol

111:     function approve(uint256 _operationId, bytes32 _hash) internal returns (bool approved_) {

124:     function deleteApproval(bytes32 _hash) internal {

128:     function isApproved(uint256 _approvalBits) internal view returns (bool) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/provers/Guardians.sol#L128)

```solidity
File: /contracts/L2/CrossChainOwned.sol

60:     function __CrossChainOwned_init(

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/CrossChainOwned.sol#L60)

```solidity
File: /contracts/L2/Lib1559Math.sol

16:     function basefee(

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/Lib1559Math.sol#L16)

```solidity
File: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

126:     function _attestationTcbIsValid(TCBInfoStruct.TCBStatus status)

364:     function _verifyParsedQuote(V3Struct.ParsedV3QuoteStruct memory v3quote)

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/AutomataDcapV3Attestation.sol#L364)

```solidity
File: /contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

21:     function parseInput(

62:     function validateParsedInput(V3Struct.ParsedV3QuoteStruct memory v3Quote)

133:     function parseEnclaveReport(bytes memory rawEnclaveReport)

244:     function packQEReport(V3Struct.EnclaveReport memory enclaveReport)

267:     function parseCerificationChainBytes(

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L267)

```solidity
File: /contracts/automata-attestation/utils/Asn1Decode.sol

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
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/Asn1Decode.sol#L179)

```solidity
File: /contracts/automata-attestation/utils/BytesUtils.sol

16:     function keccak(

39:     function compare(bytes memory self, bytes memory other) internal pure returns (int256) {

56:     function compare(

116:     function equals(

138:     function equals(

160:     function equals(

178:     function equals(bytes memory self, bytes memory other) internal pure returns (bool) {

188:     function readUint8(bytes memory self, uint256 idx) internal pure returns (uint8 ret) {

198:     function readUint16(bytes memory self, uint256 idx) internal pure returns (uint16 ret) {

211:     function readUint32(bytes memory self, uint256 idx) internal pure returns (uint32 ret) {

224:     function readBytes32(bytes memory self, uint256 idx) internal pure returns (bytes32 ret) {

237:     function readBytes20(bytes memory self, uint256 idx) internal pure returns (bytes20 ret) {

255:     function readBytesN(

284:     function substring(

320:     function base32HexDecodeWord(

371:     function compareBytes(bytes memory a, bytes memory b) internal pure returns (bool) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/BytesUtils.sol#L371)

```solidity
File: /contracts/automata-attestation/utils/RsaVerify.sol

43:     function pkcs1Sha256(

191:     function pkcs1Sha256Raw(

212:     function pkcs1Sha1(

307:     function pkcs1Sha1Raw(

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/RsaVerify.sol#L307)

```solidity
File: /contracts/automata-attestation/utils/SHA1.sol

11:     function sha1(bytes memory data) internal pure returns (bytes20 ret) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/SHA1.sol#L11)

```solidity
File: /contracts/automata-attestation/utils/X509DateUtils.sol

8:     function toTimestamp(bytes memory x509Time) internal pure returns (uint256) {

34:     function toUnixTimestamp(

71:     function isLeapYear(uint16 year) internal pure returns (bool) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/X509DateUtils.sol#L71)

```solidity
File: /contracts/bridge/Bridge.sol

461:     function _authorizePause(address)

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L461)

```solidity
File: /contracts/common/AddressManager.sol

58:     function _authorizePause(address) internal pure override {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/common/AddressManager.sol#L58)

```solidity
File: /contracts/common/EssentialContract.sol

95:     function __Essential_init(

109:     function __Essential_init(address _owner) internal virtual {

114:     function _authorizeUpgrade(address) internal virtual override onlyOwner { }

116:     function _authorizePause(address) internal virtual onlyOwner { }

119:     function _storeReentryLock(uint8 _reentry) internal virtual {

130:     function _loadReentryLock() internal view virtual returns (uint8 reentry_) {

140:     function _inNonReentrant() internal view returns (bool) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/common/EssentialContract.sol#L140)

```solidity
File: /contracts/libs/Lib4844.sol

30:     function evaluatePoint(

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/libs/Lib4844.sol#L30)

```solidity
File: /contracts/libs/LibAddress.sol

22:     function sendEther(address _to, uint256 _amount, uint256 _gasLimit) internal {

42:     function sendEther(address _to, uint256 _amount) internal {

46:     function supportsInterface(

61:     function isValidSignature(

77:     function isSenderEOA() internal view returns (bool) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/libs/LibAddress.sol#L77)

```solidity
File: /contracts/libs/LibMath.sol

12:     function min(uint256 _a, uint256 _b) internal pure returns (uint256) {

20:     function max(uint256 _a, uint256 _b) internal pure returns (uint256) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/libs/LibMath.sol#L20)

```solidity
File: /contracts/libs/LibTrieProof.sol

34:     function verifyMerkleProof(

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/libs/LibTrieProof.sol#L34)

```solidity
File: /contracts/signal/SignalService.sol

206:     function _verifyHopProof(

231:     function _authorizePause(address) internal pure override {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/SignalService.sol#L231)

```solidity
File: /contracts/team/airdrop/MerkleClaimable.sol

56:     function __MerkleClaimable_init(

67:     function _verifyClaim(bytes memory data, bytes32[] calldata proof) internal ongoingClaim {

77:     function _verifyMerkleProof(

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/MerkleClaimable.sol#L77)

```solidity
File: /contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol

25:     function excessivelySafeCall(

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L25)

```solidity
File: /contracts/thirdparty/optimism/Bytes.sol

15:     function slice(

91:     function slice(bytes memory _bytes, uint256 _start) internal pure returns (bytes memory) {

102:     function toNibbles(bytes memory _bytes) internal pure returns (bytes memory) {

149:     function equal(bytes memory _bytes, bytes memory _other) internal pure returns (bool) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/Bytes.sol#L149)

```solidity
File: /contracts/thirdparty/optimism/rlp/RLPReader.sol

35:     function toRLPItem(bytes memory _in) internal pure returns (RLPItem memory out_) {

53:     function readList(RLPItem memory _in) internal pure returns (RLPItem[] memory out_) {

102:     function readList(bytes memory _in) internal pure returns (RLPItem[] memory out_) {

109:     function readBytes(RLPItem memory _in) internal pure returns (bytes memory out_) {

128:     function readBytes(bytes memory _in) internal pure returns (bytes memory out_) {

135:     function readRawBytes(RLPItem memory _in) internal pure returns (bytes memory out_) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/rlp/RLPReader.sol#L135)

```solidity
File: /contracts/thirdparty/optimism/rlp/RLPWriter.sol

13:     function writeBytes(bytes memory _in) internal pure returns (bytes memory out_) {

24:     function writeUint(uint256 _in) internal pure returns (bytes memory out_) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/rlp/RLPWriter.sol#L24)

```solidity
File: /contracts/thirdparty/optimism/trie/MerkleTrie.sol

50:     function verifyInclusionProof(

68:     function get(

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/trie/MerkleTrie.sol#L68)

```solidity
File: /contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol

19:     function verifyInclusionProof(

38:     function get(

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L38)

```solidity
File: /contracts/tokenvault/BaseVault.sol

47:     function checkProcessMessageContext()

58:     function checkRecallMessageContext()

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BaseVault.sol#L58)

```solidity
File: /contracts/tokenvault/BridgedERC1155.sol

125:     function _beforeTokenTransfer(

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC1155.sol#L125)

```solidity
File: /contracts/tokenvault/BridgedERC20.sol

129:     function _mintToken(address _account, uint256 _amount) internal override {

133:     function _burnToken(address _from, uint256 _amount) internal override {

139:     function _beforeTokenTransfer(

152:     function _afterTokenTransfer(

163:     function _mint(

173:     function _burn(

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC20.sol#L173)

```solidity
File: /contracts/tokenvault/BridgedERC20Base.sol

101:     function _isMigratingOut() internal view returns (bool) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC20Base.sol#L101)

```solidity
File: /contracts/tokenvault/BridgedERC721.sol

115:     function _beforeTokenTransfer(

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC721.sol#L115)

```solidity
File: /contracts/tokenvault/LibBridgedToken.sol

11:     function validateInputs(

28:     function buildName(

39:     function buildSymbol(string memory _symbol) internal pure returns (string memory) {

43:     function buildURI(

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/LibBridgedToken.sol#L43)

```solidity
File: /contracts/tokenvault/adapters/USDCAdapter.sol

43:     function _mintToken(address _account, uint256 _amount) internal override {

47:     function _burnToken(address _from, uint256 _amount) internal override {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/adapters/USDCAdapter.sol#L47)

</details>

### <a name="GAS-4-1705426850"></a>[GAS-4] Avoid emitting event on every iteration
Emitting events within a loop can cause significant gas consumption due to repeated I/O operations. Instead, accumulate changes in memory and emit a single event post-loop with aggregated data. This approach improves contract efficiency, reduces gas costs, and simplifies event tracking for event listeners.

*Instances (4)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/libs/LibVerifying.sol

127:             while (blockId < b.numBlocks && numBlocksVerified < _maxBlocksToVerify) {
                     slot = blockId % _config.blockRingBufferSize;
     
                     blk = _state.blocks[slot];
                     if (blk.blockId != blockId) revert L1_BLOCK_MISMATCH();
     
                     tid = LibUtils.getTransitionId(_state, blk, slot, blockHash);
                     // When `tid` is 0, it indicates that there is no proven
                     // transition with its parentHash equal to the blockHash of the
                     // most recently verified block.
                     if (tid == 0) break;
     
                     // A transition with the correct `parentHash` has been located.
                     TaikoData.TransitionState storage ts = _state.transitions[slot][tid];
     
                     // It's not possible to verify this block if either the
                     // transition is contested and awaiting higher-tier proof or if
                     // the transition is still within its cooldown period.
                     if (ts.contester != address(0)) {
                         break;
                     } else {
                         if (tierProvider == address(0)) {
                             tierProvider = _resolver.resolve("tier_provider", false);
                         }
                         if (
                             uint256(ITierProvider(tierProvider).getTier(ts.tier).cooldownWindow) * 60
                                 + uint256(ts.timestamp).max(_state.slotB.lastUnpausedAt) > block.timestamp
                         ) {
                             // If cooldownWindow is 0, the block can theoretically
                             // be proved and verified within the same L1 block.
                             break;
                         }
                     }
     
                     // Mark this block as verified
                     blk.verifiedTransitionId = tid;
     
                     // Update variables
                     blockHash = ts.blockHash;
                     stateRoot = ts.stateRoot;
     
                     // We consistently return the liveness bond and the validity
                     // bond to the actual prover of the transition utilized for
                     // block verification. If the actual prover happens to be the
                     // block's assigned prover, he will receive both deposits,
                     // ultimately earning the proving fee paid during block
                     // proposal. In contrast, if the actual prover is different from
                     // the block's assigned prover, the liveness bond serves as a
                     // reward to the actual prover, while the assigned prover
                     // forfeits his liveness bond due to failure to fulfill their
                     // commitment.
                     uint256 bondToReturn = uint256(ts.validityBond) + blk.livenessBond;
     
                     // Nevertheless, it's possible for the actual prover to be the
                     // same individual or entity as the block's assigned prover.
                     // Consequently, we have chosen to grant the actual prover only
                     // half of the liveness bond as a reward.
                     if (ts.prover != blk.assignedProver) {
                         bondToReturn -= blk.livenessBond >> 1;
                     }
     
                     IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));
                     tko.transfer(ts.prover, bondToReturn);
     
                     // Note: We exclusively address the bonds linked to the
                     // transition used for verification. While there may exist
                     // other transitions for this block, we disregard them entirely.
                     // The bonds for these other transitions are burned either when
                     // the transitions are generated or proven. In such cases, both
                     // the provers and contesters of those transitions forfeit their bonds.
     
                     emit BlockVerified({
                         blockId: blockId,
                         assignedProver: blk.assignedProver,
                         prover: ts.prover,
                         blockHash: blockHash,
                         stateRoot: stateRoot,
                         tier: ts.tier,
                         contestations: ts.contestations
                     });
     
                     ++blockId;
                     ++numBlocksVerified;
                 }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibVerifying.sol#L127-L210)

```solidity
File: /contracts/bridge/Bridge.sol

90:         for (uint256 i; i < _msgHashes.length; ++i) {
                bytes32 msgHash = _msgHashes[i];
                proofReceipt[msgHash].receivedAt = _timestamp;
                emit MessageSuspended(msgHash, _suspend);
            }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L90-L94)

```solidity
File: /contracts/verifiers/SgxVerifier.sol

104:         for (uint256 i; i < _ids.length; ++i) {
                 uint256 idx = _ids[i];
     
                 if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();
     
                 emit InstanceDeleted(idx, instances[idx].addr);
     
                 delete instances[idx];
             }

210:         for (uint256 i; i < _instances.length; ++i) {
                 if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();
     
                 addressRegistered[_instances[i]] = true;
     
                 if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();
     
                 instances[nextInstanceId] = Instance(_instances[i], validSince);
                 ids[i] = nextInstanceId;
     
                 emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);
     
                 nextInstanceId++;
             }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/SgxVerifier.sol#L210-L223)

</details>

### <a name="GAS-5-1693311630"></a>[GAS-5] Use assembly to check for `address(0)`
*Saves 6 gas per instance*

*Instances (53)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/hooks/AssignmentHook.sol

109:         if (assignment.feeToken == address(0)) {

120:         if (input.tip != 0 && block.coinbase != address(0)) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/hooks/AssignmentHook.sol#L120)

```solidity
File: /contracts/L1/libs/LibDepositing.sol

44:         address recipient_ = _recipient == address(0) ? msg.sender : _recipient;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibDepositing.sol#L44)

```solidity
File: /contracts/L1/libs/LibProposing.sol

81:         if (params.assignedProver == address(0)) {

85:         if (params.coinbase == address(0)) {

310:             if (proposerOne != address(0) && msg.sender != proposerOne) {

316:         return proposer == address(0) || msg.sender == proposer;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProposing.sol#L316)

```solidity
File: /contracts/L1/libs/LibProving.sol

163:             if (verifier != address(0)) {

224:                 assert(ts.validityBond == 0 && ts.contestBond == 0 && ts.contester == address(0));

239:                 if (ts.contester != address(0)) revert L1_ALREADY_CONTESTED();

363:         if (_ts.contester != address(0)) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProving.sol#L363)

```solidity
File: /contracts/L1/libs/LibVerifying.sol

145:                 if (ts.contester != address(0)) {

148:                     if (tierProvider == address(0)) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibVerifying.sol#L148)

```solidity
File: /contracts/L1/provers/Guardians.sol

82:             if (guardian == address(0)) revert INVALID_GUARDIAN();

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/provers/Guardians.sol#L82)

```solidity
File: /contracts/L2/TaikoL2.sol

172:         if (_to == address(0)) revert L2_INVALID_PARAM();

173:         if (_token == address(0)) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/TaikoL2.sol#L173)

```solidity
File: /contracts/bridge/Bridge.sol

124:         if (_message.srcOwner == address(0) || _message.destOwner == address(0)) {

124:         if (_message.srcOwner == address(0) || _message.destOwner == address(0)) {

270:                 _message.to == address(0) || _message.to == address(this)

291:                 _message.refundTo == address(0) ? _message.destOwner : _message.refundTo;

398:         enabled_ = destBridge_ != address(0);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L398)

```solidity
File: /contracts/common/EssentialContract.sol

105:         if (_addressManager == address(0)) revert ZERO_ADDR_MANAGER();

110:         _transferOwnership(_owner == address(0) ? msg.sender : _owner);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/common/EssentialContract.sol#L110)

```solidity
File: /contracts/libs/LibAddress.sol

24:         if (_to == address(0)) revert ETH_TRANSFER_FAILED();

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/libs/LibAddress.sol#L24)

```solidity
File: /contracts/signal/SignalService.sol

36:         if (_app == address(0)) revert SS_INVALID_SENDER();

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/SignalService.sol#L36)

```solidity
File: /contracts/team/TimelockTokenPool.sol

121:         if (_taikoToken == address(0)) revert INVALID_PARAM();

124:         if (_costToken == address(0)) revert INVALID_PARAM();

127:         if (_sharedVault == address(0)) revert INVALID_PARAM();

136:         if (_recipient == address(0)) revert INVALID_PARAM();

169:         if (_to == address(0)) revert INVALID_PARAM();

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/TimelockTokenPool.sol#L169)

```solidity
File: /contracts/tokenvault/BaseNFTVault.sol

149:         if (_op.token == address(0)) revert VAULT_INVALID_TOKEN();

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BaseNFTVault.sol#L149)

```solidity
File: /contracts/tokenvault/BridgedERC20Base.sol

102:         return migratingAddress != address(0) && !migratingInbound;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC20Base.sol#L102)

```solidity
File: /contracts/tokenvault/ERC1155Vault.sol

64:             destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,

108:         if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

249:             if (bridgedToCanonical[_op.token].addr != address(0)) {

293:         if (btoken_ == address(0)) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC1155Vault.sol#L293)

```solidity
File: /contracts/tokenvault/ERC20Vault.sol

158:         if (_btokenNew == address(0) || bridgedToCanonical[_btokenNew].addr != address(0)) {

158:         if (_btokenNew == address(0) || bridgedToCanonical[_btokenNew].addr != address(0)) {

170:         if (btokenOld_ != address(0)) {

215:         if (_op.token == address(0)) revert VAULT_INVALID_TOKEN();

227:             destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,

267:         if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

358:         if (bridgedToCanonical[_token].addr != address(0)) {

397:         if (btoken == address(0)) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC20Vault.sol#L397)

```solidity
File: /contracts/tokenvault/ERC721Vault.sol

50:             destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,

91:         if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

195:             if (bridgedToCanonical[_op.token].addr != address(0)) {

230:         if (btoken_ == address(0)) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC721Vault.sol#L230)

```solidity
File: /contracts/tokenvault/LibBridgedToken.sol

21:             _srcToken == address(0) || _srcChainId == 0 || _srcChainId == block.chainid

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/LibBridgedToken.sol#L21)

```solidity
File: /contracts/verifiers/SgxVerifier.sol

107:             if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();

124:         if (automataDcapAttestation == address(0)) {

215:             if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();

234:         if (instance == address(0)) return false;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/SgxVerifier.sol#L234)

</details>

### <a name="GAS-6-1693311540"></a>[GAS-6] Multiple accesses of a mapping/array should use a local variable cache
The instances below point to the second+ access of a value inside a mapping/array, within a function. Caching a mapping's value in a local `storage` or `calldata` variable when the value is accessed [multiple times](https://gist.github.com/IllIllI000/ec23a57daa30a8f8ca8b9681c8ccefb0), saves **~42 gas per access** due to not having to recalculate the key's keccak256 hash (Gkeccak256 - **30 gas**) and that calculation's associated stack operations. Caching an array's struct avoids recalculating the array offsets into memory/calldata

*Instances (44)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/hooks/AssignmentHook.sol

173:             if (_tierFees[i].tier == _tierId) return _tierFees[i].fee;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/hooks/AssignmentHook.sol#L173-L173)

```solidity
File: /contracts/L1/libs/LibDepositing.sol

93:                 uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount;

93:                 uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount;

101:                     deposits_[i].amount -= _fee;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibDepositing.sol#L101-L101)

```solidity
File: /contracts/L1/provers/Guardians.sol

88:             guardianIds[guardian] = guardians.length;

116:             _approvals[version][_hash] |= 1 << (id - 1);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/provers/Guardians.sol#L116-L116)

```solidity
File: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

84:             _serialNumIsRevoked[index][serialNumBatch[i]] = true;

84:             _serialNumIsRevoked[index][serialNumBatch[i]] = true;

99:             delete _serialNumIsRevoked[index][serialNumBatch[i]];

99:             delete _serialNumIsRevoked[index][serialNumBatch[i]];

268:                     certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.ROOT)][certs[i]

270:                 } else if (certs[i].isPck) {

271:                     certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.PCK)][certs[i]

280:                 block.timestamp > certs[i].notBefore && block.timestamp < certs[i].notAfter;

280:                 block.timestamp > certs[i].notBefore && block.timestamp < certs[i].notAfter;

286:                 certs[i].tbsCertificate, certs[i].signature, issuer.pubKey

286:                 certs[i].tbsCertificate, certs[i].signature, issuer.pubKey

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/AutomataDcapV3Attestation.sol#L286-L286)

```solidity
File: /contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

282:             quoteCerts[i] = Base64.decode(string(quoteCerts[i]));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L282-L282)

```solidity
File: /contracts/bridge/Bridge.sol

110:         addressBanned[_addr] = _ban;

184:             proofReceipt[msgHash].receivedAt = receivedAt;

190:             delete proofReceipt[msgHash];

191:             messageStatus[msgHash] = Status.RECALLED;

243:                 proofReceipt[msgHash] = ProofReceipt({

250:         if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) {

264:             delete proofReceipt[msgHash];

518:         messageStatus[_msgHash] = _status;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L518-L518)

```solidity
File: /contracts/common/AddressManager.sol

49:         __addresses[_chainId][_name] = _newAddress;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/common/AddressManager.sol#L49-L49)

```solidity
File: /contracts/signal/SignalService.sol

58:         isAuthorized[_addr] = _authorize;

248:             topBlockId[_chainId][_kind] = _blockId;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/SignalService.sol#L248-L248)

```solidity
File: /contracts/team/TimelockTokenPool.sol

137:         if (recipients[_recipient].grant.amount != 0) revert ALREADY_GRANTED();

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/TimelockTokenPool.sol#L137-L137)

```solidity
File: /contracts/team/airdrop/MerkleClaimable.sol

73:         isClaimed[hash] = true;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/MerkleClaimable.sol#L73-L73)

```solidity
File: /contracts/thirdparty/optimism/trie/MerkleTrie.sol

209:             proof_[i] = TrieNode({ encoded: _proof[i], decoded: RLPReader.readList(_proof[i]) });

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/trie/MerkleTrie.sol#L209-L209)

```solidity
File: /contracts/tokenvault/ERC20Vault.sol

158:         if (_btokenNew == address(0) || bridgedToCanonical[_btokenNew].addr != address(0)) {

180:             delete bridgedToCanonical[_btokenNew];

359:             ctoken_ = bridgedToCanonical[_token];

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC20Vault.sol#L359-L359)

```solidity
File: /contracts/tokenvault/ERC721Vault.sol

171:                 IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC721Vault.sol#L171-L171)

```solidity
File: /contracts/verifiers/SgxVerifier.sol

107:             if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();

109:             emit InstanceDeleted(idx, instances[idx].addr);

213:             addressRegistered[_instances[i]] = true;

215:             if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();

217:             instances[nextInstanceId] = Instance(_instances[i], validSince);

220:             emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);

236:         return instances[id].validSince <= block.timestamp

237:             && block.timestamp <= instances[id].validSince + INSTANCE_EXPIRY;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/SgxVerifier.sol#L237-L237)

</details>

### <a name="GAS-7-1706548063"></a>[GAS-7] Use assembly scratch space to build calldata for external calls
Using Solidity's assembly scratch space for constructing calldata in external calls with one or two arguments can be a gas-efficient approach. This method leverages the designated memory area (the first 64 bytes of memory) for temporary data storage during assembly operations. By directly writing arguments into this scratch space, it eliminates the need for additional memory allocation typically required for calldata preparation. This technique can lead to notable gas savings, especially in high-frequency or gas-sensitive operations. However, it requires careful implementation to avoid data corruption and should be used with a thorough understanding of low-level EVM operations and memory handling. Proper testing and validation are crucial when employing such optimizations.

*Instances (53)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/TaikoToken.sol

62:         return super.transfer(_to, _amount);

112:         super._mint(_to, _amount);

122:         super._burn(_from, _amount);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/TaikoToken.sol#L122-L122)

```solidity
File: /contracts/L1/gov/TaikoGovernor.sol

95:         return super.supportsInterface(_interfaceId);

105:         return super.state(_proposalId);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/gov/TaikoGovernor.sol#L105-L105)

```solidity
File: /contracts/L1/libs/LibDepositing.sol

41:         _resolver.resolve("bridge", false).sendEther(msg.value);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibDepositing.sol#L41-L41)

```solidity
File: /contracts/L1/libs/LibProposing.sol

207:         meta_.minTier = ITierProvider(_resolver.resolve("tier_provider", false)).getMinTier(
                 uint256(meta_.difficulty)
             );

207:         meta_.minTier = ITierProvider(_resolver.resolve("tier_provider", false)).getMinTier(

237:             IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));

238:             uint256 tkoBalance = tko.balanceOf(address(this));

268:             if (tko.balanceOf(address(this)) != tkoBalance + _config.livenessBond) {

309:             address proposerOne = _resolver.resolve("proposer_one", true);

315:         address proposer = _resolver.resolve("proposer", true);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProposing.sol#L315-L315)

```solidity
File: /contracts/L1/libs/LibProving.sol

141:             ITierProvider(_resolver.resolve("tier_provider", false)).getTier(_proof.tier);

141:             ITierProvider(_resolver.resolve("tier_provider", false)).getTier(_proof.tier);

161:             address verifier = _resolver.resolve(tier.verifierName, true);

187:         IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));

196:                 tko.transfer(blk.assignedProver, blk.livenessBond);

367:                 _tko.transfer(_ts.prover, _ts.validityBond + reward);

371:                 _tko.transfer(_ts.contester, _ts.contestBond + reward);

382:                 _tko.transfer(msg.sender, reward - _tier.validityBond);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProving.sol#L382-L382)

```solidity
File: /contracts/L1/libs/LibVerifying.sol

149:                         tierProvider = _resolver.resolve("tier_provider", false);

152:                         uint256(ITierProvider(tierProvider).getTier(ts.tier).cooldownWindow) * 60

188:                 IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));

189:                 tko.transfer(ts.prover, bondToReturn);

232:         ISignalService signalService = ISignalService(_resolver.resolve("signal_service", false));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibVerifying.sol#L232-L232)

```solidity
File: /contracts/L1/provers/GuardianProver.sol

51:             ITaikoL1(resolve("taiko", false)).proveBlock(_meta.id, abi.encode(_meta, _tran, _proof));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/provers/GuardianProver.sol#L51-L51)

```solidity
File: /contracts/L2/TaikoL2.sol

176:             IERC20(_token).safeTransfer(_to, IERC20(_token).balanceOf(address(this)));

176:             IERC20(_token).safeTransfer(_to, IERC20(_token).balanceOf(address(this)));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/TaikoL2.sol#L176-L176)

```solidity
File: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

424:                 (certDecodedSuccessfully, parsedQuoteCerts[i]) = pemCertLib.decodeCert(
                         authDataV3.certification.decodedCertDataArray[i], isPckCert
                     );

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/AutomataDcapV3Attestation.sol#L424-L426)

```solidity
File: /contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

278:             pemCertLib.splitCertificateChain(certBytes, 3);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L278-L278)

```solidity
File: /contracts/bridge/Bridge.sol

150:         ISignalService(resolve("signal_service", false)).sendSignal(msgHash_);

174:             if (!ISignalService(signalService).isSignalSent(address(this), msgHash)) {

342:         return ISignalService(resolve("signal_service", false)).isSignalSent({
                 _app: address(this),
                 _signal: hashMessage(_message)
             });

522:             ISignalService(resolve("signal_service", false)).sendSignal(
                     signalForFailedMessage(_msgHash)
                 );

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L522-L524)

```solidity
File: /contracts/libs/LibAddress.sol

56:         try IERC165(_addr).supportsInterface(_interfaceId) returns (bool _result) {

71:             return IERC1271(_addr).isValidSignature(_hash, _sig) == _EIP1271_MAGICVALUE;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/libs/LibAddress.sol#L71-L71)

```solidity
File: /contracts/tokenvault/BridgedERC20.sol

170:         super._mint(_to, _amount);

180:         super._burn(_from, _amount);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC20.sol#L180-L180)

```solidity
File: /contracts/tokenvault/BridgedERC20Base.sol

82:             IBridgedERC20(migratingAddress).mint(_account, _amount);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC20Base.sol#L82-L82)

```solidity
File: /contracts/tokenvault/ERC1155Vault.sol

200:             || BaseVault.supportsInterface(interfaceId);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC1155Vault.sol#L200-L200)

```solidity
File: /contracts/tokenvault/ERC20Vault.sol

184:             IBridgedERC20(btokenOld_).changeMigrationStatus(_btokenNew, false);

185:             IBridgedERC20(_btokenNew).changeMigrationStatus(btokenOld_, true);

330:             IERC20(token_).safeTransfer(_to, _amount);

333:             IBridgedERC20(token_).mint(_to, _amount);

360:             IBridgedERC20(_token).burn(msg.sender, _amount);

378:             uint256 _balance = t.balanceOf(address(this));

380:             balanceChange_ = t.balanceOf(address(this)) - _balance;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC20Vault.sol#L380-L380)

```solidity
File: /contracts/tokenvault/ERC721Vault.sol

176:                 BridgedERC721(token_).mint(_to, _tokenIds[i]);

198:                     BridgedERC721(_op.token).burn(_user, _op.tokenIds[i]);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC721Vault.sol#L198-L198)

```solidity
File: /contracts/tokenvault/adapters/USDCAdapter.sol

44:         usdc.mint(_account, _amount);

49:         usdc.burn(_amount);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/adapters/USDCAdapter.sol#L49-L49)

```solidity
File: /contracts/verifiers/SgxVerifier.sol

128:         (bool verified,) = IAttestation(automataDcapAttestation).verifyParsedQuote(_attestation);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/SgxVerifier.sol#L128-L128)

</details>

### <a name="GAS-8-1693311599"></a>[GAS-8] Use assembly to calculate hashes to save gas
Using assembly to calculate hashes can save *** 80 gas *** per instance

*Instances (28)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/hooks/AssignmentHook.sol

146:         return keccak256(

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/hooks/AssignmentHook.sol#L146)

```solidity
File: /contracts/L1/libs/LibProposing.sol

126:                 depositsHash: keccak256(abi.encode(deposits_)),

189:             meta_.blobHash = keccak256(_txList);

204:         meta_.difficulty = keccak256(abi.encodePacked(block.prevrandao, b.numBlocks, block.number));

213:             metaHash: keccak256(abi.encode(meta_)),

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProposing.sol#L213)

```solidity
File: /contracts/L1/libs/LibProving.sol

20:     bytes32 public constant RETURN_LIVENESS_BOND = keccak256("RETURN_LIVENESS_BOND");

121:         if (blk.blockId != _meta.id || blk.metaHash != keccak256(abi.encode(_meta))) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProving.sol#L121)

```solidity
File: /contracts/L1/provers/GuardianProver.sol

46:         bytes32 hash = keccak256(abi.encode(_meta, _tran));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/provers/GuardianProver.sol#L46)

```solidity
File: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

292:             bytes32 issuerPubKeyHash = keccak256(issuer.pubKey);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/AutomataDcapV3Attestation.sol#L292)

```solidity
File: /contracts/automata-attestation/utils/BytesUtils.sol

372:         return keccak256(a) == keccak256(b);

372:         return keccak256(a) == keccak256(b);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/BytesUtils.sol#L372)

```solidity
File: /contracts/bridge/Bridge.sol

450:         return keccak256(abi.encode("TAIKO_MESSAGE", _message));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L450)

```solidity
File: /contracts/signal/LibSignals.sol

8:     bytes32 public constant STATE_ROOT = keccak256("STATE_ROOT");

11:     bytes32 public constant SIGNAL_ROOT = keccak256("SIGNAL_ROOT");

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/LibSignals.sol#L11)

```solidity
File: /contracts/signal/SignalService.sol

186:         return keccak256(abi.encode(_chainId, _kind, _blockId));

203:         return keccak256(abi.encodePacked("SIGNAL", _chainId, _app, _signal));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/SignalService.sol#L203)

```solidity
File: /contracts/team/TimelockTokenPool.sol

170:         bytes32 hash = keccak256(abi.encodePacked("Withdraw unlocked Taiko token to: ", _to));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/TimelockTokenPool.sol#L170)

```solidity
File: /contracts/team/airdrop/MerkleClaimable.sol

68:         bytes32 hash = keccak256(abi.encode("CLAIM_TAIKO_AIRDROP", data));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/MerkleClaimable.sol#L68)

```solidity
File: /contracts/thirdparty/optimism/Bytes.sol

150:         return keccak256(_bytes) == keccak256(_other);

150:         return keccak256(_bytes) == keccak256(_other);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/Bytes.sol#L150)

```solidity
File: /contracts/thirdparty/optimism/trie/MerkleTrie.sol

94:                     Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),

100:                     Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/trie/MerkleTrie.sol#L100)

```solidity
File: /contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol

55:         hash_ = abi.encodePacked(keccak256(_key));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L55)

```solidity
File: /contracts/tokenvault/ERC20Vault.sol

176:                     || keccak256(bytes(ctoken.symbol)) != keccak256(bytes(_ctoken.symbol))

176:                     || keccak256(bytes(ctoken.symbol)) != keccak256(bytes(_ctoken.symbol))

177:                     || keccak256(bytes(ctoken.name)) != keccak256(bytes(_ctoken.name))

177:                     || keccak256(bytes(ctoken.name)) != keccak256(bytes(_ctoken.name))

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC20Vault.sol#L177)

```solidity
File: /contracts/verifiers/SgxVerifier.sol

182:         return keccak256(

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/SgxVerifier.sol#L182)

</details>

### <a name="GAS-9-1693311663"></a>[GAS-9] Use assembly in place of `abi.decode` to extract `calldata` values more efficiently
Instead of using abi.decode, we can use assembly to decode our desired calldata values directly. This will allow us to avoid decoding calldata values that we will not use.
For more details on how to implement this, check the following [report](https://code4rena.com/reports/2023-05-juicebox#g-04-use-assembly-in-place-of-abidecode-to-extract-calldata-values-more-efficiently)

*Instances (6)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/tokenvault/ERC1155Vault.sol

141:         (CanonicalNFT memory ctoken,,, uint256[] memory tokenIds, uint256[] memory amounts) =
                 abi.decode(data, (CanonicalNFT, address, address, uint256[], uint256[]));

141:         (CanonicalNFT memory ctoken,,, uint256[] memory tokenIds, uint256[] memory amounts) =
                 abi.decode(data, (CanonicalNFT, address, address, uint256[], uint256[]));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC1155Vault.sol#L141-L142)

```solidity
File: /contracts/tokenvault/ERC20Vault.sol

299:         (CanonicalERC20 memory ctoken,,, uint256 amount) =
                 abi.decode(data, (CanonicalERC20, address, address, uint256));

299:         (CanonicalERC20 memory ctoken,,, uint256 amount) =
                 abi.decode(data, (CanonicalERC20, address, address, uint256));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC20Vault.sol#L299-L300)

```solidity
File: /contracts/tokenvault/ERC721Vault.sol

124:         (CanonicalNFT memory ctoken,,, uint256[] memory tokenIds) =
                 abi.decode(data, (CanonicalNFT, address, address, uint256[]));

124:         (CanonicalNFT memory ctoken,,, uint256[] memory tokenIds) =
                 abi.decode(data, (CanonicalNFT, address, address, uint256[]));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC721Vault.sol#L124-L125)

</details>

### <a name="GAS-10-1693311695"></a>[GAS-10] Optimize Address Storage Value Management with `assembly`
As the following instances does not pack address variables with others, then using Assembly will save gas when storing address value

*Instances (7)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

57:         owner = msg.sender;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/AutomataDcapV3Attestation.sol#L57-L57)

```solidity
File: /contracts/automata-attestation/utils/SigVerifyLib.sol

21:         ES256VERIFIER = es256Verifier;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/SigVerifyLib.sol#L21-L21)

```solidity
File: /contracts/team/TimelockTokenPool.sol

122:         taikoToken = _taikoToken;

125:         costToken = _costToken;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/TimelockTokenPool.sol#L125-L125)

```solidity
File: /contracts/team/airdrop/ERC20Airdrop.sol

41:         token = _token;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC20Airdrop.sol#L41-L41)

```solidity
File: /contracts/team/airdrop/ERC20Airdrop2.sol

69:         token = _token;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC20Airdrop2.sol#L69-L69)

```solidity
File: /contracts/team/airdrop/ERC721Airdrop.sol

39:         token = _token;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC721Airdrop.sol#L39-L39)

</details>

### <a name="GAS-11-1693311732"></a>[GAS-11] Use assembly to emit events
We can use assembly to emit events efficiently by utilizing `scratch space` and the `free memory pointer`. This will allow us to potentially avoid memory expansion costs. Note: In order to do this optimization safely, we will need to cache and restore the free memory pointer.

*Instances (55)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/hooks/AssignmentHook.sol

129:         emit BlockAssigned(_blk.assignedProver, _meta, assignment);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/hooks/AssignmentHook.sol#L129)

```solidity
File: /contracts/L1/libs/LibDepositing.sol

50:         emit EthDeposited(

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibDepositing.sol#L50)

```solidity
File: /contracts/L1/libs/LibProposing.sol

166:                     emit BlobCached(meta_.blobHash);

273:         emit BlockProposed({

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProposing.sol#L273)

```solidity
File: /contracts/L1/libs/LibProving.sol

80:         emit ProvingPaused(_pause);

209:             emit TransitionProved({

230:                 emit TransitionProved({

254:                 emit TransitionContested({

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProving.sol#L254)

```solidity
File: /contracts/L1/libs/LibVerifying.sol

73:         emit BlockVerified({

198:                 emit BlockVerified({

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibVerifying.sol#L198)

```solidity
File: /contracts/L1/provers/GuardianProver.sol

54:         emit GuardianApproval(msg.sender, _meta.id, _tran.blockHash, approved_);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/provers/GuardianProver.sol#L54)

```solidity
File: /contracts/L1/provers/Guardians.sol

95:         emit GuardiansUpdated(version, _newGuardians);

121:         emit Approved(_operationId, _approval, approved_);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/provers/Guardians.sol#L121)

```solidity
File: /contracts/L2/CrossChainOwned.sol

53:         emit TransactionExecuted(nextTxId++, bytes4(txdata));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/CrossChainOwned.sol#L53)

```solidity
File: /contracts/L2/TaikoL2.sol

157:         emit Anchored(blockhash(parentId), gasExcess);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/TaikoL2.sol#L157)

```solidity
File: /contracts/L2/TaikoL2EIP1559Configurable.sol

39:         emit ConfigAndExcessChanged(_newConfig, _newGasExcess);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/TaikoL2EIP1559Configurable.sol#L39)

```solidity
File: /contracts/bridge/Bridge.sol

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
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L519)

```solidity
File: /contracts/common/AddressManager.sol

50:         emit AddressSet(_chainId, _name, _newAddress, oldAddress);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/common/AddressManager.sol#L50)

```solidity
File: /contracts/common/EssentialContract.sol

71:         emit Paused(msg.sender);

80:         emit Unpaused(msg.sender);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/common/EssentialContract.sol#L80)

```solidity
File: /contracts/signal/SignalService.sol

59:         emit Authorized(_addr, _authorize);

250:         emit ChainDataSynced(_chainId, _blockId, _kind, _chainData, signal_);

268:         emit SignalSent(_app, _signal, slot_, _value);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/SignalService.sol#L268)

```solidity
File: /contracts/team/TimelockTokenPool.sol

143:         emit Granted(_recipient, _grant);

157:         emit Voided(_recipient, amountVoided);

222:         emit Withdrawn(_recipient, _to, amountToWithdraw, costToWithdraw);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/TimelockTokenPool.sol#L222)

```solidity
File: /contracts/team/airdrop/ERC20Airdrop2.sol

93:         emit Withdrawn(user, amount);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC20Airdrop2.sol#L93)

```solidity
File: /contracts/team/airdrop/MerkleClaimable.sol

74:         emit Claimed(hash);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/MerkleClaimable.sol#L74)

```solidity
File: /contracts/tokenvault/BridgedERC20Base.sol

51:         emit MigrationStatusChanged(_migratingAddress, _migratingInbound);

63:             emit MigratedTo(migratingAddress, _account, _amount);

80:             emit MigratedTo(migratingAddress, _account, _amount);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC20Base.sol#L80)

```solidity
File: /contracts/tokenvault/ERC1155Vault.sol

80:         emit TokenSent({

114:         emit TokenReceived({

149:         emit TokenReleased({

314:         emit BridgedTokenDeployed({

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC1155Vault.sol#L314)

```solidity
File: /contracts/tokenvault/ERC20Vault.sol

191:         emit BridgedTokenChanged({

241:         emit TokenSent({

273:         emit TokenReceived({

306:         emit TokenReleased({

425:         emit BridgedTokenDeployed({

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC20Vault.sol#L425)

```solidity
File: /contracts/tokenvault/ERC721Vault.sol

64:         emit TokenSent({

97:         emit TokenReceived({

131:         emit TokenReleased({

250:         emit BridgedTokenDeployed({

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC721Vault.sol#L250)

```solidity
File: /contracts/verifiers/SgxVerifier.sol

109:             emit InstanceDeleted(idx, instances[idx].addr);

220:             emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);

230:         emit InstanceAdded(id, newInstance, oldInstance, block.timestamp);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/SgxVerifier.sol#L230)

</details>

### <a name="GAS-12-1693311770"></a>[GAS-12] Avoid contract existence checks by using low level calls
Prior to 0.8.10 the compiler inserted extra code, including `EXTCODESIZE` (100 gas), to check for contract existence for external function calls. In more recent solidity versions, the compiler will not insert these checks if the external call has a return value. Similar behavior can be achieved in earlier versions by using low-level calls, since low level calls never check for contract existence

*Instances (1)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/tokenvault/BridgedERC20Base.sol

//@audit mint() 
82:             IBridgedERC20(migratingAddress).mint(_account, _amount);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC20Base.sol#L82-L82)

</details>

### <a name="GAS-13-1693311856"></a>[GAS-13] Using bools for storage incurs overhead
Use uint256(1) and uint256(2) for true/false to avoid a Gwarmaccess (100 gas), and to avoid Gsset (20000 gas) when changing from 'false' to 'true', after having been 'true' in the past. See [source](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/58f635312aa21f947cae5f8578638a85aa2519f5/contracts/security/ReentrancyGuard.sol#L23-L27).

*Instances (17)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/TaikoData.sol

//@audit change `blobAllowedForDA` to `uint256`
//@audit change `blobReuseEnabled` to `uint256`
10:     struct Config {
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

//@audit change `cacheBlobForReuse` to `uint256`
78:     struct BlockParams {
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

//@audit change `blobUsed` to `uint256`
94:     struct BlockMetadata {
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

//@audit change `provingPaused` to `uint256`
168:     struct SlotB {
             uint64 numBlocks;
             uint64 lastVerifiedBlockId;
             bool provingPaused;
             uint8 __reserved1;
             uint16 __reserved2;
             uint32 __reserved3;
             uint64 lastUnpausedAt;
         }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/TaikoData.sol#L168-L176)

```solidity
File: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

//@audit avoid using `bool` type for _checkLocalEnclaveReport
38:     bool private _checkLocalEnclaveReport;

//@audit avoid using `bool` type for mapping values
39:     mapping(bytes32 enclave => bool trusted) private _trustedUserMrEnclave;

//@audit avoid using `bool` type for mapping values
40:     mapping(bytes32 signer => bool trusted) private _trustedUserMrSigner;

//@audit avoid using `bool` type for mapping values
47:     mapping(uint256 idx => mapping(bytes serialNum => bool revoked)) private _serialNumIsRevoked;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/AutomataDcapV3Attestation.sol#L47)

```solidity
File: /contracts/automata-attestation/lib/PEMCertChainLib.sol

//@audit change `fmspcFound` to `uint256`
//@audit change `pceidFound` to `uint256`
//@audit change `tcbFound` to `uint256`
34:     struct PCKTCBFlags {
            bool fmspcFound;
            bool pceidFound;
            bool tcbFound;
        }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/PEMCertChainLib.sol#L34-L38)

```solidity
File: /contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol

//@audit change `isPck` to `uint256`
7:     struct ECSha256Certificate {
           uint256 notBefore;
           uint256 notAfter;
           bytes serialNumber;
           bytes tbsCertificate;
           bytes pubKey;
           bytes signature;
           bool isPck;
           PCKCertificateField pck;
       }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L7-L16)

```solidity
File: /contracts/bridge/Bridge.sol

//@audit avoid using `bool` type for mapping values
42:     mapping(address addr => bool banned) public addressBanned;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L42)

```solidity
File: /contracts/signal/SignalService.sol

//@audit avoid using `bool` type for mapping values
21:     mapping(address addr => bool authorized) public isAuthorized;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/SignalService.sol#L21)

```solidity
File: /contracts/team/airdrop/MerkleClaimable.sol

//@audit avoid using `bool` type for mapping values
12:     mapping(bytes32 hash => bool claimed) public isClaimed;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/MerkleClaimable.sol#L12)

```solidity
File: /contracts/tokenvault/BridgedERC20Base.sol

//@audit avoid using `bool` type for migratingInbound
14:     bool public migratingInbound;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC20Base.sol#L14)

```solidity
File: /contracts/tokenvault/ERC20Vault.sol

//@audit avoid using `bool` type for mapping values
52:     mapping(address btoken => bool blacklisted) public btokenBlacklist;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC20Vault.sol#L52)

```solidity
File: /contracts/verifiers/IVerifier.sol

//@audit change `isContesting` to `uint256`
//@audit change `blobUsed` to `uint256`
10:     struct Context {
            bytes32 metaHash;
            bytes32 blobHash;
            address prover;
            uint64 blockId;
            bool isContesting;
            bool blobUsed;
            address msgSender;
        }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/IVerifier.sol#L10-L18)

```solidity
File: /contracts/verifiers/SgxVerifier.sol

//@audit avoid using `bool` type for mapping values
55:     mapping(address instanceAddress => bool alreadyAttested) public addressRegistered;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/SgxVerifier.sol#L55)

</details>

### <a name="GAS-14-1693311879"></a>[GAS-14] Use byte32 in place of string
For strings of 32 char strings and below you can use bytes32 instead as it's more gas efficient

*Instances (2)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/automata-attestation/lib/PEMCertChainLib.sol

241:         string[] memory split = LibString.split(contentSlice, string(delimiter));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/PEMCertChainLib.sol#L241-L241)

```solidity
File: /contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

282:             quoteCerts[i] = Base64.decode(string(quoteCerts[i]));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L282-L282)

</details>

### <a name="GAS-15-1693311904"></a>[GAS-15] Cache array length outside of loop
If not cached, the solidity compiler will always read the length of the array during each iteration. That is, if it is a storage array, this is an extra sload operation (100 additional extra gas for each iteration except for the first) and if it is a memory array, this is an extra mload operation (3 additional gas for each iteration except for the first).

*Instances (29)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/hooks/AssignmentHook.sol

172:         for (uint256 i; i < _tierFees.length; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/hooks/AssignmentHook.sol#L172)

```solidity
File: /contracts/L1/libs/LibDepositing.sol

86:             for (uint256 i; i < deposits_.length;) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibDepositing.sol#L86)

```solidity
File: /contracts/L1/libs/LibProposing.sol

244:             for (uint256 i; i < params.hookCalls.length; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProposing.sol#L244)

```solidity
File: /contracts/L1/provers/Guardians.sol

74:         for (uint256 i; i < guardians.length; ++i) {

80:         for (uint256 i = 0; i < _newGuardians.length; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/provers/Guardians.sol#L80)

```solidity
File: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

80:         for (uint256 i; i < serialNumBatch.length; ++i) {

95:         for (uint256 i; i < serialNumBatch.length; ++i) {

191:         for (uint256 i; i < enclaveId.tcbLevels.length; ++i) {

214:         for (uint256 i; i < tcb.tcbLevels.length; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/AutomataDcapV3Attestation.sol#L214)

```solidity
File: /contracts/automata-attestation/lib/PEMCertChainLib.sol

244:         for (uint256 i; i < split.length; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/PEMCertChainLib.sol#L244)

```solidity
File: /contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

153:         for (uint256 i; i < encoded.length; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L153)

```solidity
File: /contracts/automata-attestation/utils/RsaVerify.sol

174:         for (uint256 i; i < _sha256.length; ++i) {

283:         for (uint256 i; i < sha1Prefix.length; ++i) {

290:         for (uint256 i; i < _sha1.length; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/RsaVerify.sol#L290)

```solidity
File: /contracts/bridge/Bridge.sol

90:         for (uint256 i; i < _msgHashes.length; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L90)

```solidity
File: /contracts/signal/SignalService.sol

104:         for (uint256 i; i < hopProofs.length; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/SignalService.sol#L104)

```solidity
File: /contracts/team/airdrop/ERC721Airdrop.sol

59:         for (uint256 i; i < tokenIds.length; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC721Airdrop.sol#L59)

```solidity
File: /contracts/thirdparty/optimism/rlp/RLPWriter.sol

66:         for (uint256 j = 0; j < out_.length; j++) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66)

```solidity
File: /contracts/thirdparty/optimism/trie/MerkleTrie.sol

85:         for (uint256 i = 0; i < proof.length; i++) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85)

```solidity
File: /contracts/tokenvault/ERC1155Vault.sol

47:         for (uint256 i; i < _op.amounts.length; ++i) {

251:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

269:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC1155Vault.sol#L269)

```solidity
File: /contracts/tokenvault/ERC721Vault.sol

34:         for (uint256 i; i < _op.tokenIds.length; ++i) {

170:             for (uint256 i; i < _tokenIds.length; ++i) {

175:             for (uint256 i; i < _tokenIds.length; ++i) {

197:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

210:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC721Vault.sol#L210)

```solidity
File: /contracts/verifiers/SgxVerifier.sol

104:         for (uint256 i; i < _ids.length; ++i) {

210:         for (uint256 i; i < _instances.length; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/SgxVerifier.sol#L210)

</details>

### <a name="GAS-16-1693311936"></a>[GAS-16] State variables should be cached in stack variables rather than re-reading them from storage
The instances below point to the second+ access of a state variable within a function. Caching of a state variable replaces each Gwarmaccess (100 gas) with a much cheaper stack read. Other less obvious fixes/optimizations include having local memory caches of state variable structs, or having local caches of state variable contracts/addresses.

*Saves 100 gas per instance*

*Instances (6)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/TaikoL1.sol

70:             LibVerifying.verifyBlocks(state, config, this, config.maxBlocksToVerifyPerProposal);

96:         LibVerifying.verifyBlocks(state, config, this, maxBlocksToVerify);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/TaikoL1.sol#L96)

```solidity
File: /contracts/team/TimelockTokenPool.sol

220:         IERC20(costToken).safeTransferFrom(_recipient, sharedVault, costToWithdraw);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/TimelockTokenPool.sol#L220)

```solidity
File: /contracts/team/airdrop/ERC20Airdrop.sol

71:         IVotes(token).delegateBySig(delegatee, nonce, expiry, v, r, s);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC20Airdrop.sol#L71)

```solidity
File: /contracts/tokenvault/BridgedERC20Base.sol

82:             IBridgedERC20(migratingAddress).mint(_account, _amount);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC20Base.sol#L82)

```solidity
File: /contracts/verifiers/SgxVerifier.sol

220:             emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/SgxVerifier.sol#L220)

</details>

### <a name="GAS-17-1699447317"></a>[GAS-17] Avoid caching global special variables
It's better not to cache the global special variables, because it's cheaper to use them directly (e.g. `msg.sender`).

*Instances (1)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/hooks/AssignmentHook.sol

93:         address taikoL1Address = msg.sender;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/hooks/AssignmentHook.sol#L93)

</details>

### <a name="GAS-18-1693311951"></a>[GAS-18] Use calldata instead of memory for function arguments that do not get mutated
Mark data types as `calldata` instead of `memory` where possible. This makes it so that the data is not automatically loaded into memory. If the data passed into the function does not need to be changed (like updating values in an array), it can be passed in as `calldata`. The one exception to this is if the argument must later be passed into another function that takes an argument that specifies `memory` storage.

*Instances (12)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/hooks/AssignmentHook.sol

//@audit Make `_blk` as a calldata
63:         TaikoData.Block memory _blk,

//@audit Make `_assignment` as a calldata
138:         ProverAssignment memory _assignment,

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/hooks/AssignmentHook.sol#L138)

```solidity
File: /contracts/L1/libs/LibUtils.sol

//@audit Make `_config` as a calldata
25:         TaikoData.Config memory _config,

//@audit Make `_config` as a calldata
54:         TaikoData.Config memory _config,

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibUtils.sol#L54)

```solidity
File: /contracts/automata-attestation/utils/SigVerifyLib.sol

//@audit Make `publicKey` as a calldata
27:         PublicKey memory publicKey,

//@audit Make `publicKey` as a calldata
57:         PublicKey memory publicKey,

//@audit Make `publicKey` as a calldata
82:         bytes memory publicKey

//@audit Make `publicKey` as a calldata
99:         bytes memory publicKey

//@audit Make `signature` as a calldata
115:         bytes memory signature,

//@audit Make `publicKey` as a calldata
116:         bytes memory publicKey

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/SigVerifyLib.sol#L116)

```solidity
File: /contracts/tokenvault/BridgedERC1155.sol

//@audit Make `_symbol` as a calldata
43:         string memory _symbol,

//@audit Make `_name` as a calldata
44:         string memory _name

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC1155.sol#L44)

</details>

### <a name="GAS-19-1693312015"></a>[GAS-19] Add `unchecked {}` for subtractions where the operands cannot underflow because of a previous `require()` or `if`-statement
`require(a <= b); x = b - a` => `require(a <= b); unchecked { x = b - a }`

*Instances (4)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L2/TaikoL2.sol

276:                 numL1Blocks = _l1BlockId - lastSyncedBlock;

281:                 excess = excess > issuance ? excess - issuance : 1;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/TaikoL2.sol#L281)

```solidity
File: /contracts/automata-attestation/lib/PEMCertChainLib.sol

265:         uint256 lengthDiff = n - expectedLength;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/PEMCertChainLib.sol#L265)

```solidity
File: /contracts/thirdparty/optimism/rlp/RLPWriter.sol

47:                 out_[i] = bytes1(uint8((_len / (256 ** (lenLen - i))) % 256));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/rlp/RLPWriter.sol#L47)

</details>

### <a name="GAS-20-1693312028"></a>[GAS-20] `x += y` costs more gas than `x = x + y` for state variables
Not inlining costs 20 to 40 gas because of two extra JUMP instructions and additional stack operations needed for function calls.

*Instances (4)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/team/TimelockTokenPool.sol

141:         totalAmountGranted += _grant.amount;

156:         totalAmountVoided += amountVoided;

216:         totalAmountWithdrawn += amountToWithdraw;

217:         totalCostPaid += costToWithdraw;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/TimelockTokenPool.sol#L217)

</details>

### <a name="GAS-21-1699456351"></a>[GAS-21] Gas savings can be achieved by changing the model for assigning value to the structure ***123 gas***
Change this `structName a = structName({item1: val1,item2: val2}); ==> structName a; a.item1 = val1; a.item2 = val2;`

*Instances (19)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/libs/LibDepositing.sol

88:                 deposits_[i] = TaikoData.EthDeposit({
                        recipient: address(uint160(data >> 96)),
                        amount: uint96(data),
                        id: j
                    });

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibDepositing.sol#L88-L92)

```solidity
File: /contracts/L1/libs/LibProposing.sol

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
                 });

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
             });

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProposing.sol#L212-L226)

```solidity
File: /contracts/L1/libs/LibProving.sol

166:                 IVerifier.Context memory ctx = IVerifier.Context({
                         metaHash: blk.metaHash,
                         blobHash: _meta.blobHash,
                         // Separate msgSender to allow the prover to be any address in the future.
                         prover: msg.sender,
                         msgSender: msg.sender,
                         blockId: blk.blockId,
                         isContesting: isContesting,
                         blobUsed: _meta.blobUsed
                     });

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProving.sol#L166-L175)

```solidity
File: /contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

54:         v3ParsedQuote = V3Struct.ParsedV3QuoteStruct({
                header: header,
                localEnclaveReport: localEnclaveReport,
                v3AuthData: authDataV3
            });

190:         header = V3Struct.Header({
                 version: version,
                 attestationKeyType: attestationKeyType,
                 teeType: teeType,
                 qeSvn: bytes2(rawHeader.substring(8, 2)),
                 pceSvn: bytes2(rawHeader.substring(10, 2)),
                 qeVendorId: qeVendorId,
                 userData: bytes20(rawHeader.substring(28, 20))
             });

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L190-L198)

```solidity
File: /contracts/bridge/Bridge.sol

243:                 proofReceipt[msgHash] = ProofReceipt({
                         receivedAt: receivedAt,
                         preferredExecutor: _message.gasLimit == 0 ? _message.destOwner : msg.sender
                     });

549:             __ctx = Context(_msgHash, _from, _srcChainId);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L549-L549)

```solidity
File: /contracts/thirdparty/optimism/rlp/RLPReader.sol

47:         out_ = RLPItem({ length: _in.length, ptr: ptr });

84:             out_[itemCount] = RLPItem({
                    length: itemLength + itemOffset,
                    ptr: MemoryPointer.wrap(MemoryPointer.unwrap(_in.ptr) + offset)
                });

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/rlp/RLPReader.sol#L84-L87)

```solidity
File: /contracts/thirdparty/optimism/trie/MerkleTrie.sol

209:             proof_[i] = TrieNode({ encoded: _proof[i], decoded: RLPReader.readList(_proof[i]) });

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/trie/MerkleTrie.sol#L209-L209)

```solidity
File: /contracts/tokenvault/ERC1155Vault.sol

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
            });

256:                 ctoken_ = CanonicalNFT({
                         chainId: uint64(block.chainid),
                         addr: _op.token,
                         symbol: "",
                         name: ""
                     });

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC1155Vault.sol#L256-L261)

```solidity
File: /contracts/tokenvault/ERC20Vault.sol

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
             });

365:             ctoken_ = CanonicalERC20({
                     chainId: uint64(block.chainid),
                     addr: _token,
                     decimals: meta.decimals(),
                     symbol: meta.symbol(),
                     name: meta.name()
                 });

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC20Vault.sol#L365-L371)

```solidity
File: /contracts/tokenvault/ERC721Vault.sol

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
            });

203:                 ctoken_ = CanonicalNFT({
                         chainId: uint64(block.chainid),
                         addr: _op.token,
                         symbol: t.symbol(),
                         name: t.name()
                     });

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC721Vault.sol#L203-L208)

```solidity
File: /contracts/verifiers/SgxVerifier.sol

217:             instances[nextInstanceId] = Instance(_instances[i], validSince);

229:         instances[id] = Instance(newInstance, uint64(block.timestamp));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/SgxVerifier.sol#L229-L229)

</details>

### <a name="GAS-22-1696084432"></a>[GAS-22] Simple checks for zero `uint` can be done using assembly to save gas

*Instances (58)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/libs/LibProposing.sol

135:                 blobUsed: _txList.length == 0,

195:         if (meta_.txListByteSize == 0 || meta_.txListByteSize > _config.blockMaxTxListBytes) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProposing.sol#L195)

```solidity
File: /contracts/L1/libs/LibProving.sol

134:         if (_proof.tier == 0 || _proof.tier < _meta.minTier || _proof.tier < ts.tier) {

186:         bool isTopTier = tier.contestBond == 0;

223:                 assert(tier.validityBond == 0);

224:                 assert(ts.validityBond == 0 && ts.contestBond == 0 && ts.contester == address(0));

224:                 assert(ts.validityBond == 0 && ts.contestBond == 0 && ts.contester == address(0));

280:         if (tid_ == 0) {

412:         if (_tier.contestBond == 0) return;

419:         if (_tid == 1 && _ts.tier == 0 && inProvingWindow) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProving.sol#L419)

```solidity
File: /contracts/L1/libs/LibUtils.sol

43:         if (tid == 0) revert L1_TRANSITION_NOT_FOUND();

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibUtils.sol#L43)

```solidity
File: /contracts/L1/libs/LibVerifying.sol

93:         if (_maxBlocksToVerify == 0) {

111:         if (tid == 0) revert L1_TRANSITION_ID_ZERO();

137:                 if (tid == 0) break;

250:                 || _config.blockMaxGasLimit == 0 || _config.blockMaxTxListBytes == 0

250:                 || _config.blockMaxGasLimit == 0 || _config.blockMaxTxListBytes == 0

252:                 || _config.livenessBond == 0 || _config.ethDepositRingBufferSize <= 1

253:                 || _config.ethDepositMinCountPerBlock == 0

258:                 || _config.ethDepositMinAmount == 0

260:                 || _config.ethDepositMaxAmount > type(uint96).max || _config.ethDepositGas == 0

261:                 || _config.ethDepositMaxFee == 0

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibVerifying.sol#L261)

```solidity
File: /contracts/L1/provers/Guardians.sol

113:         if (id == 0) revert INVALID_GUARDIAN();

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/provers/Guardians.sol#L113)

```solidity
File: /contracts/L1/tiers/MainnetTierProvider.sol

68:         if (_rand % 1000 == 0) return LibTiers.TIER_SGX_ZKVM;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/tiers/MainnetTierProvider.sol#L68)

```solidity
File: /contracts/L1/tiers/TestnetTierProvider.sol

68:         if (_rand % 10 == 0) return LibTiers.TIER_SGX;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/tiers/TestnetTierProvider.sol#L68)

```solidity
File: /contracts/L2/CrossChainOwned.sol

70:         if (_ownerChainId == 0 || _ownerChainId == block.chainid) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/CrossChainOwned.sol#L70)

```solidity
File: /contracts/L2/Lib1559Math.sol

24:         if (_adjustmentFactor == 0) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/Lib1559Math.sol#L24)

```solidity
File: /contracts/L2/TaikoL2.sol

86:         if (block.number == 0) {

117:             _l1BlockHash == 0 || _l1StateRoot == 0 || _l1BlockId == 0

118:                 || (block.number != 1 && _parentGasUsed == 0)

296:         if (basefee_ == 0) basefee_ = 1;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/TaikoL2.sol#L296)

```solidity
File: /contracts/L2/TaikoL2EIP1559Configurable.sol

33:         if (_newConfig.gasTargetPerL1Block == 0) revert L2_INVALID_CONFIG();

34:         if (_newConfig.basefeeAdjustmentQuotient == 0) revert L2_INVALID_CONFIG();

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/TaikoL2EIP1559Configurable.sol#L34)

```solidity
File: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

421:                 bool isPckCert = i == 0; // additional parsing for PCKCert

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/AutomataDcapV3Attestation.sol#L421)

```solidity
File: /contracts/automata-attestation/utils/BytesUtils.sol

345:         if (len % 8 == 0) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/BytesUtils.sol#L345)

```solidity
File: /contracts/bridge/Bridge.sol

245:                     preferredExecutor: _message.gasLimit == 0 ? _message.destOwner : msg.sender

260:             if (_message.gasLimit == 0 && msg.sender != _message.destOwner) {

321:         if (_message.gasLimit == 0 || _isLastAttempt) {

485:         if (_gasLimit == 0) revert B_INVALID_GAS_LIMIT();

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L485)

```solidity
File: /contracts/libs/LibTrieProof.sol

50:             if (rlpAccount.length == 0) revert LTP_INVALID_ACCOUNT_PROOF();

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/libs/LibTrieProof.sol#L50)

```solidity
File: /contracts/signal/SignalService.sol

95:         if (hopProofs.length == 0) revert SS_EMPTY_PROOF();

114:                 if (hop.chainId == 0 || hop.chainId == block.chainid) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/SignalService.sol#L114)

```solidity
File: /contracts/team/TimelockTokenPool.sol

154:         if (amountVoided == 0) revert NOTHING_TO_VOID();

255:         if (_amount == 0) return 0;

256:         if (_start == 0) return _amount;

259:         if (_period == 0) return _amount;

268:         if (_grant.amount == 0) revert INVALID_GRANT();

274:         if (_start == 0 || _period == 0) {

274:         if (_start == 0 || _period == 0) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/TimelockTokenPool.sol#L274)

```solidity
File: /contracts/team/airdrop/ERC20Airdrop2.sol

111:         if (balance == 0) return (0, 0);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC20Airdrop2.sol#L111)

```solidity
File: /contracts/team/airdrop/MerkleClaimable.sol

35:             merkleRoot == 0x0 || claimStart == 0 || claimEnd == 0 || claimStart > block.timestamp

35:             merkleRoot == 0x0 || claimStart == 0 || claimEnd == 0 || claimStart > block.timestamp

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/MerkleClaimable.sol#L35)

```solidity
File: /contracts/thirdparty/optimism/rlp/RLPReader.sol

287:         if (_length == 0) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/rlp/RLPReader.sol#L287)

```solidity
File: /contracts/thirdparty/optimism/trie/MerkleTrie.sol

91:             if (currentKeyIndex == 0) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/trie/MerkleTrie.sol#L91)

```solidity
File: /contracts/tokenvault/ERC1155Vault.sol

48:             if (_op.amounts[i] == 0) revert VAULT_INVALID_AMOUNT();

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC1155Vault.sol#L48)

```solidity
File: /contracts/tokenvault/ERC20Vault.sol

214:         if (_op.amount == 0) revert VAULT_INVALID_AMOUNT();

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC20Vault.sol#L214)

```solidity
File: /contracts/tokenvault/LibBridgedToken.sol

21:             _srcToken == address(0) || _srcChainId == 0 || _srcChainId == block.chainid

22:                 || bytes(_symbol).length == 0 || bytes(_name).length == 0

22:                 || bytes(_symbol).length == 0 || bytes(_name).length == 0

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/LibBridgedToken.sol#L22)

</details>

### <a name="GAS-23-1708173673"></a>[GAS-23] Combine `mapping`s referenced in the same function by the same key
Reads and subsequent writes can also be cheaper when a function requires both values and they both fit in the same storage slot (i.e. runtime gas savings). Even if the values can't be packed, if both fields are accessed in the same function (as is the case for these instances), combining them can save **~42 gas per access** due to [not having to recalculate the key's keccak256 hash](https://gist.github.com/IllIllI000/639032d73e35d7e968ff58d8784bc445) (Gkeccak256 - 30 gas) and that calculation's associated stack operations.

*Instances (1)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/team/airdrop/ERC20Airdrop2.sol

//@audit the following two maps should be combined : `claimedAmount` and `withdrawnAmount`
104:     function getBalance(address user)
             public
             view
             returns (uint256 balance, uint256 withdrawableAmount)
         {
             balance = claimedAmount[user];
             // If balance is 0 then there is no balance and withdrawable amount
             if (balance == 0) return (0, 0);
             // Balance might be positive before end of claiming (claimEnd - if claimed already) but
             // withdrawable is 0.
             if (block.timestamp < claimEnd) return (balance, 0);
     
             // Hard cap timestamp - so range cannot go over - to get more allocation over time.
             uint256 timeBasedAllowance = balance
                 * (block.timestamp.min(claimEnd + withdrawalWindow) - claimEnd) / withdrawalWindow;
     
             withdrawableAmount = timeBasedAllowance - withdrawnAmount[user];
         }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC20Airdrop2.sol#L104-L121)

</details>

### <a name="GAS-24-1706544439"></a>[GAS-24] Counting down in for statements is more gas efficient
Looping downwards in Solidity is more gas efficient due to how the EVM compares variables. In a 'for' loop that counts down, the end condition is usually to compare with zero, which is cheaper than comparing with another number. As such, restructure your loops to count downwards where possible.

*Instances (45)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/hooks/AssignmentHook.sol

172:         for (uint256 i; i < _tierFees.length; ++i) {
                 if (_tierFees[i].tier == _tierId) return _tierFees[i].fee;
             }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/hooks/AssignmentHook.sol#L172-L174)

```solidity
File: /contracts/L1/libs/LibProposing.sol

244:             for (uint256 i; i < params.hookCalls.length; ++i) {
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

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProposing.sol#L244-L258)

```solidity
File: /contracts/L1/provers/Guardians.sol

74:         for (uint256 i; i < guardians.length; ++i) {
                delete guardianIds[guardians[i]];
            }

80:         for (uint256 i = 0; i < _newGuardians.length; ++i) {
                address guardian = _newGuardians[i];
                if (guardian == address(0)) revert INVALID_GUARDIAN();
                // This makes sure there are not duplicate addresses
                if (guardianIds[guardian] != 0) revert INVALID_GUARDIAN_SET();
    
                // Save and index the guardian
                guardians.push(guardian);
                guardianIds[guardian] = guardians.length;
            }

133:             for (uint256 i; i < guardiansLength; ++i) {
                     if (bits & 1 == 1) ++count;
                     if (count == minGuardians) return true;
                     bits >>= 1;
                 }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/provers/Guardians.sol#L133-L137)

```solidity
File: /contracts/L2/TaikoL2.sol

234:             for (uint256 i; i < 255 && _blockId >= i + 1; ++i) {
                     uint256 j = _blockId - i - 1;
                     inputs[j % 255] = blockhash(j);
                 }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/TaikoL2.sol#L234-L237)

```solidity
File: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

80:         for (uint256 i; i < serialNumBatch.length; ++i) {
                if (_serialNumIsRevoked[index][serialNumBatch[i]]) {
                    continue;
                }
                _serialNumIsRevoked[index][serialNumBatch[i]] = true;
            }

95:         for (uint256 i; i < serialNumBatch.length; ++i) {
                if (!_serialNumIsRevoked[index][serialNumBatch[i]]) {
                    continue;
                }
                delete _serialNumIsRevoked[index][serialNumBatch[i]];
            }

191:         for (uint256 i; i < enclaveId.tcbLevels.length; ++i) {
                 EnclaveIdStruct.TcbLevel memory tcb = enclaveId.tcbLevels[i];
                 if (tcb.tcb.isvsvn <= quoteEnclaveReport.isvSvn) {
                     tcbFound = true;
                     status = tcb.tcbStatus;
                     break;
                 }
             }

214:         for (uint256 i; i < tcb.tcbLevels.length; ++i) {
                 TCBInfoStruct.TCBLevelObj memory current = tcb.tcbLevels[i];
                 bool pceSvnIsHigherOrGreater = pck.sgxExtension.pcesvn >= current.pcesvn;
                 bool cpuSvnsAreHigherOrGreater = _isCpuSvnHigherOrGreater(
                     pck.sgxExtension.sgxTcbCompSvnArr, current.sgxTcbCompSvnArr
                 );
                 if (pceSvnIsHigherOrGreater && cpuSvnsAreHigherOrGreater) {
                     status = current.status;
                     bool tcbIsRevoked = status == TCBInfoStruct.TCBStatus.TCB_REVOKED;
                     return (!tcbIsRevoked, status);
                 }
             }

240:         for (uint256 i; i < CPUSVN_LENGTH; ++i) {
                 if (pckCpuSvns[i] < tcbCpuSvns[i]) {
                     return false;
                 }
             }

259:         for (uint256 i; i < n; ++i) {
                 IPEMCertChainLib.ECSha256Certificate memory issuer;
                 if (i == n - 1) {
                     // rootCA
                     issuer = certs[i];
                 } else {
                     issuer = certs[i + 1];
                     if (i == n - 2) {
                         // this cert is expected to be signed by the root
                         certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.ROOT)][certs[i]
                             .serialNumber];
                     } else if (certs[i].isPck) {
                         certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.PCK)][certs[i]
                             .serialNumber];
                     }
                     if (certRevoked) {
                         break;
                     }
                 }
     
                 certNotExpired =
                     block.timestamp > certs[i].notBefore && block.timestamp < certs[i].notAfter;
                 if (!certNotExpired) {
                     break;
                 }
     
                 verified = sigVerifyLib.verifyES256Signature(
                     certs[i].tbsCertificate, certs[i].signature, issuer.pubKey
                 );
                 if (!verified) {
                     break;
                 }
     
                 bytes32 issuerPubKeyHash = keccak256(issuer.pubKey);
     
                 if (issuerPubKeyHash == ROOTCA_PUBKEY_HASH) {
                     certChainCanBeTrusted = true;
                     break;
                 }
             }

420:             for (uint256 i; i < 3; ++i) {
                     bool isPckCert = i == 0; // additional parsing for PCKCert
                     bool certDecodedSuccessfully;
                     // todo! move decodeCert offchain
                     (certDecodedSuccessfully, parsedQuoteCerts[i]) = pemCertLib.decodeCert(
                         authDataV3.certification.decodedCertDataArray[i], isPckCert
                     );
                     if (!certDecodedSuccessfully) {
                         return (false, retData);
                     }
                 }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/AutomataDcapV3Attestation.sol#L420-L430)

```solidity
File: /contracts/automata-attestation/lib/PEMCertChainLib.sol

54:         for (uint256 i; i < size; ++i) {
                string memory input;
                if (i > 0) {
                    input = LibString.slice(pemChainStr, index, index + len);
                } else {
                    input = pemChainStr;
                }
                uint256 increment;
                (success, certs[i], increment) = _removeHeadersAndFooters(input);
    
                if (!success) {
                    return (false, certs);
                }
    
                index += increment;
            }

244:         for (uint256 i; i < split.length; ++i) {
                 contentStr = LibString.concat(contentStr, split[i]);
             }

354:         for (uint256 i; i < SGX_TCB_CPUSVN_SIZE + 1; ++i) {
                 uint256 svnPtr = der.firstChildOf(svnParentPtr); // OID
                 uint256 svnValuePtr = der.nextSiblingOf(svnPtr); // value
                 bytes memory svnValueBytes = der.bytesAt(svnValuePtr);
                 uint16 svnValue = svnValueBytes.length < 2
                     ? uint16(bytes2(svnValueBytes)) / 256
                     : uint16(bytes2(svnValueBytes));
                 if (BytesUtils.compareBytes(der.bytesAt(svnPtr), PCESVN_OID)) {
                     // pcesvn is 4 bytes in size
                     pcesvn = uint256(svnValue);
                 } else {
                     // each cpusvn is at maximum two bytes in size
                     uint256 cpusvn = uint256(svnValue);
                     cpusvns[i] = cpusvn;
                 }
     
                 // iterate to the next svn object in the sequence
                 svnParentPtr = der.nextSiblingOf(svnParentPtr);
             }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/PEMCertChainLib.sol#L354-L372)

```solidity
File: /contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

153:         for (uint256 i; i < encoded.length; ++i) {
                 uint256 digits = uint256(uint8(bytes1(encoded[i])));
                 uint256 upperDigit = digits / 16;
                 uint256 lowerDigit = digits % 16;
     
                 uint256 acc = lowerDigit * (16 ** (2 * i));
                 acc += upperDigit * (16 ** ((2 * i) + 1));
     
                 decoded += acc;
             }

281:         for (uint256 i; i < 3; ++i) {
                 quoteCerts[i] = Base64.decode(string(quoteCerts[i]));
             }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L281-L283)

```solidity
File: /contracts/automata-attestation/utils/BytesUtils.sol

333:         for (uint256 i; i < len; ++i) {
                 bytes1 char = self[off + i];
                 require(char >= 0x30 && char <= 0x7A, "invalid char");
                 decoded = uint8(BASE32_HEX_TABLE[uint256(uint8(char)) - 0x30]);
                 require(decoded <= 0x20, "invalid decoded");
                 if (i == len - 1) {
                     break;
                 }
                 ret = (ret << 5) | decoded;
             }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/BytesUtils.sol#L333-L342)

```solidity
File: /contracts/automata-attestation/utils/RsaVerify.sol

140:         for (uint256 i = 2; i < 2 + paddingLen; ++i) {
                 if (decipher[i] != 0xff) {
                     return false;
                 }
             }

152:             for (uint256 i; i < digestAlgoWithParamLen; ++i) {
                     if (decipher[3 + paddingLen + i] != bytes1(sha256ExplicitNullParam[i])) {
                         return false;
                     }
                 }

158:             for (uint256 i; i < digestAlgoWithParamLen; ++i) {
                     if (decipher[3 + paddingLen + i] != bytes1(sha256ImplicitNullParam[i])) {
                         return false;
                     }
                 }

174:         for (uint256 i; i < _sha256.length; ++i) {
                 if (decipher[5 + paddingLen + digestAlgoWithParamLen + i] != _sha256[i]) {
                     return false;
                 }
             }

273:         for (uint256 i = 2; i < 2 + paddingLen; ++i) {
                 if (decipher[i] != 0xff) {
                     return false;
                 }
             }

283:         for (uint256 i; i < sha1Prefix.length; ++i) {
                 if (decipher[3 + paddingLen + i] != bytes1(sha1Prefix[i])) {
                     return false;
                 }
             }

290:         for (uint256 i; i < _sha1.length; ++i) {
                 if (decipher[3 + paddingLen + sha1Prefix.length + i] != _sha1[i]) {
                     return false;
                 }
             }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/RsaVerify.sol#L290-L294)

```solidity
File: /contracts/automata-attestation/utils/X509DateUtils.sol

48:         for (uint16 i = 1970; i < year; ++i) {
                if (isLeapYear(i)) {
                    timestamp += 31_622_400; // Leap year in seconds
                } else {
                    timestamp += 31_536_000; // Normal year in seconds
                }
            }

59:         for (uint8 i = 1; i < month; ++i) {
                timestamp += uint256(monthDays[i - 1]) * 86_400; // Days in seconds
            }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/X509DateUtils.sol#L59-L61)

```solidity
File: /contracts/bridge/Bridge.sol

90:         for (uint256 i; i < _msgHashes.length; ++i) {
                bytes32 msgHash = _msgHashes[i];
                proofReceipt[msgHash].receivedAt = _timestamp;
                emit MessageSuspended(msgHash, _suspend);
            }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L90-L94)

```solidity
File: /contracts/signal/SignalService.sol

104:         for (uint256 i; i < hopProofs.length; ++i) {
                 hop = hopProofs[i];
     
                 bytes32 signalRoot = _verifyHopProof(chainId, app, signal, value, hop, signalService);
                 bool isLastHop = i == hopProofs.length - 1;
     
                 if (isLastHop) {
                     if (hop.chainId != block.chainid) revert SS_INVALID_LAST_HOP_CHAINID();
                     signalService = address(this);
                 } else {
                     if (hop.chainId == 0 || hop.chainId == block.chainid) {
                         revert SS_INVALID_MID_HOP_CHAINID();
                     }
                     signalService = resolve(hop.chainId, "signal_service", false);
                 }
     
                 bool isFullProof = hop.accountProof.length > 0;
     
                 _cacheChainData(hop, chainId, hop.blockId, signalRoot, isFullProof, isLastHop);
     
                 bytes32 kind = isFullProof ? LibSignals.STATE_ROOT : LibSignals.SIGNAL_ROOT;
                 signal = signalForChainData(chainId, kind, hop.blockId);
                 value = hop.rootHash;
                 chainId = hop.chainId;
                 app = signalService;
             }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/SignalService.sol#L104-L129)

```solidity
File: /contracts/team/airdrop/ERC721Airdrop.sol

59:         for (uint256 i; i < tokenIds.length; ++i) {
                IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);
            }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC721Airdrop.sol#L59-L61)

```solidity
File: /contracts/thirdparty/optimism/rlp/RLPWriter.sol

46:             for (i = 1; i <= lenLen; i++) {
                    out_[i] = bytes1(uint8((_len / (256 ** (lenLen - i))) % 256));
                }

59:         for (; i < 32; i++) {
                if (b[i] != 0) {
                    break;
                }
            }

66:         for (uint256 j = 0; j < out_.length; j++) {
                out_[j] = b[i++];
            }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66-L68)

```solidity
File: /contracts/thirdparty/optimism/trie/MerkleTrie.sol

85:         for (uint256 i = 0; i < proof.length; i++) {
                TrieNode memory currentNode = proof[i];
    
                // Key index should never exceed total key length or we'll be out of bounds.
                require(currentKeyIndex <= key.length, "MerkleTrie: key index exceeds total key length");
    
                if (currentKeyIndex == 0) {
                    // First proof element is always the root node.
                    require(
                        Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
                        "MerkleTrie: invalid root hash"
                    );
                } else if (currentNode.encoded.length >= 32) {
                    // Nodes 32 bytes or larger are hashed inside branch nodes.
                    require(
                        Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
                        "MerkleTrie: invalid large internal hash"
                    );
                } else {
                    // Nodes smaller than 32 bytes aren't hashed.
                    require(
                        Bytes.equal(currentNode.encoded, currentNodeID),
                        "MerkleTrie: invalid internal node hash"
                    );
                }
    
                if (currentNode.decoded.length == BRANCH_NODE_LENGTH) {
                    if (currentKeyIndex == key.length) {
                        // Value is the last element of the decoded list (for branch nodes). There's
                        // some ambiguity in the Merkle trie specification because bytes(0) is a
                        // valid value to place into the trie, but for branch nodes bytes(0) can exist
                        // even when the value wasn't explicitly placed there. Geth treats a value of
                        // bytes(0) as "key does not exist" and so we do the same.
                        value_ = RLPReader.readBytes(currentNode.decoded[TREE_RADIX]);
                        require(
                            value_.length > 0,
                            "MerkleTrie: value length must be greater than zero (branch)"
                        );
    
                        // Extra proof elements are not allowed.
                        require(
                            i == proof.length - 1,
                            "MerkleTrie: value node must be last node in proof (branch)"
                        );
    
                        return value_;
                    } else {
                        // We're not at the end of the key yet.
                        // Figure out what the next node ID should be and continue.
                        uint8 branchKey = uint8(key[currentKeyIndex]);
                        RLPReader.RLPItem memory nextNode = currentNode.decoded[branchKey];
                        currentNodeID = _getNodeID(nextNode);
                        currentKeyIndex += 1;
                    }
                } else if (currentNode.decoded.length == LEAF_OR_EXTENSION_NODE_LENGTH) {
                    bytes memory path = _getNodePath(currentNode);
                    uint8 prefix = uint8(path[0]);
                    uint8 offset = 2 - (prefix % 2);
                    bytes memory pathRemainder = Bytes.slice(path, offset);
                    bytes memory keyRemainder = Bytes.slice(key, currentKeyIndex);
                    uint256 sharedNibbleLength = _getSharedNibbleLength(pathRemainder, keyRemainder);
    
                    // Whether this is a leaf node or an extension node, the path remainder MUST be a
                    // prefix of the key remainder (or be equal to the key remainder) or the proof is
                    // considered invalid.
                    require(
                        pathRemainder.length == sharedNibbleLength,
                        "MerkleTrie: path remainder must share all nibbles with key"
                    );
    
                    if (prefix == PREFIX_LEAF_EVEN || prefix == PREFIX_LEAF_ODD) {
                        // Prefix of 2 or 3 means this is a leaf node. For the leaf node to be valid,
                        // the key remainder must be exactly equal to the path remainder. We already
                        // did the necessary byte comparison, so it's more efficient here to check that
                        // the key remainder length equals the shared nibble length, which implies
                        // equality with the path remainder (since we already did the same check with
                        // the path remainder and the shared nibble length).
                        require(
                            keyRemainder.length == sharedNibbleLength,
                            "MerkleTrie: key remainder must be identical to path remainder"
                        );
    
                        // Our Merkle Trie is designed specifically for the purposes of the Ethereum
                        // state trie. Empty values are not allowed in the state trie, so we can safely
                        // say that if the value is empty, the key should not exist and the proof is
                        // invalid.
                        value_ = RLPReader.readBytes(currentNode.decoded[1]);
                        require(
                            value_.length > 0,
                            "MerkleTrie: value length must be greater than zero (leaf)"
                        );
    
                        // Extra proof elements are not allowed.
                        require(
                            i == proof.length - 1,
                            "MerkleTrie: value node must be last node in proof (leaf)"
                        );
    
                        return value_;
                    } else if (prefix == PREFIX_EXTENSION_EVEN || prefix == PREFIX_EXTENSION_ODD) {
                        // Prefix of 0 or 1 means this is an extension node. We move onto the next node
                        // in the proof and increment the key index by the length of the path remainder
                        // which is equal to the shared nibble length.
                        currentNodeID = _getNodeID(currentNode.decoded[1]);
                        currentKeyIndex += sharedNibbleLength;
                    } else {
                        revert("MerkleTrie: received a node with an unknown prefix");
                    }
                } else {
                    revert("MerkleTrie: received an unparseable node");
                }
            }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85-L196)

```solidity
File: /contracts/tokenvault/ERC1155Vault.sol

47:         for (uint256 i; i < _op.amounts.length; ++i) {
                if (_op.amounts[i] == 0) revert VAULT_INVALID_AMOUNT();
            }

251:                 for (uint256 i; i < _op.tokenIds.length; ++i) {
                         BridgedERC1155(_op.token).burn(_user, _op.tokenIds[i], _op.amounts[i]);
                     }

269:                 for (uint256 i; i < _op.tokenIds.length; ++i) {
                         IERC1155(_op.token).safeTransferFrom({
                             from: msg.sender,
                             to: address(this),
                             id: _op.tokenIds[i],
                             amount: _op.amounts[i],
                             data: ""
                         });
                     }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC1155Vault.sol#L269-L277)

```solidity
File: /contracts/tokenvault/ERC721Vault.sol

34:         for (uint256 i; i < _op.tokenIds.length; ++i) {
                if (_op.amounts[i] != 0) revert VAULT_INVALID_AMOUNT();
            }

170:             for (uint256 i; i < _tokenIds.length; ++i) {
                     IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);
                 }

175:             for (uint256 i; i < _tokenIds.length; ++i) {
                     BridgedERC721(token_).mint(_to, _tokenIds[i]);
                 }

197:                 for (uint256 i; i < _op.tokenIds.length; ++i) {
                         BridgedERC721(_op.token).burn(_user, _op.tokenIds[i]);
                     }

210:                 for (uint256 i; i < _op.tokenIds.length; ++i) {
                         t.safeTransferFrom(_user, address(this), _op.tokenIds[i]);
                     }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC721Vault.sol#L210-L212)

```solidity
File: /contracts/verifiers/SgxVerifier.sol

104:         for (uint256 i; i < _ids.length; ++i) {
                 uint256 idx = _ids[i];
     
                 if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();
     
                 emit InstanceDeleted(idx, instances[idx].addr);
     
                 delete instances[idx];
             }

210:         for (uint256 i; i < _instances.length; ++i) {
                 if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();
     
                 addressRegistered[_instances[i]] = true;
     
                 if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();
     
                 instances[nextInstanceId] = Instance(_instances[i], validSince);
                 ids[i] = nextInstanceId;
     
                 emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);
     
                 nextInstanceId++;
             }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/SgxVerifier.sol#L210-L223)

</details>

### <a name="GAS-25-1693312067"></a>[GAS-25] Use custom errors rather than `revert()`/`require()` strings to save gas
Custom errors are available from solidity version 0.8.4. Custom errors save [**~50 gas**](https://gist.github.com/IllIllI000/ad1bd0d29a0101b25e57c293b4b0c746) each time they're hit by [avoiding having to allocate and store the revert string](https://blog.soliditylang.org/2021/04/21/custom-errors/#errors-in-depth). Not defining the strings also save deployment gas

*Instances (66)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

61:         require(msg.sender == owner, "onlyOwner");

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/AutomataDcapV3Attestation.sol#L61-L61)

```solidity
File: /contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

77:         require(
                localEnclaveReport.reserved3.length == 96 && localEnclaveReport.reserved4.length == 60
                    && localEnclaveReport.reportData.length == 64,
                "local QE report has wrong length"
            );

82:         require(
                pckSignedQeReport.reserved3.length == 96 && pckSignedQeReport.reserved4.length == 60
                    && pckSignedQeReport.reportData.length == 64,
                "QE report has wrong length"
            );

87:         require(
                v3Quote.v3AuthData.certification.certType == 5,
                "certType must be 5: Concatenated PCK Cert Chain (PEM formatted)"
            );

91:         require(
                v3Quote.v3AuthData.certification.decodedCertDataArray.length == 3, "3 certs in chain"
            );

94:         require(
                v3Quote.v3AuthData.ecdsa256BitSignature.length == 64
                    && v3Quote.v3AuthData.ecdsaAttestationKey.length == 64
                    && v3Quote.v3AuthData.qeReportSignature.length == 64,
                "Invalid ECDSA signature format"
            );

100:         require(
                 v3Quote.v3AuthData.qeAuthData.parsedDataSize
                     == v3Quote.v3AuthData.qeAuthData.data.length,
                 "Invalid QEAuthData size"
             );

116:         require(totalQuoteSize >= MINIMUM_QUOTE_LENGTH, "Invalid quote size");

279:         require(certParsedSuccessfully, "splitCertificateChain failed");

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L279-L279)

```solidity
File: /contracts/automata-attestation/utils/Asn1Decode.sol

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
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/Asn1Decode.sol#L182-L182)

```solidity
File: /contracts/automata-attestation/utils/BytesUtils.sol

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
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/BytesUtils.sol#L365-L365)

```solidity
File: /contracts/automata-attestation/utils/SigVerifyLib.sol

50:             revert("Unsupported algorithm");

75:             revert("Unsupported algorithm");

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/SigVerifyLib.sol#L75-L75)

```solidity
File: /contracts/thirdparty/optimism/Bytes.sol

25:             require(_length + 31 >= _length, "slice_overflow");

26:             require(_start + _length >= _start, "slice_overflow");

27:             require(_bytes.length >= _start + _length, "slice_outOfBounds");

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/Bytes.sol#L27-L27)

```solidity
File: /contracts/thirdparty/optimism/rlp/RLPReader.sol

37:         require(
                _in.length > 0,
                "RLPReader: length of an RLP item must be greater than zero to be decodable"
            );

56:         require(
                itemType == RLPItemType.LIST_ITEM,
                "RLPReader: decoded item type for list is not a list item"
            );

61:         require(
                listOffset + listLength == _in.length,
                "RLPReader: list item has an invalid data remainder"
            );

112:         require(
                 itemType == RLPItemType.DATA_ITEM,
                 "RLPReader: decoded item type for bytes is not a data item"
             );

117:         require(
                 _in.length == itemOffset + itemLength,
                 "RLPReader: bytes value contains an invalid remainder"
             );

152:         require(
                 _in.length > 0,
                 "RLPReader: length of an RLP item must be greater than zero to be decodable"
             );

172:             require(
                     _in.length > strLen,
                     "RLPReader: length of content must be greater than string length (short string)"
                 );

182:             require(
                     strLen != 1 || firstByteOfContent >= 0x80,
                     "RLPReader: invalid prefix, single byte < 0x80 are not prefixed (short string)"
                 );

192:             require(
                     _in.length > lenOfStrLen,
                     "RLPReader: length of content must be > than length of string length (long string)"
                 );

202:             require(
                     firstByteOfContent != 0x00,
                     "RLPReader: length of content must not have any leading zeros (long string)"
                 );

212:             require(
                     strLen > 55,
                     "RLPReader: length of content must be greater than 55 bytes (long string)"
                 );

217:             require(
                     _in.length > lenOfStrLen + strLen,
                     "RLPReader: length of content must be greater than total length (long string)"
                 );

228:             require(
                     _in.length > listLen,
                     "RLPReader: length of content must be greater than list length (short list)"
                 );

238:             require(
                     _in.length > lenOfListLen,
                     "RLPReader: length of content must be > than length of list length (long list)"
                 );

248:             require(
                     firstByteOfContent != 0x00,
                     "RLPReader: length of content must not have any leading zeros (long list)"
                 );

258:             require(
                     listLen > 55,
                     "RLPReader: length of content must be greater than 55 bytes (long list)"
                 );

263:             require(
                     _in.length > lenOfListLen + listLen,
                     "RLPReader: length of content must be greater than total length (long list)"
                 );

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/rlp/RLPReader.sol#L263-L266)

```solidity
File: /contracts/thirdparty/optimism/trie/MerkleTrie.sol

77:         require(_key.length > 0, "MerkleTrie: empty key");

89:             require(currentKeyIndex <= key.length, "MerkleTrie: key index exceeds total key length");

93:                 require(
                        Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
                        "MerkleTrie: invalid root hash"
                    );

99:                 require(
                        Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
                        "MerkleTrie: invalid large internal hash"
                    );

105:                 require(
                         Bytes.equal(currentNode.encoded, currentNodeID),
                         "MerkleTrie: invalid internal node hash"
                     );

119:                     require(
                             value_.length > 0,
                             "MerkleTrie: value length must be greater than zero (branch)"
                         );

125:                     require(
                             i == proof.length - 1,
                             "MerkleTrie: value node must be last node in proof (branch)"
                         );

150:                 require(
                         pathRemainder.length == sharedNibbleLength,
                         "MerkleTrie: path remainder must share all nibbles with key"
                     );

162:                     require(
                             keyRemainder.length == sharedNibbleLength,
                             "MerkleTrie: key remainder must be identical to path remainder"
                         );

172:                     require(
                             value_.length > 0,
                             "MerkleTrie: value length must be greater than zero (leaf)"
                         );

178:                     require(
                             i == proof.length - 1,
                             "MerkleTrie: value node must be last node in proof (leaf)"
                         );

191:                     revert("MerkleTrie: received a node with an unknown prefix");

194:                 revert("MerkleTrie: received an unparseable node");

198:         revert("MerkleTrie: ran out of proof elements");

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/trie/MerkleTrie.sol#L198-L198)

</details>

### <a name="GAS-26-1693312114"></a>[GAS-26] Divisions which do not divide by -X cannot overflow or overflow so such operations can be unchecked to save gas
Make such found divisions are unchecked when ensured it is safe to do so

*Instances (13)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/TaikoL1.sol

215:             ethDepositMaxFee: 1 ether / 10,

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/TaikoL1.sol#L215)

```solidity
File: /contracts/L1/gov/TaikoGovernor.sol

124:         return 1_000_000_000 ether / 10_000; // 0.01% of Taiko Token

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/gov/TaikoGovernor.sol#L124)

```solidity
File: /contracts/L1/libs/LibVerifying.sol

262:                 || _config.ethDepositMaxFee > type(uint96).max / _config.ethDepositMaxCountPerBlock

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibVerifying.sol#L262)

```solidity
File: /contracts/L2/Lib1559Math.sol

28:         return _ethQty(_gasExcess, _adjustmentFactor) / LibFixedPointMath.SCALING_FACTOR

28:         return _ethQty(_gasExcess, _adjustmentFactor) / LibFixedPointMath.SCALING_FACTOR

41:         uint256 input = _gasExcess * LibFixedPointMath.SCALING_FACTOR / _adjustmentFactor;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/Lib1559Math.sol#L41)

```solidity
File: /contracts/automata-attestation/lib/PEMCertChainLib.sol

359:                 ? uint16(bytes2(svnValueBytes)) / 256

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/PEMCertChainLib.sol#L359)

```solidity
File: /contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

155:             uint256 upperDigit = digits / 16;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L155)

```solidity
File: /contracts/team/TimelockTokenPool.sol

197:         uint128 _amountUnlocked = amountUnlocked / 1e18; // divide first

264:         return _amount * uint64(block.timestamp - _start) / _period;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/TimelockTokenPool.sol#L264)

```solidity
File: /contracts/team/airdrop/ERC20Airdrop2.sol

117:         uint256 timeBasedAllowance = balance

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC20Airdrop2.sol#L117)

```solidity
File: /contracts/thirdparty/optimism/rlp/RLPWriter.sol

39:             while (_len / i != 0) {

47:                 out_[i] = bytes1(uint8((_len / (256 ** (lenLen - i))) % 256));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/rlp/RLPWriter.sol#L47)

</details>

### <a name="GAS-27-1693312130"></a>[GAS-27] Do not calculate constants
Due to how constant variables are implemented (replacements at compile-time), an expression assigned to a constant variable is recomputed each time that the variable is used, which wastes some gas. Even with optimizer enabled, gas consumtion is reduced when the constant is already calculated.

*Instances (2)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/libs/LibProposing.sol

21:     uint256 public constant MAX_BYTES_PER_BLOB = 4096 * 32;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProposing.sol#L21-L21)

```solidity
File: /contracts/thirdparty/optimism/trie/MerkleTrie.sol

24:     uint256 internal constant BRANCH_NODE_LENGTH = TREE_RADIX + 1;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/trie/MerkleTrie.sol#L24-L24)

</details>

### <a name="GAS-28-1694877823"></a>[GAS-28] Use `do while` loops instead of `for` loops
A `do while` loop will cost less gas since the condition is not being checked for the first iteration, Check my example on [github](https://github.com/he110-1/gasOptimization/blob/main/forToDoWhileOptimizationProof.sol). Actually, `do while` alwayse cast less gas compared to `For` check my second example [github](https://github.com/he110-1/gasOptimization/blob/main/forToDoWhileOptimizationProof2.sol)

*Instances (49)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/hooks/AssignmentHook.sol

172:         for (uint256 i; i < _tierFees.length; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/hooks/AssignmentHook.sol#L172)

```solidity
File: /contracts/L1/libs/LibDepositing.sol

86:             for (uint256 i; i < deposits_.length;) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibDepositing.sol#L86)

```solidity
File: /contracts/L1/libs/LibProposing.sol

244:             for (uint256 i; i < params.hookCalls.length; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProposing.sol#L244)

```solidity
File: /contracts/L1/provers/Guardians.sol

74:         for (uint256 i; i < guardians.length; ++i) {

80:         for (uint256 i = 0; i < _newGuardians.length; ++i) {

133:             for (uint256 i; i < guardiansLength; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/provers/Guardians.sol#L133)

```solidity
File: /contracts/L2/TaikoL2.sol

234:             for (uint256 i; i < 255 && _blockId >= i + 1; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/TaikoL2.sol#L234)

```solidity
File: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

80:         for (uint256 i; i < serialNumBatch.length; ++i) {

95:         for (uint256 i; i < serialNumBatch.length; ++i) {

191:         for (uint256 i; i < enclaveId.tcbLevels.length; ++i) {

214:         for (uint256 i; i < tcb.tcbLevels.length; ++i) {

240:         for (uint256 i; i < CPUSVN_LENGTH; ++i) {

259:         for (uint256 i; i < n; ++i) {

420:             for (uint256 i; i < 3; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/AutomataDcapV3Attestation.sol#L420)

```solidity
File: /contracts/automata-attestation/lib/PEMCertChainLib.sol

54:         for (uint256 i; i < size; ++i) {

244:         for (uint256 i; i < split.length; ++i) {

354:         for (uint256 i; i < SGX_TCB_CPUSVN_SIZE + 1; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/PEMCertChainLib.sol#L354)

```solidity
File: /contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

153:         for (uint256 i; i < encoded.length; ++i) {

281:         for (uint256 i; i < 3; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L281)

```solidity
File: /contracts/automata-attestation/utils/BytesUtils.sol

80:         for (uint256 idx = 0; idx < shortest; idx += 32) {

333:         for (uint256 i; i < len; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/BytesUtils.sol#L333)

```solidity
File: /contracts/automata-attestation/utils/RsaVerify.sol

140:         for (uint256 i = 2; i < 2 + paddingLen; ++i) {

152:             for (uint256 i; i < digestAlgoWithParamLen; ++i) {

158:             for (uint256 i; i < digestAlgoWithParamLen; ++i) {

174:         for (uint256 i; i < _sha256.length; ++i) {

273:         for (uint256 i = 2; i < 2 + paddingLen; ++i) {

283:         for (uint256 i; i < sha1Prefix.length; ++i) {

290:         for (uint256 i; i < _sha1.length; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/RsaVerify.sol#L290)

```solidity
File: /contracts/automata-attestation/utils/X509DateUtils.sol

48:         for (uint16 i = 1970; i < year; ++i) {

59:         for (uint8 i = 1; i < month; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/X509DateUtils.sol#L59)

```solidity
File: /contracts/bridge/Bridge.sol

90:         for (uint256 i; i < _msgHashes.length; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L90)

```solidity
File: /contracts/signal/SignalService.sol

104:         for (uint256 i; i < hopProofs.length; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/SignalService.sol#L104)

```solidity
File: /contracts/team/airdrop/ERC721Airdrop.sol

59:         for (uint256 i; i < tokenIds.length; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC721Airdrop.sol#L59)

```solidity
File: /contracts/thirdparty/optimism/rlp/RLPWriter.sol

46:             for (i = 1; i <= lenLen; i++) {

59:         for (; i < 32; i++) {

66:         for (uint256 j = 0; j < out_.length; j++) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66)

```solidity
File: /contracts/thirdparty/optimism/trie/MerkleTrie.sol

85:         for (uint256 i = 0; i < proof.length; i++) {

208:         for (uint256 i = 0; i < length;) {

244:         for (; shared_ < max && _a[shared_] == _b[shared_];) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/trie/MerkleTrie.sol#L244)

```solidity
File: /contracts/tokenvault/ERC1155Vault.sol

47:         for (uint256 i; i < _op.amounts.length; ++i) {

251:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

269:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC1155Vault.sol#L269)

```solidity
File: /contracts/tokenvault/ERC721Vault.sol

34:         for (uint256 i; i < _op.tokenIds.length; ++i) {

170:             for (uint256 i; i < _tokenIds.length; ++i) {

175:             for (uint256 i; i < _tokenIds.length; ++i) {

197:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

210:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC721Vault.sol#L210)

```solidity
File: /contracts/verifiers/SgxVerifier.sol

104:         for (uint256 i; i < _ids.length; ++i) {

210:         for (uint256 i; i < _instances.length; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/SgxVerifier.sol#L210)

</details>

### <a name="GAS-29-1693312160"></a>[GAS-29] Stack variable cost less while used in emiting event
Even if the variable is going to be used only one time, caching a state variable and use its cache in an emit would help you reduce the cost by at least ***9 gas***

*Instances (13)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/provers/Guardians.sol

// @audit `version` is a state variable
95:         emit GuardiansUpdated(version, _newGuardians);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/provers/Guardians.sol#L95)

```solidity
File: /contracts/L2/CrossChainOwned.sol

// @audit `nextTxId` is a state variable
53:         emit TransactionExecuted(nextTxId++, bytes4(txdata));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/CrossChainOwned.sol#L53)

```solidity
File: /contracts/L2/TaikoL2.sol

// @audit `gasExcess` is a state variable
157:         emit Anchored(blockhash(parentId), gasExcess);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/TaikoL2.sol#L157)

```solidity
File: /contracts/tokenvault/BridgedERC20Base.sol

// @audit `migratingAddress` is a state variable
63:             emit MigratedTo(migratingAddress, _account, _amount);

// @audit `migratingAddress` is a state variable
80:             emit MigratedTo(migratingAddress, _account, _amount);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC20Base.sol#L80)

```solidity
File: /contracts/tokenvault/ERC1155Vault.sol

// @audit `token` is a state variable
114:         emit TokenReceived({
                 msgHash: ctx.msgHash,
                 from: from,
                 to: to,
                 srcChainId: ctx.srcChainId,
                 ctoken: ctoken.addr,
                 token: token,
                 tokenIds: tokenIds,
                 amounts: amounts
             });

// @audit `token` is a state variable
149:         emit TokenReleased({
                 msgHash: msgHash,
                 from: message.srcOwner,
                 ctoken: ctoken.addr,
                 token: token,
                 tokenIds: tokenIds,
                 amounts: amounts
             });

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC1155Vault.sol#L149-L156)

```solidity
File: /contracts/tokenvault/ERC20Vault.sol

// @audit `token` is a state variable
273:         emit TokenReceived({
                 msgHash: ctx.msgHash,
                 from: from,
                 to: to,
                 srcChainId: ctx.srcChainId,
                 ctoken: ctoken.addr,
                 token: token,
                 amount: amount
             });

// @audit `token` is a state variable
306:         emit TokenReleased({
                 msgHash: _msgHash,
                 from: _message.srcOwner,
                 ctoken: ctoken.addr,
                 token: token,
                 amount: amount
             });

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC20Vault.sol#L306-L312)

```solidity
File: /contracts/tokenvault/ERC721Vault.sol

// @audit `token` is a state variable
97:         emit TokenReceived({
                msgHash: ctx.msgHash,
                from: from,
                to: to,
                srcChainId: ctx.srcChainId,
                ctoken: ctoken.addr,
                token: token,
                tokenIds: tokenIds,
                amounts: new uint256[](tokenIds.length)
            });

// @audit `token` is a state variable
131:         emit TokenReleased({
                 msgHash: _msgHash,
                 from: _message.srcOwner,
                 ctoken: ctoken.addr,
                 token: token,
                 tokenIds: tokenIds,
                 amounts: new uint256[](tokenIds.length)
             });

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC721Vault.sol#L131-L138)

```solidity
File: /contracts/verifiers/SgxVerifier.sol

// @audit `instances` is a state variable
109:             emit InstanceDeleted(idx, instances[idx].addr);

// @audit `nextInstanceId` is a state variable
220:             emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/SgxVerifier.sol#L220)

</details>

### <a name="GAS-30-1693312222"></a>[GAS-30] Events should be emitted outside of loops
Emitting an event has an overhead of **375 gas**, which will be incurred on every iteration of the loop. It is cheaper to `emit` only [once](https://github.com/ethereum/EIPs/blob/adad5968fd6de29902174e0cb51c8fc3dceb9ab5/EIPS/eip-1155.md?plain=1#L68) after the loop has finished.

*Instances (3)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/bridge/Bridge.sol

//@audit MessageSuspended is emited inside this loop
90:         for (uint256 i; i < _msgHashes.length; ++i) {
                bytes32 msgHash = _msgHashes[i];
                proofReceipt[msgHash].receivedAt = _timestamp;
                emit MessageSuspended(msgHash, _suspend);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L90-L93)

```solidity
File: /contracts/verifiers/SgxVerifier.sol

//@audit InstanceDeleted is emited inside this loop
104:         for (uint256 i; i < _ids.length; ++i) {
                 uint256 idx = _ids[i];
     
                 if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();
     
                 emit InstanceDeleted(idx, instances[idx].addr);

//@audit InstanceAdded is emited inside this loop
210:         for (uint256 i; i < _instances.length; ++i) {
                 if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();
     
                 addressRegistered[_instances[i]] = true;
     
                 if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();
     
                 instances[nextInstanceId] = Instance(_instances[i], validSince);
                 ids[i] = nextInstanceId;
     
                 emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/SgxVerifier.sol#L210-L220)

</details>

### <a name="GAS-31-1693312189"></a>[GAS-31] Superfluous event fields
`block.timestamp` and `block.number` are added to event information by default so adding them manually wastes gas

*Instances (1)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/verifiers/SgxVerifier.sol

230:         emit InstanceAdded(id, newInstance, oldInstance, block.timestamp);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/SgxVerifier.sol#L230)

</details>

### <a name="GAS-32-1693312238"></a>[GAS-32] Empty blocks should be removed or emit something
The code should be refactored such that they no longer exist, or the block should do something useful, such as emitting an event or reverting. If the contract is meant to be extended, the contract should be `abstract` and the function signatures be added without any default implementation. If the block is an empty `if`-statement block to avoid doing subsequent checks in the else-if/else conditions, the else-if/else conditions should be nested under the negation of the if-statement, because they involve different classes of checks, which may lead to the introduction of errors when the code is later modified (`if (x) {...} else if (y) {...} else {...}` => `if (!x) { if (y) {...} else {...} }`). Empty `receive()`/`fallback() payable` functions that are not used, can be removed to save deployment gas.

*Instances (1)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/libs/LibAddress.sol

46:     function supportsInterface(
            address _addr,
            bytes4 _interfaceId
        )
            internal
            view
            returns (bool result_)
        {
            if (!Address.isContract(_addr)) return false;
    
            try IERC165(_addr).supportsInterface(_interfaceId) returns (bool _result) {
                result_ = _result;
            } catch { }
        }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/libs/LibAddress.sol#L46-L59)

</details>

### <a name="GAS-33-1693312400"></a>[GAS-33] Don't initialize `uint` variables with default value
The default value for variables is zero, so initializing them to zero is superfluous.

*Instances (11)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/provers/Guardians.sol

80:         for (uint256 i = 0; i < _newGuardians.length; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/provers/Guardians.sol#L80)

```solidity
File: /contracts/automata-attestation/lib/PEMCertChainLib.sol

51:         uint256 index = 0;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/PEMCertChainLib.sol#L51)

```solidity
File: /contracts/automata-attestation/utils/BytesUtils.sol

80:         for (uint256 idx = 0; idx < shortest; idx += 32) {

331:         uint256 ret = 0;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/BytesUtils.sol#L331)

```solidity
File: /contracts/automata-attestation/utils/X509DateUtils.sol

46:         uint256 timestamp = 0;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/X509DateUtils.sol#L46)

```solidity
File: /contracts/thirdparty/optimism/rlp/RLPReader.sol

72:         uint256 itemCount = 0;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/rlp/RLPReader.sol#L72)

```solidity
File: /contracts/thirdparty/optimism/rlp/RLPWriter.sol

58:         uint256 i = 0;

66:         for (uint256 j = 0; j < out_.length; j++) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66)

```solidity
File: /contracts/thirdparty/optimism/trie/MerkleTrie.sol

82:         uint256 currentKeyIndex = 0;

85:         for (uint256 i = 0; i < proof.length; i++) {

208:         for (uint256 i = 0; i < length;) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/trie/MerkleTrie.sol#L208)

</details>

### <a name="GAS-34-1693312433"></a>[GAS-34] `internal` functions only called once can be inlined to save gas
Not inlining costs 20 to 40 gas because of two extra JUMP instructions and additional stack operations needed for function calls.

*Instances (12)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/TaikoL1.sol

220:     function _authorizePause(address)
             internal
             view
             virtual
             override
             onlyFromOwnerOrNamed("chain_pauser")
         { }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/TaikoL1.sol#L220-L226)

```solidity
File: /contracts/L1/TaikoToken.sol

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
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/TaikoToken.sol#L115-L121)

```solidity
File: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

126:     function _attestationTcbIsValid(TCBInfoStruct.TCBStatus status)
             internal
             pure
             virtual
             returns (bool valid)
         {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/AutomataDcapV3Attestation.sol#L126-L131)

```solidity
File: /contracts/common/EssentialContract.sol

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
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/common/EssentialContract.sol#L109)

```solidity
File: /contracts/signal/SignalService.sol

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
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/SignalService.sol#L206-L220)

```solidity
File: /contracts/team/airdrop/MerkleClaimable.sol

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
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/MerkleClaimable.sol#L77-L86)

```solidity
File: /contracts/tokenvault/BridgedERC20.sol

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
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC20.sol#L173-L179)

```solidity
File: /contracts/tokenvault/BridgedERC20Base.sol

97:     function _mintToken(address _account, uint256 _amount) internal virtual;
    
        function _burnToken(address _from, uint256 _amount) internal virtual;
    
        function _isMigratingOut() internal view returns (bool) {

99:     function _burnToken(address _from, uint256 _amount) internal virtual;
    
        function _isMigratingOut() internal view returns (bool) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC20Base.sol#L99-L101)

</details>

### <a name="GAS-35-1693312466"></a>[GAS-35] Inverting the condition of an `if`-`else`-statement wastes gas
Flipping the `true` and `false` blocks instead saves ***[3 gas](https://gist.github.com/IllIllI000/44da6fbe9d12b9ab21af82f14add56b9)***

*Instances (2)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/bridge/Bridge.sol

209:         } else if (!isMessageProven) {

302:         } else if (!isMessageProven) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L302)

</details>

### <a name="GAS-36-1693312497"></a>[GAS-36] `require()`/`revert()` strings longer than 32 bytes cost extra gas
Each extra memory word of bytes past the original 32 [incurs an MSTORE](https://gist.github.com/hrkrshnn/ee8fabd532058307229d65dcd5836ddc#consider-having-short-revert-strings) which costs **3 gas**

*Instances (30)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

87:         require(
                v3Quote.v3AuthData.certification.certType == 5,
                "certType must be 5: Concatenated PCK Cert Chain (PEM formatted)"
            );

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L87-L90)

```solidity
File: /contracts/thirdparty/optimism/rlp/RLPReader.sol

37:         require(
                _in.length > 0,
                "RLPReader: length of an RLP item must be greater than zero to be decodable"
            );

56:         require(
                itemType == RLPItemType.LIST_ITEM,
                "RLPReader: decoded item type for list is not a list item"
            );

61:         require(
                listOffset + listLength == _in.length,
                "RLPReader: list item has an invalid data remainder"
            );

112:         require(
                 itemType == RLPItemType.DATA_ITEM,
                 "RLPReader: decoded item type for bytes is not a data item"
             );

117:         require(
                 _in.length == itemOffset + itemLength,
                 "RLPReader: bytes value contains an invalid remainder"
             );

152:         require(
                 _in.length > 0,
                 "RLPReader: length of an RLP item must be greater than zero to be decodable"
             );

172:             require(
                     _in.length > strLen,
                     "RLPReader: length of content must be greater than string length (short string)"
                 );

182:             require(
                     strLen != 1 || firstByteOfContent >= 0x80,
                     "RLPReader: invalid prefix, single byte < 0x80 are not prefixed (short string)"
                 );

192:             require(
                     _in.length > lenOfStrLen,
                     "RLPReader: length of content must be > than length of string length (long string)"
                 );

202:             require(
                     firstByteOfContent != 0x00,
                     "RLPReader: length of content must not have any leading zeros (long string)"
                 );

212:             require(
                     strLen > 55,
                     "RLPReader: length of content must be greater than 55 bytes (long string)"
                 );

217:             require(
                     _in.length > lenOfStrLen + strLen,
                     "RLPReader: length of content must be greater than total length (long string)"
                 );

228:             require(
                     _in.length > listLen,
                     "RLPReader: length of content must be greater than list length (short list)"
                 );

238:             require(
                     _in.length > lenOfListLen,
                     "RLPReader: length of content must be > than length of list length (long list)"
                 );

248:             require(
                     firstByteOfContent != 0x00,
                     "RLPReader: length of content must not have any leading zeros (long list)"
                 );

258:             require(
                     listLen > 55,
                     "RLPReader: length of content must be greater than 55 bytes (long list)"
                 );

263:             require(
                     _in.length > lenOfListLen + listLen,
                     "RLPReader: length of content must be greater than total length (long list)"
                 );

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/rlp/RLPReader.sol#L263-L266)

```solidity
File: /contracts/thirdparty/optimism/trie/MerkleTrie.sol

89:             require(currentKeyIndex <= key.length, "MerkleTrie: key index exceeds total key length");
    

99:                 require(
                        Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
                        "MerkleTrie: invalid large internal hash"
                    );

105:                 require(
                         Bytes.equal(currentNode.encoded, currentNodeID),
                         "MerkleTrie: invalid internal node hash"
                     );

119:                     require(
                             value_.length > 0,
                             "MerkleTrie: value length must be greater than zero (branch)"
                         );

125:                     require(
                             i == proof.length - 1,
                             "MerkleTrie: value node must be last node in proof (branch)"
                         );

150:                 require(
                         pathRemainder.length == sharedNibbleLength,
                         "MerkleTrie: path remainder must share all nibbles with key"
                     );

162:                     require(
                             keyRemainder.length == sharedNibbleLength,
                             "MerkleTrie: key remainder must be identical to path remainder"
                         );

172:                     require(
                             value_.length > 0,
                             "MerkleTrie: value length must be greater than zero (leaf)"
                         );

178:                     require(
                             i == proof.length - 1,
                             "MerkleTrie: value node must be last node in proof (leaf)"
                         );

191:                     revert("MerkleTrie: received a node with an unknown prefix");
                     }

194:                 revert("MerkleTrie: received an unparseable node");
                 }

198:         revert("MerkleTrie: ran out of proof elements");
         }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/trie/MerkleTrie.sol#L198-L199)

</details>

### <a name="GAS-37-1709385160"></a>[GAS-37] Memory-safe annotation missing
Use `assembly ("memory- safe") { ... }` for the assembly blocks below since they dont't read or modify memory, and therefore are [memory-safe](https://docs.soliditylang.org/en/latest/assembly.html#memory-safety). This will help the optimizer to create more optimal gas-efficient code. Use the comment variant if prior to Solidity version 0.8.13

*Instances (34)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L2/TaikoL2.sol

242:         assembly {
                 publicInputHashOld := keccak256(inputs, 8192 /*mul(256, 32)*/ )
             }

247:         assembly {
                 publicInputHashNew := keccak256(inputs, 8192 /*mul(256, 32)*/ )
             }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/TaikoL2.sol#L247-L249)

```solidity
File: /contracts/automata-attestation/utils/BytesUtils.sol

26:         assembly {
                ret := keccak256(add(add(self, 32), offset), len)
            }

76:         assembly {
                selfptr := add(self, add(offset, 32))
                otherptr := add(other, add(otheroffset, 32))
            }

83:             assembly {
                    a := mload(selfptr)
                    b := mload(otherptr)
                }

200:         assembly {
                 ret := and(mload(add(add(self, 2), idx)), 0xFFFF)
             }

213:         assembly {
                 ret := and(mload(add(add(self, 4), idx)), 0xFFFFFFFF)
             }

226:         assembly {
                 ret := mload(add(add(self, 32), idx))
             }

239:         assembly {
                 ret :=
                     and(
                         mload(add(add(self, 32), idx)),
                         0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF000000000000000000000000
                     )
             }

266:         assembly {
                 let mask := not(sub(exp(256, sub(32, len)), 1))
                 ret := and(mload(add(add(self, 32), idx)), mask)
             }

273:         assembly {
                 mcopy(dest, src, len)
             }

299:         assembly {
                 dest := add(ret, 32)
                 src := add(add(self, 32), offset)
             }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/BytesUtils.sol#L299-L302)

```solidity
File: /contracts/automata-attestation/utils/RsaVerify.sol

99:         assembly {
                pop(
                    staticcall(
                        sub(gas(), 2000),
                        5,
                        add(input, 0x20),
                        inputlen,
                        add(decipher, 0x20),
                        decipherlen
                    )
                )
            }

247:         assembly {
                 pop(
                     staticcall(
                         sub(gas(), 2000),
                         5,
                         add(input, 0x20),
                         inputlen,
                         add(decipher, 0x20),
                         decipherlen
                     )
                 )
             }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/RsaVerify.sol#L247-L258)

```solidity
File: /contracts/automata-attestation/utils/SHA1.sol

12:         assembly {
                // Get a safe scratch location
                let scratch := mload(0x40)
    
                // Get the data length, and point data at the first byte
                let len := mload(data)
                data := add(data, 32)
    
                // Find the length after padding
                let totallen := add(and(add(len, 1), 0xFFFFFFFFFFFFFFC0), 64)
                switch lt(sub(totallen, len), 9)
                case 1 { totallen := add(totallen, 64) }
    
                let h := 0x6745230100EFCDAB890098BADCFE001032547600C3D2E1F0
    
                function readword(ptr, off, count) -> result {
                    result := 0
                    if lt(off, count) {
                        result := mload(add(ptr, off))
                        count := sub(count, off)
                        if lt(count, 32) {
                            let mask := not(sub(exp(256, sub(32, count)), 1))
                            result := and(result, mask)
                        }
                    }
                }
    
                for { let i := 0 } lt(i, totallen) { i := add(i, 64) } {
                    mstore(scratch, readword(data, i, len))
                    mstore(add(scratch, 32), readword(data, add(i, 32), len))
    
                    // If we loaded the last byte, store the terminator byte
                    switch lt(sub(len, i), 64)
                    case 1 { mstore8(add(scratch, sub(len, i)), 0x80) }
    
                    // If this is the last block, store the length
                    switch eq(i, sub(totallen, 64))
                    case 1 { mstore(add(scratch, 32), or(mload(add(scratch, 32)), mul(len, 8))) }
    
                    // Expand the 16 32-bit words into 80
                    for { let j := 64 } lt(j, 128) { j := add(j, 12) } {
                        let temp :=
                            xor(
                                xor(mload(add(scratch, sub(j, 12))), mload(add(scratch, sub(j, 32)))),
                                xor(mload(add(scratch, sub(j, 56))), mload(add(scratch, sub(j, 64))))
                            )
                        temp :=
                            or(
                                and(
                                    mul(temp, 2),
                                    0xFFFFFFFEFFFFFFFEFFFFFFFEFFFFFFFEFFFFFFFEFFFFFFFEFFFFFFFEFFFFFFFE
                                ),
                                and(
                                    div(temp, 0x80000000),
                                    0x0000000100000001000000010000000100000001000000010000000100000001
                                )
                            )
                        mstore(add(scratch, j), temp)
                    }
                    for { let j := 128 } lt(j, 320) { j := add(j, 24) } {
                        let temp :=
                            xor(
                                xor(mload(add(scratch, sub(j, 24))), mload(add(scratch, sub(j, 64)))),
                                xor(mload(add(scratch, sub(j, 112))), mload(add(scratch, sub(j, 128))))
                            )
                        temp :=
                            or(
                                and(
                                    mul(temp, 4),
                                    0xFFFFFFFCFFFFFFFCFFFFFFFCFFFFFFFCFFFFFFFCFFFFFFFCFFFFFFFCFFFFFFFC
                                ),
                                and(
                                    div(temp, 0x40000000),
                                    0x0000000300000003000000030000000300000003000000030000000300000003
                                )
                            )
                        mstore(add(scratch, j), temp)
                    }
    
                    let x := h
                    let f := 0
                    let k := 0
                    for { let j := 0 } lt(j, 80) { j := add(j, 1) } {
                        switch div(j, 20)
                        case 0 {
                            // f = d xor (b and (c xor d))
                            f := xor(div(x, 0x100000000000000000000), div(x, 0x10000000000))
                            f := and(div(x, 0x1000000000000000000000000000000), f)
                            f := xor(div(x, 0x10000000000), f)
                            k := 0x5A827999
                        }
                        case 1 {
                            // f = b xor c xor d
                            f :=
                                xor(
                                    div(x, 0x1000000000000000000000000000000),
                                    div(x, 0x100000000000000000000)
                                )
                            f := xor(div(x, 0x10000000000), f)
                            k := 0x6ED9EBA1
                        }
                        case 2 {
                            // f = (b and c) or (d and (b or c))
                            f :=
                                or(
                                    div(x, 0x1000000000000000000000000000000),
                                    div(x, 0x100000000000000000000)
                                )
                            f := and(div(x, 0x10000000000), f)
                            f :=
                                or(
                                    and(
                                        div(x, 0x1000000000000000000000000000000),
                                        div(x, 0x100000000000000000000)
                                    ),
                                    f
                                )
                            k := 0x8F1BBCDC
                        }
                        case 3 {
                            // f = b xor c xor d
                            f :=
                                xor(
                                    div(x, 0x1000000000000000000000000000000),
                                    div(x, 0x100000000000000000000)
                                )
                            f := xor(div(x, 0x10000000000), f)
                            k := 0xCA62C1D6
                        }
                        // temp = (a leftrotate 5) + f + e + k + w[i]
                        let temp := and(div(x, 0x80000000000000000000000000000000000000000000000), 0x1F)
                        temp :=
                            or(and(div(x, 0x800000000000000000000000000000000000000), 0xFFFFFFE0), temp)
                        temp := add(f, temp)
                        temp := add(and(x, 0xFFFFFFFF), temp)
                        temp := add(k, temp)
                        temp :=
                            add(
                                div(
                                    mload(add(scratch, mul(j, 4))),
                                    0x100000000000000000000000000000000000000000000000000000000
                                ),
                                temp
                            )
                        x :=
                            or(
                                div(x, 0x10000000000),
                                mul(temp, 0x10000000000000000000000000000000000000000)
                            )
                        x :=
                            or(
                                and(x, 0xFFFFFFFF00FFFFFFFF000000000000FFFFFFFF00FFFFFFFF),
                                mul(
                                    or(
                                        and(div(x, 0x4000000000000), 0xC0000000),
                                        and(div(x, 0x400000000000000000000), 0x3FFFFFFF)
                                    ),
                                    0x100000000000000000000
                                )
                            )
                    }
    
                    h := and(add(h, x), 0xFFFFFFFF00FFFFFFFF00FFFFFFFF00FFFFFFFF00FFFFFFFF)
                }
                ret :=
                    mul(
                        or(
                            or(
                                or(
                                    or(
                                        and(div(h, 0x100000000), 0xFFFFFFFF00000000000000000000000000000000),
                                        and(div(h, 0x1000000), 0xFFFFFFFF000000000000000000000000)
                                    ),
                                    and(div(h, 0x10000), 0xFFFFFFFF0000000000000000)
                                ),
                                and(div(h, 0x100), 0xFFFFFFFF00000000)
                            ),
                            and(h, 0xFFFFFFFF)
                        ),
                        0x1000000000000000000000000
                    )
            }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/SHA1.sol#L12-L193)

```solidity
File: /contracts/bridge/Bridge.sol

543:             assembly {
                     tstore(_CTX_SLOT, _msgHash)
                     tstore(add(_CTX_SLOT, 1), _from)
                     tstore(add(_CTX_SLOT, 2), _srcChainId)
                 }

560:             assembly {
                     msgHash := tload(_CTX_SLOT)
                     from := tload(add(_CTX_SLOT, 1))
                     srcChainId := tload(add(_CTX_SLOT, 2))
                 }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L560-L564)

```solidity
File: /contracts/common/EssentialContract.sol

121:             assembly {
                     tstore(_REENTRY_SLOT, _reentry)
                 }

132:             assembly {
                     reentry_ := tload(_REENTRY_SLOT)
                 }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/common/EssentialContract.sol#L132-L134)

```solidity
File: /contracts/libs/Lib4844.sol

53:         assembly {
                first := mload(add(ret, 32))
                second := mload(add(ret, 64))
            }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/libs/Lib4844.sol#L53-L56)

```solidity
File: /contracts/signal/SignalService.sol

265:         assembly {
                 sstore(slot_, _value)
             }

309:         assembly {
                 value_ := sload(slot)
             }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/SignalService.sol#L309-L311)

```solidity
File: /contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol

43:         assembly {
                _success :=
                    call(
                        _gas, // gas
                        _target, // recipient
                        _value, // ether value
                        add(_calldata, 0x20), // inloc
                        mload(_calldata), // inlen
                        0, // outloc
                        0 // outlen
                    )
                // limit our copy to 256 bytes
                _toCopy := returndatasize()
                if gt(_toCopy, _maxCopy) { _toCopy := _maxCopy }
                // Store the length of the copied bytes
                mstore(_returnData, _toCopy)
                // copy the bytes from returndata[0:_toCopy]
                returndatacopy(add(_returnData, 0x20), 0, _toCopy)
            }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L43-L61)

```solidity
File: /contracts/thirdparty/optimism/Bytes.sol

32:         assembly {
                switch iszero(_length)
                case 0 {
                    // Get a location of some free memory and store it in tempBytes as
                    // Solidity does for memory variables.
                    tempBytes := mload(0x40)
    
                    // The first word of the slice result is potentially a partial
                    // word read from the original array. To read it, we calculate
                    // the length of that partial word and start copying that many
                    // bytes into the array. The first word we copy will start with
                    // data we don't care about, but the last `lengthmod` bytes will
                    // land at the beginning of the contents of the new array. When
                    // we're done copying, we overwrite the full first word with
                    // the actual length of the slice.
                    let lengthmod := and(_length, 31)
    
                    // The multiplication in the next line is necessary
                    // because when slicing multiples of 32 bytes (lengthmod == 0)
                    // the following copy loop was copying the origin's length
                    // and then ending prematurely not copying everything it should.
                    let mc := add(add(tempBytes, lengthmod), mul(0x20, iszero(lengthmod)))
                    let end := add(mc, _length)
    
                    for {
                        // The multiplication in the next line has the same exact purpose
                        // as the one above.
                        let cc := add(add(add(_bytes, lengthmod), mul(0x20, iszero(lengthmod))), _start)
                    } lt(mc, end) {
                        mc := add(mc, 0x20)
                        cc := add(cc, 0x20)
                    } { mstore(mc, mload(cc)) }
    
                    mstore(tempBytes, _length)
    
                    //update free-memory pointer
                    //allocating the array padded to 32 bytes like the compiler does now
                    mstore(0x40, and(add(mc, 31), not(31)))
                }
                //if we want a zero-length slice let's just return a zero-length array
                default {
                    tempBytes := mload(0x40)
    
                    //zero out the 32 bytes slice we are about to return
                    //we need to do it because Solidity does not garbage collect
                    mstore(tempBytes, 0)
    
                    mstore(0x40, add(tempBytes, 0x20))
                }
            }

104:         assembly {
                 // Grab a free memory offset for the new array
                 _nibbles := mload(0x40)
     
                 // Load the length of the passed bytes array from memory
                 let bytesLength := mload(_bytes)
     
                 // Calculate the length of the new nibble array
                 // This is the length of the input array times 2
                 let nibblesLength := shl(0x01, bytesLength)
     
                 // Update the free memory pointer to allocate memory for the new array.
                 // To do this, we add the length of the new array + 32 bytes for the array length
                 // rounded up to the nearest 32 byte boundary to the current free memory pointer.
                 mstore(0x40, add(_nibbles, and(not(0x1F), add(nibblesLength, 0x3F))))
     
                 // Store the length of the new array in memory
                 mstore(_nibbles, nibblesLength)
     
                 // Store the memory offset of the _bytes array's contents on the stack
                 let bytesStart := add(_bytes, 0x20)
     
                 // Store the memory offset of the nibbles array's contents on the stack
                 let nibblesStart := add(_nibbles, 0x20)
     
                 // Loop through each byte in the input array
                 for { let i := 0x00 } lt(i, bytesLength) { i := add(i, 0x01) } {
                     // Get the starting offset of the next 2 bytes in the nibbles array
                     let offset := add(nibblesStart, shl(0x01, i))
                     // Load the byte at the current index within the `_bytes` array
                     let b := byte(0x00, mload(add(bytesStart, i)))
     
                     // Pull out the first nibble and store it in the new array
                     mstore8(offset, shr(0x04, b))
                     // Pull out the second nibble and store it in the new array
                     mstore8(add(offset, 0x01), and(b, 0x0F))
                 }
             }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/Bytes.sol#L104-L141)

```solidity
File: /contracts/thirdparty/optimism/rlp/RLPReader.sol

43:         assembly {
                ptr := add(_in, 32)
            }

94:         assembly {
                mstore(out_, itemCount)
            }

159:         assembly {
                 prefix := byte(0, mload(ptr))
             }

178:             assembly {
                     firstByteOfContent := and(mload(add(ptr, 1)), shl(248, 0xff))
                 }

198:             assembly {
                     firstByteOfContent := and(mload(add(ptr, 1)), shl(248, 0xff))
                 }

208:             assembly {
                     strLen := shr(sub(256, mul(8, lenOfStrLen)), mload(add(ptr, 1)))
                 }

244:             assembly {
                     firstByteOfContent := and(mload(add(ptr, 1)), shl(248, 0xff))
                 }

254:             assembly {
                     listLen := shr(sub(256, mul(8, lenOfListLen)), mload(add(ptr, 1)))
                 }

295:         assembly {
                 let dest := add(out_, 32)
                 let i := 0
                 for { } lt(i, _length) { i := add(i, 32) } { mstore(add(dest, i), mload(add(src, i))) }
     
                 if gt(i, _length) { mstore(add(dest, _length), 0) }
             }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/rlp/RLPReader.sol#L295-L301)

</details>

### <a name="GAS-38-1693312508"></a>[GAS-38] Consider merging sequential for loops
Merging multiple `for` loops within a function in Solidity can enhance efficiency and reduce gas costs, especially when they share a common iterating variable or perform related operations. By minimizing redundant iterations over the same data set, execution becomes more cost-effective. However, while merging can optimize gas usage and simplify logic, it may also increase code complexity. Therefore, careful balance between optimization and maintainability is essential, along with thorough testing to ensure the refactored code behaves as expected.

*Instances (6)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/provers/Guardians.sol

74:         for (uint256 i; i < guardians.length; ++i) {
                delete guardianIds[guardians[i]];
            }
            delete guardians;
    
            // Set the new guardians
            for (uint256 i = 0; i < _newGuardians.length; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/provers/Guardians.sol#L74-L80)

```solidity
File: /contracts/automata-attestation/utils/RsaVerify.sol

140:         for (uint256 i = 2; i < 2 + paddingLen; ++i) {
                 if (decipher[i] != 0xff) {
                     return false;
                 }
             }
             if (decipher[2 + paddingLen] != 0) {
                 return false;
             }
     
             // check digest algorithm
     
             if (digestAlgoWithParamLen == sha256ExplicitNullParam.length) {
                 for (uint256 i; i < digestAlgoWithParamLen; ++i) {
                     if (decipher[3 + paddingLen + i] != bytes1(sha256ExplicitNullParam[i])) {
                         return false;
                     }
                 }
             } else {
                 for (uint256 i; i < digestAlgoWithParamLen; ++i) {
                     if (decipher[3 + paddingLen + i] != bytes1(sha256ImplicitNullParam[i])) {
                         return false;
                     }
                 }
             }
     
             // check digest
     
             if (
                 decipher[3 + paddingLen + digestAlgoWithParamLen] != 0x04
                     || decipher[4 + paddingLen + digestAlgoWithParamLen] != 0x20
             ) {
                 return false;
             }
     
             for (uint256 i; i < _sha256.length; ++i) {

273:         for (uint256 i = 2; i < 2 + paddingLen; ++i) {
                 if (decipher[i] != 0xff) {
                     return false;
                 }
             }
             if (decipher[2 + paddingLen] != 0) {
                 return false;
             }
     
             // check digest algorithm
             for (uint256 i; i < sha1Prefix.length; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/RsaVerify.sol#L273-L283)

```solidity
File: /contracts/tokenvault/ERC1155Vault.sol

269:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC1155Vault.sol#L269-L251)

```solidity
File: /contracts/tokenvault/ERC721Vault.sol

175:             for (uint256 i; i < _tokenIds.length; ++i) {

210:                 for (uint256 i; i < _op.tokenIds.length; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC721Vault.sol#L210-L197)

</details>

### <a name="GAS-39-1709377588"></a>[GAS-39] Avoid emitting event on every iteration
Emitting events within a loop can cause significant gas consumption due to repeated I/O operations. Instead, accumulate changes in memory and emit a single event post-loop with aggregated data. This approach improves contract efficiency, reduces gas costs, and simplifies event tracking for event listeners.

*Instances (4)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/libs/LibVerifying.sol

127:             while (blockId < b.numBlocks && numBlocksVerified < _maxBlocksToVerify) {
                     slot = blockId % _config.blockRingBufferSize;
     
                     blk = _state.blocks[slot];
                     if (blk.blockId != blockId) revert L1_BLOCK_MISMATCH();
     
                     tid = LibUtils.getTransitionId(_state, blk, slot, blockHash);
                     // When `tid` is 0, it indicates that there is no proven
                     // transition with its parentHash equal to the blockHash of the
                     // most recently verified block.
                     if (tid == 0) break;
     
                     // A transition with the correct `parentHash` has been located.
                     TaikoData.TransitionState storage ts = _state.transitions[slot][tid];
     
                     // It's not possible to verify this block if either the
                     // transition is contested and awaiting higher-tier proof or if
                     // the transition is still within its cooldown period.
                     if (ts.contester != address(0)) {
                         break;
                     } else {
                         if (tierProvider == address(0)) {
                             tierProvider = _resolver.resolve("tier_provider", false);
                         }
                         if (
                             uint256(ITierProvider(tierProvider).getTier(ts.tier).cooldownWindow) * 60
                                 + uint256(ts.timestamp).max(_state.slotB.lastUnpausedAt) > block.timestamp
                         ) {
                             // If cooldownWindow is 0, the block can theoretically
                             // be proved and verified within the same L1 block.
                             break;
                         }
                     }
     
                     // Mark this block as verified
                     blk.verifiedTransitionId = tid;
     
                     // Update variables
                     blockHash = ts.blockHash;
                     stateRoot = ts.stateRoot;
     
                     // We consistently return the liveness bond and the validity
                     // bond to the actual prover of the transition utilized for
                     // block verification. If the actual prover happens to be the
                     // block's assigned prover, he will receive both deposits,
                     // ultimately earning the proving fee paid during block
                     // proposal. In contrast, if the actual prover is different from
                     // the block's assigned prover, the liveness bond serves as a
                     // reward to the actual prover, while the assigned prover
                     // forfeits his liveness bond due to failure to fulfill their
                     // commitment.
                     uint256 bondToReturn = uint256(ts.validityBond) + blk.livenessBond;
     
                     // Nevertheless, it's possible for the actual prover to be the
                     // same individual or entity as the block's assigned prover.
                     // Consequently, we have chosen to grant the actual prover only
                     // half of the liveness bond as a reward.
                     if (ts.prover != blk.assignedProver) {
                         bondToReturn -= blk.livenessBond >> 1;
                     }
     
                     IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));
                     tko.transfer(ts.prover, bondToReturn);
     
                     // Note: We exclusively address the bonds linked to the
                     // transition used for verification. While there may exist
                     // other transitions for this block, we disregard them entirely.
                     // The bonds for these other transitions are burned either when
                     // the transitions are generated or proven. In such cases, both
                     // the provers and contesters of those transitions forfeit their bonds.
     
                     emit BlockVerified({
                         blockId: blockId,
                         assignedProver: blk.assignedProver,
                         prover: ts.prover,
                         blockHash: blockHash,
                         stateRoot: stateRoot,
                         tier: ts.tier,
                         contestations: ts.contestations
                     });
     
                     ++blockId;
                     ++numBlocksVerified;
                 }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibVerifying.sol#L127-L210)

```solidity
File: /contracts/bridge/Bridge.sol

90:         for (uint256 i; i < _msgHashes.length; ++i) {
                bytes32 msgHash = _msgHashes[i];
                proofReceipt[msgHash].receivedAt = _timestamp;
                emit MessageSuspended(msgHash, _suspend);
            }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L90-L94)

```solidity
File: /contracts/verifiers/SgxVerifier.sol

104:         for (uint256 i; i < _ids.length; ++i) {
                 uint256 idx = _ids[i];
     
                 if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();
     
                 emit InstanceDeleted(idx, instances[idx].addr);
     
                 delete instances[idx];
             }

210:         for (uint256 i; i < _instances.length; ++i) {
                 if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();
     
                 addressRegistered[_instances[i]] = true;
     
                 if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();
     
                 instances[nextInstanceId] = Instance(_instances[i], validSince);
                 ids[i] = nextInstanceId;
     
                 emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);
     
                 nextInstanceId++;
             }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/SgxVerifier.sol#L210-L223)

</details>

### <a name="GAS-40-1702129464"></a>[GAS-40] Refactor modifiers to call a local function
Modifiers code is copied in all instances where it's used, increasing bytecode size. By doing a refractor to the internal function, one can reduce bytecode size significantly at the cost of one JUMP.

*Instances (7)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/common/EssentialContract.sol

41:     modifier onlyFromOwnerOrNamed(bytes32 _name) {
            if (msg.sender != owner() && msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();
            _;
        }

46:     modifier nonReentrant() {
            if (_loadReentryLock() == _TRUE) revert REENTRANT_CALL();
            _storeReentryLock(_TRUE);
            _;
            _storeReentryLock(_FALSE);
        }

53:     modifier whenPaused() {
            if (!paused()) revert INVALID_PAUSE_STATUS();
            _;
        }

58:     modifier whenNotPaused() {
            if (paused()) revert INVALID_PAUSE_STATUS();
            _;
        }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/common/EssentialContract.sol#L58-L61)

```solidity
File: /contracts/team/airdrop/MerkleClaimable.sol

33:     modifier ongoingClaim() {
            if (
                merkleRoot == 0x0 || claimStart == 0 || claimEnd == 0 || claimStart > block.timestamp
                    || claimEnd < block.timestamp
            ) revert CLAIM_NOT_ONGOING();
            _;
        }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/MerkleClaimable.sol#L33-L39)

```solidity
File: /contracts/tokenvault/BaseNFTVault.sol

140:     modifier withValidOperation(BridgeTransferOp memory _op) {
             if (_op.tokenIds.length != _op.amounts.length) {
                 revert VAULT_TOKEN_ARRAY_MISMATCH();
             }
     
             if (_op.tokenIds.length > MAX_TOKEN_PER_TXN) {
                 revert VAULT_MAX_TOKEN_PER_TXN_EXCEEDED();
             }
     
             if (_op.token == address(0)) revert VAULT_INVALID_TOKEN();
             _;
         }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BaseNFTVault.sol#L140-L151)

```solidity
File: /contracts/tokenvault/BaseVault.sol

22:     modifier onlyFromBridge() {
            if (msg.sender != resolve("bridge", false)) {
                revert VAULT_PERMISSION_DENIED();
            }
            _;
        }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BaseVault.sol#L22-L27)

</details>

### <a name="GAS-41-1696084349"></a>[GAS-41] A `modifier` used only once and not being inherited should be inlined to save gas

*Instances (2)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/team/airdrop/ERC20Airdrop2.sol

39:     modifier ongoingWithdrawals() {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC20Airdrop2.sol#L39)

```solidity
File: /contracts/tokenvault/BridgedERC20.sol

37:     modifier onlyOwnerOrSnapshooter() {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC20.sol#L37)

</details>

### <a name="GAS-42-1693312642"></a>[GAS-42] Multiple `address`/ID mappings can be combined into a single `mapping` of an `address`/ID to a `struct`, where appropriate
Saves a storage slot for the mapping. Depending on the circumstances and sizes of types, can avoid a Gsset (**20000 gas**) per mapping combined. Reads and subsequent writes can also be cheaper when a function requires both values and they both fit in the same storage slot. Finally, if both fields are accessed in the same function, can save **~42 gas per access** due to [not having to recalculate the key's keccak256 hash](https://gist.github.com/IllIllI000/ec23a57daa30a8f8ca8b9681c8ccefb0) (Gkeccak256 - 30 gas) and that calculation's associated stack operations.

*Instances (7)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/team/airdrop/ERC20Airdrop2.sol

22:     mapping(address addr => uint256 amountClaimed) public claimedAmount;

25:     mapping(address addr => uint256 amountWithdrawn) public withdrawnAmount;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC20Airdrop2.sol#L25)

```solidity
File: /contracts/tokenvault/BaseNFTVault.sol

56:     mapping(address btoken => CanonicalNFT canonical) public bridgedToCanonical;

59:     mapping(uint256 chainId => mapping(address ctoken => address btoken)) public canonicalToBridged;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BaseNFTVault.sol#L59)

```solidity
File: /contracts/tokenvault/ERC20Vault.sol

45:     mapping(address btoken => CanonicalERC20 canonical) public bridgedToCanonical;

49:     mapping(uint256 chainId => mapping(address ctoken => address btoken)) public canonicalToBridged;

52:     mapping(address btoken => bool blacklisted) public btokenBlacklist;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC20Vault.sol#L52)

</details>

### <a name="GAS-43-1693312655"></a>[GAS-43] Optimize names to save gas
`public`/`external` function names and `public` member variable names can be optimized to save gas. See [this](https://gist.github.com/IllIllI000/a5d8b486a8259f9f77891a919febd1a9) link for an example of how it works. Below are the interfaces/abstract contracts that can be optimized so that the most frequently-called functions use the least amount of gas possible during method lookup. Method IDs that have two leading zero bytes can save **128 gas** each during deployment, and renaming functions to have lower method IDs will save **22 gas** per call, [per sorted position shifted](https://medium.com/joyso/solidity-how-does-function-name-affect-gas-consumption-in-smart-contract-47d270d8ac92)

*Instances (39)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/ITaikoL1.sol

// @audit proposeBlock(bytes,bytes) ==> proposeBlock_KiT(bytes,bytes),000081f1
// @audit proveBlock(uint64,bytes) ==> proveBlock_Tsk(uint64,bytes),0000f8ab
// @audit verifyBlocks(uint64) ==> verifyBlocks_m316(uint64),0000c914
// @audit getConfig() ==> getConfig_tA0(),00002ad1
8: interface ITaikoL1 {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/ITaikoL1.sol#L8)

```solidity
File: /contracts/L1/TaikoL1.sol

// @audit init(address,address,bytes32) ==> init_KeR(address,address,bytes32),000096f3
// @audit pauseProving(bool) ==> pauseProving_A9T(bool),0000ee1c
// @audit depositEtherToL2(address) ==> depositEtherToL2_01G(address),00007a31
// @audit isBlobReusable(bytes32) ==> isBlobReusable_5nC(bytes32),0000236a
// @audit getBlock(uint64) ==> getBlock_c53(uint64),00001071
// @audit getTransition(uint64,bytes32) ==> getTransition_XmI(uint64,bytes32),00005a03
// @audit getStateVariables() ==> getStateVariables_yfF(),000000f8
22: contract TaikoL1 is EssentialContract, ITaikoL1, TaikoEvents, TaikoErrors {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/TaikoL1.sol#L22)

```solidity
File: /contracts/L1/TaikoToken.sol

// @audit init(address,string,string,address) ==> init_F5g(address,string,string,address),0000a5f6
// @audit burn(address,uint256) ==> burn_J8M(address,uint256),0000b783
// @audit snapshot() ==> snapshot_1hD(),0000996a
15: contract TaikoToken is EssentialContract, ERC20SnapshotUpgradeable, ERC20VotesUpgradeable {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/TaikoToken.sol#L15)

```solidity
File: /contracts/L1/gov/TaikoTimelockController.sol

// @audit init(address,uint256) ==> init_In(address,uint256),00004ba4
9: contract TaikoTimelockController is EssentialContract, TimelockControllerUpgradeable {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/gov/TaikoTimelockController.sol#L9)

```solidity
File: /contracts/L1/hooks/AssignmentHook.sol

// @audit init(address,address) ==> init_fcX(address,address),00008091
14: contract AssignmentHook is EssentialContract, IHook {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/hooks/AssignmentHook.sol#L14)

```solidity
File: /contracts/L1/provers/GuardianProver.sol

// @audit init(address,address) ==> init_fcX(address,address),00008091
10: contract GuardianProver is Guardians {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/provers/GuardianProver.sol#L10)

```solidity
File: /contracts/L1/provers/Guardians.sol

// @audit setGuardians(address[],uint8) ==> setGuardians_baN(address[],uint8),0000bb86
// @audit isApproved(bytes32) ==> isApproved_Ooo(bytes32),0000b2b9
// @audit numGuardians() ==> numGuardians_Ofj(),00008e18
9: abstract contract Guardians is EssentialContract {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/provers/Guardians.sol#L9)

```solidity
File: /contracts/L1/tiers/DevnetTierProvider.sol

// @audit init(address) ==> init_ctq(address),0000bf1a
10: contract DevnetTierProvider is EssentialContract, ITierProvider {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/tiers/DevnetTierProvider.sol#L10)

```solidity
File: /contracts/L1/tiers/ITierProvider.sol

// @audit getTier(uint16) ==> getTier_3ri(uint16),00006c43
// @audit getTierIds() ==> getTierIds_wqO(),000085fa
// @audit getMinTier(uint256) ==> getMinTier_52U(uint256),00005fa1
7: interface ITierProvider {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/tiers/ITierProvider.sol#L7)

```solidity
File: /contracts/L1/tiers/MainnetTierProvider.sol

// @audit init(address) ==> init_ctq(address),0000bf1a
10: contract MainnetTierProvider is EssentialContract, ITierProvider {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/tiers/MainnetTierProvider.sol#L10)

```solidity
File: /contracts/L1/tiers/TestnetTierProvider.sol

// @audit init(address) ==> init_ctq(address),0000bf1a
10: contract TestnetTierProvider is EssentialContract, ITierProvider {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/tiers/TestnetTierProvider.sol#L10)

```solidity
File: /contracts/L2/TaikoL2.sol

// @audit init(address,address,uint64,uint64) ==> init_E3x(address,address,uint64,uint64),0000ddbb
// @audit anchor(bytes32,bytes32,uint64,uint32) ==> anchor_rt(bytes32,bytes32,uint64,uint32),0000c412
// @audit withdraw(address,address) ==> withdraw_mNx(address,address),0000d0c8
// @audit getBasefee(uint64,uint32) ==> getBasefee_D6v(uint64,uint32),00000efd
// @audit getBlockHash(uint64) ==> getBlockHash_Nbs(uint64),000003b5
// @audit getConfig() ==> getConfig_tA0(),00002ad1
21: contract TaikoL2 is CrossChainOwned {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/TaikoL2.sol#L21)

```solidity
File: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

// @audit setMrSigner(bytes32,bool) ==> setMrSigner_z4y(bytes32,bool),00006779
// @audit setMrEnclave(bytes32,bool) ==> setMrEnclave_V7m(bytes32,bool),0000a518
// @audit addRevokedCertSerialNum(uint256,bytes[]) ==> addRevokedCertSerialNum_8Gv(uint256,bytes[]),00002a07
// @audit removeRevokedCertSerialNum(uint256,bytes[]) ==> removeRevokedCertSerialNum_1wQ(uint256,bytes[]),000016e0
// @audit toggleLocalReportCheck() ==> toggleLocalReportCheck_Wsf(),0000215e
22: contract AutomataDcapV3Attestation is IAttestation {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/AutomataDcapV3Attestation.sol#L22)

```solidity
File: /contracts/automata-attestation/interfaces/IAttestation.sol

// @audit verifyAttestation(bytes) ==> verifyAttestation_S2L(bytes),000053f8
8: interface IAttestation {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/interfaces/IAttestation.sol#L8)

```solidity
File: /contracts/automata-attestation/interfaces/ISigVerifyLib.sol

// @audit verifyRS256Signature(bytes,bytes,bytes) ==> verifyRS256Signature_t40(bytes,bytes,bytes),00002bdd
// @audit verifyRS1Signature(bytes,bytes,bytes) ==> verifyRS1Signature_Khb(bytes,bytes,bytes),0000c03c
// @audit verifyES256Signature(bytes,bytes,bytes) ==> verifyES256Signature_d6d(bytes,bytes,bytes),00004bcf
6: interface ISigVerifyLib {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L6)

```solidity
File: /contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol

// @audit splitCertificateChain(bytes,uint256) ==> splitCertificateChain_X5a(bytes,uint256),00007f31
// @audit decodeCert(bytes,bool) ==> decodeCert_G9P(bytes,bool),00006a87
6: interface IPEMCertChainLib {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L6)

```solidity
File: /contracts/bridge/Bridge.sol

// @audit init(address,address) ==> init_fcX(address,address),00008091
// @audit suspendMessages(bytes32[],bool) ==> suspendMessages_meq(bytes32[],bool),0000c251
// @audit banAddress(address,bool) ==> banAddress_P3q(address,bool),00006372
// @audit isDestChainEnabled(uint64) ==> isDestChainEnabled_PqO(uint64),00006b5a
// @audit getInvocationDelays() ==> getInvocationDelays_o4F(),0000e7d9
// @audit signalForFailedMessage(bytes32) ==> signalForFailedMessage_T1(bytes32),00009838
16: contract Bridge is EssentialContract, IBridge {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L16)

```solidity
File: /contracts/bridge/IBridge.sol

// @audit context() ==> context_h4s(),0000ae3c
8: interface IBridge {

// @audit onMessageInvocation(bytes) ==> onMessageInvocation_z5(bytes),00009704
174: interface IMessageInvocable {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/IBridge.sol#L174)

```solidity
File: /contracts/common/AddressManager.sol

// @audit init(address) ==> init_ctq(address),0000bf1a
// @audit setAddress(uint64,bytes32,address) ==> setAddress_u1q(uint64,bytes32,address),000001e6
10: contract AddressManager is EssentialContract, IAddressManager {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/common/AddressManager.sol#L10)

```solidity
File: /contracts/common/EssentialContract.sol

// @audit pause() ==> pause_yiS(),00002a4b
// @audit unpause() ==> unpause_88B(),000051b7
// @audit paused() ==> paused_Q3m(),0000a362
10: abstract contract EssentialContract is UUPSUpgradeable, Ownable2StepUpgradeable, AddressResolver {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/common/EssentialContract.sol#L10)

```solidity
File: /contracts/common/IAddressManager.sol

// @audit getAddress(uint64,bytes32) ==> getAddress_6rk(uint64,bytes32),00005a62
7: interface IAddressManager {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/common/IAddressManager.sol#L7)

```solidity
File: /contracts/signal/ISignalService.sol

// @audit sendSignal(bytes32) ==> sendSignal_PHJ(bytes32),00004b6c
// @audit proveSignalReceived(uint64,address,bytes32,bytes) ==> proveSignalReceived_577(uint64,address,bytes32,bytes),000079d5
// @audit isSignalSent(address,bytes32) ==> isSignalSent_Z8p(address,bytes32),0000b7b0
// @audit isChainDataSynced(uint64,bytes32,uint64,bytes32) ==> isChainDataSynced_HyC(uint64,bytes32,uint64,bytes32),00001c90
// @audit getSyncedChainData(uint64,bytes32,uint64) ==> getSyncedChainData_Ikt(uint64,bytes32,uint64),0000686b
// @audit signalForChainData(uint64,bytes32,uint64) ==> signalForChainData_nj9(uint64,bytes32,uint64),00004f35
12: interface ISignalService {

// @audit sendSignal(bytes32) ==> sendSignal_PHJ(bytes32),00004b6c
// @audit proveSignalReceived(uint64,address,bytes32,bytes) ==> proveSignalReceived_577(uint64,address,bytes32,bytes),000079d5
// @audit isSignalSent(address,bytes32) ==> isSignalSent_Z8p(address,bytes32),0000b7b0
// @audit isChainDataSynced(uint64,bytes32,uint64,bytes32) ==> isChainDataSynced_HyC(uint64,bytes32,uint64,bytes32),00001c90
// @audit getSyncedChainData(uint64,bytes32,uint64) ==> getSyncedChainData_Ikt(uint64,bytes32,uint64),0000686b
// @audit signalForChainData(uint64,bytes32,uint64) ==> signalForChainData_nj9(uint64,bytes32,uint64),00004f35
12: interface ISignalService {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/ISignalService.sol#L12)

```solidity
File: /contracts/signal/SignalService.sol

// @audit init(address,address) ==> init_fcX(address,address),00008091
// @audit authorize(address,bool) ==> authorize_4cn(address,bool),00000a30
// @audit getSignalSlot(uint64,address,bytes32) ==> getSignalSlot_u0(uint64,address,bytes32),00006c5e
14: contract SignalService is EssentialContract, ISignalService {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/SignalService.sol#L14)

```solidity
File: /contracts/team/TimelockTokenPool.sol

// @audit init(address,address,address,address) ==> init_X8n(address,address,address,address),000026a5
// @audit void(address) ==> void_x1G(address),00008f48
// @audit withdraw() ==> withdraw_wdp(),0000af32
// @audit withdraw(address,bytes) ==> withdraw_J1F(address,bytes),00008bd9
// @audit getMyGrant(address) ==> getMyGrant_qtE(address),000039f1
25: contract TimelockTokenPool is EssentialContract {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/TimelockTokenPool.sol#L25)

```solidity
File: /contracts/team/airdrop/ERC20Airdrop.sol

// @audit init(address,uint64,uint64,bytes32,address,address) ==> init_81L(address,uint64,uint64,bytes32,address,address),0000de76
// @audit claimAndDelegate(address,uint256,bytes32[],bytes) ==> claimAndDelegate_W1Y(address,uint256,bytes32[],bytes),0000a91c
11: contract ERC20Airdrop is MerkleClaimable {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC20Airdrop.sol#L11)

```solidity
File: /contracts/team/airdrop/ERC20Airdrop2.sol

// @audit init(address,uint64,uint64,bytes32,address,address,uint64) ==> init_Z4E(address,uint64,uint64,bytes32,address,address,uint64),0000e423
// @audit withdraw(address) ==> withdraw_rO7(address),00006cce
// @audit getBalance(address) ==> getBalance_p4s(address),0000b1c8
12: contract ERC20Airdrop2 is MerkleClaimable {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC20Airdrop2.sol#L12)

```solidity
File: /contracts/team/airdrop/ERC721Airdrop.sol

// @audit init(address,uint64,uint64,bytes32,address,address) ==> init_81L(address,uint64,uint64,bytes32,address,address),0000de76
// @audit claim(address,uint256[],bytes32[]) ==> claim_j6D(address,uint256[],bytes32[]),000051f7
9: contract ERC721Airdrop is MerkleClaimable {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC721Airdrop.sol#L9)

```solidity
File: /contracts/team/airdrop/MerkleClaimable.sol

// @audit setConfig(uint64,uint64,bytes32) ==> setConfig_v5m(uint64,uint64,bytes32),0000fa50
10: abstract contract MerkleClaimable is EssentialContract {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/MerkleClaimable.sol#L10)

```solidity
File: /contracts/tokenvault/BaseVault.sol

// @audit init(address,address) ==> init_fcX(address,address),00008091
// @audit name() ==> name_v1V(),00006681
12: abstract contract BaseVault is

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BaseVault.sol#L12)

```solidity
File: /contracts/tokenvault/BridgedERC1155.sol

// @audit init(address,address,address,uint256,string,string) ==> init_zvj(address,address,address,uint256,string,string),0000bfe8
// @audit mint(address,uint256,uint256) ==> mint_k3(address,uint256,uint256),0000b4b0
// @audit mintBatch(address,uint256[],uint256[]) ==> mintBatch_p6G(address,uint256[],uint256[]),0000b318
// @audit burn(address,uint256,uint256) ==> burn_g22(address,uint256,uint256),000040b7
// @audit name() ==> name_v1V(),00006681
// @audit symbol() ==> symbol_km(),000087e0
14: contract BridgedERC1155 is EssentialContract, IERC1155MetadataURIUpgradeable, ERC1155Upgradeable {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC1155.sol#L14)

```solidity
File: /contracts/tokenvault/BridgedERC20.sol

// @audit init(address,address,address,uint256,uint8,string,string) ==> init_Fax(address,address,address,uint256,uint8,string,string),00007500
// @audit setSnapshoter(address) ==> setSnapshoter_DCH(address),00002055
// @audit snapshot() ==> snapshot_1hD(),0000996a
// @audit canonical() ==> canonical_t6R(),0000d721
15: contract BridgedERC20 is

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC20.sol#L15)

```solidity
File: /contracts/tokenvault/BridgedERC721.sol

// @audit init(address,address,address,uint256,string,string) ==> init_zvj(address,address,address,uint256,string,string),0000bfe8
// @audit mint(address,uint256) ==> mint_Qgo(address,uint256),00001784
// @audit burn(address,uint256) ==> burn_J8M(address,uint256),0000b783
// @audit source() ==> source_UpZ(),00005a0f
12: contract BridgedERC721 is EssentialContract, ERC721Upgradeable {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC721.sol#L12)

```solidity
File: /contracts/tokenvault/ERC1155Vault.sol

// @audit name() ==> name_v1V(),00006681
// @audit symbol() ==> symbol_km(),000087e0
16: interface IERC1155NameAndSymbol {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC1155Vault.sol#L16)

```solidity
File: /contracts/tokenvault/IBridgedERC20.sol

// @audit mint(address,uint256) ==> mint_Qgo(address,uint256),00001784
// @audit burn(address,uint256) ==> burn_J8M(address,uint256),0000b783
// @audit changeMigrationStatus(address,bool) ==> changeMigrationStatus_qhf(address,bool),0000c8a1
// @audit owner() ==> owner_ZdW(),000030c3
10: interface IBridgedERC20 {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/IBridgedERC20.sol#L10)

```solidity
File: /contracts/tokenvault/adapters/USDCAdapter.sol

// @audit burn(uint256) ==> burn_HH(uint256),0000fd45
// @audit mint(address,uint256) ==> mint_Qgo(address,uint256),00001784
// @audit transferFrom(address,address,uint256) ==> transferFrom_78S(address,address,uint256),00008711
8: interface IUSDC {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/adapters/USDCAdapter.sol#L8)

```solidity
File: /contracts/verifiers/GuardianVerifier.sol

// @audit init(address,address) ==> init_fcX(address,address),00008091
10: contract GuardianVerifier is EssentialContract, IVerifier {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/GuardianVerifier.sol#L10)

```solidity
File: /contracts/verifiers/SgxVerifier.sol

// @audit init(address,address) ==> init_fcX(address,address),00008091
// @audit addInstances(address[]) ==> addInstances_D2L(address[]),00005b87
// @audit deleteInstances(uint256[]) ==> deleteInstances_ibM(uint256[]),00001a80
19: contract SgxVerifier is EssentialContract, IVerifier {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/SgxVerifier.sol#L19)

</details>

### <a name="GAS-44-1693312684"></a>[GAS-44] Not using the named return variables anywhere in the function wast gas
Consider changing the variable to be an unnamed one, since the variable is never assigned, nor is it returned by name. If the optimizer is not turned on, leaving the code as it is will also waste gas for the stack variable.

*Instances (7)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/libs/LibProving.sol

// @audit maxBlocksToVerify_
91:     function proveBlock(

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProving.sol#L91)

```solidity
File: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

// @audit valid
126:     function _attestationTcbIsValid(TCBInfoStruct.TCBStatus status)

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/AutomataDcapV3Attestation.sol#L126)

```solidity
File: /contracts/automata-attestation/lib/PEMCertChainLib.sol

// @audit success
216:     function _removeHeadersAndFooters(string memory pemData)

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/PEMCertChainLib.sol#L216)

```solidity
File: /contracts/automata-attestation/utils/BytesUtils.sol

// @audit ret
188:     function readUint8(bytes memory self, uint256 idx) internal pure returns (uint8 ret) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/BytesUtils.sol#L188)

```solidity
File: /contracts/automata-attestation/utils/SigVerifyLib.sol

// @audit sigValid
113:     function verifyES256Signature(

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/SigVerifyLib.sol#L113)

```solidity
File: /contracts/bridge/Bridge.sol

// @audit invocationDelay_
// @audit invocationExtraDelay_
417:     function getInvocationDelays()

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L417)

```solidity
File: /contracts/thirdparty/optimism/rlp/RLPReader.sol

// @audit offset_
// @audit length_
// @audit type_
144:     function _decodeLength(RLPItem memory _in)

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/rlp/RLPReader.sol#L144)

</details>

### <a name="GAS-45-1707917994"></a>[GAS-45] Use more recent OpenZeppelin version for gas boost
Every release contains new gas optimizations. Use the latest version to take advantage of this

*Instances (71)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/TaikoToken.sol

4: import "@openzeppelin/contracts-upgradeable/token/ERC20/ERC20Upgradeable.sol";

4: import "@openzeppelin/contracts-upgradeable/token/ERC20/ERC20Upgradeable.sol";

5: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20SnapshotUpgradeable.sol";

5: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20SnapshotUpgradeable.sol";

6: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20VotesUpgradeable.sol";

6: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20VotesUpgradeable.sol";

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/TaikoToken.sol#L6)

```solidity
File: /contracts/L1/gov/TaikoGovernor.sol

4: import "@openzeppelin/contracts-upgradeable/governance/GovernorUpgradeable.sol";

4: import "@openzeppelin/contracts-upgradeable/governance/GovernorUpgradeable.sol";

5: import

5: import

7: import "@openzeppelin/contracts-upgradeable/governance/extensions/GovernorVotesUpgradeable.sol";

7: import "@openzeppelin/contracts-upgradeable/governance/extensions/GovernorVotesUpgradeable.sol";

8: import

8: import

10: import

10: import

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/gov/TaikoGovernor.sol#L10)

```solidity
File: /contracts/L1/gov/TaikoTimelockController.sol

4: import "@openzeppelin/contracts-upgradeable/governance/TimelockControllerUpgradeable.sol";

4: import "@openzeppelin/contracts-upgradeable/governance/TimelockControllerUpgradeable.sol";

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/gov/TaikoTimelockController.sol#L4)

```solidity
File: /contracts/L1/hooks/AssignmentHook.sol

4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

5: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/hooks/AssignmentHook.sol#L5)

```solidity
File: /contracts/L1/libs/LibProposing.sol

4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProposing.sol#L4)

```solidity
File: /contracts/L1/libs/LibProving.sol

4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProving.sol#L4)

```solidity
File: /contracts/L1/libs/LibVerifying.sol

4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibVerifying.sol#L4)

```solidity
File: /contracts/L2/CrossChainOwned.sol

4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/CrossChainOwned.sol#L4)

```solidity
File: /contracts/L2/TaikoL2.sol

4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

5: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/TaikoL2.sol#L5)

```solidity
File: /contracts/bridge/Bridge.sol

4: import "@openzeppelin/contracts/utils/Address.sol";

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L4)

```solidity
File: /contracts/common/EssentialContract.sol

4: import "@openzeppelin/contracts/proxy/utils/UUPSUpgradeable.sol";

5: import "@openzeppelin/contracts-upgradeable/access/Ownable2StepUpgradeable.sol";

5: import "@openzeppelin/contracts-upgradeable/access/Ownable2StepUpgradeable.sol";

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/common/EssentialContract.sol#L5)

```solidity
File: /contracts/libs/LibAddress.sol

4: import "@openzeppelin/contracts/utils/Address.sol";

5: import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol";

6: import "@openzeppelin/contracts/utils/introspection/IERC165.sol";

7: import "@openzeppelin/contracts/interfaces/IERC1271.sol";

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/libs/LibAddress.sol#L7)

```solidity
File: /contracts/signal/SignalService.sol

4: import "@openzeppelin/contracts/utils/math/SafeCast.sol";

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/SignalService.sol#L4)

```solidity
File: /contracts/team/TimelockTokenPool.sol

4: import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol";

5: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

6: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/TimelockTokenPool.sol#L6)

```solidity
File: /contracts/team/airdrop/ERC20Airdrop.sol

4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

5: import "@openzeppelin/contracts/governance/utils/IVotes.sol";

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC20Airdrop.sol#L5)

```solidity
File: /contracts/team/airdrop/ERC20Airdrop2.sol

4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC20Airdrop2.sol#L4)

```solidity
File: /contracts/team/airdrop/ERC721Airdrop.sol

4: import "@openzeppelin/contracts/token/ERC721/IERC721.sol";

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC721Airdrop.sol#L4)

```solidity
File: /contracts/team/airdrop/MerkleClaimable.sol

4: import "@openzeppelin/contracts/utils/cryptography/MerkleProof.sol";

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/MerkleClaimable.sol#L4)

```solidity
File: /contracts/tokenvault/BaseVault.sol

4: import "@openzeppelin/contracts-upgradeable/utils/introspection/IERC165Upgradeable.sol";

4: import "@openzeppelin/contracts-upgradeable/utils/introspection/IERC165Upgradeable.sol";

5: import "@openzeppelin/contracts/proxy/ERC1967/ERC1967Proxy.sol";

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BaseVault.sol#L5)

```solidity
File: /contracts/tokenvault/BridgedERC1155.sol

4: import "@openzeppelin/contracts/utils/Strings.sol";

5: import "@openzeppelin/contracts-upgradeable/token/ERC1155/ERC1155Upgradeable.sol";

5: import "@openzeppelin/contracts-upgradeable/token/ERC1155/ERC1155Upgradeable.sol";

6: import

6: import

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC1155.sol#L6)

```solidity
File: /contracts/tokenvault/BridgedERC20.sol

4: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/IERC20MetadataUpgradeable.sol";

4: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/IERC20MetadataUpgradeable.sol";

5: import "@openzeppelin/contracts/utils/Strings.sol";

6: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20SnapshotUpgradeable.sol";

6: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20SnapshotUpgradeable.sol";

7: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20VotesUpgradeable.sol";

7: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20VotesUpgradeable.sol";

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC20.sol#L7)

```solidity
File: /contracts/tokenvault/BridgedERC721.sol

4: import "@openzeppelin/contracts-upgradeable/token/ERC721/ERC721Upgradeable.sol";

4: import "@openzeppelin/contracts-upgradeable/token/ERC721/ERC721Upgradeable.sol";

5: import "@openzeppelin/contracts/utils/Strings.sol";

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC721.sol#L5)

```solidity
File: /contracts/tokenvault/ERC1155Vault.sol

4: import "@openzeppelin/contracts/token/ERC1155/IERC1155.sol";

5: import "@openzeppelin/contracts-upgradeable/token/ERC1155/utils/ERC1155ReceiverUpgradeable.sol";

5: import "@openzeppelin/contracts-upgradeable/token/ERC1155/utils/ERC1155ReceiverUpgradeable.sol";

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC1155Vault.sol#L5)

```solidity
File: /contracts/tokenvault/ERC20Vault.sol

4: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

5: import "@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol";

6: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC20Vault.sol#L6)

```solidity
File: /contracts/tokenvault/ERC721Vault.sol

4: import "@openzeppelin/contracts/token/ERC721/IERC721.sol";

5: import "@openzeppelin/contracts/token/ERC721/IERC721Receiver.sol";

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC721Vault.sol#L5)

```solidity
File: /contracts/tokenvault/LibBridgedToken.sol

4: import "@openzeppelin/contracts/utils/Strings.sol";

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/LibBridgedToken.sol#L4)

```solidity
File: /contracts/verifiers/SgxVerifier.sol

4: import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol";

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/SgxVerifier.sol#L4)

</details>

### <a name="GAS-46-1694875070"></a>[GAS-46] State variables can be packed into fewer storage slots
If variables occupying the same slot are both written the same function or by the constructor, avoids a separate Gsset (**20000 gas**). Reads of the variables can also be cheaper

*Instances (5)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

// @audit from 6 to 5 you need to change the structure elements order to: , mapping, mapping, mapping, mapping, address, bool, ISigVerifyLib, EnclaveIdStruct.EnclaveId, IPEMCertChainLib
22: contract AutomataDcapV3Attestation is IAttestation {
        using BytesUtils for bytes;
    
        ISigVerifyLib public immutable sigVerifyLib;
        IPEMCertChainLib public immutable pemCertLib;
    
        // https://github.com/intel/SGXDataCenterAttestationPrimitives/blob/e7604e02331b3377f3766ed3653250e03af72d45/QuoteVerification/QVL/Src/AttestationLibrary/src/CertVerification/X509Constants.h#L64
        uint256 internal constant CPUSVN_LENGTH = 16;
    
        // keccak256(hex"0ba9c4c0c0c86193a3fe23d6b02cda10a8bbd4e88e48b4458561a36e705525f567918e2edc88e40d860bd0cc4ee26aacc988e505a953558c453f6b0904ae7394")
        // the uncompressed (0x04) prefix is not included in the pubkey pre-image
        bytes32 internal constant ROOTCA_PUBKEY_HASH =
            0x89f72d7c488e5b53a77c23ebcb36970ef7eb5bcf6658e9b8292cfbe4703a8473;
    
        uint8 internal constant INVALID_EXIT_CODE = 255;
    
        bool private _checkLocalEnclaveReport;
        mapping(bytes32 enclave => bool trusted) private _trustedUserMrEnclave;
        mapping(bytes32 signer => bool trusted) private _trustedUserMrSigner;
    
        // Quote Collateral Configuration
    
        // Index definition:
        // 0 = Quote PCKCrl
        // 1 = RootCrl
        mapping(uint256 idx => mapping(bytes serialNum => bool revoked)) private _serialNumIsRevoked;
        // fmspc => tcbInfo
        mapping(string fmspc => TCBInfoStruct.TCBInfo tcbInfo) public tcbInfo;
        EnclaveIdStruct.EnclaveId public qeIdentity;
    
        address public owner;
    
        constructor(address sigVerifyLibAddr, address pemCertLibAddr) {
            sigVerifyLib = ISigVerifyLib(sigVerifyLibAddr);
            pemCertLib = PEMCertChainLib(pemCertLibAddr);
            owner = msg.sender;
        }
    
        modifier onlyOwner() {
            require(msg.sender == owner, "onlyOwner");
            _;
        }
    
        function setMrSigner(bytes32 _mrSigner, bool _trusted) external onlyOwner {
            _trustedUserMrSigner[_mrSigner] = _trusted;
        }
    
        function setMrEnclave(bytes32 _mrEnclave, bool _trusted) external onlyOwner {
            _trustedUserMrEnclave[_mrEnclave] = _trusted;
        }
    
        function addRevokedCertSerialNum(
            uint256 index,
            bytes[] calldata serialNumBatch
        )
            external
            onlyOwner
        {
            for (uint256 i; i < serialNumBatch.length; ++i) {
                if (_serialNumIsRevoked[index][serialNumBatch[i]]) {
                    continue;
                }
                _serialNumIsRevoked[index][serialNumBatch[i]] = true;
            }
        }
    
        function removeRevokedCertSerialNum(
            uint256 index,
            bytes[] calldata serialNumBatch
        )
            external
            onlyOwner
        {
            for (uint256 i; i < serialNumBatch.length; ++i) {
                if (!_serialNumIsRevoked[index][serialNumBatch[i]]) {
                    continue;
                }
                delete _serialNumIsRevoked[index][serialNumBatch[i]];
            }
        }
    
        function configureTcbInfoJson(
            string calldata fmspc,
            TCBInfoStruct.TCBInfo calldata tcbInfoInput
        )
            public
            onlyOwner
        {
            // 2.2M gas
            tcbInfo[fmspc] = tcbInfoInput;
        }
    
        function configureQeIdentityJson(EnclaveIdStruct.EnclaveId calldata qeIdentityInput)
            external
            onlyOwner
        {
            // 250k gas
            qeIdentity = qeIdentityInput;
        }
    
        function toggleLocalReportCheck() external onlyOwner {
            _checkLocalEnclaveReport = !_checkLocalEnclaveReport;
        }
    
        function _attestationTcbIsValid(TCBInfoStruct.TCBStatus status)
            internal
            pure
            virtual
            returns (bool valid)
        {
            return status == TCBInfoStruct.TCBStatus.OK
                || status == TCBInfoStruct.TCBStatus.TCB_SW_HARDENING_NEEDED
                || status == TCBInfoStruct.TCBStatus.TCB_CONFIGURATION_AND_SW_HARDENING_NEEDED
                || status == TCBInfoStruct.TCBStatus.TCB_OUT_OF_DATE_CONFIGURATION_NEEDED;
        }
    
        function verifyAttestation(bytes calldata data) external view override returns (bool) {
            (bool success,) = _verify(data);
            return success;
        }
    
        /// @dev Provide the raw quote binary as input
        /// @dev The attestation data (or the returned data of this method)
        /// is constructed depending on the validity of the quote verification.
        /// @dev After confirming that a quote has been verified, the attestation's validity then
        /// depends on the
        /// status of the associated TCB.
        /// @dev Example scenarios as below:
        /// --------------------------------
        /// @dev Invalid quote verification: returns (false, INVALID_EXIT_CODE)
        ///
        /// @dev For all valid quote verification, the validity of the attestation depends on the status
        /// of a
        /// matching TCBInfo and this is defined in the _attestationTcbIsValid() method, which can be
        /// overwritten
        /// in derived contracts. (Except for "Revoked" status, which also returns (false,
        /// INVALID_EXIT_CODE) value)
        /// @dev For all valid quote verification, returns the following data:
        /// (_attestationTcbIsValid(), abi.encodePacked(sha256(quote), uint8 exitCode))
        /// @dev exitCode is defined in the {{ TCBInfoStruct.TCBStatus }} enum
        function _verify(bytes calldata quote) private view returns (bool, bytes memory) {
            bytes memory retData = abi.encodePacked(INVALID_EXIT_CODE);
    
            // Step 1: Parse the quote input = 152k gas
            (bool successful, V3Struct.ParsedV3QuoteStruct memory parsedV3Quote) =
                V3Parser.parseInput(quote, address(pemCertLib));
            if (!successful) {
                return (false, retData);
            }
    
            return _verifyParsedQuote(parsedV3Quote);
        }
    
        function _verifyQEReportWithIdentity(V3Struct.EnclaveReport memory quoteEnclaveReport)
            private
            view
            returns (bool, EnclaveIdStruct.EnclaveIdStatus status)
        {
            EnclaveIdStruct.EnclaveId memory enclaveId = qeIdentity;
            bool miscselectMatched =
                quoteEnclaveReport.miscSelect & enclaveId.miscselectMask == enclaveId.miscselect;
    
            bool attributesMatched =
                quoteEnclaveReport.attributes & enclaveId.attributesMask == enclaveId.attributes;
            bool mrsignerMatched = quoteEnclaveReport.mrSigner == enclaveId.mrsigner;
    
            bool isvprodidMatched = quoteEnclaveReport.isvProdId == enclaveId.isvprodid;
    
            bool tcbFound;
            for (uint256 i; i < enclaveId.tcbLevels.length; ++i) {
                EnclaveIdStruct.TcbLevel memory tcb = enclaveId.tcbLevels[i];
                if (tcb.tcb.isvsvn <= quoteEnclaveReport.isvSvn) {
                    tcbFound = true;
                    status = tcb.tcbStatus;
                    break;
                }
            }
            return (
                miscselectMatched && attributesMatched && mrsignerMatched && isvprodidMatched
                    && tcbFound,
                status
            );
        }
    
        function _checkTcbLevels(
            IPEMCertChainLib.PCKCertificateField memory pck,
            TCBInfoStruct.TCBInfo memory tcb
        )
            private
            pure
            returns (bool, TCBInfoStruct.TCBStatus status)
        {
            for (uint256 i; i < tcb.tcbLevels.length; ++i) {
                TCBInfoStruct.TCBLevelObj memory current = tcb.tcbLevels[i];
                bool pceSvnIsHigherOrGreater = pck.sgxExtension.pcesvn >= current.pcesvn;
                bool cpuSvnsAreHigherOrGreater = _isCpuSvnHigherOrGreater(
                    pck.sgxExtension.sgxTcbCompSvnArr, current.sgxTcbCompSvnArr
                );
                if (pceSvnIsHigherOrGreater && cpuSvnsAreHigherOrGreater) {
                    status = current.status;
                    bool tcbIsRevoked = status == TCBInfoStruct.TCBStatus.TCB_REVOKED;
                    return (!tcbIsRevoked, status);
                }
            }
            return (true, TCBInfoStruct.TCBStatus.TCB_UNRECOGNIZED);
        }
    
        function _isCpuSvnHigherOrGreater(
            uint256[] memory pckCpuSvns,
            uint8[] memory tcbCpuSvns
        )
            private
            pure
            returns (bool)
        {
            if (pckCpuSvns.length != CPUSVN_LENGTH || tcbCpuSvns.length != CPUSVN_LENGTH) {
                return false;
            }
            for (uint256 i; i < CPUSVN_LENGTH; ++i) {
                if (pckCpuSvns[i] < tcbCpuSvns[i]) {
                    return false;
                }
            }
            return true;
        }
    
        function _verifyCertChain(IPEMCertChainLib.ECSha256Certificate[] memory certs)
            private
            view
            returns (bool)
        {
            uint256 n = certs.length;
            bool certRevoked;
            bool certNotExpired;
            bool verified;
            bool certChainCanBeTrusted;
    
            for (uint256 i; i < n; ++i) {
                IPEMCertChainLib.ECSha256Certificate memory issuer;
                if (i == n - 1) {
                    // rootCA
                    issuer = certs[i];
                } else {
                    issuer = certs[i + 1];
                    if (i == n - 2) {
                        // this cert is expected to be signed by the root
                        certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.ROOT)][certs[i]
                            .serialNumber];
                    } else if (certs[i].isPck) {
                        certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.PCK)][certs[i]
                            .serialNumber];
                    }
                    if (certRevoked) {
                        break;
                    }
                }
    
                certNotExpired =
                    block.timestamp > certs[i].notBefore && block.timestamp < certs[i].notAfter;
                if (!certNotExpired) {
                    break;
                }
    
                verified = sigVerifyLib.verifyES256Signature(
                    certs[i].tbsCertificate, certs[i].signature, issuer.pubKey
                );
                if (!verified) {
                    break;
                }
    
                bytes32 issuerPubKeyHash = keccak256(issuer.pubKey);
    
                if (issuerPubKeyHash == ROOTCA_PUBKEY_HASH) {
                    certChainCanBeTrusted = true;
                    break;
                }
            }
    
            return !certRevoked && certNotExpired && verified && certChainCanBeTrusted;
        }
    
        function _enclaveReportSigVerification(
            bytes memory pckCertPubKey,
            bytes memory signedQuoteData,
            V3Struct.ECDSAQuoteV3AuthData memory authDataV3,
            V3Struct.EnclaveReport memory qeEnclaveReport
        )
            private
            view
            returns (bool)
        {
            bytes32 expectedAuthDataHash = bytes32(qeEnclaveReport.reportData.substring(0, 32));
            bytes memory concatOfAttestKeyAndQeAuthData =
                abi.encodePacked(authDataV3.ecdsaAttestationKey, authDataV3.qeAuthData.data);
            bytes32 computedAuthDataHash = sha256(concatOfAttestKeyAndQeAuthData);
    
            bool qeReportDataIsValid = expectedAuthDataHash == computedAuthDataHash;
            if (qeReportDataIsValid) {
                bytes memory pckSignedQeReportBytes =
                    V3Parser.packQEReport(authDataV3.pckSignedQeReport);
                bool qeSigVerified = sigVerifyLib.verifyES256Signature(
                    pckSignedQeReportBytes, authDataV3.qeReportSignature, pckCertPubKey
                );
                bool quoteSigVerified = sigVerifyLib.verifyES256Signature(
                    signedQuoteData, authDataV3.ecdsa256BitSignature, authDataV3.ecdsaAttestationKey
                );
                return qeSigVerified && quoteSigVerified;
            } else {
                return false;
            }
        }
    
        /// --------------- validate parsed quote ---------------
    
        /// @dev Provide the parsed quote binary as input
        /// @dev The attestation data (or the returned data of this method)
        /// is constructed depending on the validity of the quote verification.
        /// @dev After confirming that a quote has been verified, the attestation's validity then
        /// depends on the
        /// status of the associated TCB.
        /// @dev Example scenarios as below:
        /// --------------------------------
        /// @dev Invalid quote verification: returns (false, INVALID_EXIT_CODE)
        ///
        /// @dev For all valid quote verification, the validity of the attestation depends on the status
        /// of a
        /// matching TCBInfo and this is defined in the _attestationTcbIsValid() method, which can be
        /// overwritten
        /// in derived contracts. (Except for "Revoked" status, which also returns (false,
        /// INVALID_EXIT_CODE) value)
        /// @dev For all valid quote verification, returns the following data:
        /// (_attestationTcbIsValid())
        /// @dev exitCode is defined in the {{ TCBInfoStruct.TCBStatus }} enum
        function verifyParsedQuote(V3Struct.ParsedV3QuoteStruct calldata v3quote)
            external
            view
            override
            returns (bool, bytes memory)
        {
            return _verifyParsedQuote(v3quote);
        }
    
        function _verifyParsedQuote(V3Struct.ParsedV3QuoteStruct memory v3quote)
            internal
            view
            returns (bool, bytes memory)
        {
            bytes memory retData = abi.encodePacked(INVALID_EXIT_CODE);
    
            // // Step 1: Parse the quote input = 152k gas
            (
                bool successful,
                ,
                ,
                bytes memory signedQuoteData,
                V3Struct.ECDSAQuoteV3AuthData memory authDataV3
            ) = V3Parser.validateParsedInput(v3quote);
            if (!successful) {
                return (false, retData);
            }
    
            // Step 2: Verify application enclave report MRENCLAVE and MRSIGNER
            {
                if (_checkLocalEnclaveReport) {
                    // 4k gas
                    bool mrEnclaveIsTrusted =
                        _trustedUserMrEnclave[v3quote.localEnclaveReport.mrEnclave];
                    bool mrSignerIsTrusted = _trustedUserMrSigner[v3quote.localEnclaveReport.mrSigner];
    
                    if (!mrEnclaveIsTrusted || !mrSignerIsTrusted) {
                        return (false, retData);
                    }
                }
            }
    
            // Step 3: Verify enclave identity = 43k gas
            EnclaveIdStruct.EnclaveIdStatus qeTcbStatus;
            {
                bool verifiedEnclaveIdSuccessfully;
                (verifiedEnclaveIdSuccessfully, qeTcbStatus) =
                    _verifyQEReportWithIdentity(v3quote.v3AuthData.pckSignedQeReport);
                if (!verifiedEnclaveIdSuccessfully) {
                    return (false, retData);
                }
                if (
                    !verifiedEnclaveIdSuccessfully
                        || qeTcbStatus == EnclaveIdStruct.EnclaveIdStatus.SGX_ENCLAVE_REPORT_ISVSVN_REVOKED
                ) {
                    return (false, retData);
                }
            }
    
            // Step 4: Parse Quote CertChain
            IPEMCertChainLib.ECSha256Certificate[] memory parsedQuoteCerts;
            TCBInfoStruct.TCBInfo memory fetchedTcbInfo;
            {
                // 536k gas
                parsedQuoteCerts = new IPEMCertChainLib.ECSha256Certificate[](3);
                for (uint256 i; i < 3; ++i) {
                    bool isPckCert = i == 0; // additional parsing for PCKCert
                    bool certDecodedSuccessfully;
                    // todo! move decodeCert offchain
                    (certDecodedSuccessfully, parsedQuoteCerts[i]) = pemCertLib.decodeCert(
                        authDataV3.certification.decodedCertDataArray[i], isPckCert
                    );
                    if (!certDecodedSuccessfully) {
                        return (false, retData);
                    }
                }
            }
    
            // Step 5: basic PCK and TCB check = 381k gas
            {
                string memory parsedFmspc = parsedQuoteCerts[0].pck.sgxExtension.fmspc;
                fetchedTcbInfo = tcbInfo[parsedFmspc];
                bool tcbConfigured = LibString.eq(parsedFmspc, fetchedTcbInfo.fmspc);
                if (!tcbConfigured) {
                    return (false, retData);
                }
    
                IPEMCertChainLib.ECSha256Certificate memory pckCert = parsedQuoteCerts[0];
                bool pceidMatched = LibString.eq(pckCert.pck.sgxExtension.pceid, fetchedTcbInfo.pceid);
                if (!pceidMatched) {
                    return (false, retData);
                }
            }
    
            // Step 6: Verify TCB Level
            TCBInfoStruct.TCBStatus tcbStatus;
            {
                // 4k gas
                bool tcbVerified;
                (tcbVerified, tcbStatus) = _checkTcbLevels(parsedQuoteCerts[0].pck, fetchedTcbInfo);
                if (!tcbVerified) {
                    return (false, retData);
                }
            }
    
            // Step 7: Verify cert chain for PCK
            {
                // 660k gas (rootCA pubkey is trusted)
                bool pckCertChainVerified = _verifyCertChain(parsedQuoteCerts);
                if (!pckCertChainVerified) {
                    return (false, retData);
                }
            }
    
            // Step 8: Verify the local attestation sig and qe report sig = 670k gas
            {
                bool enclaveReportSigsVerified = _enclaveReportSigVerification(
                    parsedQuoteCerts[0].pubKey,
                    signedQuoteData,
                    authDataV3,
                    v3quote.v3AuthData.pckSignedQeReport
                );
                if (!enclaveReportSigsVerified) {
                    return (false, retData);
                }
            }
    
            retData = abi.encodePacked(sha256(abi.encode(v3quote)), tcbStatus);
    
            return (_attestationTcbIsValid(tcbStatus), retData);
        }
    }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/AutomataDcapV3Attestation.sol#L22-L486)

```solidity
File: /contracts/bridge/Bridge.sol

// @audit from 5 to 4 you need to change the structure elements order to: , mapping, mapping, mapping, uint128, Context, array
16: contract Bridge is EssentialContract, IBridge {
        using Address for address;
        using LibAddress for address;
        using LibAddress for address payable;
    
        /// @dev The slot in transient storage of the call context. This is the keccak256 hash
        /// of "bridge.ctx_slot"
        bytes32 private constant _CTX_SLOT =
            0xe4ece82196de19aabe639620d7f716c433d1348f96ce727c9989a982dbadc2b9;
    
        /// @dev Place holder value when not using transient storage
        uint256 internal constant PLACEHOLDER = type(uint256).max;
    
        /// @notice The next message ID.
        /// @dev Slot 1.
        uint128 public nextMessageId;
    
        /// @notice Mapping to store the status of a message from its hash.
        /// @dev Slot 2.
        mapping(bytes32 msgHash => Status status) public messageStatus;
    
        /// @dev Slots 3, 4, and 5.
        Context private __ctx;
    
        /// @notice Mapping to store banned addresses.
        /// @dev Slot 6.
        mapping(address addr => bool banned) public addressBanned;
    
        /// @notice Mapping to store the proof receipt of a message from its hash.
        /// @dev Slot 7.
        mapping(bytes32 msgHash => ProofReceipt receipt) public proofReceipt;
    
        uint256[43] private __gap;
    
        error B_INVALID_CHAINID();
        error B_INVALID_CONTEXT();
        error B_INVALID_GAS_LIMIT();
        error B_INVALID_STATUS();
        error B_INVALID_USER();
        error B_INVALID_VALUE();
        error B_MESSAGE_NOT_SENT();
        error B_NON_RETRIABLE();
        error B_NOT_FAILED();
        error B_NOT_RECEIVED();
        error B_PERMISSION_DENIED();
        error B_STATUS_MISMATCH();
        error B_INVOCATION_TOO_EARLY();
    
        modifier sameChain(uint64 _chainId) {
            if (_chainId != block.chainid) revert B_INVALID_CHAINID();
            _;
        }
    
        /// @notice Function to receive Ether.
        receive() external payable { }
    
        /// @notice Initializes the contract.
        /// @param _owner The owner of this contract. msg.sender will be used if this value is zero.
        /// @param _addressManager The address of the {AddressManager} contract.
        function init(address _owner, address _addressManager) external initializer {
            __Essential_init(_owner, _addressManager);
        }
    
        /// @notice Suspend or unsuspend invocation for a list of messages.
        /// @param _msgHashes The array of msgHashes to be suspended.
        /// @param _suspend True if suspend, false if unsuspend.
        function suspendMessages(
            bytes32[] calldata _msgHashes,
            bool _suspend
        )
            external
            onlyFromOwnerOrNamed("bridge_watchdog")
        {
            uint64 _timestamp = _suspend ? type(uint64).max : uint64(block.timestamp);
            for (uint256 i; i < _msgHashes.length; ++i) {
                bytes32 msgHash = _msgHashes[i];
                proofReceipt[msgHash].receivedAt = _timestamp;
                emit MessageSuspended(msgHash, _suspend);
            }
        }
    
        /// @notice Ban or unban an address. A banned addresses will not be invoked upon
        /// with message calls.
        /// @param _addr The address to ban or unban.
        /// @param _ban True if ban, false if unban.
        function banAddress(
            address _addr,
            bool _ban
        )
            external
            onlyFromOwnerOrNamed("bridge_watchdog")
            nonReentrant
        {
            if (addressBanned[_addr] == _ban) revert B_INVALID_STATUS();
            addressBanned[_addr] = _ban;
            emit AddressBanned(_addr, _ban);
        }
    
        /// @inheritdoc IBridge
        function sendMessage(Message calldata _message)
            external
            payable
            override
            nonReentrant
            whenNotPaused
            returns (bytes32 msgHash_, Message memory message_)
        {
            // Ensure the message owner is not null.
            if (_message.srcOwner == address(0) || _message.destOwner == address(0)) {
                revert B_INVALID_USER();
            }
    
            // Check if the destination chain is enabled.
            (bool destChainEnabled,) = isDestChainEnabled(_message.destChainId);
    
            // Verify destination chain and to address.
            if (!destChainEnabled) revert B_INVALID_CHAINID();
            if (_message.destChainId == block.chainid) {
                revert B_INVALID_CHAINID();
            }
    
            // Ensure the sent value matches the expected amount.
            uint256 expectedAmount = _message.value + _message.fee;
            if (expectedAmount != msg.value) revert B_INVALID_VALUE();
    
            message_ = _message;
    
            // Configure message details and send signal to indicate message sending.
            message_.id = nextMessageId++;
            message_.from = msg.sender;
            message_.srcChainId = uint64(block.chainid);
    
            msgHash_ = hashMessage(message_);
    
            ISignalService(resolve("signal_service", false)).sendSignal(msgHash_);
            emit MessageSent(msgHash_, message_);
        }
    
        /// @inheritdoc IBridge
        function recallMessage(
            Message calldata _message,
            bytes calldata _proof
        )
            external
            nonReentrant
            whenNotPaused
            sameChain(_message.srcChainId)
        {
            bytes32 msgHash = hashMessage(_message);
    
            if (messageStatus[msgHash] != Status.NEW) revert B_STATUS_MISMATCH();
    
            uint64 receivedAt = proofReceipt[msgHash].receivedAt;
            bool isMessageProven = receivedAt != 0;
    
            if (!isMessageProven) {
                address signalService = resolve("signal_service", false);
    
                if (!ISignalService(signalService).isSignalSent(address(this), msgHash)) {
                    revert B_MESSAGE_NOT_SENT();
                }
    
                bytes32 failureSignal = signalForFailedMessage(msgHash);
                if (!_proveSignalReceived(signalService, failureSignal, _message.destChainId, _proof)) {
                    revert B_NOT_FAILED();
                }
    
                receivedAt = uint64(block.timestamp);
                proofReceipt[msgHash].receivedAt = receivedAt;
            }
    
            (uint256 invocationDelay,) = getInvocationDelays();
    
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
                emit MessageRecalled(msgHash);
            } else if (!isMessageProven) {
                emit MessageReceived(msgHash, _message, true);
            } else {
                revert B_INVOCATION_TOO_EARLY();
            }
        }
    
        /// @inheritdoc IBridge
        function processMessage(
            Message calldata _message,
            bytes calldata _proof
        )
            external
            nonReentrant
            whenNotPaused
            sameChain(_message.destChainId)
        {
            bytes32 msgHash = hashMessage(_message);
            if (messageStatus[msgHash] != Status.NEW) revert B_STATUS_MISMATCH();
    
            address signalService = resolve("signal_service", false);
            uint64 receivedAt = proofReceipt[msgHash].receivedAt;
            bool isMessageProven = receivedAt != 0;
    
            (uint256 invocationDelay, uint256 invocationExtraDelay) = getInvocationDelays();
    
            if (!isMessageProven) {
                if (!_proveSignalReceived(signalService, msgHash, _message.srcChainId, _proof)) {
                    revert B_NOT_RECEIVED();
                }
    
                receivedAt = uint64(block.timestamp);
    
                if (invocationDelay != 0) {
                    proofReceipt[msgHash] = ProofReceipt({
                        receivedAt: receivedAt,
                        preferredExecutor: _message.gasLimit == 0 ? _message.destOwner : msg.sender
                    });
                }
            }
    
            if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) {
                // If msg.sender is not the one that proved the message, then there
                // is an extra delay.
                unchecked {
                    invocationDelay += invocationExtraDelay;
                }
            }
    
            if (block.timestamp >= invocationDelay + receivedAt) {
                // If the gas limit is set to zero, only the owner can process the message.
                if (_message.gasLimit == 0 && msg.sender != _message.destOwner) {
                    revert B_PERMISSION_DENIED();
                }
    
                delete proofReceipt[msgHash];
    
                uint256 refundAmount;
    
                // Process message differently based on the target address
                if (
                    _message.to == address(0) || _message.to == address(this)
                        || _message.to == signalService || addressBanned[_message.to]
                ) {
                    // Handle special addresses that don't require actual invocation but
                    // mark message as DONE
                    refundAmount = _message.value;
                    _updateMessageStatus(msgHash, Status.DONE);
                } else {
                    // Use the specified message gas limit if called by the owner, else
                    // use remaining gas
                    uint256 gasLimit = msg.sender == _message.destOwner ? gasleft() : _message.gasLimit;
    
                    if (_invokeMessageCall(_message, msgHash, gasLimit)) {
                        _updateMessageStatus(msgHash, Status.DONE);
                    } else {
                        _updateMessageStatus(msgHash, Status.RETRIABLE);
                    }
                }
    
                // Determine the refund recipient
                address refundTo =
                    _message.refundTo == address(0) ? _message.destOwner : _message.refundTo;
    
                // Refund the processing fee
                if (msg.sender == refundTo) {
                    refundTo.sendEther(_message.fee + refundAmount);
                } else {
                    // If sender is another address, reward it and refund the rest
                    msg.sender.sendEther(_message.fee);
                    refundTo.sendEther(refundAmount);
                }
                emit MessageExecuted(msgHash);
            } else if (!isMessageProven) {
                emit MessageReceived(msgHash, _message, false);
            } else {
                revert B_INVOCATION_TOO_EARLY();
            }
        }
    
        /// @inheritdoc IBridge
        function retryMessage(
            Message calldata _message,
            bool _isLastAttempt
        )
            external
            nonReentrant
            whenNotPaused
            sameChain(_message.destChainId)
        {
            // If the gasLimit is set to 0 or isLastAttempt is true, the caller must
            // be the message.destOwner.
            if (_message.gasLimit == 0 || _isLastAttempt) {
                if (msg.sender != _message.destOwner) revert B_PERMISSION_DENIED();
            }
    
            bytes32 msgHash = hashMessage(_message);
            if (messageStatus[msgHash] != Status.RETRIABLE) {
                revert B_NON_RETRIABLE();
            }
    
            // Attempt to invoke the messageCall.
            if (_invokeMessageCall(_message, msgHash, gasleft())) {
                _updateMessageStatus(msgHash, Status.DONE);
            } else if (_isLastAttempt) {
                _updateMessageStatus(msgHash, Status.FAILED);
            }
            emit MessageRetried(msgHash);
        }
    
        /// @inheritdoc IBridge
        function isMessageSent(Message calldata _message) public view returns (bool) {
            if (_message.srcChainId != block.chainid) return false;
            return ISignalService(resolve("signal_service", false)).isSignalSent({
                _app: address(this),
                _signal: hashMessage(_message)
            });
        }
    
        /// @notice Checks if a msgHash has failed on its destination chain.
        /// @param _message The message.
        /// @param _proof The merkle inclusion proof.
        /// @return true if the message has failed, false otherwise.
        function proveMessageFailed(
            Message calldata _message,
            bytes calldata _proof
        )
            public
            view
            returns (bool)
        {
            if (_message.srcChainId != block.chainid) return false;
    
            return _proveSignalReceived(
                resolve("signal_service", false),
                signalForFailedMessage(hashMessage(_message)),
                _message.destChainId,
                _proof
            );
        }
    
        /// @notice Checks if a msgHash has failed on its destination chain.
        /// @param _message The message.
        /// @param _proof The merkle inclusion proof.
        /// @return true if the message has failed, false otherwise.
        function proveMessageReceived(
            Message calldata _message,
            bytes calldata _proof
        )
            public
            view
            returns (bool)
        {
            if (_message.destChainId != block.chainid) return false;
            return _proveSignalReceived(
                resolve("signal_service", false), hashMessage(_message), _message.srcChainId, _proof
            );
        }
    
        /// @notice Checks if the destination chain is enabled.
        /// @param _chainId The destination chain ID.
        /// @return enabled_ True if the destination chain is enabled.
        /// @return destBridge_ The bridge of the destination chain.
        function isDestChainEnabled(uint64 _chainId)
            public
            view
            returns (bool enabled_, address destBridge_)
        {
            destBridge_ = resolve(_chainId, "bridge", true);
            enabled_ = destBridge_ != address(0);
        }
    
        /// @notice Gets the current context.
        /// @inheritdoc IBridge
        function context() public view returns (Context memory ctx_) {
            ctx_ = _loadContext();
            if (ctx_.msgHash == 0 || ctx_.msgHash == bytes32(PLACEHOLDER)) {
                revert B_INVALID_CONTEXT();
            }
        }
    
        /// @notice Returns invocation delay values.
        /// @dev Bridge contract deployed on L1 shall use a non-zero value for better
        /// security.
        /// @return invocationDelay_ The minimal delay in second before a message can be executed since
        /// and the time it was received on the this chain.
        /// @return invocationExtraDelay_ The extra delay in second (to be added to invocationDelay) if
        /// the transactor is not the preferredExecutor who proved this message.
        function getInvocationDelays()
            public
            view
            virtual
            returns (uint256 invocationDelay_, uint256 invocationExtraDelay_)
        {
            if (
                block.chainid == 1 // Ethereum mainnet
            ) {
                // For Taiko mainnet
                // 384 seconds = 6.4 minutes = one ethereum epoch
                return (1 hours, 384 seconds);
            } else if (
                block.chainid == 2 // Ropsten
                    || block.chainid == 4 // Rinkeby
                    || block.chainid == 5 // Goerli
                    || block.chainid == 42 // Kovan
                    || block.chainid == 17_000 // Holesky
                    || block.chainid == 11_155_111 // Sepolia
            ) {
                // For all Taiko public testnets
                return (30 minutes, 384 seconds);
            } else if (block.chainid >= 32_300 && block.chainid <= 32_400) {
                // For all Taiko internal devnets
                return (5 minutes, 384 seconds);
            } else {
                // This is a Taiko L2 chain where no deleys are applied.
                return (0, 0);
            }
        }
    
        /// @inheritdoc IBridge
        function hashMessage(Message memory _message) public pure returns (bytes32) {
            return keccak256(abi.encode("TAIKO_MESSAGE", _message));
        }
    
        /// @notice Returns a signal representing a failed/recalled message.
        /// @param _msgHash The message hash.
        /// @return The failed representation of it as bytes32.
        function signalForFailedMessage(bytes32 _msgHash) public pure returns (bytes32) {
            return _msgHash ^ bytes32(uint256(Status.FAILED));
        }
    
        /// @notice Checks if the given address can pause and unpause the bridge.
        function _authorizePause(address)
            internal
            view
            virtual
            override
            onlyFromOwnerOrNamed("bridge_pauser")
        { }
    
        /// @notice Invokes a call message on the Bridge.
        /// @param _message The call message to be invoked.
        /// @param _msgHash The hash of the message.
        /// @param _gasLimit The gas limit for the message call.
        /// @return success_ A boolean value indicating whether the message call was
        /// successful.
        /// @dev This function updates the context in the state before and after the
        /// message call.
        function _invokeMessageCall(
            Message calldata _message,
            bytes32 _msgHash,
            uint256 _gasLimit
        )
            private
            returns (bool success_)
        {
            if (_gasLimit == 0) revert B_INVALID_GAS_LIMIT();
            assert(_message.from != address(this));
    
            _storeContext(_msgHash, _message.from, _message.srcChainId);
    
            if (
                _message.data.length >= 4 // msg can be empty
                    && bytes4(_message.data) != IMessageInvocable.onMessageInvocation.selector
                    && _message.to.isContract()
            ) {
                success_ = false;
            } else {
                (success_,) = ExcessivelySafeCall.excessivelySafeCall(
                    _message.to,
                    _gasLimit,
                    _message.value,
                    64, // return max 64 bytes
                    _message.data
                );
            }
    
            // Must reset the context after the message call
            _resetContext();
        }
    
        /// @notice Updates the status of a bridge message.
        /// @dev If the new status is different from the current status in the
        /// mapping, the status is updated and an event is emitted.
        /// @param _msgHash The hash of the message.
        /// @param _status The new status of the message.
        function _updateMessageStatus(bytes32 _msgHash, Status _status) private {
            if (messageStatus[_msgHash] == _status) return;
    
            messageStatus[_msgHash] = _status;
            emit MessageStatusChanged(_msgHash, _status);
    
            if (_status == Status.FAILED) {
                ISignalService(resolve("signal_service", false)).sendSignal(
                    signalForFailedMessage(_msgHash)
                );
            }
        }
    
        /// @notice Resets the call context
        function _resetContext() private {
            if (block.chainid == 1) {
                _storeContext(bytes32(0), address(0), uint64(0));
            } else {
                _storeContext(bytes32(PLACEHOLDER), address(uint160(PLACEHOLDER)), uint64(PLACEHOLDER));
            }
        }
    
        /// @notice Stores the call context
        /// @param _msgHash The message hash.
        /// @param _from The sender's address.
        /// @param _srcChainId The source chain ID.
        function _storeContext(bytes32 _msgHash, address _from, uint64 _srcChainId) private {
            if (block.chainid == 1) {
                assembly {
                    tstore(_CTX_SLOT, _msgHash)
                    tstore(add(_CTX_SLOT, 1), _from)
                    tstore(add(_CTX_SLOT, 2), _srcChainId)
                }
            } else {
                __ctx = Context(_msgHash, _from, _srcChainId);
            }
        }
    
        /// @notice Loads and returns the call context.
        /// @return ctx_ The call context.
        function _loadContext() private view returns (Context memory) {
            if (block.chainid == 1) {
                bytes32 msgHash;
                address from;
                uint64 srcChainId;
                assembly {
                    msgHash := tload(_CTX_SLOT)
                    from := tload(add(_CTX_SLOT, 1))
                    srcChainId := tload(add(_CTX_SLOT, 2))
                }
                return Context(msgHash, from, srcChainId);
            } else {
                return __ctx;
            }
        }
    
        /// @notice Checks if the signal was received.
        /// @param _signalService The signal service address.
        /// @param _signal The signal.
        /// @param _chainId The ID of the chain the signal is stored on.
        /// @param _proof The merkle inclusion proof.
        /// @return success_ True if the message was received.
        function _proveSignalReceived(
            address _signalService,
            bytes32 _signal,
            uint64 _chainId,
            bytes calldata _proof
        )
            private
            view
            returns (bool success_)
        {
            bytes memory data = abi.encodeCall(
                ISignalService.proveSignalReceived,
                (_chainId, resolve(_chainId, "bridge", false), _signal, _proof)
            );
            (success_,) = _signalService.staticcall(data);
        }
    }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L16-L593)

```solidity
File: /contracts/team/airdrop/ERC20Airdrop2.sol

// @audit from 5 to 4 you need to change the structure elements order to: , mapping, mapping, address, address, uint64, array
12: contract ERC20Airdrop2 is MerkleClaimable {
        using LibMath for uint256;
    
        /// @notice The address of the token contract.
        address public token;
    
        /// @notice The address of the vault contract.
        address public vault;
    
        /// @notice Represents the token amount for which the user has claimed.
        mapping(address addr => uint256 amountClaimed) public claimedAmount;
    
        /// @notice Represents the already withdrawn amount.
        mapping(address addr => uint256 amountWithdrawn) public withdrawnAmount;
    
        /// @notice Length of the withdrawal window.
        uint64 public withdrawalWindow;
    
        uint256[45] private __gap;
    
        /// @notice Event emitted when a user withdraws their tokens.
        /// @param user The address of the user.
        /// @param amount The amount of tokens withdrawn.
        event Withdrawn(address user, uint256 amount);
    
        error WITHDRAWALS_NOT_ONGOING();
    
        modifier ongoingWithdrawals() {
            if (claimEnd > block.timestamp || claimEnd + withdrawalWindow < block.timestamp) {
                revert WITHDRAWALS_NOT_ONGOING();
            }
            _;
        }
    
        /// @notice Initializes the contract.
        /// @param _owner The owner of this contract.
        /// @param _claimStart The start time of the claim period.
        /// @param _claimEnd The end time of the claim period.
        /// @param _merkleRoot The merkle root.
        /// @param _token The address of the token contract.
        /// @param _vault The address of the vault contract.
        /// @param _withdrawalWindow The length of the withdrawal window.
        function init(
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
            __Essential_init(_owner);
            __MerkleClaimable_init(_claimStart, _claimEnd, _merkleRoot);
    
            token = _token;
            vault = _vault;
            withdrawalWindow = _withdrawalWindow;
        }
    
        /// @notice Claims the airdrop for the user.
        /// @param user The address of the user.
        /// @param amount The amount of tokens to claim.
        /// @param proof The merkle proof.
        function claim(address user, uint256 amount, bytes32[] calldata proof) external nonReentrant {
            // Check if this can be claimed
            _verifyClaim(abi.encode(user, amount), proof);
    
            // Assign the tokens
            claimedAmount[user] += amount;
        }
    
        /// @notice External withdraw function
        /// @param user User address
        function withdraw(address user) external ongoingWithdrawals {
            (, uint256 amount) = getBalance(user);
            withdrawnAmount[user] += amount;
            IERC20(token).transferFrom(vault, user, amount);
    
            emit Withdrawn(user, amount);
        }
    
        /// @notice Getter for the balance and withdrawal amount per given user
        /// The 2nd airdrop is subject to an unlock period. User has to claim his
        /// tokens (within claimStart and claimEnd), but not immediately
        /// withdrawable. With a time of X (withdrawalWindow) it becomes fully
        /// withdrawable - and unlocks linearly.
        /// @param user User address
        /// @return balance The balance the user successfully claimed
        /// @return withdrawableAmount The amount available to withdraw
        function getBalance(address user)
            public
            view
            returns (uint256 balance, uint256 withdrawableAmount)
        {
            balance = claimedAmount[user];
            // If balance is 0 then there is no balance and withdrawable amount
            if (balance == 0) return (0, 0);
            // Balance might be positive before end of claiming (claimEnd - if claimed already) but
            // withdrawable is 0.
            if (block.timestamp < claimEnd) return (balance, 0);
    
            // Hard cap timestamp - so range cannot go over - to get more allocation over time.
            uint256 timeBasedAllowance = balance
                * (block.timestamp.min(claimEnd + withdrawalWindow) - claimEnd) / withdrawalWindow;
    
            withdrawableAmount = timeBasedAllowance - withdrawnAmount[user];
        }
    }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC20Airdrop2.sol#L12-L122)

```solidity
File: /contracts/tokenvault/BridgedERC1155.sol

// @audit from 5 to 4 you need to change the structure elements order to: , uint256, string, string, address, array
14: contract BridgedERC1155 is EssentialContract, IERC1155MetadataURIUpgradeable, ERC1155Upgradeable {
        /// @notice Address of the source token contract.
        address public srcToken;
    
        /// @notice Source chain ID where the token originates.
        uint256 public srcChainId;
    
        /// @dev Symbol of the bridged token.
        string private __symbol;
    
        /// @dev Name of the bridged token.
        string private __name;
    
        uint256[46] private __gap;
    
        error BTOKEN_CANNOT_RECEIVE();
    
        /// @notice Initializes the contract.
        /// @param _owner The owner of this contract. msg.sender will be used if this value is zero.
        /// @param _addressManager The address of the {AddressManager} contract.
        /// @param _srcToken Address of the source token.
        /// @param _srcChainId Source chain ID.
        /// @param _symbol Symbol of the bridged token.
        /// @param _name Name of the bridged token.
        function init(
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
            // Check if provided parameters are valid.
            // The symbol and the name can be empty for ERC1155 tokens so we use some placeholder data
            // for them instead.
            LibBridgedToken.validateInputs(_srcToken, _srcChainId, "foo", "foo");
            __Essential_init(_owner, _addressManager);
            __ERC1155_init(LibBridgedToken.buildURI(_srcToken, _srcChainId));
    
            srcToken = _srcToken;
            srcChainId = _srcChainId;
            __symbol = _symbol;
            __name = _name;
        }
    
        /// @dev Mints tokens.
        /// @param _to Address to receive the minted tokens.
        /// @param _tokenId ID of the token to mint.
        /// @param _amount Amount of tokens to mint.
        function mint(
            address _to,
            uint256 _tokenId,
            uint256 _amount
        )
            public
            nonReentrant
            whenNotPaused
            onlyFromNamed("erc1155_vault")
        {
            _mint(_to, _tokenId, _amount, "");
        }
    
        /// @dev Mints tokens.
        /// @param _to Address to receive the minted tokens.
        /// @param _tokenIds ID of the token to mint.
        /// @param _amounts Amount of tokens to mint.
        function mintBatch(
            address _to,
            uint256[] memory _tokenIds,
            uint256[] memory _amounts
        )
            public
            nonReentrant
            whenNotPaused
            onlyFromNamed("erc1155_vault")
        {
            _mintBatch(_to, _tokenIds, _amounts, "");
        }
    
        /// @dev Burns tokens.
        /// @param _account Address from which tokens are burned.
        /// @param _tokenId ID of the token to burn.
        /// @param _amount Amount of tokens to burn.
        function burn(
            address _account,
            uint256 _tokenId,
            uint256 _amount
        )
            public
            nonReentrant
            whenNotPaused
            onlyFromNamed("erc1155_vault")
        {
            _burn(_account, _tokenId, _amount);
        }
    
        /// @notice Gets the name of the bridged token.
        /// @return The name.
        function name() public view returns (string memory) {
            return LibBridgedToken.buildName(__name, srcChainId);
        }
    
        /// @notice Gets the symbol of the bridged token.
        /// @return The symbol.
        function symbol() public view returns (string memory) {
            return LibBridgedToken.buildSymbol(__symbol);
        }
    
        function _beforeTokenTransfer(
            address, /*_operator*/
            address, /*_from*/
            address _to,
            uint256[] memory, /*_ids*/
            uint256[] memory, /*_amounts*/
            bytes memory /*_data*/
        )
            internal
            virtual
            override
        {
            if (_to == address(this)) revert BTOKEN_CANNOT_RECEIVE();
            if (paused()) revert INVALID_PAUSE_STATUS();
        }
    }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC1155.sol#L14-L140)

```solidity
File: /contracts/tokenvault/BridgedERC721.sol

// @audit from 3 to 2 you need to change the structure elements order to: , uint256, address, array
12: contract BridgedERC721 is EssentialContract, ERC721Upgradeable {
        /// @notice Address of the source token contract.
        address public srcToken;
    
        /// @notice Source chain ID where the token originates.
        uint256 public srcChainId;
    
        uint256[48] private __gap;
    
        error BTOKEN_CANNOT_RECEIVE();
        error BTOKEN_INVALID_BURN();
    
        /// @notice Initializes the contract.
        /// @param _owner The owner of this contract. msg.sender will be used if this value is zero.
        /// @param _addressManager The address of the {AddressManager} contract.
        /// @param _srcToken Address of the source token.
        /// @param _srcChainId Source chain ID.
        /// @param _symbol Symbol of the bridged token.
        /// @param _name Name of the bridged token.
        function init(
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
            // Check if provided parameters are valid
            LibBridgedToken.validateInputs(_srcToken, _srcChainId, _symbol, _name);
            __Essential_init(_owner, _addressManager);
            __ERC721_init(_name, _symbol);
    
            srcToken = _srcToken;
            srcChainId = _srcChainId;
        }
    
        /// @dev Mints tokens.
        /// @param _account Address to receive the minted token.
        /// @param _tokenId ID of the token to mint.
        function mint(
            address _account,
            uint256 _tokenId
        )
            public
            nonReentrant
            whenNotPaused
            onlyFromNamed("erc721_vault")
        {
            _safeMint(_account, _tokenId);
        }
    
        /// @dev Burns tokens.
        /// @param _account Address from which the token is burned.
        /// @param _tokenId ID of the token to burn.
        function burn(
            address _account,
            uint256 _tokenId
        )
            public
            nonReentrant
            whenNotPaused
            onlyFromNamed("erc721_vault")
        {
            // Check if the caller is the owner of the token.
            if (ownerOf(_tokenId) != _account) {
                revert BTOKEN_INVALID_BURN();
            }
            _burn(_tokenId);
        }
    
        /// @notice Gets the name of the token.
        /// @return The name.
        function name() public view override(ERC721Upgradeable) returns (string memory) {
            return LibBridgedToken.buildName(super.name(), srcChainId);
        }
    
        /// @notice Gets the symbol of the bridged token.
        /// @return The symbol.
        function symbol() public view override(ERC721Upgradeable) returns (string memory) {
            return LibBridgedToken.buildSymbol(super.symbol());
        }
    
        /// @notice Gets the source token and source chain ID being bridged.
        /// @return The source token's address.
        /// @return The source token's chain ID.
        function source() public view returns (address, uint256) {
            return (srcToken, srcChainId);
        }
    
        /// @notice Returns the token URI.
        /// @param _tokenId The token id.
        /// @return The token URI following EIP-681.
        function tokenURI(uint256 _tokenId) public view virtual override returns (string memory) {
            return string(
                abi.encodePacked(
                    LibBridgedToken.buildURI(srcToken, srcChainId), Strings.toString(_tokenId)
                )
            );
        }
    
        function _beforeTokenTransfer(
            address, /*_from*/
            address _to,
            uint256, /*_firstTokenId*/
            uint256 /*_batchSize*/
        )
            internal
            virtual
            override
        {
            if (_to == address(this)) revert BTOKEN_CANNOT_RECEIVE();
            if (paused()) revert INVALID_PAUSE_STATUS();
        }
    }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC721.sol#L12-L128)

</details>

### <a name="GAS-47-1693312720"></a>[GAS-47] Structs can be packed into fewer storage slots
Each slot saved can avoid an extra Gsset (**20000 gas**) for the first setting of the struct. Subsequent reads as well as writes have smaller gas savings

*Instances (6)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/TaikoData.sol

// @audit from 8 to 7 you need to change the structure elements order to: , uint256, uint256, uint256, uint96, uint96, uint96, uint64, uint64, uint64, uint64, uint64, uint64, uint32, uint24, uint24, bool, bool, uint8
10:     struct Config {
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

// @audit from 7 to 5 you need to change the structure elements order to: , bytes32, bytes32, bytes32, address, address, uint24, uint24, bool, array
78:     struct BlockParams {
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

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/TaikoData.sol#L78-L88)

```solidity
File: /contracts/automata-attestation/lib/EnclaveIdStruct.sol

// @audit from 4 to 3 you need to change the structure elements order to: , bytes32, bytes16, bytes16, bytes4, bytes4, uint16, array
7:     struct EnclaveId {
           bytes4 miscselect;
           bytes4 miscselectMask;
           uint16 isvprodid;
           bytes16 attributes;
           bytes16 attributesMask;
           bytes32 mrsigner;
           TcbLevel[] tcbLevels;
       }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/EnclaveIdStruct.sol#L7-L15)

```solidity
File: /contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol

// @audit from 10 to 9 you need to change the structure elements order to: , bytes32, bytes32, bytes32, bytes, bytes, bytes, bytes28, bytes16, bytes16, bytes4, uint16, uint16
17:     struct EnclaveReport {
            bytes16 cpuSvn;
            bytes4 miscSelect;
            bytes28 reserved1;
            bytes16 attributes;
            bytes32 mrEnclave;
            bytes32 reserved2;
            bytes32 mrSigner;
            bytes reserved3; // 96 bytes
            uint16 isvProdId;
            uint16 isvSvn;
            bytes reserved4; // 60 bytes
            bytes reportData; // 64 bytes - For QEReports, this contains the hash of the concatenation
                // of attestation key and QEAuthData
        }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L17-L31)

```solidity
File: /contracts/signal/ISignalService.sol

// @audit from 3 to 2 you need to change the structure elements order to: , bytes32, uint64, uint64, CacheOption, array, array
20:     struct HopProof {
            uint64 chainId;
            uint64 blockId;
            bytes32 rootHash;
            CacheOption cacheOption;
            bytes[] accountProof;
            bytes[] storageProof;
        }

// @audit from 3 to 2 you need to change the structure elements order to: , bytes32, uint64, uint64, CacheOption, array, array
20:     struct HopProof {
            uint64 chainId;
            uint64 blockId;
            bytes32 rootHash;
            CacheOption cacheOption;
            bytes[] accountProof;
            bytes[] storageProof;
        }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/ISignalService.sol#L20-L27)

</details>

### <a name="GAS-48-1693312741"></a>[GAS-48] Constructors can be marked `payable`
Payable functions cost less gas to execute, since the compiler does not have to add extra checks to ensure that a payment wasn't provided.A constructor can safely be marked as payable, since only the deployer would be able to pass funds, and the project itself would not pass any funds.

*Instances (3)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

54:     constructor(address sigVerifyLibAddr, address pemCertLibAddr) {
            sigVerifyLib = ISigVerifyLib(sigVerifyLibAddr);
            pemCertLib = PEMCertChainLib(pemCertLibAddr);
            owner = msg.sender;
        }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/AutomataDcapV3Attestation.sol#L54-L58)

```solidity
File: /contracts/automata-attestation/utils/SigVerifyLib.sol

20:     constructor(address es256Verifier) {
            ES256VERIFIER = es256Verifier;
        }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/SigVerifyLib.sol#L20-L22)

```solidity
File: /contracts/common/EssentialContract.sol

64:     constructor() {
            _disableInitializers();
        }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/common/EssentialContract.sol#L64-L66)

</details>

### <a name="GAS-49-1699444393"></a>[GAS-49] Initializer can be marked `payable`
Payable functions cost less gas to execute, since the compiler does not have to add extra checks to ensure that a payment wasn't provided.An Initializer can safely be marked as payable, since only the allowed user would be able to pass funds, and the project itself would not pass any funds.

*Instances (24)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/TaikoL1.sol

42:     function init(
            address _owner,
            address _addressManager,
            bytes32 _genesisBlockHash
        )
            external
            initializer
        {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/TaikoL1.sol#L42-L49)

```solidity
File: /contracts/L1/TaikoToken.sol

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
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/TaikoToken.sol#L25-L33)

```solidity
File: /contracts/L1/gov/TaikoGovernor.sol

31:     function init(
            address _owner,
            IVotesUpgradeable _token,
            TimelockControllerUpgradeable _timelock
        )
            external
            initializer
        {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/gov/TaikoGovernor.sol#L31-L38)

```solidity
File: /contracts/L1/gov/TaikoTimelockController.sol

15:     function init(address _owner, uint256 _minDelay) external initializer {
            __Essential_init(_owner);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/gov/TaikoTimelockController.sol#L15-L16)

```solidity
File: /contracts/L1/hooks/AssignmentHook.sol

57:     function init(address _owner, address _addressManager) external initializer {
            __Essential_init(_owner, _addressManager);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/hooks/AssignmentHook.sol#L57-L58)

```solidity
File: /contracts/L1/provers/GuardianProver.sol

25:     function init(address _owner, address _addressManager) external initializer {
            __Essential_init(_owner, _addressManager);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/provers/GuardianProver.sol#L25-L26)

```solidity
File: /contracts/L1/tiers/DevnetTierProvider.sol

15:     function init(address _owner) external initializer {
            __Essential_init(_owner);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/tiers/DevnetTierProvider.sol#L15-L16)

```solidity
File: /contracts/L1/tiers/MainnetTierProvider.sol

15:     function init(address _owner) external initializer {
            __Essential_init(_owner);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/tiers/MainnetTierProvider.sol#L15-L16)

```solidity
File: /contracts/L1/tiers/TestnetTierProvider.sol

15:     function init(address _owner) external initializer {
            __Essential_init(_owner);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/tiers/TestnetTierProvider.sol#L15-L16)

```solidity
File: /contracts/L2/TaikoL2.sol

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
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/TaikoL2.sol#L71-L79)

```solidity
File: /contracts/bridge/Bridge.sol

75:     function init(address _owner, address _addressManager) external initializer {
            __Essential_init(_owner, _addressManager);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L75-L76)

```solidity
File: /contracts/common/AddressManager.sol

30:     function init(address _owner) external initializer {
            __Essential_init(_owner);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/common/AddressManager.sol#L30-L31)

```solidity
File: /contracts/signal/SignalService.sol

48:     function init(address _owner, address _addressManager) external initializer {
            __Essential_init(_owner, _addressManager);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/SignalService.sol#L48-L49)

```solidity
File: /contracts/team/TimelockTokenPool.sol

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
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/TimelockTokenPool.sol#L111-L119)

```solidity
File: /contracts/team/airdrop/ERC20Airdrop.sol

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
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC20Airdrop.sol#L27-L37)

```solidity
File: /contracts/team/airdrop/ERC20Airdrop2.sol

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
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC20Airdrop2.sol#L54-L65)

```solidity
File: /contracts/team/airdrop/ERC721Airdrop.sol

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
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC721Airdrop.sol#L25-L35)

```solidity
File: /contracts/tokenvault/BaseVault.sol

32:     function init(address _owner, address _addressManager) external initializer {
            __Essential_init(_owner, _addressManager);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BaseVault.sol#L32-L33)

```solidity
File: /contracts/tokenvault/BridgedERC1155.sol

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
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC1155.sol#L38-L48)

```solidity
File: /contracts/tokenvault/BridgedERC20.sol

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
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC20.sol#L52-L63)

```solidity
File: /contracts/tokenvault/BridgedERC721.sol

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
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC721.sol#L31-L41)

```solidity
File: /contracts/tokenvault/adapters/USDCAdapter.sol

38:     function init(address _owner, address _addressManager, IUSDC _usdc) external initializer {
            __Essential_init(_owner, _addressManager);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/adapters/USDCAdapter.sol#L38-L39)

```solidity
File: /contracts/verifiers/GuardianVerifier.sol

18:     function init(address _owner, address _addressManager) external initializer {
            __Essential_init(_owner, _addressManager);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/GuardianVerifier.sol#L18-L19)

```solidity
File: /contracts/verifiers/SgxVerifier.sol

83:     function init(address _owner, address _addressManager) external initializer {
            __Essential_init(_owner, _addressManager);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/SgxVerifier.sol#L83-L84)

</details>

### <a name="GAS-50-1693316170"></a>[GAS-50] `++i` costs less gas than `i++`, especially when it's used in `for`-loops (`--i`/`i--` too)
*Saves 5 gas per loop*

*Instances (11)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/libs/LibDepositing.sol

62:             _state.slotA.numEthDeposits++;

116:                 _state.slotA.numEthDeposits++;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibDepositing.sol#L116)

```solidity
File: /contracts/L1/libs/LibProving.sol

293:                 tid_ = _blk.nextTransitionId++;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProving.sol#L293)

```solidity
File: /contracts/L2/CrossChainOwned.sol

53:         emit TransactionExecuted(nextTxId++, bytes4(txdata));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/CrossChainOwned.sol#L53)

```solidity
File: /contracts/bridge/Bridge.sol

144:         message_.id = nextMessageId++;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L144)

```solidity
File: /contracts/thirdparty/optimism/rlp/RLPWriter.sol

40:                 lenLen++;

46:             for (i = 1; i <= lenLen; i++) {

59:         for (; i < 32; i++) {

66:         for (uint256 j = 0; j < out_.length; j++) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66)

```solidity
File: /contracts/thirdparty/optimism/trie/MerkleTrie.sol

85:         for (uint256 i = 0; i < proof.length; i++) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85)

```solidity
File: /contracts/verifiers/SgxVerifier.sol

222:             nextInstanceId++;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/SgxVerifier.sol#L222)

</details>

### <a name="GAS-51-1696084477"></a>[GAS-51] `++i`/`i++` should be `unchecked{++i}`/`unchecked{i++}` when it is not possible for them to overflow, as is the case when used in `for`- and `while`-loops
The `unchecked` keyword is new in solidity version 0.8.0, so this only applies to that version or higher, which these instances are. This saves **30-40 gas [per loop](https://gist.github.com/hrkrshnn/ee8fabd532058307229d65dcd5836ddc#the-increment-in-for-loop-post-condition-can-be-made-unchecked)**

*Instances (39)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/hooks/AssignmentHook.sol

172:         for (uint256 i; i < _tierFees.length; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/hooks/AssignmentHook.sol#L172)

```solidity
File: /contracts/L1/libs/LibProposing.sol

244:             for (uint256 i; i < params.hookCalls.length; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProposing.sol#L244)

```solidity
File: /contracts/L1/provers/Guardians.sol

74:         for (uint256 i; i < guardians.length; ++i) {

80:         for (uint256 i = 0; i < _newGuardians.length; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/provers/Guardians.sol#L80)

```solidity
File: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

80:         for (uint256 i; i < serialNumBatch.length; ++i) {

95:         for (uint256 i; i < serialNumBatch.length; ++i) {

191:         for (uint256 i; i < enclaveId.tcbLevels.length; ++i) {

214:         for (uint256 i; i < tcb.tcbLevels.length; ++i) {

240:         for (uint256 i; i < CPUSVN_LENGTH; ++i) {

259:         for (uint256 i; i < n; ++i) {

420:             for (uint256 i; i < 3; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/AutomataDcapV3Attestation.sol#L420)

```solidity
File: /contracts/automata-attestation/lib/PEMCertChainLib.sol

54:         for (uint256 i; i < size; ++i) {

244:         for (uint256 i; i < split.length; ++i) {

354:         for (uint256 i; i < SGX_TCB_CPUSVN_SIZE + 1; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/PEMCertChainLib.sol#L354)

```solidity
File: /contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

153:         for (uint256 i; i < encoded.length; ++i) {

281:         for (uint256 i; i < 3; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L281)

```solidity
File: /contracts/automata-attestation/utils/BytesUtils.sol

333:         for (uint256 i; i < len; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/BytesUtils.sol#L333)

```solidity
File: /contracts/automata-attestation/utils/RsaVerify.sol

140:         for (uint256 i = 2; i < 2 + paddingLen; ++i) {

152:             for (uint256 i; i < digestAlgoWithParamLen; ++i) {

158:             for (uint256 i; i < digestAlgoWithParamLen; ++i) {

174:         for (uint256 i; i < _sha256.length; ++i) {

273:         for (uint256 i = 2; i < 2 + paddingLen; ++i) {

283:         for (uint256 i; i < sha1Prefix.length; ++i) {

290:         for (uint256 i; i < _sha1.length; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/RsaVerify.sol#L290)

```solidity
File: /contracts/automata-attestation/utils/X509DateUtils.sol

48:         for (uint16 i = 1970; i < year; ++i) {

59:         for (uint8 i = 1; i < month; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/X509DateUtils.sol#L59)

```solidity
File: /contracts/bridge/Bridge.sol

90:         for (uint256 i; i < _msgHashes.length; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L90)

```solidity
File: /contracts/signal/SignalService.sol

104:         for (uint256 i; i < hopProofs.length; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/SignalService.sol#L104)

```solidity
File: /contracts/team/airdrop/ERC721Airdrop.sol

59:         for (uint256 i; i < tokenIds.length; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC721Airdrop.sol#L59)

```solidity
File: /contracts/thirdparty/optimism/rlp/RLPWriter.sol

46:             for (i = 1; i <= lenLen; i++) {

59:         for (; i < 32; i++) {

66:         for (uint256 j = 0; j < out_.length; j++) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66)

```solidity
File: /contracts/thirdparty/optimism/trie/MerkleTrie.sol

85:         for (uint256 i = 0; i < proof.length; i++) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85)

```solidity
File: /contracts/tokenvault/ERC1155Vault.sol

47:         for (uint256 i; i < _op.amounts.length; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC1155Vault.sol#L47)

```solidity
File: /contracts/tokenvault/ERC721Vault.sol

34:         for (uint256 i; i < _op.tokenIds.length; ++i) {

170:             for (uint256 i; i < _tokenIds.length; ++i) {

175:             for (uint256 i; i < _tokenIds.length; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC721Vault.sol#L175)

```solidity
File: /contracts/verifiers/SgxVerifier.sol

104:         for (uint256 i; i < _ids.length; ++i) {

210:         for (uint256 i; i < _instances.length; ++i) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/SgxVerifier.sol#L210)

</details>

### <a name="GAS-52-1709377106"></a>[GAS-52] Consider pre-calculating the address of `address(this)` to save gas
Use `foundry`'s [`script.sol`](https://book.getfoundry.sh/reference/forge-std/compute-create-address) or `solady`'s [`LibRlp.sol`](https://github.com/Vectorized/solady/blob/main/src/utils/LibRLP.sol) to save the value in a constant, which will avoid having to spend gas to push the value on the stack every time it's used.

*Instances (40)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/TaikoToken.sol

61:         if (_to == address(this)) revert TKO_INVALID_ADDR();

79:         if (_to == address(this)) revert TKO_INVALID_ADDR();

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/TaikoToken.sol#L79-L79)

```solidity
File: /contracts/L1/hooks/AssignmentHook.sol

125:         if (address(this).balance > 0) {

126:             taikoL1Address.sendEther(address(this).balance);

151:                 address(this),

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/hooks/AssignmentHook.sol#L151-L151)

```solidity
File: /contracts/L1/libs/LibProposing.sol

238:             uint256 tkoBalance = tko.balanceOf(address(this));

253:                 IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }(

260:             if (address(this).balance != 0) {

261:                 msg.sender.sendEther(address(this).balance);

268:             if (tko.balanceOf(address(this)) != tkoBalance + _config.livenessBond) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProposing.sol#L268-L268)

```solidity
File: /contracts/L1/libs/LibProving.sol

242:                 tko.transferFrom(msg.sender, address(this), tier.contestBond);

384:                 _tko.transferFrom(msg.sender, address(this), _tier.validityBond - reward);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProving.sol#L384-L384)

```solidity
File: /contracts/L2/CrossChainOwned.sol

50:         (bool success,) = address(this).call(txdata);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/CrossChainOwned.sol#L50-L50)

```solidity
File: /contracts/L2/TaikoL2.sol

174:             _to.sendEther(address(this).balance);

176:             IERC20(_token).safeTransfer(_to, IERC20(_token).balanceOf(address(this)));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/TaikoL2.sol#L176-L176)

```solidity
File: /contracts/bridge/Bridge.sol

174:             if (!ISignalService(signalService).isSignalSent(address(this), msgHash)) {

196:                 _storeContext(msgHash, address(this), _message.srcChainId);

270:                 _message.to == address(0) || _message.to == address(this)

343:             _app: address(this),

486:         assert(_message.from != address(this));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L486-L486)

```solidity
File: /contracts/signal/SignalService.sol

112:                 signalService = address(this);

131:         if (value == 0 || value != _loadSignalValue(address(this), signal)) {

149:         return _loadSignalValue(address(this), signal) == _chainData;

171:             chainData_ = _loadSignalValue(address(this), signal);

245:         _sendSignal(address(this), signal_, _chainData);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/SignalService.sol#L245-L245)

```solidity
File: /contracts/tokenvault/BridgedERC1155.sol

137:         if (_to == address(this)) revert BTOKEN_CANNOT_RECEIVE();

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC1155.sol#L137-L137)

```solidity
File: /contracts/tokenvault/BridgedERC20.sol

147:         if (_to == address(this)) revert BTOKEN_CANNOT_RECEIVE();

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC20.sol#L147-L147)

```solidity
File: /contracts/tokenvault/BridgedERC721.sol

125:         if (_to == address(this)) revert BTOKEN_CANNOT_RECEIVE();

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC721.sol#L125-L125)

```solidity
File: /contracts/tokenvault/ERC1155Vault.sol

108:         if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

226:             IERC1155(token).safeBatchTransferFrom(address(this), to, tokenIds, amounts, "");

272:                         to: address(this),

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC1155Vault.sol#L272-L272)

```solidity
File: /contracts/tokenvault/ERC20Vault.sol

267:         if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

378:             uint256 _balance = t.balanceOf(address(this));

379:             t.safeTransferFrom({ from: msg.sender, to: address(this), value: _amount });

380:             balanceChange_ = t.balanceOf(address(this)) - _balance;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC20Vault.sol#L380-L380)

```solidity
File: /contracts/tokenvault/ERC721Vault.sol

91:         if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

171:                 IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);

211:                     t.safeTransferFrom(_user, address(this), _op.tokenIds[i]);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC721Vault.sol#L211-L211)

```solidity
File: /contracts/tokenvault/adapters/USDCAdapter.sol

48:         usdc.transferFrom(_from, address(this), _amount);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/adapters/USDCAdapter.sol#L48-L48)

```solidity
File: /contracts/verifiers/SgxVerifier.sol

186:                 address(this),

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/SgxVerifier.sol#L186-L186)

</details>

### <a name="GAS-53-1693312824"></a>[GAS-53] Using `private` rather than `public` for constants, saves gas
If needed, the values can be read from the verified contract source code, or if there are multiple values there can be a single getter function that [returns a tuple](https://github.com/code-423n4/2022-08-frax/blob/90f55a9ce4e25bceed3a74290b854341d8de6afa/src/contracts/FraxlendPair.sol#L156-L178) of the values of all currently-public constants. Saves **3406-3606 gas** in deployment gas due to the compiler not having to create non-payable getter functions for deployment calldata, not having to store the bytes of the value outside of where it's used, and not adding another entry to the method ID table

*Instances (21)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/hooks/AssignmentHook.sol

38:     uint256 public constant MAX_GAS_PAYING_PROVER = 50_000;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/hooks/AssignmentHook.sol#L38)

```solidity
File: /contracts/L1/libs/LibProposing.sol

21:     uint256 public constant MAX_BYTES_PER_BLOB = 4096 * 32;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProposing.sol#L21)

```solidity
File: /contracts/L1/libs/LibProving.sol

20:     bytes32 public constant RETURN_LIVENESS_BOND = keccak256("RETURN_LIVENESS_BOND");

23:     bytes32 public constant TIER_OP = bytes32("tier_optimistic");

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProving.sol#L23)

```solidity
File: /contracts/L1/provers/Guardians.sol

11:     uint256 public constant MIN_NUM_GUARDIANS = 5;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/provers/Guardians.sol#L11)

```solidity
File: /contracts/L1/tiers/ITierProvider.sol

39:     uint16 public constant TIER_OPTIMISTIC = 100;

42:     uint16 public constant TIER_SGX = 200;

45:     uint16 public constant TIER_SGX_ZKVM = 300;

48:     uint16 public constant TIER_GUARDIAN = 1000;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/tiers/ITierProvider.sol#L48)

```solidity
File: /contracts/L2/TaikoL2.sol

32:     address public constant GOLDEN_TOUCH_ADDRESS = 0x0000777735367b36bC9B61C50022d9D0700dB4Ec;

35:     uint8 public constant BLOCK_SYNC_THRESHOLD = 5;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/TaikoL2.sol#L35)

```solidity
File: /contracts/libs/Lib4844.sol

10:     address public constant POINT_EVALUATION_PRECOMPILE_ADDRESS = address(0x0A);

13:     uint32 public constant FIELD_ELEMENTS_PER_BLOB = 4096;

16:     uint256 public constant BLS_MODULUS =

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/libs/Lib4844.sol#L16)

```solidity
File: /contracts/signal/LibSignals.sol

8:     bytes32 public constant STATE_ROOT = keccak256("STATE_ROOT");

11:     bytes32 public constant SIGNAL_ROOT = keccak256("SIGNAL_ROOT");

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/LibSignals.sol#L11)

```solidity
File: /contracts/tokenvault/BaseNFTVault.sol

47:     bytes4 public constant ERC1155_INTERFACE_ID = 0xd9b67a26;

50:     bytes4 public constant ERC721_INTERFACE_ID = 0x80ac58cd;

53:     uint256 public constant MAX_TOKEN_PER_TXN = 10;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BaseNFTVault.sol#L53)

```solidity
File: /contracts/verifiers/SgxVerifier.sol

30:     uint64 public constant INSTANCE_EXPIRY = 180 days;

34:     uint64 public constant INSTANCE_VALIDITY_DELAY = 1 days;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/SgxVerifier.sol#L34)

</details>

### <a name="GAS-54-1693312893"></a>[GAS-54] `private` functions only called once can be inlined to save gas
Not inlining costs 20 to 40 gas because of two extra JUMP instructions and additional stack operations needed for function calls.

*Instances (26)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/hooks/AssignmentHook.sol

164:     function _getProverFee(
             TaikoData.TierFee[] memory _tierFees,
             uint16 _tierId
         )
             private
             pure
             returns (uint256)
         {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/hooks/AssignmentHook.sol#L164-L171)

```solidity
File: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

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
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/AutomataDcapV3Attestation.sol#L303-L312)

```solidity
File: /contracts/automata-attestation/lib/PEMCertChainLib.sol

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
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/PEMCertChainLib.sol#L341-L348)

```solidity
File: /contracts/bridge/Bridge.sol

555:     function _loadContext() private view returns (Context memory) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L555)

```solidity
File: /contracts/signal/SignalService.sol

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
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/SignalService.sol#L271-L280)

```solidity
File: /contracts/team/TimelockTokenPool.sol

225:     function _voidGrant(Grant storage _grant) private returns (uint128 amountVoided) {

239:     function _getAmountUnlocked(Grant memory _grant) private view returns (uint128) {

267:     function _validateGrant(Grant memory _grant) private pure {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/TimelockTokenPool.sol#L267)

```solidity
File: /contracts/tokenvault/ERC1155Vault.sol

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
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC1155Vault.sol#L303)

```solidity
File: /contracts/tokenvault/ERC20Vault.sol

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
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC20Vault.sol#L407)

```solidity
File: /contracts/tokenvault/ERC721Vault.sol

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
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC721Vault.sol#L240)

```solidity
File: /contracts/verifiers/SgxVerifier.sol

226:     function _replaceInstance(uint256 id, address oldInstance, address newInstance) private {

233:     function _isInstanceValid(uint256 id, address instance) private view returns (bool) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/SgxVerifier.sol#L233)

</details>

### <a name="GAS-55-1699451217"></a>[GAS-55] Redundant state variable getters
Getters for public state variables are automatically generated so there is no need to code them manually and waste gas.

*Instances (1)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L2/TaikoL2EIP1559Configurable.sol

43:     function getConfig() public view override returns (Config memory) {
            return customConfig;
        }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/TaikoL2EIP1559Configurable.sol#L43-L45)

</details>

### <a name="GAS-56-1709385583"></a>[GAS-56] Reduce deployment costs by tweaking contracts' metadata
See [this](https://www.rareskills.io/post/solidity-metadata) link, at its bottom, for full details

*Instances (85)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/ITaikoL1.sol

8: interface ITaikoL1 {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/ITaikoL1.sol#L8)

```solidity
File: /contracts/L1/TaikoData.sol

8: library TaikoData {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/TaikoData.sol#L8)

```solidity
File: /contracts/L1/TaikoErrors.sol

11: abstract contract TaikoErrors {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/TaikoErrors.sol#L11)

```solidity
File: /contracts/L1/TaikoEvents.sol

13: abstract contract TaikoEvents {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/TaikoEvents.sol#L13)

```solidity
File: /contracts/L1/TaikoL1.sol

22: contract TaikoL1 is EssentialContract, ITaikoL1, TaikoEvents, TaikoErrors {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/TaikoL1.sol#L22)

```solidity
File: /contracts/L1/TaikoToken.sol

15: contract TaikoToken is EssentialContract, ERC20SnapshotUpgradeable, ERC20VotesUpgradeable {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/TaikoToken.sol#L15)

```solidity
File: /contracts/L1/gov/TaikoGovernor.sol

16: contract TaikoGovernor is

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/gov/TaikoGovernor.sol#L16)

```solidity
File: /contracts/L1/gov/TaikoTimelockController.sol

9: contract TaikoTimelockController is EssentialContract, TimelockControllerUpgradeable {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/gov/TaikoTimelockController.sol#L9)

```solidity
File: /contracts/L1/hooks/AssignmentHook.sol

14: contract AssignmentHook is EssentialContract, IHook {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/hooks/AssignmentHook.sol#L14)

```solidity
File: /contracts/L1/hooks/IHook.sol

8: interface IHook {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/hooks/IHook.sol#L8)

```solidity
File: /contracts/L1/libs/LibDepositing.sol

12: library LibDepositing {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibDepositing.sol#L12)

```solidity
File: /contracts/L1/libs/LibProposing.sol

15: library LibProposing {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProposing.sol#L15)

```solidity
File: /contracts/L1/libs/LibProving.sol

16: library LibProving {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProving.sol#L16)

```solidity
File: /contracts/L1/libs/LibUtils.sol

9: library LibUtils {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibUtils.sol#L9)

```solidity
File: /contracts/L1/libs/LibVerifying.sol

16: library LibVerifying {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibVerifying.sol#L16)

```solidity
File: /contracts/L1/provers/GuardianProver.sol

10: contract GuardianProver is Guardians {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/provers/GuardianProver.sol#L10)

```solidity
File: /contracts/L1/provers/Guardians.sol

9: abstract contract Guardians is EssentialContract {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/provers/Guardians.sol#L9)

```solidity
File: /contracts/L1/tiers/DevnetTierProvider.sol

10: contract DevnetTierProvider is EssentialContract, ITierProvider {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/tiers/DevnetTierProvider.sol#L10)

```solidity
File: /contracts/L1/tiers/ITierProvider.sol

7: interface ITierProvider {

37: library LibTiers {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/tiers/ITierProvider.sol#L37)

```solidity
File: /contracts/L1/tiers/MainnetTierProvider.sol

10: contract MainnetTierProvider is EssentialContract, ITierProvider {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/tiers/MainnetTierProvider.sol#L10)

```solidity
File: /contracts/L1/tiers/TestnetTierProvider.sol

10: contract TestnetTierProvider is EssentialContract, ITierProvider {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/tiers/TestnetTierProvider.sol#L10)

```solidity
File: /contracts/L2/CrossChainOwned.sol

14: abstract contract CrossChainOwned is EssentialContract, IMessageInvocable {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/CrossChainOwned.sol#L14)

```solidity
File: /contracts/L2/Lib1559Math.sol

10: library Lib1559Math {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/Lib1559Math.sol#L10)

```solidity
File: /contracts/L2/TaikoL2.sol

21: contract TaikoL2 is CrossChainOwned {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/TaikoL2.sol#L21)

```solidity
File: /contracts/L2/TaikoL2EIP1559Configurable.sol

9: contract TaikoL2EIP1559Configurable is TaikoL2 {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/TaikoL2EIP1559Configurable.sol#L9)

```solidity
File: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

22: contract AutomataDcapV3Attestation is IAttestation {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/AutomataDcapV3Attestation.sol#L22)

```solidity
File: /contracts/automata-attestation/interfaces/IAttestation.sol

8: interface IAttestation {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/interfaces/IAttestation.sol#L8)

```solidity
File: /contracts/automata-attestation/interfaces/ISigVerifyLib.sol

6: interface ISigVerifyLib {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L6)

```solidity
File: /contracts/automata-attestation/lib/EnclaveIdStruct.sol

6: library EnclaveIdStruct {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/EnclaveIdStruct.sol#L6)

```solidity
File: /contracts/automata-attestation/lib/PEMCertChainLib.sol

12: contract PEMCertChainLib is IPEMCertChainLib {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/PEMCertChainLib.sol#L12)

```solidity
File: /contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

11: library V3Parser {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L11)

```solidity
File: /contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol

6: library V3Struct {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L6)

```solidity
File: /contracts/automata-attestation/lib/TCBInfoStruct.sol

6: library TCBInfoStruct {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/TCBInfoStruct.sol#L6)

```solidity
File: /contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol

6: interface IPEMCertChainLib {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L6)

```solidity
File: /contracts/automata-attestation/utils/Asn1Decode.sol

12: library NodePtr {

38: library Asn1Decode {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/Asn1Decode.sol#L38)

```solidity
File: /contracts/automata-attestation/utils/BytesUtils.sol

8: library BytesUtils {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/BytesUtils.sol#L8)

```solidity
File: /contracts/automata-attestation/utils/RsaVerify.sol

34: library RsaVerify {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/RsaVerify.sol#L34)

```solidity
File: /contracts/automata-attestation/utils/SHA1.sol

10: library SHA1 {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/SHA1.sol#L10)

```solidity
File: /contracts/automata-attestation/utils/SigVerifyLib.sol

15: contract SigVerifyLib is ISigVerifyLib {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/SigVerifyLib.sol#L15)

```solidity
File: /contracts/automata-attestation/utils/X509DateUtils.sol

7: library X509DateUtils {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/X509DateUtils.sol#L7)

```solidity
File: /contracts/bridge/Bridge.sol

16: contract Bridge is EssentialContract, IBridge {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L16)

```solidity
File: /contracts/bridge/IBridge.sol

8: interface IBridge {

160: interface IRecallableSender {

174: interface IMessageInvocable {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/IBridge.sol#L174)

```solidity
File: /contracts/common/AddressManager.sol

10: contract AddressManager is EssentialContract, IAddressManager {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/common/AddressManager.sol#L10)

```solidity
File: /contracts/common/EssentialContract.sol

10: abstract contract EssentialContract is UUPSUpgradeable, Ownable2StepUpgradeable, AddressResolver {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/common/EssentialContract.sol#L10)

```solidity
File: /contracts/common/IAddressManager.sol

7: interface IAddressManager {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/common/IAddressManager.sol#L7)

```solidity
File: /contracts/libs/Lib4844.sol

8: library Lib4844 {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/libs/Lib4844.sol#L8)

```solidity
File: /contracts/libs/LibAddress.sol

13: library LibAddress {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/libs/LibAddress.sol#L13)

```solidity
File: /contracts/libs/LibMath.sol

7: library LibMath {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/libs/LibMath.sol#L7)

```solidity
File: /contracts/libs/LibTrieProof.sol

15: library LibTrieProof {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/libs/LibTrieProof.sol#L15)

```solidity
File: /contracts/signal/ISignalService.sol

12: interface ISignalService {

12: interface ISignalService {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/ISignalService.sol#L12)

```solidity
File: /contracts/signal/LibSignals.sol

6: library LibSignals {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/LibSignals.sol#L6)

```solidity
File: /contracts/signal/SignalService.sol

14: contract SignalService is EssentialContract, ISignalService {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/SignalService.sol#L14)

```solidity
File: /contracts/team/TimelockTokenPool.sol

25: contract TimelockTokenPool is EssentialContract {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/TimelockTokenPool.sol#L25)

```solidity
File: /contracts/team/airdrop/ERC20Airdrop.sol

11: contract ERC20Airdrop is MerkleClaimable {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC20Airdrop.sol#L11)

```solidity
File: /contracts/team/airdrop/ERC20Airdrop2.sol

12: contract ERC20Airdrop2 is MerkleClaimable {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC20Airdrop2.sol#L12)

```solidity
File: /contracts/team/airdrop/ERC721Airdrop.sol

9: contract ERC721Airdrop is MerkleClaimable {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC721Airdrop.sol#L9)

```solidity
File: /contracts/team/airdrop/MerkleClaimable.sol

10: abstract contract MerkleClaimable is EssentialContract {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/MerkleClaimable.sol#L10)

```solidity
File: /contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol

5: library ExcessivelySafeCall {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L5)

```solidity
File: /contracts/thirdparty/optimism/Bytes.sol

6: library Bytes {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/Bytes.sol#L6)

```solidity
File: /contracts/thirdparty/optimism/rlp/RLPReader.sol

9: library RLPReader {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/rlp/RLPReader.sol#L9)

```solidity
File: /contracts/thirdparty/optimism/rlp/RLPWriter.sol

9: library RLPWriter {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/rlp/RLPWriter.sol#L9)

```solidity
File: /contracts/thirdparty/optimism/trie/MerkleTrie.sol

11: library MerkleTrie {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/trie/MerkleTrie.sol#L11)

```solidity
File: /contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol

9: library SecureMerkleTrie {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L9)

```solidity
File: /contracts/tokenvault/BaseNFTVault.sol

9: abstract contract BaseNFTVault is BaseVault {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BaseNFTVault.sol#L9)

```solidity
File: /contracts/tokenvault/BaseVault.sol

12: abstract contract BaseVault is

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BaseVault.sol#L12)

```solidity
File: /contracts/tokenvault/BridgedERC1155.sol

14: contract BridgedERC1155 is EssentialContract, IERC1155MetadataURIUpgradeable, ERC1155Upgradeable {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC1155.sol#L14)

```solidity
File: /contracts/tokenvault/BridgedERC20.sol

15: contract BridgedERC20 is

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC20.sol#L15)

```solidity
File: /contracts/tokenvault/BridgedERC20Base.sol

9: abstract contract BridgedERC20Base is EssentialContract, IBridgedERC20 {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC20Base.sol#L9)

```solidity
File: /contracts/tokenvault/BridgedERC721.sol

12: contract BridgedERC721 is EssentialContract, ERC721Upgradeable {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC721.sol#L12)

```solidity
File: /contracts/tokenvault/ERC1155Vault.sol

16: interface IERC1155NameAndSymbol {

29: contract ERC1155Vault is BaseNFTVault, ERC1155ReceiverUpgradeable {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC1155Vault.sol#L29)

```solidity
File: /contracts/tokenvault/ERC20Vault.sol

18: contract ERC20Vault is BaseVault {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC20Vault.sol#L18)

```solidity
File: /contracts/tokenvault/ERC721Vault.sol

16: contract ERC721Vault is BaseNFTVault, IERC721Receiver {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC721Vault.sol#L16)

```solidity
File: /contracts/tokenvault/IBridgedERC20.sol

10: interface IBridgedERC20 {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/IBridgedERC20.sol#L10)

```solidity
File: /contracts/tokenvault/LibBridgedToken.sol

8: library LibBridgedToken {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/LibBridgedToken.sol#L8)

```solidity
File: /contracts/tokenvault/adapters/USDCAdapter.sol

8: interface IUSDC {

28: contract USDCAdapter is BridgedERC20Base {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/adapters/USDCAdapter.sol#L28)

```solidity
File: /contracts/verifiers/GuardianVerifier.sol

10: contract GuardianVerifier is EssentialContract, IVerifier {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/GuardianVerifier.sol#L10)

```solidity
File: /contracts/verifiers/IVerifier.sol

9: interface IVerifier {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/IVerifier.sol#L9)

```solidity
File: /contracts/verifiers/SgxVerifier.sol

19: contract SgxVerifier is EssentialContract, IVerifier {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/SgxVerifier.sol#L19)

</details>

### <a name="GAS-57-1693312940"></a>[GAS-57] Redundant else statement

*Instances (12)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/tiers/MainnetTierProvider.sol

68:         if (_rand % 1000 == 0) return LibTiers.TIER_SGX_ZKVM;
            else return LibTiers.TIER_SGX;
        }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/tiers/MainnetTierProvider.sol#L68-L70)

```solidity
File: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

319:         if (qeReportDataIsValid) {
                 bytes memory pckSignedQeReportBytes =
                     V3Parser.packQEReport(authDataV3.pckSignedQeReport);
                 bool qeSigVerified = sigVerifyLib.verifyES256Signature(
                     pckSignedQeReportBytes, authDataV3.qeReportSignature, pckCertPubKey
                 );
                 bool quoteSigVerified = sigVerifyLib.verifyES256Signature(
                     signedQuoteData, authDataV3.ecdsa256BitSignature, authDataV3.ecdsaAttestationKey
                 );
                 return qeSigVerified && quoteSigVerified;
             } else {
                 return false;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/AutomataDcapV3Attestation.sol#L319-L330)

```solidity
File: /contracts/automata-attestation/utils/Asn1Decode.sol

158:         if (der[ptr.ixf()] == 0) {
                 return der.substring(ptr.ixf() + 1, valueLength - 1);
             } else {
                 return der.substring(ptr.ixf(), valueLength);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/Asn1Decode.sol#L158-L161)

```solidity
File: /contracts/automata-attestation/utils/RsaVerify.sol

151:         if (digestAlgoWithParamLen == sha256ExplicitNullParam.length) {
                 for (uint256 i; i < digestAlgoWithParamLen; ++i) {
                     if (decipher[3 + paddingLen + i] != bytes1(sha256ExplicitNullParam[i])) {
                         return false;
                     }
                 }
             } else {
                 for (uint256 i; i < digestAlgoWithParamLen; ++i) {
                     if (decipher[3 + paddingLen + i] != bytes1(sha256ImplicitNullParam[i])) {
                         return false;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/RsaVerify.sol#L151-L160)

```solidity
File: /contracts/automata-attestation/utils/SigVerifyLib.sol

44:         } else if (alg == Algorithm.RS1) {
                if (publicKey.keyType != KeyType.RSA) {
                    return false;
                }
                return verifyRS1Signature(tbs, signature, publicKey.pubKey);
            } else {
                revert("Unsupported algorithm");
            }
        }
    
        function verifyCertificateSignature(
            bytes memory tbs,
            bytes memory signature,
            PublicKey memory publicKey,
            CertSigAlgorithm alg
        )
            public
            view
            returns (bool)

69:         } else if (alg == CertSigAlgorithm.Sha1WithRSAEncryption) {
                if (publicKey.keyType != KeyType.RSA) {
                    return false;
                }
                return verifyRS1Signature(tbs, signature, publicKey.pubKey);
            } else {
                revert("Unsupported algorithm");
            }
        }
    
        function verifyRS256Signature(
            bytes memory tbs,
            bytes memory signature,
            bytes memory publicKey
        )
            public
            view
            returns (bool sigValid)

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/SigVerifyLib.sol#L69-L86)

```solidity
File: /contracts/bridge/Bridge.sol

439:         } else if (block.chainid >= 32_300 && block.chainid <= 32_400) {
                 // For all Taiko internal devnets
                 return (5 minutes, 384 seconds);
             } else {
                 // This is a Taiko L2 chain where no deleys are applied.
                 return (0, 0);

556:         if (block.chainid == 1) {
                 bytes32 msgHash;
                 address from;
                 uint64 srcChainId;
                 assembly {
                     msgHash := tload(_CTX_SLOT)
                     from := tload(add(_CTX_SLOT, 1))
                     srcChainId := tload(add(_CTX_SLOT, 2))
                 }
                 return Context(msgHash, from, srcChainId);
             } else {
                 return __ctx;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L556-L567)

```solidity
File: /contracts/libs/LibAddress.sol

70:         if (Address.isContract(_addr)) {
                return IERC1271(_addr).isValidSignature(_hash, _sig) == _EIP1271_MAGICVALUE;
            } else {
                return ECDSA.recover(_hash, _sig) == _addr;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/libs/LibAddress.sol#L70-L73)

```solidity
File: /contracts/thirdparty/optimism/rlp/RLPReader.sol

223:         } else if (prefix <= 0xf7) {
                 // Short list.
                 // slither-disable-next-line variable-scope
                 uint256 listLen = prefix - 0xc0;
     
                 require(
                     _in.length > listLen,
                     "RLPReader: length of content must be greater than list length (short list)"
                 );
     
                 return (1, listLen, RLPItemType.LIST_ITEM);
             } else {
                 // Long list.
                 uint256 lenOfListLen = prefix - 0xf7;
     
                 require(
                     _in.length > lenOfListLen,
                     "RLPReader: length of content must be > than length of list length (long list)"
                 );
     
                 bytes1 firstByteOfContent;
                 assembly {
                     firstByteOfContent := and(mload(add(ptr, 1)), shl(248, 0xff))
                 }
     
                 require(
                     firstByteOfContent != 0x00,
                     "RLPReader: length of content must not have any leading zeros (long list)"
                 );
     
                 uint256 listLen;
                 assembly {
                     listLen := shr(sub(256, mul(8, lenOfListLen)), mload(add(ptr, 1)))
                 }
     
                 require(
                     listLen > 55,
                     "RLPReader: length of content must be greater than 55 bytes (long list)"
                 );
     
                 require(
                     _in.length > lenOfListLen + listLen,
                     "RLPReader: length of content must be greater than total length (long list)"
                 );
     
                 return (1 + lenOfListLen, listLen, RLPItemType.LIST_ITEM);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/rlp/RLPReader.sol#L223-L268)

```solidity
File: /contracts/thirdparty/optimism/trie/MerkleTrie.sol

112:                 if (currentKeyIndex == key.length) {
                         // Value is the last element of the decoded list (for branch nodes). There's
                         // some ambiguity in the Merkle trie specification because bytes(0) is a
                         // valid value to place into the trie, but for branch nodes bytes(0) can exist
                         // even when the value wasn't explicitly placed there. Geth treats a value of
                         // bytes(0) as "key does not exist" and so we do the same.
                         value_ = RLPReader.readBytes(currentNode.decoded[TREE_RADIX]);
                         require(
                             value_.length > 0,
                             "MerkleTrie: value length must be greater than zero (branch)"
                         );
     
                         // Extra proof elements are not allowed.
                         require(
                             i == proof.length - 1,
                             "MerkleTrie: value node must be last node in proof (branch)"
                         );
     
                         return value_;
                     } else {
                         // We're not at the end of the key yet.
                         // Figure out what the next node ID should be and continue.
                         uint8 branchKey = uint8(key[currentKeyIndex]);
                         RLPReader.RLPItem memory nextNode = currentNode.decoded[branchKey];
                         currentNodeID = _getNodeID(nextNode);
                         currentKeyIndex += 1;
                     }
                 } else if (currentNode.decoded.length == LEAF_OR_EXTENSION_NODE_LENGTH) {
                     bytes memory path = _getNodePath(currentNode);
                     uint8 prefix = uint8(path[0]);
                     uint8 offset = 2 - (prefix % 2);
                     bytes memory pathRemainder = Bytes.slice(path, offset);
                     bytes memory keyRemainder = Bytes.slice(key, currentKeyIndex);
                     uint256 sharedNibbleLength = _getSharedNibbleLength(pathRemainder, keyRemainder);
     
                     // Whether this is a leaf node or an extension node, the path remainder MUST be a
                     // prefix of the key remainder (or be equal to the key remainder) or the proof is
                     // considered invalid.
                     require(
                         pathRemainder.length == sharedNibbleLength,
                         "MerkleTrie: path remainder must share all nibbles with key"
                     );
     
                     if (prefix == PREFIX_LEAF_EVEN || prefix == PREFIX_LEAF_ODD) {
                         // Prefix of 2 or 3 means this is a leaf node. For the leaf node to be valid,
                         // the key remainder must be exactly equal to the path remainder. We already
                         // did the necessary byte comparison, so it's more efficient here to check that
                         // the key remainder length equals the shared nibble length, which implies
                         // equality with the path remainder (since we already did the same check with
                         // the path remainder and the shared nibble length).
                         require(
                             keyRemainder.length == sharedNibbleLength,
                             "MerkleTrie: key remainder must be identical to path remainder"
                         );
     
                         // Our Merkle Trie is designed specifically for the purposes of the Ethereum
                         // state trie. Empty values are not allowed in the state trie, so we can safely
                         // say that if the value is empty, the key should not exist and the proof is
                         // invalid.
                         value_ = RLPReader.readBytes(currentNode.decoded[1]);
                         require(
                             value_.length > 0,
                             "MerkleTrie: value length must be greater than zero (leaf)"
                         );
     
                         // Extra proof elements are not allowed.
                         require(
                             i == proof.length - 1,
                             "MerkleTrie: value node must be last node in proof (leaf)"
                         );
     
                         return value_;

139:             } else if (currentNode.decoded.length == LEAF_OR_EXTENSION_NODE_LENGTH) {
                     bytes memory path = _getNodePath(currentNode);
                     uint8 prefix = uint8(path[0]);
                     uint8 offset = 2 - (prefix % 2);
                     bytes memory pathRemainder = Bytes.slice(path, offset);
                     bytes memory keyRemainder = Bytes.slice(key, currentKeyIndex);
                     uint256 sharedNibbleLength = _getSharedNibbleLength(pathRemainder, keyRemainder);
     
                     // Whether this is a leaf node or an extension node, the path remainder MUST be a
                     // prefix of the key remainder (or be equal to the key remainder) or the proof is
                     // considered invalid.
                     require(
                         pathRemainder.length == sharedNibbleLength,
                         "MerkleTrie: path remainder must share all nibbles with key"
                     );
     
                     if (prefix == PREFIX_LEAF_EVEN || prefix == PREFIX_LEAF_ODD) {
                         // Prefix of 2 or 3 means this is a leaf node. For the leaf node to be valid,
                         // the key remainder must be exactly equal to the path remainder. We already
                         // did the necessary byte comparison, so it's more efficient here to check that
                         // the key remainder length equals the shared nibble length, which implies
                         // equality with the path remainder (since we already did the same check with
                         // the path remainder and the shared nibble length).
                         require(
                             keyRemainder.length == sharedNibbleLength,
                             "MerkleTrie: key remainder must be identical to path remainder"
                         );
     
                         // Our Merkle Trie is designed specifically for the purposes of the Ethereum
                         // state trie. Empty values are not allowed in the state trie, so we can safely
                         // say that if the value is empty, the key should not exist and the proof is
                         // invalid.
                         value_ = RLPReader.readBytes(currentNode.decoded[1]);
                         require(
                             value_.length > 0,
                             "MerkleTrie: value length must be greater than zero (leaf)"
                         );
     
                         // Extra proof elements are not allowed.
                         require(
                             i == proof.length - 1,
                             "MerkleTrie: value node must be last node in proof (leaf)"
                         );
     
                         return value_;
                     } else if (prefix == PREFIX_EXTENSION_EVEN || prefix == PREFIX_EXTENSION_ODD) {
                         // Prefix of 0 or 1 means this is an extension node. We move onto the next node
                         // in the proof and increment the key index by the length of the path remainder
                         // which is equal to the shared nibble length.
                         currentNodeID = _getNodeID(currentNode.decoded[1]);
                         currentKeyIndex += sharedNibbleLength;
                     } else {
                         revert("MerkleTrie: received a node with an unknown prefix");
                     }
                 } else {
                     revert("MerkleTrie: received an unparseable node");
                 }
             }
     
             revert("MerkleTrie: ran out of proof elements");
         }
     
         /// @notice Parses an array of proof elements into a new array that contains both the original
         ///         encoded element and the RLP-decoded element.
         /// @param _proof Array of proof elements to parse.
         /// @return proof_ Proof parsed into easily accessible structs.

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/trie/MerkleTrie.sol#L139-L204)

</details>

### <a name="GAS-58-1693312958"></a>[GAS-58] Functions guaranteed to revert when called by normal users can be marked `payable`
If a function modifier such as `onlyOwner` is used, the function will revert if a normal user tries to pay the function. Marking the function as `payable` will lower the gas cost for legitimate callers because the compiler will not include checks for whether a payment was provided.The extra opcodes avoided are `CALLVALUE`(2), `DUP1`(3), `ISZERO`(3), `PUSH2`(3), `JUMPI`(10), `PUSH1`(3), `DUP1`(3), `REVERT`(0), `JUMPDEST`(1), `POP`(2), which costs an average of about ** 21 gas per call ** to the function, in addition to the extra deployment cost

*Instances (49)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/TaikoL1.sol

220:     function _authorizePause(address)
             internal
             view
             virtual
             override
             onlyFromOwnerOrNamed("chain_pauser")
         { }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/TaikoL1.sol#L220-L226)

```solidity
File: /contracts/L1/TaikoToken.sol

47:     function burn(address _from, uint256 _amount) public onlyOwner {

52:     function snapshot() public onlyFromOwnerOrNamed("snapshooter") {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/TaikoToken.sol#L52)

```solidity
File: /contracts/L1/libs/LibProposing.sol

299:     function _isProposerPermitted(
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

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProposing.sol#L299-L316)

```solidity
File: /contracts/L1/libs/LibProving.sol

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
             // The highest tier proof can always submit new proofs
             if (_tier.contestBond == 0) return;
     
             bool inProvingWindow = uint256(_ts.timestamp).max(_state.slotB.lastUnpausedAt)
                 + _tier.provingWindow * 60 >= block.timestamp;
             bool isAssignedPover = msg.sender == _blk.assignedProver;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProving.sol#L401-L416)

```solidity
File: /contracts/L1/provers/Guardians.sol

53:     function setGuardians(
            address[] memory _newGuardians,
            uint8 _minGuardians
        )
            external
            onlyOwner
            nonReentrant
        {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/provers/Guardians.sol#L53-L60)

```solidity
File: /contracts/L2/CrossChainOwned.sol

60:     function __CrossChainOwned_init(
            address _owner,
            address _addressManager,
            uint64 _ownerChainId
        )
            internal
            virtual
            onlyInitializing
        {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/CrossChainOwned.sol#L60-L68)

```solidity
File: /contracts/L2/TaikoL2.sol

107:     function anchor(
             bytes32 _l1BlockHash,
             bytes32 _l1StateRoot,
             uint64 _l1BlockId,
             uint32 _parentGasUsed
         )
             external
             nonReentrant
         {
             if (
                 _l1BlockHash == 0 || _l1StateRoot == 0 || _l1BlockId == 0
                     || (block.number != 1 && _parentGasUsed == 0)
             ) {
                 revert L2_INVALID_PARAM();
             }
     
             if (msg.sender != GOLDEN_TOUCH_ADDRESS) revert L2_INVALID_SENDER();

163:     function withdraw(
             address _token,
             address _to
         )
             external
             onlyFromOwnerOrNamed("withdrawer")
             nonReentrant
             whenNotPaused
         {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/TaikoL2.sol#L163-L171)

```solidity
File: /contracts/L2/TaikoL2EIP1559Configurable.sol

25:     function setConfigAndExcess(
            Config memory _newConfig,
            uint64 _newGasExcess
        )
            external
            virtual
            onlyOwner
        {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/TaikoL2EIP1559Configurable.sol#L25-L32)

```solidity
File: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

65:     function setMrSigner(bytes32 _mrSigner, bool _trusted) external onlyOwner {

69:     function setMrEnclave(bytes32 _mrEnclave, bool _trusted) external onlyOwner {

73:     function addRevokedCertSerialNum(
            uint256 index,
            bytes[] calldata serialNumBatch
        )
            external
            onlyOwner
        {

88:     function removeRevokedCertSerialNum(
            uint256 index,
            bytes[] calldata serialNumBatch
        )
            external
            onlyOwner
        {

103:     function configureTcbInfoJson(
             string calldata fmspc,
             TCBInfoStruct.TCBInfo calldata tcbInfoInput
         )
             public
             onlyOwner
         {

114:     function configureQeIdentityJson(EnclaveIdStruct.EnclaveId calldata qeIdentityInput)
             external
             onlyOwner
         {

122:     function toggleLocalReportCheck() external onlyOwner {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/AutomataDcapV3Attestation.sol#L122)

```solidity
File: /contracts/bridge/Bridge.sol

82:     function suspendMessages(
            bytes32[] calldata _msgHashes,
            bool _suspend
        )
            external
            onlyFromOwnerOrNamed("bridge_watchdog")
        {

101:     function banAddress(
             address _addr,
             bool _ban
         )
             external
             onlyFromOwnerOrNamed("bridge_watchdog")
             nonReentrant
         {

217:     function processMessage(
             Message calldata _message,
             bytes calldata _proof
         )
             external
             nonReentrant
             whenNotPaused
             sameChain(_message.destChainId)
         {
             bytes32 msgHash = hashMessage(_message);
             if (messageStatus[msgHash] != Status.NEW) revert B_STATUS_MISMATCH();
     
             address signalService = resolve("signal_service", false);
             uint64 receivedAt = proofReceipt[msgHash].receivedAt;
             bool isMessageProven = receivedAt != 0;
     
             (uint256 invocationDelay, uint256 invocationExtraDelay) = getInvocationDelays();
     
             if (!isMessageProven) {
                 if (!_proveSignalReceived(signalService, msgHash, _message.srcChainId, _proof)) {
                     revert B_NOT_RECEIVED();
                 }
     
                 receivedAt = uint64(block.timestamp);
     
                 if (invocationDelay != 0) {
                     proofReceipt[msgHash] = ProofReceipt({
                         receivedAt: receivedAt,
                         preferredExecutor: _message.gasLimit == 0 ? _message.destOwner : msg.sender
                     });
                 }
             }
     
             if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) {

310:     function retryMessage(
             Message calldata _message,
             bool _isLastAttempt
         )
             external
             nonReentrant
             whenNotPaused
             sameChain(_message.destChainId)
         {
             // If the gasLimit is set to 0 or isLastAttempt is true, the caller must
             // be the message.destOwner.
             if (_message.gasLimit == 0 || _isLastAttempt) {
                 if (msg.sender != _message.destOwner) revert B_PERMISSION_DENIED();

461:     function _authorizePause(address)
             internal
             view
             virtual
             override
             onlyFromOwnerOrNamed("bridge_pauser")
         { }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L461-L467)

```solidity
File: /contracts/common/AddressManager.sol

38:     function setAddress(
            uint64 _chainId,
            bytes32 _name,
            address _newAddress
        )
            external
            virtual
            onlyOwner
        {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/common/AddressManager.sol#L38-L46)

```solidity
File: /contracts/common/EssentialContract.sol

95:     function __Essential_init(
            address _owner,
            address _addressManager
        )
            internal
            virtual
            onlyInitializing
        {

114:     function _authorizeUpgrade(address) internal virtual override onlyOwner { }

116:     function _authorizePause(address) internal virtual onlyOwner { }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/common/EssentialContract.sol#L116)

```solidity
File: /contracts/libs/LibAddress.sol

77:     function isSenderEOA() internal view returns (bool) {
            return msg.sender == tx.origin;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/libs/LibAddress.sol#L77-L78)

```solidity
File: /contracts/signal/SignalService.sol

56:     function authorize(address _addr, bool _authorize) external onlyOwner {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/SignalService.sol#L56)

```solidity
File: /contracts/team/TimelockTokenPool.sol

135:     function grant(address _recipient, Grant memory _grant) external onlyOwner {

150:     function void(address _recipient) external onlyOwner {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/TimelockTokenPool.sol#L150)

```solidity
File: /contracts/team/airdrop/MerkleClaimable.sol

45:     function setConfig(
            uint64 _claimStart,
            uint64 _claimEnd,
            bytes32 _merkleRoot
        )
            external
            onlyOwner
        {

56:     function __MerkleClaimable_init(
            uint64 _claimStart,
            uint64 _claimEnd,
            bytes32 _merkleRoot
        )
            internal
            onlyInitializing
        {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/MerkleClaimable.sol#L56-L63)

```solidity
File: /contracts/tokenvault/BaseVault.sol

47:     function checkProcessMessageContext()
            internal
            view
            onlyFromBridge
            returns (IBridge.Context memory ctx_)
        {

58:     function checkRecallMessageContext()
            internal
            view
            onlyFromBridge
            returns (IBridge.Context memory ctx_)
        {

58:     function checkRecallMessageContext()
            internal
            view
            onlyFromBridge
            returns (IBridge.Context memory ctx_)
        {
            ctx_ = IBridge(msg.sender).context();
            if (ctx_.from != msg.sender) revert VAULT_PERMISSION_DENIED();

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BaseVault.sol#L58-L65)

```solidity
File: /contracts/tokenvault/BridgedERC1155.sol

66:     function mint(
            address _to,
            uint256 _tokenId,
            uint256 _amount
        )
            public
            nonReentrant
            whenNotPaused
            onlyFromNamed("erc1155_vault")
        {

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

100:     function burn(
             address _account,
             uint256 _tokenId,
             uint256 _amount
         )
             public
             nonReentrant
             whenNotPaused
             onlyFromNamed("erc1155_vault")
         {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC1155.sol#L100-L109)

```solidity
File: /contracts/tokenvault/BridgedERC20.sol

80:     function setSnapshoter(address _snapshooter) external onlyOwner {

85:     function snapshot() external onlyOwnerOrSnapshooter {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC20.sol#L85)

```solidity
File: /contracts/tokenvault/BridgedERC20Base.sol

36:     function changeMigrationStatus(
            address _migratingAddress,
            bool _migratingInbound
        )
            external
            nonReentrant
            whenNotPaused
            onlyFromOwnerOrNamed("erc20_vault")
        {

57:     function mint(address _account, uint256 _amount) public nonReentrant whenNotPaused {
            // mint is disabled while migrating outbound.
            if (_isMigratingOut()) revert BB_MINT_DISALLOWED();
    
            if (msg.sender == migratingAddress) {

75:     function burn(address _account, uint256 _amount) public nonReentrant whenNotPaused {
            if (_isMigratingOut()) {
                // Only the owner of the tokens himself can migrate out
                if (msg.sender != _account) revert BB_PERMISSION_DENIED();
                // Outbound migration
                emit MigratedTo(migratingAddress, _account, _amount);
                // Ask the new bridged token to mint token for the user.
                IBridgedERC20(migratingAddress).mint(_account, _amount);
            } else if (msg.sender != resolve("erc20_vault", true)) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC20Base.sol#L75-L83)

```solidity
File: /contracts/tokenvault/BridgedERC721.sol

54:     function mint(
            address _account,
            uint256 _tokenId
        )
            public
            nonReentrant
            whenNotPaused
            onlyFromNamed("erc721_vault")
        {

69:     function burn(
            address _account,
            uint256 _tokenId
        )
            public
            nonReentrant
            whenNotPaused
            onlyFromNamed("erc721_vault")
        {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC721.sol#L69-L77)

```solidity
File: /contracts/tokenvault/ERC20Vault.sol

148:     function changeBridgedToken(
             CanonicalERC20 calldata _ctoken,
             address _btokenNew
         )
             external
             nonReentrant
             whenNotPaused
             onlyOwner
             returns (address btokenOld_)
         {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC20Vault.sol#L148-L157)

```solidity
File: /contracts/verifiers/SgxVerifier.sol

90:     function addInstances(address[] calldata _instances)
            external
            onlyOwner
            returns (uint256[] memory)
        {

100:     function deleteInstances(uint256[] calldata _ids)
             external
             onlyFromOwnerOrNamed("rollup_watchdog")
         {

139:     function verifyProof(
             Context calldata _ctx,
             TaikoData.Transition calldata _tran,
             TaikoData.TierProof calldata _proof
         )
             external
             onlyFromNamed("taiko")
         {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/SgxVerifier.sol#L139-L146)

</details>

### <a name="GAS-59-1693312972"></a>[GAS-59] Avoid updating storage when the value hasn't changed to save gas
If the old value is equal to the new value, not re-storing the value will avoid a Gsreset (**2900 gas**), potentially at the expense of a Gcoldsload (**2100 gas**) or a Gwarmaccess (**100 gas**)

*Instances (4)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

65:     function setMrSigner(bytes32 _mrSigner, bool _trusted) external onlyOwner {

69:     function setMrEnclave(bytes32 _mrEnclave, bool _trusted) external onlyOwner {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/AutomataDcapV3Attestation.sol#L69)

```solidity
File: /contracts/team/airdrop/MerkleClaimable.sol

45:     function setConfig(

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/MerkleClaimable.sol#L45)

```solidity
File: /contracts/tokenvault/BridgedERC20.sol

80:     function setSnapshoter(address _snapshooter) external onlyOwner {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC20.sol#L80)

</details>

### <a name="GAS-60-1693312999"></a>[GAS-60] Use shift Left instead of multiplication if possible to save gas

*Instances (6)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L2/TaikoL2.sol

213:         config_.gasTargetPerL1Block = 15 * 1e6 * 4;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/TaikoL2.sol#L213)

```solidity
File: /contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

158:             uint256 acc = lowerDigit * (16 ** (2 * i));

159:             acc += upperDigit * (16 ** ((2 * i) + 1));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L159)

```solidity
File: /contracts/automata-attestation/utils/Asn1Decode.sol

145:         return uint256(der.readBytesN(ptr.ixf(), len) >> (32 - len) * 8);

203:                     der.readBytesN(ix + 2, lengthbytesLength) >> (32 - lengthbytesLength) * 8

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/Asn1Decode.sol#L203)

```solidity
File: /contracts/automata-attestation/utils/BytesUtils.sol

93:                     mask = ~(2 ** (8 * (32 - shortest + idx)) - 1);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/BytesUtils.sol#L93)

</details>

### <a name="GAS-61-1693313015"></a>[GAS-61] Usage of `uints`/`ints` smaller than 32 bytes (256 bits) incurs overhead
> When using elements that are smaller than 32 bytes, your contract's gas usage may be higher. This is because the EVM operates on 32 bytes at a time. Therefore, if the element is smaller than that, the EVM must use more operations in order to reduce the size of the element from 32 bytes to the desired size.
https://docs.soliditylang.org/en/v0.8.11/internals/layout_in_storage.html
Each operation involving a `uint8` costs an extra [** 22 - 28 gas **](https://gist.github.com/IllIllI000/9388d20c70f9a4632eb3ca7836f54977) (depending on whether the other operand is also a variable of type `uint8`) as compared to ones involving `uint256`, due to the compiler having to clear the higher bits of the memory word before operating on the `uint8`, as well as the associated stack operations of doing so. Use a larger size then downcast where needed

*Instances (174)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/ITaikoL1.sol

//@audit `_blockId` is `uint64`
27:     function proveBlock(uint64 _blockId, bytes calldata _input) external;

//@audit `_maxBlocksToVerify` is `uint64`
31:     function verifyBlocks(uint64 _maxBlocksToVerify) external;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/ITaikoL1.sol#L31)

```solidity
File: /contracts/L1/TaikoL1.sol

//@audit `_blockId` is `uint64`
76:         uint64 _blockId,

//@audit `maxBlocksToVerify` is `uint8`
94:         uint8 maxBlocksToVerify = LibProving.proveBlock(state, config, this, meta, tran, proof);

//@audit `_maxBlocksToVerify` is `uint64`
100:     function verifyBlocks(uint64 _maxBlocksToVerify)

//@audit `_blockId` is `uint64`
145:     function getBlock(uint64 _blockId)

//@audit `slot` is `uint64`
150:         uint64 slot;

//@audit `_blockId` is `uint64`
163:         uint64 _blockId,

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/TaikoL1.sol#L163)

```solidity
File: /contracts/L1/hooks/AssignmentHook.sol

//@audit `_tierId` is `uint16`
166:         uint16 _tierId

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/hooks/AssignmentHook.sol#L166)

```solidity
File: /contracts/L1/libs/LibDepositing.sol

//@audit `fee` is `uint96`
83:             uint96 fee = uint96(_config.ethDepositMaxFee.min(block.basefee * _config.ethDepositGas));

//@audit `j` is `uint64`
84:             uint64 j = _state.slotA.nextEthDepositToProcess;

//@audit `totalFee` is `uint96`
85:             uint96 totalFee;

//@audit `_fee` is `uint96`
93:                 uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibDepositing.sol#L93)

```solidity
File: /contracts/L1/libs/LibProving.sol

//@audit `maxBlocksToVerify_` is `uint8`
100:         returns (uint8 maxBlocksToVerify_)

//@audit `slot` is `uint64`
115:         uint64 slot = _meta.id % _config.blockRingBufferSize;

//@audit `tid` is `uint32`
129:         (uint32 tid, TaikoData.TransitionState storage ts) =

//@audit `slot` is `uint64`
273:         uint64 slot

//@audit `tid_` is `uint32`
276:         returns (uint32 tid_, TaikoData.TransitionState storage ts_)

//@audit `_tid` is `uint32`
405:         uint32 _tid,

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProving.sol#L405)

```solidity
File: /contracts/L1/libs/LibUtils.sol

//@audit `_blockId` is `uint64`
26:         uint64 _blockId,

//@audit `slot` is `uint64`
38:         uint64 slot = _blockId % _config.blockRingBufferSize;

//@audit `tid` is `uint32`
42:         uint32 tid = getTransitionId(_state, blk, slot, _parentHash);

//@audit `_blockId` is `uint64`
55:         uint64 _blockId

//@audit `slot_` is `uint64`
59:         returns (TaikoData.Block storage blk_, uint64 slot_)

//@audit `_slot` is `uint64`
73:         uint64 _slot,

//@audit `tid_` is `uint32`
78:         returns (uint32 tid_)

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibUtils.sol#L78)

```solidity
File: /contracts/L1/libs/LibVerifying.sol

//@audit `_maxBlocksToVerify` is `uint64`
89:         uint64 _maxBlocksToVerify

//@audit `blockId` is `uint64`
100:         uint64 blockId = b.lastVerifiedBlockId;

//@audit `slot` is `uint64`
102:         uint64 slot = blockId % _config.blockRingBufferSize;

//@audit `tid` is `uint32`
107:         uint32 tid = blk.verifiedTransitionId;

//@audit `numBlocksVerified` is `uint64`
117:         uint64 numBlocksVerified;

//@audit `lastVerifiedBlockId` is `uint64`
213:                 uint64 lastVerifiedBlockId = b.lastVerifiedBlockId + numBlocksVerified;

//@audit `_lastVerifiedBlockId` is `uint64`
227:         uint64 _lastVerifiedBlockId,

//@audit `lastSyncedBlock` is `uint64`
234:         (uint64 lastSyncedBlock,) = signalService.getSyncedChainData(

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibVerifying.sol#L234)

```solidity
File: /contracts/L1/provers/Guardians.sol

//@audit `_minGuardians` is `uint8`
55:         uint8 _minGuardians

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/provers/Guardians.sol#L55)

```solidity
File: /contracts/L1/tiers/DevnetTierProvider.sol

//@audit `_tierId` is `uint16`
20:     function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {

//@audit `` is `uint16`
54:     function getMinTier(uint256) public pure override returns (uint16) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/tiers/DevnetTierProvider.sol#L54)

```solidity
File: /contracts/L1/tiers/ITierProvider.sol

//@audit `tierId` is `uint16`
22:     function getTier(uint16 tierId) external view returns (Tier memory);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/tiers/ITierProvider.sol#L22)

```solidity
File: /contracts/L1/tiers/MainnetTierProvider.sol

//@audit `_tierId` is `uint16`
20:     function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {

//@audit `` is `uint16`
66:     function getMinTier(uint256 _rand) public pure override returns (uint16) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/tiers/MainnetTierProvider.sol#L66)

```solidity
File: /contracts/L1/tiers/TestnetTierProvider.sol

//@audit `_tierId` is `uint16`
20:     function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {

//@audit `` is `uint16`
66:     function getMinTier(uint256 _rand) public pure override returns (uint16) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/tiers/TestnetTierProvider.sol#L66)

```solidity
File: /contracts/L2/CrossChainOwned.sol

//@audit `txId` is `uint64`
42:         (uint64 txId, bytes memory txdata) = abi.decode(_data, (uint64, bytes));

//@audit `_ownerChainId` is `uint64`
63:         uint64 _ownerChainId

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/CrossChainOwned.sol#L63)

```solidity
File: /contracts/L2/TaikoL2.sol

//@audit `_l1ChainId` is `uint64`
74:         uint64 _l1ChainId,

//@audit `_gasExcess` is `uint64`
75:         uint64 _gasExcess

//@audit `_l1BlockId` is `uint64`
110:         uint64 _l1BlockId,

//@audit `_parentGasUsed` is `uint32`
111:         uint32 _parentGasUsed

//@audit `_l1BlockId` is `uint64`
186:         uint64 _l1BlockId,

//@audit `_parentGasUsed` is `uint32`
187:         uint32 _parentGasUsed

//@audit `_blockId` is `uint64`
200:     function getBlockHash(uint64 _blockId) public view returns (bytes32) {

//@audit `_l1BlockId` is `uint64`
254:         uint64 _l1BlockId,

//@audit `_parentGasUsed` is `uint32`
255:         uint32 _parentGasUsed

//@audit `gasExcess_` is `uint64`
259:         returns (uint256 basefee_, uint64 gasExcess_)

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/TaikoL2.sol#L259)

```solidity
File: /contracts/L2/TaikoL2EIP1559Configurable.sol

//@audit `_newGasExcess` is `uint64`
27:         uint64 _newGasExcess

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/TaikoL2EIP1559Configurable.sol#L27)

```solidity
File: /contracts/automata-attestation/lib/PEMCertChainLib.sol

//@audit `svnValue` is `uint16`
358:             uint16 svnValue = svnValueBytes.length < 2

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/PEMCertChainLib.sol#L358)

```solidity
File: /contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

//@audit `totalQuoteSize` is `uint32`
106:         uint32 totalQuoteSize = 48 // header

//@audit `isvProdIdPackBE` is `uint16`
249:         uint16 isvProdIdPackBE = (enclaveReport.isvProdId >> 8) | (enclaveReport.isvProdId << 8);

//@audit `isvSvnPackBE` is `uint16`
250:         uint16 isvSvnPackBE = (enclaveReport.isvSvn >> 8) | (enclaveReport.isvSvn << 8);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L250)

```solidity
File: /contracts/automata-attestation/utils/Asn1Decode.sol

//@audit `ixFirstContentByte` is `uint80`
189:         uint80 ixFirstContentByte;

//@audit `ixLastContentByte` is `uint80`
190:         uint80 ixLastContentByte;

//@audit `lengthbytesLength` is `uint8`
196:             uint8 lengthbytesLength = uint8(der[ix + 1] & 0x7F);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/Asn1Decode.sol#L196)

```solidity
File: /contracts/automata-attestation/utils/BytesUtils.sol

//@audit `ret` is `uint8`
188:     function readUint8(bytes memory self, uint256 idx) internal pure returns (uint8 ret) {

//@audit `ret` is `uint16`
198:     function readUint16(bytes memory self, uint256 idx) internal pure returns (uint16 ret) {

//@audit `ret` is `uint32`
211:     function readUint32(bytes memory self, uint256 idx) internal pure returns (uint32 ret) {

//@audit `decoded` is `uint8`
332:         uint8 decoded;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/BytesUtils.sol#L332)

```solidity
File: /contracts/automata-attestation/utils/X509DateUtils.sol

//@audit `yrs` is `uint16`
9:         uint16 yrs;

//@audit `mnths` is `uint8`
10:         uint8 mnths;

//@audit `dys` is `uint8`
11:         uint8 dys;

//@audit `hrs` is `uint8`
12:         uint8 hrs;

//@audit `mins` is `uint8`
13:         uint8 mins;

//@audit `secs` is `uint8`
14:         uint8 secs;

//@audit `offset` is `uint8`
15:         uint8 offset;

//@audit `year` is `uint16`
35:         uint16 year,

//@audit `month` is `uint8`
36:         uint8 month,

//@audit `day` is `uint8`
37:         uint8 day,

//@audit `hour` is `uint8`
38:         uint8 hour,

//@audit `minute` is `uint8`
39:         uint8 minute,

//@audit `second` is `uint8`
40:         uint8 second

//@audit `i` is `uint16`
48:         for (uint16 i = 1970; i < year; ++i) {

//@audit `i` is `uint8`
59:         for (uint8 i = 1; i < month; ++i) {

//@audit `year` is `uint16`
71:     function isLeapYear(uint16 year) internal pure returns (bool) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/X509DateUtils.sol#L71)

```solidity
File: /contracts/bridge/Bridge.sol

//@audit `_timestamp` is `uint64`
89:         uint64 _timestamp = _suspend ? type(uint64).max : uint64(block.timestamp);

//@audit `receivedAt` is `uint64`
168:         uint64 receivedAt = proofReceipt[msgHash].receivedAt;

//@audit `receivedAt` is `uint64`
230:         uint64 receivedAt = proofReceipt[msgHash].receivedAt;

//@audit `_chainId` is `uint64`
392:     function isDestChainEnabled(uint64 _chainId)

//@audit `_srcChainId` is `uint64`
541:     function _storeContext(bytes32 _msgHash, address _from, uint64 _srcChainId) private {

//@audit `srcChainId` is `uint64`
559:             uint64 srcChainId;

//@audit `_chainId` is `uint64`
580:         uint64 _chainId,

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L580)

```solidity
File: /contracts/common/AddressManager.sol

//@audit `_chainId` is `uint64`
39:         uint64 _chainId,

//@audit `_chainId` is `uint64`
54:     function getAddress(uint64 _chainId, bytes32 _name) public view override returns (address) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/common/AddressManager.sol#L54)

```solidity
File: /contracts/common/EssentialContract.sol

//@audit `_reentry` is `uint8`
119:     function _storeReentryLock(uint8 _reentry) internal virtual {

//@audit `reentry_` is `uint8`
130:     function _loadReentryLock() internal view virtual returns (uint8 reentry_) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/common/EssentialContract.sol#L130)

```solidity
File: /contracts/common/IAddressManager.sol

//@audit `_chainId` is `uint64`
14:     function getAddress(uint64 _chainId, bytes32 _name) external view returns (address);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/common/IAddressManager.sol#L14)

```solidity
File: /contracts/signal/ISignalService.sol

//@audit `_chainId` is `uint64`
69:         uint64 _chainId,

//@audit `_chainId` is `uint64`
69:         uint64 _chainId,

//@audit `_blockId` is `uint64`
71:         uint64 _blockId,

//@audit `_blockId` is `uint64`
71:         uint64 _blockId,

//@audit `_chainId` is `uint64`
85:         uint64 _chainId,

//@audit `_chainId` is `uint64`
85:         uint64 _chainId,

//@audit `_chainId` is `uint64`
106:         uint64 _chainId,

//@audit `_chainId` is `uint64`
106:         uint64 _chainId,

//@audit `_blockId` is `uint64`
108:         uint64 _blockId,

//@audit `_blockId` is `uint64`
108:         uint64 _blockId,

//@audit `_chainId` is `uint64`
123:         uint64 _chainId,

//@audit `_chainId` is `uint64`
123:         uint64 _chainId,

//@audit `_blockId` is `uint64`
125:         uint64 _blockId

//@audit `_blockId` is `uint64`
125:         uint64 _blockId

//@audit `blockId_` is `uint64`
129:         returns (uint64 blockId_, bytes32 chainData_);

//@audit `blockId_` is `uint64`
129:         returns (uint64 blockId_, bytes32 chainData_);

//@audit `_chainId` is `uint64`
138:         uint64 _chainId,

//@audit `_chainId` is `uint64`
138:         uint64 _chainId,

//@audit `_blockId` is `uint64`
140:         uint64 _blockId

//@audit `_blockId` is `uint64`
140:         uint64 _blockId

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/ISignalService.sol#L140)

```solidity
File: /contracts/signal/SignalService.sol

//@audit `_chainId` is `uint64`
69:         uint64 _chainId,

//@audit `_blockId` is `uint64`
71:         uint64 _blockId,

//@audit `_chainId` is `uint64`
84:         uint64 _chainId,

//@audit `chainId` is `uint64`
97:         uint64 chainId = _chainId;

//@audit `_chainId` is `uint64`
138:         uint64 _chainId,

//@audit `_blockId` is `uint64`
140:         uint64 _blockId,

//@audit `_chainId` is `uint64`
159:         uint64 _chainId,

//@audit `_blockId` is `uint64`
161:         uint64 _blockId

//@audit `blockId_` is `uint64`
165:         returns (uint64 blockId_, bytes32 chainData_)

//@audit `_chainId` is `uint64`
178:         uint64 _chainId,

//@audit `_blockId` is `uint64`
180:         uint64 _blockId

//@audit `_chainId` is `uint64`
195:         uint64 _chainId,

//@audit `_chainId` is `uint64`
207:         uint64 _chainId,

//@audit `_chainId` is `uint64`
236:         uint64 _chainId,

//@audit `_blockId` is `uint64`
238:         uint64 _blockId,

//@audit `_chainId` is `uint64`
273:         uint64 _chainId,

//@audit `_blockId` is `uint64`
274:         uint64 _blockId,

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/SignalService.sol#L274)

```solidity
File: /contracts/team/TimelockTokenPool.sol

//@audit `amountVoided` is `uint128`
152:         uint128 amountVoided = _voidGrant(r.grant);

//@audit `amountOwned` is `uint128`
180:             uint128 amountOwned,

//@audit `amountUnlocked` is `uint128`
181:             uint128 amountUnlocked,

//@audit `amountWithdrawn` is `uint128`
182:             uint128 amountWithdrawn,

//@audit `amountToWithdraw` is `uint128`
183:             uint128 amountToWithdraw,

//@audit `costToWithdraw` is `uint128`
184:             uint128 costToWithdraw

//@audit `_amountUnlocked` is `uint128`
197:         uint128 _amountUnlocked = amountUnlocked / 1e18; // divide first

//@audit `amountToWithdraw` is `uint128`
211:         (,,, uint128 amountToWithdraw, uint128 costToWithdraw) = getMyGrantSummary(_recipient);

//@audit `costToWithdraw` is `uint128`
211:         (,,, uint128 amountToWithdraw, uint128 costToWithdraw) = getMyGrantSummary(_recipient);

//@audit `amountVoided` is `uint128`
225:     function _voidGrant(Grant storage _grant) private returns (uint128 amountVoided) {

//@audit `amountOwned` is `uint128`
226:         uint128 amountOwned = _getAmountOwned(_grant);

//@audit `` is `uint128`
235:     function _getAmountOwned(Grant memory _grant) private view returns (uint128) {

//@audit `` is `uint128`
239:     function _getAmountUnlocked(Grant memory _grant) private view returns (uint128) {

//@audit `_amount` is `uint128`
246:         uint128 _amount,

//@audit `_start` is `uint64`
247:         uint64 _start,

//@audit `_cliff` is `uint64`
248:         uint64 _cliff,

//@audit `_period` is `uint64`
249:         uint64 _period

//@audit `` is `uint128`
253:         returns (uint128)

//@audit `_start` is `uint64`
273:     function _validateCliff(uint64 _start, uint64 _cliff, uint32 _period) private pure {

//@audit `_cliff` is `uint64`
273:     function _validateCliff(uint64 _start, uint64 _cliff, uint32 _period) private pure {

//@audit `_period` is `uint32`
273:     function _validateCliff(uint64 _start, uint64 _cliff, uint32 _period) private pure {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/TimelockTokenPool.sol#L273)

```solidity
File: /contracts/team/airdrop/ERC20Airdrop.sol

//@audit `_claimStart` is `uint64`
29:         uint64 _claimStart,

//@audit `_claimEnd` is `uint64`
30:         uint64 _claimEnd,

//@audit `v` is `uint8`
69:         (address delegatee, uint256 nonce, uint256 expiry, uint8 v, bytes32 r, bytes32 s) =

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC20Airdrop.sol#L69)

```solidity
File: /contracts/team/airdrop/ERC20Airdrop2.sol

//@audit `_claimStart` is `uint64`
56:         uint64 _claimStart,

//@audit `_claimEnd` is `uint64`
57:         uint64 _claimEnd,

//@audit `_withdrawalWindow` is `uint64`
61:         uint64 _withdrawalWindow

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC20Airdrop2.sol#L61)

```solidity
File: /contracts/team/airdrop/ERC721Airdrop.sol

//@audit `_claimStart` is `uint64`
27:         uint64 _claimStart,

//@audit `_claimEnd` is `uint64`
28:         uint64 _claimEnd,

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC721Airdrop.sol#L28)

```solidity
File: /contracts/team/airdrop/MerkleClaimable.sol

//@audit `_claimStart` is `uint64`
46:         uint64 _claimStart,

//@audit `_claimEnd` is `uint64`
47:         uint64 _claimEnd,

//@audit `_claimStart` is `uint64`
57:         uint64 _claimStart,

//@audit `_claimEnd` is `uint64`
58:         uint64 _claimEnd,

//@audit `_claimStart` is `uint64`
90:     function _setConfig(uint64 _claimStart, uint64 _claimEnd, bytes32 _merkleRoot) private {

//@audit `_claimEnd` is `uint64`
90:     function _setConfig(uint64 _claimStart, uint64 _claimEnd, bytes32 _merkleRoot) private {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/MerkleClaimable.sol#L90)

```solidity
File: /contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol

//@audit `_maxCopy` is `uint16`
29:         uint16 _maxCopy,

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L29)

```solidity
File: /contracts/thirdparty/optimism/trie/MerkleTrie.sol

//@audit `branchKey` is `uint8`
134:                     uint8 branchKey = uint8(key[currentKeyIndex]);

//@audit `prefix` is `uint8`
141:                 uint8 prefix = uint8(path[0]);

//@audit `offset` is `uint8`
142:                 uint8 offset = 2 - (prefix % 2);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/trie/MerkleTrie.sol#L142)

```solidity
File: /contracts/tokenvault/BridgedERC20.sol

//@audit `_decimals` is `uint8`
57:         uint8 _decimals,

//@audit `` is `uint8`
117:         returns (uint8)

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC20.sol#L117)

```solidity
File: /contracts/verifiers/SgxVerifier.sol

//@audit `id` is `uint32`
154:         uint32 id = uint32(bytes4(Bytes.slice(_proof.data, 0, 4)));

//@audit `validSince` is `uint64`
204:         uint64 validSince = uint64(block.timestamp);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/SgxVerifier.sol#L204)

</details>

### <a name="GAS-62-1693313026"></a>[GAS-62] The use of a logical AND in place of double if is slightly less gas efficient in instances where there isn't a corresponding else statement for the given if statement
Using a double if statement instead of logical AND (&&) can provide similar short-circuiting behavior whereas double if is slightly more efficient.

*Instances (15)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/hooks/AssignmentHook.sol

120:         if (input.tip != 0 && block.coinbase != address(0)) {
                 address(block.coinbase).sendEther(input.tip);
             }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/hooks/AssignmentHook.sol#L120-L122)

```solidity
File: /contracts/L1/libs/LibProposing.sol

108:         if (params.parentMetaHash != 0 && parentMetaHash != params.parentMetaHash) {
                 revert L1_UNEXPECTED_PARENT();
             }

164:                 if (_config.blobReuseEnabled && params.cacheBlobForReuse) {
                         _state.reusableBlobs[meta_.blobHash] = block.timestamp;
                         emit BlobCached(meta_.blobHash);
                     }

310:             if (proposerOne != address(0) && msg.sender != proposerOne) {
                     return false;
                 }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProposing.sol#L310-L312)

```solidity
File: /contracts/L2/TaikoL2.sol

141:         if (!skipFeeCheck() && block.basefee != basefee) {
                 revert L2_BASEFEE_MISMATCH();
             }

275:             if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {
                     numL1Blocks = _l1BlockId - lastSyncedBlock;
                 }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/TaikoL2.sol#L275-L277)

```solidity
File: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

220:             if (pceSvnIsHigherOrGreater && cpuSvnsAreHigherOrGreater) {
                     status = current.status;
                     bool tcbIsRevoked = status == TCBInfoStruct.TCBStatus.TCB_REVOKED;
                     return (!tcbIsRevoked, status);
                 }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/AutomataDcapV3Attestation.sol#L220-L224)

```solidity
File: /contracts/bridge/Bridge.sol

250:         if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) {
                 // If msg.sender is not the one that proved the message, then there
                 // is an extra delay.
                 unchecked {
                     invocationDelay += invocationExtraDelay;
                 }
             }

260:             if (_message.gasLimit == 0 && msg.sender != _message.destOwner) {
                     revert B_PERMISSION_DENIED();
                 }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L260-L262)

```solidity
File: /contracts/common/EssentialContract.sol

42:         if (msg.sender != owner() && msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/common/EssentialContract.sol#L42-L42)

```solidity
File: /contracts/signal/SignalService.sol

285:         if (cacheStateRoot && _isFullProof && !_isLastHop) {
                 _syncChainData(_chainId, LibSignals.STATE_ROOT, _blockId, _hop.rootHash);
             }

293:         if (cacheSignalRoot && (_isFullProof || !_isLastHop)) {
                 _syncChainData(_chainId, LibSignals.SIGNAL_ROOT, _blockId, _signalRoot);
             }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/SignalService.sol#L293-L295)

```solidity
File: /contracts/team/TimelockTokenPool.sol

277:             if (_cliff > 0 && _cliff <= _start) revert INVALID_GRANT();

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/TimelockTokenPool.sol#L277-L277)

```solidity
File: /contracts/tokenvault/BridgedERC20.sol

38:         if (msg.sender != owner() && msg.sender != snapshooter) {
                revert BTOKEN_UNAUTHORIZED();
            }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC20.sol#L38-L40)

```solidity
File: /contracts/tokenvault/BridgedERC20Base.sol

45:         if (_migratingAddress == migratingAddress && _migratingInbound == migratingInbound) {
                revert BB_INVALID_PARAMS();
            }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC20Base.sol#L45-L47)

</details>

### <a name="GAS-63-1693313038"></a>[GAS-63] Splitting `require()` statements that use `&&` saves gas
See [this issue](https://github.com/code-423n4/2022-01-xdefi-findings/issues/128) which describes the fact that there is a larger deployment gas cost, but with enough runtime calls, the change ends up being cheaper by **3 gas**

*Instances (4)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

77:         require(
                localEnclaveReport.reserved3.length == 96 && localEnclaveReport.reserved4.length == 60
                    && localEnclaveReport.reportData.length == 64,
                "local QE report has wrong length"
            );

82:         require(
                pckSignedQeReport.reserved3.length == 96 && pckSignedQeReport.reserved4.length == 60
                    && pckSignedQeReport.reportData.length == 64,
                "QE report has wrong length"
            );

94:         require(
                v3Quote.v3AuthData.ecdsa256BitSignature.length == 64
                    && v3Quote.v3AuthData.ecdsaAttestationKey.length == 64
                    && v3Quote.v3AuthData.qeReportSignature.length == 64,
                "Invalid ECDSA signature format"
            );

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L94-L99)

```solidity
File: /contracts/automata-attestation/utils/BytesUtils.sol

335:             require(char >= 0x30 && char <= 0x7A, "invalid char");

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/BytesUtils.sol#L335-L335)

</details>

### <a name="GAS-64-1709389408"></a>[GAS-64] Split `revert` checks to save gas
Splitting the conditions into two separate checks [saves](https://gist.github.com/IllIllI000/7e25b0fca6bd9d57d9b9bcb9d2018959) **2 gas**

*Instances (26)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/hooks/AssignmentHook.sol

81:         if (
                block.timestamp > assignment.expiry
                    || assignment.metaHash != 0 && _blk.metaHash != assignment.metaHash
                    || assignment.parentMetaHash != 0 && _meta.parentMetaHash != assignment.parentMetaHash
                    || assignment.maxBlockId != 0 && _meta.id > assignment.maxBlockId
                    || assignment.maxProposedIn != 0 && block.number > assignment.maxProposedIn
            ) {
                revert HOOK_ASSIGNMENT_EXPIRED();
            }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/hooks/AssignmentHook.sol#L81-L89)

```solidity
File: /contracts/L1/libs/LibProposing.sol

195:         if (meta_.txListByteSize == 0 || meta_.txListByteSize > _config.blockMaxTxListBytes) {
                 revert L1_TXLIST_SIZE();
             }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProposing.sol#L195-L197)

```solidity
File: /contracts/L1/libs/LibProving.sol

105:         if (_tran.parentHash == 0 || _tran.blockHash == 0 || _tran.stateRoot == 0) {
                 revert L1_INVALID_TRANSITION();
             }

111:         if (_meta.id <= b.lastVerifiedBlockId || _meta.id >= b.numBlocks) {
                 revert L1_INVALID_BLOCK_ID();
             }

121:         if (blk.blockId != _meta.id || blk.metaHash != keccak256(abi.encode(_meta))) {
                 revert L1_BLOCK_MISMATCH();
             }

134:         if (_proof.tier == 0 || _proof.tier < _meta.minTier || _proof.tier < ts.tier) {
                 revert L1_INVALID_TIER();
             }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProving.sol#L134-L136)

```solidity
File: /contracts/L1/libs/LibUtils.sol

34:         if (_blockId < b.lastVerifiedBlockId || _blockId >= b.numBlocks) {
                revert L1_INVALID_BLOCK_ID();
            }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibUtils.sol#L34-L36)

```solidity
File: /contracts/L1/provers/Guardians.sol

63:         if (_newGuardians.length < MIN_NUM_GUARDIANS || _newGuardians.length > type(uint8).max) {
                revert INVALID_GUARDIAN_SET();
            }

68:         if (_minGuardians < (_newGuardians.length + 1) >> 1 || _minGuardians > _newGuardians.length)
            {
                revert INVALID_MIN_GUARDIANS();
            }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/provers/Guardians.sol#L68-L71)

```solidity
File: /contracts/L2/CrossChainOwned.sol

46:         if (ctx.srcChainId != ownerChainId || ctx.from != owner()) {
                revert XCO_PERMISSION_DENIED();
            }

70:         if (_ownerChainId == 0 || _ownerChainId == block.chainid) {
                revert XCO_INVALID_OWNER_CHAINID();
            }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/CrossChainOwned.sol#L70-L72)

```solidity
File: /contracts/L2/TaikoL2.sol

82:         if (block.chainid <= 1 || block.chainid > type(uint64).max) {
                revert L2_INVALID_CHAIN_ID();
            }

116:         if (
                 _l1BlockHash == 0 || _l1StateRoot == 0 || _l1BlockId == 0
                     || (block.number != 1 && _parentGasUsed == 0)
             ) {
                 revert L2_INVALID_PARAM();
             }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/TaikoL2.sol#L116-L121)

```solidity
File: /contracts/bridge/Bridge.sol

124:         if (_message.srcOwner == address(0) || _message.destOwner == address(0)) {
                 revert B_INVALID_USER();
             }

405:         if (ctx_.msgHash == 0 || ctx_.msgHash == bytes32(PLACEHOLDER)) {
                 revert B_INVALID_CONTEXT();
             }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L405-L407)

```solidity
File: /contracts/libs/Lib4844.sol

57:         if (uint256(first) != FIELD_ELEMENTS_PER_BLOB || uint256(second) != BLS_MODULUS) {
                revert EVAL_FAILED_2();
            }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/libs/Lib4844.sol#L57-L59)

```solidity
File: /contracts/signal/SignalService.sol

114:                 if (hop.chainId == 0 || hop.chainId == block.chainid) {
                         revert SS_INVALID_MID_HOP_CHAINID();
                     }

131:         if (value == 0 || value != _loadSignalValue(address(this), signal)) {
                 revert SS_SIGNAL_NOT_FOUND();
             }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/SignalService.sol#L131-L133)

```solidity
File: /contracts/team/airdrop/ERC20Airdrop2.sol

40:         if (claimEnd > block.timestamp || claimEnd + withdrawalWindow < block.timestamp) {
                revert WITHDRAWALS_NOT_ONGOING();
            }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC20Airdrop2.sol#L40-L42)

```solidity
File: /contracts/team/airdrop/MerkleClaimable.sol

34:         if (
                merkleRoot == 0x0 || claimStart == 0 || claimEnd == 0 || claimStart > block.timestamp
                    || claimEnd < block.timestamp
            ) revert CLAIM_NOT_ONGOING();

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/MerkleClaimable.sol#L34-L37)

```solidity
File: /contracts/tokenvault/ERC1155Vault.sol

108:         if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC1155Vault.sol#L108-L108)

```solidity
File: /contracts/tokenvault/ERC20Vault.sol

158:         if (_btokenNew == address(0) || bridgedToCanonical[_btokenNew].addr != address(0)) {
                 revert VAULT_INVALID_NEW_BTOKEN();
             }

174:             if (
                     ctoken.decimals != _ctoken.decimals
                         || keccak256(bytes(ctoken.symbol)) != keccak256(bytes(_ctoken.symbol))
                         || keccak256(bytes(ctoken.name)) != keccak256(bytes(_ctoken.name))
                 ) revert VAULT_CTOKEN_MISMATCH();

267:         if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC20Vault.sol#L267-L267)

```solidity
File: /contracts/tokenvault/ERC721Vault.sol

91:         if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC721Vault.sol#L91-L91)

```solidity
File: /contracts/tokenvault/LibBridgedToken.sol

20:         if (
                _srcToken == address(0) || _srcChainId == 0 || _srcChainId == block.chainid
                    || bytes(_symbol).length == 0 || bytes(_name).length == 0
            ) {
                revert BTOKEN_INVALID_PARAMS();
            }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/LibBridgedToken.sol#L20-L25)

</details>

### <a name="GAS-65-1693313099"></a>[GAS-65] Cache state variables outside of loop to avoid reading storage on every iteration
Reading from storage should always try to be avoided within loops.In the following instances, we are able to cache state variables outside of the loop to save a Gwarmaccess(100 gas) per loop iteration.

Note: Due to stack too deep errors, we will not be able to cache all the state variables read within the loops.

*Instances (7)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/provers/Guardians.sol

//@audit `minGuardians` is a state variable, try to cache it outside the loop
135:                 if (count == minGuardians) return true;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/provers/Guardians.sol#L135)

```solidity
File: /contracts/team/airdrop/ERC721Airdrop.sol

//@audit `vault` is a state variable, try to cache it outside the loop
60:             IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);

//@audit `token` is a state variable, try to cache it outside the loop
60:             IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC721Airdrop.sol#L60)

```solidity
File: /contracts/verifiers/SgxVerifier.sol

//@audit `nextInstanceId` is a state variable, try to cache it outside the loop
217:             instances[nextInstanceId] = Instance(_instances[i], validSince);

//@audit `nextInstanceId` is a state variable, try to cache it outside the loop
218:             ids[i] = nextInstanceId;

//@audit `nextInstanceId` is a state variable, try to cache it outside the loop
220:             emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);

//@audit `nextInstanceId` is a state variable, try to cache it outside the loop
222:             nextInstanceId++;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/SgxVerifier.sol#L222)

</details>

### <a name="GAS-66-1693311457"></a>[GAS-66] State variable read in a loop
The state variable should be cached in a local variable rather than reading it on every iteration of the for-loop, which will replace each Gwarmaccess (**100 gas**) with a much cheaper stack read.

*Instances (7)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/provers/Guardians.sol

//@audit `minGuardians` is read in this loop
133:             for (uint256 i; i < guardiansLength; ++i) {
                     if (bits & 1 == 1) ++count;
                     if (count == minGuardians) return true;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/provers/Guardians.sol#L133-L135)

```solidity
File: /contracts/team/airdrop/ERC721Airdrop.sol

//@audit `vault` is read in this loop
59:         for (uint256 i; i < tokenIds.length; ++i) {
                IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);

//@audit `token` is read in this loop
59:         for (uint256 i; i < tokenIds.length; ++i) {
                IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC721Airdrop.sol#L59-L60)

```solidity
File: /contracts/verifiers/SgxVerifier.sol

//@audit `nextInstanceId` is read in this loop
210:         for (uint256 i; i < _instances.length; ++i) {
                 if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();
     
                 addressRegistered[_instances[i]] = true;
     
                 if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();
     
                 instances[nextInstanceId] = Instance(_instances[i], validSince);
                 ids[i] = nextInstanceId;

//@audit `nextInstanceId` is read in this loop
210:         for (uint256 i; i < _instances.length; ++i) {
                 if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();
     
                 addressRegistered[_instances[i]] = true;
     
                 if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();
     
                 instances[nextInstanceId] = Instance(_instances[i], validSince);
                 ids[i] = nextInstanceId;
     
                 emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);

//@audit `nextInstanceId` is read in this loop
210:         for (uint256 i; i < _instances.length; ++i) {
                 if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();
     
                 addressRegistered[_instances[i]] = true;
     
                 if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();
     
                 instances[nextInstanceId] = Instance(_instances[i], validSince);
                 ids[i] = nextInstanceId;
     
                 emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);
     
                 nextInstanceId++;

//@audit `nextInstanceId` is read in this loop
210:         for (uint256 i; i < _instances.length; ++i) {
                 if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();
     
                 addressRegistered[_instances[i]] = true;
     
                 if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();
     
                 instances[nextInstanceId] = Instance(_instances[i], validSince);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/SgxVerifier.sol#L210-L217)

</details>

### <a name="GAS-67-1693313054"></a>[GAS-67] State variables only set in the constructor should be declared `immutable`
Avoids a Gsset(** 20000 gas**) in the constructor, and replaces the first access in each transaction(Gcoldsload - ** 2100 gas **) and each access thereafter(Gwarmacces - ** 100 gas **) with a`PUSH32`(** 3 gas **).

While`string`s are not value types, and therefore cannot be`immutable` / `constant` if not hard - coded outside of the constructor, the same behavior can be achieved by making the current contract `abstract` with `virtual` functions for the`string` accessors, and having a child contract override the functions with the hard - coded implementation - specific values.

*Instances (2)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

57:         owner = msg.sender;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/AutomataDcapV3Attestation.sol#L57)

```solidity
File: /contracts/automata-attestation/utils/SigVerifyLib.sol

21:         ES256VERIFIER = es256Verifier;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/SigVerifyLib.sol#L21)

</details>

### <a name="GAS-68-1693313071"></a>[GAS-68] Stack variable used as a cheaper cache for a state variable is only used once
If the variable is only accessed once, it's cheaper to use the state variable directly that one time, and save the **3 gas** the extra stack assignment would spend. However, if it used as a parameter in an event emit, then caching it will help reduce gas by at least ***10 gas***

*Instances (170)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/TaikoL1.sol

/// @audit `tran`, `proof`,  are used only once
84:         (
                TaikoData.BlockMetadata memory meta,
                TaikoData.Transition memory tran,
                TaikoData.TierProof memory proof
            ) = abi.decode(_input, (TaikoData.BlockMetadata, TaikoData.Transition, TaikoData.TierProof));

/// @audit `maxBlocksToVerify`,  are used only once
94:         uint8 maxBlocksToVerify = LibProving.proveBlock(state, config, this, meta, tran, proof);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/TaikoL1.sol#L94-L94)

```solidity
File: /contracts/L1/hooks/AssignmentHook.sol

/// @audit `hash`,  are used only once
94:         bytes32 hash = hashAssignment(assignment, taikoL1Address, _meta.blobHash);

/// @audit `tko`,  are used only once
101:         IERC20 tko = IERC20(resolve("taiko_token", false));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/hooks/AssignmentHook.sol#L101-L101)

```solidity
File: /contracts/L1/libs/LibDepositing.sol

/// @audit `slot`,  are used only once
45:         uint256 slot = _state.slotA.numEthDeposits % _config.ethDepositRingBufferSize;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibDepositing.sol#L45-L45)

```solidity
File: /contracts/L1/libs/LibProposing.sol

/// @audit `tkoBalance`,  are used only once
238:             uint256 tkoBalance = tko.balanceOf(address(this));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProposing.sol#L238-L238)

```solidity
File: /contracts/L1/libs/LibProving.sol

/// @audit `tid`,  are used only once
129:         (uint32 tid, TaikoData.TransitionState storage ts) =
                 _createTransition(_state, blk, _tran, slot);

/// @audit `isContesting`,  are used only once
164:                 bool isContesting = _proof.tier == ts.tier && tier.contestBond != 0;

/// @audit `ctx`,  are used only once
166:                 IVerifier.Context memory ctx = IVerifier.Context({
                         metaHash: blk.metaHash,
                         blobHash: _meta.blobHash,
                         // Separate msgSender to allow the prover to be any address in the future.
                         prover: msg.sender,
                         msgSender: msg.sender,
                         blockId: blk.blockId,
                         isContesting: isContesting,
                         blobUsed: _meta.blobUsed
                     });

/// @audit `returnLivenessBond`,  are used only once
192:             bool returnLivenessBond = blk.livenessBond > 0 && _proof.data.length == 32
                     && bytes32(_proof.data) == RETURN_LIVENESS_BOND;

/// @audit `inProvingWindow`,  are used only once
414:         bool inProvingWindow = uint256(_ts.timestamp).max(_state.slotB.lastUnpausedAt)
                 + _tier.provingWindow * 60 >= block.timestamp;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProving.sol#L414-L415)

```solidity
File: /contracts/L1/libs/LibVerifying.sol

/// @audit `tko`,  are used only once
188:                 IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));

/// @audit `lastSyncedBlock`,  are used only once
234:         (uint64 lastSyncedBlock,) = signalService.getSyncedChainData(
                 _config.chainId, LibSignals.STATE_ROOT, 0 /* latest block Id*/
             );

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibVerifying.sol#L234-L236)

```solidity
File: /contracts/L1/provers/Guardians.sol

/// @audit `guardiansLength`,  are used only once
131:         uint256 guardiansLength = guardians.length;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/provers/Guardians.sol#L131-L131)

```solidity
File: /contracts/L2/CrossChainOwned.sol

/// @audit `txId`,  are used only once
42:         (uint64 txId, bytes memory txdata) = abi.decode(_data, (uint64, bytes));

/// @audit `success`,  are used only once
50:         (bool success,) = address(this).call(txdata);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/CrossChainOwned.sol#L50-L50)

```solidity
File: /contracts/L2/TaikoL2.sol

/// @audit `publicInputHashOld`, `publicInputHashNew`,  are used only once
131:         (bytes32 publicInputHashOld, bytes32 publicInputHashNew) = _calcPublicInputHash(parentId);

/// @audit `config`,  are used only once
136:         Config memory config = getConfig();

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/TaikoL2.sol#L136-L136)

```solidity
File: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

/// @audit `success`,  are used only once
139:         (bool success,) = _verify(data);

/// @audit `retData`,  are used only once
163:         bytes memory retData = abi.encodePacked(INVALID_EXIT_CODE);

/// @audit `successful`, `parsedV3Quote`,  are used only once
166:         (bool successful, V3Struct.ParsedV3QuoteStruct memory parsedV3Quote) =
                 V3Parser.parseInput(quote, address(pemCertLib));

/// @audit `miscselectMatched`,  are used only once
181:         bool miscselectMatched =
                 quoteEnclaveReport.miscSelect & enclaveId.miscselectMask == enclaveId.miscselect;

/// @audit `attributesMatched`,  are used only once
184:         bool attributesMatched =
                 quoteEnclaveReport.attributes & enclaveId.attributesMask == enclaveId.attributes;

/// @audit `mrsignerMatched`,  are used only once
186:         bool mrsignerMatched = quoteEnclaveReport.mrSigner == enclaveId.mrsigner;

/// @audit `isvprodidMatched`,  are used only once
188:         bool isvprodidMatched = quoteEnclaveReport.isvProdId == enclaveId.isvprodid;

/// @audit `pceSvnIsHigherOrGreater`,  are used only once
216:             bool pceSvnIsHigherOrGreater = pck.sgxExtension.pcesvn >= current.pcesvn;

/// @audit `cpuSvnsAreHigherOrGreater`,  are used only once
217:             bool cpuSvnsAreHigherOrGreater = _isCpuSvnHigherOrGreater(
                     pck.sgxExtension.sgxTcbCompSvnArr, current.sgxTcbCompSvnArr
                 );

/// @audit `tcbIsRevoked`,  are used only once
222:                 bool tcbIsRevoked = status == TCBInfoStruct.TCBStatus.TCB_REVOKED;

/// @audit `issuerPubKeyHash`,  are used only once
292:             bytes32 issuerPubKeyHash = keccak256(issuer.pubKey);

/// @audit `expectedAuthDataHash`,  are used only once
313:         bytes32 expectedAuthDataHash = bytes32(qeEnclaveReport.reportData.substring(0, 32));

/// @audit `concatOfAttestKeyAndQeAuthData`,  are used only once
314:         bytes memory concatOfAttestKeyAndQeAuthData =
                 abi.encodePacked(authDataV3.ecdsaAttestationKey, authDataV3.qeAuthData.data);

/// @audit `computedAuthDataHash`,  are used only once
316:         bytes32 computedAuthDataHash = sha256(concatOfAttestKeyAndQeAuthData);

/// @audit `qeReportDataIsValid`,  are used only once
318:         bool qeReportDataIsValid = expectedAuthDataHash == computedAuthDataHash;

/// @audit `pckSignedQeReportBytes`,  are used only once
320:             bytes memory pckSignedQeReportBytes =
                     V3Parser.packQEReport(authDataV3.pckSignedQeReport);

/// @audit `qeSigVerified`,  are used only once
322:             bool qeSigVerified = sigVerifyLib.verifyES256Signature(
                     pckSignedQeReportBytes, authDataV3.qeReportSignature, pckCertPubKey
                 );

/// @audit `quoteSigVerified`,  are used only once
325:             bool quoteSigVerified = sigVerifyLib.verifyES256Signature(
                     signedQuoteData, authDataV3.ecdsa256BitSignature, authDataV3.ecdsaAttestationKey
                 );

/// @audit `successful`, `signedQuoteData`,  are used only once
372:         (
                 bool successful,
                 ,
                 ,
                 bytes memory signedQuoteData,
                 V3Struct.ECDSAQuoteV3AuthData memory authDataV3
             ) = V3Parser.validateParsedInput(v3quote);

/// @audit `mrEnclaveIsTrusted`,  are used only once
387:                 bool mrEnclaveIsTrusted =
                         _trustedUserMrEnclave[v3quote.localEnclaveReport.mrEnclave];

/// @audit `mrSignerIsTrusted`,  are used only once
389:                 bool mrSignerIsTrusted = _trustedUserMrSigner[v3quote.localEnclaveReport.mrSigner];

/// @audit `isPckCert`,  are used only once
421:                 bool isPckCert = i == 0; // additional parsing for PCKCert

/// @audit `tcbConfigured`,  are used only once
437:             bool tcbConfigured = LibString.eq(parsedFmspc, fetchedTcbInfo.fmspc);

/// @audit `pckCert`,  are used only once
442:             IPEMCertChainLib.ECSha256Certificate memory pckCert = parsedQuoteCerts[0];

/// @audit `pceidMatched`,  are used only once
443:             bool pceidMatched = LibString.eq(pckCert.pck.sgxExtension.pceid, fetchedTcbInfo.pceid);

/// @audit `pckCertChainVerified`,  are used only once
463:             bool pckCertChainVerified = _verifyCertChain(parsedQuoteCerts);

/// @audit `enclaveReportSigsVerified`,  are used only once
471:             bool enclaveReportSigsVerified = _enclaveReportSigVerification(
                     parsedQuoteCerts[0].pubKey,
                     signedQuoteData,
                     authDataV3,
                     v3quote.v3AuthData.pckSignedQeReport
                 );

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/AutomataDcapV3Attestation.sol#L471-L476)

```solidity
File: /contracts/automata-attestation/lib/PEMCertChainLib.sol

/// @audit `len`,  are used only once
52:         uint256 len = pemChain.length;

/// @audit `root`,  are used only once
82:         uint256 root = der.root();

/// @audit `serialNumBytes`,  are used only once
107:             bytes memory serialNumBytes = der.bytesAt(tbsPtr);

/// @audit `issuerNameIsValid`,  are used only once
120:             bool issuerNameIsValid = LibString.eq(cert.pck.issuerName, PLATFORM_ISSUER_NAME)
                     || LibString.eq(cert.pck.issuerName, PROCESSOR_ISSUER_NAME);

/// @audit `sigX`,  are used only once
174:             bytes memory sigX = _trimBytes(der.bytesAt(sigPtr), 32);

/// @audit `sigY`,  are used only once
177:             bytes memory sigY = _trimBytes(der.bytesAt(sigPtr), 32);

/// @audit `headerFound`,  are used only once
225:         bool headerFound = beginPos != LibString.NOT_FOUND;

/// @audit `footerFound`,  are used only once
226:         bool footerFound = endPos != LibString.NOT_FOUND;

/// @audit `contentStart`,  are used only once
233:         uint256 contentStart = beginPos + HEADER_LENGTH;

/// @audit `delimiter`,  are used only once
239:         bytes memory delimiter = hex"0a";

/// @audit `contentSlice`,  are used only once
240:         string memory contentSlice = LibString.slice(pemData, contentStart, endPos);

/// @audit `lengthDiff`,  are used only once
265:         uint256 lengthDiff = n - expectedLength;

/// @audit `pceidPtr`,  are used only once
312:                         uint256 pceidPtr = der.nextSiblingOf(extnValueOidPtr);

/// @audit `fmspcPtr`,  are used only once
318:                         uint256 fmspcPtr = der.nextSiblingOf(extnValueOidPtr);

/// @audit `tcbPtr`,  are used only once
350:         uint256 tcbPtr = der.nextSiblingOf(oidPtr);

/// @audit `svnValuePtr`,  are used only once
356:             uint256 svnValuePtr = der.nextSiblingOf(svnPtr); // value

/// @audit `cpusvn`,  are used only once
366:                 uint256 cpusvn = uint256(svnValue);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/PEMCertChainLib.sol#L366-L366)

```solidity
File: /contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

/// @audit `rawHeader`,  are used only once
38:         bytes memory rawHeader = quote.substring(0, 48);

/// @audit `headerVerifiedSuccessfully`, `header`,  are used only once
39:         (bool headerVerifiedSuccessfully, V3Struct.Header memory header) =
                parseAndVerifyHeader(rawHeader);

/// @audit `authDataVerifiedSuccessfully`, `authDataV3`,  are used only once
45:         (bool authDataVerifiedSuccessfully, V3Struct.ECDSAQuoteV3AuthData memory authDataV3) =
                parseAuthDataAndVerifyCertType(quote.substring(436, localAuthDataSize), pemCertLibAddr);

/// @audit `rawLocalEnclaveReport`,  are used only once
51:         bytes memory rawLocalEnclaveReport = quote.substring(48, 384);

/// @audit `localEnclaveReport`,  are used only once
52:         V3Struct.EnclaveReport memory localEnclaveReport = parseEnclaveReport(rawLocalEnclaveReport);

/// @audit `totalQuoteSize`,  are used only once
106:         uint32 totalQuoteSize = 48 // header
                 + 384 // local QE report
                 + 64 // ecdsa256BitSignature
                 + 64 // ecdsaAttestationKey
                 + 384 // QE report
                 + 64 // qeReportSignature
                 + 2 // sizeof(v3Quote.v3AuthData.qeAuthData.parsedDataSize)
                 + v3Quote.v3AuthData.qeAuthData.parsedDataSize + 2 // sizeof(v3Quote.v3AuthData.certification.certType)
                 + 4 // sizeof(v3Quote.v3AuthData.certification.certDataSize)
                 + v3Quote.v3AuthData.certification.certDataSize;

/// @audit `headerBytes`,  are used only once
119:         bytes memory headerBytes = abi.encodePacked(
                 header.version,
                 header.attestationKeyType,
                 header.teeType,
                 header.qeSvn,
                 header.pceSvn,
                 header.qeVendorId,
                 header.userData
             );

/// @audit `upperDigit`,  are used only once
155:             uint256 upperDigit = digits / 16;

/// @audit `lowerDigit`,  are used only once
156:             uint256 lowerDigit = digits % 16;

/// @audit `certData`,  are used only once
224:         bytes memory certData = rawAuthData.substring(offset, cert.certDataSize);

/// @audit `rawQeReport`,  are used only once
229:         bytes memory rawQeReport = rawAuthData.substring(128, 384);

/// @audit `isvProdIdPackBE`,  are used only once
249:         uint16 isvProdIdPackBE = (enclaveReport.isvProdId >> 8) | (enclaveReport.isvProdId << 8);

/// @audit `isvSvnPackBE`,  are used only once
250:         uint16 isvSvnPackBE = (enclaveReport.isvSvn >> 8) | (enclaveReport.isvSvn << 8);

/// @audit `pemCertLib`,  are used only once
275:         IPEMCertChainLib pemCertLib = PEMCertChainLib(pemCertLibAddr);

/// @audit `parsedQuoteCerts`,  are used only once
276:         IPEMCertChainLib.ECSha256Certificate[] memory parsedQuoteCerts;

/// @audit `certParsedSuccessfully`,  are used only once
277:         (bool certParsedSuccessfully, bytes[] memory quoteCerts) =
                 pemCertLib.splitCertificateChain(certBytes, 3);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L277-L278)

```solidity
File: /contracts/automata-attestation/utils/Asn1Decode.sol

/// @audit `valueLength`,  are used only once
183:         uint256 valueLength = ptr.ixl() + 1 - ptr.ixf();

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/Asn1Decode.sol#L183-L183)

```solidity
File: /contracts/automata-attestation/utils/BytesUtils.sol

/// @audit `selfptr`,  are used only once
73:         uint256 selfptr;

/// @audit `otherptr`,  are used only once
74:         uint256 otherptr;

/// @audit `ret`,  are used only once
295:         bytes memory ret = new bytes(len);

/// @audit `dest`,  are used only once
296:         uint256 dest;

/// @audit `src`,  are used only once
297:         uint256 src;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/BytesUtils.sol#L297-L297)

```solidity
File: /contracts/automata-attestation/utils/RsaVerify.sol

/// @audit `input`,  are used only once
93:         bytes memory input =
                bytes.concat(bytes32(_s.length), bytes32(_e.length), bytes32(_m.length), _s, _e, _m);

/// @audit `inputlen`,  are used only once
95:         uint256 inputlen = input.length;

/// @audit `input`,  are used only once
241:         bytes memory input =
                 bytes.concat(bytes32(_s.length), bytes32(_e.length), bytes32(_m.length), _s, _e, _m);

/// @audit `inputlen`,  are used only once
243:         uint256 inputlen = input.length;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/RsaVerify.sol#L243-L243)

```solidity
File: /contracts/automata-attestation/utils/SigVerifyLib.sol

/// @audit `exponent`,  are used only once
89:         bytes memory exponent = publicKey.substring(0, 3);

/// @audit `modulus`,  are used only once
90:         bytes memory modulus = publicKey.substring(3, publicKey.length - 3);

/// @audit `exponent`,  are used only once
106:         bytes memory exponent = publicKey.substring(0, 3);

/// @audit `modulus`,  are used only once
107:         bytes memory modulus = publicKey.substring(3, publicKey.length - 3);

/// @audit `r`,  are used only once
126:         uint256 r = uint256(bytes32(signature.substring(0, 32)));

/// @audit `s`,  are used only once
127:         uint256 s = uint256(bytes32(signature.substring(32, 32)));

/// @audit `gx`,  are used only once
132:         uint256 gx = uint256(bytes32(publicKey.substring(0, 32)));

/// @audit `gy`,  are used only once
133:         uint256 gy = uint256(bytes32(publicKey.substring(32, 32)));

/// @audit `args`,  are used only once
136:         bytes memory args = abi.encode(sha256(tbs), r, s, gx, gy);

/// @audit `success`, `ret`,  are used only once
137:         (bool success, bytes memory ret) = ES256VERIFIER.staticcall(args);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/SigVerifyLib.sol#L137-L137)

```solidity
File: /contracts/bridge/Bridge.sol

/// @audit `_timestamp`,  are used only once
89:         uint64 _timestamp = _suspend ? type(uint64).max : uint64(block.timestamp);

/// @audit `destChainEnabled`,  are used only once
129:         (bool destChainEnabled,) = isDestChainEnabled(_message.destChainId);

/// @audit `expectedAmount`,  are used only once
138:         uint256 expectedAmount = _message.value + _message.fee;

/// @audit `failureSignal`,  are used only once
178:             bytes32 failureSignal = signalForFailedMessage(msgHash);

/// @audit `invocationDelay`,  are used only once
187:         (uint256 invocationDelay,) = getInvocationDelays();

/// @audit `invocationExtraDelay`,  are used only once
233:         (uint256 invocationDelay, uint256 invocationExtraDelay) = getInvocationDelays();

/// @audit `gasLimit`,  are used only once
280:                 uint256 gasLimit = msg.sender == _message.destOwner ? gasleft() : _message.gasLimit;

/// @audit `msgHash`,  are used only once
557:             bytes32 msgHash;

/// @audit `from`,  are used only once
558:             address from;

/// @audit `srcChainId`,  are used only once
559:             uint64 srcChainId;

/// @audit `data`,  are used only once
587:         bytes memory data = abi.encodeCall(
                 ISignalService.proveSignalReceived,
                 (_chainId, resolve(_chainId, "bridge", false), _signal, _proof)
             );

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L587-L590)

```solidity
File: /contracts/libs/Lib4844.sol

/// @audit `ok`, `ret`,  are used only once
43:         (bool ok, bytes memory ret) = POINT_EVALUATION_PRECOMPILE_ADDRESS.staticcall(
                abi.encodePacked(_blobHash, _x, _y, _commitment, _pointProof)
            );

/// @audit `first`,  are used only once
51:         bytes32 first;

/// @audit `second`,  are used only once
52:         bytes32 second;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/libs/Lib4844.sol#L52-L52)

```solidity
File: /contracts/libs/LibAddress.sol

/// @audit `success`,  are used only once
27:         (bool success,) = ExcessivelySafeCall.excessivelySafeCall(
                _to,
                _gasLimit,
                _amount,
                64, // return max 64 bytes
                ""
            );

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/libs/LibAddress.sol#L27-L33)

```solidity
File: /contracts/libs/LibTrieProof.sol

/// @audit `accountState`,  are used only once
52:             RLPReader.RLPItem[] memory accountState = RLPReader.readList(rlpAccount);

/// @audit `verified`,  are used only once
60:         bool verified = SecureMerkleTrie.verifyInclusionProof(
                bytes.concat(_slot), RLPWriter.writeUint(uint256(_value)), _storageProof, storageRoot_
            );

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/libs/LibTrieProof.sol#L60-L62)

```solidity
File: /contracts/signal/SignalService.sol

/// @audit `signalRoot`,  are used only once
107:             bytes32 signalRoot = _verifyHopProof(chainId, app, signal, value, hop, signalService);

/// @audit `kind`,  are used only once
124:             bytes32 kind = isFullProof ? LibSignals.STATE_ROOT : LibSignals.SIGNAL_ROOT;

/// @audit `signal`,  are used only once
148:         bytes32 signal = signalForChainData(_chainId, _kind, _blockId);

/// @audit `signal`,  are used only once
170:             bytes32 signal = signalForChainData(_chainId, _kind, blockId_);

/// @audit `cacheStateRoot`,  are used only once
282:         bool cacheStateRoot = _hop.cacheOption == CacheOption.CACHE_BOTH
                 || _hop.cacheOption == CacheOption.CACHE_STATE_ROOT;

/// @audit `cacheSignalRoot`,  are used only once
290:         bool cacheSignalRoot = _hop.cacheOption == CacheOption.CACHE_BOTH
                 || _hop.cacheOption == CacheOption.CACHE_SIGNAL_ROOT;

/// @audit `slot`,  are used only once
308:         bytes32 slot = getSignalSlot(uint64(block.chainid), _app, _signal);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/SignalService.sol#L308-L308)

```solidity
File: /contracts/team/TimelockTokenPool.sol

/// @audit `r`,  are used only once
151:         Recipient storage r = recipients[_recipient];

/// @audit `hash`,  are used only once
170:         bytes32 hash = keccak256(abi.encodePacked("Withdraw unlocked Taiko token to: ", _to));

/// @audit `recipient`,  are used only once
171:         address recipient = ECDSA.recover(hash, _sig);

/// @audit `_amountUnlocked`,  are used only once
197:         uint128 _amountUnlocked = amountUnlocked / 1e18; // divide first

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/TimelockTokenPool.sol#L197-L197)

```solidity
File: /contracts/team/airdrop/ERC20Airdrop.sol

/// @audit `delegatee`, `nonce`, `expiry`, `v`, `r`, `s`,  are used only once
69:         (address delegatee, uint256 nonce, uint256 expiry, uint8 v, bytes32 r, bytes32 s) =
                abi.decode(delegationData, (address, uint256, uint256, uint8, bytes32, bytes32));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC20Airdrop.sol#L69-L70)

```solidity
File: /contracts/team/airdrop/ERC20Airdrop2.sol

/// @audit `timeBasedAllowance`,  are used only once
117:         uint256 timeBasedAllowance = balance
                 * (block.timestamp.min(claimEnd + withdrawalWindow) - claimEnd) / withdrawalWindow;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC20Airdrop2.sol#L117-L118)

```solidity
File: /contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol

/// @audit `_toCopy`,  are used only once
36:         uint256 _toCopy;

/// @audit `_success`,  are used only once
37:         bool _success;

/// @audit `_returnData`,  are used only once
38:         bytes memory _returnData = new bytes(_maxCopy);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L38-L38)

```solidity
File: /contracts/thirdparty/optimism/Bytes.sol

/// @audit `tempBytes`,  are used only once
30:         bytes memory tempBytes;

/// @audit `_nibbles`,  are used only once
103:         bytes memory _nibbles;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/Bytes.sol#L103-L103)

```solidity
File: /contracts/thirdparty/optimism/rlp/RLPReader.sol

/// @audit `ptr`,  are used only once
42:         MemoryPointer ptr;

/// @audit `listLength`, `itemType`,  are used only once
54:         (uint256 listOffset, uint256 listLength, RLPItemType itemType) = _decodeLength(_in);

/// @audit `itemType`,  are used only once
110:         (uint256 itemOffset, uint256 itemLength, RLPItemType itemType) = _decodeLength(_in);

/// @audit `ptr`,  are used only once
157:         MemoryPointer ptr = _in.ptr;

/// @audit `src`,  are used only once
294:         uint256 src = MemoryPointer.unwrap(_src) + _offset;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/rlp/RLPReader.sol#L294-L294)

```solidity
File: /contracts/thirdparty/optimism/trie/MerkleTrie.sol

/// @audit `branchKey`,  are used only once
134:                     uint8 branchKey = uint8(key[currentKeyIndex]);

/// @audit `nextNode`,  are used only once
135:                     RLPReader.RLPItem memory nextNode = currentNode.decoded[branchKey];

/// @audit `offset`,  are used only once
142:                 uint8 offset = 2 - (prefix % 2);

/// @audit `max`,  are used only once
243:         uint256 max = (_a.length < _b.length) ? _a.length : _b.length;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/trie/MerkleTrie.sol#L243-L243)

```solidity
File: /contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol

/// @audit `key`,  are used only once
29:         bytes memory key = _getSecureKey(_key);

/// @audit `key`,  are used only once
47:         bytes memory key = _getSecureKey(_key);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L47-L47)

```solidity
File: /contracts/tokenvault/BaseVault.sol

/// @audit `selfOnSourceChain`,  are used only once
54:         address selfOnSourceChain = resolve(ctx_.srcChainId, name(), false);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BaseVault.sol#L54-L54)

```solidity
File: /contracts/tokenvault/ERC1155Vault.sol

/// @audit `data`, `ctoken`,  are used only once
55:         (bytes memory data, CanonicalNFT memory ctoken) = _handleMessage(msg.sender, _op);

/// @audit `message`,  are used only once
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
            });

/// @audit `from`,  are used only once
94:         (
                CanonicalNFT memory ctoken,
                address from,
                address to,
                uint256[] memory tokenIds,
                uint256[] memory amounts
            ) = abi.decode(data, (CanonicalNFT, address, address, uint256[], uint256[]));

/// @audit `token`,  are used only once
111:         address token = _transferTokens(ctoken, to, tokenIds, amounts);

/// @audit `data`,  are used only once
140:         (bytes memory data) = abi.decode(message.data[4:], (bytes));

/// @audit `token`,  are used only once
145:         address token = _transferTokens(ctoken, message.srcOwner, tokenIds, amounts);

/// @audit `data`,  are used only once
304:         bytes memory data = abi.encodeCall(
                 BridgedERC1155.init,
                 (owner(), addressManager, _ctoken.addr, _ctoken.chainId, _ctoken.symbol, _ctoken.name)
             );

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC1155Vault.sol#L304-L307)

```solidity
File: /contracts/tokenvault/ERC20Vault.sol

/// @audit `data`, `ctoken`, `balanceChange`,  are used only once
218:         (bytes memory data, CanonicalERC20 memory ctoken, uint256 balanceChange) =
                 _handleMessage(msg.sender, _op.token, _op.to, _op.amount);

/// @audit `message`,  are used only once
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
             });

/// @audit `from`,  are used only once
259:         (CanonicalERC20 memory ctoken, address from, address to, uint256 amount) =
                 abi.decode(_data, (CanonicalERC20, address, address, uint256));

/// @audit `token`,  are used only once
270:         address token = _transferTokens(ctoken, to, amount);

/// @audit `data`,  are used only once
298:         (bytes memory data) = abi.decode(_message.data[4:], (bytes));

/// @audit `token`,  are used only once
303:         address token = _transferTokens(ctoken, _message.srcOwner, amount);

/// @audit `_balance`,  are used only once
378:             uint256 _balance = t.balanceOf(address(this));

/// @audit `data`,  are used only once
408:         bytes memory data = abi.encodeCall(
                 BridgedERC20.init,
                 (
                     owner(),
                     addressManager,
                     ctoken.addr,
                     ctoken.chainId,
                     ctoken.decimals,
                     ctoken.symbol,
                     ctoken.name
                 )
             );

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC20Vault.sol#L408-L419)

```solidity
File: /contracts/tokenvault/ERC721Vault.sol

/// @audit `data`, `ctoken`,  are used only once
42:         (bytes memory data, CanonicalNFT memory ctoken) = _handleMessage(msg.sender, _op);

/// @audit `message`,  are used only once
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
            });

/// @audit `from`,  are used only once
83:         (CanonicalNFT memory ctoken, address from, address to, uint256[] memory tokenIds) =
                abi.decode(_data, (CanonicalNFT, address, address, uint256[]));

/// @audit `token`,  are used only once
94:         address token = _transferTokens(ctoken, to, tokenIds);

/// @audit `data`,  are used only once
123:         (bytes memory data) = abi.decode(_message.data[4:], (bytes));

/// @audit `token`,  are used only once
128:         address token = _transferTokens(ctoken, _message.srcOwner, tokenIds);

/// @audit `data`,  are used only once
241:         bytes memory data = abi.encodeCall(
                 BridgedERC721.init,
                 (owner(), addressManager, _ctoken.addr, _ctoken.chainId, _ctoken.symbol, _ctoken.name)
             );

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC721Vault.sol#L241-L244)

```solidity
File: /contracts/verifiers/SgxVerifier.sol

/// @audit `verified`,  are used only once
128:         (bool verified,) = IAttestation(automataDcapAttestation).verifyParsedQuote(_attestation);

/// @audit `signature`,  are used only once
156:         bytes memory signature = Bytes.slice(_proof.data, 24);

/// @audit `taikoL1`,  are used only once
181:         address taikoL1 = resolve("taiko", false);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/SgxVerifier.sol#L181-L181)

</details>

### <a name="GAS-69-1693313108"></a>[GAS-69] Using `storage` instead of `memory` for structs/arrays saves gas
When fetching data from a storage location, assigning the data to a `memory` variable causes all fields of the struct/array to be read from storage, which incurs a Gcoldsload (**2100 gas**) for *each* field of the struct/array. If the fields are read from the new memory variable, they incur an additional `MLOAD` rather than a cheap stack read. Instead of declearing the variable with the `memory` keyword, declaring the variable with the `storage` keyword and caching any fields that need to be re-read in stack variables, will be much cheaper, only incuring the Gcoldsload for the fields actually read. The only time it makes sense to read the whole struct/array into a `memory` variable, is if the full struct/array is being returned by the function, is being passed to a function that requires `memory`, or if the array/struct is being read from another `memory` array/struct

*Instances (13)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/libs/LibProving.sol

110:         TaikoData.SlotB memory b = _state.slotB;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProving.sol#L110)

```solidity
File: /contracts/L1/libs/LibUtils.sol

33:         TaikoData.SlotB memory b = _state.slotB;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibUtils.sol#L33)

```solidity
File: /contracts/L1/libs/LibVerifying.sol

99:         TaikoData.SlotB memory b = _state.slotB;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibVerifying.sol#L99)

```solidity
File: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

180:         EnclaveIdStruct.EnclaveId memory enclaveId = qeIdentity;

192:             EnclaveIdStruct.TcbLevel memory tcb = enclaveId.tcbLevels[i];

215:             TCBInfoStruct.TCBLevelObj memory current = tcb.tcbLevels[i];

442:             IPEMCertChainLib.ECSha256Certificate memory pckCert = parsedQuoteCerts[0];

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/AutomataDcapV3Attestation.sol#L442)

```solidity
File: /contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

75:         V3Struct.EnclaveReport memory pckSignedQeReport = v3Quote.v3AuthData.pckSignedQeReport;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L75)

```solidity
File: /contracts/automata-attestation/utils/RsaVerify.sol

53:         uint8[17] memory sha256ExplicitNullParam = [

73:         uint8[15] memory sha256ImplicitNullParam = [

222:         uint8[15] memory sha1Prefix = [

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/RsaVerify.sol#L222)

```solidity
File: /contracts/automata-attestation/utils/X509DateUtils.sol

56:         uint8[12] memory monthDays = [31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31];

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/X509DateUtils.sol#L56)

```solidity
File: /contracts/tokenvault/ERC20Vault.sol

171:             CanonicalERC20 memory ctoken = bridgedToCanonical[btokenOld_];

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC20Vault.sol#L171)

</details>

### <a name="GAS-70-1693313130"></a>[GAS-70] `>=`/`<=` costs less gas than `>`/`<`
The compiler uses opcodes `GT` and `ISZERO` for solidity code that uses `>`, but only requires `LT` for `>=`, [which saves **3 gas**](https://gist.github.com/IllIllI000/3dc79d25acccfa16dee4e83ffdc6ffde)

*Instances (81)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/hooks/AssignmentHook.sol

82:             block.timestamp > assignment.expiry

85:                 || assignment.maxBlockId != 0 && _meta.id > assignment.maxBlockId

86:                 || assignment.maxProposedIn != 0 && block.number > assignment.maxProposedIn

125:         if (address(this).balance > 0) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/hooks/AssignmentHook.sol#L125)

```solidity
File: /contracts/L1/libs/LibDepositing.sol

78:         if (numPending < _config.ethDepositMinCountPerBlock) {

93:                 uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount;

140:                 && _state.slotA.numEthDeposits - _state.slotA.nextEthDepositToProcess

150:         if (_amount > type(uint96).max) revert L1_INVALID_ETH_DEPOSIT();

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibDepositing.sol#L150)

```solidity
File: /contracts/L1/libs/LibProposing.sol

171:             if (uint256(params.txListByteOffset) + params.txListByteSize > MAX_BYTES_PER_BLOB) {

195:         if (meta_.txListByteSize == 0 || meta_.txListByteSize > _config.blockMaxTxListBytes) {

296:         return _state.reusableBlobs[_blobHash] + _config.blobExpiry > block.timestamp;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProposing.sol#L296)

```solidity
File: /contracts/L1/libs/LibProving.sol

134:         if (_proof.tier == 0 || _proof.tier < _meta.minTier || _proof.tier < ts.tier) {

134:         if (_proof.tier == 0 || _proof.tier < _meta.minTier || _proof.tier < ts.tier) {

192:             bool returnLivenessBond = blk.livenessBond > 0 && _proof.data.length == 32

203:         if (_proof.tier > ts.tier) {

381:             if (reward > _tier.validityBond) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProving.sol#L381)

```solidity
File: /contracts/L1/libs/LibUtils.sol

34:         if (_blockId < b.lastVerifiedBlockId || _blockId >= b.numBlocks) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibUtils.sol#L34)

```solidity
File: /contracts/L1/libs/LibVerifying.sol

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
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibVerifying.sol#L262)

```solidity
File: /contracts/L1/provers/Guardians.sol

63:         if (_newGuardians.length < MIN_NUM_GUARDIANS || _newGuardians.length > type(uint8).max) {

63:         if (_newGuardians.length < MIN_NUM_GUARDIANS || _newGuardians.length > type(uint8).max) {

68:         if (_minGuardians < (_newGuardians.length + 1) >> 1 || _minGuardians > _newGuardians.length)

68:         if (_minGuardians < (_newGuardians.length + 1) >> 1 || _minGuardians > _newGuardians.length)

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/provers/Guardians.sol#L68)

```solidity
File: /contracts/L2/Lib1559Math.sol

42:         if (input > LibFixedPointMath.MAX_EXP_INPUT) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/Lib1559Math.sol#L42)

```solidity
File: /contracts/L2/TaikoL2.sol

82:         if (block.chainid <= 1 || block.chainid > type(uint64).max) {

145:         if (_l1BlockId > lastSyncedBlock + BLOCK_SYNC_THRESHOLD) {

262:         if (gasExcess > 0) {

275:             if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {

275:             if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {

279:             if (numL1Blocks > 0) {

281:                 excess = excess > issuance ? excess - issuance : 1;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/TaikoL2.sol#L281)

```solidity
File: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

241:             if (pckCpuSvns[i] < tcbCpuSvns[i]) {

280:                 block.timestamp > certs[i].notBefore && block.timestamp < certs[i].notAfter;

280:                 block.timestamp > certs[i].notBefore && block.timestamp < certs[i].notAfter;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/AutomataDcapV3Attestation.sol#L280)

```solidity
File: /contracts/automata-attestation/lib/PEMCertChainLib.sol

56:             if (i > 0) {

323:                     if (extnValuePtr.ixl() < extnValueParentPtr.ixl()) {

333:             if (tbsPtr.ixl() < tbsParentPtr.ixl()) {

358:             uint16 svnValue = svnValueBytes.length < 2

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/PEMCertChainLib.sol#L358)

```solidity
File: /contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

218:         if (cert.certType < 1 || cert.certType > 5) {

218:         if (cert.certType < 1 || cert.certType > 5) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L218)

```solidity
File: /contracts/automata-attestation/utils/BytesUtils.sol

69:         if (otherlen < len) {

90:                 if (shortest > 32) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/BytesUtils.sol#L90)

```solidity
File: /contracts/automata-attestation/utils/X509DateUtils.sol

18:             if (uint8(x509Time[0]) - 48 < 5) yrs += 2000;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/X509DateUtils.sol#L18)

```solidity
File: /contracts/libs/LibMath.sol

13:         return _a > _b ? _b : _a;

21:         return _a > _b ? _a : _b;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/libs/LibMath.sol#L21)

```solidity
File: /contracts/signal/SignalService.sol

120:             bool isFullProof = hop.accountProof.length > 0;

247:         if (topBlockId[_chainId][_kind] < _blockId) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/SignalService.sol#L247)

```solidity
File: /contracts/team/TimelockTokenPool.sol

275:             if (_cliff > 0) revert INVALID_GRANT();

277:             if (_cliff > 0 && _cliff <= _start) revert INVALID_GRANT();

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/TimelockTokenPool.sol#L277)

```solidity
File: /contracts/team/airdrop/ERC20Airdrop2.sol

40:         if (claimEnd > block.timestamp || claimEnd + withdrawalWindow < block.timestamp) {

40:         if (claimEnd > block.timestamp || claimEnd + withdrawalWindow < block.timestamp) {

114:         if (block.timestamp < claimEnd) return (balance, 0);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC20Airdrop2.sol#L114)

```solidity
File: /contracts/team/airdrop/MerkleClaimable.sol

35:             merkleRoot == 0x0 || claimStart == 0 || claimEnd == 0 || claimStart > block.timestamp

36:                 || claimEnd < block.timestamp

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/MerkleClaimable.sol#L36)

```solidity
File: /contracts/thirdparty/optimism/rlp/RLPReader.sol

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
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/rlp/RLPReader.sol#L264)

```solidity
File: /contracts/thirdparty/optimism/rlp/RLPWriter.sol

14:         if (_in.length == 1 && uint8(_in[0]) < 128) {

33:         if (_len < 56) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/rlp/RLPWriter.sol#L33)

```solidity
File: /contracts/thirdparty/optimism/trie/MerkleTrie.sol

77:         require(_key.length > 0, "MerkleTrie: empty key");

120:                         value_.length > 0,

173:                         value_.length > 0,

221:         id_ = _node.length < 32 ? RLPReader.readRawBytes(_node) : RLPReader.readBytes(_node);

243:         uint256 max = (_a.length < _b.length) ? _a.length : _b.length;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/trie/MerkleTrie.sol#L243)

```solidity
File: /contracts/tokenvault/BaseNFTVault.sol

145:         if (_op.tokenIds.length > MAX_TOKEN_PER_TXN) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BaseNFTVault.sol#L145)

</details>

### <a name="GAS-71-1695857615"></a>[GAS-71] Avoid transferring amounts of zero in order to save gas
Skipping the external call when nothing will be transferred, will save at least **100 gas**

*Instances (19)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/TaikoToken.sol

62:         return super.transfer(_to, _amount);

80:         return super.transferFrom(_from, _to, _amount);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/TaikoToken.sol#L80-L80)

```solidity
File: /contracts/L1/hooks/AssignmentHook.sol

102:         tko.transferFrom(_blk.assignedProver, taikoL1Address, _blk.livenessBond);

114:             IERC20(assignment.feeToken).safeTransferFrom(

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/hooks/AssignmentHook.sol#L114-L114)

```solidity
File: /contracts/L1/libs/LibProving.sol

196:                 tko.transfer(blk.assignedProver, blk.livenessBond);

242:                 tko.transferFrom(msg.sender, address(this), tier.contestBond);

367:                 _tko.transfer(_ts.prover, _ts.validityBond + reward);

371:                 _tko.transfer(_ts.contester, _ts.contestBond + reward);

382:                 _tko.transfer(msg.sender, reward - _tier.validityBond);

384:                 _tko.transferFrom(msg.sender, address(this), _tier.validityBond - reward);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProving.sol#L384-L384)

```solidity
File: /contracts/L1/libs/LibVerifying.sol

189:                 tko.transfer(ts.prover, bondToReturn);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibVerifying.sol#L189-L189)

```solidity
File: /contracts/L2/TaikoL2.sol

176:             IERC20(_token).safeTransfer(_to, IERC20(_token).balanceOf(address(this)));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/TaikoL2.sol#L176-L176)

```solidity
File: /contracts/team/TimelockTokenPool.sol

219:         IERC20(taikoToken).transferFrom(sharedVault, _to, amountToWithdraw);

220:         IERC20(costToken).safeTransferFrom(_recipient, sharedVault, costToWithdraw);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/TimelockTokenPool.sol#L220-L220)

```solidity
File: /contracts/team/airdrop/ERC20Airdrop.sol

63:         IERC20(token).transferFrom(vault, user, amount);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC20Airdrop.sol#L63-L63)

```solidity
File: /contracts/team/airdrop/ERC20Airdrop2.sol

91:         IERC20(token).transferFrom(vault, user, amount);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC20Airdrop2.sol#L91-L91)

```solidity
File: /contracts/tokenvault/ERC20Vault.sol

330:             IERC20(token_).safeTransfer(_to, _amount);

379:             t.safeTransferFrom({ from: msg.sender, to: address(this), value: _amount });

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC20Vault.sol#L379-L379)

```solidity
File: /contracts/tokenvault/adapters/USDCAdapter.sol

48:         usdc.transferFrom(_from, address(this), _amount);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/adapters/USDCAdapter.sol#L48-L48)

</details>

### <a name="GAS-72-1693313275"></a>[GAS-72] Use assembly to validate `msg.sender`
We can use assembly to efficiently validate msg.sender with the least amount of opcodes necessary. For more details check the following report [Here](https://code4rena.com/reports/2023-05-juicebox#g-06-use-assembly-to-validate-msgsender)

*Instances (20)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/libs/LibProposing.sol

310:             if (proposerOne != address(0) && msg.sender != proposerOne) {

310:             if (proposerOne != address(0) && msg.sender != proposerOne) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProposing.sol#L310-L310)

```solidity
File: /contracts/L2/TaikoL2.sol

123:         if (msg.sender != GOLDEN_TOUCH_ADDRESS) revert L2_INVALID_SENDER();

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/TaikoL2.sol#L123-L123)

```solidity
File: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

61:         require(msg.sender == owner, "onlyOwner");

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/AutomataDcapV3Attestation.sol#L61-L61)

```solidity
File: /contracts/bridge/Bridge.sol

250:         if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) {

260:             if (_message.gasLimit == 0 && msg.sender != _message.destOwner) {

280:                 uint256 gasLimit = msg.sender == _message.destOwner ? gasleft() : _message.gasLimit;

294:             if (msg.sender == refundTo) {

294:             if (msg.sender == refundTo) {

322:             if (msg.sender != _message.destOwner) revert B_PERMISSION_DENIED();

322:             if (msg.sender != _message.destOwner) revert B_PERMISSION_DENIED();

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L322-L322)

```solidity
File: /contracts/common/EssentialContract.sol

42:         if (msg.sender != owner() && msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/common/EssentialContract.sol#L42-L42)

```solidity
File: /contracts/tokenvault/BaseVault.sol

23:         if (msg.sender != resolve("bridge", false)) {

65:         if (ctx_.from != msg.sender) revert VAULT_PERMISSION_DENIED();

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BaseVault.sol#L65-L65)

```solidity
File: /contracts/tokenvault/BridgedERC20.sol

38:         if (msg.sender != owner() && msg.sender != snapshooter) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC20.sol#L38-L38)

```solidity
File: /contracts/tokenvault/BridgedERC20Base.sol

61:         if (msg.sender == migratingAddress) {

64:         } else if (msg.sender != resolve("erc20_vault", true)) {

78:             if (msg.sender != _account) revert BB_PERMISSION_DENIED();

83:         } else if (msg.sender != resolve("erc20_vault", true)) {

83:         } else if (msg.sender != resolve("erc20_vault", true)) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC20Base.sol#L83-L83)

</details>

### <a name="GAS-73-1699451597"></a>[GAS-73] Using `constant`s instead of `enum` can save gas
`Enum` is expensive and it is [more efficient to use constants](https://www.codehawks.com/finding/clm84992q02j9w9ruebun36d9) instead. An illustrative example of this approach can be found in the [ReentrancyGuard.sol](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/181d518609a9f006fcb97af63e6952e603cf100e/contracts/utils/ReentrancyGuard.sol#L34-L35).

*Instances (10)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/automata-attestation/interfaces/ISigVerifyLib.sol

7:     enum KeyType {
           RSA,
           ECDSA
       }

19:     enum CertSigAlgorithm {
            Sha256WithRSAEncryption,
            Sha1WithRSAEncryption
        }

32:     enum Algorithm {
            RS256,
            ES256,
            RS1
        }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L32-L36)

```solidity
File: /contracts/automata-attestation/lib/EnclaveIdStruct.sol

26:     enum EnclaveIdStatus {
            OK,
            SGX_ENCLAVE_REPORT_ISVSVN_REVOKED
        }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/EnclaveIdStruct.sol#L26-L29)

```solidity
File: /contracts/automata-attestation/lib/TCBInfoStruct.sol

19:     enum TCBStatus {
            OK,
            TCB_SW_HARDENING_NEEDED,
            TCB_CONFIGURATION_AND_SW_HARDENING_NEEDED,
            TCB_CONFIGURATION_NEEDED,
            TCB_OUT_OF_DATE,
            TCB_OUT_OF_DATE_CONFIGURATION_NEEDED,
            TCB_REVOKED,
            TCB_UNRECOGNIZED
        }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/TCBInfoStruct.sol#L19-L28)

```solidity
File: /contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol

31:     enum CRL {
            PCK,
            ROOT
        }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L31-L34)

```solidity
File: /contracts/bridge/IBridge.sol

9:     enum Status {
           NEW,
           RETRIABLE,
           DONE,
           FAILED,
           RECALLED
       }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/IBridge.sol#L9-L15)

```solidity
File: /contracts/signal/ISignalService.sol

13:     enum CacheOption {
            CACHE_NOTHING,
            CACHE_SIGNAL_ROOT,
            CACHE_STATE_ROOT,
            CACHE_BOTH
        }

13:     enum CacheOption {
            CACHE_NOTHING,
            CACHE_SIGNAL_ROOT,
            CACHE_STATE_ROOT,
            CACHE_BOTH
        }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/ISignalService.sol#L13-L18)

```solidity
File: /contracts/thirdparty/optimism/rlp/RLPReader.sol

16:     enum RLPItemType {
            DATA_ITEM,
            LIST_ITEM
        }

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/rlp/RLPReader.sol#L16-L19)

</details>

### <a name="GAS-74-1696083995"></a>[GAS-74] When no `addresses` are used `abi.encodepacked()` Outperforms `abi.encode()` in Efficiency
when dealing with non address type parameters `encodepacked()` function less gas than `encode()`. For more details check the following [comparison](https://github.com/ConnorBlockchain/Solidity-Encode-Gas-Comparison)

*Instances (10)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/libs/LibProposing.sol

126:                 depositsHash: keccak256(abi.encode(deposits_)),

213:             metaHash: keccak256(abi.encode(meta_)),

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProposing.sol#L213)

```solidity
File: /contracts/L1/libs/LibProving.sol

121:         if (blk.blockId != _meta.id || blk.metaHash != keccak256(abi.encode(_meta))) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProving.sol#L121)

```solidity
File: /contracts/L1/provers/GuardianProver.sol

46:         bytes32 hash = keccak256(abi.encode(_meta, _tran));

51:             ITaikoL1(resolve("taiko", false)).proveBlock(_meta.id, abi.encode(_meta, _tran, _proof));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/provers/GuardianProver.sol#L51)

```solidity
File: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

482:         retData = abi.encodePacked(sha256(abi.encode(v3quote)), tcbStatus);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/AutomataDcapV3Attestation.sol#L482)

```solidity
File: /contracts/automata-attestation/utils/SigVerifyLib.sol

136:         bytes memory args = abi.encode(sha256(tbs), r, s, gx, gy);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/SigVerifyLib.sol#L136)

```solidity
File: /contracts/bridge/Bridge.sol

450:         return keccak256(abi.encode("TAIKO_MESSAGE", _message));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L450)

```solidity
File: /contracts/signal/SignalService.sol

186:         return keccak256(abi.encode(_chainId, _kind, _blockId));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/SignalService.sol#L186)

```solidity
File: /contracts/team/airdrop/MerkleClaimable.sol

68:         bytes32 hash = keccak256(abi.encode("CLAIM_TAIKO_AIRDROP", data));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/MerkleClaimable.sol#L68)

</details>

### <a name="GAS-75-1705427608"></a>[GAS-75] Consider using solady's 'FixedPointMathLib'
Using Solady's 'FixedPointMathLib' for multiplication or division operations in Solidity can lead to significant gas savings. This library is designed to optimize fixed-point arithmetic operations, which are common in financial calculations involving tokens or currencies. By implementing more efficient algorithms and assembly optimizations, 'FixedPointMathLib' minimizes the computational resources required for these operations. For contracts that frequently perform such calculations, integrating this library can reduce transaction costs, thereby enhancing overall performance and cost-effectiveness. However, developers must ensure compatibility with their existing codebase and thoroughly test for accuracy and expected behavior to avoid any unintended consequences.

*Instances (46)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/TaikoL1.sol

//@audit for: `/`
215:             ethDepositMaxFee: 1 ether / 10,

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/TaikoL1.sol#L215-L215)

```solidity
File: /contracts/L1/gov/TaikoGovernor.sol

//@audit for: `/`
124:         return 1_000_000_000 ether / 10_000; // 0.01% of Taiko Token

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/gov/TaikoGovernor.sol#L124-L124)

```solidity
File: /contracts/L1/libs/LibDepositing.sol

//@audit for: `*`
83:             uint96 fee = uint96(_config.ethDepositMaxFee.min(block.basefee * _config.ethDepositGas));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibDepositing.sol#L83-L83)

```solidity
File: /contracts/L1/libs/LibProposing.sol

//@audit for: `*`
21:     uint256 public constant MAX_BYTES_PER_BLOB = 4096 * 32;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProposing.sol#L21-L21)

```solidity
File: /contracts/L1/libs/LibProving.sol

//@audit for: `*`
415:             + _tier.provingWindow * 60 >= block.timestamp;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProving.sol#L415-L415)

```solidity
File: /contracts/L1/libs/LibVerifying.sol

//@audit for: `*`
152:                         uint256(ITierProvider(tierProvider).getTier(ts.tier).cooldownWindow) * 60

//@audit for: `*`
251:                 || _config.blockMaxTxListBytes > 128 * 1024 // calldata up to 128K

//@audit for: `/`
262:                 || _config.ethDepositMaxFee > type(uint96).max / _config.ethDepositMaxCountPerBlock

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibVerifying.sol#L262-L262)

```solidity
File: /contracts/L2/Lib1559Math.sol

//@audit for: `/`
28:         return _ethQty(_gasExcess, _adjustmentFactor) / LibFixedPointMath.SCALING_FACTOR
                / _adjustmentFactor;

//@audit for: `/`
28:         return _ethQty(_gasExcess, _adjustmentFactor) / LibFixedPointMath.SCALING_FACTOR

//@audit for: `/`
41:         uint256 input = _gasExcess * LibFixedPointMath.SCALING_FACTOR / _adjustmentFactor;

//@audit for: `*`
41:         uint256 input = _gasExcess * LibFixedPointMath.SCALING_FACTOR / _adjustmentFactor;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/Lib1559Math.sol#L41-L41)

```solidity
File: /contracts/L2/TaikoL2.sol

//@audit for: `*`
213:         config_.gasTargetPerL1Block = 15 * 1e6 * 4;

//@audit for: `*`
213:         config_.gasTargetPerL1Block = 15 * 1e6 * 4;

//@audit for: `*`
280:                 uint256 issuance = numL1Blocks * _config.gasTargetPerL1Block;

//@audit for: `*`
291:                 gasExcess_, uint256(_config.basefeeAdjustmentQuotient) * _config.gasTargetPerL1Block

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/TaikoL2.sol#L291-L291)

```solidity
File: /contracts/automata-attestation/lib/PEMCertChainLib.sol

//@audit for: `/`
359:                 ? uint16(bytes2(svnValueBytes)) / 256

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/PEMCertChainLib.sol#L359-L359)

```solidity
File: /contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

//@audit for: `/`
155:             uint256 upperDigit = digits / 16;

//@audit for: `*`
158:             uint256 acc = lowerDigit * (16 ** (2 * i));

//@audit for: `*`
158:             uint256 acc = lowerDigit * (16 ** (2 * i));

//@audit for: `*`
159:             acc += upperDigit * (16 ** ((2 * i) + 1));

//@audit for: `*`
159:             acc += upperDigit * (16 ** ((2 * i) + 1));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L159-L159)

```solidity
File: /contracts/automata-attestation/utils/Asn1Decode.sol

//@audit for: `*`
145:         return uint256(der.readBytesN(ptr.ixf(), len) >> (32 - len) * 8);

//@audit for: `*`
203:                     der.readBytesN(ix + 2, lengthbytesLength) >> (32 - lengthbytesLength) * 8

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/Asn1Decode.sol#L203-L203)

```solidity
File: /contracts/automata-attestation/utils/BytesUtils.sol

//@audit for: `*`
93:                     mask = ~(2 ** (8 * (32 - shortest + idx)) - 1);

//@audit for: `*`
344:         uint256 bitlen = len * 5;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/BytesUtils.sol#L344-L344)

```solidity
File: /contracts/automata-attestation/utils/X509DateUtils.sol

//@audit for: `*`
21:             yrs += (uint8(x509Time[0]) - 48) * 1000 + (uint8(x509Time[1]) - 48) * 100;

//@audit for: `*`
21:             yrs += (uint8(x509Time[0]) - 48) * 1000 + (uint8(x509Time[1]) - 48) * 100;

//@audit for: `*`
24:         yrs += (uint8(x509Time[offset + 0]) - 48) * 10 + uint8(x509Time[offset + 1]) - 48;

//@audit for: `*`
25:         mnths = (uint8(x509Time[offset + 2]) - 48) * 10 + uint8(x509Time[offset + 3]) - 48;

//@audit for: `*`
26:         dys += (uint8(x509Time[offset + 4]) - 48) * 10 + uint8(x509Time[offset + 5]) - 48;

//@audit for: `*`
27:         hrs += (uint8(x509Time[offset + 6]) - 48) * 10 + uint8(x509Time[offset + 7]) - 48;

//@audit for: `*`
28:         mins += (uint8(x509Time[offset + 8]) - 48) * 10 + uint8(x509Time[offset + 9]) - 48;

//@audit for: `*`
29:         secs += (uint8(x509Time[offset + 10]) - 48) * 10 + uint8(x509Time[offset + 11]) - 48;

//@audit for: `*`
60:             timestamp += uint256(monthDays[i - 1]) * 86_400; // Days in seconds

//@audit for: `*`
63:         timestamp += uint256(day - 1) * 86_400; // Days in seconds

//@audit for: `*`
64:         timestamp += uint256(hour) * 3600; // Hours in seconds

//@audit for: `*`
65:         timestamp += uint256(minute) * 60; // Minutes in seconds

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/X509DateUtils.sol#L65-L65)

```solidity
File: /contracts/team/TimelockTokenPool.sol

//@audit for: `/`
197:         uint128 _amountUnlocked = amountUnlocked / 1e18; // divide first

//@audit for: `*`
198:         costToWithdraw = _amountUnlocked * r.grant.costPerToken - r.costPaid;

//@audit for: `/`
264:         return _amount * uint64(block.timestamp - _start) / _period;

//@audit for: `*`
264:         return _amount * uint64(block.timestamp - _start) / _period;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/TimelockTokenPool.sol#L264-L264)

```solidity
File: /contracts/team/airdrop/ERC20Airdrop2.sol

//@audit for: `/`
117:         uint256 timeBasedAllowance = balance
                 * (block.timestamp.min(claimEnd + withdrawalWindow) - claimEnd) / withdrawalWindow;

//@audit for: `*`
117:         uint256 timeBasedAllowance = balance
                 * (block.timestamp.min(claimEnd + withdrawalWindow) - claimEnd) / withdrawalWindow;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC20Airdrop2.sol#L117-L118)

```solidity
File: /contracts/thirdparty/optimism/rlp/RLPWriter.sol

//@audit for: `/`
39:             while (_len / i != 0) {

//@audit for: `/`
47:                 out_[i] = bytes1(uint8((_len / (256 ** (lenLen - i))) % 256));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/rlp/RLPWriter.sol#L47-L47)

</details>

### <a name="GAS-76-1694794906"></a>[GAS-76] Using mappings instead of arrays to avoid length checks save gas
Just by using a mapping, we get a gas saving of 2102 gas. When you read the value of an index of an array, solidity adds bytecode that checks that you are reading from a valid index (i.e an index strictly less than the length of the array) else it reverts with a panic error (Panic(0x32) to be precise). This prevents from reading unallocated or worse, allocated storage/memory locations.
Due to the way mappings are(simply a key => value pair), no check like that exists and we are able to read from the a storage slot directly.Itâ€™s important to note that when using mappings in this manner, your code should ensure that you are not reading an out of bound index of your canonical array.

*Instances (1)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/provers/Guardians.sol

23:     address[] public guardians;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/provers/Guardians.sol#L23-L23)

</details>

### <a name="GAS-77-1699443465"></a>[GAS-77] Using `private` for constants saves gas
If needed, the values can be read from the verified contract source code, or if there are multiple values there can be a single getter function that [returns a tuple](https://github.com/code-423n4/2022-08-frax/blob/90f55a9ce4e25bceed3a74290b854341d8de6afa/src/contracts/FraxlendPair.sol#L156-L178) of the values of all currently-public constants. Saves **3406-3606 gas** in deployment gas due to the compiler not having to create non-payable getter functions for deployment calldata, not having to store the bytes of the value outside of where it's used, and not adding another entry to the method ID table

*Instances (23)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/hooks/AssignmentHook.sol

38:     uint256 public constant MAX_GAS_PAYING_PROVER = 50_000;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/hooks/AssignmentHook.sol#L38-L38)

```solidity
File: /contracts/L1/libs/LibProposing.sol

21:     uint256 public constant MAX_BYTES_PER_BLOB = 4096 * 32;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProposing.sol#L21-L21)

```solidity
File: /contracts/L1/libs/LibProving.sol

20:     bytes32 public constant RETURN_LIVENESS_BOND = keccak256("RETURN_LIVENESS_BOND");

23:     bytes32 public constant TIER_OP = bytes32("tier_optimistic");

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibProving.sol#L23-L23)

```solidity
File: /contracts/L1/provers/Guardians.sol

11:     uint256 public constant MIN_NUM_GUARDIANS = 5;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/provers/Guardians.sol#L11-L11)

```solidity
File: /contracts/L1/tiers/ITierProvider.sol

39:     uint16 public constant TIER_OPTIMISTIC = 100;

42:     uint16 public constant TIER_SGX = 200;

45:     uint16 public constant TIER_SGX_ZKVM = 300;

48:     uint16 public constant TIER_GUARDIAN = 1000;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/tiers/ITierProvider.sol#L48-L48)

```solidity
File: /contracts/L2/TaikoL2.sol

32:     address public constant GOLDEN_TOUCH_ADDRESS = 0x0000777735367b36bC9B61C50022d9D0700dB4Ec;

35:     uint8 public constant BLOCK_SYNC_THRESHOLD = 5;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/TaikoL2.sol#L35-L35)

```solidity
File: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

25:     ISigVerifyLib public immutable sigVerifyLib;

26:     IPEMCertChainLib public immutable pemCertLib;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/AutomataDcapV3Attestation.sol#L26-L26)

```solidity
File: /contracts/libs/Lib4844.sol

10:     address public constant POINT_EVALUATION_PRECOMPILE_ADDRESS = address(0x0A);

13:     uint32 public constant FIELD_ELEMENTS_PER_BLOB = 4096;

16:     uint256 public constant BLS_MODULUS =
            52_435_875_175_126_190_479_447_740_508_185_965_837_690_552_500_527_637_822_603_658_699_938_581_184_513;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/libs/Lib4844.sol#L16-L17)

```solidity
File: /contracts/signal/LibSignals.sol

8:     bytes32 public constant STATE_ROOT = keccak256("STATE_ROOT");

11:     bytes32 public constant SIGNAL_ROOT = keccak256("SIGNAL_ROOT");

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/LibSignals.sol#L11-L11)

```solidity
File: /contracts/tokenvault/BaseNFTVault.sol

47:     bytes4 public constant ERC1155_INTERFACE_ID = 0xd9b67a26;

50:     bytes4 public constant ERC721_INTERFACE_ID = 0x80ac58cd;

53:     uint256 public constant MAX_TOKEN_PER_TXN = 10;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BaseNFTVault.sol#L53-L53)

```solidity
File: /contracts/verifiers/SgxVerifier.sol

30:     uint64 public constant INSTANCE_EXPIRY = 180 days;

34:     uint64 public constant INSTANCE_VALIDITY_DELAY = 1 days;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/SgxVerifier.sol#L34-L34)

</details>

### <a name="GAS-78-1702131709"></a>[GAS-78] Use `solady` library where possible to save gas
[Solady](https://github.com/Vectorized/solady) is a Solidity library inspired by [Solmate](https://github.com/rari-capital/solmate), optimized heavily for gas optimizations and battle tested by [hundreds of developers](https://www.alchemy.com/dapps/solady). Consider implementing solady contracts where possible to reduce runtime gas fees.

*Instances (11)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/TaikoToken.sol

4: import "@openzeppelin/contracts-upgradeable/token/ERC20/ERC20Upgradeable.sol";

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/TaikoToken.sol#L4-L4)

```solidity
File: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

13: import { Base64 } from "solady/src/utils/Base64.sol";

14: import { LibString } from "solady/src/utils/LibString.sol";

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/AutomataDcapV3Attestation.sol#L14-L14)

```solidity
File: /contracts/automata-attestation/lib/PEMCertChainLib.sol

4: import { LibString } from "solady/src/utils/LibString.sol";

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/PEMCertChainLib.sol#L4-L4)

```solidity
File: /contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

4: import { Base64 } from "solady/src/utils/Base64.sol";

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L4-L4)

```solidity
File: /contracts/common/EssentialContract.sol

4: import "@openzeppelin/contracts/proxy/utils/UUPSUpgradeable.sol";

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/common/EssentialContract.sol#L4-L4)

```solidity
File: /contracts/libs/LibAddress.sol

5: import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol";

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/libs/LibAddress.sol#L5-L5)

```solidity
File: /contracts/team/TimelockTokenPool.sol

4: import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol";

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/TimelockTokenPool.sol#L4-L4)

```solidity
File: /contracts/tokenvault/BridgedERC1155.sol

5: import "@openzeppelin/contracts-upgradeable/token/ERC1155/ERC1155Upgradeable.sol";

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC1155.sol#L5-L5)

```solidity
File: /contracts/tokenvault/BridgedERC721.sol

4: import "@openzeppelin/contracts-upgradeable/token/ERC721/ERC721Upgradeable.sol";

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/BridgedERC721.sol#L4-L4)

```solidity
File: /contracts/verifiers/SgxVerifier.sol

4: import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol";

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/SgxVerifier.sol#L4-L4)

</details>

### <a name="GAS-79-1707922603"></a>[GAS-79] Use Array.unsafeAccess() to avoid repeated array length checks
When using storage arrays, solidity adds an internal lookup of the array's length (a Gcoldsload 2100 gas) to ensure you don't read past the array's end. You can avoid this lookup by using `Array.unsafeAccess()` in cases where the length has already been checked, as is the case with the instances below

*Instances (64)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/hooks/AssignmentHook.sol

173:             if (_tierFees[i].tier == _tierId) return _tierFees[i].fee;

173:             if (_tierFees[i].tier == _tierId) return _tierFees[i].fee;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/hooks/AssignmentHook.sol#L173-L173)

```solidity
File: /contracts/L1/libs/LibDepositing.sol

88:                 deposits_[i] = TaikoData.EthDeposit({

93:                 uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount;

93:                 uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount;

101:                     deposits_[i].amount -= _fee;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibDepositing.sol#L101-L101)

```solidity
File: /contracts/L1/provers/Guardians.sol

75:             delete guardianIds[guardians[i]];

81:             address guardian = _newGuardians[i];

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/provers/Guardians.sol#L81-L81)

```solidity
File: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

81:             if (_serialNumIsRevoked[index][serialNumBatch[i]]) {

84:             _serialNumIsRevoked[index][serialNumBatch[i]] = true;

96:             if (!_serialNumIsRevoked[index][serialNumBatch[i]]) {

99:             delete _serialNumIsRevoked[index][serialNumBatch[i]];

241:             if (pckCpuSvns[i] < tcbCpuSvns[i]) {

241:             if (pckCpuSvns[i] < tcbCpuSvns[i]) {

263:                 issuer = certs[i];

265:                 issuer = certs[i + 1];

268:                     certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.ROOT)][certs[i]

270:                 } else if (certs[i].isPck) {

271:                     certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.PCK)][certs[i]

280:                 block.timestamp > certs[i].notBefore && block.timestamp < certs[i].notAfter;

280:                 block.timestamp > certs[i].notBefore && block.timestamp < certs[i].notAfter;

286:                 certs[i].tbsCertificate, certs[i].signature, issuer.pubKey

286:                 certs[i].tbsCertificate, certs[i].signature, issuer.pubKey

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/AutomataDcapV3Attestation.sol#L286-L286)

```solidity
File: /contracts/automata-attestation/lib/PEMCertChainLib.sol

245:             contentStr = LibString.concat(contentStr, split[i]);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/PEMCertChainLib.sol#L245-L245)

```solidity
File: /contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

154:             uint256 digits = uint256(uint8(bytes1(encoded[i])));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L154-L154)

```solidity
File: /contracts/automata-attestation/utils/RsaVerify.sol

153:                 if (decipher[3 + paddingLen + i] != bytes1(sha256ExplicitNullParam[i])) {

159:                 if (decipher[3 + paddingLen + i] != bytes1(sha256ImplicitNullParam[i])) {

175:             if (decipher[5 + paddingLen + digestAlgoWithParamLen + i] != _sha256[i]) {

284:             if (decipher[3 + paddingLen + i] != bytes1(sha1Prefix[i])) {

291:             if (decipher[3 + paddingLen + sha1Prefix.length + i] != _sha1[i]) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/RsaVerify.sol#L291-L291)

```solidity
File: /contracts/automata-attestation/utils/X509DateUtils.sol

18:             if (uint8(x509Time[0]) - 48 < 5) yrs += 2000;

21:             yrs += (uint8(x509Time[0]) - 48) * 1000 + (uint8(x509Time[1]) - 48) * 100;

21:             yrs += (uint8(x509Time[0]) - 48) * 1000 + (uint8(x509Time[1]) - 48) * 100;

24:         yrs += (uint8(x509Time[offset + 0]) - 48) * 10 + uint8(x509Time[offset + 1]) - 48;

24:         yrs += (uint8(x509Time[offset + 0]) - 48) * 10 + uint8(x509Time[offset + 1]) - 48;

25:         mnths = (uint8(x509Time[offset + 2]) - 48) * 10 + uint8(x509Time[offset + 3]) - 48;

25:         mnths = (uint8(x509Time[offset + 2]) - 48) * 10 + uint8(x509Time[offset + 3]) - 48;

26:         dys += (uint8(x509Time[offset + 4]) - 48) * 10 + uint8(x509Time[offset + 5]) - 48;

26:         dys += (uint8(x509Time[offset + 4]) - 48) * 10 + uint8(x509Time[offset + 5]) - 48;

27:         hrs += (uint8(x509Time[offset + 6]) - 48) * 10 + uint8(x509Time[offset + 7]) - 48;

27:         hrs += (uint8(x509Time[offset + 6]) - 48) * 10 + uint8(x509Time[offset + 7]) - 48;

28:         mins += (uint8(x509Time[offset + 8]) - 48) * 10 + uint8(x509Time[offset + 9]) - 48;

28:         mins += (uint8(x509Time[offset + 8]) - 48) * 10 + uint8(x509Time[offset + 9]) - 48;

29:         secs += (uint8(x509Time[offset + 10]) - 48) * 10 + uint8(x509Time[offset + 11]) - 48;

29:         secs += (uint8(x509Time[offset + 10]) - 48) * 10 + uint8(x509Time[offset + 11]) - 48;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/X509DateUtils.sol#L29-L29)

```solidity
File: /contracts/bridge/Bridge.sol

91:             bytes32 msgHash = _msgHashes[i];

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L91-L91)

```solidity
File: /contracts/signal/SignalService.sol

105:             hop = hopProofs[i];

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/SignalService.sol#L105-L105)

```solidity
File: /contracts/team/airdrop/ERC721Airdrop.sol

60:             IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/team/airdrop/ERC721Airdrop.sol#L60-L60)

```solidity
File: /contracts/thirdparty/optimism/rlp/RLPWriter.sol

14:         if (_in.length == 1 && uint8(_in[0]) < 128) {

67:             out_[j] = b[i++];

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/rlp/RLPWriter.sol#L67-L67)

```solidity
File: /contracts/thirdparty/optimism/trie/MerkleTrie.sol

86:             TrieNode memory currentNode = proof[i];

134:                     uint8 branchKey = uint8(key[currentKeyIndex]);

209:             proof_[i] = TrieNode({ encoded: _proof[i], decoded: RLPReader.readList(_proof[i]) });

209:             proof_[i] = TrieNode({ encoded: _proof[i], decoded: RLPReader.readList(_proof[i]) });

244:         for (; shared_ < max && _a[shared_] == _b[shared_];) {

244:         for (; shared_ < max && _a[shared_] == _b[shared_];) {

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/trie/MerkleTrie.sol#L244-L244)

```solidity
File: /contracts/tokenvault/ERC721Vault.sol

171:                 IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);

176:                 BridgedERC721(token_).mint(_to, _tokenIds[i]);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/tokenvault/ERC721Vault.sol#L176-L176)

```solidity
File: /contracts/verifiers/SgxVerifier.sol

105:             uint256 idx = _ids[i];

211:             if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();

213:             addressRegistered[_instances[i]] = true;

215:             if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();

217:             instances[nextInstanceId] = Instance(_instances[i], validSince);

220:             emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/SgxVerifier.sol#L220-L220)

</details>

### <a name="GAS-80-1693313317"></a>[GAS-80] Can make the variable outside the loop to save gas
Creating variables inside the loop consum more gas compared to declaring them outside and just reaffecting values to them inside the loop.

*Instances (59)*:
<details><summary> see instances </summary>

```solidity
File: /contracts/L1/libs/LibDepositing.sol

//@audit variable `data` is created inside a loop.
87:                 uint256 data = _state.ethDeposits[j % _config.ethDepositRingBufferSize];

//@audit variable `_fee` is created inside a loop.
93:                 uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibDepositing.sol#L93)

```solidity
File: /contracts/L1/libs/LibVerifying.sol

//@audit variable `ts` is created inside a loop.
140:                 TaikoData.TransitionState storage ts = _state.transitions[slot][tid];

//@audit variable `bondToReturn` is created inside a loop.
178:                 uint256 bondToReturn = uint256(ts.validityBond) + blk.livenessBond;

//@audit variable `tko` is created inside a loop.
188:                 IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/libs/LibVerifying.sol#L188)

```solidity
File: /contracts/L1/provers/Guardians.sol

//@audit variable `guardian` is created inside a loop.
81:             address guardian = _newGuardians[i];

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L1/provers/Guardians.sol#L81)

```solidity
File: /contracts/L2/TaikoL2.sol

//@audit variable `j` is created inside a loop.
235:                 uint256 j = _blockId - i - 1;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/L2/TaikoL2.sol#L235)

```solidity
File: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

//@audit variable `tcb` is created inside a loop.
192:             EnclaveIdStruct.TcbLevel memory tcb = enclaveId.tcbLevels[i];

//@audit variable `current` is created inside a loop.
215:             TCBInfoStruct.TCBLevelObj memory current = tcb.tcbLevels[i];

//@audit variable `pceSvnIsHigherOrGreater` is created inside a loop.
216:             bool pceSvnIsHigherOrGreater = pck.sgxExtension.pcesvn >= current.pcesvn;

//@audit variable `cpuSvnsAreHigherOrGreater` is created inside a loop.
217:             bool cpuSvnsAreHigherOrGreater = _isCpuSvnHigherOrGreater(

//@audit variable `tcbIsRevoked` is created inside a loop.
222:                 bool tcbIsRevoked = status == TCBInfoStruct.TCBStatus.TCB_REVOKED;

//@audit variable `issuer` is created inside a loop.
260:             IPEMCertChainLib.ECSha256Certificate memory issuer;

//@audit variable `issuerPubKeyHash` is created inside a loop.
292:             bytes32 issuerPubKeyHash = keccak256(issuer.pubKey);

//@audit variable `isPckCert` is created inside a loop.
421:                 bool isPckCert = i == 0; // additional parsing for PCKCert

//@audit variable `certDecodedSuccessfully` is created inside a loop.
422:                 bool certDecodedSuccessfully;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/AutomataDcapV3Attestation.sol#L422)

```solidity
File: /contracts/automata-attestation/lib/PEMCertChainLib.sol

//@audit variable `input` is created inside a loop.
55:             string memory input;

//@audit variable `increment` is created inside a loop.
61:             uint256 increment;

//@audit variable `internalPtr` is created inside a loop.
287:             uint256 internalPtr = der.firstChildOf(tbsPtr);

//@audit variable `extnValueParentPtr` is created inside a loop.
295:                 uint256 extnValueParentPtr = der.rootOfOctetStringAt(internalPtr);

//@audit variable `extnValuePtr` is created inside a loop.
296:                 uint256 extnValuePtr = der.firstChildOf(extnValueParentPtr);

//@audit variable `flags` is created inside a loop.
299:                 PCKTCBFlags memory flags;

//@audit variable `extnValueOidPtr` is created inside a loop.
302:                     uint256 extnValueOidPtr = der.firstChildOf(extnValuePtr);

//@audit variable `extnValueOidPtr` is created inside a loop.
302:                     uint256 extnValueOidPtr = der.firstChildOf(extnValuePtr);

//@audit variable `pceidPtr` is created inside a loop.
312:                         uint256 pceidPtr = der.nextSiblingOf(extnValueOidPtr);

//@audit variable `pceidPtr` is created inside a loop.
312:                         uint256 pceidPtr = der.nextSiblingOf(extnValueOidPtr);

//@audit variable `fmspcPtr` is created inside a loop.
318:                         uint256 fmspcPtr = der.nextSiblingOf(extnValueOidPtr);

//@audit variable `fmspcPtr` is created inside a loop.
318:                         uint256 fmspcPtr = der.nextSiblingOf(extnValueOidPtr);

//@audit variable `svnPtr` is created inside a loop.
355:             uint256 svnPtr = der.firstChildOf(svnParentPtr); // OID

//@audit variable `svnValuePtr` is created inside a loop.
356:             uint256 svnValuePtr = der.nextSiblingOf(svnPtr); // value

//@audit variable `svnValueBytes` is created inside a loop.
357:             bytes memory svnValueBytes = der.bytesAt(svnValuePtr);

//@audit variable `svnValue` is created inside a loop.
358:             uint16 svnValue = svnValueBytes.length < 2

//@audit variable `cpusvn` is created inside a loop.
366:                 uint256 cpusvn = uint256(svnValue);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/PEMCertChainLib.sol#L366)

```solidity
File: /contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

//@audit variable `digits` is created inside a loop.
154:             uint256 digits = uint256(uint8(bytes1(encoded[i])));

//@audit variable `upperDigit` is created inside a loop.
155:             uint256 upperDigit = digits / 16;

//@audit variable `lowerDigit` is created inside a loop.
156:             uint256 lowerDigit = digits % 16;

//@audit variable `acc` is created inside a loop.
158:             uint256 acc = lowerDigit * (16 ** (2 * i));

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L158)

```solidity
File: /contracts/automata-attestation/utils/BytesUtils.sol

//@audit variable `a` is created inside a loop.
81:             uint256 a;

//@audit variable `b` is created inside a loop.
82:             uint256 b;

//@audit variable `mask` is created inside a loop.
89:                 uint256 mask;

//@audit variable `diff` is created inside a loop.
95:                 uint256 diff = (a & mask) - (b & mask);

//@audit variable `char` is created inside a loop.
334:             bytes1 char = self[off + i];

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/automata-attestation/utils/BytesUtils.sol#L334)

```solidity
File: /contracts/bridge/Bridge.sol

//@audit variable `msgHash` is created inside a loop.
91:             bytes32 msgHash = _msgHashes[i];

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/bridge/Bridge.sol#L91)

```solidity
File: /contracts/signal/SignalService.sol

//@audit variable `signalRoot` is created inside a loop.
107:             bytes32 signalRoot = _verifyHopProof(chainId, app, signal, value, hop, signalService);

//@audit variable `isLastHop` is created inside a loop.
108:             bool isLastHop = i == hopProofs.length - 1;

//@audit variable `isFullProof` is created inside a loop.
120:             bool isFullProof = hop.accountProof.length > 0;

//@audit variable `kind` is created inside a loop.
124:             bytes32 kind = isFullProof ? LibSignals.STATE_ROOT : LibSignals.SIGNAL_ROOT;

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/signal/SignalService.sol#L124)

```solidity
File: /contracts/thirdparty/optimism/rlp/RLPReader.sol

//@audit variable `itemOffset` is created inside a loop.
75:             (uint256 itemOffset, uint256 itemLength,) = _decodeLength(

//@audit variable `itemLength` is created inside a loop.
75:             (uint256 itemOffset, uint256 itemLength,) = _decodeLength(

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/rlp/RLPReader.sol#L75)

```solidity
File: /contracts/thirdparty/optimism/trie/MerkleTrie.sol

//@audit variable `currentNode` is created inside a loop.
86:             TrieNode memory currentNode = proof[i];

//@audit variable `branchKey` is created inside a loop.
134:                     uint8 branchKey = uint8(key[currentKeyIndex]);

//@audit variable `nextNode` is created inside a loop.
135:                     RLPReader.RLPItem memory nextNode = currentNode.decoded[branchKey];

//@audit variable `path` is created inside a loop.
140:                 bytes memory path = _getNodePath(currentNode);

//@audit variable `prefix` is created inside a loop.
141:                 uint8 prefix = uint8(path[0]);

//@audit variable `offset` is created inside a loop.
142:                 uint8 offset = 2 - (prefix % 2);

//@audit variable `pathRemainder` is created inside a loop.
143:                 bytes memory pathRemainder = Bytes.slice(path, offset);

//@audit variable `keyRemainder` is created inside a loop.
144:                 bytes memory keyRemainder = Bytes.slice(key, currentKeyIndex);

//@audit variable `sharedNibbleLength` is created inside a loop.
145:                 uint256 sharedNibbleLength = _getSharedNibbleLength(pathRemainder, keyRemainder);

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/thirdparty/optimism/trie/MerkleTrie.sol#L145)

```solidity
File: /contracts/verifiers/SgxVerifier.sol

//@audit variable `idx` is created inside a loop.
105:             uint256 idx = _ids[i];

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol//contracts/verifiers/SgxVerifier.sol#L105)

</details>

### <a name="GAS-81-1693313355"></a>[GAS-81] Consider activating via-ir for deploying
The Solidity compiler's Intermediate Representation (IR) based code generator, which can be activated using --via-ir on the command line or {""viaIR"": true} in the options, serves a dual purpose. Firstly, it boosts the transparency and audibility of code generation, which enhances developers' comprehension and control over the contract's final bytecode. Secondly, it enables more sophisticated optimization passes that span multiple functions, thereby potentially leading to more efficient bytecode.
It's important to note that using the IR- based code generator may lengthen compile times due to the extra optimization steps.Therefore, it's advised to test your contract with and without this option enabled to measure the performance and gas cost implications.If the IR- based code generator significantly enhances your contract's performance or reduces gas costs, consider using the --via-ir flag during deployment.This way, you can leverage more advanced compiler optimizations without hindering your development workflow.

*Instances (1)*:
<details><summary> see instances </summary>

```solidity
File: foundry.toml

//@audit /2024-03-taiko/packages/protocol/foundry.toml
1: 

```
[Link to code](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/foundry.toml#L1)

</details>
