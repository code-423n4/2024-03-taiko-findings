# Gas Optimizations

**Note: These all are unique findings are not present in analyzer report. Gas Mentioned in these findings title is total gas saved by all instances of that finding covered in this report.**

## Auditor's Disclaimer :

All these findings are good findings and 100% safe to implement at no security/logic risk. They all are found by thorough manual review.
Total 36 Findings

## [G-01] Use `safeBatchTransferFrom` instead of using `safeTransferFrom` in loop when from and to is same in all iterations **avoid complete loop use** and external calls.

Since from and to are same in all iterations so it is recommended to use safeBatchTransferFrom of ERC1155 standard.
**Use of safeBatchTransferFrom**: Instead of individually transferring each ERC1155 tokenId amounts in a loop, the recommendation is to use the `safeBatchTransferFrom` function provided by the ERC1155 standard. This function allows for batch transfers of multiple tokens in a single external call, thereby reducing gas costs and simplifying the code.

**Efficiency and Convenience**: Using `safeBatchTransferFrom` eliminates the need for a loop and multiple external calls, as it handles batch transfers efficiently in a single call. This can significantly reduce gas costs and improve the overall performance of the contract.

**Callback Handling**: Additionally, `safeBatchTransferFrom` ensures that any callback functions defined in the receiving contract (e.g., onERC1155BatchReceived) are invoked only once per batch transfer, rather than multiple times for each individual transfer. This further enhances efficiency gas savings and simplifies contract logic.

```solidity
File : tokenvault/ERC1155Vault.sol

269: for (uint256 i; i < _op.tokenIds.length; ++i) {
270:   IERC1155(_op.token).safeTransferFrom({
271:        from: msg.sender,
272:        to: address(this),
273:        id: _op.tokenIds[i],
274:        amount: _op.amounts[i],
275:        data: ""
276:    });
277: }

```

ERC1155Vault.sol#L269-L277[](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L269-L277)

**Recommended Mitigation Steps:**

```diff
File : tokenvault/ERC1155Vault.sol

-269: for (uint256 i; i < _op.tokenIds.length; ++i) {
-270:   IERC1155(_op.token).safeTransferFrom({
-271:        from: msg.sender,
-272:        to: address(this),
-273:        id: _op.tokenIds[i],
-274:        amount: _op.amounts[i],
-275:        data: ""
-276:    });
-277: }
+   IERC1155(_op.token).safeBatchTransferFrom(
+        msg.sender,
+        address(this),
+         _op.tokenIds,
+         _op.amounts,
+         ""
+    );
+ }

```

## [G-02] State variables can be packed into fewer storage slot by reducing their size (**Saves ~6000 Gas**)

The EVM works with 32 byte words. Variables less than 32 bytes can be declared next to each other in storage and this will pack the values together into a single 32 byte storage slot (if values combined are <= 32 bytes). If the variables packed together are retrieved together in functions (more likely with structs), we will effectively save ~2000 gas with every subsequent SLOAD for that storage slot. This is due to us incurring a Gwarmaccess (100 gas) versus a Gcoldsload (2100 gas).

**Total Gas Saved: ~6000 Gas**
**Gas Per Instance: ~2000 Gas**

The size of `srcChainId` can be reduced to uint64 Since [`struct CanonicalNFT`](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L11-L13), [`struct BridgeTransferOp`](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L23-L25), [`struct CanonicalERC20`](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L23-L24) and [`struct BridgeTransferOp`](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L32-L33) in these four struct the `chainId` and the `destChainId` is `uint64`. So we can easily reduce `srcChainId` to `uint64`. And chainId is accessed from here using context function in [BaseVault](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L53C8-L53C46) which is inherited in ERC20Vault and chainId is assigned from that ctx. So it can be safely reduced here in BridgedERC20.sol , BridgedERC721.sol and BridgedERC1155.sol to uint64 to save storage slots.

### `srcChainId` and address `snapshooter` can be packed in a single slot in `BridgedERC20` contract `SAVES: ~2000 Gas, 1 Slot`

```solidity
File : contracts/tokenvault/BridgedERC20.sol

27:   uint256 public srcChainId;
28:
29:    /// @dev Slot 3.
30:    address public snapshooter;

```

[BridgedERC20.sol#L27-L30](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L27-L30)

**Recommended Mitigation Steps:**

```diff
File : contracts/tokenvault/BridgedERC20.sol

-27:   uint256 public srcChainId;
28:
29:    /// @dev Slot 3.
30:    address public snapshooter;
+      uint64 public srcChainId;

```

### `srcChainId` and address `srcToken` can be packed in a single slot in `BridgedERC721` contract `SAVES: ~2000 Gas, 1 slot`

```solidity
File : tokenvault/BridgedERC721.sol

14:  address public srcToken;
15:
16:  /// @notice Source chain ID where the token originates.
17:  uint256 public srcChainId;

```

[BridgedERC721.sol#L14-L17](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L14-L17)

**Recommended Mitigation Steps:**

```diff
File : tokenvault/BridgedERC721.sol

14:  address public srcToken;
+    uint64 public srcChainId;
15:
16:  /// @notice Source chain ID where the token originates.
-17:  uint256 public srcChainId;

```

### `srcChainId` and address `srcToken` can be packed in a single slot in `BridgedERC1155` contract `SAVES: ~2000 Gas, 1 slot`

```solidity
File : tokenvault/BridgedERC1155.sol

16: address public srcToken;
17:
18: /// @notice Source chain ID where the token originates.
19: uint256 public srcChainId;

```

[BridgedERC1155.sol#L16-L19](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L16-L19)

**Recommended Mitigation Steps:**

```diff
File : tokenvault/BridgedERC1155.sol

16: address public srcToken;
+   uint64 public srcChainId;
17:
18: /// @notice Source chain ID where the token originates.
-19: uint256 public srcChainId;

```

## [G-03] Reduce the size of struct variables by truncating timestamp and pack them together to save storage slots (**Saves ~2000 Gas**)

### `SAVE: ~2000 GAS, 1 SLOT`

### `grantStart` ,`unlockStart`,`grantCliff`,`unlockCliff` can be reduced to `uint48` since they hold time in seconds and uint48 is more than enough to hold any realistic time and pack them with `unlockPeriod`and`grantPeriod` in one slot to save 1 slot(~2000 Gas).

48,48,32,48,48,32 becomes 256 so they can come into 1 storage slot.

uint48 can hold more than 3 Million years

```solidity
File : team/TimelockTokenPool.sol

28:   struct Grant {
29:        uint128 amount;
        // If non-zero, each TKO (1E18) will need some USD stable to purchase.
31:        uint128 costPerToken;
        // If non-zero, indicates the start time for the recipient to receive
        // tokens, subject to an unlocking schedule.
34:        uint64 grantStart;
        // If non-zero, indicates the time after which the token to be received
        // will be actually non-zero
37:        uint64 grantCliff;
        // If non-zero, specifies the total seconds required for the recipient
        // to fully own all granted tokens.
40:        uint32 grantPeriod;
        // If non-zero, indicates the start time for the recipient to unlock
        // tokens.
43:        uint64 unlockStart;
        // If non-zero, indicates the time after which the unlock will be
        // actually non-zero
46:        uint64 unlockCliff;
        // If non-zero, specifies the total seconds required for the recipient
        // to fully unlock all owned tokens.
49:        uint32 unlockPeriod;
50:    }
```

[TimelockTokenPool.sol#L28-L50](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L28-L50)

**Recommended Mitigation Steps:**

```diff
File : team/TimelockTokenPool.sol

28:   struct Grant {
29:        uint128 amount;
        // If non-zero, each TKO (1E18) will need some USD stable to purchase.
31:        uint128 costPerToken;
        // If non-zero, indicates the start time for the recipient to receive
        // tokens, subject to an unlocking schedule.
-34:        uint64 grantStart;
+         uint48 grantStart;
        // If non-zero, indicates the time after which the token to be received
        // will be actually non-zero
- 37:        uint64 grantCliff;
+ 37:        uint48 grantCliff;
        // If non-zero, specifies the total seconds required for the recipient
        // to fully own all granted tokens.
40:        uint32 grantPeriod;
        // If non-zero, indicates the start time for the recipient to unlock
        // tokens.
-43:        uint64 unlockStart;
+         uint48 unlockStart;
        // If non-zero, indicates the time after which the unlock will be
        // actually non-zero
- 46:        uint64 unlockCliff;
+ 46:        uint48 unlockCliff;
        // If non-zero, specifies the total seconds required for the recipient
        // to fully unlock all owned tokens.
49:        uint32 unlockPeriod;
50:    }

```

## [G-04] Cache `hopProofs.length - 1` outside loop to **avoid 1 checked subtraction every iterations saves ~110 Gas on every iteration**

```solidity
File : signal/SignalService.sol

104:   for (uint256 i; i < hopProofs.length; ++i) {
105:        hop = hopProofs[i];
106:
107:         bytes32 signalRoot = _verifyHopProof(chainId, app, signal, value, hop, signalService);
108:         bool isLastHop = i == hopProofs.length - 1;
```

[SignalService.sol#L104-L108](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L104-L108)

**Recommended Mitigation Steps:**

```diff
File : signal/SignalService.sol

+     uint256 hopProofs_lengh_sub_1 = hopProofs.length - 1;
104:   for (uint256 i; i < hopProofs.length; ++i) {
105:        hop = hopProofs[i];
106:
107:         bytes32 signalRoot = _verifyHopProof(chainId, app, signal, value, hop, signalService);
-108:         bool isLastHop = i == hopProofs.length - 1;
+          bool isLastHop = i == hopProofs_lengh_sub_1;
```

## [G-05] Cache state variable outside of the loop instead of reading same variable in each iteration (**Saves 2 SLOAD(~194 Gas) Per iteration**)

### Cache `token` and `vault` outside of the loop to save `2 sload per iteration` Saves ~200 Gas ( 194 exactly ie. 97\*2)

```solidity
File : team/airdrop/ERC721Airdrop.sol

59: for (uint256 i; i < tokenIds.length; ++i) {
60:            IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);
61:      }

```

[ERC721Airdrop.sol#L59-L61](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59-L61)

**Recommended Mitigation Steps:**

```diff
File : team/airdrop/ERC721Airdrop.sol

+    address _token = token;
+    address _vault = vault;
59: for (uint256 i; i < tokenIds.length; ++i) {
-60:            IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);
+           IERC721(_token).safeTransferFrom(_vault, user, tokenIds[i]);
61:      }

```

## [G-06] State variable can be packed into fewer storage slot by re-arranging their order (**Gas Saved: ~2000 Gas**)

If variables occupying the same slot are both written the same function or by the constructor, avoids a separate Gsset (20000 gas). Reads of the variables can also be cheaper

### `address vault `and `uint64 withdrawalWindow` can packed in a single slot by `withdrawalWindow` just below `vault` and can be packed together `saves: ~2000 Gas, 1 Slot`

```solidity
File : team/airdrop/ERC20Airdrop2.sol

19:    address public vault;
...
27:    /// @notice Length of the withdrawal window.
28:    uint64 public withdrawalWindow;

```

[ERC20Airdrop2.sol#L19-L28](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L19-L28)

**Recommended Mitigation Steps:**

```diff
File : team/airdrop/ERC20Airdrop2.sol

19:    address public vault;
+    uint64 public withdrawalWindow;
...
27:    /// @notice Length of the withdrawal window.
-28:    uint64 public withdrawalWindow;

```

## [G-07] Refactor `loop`in `SgxVerifier::_addInstances` function to Update `storage` variable once outside of the loop instead of updating it every time in loop it saves 1 SSTORE, 4 SLOAD per iteration(**Saves ~2500 Gas per iteration**)

Since `nextInstanceId` is updated every time inside loop and it's updated value is used in next iteration very time. So to achieve this functionality first cache nextInstanceId into local var. before loop then we can use a local variable to update every time in loop and use updated value in next iteration. Finally by this locally updated value `_nextInstanceId`, storage var. `nextInstanceId` can be updated to a final value.

### Saves 1 SSTORE, 4 SLOAD per iteration(**Saves ~2500 Gas per iteration**).

```solidity
File : verifiers/SgxVerifier.sol

210: for (uint256 i; i < _instances.length; ++i) {
211:        if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();
212:
213:       addressRegistered[_instances[i]] = true;
214:
215:        if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();
216:
217:         instances[nextInstanceId] = Instance(_instances[i], validSince);
218:         ids[i] = nextInstanceId;
219:
220:          emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);
221:
222:            nextInstanceId++;
223:        }
```

[SgxVerifier.sol#L210-L223](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210-L223)

**Recommended Mitigation Steps:**

```diff
File : verifiers/SgxVerifier.sol

+     uint256 _nextInstanceId = nextInstanceId;
210: for (uint256 i; i < _instances.length; ++i) {
211:        if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();
212:
213:       addressRegistered[_instances[i]] = true;
214:
215:        if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();
216:
-217:         instances[nextInstanceId] = Instance(_instances[i], validSince);
-218:         ids[i] = nextInstanceId;
-219:
-220:          emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);
-221:
-222:            nextInstanceId++;
+         instances[_nextInstanceId] = Instance(_instances[i], validSince);
+          ids[i] = _nextInstanceId;
+        emit InstanceAdded(_nextInstanceId, _instances[i], address(0), validSince);
+       _nextInstanceId++;
223:        }
+       nextInstanceId = _nextInstanceId;//@audit final update 1 time into storage
```

## [G-08] Cache state variable inside loop instead of reading same variable multiple times when state variable value depends on loop iteration (**Saves 3 SLOAD(~291 Gas) Per iteration**)

Since value depends on iteration number i. So It can't be cached outside loop but it can be cached inside loop when same storage var. accessed multiple times inside loop in each iteration.

```solidity
File : verifiers/SgxVerifier.sol

210: for (uint256 i; i < _instances.length; ++i) {
211:        if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();
212:
213:       addressRegistered[_instances[i]] = true;
214:
215:        if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();
216:
217:         instances[nextInstanceId] = Instance(_instances[i], validSince);
218:         ids[i] = nextInstanceId;
219:
220:          emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);
221:
222:            nextInstanceId++;
223:        }
```

[SgxVerifier.sol#L210-L223](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210-L223)

**Recommended Mitigation Steps:**

```diff
File : verifiers/SgxVerifier.sol

210: for (uint256 i; i < _instances.length; ++i) {
211:        if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();
212:
213:       addressRegistered[_instances[i]] = true;
214:
215:        if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();
+          uint256 _nextInstanceId = nextInstanceId;
216:
-217:         instances[nextInstanceId] = Instance(_instances[i], validSince);
-218:         ids[i] = nextInstanceId;
-219:
-220:          emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);
221:
-222:            nextInstanceId++;
+       instances[_nextInstanceId] = Instance(_instances[i], validSince);
+        ids[i] = _nextInstanceId;
+
+       emit InstanceAdded(_nextInstanceId, _instances[i], address(0), validSince);
+
+       nextInstanceId = _nextInstanceId + 1;

223:        }
```

## [G-09] Refactor functions to `revert` early before loop if check reverting failing. Can save loop run half of the times. (**Gas Saved ~120 Gas Per iteration**) Half of the times

Place the if statement before loop to revert early before for loop.

### Refactor `ERC721Vault::sendToken` function to revert early by placing if statement before loop

```solidity
File : tokenvault/ERC721Vault.sol

26:    function sendToken(BridgeTransferOp memory _op)
27:        external
28:        payable
29:        nonReentrant
30:        whenNotPaused
31:        withValidOperation(_op)
32:        returns (IBridge.Message memory message_)
33:    {
34:    for (uint256 i; i < _op.tokenIds.length; ++i) {
35:            if (_op.amounts[i] != 0) revert VAULT_INVALID_AMOUNT();
36:        }
37:
38:        if (!_op.token.supportsInterface(ERC721_INTERFACE_ID)) {
39:            revert VAULT_INTERFACE_NOT_SUPPORTED();
40:        }
```

[ERC721Vault.sol#L26-L40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L26-L40)

**Recommended Mitigation Steps:**

```diff
File : tokenvault/ERC721Vault.sol

26:    function sendToken(BridgeTransferOp memory _op)
27:        external
28:        payable
29:        nonReentrant
30:        whenNotPaused
31:        withValidOperation(_op)
32:        returns (IBridge.Message memory message_)
33:    {
+      if (!_op.token.supportsInterface(ERC721_INTERFACE_ID)) {
+        revert VAULT_INTERFACE_NOT_SUPPORTED();
+      }
34:    for (uint256 i; i < _op.tokenIds.length; ++i) {
35:            if (_op.amounts[i] != 0) revert VAULT_INVALID_AMOUNT();
36:        }
37:
-38:        if (!_op.token.supportsInterface(ERC721_INTERFACE_ID)) {
-39:            revert VAULT_INTERFACE_NOT_SUPPORTED();
-40:        }
```

### Refactor `ERC1155Vault::sendToken` function to revert early by placing last if statement before loop

```solidity
File : tokenvault/ERC1155Vault.sol

39:  function sendToken(BridgeTransferOp memory _op)
...
47:   for (uint256 i; i < _op.amounts.length; ++i) {
48:      if (_op.amounts[i] == 0) revert VAULT_INVALID_AMOUNT();
49:    }
50:      // Check token interface support
51:    if (!_op.token.supportsInterface(ERC1155_INTERFACE_ID)) {
52:         revert VAULT_INTERFACE_NOT_SUPPORTED();
53:     }

```

[ERC1155Vault.sol#L39-L53](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L39-L53)

**Recommended Mitigation Steps:**

```diff
File : tokenvault/ERC1155Vault.sol

39:  function sendToken(BridgeTransferOp memory _op)
...
+    if (!_op.token.supportsInterface(ERC1155_INTERFACE_ID)) {
+         revert VAULT_INTERFACE_NOT_SUPPORTED();
+     }
47:   for (uint256 i; i < _op.amounts.length; ++i) {
48:      if (_op.amounts[i] == 0) revert VAULT_INVALID_AMOUNT();
49:    }
50:      // Check token interface support
-51:    if (!_op.token.supportsInterface(ERC1155_INTERFACE_ID)) {
-52:         revert VAULT_INTERFACE_NOT_SUPPORTED();
-53:     }

```

## [G-10] Refactor `changeBridgedToken` function to save `owner()` function call (**Gas Saved ~200 Gas**)

**Description:**
The `changeBridgedToken` function in the `ERC20Vault` contract has been refactored to optimize gas usage by eliminating redundant calls to the `owner()` function.

**Problem:**
The original implementation made multiple calls to the `owner()` function within the function body, resulting in unnecessary gas consumption. Each call to `owner()` incurred gas costs for accessing storage and executing the function.

**Solution:**
To address this issue and reduce gas consumption, the code has been refactored to store the owner's address in a local variable `_owner`. This approach eliminates redundant calls to the `owner()` function again and optimizes gas usage by accessing the owner's address from the local variable instead. Remove onlyOwner modifier and write it's check directly inside function changeBridgedToken.

```solidity
File : tokenvault/ERC20Vault.sol

148:    function changeBridgedToken(
149:        CanonicalERC20 calldata _ctoken,
150:        address _btokenNew
151:    )
152:        external
153:        nonReentrant
154:        whenNotPaused
155:        onlyOwner
156:        returns (address btokenOld_)
157:    {
158:        if (_btokenNew == address(0) || bridgedToCanonical[_btokenNew].addr != address(0)) {
159:            revert VAULT_INVALID_NEW_BTOKEN();
160:        }
161:
162:        if (btokenBlacklist[_btokenNew]) revert VAULT_BTOKEN_BLACKLISTED();
163:
164:        if (IBridgedERC20(_btokenNew).owner() != owner()) {
165:            revert VAULT_NOT_SAME_OWNER();
166:        }

```

[ERC20Vault.sol#L148-L166](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L148-L166)

**Recommended Mitigation Steps:**

1. Local Variable Declaration: Added a local variable `_owner` to store the owner's address retrieved from the `owner()` function.
2. Gas Optimization: Replaced multiple calls to the `owner()` function with references to the local variable `_owner` throughout the function body.
3. Require Statement: Added a require statement to ensure that the caller of the function is the contract owner before proceeding with the execution.

```diff
File : tokenvault/ERC20Vault.sol

148:    function changeBridgedToken(
149:        CanonicalERC20 calldata _ctoken,
150:        address _btokenNew
151:    )
152:        external
153:        nonReentrant
154:        whenNotPaused
-155:        onlyOwner
156:        returns (address btokenOld_)
157:    {
+        address _owner = owner();
+        require(msg.sender == _owner,"msg.sender is not owner");
158:        if (_btokenNew == address(0) || bridgedToCanonical[_btokenNew].addr != address(0)) {
159:            revert VAULT_INVALID_NEW_BTOKEN();
160:        }
161:
162:        if (btokenBlacklist[_btokenNew]) revert VAULT_BTOKEN_BLACKLISTED();
163:
-164:        if (IBridgedERC20(_btokenNew).owner() != owner()) {
+            if (IBridgedERC20(_btokenNew)._owner != _owner) {//@audit reducing owner() function call
165:            revert VAULT_NOT_SAME_OWNER();
166:        }

```

## [G-11] Write if check before function call if condition is independent from function call. Can save function call half of the times when `if` condition fails.(**Gas Saved ~3000 Gas Half of the times**)

### Refactor `Bridge::sendMessage` function to `revert` early with low gas consuming statement **Can avoid 1 function call which includes inside multiple calls and 1 external call also and some state reads**

Refactor this function to revert early so write last two if statements above `isDestChainEnabled` function call to avoid 1 function call when any of the if condition fails. Since these `if` conditions are not depends on function call so should be written before this function call which includes inside multiple calls and 1 external call also and some storage reads. Avg Saves ~3000 Gas Half of the times.

```solidity
File : bridge/Bridge.sol

115: function sendMessage(Message calldata _message)
...
122:    {
123:        // Ensure the message owner is not null.
124:        if (_message.srcOwner == address(0) || _message.destOwner == address(0)) {
125:            revert B_INVALID_USER();
126:        }
127
128:        // Check if the destination chain is enabled.
129:        (bool destChainEnabled,) = isDestChainEnabled(_message.destChainId);
130:
131:        // Verify destination chain and to address.
132:        if (!destChainEnabled) revert B_INVALID_CHAINID();
133:        if (_message.destChainId == block.chainid) {
134:            revert B_INVALID_CHAINID();
135:        }
136:
137:        // Ensure the sent value matches the expected amount.
138:        uint256 expectedAmount = _message.value + _message.fee;
139:        if (expectedAmount != msg.value) revert B_INVALID_VALUE();

```

[Bridge.sol#L115-L139](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L115-L139)

**Recommended Mitigation Steps:**

```diff
File : bridge/Bridge.sol

115: function sendMessage(Message calldata _message)
...
122:    {
123:        // Ensure the message owner is not null.
124:        if (_message.srcOwner == address(0) || _message.destOwner == address(0)) {
125:            revert B_INVALID_USER();
126:        }
+         if (_message.destChainId == block.chainid) {
+           revert B_INVALID_CHAINID();
+         }
+
+        // Ensure the sent value matches the expected amount.
+        uint256 expectedAmount = _message.value + _message.fee;
+        if (expectedAmount != msg.value) revert B_INVALID_VALUE();
127
128:        // Check if the destination chain is enabled.
129:        (bool destChainEnabled,) = isDestChainEnabled(_message.destChainId);
130:
131:        // Verify destination chain and to address.
132:        if (!destChainEnabled) revert B_INVALID_CHAINID();
-133:        if (_message.destChainId == block.chainid) {
-134:            revert B_INVALID_CHAINID();
-135:        }
136:
-137:        // Ensure the sent value matches the expected amount.
-138:        uint256 expectedAmount = _message.value + _message.fee;
-139:        if (expectedAmount != msg.value) revert B_INVALID_VALUE();

```

### Refactor `ERC721Vault::onMessageInvocation` function to revert early before function call **avoid 1 function call**

```solidity
File : tokenvault/ERC721Vault.sol

86:     // `onlyFromBridge` checked in checkProcessMessageContext
87:    IBridge.Context memory ctx = checkProcessMessageContext();
88:
89:     // Don't allow sending to disallowed addresses.
90:    // Don't send the tokens back to `from` because `from` is on the source chain.
91:    if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

```

[ERC721Vault.sol#L86-L91](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L86-L91)

**Recommended Mitigation Steps:**

```diff
File : tokenvault/ERC721Vault.sol

+      if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();
86:     // `onlyFromBridge` checked in checkProcessMessageContext
87:    IBridge.Context memory ctx = checkProcessMessageContext();
88:
89:     // Don't allow sending to disallowed addresses.
90:    // Don't send the tokens back to `from` because `from` is on the source chain.
-91:    if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();

```

### Refactor `ERC1155Vault::onMessageInvocation` function to revert early before `checkProcessMessageContext()` function call **avoid 1 function call**

```solidity
File : tokenvault/ERC1155Vault.sol

103:   // `onlyFromBridge` checked in checkProcessMessageContext
104:  IBridge.Context memory ctx = checkProcessMessageContext();
105:
106:    // Don't allow sending to disallowed addresses.
107:    // Don't send the tokens back to `from` because `from` is on the source chain.
108:   if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();
```

[ERC1155Vault.sol#L103-L108](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L103-L108)

**Recommended Mitigation Steps:**

```diff
File : tokenvault/ERC1155Vault.sol

+   if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();
103:   // `onlyFromBridge` checked in checkProcessMessageContext
104:  IBridge.Context memory ctx = checkProcessMessageContext();
105:
106:    // Don't allow sending to disallowed addresses.
107:    // Don't send the tokens back to `from` because `from` is on the source chain.
-108:   if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();
```

## [G-12] Unnecessary `nonReentrant` modifier check in `functions` (**Gas Saved ~2397 Gas**)

The `nonReentrant` modifier is applied to a function where there are no external or internal function calls only a single state change occurs. So no possibility of reentrancy, as there are no subsequent calls that could interrupt or alter the intended behavior of the function. So it is 100% safe to remove nonReentrant modifier to save gas from those functions which just have simple state change no other function call external ,internal any type.

### Remove `nonReentrant` modifier from `banAddress` function **(Saves: `~19771 Gas` on deployment and `~2396 Gas` on function call each time)**

Here `nonReentrant` modifier is applied to just simple check and state change where there is no possibility of re-entry so removing it is safe. It starts after `onlyFromOwnerOrNamed` so it doesn't apply to this also.

```solidity
File : bridge/Bridge.sol

101:  function banAddress(
102:    address _addr,
103:    bool _ban
104:  )
105:     external
106:     onlyFromOwnerOrNamed("bridge_watchdog")
107:     nonReentrant
108:  {
109:    if (addressBanned[_addr] == _ban) revert B_INVALID_STATUS();
110:    addressBanned[_addr] = _ban;
111:     emit AddressBanned(_addr, _ban);
112:    }
```

[Bridge.sol#L101-L112](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L101-L112)

**Recommended Mitigation Steps:**

```diff
File : bridge/Bridge.sol

101:  function banAddress(
102:    address _addr,
103:    bool _ban
104:  )
105:     external
106:     onlyFromOwnerOrNamed("bridge_watchdog")
-107:     nonReentrant
108:  {
109:    if (addressBanned[_addr] == _ban) revert B_INVALID_STATUS();
110:    addressBanned[_addr] = _ban;
111:     emit AddressBanned(_addr, _ban);
112:    }
```

## [G-13] Multiple accesses of the same mapping/array key/index should be cached inside loop (**Saves 1 SLOAD(~130 Gas) Per iteration**)

The instances below point to the second+ access of a value inside a mapping/array key/index, within a function. Caching a mapping's value in a local storage or calldata variable when the value is accessed multiple times, saves ~42 gas per access due to not having to recalculate the key's keccak256 hash (Gkeccak256 - 30 gas) and that calculation's associated stack operations. Caching an array's struct avoids recalculating the array offsets into memory/calldata

### Cache `instances[idx].addr` mapping to save 1 SLOAD and some keccak ops Per iteration

```solidity
File : verifiers/SgxVerifier.sol

104: for (uint256 i; i < _ids.length; ++i) {
105:       uint256 idx = _ids[i];
106:
107:     if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();
108:
109:        emit InstanceDeleted(idx, instances[idx].addr);
110:
111:        delete instances[idx];
112:     }

```

[SgxVerifier.sol#L104-L112](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L104-L112)

**Recommended Mitigation Steps:**

```diff
File : verifiers/SgxVerifier.sol

104: for (uint256 i; i < _ids.length; ++i) {
105:       uint256 idx = _ids[i];
106:
+         Instance _instances = instances[idx].addr;
-107:     if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();
+       if (_instances == address(0)) revert SGX_INVALID_INSTANCE();
108:
-109:        emit InstanceDeleted(idx, instances[idx].addr);
+            emit InstanceDeleted(idx, _instances);
110:
111:        delete instances[idx];
112:     }

```

## [G-14] Change the order of `modifier` checks in `functions` from low to high gas consumer to fail early with less consuming one, it can save gas Half of the times when low gas consuming fails(**Total Gas Saved ~11000 Gas**)

**Total Gas Saved: ~11000 Half of the times**
**Gas Saved Per Instance: ~2200 Gas**

### Change the order of `nonReentrant`, `whenNotPaused` and `sameChain` modifier checks from low to high gas consumer one

The function incorporates three modifiers `nonReentrant`, `whenNotPaused` and `sameChain`. An optimization suggestion is made to reorder these modifiers for potential gas savings.
Place `sameChain` modifier at first and `whenNotPaused` at 2nd and `nonReentrant` at 3rd. Since `sameChain` modifier takes less gas (almost ~100 to 150) compared to `nonReentrant`(~2396) and `whenNotPaused`(~2200) modifiers. Since same chain doesn't have any function call or state read/write.
Doesn't pose any risk of reentrancy so can be outside from nonReentrant.

```solidity
File : bridge/Bridge.sol

64: modifier sameChain(uint64 _chainId) {
65:        if (_chainId != block.chainid) revert B_INVALID_CHAINID();
66:        _;
67:    }

```

[bridge/Bridge.sol#L64-L67](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L64-L67)

#### So when failing then fail with less gas consuming one first. It can save ~2200 GAS Half of the times.

### 3 Instances

#### Instance 1

```solidity
File : bridge/Bridge.sol

155:    function recallMessage(
156:        Message calldata _message,
157:        bytes calldata _proof
158:    )
159:        external
160:        nonReentrant
161:        whenNotPaused
162:        sameChain(_message.srcChainId)
163:    {

```

[bridge/Bridge.sol#L115-L122](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L115-L122)

**Recommended Mitigation Steps:**

```diff
File : bridge/Bridge.sol

155:    function recallMessage(
156:        Message calldata _message,
157:        bytes calldata _proof
158:    )
159:        external
-160:        nonReentrant
-161:        whenNotPaused
-162:        sameChain(_message.srcChainId)
+          sameChain(_message.srcChainId)
+          whenNotPaused
+          nonReentrant
163:    {

```

#### Instance 2

```solidity
File : bridge/Bridge.sol

217:    function processMessage(
218:        Message calldata _message,
219:        bytes calldata _proof
220:    )
221:        external
222:        nonReentrant
223:        whenNotPaused
224:        sameChain(_message.destChainId)
225:    {

```

[Bridge.sol#L217-L225](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L217-L225)

**Recommended Mitigation Steps:**

```diff
File : bridge/Bridge.sol

217:    function processMessage(
218:        Message calldata _message,
219:        bytes calldata _proof
220:    )
221:        external
-222:        nonReentrant
-223:        whenNotPaused
-224:        sameChain(_message.destChainId)
+          sameChain(_message.destChainId)
+          whenNotPaused
+          nonReentrant
225:    {

```

#### Instance 3

```solidity
File : bridge/Bridge.sol

310: function retryMessage(
311:        Message calldata _message,
312:        bool _isLastAttempt
313:    )
314:        external
315:        nonReentrant
316:        whenNotPaused
317:        sameChain(_message.destChainId)
318:    {

```

[Bridge.sol#L310-L318](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L310-L318)

**Recommended Mitigation Steps:**

```diff
File : bridge/Bridge.sol

310: function retryMessage(
311:        Message calldata _message,
312:        bool _isLastAttempt
313:    )
314:        external
-315:        nonReentrant
-316:        whenNotPaused
-317:        sameChain(_message.destChainId)
+          sameChain(_message.destChainId)
+          whenNotPaused
+          nonReentrant
318:    {

```

### Change the order of `nonReentrant`, `whenNotPaused` and [`withValidOperation`](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseNFTVault.sol#L140-L150) modifier checks from low to high gas consumer one

The function incorporates three modifiers `nonReentrant`, `whenNotPaused` and `withValidOperation`. An optimization suggestion is made to reorder these modifiers for potential gas savings.
Place `withValidOperation` modifier at first and `whenNotPaused` at 2nd and `nonReentrant` at 3rd. Since `withValidOperation` modifier takes less gas compared to `nonReentrant` and `whenNotPaused` modifiers.
Similarly like `sameChain` , withValidOperation also doesn't have any state read write just simple checks so it also takes 150 - 200 Gas Avg. So should be written first in order. Doesn't pose any risk of reentrancy so can be outside from nonReentrant

### 2 Instances

#### Instance 1

```solidity
File : tokenvault/ERC721Vault.sol

26:    function sendToken(BridgeTransferOp memory _op)
27:        external
28:        payable
29:        nonReentrant
30:        whenNotPaused
31:        withValidOperation(_op)
32:        returns (IBridge.Message memory message_)
33:    {
```

[ERC721Vault.sol#L26-L33](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L26-L33)

**Recommended Mitigation Steps:**

```diff
File : tokenvault/ERC721Vault.sol

26:    function sendToken(BridgeTransferOp memory _op)
27:        external
28:        payable
-29:        nonReentrant
-30:        whenNotPaused
-31:        withValidOperation(_op)
+         withValidOperation(_op)
+        whenNotPaused
+        nonReentrant
32:        returns (IBridge.Message memory message_)
33:    {
```

#### Instance 2

```solidity
File : tokenvault/ERC1155Vault.sol

39:    function sendToken(BridgeTransferOp memory _op)
40:        external
41:        payable
42:        nonReentrant
43:        whenNotPaused
44:        withValidOperation(_op)
45:        returns (IBridge.Message memory message_)
46:    {
```

[ERC1155Vault.sol#L39-L46](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L39-L46)

**Recommended Mitigation Steps:**

```diff
File : tokenvault/ERC1155Vault.sol

39:    function sendToken(BridgeTransferOp memory _op)
40:        external
41:        payable
-42:        nonReentrant
-43:        whenNotPaused
-44:        withValidOperation(_op)
+         withValidOperation(_op)
+        whenNotPaused
+        nonReentrant
45:        returns (IBridge.Message memory message_)
46:    {
```

## [G-15] State variables should be cached in stack variables rather than re-reading them from storage(**Total Gas Saved ~291 Gas**)

The instances below point to the second+ access of a state variable within a function. Caching of a state variable replaces each Gwarmaccess (100 gas) with a much cheaper stack read. Other less obvious fixes/optimizations include having local memory caches of state variable structs, or having local caches of state variable contracts/addresses.

### `migratingAddress` can be cached in `mint` function to save 1 SLOAD(~100 Gas) _97_ technically

```solidity
File : tokenvault/BridgedERC20Base.sol

61:   if (msg.sender == migratingAddress) {
62:       // Inbound migration
63:      emit MigratedTo(migratingAddress, _account, _amount);
```

[BridgedERC20Base.sol#L61-L63](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L61-L63)

**Recommended Mitigation Steps:**

```diff
File : tokenvault/BridgedERC20Base.sol

+    address _migratingAddress = migratingAddress;
-61:   if (msg.sender == migratingAddress) {
-62:       // Inbound migration
-63:      emit MigratedTo(migratingAddress, _account, _amount);
+     if (msg.sender == _migratingAddress) {
+        // Inbound migration
+        emit MigratedTo(_migratingAddress, _account, _amount);
```

### `migratingAddress` can be cached in `burn` function to save 1 SLOAD(~100 Gas)

```solidity
File : tokenvault/BridgedERC20Base.sol

80:  emit MigratedTo(migratingAddress, _account, _amount);
81:   // Ask the new bridged token to mint token for the user.
82:  IBridgedERC20(migratingAddress).mint(_account, _amount);

```

[BridgedERC20Base.sol#L80-L82](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L80-L82)

**Recommended Mitigation Steps:**

```diff
File : tokenvault/BridgedERC20Base.sol

+    address _migratingAddress = migratingAddress;
-80:  emit MigratedTo(migratingAddress, _account, _amount);
+    emit MigratedTo(_migratingAddress, _account, _amount);
81:   // Ask the new bridged token to mint token for the user.
-82:  IBridgedERC20(migratingAddress).mint(_account, _amount);
+   IBridgedERC20(_migratingAddress).mint(_account, _amount);

```

### `addressManager` can be cached in `_resolve` function saves 1 SLOAD(~100 Gas)

```solidity
File : common/AddressResolver.sol

81: if (addressManager == address(0)) revert RESOLVER_INVALID_MANAGER();
82:
83:     addr_ = payable(IAddressManager(addressManager).getAddress(_chainId, _name));

```

[AddressResolver.sol#L81-L83](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L81-L83)

**Recommended Mitigation Steps:**

```diff
File : common/AddressResolver.sol

+   address _addressManager = addressManager;
-81: if (addressManager == address(0)) revert RESOLVER_INVALID_MANAGER();
-82:
-83:     addr_ = payable(IAddressManager(addressManager).getAddress(_chainId, _name));
+  if (_addressManager == address(0)) revert RESOLVER_INVALID_MANAGER();
+
+  addr_ = payable(IAddressManager(_addressManager).getAddress(_chainId, _name));

```

## [G-16] Do not create memory variable when used only once use expressions directly which are cached in memory variables.

By directly passing the expression/function call as an argument, we avoid the need for the intermediate data memory variable if it is used only once to pass as param. This results in cleaner and more efficient code, as it eliminates unnecessary variable declarations, MLOADs and MSOTREs associated with it and makes the intent of the code clearer.

### 2 Instances

#### Instance 1

By directly passing the expression abi.encodeCall(...) as an argument to the constructor of ERC1967Proxy, we avoid the need for the intermediate data memory variable.

```solidity
File : tokenvault/ERC1155Vault.sol

303:    function _deployBridgedToken(CanonicalNFT memory _ctoken) private returns (address btoken_) {
304:        bytes memory data = abi.encodeCall(
305:            BridgedERC1155.init,
306:            (owner(), addressManager, _ctoken.addr, _ctoken.chainId, _ctoken.symbol, _ctoken.name)
307:        );
308:
309:        btoken_ = address(new ERC1967Proxy(resolve("bridged_erc1155", false), data));
```

[ERC1155Vault.sol#L303-L309](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L303-L309)

**Recommended Mitigation Steps:**

```diff
File : tokenvault/ERC1155Vault.sol

303:    function _deployBridgedToken(CanonicalNFT memory _ctoken) private returns (address btoken_) {
-304:        bytes memory data = abi.encodeCall(
-305:            BridgedERC1155.init,
-306:            (owner(), addressManager, _ctoken.addr, _ctoken.chainId, _ctoken.symbol, _ctoken.name)
-307:        );
-308:
-309:        btoken_ = address(new ERC1967Proxy(resolve("bridged_erc1155", false), data));
+    btoken_ = address(new ERC1967Proxy(
+        resolve("bridged_erc1155", false),
+        abi.encodeCall(
+            BridgedERC1155.init,
+            (
+                owner(),
+                addressManager,
+                _ctoken.addr,
+                _ctoken.chainId,
+                _ctoken.symbol,
+                _ctoken.name
+            )
+        )
+    ));
+  }
```

#### Instance 2

Use `Bytes.slice(_proof.data, 24)` directly instead of caching into signature. since `signature` is used only once. It is completely safe and clean.

```solidity
File : verifiers/SgxVerifier.sol

156:   bytes memory signature = Bytes.slice(_proof.data, 24);
157:
158:   address oldInstance =
159:      ECDSA.recover(getSignedHash(_tran, newInstance, _ctx.prover, _ctx.metaHash), signature);

```

[SgxVerifier.sol#L156-L159](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L156-L159)

**Recommended Mitigation Steps:**

```diff
File : verifiers/SgxVerifier.sol

-156:   bytes memory signature = Bytes.slice(_proof.data, 24);
157:
-158:   address oldInstance =
-159:      ECDSA.recover(getSignedHash(_tran, newInstance, _ctx.prover, _ctx.metaHash), signature);
+  address oldInstance =
+     ECDSA.recover(getSignedHash(_tran, newInstance, _ctx.prover, _ctx.metaHash), Bytes.slice(_proof.data, 24));

```

## [G-17] Refactor loop in `setGuardians` function to **avoid 1 SLOAD per iteration**

**Note It is different from caching array length in loop since it is increasing and iteration loop no. doesn't depends on it**
Cache guardians.length outside of the loop in a local var. `gLength` then use this local var. inside loop while updating it on each iteration since guardians array length also increasing on each iteration and this increased length is used to assign in guardianIds[guardian]. SO we use updated `gLength` on each iteration to avoid reading guardians length.

```solidity
File : L1/provers/Guardians.sol

80: for (uint256 i = 0; i < _newGuardians.length; ++i) {
            address guardian = _newGuardians[i];
            if (guardian == address(0)) revert INVALID_GUARDIAN();
            // This makes sure there are not duplicate addresses
            if (guardianIds[guardian] != 0) revert INVALID_GUARDIAN_SET();

            // Save and index the guardian
            guardians.push(guardian);
            guardianIds[guardian] = guardians.length;
89:        }

```

[Guardians.sol#L80-L89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L80-L89)

**Recommended Mitigation Steps:**

```diff
File : L1/provers/Guardians.sol

+   uint256 gLength = guardians.length;
80: for (uint256 i = 0; i < _newGuardians.length; ++i) {
            address guardian = _newGuardians[i];
            if (guardian == address(0)) revert INVALID_GUARDIAN();
            // This makes sure there are not duplicate addresses
            if (guardianIds[guardian] != 0) revert INVALID_GUARDIAN_SET();

            // Save and index the guardian
            guardians.push(guardian);
-            guardianIds[guardian] = guardians.length;
+            guardianIds[guardian] = ++gLength;
89:        }

```

## [G-18] Multiple address/ID mappings can be combined into a single mapping of an address/ID to a struct

Saves a storage slot for the mapping. Depending on the circumstances and sizes of types, can avoid a Gsset (20000 gas) per mapping combined. Reads and subsequent writes can also be cheaper when a function requires both values and they both fit in the same storage slot. Finally, if both fields are accessed in the same function, can save ~42 gas per access due to not having to recalculate the key's keccak256 hash (Gkeccak256 - 30 gas) and that calculation's associated stack operations

By combining the mappings into a single mapping of address to TokenData, you can save storage slots and potentially reduce gas costs associated with accessing and updating the mappings. Additionally, accessing both fields in the same function can save gas per access by avoiding the recalculation of the key's keccak256 hash.

```solidity
File : tokenvault/ERC20Vault.sol

45:    mapping(address btoken => CanonicalERC20 canonical) public bridgedToCanonical;
...
51:    /// @notice Mappings from bridged tokens to their blacklist status.
52:    mapping(address btoken => bool blacklisted) public btokenBlacklist;

```

[ERC20Vault.sol#L45-L52](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L45-L52)

**Recommended Mitigation Steps:**

```diff
File : tokenvault/ERC20Vault.sol

+// Define a struct to hold CanonicalERC20 and blacklist status
+ struct BTokenData {
+    CanonicalERC20 canonical;
+    bool blacklisted;
+ }
+
+ // Combine multiple mappings into a single mapping of address to BTokenData
+ mapping(address => BTokenData) public tokenDataMap;

-45:    mapping(address btoken => CanonicalERC20 canonical) public bridgedToCanonical;
...
-51:    /// @notice Mappings from bridged tokens to their blacklist status.
-52:    mapping(address btoken => bool blacklisted) public btokenBlacklist;

```

## [G-19] Use Short-Circuiting around _&&_ to avoid 1 function call to save gas.(**Total Saves ~120 Gas**)

### Use short-circuiting in `onlyOwnerOrSnapshooter` modifier to save function call

To save gas, rearrange the conditions in the if statement to check `msg.sender` against `snapshooter` first, as this requires only a single `storage` read operation. Checking `msg.sender` against `owner()` involves an `function` call and an additional `storage` read operation, which can be avoided half of the times if `snapshooter` is checked first.

```solidity
File : tokenvault/BridgedERC20.sol

37: modifier onlyOwnerOrSnapshooter() {
38:  if (msg.sender != owner() && msg.sender != snapshooter) {
39:      revert BTOKEN_UNAUTHORIZED();
40:    }

```

[BridgedERC20.sol#L37-L40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L37-L40)

**Recommended Mitigation Steps:**

```diff
File : tokenvault/BridgedERC20.sol

37: modifier onlyOwnerOrSnapshooter() {
-38:  if (msg.sender != owner() && msg.sender != snapshooter) {
+     if (msg.sender != snapshooter && msg.sender != owner()) {
39:      revert BTOKEN_UNAUTHORIZED();
40:    }

```

### Use short-circuiting method in `_isMigratingOut` function to save gas

By placing the condition `!migratingInbound` first, if it evaluates to false, the `&&` operator `short-circuits` and does not evaluate the second condition, potentially saving gas. Additionally, negating `migratingInbound` consumes less gas compared to the comparison operation `migratingAddress != address(0)`. This optimization aims to reduce gas consumption in the overall evaluation of the expression.

```solidity
File : tokenvault/BridgedERC20Base.sol

101: function _isMigratingOut() internal view returns (bool) {
102:    return migratingAddress != address(0) && !migratingInbound;
103:    }

```

[BridgedERC20Base.sol#L101-L103](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L101-L103)

**Recommended Mitigation Steps:**

```diff
File : tokenvault/BridgedERC20Base.sol

101: function _isMigratingOut() internal view returns (bool) {
-102:    return migratingAddress != address(0) && !migratingInbound;
+        return !migratingInbound && migratingAddress != address(0);
103:    }

```

## [G-20] Change the order of nested if statement to write less gas consuming first

The first statement within the function `retryMessage` checks two conditions, while the second statement only checks one condition. To optimize gas usage and potentially reduce gas costs, it's beneficial to prioritize the condition that checks two statements by placing last second statement to first.

```solidity
File : bridge/Bridge.sol

310: function retryMessage(
...
321:  if (_message.gasLimit == 0 || _isLastAttempt) {
322:     if (msg.sender != _message.destOwner) revert B_PERMISSION_DENIED();
323:   }

```

[Bridge.sol#L321-L323](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L321-L323)

**Recommended Mitigation Steps:**

```diff
File : bridge/Bridge.sol

310: function retryMessage(
...
-321:  if (_message.gasLimit == 0 || _isLastAttempt) {
-322:     if (msg.sender != _message.destOwner) revert B_PERMISSION_DENIED();
-323:   }
+     if (msg.sender != _message.destOwner) {
+     if (_message.gasLimit == 0 || _isLastAttempt) revert B_PERMISSION_DENIED();
+ }

```

## [G-21] Do not cache function call when it is used only once

No need to cache `resolve(ctx_.srcChainId, name(), false)` into `selfOnSourceChain` stack variable Since it is used only once.
Use `resolve(ctx_.srcChainId, name(), false)` directly.

```solidity
File : tokenvault/BaseVault.sol

54:    address selfOnSourceChain = resolve(ctx_.srcChainId, name(), false);
55:    if (ctx_.from != selfOnSourceChain) revert VAULT_PERMISSION_DENIED();
```

[BaseVault.sol#L54-L55](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BaseVault.sol#L54-L55)

**Recommended Mitigation Steps:**

```diff
File : tokenvault/BaseVault.sol

-54:    address selfOnSourceChain = resolve(ctx_.srcChainId, name(), false);
-55:    if (ctx_.from != selfOnSourceChain) revert VAULT_PERMISSION_DENIED();
+    if (ctx_.from != resolve(ctx_.srcChainId, name(), false)) revert VAULT_PERMISSION_DENIED();
```

#### Instance 2

No need to `resolve("taiko", false)` into stack variable because it is used only once in the function.

```solidity
File : verifiers/SgxVerifier.sol

181: address taikoL1 = resolve("taiko", false);
182:    return keccak256(
183:        abi.encode(
184:          "VERIFY_PROOF",
185:           ITaikoL1(taikoL1).getConfig().chainId,
```

[SgxVerifier.sol#L181-L185](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L181-L185)

**Recommended Mitigation Steps:**

```diff
File : verifiers/SgxVerifier.sol

-181: address taikoL1 = resolve("taiko", false);
182:    return keccak256(
183:        abi.encode(
184:          "VERIFY_PROOF",
-185:           ITaikoL1(taikoL1).getConfig().chainId,
+             ITaikoL1(resolve("taiko", false)).getConfig().chainId,
```

## [G-22] Use custom error instead of `assert` Statement in `_invokeMessageCall` Function

While assert statements are useful for detecting unexpected conditions during development and testing. require or custom error is more convenient to use here instead of assert and custom error takes lesser gas also.

```solidity
File : bridge/Bridge.sol

486:   assert(_message.from != address(this));
```

[Bridge.sol#L486](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L486)

**Recommended Mitigation Steps:**

```diff
File : bridge/Bridge.sol
+   error INVALID_SENDER();
   ...

-486:   assert(_message.from != address(this));
+     if(_message.from == address(this)) revert INVALID_SENDER();
```

## [G-23] Avoid zero value transfers when transferring/minting ERC20 tokens

In Solidity, performing unnecessary operations can consume more gas than needed, leading to cost inefficiencies. For instance, if a transfer function doesn't have a zero amount check and someone calls it with a zero amount, unnecessary gas will be consumed in executing the function, even though the state of the contract remains the same. By implementing a zero amount check, such unnecessary function calls can be avoided, thereby saving gas and making the contract more efficient. Amounts should be checked for 0 before calling a transfer Checking non-zero transfer values can avoid an expensive external call and save gas.

### Check amount is non 0 before transferring tokens in `onMessageInvocation` function

```solidity
File : tokenvault/ERC20Vault.sol

270: address token = _transferTokens(ctoken, to, amount);

```

[ERC20Vault.sol#L270](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L270)

**Recommended Mitigation Steps:**

```diff
File : tokenvault/ERC20Vault.sol

+    require(amount > 0, "Amount can not be 0");
270: address token = _transferTokens(ctoken, to, amount);

```

### Check amount for non 0 before `transferring` and `minting` tokens in `_transferTokens` function and they are not checked for 0 yet in which public/external function they are call. Good to check here.

```solidity
File : tokenvault/ERC20Vault.sol

328: if (_ctoken.chainId == block.chainid) {
329:     token_ = _ctoken.addr;
330:     IERC20(token_).safeTransfer(_to, _amount);
331:  } else {
332:    token_ = _getOrDeployBridgedToken(_ctoken);
333:     IBridgedERC20(token_).mint(_to, _amount);
334:        }
```

[ERC20Vault.sol#L328-L334](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L328-L334)

```diff
File : tokenvault/ERC20Vault.sol

+    require(_amount > 0, "Amount can not be 0");
328: if (_ctoken.chainId == block.chainid) {
329:     token_ = _ctoken.addr;
330:     IERC20(token_).safeTransfer(_to, _amount);
331:  } else {
332:    token_ = _getOrDeployBridgedToken(_ctoken);
333:     IBridgedERC20(token_).mint(_to, _amount);
334:        }
```

## [G-24] Cache `address(this)` outside of the `loop` instead of calculating it on every loop iteration(**Saves ~30 Gas per iteration**)

### 2 Instances

#### Cache `address(this)` outside of the loop in `_transferTokens` function

```solidity
File : tokenvault/ERC721Vault.sol

160:  function _transferTokens(
...
170:   for (uint256 i; i < _tokenIds.length; ++i) {
171:       IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);
172:     }

```

[ERC721Vault.sol#L170-L172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L170-L172)

**Recommended Mitigation Steps:**

```diff
File : tokenvault/ERC721Vault.sol

160:  function _transferTokens(
...
+     address addressOfThisContract = address(this);
170:   for (uint256 i; i < _tokenIds.length; ++i) {
-171:       IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);
+         IERC721(token_).safeTransferFrom(addressOfThisContract, _to, _tokenIds[i]);
172:     }

```

#### Cache `address(this)` outside of the loop in `_handleMessage` function

```solidity
File : tokenvault/ERC721Vault.sol

187:   function _handleMessage(
...
210:   for (uint256 i; i < _op.tokenIds.length; ++i) {
211:       t.safeTransferFrom(_user, address(this), _op.tokenIds[i]);
212:    }

```

[ERC721Vault.sol#L210-L212](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L210-L212)

**Recommended Mitigation Steps:**

```diff
File : tokenvault/ERC721Vault.sol

187:   function _handleMessage(
...
+     address addressOfThisContract = address(this);
210:   for (uint256 i; i < _op.tokenIds.length; ++i) {
-211:       t.safeTransferFrom(_user, address(this), _op.tokenIds[i]);
+       t.safeTransferFrom(_user, addressOfThisContract, _op.tokenIds[i]);
212:    }

```

## [G‑25] Do not emit events inside loop (**Gas Saved ~300 Gas**)

Emitting an event inside a loop performs a LOG op N times, where N is the loop length. Consider refactoring the code to emit the event only once at the end of loop. **Gas savings should be multiplied by the average loop length**.

#### Instance 1

```solidity
File : bridge/Bridge.sol

90:    for (uint256 i; i < _msgHashes.length; ++i) {
91:         bytes32 msgHash = _msgHashes[i];
92:         proofReceipt[msgHash].receivedAt = _timestamp;
93:         emit MessageSuspended(msgHash, _suspend);
94:      }
```

[Bridge.sol#L90-L94](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L90-L94)

**Recommended Mitigation Steps:**

```diff
File : bridge/Bridge.sol

90:    for (uint256 i; i < _msgHashes.length; ++i) {
91:         bytes32 msgHash = _msgHashes[i];
92:         proofReceipt[msgHash].receivedAt = _timestamp;
-93:         emit MessageSuspended(msgHash, _suspend);
94:      }
+    emit MessageSuspended(_msgHashes, _suspend);
```

## [G-26] Nesting if-statements is cheaper than using && (**Total Gas Saved ~120 Gas**)

Using a nested if statement instead of logical AND (&&) can provide similar short-circuiting behavior whereas nested if is slightly more efficient.

**Total Gas Saved: ~120 Gas**
**Gas Saved Per Instance: ~30 Gas**

### 4 Instances

#### Instance 1,2

```solidity
File : bridge/Bridge.sol

250:        if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) {
251:            // If msg.sender is not the one that proved the message, then there
252:            // is an extra delay.
253:            unchecked {
254:                invocationDelay += invocationExtraDelay;
255:            }
256:        }
...
...
260:  if (_message.gasLimit == 0 && msg.sender != _message.destOwner) {
261:        revert B_PERMISSION_DENIED();
262:     }

```

[Bridge.sol#L250-L262](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L250-L262)

**Recommended Mitigation Steps:**

```diff
File : bridge/Bridge.sol

-250:        if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) {
+           if (invocationDelay != 0) {
+              if (msg.sender != proofReceipt[msgHash].preferredExecutor) {
251:            // If msg.sender is not the one that proved the message, then there
252:            // is an extra delay.
253:            unchecked {
254:                invocationDelay += invocationExtraDelay;
255:            }
256:        }
...
...
-260:  if (_message.gasLimit == 0 && msg.sender != _message.destOwner) {
+     if (_message.gasLimit == 0) {
+       if (msg.sender != _message.destOwner) {
261:        revert B_PERMISSION_DENIED();
262:     }

```

#### Instance 3

```solidity
File : tokenvault/BridgedERC20.sol

37: modifier onlyOwnerOrSnapshooter() {
38:  if (msg.sender != owner() && msg.sender != snapshooter) {
39:      revert BTOKEN_UNAUTHORIZED();
40:    }

```

[BridgedERC20.sol#L37-L40](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L37-L40)

**Recommended Mitigation Steps:**

```diff
File : tokenvault/BridgedERC20.sol

37: modifier onlyOwnerOrSnapshooter() {
-38:  if (msg.sender != owner() && msg.sender != snapshooter) {
-39:      revert BTOKEN_UNAUTHORIZED();
-40:    }

+   if (msg.sender != snapshooter) {
+        if (msg.sender != owner()) {
+            revert BTOKEN_UNAUTHORIZED();
+        }
+    }


```

#### Instance 4

```solidity
File : tokenvault/BridgedERC20Base.sol

45:    if (_migratingAddress == migratingAddress && _migratingInbound == migratingInbound) {
46:        revert BB_INVALID_PARAMS();
47:    }

```

[BridgedERC20Base.sol#L45-L47](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L45-L47)

**Recommended Mitigation Steps:**

```diff
File : tokenvault/BridgedERC20Base.sol

-45:    if (_migratingAddress == migratingAddress && _migratingInbound == migratingInbound) {
-46:        revert BB_INVALID_PARAMS();
-47:    }
+      if (_migratingAddress == migratingAddress){
+         if(_migratingInbound == migratingInbound){
+            revert BB_INVALID_PARAMS();
+         }
+      }

```

## [G-27] Use separate if statements instead of the logical OR (||) operator (**Gas Saved ~30 Gas**)

**Total Gas Saved: ~30 Gas**
**Gas Saved Per Instance: ~10 Gas**

Refactor the code to use separate if statements for each condition instead of combining them with the logical OR operator. This allows each condition to be evaluated independently, potentially saving gas by avoiding unnecessary OR evaluation when a earlier condition is true to revert.

### 3 Instances

```solidity
File : tokenvault/ERC20Vault.sol

158:        if (_btokenNew == address(0) || bridgedToCanonical[_btokenNew].addr != address(0)) {
159:            revert VAULT_INVALID_NEW_BTOKEN();
160:        }
...
174:   if (
175:        ctoken.decimals != _ctoken.decimals
176:        || keccak256(bytes(ctoken.symbol)) != keccak256(bytes(_ctoken.symbol))
177:        || keccak256(bytes(ctoken.name)) != keccak256(bytes(_ctoken.name))
178:       ) revert VAULT_CTOKEN_MISMATCH();
```

[ERC20Vault.sol#L158-L178](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L158-L178)

**Recommended Mitigation Steps:**

```diff
File : tokenvault/ERC20Vault.sol

+  // Refactor the if statement to use separate if statements
+  if (_btokenNew == address(0)) {
+    revert VAULT_INVALID_NEW_BTOKEN();
+  }
+
+   if (bridgedToCanonical[_btokenNew].addr != address(0)) {
+      revert VAULT_INVALID_NEW_BTOKEN();
+ }
158:        if (_btokenNew == address(0) || bridgedToCanonical[_btokenNew].addr != address(0)) {
159:            revert VAULT_INVALID_NEW_BTOKEN();
160:        }
...
174:   if (
175:        ctoken.decimals != _ctoken.decimals
176:        || keccak256(bytes(ctoken.symbol)) != keccak256(bytes(_ctoken.symbol))
177:        || keccak256(bytes(ctoken.name)) != keccak256(bytes(_ctoken.name))
178:       ) revert VAULT_CTOKEN_MISMATCH();

+ // Refactor the if statement to use separate if statements
+ if (ctoken.decimals != _ctoken.decimals) {
+    revert VAULT_CTOKEN_MISMATCH();
+ }
+
+ if (keccak256(bytes(ctoken.symbol)) != keccak256(bytes(_ctoken.symbol))) {
+    revert VAULT_CTOKEN_MISMATCH();
+ }
+
+ if (keccak256(bytes(ctoken.name)) != keccak256(bytes(_ctoken.name))) {
+    revert VAULT_CTOKEN_MISMATCH();
+ }
```

## [G-28] Do not create stack variable if the value assigned into it is used only once, use that value directly (**Saves ~10 Gas**)

If the variable is only accessed once, it's cheaper to use the assigned value directly that one time, and save the 3 gas the extra stack assignment would spend.

```solidity
File : bridge/Bridge.sol

138:   uint256 expectedAmount = _message.value + _message.fee;
139:   if (expectedAmount != msg.value) revert B_INVALID_VALUE();
```

[Bridge.sol#L138-L139](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L138-L139)

**Recommended Mitigation Steps:**

```diff
File : bridge/Bridge.sol

-138:   uint256 expectedAmount = _message.value + _message.fee;
-139:   if (expectedAmount != msg.value) revert B_INVALID_VALUE();
+      if ((_message.value + _message.fee) != msg.value) revert B_INVALID_VALUE();

```

## [G-29] `address(this)` should be cached instead of re-calculating multiple times.

```solidity
File : tokenvault/ERC20Vault.sol

378:   uint256 _balance = t.balanceOf(address(this));
379:   t.safeTransferFrom({ from: msg.sender, to: address(this), value: _amount });
380:   balanceChange_ = t.balanceOf(address(this)) - _balance;
```

[ERC20Vault.sol#L378-L380](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L378-L380)

**Recommended Mitigation Steps:**

```diff
File : tokenvault/ERC20Vault.sol

+      address addressOfThisContract = address(this);
-378:   uint256 _balance = t.balanceOf(address(this));
-379:   t.safeTransferFrom({ from: msg.sender, to: address(this), value: _amount });
-380:   balanceChange_ = t.balanceOf(address(this)) - _balance;

+   uint256 _balance = t.balanceOf(addressOfThisContract);
+  t.safeTransferFrom({ from: msg.sender, to: addressOfThisContract, value: _amount });
+   balanceChange_ = t.balanceOf(addressOfThisContract) - _balance;
```

## [G-30] Make 3 event parameters indexed when possible

It is the most gas efficient to make up to 3 event parameters indexed. If there are less than 3 parameters, you need to make all parameters indexed.

### 2 Instances

```solidity
File : tokenvault/ERC20Vault.sol

80: event BridgedTokenChanged(
81:     uint256 indexed srcChainId,
82:     address indexed ctoken,
83:     address btokenOld,
84:     address btokenNew,
85:     string ctokenSymbol,
86:     string ctokenName,
87:     uint8 ctokenDecimal
88:  );
...
...
114: event TokenReleased(
115:   bytes32 indexed msgHash, address indexed from, address ctoken, address token, uint256 amount
116:  );

```

[ERC20Vault.sol#L80-L88](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L80-L88), [ERC20Vault.sol#L114-L116](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L114-L116)

## [G-31] Check `contract` ether _balance >= transferring value_ before transferring `ethers` to fail early

To ensure safe transfers of ethers and avoid unexpected failures it's essential to check the contract balance is >= require value transferring, proceeding with the transfers. This helps prevent unintended transfers when the contract does not possess sufficient funds to fulfill the transfer request. An dsaves the gas by failing early if txn will revert anyway int he middle.

```solidity
File : tokenvault/ERC20Vault.sol

304:   _message.srcOwner.sendEther(_message.value);
```

[ERC20Vault.sol#L271](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L271)

**Recommended Mitigation Steps:**

```diff
File : tokenvault/ERC20Vault.sol

+    require(address(this).balance >= _message.value, "Not enough balance");
304:   _message.srcOwner.sendEther(_message.value);
```

## [G-32] `Switch` the order of `if` statement to less consuming first (**Saves 1 SSTORE and 1 SLOAD half of the times**)

It is recommended to order checks from low to high gas consuming to revert early.

```solidity
File : verifiers/SgxVerifier.sol

210: for (uint256 i; i < _instances.length; ++i) {
211:        if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();
212:
213:       addressRegistered[_instances[i]] = true;
214:
215:        if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();
216:
217:         instances[nextInstanceId] = Instance(_instances[i], validSince);
218:         ids[i] = nextInstanceId;
219:
220:          emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);
221:
222:            nextInstanceId++;
223:        }
```

[SgxVerifier.sol#L210-L223](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210-L223)

**Recommended Mitigation Steps:**

```diff
File : verifiers/SgxVerifier.sol

210: for (uint256 i; i < _instances.length; ++i) {
+         if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();
+
211:        if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();
212:
213:       addressRegistered[_instances[i]] = true;
214:
-215:        if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();
216:
217:         instances[nextInstanceId] = Instance(_instances[i], validSince);
218:         ids[i] = nextInstanceId;
219:
220:          emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);
221:
222:            nextInstanceId++;
223:        }
```

## [G-33] Multiple accesses of the same mapping/array key/index should be cached in local variable

The instances below point to the second+ access of a value inside a mapping/array key/index, within a function. Caching a mapping's value in a local storage or calldata variable when the value is accessed multiple times, saves ~42 gas per access due to not having to recalculate the key's keccak256 hash (Gkeccak256 - 30 gas) and that calculation's associated stack operations. Caching an array's struct avoids recalculating the array offsets into memory/calldata

### Cache `instances[id].validSince` mapping to save 1 SLOAD(~100 Gas)

```solidity
File : verifiers/SgxVerifier.sol

235: if (instance != instances[id].addr) return false;
236:        return instances[id].validSince <= block.timestamp
237:            && block.timestamp <= instances[id].validSince + INSTANCE_EXPIRY;
```

[SgxVerifier.sol#L235-L237](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L235-L237)

**Recommended Mitigation Steps:**

```diff
File : verifiers/SgxVerifier.sol

+      Instance _instancesId_validSince = instances[id].validSince;
235: if (instance != instances[id].addr) return false;
-236:        return instances[id].validSince <= block.timestamp
-237:            && block.timestamp <= instances[id].validSince + INSTANCE_EXPIRY;
+        return _instancesId_validSince <= block.timestamp
+            && block.timestamp <= _instancesId_validSince + INSTANCE_EXPIRY;
```

## [G-34] Use `calldata` instead of `memory` for function arguments that do not get mutated (**Gas Saved ~300 Gas**)

Mark data types as calldata instead of memory where possible. This makes it so that the data is not automatically loaded into memory. If the data passed into the function does not need to be changed (like updating values in an array), it can be passed in as calldata. The one exception to this is if the argument must later be passed into another function that takes an argument that specifies memory storage.

```solidity
File : verifiers/SgxVerifier.sol

171:    function getSignedHash(
172:     TaikoData.Transition memory _tran,

```

[SgxVerifier.sol#L171-L172](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L171-L172)

**Recommended Mitigation Steps:**

```diff
File : verifiers/SgxVerifier.sol

171:    function getSignedHash(
-172:     TaikoData.Transition memory _tran,
+       TaikoData.Transition calldata _tran,

```

## [G-35] Use `abi.encodePacked` instead of `abi.encode`

By using abi.encodePacked, unnecessary padding is avoided, resulting in a more efficient encoding process and reducing gas consumption for transactions or contract deployments. This optimization aligns with best practices for gas-efficient smart contract development.

```solidity
File : signal/SignalService.sol

185:    {
186:        return keccak256(abi.encode(_chainId, _kind, _blockId));
187:    }

```

[SignalService.sol#L185-L187](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L185-L187)

**Recommended Mitigation Steps:**

```diff
File : signal/SignalService.sol

185:    {
-186:        return keccak256(abi.encode(_chainId, _kind, _blockId));
+          return keccak256(abi.encodePacked(_chainId, _kind, _blockId));
187:    }

```

### `cacheOption` can be packed with `blockId` saves 1 slot(~2000 Gas)

Since `cacheOption` holds only 4 param so it can be packed with `blockId`.

```solidity
File : signal/ISignalService.sol

20: struct HopProof {
21:        uint64 chainId;
22:        uint64 blockId;
23:        bytes32 rootHash;
24:        CacheOption cacheOption;
25:        bytes[] accountProof;
26:        bytes[] storageProof;
27:    }

```

[ISignalService.sol#L20-L27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L20-L27)

**Recommended Mitigation Steps:**

```diff
File : signal/ISignalService.sol

20: struct HopProof {
21:        uint64 chainId;
22:        uint64 blockId;
+         CacheOption cacheOption;
23:        bytes32 rootHash;
-24:        CacheOption cacheOption;
25:        bytes[] accountProof;
26:        bytes[] storageProof;
27:    }

```

## [G-36] Structs can be packed into fewer storage slot by re-arranging the storage variables (**Gas Saved: ~4000 Gas**)

As the solidity EVM works with 32 bytes, variables less than 32 bytes should be packed inside a struct so that they can be stored in the same slot, this saves gas when writing to storage ~20000 gas

### Reorder the `cacheOption` variable and place it with `blockId` saves 1 slot(~2000 Gas)

Since `cacheOption` holds only 4 param so it can be packed with `blockId`.

```solidity
File : signal/ISignalService.sol

20: struct HopProof {
21:        uint64 chainId;
22:        uint64 blockId;
23:        bytes32 rootHash;
24:        CacheOption cacheOption;
25:        bytes[] accountProof;
26:        bytes[] storageProof;
27:    }

```

[ISignalService.sol#L20-L27](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/ISignalService.sol#L20-L27)

**Recommended Mitigation Steps:**

```diff
File : signal/ISignalService.sol

20: struct HopProof {
21:        uint64 chainId;
22:        uint64 blockId;
+         CacheOption cacheOption;
23:        bytes32 rootHash;
-24:        CacheOption cacheOption;
25:        bytes[] accountProof;
26:        bytes[] storageProof;
27:    }

```

### Reorder the `blockSyncThreshold` variable and place it with `ethDepositMaxAmount` saves 1 slot(~2000 Gas)

```solidity
File : L1/TaikoData.sol

10: struct Config {
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
        uint64 maxBlocksToVerifyPerProposal;
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
        uint96 livenessBond;
        // ---------------------------------------------------------------------
        // Group 4: ETH deposit related configs
        // ---------------------------------------------------------------------
        // The size of the ETH deposit ring buffer.
        uint256 ethDepositRingBufferSize;
        // The minimum number of ETH deposits allowed per block.
        uint64 ethDepositMinCountPerBlock;
        // The maximum number of ETH deposits allowed per block.
        uint64 ethDepositMaxCountPerBlock;
        // The minimum amount of ETH required for a deposit.
        uint96 ethDepositMinAmount;
        // The maximum amount of ETH allowed for a deposit.
        uint96 ethDepositMaxAmount;
        // The gas cost for processing an ETH deposit.
        uint256 ethDepositGas;
        // The maximum fee allowed for an ETH deposit.
        uint256 ethDepositMaxFee;
        // The max number of L2 blocks that can stay unsynced on L1 (a value of zero disables
        // syncing)
        uint8 blockSyncThreshold;
60:    }
```

[TaikoData.sol#L10-L60](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L10-L60)

**Recommended Mitigation Steps:**

```diff
File : L1/TaikoData.sol

10: struct Config {
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
        uint64 maxBlocksToVerifyPerProposal;
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
        uint96 livenessBond;
        // ---------------------------------------------------------------------
        // Group 4: ETH deposit related configs
        // ---------------------------------------------------------------------
        // The size of the ETH deposit ring buffer.
        uint256 ethDepositRingBufferSize;
        // The minimum number of ETH deposits allowed per block.
        uint64 ethDepositMinCountPerBlock;
        // The maximum number of ETH deposits allowed per block.
        uint64 ethDepositMaxCountPerBlock;
        // The minimum amount of ETH required for a deposit.
        uint96 ethDepositMinAmount;
        // The maximum amount of ETH allowed for a deposit.
        uint96 ethDepositMaxAmount;
+      uint8 blockSyncThreshold;
        // The gas cost for processing an ETH deposit.
        uint256 ethDepositGas;
        // The maximum fee allowed for an ETH deposit.
        uint256 ethDepositMaxFee;
        // The max number of L2 blocks that can stay unsynced on L1 (a value of zero disables
        // syncing)
-        uint8 blockSyncThreshold;
60:    }
```
