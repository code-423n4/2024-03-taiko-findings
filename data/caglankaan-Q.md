## `block.number` Is Different On Different L2s

On Optimism, `block.number` is the L2 block number, but on Arbitrum, it's the L1 block number, and `ArbSys(address(100)).arbBlockNumber()` must be used. Furthermore, L2 block numbers often occur much more frequently than L1 block numbers (any may even occur on a per-transaction basis), so using block numbers for timing results in inconsistencies, especially when voting is involved across multiple chains. As of version 4.9, OpenZeppelin has [modified](https://blog.openzeppelin.com/introducing-openzeppelin-contracts-v4.9#governor) their governor code to use a clock rather than block numbers, to avoid these sorts of issues, but this still requires that the project [implement](https://docs.openzeppelin.com/contracts/4.x/governance#token_2) a [clock](https://eips.ethereum.org/EIPS/eip-6372) for each L2.

### Code Snippet
```solidity
l1Hash: blockhash(block.number - 1)
l1Height: uint64(block.number - 1)
meta_.difficulty = keccak256(abi.encodePacked(block.prevrandao, b.numBlocks, block.number));
proposedIn: uint64(block.number)
...
_state.slotA.genesisHeight = uint64(block.number);
...
|| assignment.maxProposedIn != 0 && block.number > assignment.maxProposedIn
...
if (block.number == 0) 
} else if (block.number == 1) {
uint256 parentHeight = block.number - 1;
 (publicInputHash,) = _calcPublicInputHash(block.number);
|| (block.number != 1 && _parentGasUsed == 0)
```

## Return values of `transfer()`/`transferFrom()` not checked
Not all `ERC20` implementations `revert()` when there's a failure in `transfer()` or `transferFrom()`. The function signature has a boolean return value and they indicate errors that way instead. By not checking the return value, operations that should have marked as failed, may potentially go through without actually transfer anything.

### Code Snippet
```solidity
tko.transfer(blk.assignedProver, blk.livenessBond)

tko.transferFrom(msg.sender, address(this), tier.contestBond)

_tko.transfer(_ts.prover, _ts.validityBond + reward)

_tko.transfer(_ts.contester, _ts.contestBond + reward)

_tko.transfer(msg.sender, reward - _tier.validityBond)

_tko.transferFrom(msg.sender, address(this), _tier.validityBond - reward)
..
tko.transfer(ts.prover, bondToReturn)
..
tko.transferFrom(_blk.assignedProver, taikoL1Address, _blk.livenessBond)
..
IERC20(taikoToken).transferFrom(sharedVault, _to, amountToWithdraw)
..
IERC20(token).transferFrom(vault, user, amount)
..
IERC20(token).transferFrom(vault, user, amount)
```

## Missing Checks For `address(0)`
In Solidity, the Ethereum address `0x0000000000000000000000000000000000000000` is known as the "zero address". This address has significance because it's the default value for uninitialized address variables and is often used to represent an invalid or non-existent address. The "
Missing zero address control" issue arises when a Solidity smart contract does not properly check or prevent interactions with the zero address, leading to unintended behavior.
For instance, a contract might allow tokens to be sent to the zero address without any checks, which essentially burns those tokens as they become irretrievable. While sometimes this is intentional, without proper control or checks, accidental transfers could occur.

### Code Snippet
```solidity
sigVerifyLib = ISigVerifyLib(sigVerifyLibAddr)

pemCertLib = PEMCertChainLib(pemCertLibAddr)
..
ES256VERIFIER = es256Verifier
..
token = _token

vault = _vault
..
srcToken = _srcToken

snapshooter = _snapshooter
..
usdc = _usdc
```

## `symbol()` and `decimal()` are not a part of the `ERC-20` standard
The `decimals()` and `symbol()` functions are not a part of the [ERC-20](https://eips.ethereum.org/EIPS/eip-20) standard, and was added later as an [optional extension](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC20/extensions/IERC20Metadata.sol). As such, some valid `ERC20` tokens do not support this interface, so it is unsafe to blindly cast all tokens to this interface, and then call this function.

### Code Snippet
```solidity
ctoken_ = CanonicalERC20({
    chainId: uint64(block.chainid),
    addr: _token,
    decimals: meta.decimals(),
    symbol: meta.symbol(),
    name: meta.name()
});
```

## `tokenURI()` does not follow EIP-721
The [EIP](https://eips.ethereum.org/EIPS/eip-721) states that `tokenURI()` "Throws if `_tokenId` is not a valid NFT", which the code below does not do. If the NFT has not yet been minted, `tokenURI()` should revert


### Code Snippet
```solidity
function tokenURI(uint256 _tokenId) public view virtual override returns (string memory) {
	return string(
	    abi.encodePacked(
		LibBridgedToken.buildURI(srcToken, srcChainId), Strings.toString(_tokenId)
	    )
	);
}
```

## State variables not limited to reasonable values
Consider adding appropriate minimum/maximum value checks to ensure that the following state variables can never be used to excessively harm users, including via griefing.

### Code Snippet
```solidity
Path: ./packages/protocol/contracts/common/EssentialContract.sol

__reentry = _reentry
```

```solidity
Path: ./packages/protocol/contracts/team/airdrop/MerkleClaimable.sol

claimStart = _claimStart

claimEnd = _claimEnd
```

```solidity
Path: ./packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

withdrawalWindow = _withdrawalWindow
```

```solidity
Path: ./packages/protocol/contracts/bridge/Bridge.sol

__ctx = Context(_msgHash, _from, _srcChainId)
```

```solidity
Path: ./packages/protocol/contracts/tokenvault/BridgedERC1155.sol

srcChainId = _srcChainId
```
```solidity
Path: ./packages/protocol/contracts/tokenvault/BridgedERC721.sol

srcChainId = _srcChainId
```

```solidity
Path: ./packages/protocol/contracts/tokenvault/BridgedERC20.sol

srcChainId = _srcChainId

__srcDecimals = _decimals
```


```solidity
Path: ./packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

gasExcess = _newGasExcess
```


```solidity
Path: ./packages/protocol/contracts/L2/TaikoL2.sol

gasExcess = _gasExcess
```

## Vulnerable versions of packages are being used
This project is using specific package versions which are vulnerable to the specific CVEs listed below. Consider switching to more recent versions of these packages that don't have these vulnerabilities.
```solidity
- [CVE-2023-40014](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-40014) - **MEDIUM** - (`openzeppelin/contracts >=4.0.0 <4.9.3`): OpenZeppelin Contracts is a library for secure smart contract development. Starting in version 4.0.0 and prior to version 4.9.3, contracts using `ERC2771Context` along with a custom trusted forwarder may see `_msgSender` return `address(0)` in calls that originate from the forwarder with calldata shorter than 20 bytes. This combination of circumstances does not appear to be common, in particular it is not the case for `MinimalForwarder` from OpenZeppelin Contracts, or any deployed forwarder the team is aware of, given that the signer address is appended to all calls that originate from these forwarders. The problem has been patched in v4.9.3.

- [CVE-2023-34459](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-34459) - **-** - (`openzeppelin/contracts >=4.3.0 <4.8.3`): When the verifyMultiProof, verifyMultiProofCalldata, processMultiProof, or processMultiProofCalldata functions are in use, it is possible to construct merkle trees that allow forging a valid multiproof for an arbitrary set of leaves. A contract may be vulnerable if it uses multiproofs for verification and the merkle tree that is processed includes a node with value 0 at depth 1(just under the root). This could happen inadvertently for balanced trees with 3 leaves or less, if the leaves are not hashed.This could happen deliberately if a malicious tree builder includes such a node in the tree. A contract is not vulnerable if it uses single- leaf proving (verify, verifyCalldata, processProof, or processProofCalldata), or if it uses multiproofs with a known tree that has hashed leaves.Standard merkle trees produced or validated with the @openzeppelin/merkle-tree library are safe (@openzeppelin/contracts >=4.7.0 <4.9.2).

- [CVE-2023-34234](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-34234) - **MEDIUM** - (`openzeppelin/contracts >=4.3.0 <4.8.3`): By frontrunning the creation of a proposal, an attacker can become the proposer and gain the ability to cancel it. The attacker can do this repeatedly to try to prevent a proposal from being proposed at all. This impacts the Governor contract in v4.9.0 only, and the GovernorCompatibilityBravo contract since v4.3.0.

- [CVE-2023-30542](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-30542) - **HIGH** - (`openzeppelin/contracts >=4.3.0 <4.8.3`): The proposal creation entrypoint (`propose`) in `GovernorCompatibilityBravo` allows the creation of proposals with a `signatures` array shorter than the `calldatas` array. This causes the additional elements of the latter to be ignored, and if the proposal succeeds the corresponding actions would eventually execute without any calldata. The `ProposalCreated` event correctly represents what will eventually execute, but the proposal parameters as queried through `getActions` appear to respect the original intended calldata. This issue has been patched in 4.8.3. As a workaround, ensure that all proposals that pass through governance have equal length `signatures` and `calldatas` parameters (@openzeppelin/contracts >=4.3.0 <4.8.3).

- [CVE-2023-30541](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-30541) - **MEDIUM** - (`openzeppelin/contracts >=3.2.0 <4.8.3`): A function in the implementation contract may be inaccessible if its selector clashes with one of the proxy's own selectors. Specifically, if the clashing function has a different signature with incompatible ABI encoding, the proxy could revert while attempting to decode the arguments from calldata. The probability of an accidental clash is negligible, but one could be caused deliberately and could cause a reduction in availability. The issue has been fixed in version 4.8.3. As a workaround if a function appears to be inaccessible for this reason, it may be possible to craft the calldata such that ABI decoding does not fail at the proxy and the function is properly proxied through (@openzeppelin/contracts >=3.2.0 <4.8.3).
```

### Code Snippet
```js
  "dependencies": {
    "@openzeppelin/contracts": "4.8.2",
    "@openzeppelin/contracts-upgradeable": "4.8.2",
```

## Non Disabled Implementation Contract
The upgradeable contracts do not disable initializers in the constructor, as recommended by the imported Initializable contract. This means that anyone can call the initializer on the implementation contract to set the contract variables and assign the roles. To reduce the potential attack surface, `_disableInitializers` in the constructor needs to be called.


### Code Snippet
```solidity
contract TaikoToken is EssentialContract, ERC20SnapshotUpgradeable, ERC20VotesUpgradeable 


contract TaikoGovernor is
    EssentialContract,
    GovernorCompatibilityBravoUpgradeable,
    GovernorVotesUpgradeable,
    GovernorVotesQuorumFractionUpgradeable,
    GovernorTimelockControlUpgradeable
{

contract TaikoTimelockController is EssentialContract, TimelockControllerUpgradeable 

contract BridgedERC1155 is EssentialContract, IERC1155MetadataURIUpgradeable, ERC1155Upgradeable 

abstract contract BaseVault is
    EssentialContract,
    IRecallableSender,
    IMessageInvocable,
    IERC165Upgradeable
{

contract BridgedERC721 is EssentialContract, ERC721Upgradeable 

contract BridgedERC20 is
    BridgedERC20Base,
    IERC20MetadataUpgradeable,
    ERC20SnapshotUpgradeable,
    ERC20VotesUpgradeable
{
```

## Potential division by zero should have zero checks in place
In Solidity, division by zero is a critical issue that can lead to exceptions and disrupt the normal flow of a contract. It's essential to ensure that the divisor in any division operation is not zero before performing the operation. Failing to check for zero can result in transaction reversion or other unintended consequences. This is especially important in financial contracts or any contract where division operations are used to determine distributions, rewards, or similar calculations. Implementing checks to ensure the divisor is not zero before performing division enhances the robustness and reliability of the contract.

### Code Snippet
```solidity
uint256 input = _gasExcess * LibFixedPointMath.SCALING_FACTOR / _adjustmentFactor;
```


