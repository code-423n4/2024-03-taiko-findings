## [G-01]	Use require instead of assert

```
  assert(tier.validityBond == 0);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L223C15-L223C48

```
    assert(ts.validityBond == 0 && ts.contestBond == 0 && ts.contester == address(0));
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L224C13-L224C99

```
 assert(success); // never reverts, always returns 0 or 1
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L138C8-L138C65

## [G-02] Use double if statements instead of &&
If the if statement has a logical AND and is not followed by an else statement, it can be replaced with 2 if statements.

```
 if (!_allowZeroAddress && addr_ == address(0)) {
            revert RESOLVER_ZERO_ADDR(_chainId, _name);
        }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L85C8-L87C10

```
  if (msg.sender != owner() && msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();
        _;
    }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L42C7-L44C6

```
  if (
            block.timestamp > assignment.expiry
                || assignment.metaHash != 0 && _blk.metaHash != assignment.metaHash
                || assignment.parentMetaHash != 0 && _meta.parentMetaHash != assignment.parentMetaHash
                || assignment.maxBlockId != 0 && _meta.id > assignment.maxBlockId
                || assignment.maxProposedIn != 0 && block.number > assignment.maxProposedIn
        ) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L81C7-L87C12

```
   if (input.tip != 0 && block.coinbase != address(0)) {
            address(block.coinbase).sendEther(input.tip);
        }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L120C6-L122C10

```
  if (params.parentMetaHash != 0 && parentMetaHash != params.parentMetaHash) {
            revert L1_UNEXPECTED_PARENT();
        }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L108C7-L110C10

```
      if (proposerOne != address(0) && msg.sender != proposerOne) {
                return false;
            }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L310C7-L312C14

```

            if (verifier != address(0)) {
                bool isContesting = _proof.tier == ts.tier && tier.contestBond != 0;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L162C1-L164C85

```
   if (isTopTier) {
            // A special return value from the top tier prover can signal this
            // contract to return all liveness bond.
            bool returnLivenessBond = blk.livenessBond > 0 && _proof.data.length == 32
                && bytes32(_proof.data) == RETURN_LIVENESS_BOND;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L189C6-L193C65

```
  if (isTopTier) {
                // The top tier prover re-proves.
                assert(tier.validityBond == 0);
                assert(ts.validityBond == 0 && ts.contestBond == 0 && ts.contester == address(0));
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L221C11-L224C99

```
 if (
            _l1BlockHash == 0 || _l1StateRoot == 0 || _l1BlockId == 0
                || (block.number != 1 && _parentGasUsed == 0)
        ) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L116C8-L119C12

```
  if (!skipFeeCheck() && block.basefee != basefee) {
            revert L2_BASEFEE_MISMATCH();
        }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L141C7-L143C10

```
  if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {
                numL1Blocks = _l1BlockId - lastSyncedBlock;
            }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L275C11-L277C14

```
if (cacheStateRoot && _isFullProof && !_isLastHop) {
            _syncChainData(_chainId, LibSignals.STATE_ROOT, _blockId, _hop.rootHash);
        }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L285C9-L288C1

```
   if (cacheSignalRoot && (_isFullProof || !_isLastHop)) {
            _syncChainData(_chainId, LibSignals.SIGNAL_ROOT, _blockId, _signalRoot);
        }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L293C6-L295C10

```
   if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) {
            // If msg.sender is not the one that proved the message, then there
            // is an extra delay.
            unchecked {
                invocationDelay += invocationExtraDelay;
            }
        }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L250C6-L256C10

```
   if (msg.sender != owner() && msg.sender != snapshooter) {
            revert BTOKEN_UNAUTHORIZED();
        }
        _;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L38C6-L41C11

```
 if (_migratingAddress == migratingAddress && _migratingInbound == migratingInbound) {
            revert BB_INVALID_PARAMS();
        }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L45C8-L47C10

```
    if (pceSvnIsHigherOrGreater && cpuSvnsAreHigherOrGreater) {
                status = current.status;
                bool tcbIsRevoked = status == TCBInfoStruct.TCBStatus.TCB_REVOKED;
                return (!tcbIsRevoked, status);
            }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L220C9-L224C14


## [G‑03] Save gas by preventing zero amount in mint() and burn()

```
76:    _mint(_to, _tokenId, _amount, "");

110:  _burn(_account, _tokenId, _amount);
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L76


```
69:         _mintToken(_account, _amount);

88:         _burnToken(_account, _amount);
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L69

```
function _mintToken(address _account, uint256 _amount) internal override {
        _mint(_account, _amount);
    }

    function _burnToken(address _from, uint256 _amount) internal override {
        _burn(_from, _amount);
    }
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L129C3-L135C6



```
function _mintToken(address _account, uint256 _amount) internal override {
        usdc.mint(_account, _amount);
    }


    function _burnToken(address _from, uint256 _amount) internal override {
        usdc.transferFrom(_from, address(this), _amount);
        usdc.burn(_amount);
    }
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L43C1-L50C6

## [G-04] Assigning keccak operations to constant variables results in extra gas costs

```
   bytes32 public constant RETURN_LIVENESS_BOND = keccak256("RETURN_LIVENESS_BOND");
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L20C2-L20C86

```
   /// @notice Keccak hash of the string "STATE_ROOT".
    bytes32 public constant STATE_ROOT = keccak256("STATE_ROOT");

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/LibSignals.sol#L7C2-L9C1

```
    /// @notice Keccak hash of the string "SIGNAL_ROOT".
    bytes32 public constant SIGNAL_ROOT = keccak256("SIGNAL_ROOT");
}
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/LibSignals.sol#L10C1-L12C2

## [G‑05]	Operator >=/<= costs less gas than operator >/<

```
    if (address(this).balance > 0) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L125C5-L125C41

```
   if (numPending < _config.ethDepositMinCountPerBlock) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L78C6-L78C63

```
    if (meta_.txListByteSize == 0 || meta_.txListByteSize > _config.blockMaxTxListBytes) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L195C5-L195C95

```
 return _state.reusableBlobs[_blobHash] + _config.blobExpiry > block.timestamp;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L296C8-L296C87

```
 if (_proof.tier == 0 || _proof.tier < _meta.minTier || _proof.tier < ts.tier) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L134C8-L134C88

```
   while (blockId < b.numBlocks && numBlocksVerified < _maxBlocksToVerify) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L127C10-L127C86

```
  if (numBlocksVerified > 0) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L212C11-L212C41

```
  if (_newGuardians.length < MIN_NUM_GUARDIANS || _newGuardians.length > type(uint8).max) {
            revert INVALID_GUARDIAN_SET();
        }
        // Minimum number of guardians to approve is at least equal or greater than half the
        // guardians (rounded up) and less or equal than the total number of guardians
        if (_minGuardians < (_newGuardians.length + 1) >> 1 || _minGuardians > _newGuardians.length)
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L63C7-L68C101

```
  if (input > LibFixedPointMath.MAX_EXP_INPUT) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L42C7-L42C55

```
    if (numL1Blocks > 0) {
                uint256 issuance = numL1Blocks * _config.gasTargetPerL1Block;
                excess = excess > issuance ? excess - issuance : 1;
            }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L279C9-L282C14

```
    if (_op.tokenIds.length > MAX_TOKEN_PER_TXN) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L145C5-L145C55

```
  uint256 max = (_a.length < _b.length) ? _a.length : _b.length;
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L243C7-L243C71

```
  if (otherlen < len) {
            shortest = otherlen;
        }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L69C7-L71C10

```
  if (tbsPtr.ixl() < tbsParentPtr.ixl()) {
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L333C11-L333C53

## [G-06] Using assembly to revert with an error message

**Issue Description** - When reverting in solidity code, it is common practice to use a require or revert statement to revert execution with an error message. This can in most cases be further optimized by using assembly to revert with the error message.

**Estimated Gas Savings** - Here’s an example:

```
/// calling restrictedAction(2) with a non-owner address: 24042contract SolidityRevert {    address owner;    uint256 specialNumber = 1;    constructor() {        owner = msg.sender;    }    function restrictedAction(uint256 num)  external {        require(owner == msg.sender, "caller is not owner");        specialNumber = num;    }}/// calling restrictedAction(2) with a non-owner address: 23734contract AssemblyRevert {    address owner;    uint256 specialNumber = 1;    constructor() {        owner = msg.sender;    }    function restrictedAction(uint256 num)  external {        assembly {            if sub(caller(), sload(owner.slot)) {                mstore(0x00, 0x20) // store offset to where length of revert message is stored                mstore(0x20, 0x13) // store length (19)                mstore(0x40, 0x63616c6c6572206973206e6f74206f776e657200000000000000000000000000) // store hex representation of message                revert(0x00, 0x60) // revert with data            }        }        specialNumber = num;    }}
```

From the example above, we can see that we get a gas saving of over 300 gas when reverting with the same error message with assembly against doing so in solidity. This gas savings come from the memory expansion costs and extra type checks the solidity compiler does under the hood.

## [G-07] Multiple accesses of a mapping/array should use a storage pointer

Caching a mapping’s value in a storage pointer when the value is accessed multiple times saves ~40 gas per access due to not having to perform the same offset calculation every time. Help the Optimizer by saving a storage variable’s reference instead of repeatedly fetching it.


```
167:         blockId_ = _blockId != 0 ? _blockId : topBlockId[_chainId][_kind];

247:	if (topBlockId[_chainId][_kind] < _blockId) {
248:          topBlockId[_chainId][_kind] = _blockId;
        }
```

&nbsp;https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L167

```
92:     proofReceipt[msgHash].receivedAt = _timestamp;

168: 	uint64 receivedAt = proofReceipt[msgHash].receivedAt;

184:	proofReceipt[msgHash].receivedAt = receivedAt;

190: 	delete proofReceipt[msgHash];

230: 	uint64 receivedAt = proofReceipt[msgHash].receivedAt;

243:	proofReceipt[msgHash] = ProofReceipt({

250: 	if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) {

264: 	delete proofReceipt[msgHash];
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L92

## [GAS-08] Constructors can be marked as payable to save deployment gas
payable functions cost less gas to execute, since the compiler does not have to add extra checks to
ensure that a payment wasn't provided.
A constructor can safely be marked as payable , since only the deployer would be able to pass funds, and the project itself would not pass any funds.

```
   constructor() {
        _disableInitializers();
    }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L64C2-L66C6

```
 constructor(address es256Verifier) {
        ES256VERIFIER = es256Verifier;
    }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L20C4-L22C6


## [G-09] abi.encode() is less efficient than abi.encodePacked()

```
   return keccak256(
            abi.encode(
                "PROVER_ASSIGNMENT",
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L146C4-L148C37

```
   depositsHash: keccak256(abi.encode(deposits_)),
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L126C14-L126C64

```
   TaikoData.Block memory blk = TaikoData.Block({
            metaHash: keccak256(abi.encode(meta_)),
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L212C6-L213C52

```
   if (blk.blockId != _meta.id || blk.metaHash != keccak256(abi.encode(_meta))) {
            revert L1_BLOCK_MISMATCH();
        }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L121C6-L123C10

```
 if (_proof.tier != LibTiers.TIER_GUARDIAN) revert INVALID_PROOF();
        bytes32 hash = keccak256(abi.encode(_meta, _tran));
        approved_ = approve(_meta.id, hash);
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L45C8-L47C45

```
  if (approved_) {
            deleteApproval(hash);
            ITaikoL1(resolve("taiko", false)).proveBlock(_meta.id, abi.encode(_meta, _tran, _proof));
        }
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L49C7-L53C1

```
  TaikoData.BlockMetadata memory meta,
            TaikoData.Transition memory tran,
            TaikoData.TierProof memory proof
        ) = abi.decode(_input, (TaikoData.BlockMetadata, TaikoData.Transition, TaikoData.TierProof));
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoL1.sol#L85C11-L89C1

## [G-10] Compute known value `off-chain`

If You know what data to hash, there is no need to consume more computational power to hash it using keccak256 , you’ll end up consuming 2x amount of gas.

```
bytes32 public constant STATE_ROOT = keccak256("STATE_ROOT");

    /// @notice Keccak hash of the string "SIGNAL_ROOT".
    bytes32 public constant SIGNAL_ROOT = keccak256("SIGNAL_ROOT");
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/LibSignals.sol#L8C4-L11C68


## [G-11] When possible, use assembly instead of `unchecked{}`

You can also use unchecked{} for even more gas savings but this will not check to see if i overflows. For best gas savings, use inline assembly, however, this limits the functionality you can achieve.

> All contest

## [G-12] Use bytes32 rather than string/bytes.

If you can fit your data in 32 bytes, then you should use bytes32 datatype rather than bytes or strings as it is much cheaper in solidity. Basically, Any fixed size variable in solidity is cheaper than variable size.

```
string private __symbol;


    /// @dev Name of the bridged token.
    string private __name;
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L22C1-L25C27

```
string name;
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L28



## [G-13] Use assembly to validate `msg.sender`

We can use assembly to efficiently validate msg.sender for the didPay and uniswapV3SwapCallback functions with the least amount of opcodes necessary. Additionally, we can use xor() instead of iszero(eq()), saving 3 gas. We can also potentially save gas on the unhappy path by using scratch space to store the error selector, potentially avoiding memory expansion costs.


```
_srcToken == address(0) || _srcChainId == 0 || _srcChainId == block.chainid
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L21

```
if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L91

```
if (btoken_ == address(0)) {
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L230

```
if (_btokenNew == address(0) || bridgedToCanonical[_btokenNew].addr != address(0)) {
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L158

```
if (_op.token == address(0)) revert VAULT_INVALID_TOKEN();
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L149


## [G-14]use Mappings Instead of Arrays

Mappings, are useful when you need to store and access data based on a key, rather than an index. Mappings have a lower gas cost for read and write operations, especially when the size of the mapping is large, since Solidity can perform these operations based on the key directly, without needing to iterate over the entire data structure.

```
uint256[] tokenIds;
        // Amounts of tokens to transfer.
        uint256[] amounts;
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L33C1-L35C27

## [G-15] Amounts should be checked for 0 before calling a transfer

It is considered a best practice to verify for zero values before executing any transfers within smart contract functions. This approach helps prevent unnecessary external calls and can effectively reduce gas costs.

This practice is particularly crucial when dealing with the transfer of tokens or ether, as sending these assets to an address with a zero value will result in the loss of those assets.

In Solidity, you can determine whether a value is zero by utilizing the == operator. Here's an example demonstrating how to check for a zero value before performing a transfer:

```
Copy code
function transfer(address payable recipient, uint256 amount) public {
    require(amount > 0, "Amount must be greater than zero");
    recipient.transfer(amount);
}
```

In the provided example, we ensure that the amount parameter is greater than zero before executing the transfer to the designated recipient address. If the amount is zero or negative, the function will revert, preventing the transfer from taking place.

```
149:         super._beforeTokenTransfer(_from, _to, _amount);

160:         super._afterTokenTransfer(_from, _to, _amount);
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L149


## [G-16] Mark initializer functions as payable to save deployment gas

```
function init(
        address _owner,
        address _addressManager,
        address _srcToken,
        uint256 _srcChainId,
        string memory _symbol,
        string memory _name
    )
        external
        initializer
    {
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L38


> All Initializer functions should marked as payable

## [G-17] Use constants instead of type(uintx).max

it's generally more gas-efficient to use constants instead of type(uintX).max when you need to set the maximum value of an unsigned integer type.

The reason for this is that the type(uintX).max expression involves a computation at runtime, whereas a constant is evaluated at compile-time. This means that using type(uintX).max can result in additional gas costs for each transaction that involves the expression.

By using a constant instead of type(uintX).max, you can avoid these additional gas costs and make your code more efficient.

Here's an example of how you can use a constant instead of type(uintX).max:

```
contract MyContract {
    uint120 constant MAX_VALUE = 2**120 - 1;
    
    function doSomething(uint120 value) public {
        require(value <= MAX_VALUE, "Value exceeds maximum");
        
        // Do something
    }
}
```

In the above example, we have a contract with a constant MAX\_VALUE that represents the maximum value of a uint120. When the doSomething function is called with a value parameter, it checks whether the value is less than or equal to MAX\_VALUE using the <= operator.

By using a constant instead of type(uint120).max, we can make our code more efficient and reduce the gas cost of our contract.

It's important to note that using constants can make your code more readable and maintainable, since the value is defined in one place and can be easily updated if necessary. However, constants should be used with caution and only when their value is known at compile-time.

```
uint256 internal constant PLACEHOLDER = type(uint256).max;
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L27

```
uint64 _timestamp = _suspend ? type(uint64).max : uint64(block.timestamp);
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L89

```
82: if (block.chainid <= 1 || block.chainid > type(uint64).max) {

284: gasExcess_ = uint64(excess.min(type(uint64).max));
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L82


## [G-18] Reduce require messages length to save contract size

```
require(
            _in.length > 0,
            "RLPReader: length of an RLP item must be greater than zero to be decodable"
        );
        
                require(
                firstByteOfContent != 0x00,
                "RLPReader: length of content must not have any leading zeros (long string)"
            );

            uint256 strLen;
            assembly {
                strLen := shr(sub(256, mul(8, lenOfStrLen)), mload(add(ptr, 1)))
            }

            require(
                strLen > 55,
                "RLPReader: length of content must be greater than 55 bytes (long string)"
            );

            require(
                _in.length > lenOfStrLen + strLen,
                "RLPReader: length of content must be greater than total length (long string)"
            );

            return (1 + lenOfStrLen, strLen, RLPItemType.DATA_ITEM);
        } else if (prefix <= 0xf7) {
            // Short list.
            // slither-disable-next-line variable-scope
            uint256 listLen = prefix - 0xc0;

            require(
                _in.length > listLen,
                "RLPReader: length of content must be greater than list length (short list)"
            );

            return (1, listLen, RLPItemType.LIST_ITEM);
        } else {
            // Long list.
            uint256 lenOfListLen = prefix - 0xf7;

            require(
                _in.length > lenOfListLen,
                "RLPReader: length of content must be > than length of list length (long list)"
            );

            bytes1 firstByteOfContent;
            assembly {
                firstByteOfContent := and(mload(add(ptr, 1)), shl(248, 0xff))
            }

            require(
                firstByteOfContent != 0x00,
                "RLPReader: length of content must not have any leading zeros (long list)"
            );

            uint256 listLen;
            assembly {
                listLen := shr(sub(256, mul(8, lenOfListLen)), mload(add(ptr, 1)))
            }

            require(
                listLen > 55,
                "RLPReader: length of content must be greater than 55 bytes (long list)"
            );

            require(
                _in.length > lenOfListLen + listLen,
                "RLPReader: length of content must be greater than total length (long list)"
            );
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L37

> All contests