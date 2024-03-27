![Pic](https://code4rena.com/_next/image?url=https%3A%2F%2Fstorage.googleapis.com%2Fcdn-c4-uploads-v0%2Fuploads%2Fx3Q5DdF66oj.0&w=256&q=75)

# Taiko Security Analysis Report

## 1. Overview

Taiko, a Type 1 (Ethereum-equivalent) ZK-EVM, aims for maximum compatibility with Ethereum, providing a seamless experience for developers. Its design prioritizes decentralization, permissionlessness, and security, allowing anyone to participate as nodes, proposers, and provers. Taiko's code is open source, fostering a community-driven development process .

From the security perspective, Taiko emphasizes several core principles to maintain its robustness and reliability. The project places security at the forefront, ensuring that all security assumptions are directly or indirectly enforced by Ethereum itself. This includes maintaining a minimal and robust protocol design that avoids unnecessary changes that could jeopardize Ethereum-equivalence. It also ensures decentralization by having decentralized proposers and provers, ensuring no single party can control transaction ordering or be solely responsible for proving blocks, thereby operating reliably even in adversarial conditions. Moreover, Taiko is committed to permissionlessness, enabling anyone to join or leave the network at any time without causing significant disturbance. By adhering to Ethereum-equivalence, Taiko ensures no changes are made to how Ethereum clients execute bytecode and store data, thereby facilitating a continual alignment with Ethereum's upgrades and contributing to the Ethereum L1 improvements【6†source】.

A detailed code review by Token Metrics reveals Taiko as a highly innovative project. It stands out for its approach to providing a ZK-EVM compatible blockchain that enables Ethereum smart contract code to run without modifications. This innovation addresses the limitations of current ZK-Rollups that are mostly application-specific. Taiko's architecture is robust, supporting the core principles of security, decentralization, and permissionlessness. The code quality is rated highly for its comprehensiveness, maintainability, and test coverage. The project's roadmap indicates a clear path to the mainnet launch expected in early 2024, with several testnets and upgrades planned in the interim. The team behind Taiko comprises active and experienced developers, showcasing a solid commitment to the project's ongoing development. 

### 1.1 Token Metrics Research

| Category      | Percentage Score |
|---------------|------------------|
| Innovation    | 18.18%           |
| Architecture  | 20.00%           |
| Code Quality  | 23.64%           |
| Mainnet       | 9.09%            |
| Usability     | 9.09%            |
| Team          | 10.91%           |
| Total         | 90.91%           |

[Source:https://research.tokenmetrics.com/taiko-code-review/](https://research.tokenmetrics.com/taiko-code-review/)

The evaluation of Taiko, a type-1 ZK-EVM blockchain, based on the review by Token Metrics, breaks down its performance across various dimensions using a percentage score. Here's an overview of how Taiko scored in each category:

- **Innovation:** 18.18%. This high score reflects Taiko's approach to providing an Ethereum-equivalent ZK-EVM, enabling smart contracts to run without any modifications. It underscores the project's unique solution to scalability while maintaining compatibility with Ethereum's ecosystem.

- **Architecture:** 20.00%. The architecture score highlights the project's solid foundation in terms of security, decentralization, and permissionlessness. The detailed and well-explained architecture in the whitepaper demonstrates the project's robustness and commitment to its core principles.

- **Code Quality:** 23.64%. This score indicates the high quality of Taiko's code, characterized by regular updates, extensive testing, and maintainability. The open-source nature of the project and the active involvement of experienced developers contribute to this positive assessment.

- **Mainnet:** 9.09%. Reflecting the project's stage in its development lifecycle, this score indicates progress toward launching the mainnet. With several testnets planned and underway, the project is methodically moving towards its mainnet launch, expected in early 2024.

- **Usability:** 9.09%. Taiko's usability score is tied to its infrastructure compatibility, making it easily integrable with existing EVM-compatible tools and wallets. This ensures a seamless user experience for end customers.

- **Team:** 10.91%. The team score highlights the expertise and active involvement of Taiko's developers. With a solid coding style and senior Git backgrounds, the team's capabilities are well-regarded.

- **Total:** 90.91%. The overall score is a testament to Taiko's promising potential within the blockchain space, indicating a strong performance across innovation, architecture, code quality, and other key metrics.


These insights highlight Taiko's potential to significantly contribute to the Ethereum ecosystem by enhancing scalability, security, and developer experience without compromising the foundational principles that have made Ethereum the leading smart contract platform.


## 2. Scope of Audit

### 2.1 In Scope

```
packages/protocol/contracts/common/IAddressManager.sol
packages/protocol/contracts/common/AddressManager.sol
packages/protocol/contracts/common/IAddressR.sol
packages/protocol/contracts/common/AddressR.sol
packages/protocol/contracts/common/EssentialContract.sol
packages/protocol/contracts/libs/Lib4844.sol
packages/protocol/contracts/libs/LibAddress.sol
packages/protocol/contracts/libs/LibMath.sol
packages/protocol/contracts/libs/LibTrieProof.sol
packages/protocol/contracts/L1/gov/TaikoGovernor.sol
packages/protocol/contracts/L1/gov/TaikoTimelockController.sol
packages/protocol/contracts/L1/hooks/IHook.sol
packages/protocol/contracts/L1/hooks/AssignmentHook.sol
packages/protocol/contracts/L1/ITaikoL1.sol
packages/protocol/contracts/L1/libs/LibDepositing.sol
packages/protocol/contracts/L1/libs/LibProposing.sol
packages/protocol/contracts/L1/libs/LibProving.sol
packages/protocol/contracts/L1/libs/LibUtils.sol
packages/protocol/contracts/L1/libs/LibVerifying.sol
packages/protocol/contracts/L1/provers/GuardianProver.sol
packages/protocol/contracts/L1/provers/Guardians.sol
packages/protocol/contracts/L1/TaikoData.sol
packages/protocol/contracts/L1/TaikoErrors.sol
packages/protocol/contracts/L1/TaikoEvents.sol
packages/protocol/contracts/L1/TaikoL1.sol
packages/protocol/contracts/L1/TaikoToken.sol
packages/protocol/contracts/L1/tiers/ITierProvider.sol
packages/protocol/contracts/L1/tiers/DevnetTierProvider.sol
packages/protocol/contracts/L1/tiers/MainnetTierProvider.sol
packages/protocol/contracts/L1/tiers/TestnetTierProvider.sol
packages/protocol/contracts/L2/CrossChainOwned.sol
packages/protocol/contracts/L2/Lib1559Math.sol
packages/protocol/contracts/L2/TaikoL2.sol
packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol
packages/protocol/contracts/signal/ISignalService.sol
packages/protocol/contracts/signal/ISignalService.sol
packages/protocol/contracts/signal/LibSignals.sol
packages/protocol/contracts/signal/SignalService.sol
packages/protocol/contracts/bridge/IBridge.sol
packages/protocol/contracts/bridge/Bridge.sol
packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol
packages/protocol/contracts/tokenvault/BridgedERC20.sol
packages/protocol/contracts/tokenvault/BridgedERC20Base.sol
packages/protocol/contracts/tokenvault/BridgedERC721.sol
packages/protocol/contracts/tokenvault/BridgedERC1155.sol
packages/protocol/contracts/tokenvault/BaseNFTVault.sol
packages/protocol/contracts/tokenvault/BaseVault.sol
packages/protocol/contracts/tokenvault/ERC1155Vault.sol
packages/protocol/contracts/tokenvault/ERC20Vault.sol
packages/protocol/contracts/tokenvault/ERC721Vault.sol
packages/protocol/contracts/tokenvault/IBridgedERC20.sol
packages/protocol/contracts/tokenvault/LibBridgedToken.sol
packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol
packages/protocol/contracts/thirdparty/optimism/Bytes.sol
packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol
packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol
packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol
packages/protocol/contracts/thirdparty/optimism/trie/SecureMerkleTrie.sol
packages/protocol/contracts/thirdparty.sol
packages/protocol/contracts/verifiers/IVerifier.sol
packages/protocol/contracts/verifiers/GuardianVerifier.sol
packages/protocol/contracts/verifiers/SgxVerifier.sol
packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol
packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol
packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol
packages/protocol/contracts/team/airdrop/MerkleClaimable.sol
packages/protocol/contracts/team/TimelockTokenPool.sol
packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol
packages/protocol/contracts/automata-attestation/interfaces/IAttestation.sol
packages/protocol/contracts/automata-attestation/interfaces/ISigVerifyLib.sol
packages/protocol/contracts/automata-attestation/lib/EnclaveIdStruct.sol
packages/protocol/contracts/automata-attestation/lib/interfaces/IPEMCertChainLib.sol
packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol
packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol
packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol
packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol
packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol
packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol
packages/protocol/contracts/automata-attestation/utils/RsaVerify.sol
packages/protocol/contracts/automata-attestation/utils/SHA1.sol
packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol
packages/protocol/contracts/automata-attestation/utils/X509DateUtils.sol
```

### 2.2. Out of Scope

> All files outside of packages/protocol/contracts are out of scope.


## 3. Architecture

The architecture of Taiko, as a Type 1 (Ethereum-equivalent) ZK-EVM, is meticulously designed to align with Ethereum's principles while enhancing its scalability, security, and developer experience. At the core, Taiko integrates several key components, principles, and strategies to achieve its goals, which are outlined below:

### 3.1. L1 Protocol Connections

The Layer 1 (L1) protocol connections facilitate communication between the L2 rollup node and Ethereum's main chain. This includes submitting proofs generated by the L2 rollup node to Ethereum for verification and finality, ensuring the security and integrity of transactions processed on Taiko.

### 3.2. L2 Rollup Node

The Layer 2 (L2) rollup node in Taiko manages the rollup chain, which aggregates transactions into batches, generating proofs of their correctness. This mechanism significantly reduces the on-chain footprint by compressing multiple transactions into a single proof, enhancing scalability.

### 3.3. L1 Protocol Connections

The Layer 1 (L1) protocol connections facilitate communication between the L2 rollup node and Ethereum's main chain. This includes submitting proofs generated by the L2 rollup node to Ethereum for verification and finality, ensuring the security and integrity of transactions processed on Taiko.

### 3.4. Decentralized and Permissionless Participation

In keeping with Ethereum's decentralized ethos, Taiko allows for decentralized and permissionless participation. Nodes, proposers, and provers can participate without centralized control, ensuring a wide and resilient network.

### 3.5. Security and Ethereum Equivalence

Security is a paramount concern in Taiko's architecture. The platform ensures that all security assumptions are either directly or indirectly enforced by Ethereum's own security mechanisms. By adhering strictly to Ethereum equivalence, Taiko ensures that it inherits Ethereum's security properties and upgrades.

### 3.6. Minimal and Robust Protocol Design

Taiko's protocol design is both minimal and robust, avoiding unnecessary changes that could compromise compatibility with Ethereum. This design philosophy ensures that Taiko remains closely aligned with Ethereum's upgrades and ecosystem.

### 3.7. Continual Ethereum Equivalence

Taiko's commitment to Ethereum equivalence is not just a static goal but a continual process. This means that Taiko not only matches Ethereum's current state but also aims to adopt future Ethereum upgrades, ensuring long-term compatibility and co-evolution.

### 3.8. Scalability Without Compromise

Through its ZK-EVM and rollup-based architecture, Taiko addresses the classic blockchain trilemma, offering scalability without sacrificing decentralization or security. This allows Ethereum to scale effectively, accommodating more transactions and reducing costs for users.

Taiko's architecture represents a thoughtful blend of innovation, security, and Ethereum compatibility, aiming to enhance the scalability and efficiency of the Ethereum ecosystem while preserving its foundational principles.

## 4. Approach

I did a manual line by line codebase review of the Taiko protocol's smart contracts. I deeply engaged with the code to identify vulnerabilities and areas for improvement, focusing solely on manual inspection techniques. This hands-on approach not only enhances the security and efficiency of the protocol but also serves as a valuable learning experience, enriching my understanding of smart contract best practices and complex blockchain interactions. You can find a high-level analysis of my findings down below.


## 5. Type 1 zkEVM inherent Risks


### 5.6 Proof Generation Cost
    
The complexity and computational intensity required to generate proofs, especially in a multi-proof system where different types of proofs are integrated, can lead to significant delays. This not only affects the speed of transaction verification but also impacts the overall throughput of the blockchain.

For example proposers can submit maliciously crafted blocks that that are cheap in gas but really expensive to generate proofs effectively leading to Dos of the system for other users.

### 5.7 Upgradability Concerns

Taiko being Type 1 based rollups has both upsides and downsides. It enjoys the security and finality of Ethereum but also suffers when it comes to being able to add features that could be overall beneficial for the protocal in serving it's purpose.

### 5.8 Scalability Concerns

The scalability benefits Taiko can offer are inherently tied to Ethereum's throughput capabilities. If Ethereum faces scalability issues, it directly impacts Taiko’s performance.

### 5.9 Proof Submission and Verification Delays

Fluctuations in Ethereum gas prices and network congestion can cause delays in the submission and verification of proofs on the Ethereum blockchain. High gas prices may disincentivize provers from submitting proofs promptly, leading to delays in block verification and finality.

## 6 SGX Risks and Side Channel Attacks

Dependence on Intel's SGX for a portion of the proof generation introduces some risks. If vulnerabilities in SGX are exploited or if there are hardware failures, it could lead to a temporary unavailability of this proof mechanism.

### 6.1. Cryptographic Primitives and Protocols

Exploitation of cryptographic vulnerabilities can undermine the security of communication and data within Taiko, leading to the exposure of sensitive information or enabling unauthorized transactions. Local attackers might exploit enclave state retention to brute-force encryption keys or misuse cryptographic protocols to compromise data integrity and confidentiality.

Use up-to-date, well-researched cryptographic primitives and avoid custom or non-standard implementations.

### 6.2. Page Table Attacks

By manipulating page tables to cause or observe page faults, an attacker could infer the pattern of memory accesses made by the SGX enclave running Taiko's proof generation code. This could potentially allow them to deduce sensitive information, such as private keys or the details of transactions before they are publicly committed to the blockchain. Even if the specific content cannot be directly accessed due to SGX's encryption, the access patterns alone might reveal enough information to compromise privacy or security.

### 6.3. Segmentation Attacks

If Taiko's SGX-enclave is implemented on systems still using x86 segmentation attackers could exploit this to gain even finer-grained insights into the enclave's memory access patterns, further compromising the security of the data processed within.

### 6.4. DRAM Vulnerabilities

DRAM-based attacks could similarly allow attackers to observe and infer patterns of memory access outside of the CPU cache, albeit with less precision. This could compromise the integrity of the proof generation process by leaking information about which parts of memory are accessed more frequently, potentially revealing sensitive computation patterns or data.


### 6.5. Cache Timing Attacks

Implement cache partitioning or cache randomization techniques to reduce the predictability of cache access patterns, making it more difficult for attackers to perform timing analysis.

Where possible, use algorithms designed to execute in constant time, regardless of input data. This approach minimizes the data-dependent variations in execution time that can be exploited through cache timing attacks.

### 6.6. Branch Prediction Attacks / Speculative Execution

Speculative execution vulnerabilities can allow attackers to bypass security boundaries within the CPU, potentially leading to unauthorized access to sensitive data processed within the enclave.

These sophisticated attacks can reveal detailed execution patterns within the SGX enclave by exploiting the processor's branch prediction mechanism. By monitoring mispredicted branches or the execution of speculative instructions, an attacker could infer sensitive details about the operations being performed within the enclave, such as the processing of transactions or the generation of cryptographic proofs.

This could not only compromise the privacy of transactions but also allow for more sophisticated attacks that could, for example, aim to influence the execution of code within the enclave in a way that could be beneficial to the attacker, such as by causing certain transactions to be prioritized or manipulated before being committed to the blockchain.

Leverage CPU microcode updates and SGX SDK features designed to limit the impact of speculative execution. This could involve disabling or restricting speculative execution for sensitive code paths.

## 7. Centralization Risks

### 7.1. Cenralization Risks in Prover Markets

If a small number of provers or prover pools come to dominate the market, it could lead to periods where proof generation is effectively controlled by these entities. This centralization risk might result in unavailability or delays in proof generation during critical periods.

> A Taiko prover needs to be able to generate both SGX and ZK proofs at the moment. We are not distributing TTKOk as we are reworking the SGX registration process to occur fully onchain.

### 7.2. Centralization Risks In Inception Layers

The reliance on specific technologies or infrastructures for managing the inception layers could lead to centralization risks, particularly if certain aspects of the system are controlled by a limited set of actors or if there is a heavy reliance on specific service providers for cross-layer communication.

### 7.3. Financial Barrier to Entry Due to High Stakes

The requirement to post substantial bonds may deter smaller participants from engaging in the proof and contestation process, potentially limiting the system to wealthier participants and centralizing validation power.

## 8. Cross Chain Replay Attacks

There's a risk that signals or transactions valid on one chain could be replayed on another, especially if nonce or identifier mechanisms aren't properly implemented or synchronized between chains.

## 9. Liquidity Risks and Pool Exploitation

Bridging mechanisms that rely on liquidity pools (for token swaps or asset bridging) could be susceptible to liquidity depletion, manipulation, or exploitation through complex attack vectors.

Maintaining robust liquidity management practices, including dynamic fee adjustments, liquidity provider incentives, and implementing security measures to prevent pool draining attacks.

## 10. Governance and Upgrade Risks

The processes for upgrading smart contracts or changing bridge parameters could be exploited to introduce vulnerabilities or malicious functionality. requiring multi-signature or DAO approval for critical changes, and time-locking upgrades to allow community review.

## 11. Cross-Chain Data Consistency

Ensuring data consistency and state synchronization across chains, especially in the face of reorgs or chain splits, presents a significant challenge. Implementing robust chain reorganization handling logic, checkpointing, and cross-chain state validation mechanisms to ensure consistency.

## 12. Cost Implications

### 12.1. Layered Rollups

Operating and maintaining multiple rollups could lead to increased costs, both in terms of transaction fees for users as they move assets or messages across layers and operational expenses for maintaining the infrastructure of each layer.

### 12.2. Variable Costs

Ethereum’s gas fees can be highly volatile, subject to market demand. Since Taiko relies on Ethereum for sequencing, the costs of using Taiko can fluctuate significantly, which might deter users during peak periods.

### 12.3. Economic Dependence

The economic model of Taiko is closely linked to Ethereum's, making it vulnerable to changes in Ethereum's fee market or gas pricing mechanisms.

## 13. Latency in Cross-Layer Transactions

While arbitrary message passing enables communication across layers, it also introduces latency. Transactions involving multiple layers might face delays as they wait for confirmation across the stack, potentially impacting applications requiring high throughput or real-time interactions.

A table summarizing the latency, cost, and delivery methods for L1 to L2 and L2 to L1 transactions:

| Direction | Latency    | Cost                                     | Delivery Method                     |
|-----------|------------|------------------------------------------|-------------------------------------|
| L1 → L2   | ~3 minutes | ~110,000 L1 gas + ~440,000 L2 gas        | Manual and automatic delivery supported |
| L2 → L1   | ~4 minutes | ~129,000 L2 gas + ~440,000 L1 gas        | Manual and automatic delivery supported |

[source:https://www.rollup.codes/taiko#opcodes](https://www.rollup.codes/taiko#opcodes)

*Note: Might have changed since post was published.*

 
## 14. Griefing Attack Risks

### 14.1 Griefing Attacks Via Contests

A bad actor could intentionally contest blocks without valid reasons, forcing honest provers to expend additional resources to re-prove blocks at a higher tier. This not only wastes computational resources but also creates unnecessary delays in the validation process. Such griefing attacks could be aimed at increasing the operational costs for competitors or simply to disrupt the normal operation of the blockchain.

### 14.2 Computational Resource Depletion

Repeatedly forcing blocks to be re-proven at higher tiers could lead to significant computational resource depletion. Malicious actors might target this aspect to drain the resources of honest provers, particularly in systems where computational resources are a limiting factor. This could result in honest provers withdrawing from the process, reducing the network’s security and resilience.

## 15. Economic Exploitation

If the economic incentives are not carefully balanced, bad actors might find ways to exploit the proof tier selection process for profit. For example, if the rewards for proving higher-tier blocks are disproportionately high, provers might be incentivized to contest blocks without valid grounds, aiming to re-prove them at a higher tier for greater rewards. This could lead to a scenario where the system is gamed for financial gain at the expense of network efficiency and trust.

Ensure that the economic incentives for contesting and re-proving blocks are balanced to discourage exploitation.

## 15.1. Influencing Tier Skipping/Delay for Potentially Malicious Blocks

The significant financial risks associated with contesting proofs might discourage participants from challenging proofs, even when valid, promoting a more conservative approach that could allow incorrect proofs to remain unchallenged.

## 15.2. Dependency on Monetary Incentives

The system heavily relies on financial incentives, which might not always align with the broader goals of truth and integrity within the blockchain, potentially leading to decisions driven more by profit than accuracy.

## 16. Denial of Service Risks

### 16.1. Complexity in Verifying Merkle Proofs 

The process of verifying Merkle proofs requires hashing operations that could become computationally expensive if the tree depth is large or if proofs are crafted to be inefficient on purpose. An attacker could exploit this by submitting claims with such proofs, potentially leading to high gas costs or even exceeding block gas limits, making it difficult or impossible for legitimate claims to be processed.

### 16.2. Maliciously Crafted Proofs

If an attacker can influence the structure of the proofs or flood the contract with expensive-to-verify claims, it might deplete the gas limit of blocks or significantly increase the cost for legitimate users to submit their claims. This can be mitigated by imposing limits on the proof size or depth and rejecting claims with proofs exceeding these limits. 


## Findings

| Severity | Findings          |
|----------|-------------------|
| Critical | 0                 |
| High     | 1                 |
| Medium   | 4                 |
| Low      | 24                 |
| Gas      | 8                 |
| NC      | 2                 |


## Time Spent: 120 hours

### Time spent:
120 hours