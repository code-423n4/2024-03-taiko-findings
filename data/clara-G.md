### Gas Optimizations


| |Issue|Instances|Total Gas Saved|
|-|:-|:-|:-:|

| [[G001](#g001---use-local-variables-for-emitting)] | Use local variables for emitting | 6 | - |

| [[G002](#g002---use-assembly-to-check-for-address0)] | Use assembly to check for `address(0)` | 55 | 330 |

| [[G003](#g003---internal-functions-not-called-by-the-contract-should-be-removed-to-save-deployment-gas)] | `internal` functions not called by the contract should be removed to save deployment gas | 13 | - |
| [[G004](#g004---use-calldata-instead-of-memory-for-function-arguments-that-do-not-get-mutated)] | Use calldata instead of memory for function arguments that do not get mutated | 70 | 25200 |
| [[G005](#g005---multiple-addressid-mappings-can-be-combined-into-a-single-mapping-of-an-addressid-to-a-struct-where-appropriate)] | Multiple address/ID mappings can be combined into a single mapping of an address/ID to a struct, where appropriate | 3 | 60126 |
| [[G006](#g006---using-storage-instead-of-memory-for-structsarrays-saves-gas)] | Using storage instead of `memory` for structs/arrays saves gas | 2 | 8400 |
| [[G007](#g007---multiple-accesses-of-a-mappingarray-should-use-a-local-variable-cache)] | Multiple accesses of a mapping/array should use a local variable cache | 45 | 1890 |
| [[G008](#g008---internal-functions-only-called-once-can-be-inlined-to-save-gas)] | Internal functions only called once can be inlined to save gas | 23 | 460 |
| [[G009](#g009---add-unchecked--for-subtractions-where-the-operands-cannot-underflow-because-of-a-previous-require-or-if-statement)] | Add unchecked {} for subtractions where the operands cannot underflow because of a previous require() or if-statement | 2 | 170 |
| [[G010](#g010---optimize-names-to-save-gas)] | Optimize names to save gas | 73 | 1606 |
| [[G011](#g011---structs-should-group-like-types-together-to-save-gas)] | Structs should group like types together to save gas | 12 | - |
| [[G012](#g012---the-result-of-function-calls-should-be-cached-rather-than-re-calling-the-function)] | The result of function calls should be cached rather than re-calling the function | 33 | 693 |

| [[G013](#g013---stack-variable-used-as-a-cheaper-cache-for-a-state-variable-is-only-used-once)] | Stack variable used as a cheaper cache for a state variable is only used once | 2 | 536 |
| [[G014](#g014---require-or-revert-statements-that-check-input-arguments-should-be-at-the-top-of-the-function)] | require() or revert() statements that check input arguments should be at the top of the function | 4 | - |
| [[G015](#g015---x--y-costs-more-gas-than-x--x--y-for-state-variables)] | `<x> += <y>` costs more gas than `<x> = <x> + <y>` for state variables | 6 | 678 |
| [[G016](#g016---constructors-can-be-marked-payable)] | Constructors can be marked payable | 3 | 63 |
| [[G017](#g017----costs-less-gas-than-)] | `>=` costs less gas than `>` | 1 | 3 |
| [[G018](#g018---use-assembly-to-emit-events)] | Use assembly to emit events | 55 | - |
| [[G019](#g019---state-variables-only-set-in-the-constructor-should-be-declared-immutable)] | State variables only set in the constructor should be declared `immutable` | 2 | 40000 |
| [[G020](#g020---use-uint2561uint2562-instead-for-true-and-false-boolean-states)] | Use `uint256(1)`/`uint256(2)` instead for `true` and `false` boolean states | 9 | 153900 |
| [[G021](#g021---superfluous-event-fields)] | Superfluous event fields | 1 | - |
| [[G022](#g022---ii-should-be-uncheckediuncheckedi-when-it-is-not-possible-for-them-to-overflow-as-is-the-case-when-used-in-for--and-while-loops)] | `++i`/`i++` should be `unchecked{++i}`/`unchecked{i++}` when it is not possible for them to overflow, as is the case when used in `for`- and `while`-loops | 39 | 2340 |
| [[G023](#g023---usage-of-uintsints-smaller-than-32-bytes-256-bits-incurs-overhead)] | Usage of `uints`/`ints` smaller than 32 bytes (256 bits) incurs overhead | 16 | 160 |
| [[G024](#g024---consider-activating-via-ir-for-deploying)] | Consider activating `via-ir` for deploying | 1 | - |
| [[G025](#g025---empty-blocks-should-be-removed-or-emit-something)] | Empty Blocks Should Be Removed Or Emit Something | 4 | 16024 |
| [[G026](#g026---emit-used-in-loop)] | Emit Used In Loop | 3 | - |
| [[G027](#g027---inverting-the-condition-of-an-if-else-statement)] | Inverting the condition of an if-else-statement | 2 | - |
| [[G028](#g028---unchecked--can-be-used-on-the-division-of-two-uints-in-order-to-save-gas)] | `unchecked {}` can be used on the division of two `uints` in order to save gas | 15 | - |
| [[G029](#g029---private-functions-used-once-can-be-inlined)] | Private functions used once can be inlined | 41 | - |
| [[G030](#g030---use-assembly-to-calculate-hashes-to-save-gas)] | Use assembly to calculate hashes to save gas | 28 | 2240 |
| [[G031](#g031---unused-named-return-variables-without-optimizer-waste-gas)] | Unused named return variables without optimizer waste gas | 10 | - |
| [[G032](#g032---avoid-updating-storage-when-the-value-hasnt-changed)] | Avoid updating storage when the value hasn't changed | 21 | 60900 |
| [[G033](#g033---do-not-calculate-constants)] | Do not calculate constants | 2 | - |
| [[G034](#g034---duplicated-requirerevert-checks-should-be-refactored-to-a-modifier-or-function)] | Duplicated `require()`/`revert()` checks should be refactored to a modifier or function | 3 | - |
| [[G035](#g035---the-use-of-a-logical-and-in-place-of-double-if-is-slightly-less-gas-efficient-in-instances-where-there-isnt-a-corresponding-else-statement-for-the-given-if-statement)] | The use of a logical AND in place of double if is slightly less gas efficient in instances where there isn't a corresponding else statement for the given if statement | 23 | - |
| [[G036](#g036---use-the-inputsresults-of-assignments-rather-than-re-reading-state-variables)] | Use the inputs/results of assignments rather than re-reading state variables | 12 | - |
| [[G037](#g037---assigning-state-variables-directly-with-named-struct-constructors-wastes-gas)] | Assigning state variables directly with named struct constructors wastes gas | 4 | - |
| [[G038](#g038---avoid-fetching-a-low-level-calls-return-data-by-using-assembly)] | Avoid fetching a low-level call's return data by using assembly | 1 | - |
| [[G039](#g039---using-msg-globals-directly-rather-than-caching-the-value-saves-gas)] | Using msg globals directly, rather than caching the value, saves gas | 5 | - |
| [[G040](#g040---state-variable-read-in-a-loop)] | State variable read in a loop | 15 | - |
| [[G041](#g041---storage-re-read-via-storage-pointer)] | Storage re-read via storage pointer | 4 | - |
| [[G042](#g042---state-variables-only-set-in-the-constructor-should-be-declared-immutable)] | State variables only set in the constructor should be declared immutable | 2 | - |
| [[G043](#g043---structs-can-be-packed-into-fewer-storage-slots)] | Structs can be packed into fewer storage slots | 3 | - |


## G001 - Use local variables for emitting:

Use the function/modifier's local copy of the state variable, rather than incurring an extra Gwarmaccess (100 gas). In the unlikely event that the state variable hasn't already been used by the function/modifier, consider whether it is really necessary to include it in the event, given the fact that it incurs a Gcoldsload (2100 gas), or whether it can be passed in to or back out of the functions that do use it


<details>
<summary>Click to show 6 findings</summary>

```solidity
File: contracts/L1/provers/Guardians.sol


95              emit GuardiansUpdated(version, _newGuardians);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/provers/Guardians.sol#L95:95

```solidity
File: contracts/L2/TaikoL2.sol


157             emit Anchored(blockhash(parentId), gasExcess);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L2/TaikoL2.sol#L157:157

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol


63                  emit MigratedTo(migratingAddress, _account, _amount);


80                  emit MigratedTo(migratingAddress, _account, _amount);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L80:80

```solidity
File: contracts/verifiers/SgxVerifier.sol


109                 emit InstanceDeleted(idx, instances[idx].addr);


220                 emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220:220

</details>



## G002 - Use assembly to check for `address(0)`:

*Saves 6 gas per instance*


<details>
<summary>Click to show 55 findings</summary>

```solidity
File: contracts/L1/hooks/AssignmentHook.sol


109             if (assignment.feeToken == address(0)) {


120             if (input.tip != 0 && block.coinbase != address(0)) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L120:120

```solidity
File: contracts/L1/libs/LibDepositing.sol


44              address recipient_ = _recipient == address(0) ? msg.sender : _recipient;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L44:44

```solidity
File: contracts/L1/libs/LibProposing.sol


81              if (params.assignedProver == address(0)) {


85              if (params.coinbase == address(0)) {


310                 if (proposerOne != address(0) && msg.sender != proposerOne) {


316             return proposer == address(0) || msg.sender == proposer;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L316:316

```solidity
File: contracts/L1/libs/LibProving.sol


163                 if (verifier != address(0)) {


224                     assert(ts.validityBond == 0 && ts.contestBond == 0 && ts.contester == address(0));


239                     if (ts.contester != address(0)) revert L1_ALREADY_CONTESTED();


363             if (_ts.contester != address(0)) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibProving.sol#L363:363

```solidity
File: contracts/L1/libs/LibVerifying.sol


145                     if (ts.contester != address(0)) {


148                         if (tierProvider == address(0)) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L148:148

```solidity
File: contracts/L1/provers/Guardians.sol


82                  if (guardian == address(0)) revert INVALID_GUARDIAN();


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/provers/Guardians.sol#L82:82

```solidity
File: contracts/L2/TaikoL2.sol


172             if (_to == address(0)) revert L2_INVALID_PARAM();


173             if (_token == address(0)) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L2/TaikoL2.sol#L173:173

```solidity
File: contracts/bridge/Bridge.sol


124             if (_message.srcOwner == address(0) || _message.destOwner == address(0)) {


124             if (_message.srcOwner == address(0) || _message.destOwner == address(0)) {


270                     _message.to == address(0) || _message.to == address(this)


291                     _message.refundTo == address(0) ? _message.destOwner : _message.refundTo;


398             enabled_ = destBridge_ != address(0);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/bridge/Bridge.sol#L398:398

```solidity
File: contracts/common/AddressResolver.sol


81              if (addressManager == address(0)) revert RESOLVER_INVALID_MANAGER();


85              if (!_allowZeroAddress && addr_ == address(0)) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/common/AddressResolver.sol#L85:85

```solidity
File: contracts/common/EssentialContract.sol


105             if (_addressManager == address(0)) revert ZERO_ADDR_MANAGER();


110             _transferOwnership(_owner == address(0) ? msg.sender : _owner);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/common/EssentialContract.sol#L110:110

```solidity
File: contracts/libs/LibAddress.sol


24              if (_to == address(0)) revert ETH_TRANSFER_FAILED();


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/libs/LibAddress.sol#L24:24

```solidity
File: contracts/signal/SignalService.sol


36              if (_app == address(0)) revert SS_INVALID_SENDER();


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/signal/SignalService.sol#L36:36

```solidity
File: contracts/team/TimelockTokenPool.sol


121             if (_taikoToken == address(0)) revert INVALID_PARAM();


124             if (_costToken == address(0)) revert INVALID_PARAM();


127             if (_sharedVault == address(0)) revert INVALID_PARAM();


136             if (_recipient == address(0)) revert INVALID_PARAM();


169             if (_to == address(0)) revert INVALID_PARAM();


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L169:169

```solidity
File: contracts/tokenvault/BaseNFTVault.sol


149             if (_op.token == address(0)) revert VAULT_INVALID_TOKEN();


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L149:149

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol


102             return migratingAddress != address(0) && !migratingInbound;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L102:102

```solidity
File: contracts/tokenvault/ERC1155Vault.sol


64                  destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,


108             if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();


249                 if (bridgedToCanonical[_op.token].addr != address(0)) {


293             if (btoken_ == address(0)) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L293:293

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L397:397

```solidity
File: contracts/tokenvault/ERC721Vault.sol


50                  destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,


91              if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();


195                 if (bridgedToCanonical[_op.token].addr != address(0)) {


230             if (btoken_ == address(0)) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L230:230

```solidity
File: contracts/tokenvault/LibBridgedToken.sol


21                  _srcToken == address(0) || _srcChainId == 0 || _srcChainId == block.chainid


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L21:21

```solidity
File: contracts/verifiers/SgxVerifier.sol


107                 if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();


124             if (automataDcapAttestation == address(0)) {


215                 if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();


234             if (instance == address(0)) return false;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L234:234

</details>

## G003 - `internal` functions not called by the contract should be removed to save deployment gas:

If the functions are required by an interface, the contract should inherit from that interface and use the override keyword


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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/TaikoToken.sol#L94:103

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L153:160

```solidity
File: contracts/common/AddressManager.sol


    function _authorizePause(address) internal pure override {
        revert AM_UNSUPPORTED();
    }

```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/common/AddressManager.sol#L58:60

```solidity
File: contracts/signal/SignalService.sol


    function _authorizePause(address) internal pure override {
        revert SS_UNSUPPORTED();
    }

```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/signal/SignalService.sol#L231:233

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L152:161

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L47:50

</details>

## G004 - Use calldata instead of memory for function arguments that do not get mutated:

Mark data types as `calldata` instead of `memory` where possible. This makes it so that the data is not automatically loaded into memory. If the data passed into the function does not need to be changed (like updating values in an array), it can be passed in as `calldata`. The one exception to this is if the argument must later be passed into another function that takes an argument that specifies `memory` storage.


<details>
<summary>Click to show 70 findings</summary>

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L49:49

```solidity
File: contracts/L1/hooks/AssignmentHook.sol


65              bytes memory _data


63              TaikoData.Block memory _blk,


64              TaikoData.BlockMetadata memory _meta,


138             ProverAssignment memory _assignment,


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L138:138

```solidity
File: contracts/L1/hooks/IHook.sol


14              TaikoData.Block memory _blk,


16              bytes memory _data


15              TaikoData.BlockMetadata memory _meta,


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/hooks/IHook.sol#L15:15

```solidity
File: contracts/L1/libs/LibUtils.sol


54              TaikoData.Config memory _config,


25              TaikoData.Config memory _config,


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L25:25

```solidity
File: contracts/L1/libs/LibVerifying.sol


49              TaikoData.Config memory _config,


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L49:49

```solidity
File: contracts/L1/provers/Guardians.sol


54              address[] memory _newGuardians,


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/provers/Guardians.sol#L54:54

```solidity
File: contracts/L2/TaikoL2EIP1559Configurable.sol


26              Config memory _newConfig,


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L26:26

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L49:49

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol


41              bytes memory pemChain,


75              bytes memory der,


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L75:75

```solidity
File: contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol


37              bytes memory pemChain,


45              bytes memory der,


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L45:45

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L56:56

```solidity
File: contracts/bridge/Bridge.sol


449         function hashMessage(Message memory _message) public pure returns (bytes32) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/bridge/Bridge.sol#L449:449

```solidity
File: contracts/bridge/IBridge.sol


155         function hashMessage(Message memory _message) external pure returns (bytes32);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/bridge/IBridge.sol#L155:155

```solidity
File: contracts/team/TimelockTokenPool.sol


168         function withdraw(address _to, bytes memory _sig) external {


135         function grant(address _recipient, Grant memory _grant) external onlyOwner {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L135:135

```solidity
File: contracts/tokenvault/BridgedERC1155.sol


43              string memory _symbol,


85              uint256[] memory _tokenIds,


86              uint256[] memory _amounts


44              string memory _name


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L44:44

```solidity
File: contracts/tokenvault/BridgedERC20.sol


59              string memory _name


58              string memory _symbol,


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L58:58

```solidity
File: contracts/tokenvault/BridgedERC721.sol


37              string memory _name


36              string memory _symbol,


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L36:36

```solidity
File: contracts/tokenvault/ERC1155Vault.sol


39          function sendToken(BridgeTransferOp memory _op)


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L39:39

```solidity
File: contracts/tokenvault/ERC721Vault.sol


26          function sendToken(BridgeTransferOp memory _op)


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L26:26

```solidity
File: contracts/verifiers/SgxVerifier.sol


172             TaikoData.Transition memory _tran,


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L172:172

</details>

## G005 - Multiple address/ID mappings can be combined into a single mapping of an address/ID to a struct, where appropriate:

Saves a storage slot for the mapping. Depending on the circumstances and sizes of types, can avoid a Gsset (20000 gas) per mapping combined. Reads and subsequent writes can also be cheaper when a function requires both values and they both fit in the same storage slot. Finally, if both fields are accessed in the same function, can save ~42 gas per access due to not having to recalculate the key's keccak256 hash (Gkeccak256 - 30 gas) and that calculation's associated stack operations.


```solidity
File: contracts/L1/TaikoData.sol


181             mapping(uint64 blockId_mod_blockRingBufferSize => Block blk) blocks;
182             // Indexing to transition ids (ring buffer not possible)
183             mapping(uint64 blockId => mapping(bytes32 parentHash => uint32 transitionId)) transitionIds;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/TaikoData.sol#L181:183

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/bridge/Bridge.sol#L35:46

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol


22          mapping(address addr => uint256 amountClaimed) public claimedAmount;
23      
24          /// @notice Represents the already withdrawn amount.
25          mapping(address addr => uint256 amountWithdrawn) public withdrawnAmount;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L22:25

## G006 - Using storage instead of `memory` for structs/arrays saves gas:

When fetching data from a storage location, assigning the data to a memory variable causes all fields of the struct/array to be read from storage, which incurs a Gcoldsload (2100 gas) for each field of the struct/array. If the fields are read from the new memory variable, they incur an additional MLOAD rather than a cheap stack read. Instead of declearing the variable with the memory keyword, declaring the variable with the storage keyword and caching any fields that need to be re-read in stack variables, will be much cheaper, only incuring the Gcoldsload for the fields actually read. The only time it makes sense to read the whole struct/array into a memory variable, is if the full struct/array is being returned by the function, is being passed to a function that requires memory, or if the array/struct is being read from another memory array/struct


```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol


180             EnclaveIdStruct.EnclaveId memory enclaveId = qeIdentity;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L180:180

```solidity
File: contracts/tokenvault/ERC20Vault.sol


171                 CanonicalERC20 memory ctoken = bridgedToCanonical[btokenOld_];


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L171:171

## G007 - Multiple accesses of a mapping/array should use a local variable cache:

The instances below point to the second+ access of a value inside a mapping/array, within a function. Caching a mapping's value in a local storage or calldata variable when the value is accessed multiple times, saves ~42 gas per access due to not having to recalculate the key's keccak256 hash (Gkeccak256 - 30 gas) and that calculation's associated stack operations. Caching an array's struct avoids recalculating the array offsets into memory/calldata


<details>
<summary>Click to show 45 findings</summary>

```solidity
File: contracts/L1/hooks/AssignmentHook.sol


173                 if (_tierFees[i].tier == _tierId) return _tierFees[i].fee;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L173:173

```solidity
File: contracts/L1/libs/LibDepositing.sol


101                         deposits_[i].amount -= _fee;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L101:101

```solidity
File: contracts/L1/libs/LibProposing.sol


257                     prevHook = params.hookCalls[i].hook;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L257:257

```solidity
File: contracts/L1/libs/LibProving.sol


345                 ts_ = _state.transitions[slot][tid_];


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibProving.sol#L345:345

```solidity
File: contracts/L1/libs/LibVerifying.sol


130                     blk = _state.blocks[slot];


140                     TaikoData.TransitionState storage ts = _state.transitions[slot][tid];


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L140:140

```solidity
File: contracts/L1/provers/Guardians.sol


88                  guardianIds[guardian] = guardians.length;


119             uint256 _approval = _approvals[version][_hash];


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/provers/Guardians.sol#L119:119

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol


84                  _serialNumIsRevoked[index][serialNumBatch[i]] = true;


84                  _serialNumIsRevoked[index][serialNumBatch[i]] = true;


99                  delete _serialNumIsRevoked[index][serialNumBatch[i]];


99                  delete _serialNumIsRevoked[index][serialNumBatch[i]];


286                     certs[i].tbsCertificate, certs[i].signature, issuer.pubKey


271                         certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.PCK)][certs[i]
272                             .serialNumber];


472                     parsedQuoteCerts[0].pubKey,


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L472:472

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol


282                 quoteCerts[i] = Base64.decode(string(quoteCerts[i]));


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L282:282

```solidity
File: contracts/automata-attestation/utils/Asn1Decode.sol


143             require(der[ptr.ixf()] & 0x80 == 0, "Not positive");


158             if (der[ptr.ixf()] == 0) {


182             require(der[ptr.ixf()] == 0x00, "ixf Not 0");


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L182:182

```solidity
File: contracts/automata-attestation/utils/X509DateUtils.sol


21                  yrs += (uint8(x509Time[0]) - 48) * 1000 + (uint8(x509Time[1]) - 48) * 100;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L21:21

```solidity
File: contracts/bridge/Bridge.sol


110             addressBanned[_addr] = _ban;


191                 messageStatus[msgHash] = Status.RECALLED;


190                 delete proofReceipt[msgHash];


264                 delete proofReceipt[msgHash];


518             messageStatus[_msgHash] = _status;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/bridge/Bridge.sol#L518:518

```solidity
File: contracts/common/AddressManager.sol


49              __addresses[_chainId][_name] = _newAddress;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/common/AddressManager.sol#L49:49

```solidity
File: contracts/signal/SignalService.sol


58              isAuthorized[_addr] = _authorize;


248                 topBlockId[_chainId][_kind] = _blockId;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/signal/SignalService.sol#L248:248

```solidity
File: contracts/team/TimelockTokenPool.sol


142             recipients[_recipient].grant = _grant;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L142:142

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol


73              isClaimed[hash] = true;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L73:73

```solidity
File: contracts/thirdparty/optimism/rlp/RLPWriter.sol


45                  out_[0] = bytes1(uint8(lenLen) + uint8(_offset) + 55);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L45:45

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol


188                         currentNodeID = _getNodeID(currentNode.decoded[1]);


209                 proof_[i] = TrieNode({ encoded: _proof[i], decoded: RLPReader.readList(_proof[i]) });


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L209:209

```solidity
File: contracts/tokenvault/ERC1155Vault.sol


250                     ctoken_ = bridgedToCanonical[_op.token];


274                             amount: _op.amounts[i],


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L274:274

```solidity
File: contracts/tokenvault/ERC20Vault.sol


188             bridgedToCanonical[_btokenNew] = _ctoken;


189             canonicalToBridged[_ctoken.chainId][_ctoken.addr] = _btokenNew;


359                 ctoken_ = bridgedToCanonical[_token];


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L359:359

```solidity
File: contracts/tokenvault/ERC721Vault.sol


176                     BridgedERC721(token_).mint(_to, _tokenIds[i]);


196                     ctoken_ = bridgedToCanonical[_op.token];


211                         t.safeTransferFrom(_user, address(this), _op.tokenIds[i]);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L211:211

```solidity
File: contracts/verifiers/SgxVerifier.sol


111                 delete instances[idx];


213                 addressRegistered[_instances[i]] = true;


220                 emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);


237                 && block.timestamp <= instances[id].validSince + INSTANCE_EXPIRY;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L237:237

</details>

## G008 - Internal functions only called once can be inlined to save gas:

Not inlining costs 20 to 40 gas because of two extra JUMP instructions and additional stack operations needed for function calls.


<details>
<summary>Click to show 23 findings</summary>

```solidity
File: contracts/L1/TaikoL1.sol


220         function _authorizePause(address)


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/TaikoL1.sol#L220:220

```solidity
File: contracts/L1/TaikoToken.sol


105         function _mint(


115         function _burn(


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/TaikoToken.sol#L115:115

```solidity
File: contracts/L1/libs/LibDepositing.sol


122         function canDepositEthToL2(


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L122:122

```solidity
File: contracts/L1/libs/LibProposing.sol


287         function isBlobReusable(


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L287:287

```solidity
File: contracts/L1/libs/LibUtils.sol


70          function getTransitionId(


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L70:70

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol


126         function _attestationTcbIsValid(TCBInfoStruct.TCBStatus status)


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L126:126

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol


267         function parseCerificationChainBytes(


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L267:267

```solidity
File: contracts/automata-attestation/utils/BytesUtils.sol


56          function compare(


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L56:56

```solidity
File: contracts/automata-attestation/utils/RsaVerify.sol


43          function pkcs1Sha256(


212         function pkcs1Sha1(


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L212:212

```solidity
File: contracts/automata-attestation/utils/X509DateUtils.sol


34          function toUnixTimestamp(


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L34:34

```solidity
File: contracts/common/EssentialContract.sol


109         function __Essential_init(address _owner) internal virtual {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/common/EssentialContract.sol#L109:109

```solidity
File: contracts/libs/LibAddress.sol


42          function sendEther(address _to, uint256 _amount) internal {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/libs/LibAddress.sol#L42:42

```solidity
File: contracts/signal/SignalService.sol


206         function _verifyHopProof(


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/signal/SignalService.sol#L206:206

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol


77          function _verifyMerkleProof(


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L77:77

```solidity
File: contracts/thirdparty/optimism/Bytes.sol


91          function slice(bytes memory _bytes, uint256 _start) internal pure returns (bytes memory) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L91:91

```solidity
File: contracts/thirdparty/optimism/rlp/RLPReader.sol


102         function readList(bytes memory _in) internal pure returns (RLPItem[] memory out_) {


128         function readBytes(bytes memory _in) internal pure returns (bytes memory out_) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L128:128

```solidity
File: contracts/thirdparty/optimism/rlp/RLPWriter.sol


13          function writeBytes(bytes memory _in) internal pure returns (bytes memory out_) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L13:13

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol


68          function get(


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L68:68

```solidity
File: contracts/tokenvault/BridgedERC20.sol


163         function _mint(


173         function _burn(


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L173:173

</details>

## G009 - Add unchecked {} for subtractions where the operands cannot underflow because of a previous require() or if-statement:

`require(a <= b); x = b - a` => `require(a <= b); unchecked { x = b - a }`


```solidity
File: contracts/automata-attestation/utils/BytesUtils.sol


93                          mask = ~(2 ** (8 * (32 - shortest + idx)) - 1);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L93:93

```solidity
File: contracts/thirdparty/optimism/Bytes.sol


95              return slice(_bytes, _start, _bytes.length - _start);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L95:95

## G010 - Optimize names to save gas:

public/external function names and public member variable names can be optimized to save gas.


<details>
<summary>Click to show 73 findings</summary>

```solidity
File: contracts/L1/ITaikoL1.sol


8       interface ITaikoL1 {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/ITaikoL1.sol#L8:8

```solidity
File: contracts/L1/TaikoL1.sol


22      contract TaikoL1 is EssentialContract, ITaikoL1, TaikoEvents, TaikoErrors {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/TaikoL1.sol#L22:22

```solidity
File: contracts/L1/TaikoToken.sol


15      contract TaikoToken is EssentialContract, ERC20SnapshotUpgradeable, ERC20VotesUpgradeable {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/TaikoToken.sol#L15:15

```solidity
File: contracts/L1/gov/TaikoGovernor.sol


16      contract TaikoGovernor is


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L16:16

```solidity
File: contracts/L1/gov/TaikoTimelockController.sol


9       contract TaikoTimelockController is EssentialContract, TimelockControllerUpgradeable {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L9:9

```solidity
File: contracts/L1/hooks/AssignmentHook.sol


14      contract AssignmentHook is EssentialContract, IHook {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L14:14

```solidity
File: contracts/L1/hooks/IHook.sol


8       interface IHook {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/hooks/IHook.sol#L8:8

```solidity
File: contracts/L1/libs/LibDepositing.sol


12      library LibDepositing {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L12:12

```solidity
File: contracts/L1/libs/LibProposing.sol


15      library LibProposing {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L15:15

```solidity
File: contracts/L1/libs/LibProving.sol


16      library LibProving {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibProving.sol#L16:16

```solidity
File: contracts/L1/libs/LibUtils.sol


9       library LibUtils {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L9:9

```solidity
File: contracts/L1/libs/LibVerifying.sol


16      library LibVerifying {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L16:16

```solidity
File: contracts/L1/provers/GuardianProver.sol


10      contract GuardianProver is Guardians {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L10:10

```solidity
File: contracts/L1/provers/Guardians.sol


9       abstract contract Guardians is EssentialContract {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/provers/Guardians.sol#L9:9

```solidity
File: contracts/L1/tiers/DevnetTierProvider.sol


10      contract DevnetTierProvider is EssentialContract, ITierProvider {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L10:10

```solidity
File: contracts/L1/tiers/ITierProvider.sol


7       interface ITierProvider {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L7:7

```solidity
File: contracts/L1/tiers/MainnetTierProvider.sol


10      contract MainnetTierProvider is EssentialContract, ITierProvider {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L10:10

```solidity
File: contracts/L1/tiers/TestnetTierProvider.sol


10      contract TestnetTierProvider is EssentialContract, ITierProvider {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L10:10

```solidity
File: contracts/L2/CrossChainOwned.sol


14      abstract contract CrossChainOwned is EssentialContract, IMessageInvocable {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L14:14

```solidity
File: contracts/L2/Lib1559Math.sol


10      library Lib1559Math {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L2/Lib1559Math.sol#L10:10

```solidity
File: contracts/L2/TaikoL2.sol


21      contract TaikoL2 is CrossChainOwned {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L2/TaikoL2.sol#L21:21

```solidity
File: contracts/L2/TaikoL2EIP1559Configurable.sol


9       contract TaikoL2EIP1559Configurable is TaikoL2 {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L9:9

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol


22      contract AutomataDcapV3Attestation is IAttestation {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L22:22

```solidity
File: contracts/automata-attestation/interfaces/IAttestation.sol


8       interface IAttestation {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/interfaces/IAttestation.sol#L8:8

```solidity
File: contracts/automata-attestation/interfaces/ISigVerifyLib.sol


6       interface ISigVerifyLib {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L6:6

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol


12      contract PEMCertChainLib is IPEMCertChainLib {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L12:12

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol


11      library V3Parser {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L11:11

```solidity
File: contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol


6       interface IPEMCertChainLib {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L6:6

```solidity
File: contracts/automata-attestation/utils/Asn1Decode.sol


12      library NodePtr {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L12:12

```solidity
File: contracts/automata-attestation/utils/BytesUtils.sol


8       library BytesUtils {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L8:8

```solidity
File: contracts/automata-attestation/utils/RsaVerify.sol


34      library RsaVerify {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L34:34

```solidity
File: contracts/automata-attestation/utils/SHA1.sol


10      library SHA1 {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/utils/SHA1.sol#L10:10

```solidity
File: contracts/automata-attestation/utils/SigVerifyLib.sol


15      contract SigVerifyLib is ISigVerifyLib {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L15:15

```solidity
File: contracts/automata-attestation/utils/X509DateUtils.sol


7       library X509DateUtils {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L7:7

```solidity
File: contracts/bridge/Bridge.sol


16      contract Bridge is EssentialContract, IBridge {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/bridge/Bridge.sol#L16:16

```solidity
File: contracts/bridge/IBridge.sol


8       interface IBridge {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/bridge/IBridge.sol#L8:8

```solidity
File: contracts/common/AddressManager.sol


10      contract AddressManager is EssentialContract, IAddressManager {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/common/AddressManager.sol#L10:10

```solidity
File: contracts/common/AddressResolver.sol


11      abstract contract AddressResolver is IAddressResolver, Initializable {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/common/AddressResolver.sol#L11:11

```solidity
File: contracts/common/EssentialContract.sol


10      abstract contract EssentialContract is UUPSUpgradeable, Ownable2StepUpgradeable, AddressResolver {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/common/EssentialContract.sol#L10:10

```solidity
File: contracts/common/IAddressManager.sol


7       interface IAddressManager {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/common/IAddressManager.sol#L7:7

```solidity
File: contracts/common/IAddressResolver.sol


13      interface IAddressResolver {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/common/IAddressResolver.sol#L13:13

```solidity
File: contracts/libs/Lib4844.sol


8       library Lib4844 {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/libs/Lib4844.sol#L8:8

```solidity
File: contracts/libs/LibAddress.sol


13      library LibAddress {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/libs/LibAddress.sol#L13:13

```solidity
File: contracts/libs/LibMath.sol


7       library LibMath {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/libs/LibMath.sol#L7:7

```solidity
File: contracts/libs/LibTrieProof.sol


15      library LibTrieProof {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/libs/LibTrieProof.sol#L15:15

```solidity
File: contracts/signal/ISignalService.sol


12      interface ISignalService {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/signal/ISignalService.sol#L12:12

```solidity
File: contracts/signal/SignalService.sol


14      contract SignalService is EssentialContract, ISignalService {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/signal/SignalService.sol#L14:14

```solidity
File: contracts/team/TimelockTokenPool.sol


25      contract TimelockTokenPool is EssentialContract {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L25:25

```solidity
File: contracts/team/airdrop/ERC20Airdrop.sol


11      contract ERC20Airdrop is MerkleClaimable {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L11:11

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol


12      contract ERC20Airdrop2 is MerkleClaimable {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L12:12

```solidity
File: contracts/team/airdrop/ERC721Airdrop.sol


9       contract ERC721Airdrop is MerkleClaimable {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L9:9

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol


10      abstract contract MerkleClaimable is EssentialContract {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L10:10

```solidity
File: contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol


5       library ExcessivelySafeCall {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L5:5

```solidity
File: contracts/thirdparty/optimism/Bytes.sol


6       library Bytes {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L6:6

```solidity
File: contracts/thirdparty/optimism/rlp/RLPReader.sol


9       library RLPReader {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L9:9

```solidity
File: contracts/thirdparty/optimism/rlp/RLPWriter.sol


9       library RLPWriter {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L9:9

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol


11      library MerkleTrie {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L11:11

```solidity
File: contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol


9       library SecureMerkleTrie {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L9:9

```solidity
File: contracts/thirdparty/solmate/LibFixedPointMath.sol


6       library LibFixedPointMath {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L6:6

```solidity
File: contracts/tokenvault/BaseVault.sol


12      abstract contract BaseVault is


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L12:12

```solidity
File: contracts/tokenvault/BridgedERC1155.sol


14      contract BridgedERC1155 is EssentialContract, IERC1155MetadataURIUpgradeable, ERC1155Upgradeable {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L14:14

```solidity
File: contracts/tokenvault/BridgedERC20.sol


15      contract BridgedERC20 is


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L15:15

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol


9       abstract contract BridgedERC20Base is EssentialContract, IBridgedERC20 {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L9:9

```solidity
File: contracts/tokenvault/BridgedERC721.sol


12      contract BridgedERC721 is EssentialContract, ERC721Upgradeable {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L12:12

```solidity
File: contracts/tokenvault/ERC1155Vault.sol


16      interface IERC1155NameAndSymbol {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L16:16

```solidity
File: contracts/tokenvault/ERC20Vault.sol


18      contract ERC20Vault is BaseVault {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L18:18

```solidity
File: contracts/tokenvault/ERC721Vault.sol


16      contract ERC721Vault is BaseNFTVault, IERC721Receiver {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L16:16

```solidity
File: contracts/tokenvault/IBridgedERC20.sol


10      interface IBridgedERC20 {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/IBridgedERC20.sol#L10:10

```solidity
File: contracts/tokenvault/LibBridgedToken.sol


8       library LibBridgedToken {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L8:8

```solidity
File: contracts/tokenvault/adapters/USDCAdapter.sol


8       interface IUSDC {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L8:8

```solidity
File: contracts/verifiers/GuardianVerifier.sol


10      contract GuardianVerifier is EssentialContract, IVerifier {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L10:10

```solidity
File: contracts/verifiers/IVerifier.sol


9       interface IVerifier {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/verifiers/IVerifier.sol#L9:9

```solidity
File: contracts/verifiers/SgxVerifier.sol


19      contract SgxVerifier is EssentialContract, IVerifier {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L19:19

</details>

## G011 - Structs should group like types together to save gas:

Structs can be more gas-efficient by grouping together members of the same type. This ordering can potentially save gas.


<details>
<summary>Click to show 12 findings</summary>

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/TaikoData.sol#L168:176

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L17:31

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/bridge/IBridge.sol#L17:46

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L28:50

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L23:44

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L32:42

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/verifiers/IVerifier.sol#L10:18

</details>

## G012 - The result of function calls should be cached rather than re-calling the function:

Caching the result of a function call in a local variable when the function is called multiple times can save gas due to avoiding the need to execute the function code multiple times.


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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L318:318

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L184:184

</details>



## G013 - Stack variable used as a cheaper cache for a state variable is only used once:

If the variable is only accessed once, it's cheaper to use the state variable directly that one time, and save the 3 gas the extra stack assignment would spend.


```solidity
File: contracts/L1/provers/Guardians.sol


133                 for (uint256 i; i < guardiansLength; ++i) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/provers/Guardians.sol#L133:133

```solidity
File: contracts/team/TimelockTokenPool.sol


152             uint128 amountVoided = _voidGrant(r.grant);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L152:152

## G014 - require() or revert() statements that check input arguments should be at the top of the function:

Checks that involve constants should come before checks that involve state variables, function calls, and calculations. By doing these checks first, the function is able to revert before wasting a Gcoldsload (2100 gas*) in a function that may ultimately revert in the unhappy case.


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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L87:90

</details>

## G015 - `<x> += <y>` costs more gas than `<x> = <x> + <y>` for state variables:

Using the addition operator instead of plus-equals saves 113 gas


<details>
<summary>Click to show 6 findings</summary>

```solidity
File: contracts/team/TimelockTokenPool.sol


141             totalAmountGranted += _grant.amount;


156             totalAmountVoided += amountVoided;


216             totalAmountWithdrawn += amountToWithdraw;


217             totalCostPaid += costToWithdraw;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L217:217

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol


83              claimedAmount[user] += amount;


90              withdrawnAmount[user] += amount;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L90:90

</details>

## G016 - Constructors can be marked payable:

Payable functions cost less gas to execute, since the compiler does not have to add extra checks to ensure that a payment wasn't provided. A constructor can safely be marked as payable, since only the deployer would be able to pass funds, and the project itself would not pass any funds.


```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol


54          constructor(address sigVerifyLibAddr, address pemCertLibAddr) {
55              sigVerifyLib = ISigVerifyLib(sigVerifyLibAddr);
56              pemCertLib = PEMCertChainLib(pemCertLibAddr);
57              owner = msg.sender;
58          }


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L54:58

```solidity
File: contracts/automata-attestation/utils/SigVerifyLib.sol


20          constructor(address es256Verifier) {
21              ES256VERIFIER = es256Verifier;
22          }


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L20:22

```solidity
File: contracts/common/EssentialContract.sol


64          constructor() {
65              _disableInitializers();
66          }


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/common/EssentialContract.sol#L64:66

## G017 - `>=` costs less gas than `>`:

The compiler uses opcodes `GT` and `ISZERO` for solidity code that uses `>`, but only requires `LT` for `>=`, [which saves 3 gas](https://gist.github.com/IllIllI000/3dc79d25acccfa16dee4e83ffdc6ffde).


```solidity
File: contracts/L1/libs/LibDepositing.sol


93                      uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L93:93

## G018 - Use assembly to emit events:

Using the [scratch space](https://github.com/Vectorized/solady/blob/30558f5402f02351b96eeb6eaf32bcea29773841/src/tokens/ERC1155.sol#L501-L504) for event arguments (two words or fewer) will save gas over needing Solidity's full abi memory expansion used for emitting normally. 


<details>
<summary>Click to show 55 findings</summary>

```solidity
File: contracts/L1/hooks/AssignmentHook.sol


129             emit BlockAssigned(_blk.assignedProver, _meta, assignment);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L129:129

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L50:56

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L273:279

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibProving.sol#L254:260

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L198:206

```solidity
File: contracts/L1/provers/GuardianProver.sol


54              emit GuardianApproval(msg.sender, _meta.id, _tran.blockHash, approved_);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L54:54

```solidity
File: contracts/L1/provers/Guardians.sol


95              emit GuardiansUpdated(version, _newGuardians);


121             emit Approved(_operationId, _approval, approved_);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/provers/Guardians.sol#L121:121

```solidity
File: contracts/L2/CrossChainOwned.sol


53              emit TransactionExecuted(nextTxId++, bytes4(txdata));


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L53:53

```solidity
File: contracts/L2/TaikoL2.sol


157             emit Anchored(blockhash(parentId), gasExcess);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L2/TaikoL2.sol#L157:157

```solidity
File: contracts/L2/TaikoL2EIP1559Configurable.sol


39              emit ConfigAndExcessChanged(_newConfig, _newGasExcess);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L39:39

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/bridge/Bridge.sol#L519:519

```solidity
File: contracts/common/AddressManager.sol


50              emit AddressSet(_chainId, _name, _newAddress, oldAddress);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/common/AddressManager.sol#L50:50

```solidity
File: contracts/common/EssentialContract.sol


71              emit Paused(msg.sender);


80              emit Unpaused(msg.sender);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/common/EssentialContract.sol#L80:80

```solidity
File: contracts/signal/SignalService.sol


59              emit Authorized(_addr, _authorize);


250             emit ChainDataSynced(_chainId, _blockId, _kind, _chainData, signal_);


268             emit SignalSent(_app, _signal, slot_, _value);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/signal/SignalService.sol#L268:268

```solidity
File: contracts/team/TimelockTokenPool.sol


143             emit Granted(_recipient, _grant);


157             emit Voided(_recipient, amountVoided);


222             emit Withdrawn(_recipient, _to, amountToWithdraw, costToWithdraw);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L222:222

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol


93              emit Withdrawn(user, amount);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L93:93

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol


74              emit Claimed(hash);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L74:74

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol


51              emit MigrationStatusChanged(_migratingAddress, _migratingInbound);


63                  emit MigratedTo(migratingAddress, _account, _amount);


80                  emit MigratedTo(migratingAddress, _account, _amount);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L80:80

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L314:320

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L425:432

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L250:256

```solidity
File: contracts/verifiers/SgxVerifier.sol


109                 emit InstanceDeleted(idx, instances[idx].addr);


220                 emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);


230             emit InstanceAdded(id, newInstance, oldInstance, block.timestamp);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L230:230

</details>

## G019 - State variables only set in the constructor should be declared `immutable`:


        Avoids a Gsset (**20000 gas**) in the constructor, and replaces the first access in each transaction (Gcoldsload - **2100 gas**) and each access thereafter (Gwarmacces - **100 gas**) with a `PUSH32` (**3 gas**). 

        While `string`s are not value types, and therefore cannot be `immutable`/`constant` if not hard-coded outside of the constructor, the same behavior can be achieved by making the current contract `abstract` with `virtual` functions for the `string` accessors, and having a child contract override the functions with the hard-coded implementation-specific values.
        


```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol


57              owner = msg.sender;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L57:57

```solidity
File: contracts/automata-attestation/utils/SigVerifyLib.sol


21              ES256VERIFIER = es256Verifier;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L21:21

## G020 - Use `uint256(1)`/`uint256(2)` instead for `true` and `false` boolean states:

If you don't use boolean for storage you will avoid Gwarmaccess 100 gas. In addition, state changes of boolean from `true` to `false` can cost up to ~20000 gas rather than `uint256(2)` to `uint256(1)` that would cost significantly less.


<details>
<summary>Click to show 9 findings</summary>

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol


38          bool private _checkLocalEnclaveReport;


39          mapping(bytes32 enclave => bool trusted) private _trustedUserMrEnclave;


40          mapping(bytes32 signer => bool trusted) private _trustedUserMrSigner;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L40:40

```solidity
File: contracts/bridge/Bridge.sol


42          mapping(address addr => bool banned) public addressBanned;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/bridge/Bridge.sol#L42:42

```solidity
File: contracts/signal/SignalService.sol


21          mapping(address addr => bool authorized) public isAuthorized;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/signal/SignalService.sol#L21:21

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol


12          mapping(bytes32 hash => bool claimed) public isClaimed;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L12:12

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol


14          bool public migratingInbound;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L14:14

```solidity
File: contracts/tokenvault/ERC20Vault.sol


52          mapping(address btoken => bool blacklisted) public btokenBlacklist;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L52:52

```solidity
File: contracts/verifiers/SgxVerifier.sol


55          mapping(address instanceAddress => bool alreadyAttested) public addressRegistered;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L55:55

</details>

## G021 - Superfluous event fields:

`block.timestamp` and `block.number` are added to event information by default so adding them manually wastes gas.


```solidity
File: contracts/verifiers/SgxVerifier.sol


230             emit InstanceAdded(id, newInstance, oldInstance, block.timestamp);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L230:230

## G022 - `++i`/`i++` should be `unchecked{++i}`/`unchecked{i++}` when it is not possible for them to overflow, as is the case when used in `for`- and `while`-loops:

The `unchecked` keyword is new in solidity version 0.8.0, so this only applies to that version or higher, which these instances are. This saves 30-40 gas [per loop](https://gist.github.com/hrkrshnn/ee8fabd532058307229d65dcd5836ddc#the-increment-in-for-loop-post-condition-can-be-made-unchecked).


<details>
<summary>Click to show 39 findings</summary>

```solidity
File: contracts/L1/hooks/AssignmentHook.sol


172             for (uint256 i; i < _tierFees.length; ++i) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L172:172

```solidity
File: contracts/L1/libs/LibProposing.sol


244                 for (uint256 i; i < params.hookCalls.length; ++i) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L244:244

```solidity
File: contracts/L1/provers/Guardians.sol


74              for (uint256 i; i < guardians.length; ++i) {


80              for (uint256 i = 0; i < _newGuardians.length; ++i) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/provers/Guardians.sol#L80:80

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol


80              for (uint256 i; i < serialNumBatch.length; ++i) {


95              for (uint256 i; i < serialNumBatch.length; ++i) {


191             for (uint256 i; i < enclaveId.tcbLevels.length; ++i) {


214             for (uint256 i; i < tcb.tcbLevels.length; ++i) {


240             for (uint256 i; i < CPUSVN_LENGTH; ++i) {


259             for (uint256 i; i < n; ++i) {


420                 for (uint256 i; i < 3; ++i) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L420:420

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol


54              for (uint256 i; i < size; ++i) {


244             for (uint256 i; i < split.length; ++i) {


354             for (uint256 i; i < SGX_TCB_CPUSVN_SIZE + 1; ++i) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L354:354

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol


153             for (uint256 i; i < encoded.length; ++i) {


281             for (uint256 i; i < 3; ++i) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L281:281

```solidity
File: contracts/automata-attestation/utils/BytesUtils.sol


333             for (uint256 i; i < len; ++i) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L333:333

```solidity
File: contracts/automata-attestation/utils/RsaVerify.sol


140             for (uint256 i = 2; i < 2 + paddingLen; ++i) {


152                 for (uint256 i; i < digestAlgoWithParamLen; ++i) {


158                 for (uint256 i; i < digestAlgoWithParamLen; ++i) {


174             for (uint256 i; i < _sha256.length; ++i) {


273             for (uint256 i = 2; i < 2 + paddingLen; ++i) {


283             for (uint256 i; i < sha1Prefix.length; ++i) {


290             for (uint256 i; i < _sha1.length; ++i) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L290:290

```solidity
File: contracts/automata-attestation/utils/X509DateUtils.sol


48              for (uint16 i = 1970; i < year; ++i) {


59              for (uint8 i = 1; i < month; ++i) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L59:59

```solidity
File: contracts/bridge/Bridge.sol


90              for (uint256 i; i < _msgHashes.length; ++i) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/bridge/Bridge.sol#L90:90

```solidity
File: contracts/signal/SignalService.sol


104             for (uint256 i; i < hopProofs.length; ++i) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/signal/SignalService.sol#L104:104

```solidity
File: contracts/team/airdrop/ERC721Airdrop.sol


59              for (uint256 i; i < tokenIds.length; ++i) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59:59

```solidity
File: contracts/thirdparty/optimism/rlp/RLPWriter.sol


46                  for (i = 1; i <= lenLen; i++) {


59              for (; i < 32; i++) {


66              for (uint256 j = 0; j < out_.length; j++) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66:66

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol


85              for (uint256 i = 0; i < proof.length; i++) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85:85

```solidity
File: contracts/tokenvault/ERC1155Vault.sol


47              for (uint256 i; i < _op.amounts.length; ++i) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L47:47

```solidity
File: contracts/tokenvault/ERC721Vault.sol


34              for (uint256 i; i < _op.tokenIds.length; ++i) {


170                 for (uint256 i; i < _tokenIds.length; ++i) {


175                 for (uint256 i; i < _tokenIds.length; ++i) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L175:175

```solidity
File: contracts/verifiers/SgxVerifier.sol


104             for (uint256 i; i < _ids.length; ++i) {


210             for (uint256 i; i < _instances.length; ++i) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210:210

</details>

## G023 - Usage of `uints`/`ints` smaller than 32 bytes (256 bits) incurs overhead:

> When using elements that are smaller than 32 bytes, your contract’s gas usage may be higher. This is because the EVM operates on 32 bytes at a time. Therefore, if the element is smaller than that, the EVM must use more operations in order to reduce the size of the element from 32 bytes to the desired size.https://docs.soliditylang.org/en/v0.8.11/internals/layout_in_storage.htmlEach operation involving a `uint8` costs an extra [**22-28 gas**](https://gist.github.com/IllIllI000/9388d20c70f9a4632eb3ca7836f54977) (depending on whether the other operand is also a variable of type `uint8`) as compared to ones involving `uint256`, due to the compiler having to clear the higher bits of the memory word before operating on the `uint8`, as well as the associated stack operations of doing so. Use a larger size then downcast where needed.


<details>
<summary>Click to show 16 findings</summary>

```solidity
File: contracts/L1/TaikoL1.sol


150             uint64 slot;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/TaikoL1.sol#L150:150

```solidity
File: contracts/L1/libs/LibDepositing.sol


83                  uint96 fee = uint96(_config.ethDepositMaxFee.min(block.basefee * _config.ethDepositGas));


93                      uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L93:93

```solidity
File: contracts/L1/libs/LibUtils.sol


42              uint32 tid = getTransitionId(_state, blk, slot, _parentHash);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L42:42

```solidity
File: contracts/L1/libs/LibVerifying.sol


107             uint32 tid = blk.verifiedTransitionId;


117             uint64 numBlocksVerified;


234             (uint64 lastSyncedBlock,) = signalService.getSyncedChainData(


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L234:234

```solidity
File: contracts/L2/CrossChainOwned.sol


42              (uint64 txId, bytes memory txdata) = abi.decode(_data, (uint64, bytes));


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L42:42

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol


106             uint32 totalQuoteSize = 48 // header


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L106:106

```solidity
File: contracts/automata-attestation/utils/BytesUtils.sol


332             uint8 decoded;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L332:332

```solidity
File: contracts/automata-attestation/utils/X509DateUtils.sol


15              uint8 offset;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L15:15

```solidity
File: contracts/bridge/Bridge.sol


89              uint64 _timestamp = _suspend ? type(uint64).max : uint64(block.timestamp);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/bridge/Bridge.sol#L89:89

```solidity
File: contracts/team/TimelockTokenPool.sol


197             uint128 _amountUnlocked = amountUnlocked / 1e18; // divide first


226             uint128 amountOwned = _getAmountOwned(_grant);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L226:226

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol


134                         uint8 branchKey = uint8(key[currentKeyIndex]);


141                     uint8 prefix = uint8(path[0]);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L141:141

</details>

## G024 - Consider activating `via-ir` for deploying:


        The IR-based code generator was introduced with an aim to not only allow code generation to be more transparent and auditable but also to enable more powerful optimization passes that span across functions.

        You can enable it on the command line using `--via-ir` or with the option `{"viaIR": true}`.

        This will take longer to compile, but you can just simple test it before deploying and if you got a better benchmark then you can add --via-ir to your deploy command

        More on: https://docs.soliditylang.org/en/v0.8.17/ir-breaking-changes.html
        


```solidity
File: Various Files


None

```

## G025 - Empty Blocks Should Be Removed Or Emit Something:

The code should be refactored such that they no longer exist, or the block should do something useful, such as emitting an event or reverting. If the contract is meant to be extended, the contract should be abstract and the function signatures be added without any default implementation. If the block is an empty if-statement block to avoid doing subsequent checks in the else-if/else conditions, the else-if/else conditions should be nested under the negation of the if-statement, because they involve different classes of checks, which may lead to the introduction of errors when the code is later modified (if(x){}else if(y){...}else{...} => if(!x){if(y){...}else{...}})


<details>
<summary>Click to show 4 findings</summary>

```solidity
File: contracts/libs/LibAddress.sol


58              } catch { }


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/libs/LibAddress.sol#L58:58

```solidity
File: contracts/thirdparty/optimism/rlp/RLPReader.sol


298                 for { } lt(i, _length) { i := add(i, 32) } { mstore(add(dest, i), mload(add(src, i))) }


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L298:298

```solidity
File: contracts/tokenvault/ERC1155Vault.sol


268                     } catch { }


265                     } catch { }


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L265:265

</details>

## G026 - Emit Used In Loop:

Emitting an event inside a loop performs a LOG op N times, where N is the loop length. Consider refactoring the code to emit the event only once at the end of loop. Gas savings should be multiplied by the average loop length.


```solidity
File: contracts/bridge/Bridge.sol


93                  emit MessageSuspended(msgHash, _suspend);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/bridge/Bridge.sol#L93:93

```solidity
File: contracts/verifiers/SgxVerifier.sol


109                 emit InstanceDeleted(idx, instances[idx].addr);


220                 emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220:220

## G027 - Inverting the condition of an if-else-statement:

Flipping the true and false blocks instead saves 3 gas.


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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/bridge/Bridge.sol#L302:306

## G028 - `unchecked {}` can be used on the division of two `uints` in order to save gas:

The division cannot overflow, since both the numerator and the denominator are non-negative.


<details>
<summary>Click to show 15 findings</summary>

```solidity
File: contracts/L1/TaikoL1.sol


215                 ethDepositMaxFee: 1 ether / 10,


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/TaikoL1.sol#L215:215

```solidity
File: contracts/L1/gov/TaikoGovernor.sol


124             return 1_000_000_000 ether / 10_000; // 0.01% of Taiko Token


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L124:124

```solidity
File: contracts/L1/libs/LibVerifying.sol


262                     || _config.ethDepositMaxFee > type(uint96).max / _config.ethDepositMaxCountPerBlock


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L262:262

```solidity
File: contracts/L2/Lib1559Math.sol


41              uint256 input = _gasExcess * LibFixedPointMath.SCALING_FACTOR / _adjustmentFactor;


28              return _ethQty(_gasExcess, _adjustmentFactor) / LibFixedPointMath.SCALING_FACTOR


28              return _ethQty(_gasExcess, _adjustmentFactor) / LibFixedPointMath.SCALING_FACTOR
29                  / _adjustmentFactor;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L2/Lib1559Math.sol#L28:29

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol


359                     ? uint16(bytes2(svnValueBytes)) / 256


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L359:359

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol


155                 uint256 upperDigit = digits / 16;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L155:155

```solidity
File: contracts/team/TimelockTokenPool.sol


197             uint128 _amountUnlocked = amountUnlocked / 1e18; // divide first


264             return _amount * uint64(block.timestamp - _start) / _period;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L264:264

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol


117             uint256 timeBasedAllowance = balance
118                 * (block.timestamp.min(claimEnd + withdrawalWindow) - claimEnd) / withdrawalWindow;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L117:118

```solidity
File: contracts/thirdparty/optimism/rlp/RLPWriter.sol


39                  while (_len / i != 0) {


47                      out_[i] = bytes1(uint8((_len / (256 ** (lenLen - i))) % 256));


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L47:47

```solidity
File: contracts/thirdparty/solmate/LibFixedPointMath.sol


39                  int256 k = ((x << 96) / 54_916_777_467_707_473_351_141_471_128 + 2 ** 95) >> 96;


33                  x = (x << 78) / 5 ** 18;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L33:33

</details>

## G029 - Private functions used once can be inlined:

Private functions used once can be inlined to save GAS


<details>
<summary>Click to show 41 findings</summary>

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L164:176

```solidity
File: contracts/L1/libs/LibProposing.sol


299         function _isProposerPermitted(
300             TaikoData.SlotB memory _slotB,
301             IAddressResolver _resolver
302         )
303             private
304             view
305             returns (bool)
306         {
307             if (_slotB.numBlocks == 1) {
308                 // Only proposer_one can propose the first block after genesis
309                 address proposerOne = _resolver.resolve("proposer_one", true);
310                 if (proposerOne != address(0) && msg.sender != proposerOne) {
311                     return false;
312                 }
313             }
314     
315             address proposer = _resolver.resolve("proposer", true);
316             return proposer == address(0) || msg.sender == proposer;
317         }


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L299:317

```solidity
File: contracts/L1/libs/LibProving.sol


269         function _createTransition(
270             TaikoData.State storage _state,
271             TaikoData.Block storage _blk,
272             TaikoData.Transition memory _tran,
273             uint64 slot
274         )
275             private
276             returns (uint32 tid_, TaikoData.TransitionState storage ts_)
277         {
278             tid_ = LibUtils.getTransitionId(_state, _blk, slot, _tran.parentHash);
279     
280             if (tid_ == 0) {
281                 // In cases where a transition with the provided parentHash is not
282                 // found, we must essentially "create" one and set it to its initial
283                 // state. This initial state can be viewed as a special transition
284                 // on tier-0.
285                 //
286                 // Subsequently, we transform this tier-0 transition into a
287                 // non-zero-tier transition with a proof. This approach ensures that
288                 // the same logic is applicable for both 0-to-non-zero transition
289                 // updates and non-zero-to-non-zero transition updates.
290                 unchecked {
291                     // Unchecked is safe:  Not realistic 2**32 different fork choice
292                     // per block will be proven and none of them is valid
293                     tid_ = _blk.nextTransitionId++;
294                 }
295     
296                 // Keep in mind that state.transitions are also reusable storage
297                 // slots, so it's necessary to reinitialize all transition fields
298                 // below.
299                 ts_ = _state.transitions[slot][tid_];
300                 ts_.blockHash = 0;
301                 ts_.stateRoot = 0;
302                 ts_.validityBond = 0;
303                 ts_.contester = address(0);
304                 ts_.contestBond = 1; // to save gas
305                 ts_.timestamp = _blk.proposedAt;
306                 ts_.tier = 0;
307                 ts_.contestations = 0;
308     
309                 if (tid_ == 1) {
310                     // This approach serves as a cost-saving technique for the
311                     // majority of blocks, where the first transition is expected to
312                     // be the correct one. Writing to `tran` is more economical
313                     // since it resides in the ring buffer, whereas writing to
314                     // `transitionIds` is not as cost-effective.
315                     ts_.key = _tran.parentHash;
316     
317                     // In the case of this first transition, the block's assigned
318                     // prover has the privilege to re-prove it, but only when the
319                     // assigned prover matches the previous prover. To ensure this,
320                     // we establish the transition's prover as the block's assigned
321                     // prover. Consequently, when we carry out a 0-to-non-zero
322                     // transition update, the previous prover will consistently be
323                     // the block's assigned prover.
324                     //
325                     // While alternative implementations are possible, introducing
326                     // such changes would require additional if-else logic.
327                     ts_.prover = _blk.assignedProver;
328                 } else {
329                     // In scenarios where this transition is not the first one, we
330                     // straightforwardly reset the transition prover to address
331                     // zero.
332                     ts_.prover = address(0);
333     
334                     // Furthermore, we index the transition for future retrieval.
335                     // It's worth emphasizing that this mapping for indexing is not
336                     // reusable. However, given that the majority of blocks will
337                     // only possess one transition — the correct one — we don't need
338                     // to be concerned about the cost in this case.
339                     _state.transitionIds[_blk.blockId][_tran.parentHash] = tid_;
340     
341                     // There is no need to initialize ts.key here because it's only used when tid == 1
342                 }
343             } else {
344                 // A transition with the provided parentHash has been located.
345                 ts_ = _state.transitions[slot][tid_];
346             }
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
360             // Higher tier proof overwriting lower tier proof
361             uint256 reward;
362     
363             if (_ts.contester != address(0)) {
364                 if (_sameTransition) {
365                     // The contested transition is proven to be valid, contestor loses the game
366                     reward = _ts.contestBond >> 2;
367                     _tko.transfer(_ts.prover, _ts.validityBond + reward);
368                 } else {
369                     // The contested transition is proven to be invalid, contestor wins the game
370                     reward = _ts.validityBond >> 2;
371                     _tko.transfer(_ts.contester, _ts.contestBond + reward);
372                 }
373             } else {
374                 if (_sameTransition) revert L1_ALREADY_PROVED();
375                 // Contest the existing transition and prove it to be invalid
376                 reward = _ts.validityBond >> 1;
377                 _ts.contestations += 1;
378             }
379     
380             unchecked {
381                 if (reward > _tier.validityBond) {
382                     _tko.transfer(msg.sender, reward - _tier.validityBond);
383                 } else {
384                     _tko.transferFrom(msg.sender, address(this), _tier.validityBond - reward);
385                 }
386             }
387     
388             _ts.validityBond = _tier.validityBond;
389             _ts.contestBond = 1; // to save gas
390             _ts.contester = address(0);
391             _ts.prover = msg.sender;
392             _ts.tier = _proof.tier;
393     
394             if (!_sameTransition) {
395                 _ts.blockHash = _tran.blockHash;
396                 _ts.stateRoot = _tran.stateRoot;
397             }
398         }


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
411             // The highest tier proof can always submit new proofs
412             if (_tier.contestBond == 0) return;
413     
414             bool inProvingWindow = uint256(_ts.timestamp).max(_state.slotB.lastUnpausedAt)
415                 + _tier.provingWindow * 60 >= block.timestamp;
416             bool isAssignedPover = msg.sender == _blk.assignedProver;
417     
418             // The assigned prover can only submit the very first transition.
419             if (_tid == 1 && _ts.tier == 0 && inProvingWindow) {
420                 if (!isAssignedPover) revert L1_NOT_ASSIGNED_PROVER();
421             } else {
422                 // Disallow the same address to prove the block so that we can detect that the
423                 // assigned prover should not receive his liveness bond back
424                 if (isAssignedPover) revert L1_ASSIGNED_PROVER_NOT_ALLOWED();
425             }
426         }


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibProving.sol#L401:426

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
232             ISignalService signalService = ISignalService(_resolver.resolve("signal_service", false));
233     
234             (uint64 lastSyncedBlock,) = signalService.getSyncedChainData(
235                 _config.chainId, LibSignals.STATE_ROOT, 0 /* latest block Id*/
236             );
237     
238             if (_lastVerifiedBlockId > lastSyncedBlock + _config.blockSyncThreshold) {
239                 signalService.syncChainData(
240                     _config.chainId, LibSignals.STATE_ROOT, _lastVerifiedBlockId, _stateRoot
241                 );
242             }
243         }


245         function _isConfigValid(TaikoData.Config memory _config) private view returns (bool) {
246             if (
247                 _config.chainId <= 1 || _config.chainId == block.chainid //
248                     || _config.blockMaxProposals == 1
249                     || _config.blockRingBufferSize <= _config.blockMaxProposals + 1
250                     || _config.blockMaxGasLimit == 0 || _config.blockMaxTxListBytes == 0
251                     || _config.blockMaxTxListBytes > 128 * 1024 // calldata up to 128K
252                     || _config.livenessBond == 0 || _config.ethDepositRingBufferSize <= 1
253                     || _config.ethDepositMinCountPerBlock == 0
254                 // Audit recommendation, and gas tested. Processing 32 deposits (as initially set in
255                 // TaikoL1.sol) costs 72_502 gas.
256                 || _config.ethDepositMaxCountPerBlock > 32
257                     || _config.ethDepositMaxCountPerBlock < _config.ethDepositMinCountPerBlock
258                     || _config.ethDepositMinAmount == 0
259                     || _config.ethDepositMaxAmount <= _config.ethDepositMinAmount
260                     || _config.ethDepositMaxAmount > type(uint96).max || _config.ethDepositGas == 0
261                     || _config.ethDepositMaxFee == 0
262                     || _config.ethDepositMaxFee > type(uint96).max / _config.ethDepositMaxCountPerBlock
263             ) return false;
264     
265             return true;
266         }


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L245:266

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
41              uint256 input = _gasExcess * LibFixedPointMath.SCALING_FACTOR / _adjustmentFactor;
42              if (input > LibFixedPointMath.MAX_EXP_INPUT) {
43                  input = LibFixedPointMath.MAX_EXP_INPUT;
44              }
45              return uint256(LibFixedPointMath.exp(int256(input)));
46          }


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L2/Lib1559Math.sol#L33:46

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L303:332

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol


216         function _removeHeadersAndFooters(string memory pemData)
217             private
218             pure
219             returns (bool success, bytes memory extracted, uint256 endIndex)
220         {
221             // Check if the input contains the "BEGIN" and "END" headers
222             uint256 beginPos = LibString.indexOf(pemData, HEADER);
223             uint256 endPos = LibString.indexOf(pemData, FOOTER);
224     
225             bool headerFound = beginPos != LibString.NOT_FOUND;
226             bool footerFound = endPos != LibString.NOT_FOUND;
227     
228             if (!headerFound || !footerFound) {
229                 return (false, extracted, endIndex);
230             }
231     
232             // Extract the content between the headers
233             uint256 contentStart = beginPos + HEADER_LENGTH;
234     
235             // Extract and return the content
236             bytes memory contentBytes;
237     
238             // do not include newline
239             bytes memory delimiter = hex"0a";
240             string memory contentSlice = LibString.slice(pemData, contentStart, endPos);
241             string[] memory split = LibString.split(contentSlice, string(delimiter));
242             string memory contentStr;
243     
244             for (uint256 i; i < split.length; ++i) {
245                 contentStr = LibString.concat(contentStr, split[i]);
246             }
247     
248             contentBytes = bytes(contentStr);
249             return (true, contentBytes, endPos + FOOTER_LENGTH);
250         }


269         function _findPckTcbInfo(
270             bytes memory der,
271             uint256 tbsPtr,
272             uint256 tbsParentPtr
273         )
274             private
275             pure
276             returns (
277                 bool success,
278                 uint256 pcesvn,
279                 uint256[] memory cpusvns,
280                 bytes memory fmspcBytes,
281                 bytes memory pceidBytes
282             )
283         {
284             // iterate through the elements in the Extension sequence
285             // until we locate the SGX Extension OID
286             while (tbsPtr != 0) {
287                 uint256 internalPtr = der.firstChildOf(tbsPtr);
288                 if (der[internalPtr.ixs()] != 0x06) {
289                     return (false, pcesvn, cpusvns, fmspcBytes, pceidBytes);
290                 }
291     
292                 if (BytesUtils.compareBytes(der.bytesAt(internalPtr), SGX_EXTENSION_OID)) {
293                     // 1.2.840.113741.1.13.1
294                     internalPtr = der.nextSiblingOf(internalPtr);
295                     uint256 extnValueParentPtr = der.rootOfOctetStringAt(internalPtr);
296                     uint256 extnValuePtr = der.firstChildOf(extnValueParentPtr);
297     
298                     // Copy flags to memory to avoid stack too deep
299                     PCKTCBFlags memory flags;
300     
301                     while (!(flags.fmspcFound && flags.pceidFound && flags.tcbFound)) {
302                         uint256 extnValueOidPtr = der.firstChildOf(extnValuePtr);
303                         if (der[extnValueOidPtr.ixs()] != 0x06) {
304                             return (false, pcesvn, cpusvns, fmspcBytes, pceidBytes);
305                         }
306                         if (BytesUtils.compareBytes(der.bytesAt(extnValueOidPtr), TCB_OID)) {
307                             // 1.2.840.113741.1.13.1.2
308                             (flags.tcbFound, pcesvn, cpusvns) = _findTcb(der, extnValueOidPtr);
309                         }
310                         if (BytesUtils.compareBytes(der.bytesAt(extnValueOidPtr), PCEID_OID)) {
311                             // 1.2.840.113741.1.13.1.3
312                             uint256 pceidPtr = der.nextSiblingOf(extnValueOidPtr);
313                             pceidBytes = der.bytesAt(pceidPtr);
314                             flags.pceidFound = true;
315                         }
316                         if (BytesUtils.compareBytes(der.bytesAt(extnValueOidPtr), FMSPC_OID)) {
317                             // 1.2.840.113741.1.13.1.4
318                             uint256 fmspcPtr = der.nextSiblingOf(extnValueOidPtr);
319                             fmspcBytes = der.bytesAt(fmspcPtr);
320                             flags.fmspcFound = true;
321                         }
322     
323                         if (extnValuePtr.ixl() < extnValueParentPtr.ixl()) {
324                             extnValuePtr = der.nextSiblingOf(extnValuePtr);
325                         } else {
326                             break;
327                         }
328                     }
329                     success = flags.fmspcFound && flags.pceidFound && flags.tcbFound;
330                     break;
331                 }
332     
333                 if (tbsPtr.ixl() < tbsParentPtr.ixl()) {
334                     tbsPtr = der.nextSiblingOf(tbsPtr);
335                 } else {
336                     tbsPtr = 0; // exit
337                 }
338             }
339         }


341         function _findTcb(
342             bytes memory der,
343             uint256 oidPtr
344         )
345             private
346             pure
347             returns (bool success, uint256 pcesvn, uint256[] memory cpusvns)
348         {
349             // sibiling of tcbOid
350             uint256 tcbPtr = der.nextSiblingOf(oidPtr);
351             // get the first svn object in the sequence
352             uint256 svnParentPtr = der.firstChildOf(tcbPtr);
353             cpusvns = new uint256[](SGX_TCB_CPUSVN_SIZE);
354             for (uint256 i; i < SGX_TCB_CPUSVN_SIZE + 1; ++i) {
355                 uint256 svnPtr = der.firstChildOf(svnParentPtr); // OID
356                 uint256 svnValuePtr = der.nextSiblingOf(svnPtr); // value
357                 bytes memory svnValueBytes = der.bytesAt(svnValuePtr);
358                 uint16 svnValue = svnValueBytes.length < 2
359                     ? uint16(bytes2(svnValueBytes)) / 256
360                     : uint16(bytes2(svnValueBytes));
361                 if (BytesUtils.compareBytes(der.bytesAt(svnPtr), PCESVN_OID)) {
362                     // pcesvn is 4 bytes in size
363                     pcesvn = uint256(svnValue);
364                 } else {
365                     // each cpusvn is at maximum two bytes in size
366                     uint256 cpusvn = uint256(svnValue);
367                     cpusvns[i] = cpusvn;
368                 }
369     
370                 // iterate to the next svn object in the sequence
371                 svnParentPtr = der.nextSiblingOf(svnParentPtr);
372             }
373             success = true;
374         }


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L341:374

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol


165         function parseAndVerifyHeader(bytes memory rawHeader)
166             private
167             pure
168             returns (bool success, V3Struct.Header memory header)
169         {
170             bytes2 version = bytes2(rawHeader.substring(0, 2));
171             if (version != SUPPORTED_QUOTE_VERSION) {
172                 return (false, header);
173             }
174     
175             bytes2 attestationKeyType = bytes2(rawHeader.substring(2, 2));
176             if (attestationKeyType != SUPPORTED_ATTESTATION_KEY_TYPE) {
177                 return (false, header);
178             }
179     
180             bytes4 teeType = bytes4(rawHeader.substring(4, 4));
181             if (teeType != SUPPORTED_TEE_TYPE) {
182                 return (false, header);
183             }
184     
185             bytes16 qeVendorId = bytes16(rawHeader.substring(12, 16));
186             if (qeVendorId != VALID_QE_VENDOR_ID) {
187                 return (false, header);
188             }
189     
190             header = V3Struct.Header({
191                 version: version,
192                 attestationKeyType: attestationKeyType,
193                 teeType: teeType,
194                 qeSvn: bytes2(rawHeader.substring(8, 2)),
195                 pceSvn: bytes2(rawHeader.substring(10, 2)),
196                 qeVendorId: qeVendorId,
197                 userData: bytes20(rawHeader.substring(28, 20))
198             });
199     
200             success = true;
201         }


203         function parseAuthDataAndVerifyCertType(
204             bytes memory rawAuthData,
205             address pemCertLibAddr
206         )
207             private
208             pure
209             returns (bool success, V3Struct.ECDSAQuoteV3AuthData memory authDataV3)
210         {
211             V3Struct.QEAuthData memory qeAuthData;
212             qeAuthData.parsedDataSize = uint16(littleEndianDecode(rawAuthData.substring(576, 2)));
213             qeAuthData.data = rawAuthData.substring(578, qeAuthData.parsedDataSize);
214     
215             uint256 offset = 578 + qeAuthData.parsedDataSize;
216             V3Struct.CertificationData memory cert;
217             cert.certType = uint16(littleEndianDecode(rawAuthData.substring(offset, 2)));
218             if (cert.certType < 1 || cert.certType > 5) {
219                 return (false, authDataV3);
220             }
221             offset += 2;
222             cert.certDataSize = uint32(littleEndianDecode(rawAuthData.substring(offset, 4)));
223             offset += 4;
224             bytes memory certData = rawAuthData.substring(offset, cert.certDataSize);
225             cert.decodedCertDataArray = parseCerificationChainBytes(certData, pemCertLibAddr);
226     
227             authDataV3.ecdsa256BitSignature = rawAuthData.substring(0, 64);
228             authDataV3.ecdsaAttestationKey = rawAuthData.substring(64, 64);
229             bytes memory rawQeReport = rawAuthData.substring(128, 384);
230             authDataV3.pckSignedQeReport = parseEnclaveReport(rawQeReport);
231             authDataV3.qeReportSignature = rawAuthData.substring(512, 64);
232             authDataV3.qeAuthData = qeAuthData;
233             authDataV3.certification = cert;
234     
235             success = true;
236         }


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L203:236

```solidity
File: contracts/automata-attestation/utils/BytesUtils.sol


272         function memcpy(uint256 dest, uint256 src, uint256 len) private pure {
273             assembly {
274                 mcopy(dest, src, len)
275             }
276         }


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L272:276

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/bridge/Bridge.sol#L555:569

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/signal/SignalService.sol#L271:296

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L267:271

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L55:69

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L235:249

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L303:321

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L407:433

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L240:257

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L233:238

</details>

## G030 - Use assembly to calculate hashes to save gas:

Using assembly to calculate hashes can save 80 gas per instance


<details>
<summary>Click to show 28 findings</summary>

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L146:161

```solidity
File: contracts/L1/libs/LibProposing.sol


126                     depositsHash: keccak256(abi.encode(deposits_)),


189                 meta_.blobHash = keccak256(_txList);


204             meta_.difficulty = keccak256(abi.encodePacked(block.prevrandao, b.numBlocks, block.number));


213                 metaHash: keccak256(abi.encode(meta_)),


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L213:213

```solidity
File: contracts/L1/libs/LibProving.sol


20          bytes32 public constant RETURN_LIVENESS_BOND = keccak256("RETURN_LIVENESS_BOND");


121             if (blk.blockId != _meta.id || blk.metaHash != keccak256(abi.encode(_meta))) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibProving.sol#L121:121

```solidity
File: contracts/L1/provers/GuardianProver.sol


46              bytes32 hash = keccak256(abi.encode(_meta, _tran));


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L46:46

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol


292                 bytes32 issuerPubKeyHash = keccak256(issuer.pubKey);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L292:292

```solidity
File: contracts/automata-attestation/utils/BytesUtils.sol


372             return keccak256(a) == keccak256(b);


372             return keccak256(a) == keccak256(b);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L372:372

```solidity
File: contracts/bridge/Bridge.sol


450             return keccak256(abi.encode("TAIKO_MESSAGE", _message));


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/bridge/Bridge.sol#L450:450

```solidity
File: contracts/signal/LibSignals.sol


8           bytes32 public constant STATE_ROOT = keccak256("STATE_ROOT");


11          bytes32 public constant SIGNAL_ROOT = keccak256("SIGNAL_ROOT");


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/signal/LibSignals.sol#L11:11

```solidity
File: contracts/signal/SignalService.sol


186             return keccak256(abi.encode(_chainId, _kind, _blockId));


203             return keccak256(abi.encodePacked("SIGNAL", _chainId, _app, _signal));


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/signal/SignalService.sol#L203:203

```solidity
File: contracts/team/TimelockTokenPool.sol


170             bytes32 hash = keccak256(abi.encodePacked("Withdraw unlocked Taiko token to: ", _to));


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L170:170

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol


68              bytes32 hash = keccak256(abi.encode("CLAIM_TAIKO_AIRDROP", data));


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L68:68

```solidity
File: contracts/thirdparty/optimism/Bytes.sol


150             return keccak256(_bytes) == keccak256(_other);


150             return keccak256(_bytes) == keccak256(_other);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L150:150

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol


94                          Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),


100                         Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L100:100

```solidity
File: contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol


55              hash_ = abi.encodePacked(keccak256(_key));


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L55:55

```solidity
File: contracts/tokenvault/ERC20Vault.sol


176                         || keccak256(bytes(ctoken.symbol)) != keccak256(bytes(_ctoken.symbol))


176                         || keccak256(bytes(ctoken.symbol)) != keccak256(bytes(_ctoken.symbol))


177                         || keccak256(bytes(ctoken.name)) != keccak256(bytes(_ctoken.name))


177                         || keccak256(bytes(ctoken.name)) != keccak256(bytes(_ctoken.name))


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L177:177

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L182:192

</details>

## G031 - Unused named return variables without optimizer waste gas:

Consider changing the variable to be an unnamed one, since the variable is never assigned, nor is it returned by name. If the optimizer is not turned on, leaving the code as it is will also waste gas for the stack variable.


<details>
<summary>Click to show 10 findings</summary>

```solidity
File: contracts/L1/libs/LibProving.sol


100             returns (uint8 maxBlocksToVerify_)


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibProving.sol#L100:100

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol


130             returns (bool valid)


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L130:130

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol


219             returns (bool success, bytes memory extracted, uint256 endIndex)


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L219:219

```solidity
File: contracts/automata-attestation/utils/BytesUtils.sol


188         function readUint8(bytes memory self, uint256 idx) internal pure returns (uint8 ret) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L188:188

```solidity
File: contracts/automata-attestation/utils/SigVerifyLib.sol


120             returns (bool sigValid)


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L120:120

```solidity
File: contracts/bridge/Bridge.sol


421             returns (uint256 invocationDelay_, uint256 invocationExtraDelay_)


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/bridge/Bridge.sol#L421:421

```solidity
File: contracts/common/AddressResolver.sol


37              returns (address payable)


51              returns (address payable)


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/common/AddressResolver.sol#L51:51

```solidity
File: contracts/thirdparty/optimism/rlp/RLPReader.sol


147             returns (uint256 offset_, uint256 length_, RLPItemType type_)


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L147:147

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol


241             returns (uint256 shared_)


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L241:241

</details>

## G032 - Avoid updating storage when the value hasn't changed:

If the old value is equal to the new value, not re-storing the value will avoid a Gsreset (**2900 gas**), potentially at the expense of a Gcoldsload (**2100 gas**) or a Gwarmaccess (**100 gas**).


<details>
<summary>Click to show 21 findings</summary>

```solidity
File: contracts/L1/provers/Guardians.sol


53          function setGuardians(


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/provers/Guardians.sol#L53:53

```solidity
File: contracts/L2/TaikoL2.sol


107         function anchor(


71          function init(


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L2/TaikoL2.sol#L71:71

```solidity
File: contracts/L2/TaikoL2EIP1559Configurable.sol


25          function setConfigAndExcess(


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L25:25

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol


114         function configureQeIdentityJson(EnclaveIdStruct.EnclaveId calldata qeIdentityInput)


122         function toggleLocalReportCheck() external onlyOwner {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L122:122

```solidity
File: contracts/bridge/Bridge.sol


541         function _storeContext(bytes32 _msgHash, address _from, uint64 _srcChainId) private {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/bridge/Bridge.sol#L541:541

```solidity
File: contracts/common/EssentialContract.sol


69          function pause() public virtual whenNotPaused {


119         function _storeReentryLock(uint8 _reentry) internal virtual {


78          function unpause() public virtual whenPaused {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/common/EssentialContract.sol#L78:78

```solidity
File: contracts/team/TimelockTokenPool.sol


111         function init(


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L111:111

```solidity
File: contracts/team/airdrop/ERC20Airdrop.sol


27          function init(


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L27:27

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol


54          function init(


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L54:54

```solidity
File: contracts/team/airdrop/ERC721Airdrop.sol


25          function init(


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L25:25

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol


90          function _setConfig(uint64 _claimStart, uint64 _claimEnd, bytes32 _merkleRoot) private {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L90:90

```solidity
File: contracts/tokenvault/BridgedERC1155.sol


38          function init(


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L38:38

```solidity
File: contracts/tokenvault/BridgedERC20.sol


52          function init(


80          function setSnapshoter(address _snapshooter) external onlyOwner {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L80:80

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol


36          function changeMigrationStatus(


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L36:36

```solidity
File: contracts/tokenvault/BridgedERC721.sol


31          function init(


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L31:31

```solidity
File: contracts/tokenvault/adapters/USDCAdapter.sol


38          function init(address _owner, address _addressManager, IUSDC _usdc) external initializer {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L38:38

</details>

## G033 - Do not calculate constants:

Due to how constant variables are implemented (replacements at compile-time), an expression assigned to a constant variable is recomputed each time that the variable is used, which wastes some gas.


```solidity
File: contracts/L1/libs/LibProposing.sol


21          uint256 public constant MAX_BYTES_PER_BLOB = 4096 * 32;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L21:21

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol


24          uint256 internal constant BRANCH_NODE_LENGTH = TREE_RADIX + 1;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L24:24

## G034 - Duplicated `require()`/`revert()` checks should be refactored to a modifier or function:

Saves deployment costs.


```solidity
File: contracts/automata-attestation/utils/Asn1Decode.sol


142             require(der[ptr.ixs()] == 0x02, "Not type INTEGER");


143             require(der[ptr.ixf()] & 0x80 == 0, "Not positive");


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L143:143

```solidity
File: contracts/automata-attestation/utils/SigVerifyLib.sol


50                  revert("Unsupported algorithm");


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L50:50

## G035 - The use of a logical AND in place of double if is slightly less gas efficient in instances where there isn't a corresponding else statement for the given if statement:

Using a double if statement instead of logical AND (&&) can provide similar short-circuiting behavior whereas double if is slightly more efficient.


<details>
<summary>Click to show 23 findings</summary>

```solidity
File: contracts/L1/hooks/AssignmentHook.sol


82                  block.timestamp > assignment.expiry
83                      || assignment.metaHash != 0 && _blk.metaHash != assignment.metaHash


120             if (input.tip != 0 && block.coinbase != address(0)) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L120:120

```solidity
File: contracts/L1/libs/LibProposing.sol


108             if (params.parentMetaHash != 0 && parentMetaHash != params.parentMetaHash) {


164                     if (_config.blobReuseEnabled && params.cacheBlobForReuse) {


310                 if (proposerOne != address(0) && msg.sender != proposerOne) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L310:310

```solidity
File: contracts/L1/libs/LibProving.sol


419             if (_tid == 1 && _ts.tier == 0 && inProvingWindow) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibProving.sol#L419:419

```solidity
File: contracts/L2/TaikoL2.sol


117                 _l1BlockHash == 0 || _l1StateRoot == 0 || _l1BlockId == 0
118                     || (block.number != 1 && _parentGasUsed == 0)


141             if (!skipFeeCheck() && block.basefee != basefee) {


275                 if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L2/TaikoL2.sol#L275:275

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol


220                 if (pceSvnIsHigherOrGreater && cpuSvnsAreHigherOrGreater) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L220:220

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol


134                 if (
135                     (notBeforeTag != 0x17 && notBeforeTag == 0x18)


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L134:135

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/bridge/Bridge.sol#L490:493

```solidity
File: contracts/common/AddressResolver.sol


85              if (!_allowZeroAddress && addr_ == address(0)) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/common/AddressResolver.sol#L85:85

```solidity
File: contracts/common/EssentialContract.sol


42              if (msg.sender != owner() && msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/common/EssentialContract.sol#L42:42

```solidity
File: contracts/signal/SignalService.sol


285             if (cacheStateRoot && _isFullProof && !_isLastHop) {


293             if (cacheSignalRoot && (_isFullProof || !_isLastHop)) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/signal/SignalService.sol#L293:293

```solidity
File: contracts/team/TimelockTokenPool.sol


277                 if (_cliff > 0 && _cliff <= _start) revert INVALID_GRANT();


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L277:277

```solidity
File: contracts/thirdparty/optimism/rlp/RLPWriter.sol


14              if (_in.length == 1 && uint8(_in[0]) < 128) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L14:14

```solidity
File: contracts/tokenvault/BridgedERC20.sol


38              if (msg.sender != owner() && msg.sender != snapshooter) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L38:38

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol


45              if (_migratingAddress == migratingAddress && _migratingInbound == migratingInbound) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L45:45

</details>

## G036 - Use the inputs/results of assignments rather than re-reading state variables:

When a state variable is assigned, it saves gas to use the value being assigned, later in the function, rather than re-reading the state variable itself. If needed, it can also be stored to a local variable, and be used in that way. Both options avoid a Gwarmaccess (100 gas). Note that if the operation is, say +=, the assignment also results in a value which can be used. The instances below point to the first reference after the assignment, since later references are already covered by issues describing the caching of state variable values.


<details>
<summary>Click to show 12 findings</summary>

```solidity
File: contracts/L1/TaikoL1.sol


67              (meta_, deposits_) = LibProposing.proposeBlock(state, config, this, _params, _txList);


94              uint8 maxBlocksToVerify = LibProving.proveBlock(state, config, this, meta, tran, proof);


181             a_ = state.slotA;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/TaikoL1.sol#L181:181

```solidity
File: contracts/L1/provers/Guardians.sol


88                  guardianIds[guardian] = guardians.length;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/provers/Guardians.sol#L88:88

```solidity
File: contracts/L2/TaikoL2.sol


265                 uint256 excess = uint256(gasExcess) + _parentGasUsed;


262             if (gasExcess > 0) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L2/TaikoL2.sol#L262:262

```solidity
File: contracts/common/AddressResolver.sol


83              addr_ = payable(IAddressManager(addressManager).getAddress(_chainId, _name));


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/common/AddressResolver.sol#L83:83

```solidity
File: contracts/team/TimelockTokenPool.sol


219             IERC20(taikoToken).transferFrom(sharedVault, _to, amountToWithdraw);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L219:219

```solidity
File: contracts/team/airdrop/ERC20Airdrop.sol


63              IERC20(token).transferFrom(vault, user, amount);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L63:63

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol


63                  emit MigratedTo(migratingAddress, _account, _amount);


80                  emit MigratedTo(migratingAddress, _account, _amount);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L80:80

```solidity
File: contracts/verifiers/SgxVerifier.sol


218                 ids[i] = nextInstanceId;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L218:218

</details>

## G037 - Assigning state variables directly with named struct constructors wastes gas:

Using named arguments for struct means that the compiler needs to organize the fields in memory before doing the assignment, which wastes gas. Set each field directly in storage (use dot-notation), or use the unnamed version of the constructor.


<details>
<summary>Click to show 4 findings</summary>

```solidity
File: contracts/thirdparty/optimism/rlp/RLPReader.sol


47              out_ = RLPItem({ length: _in.length, ptr: ptr });


84                  out_[itemCount] = RLPItem({


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L84:84

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol


209                 proof_[i] = TrieNode({ encoded: _proof[i], decoded: RLPReader.readList(_proof[i]) });


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L209:209

```solidity
File: contracts/tokenvault/ERC20Vault.sol


365                 ctoken_ = CanonicalERC20({


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L365:365

</details>

## G038 - Avoid fetching a low-level call's return data by using assembly:

Even if you don't assign the call's second return value, it still gets copied to memory. Use assembly instead to prevent this and save 159 gas.


```solidity
File: contracts/L2/CrossChainOwned.sol


50              (bool success,) = address(this).call(txdata);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L50:50

## G039 - Using msg globals directly, rather than caching the value, saves gas:

For example, use msg.sender directly rather than storing it to a local variable


<details>
<summary>Click to show 5 findings</summary>

```solidity
File: contracts/L1/libs/LibProposing.sol


86                  params.coinbase = msg.sender;


165                         _state.reusableBlobs[meta_.blobHash] = block.timestamp;


165                         _state.reusableBlobs[meta_.blobHash] = block.timestamp;


165                         _state.reusableBlobs[meta_.blobHash] = block.timestamp;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L165:165

```solidity
File: contracts/L1/libs/LibProving.sol


251                     ts.contester = msg.sender;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibProving.sol#L251:251

</details>

## G040 - State variable read in a loop:

The state variable should be cached in and read from a local variable, or accumulated in a local variable then written to storage once outside of the loop, rather than reading/updating it on every iteration of the loop, which will replace each Gwarmaccess (100 gas) with a much cheaper stack read.


<details>
<summary>Click to show 15 findings</summary>

```solidity
File: contracts/L1/provers/Guardians.sol


74              for (uint256 i; i < guardians.length; ++i) {


84                  if (guardianIds[guardian] != 0) revert INVALID_GUARDIAN_SET();


135                     if (count == minGuardians) return true;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/provers/Guardians.sol#L135:135

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol


81                  if (_serialNumIsRevoked[index][serialNumBatch[i]]) {


96                  if (!_serialNumIsRevoked[index][serialNumBatch[i]]) {


240             for (uint256 i; i < CPUSVN_LENGTH; ++i) {


268                         certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.ROOT)][certs[i]


424                     (certDecodedSuccessfully, parsedQuoteCerts[i]) = pemCertLib.decodeCert(


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L424:424

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol


354             for (uint256 i; i < SGX_TCB_CPUSVN_SIZE + 1; ++i) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L354:354

```solidity
File: contracts/automata-attestation/utils/BytesUtils.sol


336                 decoded = uint8(BASE32_HEX_TABLE[uint256(uint8(char)) - 0x30]);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L336:336

```solidity
File: contracts/bridge/Bridge.sol


92                  proofReceipt[msgHash].receivedAt = _timestamp;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/bridge/Bridge.sol#L92:92

```solidity
File: contracts/team/airdrop/ERC721Airdrop.sol


60                  IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L60:60

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol


111                 if (currentNode.decoded.length == BRANCH_NODE_LENGTH) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L111:111

```solidity
File: contracts/verifiers/SgxVerifier.sol


107                 if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();


211                 if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L211:211

</details>

## G041 - Storage re-read via storage pointer:

The instances below point to the second+ access of a state variable, via a storage pointer, within a function. Caching the value replaces each Gwarmaccess (100 gas) with a much cheaper stack read.


<details>
<summary>Click to show 4 findings</summary>

```solidity
File: contracts/L1/libs/LibProving.sol


192                 bool returnLivenessBond = blk.livenessBond > 0 && _proof.data.length == 32


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibProving.sol#L192:192

```solidity
File: contracts/L1/libs/LibVerifying.sol


107             uint32 tid = blk.verifiedTransitionId;


184                     if (ts.prover != blk.assignedProver) {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L184:184

```solidity
File: contracts/team/TimelockTokenPool.sol


198             costToWithdraw = _amountUnlocked * r.grant.costPerToken - r.costPaid;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L198:198

</details>

## G042 - State variables only set in the constructor should be declared immutable:

Avoids a Gsset (20000 gas) in the constructor, and replaces the first access in each transaction (Gcoldsload - 2100 gas) and each access thereafter (Gwarmacces - 100 gas) with a PUSH32 (3 gas).  While strings are not value types, and therefore cannot be immutable/constant if not hard-coded outside of the constructor, the same behavior can be achieved by making the current contract abstract with virtual functions for the string accessors, and having a child contract override the functions with the hard-coded implementation-specific values.


```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol


52          address public owner;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L52:52

```solidity
File: contracts/automata-attestation/utils/SigVerifyLib.sol


18          address private ES256VERIFIER;


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L18:18

## G043 - State variables can be packed into fewer storage slots:

If variables occupying the same slot are both written in the same function or by the constructor, avoids a separate Gsset (20000 gas). Reads of the variables can also be cheaper


```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol


22      contract AutomataDcapV3Attestation is IAttestation {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L22:22

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol


12      contract ERC20Airdrop2 is MerkleClaimable {


```

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L12:12

## G044 - Structs can be packed into fewer storage slots:

Each slot saved can avoid an extra Gsset (20000 gas) for the first setting of the struct. Subsequent reads as well as writes have smaller gas savings


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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/L1/TaikoData.sol#L78:88

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

https://github.com/code-423n4/2024-03-taiko/tree/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L17:31

