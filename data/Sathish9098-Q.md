# QA REPORTS

## [L-1] Inadequate Validation of RLP-Decoded Ethereum Account States

In Ethereum, an account's state comprises four fields: nonce, balance, storageHash, and codeHash. These are RLP-encoded for storage efficiency. When a smart contract, such as LibTrieProof, decodes this information, it expects an array of precisely four elements. The contract currently assumes that the decoding process results in the correct format without conducting an explicit verification

if rlpAccount is malformed, contains additional data, or is subject to tampering, this assumption can lead to significant errors.

Accessing an index that does not exist (due to fewer elements) can cause runtime errors, leading to transaction reverts and a denial of service for functionalities relying on this logic.

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/libs
/LibTrieProof.sol

52: RLPReader.RLPItem[] memory accountState = RLPReader.readList(rlpAccount);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibTrieProof.sol#L52

### Mitigation Steps

Implement an immediate check after decoding the RLP-encoded data to ensure it contains exactly four elements, reflecting the expected Ethereum account structure.

```solidity

if (accountState.length != 4) {
    revert("Invalid RLP account state length");
}

```

##

## [L-2] Inflexible Quorum Fraction Initialization in TaikoGovernor Contract

The hardcoding of the quorum fraction to a value of '4' (potentially representing 4%) lacks flexibility and adaptability. 

A fixed quorum fraction can lead to governance paralysis (if set too high relative to participation) or weakened security (if set too low). The inability to adjust this parameter in response to changes in token distribution, community engagement, or external threats could significantly impair the governance system's efficacy and responsiveness.

### Impact
- The inability to adjust the quorum fraction could result in governance gridlock or reduce security against potential governance attacks.

- The set quorum might no longer reflect the current state or sentiment of the community, leading to decreased participation and engagement.

```solidity
FILE: Breadcrumbs2024-03-taiko/packages/protocol/contracts/L1/gov
/TaikoGovernor.sol

43: __GovernorVotesQuorumFraction_init(4);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L43

### Mitigation Steps
Adding functionality to update the quorum fraction:

```solidity

// Add a new function to update the quorum fraction
function updateQuorumFraction(uint256 newQuorumFraction)
    public
    onlyRole(DEFAULT_ADMIN_ROLE) // Replace with appropriate governance control
{
    __updateQuorumFraction(newQuorumFraction);
    emit QuorumFractionUpdated(newQuorumFraction); // Ensure event logging for transparency
}

```

##

## [L-3] Ambiguity in Error Scope Due to Reuse of L1_INVALID_ETH_DEPOSIT Error

The L1_INVALID_ETH_DEPOSIT error is employed in different contexts within the LibDepositing library: it is used both for validating deposit conditions (such as incorrect deposit amounts) and for encoding deposit data. This reuse leads to ambiguity since the same error does not indicate the specific condition that failed. Consequently, developers or users encountering this error would have difficulty determining whether the issue lies with the deposit's size, the deposit's encoding, or another deposit-related condition, hindering effective debugging and resolution.

```solidity
FILE aiko/packages/protocol/contracts/L1/libs/LibDepositing.sol

if (!canDepositEthToL2(_state, _config, msg.value)) {
    revert L1_INVALID_ETH_DEPOSIT();
}

if (_amount > type(uint96).max) revert L1_INVALID_ETH_DEPOSIT();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L37-L39

##

## [L-4] Exposure to Reentrancy Threats and External Resolver Reliance in Ether Handling Functions

The LibDepositing library, specifically within the depositEtherToL2 function, sends Ether to a bridge address obtained from an external address resolver. If the bridge contract is malicious or has vulnerabilities, it could potentially exploit the interaction to reenter the calling contract, leading to unexpected behaviors such as state corruption, additional unauthorized actions, or Ether theft. This risk, while reduced due to the internal nature of the function and the sequence of actions, is not entirely negated and could lead to significant security issues.

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/L1/libs
/LibDepositing.sol

_resolver.resolve("bridge", false).sendEther(msg.value);
_resolver.resolve("bridge", false)

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L41

##

## [L-5] Ambiguities and Potential Misbehaviors in Handling Suboptimal Pending Deposits

The processDeposits function in the LibDepositing library behaves differently when the number of pending deposits (numPending) is less than the configured minimum threshold (_config.ethDepositMinCountPerBlock). Specifically, in such scenarios, it merely initializes an empty array (deposits_ = new TaikoData.EthDeposit ;) and terminates without processing any deposits.

### Impact
Lack of Clarity: The decision to not process deposits when below a certain count lacks explicit rationale or documentation, potentially confusing maintainers or users regarding its intent.
Dynamic Configuration Changes: If _config.ethDepositMinCountPerBlock is subject to change (e.g., through governance actions or dynamic adjustments), the system may exhibit unpredictable behavior, such as sudden halts in deposit processing without clear notice or understanding from users.

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/L1/libs
/LibDepositing.sol

78: if (numPending < _config.ethDepositMinCountPerBlock) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L78

##

## [L-6] Inaccurate Proof Tier Comparison Logic

This logic could reject valid tier upgrades or accept invalid ones due to not properly contextualizing the tier levels, especially when tier configurations change or when differentiating between initial submission and updates.

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/L1/libs
/LibProving.sol

// The new proof must meet or exceed the minimum tier required by the
        // block or the previous proof; it cannot be on a lower tier.
        if (_proof.tier == 0 || _proof.tier < _meta.minTier || _proof.tier < ts.tier) {
            revert L1_INVALID_TIER();
        }

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L132-L136

##

## [L-7] Vulnerabilities in Proving Process Pause Functionality

The code does not protect against rapid toggling or unclear status communication, which can disrupt the proving process, lead to unintended pauses, or confuse participants about the current operational status.

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/L1/libs
/LibProving.sol

if (_state.slotB.provingPaused == _pause) revert L1_INVALID_PAUSE_STATUS();
        _state.slotB.provingPaused = _pause;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L74-L75

##

## [L-8] Inflexible Initialization and Late Contract Setup

The contract assumes that it will be deployed either at the genesis block or the subsequent block, with no flexibility for later deployments. This rigid setup could limit the contract's deployment and testing scenarios, making it less adaptable to evolving blockchain environments.

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/L2
/TaikoL2.sol

 if (block.number == 0) {
            // This is the case in real L2 genesis
        } else if (block.number == 1) {
            // This is the case in tests
            uint256 parentHeight = block.number - 1;
            l2Hashes[parentHeight] = blockhash(parentHeight);
        } else {
            revert L2_TOO_LATE();
        }

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L86-L94

### Mitigation Steps
Allow contract initialization to handle a broader range of block numbers and scenarios while ensuring integrity and security.

##

## [L-9] Over-Constraint on Base Fee Calculation Conditions

This enforces a strict check on the base fee, which must match exactly with the calculated value. This could cause issues, especially in testing environments or in cases where slight discrepancies might arise due to block-to-block variances or initialization timing.

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/L2
/TaikoL2.sol

141: if (!skipFeeCheck() && block.basefee != basefee) {
            revert L2_BASEFEE_MISMATCH();
        }

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L141-L143

##

## [L-10] Risk of Public Input Hash Mismatches and Integrity Issues

This check ensures the integrity of public inputs between consecutive L2 blocks. A mismatch could indicate data corruption or synchronization issues between L1 and L2. However, reliance on correct previous hash values without proper error handling or recovery mechanisms can stall the system.

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/L2
/TaikoL2.sol

if (publicInputHash != publicInputHashOld) {
            revert L2_PUBLIC_INPUT_HASH_MISMATCH();
        }

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L132-L134

##

## [L-11] Arbitrary Restrictions and Inadequate Validation

The validation checks are crucial for maintaining data integrity and security, especially for cross-layer operations. However, the condition (block.number != 1 && _parentGasUsed == 0) seems arbitrary and could block legitimate anchoring in certain edge cases or during initial testing and setup phases.

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/L2
/TaikoL2.sol

 if (
            _l1BlockHash == 0 || _l1StateRoot == 0 || _l1BlockId == 0
                || (block.number != 1 && _parentGasUsed == 0)
        ) {
            revert L2_INVALID_PARAM();
        }

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L116-L121

##

## [L-12] Limited Reusability of Message IDs

The contract uses a sequential approach to assign message IDs, which inherently limits each message to a unique instance without considering batch processing or parallelism. This could limit scalability and introduce delays, especially when the network is congested or when operating at high throughput.

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/bridge
/Bridge.sol

// Configure message details and send signal to indicate message sending.
        message_.id = nextMessageId++;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L143-L144

### Mitigation Steps

Implement a more robust ID management system that can handle concurrent messages more efficiently, such as using a combination of timestamp and a counter to ensure uniqueness and support higher throughput.

##

## [L-13] Arbitrary Ban Logic for Addresses

The contract allows for banning addresses, but the logic seems arbitrary without clear criteria for what constitutes a ban-worthy offense. This could lead to misuse or misunderstandings, affecting legitimate users' operations or leaving malicious actors unchecked due to unclear policies.

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/bridge
/Bridge.sol

if (addressBanned[_addr] == _ban) revert B_INVALID_STATUS();
        addressBanned[_addr] = _ban;
        emit AddressBanned(_addr, _ban);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L109-L111

##

## [L-14] Inflexible Message Recall and Retry Logic

The contract has rigid conditions for recalling or retrying messages, based solely on their status. This could prevent legitimate retries or recalls due to transient network issues or minor mistakes, leading to unnecessary message failures.

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/bridge
/Bridge.sol

 if (messageStatus[msgHash] != Status.RETRIABLE) {
            revert B_NON_RETRIABLE();
        }

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L326-L328

##

## [L-15] Restrictive Re-registration Logic for SGX Instances

 This logic prevents an SGX instance from being re-registered once it has been used, but does not account for legitimate updates or re-attestations of the same SGX instance, potentially limiting flexibility in maintaining SGX enclave authenticity over time.

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/verifiers
/SgxVerifier.sol

if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();

            addressRegistered[_instances[i]] = true;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L211

##

## [L-16] Inflexible Proof Data Length Validation in SGX Proof Verification

The strict check on the proof data length can limit the flexibility and future adaptability of proof structures. If proof requirements change or additional information needs to be included, this fixed length check could prevent valid proofs from being processed.

```solidity
152: if (_proof.data.length != 89) revert SGX_INVALID_PROOF();

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L150-L152

##

## [L-17] Hardcoded ``MAX_TOKEN_PER_TXN`` value

Users who wish to bridge more than 10 tokens will have to perform multiple transactions. For users with large collections, this could lead to increased transaction costs (gas fees) and a more time-consuming process.

Implementing a governance mechanism to adjust the maximum tokens per transaction could provide flexibility while ensuring that changes are made responsibly and with community consensus.

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/tokenvault
/BaseNFTVault.sol

/// @notice Maximum number of tokens that can be transferred per transaction.
    uint256 public constant MAX_TOKEN_PER_TXN = 10;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L52-L53

##

## [L-18] Unsafe Down casting 

Casting the chain ID, which is a uint256 type, down to a uint64 type. This is considered unsafe downcasting because uint256 can represent much larger numbers than uint64 can. If the value of block.chainid exceeds the maximum value that uint64 can represent (which is 2^64 - 1), then the cast will result in data loss, leading to incorrect behavior.

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/L1/libs/LibDepositing.sol

90: amount: uint96(data),

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L90


##

## [L-19] ``addresses`` upcast and compared to values larger than a ``uint160``, may result in collisions

If the value is being compared to an input value in order to reject it, rather than allowing it to be converted to an address, the check will pass if the value is larger than type(uint160).max, even if, when cast, it matches the gating address.

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/L1/libs/LibDepositing.sol

151: return (uint256(uint160(_addr)) << 96) | _amount;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L151

##

## [L-20 ] ``receive()/payable fallback()`` function does not authorize requests

Having no access control on the function (e.g. require(msg.sender == address(weth))) means that someone may send Ether to the contract, and have no way to get anything back out, which is a loss of funds. If the concern is having to spend a small amount of gas to check the sender against an immutable address, the code should at least have a function to rescue mistakenly-sent Ether.

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/bridge
/Bridge.sol

70: receive() external payable { }

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L70

##

## [L-21 ] Code does not follow the best practice of check-effects-interaction

Code should follow the best-practice of [check-effects-interaction](https://blockchain-academy.hs-mittweida.de/courses/solidity-coding-beginners-to-intermediate/lessons/solidity-11-coding-patterns/topic/checks-effects-interactions/), where state variables are updated before any external calls are made. Doing so prevents a large class of reentrancy bugs.

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/L1/libs/LibProving.sol

196: if (returnLivenessBond) {
                tko.transfer(blk.assignedProver, blk.livenessBond);
                blk.livenessBond = 0;
            }


242: tko.transferFrom(msg.sender, address(this), tier.contestBond);

                // We retain the contest bond within the transition, just in
                // case this configuration is altered to a different value
                // before the contest is resolved.
                //
                // It's worth noting that the previous value of ts.contestBond
                // doesn't have any significance.
                ts.contestBond = tier.contestBond;



```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L196-L197

##

## [L-22 ] Consider implementing two-step procedure for updating protocol addresses

A copy-paste error or a typo may end up bricking protocol functionality, or sending tokens to an address with no known private key. Consider implementing a two-step procedure for updating protocol addresses, where the recipient is set as pending, and must 'accept' the assignment by making an affirmative call. A straight forward way of doing this would be to have the target contracts implement EIP-165, and to have the 'set' functions ensure that the recipient is of the right interface type.

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/tokenvault/BridgedERC20.sol

80: function setSnapshoter(address _snapshooter) external onlyOwner {
        snapshooter = _snapshooter;
    }
```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L80-L82

##

## [L-23] External calls in an un-bounded for-loop may result in a DOS

Consider limiting the number of iterations in for-loops that make external calls

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/tokenvault
/ERC1155Vault.sol


269: for (uint256 i; i < _op.tokenIds.length; ++i) {
                    IERC1155(_op.token).safeTransferFrom({
                        from: msg.sender,
                        to: address(this),
                        id: _op.tokenIds[i],
                        amount: _op.amounts[i],
                        data: ""
                    });
                }
```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L251-L253

```solidity
FILE: 2024-03-taiko/packages/protocol/contracts/tokenvault
/ERC721Vault.sol

170: for (uint256 i; i < _tokenIds.length; ++i) {
                IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);
            }

210:  for (uint256 i; i < _op.tokenIds.length; ++i) {
                    t.safeTransferFrom(_user, address(this), _op.tokenIds[i]);
                }

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L170-L172










