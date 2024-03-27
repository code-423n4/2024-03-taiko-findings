# QA Report: Taiko

## L-01 Use MerkleProofUpgradeable.sol instead of MerkleProof.sol

Upgradeable contracts allow you to change your contract's code after deployment, which can be essential for fixing bugs or adding features without deploying a new contract and migrating all existing data.

**Github:**

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L4


```solidity
import "@openzeppelin/contracts/utils/cryptography/MerkleProof.sol";
```

## L-02 Implement a Emergency Stop Mechanism for Token Withdrawals

The implementation of an emergency stop mechanism in a smart contract, particularly for sensitive operations like token withdrawals, provides several benefits that enhance the security, reliability, and trustworthiness of the contract and the overall system.

### Github: 

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L163C5-L178C6

```solidity
function withdraw(
        address _token,
        address _to
    )
        external
        onlyFromOwnerOrNamed("withdrawer")
        nonReentrant
        whenNotPaused
    {
        if (_to == address(0)) revert L2_INVALID_PARAM();
        if (_token == address(0)) {
            _to.sendEther(address(this).balance);
        } else {
            IERC20(_token).safeTransfer(_to, IERC20(_token).balanceOf(address(this)));
        }
    }
```

Github:

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L168

```solidity
function withdraw(address _to, bytes memory _sig) external {
        if (_to == address(0)) revert INVALID_PARAM();
        bytes32 hash = keccak256(abi.encodePacked("Withdraw unlocked Taiko token to: ", _to));
        address recipient = ECDSA.recover(hash, _sig);
        _withdraw(recipient, _to);
    }
```
## L-03 Use Indexed Parameters to improve Filtering

Marking parameters as indexed allows them to be efficiently filtered by Ethereum nodes. This is particularly useful for off-chain applications or services that listen for specific events. You might want to index parameters that are commonly queried or filtered, such as the app address.

Github:

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L268

```solidity
emit SignalSent(_app, _signal, slot_, _value);
```
Change to:

```solidity
event SignalSent(
    address indexed app,
    bytes32 indexed signal,
    bytes32 slot,
    bytes32 value,
    uint256 timestamp,
    uint256 blockNumber
);

```

## L-04 Division Before Multiplication Leads to Precision Loss

To reduce the risk of precision loss in calculations involving token amounts and costs, consider adjusting the order of operations to perform multiplications before divisions whenever possible and appropriate.

Github:

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L197


```solidity
 uint128 _amountUnlocked = amountUnlocked / 1e18; // divide first
        costToWithdraw = _amountUnlocked * r.grant.costPerToken - r.costPaid;
```

## L-05 Events emitted After Changes should include old values for Transparency

GuardiansUpdated event should include old set of Guardian addresses

Github:

```solidity
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L37
```


## L-06 Users Unable to Claim Airdrops due to Faulty Configurations

The setConfig and __MerkleClaimable_init functions do not explicitly validate that the _claimStart is before _claimEnd. This could potentially allow for a configuration where the claim start time is after the claim end time, which would make claiming airdrops impossible.

Github:

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L45

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

## L-07 Merkle Root Updates Could Invalidate Valid Claims

The contract allows updating the Merkle root, claim start, and claim end through setConfig, but it doesn’t handle potential edge cases related to ongoing claims. For instance, if the Merkle root is updated during an active claim period, it could invalidate previously valid claims or enable new ones unexpectedly.

Github:

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L45

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

## L-08 Denial of Service Risks when verifying Airdrop Claims due to Maliciously Crafted Proofs

A Merkle proof allows one to prove that a specific piece of data is included in a set without having to provide the entire dataset. For a Merkle proof to be verified, the smart contract needs to perform a series of hash computations. Starting from the specific leaf node, the contract hashes it together with a provided piece of the proof, then moves up the tree, hashing combined nodes, until it reaches the top. If the computed hash matches the known Merkle root, the proof is valid.

The complexity of verifying a Merkle proof depends on the number of hash operations that need to be processed to reach the root. In a balanced binary tree, this number is logarithmic in the number of leaves or data pieces. However, certain factors can increase the complexity. A deeper tree requires more hash operations to reach the root, increasing gas costs. While most Merkle trees are binary and balanced, it's possible to construct them differently, potentially leading to less efficient proofs.

### Proof of Concept
A bad actor could for instance, influence the structure of the proofs being generated, by creating proofs that are valid but require more hash operations than necessary.

Attacker could flood the contract with such claims that are expensive to process, depleting the gas limit of blocks and making it costly or impossible for legitimate users to submit their claims.

[Github:](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L78C5-L84C6)

```solidity
function claim(address user, uint256 amount, bytes32[] calldata proof) external nonReentrant {
        // Check if this can be claimed
        _verifyClaim(abi.encode(user, amount), proof);

        // Assign the tokens
        claimedAmount[user] += amount;
    }
```

[Github:](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L67)

```solidity
function _verifyClaim(bytes memory data, bytes32[] calldata proof) internal ongoingClaim {
        bytes32 hash = keccak256(abi.encode("CLAIM_TAIKO_AIRDROP", data));

        if (isClaimed[hash]) revert CLAIMED_ALREADY();
        if (!_verifyMerkleProof(proof, merkleRoot, hash)) revert INVALID_PROOF();

        isClaimed[hash] = true;
        emit Claimed(hash);
    }
```



[Github:](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L47)

```solidity
function claim(
        address user,
        uint256[] calldata tokenIds,
        bytes32[] calldata proof
    )
        external
        nonReentrant
    {
        // Check if this can be claimed
        _verifyClaim(abi.encode(user, tokenIds), proof);

        // Transfer the tokens
        for (uint256 i; i < tokenIds.length; ++i) {
            IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);
        }
    }
```
    

### Recommended Mitigation Steps

Explicitly impose limits on the proof size or depth that can be processed, rejecting claims with proofs exceeding these limits.

## L-09 Add Pausing Mechanisms to Airdrop Claims

The contract lacks mechanisms to pause or stop claims in case of an emergency or discovery of a critical bug. Incorporating such functionality could enhance control and safety.

Github:

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L78

```solidity
function claim(address user, uint256 amount, bytes32[] calldata proof) external nonReentrant {
        // Check if this can be claimed
        _verifyClaim(abi.encode(user, amount), proof);

        // Assign the tokens
        claimedAmount[user] += amount;
    }
```

## L-10 Rate Limit Missing on Airdrop Claims

The current implementation does not limit the frequency of claims. In specific scenarios, it might be beneficial to limit claims to prevent abuse or manage resource allocation more effectively.

Github:

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L78

```solidity
function claim(address user, uint256 amount, bytes32[] calldata proof) external nonReentrant {
        // Check if this can be claimed
        _verifyClaim(abi.encode(user, amount), proof);

        // Assign the tokens
        claimedAmount[user] += amount;
    }
```


## L-11 Implement Batch claiming Functions

Introduce a function that allows multiple claims to be processed in a single transaction. This batch processing should have a limit on the number of claims per transaction to prevent excessive gas costs and potential denial of service attacks.

Github:

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L78

```solidity
function claim(address user, uint256 amount, bytes32[] calldata proof) external nonReentrant {
        // Check if this can be claimed
        _verifyClaim(abi.encode(user, amount), proof);

        // Assign the tokens
        claimedAmount[user] += amount;
    }
```


## L-12 Users are unable to claim Airdrops

Eligible users are unable to access and claim their airdropped tokens beyond their initial claim, which could lead to dissatisfaction and diminish trust in the project. This is especially impactful if users encounter issues or errors during their first claim attempt that prevent them from successfully claiming.

Github:

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L78

```solidity
function claim(address user, uint256 amount, bytes32[] calldata proof) external nonReentrant {
        // Check if this can be claimed
        _verifyClaim(abi.encode(user, amount), proof);

        // Assign the tokens
        claimedAmount[user] += amount;
    }
```

Github:

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L67

```solidity
function _verifyClaim(bytes memory data, bytes32[] calldata proof) internal ongoingClaim {
        bytes32 hash = keccak256(abi.encode("CLAIM_TAIKO_AIRDROP", data));

        if (isClaimed[hash]) revert CLAIMED_ALREADY();
        if (!_verifyMerkleProof(proof, merkleRoot, hash)) revert INVALID_PROOF();

        isClaimed[hash] = true;
        emit Claimed(hash);
    }
```

1. First Claim:
   - The user calls the `claim` function with their address and the amount of 50 tokens.
   - Inside the `claim` function, the `_verifyClaim` function is called to verify the claim.
   - The `_verifyClaim` function generates a hash based on the provided data and checks if it has already been claimed. Since this is the first claim, it hasn't been claimed before, so it proceeds.
   - The Merkle proof is then verified. If the proof is valid, the claim is processed, and the `isClaimed` mapping is updated to mark this claim as already claimed.

2. Second Claim:
   - The same user attempts to claim 50 tokens again, using the same address.
   - Inside the `claim` function, the `_verifyClaim` function is called again.
   - Now, when `_verifyClaim` tries to check if the claim has been already made, it finds that the claim has already been marked as claimed during the first attempt. So, it reverts execution with the error `CLAIMED_ALREADY`.

## L-13 Openzeppelin Version Used Does not Support Compact Signatures

Signatures with a length of 64 are no longer supported for openzeppelin versions above 4.7.3. This will lead to functions invoking this method to revert due to ECDSA.recover returning 0 when signature length is 64. Support for compact signatures however, remains available for recover(bytes32,bytes32,bytes32).

Github:

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibAddress.sol#L61

```solidity
    "@openzeppelin/contracts": "4.8.2",
    "@openzeppelin/contracts-upgradeable": "4.8.2",
```

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

Github:

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L168

```solidity
function withdraw(address _to, bytes memory _sig) external {
        if (_to == address(0)) revert INVALID_PARAM();
        bytes32 hash = keccak256(abi.encodePacked("Withdraw unlocked Taiko token to: ", _to));
        address recipient = ECDSA.recover(hash, _sig);
        _withdraw(recipient, _to);
    }
```

## L-14 Missing Event Emissions For Critical Functions

Emitting an event after removing a certificate serial number would provide a clear record of the action, allowing for easier tracking and auditing of changes made to the revoked certificate list. This can be useful for compliance purposes and for detecting any unauthorized modifications to the list.

Github:

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L88

```solidity
function removeRevokedCertSerialNum(
        uint256 index,
        bytes[] calldata serialNumBatch
    )
        external
        onlyOwner
    {
        for (uint256 i; i < serialNumBatch.length; ++i) {
            if (!_serialNumIsRevoked[index][serialNumBatch[i]]) {
                continue;
            }
            delete _serialNumIsRevoked[index][serialNumBatch[i]];
        }
    }
```

Github:

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L73

```solidity
function addRevokedCertSerialNum(
        uint256 index,
        bytes[] calldata serialNumBatch
    )
        external
        onlyOwner
    {
        for (uint256 i; i < serialNumBatch.length; ++i) {
            if (_serialNumIsRevoked[index][serialNumBatch[i]]) {
                continue;
            }
            _serialNumIsRevoked[index][serialNumBatch[i]] = true;
        }
    }
    
```
Github:

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L69

```solidity
function setMrEnclave(bytes32 _mrEnclave, bool _trusted) external onlyOwner {
        _trustedUserMrEnclave[_mrEnclave] = _trusted;
    }
    
```

Github:

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L65


```solidity
function setMrSigner(bytes32 _mrSigner, bool _trusted) external onlyOwner {
        _trustedUserMrSigner[_mrSigner] = _trusted;
    }
```


## L-15 Implement Batch Approvals

A batch approval function would allow multiple guardians to approve several proofs at once. This could be particularly useful in scenarios where a series of block validations or transitions need to be approved quickly.

Github:

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L111

```solidity
function approveBatch(
    TaikoData.BlockMetadata[] calldata _metas,
    TaikoData.Transition[] calldata _trans,
    TaikoData.TierProof[] calldata _proofs
)
    external
    whenNotPaused
    nonReentrant
    returns (bool[] memory approved_)
{
    require(_metas.length == _trans.length && _trans.length == _proofs.length, "Mismatched array lengths");
    approved_ = new bool[](_metas.length);

    for (uint256 i = 0; i < _metas.length; i++) {
        if (_proofs[i].tier != LibTiers.TIER_GUARDIAN) {
            revert INVALID_PROOF();
        }
        bytes32 hash = keccak256(abi.encode(_metas[i], _trans[i]));
        bool approved = approve(_metas[i].id, hash);

        if (approved) {
            deleteApproval(hash);
            ITaikoL1(resolve("taiko", false)).proveBlock(_metas[i].id, abi.encode(_metas[i], _trans[i], _proofs[i]));
            approved_[i] = true;
        }

        emit GuardianApproval(msg.sender, _metas[i].id, _trans[i].blockHash, approved);
    }
    return approved_;
}
```

## L-16 Insufficient validation for EIP1559 Configurations

Setting gasTargetPerL1Block without an upper limit in TaikoL2EIP1559Configurable.setConfigAndExcess could allow configurations that exceed the processing capabilities of the L2 or its validators. This could result in delayed transaction processing, increased latency, or even network congestion, affecting overall performance and reliability.

Github:

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L25

```solidity
function setConfigAndExcess(
        Config memory _newConfig,
        uint64 _newGasExcess
    )
        external
        virtual
        onlyOwner
    {
        if (_newConfig.gasTargetPerL1Block == 0) revert L2_INVALID_CONFIG();
        if (_newConfig.basefeeAdjustmentQuotient == 0) revert L2_INVALID_CONFIG();

        customConfig = _newConfig;
        gasExcess = _newGasExcess;

        emit ConfigAndExcessChanged(_newConfig, _newGasExcess);
    }
    
```

## L-17 setConfigAndExcess might not be Optimal
Adding a requirement check to validate the _newConfig.gasTargetPerL1Block against a predefined MAX_GAS_TARGET ensures that the gas target for each L1 block does not exceed a maximum threshold, potentially preventing inefficient gas usage or other undesirable effects.

Github:

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L25

```solidity
function setConfigAndExcess(
        Config memory _newConfig,
        uint64 _newGasExcess
    )
        external
        virtual
        onlyOwner
    {
        if (_newConfig.gasTargetPerL1Block == 0) revert L2_INVALID_CONFIG();
        if (_newConfig.basefeeAdjustmentQuotient == 0) revert L2_INVALID_CONFIG();

        customConfig = _newConfig;
        gasExcess = _newGasExcess;

        emit ConfigAndExcessChanged(_newConfig, _newGasExcess);
    }
```
Add this check to function.

```solidity
require(_newConfig.gasTargetPerL1Block <= MAX_GAS_TARGET, "Gas target exceeds maximum allowed");
```

## L-18 Missing array length mismatch checks

If the lengths of _targets, _values, and _calldatas do not match, it could result in logical inconsistencies when executing proposals. For example, a mismatch might lead to executing a call to a target with the wrong calldata or transaction value, potentially resulting in failed transactions or unintended side effects. This could disrupt the intended governance actions and undermine the contract's integrity.

An attacker might exploit the lack of validation to craft proposals that are ambiguous or misleading. For instance, by carefully crafting the lengths of these arrays, an attacker could potentially cause the execution of unintended actions.

Validate that array lengths match.

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L48


```solidity
function propose(
        address[] memory _targets,
        uint256[] memory _values,
        bytes[] memory _calldatas,
        string memory _description
    )
```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L69

```solidity
function propose(
        address[] memory _targets,
        uint256[] memory _values,
        string[] memory _signatures,
        bytes[] memory _calldatas,
        string memory _description
    )
```

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L34C5-L41C6

```solidity
function verifyMerkleProof(
        bytes32 _rootHash,
        address _addr,
        bytes32 _slot,
        bytes32 _value,
        bytes[] memory _accountProof,
        bytes[] memory _storageProof
    )
```



```solidity
function _transferTokens(
        CanonicalNFT memory ctoken,
        address to,
        uint256[] memory tokenIds,
        uint256[] memory amounts
    )  
```    

```solidity
function _execute(
        uint256 _proposalId,
        address[] memory _targets,
        uint256[] memory _values,
        bytes[] memory _calldatas,
        bytes32 _descriptionHash
    )
```

```solidity 
function _cancel(
        address[] memory _targets,
        uint256[] memory _values,
        bytes[] memory _calldatas,
        bytes32 _descriptionHash
    )
```

```solidity
function mintBatch(
        address _to,
        uint256[] memory _tokenIds,
        uint256[] memory _amounts
    )
```
    
```solidity
function _beforeTokenTransfer(
        address, /*_operator*/
        address, /*_from*/
        address _to,
        uint256[] memory, /*_ids*/
        uint256[] memory, /*_amounts*/
        bytes memory /*_data*/
    )
```    

```solidity
function onERC1155BatchReceived(
        address,
        address,
        uint256[] calldata,
        uint256[] calldata,
        bytes calldata
    )
```
    
```solidity
function _transferTokens(
        CanonicalNFT memory ctoken,
        address to,
        uint256[] memory tokenIds,
        uint256[] memory amounts
    )
```

```solidity
function claim(
        address user,
        uint256[] calldata tokenIds,
        bytes32[] calldata proof
    )
```
    
```solidity
function _isCpuSvnHigherOrGreater(
        uint256[] memory pckCpuSvns,
        uint8[] memory tcbCpuSvns
    )
```  


## L-19 Avoid Empty Names when Setting Addresses

In the setAddress function of the AddressManager contract, there is no explicit check to ensure that the _name parameter is not empty. The function updates the address for a given chain ID and name pair without validating the content of _name. This allows for setting an address with an empty name, which could lead to unintended consequences, such as difficulties in retrieving or managing these addresses later on.

Github:

```solidity
function setAddress(
        uint64 _chainId,
        bytes32 _name,
        address _newAddress
    )
        external
        virtual
        onlyOwner
    {
    
        if (_name == bytes32(0)) revert AM_INVALID_PARAMS(); // Check if _name is empty
        address oldAddress = __addresses[_chainId][_name];
        if (_newAddress == oldAddress) revert AM_INVALID_PARAMS();
        __addresses[_chainId][_name] = _newAddress;
        emit AddressSet(_chainId, _name, _newAddress, oldAddress);
    }
```



Add a validation step in the setAddress function to ensure that the _name parameter contains a valid, non-empty value. You can do this by adding a simple condition to revert the transaction if _name is empty.


## L-20 Add Timelocks to Sensitive Functions

Adding timelocks to sensitive functions in a smart contract is a powerful security mechanism. It prevents immediate changes to critical parameters, giving stakeholders time to react if an unauthorized or harmful update is attempted.

Github:

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L65

```solidity
function setMrSigner(bytes32 _mrSigner, bool _trusted) external onlyOwner {
        _trustedUserMrSigner[_mrSigner] = _trusted;
    }
```

Github:

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L69

```solidity
function setMrEnclave(bytes32 _mrEnclave, bool _trusted) external onlyOwner {
        _trustedUserMrEnclave[_mrEnclave] = _trusted;
    }
```


## L-21 Add checks for Empty Arrays

Adding checks for empty arrays in Solidity functions is crucial for avoiding unnecessary gas expenditure and potential logical errors in smart contracts. In your provided function addRevokedCertSerialNum, you can include a check at the beginning of the function to ensure that the serialNumBatch array is not empty.

Github:

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L73

```solidity
function addRevokedCertSerialNum(
        uint256 index,
        bytes[] calldata serialNumBatch
    )
```

## L-22 Implement a Two Step Guardian Confirmation Process

Require that newly added guardians confirm their acceptance of the role before being fully integrated into the guardians array. Similarly, implement a mechanism for guardians to voluntarily resign.

Ensures that guardians are willing and aware participants, reducing the risk of inactive or unwilling guardians being added maliciously or by mistake.

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L53


## L-23 Enforce Optimal Hard limits on Guardians Set to Prevent Malicious Dos attempts by Compromoised Owner 

The setGuardians leverages the data type's maximum value to impose a limit, serving as an implicit hard cap on the array's size. However, this cap is more related to the technical limitations of the data type than to an explicit design choice regarding the optimal number of guardians for operational efficiency and gas cost considerations.

The function iterates over the current list of guardians, deleting each one's entry in the guardianIds mapping. If there's a significant number of existing guardians, this loop itself consumes gas for each iteration due to the delete operation, which contributes to the total.

The deletion of the array is a single operation, but it's a state change that affects the entire storage structure of the array. The gas cost depends on the size of the array being cleared.

The combined gas costs of checking conditions, adding new guardians, deleting existing ones, and emitting events can accumulate quickly. While optimizations like gas refunds for deleting storage slots can reduce the net cost, the total required gas can still be substantial.

Attempting to add 255 guardians in one transaction could stress the Ethereum network by consuming a large amount of gas, potentially approaching or exceeding block gas limits and incurring significant transaction costs.

Define a more practical upper limit on the number of guardians based on typical governance needs and operational considerations.

Github:

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L53

```solidity
function setGuardians(
        address[] memory _newGuardians,
        uint8 _minGuardians
    )
        external
        onlyOwner
        nonReentrant
    {
        // We need at least MIN_NUM_GUARDIANS and at most 255 guardians (so the approval bits fit in
        // a uint256)
        if (_newGuardians.length < MIN_NUM_GUARDIANS || _newGuardians.length > type(uint8).max) {
            revert INVALID_GUARDIAN_SET();
        }
        // Minimum number of guardians to approve is at least equal or greater than half the
        // guardians (rounded up) and less or equal than the total number of guardians
        if (_minGuardians < (_newGuardians.length + 1) >> 1 || _minGuardians > _newGuardians.length)
        {
            revert INVALID_MIN_GUARDIANS();
        }

        // Delete the current guardians
        for (uint256 i; i < guardians.length; ++i) {
            delete guardianIds[guardians[i]];
        }
        delete guardians;

        // Set the new guardians
        for (uint256 i = 0; i < _newGuardians.length; ++i) {
            address guardian = _newGuardians[i];
            if (guardian == address(0)) revert INVALID_GUARDIAN();
            // This makes sure there are not duplicate addresses
            if (guardianIds[guardian] != 0) revert INVALID_GUARDIAN_SET();

            // Save and index the guardian
            guardians.push(guardian);
            guardianIds[guardian] = guardians.length;
        }

        // Bump the version so previous approvals get invalidated
        ++version;

        minGuardians = _minGuardians;
        emit GuardiansUpdated(version, _newGuardians);
    }
```

## L-24 Missing checks for zero amounts in some functions

Without these checks, attacker might abuse the function for purposes like denial of service (DoS) by spamming it with zero-amount claims that still consume resources or spamming the Claimed event hindering effective analytics of claims.

Github: 

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L52

```solidity
function claimAndDelegate(
        address user,
        uint256 amount,
        bytes32[] calldata proof,
        bytes calldata delegationData
    )
        external
        nonReentrant
    {
        // Check if this can be claimed
        _verifyClaim(abi.encode(user, amount), proof);

        // Transfer the tokens
        IERC20(token).transferFrom(vault, user, amount);

        // Delegate the voting power to delegatee.
        // Note that the signature (v,r,s) may not correspond to the user address,
        // but since the data is provided by Taiko backend, it's not an issue even if
        // client can change the data to call delegateBySig for another user.
        (address delegatee, uint256 nonce, uint256 expiry, uint8 v, bytes32 r, bytes32 s) =
            abi.decode(delegationData, (address, uint256, uint256, uint8, bytes32, bytes32));
        IVotes(token).delegateBySig(delegatee, nonce, expiry, v, r, s);
    }
```

Github: 

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L78C5-L84C6

```solidity
function claim(address user, uint256 amount, bytes32[] calldata proof) external nonReentrant {
        // Check if this can be claimed
        _verifyClaim(abi.encode(user, amount), proof);

        // Assign the tokens
        claimedAmount[user] += amount;
    }
```

## NC-01 Add comments to uint128 amount struct member

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L29

## NC-02 Function Violating Solidity Naming Conventions

The function name basefee violates the naming convention typically used in solidity, where function names should follow the camelCase style.

Github:
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/Lib1559Math.sol#L16

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
The correct way to name this function, following the camelCase convention, would be baseFee.