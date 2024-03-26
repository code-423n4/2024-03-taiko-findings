## Introduction
This analysis report's main intention is to provide insights on concerns that may represent threats to Taiko but don't necessarily fall into the vulnerabilities realm. 
In it I present ways trusted parties could provide risks to the protocol and informational findings. Note some of the findings may yield bad outcomes if not addressed, but considering those high or medium severity would be equivalent to stating footguns are valid issues. 
I have opted not to beat about the bush by diagramming or stating each of the smart contract's functions and variables as Taiko Labs already did so masterfully.
Finally, I hope the read is enjoyable and the risks here presented provide value. The most important part of this report is at the [Risks](#Risks) section: issues 1-4 are informational and 5-6 are centralization risks related to trusting too much on trusted parties.
## Summary
| Section                       | Details                                                                 |
| :---------------------------- | :---------------------------------------------------------------------- |
| [Introduction](#Introduction) | Initial commentary                                                      |
| [Protocol](#Protocol)         | Brief overview of Taiko; sources utilized to learn about the protocol.  |
| [Methods](#Methods)           | Codebase evaluation methodology.                                        |
| [Risks](#Risks)               | Architecture, business-logic, centralization and trusted roles concerns |

## Protocol
### Brief Overview
Taiko is a Based Contestable Rollup (BCR).
As straightforward as one can get, it means the rollup's architecture allows multi-party sequencing with contestations as the fault-proof mechanism.

Every time a sequencer tries to prove a previously proposed L2 state transition, the system requires a validity bond in order to incentivize non-malicious behavior. Contesting also comes with a bond cost to make sure disputes only occur when one is certain of a wrongly proposed state transition.

If the proof is contested, a sequencer with a higher tier than the first prover is able to present another proof that will either confirm the first sequencer's proof or deny it. Finally, rewards are distributed.
	* If the original proof is correct, the first-prover and the last one earn rewards and the contester loses its contestation bond.
	* Else, the first-prover loses its validity bond and the other parties get rewards.

The protocol maintains knowledge of the layer 1 state by anchoring updated layer 1 block details at the start of a new L2 block. This is what enables reliable cross-chain message verification.

The protocol also provides mechanisms to send ether and messages, and transfer assets² to and from the Layer 2 to the Layer 1. 
²-which is a bit more than what rollups commonly offer.

All those cross-chain messages/activities are mediated by the Bridge and the SignalService contracts.
	The bridge provides the high-level entry points for users to interact with and its two main capabilities are sending messages (when a request is initiated) and processing those (when a relayer picks up the request and attempts to process them at the target chain). The other capabilities offered by the bridge are related to edge cases, such as retrying a message and calling it back to the source chain.
	The signal service provides the low-level logic for cross-chain message passing and is permissionless, even though it is not a good idea to call directly it without significant knowledge of the system. It defines methods for sending and verifying signals with Merkle proofs whose roots are dependent on proper layer 1 anchoring. 
### Sources
Taiko Labs has provided amazing content to enable both developers and regular users to understand Taiko better. The docs are comprehensive and loaded with diagrams.
I've selected some sources tailored for the technical-heavy audience as they have played a major role in understanding how the protocol works:
[Based Rollup FAQ — Taiko Labs (mirror.xyz)](https://taiko.mirror.xyz/7dfMydX1FqEx9_sOvhRt3V8hJksKSIWjzhCVu7FyMZU)
[Based Contestable Rollup (BCR): A configurable, multi-proof roll… — Taiko Labs (mirror.xyz)](https://taiko.mirror.xyz/Z4I5ZhreGkyfdaL5I9P0Rj0DNX4zaWFmcws-0CVMJ2A)
[Multi-proofs | Docs (taiko.xyz)](https://docs.taiko.xyz/core-concepts/multi-proofs/)
[Proposers and Provers on Taiko (Jolnir) (youtube.com)](https://www.youtube.com/watch?v=9LT6B1pgkI8)
https://docs.taiko.xyz/core-concepts/bridging/

## Methods
The security research was conducted on three steps: context-gathering, codebase-evaluation and report-generation.

**Context-gathering:** read all documentation available and review the sources provided at the protocol overview. Even though the documentation is solid, I have proudly asked many dumb questions and it helped to avoid submitting issues that were protocol design choices.

The objective during this phase is to develop a mental-model of flows and reach clarity on important concepts.
This enables threat-modeling adjustments and helps classify the project into protocol categories to look for previously reported bugs. 
For this research, I have opted to study previous reports/bug bounties on Bridges, Rollups and Multi-Chain protocols on solodit.xyz and Jump Crypto.

Finally I read the already-available audit reports for Taiko and then started with the codebase.

**Codebase-evaluation:** consisted of 3 steps. First-glance, line-by-line review and semantical analysis. 
1. First glance: I passively read the contracts before doing deep dives. This helps pointing the areas of most expected complexity and target those to be checked multiple times. If something looks odd or incomplete, I tag it with "// @audit" comments but don't develop the lead further for now.
   At the end of this stage, I have a decent understanding of the order of calls and expected flows, but no deep knowledge of execution traces. 
2. Line-by-line review: the most thorough part of the process.
   Consists of analyzing the functions with as many details as possible. Even though I call this line-by-line, what actually happens is code-review by order of appearance. 
   As an example: if we have a function a that calls function b before returning a value X + Y, I evaluate function b first then the correctness of X + Y.
   This is when most of the "// @audit" tags appear, as they represent leads that can be related, but not limited to: wrong external integrations, logic errors, poor state-management and invariants not being held.
   By the end of stage 2, I have gathered most of the leads worth testing.
1. Semantical analysis: consists on a more targeted approach. On Taiko I have attempted techniques like mirroring (looking at methods that did opposite things to find state asymmetries); repeated reads(reading the same complex portion of a function to check if all details are correctly handled) and random attack vectors(when one has an attack vector idea while running at the park). 

**Report-generation:** involved gathering the observations made on the previous phases and pre-sorting them into the following categories: "ask-the-sponsor", "easy-proof-of-concept", "hard-proof-of-concept", "false-positive".
Testing begins and a very small amount of leads actually makes it to the end.
Finally, reports are categorized by severity level and, if necessary, placed at the Analysis category.
## Risks

### A-01 - TaikoToken:burn has centralization risks

#### Description
A burn function that allows a owner to arbitrarily burn tokens from any user may be utilized for censorship purposes. It also represents a important point of failure in case the owner's private keys fall into bad actors' possession.

Code snippet:
```solidity
function burn(address _from, uint256 _amount) public onlyOwner {
        _burn(_from, _amount);
    }
```

### A-02 - TaikoToken:snapshot has front-running risks

#### Description
The snapshot function at the TaikoToken serves for instant token balance accounting and can serve many purposes for a protocol.
A malicious party may front-run snapshot transactions and acquire Taiko Tokens in order to inflate their accounted balances then sell back right after the snapshot is made.
#### Recommended Mitigation Steps
This risk is inevitable but can be lessened by avoiding the utilization of public mempools. Make sure to utilize MEV protection services for such transactions, such as Flashbots. 

### A-03 - mint is defined at the BridgedERC1155 contract but never called by the ERC1155Vault

#### Description
The BridgedERC1155 contract defines a mint method that is only callable by the erc1155_vault role, as shown in the following code snippet:
```solidity
function mint(
        address _to,
        uint256 _tokenId,
        uint256 _amount
    )
        public
        nonReentrant
        whenNotPaused
        onlyFromNamed("erc1155_vault")
    {
        _mint(_to, _tokenId, _amount, "");
    }

```

The ERC1155Vault contract implementation, however, never calls this function, making it pointless.

### A-04 - ERC1155Vault could use safeBatchTransferFrom instead of loop at the handleMessage private function
#### Description
The handleMessage private function runs a loop to do safeTransferFrom calls to an ERC1155 contract. Using individual safeTransferFrom calls is not optimal because the contract provides a safeBatchTransferFrom function designed for this scenario:
```solidity
function _handleMessage(
        address _user,
        BridgeTransferOp memory _op
    )
        private
        returns (bytes memory msgData_, CanonicalNFT memory ctoken_)
    {
    ...
		for (uint256 i; i < _op.tokenIds.length; ++i) {
            IERC1155(_op.token).safeTransferFrom({
            from: msg.sender,
            to: address(this),
            id: _op.tokenIds[i],
            amount: _op.amounts[i],
            data: ""
	    });
    }
    ...
}
```

### A-05 - TaikoL1:proveBlock allows a guardian to prove a block with maximum tier proof avoiding GuardianProver:approve's approval

#### Description
The proveBlock at the TaikoL1 contract allows a Guardian to call it directly with a topTier proof and bypass the GuardianProver approval flow that safeguards guardian proofs proving.
#### Impact
The GuardianProver contract becomes pointless, as anytime a Guardian may opt to bypass the approval flow that requires other guardians to agree with the proposed block and prove a block directly on its own.
#### Recommended Mitigation Steps
Make sure to check the caller of proveBlock is the GuardianProver contract if the proof tier is the highest. This can be done by adding the following lines of code at LibProving's proveBlock implementation:
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
    {
...
bool isTopTier = tier.contestBond == 0;
if (isTopTier){
	require(msg.sender == GUARDIAN_PROVER_CONTRACT);
}
...
}
```

### A-06 GuardianProver:approve only verifies the proof argument of the caller that reaches a hash approval 

#### Impact
Guardians are able to call the approve function at the GuardianProver contract without any proof.

#### Proof of Concept
Until approved, the approve function doesn't check the proofs sent by the guardians that vote for the approval of certain transition and its block metadata. Considering the function's purpose is to approve a guardian proof, then the proof ought to be evaluated, not only the transition.
This behavior can be seen at the following code snippet, as only the transition and metadata are hashed and approved, but not the proof:
```solidity
function approve(
        TaikoData.BlockMetadata calldata _meta,
        TaikoData.Transition calldata _tran,
        TaikoData.TierProof calldata _proof
    )
        external
        whenNotPaused
        nonReentrant
        returns (bool approved_)
    {
        if (_proof.tier != LibTiers.TIER_GUARDIAN) revert INVALID_PROOF();
        bytes32 hash = keccak256(abi.encode(_meta, _tran));
        approved_ = approve(_meta.id, hash);
...
}  
```

#### Recommended Mitigation Steps
Consider hashing the proof as well so that guardians agree on all ends of the proposed block:
```solidity
bytes32 hash = keccak256(abi.encode(_meta, _tran, proof));
approved_ = approve(_meta.id, hash);
```


### Time spent:
070 hours