# Low-Severity

## [L-01] Wrong slot mentioned

The mistake in the comment is that it mentions "Slots 3, 4, and 5" for **ctx, but it actually occupies only two slots. Therefore, the comment is incorrect in stating that** ctx takes up three slots.

Slot 1: `nextMessageId`
Slot 2: `messageStatus` (mapping), `addressBanned` (mapping)
Slots 3 and 4: `__ctx`
Slot 5: `proofReceipt` (mapping)

```solidity
File : packages/protocol/contracts/bridge/Bridge.sol

       /// @dev Slot 1.
31:    uint128 public nextMessageId;

       /// @notice Mapping to store the status of a message from its hash.
       /// @dev Slot 2.
35:    mapping(bytes32 msgHash => Status status) public messageStatus;

       /// @dev Slots 3, 4, and 5.
38:    Context private __ctx;

       /// @notice Mapping to store banned addresses.
       /// @dev Slot 6.
42:    mapping(address addr => bool banned) public addressBanned;

       /// @notice Mapping to store the proof receipt of a message from its hash.
       /// @dev Slot 7.
46:    mapping(bytes32 msgHash => ProofReceipt receipt) public proofReceipt;

```

[30-46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L30C4-L46C74)

## [L-02] Emit events before external call

Emitting events before external calls in Solidity enhances transaction atomicity, provides comprehensive event logging, helps protect against front-running attacks, improves user experience, and enables better gas optimization. It's a best practice that contributes to the security, transparency, and efficiency of smart contract development.

```solidity
File : packages/protocol/contracts/bridge/Bridge.sol

115:    function sendMessage(Message calldata _message)
...
150:         ISignalService(resolve("signal_service", false)).sendSignal(msgHash_);
151:         emit MessageSent(msgHash_, message_);

```

[150-151](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L150C1-L151C46)

## [L-03] Using a `constructor` and calling `disableInitializers` ensures that the contract's `initialization` logic is executed only once during deployment via the proxy

Using a constructor and calling disableInitializers in it is a common pattern used in upgradeable contracts implemented with the Proxy pattern. This pattern ensures that the contract `Bridge` can only be initialized once, typically during deployment through the proxy.

```solidity
File : packages/protocol/contracts/bridge/Bridge.sol

16:     contract Bridge is EssentialContract, IBridge {

```

[16](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L16)

## [L-04] `supportsInterface` function will result wrong output

By checking only for `IRecallableSender`, the `supportsInterface` function may return incorrect results for other interfaces implemented by the contract. This could lead to unexpected behavior or interoperability issues when interacting with the contract from other smart contracts or applications.

```solidity
File : packages/protocol/contracts/tokenvault/BaseVault.sol

39:    function supportsInterface(bytes4 _interfaceId) public view virtual override returns (bool) {
40:        return _interfaceId == type(IRecallableSender).interfaceId;
41:    }

```

[39-41](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L39C1-L41C6)

## [L-05] Missing `address(0)` check in functions

### Check `_snapshooter` for `address(0)`

Setting critical addresses, such as the `snapshooter`, to the zero address can lead to unexpected behavior within the contract. Including a check for the `zero` address helps prevent invalid operations or unintentional assignments. By explicitly disallowing the zero address, reducing the risk of mistakes or oversights during contract management.

```solidity
File : contracts/tokenvault/BridgedERC20.sol

80:    function setSnapshoter(address _snapshooter) external onlyOwner {
81:        snapshooter = _snapshooter;
82:     }

```

[80-82](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L80C1-L82C6)

### Check `_token` and `_vault` for `address(0)`

```solidity
File : contracts/team/airdrop/ERC20Airdrop.sol

27:    function init(
        address _owner,
        uint64 _claimStart,
        uint64 _claimEnd,
        bytes32 _merkleRoot,
        address _token,
        address _vault
    )
        external
        initializer
    {
        __Essential_init(_owner);
        __MerkleClaimable_init(_claimStart, _claimEnd, _merkleRoot);

41:        token = _token;
42:        vault = _vault;
    }

```

[27-43](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L27C1-L43C6)

## [L-06] Check that `_op.tokenIds` and `_op.amounts` have the same `length`

Ensuring that `_op.tokenIds` and `_op.amounts` have the same length before proceeding with the loop is crucial to prevent runtime errors, inconsistencies, or unintended consequences.
`_op.tokenIds` and `_op.amounts` likely correspond to each other, meaning that each token ID in `_op.tokenIds` corresponds to an amount in `_op.amounts`. If the lengths of these arrays are different, it suggests a data inconsistency or a mistake in how the data is being handled. Executing the loop without ensuring equal lengths could result in incorrect token burns, causing loss of tokens or other unexpected behavior.

```solidity
File : contracts/tokenvault/ERC1155Vault.sol

240:    function _handleMessage(
...
251:        for (uint256 i; i < _op.tokenIds.length; ++i) {
252:                    BridgedERC1155(_op.token).burn(_user, _op.tokenIds[i], _op.amounts[i]);
253:                }

```

[251-253](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L251C16-L253C18)

## [L-07] Solidity version 0.8.25 introduced the `tstore` and `tload` opcodes, which are not available in version 0.8.24 so code wont'even compile with mentioned version in files.

Using a Solidity compiler version 0.8.25 that supports those `tstore` and `tload` features. Attempting to compile code using features not available in the compiler version 0.8.24 will result in compilation errors.
If you encounter compilation errors due to incompatible features, use `tstore` and `tload`, you should use Solidity version `0.8.25` or later as your compiler version.

```solidity
File : contracts/common/EssentialContract.sol

02:  pragma solidity 0.8.24;

```

[02](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L2)

## [L-08] Risky unchecked as it may underflow when block is 0

The `parentId` is assigned the value of `block.number - 1`. However, if `block.number` is `0`, subtracting 1 from it would result in an `underflow`, as there are no negative block numbers. Solidity's arithmetic `underflow` behavior causes the result to wrap around to the maximum value of the data type. This could lead to unexpected behavior or vulnerabilities in your contract logic.
To mitigate this risk, you should explicitly check whether block.number is greater than 0 before performing the subtraction.

```solidity
File : contracts/L2/TaikoL2.sol

107:    function anchor(
...
126:        unchecked {
127:            parentId = block.number - 1;
128:        }

```

[126-128](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L126C1-L128C10)

## [L-09] `uint24` can hold till `194` days only so it little less to hold realistic `timestamp` use `uint32` or `uint48`

```solidity
File : contracts/L1/TaikoData.sol

10:      struct Config {
...
29:        // The max period in seconds that a blob can be reused for DA.
30:        uint24 blobExpiry;

```

[29-30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L29C1-L30C27)

## [L-10] Use `safeTransferFrom` instead of `transferFrom`

Using safeTransferFrom instead of transferFrom provides an additional layer of safety when transferring tokens in your Solidity smart contract. By using safeTransferFrom, you enhance the security and reliability of your contract when transferring tokens, reducing the risk of potential vulnerabilities or loss of funds.

```solidity
File : contracts/team/airdrop/ERC20Airdrop2.sol

88:   function withdraw(address user) external ongoingWithdrawals {

91:       IERC20(token).transferFrom(vault, user, amount);

```

[91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L91)

# Non Critical

## [N-01] Use underscore(`_`) for `internal`/`private` function

Using underscores (`_`) as a prefix for `internal` or `private` functions is a common convention in Solidity. This practice helps to clearly distinguish `internal` or `private` functions from `public` or `external` ones, making the code more readable and understandable.

```solidity
File : contracts/tokenvault/BaseVault.sol

47:      function checkProcessMessageContext()

```

[47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L47)

```solidity
File : contracts/L1/provers/Guardians.sol

124:     function deleteApproval(bytes32 _hash) internal {

128:     function isApproved(uint256 _approvalBits) internal view returns (bool) {

```

[124](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L124), [128](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L128)

## [N-02] Typo

### Correct the spelling of `setSnapshoter` to `setSnapshooter`

```diff
File : contracts/tokenvault/BridgedERC20.sol

79:      /// @param _snapshooter snapshooter address.
-80:      function setSnapshoter(address _snapshooter) external onlyOwner {
+80:      function setSnapshooter(address _snapshooter) external onlyOwner {

```

[79-80](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L79C4-L80C70)

## [N-03] Functions not used `internally` could be marked `external`

```solidity
File : contracts/bridge/Bridge.sol

352:         function proveMessageFailed(

374:         function proveMessageReceived(

403:         function context() public view returns (Context memory ctx_) {

```

[352](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L352), [374](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L374), [403](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L403)

## [N-04] Not using the named return variables anywhere in the function is confusing

Declaring named returns, but not using them, is confusing to the reader. Consider either completely removing them (by declaring just the type without a name), or remove the return statement and do a variable assignment.
This would improve the readability of the code, and it may also help reduce regressions during future code refactors.

```solidity
File : contracts/bridge/Bridge.sol

417:    function getInvocationDelays()
            public
            view
            virtual
421:        returns (uint256 invocationDelay_, uint256 invocationExtraDelay_)
        {
           if (
               block.chainid == 1 // Ethereum mainnet
            ){
                // For Taiko mainnet
                // 384 seconds = 6.4 minutes = one ethereum epoch
428:                return (1 hours, 384 seconds);
            } else if (
                block.chainid == 2 // Ropsten
                    || block.chainid == 4 // Rinkeby
                    || block.chainid == 5 // Goerli
                    || block.chainid == 42 // Kovan
                    || block.chainid == 17_000 // Holesky
                    || block.chainid == 11_155_111 // Sepolia
            ) {
               // For all Taiko public testnets
438:               return (30 minutes, 384 seconds);
            } else if (block.chainid >= 32_300 && block.chainid <= 32_400) {
                // For all Taiko internal devnets
441:                return (5 minutes, 384 seconds);
            } else {
                  // This is a Taiko L2 chain where no deleys are applied.
444:                  return (0, 0);
            }
        }

```

[417-446](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L417C5-L446C6)

## [N-05] Custom error without details

Consider adding some parameters to the error to indicate which user or values caused the failure.

```solidity
File : contracts/tokenvault/LibBridgedToken.sol

09:     error BTOKEN_INVALID_PARAMS();

```

[09](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L9)

```solidity
File : contracts/tokenvault/ERC20Vault.sol

136:     error VAULT_BTOKEN_BLACKLISTED();
137:     error VAULT_CTOKEN_MISMATCH();
138:     error VAULT_INVALID_TOKEN();
139:     error VAULT_INVALID_AMOUNT();
140:     error VAULT_INVALID_NEW_BTOKEN();
141:     error VAULT_INVALID_TO();
142:     error VAULT_NOT_SAME_OWNER();

```

[136-142](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L136C4-L142C34)

## [N-06] NatSpec: `Contract` declarations should have` @author` tags

```solidity
File : contracts/tokenvault/ERC20Vault.sol

18:     contract ERC20Vault is BaseVault {

```

[18](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L18)

## [N-07] NatSpec: `Error` missing NatSpec `@param` tag

```solidity
File : contracts/tokenvault/LibBridgedToken.sol

09:     error BTOKEN_INVALID_PARAMS();

```

[09](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L9)

```solidity
File : contracts/tokenvault/ERC20Vault.sol

136:     error VAULT_BTOKEN_BLACKLISTED();
137:     error VAULT_CTOKEN_MISMATCH();
138:     error VAULT_INVALID_TOKEN();
139:     error VAULT_INVALID_AMOUNT();
140:     error VAULT_INVALID_NEW_BTOKEN();
141:     error VAULT_INVALID_TO();
142:     error VAULT_NOT_SAME_OWNER();

```

[136-142](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L136C4-L142C34)

## [N-08] NatSpec: `Error` missing NatSpec `@dev` tag

```solidity
File : contracts/tokenvault/LibBridgedToken.sol

09:     error BTOKEN_INVALID_PARAMS();

```

[09](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/LibBridgedToken.sol#L9)

```solidity
File : contracts/tokenvault/ERC20Vault.sol

136:     error VAULT_BTOKEN_BLACKLISTED();
137:     error VAULT_CTOKEN_MISMATCH();
138:     error VAULT_INVALID_TOKEN();
139:     error VAULT_INVALID_AMOUNT();
140:     error VAULT_INVALID_NEW_BTOKEN();
141:     error VAULT_INVALID_TO();
142:     error VAULT_NOT_SAME_OWNER();

```

[136-142](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L136C4-L142C34)

## [N-09] NatSpec: `Event` missing NatSpec `@dev` tag

```solidity
File : contracts/bridge/IBridge.sol

       /// @notice Emitted when a message is sent.
       /// @param msgHash The hash of the message.
       /// @param message The message.
69:    event MessageSent(bytes32 indexed msgHash, Message message);

       /// @notice Emitted when a message is received.
       /// @param msgHash The hash of the message.
       /// @param message The message.
       /// @param isRecall True if the message is a recall.
75:    event MessageReceived(bytes32 indexed msgHash, Message message, bool isRecall);

       /// @notice Emitted when a message is recalled.
       /// @param msgHash The hash of the message.
79:    event MessageRecalled(bytes32 indexed msgHash);

       /// @notice Emitted when a message is executed.
       /// @param msgHash The hash of the message.
83:    event MessageExecuted(bytes32 indexed msgHash);

       /// @notice Emitted when a message is retried.
       /// @param msgHash The hash of the message.
87:    event MessageRetried(bytes32 indexed msgHash);

       /// @notice Emitted when the status of a message changes.
       /// @param msgHash The hash of the message.
       /// @param status The new status of the message.
92:    event MessageStatusChanged(bytes32 indexed msgHash, Status status);

       /// @notice Emitted when a message is suspended or unsuspended.
       /// @param msgHash The hash of the message.
       /// @param suspended True if the message is suspended.
97:    event MessageSuspended(bytes32 msgHash, bool suspended);

        /// @notice Emitted when an address is banned or unbanned.
        /// @param addr The address to ban or unban.
        /// @param banned True if the address is banned.
102:    event AddressBanned(address indexed addr, bool banned);

```

[66-102](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/IBridge.sol#L66C4-L102C60)

## [N-10] Use a single file for system wide constants

Consider grouping all the system constants under a single file. This finding shows only the first constant for each file, for brevity.

```solidity
File : contracts/bridge/Bridge.sol

24:    bytes32 private constant _CTX_SLOT =
           0xe4ece82196de19aabe639620d7f716c433d1348f96ce727c9989a982dbadc2b9;

27:    uint256 internal constant PLACEHOLDER = type(uint256).max;

```

[24](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L23C1-L24C76), [27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L27C5-L27C63)

```solidity
File : contracts/tokenvault/BaseNFTVault.sol

47:       bytes4 public constant ERC1155_INTERFACE_ID = 0xd9b67a26;

50:       bytes4 public constant ERC721_INTERFACE_ID = 0x80ac58cd;

53:       uint256 public constant MAX_TOKEN_PER_TXN = 10;

```

[47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L47), [50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L50), [53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L53)

## [N-11] Event is missing indexed fields

Index event fields make the field more quickly accessible to off-chain tools that parse events. However, note that each index field costs extra gas during emission, so it's not necessarily best to index the maximum allowed per event (three fields). Each event should use three indexed fields if there are three or more fields, and gas usage is not particularly of concern for the events in question. If there are fewer than three fields, all of the fields should be indexed.

```solidity
File : contracts/common/AddressManager.sol

21:    event AddressSet(
22:         uint64 indexed chainId, bytes32 indexed name, address newAddress, address oldAddress
23:     );

```

[21-23](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L21C4-L23C7)
