
# Introduction

  

Taiko is a scalable solution for Ethereum that aims to address the high transaction fees on the Ethereum network. It is based on the concept of ZK-Rollups, which are layer 2 scaling solutions that bundle hundreds of transfers off-chain into a single transaction on-chain. This significantly reduces the cost of transactions while maintaining the security and decentralization of the Ethereum network.

  

**Key Features of Taiko:**

 
- Ethereum-equivalent ZK-Rollup: Taiko is fully open-source and permissionless, similar to Ethereum. It aims to provide a seamless user experience, making it feel the same as using Ethereum.

- Based Rollup: Taiko is a based rollup, which means its sequencing is driven by the base L1 (Layer 1). There is no centralized sequencer; instead, Ethereum L1 validators play the role of sequencers.

- Multi-proofs: Taiko uses multi-proofs to ensure the security and integrity of its blocks. This approach involves using multiple proof systems and clients, reducing the risk of bugs or vulnerabilities in any single system.

- Off-chain Prover Market: To incentivize provers to generate proofs, Taiko has a dynamic off-chain proof market where proposers can engage with potential proof service providers. This helps balance costs and optimize network efficiency.

- Bridging: Taiko's bridging mechanism allows for secure cross-chain messaging between Ethereum and Taiko. It utilizes merkle proofs and a signal service to verify messages sent between the two chains, ensuring reliability and security.

- Inception Layers: Taiko is designed to support multiple instances of Taiko running in parallel as L2s, and even has the option to run Taiko on Taiko as an L3. This concept of inception layers enables scalable horizontal scaling for Ethereum.

  

**Conclusion:**

  

Taiko is a promising solution for scaling Ethereum, offering lower transaction fees, scalability, and security. Its innovative features, such as based sequencing, multi-proofs, and inception layers, make it a compelling choice for developers and users looking to optimize their experience on the Ethereum network.

  

# Overview

  ![enter image description here](https://i.imgur.com/MBZDH4P.png)

![enter image description here](https://i.imgur.com/9W0SLii.png)
Structuring the code is crucial for conducting a thorough analysis of the code base. This enables auditors to predict the level of contract difficulty, identify critical contracts, and determine security-critical features such as payment functions or assembly usage. Additionally, this approach accurately measures the time required to perform a detailed audit and helps determine the cost of a project audit. To achieve efficiency, clarity, and improvements, it is essential to have a comprehensive view of the entire architecture. This enables the identification of the basic structure, relationships between modules, and key design patterns. By understanding the big picture, we can analyze the complexity of the code and reveal its strengths and potential for improvement with confidence.

  

Taiko is a tier-based rollup network designed to run on top of the Ethereum Mainnet. As a Base rollup, all

proposing and proving is performed on Ethereum, through the use of smart contracts.

  

The proof system consists of multiple proof tiers, with each tier expected to be more secure than the last. Taiko

includes a zero-knowledge prover along with optimistic and SGX proof systems. Additionally, there is a centralised guardian proof system, which is the highest tier.

  

The core block processing system Taiko has designed is a native bridge to enable the sending of ETH and ERC20

tokens to and from Taiko L2.

  

Furthermore, this technology can be used recursively, for layer 2 to layer 3 or layer 3 to layer 4 and onwards.

  
  

# Approach to Auditing

  

- We began by thoroughly reviewing and read docs, youtube and articel Taiko procotol the provided documentations, as well as reviewing the video provided. Here, we made note of important information, noted down unclear parts and overall tried to fully understand how the protocol should function. We also took notes of integrated and inherited protocols and mapped out possible risk areas.

  

- While we were studying the docs, we had ran static analyzers and linters through the contracts to detect basic vulnerabilities and other non critical errors. The result of our static analysis was then compared to the provided bot reports and those deemed known were removed.

  

- After the documentation review and static analysis, we started the process of manual code inspection. We noted how the contracts were divided into different modules and we inspected the contracts in each module carefully. We stuidied each of the contracts, tested how each function behaves and compared that to how they're expected to behave. We then tried out various attack ideas, including the ones provided by the sponsors. We noted the dependencies, inheritancies, and possible vulnerabilities that can arise from them. We made comparisons to issues found in protocols of the same kind (including older commits) to see if the same mistakes were repeated and how effective the provided fixes were.

  

After this was done, we made notes on the issues we found and prepared the analysis report.

  

# Codebase quality

  

Overall, I consider the quality of the Taiko codebase to be excellent. The code appears to be very mature and well-developed. We have noticed the implementation of various standards adhere to appropriately. Details are explained below:

  

Strengths :

Exemplary unit test coverage: The codebase shines with its meticulous unit testing strategy. The comprehensive suite of unit tests ensures the reliability and resilience of the system's core functionality, providing confidence in its performance under various scenarios.

  

Artful integration of Natspec: A commendable strength is the thoughtful integration of Natspec. The use of this documentation format not only improves code readability, but also exemplifies a commitment to providing clear and human-friendly documentation that fosters a more collaborative and accessible development environment.

  

Weaknesses :

Opportunities to improve documentation: While the codebase stands out in many ways, there is an opportunity for refinement in the documentation. Addressing this area of improvement can increase the overall clarity of the codebase, make it more accessible, and facilitate seamless collaboration among developers. In essence, the codebase demonstrates proficiency in testing methodologies and documentation practices. Strengthening the documentation further would strengthen the codebase's comprehensibility and contribute to an even more polished and developer-friendly ecosystem.

  

# Analysis of the code base and diagram architecture

  

## AutomataDcapV3Attestation

  ![enter image description here](https://i.imgur.com/CbRnl4t.png)

Part of the system for verifying and checking data generated from various security-related processes on Intel SGX-based devices.

  

### verifyAttestation(bytes calldata data) external view override returns (bool)

  

verify attested data. ensure that the data comes from a trusted source and has not been altered during transmission.

  

### verifyParsedQuote(V3Struct.ParsedV3QuoteStruct calldata v3quote) external view override returns (bool, bytes memory)

  

verify parsed data. validate information in the quote, including QE identity, TCB status, and data integrity.

  

### configureTcbInfoJson(string calldata fmspc, TCBInfoStruct.TCBInfo calldata tcbInfoInput) public onlyOwner

  

configure TCB (Trusted Computing Base) information. add or update TCB information to be used in the verification process.

  

### configureQeIdentityJson(EnclaveIdStruct.EnclaveId calldata qeIdentityInput) external onlyOwner

  

configure QE (Quoting Enclave) identity. add or update QE identity information to be used in the verification process.

  

### toggleLocalReportCheck() external onlyOwner

  

enable or disable local report checking. decide whether reports from the local enclave should be verified or not.

  

### setMrSigner(bytes32 _mrSigner, bool _trusted) external onlyOwner

  

set whether an MR Signer (Measurement Report Signer) is trusted or not. control access to specific functions based on the MR Signer.

  

### setMrEnclave(bytes32 _mrEnclave, bool _trusted) external onlyOwner

  

set whether an MR Enclave (Measurement Report Enclave) is trusted or not. control access to specific functions based on the MR Enclave.

  

### addRevokedCertSerialNum(uint256 index, bytes[] calldata serialNumBatch) external onlyOwner

  

add revoked certificate serial numbers for a specific index. manage revoked certificates for the verification process.

  

### removeRevokedCertSerialNum(uint256 index, bytes[] calldata serialNumBatch) external onlyOwner

  

remove revoked certificate serial numbers for a specific index. manage revoked certificates for the verification process.

  

## Bridge

![enter image description here](https://i.imgur.com/EBPssRq.png)


Bridge enables users to send messages from one blockchain to another securely and verifiably.

  

-  **sendMessage**: send messages from one blockchain to another. This function validates the message, sends a signal to indicate that the message has been sent, and emits an event to notify that the message has been sent.

  

-  **recallMessage**: cancel a previously sent message if the message has not been executed. This function validates the message status and processes the message cancellation if eligible.

  

-  **processMessage**: Used to process messages received from another blockchain. This function validates the message, processes the message by calling functions on the target contract, and returns a refund value if applicable.

  

-  **retryMessage**: retry sending a previously failed message, as long as the message is still in a retryable status. This function validates the message status and, if eligible, attempts to resend the message.

  

-  **banAddress**: ban or unban specific addresses from sending or receiving messages. This function helps manage network security and integrity.

  

-  **suspendMessages**: suspend or unsuspend specific messages. This function helps manage the delivery of messages deemed risky or unsafe.

  
  

## Basefee Calculation
![enter image description here](https://i.imgur.com/HDA5bXI.png)
  

## Data BlockMetadata
![enter image description here](https://i.imgur.com/RQhy8Yt.png)
  

## Multi-hop Cross-chain Bridging:

  ![enter image description here](https://i.imgur.com/CP55rFn.png)

## Synchronization
![enter image description here](https://i.imgur.com/j1gUdr0.png)
  

## Multi Hop Bridging

  ![enter image description here](https://i.imgur.com/nqyI2jU.png)
  
  
## One-Hop Bridging
![enter image description here](https://i.imgur.com/yKgTTCo.png)

##  Caching 

![enter image description here](https://i.imgur.com/tCbOHpy.png)


## Bridge

  

**Timestamp Manipulation:** The `getInvocationDelays` function has different delay times for different networks, but it does not check if the current network is the expected network. An attacker could potentially manipulate the timestamp and call the `getInvocationDelays` function to receive a different invocation delay time.

  

**Access Control:** The `retryMessage` function requires the caller to be the `message.destOwner` when the `message.gasLimit` is zero or when the function is called in the last attempt. However, this check is not performed in the `processMessage` function, which could allow an attacker to execute the message with zero gas and bypass the access control check.

  

**Integer Overflow/Underflow:** The `recallMessage` function uses the unchecked keyword when calculating the invocation delay, which could allow for an integer overflow/underflow attack. An attacker could potentially create a message with a large invocationDelay value, causing the `if (block.timestamp >= invocationDelay + receivedAt)` condition to evaluate to false, allowing the attacker to execute the message immediately.

  

**Possible DOS:** The `sendMessage` function checks if the expected amount of Ether is provided in the message, but it does not check if the message fee is sufficient. An attacker could potentially create a large number of messages with zero or low fees, which could cause the contract to become unresponsive and create a denial of service (DoS) attack. This vulnerability can be mitigated by implementing a minimum fee for message creation.

  

**Possible Reentrancy:** An attacker could potentially exploit this by manipulating the `gasLimit` parameter or by calling external contracts that could reenter the `processMessage` or `recallMessage` functions.

  

```solidity

Bridge.sol

417: function getInvocationDelays()

418: public

419: view

420: virtual

421: returns (uint256 invocationDelay_, uint256 invocationExtraDelay_)

422: {

```

  
  

# Systemic Risks

  

## Centralization Concerns

One of the systemic risks associated with Taiko is the potential for centralization. Although the protocol is designed to be decentralized, there is a risk that certain entities or groups may assert enough influence to influence governance decisions or control large portions of the network.

  

## Smart Contract Risk

Another systemic risk lies in smart contract vulnerabilities. Despite careful testing and auditing, smart contracts are not immune to bugs or vulnerabilities, which can cause network disruptions or loss of user funds.

  
  

# Technical risks

  

## Scalability

One of the key technical risks for Taiko is scalability. While the protocol aims to reduce transaction costs on Ethereum, scalability to accommodate a large number of users and transactions without compromising security or decentralization is a complex challenge.

  

## Security Threats

Security threats, such as 51% attacks or exploits targeting vulnerabilities in the protocol or its underlying technology, pose a significant risk to the integrity of Taiko and the funds stored within the network.

  

## Performance and Efficiency

Maintaining high performance and efficiency is crucial for user experience. Technical issues related to network congestion, transaction processing speed, or data storage can impact the usability and appeal of the Taiko protocol.

  

# Integration risks

  

## Ecosystem Support

Taiko's success depends on the support of its ecosystem. Risks related to developer adoption, community engagement, and ecosystem growth can impact the long-term sustainability of the protocol.

  

# Admin abuse risks

  

## AutomataDcapV3Attestation

Unauthorized Modifications: An admin could make unauthorized modifications to the contract's state, such as changing trusted user mappings (_trustedUserMrEnclave and _trustedUserMrSigner) or altering TCB information (tcbInfo).

  

Revocation List Manipulation: Admins could misuse their privileges to manipulate the revocation list (_serialNumIsRevoked), adding or removing certificates from the list improperly.

  

Configuration Tampering: Admins could tamper with the configuration of the contract, such as toggling the local report check (_checkLocalEnclaveReport) or modifying the TCB information configuration (configureTcbInfoJson).

  

Identity Impersonation: Admins could impersonate identities by setting MR_SIGNER and MR_ENCLAVE values (setMrSigner and setMrEnclave) incorrectly, leading to false trust relationships.

  

False Attestation: Admins could falsely attest to the validity of data by manipulating the verification process, potentially allowing malicious actors to gain unauthorized access.

  

## Bridge

### Message Status Manipulation

Admins can unfairly change the status of messages that have been sent, received, or processed by the contract. This can result in unfair delivery or processing of messages that do not comply with the established rules.

  

### Service Termination

Admins can use their authority to terminate contract services without clear reasons or for personal gain. This can disrupt the flow of messages between two blockchains and harm users relying on contract services.

  

### Address Blocking

Admins can exploit their authority to prohibit certain addresses from sending or receiving messages. This can be used to limit access or harm users unfairly.

  

### Fund Return Manipulation

Admins can manipulate the process of returning funds that should be given to users if messages fail to be processed correctly. This can result in fund loss or unfairness in the return process.

  

### Call Context Manipulation

Admins can manipulate the call context stored in the contract to alter the execution flow of certain messages. This can result in unfair execution or harm to involved users.

  

### Abuse of Confidential Information

Admins can use confidential or sensitive information they possess for personal gain or to harm others. This can damage user trust in the contract and result in financial or reputational losses.

  

### Recommendations

  

-  **Multi-Signature Approvals:** Require multiple admins to approve critical actions, such as modifying trusted user mappings or revocation list entries. This adds an additional layer of security and oversight.

-  **Logging:** Implement logging to record admin actions, including changes to contract state and revocation list modifications. This can help in detecting and investigating potential abuses.

-  **Role-Based Access Control:** Use RBAC to limit admin privileges based on their roles. Only grant permissions necessary for their specific responsibilities.

-  **Monitoring:** Monitor contract activities and system logs for unusual or suspicious behavior, which may indicate potential abuse.

-  **Transparency:** Maintain transparency regarding administrative actions and their justifications. Ensure that admins are accountable for their actions.

### Time spent:
23 hours