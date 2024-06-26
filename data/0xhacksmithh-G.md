### [Gas-1] By re-arranging struct element extra storage slot can be saved (1SLOT saved)
Current implementation storage consumed
16bytes - 1st SLOT
20bytes - 2nd SLOT
8bytes + 8bytes - 3rd SLOT
20byes  - 4th SLOT
20byes  - 5th SLOT
20byes  - 6th SLOT
20byes  - 7th SLOT
32byes  - 8th SLOT
32byes  - 9th SLOT
32byes  - 10th SLOT
below 2 dynamic


3rd SLOT can be saved if we distribute both `uint64` to 2 different `address`
New implementation
16bytes - 1st SLOT
20bytes + 8bytes - 2nd SLOT
20byes + 8bytes - 3rd SLOT
20byes  - 4th SLOT
20byes  - 5th SLOT
20byes  - 6th SLOT
32byes  - 7th SLOT
32byes  - 8th SLOT
32byes  - 9th SLOT
below 2 dynamic
```diff
    struct Message {  // @audit G:: re-arrange save gas
        // Message ID whose value is automatically assigned.
        uint128 id; // 16bytes
        // The address, EOA or contract, that interacts with this bridge.
        // The value is automatically assigned.
        address from;
        // Source chain ID whose value is automatically assigned.
        uint64 srcChainId; // 8bytes
        // Destination chain ID where the `to` address lives.
        uint64 destChainId; // 8bytes
        // The owner of the message on the source chain.
        address srcOwner;
        // The owner of the message on the destination chain.
        address destOwner;
        // The destination address on the destination chain.
        address to;
        // Alternate address to send any refund on the destination chain.
        // If blank, defaults to destOwner.
        address refundTo;
        // value to invoke on the destination chain.
        uint256 value;
        // Processing fee for the relayer. Zero if owner will process themself.
        uint256 fee;
        // gasLimit to invoke on the destination chain.
        uint256 gasLimit;
        // callData to invoke on the destination chain.
        bytes data;
        // Optional memo.
        string memo;
    }
``` 
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L24-L26
```

### [Gas- 2] By reduing size of some `element` and re-arranging elements (1 storage SLOT) can saved
```solidity
    struct HopProof {
        uint64 chainId;  
        uint64 blockId;
        bytes32 rootHash;
        CacheOption cacheOption;
        bytes[] accountProof;
        bytes[] storageProof;
    }
```
Current implementation
8bytes + 8bytes - 1st SLOT
32bytes         - 2nd SLOT
20bytes         - 3rd SLOT
dynamic
dynamic

Now by reducing size of both `chainId` and `blockId` and re-arragning 1 storage slot can saved
`
1bytes + 1bytes + 20bytes - 1st SLOT // uint8 chainId + uint8 blockId + cacheOption
32bytes         - 2nd SLOT
dynamic
dynamic
`
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L20-L27
```

### [Gas- 3] Re-order modifiers
more efficient(i.e those modifier which consume less gas should be placed first)

```diff
    function mint(
        address _account,
        uint256 _tokenId
    )
        public
+       whenNotPaused 
        nonReentrant
-       whenNotPaused  // @audit G:: 
        onlyFromNamed("erc721_vault")
    {
        _safeMint(_account, _tokenId);
    }
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L58-L62

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L73-L76
```

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L72-L73

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L88-L91
```

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L40-L43

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L57

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L75
```

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L153-L155

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L210-L211

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L256-L257

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L291-L293
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L43
```


### [Gas- 4] Modifier Optimization
The code of modifiers is placed in a modified function, and modifier code is copied in all instances where it’s used. This will increase bytecode size and gas usage.

Below is one way to optimize modifier gas cost.

Before:
```solidity
modifier onlyOwner(){
   require(owner() == mag.sender, "Ownable: Caller is not the owner");
   _;
}
```


After:
```solidity
modifier onlyOwner() {
   _checkOwner();
   _;
}

function _checkOwner() internal view virtual{
   require(owner() == msg.sender, "Ownable: Caller is not the owner");
}
```


In this example, a refractor is done to the internal function _checkOwner(), allowing the internal function to be reused in modifiers. This method saves bytecode size and gas cost.

```diff
    modifier withValidOperation(BridgeTransferOp memory _op) {  
        if (_op.tokenIds.length != _op.amounts.length) {
            revert VAULT_TOKEN_ARRAY_MISMATCH();
        }

        if (_op.tokenIds.length > MAX_TOKEN_PER_TXN) {
            revert VAULT_MAX_TOKEN_PER_TXN_EXCEEDED();
        }

        if (_op.token == address(0)) revert VAULT_INVALID_TOKEN();
        _;
    }
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L140-L151
```

```diff
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L22-L27
```

```diff
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L
```
```diff
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L46-L51
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L36

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L41
```

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L39-L43
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L33-L38
```

### [Gas-5] Via re-arranging elements in `BlockParams` struct extra storage SLOT can saved
1 storage Slot saved via tight packing
```diff
    struct BlockParams {
        address assignedProver;
        address coinbase;
+       uint24 txListByteOffset;  
+       uint24 txListByteSize;
+       bool cacheBlobForReuse;
        bytes32 extraData;
        bytes32 blobHash;
-       uint24 txListByteOffset;  
-       uint24 txListByteSize;
-       bool cacheBlobForReuse;
        bytes32 parentMetaHash;
        HookCall[] hookCalls;
    }
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L83-L85
```


### [Gas-6] via moving `blockSyncThreshold` to near `ethDepositMaxAmount`, 1 extra storage SLOT will be saved
```diff
library TaikoData {
    /// @dev Struct holding Taiko configuration parameters. See {TaikoConfig}.
    struct Config {
        // ---------------------------------------------------------------------
        // Group 1: General configs
        // ---------------------------------------------------------------------
        // The chain ID of the network where Taiko contracts are deployed.
        uint64 chainId;
        // ---------------------------------------------------------------------
        // Group 2: Block level configs
        // ---------------------------------------------------------------------
        // The maximum number of proposals allowed in a single block.
        uint64 blockMaxProposals;
        // Size of the block ring buffer, allowing extra space for proposals.
        uint64 blockRingBufferSize;
        // The maximum number of verifications allowed when a block is proposed.
        uint64 maxBlocksToVerifyPerProposal; //// SLOT-1(8 + 8 + 8 + 8)
        // The maximum gas limit allowed for a block.
        uint32 blockMaxGasLimit;
        // The maximum allowed bytes for the proposed transaction list calldata.
        uint24 blockMaxTxListBytes;
        // The max period in seconds that a blob can be reused for DA.
        uint24 blobExpiry;
        // True if EIP-4844 is enabled for DA
        bool blobAllowedForDA;
        // True if blob can be reused
        bool blobReuseEnabled; 
        // ---------------------------------------------------------------------
        // Group 3: Proof related configs
        // ---------------------------------------------------------------------
        // The amount of Taiko token as a prover liveness bond
        uint96 livenessBond; //// SLOT-2 (4 + 3 + 3 + 1 + 1 + 12) = 24
        // ---------------------------------------------------------------------
        // Group 4: ETH deposit related configs
        // ---------------------------------------------------------------------
        // The size of the ETH deposit ring buffer.
        uint256 ethDepositRingBufferSize; /// SLOT-3
        // The minimum number of ETH deposits allowed per block.
        uint64 ethDepositMinCountPerBlock;
        // The maximum number of ETH deposits allowed per block.
        uint64 ethDepositMaxCountPerBlock;
        // The minimum amount of ETH required for a deposit.
        uint96 ethDepositMinAmount; /// SLOT-4 (8 + 8 + 12) = 28
        // The maximum amount of ETH allowed for a deposit.
        uint96 ethDepositMaxAmount; /// SLOT-5 (12)
+       uint8 blockSyncThreshold;
        // The gas cost for processing an ETH deposit.
        uint256 ethDepositGas; /// SLOT-6
        // The maximum fee allowed for an ETH deposit.
        uint256 ethDepositMaxFee; /// SLOT-7
        // The max number of L2 blocks that can stay unsynced on L1 (a value of zero disables
        // syncing)
-       uint8 blockSyncThreshold; // @audit G:: re-arrange to save gas /// SLOT-8
    }
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L59
```

### [Gas-7] Use `circuiting` method during condition check
By this method you first place more efficient(i.e more gas consuming) check eailier then followed by less efficient check

AS `blk.livenessBond` is a storage read.
```diff
- bool returnLivenessBond = blk.livenessBond > 0 && _proof.data.length == 32  // @audit G :: ciircuiting, chache blk.livenessBond
                && bytes32(_proof.data) == RETURN_LIVENESS_BOND;

+ bool returnLivenessBond = _proof.data.length == 32 && bytes32(_proof.data) == RETURN_LIVENESS_BOND && blk.livenessBond > 0;
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L192
``` 

### [Gas-8] Cache state variables accessed multiple times in the same function
#### `migratingAddress` could be cached in memory rather than calling 2 times
```diff
    function mint(address _account, uint256 _amount) public nonReentrant whenNotPaused {  // @audit G:: 
        // mint is disabled while migrating outbound.
        if (_isMigratingOut()) revert BB_MINT_DISALLOWED();

        if (msg.sender == migratingAddress) {  // @audit G:: cache
            // Inbound migration
            emit MigratedTo(migratingAddress, _account, _amount);
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L61-L63

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L80-L82
```

#### `gasExcess` could be cached in `memory`
```diff
        // gasExcess being 0 indicate the dynamic 1559 base fee is disabled.
+       uint256 _gasExcess = gasExcess;
        if (_gasExcess > 0) {
            // We always add the gas used by parent block to the gas excess
            // value as this has already happened
            uint256 excess = uint256(_gasExcess) + _parentGasUsed;
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L265
```

#### `shareVault` could be cached in `memory`
```diff
    function _withdraw(address _recipient, address _to) private {
        Recipient storage r = recipients[_recipient];

        (,,, uint128 amountToWithdraw, uint128 costToWithdraw) = getMyGrantSummary(_recipient);

        r.amountWithdrawn += amountToWithdraw;
        r.costPaid += costToWithdraw;

        totalAmountWithdrawn += amountToWithdraw;
        totalCostPaid += costToWithdraw;
+       address _sharedVault = sharedVault;

-       IERC20(taikoToken).transferFrom(sharedVault, _to, amountToWithdraw);
-       IERC20(costToken).safeTransferFrom(_recipient, sharedVault, costToWithdraw);

+       IERC20(taikoToken).transferFrom(_sharedVault, _to, amountToWithdraw);
+       IERC20(costToken).safeTransferFrom(_recipient, _sharedVault, costToWithdraw);

        emit Withdrawn(_recipient, _to, amountToWithdraw, costToWithdraw);
    }
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L219
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L220
```


### [Gas-9] Use `mappings` instead of `ARRAYs`
```
    address[] public guardians;
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L23
```


### [Gas-10] Rather than calculating same expression repeatedly inside a loop it should be cached in `memory`
`hopProofs.length - 1` should cached to memory
```
        HopProof memory hop;
+       uint256 len =  hopProofs.length;
+       uint256 compLen = len - 1;
        for (uint256 i; i < hopProofs.length; ++i) {
            hop = hopProofs[i];

            bytes32 signalRoot = _verifyHopProof(chainId, app, signal, value, hop, signalService);  
-           bool isLastHop = i == hopProofs.length - 1;

+           bool isLastHop = i == compLen - 1;
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L108
```

### [Gas-11] Instead of caching to `memory` variable directly use in code, as it only once used
```
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L127
```
```diff
-       uint256 expectedAmount = _message.value + _message.fee;  
-       if (expectedAmount != msg.value) revert B_INVALID_VALUE();

+       if (_message.value + _message.fee) revert B_INVALID_VALUE();



-       bool isMessageProven = receivedAt != 0;  
-       if (!isMessageProven) {

+       if (!(receivedAt != 0)) {
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L138
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L169
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L231
```

```diff
        bytes32 signal = signalForChainData(_chainId, _kind, _blockId); 
        return _loadSignalValue(address(this), signal) == _chainData;
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L148
```

### [Gas-12] `const` should be value rather than expression, and comment should present which explain how that value got(expression should in comment)
```diff
    bytes32 public constant STATE_ROOT = keccak256("STATE_ROOT");  
    /// @notice Keccak hash of the string "SIGNAL_ROOT".
    bytes32 public constant SIGNAL_ROOT = keccak256("SIGNAL_ROOT");
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/LibSignals.sol#L8
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/LibSignals.sol#L11
```

### [Gas-13] `keccak256(` hshing should be `immutable` instead of `constant`
```diff
    bytes32 public constant STATE_ROOT = keccak256("STATE_ROOT");  

    /// @notice Keccak hash of the string "SIGNAL_ROOT".
    bytes32 public constant SIGNAL_ROOT = keccak256("SIGNAL_ROOT");
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/LibSignals.sol#L8
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/LibSignals.sol#L11
```

### [Gas-14] Instead of Using `migratingAddress` and calling it 2 times directly we could use `msg.sender` in emit, due to above `if` condition check.

```diff
....
....
        if (_isMigratingOut()) revert BB_MINT_DISALLOWED();

        if (msg.sender == migratingAddress) {  // @audit G:: cache
            // Inbound migration
 -          emit MigratedTo(migratingAddress, _account, _amount);
 +          emit MigratedTo(msg.sender, _account, _amount);
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L61-L63

```
```
```
```
```
### [Gas-15] Use assembly to write mutable storage values
```diff
        if (_migratingAddress == migratingAddress && _migratingInbound == migratingInbound) {
            revert BB_INVALID_PARAMS();
        }

        migratingAddress = _migratingAddress;  // @audit G:: write to stoage through assembly
        migratingInbound = _migratingInbound;
        emit MigrationStatusChanged(_migratingAddress, _migratingInbound);
    }
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L49-L50
```

### [Gas-16] Use unchecked for %
```
inputs[_blockId % 255] = blockhash(_blockId);
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L246
```

### [Gas-17] abi.encodePacked is more gas efficient than abi.encode
```
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L450
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L186
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L186
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L203
```

### [Gas-18] Multiple address/ID mappings can be combined into a single mapping of an address/ID to a struct
```solidity
mapping(uint256 chainId => mapping(address ctoken => address btoken)) public canonicalToBridged;
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L59
```

```diff
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L49
```

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L12
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L17
```



### [Gas-19] Inheritance Re-ordering May save gas
```diff

abstract contract BaseVault is
    EssentialContract,
    IRecallableSender,
    IMessageInvocable,
    IERC165Upgradeable
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L13-L16
```

### [Gas-20] Improve `imports` importing
```
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L6-L9
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L4
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L8-L11
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L5-L8
```

### [Gas-21] Split Or conditions [If(||)], which consumes more gas than normal
```
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L21-L22
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L108
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L124
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L270
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L321
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L405
```

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L114
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L131
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L274
```

### [Gas-22] Use `named return` value for `pure` functions
```
    function skipFeeCheck() public pure virtual returns (bool) {  
        return false;
    }
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L219
```



### [Gas-23] Use `self.balance()` instead of `address(this)`
```diff
        if (_token == address(0)) {
 -          _to.sendEther(address(this).balance);

 +          _to.sendEther(self.balance);
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L174
```



### [Gas-24] Some state variable could be `private` rather than `public` to save some gas
```
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L16
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L11
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L43
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L47
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L50
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L13
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L59-L77
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L13
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L16
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L15
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L21
```

### [Gas-25] Some public functions could be `external`
```
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L69
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L78
```




### [Gas-26] No need for `Type casting`
```diff
receivedAt = uint64(block.timestamp);
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L89
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L183
```

### [Gas-27] `memory` Variable should created outside of the `loop` and it get overriden with each iteration of loop so that creation cost for variable will save every time.
```diff
 +      bytes32 signalRoot 
 +      bool isLastHop 
        HopProof memory hop;
        for (uint256 i; i < hopProofs.length; ++i) {
            hop = hopProofs[i];

 -          bytes32 signalRoot = _verifyHopProof(chainId, app, signal, value, hop, signalService);  
 -          bool isLastHop = i == hopProofs.length - 1;

 +          signalRoot = _verifyHopProof(chainId, app, signal, value, hop, signalService);  
 +          isLastHop = i == hopProofs.length - 1;
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L107
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L108
```
```diff
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L91
```

### [Gas-28] use `delete` instead of setting to `default`
```diff
    function _voidGrant(Grant storage _grant) private returns (uint128 amountVoided) {
        uint128 amountOwned = _getAmountOwned(_grant);

        amountVoided = _grant.amount - amountOwned;
        _grant.amount = amountOwned;

        _grant.grantStart = 0;
        _grant.grantPeriod = 0;
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L231
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L232
```

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L111
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L114
```

### [Gas-29] `_hop.cacheOption == CacheOption.CACHE_BOTH` this expression is repeated in code base, so it should be cached
```diff
+       bool res = _hop.cacheOption == CacheOption.CACHE_BOTH;
        // cache state root
-       bool cacheStateRoot = _hop.cacheOption == CacheOption.CACHE_BOTH 
            || _hop.cacheOption == CacheOption.CACHE_STATE_ROOT;
+       bool cacheStateRoot = res || _hop.cacheOption == CacheOption.CACHE_STATE_ROOT;

        if (cacheStateRoot && _isFullProof && !_isLastHop) {  
            _syncChainData(_chainId, LibSignals.STATE_ROOT, _blockId, _hop.rootHash);
        }

        // cache signal root
-       bool cacheSignalRoot = _hop.cacheOption == CacheOption.CACHE_BOTH
            || _hop.cacheOption == CacheOption.CACHE_SIGNAL_ROOT;

+       bool cacheSignalRoot = res
            || _hop.cacheOption == CacheOption.CACHE_SIGNAL_ROOT;

        if (cacheSignalRoot && (_isFullProof || !_isLastHop)) {
            _syncChainData(_chainId, LibSignals.SIGNAL_ROOT, _blockId, _signalRoot);
        }
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L282-L283
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L290-L291
```

### [Gas-30] Instead of first creating `variable` and then assigning value to it, we could directly assign value at time of creation of memory which is more gas efficient.
```diff
        uint256 parentId;
        unchecked {
            parentId = block.number - 1;  
        }
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L127
```

### [Gas-31] Use Fixed-Size Variables Instead of Dynamic
Using bytes32 datatype instead of bytes or strings is recommended if the data can fit in 32 bytes. In general, any fixed-size variable is less expensive than a variable-size one. If the length of bytes can be limited, use the lowest amount possible from bytes1 to bytes32.

Before
```diff
string a;

function add(string str) public {
   a= str;
}
```

After
```diff
bytes32 a;

function add(bytes32 str) public {
   a = str;
}
```
```diff
    struct CanonicalERC20 {
        uint64 chainId;
        address addr;
        uint8 decimals;
 -      string symbol;  // @audit G:: 
 -      string name;

 +      string symbol;  // @audit G:: 
 +      string name;
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L27-L28
```

### [Gas-32] Use assembly for Efficient Event Emission
```
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L93
```



### [Gas-33] Nesting if-statements is cheaper than using &&
```
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L141
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L275
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L85
```

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L250
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L260
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L490-L494
```

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L285
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L277
```




### [Gas-34] Simple checks for zero can be done using assembly to save gas
```
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L214
```
```diff
        if (_adjustmentFactor == 0) {  // @audit G:: 
            revert EIP1559_INVALID_PARAMS();
        }
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L24
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L33
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L34
```

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L176
```

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L485
```

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L341
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L360
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L382
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibTrieProof.sol#L50
```

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L95
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L114
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L131
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L172
```

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L154
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L255
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L256
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L268
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L274
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L111
```





### [Gas-35] Refactor code base
AS 
```solidity
if (_message.srcChainId != block.chainid) return false;
```
is a code segment which repeated 3 times in `Bridge.sol` contract file

So this should be refactore to a private function and used in following senarios
This will save Deployment Gas & Satisfy DRY-principle of coding

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L382
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L360
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L341
```



### [Gas-36] Assembly: Use scratch space for calculating small keccak256 hashes
```
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L450
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L68
```


### [Gas-37] Common Calculation could be hardcoded in a `constant` state variable.
```
    function getConfig() public view virtual returns (Config memory config_) {
        // 4x Ethereum gas target, if we assume most of the time, L2 block time
        // is 3s, and each block is full (gasUsed is 15_000_000), then its
        // ~60_000_000, if the  network is congester than that, the base fee
        // will increase.
-       config_.gasTargetPerL1Block = 15 * 1e6 * 4;  
+       config_.gasTargetPerL1Block = CONST_RES; // CONST_RES = 15 * 1e6 * 4
        config_.basefeeAdjustmentQuotient = 8;
    }
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L213
```






### [Gas-38] Use assembly to check for address(0)
```
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L158
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L170
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L267
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L397
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L108
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L62
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L81
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L121
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L124
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L127
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L136
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L169
```



### [Gas-39] Use unchecked for Non-Loop Increment/Decrement Operations
```diff
        (bool success,) = address(this).call(txdata); 
        if (!success) revert XCO_TX_REVERTED();

-       emit TransactionExecuted(nextTxId++, bytes4(txdata)); 

+       unchecked {
+       emit TransactionExecuted(nextTxId++, bytes4(txdata)); 
+       }
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L53
```
```diff
+  message_.id = nextMessageId++; 
-  unchecked { message_.id = nextMessageId++; }
```

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L144
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L258
```

### [Gas-40] Consider pre-calculating the address of address(this) to save gas
```
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L378
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L379
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L390
```

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L343
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L270
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L196
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L174
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L486
```





### [Gas-41] `0` trasfer amount check before token transfer
```diff
    {
        if (_to == address(0)) revert L2_INVALID_PARAM();
        if (_token == address(0)) {
            _to.sendEther(address(this).balance);
        } else {
-           IERC20(_token).safeTransfer(_to, IERC20(_token).balanceOf(address(this))); 

+           uint256 amount = IERC20(_token).balanceOf(address(this));
+           if(amount != 0){
+           IERC20(_token).safeTransfer(_to, amount);

+         }
        }
    }
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L176
```

### [Gas-42] Instead of `block.number - 1` calculation directly 0 could used as here `block.number == 1`
```diff
        if (block.number == 0) {
            // This is the case in real L2 genesis
        } else if (block.number == 1) {
            // This is the case in tests
-           uint256 parentHeight = block.number - 1;  
-           l2Hashes[parentHeight] = blockhash(parentHeight);
+           l2Hashes[0] = blockhash(0); // As block.number - 1 = 0
        } else {
            revert L2_TOO_LATE();
        }
```
```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L86-L94
```



### [Gas-43] Replace OpenZeppelin components with Solady equivalents to save gas
```
Multiple instances
```
```
```
### [Gas-44] Use calldata instead of memory for function arguments that are read only
```
Multiple instances
```
```
```
### [Gas-45] Use Assembly for Efficient Memory Management in Multiple External Calls
```
specifically when external call, appear inside loop
```
```
```


### [Gas-46] Constructors can be marked payable
```
All cases
```
```
```

### [Gas-47] Enable IR-based code generation
By using --via-ir or {"viaIR": true}, the compiler is able to use more advanced multi-function optimizations, for extra gas savings.
```
```
```
```


### [Gas-48] Optimize names to save gas
public/external function names and public member variable names can be optimized to save gas. See this link for an example of how it works. Below are the interfaces/abstract contracts that can be optimized so that the most frequently-called functions use the least amount of gas possible during method lookup. Method IDs that have two leading zero bytes can save 128 gas each during deployment, and renaming functions to have lower method IDs will save 22 gas per call, per sorted position shifted
```
```
```
```


