## Gas Findings

|    | Issue | Instances | Total Gas Saved |
|----|-------|:---------:|:---------:|
| [G-01] | Structs can be packed into fewer storage slots | 3 | 60000 |
| [G-02] | State variables can be packed into fewer storage slots | 2 | 40000 |
| [G-03] | Optimize Storage Layout in Structs by Truncating Time Related Fields | 1 | 20000 |
| [G-04] | A `memory` array's `length` should not be looked up in every iteration of a `for`/`while`-loop | 29 | 87 |
| [G-05] | `do`-`while` is cheaper than `for`-loops when the initial check can be skipped | 49 | 12495 |
| [G-06] | Use `assembly` for Efficient Event Emission | 55 | 20900 |
| [G-07] | Use custom errors rather than `require()/assert()/revert(with msg)` with string to save gas | 70 | 3500 |
| [G-08] | Avoid Emitting Events Inside Loops | 4 | 1600 |
| [G-09] | Enable IR-based code generation | 81 | - |
| [G-10] | Assembly: Check `msg.sender` using xor and the scratch space | 22 | 462 |
| [G-11] | Assembly: Use scratch space for building calldata | 1 | 220 |
| [G-12] | Multiple `address`/ID mappings can be combined into a single `mapping` of an `address`/ID to a `struct` | 8 | - |
| [G-13] | Assigning `state` variables directly with struct constructors wastes gas | 4 | 284 |
| [G-14] | Assembly: Use scratch space when building emitted events with two data arguments | 9 | 135 |
| [G-15] | Stack variable is only used once | 124 | 372 |
| [G-16] | `abi.encodePacked `is more gas efficient than `abi.encode` | 18 | 3600 |
| [G-17] | Consider Using `selfbalance()` Over `address(this).balance` | 6 | - |
| [G-18] | Using `require()` instead of `assert()` safes gas | 4 | 132 |
| [G-19] | Use `assembly` to write mutable storage values | 81 | 891 |
| [G-20] | Using `delete` on a `uint/int` variable is cheaper than assigning it to `0` | 10 | 80 |
| [G-21] | Optimize Ether Transfers with `receive()` Function | 14 | 630 |
| [G-22] | Use `revert()` to gain maximum gas savings | 244 | 12200 |
| [G-23] | Use local variables for emitting | 5 | 500 |
| [G-24] | `x.a = x.a + b` always cheaper than `x.a += b` for Structs | 5 | 25 |
| [G-25] | Initializers can be marked as payable | 25 | - |
| [G-26] | Using `constants` instead of `enum` can save gas | 9 | 0 |
| [G-27] | Merging Sequential `for` Loops with Identical Conditions | 8 | 6800 |
| [G-28] | Create variable outside the loop | 57 | 1140 |
| [G-29] | Use `assembly` in place of `abi.decode` to extract calldata values more efficiently | 3 | 30 |
| [G-30] | Redundant state variable getters | 1 | 0 |
| [G-31] | Shorten the array rather than copying to a new on | 12 | 0 |
| [G-32] | Nested for loops should be avoided due to high gas costs resulting from O^2 time complexity | 1 | 0 |
| [G-33] | Use bytes32 in place of string | 9 | 0 |
| [G-34] | Using `delete` on a `bool` variable is cheaper than assigning it to `false` | 2 | 48 |
| [G-35] | Use `Array.unsafeAccess()` to avoid repeated array length checks | 29 | 60900 |
| [G-36] | Counting down when iterating, saves gas | 45 | 405 |
| [G-37] | `>=` costs less gas than `>` | 15 | 90 |
| [G-38] | Consider pre-calculating the address of `address(this)` to save gas | 40 | 0 |
| [G-39] | Call `msg.sender` directly instead of caching it | 1 | 14 |
| [G-40] | Use `unchecked` for Non-Loop Increment/Decrement Operations | 13 | 390 |
| [G-41] | Using `this` to access functions results in an external call, wasting gas | 10 | 1000 |
| [G-42] | Constructors can be marked `payable` | 3 | 72 |
| [G-43] | Split `revert` checks to save gas | 26 | - |
| [G-44] | Multiple accesses of a mapping/array should use a local variable cache | 25 | 3700 |
| [G-45] | Reduce deployment costs by tweaking contracts' metadata | 81 | 858600 |
| [G-46] | Use Pre-Increment/Decrement (++i/--i) to Save Gas | 14 | 70 |
| [G-47] | Nesting `if`-statements is cheaper than using `&&` | 19 | 114 |
| [G-48] | Use `storage` instead of `memory` for state structs/arrays | 28 | 58800 |
| [G-49] | Optimize by Using Assembly for Low-Level Calls' Return Data | 1 | 159 |
| [G-50] | Avoid transferring amounts of zero in order to save gas | 18 | 1800 |
| [G-51] | Cache Function Calls for Efficiency | 54 | - |
| [G-52] | Superfluous Event Fields | 1 | 34 |
| [G-53] | Unutilized Named Return Variables Waste Gas Without Optimizer | 22 | - |
| [G-54] | Use `unchecked` for Math Operations if they already checked | 17 | 1445 |
| [G-55] | Using `private` rather than `public`, saves gas | 86 | 1892000 |
| [G-56] | Use Assembly for Hash Calculations | 25 | 25125 |
| [G-57] | Consider using ERC721A instead of ERC721 | 3 | - |
| [G-58] | Refactor duplicated require()/revert() checks to save gas | 14 | - |
| [G-59] | Use Assembly for Efficient Memory Management in Multiple External Calls | 6 | 18000 |
| [G-60] | Optimize `require/revert` Statements with Assembly | 56 | 16800 |
| [G-61] | Cached Global Variables | 1 | 12 |
| [G-62] | Simple checks for zero `uint` can be done using `assembly` to save gas | 91 | 364 |
| [G-63] | Use Cached Contracts for Multiple External Calls | 2 | 336 |
| [G-64] | Consider using solady's `FixedPointMathLib` | 73 | - |
| [G-65] | Avoid Zero to Non-Zero Storage Writes Where Possible | 23 | 508300 |
| [G-66] | Consider Packing Small `uint` When it's Possible | 15 | 312000 |
| [G-67] | Consider Using `calldata` Instead of `memory` for Function Parameters | 9 | 2700 |
| [G-68] | Avoid Unnecessary Gas Usage with Shorter `require()/revert()` Strings | 30 | 540 |
| [G-69] | Use `unchecked` for division which do not divide by -X sonce they can't overflow | 14 | 280 |
| [G-70] | State Variables Should Be `immutable` Since They Are Only Set in the Constructor | 2 | 4200 |
| [G-71] | Use solady library where possible to save gas | 54 | 54000 |
| [G-72] | Avoid Inverting `if`-`else` Conditions | 1 | 3 |
| [G-73] | Use `uint256(1)`/`uint256(2)` instead of `true`/`false` to save gas for changes | 10 | 170000 |
| [G-74] | Use Bit Shifting for Multiplication by Powers of Two | 4 | 80 |
| [G-75] | Keep Strings Smaller Than 32 Bytes for Storage Efficiency | 2 | 40000 |
| [G-76] | Use Multiple `require()` Statements Instead of chaining | 4 | 12 |
| [G-77] | Delete Unused State Variables | 1 | 20000 |
| [G-78] | Consider Using Mappings Instead of Arrays to Save Gas | 1 | 2102 |
| [G-79] | Mark Functions That Revert For Normal Users As `payable` | 45 | 945 |
| [G-80] | Prefer `private` over `public` for Constants to Save Gas | 23 | 69000 |
| [G-81] | `<x> += <y>` costs more gas than `<x> = <x> + <y>` for state variables | 4 | 452 |
| [G-82] | Using `bool`s for storage incurs overhead | 10 | 1000 |
| [G-83] | Optimize Gas by Using Only Named Returns | 162 | 7128 |
| [G-84] | Cache State Variable Reads Outside Loops | 7 | 1855 |
| [G-85] | Usage of `uints`/`ints` smaller than 32 bytes (256 bits) incurs overhead | 237 | 1422 |
| [G-86] | Unlimited gas consumption risk due to external call recipients | 1 | - |
| [G-87] | Use assembly to check for `address(0)` | 43 | 2494 |
| [G-88] | `internal`/`private` functions only called once can be inlined to save gas | 69 | 1380 |
| [G-89] | Inefficient Use of String Constants | 7 | 2646 |
| [G-90] | Consider using OZ EnumerateSet in place of nested mappings | 8 | 8000 |
| [G-91] | Declare `immutable` as `private` to save gas | 2 | 6000 |
| [G-92] | State variables should be cached in stack rather than re-reading them from storage | 46 | 6111 |
| [G-93] | Division by powers of two should use bit shifting | 2 | 40 |
| [G-94] | Optimize names to save gas | 71 | 1420 |
| [G-95] | Avoid updating storage when the value hasn't changed | 13 | 10400 |
| [G-96] | Optimize External Calls with Assembly for Memory Efficiency | 31 | 6820 |

Total: 2746 instances of 96 issues with 4367691 gas saved

## Gas Findings Details

### [G-01] Structs can be packed into fewer storage slots

Each slot saved can avoid an extra Gsset (20000 gas) for the first setting of the struct. Subsequent reads as well as writes have smaller gas savings.

<details>
<summary><i>3 issue instances in 2 files:</i></summary>

```solidity
File: packages/protocol/contracts/L1/TaikoData.sol

/// @audit - Struct used 8 storage slots, but can be packed to 6 storage slots.
//	struct Config {
//	    uint256 ethDepositMaxFee;
//	    uint256 ethDepositGas;
//	    uint256 ethDepositRingBufferSize;
//	    uint96 ethDepositMaxAmount;
//	    uint96 ethDepositMinAmount;
//	    uint64 ethDepositMaxCountPerBlock;
//	    uint96 livenessBond;
//	    uint64 ethDepositMinCountPerBlock;
//	    uint64 maxBlocksToVerifyPerProposal;
//	    uint32 blockMaxGasLimit;
//	    uint64 blockRingBufferSize;
//	    uint64 blockMaxProposals;
//	    uint64 chainId;
//	    uint24 blobExpiry;
//	    uint24 blockMaxTxListBytes;
//	    uint8 blockSyncThreshold;
//	    bool blobReuseEnabled;
//	    bool blobAllowedForDA;
//	}
10: struct Config {
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
/// @audit - Struct used 7 storage slots, but can be packed to 6 storage slots.
//	struct BlockParams {
//	    HookCall[] hookCalls;
//	    bytes32 parentMetaHash;
//	    bytes32 blobHash;
//	    bytes32 extraData;
//	    address coinbase;
//	    uint24 txListByteSize;
//	    uint24 txListByteOffset;
//	    bool cacheBlobForReuse;
//	    address assignedProver;
//	}
78: struct BlockParams {
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
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L10) | [78](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L78)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol

/// @audit - Struct used 10 storage slots, but can be packed to 9 storage slots.
//	struct EnclaveReport {
//	    bytes reportData;
//	    bytes reserved4;
//	    bytes reserved3;
//	    bytes32 mrSigner;
//	    bytes32 reserved2;
//	    bytes32 mrEnclave;
//	    bytes28 reserved1;
//	    bytes4 miscSelect;
//	    bytes16 attributes;
//	    bytes16 cpuSvn;
//	    uint16 isvSvn;
//	    uint16 isvProdId;
//	}
17: struct EnclaveReport {
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
[17](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L17)
</details>

### [G-02] State variables can be packed into fewer storage slots

Each slot saved can avoid an extra Gsset (20000 gas). Reads and writes (if two variables that occupy the same slot are written by the same function) will have a cheaper gas consumption.

<details>
<summary><i>2 issue instances in 2 files:</i></summary>

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

/// @audit - State variables use 6 storage slots, but can be packed to 5 storage slots.
//	uint256[45] private __gap
//	mapping(address addr => uint256 amountWithdrawn) public withdrawnAmount
//	mapping(address addr => uint256 amountClaimed) public claimedAmount
//	address public vault
//	uint64 public withdrawalWindow
//	address public token

12: contract ERC20Airdrop2 is MerkleClaimable
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L12)

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

/// @audit - State variables use 7 storage slots, but can be packed to 6 storage slots.
//	EnclaveIdStruct.EnclaveId public qeIdentity
//	mapping(string fmspc => TCBInfoStruct.TCBInfo tcbInfo) public tcbInfo
//	mapping(uint256 idx => mapping(bytes serialNum => bool revoked)) private _serialNumIsRevoked
//	mapping(bytes32 signer => bool trusted) private _trustedUserMrSigner
//	mapping(bytes32 enclave => bool trusted) private _trustedUserMrEnclave
//	address public owner
//	bool private _checkLocalEnclaveReport

22: contract AutomataDcapV3Attestation is IAttestation
```
[22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L22)
</details>

### [G-03] Optimize Storage Layout in Structs by Truncating Time Related Fields

The field ordering within the following structs isn't optimized for efficient storage in the Ethereum Virtual Machine (EVM). By appropriately rearranging the fields within these structs, you can achieve improved gas efficiency during interactions with these structs. 

In the context of EVM, a well-structured and optimized struct can save a substantial amount of gas. For instance, packing the struct into fewer storage slots could avoid an extra SSTORE operation (costing 20000 gas) during the first setting of the struct. Subsequent read and write operations also experience reduced gas consumption due to optimized struct layout.

Please consider rearranging the fields in the identified structs to capitalize on these potential gas savings and improve overall contract performance.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

/// @audit - Packed struct used 3 storage slots, but can be packed to 2 storage slots.
//	struct Grant {
//	    uint128 costPerToken;
//	    uint128 amount;
//	    uint64 unlockCliff;
//	    uint64 grantCliff;
//	    uint32 unlockPeriod;
//	    uint32 unlockStart;
//	    uint32 grantPeriod;
//	    uint32 grantStart;
//	}
28: struct Grant {
        uint128 amount;
        // If non-zero, each TKO (1E18) will need some USD stable to purchase.
        uint128 costPerToken;
        // If non-zero, indicates the start time for the recipient to receive
        // tokens, subject to an unlocking schedule.
        uint64 grantStart;
        // If non-zero, indicates the time after which the token to be received
        // will be actually non-zero
        uint64 grantCliff;
        // If non-zero, specifies the total seconds required for the recipient
        // to fully own all granted tokens.
        uint32 grantPeriod;
        // If non-zero, indicates the start time for the recipient to unlock
        // tokens.
        uint64 unlockStart;
        // If non-zero, indicates the time after which the unlock will be
        // actually non-zero
        uint64 unlockCliff;
        // If non-zero, specifies the total seconds required for the recipient
        // to fully unlock all owned tokens.
        uint32 unlockPeriod;
    }
```
[28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L28)
</details>

### [G-04] A `memory` array's `length` should not be looked up in every iteration of a `for`/`while`-loop

It is more efficient to cache the array length instead of looking it up in every iteration of a for-loop.

Example:

```solidity
- for(uint i = 0; i < array.length; i++)
+ uint length = array.length;
+ for(uint i = 0; i < length; i++);
```

<details>
<summary><i>29 issue instances in 16 files:</i></summary>

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

172: for (uint256 i; i < _tierFees.length; ++i) {
```
[172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L172)

```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

86: for (uint256 i; i < deposits_.length;) {
```
[86](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L86)

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

244: for (uint256 i; i < params.hookCalls.length; ++i) {
```
[244](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L244)

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

74: for (uint256 i; i < guardians.length; ++i) {
80: for (uint256 i = 0; i < _newGuardians.length; ++i) {
```
[74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L74) | [80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L80)

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

104: for (uint256 i; i < hopProofs.length; ++i) {
```
[104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L104)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

90: for (uint256 i; i < _msgHashes.length; ++i) {
```
[90](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L90)

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

47: for (uint256 i; i < _op.amounts.length; ++i) {
251: for (uint256 i; i < _op.tokenIds.length; ++i) {
269: for (uint256 i; i < _op.tokenIds.length; ++i) {
```
[47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L47) | [251](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L251) | [269](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L269)

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

34: for (uint256 i; i < _op.tokenIds.length; ++i) {
170: for (uint256 i; i < _tokenIds.length; ++i) {
175: for (uint256 i; i < _tokenIds.length; ++i) {
197: for (uint256 i; i < _op.tokenIds.length; ++i) {
210: for (uint256 i; i < _op.tokenIds.length; ++i) {
```
[34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L34) | [170](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L170) | [175](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L175) | [197](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L197) | [210](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L210)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

66: for (uint256 j = 0; j < out_.length; j++) {
```
[66](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

85: for (uint256 i = 0; i < proof.length; i++) {
```
[85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

104: for (uint256 i; i < _ids.length; ++i) {
210: for (uint256 i; i < _instances.length; ++i) {
```
[104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L104) | [210](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

59: for (uint256 i; i < tokenIds.length; ++i) {
```
[59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59)

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

80: for (uint256 i; i < serialNumBatch.length; ++i) {
95: for (uint256 i; i < serialNumBatch.length; ++i) {
191: for (uint256 i; i < enclaveId.tcbLevels.length; ++i) {
214: for (uint256 i; i < tcb.tcbLevels.length; ++i) {
```
[80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L80) | [95](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L95) | [191](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L191) | [214](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L214)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

244: for (uint256 i; i < split.length; ++i) {
```
[244](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L244)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

153: for (uint256 i; i < encoded.length; ++i) {
```
[153](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L153)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

174: for (uint256 i; i < _sha256.length; ++i) {
283: for (uint256 i; i < sha1Prefix.length; ++i) {
290: for (uint256 i; i < _sha1.length; ++i) {
```
[174](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L174) | [283](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L283) | [290](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L290)
</details>

### [G-05] `do`-`while` is cheaper than `for`-loops when the initial check can be skipped

Using `do-while` loops instead of `for` loops can be more gas-efficient. 
Even if you add an `if` condition to account for the case where the loop doesn't execute at all, a `do-while` loop can still be cheaper in terms of gas.

Example:
```solidity
/// 774 gas cost
function forLoop() public pure {
    for (uint256 i; i < 10;) {
        unchecked {
            ++i;
        }
    }
}
/// 519 gas cost
function doWhileLoop() public pure {
    uint256 i;
    do {
        unchecked {
            ++i;
        }
    } while (i < 10);
}
```

<details>
<summary><i>49 issue instances in 19 files:</i></summary>

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

172: for (uint256 i; i < _tierFees.length; ++i)
```
[172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L172)

```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

86: for (uint256 i; i < deposits_.length;)
```
[86](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L86)

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

244: for (uint256 i; i < params.hookCalls.length; ++i)
```
[244](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L244)

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

74: for (uint256 i; i < guardians.length; ++i)
80: for (uint256 i = 0; i < _newGuardians.length; ++i)
133: for (uint256 i; i < guardiansLength; ++i)
```
[74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L74) | [80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L80) | [133](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L133)

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

234: for (uint256 i; i < 255 && _blockId >= i + 1; ++i)
```
[234](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L234)

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

104: for (uint256 i; i < hopProofs.length; ++i)
```
[104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L104)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

90: for (uint256 i; i < _msgHashes.length; ++i)
```
[90](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L90)

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

47: for (uint256 i; i < _op.amounts.length; ++i)
251: for (uint256 i; i < _op.tokenIds.length; ++i)
269: for (uint256 i; i < _op.tokenIds.length; ++i)
```
[47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L47) | [251](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L251) | [269](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L269)

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

34: for (uint256 i; i < _op.tokenIds.length; ++i)
170: for (uint256 i; i < _tokenIds.length; ++i)
175: for (uint256 i; i < _tokenIds.length; ++i)
197: for (uint256 i; i < _op.tokenIds.length; ++i)
210: for (uint256 i; i < _op.tokenIds.length; ++i)
```
[34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L34) | [170](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L170) | [175](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L175) | [197](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L197) | [210](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L210)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

46: for (i = 1; i <= lenLen; i++)
59: for (; i < 32; i++)
66: for (uint256 j = 0; j < out_.length; j++)
```
[46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L46) | [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L59) | [66](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

85: for (uint256 i = 0; i < proof.length; i++)
208: for (uint256 i = 0; i < length;)
244: for (; shared_ < max && _a[shared_] == _b[shared_];)
```
[85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85) | [208](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L208) | [244](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L244)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

104: for (uint256 i; i < _ids.length; ++i)
210: for (uint256 i; i < _instances.length; ++i)
```
[104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L104) | [210](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

59: for (uint256 i; i < tokenIds.length; ++i)
```
[59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59)

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

80: for (uint256 i; i < serialNumBatch.length; ++i)
95: for (uint256 i; i < serialNumBatch.length; ++i)
191: for (uint256 i; i < enclaveId.tcbLevels.length; ++i)
214: for (uint256 i; i < tcb.tcbLevels.length; ++i)
240: for (uint256 i; i < CPUSVN_LENGTH; ++i)
259: for (uint256 i; i < n; ++i)
420: for (uint256 i; i < 3; ++i)
```
[80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L80) | [95](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L95) | [191](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L191) | [214](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L214) | [240](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L240) | [259](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L259) | [420](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L420)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

54: for (uint256 i; i < size; ++i)
244: for (uint256 i; i < split.length; ++i)
354: for (uint256 i; i < SGX_TCB_CPUSVN_SIZE + 1; ++i)
```
[54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L54) | [244](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L244) | [354](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L354)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

153: for (uint256 i; i < encoded.length; ++i)
281: for (uint256 i; i < 3; ++i)
```
[153](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L153) | [281](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L281)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

80: for (uint256 idx = 0; idx < shortest; idx += 32)
333: for (uint256 i; i < len; ++i)
```
[80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L80) | [333](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L333)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

140: for (uint256 i = 2; i < 2 + paddingLen; ++i)
152: for (uint256 i; i < digestAlgoWithParamLen; ++i)
158: for (uint256 i; i < digestAlgoWithParamLen; ++i)
174: for (uint256 i; i < _sha256.length; ++i)
273: for (uint256 i = 2; i < 2 + paddingLen; ++i)
283: for (uint256 i; i < sha1Prefix.length; ++i)
290: for (uint256 i; i < _sha1.length; ++i)
```
[140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L140) | [152](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L152) | [158](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L158) | [174](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L174) | [273](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L273) | [283](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L283) | [290](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L290)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

48: for (uint16 i = 1970; i < year; ++i)
59: for (uint8 i = 1; i < month; ++i)
```
[48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L48) | [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L59)
</details>

### [G-06] Use `assembly` for Efficient Event Emission

To efficiently emit events, consider utilizing assembly by making use of scratch space and the free memory pointer.
This approach can potentially avoid the costs associated with memory expansion.

However, it's crucial to cache and restore the free memory pointer for safe optimization.
Good examples of such practices can be found in well-optimized [Solady's codebases](https://github.com/Vectorized/solady/blob/main/src/tokens/ERC1155.sol#L167).
Please review your code and consider the potential gas savings of this approach.

<details>
<summary><i>55 issue instances in 22 files:</i></summary>

```solidity
File: packages/protocol/contracts/common/AddressManager.sol

50: emit AddressSet(_chainId, _name, _newAddress, oldAddress)
```
[50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L50)

```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

71: emit Paused(msg.sender)
80: emit Unpaused(msg.sender)
```
[71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L71) | [80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L80)

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

129: emit BlockAssigned(_blk.assignedProver, _meta, assignment)
```
[129](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L129)

```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

50: emit EthDeposited(
            TaikoData.EthDeposit({
                recipient: recipient_,
                amount: uint96(msg.value),
                id: _state.slotA.numEthDeposits
            })
        )
```
[50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L50)

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

166: emit BlobCached(meta_.blobHash)
273: emit BlockProposed({
            blockId: blk.blockId,
            assignedProver: blk.assignedProver,
            livenessBond: _config.livenessBond,
            meta: meta_,
            depositsProcessed: deposits_
        })
```
[166](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L166) | [273](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L273)

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

80: emit ProvingPaused(_pause)
209: emit TransitionProved({
                blockId: blk.blockId,
                tran: _tran,
                prover: msg.sender,
                validityBond: tier.validityBond,
                tier: _proof.tier
            })
230: emit TransitionProved({
                    blockId: blk.blockId,
                    tran: _tran,
                    prover: msg.sender,
                    validityBond: 0,
                    tier: _proof.tier
                })
254: emit TransitionContested({
                    blockId: blk.blockId,
                    tran: _tran,
                    contester: msg.sender,
                    contestBond: tier.contestBond,
                    tier: _proof.tier
                })
```
[80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L80) | [209](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L209) | [230](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L230) | [254](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L254)

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

73: emit BlockVerified({
            blockId: 0,
            assignedProver: address(0),
            prover: address(0),
            blockHash: _genesisBlockHash,
            stateRoot: 0,
            tier: 0,
            contestations: 0
        })
198: emit BlockVerified({
                    blockId: blockId,
                    assignedProver: blk.assignedProver,
                    prover: ts.prover,
                    blockHash: blockHash,
                    stateRoot: stateRoot,
                    tier: ts.tier,
                    contestations: ts.contestations
                })
```
[73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L73) | [198](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L198)

```solidity
File: packages/protocol/contracts/L1/provers/GuardianProver.sol

54: emit GuardianApproval(msg.sender, _meta.id, _tran.blockHash, approved_)
```
[54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L54)

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

95: emit GuardiansUpdated(version, _newGuardians)
121: emit Approved(_operationId, _approval, approved_)
```
[95](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L95) | [121](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L121)

```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

53: emit TransactionExecuted(nextTxId++, bytes4(txdata))
```
[53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L53)

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

157: emit Anchored(blockhash(parentId), gasExcess)
```
[157](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L157)

```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

39: emit ConfigAndExcessChanged(_newConfig, _newGasExcess)
```
[39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L39)

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

59: emit Authorized(_addr, _authorize)
250: emit ChainDataSynced(_chainId, _blockId, _kind, _chainData, signal_)
268: emit SignalSent(_app, _signal, slot_, _value)
```
[59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L59) | [250](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L250) | [268](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L268)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

93: emit MessageSuspended(msgHash, _suspend)
111: emit AddressBanned(_addr, _ban)
151: emit MessageSent(msgHash_, message_)
208: emit MessageRecalled(msgHash)
210: emit MessageReceived(msgHash, _message, true)
301: emit MessageExecuted(msgHash)
303: emit MessageReceived(msgHash, _message, false)
336: emit MessageRetried(msgHash)
519: emit MessageStatusChanged(_msgHash, _status)
```
[93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L93) | [111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L111) | [151](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L151) | [208](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L208) | [210](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L210) | [301](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L301) | [303](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L303) | [336](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L336) | [519](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L519)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

51: emit MigrationStatusChanged(_migratingAddress, _migratingInbound)
63: emit MigratedTo(migratingAddress, _account, _amount)
80: emit MigratedTo(migratingAddress, _account, _amount)
```
[51](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L51) | [63](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L63) | [80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L80)

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

80: emit TokenSent({
            msgHash: msgHash,
            from: message_.srcOwner,
            to: _op.to,
            destChainId: message_.destChainId,
            ctoken: ctoken.addr,
            token: _op.token,
            tokenIds: _op.tokenIds,
            amounts: _op.amounts
        })
114: emit TokenReceived({
            msgHash: ctx.msgHash,
            from: from,
            to: to,
            srcChainId: ctx.srcChainId,
            ctoken: ctoken.addr,
            token: token,
            tokenIds: tokenIds,
            amounts: amounts
        })
149: emit TokenReleased({
            msgHash: msgHash,
            from: message.srcOwner,
            ctoken: ctoken.addr,
            token: token,
            tokenIds: tokenIds,
            amounts: amounts
        })
314: emit BridgedTokenDeployed({
            chainId: _ctoken.chainId,
            ctoken: _ctoken.addr,
            btoken: btoken_,
            ctokenSymbol: _ctoken.symbol,
            ctokenName: _ctoken.name
        })
```
[80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L80) | [114](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L114) | [149](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L149) | [314](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L314)

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

191: emit BridgedTokenChanged({
            srcChainId: _ctoken.chainId,
            ctoken: _ctoken.addr,
            btokenOld: btokenOld_,
            btokenNew: _btokenNew,
            ctokenSymbol: _ctoken.symbol,
            ctokenName: _ctoken.name,
            ctokenDecimal: _ctoken.decimals
        })
241: emit TokenSent({
            msgHash: msgHash,
            from: message_.srcOwner,
            to: _op.to,
            destChainId: _op.destChainId,
            ctoken: ctoken.addr,
            token: _op.token,
            amount: balanceChange
        })
273: emit TokenReceived({
            msgHash: ctx.msgHash,
            from: from,
            to: to,
            srcChainId: ctx.srcChainId,
            ctoken: ctoken.addr,
            token: token,
            amount: amount
        })
306: emit TokenReleased({
            msgHash: _msgHash,
            from: _message.srcOwner,
            ctoken: ctoken.addr,
            token: token,
            amount: amount
        })
425: emit BridgedTokenDeployed({
            srcChainId: ctoken.chainId,
            ctoken: ctoken.addr,
            btoken: btoken,
            ctokenSymbol: ctoken.symbol,
            ctokenName: ctoken.name,
            ctokenDecimal: ctoken.decimals
        })
```
[191](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L191) | [241](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L241) | [273](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L273) | [306](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L306) | [425](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L425)

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

64: emit TokenSent({
            msgHash: msgHash,
            from: message_.srcOwner,
            to: _op.to,
            destChainId: message_.destChainId,
            ctoken: ctoken.addr,
            token: _op.token,
            tokenIds: _op.tokenIds,
            amounts: _op.amounts
        })
97: emit TokenReceived({
            msgHash: ctx.msgHash,
            from: from,
            to: to,
            srcChainId: ctx.srcChainId,
            ctoken: ctoken.addr,
            token: token,
            tokenIds: tokenIds,
            amounts: new uint256[](tokenIds.length)
        })
131: emit TokenReleased({
            msgHash: _msgHash,
            from: _message.srcOwner,
            ctoken: ctoken.addr,
            token: token,
            tokenIds: tokenIds,
            amounts: new uint256[](tokenIds.length)
        })
250: emit BridgedTokenDeployed({
            chainId: _ctoken.chainId,
            ctoken: _ctoken.addr,
            btoken: btoken_,
            ctokenSymbol: _ctoken.symbol,
            ctokenName: _ctoken.name
        })
```
[64](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L64) | [97](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L97) | [131](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L131) | [250](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L250)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

109: emit InstanceDeleted(idx, instances[idx].addr)
220: emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince)
230: emit InstanceAdded(id, newInstance, oldInstance, block.timestamp)
```
[109](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L109) | [220](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220) | [230](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L230)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

93: emit Withdrawn(user, amount)
```
[93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L93)

```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

74: emit Claimed(hash)
```
[74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L74)

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

143: emit Granted(_recipient, _grant)
157: emit Voided(_recipient, amountVoided)
222: emit Withdrawn(_recipient, _to, amountToWithdraw, costToWithdraw)
```
[143](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L143) | [157](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L157) | [222](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L222)
</details>

### [G-07] Use custom errors rather than `require()/assert()/revert(with msg)` with string to save gas

Custom errors are available from solidity version 0.8.4.
Custom errors save [~50](https://gist.github.com/IllIllI000/ad1bd0d29a0101b25e57c293b4b0c746) gas each time they're hit by [avoiding having to allocate and store the revert string](https://soliditylang.org/blog/2021/04/21/custom-errors/#errors-in-depth).
Alse Custom error are cheaper than `assert()`.
```solidity
    revert CustomError(); // 157 gas
    assert(false); // 164 gas
    revert("Custom Error"); // 406 gas
    require(false, "Custom Error"); // 421 gas
```


<details>
<summary><i>70 issue instances in 10 files:</i></summary>

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

223: assert(tier.validityBond == 0)
224: assert(ts.validityBond == 0 && ts.contestBond == 0 && ts.contester == address(0))
```
[223](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L223) | [224](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L224)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

486: assert(_message.from != address(this))
```
[486](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L486)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/Bytes.sol

25: require(_length + 31 >= _length, "slice_overflow")
26: require(_start + _length >= _start, "slice_overflow")
27: require(_bytes.length >= _start + _length, "slice_outOfBounds")
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L25) | [26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L26) | [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L27)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

37: require(
            _in.length > 0,
            "RLPReader: length of an RLP item must be greater than zero to be decodable"
        )
56: require(
            itemType == RLPItemType.LIST_ITEM,
            "RLPReader: decoded item type for list is not a list item"
        )
61: require(
            listOffset + listLength == _in.length,
            "RLPReader: list item has an invalid data remainder"
        )
112: require(
            itemType == RLPItemType.DATA_ITEM,
            "RLPReader: decoded item type for bytes is not a data item"
        )
117: require(
            _in.length == itemOffset + itemLength,
            "RLPReader: bytes value contains an invalid remainder"
        )
152: require(
            _in.length > 0,
            "RLPReader: length of an RLP item must be greater than zero to be decodable"
        )
172: require(
                _in.length > strLen,
                "RLPReader: length of content must be greater than string length (short string)"
            )
182: require(
                strLen != 1 || firstByteOfContent >= 0x80,
                "RLPReader: invalid prefix, single byte < 0x80 are not prefixed (short string)"
            )
192: require(
                _in.length > lenOfStrLen,
                "RLPReader: length of content must be > than length of string length (long string)"
            )
202: require(
                firstByteOfContent != 0x00,
                "RLPReader: length of content must not have any leading zeros (long string)"
            )
212: require(
                strLen > 55,
                "RLPReader: length of content must be greater than 55 bytes (long string)"
            )
217: require(
                _in.length > lenOfStrLen + strLen,
                "RLPReader: length of content must be greater than total length (long string)"
            )
228: require(
                _in.length > listLen,
                "RLPReader: length of content must be greater than list length (short list)"
            )
238: require(
                _in.length > lenOfListLen,
                "RLPReader: length of content must be > than length of list length (long list)"
            )
248: require(
                firstByteOfContent != 0x00,
                "RLPReader: length of content must not have any leading zeros (long list)"
            )
258: require(
                listLen > 55,
                "RLPReader: length of content must be greater than 55 bytes (long list)"
            )
263: require(
                _in.length > lenOfListLen + listLen,
                "RLPReader: length of content must be greater than total length (long list)"
            )
```
[37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L37) | [56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L56) | [61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L61) | [112](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L112) | [117](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L117) | [152](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L152) | [172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L172) | [182](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L182) | [192](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L192) | [202](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L202) | [212](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L212) | [217](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L217) | [228](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L228) | [238](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L238) | [248](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L248) | [258](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L258) | [263](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L263)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

77: require(_key.length > 0, "MerkleTrie: empty key")
89: require(currentKeyIndex <= key.length, "MerkleTrie: key index exceeds total key length")
93: require(
                    Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
                    "MerkleTrie: invalid root hash"
                )
99: require(
                    Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
                    "MerkleTrie: invalid large internal hash"
                )
105: require(
                    Bytes.equal(currentNode.encoded, currentNodeID),
                    "MerkleTrie: invalid internal node hash"
                )
119: require(
                        value_.length > 0,
                        "MerkleTrie: value length must be greater than zero (branch)"
                    )
125: require(
                        i == proof.length - 1,
                        "MerkleTrie: value node must be last node in proof (branch)"
                    )
150: require(
                    pathRemainder.length == sharedNibbleLength,
                    "MerkleTrie: path remainder must share all nibbles with key"
                )
162: require(
                        keyRemainder.length == sharedNibbleLength,
                        "MerkleTrie: key remainder must be identical to path remainder"
                    )
172: require(
                        value_.length > 0,
                        "MerkleTrie: value length must be greater than zero (leaf)"
                    )
178: require(
                        i == proof.length - 1,
                        "MerkleTrie: value node must be last node in proof (leaf)"
                    )
191: revert("MerkleTrie: received a node with an unknown prefix")
194: revert("MerkleTrie: received an unparseable node")
198: revert("MerkleTrie: ran out of proof elements")
```
[77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L77) | [89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L89) | [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L93) | [99](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L99) | [105](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L105) | [119](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L119) | [125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L125) | [150](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L150) | [162](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L162) | [172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L172) | [178](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L178) | [191](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L191) | [194](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L194) | [198](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L198)

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

61: require(msg.sender == owner, "onlyOwner")
```
[61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L61)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

77: require(
            localEnclaveReport.reserved3.length == 96 && localEnclaveReport.reserved4.length == 60
                && localEnclaveReport.reportData.length == 64,
            "local QE report has wrong length"
        )
82: require(
            pckSignedQeReport.reserved3.length == 96 && pckSignedQeReport.reserved4.length == 60
                && pckSignedQeReport.reportData.length == 64,
            "QE report has wrong length"
        )
87: require(
            v3Quote.v3AuthData.certification.certType == 5,
            "certType must be 5: Concatenated PCK Cert Chain (PEM formatted)"
        )
91: require(
            v3Quote.v3AuthData.certification.decodedCertDataArray.length == 3, "3 certs in chain"
        )
94: require(
            v3Quote.v3AuthData.ecdsa256BitSignature.length == 64
                && v3Quote.v3AuthData.ecdsaAttestationKey.length == 64
                && v3Quote.v3AuthData.qeReportSignature.length == 64,
            "Invalid ECDSA signature format"
        )
100: require(
            v3Quote.v3AuthData.qeAuthData.parsedDataSize
                == v3Quote.v3AuthData.qeAuthData.data.length,
            "Invalid QEAuthData size"
        )
116: require(totalQuoteSize >= MINIMUM_QUOTE_LENGTH, "Invalid quote size")
279: require(certParsedSuccessfully, "splitCertificateChain failed")
```
[77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L77) | [82](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L82) | [87](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L87) | [91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L91) | [94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L94) | [100](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L100) | [116](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L116) | [279](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L279)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

57: require(der[ptr.ixs()] == 0x03, "Not type BIT STRING")
67: require(der[ptr.ixs()] == 0x04, "Not type OCTET STRING")
88: require(der[ptr.ixs()] & 0x20 == 0x20, "Not a constructed type")
142: require(der[ptr.ixs()] == 0x02, "Not type INTEGER")
143: require(der[ptr.ixf()] & 0x80 == 0, "Not positive")
155: require(der[ptr.ixs()] == 0x02, "Not type INTEGER")
156: require(der[ptr.ixf()] & 0x80 == 0, "Not positive")
180: require(der[ptr.ixs()] == 0x03, "ixs Not type BIT STRING 0x03")
182: require(der[ptr.ixf()] == 0x00, "ixf Not 0")
```
[57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L57) | [67](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L67) | [88](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L88) | [142](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L142) | [143](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L143) | [155](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L155) | [156](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L156) | [180](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L180) | [182](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L182)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

25: require(offset + len <= self.length, "invalid offset")
199: require(idx + 2 <= self.length, "invalid idx")
212: require(idx + 4 <= self.length, "unexpected idx")
225: require(idx + 32 <= self.length, "unexpected idx")
238: require(idx + 20 <= self.length, "unexpected idx")
264: require(len <= 32, "unexpected len")
265: require(idx + len <= self.length, "unexpected idx")
293: require(offset + len <= self.length, "unexpected offset")
329: require(len <= 52, "unexpected len")
335: require(char >= 0x30 && char <= 0x7A, "invalid char")
337: require(decoded <= 0x20, "invalid decoded")
365: revert("unexpected len")
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L25) | [199](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L199) | [212](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L212) | [225](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L225) | [238](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L238) | [264](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L264) | [265](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L265) | [293](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L293) | [329](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L329) | [335](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L335) | [337](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L337) | [365](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L365)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

138: assert(success)
50: revert("Unsupported algorithm")
75: revert("Unsupported algorithm")
```
[138](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L138) | [50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L50) | [75](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L75)
</details>

### [G-08] Avoid Emitting Events Inside Loops

Emitting an event inside a loop performs a LOG operation N times, where N is the loop length.
Consider refactoring the code to emit the event only once at the end of the loop.
Gas savings should be multiplied by the average loop length.
This approach can improve the gas efficiency of your contract and make transaction costs more predictable for users.

<details>
<summary><i>4 issue instances in 3 files:</i></summary>

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

198: emit BlockVerified({
                    blockId: blockId,
                    assignedProver: blk.assignedProver,
                    prover: ts.prover,
                    blockHash: blockHash,
                    stateRoot: stateRoot,
                    tier: ts.tier,
                    contestations: ts.contestations
                })
```
[198](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L198)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

93: emit MessageSuspended(msgHash, _suspend)
```
[93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L93)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

109: emit InstanceDeleted(idx, instances[idx].addr)
220: emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince)
```
[109](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L109) | [220](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220)
</details>

### [G-09] Enable IR-based code generation

The `--via-ir` command line option activates the IR-based code generator in Solidity, which is designed to enable powerful optimization passes that can span across functions. The end result may be a contract that requires less gas to execute its functions.

We recommend you enable this feature, run tests, and benchmark the gas usage of your contract to evaluate if it leads to any tangible gas savings. Experimenting with this feature could lead to a more gas-efficient contract.

[Solidity Documentation](https://docs.soliditylang.org/en/v0.8.20/ir-breaking-changes.html#solidity-ir-based-codegen-changes).

<details>
<summary><i>81 issue instances in 1 files:</i></summary>

```solidity

File: packages/protocol/contracts/common/IAddressManager.sol
File: packages/protocol/contracts/common/AddressManager.sol
File: packages/protocol/contracts/common/IAddressResolver.sol
File: packages/protocol/contracts/common/AddressResolver.sol
File: packages/protocol/contracts/common/EssentialContract.sol
File: packages/protocol/contracts/libs/Lib4844.sol
File: packages/protocol/contracts/libs/LibAddress.sol
File: packages/protocol/contracts/libs/LibMath.sol
File: packages/protocol/contracts/libs/LibTrieProof.sol
File: packages/protocol/contracts/L1/gov/TaikoGovernor.sol
File: packages/protocol/contracts/L1/gov/TaikoTimelockController.sol
File: packages/protocol/contracts/L1/hooks/IHook.sol
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol
File: packages/protocol/contracts/L1/ITaikoL1.sol
File: packages/protocol/contracts/L1/libs/LibDepositing.sol
File: packages/protocol/contracts/L1/libs/LibProposing.sol
File: packages/protocol/contracts/L1/libs/LibProving.sol
File: packages/protocol/contracts/L1/libs/LibUtils.sol
File: packages/protocol/contracts/L1/libs/LibVerifying.sol
File: packages/protocol/contracts/L1/provers/GuardianProver.sol
File: packages/protocol/contracts/L1/provers/Guardians.sol
File: packages/protocol/contracts/L1/TaikoData.sol
File: packages/protocol/contracts/L1/TaikoErrors.sol
File: packages/protocol/contracts/L1/TaikoEvents.sol
File: packages/protocol/contracts/L1/TaikoL1.sol
File: packages/protocol/contracts/L1/TaikoToken.sol
File: packages/protocol/contracts/L1/tiers/ITierProvider.sol
File: packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol
File: packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol
File: packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol
File: packages/protocol/contracts/L2/CrossChainOwned.sol
File: packages/protocol/contracts/L2/Lib1559Math.sol
File: packages/protocol/contracts/L2/TaikoL2.sol
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol
File: packages/protocol/contracts/signal/ISignalService.sol
File: packages/protocol/contracts/signal/LibSignals.sol
File: packages/protocol/contracts/signal/SignalService.sol
File: packages/protocol/contracts/bridge/IBridge.sol
File: packages/protocol/contracts/bridge/Bridge.sol
File: packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol
File: packages/protocol/contracts/tokenvault/BaseNFTVault.sol
File: packages/protocol/contracts/tokenvault/BaseVault.sol
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol
File: packages/protocol/contracts/tokenvault/IBridgedERC20.sol
File: packages/protocol/contracts/tokenvault/LibBridgedToken.sol
File: packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol
File: packages/protocol/contracts/thirdparty/optimism/Bytes.sol
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol
File: packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol
File: packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol
File: packages/protocol/contracts/verifiers/IVerifier.sol
File: packages/protocol/contracts/verifiers/GuardianVerifier.sol
File: packages/protocol/contracts/verifiers/SgxVerifier.sol
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol
File: packages/protocol/contracts/team/TimelockTokenPool.sol
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol
File: packages/protocol/contracts/automata-attestation/interfaces/IAttestation.sol
File: packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol
File: packages/protocol/contracts/automata-attestation/lib/EnclaveIdStruct.sol
File: packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol
File: packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol
File: packages/protocol/contracts/automata-attestation/utils/SHA1.sol
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressManager.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressResolver.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibMath.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/IHook.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/ITaikoL1.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoErrors.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/LibSignals.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/IBridgedERC20.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/IVerifier.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/interfaces/IAttestation.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/EnclaveIdStruct.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SHA1.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L1) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L1)
</details>

### [G-10] Assembly: Check `msg.sender` using xor and the scratch space

See [this](https://code4rena.com/reports/2023-05-juicebox#g-06-use-assembly-to-validate-msgsender) prior finding for details on the conversion

<details>
<summary><i>22 issue instances in 11 files:</i></summary>

```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

25: if (msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L25)

```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

42: if (msg.sender != owner() && msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();
42: if (msg.sender != owner() && msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();
```
[42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L42) | [42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L42)

```solidity
File: packages/protocol/contracts/libs/LibAddress.sol

78: return msg.sender == tx.origin;
```
[78](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L78)

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

310: if (proposerOne != address(0) && msg.sender != proposerOne) {
316: return proposer == address(0) || msg.sender == proposer;
```
[310](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L310) | [316](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L316)

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

416: bool isAssignedPover = msg.sender == _blk.assignedProver;
```
[416](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L416)

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

123: if (msg.sender != GOLDEN_TOUCH_ADDRESS) revert L2_INVALID_SENDER();
```
[123](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L123)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

250: if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) {
260: if (_message.gasLimit == 0 && msg.sender != _message.destOwner) {
280: uint256 gasLimit = msg.sender == _message.destOwner ? gasleft() : _message.gasLimit;
294: if (msg.sender == refundTo) {
322: if (msg.sender != _message.destOwner) revert B_PERMISSION_DENIED();
```
[250](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L250) | [260](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L260) | [280](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L280) | [294](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L294) | [322](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L322)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

38: if (msg.sender != owner() && msg.sender != snapshooter) {
38: if (msg.sender != owner() && msg.sender != snapshooter) {
```
[38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L38) | [38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L38)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

61: if (msg.sender == migratingAddress) {
64: } else if (msg.sender != resolve("erc20_vault", true)) {
78: if (msg.sender != _account) revert BB_PERMISSION_DENIED();
83: } else if (msg.sender != resolve("erc20_vault", true)) {
```
[61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L61) | [64](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L64) | [78](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L78) | [83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L83)

```solidity
File: packages/protocol/contracts/tokenvault/BaseVault.sol

23: if (msg.sender != resolve("bridge", false)) {
65: if (ctx_.from != msg.sender) revert VAULT_PERMISSION_DENIED();
```
[23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L23) | [65](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L65)

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

61: require(msg.sender == owner, "onlyOwner");
```
[61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L61)
</details>

### [G-11] Assembly: Use scratch space for building calldata

If an external call's calldata can fit into two or fewer words, use the scratch space to build the calldata, rather than allowing Solidity to do a memory expansion.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

372: (
            bool successful,
            ,
            ,
            bytes memory signedQuoteData,
            V3Struct.ECDSAQuoteV3AuthData memory authDataV3
        ) = V3Parser.validateParsedInput(v3quote)
```
[372](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L372)
</details>

### [G-12] Multiple `address`/ID mappings can be combined into a single `mapping` of an `address`/ID to a `struct`

Combining multiple address/ID mappings into a single mapping to a struct can lead to gas savings.
By refactoring multiple mappings into a singular mapping with a struct, you can save on storage slots, which in turn can reduce the gas cost in certain operations.
Prioritize this refactor if optimizing gas is a primary concern for your contract's operations.

<details>
<summary><i>8 issue instances in 4 files:</i></summary>

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

35: mapping(bytes32 msgHash => Status status) public messageStatus
46: mapping(bytes32 msgHash => ProofReceipt receipt) public proofReceipt
```
[35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L35) | [46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L46)

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

45: mapping(address btoken => CanonicalERC20 canonical) public bridgedToCanonical
52: mapping(address btoken => bool blacklisted) public btokenBlacklist
```
[45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L45) | [52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L52)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

22: mapping(address addr => uint256 amountClaimed) public claimedAmount
25: mapping(address addr => uint256 amountWithdrawn) public withdrawnAmount
```
[22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L22) | [25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L25)

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

39: mapping(bytes32 enclave => bool trusted) private _trustedUserMrEnclave
40: mapping(bytes32 signer => bool trusted) private _trustedUserMrSigner
```
[39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L39) | [40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L40)
</details>

### [G-13] Assigning `state` variables directly with struct constructors wastes gas

Utilizing named struct constructors for `state`(only state) variable assignments can lead to inefficient gas usage.
When a struct is initialized with named arguments, the Solidity compiler must first organize these fields in memory, which consumes additional gas.
To optimize gas usage, it is recommended to assign struct fields directly in storage using dot notation.
```solidity
    // stateStruct = TestStruct(20, 20); // 4633 gas
    // stateStruct = TestStruct({ var1: 20, var2: 20 }); // 4633 gas
    // stateStruct.var1 = 20;
    // stateStruct.var2 = 20; // 4562 gas
```

<details>
<summary><i>4 issue instances in 2 files:</i></summary>

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

243: proofReceipt[msgHash] = ProofReceipt({
                    receivedAt: receivedAt,
                    preferredExecutor: _message.gasLimit == 0 ? _message.destOwner : msg.sender
                })
549: __ctx = Context(_msgHash, _from, _srcChainId)
```
[243](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L243) | [549](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L549)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

217: instances[nextInstanceId] = Instance(_instances[i], validSince)
229: instances[id] = Instance(newInstance, uint64(block.timestamp))
```
[217](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L217) | [229](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L229)
</details>

### [G-14] Assembly: Use scratch space when building emitted events with two data arguments

Using the scratch space for more than one, but at most two words worth of data (non-indexed arguments) will save gas over needing Solidity's abi memory expansion used for emitting normally.

<details>
<summary><i>9 issue instances in 8 files:</i></summary>

```solidity
File: packages/protocol/contracts/common/AddressManager.sol

50: emit AddressSet(_chainId, _name, _newAddress, oldAddress)
```
[50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L50)

```solidity
File: packages/protocol/contracts/L1/provers/GuardianProver.sol

54: emit GuardianApproval(msg.sender, _meta.id, _tran.blockHash, approved_)
```
[54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L54)

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

121: emit Approved(_operationId, _approval, approved_)
```
[121](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L121)

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

157: emit Anchored(blockhash(parentId), gasExcess)
```
[157](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L157)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

51: emit MigrationStatusChanged(_migratingAddress, _migratingInbound)
```
[51](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L51)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

220: emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince)
230: emit InstanceAdded(id, newInstance, oldInstance, block.timestamp)
```
[220](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220) | [230](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L230)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

93: emit Withdrawn(user, amount)
```
[93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L93)

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

222: emit Withdrawn(_recipient, _to, amountToWithdraw, costToWithdraw)
```
[222](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L222)
</details>

### [G-15] Stack variable is only used once

If the variable is only accessed once, it's cheaper to use the assigned value directly that one time, and save the 3 gas the extra stack assignment would spend

<details>
<summary><i>124 issue instances in 27 files:</i></summary>

```solidity
File: packages/protocol/contracts/libs/LibTrieProof.sol

/// @audit - `accountState` variable
52: RLPReader.RLPItem[] memory accountState = RLPReader.readList(rlpAccount)
/// @audit - `verified` variable
60: bool verified = SecureMerkleTrie.verifyInclusionProof(
            bytes.concat(_slot), RLPWriter.writeUint(uint256(_value)), _storageProof, storageRoot_
        )
```
[52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L52) | [60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L60)

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

/// @audit - `hash` variable
94: bytes32 hash = hashAssignment(assignment, taikoL1Address, _meta.blobHash)
/// @audit - `tko` variable
101: IERC20 tko = IERC20(resolve("taiko_token", false))
```
[94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L94) | [101](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L101)

```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

/// @audit - `slot` variable
45: uint256 slot = _state.slotA.numEthDeposits % _config.ethDepositRingBufferSize
```
[45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L45)

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

/// @audit - `tkoBalance` variable
238: uint256 tkoBalance = tko.balanceOf(address(this))
```
[238](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L238)

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

/// @audit - `isContesting` variable
164: bool isContesting = _proof.tier == ts.tier && tier.contestBond != 0
/// @audit - `ctx` variable
166: IVerifier.Context memory ctx = IVerifier.Context({
                    metaHash: blk.metaHash,
                    blobHash: _meta.blobHash,
                    // Separate msgSender to allow the prover to be any address in the future.
                    prover: msg.sender,
                    msgSender: msg.sender,
                    blockId: blk.blockId,
                    isContesting: isContesting,
                    blobUsed: _meta.blobUsed
                })
/// @audit - `returnLivenessBond` variable
192: bool returnLivenessBond = blk.livenessBond > 0 && _proof.data.length == 32
                && bytes32(_proof.data) == RETURN_LIVENESS_BOND
/// @audit - `inProvingWindow` variable
414: bool inProvingWindow = uint256(_ts.timestamp).max(_state.slotB.lastUnpausedAt)
            + _tier.provingWindow * 60 >= block.timestamp
```
[164](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L164) | [166](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L166) | [192](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L192) | [414](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L414)

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

/// @audit - `tko` variable
188: IERC20 tko = IERC20(_resolver.resolve("taiko_token", false))
```
[188](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L188)

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

/// @audit - `guardiansLength` variable
131: uint256 guardiansLength = guardians.length
```
[131](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L131)

```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

/// @audit - `maxBlocksToVerify` variable
94: uint8 maxBlocksToVerify = LibProving.proveBlock(state, config, this, meta, tran, proof)
```
[94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L94)

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

/// @audit - `config` variable
136: Config memory config = getConfig()
```
[136](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L136)

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

/// @audit - `signalRoot` variable
107: bytes32 signalRoot = _verifyHopProof(chainId, app, signal, value, hop, signalService)
/// @audit - `kind` variable
124: bytes32 kind = isFullProof ? LibSignals.STATE_ROOT : LibSignals.SIGNAL_ROOT
/// @audit - `signal` variable
148: bytes32 signal = signalForChainData(_chainId, _kind, _blockId)
/// @audit - `signal` variable
170: bytes32 signal = signalForChainData(_chainId, _kind, blockId_)
/// @audit - `cacheStateRoot` variable
282: bool cacheStateRoot = _hop.cacheOption == CacheOption.CACHE_BOTH
            || _hop.cacheOption == CacheOption.CACHE_STATE_ROOT
/// @audit - `cacheSignalRoot` variable
290: bool cacheSignalRoot = _hop.cacheOption == CacheOption.CACHE_BOTH
            || _hop.cacheOption == CacheOption.CACHE_SIGNAL_ROOT
/// @audit - `slot` variable
308: bytes32 slot = getSignalSlot(uint64(block.chainid), _app, _signal)
```
[107](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L107) | [124](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L124) | [148](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L148) | [170](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L170) | [282](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L282) | [290](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L290) | [308](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L308)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

/// @audit - `_timestamp` variable
89: uint64 _timestamp = _suspend ? type(uint64).max : uint64(block.timestamp)
/// @audit - `expectedAmount` variable
138: uint256 expectedAmount = _message.value + _message.fee
/// @audit - `failureSignal` variable
178: bytes32 failureSignal = signalForFailedMessage(msgHash)
/// @audit - `gasLimit` variable
280: uint256 gasLimit = msg.sender == _message.destOwner ? gasleft() : _message.gasLimit
/// @audit - `msgHash` variable
557: bytes32 msgHash
/// @audit - `from` variable
558: address from
/// @audit - `srcChainId` variable
559: uint64 srcChainId
/// @audit - `data` variable
587: bytes memory data = abi.encodeCall(
            ISignalService.proveSignalReceived,
            (_chainId, resolve(_chainId, "bridge", false), _signal, _proof)
        )
```
[89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L89) | [138](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L138) | [178](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L178) | [280](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L280) | [557](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L557) | [558](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L558) | [559](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L559) | [587](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L587)

```solidity
File: packages/protocol/contracts/tokenvault/BaseVault.sol

/// @audit - `selfOnSourceChain` variable
54: address selfOnSourceChain = resolve(ctx_.srcChainId, name(), false)
```
[54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L54)

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

/// @audit - `message` variable
58: IBridge.Message memory message = IBridge.Message({
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
        })
/// @audit - `token` variable
111: address token = _transferTokens(ctoken, to, tokenIds, amounts)
/// @audit - `token` variable
145: address token = _transferTokens(ctoken, message.srcOwner, tokenIds, amounts)
/// @audit - `data` variable
304: bytes memory data = abi.encodeCall(
            BridgedERC1155.init,
            (owner(), addressManager, _ctoken.addr, _ctoken.chainId, _ctoken.symbol, _ctoken.name)
        )
```
[58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L58) | [111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L111) | [145](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L145) | [304](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L304)

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

/// @audit - `message` variable
221: IBridge.Message memory message = IBridge.Message({
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
        })
/// @audit - `token` variable
270: address token = _transferTokens(ctoken, to, amount)
/// @audit - `token` variable
303: address token = _transferTokens(ctoken, _message.srcOwner, amount)
/// @audit - `_balance` variable
378: uint256 _balance = t.balanceOf(address(this))
/// @audit - `data` variable
408: bytes memory data = abi.encodeCall(
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
        )
```
[221](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L221) | [270](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L270) | [303](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L303) | [378](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L378) | [408](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L408)

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

/// @audit - `message` variable
44: IBridge.Message memory message = IBridge.Message({
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
        })
/// @audit - `token` variable
94: address token = _transferTokens(ctoken, to, tokenIds)
/// @audit - `token` variable
128: address token = _transferTokens(ctoken, _message.srcOwner, tokenIds)
/// @audit - `data` variable
241: bytes memory data = abi.encodeCall(
            BridgedERC721.init,
            (owner(), addressManager, _ctoken.addr, _ctoken.chainId, _ctoken.symbol, _ctoken.name)
        )
```
[44](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L44) | [94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L94) | [128](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L128) | [241](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L241)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

/// @audit - `ptr` variable
157: MemoryPointer ptr = _in.ptr
/// @audit - `src` variable
294: uint256 src = MemoryPointer.unwrap(_src) + _offset
```
[157](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L157) | [294](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L294)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

/// @audit - `branchKey` variable
134: uint8 branchKey = uint8(key[currentKeyIndex])
/// @audit - `nextNode` variable
135: RLPReader.RLPItem memory nextNode = currentNode.decoded[branchKey]
/// @audit - `offset` variable
142: uint8 offset = 2 - (prefix % 2)
/// @audit - `max` variable
243: uint256 max = (_a.length < _b.length) ? _a.length : _b.length
```
[134](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L134) | [135](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L135) | [142](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L142) | [243](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L243)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol

/// @audit - `key` variable
29: bytes memory key = _getSecureKey(_key)
/// @audit - `key` variable
47: bytes memory key = _getSecureKey(_key)
```
[29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L29) | [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L47)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

/// @audit - `signature` variable
156: bytes memory signature = Bytes.slice(_proof.data, 24)
/// @audit - `taikoL1` variable
181: address taikoL1 = resolve("taiko", false)
```
[156](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L156) | [181](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L181)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

/// @audit - `timeBasedAllowance` variable
117: uint256 timeBasedAllowance = balance
            * (block.timestamp.min(claimEnd + withdrawalWindow) - claimEnd) / withdrawalWindow
```
[117](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L117)

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

/// @audit - `r` variable
151: Recipient storage r = recipients[_recipient]
/// @audit - `hash` variable
170: bytes32 hash = keccak256(abi.encodePacked("Withdraw unlocked Taiko token to: ", _to))
/// @audit - `recipient` variable
171: address recipient = ECDSA.recover(hash, _sig)
/// @audit - `_amountUnlocked` variable
197: uint128 _amountUnlocked = amountUnlocked / 1e18
```
[151](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L151) | [170](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L170) | [171](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L171) | [197](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L197)

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

/// @audit - `retData` variable
163: bytes memory retData = abi.encodePacked(INVALID_EXIT_CODE)
/// @audit - `miscselectMatched` variable
181: bool miscselectMatched =
            quoteEnclaveReport.miscSelect & enclaveId.miscselectMask == enclaveId.miscselect
/// @audit - `attributesMatched` variable
184: bool attributesMatched =
            quoteEnclaveReport.attributes & enclaveId.attributesMask == enclaveId.attributes
/// @audit - `mrsignerMatched` variable
186: bool mrsignerMatched = quoteEnclaveReport.mrSigner == enclaveId.mrsigner
/// @audit - `isvprodidMatched` variable
188: bool isvprodidMatched = quoteEnclaveReport.isvProdId == enclaveId.isvprodid
/// @audit - `pceSvnIsHigherOrGreater` variable
216: bool pceSvnIsHigherOrGreater = pck.sgxExtension.pcesvn >= current.pcesvn
/// @audit - `cpuSvnsAreHigherOrGreater` variable
217: bool cpuSvnsAreHigherOrGreater = _isCpuSvnHigherOrGreater(
                pck.sgxExtension.sgxTcbCompSvnArr, current.sgxTcbCompSvnArr
            )
/// @audit - `tcbIsRevoked` variable
222: bool tcbIsRevoked = status == TCBInfoStruct.TCBStatus.TCB_REVOKED
/// @audit - `issuerPubKeyHash` variable
292: bytes32 issuerPubKeyHash = keccak256(issuer.pubKey)
/// @audit - `expectedAuthDataHash` variable
313: bytes32 expectedAuthDataHash = bytes32(qeEnclaveReport.reportData.substring(0, 32))
/// @audit - `concatOfAttestKeyAndQeAuthData` variable
314: bytes memory concatOfAttestKeyAndQeAuthData =
            abi.encodePacked(authDataV3.ecdsaAttestationKey, authDataV3.qeAuthData.data)
/// @audit - `computedAuthDataHash` variable
316: bytes32 computedAuthDataHash = sha256(concatOfAttestKeyAndQeAuthData)
/// @audit - `qeReportDataIsValid` variable
318: bool qeReportDataIsValid = expectedAuthDataHash == computedAuthDataHash
/// @audit - `pckSignedQeReportBytes` variable
320: bytes memory pckSignedQeReportBytes =
                V3Parser.packQEReport(authDataV3.pckSignedQeReport)
/// @audit - `qeSigVerified` variable
322: bool qeSigVerified = sigVerifyLib.verifyES256Signature(
                pckSignedQeReportBytes, authDataV3.qeReportSignature, pckCertPubKey
            )
/// @audit - `quoteSigVerified` variable
325: bool quoteSigVerified = sigVerifyLib.verifyES256Signature(
                signedQuoteData, authDataV3.ecdsa256BitSignature, authDataV3.ecdsaAttestationKey
            )
/// @audit - `mrEnclaveIsTrusted` variable
387: bool mrEnclaveIsTrusted =
                    _trustedUserMrEnclave[v3quote.localEnclaveReport.mrEnclave]
/// @audit - `mrSignerIsTrusted` variable
389: bool mrSignerIsTrusted = _trustedUserMrSigner[v3quote.localEnclaveReport.mrSigner]
/// @audit - `isPckCert` variable
421: bool isPckCert = i == 0
/// @audit - `tcbConfigured` variable
437: bool tcbConfigured = LibString.eq(parsedFmspc, fetchedTcbInfo.fmspc)
/// @audit - `pckCert` variable
442: IPEMCertChainLib.ECSha256Certificate memory pckCert = parsedQuoteCerts[0]
/// @audit - `pceidMatched` variable
443: bool pceidMatched = LibString.eq(pckCert.pck.sgxExtension.pceid, fetchedTcbInfo.pceid)
/// @audit - `pckCertChainVerified` variable
463: bool pckCertChainVerified = _verifyCertChain(parsedQuoteCerts)
/// @audit - `enclaveReportSigsVerified` variable
471: bool enclaveReportSigsVerified = _enclaveReportSigVerification(
                parsedQuoteCerts[0].pubKey,
                signedQuoteData,
                authDataV3,
                v3quote.v3AuthData.pckSignedQeReport
            )
```
[163](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L163) | [181](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L181) | [184](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L184) | [186](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L186) | [188](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L188) | [216](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L216) | [217](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L217) | [222](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L222) | [292](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L292) | [313](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L313) | [314](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L314) | [316](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L316) | [318](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L318) | [320](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L320) | [322](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L322) | [325](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L325) | [387](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L387) | [389](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L389) | [421](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L421) | [437](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L437) | [442](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L442) | [443](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L443) | [463](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L463) | [471](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L471)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

/// @audit - `len` variable
52: uint256 len = pemChain.length
/// @audit - `root` variable
82: uint256 root = der.root()
/// @audit - `serialNumBytes` variable
107: bytes memory serialNumBytes = der.bytesAt(tbsPtr)
/// @audit - `issuerNameIsValid` variable
120: bool issuerNameIsValid = LibString.eq(cert.pck.issuerName, PLATFORM_ISSUER_NAME)
                || LibString.eq(cert.pck.issuerName, PROCESSOR_ISSUER_NAME)
/// @audit - `sigX` variable
174: bytes memory sigX = _trimBytes(der.bytesAt(sigPtr), 32)
/// @audit - `sigY` variable
177: bytes memory sigY = _trimBytes(der.bytesAt(sigPtr), 32)
/// @audit - `headerFound` variable
225: bool headerFound = beginPos != LibString.NOT_FOUND
/// @audit - `footerFound` variable
226: bool footerFound = endPos != LibString.NOT_FOUND
/// @audit - `contentStart` variable
233: uint256 contentStart = beginPos + HEADER_LENGTH
/// @audit - `delimiter` variable
239: bytes memory delimiter = hex"0a"
/// @audit - `contentSlice` variable
240: string memory contentSlice = LibString.slice(pemData, contentStart, endPos)
/// @audit - `lengthDiff` variable
265: uint256 lengthDiff = n - expectedLength
/// @audit - `pceidPtr` variable
312: uint256 pceidPtr = der.nextSiblingOf(extnValueOidPtr)
/// @audit - `fmspcPtr` variable
318: uint256 fmspcPtr = der.nextSiblingOf(extnValueOidPtr)
/// @audit - `tcbPtr` variable
350: uint256 tcbPtr = der.nextSiblingOf(oidPtr)
/// @audit - `svnValuePtr` variable
356: uint256 svnValuePtr = der.nextSiblingOf(svnPtr)
/// @audit - `cpusvn` variable
366: uint256 cpusvn = uint256(svnValue)
```
[52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L52) | [82](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L82) | [107](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L107) | [120](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L120) | [174](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L174) | [177](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L177) | [225](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L225) | [226](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L226) | [233](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L233) | [239](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L239) | [240](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L240) | [265](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L265) | [312](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L312) | [318](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L318) | [350](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L350) | [356](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L356) | [366](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L366)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

/// @audit - `rawHeader` variable
38: bytes memory rawHeader = quote.substring(0, 48)
/// @audit - `rawLocalEnclaveReport` variable
51: bytes memory rawLocalEnclaveReport = quote.substring(48, 384)
/// @audit - `localEnclaveReport` variable
52: V3Struct.EnclaveReport memory localEnclaveReport = parseEnclaveReport(rawLocalEnclaveReport)
/// @audit - `totalQuoteSize` variable
106: uint32 totalQuoteSize = 48 // header
            + 384 // local QE report
            + 64 // ecdsa256BitSignature
            + 64 // ecdsaAttestationKey
            + 384 // QE report
            + 64 // qeReportSignature
            + 2 // sizeof(v3Quote.v3AuthData.qeAuthData.parsedDataSize)
            + v3Quote.v3AuthData.qeAuthData.parsedDataSize + 2 // sizeof(v3Quote.v3AuthData.certification.certType)
            + 4 // sizeof(v3Quote.v3AuthData.certification.certDataSize)
            + v3Quote.v3AuthData.certification.certDataSize
/// @audit - `headerBytes` variable
119: bytes memory headerBytes = abi.encodePacked(
            header.version,
            header.attestationKeyType,
            header.teeType,
            header.qeSvn,
            header.pceSvn,
            header.qeVendorId,
            header.userData
        )
/// @audit - `upperDigit` variable
155: uint256 upperDigit = digits / 16
/// @audit - `lowerDigit` variable
156: uint256 lowerDigit = digits % 16
/// @audit - `certData` variable
224: bytes memory certData = rawAuthData.substring(offset, cert.certDataSize)
/// @audit - `rawQeReport` variable
229: bytes memory rawQeReport = rawAuthData.substring(128, 384)
/// @audit - `isvProdIdPackBE` variable
249: uint16 isvProdIdPackBE = (enclaveReport.isvProdId >> 8) | (enclaveReport.isvProdId << 8)
/// @audit - `isvSvnPackBE` variable
250: uint16 isvSvnPackBE = (enclaveReport.isvSvn >> 8) | (enclaveReport.isvSvn << 8)
/// @audit - `pemCertLib` variable
275: IPEMCertChainLib pemCertLib = PEMCertChainLib(pemCertLibAddr)
/// @audit - `parsedQuoteCerts` variable
276: IPEMCertChainLib.ECSha256Certificate[] memory parsedQuoteCerts
```
[38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L38) | [51](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L51) | [52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L52) | [106](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L106) | [119](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L119) | [155](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L155) | [156](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L156) | [224](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L224) | [229](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L229) | [249](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L249) | [250](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L250) | [275](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L275) | [276](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L276)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

/// @audit - `valueLength` variable
183: uint256 valueLength = ptr.ixl() + 1 - ptr.ixf()
```
[183](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L183)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

/// @audit - `inputlen` variable
95: uint256 inputlen = input.length
/// @audit - `inputlen` variable
243: uint256 inputlen = input.length
```
[95](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L95) | [243](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L243)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

/// @audit - `exponent` variable
89: bytes memory exponent = publicKey.substring(0, 3)
/// @audit - `modulus` variable
90: bytes memory modulus = publicKey.substring(3, publicKey.length - 3)
/// @audit - `exponent` variable
106: bytes memory exponent = publicKey.substring(0, 3)
/// @audit - `modulus` variable
107: bytes memory modulus = publicKey.substring(3, publicKey.length - 3)
/// @audit - `r` variable
126: uint256 r = uint256(bytes32(signature.substring(0, 32)))
/// @audit - `s` variable
127: uint256 s = uint256(bytes32(signature.substring(32, 32)))
/// @audit - `gx` variable
132: uint256 gx = uint256(bytes32(publicKey.substring(0, 32)))
/// @audit - `gy` variable
133: uint256 gy = uint256(bytes32(publicKey.substring(32, 32)))
/// @audit - `args` variable
136: bytes memory args = abi.encode(sha256(tbs), r, s, gx, gy)
```
[89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L89) | [90](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L90) | [106](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L106) | [107](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L107) | [126](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L126) | [127](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L127) | [132](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L132) | [133](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L133) | [136](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L136)
</details>

### [G-16] `abi.encodePacked `is more gas efficient than `abi.encode`

`abi.encode()` pads all elementary types to 32 bytes, whereas `abi.encodePacked()` will only use the minimal required memory to encode the data.
```solidity
    function testPacking() public pure returns (bytes memory) {
        // return abi.encode("string"); // 1120 gas
        // return abi.encodePacked("string"); // 913 gas
    }
```

<details>
<summary><i>18 issue instances in 16 files:</i></summary>

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

147: abi.encode(
                "PROVER_ASSIGNMENT",
                ITaikoL1(_taikoL1Address).getConfig().chainId,
                _taikoL1Address,
                address(this),
                _assignment.metaHash,
                _assignment.parentMetaHash,
                _blobHash,
                _assignment.feeToken,
                _assignment.expiry,
                _assignment.maxBlockId,
                _assignment.maxProposedIn,
                _assignment.tierFees
            )
```
[147](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L147)

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

126: abi.encode(deposits_)
213: abi.encode(meta_)
```
[126](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L126) | [213](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L213)

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

121: abi.encode(_meta)
```
[121](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L121)

```solidity
File: packages/protocol/contracts/L1/provers/GuardianProver.sol

46: abi.encode(_meta, _tran)
51: abi.encode(_meta, _tran, _proof)
```
[46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L46) | [51](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L51)

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

186: abi.encode(_chainId, _kind, _blockId)
```
[186](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L186)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

450: abi.encode("TAIKO_MESSAGE", _message)
```
[450](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L450)

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

281: abi.encode(ctoken_, _user, _op.to, _op.tokenIds, _op.amounts)
```
[281](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L281)

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

384: abi.encode(ctoken_, _user, _to, balanceChange_)
```
[384](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L384)

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

217: abi.encode(ctoken_, _user, _op.to, _op.tokenIds)
```
[217](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L217)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

183: abi.encode(
                "VERIFY_PROOF",
                ITaikoL1(taikoL1).getConfig().chainId,
                address(this),
                _tran,
                _newInstance,
                _prover,
                _metaHash
            )
```
[183](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L183)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

60: abi.encode(user, amount)
```
[60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L60)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

80: abi.encode(user, amount)
```
[80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L80)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

56: abi.encode(user, tokenIds)
```
[56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L56)

```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

68: abi.encode("CLAIM_TAIKO_AIRDROP", data)
```
[68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L68)

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

482: abi.encode(v3quote)
```
[482](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L482)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

136: abi.encode(sha256(tbs), r, s, gx, gy)
```
[136](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L136)
</details>

### [G-17] Consider Using `selfbalance()` Over `address(this).balance`

The `selfbalance()` function from Yul can be more gas-efficient than using `address(this).balance` in certain scenarios.
Although the Solidity compiler is sometimes optimized enough to handle this, manually switching to `selfbalance()` could yield gas savings.

Note: Always thoroughly test both approaches to confirm the actual gas savings.

<details>
<summary><i>6 issue instances in 3 files:</i></summary>

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

125: address(this).balance
126: address(this).balance
```
[125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L125) | [126](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L126)

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

253: address(this).balance
260: address(this).balance
261: address(this).balance
```
[253](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L253) | [260](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L260) | [261](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L261)

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

174: address(this).balance
```
[174](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L174)
</details>

### [G-18] Using `require()` instead of `assert()` safes gas

Since `assert()` can't contain any message, it is recommended to use `require()` without message instead.
Using `require()` saves 33 gas per call.
```solidity
    require(false); // 133 gas
    assert(false); // 166 gas 
```


<details>
<summary><i>4 issue instances in 3 files:</i></summary>

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

223: assert(tier.validityBond == 0)
224: assert(ts.validityBond == 0 && ts.contestBond == 0 && ts.contester == address(0))
```
[223](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L223) | [224](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L224)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

486: assert(_message.from != address(this))
```
[486](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L486)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

138: assert(success)
```
[138](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L138)
</details>

### [G-19] Use `assembly` to write mutable storage values

Writing to storage using `assembly` is more gas efficient.
```solidity
    function writeStorage() external {
        // storageNumber = 10; // 2358 gas
        // assembly {
        //     sstore(storageNumber.slot, 10) // 2350 gas
        // }
        // storageAddr = 0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc3; // 2411 gas
        // assembly {
        //     sstore(storageAddr.slot, 0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc3) // 2350 gas
        // }
    }
```

<details>
<summary><i>81 issue instances in 28 files:</i></summary>

```solidity
File: packages/protocol/contracts/common/AddressManager.sol

49: __addresses[_chainId][_name] = _newAddress
```
[49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L49)

```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

62: addressManager = _addressManager
```
[62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L62)

```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

70: __paused = _TRUE
79: __paused = _FALSE
111: __paused = _FALSE
125: __reentry = _reentry
```
[70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L70) | [79](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L79) | [111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L111) | [125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L125)

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

226: ts.prover = msg.sender
227: ts.blockHash = _tran.blockHash
228: ts.stateRoot = _tran.stateRoot
250: ts.contestBond = tier.contestBond
251: ts.contester = msg.sender
264: ts.timestamp = uint64(block.timestamp)
```
[226](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L226) | [227](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L227) | [228](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L228) | [250](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L250) | [251](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L251) | [264](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L264)

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

88: guardianIds[guardian] = guardians.length
94: minGuardians = _minGuardians
```
[88](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L88) | [94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L94)

```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

126: state.slotB.lastUnpausedAt = uint64(block.timestamp)
```
[126](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L126)

```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

73: ownerChainId = _ownerChainId
```
[73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L73)

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

91: l2Hashes[parentHeight] = blockhash(parentHeight)
96: gasExcess = _gasExcess
151: lastSyncedBlock = _l1BlockId
154: l2Hashes[parentId] = blockhash(parentId)
155: publicInputHash = publicInputHashNew
```
[91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L91) | [96](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L96) | [151](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L151) | [154](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L154) | [155](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L155)

```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

36: customConfig = _newConfig
37: gasExcess = _newGasExcess
```
[36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L36) | [37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L37)

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

58: isAuthorized[_addr] = _authorize
248: topBlockId[_chainId][_kind] = _blockId
```
[58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L58) | [248](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L248)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

92: proofReceipt[msgHash].receivedAt = _timestamp
110: addressBanned[_addr] = _ban
184: proofReceipt[msgHash].receivedAt = receivedAt
191: messageStatus[msgHash] = Status.RECALLED
243: proofReceipt[msgHash] = ProofReceipt({
                    receivedAt: receivedAt,
                    preferredExecutor: _message.gasLimit == 0 ? _message.destOwner : msg.sender
                })
518: messageStatus[_msgHash] = _status
549: __ctx = Context(_msgHash, _from, _srcChainId)
```
[92](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L92) | [110](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L110) | [184](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L184) | [191](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L191) | [243](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L243) | [518](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L518) | [549](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L549)

```solidity
File: packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

40: usdc = _usdc
```
[40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L40)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

73: srcToken = _srcToken
74: srcChainId = _srcChainId
75: __srcDecimals = _decimals
81: snapshooter = _snapshooter
```
[73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L73) | [74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L74) | [75](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L75) | [81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L81)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

49: migratingAddress = _migratingAddress
50: migratingInbound = _migratingInbound
```
[49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L49) | [50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L50)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

47: srcToken = _srcToken
48: srcChainId = _srcChainId
```
[47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L47) | [48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L48)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

56: srcToken = _srcToken
57: srcChainId = _srcChainId
58: __symbol = _symbol
59: __name = _name
```
[56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L56) | [57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L57) | [58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L58) | [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L59)

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

311: bridgedToCanonical[btoken_] = _ctoken
312: canonicalToBridged[_ctoken.chainId][_ctoken.addr] = btoken_
```
[311](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L311) | [312](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L312)

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

181: btokenBlacklist[btokenOld_] = true
188: bridgedToCanonical[_btokenNew] = _ctoken
189: canonicalToBridged[_ctoken.chainId][_ctoken.addr] = _btokenNew
422: bridgedToCanonical[btoken] = ctoken
423: canonicalToBridged[ctoken.chainId][ctoken.addr] = btoken
```
[181](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L181) | [188](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L188) | [189](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L189) | [422](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L422) | [423](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L423)

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

247: bridgedToCanonical[btoken_] = _ctoken
248: canonicalToBridged[_ctoken.chainId][_ctoken.addr] = btoken_
```
[247](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L247) | [248](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L248)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

213: addressRegistered[_instances[i]] = true
217: instances[nextInstanceId] = Instance(_instances[i], validSince)
229: instances[id] = Instance(newInstance, uint64(block.timestamp))
```
[213](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L213) | [217](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L217) | [229](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L229)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

41: token = _token
42: vault = _vault
```
[41](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L41) | [42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L42)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

69: token = _token
70: vault = _vault
71: withdrawalWindow = _withdrawalWindow
```
[69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L69) | [70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L70) | [71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L71)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

39: token = _token
40: vault = _vault
```
[39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L39) | [40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L40)

```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

73: isClaimed[hash] = true
91: claimStart = _claimStart
92: claimEnd = _claimEnd
93: merkleRoot = _merkleRoot
```
[73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L73) | [91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L91) | [92](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L92) | [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L93)

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

122: taikoToken = _taikoToken
125: costToken = _costToken
128: sharedVault = _sharedVault
142: recipients[_recipient].grant = _grant
```
[122](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L122) | [125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L125) | [128](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L128) | [142](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L142)

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

57: owner = msg.sender
66: _trustedUserMrSigner[_mrSigner] = _trusted
70: _trustedUserMrEnclave[_mrEnclave] = _trusted
84: _serialNumIsRevoked[index][serialNumBatch[i]] = true
111: tcbInfo[fmspc] = tcbInfoInput
119: qeIdentity = qeIdentityInput
123: _checkLocalEnclaveReport = !_checkLocalEnclaveReport
```
[57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L57) | [66](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L66) | [70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L70) | [84](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L84) | [111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L111) | [119](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L119) | [123](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L123)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

282: quoteCerts[i] = Base64.decode(string(quoteCerts[i]))
```
[282](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L282)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

21: ES256VERIFIER = es256Verifier
```
[21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L21)
</details>

### [G-20] Using `delete` on a `uint/int` variable is cheaper than assigning it to `0`

```solidity
function test() external {
    delete foo; // 5148 gas
    foo = 0; // 5156 gas
}
```

<details>
<summary><i>10 issue instances in 4 files:</i></summary>

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

190: meta_.txListByteOffset = 0
```
[190](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L190)

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

197: blk.livenessBond = 0
300: ts_.blockHash = 0
301: ts_.stateRoot = 0
302: ts_.validityBond = 0
306: ts_.tier = 0
307: ts_.contestations = 0
```
[197](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L197) | [300](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L300) | [301](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L301) | [302](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L302) | [306](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L306) | [307](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L307)

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

231: _grant.grantStart = 0
232: _grant.grantPeriod = 0
```
[231](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L231) | [232](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L232)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

336: tbsPtr = 0
```
[336](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L336)
</details>

### [G-21] Optimize Ether Transfers with `receive()` Function

Consider using `receive()` function instead of a specific `deposit()` (or similar) function.
If there are several functions in the contract that can receive Ether, it is recommended to use `receive()` for the most frequently used function.
```solidity
function deposit() external payable { // 5401 gas
    // your logic
}

receive() external payable {  // 5356 gas
    // your logic
}
```

The `receive()` or `fallback()` function can handle incoming Ether transfers directly, providing more gas-efficient way to manage deposits.

<details>
<summary><i>14 issue instances in 7 files:</i></summary>

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

62: function onBlockProposed(
        TaikoData.Block memory _blk,
        TaikoData.BlockMetadata memory _meta,
        bytes memory _data
    )
        external
        payable
        nonReentrant
        onlyFromNamed("taiko")
```
[62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L62)

```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

55: function proposeBlock(
        bytes calldata _params,
        bytes calldata _txList
    )
        external
        payable
        nonReentrant
        whenNotPaused
        returns (TaikoData.BlockMetadata memory meta_, TaikoData.EthDeposit[] memory deposits_)
119: function depositEtherToL2(address _recipient) external payable nonReentrant whenNotPaused
```
[55](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L55) | [119](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L119)

```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

36: function onMessageInvocation(bytes calldata _data)
        external
        payable
        whenNotPaused
        onlyFromNamed("bridge")
```
[36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L36)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

115: function sendMessage(Message calldata _message)
        external
        payable
        override
        nonReentrant
        whenNotPaused
        returns (bytes32 msgHash_, Message memory message_)
```
[115](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L115)

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

39: function sendToken(BridgeTransferOp memory _op)
        external
        payable
        nonReentrant
        whenNotPaused
        withValidOperation(_op)
        returns (IBridge.Message memory message_)
93: function onMessageInvocation(bytes calldata data) external payable nonReentrant whenNotPaused
127: function onMessageRecalled(
        IBridge.Message calldata message,
        bytes32 msgHash
    )
        external
        payable
        override
        nonReentrant
        whenNotPaused
```
[39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L39) | [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L93) | [127](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L127)

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

207: function sendToken(BridgeTransferOp calldata _op)
        external
        payable
        nonReentrant
        whenNotPaused
        returns (IBridge.Message memory message_)
253: function onMessageInvocation(bytes calldata _data)
        external
        payable
        nonReentrant
        whenNotPaused
285: function onMessageRecalled(
        IBridge.Message calldata _message,
        bytes32 _msgHash
    )
        external
        payable
        override
        nonReentrant
        whenNotPaused
```
[207](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L207) | [253](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L253) | [285](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L285)

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

26: function sendToken(BridgeTransferOp memory _op)
        external
        payable
        nonReentrant
        whenNotPaused
        withValidOperation(_op)
        returns (IBridge.Message memory message_)
77: function onMessageInvocation(bytes calldata _data)
        external
        payable
        nonReentrant
        whenNotPaused
110: function onMessageRecalled(
        IBridge.Message calldata _message,
        bytes32 _msgHash
    )
        external
        payable
        override
        nonReentrant
        whenNotPaused
```
[26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L26) | [77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L77) | [110](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L110)
</details>

### [G-22] Use `revert()` to gain maximum gas savings

If you dont need Error messages, or you want gain maximum gas savings - `revert()` is a cheapest way to revert transaction in terms of gas.
```solidity
    revert(); // 117 gas 
    require(false); // 132 gas
    revert CustomError(); // 157 gas
    assert(false); // 164 gas
    revert("Custom Error"); // 406 gas
    require(false, "Custom Error"); // 421 gas
```


<details>
<summary><i>244 issue instances in 50 files:</i></summary>

```solidity
File: packages/protocol/contracts/common/AddressManager.sol

48: revert AM_INVALID_PARAMS()
59: revert AM_UNSUPPORTED()
```
[48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L48) | [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L59)

```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

25: revert RESOLVER_DENIED()
60: revert RESOLVER_UNEXPECTED_CHAINID()
81: revert RESOLVER_INVALID_MANAGER()
86: revert RESOLVER_ZERO_ADDR(_chainId, _name)
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L25) | [60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L60) | [81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L81) | [86](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L86)

```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

42: revert RESOLVER_DENIED()
47: revert REENTRANT_CALL()
54: revert INVALID_PAUSE_STATUS()
59: revert INVALID_PAUSE_STATUS()
105: revert ZERO_ADDR_MANAGER()
```
[42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L42) | [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L47) | [54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L54) | [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L59) | [105](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L105)

```solidity
File: packages/protocol/contracts/libs/Lib4844.sol

40: revert POINT_X_TOO_LARGE()
41: revert POINT_Y_TOO_LARGE()
47: revert EVAL_FAILED_1()
49: revert EVAL_FAILED_2()
58: revert EVAL_FAILED_2()
```
[40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L40) | [41](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L41) | [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L47) | [49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L49) | [58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L58)

```solidity
File: packages/protocol/contracts/libs/LibAddress.sol

24: revert ETH_TRANSFER_FAILED()
36: revert ETH_TRANSFER_FAILED()
```
[24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L24) | [36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L36)

```solidity
File: packages/protocol/contracts/libs/LibTrieProof.sol

50: revert LTP_INVALID_ACCOUNT_PROOF()
64: revert LTP_INVALID_INCLUSION_PROOF()
```
[50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L50) | [64](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L64)

```solidity
File: packages/protocol/contracts/L1/gov/TaikoGovernor.sol

81: revert TG_INVALID_SIGNATURES_LENGTH()
```
[81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L81)

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

88: revert HOOK_ASSIGNMENT_EXPIRED()
97: revert HOOK_ASSIGNMENT_INVALID_SIG()
175: revert HOOK_TIER_NOT_FOUND()
```
[88](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L88) | [97](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L97) | [175](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L175)

```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

38: revert L1_INVALID_ETH_DEPOSIT()
150: revert L1_INVALID_ETH_DEPOSIT()
```
[38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L38) | [150](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L150)

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

82: revert L1_INVALID_PROVER()
94: revert L1_UNAUTHORIZED()
99: revert L1_TOO_MANY_BLOCKS()
109: revert L1_UNEXPECTED_PARENT()
142: revert L1_BLOB_FOR_DA_DISABLED()
145: revert L1_BLOB_REUSE_DISABLED()
149: revert L1_BLOB_NOT_REUSABLE()
159: revert L1_BLOB_NOT_FOUND()
172: revert L1_TXLIST_OFFSET()
182: revert L1_PROPOSER_NOT_EOA()
186: revert L1_INVALID_PARAM()
196: revert L1_TXLIST_SIZE()
246: revert L1_INVALID_HOOK()
269: revert L1_LIVENESS_BOND_NOT_RECEIVED()
```
[82](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L82) | [94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L94) | [99](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L99) | [109](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L109) | [142](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L142) | [145](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L145) | [149](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L149) | [159](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L159) | [172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L172) | [182](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L182) | [186](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L186) | [196](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L196) | [246](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L246) | [269](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L269)

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

223: assert(tier.validityBond == 0)
224: assert(ts.validityBond == 0 && ts.contestBond == 0 && ts.contester == address(0))
74: revert L1_INVALID_PAUSE_STATUS()
106: revert L1_INVALID_TRANSITION()
112: revert L1_INVALID_BLOCK_ID()
122: revert L1_BLOCK_MISMATCH()
135: revert L1_INVALID_TIER()
182: revert L1_MISSING_VERIFIER()
219: revert L1_ALREADY_PROVED()
239: revert L1_ALREADY_CONTESTED()
374: revert L1_ALREADY_PROVED()
420: revert L1_NOT_ASSIGNED_PROVER()
424: revert L1_ASSIGNED_PROVER_NOT_ALLOWED()
```
[223](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L223) | [224](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L224) | [74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L74) | [106](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L106) | [112](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L112) | [122](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L122) | [135](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L135) | [182](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L182) | [219](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L219) | [239](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L239) | [374](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L374) | [420](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L420) | [424](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L424)

```solidity
File: packages/protocol/contracts/L1/libs/LibUtils.sol

35: revert L1_INVALID_BLOCK_ID()
40: revert L1_BLOCK_MISMATCH()
43: revert L1_TRANSITION_NOT_FOUND()
64: revert L1_INVALID_BLOCK_ID()
86: revert L1_UNEXPECTED_TRANSITION_ID()
```
[35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L35) | [40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L40) | [43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L43) | [64](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L64) | [86](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L86)

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

54: revert L1_INVALID_CONFIG()
105: revert L1_BLOCK_MISMATCH()
111: revert L1_TRANSITION_ID_ZERO()
131: revert L1_BLOCK_MISMATCH()
```
[54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L54) | [105](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L105) | [111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L111) | [131](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L131)

```solidity
File: packages/protocol/contracts/L1/provers/GuardianProver.sol

45: revert INVALID_PROOF()
```
[45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L45)

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

64: revert INVALID_GUARDIAN_SET()
70: revert INVALID_MIN_GUARDIANS()
82: revert INVALID_GUARDIAN()
84: revert INVALID_GUARDIAN_SET()
113: revert INVALID_GUARDIAN()
```
[64](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L64) | [70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L70) | [82](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L82) | [84](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L84) | [113](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L113)

```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

29: revert L1_PROVING_PAUSED()
35: revert L1_RECEIVE_DISABLED()
90: revert L1_INVALID_BLOCK_ID()
```
[29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L29) | [35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L35) | [90](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L90)

```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

61: revert TKO_INVALID_ADDR()
79: revert TKO_INVALID_ADDR()
```
[61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L61) | [79](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L79)

```solidity
File: packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol

43: revert TIER_NOT_FOUND()
```
[43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L43)

```solidity
File: packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol

54: revert TIER_NOT_FOUND()
```
[54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L54)

```solidity
File: packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol

54: revert TIER_NOT_FOUND()
```
[54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L54)

```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

43: revert XCO_INVALID_TX_ID()
47: revert XCO_PERMISSION_DENIED()
51: revert XCO_TX_REVERTED()
71: revert XCO_INVALID_OWNER_CHAINID()
```
[43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L43) | [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L47) | [51](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L51) | [71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L71)

```solidity
File: packages/protocol/contracts/L2/Lib1559Math.sol

25: revert EIP1559_INVALID_PARAMS()
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L25)

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

83: revert L2_INVALID_CHAIN_ID()
93: revert L2_TOO_LATE()
120: revert L2_INVALID_PARAM()
123: revert L2_INVALID_SENDER()
133: revert L2_PUBLIC_INPUT_HASH_MISMATCH()
142: revert L2_BASEFEE_MISMATCH()
172: revert L2_INVALID_PARAM()
```
[83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L83) | [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L93) | [120](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L120) | [123](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L123) | [133](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L133) | [142](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L142) | [172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L172)

```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

33: revert L2_INVALID_CONFIG()
34: revert L2_INVALID_CONFIG()
```
[33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L33) | [34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L34)

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

36: revert SS_INVALID_SENDER()
41: revert SS_INVALID_VALUE()
57: revert SS_INVALID_STATE()
77: revert SS_UNAUTHORIZED()
95: revert SS_EMPTY_PROOF()
111: revert SS_INVALID_LAST_HOP_CHAINID()
115: revert SS_INVALID_MID_HOP_CHAINID()
132: revert SS_SIGNAL_NOT_FOUND()
172: revert SS_SIGNAL_NOT_FOUND()
232: revert SS_UNSUPPORTED()
```
[36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L36) | [41](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L41) | [57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L57) | [77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L77) | [95](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L95) | [111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L111) | [115](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L115) | [132](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L132) | [172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L172) | [232](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L232)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

486: assert(_message.from != address(this))
65: revert B_INVALID_CHAINID()
109: revert B_INVALID_STATUS()
125: revert B_INVALID_USER()
132: revert B_INVALID_CHAINID()
134: revert B_INVALID_CHAINID()
139: revert B_INVALID_VALUE()
166: revert B_STATUS_MISMATCH()
175: revert B_MESSAGE_NOT_SENT()
180: revert B_NOT_FAILED()
212: revert B_INVOCATION_TOO_EARLY()
227: revert B_STATUS_MISMATCH()
237: revert B_NOT_RECEIVED()
261: revert B_PERMISSION_DENIED()
305: revert B_INVOCATION_TOO_EARLY()
322: revert B_PERMISSION_DENIED()
327: revert B_NON_RETRIABLE()
406: revert B_INVALID_CONTEXT()
485: revert B_INVALID_GAS_LIMIT()
```
[486](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L486) | [65](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L65) | [109](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L109) | [125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L125) | [132](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L132) | [134](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L134) | [139](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L139) | [166](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L166) | [175](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L175) | [180](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L180) | [212](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L212) | [227](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L227) | [237](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L237) | [261](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L261) | [305](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L305) | [322](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L322) | [327](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L327) | [406](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L406) | [485](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L485)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

39: revert BTOKEN_UNAUTHORIZED()
147: revert BTOKEN_CANNOT_RECEIVE()
148: revert INVALID_PAUSE_STATUS()
```
[39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L39) | [147](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L147) | [148](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L148)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

46: revert BB_INVALID_PARAMS()
59: revert BB_MINT_DISALLOWED()
66: revert BB_PERMISSION_DENIED()
78: revert BB_PERMISSION_DENIED()
85: revert RESOLVER_DENIED()
```
[46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L46) | [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L59) | [66](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L66) | [78](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L78) | [85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L85)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

80: revert BTOKEN_INVALID_BURN()
125: revert BTOKEN_CANNOT_RECEIVE()
126: revert INVALID_PAUSE_STATUS()
```
[80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L80) | [125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L125) | [126](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L126)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

137: revert BTOKEN_CANNOT_RECEIVE()
138: revert INVALID_PAUSE_STATUS()
```
[137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L137) | [138](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L138)

```solidity
File: packages/protocol/contracts/tokenvault/BaseNFTVault.sol

142: revert VAULT_TOKEN_ARRAY_MISMATCH()
146: revert VAULT_MAX_TOKEN_PER_TXN_EXCEEDED()
149: revert VAULT_INVALID_TOKEN()
```
[142](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L142) | [146](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L146) | [149](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L149)

```solidity
File: packages/protocol/contracts/tokenvault/BaseVault.sol

24: revert VAULT_PERMISSION_DENIED()
55: revert VAULT_PERMISSION_DENIED()
65: revert VAULT_PERMISSION_DENIED()
```
[24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L24) | [55](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L55) | [65](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L65)

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

48: revert VAULT_INVALID_AMOUNT()
52: revert VAULT_INTERFACE_NOT_SUPPORTED()
108: revert VAULT_INVALID_TO()
```
[48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L48) | [52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L52) | [108](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L108)

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

159: revert VAULT_INVALID_NEW_BTOKEN()
162: revert VAULT_BTOKEN_BLACKLISTED()
165: revert VAULT_NOT_SAME_OWNER()
178: revert VAULT_CTOKEN_MISMATCH()
214: revert VAULT_INVALID_AMOUNT()
215: revert VAULT_INVALID_TOKEN()
216: revert VAULT_BTOKEN_BLACKLISTED()
267: revert VAULT_INVALID_TO()
```
[159](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L159) | [162](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L162) | [165](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L165) | [178](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L178) | [214](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L214) | [215](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L215) | [216](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L216) | [267](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L267)

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

35: revert VAULT_INVALID_AMOUNT()
39: revert VAULT_INTERFACE_NOT_SUPPORTED()
91: revert VAULT_INVALID_TO()
```
[35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L35) | [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L39) | [91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L91)

```solidity
File: packages/protocol/contracts/tokenvault/LibBridgedToken.sol

24: revert BTOKEN_INVALID_PARAMS()
```
[24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L24)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/Bytes.sol

25: require(_length + 31 >= _length, "slice_overflow")
26: require(_start + _length >= _start, "slice_overflow")
27: require(_bytes.length >= _start + _length, "slice_outOfBounds")
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L25) | [26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L26) | [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L27)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

37: require(
            _in.length > 0,
            "RLPReader: length of an RLP item must be greater than zero to be decodable"
        )
56: require(
            itemType == RLPItemType.LIST_ITEM,
            "RLPReader: decoded item type for list is not a list item"
        )
61: require(
            listOffset + listLength == _in.length,
            "RLPReader: list item has an invalid data remainder"
        )
112: require(
            itemType == RLPItemType.DATA_ITEM,
            "RLPReader: decoded item type for bytes is not a data item"
        )
117: require(
            _in.length == itemOffset + itemLength,
            "RLPReader: bytes value contains an invalid remainder"
        )
152: require(
            _in.length > 0,
            "RLPReader: length of an RLP item must be greater than zero to be decodable"
        )
172: require(
                _in.length > strLen,
                "RLPReader: length of content must be greater than string length (short string)"
            )
182: require(
                strLen != 1 || firstByteOfContent >= 0x80,
                "RLPReader: invalid prefix, single byte < 0x80 are not prefixed (short string)"
            )
192: require(
                _in.length > lenOfStrLen,
                "RLPReader: length of content must be > than length of string length (long string)"
            )
202: require(
                firstByteOfContent != 0x00,
                "RLPReader: length of content must not have any leading zeros (long string)"
            )
212: require(
                strLen > 55,
                "RLPReader: length of content must be greater than 55 bytes (long string)"
            )
217: require(
                _in.length > lenOfStrLen + strLen,
                "RLPReader: length of content must be greater than total length (long string)"
            )
228: require(
                _in.length > listLen,
                "RLPReader: length of content must be greater than list length (short list)"
            )
238: require(
                _in.length > lenOfListLen,
                "RLPReader: length of content must be > than length of list length (long list)"
            )
248: require(
                firstByteOfContent != 0x00,
                "RLPReader: length of content must not have any leading zeros (long list)"
            )
258: require(
                listLen > 55,
                "RLPReader: length of content must be greater than 55 bytes (long list)"
            )
263: require(
                _in.length > lenOfListLen + listLen,
                "RLPReader: length of content must be greater than total length (long list)"
            )
```
[37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L37) | [56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L56) | [61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L61) | [112](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L112) | [117](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L117) | [152](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L152) | [172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L172) | [182](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L182) | [192](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L192) | [202](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L202) | [212](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L212) | [217](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L217) | [228](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L228) | [238](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L238) | [248](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L248) | [258](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L258) | [263](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L263)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

77: require(_key.length > 0, "MerkleTrie: empty key")
89: require(currentKeyIndex <= key.length, "MerkleTrie: key index exceeds total key length")
93: require(
                    Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
                    "MerkleTrie: invalid root hash"
                )
99: require(
                    Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
                    "MerkleTrie: invalid large internal hash"
                )
105: require(
                    Bytes.equal(currentNode.encoded, currentNodeID),
                    "MerkleTrie: invalid internal node hash"
                )
119: require(
                        value_.length > 0,
                        "MerkleTrie: value length must be greater than zero (branch)"
                    )
125: require(
                        i == proof.length - 1,
                        "MerkleTrie: value node must be last node in proof (branch)"
                    )
150: require(
                    pathRemainder.length == sharedNibbleLength,
                    "MerkleTrie: path remainder must share all nibbles with key"
                )
162: require(
                        keyRemainder.length == sharedNibbleLength,
                        "MerkleTrie: key remainder must be identical to path remainder"
                    )
172: require(
                        value_.length > 0,
                        "MerkleTrie: value length must be greater than zero (leaf)"
                    )
178: require(
                        i == proof.length - 1,
                        "MerkleTrie: value node must be last node in proof (leaf)"
                    )
191: revert("MerkleTrie: received a node with an unknown prefix")
194: revert("MerkleTrie: received an unparseable node")
198: revert("MerkleTrie: ran out of proof elements")
```
[77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L77) | [89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L89) | [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L93) | [99](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L99) | [105](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L105) | [119](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L119) | [125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L125) | [150](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L150) | [162](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L162) | [172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L172) | [178](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L178) | [191](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L191) | [194](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L194) | [198](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L198)

```solidity
File: packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol

26: revert Overflow()
```
[26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L26)

```solidity
File: packages/protocol/contracts/verifiers/GuardianVerifier.sol

32: revert PERMISSION_DENIED()
```
[32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L32)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

107: revert SGX_INVALID_INSTANCE()
125: revert SGX_RA_NOT_SUPPORTED()
130: revert SGX_INVALID_ATTESTATION()
152: revert SGX_INVALID_PROOF()
161: revert SGX_INVALID_INSTANCE()
211: revert SGX_ALREADY_ATTESTED()
215: revert SGX_INVALID_INSTANCE()
```
[107](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L107) | [125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L125) | [130](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L130) | [152](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L152) | [161](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L161) | [211](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L211) | [215](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L215)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

41: revert WITHDRAWALS_NOT_ONGOING()
```
[41](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L41)

```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

37: revert CLAIM_NOT_ONGOING()
70: revert CLAIMED_ALREADY()
71: revert INVALID_PROOF()
```
[37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L37) | [70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L70) | [71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L71)

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

121: revert INVALID_PARAM()
124: revert INVALID_PARAM()
127: revert INVALID_PARAM()
136: revert INVALID_PARAM()
137: revert ALREADY_GRANTED()
154: revert NOTHING_TO_VOID()
169: revert INVALID_PARAM()
268: revert INVALID_GRANT()
275: revert INVALID_GRANT()
277: revert INVALID_GRANT()
278: revert INVALID_GRANT()
```
[121](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L121) | [124](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L124) | [127](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L127) | [136](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L136) | [137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L137) | [154](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L154) | [169](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L169) | [268](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L268) | [275](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L275) | [277](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L277) | [278](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L278)

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

61: require(msg.sender == owner, "onlyOwner")
```
[61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L61)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

77: require(
            localEnclaveReport.reserved3.length == 96 && localEnclaveReport.reserved4.length == 60
                && localEnclaveReport.reportData.length == 64,
            "local QE report has wrong length"
        )
82: require(
            pckSignedQeReport.reserved3.length == 96 && pckSignedQeReport.reserved4.length == 60
                && pckSignedQeReport.reportData.length == 64,
            "QE report has wrong length"
        )
87: require(
            v3Quote.v3AuthData.certification.certType == 5,
            "certType must be 5: Concatenated PCK Cert Chain (PEM formatted)"
        )
91: require(
            v3Quote.v3AuthData.certification.decodedCertDataArray.length == 3, "3 certs in chain"
        )
94: require(
            v3Quote.v3AuthData.ecdsa256BitSignature.length == 64
                && v3Quote.v3AuthData.ecdsaAttestationKey.length == 64
                && v3Quote.v3AuthData.qeReportSignature.length == 64,
            "Invalid ECDSA signature format"
        )
100: require(
            v3Quote.v3AuthData.qeAuthData.parsedDataSize
                == v3Quote.v3AuthData.qeAuthData.data.length,
            "Invalid QEAuthData size"
        )
116: require(totalQuoteSize >= MINIMUM_QUOTE_LENGTH, "Invalid quote size")
279: require(certParsedSuccessfully, "splitCertificateChain failed")
```
[77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L77) | [82](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L82) | [87](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L87) | [91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L91) | [94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L94) | [100](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L100) | [116](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L116) | [279](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L279)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

57: require(der[ptr.ixs()] == 0x03, "Not type BIT STRING")
67: require(der[ptr.ixs()] == 0x04, "Not type OCTET STRING")
88: require(der[ptr.ixs()] & 0x20 == 0x20, "Not a constructed type")
142: require(der[ptr.ixs()] == 0x02, "Not type INTEGER")
143: require(der[ptr.ixf()] & 0x80 == 0, "Not positive")
155: require(der[ptr.ixs()] == 0x02, "Not type INTEGER")
156: require(der[ptr.ixf()] & 0x80 == 0, "Not positive")
180: require(der[ptr.ixs()] == 0x03, "ixs Not type BIT STRING 0x03")
182: require(der[ptr.ixf()] == 0x00, "ixf Not 0")
```
[57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L57) | [67](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L67) | [88](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L88) | [142](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L142) | [143](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L143) | [155](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L155) | [156](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L156) | [180](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L180) | [182](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L182)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

25: require(offset + len <= self.length, "invalid offset")
199: require(idx + 2 <= self.length, "invalid idx")
212: require(idx + 4 <= self.length, "unexpected idx")
225: require(idx + 32 <= self.length, "unexpected idx")
238: require(idx + 20 <= self.length, "unexpected idx")
264: require(len <= 32, "unexpected len")
265: require(idx + len <= self.length, "unexpected idx")
293: require(offset + len <= self.length, "unexpected offset")
329: require(len <= 52, "unexpected len")
335: require(char >= 0x30 && char <= 0x7A, "invalid char")
337: require(decoded <= 0x20, "invalid decoded")
365: revert("unexpected len")
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L25) | [199](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L199) | [212](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L212) | [225](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L225) | [238](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L238) | [264](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L264) | [265](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L265) | [293](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L293) | [329](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L329) | [335](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L335) | [337](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L337) | [365](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L365)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

138: assert(success)
50: revert("Unsupported algorithm")
75: revert("Unsupported algorithm")
```
[138](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L138) | [50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L50) | [75](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L75)
</details>

### [G-23] Use local variables for emitting

Use the function/modifier's local copy of the state variable, rather than incurring an extra Gwarmaccess (100 gas).
In the unlikely event that the state variable hasn't already been used by the function/modifier, consider whether it is really necessary to include it in the event, given the fact that it incurs a Gcoldsload (2100 gas), or whether it can be passed in to or back out of the functions that do use it.

<details>
<summary><i>5 issue instances in 4 files:</i></summary>

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

95: emit GuardiansUpdated(version, _newGuardians)
```
[95](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L95)

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

157: emit Anchored(blockhash(parentId), gasExcess)
```
[157](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L157)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

63: emit MigratedTo(migratingAddress, _account, _amount)
80: emit MigratedTo(migratingAddress, _account, _amount)
```
[63](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L63) | [80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L80)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

220: emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince)
```
[220](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220)
</details>

### [G-24] `x.a = x.a + b` always cheaper than `x.a += b` for Structs

Using direct assignment operations (e.g., `x.a = x.a + b`) is more gas-efficient compared to compound assignment operations (e.g., `x.a += b`).
Examples:
```solidity
    // direct write to storage   -> 5337 gas
    // struct storage pointer    -> 5341 gas
    // memory struct             -> 4628 gas
    // memory function param     -> 1109 gas
    x.a += b;

    // direct write to storage   -> 5330 gas
    // struct storage pointer    -> 5334 gas
    // memory struct             -> 4625 gas
    // memory function param     -> 1106 gas
    x.a = struct.a + b;
```


<details>
<summary><i>5 issue instances in 3 files:</i></summary>

```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

101: deposits_[i].amount -= _fee
```
[101](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L101)

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

252: ts.contestations += 1
377: _ts.contestations += 1
```
[252](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L252) | [377](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L377)

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

213: r.amountWithdrawn += amountToWithdraw
214: r.costPaid += costToWithdraw
```
[213](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L213) | [214](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L214)
</details>

### [G-25] Initializers can be marked as payable

Payable functions cost less gas to execute, because the compiler does not have to add extra checks to ensure that no payment is provided.
Initializers can be safely marked as payable, because only the deployer or the factory contract would call the function without carrying any funds.

<details>
<summary><i>25 issue instances in 25 files:</i></summary>

```solidity
File: packages/protocol/contracts/common/AddressManager.sol

30: function init(address _owner) external initializer
```
[30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L30)

```solidity
File: packages/protocol/contracts/L1/gov/TaikoGovernor.sol

31: function init(
        address _owner,
        IVotesUpgradeable _token,
        TimelockControllerUpgradeable _timelock
    )
        external
        initializer
```
[31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L31)

```solidity
File: packages/protocol/contracts/L1/gov/TaikoTimelockController.sol

15: function init(address _owner, uint256 _minDelay) external initializer
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L15)

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

57: function init(address _owner, address _addressManager) external initializer
```
[57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L57)

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

47: function init(
        TaikoData.State storage _state,
        TaikoData.Config memory _config,
        bytes32 _genesisBlockHash
    )
        external
```
[47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L47)

```solidity
File: packages/protocol/contracts/L1/provers/GuardianProver.sol

25: function init(address _owner, address _addressManager) external initializer
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L25)

```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

42: function init(
        address _owner,
        address _addressManager,
        bytes32 _genesisBlockHash
    )
        external
        initializer
```
[42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L42)

```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

25: function init(
        address _owner,
        string calldata _name,
        string calldata _symbol,
        address _recipient
    )
        public
        initializer
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L25)

```solidity
File: packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol

15: function init(address _owner) external initializer
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L15)

```solidity
File: packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol

15: function init(address _owner) external initializer
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L15)

```solidity
File: packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol

15: function init(address _owner) external initializer
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L15)

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

71: function init(
        address _owner,
        address _addressManager,
        uint64 _l1ChainId,
        uint64 _gasExcess
    )
        external
        initializer
```
[71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L71)

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

48: function init(address _owner, address _addressManager) external initializer
```
[48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L48)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

75: function init(address _owner, address _addressManager) external initializer
```
[75](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L75)

```solidity
File: packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

38: function init(address _owner, address _addressManager, IUSDC _usdc) external initializer
```
[38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L38)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

52: function init(
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
```
[52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L52)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

31: function init(
        address _owner,
        address _addressManager,
        address _srcToken,
        uint256 _srcChainId,
        string memory _symbol,
        string memory _name
    )
        external
        initializer
```
[31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L31)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

38: function init(
        address _owner,
        address _addressManager,
        address _srcToken,
        uint256 _srcChainId,
        string memory _symbol,
        string memory _name
    )
        external
        initializer
```
[38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L38)

```solidity
File: packages/protocol/contracts/tokenvault/BaseVault.sol

32: function init(address _owner, address _addressManager) external initializer
```
[32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L32)

```solidity
File: packages/protocol/contracts/verifiers/GuardianVerifier.sol

18: function init(address _owner, address _addressManager) external initializer
```
[18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L18)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

83: function init(address _owner, address _addressManager) external initializer
```
[83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L83)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

27: function init(
        address _owner,
        uint64 _claimStart,
        uint64 _claimEnd,
        bytes32 _merkleRoot,
        address _token,
        address _vault
    )
        external
        initializer
```
[27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L27)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

54: function init(
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
```
[54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L54)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

25: function init(
        address _owner,
        uint64 _claimStart,
        uint64 _claimEnd,
        bytes32 _merkleRoot,
        address _token,
        address _vault
    )
        external
        initializer
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L25)

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

111: function init(
        address _owner,
        address _taikoToken,
        address _costToken,
        address _sharedVault
    )
        external
        initializer
```
[111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L111)
</details>

### [G-26] Using `constants` instead of `enum` can save gas

`Enum` is expensive and it is [more efficient to use constants](https://www.codehawks.com/finding/clm84992q02j9w9ruebun36d9) instead.
An illustrative example of this approach can be found in the [ReentrancyGuard.sol](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/181d518609a9f006fcb97af63e6952e603cf100e/contracts/utils/ReentrancyGuard.sol#L34-L35)

<details>
<summary><i>9 issue instances in 7 files:</i></summary>

```solidity
File: packages/protocol/contracts/signal/ISignalService.sol

13: enum CacheOption {
        CACHE_NOTHING,
        CACHE_SIGNAL_ROOT,
        CACHE_STATE_ROOT,
        CACHE_BOTH
    }
```
[13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L13)

```solidity
File: packages/protocol/contracts/bridge/IBridge.sol

9: enum Status {
        NEW,
        RETRIABLE,
        DONE,
        FAILED,
        RECALLED
    }
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L9)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

16: enum RLPItemType {
        DATA_ITEM,
        LIST_ITEM
    }
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L16)

```solidity
File: packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol

7: enum KeyType {
        RSA,
        ECDSA
    }
19: enum CertSigAlgorithm {
        Sha256WithRSAEncryption,
        Sha1WithRSAEncryption
    }
32: enum Algorithm {
        RS256,
        ES256,
        RS1
    }
```
[7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L7) | [19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L19) | [32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L32)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/EnclaveIdStruct.sol

26: enum EnclaveIdStatus {
        OK,
        SGX_ENCLAVE_REPORT_ISVSVN_REVOKED
    }
```
[26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/EnclaveIdStruct.sol#L26)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol

31: enum CRL {
        PCK,
        ROOT
    }
```
[31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L31)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol

19: enum TCBStatus {
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
[19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol#L19)
</details>

### [G-27] Merging Sequential `for` Loops with Identical Conditions

Contracts with multiple sequential `for` loops with identical conditions can be merged.
Merging these loops can significantly reduce gas consumption and enhance contract performance.
While this optimization streamlines the code and improves efficiency, it's important to balance this with code clarity and maintainability.
Thorough testing is recommended to ensure the merged loops function correctly without introducing complexity or bugs.
```solidity
    // two loops 16683 gas
    // one loop  14912 gas
    for (uint256 i = 0; i < inputLen; i++) {
        // do something
    }
    for (uint256 i = 0; i < inputLen; i++) {
        emit Event(i);
    }
```

<details>
<summary><i>8 issue instances in 3 files:</i></summary>

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

251: for (uint256 i; i < _op.tokenIds.length; ++i)
269: for (uint256 i; i < _op.tokenIds.length; ++i)
```
[251](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L251) | [269](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L269)

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

170: for (uint256 i; i < _tokenIds.length; ++i)
175: for (uint256 i; i < _tokenIds.length; ++i)
197: for (uint256 i; i < _op.tokenIds.length; ++i)
210: for (uint256 i; i < _op.tokenIds.length; ++i)
```
[170](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L170) | [175](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L175) | [197](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L197) | [210](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L210)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

152: for (uint256 i; i < digestAlgoWithParamLen; ++i)
158: for (uint256 i; i < digestAlgoWithParamLen; ++i)
```
[152](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L152) | [158](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L158)
</details>

### [G-28] Create variable outside the loop

Creating variables inside the loop consum more gas compared to declaring them outside and just reaffecting values to them inside the loop.
```solidity
    // uint256 outsideVar = anyValue;
    for (uint256 i = 0; i < 10; i++) {
        // outsideVar = value;     // 1984 gas
        uint256 insideVar = value; // 2012 gas 
    }
```

<details>
<summary><i>57 issue instances in 12 files:</i></summary>

```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

87: uint256 data = _state.ethDeposits[j % _config.ethDepositRingBufferSize]
93: uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount
```
[87](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L87) | [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L93)

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

140: TaikoData.TransitionState storage ts = _state.transitions[slot][tid]
178: uint256 bondToReturn = uint256(ts.validityBond) + blk.livenessBond
188: IERC20 tko = IERC20(_resolver.resolve("taiko_token", false))
```
[140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L140) | [178](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L178) | [188](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L188)

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

81: address guardian = _newGuardians[i]
```
[81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L81)

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

235: uint256 j = _blockId - i - 1
```
[235](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L235)

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

107: bytes32 signalRoot = _verifyHopProof(chainId, app, signal, value, hop, signalService)
108: bool isLastHop = i == hopProofs.length - 1
120: bool isFullProof = hop.accountProof.length > 0
124: bytes32 kind = isFullProof ? LibSignals.STATE_ROOT : LibSignals.SIGNAL_ROOT
```
[107](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L107) | [108](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L108) | [120](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L120) | [124](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L124)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

91: bytes32 msgHash = _msgHashes[i]
```
[91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L91)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

86: TrieNode memory currentNode = proof[i]
134: uint8 branchKey = uint8(key[currentKeyIndex])
135: RLPReader.RLPItem memory nextNode = currentNode.decoded[branchKey]
140: bytes memory path = _getNodePath(currentNode)
141: uint8 prefix = uint8(path[0])
142: uint8 offset = 2 - (prefix % 2)
143: bytes memory pathRemainder = Bytes.slice(path, offset)
144: bytes memory keyRemainder = Bytes.slice(key, currentKeyIndex)
145: uint256 sharedNibbleLength = _getSharedNibbleLength(pathRemainder, keyRemainder)
```
[86](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L86) | [134](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L134) | [135](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L135) | [140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L140) | [141](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L141) | [142](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L142) | [143](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L143) | [144](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L144) | [145](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L145)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

105: uint256 idx = _ids[i]
```
[105](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L105)

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

192: EnclaveIdStruct.TcbLevel memory tcb = enclaveId.tcbLevels[i]
215: TCBInfoStruct.TCBLevelObj memory current = tcb.tcbLevels[i]
216: bool pceSvnIsHigherOrGreater = pck.sgxExtension.pcesvn >= current.pcesvn
217: bool cpuSvnsAreHigherOrGreater = _isCpuSvnHigherOrGreater(
                pck.sgxExtension.sgxTcbCompSvnArr, current.sgxTcbCompSvnArr
            )
222: bool tcbIsRevoked = status == TCBInfoStruct.TCBStatus.TCB_REVOKED
260: IPEMCertChainLib.ECSha256Certificate memory issuer
292: bytes32 issuerPubKeyHash = keccak256(issuer.pubKey)
421: bool isPckCert = i == 0
422: bool certDecodedSuccessfully
```
[192](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L192) | [215](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L215) | [216](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L216) | [217](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L217) | [222](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L222) | [260](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L260) | [292](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L292) | [421](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L421) | [422](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L422)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

55: string memory input
61: uint256 increment
287: uint256 internalPtr = der.firstChildOf(tbsPtr)
295: uint256 extnValueParentPtr = der.rootOfOctetStringAt(internalPtr)
296: uint256 extnValuePtr = der.firstChildOf(extnValueParentPtr)
299: PCKTCBFlags memory flags
302: uint256 extnValueOidPtr = der.firstChildOf(extnValuePtr)
312: uint256 pceidPtr = der.nextSiblingOf(extnValueOidPtr)
318: uint256 fmspcPtr = der.nextSiblingOf(extnValueOidPtr)
302: uint256 extnValueOidPtr = der.firstChildOf(extnValuePtr)
312: uint256 pceidPtr = der.nextSiblingOf(extnValueOidPtr)
318: uint256 fmspcPtr = der.nextSiblingOf(extnValueOidPtr)
355: uint256 svnPtr = der.firstChildOf(svnParentPtr)
356: uint256 svnValuePtr = der.nextSiblingOf(svnPtr)
357: bytes memory svnValueBytes = der.bytesAt(svnValuePtr)
358: uint16 svnValue = svnValueBytes.length < 2
                ? uint16(bytes2(svnValueBytes)) / 256
                : uint16(bytes2(svnValueBytes))
366: uint256 cpusvn = uint256(svnValue)
```
[55](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L55) | [61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L61) | [287](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L287) | [295](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L295) | [296](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L296) | [299](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L299) | [302](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L302) | [312](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L312) | [318](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L318) | [302](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L302) | [312](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L312) | [318](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L318) | [355](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L355) | [356](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L356) | [357](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L357) | [358](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L358) | [366](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L366)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

154: uint256 digits = uint256(uint8(bytes1(encoded[i])))
155: uint256 upperDigit = digits / 16
156: uint256 lowerDigit = digits % 16
158: uint256 acc = lowerDigit * (16 ** (2 * i))
```
[154](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L154) | [155](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L155) | [156](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L156) | [158](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L158)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

81: uint256 a
82: uint256 b
89: uint256 mask
95: uint256 diff = (a & mask) - (b & mask)
334: bytes1 char = self[off + i]
```
[81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L81) | [82](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L82) | [89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L89) | [95](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L95) | [334](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L334)
</details>

### [G-29] Use `assembly` in place of `abi.decode` to extract calldata values more efficiently

Instead of using abi.decode, we can use assembly to decode our desired calldata values directly.
This will allow us to avoid decoding calldata values that we will not use.
[More details](https://code4rena.com/reports/2023-05-juicebox#g-04-use-assembly-in-place-of-abidecode-to-extract-calldata-values-more-efficiently)

<details>
<summary><i>3 issue instances in 3 files:</i></summary>

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

141: (CanonicalNFT memory ctoken,,, uint256[] memory tokenIds, uint256[] memory amounts) =
            abi.decode(data, (CanonicalNFT, address, address, uint256[], uint256[]))
```
[141](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L141)

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

299: (CanonicalERC20 memory ctoken,,, uint256 amount) =
            abi.decode(data, (CanonicalERC20, address, address, uint256))
```
[299](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L299)

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

124: (CanonicalNFT memory ctoken,,, uint256[] memory tokenIds) =
            abi.decode(data, (CanonicalNFT, address, address, uint256[]))
```
[124](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L124)
</details>

### [G-30] Redundant state variable getters

Getters for public state variables are automatically generated so there is no need to code them manually and waste gas.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

44: return customConfig
```
[44](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L44)
</details>

### [G-31] Shorten the array rather than copying to a new on

In Solidity, harnessing inline assembly empowers you to modify an array's length slot directly, obviating the need to duplicate elements into a new array of the desired size.
This method shines in terms of gas efficiency, as it sidesteps the computational overhead tied to array replication.
However, it's important to exercise caution when using this technique, as it bypasses the type-checking and safety features of high-level Solidity.

Always exercise due diligence to ensure that the array doesn't contain critical data beyond the adjusted length.
Data exceeding the new length will become inaccessible, yet it will still occupy storage space.

<details>
<summary><i>12 issue instances in 10 files:</i></summary>

```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

79: deposits_ = new TaikoData.EthDeposit[](0)
81: deposits_ =
                new TaikoData.EthDeposit[](numPending.min(_config.ethDepositMaxCountPerBlock))
```
[79](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L79) | [81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L81)

```solidity
File: packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol

48: tiers_ = new uint16[](2)
```
[48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L48)

```solidity
File: packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol

59: tiers_ = new uint16[](3)
```
[59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L59)

```solidity
File: packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol

59: tiers_ = new uint16[](3)
```
[59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L59)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

70: out_ = new RLPItem[](MAX_LIST_LENGTH)
```
[70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L70)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

207: proof_ = new TrieNode[](length)
```
[207](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L207)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

202: ids = new uint256[](_instances.length)
```
[202](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L202)

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

419: parsedQuoteCerts = new IPEMCertChainLib.ECSha256Certificate[](3)
```
[419](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L419)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

48: certs = new bytes[](size)
353: cpusvns = new uint256[](SGX_TCB_CPUSVN_SIZE)
```
[48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L48) | [353](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L353)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

280: parsedQuoteCerts = new IPEMCertChainLib.ECSha256Certificate[](3)
```
[280](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L280)
</details>

### [G-32] Nested for loops should be avoided due to high gas costs resulting from O^2 time complexity

In Solidity, avoiding nested for loops is a recommended practice primarily due to the high gas costs associated with them.
These loops can lead to quadratic (O^2) time complexity, especially when they iterate over large data sets or perform complex computations.
Since every operation in a smart contract consumes gas, and users pay for this gas, optimizing for lower gas usage is crucial.
Nested loops, which inherently have higher computational complexity, can significantly increase the gas costs of a contract.
To optimize for efficiency, it's advisable to minimize the use of loops, limit their range, and reduce computations within each loop iteration.
Alternative patterns like map/filter/reduce might often be cheaper than traditional for loops in terms of gas usage

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

301: while (!(flags.fmspcFound && flags.pceidFound && flags.tcbFound)
```
[301](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L301)
</details>

### [G-33] Use bytes32 in place of string

For strings of 32 char strings and below you can use bytes32 instead as it's more gas efficient

<details>
<summary><i>9 issue instances in 4 files:</i></summary>

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

108: string(
            abi.encodePacked(
                LibBridgedToken.buildURI(srcToken, srcChainId), Strings.toString(_tokenId)
            )
        )
```
[108](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L108)

```solidity
File: packages/protocol/contracts/tokenvault/LibBridgedToken.sol

36: string.concat("Bridged ", _name, unicode" (⭀", Strings.toString(_srcChainId), ")")
40: string.concat(_symbol, ".t")
53: string(
            abi.encodePacked(
                "ethereum:",
                Strings.toHexString(uint160(_srcToken), 20),
                "@",
                Strings.toString(_srcChainId),
                "/tokenURI?uint256="
            )
        )
```
[36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L36) | [40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L40) | [53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L53)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

49: string(pemChain)
119: string(der.bytesAt(issuerPtr))
151: string(der.bytesAt(subjectPtr))
241: string(delimiter)
```
[49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L49) | [119](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L119) | [151](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L151) | [241](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L241)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

282: string(quoteCerts[i])
```
[282](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L282)
</details>

### [G-34] Using `delete` on a `bool` variable is cheaper than assigning it to `false`

```solidity
function test() external {
    delete bar; // 5184 gas
    bar = false; // 5208 gas
}
```

<details>
<summary><i>2 issue instances in 2 files:</i></summary>

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

495: success_ = false
```
[495](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L495)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

129: hasNullParam = false
```
[129](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L129)
</details>

### [G-35] Use `Array.unsafeAccess()` to avoid repeated array length checks

When using storage arrays, solidity adds an internal lookup of the array's length (a Gcoldsload 2100 gas) to ensure you don't read past the array's end.
You can avoid this lookup by using `Array.unsafeAccess()` in cases where the length has already been checked, as is the case with the instances below.

<details>
<summary><i>29 issue instances in 16 files:</i></summary>

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

172: for (uint256 i; i < _tierFees.length; ++i) {
```
[172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L172)

```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

86: for (uint256 i; i < deposits_.length;) {
```
[86](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L86)

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

244: for (uint256 i; i < params.hookCalls.length; ++i) {
```
[244](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L244)

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

74: for (uint256 i; i < guardians.length; ++i) {
80: for (uint256 i = 0; i < _newGuardians.length; ++i) {
```
[74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L74) | [80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L80)

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

104: for (uint256 i; i < hopProofs.length; ++i) {
```
[104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L104)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

90: for (uint256 i; i < _msgHashes.length; ++i) {
```
[90](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L90)

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

47: for (uint256 i; i < _op.amounts.length; ++i) {
251: for (uint256 i; i < _op.tokenIds.length; ++i) {
269: for (uint256 i; i < _op.tokenIds.length; ++i) {
```
[47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L47) | [251](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L251) | [269](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L269)

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

34: for (uint256 i; i < _op.tokenIds.length; ++i) {
170: for (uint256 i; i < _tokenIds.length; ++i) {
175: for (uint256 i; i < _tokenIds.length; ++i) {
197: for (uint256 i; i < _op.tokenIds.length; ++i) {
210: for (uint256 i; i < _op.tokenIds.length; ++i) {
```
[34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L34) | [170](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L170) | [175](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L175) | [197](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L197) | [210](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L210)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

66: for (uint256 j = 0; j < out_.length; j++) {
```
[66](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

85: for (uint256 i = 0; i < proof.length; i++) {
```
[85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

104: for (uint256 i; i < _ids.length; ++i) {
210: for (uint256 i; i < _instances.length; ++i) {
```
[104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L104) | [210](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

59: for (uint256 i; i < tokenIds.length; ++i) {
```
[59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59)

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

80: for (uint256 i; i < serialNumBatch.length; ++i) {
95: for (uint256 i; i < serialNumBatch.length; ++i) {
191: for (uint256 i; i < enclaveId.tcbLevels.length; ++i) {
214: for (uint256 i; i < tcb.tcbLevels.length; ++i) {
```
[80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L80) | [95](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L95) | [191](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L191) | [214](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L214)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

244: for (uint256 i; i < split.length; ++i) {
```
[244](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L244)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

153: for (uint256 i; i < encoded.length; ++i) {
```
[153](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L153)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

174: for (uint256 i; i < _sha256.length; ++i) {
283: for (uint256 i; i < sha1Prefix.length; ++i) {
290: for (uint256 i; i < _sha1.length; ++i) {
```
[174](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L174) | [283](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L283) | [290](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L290)
</details>

### [G-36] Counting down when iterating, saves gas

Counting down saves 6 gas per loop, since checks for zero are more efficient than checks against any other value.

<details>
<summary><i>45 issue instances in 18 files:</i></summary>

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

172: for (uint256 i; i < _tierFees.length; ++i) {
```
[172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L172)

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

244: for (uint256 i; i < params.hookCalls.length; ++i) {
```
[244](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L244)

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

74: for (uint256 i; i < guardians.length; ++i) {
80: for (uint256 i = 0; i < _newGuardians.length; ++i) {
133: for (uint256 i; i < guardiansLength; ++i) {
```
[74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L74) | [80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L80) | [133](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L133)

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

234: for (uint256 i; i < 255 && _blockId >= i + 1; ++i) {
```
[234](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L234)

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

104: for (uint256 i; i < hopProofs.length; ++i) {
```
[104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L104)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

90: for (uint256 i; i < _msgHashes.length; ++i) {
```
[90](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L90)

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

47: for (uint256 i; i < _op.amounts.length; ++i) {
251: for (uint256 i; i < _op.tokenIds.length; ++i) {
269: for (uint256 i; i < _op.tokenIds.length; ++i) {
```
[47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L47) | [251](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L251) | [269](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L269)

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

34: for (uint256 i; i < _op.tokenIds.length; ++i) {
170: for (uint256 i; i < _tokenIds.length; ++i) {
175: for (uint256 i; i < _tokenIds.length; ++i) {
197: for (uint256 i; i < _op.tokenIds.length; ++i) {
210: for (uint256 i; i < _op.tokenIds.length; ++i) {
```
[34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L34) | [170](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L170) | [175](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L175) | [197](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L197) | [210](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L210)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

46: for (i = 1; i <= lenLen; i++) {
59: for (; i < 32; i++) {
66: for (uint256 j = 0; j < out_.length; j++) {
```
[46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L46) | [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L59) | [66](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

85: for (uint256 i = 0; i < proof.length; i++) {
```
[85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

104: for (uint256 i; i < _ids.length; ++i) {
210: for (uint256 i; i < _instances.length; ++i) {
```
[104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L104) | [210](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

59: for (uint256 i; i < tokenIds.length; ++i) {
```
[59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59)

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

80: for (uint256 i; i < serialNumBatch.length; ++i) {
95: for (uint256 i; i < serialNumBatch.length; ++i) {
191: for (uint256 i; i < enclaveId.tcbLevels.length; ++i) {
214: for (uint256 i; i < tcb.tcbLevels.length; ++i) {
240: for (uint256 i; i < CPUSVN_LENGTH; ++i) {
259: for (uint256 i; i < n; ++i) {
420: for (uint256 i; i < 3; ++i) {
```
[80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L80) | [95](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L95) | [191](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L191) | [214](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L214) | [240](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L240) | [259](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L259) | [420](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L420)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

54: for (uint256 i; i < size; ++i) {
244: for (uint256 i; i < split.length; ++i) {
354: for (uint256 i; i < SGX_TCB_CPUSVN_SIZE + 1; ++i) {
```
[54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L54) | [244](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L244) | [354](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L354)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

153: for (uint256 i; i < encoded.length; ++i) {
281: for (uint256 i; i < 3; ++i) {
```
[153](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L153) | [281](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L281)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

333: for (uint256 i; i < len; ++i) {
```
[333](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L333)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

140: for (uint256 i = 2; i < 2 + paddingLen; ++i) {
152: for (uint256 i; i < digestAlgoWithParamLen; ++i) {
158: for (uint256 i; i < digestAlgoWithParamLen; ++i) {
174: for (uint256 i; i < _sha256.length; ++i) {
273: for (uint256 i = 2; i < 2 + paddingLen; ++i) {
283: for (uint256 i; i < sha1Prefix.length; ++i) {
290: for (uint256 i; i < _sha1.length; ++i) {
```
[140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L140) | [152](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L152) | [158](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L158) | [174](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L174) | [273](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L273) | [283](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L283) | [290](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L290)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

48: for (uint16 i = 1970; i < year; ++i) {
59: for (uint8 i = 1; i < month; ++i) {
```
[48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L48) | [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L59)
</details>

### [G-37] `>=` costs less gas than `>`

The compiler uses opcodes GT and ISZERO for solidity code that uses >, but only requires LT for >=, which saves 3 gas. If < is being used, the condition can be inverted.
In cases where a for-loop is being used, one can count down rather than up, in order to use the optimal operator.

<details>
<summary><i>15 issue instances in 9 files:</i></summary>

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

125: if (address(this).balance > 0) {
```
[125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L125)

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

192: bool returnLivenessBond = blk.livenessBond > 0 && _proof.data.length == 32
```
[192](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L192)

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

212: if (numBlocksVerified > 0) {
```
[212](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L212)

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

262: if (gasExcess > 0) {
275: if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {
279: if (numL1Blocks > 0) {
```
[262](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L262) | [275](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L275) | [279](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L279)

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

120: bool isFullProof = hop.accountProof.length > 0;
```
[120](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L120)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

38: _in.length > 0,
153: _in.length > 0,
```
[38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L38) | [153](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L153)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

77: require(_key.length > 0, "MerkleTrie: empty key");
120: value_.length > 0,
173: value_.length > 0,
```
[77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L77) | [120](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L120) | [173](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L173)

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

275: if (_cliff > 0) revert INVALID_GRANT();
277: if (_cliff > 0 && _cliff <= _start) revert INVALID_GRANT();
```
[275](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L275) | [277](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L277)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

56: if (i > 0) {
```
[56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L56)
</details>

### [G-38] Consider pre-calculating the address of `address(this)` to save gas

Use foundry's script.sol or solady's LibRlp.sol to save the value in a constant, which will avoid having to spend gas to push the value on the stack every time it's used.

<details>
<summary><i>40 issue instances in 16 files:</i></summary>

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

125: if (address(this).balance > 0) {
126: taikoL1Address.sendEther(address(this).balance);
151: address(this),
```
[125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L125) | [126](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L126) | [151](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L151)

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

238: uint256 tkoBalance = tko.balanceOf(address(this));
253: IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }(
260: if (address(this).balance != 0) {
261: msg.sender.sendEther(address(this).balance);
268: if (tko.balanceOf(address(this)) != tkoBalance + _config.livenessBond) {
```
[238](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L238) | [253](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L253) | [260](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L260) | [261](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L261) | [268](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L268)

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

242: tko.transferFrom(msg.sender, address(this), tier.contestBond);
384: _tko.transferFrom(msg.sender, address(this), _tier.validityBond - reward);
```
[242](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L242) | [384](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L384)

```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

61: if (_to == address(this)) revert TKO_INVALID_ADDR();
79: if (_to == address(this)) revert TKO_INVALID_ADDR();
```
[61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L61) | [79](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L79)

```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

50: (bool success,) = address(this).call(txdata);
```
[50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L50)

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

174: _to.sendEther(address(this).balance);
176: IERC20(_token).safeTransfer(_to, IERC20(_token).balanceOf(address(this)));
```
[174](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L174) | [176](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L176)

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

112: signalService = address(this);
131: if (value == 0 || value != _loadSignalValue(address(this), signal)) {
149: return _loadSignalValue(address(this), signal) == _chainData;
171: chainData_ = _loadSignalValue(address(this), signal);
245: _sendSignal(address(this), signal_, _chainData);
```
[112](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L112) | [131](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L131) | [149](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L149) | [171](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L171) | [245](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L245)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

174: if (!ISignalService(signalService).isSignalSent(address(this), msgHash)) {
196: _storeContext(msgHash, address(this), _message.srcChainId);
270: _message.to == address(0) || _message.to == address(this)
343: _app: address(this),
486: assert(_message.from != address(this));
```
[174](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L174) | [196](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L196) | [270](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L270) | [343](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L343) | [486](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L486)

```solidity
File: packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

48: usdc.transferFrom(_from, address(this), _amount);
```
[48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L48)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

147: if (_to == address(this)) revert BTOKEN_CANNOT_RECEIVE();
```
[147](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L147)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

125: if (_to == address(this)) revert BTOKEN_CANNOT_RECEIVE();
```
[125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L125)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

137: if (_to == address(this)) revert BTOKEN_CANNOT_RECEIVE();
```
[137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L137)

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

108: if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();
226: IERC1155(token).safeBatchTransferFrom(address(this), to, tokenIds, amounts, "");
272: to: address(this),
```
[108](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L108) | [226](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L226) | [272](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L272)

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

267: if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();
378: uint256 _balance = t.balanceOf(address(this));
379: t.safeTransferFrom({ from: msg.sender, to: address(this), value: _amount });
380: balanceChange_ = t.balanceOf(address(this)) - _balance;
```
[267](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L267) | [378](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L378) | [379](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L379) | [380](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L380)

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

91: if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();
171: IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);
211: t.safeTransferFrom(_user, address(this), _op.tokenIds[i]);
```
[91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L91) | [171](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L171) | [211](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L211)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

186: address(this),
```
[186](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L186)
</details>

### [G-39] Call `msg.sender` directly instead of caching it

In the instance below, instead of caching `msg.sender` and incurring unnecessary stack manipulation, we can call `msg.sender` directly.
```solidity
/// 3047 gas
function test() external {
    internalFunc(msg.sender);
    internalFunc(msg.sender);
    internalFunc(msg.sender);
}
// 3061 gas
function test() external {
    address callerLocal = msg.sender;
    internalFunc(callerLocal);
    internalFunc(callerLocal);
    internalFunc(callerLocal);
}
```

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

93: address taikoL1Address = msg.sender
```
[93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L93)
</details>

### [G-40] Use `unchecked` for Non-Loop Increment/Decrement Operations

Disclaimer: `You should be sure that underflow is not possible `
Using `unchecked` increments can save gas by bypassing the built-in overflow checks.
This can save 30-40 gas per iteration.
It is recommended to use unchecked increments when overflow is not possible.

<details>
<summary><i>13 issue instances in 9 files:</i></summary>

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

244: ++i
```
[244](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L244)

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

92: ++version
```
[92](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L92)

```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

53: nextTxId++
```
[53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L53)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

144: nextMessageId++
```
[144](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L144)

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

170: ++i
175: ++i
```
[170](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L170) | [175](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L175)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

40: lenLen++
46: i++
67: i++
```
[40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L40) | [46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L46) | [67](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L67)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

222: nextInstanceId++
```
[222](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L222)

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

420: ++i
```
[420](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L420)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

152: ++i
158: ++i
```
[152](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L152) | [158](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L158)
</details>

### [G-41] Using `this` to access functions results in an external call, wasting gas

Using `this.<fn>()` to call an external function from within the contract unnecessarily wastes gas. This is because calling an external function requires a gas overhead of 100 gas.

Instead, you can reduce the gas cost by making the function public and calling it directly without `this`. The Ethereum Virtual Machine (EVM) does not require additional gas for calling public functions internally.

Always aim for efficient gas usage when writing Solidity contracts to optimize for cost and performance.

<details>
<summary><i>10 issue instances in 7 files:</i></summary>

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

125: if (address(this).balance > 0) {
126: taikoL1Address.sendEther(address(this).balance);
```
[125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L125) | [126](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L126)

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

253: IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }(
260: if (address(this).balance != 0) {
261: msg.sender.sendEther(address(this).balance);
```
[253](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L253) | [260](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L260) | [261](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L261)

```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

50: (bool success,) = address(this).call(txdata);
```
[50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L50)

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

174: _to.sendEther(address(this).balance);
```
[174](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L174)

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

281: this.onMessageInvocation, abi.encode(ctoken_, _user, _op.to, _op.tokenIds, _op.amounts)
```
[281](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L281)

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

384: this.onMessageInvocation, abi.encode(ctoken_, _user, _to, balanceChange_)
```
[384](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L384)

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

217: this.onMessageInvocation, abi.encode(ctoken_, _user, _op.to, _op.tokenIds)
```
[217](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L217)
</details>

### [G-42] Constructors can be marked `payable`

Payable functions cost less gas to execute, since the compiler does not have to add extra checks to ensure that a payment wasn't provided.

A constructor can safely be marked as `payable`, since only the deployer would be able to pass funds, and the project itself would not pass any funds. 
T
his could save an average of about 21 gas per call, in addition to the extra deployment cost.

<details>
<summary><i>3 issue instances in 3 files:</i></summary>

```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

64: constructor() {
```
[64](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L64)

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

53: constructor(address sigVerifyLibAddr, address pemCertLibAddr) {
```
[53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L53)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

19: constructor(address es256Verifier) {
```
[19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L19)
</details>

### [G-43] Split `revert` checks to save gas

Using boolean operators in a single `if() revert` statement can consume more gas than necessary.
Consider splitting these statements to save gas.

<details>
<summary><i>26 issue instances in 16 files:</i></summary>

```solidity
File: packages/protocol/contracts/libs/Lib4844.sol

57: if (uint256(first) != FIELD_ELEMENTS_PER_BLOB || uint256(second) != BLS_MODULUS) {
            revert EVAL_FAILED_2();
```
[57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L57)

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

81: if (
            block.timestamp > assignment.expiry
                || assignment.metaHash != 0 && _blk.metaHash != assignment.metaHash
                || assignment.parentMetaHash != 0 && _meta.parentMetaHash != assignment.parentMetaHash
                || assignment.maxBlockId != 0 && _meta.id > assignment.maxBlockId
                || assignment.maxProposedIn != 0 && block.number > assignment.maxProposedIn
        ) {
            revert HOOK_ASSIGNMENT_EXPIRED();
```
[81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L81)

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

195: if (meta_.txListByteSize == 0 || meta_.txListByteSize > _config.blockMaxTxListBytes) {
            revert L1_TXLIST_SIZE();
```
[195](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L195)

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

105: if (_tran.parentHash == 0 || _tran.blockHash == 0 || _tran.stateRoot == 0) {
            revert L1_INVALID_TRANSITION();
111: if (_meta.id <= b.lastVerifiedBlockId || _meta.id >= b.numBlocks) {
            revert L1_INVALID_BLOCK_ID();
121: if (blk.blockId != _meta.id || blk.metaHash != keccak256(abi.encode(_meta))) {
            revert L1_BLOCK_MISMATCH();
134: if (_proof.tier == 0 || _proof.tier < _meta.minTier || _proof.tier < ts.tier) {
            revert L1_INVALID_TIER();
```
[105](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L105) | [111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L111) | [121](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L121) | [134](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L134)

```solidity
File: packages/protocol/contracts/L1/libs/LibUtils.sol

34: if (_blockId < b.lastVerifiedBlockId || _blockId >= b.numBlocks) {
            revert L1_INVALID_BLOCK_ID();
```
[34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L34)

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

63: if (_newGuardians.length < MIN_NUM_GUARDIANS || _newGuardians.length > type(uint8).max) {
            revert INVALID_GUARDIAN_SET();
68: if (_minGuardians < (_newGuardians.length + 1) >> 1 || _minGuardians > _newGuardians.length)
        {
            revert INVALID_MIN_GUARDIANS();
```
[63](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L63) | [68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L68)

```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

46: if (ctx.srcChainId != ownerChainId || ctx.from != owner()) {
            revert XCO_PERMISSION_DENIED();
70: if (_ownerChainId == 0 || _ownerChainId == block.chainid) {
            revert XCO_INVALID_OWNER_CHAINID();
```
[46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L46) | [70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L70)

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

81: if (block.chainid <= 1 || block.chainid > type(uint64).max) {
            revert L2_INVALID_CHAIN_ID();
116: if (
            _l1BlockHash == 0 || _l1StateRoot == 0 || _l1BlockId == 0
                || (block.number != 1 && _parentGasUsed == 0)
        ) {
            revert L2_INVALID_PARAM();
```
[81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L81) | [116](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L116)

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

114: if (hop.chainId == 0 || hop.chainId == block.chainid) {
                    revert SS_INVALID_MID_HOP_CHAINID();
130: if (value == 0 || value != _loadSignalValue(address(this), signal)) {
            revert SS_SIGNAL_NOT_FOUND();
```
[114](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L114) | [130](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L130)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

124: if (_message.srcOwner == address(0) || _message.destOwner == address(0)) {
            revert B_INVALID_USER();
405: if (ctx_.msgHash == 0 || ctx_.msgHash == bytes32(PLACEHOLDER)) {
            revert B_INVALID_CONTEXT();
```
[124](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L124) | [405](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L405)

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

108: if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();
```
[108](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L108)

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

158: if (_btokenNew == address(0) || bridgedToCanonical[_btokenNew].addr != address(0)) {
            revert VAULT_INVALID_NEW_BTOKEN();
174: if (
                ctoken.decimals != _ctoken.decimals
                    || keccak256(bytes(ctoken.symbol)) != keccak256(bytes(_ctoken.symbol))
                    || keccak256(bytes(ctoken.name)) != keccak256(bytes(_ctoken.name))
            ) revert VAULT_CTOKEN_MISMATCH();
267: if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();
```
[158](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L158) | [174](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L174) | [267](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L267)

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

91: if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();
```
[91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L91)

```solidity
File: packages/protocol/contracts/tokenvault/LibBridgedToken.sol

20: if (
            _srcToken == address(0) || _srcChainId == 0 || _srcChainId == block.chainid
                || bytes(_symbol).length == 0 || bytes(_name).length == 0
        ) {
            revert BTOKEN_INVALID_PARAMS();
```
[20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L20)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

40: if (claimEnd > block.timestamp || claimEnd + withdrawalWindow < block.timestamp) {
            revert WITHDRAWALS_NOT_ONGOING();
```
[40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L40)

```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

34: if (
            merkleRoot == 0x0 || claimStart == 0 || claimEnd == 0 || claimStart > block.timestamp
                || claimEnd < block.timestamp
        ) revert CLAIM_NOT_ONGOING();
```
[34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L34)
</details>

### [G-44] Multiple accesses of a mapping/array should use a local variable cache

Leveraging a local variable to cache these values when accessed more than once can yield a gas saving of approximately 42 units per access.
This reduction is attributed to eliminating the need for recalculating the key's keccak256 hash (which costs Gkeccak256 - 30 gas) and the associated stack operations.
For arrays, this also prevents the overhead of re-computing offsets in memory or calldata.

<details>
<summary><i>25 issue instances in 8 files:</i></summary>

```solidity
File: packages/protocol/contracts/common/AddressManager.sol

/// @audit `__addresses[_chainId]` is used 2 times
47: address oldAddress = __addresses[_chainId][_name];
49: __addresses[_chainId][_name] = _newAddress;
```
[47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L47) | [49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L49)

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

/// @audit `_approvals[version]` is used 2 times
116: _approvals[version][_hash] |= 1 << (id - 1);
119: uint256 _approval = _approvals[version][_hash];
```
[116](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L116) | [119](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L119)

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

/// @audit `topBlockId[_chainId]` is used 2 times
247: if (topBlockId[_chainId][_kind] < _blockId) {
248: topBlockId[_chainId][_kind] = _blockId;
```
[247](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L247) | [248](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L248)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

/// @audit `proofReceipt[msgHash]` is used 2 times
168: uint64 receivedAt = proofReceipt[msgHash].receivedAt;
184: proofReceipt[msgHash].receivedAt = receivedAt;
/// @audit `proofReceipt[msgHash]` is used 2 times
230: uint64 receivedAt = proofReceipt[msgHash].receivedAt;
250: if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) {
```
[168](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L168) | [184](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L184) | [230](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L230) | [250](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L250)

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

/// @audit `canonicalToBridged[_ctoken.chainId]` is used 2 times
168: btokenOld_ = canonicalToBridged[_ctoken.chainId][_ctoken.addr];
189: canonicalToBridged[_ctoken.chainId][_ctoken.addr] = _btokenNew;
/// @audit `bridgedToCanonical[_token]` is used 2 times
358: if (bridgedToCanonical[_token].addr != address(0)) {
359: ctoken_ = bridgedToCanonical[_token];
```
[168](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L168) | [189](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L189) | [358](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L358) | [359](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L359)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

/// @audit `instances[idx]` is used 2 times
107: if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();
109: emit InstanceDeleted(idx, instances[idx].addr);
/// @audit `addressRegistered[_instances[i]` is used 2 times
211: if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();
213: addressRegistered[_instances[i]] = true;
/// @audit `instances[id]` is used 3 times
235: if (instance != instances[id].addr) return false;
236: return instances[id].validSince <= block.timestamp
237: && block.timestamp <= instances[id].validSince + INSTANCE_EXPIRY;
```
[107](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L107) | [109](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L109) | [211](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L211) | [213](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L213) | [235](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L235) | [236](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L236) | [237](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L237)

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

/// @audit `recipients[_recipient]` is used 2 times
137: if (recipients[_recipient].grant.amount != 0) revert ALREADY_GRANTED();
142: recipients[_recipient].grant = _grant;
```
[137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L137) | [142](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L142)

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

/// @audit `_serialNumIsRevoked[index]` is used 2 times
81: if (_serialNumIsRevoked[index][serialNumBatch[i]]) {
84: _serialNumIsRevoked[index][serialNumBatch[i]] = true;
```
[81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L81) | [84](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L84)
</details>

### [G-45] Reduce deployment costs by tweaking contracts' metadata

The Solidity compiler appends 53 bytes of metadata to the smart contract code which translates to an extra 10,600 gas (200 per bytecode) + the calldata cost (16 gas per non-zero bytes, 4 gas per zero-byte).
This translates to up to 848 additional gas in calldata cost.
One way to reduce this cost is by optimizing the IPFS hash that gets appended to the smart contract code.

Why is this important?
- The metadata adds an extra 53 bytes, resulting in an additional 10,600 gas cost for deployment.
- It also incurs up to 848 additional gas in calldata cost.

Options to Reduce Gas:
1. Use the `--no-cbor-metadata` compiler option to exclude metadata, but this might affect contract verification.
2. Mine for code comments that lead to an IPFS hash with more zeros, reducing calldata costs.

<details>
<summary><i>81 issue instances in 81 files:</i></summary>

```solidity
File: packages/protocol/contracts/common/IAddressManager.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressManager.sol#L1)

```solidity
File: packages/protocol/contracts/common/AddressManager.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L1)

```solidity
File: packages/protocol/contracts/common/IAddressResolver.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressResolver.sol#L1)

```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L1)

```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L1)

```solidity
File: packages/protocol/contracts/libs/Lib4844.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L1)

```solidity
File: packages/protocol/contracts/libs/LibAddress.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L1)

```solidity
File: packages/protocol/contracts/libs/LibMath.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibMath.sol#L1)

```solidity
File: packages/protocol/contracts/libs/LibTrieProof.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L1)

```solidity
File: packages/protocol/contracts/L1/gov/TaikoGovernor.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L1)

```solidity
File: packages/protocol/contracts/L1/gov/TaikoTimelockController.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L1)

```solidity
File: packages/protocol/contracts/L1/hooks/IHook.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/IHook.sol#L1)

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L1)

```solidity
File: packages/protocol/contracts/L1/ITaikoL1.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/ITaikoL1.sol#L1)

```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L1)

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L1)

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L1)

```solidity
File: packages/protocol/contracts/L1/libs/LibUtils.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L1)

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L1)

```solidity
File: packages/protocol/contracts/L1/provers/GuardianProver.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L1)

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L1)

```solidity
File: packages/protocol/contracts/L1/TaikoData.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L1)

```solidity
File: packages/protocol/contracts/L1/TaikoErrors.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoErrors.sol#L1)

```solidity
File: packages/protocol/contracts/L1/TaikoEvents.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L1)

```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L1)

```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L1)

```solidity
File: packages/protocol/contracts/L1/tiers/ITierProvider.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L1)

```solidity
File: packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L1)

```solidity
File: packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L1)

```solidity
File: packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L1)

```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L1)

```solidity
File: packages/protocol/contracts/L2/Lib1559Math.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L1)

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L1)

```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L1)

```solidity
File: packages/protocol/contracts/signal/ISignalService.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L1)

```solidity
File: packages/protocol/contracts/signal/LibSignals.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/LibSignals.sol#L1)

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L1)

```solidity
File: packages/protocol/contracts/bridge/IBridge.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L1)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L1)

```solidity
File: packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L1)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L1)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L1)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L1)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L1)

```solidity
File: packages/protocol/contracts/tokenvault/BaseNFTVault.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L1)

```solidity
File: packages/protocol/contracts/tokenvault/BaseVault.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L1)

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L1)

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L1)

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L1)

```solidity
File: packages/protocol/contracts/tokenvault/IBridgedERC20.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/IBridgedERC20.sol#L1)

```solidity
File: packages/protocol/contracts/tokenvault/LibBridgedToken.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L1)

```solidity
File: packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L1)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/Bytes.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L1)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L1)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L1)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L1)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L1)

```solidity
File: packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L1)

```solidity
File: packages/protocol/contracts/verifiers/IVerifier.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/IVerifier.sol#L1)

```solidity
File: packages/protocol/contracts/verifiers/GuardianVerifier.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L1)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L1)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L1)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L1)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L1)

```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L1)

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L1)

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L1)

```solidity
File: packages/protocol/contracts/automata-attestation/interfaces/IAttestation.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/interfaces/IAttestation.sol#L1)

```solidity
File: packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L1)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/EnclaveIdStruct.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/EnclaveIdStruct.sol#L1)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol#L1)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L1)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L1)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L1)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol#L1)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L1)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L1)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L1)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/SHA1.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SHA1.sol#L1)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L1)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

1: Consider optimizing the IPFS hash during deployment.
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L1)
</details>

### [G-46] Use Pre-Increment/Decrement (++i/--i) to Save Gas

Using pre-increment (++i) or pre-decrement (--i) operators is more gas-efficient compared to their post counterparts (i++ or i--).
This is because pre-increment/decrement operators avoid the need for an additional temporary variable that stores the original value of the iterator.
This subtle difference results in saving of around 5 gas units per operation, which can accumulate to substantial savings in gas costs in contracts with frequent increment/decrement operations.

<details>
<summary><i>14 issue instances in 8 files:</i></summary>

```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

62: _state.slotA.numEthDeposits++;
116: _state.slotA.numEthDeposits++;
```
[62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L62) | [116](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L116)

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

293: tid_ = _blk.nextTransitionId++;
```
[293](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L293)

```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

53: emit TransactionExecuted(nextTxId++, bytes4(txdata));
```
[53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L53)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

144: message_.id = nextMessageId++;
```
[144](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L144)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

40: lenLen++;
46: for (i = 1; i <= lenLen; i++) {
59: for (; i < 32; i++) {
66: for (uint256 j = 0; j < out_.length; j++) {
67: out_[j] = b[i++];
```
[40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L40) | [46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L46) | [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L59) | [66](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L66) | [67](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L67)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

85: for (uint256 i = 0; i < proof.length; i++) {
```
[85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

222: nextInstanceId++;
```
[222](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L222)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

17: string internal constant HEADER = "-----BEGIN CERTIFICATE-----";
18: string internal constant FOOTER = "-----END CERTIFICATE-----";
```
[17](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L17) | [18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L18)
</details>

### [G-47] Nesting `if`-statements is cheaper than using `&&`

Optimization of condition checks in your smart contract is a crucial aspect in ensuring gas efficiency. Specifically, substituting multiple `&&` checks with nested `if` statements can lead to substantial gas savings.

When evaluating multiple conditions within a single `if` statement using the `&&` operator, each condition will consume gas even if a preceding condition fails. However, if these checks are broken down into nested `if` statements, execution halts as soon as a condition fails, saving the gas that would have been consumed by subsequent checks.

This practice is especially beneficial in scenarios where the `if` statement isn't followed by an `else` statement. The reason being, when an `else` statement is present, all conditions must be checked regardless to determine the correct branch of execution.

By reworking your code to utilize nested `if` statements, you can optimize gas usage, reduce execution cost, and enhance your contract's performance.

<details>
<summary><i>19 issue instances in 13 files:</i></summary>

```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

85: if (!_allowZeroAddress && addr_ == address(0)) {
```
[85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L85)

```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

42: if (msg.sender != owner() && msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();
```
[42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L42)

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

120: if (input.tip != 0 && block.coinbase != address(0)) {
```
[120](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L120)

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

108: if (params.parentMetaHash != 0 && parentMetaHash != params.parentMetaHash) {
164: if (_config.blobReuseEnabled && params.cacheBlobForReuse) {
310: if (proposerOne != address(0) && msg.sender != proposerOne) {
```
[108](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L108) | [164](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L164) | [310](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L310)

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

419: if (_tid == 1 && _ts.tier == 0 && inProvingWindow) {
```
[419](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L419)

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

141: if (!skipFeeCheck() && block.basefee != basefee) {
275: if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {
```
[141](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L141) | [275](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L275)

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

285: if (cacheStateRoot && _isFullProof && !_isLastHop) {
293: if (cacheSignalRoot && (_isFullProof || !_isLastHop)) {
```
[285](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L285) | [293](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L293)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

250: if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) {
260: if (_message.gasLimit == 0 && msg.sender != _message.destOwner) {
439: } else if (block.chainid >= 32_300 && block.chainid <= 32_400) {
```
[250](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L250) | [260](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L260) | [439](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L439)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

38: if (msg.sender != owner() && msg.sender != snapshooter) {
```
[38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L38)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

45: if (_migratingAddress == migratingAddress && _migratingInbound == migratingInbound) {
```
[45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L45)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

14: if (_in.length == 1 && uint8(_in[0]) < 128) {
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L14)

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

277: if (_cliff > 0 && _cliff <= _start) revert INVALID_GRANT();
```
[277](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L277)

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

220: if (pceSvnIsHigherOrGreater && cpuSvnsAreHigherOrGreater) {
```
[220](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L220)
</details>

### [G-48] Use `storage` instead of `memory` for state structs/arrays

When fetching data from storage, assigning it to a memory variable causes all fields of the struct/array to be read from storage, incurring a Gcoldsload (2100 gas) for each field.
Reading fields from the new memory variable incurs an additional MLOAD rather than a cheap stack read.

Instead, declare variables with the storage keyword and cache any fields that need to be re-read in stack variables.
This approach is more cost-efficient, only incurring the Gcoldsload for fields actually read.

The only time it makes sense to read the whole struct/array into a memory variable is if the full struct/array is being returned by the function, passed to a function that requires memory, or read from another memory array/struct.

<details>
<summary><i>28 issue instances in 15 files:</i></summary>

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

78: ProverAssignment memory assignment = input.assignment;
```
[78](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L78)

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

93: TaikoData.SlotB memory b = _state.slotB;
```
[93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L93)

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

110: TaikoData.SlotB memory b = _state.slotB;
```
[110](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L110)

```solidity
File: packages/protocol/contracts/L1/libs/LibUtils.sol

33: TaikoData.SlotB memory b = _state.slotB;
```
[33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L33)

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

99: TaikoData.SlotB memory b = _state.slotB;
```
[99](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L99)

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

136: Config memory config = getConfig();
```
[136](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L136)

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

104: IBridge.Context memory ctx = checkProcessMessageContext();
```
[104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L104)

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

171: CanonicalERC20 memory ctoken = bridgedToCanonical[btokenOld_];
263: IBridge.Context memory ctx = checkProcessMessageContext();
```
[171](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L171) | [263](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L263)

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

87: IBridge.Context memory ctx = checkProcessMessageContext();
```
[87](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L87)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

56: bytes memory b = abi.encodePacked(_x);
```
[56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L56)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

79: TrieNode[] memory proof = _parseProof(_proof);
81: bytes memory currentNodeID = abi.encodePacked(_root);
86: TrieNode memory currentNode = proof[i];
135: RLPReader.RLPItem memory nextNode = currentNode.decoded[branchKey];
140: bytes memory path = _getNodePath(currentNode);
```
[79](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L79) | [81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L81) | [86](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L86) | [135](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L135) | [140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L140)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol

29: bytes memory key = _getSecureKey(_key);
47: bytes memory key = _getSecureKey(_key);
```
[29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L29) | [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L47)

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

180: EnclaveIdStruct.EnclaveId memory enclaveId = qeIdentity;
192: EnclaveIdStruct.TcbLevel memory tcb = enclaveId.tcbLevels[i];
215: TCBInfoStruct.TCBLevelObj memory current = tcb.tcbLevels[i];
435: string memory parsedFmspc = parsedQuoteCerts[0].pck.sgxExtension.fmspc;
442: IPEMCertChainLib.ECSha256Certificate memory pckCert = parsedQuoteCerts[0];
```
[180](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L180) | [192](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L192) | [215](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L215) | [435](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L435) | [442](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L442)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

49: string memory pemChainStr = string(pemChain);
107: bytes memory serialNumBytes = der.bytesAt(tbsPtr);
357: bytes memory svnValueBytes = der.bytesAt(svnValuePtr);
```
[49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L49) | [107](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L107) | [357](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L357)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

52: V3Struct.EnclaveReport memory localEnclaveReport = parseEnclaveReport(rawLocalEnclaveReport);
75: V3Struct.EnclaveReport memory pckSignedQeReport = v3Quote.v3AuthData.pckSignedQeReport;
```
[52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L52) | [75](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L75)
</details>

### [G-49] Optimize by Using Assembly for Low-Level Calls' Return Data

Even second return value from a low-level call is not assigned, it is still copied to memory, leading to additional gas costs.
By employing assembly, you can bypass this memory copying, achieving a 159 gas saving.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

50: (bool success,) = address(this).call(txdata);
```
[50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L50)
</details>

### [G-50] Avoid transferring amounts of zero in order to save gas

Performing token or Ether transfers with a zero amount may result in unnecessary gas consumption. 
The absence of a zero-amount check before a transfer or send operation can lead to wasted gas, as the state of the contract remains the same even if the amount is zero. 
Adding a conditional check for zero amounts can prevent these costly, unnecessary operations, thereby optimizing the contract's gas usage.

<details>
<summary><i>18 issue instances in 11 files:</i></summary>

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

/// @audit `_blk.livenessBond` has not been checked for zero value before transfer
102: tko.transferFrom(_blk.assignedProver, taikoL1Address, _blk.livenessBond);
```
[102](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L102)

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

/// @audit `tier.contestBond` has not been checked for zero value before transfer
242: tko.transferFrom(msg.sender, address(this), tier.contestBond);
/// @audit `_ts.validityBond + reward` has not been checked for zero value before transfer
367: _tko.transfer(_ts.prover, _ts.validityBond + reward);
/// @audit `_ts.contestBond + reward` has not been checked for zero value before transfer
371: _tko.transfer(_ts.contester, _ts.contestBond + reward);
/// @audit `reward - _tier.validityBond` has not been checked for zero value before transfer
382: _tko.transfer(msg.sender, reward - _tier.validityBond);
/// @audit `_tier.validityBond - reward` has not been checked for zero value before transfer
384: _tko.transferFrom(msg.sender, address(this), _tier.validityBond - reward);
```
[242](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L242) | [367](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L367) | [371](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L371) | [382](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L382) | [384](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L384)

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

/// @audit `bondToReturn` has not been checked for zero value before transfer
189: tko.transfer(ts.prover, bondToReturn);
```
[189](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L189)

```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

/// @audit `_amount` has not been checked for zero value before transfer
62: return super.transfer(_to, _amount);
/// @audit `_amount` has not been checked for zero value before transfer
80: return super.transferFrom(_from, _to, _amount);
```
[62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L62) | [80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L80)

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

/// @audit `IERC20(_token).balanceOf(address(this))` has not been checked for zero value before transfer
176: IERC20(_token).safeTransfer(_to, IERC20(_token).balanceOf(address(this)));
```
[176](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L176)

```solidity
File: packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

/// @audit `_amount` has not been checked for zero value before transfer
48: usdc.transferFrom(_from, address(this), _amount);
```
[48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L48)

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

/// @audit `_amount` has not been checked for zero value before transfer
330: IERC20(token_).safeTransfer(_to, _amount);
/// @audit `value: _amount }` has not been checked for zero value before transfer
379: t.safeTransferFrom({ from: msg.sender, to: address(this), value: _amount });
```
[330](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L330) | [379](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L379)

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

/// @audit `_op.tokenIds[i]` has not been checked for zero value before transfer
211: t.safeTransferFrom(_user, address(this), _op.tokenIds[i]);
```
[211](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L211)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

/// @audit `amount` has not been checked for zero value before transfer
63: IERC20(token).transferFrom(vault, user, amount);
```
[63](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L63)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

/// @audit `amount` has not been checked for zero value before transfer
91: IERC20(token).transferFrom(vault, user, amount);
```
[91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L91)

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

/// @audit `amountToWithdraw` has not been checked for zero value before transfer
219: IERC20(taikoToken).transferFrom(sharedVault, _to, amountToWithdraw);
/// @audit `costToWithdraw` has not been checked for zero value before transfer
220: IERC20(costToken).safeTransferFrom(_recipient, sharedVault, costToWithdraw);
```
[219](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L219) | [220](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L220)
</details>

### [G-51] Cache Function Calls for Efficiency

Function calls, especially external function calls, can be quite expensive in terms of gas. 
If you need to retrieve the same data more than once in a function, it is more efficient to call 
the function once, store the result in a local variable, and then use that variable later in the 
code instead of making the function call again.

<details>
<summary><i>54 issue instances in 6 files:</i></summary>

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

238: uint256 tkoBalance = tko.balanceOf(address(this));
268: if (tko.balanceOf(address(this)) != tkoBalance + _config.livenessBond) {
```
[238](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L238) | [268](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L268)

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

378: uint256 _balance = t.balanceOf(address(this));
380: balanceChange_ = t.balanceOf(address(this)) - _balance;
```
[378](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L378) | [380](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L380)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

78: ptr: MemoryPointer.wrap(MemoryPointer.unwrap(_in.ptr) + offset)
                })
86: ptr: MemoryPointer.wrap(MemoryPointer.unwrap(_in.ptr) + offset)
            });
78: ptr: MemoryPointer.wrap(MemoryPointer.unwrap(_in.ptr) + offset)
86: ptr: MemoryPointer.wrap(MemoryPointer.unwrap(_in.ptr) + offset)
```
[78](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L78) | [86](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L86) | [78](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L78) | [86](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L86)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

94: Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
100: Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
```
[94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L94) | [100](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L100)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

104: tbsPtr = der.nextSiblingOf(tbsPtr);
111: tbsPtr = der.nextSiblingOf(tbsPtr);
112: tbsPtr = der.nextSiblingOf(tbsPtr);
127: tbsPtr = der.nextSiblingOf(tbsPtr);
144: tbsPtr = der.nextSiblingOf(tbsPtr);
157: tbsPtr = der.nextSiblingOf(tbsPtr);
186: tbsPtr = der.nextSiblingOf(tbsPtr);
115: uint256 issuerPtr = der.firstChildOf(tbsPtr);
130: uint256 notBeforePtr = der.firstChildOf(tbsPtr);
147: uint256 subjectPtr = der.firstChildOf(tbsPtr);
161: uint256 subjectPublicKeyInfoPtr = der.firstChildOf(tbsPtr);
193: tbsPtr = der.firstChildOf(tbsPtr);
194: tbsPtr = der.firstChildOf(tbsPtr);
116: issuerPtr = der.firstChildOf(issuerPtr);
117: issuerPtr = der.firstChildOf(issuerPtr);
148: subjectPtr = der.firstChildOf(subjectPtr);
149: subjectPtr = der.firstChildOf(subjectPtr);
167: sigPtr = der.nextSiblingOf(sigPtr);
176: sigPtr = der.nextSiblingOf(sigPtr);
174: bytes memory sigX = _trimBytes(der.bytesAt(sigPtr), 32);
177: bytes memory sigY = _trimBytes(der.bytesAt(sigPtr), 32);
306: if (BytesUtils.compareBytes(der.bytesAt(extnValueOidPtr), TCB_OID)) {
310: if (BytesUtils.compareBytes(der.bytesAt(extnValueOidPtr), PCEID_OID)) {
316: if (BytesUtils.compareBytes(der.bytesAt(extnValueOidPtr), FMSPC_OID)) {
312: uint256 pceidPtr = der.nextSiblingOf(extnValueOidPtr);
318: uint256 fmspcPtr = der.nextSiblingOf(extnValueOidPtr);
```
[104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L104) | [111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L111) | [112](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L112) | [127](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L127) | [144](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L144) | [157](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L157) | [186](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L186) | [115](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L115) | [130](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L130) | [147](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L147) | [161](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L161) | [193](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L193) | [194](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L194) | [116](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L116) | [117](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L117) | [148](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L148) | [149](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L149) | [167](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L167) | [176](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L176) | [174](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L174) | [177](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L177) | [306](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L306) | [310](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L310) | [316](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L316) | [312](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L312) | [318](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L318)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

100: ((i.ixf() <= j.ixs()) && (j.ixl() <= i.ixl()))
101: || ((j.ixf() <= i.ixs()) && (i.ixl() <= j.ixl()))
112: return der.substring(ptr.ixf(), ptr.ixl() + 1 - ptr.ixf());
122: return der.substring(ptr.ixs(), ptr.ixl() + 1 - ptr.ixs());
132: return der.readBytesN(ptr.ixf(), ptr.ixl() + 1 - ptr.ixf());
143: require(der[ptr.ixf()] & 0x80 == 0, "Not positive");
144: uint256 len = ptr.ixl() + 1 - ptr.ixf();
145: return uint256(der.readBytesN(ptr.ixf(), len) >> (32 - len) * 8);
156: require(der[ptr.ixf()] & 0x80 == 0, "Not positive");
157: uint256 valueLength = ptr.ixl() + 1 - ptr.ixf();
158: if (der[ptr.ixf()] == 0) {
159: return der.substring(ptr.ixf() + 1, valueLength - 1);
161: return der.substring(ptr.ixf(), valueLength);
166: return der.keccak(ptr.ixf(), ptr.ixl() + 1 - ptr.ixf());
170: return der.keccak(ptr.ixs(), ptr.ixl() + 1 - ptr.ixs());
182: require(der[ptr.ixf()] == 0x00, "ixf Not 0");
183: uint256 valueLength = ptr.ixl() + 1 - ptr.ixf();
184: return der.substring(ptr.ixf() + 1, valueLength - 1);
```
[100](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L100) | [101](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L101) | [112](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L112) | [122](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L122) | [132](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L132) | [143](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L143) | [144](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L144) | [145](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L145) | [156](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L156) | [157](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L157) | [158](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L158) | [159](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L159) | [161](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L161) | [166](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L166) | [170](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L170) | [182](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L182) | [183](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L183) | [184](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L184)
</details>

### [G-52] Superfluous Event Fields

Event logs in the Ethereum Virtual Machine (EVM) automatically include certain block data such as the `block.timestamp` and `block.number`.
Explicitly including these values in your event arguments results in superfluous data that unnecessarily consumes gas.
This redundancy not only leads to higher execution costs for your smart contract functions but also increases the amount of data stored on the Ethereum blockchain, which in turn, inflates storage and processing requirements for all participating nodes. 

By removing these redundant fields from your events, you can potentially save a significant amount of gas.
This optimization will not only make your smart contract more efficient but also more cost-effective to execute.
This practice emphasizes the importance of optimizing smart contract code to achieve maximum efficiency and minimal gas costs, contributing to the sustainability of the Ethereum ecosystem.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

230: emit InstanceAdded(id, newInstance, oldInstance, block.timestamp);
```
[230](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L230)
</details>

### [G-53] Unutilized Named Return Variables Waste Gas Without Optimizer

Utilizing named return variables without assignment or explicit return in functions can lead to unnecessary gas costs without an active optimizer.
To enhance gas efficiency, you might consider opting for unnamed return variables, especially when they aren't explicitly used or returned.
Keeping the current configuration without an active optimizer can result in extra gas costs associated with superfluous stack variables.

<details>
<summary><i>22 issue instances in 12 files:</i></summary>

```solidity
File: packages/protocol/contracts/libs/LibAddress.sol

/// @audit - Redundant `if (!Address.isContract(_addr)) return false;` statement in functions with named return variables
45: function supportsInterface(
        address _addr,
        bytes4 _interfaceId
    )
        internal
        view
        returns (bool result_)
    {
```
[45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L45)

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

/// @audit - Redundant `return tier.maxBlocksToVerifyPerProof;` statement in functions with named return variables
91: function proveBlock(
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
```
[91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L91)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

/// @audit - Redundant `return (1 hours, 384 seconds);` statement in functions with named return variables
/// @audit - Redundant `return (30 minutes, 384 seconds);` statement in functions with named return variables
/// @audit - Redundant `return (5 minutes, 384 seconds);` statement in functions with named return variables
/// @audit - Redundant `return (0, 0);` statement in functions with named return variables
417: function getInvocationDelays()
        public
        view
        virtual
        returns (uint256 invocationDelay_, uint256 invocationExtraDelay_)
    {
/// @audit - Redundant `64, // return max 64 bytes
                _message.data
            );` statement in functions with named return variables
477: function _invokeMessageCall(
        Message calldata _message,
        bytes32 _msgHash,
        uint256 _gasLimit
    )
        private
        returns (bool success_)
    {
```
[417](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L417) | [477](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L477)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

/// @audit - Redundant `return (0, 1, RLPItemType.DATA_ITEM);` statement in functions with named return variables
/// @audit - Redundant `return (1, strLen, RLPItemType.DATA_ITEM);` statement in functions with named return variables
/// @audit - Redundant `return (1 + lenOfStrLen, strLen, RLPItemType.DATA_ITEM);` statement in functions with named return variables
/// @audit - Redundant `return (1, listLen, RLPItemType.LIST_ITEM);` statement in functions with named return variables
/// @audit - Redundant `return (1 + lenOfListLen, listLen, RLPItemType.LIST_ITEM);` statement in functions with named return variables
144: function _decodeLength(RLPItem memory _in)
        private
        pure
        returns (uint256 offset_, uint256 length_, RLPItemType type_)
    {
/// @audit - Redundant `return out_;` statement in functions with named return variables
277: function _copy(
        MemoryPointer _src,
        uint256 _offset,
        uint256 _length
    )
        private
        pure
        returns (bytes memory out_)
    {
```
[144](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L144) | [277](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L277)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

/// @audit - Redundant `return value_;` statement in functions with named return variables
/// @audit - Redundant `return value_;` statement in functions with named return variables
68: function get(
        bytes memory _key,
        bytes[] memory _proof,
        bytes32 _root
    )
        internal
        pure
        returns (bytes memory value_)
    {
```
[68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L68)

```solidity
File: packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol

13: function exp(int256 x) internal pure returns (int256 r) {
```
[13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L13)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

/// @audit - Redundant `if (balance == 0) return (0, 0);` statement in functions with named return variables
/// @audit - Redundant `if (block.timestamp < claimEnd) return (balance, 0);` statement in functions with named return variables
104: function getBalance(address user)
        public
        view
        returns (uint256 balance, uint256 withdrawableAmount)
    {
```
[104](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L104)

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

/// @audit - Redundant `return status == TCBInfoStruct.TCBStatus.OK
            || status == TCBInfoStruct.TCBStatus.TCB_SW_HARDENING_NEEDED
            || status == TCBInfoStruct.TCBStatus.TCB_CONFIGURATION_AND_SW_HARDENING_NEEDED
            || status == TCBInfoStruct.TCBStatus.TCB_OUT_OF_DATE_CONFIGURATION_NEEDED;` statement in functions with named return variables
125: function _attestationTcbIsValid(TCBInfoStruct.TCBStatus status)
        internal
        pure
        virtual
        returns (bool valid)
    {
/// @audit - Redundant `return (
            miscselectMatched && attributesMatched && mrsignerMatched && isvprodidMatched
                && tcbFound,
            status
        );` statement in functions with named return variables
174: function _verifyQEReportWithIdentity(V3Struct.EnclaveReport memory quoteEnclaveReport)
        private
        view
        returns (bool, EnclaveIdStruct.EnclaveIdStatus status)
    {
/// @audit - Redundant `return (!tcbIsRevoked, status);` statement in functions with named return variables
/// @audit - Redundant `return (true, TCBInfoStruct.TCBStatus.TCB_UNRECOGNIZED);` statement in functions with named return variables
205: function _checkTcbLevels(
        IPEMCertChainLib.PCKCertificateField memory pck,
        TCBInfoStruct.TCBInfo memory tcb
    )
        private
        pure
        returns (bool, TCBInfoStruct.TCBStatus status)
    {
```
[125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L125) | [174](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L174) | [205](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L205)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

/// @audit - Redundant `return (false, certs);` statement in functions with named return variables
39: function splitCertificateChain(
        bytes memory pemChain,
        uint256 size
    )
        external
        pure
        returns (bool success, bytes[] memory certs)
    {
/// @audit - Redundant `return (false, cert);` statement in functions with named return variables
/// @audit - Redundant `return (false, cert);` statement in functions with named return variables
/// @audit - Redundant `return (false, cert);` statement in functions with named return variables
/// @audit - Redundant `return (false, cert);` statement in functions with named return variables
/// @audit - Redundant `return (false, cert);` statement in functions with named return variables
73: function decodeCert(
        bytes memory der,
        bool isPckCert
    )
        external
        pure
        returns (bool success, ECSha256Certificate memory cert)
    {
/// @audit - Redundant `return (false, extracted, endIndex);` statement in functions with named return variables
/// @audit - Redundant `return (true, contentBytes, endPos + FOOTER_LENGTH);` statement in functions with named return variables
215: function _removeHeadersAndFooters(string memory pemData)
        private
        pure
        returns (bool success, bytes memory extracted, uint256 endIndex)
    {
/// @audit - Redundant `return input;` statement in functions with named return variables
251: function _trimBytes(
        bytes memory input,
        uint256 expectedLength
    )
        private
        pure
        returns (bytes memory output)
    {
/// @audit - Redundant `return (false, pcesvn, cpusvns, fmspcBytes, pceidBytes);` statement in functions with named return variables
/// @audit - Redundant `return (false, pcesvn, cpusvns, fmspcBytes, pceidBytes);` statement in functions with named return variables
268: function _findPckTcbInfo(
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
```
[39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L39) | [73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L73) | [215](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L215) | [251](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L251) | [268](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L268)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

/// @audit - Redundant `return (false, v3ParsedQuote);` statement in functions with named return variables
/// @audit - Redundant `return (false, v3ParsedQuote);` statement in functions with named return variables
/// @audit - Redundant `return (false, v3ParsedQuote);` statement in functions with named return variables
/// @audit - Redundant `return (false, v3ParsedQuote);` statement in functions with named return variables
20: function parseInput(
        bytes memory quote,
        address pemCertLibAddr
    )
        internal
        pure
        returns (bool success, V3Struct.ParsedV3QuoteStruct memory v3ParsedQuote)
    {
/// @audit - Redundant `return (false, header);` statement in functions with named return variables
/// @audit - Redundant `return (false, header);` statement in functions with named return variables
/// @audit - Redundant `return (false, header);` statement in functions with named return variables
/// @audit - Redundant `return (false, header);` statement in functions with named return variables
164: function parseAndVerifyHeader(bytes memory rawHeader)
        private
        pure
        returns (bool success, V3Struct.Header memory header)
    {
/// @audit - Redundant `return (false, authDataV3);` statement in functions with named return variables
202: function parseAuthDataAndVerifyCertType(
        bytes memory rawAuthData,
        address pemCertLibAddr
    )
        private
        pure
        returns (bool success, V3Struct.ECDSAQuoteV3AuthData memory authDataV3)
    {
```
[20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L20) | [164](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L164) | [202](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L202)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

/// @audit - Redundant `return uint8(self[idx]);` statement in functions with named return variables
188: function readUint8(bytes memory self, uint256 idx) internal pure returns (uint8 ret) {
```
[188](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L188)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

/// @audit - Redundant `return false;` statement in functions with named return variables
/// @audit - Redundant `return false;` statement in functions with named return variables
/// @audit - Redundant `return abi.decode(ret, (uint256)) == 1;` statement in functions with named return variables
112: function verifyES256Signature(
        bytes memory tbs,
        bytes memory signature,
        bytes memory publicKey
    )
        public
        view
        returns (bool sigValid)
    {
```
[112](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L112)
</details>

### [G-54] Use `unchecked` for Math Operations if they already checked

Some subtraction operations in the contract have implicit checks that prevent underflow. 
To optimize gas, consider wrapping such operations in an `unchecked` block. 
Always review the logic thoroughly before making changes to ensure the safety of operations.

<details>
<summary><i>17 issue instances in 9 files:</i></summary>

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

/// @audit - mathematical operation `reward - _tier.validityBond` checked above in line:
/// 381: if (reward > _tier.validityBond) {
382: _tko.transfer(msg.sender, reward - _tier.validityBond);
/// @audit - mathematical operation `_tier.validityBond - reward` checked above in line:
/// 381: if (reward > _tier.validityBond) {
384: _tko.transferFrom(msg.sender, address(this), _tier.validityBond - reward);
```
[382](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L382) | [384](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L384)

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

/// @audit - mathematical operation `_l1BlockId - lastSyncedBlock` checked above in line:
/// 275: if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {
276: numL1Blocks = _l1BlockId - lastSyncedBlock;
```
[276](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L276)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/Bytes.sol

/// @audit - mathematical operation `_start + _length` checked above in line:
/// 26: require(_start + _length >= _start, "slice_overflow");
27: require(_bytes.length >= _start + _length, "slice_outOfBounds");
/// @audit - mathematical operation `_bytes.length - _start` checked above in line:
/// 92: if (_start >= _bytes.length) {
95: return slice(_bytes, _start, _bytes.length - _start);
```
[27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L27) | [95](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L95)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

/// @audit - mathematical operation `prefix - 0` checked above in line:
/// 163: if (prefix <= 0x7f) {
170: uint256 strLen = prefix - 0x80;
/// @audit - mathematical operation `prefix - 0` checked above in line:
/// 163: if (prefix <= 0x7f) {
190: uint256 lenOfStrLen = prefix - 0xb7;
/// @audit - mathematical operation `prefix - 0` checked above in line:
/// 163: if (prefix <= 0x7f) {
226: uint256 listLen = prefix - 0xc0;
/// @audit - mathematical operation `prefix - 0` checked above in line:
/// 163: if (prefix <= 0x7f) {
236: uint256 lenOfListLen = prefix - 0xf7;
```
[170](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L170) | [190](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L190) | [226](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L226) | [236](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L236)

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

/// @audit - mathematical operation `block.timestamp - _start` checked above in line:
/// 257: if (block.timestamp <= _start) return 0;
264: return _amount * uint64(block.timestamp - _start) / _period;
```
[264](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L264)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

/// @audit - mathematical operation `n - expectedLength` checked above in line:
/// 262: if (n <= expectedLength) {
265: uint256 lengthDiff = n - expectedLength;
```
[265](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L265)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

/// @audit - mathematical operation `ix + 1` checked above in line:
/// 191: if ((der[ix + 1] & 0x80) == 0) {
192: length = uint8(der[ix + 1]);
/// @audit - mathematical operation `ix + 1` checked above in line:
/// 191: if ((der[ix + 1] & 0x80) == 0) {
196: uint8 lengthbytesLength = uint8(der[ix + 1] & 0x7F);
```
[192](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L192) | [196](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L196)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

/// @audit - mathematical operation `32 - shortest` checked above in line:
/// 90: if (shortest > 32) {
93: mask = ~(2 ** (8 * (32 - shortest + idx)) - 1);
```
[93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L93)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

/// @audit - mathematical operation `3 + paddingLen` checked above in line:
/// 153: if (decipher[3 + paddingLen + i] != bytes1(sha256ExplicitNullParam[i])) {
159: if (decipher[3 + paddingLen + i] != bytes1(sha256ImplicitNullParam[i])) {
/// @audit - mathematical operation `3 + paddingLen` checked above in line:
/// 153: if (decipher[3 + paddingLen + i] != bytes1(sha256ExplicitNullParam[i])) {
168: decipher[3 + paddingLen + digestAlgoWithParamLen] != 0x04
/// @audit - mathematical operation `3 + paddingLen` checked above in line:
/// 284: if (decipher[3 + paddingLen + i] != bytes1(sha1Prefix[i])) {
291: if (decipher[3 + paddingLen + sha1Prefix.length + i] != _sha1[i]) {
```
[159](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L159) | [168](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L168) | [291](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L291)
</details>

### [G-55] Using `private` rather than `public`, saves gas

Public storage variables increase the contract's size due to the implicit generation of public getter functions. 
This makes the contract larger and could increase deployment and interaction costs.

If you do not require other contracts to read these variables, consider making them `private`. 

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

<details>
<summary><i>86 issue instances in 29 files:</i></summary>

```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

13: address public addressManager;
```
[13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L13)

```solidity
File: packages/protocol/contracts/libs/Lib4844.sol

10: address public constant POINT_EVALUATION_PRECOMPILE_ADDRESS = address(0x0A);
13: uint32 public constant FIELD_ELEMENTS_PER_BLOB = 4096;
16: uint256 public constant BLS_MODULUS =
        52_435_875_175_126_190_479_447_740_508_185_965_837_690_552_500_527_637_822_603_658_699_938_581_184_513;
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L10) | [13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L13) | [16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L16)

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

38: uint256 public constant MAX_GAS_PAYING_PROVER = 50_000;
```
[38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L38)

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

21: uint256 public constant MAX_BYTES_PER_BLOB = 4096 * 32;
```
[21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L21)

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

20: bytes32 public constant RETURN_LIVENESS_BOND = keccak256("RETURN_LIVENESS_BOND");
23: bytes32 public constant TIER_OP = bytes32("tier_optimistic");
```
[20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L20) | [23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L23)

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

11: uint256 public constant MIN_NUM_GUARDIANS = 5;
16: mapping(address guardian => uint256 id) public guardianIds;
23: address[] public guardians;
27: uint32 public version;
30: uint32 public minGuardians;
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L11) | [16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L16) | [23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L23) | [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L27) | [30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L30)

```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

24: TaikoData.State public state;
```
[24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L24)

```solidity
File: packages/protocol/contracts/L1/tiers/ITierProvider.sol

39: uint16 public constant TIER_OPTIMISTIC = 100;
42: uint16 public constant TIER_SGX = 200;
45: uint16 public constant TIER_SGX_ZKVM = 300;
48: uint16 public constant TIER_GUARDIAN = 1000;
```
[39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L39) | [42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L42) | [45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L45) | [48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L48)

```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

16: uint64 public ownerChainId;
19: uint64 public nextTxId;
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L16) | [19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L19)

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

32: address public constant GOLDEN_TOUCH_ADDRESS = 0x0000777735367b36bC9B61C50022d9D0700dB4Ec;
35: uint8 public constant BLOCK_SYNC_THRESHOLD = 5;
39: mapping(uint256 blockId => bytes32 blockHash) public l2Hashes;
43: bytes32 public publicInputHash;
47: uint64 public gasExcess;
50: uint64 public lastSyncedBlock;
```
[32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L32) | [35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L35) | [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L39) | [43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L43) | [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L47) | [50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L50)

```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

11: Config public customConfig;
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L11)

```solidity
File: packages/protocol/contracts/signal/LibSignals.sol

8: bytes32 public constant STATE_ROOT = keccak256("STATE_ROOT");
11: bytes32 public constant SIGNAL_ROOT = keccak256("SIGNAL_ROOT");
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/LibSignals.sol#L8) | [11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/LibSignals.sol#L11)

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

17: mapping(uint64 chainId => mapping(bytes32 kind => uint64 blockId)) public topBlockId;
21: mapping(address addr => bool authorized) public isAuthorized;
```
[17](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L17) | [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L21)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

31: uint128 public nextMessageId;
35: mapping(bytes32 msgHash => Status status) public messageStatus;
42: mapping(address addr => bool banned) public addressBanned;
46: mapping(bytes32 msgHash => ProofReceipt receipt) public proofReceipt;
```
[31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L31) | [35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L35) | [42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L42) | [46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L46)

```solidity
File: packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

31: IUSDC public usdc;
```
[31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L31)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

22: address public srcToken;
27: uint256 public srcChainId;
30: address public snapshooter;
```
[22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L22) | [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L27) | [30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L30)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

11: address public migratingAddress;
14: bool public migratingInbound;
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L11) | [14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L14)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

14: address public srcToken;
17: uint256 public srcChainId;
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L14) | [17](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L17)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

16: address public srcToken;
19: uint256 public srcChainId;
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L16) | [19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L19)

```solidity
File: packages/protocol/contracts/tokenvault/BaseNFTVault.sol

47: bytes4 public constant ERC1155_INTERFACE_ID = 0xd9b67a26;
50: bytes4 public constant ERC721_INTERFACE_ID = 0x80ac58cd;
53: uint256 public constant MAX_TOKEN_PER_TXN = 10;
56: mapping(address btoken => CanonicalNFT canonical) public bridgedToCanonical;
59: mapping(uint256 chainId => mapping(address ctoken => address btoken)) public canonicalToBridged;
```
[47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L47) | [50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L50) | [53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L53) | [56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L56) | [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L59)

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

45: mapping(address btoken => CanonicalERC20 canonical) public bridgedToCanonical;
49: mapping(uint256 chainId => mapping(address ctoken => address btoken)) public canonicalToBridged;
52: mapping(address btoken => bool blacklisted) public btokenBlacklist;
```
[45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L45) | [49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L49) | [52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L52)

```solidity
File: packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol

7: uint128 public constant MAX_EXP_INPUT = 135_305_999_368_893_231_588;
8: uint256 public constant SCALING_FACTOR = 1e18; // For fixed point representation factor
```
[7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L7) | [8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L8)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

30: uint64 public constant INSTANCE_EXPIRY = 180 days;
34: uint64 public constant INSTANCE_VALIDITY_DELAY = 1 days;
39: uint256 public nextInstanceId;
47: mapping(uint256 instanceId => Instance instance) public instances;
55: mapping(address instanceAddress => bool alreadyAttested) public addressRegistered;
```
[30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L30) | [34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L34) | [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L39) | [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L47) | [55](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L55)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

13: address public token;
16: address public vault;
```
[13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L13) | [16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L16)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

16: address public token;
19: address public vault;
22: mapping(address addr => uint256 amountClaimed) public claimedAmount;
25: mapping(address addr => uint256 amountWithdrawn) public withdrawnAmount;
28: uint64 public withdrawalWindow;
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L16) | [19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L19) | [22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L22) | [25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L25) | [28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L28)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

11: address public token;
14: address public vault;
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L11) | [14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L14)

```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

12: mapping(bytes32 hash => bool claimed) public isClaimed;
15: bytes32 public merkleRoot;
18: uint64 public claimStart;
21: uint64 public claimEnd;
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L12) | [15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L15) | [18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L18) | [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L21)

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

59: address public taikoToken;
62: address public costToken;
65: address public sharedVault;
68: uint128 public totalAmountGranted;
71: uint128 public totalAmountVoided;
74: uint128 public totalAmountWithdrawn;
77: uint128 public totalCostPaid;
80: mapping(address recipient => Recipient receipt) public recipients;
```
[59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L59) | [62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L62) | [65](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L65) | [68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L68) | [71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L71) | [74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L74) | [77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L77) | [80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L80)

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

25: ISigVerifyLib public immutable sigVerifyLib;
26: IPEMCertChainLib public immutable pemCertLib;
49: mapping(string fmspc => TCBInfoStruct.TCBInfo tcbInfo) public tcbInfo;
50: EnclaveIdStruct.EnclaveId public qeIdentity;
52: address public owner;
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L25) | [26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L26) | [49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L49) | [50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L50) | [52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L52)
</details>

### [G-56] Use Assembly for Hash Calculations

In certain cases, using inline assembly to calculate hashes can lead to significant gas savings. Solidity's built-in keccak256 function is convenient but costs more gas than the equivalent assembly code. However, it's important to note that using assembly should be done with care as it's less readable and could increase the risk of introducing errors.

<details>
<summary><i>25 issue instances in 15 files:</i></summary>

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

146: return keccak256(
```
[146](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L146)

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

126: depositsHash: keccak256(abi.encode(deposits_)),
189: meta_.blobHash = keccak256(_txList);
204: meta_.difficulty = keccak256(abi.encodePacked(block.prevrandao, b.numBlocks, block.number));
213: metaHash: keccak256(abi.encode(meta_)),
```
[126](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L126) | [189](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L189) | [204](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L204) | [213](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L213)

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

121: if (blk.blockId != _meta.id || blk.metaHash != keccak256(abi.encode(_meta))) {
```
[121](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L121)

```solidity
File: packages/protocol/contracts/L1/provers/GuardianProver.sol

46: bytes32 hash = keccak256(abi.encode(_meta, _tran));
```
[46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L46)

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

186: return keccak256(abi.encode(_chainId, _kind, _blockId));
203: return keccak256(abi.encodePacked("SIGNAL", _chainId, _app, _signal));
```
[186](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L186) | [203](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L203)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

450: return keccak256(abi.encode("TAIKO_MESSAGE", _message));
```
[450](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L450)

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

176: || keccak256(bytes(ctoken.symbol)) != keccak256(bytes(_ctoken.symbol))
176: || keccak256(bytes(ctoken.symbol)) != keccak256(bytes(_ctoken.symbol))
177: || keccak256(bytes(ctoken.name)) != keccak256(bytes(_ctoken.name))
177: || keccak256(bytes(ctoken.name)) != keccak256(bytes(_ctoken.name))
```
[176](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L176) | [176](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L176) | [177](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L177) | [177](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L177)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/Bytes.sol

150: return keccak256(_bytes) == keccak256(_other);
150: return keccak256(_bytes) == keccak256(_other);
```
[150](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L150) | [150](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L150)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

94: Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
100: Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
```
[94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L94) | [100](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L100)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol

55: hash_ = abi.encodePacked(keccak256(_key));
```
[55](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L55)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

182: return keccak256(
```
[182](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L182)

```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

68: bytes32 hash = keccak256(abi.encode("CLAIM_TAIKO_AIRDROP", data));
```
[68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L68)

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

170: bytes32 hash = keccak256(abi.encodePacked("Withdraw unlocked Taiko token to: ", _to));
```
[170](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L170)

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

292: bytes32 issuerPubKeyHash = keccak256(issuer.pubKey);
```
[292](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L292)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

372: return keccak256(a) == keccak256(b);
372: return keccak256(a) == keccak256(b);
```
[372](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L372) | [372](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L372)
</details>

### [G-57] Consider using ERC721A instead of ERC721

The ERC721A standard, an evolution of the ERC721 standard, has been designed to significantly reduce gas costs associated with minting multiple non-fungible tokens (NFTs) in a single transaction.
Switching to ERC721A can offer substantial gas savings, thereby optimizing the efficiency of NFT transactions and potentially leading to considerable cost reductions.

<details>
<summary><i>3 issue instances in 3 files:</i></summary>

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

12: contract BridgedERC721 is EssentialContract, ERC721Upgradeable {
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L12)

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

16: contract ERC721Vault is BaseNFTVault, IERC721Receiver {
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L16)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

9: contract ERC721Airdrop is MerkleClaimable {
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L9)
</details>

### [G-58] Refactor duplicated require()/revert() checks to save gas

Duplicate require()/revert() checks can be refactored into a modifier or function, saving deployment costs.

<details>
<summary><i>14 issue instances in 6 files:</i></summary>

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

105: if (blk.blockId != blockId) revert L1_BLOCK_MISMATCH();
131: if (blk.blockId != blockId) revert L1_BLOCK_MISMATCH();
```
[105](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L105) | [131](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L131)

```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

61: if (_to == address(this)) revert TKO_INVALID_ADDR();
79: if (_to == address(this)) revert TKO_INVALID_ADDR();
```
[61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L61) | [79](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L79)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

166: if (messageStatus[msgHash] != Status.NEW) revert B_STATUS_MISMATCH();
227: if (messageStatus[msgHash] != Status.NEW) revert B_STATUS_MISMATCH();
```
[166](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L166) | [227](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L227)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

37: require(
            _in.length > 0,
            "RLPReader: length of an RLP item must be greater than zero to be decodable"
        );
152: require(
            _in.length > 0,
            "RLPReader: length of an RLP item must be greater than zero to be decodable"
        );
```
[37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L37) | [152](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L152)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

142: require(der[ptr.ixs()] == 0x02, "Not type INTEGER");
155: require(der[ptr.ixs()] == 0x02, "Not type INTEGER");
143: require(der[ptr.ixf()] & 0x80 == 0, "Not positive");
156: require(der[ptr.ixf()] & 0x80 == 0, "Not positive");
```
[142](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L142) | [155](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L155) | [143](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L143) | [156](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L156)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

50: revert("Unsupported algorithm");
75: revert("Unsupported algorithm");
```
[50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L50) | [75](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L75)
</details>

### [G-59] Use Assembly for Efficient Memory Management in Multiple External Calls

When making multiple external calls in a Solidity contract, it may be more efficient to use inline assembly to reuse the memory space allocated for function arguments and return data.
This can prevent unnecessary memory expansion and reduce gas costs.

Example:
```solidity
contract Solidity {
    // cost: 7262
    function call(address calledAddress) external pure returns(uint256) {
        Called called = Called(calledAddress);
        uint256 res1 = called.add(1, 2);
        uint256 res2 = called.add(3, 4);

        uint256 res = res1 + res2;
        return res;
    }
}

contract Assembly {
    // cost: 5281
    function call(address calledAddress) external view returns(uint256) {
        assembly {
            // check that calledAddress has code deployed to it
            if iszero(extcodesize(calledAddress)) {
                revert(0x00, 0x00)
            }

            // first call
            mstore(0x00, hex"771602f7")
            mstore(0x04, 0x01)
            mstore(0x24, 0x02)
            let success := staticcall(gas(), calledAddress, 0x00, 0x44, 0x60, 0x20)
            if iszero(success) {
                revert(0x00, 0x00)
            }
            let res1 := mload(0x60)

            // second call
            mstore(0x04, 0x03)
            mstore(0x24, 0x4)
            success := staticcall(gas(), calledAddress, 0x00, 0x44, 0x60, 0x20)
            if iszero(success) {
                revert(0x00, 0x00)
            }
            let res2 := mload(0x60)

            // add results
            let res := add(res1, res2)

            // return data
            mstore(0x60, res)
            return(0x60, 0x20)
        }
    }
}
```

<details>
<summary><i>6 issue instances in 3 files:</i></summary>

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

/// @audit function `_transferTokens()` has multiple external calls
226: IERC1155(token).safeBatchTransferFrom(address(this), to, tokenIds, amounts, "");
230: BridgedERC1155(token).mintBatch(to, tokenIds, amounts);
```
[226](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L226) | [230](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L230)

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

/// @audit function `changeBridgedToken()` has multiple external calls
184: IBridgedERC20(btokenOld_).changeMigrationStatus(_btokenNew, false);
185: IBridgedERC20(_btokenNew).changeMigrationStatus(btokenOld_, true);
```
[184](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L184) | [185](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L185)

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

/// @audit function `_enclaveReportSigVerification()` has multiple external calls
322: bool qeSigVerified = sigVerifyLib.verifyES256Signature(
                pckSignedQeReportBytes, authDataV3.qeReportSignature, pckCertPubKey
            );
325: bool quoteSigVerified = sigVerifyLib.verifyES256Signature(
                signedQuoteData, authDataV3.ecdsa256BitSignature, authDataV3.ecdsaAttestationKey
            );
```
[322](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L322) | [325](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L325)
</details>

### [G-60] Optimize `require/revert` Statements with Assembly

Using inline assembly for revert statements in Solidity can offer gas optimizations.
The typical `require` or `revert` statements in Solidity perform additional memory operations and type checks which can be avoided by using low-level assembly code.

In certain contracts, particularly those that might revert often or are otherwise sensitive to gas costs, using assembly to handle reversion can offer meaningful savings.
These savings primarily come from avoiding memory expansion costs and extra type checks that the Solidity compiler performs.

Example:
```solidity
/// calling restrictedAction(2) with a non-owner address: 24042
function restrictedAction(uint256 num)  external {
    require(owner == msg.sender, "caller is not owner");
    specialNumber = num;
}

// calling restrictedAction(2) with a non-owner address: 23734
function restrictedAction(uint256 num)  external {
    assembly {
        if sub(caller(), sload(owner.slot)) {
            mstore(0x00, 0x20) // store offset to where length of revert message is stored
            mstore(0x20, 0x13) // store length (19)
            mstore(0x40, 0x63616c6c6572206973206e6f74206f776e657200000000000000000000000000) // store hex representation of message
            revert(0x00, 0x60) // revert with data
        }
    }
    specialNumber = num;
}
```

<details>
<summary><i>56 issue instances in 8 files:</i></summary>

```solidity
File: packages/protocol/contracts/thirdparty/optimism/Bytes.sol

25: require(_length + 31 >= _length, "slice_overflow");
26: require(_start + _length >= _start, "slice_overflow");
27: require(_bytes.length >= _start + _length, "slice_outOfBounds");
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L25) | [26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L26) | [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L27)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

37: require(
            _in.length > 0,
            "RLPReader: length of an RLP item must be greater than zero to be decodable"
        );
56: require(
            itemType == RLPItemType.LIST_ITEM,
            "RLPReader: decoded item type for list is not a list item"
        );
61: require(
            listOffset + listLength == _in.length,
            "RLPReader: list item has an invalid data remainder"
        );
112: require(
            itemType == RLPItemType.DATA_ITEM,
            "RLPReader: decoded item type for bytes is not a data item"
        );
117: require(
            _in.length == itemOffset + itemLength,
            "RLPReader: bytes value contains an invalid remainder"
        );
152: require(
            _in.length > 0,
            "RLPReader: length of an RLP item must be greater than zero to be decodable"
        );
172: require(
                _in.length > strLen,
                "RLPReader: length of content must be greater than string length (short string)"
            );
```
[37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L37) | [56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L56) | [61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L61) | [112](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L112) | [117](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L117) | [152](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L152) | [172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L172)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

77: require(_key.length > 0, "MerkleTrie: empty key");
89: require(currentKeyIndex <= key.length, "MerkleTrie: key index exceeds total key length");
93: require(
                    Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
                    "MerkleTrie: invalid root hash"
                );
99: require(
                    Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
                    "MerkleTrie: invalid large internal hash"
                );
105: require(
                    Bytes.equal(currentNode.encoded, currentNodeID),
                    "MerkleTrie: invalid internal node hash"
                );
119: require(
                        value_.length > 0,
                        "MerkleTrie: value length must be greater than zero (branch)"
                    );
125: require(
                        i == proof.length - 1,
                        "MerkleTrie: value node must be last node in proof (branch)"
                    );
150: require(
                    pathRemainder.length == sharedNibbleLength,
                    "MerkleTrie: path remainder must share all nibbles with key"
                );
162: require(
                        keyRemainder.length == sharedNibbleLength,
                        "MerkleTrie: key remainder must be identical to path remainder"
                    );
172: require(
                        value_.length > 0,
                        "MerkleTrie: value length must be greater than zero (leaf)"
                    );
178: require(
                        i == proof.length - 1,
                        "MerkleTrie: value node must be last node in proof (leaf)"
                    );
191: revert("MerkleTrie: received a node with an unknown prefix");
194: revert("MerkleTrie: received an unparseable node");
198: revert("MerkleTrie: ran out of proof elements");
```
[77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L77) | [89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L89) | [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L93) | [99](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L99) | [105](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L105) | [119](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L119) | [125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L125) | [150](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L150) | [162](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L162) | [172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L172) | [178](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L178) | [191](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L191) | [194](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L194) | [198](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L198)

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

61: require(msg.sender == owner, "onlyOwner");
```
[61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L61)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

77: require(
            localEnclaveReport.reserved3.length == 96 && localEnclaveReport.reserved4.length == 60
                && localEnclaveReport.reportData.length == 64,
            "local QE report has wrong length"
        );
82: require(
            pckSignedQeReport.reserved3.length == 96 && pckSignedQeReport.reserved4.length == 60
                && pckSignedQeReport.reportData.length == 64,
            "QE report has wrong length"
        );
87: require(
            v3Quote.v3AuthData.certification.certType == 5,
            "certType must be 5: Concatenated PCK Cert Chain (PEM formatted)"
        );
91: require(
            v3Quote.v3AuthData.certification.decodedCertDataArray.length == 3, "3 certs in chain"
        );
94: require(
            v3Quote.v3AuthData.ecdsa256BitSignature.length == 64
                && v3Quote.v3AuthData.ecdsaAttestationKey.length == 64
                && v3Quote.v3AuthData.qeReportSignature.length == 64,
            "Invalid ECDSA signature format"
        );
100: require(
            v3Quote.v3AuthData.qeAuthData.parsedDataSize
                == v3Quote.v3AuthData.qeAuthData.data.length,
            "Invalid QEAuthData size"
        );
116: require(totalQuoteSize >= MINIMUM_QUOTE_LENGTH, "Invalid quote size");
279: require(certParsedSuccessfully, "splitCertificateChain failed");
```
[77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L77) | [82](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L82) | [87](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L87) | [91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L91) | [94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L94) | [100](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L100) | [116](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L116) | [279](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L279)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

57: require(der[ptr.ixs()] == 0x03, "Not type BIT STRING");
67: require(der[ptr.ixs()] == 0x04, "Not type OCTET STRING");
88: require(der[ptr.ixs()] & 0x20 == 0x20, "Not a constructed type");
142: require(der[ptr.ixs()] == 0x02, "Not type INTEGER");
143: require(der[ptr.ixf()] & 0x80 == 0, "Not positive");
155: require(der[ptr.ixs()] == 0x02, "Not type INTEGER");
156: require(der[ptr.ixf()] & 0x80 == 0, "Not positive");
180: require(der[ptr.ixs()] == 0x03, "ixs Not type BIT STRING 0x03");
182: require(der[ptr.ixf()] == 0x00, "ixf Not 0");
```
[57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L57) | [67](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L67) | [88](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L88) | [142](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L142) | [143](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L143) | [155](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L155) | [156](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L156) | [180](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L180) | [182](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L182)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

25: require(offset + len <= self.length, "invalid offset");
199: require(idx + 2 <= self.length, "invalid idx");
212: require(idx + 4 <= self.length, "unexpected idx");
225: require(idx + 32 <= self.length, "unexpected idx");
238: require(idx + 20 <= self.length, "unexpected idx");
264: require(len <= 32, "unexpected len");
265: require(idx + len <= self.length, "unexpected idx");
293: require(offset + len <= self.length, "unexpected offset");
329: require(len <= 52, "unexpected len");
335: require(char >= 0x30 && char <= 0x7A, "invalid char");
337: require(decoded <= 0x20, "invalid decoded");
365: revert("unexpected len");
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L25) | [199](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L199) | [212](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L212) | [225](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L225) | [238](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L238) | [264](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L264) | [265](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L265) | [293](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L293) | [329](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L329) | [335](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L335) | [337](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L337) | [365](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L365)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

50: revert("Unsupported algorithm");
75: revert("Unsupported algorithm");
```
[50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L50) | [75](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L75)
</details>

### [G-61] Cached Global Variables

Storing global variables in local storage might appear as a useful caching mechanism. 
However, in Solidity, accessing global variables directly is often more gas-efficient than caching them. 
Consider removing these redundant assignments and use the global variables directly.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

93: address taikoL1Address = msg.sender;
```
[93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L93)
</details>

### [G-62] Simple checks for zero `uint` can be done using `assembly` to save gas

The usage of inline `assembly` to check if variable is the `zero` can save gas compared to traditional `require` or `if` statement checks.
```solidity
    // gas 396 gas | 399 gas
    assembly {
        if iszero(value) { // use iszero(iszero(value)) for != add 3 gas
            revert(0, 0)
        }
    }
    require(value != 0); // 401 gas
    require(value == 0); // 401 gas

<details>
<summary><i>91 issue instances in 31 files:</i></summary>

```solidity
File: packages/protocol/contracts/libs/LibTrieProof.sol

46: if (_accountProof.length != 0) {
            bytes memory rlpAccount =
                SecureMerkleTrie.get(abi.encodePacked(_addr), _accountProof, _rootHash);
50: if (rlpAccount.length == 0) revert LTP_INVALID_ACCOUNT_PROOF();
```
[46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L46) | [50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L50)

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

81: if (
            block.timestamp > assignment.expiry
                || assignment.metaHash != 0 && _blk.metaHash != assignment.metaHash
                || assignment.parentMetaHash != 0 && _meta.parentMetaHash != assignment.parentMetaHash
                || assignment.maxBlockId != 0 && _meta.id > assignment.maxBlockId
                || assignment.maxProposedIn != 0 && block.number > assignment.maxProposedIn
        ) {
            revert HOOK_ASSIGNMENT_EXPIRED();
120: if (input.tip != 0 && block.coinbase != address(0)) {
            address(block.coinbase).sendEther(input.tip);
```
[81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L81) | [120](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L120)

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

108: if (params.parentMetaHash != 0 && parentMetaHash != params.parentMetaHash) {
            revert L1_UNEXPECTED_PARENT();
144: if (params.blobHash != 0) {
                if (!_config.blobReuseEnabled) revert L1_BLOB_REUSE_DISABLED();
159: if (meta_.blobHash == 0) revert L1_BLOB_NOT_FOUND();
185: if (params.txListByteOffset != 0) {
                revert L1_INVALID_PARAM();
195: if (meta_.txListByteSize == 0 || meta_.txListByteSize > _config.blockMaxTxListBytes) {
            revert L1_TXLIST_SIZE();
260: if (address(this).balance != 0) {
                msg.sender.sendEther(address(this).balance);
```
[108](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L108) | [144](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L144) | [159](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L159) | [185](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L185) | [195](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L195) | [260](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L260)

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

105: if (_tran.parentHash == 0 || _tran.blockHash == 0 || _tran.stateRoot == 0) {
            revert L1_INVALID_TRANSITION();
134: if (_proof.tier == 0 || _proof.tier < _meta.minTier || _proof.tier < ts.tier) {
            revert L1_INVALID_TIER();
280: if (tid_ == 0) {
412: if (_tier.contestBond == 0) return;
419: if (_tid == 1 && _ts.tier == 0 && inProvingWindow) {
            if (!isAssignedPover) revert L1_NOT_ASSIGNED_PROVER();
```
[105](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L105) | [134](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L134) | [280](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L280) | [412](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L412) | [419](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L419)

```solidity
File: packages/protocol/contracts/L1/libs/LibUtils.sol

43: if (tid == 0) revert L1_TRANSITION_NOT_FOUND();
```
[43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L43)

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

93: if (_maxBlocksToVerify == 0) {
111: if (tid == 0) revert L1_TRANSITION_ID_ZERO();
137: if (tid == 0) break;
246: if (
            _config.chainId <= 1 || _config.chainId == block.chainid //
                || _config.blockMaxProposals == 1
                || _config.blockRingBufferSize <= _config.blockMaxProposals + 1
                || _config.blockMaxGasLimit == 0 || _config.blockMaxTxListBytes == 0
                || _config.blockMaxTxListBytes > 128 * 1024 // calldata up to 128K
                || _config.livenessBond == 0 || _config.ethDepositRingBufferSize <= 1
                || _config.ethDepositMinCountPerBlock == 0
            // Audit recommendation, and gas tested. Processing 32 deposits (as initially set in
            // TaikoL1.sol) costs 72_502 gas.
            || _config.ethDepositMaxCountPerBlock > 32
                || _config.ethDepositMaxCountPerBlock < _config.ethDepositMinCountPerBlock
                || _config.ethDepositMinAmount == 0
                || _config.ethDepositMaxAmount <= _config.ethDepositMinAmount
                || _config.ethDepositMaxAmount > type(uint96).max || _config.ethDepositGas == 0
                || _config.ethDepositMaxFee == 0
                || _config.ethDepositMaxFee > type(uint96).max / _config.ethDepositMaxCountPerBlock
        ) return false;
```
[93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L93) | [111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L111) | [137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L137) | [246](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L246)

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

84: if (guardianIds[guardian] != 0) revert INVALID_GUARDIAN_SET();
113: if (id == 0) revert INVALID_GUARDIAN();
```
[84](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L84) | [113](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L113)

```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

153: if (blk_.verifiedTransitionId != 0) {
```
[153](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L153)

```solidity
File: packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol

68: if (_rand % 1000 == 0) return LibTiers.TIER_SGX_ZKVM;
```
[68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L68)

```solidity
File: packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol

68: if (_rand % 10 == 0) return LibTiers.TIER_SGX;
```
[68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L68)

```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

70: if (_ownerChainId == 0 || _ownerChainId == block.chainid) {
            revert XCO_INVALID_OWNER_CHAINID();
```
[70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L70)

```solidity
File: packages/protocol/contracts/L2/Lib1559Math.sol

24: if (_adjustmentFactor == 0) {
            revert EIP1559_INVALID_PARAMS();
```
[24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L24)

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

86: if (block.number == 0) {
            // This is the case in real L2 genesis
        } else if (block.number == 1) {
116: if (
            _l1BlockHash == 0 || _l1StateRoot == 0 || _l1BlockId == 0
                || (block.number != 1 && _parentGasUsed == 0)
        ) {
            revert L2_INVALID_PARAM();
296: if (basefee_ == 0) basefee_ = 1;
```
[86](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L86) | [116](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L116) | [296](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L296)

```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

33: if (_newConfig.gasTargetPerL1Block == 0) revert L2_INVALID_CONFIG();
34: if (_newConfig.basefeeAdjustmentQuotient == 0) revert L2_INVALID_CONFIG();
```
[33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L33) | [34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L34)

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

41: if (_input == 0) revert SS_INVALID_VALUE();
95: if (hopProofs.length == 0) revert SS_EMPTY_PROOF();
114: if (hop.chainId == 0 || hop.chainId == block.chainid) {
                    revert SS_INVALID_MID_HOP_CHAINID();
131: if (value == 0 || value != _loadSignalValue(address(this), signal)) {
            revert SS_SIGNAL_NOT_FOUND();
169: if (blockId_ != 0) {
            bytes32 signal = signalForChainData(_chainId, _kind, blockId_);
172: if (chainData_ == 0) revert SS_SIGNAL_NOT_FOUND();
```
[41](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L41) | [95](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L95) | [114](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L114) | [131](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L131) | [169](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L169) | [172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L172)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

242: if (invocationDelay != 0) {
                proofReceipt[msgHash] = ProofReceipt({
                    receivedAt: receivedAt,
                    preferredExecutor: _message.gasLimit == 0 ? _message.destOwner : msg.sender
                });
250: if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) {
260: if (_message.gasLimit == 0 && msg.sender != _message.destOwner) {
                revert B_PERMISSION_DENIED();
321: if (_message.gasLimit == 0 || _isLastAttempt) {
            if (msg.sender != _message.destOwner) revert B_PERMISSION_DENIED();
405: if (ctx_.msgHash == 0 || ctx_.msgHash == bytes32(PLACEHOLDER)) {
            revert B_INVALID_CONTEXT();
485: if (_gasLimit == 0) revert B_INVALID_GAS_LIMIT();
```
[242](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L242) | [250](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L250) | [260](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L260) | [321](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L321) | [405](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L405) | [485](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L485)

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

48: if (_op.amounts[i] == 0) revert VAULT_INVALID_AMOUNT();
```
[48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L48)

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

214: if (_op.amount == 0) revert VAULT_INVALID_AMOUNT();
```
[214](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L214)

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

35: if (_op.amounts[i] != 0) revert VAULT_INVALID_AMOUNT();
```
[35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L35)

```solidity
File: packages/protocol/contracts/tokenvault/LibBridgedToken.sol

20: if (
            _srcToken == address(0) || _srcChainId == 0 || _srcChainId == block.chainid
                || bytes(_symbol).length == 0 || bytes(_name).length == 0
        ) {
            revert BTOKEN_INVALID_PARAMS();
```
[20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L20)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

202: require(
                firstByteOfContent != 0x00,
                "RLPReader: length of content must not have any leading zeros (long string)"
            );
248: require(
                firstByteOfContent != 0x00,
                "RLPReader: length of content must not have any leading zeros (long list)"
            );
287: if (_length == 0) {
```
[202](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L202) | [248](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L248) | [287](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L287)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

60: if (b[i] != 0) {
```
[60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L60)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

91: if (currentKeyIndex == 0) {
                // First proof element is always the root node.
                require(
                    Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
                    "MerkleTrie: invalid root hash"
                );
```
[91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L91)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

111: if (balance == 0) return (0, 0);
```
[111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L111)

```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

34: if (
            merkleRoot == 0x0 || claimStart == 0 || claimEnd == 0 || claimStart > block.timestamp
                || claimEnd < block.timestamp
        ) revert CLAIM_NOT_ONGOING();
```
[34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L34)

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

137: if (recipients[_recipient].grant.amount != 0) revert ALREADY_GRANTED();
154: if (amountVoided == 0) revert NOTHING_TO_VOID();
255: if (_amount == 0) return 0;
256: if (_start == 0) return _amount;
259: if (_period == 0) return _amount;
268: if (_grant.amount == 0) revert INVALID_GRANT();
274: if (_start == 0 || _period == 0) {
            if (_cliff > 0) revert INVALID_GRANT();
```
[137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L137) | [154](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L154) | [255](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L255) | [256](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L256) | [259](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L259) | [268](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L268) | [274](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L274)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

134: if (
                (notBeforeTag != 0x17 && notBeforeTag == 0x18)
                    || (notAfterTag != 0x17 && notAfterTag != 0x18)
            ) {
                return (false, cert);
189: if (der[tbsPtr.ixs()] != 0xA3) {
                return (false, cert);
288: if (der[internalPtr.ixs()] != 0x06) {
                return (false, pcesvn, cpusvns, fmspcBytes, pceidBytes);
303: if (der[extnValueOidPtr.ixs()] != 0x06) {
                        return (false, pcesvn, cpusvns, fmspcBytes, pceidBytes);
```
[134](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L134) | [189](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L189) | [288](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L288) | [303](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L303)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

57: require(der[ptr.ixs()] == 0x03, "Not type BIT STRING");
67: require(der[ptr.ixs()] == 0x04, "Not type OCTET STRING");
88: require(der[ptr.ixs()] & 0x20 == 0x20, "Not a constructed type");
142: require(der[ptr.ixs()] == 0x02, "Not type INTEGER");
143: require(der[ptr.ixf()] & 0x80 == 0, "Not positive");
155: require(der[ptr.ixs()] == 0x02, "Not type INTEGER");
156: require(der[ptr.ixf()] & 0x80 == 0, "Not positive");
158: if (der[ptr.ixf()] == 0) {
            return der.substring(ptr.ixf() + 1, valueLength - 1);
180: require(der[ptr.ixs()] == 0x03, "ixs Not type BIT STRING 0x03");
182: require(der[ptr.ixf()] == 0x00, "ixf Not 0");
191: if ((der[ix + 1] & 0x80) == 0) {
            length = uint8(der[ix + 1]);
```
[57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L57) | [67](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L67) | [88](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L88) | [142](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L142) | [143](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L143) | [155](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L155) | [156](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L156) | [158](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L158) | [180](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L180) | [182](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L182) | [191](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L191)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

96: if (diff != 0) {
                    return int256(diff);
345: if (len % 8 == 0) {
            // Multiple of 8 characters, no padding
            ret = (ret << 5) | decoded;
```
[96](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L96) | [345](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L345)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

125: if (uint8(decipher[decipherlen - 50]) == 0x31) {
128: } else if (uint8(decipher[decipherlen - 48]) == 0x2f) {
137: if (decipher[0] != 0 || decipher[1] != 0x01) {
141: if (decipher[i] != 0xff) {
145: if (decipher[2 + paddingLen] != 0) {
167: if (
            decipher[3 + paddingLen + digestAlgoWithParamLen] != 0x04
                || decipher[4 + paddingLen + digestAlgoWithParamLen] != 0x20
        ) {
270: if (decipher[0] != 0 || decipher[1] != 0x01) {
274: if (decipher[i] != 0xff) {
278: if (decipher[2 + paddingLen] != 0) {
```
[125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L125) | [128](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L128) | [137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L137) | [141](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L141) | [145](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L145) | [167](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L167) | [270](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L270) | [274](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L274) | [278](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L278)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

72: if (year % 4 != 0) return false;
73: if (year % 100 != 0) return true;
74: if (year % 400 != 0) return false;
```
[72](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L72) | [73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L73) | [74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L74)
</details>

### [G-63] Use Cached Contracts for Multiple External Calls

When function makes multiple calls to the same external contract, it is more gas-efficient to use a local copy of the contract.
This is because the EVM will cache the contract in memory, and subsequent calls will be cheaper.
It's especially true for contracts that are large and/or have many functions.
```solidity
    // local cache -> 6561 gas
    IToken localCache = storageContract;
    localCache.externalCall();
    localCache.externalCall();

    // direct call 6683 gas
    storageContract.externalCall();
    storageContract.externalCall();
```

<details>
<summary><i>2 issue instances in 1 files:</i></summary>

```solidity
File: packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

/// @audit function _burnToken() make external call of `usdc` - 2 times
48: usdc.transferFrom(_from, address(this), _amount);
49: usdc.burn(_amount);
```
[48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L48) | [49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L49)
</details>

### [G-64] Consider using solady's `FixedPointMathLib`

Utilizing gas-optimized math functions from libraries like [Solady](https://github.com/Vectorized/solady/blob/main/src/utils/FixedPointMathLib.sol) can lead to more efficient smart contracts.
This is particularly beneficial in contracts where these operations are frequently used.

<details>
<summary><i>73 issue instances in 19 files:</i></summary>

```solidity
File: packages/protocol/contracts/L1/gov/TaikoGovernor.sol

124: return 1_000_000_000 ether / 10_000; // 0.01% of Taiko Token
```
[124](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L124)

```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

83: uint96 fee = uint96(_config.ethDepositMaxFee.min(block.basefee * _config.ethDepositGas));
```
[83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L83)

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

21: uint256 public constant MAX_BYTES_PER_BLOB = 4096 * 32;
```
[21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L21)

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

415: + _tier.provingWindow * 60 >= block.timestamp;
```
[415](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L415)

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

152: uint256(ITierProvider(tierProvider).getTier(ts.tier).cooldownWindow) * 60
251: || _config.blockMaxTxListBytes > 128 * 1024 // calldata up to 128K
262: || _config.ethDepositMaxFee > type(uint96).max / _config.ethDepositMaxCountPerBlock
```
[152](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L152) | [251](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L251) | [262](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L262)

```solidity
File: packages/protocol/contracts/L1/TaikoData.sol

123: bytes32 key; // slot 1, only written/read for the 1st state transition.
```
[123](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L123)

```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

215: ethDepositMaxFee: 1 ether / 10,
```
[215](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L215)

```solidity
File: packages/protocol/contracts/L2/Lib1559Math.sol

41: uint256 input = _gasExcess * LibFixedPointMath.SCALING_FACTOR / _adjustmentFactor;
28: return _ethQty(_gasExcess, _adjustmentFactor) / LibFixedPointMath.SCALING_FACTOR
28: return _ethQty(_gasExcess, _adjustmentFactor) / LibFixedPointMath.SCALING_FACTOR
            / _adjustmentFactor;
41: uint256 input = _gasExcess * LibFixedPointMath.SCALING_FACTOR / _adjustmentFactor;
```
[41](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L41) | [28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L28) | [28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L28) | [41](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L41)

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

213: config_.gasTargetPerL1Block = 15 * 1e6 * 4;
213: config_.gasTargetPerL1Block = 15 * 1e6 * 4;
280: uint256 issuance = numL1Blocks * _config.gasTargetPerL1Block;
291: gasExcess_, uint256(_config.basefeeAdjustmentQuotient) * _config.gasTargetPerL1Block
```
[213](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L213) | [213](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L213) | [280](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L280) | [291](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L291)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

41: i *= 256;
39: while (_len / i != 0) {
47: out_[i] = bytes1(uint8((_len / (256 ** (lenLen - i))) % 256));
47: out_[i] = bytes1(uint8((_len / (256 ** (lenLen - i))) % 256));
```
[41](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L41) | [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L39) | [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L47) | [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L47)

```solidity
File: packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol

40: x = x - k * 54_916_777_467_707_473_351_141_471_128;
46: y = ((y * x) >> 96) + 57_155_421_227_552_351_082_224_309_758_442;
48: p = ((p * y) >> 96) + 28_719_021_644_029_726_153_956_944_680_412_240;
49: p = p * x + (4_385_272_521_454_847_904_659_076_985_693_276 << 96);
54: q = ((q * x) >> 96) + 50_020_603_652_535_783_019_961_831_881_945;
55: q = ((q * x) >> 96) - 533_845_033_583_426_703_283_633_433_725_380;
56: q = ((q * x) >> 96) + 3_604_857_256_930_695_427_073_651_918_091_429;
57: q = ((q * x) >> 96) - 14_423_608_567_350_463_180_887_372_962_807_573;
58: q = ((q * x) >> 96) + 26_449_188_498_355_588_339_934_803_723_976_023;
77: (uint256(r) * 3_822_833_074_963_236_453_042_738_258_902_158_003_155_416_615_667)
33: x = (x << 78) / 5 ** 18;
39: int256 k = ((x << 96) / 54_916_777_467_707_473_351_141_471_128 + 2 ** 95) >> 96;
33: x = (x << 78) / 5 ** 18;
39: int256 k = ((x << 96) / 54_916_777_467_707_473_351_141_471_128 + 2 ** 95) >> 96;
```
[40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L40) | [46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L46) | [48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L48) | [49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L49) | [54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L54) | [55](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L55) | [56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L56) | [57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L57) | [58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L58) | [77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L77) | [33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L33) | [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L39) | [33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L33) | [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L39)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

117: uint256 timeBasedAllowance = balance
            * (block.timestamp.min(claimEnd + withdrawalWindow) - claimEnd) / withdrawalWindow;
```
[117](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L117)

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

198: costToWithdraw = _amountUnlocked * r.grant.costPerToken - r.costPaid;
264: return _amount * uint64(block.timestamp - _start) / _period;
197: uint128 _amountUnlocked = amountUnlocked / 1e18; // divide first
264: return _amount * uint64(block.timestamp - _start) / _period;
```
[198](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L198) | [264](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L264) | [197](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L197) | [264](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L264)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

359: ? uint16(bytes2(svnValueBytes)) / 256
```
[359](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L359)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

158: uint256 acc = lowerDigit * (16 ** (2 * i));
158: uint256 acc = lowerDigit * (16 ** (2 * i));
159: acc += upperDigit * (16 ** ((2 * i) + 1));
159: acc += upperDigit * (16 ** ((2 * i) + 1));
155: uint256 upperDigit = digits / 16;
158: uint256 acc = lowerDigit * (16 ** (2 * i));
159: acc += upperDigit * (16 ** ((2 * i) + 1));
```
[158](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L158) | [158](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L158) | [159](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L159) | [159](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L159) | [155](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L155) | [158](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L158) | [159](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L159)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

145: return uint256(der.readBytesN(ptr.ixf(), len) >> (32 - len) * 8);
203: der.readBytesN(ix + 2, lengthbytesLength) >> (32 - lengthbytesLength) * 8
```
[145](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L145) | [203](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L203)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

93: mask = ~(2 ** (8 * (32 - shortest + idx)) - 1);
344: uint256 bitlen = len * 5;
93: mask = ~(2 ** (8 * (32 - shortest + idx)) - 1);
```
[93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L93) | [344](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L344) | [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L93)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

13: This program is free software: you can redistribute it and/or modify
24: along with this program.  If not, see <http://www.gnu.org/licenses/>.
27: https://csrc.nist.gov/CSRC/media/Projects/Cryptographic-Algorithm-Validation-Program/documents/dss/186-2rsatestvectors.zip
27: https://csrc.nist.gov/CSRC/media/Projects/Cryptographic-Algorithm-Validation-Program/documents/dss/186-2rsatestvectors.zip
27: https://csrc.nist.gov/CSRC/media/Projects/Cryptographic-Algorithm-Validation-Program/documents/dss/186-2rsatestvectors.zip
27: https://csrc.nist.gov/CSRC/media/Projects/Cryptographic-Algorithm-Validation-Program/documents/dss/186-2rsatestvectors.zip
27: https://csrc.nist.gov/CSRC/media/Projects/Cryptographic-Algorithm-Validation-Program/documents/dss/186-2rsatestvectors.zip
27: https://csrc.nist.gov/CSRC/media/Projects/Cryptographic-Algorithm-Validation-Program/documents/dss/186-2rsatestvectors.zip
```
[13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L13) | [24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L24) | [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L27) | [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L27) | [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L27) | [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L27) | [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L27) | [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L27)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

21: yrs += (uint8(x509Time[0]) - 48) * 1000 + (uint8(x509Time[1]) - 48) * 100;
21: yrs += (uint8(x509Time[0]) - 48) * 1000 + (uint8(x509Time[1]) - 48) * 100;
24: yrs += (uint8(x509Time[offset + 0]) - 48) * 10 + uint8(x509Time[offset + 1]) - 48;
25: mnths = (uint8(x509Time[offset + 2]) - 48) * 10 + uint8(x509Time[offset + 3]) - 48;
26: dys += (uint8(x509Time[offset + 4]) - 48) * 10 + uint8(x509Time[offset + 5]) - 48;
27: hrs += (uint8(x509Time[offset + 6]) - 48) * 10 + uint8(x509Time[offset + 7]) - 48;
28: mins += (uint8(x509Time[offset + 8]) - 48) * 10 + uint8(x509Time[offset + 9]) - 48;
29: secs += (uint8(x509Time[offset + 10]) - 48) * 10 + uint8(x509Time[offset + 11]) - 48;
60: timestamp += uint256(monthDays[i - 1]) * 86_400; // Days in seconds
63: timestamp += uint256(day - 1) * 86_400; // Days in seconds
64: timestamp += uint256(hour) * 3600; // Hours in seconds
65: timestamp += uint256(minute) * 60; // Minutes in seconds
```
[21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L21) | [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L21) | [24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L24) | [25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L25) | [26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L26) | [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L27) | [28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L28) | [29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L29) | [60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L60) | [63](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L63) | [64](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L64) | [65](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L65)
</details>

### [G-65] Avoid Zero to Non-Zero Storage Writes Where Possible

Changing a storage variable from zero to non-zero costs 22,100 gas in total. (20,000 gas for a zero to non-zero write and 2,100 for a cold storage access)
Consider using non-zero architecture to avoid high gas costs for zero to non-zero storage writes.

Example:

```solidity
- uint256 public counter = 0;  // rewrite this costs more
+ uint256 public counter = 1;  // rewrite this costs less
```

<details>
<summary><i>23 issue instances in 11 files:</i></summary>

```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

70: __paused = _TRUE;
79: __paused = _FALSE;
111: __paused = _FALSE;
125: __reentry = _reentry;
```
[70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L70) | [79](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L79) | [111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L111) | [125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L125)

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

88: guardianIds[guardian] = guardians.length;
94: minGuardians = _minGuardians;
116: _approvals[version][_hash] |= 1 << (id - 1);
```
[88](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L88) | [94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L94) | [116](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L116)

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

96: gasExcess = _gasExcess;
151: lastSyncedBlock = _l1BlockId;
155: publicInputHash = publicInputHashNew;
```
[96](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L96) | [151](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L151) | [155](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L155)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

74: srcChainId = _srcChainId;
75: __srcDecimals = _decimals;
```
[74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L74) | [75](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L75)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

50: migratingInbound = _migratingInbound;
```
[50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L50)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

48: srcChainId = _srcChainId;
```
[48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L48)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

57: srcChainId = _srcChainId;
58: __symbol = _symbol;
59: __name = _name;
```
[57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L57) | [58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L58) | [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L59)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

217: instances[nextInstanceId] = Instance(_instances[i], validSince);
```
[217](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L217)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

71: withdrawalWindow = _withdrawalWindow;
```
[71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L71)

```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

91: claimStart = _claimStart;
92: claimEnd = _claimEnd;
93: merkleRoot = _merkleRoot;
```
[91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L91) | [92](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L92) | [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L93)

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

123: _checkLocalEnclaveReport = !_checkLocalEnclaveReport;
```
[123](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L123)
</details>

### [G-66] Consider Packing Small `uint` When it's Possible

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

<details>
<summary><i>15 issue instances in 6 files:</i></summary>

```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

21: uint8 private __reentry;
23: uint8 private __paused;
```
[21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L21) | [23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L23)

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

27: uint32 public version;
30: uint32 public minGuardians;
```
[27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L27) | [30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L30)

```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

16: uint64 public ownerChainId;
19: uint64 public nextTxId;
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L16) | [19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L19)

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

47: uint64 public gasExcess;
50: uint64 public lastSyncedBlock;
```
[47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L47) | [50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L50)

```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

18: uint64 public claimStart;
21: uint64 public claimEnd;
```
[18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L18) | [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L21)

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

68: uint128 public totalAmountGranted;
71: uint128 public totalAmountVoided;
74: uint128 public totalAmountWithdrawn;
77: uint128 public totalCostPaid;
82: uint128[44] private __gap;
```
[68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L68) | [71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L71) | [74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L74) | [77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L77) | [82](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L82)
</details>

### [G-67] Consider Using `calldata` Instead of `memory` for Function Parameters

When function parameters are not being modified within the function, it can be more gas efficient 
to use `calldata` instead of `memory`. The Ethereum Virtual Machine (EVM) does not need to copy 
parameters marked with `calldata` from `calldata` to `memory`, saving gas. This is particularly effective 
for larger arrays and structs.

<details>
<summary><i>9 issue instances in 3 files:</i></summary>

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

/// @audit `_blk` not modified within function
62: function onBlockProposed(
        TaikoData.Block memory _blk,
        TaikoData.BlockMetadata memory _meta,
        bytes memory _data
    )
        external
        payable
        nonReentrant
        onlyFromNamed("taiko")
    {
/// @audit `_assignment` not modified within function
137: function hashAssignment(
        ProverAssignment memory _assignment,
        address _taikoL1Address,
        bytes32 _blobHash
    )
        public
        view
        returns (bytes32)
    {
```
[62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L62) | [137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L137)

```solidity
File: packages/protocol/contracts/L1/libs/LibUtils.sol

/// @audit `_config` not modified within function
23: function getTransition(
        TaikoData.State storage _state,
        TaikoData.Config memory _config,
        uint64 _blockId,
        bytes32 _parentHash
    )
        external
        view
        returns (TaikoData.TransitionState storage)
    {
/// @audit `_config` not modified within function
52: function getBlock(
        TaikoData.State storage _state,
        TaikoData.Config memory _config,
        uint64 _blockId
    )
        external
        view
        returns (TaikoData.Block storage blk_, uint64 slot_)
    {
```
[23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L23) | [52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L52)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

/// @audit `publicKey` not modified within function
23: function verifyAttStmtSignature(
        bytes memory tbs,
        bytes memory signature,
        PublicKey memory publicKey,
        Algorithm alg
    )
        public
        view
        returns (bool)
    {
/// @audit `publicKey` not modified within function
53: function verifyCertificateSignature(
        bytes memory tbs,
        bytes memory signature,
        PublicKey memory publicKey,
        CertSigAlgorithm alg
    )
        public
        view
        returns (bool)
    {
/// @audit `publicKey` not modified within function
78: function verifyRS256Signature(
        bytes memory tbs,
        bytes memory signature,
        bytes memory publicKey
    )
        public
        view
        returns (bool sigValid)
    {
/// @audit `publicKey` not modified within function
95: function verifyRS1Signature(
        bytes memory tbs,
        bytes memory signature,
        bytes memory publicKey
    )
        public
        view
        returns (bool sigValid)
    {
/// @audit `signature, publicKey` not modified within function
112: function verifyES256Signature(
        bytes memory tbs,
        bytes memory signature,
        bytes memory publicKey
    )
        public
        view
        returns (bool sigValid)
    {
```
[23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L23) | [53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L53) | [78](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L78) | [95](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L95) | [112](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L112)
</details>

### [G-68] Avoid Unnecessary Gas Usage with Shorter `require()/revert()` Strings

Long require() or revert() strings that exceed 32 bytes can lead to extra gas costs.

This unnecessary gas consumption can be avoided by ensuring your `require()` or `revert()` strings are 32 bytes or shorter.
This optimizes your contract's gas efficiency without compromising the clarity and specificity of your error messages.

<details>
<summary><i>30 issue instances in 3 files:</i></summary>

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

37: require(
            _in.length > 0,
            "RLPReader: length of an RLP item must be greater than zero to be decodable"
        );
56: require(
            itemType == RLPItemType.LIST_ITEM,
            "RLPReader: decoded item type for list is not a list item"
        );
61: require(
            listOffset + listLength == _in.length,
            "RLPReader: list item has an invalid data remainder"
        );
112: require(
            itemType == RLPItemType.DATA_ITEM,
            "RLPReader: decoded item type for bytes is not a data item"
        );
117: require(
            _in.length == itemOffset + itemLength,
            "RLPReader: bytes value contains an invalid remainder"
        );
152: require(
            _in.length > 0,
            "RLPReader: length of an RLP item must be greater than zero to be decodable"
        );
172: require(
                _in.length > strLen,
                "RLPReader: length of content must be greater than string length (short string)"
            );
182: require(
                strLen != 1 || firstByteOfContent >= 0x80,
                "RLPReader: invalid prefix, single byte < 0x80 are not prefixed (short string)"
            );
192: require(
                _in.length > lenOfStrLen,
                "RLPReader: length of content must be > than length of string length (long string)"
            );
202: require(
                firstByteOfContent != 0x00,
                "RLPReader: length of content must not have any leading zeros (long string)"
            );
212: require(
                strLen > 55,
                "RLPReader: length of content must be greater than 55 bytes (long string)"
            );
217: require(
                _in.length > lenOfStrLen + strLen,
                "RLPReader: length of content must be greater than total length (long string)"
            );
228: require(
                _in.length > listLen,
                "RLPReader: length of content must be greater than list length (short list)"
            );
238: require(
                _in.length > lenOfListLen,
                "RLPReader: length of content must be > than length of list length (long list)"
            );
248: require(
                firstByteOfContent != 0x00,
                "RLPReader: length of content must not have any leading zeros (long list)"
            );
258: require(
                listLen > 55,
                "RLPReader: length of content must be greater than 55 bytes (long list)"
            );
263: require(
                _in.length > lenOfListLen + listLen,
                "RLPReader: length of content must be greater than total length (long list)"
            );
```
[37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L37) | [56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L56) | [61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L61) | [112](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L112) | [117](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L117) | [152](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L152) | [172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L172) | [182](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L182) | [192](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L192) | [202](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L202) | [212](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L212) | [217](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L217) | [228](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L228) | [238](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L238) | [248](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L248) | [258](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L258) | [263](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L263)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

89: require(currentKeyIndex <= key.length, "MerkleTrie: key index exceeds total key length");
99: require(
                    Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
                    "MerkleTrie: invalid large internal hash"
                );
105: require(
                    Bytes.equal(currentNode.encoded, currentNodeID),
                    "MerkleTrie: invalid internal node hash"
                );
119: require(
                        value_.length > 0,
                        "MerkleTrie: value length must be greater than zero (branch)"
                    );
125: require(
                        i == proof.length - 1,
                        "MerkleTrie: value node must be last node in proof (branch)"
                    );
150: require(
                    pathRemainder.length == sharedNibbleLength,
                    "MerkleTrie: path remainder must share all nibbles with key"
                );
162: require(
                        keyRemainder.length == sharedNibbleLength,
                        "MerkleTrie: key remainder must be identical to path remainder"
                    );
172: require(
                        value_.length > 0,
                        "MerkleTrie: value length must be greater than zero (leaf)"
                    );
178: require(
                        i == proof.length - 1,
                        "MerkleTrie: value node must be last node in proof (leaf)"
                    );
191: revert("MerkleTrie: received a node with an unknown prefix");
194: revert("MerkleTrie: received an unparseable node");
198: revert("MerkleTrie: ran out of proof elements");
```
[89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L89) | [99](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L99) | [105](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L105) | [119](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L119) | [125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L125) | [150](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L150) | [162](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L162) | [172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L172) | [178](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L178) | [191](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L191) | [194](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L194) | [198](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L198)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

87: require(
            v3Quote.v3AuthData.certification.certType == 5,
            "certType must be 5: Concatenated PCK Cert Chain (PEM formatted)"
        );
```
[87](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L87)
</details>

### [G-69] Use `unchecked` for division which do not divide by -X sonce they can't overflow

Solidity introduced the `unchecked` block in version 0.8.0 as a measure to provide control over arithmetic operations. 
Any operation inside this block will not trigger the built-in overflow and underflow checks, thus saving gas costs. 
Since a division operation between two `uint`s (unsigned integers) can never result in an overflow or underflow, it's an ideal candidate for the use of `unchecked {}` block.
This practice enables optimal gas usage without risking any arithmetic anomalies.

<details>
<summary><i>14 issue instances in 9 files:</i></summary>

```solidity
File: packages/protocol/contracts/L1/gov/TaikoGovernor.sol

124: return 1_000_000_000 ether / 10_000; // 0.01% of Taiko Token
```
[124](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L124)

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

262: || _config.ethDepositMaxFee > type(uint96).max / _config.ethDepositMaxCountPerBlock
```
[262](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L262)

```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

215: ethDepositMaxFee: 1 ether / 10,
```
[215](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L215)

```solidity
File: packages/protocol/contracts/L2/Lib1559Math.sol

28: return _ethQty(_gasExcess, _adjustmentFactor) / LibFixedPointMath.SCALING_FACTOR
28: return _ethQty(_gasExcess, _adjustmentFactor) / LibFixedPointMath.SCALING_FACTOR
            / _adjustmentFactor;
41: uint256 input = _gasExcess * LibFixedPointMath.SCALING_FACTOR / _adjustmentFactor;
```
[28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L28) | [28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L28) | [41](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L41)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

39: while (_len / i != 0) {
47: out_[i] = bytes1(uint8((_len / (256 ** (lenLen - i))) % 256));
```
[39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L39) | [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L47)

```solidity
File: packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol

33: x = (x << 78) / 5 ** 18;
39: int256 k = ((x << 96) / 54_916_777_467_707_473_351_141_471_128 + 2 ** 95) >> 96;
```
[33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L33) | [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L39)

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

197: uint128 _amountUnlocked = amountUnlocked / 1e18; // divide first
264: return _amount * uint64(block.timestamp - _start) / _period;
```
[197](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L197) | [264](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L264)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

359: ? uint16(bytes2(svnValueBytes)) / 256
```
[359](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L359)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

155: uint256 upperDigit = digits / 16;
```
[155](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L155)
</details>

### [G-70] State Variables Should Be `immutable` Since They Are Only Set in the Constructor

State variables that are only set in the constructor and are not modified elsewhere in the code should be declared as `immutable`.
This can optimize gas usage as `immutable` variables are read from code, not from storage.

<details>
<summary><i>2 issue instances in 2 files:</i></summary>

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

57: owner = msg.sender;
```
[57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L57)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

21: ES256VERIFIER = es256Verifier;
```
[21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L21)
</details>

### [G-71] Use solady library where possible to save gas

The following OpenZeppelin imports have a Solady equivalent, as such they can be used to save GAS as Solady modules have been specifically designed to be as GAS efficient as possible.

<details>
<summary><i>54 issue instances in 28 files:</i></summary>

```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

3: import "@openzeppelin/contracts-upgradeable/proxy/utils/Initializable.sol";
```
[3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L3)

```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

3: import "@openzeppelin/contracts/proxy/utils/UUPSUpgradeable.sol";
5: import "@openzeppelin/contracts-upgradeable/access/Ownable2StepUpgradeable.sol";
```
[3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L3) | [5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L5)

```solidity
File: packages/protocol/contracts/libs/LibAddress.sol

3: import "@openzeppelin/contracts/utils/Address.sol";
5: import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol";
6: import "@openzeppelin/contracts/utils/introspection/IERC165.sol";
7: import "@openzeppelin/contracts/interfaces/IERC1271.sol";
```
[3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L3) | [5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L5) | [6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L6) | [7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L7)

```solidity
File: packages/protocol/contracts/L1/gov/TaikoGovernor.sol

3: import "@openzeppelin/contracts-upgradeable/governance/GovernorUpgradeable.sol";
5: import
    "@openzeppelin/contracts-upgradeable/governance/compatibility/GovernorCompatibilityBravoUpgradeable.sol";
7: import "@openzeppelin/contracts-upgradeable/governance/extensions/GovernorVotesUpgradeable.sol";
8: import
    "@openzeppelin/contracts-upgradeable/governance/extensions/GovernorVotesQuorumFractionUpgradeable.sol";
10: import
    "@openzeppelin/contracts-upgradeable/governance/extensions/GovernorTimelockControlUpgradeable.sol";
```
[3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L3) | [5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L5) | [7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L7) | [8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L8) | [10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L10)

```solidity
File: packages/protocol/contracts/L1/gov/TaikoTimelockController.sol

3: import "@openzeppelin/contracts-upgradeable/governance/TimelockControllerUpgradeable.sol";
```
[3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L3)

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

3: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
5: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```
[3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L3) | [5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L5)

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

3: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```
[3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L3)

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

3: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```
[3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L3)

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

3: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```
[3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L3)

```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

3: import "@openzeppelin/contracts-upgradeable/token/ERC20/ERC20Upgradeable.sol";
5: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20SnapshotUpgradeable.sol";
6: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20VotesUpgradeable.sol";
```
[3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L3) | [5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L5) | [6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L6)

```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

3: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```
[3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L3)

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

3: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
5: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```
[3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L3) | [5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L5)

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

3: import "@openzeppelin/contracts/utils/math/SafeCast.sol";
```
[3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L3)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

3: import "@openzeppelin/contracts/utils/Address.sol";
```
[3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L3)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

3: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/IERC20MetadataUpgradeable.sol";
5: import "@openzeppelin/contracts/utils/Strings.sol";
6: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20SnapshotUpgradeable.sol";
7: import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20VotesUpgradeable.sol";
```
[3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L3) | [5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L5) | [6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L6) | [7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L7)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

3: import "@openzeppelin/contracts-upgradeable/token/ERC721/ERC721Upgradeable.sol";
5: import "@openzeppelin/contracts/utils/Strings.sol";
```
[3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L3) | [5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L5)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

3: import "@openzeppelin/contracts/utils/Strings.sol";
5: import "@openzeppelin/contracts-upgradeable/token/ERC1155/ERC1155Upgradeable.sol";
6: import
    "@openzeppelin/contracts-upgradeable/token/ERC1155/extensions/IERC1155MetadataURIUpgradeable.sol";
```
[3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L3) | [5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L5) | [6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L6)

```solidity
File: packages/protocol/contracts/tokenvault/BaseVault.sol

3: import "@openzeppelin/contracts-upgradeable/utils/introspection/IERC165Upgradeable.sol";
5: import "@openzeppelin/contracts/proxy/ERC1967/ERC1967Proxy.sol";
```
[3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L3) | [5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L5)

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

3: import "@openzeppelin/contracts/token/ERC1155/IERC1155.sol";
5: import "@openzeppelin/contracts-upgradeable/token/ERC1155/utils/ERC1155ReceiverUpgradeable.sol";
```
[3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L3) | [5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L5)

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

3: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
5: import "@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol";
6: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```
[3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L3) | [5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L5) | [6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L6)

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

3: import "@openzeppelin/contracts/token/ERC721/IERC721.sol";
5: import "@openzeppelin/contracts/token/ERC721/IERC721Receiver.sol";
```
[3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L3) | [5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L5)

```solidity
File: packages/protocol/contracts/tokenvault/LibBridgedToken.sol

3: import "@openzeppelin/contracts/utils/Strings.sol";
```
[3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L3)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

3: import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol";
```
[3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L3)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

3: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
5: import "@openzeppelin/contracts/governance/utils/IVotes.sol";
```
[3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L3) | [5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L5)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

3: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
```
[3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L3)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

3: import "@openzeppelin/contracts/token/ERC721/IERC721.sol";
```
[3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L3)

```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

3: import "@openzeppelin/contracts/utils/cryptography/MerkleProof.sol";
```
[3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L3)

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

3: import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol";
5: import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
6: import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";
```
[3](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L3) | [5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L5) | [6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L6)
</details>

### [G-72] Avoid Inverting `if`-`else` Conditions

Inverting the condition of an `if`-`else`-statement results in extra gas consumption.
Consider simplifying the condition to reduce gas costs.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

77: if (!isAuthorized[msg.sender]) revert SS_UNAUTHORIZED();
        return _syncChainData(_chainId, _kind, _blockId, _chainData);
    }

    /// @inheritdoc ISignalService
    /// @dev This function may revert.
    function proveSignalReceived(
        uint64 _chainId,
        address _app,
        bytes32 _signal,
        bytes calldata _proof
    )
        public
        virtual
        validSender(_app)
        nonZeroValue(_signal)
    {
        HopProof[] memory hopProofs = abi.decode(_proof, (HopProof[]));
        if (hopProofs.length == 0) revert SS_EMPTY_PROOF();

        uint64 chainId = _chainId;
        address app = _app;
        bytes32 signal = _signal;
        bytes32 value = _signal;
        address signalService = resolve(chainId, "signal_service", false);

        HopProof memory hop;
        for (uint256 i; i < hopProofs.length; ++i) {
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
```
[77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L77)
</details>

### [G-73] Use `uint256(1)`/`uint256(2)` instead of `true`/`false` to save gas for changes

Boolean variables in Solidity are more expensive than `uint256` or any type that takes up a full word, due to additional gas costs associated with write operations.
When using boolean variables, each write operation emits an extra SLOAD to read the slot's contents, replace the bits taken up by the boolean, and then write back.
This process cannot be disabled and leads to extra gas consumption.

By using `uint256(1)` and `uint256(2)` for representing true and false states, you can avoid a `Gwarmaccess` (100 gas) cost and also avoid a `Gsset` (20000 gas) cost when changing from `false` to `true`, after having been `true` in the past.
This approach helps in optimizing gas usage, making your contract more cost-effective.

[Usage in OpenZeppelin ReentrancyGuard.sol](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/58f635312aa21f947cae5f8578638a85aa2519f5/contracts/security/ReentrancyGuard.sol#L23-L27)

<details>
<summary><i>10 issue instances in 7 files:</i></summary>

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

21: mapping(address addr => bool authorized) public isAuthorized;
```
[21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L21)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

42: mapping(address addr => bool banned) public addressBanned;
```
[42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L42)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

14: bool public migratingInbound;
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L14)

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

52: mapping(address btoken => bool blacklisted) public btokenBlacklist;
```
[52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L52)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

55: mapping(address instanceAddress => bool alreadyAttested) public addressRegistered;
```
[55](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L55)

```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

12: mapping(bytes32 hash => bool claimed) public isClaimed;
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L12)

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

38: bool private _checkLocalEnclaveReport;
39: mapping(bytes32 enclave => bool trusted) private _trustedUserMrEnclave;
40: mapping(bytes32 signer => bool trusted) private _trustedUserMrSigner;
47: mapping(uint256 idx => mapping(bytes serialNum => bool revoked)) private _serialNumIsRevoked;
```
[38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L38) | [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L39) | [40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L40) | [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L47)
</details>

### [G-74] Use Bit Shifting for Multiplication by Powers of Two

When multiplying by powers of two (e.g., 2, 4, 8), it is more efficient to use bit shifting.

`<x> * 2` can be replaced with `<x> << 1`, as both operations are equivalent.
However, the multiplication approach may incur additional gas overhead due to potential jumps to and from a compiler utility function that introduces checks.

This overhead can be minimized by using bit shifting when multiplying by powers of two.

<details>
<summary><i>4 issue instances in 3 files:</i></summary>

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

21: uint256 public constant MAX_BYTES_PER_BLOB = 4096 * 32;
```
[21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L21)

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

213: config_.gasTargetPerL1Block = 15 * 1e6 * 4;
```
[213](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L213)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

145: return uint256(der.readBytesN(ptr.ixf(), len) >> (32 - len) * 8);
203: der.readBytesN(ix + 2, lengthbytesLength) >> (32 - lengthbytesLength) * 8
```
[145](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L145) | [203](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L203)
</details>

### [G-75] Keep Strings Smaller Than 32 Bytes for Storage Efficiency

In Solidity, how strings are stored in the contract's storage can have implications for gas costs. Specifically, strings that are 32 bytes or longer are stored differently than shorter strings:

- If the length of the string is 32 bytes or longer, the storage slot for the string variable will hold the value of the length of the string multiplied by 2, plus 1. The actual data of the string is stored in a separate slot, the address of which is the keccak256 hash of the original storage slot.

- For strings shorter than 32 bytes, the length multiplied by 2 is stored in the least significant byte of its storage slot. The remaining bytes of the slot store the string data itself.

Keeping strings shorter than 32 bytes could therefore yield gas savings due to more efficient storage use.

<details>
<summary><i>2 issue instances in 1 files:</i></summary>

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

/// @audit variable initial value is not set, it should be set to a value shorter than 32 bytes
22: string private __symbol;
/// @audit variable initial value is not set, it should be set to a value shorter than 32 bytes
25: string private __name;
```
[22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L22) | [25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L25)
</details>

### [G-76] Use Multiple `require()` Statements Instead of chaining

Breaking down complex conditions in `require()` into separate statements improves code readability and gas efficiency.
Instead of chaining conditions with `&&` within a single `require()`, consider using separate `require()` statements for each condition.

<details>
<summary><i>4 issue instances in 2 files:</i></summary>

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

77: require(
            localEnclaveReport.reserved3.length == 96 && localEnclaveReport.reserved4.length == 60
                && localEnclaveReport.reportData.length == 64,
            "local QE report has wrong length"
        );
82: require(
            pckSignedQeReport.reserved3.length == 96 && pckSignedQeReport.reserved4.length == 60
                && pckSignedQeReport.reportData.length == 64,
            "QE report has wrong length"
        );
94: require(
            v3Quote.v3AuthData.ecdsa256BitSignature.length == 64
                && v3Quote.v3AuthData.ecdsaAttestationKey.length == 64
                && v3Quote.v3AuthData.qeReportSignature.length == 64,
            "Invalid ECDSA signature format"
        );
```
[77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L77) | [82](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L82) | [94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L94)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

335: require(char >= 0x30 && char <= 0x7A, "invalid char");
```
[335](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L335)
</details>

### [G-77] Delete Unused State Variables

State variables that aren't used in the contract not only clutter the codebase but also consume unnecessary gas during deployment.
Specifically, setting non-zero initial values for state variables costs significant gas.
By removing these unused state variables, you can save on both deployment gas and potential future storage gas costs.
This optimization not only reduces gas expenditures but also enhances code clarity and maintainability.
Always ensure a thorough review to confirm that these variables are indeed redundant before removal.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol

/// @audit Unused state variable: LOW_28_MASK
6: uint256 constant LOW_28_MASK =
        0x00000000ffffffffffffffffffffffffffffffffffffffffffffffffffffffff;
```
[6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L6)
</details>

### [G-78] Consider Using Mappings Instead of Arrays to Save Gas

When you use arrays in Solidity, extra bytecode is generated to check whether the index being accessed is valid.
This ensures you don't read unallocated or dangerous memory locations, but it costs additional gas.

Mappings, being simple key-value pairs, do not have this check, which can save around 2102 gas per read operation.
Below array reads that can be replaced with mappings and saves 2102 on each read.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

75: delete guardianIds[guardians[i]];
```
[75](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L75)
</details>

### [G-79] Mark Functions That Revert For Normal Users As `payable`

Functions guaranteed to revert when called by normal users can be marked `payable`.
If a function modifier such as onlyOwner is used, the function will revert if a normal user tries to pay the function.
Marking the function as payable will lower the gas cost for legitimate callers because the compiler will not include checks for whether a payment was provided.

The extra opcodes avoided are CALLVALUE(2),DUP1(3),ISZERO(3),PUSH2(3),JUMPI(10),PUSH1(3),DUP1(3),REVERT(0),JUMPDEST(1),POP(2), which costs an average of about 21 gas per call to the function, in addition to the extra deployment cost.

<details>
<summary><i>45 issue instances in 23 files:</i></summary>

```solidity
File: packages/protocol/contracts/common/AddressManager.sol

38: function setAddress(
        uint64 _chainId,
        bytes32 _name,
        address _newAddress
    )
        external
        virtual
        onlyOwner
    {
```
[38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L38)

```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

58: function __AddressResolver_init(address _addressManager) internal virtual onlyInitializing {
```
[58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L58)

```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

95: function __Essential_init(
        address _owner,
        address _addressManager
    )
        internal
        virtual
        onlyInitializing
    {
113: function _authorizeUpgrade(address) internal virtual override onlyOwner { }
115: function _authorizePause(address) internal virtual onlyOwner { }
```
[95](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L95) | [113](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L113) | [115](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L115)

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

62: function onBlockProposed(
        TaikoData.Block memory _blk,
        TaikoData.BlockMetadata memory _meta,
        bytes memory _data
    )
        external
        payable
        nonReentrant
        onlyFromNamed("taiko")
    {
```
[62](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L62)

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

53: function setGuardians(
        address[] memory _newGuardians,
        uint8 _minGuardians
    )
        external
        onlyOwner
        nonReentrant
    {
```
[53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L53)

```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

219: function _authorizePause(address)
        internal
        view
        virtual
        override
        onlyFromOwnerOrNamed("chain_pauser")
    { }
```
[219](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L219)

```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

47: function burn(address _from, uint256 _amount) public onlyOwner {
52: function snapshot() public onlyFromOwnerOrNamed("snapshooter") {
```
[47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L47) | [52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L52)

```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

36: function onMessageInvocation(bytes calldata _data)
        external
        payable
        whenNotPaused
        onlyFromNamed("bridge")
    {
60: function __CrossChainOwned_init(
        address _owner,
        address _addressManager,
        uint64 _ownerChainId
    )
        internal
        virtual
        onlyInitializing
    {
```
[36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L36) | [60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L60)

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

163: function withdraw(
        address _token,
        address _to
    )
        external
        onlyFromOwnerOrNamed("withdrawer")
        nonReentrant
        whenNotPaused
    {
```
[163](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L163)

```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

25: function setConfigAndExcess(
        Config memory _newConfig,
        uint64 _newGasExcess
    )
        external
        virtual
        onlyOwner
    {
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L25)

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

56: function authorize(address _addr, bool _authorize) external onlyOwner {
```
[56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L56)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

82: function suspendMessages(
        bytes32[] calldata _msgHashes,
        bool _suspend
    )
        external
        onlyFromOwnerOrNamed("bridge_watchdog")
    {
101: function banAddress(
        address _addr,
        bool _ban
    )
        external
        onlyFromOwnerOrNamed("bridge_watchdog")
        nonReentrant
    {
461: function _authorizePause(address)
        internal
        view
        virtual
        override
        onlyFromOwnerOrNamed("bridge_pauser")
    { }
```
[82](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L82) | [101](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L101) | [461](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L461)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

80: function setSnapshoter(address _snapshooter) external onlyOwner {
85: function snapshot() external onlyOwnerOrSnapshooter {
```
[80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L80) | [85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L85)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

36: function changeMigrationStatus(
        address _migratingAddress,
        bool _migratingInbound
    )
        external
        nonReentrant
        whenNotPaused
        onlyFromOwnerOrNamed("erc20_vault")
    {
```
[36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L36)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

54: function mint(
        address _account,
        uint256 _tokenId
    )
        public
        nonReentrant
        whenNotPaused
        onlyFromNamed("erc721_vault")
    {
69: function burn(
        address _account,
        uint256 _tokenId
    )
        public
        nonReentrant
        whenNotPaused
        onlyFromNamed("erc721_vault")
    {
```
[54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L54) | [69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L69)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

66: function mint(
        address _to,
        uint256 _tokenId,
        uint256 _amount
    )
        public
        nonReentrant
        whenNotPaused
        onlyFromNamed("erc1155_vault")
    {
83: function mintBatch(
        address _to,
        uint256[] memory _tokenIds,
        uint256[] memory _amounts
    )
        public
        nonReentrant
        whenNotPaused
        onlyFromNamed("erc1155_vault")
    {
100: function burn(
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
[66](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L66) | [83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L83) | [100](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L100)

```solidity
File: packages/protocol/contracts/tokenvault/BaseVault.sol

46: function checkProcessMessageContext()
        internal
        view
        onlyFromBridge
        returns (IBridge.Context memory ctx_)
    {
57: function checkRecallMessageContext()
        internal
        view
        onlyFromBridge
        returns (IBridge.Context memory ctx_)
    {
```
[46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L46) | [57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L57)

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

148: function changeBridgedToken(
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
[148](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L148)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

90: function addInstances(address[] calldata _instances)
        external
        onlyOwner
        returns (uint256[] memory)
    {
100: function deleteInstances(uint256[] calldata _ids)
        external
        onlyFromOwnerOrNamed("rollup_watchdog")
    {
139: function verifyProof(
        Context calldata _ctx,
        TaikoData.Transition calldata _tran,
        TaikoData.TierProof calldata _proof
    )
        external
        onlyFromNamed("taiko")
    {
```
[90](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L90) | [100](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L100) | [139](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L139)

```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

45: function setConfig(
        uint64 _claimStart,
        uint64 _claimEnd,
        bytes32 _merkleRoot
    )
        external
        onlyOwner
    {
55: function __MerkleClaimable_init(
        uint64 _claimStart,
        uint64 _claimEnd,
        bytes32 _merkleRoot
    )
        internal
        onlyInitializing
    {
```
[45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L45) | [55](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L55)

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

135: function grant(address _recipient, Grant memory _grant) external onlyOwner {
150: function void(address _recipient) external onlyOwner {
```
[135](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L135) | [150](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L150)

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

64: function setMrSigner(bytes32 _mrSigner, bool _trusted) external onlyOwner {
68: function setMrEnclave(bytes32 _mrEnclave, bool _trusted) external onlyOwner {
72: function addRevokedCertSerialNum(
        uint256 index,
        bytes[] calldata serialNumBatch
    )
        external
        onlyOwner
    {
87: function removeRevokedCertSerialNum(
        uint256 index,
        bytes[] calldata serialNumBatch
    )
        external
        onlyOwner
    {
102: function configureTcbInfoJson(
        string calldata fmspc,
        TCBInfoStruct.TCBInfo calldata tcbInfoInput
    )
        public
        onlyOwner
    {
113: function configureQeIdentityJson(EnclaveIdStruct.EnclaveId calldata qeIdentityInput)
        external
        onlyOwner
    {
121: function toggleLocalReportCheck() external onlyOwner {
```
[64](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L64) | [68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L68) | [72](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L72) | [87](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L87) | [102](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L102) | [113](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L113) | [121](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L121)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

61: function validateParsedInput(V3Struct.ParsedV3QuoteStruct memory v3Quote)
        internal
        pure
        returns (
            bool success,
            V3Struct.Header memory header,
            V3Struct.EnclaveReport memory localEnclaveReport,
            bytes memory signedQuoteData, // concatenation of header and local enclave report bytes
            V3Struct.ECDSAQuoteV3AuthData memory authDataV3
        )
    {
202: function parseAuthDataAndVerifyCertType(
        bytes memory rawAuthData,
        address pemCertLibAddr
    )
        private
        pure
        returns (bool success, V3Struct.ECDSAQuoteV3AuthData memory authDataV3)
    {
```
[61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L61) | [202](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L202)
</details>

### [G-80] Prefer `private` over `public` for Constants to Save Gas

Using `private` instead of `public` for constants can save gas.

The compiler doesn't need to create non-payable getter functions for deployment calldata, store the bytes of the value outside of where it's used, or add another entry to the method ID table, saving 3406-3606 gas in deployment.

If needed, the values can be read from the verified contract source code, or a single getter function that returns a tuple of the values of all currently public constants can be implemented.

<details>
<summary><i>23 issue instances in 11 files:</i></summary>

```solidity
File: packages/protocol/contracts/libs/Lib4844.sol

10: address public constant POINT_EVALUATION_PRECOMPILE_ADDRESS = address(0x0A);
13: uint32 public constant FIELD_ELEMENTS_PER_BLOB = 4096;
16: uint256 public constant BLS_MODULUS =
        52_435_875_175_126_190_479_447_740_508_185_965_837_690_552_500_527_637_822_603_658_699_938_581_184_513;
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L10) | [13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L13) | [16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L16)

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

38: uint256 public constant MAX_GAS_PAYING_PROVER = 50_000;
```
[38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L38)

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

21: uint256 public constant MAX_BYTES_PER_BLOB = 4096 * 32;
```
[21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L21)

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

20: bytes32 public constant RETURN_LIVENESS_BOND = keccak256("RETURN_LIVENESS_BOND");
23: bytes32 public constant TIER_OP = bytes32("tier_optimistic");
```
[20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L20) | [23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L23)

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

11: uint256 public constant MIN_NUM_GUARDIANS = 5;
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L11)

```solidity
File: packages/protocol/contracts/L1/tiers/ITierProvider.sol

39: uint16 public constant TIER_OPTIMISTIC = 100;
42: uint16 public constant TIER_SGX = 200;
45: uint16 public constant TIER_SGX_ZKVM = 300;
48: uint16 public constant TIER_GUARDIAN = 1000;
```
[39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L39) | [42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L42) | [45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L45) | [48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L48)

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

32: address public constant GOLDEN_TOUCH_ADDRESS = 0x0000777735367b36bC9B61C50022d9D0700dB4Ec;
35: uint8 public constant BLOCK_SYNC_THRESHOLD = 5;
```
[32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L32) | [35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L35)

```solidity
File: packages/protocol/contracts/signal/LibSignals.sol

8: bytes32 public constant STATE_ROOT = keccak256("STATE_ROOT");
11: bytes32 public constant SIGNAL_ROOT = keccak256("SIGNAL_ROOT");
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/LibSignals.sol#L8) | [11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/LibSignals.sol#L11)

```solidity
File: packages/protocol/contracts/tokenvault/BaseNFTVault.sol

47: bytes4 public constant ERC1155_INTERFACE_ID = 0xd9b67a26;
50: bytes4 public constant ERC721_INTERFACE_ID = 0x80ac58cd;
53: uint256 public constant MAX_TOKEN_PER_TXN = 10;
```
[47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L47) | [50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L50) | [53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L53)

```solidity
File: packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol

7: uint128 public constant MAX_EXP_INPUT = 135_305_999_368_893_231_588;
8: uint256 public constant SCALING_FACTOR = 1e18; // For fixed point representation factor
```
[7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L7) | [8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L8)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

30: uint64 public constant INSTANCE_EXPIRY = 180 days;
34: uint64 public constant INSTANCE_VALIDITY_DELAY = 1 days;
```
[30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L30) | [34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L34)
</details>

### [G-81] `<x> += <y>` costs more gas than `<x> = <x> + <y>` for state variables

Using the addition operator instead of plus-equals saves gas.
Replace `<x> += <y>` or `<x> -= <y>` with `<x> = <x> + <y>` or `<x> = <x> - <y>`.

<details>
<summary><i>4 issue instances in 1 files:</i></summary>

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

141: totalAmountGranted += _grant.amount;
156: totalAmountVoided += amountVoided;
216: totalAmountWithdrawn += amountToWithdraw;
217: totalCostPaid += costToWithdraw;
```
[141](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L141) | [156](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L156) | [216](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L216) | [217](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L217)
</details>

### [G-82] Using `bool`s for storage incurs overhead

Utilizing booleans for storage is less gas-efficient compared to using types that consume a full word like uint256.
Every write operation on a boolean necessitates an extra SLOAD operation to read the slot's current value, modify the boolean bits, and then write back.
This additional step is the compiler's measure against contract upgrades and pointer aliasing.

To enhance gas efficiency, consider using `uint256(0)` for false and `uint256(1)` for true, bypassing the extra Gwarmaccess (100 gas) incurred by the SLOAD.

<details>
<summary><i>10 issue instances in 7 files:</i></summary>

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

21: mapping(address addr => bool authorized) public isAuthorized;
```
[21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L21)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

42: mapping(address addr => bool banned) public addressBanned;
```
[42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L42)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

14: bool public migratingInbound;
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L14)

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

52: mapping(address btoken => bool blacklisted) public btokenBlacklist;
```
[52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L52)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

55: mapping(address instanceAddress => bool alreadyAttested) public addressRegistered;
```
[55](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L55)

```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

12: mapping(bytes32 hash => bool claimed) public isClaimed;
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L12)

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

38: bool private _checkLocalEnclaveReport;
39: mapping(bytes32 enclave => bool trusted) private _trustedUserMrEnclave;
40: mapping(bytes32 signer => bool trusted) private _trustedUserMrSigner;
47: mapping(uint256 idx => mapping(bytes serialNum => bool revoked)) private _serialNumIsRevoked;
```
[38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L38) | [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L39) | [40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L40) | [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L47)
</details>

### [G-83] Optimize Gas by Using Only Named Returns

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

<details>
<summary><i>162 issue instances in 53 files:</i></summary>

```solidity
File: packages/protocol/contracts/common/IAddressManager.sol

14: function getAddress(uint64 _chainId, bytes32 _name) external view returns (address);
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressManager.sol#L14)

```solidity
File: packages/protocol/contracts/common/AddressManager.sol

54: function getAddress(uint64 _chainId, bytes32 _name) public view override returns (address) {
```
[54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L54)

```solidity
File: packages/protocol/contracts/common/IAddressResolver.sol

19: function resolve(
        bytes32 _name,
        bool _allowZeroAddress
    )
        external
        view
        returns (address payable);
34: function resolve(
        uint64 _chainId,
        bytes32 _name,
        bool _allowZeroAddress
    )
        external
        view
        returns (address payable);
```
[19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressResolver.sol#L19) | [34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressResolver.sol#L34)

```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

30: function resolve(
        bytes32 _name,
        bool _allowZeroAddress
    )
        public
        view
        virtual
        returns (address payable)
    {
43: function resolve(
        uint64 _chainId,
        bytes32 _name,
        bool _allowZeroAddress
    )
        public
        view
        virtual
        returns (address payable)
    {
```
[30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L30) | [43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L43)

```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

88: function paused() public view returns (bool) {
139: function _inNonReentrant() internal view returns (bool) {
```
[88](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L88) | [139](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L139)

```solidity
File: packages/protocol/contracts/libs/LibAddress.sol

60: function isValidSignature(
        address _addr,
        bytes32 _hash,
        bytes memory _sig
    )
        internal
        view
        returns (bool)
    {
76: function isSenderEOA() internal view returns (bool) {
```
[60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L60) | [76](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L76)

```solidity
File: packages/protocol/contracts/libs/LibMath.sol

12: function min(uint256 _a, uint256 _b) internal pure returns (uint256) {
20: function max(uint256 _a, uint256 _b) internal pure returns (uint256) {
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibMath.sol#L12) | [20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibMath.sol#L20)

```solidity
File: packages/protocol/contracts/L1/gov/TaikoGovernor.sol

48: function propose(
        address[] memory _targets,
        uint256[] memory _values,
        bytes[] memory _calldatas,
        string memory _description
    )
        public
        override(IGovernorUpgradeable, GovernorUpgradeable, GovernorCompatibilityBravoUpgradeable)
        returns (uint256)
    {
69: function propose(
        address[] memory _targets,
        uint256[] memory _values,
        string[] memory _signatures,
        bytes[] memory _calldatas,
        string memory _description
    )
        public
        virtual
        override(GovernorCompatibilityBravoUpgradeable)
        returns (uint256)
    {
89: function supportsInterface(bytes4 _interfaceId)
        public
        view
        override(GovernorUpgradeable, GovernorTimelockControlUpgradeable, IERC165Upgradeable)
        returns (bool)
    {
99: function state(uint256 _proposalId)
        public
        view
        override(IGovernorUpgradeable, GovernorUpgradeable, GovernorTimelockControlUpgradeable)
        returns (ProposalState)
    {
111: function votingDelay() public pure override returns (uint256) {
117: function votingPeriod() public pure override returns (uint256) {
123: function proposalThreshold() public pure override returns (uint256) {
139: function _cancel(
        address[] memory _targets,
        uint256[] memory _values,
        bytes[] memory _calldatas,
        bytes32 _descriptionHash
    )
        internal
        override(GovernorUpgradeable, GovernorTimelockControlUpgradeable)
        returns (uint256)
    {
152: function _executor()
        internal
        view
        override(GovernorUpgradeable, GovernorTimelockControlUpgradeable)
        returns (address)
    {
```
[48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L48) | [69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L69) | [89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L89) | [99](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L99) | [111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L111) | [117](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L117) | [123](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L123) | [139](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L139) | [152](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L152)

```solidity
File: packages/protocol/contracts/L1/gov/TaikoTimelockController.sol

24: function getMinDelay() public view override returns (uint256) {
```
[24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L24)

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

137: function hashAssignment(
        ProverAssignment memory _assignment,
        address _taikoL1Address,
        bytes32 _blobHash
    )
        public
        view
        returns (bytes32)
    {
163: function _getProverFee(
        TaikoData.TierFee[] memory _tierFees,
        uint16 _tierId
    )
        private
        pure
        returns (uint256)
    {
```
[137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L137) | [163](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L163)

```solidity
File: packages/protocol/contracts/L1/ITaikoL1.sol

35: function getConfig() external view returns (TaikoData.Config memory);
```
[35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/ITaikoL1.sol#L35)

```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

122: function canDepositEthToL2(
        TaikoData.State storage _state,
        TaikoData.Config memory _config,
        uint256 _amount
    )
        internal
        view
        returns (bool)
    {
149: function _encodeEthDeposit(address _addr, uint256 _amount) private pure returns (uint256) {
```
[122](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L122) | [149](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L149)

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

287: function isBlobReusable(
        TaikoData.State storage _state,
        TaikoData.Config memory _config,
        bytes32 _blobHash
    )
        internal
        view
        returns (bool)
    {
298: function _isProposerPermitted(
        TaikoData.SlotB memory _slotB,
        IAddressResolver _resolver
    )
        private
        view
        returns (bool)
    {
```
[287](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L287) | [298](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L298)

```solidity
File: packages/protocol/contracts/L1/libs/LibUtils.sol

23: function getTransition(
        TaikoData.State storage _state,
        TaikoData.Config memory _config,
        uint64 _blockId,
        bytes32 _parentHash
    )
        external
        view
        returns (TaikoData.TransitionState storage)
    {
```
[23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L23)

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

244: function _isConfigValid(TaikoData.Config memory _config) private view returns (bool) {
```
[244](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L244)

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

101: function isApproved(bytes32 _hash) public view returns (bool) {
107: function numGuardians() public view returns (uint256) {
127: function isApproved(uint256 _approvalBits) internal view returns (bool) {
```
[101](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L101) | [107](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L107) | [127](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L127)

```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

132: function canDepositEthToL2(uint256 _amount) public view returns (bool) {
137: function isBlobReusable(bytes32 _blobHash) public view returns (bool) {
162: function getTransition(
        uint64 _blockId,
        bytes32 _parentHash
    )
        public
        view
        returns (TaikoData.TransitionState memory)
    {
186: function getConfig() public view virtual override returns (TaikoData.Config memory) {
```
[132](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L132) | [137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L137) | [162](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L162) | [186](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L186)

```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

60: function transfer(address _to, uint256 _amount) public override returns (bool) {
70: function transferFrom(
        address _from,
        address _to,
        uint256 _amount
    )
        public
        override
        returns (bool)
    {
```
[60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L60) | [70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L70)

```solidity
File: packages/protocol/contracts/L1/tiers/ITierProvider.sol

22: function getTier(uint16 tierId) external view returns (Tier memory);
28: function getTierIds() external view returns (uint16[] memory);
33: function getMinTier(uint256 rand) external view returns (uint16);
```
[22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L22) | [28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L28) | [33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L33)

```solidity
File: packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol

20: function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {
54: function getMinTier(uint256) public pure override returns (uint16) {
```
[20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L20) | [54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L54)

```solidity
File: packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol

20: function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {
66: function getMinTier(uint256 _rand) public pure override returns (uint16) {
```
[20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L20) | [66](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L66)

```solidity
File: packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol

20: function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {
66: function getMinTier(uint256 _rand) public pure override returns (uint16) {
```
[20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L20) | [66](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L66)

```solidity
File: packages/protocol/contracts/L2/Lib1559Math.sol

16: function basefee(
        uint256 _gasExcess,
        uint256 _adjustmentFactor
    )
        internal
        pure
        returns (uint256)
    {
33: function _ethQty(
        uint256 _gasExcess,
        uint256 _adjustmentFactor
    )
        private
        pure
        returns (uint256)
    {
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L16) | [33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L33)

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

200: function getBlockHash(uint64 _blockId) public view returns (bytes32) {
219: function skipFeeCheck() public pure virtual returns (bool) {
```
[200](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L200) | [219](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L219)

```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

43: function getConfig() public view override returns (Config memory) {
```
[43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L43)

```solidity
File: packages/protocol/contracts/signal/ISignalService.sol

96: function isSignalSent(address _app, bytes32 _signal) external view returns (bool);
105: function isChainDataSynced(
        uint64 _chainId,
        bytes32 _kind,
        uint64 _blockId,
        bytes32 _chainData
    )
        external
        view
        returns (bool);
```
[96](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L96) | [105](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L105)

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

63: function sendSignal(bytes32 _signal) external returns (bytes32) {
68: function syncChainData(
        uint64 _chainId,
        bytes32 _kind,
        uint64 _blockId,
        bytes32 _chainData
    )
        external
        returns (bytes32)
    {
137: function isChainDataSynced(
        uint64 _chainId,
        bytes32 _kind,
        uint64 _blockId,
        bytes32 _chainData
    )
        public
        view
        nonZeroValue(_chainData)
        returns (bool)
    {
153: function isSignalSent(address _app, bytes32 _signal) public view returns (bool) {
177: function signalForChainData(
        uint64 _chainId,
        bytes32 _kind,
        uint64 _blockId
    )
        public
        pure
        returns (bytes32)
    {
194: function getSignalSlot(
        uint64 _chainId,
        address _app,
        bytes32 _signal
    )
        public
        pure
        returns (bytes32)
    {
205: function _verifyHopProof(
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
[63](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L63) | [68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L68) | [137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L137) | [153](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L153) | [177](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L177) | [194](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L194) | [205](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L205)

```solidity
File: packages/protocol/contracts/bridge/IBridge.sol

150: function isMessageSent(Message calldata _message) external view returns (bool);
155: function hashMessage(Message memory _message) external pure returns (bytes32);
```
[150](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L150) | [155](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L155)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

340: function isMessageSent(Message calldata _message) public view returns (bool) {
352: function proveMessageFailed(
        Message calldata _message,
        bytes calldata _proof
    )
        public
        view
        returns (bool)
    {
374: function proveMessageReceived(
        Message calldata _message,
        bytes calldata _proof
    )
        public
        view
        returns (bool)
    {
449: function hashMessage(Message memory _message) public pure returns (bytes32) {
456: function signalForFailedMessage(bytes32 _msgHash) public pure returns (bytes32) {
555: function _loadContext() private view returns (Context memory) {
```
[340](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L340) | [352](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L352) | [374](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L374) | [449](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L449) | [456](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L456) | [555](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L555)

```solidity
File: packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

23: function transferFrom(address from, address _to, uint256 _amount) external returns (bool);
```
[23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L23)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

91: function name()
        public
        view
        override(ERC20Upgradeable, IERC20MetadataUpgradeable)
        returns (string memory)
    {
102: function symbol()
        public
        view
        override(ERC20Upgradeable, IERC20MetadataUpgradeable)
        returns (string memory)
    {
113: function decimals()
        public
        view
        override(ERC20Upgradeable, IERC20MetadataUpgradeable)
        returns (uint8)
    {
125: function canonical() public view returns (address, uint256) {
```
[91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L91) | [102](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L102) | [113](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L113) | [125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L125)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

93: function owner() public view override(IBridgedERC20, OwnableUpgradeable) returns (address) {
100: function _isMigratingOut() internal view returns (bool) {
```
[93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L93) | [100](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L100)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

87: function name() public view override(ERC721Upgradeable) returns (string memory) {
93: function symbol() public view override(ERC721Upgradeable) returns (string memory) {
100: function source() public view returns (address, uint256) {
107: function tokenURI(uint256 _tokenId) public view virtual override returns (string memory) {
```
[87](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L87) | [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L93) | [100](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L100) | [107](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L107)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

115: function name() public view returns (string memory) {
121: function symbol() public view returns (string memory) {
```
[115](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L115) | [121](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L121)

```solidity
File: packages/protocol/contracts/tokenvault/BaseVault.sol

39: function supportsInterface(bytes4 _interfaceId) public view virtual override returns (bool) {
45: function name() public pure virtual returns (bytes32);
```
[39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L39) | [45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L45)

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

18: function name() external view returns (string memory);
21: function symbol() external view returns (string memory);
160: function onERC1155BatchReceived(
        address,
        address,
        uint256[] calldata,
        uint256[] calldata,
        bytes calldata
    )
        external
        pure
        returns (bytes4)
    {
175: function onERC1155Received(
        address,
        address,
        uint256,
        uint256,
        bytes calldata
    )
        external
        pure
        returns (bytes4)
    {
192: function supportsInterface(bytes4 interfaceId)
        public
        view
        virtual
        override(BaseVault, ERC1155ReceiverUpgradeable)
        returns (bool)
    {
204: function name() public pure override returns (bytes32) {
```
[18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L18) | [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L21) | [160](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L160) | [175](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L175) | [192](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L192) | [204](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L204)

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

316: function name() public pure override returns (bytes32) {
```
[316](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L316)

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

142: function onERC721Received(
        address,
        address,
        uint256,
        bytes calldata
    )
        external
        pure
        returns (bytes4)
    {
156: function name() public pure override returns (bytes32) {
```
[142](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L142) | [156](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L156)

```solidity
File: packages/protocol/contracts/tokenvault/IBridgedERC20.sol

28: function owner() external view returns (address);
```
[28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/IBridgedERC20.sol#L28)

```solidity
File: packages/protocol/contracts/tokenvault/LibBridgedToken.sol

27: function buildName(
        string memory _name,
        uint256 _srcChainId
    )
        internal
        pure
        returns (string memory)
    {
38: function buildSymbol(string memory _symbol) internal pure returns (string memory) {
42: function buildURI(
        address _srcToken,
        uint256 _srcChainId
    )
        internal
        pure
        returns (string memory)
    {
```
[27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L27) | [38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L38) | [42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L42)

```solidity
File: packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol

25: function excessivelySafeCall(
        address _target,
        uint256 _gas,
        uint256 _value,
        uint16 _maxCopy,
        bytes memory _calldata
    )
        internal
        returns (bool, bytes memory)
    {
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L25)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/Bytes.sol

15: function slice(
        bytes memory _bytes,
        uint256 _start,
        uint256 _length
    )
        internal
        pure
        returns (bytes memory)
    {
91: function slice(bytes memory _bytes, uint256 _start) internal pure returns (bytes memory) {
102: function toNibbles(bytes memory _bytes) internal pure returns (bytes memory) {
149: function equal(bytes memory _bytes, bytes memory _other) internal pure returns (bool) {
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L15) | [91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L91) | [102](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L102) | [149](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L149)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

90: function addInstances(address[] calldata _instances)
        external
        onlyOwner
        returns (uint256[] memory)
    {
118: function registerInstance(V3Struct.ParsedV3QuoteStruct calldata _attestation)
        external
        returns (uint256)
    {
171: function getSignedHash(
        TaikoData.Transition memory _tran,
        address _newInstance,
        address _prover,
        bytes32 _metaHash
    )
        public
        view
        returns (bytes32)
    {
232: function _isInstanceValid(uint256 id, address instance) private view returns (bool) {
```
[90](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L90) | [118](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L118) | [171](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L171) | [232](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L232)

```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

76: function _verifyMerkleProof(
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
[76](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L76)

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

204: function getMyGrant(address _recipient) public view returns (Grant memory) {
234: function _getAmountOwned(Grant memory _grant) private view returns (uint128) {
238: function _getAmountUnlocked(Grant memory _grant) private view returns (uint128) {
244: function _calcAmount(
        uint128 _amount,
        uint64 _start,
        uint64 _cliff,
        uint64 _period
    )
        private
        view
        returns (uint128)
    {
```
[204](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L204) | [234](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L234) | [238](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L238) | [244](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L244)

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

137: function verifyAttestation(bytes calldata data) external view override returns (bool) {
162: function _verify(bytes calldata quote) private view returns (bool, bytes memory) {
174: function _verifyQEReportWithIdentity(V3Struct.EnclaveReport memory quoteEnclaveReport)
        private
        view
        returns (bool, EnclaveIdStruct.EnclaveIdStatus status)
    {
205: function _checkTcbLevels(
        IPEMCertChainLib.PCKCertificateField memory pck,
        TCBInfoStruct.TCBInfo memory tcb
    )
        private
        pure
        returns (bool, TCBInfoStruct.TCBStatus status)
    {
228: function _isCpuSvnHigherOrGreater(
        uint256[] memory pckCpuSvns,
        uint8[] memory tcbCpuSvns
    )
        private
        pure
        returns (bool)
    {
247: function _verifyCertChain(IPEMCertChainLib.ECSha256Certificate[] memory certs)
        private
        view
        returns (bool)
    {
302: function _enclaveReportSigVerification(
        bytes memory pckCertPubKey,
        bytes memory signedQuoteData,
        V3Struct.ECDSAQuoteV3AuthData memory authDataV3,
        V3Struct.EnclaveReport memory qeEnclaveReport
    )
        private
        view
        returns (bool)
    {
355: function verifyParsedQuote(V3Struct.ParsedV3QuoteStruct calldata v3quote)
        external
        view
        override
        returns (bool, bytes memory)
    {
363: function _verifyParsedQuote(V3Struct.ParsedV3QuoteStruct memory v3quote)
        internal
        view
        returns (bool, bytes memory)
    {
```
[137](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L137) | [162](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L162) | [174](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L174) | [205](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L205) | [228](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L228) | [247](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L247) | [302](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L302) | [355](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L355) | [363](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L363)

```solidity
File: packages/protocol/contracts/automata-attestation/interfaces/IAttestation.sol

9: function verifyAttestation(bytes calldata data) external returns (bool);
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/interfaces/IAttestation.sol#L9)

```solidity
File: packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol

37: function verifyAttStmtSignature(
        bytes memory tbs,
        bytes memory signature,
        PublicKey memory publicKey,
        Algorithm alg
    )
        external
        view
        returns (bool);
47: function verifyCertificateSignature(
        bytes memory tbs,
        bytes memory signature,
        PublicKey memory publicKey,
        CertSigAlgorithm alg
    )
        external
        view
        returns (bool);
```
[37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L37) | [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol#L47)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

14: function ixs(uint256 self) internal pure returns (uint256) {
18: function ixf(uint256 self) internal pure returns (uint256) {
23: function ixl(uint256 self) internal pure returns (uint256) {
28: function getPtr(uint256 _ixs, uint256 _ixf, uint256 _ixl) internal pure returns (uint256) {
47: function root(bytes memory der) internal pure returns (uint256) {
56: function rootOfBitStringAt(bytes memory der, uint256 ptr) internal pure returns (uint256) {
66: function rootOfOctetStringAt(bytes memory der, uint256 ptr) internal pure returns (uint256) {
77: function nextSiblingOf(bytes memory der, uint256 ptr) internal pure returns (uint256) {
87: function firstChildOf(bytes memory der, uint256 ptr) internal pure returns (uint256) {
98: function isChildOf(uint256 i, uint256 j) internal pure returns (bool) {
111: function bytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes memory) {
121: function allBytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes memory) {
131: function bytes32At(bytes memory der, uint256 ptr) internal pure returns (bytes32) {
141: function uintAt(bytes memory der, uint256 ptr) internal pure returns (uint256) {
154: function uintBytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes memory) {
164: function keccakOfBytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes32) {
168: function keccakOfAllBytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes32) {
179: function bitstringAt(bytes memory der, uint256 ptr) internal pure returns (bytes memory) {
186: function _readNodeLength(bytes memory der, uint256 ix) private pure returns (uint256) {
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L14) | [18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L18) | [23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L23) | [28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L28) | [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L47) | [56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L56) | [66](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L66) | [77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L77) | [87](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L87) | [98](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L98) | [111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L111) | [121](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L121) | [131](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L131) | [141](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L141) | [154](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L154) | [164](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L164) | [168](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L168) | [179](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L179) | [186](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L186)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

39: function compare(bytes memory self, bytes memory other) internal pure returns (int256) {
56: function compare(
        bytes memory self,
        uint256 offset,
        uint256 len,
        bytes memory other,
        uint256 otheroffset,
        uint256 otherlen
    )
        internal
        pure
        returns (int256)
    {
116: function equals(
        bytes memory self,
        uint256 offset,
        bytes memory other,
        uint256 otherOffset,
        uint256 len
    )
        internal
        pure
        returns (bool)
    {
138: function equals(
        bytes memory self,
        uint256 offset,
        bytes memory other,
        uint256 otherOffset
    )
        internal
        pure
        returns (bool)
    {
160: function equals(
        bytes memory self,
        uint256 offset,
        bytes memory other
    )
        internal
        pure
        returns (bool)
    {
178: function equals(bytes memory self, bytes memory other) internal pure returns (bool) {
284: function substring(
        bytes memory self,
        uint256 offset,
        uint256 len
    )
        internal
        pure
        returns (bytes memory)
    {
320: function base32HexDecodeWord(
        bytes memory self,
        uint256 off,
        uint256 len
    )
        internal
        pure
        returns (bytes32)
    {
370: function compareBytes(bytes memory a, bytes memory b) internal pure returns (bool) {
```
[39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L39) | [56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L56) | [116](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L116) | [138](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L138) | [160](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L160) | [178](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L178) | [284](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L284) | [320](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L320) | [370](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L370)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

43: function pkcs1Sha256(
        bytes32 _sha256,
        bytes memory _s,
        bytes memory _e,
        bytes memory _m
    )
        internal
        view
        returns (bool)
    {
191: function pkcs1Sha256Raw(
        bytes memory _data,
        bytes memory _s,
        bytes memory _e,
        bytes memory _m
    )
        internal
        view
        returns (bool)
    {
212: function pkcs1Sha1(
        bytes20 _sha1,
        bytes memory _s,
        bytes memory _e,
        bytes memory _m
    )
        internal
        view
        returns (bool)
    {
307: function pkcs1Sha1Raw(
        bytes memory _data,
        bytes memory _s,
        bytes memory _e,
        bytes memory _m
    )
        internal
        view
        returns (bool)
    {
```
[43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L43) | [191](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L191) | [212](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L212) | [307](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L307)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

23: function verifyAttStmtSignature(
        bytes memory tbs,
        bytes memory signature,
        PublicKey memory publicKey,
        Algorithm alg
    )
        public
        view
        returns (bool)
    {
53: function verifyCertificateSignature(
        bytes memory tbs,
        bytes memory signature,
        PublicKey memory publicKey,
        CertSigAlgorithm alg
    )
        public
        view
        returns (bool)
    {
```
[23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L23) | [53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L53)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

8: function toTimestamp(bytes memory x509Time) internal pure returns (uint256) {
33: function toUnixTimestamp(
        uint16 year,
        uint8 month,
        uint8 day,
        uint8 hour,
        uint8 minute,
        uint8 second
    )
        internal
        pure
        returns (uint256)
    {
70: function isLeapYear(uint16 year) internal pure returns (bool) {
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L8) | [33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L33) | [70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L70)
</details>

### [G-84] Cache State Variable Reads Outside Loops

Accessing state variables directly within loops can lead to increased gas costs due to the higher expense of state reads.
To optimize for gas efficiency, consider caching state variable values in local variables before the loop.
This practice reduces the number of costly state reads, particularly beneficial when loops execute multiple iterations
Refactor your contract to move state variable reads outside of loops wherever possible, enhancing performance and cost-effectiveness.

<details>
<summary><i>7 issue instances in 3 files:</i></summary>

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

/// @audit access state variable `minGuardians` access inside loop
135: if (count == minGuardians) return true;
```
[135](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L135)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

/// @audit access state variable `nextInstanceId` access inside loop
217: instances[nextInstanceId] = Instance(_instances[i], validSince);
/// @audit access state variable `nextInstanceId` access inside loop
218: ids[i] = nextInstanceId;
/// @audit access state variable `nextInstanceId` access inside loop
220: emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);
/// @audit access state variable `nextInstanceId` access inside loop
222: nextInstanceId++;
```
[217](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L217) | [218](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L218) | [220](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220) | [222](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L222)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

/// @audit access state variable `token` access inside loop
60: IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);
/// @audit access state variable `vault` access inside loop
60: IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);
```
[60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L60) | [60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L60)
</details>

### [G-85] Usage of `uints`/`ints` smaller than 32 bytes (256 bits) incurs overhead

Usage of uints/ints smaller than 32 bytes (256 bits) incurs overhead. The Ethereum Virtual Machine (EVM) operates on 32 bytes at a time. Therefore, if an element is smaller than 32 bytes, the EVM must use more operations to reduce the size of the element from 32 bytes to the desired size. 

Operations involving smaller size uints/ints cost extra gas due to the compiler having to clear the higher bits of the memory word before operating on the small size integer. This also includes the associated stack operations of doing so. 

It's recommended to use larger sizes and downcast where needed to optimize for gas efficiency.

<details>
<summary><i>237 issue instances in 47 files:</i></summary>

```solidity
File: packages/protocol/contracts/common/IAddressManager.sol

14: function getAddress(uint64 _chainId, bytes32 _name) external view returns (address);
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressManager.sol#L14)

```solidity
File: packages/protocol/contracts/common/AddressManager.sol

22: uint64 indexed chainId, bytes32 indexed name, address newAddress, address oldAddress
    );
39: uint64 _chainId,
        bytes32 _name,
        address _newAddress
    )
        external
        virtual
        onlyOwner
    {
54: function getAddress(uint64 _chainId, bytes32 _name) public view override returns (address) {
```
[22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L22) | [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L39) | [54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L54)

```solidity
File: packages/protocol/contracts/common/IAddressResolver.sol

35: uint64 _chainId,
        bytes32 _name,
        bool _allowZeroAddress
    )
        external
        view
        returns (address payable);
```
[35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/IAddressResolver.sol#L35)

```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

19: error RESOLVER_ZERO_ADDR(uint64 chainId, bytes32 name);
39: return _resolve(uint64(block.chainid), _name, _allowZeroAddress);
44: uint64 _chainId,
        bytes32 _name,
        bool _allowZeroAddress
    )
        public
        view
        virtual
        returns (address payable)
    {
59: if (block.chainid > type(uint64).max) {
73: uint64 _chainId,
        bytes32 _name,
        bool _allowZeroAddress
    )
        private
        view
        returns (address payable addr_)
    {
```
[19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L19) | [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L39) | [44](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L44) | [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L59) | [73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L73)

```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

11: uint8 private constant _FALSE = 1;
13: uint8 private constant _TRUE = 2;
21: uint8 private __reentry;
23: uint8 private __paused;
119: function _storeReentryLock(uint8 _reentry) internal virtual {
130: function _loadReentryLock() internal view virtual returns (uint8 reentry_) {
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L11) | [13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L13) | [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L21) | [23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L23) | [119](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L119) | [130](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L130)

```solidity
File: packages/protocol/contracts/libs/Lib4844.sol

13: uint32 public constant FIELD_ELEMENTS_PER_BLOB = 4096;
```
[13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L13)

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

166: uint16 _tierId
    )
        private
        pure
        returns (uint256)
    {
```
[166](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L166)

```solidity
File: packages/protocol/contracts/L1/ITaikoL1.sol

27: function proveBlock(uint64 _blockId, bytes calldata _input) external;
31: function verifyBlocks(uint64 _maxBlocksToVerify) external;
```
[27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/ITaikoL1.sol#L27) | [31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/ITaikoL1.sol#L31)

```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

53: amount: uint96(msg.value),
                id: _state.slotA.numEthDeposits
            })
        );
83: uint96 fee = uint96(_config.ethDepositMaxFee.min(block.basefee * _config.ethDepositGas));
84: uint64 j = _state.slotA.nextEthDepositToProcess;
85: uint96 totalFee;
89: recipient: address(uint160(data >> 96)),
                    amount: uint96(data),
                    id: j
                });
93: uint96 _fee = deposits_[i].amount > fee ? fee : deposits_[i].amount;
150: if (_amount > type(uint96).max) revert L1_INVALID_ETH_DEPOSIT();
```
[53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L53) | [83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L83) | [84](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L84) | [85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L85) | [89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L89) | [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L93) | [150](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L150)

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

130: timestamp: uint64(block.timestamp),
                l1Height: uint64(block.number - 1),
                txListByteOffset: 0, // to be initialized below
                txListByteSize: 0, // to be initialized below
                minTier: 0, // to be initialized below
                blobUsed: _txList.length == 0,
                parentMetaHash: parentMetaHash
            });
191: meta_.txListByteSize = uint24(_txList.length);
220: proposedIn: uint64(block.number),
            // For a new block, the next transition ID is always 1, not 0.
            nextTransitionId: 1,
            // For unverified block, its verifiedTransitionId is always 0.
            verifiedTransitionId: 0,
            assignedProver: params.assignedProver
        });
245: if (uint160(prevHook) >= uint160(params.hookCalls[i].hook)) {
```
[130](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L130) | [191](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L191) | [220](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L220) | [245](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L245)

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

78: _state.slotB.lastUnpausedAt = uint64(block.timestamp);
100: returns (uint8 maxBlocksToVerify_)
    {
115: uint64 slot = _meta.id % _config.blockRingBufferSize;
129: (uint32 tid, TaikoData.TransitionState storage ts) =
            _createTransition(_state, blk, _tran, slot);
264: ts.timestamp = uint64(block.timestamp);
273: uint64 slot
    )
        private
        returns (uint32 tid_, TaikoData.TransitionState storage ts_)
    {
405: uint32 _tid,
        ITierProvider.Tier memory _tier
    )
        private
        view
    {
```
[78](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L78) | [100](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L100) | [115](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L115) | [129](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L129) | [264](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L264) | [273](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L273) | [405](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L405)

```solidity
File: packages/protocol/contracts/L1/libs/LibUtils.sol

26: uint64 _blockId,
        bytes32 _parentHash
    )
        external
        view
        returns (TaikoData.TransitionState storage)
    {
38: uint64 slot = _blockId % _config.blockRingBufferSize;
42: uint32 tid = getTransitionId(_state, blk, slot, _parentHash);
55: uint64 _blockId
    )
        external
        view
        returns (TaikoData.Block storage blk_, uint64 slot_)
    {
73: uint64 _slot,
        bytes32 _parentHash
    )
        internal
        view
        returns (uint32 tid_)
    {
```
[26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L26) | [38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L38) | [42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L42) | [55](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L55) | [73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L73)

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

57: _state.slotA.genesisHeight = uint64(block.number);
58: _state.slotA.genesisTimestamp = uint64(block.timestamp);
64: blk.proposedAt = uint64(block.timestamp);
71: ts.timestamp = uint64(block.timestamp);
89: uint64 _maxBlocksToVerify
    )
        internal
    {
100: uint64 blockId = b.lastVerifiedBlockId;
102: uint64 slot = blockId % _config.blockRingBufferSize;
107: uint32 tid = blk.verifiedTransitionId;
117: uint64 numBlocksVerified;
213: uint64 lastVerifiedBlockId = b.lastVerifiedBlockId + numBlocksVerified;
227: uint64 _lastVerifiedBlockId,
        bytes32 _stateRoot
    )
        private
    {
234: (uint64 lastSyncedBlock,) = signalService.getSyncedChainData(
            _config.chainId, LibSignals.STATE_ROOT, 0 /* latest block Id*/
        );
260: || _config.ethDepositMaxAmount > type(uint96).max || _config.ethDepositGas == 0
                || _config.ethDepositMaxFee == 0
                || _config.ethDepositMaxFee > type(uint96).max / _config.ethDepositMaxCountPerBlock
        ) return false;
```
[57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L57) | [58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L58) | [64](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L64) | [71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L71) | [89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L89) | [100](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L100) | [102](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L102) | [107](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L107) | [117](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L117) | [213](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L213) | [227](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L227) | [234](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L234) | [260](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L260)

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

19: mapping(uint32 version => mapping(bytes32 hash => uint256 approvalBits)) internal _approvals;
27: uint32 public version;
30: uint32 public minGuardians;
37: event GuardiansUpdated(uint32 version, address[] guardians);
55: uint8 _minGuardians
    )
        external
        onlyOwner
        nonReentrant
    {
```
[19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L19) | [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L27) | [30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L30) | [37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L37) | [55](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L55)

```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

76: uint64 _blockId,
        bytes calldata _input
    )
        external
        nonReentrant
        whenNotPaused
        whenProvingNotPaused
    {
94: uint8 maxBlocksToVerify = LibProving.proveBlock(state, config, this, meta, tran, proof);
100: function verifyBlocks(uint64 _maxBlocksToVerify)
        external
        nonReentrant
        whenNotPaused
        whenProvingNotPaused
    {
126: state.slotB.lastUnpausedAt = uint64(block.timestamp);
145: function getBlock(uint64 _blockId)
        public
        view
        returns (TaikoData.Block memory blk_, TaikoData.TransitionState memory ts_)
    {
150: uint64 slot;
163: uint64 _blockId,
        bytes32 _parentHash
    )
        public
        view
        returns (TaikoData.TransitionState memory)
    {
```
[76](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L76) | [94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L94) | [100](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L100) | [126](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L126) | [145](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L145) | [150](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L150) | [163](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L163)

```solidity
File: packages/protocol/contracts/L1/tiers/ITierProvider.sol

22: function getTier(uint16 tierId) external view returns (Tier memory);
28: function getTierIds() external view returns (uint16[] memory);
39: uint16 public constant TIER_OPTIMISTIC = 100;
42: uint16 public constant TIER_SGX = 200;
45: uint16 public constant TIER_SGX_ZKVM = 300;
48: uint16 public constant TIER_GUARDIAN = 1000;
```
[22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L22) | [28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L28) | [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L39) | [42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L42) | [45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L45) | [48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L48)

```solidity
File: packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol

20: function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {
47: function getTierIds() public pure override returns (uint16[] memory tiers_) {
48: tiers_ = new uint16[](2);
```
[20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L20) | [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L47) | [48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L48)

```solidity
File: packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol

20: function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {
58: function getTierIds() public pure override returns (uint16[] memory tiers_) {
59: tiers_ = new uint16[](3);
```
[20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L20) | [58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L58) | [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L59)

```solidity
File: packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol

20: function getTier(uint16 _tierId) public pure override returns (ITierProvider.Tier memory) {
58: function getTierIds() public pure override returns (uint16[] memory tiers_) {
59: tiers_ = new uint16[](3);
```
[20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L20) | [58](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L58) | [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L59)

```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

16: uint64 public ownerChainId;
19: uint64 public nextTxId;
26: event TransactionExecuted(uint64 indexed txId, bytes4 indexed selector);
42: (uint64 txId, bytes memory txdata) = abi.decode(_data, (uint64, bytes));
63: uint64 _ownerChainId
    )
        internal
        virtual
        onlyInitializing
    {
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L16) | [19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L19) | [26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L26) | [42](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L42) | [63](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L63)

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

35: uint8 public constant BLOCK_SYNC_THRESHOLD = 5;
47: uint64 public gasExcess;
50: uint64 public lastSyncedBlock;
57: event Anchored(bytes32 parentHash, uint64 gasExcess);
74: uint64 _l1ChainId,
        uint64 _gasExcess
    )
        external
        initializer
    {
82: if (block.chainid <= 1 || block.chainid > type(uint64).max) {
110: uint64 _l1BlockId,
        uint32 _parentGasUsed
    )
        external
        nonReentrant
    {
186: uint64 _l1BlockId,
        uint32 _parentGasUsed
    )
        public
        view
        returns (uint256 basefee_)
    {
200: function getBlockHash(uint64 _blockId) public view returns (bytes32) {
254: uint64 _l1BlockId,
        uint32 _parentGasUsed
    )
        private
        view
        returns (uint256 basefee_, uint64 gasExcess_)
    {
284: gasExcess_ = uint64(excess.min(type(uint64).max));
```
[35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L35) | [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L47) | [50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L50) | [57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L57) | [74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L74) | [82](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L82) | [110](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L110) | [186](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L186) | [200](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L200) | [254](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L254) | [284](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L284)

```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

18: event ConfigAndExcessChanged(Config config, uint64 gasExcess);
27: uint64 _newGasExcess
    )
        external
        virtual
        onlyOwner
    {
```
[18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L18) | [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L27)

```solidity
File: packages/protocol/contracts/signal/ISignalService.sol

37: uint64 indexed chainId,
        uint64 indexed blockId,
        bytes32 indexed kind,
        bytes32 data,
        bytes32 signal
    );
69: uint64 _chainId,
        bytes32 _kind,
        uint64 _blockId,
        bytes32 _chainData
    )
        external
        returns (bytes32 signal_);
85: uint64 _chainId,
        address _app,
        bytes32 _signal,
        bytes calldata _proof
    )
        external;
106: uint64 _chainId,
        bytes32 _kind,
        uint64 _blockId,
        bytes32 _chainData
    )
        external
        view
        returns (bool);
123: uint64 _chainId,
        bytes32 _kind,
        uint64 _blockId
    )
        external
        view
        returns (uint64 blockId_, bytes32 chainData_);
138: uint64 _chainId,
        bytes32 _kind,
        uint64 _blockId
    )
        external
        pure
        returns (bytes32 signal_);
```
[37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L37) | [69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L69) | [85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L85) | [106](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L106) | [123](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L123) | [138](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L138)

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

17: mapping(uint64 chainId => mapping(bytes32 kind => uint64 blockId)) public topBlockId;
69: uint64 _chainId,
        bytes32 _kind,
        uint64 _blockId,
        bytes32 _chainData
    )
        external
        returns (bytes32)
    {
84: uint64 _chainId,
        address _app,
        bytes32 _signal,
        bytes calldata _proof
    )
        public
        virtual
        validSender(_app)
        nonZeroValue(_signal)
    {
97: uint64 chainId = _chainId;
138: uint64 _chainId,
        bytes32 _kind,
        uint64 _blockId,
        bytes32 _chainData
    )
        public
        view
        nonZeroValue(_chainData)
        returns (bool)
    {
159: uint64 _chainId,
        bytes32 _kind,
        uint64 _blockId
    )
        public
        view
        returns (uint64 blockId_, bytes32 chainData_)
    {
178: uint64 _chainId,
        bytes32 _kind,
        uint64 _blockId
    )
        public
        pure
        returns (bytes32)
    {
195: uint64 _chainId,
        address _app,
        bytes32 _signal
    )
        public
        pure
        returns (bytes32)
    {
207: uint64 _chainId,
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
236: uint64 _chainId,
        bytes32 _kind,
        uint64 _blockId,
        bytes32 _chainData
    )
        private
        returns (bytes32 signal_)
    {
264: slot_ = getSignalSlot(uint64(block.chainid), _app, _signal);
273: uint64 _chainId,
        uint64 _blockId,
        bytes32 _signalRoot,
        bool _isFullProof,
        bool _isLastHop
    )
        private
    {
308: bytes32 slot = getSignalSlot(uint64(block.chainid), _app, _signal);
```
[17](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L17) | [69](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L69) | [84](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L84) | [97](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L97) | [138](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L138) | [159](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L159) | [178](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L178) | [195](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L195) | [207](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L207) | [236](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L236) | [264](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L264) | [273](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L273) | [308](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L308)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

31: uint128 public nextMessageId;
64: modifier sameChain(uint64 _chainId) {
89: uint64 _timestamp = _suspend ? type(uint64).max : uint64(block.timestamp);
146: message_.srcChainId = uint64(block.chainid);
168: uint64 receivedAt = proofReceipt[msgHash].receivedAt;
183: receivedAt = uint64(block.timestamp);
230: uint64 receivedAt = proofReceipt[msgHash].receivedAt;
240: receivedAt = uint64(block.timestamp);
392: function isDestChainEnabled(uint64 _chainId)
        public
        view
        returns (bool enabled_, address destBridge_)
    {
531: _storeContext(bytes32(0), address(0), uint64(0));
533: _storeContext(bytes32(PLACEHOLDER), address(uint160(PLACEHOLDER)), uint64(PLACEHOLDER));
541: function _storeContext(bytes32 _msgHash, address _from, uint64 _srcChainId) private {
559: uint64 srcChainId;
580: uint64 _chainId,
        bytes calldata _proof
    )
        private
        view
        returns (bool success_)
    {
```
[31](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L31) | [64](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L64) | [89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L89) | [146](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L146) | [168](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L168) | [183](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L183) | [230](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L230) | [240](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L240) | [392](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L392) | [531](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L531) | [533](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L533) | [541](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L541) | [559](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L559) | [580](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L580)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

24: uint8 private __srcDecimals;
117: returns (uint8)
    {
```
[24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L24) | [117](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L117)

```solidity
File: packages/protocol/contracts/tokenvault/BaseNFTVault.sol

70: uint64 indexed chainId,
        address indexed ctoken,
        address indexed btoken,
        string ctokenSymbol,
        string ctokenName
    );
90: uint64 destChainId,
        address ctoken,
        address token,
        uint256[] tokenIds,
        uint256[] amounts
    );
126: uint64 srcChainId,
        address ctoken,
        address token,
        uint256[] tokenIds,
        uint256[] amounts
    );
```
[70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L70) | [90](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L90) | [126](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L126)

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

257: chainId: uint64(block.chainid),
                    addr: _op.token,
                    symbol: "",
                    name: ""
                });
```
[257](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L257)

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

102: uint64 destChainId,
        address ctoken,
        address token,
        uint256 amount
    );
130: uint64 srcChainId,
        address ctoken,
        address token,
        uint256 amount
    );
366: chainId: uint64(block.chainid),
                addr: _token,
                decimals: meta.decimals(),
                symbol: meta.symbol(),
                name: meta.name()
            });
```
[102](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L102) | [130](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L130) | [366](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L366)

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

204: chainId: uint64(block.chainid),
                    addr: _op.token,
                    symbol: t.symbol(),
                    name: t.name()
                });
```
[204](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L204)

```solidity
File: packages/protocol/contracts/tokenvault/LibBridgedToken.sol

56: Strings.toHexString(uint160(_srcToken), 20),
                "@",
                Strings.toString(_srcChainId),
                "/tokenURI?uint256="
            )
        );
```
[56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L56)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

14: if (_in.length == 1 && uint8(_in[0]) < 128) {
35: out_[0] = bytes1(uint8(_len) + uint8(_offset));
45: out_[0] = bytes1(uint8(lenLen) + uint8(_offset) + 55);
47: out_[i] = bytes1(uint8((_len / (256 ** (lenLen - i))) % 256));
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L14) | [35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L35) | [45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L45) | [47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L47)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

30: uint8 internal constant PREFIX_EXTENSION_EVEN = 0;
33: uint8 internal constant PREFIX_EXTENSION_ODD = 1;
36: uint8 internal constant PREFIX_LEAF_EVEN = 2;
39: uint8 internal constant PREFIX_LEAF_ODD = 3;
134: uint8 branchKey = uint8(key[currentKeyIndex]);
141: uint8 prefix = uint8(path[0]);
142: uint8 offset = 2 - (prefix % 2);
```
[30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L30) | [33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L33) | [36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L36) | [39](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L39) | [134](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L134) | [141](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L141) | [142](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L142)

```solidity
File: packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol

7: uint128 public constant MAX_EXP_INPUT = 135_305_999_368_893_231_588;
```
[7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L7)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

30: uint64 public constant INSTANCE_EXPIRY = 180 days;
34: uint64 public constant INSTANCE_VALIDITY_DELAY = 1 days;
154: uint32 id = uint32(bytes4(Bytes.slice(_proof.data, 0, 4)));
204: uint64 validSince = uint64(block.timestamp);
229: instances[id] = Instance(newInstance, uint64(block.timestamp));
```
[30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L30) | [34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L34) | [154](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L154) | [204](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L204) | [229](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L229)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

29: uint64 _claimStart,
        uint64 _claimEnd,
        bytes32 _merkleRoot,
        address _token,
        address _vault
    )
        external
        initializer
    {
```
[29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L29)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

28: uint64 public withdrawalWindow;
56: uint64 _claimStart,
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
[28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L28) | [56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L56)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

27: uint64 _claimStart,
        uint64 _claimEnd,
        bytes32 _merkleRoot,
        address _token,
        address _vault
    )
        external
        initializer
    {
```
[27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L27)

```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

18: uint64 public claimStart;
21: uint64 public claimEnd;
46: uint64 _claimStart,
        uint64 _claimEnd,
        bytes32 _merkleRoot
    )
        external
        onlyOwner
    {
57: uint64 _claimStart,
        uint64 _claimEnd,
        bytes32 _merkleRoot
    )
        internal
        onlyInitializing
    {
90: function _setConfig(uint64 _claimStart, uint64 _claimEnd, bytes32 _merkleRoot) private {
```
[18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L18) | [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L21) | [46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L46) | [57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L57) | [90](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L90)

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

68: uint128 public totalAmountGranted;
71: uint128 public totalAmountVoided;
74: uint128 public totalAmountWithdrawn;
77: uint128 public totalCostPaid;
82: uint128[44] private __gap;
92: event Voided(address indexed recipient, uint128 amount);
99: event Withdrawn(address indexed recipient, address to, uint128 amount, uint128 cost);
152: uint128 amountVoided = _voidGrant(r.grant);
180: uint128 amountOwned,
            uint128 amountUnlocked,
            uint128 amountWithdrawn,
            uint128 amountToWithdraw,
            uint128 costToWithdraw
        )
    {
211: (,,, uint128 amountToWithdraw, uint128 costToWithdraw) = getMyGrantSummary(_recipient);
225: function _voidGrant(Grant storage _grant) private returns (uint128 amountVoided) {
226: uint128 amountOwned = _getAmountOwned(_grant);
235: function _getAmountOwned(Grant memory _grant) private view returns (uint128) {
239: function _getAmountUnlocked(Grant memory _grant) private view returns (uint128) {
246: uint128 _amount,
        uint64 _start,
        uint64 _cliff,
        uint64 _period
    )
        private
        view
        returns (uint128)
    {
264: return _amount * uint64(block.timestamp - _start) / _period;
273: function _validateCliff(uint64 _start, uint64 _cliff, uint32 _period) private pure {
```
[68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L68) | [71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L71) | [74](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L74) | [77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L77) | [82](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L82) | [92](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L92) | [99](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L99) | [152](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L152) | [180](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L180) | [211](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L211) | [225](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L225) | [226](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L226) | [235](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L235) | [239](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L239) | [246](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L246) | [264](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L264) | [273](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L273)

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

36: uint8 internal constant INVALID_EXIT_CODE = 255;
```
[36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L36)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

358: uint16 svnValue = svnValueBytes.length < 2
                ? uint16(bytes2(svnValueBytes)) / 256
                : uint16(bytes2(svnValueBytes));
```
[358](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L358)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

106: uint32 totalQuoteSize = 48 // header
            + 384 // local QE report
            + 64 // ecdsa256BitSignature
            + 64 // ecdsaAttestationKey
            + 384 // QE report
            + 64 // qeReportSignature
            + 2 // sizeof(v3Quote.v3AuthData.qeAuthData.parsedDataSize)
            + v3Quote.v3AuthData.qeAuthData.parsedDataSize + 2 // sizeof(v3Quote.v3AuthData.certification.certType)
            + 4 // sizeof(v3Quote.v3AuthData.certification.certDataSize)
            + v3Quote.v3AuthData.certification.certDataSize;
146: enclaveReport.isvProdId = uint16(littleEndianDecode(rawEnclaveReport.substring(256, 2)));
147: enclaveReport.isvSvn = uint16(littleEndianDecode(rawEnclaveReport.substring(258, 2)));
212: qeAuthData.parsedDataSize = uint16(littleEndianDecode(rawAuthData.substring(576, 2)));
217: cert.certType = uint16(littleEndianDecode(rawAuthData.substring(offset, 2)));
222: cert.certDataSize = uint32(littleEndianDecode(rawAuthData.substring(offset, 4)));
249: uint16 isvProdIdPackBE = (enclaveReport.isvProdId >> 8) | (enclaveReport.isvProdId << 8);
250: uint16 isvSvnPackBE = (enclaveReport.isvSvn >> 8) | (enclaveReport.isvSvn << 8);
```
[106](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L106) | [146](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L146) | [147](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L147) | [212](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L212) | [217](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L217) | [222](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L222) | [249](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L249) | [250](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L250)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

15: return uint80(self);
20: return uint80(self >> 80);
25: return uint80(self >> 160);
189: uint80 ixFirstContentByte;
190: uint80 ixLastContentByte;
192: length = uint8(der[ix + 1]);
193: ixFirstContentByte = uint80(ix + 2);
194: ixLastContentByte = uint80(ixFirstContentByte + length - 1);
196: uint8 lengthbytesLength = uint8(der[ix + 1] & 0x7F);
206: ixFirstContentByte = uint80(ix + 2 + lengthbytesLength);
207: ixLastContentByte = uint80(ixFirstContentByte + length - 1);
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L15) | [20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L20) | [25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L25) | [189](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L189) | [190](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L190) | [192](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L192) | [193](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L193) | [194](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L194) | [196](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L196) | [206](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L206) | [207](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L207)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

189: return uint8(self[idx]);
332: uint8 decoded;
336: decoded = uint8(BASE32_HEX_TABLE[uint256(uint8(char)) - 0x30]);
```
[189](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L189) | [332](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L332) | [336](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L336)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

53: uint8[17] memory sha256ExplicitNullParam = [
            0x30,
            0x31,
            0x30,
            0x0d,
            0x06,
            0x09,
            0x60,
            0x86,
            0x48,
            0x01,
            0x65,
            0x03,
            0x04,
            0x02,
            0x01,
            0x05,
            0x00
        ];
73: uint8[15] memory sha256ImplicitNullParam = [
            0x30,
            0x2f,
            0x30,
            0x0b,
            0x06,
            0x09,
            0x60,
            0x86,
            0x48,
            0x01,
            0x65,
            0x03,
            0x04,
            0x02,
            0x01
        ];
125: if (uint8(decipher[decipherlen - 50]) == 0x31) {
128: } else if (uint8(decipher[decipherlen - 48]) == 0x2f) {
222: uint8[15] memory sha1Prefix = [
            0x30,
            0x21,
            0x30,
            0x09,
            0x06,
            0x05,
            0x2b,
            0x0e,
            0x03,
            0x02,
            0x1a,
            0x05,
            0x00,
            0x04,
            0x14
        ];
```
[53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L53) | [73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L73) | [125](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L125) | [128](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L128) | [222](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L222)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

9: uint16 yrs;
10: uint8 mnths;
11: uint8 dys;
12: uint8 hrs;
13: uint8 mins;
14: uint8 secs;
15: uint8 offset;
18: if (uint8(x509Time[0]) - 48 < 5) yrs += 2000;
21: yrs += (uint8(x509Time[0]) - 48) * 1000 + (uint8(x509Time[1]) - 48) * 100;
24: yrs += (uint8(x509Time[offset + 0]) - 48) * 10 + uint8(x509Time[offset + 1]) - 48;
25: mnths = (uint8(x509Time[offset + 2]) - 48) * 10 + uint8(x509Time[offset + 3]) - 48;
26: dys += (uint8(x509Time[offset + 4]) - 48) * 10 + uint8(x509Time[offset + 5]) - 48;
27: hrs += (uint8(x509Time[offset + 6]) - 48) * 10 + uint8(x509Time[offset + 7]) - 48;
28: mins += (uint8(x509Time[offset + 8]) - 48) * 10 + uint8(x509Time[offset + 9]) - 48;
29: secs += (uint8(x509Time[offset + 10]) - 48) * 10 + uint8(x509Time[offset + 11]) - 48;
35: uint16 year,
        uint8 month,
        uint8 day,
        uint8 hour,
        uint8 minute,
        uint8 second
    )
        internal
        pure
        returns (uint256)
    {
48: for (uint16 i = 1970; i < year; ++i) {
56: uint8[12] memory monthDays = [31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31];
59: for (uint8 i = 1; i < month; ++i) {
71: function isLeapYear(uint16 year) internal pure returns (bool) {
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L9) | [10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L10) | [11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L11) | [12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L12) | [13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L13) | [14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L14) | [15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L15) | [18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L18) | [21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L21) | [24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L24) | [25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L25) | [26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L26) | [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L27) | [28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L28) | [29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L29) | [35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L35) | [48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L48) | [56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L56) | [59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L59) | [71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L71)
</details>

### [G-86] Unlimited gas consumption risk due to external call recipients

When calling an external function without specifying a gas limit , the called contract may consume all the remaining gas, causing the tx to be reverted.
To mitigate this, it is recommended to explicitly set a gas limit when making low level external calls.

<details>
<summary><i>1 issue instances in 1 files:</i></summary>

```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

50: (bool success,) = address(this).call(txdata);
```
[50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L50)
</details>

### [G-87] Use assembly to check for `address(0)`

The usage of inline assembly to check if variable is the zero can save gas compared to traditional `require` or `if` statement checks. 

The assembly check uses the `extcodesize` operation which is generally cheaper in terms of gas.

[More information can be found here.](https://medium.com/@kalexotsu/solidity-assembly-checking-if-an-address-is-0-efficiently-d2bfe071331)

<details>
<summary><i>43 issue instances in 18 files:</i></summary>

```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

81: if (addressManager == address(0)) revert RESOLVER_INVALID_MANAGER();
85: if (!_allowZeroAddress && addr_ == address(0)) {
            revert RESOLVER_ZERO_ADDR(_chainId, _name);
```
[81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L81) | [85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L85)

```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

105: if (_addressManager == address(0)) revert ZERO_ADDR_MANAGER();
```
[105](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L105)

```solidity
File: packages/protocol/contracts/libs/LibAddress.sol

24: if (_to == address(0)) revert ETH_TRANSFER_FAILED();
```
[24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L24)

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

109: if (assignment.feeToken == address(0)) {
            // Paying Ether
            _blk.assignedProver.sendEther(proverFee, MAX_GAS_PAYING_PROVER);
120: if (input.tip != 0 && block.coinbase != address(0)) {
            address(block.coinbase).sendEther(input.tip);
```
[109](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L109) | [120](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L120)

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

81: if (params.assignedProver == address(0)) {
            revert L1_INVALID_PROVER();
85: if (params.coinbase == address(0)) {
310: if (proposerOne != address(0) && msg.sender != proposerOne) {
```
[81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L81) | [85](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L85) | [310](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L310)

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

163: if (verifier != address(0)) {
239: if (ts.contester != address(0)) revert L1_ALREADY_CONTESTED();
363: if (_ts.contester != address(0)) {
            if (_sameTransition) {
```
[163](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L163) | [239](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L239) | [363](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L363)

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

145: if (ts.contester != address(0)) {
148: if (tierProvider == address(0)) {
                        tierProvider = _resolver.resolve("tier_provider", false);
```
[145](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L145) | [148](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L148)

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

82: if (guardian == address(0)) revert INVALID_GUARDIAN();
```
[82](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L82)

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

172: if (_to == address(0)) revert L2_INVALID_PARAM();
173: if (_token == address(0)) {
            _to.sendEther(address(this).balance);
```
[172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L172) | [173](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L173)

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

36: if (_app == address(0)) revert SS_INVALID_SENDER();
```
[36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L36)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

124: if (_message.srcOwner == address(0) || _message.destOwner == address(0)) {
            revert B_INVALID_USER();
269: if (
                _message.to == address(0) || _message.to == address(this)
                    || _message.to == signalService || addressBanned[_message.to]
            ) {
```
[124](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L124) | [269](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L269)

```solidity
File: packages/protocol/contracts/tokenvault/BaseNFTVault.sol

149: if (_op.token == address(0)) revert VAULT_INVALID_TOKEN();
```
[149](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L149)

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

108: if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();
249: if (bridgedToCanonical[_op.token].addr != address(0)) {
293: if (btoken_ == address(0)) {
            btoken_ = _deployBridgedToken(_ctoken);
```
[108](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L108) | [249](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L249) | [293](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L293)

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

158: if (_btokenNew == address(0) || bridgedToCanonical[_btokenNew].addr != address(0)) {
            revert VAULT_INVALID_NEW_BTOKEN();
170: if (btokenOld_ != address(0)) {
215: if (_op.token == address(0)) revert VAULT_INVALID_TOKEN();
267: if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();
358: if (bridgedToCanonical[_token].addr != address(0)) {
397: if (btoken == address(0)) {
            btoken = _deployBridgedToken(ctoken);
```
[158](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L158) | [170](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L170) | [215](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L215) | [267](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L267) | [358](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L358) | [397](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L397)

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

91: if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();
195: if (bridgedToCanonical[_op.token].addr != address(0)) {
230: if (btoken_ == address(0)) {
            btoken_ = _deployBridgedToken(_ctoken);
```
[91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L91) | [195](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L195) | [230](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L230)

```solidity
File: packages/protocol/contracts/tokenvault/LibBridgedToken.sol

20: if (
            _srcToken == address(0) || _srcChainId == 0 || _srcChainId == block.chainid
                || bytes(_symbol).length == 0 || bytes(_name).length == 0
        ) {
            revert BTOKEN_INVALID_PARAMS();
```
[20](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L20)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

107: if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();
124: if (automataDcapAttestation == address(0)) {
            revert SGX_RA_NOT_SUPPORTED();
215: if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();
234: if (instance == address(0)) return false;
```
[107](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L107) | [124](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L124) | [215](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L215) | [234](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L234)

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

121: if (_taikoToken == address(0)) revert INVALID_PARAM();
124: if (_costToken == address(0)) revert INVALID_PARAM();
127: if (_sharedVault == address(0)) revert INVALID_PARAM();
136: if (_recipient == address(0)) revert INVALID_PARAM();
169: if (_to == address(0)) revert INVALID_PARAM();
```
[121](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L121) | [124](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L124) | [127](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L127) | [136](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L136) | [169](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L169)
</details>

### [G-88] `internal`/`private` functions only called once can be inlined to save gas

`internal` functions that are only called once should be inlined to save gas. 
Not inlining such functions costs an extra 20 to 40 gas due to the additional `JUMP` instructions and stack operations required for function calls.

<details>
<summary><i>69 issue instances in 32 files:</i></summary>

```solidity
File: packages/protocol/contracts/libs/LibAddress.sol

/// @audit function `supportsInterface()` called only once
46: function supportsInterface(
        address _addr,
        bytes4 _interfaceId
    )
        internal
        view
        returns (bool result_)
    {
/// @audit function `isValidSignature()` called only once
61: function isValidSignature(
        address _addr,
        bytes32 _hash,
        bytes memory _sig
    )
        internal
        view
        returns (bool)
    {
```
[46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L46) | [61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L61)

```solidity
File: packages/protocol/contracts/L1/gov/TaikoGovernor.sol

/// @audit function `_execute()` called only once
127: function _execute(
        uint256 _proposalId,
        address[] memory _targets,
        uint256[] memory _values,
        bytes[] memory _calldatas,
        bytes32 _descriptionHash
    )
        internal
        override(GovernorUpgradeable, GovernorTimelockControlUpgradeable)
    {
/// @audit function `_cancel()` called only once
140: function _cancel(
        address[] memory _targets,
        uint256[] memory _values,
        bytes[] memory _calldatas,
        bytes32 _descriptionHash
    )
        internal
        override(GovernorUpgradeable, GovernorTimelockControlUpgradeable)
        returns (uint256)
    {
/// @audit function `_executor()` called only once
153: function _executor()
        internal
        view
        override(GovernorUpgradeable, GovernorTimelockControlUpgradeable)
        returns (address)
    {
```
[127](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L127) | [140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L140) | [153](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L153)

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

/// @audit function `_getProverFee()` called only once
164: function _getProverFee(
        TaikoData.TierFee[] memory _tierFees,
        uint16 _tierId
    )
        private
        pure
        returns (uint256)
    {
```
[164](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L164)

```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

/// @audit function `canDepositEthToL2()` called only once
122: function canDepositEthToL2(
        TaikoData.State storage _state,
        TaikoData.Config memory _config,
        uint256 _amount
    )
        internal
        view
        returns (bool)
    {
```
[122](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L122)

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

/// @audit function `isBlobReusable()` called only once
287: function isBlobReusable(
        TaikoData.State storage _state,
        TaikoData.Config memory _config,
        bytes32 _blobHash
    )
        internal
        view
        returns (bool)
    {
/// @audit function `_isProposerPermitted()` called only once
299: function _isProposerPermitted(
        TaikoData.SlotB memory _slotB,
        IAddressResolver _resolver
    )
        private
        view
        returns (bool)
    {
```
[287](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L287) | [299](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L299)

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

/// @audit function `_createTransition()` called only once
269: function _createTransition(
        TaikoData.State storage _state,
        TaikoData.Block storage _blk,
        TaikoData.Transition memory _tran,
        uint64 slot
    )
        private
        returns (uint32 tid_, TaikoData.TransitionState storage ts_)
    {
/// @audit function `_overrideWithHigherProof()` called only once
350: function _overrideWithHigherProof(
        TaikoData.TransitionState storage _ts,
        TaikoData.Transition memory _tran,
        TaikoData.TierProof memory _proof,
        ITierProvider.Tier memory _tier,
        IERC20 _tko,
        bool _sameTransition
    )
        private
    {
/// @audit function `_checkProverPermission()` called only once
401: function _checkProverPermission(
        TaikoData.State storage _state,
        TaikoData.Block storage _blk,
        TaikoData.TransitionState storage _ts,
        uint32 _tid,
        ITierProvider.Tier memory _tier
    )
        private
        view
    {
```
[269](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L269) | [350](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L350) | [401](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L401)

```solidity
File: packages/protocol/contracts/L1/libs/LibUtils.sol

/// @audit function `getTransitionId()` called only once
70: function getTransitionId(
        TaikoData.State storage _state,
        TaikoData.Block storage _blk,
        uint64 _slot,
        bytes32 _parentHash
    )
        internal
        view
        returns (uint32 tid_)
    {
```
[70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L70)

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

/// @audit function `_syncChainData()` called only once
224: function _syncChainData(
        TaikoData.Config memory _config,
        IAddressResolver _resolver,
        uint64 _lastVerifiedBlockId,
        bytes32 _stateRoot
    )
        private
    {
/// @audit function `_isConfigValid()` called only once
245: function _isConfigValid(TaikoData.Config memory _config) private view returns (bool) {
```
[224](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L224) | [245](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L245)

```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

/// @audit function `_authorizePause()` called only once
220: function _authorizePause(address)
        internal
        view
        virtual
        override
        onlyFromOwnerOrNamed("chain_pauser")
    { }
```
[220](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L220)

```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

/// @audit function `_beforeTokenTransfer()` called only once
83: function _beforeTokenTransfer(
        address _from,
        address _to,
        uint256 _amount
    )
        internal
        override(ERC20Upgradeable, ERC20SnapshotUpgradeable)
    {
/// @audit function `_afterTokenTransfer()` called only once
94: function _afterTokenTransfer(
        address _from,
        address _to,
        uint256 _amount
    )
        internal
        override(ERC20Upgradeable, ERC20VotesUpgradeable)
    {
```
[83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L83) | [94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L94)

```solidity
File: packages/protocol/contracts/L2/Lib1559Math.sol

/// @audit function `_ethQty()` called only once
33: function _ethQty(
        uint256 _gasExcess,
        uint256 _adjustmentFactor
    )
        private
        pure
        returns (uint256)
    {
```
[33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L33)

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

/// @audit function `_verifyHopProof()` called only once
206: function _verifyHopProof(
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
/// @audit function `_cacheChainData()` called only once
271: function _cacheChainData(
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
[206](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L206) | [271](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L271)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

/// @audit function `_loadContext()` called only once
555: function _loadContext() private view returns (Context memory) {
```
[555](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L555)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

/// @audit function `_beforeTokenTransfer()` called only once
139: function _beforeTokenTransfer(
        address _from,
        address _to,
        uint256 _amount
    )
        internal
        override(ERC20Upgradeable, ERC20SnapshotUpgradeable)
    {
/// @audit function `_afterTokenTransfer()` called only once
152: function _afterTokenTransfer(
        address _from,
        address _to,
        uint256 _amount
    )
        internal
        override(ERC20Upgradeable, ERC20VotesUpgradeable)
    {
```
[139](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L139) | [152](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L152)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

/// @audit function `_mintToken()` called only once
97: function _mintToken(address _account, uint256 _amount) internal virtual;

    function _burnToken(address _from, uint256 _amount) internal virtual;

    function _isMigratingOut() internal view returns (bool) {
```
[97](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L97)

```solidity
File: packages/protocol/contracts/tokenvault/BaseVault.sol

/// @audit function `name()` called only once
45: function name() public pure virtual returns (bytes32);

    function checkProcessMessageContext()
        internal
        view
        onlyFromBridge
        returns (IBridge.Context memory ctx_)
    {
```
[45](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L45)

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

/// @audit function `_handleMessage()` called only once
240: function _handleMessage(
        address _user,
        BridgeTransferOp memory _op
    )
        private
        returns (bytes memory msgData_, CanonicalNFT memory ctoken_)
    {
/// @audit function `_getOrDeployBridgedToken()` called only once
288: function _getOrDeployBridgedToken(CanonicalNFT memory _ctoken)
        private
        returns (address btoken_)
    {
/// @audit function `_deployBridgedToken()` called only once
303: function _deployBridgedToken(CanonicalNFT memory _ctoken) private returns (address btoken_) {
```
[240](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L240) | [288](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L288) | [303](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L303)

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

/// @audit function `_handleMessage()` called only once
348: function _handleMessage(
        address _user,
        address _token,
        address _to,
        uint256 _amount
    )
        private
        returns (bytes memory msgData_, CanonicalERC20 memory ctoken_, uint256 balanceChange_)
    {
/// @audit function `_getOrDeployBridgedToken()` called only once
391: function _getOrDeployBridgedToken(CanonicalERC20 memory ctoken)
        private
        returns (address btoken)
    {
/// @audit function `_deployBridgedToken()` called only once
407: function _deployBridgedToken(CanonicalERC20 memory ctoken) private returns (address btoken) {
```
[348](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L348) | [391](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L391) | [407](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L407)

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

/// @audit function `_handleMessage()` called only once
187: function _handleMessage(
        address _user,
        BridgeTransferOp memory _op
    )
        private
        returns (bytes memory msgData_, CanonicalNFT memory ctoken_)
    {
/// @audit function `_getOrDeployBridgedToken()` called only once
224: function _getOrDeployBridgedToken(CanonicalNFT memory _ctoken)
        private
        returns (address btoken_)
    {
/// @audit function `_deployBridgedToken()` called only once
240: function _deployBridgedToken(CanonicalNFT memory _ctoken) private returns (address btoken_) {
```
[187](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L187) | [224](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L224) | [240](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L240)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

/// @audit function `writeBytes()` called only once
13: function writeBytes(bytes memory _in) internal pure returns (bytes memory out_) {
/// @audit function `_writeLength()` called only once
32: function _writeLength(uint256 _len, uint256 _offset) private pure returns (bytes memory out_) {
/// @audit function `_toBinary()` called only once
55: function _toBinary(uint256 _x) private pure returns (bytes memory out_) {
```
[13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L13) | [32](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L32) | [55](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L55)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

/// @audit function `get()` called only once
68: function get(
        bytes memory _key,
        bytes[] memory _proof,
        bytes32 _root
    )
        internal
        pure
        returns (bytes memory value_)
    {
/// @audit function `_parseProof()` called only once
205: function _parseProof(bytes[] memory _proof) private pure returns (TrieNode[] memory proof_) {
/// @audit function `_getNodePath()` called only once
227: function _getNodePath(TrieNode memory _node) private pure returns (bytes memory nibbles_) {
/// @audit function `_getSharedNibbleLength()` called only once
235: function _getSharedNibbleLength(
        bytes memory _a,
        bytes memory _b
    )
        private
        pure
        returns (uint256 shared_)
    {
```
[68](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L68) | [205](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L205) | [227](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L227) | [235](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L235)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol

/// @audit function `verifyInclusionProof()` called only once
19: function verifyInclusionProof(
        bytes memory _key,
        bytes memory _value,
        bytes[] memory _proof,
        bytes32 _root
    )
        internal
        pure
        returns (bool valid_)
    {
/// @audit function `get()` called only once
38: function get(
        bytes memory _key,
        bytes[] memory _proof,
        bytes32 _root
    )
        internal
        pure
        returns (bytes memory value_)
    {
```
[19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L19) | [38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L38)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

/// @audit function `_replaceInstance()` called only once
226: function _replaceInstance(uint256 id, address oldInstance, address newInstance) private {
/// @audit function `_isInstanceValid()` called only once
233: function _isInstanceValid(uint256 id, address instance) private view returns (bool) {
```
[226](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L226) | [233](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L233)

```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

/// @audit function `_verifyMerkleProof()` called only once
77: function _verifyMerkleProof(
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
[77](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L77)

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

/// @audit function `_voidGrant()` called only once
225: function _voidGrant(Grant storage _grant) private returns (uint128 amountVoided) {
/// @audit function `_getAmountUnlocked()` called only once
239: function _getAmountUnlocked(Grant memory _grant) private view returns (uint128) {
/// @audit function `_validateGrant()` called only once
267: function _validateGrant(Grant memory _grant) private pure {
```
[225](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L225) | [239](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L239) | [267](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L267)

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

/// @audit function `_attestationTcbIsValid()` called only once
126: function _attestationTcbIsValid(TCBInfoStruct.TCBStatus status)
        internal
        pure
        virtual
        returns (bool valid)
    {
/// @audit function `_verify()` called only once
162: function _verify(bytes calldata quote) private view returns (bool, bytes memory) {
/// @audit function `_verifyQEReportWithIdentity()` called only once
175: function _verifyQEReportWithIdentity(V3Struct.EnclaveReport memory quoteEnclaveReport)
        private
        view
        returns (bool, EnclaveIdStruct.EnclaveIdStatus status)
    {
/// @audit function `_checkTcbLevels()` called only once
206: function _checkTcbLevels(
        IPEMCertChainLib.PCKCertificateField memory pck,
        TCBInfoStruct.TCBInfo memory tcb
    )
        private
        pure
        returns (bool, TCBInfoStruct.TCBStatus status)
    {
/// @audit function `_isCpuSvnHigherOrGreater()` called only once
229: function _isCpuSvnHigherOrGreater(
        uint256[] memory pckCpuSvns,
        uint8[] memory tcbCpuSvns
    )
        private
        pure
        returns (bool)
    {
/// @audit function `_verifyCertChain()` called only once
248: function _verifyCertChain(IPEMCertChainLib.ECSha256Certificate[] memory certs)
        private
        view
        returns (bool)
    {
/// @audit function `_enclaveReportSigVerification()` called only once
303: function _enclaveReportSigVerification(
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
[126](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L126) | [162](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L162) | [175](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L175) | [206](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L206) | [229](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L229) | [248](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L248) | [303](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L303)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

/// @audit function `_removeHeadersAndFooters()` called only once
216: function _removeHeadersAndFooters(string memory pemData)
        private
        pure
        returns (bool success, bytes memory extracted, uint256 endIndex)
    {
/// @audit function `_findPckTcbInfo()` called only once
269: function _findPckTcbInfo(
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
/// @audit function `_findTcb()` called only once
341: function _findTcb(
        bytes memory der,
        uint256 oidPtr
    )
        private
        pure
        returns (bool success, uint256 pcesvn, uint256[] memory cpusvns)
    {
```
[216](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L216) | [269](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L269) | [341](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L341)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

/// @audit function `parseAndVerifyHeader()` called only once
165: function parseAndVerifyHeader(bytes memory rawHeader)
        private
        pure
        returns (bool success, V3Struct.Header memory header)
    {
/// @audit function `parseAuthDataAndVerifyCertType()` called only once
203: function parseAuthDataAndVerifyCertType(
        bytes memory rawAuthData,
        address pemCertLibAddr
    )
        private
        pure
        returns (bool success, V3Struct.ECDSAQuoteV3AuthData memory authDataV3)
    {
/// @audit function `packQEReport()` called only once
244: function packQEReport(V3Struct.EnclaveReport memory enclaveReport)
        internal
        pure
        returns (bytes memory packedQEReport)
    {
/// @audit function `parseCerificationChainBytes()` called only once
267: function parseCerificationChainBytes(
        bytes memory certBytes,
        address pemCertLibAddr
    )
        internal
        pure
        returns (bytes[3] memory certChainData)
    {
```
[165](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L165) | [203](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L203) | [244](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L244) | [267](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L267)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

/// @audit function `getPtr()` called only once
29: function getPtr(uint256 _ixs, uint256 _ixf, uint256 _ixl) internal pure returns (uint256) {
```
[29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L29)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

/// @audit function `memcpy()` called only once
272: function memcpy(uint256 dest, uint256 src, uint256 len) private pure {
```
[272](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L272)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

/// @audit function `pkcs1Sha256()` called only once
43: function pkcs1Sha256(
        bytes32 _sha256,
        bytes memory _s,
        bytes memory _e,
        bytes memory _m
    )
        internal
        view
        returns (bool)
    {
/// @audit function `pkcs1Sha1()` called only once
212: function pkcs1Sha1(
        bytes20 _sha1,
        bytes memory _s,
        bytes memory _e,
        bytes memory _m
    )
        internal
        view
        returns (bool)
    {
```
[43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L43) | [212](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L212)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

/// @audit function `toUnixTimestamp()` called only once
34: function toUnixTimestamp(
        uint16 year,
        uint8 month,
        uint8 day,
        uint8 hour,
        uint8 minute,
        uint8 second
    )
        internal
        pure
        returns (uint256)
    {
```
[34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L34)
</details>

### [G-89] Inefficient Use of String Constants

In Solidity, if data can fit into 32 bytes, it's more efficient to use the bytes32 datatype instead of bytes or strings.

This is because the bytes32 datatype is cheaper in terms of gas usage.

<details>
<summary><i>7 issue instances in 2 files:</i></summary>

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

22: string private __symbol;
25: string private __name;
```
[22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L22) | [25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L25)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

17: string internal constant HEADER = "-----BEGIN CERTIFICATE-----";
18: string internal constant FOOTER = "-----END CERTIFICATE-----";
22: string internal constant PCK_COMMON_NAME = "Intel SGX PCK Certificate";
23: string internal constant PLATFORM_ISSUER_NAME = "Intel SGX PCK Platform CA";
24: string internal constant PROCESSOR_ISSUER_NAME = "Intel SGX PCK Processor CA";
```
[17](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L17) | [18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L18) | [22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L22) | [23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L23) | [24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L24)
</details>

### [G-90] Consider using OZ EnumerateSet in place of nested mappings

Nested mappings and multi-dimensional arrays in Solidity operate through a process of double hashing, wherein the original storage slot and the first key are concatenated and hashed, and then this hash is again concatenated with the second key and hashed. This process can be quite gas expensive due to the double-hashing operation and subsequent storage operation (sstore).

A possible optimization involves manually concatenating the keys followed by a single hash operation and an sstore. However, this technique introduces the risk of storage collision, especially when there are other nested hash maps in the contract that use the same key types. Because Solidity is unaware of the number and structure of nested hash maps in a contract, it follows a conservative approach in computing the storage slot to avoid possible collisions.

OpenZeppelin's EnumerableSet provides a potential solution to this problem. It creates a data structure that combines the benefits of set operations with the ability to enumerate stored elements, which is not natively available in Solidity. EnumerableSet handles the element uniqueness internally and can therefore provide a more gas-efficient and collision-resistant alternative to nested mappings or multi-dimensional arrays in certain scenarios.

<details>
<summary><i>8 issue instances in 7 files:</i></summary>

```solidity
File: packages/protocol/contracts/common/AddressManager.sol

12: mapping(uint256 chainId => mapping(bytes32 name => address addr)) private __addresses;
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L12)

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

19: mapping(uint32 version => mapping(bytes32 hash => uint256 approvalBits)) internal _approvals;
```
[19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L19)

```solidity
File: packages/protocol/contracts/L1/TaikoData.sol

183: mapping(uint64 blockId => mapping(bytes32 parentHash => uint32 transitionId)) transitionIds;
185: mapping(
            uint64 blockId_mod_blockRingBufferSize
                => mapping(uint32 transitionId => TransitionState ts)
            ) transitions;
```
[183](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L183) | [185](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L185)

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

17: mapping(uint64 chainId => mapping(bytes32 kind => uint64 blockId)) public topBlockId;
```
[17](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L17)

```solidity
File: packages/protocol/contracts/tokenvault/BaseNFTVault.sol

59: mapping(uint256 chainId => mapping(address ctoken => address btoken)) public canonicalToBridged;
```
[59](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L59)

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

49: mapping(uint256 chainId => mapping(address ctoken => address btoken)) public canonicalToBridged;
```
[49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L49)

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

47: mapping(uint256 idx => mapping(bytes serialNum => bool revoked)) private _serialNumIsRevoked;
```
[47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L47)
</details>

### [G-91] Declare `immutable` as `private` to save gas

Using `private` instead of `public` for immutables saves gas.

The compiler doesn't need to create non-payable getter functions for deployment calldata, store the bytes of the value outside of where it's used, or add another entry to the method ID table, saving 3406-3606 gas in deployment.

<details>
<summary><i>2 issue instances in 1 files:</i></summary>

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

25: ISigVerifyLib public immutable sigVerifyLib;
26: IPEMCertChainLib public immutable pemCertLib;
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L25) | [26](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L26)
</details>

### [G-92] State variables should be cached in stack rather than re-reading them from storage

Caching state variables in local variables can optimize gas usage, as accessing the stack is cheaper than accessing storage.

The instances below point to the second+ access of a state variable within a function.

<details>
<summary><i>46 issue instances in 10 files:</i></summary>

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

/// @audit function setGuardians() uses state variable `version` 2 times
1: // SPDX-License-Identifier: MIT
95: emit GuardiansUpdated(version, _newGuardians);
/// @audit function approve() uses state variable `version` 2 times
116: _approvals[version][_hash] |= 1 << (id - 1);
119: uint256 _approval = _approvals[version][_hash];
```
[1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L1) | [95](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L95) | [116](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L116) | [119](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L119)

```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

/// @audit function proposeBlock() uses state variable `state` 2 times
67: (meta_, deposits_) = LibProposing.proposeBlock(state, config, this, _params, _txList);
70: LibVerifying.verifyBlocks(state, config, this, config.maxBlocksToVerifyPerProposal);
/// @audit function proveBlock() uses state variable `state` 2 times
94: uint8 maxBlocksToVerify = LibProving.proveBlock(state, config, this, meta, tran, proof);
96: LibVerifying.verifyBlocks(state, config, this, maxBlocksToVerify);
```
[67](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L67) | [70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L70) | [94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L94) | [96](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L96)

```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

/// @audit function onMessageInvocation() uses state variable `nextTxId` 2 times
43: if (txId != nextTxId) revert XCO_INVALID_TX_ID();
53: emit TransactionExecuted(nextTxId++, bytes4(txdata));
```
[43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L43) | [53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L53)

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

/// @audit function anchor() uses state variable `gasExcess` 2 times
140: (basefee, gasExcess) = _calc1559BaseFee(config, _l1BlockId, _parentGasUsed);
157: emit Anchored(blockhash(parentId), gasExcess);
/// @audit function _calc1559BaseFee() uses state variable `gasExcess` 2 times
262: if (gasExcess > 0) {
265: uint256 excess = uint256(gasExcess) + _parentGasUsed;
/// @audit function _calc1559BaseFee() uses state variable `lastSyncedBlock` 3 times
275: if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {
275: if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {
276: numL1Blocks = _l1BlockId - lastSyncedBlock;
```
[140](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L140) | [157](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L157) | [262](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L262) | [265](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L265) | [275](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L275) | [275](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L275) | [276](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L276)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

/// @audit function mint() uses state variable `migratingAddress` 2 times
61: if (msg.sender == migratingAddress) {
63: emit MigratedTo(migratingAddress, _account, _amount);
/// @audit function burn() uses state variable `migratingAddress` 2 times
63: emit MigratedTo(migratingAddress, _account, _amount);
82: IBridgedERC20(migratingAddress).mint(_account, _amount);
```
[61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L61) | [63](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L63) | [63](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L63) | [82](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L82)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

/// @audit function readList() uses state variable `uint256` 6 times
54: (uint256 listOffset, uint256 listLength, RLPItemType itemType) = _decodeLength(_in);
54: (uint256 listOffset, uint256 listLength, RLPItemType itemType) = _decodeLength(_in);
72: uint256 itemCount = 0;
73: uint256 offset = listOffset;
75: (uint256 itemOffset, uint256 itemLength,) = _decodeLength(
75: (uint256 itemOffset, uint256 itemLength,) = _decodeLength(
/// @audit function readBytes() uses state variable `uint256` 2 times
110: (uint256 itemOffset, uint256 itemLength, RLPItemType itemType) = _decodeLength(_in);
110: (uint256 itemOffset, uint256 itemLength, RLPItemType itemType) = _decodeLength(_in);
/// @audit function _decodeLength() uses state variable `uint256` 7 times
157: MemoryPointer ptr = _in.ptr;
1: // SPDX-License-Identifier: MIT
188: } else if (prefix <= 0xbf) {
204: "RLPReader: length of content must not have any leading zeros (long string)"
1: // SPDX-License-Identifier: MIT
234: } else {
250: "RLPReader: length of content must not have any leading zeros (long list)"
```
[54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L54) | [54](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L54) | [72](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L72) | [73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L73) | [75](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L75) | [75](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L75) | [110](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L110) | [110](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L110) | [157](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L157) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L1) | [188](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L188) | [204](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L204) | [1](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L1) | [234](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L234) | [250](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L250)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

/// @audit function _addInstances() uses state variable `nextInstanceId` 4 times
217: instances[nextInstanceId] = Instance(_instances[i], validSince);
218: ids[i] = nextInstanceId;
220: emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);
222: nextInstanceId++;
```
[217](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L217) | [218](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L218) | [220](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L220) | [222](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L222)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

/// @audit function claimAndDelegate() uses state variable `token` 2 times
63: IERC20(token).transferFrom(vault, user, amount);
71: IVotes(token).delegateBySig(delegatee, nonce, expiry, v, r, s);
```
[63](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L63) | [71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L71)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

/// @audit function getBalance() uses state variable `withdrawalWindow` 2 times
118: * (block.timestamp.min(claimEnd + withdrawalWindow) - claimEnd) / withdrawalWindow;
118: * (block.timestamp.min(claimEnd + withdrawalWindow) - claimEnd) / withdrawalWindow;
```
[118](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L118) | [118](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L118)

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

/// @audit function _withdraw() uses state variable `sharedVault` 2 times
219: IERC20(taikoToken).transferFrom(sharedVault, _to, amountToWithdraw);
220: IERC20(costToken).safeTransferFrom(_recipient, sharedVault, costToWithdraw);
```
[219](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L219) | [220](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L220)
</details>

### [G-93] Division by powers of two should use bit shifting

When dividing by powers of two (e.g., 2, 4, 8), it is more efficient to use bit shifting.

`<x> / 2` can be replaced with `<x> >> 1`, as both operations use the SHR opcode in the compiler.
However, the division approach incurs an additional 20 gas overhead due to jumps to and from a compiler utility function that introduces checks.

This overhead can be avoided by using `unchecked` around the division by powers of two.

<details>
<summary><i>2 issue instances in 2 files:</i></summary>

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

359: ? uint16(bytes2(svnValueBytes)) / 256
```
[359](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L359)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

155: uint256 upperDigit = digits / 16;
```
[155](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L155)
</details>

### [G-94] Optimize names to save gas

Function names for public and external methods, as well as public state variable names, can be optimized to achieve gas savings.
By renaming functions to generate method IDs with two leading zero bytes, you can save 128 gas during contract deployment.
Further, renaming functions for lower method IDs can conserve 22 gas per call for each sorted position shifted.

Optimizing function names for gas efficiency can result in significant savings, especially for frequently called functions or heavily deployed contracts. 
Reference: [Solidity Gas Optimizations - Function Name](https://blog.emn178.cc/en/post/solidity-gas-optimization-function-name/)

<details>
<summary><i>71 issue instances in 70 files:</i></summary>

```solidity
File: packages/protocol/contracts/common/AddressManager.sol

10: contract AddressManager is EssentialContract, IAddressManager {
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L10)

```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

11: abstract contract AddressResolver is IAddressResolver, Initializable {
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L11)

```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

10: abstract contract EssentialContract is UUPSUpgradeable, Ownable2StepUpgradeable, AddressResolver {
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L10)

```solidity
File: packages/protocol/contracts/libs/Lib4844.sol

8: library Lib4844 {
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L8)

```solidity
File: packages/protocol/contracts/libs/LibAddress.sol

13: library LibAddress {
```
[13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L13)

```solidity
File: packages/protocol/contracts/libs/LibMath.sol

7: library LibMath {
```
[7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibMath.sol#L7)

```solidity
File: packages/protocol/contracts/libs/LibTrieProof.sol

15: library LibTrieProof {
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L15)

```solidity
File: packages/protocol/contracts/L1/gov/TaikoGovernor.sol

16: contract TaikoGovernor is
    EssentialContract,
    GovernorCompatibilityBravoUpgradeable,
    GovernorVotesUpgradeable,
    GovernorVotesQuorumFractionUpgradeable,
    GovernorTimelockControlUpgradeable
{
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L16)

```solidity
File: packages/protocol/contracts/L1/gov/TaikoTimelockController.sol

9: contract TaikoTimelockController is EssentialContract, TimelockControllerUpgradeable {
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L9)

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

14: contract AssignmentHook is EssentialContract, IHook {
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L14)

```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

12: library LibDepositing {
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L12)

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

15: library LibProposing {
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L15)

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

16: library LibProving {
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L16)

```solidity
File: packages/protocol/contracts/L1/libs/LibUtils.sol

9: library LibUtils {
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibUtils.sol#L9)

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

16: library LibVerifying {
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L16)

```solidity
File: packages/protocol/contracts/L1/provers/GuardianProver.sol

10: contract GuardianProver is Guardians {
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L10)

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

9: abstract contract Guardians is EssentialContract {
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L9)

```solidity
File: packages/protocol/contracts/L1/TaikoData.sol

8: library TaikoData {
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L8)

```solidity
File: packages/protocol/contracts/L1/TaikoErrors.sol

11: abstract contract TaikoErrors {
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoErrors.sol#L11)

```solidity
File: packages/protocol/contracts/L1/TaikoEvents.sol

13: abstract contract TaikoEvents {
```
[13](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoEvents.sol#L13)

```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

22: contract TaikoL1 is EssentialContract, ITaikoL1, TaikoEvents, TaikoErrors {
```
[22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L22)

```solidity
File: packages/protocol/contracts/L1/TaikoToken.sol

15: contract TaikoToken is EssentialContract, ERC20SnapshotUpgradeable, ERC20VotesUpgradeable {
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L15)

```solidity
File: packages/protocol/contracts/L1/tiers/ITierProvider.sol

37: library LibTiers {
```
[37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/ITierProvider.sol#L37)

```solidity
File: packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol

10: contract DevnetTierProvider is EssentialContract, ITierProvider {
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol#L10)

```solidity
File: packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol

10: contract MainnetTierProvider is EssentialContract, ITierProvider {
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol#L10)

```solidity
File: packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol

10: contract TestnetTierProvider is EssentialContract, ITierProvider {
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol#L10)

```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

14: abstract contract CrossChainOwned is EssentialContract, IMessageInvocable {
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L14)

```solidity
File: packages/protocol/contracts/L2/Lib1559Math.sol

10: library Lib1559Math {
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L10)

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

21: contract TaikoL2 is CrossChainOwned {
```
[21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L21)

```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

9: contract TaikoL2EIP1559Configurable is TaikoL2 {
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L9)

```solidity
File: packages/protocol/contracts/signal/LibSignals.sol

6: library LibSignals {
```
[6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/LibSignals.sol#L6)

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

14: contract SignalService is EssentialContract, ISignalService {
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L14)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

16: contract Bridge is EssentialContract, IBridge {
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L16)

```solidity
File: packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

28: contract USDCAdapter is BridgedERC20Base {
```
[28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L28)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

15: contract BridgedERC20 is
    BridgedERC20Base,
    IERC20MetadataUpgradeable,
    ERC20SnapshotUpgradeable,
    ERC20VotesUpgradeable
{
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L15)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

9: abstract contract BridgedERC20Base is EssentialContract, IBridgedERC20 {
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L9)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

12: contract BridgedERC721 is EssentialContract, ERC721Upgradeable {
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L12)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

14: contract BridgedERC1155 is EssentialContract, IERC1155MetadataURIUpgradeable, ERC1155Upgradeable {
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L14)

```solidity
File: packages/protocol/contracts/tokenvault/BaseNFTVault.sol

9: abstract contract BaseNFTVault is BaseVault {
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L9)

```solidity
File: packages/protocol/contracts/tokenvault/BaseVault.sol

12: abstract contract BaseVault is
    EssentialContract,
    IRecallableSender,
    IMessageInvocable,
    IERC165Upgradeable
{
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L12)

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

29: contract ERC1155Vault is BaseNFTVault, ERC1155ReceiverUpgradeable {
```
[29](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L29)

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

18: contract ERC20Vault is BaseVault {
```
[18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L18)

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

16: contract ERC721Vault is BaseNFTVault, IERC721Receiver {
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L16)

```solidity
File: packages/protocol/contracts/tokenvault/LibBridgedToken.sol

8: library LibBridgedToken {
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L8)

```solidity
File: packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol

4: library ExcessivelySafeCall {
```
[4](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L4)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/Bytes.sol

6: library Bytes {
```
[6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L6)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

9: library RLPReader {
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L9)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

9: library RLPWriter {
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L9)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

11: library MerkleTrie {
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L11)

```solidity
File: packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol

9: library SecureMerkleTrie {
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol#L9)

```solidity
File: packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol

5: library LibFixedPointMath {
```
[5](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L5)

```solidity
File: packages/protocol/contracts/verifiers/GuardianVerifier.sol

10: contract GuardianVerifier is EssentialContract, IVerifier {
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/GuardianVerifier.sol#L10)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

19: contract SgxVerifier is EssentialContract, IVerifier {
```
[19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L19)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

11: contract ERC20Airdrop is MerkleClaimable {
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L11)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

12: contract ERC20Airdrop2 is MerkleClaimable {
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L12)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

9: contract ERC721Airdrop is MerkleClaimable {
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L9)

```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

10: abstract contract MerkleClaimable is EssentialContract {
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L10)

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

25: contract TimelockTokenPool is EssentialContract {
```
[25](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L25)

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

22: contract AutomataDcapV3Attestation is IAttestation {
```
[22](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L22)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/EnclaveIdStruct.sol

6: library EnclaveIdStruct {
```
[6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/EnclaveIdStruct.sol#L6)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

12: contract PEMCertChainLib is IPEMCertChainLib {
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L12)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

11: library V3Parser {
```
[11](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L11)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol

6: library V3Struct {
```
[6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L6)

```solidity
File: packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol

6: library TCBInfoStruct {
```
[6](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol#L6)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

12: library NodePtr {
38: library Asn1Decode {
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L12) | [38](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L38)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

8: library BytesUtils {
```
[8](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L8)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol

34: library RsaVerify {
```
[34](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol#L34)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/SHA1.sol

10: library SHA1 {
```
[10](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SHA1.sol#L10)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

15: contract SigVerifyLib is ISigVerifyLib {
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L15)

```solidity
File: packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol

7: library X509DateUtils {
```
[7](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol#L7)
</details>

### [G-95] Avoid updating storage when the value hasn't changed

A check regarding whether the current value and the new value are the same should be added.
This helps prevent unnecessary state changes and events in case the new value is the same as the current value.

<details>
<summary><i>13 issue instances in 7 files:</i></summary>

```solidity
File: packages/protocol/contracts/common/AddressManager.sol

/// @audit Missing `_newAddress` check before state change
49: __addresses[_chainId][_name] = _newAddress;
```
[49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L49)

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

/// @audit Missing `_minGuardians` check before state change
93: minGuardians = _minGuardians;
```
[93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L93)

```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

/// @audit Missing `_newConfig` check before state change
35: customConfig = _newConfig;
/// @audit Missing `_newGasExcess` check before state change
37: gasExcess = _newGasExcess;
```
[35](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L35) | [37](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L37)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

/// @audit Missing `_snapshooter` check before state change
81: snapshooter = _snapshooter;
```
[81](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L81)

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

/// @audit Missing `_ctoken` check before state change
187: bridgedToCanonical[_btokenNew] = _ctoken;
/// @audit Missing `_btokenNew` check before state change
184: IBridgedERC20(btokenOld_).changeMigrationStatus(_btokenNew, false);
```
[187](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L187) | [184](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L184)

```solidity
File: packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

/// @audit Missing `_merkleRoot` check before state change
53: _setConfig(_claimStart, _claimEnd, _merkleRoot);
/// @audit Missing `_claimStart` check before state change
91: claimStart = _claimStart;
/// @audit Missing `_claimEnd` check before state change
92: claimEnd = _claimEnd;
/// @audit Missing `_merkleRoot` check before state change
93: merkleRoot = _merkleRoot;
```
[53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L53) | [91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L91) | [92](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L92) | [93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L93)

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

/// @audit Missing `_trusted` check before state change
66: _trustedUserMrSigner[_mrSigner] = _trusted;
/// @audit Missing `_trusted` check before state change
70: _trustedUserMrEnclave[_mrEnclave] = _trusted;
```
[66](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L66) | [70](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L70)
</details>

### [G-96] Optimize External Calls with Assembly for Memory Efficiency

Using interfaces to make external contract calls in Solidity is convenient but can be inefficient in terms of memory utilization.
Each such call involves creating a new memory location to store the data being passed, thus incurring memory expansion costs. 

Inline assembly allows for optimized memory usage by re-using already allocated memory spaces or using the scratch space for smaller datasets.
This can result in notable gas savings, especially for contracts that make frequent external calls.

Additionally, using inline assembly enables important safety checks like verifying if the target address has code deployed to it using `extcodesize(addr)` before making the call, mitigating risks associated with contract interactions.

<details>
<summary><i>31 issue instances in 17 files:</i></summary>

```solidity
File: packages/protocol/contracts/common/AddressResolver.sol

83: addr_ = payable(IAddressManager(addressManager).getAddress(_chainId, _name));
```
[83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L83)

```solidity
File: packages/protocol/contracts/libs/LibAddress.sol

56: try IERC165(_addr).supportsInterface(_interfaceId) returns (bool _result) {
            result_ = _result;
71: return IERC1271(_addr).isValidSignature(_hash, _sig) == _EIP1271_MAGICVALUE;
```
[56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L56) | [71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L71)

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

177: IVerifier(verifier).verifyProof(ctx, _tran, _proof);
```
[177](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L177)

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

152: uint256(ITierProvider(tierProvider).getTier(ts.tier).cooldownWindow) * 60
                            + uint256(ts.timestamp).max(_state.slotB.lastUnpausedAt) > block.timestamp
                    ) {
                        // If cooldownWindow is 0, the block can theoretically
                        // be proved and verified within the same L1 block.
                        break;
```
[152](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L152)

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

176: IERC20(_token).safeTransfer(_to, IERC20(_token).balanceOf(address(this)));
```
[176](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L176)

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

174: if (!ISignalService(signalService).isSignalSent(address(this), msgHash)) {
                revert B_MESSAGE_NOT_SENT();
```
[174](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L174)

```solidity
File: packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

44: usdc.mint(_account, _amount);
48: usdc.transferFrom(_from, address(this), _amount);
49: usdc.burn(_amount);
```
[44](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L44) | [48](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L48) | [49](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L49)

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

82: IBridgedERC20(migratingAddress).mint(_account, _amount);
```
[82](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L82)

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

226: IERC1155(token).safeBatchTransferFrom(address(this), to, tokenIds, amounts, "");
230: BridgedERC1155(token).mintBatch(to, tokenIds, amounts);
```
[226](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L226) | [230](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L230)

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

184: IBridgedERC20(btokenOld_).changeMigrationStatus(_btokenNew, false);
185: IBridgedERC20(_btokenNew).changeMigrationStatus(btokenOld_, true);
330: IERC20(token_).safeTransfer(_to, _amount);
333: IBridgedERC20(token_).mint(_to, _amount);
360: IBridgedERC20(_token).burn(msg.sender, _amount);
```
[184](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L184) | [185](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L185) | [330](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L330) | [333](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L333) | [360](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L360)

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

171: IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);
176: BridgedERC721(token_).mint(_to, _tokenIds[i]);
```
[171](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L171) | [176](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L176)

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

128: (bool verified,) = IAttestation(automataDcapAttestation).verifyParsedQuote(_attestation);
```
[128](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L128)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

63: IERC20(token).transferFrom(vault, user, amount);
71: IVotes(token).delegateBySig(delegatee, nonce, expiry, v, r, s);
```
[63](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L63) | [71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L71)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

91: IERC20(token).transferFrom(vault, user, amount);
```
[91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L91)

```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

60: IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);
```
[60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L60)

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

219: IERC20(taikoToken).transferFrom(sharedVault, _to, amountToWithdraw);
220: IERC20(costToken).safeTransferFrom(_recipient, sharedVault, costToWithdraw);
```
[219](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L219) | [220](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L220)

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

285: verified = sigVerifyLib.verifyES256Signature(
                certs[i].tbsCertificate, certs[i].signature, issuer.pubKey
            );
322: bool qeSigVerified = sigVerifyLib.verifyES256Signature(
                pckSignedQeReportBytes, authDataV3.qeReportSignature, pckCertPubKey
            );
325: bool quoteSigVerified = sigVerifyLib.verifyES256Signature(
                signedQuoteData, authDataV3.ecdsa256BitSignature, authDataV3.ecdsaAttestationKey
            );
424: (certDecodedSuccessfully, parsedQuoteCerts[i]) = pemCertLib.decodeCert(
                    authDataV3.certification.decodedCertDataArray[i], isPckCert
                );
```
[285](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L285) | [322](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L322) | [325](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L325) | [424](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L424)
</details>

