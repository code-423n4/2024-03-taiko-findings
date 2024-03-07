
### `block.number` means different things on different L2s
On Optimism, `block.number` is the L2 block number, but on Arbitrum, it's the L1 block number, and `ArbSys(address(100)).arbBlockNumber()` must be used. Furthermore, L2 block numbers often occur much more frequently than L1 block numbers (any may even occur on a per-transaction basis), so using block numbers for timing results in inconsistencies, especially when voting is involved across multiple chains. As of version 4.9, OpenZeppelin has [modified](https://blog.openzeppelin.com/introducing-openzeppelin-contracts-v4.9#governor) their governor code to use a clock rather than block numbers, to avoid these sorts of issues, but this still requires that the project [implement](https://docs.openzeppelin.com/contracts/4.x/governance#token_2) a [clock](https://eips.ethereum.org/EIPS/eip-6372) for each L2.

```solidity
Path: ./packages/protocol/contracts/L1/libs/LibProposing.sol

122:                l1Hash: blockhash(block.number - 1),	// @audit-issue

131:                l1Height: uint64(block.number - 1),	// @audit-issue

204:        meta_.difficulty = keccak256(abi.encodePacked(block.prevrandao, b.numBlocks, block.number));	// @audit-issue

220:            proposedIn: uint64(block.number),	// @audit-issue
```
[122](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/L1/libs/LibProposing.sol#L122-L122), [131](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/L1/libs/LibProposing.sol#L131-L131), [204](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/L1/libs/LibProposing.sol#L204-L204), [220](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/L1/libs/LibProposing.sol#L220-L220), 


```solidity
Path: ./packages/protocol/contracts/L1/libs/LibVerifying.sol

57:        _state.slotA.genesisHeight = uint64(block.number);	// @audit-issue
```
[57](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/L1/libs/LibVerifying.sol#L57-L57), 


```solidity
Path: ./packages/protocol/contracts/L1/hooks/AssignmentHook.sol

86:                || assignment.maxProposedIn != 0 && block.number > assignment.maxProposedIn	// @audit-issue
```
[86](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L86-L86), 


```solidity
Path: ./packages/protocol/contracts/L2/TaikoL2.sol

86:        if (block.number == 0) {	// @audit-issue

88:        } else if (block.number == 1) {	// @audit-issue

90:            uint256 parentHeight = block.number - 1;	// @audit-issue

97:        (publicInputHash,) = _calcPublicInputHash(block.number);	// @audit-issue

118:                || (block.number != 1 && _parentGasUsed == 0)	// @audit-issue

127:            parentId = block.number - 1;	// @audit-issue

201:        if (_blockId >= block.number) return 0;	// @audit-issue

202:        if (_blockId + 256 >= block.number) return blockhash(_blockId);	// @audit-issue
```
[86](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/L2/TaikoL2.sol#L86-L86), [88](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/L2/TaikoL2.sol#L88-L88), [90](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/L2/TaikoL2.sol#L90-L90), [97](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/L2/TaikoL2.sol#L97-L97), [118](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/L2/TaikoL2.sol#L118-L118), [127](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/L2/TaikoL2.sol#L127-L127), [201](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/L2/TaikoL2.sol#L201-L201), [202](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/L2/TaikoL2.sol#L202-L202), 


#### Recommendation

Adopt a consistent timekeeping mechanism across L1 and L2 solutions when using `block.number` or similar timing mechanisms in your Solidity contracts. Consider using a standard clock or timestamp-based system, especially for functionalities like governance that require consistent timing across chains. For contracts on specific L2 solutions, ensure you're using the correct method to obtain block numbers consistent with the intended behavior. Keep abreast of standards and best practices, such as those suggested by OpenZeppelin, and implement appropriate solutions like EIP-6372 to provide a consistent and reliable timing mechanism across different blockchain environments.


### Return values of `transfer()`/`transferFrom()` not checked
Not all `ERC20` implementations `revert()` when there's a failure in `transfer()` or `transferFrom()`. The function signature has a boolean return value and they indicate errors that way instead. By not checking the return value, operations that should have marked as failed, may potentially go through without actually transfer anything.


```solidity
Path: ./packages/protocol/contracts/L1/libs/LibVerifying.sol

189:                tko.transfer(ts.prover, bondToReturn);	// @audit-issue
```
[189](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/L1/libs/LibVerifying.sol#L189-L189), 


```solidity
Path: ./packages/protocol/contracts/L1/libs/LibProving.sol

196:                tko.transfer(blk.assignedProver, blk.livenessBond);	// @audit-issue

242:                tko.transferFrom(msg.sender, address(this), tier.contestBond);	// @audit-issue

367:                _tko.transfer(_ts.prover, _ts.validityBond + reward);	// @audit-issue

371:                _tko.transfer(_ts.contester, _ts.contestBond + reward);	// @audit-issue

382:                _tko.transfer(msg.sender, reward - _tier.validityBond);	// @audit-issue

384:                _tko.transferFrom(msg.sender, address(this), _tier.validityBond - reward);	// @audit-issue
```
[196](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/L1/libs/LibProving.sol#L196-L196), [242](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/L1/libs/LibProving.sol#L242-L242), [367](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/L1/libs/LibProving.sol#L367-L367), [371](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/L1/libs/LibProving.sol#L371-L371), [382](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/L1/libs/LibProving.sol#L382-L382), [384](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/L1/libs/LibProving.sol#L384-L384), 


```solidity
Path: ./packages/protocol/contracts/L1/hooks/AssignmentHook.sol

102:        tko.transferFrom(_blk.assignedProver, taikoL1Address, _blk.livenessBond);	// @audit-issue
```
[102](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L102-L102), 


```solidity
Path: ./packages/protocol/contracts/team/TimelockTokenPool.sol

219:        IERC20(taikoToken).transferFrom(sharedVault, _to, amountToWithdraw);	// @audit-issue
```
[219](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/team/TimelockTokenPool.sol#L219-L219), 


```solidity
Path: ./packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

91:        IERC20(token).transferFrom(vault, user, amount);	// @audit-issue
```
[91](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L91-L91), 


```solidity
Path: ./packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

63:        IERC20(token).transferFrom(vault, user, amount);	// @audit-issue
```
[63](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L63-L63), 


#### Recommendation

To ensure the reliability and security of token transfers in your smart contract, it's crucial to check the return values of the `transfer()` and `transferFrom()` functions. These functions often return a boolean value indicating the success or failure of the transfer operation. By checking this return value, you can accurately determine whether the transfer was successful and handle any potential errors or failures accordingly. Failing to check the return value may lead to unintended and unhandled transfer failures, which could have security and usability implications.


### Missing checks for `address(0)`
In Solidity, the Ethereum address `0x0000000000000000000000000000000000000000` is known as the "zero address". This address has significance because it's the default value for uninitialized address variables and is often used to represent an invalid or non-existent address. The "
Missing zero address control" issue arises when a Solidity smart contract does not properly check or prevent interactions with the zero address, leading to unintended behavior.
For instance, a contract might allow tokens to be sent to the zero address without any checks, which essentially burns those tokens as they become irretrievable. While sometimes this is intentional, without proper control or checks, accidental transfers could occur.    
        

```solidity
Path: ./packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

55:        sigVerifyLib = ISigVerifyLib(sigVerifyLibAddr);	// @audit-issue

56:        pemCertLib = PEMCertChainLib(pemCertLibAddr);	// @audit-issue
```
[55](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L55-L55), [56](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L56-L56), 


```solidity
Path: ./packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

21:        ES256VERIFIER = es256Verifier;	// @audit-issue
```
[21](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L21-L21), 


```solidity
Path: ./packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

69:        token = _token;	// @audit-issue

70:        vault = _vault;	// @audit-issue
```
[69](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L69-L69), [70](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L70-L70), 


```solidity
Path: ./packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

39:        token = _token;	// @audit-issue

40:        vault = _vault;	// @audit-issue
```
[39](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L39-L39), [40](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L40-L40), 


```solidity
Path: ./packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

41:        token = _token;	// @audit-issue

42:        vault = _vault;	// @audit-issue
```
[41](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L41-L41), [42](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L42-L42), 


```solidity
Path: ./packages/protocol/contracts/tokenvault/BridgedERC1155.sol

56:        srcToken = _srcToken;	// @audit-issue
```
[56](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L56-L56), 


```solidity
Path: ./packages/protocol/contracts/tokenvault/BridgedERC721.sol

47:        srcToken = _srcToken;	// @audit-issue
```
[47](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/tokenvault/BridgedERC721.sol#L47-L47), 


```solidity
Path: ./packages/protocol/contracts/tokenvault/BridgedERC20.sol

73:        srcToken = _srcToken;	// @audit-issue

81:        snapshooter = _snapshooter;	// @audit-issue
```
[73](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/tokenvault/BridgedERC20.sol#L73-L73), [81](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/tokenvault/BridgedERC20.sol#L81-L81), 


```solidity
Path: ./packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol

40:        usdc = _usdc;	// @audit-issue
```
[40](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L40-L40), 


#### Recommendation

It is strongly recommended to implement checks to prevent the zero address from being set during the initialization of contracts. This can be achieved by adding require statements that ensure address parameters are not the zero address. 


### `tokenURI()` does not follow EIP-721
The [EIP](https://eips.ethereum.org/EIPS/eip-721) states that `tokenURI()` "Throws if `_tokenId` is not a valid NFT", which the code below does not do. If the NFT has not yet been minted, `tokenURI()` should revert

```solidity
Path: ./packages/protocol/contracts/tokenvault/BridgedERC721.sol

107:    function tokenURI(uint256 _tokenId) public view virtual override returns (string memory) {	// @audit-issue
```
[107](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/tokenvault/BridgedERC721.sol#L107-L107), 


#### Recommendation

Audit and update the `tokenURI()` function in your NFT contracts to ensure strict compliance with the EIP-721 standard. Specifically, implement a check at the beginning of the function to determine whether the `_tokenId` argument corresponds to a minted token. If the token does not exist, the function should revert with an appropriate error message. This can be achieved using a state variable or mapping that tracks minted tokens. Ensuring compliance with EIP-721 not only aligns with best practices but also enhances the robustness and user trust in your NFT implementation. Consider thorough testing and potential auditing to verify compliance across all aspects of the EIP-721 standard.


### State variables not limited to reasonable values
Consider adding appropriate minimum/maximum value checks to ensure that the following state variables can never be used to excessively harm users, including via griefing.

```solidity
Path: ./packages/protocol/contracts/common/EssentialContract.sol

125:            __reentry = _reentry;	// @audit-issue
```
[125](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/common/EssentialContract.sol#L125-L125), 


```solidity
Path: ./packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

91:        claimStart = _claimStart;	// @audit-issue

92:        claimEnd = _claimEnd;	// @audit-issue
```
[91](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L91-L91), [92](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L92-L92), 


```solidity
Path: ./packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

71:        withdrawalWindow = _withdrawalWindow;	// @audit-issue
```
[71](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L71-L71), 


```solidity
Path: ./packages/protocol/contracts/bridge/Bridge.sol

549:            __ctx = Context(_msgHash, _from, _srcChainId);	// @audit-issue
```
[549](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/bridge/Bridge.sol#L549-L549), 


```solidity
Path: ./packages/protocol/contracts/tokenvault/BridgedERC1155.sol

57:        srcChainId = _srcChainId;	// @audit-issue
```
[57](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L57-L57), 


```solidity
Path: ./packages/protocol/contracts/tokenvault/BridgedERC721.sol

48:        srcChainId = _srcChainId;	// @audit-issue
```
[48](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/tokenvault/BridgedERC721.sol#L48-L48), 


```solidity
Path: ./packages/protocol/contracts/tokenvault/BridgedERC20.sol

74:        srcChainId = _srcChainId;	// @audit-issue

75:        __srcDecimals = _decimals;	// @audit-issue
```
[74](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/tokenvault/BridgedERC20.sol#L74-L74), [75](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/tokenvault/BridgedERC20.sol#L75-L75), 


```solidity
Path: ./packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

37:        gasExcess = _newGasExcess;	// @audit-issue
```
[37](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L37-L37), 


```solidity
Path: ./packages/protocol/contracts/L2/TaikoL2.sol

96:        gasExcess = _gasExcess;	// @audit-issue
```
[96](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/L2/TaikoL2.sol#L96-L96), 


#### Recommendation


Implement validation checks for state variables to enforce minimum and maximum value limits. This can be achieved by adding modifiers or require statements in Solidity functions that modify these state variables. Ensure that these limits are reasonable and reflect the intended use of the contract. Additionally, consider implementing a mechanism to update these limits through a governance process or a trusted role, if applicable, to maintain flexibility and adaptability of the contract over time.


### Vulnerable versions of packages are being used
This project is using specific package versions which are vulnerable to the specific CVEs listed below. Consider switching to more recent versions of these packages that don't have these vulnerabilities.


```solidity
Path: ./packages/protocol/contracts/L1/TaikoData.sol
- [CVE-2023-40014](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-40014) - **MEDIUM** - (`openzeppelin/contracts >=4.0.0 <4.9.3`): OpenZeppelin Contracts is a library for secure smart contract development. Starting in version 4.0.0 and prior to version 4.9.3, contracts using `ERC2771Context` along with a custom trusted forwarder may see `_msgSender` return `address(0)` in calls that originate from the forwarder with calldata shorter than 20 bytes. This combination of circumstances does not appear to be common, in particular it is not the case for `MinimalForwarder` from OpenZeppelin Contracts, or any deployed forwarder the team is aware of, given that the signer address is appended to all calls that originate from these forwarders. The problem has been patched in v4.9.3.

- [CVE-2023-34459](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-34459) - **-** - (`openzeppelin/contracts >=4.3.0 <4.8.3`): When the verifyMultiProof, verifyMultiProofCalldata, processMultiProof, or processMultiProofCalldata functions are in use, it is possible to construct merkle trees that allow forging a valid multiproof for an arbitrary set of leaves. A contract may be vulnerable if it uses multiproofs for verification and the merkle tree that is processed includes a node with value 0 at depth 1(just under the root). This could happen inadvertently for balanced trees with 3 leaves or less, if the leaves are not hashed.This could happen deliberately if a malicious tree builder includes such a node in the tree. A contract is not vulnerable if it uses single- leaf proving (verify, verifyCalldata, processProof, or processProofCalldata), or if it uses multiproofs with a known tree that has hashed leaves.Standard merkle trees produced or validated with the @openzeppelin/merkle-tree library are safe (@openzeppelin/contracts >=4.7.0 <4.9.2).

- [CVE-2023-34234](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-34234) - **MEDIUM** - (`openzeppelin/contracts >=4.3.0 <4.8.3`): By frontrunning the creation of a proposal, an attacker can become the proposer and gain the ability to cancel it. The attacker can do this repeatedly to try to prevent a proposal from being proposed at all. This impacts the Governor contract in v4.9.0 only, and the GovernorCompatibilityBravo contract since v4.3.0.

- [CVE-2023-30542](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-30542) - **HIGH** - (`openzeppelin/contracts >=4.3.0 <4.8.3`): The proposal creation entrypoint (`propose`) in `GovernorCompatibilityBravo` allows the creation of proposals with a `signatures` array shorter than the `calldatas` array. This causes the additional elements of the latter to be ignored, and if the proposal succeeds the corresponding actions would eventually execute without any calldata. The `ProposalCreated` event correctly represents what will eventually execute, but the proposal parameters as queried through `getActions` appear to respect the original intended calldata. This issue has been patched in 4.8.3. As a workaround, ensure that all proposals that pass through governance have equal length `signatures` and `calldatas` parameters (@openzeppelin/contracts >=4.3.0 <4.8.3).

- [CVE-2023-30541](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-30541) - **MEDIUM** - (`openzeppelin/contracts >=3.2.0 <4.8.3`): A function in the implementation contract may be inaccessible if its selector clashes with one of the proxy's own selectors. Specifically, if the clashing function has a different signature with incompatible ABI encoding, the proxy could revert while attempting to decode the arguments from calldata. The probability of an accidental clash is negligible, but one could be caused deliberately and could cause a reduction in availability. The issue has been fixed in version 4.8.3. As a workaround if a function appears to be inaccessible for this reason, it may be possible to craft the calldata such that ABI decoding does not fail at the proxy and the function is properly proxied through (@openzeppelin/contracts >=3.2.0 <4.8.3).

```


#### Recommendation

Consider updating packages to safest version.


### Non Disabled Implementation Contract
The upgradeable contracts do not disable initializers in the constructor, as recommended by the imported Initializable contract. This means that anyone can call the initializer on the implementation contract to set the contract variables and assign the roles. To reduce the potential attack surface, `_disableInitializers` in the constructor needs to be called.

```solidity
Path: ./packages/protocol/contracts/L1/TaikoToken.sol

15:contract TaikoToken is EssentialContract, ERC20SnapshotUpgradeable, ERC20VotesUpgradeable {	// @audit-issue
```
[15](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/L1/TaikoToken.sol#L15-L15), 


```solidity
Path: ./packages/protocol/contracts/L1/gov/TaikoGovernor.sol

21:    GovernorTimelockControlUpgradeable	// @audit-issue
```
[21](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L21-L21), 


```solidity
Path: ./packages/protocol/contracts/L1/gov/TaikoTimelockController.sol

9:contract TaikoTimelockController is EssentialContract, TimelockControllerUpgradeable {	// @audit-issue
```
[9](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/L1/gov/TaikoTimelockController.sol#L9-L9), 


```solidity
Path: ./packages/protocol/contracts/tokenvault/BridgedERC1155.sol

14:contract BridgedERC1155 is EssentialContract, IERC1155MetadataURIUpgradeable, ERC1155Upgradeable {	// @audit-issue
```
[14](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L14-L14), 


```solidity
Path: ./packages/protocol/contracts/tokenvault/BaseVault.sol

16:    IERC165Upgradeable	// @audit-issue
```
[16](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/tokenvault/BaseVault.sol#L16-L16), 


```solidity
Path: ./packages/protocol/contracts/tokenvault/BridgedERC721.sol

12:contract BridgedERC721 is EssentialContract, ERC721Upgradeable {	// @audit-issue
```
[12](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/tokenvault/BridgedERC721.sol#L12-L12), 


```solidity
Path: ./packages/protocol/contracts/tokenvault/BridgedERC20.sol

19:    ERC20VotesUpgradeable	// @audit-issue
```
[19](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/tokenvault/BridgedERC20.sol#L19-L19), 


#### Recommendation


Build a constructor function in the upgradeable contracts that calls the disableInitializers() function.



### Potential division by zero should have zero checks in place
In Solidity, division by zero is a critical issue that can lead to exceptions and disrupt the normal flow of a contract. It's essential to ensure that the divisor in any division operation is not zero before performing the operation. Failing to check for zero can result in transaction reversion or other unintended consequences. This is especially important in financial contracts or any contract where division operations are used to determine distributions, rewards, or similar calculations. Implementing checks to ensure the divisor is not zero before performing division enhances the robustness and reliability of the contract.

```solidity
Path: ./packages/protocol/contracts/L2/Lib1559Math.sol

41:        uint256 input = _gasExcess * LibFixedPointMath.SCALING_FACTOR / _adjustmentFactor;	// @audit-issue: Variable `_adjustmentFactor` not checked.
```
[41](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/L2/Lib1559Math.sol#L41-L41), 


#### Recommendation

Before performing any division operation in Solidity, implement a check to ensure that the divisor is not zero. Use a `require()` statement or a similar assertion to validate the divisor. For example, use `require(divisor != 0, "Divisor cannot be zero");` before executing the division. This precaution prevents exceptions due to division by zero and ensures that your contract remains stable and predictable under all operational conditions. Regularly review your contract's logic to identify and safeguard against potential division by zero occurrences.



## `symbol()` and `decimal()` are not a part of the `ERC-20` standard
The `decimals()` and `symbol()` functions are not a part of the [ERC-20](https://eips.ethereum.org/EIPS/eip-20) standard, and was added later as an [optional extension](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC20/extensions/IERC20Metadata.sol). As such, some valid `ERC20` tokens do not support this interface, so it is unsafe to blindly cast all tokens to this interface, and then call this function.


```solidity
Path: ./packages/protocol/contracts/tokenvault/ERC20Vault.sol

368:                decimals: meta.decimals(),	// @audit-issue
```
[368](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/tokenvault/ERC20Vault.sol#L368-L368), 


```solidity
Path: ./packages/protocol/contracts/tokenvault/BridgedERC721.sol

94:        return LibBridgedToken.buildSymbol(super.symbol());	// @audit-issue
```
[94](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/tokenvault/BridgedERC721.sol#L94-L94), 


```solidity
Path: ./packages/protocol/contracts/tokenvault/ERC20Vault.sol

369:                symbol: meta.symbol(),	// @audit-issue
```
[369](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/tokenvault/ERC20Vault.sol#L369-L369), 


```solidity
Path: ./packages/protocol/contracts/tokenvault/BridgedERC20.sol

108:        return LibBridgedToken.buildSymbol(super.symbol());	// @audit-issue
```
[108](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/tokenvault/BridgedERC20.sol#L108-L108), 


#### Recommendation

When working with ERC-20 tokens in your Solidity code, be aware that the `symbol()` and `decimal()` functions are not a part of the ERC-20 standard and is considered an optional extension. Not all valid ERC-20 tokens implement this interface, so avoid blindly casting all tokens to this interface and calling the `symbol()` and `decimal()` functions. Instead, check the token's documentation or contract to determine whether it supports this extension before using it.
