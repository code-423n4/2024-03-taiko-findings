## [G-01] Using private rather than public for constants, and other storage variables saves Gas

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressResolver.sol#L13

```solidity
address public addressManager;
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/Lib4844.sol#L10C4-L17C112

```solidity
address public constant POINT_EVALUATION_PRECOMPILE_ADDRESS = address(0x0A);

/// @notice The number of field elements per blob
uint32 public constant FIELD_ELEMENTS_PER_BLOB = 4096;

/// @notice The modulus of the BLS curve
uint256 public constant BLS_MODULUS =
     52_435_875_175_126_190_479_447_740_508_185_965_837_690_552_500_527_637_822_603_658_699_938_581_184_513;
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L23C5-L30C32

```solidity
    address[] public guardians;

    /// @notice The version of the guardians
    /// @dev Slot 4
    uint32 public version;

    /// @notice The minimum number of guardians required to approve
    uint32 public minGuardians;
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L24


```solidity
    TaikoData.State public state;
```
 
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L39C4-L50C35

```solidity
    mapping(uint256 blockId => bytes32 blockHash) public l2Hashes;


    /// @notice A hash to check the integrity of public inputs.
    /// @dev Slot 2.
    bytes32 public publicInputHash;


    /// @notice The gas excess value used to calculate the base fee.
    /// @dev Slot 3.
    uint64 public gasExcess;


    /// @notice The last synced L1 block height.
    uint64 public lastSyncedBlock;
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L11

```solidity
    Config public customConfig;
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L17C5-L21C66

```solidity
    mapping(uint64 chainId => mapping(bytes32 kind => uint64 blockId)) public topBlockId;


    /// @notice Mapping to store the authorized addresses.
    /// @dev Slot 2.
    mapping(address addr => bool authorized) public isAuthorized;

```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L31C4-L35C68

```solidity
    uint128 public nextMessageId;


    /// @notice Mapping to store the status of a message from its hash.
    /// @dev Slot 2.
    mapping(bytes32 msgHash => Status status) public messageStatus;
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L42C5-L46C74

```solidity
    mapping(address addr => bool banned) public addressBanned;


    /// @notice Mapping to store the proof receipt of a message from its hash.
    /// @dev Slot 7.
    mapping(bytes32 msgHash => ProofReceipt receipt) public proofReceipt;
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L31

```solidity
    IUSDC public usdc;
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L22C5-L32C31

```solidity
    address public srcToken;

    uint256 public srcChainId;

    address public snapshooter;

```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L11C5-L14C34

```solidity
    address public migratingAddress;

    bool public migratingInbound;
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L14C4-L17C31

```solidity
    address public srcToken;

    uint256 public srcChainId;
```


https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L16C5-L19C31

```solidity
    address public srcToken;

    uint256 public srcChainId;
```


https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L56C5-L59C101


```solidity
    mapping(address btoken => CanonicalNFT canonical) public bridgedToCanonical;

    mapping(uint256 chainId => mapping(address ctoken => address btoken)) public canonicalToBridged;

```


https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L45C4-L52C72


```solidity
    mapping(address btoken => CanonicalERC20 canonical) public bridgedToCanonical;


    /// @notice Mappings from canonical tokens to their bridged tokens. Also storing
    /// the chainId for tokens across other chains aside from Ethereum.
    mapping(uint256 chainId => mapping(address ctoken => address btoken)) public canonicalToBridged;


    /// @notice Mappings from bridged tokens to their blacklist status.
    mapping(address btoken => bool blacklisted) public btokenBlacklist;

```



https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L7C5-L8C92


```solidity
    uint128 public constant MAX_EXP_INPUT = 135_305_999_368_893_231_588;
    uint256 public constant SCALING_FACTOR = 1e18; // For fixed point representation factor
```


https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L39C5-L55C87


```solidity
    uint256 public nextInstanceId;

    mapping(uint256 instanceId => Instance instance) public instances;

    mapping(address instanceAddress => bool alreadyAttested) public addressRegistered;
```


https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L13C4-L16C26


```solidity

    address public token;


    /// @notice The address of the vault contract.
    address public vault;

```


https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L16C4-L28C36


```solidity

    address public token;


    /// @notice The address of the vault contract.
    address public vault;


    /// @notice Represents the token amount for which the user has claimed.
    mapping(address addr => uint256 amountClaimed) public claimedAmount;


    /// @notice Represents the already withdrawn amount.
    mapping(address addr => uint256 amountWithdrawn) public withdrawnAmount;


    /// @notice Length of the withdrawal window.
    uint64 public withdrawalWindow;

```


https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L11C4-L14C26


```solidity
    address public token;


    /// @notice The address of the vault contract.
    address public vault;
```


https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/MerkleClaimable.sol#L12C5-L21C28


```solidity
    mapping(bytes32 hash => bool claimed) public isClaimed;


    /// @notice Merkle root of the tree
    bytes32 public merkleRoot;


    /// @notice Unix timestamp for claim start
    uint64 public claimStart;


    /// @notice Unix timestamp for claim end
    uint64 public claimEnd;
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L59C4-L80C71


```solidity
    address public taikoToken;


    /// @notice The cost token address.
    address public costToken;


    /// @notice The shared vault address.
    address public sharedVault;


    /// @notice The total amount of tokens granted.
    uint128 public totalAmountGranted;


    /// @notice The total amount of tokens voided.
    uint128 public totalAmountVoided;


    /// @notice The total amount of tokens withdrawn.
    uint128 public totalAmountWithdrawn;


    /// @notice The total cost paid.
    uint128 public totalCostPaid;


    /// @notice Mapping of recipient address to grant information.
    mapping(address recipient => Recipient receipt) public recipients;
```


https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L25C5-L26C50


```solidity
    ISigVerifyLib public immutable sigVerifyLib;
    IPEMCertChainLib public immutable pemCertLib;
```


https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L49C4-L52C26


```solidity
    mapping(string fmspc => TCBInfoStruct.TCBInfo tcbInfo) public tcbInfo;
    
    address public owner;
```


## [G-02] Directly using storage variables in for loop is very gas expensive instead cache storage variables inside function and use it in loops

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L74


```solidity
        for (uint256 i; i < guardians.length; ++i) {
            delete guardianIds[guardians[i]];
        }

```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L74C9-L89C10


```solidity
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
```



## [G-03] Use Custom Errors instead of Revert Strings to save Gas

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L172C12-L271C1


```solidity
            require(
                _in.length > strLen,
                "RLPReader: length of content must be greater than string length (short string)"
            );


            bytes1 firstByteOfContent;
            assembly {
                firstByteOfContent := and(mload(add(ptr, 1)), shl(248, 0xff))
            }


            require(
                strLen != 1 || firstByteOfContent >= 0x80,
                "RLPReader: invalid prefix, single byte < 0x80 are not prefixed (short string)"
            );


            return (1, strLen, RLPItemType.DATA_ITEM);
        } else if (prefix <= 0xbf) {
            // Long string.
            uint256 lenOfStrLen = prefix - 0xb7;


            require(
                _in.length > lenOfStrLen,
                "RLPReader: length of content must be > than length of string length (long string)"
            );


            bytes1 firstByteOfContent;
            assembly {
                firstByteOfContent := and(mload(add(ptr, 1)), shl(248, 0xff))
            }


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


            return (1 + lenOfListLen, listLen, RLPItemType.LIST_ITEM);
        }
    }
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L125C16-L128C23


```solidity
                    require(
                        
                        "MerkleTrie: value node must be last node in proof (branch)"
                    );
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L150C16-L153C19


```solidity
                require(
                    pathRemainder.length == sharedNibbleLength,
                    "MerkleTrie: path remainder must share all nibbles with key"
                );
```


## [G-04] write uint256 index; instead of writing uint256 index = 0; as being a uint256, it will be 0 by default so you can save some gas by avoiding initialization.

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L85

```solidity
        for (uint256 i = 0; i < proof.length; i++) {
```

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L208


```solidity
        for (uint256 i = 0; i < length;) {
```



