## NC-2: Functions not used internally could be marked external



- Found in contracts/L1/TaikoL1.sol [Line: 124](contracts/L1/TaikoL1.sol#L124)

	```solidity
	    function unpause() public override {
	```

- Found in contracts/L1/TaikoL1.sol [Line: 132](contracts/L1/TaikoL1.sol#L132)

	```solidity
	    function canDepositEthToL2(uint256 _amount) public view returns (bool) {
	```

- Found in contracts/L1/TaikoL1.sol [Line: 137](contracts/L1/TaikoL1.sol#L137)

	```solidity
	    function isBlobReusable(bytes32 _blobHash) public view returns (bool) {
	```

- Found in contracts/L1/TaikoL1.sol [Line: 145](contracts/L1/TaikoL1.sol#L145)

	```solidity
	    function getBlock(uint64 _blockId)
	```

- Found in contracts/L1/TaikoL1.sol [Line: 162](contracts/L1/TaikoL1.sol#L162)

	```solidity
	    function getTransition(
	```

- Found in contracts/L1/TaikoL1.sol [Line: 176](contracts/L1/TaikoL1.sol#L176)

	```solidity
	    function getStateVariables()
	```

- Found in contracts/L1/TaikoToken.sol [Line: 25](contracts/L1/TaikoToken.sol#L25)

	```solidity
	    function init(
	```

- Found in contracts/L1/TaikoToken.sol [Line: 47](contracts/L1/TaikoToken.sol#L47)

	```solidity
	    function burn(address _from, uint256 _amount) public onlyOwner {
	```

- Found in contracts/L1/TaikoToken.sol [Line: 52](contracts/L1/TaikoToken.sol#L52)

	```solidity
	    function snapshot() public onlyFromOwnerOrNamed("snapshooter") {
	```

- Found in contracts/L1/TaikoToken.sol [Line: 60](contracts/L1/TaikoToken.sol#L60)

	```solidity
	    function transfer(address _to, uint256 _amount) public override returns (bool) {
	```

- Found in contracts/L1/TaikoToken.sol [Line: 70](contracts/L1/TaikoToken.sol#L70)

	```solidity
	    function transferFrom(
	```

- Found in contracts/L1/gov/TaikoGovernor.sol [Line: 48](contracts/L1/gov/TaikoGovernor.sol#L48)

	```solidity
	    function propose(
	```

- Found in contracts/L1/gov/TaikoGovernor.sol [Line: 69](contracts/L1/gov/TaikoGovernor.sol#L69)

	```solidity
	    function propose(
	```

- Found in contracts/L1/gov/TaikoGovernor.sol [Line: 89](contracts/L1/gov/TaikoGovernor.sol#L89)

	```solidity
	    function supportsInterface(bytes4 _interfaceId)
	```

- Found in contracts/L1/gov/TaikoGovernor.sol [Line: 99](contracts/L1/gov/TaikoGovernor.sol#L99)

	```solidity
	    function state(uint256 _proposalId)
	```

- Found in contracts/L1/gov/TaikoGovernor.sol [Line: 111](contracts/L1/gov/TaikoGovernor.sol#L111)

	```solidity
	    function votingDelay() public pure override returns (uint256) {
	```

- Found in contracts/L1/gov/TaikoGovernor.sol [Line: 117](contracts/L1/gov/TaikoGovernor.sol#L117)

	```solidity
	    function votingPeriod() public pure override returns (uint256) {
	```

- Found in contracts/L1/gov/TaikoGovernor.sol [Line: 123](contracts/L1/gov/TaikoGovernor.sol#L123)

	```solidity
	    function proposalThreshold() public pure override returns (uint256) {
	```

- Found in contracts/L1/gov/TaikoTimelockController.sol [Line: 24](contracts/L1/gov/TaikoTimelockController.sol#L24)

	```solidity
	    function getMinDelay() public view override returns (uint256) {
	```

- Found in contracts/L1/provers/Guardians.sol [Line: 101](contracts/L1/provers/Guardians.sol#L101)

	```solidity
	    function isApproved(bytes32 _hash) public view returns (bool) {
	```

- Found in contracts/L1/provers/Guardians.sol [Line: 107](contracts/L1/provers/Guardians.sol#L107)

	```solidity
	    function numGuardians() public view returns (uint256) {
	```

- Found in contracts/L1/tiers/DevnetTierProvider.sol [Line: 20](contracts/L1/tiers/DevnetTierProvider.sol#L20)

	```solidity
	    function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {
	```

- Found in contracts/L1/tiers/DevnetTierProvider.sol [Line: 47](contracts/L1/tiers/DevnetTierProvider.sol#L47)

	```solidity
	    function getTierIds() public pure override returns (uint16[] memory tiers_) {
	```

- Found in contracts/L1/tiers/DevnetTierProvider.sol [Line: 54](contracts/L1/tiers/DevnetTierProvider.sol#L54)

	```solidity
	    function getMinTier(uint256) public pure override returns (uint16) {
	```

- Found in contracts/L1/tiers/MainnetTierProvider.sol [Line: 20](contracts/L1/tiers/MainnetTierProvider.sol#L20)

	```solidity
	    function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {
	```

- Found in contracts/L1/tiers/MainnetTierProvider.sol [Line: 58](contracts/L1/tiers/MainnetTierProvider.sol#L58)

	```solidity
	    function getTierIds() public pure override returns (uint16[] memory tiers_) {
	```

- Found in contracts/L1/tiers/MainnetTierProvider.sol [Line: 66](contracts/L1/tiers/MainnetTierProvider.sol#L66)

	```solidity
	    function getMinTier(uint256 _rand) public pure override returns (uint16) {
	```

- Found in contracts/L1/tiers/TestnetTierProvider.sol [Line: 20](contracts/L1/tiers/TestnetTierProvider.sol#L20)

	```solidity
	    function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {
	```

- Found in contracts/L1/tiers/TestnetTierProvider.sol [Line: 58](contracts/L1/tiers/TestnetTierProvider.sol#L58)

	```solidity
	    function getTierIds() public pure override returns (uint16[] memory tiers_) {
	```

- Found in contracts/L1/tiers/TestnetTierProvider.sol [Line: 66](contracts/L1/tiers/TestnetTierProvider.sol#L66)

	```solidity
	    function getMinTier(uint256 _rand) public pure override returns (uint16) {
	```

- Found in contracts/L2/TaikoL2.sol [Line: 185](contracts/L2/TaikoL2.sol#L185)

	```solidity
	    function getBasefee(
	```

- Found in contracts/L2/TaikoL2.sol [Line: 200](contracts/L2/TaikoL2.sol#L200)

	```solidity
	    function getBlockHash(uint64 _blockId) public view returns (bytes32) {
	```

- Found in contracts/L2/TaikoL2EIP1559Configurable.sol [Line: 43](contracts/L2/TaikoL2EIP1559Configurable.sol#L43)

	```solidity
	    function getConfig() public view override returns (Config memory) {
	```

- Found in contracts/automata-attestation/AutomataDcapV3Attestation.sol [Line: 103](contracts/automata-attestation/AutomataDcapV3Attestation.sol#L103)

	```solidity
	    function configureTcbInfoJson(
	```

- Found in contracts/automata-attestation/utils/SigVerifyLib.sol [Line: 24](contracts/automata-attestation/utils/SigVerifyLib.sol#L24)

	```solidity
	    function verifyAttStmtSignature(
	```

- Found in contracts/automata-attestation/utils/SigVerifyLib.sol [Line: 54](contracts/automata-attestation/utils/SigVerifyLib.sol#L54)

	```solidity
	    function verifyCertificateSignature(
	```

- Found in contracts/bridge/Bridge.sol [Line: 340](contracts/bridge/Bridge.sol#L340)

	```solidity
	    function isMessageSent(Message calldata _message) public view returns (bool) {
	```

- Found in contracts/bridge/Bridge.sol [Line: 352](contracts/bridge/Bridge.sol#L352)

	```solidity
	    function proveMessageFailed(
	```

- Found in contracts/bridge/Bridge.sol [Line: 374](contracts/bridge/Bridge.sol#L374)

	```solidity
	    function proveMessageReceived(
	```

- Found in contracts/bridge/Bridge.sol [Line: 403](contracts/bridge/Bridge.sol#L403)

	```solidity
	    function context() public view returns (Context memory ctx_) {
	```

- Found in contracts/common/AddressManager.sol [Line: 54](contracts/common/AddressManager.sol#L54)

	```solidity
	    function getAddress(uint64 _chainId, bytes32 _name) public view override returns (address) {
	```

- Found in contracts/common/EssentialContract.sol [Line: 69](contracts/common/EssentialContract.sol#L69)

	```solidity
	    function pause() public virtual whenNotPaused {
	```

- Found in contracts/common/EssentialContract.sol [Line: 78](contracts/common/EssentialContract.sol#L78)

	```solidity
	    function unpause() public virtual whenPaused {
	```

- Found in contracts/signal/SignalService.sol [Line: 83](contracts/signal/SignalService.sol#L83)

	```solidity
	    function proveSignalReceived(
	```

- Found in contracts/signal/SignalService.sol [Line: 137](contracts/signal/SignalService.sol#L137)

	```solidity
	    function isChainDataSynced(
	```

- Found in contracts/signal/SignalService.sol [Line: 153](contracts/signal/SignalService.sol#L153)

	```solidity
	    function isSignalSent(address _app, bytes32 _signal) public view returns (bool) {
	```

- Found in contracts/signal/SignalService.sol [Line: 158](contracts/signal/SignalService.sol#L158)

	```solidity
	    function getSyncedChainData(
	```

- Found in contracts/team/TimelockTokenPool.sol [Line: 204](contracts/team/TimelockTokenPool.sol#L204)

	```solidity
	    function getMyGrant(address _recipient) public view returns (Grant memory) {
	```

- Found in contracts/tokenvault/BaseVault.sol [Line: 39](contracts/tokenvault/BaseVault.sol#L39)

	```solidity
	    function supportsInterface(bytes4 _interfaceId) public view virtual override returns (bool) {
	```

- Found in contracts/tokenvault/BridgedERC1155.sol [Line: 66](contracts/tokenvault/BridgedERC1155.sol#L66)

	```solidity
	    function mint(
	```

- Found in contracts/tokenvault/BridgedERC1155.sol [Line: 83](contracts/tokenvault/BridgedERC1155.sol#L83)

	```solidity
	    function mintBatch(
	```

- Found in contracts/tokenvault/BridgedERC1155.sol [Line: 100](contracts/tokenvault/BridgedERC1155.sol#L100)

	```solidity
	    function burn(
	```

- Found in contracts/tokenvault/BridgedERC1155.sol [Line: 115](contracts/tokenvault/BridgedERC1155.sol#L115)

	```solidity
	    function name() public view returns (string memory) {
	```

- Found in contracts/tokenvault/BridgedERC1155.sol [Line: 121](contracts/tokenvault/BridgedERC1155.sol#L121)

	```solidity
	    function symbol() public view returns (string memory) {
	```

- Found in contracts/tokenvault/BridgedERC20.sol [Line: 91](contracts/tokenvault/BridgedERC20.sol#L91)

	```solidity
	    function name()
	```

- Found in contracts/tokenvault/BridgedERC20.sol [Line: 102](contracts/tokenvault/BridgedERC20.sol#L102)

	```solidity
	    function symbol()
	```

- Found in contracts/tokenvault/BridgedERC20.sol [Line: 113](contracts/tokenvault/BridgedERC20.sol#L113)

	```solidity
	    function decimals()
	```

- Found in contracts/tokenvault/BridgedERC20.sol [Line: 125](contracts/tokenvault/BridgedERC20.sol#L125)

	```solidity
	    function canonical() public view returns (address, uint256) {
	```

- Found in contracts/tokenvault/BridgedERC20Base.sol [Line: 57](contracts/tokenvault/BridgedERC20Base.sol#L57)

	```solidity
	    function mint(address _account, uint256 _amount) public nonReentrant whenNotPaused {
	```

- Found in contracts/tokenvault/BridgedERC20Base.sol [Line: 75](contracts/tokenvault/BridgedERC20Base.sol#L75)

	```solidity
	    function burn(address _account, uint256 _amount) public nonReentrant whenNotPaused {
	```

- Found in contracts/tokenvault/BridgedERC721.sol [Line: 54](contracts/tokenvault/BridgedERC721.sol#L54)

	```solidity
	    function mint(
	```

- Found in contracts/tokenvault/BridgedERC721.sol [Line: 69](contracts/tokenvault/BridgedERC721.sol#L69)

	```solidity
	    function burn(
	```

- Found in contracts/tokenvault/BridgedERC721.sol [Line: 87](contracts/tokenvault/BridgedERC721.sol#L87)

	```solidity
	    function name() public view override(ERC721Upgradeable) returns (string memory) {
	```

- Found in contracts/tokenvault/BridgedERC721.sol [Line: 93](contracts/tokenvault/BridgedERC721.sol#L93)

	```solidity
	    function symbol() public view override(ERC721Upgradeable) returns (string memory) {
	```

- Found in contracts/tokenvault/BridgedERC721.sol [Line: 100](contracts/tokenvault/BridgedERC721.sol#L100)

	```solidity
	    function source() public view returns (address, uint256) {
	```

- Found in contracts/tokenvault/BridgedERC721.sol [Line: 107](contracts/tokenvault/BridgedERC721.sol#L107)

	```solidity
	    function tokenURI(uint256 _tokenId) public view virtual override returns (string memory) {
	```

- Found in contracts/tokenvault/ERC1155Vault.sol [Line: 192](contracts/tokenvault/ERC1155Vault.sol#L192)

	```solidity
	    function supportsInterface(bytes4 interfaceId)
	```


