


## Introduction

Taiko is a fully open-source, permissionless, Ethereum-equivalent ZK-Rollup designed to make Ethereum transactions cheaper while maintaining its core properties of censorship resistance, permissionlessness, and security. The protocol aims to extend Ethereum's properties through two innovative approaches: the Based Contestable Rollup, which is a configurable rollup to reduce transaction fees, and the Based Booster Rollup, an approach to native L1 scaling. Taiko's governance is embedded within its smart contracts, ensuring that all operations are run permissionlessly by the community.

### Some key innovative aspects:

 - Ethereum-Equivalent: Taiko aims to be a Type 1 (Ethereum-equivalent) ZK-EVM, providing a seamless developer experience by maximizing compatibility with Ethereum.
 - Organizations: The Taiko ecosystem includes Taiko Labs for R&D, Taiko Treasury funded by protocol income, Taiko DAO for governance, Taiko Foundation for stewarding growth and development, and Taiko Security Council for emergency actions and protocol safety.
 - Products and Infrastructure: Taiko Labs operates a range of frontends, non-critical backend infrastructure, critical backend infrastructure, and open-source software, including Taiko protocol smart contracts, Taiko geth, Taiko client, Raiko client, and Simple Taiko node.
 - Open Source: The protocol's code is open source, available on GitHub, and can be freely used and modified under a permissive license. 
 - Decentralization: Taiko operates on a decentralized and permissionless model, allowing anyone to participate as nodes, proposers, and provers.

## System Overview

 ### Scope in High Priority

- **BridgedERC20.sol** The contract is an upgradeable ERC20 token that represents tokens bridged from another chain. It leverages OpenZeppelin's upgradeable contracts for ERC20 functionality, including snapshots and voting capabilities. The contract introduces a special role called "snapshooter" that can take snapshots of the token's state.

- **TaikoToken.sol** The TaikoToken (TKO) is an ERC20 token with 18 decimal places of precision, used for prover collateral in the form of bonds within the Taiko protocol. It is labeled in AddressResolver as "taiko_token".

- **TaikoL1.sol** The TaikoL1 contract serves as the "base layer contract" of the Taiko protocol, providing functionalities for proposing, proving, and verifying blocks. It can be deployed on L1 or L2s to create L3 "inception layers". The contract also handles the deposit and withdrawal of Taiko tokens and Ether, with Ether deposited to L2 being held by the Bridge contract.

- **TaikoGovernor.sol** The TaikoGovernor contract is designed to manage governance decisions within the Taiko protocol. It leverages OpenZeppelin's upgradeable governance contracts to provide a robust framework for proposing, voting on, and executing governance proposals. The contract is upgradeable, allowing for future improvements and security patches.

- **TaikoTimelockController.sol** The TaikoGovernor contract is designed to manage governance decisions within the Taiko protocol. It leverages OpenZeppelin's upgradeable governance contracts to provide a robust framework for proposing, voting on, and executing governance proposals. The contract is upgradeable, allowing for future improvements and security patches.

- **TaikoL2.sol** TaikoL2 contract is designed to handle cross-layer message verification and manage EIP-1559 gas pricing for Layer 2 (L2) operations. It anchors the latest L1 block details to L2 for cross-layer communication, manages EIP-1559 parameters for gas pricing, and stores verified L1 block information.

- **AddressManager.sol** The AddressManager contract is designed to manage a mapping of (chainId, name) pairs to Ethereum addresses. It provides a way to set and retrieve addresses associated with specific chain IDs and names, facilitating the management of addresses across different blockchain networks.

- **SignalService.sol** The SignalService contract is designed to facilitate secure cross-chain message passing, leveraging merkle proofs for signal verification. It supports sending signals, syncing chain data, and verifying signals received on target chains. This contract is crucial for maintaining secure and reliable communication across different blockchain networks.

- **Bridge.sol** The Bridge contract is designed to facilitate cross-chain communication by sending, recalling, and processing messages between different blockchain networks. It leverages the ISignalService to send signals indicating message sending, and it includes mechanisms for suspending messages, banning addresses, and handling message statuses.

- **EssentialContract.sol** The EssentialContract serves as a base class for all proxied contracts, leveraging the UUPS (Universal Upgradeable Proxy Standard) upgrade mechanism from OpenZeppelin. It incorporates Ownable2StepUpgradeable for ownership management, AddressResolver for resolving addresses dynamically, and includes reentrancy protection, pause functionality, and custom error handling.

- **LibDepositing.sol** The LibDepositing library is designed to handle Ether deposits within the Taiko protocol, specifically for depositing Ether to Layer 2. It leverages the TaikoData struct for managing state and configuration, and utilizes IAddressResolver for dynamic address resolution. The library includes core logic for depositing Ether, processing deposits in a batched manner, and encoding deposit information.

- **BridgedERC20Base.sol** The BridgedERC20Base contract is an abstract contract that serves as a base for ERC20 tokens bridged from another blockchain. It provides functionality for token migration, both inbound and outbound, and includes events for tracking migration status changes and token migrations. The contract is designed to work with an EssentialContract and implements the IBridgedERC20 interface, indicating a modular and extensible design.

- **BridgedERC1155.sol** The BridgedERC20Base contract is an abstract contract that serves as a base for ERC20 tokens bridged from another blockchain. It provides functionality for token migration, both inbound and outbound, and includes events for tracking migration status changes and token migrations. The contract is designed to work with an EssentialContract and implements the IBridgedERC20 interface, indicating a modular and extensible design.


## Approach Taken-in Evaluating The Taiko Protocol

I focused on thoroughly understanding the codebase and providing recommendations to improve its functionality. The main goal was to take a close look at the important contracts and how they work together in the Taiko protocol

I start with the following contracts, which play crucial roles in the Taiko protocol:

  **Main Contracts I Looked At**
I start with the following contracts, which play crucial roles in the Taiko protocol:

 |                          |
 |--------------------------|
 | **BridgedERC20.sol** |
 | **TaikoToken.sol** |
 | **TaikoL1.sol** |
 | **TaikoGovernor.sol** |
 | **TaikoTimelockController.sol** |
 | **TaikoL2.sol** |
 | **AddressManager.sol** |
 | **SignalService.sol** |
 | **Bridge.sol** |
 | **EssentialContract.sol** |
 | **LibDepositing.sol** |
 | **BridgedERC20Base.sol** |
 | **BridgedERC1155.sol** |

Address Mappings and Cross-Chain Signals: Efficiently manage address mappings using Solidity's mapping data structure and ensure secure cross-chain signals and data synchronization.
Cross-Layer Communication and Gas Pricing: Manage cross-layer communication and gas pricing efficiently, leveraging EIP-1559 for gas pricing management and OpenZeppelin's SafeERC20 for secure ERC20 token interactions.
Security Best Practices: Incorporate security best practices such as the use of non-reentrant modifiers to prevent reentrancy attacks and custom proposal functions to address specific vulnerabilities.
Modular Design and Libraries: Utilize modular libraries for different functionalities (e.g., proposing, proving, verifying, depositing) to improve code maintainability and readability. This approach also allows for easier updates and modifications in the future.
Access Control and Modifiers: Implement access control mechanisms, such as the onlyOwner and onlyOwnerOrSnapshooter modifiers, to restrict critical functions to authorized users. This enhances security by preventing unauthorized access to sensitive operations.
Use of OpenZeppelin's Upgradeable Contracts: Leverage OpenZeppelin's upgradeable contracts for security and reliability. This ensures that your contract can be upgraded safely without losing state or funds.

## Owner Role:

The Owner role is central to the system, responsible for initializing the contract, setting up initial parameters, and managing critical aspects of the system. This includes:
Setting the snapshooter address and initializing the contract.
Initializing the contract and setting up the initial governance parameters.
Initializing the contract and setting addresses for specific chainId-name pairs.
Initializing the contract and authorizing or deauthorizing addresses for calling syncChainData.
Initializing the contract and managing the contract's state, including suspending messages, banning or unbanning addresses.
Pausing and unpausing the contract, authorizing upgrades, and managing the contract's state.
Changing the migration status and initiating token minting and burning operations.
Snapshooter Role: The Snapshooter role is responsible for taking snapshots of the token's state, ensuring the integrity and security of cross-layer operations.

## Architecture View

Modular Approach: Adopt a modular approach to structure your contracts. This involves inheriting from multiple contracts to add features like snapshots, voting, and governance functionalities. It also includes using separate libraries for different functionalities, such as handling Ether deposits, ensuring maintainability and extensibility.\
Foundation on OpenZeppelin's Upgradeable Contracts: Utilize OpenZeppelin's upgradeable contracts as the foundation for your system. This ensures security, reliability, and the ability to upgrade contracts without losing state or funds. This approach is highlighted across multiple contracts, emphasizing the importance of OpenZeppelin's libraries for building secure and upgradeable smart contracts.
State Management: Implement a state pattern to manage complex state transitions effectively. This is a good practice for managing the contract's state, especially in systems with multiple functionalities and state changes.
Governance Extensions: Utilize a combination of different governance extensions to support various governance functionalities. This includes voting power quorum, timelock control, and compatibility with the Bravo voting system, ensuring a flexible and robust governance mechanism.
Cross-Layer Message Verification and Gas Pricing: Incorporate custom logic for cross-layer message verification and EIP-1559 gas pricing management. This enhances the contract's functionality and efficiency, especially in systems that require cross-layer interactions.
Standardized Contract Interfaces: Implement standardized contract interfaces such as IAddressManager, ISignalService, and IBridge for address management, signal services, and bridges. This ensures adherence to a standardized interface, facilitating integration and interoperability with other contracts or systems.
Dynamic Address Resolution: Integrate AddressResolver for dynamic address resolution, allowing for more flexible contract interactions and enhancing the contract's adaptability to changes.
Token Migration and Events: Include functionality for token migration, both inbound and outbound, and emit events for tracking migration status changes and token migrations. This is crucial for systems that involve token migration across different layers or chains.


## Centralization Risks && Systemic Risk:

### Centralization Risks

The system design inherently minimizes centralization risks by allowing any address to become the snapshooter, assuming the owner grants this role.
The use of OpenZeppelin's upgradeable contracts reduces the risk of centralization since upgrades can be managed by the community through governance mechanisms.
also the  minimizes centralization risks by allowing any address to become the snapshooter, assuming the owner grants this role.
The use of modular libraries and a non-reentrant modifier reduces the risk of centralization by ensuring that the contract's logic is not tightly coupled with external actors.

### Systemic Risk

- Owner's Private Key Compromise: The system's ability to pause block proving, set the snapshooter role, and authorize addresses introduces a systemic risk if the owner's private key is compromised. This risk is mitigated by the contract's design, which restricts critical operations to the owner. However, the security of the owner's private key remains a critical aspect of the system's security 
- Governance Token Voting Power Manipulation: The ability to propose and execute governance proposals introduces a systemic risk if the governance token's voting power is manipulated. This risk is mitigated by the contract's design, which includes mechanisms for voting power quorum and timelock control, ensuring that decisions are made through a fair and secure process
- IP-1559 Gas Pricing Management: The system's reliance on EIP-1559 for gas pricing management introduces a systemic risk if the EIP-1559 mechanism is compromised or if it introduces vulnerabilities. This risk is mitigated by the contract's design, which includes custom logic for cross-layer message verification and gas pricing management, ensuring that gas pricing is handled securely and efficiently
- Dynamic Address Resolution: The library's reliance on the IAddressResolver for dynamic address resolution introduces a systemic risk if the resolver's behavior is manipulated or compromised. This risk is mitigated by the library's design, which relies on the resolver for address resolution rather than hardcoding addresses, enhancing the contract's flexibility and adaptability
- Custom Errors and EssentialContract Base: The contract's reliance on custom errors and the use of an EssentialContract as a base introduces potential systemic risks related to the accuracy of error handling and the security of the base contract. These risks are mitigated by the contract's design, which includes checks for invalid parameters and permissions, ensuring that the contract operates securely and efficiently
- Reliance on External Libraries: The system's reliance on external libraries, such as OpenZeppelin, introduces a systemic risk if those libraries are compromised or if they introduce vulnerabilities. This risk is mitigated by the use of well-audited and community-vetted libraries, but it remains a critical consideration for the overall security of the system

## Codebase Quality

| Codebase Quality Categories | Comments | 
|-----------------------------|----------|
| Code Maintainability and Reliability |  The system is well-structured use OpenZeppelin's upgradeable contracts, which are widely regarded as secure and reliable  and uses modular libraries for different functionalities, enhancing maintainability and reliability. |
| Code Comments | The system includes comments that explain the purpose of functions and variables, enhancing readability and maintainability |
| Documentation | The system  documentation is minimal but sufficient for understanding its basic functionality |
| Code Structure and Formatting | The system is well-organized, with clear separation of concerns and use of modular libraries for functionality. |
| Error Handling | The contract uses custom errors for specific conditions, such as invalid block IDs,unauthorized actionsm, invalid signatures length, invalid parameters and sender, invalid proofs, invalid sender addresses enhancing error handling |

## Gas Optimizations

| Number | Issue | Instences |
|--------|-------|-----------|
|[G-01]| Consider using OpenZeppelin's EnumerateSet instead of nested mappings | 8 |
|[G-02]| Use assembly to emit an event | 55 | 
|[G-03]| Multiple accesses of the same mapping/array key/index should be cached | 18 |
|[G-04]| Using assembly to revert with an error message | 57 |
|[G-05]| Cache storage variables: write and read storage variables exactly once | 15 |
|[G-06]| Using mappings instead of arrays to avoid length checks | 3 |
|[G-07]| Make constructors payable | 3 |
|[G-08]| Custom errors are (usually) smaller than require statements | 57 |
|[G-09]| Use inline assembly to check for address(0) | 67 |
|[G-10]| Do-While loops are cheaper than for loops | 23 |
|[G-11]| Call msg.sender directly instead of caching them | 1 |
|[G-12]| Use uint8 Can Increase Gas Cost | 55 |
|[G-13]| Store Data in calldata Instead of Memory for Certain Function Parameters  | 120 |
|[G-14]| Using bytes32 is cheaper than using string. | 40 |
|[G-15]| Avoid Unnecessary Use of Storage | 5 |
|[G-16]| Precompute Off-Chain When Possible | 35 |
|[G-17]| abi.encode() is less efficient than abi.encodePacked() | 18 |
|[G-18]| Alternative Solady library can be used instead of OpenZeppelin to save gas | 2 |
|[G-19]| Avoid unnecessary public variables | 2 |
|[G-20]| Consider pre-calculating the address of address(this) | 41 |
|[G-21]| Counting down in for statements is more gas efficient | 43 |
|[G-22]| Do not calculate constants | 2 |
|[G-23]| do-while is cheaper than for-loops when the initial check can be skipped | 43 |
|[G-24]| Empty blocks should be removed or emit something | 5 |
|[G-25]| Nesting if-statements is cheaper than using && | 28 |
|[G-26]| Struct can be reordered to fit into fewer storage slots | 9 |
|[G-27]| Use assembly for small keccak256 hashes, in order to save gas | 10 |
|[G-28]| Use assembly in place of abi.decode to save gas | 16 |
|[G-29]| Use assembly to validate msg.sender | 17 |
|[G-30]| Use assembly to write address/contract storage values | 15 |

## Recommendations

Security Audit: Consider conducting a thorough security audit to identify any potential vulnerabilities, especially around the contract owner's ability to authorize addresses.
Governance Mechanism: Implement a governance mechanism for changing the owner role, ensuring that this critical role can be updated by the community in a secure and transparent manner.
Documentation: Enhance the contract's documentation to include more detailed information about the signal management process and security considerations.
Testing: Ensure comprehensive testing, including unit tests, integration tests, and security tests, to validate the contract's functionality and security.




### Time spent:
37 hours