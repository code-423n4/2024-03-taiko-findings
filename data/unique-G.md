## \[G‑01\] Save gas by preventing zero amount in mint() and burn()

```
76:    _mint(_to, _tokenId, _amount, "");

110:  _burn(_account, _tokenId, _amount);
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L76

&nbsp;

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

&nbsp;

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

### **\[G-02\]** Compute known value `off-chain`

If You know what data to hash, there is no need to consume more computational power to hash it using keccak256 , you’ll end up consuming 2x amount of gas.

```
bytes32 public constant STATE_ROOT = keccak256("STATE_ROOT");

    /// @notice Keccak hash of the string "SIGNAL_ROOT".
    bytes32 public constant SIGNAL_ROOT = keccak256("SIGNAL_ROOT");
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/LibSignals.sol#L8C4-L11C68

## \[G-03\] Multiple accesses of a mapping/array should use a storage pointer

Caching a mapping’s value in a storage pointer when the value is accessed multiple times saves ~40 gas per access due to not having to perform the same offset calculation every time. Help the Optimizer by saving a storage variable’s reference instead of repeatedly fetching it.

&nbsp;

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

&nbsp;

## \[G-04\] When possible, use assembly instead of `unchecked{}`

You can also use unchecked{} for even more gas savings but this will not check to see if i overflows. For best gas savings, use inline assembly, however, this limits the functionality you can achieve.

> All contest

## \[G-05\] Use bytes32 rather than string/bytes.

If you can fit your data in 32 bytes, then you should use bytes32 datatype rather than bytes or strings as it is much cheaper in solidity. Basically, Any fixed size variable in solidity is cheaper than variable size.

```
string private __symbol;


    /// @dev Name of the bridged token.
    string private __name;
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L22C1-L25C27

&nbsp;

```
string name;
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L28

```
string symbol;
        // Name of the NFT.
        string name;
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L17C1-L19C21

## \[G-06\] Using assembly to revert with an error message

**Issue Description** - When reverting in solidity code, it is common practice to use a require or revert statement to revert execution with an error message. This can in most cases be further optimized by using assembly to revert with the error message.

**Estimated Gas Savings** - Here’s an example:

```
/// calling restrictedAction(2) with a non-owner address: 24042contract SolidityRevert {    address owner;    uint256 specialNumber = 1;    constructor() {        owner = msg.sender;    }    function restrictedAction(uint256 num)  external {        require(owner == msg.sender, "caller is not owner");        specialNumber = num;    }}/// calling restrictedAction(2) with a non-owner address: 23734contract AssemblyRevert {    address owner;    uint256 specialNumber = 1;    constructor() {        owner = msg.sender;    }    function restrictedAction(uint256 num)  external {        assembly {            if sub(caller(), sload(owner.slot)) {                mstore(0x00, 0x20) // store offset to where length of revert message is stored                mstore(0x20, 0x13) // store length (19)                mstore(0x40, 0x63616c6c6572206973206e6f74206f776e657200000000000000000000000000) // store hex representation of message                revert(0x00, 0x60) // revert with data            }        }        specialNumber = num;    }}
```

From the example above, we can see that we get a gas saving of over 300 gas when reverting with the same error message with assembly against doing so in solidity. This gas savings come from the memory expansion costs and extra type checks the solidity compiler does under the hood.

## \[G-07\] Don't `emit` `state` variable

```
emit Anchored(blockhash(parentId), gasExcess);
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L157

## \[G-08\] Mark initializer functions as payable to save deployment gas

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

&nbsp;

> All Initializer functions should marked as payable

## \[G-09\] Use assembly to validate `msg.sender`

We can use assembly to efficiently validate msg.sender for the didPay and uniswapV3SwapCallback functions with the least amount of opcodes necessary. Additionally, we can use xor() instead of iszero(eq()), saving 3 gas. We can also potentially save gas on the unhappy path by using scratch space to store the error selector, potentially avoiding memory expansion costs.

&nbsp;

```
_srcToken == address(0) || _srcChainId == 0 || _srcChainId == block.chainid
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L21

```
if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L91

&nbsp;

&nbsp;

```
if (btoken_ == address(0)) {
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L230

```
if (_btokenNew == address(0) || bridgedToCanonical[_btokenNew].addr != address(0)) {
```

&nbsp;https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L158

```
if (_op.token == address(0)) revert VAULT_INVALID_TOKEN();
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L149

```
if (_message.srcOwner == address(0) || _message.destOwner == address(0)) {
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L124

## \[G-10\] Use hardcode address instead `address(this)`

Instead of using `address(this)`, it is more gas-efficient to pre-calculate and use the hardcoded `address`. Foundry’s script.sol and solmate’s `LibRlp.sol` contracts can help achieve this.

References: <ins>https://book.getfoundry.sh/reference/forge-std/compute-create-address</ins>

<ins>https://twitter.com/transmissions11/status/1518507047943245824</ins>

&nbsp;

```
if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L91

```
t.safeTransferFrom(_user, address(this), _op.tokenIds[i]);
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L211

&nbsp;

```
if (_to == address(this)) revert BTOKEN_CANNOT_RECEIVE();
```

&nbsp;https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L137

```
signalService = address(this);
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L112

## \[G-11\] Do not calculate constants

Due to how constant variables are implemented (replacements at compile-time), an expression assigned to a constant variable is recomputed each time that the variable is used, which wastes some gas.

```
config_.gasTargetPerL1Block = 15 * 1e6 * 4;
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L213

## \[G-12\] Use constants instead of type(uintx).max

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

## \[G-13\] Amounts should be checked for 0 before calling a transfer

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

&nbsp;

## \[G-14\]use Mappings Instead of Arrays

Mappings, are useful when you need to store and access data based on a key, rather than an index. Mappings have a lower gas cost for read and write operations, especially when the size of the mapping is large, since Solidity can perform these operations based on the key directly, without needing to iterate over the entire data structure.

```
uint256[] tokenIds;
        // Amounts of tokens to transfer.
        uint256[] amounts;
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L33C1-L35C27

## \[G-15\] Reduce require messages length to save contract size

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
> 
> &nbsp;

## \[G-16\] Assigning keccak operations to constant variables results in extra gas costs

&nbsp;

```
bytes32 public constant STATE_ROOT = keccak256("STATE_ROOT");

    /// @notice Keccak hash of the string "SIGNAL_ROOT".
    bytes32 public constant SIGNAL_ROOT = keccak256("SIGNAL_ROOT");
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/LibSignals.sol#L8C4-L11C68

## \[GAS-17\] Constructors can be marked as payable to save deployment gas  
payable functions cost less gas to execute, since the compiler does not have to add extra checks to  
ensure that a payment wasn't provided.  
A constructor can safely be marked as payable , since only the deployer would be able to pass funds, and the project itself would not pass any funds.

&nbsp;

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

## \[G-18\] abi.encode() is less efficient than abi.encodePacked()

&nbsp;

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