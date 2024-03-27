# Analysis - `Taiko` Contest

![Taiko Protocol](https://code4rena.com/_next/image?url=https%3A%2F%2Fstorage.googleapis.com%2Fcdn-c4-uploads-v0%2Fuploads%2Fx3Q5DdF66oj.0&w=256&q=75)

## Description overview of `Taiko` Contest

Taiko is an innovative Ethereum layer 2 scaling solution that aims to reduce transaction fees while maintaining Ethereum's core properties, such as censorship resistance, permissionlessness, and security. It employs a two-pronged approach: the Based Contestable Rollup (BCR) and the Based Booster Rollup (BBR).

1. **Based Contestable Rollup (BCR)**: This is Taiko's initial milestone, introducing a permissionless and sequencer-free Layer 2 network. It uses a system of Liveness, Validity, and Contestation Bonds in the Taiko token (TKO) to ensure timely and accurate proof submissions. Network participants, known as provers, can engage in this process, enhancing decentralization and security. The BCR lays the foundation for Taiko's trust-minimized Layer 2 infrastructure.

2. **Based Booster Rollup (BBR)**: This innovative approach extends the BCR's functionality, allowing any rollup, whether optimistic or ZK, to be enhanced with BBR functionality, directly bolstering Ethereum's scalability.

The Taiko token (TKO) plays a crucial role in the contestable rollup design, underpinning critical bond systems in both BCR and BBR. These bonds, held in TKO, ensure the integrity and timeliness of network operations. Forfeited bonds are redirected to Taiko's Treasury on Layer 1, ensuring their value is conserved and utilized as per community consensus.

Taiko's governance model is decentralized, with the Taiko DAO comprising TKO holders who can influence network upgrades and manage the Taiko treasury on both Layer 1 and Layer 2. The total supply of TKO is fixed at 1 billion, with 18 decimals, and minting or burning is strictly governed to maintain transparency and consensus.

Taiko is a fully open-source, permissionless, Ethereum-equivalent ZK-Rollup, with no centralized actors operating the network. All operations are run permissionlessly by the community, with organizations like Taiko Labs, Taiko Treasury, Taiko DAO, Taiko Foundation, and Taiko Security Council playing essential roles in the ecosystem's development and governance.

One of Taiko's major differentiators is that it is a "based rollup," meaning its sequencing is driven by the base Ethereum Layer 1, rather than a centralized sequencer. This role falls on the shoulders of Ethereum Layer 1 validators, contributing to Taiko's decentralized and trustless nature.

## System Overview

## 1. Scope

### packages/protocol/contracts/common/AddressManager.sol:

This `AddressManager` contract implements an address `mapping` system for different `chain IDs` and `names`, allowing for setting and retrieving addresses while inheriting from `EssentialContract` and implementing the IAddressManager interface, with additional features such as `ownership` control and error handling for invalid parameters and unsupported operations.

### packages/protocol/contracts/common/AddressResolver.sol:

The `AddressResolver` contract, initialized with an `AddressManager` reference, serves as an abstract implementation of `IAddressResolver`, facilitating the resolution of named addresses while enforcing access control and chain ID validation.

### packages/protocol/contracts/common/EssentialContract.sol:

- The `EssentialContract` is an abstract contract that provides essential functionality for other contracts in a system. It includes:

  - **Ownership Management:** Inherits from `Ownable2StepUpgradeable` for multi-step ownership transfer.
  - **Address Resolution:** Inherits from `AddressResolver` for resolving named addresses.
  - **Pause/Unpause Mechanism:** Allows the contract to be paused and unpaused.
  - **Reentrancy Protection:** Prevents `_loadReentryLock` calls.

- **Key Features**

  - **Modifier `onlyFromOwnerOrNamed`:** Ensures that only the owner or an address resolved by a given name can call a function.
  - **Modifier `nonReentrant`:** Prevents reentrant calls.
  - **Modifier `whenPaused`:** Only allows function execution when the contract is paused.
  - **Modifier `whenNotPaused`:** Only allows function execution when the contract is not paused.
  - **Function `pause`:** Pauses the contract.
  - **Function `unpause`:** Unpauses the contract.
  - **Function `paused`:** Returns `true` if the contract is paused, `false` otherwise.
  - **Function `__Essential_init`:** Initializes the contract with the owner and address manager.

- **Upgradeability**

  -The contract inherits from `UUPSUpgradeable`, which allows it to be upgraded using the OpenZeppelin upgradeability mechanism.

Overall, the `EssentialContract` is a well-designed and secure base contract.

### packages/protocol/contracts/libs/Lib4844.sol:

This `Lib4844` library provides functions for handling `EIP-4844` blobs by evaluating points using a precompile, with constants defined for specific parameters such as the precompile address, field elements per blob, and the modulus of the `BLS curve`, along with error handling for failed evaluations and boundary checks for point coordinates.

### packages/protocol/contracts/libs/LibAddress.sol:

This `LibAddress` library provides utilities for `address-related` operations such as sending Ether safely, checking contract support for specific interfaces, validating signatures using `EIP-1271` or `ECDSA`, and verifying if the sender is an externally owned account `EOA`, with error handling for failed Ether transfers and contract interactions.

### packages/protocol/contracts/libs/LibMath.sol:

This `LibMath` library provides functions for comparing and returning the smaller or larger of two `uint256` values, enhancing mathematical capabilities within contracts.

### packages/protocol/contracts/libs/LibTrieProof.sol:

- The `LibTrieProof` library provides functions for verifying Merkle proofs in a Taiko Protocol. Specifically, it allows for `verifying` the value of a slot in the storage of an account.

- **Key Features**

  - **Function `verifyMerkleProof`:** Verifies a Merkle proof for a given account and slot.

- The `verifyMerkleProof` function takes the following parameters:

  - `_rootHash`: The Merkle root hash of the tree.
  - `_addr`: The address of the account.
  - `_slot`: The slot in the account's storage.
  - `_value`: The expected value of the slot.
  - `_accountProof`: The Merkle proof for the account.
  - `_storageProof`: The Merkle proof for the storage slot.

  - The function first checks if the account proof is `empty`. If it is, then the `root hash` is used as the account's storage root. Otherwise, the account proof is used to retrieve the account's storage root.

  - Next, the function verifies the storage proof using the `SecureMerkleTrie` library. If the proof is valid, then the function returns `true`. Otherwise, it reverts.

- Overall, the `LibTrieProof` library is a well-designed and secure library for verifying Merkle proofs in protocol.

### packages/protocol/contracts/L1/gov/TaikoGovernor.sol:

`TaikoGovernor` contract inherits from various `OpenZeppelin` `governor-related` contracts to create a comprehensive governance system, allowing for `proposal creation`, `execution`, and `management`, with configurable parameters such as `voting delay`, `voting period`, and `proposal threshold` for Taiko token holders.

### packages/protocol/contracts/L1/gov/TaikoTimelockController.sol:

`TaikoTimelockController` extends the OpenZeppelin `TimelockControllerUpgradeable` contract and provides additional functionality for initializing the contract with a minimum delay and allowing the admin to bypass the minimum delay requirement when necessary.

### packages/protocol/contracts/L1/hooks/AssignmentHook.sol:

`AssignmentHook` serves as a hook for `verifying` prover assignments and processing fees, interacting with `TaikoL1` contracts, implementing assignment validation logic, `signature verification`, and `fee processing` for assigned provers based on specified conditions and `fee tiers`.

### packages/protocol/contracts/L1/libs/LibDepositing.sol:

- The `LibDepositing` library provides functions for handling Ether deposits in the Taiko protocol. It includes functionality for:

  - Depositing Ether to Layer 2
  - Processing batched Ether deposits
  - Checking if Ether deposit is allowed for Layer 2
  - Encoding Ether deposits into a uint256

- **Key Features**

  - **Function `depositEtherToL2`:** Deposits Ether to Layer 2.
  - **Function `processDeposits`:** Processes batched Ether deposits.
  - **Function `canDepositEthToL2`:** Checks if Ether deposit is allowed for Layer 2.
  - **Function `_encodeEthDeposit`:** Encodes the given deposit into a uint256.

- The `depositEtherToL2` function checks if the deposit is valid and then sends the Ether to Layer 2. The `processDeposits` function processes batched Ether deposits and sends them to Layer 2. The `canDepositEthToL2` function checks if Ether deposit is allowed for Layer 2. The `_encodeEthDeposit` function encodes the given deposit into a uint256.

- The `canDepositEthToL2` function takes the following parameters:

  - `_state`: The current TaikoData.State.
  - `_config`: The current TaikoData.Config.
  - `_amount`: The amount of Ether to deposit.

### packages/protocol/contracts/L1/libs/LibProposing.sol:

- The `LibProposing` library provides functions for handling block proposals in the Taiko protocol. It includes functionality for:

  - Proposing a Taiko L2 block
  - Checking if a blob is reusable
  - Determining if the proposer is permitted

- **Key Features**

  - **Function `proposeBlock`:** Proposes a Taiko L2 block.
  - **Function `isBlobReusable`:** Checks if a blob is reusable.
  - **Function `_isProposerPermitted`:** Determines if the proposer is permitted.

- The `proposeBlock` function takes the following parameters:

  - `_state`: The current TaikoData.State.
  - `_config`: The current TaikoData.Config.
  - `_resolver`: The address resolver interface.
  - `_data`: Encoded data bytes containing the block params.
  - `_txList`: Transaction list bytes (if not blob).

  - The function first checks if the proposer is permitted. If the proposer is not permitted, the function reverts.

  - Next, the function initializes the block metadata and updates certain meta fields. The function then creates the block that will be stored on-chain and stores the block in the ring buffer.

  - Finally, the function runs all hooks and checks that the Taiko Token balance of this contract have increased by the same amount as `_config.livenessBond`.

- The `isBlobReusable` function takes the following parameters:

  - `_state`: The current TaikoData.State.
  - `_config`: The TaikoData.Config.
  - `_blobHash`: The blob hash.

  - The function checks if the blob is reusable. If the blob is reusable, the function returns `true`. Otherwise, the function returns `false`.

- The `_isProposerPermitted` function takes the following parameters:

  - `_slotB`: The current TaikoData.SlotB.
  - `_resolver`: The address resolver interface.

  - The function checks if the proposer is permitted. If the proposer is permitted, the function returns `true`. Otherwise, the function returns `false`.

### packages/protocol/contracts/L1/libs/LibProving.sol:

- Tthe `LibProving` library, which handles `block contestation` and proving in the Taiko protocol. It includes functions for `pausing` or `unpausing` the proving process, proving or contesting a block transition, and handling the transition initialization logic.

- **Key Functions:**

  - **pauseProving**: Pauses or unpauses the proving process, updating the `provingPaused` flag in the TaikoData.State struct.
  - **proveBlock**: Proves or contests a block transition. It verifies the proof, updates the transition state, and emits events for transition proved or contested.
  - **`_createTransition`**: Initializes a transition state if it doesn't exist for the given parent hash, block, and slot. It assigns an ID to the transition and initializes its fields.
  - **`_overrideWithHigherProof`**: Handles the case when a higher tier proof overwrites a lower tier proof. It updates the transition state, transfers rewards, and adjusts the validity bond and contest bond.
  - **`_checkProverPermission`**: Checks if the prover is allowed to submit a proof for the block based on the tier and proving window rules.

- **Data Structures:**

  - **TaikoData.State**: Stores the current state of the Taiko protocol, including the `provingPaused` flag and other configuration parameters.

  - **TaikoData.Block**: Represents a block in the Taiko blockchain, including its metadata, proposed timestamp, and assigned prover.

  - **TaikoData.Transition**: Represents a transition in the Taiko blockchain, including its parent hash, block hash, state root, and other transition-related data.

  - **TaikoData.TierProof**: Represents a proof for a transition, including the tier of the proof and the proof data.

  - **ITierProvider.Tier**: Represents a tier in the Taiko protocol, including its name, verifier contract name, validity bond, contest bond, maximum blocks to verify per proof, and proving window duration.

- **Events:**

  - **TransitionProved**: Emitted when a transition is proved, including the block ID, transition data, prover address, validity bond, and tier.

  - **TransitionContested**: Emitted when a transition is contested, including the block ID, transition data, contester address, contest bond, and tier.

  - **ProvingPaused**: Emitted when proving is paused or unpaused, indicating the pause status.

- **Errors:**

  - **L1_ALREADY_CONTESTED**: Raised when trying to contest an already contested transition.
  - **L1_ALREADY_PROVED**: Raised when trying to prove a transition that has already been proved.
  - **L1_ASSIGNED_PROVER_NOT_ALLOWED**: Raised when the assigned prover attempts to prove a block other than the first transition.
  - **L1_BLOCK_MISMATCH**: Raised when the block data provided does not match the stored block data.
  - **L1_INVALID_BLOCK_ID**: Raised when the provided block ID is invalid.
  - **L1_INVALID_PAUSE_STATUS**: Raised when trying to pause or unpause proving with an invalid pause status.
  - **L1_INVALID_TIER**: Raised when the tier of the proof is not supported or is invalid.
  - **L1_INVALID_TRANSITION**: Raised when the provided transition data is invalid.
  - **L1_MISSING_VERIFIER**: Raised when the verifier contract for a tier is missing.
  - **L1_NOT_ASSIGNED_PROVER**: Raised when a non-assigned prover tries to prove a transition other than the first one.

### packages/protocol/contracts/L1/libs/LibUtils.sol:

- `LibUtils` library which offers helper functions for working with Taiko data structures. It includes functions for retrieving `transitions` and blocks based on their IDs or parent hashes.

- **Key Functions:**

  - **getTransition**: Retrieves the transition state data for a block with a given ID and parent hash. It checks that the block exists and reverts if the transition is not found.

  - **getBlock**: Retrieves the block data for a block with a given ID. It checks that the block exists and reverts if it does not.

  - **getTransitionId**: Retrieves the ID of the transition with a given parent hash. It returns 0 if the transition is not found.

- **Data Structures:**

  - **TaikoData.State**: Stores the current state of the Taiko protocol, including the block ring buffer and transition states.

  - **TaikoData.Config**: Stores the configuration parameters of the Taiko protocol, including the block ring buffer size.

  - **TaikoData.Block**: Represents a block in the Taiko blockchain, including its metadata, proposed timestamp, and assigned prover.

  - **TaikoData.TransitionState**: Represents a transition in the Taiko blockchain, including its parent hash, block hash, state root, and other transition-related data.

- **Errors:**

  - **L1_BLOCK_MISMATCH**: Raised when the block data provided does not match the stored block data.

  - **L1_INVALID_BLOCK_ID**: Raised when the provided block ID is invalid.

  - **L1_TRANSITION_NOT_FOUND**: Raised when the transition with the given parent hash is not found.

  - **L1_UNEXPECTED_TRANSITION_ID**: Raised when the transition ID is unexpected or out of range.

### packages/protocol/contracts/L1/libs/LibVerifying.sol:

`LibVerifying` library which handles `block verification` in the Taiko protocol. It includes functions for `verifying blocks`, initializing the protocol state, and syncing chain data.

- **Key Functions:**

  - **init**: Initializes the Taiko protocol state with the genesis block hash and configuration parameters.

  - **verifyBlocks**: Verifies up to a specified number of blocks, updating the last verified block ID and state root. It also handles bond distribution to provers and syncs chain data if necessary.

  - **`_syncChainData`**: Syncs the latest state root to the Signal Service if the last verified block ID exceeds a threshold.

- **Data Structures:**

  - **TaikoData.State**: Stores the current state of the Taiko protocol, including the block ring buffer and transition states.

  - **TaikoData.Config**: Stores the configuration parameters of the Taiko protocol, including the block ring buffer size, block gas limit, and bond amounts.

  - **TaikoData.Block**: Represents a block in the Taiko blockchain, including its metadata, proposed timestamp, and assigned prover.

  - **TaikoData.TransitionState**: Represents a transition in the Taiko blockchain, including its parent hash, block hash, state root, and other transition-related data.

- **Errors:**

  - **L1_BLOCK_MISMATCH**: Raised when the block data provided does not match the stored block data.

  - **L1_INVALID_CONFIG**: Raised when the provided configuration parameters are invalid.

  - **L1_TRANSITION_ID_ZERO**: Raised when the transition ID is zero.

### packages/protocol/contracts/L1/provers/GuardianProver.sol:

`GuardianProver` extends functionality from Guardians to allow guardians to approve `guardian proofs`, triggering the proving transaction and `emitting` events based on successful approvals or rejections, while integrating with TaikoL1 contracts and handling block metadata, `transitions`, and `tier proofs`.

### packages/protocol/contracts/L1/provers/Guardians.sol:

`Guardians` manages a set of guardians and their approvals through `mappings` and arrays, providing functions to `set guardians`, `check approvals`, and handle `guardian-related` operations while ensuring minimum guardian requirements and emitting relevant events.

### packages/protocol/contracts/L1/TaikoData.sol:

`TaikoData` contract defines various data structures such as `configuration parameters`, `block metadata`, `transition states`, and `Ethereum deposits`, used within the Taiko protocol, specifying their attributes and relationships for efficient contract operations.

### packages/protocol/contracts/L1/TaikoL1.sol:

- `TaikoL1` contract which serves as the `base layer contract` of the Taiko protocol. It handles `block proposing`, `proving`, and `verifying`, as well as Ether and Taiko token deposits and withdrawals.

- **Key Functions:**

  - **proposeBlock**: Proposes a new block to the Taiko blockchain. It includes the block metadata and a list of transactions.

  - **proveBlock**: Proves a proposed block using a state transition and a tier proof.

  - **verifyBlocks**: Verifies a specified number of blocks, updating the last verified block ID and state root.

  - **pauseProving**: Pauses or unpauses block proving.

  - **depositEtherToL2**: Deposits Ether to Layer 2.

  - **unpause**: Unpauses the contract and updates the `lastUnpausedAt` timestamp.

  - **canDepositEthToL2**: Checks if Ether deposit is allowed for Layer 2.

  - **isBlobReusable**: Checks if a blob hash can be reused for block proposal.

  - **getBlock**: Retrieves a block and its associated transition state.

  - **getTransition**: Retrieves the transition state for a specific block and parent hash.

  - **getStateVariables**: Retrieves the state variables of the contract.

- **Data Structures:**

  - **TaikoData.State**: Stores the current state of the Taiko protocol, including the block ring buffer and transition states.

  - **TaikoData.Config**: Stores the configuration parameters of the Taiko protocol, including the block ring buffer size, block gas limit, and bond amounts.

  - **TaikoData.Block**: Represents a block in the Taiko blockchain, including its metadata, proposed timestamp, and assigned prover.

  - **TaikoData.TransitionState**: Represents a transition in the Taiko blockchain, including its parent hash, block hash, state root, and other transition-related data.

- **Errors:**

  - **L1_INVALID_BLOCK_ID**: Raised when the provided block ID is invalid.

  - **L1_PROVING_PAUSED**: Raised when block proving is paused.

  - **L1_RECEIVE_DISABLED**: Raised when receiving Ether is disabled.

- **Events:**

  - **BlockProposed**: Emitted when a new block is proposed.

  - **BlockProven**: Emitted when a block is proven.

  - **BlocksVerified**: Emitted when multiple blocks are verified.

  - **ProvingPaused**: Emitted when block proving is paused.

  - **ProvingUnpaused**: Emitted when block proving is unpaused.

  - **EtherDepositedToL2**: Emitted when Ether is deposited to Layer 2.

### packages/protocol/contracts/L1/TaikoToken.sol:

`TaikoToken` is an ERC20 token with additional features such as `snapshotting`, `voting delegation`, and `permit support`, used within the `Taiko` protocol for prover collateral in the form of `bonds`, `featuring a minting function`, `burning tokens`, and transfer restrictions to prevent sending tokens to the token contract itself.

### packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol:

`DevnetTierProvider` implements the `ITierProvider` interface to provide tier information such as `verifier names`, `bond amounts`, `cooldown windows`, `proving windows`, and `maximum blocks` to verify per proof for the Optimistic and Guardian tiers within the Taiko protocol.

### packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol:

This contract `MainnetTierProvider` implements the `ITierProvider` interface to provide tier information such as `verifier names`, `bond amounts`, `cooldown windows`, `proving windows`, and `maximum blocks` to `verify per proof` for the `SGX`, SGX with ZKVM, and Guardian tiers within the Taiko protocol, with specific conditions for determining the minimum required tier based on a random value.

### packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol:

This contract `TestnetTierProvider` provide tier information such as `verifier names`, bond amounts, cooldown windows, proving windows, and maximum blocks to verify per proof for the Optimistic, SGX, and Guardian tiers within the Taiko protocol, with specific conditions for determining the minimum required tier based on a random value, where `10%` of blocks require `SGX` proofs and the rest are optimistic without validity proofs.

### packages/protocol/contracts/L2/CrossChainOwned.sol:

`CrossChainOwned` is an abstract contract that allows its owner to be either a `local address` or an address on another chain, using signals for `transaction approval`, and it defines functionality related to `transaction execution` based on specific conditions such as the owner `chain ID` and `transaction ID` validation.

### packages/protocol/contracts/L2/Lib1559Math.sol:

- The `Lib1559Math` library which implements an `exponential bonding curve` for `EIP-1559`. This curve is used to calculate the base fee for transactions based on the amount of excess gas issued.

- **Key Functions:**

  - **basefee**: Calculates the base fee based on the excess gas issued and the adjustment factor.

- **Mathematical Formula:**

  - The base fee is calculated using the following formula:

  ```solidity
  basefee = eth_qty(excess_gas_issued) / (TARGET * ADJUSTMENT_QUOTIENT)
  ```

  - where:

  - `eth_qty` is a function that converts the excess gas issued to an Ethereum quantity using an exponential bonding curve.
  - `TARGET` is the target gas usage for a block.
  - `ADJUSTMENT_QUOTIENT` is a constant that adjusts the curve's sensitivity.

- **Implementation Details:**

  - The `_ethQty` function uses the `exp` function from the `LibFixedPointMath` library to calculate the Ethereum quantity based on the excess gas issued and the adjustment factor.
  - The `basefee` function divides the result of `_ethQty` by the adjustment factor and the scaling factor to obtain the base fee.

### packages/protocol/contracts/L2/TaikoL2.sol:

- The `TaikoL2` contract which is responsible for anchoring the latest `L1` block details to `L2` for `cross-layer` communication, managing `EIP-1559` gas pricing for Layer 2 (L2) operations, and storing verified L1 block information.

- **Key Functions:**

  - **anchor**: Anchors the latest `L1` block details to `L2`, including the block hash, state root, block ID, and parent gas used.

  - **withdraw**: Withdraws tokens or Ether from the contract.

  - **getBasefee**: Calculates the base fee per gas using EIP-1559 configuration for the given parameters.

  - **getBlockHash**: Retrieves the block hash for a given L2 block number.

  - **getConfig**: Returns the EIP-1559 related configurations.

  - **skipFeeCheck**: Indicates whether to skip checking base fee mismatch (for simulation purposes).

- **Data Structures:**

  - **Config**: Stores the EIP-1559 configuration parameters, including the gas target per L1 block and the base fee adjustment quotient.

- **Errors:**

  - **L2_BASEFEE_MISMATCH**: Raised when the base fee per gas is incorrect.

  - **L2_INVALID_CHAIN_ID**: Raised when the chain ID is invalid.

  - **L2_INVALID_PARAM**: Raised when invalid parameters are provided.

  - **L2_INVALID_SENDER**: Raised when the sender is not authorized.

  - **L2_PUBLIC_INPUT_HASH_MISMATCH**: Raised when the public input hash does not match.

  - **L2_TOO_LATE**: Raised when the contract is initialized too late.

### packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol:

This `TaikoL2EIP1559Configurable` contract extends the `TaikoL2` contract and introduces a setter function to change `EIP-1559` configurations and states, emitting an event when these changes occur.

### packages/protocol/contracts/signal/SignalService.sol:

- The provided `SignalService` contract which is responsible for `sending` and `receiving` signals (messages) across different chains and layers. It also provides functionality for synchronizing chain data and `verifying signal proofs`.

- **Key Functions:**

  - **sendSignal**: Sends a signal to the contract's own chain.

  - **syncChainData**: Synchronizes chain data from another chain, such as the state root or a specific block hash.

  - **proveSignalReceived**: Verifies a proof that a signal was received on another chain.

  - **isChainDataSynced**: Checks if a specific chain data is synchronized with the contract.

  - **isSignalSent**: Checks if a signal has been sent from a specific address.

  - **getSyncedChainData**: Retrieves the synchronized chain data for a given chain ID, kind, and block ID.

  - **signalForChainData**: Calculates the signal hash for a specific chain data.

- **Events:**

  - **SignalSent**: Emitted when a signal is sent.

  - **ChainDataSynced**: Emitted when chain data is synchronized.

- **Errors:**

  - **SS_EMPTY_PROOF**: Raised when the proof is empty.

  - **SS_INVALID_SENDER**: Raised when the sender is not authorized.

  - **SS_INVALID_LAST_HOP_CHAINID**: Raised when the last hop chain ID is invalid.

  - **SS_INVALID_MID_HOP_CHAINID**: Raised when a mid-hop chain ID is invalid.

  - **SS_INVALID_STATE**: Raised when the state is invalid.

  - **SS_INVALID_VALUE**: Raised when the value is invalid.

  - **SS_SIGNAL_NOT_FOUND**: Raised when the signal is not found.

  - **SS_UNAUTHORIZED**: Raised when the sender is not authorized.

  - **SS_UNSUPPORTED**: Raised when a function is not supported.

### packages/protocol/contracts/bridge/Bridge.sol:

- The `Bridge` contract is a core component of the Taiko `cross-chain` messaging system. It serves as a gateway for sending and receiving messages between different blockchain networks. The contract manages the lifecycle of messages, including their creation, transmission, and execution.

- **Key Features**

  - **Message Sending:** Allows users to send messages to other chains. Messages include details such as the sender, recipient, value, and gas limit.
  - **Message Receiving:** Handles the receipt of messages from other chains and verifies their authenticity using merkle inclusion proofs.
  - **Message Execution:** Executes received messages on the current chain, invoking the appropriate functions in the target contract.
  - **Message Status Tracking:** Maintains the status of messages throughout their lifecycle, including `NEW`, `DONE`, `FAILED`, and `RETRIABLE`.
  - **Invocation Delay:** Introduces a configurable delay before messages can be executed, providing time for security checks and fraud detection.
  - **Message Recalling:** Allows users to recall messages before they are executed, preventing unauthorized access to funds.
  - **Banning Addresses:** Enables the contract owner to ban specific addresses from interacting with the bridge.

- **Events:**

  - `MessageSent`: Emitted when a message is sent.
  - `MessageReceived`: Emitted when a message is received.
  - `MessageExecuted`: Emitted when a message is executed.
  - `MessageStatusChanged`: Emitted when the status of a message changes.
  - `AddressBanned`: Emitted when an address is banned.
  - `MessageSuspended`: Emitted when a message is suspended.
  - `MessageRecalled`: Emitted when a message is recalled.
  - `MessageRetried`: Emitted when a message is retried.

- **Functions:**

  - `sendMessage`: Allows users to send messages.
  - `recallMessage`: Allows users to recall messages before they are executed.
  - `processMessage`: Handles the receipt and execution of messages.
  - `retryMessage`: Allows users to retry failed or retriable messages.
  - `isMessageSent`: Checks if a message has been sent.
  - `proveMessageFailed`: Checks if a message has failed on the destination chain.
  - `proveMessageReceived`: Checks if a message has been received on the current chain.
  - `isDestChainEnabled`: Checks if a destination chain is enabled.
  - `context`: Returns the current call context.
  - `getInvocationDelays`: Returns the invocation delay values.
  - `hashMessage`: Computes the hash of a message.
  - `signalForFailedMessage`: Computes the signal representing a failed message.

- **Limitations**

  - The bridge relies on the reliability of the underlying blockchain networks and the signal service used for message transmission.
  - The invocation delay can potentially delay the execution of critical messages.
  - The contract does not support the transfer of arbitrary data types. such as:

  - **Invocation Delays:** Delays before messages can be executed to prevent premature execution.
  - **Message Status Tracking:** Tracks the status of each message to ensure it is processed correctly.
  - **Address Banning:** Allows administrators to ban addresses from sending messages.

### packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol:

- The `USDCAdapter` contract which is a `bridged` ERC20 token adapter for USDC. It allows for minting and burning of USDC tokens on the local chain, while the actual minting and burning operations are performed on the remote chain.

### packages/protocol/contracts/tokenvault/BridgedERC20.sol:

- Is an upgradeable ERC20 contract that represents tokens bridged from another chain. It is an implementation of the `BridgedERC20Base` contract which provides the basic functionality for a bridged token.

- The BridgedERC20 contract includes the following additional features:

  - **ERC20MetadataUpgradeable:** This interface provides the name, symbol, and decimals of the token.
  - **ERC20SnapshotUpgradeable:** This interface allows for the creation of snapshots of the token's state at specific points in time.
  - **ERC20VotesUpgradeable:** This interface allows for the creation of voting rights for token holders.

- The BridgedERC20 contract is initialized with the following parameters:

  - **`_owner`:** The owner of the contract.
  - **`_addressManager`:** The address of the AddressManager contract.
  - **`_srcToken`:** The source token address.
  - **`_srcChainId`:** The source chain ID.
  - **`_decimals`:** The number of decimal places of the source token.
  - **`_symbol`:** The symbol of the token.
  - **`_name`:** The name of the token.

- The BridgedERC20 contract has the following public functions:

  - **`init`:** Initializes the contract.
  - **`setSnapshoter`:** Sets the snapshoter address.
  - **`snapshot`:** Creates a new token snapshot.
  - **`name`:** Gets the name of the token.
  - **`symbol`:** Gets the symbol of the bridged token.
  - **`decimals`:** Gets the number of decimal places of the token.
  - **`canonical`:** Gets the canonical token's address and chain ID.

- The BridgedERC20 contract has the following internal functions:

  - **`_mintToken`:** Mints a new token.
  - **`_burnToken`:** Burns a token.
  - **`_beforeTokenTransfer`:** Called before a token transfer.
  - **`_afterTokenTransfer`:** Called after a token transfer.
  - **`_mint`:** Mints a new token.
  - **`_burn`:** Burns a token.

- The BridgedERC20 contract has the following errors:

  - **BTOKEN_CANNOT_RECEIVE:** The token cannot be received by this contract.
  - **BTOKEN_UNAUTHORIZED:** The caller is not authorized to call the function.`: Internal function to burn tokens.
    - **ERC20 and Voting Hooks:**
      - `_beforeTokenTransfer`: Implements ERC20 and ERC20Votes transfer hooks.
      - `_afterTokenTransfer`: Implements ERC20 and ERC20Votes transfer hooks.
      - `_mint`: Implements ERC20 and ERC20Votes mint hooks.
      - `_burn`: Implements ERC20 and ERC20Votes burn hooks.

### packages/protocol/contracts/tokenvault/BridgedERC20Base.sol:

- **BridgedERC20Base** is a base contract for bridged ERC20 tokens. It provides the following functionality:

  - **Migration:** Allows the contract to migrate tokens to or from another contract.
  - **Minting:** Allows the contract to mint new tokens.
  - **Burning:** Allows the contract to burn tokens.

- The BridgedERC20Base contract has the following public functions:

  - **changeMigrationStatus:** Start or stop migration to/from a specified contract.
  - **mint:** Mints tokens to the specified account.
  - **burn:** Burns tokens from the specified account.
  - **owner:** Returns the owner of the contract.

- The BridgedERC20Base contract has the following internal functions:

  - **`_mintToken`:** Mints tokens to the specified account.
  - **`_burnToken`:** Burns tokens from the specified account.
  - **`_isMigratingOut`:** Returns true if the contract is migrating tokens out, false otherwise.

- The BridgedERC20Base contract has the following errors:

  - **BB_PERMISSION_DENIED:** The caller does not have permission to perform the operation.
  - **BB_INVALID_PARAMS:** The provided parameters are invalid.
  - **BB_MINT_DISALLOWED:** Minting is not allowed while migrating outbound.

### packages/protocol/contracts/tokenvault/BridgedERC721.sol:

- Bridging `ERC721` tokens across different chains providing the functionality to `mint` and `burn` tokens while maintaining a connection to the source token and chain ID. chain ID.

- The BridgedERC721 contract has the following public functions:

  - **init:** Initializes the contract.
  - **mint:** Mints tokens.
  - **burn:** Burns tokens.
  - **name:** Gets the name of the token.
  - **symbol:** Gets the symbol of the bridged token.
  - **source:** Gets the source token and source chain ID being bridged.
  - **tokenURI:** Returns the token URI.

- The BridgedERC721 contract has the following internal functions:

  - **`_beforeTokenTransfer`:** Called before any token transfer.

- The BridgedERC721 contract has the following errors:

  - **BTOKEN_CANNOT_RECEIVE:** The token cannot be received by this contract.
  - **BTOKEN_INVALID_BURN:** The token cannot be burned by the caller.

### packages/protocol/contracts/tokenvault/BridgedERC1155.sol:

- Bridging `ERC1155` tokens across different chains providing the functionality to mint and burn tokens while maintaining a connection to the source token and `chain ID`.

- The `BridgedERC1155` contract has the following public functions:

  - **init:** Initializes the contract.
  - **mint:** Mints tokens.
  - **mintBatch:** Mints multiple tokens in a single transaction.
  - **burn:** Burns tokens.
  - **name:** Gets the name of the bridged token.
  - **symbol:** Gets the symbol of the bridged token.

- The BridgedERC1155 contract has the following internal functions:

  - **`_beforeTokenTransfer`:** Called before any token transfer.

- The BridgedERC1155 contract has the following errors:

  - **BTOKEN_CANNOT_RECEIVE:** The token cannot be received by this contract.

### packages/protocol/contracts/tokenvault/BaseNFTVault.sol:

- `BaseNFTVault` is an abstract contract for bridging NFTs across different chains.

  - **Bridging:** Allows the transfer of NFTs from one chain to another.
  - **Canonical Tokens:** Maintains a mapping between bridged NFTs and their canonical counterparts on other chains.
  - **Bridged Tokens:** Maintains a mapping between canonical NFTs and their bridged counterparts on this chain.

- The BaseNFTVault contract has the following public functions:

  - **canonicalToBridged:** Gets the bridged token address for a given canonical token address.
  - **bridgedToCanonical:** Gets the canonical token address for a given bridged token address.

- The BaseNFTVault contract has the following internal functions:

  - **`_sendToken`:** Sends a token to another chain.
  - **`_releaseToken`:** Releases a token on the current chain.

- The BaseNFTVault contract has the following events:

  - **BridgedTokenDeployed:** Emitted when a new bridged token is deployed.
  - **TokenSent:** Emitted when a token is sent to another chain.
  - **TokenReleased:** Emitted when a token is released on the current chain.
  - **TokenReceived:** Emitted when a token is received from another chain.

- The BaseNFTVault contract has the following errors:

  - **VAULT_INVALID_TOKEN:** The token address is invalid.
  - **VAULT_INVALID_AMOUNT:** The amount of tokens to transfer is invalid.
  - **VAULT_INVALID_TO:** The recipient address is invalid.
  - **VAULT_INTERFACE_NOT_SUPPORTED:** The token does not support the required interface.
  - **VAULT_TOKEN_ARRAY_MISMATCH:** The token ID array and the amount array must have the same length.
  - **VAULT_MAX_TOKEN_PER_TXN_EXCEEDED:** The maximum number of tokens that can be transferred per transaction has been exceeded.

### packages/protocol/contracts/tokenvault/BaseVault.sol:

- `BaseVault` is an abstract contract that provides a base implementation for vaults. Vaults are used to manage the bridging of assets between different chains.

- The BaseVault contract has the following public functions:

  - **init:** Initializes the contract.
  - **supportsInterface:** Checks if the contract supports the given interface.
  - **name:** Returns the name of the vault.

- The BaseVault contract has the following internal functions:

  - **checkProcessMessageContext:** Checks if the message context is valid.
  - **checkRecallMessageContext:** Checks if the recall message context is valid.

- The BaseVault contract has the following errors:

  - **VAULT_PERMISSION_DENIED:** The caller does not have permission to perform the operation.

### packages/protocol/contracts/tokenvault/ERC1155Vault.sol:

- The `ERC1155Vault` contract holds `ERC1155` tokens deposited by users and manages the mapping between canonical tokens and their bridged tokens. It allows users to send ERC1155 tokens to other chains by invoking the `sendToken` function and receive bridged tokens on the destination chain by invoking the `onMessageInvocation` function.

- **Key Features**

  - **ERC1155 Token Vault:** Holds ERC1155 tokens deposited by users.
  - **Canonical Token Mapping:** Manages the mapping between canonical tokens (tokens that live on the source chain) and bridged tokens (tokens that live on the destination chain).
  - **Bridged Token Deployment:** Deploys bridged token contracts on the destination chain if they do not exist.
  - **Message Handling:** Handles messages from the bridge on the destination chain to transfer bridged tokens to users.
  - **Message Recall Handling:** Handles messages from the bridge to recall bridged tokens and refund users.

- **Functions**

  - **sendToken:** Transfers ERC1155 tokens to the vault and sends a message to the destination chain to create bridged tokens.
  - **onMessageInvocation:** Handles messages from the bridge on the destination chain to transfer bridged tokens to users.
  - **onMessageRecalled:** Handles messages from the bridge to recall bridged tokens and refund users.
  - **onERC1155BatchReceived:** Receives ERC1155 tokens from the bridge on the source chain.
  - **onERC1155Received:** Receives ERC1155 tokens from the bridge on the source chain.

- **Events**

  - **TokenSent:** Emitted when tokens are sent to the destination chain.
  - **TokenReceived:** Emitted when bridged tokens are received on the destination chain.
  - **TokenReleased:** Emitted when bridged tokens are recalled and refunded.
  - **BridgedTokenDeployed:** Emitted when a new bridged token contract is deployed.

### packages/protocol/contracts/tokenvault/ERC20Vault.sol:

- The `ERC20Vault` contract which serves as a central repository for `ERC20` tokens within a `cross-chain` bridge system. Its primary purpose is to facilitate the transfer of ERC20 tokens between different chains while maintaining accurate token balances and ensuring the integrity of the bridging process.

- **Key Features**

  - **Token Deposits and Withdrawals**

    - Users can deposit ERC20 tokens into the vault by transferring them to the contract's address.
    - Bridged tokens are minted on the destination chain when tokens are transferred to the vault.
    - When tokens are received from another chain, they are released from the vault and transferred to the recipient's address.

  - **Cross-Chain Token Transfers**

    - The `sendToken` function allows users to initiate cross-chain token transfers by providing the destination chain ID, recipient address, token address, and amount.
    - The function generates a message containing the necessary data and sends it to the bridge contract.
    - The bridge contract relays the message to the destination chain, where the tokens are released and transferred to the recipient.

  - **Bridged Token Management**

    - The vault maintains a mapping between canonical ERC20 tokens (native tokens on their respective chains) and their corresponding bridged tokens (tokens that represent the canonical tokens on other chains).
    - The `changeBridgedToken` function allows the contract owner to update the bridged token address for a given canonical token.

### packages/protocol/contracts/tokenvault/ERC721Vault.sol:

- The `ERC721Vault` contract serves as a central repository for `ERC721` tokens within a `cross-chain` bridge system. Its primary purpose is to facilitate the transfer of `ERC721` tokens between different chains while maintaining accurate token balances and ensuring the integrity of the bridging process.

- **Key Features**

  - **Token Deposits and Withdrawals**

    - Users can deposit ERC721 tokens into the vault by transferring them to the contract's address.
    - Bridged tokens are minted on the destination chain when tokens are transferred to the vault.
    - When tokens are received from another chain, they are released from the vault and transferred to the recipient's address.

  - **Cross-Chain Token Transfers**

    - The `sendToken` function allows users to initiate cross-chain token transfers by providing the destination chain ID, recipient address, token address, token IDs, and amounts.
    - The function generates a message containing the necessary data and sends it to the bridge contract.
    - The bridge contract relays the message to the destination chain, where the tokens are released and transferred to the recipient.

  - **Bridged Token Management**

    - The vault maintains a mapping between canonical ERC721 tokens (native tokens on their respective chains) and their corresponding bridged tokens (tokens that represent the canonical tokens on other chains).
    - The `changeBridgedToken` function allows the contract owner to update the bridged token address for a given canonical token.

### packages/protocol/contracts/tokenvault/LibBridgedToken.sol:

This `LibBridgedToken` contract provides functions to validate input parameters, `build names`, `symbols`, and URIs for bridged tokens, ensuring correct formatting and integrity for `cross-chain` token representation and interaction.

### packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol:

This library `ExcessivelySafeCall` provides a way to make calls to external contracts with an additional safety layer to limit the amount of returndata copied to prevent potential `out-of-gas` issues caused by malicious contracts returning excessively large data.

### packages/protocol/contracts/thirdparty/optimism/Bytes.sol:

The `Bytes` library provides functions for `manipulating` byte arrays, including `slicing a byte array`, converting it into nibbles, and comparing byte arrays by comparing their keccak256 hashes.

### packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol:

The `RLPReader` library is designed to parse `RLP-encoded` byte arrays including functions for `converting bytes to RLP` items, reading RLP lists and bytes, `decoding RLP item lengths`, and copying bytes from memory locations.

### packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol:

This `RLPWriter` library is designed to encode some types such as `byte strings` and `uint256` values into `RLP` format, with functions to handle `encoding lengths` and `converting integers` to big-endian binary form without leading zeroes.

### packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol:

The `MerkleTrie` library provides functionality for `verifying` inclusion proofs and `retrieving values` associated with keys in a `Merkle-Patricia trie`, handling various trie node types, node IDs, and path comparisons efficiently.

### packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol:

`SecureMerkleTrie` library is a `wrapper` around the `MerkleTrie library` that hashes input keys using `Keccak256` before passing them to the `MerkleTrie` functions for verifying inclusion proofs and retrieving values from a Merkle trie, ensuring compatibility with Ethereum's state trie behavior.

### packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol:

`LibFixedPointMath` library provides a `fixed-point` math function `exp(int256 x)` that computes the exponential function `e^x` in `1e18` `fixed-point` format, with rigorous handling of input ranges and precision adjustments to ensure accurate results within the specified bounds.

### packages/protocol/contracts/verifiers/GuardianVerifier.sol:

The `GuardianVerifier` contract is an implementation of the `IVerifier` interface that restricts access to the `verifyProof` function based on the caller's identity, requiring it to match a specific address resolved through the address manager.

### packages/protocol/contracts/verifiers/SgxVerifier.sol:

The `SgxVerifier` contract serves as a component within a `cross-chain` bridge system. Its primary purpose is to verify the authenticity of `SGX` instances and their proofs to ensure the integrity of `cross-chain` message attestations.

- **Key Features**

  - **SGX Instance Management**

    - The contract maintains a registry of trusted SGX instances, each identified by its Ethereum address.
    - SGX instances can be added to the registry through an attestation process or by the contract owner.
    - Instances have a limited lifespan, after which they expire and must be replaced.

  - **Proof Verification**

    - The contract verifies proofs generated by SGX instances to attest to the validity of cross-chain messages.
    - Proofs contain a signature from the old SGX instance and the address of the new SGX instance.
    - The contract checks the validity of the old instance and replaces it with the new instance if the proof is valid.

### packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol:

This `ERC20Airdrop` facilitates the `claiming` of airdropped tokens by eligible users within a specified period and allows them to delegate their `voting power` to a delegatee using a provided merkle proof and `delegation data`, enhancing user interaction and governance functionalities for the Taiko token ecosystem.

### packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol:

`ERC20Airdrop2` manages a Taiko token airdrop for eligible users with a withdrawal window mechanism, allowing users to claim tokens within a specified period and withdraw them gradually over time, enhancing token distribution control and user experience within the Taiko token ecosystem.

### packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol:

`ERC721Airdrop` facilitates the claiming of `ERC721` tokens from a designated vault by eligible users using a merkle proof mechanism, streamlining the distribution process within the Taiko token ecosystem.

### packages/protocol/contracts/team/airdrop/MerkleClaimablex.sol:

`MerkleClaimable` provides functionalities for `managing` a Taiko token airdrop for `eligible users`, including `verification of merkle proofs`, setting configuration parameters, and maintaining claim status, enhancing security and control over the airdrop process within the Taiko token ecosystem.

### packages/protocol/contracts/team/TimelockTokenPool.sol:

- The `TimelockTokenPool` contract serves as a mechanism for managing and `distributing Taiko tokens` to various recipients, including `investors`, `team members`, and grant program grantees.

- It implements a three-state lifecycle for tokens:

  1.  **Allocated**: Tokens are initially allocated to recipients but not yet granted or owned.
  2.  **Granted and Owned**: Tokens are granted to recipients and become their property, subject to an unlocking schedule.
  3.  **Granted, Owned, and Unlocked**: Tokens are fully unlocked and can be withdrawn by the recipient.

- **Key Features**

  - **Grant Management**

    - The contract allows the owner to grant tokens to recipients with customized unlocking schedules.
    - Grants include parameters such as the amount of tokens, the cost per token, the grant start and cliff times, and the grant and unlock periods.

  - **Token Vesting and Withdrawal**

    - Tokens are vested over a specified period, with a portion of the granted tokens becoming available for withdrawal at regular intervals.
    - Recipients can withdraw their unlocked tokens at any time, either to their own address or to a designated recipient.

  - **Cost Token Support**

    - The contract supports the use of a cost token, which recipients must pay in exchange for granted TKO tokens.

- **Additional Notes**

  - The contract maintains separate balances for allocated, granted, and unlocked tokens for each recipient.
  - The contract allows for multiple grants to the same recipient, each with its own unlocking schedule.
  - The contract provides a `getMyGrantSummary` function for recipients to view their current token balances and withdrawal status.

### packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol:

- `AutomataDcapV3Attestation` provides a mechanism for verifying the authenticity and integrity of `SGX quotes` using the `DCAPV3` protocol. It allows users to attest to the validity of an `SGX` quote and obtain a verification result.

- **Key Features:**

  - **Quote Verification:** Verifies the authenticity and integrity of SGX quotes using the DCAP V3 protocol.
  - **TCB Info:** Stores and manages TCB information associated with SGX quotes, including enclave identity, TCB levels, and status.
  - **Trusted Enclave and Signer Management:** Allows the contract owner to specify trusted enclave and signer identities.
  - **Revocation Management:** Provides a mechanism for revoking certificates associated with PCKs and root CAs.

- **Verification Process:**

  - The `verifyAttestation` function is the entry point for verifying an SGX quote. It performs the following steps:

    1. Parses the quote input using the `V3Parser` library.
    2. Verifies the MRENCLAVE and MRSIGNER values in the local enclave report.
    3. Verifies the enclave identity using the `EnclaveIdStruct` data structure.
    4. Parses the quote certificate chain using the `IPEMCertChainLib`.
    5. Checks TCB levels using the `TCBInfoStruct` data structure.
    6. Verifies the certificate chain for the PCK.
    7. Verifies the local attestation signature and QE report signature.

- **Trusted Enclave and Signer Management:**

  - The contract owner can manage trusted enclave and signer identities using the `setMrSigner` and `setMrEnclave` functions. This allows the contract to validate the authenticity of quotes based on trusted identities.

- **TCB Info Management:**

  - The contract owner can configure TCB information using the `configureTcbInfoJson` and `configureQeIdentityJson` functions. This information is used to determine the validity of SGX quotes.

- **Revocation Management:**

  - The contract owner can add or remove revoked certificate serial numbers using the `addRevokedCertSerialNum` and `removeRevokedCertSerialNum` functions. This allows the contract to invalidate quotes based on revoked certificates.

### packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol:

- `PEMCertChainLib` is a library that provides functions for `decoding` and processing `PEM-encoded` certificate chains, extracting information such as issuer names, validity dates, public keys, and SGX-specific information like TCB levels, PCE IDs, and FMS PC values, enhancing the verification and analysis capabilities of certificate chains within the context of `SGX`.

- **Functions**

  - `splitCertificateChain`

    - Splits a PEM-encoded certificate chain into individual certificates.
    - Returns a boolean indicating success and an array of certificate bytes.
    - Removes the "-----BEGIN CERTIFICATE-----" and "-----END CERTIFICATE-----" headers and footers from each certificate.

  - `decodeCert`

    - Decodes a DER-encoded certificate into a structured `ECSha256Certificate` object.
    - Validates the certificate's signature and other fields.
    - Extracts information from PCK certificates, such as the issuer name, common name, and SGX extension data.

  - `_removeHeadersAndFooters`

    - Helper function used internally to remove the headers and footers from a PEM-encoded certificate.
    - Returns a boolean indicating success, the extracted certificate bytes, and the index of the end of the extracted content.

  - `_trimBytes`

    - Helper function used internally to trim excess bytes from a byte array.
    - Ensures that the byte array has the expected length.

  - `_findPckTcbInfo`

    - Helper function used internally to extract PCK-specific information from the SGX extension of a PCK certificate.
    - Returns a boolean indicating success, the `PCESVN`, an array of SVNs, the FMSPC, and the PCeID.

  - `_findTcb`

    - Helper function used internally to extract TCB information from the SGX extension of a PCK certificate.
    - Returns a boolean indicating success, the PCESVN, and an array of cpuSvns.

### packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol:

- This `V3Parser` library provides functionality for `parsing` and validating `SGX` Enclave Quote data in the V3 format.

- **Functions:**

  - **parseInput:** Parses the raw Enclave Quote data and returns a `V3Struct.ParsedV3QuoteStruct` if the quote is valid.
  - **validateParsedInput:** Validates the parsed Enclave Quote data and returns the header, local enclave report, signed quote data, and ECDSA quote V3 auth data.

- **Parsing and Validation Process:**

  - **1. parseInput:**

    - Checks if the quote is long enough (minimum 1020 bytes).
    - Decodes the local auth data size from the quote.
    - Verifies that the quote length matches the local auth data size.
    - Parses the header and verifies its validity (version, attestation key type, TEE type, QE vendor ID).
    - Parses the ECDSA auth data and verifies the certificate type (must be 5: Concatenated PCK Cert Chain).
    - Parses the local enclave report.

  - **2. validateParsedInput:**

    - Verifies the lengths and formats of the enclave report and QE report.
    - Verifies that the certificate chain contains exactly 3 certificates.
    - Verifies the sizes and formats of the ECDSA signatures.
    - Verifies that the QE auth data size matches the actual data size.
    - Calculates the total quote size and ensures it meets the minimum requirement.

- **Additional Notes:**

  - The library uses the `littleEndianDecode` function to decode little-endian encoded values.
  - The library uses the `Base64` library from `solady` to decode the certificate chain data.
  - The library uses the `PEMCertChainLib` library to parse the certificate chain data.

### packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol:

- This `Asn1Decode` library provides functionality for decoding `DER-encoded` ASN.

- **Functions:**

  - **root:** Gets the root node of an ASN.1 structure.
  - **rootOfBitStringAt:** Gets the root node of an ASN.1 structure that is within a bit string value.
  - **rootOfOctetStringAt:** Gets the root node of an ASN.1 structure that is within an octet string value.
  - **nextSiblingOf:** Gets the next sibling node of the current node.
  - **firstChildOf:** Gets the first child node of the current node.
  - **isChildOf:** Checks if one node is a child of another node.
  - **bytesAt:** Extracts the value bytes of a node.
  - **allBytesAt:** Extracts all bytes of a node.
  - **bytes32At:** Extracts the value bytes of a node as a bytes32.
  - **uintAt:** Extracts the uint value of a node.
  - **uintBytesAt:** Extracts the value bytes of a positive integer node.
  - **keccakOfBytesAt:** Calculates the Keccak-256 hash of the value bytes of a node.
  - **keccakOfAllBytesAt:** Calculates the Keccak-256 hash of all bytes of a node.
  - **bitstringAt:** Extracts the value of a bitstring node as bytes.

- **Decoding Process:**

  - The library uses the `NodePtr` library to represent ASN.1 nodes as pointers with three indices:

    - `ixs`: Index of the first byte of the node.
    - `ixf`: Index of the first byte of the node's content.
    - `ixl`: Index of the last byte of the node's content.

### packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol:

- This `BytesUtils` library provides utility functions for working with byte arrays, including `hashing byte ranges`, checking byte equality, reading integers and byte values at specified indices, copying substrings, and decoding base32-encoded data, enhancing the functionality of contracts to handle and manipulate byte data efficiently and securely.

### packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol:

- This library `RsaVerify` implements functions for `verifying RSA` signatures using the PKCSv1.5 padding scheme with SHA256 and SHA1 hashing algorithms. It includes methods to verify signatures with explicit SHA256 or SHA1 hashes, using the RSA public key components (exponent and modulus) and the signature itself. The library ensures that the signature is correctly formatted according to `PKCSv1.5` standards and performs the necessary checks to validate the signature against the provided data and public key parameters, enhancing the security and integrity verification capabilities of smart contracts when dealing with RSA signatures.

- **Functions:**

  - **pkcs1Sha256:** Verifies a PKCSv1.5 SHA-256 signature.
  - **pkcs1Sha256Raw:** Verifies a PKCSv1.5 SHA-256 signature directly from the data.
  - **pkcs1Sha1:** Verifies a PKCSv1.5 SHA-1 signature.
  - **pkcs1Sha1Raw:** Verifies a PKCSv1.5 SHA-1 signature directly from the data.

- **Verification Process:**

  - The verification process involves the following steps:

    1. Decipher the signature using the provided exponent and modulus.
    2. Check the padding and digest algorithm information in the deciphered data.
    3. Compare the calculated digest (SHA-256 or SHA-1) with the provided digest.

- **Input Parameters:**

  - **`_sha256`:** The SHA-256 hash of the data (for `pkcs1Sha256`).
  - **`_data`:** The data to verify (for `pkcs1Sha256Raw` and `pkcs1Sha1Raw`).
  - **`_s`:** The signature.
  - **`_e`:** The exponent.
  - **`_m`:** The modulus.

- **Additional Notes:**

  - The library uses the `SHA1` library for SHA-1 hashing.
  - The library assumes that the provided exponent and modulus are valid.
  - The library does not support verifying signatures with other hashing algorithms.

### packages/protocol/contracts/automata-attestation/utils/SHA1.sol:

This `SHA1` library hashing algorithm using low-level assembly code to efficiently compute the hash value for a given input data, providing a secure and reliable way to generate SHA-1 hashes.

### packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol:

`SigVerifyLib` is a library for verifying signatures using different cryptographic algorithms such as `RS256`, `ES256`, and `RS1`, providing support for verifying signatures on attestation statements and certificates based on the specified algorithms and public keys.

## 2. Multi-proofs

Taiko's multi-proof approach, SGX is used to generate a different type of proof alongside ZK (Zero-Knowledge) proofs. The same code that would be executed on a zkVM (Zero-knowledge Virtual Machine) is run within an SGX enclave. This code functions somewhat like a light execution client, verifying the underlying state transitions in the rollup.

The necessary data from the execution is then signed within the SGX enclave using a standard ECDSA (Elliptic Curve Digital Signature Algorithm) signature, with a private key that is exclusive to the SGX enclave. This signature is then verified within the smart contract on the Ethereum mainnet.

The use of SGX in Taiko's multi-proof approach provides an additional layer of security and diversity. By utilizing different proof systems that all verify the same underlying light client's execution, the risk associated with bugs or vulnerabilities in any single proof system is reduced. This contributes to the overall robustness and reliability of the Taiko rollup.

![Diagram](https://docs.taiko.xyz/_astro/verified.CY0vM6bx_Z22FCQE.webp)

## 3. Bridging

The Taiko protocol enables secure cross-chain messaging through its Ethereum-equivalence design and the use of Merkle proofs. Taiko stores block hashes of each chain in two smart contracts: TaikoL1 and TaikoL2. TaikoL1 is deployed on Ethereum and stores a mapping of blockNumber to blockHash (l2Hashes), while TaikoL2 is deployed on Taiko and stores a similar mapping (l1Hashes).

Merkle trees are used to verify values exist on the other chain. These trees allow a lot of data to be fingerprinted with a single hash, known as the Merkle root. Verifiers can confirm that some value exists within this large data structure without needing access to the entire Merkle tree. They just need the Merkle root, the value, and a list of intermediate sibling hashes.

Taiko's signal service is a smart contract available on both L1 and L2, which uses Merkle proofs to provide a service for secure cross-chain messaging. It allows you to store signals and check if a signal was sent from an address. The function `isSignalReceived` can prove on either chain that you sent a signal to the Signal Service on the other chain.

The bridge in Taiko is a set of smart contracts and a frontend web app that allow you to send testnet ETH and ERC-20, ERC-1155, and ERC-721 tokens between Ethereum and Taiko. The user sends their funds to the Bridge contract, which locks the Ether and stores a message by calling `sendSignal(message)` on the SignalService contract. The user receives Ether on the destination chain if they (or another) provide a valid Merkle proof that the message was received on the source chain.

![Bridge](https://docs.taiko.xyz/_astro/bridging-send-message.excalidraw.B7z4_iJn_HyBVw.webp)

For ERC-20 (or ERC-721, ERC-1155) bridging, a new BridgedERC20 contract needs to be deployed on the destination chain. The vault contract (via the Bridge) sends a message to the Signal Service, which contains metadata related to the bridge request and the calldata for the `receiveToken` method. This process mints ERC-20 (or ERC-721, ERC-1155) on the BridgedERC20 contract to the recipient's address on the destination chain.

![Bridge](https://docs.taiko.xyz/_astro/bridging-process-message.excalidraw.DfHWyAz9_20jAnU.webp)

## 4. Functional Tests

### Bridge:

- **Users can send the message to send the native token.**
- **Users can retry the retriable message.**
- **Users can recall the failed message.**
- **Should revert while processing the message on the chain diﬀerent than**
- **message.destChainId.**
- **Should revert while retrying the message on the chain diﬀerent than**
- **message.destChainId.**
- **Should revert while recalling the message on the chain diﬀerent than**
- **message.srcChainId.**
- **Should revert if signal veriﬁcation fails on signal service.**
- **processing, retrying and recalling messages updates the status of messages.**
- **Should not be able to execute the transaction on Bridge.**
- **Should not be able to execute the transaction on signal service.**

### ERC20Vault:

- **Should be able to send canonical tokens on other chain.**
- **Should be able to receive the bridge token on other chain.**
- **Should be able to get the recalled canonical tokens back.**
- **Should be able to send bridge tokens on other chain.**
- **Should be able to receive the canonical tokens on other chain.**
- **Should be able to get the recalled bridged tokens back.**
- **Owner should be able to change the bridge token.**

### ERC721Vault:

- **Should be able to send canonical tokens on other chain.**
- **Should be able to receive the bridge token on other chain.**
- **Should be able to get the recalled canonical tokens back.**
- **Should be able to send bridge tokens on other chain.**
- **Should be able to receive the canonical tokens on other chain.**
- **Should be able to get the recalled bridged tokens back.**

### ERC1155Vault:

- **Should be able to send canonical tokens on another chain.**
- **Should be able to receive the bridge token on other chain.**
- **Should be able to get the recalled canonical tokens back.**
- **Should be able to send bridge tokens on other chain.**
- **Should be able to receive the canonical tokens on other chain.**
- **Should be able to get the recalled bridged tokens back.**

## Systemic Risks, Centralization Risks, Technical Risks & Integration Risks

### Note: **I analyze every contract in scope and check for systemic risk, admin or centralization risks, technical risk and integration risk.**

### packages/protocol/contracts/common/AddressManager.sol

1. **Systemic Risks**

   - `Not obvious Systemic risk`

2. **Centralization Risks**

   - The AddressManager contract has an `onlyOwner` modifier on the `setAddress` function, which means only the owner can change the addresses. This centralizes control and could lead to censorship or single point of failure. If the owner's account is compromised or the owner becomes malicious, they could change the addresses to malicious ones.

3. **Technical Risks**

   - The `setAddress` function does not have a check to ensure that the new address is a valid contract address. This could potentially lead to the setting of an incorrect or malicious address.

4. **Integration Risks**

   - `Not obvious Systemic risk`

### packages/protocol/contracts/common/AddressResolver.sol

1. **Systemic Risks**

   - Use of `onlyFromNamed` Modifier: The contract uses the `onlyFromNamed` modifier to restrict certain functions to be called only by a specific address. However, the modifier does not check if the `_name` parameter is valid or not. If an attacker can find a valid `_name` that has not been assigned to any address, they could potentially bypass the modifier and call the restricted function.

   - Use of `_allowZeroAddress` Parameter: The contract has a `_allowZeroAddress` parameter that allows zero addresses to be returned in certain cases. However, the contract does not check if the returned address is a contract address or an externally owned account. If the returned address is an externally owned account, it could potentially lead to issues with the contract's functionality.

2. **Centralization Risks**

   - Single point of failure: The contract has a single addressManager variable that stores the address of the AddressManager contract. If this address is compromised or becomes unavailable, the AddressResolver contract will not be able to function properly.

3. **Technical Risks**

   - `Not obvious Technical risk`

4. **Integration Risks**

   - `Not obvious Integration risk`

### packages/protocol/contracts/common/EssentialContract.sol

1.  **Systemic Risks**

    - `Incorrect Initialization`: The contract has an initialization function `__Essential_init` that takes an `_addressManager` parameter. If this parameter is not set correctly during deployment, it could lead to unintended behavior or even render some functions unusable.

      ```solidity
         function __Essential_init(
            address _owner,
            address _addressManager
         )
            internal
            virtual
            onlyInitializing
         {
            __Essential_init(_owner);

            if (_addressManager == address(0)) revert ZERO_ADDR_MANAGER();
            __AddressResolver_init(_addressManager);
         }
      ```

    - `Re-entrancy Guard Inconsistency`: The contract uses a `custom re-entrancy` guard with different storage mechanisms based on the chain ID. This could lead to inconsistencies in re-entrancy protection if the contract is interacted with across different chains or if the chain ID is not correctly identified.

      ```solidity
       function _loadReentryLock() internal view virtual returns (uint8 reentry_) {
          if (block.chainid == 1) {
                assembly {
                   reentry_ := tload(_REENTRY_SLOT)
                }
          } else {
                reentry_ = __reentry;
          }
       }

       function _inNonReentrant() internal view returns (bool) {
          return _loadReentryLock() == _TRUE;
       }
      ```

2.  **Centralization Risks**

    - The `onlyFromOwnerOrNamed` modifier restricts function calls to either the contract owner or a resolved address with a specific name. This centralization of control could lead to censorship or single point of failure issues.

      ```solidity
         modifier onlyFromOwnerOrNamed(bytes32 _name) {
            if (msg.sender != owner() && msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();
            _;
         }
      ```

    - The `pause` and `unpause` functions are controlled by the contract owner, which could lead to centralization risks if the owner decides to pause the contract indefinitely or maliciously.

3.  **Technical Risks**

    - The `_storeReentryLock` and `_loadReentryLock` functions use different storage mechanisms based on the chain ID. This could lead to inconsistencies or bugs if the chain ID is not properly handled or if the contract is deployed on an unsupported chain.

    - The contract uses a custom error code (`INVALID_PAUSE_STATUS`) for both paused and unpaused states, which might lead to confusion or misinterpretation of the contract state.

4.  **Integration Risks**

    - Inheritance Complexity: The contract inherits from multiple contracts (`UUPSUpgradeable`, `Ownable2StepUpgradeable`, and `AddressResolver`), which could increase its complexity and make it harder to understand and maintain.

### packages/protocol/contracts/libs/LibAddress.sol

1. **Systemic Risks**

   - `Unbounded Gas Usage`: In the `sendEther` function without the `_gasLimit` parameter, the `gasleft()` function is used to determine the gas limit. This could lead to unbounded gas usage if the contract's gas consumption is not properly managed, potentially causing transaction reverts or out-of-gas errors.

   - Magic Value Dependency: The `isValidSignature` function relies on the `_EIP1271_MAGICVALUE` constant when checking for EIP-1271 signatures. If this magic value changes in the future or if there are compatibility issues with contracts implementing EIP-1271, it could lead to incorrect signature validation.

   - `EIP-1271 Signature Validation`: The `isValidSignature` function assumes that a contract implementing EIP-1271 will return the magic value (`_EIP1271_MAGICVALUE`) when the signature is valid. If a contract implements EIP-1271 but does not follow this convention, it could lead to incorrect signature validation.

     ```solidity
        function isValidSignature(
           address _addr,
           bytes32 _hash,
           bytes memory _sig
        )
           internal
           view
           returns (bool)
        {
           if (Address.isContract(_addr)) {
                 return IERC1271(_addr).isValidSignature(_hash, _sig) == _EIP1271_MAGICVALUE;
           } else {
                 return ECDSA.recover(_hash, _sig) == _addr;
           }
        }
     ```

   - `False Positive EOA Detection`: The `isSenderEOA` function checks if the transaction sender is an externally owned account (EOA) by comparing `msg.sender` and `tx.origin`. However, this check might not be reliable in some cases, such as when using meta-transactions or certain proxy contracts, leading to false positives.

2. **Centralization Risks**

   - `Not obvious Centralization risk`

3. **Technical Risks**

   - In the `sendEther` function, the gas limit is passed as a parameter, which could lead to potential issues if the gas limit is not correctly estimated or if it is manipulated by an attacker.

4. **Integration Risks**

   - The `isValidSignature` function checks for both ECDSA and EIP-1271 signatures. If the contracts being interacted with do not correctly implement these signatures or have compatibility issues, it could lead to signature validation issues or other integration problems.

   - `Unused Import`: The library imports the `IERC165` interface, but it is not used anywhere in the code. This could lead to confusion during code audits or maintenance and might indicate that some functionality is incomplete or not properly implemented.

### packages/protocol/contracts/libs/LibTrieProof.sol

1.  **Systemic Risks**

    - `Unchecked RLP Item Length`: The contract does not check the length of the `RLPReader.RLPItem[] memory accountState` array. If the RLP-encoded account data does not contain the expected number of fields, it could lead to out-of-bounds access in the following line:

      ```solidity
         storageRoot_ = bytes32(RLPReader.readBytes(accountState[_ACCOUNT_FIELD_INDEX_STORAGE_HASH]));
      ```

    - Use of `abi.encodePacked`: The LibTrieProof contract uses `abi.encodePacked` to encode the address when fetching the account data from the Merkle tree:

      ```solidity
      bytes memory rlpAccount = SecureMerkleTrie.get(abi.encodePacked(_addr), _accountProof, _rootHash);
      ```

    Using `abi.encodePacked` can potentially lead to issues when encoding addresses, as it does not include padding. This could result in incorrect data being fetched from the Merkle tree if the encoding does not match the encoding used when the data was stored. It would be safer to use `abi.encode` instead, which includes padding and is less prone to errors.

2.  **Centralization Risks**

- `Not obvious Centralization risk`

3. **Technical Risks**

   - The contract does not check the length of the `_storageProof` parameter. If an empty or incomplete proof is provided, it could cause unexpected behavior.

   - The contract does not validate the `_addr` parameter. If an invalid address is provided, it could lead to issues.

4. **Integration Risks**

   - The contract is a library and is meant to be used by other contracts. Improper integration or usage of this library could lead
     to issues. For example, if a contract using this library does not properly handle the exceptions thrown by the `verifyMerkleProof` function, it could lead to unintended behavior. Additionally, the contract assumes that the provided proofs are generated correctly. If the system generating these proofs has issues, it could impact the functionality of this contract.

### packages/protocol/contracts/L1/gov/TaikoGovernor.sol

1. **Systemic Risks**

   - `Fixed Voting Delay and Voting Period`: The `votingDelay()` and `votingPeriod()` functions return hardcoded values of 1 day and 1 week, respectively. These fixed values could lead to risks if the governance process needs to be adjusted in the future. For example, a longer voting period might be required for certain proposals, or a shorter voting delay might be desired to expedite the voting process. The contract would need to be updated to accommodate any such changes.

   - `Fixed Proposal Threshold`: The `proposalThreshold()` function returns a hardcoded value of 0.01% of the total Taiko Token supply. if the governance process needs to be adjusted in the future. For example, if the Taiko Token supply changes or if the community decides to lower or raise the proposal threshold, the contract would need to be updated to accommodate these changes.

2. **Centralization Risks**

   - The contract uses a `timelock controller`, which could pose a centralization risk if only a limited number of addresses have the ability to execute proposals after the timelock has passed.

3. **Technical Risks**

   - The contract uses the `ether` unit to calculate the `proposalThreshold()`. While this is not an issue by itself, it could lead to confusion or errors if someone misunderstands the unit or if the unit is changed in the future. It would be clearer to use the `wei` unit and specify the exact number of wei required for the proposal threshold.

     - The contract does not validate the input parameters for some functions, such as `propose()` and `_execute()`. If invalid parameters are provided, it could cause unexpected behavior or revert the function call.

4. **Integration Risks**

   - `Not obvious Integration risk`

### packages/protocol/contracts/L1/hooks/AssignmentHook.sol

1.  **Systemic Risks**

    - `Incorrect signature verification`: The contract verifies the signature of the assigned prover in the `onBlockProposed` function. If the signature verification logic is incorrect, it can lead to unauthorized provers being assigned.

    - `fee calculation`: The contract calculates the prover fee in the `_getProverFee` function. If the fee calculation logic is incorrect, it can lead to underpayment or overpayment of fees.

          ```solidity
             function _getProverFee(
             TaikoData.TierFee[] memory _tierFees,
             uint16 _tierId
          )
             private
             pure
             returns (uint256)
          {
             for (uint256 i; i < _tierFees.length; ++i) {
                   if (_tierFees[i].tier == _tierId) return _tierFees[i].fee;
             }
             revert HOOK_TIER_NOT_FOUND();
          }
          ```

2.  **Centralization Risks**

    - `Not obvious Centralization risk`

3.  **Technical Risks**

    - `Time dependency`: The contract uses `block.timestamp` to check the expiry of the assignment. However, miners can manipulate the timestamp to some extent, which may lead to potential vulnerabilities.

    - `Unchecked-send`: The contract uses `.sendEther()` to transfer Ether, which can fail silently if the call stack depth is above 1024, potentially leading to loss of funds.

4.  **Integration Risks**

    - `Compatibility issues`: If the interfaces of the external contracts (`TaikoL1`, `IERC20`, `AddressManager`) change, this contract may no longer work as expected.

### packages/protocol/contracts/L1/libs/LibDepositing.sol

1.  **Systemic Risks**

    - `Incorrect calculation of pending deposits`: The contract calculates the number of pending deposits as `_state.slotA.numEthDeposits - _state.slotA.nextEthDepositToProcess`. If the `nextEthDepositToProcess` variable is not updated correctly, it can lead to an incorrect calculation of pending deposits, which can cause deposits to be skipped or processed multiple times.

      ```solidity
             return _amount >= _config.ethDepositMinAmount && _amount <= _config.ethDepositMaxAmount
             && _state.slotA.numEthDeposits - _state.slotA.nextEthDepositToProcess
                < _config.ethDepositRingBufferSize - 1;
      ```

    - `deposit slot calculation`: The contract uses the `slot` variable to store the position of the deposit in the ring buffer. If the slot calculation logic is incorrect, it can lead to deposits being stored in the wrong position in the ring buffer, which can cause deposits to be overwritten or lost.

    - `handling of deposit Ringbuffer`: The contract uses a ring buffer to store pending deposits. If the ring buffer handling logic is incorrect, it can lead to deposits being overwritten or lost, especially in cases where the ring buffer is full.

2.  **Centralization Risks**

    - The `_recipient` parameter is used to determine the recipient address for deposits. If `_recipient` is not specified `address(0)`, the default recipient becomes msg.sender. This design limits flexibility and decentralization since all deposits without a specified recipient will go to msg.sender. It doesn't allow for dynamic selection of recipients based on conditions or external factors.

3.  **Technical Risks**

    - `Unchecked-send`: The contract uses `.sendEther()` to transfer Ether, which can fail silently if the call stack depth is above 1024, potentially leading to loss of funds.

4.  **Integration Risks**

    - `data feeding`: The contract relies on external data provided by the address resolver contract and the configuration contract. If the data is incorrect or manipulated, the contract's functionality can be affected.

### packages/protocol/contracts/L1/libs/LibProposing.sol

1. **Systemic Risks**

   - `Liveness Bond Not Received`: The contract assumes that the liveness bond will be received after the hooks are executed. If this does not happen, the contract will revert, potentially causing loss of funds.

1. **Centralization Risks**

   - Centralized Control: The contract has a centralized point of control in the form of the address resolver. The resolver can change the addresses of the `Taiko token`, `tier provider`, and `proposer`, which could lead to centralization risks.

1. **Technical Risks**

   - `Unchecked-send`: The contract uses the low-level `.sendEther()` function, which can fail silently and cause unpredictable behavior.

   - Use of `block.timestamp`: The contract uses `block.timestamp` for various purposes, which can be manipulated by miners to some extent.

1. **Integration Risks**

   - `Incorrect Assumptions`: The contract assumes that the external contracts it interacts with will behave as expected. If these contracts behave unexpectedly, it could lead to integration issues.

### packages/protocol/contracts/L1/libs/LibProving.sol

1. **Systemic Risks**

   - `Assigned Prover Not Allowed`: The `LibProving` contract assumes that the assigned prover will not submit a proof for a block. If this is not the case, the contract will revert.

- Missing Verifier: The contract assumes that a verifier will always be present for a given tier. If this is not the case, the contract will revert, potentially causing loss of funds.

  ```solidity
          bool inProvingWindow = uint256(_ts.timestamp).max(_state.slotB.lastUnpausedAt)
           + _tier.provingWindow * 60 >= block.timestamp;
       bool isAssignedPover = msg.sender == _blk.assignedProver;

       // The assigned prover can only submit the very first transition.
       if (_tid == 1 && _ts.tier == 0 && inProvingWindow) {
           if (!isAssignedPover) revert L1_NOT_ASSIGNED_PROVER();
       } else {
           // Disallow the same address to prove the block so that we can detect that the
           // assigned prover should not receive his liveness bond back
           if (isAssignedPover) revert L1_ASSIGNED_PROVER_NOT_ALLOWED();
       }
  ```

2. **Centralization Risks**

   - `Centralized Control`: The contract has a centralized point of control in the form of the address resolver. The resolver can change the addresses of the Taiko token, tier provider, and verifier contracts, which could lead to centralization risks.

3. **Technical Risks**

   - Use of `transferFrom`: The contract uses the `transferFrom` function to transfer tokens from the message sender's account, which could potentially fail if the sender does not have enough tokens or has not approved the contract to transfer the tokens.

### packages/protocol/contracts/L1/libs/LibUtils.sol

1. **Systemic Risks**

   - `Unexpected Transition ID`: The `LibUtils` contract assumes that transition IDs will be within a certain range. If a transition ID is unexpected, the contract will revert with the `L1_UNEXPECTED_TRANSITION_ID` error. This could potentially be exploited if an attacker can manipulate the transition IDs in a way that causes the contract to revert for all users.

2. **Centralization Risks**

   - `Not obvious Centralization risk`

3. **Technical Risks**

   - `Invalid Input`: The contract assumes that the input parameters are valid and does not perform extensive input validation. If invalid input is provided, the contract may revert or produce incorrect results.

4. **Integration Risks**

   - Incompatible Data Structures: If the data structures in the `TaikoData` contract are changed, this contract may need to be updated as well to ensure compatibility.

     - Dependency Changes: If the `TaikoData` contract is updated or replaced, this contract may need to be updated as well to maintain compatibility and functionality.

### packages/protocol/contracts/L1/libs/LibVerifying.sol

1. **Systemic Risks**

   - The `init` function can only be called once during contract deployment, and it sets critical state variables like `genesisBlockHash`, `genesisHeight`, and `genesisTimestamp`. If these values are incorrectly set during deployment, the Taiko protocol may not function as intended.

   - The `_isConfigValid` function checks for valid configuration values. If the function logic does not cover all possible edge cases, the contract may be initialized with invalid configuration values.

     ```solidity
        function _isConfigValid(TaikoData.Config memory _config) private view returns (bool) {
        if (
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

        return true;
     }
     ```

2. **Centralization Risks**

   - The `_resolver.resolve("tier_provider", false)` function call may return a centralized tier provider, which could lead to centralization risks if the provider has too much control over the system.

3. **Technical Risks**

   - The `verifyBlocks` function has a while loop that may lead to gas limit issues if the loop iterates too many times.

     ```solidity
                 while (blockId < b.numBlocks && numBlocksVerified < _maxBlocksToVerify) {
                    slot = blockId % _config.blockRingBufferSize;

                    blk = _state.blocks[slot];
                    if (blk.blockId != blockId) revert L1_BLOCK_MISMATCH();

                    tid = LibUtils.getTransitionId(_state, blk, slot, blockHash);
                    // When `tid` is 0, it indicates that there is no proven
                    // transition with its parentHash equal to the blockHash of the
                    // most recently verified block.
                    if (tid == 0) break;

     ```

   - The contract uses the `transfer` function from the IERC20 contract, which may fail if the recipient contract does not properly handle ERC20 token transfers.

     ```solidity
        tko.transfer(ts.prover, bondToReturn);
     ```

4. **Integration Risks**

   - The contract depends on the correct functioning of the `AddressResolver` contract for resolving contract addresses like the tier provider, signal service, and Taiko token. If the AddressResolver contract is not properly configured or has issues, the Taiko protocol may be affected.

### protocol/contracts/L1/provers/Guardians.sol

1. **Systemic Risks**

   - The contract uses a mapping `guardianIds` to store the index of each guardian in the `guardians` array. This mapping is not updated when a new set of guardians is set using the `setGuardians` function. This could potentially lead to inconsistencies or errors if the new set of guardians includes addresses that were also in the old set.

     ```solidity
        mapping(address guardian => uint256 id) public guardianIds;
     ```

   - The contract uses a constant (`MIN_NUM_GUARDIANS`) to enforce a minimum number of guardians. This constant is set to 5, which could potentially be too low for some use cases, leading to a lack of security or robustness. On the other hand, it could potentially be too high for other use cases, leading to unnecessary complexity or inefficiency.

2. **Centralization Risks**

   - The `setGuardians` function is only callable by the owner of the contract (as indicated by the `onlyOwner` modifier). This means that the power to change the set of guardians is centralized to a single entity, which could potentially lead to censorship or manipulation.

   - The contract does not provide a mechanism for adding or removing guardians one at a time. The `setGuardians` function requires a completely new set of guardians to be provided each time it is called, which could lead to centralization if the owner of the contract decides to set a small or biased set of guardians.

3. **Technical Risks**

   - The `setGuardians` function does not check if the new set of guardians contains the address of the contract itself. This could potentially allow the owner to add the contract as a guardian, which could lead to unintended behavior or vulnerabilities.

   - The `approve` function does not check if the given hash has already been approved. This could potentially allow a guardian to approve the same hash multiple times, which could lead to unintended behavior or vulnerabilities.

4. **Integration Risks**

   - The contract does not validate the input to the `approve` function. If this function is called with a hash that was not generated by the expected process, it could lead to vulnerabilities.

### packages/protocol/contracts/L1/TaikoL1.sol

1. **Systemic Risks**

   - Block proposing and proving: The contract's functionality of `LibProposing` and `proving blocks` could be exploited if not properly secured, leading to risks like block manipulation or false proofs.

   - `Pausing functionality`: The contract allows pausing of the proving process. If misused, it could lead to service disruption or other attacks.

   - `Economic model risks`: The contract involves staking Taiko tokens and Ether deposits. If the economic model is not well-designed, it could lead to systemic risks like token devaluation or economic attacks.

2. **Centralization Risks**

   - `Admin control`: The contract has an `owner/admin` who can pause the proving process. This centralizes control and could potentially be misused.

3. **Technical Risks**

   - `Not obvious Technical risk`

4. **Integration Risks**

   - `Compatibility issues`: The contract could face integration issues with other contracts or systems it interacts with, especially during upgrades or changes in those systems.

### packages/protocol/contracts/L1/TaikoToken.sol

1. **Systemic Risks**

   - `Token Minting`: The contract mints a fixed amount of 1 billion tokens at initialization. If there's a need for more tokens in the future, a new contract would have to be deployed, which could lead to compatibility issues and complexities.

   - `Token Transfer Restrictions`: The contract does not seem to have any token transfer restrictions or whitelisting. If such restrictions are needed in the future, they would have to be implemented in a new contract or upgrade.

   - `Token Voting`: The contract uses `ERC20VotesUpgradeable`, which means the token is used for voting. If the voting process is not properly secured and managed, it could lead to `governance attacks` or `manipulation`.

   - `Token Value Dependence`: The value of the `TaikoToken` is dependent on the overall performance and adoption of the Taiko protocol. Any issues or negative perceptions about the protocol could lead to a decrease in the token's value.

   - `Token Economic Model`: The token economic model, including `minting`, `burning`, and `distribution policies`, could lead to systemic risks if not properly designed and balanced.

2. **Centralization Risks**

   - `Owner Control`: The contract owner has the power to burn tokens, which could lead to centralization risks if misused.

   - `Snapshotter Role`: The contract allows a named role `snapshooter` to create token snapshots. If this role is controlled by a single entity, it could lead to centralization risks.

3. **Technical Risks**

   - `Not obvious Technical risk`

4. **Integration Risks**

   - `Compatibility Issues`: The contract could face integration issues with other contracts or systems it interacts with, especially during upgrades or changes in those systems.

### packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol

1. **Systemic Risks**

   - `Bonding Requirements`: The contract specifies bonding requirements for different tiers. If these requirements are not properly balanced, they could lead to economic attacks or token devaluation.

     ```solidity
             if (_tierId == LibTiers.TIER_OPTIMISTIC) {
                 return ITierProvider.Tier({
                     verifierName: "tier_optimistic",
                     validityBond: 250 ether, // TKO
                     contestBond: 500 ether, // TKO
                     cooldownWindow: 1440, //24 hours
                     provingWindow: 120, // 2 hours
                     maxBlocksToVerifyPerProof: 16
                 });
             }

             if (_tierId == LibTiers.TIER_GUARDIAN) {
                 return ITierProvider.Tier({
                     verifierName: "tier_guardian",
                     validityBond: 0, // must be 0 for top tier
                     contestBond: 0, // must be 0 for top tier
                     cooldownWindow: 60, //1 hours
                     provingWindow: 2880, // 48 hours
                     maxBlocksToVerifyPerProof: 16
                 });
     ```

   - `Proving Window`: The contract specifies a proving window for each tier. If the proving window is too short, it could lead to liveness issues. If it's too long, it could lead to delayed finality and increased risk of chain reorgs.

   - `Hardcoded Values`: The contract has hardcoded values for tier parameters. If these values need to be changed in the future, a new contract would have to be deployed, which could lead to compatibility issues and complexities.

2. **Centralization Risks**

   - `Owner Control`: The contract has an owner who can potentially control or influence the contract's behavior, leading to centralization risks.

3. **Technical Risks**

   - `Limited Tiers`: The contract only supports two tiers. If more tiers are needed in the future, the contract would have to be upgraded or replaced.

   - `Max Blocks to Verify Per Proof`: The contract specifies a `maximum number` of blocks that can be verified per proof for each tier. If this number is not properly set, it could lead to liveness issues or `proof manipulation`.

4. **Integration Risks**

   - `Not obvious Integration risk`

### packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol

1. **Systemic Risks**

   - The `getMinTier` function uses a random number (`_rand`) to determine the minimum tier. If the source of this random number is not truly random or can be manipulated, this could lead to potential security risks or unfair distribution of tiers.

     ```solidity
         function getMinTier(uint256 _rand) public pure override returns (uint16) {
         // 0.1% require SGX + ZKVM; all others require SGX
         if (_rand % 1000 == 0) return LibTiers.TIER_SGX_ZKVM;
         else return LibTiers.TIER_SGX;
     }
     ```

   - The `revert TIER_NOT_FOUND()` statement in the `getTier` function could potentially be used to perform a Denial of Service attack if an attacker can repeatedly trigger this revert, causing the contract to consume all available gas.

2. **Centralization Risks**

   - The `tier information is hardcoded` in the contract, which means that any changes to the `tier parameters` would require a new deployment of the contract. This could lead to centralization, as only the person or entity with the ability to deploy new contracts can make these changes.

3. **Technical Risks**

   - `Not obvious Technical risk`

4. **Integration Risks**

   - The contract uses the `initializer` modifier for the `init` function, which might not be compatible with all contract deployment frameworks or libraries. This could lead to integration issues when deploying the contract.

### packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol

1. **Systemic Risks:**

   - The contract does not have any mechanisms to `update` the tier parameters. If these `parameters` need to be changed in the future, a new contract would have to be deployed.

2. **Centralization Risks:**

   - The contract is `initialized` with an owner, which could potentially have centralization risks if the owner has special privileges not shown in this contract. The owner could potentially manipulate the contract to their advantage.

3. **Technical Risks:**

   - The `getTier` function uses a series of if statements to return the tier. If a new tier is added and not accounted for in this function, it could lead to a `TIER_NOT_FOUND` revert. This could be mitigated by using a more scalable data structure or function.

   - The `getMinTier` function uses a simple modulo operation to determine the minimum tier. This could lead to predictable results and potential manipulation if the source of randomness (`_rand`) is not truly random.

4. **Integration Risks:**

   - The contract assumes that the `_rand` parameter in the `getMinTier` function is a reliable source of randomness. If this is not the case, the function may not behave as expected.

   - The contract uses `ether` values for bonds. If the contract interacts with other contracts that do not use the same ether values, it could lead to inconsistencies or errors.

### packages/protocol/contracts/L2/Lib1559Math.sol

1. **Systemic Risks:**

   - The `_ethQty` function uses the `exp` function from `LibFixedPointMath`. This function is known to have precision loss for large inputs. This could potentially lead to inaccurate results in certain situations.

     ```solidity
         function _ethQty(
         uint256 _gasExcess,
         uint256 _adjustmentFactor
     )
         private
         pure
         returns (uint256)
     {
         uint256 input = _gasExcess * LibFixedPointMath.SCALING_FACTOR / _adjustmentFactor;
         if (input > LibFixedPointMath.MAX_EXP_INPUT) {
             input = LibFixedPointMath.MAX_EXP_INPUT;
         }
         return uint256(LibFixedPointMath.exp(int256(input)));
     }
     ```

2. **Centralization Risks:**

   - `Not obvious Centralization risk`

3. **Technical Risks:**

   - The `basefee` function divides by `_adjustmentFactor`. If this value is 0, the function will revert. However, if this value is very small, it could potentially lead to a large result that could cause issues in other parts of the system.

     ```solidity
         function basefee(
             uint256 _gasExcess,
             uint256 _adjustmentFactor
         )
             internal
             pure
             returns (uint256)
         {
             if (_adjustmentFactor == 0) {
                 revert EIP1559_INVALID_PARAMS();
             }

             return _ethQty(_gasExcess, _adjustmentFactor) / LibFixedPointMath.SCALING_FACTOR
                 / _adjustmentFactor;
         }
     ```

4. **Integration Risks:**

   - The contract assumes that the `_gasExcess` and `_adjustmentFactor` parameters are accurate and properly scaled. If these values are not correct, the functions may not behave as expected.

   - The contract uses the `LibFixedPointMath.SCALING_FACTOR` constant for calculations. If other contracts or systems that interact with this contract use a different scaling factor, it could lead to inconsistencies or errors.

### packages/protocol/contracts/L2/TaikoL2.sol

1. **Systemic Risks:**

   - The contract uses the `block.chainid` to get the current chain ID. If this value is not properly validated, it could potentially lead to issues.

   - The contract uses the `skipFeeCheck` function to determine whether to check the base fee. If this function is overridden in a malicious way, it could potentially lead to issues.

     ```solidity
             if (!skipFeeCheck() && block.basefee != basefee) {
             revert L2_BASEFEE_MISMATCH();
         }
     ```

   - The contract uses the `blockhash` function to get the hash of a block, which could potentially be manipulated by miners.

     ```solidity
         function getBlockHash(uint64 _blockId) public view returns (bytes32) {
             if (_blockId >= block.number) return 0;
             if (_blockId + 256 >= block.number) return blockhash(_blockId);
             return l2Hashes[_blockId];
         }
     ```

2. **Centralization Risks:**

   - The contract has an owner, who has special privileges such as the ability to withdraw tokens or Ether from the contract. This could potentially lead to centralization risks if the owner misuses their power.

   - The `anchor` function can only be called by the `GOLDEN_TOUCH_ADDRESS`, which could potentially lead to centralization risks if this address is controlled by a single entity.

3. **Technical Risks:**

   - The `getConfig` function hardcodes the `gasTargetPerL1Block` and `basefeeAdjustmentQuotient` values. If these values need to be changed in the future, the contract would need to be updated.

   - The `_calc1559BaseFee` function uses the `basefee` function from `Lib1559Math`, which could potentially lead to issues if the input parameters are not properly validated.

4. **Integration Risks:**

   - The contract uses the `sendEther` and `safeTransfer` functions to transfer Ether and tokens, respectively. If these functions are not properly integrated with the rest of the system, it could lead to issues.

     ```solidity
             if (_token == address(0)) {
                 _to.sendEther(address(this).balance);
             } else {
                 IERC20(_token).safeTransfer(_to, IERC20(_token).balanceOf(address(this)));
             }
     ```

### packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

1. **Systemic Risks:**

   - The contract uses the `onlyOwner` modifier for the `setConfigAndExcess` function. If the owner's address is compromised, an attacker could potentially change the EIP-1559 configuration and gas excess.

   - The `setConfigAndExcess` function allows the owner to change the EIP-1559 configuration and gas excess at any time. If these values are changed frequently or unexpectedly, it could potentially disrupt the functioning of the system.

   - The contract does not have any mechanism to prevent the owner from setting an unreasonably high or low gas excess value, which could potentially lead to issues.

2. **Centralization Risks:**

   - The contract has an owner, who has the ability to change the EIP-1559 configuration and gas excess using the `setConfigAndExcess` function. This could potentially lead to centralization risks if the owner misuses their power.

3. **Technical Risks:**

   - The `setConfigAndExcess` function checks if the `gasTargetPerL1Block` and `basefeeAdjustmentQuotient` values are non-zero. However, it does not validate the values beyond this. If the values are not properly validated, it could potentially lead to issues.

4. **Integration Risks:**

   - The contract assumes that the `_newConfig` parameter passed to the `setConfigAndExcess` function is accurate. If this value is not correct, the function may not behave as expected.

### packages/protocol/contracts/signal/SignalService.sol

1. **Systemic Risks**

   - The contract uses a `validSender` modifier for several functions. However, this modifier only checks if the sender is not a zero address. It does not check if the sender is authorized, which may allow unauthorized addresses to call these functions.

     ```solidity
         modifier validSender(address _app) {
         if (_app == address(0)) revert SS_INVALID_SENDER();
         _;
     }
     ```

   - The contract uses the `assembly` keyword in the `_sendSignal` and `_loadSignalValue` functions to interact with storage. If the assembly code is not written correctly, it may lead to storage collisions or other unexpected behavior.

2. **Centralization Risks**

   - The contract has an `onlyOwner` modifier for the `authorize` function. This means that only the contract owner can authorize or deauthorize addresses. This centralizes control and may lead to censorship or single point of failure.

     ```solidity
         function authorize(address _addr, bool _authorize) external onlyOwner {
         if (isAuthorized[_addr] == _authorize) revert SS_INVALID_STATE();
         isAuthorized[_addr] = _authorize;
         emit Authorized(_addr, _authorize);
     }
     ```

   - The contract uses a mapping `isAuthorized` to store authorized addresses. If the contract owner's private key is compromised, an attacker can authorize malicious addresses.

     ```solidity
         mapping(address addr => bool authorized) public isAuthorized;
     ```

3. **Technical Risks**

   - The `sendSignal` function stores the signal value in storage without any validation checks. If a malicious actor sends a large amount of data as a signal, it could potentially lead to a denial of service attack.

     ```solidity
         function sendSignal(bytes32 _signal) external returns (bytes32) {
         return _sendSignal(msg.sender, _signal, _signal);
     }
     ```

   - The `proveSignalReceived` function decodes `hopProofs` from the provided proof without any length check. If a malicious actor provides a large proof, it could potentially lead to a denial of service attack.

     ```solidity
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

             if (value == 0 || value != _loadSignalValue(address(this), signal)) {
                 revert SS_SIGNAL_NOT_FOUND();
             }
         }
     ```

4. **Integration Risks**

   - `Not obvious Integration risk`

### packages/protocol/contracts/bridge/Bridge.sol

1. **Systemic Risks**

   - The contract uses a `sameChain` modifier for several functions. However, this modifier only checks if the provided chain ID is the same as the current chain ID. It does not check if the chain is enabled, which may allow messages to be processed on a disabled chain.

     ```solidity
         modifier sameChain(uint64 _chainId) {
         if (_chainId != block.chainid) revert B_INVALID_CHAINID();
         _;
      }
     ```

   - `Lack of Input Validation`: The `suspendMessages()` function does not validate the input array length, potentially allowing an attacker to cause a Denial of Service attack by providing an excessively large array.

     ```solidity
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
     ```

   - Use of `block.timestamp`: The contract uses `block.timestamp` in several places, which can be manipulated by miners to some extent. This could lead to potential issues in functions like `banAddress()` and `recallMessage()` where the timestamp is used for logic related to banning addresses or message recall.

   - Incorrect Error Handling: In the `recallMessage()` function, the contract checks if a message has been sent by calling `isSignalSent()`. If the message has not been sent, the contract should revert with an appropriate error message. However, the contract does not revert in this case, potentially leading to unexpected behavior.

     ```solidity
         function recallMessage(
         Message calldata _message,
         bytes calldata _proof
     )
         external
         nonReentrant
         whenNotPaused
         sameChain(_message.srcChainId)
     {
         ...
     ```

2. **Centralization Risks**

   - The contract has an `onlyFromOwnerOrNamed` modifier for the `suspendMessages` and `banAddress` functions. This means that only the contract owner or a specific named address can suspend messages or ban addresses. This centralizes control and may lead to censorship or single point of failure.

   - The contract uses a mapping `addressBanned` to store banned addresses. If the contract owner's private key is compromised, an attacker can ban or unban addresses.

3. **Technical Risks**

   - The `sendMessage` function stores the message in storage without any validation checks. If a malicious actor sends a large amount of data as a message, it could potentially lead to a denial of service attack.

   - The `recallMessage` and `processMessage` functions decode proof from the provided data without any length check. If a malicious actor provides a large proof, it could potentially lead to a denial of service attack.

4. **Integration Risks**

   - `Not obvious Integration risk`

### packages/protocol/contracts/tokenvault/BridgedERC20.sol

1. **Systemic Risks**

   - The contract has a `BTOKEN_CANNOT_RECEIVE` error, which is used to prevent the contract from receiving tokens. However, this error is only checked in the `_beforeTokenTransfer` function, which means that it may still be possible to send tokens to the contract in certain circumstances.

     ```solidity
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
     ```

   - The contract does not have a mechanism for recovering lost or stolen tokens. If a user loses access to their tokens or their tokens are stolen, there is no way to recover them.

   - The contract does not have a mechanism for handling token transfers that are front-run or sandwiched by malicious actors. If a token transfer is front-run or sandwiched, the user may lose their tokens or pay a higher fee than necessary.

2. **Centralization Risks**

   - The contract has an `onlyOwner` modifier for the `setSnapshoter` function. This means that only the contract owner can set the snapshoter address, which centralizes control.

   - The contract has an `onlyOwnerOrSnapshooter` modifier for the `snapshot` function. This means that only the contract owner or the snapshoter can create a new token snapshot, which centralizes control.

3. **Technical Risks**

   - The contract uses the `ERC20SnapshotUpgradeable` and `ERC20VotesUpgradeable` contracts to provide snapshot and voting functionalities. If there are any vulnerabilities in these contracts, this contract may also be affected.

   - The contract uses the `ERC20Permit` contract to allow token holders to permit other addresses to spend their tokens. If there are any vulnerabilities in the `ERC20Permit` contract, this contract may also be affected.

4. **Integration Risks**

   - The contract is designed to represent tokens bridged from another chain. If there are any issues with the bridging mechanism, it could lead to unexpected behavior or loss of funds.

### packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

1. **Systemic Risks**

   - `Minting restrictions`: Minting is disallowed while migrating outbound, which could lead to issues if the migration process takes longer than expected or if the migration status is changed unexpectedly.

   - `Outbound migration permissions`: During outbound migration, only the token owner can call the `burn` function. This restriction could lead to issues if a user loses access to their tokens or if the migration process is disrupted.

2. **Centralization Risks**

   - `Owner control`: The contract's owner has the power to change the migration status and address, potentially allowing them to manipulate the token migration process.

   - `Vault control`: The "erc20_vault" contract has special permissions in the 'mint' and 'burn' functions. If the vault contract is compromised, it could lead to unauthorized token minting or burning.

3. **Technical Risks**

   - `Not obvious Technical risk`

4. **Integration Risks**

   - `Migration process`: The contract's primary function is to facilitate token migration between different contracts. Any issues in the integration with the source or destination contracts could result in token loss or other issues.

### packages/protocol/contracts/tokenvault/BridgedERC721.sol

1. **Systemic Risks**

   - The contract does not have a mechanism to ensure that the `mint` and `burn` functions are called only when the corresponding actions are performed on the source chain. This could lead to token supply inconsistencies between the source and destination chains.

     ```solidity
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
     ```

   - The `BridgedERC721` contract does not have a built-in mechanism to handle token metadata changes on the source chain. This could lead to outdated or inconsistent token URIs on the destination chain.

2. **Centralization Risks**

   - The `onlyFromNamed` modifier is used in the `mint` and `burn` functions, restricting these actions to be called only by an address named "erc721_vault". Centralization risks may arise if this address has too much control over the token supply or if it becomes compromised.

3. **Technical Risks**

   - `Not obvious Technical risk`

4. **Integration Risks**

   - The contract is designed to `bridge ERC721` tokens across different chains. Integration risks may arise when interacting with various token contracts, especially if they have different implementations or contain vulnerabilities.

### packages/protocol/contracts/tokenvault/BridgedERC1155.sol

1. **Systemic Risks**

   - The contract does not have a mechanism to ensure that the `mint`, `mintBatch`, and `burn` functions are called only when the corresponding actions are performed on the source chain. This could lead to token supply inconsistencies between the source and destination chains.

   - The contract uses placeholder data `foo` for the symbol and name validation in the `validateInputs` function. This could lead to unintended consequences if the function is updated in the future or if it has side effects that depend on the input data.

     ```solidity
              LibBridgedToken.validateInputs(_srcToken, _srcChainId, "foo", "foo");

     ```

   - The contract does not have a built-in mechanism to handle token metadata changes on the source chain. This could lead to outdated or inconsistent token URIs on the destination chain.

2. **Centralization Risks**

   - The `onlyFromNamed` modifier is used in the `mint`, `mintBatch`, and `burn` functions, restricting these actions to be called only by an address named "erc1155_vault". Centralization risks may arise if this address has too much control over the token supply or if it becomes compromised.

3. **Technical Risks**

   - `Not obvious Systemic risk`

4. **Integration Risks**

   - The contract is designed to bridge ERC1155 tokens across different chains. Integration risks may arise when interacting with various token contracts, especially if they have different implementations or contain vulnerabilities.

### packages/protocol/contracts/tokenvault/BaseVault.sol

1. **Systemic Risks**

   - `Not obvious Systemic risk`

2. **Centralization Risks**

   - The `onlyFromBridge` modifier is used in the `checkProcessMessageContext` and `checkRecallMessageContext` functions, restricting these actions to be called only by the address resolved as "bridge". Centralization risks may arise if this address has too much control over the vault or if it becomes compromised.

     ```solidity
         modifier onlyFromBridge() {
         if (msg.sender != resolve("bridge", false)) {
             revert VAULT_PERMISSION_DENIED();
         }
         _;
     }
     ```

3. **Technical Risks**

   - `Not obvious Technical risk`

4. **Integration Risks**

   - The contract is designed to interact with a bridge contract. Integration risks may arise if the bridge contract has vulnerabilities or is compromised.

### packages/protocol/contracts/tokenvault/ERC1155Vault.sol

1. **Systemic Risks**

   - `Bridged token deployment`: The contract deploys new bridged tokens when required, but this process might be vulnerable to attacks or failures if not properly managed. For example, a malicious user could try to deploy a fake bridged token contract with the same address.

   - `Unknown token contracts`: The `ERC1155Vault` contract interacts with arbitrary token contracts, which could have malicious code or vulnerabilities that could be exploited to steal funds or disrupt the system. It's important to ensure that only trusted and verified token contracts are used with this contract.

   - Unvalidated `refundTo` address: The contract does not validate the `refundTo` address provided in the `BridgeTransferOp` struct. If an attacker provides a malicious contract address as the `refundTo` address, it could lead to unintended consequences, such as reentrancy attacks or loss of funds.

   - Unvalidated `destOwner` address: The contract allows the `destOwner` address to be the same as the `msg.sender` if the `_op.destOwner` is not provided. This could lead to confusion and potential misdirection of funds if the user unintentionally provides an incorrect `destOwner` address.

   - Lack of rate limits: The contract does not impose any rate limits on the `sendToken`, `onMessageInvocation`, or `onMessageRecalled` functions. This could make the contract vulnerable to spamming or denial-of-service attacks.

   - Misuse of `abi.encodeCall`: The contract uses `abi.encodeCall` to encode the call data for the `msgData_` variable. If the function signature or parameters are not correctly specified, it could lead to incorrect call data and potential failures in the contract's logic.

2. **Centralization Risks**

   - `Centralized bridge contract`: The bridge contract used for interoperability between chains could become a central point of control and failure if it's not properly decentralized.

3. **Technical Risks**

   - `Incorrect handling of ERC1155 tokens`: The contract assumes that all tokens that support the ERC1155 interface follow the standard correctly. However, some tokens might have custom implementations that could lead to unexpected behavior.

4. **Integration Risks**

   - `Incorrect bridge contract integration`: If the bridge contract is not properly integrated with this contract, it could result in the loss or incorrect transfer of tokens between chains.

### packages/protocol/contracts/tokenvault/ERC20Vault.sol

1. **Systemic Risks**

   - `Blacklisting bridged tokens`: The contract has a blacklist mechanism for bridged tokens, but the process for adding or removing tokens from the blacklist is not specified. This could lead to tokens being incorrectly blacklisted or remaining blacklisted even after issues have been resolved.

   - `Canonical token mismatch`: The `changeBridgedToken` function checks for canonical token mismatch using keccak256 hashes of symbol and name. However, this approach might not be foolproof, as two different strings could have the same hash, although the probability is extremely low.

   - `Decimal mismatch`: The contract does not validate the decimals of the canonical token when burning or minting tokens. A mismatch in decimals could lead to incorrect token amounts being transferred.

2. **Centralization Risks**

   - Owner control: The contract has an `onlyOwner` modifier for the `changeBridgedToken` function, which means only the owner can change the bridged token. This centralizes control over the contract and could lead to censorship or misuse.

3. **Technical Risks**

   - `Not obvious Technical risk`

4. **Integration Risks**

   - `Incompatible token contracts`: If the contract interacts with ERC20 or IBridgedERC20 contracts that have non-standard implementations, it could lead to unexpected behavior or token loss.

   - `Bridge contract integration`: If the bridge contract's interface or behavior changes, it could break the integration with the ERC20Vault contract, leading to potential loss of tokens or other issues.

### packages/protocol/contracts/tokenvault/ERC721Vault.sol

1. **Systemic Risks**

   - `Mismatched token IDs`: When `transferring ERC721` tokens, the contract assumes that the `token IDs` are unique and valid. If there is a mismatch between the token IDs on the source and target chains or if an invalid token ID is used, it could lead to the loss or theft of tokens.

   - `Token duplication`: If there is an issue with the deployment of the `BridgedERC721` contract, it could potentially lead to the duplication of tokens, which would have serious consequences for the integrity and value of the tokens on both the source and target chains.

   - `Unvalidated input data`: The ERC721Vault contract does not perform extensive validation of `input data`, such as `token IDs` or `addresses`. This could lead to unexpected behavior, security risks, or loss of tokens if invalid data is provided.

2. **Centralization Risks**

   - `Centralized control over the vault`: The ERC721Vault contract has an `onlyOwner` modifier for certain functions, which means that only the owner of the contract can perform specific actions. This centralization of control could lead to potential abuse or mismanagement.

3. **Technical Risks**

   - `Unverified contracts`: The `ERC721Vault` contract does not verify the authenticity or security of the contracts it interacts with. This means that it could potentially interact with malicious or compromised contracts, leading to potential loss or theft of tokens.

4. **Integration Risks**

   - `Compatibility issues`: The ERC721Vault contract assumes that the ERC721 tokens it interacts with adhere to the ERC721 standard. However, some tokens may have custom implementations or extensions that are not compatible with the `ERC721Vault` contract, potentially leading to unexpected behavior.

### packages/protocol/contracts/thirdparty/optimism/Bytes.sol

1. **Systemic Risks**

   - `Incorrect keccak256 comparison`: The `equal` function compares two byte arrays by comparing their keccak256 hashes. This approach assumes that there are no hash collisions, which is highly unlikely but theoretically possible. In the rare case of a hash collision, the function would return true even though the byte arrays are not equal.

   - Incorrect input handling: The `toNibbles` function assumes that the input byte array is well-formed and does not contain any invalid data. If the input byte array contains unexpected data, the function might produce an incorrect output or behave unexpectedly.

   - `Memory management`: The contract uses manual memory management in assembly code, which could lead to potential errors or vulnerabilities if not handled correctly. For example, memory overlaps, underflows, or overflows could occur if memory pointers are not properly managed.

2. **Centralization Risks**

   - `Not obvious Centralization risk`

3. **Technical Risks**

   - `Input validation`: The contract doesn't perform extensive input validation for its functions. This could lead to unexpected behavior or errors if invalid inputs are provided.

4. **Integration Risks**

   - `Not obvious Integration risk`

### packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

1. **Systemic Risks**

   - `Incorrect decoding of RLP items`: The contract's `_decodeLength` function is responsible for decoding the length of RLP items. If this function has any errors or edge cases that are not properly handled, it could lead to incorrect decoding of RLP items.

2. **Centralization Risks**

   - `Not obvious Centralization risk`

3. **Technical Risks**

   - `Incorrect input handling`: The contract assumes that the input byte arrays are correctly `RLP-encoded`. If the input is malformed or not properly encoded, it could lead to unexpected behavior or errors.

   - `Limited list length`: The contract has a maximum list length of 32 items. If a longer list is encountered, it could lead to truncation or incorrect parsing of the data.

4. **Integration Risks**

   - `Compatibility issues`: The contract may not be compatible with other contracts or systems that use different encoding standards or formats for byte arrays.

### packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

1. **Systemic Risks**

   - The contract does not perform any checks on the provided `_root` parameter. If an incorrect root is provided, the contract will still execute without any errors, potentially leading to incorrect results or false positives in proof verification.

   - The contract assumes that the `Merkle trie` used for proofs follows the Ethereum state trie structure. However, if the trie is constructed differently (e.g., using different node types or encoding schemes), the contract may not function correctly and could lead to incorrect results or errors.

   - The contract's `get` function does not handle the case where a key exists in the trie but its value is set to an empty byte array (`bytes(0)`). In such cases, the function will revert with an error, even though the key is technically present in the trie. This behavior might not be desirable for some use cases.

   ```solidity
       function get(
           bytes memory _key,
           bytes[] memory _proof,
           bytes32 _root
       )
           internal
           pure
           returns (bytes memory value_)
       {
           require(_key.length > 0, "MerkleTrie: empty key");

           TrieNode[] memory proof = _parseProof(_proof);
           bytes memory key = Bytes.toNibbles(_key);
           bytes memory currentNodeID = abi.encodePacked(_root);
           uint256 currentKeyIndex = 0;

           // Proof is top-down, so we start at the first element (root).
           for (uint256 i = 0; i < proof.length; i++) {
               TrieNode memory currentNode = proof[i];

   ```

   - The contract's `verifyInclusionProof` function relies solely on the equality of the provided `_value` and the value obtained from the trie using the `get` function. If the provided `_value` is incorrect or tampered with, the function will return an incorrect result. This risk can be mitigated by ensuring that the `_value` parameter is obtained from a trusted source.

   ```solidity
           function verifyInclusionProof(
           bytes memory _key,
           bytes memory _value,
           bytes[] memory _proof,
           bytes32 _root
       )
           internal
           pure
           returns (bool valid_)
       {
           valid_ = Bytes.equal(_value, get(_key, _proof, _root));
       }
   ```

   - The contract's `_getSharedNibbleLength` function uses a loop to iterate through the nibbles of two byte arrays, which could be inefficient for large arrays and lead to high gas consumption. An alternative implementation using assembly or a more efficient algorithm could help mitigate this issue.

     ```solidity
         function _getSharedNibbleLength(
         bytes memory _a,
         bytes memory _b
     )
         private
         pure
         returns (uint256 shared_)
     {
         uint256 max = (_a.length < _b.length) ? _a.length : _b.length;
         for (; shared_ < max && _a[shared_] == _b[shared_];) {
             unchecked {
                 ++shared_;
             }
         }
     }
     ```

2. **Centralization Risks**

   - `Not obvious Centralization risk`

3. **Technical Risks**

   - The contract assumes a hexary trie (with a radix of 16), which may not be suitable for all use cases. If the contract is used with a trie of a different radix, it could lead to incorrect behavior.

   - The `verifyInclusionProof` and `get` functions do not have any bounds checking for the `_proof` array. If an excessively large proof is provided, it could lead to high gas consumption or out-of-gas errors.

   - The contract uses the `bytes` type for some function parameters and return values, which can be inefficient in terms of gas consumption and storage. Using `bytes32` or other fixed-size types might be more appropriate, depending on the use case.

4. **Integration Risks**

   - The contract assumes that the provided proof is a top-down Merkle trie inclusion proof. If the proof is constructed differently or is from a different data structure, the contract may not function correctly.

### packages/protocol/contracts/verifiers/SgxVerifier.sol

1. **Systemic Risks**

   - Misuse of atte`station: The `SgxVerifier` contract checks if an address has already been attested to prevent bypassing the contract's expiry check. However, it is possible to register old addresses during proving, which could be misused.

   - Misuse of `instance replacement`: The contract allows replacing an instance, which could be misused if not properly controlled. For example, `an attacker could replace an instance with a malicious one if they have control over the old instance's address`.

   - Misuse of instance `validity dela`y: The `SgxVerifier` has a delay until an instance is enabled when using `onchain` RA verification. This delay could be misused by an attacker to perform a denial-of-service attack by repeatedly registering instances.

2. **Centralization Risks**

   - `Owner control`: The contract has an owner who can add or delete instances. This centralizes control and could lead to censorship or manipulation if the owner's account is compromised.

3. **Technical Risks**

   - `Unhandled exceptions`: The contract does not have error handling for all `external calls`. If an external call fails, it could cause the contract to revert or behave unexpectedly.

4. **Integration Risks**

   - `Incorrect data formats`: The contract expects data in specific formats, such as the `V3Struct.ParsedV3QuoteStruct` for attestation and the `TaikoData.Transition` for proof verification. If the data is not in the correct format, it could lead to errors or unexpected behavior.

### packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

1. **Systemic Risks**

   - `claim period`: The contract allows users to claim the airdrop only during the claim period. This could be misused by an attacker who manipulates the blockchain's time to claim the airdrop outside of the claim period.

2. **Centralization Risks**

   - `Owner control`: The contract has an owner who can control the contract's functionality. This centralizes control and could lead to censorship or manipulation if the owner's account is compromised.

3. **Technical Risks**

   - `Not obvious Technical risk`

4. **Integration Risks**

   - `Not obvious Integration risk`

### packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

1. **Systemic Risks**

   - `claimedAmount and withdrawnAmount mappings`: The contract stores the claimed amount and withdrawn amount for each user in mappings. This could be misused by an attacker who manipulates these mappings to steal tokens from other users or to claim more tokens than they are eligible for.

2. **Centralization Risks**

   - `Owner control`: The contract has an owner who can control the contract's functionality. This centralizes control and could lead to censorship or manipulation if the owner's account is compromised.

3. **Technical Risks**

   - `Not obvious Technical risk`

4. **Integration Risks**

   - `Not obvious Integration risk`

### packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

1. **Systemic Risks**

   - `Not obvious Systemic risk`

2. **Centralization Risks**

   - `setConfig function`: The contract's `setConfig` function is only callable by the owner. This could be misused by the owner to change the configuration parameters in a way that benefits themselves or harms other users.

     ```solidity
         function setConfig(
             uint64 _claimStart,
             uint64 _claimEnd,
             bytes32 _merkleRoot
         )
             external
             onlyOwner
         {
             _setConfig(_claimStart, _claimEnd, _merkleRoot);
         }
     ```

3. **Technical Risks**

   - `Not obvious Systemic risk`

4. **Integration Risks**

   - `MerkleProof library`: The contract uses the `MerkleProof` library to verify merkle proofs. This library could have vulnerabilities or be compromised, which could affect the contract's functionality.

### packages/protocol/contracts/team/TimelockTokenPool.sol

1. **Systemic Risks**

   - The `_voidGrant` function sets the `grantStart` and `grantPeriod` of a grant to 0 when voiding the grant. This could potentially cause confusion or unexpected behavior if these fields are used elsewhere in the system.

   - The `_calcAmount` function has complex logic involving multiple parameters (`_amount`, `_start`, `_cliff`, `_period`). This complexity could lead to unexpected behavior or bugs if not properly understood or implemented.

2. **Centralization Risks**

   - The contract has an `onlyOwner` modifier for the `grant` and `void` functions. This means that only the contract owner can grant tokens or void grants. This centralization of power could lead to misuse or abuse.

3. **Technical Risks**

   - The `_calcAmount` function uses `block.timestamp` to calculate the amount of tokens that can be withdrawn. However, `block.timestamp` can be manipulated by miners to a certain extent, which could lead to unexpected behavior.

   - The `ECDSA.recover` function used in the `withdraw` function could potentially be vulnerable to replay attacks if the same signature is used twice.

4. **Integration Risks**

   - `Not obvious Integration risk`

### packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

1. **Systemic Risks**

   - The contract uses the `sha256` function for hashing data, but it does not include a salt or nonce. This could potentially lead to hash collisions or pre-image attacks.

2. **Centralization Risks**

   - The contract uses the `msg.sender` as the owner during initialization. If the owner's account is compromised, an attacker could gain control over the contract.

3. **Technical Risks**

   - The contract uses the `block.timestamp` for certificate validity checks. However, `block.timestamp` can be manipulated by miners to a certain extent, potentially leading to security issues.

4. **Integration Risks**

   - `Not obvious Integration risk`

### packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

1. **Systemic Risks**

   - `Not obvious Systemic risk`

2. **Centralization Risks**

   - `Not obvious Centralization risk`

3. **Technical Risks**

   - The contract uses complex parsing and decoding logic, which could lead to potential bugs or errors in the processing of certificates.

   - The contract assumes that the input data is well-formed and does not perform extensive input validation, which could lead to unexpected behavior or errors.

4. **Integration Risks**

   - The contract assumes that the input certificates are signed using the ECDSA algorithm with a specific curve (secp256r1). If the input certificates use a different signing algorithm or curve, the contract may not function correctly.

### packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

1. **Systemic Risks**

   - The contract uses the '`decode`' function of the 'Base64' library to decode base64 encoded strings. If the input strings are not base64 encoded, the function could fail or behave unexpectedly.

2. **Centralization Risks**

   - `Not obvious Centralization risk`

3. **Technical Risks**

   - `Not obvious Technical risk`

4. **Integration Risks**

   - `Incorrect Assumptions`: The contract assumes that the input quote will always be larger than `MINIMUM_QUOTE_LENGTH` and that the quote length minus `436` will always equal `localAuthDataSize`. If these assumptions are incorrect, the contract could fail or behave unexpectedly.

### packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

1. **Systemic Risks**

   - The specific parsing and handling of cryptographic elements (exponents, moduli, signatures) in functions like `verifyRS256Signature`, `verifyRS1Signature`, `verifyES256Signature` introduce unique risks related to cryptographic implementation correctness and efficiency.

   - The reliance on specific cryptographic algorithms and formats may limit interoperability or compatibility with systems using different standards or protocols.

2. **Centralization Risks**

   - The contract relies on an external `ES256VERIFIER` address for verifying ES256 signatures, which introduces centralization risks if this verifier is controlled or compromised by a single entity.

3. **Technical Risks:**

   - Potential vulnerabilities in signature parsing and verification logic (`verifyRS256Signature`, `verifyRS1Signature`, `verifyES256Signature`) could lead to signature forgery or unauthorized access.

   - Incomplete input validation in functions like `verifyES256Signature` (e.g., not checking all possible edge cases) may lead to unexpected behavior or vulnerabilities.

4. **Integration Risks:**

   - `Not obvious Integration risk`

## Codebase Core Functionality,Technical Characteristics, Importance and Management Overview

| File Name               | Core Functionality                                                                                                                                                                                                                                                                                                                                                                                                              | Technical Characteristics                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | Importance and Management                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `EssentialContract.sol` | This `EssentialContract` contract defines essential functionality such as `pausing` and `unpausing` operations, managing ownership, and enforcing access control through modifiers.                                                                                                                                                                                                                                             | It uses OpenZeppelin libraries like `UUPSUpgradeable`, `Ownable2StepUpgradeable`, and `AddressResolver`, implements modifiers for reentrancy checks, and leverages assembly code for efficiency in certain storage operations.                                                                                                                                                                                                                                                                                                                                                                                                                  | These functionalities are crucial for managing contracts securely, controlling critical operations, and ensuring that certain functions can only be executed by authorized entities, enhancing the contract's robustness and security.Management: The contract manages `ownership` transfer, upgrade authorization, `pause/unpause` states, and address resolution, providing a structured approach to contract governance and control over critical contract functions.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `LibTrieProof.sol`      | The contract provides a library `LibTrieProof` that allows verifying Merkle proofs for storage slots in Ethereum accounts, ensuring data integrity and security.                                                                                                                                                                                                                                                                | It leverages third-party libraries like `RLPReader`, `RLPWriter`, and `SecureMerkleTrie` for parsing `RLP-encoded` data and performing `Merkle proof verification`, enhancing the contract's functionality and security.                                                                                                                                                                                                                                                                                                                                                                                                                        | This library is essential for applications requiring secure verification of storage values and ensuring that data accessed from Ethereum accounts is valid and `tamper-proof`, thereby contributing to the overall integrity and reliability of blockchain-based systems.Management: The contract manages the verification process for Merkle proofs, handling errors such as invalid account proofs or inclusion proofs, ensuring that only valid and verified data is accepted, which is critical for maintaining the integrity of smart contract interactions.                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `LibDepositing.sol`     | The `LibDepositing` library provides functions for `depositing` Ether to Layer 2 in the Taiko protocol, managing deposits, `processing them in batches`, and ensuring deposit limits and fees are adhered to.                                                                                                                                                                                                                   | It uses the `LibAddress` and `LibMath` libraries for address and math operations, incorporates storage management techniques such as ring buffers for deposits, and efficiently processes multiple deposits in a batched manner to optimize gas usage.                                                                                                                                                                                                                                                                                                                                                                                          | This library is crucial for the `Taiko` protocol as it handles the crucial task of depositing Ether to Layer 2, ensuring that deposits are within specified limits, calculating fees accurately, and managing deposit processing to maintain protocol efficiency and integrity.Management: The library manages the `depositing process`, including `checking deposit limits`, processing deposits in `batches`, encoding deposit data for storage, and emitting events to track deposit activities, contributing to effective and secure deposit handling within the Taiko protocol.                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `LibProposing.sol`      | The `LibProposing` library facilitates block proposals in the Taiko protocol, handling various aspects such as validating proposers, managing block metadata, processing deposits, and executing hooks.                                                                                                                                                                                                                         | It uses several `libraries` and interfaces such as `LibAddress`, `IAddressResolver`, `ITierProvider`, and `IERC20` for address handling, resolution, tier determination, and ERC20 token operations, respectively. The library also employs data encoding and decoding techniques, blob caching mechanisms, and checks for valid block parameters and configurations.                                                                                                                                                                                                                                                                           | This library plays a crucial role in the `Taiko protocol` by enabling permissionless `block proposals`, ensuring integrity through metadata and hash validations, managing hooks for additional functionalities, `processing deposits`, and handling token balances, contributing to the protocol's security, functionality, and performance.Management: The library manages block proposal logic, including checks for valid `proposers`, processing and `caching blobs`, handling metadata and block data, executing hooks securely, verifying token balances, and emitting events to track block proposal activities, ensuring efficient and secure operation within the Taiko protocol.                                                                                                                                                                                                                                                                                                            |
| `LibProving.sol`        | The `LibProving` library provides functionality for handling block contestation and proving within the Taiko protocol. It includes methods for proving or contesting block transitions, pausing or unpausing the proving process, and managing transition states.                                                                                                                                                               | This library uses various Solidity features such as `storage variables`, structs (TaikoData), events (TransitionProved, TransitionContested, ProvingPaused), error handling (revert statements with custom errors), and interfaces (`IERC20`, `IAddressResolver`, `IVerifier`, `ITierProvider`). It also employs mathematical operations (`LibMath`) and integrates with other contracts through imports and function calls.                                                                                                                                                                                                                    | The `LibProving` library plays a crucial role in the Taiko protocol by ensuring the integrity and validity of block transitions through proof `verification` and contestation. It manages transition states, handles `tier-based` proofs, and enforces rules for proving and contesting transitions, which are fundamental for the security and reliability of the protocol.Management: The library manages transition states within the TaikoData storage, interacts with external contracts such as verifiers and tier providers via the IAddressResolver, and handles token transfers using `IERC20` for managing rewards and bonds. It also manages the pausing and `unpausing` of the proving process through the ProvingPaused event and pauseProving function. Overall, it provides a structured and controlled environment for proving and contesting block transitions within the Taiko protocol.                                                                                             |
| `LibVerifying.sol`      | The `LibVerifying` library handles block verification within the Taiko protocol, including initializing the protocol state, verifying blocks, and syncing chain data.                                                                                                                                                                                                                                                           | This library utilizes Solidity features such as `storage` variables (`TaikoData`), events (`BlockVerified`), error handling (`revert` statements with custom errors), interfaces (`IERC20`, `IAddressResolver`, `ISignalService`, `ITierProvider`), mathematical operations (`LibMath`), and external calls to other contracts (`_syncChainData`, `getSyncedChainData`, `syncChainData`).                                                                                                                                                                                                                                                       | The `LibVerifying` library is crucial for ensuring the integrity and correctness of the `Taiko protocol` by verifying blocks, validating transitions, and syncing chain data. It plays a fundamental role in maintaining consensus and security across the protocol's layers.Management: This library manages protocol-level states such as block verification status (`lastVerifiedBlockId`), handles interactions with external contracts (`IERC20`, `ISignalService`, `ITierProvider`), and implements logic for validating configurations (`_isConfigValid`). It also emits events (`BlockVerified`) to notify about block verifications and coordinates the verification process based on specified criteria and thresholds. Overall, it provides essential functionalities for managing and maintaining the Taiko protocol's operational integrity.                                                                                                                                              |
| `Lib1559Math.sol`       | The `Lib1559Math` library implements a bonding curve based on the mathematical function `e^(x)` for `EIP-1559`, specifically for calculating the base fee in Ethereum transactions.                                                                                                                                                                                                                                             | This library uses mathematical functions like exponential calculation `_ethQty` based on gas parameters and adjustment factors. It imports `LibFixedPointMath` from a third-party library to perform fixed-point arithmetic operations necessary for accurate fee calculations.                                                                                                                                                                                                                                                                                                                                                                 | The `Lib1559Math` library is crucial for implementing the fee `calculation` mechanism proposed in `EIP-1559` for Ethereum transactions. It helps determine the base fee dynamically based on network demand, aiming to achieve better fee predictability and transaction inclusion.Management: This library manages mathematical computations related to fee calculation, ensuring that the base fee calculation follows the `EIP-1559` specifications and handles exceptional cases such as invalid parameters through error handling `EIP1559_INVALID_PARAMS`. It provides a foundational component for managing transaction fees in a more efficient and predictable manner on the Ethereum network.                                                                                                                                                                                                                                                                                                |
| `TaikoL2.sol`           | The `TaikoL2` contract is designed to handle `cross-layer` message verification and manage `EIP-1559` gas pricing for `Layer 2` operations. It anchors the latest `L1` block details to `L2` for `cross-layer` communication, manages EIP-1559 parameters for gas pricing, and stores verified L1 block information.                                                                                                            | This contract leverages various Solidity features and libraries such as `SafeERC20` for safe token transfers, `LibAddress` for address-related operations, `LibMath` for mathematical calculations, and Lib1559Math for `EIP-1559` base fee calculations using mathematical functions like exponential computation.                                                                                                                                                                                                                                                                                                                             | The TaikoL2 contract plays a crucial role in `bridging` communication between `Layer 1` and `Layer 2` of the Ethereum network, ensuring accurate gas pricing through `EIP-1559` parameters, and maintaining synchronization of block details between the two layers for efficient transaction processing and state management.Management: This contract manages several key functionalities including anchoring L1 block details to L2, verifying base fees using EIP-1559 calculations, handling token withdrawals, and managing ownership and access control through inheritance from CrossChainOwned. It incorporates error handling for various scenarios such as invalid parameters, sender verification, and base fee mismatches, ensuring the integrity and security of its operations.                                                                                                                                                                                                         |
| `SignalService.sol`     | The `SignalService` contract facilitates signal propagation and chain data synchronization across different chains by `managing signals`, authorizing addresses for data syncing, and `verifying Merkle proofs` to ensure data integrity and authenticity during synchronization processes.                                                                                                                                     | This contract employs mappings to store top block IDs and authorized addresses, `utilizes` error handling mechanisms for various invalid states and `unauthorized access`, and integrates with essential libraries like `LibTrieProof` for verifying Merkle proofs and `SafeCast` for safe type conversions. It also implements modifiers to ensure valid senders and non-zero values for critical operations.                                                                                                                                                                                                                                  | The `SignalService` contract plays a vital role in maintaining the integrity and synchronization of chain data across multiple chains within a decentralized ecosystem. It provides a secure mechanism for signaling and syncing data, enabling cross-chain communication and interoperability, which are crucial aspects of blockchain scalability and usability.Management: This contract is managed through functions such as initialization for contract setup, authorization of addresses for data syncing, sending signals and syncing chain data, verifying Merkle proofs for signal integrity, and handling error conditions to maintain contract security and reliability. It includes emit events for tracking authorized actions and synced data, enhancing transparency and auditability within the system.                                                                                                                                                                                |
| `Bridge.sol`            | The Bridge contract facilitates `cross-chain` message passing by managing message statuses, `proofs`, and handling message execution and recalls based on specified conditions. It provides methods like `sendMessage`, `recallMessage`, `processMessage`, and `retryMessage` to manage message execution across different chains, allowing messages to be sent, recalled, processed, or retried based on certain criteria.     | The contract imports various `libraries` and interfaces such as Address, `EssentialContract`, `LibAddress`, `ISignalService`, and `IBridge`.It employs storage mappings (`messageStatus`, `addressBanned`, `proofReceipt`) to store message status, `banned addresses`, and proof receipts, `respectively`.The contract utilizes modifiers like sameChain to validate chain IDs and various error states to handle exceptional conditions during message processing.It implements functions for `message sending`, recalling, `processing`, `retrying`, and handling message statuses and proofs using merkle inclusion `proofs` and `signals`. | The `Bridge` contract plays a crucial role in interoperability between different blockchain networks by enabling the transfer of messages and data securely and efficiently.It ensures that messages are processed correctly based on predefined conditions, manages message statuses to prevent duplicate or unauthorized executions, and handles proofs to verify message authenticity and execution.By providing methods to suspend messages, ban addresses, and manage message retries, the contract enhances the reliability and security of cross-chain communication, reducing potential risks and ensuring smooth message execution.                                                                                                                                                                                                                                                                                                                                                           |
| `BridgedERC20.sol`      | The contract `BridgedERC20` is an upgradeable ERC20 token contract designed to represent tokens bridged from another chain. It includes functionalities such as `token initialization`, `snapshot creation`, `metadata retrieval`, and token transfer management.                                                                                                                                                               | This contract imports various libraries and contracts from `OpenZeppelin`, including `IERC20MetadataUpgradeable`, `Strings`, `ERC20SnapshotUpgradeable`, and `ERC20VotesUpgradeable`. It implements specific functions such as init, `setSnapshoter`, `snapshot`, and internal token minting/burning functions.                                                                                                                                                                                                                                                                                                                                 | The importance of `BridgedERC20.sol` contract lies in its ability to facilitate the representation and management of tokens `bridged` from another blockchain within the Ethereum ecosystem. It provides essential features like `metadata handling`, `snapshot` creation for governance purposes, and token transfer logic while maintaining upgradability.The contract includes a snapshooter address that can be set by the owner, allowing designated entities to create token `snapshots`. `Ownership` and authorization are managed through modifiers like `onlyOwner` and `onlyOwnerOrSnapshooter`, ensuring controlled access to critical functions like snapshot creation and token transfers.                                                                                                                                                                                                                                                                                                |
| `BridgedERC20Base.sol`  | The contract `BridgedERC20Base` serves as an abstract base contract for bridged ERC20 tokens, implementing functionalities related to token migration, `minting`, `burning`, and ownership management.                                                                                                                                                                                                                          | This Solidity contract imports `EssentialContract` and IBridgedERC20 interfaces and includes internal functions such as `_mintToken`, `_burnToken`, and `_isMigratingOut` for token management during migration processes.                                                                                                                                                                                                                                                                                                                                                                                                                      | The contract's importance lies in its role as a foundational component for managing bridged `ERC20` tokens, enabling features like changing migration status, `minting` and `burning` tokens during migration, and ensuring ownership integrity through access control mechanisms.Management aspects are handled through functions like changeMigrationStatus for updating migration status, mint and burn functions with appropriate checks during migration scenarios, and ownership retrieval via the owner function inherited from OwnableUpgradeable. Access control is enforced through modifiers like `nonReentrant`, `whenNotPaused`, and `onlyFromOwnerOrNamed`("erc20_vault").                                                                                                                                                                                                                                                                                                               |
| `BridgedERC721.sol`     | The contract `BridgedERC721` facilitates the bridging of `ERC721` tokens between different blockchain networks by allowing `minting`, `burning`, and querying token-related information.                                                                                                                                                                                                                                        | It is utilizes OpenZeppelin's `ERC721Upgradeable` and `Strings` libraries, implements essential contract functionalities, and employs a bridging mechanism via LibBridgedToken.                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | This contract is crucial for interoperability between blockchain networks as it enables the transfer and management of ERC721 tokens across different chains, enhancing token utility and accessibility.The contract incorporates access control mechanisms such as `pausing` functionality and `permission-based` minting and burning operations, ensuring secure and controlled token management. Additionally, it defines specific error cases to handle exceptional conditions like invalid burns or token transfers to the contract itself.                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `BridgedERC1155.sol`    | The contract facilitates the bridging of `ERC721` tokens across different chains by allowing `minting` and `burning` of tokens according to specified rules.                                                                                                                                                                                                                                                                    | It implements the `ERC721` standard, utilizing OpenZeppelin's `ERC721Upgradeable` contract and Strings library for string manipulation. The contract also utilizes upgradability patterns for potential future enhancements.                                                                                                                                                                                                                                                                                                                                                                                                                    | This contract plays a crucial role in interoperability between different blockchain networks by enabling the transfer of `NFTs` across chains, which is essential for maintaining `liquidity` and utility of NFT assets.Management: The contract is managed by an essential contract (`EssentialContract`) and implements access control mechanisms, allowing only designated addresses such as `erc721_vault` to mint and burn tokens. It also incorporates a `pause` mechanism to control contract operations during certain conditions, enhancing security and operational control.                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `BaseNFTVault.sol`      | The contract serves as an abstract base for bridging `NFTs` across different blockchain networks, facilitating token transfers and management.                                                                                                                                                                                                                                                                                  | It includes `mappings` and `structs` to store information about bridged `NFTs` and their canonical counterparts, as well as structs to represent bridged token transfer operations. Additionally, it defines interface `IDs` for `ERC1155` and `ERC721` standards and includes event logging for token-related actions.                                                                                                                                                                                                                                                                                                                         | This contract plays a critical role in enabling `cross-chain` interoperability for `NFTs`, allowing users to transfer NFTs between different blockchain networks, which is essential for expanding the utility and accessibility of `NFT` assets.Management: The contract implements modifiers and error handling to ensure the validity of token transfer operations, including checks for token array mismatches, maximum token transfer limits, and the validity of token addresses. It also emits events to provide transparency and track token-related actions on the contract.                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `BaseVault.sol`         | This abstract contract serves as a base implementation for `vaults`, providing functionality for initialization, interface support `checking`, and context validation for processing and recalling messages from a bridge.                                                                                                                                                                                                      | Includes inheritance from `OpenZeppelin's` upgradeable contracts for essential contract functionalities and `ERC165` for interface support checking. The contract also employs modifiers for access control and error handling.                                                                                                                                                                                                                                                                                                                                                                                                                 | The contract is crucial for creating vaults that interact with bridges to facilitate `cross-chain` communication and asset transfers. It ensures that only authorized entities, such as `bridges`, can interact with the `vault`, enhancing security and integrity in cross-chain operations.Management: Access to critical functions is restricted through the 'onlyFromBridge' modifier, which verifies that the caller is the designated bridge contract. Error handling ensures that unauthorized access attempts are reverted, maintaining the integrity and security of the vault operations. Additionally, the contract provides an initialization function for setting the owner and address manager, allowing for proper configuration upon deployment.                                                                                                                                                                                                                                       |
| `ERC1155Vault.sol`      | The contract acts as a vault for `ERC1155` tokens, facilitating their `deposit`, `withdrawal`, and `transfer` across different blockchain networks via a `bridge`. It also manages the mapping between canonical ERC1155 tokens and their bridged counterparts.                                                                                                                                                                 | It imports OpenZeppelin's `ERC1155` contracts for token handling and `ERC1155ReceiverUpgradeable` for receiving `ERC1155` tokens. Additionally, it uses an interface for `ERC1155` contracts with name() and symbol() functions and incorporates proxy deployment using ERC1967Proxy for bridged token deployment.                                                                                                                                                                                                                                                                                                                              | The contract plays a crucial role in enabling `cross-chain` token transfers by acting as a centralized repository for `ERC1155` tokens and facilitating their `conversion` to bridged tokens for interoperability across disparate blockchain networks. Its ability to deploy and manage bridged token contracts enhances the scalability and accessibility of tokenized assets across multiple chains.Management: Access to critical functions like token `transfer` and message handling is `restricted` to authorized users, ensuring secure and controlled token management. The contract maintains mappings to track canonical and bridged tokens, providing transparency and auditability in token handling operations. Events are emitted to notify stakeholders about token transfers and contract deployments, enhancing visibility and accountability in the token bridging process.                                                                                                         |
| `ERC20Vault.sol`        | The contract serves as a `vault` for ERC20 tokens, excluding Ether, `allowing users to deposit`, `withdraw`, and `transfer` these tokens between different blockchain networks via a bridge. It also manages the mapping between canonical `ERC20` tokens and their bridged counterparts.                                                                                                                                       | It imports OpenZeppelin's ERC20 contracts for token handling and uses `SafeERC20` for safe token transfers. Additionally, it utilizes a `struct` to represent canonical `ERC20` tokens and another struct to represent bridge transfer operations. The contract also implements functions for changing bridged tokens, handling token transfers, and deploying bridged ERC20 tokens using proxy deployment.                                                                                                                                                                                                                                     | This contract is essential for facilitating `cross-chain` interoperability for ERC20 tokens, enabling seamless token transfers between different blockchain networks. It ensures proper handling of token transfers and `mappings` between canonical and bridged tokens, which is crucial for maintaining token integrity and accessibility across chains.Management: Access to critical functions is restricted through modifiers such as `onlyOwner` to ensure that only authorized entities can interact with the vault and manage bridged tokens. Error handling mechanisms are implemented to ensure the validity of token transfer operations and prevent unauthorized access. Additionally, the contract emits events to provide transparency and track token-related actions.                                                                                                                                                                                                                  |
| `ERC721Vault.sol`       | The contract acts as a vault for `ERC721` tokens, `receiving` and `managing` deposits of these tokens from users, and facilitating their transfer between different blockchain networks via a `bridge`. It maintains mappings between canonical `ERC721` tokens and their bridged counterparts.                                                                                                                                 | It implements functions for handling `ERC721` token transfers, including `receiving tokens from users`, `sending tokens` to other chains, and recalling tokens back to the original chain. The contract also utilizes `proxy` deployment for deploying bridged ERC721 token contracts and initializes them accordingly.                                                                                                                                                                                                                                                                                                                         | This contract plays a vital role in enabling `cross-chain` interoperability for ERC721 tokens, allowing users to transfer their tokens seamlessly between different blockchain networks. By `managing` the `mapping` between canonical and `bridged` tokens, it ensures the integrity and accessibility of ERC721 tokens across chains.Management: Access to critical functions is restricted through modifiers such as 'onlyOwner' to ensure that only authorized entities can interact with the vault and manage bridged tokens. Error handling mechanisms are implemented to ensure the validity of token transfer operations and prevent unauthorized access. Additionally, the contract emits events to provide transparency and track token-related actions.                                                                                                                                                                                                                                     |
| `SgxVerifier.sol`       | The `SgxVerifier` contract facilitates the verification of SGX signature proofs `on-chain`, ensuring the integrity and validity of attestation quotes provided by `SGX` instances. It manages the `registration`, `validation`, and replacement of trusted `SGX` instances, maintaining a registry of `ECDSA` public keys associated with valid SGX instances.                                                                  | Leveraging cryptographic primitives from OpenZeppelin's `ECDSA` library, the contract verifies SGX proofs submitted during state transitions, confirming the authenticity of the transition and the legitimacy of the associated `SGX` instance. It interacts with the Automata Attestation contract to verify attestation quotes, ensuring the trustworthiness of SGX instances. Gas-saving techniques, such as using instance IDs for storage efficiency, are implemented to optimize contract functionality.                                                                                                                                 | The contract plays a critical role in enhancing the security and reliability of `off-chain` computations by verifying `SGX` proofs on-chain, mitigating the risk of malicious behavior or compromised SGX instances. By maintaining a registry of trusted SGX instances and enforcing expiration checks, the contract fosters a secure environment for `on-chain` interactions relying on SGX-based computations, bolstering the integrity of decentralized systems.Management: Access to critical functions like adding and deleting SGX instances is restricted to authorized users, ensuring controlled management of the instance registry. The contract emits events to notify stakeholders about the addition, replacement, or deletion of SGX instances, enhancing transparency and accountability in the management process. Gas-efficient storage mechanisms are employed to optimize resource utilization and minimize transaction costs associated with instance management operations.     |
| `TimelockTokenPool.sol` | The `TimelockTokenPool` contract manages Taiko tokens allocated to different roles and individuals, facilitating a three-state lifecycle for token management: "`allocated`" to "`granted`, owned, and `locked`," and finally to "granted, owned, and `unlocked`." It allows for conditional allocation of tokens, with the ability to cancel allocations and ensures irreversible ownership once tokens are granted and owned. | Utilizing OpenZeppelin's `SafeERC20` library, the contract interacts with ERC20-compliant tokens (Taiko tokens and a cost token) to handle token transfers securely. It implements functions to grant, `void`, and `withdraw` tokens based on predefined schedules, enforcing constraints such as start times, cliffs, and periods for token unlocking and ownership.                                                                                                                                                                                                                                                                           | Deploying multiple instances of this contract for different roles (e.g., `investors`, `team members`, `grant program grantees`) enables precise management of token `allocations`, fostering accountability and transparency in token distribution. By enforcing predetermined unlocking schedules and ownership constraints, the contract ensures fair and controlled token distribution while mitigating the risk of unauthorized token withdrawals or voiding.Management: Access to critical functions such as `granting` and voiding tokens is restricted to the contract owner, ensuring centralized control over token allocation and management. The contract emits events to track grant, void, and withdrawal actions, providing stakeholders with visibility into token-related activities. Gas-efficient storage techniques, including using a storage gap array, are employed to optimize resource utilization and minimize transaction costs associated with token management operations. |

## Issues surfaced from Attack Ideas

- **Launching a DoS attack on the core protocol.**

- **Exploiting bugs in Merkle proof verification logic.**

- **Exploiting potential bugs in multi-hop bridging, for example, use a multi-hop that contains a loop.**

- **Constructing bridge messages whose hashes collide.**

- **Continuously contesting valid proofs to delay block confirmation.**

- **Exhausting the L1 block proposing ring-buffer to halt the chain.**

- **Exploring bugs in L2's anchor transaction.**


### Time spent:
40 hours