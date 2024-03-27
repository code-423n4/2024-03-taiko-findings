## Summary

### Gas Optimization

no | Issue |Instances||
|-|:-|:-:|:-:|
|
| [G-01] |  Using `calldata` instead of `memory` for read-only arguments in external functions saves gas | 9 | - |
| [G-02] | Public function not called by the contract should be declared external instead  | 3 | - |
| [G-03] | Use assembly to check for address(0) | 6 | - |
| [G-14] | Bytes constants are more efficient than String constants | 5 | - |
| [G-05] | Don't initialize variables with default value | 4 | - |
| [G-06] | State varaibles only set in the Constructor should be declared `Immutable` | 1 | - |
| [G-07] | Internal functions only called once can be inlined to save gas | 5 | - |
| [G-08] | `keccak256()` should only need to be called on a specific string literal once | 1 | - |
| [G-09] | Optimize Names to save Gas | 4 | - |
| [G-10] | `Require() `/ `Revert()` string longer than 32 bytes cost extra gas  | 10 | - |
| [G-11] | Setting the constructor to `payable` | 1 | - |
| [G-12] |  Can make the variable outside the loop to save gas | 6 | - | |
| [G-13] | Use constants instead of `type(uintx).max` | 5 | - |
| [G-14] | Use nested if and, avoid multiple check combinations | 4 | - |
| [G-15] | Caching global variables is more expensive than using the actual variable (use msg.sender instead of caching it) | 1 | - |
| [G-16] | Use `selfbalance()` instead of `address(this).balance` | 6 | - |
| [G-17] | `abi.encode()` is less efficient than  `abi.encodepacked()` | 4 | - |

## Gas Optimizations  
## [G-01] Using `calldata` instead of `memory` for read-only arguments in external functions saves gas 

```solidity
file: /contracts/automata-attestation/interfaces/ISigVerifyLib.sol

38    function verifyAttStmtSignature(
        bytes memory tbs,
        bytes memory signature,
        PublicKey memory publicKey,
        Algorithm alg
    )
        external
        view
       returns (bool);


67    function verifyRS1Signature(
        bytes memory tbs,
        bytes memory signature,
        bytes memory publicKey
    )

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L38-L46


```solidity
file: /contracts/L1/hooks/AssignmentHook.sol

62    function onBlockProposed(
        TaikoData.Block memory _blk,
        TaikoData.BlockMetadata memory _meta,
        bytes memory _data
    )

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L62-L66


## [G-02] Public function not called by the contract should be declared external instead 

Contracts are allowed to override their parents' functions and change the visibility from external to public and can save gas by doing so.

```solidity
file: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

103    function configureTcbInfoJson(
        string calldata fmspc,
        TCBInfoStruct.TCBInfo calldata tcbInfoInput
    )
        public
        onlyOwner
    {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L103


```solidity
file: /contracts/automata-attestation/utils/SigVerifyLib.sol

24    function verifyAttStmtSignature(
        bytes memory tbs,
        bytes memory signature,
        PublicKey memory publicKey,
        Algorithm alg
    )
        public
        view
        returns (bool)
    {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L24


```solidity
file: /contracts/bridge/Bridge.sol

352    function proveMessageFailed(
        Message calldata _message,
        bytes calldata _proof
    )
        public
        view
        returns (bool)
    {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L352


## [G-03] Use assembly to check for address(0)

```solidity
file: /contracts/common/AddressResolver.sol

81        if (addressManager == address(0)) revert RESOLVER_INVALID_MANAGER();

85        if (!_allowZeroAddress && addr_ == address(0)) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L81C1-L81C77


```solidity
file: /contracts/common/EssentialContract.so

105        if (_addressManager == address(0)) revert ZERO_ADDR_MANAGER();

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L105C1-L105C71


```solidity
file: /contracts/libs/LibAddress.sol

24        if (_to == address(0)) revert ETH_TRANSFER_FAILED();

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L24C1-L24C61


```solidity
file: /contracts/L1/hooks/AssignmentHook.sol

120        if (input.tip != 0 && block.coinbase != address(0)) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L120C1-L120C62


```solidity
file: /contracts/L1/libs/LibProving.sol

163            if (verifier != address(0)) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L163C1-L163C42

## [G-04] Bytes constants are more efficient than String constants

If data can fit into 32 bytes, then you should use bytes32 datatype rather than bytes or strings as it is cheaper in solidity.

```solidity
file: /contracts/automata-attestation/lib/PEMCertChainLib.sol

17    string internal constant HEADER = "-----BEGIN CERTIFICATE-----";
      string internal constant FOOTER = "-----END CERTIFICATE-----";


    string internal constant PCK_COMMON_NAME = "Intel SGX PCK Certificate";
    string internal constant PLATFORM_ISSUER_NAME = "Intel SGX PCK Platform CA";
    string internal constant PROCESSOR_ISSUER_NAME = "Intel SGX PCK Processor CA";

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L17-L24


## [G-05] Don't initialize variables with default value

Uninitialized variables are assigned with the types default value. Explicitly initializing a variable with it's default value costs unnecesary gas.

```solidity
file: /contracts/automata-attestation/lib/PEMCertChainLib.sol

51        uint256 index = 0;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L51


```solidity
file: /contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

18    bytes4 internal constant SUPPORTED_TEE_TYPE = 0;


```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L18


```solidity
file: /contracts/automata-attestation/utils/BytesUtils.sol

331        uint256 ret = 0;


```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L331


```solidity
file: /contracts/thirdparty/optimism/rlp/RLPReader.sol

72        uint256 itemCount = 0;

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L72


## [G-06]  State varaibles only set in the Constructor should be declared `Immutable`

```solidity
file: /contracts/automata-attestation/utils/SigVerifyLib.sol

18    address private ES256VERIFIER;

    constructor(address es256Verifier) {
        ES256VERIFIER = es256Verifier;
    }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L18
## [G-07] Internal functions only called once can be inlined to save gas


```solidity
file: /contracts/libs/LibAddress.sol

45    function supportsInterface(
        address _addr,
        bytes4 _interfaceId
    )
        internal
        view
        returns (bool result_)
    {


61    function isValidSignature(
        address _addr,
        bytes32 _hash,
        bytes memory _sig
    )
        internal
        view
        returns (bool)
    {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L45C1-L53C6


```solidity
file: /contracts/L1/gov/TaikoGovernor.sol

127    function _execute(
        uint256 _proposalId,
        address[] memory _targets,
        uint256[] memory _values,
        bytes[] memory _calldatas,
        bytes32 _descriptionHash
    )
        internal

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L127C1-L134C17


```solidity
file: /contracts/L1/libs/LibDepositing.sol

122    function canDepositEthToL2(
        TaikoData.State storage _state,
        TaikoData.Config memory _config,
        uint256 _amount
    )
        internal
        view
        returns (bool)
    {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L122C1-L129C23


```solidity
file: /contracts/L1/libs/LibProposing.sol

287    function isBlobReusable(
        TaikoData.State storage _state,
        TaikoData.Config memory _config,
        bytes32 _blobHash
    )
        internal
        view
        returns (bool)
    {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L287C1-L295C6


## [G-08] `keccak256()` should only need to be called on a specific string literal once

It should be saved to an immutable variable, and the variable used instead. If the hash is being used as a part of a function selector, the cast to `bytes4` should also only be done once


```solidity
file:

242        assembly {
            publicInputHashOld := keccak256(inputs, 8192 /*mul(256, 32)*/ )
        }

        inputs[_blockId % 255] = blockhash(_blockId);
        assembly {
            publicInputHashNew := keccak256(inputs, 8192 /*mul(256, 32)*/ )
249        }


```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L242-L249



## [G-09] Optimize Names to save Gas

```solidity
file: /contracts/L1/TaikoToken.sol

15  contract TaikoToken is EssentialContract, ERC20SnapshotUpgradeable, ERC20VotesUpgradeable {


```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L15


```solidity
file: /contracts/automata-attestation/lib/PEMCertChainLib.sol

12 contract PEMCertChainLib is IPEMCertChainLib {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L12


```solidity
file: /packages/protocol/contracts/bridge/Bridge.sol

16   contract Bridge is EssentialContract, IBridge {


```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L16


```solidity
file: /contracts/common/AddressManager.sol

10  contract AddressManager is EssentialContract, IAddressManager {


```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L10



## [G-10] `Require() `/ `Revert()` string longer than 32 bytes cost extra gas 


```solidity
file: /contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

87   require(
            v3Quote.v3AuthData.certification.certType == 5,
            "certType must be 5: Concatenated PCK Cert Chain (PEM formatted)"
90        );

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L87-L90


```solidity
file: /contracts/thirdparty/optimism/rlp/RLPReader.sol

37  require(
            _in.length > 0,
            "RLPReader: length of an RLP item must be greater than zero to be decodable"
        
        );

56       require(
            itemType == RLPItemType.LIST_ITEM,
            "RLPReader: decoded item type for list is not a list item"
        );


61        require(
            listOffset + listLength == _in.length,
            "RLPReader: list item has an invalid data remainder"
        );

112       require(
            itemType == RLPItemType.DATA_ITEM,
            "RLPReader: decoded item type for bytes is not a data item"
        );

117        require(
            _in.length == itemOffset + itemLength,
            "RLPReader: bytes value contains an invalid remainder"
        );

152        require(
            _in.length > 0,
            "RLPReader: length of an RLP item must be greater than zero to be decodable"
        );

172           require(
                _in.length > strLen,
                "RLPReader: length of content must be greater than string length (short string)"
            );

182            require(
                strLen != 1 || firstByteOfContent >= 0x80,
                "RLPReader: invalid prefix, single byte < 0x80 are not prefixed (short string)"
            );
                            
        

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L37-L40


```solidity
file: /contracts/thirdparty/optimism/trie/MerkleTrie.sol

89             require(currentKeyIndex <= key.length, "MerkleTrie: key index exceeds total key length");

125               require(
                        i == proof.length - 1,
                        "MerkleTrie: value node must be last node in proof (branch)"
                    );

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L89


## [G-11]  Setting the constructor to `payable`

You can cut out 10 opcodes in the creation-time EVM bytecode if you declare a constructor payable. Making the constructor payable eliminates the need for an initial check of msg.value == 0 and saves 13 gas on deployment with no security risks.


```solidity
file: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

54    constructor(address sigVerifyLibAddr, address pemCertLibAddr) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L54C1-L54C68


## [G-12]  Can make the variable outside the loop to save gas

```solidity
file: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

214        for (uint256 i; i < tcb.tcbLevels.length; ++i) {
            TCBInfoStruct.TCBLevelObj memory current = tcb.tcbLevels[i];
            bool pceSvnIsHigherOrGreater = pck.sgxExtension.pcesvn >= current.pcesvn;
217            bool cpuSvnsAreHigherOrGreater = _isCpuSvnHigherOrGreater(

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L214-L217


```solidity
file: /contracts/automata-attestation/lib/PEMCertChainLib.sol

355            uint256 svnPtr = der.firstChildOf(svnParentPtr); // OID
356            uint256 svnValuePtr = der.nextSiblingOf(svnPtr); // value
357            bytes memory svnValueBytes = der.bytesAt(svnValu

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L355





## [G-13] Use constants instead of `type(uintx).max`

type(uint120).max or type(uint128).max, etc. it uses more gas in the distribution process and also for each transaction than constant usage.

```solidity
file: /contracts/automata-attestation/utils/BytesUtils.sol

91                    mask = type(uint256).max; // aka 0xffffff....


```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L91


```solidity
file: /contracts/bridge/Bridge.sol

27    uint256 internal constant PLACEHOLDER = type(uint256).max;


```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L27


```solidity
file: /contracts/L1/libs/LibDepositing.sol

150        if (_amount > type(uint96).max) revert L1_INVALID_ETH_DEPOSIT();


```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L150


```solidity
file: /contracts/L1/libs/LibVerifying.so

262                || _config.ethDepositMaxFee > type(uint96).max / _config.ethDepositMaxCountPerBlock


```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L262


```solidity
file: /contracts/L2/TaikoL2.sol

82        if (block.chainid <= 1 || block.chainid > type(uint64).max) {


```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L82

## [G-14] Use nested if and, avoid multiple check combinations

Using nested if is cheaper than using && multiple check combinations. There are more advantages, such as easier to read code and better coverage reports.

```solidity
file: /contracts/automata-attestation/lib/PEMCertChainLib.sol

134            if (
                (notBeforeTag != 0x17 && notBeforeTag == 0x18)
                    || (notAfterTag != 0x17 && notAfterTag != 0x18)
            ) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L134-L137


```solidity
file: /contracts/bridge/Bridge.sol

490        if (
            _message.data.length >= 4 // msg can be empty
                && bytes4(_message.data) != IMessageInvocable.onMessageInvocation.selector
                && _message.to.isContract()
        ) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L490-L494


```solidity
file: /contracts/L1/hooks/AssignmentHook.sol

81        if (
            block.timestamp > assignment.expiry
                || assignment.metaHash != 0 && _blk.metaHash != assignment.metaHash
                || assignment.parentMetaHash != 0 && _meta.parentMetaHash != assignment.parentMetaHash
                || assignment.maxBlockId != 0 && _meta.id > assignment.maxBlockId
                || assignment.maxProposedIn != 0 && block.number > assignment.maxProposedIn
        ) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L81-L87


```solidity
file: /contracts/signal/SignalService.sol

285        if (cacheStateRoot && _isFullProof && !_isLastHop) {


```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L285

## [G-15] Caching global variables is more expensive than using the actual variable (use msg.sender instead of caching it)

```solidity
file: /contracts/L1/hooks/AssignmentHook.sol

93        address taikoL1Address = msg.sender;


```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L93


## [G-16] Use `selfbalance()` instead of `address(this).balance`

Using selfbalance() instead of address(this).balance can save gas in Solidity because selfbalance() is a built-in function that returns the balance of the current contract directly as a uint256 value, without the need to create a new address object.
On the other hand, using address(this).balance to get the balance of the current contract creates a new address object, which consumes more gas and can make the code less efficient.
By using selfbalance(), you can reduce the amount of gas consumed by your Solidity code and make your contracts more efficient.

```solidity
file: /contracts/L1/hooks/AssignmentHook.sol

125        if (address(this).balance > 0) {
            taikoL1Address.sendEther(address(this).balance);
        }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L125-L127


```solidity
file: /contracts/L1/libs/LibProposing.sol

253                IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }(


260    if (address(this).balance != 0) {
                msg.sender.sendEther(address(this).balance);
            }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L253


```solidity
file: /contracts/L2/TaikoL2.sol

174            _to.sendEther(address(this).balance);


```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L174


## [G-17] `abi.encode()` is less efficient than  `abi.encodepacked()`

In terms of efficiency, abi.encodePacked() is generally considered to be more gas-efficient than abi.encode(), because it skips the step of adding function signatures and other metadata to the encoded data. However, this comes at the cost of reduced safety, as abi.encodePacked() does not perform any type checking or padding of data.

```solidity
file: /contracts/automata-attestation/utils/SigVerifyLib.sol

136        bytes memory args = abi.encode(sha256(tbs), r, s, gx, gy);


```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L136


```solidity
file: /contracts/bridge/Bridge.sol
 
450        return keccak256(abi.encode("TAIKO_MESSAGE", _message));


```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L450


```solidity
file: /contracts/L1/provers/GuardianProver.sol

46        bytes32 hash = keccak256(abi.encode(_meta, _tran));

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L46


```solidity
file: /contracts/team/airdrop/ERC20Airdrop2.sol

80        _verifyClaim(abi.encode(user, amount), proof);


```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L80
