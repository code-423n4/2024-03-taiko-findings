# 🛠️ Taiko
**A based rollup -- inspired, secured, and sequenced by Ethereum.**

## Conceptual overview of the project:
The Taiko protocol is designed as an advanced Layer 2 (L2) solution for Ethereum, aiming to extend Ethereum's scalability, security, and decentralization. Its unique architecture is built upon the principles of Based Contestable Rollup (BCR), providing a novel approach to handling transactions, state transitions, and inter-layer communications. The protocol leverages several core mechanisms to ensure efficient operation, seamless user interaction, and robust security.

### Architecture and Functionalities:
Taiko introduces a multi-tiered rollup strategy, operating directly atop Ethereum's Layer 1 (L1) and capable of deploying further Taiko instances as Layer 3 (L3), essentially enabling horizontal scalability. This structure allows each layer to maintain its own state while synchronizing with the L1 state, thus ensuring data integrity and security without compromising scalability.

Central to Taiko's design is the Based Contestable Rollup (BCR) architecture, which employs a unique contestation mechanism to ensure the integrity of state transitions. This is achieved through a process where proposed blocks can be contested by the community, with economic incentives designed to encourage honest participation and penalize incorrect submissions. This process relies heavily on cryptographic proofs and the use of Merkle proofs for efficient and secure cross-chain communication.

<br/>

[![Screenshot-from-2024-03-27-14-19-25.png](https://i.postimg.cc/yWqZXSnP/Screenshot-from-2024-03-27-14-19-25.png)](https://postimg.cc/N24FQF39)


## Main Functionality of Protocol
Following is the main functioclity of the protocol ordered by significance and impact.

1. **State Transition Verification with Merkle Proofs**: At the heart of Taiko's operational integrity is the state transition verification mechanism. Leveraging Merkle proofs, it ensures that state changes across its layered architecture are accurately and securely validated. This functionality underpins the trust and security model of Taiko, allowing for decentralized verification of state changes without compromising scalability.

2. **Cross-Chain Communication and Signal Service**: Essential for interoperability within Taiko's ecosystem, the Signal Service facilitates secure and efficient communication between different layers (L1, L2, L3) and instances of Taiko. This service manages the emission, recording, and verification of signals across chains, crucial for asset bridging and maintaining coherence across the network.

3. **Decentralized Rollup Operation (Based Contestable Rollup - BCR)**: Taiko introduces a novel rollup mechanism where state transitions can be contested, ensuring the network's integrity through community-driven checks and balances. This approach not only enhances security but also aligns with the decentralized ethos of blockchain technology by allowing participants to challenge and verify state changes.

4. **Token Bridging and Asset Management**: Facilitating the seamless transfer and management of assets across Taiko's multi-layered ecosystem, this functionality includes smart contracts and mechanisms for locking, minting, and burning tokens as they move between layers. It's critical for enabling a fluid user experience and asset interoperability within Taiko and with external chains.

5. **Ethereum-Equivalence and EVM Compatibility**: By maintaining compatibility with Ethereum's Virtual Machine (EVM), Taiko ensures that developers can easily migrate existing Ethereum dApps to Taiko's network without significant modifications. This feature is pivotal for fostering adoption and facilitating a rich ecosystem of applications on Taiko.

6. **Governance through Decentralization**: Implementing a token-based governance model, Taiko empowers TKO token holders to participate in crucial decision-making processes, such as protocol upgrades and parameter adjustments. This functionality is key to ensuring that Taiko remains adaptive, community-driven, and aligned with the interests of its stakeholders.

## 1): State Transition Verification with Merkle Proofs:
State Transition Verification within Taiko leverages Merkle Proofs to ensure the integrity and security of transitions between states across its network. This mechanism is a cornerstone of Taiko's architecture, providing a decentralized and efficient method for validating state changes without requiring the full transaction data. By utilizing cryptographic proofs, Taiko can verify the inclusion or absence of a particular transaction in a block, thus ensuring the authenticity and finality of cross-chain communications and state transitions.

### Logic and Implementation:

1. **Merkle Tree Construction**: At the core of the Merkle Proof mechanism is the construction of a Merkle Tree for each block of transactions. Each leaf node of the tree represents a hash of individual transaction data, and each non-leaf node represents a hash of its child nodes. This recursive hashing continues until there is a single hash, the Merkle Root, which represents the entire block.

2. **Merkle Proof Verification**: To verify the inclusion of a transaction within a block, Taiko uses a Merkle Proof, which is a sequence of hashes that, when combined with the transaction hash, can recreate the Merkle Root stored in the block header. If the calculated root matches the stored root, the transaction's inclusion is proven.

    ```solidity
     function verifyMerkleProof(
        bytes32 _rootHash,
        address _addr,
        bytes32 _slot,
        bytes32 _value,
        bytes[] memory _accountProof,
        bytes[] memory _storageProof
    )
        internal
        pure
        returns (bytes32 storageRoot_)
    {
        if (_accountProof.length != 0) {
            bytes memory rlpAccount =
                SecureMerkleTrie.get(abi.encodePacked(_addr), _accountProof, _rootHash);

            if (rlpAccount.length == 0) revert LTP_INVALID_ACCOUNT_PROOF();

            RLPReader.RLPItem[] memory accountState = RLPReader.readList(rlpAccount);

            storageRoot_ =
                bytes32(RLPReader.readBytes(accountState[_ACCOUNT_FIELD_INDEX_STORAGE_HASH]));
        } else {
            storageRoot_ = _rootHash;
        }

        bool verified = SecureMerkleTrie.verifyInclusionProof(
            bytes.concat(_slot), RLPWriter.writeUint(uint256(_value)), _storageProof, storageRoot_
        );

        if (!verified) revert LTP_INVALID_INCLUSION_PROOF();
    }
    ```

3. **Block Header and Merkle Root Storage**: Taiko stores the Merkle Root of each block within its smart contracts, enabling the verification of Merkle Proofs without requiring access to the full block data. This approach significantly reduces the data and computational requirements for verification.


4. **Cross-Chain Verification**: For cross-chain communication and state transitions, Taiko employs Merkle Proofs to verify the state or transaction on one chain within another chain's smart contracts. This ensures that actions taken on one layer or instance are accurately reflected across the network.

    

<br/>

[![download-1.png](https://i.postimg.cc/GtTtPHvz/download-1.png)](https://postimg.cc/T5GTf27W)




## 2): Cross-Chain Communication and the Signal Service:
Cross-Chain Communication and the Signal Service in Taiko represent core components designed to enable secure and verified interactions between different blockchain layers or entirely separate blockchain networks. This mechanism is pivotal for maintaining the integrity and security of state transitions and data exchange across Taiko's layered architecture and external blockchains.

### Technical Overview and Implementation:

#### Signal Service:
At its core, the Signal Service facilitates the broadcasting and verification of signals (or messages) across chains. Signals could encompass state changes, token transfers, or generic messages that need to be communicated securely between chains.

1. **Signal Generation and Storage:**
   - **Contract Role:** `SignalService.sol` plays a pivotal role here. It defines the structure for storing signal-related data and the functionality to emit signals.
   - **Logic:** When a particular action is performed on one chain that needs to be communicated to another, a signal is generated within this service. This could be triggered by user actions, smart contract calls, or automated processes within the Taiko ecosystem.
   - **Data Storage:** Signals are stored with their respective metadata, including the source chain ID, the type of signal, and a unique identifier. This data structure ensures that each signal can be efficiently identified and processed.

2. **Cross-Chain Signal Transmission:**
   - **Contract Role:** Integrations with `Bridge.sol` facilitate the secure transmission of signals across chains. The bridge utilizes the signal data from `SignalService.sol` to initiate cross-chain messages.
   - **Logic:** The bridge contract captures the signal, encapsulates it into a cross-chain message, and transmits it to the target chain. This process involves cryptographic operations to ensure the integrity and authenticity of the signal.

```solidity
function _sendSignal(
        address _app,
        bytes32 _signal,
        bytes32 _value
    )
        private
        validSender(_app)
        nonZeroValue(_signal)
        nonZeroValue(_value)
        returns (bytes32 slot_)
    {
        slot_ = getSignalSlot(uint64(block.chainid), _app, _signal);
        assembly {
            sstore(slot_, _value)
        }
        emit SignalSent(_app, _signal, slot_, _value);
    }
```

3. **Signal Verification:**
   - **Contract Role:** Upon receiving a signal on the target chain, contracts `SignalService.sol` on the destination chain are responsible for verifying the signal's authenticity and integrity.
   - **Logic:** Verification involves checking the signal's metadata against expected parameters and cryptographic proofs (such as Merkle proofs) to ensure the signal was indeed emitted by the source chain and has not been tampered with during transmission.

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

<br/>

[![Screenshot-from-2024-03-27-16-33-54.png](https://i.postimg.cc/qB3f289y/Screenshot-from-2024-03-27-16-33-54.png)](https://postimg.cc/t7pmjVR4)


## 3): Decentralized Rollup Operation (Based Contestable Rollup - BCR):

The Taiko protocol introduces a novel concept called Based Contestable Rollup (BCR), designed to enhance the scalability of Ethereum while ensuring the security and decentralization of the network. The BCR mechanism is pivotal to the protocol's architecture, offering a scalable solution that maintains the integrity of state transitions through a process of proposal, contestation, and verification.

### Working Mechanism of BCR:

1. **Proposal Submission:**
   - In the BCR framework, a prover, submits a new block to the network. This block contains a series of state transitions, encapsulating the changes from the previous block.

2. **Contestation Period:**
   - Upon submission, the block enters a contestation period. During this time frame, other network participants, including validators and full nodes, have the opportunity to review the proposed block and its contained state transitions.

3. **Challenge Process:**
   - If any participant believes that a block contains incorrect or fraudulent state transitions, they can challenge the block by submitting a contestation. This challenge must be backed by a security deposit or stake.

4. **Adjudication:**
   - The challenge triggers an adjudication process, where the contested state transitions are scrutinized. This may involve executing the transactions on a trusted execution environment or through a deterministic verification process by the network's validators.

5. **Resolution:**
   - If the challenge is deemed valid, the contested block is rejected, and the proposer's stake is slashed. The challenger is often rewarded for identifying the fraudulent block. If the challenge is unfounded, the block is accepted, and the challenger's stake may be slashed as a deterrent against frivolous or malicious challenges.

6. **Finalization:**
   - Once a block successfully passes the contestation period without challenges or after a challenge has been resolved, the block is finalized. The state transitions within are considered valid, and the block is added to the blockchain.

<br/>

[![download-2.png](https://i.postimg.cc/kGvs8kHg/download-2.png)](https://postimg.cc/QKVcZns2)


Token Bridging and Asset Management within Taiko is a fundamental aspect that facilitates the seamless transfer and management of assets across different layers (L1, L2, L3) and potentially across different blockchains. This process ensures that users can interact with a unified ecosystem without being restricted by the underlying complexity of cross-chain operations.

### Implementation Overview:
The core implementation of Token Bridging and Asset Management within Taiko revolves around a set of smart contracts, including **Bridge**, **BridgedERC20**, **BridgedERC721**, **BridgedERC1155**, and vault contracts like **ERC20Vault**, **ERC721Vault**, and **ERC1155Vault**.

### Main Components and Logic:

1. **Bridge Contract:**
   - Responsible for initiating the bridging process. It keeps track of cross-chain messages, ensuring that assets sent from one chain can be claimed on another.
   - Utilizes **SignalService** for secure message transmission across chains. Messages are encapsulated with relevant asset and transfer information.

2. **Bridged Token Contracts (BridgedERC20, BridgedERC721, BridgedERC1155):**
   - These contracts represent the bridged version of the original assets on the target chain. They are minted or burned based on the cross-chain transfer actions.
   - Implement the logic for minting and burning tokens in response to bridge operations. They ensure that the total supply across all chains remains consistent with the original asset's supply.

3. **Vault Contracts (ERC20Vault, ERC721Vault, and ERC1155Vault):**
   - Act as the custodian of assets during the bridging process. They hold the original assets when they are locked on the source chain and manage the minting and burning of bridged assets on the target chain.
   - Ensure that assets are only released to the correct recipients based on verified bridge messages.

4. **SignalService and Merkle Proofs:**
   - A critical component for verifying the integrity and authenticity of cross-chain messages. It allows the system to verify that a message was indeed sent from the source chain without requiring the entire block data.
   - Utilizes Merkle proofs to prove the inclusion of a specific message in a block, ensuring the message's validity and the asset transfer's legitimacy.

### Code Implementation:

The bridging process starts with the **Bridge** contract, where a user initiates a token transfer to another chain. The contract records this operation and emits a cross-chain message containing the asset information and destination details.

```solidity
function sendMessage(Message calldata _message)
        external
        payable
        override
        nonReentrant
        whenNotPaused
        returns (bytes32 msgHash_, Message memory message_)
    {
        // Ensure the message owner is not null.
        if (_message.srcOwner == address(0) || _message.destOwner == address(0)) {
            revert B_INVALID_USER();
        }

        // Check if the destination chain is enabled.
        (bool destChainEnabled,) = isDestChainEnabled(_message.destChainId);

        // Verify destination chain and to address.
        if (!destChainEnabled) revert B_INVALID_CHAINID();
        if (_message.destChainId == block.chainid) {
            revert B_INVALID_CHAINID();
        }

        // Ensure the sent value matches the expected amount.
        uint256 expectedAmount = _message.value + _message.fee;
        if (expectedAmount != msg.value) revert B_INVALID_VALUE();

        message_ = _message;

        // Configure message details and send signal to indicate message sending.
        message_.id = nextMessageId++;
        message_.from = msg.sender;
        message_.srcChainId = uint64(block.chainid);

        msgHash_ = hashMessage(message_);

        ISignalService(resolve("signal_service", false)).sendSignal(msgHash_);
        emit MessageSent(msgHash_, message_);
    }
```

Upon receiving the message on the target chain, the **SignalService** verifies its authenticity using Merkle proofs. Once verified, the corresponding **Vault** contract interacts with the **BridgedToken** contract to mint or release the asset to the recipient.

```solidity
function onMessageInvocation(bytes calldata _data)
        external
        payable
        nonReentrant
        whenNotPaused
    {
        (CanonicalERC20 memory ctoken, address from, address to, uint256 amount) =
            abi.decode(_data, (CanonicalERC20, address, address, uint256));

        // `onlyFromBridge` checked in checkProcessMessageContext
        IBridge.Context memory ctx = checkProcessMessageContext();

        // Don't allow sending to disallowed addresses.
        // Don't send the tokens back to `from` because `from` is on the source chain.
        if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

        // Transfer the ETH and the tokens to the `to` address
        address token = _transferTokens(ctoken, to, amount);
        to.sendEther(msg.value);

        emit TokenReceived({
            msgHash: ctx.msgHash,
            from: from,
            to: to,
            srcChainId: ctx.srcChainId,
            ctoken: ctoken.addr,
            token: token,
            amount: amount
        });
    }
```

These interactions ensure that tokens can be securely transferred across chains, with the system automatically handling asset locking, minting of bridged tokens, and unlocking of assets to the rightful owners. The use of Merkle proofs for message verification adds an additional layer of security, making the process reliable and tamper-proof.

<br/>

[![download-3.png](https://i.postimg.cc/5t19btYr/download-3.png)](https://postimg.cc/21cNxrxd)

## Codebase Quality

Overall, I consider the quality of the **Taiko** codebase to be of high caliber. The codebase exhibits mature software engineering practices with a strong emphasis on security, modularity, and clear documentation. The smart contracts leverage established standards, which demonstrates adherence to best practices within the Ethereum development community. Details are explained below:

| Codebase Quality Categories                     | Comments |
| ----------------------------------------------- | -------- |
| **Documentation and Comments**                  | The codebase is well-documented with comprehensive comments that explain the functionality and purpose of each contract and function, facilitating understandability and maintainability. |
| **Code Structure and Organization**             | Code is logically organized into directories and files based on functionality, making navigation and understanding of the project's architecture straightforward. |
| **Consistency and Coding Standards**            | The project adheres to common Solidity coding standards and naming conventions, ensuring consistency and readability across the codebase. |
| **Test Coverage and Quality**                   | With a test coverage of 79%, the project demonstrates a strong commitment to testing, though there's room for improvement to cover edge cases and potential security vulnerabilities more comprehensively. |
| **Security Practices and Considerations**       | The use of libraries like OpenZeppelin and custom security mechanisms indicates a focus on security. However, continuous security audits and reviews are essential to maintain high security standards. |
| **Use of Libraries and Dependencies**            | The project effectively uses reputable libraries (e.g., OpenZeppelin) to leverage pre-built functionalities, reducing the likelihood of bugs in foundational components. |
| **Upgradability and Maintenance**               | The project is designed with upgradability in mind, using proxy patterns and carefully managing state to ensure future improvements can be made with minimal disruption. |
| **Performance and Gas Optimization**            | The code shows considerations for gas optimization, crucial for scalability and user experience on Ethereum. Continuous profiling and optimization can further enhance performance. |
| **Error Handling and Data Validation**          | Solid error handling and data validation are present throughout, using require statements and custom error messages to ensure contract integrity and inform users of issues. |



## Analysis of the code base

The most important summary in analyzing the code base is the stacking of codes to be analyzed.
In this way, many predictions can be made, including the difficulty levels of the contracts, which one is more important for the auditor, the features they contain that are important for security (payable functions, uses assembly, etc.).

using [vscode-counter](https://github.com/uctakeoff/vscode-counter)


-  **filename:** This field indicates the language in which smart contracts are written

-  **Language:** Language in which the codebase is written.

-  **Code:** This field indicates the number of actual lines of code in the smart contract.

-  **Comment:** This field indicates the number of lines in the smart contract.

-  **Blank:** This field indicates the number of Blank lines in the smart contract.

-  **Total:** This field indicates the number of Total lines (code + comment + blank) in the smart contract.



Total : 85 files,  7611 codes, 2757 comments, 1534 blanks, all 11902 lines


## Files
| filename | language | code | comment | blank | total |
| :--- | :--- | ---: | ---: | ---: | ---: |
| [L1/ITaikoL1.sol](/L1/ITaikoL1.sol) | Solidity | 14 | 17 | 6 | 37 |
| [L1/TaikoData.sol](/L1/TaikoData.sol) | Solidity | 124 | 60 | 14 | 198 |
| [L1/TaikoErrors.sol](/L1/TaikoErrors.sol) | Solidity | 34 | 8 | 2 | 44 |
| [L1/TaikoEvents.sol](/L1/TaikoEvents.sol) | Solidity | 37 | 43 | 8 | 88 |
| [L1/TaikoL1.sol](/L1/TaikoL1.sol) | Solidity | 149 | 52 | 27 | 228 |
| [L1/TaikoToken.sol](/L1/TaikoToken.sol) | Solidity | 85 | 26 | 14 | 125 |
| [L1/gov/TaikoGovernor.sol](/L1/gov/TaikoGovernor.sol) | Solidity | 121 | 25 | 16 | 162 |
| [L1/gov/TaikoTimelockController.sol](/L1/gov/TaikoTimelockController.sol) | Solidity | 14 | 9 | 5 | 28 |
| [L1/hooks/AssignmentHook.sol](/L1/hooks/AssignmentHook.sol) | Solidity | 119 | 36 | 23 | 178 |
| [L1/hooks/IHook.sol](/L1/hooks/IHook.sol) | Solidity | 11 | 7 | 3 | 21 |
| [L1/libs/LibDepositing.sol](/L1/libs/LibDepositing.sol) | Solidity | 97 | 40 | 17 | 154 |
| [L1/libs/LibProposing.sol](/L1/libs/LibProposing.sol) | Solidity | 188 | 91 | 40 | 319 |
| [L1/libs/LibProving.sol](/L1/libs/LibProving.sol) | Solidity | 243 | 134 | 51 | 428 |
| [L1/libs/LibUtils.sol](/L1/libs/LibUtils.sol) | Solidity | 61 | 18 | 10 | 89 |
| [L1/libs/LibVerifying.sol](/L1/libs/LibVerifying.sol) | Solidity | 162 | 67 | 39 | 268 |
| [L1/provers/GuardianProver.sol](/L1/provers/GuardianProver.sol) | Solidity | 32 | 17 | 8 | 57 |
| [L1/provers/Guardians.sol](/L1/provers/Guardians.sol) | Solidity | 79 | 38 | 25 | 142 |
| [L1/tiers/DevnetTierProvider.sol](/L1/tiers/DevnetTierProvider.sol) | Solidity | 40 | 9 | 9 | 58 |
| [L1/tiers/ITierProvider.sol](/L1/tiers/ITierProvider.sol) | Solidity | 21 | 19 | 10 | 50 |
| [L1/tiers/MainnetTierProvider.sol](/L1/tiers/MainnetTierProvider.sol) | Solidity | 52 | 10 | 10 | 72 |
| [L1/tiers/TestnetTierProvider.sol](/L1/tiers/TestnetTierProvider.sol) | Solidity | 52 | 11 | 10 | 73 |
| [L2/CrossChainOwned.sol](/L2/CrossChainOwned.sol) | Solidity | 45 | 19 | 12 | 76 |
| [L2/Lib1559Math.sol](/L2/Lib1559Math.sol) | Solidity | 33 | 9 | 6 | 48 |
| [L2/TaikoL2.sol](/L2/TaikoL2.sol) | Solidity | 180 | 77 | 42 | 299 |
| [L2/TaikoL2EIP1559Configurable.sol](/L2/TaikoL2EIP1559Configurable.sol) | Solidity | 25 | 12 | 10 | 47 |
| [automata-attestation/AutomataDcapV3Attestation.sol](/automata-attestation/AutomataDcapV3Attestation.sol) | Solidity | 360 | 70 | 57 | 487 |
| [automata-attestation/interfaces/IAttestation.sol](/automata-attestation/interfaces/IAttestation.sol) | Solidity | 8 | 3 | 3 | 14 |
| [automata-attestation/interfaces/ISigVerifyLib.sol](/automata-attestation/interfaces/ISigVerifyLib.sol) | Solidity | 68 | 6 | 11 | 85 |
| [automata-attestation/lib/EnclaveIdStruct.sol](/automata-attestation/lib/EnclaveIdStruct.sol) | Solidity | 23 | 3 | 5 | 31 |
| [automata-attestation/lib/PEMCertChainLib.sol](/automata-attestation/lib/PEMCertChainLib.sol) | Solidity | 279 | 38 | 59 | 376 |
| [automata-attestation/lib/QuoteV3Auth/V3Parser.sol](/automata-attestation/lib/QuoteV3Auth/V3Parser.sol) | Solidity | 246 | 10 | 32 | 288 |
| [automata-attestation/lib/QuoteV3Auth/V3Struct.sol](/automata-attestation/lib/QuoteV3Auth/V3Struct.sol) | Solidity | 48 | 7 | 7 | 62 |
| [automata-attestation/lib/TCBInfoStruct.sol](/automata-attestation/lib/TCBInfoStruct.sol) | Solidity | 23 | 3 | 4 | 30 |
| [automata-attestation/lib/interfaces/IPEMCertChainLib.sol](/automata-attestation/lib/interfaces/IPEMCertChainLib.sol) | Solidity | 42 | 3 | 7 | 52 |
| [automata-attestation/utils/Asn1Decode.sol](/automata-attestation/utils/Asn1Decode.sol) | Solidity | 107 | 82 | 23 | 212 |
| [automata-attestation/utils/BytesUtils.sol](/automata-attestation/utils/BytesUtils.sol) | Solidity | 225 | 122 | 28 | 375 |
| [automata-attestation/utils/RsaVerify.sol](/automata-attestation/utils/RsaVerify.sol) | Solidity | 208 | 80 | 32 | 320 |
| [automata-attestation/utils/SHA1.sol](/automata-attestation/utils/SHA1.sol) | Solidity | 166 | 16 | 14 | 196 |
| [automata-attestation/utils/SigVerifyLib.sol](/automata-attestation/utils/SigVerifyLib.sol) | Solidity | 114 | 15 | 14 | 143 |
| [automata-attestation/utils/X509DateUtils.sol](/automata-attestation/utils/X509DateUtils.sol) | Solidity | 63 | 3 | 12 | 78 |
| [bridge/Bridge.sol](/bridge/Bridge.sol) | Solidity | 404 | 115 | 75 | 594 |
| [bridge/IBridge.sol](/bridge/IBridge.sol) | Solidity | 63 | 95 | 22 | 180 |
| [common/AddressManager.sol](/common/AddressManager.sol) | Solidity | 35 | 17 | 10 | 62 |
| [common/AddressResolver.sol](/common/AddressResolver.sol) | Solidity | 60 | 19 | 11 | 90 |
| [common/EssentialContract.sol](/common/EssentialContract.sol) | Solidity | 91 | 26 | 27 | 144 |
| [common/IAddressManager.sol](/common/IAddressManager.sol) | Solidity | 4 | 10 | 2 | 16 |
| [common/IAddressResolver.sol](/common/IAddressResolver.sol) | Solidity | 18 | 22 | 3 | 43 |
| [libs/Lib4844.sol](/libs/Lib4844.sol) | Solidity | 38 | 14 | 10 | 62 |
| [libs/LibAddress.sol](/libs/LibAddress.sol) | Solidity | 55 | 14 | 12 | 81 |
| [libs/LibMath.sol](/libs/LibMath.sol) | Solidity | 9 | 12 | 3 | 24 |
| [libs/LibTrieProof.sol](/libs/LibTrieProof.sol) | Solidity | 36 | 20 | 11 | 67 |
| [signal/ISignalService.sol](/signal/ISignalService.sol) | Solidity | 68 | 65 | 13 | 146 |
| [signal/LibSignals.sol](/signal/LibSignals.sol) | Solidity | 5 | 5 | 3 | 13 |
| [signal/SignalService.sol](/signal/SignalService.sol) | Solidity | 246 | 31 | 37 | 314 |
| [team/TimelockTokenPool.sol](/team/TimelockTokenPool.sol) | Solidity | 159 | 72 | 51 | 282 |
| [team/airdrop/ERC20Airdrop.sol](/team/airdrop/ERC20Airdrop.sol) | Solidity | 40 | 24 | 10 | 74 |
| [team/airdrop/ERC20Airdrop2.sol](/team/airdrop/ERC20Airdrop2.sol) | Solidity | 61 | 41 | 21 | 123 |
| [team/airdrop/ERC721Airdrop.sol](/team/airdrop/ERC721Airdrop.sol) | Solidity | 37 | 18 | 9 | 64 |
| [team/airdrop/MerkleClaimable.sol](/team/airdrop/MerkleClaimable.sol) | Solidity | 65 | 14 | 17 | 96 |
| [thirdparty/nomad-xyz/ExcessivelySafeCall.sol](/thirdparty/nomad-xyz/ExcessivelySafeCall.sol) | Solidity | 36 | 26 | 3 | 65 |
| [thirdparty/optimism/Bytes.sol](/thirdparty/optimism/Bytes.sol) | Solidity | 70 | 60 | 23 | 153 |
| [thirdparty/optimism/rlp/RLPReader.sol](/thirdparty/optimism/rlp/RLPReader.sol) | Solidity | 191 | 63 | 50 | 304 |
| [thirdparty/optimism/rlp/RLPWriter.sol](/thirdparty/optimism/rlp/RLPWriter.sol) | Solidity | 44 | 19 | 8 | 71 |
| [thirdparty/optimism/trie/MerkleTrie.sol](/thirdparty/optimism/trie/MerkleTrie.sol) | Solidity | 148 | 74 | 29 | 251 |
| [thirdparty/optimism/trie/SecureMerkleTrie.sol](/thirdparty/optimism/trie/SecureMerkleTrie.sol) | Solidity | 32 | 21 | 5 | 58 |
| [thirdparty/solmate/LibFixedPointMath.sol](/thirdparty/solmate/LibFixedPointMath.sol) | Solidity | 35 | 37 | 11 | 83 |
| [tokenvault/BaseNFTVault.sol](/tokenvault/BaseNFTVault.sol) | Solidity | 79 | 56 | 18 | 153 |
| [tokenvault/BaseVault.sol](/tokenvault/BaseVault.sol) | Solidity | 46 | 12 | 10 | 68 |
| [tokenvault/BridgedERC1155.sol](/tokenvault/BridgedERC1155.sol) | Solidity | 91 | 34 | 16 | 141 |
| [tokenvault/BridgedERC20.sol](/tokenvault/BridgedERC20.sol) | Solidity | 128 | 32 | 23 | 183 |
| [tokenvault/BridgedERC20Base.sol](/tokenvault/BridgedERC20Base.sol) | Solidity | 56 | 30 | 19 | 105 |
| [tokenvault/BridgedERC721.sol](/tokenvault/BridgedERC721.sol) | Solidity | 83 | 31 | 15 | 129 |
| [tokenvault/ERC1155Vault.sol](/tokenvault/ERC1155Vault.sol) | Solidity | 230 | 62 | 31 | 323 |
| [tokenvault/ERC20Vault.sol](/tokenvault/ERC20Vault.sol) | Solidity | 291 | 95 | 49 | 435 |
| [tokenvault/ERC721Vault.sol](/tokenvault/ERC721Vault.sol) | Solidity | 193 | 35 | 31 | 259 |
| [tokenvault/IBridgedERC20.sol](/tokenvault/IBridgedERC20.sol) | Solidity | 7 | 18 | 5 | 30 |
| [tokenvault/LibBridgedToken.sol](/tokenvault/LibBridgedToken.sol) | Solidity | 52 | 5 | 7 | 64 |
| [tokenvault/adapters/USDCAdapter.sol](/tokenvault/adapters/USDCAdapter.sol) | Solidity | 22 | 21 | 9 | 52 |
| [verifiers/GuardianVerifier.sol](/verifiers/GuardianVerifier.sol) | Solidity | 23 | 7 | 6 | 36 |
| [verifiers/IVerifier.sol](/verifiers/IVerifier.sol) | Solidity | 19 | 8 | 4 | 31 |
| [verifiers/SgxVerifier.sol](/verifiers/SgxVerifier.sol) | Solidity | 137 | 62 | 41 | 240 |


### Dependencies / External Imports

| Dependency / Import Path | Count |
| ------------------------ | ----- |
| `access/Ownable2StepUpgradeable.sol` | 1 |
| `governance/GovernorUpgradeable.sol` | 1 |
| `governance/TimelockControllerUpgradeable.sol` | 1 |
| `governance/compatibility/GovernorCompatibilityBravoUpgradeable.sol` | 1 |
| `governance/extensions/GovernorTimelockControlUpgradeable.sol` | 1 |
| `governance/extensions/GovernorVotesQuorumFractionUpgradeable.sol` | 1 |
| `governance/extensions/GovernorVotesUpgradeable.sol` | 1 |
| `proxy/utils/Initializable.sol` | 1 |
| `token/ERC1155/ERC1155Upgradeable.sol` | 1 |
| `token/ERC1155/extensions/IERC1155MetadataURIUpgradeable.sol` | 1 |
| `token/ERC1155/utils/ERC1155ReceiverUpgradeable.sol` | 1 |
| `token/ERC20/ERC20Upgradeable.sol` | 1 |
| `token/ERC20/extensions/ERC20SnapshotUpgradeable.sol` | 2 |
| `token/ERC20/extensions/ERC20VotesUpgradeable.sol` | 2 |
| `token/ERC20/extensions/IERC20MetadataUpgradeable.sol` | 1 |
| `token/ERC721/ERC721Upgradeable.sol` | 1 |
| `utils/introspection/IERC165Upgradeable.sol` | 1 |
| `utils/IVotes.sol` | 1 |
| `interfaces/IERC1271.sol` | 1 |
| `ERC1967/ERC1967Proxy.sol` | 1 |
| `utils/UUPSUpgradeable.sol` | 1 |
| `ERC1155/IERC1155.sol` | 1 |
| `ERC20/IERC20.sol` | 10 |
| `ERC20/extensions/IERC20Metadata.sol` | 1 |
| `ERC20/utils/SafeERC20.sol` | 4 |
| `ERC721/IERC721.sol` | 2 |
| `ERC721/IERC721Receiver.sol` | 1 |
| `utils/Address.sol` | 2 |
| `utils/Strings.sol` | 4 |
| `utils/cryptography/ECDSA.sol` | 3 |
| `utils/cryptography/MerkleProof.sol` | 1 |
| `utils/introspection/IERC165.sol` | 1 |
| `utils/math/SafeCast.sol` | 1 |
| `solady/src/utils/Base64.sol` | 2 |
| `solady/src/utils/LibString.sol` | 2 |


## Comment-to-Source Ratio:

On average there are **2.59** code lines per comment (lower=better).



## Test analysis

**Setup**

Clone using:

```bash
git clone https://github.com/code-423n4/2024-03-taiko
```

Getting into the directory
```bash
cd 2024-03-taiko/packages/protocol
```

I ran this command to install dependencies:

```bash
pnpm install
```
Then to compile the testcases I ran this:
```bash
pnpm compile
```

Then for testcases I ran this:
```bash
pnpm test
```



### What did the project do differently? ;
-   1) It can be said that the developers of the project did a quality job, there is a test structure consisting of tests with quality content. In particular, tests have been written successfully.

-   2) Overall line coverage percentage provided by your tests : 79%
 
### What can be done better:
-  1): It is recommended to increase the test coverage to 100% so make sure that each and every line is battle tested.









## Approach Taken while auditing
When conducting an audit for a complex blockchain project like Taiko, my approach combines rigorous technical analysis with strategic insights gleaned from the project's documentation and any previous audits. This multifaceted strategy ensures a comprehensive understanding and thorough examination of the project's codebase and operational mechanisms.

**Understanding the Theoretical Framework:**
Firstly, I immerse myself in the project's whitepaper and any available technical documentation. This deep dive is critical for understanding the theoretical underpinnings of the project, including its unique features and the specific challenges it aims to address. For Taiko, which introduces novel concepts such as Cross-Chain Communication and Based Contestable Rollup (BCR), gaining a clear understanding of these mechanisms at a theoretical level is crucial for effectively auditing their implementation.

**Reviewing Previous Audits:**
Next, I review any previous audit reports available for the project. This step is invaluable for several reasons. It allows me to identify any recurring issues or vulnerabilities that have been previously highlighted, assess how the development team has addressed these past concerns, and understand the evolution of the project's security practices over time. This historical context helps in focusing the audit efforts on newly developed features or areas that have posed challenges in the past.

**In-depth Code Analysis:**
With a solid understanding of Taiko's theoretical framework and historical security context, I proceed to a detailed analysis of the codebase. My focus is on the critical components that are essential to the protocol's core functionality and security. This includes, but is not limited to, smart contracts responsible for Merkle proof-based state transition verification, cross-chain signal service mechanisms, and the intricacies of the BCR model. During this stage, I meticulously examine the code for common vulnerabilities, such as reentrancy, overflow/underflow, and improper access controls. I also assess the project's unique features for potential security risks specific to its architecture.

**Testing and Validation:**
An important part of the audit involves simulating various operational scenarios to test the system's resilience and behavior under different conditions. I ran the test cases to see how they are performing.

For each component of the system, I evaluated the coding standards and documentation quality. Well-documented code and adherence to established coding conventions are crucial for maintaining code quality, facilitating future updates, and ensuring that new developers can easily understand and contribute to the project.





## Other Audit Reports and Automated Findings 

**Previous Audits**
There are 2 previous audits(mentioned on c4 website)
[Sigma Prime](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/audit/sigma_prime_taiko_smart_contract_security_assessment_report_v2_0.pdf)
[Quill Audits](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/audit/quill_audits_taiko_smart_contract_audit_report.pdf)

**Known issues and risks**: 
[3naly3er Report](https://github.com/code-423n4/2024-03-taiko/blob/main/4naly3er-report.md)


## Full representation of the project’s risk model


### Systemic Risks
Systemic risks within the Taiko project include:

1. **Cross-Chain Communication Security**: The Signal Service, pivotal for secure cross-chain message passing, could be compromised if vulnerabilities in the verification process or external dependencies are exploited, leading to potential breaches in data integrity or asset misappropriation.

3. **Economic Attack Vectors on BCR**: The Based Contestable Rollup relies on economic incentives for its security model. Sophisticated attackers could potentially manipulate or exploit these economic models, leading to issues like false contestation or block verification delays.

4. **Dependency on External Systems**: Taiko's functionality and security rely on external systems, such as Ethereum L1 and trusted execution environments (TEEs) like Intel SGX. Vulnerabilities or failures in these systems could cascade into Taiko, impacting its operational integrity.

5. **Governance Manipulation**: While decentralized governance aims to democratize decision-making, there's a risk of governance attacks where entities acquire disproportionate control or influence, leading to decisions that could compromise the system's security or deviate from its intended path.

Understanding and mitigating these systemic risks are crucial for ensuring the long-term resilience and success of the Taiko project.

### Centalization Risks:
Centralization risks in the Taiko project primarily stem from points of control that could potentially be exploited or mismanaged, leading to centralized decision-making or vulnerabilities. Here are a few examples:

1. **Ownership Control in Smart Contracts**: Contracts like `SignalService` and `Bridge` have functions that are only callable by the owner or designated addresses, which could centralize control over critical functionalities.

    ```solidity
    function authorize(address _addr, bool _authorize) external onlyOwner {
        isAuthorized[_addr] = _authorize;
        emit Authorized(_addr, _authorize);
    }
    ```

    The `authorize` function allows the contract owner to control which addresses are authorized to perform certain actions, like syncing chain data. This centralizes control over an aspect of cross-chain communication.


3. **Guardian Roles in Emergency Decisions**: Certain contracts include roles or mechanisms for emergency intervention, which, while designed for protection, concentrate power in the hands of a few.

    ```solidity
    function pauseProving(bool _pause) external {
        _authorizePause(msg.sender);
        LibProving.pauseProving(state, _pause);
    }
    ```

4. **Token Management and Economic Incentives**: Contracts managing tokens or economic incentives have functions that could be exploited if not properly decentralized.

    ```solidity
    function grant(address _recipient, Grant memory _grant) external onlyOwner { ... }
    ```

    The `grant` function allows only the contract owner to allocate tokens, centralizing the decision-making process regarding token distribution.

Addressing centralization risks involves ensuring a transparent and distributed control mechanism, improving smart contract security practices, and incorporating community governance where feasible to mitigate the potential for misuse or targeted attacks.




### Technical Risks

**Smart Contract Vulnerabilities:** Bugs or logical errors in the smart contracts can lead to loss of funds, unauthorized access, or unintended behavior.

**Scalability Concerns:** As transaction volumes grow, the platform must scale without compromising performance or security.


## New insights and learning of project from this audit:

Reflecting on the Taiko project audit, my insights and learnings are encapsulated as follows:

1. **Modular and Layered Architecture**: The architecture demonstrated a scalable solution for blockchain scalability challenges, showcasing how modular design can facilitate scalability without compromising on security or decentralization.

2. **Advanced State Transition Verification**: The application of Merkle proofs for secure and efficient state verification across chains has deepened my understanding of cryptographic proofs in ensuring data integrity within decentralized systems.

3. **Economic Incentives in Rollup Operations**: The Based Contestable Rollup (BCR) approach provided a novel perspective on maintaining network integrity through economic incentives and contestation mechanisms, emphasizing the role of game theory in blockchain security.

4. **Cross-Chain Communication**: The Signal Service mechanism underscored the complexity of secure message passing between chains, offering valuable insights into the design of robust cross-chain protocols.

5. **Token Bridging and Asset Management**: The mechanisms for token bridging and asset management, including the mathematical logic behind token locking, minting, and burning, illustrated the intricacies of managing digital assets in a multi-chain environment.

These insights not only enhance my understanding of blockchain technology's evolving landscape but also equip me with valuable perspectives for future audits and blockchain development projects.

NOTE: I don't track time while auditing or writing report, so what the time I specified is just a number




### Time spent:
5 hours