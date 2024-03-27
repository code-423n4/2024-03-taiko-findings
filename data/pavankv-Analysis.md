**Index of table**
| Sl.no  | Particulars  |
|---|---|
| 1   | Overview  |
| 2  | Architecture view(Diagram)  |
| 3  | Approach taken in evaluating the codebase  |
| 4  | Systematic risks  |
| 5 | Mechanism review  |
| 6  | Recommendation   |
| 7  | Hours spend  |


## 1. Overview

Taiko Protocol represents a groundbreaking concept in scaling solutions for the Ethereum blockchain. It introduces innovative concepts called contestable rollups, where numerous users can create nodes to generate proof of proposed blocks from Layer 1 (L1) to Layer 2 (L2). Participants agree upon a bond amount, which serves as collateral to ensure the integrity of the proof. If another prover successfully validates the proof, they claim the liveness bond of the previous prover and receive rewards for their contribution. This concept fosters dynamic and economically beneficial activity within the Taiko Protocol ecosystem.

Key features are 

Block Proposals:- 
Transactions are bundled into blocks by anyone on the network.

Proof Generation:-
Users compete to create a zk-SNARK (Zero-Knowledge Succinct Non-interactive Argument of Knowledge) proof for the proposed block. This proof mathematically verifies that the block's execution was valid without revealing all transaction details.

Bonding Mechanism:- 
To incentivize ethical participation, each prover places a liveness bond and validity bond.

Contestation:- 
If another user discovers an error in the proof or submits a valid proof faster, they can challenge the original prover.

Dispute Resolution:- 
The challenger wins the first prover's liveness bond and receives an additional reward, while the original prover loses their bond. This mechanism ensures only valid proofs are accepted.



## 2 . Chart Flow (Diagram) :-

Please visit the below link 
http://icp-tool.rf.gd/Taiko.png



![Taiko](http://icp-tool.rf.gd/Taiko.png)



## 3.  Approach taken in evaluating the codebase

We approached manual code review by looking into each space in the scoped contract and decided to explain some core functional contracts.It is important to note that manual code reviews can be very time-consuming.

**1. Bridge.sol** 
This contract plays vital role in interoperability between Layer 1 and layer 2 and The bridge interacts with the  signal service, a core protocol component responsible for storing the world state and root state merkle proofs. These proofs cryptographically guarantee the validity of transactions occurring on L2 without requiring full execution on L1.

Core Methods :-

i. SendMEssage() :-

```solidity
unction sendMessage(Message calldata _message)
        external
        payable
        override
        nonReentrant
        whenNotPaused
        returns (bytes32 msgHash_, Message memory message_)
    {...}

```

The above function is used send message to valid destination chain by calling the sendsignal() and contains multiple validation.

ii. RecallMessage() :-

```solidity
    function recallMessage(
        Message calldata _message,
        bytes calldata _proof
    )
        external
        nonReentrant
        whenNotPaused
        sameChain(_message.srcChainId)
    {...}

```

The above function is used to invoke the failed calls on its source chain and used to release if any associated assets and reset the calls context and deletes the proof of receipt.

iii . processMessage() :-

```solidity
    function processMessage(
        Message calldata _message,
        bytes calldata _proof
    )
        external
        nonReentrant
        whenNotPaused
        sameChain(_message.destChainId)
    {...}

```

This function is used to process the proven message and the proof that has been received through the signal service, refunding the processing fee, and updating the message status.

iv . retryMessage() :-

```solidity
    function retryMessage(
        Message calldata _message,
        bool _isLastAttempt
    )
        external
        nonReentrant
        whenNotPaused
        sameChain(_message.destChainId)
    {
```
The above function is used to retry the failed message call only if it has a Status.Retriable status. It calls invokeMessageCall() to make a call to the specified address. 


**2. LibsDepositing.sol**

This is library class which plays vital role while depositing tokens on L2 layer through the L1 layer and process the deposits and update the state.

Core Methods :-

 A. depositEtherToL2() :-

```solidity
    function depositEtherToL2(
        TaikoData.State storage _state,
        TaikoData.Config memory _config,
        IAddressResolver _resolver,
        address _recipient
    )
```

The above function is used to Ether to layer called by TaikoL1 contract first it checks whether the ETH depositable to the L2 and sends the ether and get slot value by rearEnd algorithm like `rearEnd++ % Queue.length()` and update the state.


 B . processDeposits() :-

```solidity

    function processDeposits(
        TaikoData.State storage _state,
        TaikoData.Config memory _config,
        address _feeRecipient
    )
        internal
        returns (TaikoData.EthDeposit[] memory deposits_)
    {...}
```
The above function is used process the deposits while proposing the L2 blocks which have similar implementation like depositEther() function but the `TaikoData.EthDeposit[] memory deposits_` will updated and return to calling function.

**3. LibProposing.sol**

This contract used to propose the L2 blocks to the layer 1 blocks which has been already verified on layer 1 and this implemented by the TaikoL1 contract which is deployed on layer 1.

Core Methods:-

A. proposeBlock() :-

```solidity
    function proposeBlock(
        TaikoData.State storage _state,
        TaikoData.Config memory _config,
        IAddressResolver _resolver,
        bytes calldata _data,
        bytes calldata _txList
    )
        internal
        returns (TaikoData.BlockMetadata memory meta_, TaikoData.EthDeposit[] memory deposits_)
    {...}

```
The above function is used to propose blocks from L2 Taiko to L1 Taiko. Initially, it checks whether the prover address exists and conducts multiple levels of validation checks. It fetches the parent meta hash using a ring buffer data structure and calls the processDeposits() function to deposit and returns the _deposits. Additionally, it updates the block metadata, updates the blob hashes, and calls the onBlockProposed() function to send the liveness bond to the Taiko contract. The proposer pays fees to the prover in Ether or ERC20 tokens.

**4. LibProving.sol**

A. proveBlocks :-

```solidity
    function proveBlock(
        TaikoData.State storage _state,
        TaikoData.Config memory _config,
        IAddressResolver _resolver,
        TaikoData.BlockMetadata memory _meta,
        TaikoData.Transition memory _tran,
        TaikoData.TierProof memory _proof
    )
        internal
        returns (uint8 maxBlocksToVerify_)
    {...}

```

The above function plays a vital role in proving or contesting the L2 block transition to L1 within a specified time. Firstly, it uses Ring buffer DSA to store the state blocks and calls the createTransition() function to set the assigned prover if the transition is the first one and updates the transitionIds.

B. _overrideWithHigherProof() :-

```solidity
    function _overrideWithHigherProof(
        TaikoData.TransitionState storage _ts,
        TaikoData.Transition memory _tran,
        TaikoData.TierProof memory _proof,
        ITierProvider.Tier memory _tier,
        IERC20 _tko,
        bool _sameTransition
    )
        private
    {...}

```

The above function plays a vital role in contesting the proof of an already proven transition. In case the new contestant fails to prove that the contested transition is invalid, then half of the contestBond will be sent to the previous prover. If the new contestant proves that the previous transition is indeed invalid, then half of the prover validity bond will be sent to the new contestant. If it is not a contestant transition, then it adds the total contestant and updates the state root and blockHash.

C. _checkProverPermission() :-

```solidity
    function _checkProverPermission( // Check Prover
        TaikoData.State storage _state,
        TaikoData.Block storage _blk,
        TaikoData.TransitionState storage _ts,
        uint32 _tid,
        ITierProvider.Tier memory _tier
    )
        private
        view
    {...}

```
The above function is used to check whether the proving window has started or not, and whether the transition submitted by the assigned prover. This function method is called by the proveBlock() function.

**5. VerifyBlocks() :-**

This contract used to verify the blocks which have been proved by verifying each blocks parent block whether is it verified or not.

Core method are :-

A. verifyBlocks() :-

```solidity
    function verifyBlocks(
        TaikoData.State storage _state,
        TaikoData.Config memory _config,
        IAddressResolver _resolver,
        uint64 _maxBlocksToVerify
    )
        internal
    {...}

```

This function plays vital role in verifying the blocks first it fetch the slot value and block hash value by using the Ring buffer DSA and increment the block id to verify that parent hash and child hash are valid or not. If it verified then returns the validity and liveness bond to the prover finally updates the final states.

**6. SignalService.sol**
This Signal Service act as a secure communication between L1 and L2. It enables applications and contracts to exchange messages and data reliably by sending and syncing the world state and root state between two chains.

Core Method are :-

A. proveSignalReceived() :-

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
    {...}

```

The above function used to receive the proof from the other client and verifies by calling the `_verifyHopProof()` function in for-loop and checks whether the hop.ChainiD is current block.chain id and sync the data to the root state.



## 4. Systematic risks

1. As we know that taiko is as a fully open source, permissionless anyone can create node (prover , proposer and verifier) if the one entity or community are running large number of the nodes to process the blocks if any outage occurs like Arbitrum L2 Sequencer down and Solana faced and whole protocol transaction process was down for several minutes then the end-user has face that and they have to wait upto the fix applied.

2. Taiko Protocol implements the EIP-4844 in its core operation like proposing the blocks and others. Considered the security associated with that proposal which posses a mempool Dos risk though not an unprecedented one as this also applies to transactions with large amounts of calldata. 

Reference the Mempool issues section in below [Link](https://eips.ethereum.org/EIPS/eip-4844#consensus-layer-validation)

3. Centralized risk arises in methodologies reliant on a singular owner address. Notably, attention is drawn to the `setGuardians()` function within the abstract Guardians contract, which presents a security vulnerability should the sole owner address become compromised due to any unforeseen circumstances.

```solidity
    /// @notice Set the set of guardians
    /// @param _newGuardians The new set of guardians
    /// @param _minGuardians The minimum required to sign
    function setGuardians(
        address[] calldata _newGuardians, // Gas savings can be call data
        uint8 _minGuardians
    )
        external
        onlyOwner
        nonReentrant
    {...}

```

Code snippet:- 
https://github.com/pavankv241/2024-03-taiko-ICP/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L50C1-L60C6




## 5. Mechanism review 

After manual testing, we concluded that a Taiko protocol is designed to manage the innovative concepts like contestable rollups with taiko clients (prover , proposer and verifier) which provide various opportunities to users to interact with protocol and helpful to growth economically both firm and users. The concepts which would like highlight are :-

**1.Signal Service** 
It is the crucial component which operates as a smart contract deployed on both L1 (Ethereum mainnet) and L2 (Taiko's Layer 2 scaling solution).

Secure Cross-Chain Messaging:- The Signal Service facilitates secure communication between L1 and L2. It enables applications and contracts to exchange messages and data reliably.

Merkle Proofs for Verification:- This service leverages Merkle proofs, a cryptographic technique that allows verifying the inclusion of a specific message within a larger dataset without needing to download the entire dataset.
In Taiko's context, Merkle proofs are used to efficiently prove that a message originated on L1.

Storing World State and Root State:- The Signal Service plays a role in storing the world state (a snapshot of all blockchain data at a specific point) and root state (a condensed representation of the world state) for L2. This information is crucial for maintaining consistency and verifying the validity of L2 transactions.

Verifying Message Origin (isSignalSent):- This function allows contracts to confirm whether a particular message originated from a specific address on L1. This verification is vital for ensuring the authenticity and integrity of messages received on L2.

**2. Constestable Rollups**

The concept revolves around the Taiko Protocol, offering users diverse opportunities to become Taiko clients by running nodes, namely proposers, provers, and verifiers. This role is open to all users, and it comes with a bonding mechanism. If a new contestant successfully proves that a previously accepted proof is invalid, they receive half of the validity bond along with the liveness bond. This system aims to boost economic activity for both the protocol and its users.


 
**Comparison Table**

| Feature  | Taiko Protocol  | zkSync Protocol  |
|---|---|---|
| Type of ZK-Proof  |  zk-SNARKs and STARKs  |zk-SNARKs (Zero-knowledge Succinct Non-interactive Argument of Knowledge)|
| Focus | Scalable and cheaper transactions on Ethereum  | Scalable infrastructure for various blockchain applications  |
| Ethereum Compatibility  | High (designed for EVM)  | High (supports interaction with Ethereum mainnet)			  |
| Transaction Fees  | Lower than Ethereum mainnet  | Lower than Ethereum mainnet  |
|Transaction Process| Faster than Ethereum mainnet  | Faster than Ethereum mainnet  |
| Smart Contract Support  | Yes (EVM compatible)  | Yes (limited at present, but expanding)	  |
| Security  | Inherits security from Ethereum  |Inherits security from Ethereum|
|Use Cases| General purpose Ethereum scaling and other feature (Client nodes) | Blockchain applications beyond just payments  |
| Proto-Danksharding  | Implemented  | Implemented  |
| Constestable rollups  | Implemented  | No feature like that  |


## 6. Recommendation

 1.The Taiko protocol can be significantly improved by introducing a robust governance mechanism that empowers a designated group to establish fee structures for various client activities. This mechanism would enable a transparent and collaborative approach to determining how fees are distributed among the protocol, contributors (proposers, provers, and verifiers), ensuring a fair and sustainable ecosystem. Additionally, the governance system would facilitate the proposal and implementation of new ideas through a well-defined voting process, fostering innovation and continuous improvement of the Taiko protocol.

Key feature which can be benefited if added in governance concept :-

Fee Structure Management
This are designated fee parameters that the governance body can adjust, encompassing elements such as the base fee for client activities, fee distribution percentages among protocol stakeholders, minimum fees for specific actions, and discount structures for incentivizing desired behaviors. This framework establishes a structured process for proposing and approving changes to fee structures. Governance body members can submit proposals detailing fee adjustments and their rationale, which are then subject to discussion and transparent voting. This process allows for ample time for deliberation to ensure informed decision-making. Upon approval by a predefined majority vote, the proposed fee changes are implemented within the Taiko client. Furthermore, this governance concept is designed to integrate seamlessly with new ideas and innovations, ensuring that the fee structure remains adaptive and aligned with the protocol's objectives over time.

Fair and Sustainable Fee Distribution
The governance mechanism ensures that fees are distributed equitably among protocol stakeholders, incentivizing participation and maintaining a healthy ecosystem.

 2.As we know, guardians play a vital role in protocols. However, the Security Council and individual actors can exert control over the guardians and their activities. We would like to recommend implementing a multi-signature mechanism to enhance transparency and integrity within the protocol. This mechanism would allow actions to be executed only with the approval of multiple authorized individuals. Even if one authority figure's address is compromised, malicious activities cannot be carried out without the additional signatures. By distributing the risk among multiple members, rather than burdening a single individual, multi-signature systems represent one of the best risk management strategies.

3. Implement the [Solady](https://github.com/Vectorized/solady) to all ERC20 and erc721 operation which is gas-efficient in nature.Solmate is a library that provides a number of gas-efficient implementations of common smart contract patterns. Solady is another gas-efficient library that places a strong emphasis on using assembly.





### Time spent:
68 hours