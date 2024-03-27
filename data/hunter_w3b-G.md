# Gas Optimization Taiko Contest

I have conducted a thorough audit of Taiko contest, focusing on optimizing gas saving for efficient and cost-effective operations. After rigorous analysis, I am pleased to present the following key findings and recommendations to help improve the gas optmization of `Taiko`:

When doing the refactoring, we’ve avoided including any changes that were `reported by the` [4naly3er](https://github.com/code-423n4/2024-03-taiko/blob/main/4naly3er-report.md) and we encourage you to go through the automated findings to maximum the amount of gas being saved.

| Num | Finding Issue                                                                                               | Instances |
| --- | :---------------------------------------------------------------------------------------------------------- | :-------- |
| 1   | Use `SSTORE2` or `SSTORE3` to store a lot of data                                                           | 1         |
| 2   | Use local variables for `emitting`                                                                          | 6         |
| 3   | Use the `inputs/results` of assignments rather than `re-reading` state variables                            | 12        |
| 4   | The result of function calls should be cached rather than `re-calling` the function                         | 33        |
| 5   | Internal functions only called once can be `inlined` to save gas                                            | 23        |
| 6   | Splitting `require()` statements that use `&&` saves gas                                                    | 4         |
| 7   | `require()` or `revert()` statements that check input arguments should be at the top of the function        | 4         |
| 8   | Using mappings instead of arrays to avoid length checks                                                     | 1         |
| 9   | `Do-While` loops are cheaper than for loops                                                                 | 35        |
| 10  | `selfbalance` is cheaper than `address(this).balance`                                                       | 2         |
| 11  | `REQUIRE()/REVERT()` strings longer than 32 bytes cost extra Gas                                            | 1         |
| 12  | Don't Initialize Variables with Default Value                                                               | 15        |
| 13  | Use assembly to check for `address(0)`                                                                      | 55        |
| 14  | `internal` functions not called by the contract should be removed to save deployment gas                    | 13        |
| 15  | `Calldata` is cheaper than `memory`                                                                         | 59        |
| 16  | State variables only set in the `constructor` should be declared `immutable`                                | 2         |
| 17  | `Stack variable` used as a cheaper cache for a state variable is only used once                             | 2         |
| 18  | Make `constructors` payable                                                                                 | 3         |
| 19  | Multiple `address/ID` mappings can be combined into a single mapping of an `address/ID` to a struct         | 7         |
| 20  | Using storage instead of `memory` for structs/arrays saves gas                                              | 2         |
| 21  | Use assembly to `emit` events                                                                               | 55        |
| 22  | Superfluous `event` fields                                                                                  | 1         |
| 23  | Usage of `uints`/`ints` smaller than 32 bytes (256 bits) incurs overhead                                    | 23        |
| 24  | `Emit` Used In Loop                                                                                         | 3         |
| 25  | `Private` functions used once can be inlined                                                                | 40        |
| 26  | Use `SUB` or `XOR` instead of `ISZERO(EQ())` to check for inequality                                        | 3         |
| 27  | Use assembly to calculate hashes to save gas                                                                | 28        |
| 28  | Do not `calculate` constants                                                                                | 2         |
| 29  | Assigning state variables directly with named struct constructors wastes gas                                | 15        |
| 30  | The use of a logical AND in place of double if is slightly less gas efficient                               | 23        |
| 31  | Avoid fetching a `low-level` call's return data by using assembly                                           | 1         |
| 32  | Duplicated `require()`/`revert()` checks should be refactored to a modifier or function                     | 3         |
| 33  | `State variable` read in a loop                                                                             | 15        |
| 34  | Storage `re-read` via storage pointer                                                                       | 4         |
| 35  | Inverting the condition of an `if-else-statement`                                                           | 2         |
| 36  | Timestamps and block numbers in storage do not need to be `uint256`                                         | 12        |
| 37  | Use fallback or receive instead of `deposit()` when transferring Ether                                      | 2         |
| 38  | Consider using alternatives to `OpenZeppelin`                                                               | 56        |
| 39  | A `MODIFIER` used only once and not being inherited should be inlined to save gas                           | 3         |
| 40  | Expressions for constant values such as a call to ` KECCAK256`(), should use IMMUTABLE rather than CONSTANT | 3         |
| 41  | Consider using `OZ` EnumerateSet in place of nested mappings                                                | 5         |
| 42  | Shorten the array rather than copying to a new one                                                          | 4         |

Total: `42` Instances.

## [G-01] Use `SSTORE2` or `SSTORE3` to store a lot of data

**Issue Description**\
The use of `SSTORE` opcode for storing persistent data on a key-value basis in `EVM` is very expensive in terms of gas consumption.

**Proposed Optimization**\
Instead of using `SSTORE` for storing data, it is recommended to store the data in the contract's bytecode during deployment. This approach is more gas-efficient as writing to the bytecode costs only 200 gas per byte, compared to `22,100` gas for writing 32 bytes using `SSTORE`.

**Estimated Gas Savings**\
Writing 32 bytes using `SSTORE` costs `22,100` gas, which translates to approximately 690 gas per byte. On the other hand, writing the same data to the contract's bytecode during deployment would cost only 200 gas per byte. Therefore, the estimated gas savings by using this optimization would be `(690 - 200) = 490` gas per byte of data stored.

**Attachments**

- **Code Snippets**

```solidity
File: contracts/signal/SignalService.sol

       assembly {
            sstore(slot_, _value)
        }
```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L265-L267

## [G-02] Use local variables for `emitting`

**Issue Description**\
The issue is related to the inefficient use of state variables when emitting events in contracts. Directly accessing state variables when emitting events can lead to unnecessary gas consumption due to additional read operations (e.g., Gwarmaccess or Gcoldsload).

**Proposed Optimization**\
Instead of directly accessing state variables when emitting events, it is recommended to use local variables or function parameters. By doing so, the contract can avoid unnecessary read operations from storage, resulting in gas savings.

**Estimated Gas Savings**\
The gas savings depend on the specific context and usage of the state variables. However, the following estimates can be provided:

- If the state variable has already been accessed within the function/modifier, using a local copy can save 100 gas (Gwarmaccess) per instance.
- If the state variable has not been accessed yet, using a local copy can save 2100 gas (Gcoldsload) per instance.

**Attachments**

- **Code Snippets**

    <details>
    <summary>Click to show 6 findings</summary>

  ```solidity
  File: contracts/L1/provers/Guardians.sol


  95              emit GuardiansUpdated(version, _newGuardians);
  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L95

  ```solidity
  File: contracts/L2/TaikoL2.sol


  157             emit Anchored(blockhash(parentId), gasExcess);


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L157

  ```solidity
  File: contracts/tokenvault/BridgedERC20Base.sol


  63                  emit MigratedTo(migratingAddress, _account, _amount);


  80                  emit MigratedTo(migratingAddress, _account, _amount);


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/tokenvault/BridgedERC20Base.sol#L80

  ```solidity
  File: contracts/verifiers/SgxVerifier.sol


  109                 emit InstanceDeleted(idx, instances[idx].addr);


  220                 emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/verifiers/SgxVerifier.sol#L220

## [G-03] Use the `inputs/results` of assignments rather than `re-reading` state variables

**Issue Description**\
The issue relates to the inefficient `re-reading` of state variables after they have been assigned a value within the same function. Re-reading state variables incurs additional gas costs due to the need to perform a storage read operation (`Gwarmaccess`).

**Proposed Optimization**\
Instead of re-reading state variables after they have been assigned a value, it is recommended to use the assigned value directly or store it in a local variable. This optimization avoids the unnecessary storage read operation and can lead to gas savings.

**Estimated Gas Savings**\
The estimated gas savings for each instance where a state variable is `re-read` after being assigned is 100 gas (Gwarmaccess). This saving applies to each occurrence of `re-reading` the state variable within the same function or modifier.

**Attachments**

- **Code Snippets**

    <details>
    <summary>Click to show 12 findings</summary>

  ```solidity
  File: contracts/L1/TaikoL1.sol


  67              (meta_, deposits_) = LibProposing.proposeBlock(state, config, this, _params, _txList);


  94              uint8 maxBlocksToVerify = LibProving.proveBlock(state, config, this, meta, tran, proof);


  181             a_ = state.slotA;


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/main/L1/TaikoL1.sol#L181

  ```solidity
  File: contracts/L1/provers/Guardians.sol


  88                  guardianIds[guardian] = guardians.length;


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L88

  ```solidity
  File: contracts/L2/TaikoL2.sol


  265                 uint256 excess = uint256(gasExcess) + _parentGasUsed;


  262             if (gasExcess > 0) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L262

  ```solidity
  File: contracts/common/AddressResolver.sol


  83              addr_ = payable(IAddressManager(addressManager).getAddress(_chainId, _name));


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L83

  ```solidity
  File: contracts/team/TimelockTokenPool.sol


  219             IERC20(taikoToken).transferFrom(sharedVault, _to, amountToWithdraw);


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L219

  ```solidity
  File: contracts/team/airdrop/ERC20Airdrop.sol


  63              IERC20(token).transferFrom(vault, user, amount);


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L63:63

  ```solidity
  File: contracts/tokenvault/BridgedERC20Base.sol


  63                  emit MigratedTo(migratingAddress, _account, _amount);


  80                  emit MigratedTo(migratingAddress, _account, _amount);


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L80:80

  ```solidity
  File: contracts/verifiers/SgxVerifier.sol


  218                 ids[i] = nextInstanceId;


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L218:218

    </details>

## [G-04] The result of function calls should be cached rather than `re-calling` the function

**Issue Description**\
The issue is related to the inefficient practice of calling the same function multiple times within a contract, leading to unnecessary gas consumption. When a function is called, its code is executed, and if the function is called multiple times, the same code is executed repeatedly, resulting in higher gas costs.

**Proposed Optimization**\
Instead of calling the same function multiple times, it is recommended to cache the result of the function call in a local variable. By doing so, the contract can avoid executing the function code repeatedly, leading to gas savings.

**Estimated Gas Savings**\
The estimated gas savings depend on the complexity and gas cost of the function being called. In general, the `gas savings` will be proportional to the number of times the function is called after the initial call. For each subsequent call, the gas cost of executing the function code is saved.

**Attachments**

- **Code Snippets**

    <details>

    <summary>Click to show 33 findings</summary>

  ```solidity
  File: contracts/automata-attestation/lib/PEMCertChainLib.sol


  111             tbsPtr = der.nextSiblingOf(tbsPtr);


  112             tbsPtr = der.nextSiblingOf(tbsPtr);


  117                 issuerPtr = der.firstChildOf(issuerPtr);


  127             tbsPtr = der.nextSiblingOf(tbsPtr);


  130                 uint256 notBeforePtr = der.firstChildOf(tbsPtr);


  144             tbsPtr = der.nextSiblingOf(tbsPtr);


  147                 uint256 subjectPtr = der.firstChildOf(tbsPtr);


  149                 subjectPtr = der.firstChildOf(subjectPtr);


  157             tbsPtr = der.nextSiblingOf(tbsPtr);


  161                 uint256 subjectPublicKeyInfoPtr = der.firstChildOf(tbsPtr);


  176                 sigPtr = der.nextSiblingOf(sigPtr);


  177                 bytes memory sigY = _trimBytes(der.bytesAt(sigPtr), 32);


  186                 tbsPtr = der.nextSiblingOf(tbsPtr);


  193                 tbsPtr = der.firstChildOf(tbsPtr);


  194                 tbsPtr = der.firstChildOf(tbsPtr);


  310                         if (BytesUtils.compareBytes(der.bytesAt(extnValueOidPtr), PCEID_OID)) {


  316                         if (BytesUtils.compareBytes(der.bytesAt(extnValueOidPtr), FMSPC_OID)) {


  318                             uint256 fmspcPtr = der.nextSiblingOf(extnValueOidPtr);


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L318

  ```solidity
  File: contracts/automata-attestation/utils/Asn1Decode.sol


  101                     || ((j.ixf() <= i.ixs()) && (i.ixl() <= j.ixl()))


  101                     || ((j.ixf() <= i.ixs()) && (i.ixl() <= j.ixl()))


  112             return der.substring(ptr.ixf(), ptr.ixl() + 1 - ptr.ixf());


  122             return der.substring(ptr.ixs(), ptr.ixl() + 1 - ptr.ixs());


  132             return der.readBytesN(ptr.ixf(), ptr.ixl() + 1 - ptr.ixf());


  144             uint256 len = ptr.ixl() + 1 - ptr.ixf();


  145             return uint256(der.readBytesN(ptr.ixf(), len) >> (32 - len) * 8);


  157             uint256 valueLength = ptr.ixl() + 1 - ptr.ixf();


  158             if (der[ptr.ixf()] == 0) {


  159                 return der.substring(ptr.ixf() + 1, valueLength - 1);


  161                 return der.substring(ptr.ixf(), valueLength);


  166             return der.keccak(ptr.ixf(), ptr.ixl() + 1 - ptr.ixf());


  170             return der.keccak(ptr.ixs(), ptr.ixl() + 1 - ptr.ixs());


  183             uint256 valueLength = ptr.ixl() + 1 - ptr.ixf();


  184             return der.substring(ptr.ixf() + 1, valueLength - 1);


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L184

    </details>

## [G-05] Internal functions only called once can be `inlined` to save gas

**Issue Description**\
The issue is related to the gas cost associated with function calls in contracts. When a function is not inlined, it requires additional instructions and stack operations, resulting in higher gas consumption.

**Proposed Optimization**\
To optimize gas usage, it is recommended to inline small functions whenever possible. Inlining a function eliminates the need for additional instructions and stack operations associated with function calls, leading to gas savings.

**Estimated Gas Savings**\
Not inlining a function costs approximately 20 to 40 gas due to the following factors:

- Two extra JUMP instructions (one for the function call and one for the return)
- Additional stack operations needed for function calls

By inlining small functions, the estimated gas savings range from 20 to 40 gas per function call.
**Attachments**

- **Code Snippets**

    <details>
    <summary>Click to show 23 findings</summary>

  ```solidity
  File: contracts/L1/TaikoL1.sol


  220         function _authorizePause(address)


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L220

  ```solidity
  File: contracts/L1/TaikoToken.sol


  105         function _mint(


  115         function _burn(


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L115

  ```solidity
  File: contracts/L1/libs/LibDepositing.sol


  122         function canDepositEthToL2(


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L122

  ```solidity
  File: contracts/L1/libs/LibProposing.sol


  287         function isBlobReusable(


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L287

  ```solidity
  File: contracts/L1/libs/LibUtils.sol


  70          function getTransitionId(


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L70

  ```solidity
  File: contracts/automata-attestation/AutomataDcapV3Attestation.sol


  126         function _attestationTcbIsValid(TCBInfoStruct.TCBStatus status)


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L126

  ```solidity
  File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol


  267         function parseCerificationChainBytes(


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L267

  ```solidity
  File: contracts/automata-attestation/utils/BytesUtils.sol


  56          function compare(


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L56

  ```solidity
  File: contracts/automata-attestation/utils/RsaVerify.sol


  43          function pkcs1Sha256(


  212         function pkcs1Sha1(


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L212

  ```solidity
  File: contracts/automata-attestation/utils/X509DateUtils.sol


  34          function toUnixTimestamp(


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L34

  ```solidity
  File: contracts/common/EssentialContract.sol


  109         function __Essential_init(address _owner) internal virtual {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L109

  ```solidity
  File: contracts/libs/LibAddress.sol


  42          function sendEther(address _to, uint256 _amount) internal {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L42

  ```solidity
  File: contracts/signal/SignalService.sol


  206         function _verifyHopProof(


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L206

  ```solidity
  File: contracts/team/airdrop/MerkleClaimable.sol


  77          function _verifyMerkleProof(


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L77

  ```solidity
  File: contracts/thirdparty/optimism/Bytes.sol


  91          function slice(bytes memory _bytes, uint256 _start) internal pure returns (bytes memory) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L91

  ```solidity
  File: contracts/thirdparty/optimism/rlp/RLPReader.sol


  102         function readList(bytes memory _in) internal pure returns (RLPItem[] memory out_) {


  128         function readBytes(bytes memory _in) internal pure returns (bytes memory out_) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L128

  ```solidity
  File: contracts/thirdparty/optimism/rlp/RLPWriter.sol


  13          function writeBytes(bytes memory _in) internal pure returns (bytes memory out_) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L13

  ```solidity
  File: contracts/thirdparty/optimism/trie/MerkleTrie.sol


  68          function get(


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L68

  ```solidity
  File: contracts/tokenvault/BridgedERC20.sol


  163         function _mint(


  173         function _burn(


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L173

    </details>

## [G-06] Splitting `require()` statements that use `&&` saves gas

**Issue Description**\
The issue is related to the gas cost associated with the usage of the `&&` operator in require statements in contracts. When multiple conditions are combined using the && operator in a single require statement, it can lead to higher gas consumption.

**Proposed Optimization**\
To optimize gas usage, it is recommended to split the require statements that use the `&&` operator into multiple require statements, each with a single condition. This approach can save gas in the long run, despite having a larger deployment gas cost.

**Estimated Gas Savings**\
Splitting a require statement that uses the && operator saves approximately 3 gas per runtime call. However, it does incur a larger deployment gas cost due to the increased bytecode size.

The actual gas savings depend on the number of runtime calls to the contract. If there are enough runtime calls, the change ends up being cheaper overall due to the cumulative gas savings of 3 gas per call.

**Attachments**

- **Code Snippets**

    <details>
    <summary>Click to show 4 findings</summary>

  ```solidity
  File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol


  77              require(
  78                  localEnclaveReport.reserved3.length == 96 && localEnclaveReport.reserved4.length == 60
  79                      && localEnclaveReport.reportData.length == 64,
  80                  "local QE report has wrong length"
  81              );


  82              require(
  83                  pckSignedQeReport.reserved3.length == 96 && pckSignedQeReport.reserved4.length == 60
  84                      && pckSignedQeReport.reportData.length == 64,
  85                  "QE report has wrong length"
  86              );


  94              require(
  95                  v3Quote.v3AuthData.ecdsa256BitSignature.length == 64
  96                      && v3Quote.v3AuthData.ecdsaAttestationKey.length == 64
  97                      && v3Quote.v3AuthData.qeReportSignature.length == 64,
  98                  "Invalid ECDSA signature format"
  99              );


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L94:99

  ```solidity
  File: contracts/automata-attestation/utils/BytesUtils.sol


  335                 require(char >= 0x30 && char <= 0x7A, "invalid char");


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L335

    </details>

## [G-07] `require()` or `revert()` statements that check input arguments should be at the top of the function

**Issue Description**\
The issue is related to the order of checks performed in functions. When a function performs multiple checks, the order in which these checks are executed can impact gas consumption. Checks involving constants should be performed before checks involving state variables, function calls, and calculations.

**Proposed Optimization**\
To optimize gas usage, it is recommended to order the checks in a function such that checks involving constants are performed first, followed by checks involving state variables, function calls, and calculations. By performing the constant checks first, the function can revert early without incurring the gas cost of loading state variables or executing complex operations.

**Estimated Gas Savings**\
The estimated gas savings depend on the specific checks involved and the number of times the function is called. However, the following estimates can be provided:

-If a function performs a check involving a state variable or a function call, and this check is executed before constant checks, the gas cost of loading the state variable (`Gcoldsload`) or executing the function call is incurred unnecessarily if the function ultimately reverts due to a failed constant check.
-The gas cost of Gcoldsload is approximately 2100 gas.

**Attachments**

- **Code Snippets**

    <details>
    <summary>Click to show 4 findings</summary>

  ```solidity
  File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol


  91              require(
  92                  v3Quote.v3AuthData.certification.decodedCertDataArray.length == 3, "3 certs in chain"
  93              );


  100             require(
  101                 v3Quote.v3AuthData.qeAuthData.parsedDataSize
  102                     == v3Quote.v3AuthData.qeAuthData.data.length,
  103                 "Invalid QEAuthData size"
  104             );


  94              require(
  95                  v3Quote.v3AuthData.ecdsa256BitSignature.length == 64
  96                      && v3Quote.v3AuthData.ecdsaAttestationKey.length == 64
  97                      && v3Quote.v3AuthData.qeReportSignature.length == 64,
  98                  "Invalid ECDSA signature format"
  99              );


  87              require(
  88                  v3Quote.v3AuthData.certification.certType == 5,
  89                  "certType must be 5: Concatenated PCK Cert Chain (PEM formatted)"
  90              );


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L87:90

    </details>

## [G-08] Using mappings instead of arrays to avoid length checks

**Issue Description**\
When fetching an element from an array, Solidity adds `bytecode` that checks if the index being accessed is within the valid range of the array's length. This bounds check is performed to prevent reading from unallocated or allocated storage/memory locations, but it incurs additional gas costs.

**Proposed Optimization**\
To optimize gas usage, it is recommended to use `mappings` instead of arrays when storing and fetching elements with fixed keys or indexes. `Mappings` do not have the same bounds checking as arrays, allowing direct access to storage slots without the additional gas cost of bounds checking.

**Estimated Gas Savings**\
The estimated gas savings by using mappings instead of arrays for fetching elements can be significant. According to the provided example, the gas cost for fetching an element from an array `get(0)` is `4860` gas, while the gas cost for fetching an element from a mapping (get(0)) is 2758 gas. This results in a gas saving of `approximately` 2102 gas per element fetch operation.

**Attachments**

- **Code Snippets**

```solidity
File: contracts/L1/provers/Guardians.sol

    address[] public guardians;
```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol

## [G-09] `Do-While` loops are cheaper than for loops

**Issue Description**\
The choice between using a for loop or a do-while loop can impact gas consumption.

**Proposed Optimization**\
To optimize gas usage, it is recommended to use `do-while` loops instead of for loops, even if an additional condition check is required to handle the case where the loop does not execute at all. Despite the additional condition check, `do-while` loops are generally cheaper in terms of gas cost compared to for loops.

**Estimated Gas Savings**\

**Attachments**

- **Code Snippets**

    <details>
    <summary>Click to show 29 findings</summary>

  ```solidity
  File: contracts/L1/hooks/AssignmentHook.sol


  172             for (uint256 i; i < _tierFees.length; ++i) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L172:172

  ```solidity
  File: contracts/L1/libs/LibDepositing.sol


  86                  for (uint256 i; i < deposits_.length;) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L86:86

  ```solidity
  File: contracts/L1/libs/LibProposing.sol


  244                 for (uint256 i; i < params.hookCalls.length; ++i) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L244:244

  ```solidity
  File: contracts/L1/provers/Guardians.sol


  74              for (uint256 i; i < guardians.length; ++i) {


  80              for (uint256 i = 0; i < _newGuardians.length; ++i) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L80:80

  ```solidity
  File: contracts/automata-attestation/AutomataDcapV3Attestation.sol


  80              for (uint256 i; i < serialNumBatch.length; ++i) {


  95              for (uint256 i; i < serialNumBatch.length; ++i) {


  191             for (uint256 i; i < enclaveId.tcbLevels.length; ++i) {


  214             for (uint256 i; i < tcb.tcbLevels.length; ++i) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L214:214

  ```solidity
  File: contracts/automata-attestation/lib/PEMCertChainLib.sol


  244             for (uint256 i; i < split.length; ++i) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L244:244

  ```solidity
  File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol


  153             for (uint256 i; i < encoded.length; ++i) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L153:153

  ```solidity
  File: contracts/automata-attestation/utils/RsaVerify.sol


  174             for (uint256 i; i < _sha256.length; ++i) {


  283             for (uint256 i; i < sha1Prefix.length; ++i) {


  290             for (uint256 i; i < _sha1.length; ++i) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L290:290

  ```solidity
  File: contracts/bridge/Bridge.sol


  90              for (uint256 i; i < _msgHashes.length; ++i) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/main/bridge/Bridge.sol#L90:90

  ```solidity
  File: contracts/signal/SignalService.sol


  104             for (uint256 i; i < hopProofs.length; ++i) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/main/signal/SignalService.sol#L104:104

  ```solidity
  File: contracts/team/airdrop/ERC721Airdrop.sol


  59              for (uint256 i; i < tokenIds.length; ++i) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/main/team/airdrop/ERC721Airdrop.sol#L59:59

  ```solidity
  File: contracts/thirdparty/optimism/rlp/RLPWriter.sol


  66              for (uint256 j = 0; j < out_.length; j++) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66:66

  ```solidity
  File: contracts/thirdparty/optimism/trie/MerkleTrie.sol


  85              for (uint256 i = 0; i < proof.length; i++) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85:85

  ```solidity
  File: contracts/tokenvault/ERC1155Vault.sol


  47              for (uint256 i; i < _op.amounts.length; ++i) {


  251                     for (uint256 i; i < _op.tokenIds.length; ++i) {


  269                     for (uint256 i; i < _op.tokenIds.length; ++i) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L269:269

  ```solidity
  File: contracts/tokenvault/ERC721Vault.sol


  34              for (uint256 i; i < _op.tokenIds.length; ++i) {


  170                 for (uint256 i; i < _tokenIds.length; ++i) {


  175                 for (uint256 i; i < _tokenIds.length; ++i) {


  197                     for (uint256 i; i < _op.tokenIds.length; ++i) {


  210                     for (uint256 i; i < _op.tokenIds.length; ++i) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L210:210

  ```solidity
  File: contracts/verifiers/SgxVerifier.sol


  104             for (uint256 i; i < _ids.length; ++i) {


  210             for (uint256 i; i < _instances.length; ++i) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210:210

    </details>

## [G-10] `selfbalance` is cheaper than `address(this).balance` (more efficient in certain scenarios)

**Issue Description**\
The choice between using address(this).balance or the selfbalance() function from the assembly language can impact gas consumption.

**Proposed Optimization**\
To optimize gas usage, it is recommended to use the `selfbalance()` function from Yul instead of `address(this).balance` when retrieving the balance of a contract. The selfbalance() function can be more efficient in certain scenarios.

**Estimated Gas Savings**\
The estimated gas savings from using selfbalance() instead of address(this).balance can vary depending on the specific use case and the overall complexity of the contract. However, in general, selfbalance() can save a few gas units compared to address(this).balance.

**Attachments**

- **Code Snippets**

```solidity
File: contracts/L1/hooks/AssignmentHook.sol

125        if (address(this).balance > 0) {

```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L125

```solidity
File: contracts/L1/libs/LibProposing.sol

260            if (address(this).balance != 0) {

```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L260

## [G-11] `REQUIRE()/REVERT()` strings longer than 32 bytes cost extra Gas

**Issue Description**\
When using the `REQUIRE()` strings longer than 32 bytes incur additional gas costs due to the way they are stored and handled.

**Proposed Optimization**\
Refactor the code to avoid passing strings longer than 32 bytes to the `REQUIRE()` or REVERT() functions. Instead, consider using more concise error messages or splitting longer messages into multiple smaller ones.

**Estimated Gas Savings**\

**Attachments**

- **Code Snippets**

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol


require(currentKeyIndex <= key.length, "MerkleTrie: key index exceeds total key length");

```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L89:89

## [G-12] Don't Initialize Variables with Default Value

<details>
<summary>Click to show 15 findings</summary>

```solidity
File: contracts/L1/provers/Guardians.sol


for (uint256 i = 0; i < _newGuardians.length; ++i) {

```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L80:80

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol


uint256 index = 0;

```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L51:51

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol


bytes4 internal constant SUPPORTED_TEE_TYPE = 0;

```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L18:18

```solidity
File: contracts/automata-attestation/utils/BytesUtils.sol


for (uint256 idx = 0; idx < shortest; idx += 32) {

uint256 ret = 0;

```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L331:331

```solidity
File: contracts/automata-attestation/utils/X509DateUtils.sol


uint256 timestamp = 0;

```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L46:46

```solidity
File: contracts/thirdparty/optimism/rlp/RLPReader.sol


uint256 itemCount = 0;

```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L72:72

```solidity
File: contracts/thirdparty/optimism/rlp/RLPWriter.sol


uint256 i = 0;

for (uint256 j = 0; j < out_.length; j++) {

```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66:66

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol


uint8 internal constant PREFIX_EXTENSION_EVEN = 0;

uint256 currentKeyIndex = 0;

for (uint256 i = 0; i < proof.length; i++) {

for (uint256 i = 0; i < length;) {

```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L208:208

</details>

## [G-13] Use assembly to check for `address(0)`

**Issue Description**\
Currently, the contracts may be using the `address(0)` check conventionally, which can consume unnecessary gas.

**Proposed Optimization**\
Utilize assembly to check for the zero address `address(0)` more efficiently, resulting in gas savings.

**Estimated Gas Savings**\
Implementing this optimization can save approximately `6` gas per instance where the zero address check is performed.

**Attachments**

- **Code Snippets**

    <details>
    <summary>Click to show 55 findings</summary>

  ```solidity
  File: contracts/L1/hooks/AssignmentHook.sol


  109             if (assignment.feeToken == address(0)) {


  120             if (input.tip != 0 && block.coinbase != address(0)) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L120:120

  ```solidity
  File: contracts/L1/libs/LibDepositing.sol


  44              address recipient_ = _recipient == address(0) ? msg.sender : _recipient;


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L44:44

  ```solidity
  File: contracts/L1/libs/LibProposing.sol


  81              if (params.assignedProver == address(0)) {


  85              if (params.coinbase == address(0)) {


  310                 if (proposerOne != address(0) && msg.sender != proposerOne) {


  316             return proposer == address(0) || msg.sender == proposer;


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L316:316

  ```solidity
  File: contracts/L1/libs/LibProving.sol


  163                 if (verifier != address(0)) {


  224                     assert(ts.validityBond == 0 && ts.contestBond == 0 && ts.contester == address(0));


  239                     if (ts.contester != address(0)) revert L1_ALREADY_CONTESTED();


  363             if (_ts.contester != address(0)) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L363:363

  ```solidity
  File: contracts/L1/libs/LibVerifying.sol


  145                     if (ts.contester != address(0)) {


  148                         if (tierProvider == address(0)) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L148:148

  ```solidity
  File: contracts/L1/provers/Guardians.sol


  82                  if (guardian == address(0)) revert INVALID_GUARDIAN();


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L82:82

  ```solidity
  File: contracts/L2/TaikoL2.sol


  172             if (_to == address(0)) revert L2_INVALID_PARAM();


  173             if (_token == address(0)) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L173:173

  ```solidity
  File: contracts/bridge/Bridge.sol


  124             if (_message.srcOwner == address(0) || _message.destOwner == address(0)) {


  124             if (_message.srcOwner == address(0) || _message.destOwner == address(0)) {


  270                     _message.to == address(0) || _message.to == address(this)


  291                     _message.refundTo == address(0) ? _message.destOwner : _message.refundTo;


  398             enabled_ = destBridge_ != address(0);


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L398:398

  ```solidity
  File: contracts/common/AddressResolver.sol


  81              if (addressManager == address(0)) revert RESOLVER_INVALID_MANAGER();


  85              if (!_allowZeroAddress && addr_ == address(0)) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L85:85

  ```solidity
  File: contracts/common/EssentialContract.sol


  105             if (_addressManager == address(0)) revert ZERO_ADDR_MANAGER();


  110             _transferOwnership(_owner == address(0) ? msg.sender : _owner);


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L110:110

  ```solidity
  File: contracts/libs/LibAddress.sol


  24              if (_to == address(0)) revert ETH_TRANSFER_FAILED();


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L24:24

  ```solidity
  File: contracts/signal/SignalService.sol


  36              if (_app == address(0)) revert SS_INVALID_SENDER();


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L36:36

  ```solidity
  File: contracts/team/TimelockTokenPool.sol


  121             if (_taikoToken == address(0)) revert INVALID_PARAM();


  124             if (_costToken == address(0)) revert INVALID_PARAM();


  127             if (_sharedVault == address(0)) revert INVALID_PARAM();


  136             if (_recipient == address(0)) revert INVALID_PARAM();


  169             if (_to == address(0)) revert INVALID_PARAM();


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L169:169

  ```solidity
  File: contracts/tokenvault/BaseNFTVault.sol


  149             if (_op.token == address(0)) revert VAULT_INVALID_TOKEN();


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L149:149

  ```solidity
  File: contracts/tokenvault/BridgedERC20Base.sol


  102             return migratingAddress != address(0) && !migratingInbound;


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L102:102

  ```solidity
  File: contracts/tokenvault/ERC1155Vault.sol


  64                  destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,


  108             if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();


  249                 if (bridgedToCanonical[_op.token].addr != address(0)) {


  293             if (btoken_ == address(0)) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L293:293

  ```solidity
  File: contracts/tokenvault/ERC20Vault.sol


  158             if (_btokenNew == address(0) || bridgedToCanonical[_btokenNew].addr != address(0)) {


  158             if (_btokenNew == address(0) || bridgedToCanonical[_btokenNew].addr != address(0)) {


  170             if (btokenOld_ != address(0)) {


  215             if (_op.token == address(0)) revert VAULT_INVALID_TOKEN();


  227                 destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,


  267             if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();


  358             if (bridgedToCanonical[_token].addr != address(0)) {


  397             if (btoken == address(0)) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L397:397

  ```solidity
  File: contracts/tokenvault/ERC721Vault.sol


  50                  destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,


  91              if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();


  195                 if (bridgedToCanonical[_op.token].addr != address(0)) {


  230             if (btoken_ == address(0)) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L230:230

  ```solidity
  File: contracts/tokenvault/LibBridgedToken.sol


  21                  _srcToken == address(0) || _srcChainId == 0 || _srcChainId == block.chainid


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L21:21

  ```solidity
  File: contracts/verifiers/SgxVerifier.sol


  107                 if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();


  124             if (automataDcapAttestation == address(0)) {


  215                 if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();


  234             if (instance == address(0)) return false;


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L234:234

    </details>

## [G-14] `internal` functions not called by the contract should be removed to save deployment gas

**Issue Description**\
Unused internal functions within the contract contribute to unnecessary deployment gas costs.

**Proposed Optimization**\
Remove `internal` functions that are not called within the contract. If these functions are required by an interface, consider inheriting from that interface and using the override keyword to maintain compatibility.

**Estimated Gas Savings**\
Removing unused `internal` functions can result in significant deployment gas savings, depending on the number and complexity of the functions removed. The exact savings would vary based on the size and structure of the contract.

**Attachments**

- **Code Snippets**

    <details>
    <summary>Click to show 13 findings</summary>

  ```solidity
  File: contracts/L1/TaikoToken.sol


      function _beforeTokenTransfer(
          address _from,
          address _to,
          uint256 _amount
      )
          internal
          override(ERC20Upgradeable, ERC20SnapshotUpgradeable)
      {
          super._beforeTokenTransfer(_from, _to, _amount);
      }

      function _afterTokenTransfer(
          address _from,
          address _to,
          uint256 _amount
      )
          internal
          override(ERC20Upgradeable, ERC20VotesUpgradeable)
      {
          super._afterTokenTransfer(_from, _to, _amount);
      }

  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L94:103

  ```solidity
  File: contracts/L1/gov/TaikoGovernor.sol


      function _execute(
          uint256 _proposalId,
          address[] memory _targets,
          uint256[] memory _values,
          bytes[] memory _calldatas,
          bytes32 _descriptionHash
      )
          internal
          override(GovernorUpgradeable, GovernorTimelockControlUpgradeable)
      {
          super._execute(_proposalId, _targets, _values, _calldatas, _descriptionHash);
      }

      function _cancel(
          address[] memory _targets,
          uint256[] memory _values,
          bytes[] memory _calldatas,
          bytes32 _descriptionHash
      )
          internal
          override(GovernorUpgradeable, GovernorTimelockControlUpgradeable)
          returns (uint256)
      {
          return super._cancel(_targets, _values, _calldatas, _descriptionHash);
      }

      function _executor()
          internal
          view
          override(GovernorUpgradeable, GovernorTimelockControlUpgradeable)
          returns (address)
      {
          return super._executor();
      }

  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L153:160

  ```solidity
  File: contracts/common/AddressManager.sol


      function _authorizePause(address) internal pure override {
          revert AM_UNSUPPORTED();
      }

  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L58:60

  ```solidity
  File: contracts/signal/SignalService.sol


      function _authorizePause(address) internal pure override {
          revert SS_UNSUPPORTED();
      }

  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L231:233

  ```solidity
  File: contracts/tokenvault/BridgedERC20.sol


      function _mintToken(address _account, uint256 _amount) internal override {
          _mint(_account, _amount);
      }

      function _burnToken(address _from, uint256 _amount) internal override {
          _burn(_from, _amount);
      }

      function _beforeTokenTransfer(
          address _from,
          address _to,
          uint256 _amount
      )
          internal
          override(ERC20Upgradeable, ERC20SnapshotUpgradeable)
      {
          if (_to == address(this)) revert BTOKEN_CANNOT_RECEIVE();
          if (paused()) revert INVALID_PAUSE_STATUS();
          super._beforeTokenTransfer(_from, _to, _amount);
      }

      function _afterTokenTransfer(
          address _from,
          address _to,
          uint256 _amount
      )
          internal
          override(ERC20Upgradeable, ERC20VotesUpgradeable)
      {
          super._afterTokenTransfer(_from, _to, _amount);
      }

  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L152:161

  ```solidity
  File: contracts/tokenvault/adapters/USDCAdapter.sol


      function _mintToken(address _account, uint256 _amount) internal override {
          usdc.mint(_account, _amount);
      }

      function _burnToken(address _from, uint256 _amount) internal override {
          usdc.transferFrom(_from, address(this), _amount);
          usdc.burn(_amount);
      }

  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L47:50

    </details>

## [G-15] `Calldata` is cheaper than `memory`

**Issue Description**\
The contract functions are currently using `memory` to load and process data. Memory is more expensive in terms of gas costs compared to calldata, especially when the data does not need to be modified within the function.

**Proposed Optimization**\
To optimize the gas costs, we can use `calldata` instead of memory for loading function inputs or data that does not require modification. Calldata is cheaper as it involves fewer operations and lower gas costs compared to memory.

**Estimated Gas Savings**\
The exact gas savings will depend on the size of the data being processed and the frequency of function calls. However, using calldata can result in significant gas savings, especially for larger data and high-frequency function calls.

**Attachments**

- **Code Snippets**

    <details>
    <summary>Click to show 59 findings</summary>

  ```solidity
  File: contracts/L1/gov/TaikoGovernor.sol

  49        address[] memory _targets,

  50        uint256[] memory _values,

  51        bytes[] memory _calldatas,

  70        address[] memory _targets,

  71        uint256[] memory _values,

  72        string[] memory _signatures,

  73        bytes[] memory _calldatas,


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L49

  ```solidity
  File: contracts/L1/hooks/AssignmentHook.sol


  65              bytes memory _data


  63              TaikoData.Block memory _blk,


  64              TaikoData.BlockMetadata memory _meta,


  138             ProverAssignment memory _assignment,


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L138

  ```solidity
  File: contracts/L1/hooks/IHook.sol


  14              TaikoData.Block memory _blk,


  16              bytes memory _data


  15              TaikoData.BlockMetadata memory _meta,


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/IHook.sol#L15

  ```solidity
  File: contracts/L1/libs/LibUtils.sol


  54              TaikoData.Config memory _config,


  25              TaikoData.Config memory _config,


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L25

  ```solidity
  File: contracts/L1/libs/LibVerifying.sol


  49              TaikoData.Config memory _config,


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L49

  ```solidity
  File: contracts/L1/provers/Guardians.sol


  54              address[] memory _newGuardians,


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L54

  ```solidity
  File: contracts/L2/TaikoL2EIP1559Configurable.sol


  26              Config memory _newConfig,


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L26

  ```solidity
  File: contracts/automata-attestation/lib/PEMCertChainLib.sol


  41              bytes memory pemChain,


  75              bytes memory der,

  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/main/automata-attestation/lib/PEMCertChainLib.sol#L75

  ```solidity
  File: contracts/automata-attestation/utils/SigVerifyLib.sol


  114             bytes memory tbs,


  98              bytes memory signature,


  27              PublicKey memory publicKey,


  116             bytes memory publicKey


  25              bytes memory tbs,


  97              bytes memory tbs,


  115             bytes memory signature,


  26              bytes memory signature,


  81              bytes memory signature,


  99              bytes memory publicKey


  80              bytes memory tbs,


  55              bytes memory tbs,


  82              bytes memory publicKey


  57              PublicKey memory publicKey,


  56              bytes memory signature,


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L56

  ```solidity
  File: contracts/bridge/Bridge.sol


  449         function hashMessage(Message memory _message) public pure returns (bytes32) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L449

  ```solidity
  File: contracts/bridge/IBridge.sol


  155         function hashMessage(Message memory _message) external pure returns (bytes32);


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L155

  ```solidity
  File: contracts/team/TimelockTokenPool.sol


  168         function withdraw(address _to, bytes memory _sig) external {


  135         function grant(address _recipient, Grant memory _grant) external onlyOwner {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L135

  ```solidity
  File: contracts/tokenvault/BridgedERC1155.sol


  43              string memory _symbol,


  85              uint256[] memory _tokenIds,


  86              uint256[] memory _amounts


  44              string memory _name


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L44

  ```solidity
  File: contracts/tokenvault/BridgedERC20.sol


  59              string memory _name


  58              string memory _symbol,


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L58

  ```solidity
  File: contracts/tokenvault/BridgedERC721.sol


  37              string memory _name


  36              string memory _symbol,


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L36

  ```solidity
  File: contracts/tokenvault/ERC1155Vault.sol


  39          function sendToken(BridgeTransferOp memory _op)


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L39

  ```solidity
  File: contracts/tokenvault/ERC721Vault.sol


  26          function sendToken(BridgeTransferOp memory _op)


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L26

  ```solidity
  File: contracts/verifiers/SgxVerifier.sol


  172             TaikoData.Transition memory _tran,


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L172

    </details>

## [G-16] State variables only set in the `constructor` should be declared `immutable`

**Issue Description**\
The contracts is currently using state variables that are only set in the `constructor` but are not declared as immutable. This results in unnecessary gas costs for setting and accessing these variables.

**Proposed Optimization**\
To optimize the gas costs, we can declare state variables that are only set in the constructor as immutable. This will avoid the gas cost of setting the variable in the constructor (`Gsset - 20000 gas`) and replace the first access in each transaction (Gcoldsload - 2100 gas) and each access thereafter (Gwarmaccess - 100 gas) with a PUSH32 (3 gas).

**Estimated Gas Savings**\
Gsset - 20000 gas

**Attachments**

- **Code Snippets**

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol


52          address public owner;


```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L52

```solidity
File: contracts/automata-attestation/utils/SigVerifyLib.sol


18          address private ES256VERIFIER;


```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L18

## [G-17] `Stack variable` used as a cheaper cache for a state variable is only used once

**Issue Description**\
If the variable is only accessed once, it's cheaper to use the state variable directly that one time, and save the 3 gas the extra stack assignment would spend.

**Attachments**

- **Code Snippets**

```solidity
File: contracts/L1/provers/Guardians.sol


133                 for (uint256 i; i < guardiansLength; ++i) {


```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L133

```solidity
File: contracts/team/TimelockTokenPool.sol


152             uint128 amountVoided = _voidGrant(r.grant);


```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L152

## [G-18] Make `constructors` payable

**Issue Description**\
Payable functions cost less gas to execute, since the compiler does not have to add extra checks to ensure that a payment wasn't provided. A constructor can safely be marked as payable, since only the deployer would be able to pass funds, and the project itself would not pass any funds.

**Proposed Optimization**\

```solidity
// SPDX-License-Identifier: UNLICENSED
pragma solidity 0.8.20;

contract A {}

contract B {
    constructor() payable {}
}
```

**Estimated Gas Savings**\
Making the constructor payable saved 200 gas on deployment. This is because non-payable functions have an implicit `require(msg.value == 0)` inserted in them. Additionally, fewer bytecode at deploy time mean less gas cost due to smaller calldata.

**Attachments**

- **Code Snippets**

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol


54          constructor(address sigVerifyLibAddr, address pemCertLibAddr) {
55              sigVerifyLib = ISigVerifyLib(sigVerifyLibAddr);
56              pemCertLib = PEMCertChainLib(pemCertLibAddr);
57              owner = msg.sender;
58          }


```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L54

```solidity
File: contracts/automata-attestation/utils/SigVerifyLib.sol


20          constructor(address es256Verifier) {
21              ES256VERIFIER = es256Verifier;
22          }


```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L20

```solidity
File: contracts/common/EssentialContract.sol


64          constructor() {
65              _disableInitializers();
66          }


```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L64

## [G-19] Multiple `address/ID` mappings can be combined into a single mapping of an `address/ID` to a struct, where appropriate

**Issue Description**\
Saves a storage slot for the mapping. Depending on the circumstances and sizes of types, can avoid a Gsset `20000 gas` per mapping combined. Reads and subsequent writes can also be cheaper when a function requires both values and they both fit in the same storage slot. Finally, if both fields are accessed in the same function, can save `~42` gas per access due to not having to recalculate the key's keccak256 hash `Gkeccak256 - 30 gas` and that calculation's associated stack operations.

**Proposed Optimization**\
To optimize the gas costs, we can combine multiple address/ID mappings into a single mapping of an address/ID to a struct, where appropriate. This can save a storage slot for the mapping and avoid a Gsset (20000 gas) per mapping combined. Reads and subsequent writes can also be cheaper when a function requires both values and they both fit in the same storage slot. Finally, if both fields are accessed in the same function, this can save ~42 gas per access due to not having to recalculate the key's keccak256 hash (Gkeccak256 - 30 gas) and that calculation's associated stack operations.

**Attachments**

- **Code Snippets**

```solidity
File: contracts/L1/TaikoData.sol


181             mapping(uint64 blockId_mod_blockRingBufferSize => Block blk) blocks;

183             mapping(uint64 blockId => mapping(bytes32 parentHash => uint32 transitionId)) transitionIds;


```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L181

```solidity
File: contracts/bridge/Bridge.sol


35          mapping(bytes32 msgHash => Status status) public messageStatus;
46          mapping(bytes32 msgHash => ProofReceipt receipt) public proofReceipt;


42          mapping(address addr => bool banned) public addressBanned;


```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L35

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol


22          mapping(address addr => uint256 amountClaimed) public claimedAmount;

25          mapping(address addr => uint256 amountWithdrawn) public withdrawnAmount;


```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L22

## [G-20] Using storage instead of `memory` for structs/arrays saves gas

When fetching data from a storage location, assigning the data to a memory variable causes all fields of the struct/array to be read from storage, which incurs a Gcoldsload (2100 gas) for each field of the struct/array. If the fields are read from the new memory variable, they incur an additional MLOAD rather than a cheap stack read. Instead of declearing the variable with the memory keyword, declaring the variable with the storage keyword and caching any fields that need to be re-read in stack variables, will be much cheaper, only incuring the Gcoldsload for the fields actually read. The only time it makes sense to read the whole struct/array into a memory variable, is if the full struct/array is being returned by the function, is being passed to a function that requires memory, or if the array/struct is being read from another memory array/struct

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol


180             EnclaveIdStruct.EnclaveId memory enclaveId = qeIdentity;


```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L180

```solidity
File: contracts/tokenvault/ERC20Vault.sol


171                 CanonicalERC20 memory ctoken = bridgedToCanonical[btokenOld_];


```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L171

## [G-21] Use assembly to emit events

**Issue Description**\
Using the [scratch space](https://github.com/Vectorized/solady/blob/30558f5402f02351b96eeb6eaf32bcea29773841/src/tokens/ERC1155.sol#L501-L504) for event arguments (two words or fewer) will save gas over needing Solidity's full abi memory expansion used for emitting normally.

**Attachments**

- **Code Snippets**

    <details>
    <summary>Click to show 55 findings</summary>

  ```solidity
  File: contracts/L1/hooks/AssignmentHook.sol


  129             emit BlockAssigned(_blk.assignedProver, _meta, assignment);


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L129

  ```solidity
  File: contracts/L1/libs/LibDepositing.sol


  50              emit EthDeposited(
  51                  TaikoData.EthDeposit({
  52                      recipient: recipient_,
  53                      amount: uint96(msg.value),
  54                      id: _state.slotA.numEthDeposits
  55                  })
  56              );


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L50

  ```solidity
  File: contracts/L1/libs/LibProposing.sol


  166                         emit BlobCached(meta_.blobHash);


  273             emit BlockProposed({
  274                 blockId: blk.blockId,
  275                 assignedProver: blk.assignedProver,
  276                 livenessBond: _config.livenessBond,
  277                 meta: meta_,
  278                 depositsProcessed: deposits_
  279             });


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L273

  ```solidity
  File: contracts/L1/libs/LibProving.sol


  80              emit ProvingPaused(_pause);


  209                 emit TransitionProved({
  210                     blockId: blk.blockId,
  211                     tran: _tran,
  212                     prover: msg.sender,
  213                     validityBond: tier.validityBond,
  214                     tier: _proof.tier
  215                 });


  230                     emit TransitionProved({
  231                         blockId: blk.blockId,
  232                         tran: _tran,
  233                         prover: msg.sender,
  234                         validityBond: 0,
  235                         tier: _proof.tier
  236                     });


  254                     emit TransitionContested({
  255                         blockId: blk.blockId,
  256                         tran: _tran,
  257                         contester: msg.sender,
  258                         contestBond: tier.contestBond,
  259                         tier: _proof.tier
  260                     });


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L254

  ```solidity
  File: contracts/L1/libs/LibVerifying.sol


  73              emit BlockVerified({
  74                  blockId: 0,
  75                  assignedProver: address(0),
  76                  prover: address(0),
  77                  blockHash: _genesisBlockHash,
  78                  stateRoot: 0,
  79                  tier: 0,
  80                  contestations: 0
  81              });


  198                     emit BlockVerified({
  199                         blockId: blockId,
  200                         assignedProver: blk.assignedProver,
  201                         prover: ts.prover,
  202                         blockHash: blockHash,
  203                         stateRoot: stateRoot,
  204                         tier: ts.tier,
  205                         contestations: ts.contestations
  206                     });


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L198

  ```solidity
  File: contracts/L1/provers/GuardianProver.sol


  54              emit GuardianApproval(msg.sender, _meta.id, _tran.blockHash, approved_);


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L54

  ```solidity
  File: contracts/L1/provers/Guardians.sol


  95              emit GuardiansUpdated(version, _newGuardians);


  121             emit Approved(_operationId, _approval, approved_);


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L121

  ```solidity
  File: contracts/L2/CrossChainOwned.sol


  53              emit TransactionExecuted(nextTxId++, bytes4(txdata));


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L53

  ```solidity
  File: contracts/L2/TaikoL2.sol


  157             emit Anchored(blockhash(parentId), gasExcess);


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L157

  ```solidity
  File: contracts/L2/TaikoL2EIP1559Configurable.sol


  39              emit ConfigAndExcessChanged(_newConfig, _newGasExcess);


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L39

  ```solidity
  File: contracts/bridge/Bridge.sol


  93                  emit MessageSuspended(msgHash, _suspend);


  111             emit AddressBanned(_addr, _ban);


  151             emit MessageSent(msgHash_, message_);


  208                 emit MessageRecalled(msgHash);


  210                 emit MessageReceived(msgHash, _message, true);


  301                 emit MessageExecuted(msgHash);


  303                 emit MessageReceived(msgHash, _message, false);


  336             emit MessageRetried(msgHash);


  519             emit MessageStatusChanged(_msgHash, _status);


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L519

  ```solidity
  File: contracts/common/AddressManager.sol


  50              emit AddressSet(_chainId, _name, _newAddress, oldAddress);


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L50

  ```solidity
  File: contracts/common/EssentialContract.sol


  71              emit Paused(msg.sender);


  80              emit Unpaused(msg.sender);


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L80

  ```solidity
  File: contracts/signal/SignalService.sol


  59              emit Authorized(_addr, _authorize);


  250             emit ChainDataSynced(_chainId, _blockId, _kind, _chainData, signal_);


  268             emit SignalSent(_app, _signal, slot_, _value);


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L268

  ```solidity
  File: contracts/team/TimelockTokenPool.sol


  143             emit Granted(_recipient, _grant);


  157             emit Voided(_recipient, amountVoided);


  222             emit Withdrawn(_recipient, _to, amountToWithdraw, costToWithdraw);


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L222

  ```solidity
  File: contracts/team/airdrop/ERC20Airdrop2.sol


  93              emit Withdrawn(user, amount);


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L93

  ```solidity
  File: contracts/team/airdrop/MerkleClaimable.sol


  74              emit Claimed(hash);


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L74

  ```solidity
  File: contracts/tokenvault/BridgedERC20Base.sol


  51              emit MigrationStatusChanged(_migratingAddress, _migratingInbound);


  63                  emit MigratedTo(migratingAddress, _account, _amount);


  80                  emit MigratedTo(migratingAddress, _account, _amount);


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L80

  ```solidity
  File: contracts/tokenvault/ERC1155Vault.sol


  80              emit TokenSent({
  81                  msgHash: msgHash,
  82                  from: message_.srcOwner,
  83                  to: _op.to,
  84                  destChainId: message_.destChainId,
  85                  ctoken: ctoken.addr,
  86                  token: _op.token,
  87                  tokenIds: _op.tokenIds,
  88                  amounts: _op.amounts
  89              });


  114             emit TokenReceived({
  115                 msgHash: ctx.msgHash,
  116                 from: from,
  117                 to: to,
  118                 srcChainId: ctx.srcChainId,
  119                 ctoken: ctoken.addr,
  120                 token: token,
  121                 tokenIds: tokenIds,
  122                 amounts: amounts
  123             });


  149             emit TokenReleased({
  150                 msgHash: msgHash,
  151                 from: message.srcOwner,
  152                 ctoken: ctoken.addr,
  153                 token: token,
  154                 tokenIds: tokenIds,
  155                 amounts: amounts
  156             });


  314             emit BridgedTokenDeployed({
  315                 chainId: _ctoken.chainId,
  316                 ctoken: _ctoken.addr,
  317                 btoken: btoken_,
  318                 ctokenSymbol: _ctoken.symbol,
  319                 ctokenName: _ctoken.name
  320             });


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L314

  ```solidity
  File: contracts/tokenvault/ERC20Vault.sol


  191             emit BridgedTokenChanged({
  192                 srcChainId: _ctoken.chainId,
  193                 ctoken: _ctoken.addr,
  194                 btokenOld: btokenOld_,
  195                 btokenNew: _btokenNew,
  196                 ctokenSymbol: _ctoken.symbol,
  197                 ctokenName: _ctoken.name,
  198                 ctokenDecimal: _ctoken.decimals
  199             });


  241             emit TokenSent({
  242                 msgHash: msgHash,
  243                 from: message_.srcOwner,
  244                 to: _op.to,
  245                 destChainId: _op.destChainId,
  246                 ctoken: ctoken.addr,
  247                 token: _op.token,
  248                 amount: balanceChange
  249             });


  273             emit TokenReceived({
  274                 msgHash: ctx.msgHash,
  275                 from: from,
  276                 to: to,
  277                 srcChainId: ctx.srcChainId,
  278                 ctoken: ctoken.addr,
  279                 token: token,
  280                 amount: amount
  281             });


  306             emit TokenReleased({
  307                 msgHash: _msgHash,
  308                 from: _message.srcOwner,
  309                 ctoken: ctoken.addr,
  310                 token: token,
  311                 amount: amount
  312             });


  425             emit BridgedTokenDeployed({
  426                 srcChainId: ctoken.chainId,
  427                 ctoken: ctoken.addr,
  428                 btoken: btoken,
  429                 ctokenSymbol: ctoken.symbol,
  430                 ctokenName: ctoken.name,
  431                 ctokenDecimal: ctoken.decimals
  432             });


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L425

  ```solidity
  File: contracts/tokenvault/ERC721Vault.sol


  64              emit TokenSent({
  65                  msgHash: msgHash,
  66                  from: message_.srcOwner,
  67                  to: _op.to,
  68                  destChainId: message_.destChainId,
  69                  ctoken: ctoken.addr,
  70                  token: _op.token,
  71                  tokenIds: _op.tokenIds,
  72                  amounts: _op.amounts
  73              });


  97              emit TokenReceived({
  98                  msgHash: ctx.msgHash,
  99                  from: from,
  100                 to: to,
  101                 srcChainId: ctx.srcChainId,
  102                 ctoken: ctoken.addr,
  103                 token: token,
  104                 tokenIds: tokenIds,
  105                 amounts: new uint256[](tokenIds.length)
  106             });


  131             emit TokenReleased({
  132                 msgHash: _msgHash,
  133                 from: _message.srcOwner,
  134                 ctoken: ctoken.addr,
  135                 token: token,
  136                 tokenIds: tokenIds,
  137                 amounts: new uint256[](tokenIds.length)
  138             });


  250             emit BridgedTokenDeployed({
  251                 chainId: _ctoken.chainId,
  252                 ctoken: _ctoken.addr,
  253                 btoken: btoken_,
  254                 ctokenSymbol: _ctoken.symbol,
  255                 ctokenName: _ctoken.name
  256             });


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L250

  ```solidity
  File: contracts/verifiers/SgxVerifier.sol


  109                 emit InstanceDeleted(idx, instances[idx].addr);


  220                 emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);


  230             emit InstanceAdded(id, newInstance, oldInstance, block.timestamp);


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L230

    </details>

## [G-22] Superfluous `event` fields

**Issue Description**\
`block.timestamp` and `block.number` are added to event information by default so adding them manually wastes gas.

**Attachments**

- **Code Snippets**

```solidity
File: contracts/verifiers/SgxVerifier.sol


230             emit InstanceAdded(id, newInstance, oldInstance, block.timestamp);


```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L230

## [G-23] Usage of `uints`/`ints` smaller than 32 bytes (256 bits) incurs overhead

**Issue Description**\
Usage of uints/ints smaller than 32 bytes (256 bits) in the contract can incur overhead and increase gas usage. This is because the EVM operates on 32 bytes at a time, and if the element is smaller than that, the EVM must use more operations to reduce the size of the element from 32 bytes to the desired size.

**Proposed Optimization**\
To optimize the gas usage, use a larger size (uint256 or int256) and then downcast to the desired size where needed. This can save gas as each operation involving a smaller size (e.g. uint8) can cost an extra 22-28 gas (depending on whether the other operand is also a variable of the same type) compared to operations involving uint256 or int256.

**Estimated Gas Savings**\
The estimated gas savings will depend on the number of operations involving smaller uints/ints in the contract. However, using a larger size and downcasting where needed can save an estimated `22-28` gas per operation.

**Attachments**

- **Code Snippets**

    <details>
    <summary>Click to show 16 findings</summary>

  ```solidity
  File: contracts/L1/TaikoL1.sol


  150             uint64 slot;


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L150

  ```solidity
  File: contracts/L1/libs/LibDepositing.sol


  83                  uint96 fee = uint96(_config.ethDepositMaxFee.min(block.basefee * _config.ethDepositGas));


  93                      uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount;


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L93

  ```solidity
  File: contracts/L1/libs/LibUtils.sol


  42              uint32 tid = getTransitionId(_state, blk, slot, _parentHash);


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/main/L1/libs/LibUtils.sol#L42

  ```solidity
  File: contracts/L1/libs/LibVerifying.sol


  107             uint32 tid = blk.verifiedTransitionId;


  117             uint64 numBlocksVerified;


  234             (uint64 lastSyncedBlock,) = signalService.getSyncedChainData(


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L234

  ```solidity
  File: contracts/L2/CrossChainOwned.sol


  42              (uint64 txId, bytes memory txdata) = abi.decode(_data, (uint64, bytes));


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L42

  ```solidity
  File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol


  106             uint32 totalQuoteSize = 48 // header


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L106

  ```solidity
  File: contracts/automata-attestation/utils/BytesUtils.sol


  332             uint8 decoded;


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L332

  ```solidity
  File: contracts/automata-attestation/utils/X509DateUtils.sol


  15              uint8 offset;


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L15

  ```solidity
  File: contracts/bridge/Bridge.sol


  89              uint64 _timestamp = _suspend ? type(uint64).max : uint64(block.timestamp);


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L89

  ```solidity
  File: contracts/team/TimelockTokenPool.sol


  197             uint128 _amountUnlocked = amountUnlocked / 1e18; // divide first


  226             uint128 amountOwned = _getAmountOwned(_grant);


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L226

  ```solidity
  File: contracts/thirdparty/optimism/trie/MerkleTrie.sol


  134                         uint8 branchKey = uint8(key[currentKeyIndex]);


  141                     uint8 prefix = uint8(path[0]);


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L141

    </details>

## [G-24] Emit Used In Loop

**Issue Description**\
Emitting an event inside a loop performs a LOG op N times, where N is the loop length. Consider refactoring the code to emit the event only once at the end of loop. Gas savings should be multiplied by the average loop length.

**Attachments**

- **Code Snippets**

```solidity
File: contracts/bridge/Bridge.sol


93                  emit MessageSuspended(msgHash, _suspend);


```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L93

```solidity
File: contracts/verifiers/SgxVerifier.sol


109                 emit InstanceDeleted(idx, instances[idx].addr);


220                 emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);


```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220

## [G-25] Private functions used once can be inlined

**Issue Description**\
Private functions that are used only once in the contract can consume more gas than necessary. This is because the EVM must perform a JUMP operation to call the function, which incurs a gas cost.

**Proposed Optimization**\
To optimize the gas usage, private functions that are used only once can be inlined. This means that the code of the function is copied directly into the calling function, eliminating the need for a JUMP operation.

**Estimated Gas Savings**\
The estimated gas savings will depend on the size and complexity of the private function being inlined. However, inlining a private function can save an estimated 20-40 gas per call.

**Attachments**

- **Code Snippets**

    <details>
    <summary>Click to show 41 findings</summary>

  ```solidity
  File: contracts/L1/hooks/AssignmentHook.sol


  164         function _getProverFee(

  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L164

  ```solidity
  File: contracts/L1/libs/LibProposing.sol


  299         function _isProposerPermitted(

  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L299

  ```solidity
  File: contracts/L1/libs/LibProving.sol


  269         function _createTransition(
  270             TaikoData.State storage _state,
  271             TaikoData.Block storage _blk,
  272             TaikoData.Transition memory _tran,
  273             uint64 slot
  274         )
  275             private
  347         }


  350         function _overrideWithHigherProof(
  351             TaikoData.TransitionState storage _ts,
  352             TaikoData.Transition memory _tran,
  353             TaikoData.TierProof memory _proof,
  354             ITierProvider.Tier memory _tier,
  355             IERC20 _tko,
  356             bool _sameTransition
  357         )
  358             private
  359         {


  401         function _checkProverPermission(
  402             TaikoData.State storage _state,
  403             TaikoData.Block storage _blk,
  404             TaikoData.TransitionState storage _ts,
  405             uint32 _tid,
  406             ITierProvider.Tier memory _tier
  407         )
  408             private
  409             view
  410         {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L401

  ```solidity
  File: contracts/L1/libs/LibVerifying.sol


  224         function _syncChainData(
  225             TaikoData.Config memory _config,
  226             IAddressResolver _resolver,
  227             uint64 _lastVerifiedBlockId,
  228             bytes32 _stateRoot
  229         )
  230             private
  231         {


  245         function _isConfigValid(TaikoData.Config memory _config) private view returns (bool) {

  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L245

  ```solidity
  File: contracts/L2/Lib1559Math.sol


  33          function _ethQty(
  34              uint256 _gasExcess,
  35              uint256 _adjustmentFactor
  36          )
  37              private
  38              pure
  39              returns (uint256)
  40          {

  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L33

  ```solidity
  File: contracts/automata-attestation/AutomataDcapV3Attestation.sol


  162         function _verify(bytes calldata quote) private view returns (bool, bytes memory) {


  175         function _verifyQEReportWithIdentity(V3Struct.EnclaveReport memory quoteEnclaveReport)
  176             private
  177             view
  178             returns (bool, EnclaveIdStruct.EnclaveIdStatus status)
  179         {

  206         function _checkTcbLevels(
  207             IPEMCertChainLib.PCKCertificateField memory pck,
  208             TCBInfoStruct.TCBInfo memory tcb
  209         )
  210             private
  211             pure
  212             returns (bool, TCBInfoStruct.TCBStatus status)
  213         {

  229         function _isCpuSvnHigherOrGreater(
  230             uint256[] memory pckCpuSvns,
  231             uint8[] memory tcbCpuSvns
  232         )
  233             private
  234             pure
  235             returns (bool)
  236         {

  248         function _verifyCertChain(IPEMCertChainLib.ECSha256Certificate[] memory certs)
  249             private
  250             view
  251             returns (bool)


  303         function _enclaveReportSigVerification(
  304             bytes memory pckCertPubKey,
  305             bytes memory signedQuoteData,
  306             V3Struct.ECDSAQuoteV3AuthData memory authDataV3,
  307             V3Struct.EnclaveReport memory qeEnclaveReport
  308         )
  309             private
  310             view
  311             returns (bool)
  312         {

  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L303

  ```solidity
  File: contracts/automata-attestation/lib/PEMCertChainLib.sol


  216         function _removeHeadersAndFooters(string memory pemData)
  217             private
  218             pure
  219             returns (bool success, bytes memory extracted, uint256 endIndex)
  220         {


  269         function _findPckTcbInfo(
  270             bytes memory der,
  271             uint256 tbsPtr,
  272             uint256 tbsParentPtr
  273         )
  274             private
  275             pure
  339         }


  341         function _findTcb(
  342             bytes memory der,
  343             uint256 oidPtr
  344         )
  345             private
  346             pure
  347             returns (bool success, uint256 pcesvn, uint256[] memory cpusvns)
  348         {

  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L341

  ```solidity
  File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol


  165         function parseAndVerifyHeader(bytes memory rawHeader)
  166             private
  167             pure
  168             returns (bool success, V3Struct.Header memory header)
  169         {


  203         function parseAuthDataAndVerifyCertType(
  204             bytes memory rawAuthData,
  205             address pemCertLibAddr
  206         )
  207             private
  208             pure
  209             returns (bool success, V3Struct.ECDSAQuoteV3AuthData memory authDataV3)
  210         {

  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L203

  ```solidity
  File: contracts/automata-attestation/utils/BytesUtils.sol


  272         function memcpy(uint256 dest, uint256 src, uint256 len) private pure {

  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L272

  ```solidity
  File: contracts/bridge/Bridge.sol


  555         function _loadContext() private view returns (Context memory) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L555

  ```solidity
  File: contracts/signal/SignalService.sol


  271         function _cacheChainData(
  272             HopProof memory _hop,
  273             uint64 _chainId,
  274             uint64 _blockId,
  275             bytes32 _signalRoot,
  276             bool _isFullProof,
  277             bool _isLastHop
  278         )
  279             private
  280         {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L271

  ```solidity
  File: contracts/team/TimelockTokenPool.sol


  225         function _voidGrant(Grant storage _grant) private returns (uint128 amountVoided) {


  239         function _getAmountUnlocked(Grant memory _grant) private view returns (uint128) {


  267         function _validateGrant(Grant memory _grant) private pure {

  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L267

  ```solidity
  File: contracts/thirdparty/optimism/rlp/RLPWriter.sol


  32          function _writeLength(uint256 _len, uint256 _offset) private pure returns (bytes memory out_) {


  55          function _toBinary(uint256 _x) private pure returns (bytes memory out_) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L55

  ```solidity
  File: contracts/thirdparty/optimism/trie/MerkleTrie.sol


  205         function _parseProof(bytes[] memory _proof) private pure returns (TrieNode[] memory proof_) {


  227         function _getNodePath(TrieNode memory _node) private pure returns (bytes memory nibbles_) {


  235         function _getSharedNibbleLength(
  236             bytes memory _a,
  237             bytes memory _b
  238         )
  239             private
  240             pure
  241             returns (uint256 shared_)
  242         {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L235

  ```solidity
  File: contracts/tokenvault/ERC1155Vault.sol


  240         function _handleMessage(
  241             address _user,
  242             BridgeTransferOp memory _op
  243         )
  244             private
  245             returns (bytes memory msgData_, CanonicalNFT memory ctoken_)
  246         {


  288         function _getOrDeployBridgedToken(CanonicalNFT memory _ctoken)
  289             private
  290             returns (address btoken_)
  291         {


  303         function _deployBridgedToken(CanonicalNFT memory _ctoken) private returns (address btoken_) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L303

  ```solidity
  File: contracts/tokenvault/ERC20Vault.sol


  348         function _handleMessage(
  349             address _user,
  350             address _token,
  351             address _to,
  352             uint256 _amount
  353         )
  354             private
  355             returns (bytes memory msgData_, CanonicalERC20 memory ctoken_, uint256 balanceChange_)
  356         {


  391         function _getOrDeployBridgedToken(CanonicalERC20 memory ctoken)
  392             private
  393             returns (address btoken)
  394         {


  407         function _deployBridgedToken(CanonicalERC20 memory ctoken) private returns (address btoken) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L407

  ```solidity
  File: contracts/tokenvault/ERC721Vault.sol


  187         function _handleMessage(
  188             address _user,
  189             BridgeTransferOp memory _op
  190         )
  191             private
  192             returns (bytes memory msgData_, CanonicalNFT memory ctoken_)
  193         {


  224         function _getOrDeployBridgedToken(CanonicalNFT memory _ctoken)
  225             private
  226             returns (address btoken_)
  227         {


  240         function _deployBridgedToken(CanonicalNFT memory _ctoken) private returns (address btoken_) {

  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L240

  ```solidity
  File: contracts/verifiers/SgxVerifier.sol


  226         function _replaceInstance(uint256 id, address oldInstance, address newInstance) private {


  233         function _isInstanceValid(uint256 id, address instance) private view returns (bool) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L233

    </details>

## [G-26] Use `SUB` or `XOR` instead of `ISZERO(EQ())` to check for inequality

**Issue Description**\
When using inline assembly to compare the equality of two values (e.g if owner is the same as caller()), It is sometimes more efficient to do

**Proposed Optimization**\

```solidity
if sub(caller, sload(owner.slot)) {
    revert(0x00, 0x00)
}
over doing this

if eq(caller, sload(owner.slot)) {
    revert(0x00, 0x00)
}
```

xor can accomplish the same thing, but be aware that xor will consider a value with all the bits flipped to be equal also, so make sure that this cannot become an attack vector.

**Attachments**

- **Code Snippets**

```solidity
File: contracts/thirdparty/optimism/Bytes.sol

33            switch iszero(_length)

53                let mc := add(add(tempBytes, lengthmod), mul(0x20, iszero(lengthmod)))

59                    let cc := add(add(add(_bytes, lengthmod), mul(0x20, iszero(lengthmod))), _start)
```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L33

## [G-27] Use assembly to calculate hashes to save gas

**Issue Description**\
Solidity writes to memory by expanding it, which can be inefficient for operations on data that are 96 bytes in size or less. This is because Solidity reserves the first 64 bytes of memory as scratch space, the next 32 bytes of memory for the free memory pointer, and the next 32 bytes of memory as the zero slot for uninitialized dynamic memory data.

**Proposed Optimization**\
To optimize memory operations on data that are 96 bytes in size or less, we can utilize inline assembly to perform operations on the scratch space and the free memory pointer space. This can help avoid unnecessary memory expansion and save gas.

**Estimated Gas Savings**\
Using assembly to calculate hashes can save 80 gas per instance

**Attachments**

- **Code Snippets**

    <details>
    <summary>Click to show 28 findings</summary>

  ```solidity
  File: contracts/L1/hooks/AssignmentHook.sol


  146             return keccak256(


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L146

  ```solidity
  File: contracts/L1/libs/LibProposing.sol


  126                     depositsHash: keccak256(abi.encode(deposits_)),


  189                 meta_.blobHash = keccak256(_txList);


  204             meta_.difficulty = keccak256(abi.encodePacked(block.prevrandao, b.numBlocks, block.number));


  213                 metaHash: keccak256(abi.encode(meta_)),


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L213

  ```solidity
  File: contracts/L1/libs/LibProving.sol


  20          bytes32 public constant RETURN_LIVENESS_BOND = keccak256("RETURN_LIVENESS_BOND");


  121             if (blk.blockId != _meta.id || blk.metaHash != keccak256(abi.encode(_meta))) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L121

  ```solidity
  File: contracts/L1/provers/GuardianProver.sol


  46              bytes32 hash = keccak256(abi.encode(_meta, _tran));


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L46

  ```solidity
  File: contracts/automata-attestation/AutomataDcapV3Attestation.sol


  292                 bytes32 issuerPubKeyHash = keccak256(issuer.pubKey);


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L292

  ```solidity
  File: contracts/automata-attestation/utils/BytesUtils.sol


  372             return keccak256(a) == keccak256(b);


  372             return keccak256(a) == keccak256(b);


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L372

  ```solidity
  File: contracts/bridge/Bridge.sol


  450             return keccak256(abi.encode("TAIKO_MESSAGE", _message));


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L450

  ```solidity
  File: contracts/signal/LibSignals.sol


  8           bytes32 public constant STATE_ROOT = keccak256("STATE_ROOT");


  11          bytes32 public constant SIGNAL_ROOT = keccak256("SIGNAL_ROOT");


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/LibSignals.sol#L11

  ```solidity
  File: contracts/signal/SignalService.sol


  186             return keccak256(abi.encode(_chainId, _kind, _blockId));


  203             return keccak256(abi.encodePacked("SIGNAL", _chainId, _app, _signal));


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L203

  ```solidity
  File: contracts/team/TimelockTokenPool.sol


  170             bytes32 hash = keccak256(abi.encodePacked("Withdraw unlocked Taiko token to: ", _to));


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L170

  ```solidity
  File: contracts/team/airdrop/MerkleClaimable.sol


  68              bytes32 hash = keccak256(abi.encode("CLAIM_TAIKO_AIRDROP", data));


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L68

  ```solidity
  File: contracts/thirdparty/optimism/Bytes.sol


  150             return keccak256(_bytes) == keccak256(_other);


  150             return keccak256(_bytes) == keccak256(_other);


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L150

  ```solidity
  File: contracts/thirdparty/optimism/trie/MerkleTrie.sol


  94                          Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),


  100                         Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L100

  ```solidity
  File: contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol


  55              hash_ = abi.encodePacked(keccak256(_key));


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L55

  ```solidity
  File: contracts/tokenvault/ERC20Vault.sol


  176                         || keccak256(bytes(ctoken.symbol)) != keccak256(bytes(_ctoken.symbol))


  176                         || keccak256(bytes(ctoken.symbol)) != keccak256(bytes(_ctoken.symbol))


  177                         || keccak256(bytes(ctoken.name)) != keccak256(bytes(_ctoken.name))


  177                         || keccak256(bytes(ctoken.name)) != keccak256(bytes(_ctoken.name))


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L177

  ```solidity
  File: contracts/verifiers/SgxVerifier.sol


  182             return keccak256(


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L182

    </details>

## [G-28] Do not calculate constants

**Issue Description**\
Due to how constant variables are implemented (replacements at compile-time), an expression assigned to a constant variable is recomputed each time that the variable is used, which wastes some gas.

**Attachments**

- **Code Snippets**

```solidity
File: contracts/L1/libs/LibProposing.sol


21          uint256 public constant MAX_BYTES_PER_BLOB = 4096 * 32;


```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L21

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol


24          uint256 internal constant BRANCH_NODE_LENGTH = TREE_RADIX + 1;


```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L24

## [G-29] Assigning state variables directly with named struct constructors wastes gas

**Issue Description**\
Using named arguments for struct means that the compiler needs to organize the fields in memory before doing the assignment, which wastes gas. Set each field directly in storage (use dot-notation), or use the unnamed version of the constructor.

**Proposed Optimization**\
To optimize gas usage, set each field directly in storage using dot-notation, or use the unnamed version of the constructor. This will avoid the need for the compiler to organize the fields in memory before doing the assignment, resulting in gas savings.

**Attachments**

- **Code Snippets**

    <details>
    <summary>Click to show 15 findings</summary>

  ```solidity
  File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

  54        v3ParsedQuote = V3Struct.ParsedV3QuoteStruct({

  190        header = V3Struct.Header({
  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L54

  ```solidity
  File: contracts/bridge/Bridge.sol

  243                proofReceipt[msgHash] = ProofReceipt({

  342        return ISignalService(resolve("signal_service", false)).isSignalSent({

  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L243

  ```solidity
  File: contracts/L1/libs/LibProposing.sol

  121            meta_ = TaikoData.BlockMetadata({

  212        TaikoData.Block memory blk = TaikoData.Block({

  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L121

  ```solidity
  File: contracts/L1/tiers/DevnetTierProvider.sol

  22            return ITierProvider.Tier({

  33            return ITierProvider.Tier({
  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L22

  ```solidity
  File: contracts/L1/tiers/MainnetTierProvider.sol

  22            return ITierProvider.Tier({

  33            return ITierProvider.Tier({

  44            return ITierProvider.Tier({

  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L22

  ```solidity
  File: contracts/thirdparty/optimism/rlp/RLPReader.sol


  47              out_ = RLPItem({ length: _in.length, ptr: ptr });


  84                  out_[itemCount] = RLPItem({


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L84

  ```solidity
  File: contracts/thirdparty/optimism/trie/MerkleTrie.sol


  209                 proof_[i] = TrieNode({ encoded: _proof[i], decoded: RLPReader.readList(_proof[i]) });


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L209

  ```solidity
  File: contracts/tokenvault/ERC20Vault.sol


  365                 ctoken_ = CanonicalERC20({


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L365

## [G-30] The use of a logical AND in place of double if is slightly less gas efficient in instances where there isn't a corresponding else statement for the given if statement

**Issue Description**\
Using a double if statement instead of logical AND (&&) can provide similar short-circuiting behavior whereas double if is slightly more efficient.

**Attachments**

- **Code Snippets**

    <details>
    <summary>Click to show 23 findings</summary>

  ```solidity
  File: contracts/L1/hooks/AssignmentHook.sol


  82                  block.timestamp > assignment.expiry
  83                      || assignment.metaHash != 0 && _blk.metaHash != assignment.metaHash


  120             if (input.tip != 0 && block.coinbase != address(0)) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L120

  ```solidity
  File: contracts/L1/libs/LibProposing.sol


  108             if (params.parentMetaHash != 0 && parentMetaHash != params.parentMetaHash) {


  164                     if (_config.blobReuseEnabled && params.cacheBlobForReuse) {


  310                 if (proposerOne != address(0) && msg.sender != proposerOne) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L310

  ```solidity
  File: contracts/L1/libs/LibProving.sol


  419             if (_tid == 1 && _ts.tier == 0 && inProvingWindow) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L419

  ```solidity
  File: contracts/L2/TaikoL2.sol


  117                 _l1BlockHash == 0 || _l1StateRoot == 0 || _l1BlockId == 0
  118                     || (block.number != 1 && _parentGasUsed == 0)


  141             if (!skipFeeCheck() && block.basefee != basefee) {


  275                 if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L275

  ```solidity
  File: contracts/automata-attestation/AutomataDcapV3Attestation.sol


  220                 if (pceSvnIsHigherOrGreater && cpuSvnsAreHigherOrGreater) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L220

  ```solidity
  File: contracts/automata-attestation/lib/PEMCertChainLib.sol


  134                 if (
  135                     (notBeforeTag != 0x17 && notBeforeTag == 0x18)


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L134

  ```solidity
  File: contracts/bridge/Bridge.sol


  250             if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) {


  260                 if (_message.gasLimit == 0 && msg.sender != _message.destOwner) {


  439             } else if (block.chainid >= 32_300 && block.chainid <= 32_400) {


  490             if (
  491                 _message.data.length >= 4 // msg can be empty
  492                     && bytes4(_message.data) != IMessageInvocable.onMessageInvocation.selector
  493                     && _message.to.isContract()


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L490

  ```solidity
  File: contracts/common/AddressResolver.sol


  85              if (!_allowZeroAddress && addr_ == address(0)) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L85

  ```solidity
  File: contracts/common/EssentialContract.sol


  42              if (msg.sender != owner() && msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L42

  ```solidity
  File: contracts/signal/SignalService.sol


  285             if (cacheStateRoot && _isFullProof && !_isLastHop) {


  293             if (cacheSignalRoot && (_isFullProof || !_isLastHop)) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L293

  ```solidity
  File: contracts/team/TimelockTokenPool.sol


  277                 if (_cliff > 0 && _cliff <= _start) revert INVALID_GRANT();


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L277

  ```solidity
  File: contracts/thirdparty/optimism/rlp/RLPWriter.sol


  14              if (_in.length == 1 && uint8(_in[0]) < 128) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L14

  ```solidity
  File: contracts/tokenvault/BridgedERC20.sol


  38              if (msg.sender != owner() && msg.sender != snapshooter) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L38

  ```solidity
  File: contracts/tokenvault/BridgedERC20Base.sol


  45              if (_migratingAddress == migratingAddress && _migratingInbound == migratingInbound) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L45

    </details>

## [G-31] Avoid fetching a `low-level` call's return data by using assembly

**Issue Description**\
In Solidity, when making a low-level call using the call() function, the second return value (i.e., the return data) gets copied to memory even if it is not assigned to a variable. This can result in unnecessary gas usage.

**Proposed Optimization**\
To optimize gas usage, use assembly to prevent the return data from being copied to memory. This can save `159` gas.

**Estimated Gas Savings**\
The estimated gas savings for this optimization is 159 gas.

**Attachments**

- **Code Snippets**

```solidity
File: contracts/L2/CrossChainOwned.sol


50              (bool success,) = address(this).call(txdata);


```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L50

## [G-32] Duplicated `require()`/`revert()` checks should be refactored to a modifier or function

**Saves deployment costs**

**Attachments**

- **Code Snippets**

```solidity
File: contracts/automata-attestation/utils/Asn1Decode.sol


142             require(der[ptr.ixs()] == 0x02, "Not type INTEGER");


143             require(der[ptr.ixf()] & 0x80 == 0, "Not positive");


```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L143

```solidity
File: contracts/automata-attestation/utils/SigVerifyLib.sol


50                  revert("Unsupported algorithm");


```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L50

## [G-33] `State variable` read in a loop

**Issue Description**\
The state variable should be cached in and read from a local variable, or accumulated in a local variable then written to storage once outside of the loop, rather than `reading/updating` it on every iteration of the loop, which will replace each `Gwarmaccess` (100 gas) with a much cheaper stack read.

**Proposed Optimization**\
To optimize gas usage, cache the state variable in a local variable and read from it within the loop, or accumulate the values in a local variable and write to storage once outside of the loop. This will replace each Gwarmaccess operation with a much cheaper stack read.

**Estimated Gas Savings**\
The estimated gas savings for this optimization will depend on the number of iterations in the loop. However, each `Gwarmaccess` operation that is replaced with a stack read can result in a gas savings of `95` gas.

**Attachments**

- **Code Snippets**

    <details>
    <summary>Click to show 15 findings</summary>

  ```solidity
  File: contracts/L1/provers/Guardians.sol


  74              for (uint256 i; i < guardians.length; ++i) {


  84                  if (guardianIds[guardian] != 0) revert INVALID_GUARDIAN_SET();


  135                     if (count == minGuardians) return true;


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L135

  ```solidity
  File: contracts/automata-attestation/AutomataDcapV3Attestation.sol


  81                  if (_serialNumIsRevoked[index][serialNumBatch[i]]) {


  96                  if (!_serialNumIsRevoked[index][serialNumBatch[i]]) {


  240             for (uint256 i; i < CPUSVN_LENGTH; ++i) {


  268                         certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.ROOT)][certs[i]


  424                     (certDecodedSuccessfully, parsedQuoteCerts[i]) = pemCertLib.decodeCert(


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L424

  ```solidity
  File: contracts/automata-attestation/lib/PEMCertChainLib.sol


  354             for (uint256 i; i < SGX_TCB_CPUSVN_SIZE + 1; ++i) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L354

  ```solidity
  File: contracts/automata-attestation/utils/BytesUtils.sol


  336                 decoded = uint8(BASE32_HEX_TABLE[uint256(uint8(char)) - 0x30]);


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L336

  ```solidity
  File: contracts/bridge/Bridge.sol


  92                  proofReceipt[msgHash].receivedAt = _timestamp;


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L92

  ```solidity
  File: contracts/team/airdrop/ERC721Airdrop.sol


  60                  IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L60

  ```solidity
  File: contracts/thirdparty/optimism/trie/MerkleTrie.sol


  111                 if (currentNode.decoded.length == BRANCH_NODE_LENGTH) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L111

  ```solidity
  File: contracts/verifiers/SgxVerifier.sol


  107                 if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();


  211                 if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L211

    </details>

## [G-34] Storage `re-read` via storage pointer

**Issue Description**\
The instances below point to the second+ access of a state variable, via a storage pointer, within a function. Caching the value replaces each `Gwarmaccess` (100 gas) with a much cheaper stack read.

**Proposed Optimization**\
To optimize gas usage, cache the value of the state variable in a local variable and read from it within the function. This will replace each Gwarmaccess operation with a much cheaper stack read.

**Estimated Gas Savings**\
The estimated gas savings for this optimization will depend on the number of times the state variable is read within the function. However, each Gwarmaccess operation that is replaced with a stack read can result in a gas savings of `95` gas.

**Attachments**

- **Code Snippets**

    <details>
    <summary>Click to show 4 findings</summary>

  ```solidity
  File: contracts/L1/libs/LibProving.sol


  192                 bool returnLivenessBond = blk.livenessBond > 0 && _proof.data.length == 32


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L192

  ```solidity
  File: contracts/L1/libs/LibVerifying.sol


  107             uint32 tid = blk.verifiedTransitionId;


  184                     if (ts.prover != blk.assignedProver) {


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L184

  ```solidity
  File: contracts/team/TimelockTokenPool.sol


  198             costToWithdraw = _amountUnlocked * r.grant.costPerToken - r.costPaid;


  ```

  https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L198

    </details>

## [G-35] Inverting the condition of an `if-else-statement`

**Issue Description**\
Flipping the true and false blocks instead saves 3 gas.

**Estimated Gas Savings**\
`saves 3 gas`

**Attachments**

- **Code Snippets**

```solidity
File: contracts/bridge/Bridge.sol


209             } else if (!isMessageProven) {
210                 emit MessageReceived(msgHash, _message, true);
211             } else {
212                 revert B_INVOCATION_TOO_EARLY();
213             }


302             } else if (!isMessageProven) {
303                 emit MessageReceived(msgHash, _message, false);
304             } else {
305                 revert B_INVOCATION_TOO_EARLY();
306             }


```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L302

## [G-36] Timestamps and block numbers in storage do not need to be `uint256`

**Issue Description**\
A timestamp of size `uint48` will work for millions of years into the future. A block number increments once every 12 seconds. This should give you a sense of the size of numbers that are sensible.

**Attachments**

- **Code Snippets**

```solidity
File: contracts/bridge/Bridge.sol


146        message_.srcChainId = uint64(block.chainid);

183            receivedAt = uint64(block.timestamp);

240            receivedAt = uint64(block.timestamp);

```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L146

```solidity
File: contracts/L1/TaikoL1.sol

126        state.slotB.lastUnpausedAt = uint64(block.timestamp);
```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L126

```solidity
File: contracts/L1/libs/LibProposing.sol

                timestamp: uint64(block.timestamp),
                l1Height: uint64(block.number - 1),

            proposedIn: uint64(block.number),
```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L220

```solidity
File: contracts/L1/libs/LibProving.sol


264        ts.timestamp = uint64(block.timestamp);
```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L264

```solidity
File: contracts/L1/libs/LibVerifying.sol


57        _state.slotA.genesisHeight = uint64(block.number);

58        _state.slotA.genesisTimestamp = uint64(block.timestamp);

64        blk.proposedAt = uint64(block.timestamp);

71        ts.timestamp = uint64(block.timestamp);

```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L57

## [G-37] Use fallback or receive instead of `deposit()` when transferring Ether

**Issue Description**\
Similar to above, you can “just transfer” ether to a contract and have it respond to the transfer instead of using a payable function. This of course, depends on the rest of the contract’s architecture.

**Example Deposit in AAVE**

```solidity
contract AddLiquidity{

    receive() external payable {
      IWETH(weth).deposit{msg.value}();
      AAVE.deposit(weth, msg.value, msg.sender, REFERRAL_CODE)
    }
}
```

The fallback function is capable of receiving bytes data which can be parsed with abi.decode. This servers as an alternative to supplying arguments to a deposit function.

**Attachments**

- **Code Snippets**

```solidity
File: contracts/L1/TaikoL1.sol

119    function depositEtherToL2(address _recipient) external payable nonReentrant whenNotPaused {

```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L119

```solidity
File: contracts/L1/libs/LibDepositing.sol

29    function depositEtherToL2(

```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L29

## [G-38] Consider using alternatives to `OpenZeppelin`

**Issue Description**\
OpenZeppelin is a great and popular smart contract library, but there are other alternatives that are worth considering. These alternatives offer better gas efficiency and have been tested and recommended by developers.

Two examples of such alternatives are [Solmate](https://github.com/transmissions11/solmate) and [Solady](https://github.com/Vectorized/solady).

Solmate is a library that provides a number of `gas-efficient` implementations of common smart contract patterns. Solady is another `gas-efficient` library that places a strong emphasis on using assembly.

**Attachments**

- **Code Snippets**

```solidity

import "@openzeppelin/contracts/";

```

## [G-39] A `MODIFIER` used only once and not being inherited should be inlined to save gas

**Issue Description**\
When a modifier is used only once in a contract and is not being inherited by other contracts, it can be inlined to save gas.

**Proposed Optimization**\
To optimize gas usage, inline the modifier code directly into the function it modifies, rather than using a separate modifier function.

**Attachments**

- **Code Snippets**

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol

39    modifier ongoingWithdrawals() {
41        if (claimEnd > block.timestamp || claimEnd + withdrawalWindow < block.timestamp) {
42            revert WITHDRAWALS_NOT_ONGOING();
43        }
44        _;
45    }
```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L39

only Used in this function

```solidity
    function withdraw(address user) external ongoingWithdrawals {
```

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol

33    modifier ongoingClaim() {
34        if (
35            merkleRoot == 0x0 || claimStart == 0 || claimEnd == 0 || claimStart > block.timestamp
36                || claimEnd < block.timestamp
37        ) revert CLAIM_NOT_ONGOING();
38        _;
39    }
```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L33

```solidity
File: contracts/tokenvault/BridgedERC20.sol

37    modifier onlyOwnerOrSnapshooter() {
38        if (msg.sender != owner() && msg.sender != snapshooter) {
39            revert BTOKEN_UNAUTHORIZED();
40        }
41        _;
42    }
```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L37

## [G-40] Expressions for constant values such as a call to  KECCAK256(), should use IMMUTABLE rather than CONSTANT

**Issue Description**\
Immutable variables are more gas-efficient than constant variables for expressions that are computed at compile-time, such as a call to `KECCAK256()`.

**Proposed Optimization**\
To optimize gas usage, use immutable instead of constant for expressions that are computed at compile-time.

**Attachments**

- **Code Snippets**

```solidity
File: contracts/L1/libs/LibProving.sol

20    bytes32 public constant RETURN_LIVENESS_BOND = keccak256("RETURN_LIVENESS_BOND");
```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L20

```solidity
File: contracts/signal/LibSignals.sol

8    bytes32 public constant STATE_ROOT = keccak256("STATE_ROOT");

11    bytes32 public constant SIGNAL_ROOT = keccak256("SIGNAL_ROOT");
```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/LibSignals.sol#L8

## [G-41] Consider using OZ EnumerateSet in place of nested mappings

**Issue Description**\
Nested mappings and multi-dimensional arrays in Solidity operate through a process of double hashing, which can be gas expensive due to the double-hashing operation and subsequent storage operation (sstore).

**Proposed Optimization**\
Consider using `OpenZeppelin's` EnumerableSet in place of nested mappings or multi-dimensional arrays. EnumerableSet creates a data structure that combines the benefits of set operations with the ability to enumerate stored elements, providing a more gas-efficient and collision-resistant alternative in certain scenarios.

**Attachments**

- **Code Snippets**

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol

47    mapping(uint256 idx => mapping(bytes serialNum => bool revoked)) private _serialNumIsRevoked;

```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L47

```solidity
File: contracts/common/AddressManager.sol

12    mapping(uint256 chainId => mapping(bytes32 name => address addr)) private __addresses;

```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L12

```solidity
File: contracts/L1/TaikoData.sol

183        mapping(uint64 blockId => mapping(bytes32 parentHash => uint32 transitionId)) transitionIds;

```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L183

```solidity
File: contracts/signal/SignalService.sol

17    mapping(uint64 chainId => mapping(bytes32 kind => uint64 blockId)) public topBlockId;
```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L17

```solidity
File: contracts/tokenvault/ERC20Vault.sol

49    mapping(uint256 chainId => mapping(address ctoken => address btoken)) public canonicalToBridged;

```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L49

## [G-42] Shorten the array rather than copying to a new one

**Issue Description**\
ASSEMBLY can be used to shorten the array by changing the length slot, so that the entries don't have to be copied to a new, shorter array

**Attachments**

- **Code Snippets**

```solidity
File: contracts/L1/gov/TaikoTimelockController.sol

17        address[] memory nil = new address[](0);

```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L17

```solidity
File: contracts/L1/tiers/DevnetTierProvider.sol

48        tiers_ = new uint16[](2);

```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L48

```solidity
File: contracts/L1/tiers/MainnetTierProvider.sol

59        tiers_ = new uint16[](3);

```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L59

```solidity
File:

59        tiers_ = new uint16[](3);
```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L59
