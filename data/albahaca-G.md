# Gas Optimization For Taiko Contest


# SUMMARY
|      |  issue  |  instance  |
|------|---------|------------|
|[G‑01]|Use calldata instead of memory for function arguments that do not get mutated|70|
|[G‑02]|Use assembly to check for `address(0)`|55|
|[G‑03]|State variables that are used multiple times in a function should be cached in stack variables|14|
|[G‑04]|Can Make The Variable Outside The Loop To Save Gas|17|
|[G‑05]|Use assembly to write address storage values|17|
|[G‑06]|Use nested if statements instead of &&|20|
|[G‑07]|Multiple Address/id Mappings Can Be Combined Into A Single Mapping Of An Address/id To A Struct, Where Appropriate|5|
|[G‑08]|`internal` functions not called by the contract should be removed to save deployment gas|13|
|[G‑09]|Amounts should be checked for 0 before calling a transfer|6|
|[G‑10]|Avoid updating storage when the value hasn't changed|20|
|[G‑11]|Do not calculate constants|2|
|[G‑12]|State variables can be packed into fewer storage slots|2|
|[G‑13]|With assembly, .call (bool success) transfer can be done gas-optimized|1|
|[G‑14]|Use hardcode address instead address(this)|31|
|[G‑15]|Structs can be packed to use fewer storage slots|4|
|[G‑16]|use Mappings Instead of Arrays|1|
|[G‑17]|Use constants instead of type(uintx).max|4|
|[G‑18]|Duplicated require()/if() checks should be refactored to a modifier or function|3|
|[G‑19]|Not using the named return variables when a function returns, wastes deployment gas|10|
|[G‑20]|Using storage instead of `memory` for structs/arrays saves gas|2|
|[G‑21]|Multiple accesses of a mapping/array should use a local variable cache|45|
|[G‑22]|internal functions only called once can be inlined to save gas|23|
|[G‑23]|bytes constants are more eficient than string constans|5|
|[G‑24]|Use assembly to hash instead of solidity|28|
|[G‑25]|Stack variable used as a cheaper cache for a state variable is only used once|1|
|[G‑26]|Use assembly to emit an event|55|
|[G‑27]|Using a positive conditional flow to save a NOT opcode|2|
|[G‑28]|Avoid contract existence checks by using low level calls|25|
|[G‑29]|Use do while loops instead of for loops|5|
|[G‑30]|Splitting require() statements that use && saves gas|3|
|[G‑31]|Do not shrink Variables|2|
|[G‑32]|Constructors can be marked payable|3|
|[G‑33]|The result of function calls should be cached rather than re-calling the function|33|
|[G‑34]|Empty Blocks Should Be Removed Or Emit Something|4|
|[G‑35]|Use custom errors rather than revert()/require() strings to save gas|35|
|[G‑36]|State variables only set in the constructor should be declared immutable|2|
|[G‑37]|Caching global variables is more expensive than using the actual variable (use msg.sender instead of caching it)|2|
|[G‑38]|Use local variables for emitting|6|
|[G‑39]|Use selfbalance() instead of address(this).balance|6|
|[G‑40]|Private functions used once can be inlined|35|
|[G‑41]|State variable read in a loop|15|
|[G‑42]|Use struct dot notation to avoid memory allocation|4|
|[G‑43]|Use assembly in place of abi.decode to extract calldata values more efficiently|16|
|[G‑44]|Cache external calls outside of loop to avoid re-calling function on each iteration|6|
|[G‑45]|Structs can be modified to fit in fewer storage slots|1|
|[G‑46]|Use assembly to validate msg.sender|10|
|[G‑47]|Pre-increment and pre-decrement are cheaper thanĀ +1 ,-1|5|
|[G‑48]|Storage re-read via storage pointer|4|
|[G‑49]|Initializer can be marked payable|25|
|[G‑50]|Use inline assembly to access the chain ID|37|
|[G‑51]|Consider using OZ EnumerateSet in place of nested mappings|7|
|[G‑52]|Instead of counting down in for statements, count up|25|
|[G‑53]|require() or revert() statements that check input arguments should be at the top of the function|4|
|[G‑54]|Structs should group like types together to save gas|12|
|[G‑55]|`>=` costs less gas than `>`|1|
|[G‑56]|Usage of `uints`/`ints` smaller than 32 bytes (256 bits) incurs overhead|16|
|[G‑57]|Emit Used In Loop|3|
|[G‑58]|Require()/revert() Strings Longer Than 32 Bytes Cost Extra Gas|1|
|[G‑59]|Using `private` rather than `public` for constants, saves gas|2|
|[G‑60]|Functions guaranteed to revert when called by normal users can be marked `payable`|2|
|[G‑61]|Superfluous event fields|1|
|[G‑62]|Use assembly to perform efficient back-to-back calls|2|
|[G‑63]|Delete variables that you don't need|1|




## [G-01] Use calldata instead of memory for function arguments that do not get mutated

Mark data types as `calldata` instead of `memory` where possible. This makes it so that the data is not automatically loaded into memory. If the data passed into the function does not need to be changed (like updating values in an array), it can be passed in as `calldata`. The one exception to this is if the argument must later be passed into another function that takes an argument that specifies `memory` storage.


🔴 Affected code:
There are 70 instances of this issue:
```solidity
File: contracts/L1/gov/TaikoGovernor.sol
71              uint256[] memory _values,

72              string[] memory _signatures,

52              string memory _description

70              address[] memory _targets,

74              string memory _description

73              bytes[] memory _calldatas,

50              uint256[] memory _values,

51              bytes[] memory _calldatas,

49              address[] memory _targets,
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L49:49

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
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/IHook.sol#L15:15

```solidity
File: contracts/L1/libs/LibUtils.sol
54              TaikoData.Config memory _config,

25              TaikoData.Config memory _config,
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L25:25

```solidity
File: contracts/L1/libs/LibVerifying.sol
49              TaikoData.Config memory _config,
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L49:49

```solidity
File: contracts/L1/provers/Guardians.sol
54              address[] memory _newGuardians,
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L54

```solidity
File: contracts/L2/TaikoL2EIP1559Configurable.sol
26              Config memory _newConfig,
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L26:26

```solidity
File: contracts/automata-attestation/interfaces/ISigVerifyLib.sol
59              bytes memory tbs,

69              bytes memory signature,

78              bytes memory signature,

68              bytes memory tbs,

61              bytes memory publicKey

70              bytes memory publicKey

60              bytes memory signature,

50              bytes memory signature,

39              bytes memory tbs,

77              bytes memory tbs,

40              bytes memory signature,

79              bytes memory publicKey

41              PublicKey memory publicKey,

51              PublicKey memory publicKey,

49              bytes memory tbs,
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L49:49

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol
41              bytes memory pemChain,

75              bytes memory der,
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L75:75

```solidity
File: contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol
37              bytes memory pemChain,

45              bytes memory der,
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L45:45

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
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L56:56

```solidity
File: contracts/bridge/Bridge.sol
449         function hashMessage(Message memory _message) public pure returns (bytes32) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L449:449

```solidity
File: contracts/bridge/IBridge.sol
155         function hashMessage(Message memory _message) external pure returns (bytes32);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L155:155

```solidity
File: contracts/team/TimelockTokenPool.sol
168         function withdraw(address _to, bytes memory _sig) external {

135         function grant(address _recipient, Grant memory _grant) external onlyOwner {
```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L135:135

```solidity
File: contracts/tokenvault/BridgedERC1155.sol
43              string memory _symbol,

85              uint256[] memory _tokenIds,

86              uint256[] memory _amounts

44              string memory _name
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L44:44

```solidity
File: contracts/tokenvault/BridgedERC20.sol
59              string memory _name

58              string memory _symbol,
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L58:58

```solidity
File: contracts/tokenvault/BridgedERC721.sol
37              string memory _name

36              string memory _symbol,
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L36:36

```solidity
File: contracts/tokenvault/ERC1155Vault.sol
39          function sendToken(BridgeTransferOp memory _op)
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L39:39

```solidity
File: contracts/tokenvault/ERC721Vault.sol
26          function sendToken(BridgeTransferOp memory _op)
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L26:26

```solidity
File: contracts/verifiers/SgxVerifier.sol
172             TaikoData.Transition memory _tran,
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L172:172


## [G-02] Use assembly to check for `address(0)`

*Saves 6 gas per instance*

🔴 Affected code:
There are 55 instances of this issue:

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
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L234


## [G‑03] State variables that are used multiple times in a function should be cached in stack variables
When performing multiple operations on a state variable in a function, it is recommended to cache it first. Either multiple reads or multiple writes to a state variable can save gas by caching it on the stack. Caching of a state variable replaces each Gwarmaccess (100 gas) with a much cheaper stack read. Other less obvious fixes/optimizations include having local memory caches of state variable structs, or having local caches of state variable contracts/addresses. Saves 100 gas per instance.


🔴 Affected code:
There are 14 instances of this issue:

```solidity
File: contracts/L1/TaikoL1.sol
// @audit - in `TaikoL1::proposeBlock` function `state` storage variables that are used multiple times Lines : 67,69,70
67      (meta_, deposits_) = LibProposing.proposeBlock(state, config, this, _params, _txList);

// @audit - in `TaikoL1::proveBlock` function `state` storage variables that are used multiple times Lines : 94,96
94      uint8 maxBlocksToVerify = LibProving.proveBlock(state, config, this, meta, tran, proof);

// @audit - in `TaikoL1::getBlock` function `state` storage variables that are used multiple times Lines : 151,154
151   (blk_, slot) = LibUtils.getBlock(state, getConfig(), _blockId);

// @audit - in `TaikoL1::getStateVariables` function `state` storage variables that are used multiple times Lines : 181,182
181             a_ = state.slotA;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L181


```solidity
File: contracts/L2/TaikoL2.sol
// @audit - in `TaikoL2::_calc1559BaseFee` function `gasExcess` storage variables that are used multiple times Lines : 262,265
262     if (gasExcess > 0) {

// @audit - in `TaikoL2::_calc1559BaseFee` function `lastSyncedBlock` storage variables that are used multiple times Lines : 275,276
275    if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {
276         numL1Blocks = _l1BlockId - lastSyncedBlock;    
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L262

```solidity
File: contracts/common/AddressResolver.sol
// @audit - in `AddressResolver::_resolve` function `addressManager` storage variables that are used multiple times Lines : 81,83
81  if (addressManager == address(0)) revert RESOLVER_INVALID_MANAGER();
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L83:83

```solidity
File: contracts/team/TimelockTokenPool.sol
// @audit - in `TimelockTokenPool::_withdraw` function `sharedVault` storage variables that are used multiple times Lines : 219,220
219        IERC20(taikoToken).transferFrom(sharedVault, _to, amountToWithdraw);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L219

```solidity
File: contracts/team/airdrop/ERC20Airdrop.sol
// @audit - in `ERC20Airdrop::claimAndDelegate` function `token` storage variables that are used multiple times Lines : 63,71
63        IERC20(token).transferFrom(vault, user, amount);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L63:63

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol
// @audit - in `BridgedERC20Base::mint` function `migratingAddress` storage variables that are used multiple times Lines : 61,63
61   if (msg.sender == migratingAddress) {

// @audit - in `BridgedERC20Base::burn` function `migratingAddress` storage variables that are used multiple times Lines : 80,82
80   emit MigratedTo(migratingAddress, _account, _amount);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L80-L82

```solidity
File: contracts/verifiers/SgxVerifier.sol
// @audit - in `SgxVerifier::_addInstances` function `nextInstanceId` storage variables that are used multiple times Lines : 217,218,220
217  instances[nextInstanceId] = Instance(_instances[i], validSince);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L218


```solidity
File: contracts/L1/provers/Guardians.sol
88      guardianIds[guardian] = guardians.length;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L88:88



```solidity
File:  contracts/automata-attestation/AutomataDcapV3Attestation.sol
123  _checkLocalEnclaveReport = !_checkLocalEnclaveReport;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L123



## [G-04] Can Make The Variable Outside The Loop To Save Gas 
When you declare a variable inside a loop, Solidity creates a new instance of the variable for each iteration of the loop. This can lead to unnecessary gas costs, especially if the loop is executed frequently or iterates over a large number of elements.

By declaring the variable outside the loop, you can avoid the creation of multiple instances of the variable and reduce the gas cost of your contract. Here's an example:

```
contract MyContract {
    function sum(uint256[] memory values) public pure returns (uint256) {
        uint256 total = 0;
        
        for (uint256 i = 0; i < values.length; i++) {
            total += values[i];
        }
        
        return total;
    }
}
```

🔴 Affected code:
There are 17 instances of this issue:

```solidity
File:  contracts/automata-attestation/lib/PEMCertChainLib.sol
55    string memory input;

61     uint256 increment;

355         uint256 svnPtr = der.firstChildOf(svnParentPtr); // OID
            uint256 svnValuePtr = der.nextSiblingOf(svnPtr); // value
            bytes memory svnValueBytes = der.bytesAt(svnValuePtr);
            uint16 svnValue = svnValueBytes.length < 2
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#55


```solidity
File:  contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol
154         uint256 digits = uint256(uint8(bytes1(encoded[i])));
            uint256 upperDigit = digits / 16;
            uint256 lowerDigit = digits % 16;

            uint256 acc = lowerDigit * (16 ** (2 * i));
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L154-L158


```solidity
File:  contracts/automata-attestation/utils/BytesUtils.sol
334  bytes1 char = self[off + i];
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L344


```solidity
File:  contracts/bridge/Bridge.sol
91   bytes32 msgHash = _msgHashes[i];
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L91


```solidity
File:  contracts/L1/libs/LibDepositing.sol
87   uint256 data = _state.ethDeposits[j % _config.ethDepositRingBufferSize];
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L87


```solidity
File:  contracts/L1/provers/Guardians.sol
81  address guardian = _newGuardians[i];
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L81



```solidity
File:  contracts/L2/TaikoL2.sol
335  uint256 j = _blockId - i - 1;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L335


```solidity
File:  contracts/signal/SignalService.sol
107            bytes32 signalRoot = _verifyHopProof(chainId, app, signal, value, hop, signalService);
            bool isLastHop = i == hopProofs.length - 1;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L107-L108



```solidity
File:  contracts/verifiers/SgxVerifier.sol
105  uint256 idx = _ids[i];
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L105


## [G-05] Use assembly to write address storage values
By using assembly to write to address storage values, you can bypass some of these operations and lower the gas cost of writing to storage. Assembly code allows you to directly access the Ethereum Virtual Machine (EVM) and perform low-level operations that are not possible in Solidity.

example of using assembly to write to address storage values:
```
contract MyContract {
    address private myAddress;
    
    function setAddressUsingAssembly(address newAddress) public {
        assembly {
            sstore(0, newAddress)
        }
    }
}
```


🔴 Affected code:
There are 17 instances of this issue:

```solidity
File:  contracts/automata-attestation/AutomataDcapV3Attestation.sol
57  owner = msg.sender;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L57


```solidity
File:  contracts/automata-attestation/utils/SigVerifyLib.sol
21  ES256VERIFIER = es256Verifier;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L21


```solidity
File:  contracts/common/AddressResolver.sol
62   addressManager = _addressManager;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L62


```solidity
File:  contracts/team/TimelockTokenPool.sol
122   taikoToken = _taikoToken;

125   costToken = _costToken;

128   sharedVault = _sharedVault;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L122


```solidity
File:  contracts/team/airdrop/ERC20Airdrop.sol
41      token = _token;
        vault = _vault;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L41-L42


```solidity
File:  contracts/team/airdrop/ERC20Airdrop2.sol
69        token = _token;
        vault = _vault;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L69-L70


```solidity
File:  contracts/team/airdrop/ERC721Airdrop.sol
39        token = _token;
          vault = _vault;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L39-L40



```solidity
File:  contracts/tokenvault/BridgedERC20.sol
73        srcToken = _srcToken;

81  snapshooter = _snapshooter;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L73

```solidity
File:  contracts/tokenvault/BridgedERC20Base.sol
49   migratingAddress = _migratingAddress;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L49



```solidity
File:  contracts/tokenvault/BridgedERC721.sol
47  srcToken = _srcToken;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L47



```solidity
File:  contracts/tokenvault/BridgedERC1155.sol
56  srcToken = _srcToken;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L56



## [G-06] Use nested if statements instead of &&
If the if statement has a logical AND and is not followed by an else statement, it can be replaced with 2 if statements.

```
contract NestedIfTest {

    //Execution cost: 22334 gas
    function funcBad(uint256 input) public pure returns (string memory) { 
       if (input<10 && input>0 && input!=6){ 
           return "If condition passed";
       } 

   }

    //Execution cost: 22294 gas
    function funcGood(uint256 input) public pure returns (string memory) { 
    if (input<10) { 
        if (input>0){
            if (input!=6){
                return "If condition passed";
            }
        }
    }
   }
}
   
```

🔴 Affected code:
There are 20 instances of this issue:
```solidity
File: contracts/L1/hooks/AssignmentHook.sol
120             if (input.tip != 0 && block.coinbase != address(0)) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L120:120

```solidity
File: contracts/L1/libs/LibProposing.sol
108             if (params.parentMetaHash != 0 && parentMetaHash != params.parentMetaHash) {

164                     if (_config.blobReuseEnabled && params.cacheBlobForReuse) {

310                 if (proposerOne != address(0) && msg.sender != proposerOne) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L310


```solidity
File: contracts/L2/TaikoL2.sol
117                 _l1BlockHash == 0 || _l1StateRoot == 0 || _l1BlockId == 0
118                     || (block.number != 1 && _parentGasUsed == 0)

141             if (!skipFeeCheck() && block.basefee != basefee) {

275                 if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L275:275

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol
220                 if (pceSvnIsHigherOrGreater && cpuSvnsAreHigherOrGreater) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L220:220

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol
134                 if (
135                     (notBeforeTag != 0x17 && notBeforeTag == 0x18)
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L134:135

```solidity
File: contracts/bridge/Bridge.sol
250             if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) {

260                 if (_message.gasLimit == 0 && msg.sender != _message.destOwner) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L490:493

```solidity
File: contracts/common/AddressResolver.sol
85              if (!_allowZeroAddress && addr_ == address(0)) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L85:85

```solidity
File: contracts/common/EssentialContract.sol
42              if (msg.sender != owner() && msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L42:42

```solidity
File: contracts/signal/SignalService.sol
285             if (cacheStateRoot && _isFullProof && !_isLastHop) {

293             if (cacheSignalRoot && (_isFullProof || !_isLastHop)) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L293:293

```solidity
File: contracts/team/TimelockTokenPool.sol
277                 if (_cliff > 0 && _cliff <= _start) revert INVALID_GRANT();
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L277:277

```solidity
File: contracts/thirdparty/optimism/rlp/RLPWriter.sol
14              if (_in.length == 1 && uint8(_in[0]) < 128) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L14:14

```solidity
File: contracts/tokenvault/BridgedERC20.sol
38              if (msg.sender != owner() && msg.sender != snapshooter) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L38:38

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol
45              if (_migratingAddress == migratingAddress && _migratingInbound == migratingInbound) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L45:45


## [G-07] Multiple Address/id Mappings Can Be Combined Into A Single Mapping Of An Address/id To A Struct, Where Appropriate
Saves a storage slot for the mapping. Depending on the circumstances and sizes of types, can avoid a Gsset (20000 gas) per mapping combined. Reads and subsequent writes can also be cheaper when a function requires both values and they both fit in the same storage slot. Finally, if both fields are accessed in the same function, can save ~42 gas per access due to [not having to recalculate the key’s keccak256 hash](https://gist.github.com/IllIllI000/ec23a57daa30a8f8ca8b9681c8ccefb0) (Gkeccak256 - 30 gas) and that calculation’s associated stack operations.

🔴 Affected code:
There are 5 instances of this issue:

```solidity
File:  contracts/automata-attestation/AutomataDcapV3Attestation.sol
39    mapping(bytes32 enclave => bool trusted) private _trustedUserMrEnclave;
40    mapping(bytes32 signer => bool trusted) private _trustedUserMrSigner;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L39-L40

- `messageStatus` and `proofReceipt`.
```solidity
File: contracts/bridge/Bridge.sol
35          mapping(bytes32 msgHash => Status status) public messageStatus;
36      
37          /// @dev Slots 3, 4, and 5.
38          Context private __ctx;
39      
40          /// @notice Mapping to store banned addresses.
41          /// @dev Slot 6.
42          mapping(address addr => bool banned) public addressBanned;
43      
44          /// @notice Mapping to store the proof receipt of a message from its hash.
45          /// @dev Slot 7.
46          mapping(bytes32 msgHash => ProofReceipt receipt) public proofReceipt;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L35-L46


```solidity
File: contracts/L1/TaikoData.sol
181             mapping(uint64 blockId_mod_blockRingBufferSize => Block blk) blocks;
182             // Indexing to transition ids (ring buffer not possible)
183             mapping(uint64 blockId => mapping(bytes32 parentHash => uint32 transitionId)) transitionIds;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L181-L183


```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol
22          mapping(address addr => uint256 amountClaimed) public claimedAmount;
23      
24          /// @notice Represents the already withdrawn amount.
25          mapping(address addr => uint256 amountWithdrawn) public withdrawnAmount;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L22-L25

- `bridgedToCanonical` and `btokenBlacklist`.
```solidity
File:  contracts/tokenvault/ERC20Vault.sol
    mapping(address btoken => CanonicalERC20 canonical) public bridgedToCanonical;

    /// @notice Mappings from canonical tokens to their bridged tokens. Also storing
    /// the chainId for tokens across other chains aside from Ethereum.
    mapping(uint256 chainId => mapping(address ctoken => address btoken)) public canonicalToBridged;

    /// @notice Mappings from bridged tokens to their blacklist status.
    mapping(address btoken => bool blacklisted) public btokenBlacklist;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L45-L52


## [G-08] `internal` functions not called by the contract should be removed to save deployment gas

🔴 Affected code:
There are 13 instances of this issue:

```solidity
File: contracts/L1/TaikoToken.sol
83  function _beforeTokenTransfer(
        address _from,
        address _to,
        uint256 _amount
    )
        internal
        override(ERC20Upgradeable, ERC20SnapshotUpgradeable)
    {
        super._beforeTokenTransfer(_from, _to, _amount);
    }

94   function _afterTokenTransfer(
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
127   function _execute(
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

140   function _cancel(
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

153   function _executor()
        internal
        view
        override(GovernorUpgradeable, GovernorTimelockControlUpgradeable)
        returns (address)
    {
        return super._executor();
    }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L153-L160

```solidity
File: contracts/common/AddressManager.sol
59   function _authorizePause(address) internal pure override {
        revert AM_UNSUPPORTED();
    }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L58:60

```solidity
File: contracts/signal/SignalService.sol
231   function _authorizePause(address) internal pure override {
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

## [G-09] Amounts should be checked for 0 before calling a transfer
Checking non-zero transfer values can avoid an expensive external call and save gas.

🔴 Affected code:
There are 6 instances of this issue:

```solidity
File:  contracts/L1/TaikoToken.sol
62  return super.transfer(_to, _amount);

80  return super.transferFrom(_from, _to, _amount);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L62-L80


```solidity
File:  contracts/team/TimelockTokenPool.sol
219        IERC20(taikoToken).transferFrom(sharedVault, _to, amountToWithdraw);
220        IERC20(costToken).safeTransferFrom(_recipient, sharedVault, costToWithdraw);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L219-L220


```solidity
File:  contracts/team/airdrop/ERC20Airdrop.sol
63  IERC20(token).transferFrom(vault, user, amount);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L63


```solidity
File:  contracts/tokenvault/adapters/USDCAdapter.sol
48  usdc.transferFrom(_from, address(this), _amount);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L48


## [G-10] Avoid updating storage when the value hasn't changed
If the old value is equal to the new value, not re-storing the value will avoid a Gsreset (**2900 gas**), potentially at the expense of a Gcoldsload (**2100 gas**) or a Gwarmaccess (**100 gas**).


🔴 Affected code:
There are 20 instances of this issue:

```solidity
File: contracts/L1/provers/Guardians.sol
94   minGuardians = _minGuardians;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L94

```solidity
File: contracts/L2/TaikoL2.sol
96   gasExcess = _gasExcess;

155   publicInputHash = publicInputHashNew;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L96



```solidity
File: contracts/L2/TaikoL2EIP1559Configurable.sol
36         customConfig = _newConfig;
37        gasExcess = _newGasExcess;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L36-L37

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol
119   qeIdentity = qeIdentityInput;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L119

- also in these function
```solidity
File: contracts/common/EssentialContract.sol
69          function pause() public virtual whenNotPaused {

119         function _storeReentryLock(uint8 _reentry) internal virtual {

78          function unpause() public virtual whenPaused {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L78:78

```solidity
File: contracts/team/TimelockTokenPool.sol
111         function init(
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L111:111

```solidity
File: contracts/team/airdrop/ERC20Airdrop.sol
27          function init(
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L27:27

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol
54          function init(
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L54:54

```solidity
File: contracts/team/airdrop/ERC721Airdrop.sol
25          function init(
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L25:25

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol
90          function _setConfig(uint64 _claimStart, uint64 _claimEnd, bytes32 _merkleRoot) private {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L90:90

```solidity
File: contracts/tokenvault/BridgedERC1155.sol
38          function init(
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L38:38

```solidity
File: contracts/tokenvault/BridgedERC20.sol
52          function init(

80          function setSnapshoter(address _snapshooter) external onlyOwner {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L80:80

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol
36          function changeMigrationStatus(
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L36:36

```solidity
File: contracts/tokenvault/BridgedERC721.sol
31          function init(
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L31:31

```solidity
File: contracts/tokenvault/adapters/USDCAdapter.sol
38          function init(address _owner, address _addressManager, IUSDC _usdc) external initializer {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L38:38



## [G-11] Do not calculate constants
Due to how constant variables are implemented (replacements at compile-time), an expression assigned to a constant variable is recomputed each time that the variable is used, which wastes some gas.

🔴 Affected code:
There are 2 instances of this issue:

```solidity
File: contracts/L1/libs/LibProposing.sol
21          uint256 public constant MAX_BYTES_PER_BLOB = 4096 * 32;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L21:21

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol
24          uint256 internal constant BRANCH_NODE_LENGTH = TREE_RADIX + 1;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L24:24





## [G-12] State variables can be packed into fewer storage slots

If variables occupying the same slot are both written in the same function or by the constructor, avoids a separate Gsset (20000 gas). Reads of the variables can also be cheaper

🔴 Affected code:
There are 2 instances of this issue:

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol
22      contract AutomataDcapV3Attestation is IAttestation {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L22:22

- with this change you can save one storage slot
```diff
    bool private _checkLocalEnclaveReport;
+   address public owner;
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

-   address public owner;
```    

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol
12      contract ERC20Airdrop2 is MerkleClaimable {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L12:12

- with this change you can save one storage slot
```diff
contract ERC20Airdrop2 is MerkleClaimable {
    using LibMath for uint256;

    /// @notice The address of the token contract.
    address public token;

    /// @notice The address of the vault contract.
    address public vault;
+   uint64 public withdrawalWindow;
    /// @notice Represents the token amount for which the user has claimed.
    mapping(address addr => uint256 amountClaimed) public claimedAmount;

    /// @notice Represents the already withdrawn amount.
    mapping(address addr => uint256 amountWithdrawn) public withdrawnAmount;

    /// @notice Length of the withdrawal window.
-   uint64 public withdrawalWindow;
```


## [G-13] With assembly, .call (bool success) transfer can be done gas-optimized
return data (bool success,) has to be stored due to EVM architecture, but in a usage like below, ‘out’ and ‘outsize’ values are given (0,0), this storage disappears and gas optimization is provided.
https://code4rena.com/reports/2023-01-biconomy#g-01-with-assembly-call-bool-success-transfer-can-be-done-gas-optimized

🔴 Affected code:
There are 1 instances of this issue:

```solidity
File: contracts/L2/CrossChainOwned.sol
50              (bool success,) = address(this).call(txdata);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L50


## [G-14] Use hardcode address instead address(this)
it can be more gas-efficient to use a hardcoded address instead of the address(this) expression, especially if you need to use the same address multiple times in your contract.

The reason for this is that using address(this) requires an additional EXTCODESIZE operation to retrieve the contract's address from its bytecode, which can increase the gas cost of your contract. By pre-calculating and using a hardcoded address, you can avoid this additional operation and reduce the overall gas cost of your contract.

Here's an example of how you can use a hardcoded address instead of address(this):

```
contract MyContract {
    address public immutable myAddress = 0x1234567890123456789012345678901234567890;
    #L
    function doSomething() public {
        // Use myAddress instead of address(this)
        require(msg.sender == myAddress, "Caller is not authorized");
        
        // Do something
    }
}
```
In the above example, we have a contract MyContract with a public address variable myAddress. Instead of using address(this) to retrieve the contract's address, we have pre-calculated and hardcoded the address in the variable. This can help to reduce the gas cost of our contract and make our code more efficient.

[References](https://book.getfoundry.sh/reference/forge-std/compute-create-address)

🔴 Affected code:
There are 31 instances of this issue:

```solidity
File:  contracts/bridge/Bridge.sol
174  if (!ISignalService(signalService).isSignalSent(address(this), msgHash)) {

196  _storeContext(msgHash, address(this), _message.srcChainId);   

270    _message.to == address(0) || _message.to == address(this)

343      _app: address(this),

486  assert(_message.from != address(this));
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L174


```solidity
File:  contracts/L1/TaikoToken.sol
61   if (_to == address(this)) revert TKO_INVALID_ADDR();

79   if (_to == address(this)) revert TKO_INVALID_ADDR();
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L61


```solidity
File:  contracts/L1/hooks/AssignmentHook.sol
125  if (address(this).balance > 0) {

1265 taikoL1Address.sendEther(address(this).balance);

151  address(this),
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L125


```solidity
File:  contracts/L1/libs/LibProposing.sol
238  uint256 tkoBalance = tko.balanceOf(address(this));

253  IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }(

260  if (address(this).balance != 0) {

261  msg.sender.sendEther(address(this).balance);

268  if (tko.balanceOf(address(this)) != tkoBalance + _config.livenessBond) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L238


```solidity
File:  contracts/L1/libs/LibProving.sol
242  tko.transferFrom(msg.sender, address(this), tier.contestBond);

384  _tko.transferFrom(msg.sender, address(this), _tier.validityBond - reward);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L242


```solidity
File:  contracts/L2/TaikoL2.sol
174  _to.sendEther(address(this).balance);

176  IERC20(_token).safeTransfer(_to, IERC20(_token).balanceOf(address(this)));
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L174


```solidity
File:  contracts/signal/SignalService.sol
112   signalService = address(this);

131  if (value == 0 || value != _loadSignalValue(address(this), signal)) {

149  return _loadSignalValue(address(this), signal) == _chainData;

171  chainData_ = _loadSignalValue(address(this), signal);

245  _sendSignal(address(this), signal_, _chainData);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L112



```solidity
File:  contracts/tokenvault/ERC20Vault.sol
267   if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

378         uint256 _balance = t.balanceOf(address(this));
            t.safeTransferFrom({ from: msg.sender, to: address(this), value: _amount });
            balanceChange_ = t.balanceOf(address(this)) - _balance;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L267


```solidity
File:  contracts/tokenvault/ERC721Vault.sol
91  if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

171 IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);

211 t.safeTransferFrom(_user, address(this), _op.tokenIds[i]);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L91

## [G-15] Structs can be packed to use fewer storage slots
The EVM works with 32 byte words. Variables less than 32 bytes can be declared next to each other in storage and this will pack the values together into a single 32 byte storage slot (if values combined are <= 32 bytes). If the variables packed together are retrieved together in functions (more likely with structs) we will effectively save ~2000 gas with every subsequent SLOAD for that storage slot. This is due to us incurring a Gwarmaccess (100 gas) versus a Gcoldsload (2100 gas).

🔴 Affected code:
There are 4 instances of this issue:

```solidity
File: contracts/L1/TaikoData.sol
10          struct Config {
11              // ---------------------------------------------------------------------
12              // Group 1: General configs
13              // ---------------------------------------------------------------------
14              // The chain ID of the network where Taiko contracts are deployed.
15              uint64 chainId;
16              // ---------------------------------------------------------------------
17              // Group 2: Block level configs
18              // ---------------------------------------------------------------------
19              // The maximum number of proposals allowed in a single block.
20              uint64 blockMaxProposals;
21              // Size of the block ring buffer, allowing extra space for proposals.
22              uint64 blockRingBufferSize;
23              // The maximum number of verifications allowed when a block is proposed.
24              uint64 maxBlocksToVerifyPerProposal;
25              // The maximum gas limit allowed for a block.
26              uint32 blockMaxGasLimit;
27              // The maximum allowed bytes for the proposed transaction list calldata.
28              uint24 blockMaxTxListBytes;
29              // The max period in seconds that a blob can be reused for DA.
30              uint24 blobExpiry;
31              // True if EIP-4844 is enabled for DA
32              bool blobAllowedForDA;
33              // True if blob can be reused
34              bool blobReuseEnabled;
35              // ---------------------------------------------------------------------
36              // Group 3: Proof related configs
37              // ---------------------------------------------------------------------
38              // The amount of Taiko token as a prover liveness bond
39              uint96 livenessBond;
40              // ---------------------------------------------------------------------
41              // Group 4: ETH deposit related configs
42              // ---------------------------------------------------------------------
43              // The size of the ETH deposit ring buffer.
44              uint256 ethDepositRingBufferSize;
45              // The minimum number of ETH deposits allowed per block.
46              uint64 ethDepositMinCountPerBlock;
47              // The maximum number of ETH deposits allowed per block.
48              uint64 ethDepositMaxCountPerBlock;
49              // The minimum amount of ETH required for a deposit.
50              uint96 ethDepositMinAmount;
51              // The maximum amount of ETH allowed for a deposit.
52              uint96 ethDepositMaxAmount;
53              // The gas cost for processing an ETH deposit.
54              uint256 ethDepositGas;
55              // The maximum fee allowed for an ETH deposit.
56              uint256 ethDepositMaxFee;
57              // The max number of L2 blocks that can stay unsynced on L1 (a value of zero disables
58              // syncing)
59              uint8 blockSyncThreshold;
60          }

78          struct BlockParams {
79              address assignedProver;
80              address coinbase;
81              bytes32 extraData;
82              bytes32 blobHash;
83              uint24 txListByteOffset;
84              uint24 txListByteSize;
85              bool cacheBlobForReuse;
86              bytes32 parentMetaHash;
87              HookCall[] hookCalls;
88          }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L78:88

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol
17          struct EnclaveReport {
18              bytes16 cpuSvn;
19              bytes4 miscSelect;
20              bytes28 reserved1;
21              bytes16 attributes;
22              bytes32 mrEnclave;
23              bytes32 reserved2;
24              bytes32 mrSigner;
25              bytes reserved3; // 96 bytes
26              uint16 isvProdId;
27              uint16 isvSvn;
28              bytes reserved4; // 60 bytes
29              bytes reportData; // 64 bytes - For QEReports, this contains the hash of the concatenation
30                  // of attestation key and QEAuthData
31          }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L17:31

```solidity
File:  contracts/bridge/IBridge.sol
17    struct Message {
        // Message ID whose value is automatically assigned.
        uint128 id;
        // The address, EOA or contract, that interacts with this bridge.
        // The value is automatically assigned.
        address from;
        // Source chain ID whose value is automatically assigned.
        uint64 srcChainId;
        // Destination chain ID where the `to` address lives.
        uint64 destChainId;
        // The owner of the message on the source chain.
        address srcOwner;
        // The owner of the message on the destination chain.
        address destOwner;
        // The destination address on the destination chain.
        address to;
        // Alternate address to send any refund on the destination chain.
        // If blank, defaults to destOwner.
        address refundTo;
        // value to invoke on the destination chain.
        uint256 value;
        // Processing fee for the relayer. Zero if owner will process themself.
        uint256 fee;
        // gasLimit to invoke on the destination chain.
        uint256 gasLimit;
        // callData to invoke on the destination chain.
        bytes data;
        // Optional memo.
        string memo;
    }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L17-L46

## [G-16] use Mappings Instead of Arrays
Arrays are useful when you need to maintain an ordered list of data that can be iterated over, but they have a higher gas cost for read and write operations, especially when the size of the array is large. This is because Solidity needs to iterate over the entire array to perform certain operations, such as finding a specific element or deleting an element.

Mappings, on the other hand, are useful when you need to store and access data based on a key, rather than an index. Mappings have a lower gas cost for read and write operations, especially when the size of the mapping is large, since Solidity can perform these operations based on the key directly, without needing to iterate over the entire data structure.


🔴 Affected code:
There are 1 instances of this issue:

```solidity
File:  contracts/L1/provers/Guardians.sol
23  address[] public guardians;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L23


## [G-17] Use constants instead of type(uintx).max
Using constants instead of type(uintx).max can save gas in some cases because constants are precomputed at compile-time and can be reused throughout the code, whereas type(uintx).max requires computation at runtime

🔴 Affected code:
There are 4 instances of this issue:

```solidity
File:  contracts/L1/libs/LibVerifying.sol
260  || _config.ethDepositMaxAmount > type(uint96).max || _config.ethDepositGas == 0

262  || _config.ethDepositMaxFee > type(uint96).max / _config.ethDepositMaxCountPerBlock
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L260-L262



```solidity
File:  contracts/L2/TaikoL2.sol
82  if (block.chainid <= 1 || block.chainid > type(uint64).max) {

284 gasExcess_ = uint64(excess.min(type(uint64).max));    
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L82


## [G-18] Duplicated require()/if() checks should be refactored to a modifier or function
sing modifiers or functions can make your code more gas-efficient by reducing the overall number of operations that need to be executed. For example, if you have a complex validation check that involves multiple operations, and you refactor it into a function, then the function can be executed with a single opcode, rather than having to execute each operation separately in multiple locations.

Recommendation
You can consider adding a modifier like below
```
 modifer check (address checkToAddress) {    
     require(checkToAddress != address(0) && checkToAddress != SENTINEL_MODULES, "BSA101");  
      _; 
 }
```

🔴 Affected code:
There are 3 instances of this issue:

```solidity
File:  contracts/automata-attestation/utils/Asn1Decode.sol
// @audit alos in line 180
57  require(der[ptr.ixs()] == 0x03, "Not type BIT STRING");

// @audit alos in line 155
142 require(der[ptr.ixs()] == 0x02, "Not type INTEGER");

// @audit alos in line 156
143    require(der[ptr.ixf()] & 0x80 == 0, "Not positive");
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L57



## [G-19] Not using the named return variables when a function returns, wastes deployment gas
When a function returns multiple values without named return variables, it creates a temporary variable to hold the returned values, which can increase the deployment gas cost

🔴 Affected code:
There are 10 instances of this issue:

```solidity
File: contracts/L1/libs/LibProving.sol
100    returns (uint8 maxBlocksToVerify_)
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L100


```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol
130             returns (bool valid)
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L130

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol
219             returns (bool success, bytes memory extracted, uint256 endIndex)
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L219:219

```solidity
File: contracts/automata-attestation/utils/BytesUtils.sol
188         function readUint8(bytes memory self, uint256 idx) internal pure returns (uint8 ret) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L188:188

```solidity
File: contracts/automata-attestation/utils/SigVerifyLib.sol
120             returns (bool sigValid)
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L120:120

```solidity
File: contracts/bridge/Bridge.sol
421             returns (uint256 invocationDelay_, uint256 invocationExtraDelay_)
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L421:421

```solidity
File: contracts/common/AddressResolver.sol
37              returns (address payable)

51              returns (address payable)
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L51:51

```solidity
File: contracts/thirdparty/optimism/rlp/RLPReader.sol
147             returns (uint256 offset_, uint256 length_, RLPItemType type_)
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L147:147

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol
241             returns (uint256 shared_)
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L241:241




## [G-20] Using storage instead of `memory` for structs/arrays saves gas
When fetching data from a storage location, assigning the data to a memory variable causes all fields of the struct/array to be read from storage, which incurs a Gcoldsload (2100 gas) for each field of the struct/array. If the fields are read from the new memory variable, they incur an additional MLOAD rather than a cheap stack read. Instead of declearing the variable with the memory keyword, declaring the variable with the storage keyword and caching any fields that need to be re-read in stack variables, will be much cheaper, only incuring the Gcoldsload for the fields actually read. The only time it makes sense to read the whole struct/array into a memory variable, is if the full struct/array is being returned by the function, is being passed to a function that requires memory, or if the array/struct is being read from another memory array/struct


🔴 Affected code:
There are 2 instances of this issue:

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol
180    EnclaveIdStruct.EnclaveId memory enclaveId = qeIdentity;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L180

```solidity
File: contracts/tokenvault/ERC20Vault.sol
171     CanonicalERC20 memory ctoken = bridgedToCanonical[btokenOld_];
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L171





## [G‑21] Multiple accesses of a mapping/array should use a local variable cache
The instances below point to the second+ access of a value inside a mapping/array, within a function. Caching a mapping’s value in a local storage or calldata variable when the value is accessed multiple times, saves ~42 gas per access due to not having to recalculate the key’s keccak256 hash (Gkeccak256 - 30 gas) and that calculation’s associated stack operations. Caching an array’s struct avoids recalculating the array offsets into memory/calldata.

🔴 Affected code:
There are 45 instances of this issue:

```solidity
File: contracts/L1/hooks/AssignmentHook.sol
173      if (_tierFees[i].tier == _tierId) return _tierFees[i].fee;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L173:173

```solidity
File: contracts/L1/libs/LibDepositing.sol
101     deposits_[i].amount -= _fee;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L101:101

```solidity
File: contracts/L1/libs/LibProposing.sol
257    prevHook = params.hookCalls[i].hook;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L257:257

```solidity
File: contracts/L1/libs/LibProving.sol
345      ts_ = _state.transitions[slot][tid_];
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L345:345

```solidity
File: contracts/L1/libs/LibVerifying.sol
130       blk = _state.blocks[slot];

140       TaikoData.TransitionState storage ts = _state.transitions[slot][tid];
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L140:140

```solidity
File: contracts/L1/provers/Guardians.sol
88     guardianIds[guardian] = guardians.length;

119    uint256 _approval = _approvals[version][_hash];
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L119:119

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol
84     _serialNumIsRevoked[index][serialNumBatch[i]] = true;

84     _serialNumIsRevoked[index][serialNumBatch[i]] = true;

99     delete _serialNumIsRevoked[index][serialNumBatch[i]];

99     delete _serialNumIsRevoked[index][serialNumBatch[i]];

286    certs[i].tbsCertificate, certs[i].signature, issuer.pubKey

271    certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.PCK)][certs[i]

272    .serialNumber];

472    parsedQuoteCerts[0].pubKey,
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L472:472

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol
282   quoteCerts[i] = Base64.decode(string(quoteCerts[i]));
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L282:282

```solidity
File: contracts/automata-attestation/utils/Asn1Decode.sol
143    require(der[ptr.ixf()] & 0x80 == 0, "Not positive");

158    if (der[ptr.ixf()] == 0) {

182    require(der[ptr.ixf()] == 0x00, "ixf Not 0");
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L182:182

```solidity
File: contracts/automata-attestation/utils/X509DateUtils.sol
21   yrs += (uint8(x509Time[0]) - 48) * 1000 + (uint8(x509Time[1]) - 48) * 100;
```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L21:21

```solidity
File: contracts/bridge/Bridge.sol
110   addressBanned[_addr] = _ban;

191   messageStatus[msgHash] = Status.RECALLED;

190   delete proofReceipt[msgHash];

264   delete proofReceipt[msgHash];

518   messageStatus[_msgHash] = _status;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L518:518

```solidity
File: contracts/common/AddressManager.sol
49    __addresses[_chainId][_name] = _newAddress;
```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L49:49

```solidity
File: contracts/signal/SignalService.sol
58    isAuthorized[_addr] = _authorize;

248   topBlockId[_chainId][_kind] = _blockId;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L248:248

```solidity
File: contracts/team/TimelockTokenPool.sol
142   recipients[_recipient].grant = _grant;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L142:142

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol
73   isClaimed[hash] = true;
```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L73:73

```solidity
File: contracts/thirdparty/optimism/rlp/RLPWriter.sol
45   out_[0] = bytes1(uint8(lenLen) + uint8(_offset) + 55);
```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L45:45

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol
188    currentNodeID = _getNodeID(currentNode.decoded[1]);

209    proof_[i] = TrieNode({ encoded: _proof[i], decoded: RLPReader.readList(_proof[i]) });
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L209:209

```solidity
File: contracts/tokenvault/ERC1155Vault.sol
250   ctoken_ = bridgedToCanonical[_op.token];

274    amount: _op.amounts[i],
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L274:274

```solidity
File: contracts/tokenvault/ERC20Vault.sol
188    bridgedToCanonical[_btokenNew] = _ctoken;

189    canonicalToBridged[_ctoken.chainId][_ctoken.addr] = _btokenNew;

359    ctoken_ = bridgedToCanonical[_token];
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L359:359

```solidity
File: contracts/tokenvault/ERC721Vault.sol
176     BridgedERC721(token_).mint(_to, _tokenIds[i]);

196    ctoken_ = bridgedToCanonical[_op.token];

211    t.safeTransferFrom(_user, address(this), _op.tokenIds[i]);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L211:211

```solidity
File: contracts/verifiers/SgxVerifier.sol
111    delete instances[idx];

213    addressRegistered[_instances[i]] = true;

220    emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);

237    && block.timestamp <= instances[id].validSince + INSTANCE_EXPIRY;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L237:237


## [G‑22] internal functions only called once can be inlined to save gas
Not inlining costs 20 to 40 gas because of two extra JUMP instructions and additional stack operations needed for function calls.

🔴 Affected code:
There are 23 instances of this issue:


```solidity
File: contracts/thirdparty/optimism/Bytes.sol
91          function slice(bytes memory _bytes, uint256 _start) internal pure returns (bytes memory) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L91:91

```solidity
File: contracts/thirdparty/optimism/rlp/RLPReader.sol
102         function readList(bytes memory _in) internal pure returns (RLPItem[] memory out_) {

128         function readBytes(bytes memory _in) internal pure returns (bytes memory out_) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L128:128

```solidity
File: contracts/thirdparty/optimism/rlp/RLPWriter.sol
13          function writeBytes(bytes memory _in) internal pure returns (bytes memory out_) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L13:13

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
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L115:115

```solidity
File: contracts/L1/libs/LibDepositing.sol
122         function canDepositEthToL2(
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L122:122

```solidity
File: contracts/L1/libs/LibProposing.sol
287         function isBlobReusable(
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L287:287

```solidity
File: contracts/L1/libs/LibUtils.sol
70          function getTransitionId(
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L70:70

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol
126         function _attestationTcbIsValid(TCBInfoStruct.TCBStatus status)
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L126:126

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol
267         function parseCerificationChainBytes(
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L267:267

```solidity
File: contracts/automata-attestation/utils/BytesUtils.sol
56          function compare(
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L56:56

```solidity
File: contracts/automata-attestation/utils/RsaVerify.sol
43          function pkcs1Sha256(

212         function pkcs1Sha1(
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L212:212

```solidity
File: contracts/automata-attestation/utils/X509DateUtils.sol
34          function toUnixTimestamp(
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L34:34

```solidity
File: contracts/common/EssentialContract.sol
109         function __Essential_init(address _owner) internal virtual {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L109:109

```solidity
File: contracts/libs/LibAddress.sol
42          function sendEther(address _to, uint256 _amount) internal {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L42:42

```solidity
File: contracts/signal/SignalService.sol
206         function _verifyHopProof(
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L206:206

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol
77          function _verifyMerkleProof(
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L77:77


```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol
68          function get(
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L68:68

```solidity
File: contracts/tokenvault/BridgedERC20.sol
163         function _mint(

173         function _burn(
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L173:173



## [G-23] bytes constants are more eficient than string constans
If the data can fit in 32 bytes, the bytes32 data type can be used instead of bytes or strings, as it is less robust in terms of robustness.


🔴 Affected code:
There are 5 instances of this issue:

```solidity
File:  contracts/automata-attestation/lib/PEMCertChainLib.sol
17  string internal constant HEADER = "-----BEGIN CERTIFICATE-----";
    string internal constant FOOTER = "-----END CERTIFICATE-----";
    uint256 internal constant HEADER_LENGTH = 27;
    uint256 internal constant FOOTER_LENGTH = 25;

    string internal constant PCK_COMMON_NAME = "Intel SGX PCK Certificate";
    string internal constant PLATFORM_ISSUER_NAME = "Intel SGX PCK Platform CA";
    string internal constant PROCESSOR_ISSUER_NAME = "Intel SGX PCK Processor CA";
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L17-L24


## [G-24] Use assembly to hash instead of solidity
```
function solidityHash(uint256 a, uint256 b) public view {
   //unoptimized
   keccak256(abi.encodePacked(a, b));
}
```
Gas: 313
```
function assemblyHash(uint256 a, uint256 b) public view {
   //optimized
   assembly {
       mstore(0x00, a)
       mstore(0x20, b)
       let hashedVal := keccak256(0x00, 0x40)
   }
}
```
Gas: 231

🔴 Affected code:
There are 28 instances of this issue:

```solidity
File: contracts/L1/hooks/AssignmentHook.sol
146             return keccak256(
147                 abi.encode(
148                     "PROVER_ASSIGNMENT",
149                     ITaikoL1(_taikoL1Address).getConfig().chainId,
150                     _taikoL1Address,
151                     address(this),
152                     _assignment.metaHash,
153                     _assignment.parentMetaHash,
154                     _blobHash,
155                     _assignment.feeToken,
156                     _assignment.expiry,
157                     _assignment.maxBlockId,
158                     _assignment.maxProposedIn,
159                     _assignment.tierFees
160                 )
161             );
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L146:161

```solidity
File: contracts/L1/libs/LibProposing.sol
126   depositsHash: keccak256(abi.encode(deposits_)),

189   meta_.blobHash = keccak256(_txList);

204   meta_.difficulty = keccak256(abi.encodePacked(block.prevrandao, b.numBlocks, block.number));

213   metaHash: keccak256(abi.encode(meta_)),
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L213:213

```solidity
File: contracts/L1/libs/LibProving.sol
20      bytes32 public constant RETURN_LIVENESS_BOND = keccak256("RETURN_LIVENESS_BOND");

121    if (blk.blockId != _meta.id || blk.metaHash != keccak256(abi.encode(_meta))) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L121:121

```solidity
File: contracts/L1/provers/GuardianProver.sol
46     bytes32 hash = keccak256(abi.encode(_meta, _tran));
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L46:46

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol
292   bytes32 issuerPubKeyHash = keccak256(issuer.pubKey);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L292:292

```solidity
File: contracts/automata-attestation/utils/BytesUtils.sol
372    return keccak256(a) == keccak256(b);

372    return keccak256(a) == keccak256(b);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L372:372

```solidity
File: contracts/bridge/Bridge.sol
450   return keccak256(abi.encode("TAIKO_MESSAGE", _message));
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L450:450

```solidity
File: contracts/signal/LibSignals.sol
8     bytes32 public constant STATE_ROOT = keccak256("STATE_ROOT");

11    bytes32 public constant SIGNAL_ROOT = keccak256("SIGNAL_ROOT");
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/LibSignals.sol#L11:11

```solidity
File: contracts/signal/SignalService.sol
186   return keccak256(abi.encode(_chainId, _kind, _blockId));

203   return keccak256(abi.encodePacked("SIGNAL", _chainId, _app, _signal));
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L203:203

```solidity
File: contracts/team/TimelockTokenPool.sol
170   bytes32 hash = keccak256(abi.encodePacked("Withdraw unlocked Taiko token to: ", _to));
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L170:170

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol
68   bytes32 hash = keccak256(abi.encode("CLAIM_TAIKO_AIRDROP", data));
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L68:68

```solidity
File: contracts/thirdparty/optimism/Bytes.sol
150   return keccak256(_bytes) == keccak256(_other);

150   return keccak256(_bytes) == keccak256(_other);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L150:150

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol
94    Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),

100   Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L100:100

```solidity
File: contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol
55      hash_ = abi.encodePacked(keccak256(_key));
```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L55:55

```solidity
File: contracts/tokenvault/ERC20Vault.sol
176    || keccak256(bytes(ctoken.symbol)) != keccak256(bytes(_ctoken.symbol))


176     || keccak256(bytes(ctoken.symbol)) != keccak256(bytes(_ctoken.symbol))


177     || keccak256(bytes(ctoken.name)) != keccak256(bytes(_ctoken.name))


177     || keccak256(bytes(ctoken.name)) != keccak256(bytes(_ctoken.name))
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L177:177

```solidity
File: contracts/verifiers/SgxVerifier.sol
182             return keccak256(
183                 abi.encode(
184                     "VERIFY_PROOF",
185                     ITaikoL1(taikoL1).getConfig().chainId,
186                     address(this),
187                     _tran,
188                     _newInstance,
189                     _prover,
190                     _metaHash
191                 )
192             );
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L182:192

## [G-25] Stack variable used as a cheaper cache for a state variable is only used once
If the variable is only accessed once, it's cheaper to use the state variable directly that one time, and save the 3 gas the extra stack assignment would spend.


🔴 Affected code:
There are 1 instances of this issue:

```solidity
File: contracts/team/TimelockTokenPool.sol
152       uint128 amountVoided = _voidGrant(r.grant);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L152:152



## [G-26] Use assembly to emit an event
To efficiently emit events, it's possible to utilize assembly by making use of scratch space and the free memory pointer. This approach has the advantage of potentially avoiding the costs associated with memory expansion.

However, it's important to note that in order to safely optimize this process, it is preferable to cache and restore the free memory pointer.

A good example of such practice can be seen in [Solady's](https://github.com/Vectorized/solady/blob/main/src/tokens/ERC1155.sol#L167) codebase.

[Reffrence](https://gist.github.com/CloudEllie/05fda0fdecba2ed7d85f68c709e46c8d#gas-17-use-assembly-to-emit-an-event)


🔴 Affected code:
There are 55 instances of this issue:

```solidity
File: contracts/L1/hooks/AssignmentHook.sol
129     emit BlockAssigned(_blk.assignedProver, _meta, assignment);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L129:129

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
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L50:56

```solidity
File: contracts/L1/libs/LibProposing.sol
166    emit BlobCached(meta_.blobHash);

273             emit BlockProposed({
274                 blockId: blk.blockId,
275                 assignedProver: blk.assignedProver,
276                 livenessBond: _config.livenessBond,
277                 meta: meta_,
278                 depositsProcessed: deposits_
279             });
```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L273:279

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
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L254:260

```solidity
File: contracts/L1/libs/LibVerifying.sol
73             emit BlockVerified({
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
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L198:206

```solidity
File: contracts/L1/provers/GuardianProver.sol
54              emit GuardianApproval(msg.sender, _meta.id, _tran.blockHash, approved_);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L54:54

```solidity
File: contracts/L1/provers/Guardians.sol
95              emit GuardiansUpdated(version, _newGuardians);

121             emit Approved(_operationId, _approval, approved_);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L121:121

```solidity
File: contracts/L2/CrossChainOwned.sol
53              emit TransactionExecuted(nextTxId++, bytes4(txdata));
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L53:53

```solidity
File: contracts/L2/TaikoL2.so
157             emit Anchored(blockhash(parentId), gasExcess);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L157:157

```solidity
File: contracts/L2/TaikoL2EIP1559Configurable.sol
39            emit ConfigAndExcessChanged(_newConfig, _newGasExcess);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L39:39

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
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L519:519

```solidity
File: contracts/common/AddressManager.sol
50              emit AddressSet(_chainId, _name, _newAddress, oldAddress);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L50:50

```solidity
File: contracts/common/EssentialContract.sol
71              emit Paused(msg.sender);

80              emit Unpaused(msg.sender);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L80:80

```solidity
File: contracts/signal/SignalService.sol
59              emit Authorized(_addr, _authorize);

250             emit ChainDataSynced(_chainId, _blockId, _kind, _chainData, signal_);

268             emit SignalSent(_app, _signal, slot_, _value);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L268:268

```solidity
File: contracts/team/TimelockTokenPool.sol
143             emit Granted(_recipient, _grant);

157             emit Voided(_recipient, amountVoided);

222             emit Withdrawn(_recipient, _to, amountToWithdraw, costToWithdraw);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L222:222

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol
93              emit Withdrawn(user, amount);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L93:93

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol
74              emit Claimed(hash);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L74:74

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol
51              emit MigrationStatusChanged(_migratingAddress, _migratingInbound);

63                  emit MigratedTo(migratingAddress, _account, _amount);

80                  emit MigratedTo(migratingAddress, _account, _amount);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L80:80

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
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L314:320

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
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L425:432

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
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L250:256

```solidity
File: contracts/verifiers/SgxVerifier.sol
109                 emit InstanceDeleted(idx, instances[idx].addr);

220                 emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);

230             emit InstanceAdded(id, newInstance, oldInstance, block.timestamp);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L230:230


## [G-27] Using a positive conditional flow to save a NOT opcode
Estimated savings: 3 gas
[Reffrence](https://code4rena.com/reports/2023-01-opensea#g-03-using-a-positive-conditional-flow-to-save-a-not-opcode)

🔴 Affected code:
There are 2 instances of this issue:

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
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L302:306



## [G-28] Avoid contract existence checks by using low level calls
Prior to 0.8.10 the compiler inserted extra code, including EXTCODESIZE (100 gas), to check for contract existence for external function calls. In more recent solidity versions, the compiler will not insert these checks if the external call has a return value. Similar behavior can be achieved in earlier versions by using low-level calls, since low level calls never check for contract existence

note: these are instance missed from bots

🔴 Affected code:
There are 25 instances of this issue:

```solidity
File:  contracts/bridge/Bridge.sol
150  ISignalService(resolve("signal_service", false)).sendSignal(msgHash_);

174  if (!ISignalService(signalService).isSignalSent(address(this), msgHash)) {

199  IRecallableSender(_message.from).onMessageRecalled{ value: _message.value }(
                    _message, msgHash
                ); 

342  ISignalService(resolve("signal_service", false)).isSignalSent({

522  ISignalService(resolve("signal_service", false)).sendSignal(                       
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L150



```solidity
File:  contracts/common/AddressResolver.sol
83   addr_ = payable(IAddressManager(addressManager).getAddress(_chainId, _name));
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L83



```solidity
File:  contracts/L1/hooks/AssignmentHook.sol
149  ITaikoL1(_taikoL1Address).getConfig().chainId,
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L149


```solidity
File:  contracts/L1/provers/GuardianProver.sol
51  ITaikoL1(resolve("taiko", false)).proveBlock(_meta.id, abi.encode(_meta, _tran, _proof));
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L51



```solidity
File:  contracts/L2/TaikoL2.sol
148  ISignalService(resolve("signal_service", false)).syncChainData(
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L148


```solidity
File:  contracts/team/airdrop/ERC20Airdrop.sol
63  IERC20(token).transferFrom(vault, user, amount);

71  IVotes(token).delegateBySig(delegatee, nonce, expiry, v, r, s);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L63


```solidity
File:  contracts/team/TimelockTokenPool.sol
219          IERC20(taikoToken).transferFrom(sharedVault, _to, amountToWithdraw);
220          IERC20(costToken).safeTransferFrom(_recipient, sharedVault, costToWithdraw);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L219-L220


```solidity
File:  contracts/tokenvault/BridgedERC20Base.sol
82  IBridgedERC20(migratingAddress).mint(_account, _amount);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L82


```solidity
File:  contracts/tokenvault/ERC20Vault.sol
164  if (IBridgedERC20(_btokenNew).owner() != owner()) {

184            IBridgedERC20(btokenOld_).changeMigrationStatus(_btokenNew, false);
185            IBridgedERC20(_btokenNew).changeMigrationStatus(btokenOld_, true); 

239  IBridge(resolve("bridge", false)).sendMessage{ value: msg.value }(message);

330  IERC20(token_).safeTransfer(_to, _amount);

360  IBridgedERC20(_token).burn(msg.sender, _amount);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L164



```solidity
File:  contracts/tokenvault/ERC721Vault.sol
176   BridgedERC721(token_).mint(_to, _tokenIds[i]);

198   BridgedERC721(_op.token).burn(_user, _op.tokenIds[i]);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L176


```solidity
File:  contracts/tokenvault/ERC1155Vault.sol
230  BridgedERC1155(token).mintBatch(to, tokenIds, amounts);

252  BridgedERC1155(_op.token).burn(_user, _op.tokenIds[i], _op.amounts[i]);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L230



```solidity
File:  contracts/verifiers/SgxVerifier.sol
128  (bool verified,) = IAttestation(automataDcapAttestation).verifyParsedQuote(_attestation);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L128





## [G-29] Use do while loops instead of for loops
A do while loop will cost less gas since the condition is not being checked for the first iteration.
[Reffrence](https://code4rena.com/reports/2023-05-ajna#g-09-use-do-while-loops-instead-of-for-loops)

🔴 Affected code:
There are 5 instances of this issue:

```solidity
File:  contracts/automata-attestation/AutomataDcapV3Attestation.sol
240   for (uint256 i; i < CPUSVN_LENGTH; ++i) {

420  for (uint256 i; i < 3; ++i) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L240


```solidity
File:  contracts/automata-attestation/lib/PEMCertChainLib.sol
354  for (uint256 i; i < SGX_TCB_CPUSVN_SIZE + 1; ++i) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L354



```solidity
File:  contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol
281  for (uint256 i; i < 3; ++i) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L281


```solidity
File:  contracts/signal/SignalService.sol
104   for (uint256 i; i < hopProofs.length; ++i) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L104

## [G-30] Splitting require() statements that use && saves gas

Splitting require statements that use && operator can save gas. There is a larger deployment gas cost, but with enough runtime calls, the change ends up being cheaper by 3 gas.

note: these are instance missed from bots

🔴 Affected code:
There are 3 instances of this issue:

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


## [G-31] Do not shrink Variables
This means that if you use uint8, EVM has to first convert it uint256 to work on it and the conversion costs extra gas! You may wonder, What were the devs thinking? Why did they create smaller variables then? The answer lies in packing. In solidity, you can pack multiple small variables into one slot, but if you are defining a lone variable and can’t pack it, it’s optimal to use a uint256 rather than uint8.

🔴 Affected code:
There are 2 instances of this issue:

```solidity
File:  contracts/bridge/Bridge.sol
31  uint128 public nextMessageId;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L31


```solidity
File:  contracts/team/airdrop/ERC20Airdrop2.sol
28  uint64 public withdrawalWindow;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L28


## [G-32] Constructors can be marked payable

Payable functions cost less gas to execute, since the compiler does not have to add extra checks to ensure that a payment wasn't provided. A constructor can safely be marked as payable, since only the deployer would be able to pass funds, and the project itself would not pass any funds.

🔴 Affected code:
There are 3 instances of this issue:

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol
54          constructor(address sigVerifyLibAddr, address pemCertLibAddr) {
55              sigVerifyLib = ISigVerifyLib(sigVerifyLibAddr);
56              pemCertLib = PEMCertChainLib(pemCertLibAddr);
57              owner = msg.sender;
58          }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L54-L58

```solidity
File: contracts/automata-attestation/utils/SigVerifyLib.sol
20          constructor(address es256Verifier) {
21              ES256VERIFIER = es256Verifier;
22          }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L20-L22

```solidity
File: contracts/common/EssentialContract.sol
64          constructor() {
65              _disableInitializers();
66          }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L64-L66


## [G-33] The result of function calls should be cached rather than re-calling the function

Caching the result of a function call in a local variable when the function is called multiple times can save gas due to avoiding the need to execute the function code multiple times.


🔴 Affected code:
There are 33 instances of this issue:

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol
111             tbsPtr = der.nextSiblingOf(tbsPtr);

112             tbsPtr = der.nextSiblingOf(tbsPtr);

117             issuerPtr = der.firstChildOf(issuerPtr);

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
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L318:318

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
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L184:184


## [G-34] Empty Blocks Should Be Removed Or Emit Something

The code should be refactored such that they no longer exist, or the block should do something useful, such as emitting an event or reverting. If the contract is meant to be extended, the contract should be abstract and the function signatures be added without any default implementation. If the block is an empty if-statement block to avoid doing subsequent checks in the else-if/else conditions, the else-if/else conditions should be nested under the negation of the if-statement, because they involve different classes of checks, which may lead to the introduction of errors when the code is later modified (if(x){}else if(y){...}else{...} => if(!x){if(y){...}else{...}})

🔴 Affected code:
There are 4 instances of this issue:

```solidity
File: contracts/libs/LibAddress.sol
58              } catch { }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L58:58

```solidity
File: contracts/thirdparty/optimism/rlp/RLPReader.sol
298                 for { } lt(i, _length) { i := add(i, 32) } { mstore(add(dest, i), mload(add(src, i))) }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L298:298

```solidity
File: contracts/tokenvault/ERC1155Vault.sol
268                     } catch { }

265                     } catch { }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L265:265


## [G‑35] Use custom errors rather than revert()/require() strings to save gas
Custom errors are available from solidity version 0.8.4. Custom errors save [~50 gas](https://gist.github.com/IllIllI000/ad1bd0d29a0101b25e57c293b4b0c746) each time they’re hit by [avoiding having to allocate and store the revert string](https://blog.soliditylang.org/2021/04/21/custom-errors/#errors-in-depth). Not defining the strings also save deployment gas


note: these are instance missed from bots

🔴 Affected code:
There are 35 instances of this issue:

```solidity
File:  contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol
77      require(
            localEnclaveReport.reserved3.length == 96 && localEnclaveReport.reserved4.length == 60
                && localEnclaveReport.reportData.length == 64,
            "local QE report has wrong length"
        );
        require(
            pckSignedQeReport.reserved3.length == 96 && pckSignedQeReport.reserved4.length == 60
                && pckSignedQeReport.reportData.length == 64,
            "QE report has wrong length"
        );
        require(
            v3Quote.v3AuthData.certification.certType == 5,
            "certType must be 5: Concatenated PCK Cert Chain (PEM formatted)"
        );
        require(
            v3Quote.v3AuthData.certification.decodedCertDataArray.length == 3, "3 certs in chain"
        );
        require(
            v3Quote.v3AuthData.ecdsa256BitSignature.length == 64
                && v3Quote.v3AuthData.ecdsaAttestationKey.length == 64
                && v3Quote.v3AuthData.qeReportSignature.length == 64,
            "Invalid ECDSA signature format"
        );
        require(
            v3Quote.v3AuthData.qeAuthData.parsedDataSize
                == v3Quote.v3AuthData.qeAuthData.data.length,
            "Invalid QEAuthData size"
        );
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L77-L104


```solidity
File:   contracts/thirdparty/optimism/rlp/RLPReader.sol
37      require(
            _in.length > 0,
            "RLPReader: length of an RLP item must be greater than zero to be decodable"
        );

56      require(
            itemType == RLPItemType.LIST_ITEM,
            "RLPReader: decoded item type for list is not a list item"
        );

        require(
            listOffset + listLength == _in.length,
            "RLPReader: list item has an invalid data remainder"
        );   

112     require(
            itemType == RLPItemType.DATA_ITEM,
            "RLPReader: decoded item type for bytes is not a data item"
        );

        require(
            _in.length == itemOffset + itemLength,
            "RLPReader: bytes value contains an invalid remainder"
        );

152     require(
            _in.length > 0,
            "RLPReader: length of an RLP item must be greater than zero to be decodable"
        );   

172          require(
                _in.length > strLen,
                "RLPReader: length of content must be greater than string length (short string)"
            );    

182         require(
                strLen != 1 || firstByteOfContent >= 0x80,
                "RLPReader: invalid prefix, single byte < 0x80 are not prefixed (short string)"
            );      

192         require(
                _in.length > lenOfStrLen,
                "RLPReader: length of content must be > than length of string length (long string)"
            );

202          require(
                firstByteOfContent != 0x00,
                "RLPReader: length of content must not have any leading zeros (long string)"
            );   

212         require(
                strLen > 55,
                "RLPReader: length of content must be greater than 55 bytes (long string)"
            );

            require(
                _in.length > lenOfStrLen + strLen,
                "RLPReader: length of content must be greater than total length (long string)"
            ); 

228         require(
                _in.length > listLen,
                "RLPReader: length of content must be greater than list length (short list)"
            );     

238         require(
                _in.length > lenOfListLen,
                "RLPReader: length of content must be > than length of list length (long list)"
            );   

248         require(
                firstByteOfContent != 0x00,
                "RLPReader: length of content must not have any leading zeros (long list)"
            );  

258         require(
                listLen > 55,
                "RLPReader: length of content must be greater than 55 bytes (long list)"
            );

            require(
                _in.length > lenOfListLen + listLen,
                "RLPReader: length of content must be greater than total length (long list)"
            );                                                                                                  
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L37


```solidity
File:  contracts/thirdparty/optimism/trie/MerkleTrie.sol
93          require(
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
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L93-L109



```solidity
File:  contracts/thirdparty/optimism/trie/MerkleTrie.sol
128                 require(
                        value_.length > 0,
                        "MerkleTrie: value length must be greater than zero (branch)"
                    );

                    // Extra proof elements are not allowed.
                    require(
                        i == proof.length - 1,
                        "MerkleTrie: value node must be last node in proof (branch)"
                    );

150             require(
                    pathRemainder.length == sharedNibbleLength,
                    "MerkleTrie: path remainder must share all nibbles with key"
                );    

162                require(
                        keyRemainder.length == sharedNibbleLength,
                        "MerkleTrie: key remainder must be identical to path remainder"
                    );

172
                    require(
                        value_.length > 0,
                        "MerkleTrie: value length must be greater than zero (leaf)"
                    );

                    // Extra proof elements are not allowed.
                    require(
                        i == proof.length - 1,
                        "MerkleTrie: value node must be last node in proof (leaf)"
                    );                                                    
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L128



## [G‑36] State variables only set in the constructor should be declared immutable
Avoids a Gsset (20000 gas) in the constructor, and replaces the first access in each transaction (Gcoldsload - 2100 gas) and each access thereafter (Gwarmacces - 100 gas) with a PUSH32 (3 gas). 
While strings are not value types, and therefore cannot be immutable/constant if not hard-coded outside of the constructor, the same behavior can be achieved by making the current contract abstract with virtual functions for the string accessors, and having a child contract override the functions with the hard-coded implementation-specific values
        
🔴 Affected code:
There are 2 instances of this issue:

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol
57              owner = msg.sender;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L57:57

```solidity
File: contracts/automata-attestation/utils/SigVerifyLib.sol
21              ES256VERIFIER = es256Verifier;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L21:21


## [G-37] Caching global variables is more expensive than using the actual variable (use msg.sender instead of caching it)
https://code4rena.com/reports/2022-12-forgeries/#g-07-caching-global-variables-is-more-expensive-than-using-the-actual-variable-use-msgsender-instead-of-caching-it

🔴 Affected code:
There are 2 instances of this issue:

```solidity
File:  contracts/L1/hooks/AssignmentHook.sol
93  address taikoL1Address = msg.sender;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L93



## [G-38] Use local variables for emitting
Use the function/modifier's local copy of the state variable, rather than incurring an extra Gwarmaccess (100 gas). In the unlikely event that the state variable hasn't already been used by the function/modifier, consider whether it is really necessary to include it in the event, given the fact that it incurs a Gcoldsload (2100 gas), or whether it can be passed in to or back out of the functions that do use it

🔴 Affected code:
There are 6 instances of this issue:

```solidity
File: contracts/L1/provers/Guardians.sol
95              emit GuardiansUpdated(version, _newGuardians);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L95:95

```solidity
File: contracts/L2/TaikoL2.sol
157             emit Anchored(blockhash(parentId), gasExcess);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L157:157

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol
63                  emit MigratedTo(migratingAddress, _account, _amount);

80                 emit MigratedTo(migratingAddress, _account, _amount);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L80:80

```solidity
File: contracts/verifiers/SgxVerifier.sol
109                 emit InstanceDeleted(idx, instances[idx].addr);

220                 emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220:

## [G-39] Use selfbalance() instead of address(this).balance
it's recommended to use the selfbalance() function instead of address(this).balance. The selfbalance() function is a built-in Solidity function that returns the balance of the current contract in Wei and is considered more gas-efficient and secure.

🔴 Affected code:
There are 6 instances of this issue:

```solidity
File:  contracts/L1/hooks/AssignmentHook.sol
125        if (address(this).balance > 0) {
            taikoL1Address.sendEther(address(this).balance);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L125-L126



```solidity
File:  contracts/L1/libs/LibProposing.sol
            IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }(
                    blk, meta_, params.hookCalls[i].data
                );

                prevHook = params.hookCalls[i].hook;
            }
            // Refund Ether
            if (address(this).balance != 0) {
                msg.sender.sendEther(address(this).balance);
            }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L153-L262


```solidity
File:  contracts/L2/TaikoL2.sol
174  _to.sendEther(address(this).balance);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L174


## [G-40] Private functions used once can be inlined

Private functions used once can be inlined to save GAS


🔴 Affected code:
There are 35 instances of this issue:

```solidity
File: contracts/L1/hooks/AssignmentHook.sol
164         function _getProverFee(
165             TaikoData.TierFee[] memory _tierFees,
166             uint16 _tierId
167         )
168             private
169             pure
170             returns (uint256)
171         {
172             for (uint256 i; i < _tierFees.length; ++i) {
173                 if (_tierFees[i].tier == _tierId) return _tierFees[i].fee;
174             }
175             revert HOOK_TIER_NOT_FOUND();
176         }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L164:176


```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol
162         function _verify(bytes calldata quote) private view returns (bool, bytes memory) {
163             bytes memory retData = abi.encodePacked(INVALID_EXIT_CODE);
164     
165             // Step 1: Parse the quote input = 152k gas
166             (bool successful, V3Struct.ParsedV3QuoteStruct memory parsedV3Quote) =
167                 V3Parser.parseInput(quote, address(pemCertLib));
168             if (!successful) {
169                 return (false, retData);
170             }
171     
172             return _verifyParsedQuote(parsedV3Quote);
173         }


175         function _verifyQEReportWithIdentity(V3Struct.EnclaveReport memory quoteEnclaveReport)
176             private
177             view
178             returns (bool, EnclaveIdStruct.EnclaveIdStatus status)
179         {
180             EnclaveIdStruct.EnclaveId memory enclaveId = qeIdentity;
181             bool miscselectMatched =
182                 quoteEnclaveReport.miscSelect & enclaveId.miscselectMask == enclaveId.miscselect;
183     
184             bool attributesMatched =
185                 quoteEnclaveReport.attributes & enclaveId.attributesMask == enclaveId.attributes;
186             bool mrsignerMatched = quoteEnclaveReport.mrSigner == enclaveId.mrsigner;
187     
188             bool isvprodidMatched = quoteEnclaveReport.isvProdId == enclaveId.isvprodid;
189     
190             bool tcbFound;
191             for (uint256 i; i < enclaveId.tcbLevels.length; ++i) {
192                 EnclaveIdStruct.TcbLevel memory tcb = enclaveId.tcbLevels[i];
193                 if (tcb.tcb.isvsvn <= quoteEnclaveReport.isvSvn) {
194                     tcbFound = true;
195                     status = tcb.tcbStatus;
196                     break;
197                 }
198             }
199             return (
200                 miscselectMatched && attributesMatched && mrsignerMatched && isvprodidMatched
201                     && tcbFound,
202                 status
203             );
204         }


206         function _checkTcbLevels(
207             IPEMCertChainLib.PCKCertificateField memory pck,
208             TCBInfoStruct.TCBInfo memory tcb
209         )
210             private
211             pure
212             returns (bool, TCBInfoStruct.TCBStatus status)
213         {
214             for (uint256 i; i < tcb.tcbLevels.length; ++i) {
215                 TCBInfoStruct.TCBLevelObj memory current = tcb.tcbLevels[i];
216                 bool pceSvnIsHigherOrGreater = pck.sgxExtension.pcesvn >= current.pcesvn;
217                 bool cpuSvnsAreHigherOrGreater = _isCpuSvnHigherOrGreater(
218                     pck.sgxExtension.sgxTcbCompSvnArr, current.sgxTcbCompSvnArr
219                 );
220                 if (pceSvnIsHigherOrGreater && cpuSvnsAreHigherOrGreater) {
221                     status = current.status;
222                     bool tcbIsRevoked = status == TCBInfoStruct.TCBStatus.TCB_REVOKED;
223                     return (!tcbIsRevoked, status);
224                 }
225             }
226             return (true, TCBInfoStruct.TCBStatus.TCB_UNRECOGNIZED);
227         }


229         function _isCpuSvnHigherOrGreater(
230             uint256[] memory pckCpuSvns,
231             uint8[] memory tcbCpuSvns
232         )
233             private
234             pure
235             returns (bool)
236         {
237             if (pckCpuSvns.length != CPUSVN_LENGTH || tcbCpuSvns.length != CPUSVN_LENGTH) {
238                 return false;
239             }
240             for (uint256 i; i < CPUSVN_LENGTH; ++i) {
241                 if (pckCpuSvns[i] < tcbCpuSvns[i]) {
242                     return false;
243                 }
244             }
245             return true;
246         }


248         function _verifyCertChain(IPEMCertChainLib.ECSha256Certificate[] memory certs)
249             private
250             view
251             returns (bool)
252         {
253             uint256 n = certs.length;
254             bool certRevoked;
255             bool certNotExpired;
256             bool verified;
257             bool certChainCanBeTrusted;
258     
259             for (uint256 i; i < n; ++i) {
260                 IPEMCertChainLib.ECSha256Certificate memory issuer;
261                 if (i == n - 1) {
262                     // rootCA
263                     issuer = certs[i];
264                 } else {
265                     issuer = certs[i + 1];
266                     if (i == n - 2) {
267                         // this cert is expected to be signed by the root
268                         certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.ROOT)][certs[i]
269                             .serialNumber];
270                     } else if (certs[i].isPck) {
271                         certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.PCK)][certs[i]
272                             .serialNumber];
273                     }
274                     if (certRevoked) {
275                         break;
276                     }
277                 }
278     
279                 certNotExpired =
280                     block.timestamp > certs[i].notBefore && block.timestamp < certs[i].notAfter;
281                 if (!certNotExpired) {
282                     break;
283                 }
284     
285                 verified = sigVerifyLib.verifyES256Signature(
286                     certs[i].tbsCertificate, certs[i].signature, issuer.pubKey
287                 );
288                 if (!verified) {
289                     break;
290                 }
291     
292                 bytes32 issuerPubKeyHash = keccak256(issuer.pubKey);
293     
294                 if (issuerPubKeyHash == ROOTCA_PUBKEY_HASH) {
295                     certChainCanBeTrusted = true;
296                     break;
297                 }
298             }
299     
300             return !certRevoked && certNotExpired && verified && certChainCanBeTrusted;
301         }

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
313             bytes32 expectedAuthDataHash = bytes32(qeEnclaveReport.reportData.substring(0, 32));
314             bytes memory concatOfAttestKeyAndQeAuthData =
315                 abi.encodePacked(authDataV3.ecdsaAttestationKey, authDataV3.qeAuthData.data);
316             bytes32 computedAuthDataHash = sha256(concatOfAttestKeyAndQeAuthData);
317     
318             bool qeReportDataIsValid = expectedAuthDataHash == computedAuthDataHash;
319             if (qeReportDataIsValid) {
320                 bytes memory pckSignedQeReportBytes =
321                     V3Parser.packQEReport(authDataV3.pckSignedQeReport);
322                 bool qeSigVerified = sigVerifyLib.verifyES256Signature(
323                     pckSignedQeReportBytes, authDataV3.qeReportSignature, pckCertPubKey
324                 );
325                 bool quoteSigVerified = sigVerifyLib.verifyES256Signature(
326                     signedQuoteData, authDataV3.ecdsa256BitSignature, authDataV3.ecdsaAttestationKey
327                 );
328                 return qeSigVerified && quoteSigVerified;
329             } else {
330                 return false;
331             }
332         }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L303:332

```solidity
File: contracts/automata-attestation/utils/BytesUtils.sol
272         function memcpy(uint256 dest, uint256 src, uint256 len) private pure {
273             assembly {
274                 mcopy(dest, src, len)
275             }
276         }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L272:276

```solidity
File: contracts/bridge/Bridge.sol
555         function _loadContext() private view returns (Context memory) {
556             if (block.chainid == 1) {
557                 bytes32 msgHash;
558                 address from;
559                 uint64 srcChainId;
560                 assembly {
561                     msgHash := tload(_CTX_SLOT)
562                     from := tload(add(_CTX_SLOT, 1))
563                     srcChainId := tload(add(_CTX_SLOT, 2))
564                 }
565                 return Context(msgHash, from, srcChainId);
566             } else {
567                 return __ctx;
568             }
569         }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L555:569

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
281             // cache state root
282             bool cacheStateRoot = _hop.cacheOption == CacheOption.CACHE_BOTH
283                 || _hop.cacheOption == CacheOption.CACHE_STATE_ROOT;
284     
285             if (cacheStateRoot && _isFullProof && !_isLastHop) {
286                 _syncChainData(_chainId, LibSignals.STATE_ROOT, _blockId, _hop.rootHash);
287             }
288     
289             // cache signal root
290             bool cacheSignalRoot = _hop.cacheOption == CacheOption.CACHE_BOTH
291                 || _hop.cacheOption == CacheOption.CACHE_SIGNAL_ROOT;
292     
293             if (cacheSignalRoot && (_isFullProof || !_isLastHop)) {
294                 _syncChainData(_chainId, LibSignals.SIGNAL_ROOT, _blockId, _signalRoot);
295             }
296         }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L271:296

```solidity
File: contracts/team/TimelockTokenPool.sol
225         function _voidGrant(Grant storage _grant) private returns (uint128 amountVoided) {
226             uint128 amountOwned = _getAmountOwned(_grant);
227     
228             amountVoided = _grant.amount - amountOwned;
229             _grant.amount = amountOwned;
230     
231             _grant.grantStart = 0;
232             _grant.grantPeriod = 0;
233         }

239         function _getAmountUnlocked(Grant memory _grant) private view returns (uint128) {
240             return _calcAmount(
241                 _getAmountOwned(_grant), _grant.unlockStart, _grant.unlockCliff, _grant.unlockPeriod
242             );
243         }

267         function _validateGrant(Grant memory _grant) private pure {
268             if (_grant.amount == 0) revert INVALID_GRANT();
269             _validateCliff(_grant.grantStart, _grant.grantCliff, _grant.grantPeriod);
270             _validateCliff(_grant.unlockStart, _grant.unlockCliff, _grant.unlockPeriod);
271         }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L267:271

```solidity
File: contracts/thirdparty/optimism/rlp/RLPWriter.sol
32          function _writeLength(uint256 _len, uint256 _offset) private pure returns (bytes memory out_) {
33              if (_len < 56) {
34                  out_ = new bytes(1);
35                  out_[0] = bytes1(uint8(_len) + uint8(_offset));
36              } else {
37                  uint256 lenLen;
38                  uint256 i = 1;
39                  while (_len / i != 0) {
40                      lenLen++;
41                      i *= 256;
42                  }
43      
44                  out_ = new bytes(lenLen + 1);
45                  out_[0] = bytes1(uint8(lenLen) + uint8(_offset) + 55);
46                  for (i = 1; i <= lenLen; i++) {
47                      out_[i] = bytes1(uint8((_len / (256 ** (lenLen - i))) % 256));
48                  }
49              }
50          }

55          function _toBinary(uint256 _x) private pure returns (bytes memory out_) {
56              bytes memory b = abi.encodePacked(_x);
57      
58              uint256 i = 0;
59              for (; i < 32; i++) {
60                  if (b[i] != 0) {
61                      break;
62                  }
63              }
64      
65              out_ = new bytes(32 - i);
66              for (uint256 j = 0; j < out_.length; j++) {
67                  out_[j] = b[i++];
68              }
69          }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L55:69

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol
205         function _parseProof(bytes[] memory _proof) private pure returns (TrieNode[] memory proof_) {
206             uint256 length = _proof.length;
207             proof_ = new TrieNode[](length);
208             for (uint256 i = 0; i < length;) {
209                 proof_[i] = TrieNode({ encoded: _proof[i], decoded: RLPReader.readList(_proof[i]) });
210                 unchecked {
211                     ++i;
212                 }
213             }
214         }

227         function _getNodePath(TrieNode memory _node) private pure returns (bytes memory nibbles_) {
228             nibbles_ = Bytes.toNibbles(RLPReader.readBytes(_node.decoded[0]));
229         }

235         function _getSharedNibbleLength(
236             bytes memory _a,
237             bytes memory _b
238         )
239             private
240             pure
241             returns (uint256 shared_)
242         {
243             uint256 max = (_a.length < _b.length) ? _a.length : _b.length;
244             for (; shared_ < max && _a[shared_] == _b[shared_];) {
245                 unchecked {
246                     ++shared_;
247                 }
248             }
249         }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L235:249

```solidity
File: contracts/tokenvault/ERC1155Vault.sol
240         function _handleMessage(
241             address _user,
242             BridgeTransferOp memory _op
243         )
244             private
245             returns (bytes memory msgData_, CanonicalNFT memory ctoken_)
246         {
247             unchecked {
248                 // is a btoken, meaning, it does not live on this chain
249                 if (bridgedToCanonical[_op.token].addr != address(0)) {
250                     ctoken_ = bridgedToCanonical[_op.token];
251                     for (uint256 i; i < _op.tokenIds.length; ++i) {
252                         BridgedERC1155(_op.token).burn(_user, _op.tokenIds[i], _op.amounts[i]);
253                     }
254                 } else {
255                     // is a ctoken token, meaning, it lives on this chain
256                     ctoken_ = CanonicalNFT({
257                         chainId: uint64(block.chainid),
258                         addr: _op.token,
259                         symbol: "",
260                         name: ""
261                     });
262                     IERC1155NameAndSymbol t = IERC1155NameAndSymbol(_op.token);
263                     try t.name() returns (string memory _name) {
264                         ctoken_.name = _name;
265                     } catch { }
266                     try t.symbol() returns (string memory _symbol) {
267                         ctoken_.symbol = _symbol;
268                     } catch { }
269                     for (uint256 i; i < _op.tokenIds.length; ++i) {
270                         IERC1155(_op.token).safeTransferFrom({
271                             from: msg.sender,
272                             to: address(this),
273                             id: _op.tokenIds[i],
274                             amount: _op.amounts[i],
275                             data: ""
276                         });
277                     }
278                 }
279             }
280             msgData_ = abi.encodeCall(
281                 this.onMessageInvocation, abi.encode(ctoken_, _user, _op.to, _op.tokenIds, _op.amounts)
282             );
283         }

288         function _getOrDeployBridgedToken(CanonicalNFT memory _ctoken)
289             private
290             returns (address btoken_)
291         {
292             btoken_ = canonicalToBridged[_ctoken.chainId][_ctoken.addr];
293             if (btoken_ == address(0)) {
294                 btoken_ = _deployBridgedToken(_ctoken);
295             }
296         }

303         function _deployBridgedToken(CanonicalNFT memory _ctoken) private returns (address btoken_) {
304             bytes memory data = abi.encodeCall(
305                 BridgedERC1155.init,
306                 (owner(), addressManager, _ctoken.addr, _ctoken.chainId, _ctoken.symbol, _ctoken.name)
307             );
308     
309             btoken_ = address(new ERC1967Proxy(resolve("bridged_erc1155", false), data));
310     
311             bridgedToCanonical[btoken_] = _ctoken;
312             canonicalToBridged[_ctoken.chainId][_ctoken.addr] = btoken_;
313     
314             emit BridgedTokenDeployed({
315                 chainId: _ctoken.chainId,
316                 ctoken: _ctoken.addr,
317                 btoken: btoken_,
318                 ctokenSymbol: _ctoken.symbol,
319                 ctokenName: _ctoken.name
320             });
321         }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L303:321

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
357             // If it's a bridged token
358             if (bridgedToCanonical[_token].addr != address(0)) {
359                 ctoken_ = bridgedToCanonical[_token];
360                 IBridgedERC20(_token).burn(msg.sender, _amount);
361                 balanceChange_ = _amount;
362             } else {
363                 // If it's a canonical token
364                 IERC20Metadata meta = IERC20Metadata(_token);
365                 ctoken_ = CanonicalERC20({
366                     chainId: uint64(block.chainid),
367                     addr: _token,
368                     decimals: meta.decimals(),
369                     symbol: meta.symbol(),
370                     name: meta.name()
371                 });
372     
373                 // Query the balance then query it again to get the actual amount of
374                 // token transferred into this address, this is more accurate than
375                 // simply using `amount` -- some contract may deduct a fee from the
376                 // transferred amount.
377                 IERC20 t = IERC20(_token);
378                 uint256 _balance = t.balanceOf(address(this));
379                 t.safeTransferFrom({ from: msg.sender, to: address(this), value: _amount });
380                 balanceChange_ = t.balanceOf(address(this)) - _balance;
381             }
382     
383             msgData_ = abi.encodeCall(
384                 this.onMessageInvocation, abi.encode(ctoken_, _user, _to, balanceChange_)
385             );
386         }

391         function _getOrDeployBridgedToken(CanonicalERC20 memory ctoken)
392             private
393             returns (address btoken)
394         {
395             btoken = canonicalToBridged[ctoken.chainId][ctoken.addr];
396     
397             if (btoken == address(0)) {
398                 btoken = _deployBridgedToken(ctoken);
399             }
400         }

407         function _deployBridgedToken(CanonicalERC20 memory ctoken) private returns (address btoken) {
408             bytes memory data = abi.encodeCall(
409                 BridgedERC20.init,
410                 (
411                     owner(),
412                     addressManager,
413                     ctoken.addr,
414                     ctoken.chainId,
415                     ctoken.decimals,
416                     ctoken.symbol,
417                     ctoken.name
418                 )
419             );
420     
421             btoken = address(new ERC1967Proxy(resolve("bridged_erc20", false), data));
422             bridgedToCanonical[btoken] = ctoken;
423             canonicalToBridged[ctoken.chainId][ctoken.addr] = btoken;
424     
425             emit BridgedTokenDeployed({
426                 srcChainId: ctoken.chainId,
427                 ctoken: ctoken.addr,
428                 btoken: btoken,
429                 ctokenSymbol: ctoken.symbol,
430                 ctokenName: ctoken.name,
431                 ctokenDecimal: ctoken.decimals
432             });
433         }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L407:433

```solidity
File: contracts/tokenvault/ERC721Vault.sol
187         function _handleMessage(
188             address _user,
189             BridgeTransferOp memory _op
190         )
191             private
192             returns (bytes memory msgData_, CanonicalNFT memory ctoken_)
193         {
194             unchecked {
195                 if (bridgedToCanonical[_op.token].addr != address(0)) {
196                     ctoken_ = bridgedToCanonical[_op.token];
197                     for (uint256 i; i < _op.tokenIds.length; ++i) {
198                         BridgedERC721(_op.token).burn(_user, _op.tokenIds[i]);
199                     }
200                 } else {
201                     ERC721Upgradeable t = ERC721Upgradeable(_op.token);
202     
203                     ctoken_ = CanonicalNFT({
204                         chainId: uint64(block.chainid),
205                         addr: _op.token,
206                         symbol: t.symbol(),
207                         name: t.name()
208                     });
209     
210                     for (uint256 i; i < _op.tokenIds.length; ++i) {
211                         t.safeTransferFrom(_user, address(this), _op.tokenIds[i]);
212                     }
213                 }
214             }
215     
216             msgData_ = abi.encodeCall(
217                 this.onMessageInvocation, abi.encode(ctoken_, _user, _op.to, _op.tokenIds)
218             );
219         }

224         function _getOrDeployBridgedToken(CanonicalNFT memory _ctoken)
225             private
226             returns (address btoken_)
227         {
228             btoken_ = canonicalToBridged[_ctoken.chainId][_ctoken.addr];
229     
230             if (btoken_ == address(0)) {
231                 btoken_ = _deployBridgedToken(_ctoken);
232             }
233         }

240         function _deployBridgedToken(CanonicalNFT memory _ctoken) private returns (address btoken_) {
241             bytes memory data = abi.encodeCall(
242                 BridgedERC721.init,
243                 (owner(), addressManager, _ctoken.addr, _ctoken.chainId, _ctoken.symbol, _ctoken.name)
244             );
245     
246             btoken_ = address(new ERC1967Proxy(resolve("bridged_erc721", false), data));
247             bridgedToCanonical[btoken_] = _ctoken;
248             canonicalToBridged[_ctoken.chainId][_ctoken.addr] = btoken_;
249     
250             emit BridgedTokenDeployed({
251                 chainId: _ctoken.chainId,
252                 ctoken: _ctoken.addr,
253                 btoken: btoken_,
254                 ctokenSymbol: _ctoken.symbol,
255                 ctokenName: _ctoken.name
256             });
257         }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L240:257

```solidity
File: contracts/verifiers/SgxVerifier.sol
226         function _replaceInstance(uint256 id, address oldInstance, address newInstance) private {
227             // Replacing an instance means, it went through a cooldown (if added by on-chain RA) so no
228             // need to have a cooldown
229             instances[id] = Instance(newInstance, uint64(block.timestamp));
230             emit InstanceAdded(id, newInstance, oldInstance, block.timestamp);
231         }

233         function _isInstanceValid(uint256 id, address instance) private view returns (bool) {
234             if (instance == address(0)) return false;
235             if (instance != instances[id].addr) return false;
236             return instances[id].validSince <= block.timestamp
237                 && block.timestamp <= instances[id].validSince + INSTANCE_EXPIRY;
238         }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L233:238



## [G-41] State variable read in a loop

The state variable should be cached in and read from a local variable, or accumulated in a local variable then written to storage once outside of the loop, rather than reading/updating it on every iteration of the loop, which will replace each Gwarmaccess (100 gas) with a much cheaper stack read.


🔴 Affected code:
There are 15 instances of this issue:

```solidity
File: contracts/L1/provers/Guardians.sol
74              for (uint256 i; i < guardians.length; ++i) {

84                  if (guardianIds[guardian] != 0) revert INVALID_GUARDIAN_SET();

135                     if (count == minGuardians) return true;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L135:135

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol
81                  if (_serialNumIsRevoked[index][serialNumBatch[i]]) {

96                  if (!_serialNumIsRevoked[index][serialNumBatch[i]]) {

240             for (uint256 i; i < CPUSVN_LENGTH; ++i) {

268                         certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.ROOT)][certs[i]

424                     (certDecodedSuccessfully, parsedQuoteCerts[i]) = pemCertLib.decodeCert(
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L424:424

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol
354             for (uint256 i; i < SGX_TCB_CPUSVN_SIZE + 1; ++i) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L354:354

```solidity
File: contracts/automata-attestation/utils/BytesUtils.sol
336                 decoded = uint8(BASE32_HEX_TABLE[uint256(uint8(char)) - 0x30]);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L336:336

```solidity
File: contracts/bridge/Bridge.sol
92                  proofReceipt[msgHash].receivedAt = _timestamp;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L92:92

```solidity
File: contracts/team/airdrop/ERC721Airdrop.sol
60                  IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L60:60

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol
111                 if (currentNode.decoded.length == BRANCH_NODE_LENGTH) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L111:111

```solidity
File: contracts/verifiers/SgxVerifier.sol
107                 if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();

211                 if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L211:211

## [G-42] Use struct dot notation to avoid memory allocation
In the instances below, structs values are being assigned via the following method: Type({field1: value1, field2: value2});. This method results in a new struct being created in memory with our specified fields. That memory struct is then written to storage. We can leverage the struct dot notation to assign values directly to storage, thus avoiding allocating memory space for a temporary struct.


🔴 Affected code:
There are 4 instances of this issue:

```solidity
File: contracts/thirdparty/optimism/rlp/RLPReader.sol
47              out_ = RLPItem({ length: _in.length, ptr: ptr });

84                  out_[itemCount] = RLPItem({
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L84:84

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol
209                 proof_[i] = TrieNode({ encoded: _proof[i], decoded: RLPReader.readList(_proof[i]) });
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L209:209

```solidity
File: contracts/tokenvault/ERC20Vault.sol
365                 ctoken_ = CanonicalERC20({
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L365:365


## [G-43] Use assembly in place of abi.decode to extract calldata values more efficiently
Instead of using abi.decode, we can use assembly to decode our desired calldata values directly. This will allow us to avoid decoding calldata values that we will not use.
[Reffrence](https://code4rena.com/reports/2023-05-juicebox#g-04-use-assembly-in-place-of-abidecode-to-extract-calldata-values-more-efficiently)

🔴 Affected code:
There are 16 instances of this issue:

```solidity
File:  contracts/automata-attestation/utils/SigVerifyLib.sol
140  return abi.decode(ret, (uint256)) == 1;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L140


```solidity
File:  contracts/L1/TaikoL1.sol
88  ) = abi.decode(_input, (TaikoData.BlockMetadata, TaikoData.Transition, TaikoData.TierProof));
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L88


```solidity
File:  contracts/L1/hooks/AssignmentHook.sol
77  Input memory input = abi.decode(_data, (Input));
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L77


```solidity
File:  contracts/L1/libs/LibProposing.sol
78  TaikoData.BlockParams memory params = abi.decode(_data, (TaikoData.BlockParams));
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L78



```solidity
File:  contracts/L2/CrossChainOwned.sol
42  (uint64 txId, bytes memory txdata) = abi.decode(_data, (uint64, bytes));
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L42


```solidity
File:  contracts/signal/SignalService.sol
94  HopProof[] memory hopProofs = abi.decode(_proof, (HopProof[]));
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L94



```solidity
File:  contracts/team/airdrop/ERC20Airdrop.sol
70   abi.decode(delegationData, (address, uint256, uint256, uint8, bytes32, bytes32));
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L70



```solidity
File:  contracts/tokenvault/ERC20Vault.sol
260    abi.decode(_data, (CanonicalERC20, address, address, uint256));

298   (bytes memory data) = abi.decode(_message.data[4:], (bytes));

300    abi.decode(data, (CanonicalERC20, address, address, uint256));
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L260


```solidity
File:  contracts/tokenvault/ERC721Vault.sol
84   abi.decode(_data, (CanonicalNFT, address, address, uint256[]));

123  (bytes memory data) = abi.decode(_message.data[4:], (bytes));

125    abi.decode(data, (CanonicalNFT, address, address, uint256[]));
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L84



```solidity
File:  contracts/tokenvault/ERC1155Vault.sol
100  ) = abi.decode(data, (CanonicalNFT, address, address, uint256[], uint256[]));

140   (bytes memory data) = abi.decode(message.data[4:], (bytes));

142    abi.decode(data, (CanonicalNFT, address, address, uint256[], uint256[]));
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L100


## [G-44] Cache external calls outside of loop to avoid re-calling function on each iteration
Performing STATICCALLs that do not depend on variables incremented in loops should always try to be avoided within the loop. In the following instances, we are able to cache the external calls outside of the loop to save a STATICCALL (100 gas) per loop iteration.

🔴 Affected code:
There are 6 instances of this issue:

```solidity
File:  contracts/team/airdrop/ERC721Airdrop.sol
60   IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L60


```solidity
File:  contracts/tokenvault/ERC721Vault.sol
171  IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);

176  BridgedERC721(token_).mint(_to, _tokenIds[i]);

198  BridgedERC721(_op.token).burn(_user, _op.tokenIds[i]);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L171


```solidity
File:  contracts/tokenvault/ERC1155Vault.sol
252   BridgedERC1155(_op.token).burn(_user, _op.tokenIds[i], _op.amounts[i]);

170    IERC1155(_op.token).safeTransferFrom({
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L252


## [G-45] Structs can be modified to fit in fewer storage slots
Some member types can be safely modified, and as result, these struct will fit in fewer storage slots. Each slot saved can avoid an extra Gsset (20000 gas) for the first setting of the struct. Subsequent reads as well as writes have smaller gas savings.

🔴 Affected code:
There are 1 instances of this issue:
```solidity
File:  contracts/tokenvault/ERC20Vault.sol
32  struct BridgeTransferOp {
        uint64 destChainId;
        address destOwner;
        address to;
        address token;
        uint256 amount;
        uint256 gasLimit;
        uint256 fee;
        address refundTo;
        string memo;
    }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L32-L42

- with this change you can save 3 storage slote
```diff
    struct BridgeTransferOp {
        uint64 destChainId;
        address destOwner;
+       uint64 amount;
        address to;
+       uint64 gasLimit;
        address token;
-       uint256 amount;
-       uint256 gasLimit;
-       uint256 fee;
+       uint64 fee;
        address refundTo;
        string memo;
    }
```

## [G‑46] Use assembly to validate msg.sender
We can use assembly to efficiently validate msg.sender with the least amount of opcodes necessary.

🔴 Affected code:
There are 10 instances of this issue:

```solidity
File:  contracts/bridge/Bridge.sol
294  if (msg.sender == refundTo) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L294


```solidity
File:  contracts/tokenvault/BridgedERC20Base.sol
61   if (msg.sender == migratingAddress) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L61



```solidity 
File:  contracts/bridge/Bridge.sol
322  if (msg.sender != _message.destOwner) revert B_PERMISSION_DENIED();
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L322



```solidity
File:  contracts/common/AddressResolver.sol
25   if (msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L25


```solidity
File:  contracts/common/EssentialContract.sol
42  if (msg.sender != owner() && msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L42



```solidity
File:  contracts/L2/TaikoL2.sol
123  if (msg.sender != GOLDEN_TOUCH_ADDRESS) revert L2_INVALID_SENDER();
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L123


```solidity
File:  contracts/tokenvault/BridgedERC20.sol
38  if (msg.sender != owner() && msg.sender != snapshooter) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L38


```solidity
File: contracts/tokenvault/BridgedERC20Base.sol
78  if (msg.sender != _account) revert BB_PERMISSION_DENIED();
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L78



## [G-47] Pre-increment and pre-decrement are cheaper thanĀ +1 ,-1

🔴 Affected code:
There are 5 instances of this issue:

```solidity
File:  contracts/L1/libs/LibProving.sol
252  ts.contestations += 1;

377  _ts.contestations += 1;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L252


```solidity
File:  contracts/thirdparty/optimism/rlp/RLPReader.sol
89  itemCount += 1;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L89



```solidity
File:  contracts/thirdparty/optimism/trie/MerkleTrie.sol
137 currentKeyIndex += 1;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L137


```solidity
File:  contracts/automata-attestation/utils/BytesUtils.sol
359  bitlen -= 1;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L359




## [G-48] Storage re-read via storage pointer

The instances below point to the second+ access of a state variable, via a storage pointer, within a function. Caching the value replaces each Gwarmaccess (100 gas) with a much cheaper stack read.

🔴 Affected code:
There are 4 instances of this issue:

```solidity
File: contracts/L1/libs/LibProving.sol
192                 bool returnLivenessBond = blk.livenessBond > 0 && _proof.data.length == 32
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L192:192

```solidity
File: contracts/L1/libs/LibVerifying.sol
107             uint32 tid = blk.verifiedTransitionId;

184                     if (ts.prover != blk.assignedProver) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L184:184

```solidity
File: contracts/team/TimelockTokenPool.sol
198             costToWithdraw = _amountUnlocked * r.grant.costPerToken - r.costPaid;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L198:198


## [G-49] Initializer can be marked payable
Payable functions cost less gas to execute, since the compiler does not have to add extra checks to ensure that a payment wasn't provided.An Initializer can safely be marked as payable, since only the allowed user would be able to pass funds, and the project itself would not pass any funds.

🔴 Affected code:
There are 25 instances of this issue:


```solidity
File:  contracts/bridge/Bridge.sol
75  function init(address _owner, address _addressManager) external initializer {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L75



```solidity
File:  contracts/common/AddressManager.sol
30  function init(address _owner) external initializer {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L30


```solidity
File:  contracts/L1/TaikoL1.sol
42  function init(
        address _owner,
        address _addressManager,
        bytes32 _genesisBlockHash
    )
        external
        initializer
    {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L42



```solidity 
File:  contracts/L1/TaikoToken.sol
25  function init(
        address _owner,
        string calldata _name,
        string calldata _symbol,
        address _recipient
    )
        public
        initializer
    {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L25


```solidity
File:  contracts/L1/gov/TaikoGovernor.sol
31  function init(
        address _owner,
        IVotesUpgradeable _token,
        TimelockControllerUpgradeable _timelock
    )
        external
        initializer
    {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L31


```solidity
File:  contracts/L1/gov/TaikoTimelockController.sol
15   function init(address _owner, uint256 _minDelay) external initializer {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L15


```solidity
File:  contracts/L1/hooks/AssignmentHook.sol
57   function init(address _owner, address _addressManager) external initializer {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L57


```solidity
File:  contracts/L1/provers/GuardianProver.sol
25  function init(address _owner, address _addressManager) external initializer {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L25



```solidity
File:  contracts/L1/tiers/DevnetTierProvider.sol
15  function init(address _owner) external initializer {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L15


```solidity
File:  contracts/L1/tiers/MainnetTierProvider.sol
15  function init(address _owner) external initializer {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L15



```solidity
File:  contracts/L1/tiers/TestnetTierProvider.sol
15  function init(address _owner) external initializer {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L15



```solidity
File:  contracts/L2/TaikoL2.sol
71    function init(
        address _owner,
        address _addressManager,
        uint64 _l1ChainId,
        uint64 _gasExcess
    )
        external
        initializer
    {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L71


```solidity
File:  contracts/signal/SignalService.sol
48  function init(address _owner, address _addressManager) external initializer {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L48



```solidity
File:  contracts/team/TimelockTokenPool.sol
111 function init(
        address _owner,
        address _taikoToken,
        address _costToken,
        address _sharedVault
    )
        external
        initializer
    {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L111


```solidity
File:  contracts/team/airdrop/ERC20Airdrop.sol
27  function init(
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
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L27


```solidity
File:  contracts/team/airdrop/ERC20Airdrop2.sol
54  function init(
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
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L54


```solidity
File:  contracts/team/airdrop/ERC721Airdrop.sol
25  function init(
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
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L25


```solidity
File:  contracts/tokenvault/BaseVault.sol
32  function init(address _owner, address _addressManager) external initializer {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L32



```solidity
File:  contracts/tokenvault/BridgedERC20.sol
52  function init(
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
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L52


```solidity
File:  contracts/tokenvault/BridgedERC721.sol
31    function init(
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
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L31



```solidity
File:  contracts/tokenvault/BridgedERC1155.sol
38    function init(
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
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L38



```solidity
File:  contracts/tokenvault/adapters/USDCAdapter.sol
38  function init(address _owner, address _addressManager, IUSDC _usdc) external initializer {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L38


```solidity
File:  contracts/verifiers/GuardianVerifier.sol
18  function init(address _owner, address _addressManager) external initializer {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L18



```solidity
File:  contracts/verifiers/SgxVerifier.sol
83   function init(address _owner, address _addressManager) external initializer {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L83


## [G‑50] Use inline assembly to access the chain ID
The original implementation uses the block.chainid global variable, while the optimized version employs inline assembly to access the chain ID, potentially reducing gas consumption.

🔴 Affected code:
There are 37 instances of this issue:

```solidity
File:  contracts/bridge/Bridge.sol
65  if (_chainId != block.chainid) revert B_INVALID_CHAINID();

133 if (_message.destChainId == block.chainid) {

146  message_.srcChainId = uint64(block.chainid);

341  if (_message.srcChainId != block.chainid) return false;

360  if (_message.srcChainId != block.chainid) return false;

382  if (_message.destChainId != block.chainid) return false;

430            block.chainid == 2 // Ropsten
                || block.chainid == 4 // Rinkeby
                || block.chainid == 5 // Goerli
                || block.chainid == 42 // Kovan
                || block.chainid == 17_000 // Holesky
                || block.chainid == 11_155_111 // Sepolia

439  } else if (block.chainid >= 32_300 && block.chainid <= 32_400) {

530  if (block.chainid == 1) {

542  if (block.chainid == 1) {

556  if (block.chainid == 1) {                                
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L65


```solidity
File:  contracts/common/AddressResolver.sol
39   return _resolve(uint64(block.chainid), _name, _allowZeroAddress);

59   if (block.chainid > type(uint64).max) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L39


```solidity
File:  contracts/common/EssentialContract.sol
120  if (block.chainid == 1) {

131  if (block.chainid == 1) {    
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L120


```solidity
File:  contracts/L1/libs/LibVerifying.sol
247   _config.chainId <= 1 || _config.chainId == block.chainid //
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L247



```solidity
File:  contracts/L2/CrossChainOwned.sol
70  if (_ownerChainId == 0 || _ownerChainId == block.chainid) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L70


```solidity
File:  contracts/L2/TaikoL2.sol
82  if (block.chainid <= 1 || block.chainid > type(uint64).max) {

240  inputs[255] = bytes32(block.chainid);    
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L82



```solidity
File:  contracts/signal/SignalService.sol
111  if (hop.chainId != block.chainid) revert SS_INVALID_LAST_HOP_CHAINID();

114  if (hop.chainId == 0 || hop.chainId == block.chainid) {

264  slot_ = getSignalSlot(uint64(block.chainid), _app, _signal);    

308  bytes32 slot = getSignalSlot(uint64(block.chainid), _app, _signal);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L111



```solidity
File:  contracts/tokenvault/ERC20Vault.sol
328  if (_ctoken.chainId == block.chainid) {

366  chainId: uint64(block.chainid),    
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#328


```solidity
File:  contracts/tokenvault/ERC721Vault.sol
168  if (_ctoken.chainId == block.chainid) {

204   chainId: uint64(block.chainid),    
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L168



```solidity
File:  contracts/tokenvault/ERC1155Vault.sol
223  if (ctoken.chainId == block.chainid) {

257   chainId: uint64(block.chainid),    
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L223


```solidity
File:  contracts/tokenvault/LibBridgedToken.sol
21  _srcToken == address(0) || _srcChainId == 0 || _srcChainId == block.chainid
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L21

## [G-51] Consider using OZ EnumerateSet in place of nested mappings             
Nested mappings and multi-dimensional arrays in Solidity operate through a process of double hashing, wherein the original storage slot and the first key are concatenated and hashed, and then this hash is again concatenated with the second key and hashed. This process can be quite gas expensive due to the double-hashing operation and subsequent storage operation (sstore).
A possible optimization involves manually concatenating the keys followed by a single hash operation and an sstore. However, this technique introduces the risk of storage collision, especially when there are other nested hash maps in the contract that use the same key types. Because Solidity is unaware of the number and structure of nested hash maps in a contract, it follows a conservative approach in computing the storage slot to avoid possible collisions.
OpenZeppelin's EnumerableSet provides a potential solution to this problem. It creates a data structure that combines the benefits of set operations with the ability to enumerate stored elements, which is not natively available in Solidity. EnumerableSet handles the element uniqueness internally and can therefore provide a more gas-efficient and collision-resistant alternative to nested mappings or multi-dimensional arrays in certain scenarios.

🔴 Affected code:
There are 7 instances of this issue:

```solidity
File:  contracts/automata-attestation/AutomataDcapV3Attestation.sol
47  mapping(uint256 idx => mapping(bytes serialNum => bool revoked)) private _serialNumIsRevoked;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L47


```solidity
File:  contracts/common/AddressManager.sol
12   mapping(uint256 chainId => mapping(bytes32 name => address addr)) private __addresses;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L12


```solidity
File:  contracts/L1/TaikoData.sol
183  mapping(uint64 blockId => mapping(bytes32 parentHash => uint32 transitionId)) transitionIds;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L183



```solidity
File:  contracts/L1/provers/Guardians.sol
19  mapping(uint32 version => mapping(bytes32 hash => uint256 approvalBits)) internal _approvals;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L19


```solidity
File:  contracts/signal/SignalService.sol
17    mapping(uint64 chainId => mapping(bytes32 kind => uint64 blockId)) public topBlockId;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L17



```solidity
File:  contracts/tokenvault/BaseNFTVault.sol
59   mapping(uint256 chainId => mapping(address ctoken => address btoken)) public canonicalToBridged;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L59



```solidity
File:  contracts/tokenvault/ERC20Vault.sol
49   mapping(uint256 chainId => mapping(address ctoken => address btoken)) public canonicalToBridged;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L49

## [G-52] Instead of counting down in for statements, count up
Counting down is more gas efficient than counting up because neither we are making zero variable to non-zero variable and also we will get gas refund in the last transaction when making non-zero to zero variable.

🔴 Affected code:
There are 25 instances of this issue:

```solidity
File:  contracts/L1/hooks/AssignmentHook.sol
172   for (uint256 i; i < _tierFees.length; ++i) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L172



```solidity
File:   contracts/L1/libs/LibProposing.sol
244        for (uint256 i; i < params.hookCalls.length; ++i) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L244


```solidity
File:  contracts/L1/provers/Guardians.sol
74      for (uint256 i; i < guardians.length; ++i) {

80      for (uint256 i = 0; i < _newGuardians.length; ++i) {

133     for (uint256 i; i < guardiansLength; ++i) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L74


```solidity
File:  contracts/L2/TaikoL2.sol
234    for (uint256 i; i < 255 && _blockId >= i + 1; ++i) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L234


```solidity
File:  contracts/automata-attestation/AutomataDcapV3Attestation.sol
80:         for (uint256 i; i < serialNumBatch.length; ++i) {

95:         for (uint256 i; i < serialNumBatch.length; ++i) {

191:         for (uint256 i; i < enclaveId.tcbLevels.length; ++i) {

214:         for (uint256 i; i < tcb.tcbLevels.length; ++i) {

240:         for (uint256 i; i < CPUSVN_LENGTH; ++i) {

259:         for (uint256 i; i < n; ++i) {

420:         for (uint256 i; i < 3; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L80


```solidity
File:  contracts/automata-attestation/lib/PEMCertChainLib.sol
54:         for (uint256 i; i < size; ++i) {

244:         for (uint256 i; i < split.length; ++i) {

354:         for (uint256 i; i < SGX_TCB_CPUSVN_SIZE + 1; ++i) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L54



```solidity
File:  contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol
153    for (uint256 i; i < encoded.length; ++i) {

281    for (uint256 i; i < 3; ++i) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L153



```solidity
File:  contracts/automata-attestation/utils/RsaVerify.sol
140:         for (uint256 i = 2; i < 2 + paddingLen; ++i) {

152:             for (uint256 i; i < digestAlgoWithParamLen; ++i) {

158:             for (uint256 i; i < digestAlgoWithParamLen; ++i) {

174:         for (uint256 i; i < _sha256.length; ++i) {

273:         for (uint256 i = 2; i < 2 + paddingLen; ++i) {

283:         for (uint256 i; i < sha1Prefix.length; ++i) {

290:         for (uint256 i; i < _sha1.length; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L140




## [G-53] require() or revert() statements that check input arguments should be at the top of the function
Checks that involve constants should come before checks that involve state variables, function calls, and calculations. By doing these checks first, the function is able to revert before wasting a Gcoldsload (2100 gas*) in a function that may ultimately revert in the unhappy case.

🔴 Affected code:
There are 4 instances of this issue:

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


## [G-54] Structs should group like types together to save gas

Structs can be more gas-efficient by grouping together members of the same type. This ordering can potentially save gas.


🔴 Affected code:
There are 12 instances of this issue:

```solidity
File: contracts/L1/TaikoData.sol
10          struct Config {
11              // ---------------------------------------------------------------------
12              // Group 1: General configs
13              // ---------------------------------------------------------------------
14              // The chain ID of the network where Taiko contracts are deployed.
15              uint64 chainId;
16              // ---------------------------------------------------------------------
17              // Group 2: Block level configs
18              // ---------------------------------------------------------------------
19              // The maximum number of proposals allowed in a single block.
20              uint64 blockMaxProposals;
21              // Size of the block ring buffer, allowing extra space for proposals.
22              uint64 blockRingBufferSize;
23              // The maximum number of verifications allowed when a block is proposed.
24              uint64 maxBlocksToVerifyPerProposal;
25              // The maximum gas limit allowed for a block.
26              uint32 blockMaxGasLimit;
27              // The maximum allowed bytes for the proposed transaction list calldata.
28              uint24 blockMaxTxListBytes;
29              // The max period in seconds that a blob can be reused for DA.
30              uint24 blobExpiry;
31              // True if EIP-4844 is enabled for DA
32              bool blobAllowedForDA;
33              // True if blob can be reused
34              bool blobReuseEnabled;
35              // ---------------------------------------------------------------------
36              // Group 3: Proof related configs
37              // ---------------------------------------------------------------------
38              // The amount of Taiko token as a prover liveness bond
39              uint96 livenessBond;
40              // ---------------------------------------------------------------------
41              // Group 4: ETH deposit related configs
42              // ---------------------------------------------------------------------
43              // The size of the ETH deposit ring buffer.
44              uint256 ethDepositRingBufferSize;
45              // The minimum number of ETH deposits allowed per block.
46              uint64 ethDepositMinCountPerBlock;
47              // The maximum number of ETH deposits allowed per block.
48              uint64 ethDepositMaxCountPerBlock;
49              // The minimum amount of ETH required for a deposit.
50              uint96 ethDepositMinAmount;
51              // The maximum amount of ETH allowed for a deposit.
52              uint96 ethDepositMaxAmount;
53              // The gas cost for processing an ETH deposit.
54              uint256 ethDepositGas;
55              // The maximum fee allowed for an ETH deposit.
56              uint256 ethDepositMaxFee;
57              // The max number of L2 blocks that can stay unsynced on L1 (a value of zero disables
58              // syncing)
59              uint8 blockSyncThreshold;
60          }


78          struct BlockParams {
79              address assignedProver;
80              address coinbase;
81              bytes32 extraData;
82              bytes32 blobHash;
83              uint24 txListByteOffset;
84              uint24 txListByteSize;
85              bool cacheBlobForReuse;
86              bytes32 parentMetaHash;
87              HookCall[] hookCalls;
88          }


94          struct BlockMetadata {
95              bytes32 l1Hash; // slot 1
96              bytes32 difficulty; // slot 2
97              bytes32 blobHash; //or txListHash (if Blob not yet supported), // slot 3
98              bytes32 extraData; // slot 4
99              bytes32 depositsHash; // slot 5
100             address coinbase; // L2 coinbase, // slot 6
101             uint64 id;
102             uint32 gasLimit;
103             uint64 timestamp; // slot 7
104             uint64 l1Height;
105             uint24 txListByteOffset;
106             uint24 txListByteSize;
107             uint16 minTier;
108             bool blobUsed;
109             bytes32 parentMetaHash; // slot 8
110         }


122         struct TransitionState {
123             bytes32 key; // slot 1, only written/read for the 1st state transition.
124             bytes32 blockHash; // slot 2
125             bytes32 stateRoot; // slot 3
126             address prover; // slot 4
127             uint96 validityBond;
128             address contester; // slot 5
129             uint96 contestBond;
130             uint64 timestamp; // slot 6 (90 bits)
131             uint16 tier;
132             uint8 contestations;
133         }


168         struct SlotB {
169             uint64 numBlocks;
170             uint64 lastVerifiedBlockId;
171             bool provingPaused;
172             uint8 __reserved1;
173             uint16 __reserved2;
174             uint32 __reserved3;
175             uint64 lastUnpausedAt;
176         }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L168:176

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol
7           struct Header {
8               bytes2 version;
9               bytes2 attestationKeyType;
10              bytes4 teeType;
11              bytes2 qeSvn;
12              bytes2 pceSvn;
13              bytes16 qeVendorId;
14              bytes20 userData;
15          }

17          struct EnclaveReport {
18              bytes16 cpuSvn;
19              bytes4 miscSelect;
20              bytes28 reserved1;
21              bytes16 attributes;
22              bytes32 mrEnclave;
23              bytes32 reserved2;
24              bytes32 mrSigner;
25              bytes reserved3; // 96 bytes
26              uint16 isvProdId;
27              uint16 isvSvn;
28              bytes reserved4; // 60 bytes
29              bytes reportData; // 64 bytes - For QEReports, this contains the hash of the concatenation
30                  // of attestation key and QEAuthData
31          }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L17:31

```solidity
File: contracts/bridge/IBridge.sol
17          struct Message {
18              // Message ID whose value is automatically assigned.
19              uint128 id;
20              // The address, EOA or contract, that interacts with this bridge.
21              // The value is automatically assigned.
22              address from;
23              // Source chain ID whose value is automatically assigned.
24              uint64 srcChainId;
25              // Destination chain ID where the `to` address lives.
26              uint64 destChainId;
27              // The owner of the message on the source chain.
28              address srcOwner;
29              // The owner of the message on the destination chain.
30              address destOwner;
31              // The destination address on the destination chain.
32              address to;
33              // Alternate address to send any refund on the destination chain.
34              // If blank, defaults to destOwner.
35              address refundTo;
36              // value to invoke on the destination chain.
37              uint256 value;
38              // Processing fee for the relayer. Zero if owner will process themself.
39              uint256 fee;
40              // gasLimit to invoke on the destination chain.
41              uint256 gasLimit;
42              // callData to invoke on the destination chain.
43              bytes data;
44              // Optional memo.
45              string memo;
46          }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L17:46

```solidity
File: contracts/team/TimelockTokenPool.sol
28          struct Grant {
29              uint128 amount;
30              // If non-zero, each TKO (1E18) will need some USD stable to purchase.
31              uint128 costPerToken;
32              // If non-zero, indicates the start time for the recipient to receive
33              // tokens, subject to an unlocking schedule.
34              uint64 grantStart;
35              // If non-zero, indicates the time after which the token to be received
36              // will be actually non-zero
37              uint64 grantCliff;
38              // If non-zero, specifies the total seconds required for the recipient
39              // to fully own all granted tokens.
40              uint32 grantPeriod;
41              // If non-zero, indicates the start time for the recipient to unlock
42              // tokens.
43              uint64 unlockStart;
44              // If non-zero, indicates the time after which the unlock will be
45              // actually non-zero
46              uint64 unlockCliff;
47              // If non-zero, specifies the total seconds required for the recipient
48              // to fully unlock all owned tokens.
49              uint32 unlockPeriod;
50          }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L28:50

```solidity
File: contracts/tokenvault/BaseNFTVault.sol
23          struct BridgeTransferOp {
24              // Destination chain ID.
25              uint64 destChainId;
26              // The owner of the bridge message on the destination chain.
27              address destOwner;
28              // Recipient address.
29              address to;
30              // Address of the token.
31              address token;
32              // IDs of the tokens to transfer.
33              uint256[] tokenIds;
34              // Amounts of tokens to transfer.
35              uint256[] amounts;
36              // Gas limit for the operation.
37              uint256 gasLimit;
38              // Processing fee for the relayer.
39              uint256 fee;
40              // Address for refund, if needed.
41              address refundTo;
42              // Optional memo.
43              string memo;
44          }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L23:44

```solidity
File: contracts/tokenvault/ERC20Vault.sol
32          struct BridgeTransferOp {
33              uint64 destChainId;
34              address destOwner;
35              address to;
36              address token;
37              uint256 amount;
38              uint256 gasLimit;
39              uint256 fee;
40              address refundTo;
41              string memo;
42          }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L32:42

```solidity
File: contracts/verifiers/IVerifier.sol
10          struct Context {
11              bytes32 metaHash;
12              bytes32 blobHash;
13              address prover;
14              uint64 blockId;
15              bool isContesting;
16              bool blobUsed;
17              address msgSender;
18          }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/IVerifier.sol#L10:18


## [G-55] `>=` costs less gas than `>`
The compiler uses opcodes `GT` and `ISZERO` for solidity code that uses `>`, but only requires `LT` for `>=`, [which saves 3 gas](https://gist.github.com/IllIllI000/3dc79d25acccfa16dee4e83ffdc6ffde).

🔴 Affected code:
There are 1 instances of this issue:
```solidity
File: contracts/L1/libs/LibDepositing.sol
93      uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L93




## [G-56] Usage of `uints`/`ints` smaller than 32 bytes (256 bits) incurs overhead

> When using elements that are smaller than 32 bytes, your contract’s gas usage may be higher. This is because the EVM operates on 32 bytes at a time. Therefore, if the element is smaller than that, the EVM must use more operations in order to reduce the size of the element from 32 bytes to the desired size.https://docs.soliditylang.org/en/v0.8.11/internals/layout_in_storage.htmlEach operation involving a `uint8` costs an extra [**22-28 gas**](https://gist.github.com/IllIllI000/9388d20c70f9a4632eb3ca7836f54977) (depending on whether the other operand is also a variable of type `uint8`) as compared to ones involving `uint256`, due to the compiler having to clear the higher bits of the memory word before operating on the `uint8`, as well as the associated stack operations of doing so. Use a larger size then downcast where needed.


🔴 Affected code:
There are 16 instances of this issue:

```solidity
File: contracts/L1/TaikoL1.sol
150             uint64 slot;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L150:150

```solidity
File: contracts/L1/libs/LibDepositing.sol
83                  uint96 fee = uint96(_config.ethDepositMaxFee.min(block.basefee * _config.ethDepositGas));

93                      uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L93:93

```solidity
File: contracts/L1/libs/LibUtils.sol
42              uint32 tid = getTransitionId(_state, blk, slot, _parentHash);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L42:42

```solidity
File: contracts/L1/libs/LibVerifying.sol
107             uint32 tid = blk.verifiedTransitionId;

117             uint64 numBlocksVerified;

234             (uint64 lastSyncedBlock,) = signalService.getSyncedChainData(
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L234:234

```solidity
File: contracts/L2/CrossChainOwned.sol
42              (uint64 txId, bytes memory txdata) = abi.decode(_data, (uint64, bytes));
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L42:42

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol
106             uint32 totalQuoteSize = 48 // header
```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L106:106

```solidity
File: contracts/automata-attestation/utils/BytesUtils.sol
332             uint8 decoded;
```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L332:332

```solidity
File: contracts/automata-attestation/utils/X509DateUtils.sol
15              uint8 offset;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L15:15

```solidity
File: contracts/bridge/Bridge.sol
89              uint64 _timestamp = _suspend ? type(uint64).max : uint64(block.timestamp);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L89:89

```solidity
File: contracts/team/TimelockTokenPool.sol
197             uint128 _amountUnlocked = amountUnlocked / 1e18; // divide first

226             uint128 amountOwned = _getAmountOwned(_grant);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L226:226

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol
134                        uint8 branchKey = uint8(key[currentKeyIndex]);

141                     uint8 prefix = uint8(path[0]);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L141:141




## [G-57] Emit Used In Loop

Emitting an event inside a loop performs a LOG op N times, where N is the loop length. Consider refactoring the code to emit the event only once at the end of loop. Gas savings should be multiplied by the average loop length.

🔴 Affected code:
There are 3 instances of this issue:

```solidity
File: contracts/bridge/Bridge.sol
93                  emit MessageSuspended(msgHash, _suspend);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L93:93

```solidity
File: contracts/verifiers/SgxVerifier.sol
109                 emit InstanceDeleted(idx, instances[idx].addr);

220                 emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220:220


## [G-58] Require()/revert() Strings Longer Than 32 Bytes Cost Extra Gas

🔴 Affected code:
There are 1 instances of this issue:
```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol
require(currentKeyIndex <= key.length, "MerkleTrie: key index exceeds total key length");
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L89

## [G-59] Using `private` rather than `public` for constants, saves gas

If needed, the values can be read from the verified contract source code, or if there are multiple values there can be a single getter function that [returns a tuple](https://github.com/code-423n4/2022-08-frax/blob/90f55a9ce4e25bceed3a74290b854341d8de6afa/src/contracts/FraxlendPair.sol#L156-L178) of the values of all currently-public constants. Saves **3406-3606 gas** in deployment gas due to the compiler not having to create non-payable getter functions for deployment calldata, not having to store the bytes of the value outside of where it's used, and not adding another entry to the method ID table

Note: these insteance are missed from bots

🔴 Affected code:
There are 2 instances of this issue:
```solidity
File: contracts/thirdparty/solmate/LibFixedPointMath.sol
uint128 public constant MAX_EXP_INPUT = 135_305_999_368_893_231_588;

uint256 public constant SCALING_FACTOR = 1e18; // For fixed point representation factor
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L8




## [G-60] Functions guaranteed to revert when called by normal users can be marked `payable`

If a function modifier such as `onlyOwner` is used, the function will revert if a normal user tries to pay the function. Marking the function as `payable` will lower the gas cost for legitimate callers because the compiler will not include checks for whether a payment was provided.

Note: these insteance are missed from bots

🔴 Affected code:
There are 2 instances of this issue:
```solidity
File: contracts/common/AddressResolver.sol
function __AddressResolver_init(address _addressManager) internal virtual onlyInitializing {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L58

## [G-61] Superfluous event fields
`block.timestamp` and `block.number` are added to event information by default so adding them manually wastes gas.

🔴 Affected code:
There are 1 instances of this issue:

```solidity
File: contracts/verifiers/SgxVerifier.sol
230     emit InstanceAdded(id, newInstance, oldInstance, block.timestamp);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L230:230


## [G-62] Use assembly to perform efficient back-to-back calls
If a similar external call is performed back-to-back, we can use assembly to reuse any function signatures and function parameters that stay the same. In addition, we can also reuse the same memory space for each function call (scratch space + free memory pointer + zero slot), which can potentially allow us to avoid memory expansion costs.
Note: In order to do this optimization safely we will cache the free memory pointer value and restore it once we are done with our function calls. We will also set the zero slot back to 0 if neccessary.
[Reffrence](https://code4rena.com/reports/2023-05-ajna#g-10-use-assembly-to-perform-efficient-back-to-back-calls)

🔴 Affected code:
There are 2 instances of this issue:


```solidity
File:  contracts/team/TimelockTokenPool.sol
219          IERC20(taikoToken).transferFrom(sharedVault, _to, amountToWithdraw);
220          IERC20(costToken).safeTransferFrom(_recipient, sharedVault, costToWithdraw);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L219-L220


```solidity
File:  contracts/tokenvault/ERC20Vault.sol
184            IBridgedERC20(btokenOld_).changeMigrationStatus(_btokenNew, false);
185            IBridgedERC20(_btokenNew).changeMigrationStatus(btokenOld_, true); 
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L164


## [G-63] Delete variables that you don't need
In Ethereum, you get a gas refund for freeing up storage space.
Deleting a variable refund 15,000 gas up to a maximum of half the gas cost of the transaction. Deleting with the delete keyword is equivalent to assigning the initial value for the data type, such as 0 for integers.

🔴 Affected code:
There are 1 instances of this issue:


```solidity
File:  contracts/L1/provers/Guardians.sol
77   delete guardians;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L77