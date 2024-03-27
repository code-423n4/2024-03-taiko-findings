# Gas Report: Taiko

## G-01 Optimize Structs to Utilize Solidity Struct Packing

Solidity utilizes EVM storage slots in a 32-byte (256-bit) alignment, and struct packing is an optimization technique that allows you to minimize the storage space structs use. The goal is to pack smaller data types together within the 32-byte slots to reduce the overall gas cost associated with storage operations. In your Grant struct, you can reorder the fields to ensure that smaller data types are packed together efficiently, thus potentially fitting more data into fewer storage slots.

### Github: 

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L28

```solidity
struct Grant {
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

## G-02 Datatypes Smaller than 32bytes can be Expensive in Structs in Some Cases

In this case it will be cheaper for both variables in the struct to be uint256

### Github: 

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/TCBInfoStruct.sol#L13C5-L17C6

```solidity
struct TCBLevelObj {
        uint256 pcesvn;
        uint8[] sgxTcbCompSvnArr;
        TCBStatus status;
    }
```

## G-03 Inline numGuardians() function to save gas

When you inline numGuardians(), every place in your code where numGuardians() is called would be directly replaced with guardians.length. This saves the gas that would be spent on making a function call.

### Github:

```solidity
function numGuardians() public view returns (uint256) {
        return guardians.length;
    }
```

## G-04 Fail Fast Approach in _resolve function can save gas

Implement a chain ID validation within the getAddress function to indirectly benefit the _resolve function by preventing unnecessary operations. If a chain ID is unsupported, the system can halt the resolution process early, saving computational resources and reducing transaction costs associated with on-chain operations.

### Github:

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressResolver.sol#L72C5-L88C6

```solidity
function _resolve(
        uint64 _chainId,
        bytes32 _name,
        bool _allowZeroAddress
    )
        private
        view
        returns (address payable addr_)
    {
        if (addressManager == address(0)) revert RESOLVER_INVALID_MANAGER();

        addr_ = payable(IAddressManager(addressManager).getAddress(_chainId, _name));

        if (!_allowZeroAddress && addr_ == address(0)) {
            revert RESOLVER_ZERO_ADDR(_chainId, _name);
        }
    }
```

### Github:
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L54

```solidity
function getAddress(uint64 _chainId, bytes32 _name) public view override returns (address) {
        return __addresses[_chainId][_name];
    }
```

### G-05 Use Short-Circuiting in Return Statement of _verifyCertChain to Save Gas

The final return statement checks all flags (!certRevoked && certNotExpired && verified && certChainCanBeTrusted). If the function is structured to ensure that it only proceeds when all conditions are met, some of these checks might be redundant. Additionally, if the logic ensures that at the first failure, the function will exit, simplifying this condition could save some gas.

### Github:
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L248

```solidity
return !certRevoked && certNotExpired && verified && certChainCanBeTrusted;
```

To address the issue of lack of short-circuiting in the return statement and potentially redundant checks, we can modify the function to immediately return false upon encountering any condition that invalidates the certificate chain. Since the loop breaks on the first failure condition, there's no need to check all conditions again at the end. Instead, you can return true at the end of the function if none of the break conditions are met, indicating that all certificates in the chain are valid, not revoked, not expired, and the chain can be trusted. Here's how you could restructure the function:

```solidity
function _verifyCertChain(IPEMCertChainLib.ECSha256Certificate[] memory certs)
    private
    view
    returns (bool)
{
    uint256 n = certs.length;

    for (uint256 i = 0; i < n; ++i) {
        IPEMCertChainLib.ECSha256Certificate memory issuer;
        if (i == n - 1) {
            issuer = certs[i];
        } else {
            issuer = certs[i + 1];
        }

        // Check if the certificate is revoked
        if ((i == n - 2 && _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.ROOT)][certs[i].serialNumber])
            || (certs[i].isPck && _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.PCK)][certs[i].serialNumber])) {
            return false; // Certificate is revoked
        }

        // Check if the certificate is expired
        if (block.timestamp <= certs[i].notBefore || block.timestamp >= certs[i].notAfter) {
            return false; // Certificate is expired
        }

        // Verify the certificate's signature
        bool verified = sigVerifyLib.verifyES256Signature(
            certs[i].tbsCertificate, certs[i].signature, issuer.pubKey
        );
        if (!verified) {
            return false; // Signature verification failed
        }

        // Check if the issuer's public key hash matches the trusted root CA's public key hash
        if (i == n - 1 && keccak256(issuer.pubKey) != ROOTCA_PUBKEY_HASH) {
            return false; // The chain cannot be trusted
        }
    }

    // If all checks passed, the certificate chain can be trusted
    return true;
}
```

This revised version simplifies the function by removing the boolean flags (`certRevoked`, `certNotExpired`, `verified`, `certChainCanBeTrusted`) and directly returning false upon detecting any issue with the certificate chain. It concludes by returning true only if the function has not exited by any of the previous conditions, implying that the certificate chain is valid and can be trusted. This change makes the function more gas-efficient by avoiding unnecessary checks after a failure condition has already determined the outcome.


## G-06 Avoid No-op in claimAndDelegate function to save gas

If the amount is zero, the function will still execute, consuming gas without performing any meaningful action. This results in a waste of resources for the user calling the function.

### Github: 

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L52

```solidity
function claimAndDelegate(
        address user,
        uint256 amount,
        bytes32[] calldata proof,
        bytes calldata delegationData
    )

```

## G-07 Avoid Proceeding with proof verification if empty to save on gas

Calling the function with an empty proof array when the context expects a non-empty proof can result in unnecessary gas consumption for operations that are guaranteed to fail the intended logical checks of a well-formed Merkle tree with multiple elements.

### Github:

```solidity
function _verifyMerkleProof(
    bytes32[] calldata _proof,
    bytes32 _merkleRoot,
    bytes32 _value
)
    internal
    pure
    virtual
    returns (bool)
{
    // Check for non-empty proof
    require(_proof.length > 0, "Merkle proof must not be empty");

    return MerkleProof.verify(_proof, _merkleRoot, _value);
}

```

## G-08 Use abi.encodePacked instead of abi.encode to save gas in some cases

When using abi.encodePacked instead of abi.encode, you can save some gas because abi.encodePacked removes all padding while encoding the data.

### Github:

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/GuardianProver.sol#L46

```solidity
 if (_proof.tier != LibTiers.TIER_GUARDIAN) revert INVALID_PROOF();
        bytes32 hash = keccak256(abi.encode(_meta, _tran));
```

### Github:
 
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L186

```solidity
return keccak256(abi.encode(_chainId, _kind, _blockId));
```

