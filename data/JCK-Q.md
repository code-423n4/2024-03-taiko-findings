

# Low Risk

| Number | Issue | Instences |
|--------|-------|-----------|
|[G-01]| Unused/empty receive()/fallback() function | 1 |
|[G-02]| Use forceApprove in place of approve | 1 | 
|[G-03]| Governance functions should be controlled by time locks | 21 |
|[G-04]| Protect your NFT from copying in POW forks | 1 |
|[G-05]| External calls in an un-bounded for-loop may result in a DOS | 4 |
|[G-06]| Missing zero address check in functions with address parameters | 26 |
|[G-07]| onlyOwner functions not accessible if owner renounces ownership | 4  |
|[G-08]| pure function accesses storage | 3 |
|[G-09]| Use of abi.encodeWithSignature/abi.encodeWithSelector instead of abi.encodeCall | 7 |
|[G-10]| Some tokens may revert when zero value transfers are made | 11 |
|[G-11]| Consider using OpenZeppelin's SafeCast library to prevent unexpected overflows when downcasting | 6 |
|[G-12]| Arrays can grow in size without a way to shrink them | 1 |
|[G-13]| Events may be emitted out of order due to reentrancy | 4 |

## [L-01] Unused/empty receive()/fallback() function

If the intention is for the Ether to be used, the function should call another function or emit an event, otherwise it should revert.

```solidity
file: blob/main/packages/protocol/contracts/bridge/Bridge.sol

70   receive() external payable { }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L70


## [L-02] Use forceApprove in place of approve

The forceApprove function is a specialized solution addressing the issues that arise with non-standard ERC-20 tokens, such as USDT, which exhibit non-standard behavior in their approve function. These tokens may necessitate setting the allowance to 0 before changing it, may not return a boolean value from approve calls, or may return false instead of reverting on failure. OpenZeppelin's SafeERC20 library includes a forceApprove method to safely handle these peculiarities, ensuring that smart contracts can interact with such tokens without transaction failures. It rectifies inconsistencies by ensuring that all token interactions, including approvals, adhere to expected standards, even when the underlying tokens do not.

```solidity
file: blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol

47  approved_ = approve(_meta.id, hash);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L47

## [L-03] Governance functions should be controlled by time locks

Governance functions (such as upgrading contracts, setting critical parameters) should be controlled using time locks to introduce a delay between a proposal and its execution. This gives users time to exit before a potentially dangerous or malicious operation is applied.

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

65  function setMrSigner(bytes32 _mrSigner, bool _trusted) external onlyOwner {

69  function setMrEnclave(bytes32 _mrEnclave, bool _trusted) external onlyOwner {

73  function addRevokedCertSerialNum(
        uint256 index,
        bytes[] calldata serialNumBatch
    )
        external
        onlyOwner
    {

88  function removeRevokedCertSerialNum(
        uint256 index,
        bytes[] calldata serialNumBatch
    )
        external
        onlyOwner
    {

103 function configureTcbInfoJson(
        string calldata fmspc,
        TCBInfoStruct.TCBInfo calldata tcbInfoInput
    )
        public
        onlyOwner
    {blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol
    
114  function configureQeIdentityJson(EnclaveIdStruct.EnclaveId calldata qeIdentityInput)
        external
        onlyOwner
    {

122  function toggleLocalReportCheck() external onlyOwner {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L65

```solidity
file: blob/main/packages/protocol/contracts/common/AddressManager.sol

38  function setAddress(
        uint64 _chainId,
        bytes32 _name,
        address _newAddress
    )
        external
        virtual
        onlyOwner
    {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L38-L46
blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol
```solidity
file: blob/main/packages/protocol/contracts/common/EssentialContract.sol

114  function _authorizeUpgrade(address) internal virtual override onlyOwner { }

116  function _authorizePause(address) internal virtual onlyOwner { }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L114


```solidity
file: blob/main/packages/protocol/contracts/L1/TaikoToken.sol

47   function burn(address _from, uint256 _amount) public onlyOwner {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L47

```solidity
file: blob/main/packages/protocol/contracts/L1/provers/Guardians.sol
 
53  function setGuardians(
        address[] memory _newGuardians,
        uint8 _minGuardians
    )
        external
        onlyOwner
        nonReentrant
    {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L53-L60


```solidity
file: blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

25  function setConfigAndExcess(
        Config memory _newConfig,
        uint64 _newGasExcess
    )
        external
        virtual
        onlyOwner
    {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L25-L32

```solidity
file: blob/main/packages/protocol/contracts/signal/SignalService.sol

56  function authorize(address _addr, bool _authorize) external onlyOwner {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L56

```solidity
file: blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol

135  function grant(address _recipient, Grant memory _grant) external onlyOwner {

150  function void(address _recipient) external onlyOwner {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L135

```solidity
file: blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

45  function setConfig(
        uint64 _claimStart,
        uint64 _claimEnd,
        bytes32 _merkleRoot
    )
        external
        onlyOwner
    {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L45-L52


```solidity
file: blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol

80  function setSnapshoter(address _snapshooter) external onlyOwner {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L80

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol

148  function changeBridgedToken(
        CanonicalERC20 calldata _ctoken,
        address _btokenNew
    )
        external
        nonReentrant
        whenNotPaused
        onlyOwner
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L148-L155

```solidity
file: blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol

90  function addInstances(address[] calldata _instances)
        external
        onlyOwner
        returns (uint256[] memory)
    {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L90-L94

## [L-04] Protect your NFT from copying in POW forks

Ethereum has performed the long-awaited "merge" that will dramatically reduce the environmental impact of the network

There may be forked versions of Ethereum, which could cause confusion and lead to scams as duplicated NFT assets enter the market.

If the Ethereum Merge, which took place in September 2022, results in the Blockchain splitting into two Blockchains due to the 'THE DAO' attack in 2016, this could result in duplication of immutable tokens (NFTs).

In any case, duplicate NFTs will exist due to the ETH proof-of-work chain and other potential forks, and there’s likely to be some level of confusion around which assets are 'official' or 'authentic.'

Even so, there could be a frenzy for these copies, as NFT owners attempt to flip the proof-of-work versions of their valuable tokens.

As ETHPOW and any other forks spin off of the Ethereum mainnet, they will yield duplicate versions of Ethereum’s NFTs. An NFT is simply a blockchain token, and it can work as a deed of ownership to digital items like artwork and collectibles. A forked Ethereum chain will thus have duplicated deeds that point to the same tokenURI

About Merge Replay Attack: https://twitter.com/elerium115/status/1558471934924431363?s=20&t=RRheaYJwo-GmSnePwofgag

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol

107  function tokenURI(uint256 _tokenId) public view virtual override returns (string memory) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L107

## [L-05] External calls in an un-bounded for-loop may result in a DOS


Consider limiting the number of iterations in for-loops that make external calls

```solidity
file: blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

59  for (uint256 i; i < tokenIds.length; ++i) {
            IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);
        }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59-L61

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol

170  for (uint256 i; i < _tokenIds.length; ++i) {
                IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);
            }
        
210  for (uint256 i; i < _op.tokenIds.length; ++i) {
                    t.safeTransferFrom(_user, address(this), _op.tokenIds[i]);
                }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L170-L172

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol

269  for (uint256 i; i < _op.tokenIds.length; ++i) {
                    IERC1155(_op.token).safeTransferFrom({
                        from: msg.sender,
                        to: address(this),
                        id: _op.tokenIds[i],
                        amount: _op.amounts[i],
                        data: ""
                    });
                }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L269-L277

## [L-06] Missing zero address check in functions with address parameters

Adding a zero address check for each address type parameter can prevent errors.

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

54  constructor(address sigVerifyLibAddr, address pemCertLibAddr) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L54


```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

21   function parseInput(
        bytes memory quote,
        address pemCertLibAddr
    )

203  function parseAuthDataAndVerifyCertType(
        bytes memory rawAuthData,
        address pemCertLibAddr
    )

267 function parseCerificationChainBytes(
        bytes memory certBytes,
        address pemCertLibAddr
    )

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L21-L24

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

20  constructor(address es256Verifier) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L20

```solidity
file: blob/main/packages/protocol/contracts/bridge/Bridge.sol

75  function init(address _owner, address _addressManager) external initializer {

101 function banAddress(
        address _addr,
        bool _ban
    )

541  function _storeContext(bytes32 _msgHash, address _from, uint64 _srcChainId) private {

577  function _proveSignalReceived(
        address _signalService,

```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L75

```solidity
file: blob/main/packages/protocol/contracts/common/AddressManager.sol

30  function init(address _owner) external initializer {

38  function setAddress(
        uint64 _chainId,
        bytes32 _name,
        address _newAddress
    )
    
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L30

```solidity
file: blob/main/packages/protocol/contracts/common/AddressResolver.sol

58  function __AddressResolver_init(address _addressManager) internal virtual onlyInitializing {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L58

```solidity
file: blob/main/packages/protocol/contracts/common/EssentialContract.sol

95  function __Essential_init(
        address _owner,
        address _addressManager
    )

109  function __Essential_init(address _owner) internal virtual {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L95-L98

```solidity
file: blob/main/packages/protocol/contracts/L1/TaikoL1.sol

42  function init(
        address _owner,
        address _addressManager,
        bytes32 _genesisBlockHash
    )

119 function depositEtherToL2(address _recipient) external payable nonReentrant whenNotPaused {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L42-L46

```solidity
file: blob/main/packages/protocol/contracts/L1/TaikoToken.sol

25  function init(
        address _owner,
        string calldata _name,
        string calldata _symbol,
        address _recipient
    )

47 function burn(address _from, uint256 _amount) public onlyOwner {

60 function transfer(address _to, uint256 _amount) public override returns (bool) {

70   function transferFrom(
        address _from,
        address _to,
        uint256 _amount
    )

83  function _beforeTokenTransfer(
        address _from,
        address _to,
        uint256 _amount
    )

94  function _afterTokenTransfer(
        address _from,
        address _to,
        uint256 _amount
    )

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L25-L31

```solidity
file: blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol

60  function __CrossChainOwned_init(
        address _owner,
        address _addressManager,
        uint64 _ownerChainId
    )

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L60-L64


```solidity
file: blob/main/packages/protocol/contracts/signal/SignalService.sol

206  function _verifyHopProof(
        uint64 _chainId,
        address _app,
        bytes32 _signal,
        bytes32 _value,
        HopProof memory _hop,
        address _signalService
    )

253  function _sendSignal(
        address _app,
        bytes32 _signal,
        bytes32 _value
    )

298  function _loadSignalValue(
        address _app,
        bytes32 _signal
    )

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L206-L214

## [L-07] onlyOwner functions not accessible if owner renounces ownership

The owner is able to perform certain privileged activities, but it's possible to set the owner to address(0). This can represent a certain risk if the ownership is renounced for any other reason than by design.

Renouncing ownership will leave the contract without an owner, therefore limiting any functionality that needs authority.

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol

80  function setSnapshoter(address _snapshooter) external onlyOwner {
        snapshooter = _snapshooter;
    }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L80-L82


```solidity
file: blob/main/packages/protocol/contracts/common/AddressManager.sol

38   function setAddress(
        uint64 _chainId,
        bytes32 _name,
        address _newAddress
    )
        external
        virtual
        onlyOwner
    {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L38-L46

```solidity
file: blob/main/packages/protocol/contracts/L1/TaikoToken.sol

47   function burn(address _from, uint256 _amount) public onlyOwner {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L47

```solidity
file: blob/main/packages/protocol/contracts/L1/provers/Guardians.sol

53  function setGuardians(
        address[] memory _newGuardians,
        uint8 _minGuardians
    )
        external
        onlyOwner
        nonReentrant
    {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L53-L60

## [L-08] pure function accesses storage

While the compiler currently flags functions like these as being pure, this is a bug which will be fixed in a future version, so it's best to not use pure visibility, in order to not break when this bug is fixed.

```solidity
file: blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol

54  function getMinTier(uint256) public pure override returns (uint16) {
        return LibTiers.TIER_OPTIMISTIC;
    }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L54-L56

```solidity
file: blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol

66   function getMinTier(uint256 _rand) public pure override returns (uint16) {
        // 0.1% require SGX + ZKVM; all others require SGX
        if (_rand % 1000 == 0) return LibTiers.TIER_SGX_ZKVM;
        else return LibTiers.TIER_SGX;
    }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L66-L70

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol

39  function buildSymbol(string memory _symbol) internal pure returns (string memory) {
        return string.concat(_symbol, ".t");
    }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol39-L41

## [L-09] Use of abi.encodeWithSignature/abi.encodeWithSelector instead of abi.encodeCall

Consider refactoring the code by using abi.encodeCall instead of abi.encodeWithSignature/abi.encodeWithSelector, as the former keeps the code typo/type safe. https://github.com/OpenZeppelin/openzeppelin-contracts/issues/3693

```solidity
file: main/packages/protocol/contracts/bridge/Bridge.sol

587   bytes memory data = abi.encodeCall(

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L587

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol

401  msgData_ = abi.encodeCall(

428  bytes memory data = abi.encodeCall(

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L401

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol

216  msgData_ = abi.encodeCall(

241  bytes memory data = abi.encodeCall(

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L216


```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol

280  msgData_ = abi.encodeCall(

304  bytes memory data = abi.encodeCall(

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L280

## [L-10] Some tokens may revert when zero value transfers are made

In spite of the fact that EIP-20 states that zero-valued transfers must be accepted, some tokens, such as LEND will revert if this is attempted, which may cause transactions that involve other tokens (such as batch operations) to fully revert. Consider skipping the transfer if the amount is zero, which will also save gas.


```solidity
file: blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

63  IERC20(token).transferFrom(vault, user, amount);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L63


```solidity
file: blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

91  IERC20(token).transferFrom(vault, user, amount);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L91


```solidity
file: blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol

149  super._beforeTokenTransfer(_from, _to, _amount);

160  super._afterTokenTransfer(_from, _to, _amount);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L149


```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol

270  address token = _transferTokens(ctoken, to, amount);

303  address token = _transferTokens(ctoken, _message.srcOwner, amount);

330  IERC20(token_).safeTransfer(_to, _amount);

379  t.safeTransferFrom({ from: msg.sender, to: address(this), value: _amount });

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L270

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol

145  address token = _transferTokens(ctoken, message.srcOwner, tokenIds, amounts);

226  IERC1155(token).safeBatchTransferFrom(address(this), to, tokenIds, amounts, "");

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L145


```solidity
file: blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol
 
48  usdc.transferFrom(_from, address(this), _amount);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L48


## [L-11] Consider using OpenZeppelin's SafeCast library to prevent unexpected overflows when downcasting

Downcasting from uint256/int256 in Solidity does not revert on overflow. This can result in undesired exploitation or bugs, since developers usually assume that overflows raise errors. https://docs.openzeppelin.com/contracts/3.x/api/utils#SafeCast OpenZeppelin's SafeCast library restores this intuition by reverting the transaction when such an operation overflows. Using this library eliminates an entire class of bugs, so it's recommended to use it always. Some exceptions are acceptable like with the classic uint256(uint160(address(variable)))

```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

217  cert.certType = uint16(littleEndianDecode(rawAuthData.substring(offset, 2)));

222  cert.certDataSize = uint32(littleEndianDecode(rawAuthData.substring(offset, 4)));

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L217


```solidity
file: blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

20  return uint80(self >> 80);

206  ixFirstContentByte = uint80(ix + 2 + lengthbytesLength);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L20


```solidity
file: blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol

89  recipient: address(uint160(data >> 96)),

90   amount: uint96(data),

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L89

## [L-12] Arrays can grow in size without a way to shrink them

Array entries are added but are never removed. Consider whether this should be the case, or whether there should be a maximum, or whether old entries should be removed. Cases where there are specific potential problems will be flagged separately under a different issue.

```solidity
file: blob/main/packages/protocol/contracts/L1/provers/Guardians.sol

87  guardians.push(guardian);

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L87

## [L-13] Events may be emitted out of order due to reentrancy
    
To strictly conform to the Checks Effects Interactions pattern, it is recommended to emit events before any external interactions.

```solidity
file: blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

75   function burn(address _account, uint256 _amount) public nonReentrant whenNotPaused {
        if (_isMigratingOut()) {
            // Only the owner of the tokens himself can migrate out
            if (msg.sender != _account) revert BB_PERMISSION_DENIED();
            // Outbound migration
            emit MigratedTo(migratingAddress, _account, _amount);
            // Ask the new bridged token to mint token for the user.
            IBridgedERC20(migratingAddress).mint(_account, _amount);
        } else if (msg.sender != resolve("erc20_vault", true)) {
            // Only the vault can burn tokens when not migrating out
            revert RESOLVER_DENIED();
        }

        _burnToken(_account, _amount);
    }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L75-L89

```solidity
file: blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol

29      function depositEtherToL2(
        TaikoData.State storage _state,
        TaikoData.Config memory _config,
        IAddressResolver _resolver,
        address _recipient
    )
        internal
    {
        if (!canDepositEthToL2(_state, _config, msg.value)) {
            revert L1_INVALID_ETH_DEPOSIT();
        }

        _resolver.resolve("bridge", false).sendEther(msg.value);

        // Append the deposit to the queue.
        address recipient_ = _recipient == address(0) ? msg.sender : _recipient;
        uint256 slot = _state.slotA.numEthDeposits % _config.ethDepositRingBufferSize;

        // range of msg.value is checked by next line.
        _state.ethDeposits[slot] = _encodeEthDeposit(recipient_, msg.value);

        emit EthDeposited(
            TaikoData.EthDeposit({
                recipient: recipient_,
                amount: uint96(msg.value),
                id: _state.slotA.numEthDeposits
            })
        );

        // Unchecked is safe:
        // - uint64 can store up to ~1.8 * 1e19, which can represent 584K years
        // if we are depositing at every second
        unchecked {
            _state.slotA.numEthDeposits++;
        }
    }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L29-L64


```solidity
file: blob/main/packages/protocol/contracts/L1/libs/LibProving.sol

91  function proveBlock(
        TaikoData.State storage _state,
        TaikoData.Config memory _config,
        IAddressResolver _resolver,
        TaikoData.BlockMetadata memory _meta,
        TaikoData.Transition memory _tran,
        TaikoData.TierProof memory _proof
    )
        internal
        returns (uint8 maxBlocksToVerify_)
    {
        // Make sure parentHash is not zero
        // To contest an existing transition, simply use any non-zero value as
        // the blockHash and stateRoot.
        if (_tran.parentHash == 0 || _tran.blockHash == 0 || _tran.stateRoot == 0) {
            revert L1_INVALID_TRANSITION();
        }

        // Check that the block has been proposed but has not yet been verified.
        TaikoData.SlotB memory b = _state.slotB;
        if (_meta.id <= b.lastVerifiedBlockId || _meta.id >= b.numBlocks) {
            revert L1_INVALID_BLOCK_ID();
        }

        uint64 slot = _meta.id % _config.blockRingBufferSize;
        TaikoData.Block storage blk = _state.blocks[slot];

        // Check the integrity of the block data. It's worth noting that in
        // theory, this check may be skipped, but it's included for added
        // caution.
        if (blk.blockId != _meta.id || blk.metaHash != keccak256(abi.encode(_meta))) {
            revert L1_BLOCK_MISMATCH();
        }

        // Each transition is uniquely identified by the parentHash, with the
        // blockHash and stateRoot open for later updates as higher-tier proofs
        // become available. In cases where a transition with the specified
        // parentHash does not exist, the transition ID (tid) will be set to 0.
        (uint32 tid, TaikoData.TransitionState storage ts) =
            _createTransition(_state, blk, _tran, slot);

        // The new proof must meet or exceed the minimum tier required by the
        // block or the previous proof; it cannot be on a lower tier.
        if (_proof.tier == 0 || _proof.tier < _meta.minTier || _proof.tier < ts.tier) {
            revert L1_INVALID_TIER();
        }

        // Retrieve the tier configurations. If the tier is not supported, the
        // subsequent action will result in a revert.
        ITierProvider.Tier memory tier =
            ITierProvider(_resolver.resolve("tier_provider", false)).getTier(_proof.tier);

        // Check if this prover is allowed to submit a proof for this block
        _checkProverPermission(_state, blk, ts, tid, tier);

        // We must verify the proof, and any failure in proof verification will
        // result in a revert.
        //
        // It's crucial to emphasize that the proof can be assessed in two
        // potential modes: "proving mode" and "contesting mode." However, the
        // precise verification logic is defined within each tier's IVerifier
        // contract implementation. We simply specify to the verifier contract
        // which mode it should utilize - if the new tier is higher than the
        // previous tier, we employ the proving mode; otherwise, we employ the
        // contesting mode (the new tier cannot be lower than the previous tier,
        // this has been checked above).
        //
        // It's obvious that proof verification is entirely decoupled from
        // Taiko's core protocol.
        {
            address verifier = _resolver.resolve(tier.verifierName, true);

            if (verifier != address(0)) {
                bool isContesting = _proof.tier == ts.tier && tier.contestBond != 0;

                IVerifier.Context memory ctx = IVerifier.Context({
                    metaHash: blk.metaHash,
                    blobHash: _meta.blobHash,
                    // Separate msgSender to allow the prover to be any address in the future.
                    prover: msg.sender,
                    msgSender: msg.sender,
                    blockId: blk.blockId,
                    isContesting: isContesting,
                    blobUsed: _meta.blobUsed
                });

                IVerifier(verifier).verifyProof(ctx, _tran, _proof);
            } else if (tier.verifierName != TIER_OP) {
                // The verifier can be address-zero, signifying that there are no
                // proof checks for the tier. In practice, this only applies to
                // optimistic proofs.
                revert L1_MISSING_VERIFIER();
            }
        }

        bool isTopTier = tier.contestBond == 0;
        IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));

        if (isTopTier) {
            // A special return value from the top tier prover can signal this
            // contract to return all liveness bond.
            bool returnLivenessBond = blk.livenessBond > 0 && _proof.data.length == 32
                && bytes32(_proof.data) == RETURN_LIVENESS_BOND;

            if (returnLivenessBond) {
                tko.transfer(blk.assignedProver, blk.livenessBond);
                blk.livenessBond = 0;
            }
        }

        bool sameTransition = _tran.blockHash == ts.blockHash && _tran.stateRoot == ts.stateRoot;

        if (_proof.tier > ts.tier) {
            // Handles the case when an incoming tier is higher than the current transition's tier.
            // Reverts when the incoming proof tries to prove the same transition
            // (L1_ALREADY_PROVED).
            _overrideWithHigherProof(ts, _tran, _proof, tier, tko, sameTransition);

            emit TransitionProved({
                blockId: blk.blockId,
                tran: _tran,
                prover: msg.sender,
                validityBond: tier.validityBond,
                tier: _proof.tier
            });
        } else {
            // New transition and old transition on the same tier - and if this transaction tries to
            // prove the same, it reverts
            if (sameTransition) revert L1_ALREADY_PROVED();

            if (isTopTier) {
                // The top tier prover re-proves.
                assert(tier.validityBond == 0);
                assert(ts.validityBond == 0 && ts.contestBond == 0 && ts.contester == address(0));

                ts.prover = msg.sender;
                ts.blockHash = _tran.blockHash;
                ts.stateRoot = _tran.stateRoot;

                emit TransitionProved({
                    blockId: blk.blockId,
                    tran: _tran,
                    prover: msg.sender,
                    validityBond: 0,
                    tier: _proof.tier
                });
            } else {
                // Contesting but not on the highest tier
                if (ts.contester != address(0)) revert L1_ALREADY_CONTESTED();

                // Burn the contest bond from the prover.
                tko.transferFrom(msg.sender, address(this), tier.contestBond);

                // We retain the contest bond within the transition, just in
                // case this configuration is altered to a different value
                // before the contest is resolved.
                //
                // It's worth noting that the previous value of ts.contestBond
                // doesn't have any significance.
                ts.contestBond = tier.contestBond;
                ts.contester = msg.sender;
                ts.contestations += 1;

                emit TransitionContested({
                    blockId: blk.blockId,
                    tran: _tran,
                    contester: msg.sender,
                    contestBond: tier.contestBond,
                    tier: _proof.tier
                });
            }
        }

        ts.timestamp = uint64(block.timestamp);
        return tier.maxBlocksToVerifyPerProof;
    }

```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L91-L266


```solidity
file:  blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol

197  
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

            if (numBlocksVerified > 0) {
                uint64 lastVerifiedBlockId = b.lastVerifiedBlockId + numBlocksVerified;

                // Update protocol level state variables
                _state.slotB.lastVerifiedBlockId = lastVerifiedBlockId;

                // sync chain data
                _syncChainData(_config, _resolver, lastVerifiedBlockId, stateRoot);
            }
        }
    }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L197-L222