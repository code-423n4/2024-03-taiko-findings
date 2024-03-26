The content section shows only 10 examples, subsequent cases are listed as links.

### Gas Risk Issues

| |Issue|Instances| Gas Savings|
|-|:-|:-:|:-:|
| [[G-01](#g-01)] | Alternative Solady library can be used instead of OpenZeppelin to save gas | 34| 34000|
| [[G-02](#g-02)] | Setting the `constructor` to `payable` | 3| 39|
| [[G-03](#g-03)] | Don't initialize state variables with default value | 2| 0|
| [[G-04](#g-04)] | Use assembly to check for `address(0)` | 55| 330|
| [[G-05](#g-05)] | `Internal` functions only called once can be inlined to save gas | 29| 870|
| [[G-06](#g-06)] | `selfbalance()` is cheaper than `address(this).balance` | 6| 0|
| [[G-07](#g-07)] | Usage of `uint`/`int` smaller than 32 bytes (256 bits) incurs overhead | 307| 6754|
| [[G-08](#g-08)] | `>=` costs less gas than `>` | 30| 90|
| [[G-09](#g-09)] | Multiple mappings can be replaced with a single struct mapping | 8| 160000|
| [[G-10](#g-10)] | Structs can be packed into fewer storage slots | 3| 60000|
| [[G-11](#g-11)] | Using `storage` instead of `memory` for structs/arrays saves gas | 6| 25200|
| [[G-12](#g-12)] | State variables should be cached in stack variables rather than re-reading them from storage | 114| 11058|
| [[G-13](#g-13)] | `require()`/`revert()` strings longer than 32 bytes cost extra gas | 30| 90|
| [[G-14](#g-14)] | Stack variable used as a cheaper cache for a state variable is only used once | 86| 258|
| [[G-15](#g-15)] | State Variables can be packed into fewer storage slots | 3| 60000|
| [[G-16](#g-16)] | State variables access within a loop | 17| 9010|
| [[G-17](#g-17)] | State variables only set in the constructor should be declared `immutable` | 2| 40000|
| [[G-18](#g-18)] | Newer versions of solidity are more gas efficient | 81| 0|
| [[G-19](#g-19)] | Consider activating `via-ir` for deploying | 1| 0|
| [[G-20](#g-20)] | Function calls should be cached instead of re-calling the function | 15| 720|
| [[G-21](#g-21)] | Add `unchecked` blocks for divisions where the operands cannot overflow | 15| 2385|
| [[G-22](#g-22)] | Multiplication/division by two should use bit shifting | 10| 200|
| [[G-23](#g-23)] | Consider pre-calculating the address of `address(this)` | 40| 104000|
| [[G-24](#g-24)] | Consider using `bytes32` rather than a `string` | 59| 7552|
| [[G-25](#g-25)] | Optimize Zero Checks Using Assembly | 176| 10208|
| [[G-26](#g-26)] | Consider using `assembly` to write address storage values if the address variable is mutable | 49| 0|
| [[G-27](#g-27)] | Consider Caching Multiple Accesses to Mappings/Arrays | 34| 3400|
| [[G-28](#g-28)] | Optimize Gas by Using Do-While Loops | 54| 13770|
| [[G-29](#g-29)] | Use Assembly for Efficient Event Emission | 55| 99000|
| [[G-30](#g-30)] | Optimize External Calls with Assembly for Memory Efficiency | 92| 20240|
| [[G-31](#g-31)] | Use Assembly for Hash Calculations | 25| 25125|
| [[G-32](#g-32)] | Consider Using Solady's Gas Optimized Lib for Math | 58| 0|
| [[G-33](#g-33)] | Trade-offs Between Modifiers and Internal Functions | 168| 1764000|
| [[G-34](#g-34)] | Optimize Boolean States with `uint256(1/2)` | 10| 170000|
| [[G-35](#g-35)] | Consider Packing Small `uint` When it's Possible | 36| 748800|
| [[G-36](#g-36)] | Avoid Unnecessary Public Variables | 86| 1892000|
| [[G-37](#g-37)] | Optimize by Using Assembly for Low-Level Calls' Return Data | 1| 159|
| [[G-38](#g-38)] | Avoid Zero Transfers to Save Gas | 10| 0|
| [[G-39](#g-39)] | Optimize Unsigned Integer Comparison With Zero | 15| 60|
| [[G-40](#g-40)] | Delete Unused State Variables | 67| 1340000|
| [[G-41](#g-41)] | Optimize Gas by Using Only Named Returns | 162| 7128|
| [[G-42](#g-42)] | Use assembly in place of `abi.decode` to extract `calldata` values more efficiently | 16| 0|
| [[G-43](#g-43)] | Optimize Address Storage Value Management with `assembly` | 22| 0|
| [[G-44](#g-44)] | Use calldata instead of memory for function arguments that do not get mutated | 206| 0|
| [[G-45](#g-45)] | Gas savings can be achieved by changing the model for assigning value to the structure | 31| 8060|
| [[G-46](#g-46)] | Use `Array.unsafeAccess` to avoid repeated array length checks | 118| 247800|
| [[G-47](#g-47)] | Consider using OpenZeppelin's `EnumerateSet` instead of nested mappings | 8| 8000|
| [[G-48](#g-48)] | Counting down in `for` statements is more gas efficient | 45| 360|
| [[G-49](#g-49)] | Do not calculate constants | 2| 0|

### Gas Risk Issues

### [G-01]<a name="g-01"></a> Alternative Solady library can be used instead of OpenZeppelin to save gas

The following OpenZeppelin imports have a [Solady](https://github.com/Vectorized/solady) equivalent, as such they can be used to save GAS as Solady modules have been specifically designed to be as GAS efficient as possible.    

*There are 34 instance(s) of this issue:*


---

	 - contracts/common/AddressResolver.sol

```solidity
 // @audit `Initializable` has Solady alternative
4	import "@openzeppelin/contracts-upgradeable/proxy/utils/Initializable.sol";
```

*GitHub* : [4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L4)


---

	 - contracts/common/EssentialContract.sol

```solidity
 // @audit `UUPSUpgradeable` has Solady alternative
4	import "@openzeppelin/contracts/proxy/utils/UUPSUpgradeable.sol";
```

*GitHub* : [4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L4)


---

	 - contracts/libs/LibAddress.sol

```solidity
 // @audit `ECDSA` has Solady alternative
5	import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol";
```

*GitHub* : [5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L5)


---

	 - contracts/L1/hooks/AssignmentHook.sol

```solidity
 // @audit `IERC20` has Solady alternative
4	import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
...
 // @audit `SafeERC20` has Solady alternative
5	import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```

*GitHub* : [4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L5)


---

	 - contracts/L1/libs/LibProposing.sol

```solidity
 // @audit `IERC20` has Solady alternative
4	import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```

*GitHub* : [4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L4)


---

	 - contracts/L1/libs/LibProving.sol

```solidity
 // @audit `IERC20` has Solady alternative
4	import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```

*GitHub* : [4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L4)


---

	 - contracts/L1/libs/LibVerifying.sol

```solidity
 // @audit `IERC20` has Solady alternative
4	import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```

*GitHub* : [4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L4)


---

	 - contracts/L1/TaikoToken.sol

```solidity
 // @audit `ERC20Upgradeable` has Solady alternative
4	import "@openzeppelin/contracts-upgradeable/token/ERC20/ERC20Upgradeable.sol";
...
 // @audit `ERC20SnapshotUpgradeable` has Solady alternative
5	import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20SnapshotUpgradeable.sol";
```

*GitHub* : [4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L6)


---

	 - contracts/L2/CrossChainOwned.sol


*GitHub* : [4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L4)


---

	 - contracts/L2/TaikoL2.sol


*GitHub* : [4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L5)


---

	 - contracts/tokenvault/BridgedERC20.sol


*GitHub* : [4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L4), [6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L6), [7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L7)


---

	 - contracts/tokenvault/BridgedERC721.sol


*GitHub* : [4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L4)


---

	 - contracts/tokenvault/BridgedERC1155.sol


*GitHub* : [5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L5), [6..7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L6-L7)


---

	 - contracts/tokenvault/ERC1155Vault.sol


*GitHub* : [4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L5)


---

	 - contracts/tokenvault/ERC20Vault.sol


*GitHub* : [4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L6)


---

	 - contracts/tokenvault/ERC721Vault.sol


*GitHub* : [4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L5)


---

	 - contracts/verifiers/SgxVerifier.sol


*GitHub* : [4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L4)


---

	 - contracts/team/airdrop/ERC20Airdrop.sol


*GitHub* : [4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L4)


---

	 - contracts/team/airdrop/ERC20Airdrop2.sol


*GitHub* : [4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L4)


---

	 - contracts/team/airdrop/ERC721Airdrop.sol


*GitHub* : [4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L4)


---

	 - contracts/team/TimelockTokenPool.sol


*GitHub* : [4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L4), [5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L5), [6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L6)

### [G-02]<a name="g-02"></a> Setting the `constructor` to `payable`

Saves ~13 gas per instance

*There are 3 instance(s) of this issue:*


---

	 - contracts/common/EssentialContract.sol

```solidity
64	    constructor() {
```

*GitHub* : [64](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L64)


---

	 - contracts/automata-attestation/AutomataDcapV3Attestation.sol

```solidity
54	    constructor(address sigVerifyLibAddr, address pemCertLibAddr) {
```

*GitHub* : [54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L54)


---

	 - contracts/automata-attestation/utils/SigVerifyLib.sol

```solidity
20	    constructor(address es256Verifier) {
```

*GitHub* : [20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L20)

### [G-03]<a name="g-03"></a> Don't initialize state variables with default value



*There are 2 instance(s) of this issue:*


---

	 - contracts/thirdparty/optimism/trie/MerkleTrie.sol

```solidity
30	    uint8 internal constant PREFIX_EXTENSION_EVEN = 0;
```

*GitHub* : [30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L30)


---

	 - contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

```solidity
18	    bytes4 internal constant SUPPORTED_TEE_TYPE = 0;
```

*GitHub* : [18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L18)

### [G-04]<a name="g-04"></a> Use assembly to check for `address(0)`



*There are 55 instance(s) of this issue:*


---

	 - contracts/common/AddressResolver.sol

```solidity
81	        if (addressManager == address(0)) revert RESOLVER_INVALID_MANAGER();
...
85	        if (!_allowZeroAddress && addr_ == address(0)) {
```

*GitHub* : [81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L81), [85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L85)


---

	 - contracts/common/EssentialContract.sol

```solidity
105	        if (_addressManager == address(0)) revert ZERO_ADDR_MANAGER();
...
110	        _transferOwnership(_owner == address(0) ? msg.sender : _owner);
```

*GitHub* : [105](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L105), [110](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L110)


---

	 - contracts/libs/LibAddress.sol

```solidity
24	        if (_to == address(0)) revert ETH_TRANSFER_FAILED();
```

*GitHub* : [24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L24)


---

	 - contracts/L1/hooks/AssignmentHook.sol

```solidity
109	        if (assignment.feeToken == address(0)) {
...
120	        if (input.tip != 0 && block.coinbase != address(0)) {
```

*GitHub* : [109](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L109), [120](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L120)


---

	 - contracts/L1/libs/LibDepositing.sol

```solidity
44	        address recipient_ = _recipient == address(0) ? msg.sender : _recipient;
```

*GitHub* : [44](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L44)


---

	 - contracts/L1/libs/LibProposing.sol

```solidity
81	        if (params.assignedProver == address(0)) {
...
85	        if (params.coinbase == address(0)) {
```

*GitHub* : [81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L81), [85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L85), [310](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L310), [316](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L316)


---

	 - contracts/L1/libs/LibProving.sol


*GitHub* : [163](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L163), [239](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L239), [224](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L224), [363](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L363)


---

	 - contracts/L1/libs/LibVerifying.sol


*GitHub* : [145](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L145), [148](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L148)


---

	 - contracts/L1/provers/Guardians.sol


*GitHub* : [82](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L82)


---

	 - contracts/L2/TaikoL2.sol


*GitHub* : [172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L172), [173](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L173)


---

	 - contracts/signal/SignalService.sol


*GitHub* : [36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L36)


---

	 - contracts/bridge/Bridge.sol


*GitHub* : [124](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L124), [124](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L124), [270](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L270), [291](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L291), [398](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L398)


---

	 - contracts/tokenvault/BridgedERC20Base.sol


*GitHub* : [102](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L102)


---

	 - contracts/tokenvault/BaseNFTVault.sol


*GitHub* : [149](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L149)


---

	 - contracts/tokenvault/ERC1155Vault.sol


*GitHub* : [64](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L64), [108](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L108), [249](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L249), [293](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L293)


---

	 - contracts/tokenvault/ERC20Vault.sol


*GitHub* : [158](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L158), [158](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L158), [170](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L170), [215](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L215), [227](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L227), [267](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L267), [358](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L358), [397](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L397)


---

	 - contracts/tokenvault/ERC721Vault.sol


*GitHub* : [50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L50), [91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L91), [195](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L195), [230](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L230)


---

	 - contracts/tokenvault/LibBridgedToken.sol


*GitHub* : [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L21)


---

	 - contracts/verifiers/SgxVerifier.sol


*GitHub* : [107](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L107), [124](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L124), [215](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L215), [234](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L234)


---

	 - contracts/team/TimelockTokenPool.sol


*GitHub* : [121](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L121), [124](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L124), [127](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L127), [136](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L136), [169](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L169)

### [G-05]<a name="g-05"></a> `Internal` functions only called once can be inlined to save gas



*There are 29 instance(s) of this issue:*


---

	 - contracts/common/AddressResolver.sol

```solidity
58	    function __AddressResolver_init(address _addressManager) internal virtual onlyInitializing {
```

*GitHub* : [58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L58)


---

	 - contracts/common/EssentialContract.sol

```solidity
140	    function _inNonReentrant() internal view returns (bool) {
```

*GitHub* : [140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L140)


---

	 - contracts/libs/LibAddress.sol

```solidity
22	    function sendEther(address _to, uint256 _amount, uint256 _gasLimit) internal {
```

*GitHub* : [22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L22)


---

	 - contracts/L1/libs/LibDepositing.sol

```solidity
122	    function canDepositEthToL2(
123	        TaikoData.State storage _state,
124	        TaikoData.Config memory _config,
125	        uint256 _amount
126	    )
127	        internal
128	        view
129	        returns (bool)
130	    {
```

*GitHub* : [122..130](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L122-L130)


---

	 - contracts/L1/libs/LibProposing.sol

```solidity
287	    function isBlobReusable(
288	        TaikoData.State storage _state,
289	        TaikoData.Config memory _config,
290	        bytes32 _blobHash
291	    )
292	        internal
293	        view
294	        returns (bool)
295	    {
```

*GitHub* : [287..295](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L287-L295)


---

	 - contracts/L1/libs/LibUtils.sol

```solidity
70	    function getTransitionId(
71	        TaikoData.State storage _state,
72	        TaikoData.Block storage _blk,
73	        uint64 _slot,
74	        bytes32 _parentHash
75	    )
76	        internal
77	        view
78	        returns (uint32 tid_)
79	    {
```

*GitHub* : [70..79](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L70-L79)


---

	 - contracts/L1/provers/Guardians.sol

```solidity
111	    function approve(uint256 _operationId, bytes32 _hash) internal returns (bool approved_) {
...
124	    function deleteApproval(bytes32 _hash) internal {
```

*GitHub* : [111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L111), [124](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L124)


---

	 - contracts/L1/TaikoL1.sol

```solidity
220	    function _authorizePause(address)
221	        internal
222	        view
223	        virtual
224	        override
225	        onlyFromOwnerOrNamed("chain_pauser")
226	    { }
```

*GitHub* : [220..226](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L220-L226)


---

	 - contracts/L1/TaikoToken.sol

```solidity
105	    function _mint(
106	        address _to,
107	        uint256 _amount
108	    )
109	        internal
110	        override(ERC20Upgradeable, ERC20VotesUpgradeable)
111	    {
```

*GitHub* : [105..111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L105-L111), [115..121](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L115-L121)


---

	 - contracts/L2/CrossChainOwned.sol


*GitHub* : [60..68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L60-L68)


---

	 - contracts/signal/SignalService.sol


*GitHub* : [206..220](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L206-L220)


---

	 - contracts/tokenvault/BridgedERC20.sol


*GitHub* : [163..169](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L163-L169), [173..179](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L173-L179)


---

	 - contracts/tokenvault/BridgedERC20Base.sol


*GitHub* : [97](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L97), [99](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L99)


---

	 - contracts/thirdparty/optimism/Bytes.sol


*GitHub* : [15..23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L15-L23)


---

	 - contracts/thirdparty/optimism/rlp/RLPReader.sol


*GitHub* : [53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L53), [109](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L109)


---

	 - contracts/thirdparty/optimism/rlp/RLPWriter.sol


*GitHub* : [13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L13)


---

	 - contracts/thirdparty/optimism/trie/MerkleTrie.sol


*GitHub* : [68..76](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L68-L76)


---

	 - contracts/team/airdrop/MerkleClaimable.sol


*GitHub* : [77..86](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L77-L86)


---

	 - contracts/automata-attestation/AutomataDcapV3Attestation.sol


*GitHub* : [126..131](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L126-L131)


---

	 - contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol


*GitHub* : [267..274](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L267-L274)


---

	 - contracts/automata-attestation/utils/BytesUtils.sol


*GitHub* : [56..67](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L56-L67)


---

	 - contracts/automata-attestation/utils/RsaVerify.sol


*GitHub* : [43..52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L43-L52), [212..221](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L212-L221)


---

	 - contracts/automata-attestation/utils/X509DateUtils.sol


*GitHub* : [34..45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L34-L45)

### [G-06]<a name="g-06"></a> `selfbalance()` is cheaper than `address(this).balance`



*There are 6 instance(s) of this issue:*


---

	 - contracts/L1/hooks/AssignmentHook.sol

```solidity
125	        if (address(this).balance > 0) {
...
126	            taikoL1Address.sendEther(address(this).balance);
```

*GitHub* : [125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L125), [126](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L126)


---

	 - contracts/L1/libs/LibProposing.sol

```solidity
253	                IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }(
...
260	            if (address(this).balance != 0) {
...
261	                msg.sender.sendEther(address(this).balance);
```

*GitHub* : [253](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L253), [260](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L260), [261](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L261)


---

	 - contracts/L2/TaikoL2.sol

```solidity
174	            _to.sendEther(address(this).balance);
```

*GitHub* : [174](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L174)

### [G-07]<a name="g-07"></a> Usage of `uint`/`int` smaller than 32 bytes (256 bits) incurs overhead

When using elements that are smaller than 32 bytes, your contract’s gas usage may be higher. This is because the EVM operates on 32 bytes at a time. Therefore, if the element is smaller than that, the EVM must use more operations in order to reduce the size of the element from 32 bytes to the desired size.

Each operation involving a uint8 costs an extra 22-28 gas (depending on whether the other operand is also a variable of type uint8) as compared to ones involving uint256, due to the compiler having to clear the higher bits of the memory word before operating on the uint8, as well as the associated stack operations of doing so. Use a larger size then downcast where needed.

https://docs.soliditylang.org/en/v0.8.11/internals/layout_in_storage.html

Use a larger size then downcast where needed.

*There are 307 instance(s) of this issue:*


---

	 - contracts/common/IAddressManager.sol

```solidity
14	    function getAddress(uint64 _chainId, bytes32 _name) external view returns (address);
```

*GitHub* : [14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressManager.sol#L14)


---

	 - contracts/common/AddressManager.sol

```solidity
22	        uint64 indexed chainId, bytes32 indexed name, address newAddress, address oldAddress
...
39	        uint64 _chainId,
...
54	    function getAddress(uint64 _chainId, bytes32 _name) public view override returns (address) {
```

*GitHub* : [22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L22), [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L39), [54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L54)


---

	 - contracts/common/IAddressResolver.sol

```solidity
35	        uint64 _chainId,
```

*GitHub* : [35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressResolver.sol#L35)


---

	 - contracts/common/AddressResolver.sol

```solidity
19	    error RESOLVER_ZERO_ADDR(uint64 chainId, bytes32 name);
...
44	        uint64 _chainId,
...
73	        uint64 _chainId,
```

*GitHub* : [19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L19), [44](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L44), [73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L73)


---

	 - contracts/common/EssentialContract.sol

```solidity
21	    uint8 private __reentry;
...
23	    uint8 private __paused;
```

*GitHub* : [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L21), [23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L23), [119](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L119), [130](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L130)


---

	 - contracts/L1/hooks/AssignmentHook.sol


*GitHub* : [20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L20), [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L21), [22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L22), [166](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L166)


---

	 - contracts/L1/ITaikoL1.sol


*GitHub* : [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/ITaikoL1.sol#L27), [31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/ITaikoL1.sol#L31)


---

	 - contracts/L1/libs/LibDepositing.sol


*GitHub* : [83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L83), [84](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L84), [85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L85), [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L93)


---

	 - contracts/L1/libs/LibProposing.sol


*GitHub* : [34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L34)


---

	 - contracts/L1/libs/LibProving.sol


*GitHub* : [36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L36), [37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L37), [50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L50), [51](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L51), [115](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L115), [129](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L129), [100](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L100), [273](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L273), [276](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L276), [405](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L405)


---

	 - contracts/L1/libs/LibUtils.sol


*GitHub* : [38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L38), [42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L42), [26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L26), [55](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L55), [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L59), [73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L73), [78](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L78)


---

	 - contracts/L1/libs/LibVerifying.sol


*GitHub* : [34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L34), [35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L35), [100](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L100), [102](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L102), [107](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L107), [117](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L117), [213](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L213), [89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L89), [234](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L234), [227](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L227)


---

	 - contracts/L1/provers/Guardians.sol


*GitHub* : [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L27), [30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L30), [37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L37), [55](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L55)


---

	 - contracts/L1/TaikoData.sol


*GitHub* : [15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L15), [20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L20), [22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L22), [24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L24), [26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L26), [28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L28), [30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L30), [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L39), [46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L46), [48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L48), [50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L50), [52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L52), [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L59), [64](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L64), [65](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L65), [69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L69), [83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L83), [84](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L84), [101](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L101), [102](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L102), [103](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L103), [104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L104), [105](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L105), [106](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L106), [107](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L107), [127](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L127), [129](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L129), [130](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L130), [131](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L131), [132](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L132), [140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L140), [141](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L141), [142](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L142), [143](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L143), [144](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L144), [145](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L145), [152](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L152), [153](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L153), [162](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L162), [163](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L163), [164](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L164), [165](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L165), [169](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L169), [170](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L170), [172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L172), [173](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L173), [174](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L174), [175](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L175)


---

	 - contracts/L1/TaikoEvents.sol


*GitHub* : [24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L24), [43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L43), [44](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L44), [57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L57), [58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L58), [71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L71), [72](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L72)


---

	 - contracts/L1/TaikoL1.sol


*GitHub* : [94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L94), [76](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L76), [100](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L100), [150](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L150), [145](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L145), [163](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L163)


---

	 - contracts/L1/tiers/ITierProvider.sol


*GitHub* : [10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L10), [11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L11), [12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L12), [13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L13), [14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L14), [22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L22), [33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L33)


---

	 - contracts/L1/tiers/DevnetTierProvider.sol


*GitHub* : [20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L20), [54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L54)


---

	 - contracts/L1/tiers/MainnetTierProvider.sol


*GitHub* : [20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L20), [66](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L66)


---

	 - contracts/L1/tiers/TestnetTierProvider.sol


*GitHub* : [20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L20), [66](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L66)


---

	 - contracts/L2/CrossChainOwned.sol


*GitHub* : [16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L16), [19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L19), [26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L26), [42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L42), [63](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L63)


---

	 - contracts/L2/TaikoL2.sol


*GitHub* : [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L27), [28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L28), [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L47), [50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L50), [57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L57), [74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L74), [75](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L75), [110](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L110), [111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L111), [186](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L186), [187](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L187), [200](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L200), [254](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L254), [255](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L255), [259](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L259)


---

	 - contracts/L2/TaikoL2EIP1559Configurable.sol


*GitHub* : [18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L18), [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L27)


---

	 - contracts/signal/ISignalService.sol


*GitHub* : [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L21), [22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L22), [37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L37), [38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L38), [69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L69), [71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L71), [85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L85), [106](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L106), [108](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L108), [123](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L123), [125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L125), [129](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L129), [138](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L138), [140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L140)


---

	 - contracts/signal/SignalService.sol


*GitHub* : [69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L69), [71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L71), [97](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L97), [84](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L84), [138](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L138), [140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L140), [159](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L159), [161](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L161), [165](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L165), [178](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L178), [180](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L180), [195](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L195), [207](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L207), [236](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L236), [238](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L238), [273](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L273), [274](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L274)


---

	 - contracts/bridge/IBridge.sol


*GitHub* : [19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L19), [24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L24), [26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L26), [51](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L51), [63](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L63)


---

	 - contracts/bridge/Bridge.sol


*GitHub* : [31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L31), [64](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L64), [89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L89), [168](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L168), [230](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L230), [392](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L392), [541](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L541), [559](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L559), [580](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L580)


---

	 - contracts/tokenvault/BridgedERC20.sol


*GitHub* : [24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L24), [57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L57), [117](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L117)


---

	 - contracts/tokenvault/BaseNFTVault.sol


*GitHub* : [13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L13), [25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L25), [70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L70), [90](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L90), [126](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L126)


---

	 - contracts/tokenvault/ERC20Vault.sol


*GitHub* : [24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L24), [26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L26), [33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L33), [69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L69), [87](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L87), [102](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L102), [130](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L130)


---

	 - contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol


*GitHub* : [29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L29)


---

	 - contracts/thirdparty/optimism/trie/MerkleTrie.sol


*GitHub* : [141](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L141), [142](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L142), [134](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L134)


---

	 - contracts/verifiers/IVerifier.sol


*GitHub* : [14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/IVerifier.sol#L14)


---

	 - contracts/verifiers/SgxVerifier.sol


*GitHub* : [26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L26), [154](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L154), [204](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L204)


---

	 - contracts/team/airdrop/ERC20Airdrop.sol


*GitHub* : [29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L29), [30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L30), [69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L69)


---

	 - contracts/team/airdrop/ERC20Airdrop2.sol


*GitHub* : [28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L28), [56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L56), [57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L57), [61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L61)


---

	 - contracts/team/airdrop/ERC721Airdrop.sol


*GitHub* : [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L27), [28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L28)


---

	 - contracts/team/airdrop/MerkleClaimable.sol


*GitHub* : [18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L18), [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L21), [46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L46), [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L47), [57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L57), [58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L58), [90](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L90), [90](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L90)


---

	 - contracts/team/TimelockTokenPool.sol


*GitHub* : [29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L29), [31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L31), [34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L34), [37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L37), [40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L40), [43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L43), [46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L46), [49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L49), [53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L53), [54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L54), [68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L68), [71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L71), [74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L74), [77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L77), [92](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L92), [99](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L99), [99](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L99), [152](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L152), [197](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L197), [180](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L180), [181](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L181), [182](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L182), [183](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L183), [184](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L184), [211](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L211), [211](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L211), [226](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L226), [225](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L225), [235](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L235), [239](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L239), [246](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L246), [247](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L247), [248](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L248), [249](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L249), [253](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L253), [273](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L273), [273](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L273), [273](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L273)


---

	 - contracts/automata-attestation/lib/EnclaveIdStruct.sol


*GitHub* : [10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/EnclaveIdStruct.sol#L10), [23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/EnclaveIdStruct.sol#L23)


---

	 - contracts/automata-attestation/lib/PEMCertChainLib.sol


*GitHub* : [358](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L358)


---

	 - contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol


*GitHub* : [106](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L106), [249](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L249), [250](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L250)


---

	 - contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol


*GitHub* : [26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L26), [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L27), [34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L34), [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L39), [43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L43)


---

	 - contracts/automata-attestation/utils/Asn1Decode.sol


*GitHub* : [189](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L189), [190](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L190), [196](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L196)


---

	 - contracts/automata-attestation/utils/BytesUtils.sol


*GitHub* : [188](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L188), [198](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L198), [211](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L211), [332](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L332)


---

	 - contracts/automata-attestation/utils/X509DateUtils.sol


*GitHub* : [9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L9), [10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L10), [11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L11), [12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L12), [13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L13), [14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L14), [15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L15), [48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L48), [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L59), [35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L35), [36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L36), [37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L37), [38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L38), [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L39), [40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L40), [71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L71)

### [G-08]<a name="g-08"></a> `>=` costs less gas than `>`

The compiler uses opcodes `GT` and `ISZERO` for solidity code that uses `>`, but only requires LT for `>=`, which saves 3 gas. Similarly for `<=`.

*There are 30 instance(s) of this issue:*


---

	 - contracts/L1/hooks/AssignmentHook.sol

```solidity
125	        if (address(this).balance > 0) {
```

*GitHub* : [125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L125)


---

	 - contracts/L1/libs/LibProving.sol

```solidity
192	            bool returnLivenessBond = blk.livenessBond > 0 && _proof.data.length == 32
```

*GitHub* : [192](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L192)


---

	 - contracts/L1/libs/LibVerifying.sol

```solidity
212	            if (numBlocksVerified > 0) {
...
256	            || _config.ethDepositMaxCountPerBlock > 32
```

*GitHub* : [212](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L212), [256](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L256)


---

	 - contracts/L2/TaikoL2.sol

```solidity
234	            for (uint256 i; i < 255 && _blockId >= i + 1; ++i) {
...
262	        if (gasExcess > 0) {
...
275	            if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {
...
279	            if (numL1Blocks > 0) {
```

*GitHub* : [234](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L234), [262](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L262), [275](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L275), [279](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L279)


---

	 - contracts/signal/SignalService.sol

```solidity
120	            bool isFullProof = hop.accountProof.length > 0;
```

*GitHub* : [120](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L120)


---

	 - contracts/thirdparty/optimism/rlp/RLPReader.sol

```solidity
38	            _in.length > 0,
```

*GitHub* : [38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L38), [153](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L153), [259](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L259), [213](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L213)


---

	 - contracts/thirdparty/optimism/rlp/RLPWriter.sol


*GitHub* : [14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L14), [33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L33), [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L59)


---

	 - contracts/thirdparty/optimism/trie/MerkleTrie.sol


*GitHub* : [77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L77), [173](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L173), [120](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L120), [221](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L221)


---

	 - contracts/team/TimelockTokenPool.sol


*GitHub* : [277](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L277), [275](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L275)


---

	 - contracts/automata-attestation/AutomataDcapV3Attestation.sol


*GitHub* : [420](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L420)


---

	 - contracts/automata-attestation/lib/PEMCertChainLib.sol


*GitHub* : [56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L56), [358](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L358)


---

	 - contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol


*GitHub* : [218](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L218), [218](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L218), [281](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L281)


---

	 - contracts/automata-attestation/utils/BytesUtils.sol


*GitHub* : [90](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L90)


---

	 - contracts/automata-attestation/utils/X509DateUtils.sol


*GitHub* : [18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L18)

### [G-09]<a name="g-09"></a> Multiple mappings can be replaced with a single struct mapping

Saves a storage slot for the mapping. Depending on the circumstances and sizes of types, can avoid a Gsset (20000 gas) per mapping combined. Reads and subsequent writes can also be cheaper when a function requires both values and they both fit in the same storage slot.

*There are 8 instance(s) of this issue:*


---

	 - contracts/bridge/Bridge.sol

```solidity
35	    mapping(bytes32 msgHash => Status status) public messageStatus;
...
46	    mapping(bytes32 msgHash => ProofReceipt receipt) public proofReceipt;
```

*GitHub* : [35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L35), [46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L46)


---

	 - contracts/tokenvault/ERC20Vault.sol

```solidity
45	    mapping(address btoken => CanonicalERC20 canonical) public bridgedToCanonical;
...
52	    mapping(address btoken => bool blacklisted) public btokenBlacklist;
```

*GitHub* : [45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L45), [52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L52)


---

	 - contracts/team/airdrop/ERC20Airdrop2.sol

```solidity
22	    mapping(address addr => uint256 amountClaimed) public claimedAmount;
...
25	    mapping(address addr => uint256 amountWithdrawn) public withdrawnAmount;
```

*GitHub* : [22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L22), [25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L25)


---

	 - contracts/automata-attestation/AutomataDcapV3Attestation.sol

```solidity
39	    mapping(bytes32 enclave => bool trusted) private _trustedUserMrEnclave;
...
40	    mapping(bytes32 signer => bool trusted) private _trustedUserMrSigner;
```

*GitHub* : [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L39), [40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L40)

### [G-10]<a name="g-10"></a> Structs can be packed into fewer storage slots

Each slot saved can avoid an extra Gsset (20000 gas) for the first setting of the struct. Subsequent reads as well as writes have smaller gas savings

*There are 3 instance(s) of this issue:*


---

	 - contracts/L1/TaikoData.sol

```solidity
10	    struct Config {
11	        // ---------------------------------------------------------------------
12	        // Group 1: General configs
13	        // ---------------------------------------------------------------------
14	        // The chain ID of the network where Taiko contracts are deployed.
15	        uint64 chainId;
16	        // ---------------------------------------------------------------------
17	        // Group 2: Block level configs
18	        // ---------------------------------------------------------------------
19	        // The maximum number of proposals allowed in a single block.
20	        uint64 blockMaxProposals;
21	        // Size of the block ring buffer, allowing extra space for proposals.
22	        uint64 blockRingBufferSize;
23	        // The maximum number of verifications allowed when a block is proposed.
24	        uint64 maxBlocksToVerifyPerProposal;
25	        // The maximum gas limit allowed for a block.
26	        uint32 blockMaxGasLimit;
27	        // The maximum allowed bytes for the proposed transaction list calldata.
28	        uint24 blockMaxTxListBytes;
29	        // The max period in seconds that a blob can be reused for DA.
30	        uint24 blobExpiry;
31	        // True if EIP-4844 is enabled for DA
32	        bool blobAllowedForDA;
33	        // True if blob can be reused
34	        bool blobReuseEnabled;
35	        // ---------------------------------------------------------------------
36	        // Group 3: Proof related configs
37	        // ---------------------------------------------------------------------
38	        // The amount of Taiko token as a prover liveness bond
39	        uint96 livenessBond;
40	        // ---------------------------------------------------------------------
41	        // Group 4: ETH deposit related configs
42	        // ---------------------------------------------------------------------
43	        // The size of the ETH deposit ring buffer.
44	        uint256 ethDepositRingBufferSize;
45	        // The minimum number of ETH deposits allowed per block.
46	        uint64 ethDepositMinCountPerBlock;
47	        // The maximum number of ETH deposits allowed per block.
48	        uint64 ethDepositMaxCountPerBlock;
49	        // The minimum amount of ETH required for a deposit.
50	        uint96 ethDepositMinAmount;
51	        // The maximum amount of ETH allowed for a deposit.
52	        uint96 ethDepositMaxAmount;
53	        // The gas cost for processing an ETH deposit.
54	        uint256 ethDepositGas;
55	        // The maximum fee allowed for an ETH deposit.
56	        uint256 ethDepositMaxFee;
57	        // The max number of L2 blocks that can stay unsynced on L1 (a value of zero disables
58	        // syncing)
59	        uint8 blockSyncThreshold;
60	    }
...
78	    struct BlockParams {
79	        address assignedProver;
80	        address coinbase;
81	        bytes32 extraData;
82	        bytes32 blobHash;
83	        uint24 txListByteOffset;
84	        uint24 txListByteSize;
85	        bool cacheBlobForReuse;
86	        bytes32 parentMetaHash;
87	        HookCall[] hookCalls;
88	    }
```

*GitHub* : [10..60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L10-L60), [78..88](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L78-L88)


---

	 - contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol

```solidity
17	    struct EnclaveReport {
18	        bytes16 cpuSvn;
19	        bytes4 miscSelect;
20	        bytes28 reserved1;
21	        bytes16 attributes;
22	        bytes32 mrEnclave;
23	        bytes32 reserved2;
24	        bytes32 mrSigner;
25	        bytes reserved3; // 96 bytes
26	        uint16 isvProdId;
27	        uint16 isvSvn;
28	        bytes reserved4; // 60 bytes
29	        bytes reportData; // 64 bytes - For QEReports, this contains the hash of the concatenation
30	            // of attestation key and QEAuthData
31	    }
```

*GitHub* : [17..31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L17-L31)

### [G-11]<a name="g-11"></a> Using `storage` instead of `memory` for structs/arrays saves gas

When fetching data from a storage location, assigning the data to a `memory` variable causes all fields of the struct/array to be read from storage, which incurs a Gcoldsload (**2100 gas**) for *each* field of the struct/array. If the fields are read from the new memory variable, they incur an additional `MLOAD` rather than a cheap stack read. Instead of declearing the variable with the `memory` keyword, declaring the variable with the `storage` keyword and caching any fields that need to be re-read in stack variables, will be much cheaper, only incuring the Gcoldsload for the fields actually read. The only time it makes sense to read the whole struct/array into a `memory` variable, is if the full struct/array is being returned by the function, is being passed to a function that requires `memory`, or if the array/struct is being read from another `memory` array/struct

*There are 6 instance(s) of this issue:*


---

	 - contracts/L1/libs/LibProposing.sol

```solidity
93	        TaikoData.SlotB memory b = _state.slotB;
```

*GitHub* : [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L93)


---

	 - contracts/L1/libs/LibProving.sol

```solidity
110	        TaikoData.SlotB memory b = _state.slotB;
```

*GitHub* : [110](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L110)


---

	 - contracts/L1/libs/LibUtils.sol

```solidity
33	        TaikoData.SlotB memory b = _state.slotB;
```

*GitHub* : [33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L33)


---

	 - contracts/L1/libs/LibVerifying.sol

```solidity
99	        TaikoData.SlotB memory b = _state.slotB;
```

*GitHub* : [99](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L99)


---

	 - contracts/tokenvault/ERC20Vault.sol

```solidity
171	            CanonicalERC20 memory ctoken = bridgedToCanonical[btokenOld_];
```

*GitHub* : [171](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L171)


---

	 - contracts/automata-attestation/AutomataDcapV3Attestation.sol

```solidity
180	        EnclaveIdStruct.EnclaveId memory enclaveId = qeIdentity;
```

*GitHub* : [180](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L180)

### [G-12]<a name="g-12"></a> State variables should be cached in stack variables rather than re-reading them from storage

The instances below point to the second+ access of a state variable within a function. Caching of a state variable replaces each Gwarmaccess (**100 gas**) with a much cheaper stack read. Other less obvious fixes/optimizations include having local memory caches of state variable structs, or having local caches of state variable contracts/addresses.

*There are 114 instance(s) of this issue:*


---

	 - contracts/common/AddressManager.sol

```solidity
// @audit State variable `__addresses` called 2 times in one function
47	        address oldAddress = __addresses[_chainId][_name];
...
// @audit State variable `__addresses` called 2 times in one function
49	        __addresses[_chainId][_name] = _newAddress;
```

*GitHub* : [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L47), [49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L49)


---

	 - contracts/common/AddressResolver.sol

```solidity
// @audit State variable `addressManager` called 2 times in one function
81	        if (addressManager == address(0)) revert RESOLVER_INVALID_MANAGER();
...
// @audit State variable `addressManager` called 2 times in one function
83	        addr_ = payable(IAddressManager(addressManager).getAddress(_chainId, _name));
```

*GitHub* : [81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L81), [83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L83)


---

	 - contracts/L1/provers/Guardians.sol

```solidity
// @audit State variable `guardianIds` called 3 times in one function
75	            delete guardianIds[guardians[i]];
...
// @audit State variable `guardianIds` called 3 times in one function
84	            if (guardianIds[guardian] != 0) revert INVALID_GUARDIAN_SET();
...
// @audit State variable `guardianIds` called 3 times in one function
88	            guardianIds[guardian] = guardians.length;
...
// @audit State variable `guardians` called 5 times in one function
74	        for (uint256 i; i < guardians.length; ++i) {
...
// @audit State variable `guardians` called 5 times in one function
75	            delete guardianIds[guardians[i]];
...
// @audit State variable `guardians` called 5 times in one function
77	        delete guardians;
```

*GitHub* : [75](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L75), [84](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L84), [88](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L88), [74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L74), [75](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L75), [77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L77), [87](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L87), [88](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L88), [92](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L92), [95](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L95)


---

	 - contracts/L1/provers/Guardians.sol


*GitHub* : [116](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L116), [119](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L119), [116](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L116), [119](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L119)


---

	 - contracts/L1/TaikoL1.sol


*GitHub* : [67](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L67), [69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L69), [70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L70)


---

	 - contracts/L1/TaikoL1.sol


*GitHub* : [94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L94), [96](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L96)


---

	 - contracts/L1/TaikoL1.sol


*GitHub* : [151](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L151), [154](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L154)


---

	 - contracts/L1/TaikoL1.sol


*GitHub* : [181](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L181), [182](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L182)


---

	 - contracts/L2/CrossChainOwned.sol


*GitHub* : [43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L43), [53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L53)


---

	 - contracts/L2/TaikoL2.sol


*GitHub* : [140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L140), [157](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L157), [145](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L145), [151](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L151), [132](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L132), [155](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L155)


---

	 - contracts/L2/TaikoL2.sol


*GitHub* : [262](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L262), [265](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L265), [275](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L275), [275](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L275), [276](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L276)


---

	 - contracts/signal/SignalService.sol


*GitHub* : [57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L57), [58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L58)


---

	 - contracts/signal/SignalService.sol


*GitHub* : [247](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L247), [248](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L248)


---

	 - contracts/bridge/Bridge.sol


*GitHub* : [109](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L109), [110](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L110)


---

	 - contracts/bridge/Bridge.sol


*GitHub* : [166](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L166), [191](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L191), [168](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L168), [184](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L184), [190](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L190)


---

	 - contracts/bridge/Bridge.sol


*GitHub* : [230](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L230), [243](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L243), [250](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L250), [264](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L264)


---

	 - contracts/bridge/Bridge.sol


*GitHub* : [516](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L516), [518](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L518)


---

	 - contracts/tokenvault/adapters/USDCAdapter.sol


*GitHub* : [48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L48), [49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L49)


---

	 - contracts/tokenvault/BridgedERC20Base.sol


*GitHub* : [45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L45), [49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L49), [45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L45), [50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L50)


---

	 - contracts/tokenvault/BridgedERC20Base.sol


*GitHub* : [61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L61), [63](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L63)


---

	 - contracts/tokenvault/BridgedERC20Base.sol


*GitHub* : [80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L80), [82](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L82)


---

	 - contracts/tokenvault/ERC1155Vault.sol


*GitHub* : [249](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L249), [250](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L250)


---

	 - contracts/tokenvault/ERC20Vault.sol


*GitHub* : [158](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L158), [171](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L171), [180](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L180), [188](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L188), [162](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L162), [181](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L181), [168](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L168), [189](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L189)


---

	 - contracts/tokenvault/ERC20Vault.sol


*GitHub* : [358](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L358), [359](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L359)


---

	 - contracts/tokenvault/ERC721Vault.sol


*GitHub* : [195](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L195), [196](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L196)


---

	 - contracts/verifiers/SgxVerifier.sol


*GitHub* : [107](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L107), [109](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L109), [111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L111)


---

	 - contracts/verifiers/SgxVerifier.sol


*GitHub* : [211](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L211), [213](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L213), [217](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L217), [218](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L218), [220](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220), [222](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L222)


---

	 - contracts/verifiers/SgxVerifier.sol


*GitHub* : [235](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L235), [236](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L236), [237](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L237)


---

	 - contracts/team/airdrop/ERC20Airdrop.sol


*GitHub* : [63](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L63), [71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L71)


---

	 - contracts/team/airdrop/ERC20Airdrop2.sol


*GitHub* : [114](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L114), [118](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L118), [118](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L118), [118](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L118), [118](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L118)


---

	 - contracts/team/airdrop/MerkleClaimable.sol


*GitHub* : [70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L70), [73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L73)


---

	 - contracts/team/TimelockTokenPool.sol


*GitHub* : [137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L137), [142](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L142)


---

	 - contracts/team/TimelockTokenPool.sol


*GitHub* : [219](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L219), [220](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L220)


---

	 - contracts/automata-attestation/AutomataDcapV3Attestation.sol


*GitHub* : [81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L81), [84](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L84)


---

	 - contracts/automata-attestation/AutomataDcapV3Attestation.sol


*GitHub* : [96](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L96), [99](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L99)


---

	 - contracts/automata-attestation/AutomataDcapV3Attestation.sol


*GitHub* : [123](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L123), [123](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L123)


---

	 - contracts/automata-attestation/AutomataDcapV3Attestation.sol


*GitHub* : [268](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L268), [271](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L271)

### [G-13]<a name="g-13"></a> `require()`/`revert()` strings longer than 32 bytes cost extra gas

Each extra memory word of bytes past the original 32 [incurs an MSTORE](https://gist.github.com/hrkrshnn/ee8fabd532058307229d65dcd5836ddc#consider-having-short-revert-strings)

*There are 30 instance(s) of this issue:*


---

	 - contracts/thirdparty/optimism/rlp/RLPReader.sol

```solidity
37	        require(
38	            _in.length > 0,
39	            "RLPReader: length of an RLP item must be greater than zero to be decodable"
40	        );
...
56	        require(
57	            itemType == RLPItemType.LIST_ITEM,
58	            "RLPReader: decoded item type for list is not a list item"
59	        );
...
61	        require(
62	            listOffset + listLength == _in.length,
63	            "RLPReader: list item has an invalid data remainder"
64	        );
...
112	        require(
113	            itemType == RLPItemType.DATA_ITEM,
114	            "RLPReader: decoded item type for bytes is not a data item"
115	        );
...
117	        require(
118	            _in.length == itemOffset + itemLength,
119	            "RLPReader: bytes value contains an invalid remainder"
120	        );
...
152	        require(
153	            _in.length > 0,
154	            "RLPReader: length of an RLP item must be greater than zero to be decodable"
155	        );
...
238	            require(
239	                _in.length > lenOfListLen,
240	                "RLPReader: length of content must be > than length of list length (long list)"
241	            );
...
248	            require(
249	                firstByteOfContent != 0x00,
250	                "RLPReader: length of content must not have any leading zeros (long list)"
251	            );
...
258	            require(
259	                listLen > 55,
260	                "RLPReader: length of content must be greater than 55 bytes (long list)"
261	            );
...
263	            require(
264	                _in.length > lenOfListLen + listLen,
265	                "RLPReader: length of content must be greater than total length (long list)"
266	            );
```

*GitHub* : [37..40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L37-L40), [56..59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L56-L59), [61..64](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L61-L64), [112..115](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L112-L115), [117..120](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L117-L120), [152..155](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L152-L155), [238..241](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L238-L241), [248..251](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L248-L251), [258..261](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L258-L261), [263..266](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L263-L266), [228..231](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L228-L231), [192..195](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L192-L195), [202..205](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L202-L205), [212..215](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L212-L215), [217..220](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L217-L220), [172..175](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L172-L175), [182..185](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L182-L185)


---

	 - contracts/thirdparty/optimism/trie/MerkleTrie.sol


*GitHub* : [89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L89), [105..108](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L105-L108), [99..102](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L99-L102), [194](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L194), [150..153](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L150-L153), [191](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L191), [162..165](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L162-L165), [172..175](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L172-L175), [178..181](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L178-L181), [119..122](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L119-L122), [125..128](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L125-L128), [198](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L198)


---

	 - contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol


*GitHub* : [87..90](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L87-L90)

### [G-14]<a name="g-14"></a> Stack variable used as a cheaper cache for a state variable is only used once

If the variable is only accessed once, it's cheaper to use the state variable directly that one time, and save the 3 gas the extra stack assignment would spend

*There are 86 instance(s) of this issue:*


---

	 - contracts/libs/Lib4844.sol

```solidity
30	    function evaluatePoint(
31	        bytes32 _blobHash,
32	        uint256 _x,
33	        uint256 _y,
34	        bytes1[48] memory _commitment,
35	        bytes1[48] memory _pointProof
36	    )
37	        internal
38	        view
39	    {
```

*GitHub* : [30..39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L30-L39)


---

	 - contracts/libs/LibAddress.sol

```solidity
22	    function sendEther(address _to, uint256 _amount, uint256 _gasLimit) internal {
...
46	    function supportsInterface(
47	        address _addr,
48	        bytes4 _interfaceId
49	    )
50	        internal
51	        view
52	        returns (bool result_)
53	    {
```

*GitHub* : [22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L22), [46..53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L46-L53)


---

	 - contracts/libs/LibTrieProof.sol

```solidity
34	    function verifyMerkleProof(
35	        bytes32 _rootHash,
36	        address _addr,
37	        bytes32 _slot,
38	        bytes32 _value,
39	        bytes[] memory _accountProof,
40	        bytes[] memory _storageProof
41	    )
42	        internal
43	        pure
44	        returns (bytes32 storageRoot_)
45	    {
```

*GitHub* : [34..45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L34-L45)


---

	 - contracts/L1/hooks/AssignmentHook.sol

```solidity
62	    function onBlockProposed(
63	        TaikoData.Block memory _blk,
64	        TaikoData.BlockMetadata memory _meta,
65	        bytes memory _data
66	    )
67	        external
68	        payable
69	        nonReentrant
70	        onlyFromNamed("taiko")
71	    {
```

*GitHub* : [62..71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L62-L71)


---

	 - contracts/L1/libs/LibDepositing.sol

```solidity
29	    function depositEtherToL2(
30	        TaikoData.State storage _state,
31	        TaikoData.Config memory _config,
32	        IAddressResolver _resolver,
33	        address _recipient
34	    )
35	        internal
36	    {
```

*GitHub* : [29..36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L29-L36)


---

	 - contracts/L1/libs/LibProposing.sol

```solidity
68	    function proposeBlock(
69	        TaikoData.State storage _state,
70	        TaikoData.Config memory _config,
71	        IAddressResolver _resolver,
72	        bytes calldata _data,
73	        bytes calldata _txList
74	    )
75	        internal
76	        returns (TaikoData.BlockMetadata memory meta_, TaikoData.EthDeposit[] memory deposits_)
77	    {
```

*GitHub* : [68..77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L68-L77)


---

	 - contracts/L1/libs/LibProving.sol

```solidity
91	    function proveBlock(
92	        TaikoData.State storage _state,
93	        TaikoData.Config memory _config,
94	        IAddressResolver _resolver,
95	        TaikoData.BlockMetadata memory _meta,
96	        TaikoData.Transition memory _tran,
97	        TaikoData.TierProof memory _proof
98	    )
99	        internal
100	        returns (uint8 maxBlocksToVerify_)
101	    {
...
401	    function _checkProverPermission(
402	        TaikoData.State storage _state,
403	        TaikoData.Block storage _blk,
404	        TaikoData.TransitionState storage _ts,
405	        uint32 _tid,
406	        ITierProvider.Tier memory _tier
407	    )
408	        private
409	        view
410	    {
```

*GitHub* : [91..101](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L91-L101), [401..410](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L401-L410)


---

	 - contracts/L1/libs/LibVerifying.sol

```solidity
85	    function verifyBlocks(
86	        TaikoData.State storage _state,
87	        TaikoData.Config memory _config,
88	        IAddressResolver _resolver,
89	        uint64 _maxBlocksToVerify
90	    )
91	        internal
92	    {
```

*GitHub* : [85..92](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L85-L92), [224..231](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L224-L231)


---

	 - contracts/L1/provers/Guardians.sol


*GitHub* : [128](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L128)


---

	 - contracts/L1/TaikoL1.sol


*GitHub* : [75..83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L75-L83)


---

	 - contracts/L2/CrossChainOwned.sol


*GitHub* : [36..41](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L36-L41)


---

	 - contracts/L2/TaikoL2.sol


*GitHub* : [107..115](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L107-L115)


---

	 - contracts/signal/SignalService.sol


*GitHub* : [83..93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L83-L93), [137..147](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L137-L147), [158..166](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L158-L166), [271..280](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L271-L280)


---

	 - contracts/bridge/Bridge.sol


*GitHub* : [82..88](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L82-L88), [115..122](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L115-L122), [155..163](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L155-L163), [217..225](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L217-L225), [555](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L555), [577..586](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L577-L586)


---

	 - contracts/tokenvault/BaseVault.sol


*GitHub* : [47..52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L47-L52)


---

	 - contracts/tokenvault/ERC1155Vault.sol


*GitHub* : [39..46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L39-L46), [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L93), [127..136](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L127-L136), [240..246](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L240-L246), [303](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L303)


---

	 - contracts/tokenvault/ERC20Vault.sol


*GitHub* : [207..213](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L207-L213), [253..258](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L253-L258), [285..294](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L285-L294), [348..356](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L348-L356), [407](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L407)


---

	 - contracts/tokenvault/ERC721Vault.sol


*GitHub* : [26..33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L26-L33), [77..82](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L77-L82), [110..119](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L110-L119), [240](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L240)


---

	 - contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol


*GitHub* : [25..34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L25-L34)


---

	 - contracts/thirdparty/optimism/Bytes.sol


*GitHub* : [15..23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L15-L23), [102](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L102)


---

	 - contracts/thirdparty/optimism/rlp/RLPReader.sol


*GitHub* : [35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L35), [53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L53), [109](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L109), [144..148](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L144-L148)


---

	 - contracts/thirdparty/optimism/trie/MerkleTrie.sol


*GitHub* : [68..76](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L68-L76), [235..242](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L235-L242)


---

	 - contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol


*GitHub* : [19..28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L19-L28), [38..46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L38-L46)


---

	 - contracts/verifiers/SgxVerifier.sol


*GitHub* : [118..121](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L118-L121), [139..146](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L139-L146), [171..180](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L171-L180)


---

	 - contracts/team/airdrop/ERC20Airdrop.sol


*GitHub* : [50..58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L50-L58)


---

	 - contracts/team/airdrop/ERC20Airdrop2.sol


*GitHub* : [104..108](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L104-L108)


---

	 - contracts/team/TimelockTokenPool.sol


*GitHub* : [150](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L150), [168](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L168), [176..186](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L176-L186)


---

	 - contracts/automata-attestation/AutomataDcapV3Attestation.sol


*GitHub* : [138](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L138), [162](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L162), [175..179](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L175-L179), [206..213](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L206-L213), [248..252](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L248-L252), [303..312](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L303-L312), [364..368](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L364-L368)


---

	 - contracts/automata-attestation/lib/PEMCertChainLib.sol


*GitHub* : [40..47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L40-L47), [74..81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L74-L81), [216..220](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L216-L220), [252..259](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L252-L259), [269..283](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L269-L283), [341..348](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L341-L348)


---

	 - contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol


*GitHub* : [21..28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L21-L28), [62..72](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L62-L72), [152](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L152), [203..210](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L203-L210), [244..248](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L244-L248), [267..274](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L267-L274)


---

	 - contracts/automata-attestation/utils/Asn1Decode.sol


*GitHub* : [179](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L179)


---

	 - contracts/automata-attestation/utils/BytesUtils.sol


*GitHub* : [56..67](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L56-L67), [284..292](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L284-L292)


---

	 - contracts/automata-attestation/utils/RsaVerify.sol


*GitHub* : [43..52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L43-L52), [212..221](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L212-L221)


---

	 - contracts/automata-attestation/utils/SigVerifyLib.sol


*GitHub* : [79..87](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L79-L87), [96..104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L96-L104), [113..121](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L113-L121)

### [G-15]<a name="g-15"></a> State Variables can be packed into fewer storage slots

Each slot saved can avoid an extra Gsset (21000 gas). Subsequent reads as well as writes have smaller gas savings

*There are 3 instance(s) of this issue:*


---

	 - contracts/common/EssentialContract.sol

```solidity
10	abstract contract EssentialContract is UUPSUpgradeable, Ownable2StepUpgradeable, AddressResolver {
11	    uint8 private constant _FALSE = 1;
```

*GitHub* : [10..11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L10-L11)


---

	 - contracts/team/airdrop/ERC20Airdrop2.sol

```solidity
12	contract ERC20Airdrop2 is MerkleClaimable {
13	    using LibMath for uint256;
```

*GitHub* : [12..13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L12-L13)


---

	 - contracts/automata-attestation/AutomataDcapV3Attestation.sol

```solidity
22	contract AutomataDcapV3Attestation is IAttestation {
23	    using BytesUtils for bytes;
```

*GitHub* : [22..23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L22-L23)

### [G-16]<a name="g-16"></a> State variables access within a loop

State variable reads and writes are more expensive than local variable reads and writes. Therefore, it is recommended to replace state variable reads and writes within loops with a local variable. Gas savings should be multiplied by the average loop length.

*There are 17 instance(s) of this issue:*


---

	 - contracts/L1/provers/Guardians.sol

```solidity
74	        for (uint256 i; i < guardians.length; ++i) {
75	            delete guardianIds[guardians[i]];
76	        }
...
80	        for (uint256 i = 0; i < _newGuardians.length; ++i) {
81	            address guardian = _newGuardians[i];
82	            if (guardian == address(0)) revert INVALID_GUARDIAN();
83	            // This makes sure there are not duplicate addresses
84	            if (guardianIds[guardian] != 0) revert INVALID_GUARDIAN_SET();
85	
86	            // Save and index the guardian
87	            guardians.push(guardian);
88	            guardianIds[guardian] = guardians.length;
89	        }
...
133	            for (uint256 i; i < guardiansLength; ++i) {
134	                if (bits & 1 == 1) ++count;
135	                if (count == minGuardians) return true;
136	                bits >>= 1;
137	            }
```

*GitHub* : [74..76](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L74-L76), [80..89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L80-L89), [133..137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L133-L137)


---

	 - contracts/signal/SignalService.sol

```solidity
104	        for (uint256 i; i < hopProofs.length; ++i) {
105	            hop = hopProofs[i];
106	
107	            bytes32 signalRoot = _verifyHopProof(chainId, app, signal, value, hop, signalService);
108	            bool isLastHop = i == hopProofs.length - 1;
109	
110	            if (isLastHop) {
111	                if (hop.chainId != block.chainid) revert SS_INVALID_LAST_HOP_CHAINID();
112	                signalService = address(this);
113	            } else {
114	                if (hop.chainId == 0 || hop.chainId == block.chainid) {
115	                    revert SS_INVALID_MID_HOP_CHAINID();
116	                }
117	                signalService = resolve(hop.chainId, "signal_service", false);
118	            }
119	
120	            bool isFullProof = hop.accountProof.length > 0;
121	
122	            _cacheChainData(hop, chainId, hop.blockId, signalRoot, isFullProof, isLastHop);
123	
124	            bytes32 kind = isFullProof ? LibSignals.STATE_ROOT : LibSignals.SIGNAL_ROOT;
125	            signal = signalForChainData(chainId, kind, hop.blockId);
126	            value = hop.rootHash;
127	            chainId = hop.chainId;
128	            app = signalService;
129	        }
```

*GitHub* : [104..129](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L104-L129)


---

	 - contracts/bridge/Bridge.sol

```solidity
90	        for (uint256 i; i < _msgHashes.length; ++i) {
91	            bytes32 msgHash = _msgHashes[i];
92	            proofReceipt[msgHash].receivedAt = _timestamp;
93	            emit MessageSuspended(msgHash, _suspend);
94	        }
```

*GitHub* : [90..94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L90-L94)


---

	 - contracts/thirdparty/optimism/trie/MerkleTrie.sol

```solidity
85	        for (uint256 i = 0; i < proof.length; i++) {
86	            TrieNode memory currentNode = proof[i];
87	
88	            // Key index should never exceed total key length or we'll be out of bounds.
89	            require(currentKeyIndex <= key.length, "MerkleTrie: key index exceeds total key length");
90	
91	            if (currentKeyIndex == 0) {
92	                // First proof element is always the root node.
93	                require(
94	                    Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
95	                    "MerkleTrie: invalid root hash"
96	                );
97	            } else if (currentNode.encoded.length >= 32) {
98	                // Nodes 32 bytes or larger are hashed inside branch nodes.
99	                require(
100	                    Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
101	                    "MerkleTrie: invalid large internal hash"
102	                );
103	            } else {
104	                // Nodes smaller than 32 bytes aren't hashed.
105	                require(
106	                    Bytes.equal(currentNode.encoded, currentNodeID),
107	                    "MerkleTrie: invalid internal node hash"
108	                );
109	            }
110	
111	            if (currentNode.decoded.length == BRANCH_NODE_LENGTH) {
112	                if (currentKeyIndex == key.length) {
113	                    // Value is the last element of the decoded list (for branch nodes). There's
114	                    // some ambiguity in the Merkle trie specification because bytes(0) is a
115	                    // valid value to place into the trie, but for branch nodes bytes(0) can exist
116	                    // even when the value wasn't explicitly placed there. Geth treats a value of
117	                    // bytes(0) as "key does not exist" and so we do the same.
118	                    value_ = RLPReader.readBytes(currentNode.decoded[TREE_RADIX]);
119	                    require(
120	                        value_.length > 0,
121	                        "MerkleTrie: value length must be greater than zero (branch)"
122	                    );
123	
124	                    // Extra proof elements are not allowed.
125	                    require(
126	                        i == proof.length - 1,
127	                        "MerkleTrie: value node must be last node in proof (branch)"
128	                    );
129	
130	                    return value_;
131	                } else {
132	                    // We're not at the end of the key yet.
133	                    // Figure out what the next node ID should be and continue.
134	                    uint8 branchKey = uint8(key[currentKeyIndex]);
135	                    RLPReader.RLPItem memory nextNode = currentNode.decoded[branchKey];
136	                    currentNodeID = _getNodeID(nextNode);
137	                    currentKeyIndex += 1;
138	                }
139	            } else if (currentNode.decoded.length == LEAF_OR_EXTENSION_NODE_LENGTH) {
140	                bytes memory path = _getNodePath(currentNode);
141	                uint8 prefix = uint8(path[0]);
142	                uint8 offset = 2 - (prefix % 2);
143	                bytes memory pathRemainder = Bytes.slice(path, offset);
144	                bytes memory keyRemainder = Bytes.slice(key, currentKeyIndex);
145	                uint256 sharedNibbleLength = _getSharedNibbleLength(pathRemainder, keyRemainder);
146	
147	                // Whether this is a leaf node or an extension node, the path remainder MUST be a
148	                // prefix of the key remainder (or be equal to the key remainder) or the proof is
149	                // considered invalid.
150	                require(
151	                    pathRemainder.length == sharedNibbleLength,
152	                    "MerkleTrie: path remainder must share all nibbles with key"
153	                );
154	
155	                if (prefix == PREFIX_LEAF_EVEN || prefix == PREFIX_LEAF_ODD) {
156	                    // Prefix of 2 or 3 means this is a leaf node. For the leaf node to be valid,
157	                    // the key remainder must be exactly equal to the path remainder. We already
158	                    // did the necessary byte comparison, so it's more efficient here to check that
159	                    // the key remainder length equals the shared nibble length, which implies
160	                    // equality with the path remainder (since we already did the same check with
161	                    // the path remainder and the shared nibble length).
162	                    require(
163	                        keyRemainder.length == sharedNibbleLength,
164	                        "MerkleTrie: key remainder must be identical to path remainder"
165	                    );
166	
167	                    // Our Merkle Trie is designed specifically for the purposes of the Ethereum
168	                    // state trie. Empty values are not allowed in the state trie, so we can safely
169	                    // say that if the value is empty, the key should not exist and the proof is
170	                    // invalid.
171	                    value_ = RLPReader.readBytes(currentNode.decoded[1]);
172	                    require(
173	                        value_.length > 0,
174	                        "MerkleTrie: value length must be greater than zero (leaf)"
175	                    );
176	
177	                    // Extra proof elements are not allowed.
178	                    require(
179	                        i == proof.length - 1,
180	                        "MerkleTrie: value node must be last node in proof (leaf)"
181	                    );
182	
183	                    return value_;
184	                } else if (prefix == PREFIX_EXTENSION_EVEN || prefix == PREFIX_EXTENSION_ODD) {
185	                    // Prefix of 0 or 1 means this is an extension node. We move onto the next node
186	                    // in the proof and increment the key index by the length of the path remainder
187	                    // which is equal to the shared nibble length.
188	                    currentNodeID = _getNodeID(currentNode.decoded[1]);
189	                    currentKeyIndex += sharedNibbleLength;
190	                } else {
191	                    revert("MerkleTrie: received a node with an unknown prefix");
192	                }
193	            } else {
194	                revert("MerkleTrie: received an unparseable node");
195	            }
196	        }
```

*GitHub* : [85..196](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85-L196)


---

	 - contracts/verifiers/SgxVerifier.sol

```solidity
104	        for (uint256 i; i < _ids.length; ++i) {
105	            uint256 idx = _ids[i];
106	
107	            if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();
108	
109	            emit InstanceDeleted(idx, instances[idx].addr);
110	
111	            delete instances[idx];
112	        }
...
210	        for (uint256 i; i < _instances.length; ++i) {
211	            if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();
212	
213	            addressRegistered[_instances[i]] = true;
214	
215	            if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();
216	
217	            instances[nextInstanceId] = Instance(_instances[i], validSince);
218	            ids[i] = nextInstanceId;
219	
220	            emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);
221	
222	            nextInstanceId++;
223	        }
```

*GitHub* : [104..112](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L104-L112), [210..223](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210-L223)


---

	 - contracts/team/airdrop/ERC721Airdrop.sol

```solidity
59	        for (uint256 i; i < tokenIds.length; ++i) {
60	            IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);
61	        }
```

*GitHub* : [59..61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59-L61)


---

	 - contracts/automata-attestation/AutomataDcapV3Attestation.sol

```solidity
80	        for (uint256 i; i < serialNumBatch.length; ++i) {
81	            if (_serialNumIsRevoked[index][serialNumBatch[i]]) {
82	                continue;
83	            }
84	            _serialNumIsRevoked[index][serialNumBatch[i]] = true;
85	        }
```

*GitHub* : [80..85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L80-L85), [95..100](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L95-L100), [259..298](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L259-L298), [420..430](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L420-L430)


---

	 - contracts/automata-attestation/lib/PEMCertChainLib.sol


*GitHub* : [286..338](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L286-L338), [301..328](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L301-L328), [354..372](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L354-L372)


---

	 - contracts/automata-attestation/utils/BytesUtils.sol


*GitHub* : [333..342](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L333-L342)

### [G-17]<a name="g-17"></a> State variables only set in the constructor should be declared `immutable`

Accessing state variables within a function involves an SLOAD operation, but `immutable` variables can be accessed directly without the need of it, thus reducing gas costs. As these state variables are assigned only in the constructor, consider declaring them `immutable`.

*There are 2 instance(s) of this issue:*


---

	 - contracts/automata-attestation/AutomataDcapV3Attestation.sol

```solidity
52	    address public owner;
```

*GitHub* : [52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L52)


---

	 - contracts/automata-attestation/utils/SigVerifyLib.sol

```solidity
18	    address private ES256VERIFIER;
```

*GitHub* : [18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L18)

### [G-18]<a name="g-18"></a> Newer versions of solidity are more gas efficient

The solidity language continues to pursue more efficient gas optimization schemes. Adopting a [newer version of solidity](https://github.com/ethereum/solc-js/tags) can be more gas efficient.

```md
3    solc_version = "0.8.24"
```

proof: 
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/foundry.toml#L3


*There are 81 instance(s) of this issue:*


---

	 - contracts/common/IAddressManager.sol

```solidity
2	pragma solidity 0.8.24;
```

*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressManager.sol#L2)


---

	 - contracts/common/AddressManager.sol

```solidity
2	pragma solidity 0.8.24;
```

*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L2)


---

	 - contracts/common/IAddressResolver.sol

```solidity
2	pragma solidity 0.8.24;
```

*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressResolver.sol#L2)


---

	 - contracts/common/AddressResolver.sol

```solidity
2	pragma solidity 0.8.24;
```

*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L2)


---

	 - contracts/common/EssentialContract.sol

```solidity
2	pragma solidity 0.8.24;
```

*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L2)


---

	 - contracts/libs/Lib4844.sol

```solidity
2	pragma solidity 0.8.24;
```

*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L2)


---

	 - contracts/libs/LibAddress.sol

```solidity
2	pragma solidity 0.8.24;
```

*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L2)


---

	 - contracts/libs/LibMath.sol

```solidity
2	pragma solidity 0.8.24;
```

*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibMath.sol#L2)


---

	 - contracts/libs/LibTrieProof.sol

```solidity
7	pragma solidity 0.8.24;
```

*GitHub* : [7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L7)


---

	 - contracts/L1/gov/TaikoGovernor.sol

```solidity
2	pragma solidity 0.8.24;
```

*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L2)


---

	 - contracts/L1/gov/TaikoTimelockController.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L2)


---

	 - contracts/L1/hooks/IHook.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/IHook.sol#L2)


---

	 - contracts/L1/hooks/AssignmentHook.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L2)


---

	 - contracts/L1/ITaikoL1.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/ITaikoL1.sol#L2)


---

	 - contracts/L1/libs/LibDepositing.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L2)


---

	 - contracts/L1/libs/LibProposing.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L2)


---

	 - contracts/L1/libs/LibProving.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L2)


---

	 - contracts/L1/libs/LibUtils.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L2)


---

	 - contracts/L1/libs/LibVerifying.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L2)


---

	 - contracts/L1/provers/GuardianProver.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L2)


---

	 - contracts/L1/provers/Guardians.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L2)


---

	 - contracts/L1/TaikoData.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L2)


---

	 - contracts/L1/TaikoErrors.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoErrors.sol#L2)


---

	 - contracts/L1/TaikoEvents.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L2)


---

	 - contracts/L1/TaikoL1.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L2)


---

	 - contracts/L1/TaikoToken.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L2)


---

	 - contracts/L1/tiers/ITierProvider.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L2)


---

	 - contracts/L1/tiers/DevnetTierProvider.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L2)


---

	 - contracts/L1/tiers/MainnetTierProvider.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L2)


---

	 - contracts/L1/tiers/TestnetTierProvider.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L2)


---

	 - contracts/L2/CrossChainOwned.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L2)


---

	 - contracts/L2/Lib1559Math.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L2)


---

	 - contracts/L2/TaikoL2.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L2)


---

	 - contracts/L2/TaikoL2EIP1559Configurable.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L2)


---

	 - contracts/signal/ISignalService.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L2)


---

	 - contracts/signal/LibSignals.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/LibSignals.sol#L2)


---

	 - contracts/signal/SignalService.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L2)


---

	 - contracts/bridge/IBridge.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L2)


---

	 - contracts/bridge/Bridge.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L2)


---

	 - contracts/tokenvault/adapters/USDCAdapter.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L2)


---

	 - contracts/tokenvault/BridgedERC20.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L2)


---

	 - contracts/tokenvault/BridgedERC20Base.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L2)


---

	 - contracts/tokenvault/BridgedERC721.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L2)


---

	 - contracts/tokenvault/BridgedERC1155.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L2)


---

	 - contracts/tokenvault/BaseNFTVault.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L2)


---

	 - contracts/tokenvault/BaseVault.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L2)


---

	 - contracts/tokenvault/ERC1155Vault.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L2)


---

	 - contracts/tokenvault/ERC20Vault.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L2)


---

	 - contracts/tokenvault/ERC721Vault.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L2)


---

	 - contracts/tokenvault/IBridgedERC20.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/IBridgedERC20.sol#L2)


---

	 - contracts/tokenvault/LibBridgedToken.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L2)


---

	 - contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol


*GitHub* : [3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L3)


---

	 - contracts/thirdparty/optimism/Bytes.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L2)


---

	 - contracts/thirdparty/optimism/rlp/RLPReader.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L2)


---

	 - contracts/thirdparty/optimism/rlp/RLPWriter.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L2)


---

	 - contracts/thirdparty/optimism/trie/MerkleTrie.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L2)


---

	 - contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L2)


---

	 - contracts/thirdparty/solmate/LibFixedPointMath.sol


*GitHub* : [4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L4)


---

	 - contracts/verifiers/IVerifier.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/IVerifier.sol#L2)


---

	 - contracts/verifiers/GuardianVerifier.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L2)


---

	 - contracts/verifiers/SgxVerifier.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L2)


---

	 - contracts/team/airdrop/ERC20Airdrop.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L2)


---

	 - contracts/team/airdrop/ERC20Airdrop2.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L2)


---

	 - contracts/team/airdrop/ERC721Airdrop.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L2)


---

	 - contracts/team/airdrop/MerkleClaimable.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L2)


---

	 - contracts/team/TimelockTokenPool.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L2)


---

	 - contracts/automata-attestation/AutomataDcapV3Attestation.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L2)


---

	 - contracts/automata-attestation/interfaces/IAttestation.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/interfaces/IAttestation.sol#L2)


---

	 - contracts/automata-attestation/interfaces/ISigVerifyLib.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L2)


---

	 - contracts/automata-attestation/lib/EnclaveIdStruct.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/EnclaveIdStruct.sol#L2)


---

	 - contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L2)


---

	 - contracts/automata-attestation/lib/PEMCertChainLib.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L2)


---

	 - contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L2)


---

	 - contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L2)


---

	 - contracts/automata-attestation/lib/TCBInfoStruct.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol#L2)


---

	 - contracts/automata-attestation/utils/Asn1Decode.sol


*GitHub* : [3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L3)


---

	 - contracts/automata-attestation/utils/BytesUtils.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L2)


---

	 - contracts/automata-attestation/utils/RsaVerify.sol


*GitHub* : [3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L3)


---

	 - contracts/automata-attestation/utils/SHA1.sol


*GitHub* : [3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SHA1.sol#L3)


---

	 - contracts/automata-attestation/utils/SigVerifyLib.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L2)


---

	 - contracts/automata-attestation/utils/X509DateUtils.sol


*GitHub* : [3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L3)

### [G-19]<a name="g-19"></a> Consider activating `via-ir` for deploying

The IR-based code generator was developed to make code generation more performant by enabling optimization passes that can be applied across functions.

It is possible to activate the IR-based code generator through the command line by using the flag `--via-ir` or by including the option `{"viaIR": true}`.

Keep in mind that compiling with this option may take longer. However, you can simply test it before deploying your code. If you find that it provides better performance, you can add the `--via-ir` flag to your deploy command.

*There are 1 instance(s) of this issue:*

*GitHub* : [project\2024-03-taiko\packages\protocol](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/#L0)

### [G-20]<a name="g-20"></a> Function calls should be cached instead of re-calling the function

Consider caching the result instead of re-calling the function when possible. Note: this also includes casts, which cost between 42-46 gas, depending on the type.

*There are 15 instance(s) of this issue:*


---

	 - contracts/L1/libs/LibProposing.sol

```solidity
68	    function proposeBlock(
69	        TaikoData.State storage _state,
70	        TaikoData.Config memory _config,
71	        IAddressResolver _resolver,
72	        bytes calldata _data,
73	        bytes calldata _txList
74	    )
75	        internal
76	        returns (TaikoData.BlockMetadata memory meta_, TaikoData.EthDeposit[] memory deposits_)
77	    {
```

*GitHub* : [68..77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L68-L77)


---

	 - contracts/bridge/Bridge.sol

```solidity
217	    function processMessage(
218	        Message calldata _message,
219	        bytes calldata _proof
220	    )
221	        external
222	        nonReentrant
223	        whenNotPaused
224	        sameChain(_message.destChainId)
225	    {
```

*GitHub* : [217..225](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L217-L225)


---

	 - contracts/tokenvault/ERC20Vault.sol

```solidity
348	    function _handleMessage(
349	        address _user,
350	        address _token,
351	        address _to,
352	        uint256 _amount
353	    )
354	        private
355	        returns (bytes memory msgData_, CanonicalERC20 memory ctoken_, uint256 balanceChange_)
356	    {
```

*GitHub* : [348..356](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L348-L356)


---

	 - contracts/thirdparty/optimism/trie/MerkleTrie.sol

```solidity
68	    function get(
69	        bytes memory _key,
70	        bytes[] memory _proof,
71	        bytes32 _root
72	    )
73	        internal
74	        pure
75	        returns (bytes memory value_)
76	    {
```

*GitHub* : [68..76](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L68-L76)


---

	 - contracts/automata-attestation/lib/PEMCertChainLib.sol

```solidity
74	    function decodeCert(
75	        bytes memory der,
76	        bool isPckCert
77	    )
78	        external
79	        pure
80	        returns (bool success, ECSha256Certificate memory cert)
81	    {
...
269	    function _findPckTcbInfo(
270	        bytes memory der,
271	        uint256 tbsPtr,
272	        uint256 tbsParentPtr
273	    )
274	        private
275	        pure
276	        returns (
277	            bool success,
278	            uint256 pcesvn,
279	            uint256[] memory cpusvns,
280	            bytes memory fmspcBytes,
281	            bytes memory pceidBytes
282	        )
283	    {
```

*GitHub* : [74..81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L74-L81), [269..283](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L269-L283)


---

	 - contracts/automata-attestation/utils/Asn1Decode.sol

```solidity
98	    function isChildOf(uint256 i, uint256 j) internal pure returns (bool) {
...
111	    function bytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes memory) {
...
121	    function allBytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes memory) {
...
131	    function bytes32At(bytes memory der, uint256 ptr) internal pure returns (bytes32) {
```

*GitHub* : [98](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L98), [111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L111), [121](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L121), [131](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L131), [141](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L141), [154](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L154), [165](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L165), [169](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L169), [179](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L179)

### [G-21]<a name="g-21"></a> Add `unchecked` blocks for divisions where the operands cannot overflow

`uint` divisions can't overflow, while `int` divisions can overflow only in [one specific case](https://docs.soliditylang.org/en/latest/types.html#division).

Consider adding an `unchecked` block to have some [gas savings](https://gist.github.com/DadeKuma/3bc597338ae774b8b3bd43280d55271f).

*There are 15 instance(s) of this issue:*


---

	 - contracts/L1/gov/TaikoGovernor.sol

```solidity
124	        return 1_000_000_000 ether / 10_000; // 0.01% of Taiko Token
```

*GitHub* : [124](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L124)


---

	 - contracts/L1/libs/LibVerifying.sol

```solidity
262	                || _config.ethDepositMaxFee > type(uint96).max / _config.ethDepositMaxCountPerBlock
```

*GitHub* : [262](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L262)


---

	 - contracts/L1/TaikoL1.sol

```solidity
215	            ethDepositMaxFee: 1 ether / 10,
```

*GitHub* : [215](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L215)


---

	 - contracts/L2/Lib1559Math.sol

```solidity
28	        return _ethQty(_gasExcess, _adjustmentFactor) / LibFixedPointMath.SCALING_FACTOR
29	            / _adjustmentFactor;
...
28	        return _ethQty(_gasExcess, _adjustmentFactor) / LibFixedPointMath.SCALING_FACTOR
...
41	        uint256 input = _gasExcess * LibFixedPointMath.SCALING_FACTOR / _adjustmentFactor;
```

*GitHub* : [28..29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L28-L29), [28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L28), [41](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L41)


---

	 - contracts/thirdparty/optimism/rlp/RLPWriter.sol

```solidity
39	            while (_len / i != 0) {
...
47	                out_[i] = bytes1(uint8((_len / (256 ** (lenLen - i))) % 256));
```

*GitHub* : [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L39), [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L47)


---

	 - contracts/thirdparty/solmate/LibFixedPointMath.sol

```solidity
33	            x = (x << 78) / 5 ** 18;
...
39	            int256 k = ((x << 96) / 54_916_777_467_707_473_351_141_471_128 + 2 ** 95) >> 96;
```

*GitHub* : [33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L33), [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L39)


---

	 - contracts/team/airdrop/ERC20Airdrop2.sol


*GitHub* : [117..118](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L117-L118)


---

	 - contracts/team/TimelockTokenPool.sol


*GitHub* : [197](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L197), [264](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L264)


---

	 - contracts/automata-attestation/lib/PEMCertChainLib.sol


*GitHub* : [359](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L359)


---

	 - contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol


*GitHub* : [155](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L155)

### [G-22]<a name="g-22"></a> Multiplication/division by two should use bit shifting

`X * 2` is equivalent to `X << 1` and `X / 2` is the same as `X >> 1`.

The `MUL` and `DIV` opcodes cost 5 gas, whereas `SHL` and `SHR` only cost 3 gas.

*There are 10 instance(s) of this issue:*


---

	 - contracts/L1/libs/LibProposing.sol

```solidity
21	    uint256 public constant MAX_BYTES_PER_BLOB = 4096 * 32;
```

*GitHub* : [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L21)


---

	 - contracts/L1/libs/LibVerifying.sol

```solidity
251	                || _config.blockMaxTxListBytes > 128 * 1024 // calldata up to 128K
```

*GitHub* : [251](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L251)


---

	 - contracts/L2/TaikoL2.sol

```solidity
213	        config_.gasTargetPerL1Block = 15 * 1e6 * 4;
```

*GitHub* : [213](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L213)


---

	 - contracts/automata-attestation/lib/PEMCertChainLib.sol

```solidity
359	                ? uint16(bytes2(svnValueBytes)) / 256
```

*GitHub* : [359](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L359)


---

	 - contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

```solidity
155	            uint256 upperDigit = digits / 16;
...
158	            uint256 acc = lowerDigit * (16 ** (2 * i));
...
159	            acc += upperDigit * (16 ** ((2 * i) + 1));
```

*GitHub* : [155](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L155), [158](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L158), [159](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L159)


---

	 - contracts/automata-attestation/utils/Asn1Decode.sol

```solidity
145	        return uint256(der.readBytesN(ptr.ixf(), len) >> (32 - len) * 8);
...
203	                    der.readBytesN(ix + 2, lengthbytesLength) >> (32 - lengthbytesLength) * 8
```

*GitHub* : [145](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L145), [203](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L203)


---

	 - contracts/automata-attestation/utils/BytesUtils.sol

```solidity
93	                    mask = ~(2 ** (8 * (32 - shortest + idx)) - 1);
```

*GitHub* : [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L93)

### [G-23]<a name="g-23"></a> Consider pre-calculating the address of `address(this)`

It can be more gas-efficient to use a hardcoded address instead of the `address(this)` expression, especially if you need to use the same address multiple times in your contract.

The reason for this, is that using `address(this)` requires an additional `EXTCODESIZE` operation to retrieve the contract’s address from its bytecode, which can increase the gas cost of your contract. By pre-calculating and using a hardcoded address, you can avoid this additional operation and reduce the overall gas cost of your contract.

Save 100 - 2600 Gas

*There are 40 instance(s) of this issue:*


---

	 - contracts/L1/hooks/AssignmentHook.sol

```solidity
125	        if (address(this).balance > 0) {
...
126	            taikoL1Address.sendEther(address(this).balance);
...
151	                address(this),
```

*GitHub* : [125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L125), [126](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L126), [151](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L151)


---

	 - contracts/L1/libs/LibProposing.sol

```solidity
238	            uint256 tkoBalance = tko.balanceOf(address(this));
...
253	                IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }(
...
260	            if (address(this).balance != 0) {
...
261	                msg.sender.sendEther(address(this).balance);
...
268	            if (tko.balanceOf(address(this)) != tkoBalance + _config.livenessBond) {
```

*GitHub* : [238](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L238), [253](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L253), [260](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L260), [261](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L261), [268](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L268)


---

	 - contracts/L1/libs/LibProving.sol

```solidity
242	                tko.transferFrom(msg.sender, address(this), tier.contestBond);
...
384	                _tko.transferFrom(msg.sender, address(this), _tier.validityBond - reward);
```

*GitHub* : [242](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L242), [384](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L384)


---

	 - contracts/L1/TaikoToken.sol


*GitHub* : [61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L61), [79](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L79)


---

	 - contracts/L2/CrossChainOwned.sol


*GitHub* : [50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L50)


---

	 - contracts/L2/TaikoL2.sol


*GitHub* : [176](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L176), [174](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L174)


---

	 - contracts/signal/SignalService.sol


*GitHub* : [112](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L112), [131](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L131), [149](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L149), [171](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L171), [245](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L245)


---

	 - contracts/bridge/Bridge.sol


*GitHub* : [174](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L174), [196](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L196), [270](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L270), [343](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L343), [486](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L486)


---

	 - contracts/tokenvault/adapters/USDCAdapter.sol


*GitHub* : [48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L48)


---

	 - contracts/tokenvault/BridgedERC20.sol


*GitHub* : [147](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L147)


---

	 - contracts/tokenvault/BridgedERC721.sol


*GitHub* : [125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L125)


---

	 - contracts/tokenvault/BridgedERC1155.sol


*GitHub* : [137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L137)


---

	 - contracts/tokenvault/ERC1155Vault.sol


*GitHub* : [108](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L108), [226](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L226), [272](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L272)


---

	 - contracts/tokenvault/ERC20Vault.sol


*GitHub* : [267](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L267), [378](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L378), [379](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L379), [380](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L380)


---

	 - contracts/tokenvault/ERC721Vault.sol


*GitHub* : [91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L91), [171](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L171), [211](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L211)


---

	 - contracts/verifiers/SgxVerifier.sol


*GitHub* : [186](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L186)

### [G-24]<a name="g-24"></a> Consider using `bytes32` rather than a `string`

Using the `bytes` types for fixed-length strings is more efficient than having the EVM have to incur the overhead of string processing. Consider whether the value _needs_ to be a `string`. A good reason to keep it as a `string` would be if the variable is defined in an interface that this project does not own.

*There are 59 instance(s) of this issue:*


---

	 - contracts/L1/gov/TaikoGovernor.sol

```solidity
52	        string memory _description
...
72	        string[] memory _signatures,
...
74	        string memory _description
```

*GitHub* : [52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L52), [72](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L72), [74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L74)


---

	 - contracts/L1/TaikoToken.sol

```solidity
27	        string calldata _name,
...
28	        string calldata _symbol,
```

*GitHub* : [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L27), [28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L28)


---

	 - contracts/bridge/IBridge.sol

```solidity
45	        string memo;
```

*GitHub* : [45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L45)


---

	 - contracts/tokenvault/BridgedERC20.sol

```solidity
58	        string memory _symbol,
...
59	        string memory _name
...
95	        returns (string memory)
...
106	        returns (string memory)
```

*GitHub* : [58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L58), [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L59), [95](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L95), [106](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L106)


---

	 - contracts/tokenvault/BridgedERC721.sol


*GitHub* : [36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L36), [37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L37), [87](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L87), [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L93), [107](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L107)


---

	 - contracts/tokenvault/BridgedERC1155.sol


*GitHub* : [22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L22), [25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L25), [43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L43), [44](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L44), [115](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L115), [121](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L121)


---

	 - contracts/tokenvault/BaseNFTVault.sol


*GitHub* : [17](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L17), [19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L19), [43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L43), [73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L73), [74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L74)


---

	 - contracts/tokenvault/ERC1155Vault.sol


*GitHub* : [18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L18), [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L21), [263](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L263), [266](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L266)


---

	 - contracts/tokenvault/ERC20Vault.sol


*GitHub* : [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L27), [28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L28), [41](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L41), [67](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L67), [68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L68), [85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L85), [86](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L86)


---

	 - contracts/tokenvault/LibBridgedToken.sol


*GitHub* : [14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L14), [15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L15), [29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L29), [34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L34), [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L39), [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L39), [49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L49)


---

	 - contracts/automata-attestation/AutomataDcapV3Attestation.sol


*GitHub* : [49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L49), [104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L104), [435](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L435)


---

	 - contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol


*GitHub* : [19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L19), [20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L20), [25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L25), [26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L26)


---

	 - contracts/automata-attestation/lib/PEMCertChainLib.sol


*GitHub* : [49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L49), [55](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L55), [240](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L240), [241](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L241), [242](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L242), [216](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L216)


---

	 - contracts/automata-attestation/lib/TCBInfoStruct.sol


*GitHub* : [8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol#L8), [9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol#L9)

### [G-25]<a name="g-25"></a> Optimize Zero Checks Using Assembly

The usage of inline assembly to check if variable is the zero can save gas compared to traditional `require` or `if` statement checks. 

The assembly check uses the `extcodesize` operation which is generally cheaper in terms of gas.

[More information can be found here.](https://medium.com/@kalexotsu/solidity-assembly-checking-if-an-address-is-0-efficiently-d2bfe071331)

*There are 176 instance(s) of this issue:*


---

	 - contracts/common/AddressResolver.sol

```solidity
81	        if (addressManager == address(0)) revert RESOLVER_INVALID_MANAGER();
...
85	        if (!_allowZeroAddress && addr_ == address(0)) {
```

*GitHub* : [81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L81), [85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L85)


---

	 - contracts/common/EssentialContract.sol

```solidity
105	        if (_addressManager == address(0)) revert ZERO_ADDR_MANAGER();
...
110	        _transferOwnership(_owner == address(0) ? msg.sender : _owner);
```

*GitHub* : [105](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L105), [110](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L110)


---

	 - contracts/libs/LibAddress.sol

```solidity
24	        if (_to == address(0)) revert ETH_TRANSFER_FAILED();
```

*GitHub* : [24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L24)


---

	 - contracts/libs/LibTrieProof.sol

```solidity
46	        if (_accountProof.length != 0) {
...
50	            if (rlpAccount.length == 0) revert LTP_INVALID_ACCOUNT_PROOF();
```

*GitHub* : [46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L46), [50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L50)


---

	 - contracts/L1/hooks/AssignmentHook.sol

```solidity
83	                || assignment.metaHash != 0 && _blk.metaHash != assignment.metaHash
...
84	                || assignment.parentMetaHash != 0 && _meta.parentMetaHash != assignment.parentMetaHash
...
85	                || assignment.maxBlockId != 0 && _meta.id > assignment.maxBlockId
```

*GitHub* : [83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L83), [84](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L84), [85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L85), [86](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L86), [109](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L109), [120](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L120), [120](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L120), [125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L125)


---

	 - contracts/L1/libs/LibDepositing.sol


*GitHub* : [44](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L44)


---

	 - contracts/L1/libs/LibProposing.sol


*GitHub* : [81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L81), [85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L85), [108](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L108), [135](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L135), [185](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L185), [144](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L144), [159](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L159), [195](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L195), [260](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L260), [310](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L310), [316](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L316)


---

	 - contracts/L1/libs/LibProving.sol


*GitHub* : [105](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L105), [105](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L105), [105](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L105), [134](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L134), [163](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L163), [164](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L164), [186](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L186), [192](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L192), [239](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L239), [223](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L223), [224](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L224), [224](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L224), [224](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L224), [280](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L280), [363](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L363), [412](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L412), [419](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L419)


---

	 - contracts/L1/libs/LibUtils.sol


*GitHub* : [43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L43)


---

	 - contracts/L1/libs/LibVerifying.sol


*GitHub* : [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L93), [111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L111), [137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L137), [145](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L145), [148](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L148), [212](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L212), [250](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L250), [250](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L250), [252](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L252), [253](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L253), [258](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L258), [260](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L260), [261](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L261)


---

	 - contracts/L1/provers/Guardians.sol


*GitHub* : [82](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L82), [84](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L84), [113](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L113)


---

	 - contracts/L1/TaikoL1.sol


*GitHub* : [153](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L153)


---

	 - contracts/L1/tiers/MainnetTierProvider.sol


*GitHub* : [68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L68)


---

	 - contracts/L1/tiers/TestnetTierProvider.sol


*GitHub* : [68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L68)


---

	 - contracts/L2/CrossChainOwned.sol


*GitHub* : [70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L70)


---

	 - contracts/L2/Lib1559Math.sol


*GitHub* : [24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L24)


---

	 - contracts/L2/TaikoL2.sol


*GitHub* : [86](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L86), [117](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L117), [117](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L117), [117](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L117), [118](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L118), [172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L172), [173](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L173), [262](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L262), [275](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L275), [279](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L279), [296](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L296)


---

	 - contracts/L2/TaikoL2EIP1559Configurable.sol


*GitHub* : [33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L33), [34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L34)


---

	 - contracts/signal/SignalService.sol


*GitHub* : [36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L36), [41](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L41), [95](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L95), [114](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L114), [120](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L120), [131](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L131), [154](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L154), [167](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L167), [169](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L169), [172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L172)


---

	 - contracts/bridge/Bridge.sol


*GitHub* : [124](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L124), [124](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L124), [169](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L169), [231](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L231), [242](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L242), [245](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L245), [250](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L250), [260](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L260), [270](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L270), [291](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L291), [321](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L321), [398](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L398), [405](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L405), [485](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L485)


---

	 - contracts/tokenvault/BridgedERC20Base.sol


*GitHub* : [102](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L102)


---

	 - contracts/tokenvault/BaseNFTVault.sol


*GitHub* : [149](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L149)


---

	 - contracts/tokenvault/ERC1155Vault.sol


*GitHub* : [48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L48), [64](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L64), [108](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L108), [249](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L249), [293](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L293)


---

	 - contracts/tokenvault/ERC20Vault.sol


*GitHub* : [158](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L158), [158](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L158), [170](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L170), [214](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L214), [215](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L215), [227](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L227), [267](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L267), [358](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L358), [397](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L397)


---

	 - contracts/tokenvault/ERC721Vault.sol


*GitHub* : [35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L35), [50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L50), [91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L91), [195](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L195), [230](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L230)


---

	 - contracts/tokenvault/LibBridgedToken.sol


*GitHub* : [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L21), [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L21), [22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L22), [22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L22)


---

	 - contracts/thirdparty/optimism/rlp/RLPReader.sol


*GitHub* : [38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L38), [153](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L153), [287](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L287)


---

	 - contracts/thirdparty/optimism/rlp/RLPWriter.sol


*GitHub* : [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L39), [60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L60)


---

	 - contracts/thirdparty/optimism/trie/MerkleTrie.sol


*GitHub* : [77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L77), [91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L91), [173](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L173), [120](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L120)


---

	 - contracts/verifiers/SgxVerifier.sol


*GitHub* : [107](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L107), [124](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L124), [215](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L215), [234](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L234)


---

	 - contracts/team/airdrop/ERC20Airdrop2.sol


*GitHub* : [111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L111)


---

	 - contracts/team/airdrop/MerkleClaimable.sol


*GitHub* : [35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L35), [35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L35)


---

	 - contracts/team/TimelockTokenPool.sol


*GitHub* : [121](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L121), [124](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L124), [127](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L127), [136](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L136), [137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L137), [154](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L154), [169](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L169), [255](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L255), [256](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L256), [259](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L259), [268](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L268), [274](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L274), [274](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L274), [277](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L277), [275](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L275)


---

	 - contracts/automata-attestation/AutomataDcapV3Attestation.sol


*GitHub* : [421](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L421)


---

	 - contracts/automata-attestation/lib/PEMCertChainLib.sol


*GitHub* : [56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L56), [286](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L286)


---

	 - contracts/automata-attestation/utils/Asn1Decode.sol


*GitHub* : [143](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L143), [156](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L156), [158](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L158), [191](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L191)


---

	 - contracts/automata-attestation/utils/BytesUtils.sol


*GitHub* : [96](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L96), [345](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L345)


---

	 - contracts/automata-attestation/utils/RsaVerify.sol


*GitHub* : [137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L137), [145](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L145), [270](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L270), [278](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L278)


---

	 - contracts/automata-attestation/utils/X509DateUtils.sol


*GitHub* : [24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L24), [72](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L72), [73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L73), [74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L74)

### [G-26]<a name="g-26"></a> Consider using `assembly` to write address storage values if the address variable is mutable

Writing address storage values using `assembly` can be more gas efficient when the address variable is mutable.
The following instances show mutable address storage variables that could be optimized using `assembly`.

*There are 49 instance(s) of this issue:*


---

	 - contracts/common/AddressResolver.sol

```solidity
62	        addressManager = _addressManager;
```

*GitHub* : [62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L62)


---

	 - contracts/L1/libs/LibProposing.sol

```solidity
86	            params.coinbase = msg.sender;
...
257	                prevHook = params.hookCalls[i].hook;
```

*GitHub* : [86](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L86), [257](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L257)


---

	 - contracts/L1/libs/LibProving.sol

```solidity
251	                ts.contester = msg.sender;
...
226	                ts.prover = msg.sender;
...
303	            ts_.contester = address(0);
...
332	                ts_.prover = address(0);
...
327	                ts_.prover = _blk.assignedProver;
...
390	        _ts.contester = address(0);
...
391	        _ts.prover = msg.sender;
```

*GitHub* : [251](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L251), [226](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L226), [303](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L303), [332](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L332), [327](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L327), [390](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L390), [391](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L391)


---

	 - contracts/L1/libs/LibVerifying.sol


*GitHub* : [70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L70), [149](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L149)


---

	 - contracts/signal/SignalService.sol


*GitHub* : [117](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L117), [112](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L112), [128](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L128)


---

	 - contracts/bridge/Bridge.sol


*GitHub* : [145](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L145), [397](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L397)


---

	 - contracts/tokenvault/BridgedERC20.sol


*GitHub* : [73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L73), [81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L81)


---

	 - contracts/tokenvault/BridgedERC20Base.sol


*GitHub* : [49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L49)


---

	 - contracts/tokenvault/BridgedERC721.sol


*GitHub* : [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L47)


---

	 - contracts/tokenvault/BridgedERC1155.sol


*GitHub* : [56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L56)


---

	 - contracts/tokenvault/ERC1155Vault.sol


*GitHub* : [229](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L229), [225](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L225), [292](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L292), [294](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L294), [309](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L309)


---

	 - contracts/tokenvault/ERC20Vault.sol


*GitHub* : [168](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L168), [332](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L332), [329](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L329), [395](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L395), [398](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L398), [421](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L421)


---

	 - contracts/tokenvault/ERC721Vault.sol


*GitHub* : [174](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L174), [169](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L169), [228](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L228), [231](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L231), [246](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L246)


---

	 - contracts/team/airdrop/ERC20Airdrop.sol


*GitHub* : [41](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L41), [42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L42)


---

	 - contracts/team/airdrop/ERC20Airdrop2.sol


*GitHub* : [69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L69), [70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L70)


---

	 - contracts/team/airdrop/ERC721Airdrop.sol


*GitHub* : [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L39), [40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L40)


---

	 - contracts/team/TimelockTokenPool.sol


*GitHub* : [122](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L122), [125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L125), [128](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L128)


---

	 - contracts/automata-attestation/AutomataDcapV3Attestation.sol


*GitHub* : [57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L57)


---

	 - contracts/automata-attestation/utils/SigVerifyLib.sol


*GitHub* : [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L21)

### [G-27]<a name="g-27"></a> Consider Caching Multiple Accesses to Mappings/Arrays

Leveraging a local variable to cache these values when accessed more than once can yield a gas saving of approximately 42 units per access. This reduction is attributed to eliminating the need for recalculating the key's keccak256 hash (which costs Gkeccak256 - 30 gas) and the associated stack operations. For arrays, this also prevents the overhead of re-computing offsets in memory or calldata.

*There are 34 instance(s) of this issue:*


---

	 - contracts/common/AddressManager.sol

```solidity
38	    function setAddress(
39	        uint64 _chainId,
40	        bytes32 _name,
41	        address _newAddress
42	    )
43	        external
44	        virtual
45	        onlyOwner
46	    {
```

*GitHub* : [38..46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L38-L46)


---

	 - contracts/L1/gov/TaikoTimelockController.sol

```solidity
15	    function init(address _owner, uint256 _minDelay) external initializer {
```

*GitHub* : [15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L15)


---

	 - contracts/L1/libs/LibDepositing.sol

```solidity
67	    function processDeposits(
68	        TaikoData.State storage _state,
69	        TaikoData.Config memory _config,
70	        address _feeRecipient
71	    )
72	        internal
73	        returns (TaikoData.EthDeposit[] memory deposits_)
74	    {
```

*GitHub* : [67..74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L67-L74)


---

	 - contracts/L1/libs/LibProposing.sol

```solidity
68	    function proposeBlock(
69	        TaikoData.State storage _state,
70	        TaikoData.Config memory _config,
71	        IAddressResolver _resolver,
72	        bytes calldata _data,
73	        bytes calldata _txList
74	    )
75	        internal
76	        returns (TaikoData.BlockMetadata memory meta_, TaikoData.EthDeposit[] memory deposits_)
77	    {
```

*GitHub* : [68..77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L68-L77)


---

	 - contracts/L1/libs/LibProving.sol

```solidity
269	    function _createTransition(
270	        TaikoData.State storage _state,
271	        TaikoData.Block storage _blk,
272	        TaikoData.Transition memory _tran,
273	        uint64 slot
274	    )
275	        private
276	        returns (uint32 tid_, TaikoData.TransitionState storage ts_)
277	    {
```

*GitHub* : [269..277](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L269-L277)


---

	 - contracts/L1/libs/LibUtils.sol

```solidity
70	    function getTransitionId(
71	        TaikoData.State storage _state,
72	        TaikoData.Block storage _blk,
73	        uint64 _slot,
74	        bytes32 _parentHash
75	    )
76	        internal
77	        view
78	        returns (uint32 tid_)
79	    {
```

*GitHub* : [70..79](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L70-L79)


---

	 - contracts/L1/libs/LibVerifying.sol

```solidity
85	    function verifyBlocks(
86	        TaikoData.State storage _state,
87	        TaikoData.Config memory _config,
88	        IAddressResolver _resolver,
89	        uint64 _maxBlocksToVerify
90	    )
91	        internal
92	    {
```

*GitHub* : [85..92](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L85-L92)


---

	 - contracts/L1/provers/Guardians.sol

```solidity
53	    function setGuardians(
54	        address[] memory _newGuardians,
55	        uint8 _minGuardians
56	    )
57	        external
58	        onlyOwner
59	        nonReentrant
60	    {
...
111	    function approve(uint256 _operationId, bytes32 _hash) internal returns (bool approved_) {
```

*GitHub* : [53..60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L53-L60), [111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L111)


---

	 - contracts/signal/SignalService.sol

```solidity
56	    function authorize(address _addr, bool _authorize) external onlyOwner {
```

*GitHub* : [56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L56), [235..243](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L235-L243)


---

	 - contracts/bridge/Bridge.sol


*GitHub* : [101..108](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L101-L108), [155..163](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L155-L163), [217..225](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L217-L225), [515](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L515)


---

	 - contracts/tokenvault/ERC1155Vault.sol


*GitHub* : [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L93), [127..136](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L127-L136), [240..246](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L240-L246)


---

	 - contracts/tokenvault/ERC20Vault.sol


*GitHub* : [148..157](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L148-L157), [348..356](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L348-L356)


---

	 - contracts/tokenvault/ERC721Vault.sol


*GitHub* : [77..82](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L77-L82), [110..119](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L110-L119), [187..193](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L187-L193)


---

	 - contracts/verifiers/SgxVerifier.sol


*GitHub* : [100..103](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L100-L103), [118..121](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L118-L121), [195..201](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L195-L201), [233](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L233)


---

	 - contracts/team/airdrop/MerkleClaimable.sol


*GitHub* : [67](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L67)


---

	 - contracts/team/TimelockTokenPool.sol


*GitHub* : [135](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L135)


---

	 - contracts/automata-attestation/AutomataDcapV3Attestation.sol


*GitHub* : [73..79](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L73-L79), [88..94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L88-L94), [248..252](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L248-L252), [364..368](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L364-L368)


---

	 - contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol


*GitHub* : [267..274](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L267-L274)

### [G-28]<a name="g-28"></a> Optimize Gas by Using Do-While Loops

Using `do-while` loops instead of `for` loops can be more gas-efficient. 
Even if you add an `if` condition to account for the case where the loop doesn't execute at all, a `do-while` loop can still be cheaper in terms of gas.

*There are 54 instance(s) of this issue:*


---

	 - contracts/L1/hooks/AssignmentHook.sol

```solidity
172	        for (uint256 i; i < _tierFees.length; ++i) {
173	            if (_tierFees[i].tier == _tierId) return _tierFees[i].fee;
174	        }
```

*GitHub* : [172..174](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L172-L174)


---

	 - contracts/L1/libs/LibDepositing.sol

```solidity
86	            for (uint256 i; i < deposits_.length;) {
87	                uint256 data = _state.ethDeposits[j % _config.ethDepositRingBufferSize];
88	                deposits_[i] = TaikoData.EthDeposit({
89	                    recipient: address(uint160(data >> 96)),
90	                    amount: uint96(data),
91	                    id: j
92	                });
93	                uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount;
94	
95	                // Unchecked is safe:
96	                // - _fee cannot be bigger than deposits_[i].amount
97	                // - all values are in the same range (uint96) except loop
98	                // counter, which obviously cannot be bigger than uint95
99	                // otherwise the function would be gassing out.
100	                unchecked {
101	                    deposits_[i].amount -= _fee;
102	                    totalFee += _fee;
103	                    ++i;
104	                    ++j;
105	                }
106	            }
```

*GitHub* : [86..106](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L86-L106)


---

	 - contracts/L1/libs/LibProposing.sol

```solidity
244	            for (uint256 i; i < params.hookCalls.length; ++i) {
245	                if (uint160(prevHook) >= uint160(params.hookCalls[i].hook)) {
246	                    revert L1_INVALID_HOOK();
247	                }
248	
249	                // When a hook is called, all ether in this contract will be send to the hook.
250	                // If the ether sent to the hook is not used entirely, the hook shall send the Ether
251	                // back to this contract for the next hook to use.
252	                // Proposers shall choose use extra hooks wisely.
253	                IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }(
254	                    blk, meta_, params.hookCalls[i].data
255	                );
256	
257	                prevHook = params.hookCalls[i].hook;
258	            }
```

*GitHub* : [244..258](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L244-L258)


---

	 - contracts/L1/libs/LibVerifying.sol

```solidity
127	            while (blockId < b.numBlocks && numBlocksVerified < _maxBlocksToVerify) {
128	                slot = blockId % _config.blockRingBufferSize;
129	
130	                blk = _state.blocks[slot];
131	                if (blk.blockId != blockId) revert L1_BLOCK_MISMATCH();
132	
133	                tid = LibUtils.getTransitionId(_state, blk, slot, blockHash);
134	                // When `tid` is 0, it indicates that there is no proven
135	                // transition with its parentHash equal to the blockHash of the
136	                // most recently verified block.
137	                if (tid == 0) break;
138	
139	                // A transition with the correct `parentHash` has been located.
140	                TaikoData.TransitionState storage ts = _state.transitions[slot][tid];
141	
142	                // It's not possible to verify this block if either the
143	                // transition is contested and awaiting higher-tier proof or if
144	                // the transition is still within its cooldown period.
145	                if (ts.contester != address(0)) {
146	                    break;
147	                } else {
148	                    if (tierProvider == address(0)) {
149	                        tierProvider = _resolver.resolve("tier_provider", false);
150	                    }
151	                    if (
152	                        uint256(ITierProvider(tierProvider).getTier(ts.tier).cooldownWindow) * 60
153	                            + uint256(ts.timestamp).max(_state.slotB.lastUnpausedAt) > block.timestamp
154	                    ) {
155	                        // If cooldownWindow is 0, the block can theoretically
156	                        // be proved and verified within the same L1 block.
157	                        break;
158	                    }
159	                }
160	
161	                // Mark this block as verified
162	                blk.verifiedTransitionId = tid;
163	
164	                // Update variables
165	                blockHash = ts.blockHash;
166	                stateRoot = ts.stateRoot;
167	
168	                // We consistently return the liveness bond and the validity
169	                // bond to the actual prover of the transition utilized for
170	                // block verification. If the actual prover happens to be the
171	                // block's assigned prover, he will receive both deposits,
172	                // ultimately earning the proving fee paid during block
173	                // proposal. In contrast, if the actual prover is different from
174	                // the block's assigned prover, the liveness bond serves as a
175	                // reward to the actual prover, while the assigned prover
176	                // forfeits his liveness bond due to failure to fulfill their
177	                // commitment.
178	                uint256 bondToReturn = uint256(ts.validityBond) + blk.livenessBond;
179	
180	                // Nevertheless, it's possible for the actual prover to be the
181	                // same individual or entity as the block's assigned prover.
182	                // Consequently, we have chosen to grant the actual prover only
183	                // half of the liveness bond as a reward.
184	                if (ts.prover != blk.assignedProver) {
185	                    bondToReturn -= blk.livenessBond >> 1;
186	                }
187	
188	                IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));
189	                tko.transfer(ts.prover, bondToReturn);
190	
191	                // Note: We exclusively address the bonds linked to the
192	                // transition used for verification. While there may exist
193	                // other transitions for this block, we disregard them entirely.
194	                // The bonds for these other transitions are burned either when
195	                // the transitions are generated or proven. In such cases, both
196	                // the provers and contesters of those transitions forfeit their bonds.
197	
198	                emit BlockVerified({
199	                    blockId: blockId,
200	                    assignedProver: blk.assignedProver,
201	                    prover: ts.prover,
202	                    blockHash: blockHash,
203	                    stateRoot: stateRoot,
204	                    tier: ts.tier,
205	                    contestations: ts.contestations
206	                });
207	
208	                ++blockId;
209	                ++numBlocksVerified;
210	            }
```

*GitHub* : [127..210](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L127-L210)


---

	 - contracts/L1/provers/Guardians.sol

```solidity
74	        for (uint256 i; i < guardians.length; ++i) {
75	            delete guardianIds[guardians[i]];
76	        }
...
80	        for (uint256 i = 0; i < _newGuardians.length; ++i) {
81	            address guardian = _newGuardians[i];
82	            if (guardian == address(0)) revert INVALID_GUARDIAN();
83	            // This makes sure there are not duplicate addresses
84	            if (guardianIds[guardian] != 0) revert INVALID_GUARDIAN_SET();
85	
86	            // Save and index the guardian
87	            guardians.push(guardian);
88	            guardianIds[guardian] = guardians.length;
89	        }
...
133	            for (uint256 i; i < guardiansLength; ++i) {
134	                if (bits & 1 == 1) ++count;
135	                if (count == minGuardians) return true;
136	                bits >>= 1;
137	            }
```

*GitHub* : [74..76](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L74-L76), [80..89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L80-L89), [133..137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L133-L137)


---

	 - contracts/L2/TaikoL2.sol

```solidity
234	            for (uint256 i; i < 255 && _blockId >= i + 1; ++i) {
235	                uint256 j = _blockId - i - 1;
236	                inputs[j % 255] = blockhash(j);
237	            }
```

*GitHub* : [234..237](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L234-L237)


---

	 - contracts/signal/SignalService.sol

```solidity
104	        for (uint256 i; i < hopProofs.length; ++i) {
105	            hop = hopProofs[i];
106	
107	            bytes32 signalRoot = _verifyHopProof(chainId, app, signal, value, hop, signalService);
108	            bool isLastHop = i == hopProofs.length - 1;
109	
110	            if (isLastHop) {
111	                if (hop.chainId != block.chainid) revert SS_INVALID_LAST_HOP_CHAINID();
112	                signalService = address(this);
113	            } else {
114	                if (hop.chainId == 0 || hop.chainId == block.chainid) {
115	                    revert SS_INVALID_MID_HOP_CHAINID();
116	                }
117	                signalService = resolve(hop.chainId, "signal_service", false);
118	            }
119	
120	            bool isFullProof = hop.accountProof.length > 0;
121	
122	            _cacheChainData(hop, chainId, hop.blockId, signalRoot, isFullProof, isLastHop);
123	
124	            bytes32 kind = isFullProof ? LibSignals.STATE_ROOT : LibSignals.SIGNAL_ROOT;
125	            signal = signalForChainData(chainId, kind, hop.blockId);
126	            value = hop.rootHash;
127	            chainId = hop.chainId;
128	            app = signalService;
129	        }
```

*GitHub* : [104..129](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L104-L129)


---

	 - contracts/bridge/Bridge.sol

```solidity
90	        for (uint256 i; i < _msgHashes.length; ++i) {
91	            bytes32 msgHash = _msgHashes[i];
92	            proofReceipt[msgHash].receivedAt = _timestamp;
93	            emit MessageSuspended(msgHash, _suspend);
94	        }
```

*GitHub* : [90..94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L90-L94)


---

	 - contracts/tokenvault/ERC1155Vault.sol


*GitHub* : [47..49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L47-L49), [269..277](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L269-L277), [251..253](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L251-L253)


---

	 - contracts/tokenvault/ERC721Vault.sol


*GitHub* : [34..36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L34-L36), [175..177](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L175-L177), [170..172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L170-L172), [210..212](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L210-L212), [197..199](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L197-L199)


---

	 - contracts/thirdparty/optimism/rlp/RLPReader.sol


*GitHub* : [74..91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L74-L91)


---

	 - contracts/thirdparty/optimism/rlp/RLPWriter.sol


*GitHub* : [39..42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L39-L42), [46..48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L46-L48), [59..63](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L59-L63), [66..68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66-L68)


---

	 - contracts/thirdparty/optimism/trie/MerkleTrie.sol


*GitHub* : [85..196](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85-L196), [208..213](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L208-L213), [244..248](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L244-L248)


---

	 - contracts/verifiers/SgxVerifier.sol


*GitHub* : [104..112](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L104-L112), [210..223](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210-L223)


---

	 - contracts/team/airdrop/ERC721Airdrop.sol


*GitHub* : [59..61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59-L61)


---

	 - contracts/automata-attestation/AutomataDcapV3Attestation.sol


*GitHub* : [80..85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L80-L85), [95..100](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L95-L100), [191..198](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L191-L198), [214..225](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L214-L225), [240..244](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L240-L244), [259..298](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L259-L298), [420..430](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L420-L430)


---

	 - contracts/automata-attestation/lib/PEMCertChainLib.sol


*GitHub* : [54..69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L54-L69), [244..246](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L244-L246), [286..338](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L286-L338), [301..328](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L301-L328), [354..372](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L354-L372)


---

	 - contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol


*GitHub* : [153..162](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L153-L162), [281..283](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L281-L283)


---

	 - contracts/automata-attestation/utils/BytesUtils.sol


*GitHub* : [80..102](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L80-L102), [333..342](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L333-L342)


---

	 - contracts/automata-attestation/utils/RsaVerify.sol


*GitHub* : [140..144](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L140-L144), [158..162](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L158-L162), [152..156](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L152-L156), [174..178](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L174-L178), [273..277](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L273-L277), [283..287](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L283-L287), [290..294](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L290-L294)


---

	 - contracts/automata-attestation/utils/X509DateUtils.sol


*GitHub* : [48..54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L48-L54), [59..61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L59-L61)

### [G-29]<a name="g-29"></a> Use Assembly for Efficient Event Emission

To efficiently emit events, consider utilizing assembly by making use of scratch space and the free memory pointer.
This approach can potentially avoid the costs associated with memory expansion.

However, it's crucial to cache and restore the free memory pointer for safe optimization.
Good examples of such practices can be found in well-optimized [Solady's codebases](https://github.com/Vectorized/solady/blob/main/src/tokens/ERC1155.sol#L167).
Please review your code and consider the potential gas savings of this approach.

*There are 55 instance(s) of this issue:*


---

	 - contracts/common/AddressManager.sol

```solidity
50	        emit AddressSet(_chainId, _name, _newAddress, oldAddress);
```

*GitHub* : [50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L50)


---

	 - contracts/common/EssentialContract.sol

```solidity
71	        emit Paused(msg.sender);
...
80	        emit Unpaused(msg.sender);
```

*GitHub* : [71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L71), [80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L80)


---

	 - contracts/L1/hooks/AssignmentHook.sol

```solidity
129	        emit BlockAssigned(_blk.assignedProver, _meta, assignment);
```

*GitHub* : [129](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L129)


---

	 - contracts/L1/libs/LibDepositing.sol

```solidity
50	        emit EthDeposited(
51	            TaikoData.EthDeposit({
52	                recipient: recipient_,
53	                amount: uint96(msg.value),
54	                id: _state.slotA.numEthDeposits
55	            })
56	        );
```

*GitHub* : [50..56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L50-L56)


---

	 - contracts/L1/libs/LibProposing.sol

```solidity
166	                    emit BlobCached(meta_.blobHash);
...
273	        emit BlockProposed({
274	            blockId: blk.blockId,
275	            assignedProver: blk.assignedProver,
276	            livenessBond: _config.livenessBond,
277	            meta: meta_,
278	            depositsProcessed: deposits_
279	        });
```

*GitHub* : [166](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L166), [273..279](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L273-L279)


---

	 - contracts/L1/libs/LibProving.sol

```solidity
80	        emit ProvingPaused(_pause);
...
254	                emit TransitionContested({
255	                    blockId: blk.blockId,
256	                    tran: _tran,
257	                    contester: msg.sender,
258	                    contestBond: tier.contestBond,
259	                    tier: _proof.tier
260	                });
...
230	                emit TransitionProved({
231	                    blockId: blk.blockId,
232	                    tran: _tran,
233	                    prover: msg.sender,
234	                    validityBond: 0,
235	                    tier: _proof.tier
236	                });
```

*GitHub* : [80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L80), [254..260](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L254-L260), [230..236](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L230-L236), [209..215](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L209-L215)


---

	 - contracts/L1/libs/LibVerifying.sol


*GitHub* : [73..81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L73-L81), [198..206](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L198-L206)


---

	 - contracts/L1/provers/GuardianProver.sol


*GitHub* : [54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L54)


---

	 - contracts/L1/provers/Guardians.sol


*GitHub* : [95](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L95), [121](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L121)


---

	 - contracts/L2/CrossChainOwned.sol


*GitHub* : [53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L53)


---

	 - contracts/L2/TaikoL2.sol


*GitHub* : [157](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L157)


---

	 - contracts/L2/TaikoL2EIP1559Configurable.sol


*GitHub* : [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L39)


---

	 - contracts/signal/SignalService.sol


*GitHub* : [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L59), [250](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L250), [268](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L268)


---

	 - contracts/bridge/Bridge.sol


*GitHub* : [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L93), [111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L111), [151](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L151), [210](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L210), [208](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L208), [303](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L303), [301](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L301), [336](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L336), [519](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L519)


---

	 - contracts/tokenvault/BridgedERC20Base.sol


*GitHub* : [51](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L51), [63](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L63), [80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L80)


---

	 - contracts/tokenvault/ERC1155Vault.sol


*GitHub* : [80..89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L80-L89), [114..123](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L114-L123), [149..156](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L149-L156), [314..320](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L314-L320)


---

	 - contracts/tokenvault/ERC20Vault.sol


*GitHub* : [191..199](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L191-L199), [241..249](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L241-L249), [273..281](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L273-L281), [306..312](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L306-L312), [425..432](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L425-L432)


---

	 - contracts/tokenvault/ERC721Vault.sol


*GitHub* : [64..73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L64-L73), [97..106](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L97-L106), [131..138](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L131-L138), [250..256](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L250-L256)


---

	 - contracts/verifiers/SgxVerifier.sol


*GitHub* : [109](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L109), [220](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220), [230](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L230)


---

	 - contracts/team/airdrop/ERC20Airdrop2.sol


*GitHub* : [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L93)


---

	 - contracts/team/airdrop/MerkleClaimable.sol


*GitHub* : [74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L74)


---

	 - contracts/team/TimelockTokenPool.sol


*GitHub* : [143](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L143), [157](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L157), [222](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L222)

### [G-30]<a name="g-30"></a> Optimize External Calls with Assembly for Memory Efficiency

Using interfaces to make external contract calls in Solidity is convenient but can be inefficient in terms of memory utilization.
Each such call involves creating a new memory location to store the data being passed, thus incurring memory expansion costs. 

Inline assembly allows for optimized memory usage by re-using already allocated memory spaces or using the scratch space for smaller datasets.
This can result in notable gas savings, especially for contracts that make frequent external calls.

Additionally, using inline assembly enables important safety checks like verifying if the target address has code deployed to it using `extcodesize(addr)` before making the call, mitigating risks associated with contract interactions.

*There are 92 instance(s) of this issue:*


---

	 - contracts/common/AddressResolver.sol

```solidity
83	        addr_ = payable(IAddressManager(addressManager).getAddress(_chainId, _name));
```

*GitHub* : [83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L83)


---

	 - contracts/libs/LibAddress.sol

```solidity
56	        try IERC165(_addr).supportsInterface(_interfaceId) returns (bool _result) {
...
71	            return IERC1271(_addr).isValidSignature(_hash, _sig) == _EIP1271_MAGICVALUE;
```

*GitHub* : [56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L56), [71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L71)


---

	 - contracts/L1/hooks/AssignmentHook.sol

```solidity
102	        tko.transferFrom(_blk.assignedProver, taikoL1Address, _blk.livenessBond);
...
149	                ITaikoL1(_taikoL1Address).getConfig().chainId,
```

*GitHub* : [102](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L102), [149](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L149)


---

	 - contracts/L1/libs/LibDepositing.sol

```solidity
41	        _resolver.resolve("bridge", false).sendEther(msg.value);
```

*GitHub* : [41](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L41)


---

	 - contracts/L1/libs/LibProposing.sol

```solidity
207	        meta_.minTier = ITierProvider(_resolver.resolve("tier_provider", false)).getMinTier(
...
207	        meta_.minTier = ITierProvider(_resolver.resolve("tier_provider", false)).getMinTier(
...
237	            IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));
...
238	            uint256 tkoBalance = tko.balanceOf(address(this));
```

*GitHub* : [207](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L207), [207](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L207), [237](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L237), [238](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L238), [253](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L253), [253](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L253), [268](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L268), [309](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L309), [315](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L315)


---

	 - contracts/L1/libs/LibProving.sol


*GitHub* : [141](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L141), [141](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L141), [161](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L161), [177](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L177), [187](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L187), [196](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L196), [242](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L242), [371](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L371), [367](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L367), [384](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L384), [382](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L382)


---

	 - contracts/L1/libs/LibVerifying.sol


*GitHub* : [149](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L149), [152](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L152), [188](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L188), [189](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L189), [232](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L232), [234](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L234), [239](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L239)


---

	 - contracts/L1/provers/GuardianProver.sol


*GitHub* : [51](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L51)


---

	 - contracts/L2/CrossChainOwned.sol


*GitHub* : [45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L45)


---

	 - contracts/L2/TaikoL2.sol


*GitHub* : [148](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L148), [176](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L176)


---

	 - contracts/bridge/Bridge.sol


*GitHub* : [150](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L150), [174](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L174), [199](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L199), [199](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L199), [342](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L342), [522](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L522)


---

	 - contracts/tokenvault/adapters/USDCAdapter.sol


*GitHub* : [44](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L44), [48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L48), [49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L49)


---

	 - contracts/tokenvault/BridgedERC20Base.sol


*GitHub* : [82](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L82)


---

	 - contracts/tokenvault/BaseVault.sol


*GitHub* : [53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L53), [64](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L64)


---

	 - contracts/tokenvault/ERC1155Vault.sol


*GitHub* : [77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L77), [77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L77), [230](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L230), [226](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L226), [263](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L263), [266](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L266), [270](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L270), [252](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L252), [281](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L281)


---

	 - contracts/tokenvault/ERC20Vault.sol


*GitHub* : [164](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L164), [184](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L184), [185](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L185), [239](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L239), [239](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L239), [333](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L333), [368](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L368), [369](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L369), [370](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L370), [378](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L378), [380](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L380), [360](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L360), [384](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L384)


---

	 - contracts/tokenvault/ERC721Vault.sol


*GitHub* : [62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L62), [62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L62), [176](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L176), [171](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L171), [206](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L206), [207](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L207), [211](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L211), [198](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L198), [217](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L217)


---

	 - contracts/verifiers/SgxVerifier.sol


*GitHub* : [128](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L128), [185](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L185)


---

	 - contracts/team/airdrop/ERC20Airdrop.sol


*GitHub* : [63](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L63), [71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L71)


---

	 - contracts/team/airdrop/ERC20Airdrop2.sol


*GitHub* : [91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L91)


---

	 - contracts/team/airdrop/ERC721Airdrop.sol


*GitHub* : [60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L60)


---

	 - contracts/team/TimelockTokenPool.sol


*GitHub* : [219](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L219)


---

	 - contracts/automata-attestation/AutomataDcapV3Attestation.sol


*GitHub* : [285](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L285), [322](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L322), [325](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L325), [424](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L424)


---

	 - contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol


*GitHub* : [278](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L278)

### [G-31]<a name="g-31"></a> Use Assembly for Hash Calculations

In certain cases, using inline assembly to calculate hashes can lead to significant gas savings. Solidity's built-in keccak256 function is convenient but costs more gas than the equivalent assembly code. However, it's important to note that using assembly should be done with care as it's less readable and could increase the risk of introducing errors.

*There are 25 instance(s) of this issue:*


---

	 - contracts/L1/hooks/AssignmentHook.sol

```solidity
146	        return keccak256(
```

*GitHub* : [146](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L146)


---

	 - contracts/L1/libs/LibProposing.sol

```solidity
126	                depositsHash: keccak256(abi.encode(deposits_)),
...
189	            meta_.blobHash = keccak256(_txList);
...
204	        meta_.difficulty = keccak256(abi.encodePacked(block.prevrandao, b.numBlocks, block.number));
...
213	            metaHash: keccak256(abi.encode(meta_)),
```

*GitHub* : [126](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L126), [189](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L189), [204](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L204), [213](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L213)


---

	 - contracts/L1/libs/LibProving.sol

```solidity
121	        if (blk.blockId != _meta.id || blk.metaHash != keccak256(abi.encode(_meta))) {
```

*GitHub* : [121](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L121)


---

	 - contracts/L1/provers/GuardianProver.sol

```solidity
46	        bytes32 hash = keccak256(abi.encode(_meta, _tran));
```

*GitHub* : [46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L46)


---

	 - contracts/signal/SignalService.sol

```solidity
186	        return keccak256(abi.encode(_chainId, _kind, _blockId));
...
203	        return keccak256(abi.encodePacked("SIGNAL", _chainId, _app, _signal));
```

*GitHub* : [186](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L186), [203](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L203)


---

	 - contracts/bridge/Bridge.sol

```solidity
450	        return keccak256(abi.encode("TAIKO_MESSAGE", _message));
```

*GitHub* : [450](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L450)


---

	 - contracts/tokenvault/ERC20Vault.sol


*GitHub* : [176](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L176), [176](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L176), [177](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L177), [177](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L177)


---

	 - contracts/thirdparty/optimism/Bytes.sol


*GitHub* : [150](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L150), [150](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L150)


---

	 - contracts/thirdparty/optimism/trie/MerkleTrie.sol


*GitHub* : [100](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L100), [94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L94)


---

	 - contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol


*GitHub* : [55](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L55)


---

	 - contracts/verifiers/SgxVerifier.sol


*GitHub* : [182](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L182)


---

	 - contracts/team/airdrop/MerkleClaimable.sol


*GitHub* : [68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L68)


---

	 - contracts/team/TimelockTokenPool.sol


*GitHub* : [170](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L170)


---

	 - contracts/automata-attestation/AutomataDcapV3Attestation.sol


*GitHub* : [292](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L292)


---

	 - contracts/automata-attestation/utils/BytesUtils.sol


*GitHub* : [372](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L372), [372](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L372)

### [G-32]<a name="g-32"></a> Consider Using Solady's Gas Optimized Lib for Math

Utilizing gas-optimized math functions from libraries like [Solady](https://github.com/Vectorized/solady/blob/main/src/utils/FixedPointMathLib.sol) can lead to more efficient smart contracts.
This is particularly beneficial in contracts where these operations are frequently used.

*There are 58 instance(s) of this issue:*


---

	 - contracts/L1/gov/TaikoGovernor.sol

```solidity
124	        return 1_000_000_000 ether / 10_000; // 0.01% of Taiko Token
```

*GitHub* : [124](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L124)


---

	 - contracts/L1/libs/LibDepositing.sol

```solidity
83	            uint96 fee = uint96(_config.ethDepositMaxFee.min(block.basefee * _config.ethDepositGas));
```

*GitHub* : [83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L83)


---

	 - contracts/L1/libs/LibProposing.sol

```solidity
21	    uint256 public constant MAX_BYTES_PER_BLOB = 4096 * 32;
```

*GitHub* : [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L21)


---

	 - contracts/L1/libs/LibProving.sol

```solidity
415	            + _tier.provingWindow * 60 >= block.timestamp;
```

*GitHub* : [415](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L415)


---

	 - contracts/L1/libs/LibVerifying.sol

```solidity
152	                        uint256(ITierProvider(tierProvider).getTier(ts.tier).cooldownWindow) * 60
...
251	                || _config.blockMaxTxListBytes > 128 * 1024 // calldata up to 128K
...
262	                || _config.ethDepositMaxFee > type(uint96).max / _config.ethDepositMaxCountPerBlock
```

*GitHub* : [152](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L152), [251](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L251), [262](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L262)


---

	 - contracts/L1/TaikoL1.sol

```solidity
215	            ethDepositMaxFee: 1 ether / 10,
```

*GitHub* : [215](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L215)


---

	 - contracts/L2/Lib1559Math.sol

```solidity
28	        return _ethQty(_gasExcess, _adjustmentFactor) / LibFixedPointMath.SCALING_FACTOR
29	            / _adjustmentFactor;
...
28	        return _ethQty(_gasExcess, _adjustmentFactor) / LibFixedPointMath.SCALING_FACTOR
```

*GitHub* : [28..29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L28-L29), [28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L28), [41](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L41), [41](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L41)


---

	 - contracts/L2/TaikoL2.sol


*GitHub* : [213](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L213), [213](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L213), [280](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L280), [291](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L291)


---

	 - contracts/thirdparty/optimism/rlp/RLPWriter.sol


*GitHub* : [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L39), [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L47)


---

	 - contracts/thirdparty/solmate/LibFixedPointMath.sol


*GitHub* : [33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L33), [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L39), [40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L40), [46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L46), [48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L48), [49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L49), [54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L54), [55](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L55), [56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L56), [57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L57), [58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L58), [77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L77)


---

	 - contracts/team/airdrop/ERC20Airdrop2.sol


*GitHub* : [117..118](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L117-L118), [117..118](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L117-L118)


---

	 - contracts/team/TimelockTokenPool.sol


*GitHub* : [197](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L197), [198](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L198), [264](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L264), [264](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L264)


---

	 - contracts/automata-attestation/lib/PEMCertChainLib.sol


*GitHub* : [359](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L359)


---

	 - contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol


*GitHub* : [155](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L155), [158](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L158), [158](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L158), [159](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L159), [159](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L159)


---

	 - contracts/automata-attestation/utils/Asn1Decode.sol


*GitHub* : [145](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L145), [203](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L203)


---

	 - contracts/automata-attestation/utils/BytesUtils.sol


*GitHub* : [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L93), [344](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L344)


---

	 - contracts/automata-attestation/utils/X509DateUtils.sol


*GitHub* : [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L21), [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L21), [24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L24), [25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L25), [26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L26), [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L27), [28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L28), [29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L29), [60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L60), [63](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L63), [64](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L64), [65](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L65)

### [G-33]<a name="g-33"></a> Trade-offs Between Modifiers and Internal Functions

In Solidity, both internal functions and modifiers are used to refactor and manage code, but they come with their own trade-offs, especially in terms of gas cost and flexibility.

#### Modifiers:
- Less runtime gas cost (saves around 24 gas per function call).
- Increases deployment gas cost due to repetitive code.
- Can only be executed at the start or end of a function.

#### Internal Functions:
- Lower deployment cost.
- Can be executed at any point in a function.
- Slightly higher runtime gas cost (24 gas) due to the need to jump to the function's location in bytecode.

#### Recommendations:
- Use modifiers for high-frequency functions where runtime gas cost matters the most.
- Use internal functions where the priority is reducing deployment gas cost or when you need more flexibility in the function's logic.

Example analysis shows that using modifiers can increase deployment costs by over 35k gas but save 24 gas per function call during runtime. Choose wisely based on your specific use case.

*There are 168 instance(s) of this issue:*


---

	 - contracts/common/AddressManager.sol

```solidity
30	    function init(address _owner) external initializer {
...
45	        onlyOwner
```

*GitHub* : [30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L30), [45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L45)


---

	 - contracts/common/AddressResolver.sol

```solidity
24	    modifier onlyFromNamed(bytes32 _name) {
25	        if (msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();
26	        _;
27	    }
...
58	    function __AddressResolver_init(address _addressManager) internal virtual onlyInitializing {
```

*GitHub* : [24..27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L24-L27), [58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L58)


---

	 - contracts/common/EssentialContract.sol

```solidity
41	    modifier onlyFromOwnerOrNamed(bytes32 _name) {
42	        if (msg.sender != owner() && msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();
43	        _;
44	    }
...
46	    modifier nonReentrant() {
47	        if (_loadReentryLock() == _TRUE) revert REENTRANT_CALL();
48	        _storeReentryLock(_TRUE);
49	        _;
50	        _storeReentryLock(_FALSE);
51	    }
...
53	    modifier whenPaused() {
54	        if (!paused()) revert INVALID_PAUSE_STATUS();
55	        _;
56	    }
...
58	    modifier whenNotPaused() {
59	        if (paused()) revert INVALID_PAUSE_STATUS();
60	        _;
61	    }
...
69	    function pause() public virtual whenNotPaused {
...
78	    function unpause() public virtual whenPaused {
```

*GitHub* : [41..44](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L41-L44), [46..51](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L46-L51), [53..56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L53-L56), [58..61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L58-L61), [69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L69), [78](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L78), [101](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L101), [114](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L114), [116](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L116)


---

	 - contracts/L1/gov/TaikoGovernor.sol


*GitHub* : [37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L37)


---

	 - contracts/L1/gov/TaikoTimelockController.sol


*GitHub* : [15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L15)


---

	 - contracts/L1/hooks/AssignmentHook.sol


*GitHub* : [57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L57), [69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L69), [70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L70)


---

	 - contracts/L1/provers/GuardianProver.sol


*GitHub* : [25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L25), [41](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L41), [42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L42)


---

	 - contracts/L1/provers/Guardians.sol


*GitHub* : [58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L58), [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L59)


---

	 - contracts/L1/TaikoL1.sol


*GitHub* : [28..31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L28-L31), [48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L48), [61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L61), [62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L62), [80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L80), [81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L81), [82](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L82), [102](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L102), [103](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L103), [104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L104), [119](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L119), [119](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L119), [225](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L225)


---

	 - contracts/L1/TaikoToken.sol


*GitHub* : [32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L32), [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L47), [52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L52)


---

	 - contracts/L1/tiers/DevnetTierProvider.sol


*GitHub* : [15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L15)


---

	 - contracts/L1/tiers/MainnetTierProvider.sol


*GitHub* : [15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L15)


---

	 - contracts/L1/tiers/TestnetTierProvider.sol


*GitHub* : [15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L15)


---

	 - contracts/L2/CrossChainOwned.sol


*GitHub* : [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L39), [40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L40), [67](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L67)


---

	 - contracts/L2/TaikoL2.sol


*GitHub* : [78](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L78), [114](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L114), [168](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L168), [169](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L169), [170](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L170)


---

	 - contracts/L2/TaikoL2EIP1559Configurable.sol


*GitHub* : [31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L31)


---

	 - contracts/signal/SignalService.sol


*GitHub* : [35..38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L35-L38), [40..43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L40-L43), [48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L48), [56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L56), [91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L91), [92](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L92), [145](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L145), [216](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L216), [217](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L217), [218](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L218), [259](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L259), [260](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L260), [261](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L261), [304](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L304), [305](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L305)


---

	 - contracts/bridge/Bridge.sol


*GitHub* : [64..67](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L64-L67), [75](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L75), [87](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L87), [106](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L106), [107](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L107), [119](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L119), [120](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L120), [160](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L160), [161](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L161), [162](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L162), [222](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L222), [223](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L223), [224](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L224), [315](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L315), [316](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L316), [317](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L317), [466](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L466)


---

	 - contracts/tokenvault/adapters/USDCAdapter.sol


*GitHub* : [38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L38)


---

	 - contracts/tokenvault/BridgedERC20.sol


*GitHub* : [37..42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L37-L42), [62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L62), [80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L80), [85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L85)


---

	 - contracts/tokenvault/BridgedERC20Base.sol


*GitHub* : [41](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L41), [42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L42), [43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L43), [57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L57), [57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L57), [75](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L75), [75](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L75)


---

	 - contracts/tokenvault/BridgedERC721.sol


*GitHub* : [40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L40), [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L59), [60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L60), [61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L61), [74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L74), [75](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L75), [76](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L76)


---

	 - contracts/tokenvault/BridgedERC1155.sol


*GitHub* : [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L47), [72](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L72), [73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L73), [74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L74), [89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L89), [90](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L90), [91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L91), [106](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L106), [107](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L107), [108](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L108)


---

	 - contracts/tokenvault/BaseNFTVault.sol


*GitHub* : [140..151](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L140-L151)


---

	 - contracts/tokenvault/BaseVault.sol


*GitHub* : [22..27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L22-L27), [32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L32), [50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L50), [61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L61)


---

	 - contracts/tokenvault/ERC1155Vault.sol


*GitHub* : [42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L42), [43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L43), [44](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L44), [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L93), [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L93), [134](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L134), [135](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L135)


---

	 - contracts/tokenvault/ERC20Vault.sol


*GitHub* : [153](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L153), [154](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L154), [155](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L155), [210](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L210), [211](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L211), [256](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L256), [257](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L257), [292](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L292), [293](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L293)


---

	 - contracts/tokenvault/ERC721Vault.sol


*GitHub* : [29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L29), [30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L30), [31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L31), [80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L80), [81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L81), [117](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L117), [118](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L118)


---

	 - contracts/verifiers/GuardianVerifier.sol


*GitHub* : [18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L18)


---

	 - contracts/verifiers/SgxVerifier.sol


*GitHub* : [83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L83), [92](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L92), [102](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L102), [145](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L145)


---

	 - contracts/team/airdrop/ERC20Airdrop.sol


*GitHub* : [36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L36), [57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L57)


---

	 - contracts/team/airdrop/ERC20Airdrop2.sol


*GitHub* : [39..44](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L39-L44), [64](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L64), [78](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L78), [88](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L88)


---

	 - contracts/team/airdrop/ERC721Airdrop.sol


*GitHub* : [34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L34), [53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L53)


---

	 - contracts/team/airdrop/MerkleClaimable.sol


*GitHub* : [33..39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L33-L39), [51](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L51), [62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L62), [67](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L67)


---

	 - contracts/team/TimelockTokenPool.sol


*GitHub* : [118](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L118), [135](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L135), [150](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L150)


---

	 - contracts/automata-attestation/AutomataDcapV3Attestation.sol


*GitHub* : [60..63](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L60-L63), [65](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L65), [69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L69), [78](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L78), [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L93), [108](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L108), [116](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L116), [122](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L122)

### [G-34]<a name="g-34"></a> Optimize Boolean States with `uint256(1/2)`

Boolean variables in Solidity are more expensive than `uint256` or any type that takes up a full word, due to additional gas costs associated with write operations.
When using boolean variables, each write operation emits an extra SLOAD to read the slot's contents, replace the bits taken up by the boolean, and then write back.
This process cannot be disabled and leads to extra gas consumption.

By using `uint256(1)` and `uint256(2)` for representing true and false states, you can avoid a `Gwarmaccess` (100 gas) cost and also avoid a `Gsset` (20000 gas) cost when changing from `false` to `true`, after having been `true` in the past.
This approach helps in optimizing gas usage, making your contract more cost-effective.

[Usage in OpenZeppelin ReentrancyGuard.sol](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/58f635312aa21f947cae5f8578638a85aa2519f5/contracts/security/ReentrancyGuard.sol#L23-L27)

*There are 10 instance(s) of this issue:*


---

	 - contracts/signal/SignalService.sol

```solidity
21	    mapping(address addr => bool authorized) public isAuthorized;
```

*GitHub* : [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L21)


---

	 - contracts/bridge/Bridge.sol

```solidity
42	    mapping(address addr => bool banned) public addressBanned;
```

*GitHub* : [42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L42)


---

	 - contracts/tokenvault/BridgedERC20Base.sol

```solidity
14	    bool public migratingInbound;
```

*GitHub* : [14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L14)


---

	 - contracts/tokenvault/ERC20Vault.sol

```solidity
52	    mapping(address btoken => bool blacklisted) public btokenBlacklist;
```

*GitHub* : [52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L52)


---

	 - contracts/verifiers/SgxVerifier.sol

```solidity
55	    mapping(address instanceAddress => bool alreadyAttested) public addressRegistered;
```

*GitHub* : [55](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L55)


---

	 - contracts/team/airdrop/MerkleClaimable.sol

```solidity
12	    mapping(bytes32 hash => bool claimed) public isClaimed;
```

*GitHub* : [12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L12)


---

	 - contracts/automata-attestation/AutomataDcapV3Attestation.sol

```solidity
38	    bool private _checkLocalEnclaveReport;
...
39	    mapping(bytes32 enclave => bool trusted) private _trustedUserMrEnclave;
...
40	    mapping(bytes32 signer => bool trusted) private _trustedUserMrSigner;
...
47	    mapping(uint256 idx => mapping(bytes serialNum => bool revoked)) private _serialNumIsRevoked;
```

*GitHub* : [38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L38), [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L39), [40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L40), [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L47)

### [G-35]<a name="g-35"></a> Consider Packing Small `uint` When it's Possible

Packing `uint` variables into the same storage slot can help in reducing gas costs.
This is particularly useful when storing or reading multiple smaller uints (e.g., uint80) in a single transaction.
Consider using bit manipulation to pack these variables.

If you pack two `uint` variables into a single `uint` storage slot, you'd perform only one SLOAD operation (800 gas) instead of two (1,600 gas) when you read them.
This saves 800 gas for each read operation involving the two variables.

Similarly, when you need to update both variables, a single SSTORE operation would cost you 20,000 gas instead of 40,000 gas, saving you another 20,000 gas. 

Example:
```Solidity
uint160 packedVariables;

function packVariables(uint80 x, uint80 y) external {
  packedVariables = uint160(x) << 80 | uint160(y);
}
```

*There are 36 instance(s) of this issue:*


---

	 - contracts/common/EssentialContract.sol

```solidity
11	    uint8 private constant _FALSE = 1;
...
13	    uint8 private constant _TRUE = 2;
...
21	    uint8 private __reentry;
...
23	    uint8 private __paused;
```

*GitHub* : [11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L11), [13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L13), [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L21), [23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L23)


---

	 - contracts/libs/Lib4844.sol

```solidity
13	    uint32 public constant FIELD_ELEMENTS_PER_BLOB = 4096;
```

*GitHub* : [13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L13)


---

	 - contracts/L1/provers/Guardians.sol

```solidity
19	    mapping(uint32 version => mapping(bytes32 hash => uint256 approvalBits)) internal _approvals;
...
27	    uint32 public version;
...
30	    uint32 public minGuardians;
```

*GitHub* : [19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L19), [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L27), [30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L30)


---

	 - contracts/L1/tiers/ITierProvider.sol

```solidity
39	    uint16 public constant TIER_OPTIMISTIC = 100;
...
42	    uint16 public constant TIER_SGX = 200;
```

*GitHub* : [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L39), [42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L42), [45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L45), [48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L48)


---

	 - contracts/L2/CrossChainOwned.sol


*GitHub* : [16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L16), [19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L19)


---

	 - contracts/L2/TaikoL2.sol


*GitHub* : [35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L35), [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L47), [50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L50)


---

	 - contracts/signal/SignalService.sol


*GitHub* : [17](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L17)


---

	 - contracts/bridge/Bridge.sol


*GitHub* : [31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L31)


---

	 - contracts/tokenvault/BridgedERC20.sol


*GitHub* : [24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L24)


---

	 - contracts/thirdparty/optimism/trie/MerkleTrie.sol


*GitHub* : [30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L30), [33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L33), [36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L36), [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L39)


---

	 - contracts/thirdparty/solmate/LibFixedPointMath.sol


*GitHub* : [7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L7)


---

	 - contracts/verifiers/SgxVerifier.sol


*GitHub* : [30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L30), [34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L34)


---

	 - contracts/team/airdrop/ERC20Airdrop2.sol


*GitHub* : [28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L28)


---

	 - contracts/team/airdrop/MerkleClaimable.sol


*GitHub* : [18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L18), [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L21)


---

	 - contracts/team/TimelockTokenPool.sol


*GitHub* : [68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L68), [71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L71), [74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L74), [77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L77), [82](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L82)


---

	 - contracts/automata-attestation/AutomataDcapV3Attestation.sol


*GitHub* : [36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L36)

### [G-36]<a name="g-36"></a> Avoid Unnecessary Public Variables

Public storage variables increase the contract's size due to the implicit generation of public getter functions. 
This makes the contract larger and could increase deployment and interaction costs.

If you do not require other contracts to read these variables, consider making them `private` or `internal`. 

Example:
```solidity
/// 145426 gas to deploy
contract PublicState {
  address public first;
  address public second;
}
/// 77126 gas to deploy
contract PrivateState {
  address private first;
  address private second;
}
```

*There are 86 instance(s) of this issue:*


---

	 - contracts/common/AddressResolver.sol

```solidity
13	    address public addressManager;
```

*GitHub* : [13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L13)


---

	 - contracts/libs/Lib4844.sol

```solidity
10	    address public constant POINT_EVALUATION_PRECOMPILE_ADDRESS = address(0x0A);
...
13	    uint32 public constant FIELD_ELEMENTS_PER_BLOB = 4096;
...
16	    uint256 public constant BLS_MODULUS =
17	        52_435_875_175_126_190_479_447_740_508_185_965_837_690_552_500_527_637_822_603_658_699_938_581_184_513;
```

*GitHub* : [10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L10), [13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L13), [16..17](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L16-L17)


---

	 - contracts/L1/hooks/AssignmentHook.sol

```solidity
38	    uint256 public constant MAX_GAS_PAYING_PROVER = 50_000;
```

*GitHub* : [38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L38)


---

	 - contracts/L1/libs/LibProposing.sol

```solidity
21	    uint256 public constant MAX_BYTES_PER_BLOB = 4096 * 32;
```

*GitHub* : [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L21)


---

	 - contracts/L1/libs/LibProving.sol

```solidity
20	    bytes32 public constant RETURN_LIVENESS_BOND = keccak256("RETURN_LIVENESS_BOND");
...
23	    bytes32 public constant TIER_OP = bytes32("tier_optimistic");
```

*GitHub* : [20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L20), [23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L23)


---

	 - contracts/L1/provers/Guardians.sol

```solidity
11	    uint256 public constant MIN_NUM_GUARDIANS = 5;
...
16	    mapping(address guardian => uint256 id) public guardianIds;
```

*GitHub* : [11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L11), [16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L16), [23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L23), [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L27), [30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L30)


---

	 - contracts/L1/TaikoL1.sol


*GitHub* : [24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L24)


---

	 - contracts/L1/tiers/ITierProvider.sol


*GitHub* : [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L39), [42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L42), [45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L45), [48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L48)


---

	 - contracts/L2/CrossChainOwned.sol


*GitHub* : [16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L16), [19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L19)


---

	 - contracts/L2/TaikoL2.sol


*GitHub* : [32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L32), [35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L35), [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L39), [43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L43), [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L47), [50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L50)


---

	 - contracts/L2/TaikoL2EIP1559Configurable.sol


*GitHub* : [11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L11)


---

	 - contracts/signal/LibSignals.sol


*GitHub* : [8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/LibSignals.sol#L8), [11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/LibSignals.sol#L11)


---

	 - contracts/signal/SignalService.sol


*GitHub* : [17](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L17), [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L21)


---

	 - contracts/bridge/Bridge.sol


*GitHub* : [31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L31), [35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L35), [42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L42), [46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L46)


---

	 - contracts/tokenvault/adapters/USDCAdapter.sol


*GitHub* : [31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L31)


---

	 - contracts/tokenvault/BridgedERC20.sol


*GitHub* : [22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L22), [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L27), [30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L30)


---

	 - contracts/tokenvault/BridgedERC20Base.sol


*GitHub* : [11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L11), [14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L14)


---

	 - contracts/tokenvault/BridgedERC721.sol


*GitHub* : [14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L14), [17](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L17)


---

	 - contracts/tokenvault/BridgedERC1155.sol


*GitHub* : [16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L16), [19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L19)


---

	 - contracts/tokenvault/BaseNFTVault.sol


*GitHub* : [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L47), [50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L50), [53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L53), [56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L56), [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L59)


---

	 - contracts/tokenvault/ERC20Vault.sol


*GitHub* : [45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L45), [49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L49), [52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L52)


---

	 - contracts/thirdparty/solmate/LibFixedPointMath.sol


*GitHub* : [7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L7), [8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L8)


---

	 - contracts/verifiers/SgxVerifier.sol


*GitHub* : [30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L30), [34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L34), [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L39), [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L47), [55](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L55)


---

	 - contracts/team/airdrop/ERC20Airdrop.sol


*GitHub* : [13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L13), [16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L16)


---

	 - contracts/team/airdrop/ERC20Airdrop2.sol


*GitHub* : [16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L16), [19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L19), [22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L22), [25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L25), [28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L28)


---

	 - contracts/team/airdrop/ERC721Airdrop.sol


*GitHub* : [11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L11), [14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L14)


---

	 - contracts/team/airdrop/MerkleClaimable.sol


*GitHub* : [12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L12), [15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L15), [18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L18), [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L21)


---

	 - contracts/team/TimelockTokenPool.sol


*GitHub* : [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L59), [62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L62), [65](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L65), [68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L68), [71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L71), [74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L74), [77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L77), [80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L80)


---

	 - contracts/automata-attestation/AutomataDcapV3Attestation.sol


*GitHub* : [25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L25), [26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L26), [49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L49), [50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L50), [52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L52)

### [G-37]<a name="g-37"></a> Optimize by Using Assembly for Low-Level Calls' Return Data

Even second return value from a low-level call is not assigned, it is still copied to memory, leading to additional gas costs.
By employing assembly, you can bypass this memory copying, achieving a 159 gas saving.

*There are 1 instance(s) of this issue:*


---

	 - contracts/L2/CrossChainOwned.sol

```solidity
50	        (bool success,) = address(this).call(txdata);
```

*GitHub* : [50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L50)

### [G-38]<a name="g-38"></a> Avoid Zero Transfers to Save Gas

Performing token or Ether transfers with a zero amount may result in unnecessary gas consumption. 
The absence of a zero-amount check before a transfer or send operation can lead to wasted gas, as the state of the contract remains the same even if the amount is zero. 
Adding a conditional check for zero amounts can prevent these costly, unnecessary operations, thereby optimizing the contract's gas usage.

*There are 10 instance(s) of this issue:*


---

	 - contracts/L1/hooks/AssignmentHook.sol

```solidity
62	    function onBlockProposed(
63	        TaikoData.Block memory _blk,
64	        TaikoData.BlockMetadata memory _meta,
65	        bytes memory _data
66	    )
67	        external
68	        payable
69	        nonReentrant
70	        onlyFromNamed("taiko")
71	    {
```

*GitHub* : [62..71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L62-L71)


---

	 - contracts/L1/libs/LibProving.sol

```solidity
350	    function _overrideWithHigherProof(
351	        TaikoData.TransitionState storage _ts,
352	        TaikoData.Transition memory _tran,
353	        TaikoData.TierProof memory _proof,
354	        ITierProvider.Tier memory _tier,
355	        IERC20 _tko,
356	        bool _sameTransition
357	    )
358	        private
359	    {
```

*GitHub* : [350..359](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L350-L359)


---

	 - contracts/L1/libs/LibVerifying.sol

```solidity
85	    function verifyBlocks(
86	        TaikoData.State storage _state,
87	        TaikoData.Config memory _config,
88	        IAddressResolver _resolver,
89	        uint64 _maxBlocksToVerify
90	    )
91	        internal
92	    {
```

*GitHub* : [85..92](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L85-L92)


---

	 - contracts/L2/TaikoL2.sol

```solidity
163	    function withdraw(
164	        address _token,
165	        address _to
166	    )
167	        external
168	        onlyFromOwnerOrNamed("withdrawer")
169	        nonReentrant
170	        whenNotPaused
171	    {
```

*GitHub* : [163..171](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L163-L171)


---

	 - contracts/tokenvault/adapters/USDCAdapter.sol

```solidity
47	    function _burnToken(address _from, uint256 _amount) internal override {
```

*GitHub* : [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L47)


---

	 - contracts/tokenvault/ERC20Vault.sol

```solidity
320	    function _transferTokens(
321	        CanonicalERC20 memory _ctoken,
322	        address _to,
323	        uint256 _amount
324	    )
325	        private
326	        returns (address token_)
327	    {
...
348	    function _handleMessage(
349	        address _user,
350	        address _token,
351	        address _to,
352	        uint256 _amount
353	    )
354	        private
355	        returns (bytes memory msgData_, CanonicalERC20 memory ctoken_, uint256 balanceChange_)
356	    {
```

*GitHub* : [320..327](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L320-L327), [348..356](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L348-L356)


---

	 - contracts/team/airdrop/ERC20Airdrop.sol

```solidity
50	    function claimAndDelegate(
51	        address user,
52	        uint256 amount,
53	        bytes32[] calldata proof,
54	        bytes calldata delegationData
55	    )
56	        external
57	        nonReentrant
58	    {
```

*GitHub* : [50..58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L50-L58)


---

	 - contracts/team/airdrop/ERC20Airdrop2.sol

```solidity
88	    function withdraw(address user) external ongoingWithdrawals {
```

*GitHub* : [88](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L88)


---

	 - contracts/team/TimelockTokenPool.sol

```solidity
208	    function _withdraw(address _recipient, address _to) private {
```

*GitHub* : [208](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L208)

### [G-39]<a name="g-39"></a> Optimize Unsigned Integer Comparison With Zero

For unsigned integers, checking whether the integer is not equal to zero (`!= 0`) is less gas-intensive than checking whether it is greater than zero (`> 0`). 

This is because the Ethereum Virtual Machine (EVM) can perform a simple bitwise operation to check if any bit is set (which directly translates to `!= 0`), while checking for `> 0` requires additional logic.

As such, when dealing with unsigned integers in Solidity, it is recommended to use the `!= 0` comparison for gas optimization.

*There are 15 instance(s) of this issue:*


---

	 - contracts/L1/hooks/AssignmentHook.sol

```solidity
125	        if (address(this).balance > 0) {
```

*GitHub* : [125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L125)


---

	 - contracts/L1/libs/LibProving.sol

```solidity
192	            bool returnLivenessBond = blk.livenessBond > 0 && _proof.data.length == 32
```

*GitHub* : [192](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L192)


---

	 - contracts/L1/libs/LibVerifying.sol

```solidity
212	            if (numBlocksVerified > 0) {
```

*GitHub* : [212](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L212)


---

	 - contracts/L2/TaikoL2.sol

```solidity
262	        if (gasExcess > 0) {
...
275	            if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {
...
279	            if (numL1Blocks > 0) {
```

*GitHub* : [262](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L262), [275](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L275), [279](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L279)


---

	 - contracts/signal/SignalService.sol

```solidity
120	            bool isFullProof = hop.accountProof.length > 0;
```

*GitHub* : [120](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L120)


---

	 - contracts/thirdparty/optimism/rlp/RLPReader.sol

```solidity
38	            _in.length > 0,
...
153	            _in.length > 0,
```

*GitHub* : [38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L38), [153](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L153)


---

	 - contracts/thirdparty/optimism/trie/MerkleTrie.sol

```solidity
77	        require(_key.length > 0, "MerkleTrie: empty key");
```

*GitHub* : [77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L77), [173](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L173), [120](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L120)


---

	 - contracts/team/TimelockTokenPool.sol


*GitHub* : [277](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L277), [275](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L275)


---

	 - contracts/automata-attestation/lib/PEMCertChainLib.sol


*GitHub* : [56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L56)

### [G-40]<a name="g-40"></a> Delete Unused State Variables

State variables that aren't used in the contract not only clutter the codebase but also consume unnecessary gas during deployment.
Specifically, setting non-zero initial values for state variables costs significant gas.
By removing these unused state variables, you can save on both deployment gas and potential future storage gas costs.
This optimization not only reduces gas expenditures but also enhances code clarity and maintainability.
Always ensure a thorough review to confirm that these variables are indeed redundant before removal.

*There are 67 instance(s) of this issue:*


---

	 - contracts/common/AddressManager.sol

```solidity
14	    uint256[49] private __gap;
```

*GitHub* : [14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L14)


---

	 - contracts/common/AddressResolver.sol

```solidity
14	    uint256[49] private __gap;
...
19	    error RESOLVER_ZERO_ADDR(uint64 chainId, bytes32 name);
...
19	    error RESOLVER_ZERO_ADDR(uint64 chainId, bytes32 name);
```

*GitHub* : [14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L14), [19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L19), [19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L19)


---

	 - contracts/common/EssentialContract.sol

```solidity
17	    bytes32 private constant _REENTRY_SLOT =
18	        0xa5054f728453d3dbe953bdc43e4d0cb97e662ea32d7958190f3dc2da31d9721a;
...
25	    uint256[49] private __gap;
```

*GitHub* : [17..18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L17-L18), [25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L25)


---

	 - contracts/L1/gov/TaikoGovernor.sol

```solidity
23	    uint256[50] private __gap;
```

*GitHub* : [23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L23)


---

	 - contracts/L1/gov/TaikoTimelockController.sol

```solidity
10	    uint256[50] private __gap;
```

*GitHub* : [10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L10)


---

	 - contracts/L1/hooks/AssignmentHook.sol

```solidity
40	    uint256[50] private __gap;
```

*GitHub* : [40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L40)


---

	 - contracts/L1/provers/GuardianProver.sol

```solidity
11	    uint256[50] private __gap;
```

*GitHub* : [11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L11)


---

	 - contracts/L1/provers/Guardians.sol


*GitHub* : [32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L32)


---

	 - contracts/L1/TaikoL1.sol


*GitHub* : [26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L26)


---

	 - contracts/L1/TaikoToken.sol


*GitHub* : [16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L16)


---

	 - contracts/L1/tiers/DevnetTierProvider.sol


*GitHub* : [11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L11)


---

	 - contracts/L1/tiers/MainnetTierProvider.sol


*GitHub* : [11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L11)


---

	 - contracts/L1/tiers/TestnetTierProvider.sol


*GitHub* : [11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L11)


---

	 - contracts/L2/CrossChainOwned.sol


*GitHub* : [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L21)


---

	 - contracts/L2/TaikoL2.sol


*GitHub* : [52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L52), [226](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L226), [226](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L226)


---

	 - contracts/L2/TaikoL2EIP1559Configurable.sol


*GitHub* : [13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L13)


---

	 - contracts/signal/SignalService.sol


*GitHub* : [23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L23), [308](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L308), [306](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L306)


---

	 - contracts/bridge/Bridge.sol


*GitHub* : [23..24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L23-L24), [48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L48), [421](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L421), [421](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L421)


---

	 - contracts/tokenvault/adapters/USDCAdapter.sol


*GitHub* : [32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L32)


---

	 - contracts/tokenvault/BridgedERC20.sol


*GitHub* : [32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L32)


---

	 - contracts/tokenvault/BridgedERC20Base.sol


*GitHub* : [16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L16), [97](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L97), [97](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L97), [99](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L99), [99](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L99)


---

	 - contracts/tokenvault/BridgedERC721.sol


*GitHub* : [19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L19)


---

	 - contracts/tokenvault/BridgedERC1155.sol


*GitHub* : [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L27)


---

	 - contracts/tokenvault/BaseNFTVault.sol


*GitHub* : [13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L13), [15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L15), [17](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L17), [19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L19), [25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L25), [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L27), [29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L29), [37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L37), [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L39), [41](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L41), [43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L43), [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L47), [50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L50), [56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L56), [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L59), [61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L61)


---

	 - contracts/tokenvault/BaseVault.sol


*GitHub* : [18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L18)


---

	 - contracts/tokenvault/ERC1155Vault.sol


*GitHub* : [32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L32)


---

	 - contracts/tokenvault/ERC20Vault.sol


*GitHub* : [54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L54)


---

	 - contracts/tokenvault/ERC721Vault.sol


*GitHub* : [19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L19)


---

	 - contracts/verifiers/GuardianVerifier.sol


*GitHub* : [11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L11)


---

	 - contracts/verifiers/SgxVerifier.sol


*GitHub* : [57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L57)


---

	 - contracts/team/airdrop/ERC20Airdrop.sol


*GitHub* : [18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L18)


---

	 - contracts/team/airdrop/ERC20Airdrop2.sol


*GitHub* : [30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L30)


---

	 - contracts/team/airdrop/ERC721Airdrop.sol


*GitHub* : [16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L16)


---

	 - contracts/team/airdrop/MerkleClaimable.sol


*GitHub* : [23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L23)


---

	 - contracts/team/TimelockTokenPool.sol


*GitHub* : [82](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L82)


---

	 - contracts/automata-attestation/AutomataDcapV3Attestation.sol


*GitHub* : [130](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L130)


---

	 - contracts/automata-attestation/lib/PEMCertChainLib.sol


*GitHub* : [219](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L219)


---

	 - contracts/automata-attestation/utils/SigVerifyLib.sol


*GitHub* : [120](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L120)

### [G-41]<a name="g-41"></a> Optimize Gas by Using Only Named Returns

The Solidity compiler can generate more efficient bytecode when using named returns.
It's recommended to replace anonymous returns with named returns for potential gas savings.

Example:
```solidity
/// 985 gas cost
function add(uint256 x, uint256 y) public pure returns (uint256) {
  return x + y;
}
/// 941 gas cost
function addNamed(uint256 x, uint256 y) public pure returns (uint256 res) {
  res = x + y;
}
```

*There are 162 instance(s) of this issue:*


---

	 - contracts/common/IAddressManager.sol

```solidity
14	    function getAddress(uint64 _chainId, bytes32 _name) external view returns (address);
```

*GitHub* : [14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressManager.sol#L14)


---

	 - contracts/common/AddressManager.sol

```solidity
54	    function getAddress(uint64 _chainId, bytes32 _name) public view override returns (address) {
```

*GitHub* : [54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L54)


---

	 - contracts/common/IAddressResolver.sol

```solidity
19	    function resolve(
20	        bytes32 _name,
21	        bool _allowZeroAddress
22	    )
23	        external
24	        view
25	        returns (address payable);
...
34	    function resolve(
35	        uint64 _chainId,
36	        bytes32 _name,
37	        bool _allowZeroAddress
38	    )
39	        external
40	        view
41	        returns (address payable);
```

*GitHub* : [19..25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressResolver.sol#L19-L25), [34..41](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressResolver.sol#L34-L41)


---

	 - contracts/common/AddressResolver.sol

```solidity
30	    function resolve(
31	        bytes32 _name,
32	        bool _allowZeroAddress
33	    )
34	        public
35	        view
36	        virtual
37	        returns (address payable)
38	    {
...
43	    function resolve(
44	        uint64 _chainId,
45	        bytes32 _name,
46	        bool _allowZeroAddress
47	    )
48	        public
49	        view
50	        virtual
51	        returns (address payable)
52	    {
```

*GitHub* : [30..38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L30-L38), [43..52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L43-L52)


---

	 - contracts/common/EssentialContract.sol

```solidity
88	    function paused() public view returns (bool) {
...
140	    function _inNonReentrant() internal view returns (bool) {
```

*GitHub* : [88](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L88), [140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L140)


---

	 - contracts/libs/LibAddress.sol

```solidity
61	    function isValidSignature(
62	        address _addr,
63	        bytes32 _hash,
64	        bytes memory _sig
65	    )
66	        internal
67	        view
68	        returns (bool)
69	    {
...
77	    function isSenderEOA() internal view returns (bool) {
```

*GitHub* : [61..69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L61-L69), [77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L77)


---

	 - contracts/libs/LibMath.sol


*GitHub* : [12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibMath.sol#L12), [20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibMath.sol#L20)


---

	 - contracts/L1/gov/TaikoGovernor.sol


*GitHub* : [48..57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L48-L57), [69..80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L69-L80), [89..94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L89-L94), [99..104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L99-L104), [111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L111), [117](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L117), [123](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L123), [140..149](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L140-L149), [153..158](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L153-L158)


---

	 - contracts/L1/gov/TaikoTimelockController.sol


*GitHub* : [24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L24)


---

	 - contracts/L1/hooks/AssignmentHook.sol


*GitHub* : [137..145](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L137-L145), [164..171](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L164-L171)


---

	 - contracts/L1/ITaikoL1.sol


*GitHub* : [35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/ITaikoL1.sol#L35)


---

	 - contracts/L1/libs/LibDepositing.sol


*GitHub* : [122..130](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L122-L130), [149](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L149)


---

	 - contracts/L1/libs/LibProposing.sol


*GitHub* : [287..295](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L287-L295), [299..306](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L299-L306)


---

	 - contracts/L1/libs/LibUtils.sol


*GitHub* : [23..32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L23-L32)


---

	 - contracts/L1/libs/LibVerifying.sol


*GitHub* : [245](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L245)


---

	 - contracts/L1/provers/Guardians.sol


*GitHub* : [101](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L101), [107](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L107), [128](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L128)


---

	 - contracts/L1/TaikoL1.sol


*GitHub* : [132](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L132), [137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L137), [162..169](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L162-L169), [186](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L186)


---

	 - contracts/L1/TaikoToken.sol


*GitHub* : [60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L60), [70..78](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L70-L78)


---

	 - contracts/L1/tiers/ITierProvider.sol


*GitHub* : [22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L22), [28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L28), [33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L33)


---

	 - contracts/L1/tiers/DevnetTierProvider.sol


*GitHub* : [20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L20), [54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L54)


---

	 - contracts/L1/tiers/MainnetTierProvider.sol


*GitHub* : [20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L20), [66](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L66)


---

	 - contracts/L1/tiers/TestnetTierProvider.sol


*GitHub* : [20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L20), [66](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L66)


---

	 - contracts/L2/Lib1559Math.sol


*GitHub* : [16..23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L16-L23), [33..40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L33-L40)


---

	 - contracts/L2/TaikoL2.sol


*GitHub* : [200](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L200), [219](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L219)


---

	 - contracts/L2/TaikoL2EIP1559Configurable.sol


*GitHub* : [43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L43)


---

	 - contracts/signal/ISignalService.sol


*GitHub* : [96](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L96), [105..113](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L105-L113)


---

	 - contracts/signal/SignalService.sol


*GitHub* : [63](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L63), [68..76](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L68-L76), [137..147](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L137-L147), [153](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L153), [177..185](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L177-L185), [194..202](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L194-L202), [206..220](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L206-L220)


---

	 - contracts/bridge/IBridge.sol


*GitHub* : [150](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L150), [155](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L155)


---

	 - contracts/bridge/Bridge.sol


*GitHub* : [340](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L340), [352..359](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L352-L359), [374..381](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L374-L381), [449](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L449), [456](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L456), [555](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L555)


---

	 - contracts/tokenvault/adapters/USDCAdapter.sol


*GitHub* : [23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L23)


---

	 - contracts/tokenvault/BridgedERC20.sol


*GitHub* : [91..96](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L91-L96), [102..107](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L102-L107), [113..118](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L113-L118), [125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L125)


---

	 - contracts/tokenvault/BridgedERC20Base.sol


*GitHub* : [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L93), [101](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L101)


---

	 - contracts/tokenvault/BridgedERC721.sol


*GitHub* : [87](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L87), [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L93), [100](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L100), [107](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L107)


---

	 - contracts/tokenvault/BridgedERC1155.sol


*GitHub* : [115](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L115), [121](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L121)


---

	 - contracts/tokenvault/BaseVault.sol


*GitHub* : [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L39), [45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L45)


---

	 - contracts/tokenvault/ERC1155Vault.sol


*GitHub* : [18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L18), [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L21), [160..170](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L160-L170), [175..185](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L175-L185), [192..198](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L192-L198), [204](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L204)


---

	 - contracts/tokenvault/ERC20Vault.sol


*GitHub* : [316](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L316)


---

	 - contracts/tokenvault/ERC721Vault.sol


*GitHub* : [142..151](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L142-L151), [156](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L156)


---

	 - contracts/tokenvault/IBridgedERC20.sol


*GitHub* : [28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/IBridgedERC20.sol#L28)


---

	 - contracts/tokenvault/LibBridgedToken.sol


*GitHub* : [28..35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L28-L35), [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L39), [43..50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L43-L50)


---

	 - contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol


*GitHub* : [25..34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L25-L34)


---

	 - contracts/thirdparty/optimism/Bytes.sol


*GitHub* : [15..23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L15-L23), [91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L91), [102](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L102), [149](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L149)


---

	 - contracts/verifiers/SgxVerifier.sol


*GitHub* : [90..94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L90-L94), [118..121](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L118-L121), [171..180](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L171-L180), [233](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L233)


---

	 - contracts/team/airdrop/MerkleClaimable.sol


*GitHub* : [77..86](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L77-L86)


---

	 - contracts/team/TimelockTokenPool.sol


*GitHub* : [204](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L204), [235](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L235), [239](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L239), [245..254](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L245-L254)


---

	 - contracts/automata-attestation/AutomataDcapV3Attestation.sol


*GitHub* : [138](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L138), [162](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L162), [175..179](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L175-L179), [206..213](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L206-L213), [229..236](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L229-L236), [248..252](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L248-L252), [303..312](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L303-L312), [355..360](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L355-L360), [364..368](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L364-L368)


---

	 - contracts/automata-attestation/interfaces/IAttestation.sol


*GitHub* : [9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/interfaces/IAttestation.sol#L9)


---

	 - contracts/automata-attestation/interfaces/ISigVerifyLib.sol


*GitHub* : [38..46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L38-L46), [48..56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L48-L56)


---

	 - contracts/automata-attestation/utils/Asn1Decode.sol


*GitHub* : [14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L14), [19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L19), [24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L24), [29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L29), [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L47), [56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L56), [66](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L66), [77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L77), [87](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L87), [98](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L98), [111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L111), [121](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L121), [131](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L131), [141](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L141), [154](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L154), [165](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L165), [169](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L169), [179](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L179), [187](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L187)


---

	 - contracts/automata-attestation/utils/BytesUtils.sol


*GitHub* : [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L39), [56..67](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L56-L67), [116..126](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L116-L126), [138..147](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L138-L147), [160..168](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L160-L168), [178](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L178), [284..292](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L284-L292), [320..328](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L320-L328), [371](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L371)


---

	 - contracts/automata-attestation/utils/RsaVerify.sol


*GitHub* : [43..52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L43-L52), [191..200](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L191-L200), [212..221](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L212-L221), [307..316](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L307-L316)


---

	 - contracts/automata-attestation/utils/SigVerifyLib.sol


*GitHub* : [24..33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L24-L33), [54..63](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L54-L63)


---

	 - contracts/automata-attestation/utils/X509DateUtils.sol


*GitHub* : [8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L8), [34..45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L34-L45), [71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L71)

### [G-42]<a name="g-42"></a> Use assembly in place of `abi.decode` to extract `calldata` values more efficiently

Instead of using abi.decode, we can use assembly to decode our desired calldata values directly. This will allow us to avoid decoding calldata values that we will not use.
For more details on how to implement this, check the following [report](https://code4rena.com/reports/2023-05-juicebox#g-04-use-assembly-in-place-of-abidecode-to-extract-calldata-values-more-efficiently)

*There are 16 instance(s) of this issue:*


---

	 - contracts/L1/hooks/AssignmentHook.sol

```solidity
77	        Input memory input = abi.decode(_data, (Input));
```

*GitHub* : [77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L77)


---

	 - contracts/L1/libs/LibProposing.sol

```solidity
78	        TaikoData.BlockParams memory params = abi.decode(_data, (TaikoData.BlockParams));
```

*GitHub* : [78](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L78)


---

	 - contracts/L1/TaikoL1.sol

```solidity
88	        ) = abi.decode(_input, (TaikoData.BlockMetadata, TaikoData.Transition, TaikoData.TierProof));
```

*GitHub* : [88](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L88)


---

	 - contracts/L2/CrossChainOwned.sol

```solidity
42	        (uint64 txId, bytes memory txdata) = abi.decode(_data, (uint64, bytes));
```

*GitHub* : [42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L42)


---

	 - contracts/signal/SignalService.sol

```solidity
94	        HopProof[] memory hopProofs = abi.decode(_proof, (HopProof[]));
```

*GitHub* : [94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L94)


---

	 - contracts/tokenvault/ERC1155Vault.sol

```solidity
100	        ) = abi.decode(data, (CanonicalNFT, address, address, uint256[], uint256[]));
...
140	        (bytes memory data) = abi.decode(message.data[4:], (bytes));
...
142	            abi.decode(data, (CanonicalNFT, address, address, uint256[], uint256[]));
```

*GitHub* : [100](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L100), [140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L140), [142](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L142)


---

	 - contracts/tokenvault/ERC20Vault.sol

```solidity
260	            abi.decode(_data, (CanonicalERC20, address, address, uint256));
...
298	        (bytes memory data) = abi.decode(_message.data[4:], (bytes));
```

*GitHub* : [260](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L260), [298](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L298), [300](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L300)


---

	 - contracts/tokenvault/ERC721Vault.sol


*GitHub* : [84](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L84), [123](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L123), [125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L125)


---

	 - contracts/team/airdrop/ERC20Airdrop.sol


*GitHub* : [70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L70)


---

	 - contracts/automata-attestation/utils/SigVerifyLib.sol


*GitHub* : [140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L140)

### [G-43]<a name="g-43"></a> Optimize Address Storage Value Management with `assembly`



*There are 22 instance(s) of this issue:*


---

	 - contracts/common/AddressManager.sol

```solidity
49	        __addresses[_chainId][_name] = _newAddress;
```

*GitHub* : [49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L49)


---

	 - contracts/common/AddressResolver.sol

```solidity
62	        addressManager = _addressManager;
```

*GitHub* : [62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L62)


---

	 - contracts/tokenvault/BridgedERC20.sol

```solidity
73	        srcToken = _srcToken;
...
81	        snapshooter = _snapshooter;
```

*GitHub* : [73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L73), [81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L81)


---

	 - contracts/tokenvault/BridgedERC20Base.sol

```solidity
49	        migratingAddress = _migratingAddress;
```

*GitHub* : [49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L49)


---

	 - contracts/tokenvault/BridgedERC721.sol

```solidity
47	        srcToken = _srcToken;
```

*GitHub* : [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L47)


---

	 - contracts/tokenvault/BridgedERC1155.sol

```solidity
56	        srcToken = _srcToken;
```

*GitHub* : [56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L56)


---

	 - contracts/tokenvault/ERC1155Vault.sol

```solidity
312	        canonicalToBridged[_ctoken.chainId][_ctoken.addr] = btoken_;
```

*GitHub* : [312](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L312)


---

	 - contracts/tokenvault/ERC20Vault.sol

```solidity
189	        canonicalToBridged[_ctoken.chainId][_ctoken.addr] = _btokenNew;
...
423	        canonicalToBridged[ctoken.chainId][ctoken.addr] = btoken;
```

*GitHub* : [189](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L189), [423](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L423)


---

	 - contracts/tokenvault/ERC721Vault.sol


*GitHub* : [248](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L248)


---

	 - contracts/team/airdrop/ERC20Airdrop.sol


*GitHub* : [41](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L41), [42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L42)


---

	 - contracts/team/airdrop/ERC20Airdrop2.sol


*GitHub* : [69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L69), [70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L70)


---

	 - contracts/team/airdrop/ERC721Airdrop.sol


*GitHub* : [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L39), [40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L40)


---

	 - contracts/team/TimelockTokenPool.sol


*GitHub* : [122](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L122), [125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L125), [128](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L128)


---

	 - contracts/automata-attestation/AutomataDcapV3Attestation.sol


*GitHub* : [57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L57)


---

	 - contracts/automata-attestation/utils/SigVerifyLib.sol


*GitHub* : [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L21)

### [G-44]<a name="g-44"></a> Use calldata instead of memory for function arguments that do not get mutated

Mark data types as `calldata` instead of `memory` where possible. This makes it so that the data is not automatically loaded into memory. If the data passed into the function does not need to be changed (like updating values in an array), it can be passed in as `calldata`. The one exception to this is if the argument must later be passed into another function that takes an argument that specifies `memory` storage.

*There are 206 instance(s) of this issue:*


---

	 - contracts/libs/Lib4844.sol

```solidity
34	        bytes1[48] memory _commitment,
...
35	        bytes1[48] memory _pointProof
```

*GitHub* : [34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L34), [35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L35)


---

	 - contracts/libs/LibAddress.sol

```solidity
64	        bytes memory _sig
```

*GitHub* : [64](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L64)


---

	 - contracts/libs/LibTrieProof.sol

```solidity
39	        bytes[] memory _accountProof,
...
40	        bytes[] memory _storageProof
```

*GitHub* : [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L39), [40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L40)


---

	 - contracts/L1/gov/TaikoGovernor.sol

```solidity
49	        address[] memory _targets,
...
50	        uint256[] memory _values,
...
51	        bytes[] memory _calldatas,
...
52	        string memory _description
...
70	        address[] memory _targets,
```

*GitHub* : [49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L49), [50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L50), [51](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L51), [52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L52), [70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L70), [71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L71), [72](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L72), [73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L73), [74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L74), [129](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L129), [130](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L130), [131](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L131), [141](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L141), [142](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L142), [143](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L143)


---

	 - contracts/L1/hooks/AssignmentHook.sol


*GitHub* : [63](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L63), [64](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L64), [65](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L65), [138](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L138), [165](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L165)


---

	 - contracts/L1/libs/LibDepositing.sol


*GitHub* : [31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L31), [69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L69), [124](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L124)


---

	 - contracts/L1/libs/LibProposing.sol


*GitHub* : [70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L70), [289](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L289), [300](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L300)


---

	 - contracts/L1/libs/LibProving.sol


*GitHub* : [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L93), [95](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L95), [96](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L96), [97](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L97), [272](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L272), [352](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L352), [353](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L353), [354](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L354), [406](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L406)


---

	 - contracts/L1/libs/LibUtils.sol


*GitHub* : [25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L25), [54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L54)


---

	 - contracts/L1/libs/LibVerifying.sol


*GitHub* : [49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L49), [87](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L87), [225](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L225), [245](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L245)


---

	 - contracts/L1/provers/Guardians.sol


*GitHub* : [54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L54)


---

	 - contracts/L2/TaikoL2.sol


*GitHub* : [253](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L253)


---

	 - contracts/L2/TaikoL2EIP1559Configurable.sol


*GitHub* : [26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L26)


---

	 - contracts/signal/SignalService.sol


*GitHub* : [211](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L211), [272](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L272)


---

	 - contracts/bridge/Bridge.sol


*GitHub* : [449](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L449)


---

	 - contracts/tokenvault/BridgedERC20.sol


*GitHub* : [58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L58), [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L59)


---

	 - contracts/tokenvault/BridgedERC721.sol


*GitHub* : [36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L36), [37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L37)


---

	 - contracts/tokenvault/BridgedERC1155.sol


*GitHub* : [43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L43), [44](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L44), [85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L85), [86](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L86)


---

	 - contracts/tokenvault/ERC1155Vault.sol


*GitHub* : [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L39), [215](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L215), [217](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L217), [218](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L218), [242](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L242), [288](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L288), [303](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L303)


---

	 - contracts/tokenvault/ERC20Vault.sol


*GitHub* : [321](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L321), [391](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L391), [407](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L407)


---

	 - contracts/tokenvault/ERC721Vault.sol


*GitHub* : [26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L26), [161](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L161), [163](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L163), [189](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L189), [224](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L224), [240](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L240)


---

	 - contracts/tokenvault/LibBridgedToken.sol


*GitHub* : [14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L14), [15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L15), [29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L29), [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L39)


---

	 - contracts/thirdparty/optimism/Bytes.sol


*GitHub* : [16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L16), [91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L91), [149](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L149), [149](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L149)


---

	 - contracts/thirdparty/optimism/rlp/RLPReader.sol


*GitHub* : [35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L35), [53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L53), [102](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L102), [109](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L109), [128](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L128), [135](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L135), [144](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L144)


---

	 - contracts/thirdparty/optimism/rlp/RLPWriter.sol


*GitHub* : [13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L13)


---

	 - contracts/thirdparty/optimism/trie/MerkleTrie.sol


*GitHub* : [51](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L51), [52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L52), [53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L53), [69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L69), [70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L70), [205](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L205), [220](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L220), [227](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L227), [236](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L236), [237](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L237)


---

	 - contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol


*GitHub* : [20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L20), [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L21), [22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L22), [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L39), [40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L40), [54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L54)


---

	 - contracts/verifiers/SgxVerifier.sol


*GitHub* : [172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L172), [196](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L196)


---

	 - contracts/team/airdrop/MerkleClaimable.sol


*GitHub* : [67](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L67)


---

	 - contracts/team/TimelockTokenPool.sol


*GitHub* : [135](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L135), [168](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L168), [235](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L235), [239](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L239), [267](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L267)


---

	 - contracts/automata-attestation/AutomataDcapV3Attestation.sol


*GitHub* : [175](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L175), [207](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L207), [208](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L208), [230](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L230), [231](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L231), [248](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L248), [304](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L304), [305](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L305), [306](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L306), [307](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L307), [364](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L364)


---

	 - contracts/automata-attestation/lib/PEMCertChainLib.sol


*GitHub* : [41](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L41), [75](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L75), [216](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L216), [253](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L253), [270](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L270), [342](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L342)


---

	 - contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol


*GitHub* : [22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L22), [62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L62), [133](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L133), [152](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L152), [165](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L165), [204](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L204), [244](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L244), [268](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L268)


---

	 - contracts/automata-attestation/utils/Asn1Decode.sol


*GitHub* : [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L47), [56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L56), [66](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L66), [77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L77), [87](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L87), [111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L111), [121](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L121), [131](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L131), [141](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L141), [154](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L154), [165](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L165), [169](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L169), [179](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L179), [187](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L187)


---

	 - contracts/automata-attestation/utils/BytesUtils.sol


*GitHub* : [17](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L17), [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L39), [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L39), [117](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L117), [119](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L119), [139](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L139), [141](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L141), [161](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L161), [163](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L163), [178](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L178), [178](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L178), [188](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L188), [198](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L198), [211](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L211), [224](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L224), [237](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L237), [256](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L256), [285](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L285), [321](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L321), [371](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L371), [371](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L371)


---

	 - contracts/automata-attestation/utils/RsaVerify.sol


*GitHub* : [45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L45), [46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L46), [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L47), [192](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L192), [193](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L193), [194](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L194), [195](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L195), [214](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L214), [215](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L215), [216](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L216), [308](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L308), [309](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L309), [310](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L310), [311](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L311)


---

	 - contracts/automata-attestation/utils/SigVerifyLib.sol


*GitHub* : [25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L25), [26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L26), [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L27), [55](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L55), [56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L56), [57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L57), [80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L80), [81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L81), [82](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L82), [97](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L97), [98](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L98), [99](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L99), [114](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L114), [115](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L115), [116](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L116)


---

	 - contracts/automata-attestation/utils/X509DateUtils.sol


*GitHub* : [8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L8)

### [G-45]<a name="g-45"></a> Gas savings can be achieved by changing the model for assigning value to the structure

Change this `structName a = structName({item1: val1,item2: val2}); ==> structName a; a.item1 = val1; a.item2 = val2;`

*There are 31 instance(s) of this issue:*


---

	 - contracts/L1/libs/LibDepositing.sol

```solidity
51	            TaikoData.EthDeposit({
52	                recipient: recipient_,
53	                amount: uint96(msg.value),
54	                id: _state.slotA.numEthDeposits
55	            })
...
88	                deposits_[i] = TaikoData.EthDeposit({
89	                    recipient: address(uint160(data >> 96)),
90	                    amount: uint96(data),
91	                    id: j
92	                });
```

*GitHub* : [51..55](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L51-L55), [88..92](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L88-L92)


---

	 - contracts/L1/libs/LibProposing.sol

```solidity
121	            meta_ = TaikoData.BlockMetadata({
122	                l1Hash: blockhash(block.number - 1),
123	                difficulty: 0, // to be initialized below
124	                blobHash: 0, // to be initialized below
125	                extraData: params.extraData,
126	                depositsHash: keccak256(abi.encode(deposits_)),
127	                coinbase: params.coinbase,
128	                id: b.numBlocks,
129	                gasLimit: _config.blockMaxGasLimit,
130	                timestamp: uint64(block.timestamp),
131	                l1Height: uint64(block.number - 1),
132	                txListByteOffset: 0, // to be initialized below
133	                txListByteSize: 0, // to be initialized below
134	                minTier: 0, // to be initialized below
135	                blobUsed: _txList.length == 0,
136	                parentMetaHash: parentMetaHash
137	            });
...
212	        TaikoData.Block memory blk = TaikoData.Block({
213	            metaHash: keccak256(abi.encode(meta_)),
214	            // Safeguard the liveness bond to ensure its preservation,
215	            // particularly in scenarios where it might be altered after the
216	            // block's proposal but before it has been proven or verified.
217	            livenessBond: _config.livenessBond,
218	            blockId: b.numBlocks,
219	            proposedAt: meta_.timestamp,
220	            proposedIn: uint64(block.number),
221	            // For a new block, the next transition ID is always 1, not 0.
222	            nextTransitionId: 1,
223	            // For unverified block, its verifiedTransitionId is always 0.
224	            verifiedTransitionId: 0,
225	            assignedProver: params.assignedProver
226	        });
```

*GitHub* : [121..137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L121-L137), [212..226](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L212-L226)


---

	 - contracts/L1/libs/LibProving.sol

```solidity
166	                IVerifier.Context memory ctx = IVerifier.Context({
167	                    metaHash: blk.metaHash,
168	                    blobHash: _meta.blobHash,
169	                    // Separate msgSender to allow the prover to be any address in the future.
170	                    prover: msg.sender,
171	                    msgSender: msg.sender,
172	                    blockId: blk.blockId,
173	                    isContesting: isContesting,
174	                    blobUsed: _meta.blobUsed
175	                });
```

*GitHub* : [166..175](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L166-L175)


---

	 - contracts/L1/TaikoL1.sol

```solidity
191	        return TaikoData.Config({
192	            chainId: 167_008,
193	            // Assume the block time is 3s, the protocol will allow ~1 month of
194	            // new blocks without any verification.
195	            blockMaxProposals: 864_000,
196	            blockRingBufferSize: 864_100,
197	            // Can be overridden by the tier config.
198	            maxBlocksToVerifyPerProposal: 10,
199	            blockMaxGasLimit: 15_000_000,
200	            // Each go-ethereum transaction has a size limit of 128KB,
201	            // and right now txList is still saved in calldata, so we set it
202	            // to 120KB.
203	            blockMaxTxListBytes: 120_000,
204	            blobExpiry: 24 hours,
205	            blobAllowedForDA: false,
206	            blobReuseEnabled: false,
207	            livenessBond: 250e18, // 250 Taiko token
208	            // ETH deposit related.
209	            ethDepositRingBufferSize: 1024,
210	            ethDepositMinCountPerBlock: 8,
211	            ethDepositMaxCountPerBlock: 32,
212	            ethDepositMinAmount: 1 ether,
213	            ethDepositMaxAmount: 10_000 ether,
214	            ethDepositGas: 21_000,
215	            ethDepositMaxFee: 1 ether / 10,
216	            blockSyncThreshold: 16
217	        });
```

*GitHub* : [191..217](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L191-L217)


---

	 - contracts/L1/tiers/DevnetTierProvider.sol

```solidity
22	            return ITierProvider.Tier({
23	                verifierName: "tier_optimistic",
24	                validityBond: 250 ether, // TKO
25	                contestBond: 500 ether, // TKO
26	                cooldownWindow: 1440, //24 hours
27	                provingWindow: 120, // 2 hours
28	                maxBlocksToVerifyPerProof: 16
29	            });
...
33	            return ITierProvider.Tier({
34	                verifierName: "tier_guardian",
35	                validityBond: 0, // must be 0 for top tier
36	                contestBond: 0, // must be 0 for top tier
37	                cooldownWindow: 60, //1 hours
38	                provingWindow: 2880, // 48 hours
39	                maxBlocksToVerifyPerProof: 16
40	            });
```

*GitHub* : [22..29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L22-L29), [33..40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L33-L40)


---

	 - contracts/L1/tiers/MainnetTierProvider.sol

```solidity
22	            return ITierProvider.Tier({
23	                verifierName: "tier_sgx",
24	                validityBond: 250 ether, // TKO
25	                contestBond: 500 ether, // TKO
26	                cooldownWindow: 1440, //24 hours
27	                provingWindow: 60, // 1 hours
28	                maxBlocksToVerifyPerProof: 8
29	            });
...
33	            return ITierProvider.Tier({
34	                verifierName: "tier_sgx_zkvm",
35	                validityBond: 500 ether, // TKO
36	                contestBond: 1000 ether, // TKO
37	                cooldownWindow: 1440, //24 hours
38	                provingWindow: 240, // 4 hours
39	                maxBlocksToVerifyPerProof: 4
40	            });
```

*GitHub* : [22..29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L22-L29), [33..40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L33-L40), [44..51](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L44-L51)


---

	 - contracts/L1/tiers/TestnetTierProvider.sol


*GitHub* : [22..29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L22-L29), [33..40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L33-L40), [44..51](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L44-L51)


---

	 - contracts/bridge/Bridge.sol


*GitHub* : [243..246](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L243-L246), [549](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L549), [565](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L565)


---

	 - contracts/tokenvault/ERC1155Vault.sol


*GitHub* : [58..72](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L58-L72), [256..261](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L256-L261)


---

	 - contracts/tokenvault/ERC20Vault.sol


*GitHub* : [221..235](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L221-L235), [365..371](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L365-L371)


---

	 - contracts/tokenvault/ERC721Vault.sol


*GitHub* : [44..58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L44-L58), [203..208](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L203-L208)


---

	 - contracts/thirdparty/optimism/rlp/RLPReader.sol


*GitHub* : [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L47), [76..79](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L76-L79), [84..87](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L84-L87)


---

	 - contracts/thirdparty/optimism/trie/MerkleTrie.sol


*GitHub* : [209](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L209)


---

	 - contracts/verifiers/SgxVerifier.sol


*GitHub* : [217](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L217), [229](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L229)


---

	 - contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol


*GitHub* : [54..58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L54-L58), [190..198](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L190-L198)

### [G-46]<a name="g-46"></a> Use `Array.unsafeAccess` to avoid repeated array length checks

When using storage arrays, solidity adds an internal lookup of the array's length (a **Gcoldsload 2100 gas**) to ensure it doesn't read past the array's end.

It's possible to avoid this lookup by using `Array.unsafeAccess` in cases where the length has already been checked.

*There are 118 instance(s) of this issue:*


---

	 - contracts/common/AddressManager.sol

```solidity
38	    function setAddress(
39	        uint64 _chainId,
40	        bytes32 _name,
41	        address _newAddress
42	    )
43	        external
44	        virtual
45	        onlyOwner
46	    {
...
// @audit: array `__addresses[_chainId]` is accesed 2 times
47	        address oldAddress = __addresses[_chainId][_name];
...
// @audit: array `__addresses[_chainId]` is accesed 2 times
49	        __addresses[_chainId][_name] = _newAddress;
...
// @audit: array `__addresses[_chainId][_name]` is accesed 2 times
47	        address oldAddress = __addresses[_chainId][_name];
...
// @audit: array `__addresses[_chainId][_name]` is accesed 2 times
49	        __addresses[_chainId][_name] = _newAddress;
```

*GitHub* : [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L47), [49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L49), [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L47), [49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L49)


---

	 - contracts/L1/hooks/AssignmentHook.sol

```solidity
164	    function _getProverFee(
165	        TaikoData.TierFee[] memory _tierFees,
166	        uint16 _tierId
167	    )
168	        private
169	        pure
170	        returns (uint256)
171	    {
...
// @audit: array `_tierFees[i]` is accesed 2 times
173	            if (_tierFees[i].tier == _tierId) return _tierFees[i].fee;
...
// @audit: array `_tierFees[i]` is accesed 2 times
173	            if (_tierFees[i].tier == _tierId) return _tierFees[i].fee;
```

*GitHub* : [173](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L173), [173](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L173)


---

	 - contracts/L1/libs/LibDepositing.sol

```solidity
67	    function processDeposits(
68	        TaikoData.State storage _state,
69	        TaikoData.Config memory _config,
70	        address _feeRecipient
71	    )
72	        internal
73	        returns (TaikoData.EthDeposit[] memory deposits_)
74	    {
...
// @audit: array `deposits_[i]` is accesed 4 times
88	                deposits_[i] = TaikoData.EthDeposit({
```

*GitHub* : [88](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L88), [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L93), [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L93), [101](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L101)


---

	 - contracts/L1/libs/LibProposing.sol


*GitHub* : [245](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L245), [253](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L253), [254](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L254), [257](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L257)


---

	 - contracts/L1/libs/LibProving.sol


*GitHub* : [299](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L299), [345](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L345), [299](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L299), [345](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L345)


---

	 - contracts/L1/libs/LibVerifying.sol


*GitHub* : [104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L104), [130](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L130), [115](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L115), [140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L140), [115](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L115), [140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L140)


---

	 - contracts/L1/provers/Guardians.sol


*GitHub* : [84](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L84), [88](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L88), [116](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L116), [119](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L119), [116](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L116), [119](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L119)


---

	 - contracts/signal/SignalService.sol


*GitHub* : [57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L57), [58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L58), [247](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L247), [248](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L248), [247](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L247), [248](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L248)


---

	 - contracts/bridge/Bridge.sol


*GitHub* : [109](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L109), [110](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L110), [166](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L166), [191](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L191), [168](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L168), [184](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L184), [190](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L190), [230](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L230), [243](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L243), [250](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L250), [264](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L264), [516](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L516), [518](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L518)


---

	 - contracts/tokenvault/ERC1155Vault.sol


*GitHub* : [252](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L252), [273](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L273), [274](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L274), [252](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L252), [249](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L249), [250](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L250)


---

	 - contracts/tokenvault/ERC20Vault.sol


*GitHub* : [158](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L158), [180](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L180), [188](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L188), [168](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L168), [189](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L189), [168](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L168), [189](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L189), [358](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L358), [359](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L359)


---

	 - contracts/tokenvault/ERC721Vault.sol


*GitHub* : [171](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L171), [176](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L176), [198](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L198), [211](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L211), [195](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L195), [196](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L196)


---

	 - contracts/thirdparty/optimism/trie/MerkleTrie.sol


*GitHub* : [209](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L209), [209](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L209)


---

	 - contracts/verifiers/SgxVerifier.sol


*GitHub* : [107](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L107), [109](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L109), [111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L111), [211](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L211), [213](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L213), [211](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L211), [213](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L213), [215](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L215), [217](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L217), [220](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220), [235](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L235), [236](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L236), [237](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L237)


---

	 - contracts/team/airdrop/MerkleClaimable.sol


*GitHub* : [70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L70), [73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L73)


---

	 - contracts/team/TimelockTokenPool.sol


*GitHub* : [137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L137), [142](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L142)


---

	 - contracts/automata-attestation/AutomataDcapV3Attestation.sol


*GitHub* : [81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L81), [84](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L84), [81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L81), [84](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L84), [81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L81), [84](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L84), [96](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L96), [99](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L99), [96](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L96), [99](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L99), [96](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L96), [99](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L99), [268](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L268), [270](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L270), [271](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L271), [280](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L280), [280](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L280), [286](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L286), [286](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L286), [263](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L263)


---

	 - contracts/automata-attestation/lib/PEMCertChainLib.sol


*GitHub* : [132](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L132), [133](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L133), [189](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L189), [288](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L288), [303](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L303)


---

	 - contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol


*GitHub* : [282](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L282), [282](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L282)


---

	 - contracts/automata-attestation/utils/Asn1Decode.sol


*GitHub* : [156](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L156), [158](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L158)

### [G-47]<a name="g-47"></a> Consider using OpenZeppelin's `EnumerateSet` instead of nested mappings

Nested mappings and multi-dimensional arrays in Solidity operate through a process of double hashing, wherein the original storage slot and the first key are concatenated and hashed, and then this hash is again concatenated with the second key and hashed. This process can be quite gas expensive due to the double-hashing operation and subsequent storage operation (sstore).

OpenZeppelin's `EnumerableSet` provides a potential solution to this problem. It creates a data structure that combines the benefits of set operations with the ability to enumerate stored elements, which is not natively available in Solidity. EnumerableSet handles the element uniqueness internally and can therefore provide a more gas-efficient and collision-resistant alternative to nested mappings or multi-dimensional arrays in certain scenarios.

*There are 8 instance(s) of this issue:*


---

	 - contracts/common/AddressManager.sol

```solidity
12	    mapping(uint256 chainId => mapping(bytes32 name => address addr)) private __addresses;
```

*GitHub* : [12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L12)


---

	 - contracts/L1/provers/Guardians.sol

```solidity
19	    mapping(uint32 version => mapping(bytes32 hash => uint256 approvalBits)) internal _approvals;
```

*GitHub* : [19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L19)


---

	 - contracts/L1/TaikoData.sol

```solidity
183	        mapping(uint64 blockId => mapping(bytes32 parentHash => uint32 transitionId)) transitionIds;
...
185	        mapping(
186	            uint64 blockId_mod_blockRingBufferSize
187	                => mapping(uint32 transitionId => TransitionState ts)
188	            ) transitions;
```

*GitHub* : [183](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L183), [185..188](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L185-L188)


---

	 - contracts/signal/SignalService.sol

```solidity
17	    mapping(uint64 chainId => mapping(bytes32 kind => uint64 blockId)) public topBlockId;
```

*GitHub* : [17](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L17)


---

	 - contracts/tokenvault/BaseNFTVault.sol

```solidity
59	    mapping(uint256 chainId => mapping(address ctoken => address btoken)) public canonicalToBridged;
```

*GitHub* : [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L59)


---

	 - contracts/tokenvault/ERC20Vault.sol

```solidity
49	    mapping(uint256 chainId => mapping(address ctoken => address btoken)) public canonicalToBridged;
```

*GitHub* : [49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L49)


---

	 - contracts/automata-attestation/AutomataDcapV3Attestation.sol

```solidity
47	    mapping(uint256 idx => mapping(bytes serialNum => bool revoked)) private _serialNumIsRevoked;
```

*GitHub* : [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L47)

### [G-48]<a name="g-48"></a> Counting down in `for` statements is more gas efficient

Counting down is more gas efficient than counting up because neither we are making zero variable to non-zero variable and also we will get gas refund in the last transaction when making non-zero to zero variable. [More info](https://solodit.xyz/issues/g-02-counting-down-in-for-statements-is-more-gas-efficient-code4rena-pooltogether-pooltogether-git)

*There are 45 instance(s) of this issue:*


---

	 - contracts/L1/hooks/AssignmentHook.sol

```solidity
// @audit `i` is counter for the loop
172	        for (uint256 i; i < _tierFees.length; ++i) {
...
 // @audit increment is used for counter
172	        for (uint256 i; i < _tierFees.length; ++i) {
```

*GitHub* : [172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L172)


---

	 - contracts/L1/libs/LibDepositing.sol

```solidity
// @audit `i` is counter for the loop
86	            for (uint256 i; i < deposits_.length;) {
...
 // @audit increment is used for counter
103	                    ++i;
```

*GitHub* : [103](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L103)


---

	 - contracts/L1/libs/LibProposing.sol

```solidity
// @audit `i` is counter for the loop
244	            for (uint256 i; i < params.hookCalls.length; ++i) {
...
 // @audit increment is used for counter
244	            for (uint256 i; i < params.hookCalls.length; ++i) {
```

*GitHub* : [244](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L244)


---

	 - contracts/L1/provers/Guardians.sol

```solidity
// @audit `i` is counter for the loop
74	        for (uint256 i; i < guardians.length; ++i) {
...
 // @audit increment is used for counter
74	        for (uint256 i; i < guardians.length; ++i) {
...
// @audit `i` is counter for the loop
80	        for (uint256 i = 0; i < _newGuardians.length; ++i) {
...
 // @audit increment is used for counter
80	        for (uint256 i = 0; i < _newGuardians.length; ++i) {
```

*GitHub* : [74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L74), [80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L80), [133](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L133)


---

	 - contracts/L2/TaikoL2.sol


*GitHub* : [234](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L234)


---

	 - contracts/signal/SignalService.sol


*GitHub* : [104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L104)


---

	 - contracts/bridge/Bridge.sol


*GitHub* : [90](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L90)


---

	 - contracts/tokenvault/ERC1155Vault.sol


*GitHub* : [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L47), [269](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L269), [251](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L251)


---

	 - contracts/tokenvault/ERC721Vault.sol


*GitHub* : [34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L34), [175](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L175), [170](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L170), [210](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L210), [197](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L197)


---

	 - contracts/thirdparty/optimism/rlp/RLPWriter.sol


*GitHub* : [66](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66)


---

	 - contracts/thirdparty/optimism/trie/MerkleTrie.sol


*GitHub* : [85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85), [211](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L211)


---

	 - contracts/verifiers/SgxVerifier.sol


*GitHub* : [104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L104), [210](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210)


---

	 - contracts/team/airdrop/ERC721Airdrop.sol


*GitHub* : [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59)


---

	 - contracts/automata-attestation/AutomataDcapV3Attestation.sol


*GitHub* : [80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L80), [95](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L95), [191](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L191), [214](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L214), [240](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L240), [259](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L259), [420](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L420)


---

	 - contracts/automata-attestation/lib/PEMCertChainLib.sol


*GitHub* : [54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L54), [244](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L244), [354](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L354)


---

	 - contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol


*GitHub* : [153](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L153), [281](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L281)


---

	 - contracts/automata-attestation/utils/BytesUtils.sol


*GitHub* : [333](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L333)


---

	 - contracts/automata-attestation/utils/RsaVerify.sol


*GitHub* : [140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L140), [158](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L158), [152](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L152), [174](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L174), [273](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L273), [283](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L283), [290](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L290)


---

	 - contracts/automata-attestation/utils/X509DateUtils.sol


*GitHub* : [48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L48), [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L59)

### [G-49]<a name="g-49"></a> Do not calculate constants

Due to how constant variables are implemented (replacements at compile-time), an expression assigned to a constant variable is recomputed each time that the variable is used, which wastes some gas.

*There are 2 instance(s) of this issue:*


---

	 - contracts/L1/libs/LibProposing.sol

```solidity
21	    uint256 public constant MAX_BYTES_PER_BLOB = 4096 * 32;
```

*GitHub* : [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L21)


---

	 - contracts/thirdparty/optimism/trie/MerkleTrie.sol

```solidity
24	    uint256 internal constant BRANCH_NODE_LENGTH = TREE_RADIX + 1;
```

*GitHub* : [24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L24)


The rule itself is correct. But here are the cases in which SemVer allows you to use version up to `0.8.20`

*There are 81 instance(s) of this issue:*


---

	 - contracts/common/IAddressManager.sol

```solidity
2	pragma solidity 0.8.24;
```

*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressManager.sol#L2)


---

	 - contracts/common/AddressManager.sol

```solidity
2	pragma solidity 0.8.24;
```

*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L2)


---

	 - contracts/common/IAddressResolver.sol

```solidity
2	pragma solidity 0.8.24;
```

*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressResolver.sol#L2)


---

	 - contracts/common/AddressResolver.sol

```solidity
2	pragma solidity 0.8.24;
```

*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L2)


---

	 - contracts/common/EssentialContract.sol

```solidity
2	pragma solidity 0.8.24;
```

*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L2)


---

	 - contracts/libs/Lib4844.sol

```solidity
2	pragma solidity 0.8.24;
```

*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L2)


---

	 - contracts/libs/LibAddress.sol

```solidity
2	pragma solidity 0.8.24;
```

*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L2)


---

	 - contracts/libs/LibMath.sol

```solidity
2	pragma solidity 0.8.24;
```

*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibMath.sol#L2)


---

	 - contracts/libs/LibTrieProof.sol

```solidity
7	pragma solidity 0.8.24;
```

*GitHub* : [7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L7)


---

	 - contracts/L1/gov/TaikoGovernor.sol

```solidity
2	pragma solidity 0.8.24;
```

*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L2)


---

	 - contracts/L1/gov/TaikoTimelockController.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L2)


---

	 - contracts/L1/hooks/IHook.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/IHook.sol#L2)


---

	 - contracts/L1/hooks/AssignmentHook.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L2)


---

	 - contracts/L1/ITaikoL1.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/ITaikoL1.sol#L2)


---

	 - contracts/L1/libs/LibDepositing.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L2)


---

	 - contracts/L1/libs/LibProposing.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L2)


---

	 - contracts/L1/libs/LibProving.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L2)


---

	 - contracts/L1/libs/LibUtils.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L2)


---

	 - contracts/L1/libs/LibVerifying.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L2)


---

	 - contracts/L1/provers/GuardianProver.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L2)


---

	 - contracts/L1/provers/Guardians.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L2)


---

	 - contracts/L1/TaikoData.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L2)


---

	 - contracts/L1/TaikoErrors.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoErrors.sol#L2)


---

	 - contracts/L1/TaikoEvents.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L2)


---

	 - contracts/L1/TaikoL1.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L2)


---

	 - contracts/L1/TaikoToken.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L2)


---

	 - contracts/L1/tiers/ITierProvider.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L2)


---

	 - contracts/L1/tiers/DevnetTierProvider.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L2)


---

	 - contracts/L1/tiers/MainnetTierProvider.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L2)


---

	 - contracts/L1/tiers/TestnetTierProvider.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L2)


---

	 - contracts/L2/CrossChainOwned.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L2)


---

	 - contracts/L2/Lib1559Math.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L2)


---

	 - contracts/L2/TaikoL2.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L2)


---

	 - contracts/L2/TaikoL2EIP1559Configurable.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L2)


---

	 - contracts/signal/ISignalService.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L2)


---

	 - contracts/signal/LibSignals.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/LibSignals.sol#L2)


---

	 - contracts/signal/SignalService.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L2)


---

	 - contracts/bridge/IBridge.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L2)


---

	 - contracts/bridge/Bridge.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L2)


---

	 - contracts/tokenvault/adapters/USDCAdapter.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L2)


---

	 - contracts/tokenvault/BridgedERC20.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L2)


---

	 - contracts/tokenvault/BridgedERC20Base.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L2)


---

	 - contracts/tokenvault/BridgedERC721.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L2)


---

	 - contracts/tokenvault/BridgedERC1155.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L2)


---

	 - contracts/tokenvault/BaseNFTVault.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L2)


---

	 - contracts/tokenvault/BaseVault.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L2)


---

	 - contracts/tokenvault/ERC1155Vault.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L2)


---

	 - contracts/tokenvault/ERC20Vault.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L2)


---

	 - contracts/tokenvault/ERC721Vault.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L2)


---

	 - contracts/tokenvault/IBridgedERC20.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/IBridgedERC20.sol#L2)


---

	 - contracts/tokenvault/LibBridgedToken.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L2)


---

	 - contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol


*GitHub* : [3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L3)


---

	 - contracts/thirdparty/optimism/Bytes.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L2)


---

	 - contracts/thirdparty/optimism/rlp/RLPReader.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L2)


---

	 - contracts/thirdparty/optimism/rlp/RLPWriter.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L2)


---

	 - contracts/thirdparty/optimism/trie/MerkleTrie.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L2)


---

	 - contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L2)


---

	 - contracts/thirdparty/solmate/LibFixedPointMath.sol


*GitHub* : [4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L4)


---

	 - contracts/verifiers/IVerifier.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/IVerifier.sol#L2)


---

	 - contracts/verifiers/GuardianVerifier.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L2)


---

	 - contracts/verifiers/SgxVerifier.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L2)


---

	 - contracts/team/airdrop/ERC20Airdrop.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L2)


---

	 - contracts/team/airdrop/ERC20Airdrop2.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L2)


---

	 - contracts/team/airdrop/ERC721Airdrop.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L2)


---

	 - contracts/team/airdrop/MerkleClaimable.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L2)


---

	 - contracts/team/TimelockTokenPool.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L2)


---

	 - contracts/automata-attestation/AutomataDcapV3Attestation.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L2)


---

	 - contracts/automata-attestation/interfaces/IAttestation.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/interfaces/IAttestation.sol#L2)


---

	 - contracts/automata-attestation/interfaces/ISigVerifyLib.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L2)


---

	 - contracts/automata-attestation/lib/EnclaveIdStruct.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/EnclaveIdStruct.sol#L2)


---

	 - contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L2)


---

	 - contracts/automata-attestation/lib/PEMCertChainLib.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L2)


---

	 - contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L2)


---

	 - contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L2)


---

	 - contracts/automata-attestation/lib/TCBInfoStruct.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol#L2)


---

	 - contracts/automata-attestation/utils/Asn1Decode.sol


*GitHub* : [3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L3)


---

	 - contracts/automata-attestation/utils/BytesUtils.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L2)


---

	 - contracts/automata-attestation/utils/RsaVerify.sol


*GitHub* : [3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L3)


---

	 - contracts/automata-attestation/utils/SHA1.sol


*GitHub* : [3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SHA1.sol#L3)


---

	 - contracts/automata-attestation/utils/SigVerifyLib.sol


*GitHub* : [2](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L2)


---

	 - contracts/automata-attestation/utils/X509DateUtils.sol


*GitHub* : [3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L3)