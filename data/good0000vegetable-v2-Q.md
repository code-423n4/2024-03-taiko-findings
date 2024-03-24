[NC-#] Functions not used internally could be marked external
File: packages/protocol/contracts/L1/TaikoL1.sol

```solidity
124:         function unpause() public override {
132:         function canDepositEthToL2(uint256 _amount) public view returns (bool) {
137:         function isBlobReusable(bytes32 _blobHash) public view returns (bool) {
145:         function getBlock(uint64 _blockId)
162:         function getTransition(
176:         function getStateVariables()
```

File: packages/protocol/contracts/L1/TaikoToken.sol

```solidity
25:  function init(
47:  function burn(address _from, uint256 _amount) public onlyOwner {
52:  function snapshot() public onlyFromOwnerOrNamed("snapshooter") {
60:  function transfer(address _to, uint256 _amount) public override returns (bool) {
70:  function transferFrom(
```

File: packages/protocol/contracts/L1/gov/TaikoGovernor.sol

```solidity
48:         function propose(
69:         function propose(
89:         function supportsInterface(bytes4 _interfaceId)
99:         function state(uint256 _proposalId)
111:        function votingDelay() public pure override returns (uint256) {
117:        function votingPeriod() public pure override returns (uint256) {
123:        function proposalThreshold() public pure override returns (uint256) {
```

File: packages/protocol/contracts/L1/gov/TaikoTimelockController.sol

```solidity
24:         function getMinDelay() public view override returns (uint256) {
```

File: packages/protocol/contracts/L1/provers/Guardians.sol

```solidity
101:         function isApproved(bytes32 _hash) public view returns (bool) {
107:         function numGuardians() public view returns (uint256) {
```

File: packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol

```solidity
20:          function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {
47:          function getTierIds() public pure override returns (uint16[] memory tiers_) {
54:          function getMinTier(uint256) public pure override returns (uint16) {
```

File: packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol

```solidity
20:          function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {
58:          function getTierIds() public pure override returns (uint16[] memory tiers_) {
66:          function getMinTier(uint256 _rand) public pure override returns (uint16) {
```

File: packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol

```solidity
20:          function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {
58:          function getTierIds() public pure override returns (uint16[] memory tiers_) {
66:          function getMinTier(uint256 _rand) public pure override returns (uint16) {
```

File: packages/protocol/contracts/L2/TaikoL2.sol

```solidity
185:         function getBasefee(
200:         function getBlockHash(uint64 _blockId) public view returns (bytes32) {
```

File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

```solidity
43:          function getConfig() public view override returns (Config memory) {
```

File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

```solidity
103:         function configureTcbInfoJson(
```

File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

```solidity
24:          function verifyAttStmtSignature(
54:          function verifyCertificateSignature(
```

File: packages/protocol/contracts/bridge/Bridge.sol

```solidity
340:         function isMessageSent(Message calldata _message) public view returns (bool) {
352:         function proveMessageFailed(
374:         function proveMessageReceived(
403:         function context() public view returns (Context memory ctx_) {
```

File: packages/protocol/contracts/common/AddressManager.sol

```solidity
54:          function getAddress(uint64 _chainId, bytes32 _name) public view override returns (address) {
```

File: packages/protocol/contracts/common/EssentialContract.sol

```solidity
69:          function pause() public virtual whenNotPaused {
78:          function unpause() public virtual whenPaused {
```

File: packages/protocol/contracts/signal/SignalService.sol

```solidity
83:          function proveSignalReceived(
137:         function isChainDataSynced(
153:         function isSignalSent(address _app, bytes32 _signal) public view returns (bool) {
158:         function getSyncedChainData(
```

File: packages/protocol/contracts/team/TimelockTokenPool.sol

```solidity
204:         function getMyGrant(address _recipient) public view returns (Grant memory) {
```

File: packages/protocol/contracts/tokenvault/BaseVault.sol

```solidity
39:          function supportsInterface(bytes4 _interfaceId) public view virtual override returns (bool) {
```

File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

```solidity
66:          function mint(
83:          function mintBatch(
100:         function burn(
115:         function name() public view returns (string memory) {
121:         function symbol() public view returns (string memory) {
```

File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

```solidity
91:          function name()
102:          function symbol()
113:          function decimals()
125:         function canonical() public view returns (address, uint256) {
```

File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

```solidity
57:          function mint(address _account, uint256 _amount) public nonReentrant whenNotPaused {
75:          function burn(address _account, uint256 _amount) public nonReentrant whenNotPaused {
```

File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

```solidity
54:          function mint(
69:          function burn(
87:          function name() public view override(ERC721Upgradeable) returns (string memory) {
93:          function symbol() public view override(ERC721Upgradeable) returns (string memory) {
100:         function source() public view returns (address, uint256) {
107:         function tokenURI(uint256 _tokenId) public view virtual override returns (string memory) {
```

File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

```solidity
192:         function supportsInterface(bytes4 interfaceId)
```
