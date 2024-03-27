# Quality Assurance Report

| ID     | QA issues                                                                                                                           |
|--------|-------------------------------------------------------------------------------------------------------------------------------------|
| [L-01] | Consider initializing ContextUpgradeable contract by calling __Context_init() in TaikoToken.sol                                     |
| [L-02] | Missing address(0) check for USDC in USDCAdapter                                                                                    |
| [L-03] | __ERC1155Receiver_init() not initialized in ERC1155Vault                                                                            |
| [L-04] | srcToken and srcChainId is not updated on old token after migration through changeBridgedToken()                                    |
| [L-05] | MerkleClaimable does not check if claimStart is less than claimEnd                                                                  |
| [L-06] | If amountUnlocked in TimelockTokenPool is less than 1e18, rounding down occurs                                                      |
| [L-07] | sendSignal() calls can be spammed by attacker to relayer                                                                            |
| [L-08] | Consider calling Ownable_init() function in constructor to prevent frontrunning of initializer functions are non-approved attackers |
| [L-09] | Add "Zero if owner will process themself" comment to gasLimit instead of fee                                                        |
| [L-10] | Bridge integration issues with swapping protocols                                                                                   |
| [L-11] | sendMessage() does not check if STATUS is equal to NEW                                                                              |
| [L-12] | Protocol does not refund extra ETH but implements strict check                                                                      |
| [L-13] | If a message is suspended before processMessage() is called, the ERC20 tokens on the source chain and Ether are not refunded.       |
| [L-14] | User loses all Ether if their address is blacklisted on canonical token                                                             |
| [L-15] | onMessageInvocation checks in _invokeMessageCall() can be bypassed to call arbitrary function from Bridge contract                  |
| [L-16] | Consider reading return value from snapshot() function                                                                              |
| [L-17] | One off error in block sync threshold check to sync chain data                                                                      |
| [L-18] | Guardian proof that is never fully approved by minGuardians is never deleted                                                        |
| [L-19] | Consider making the TIMELOCK_ADMIN_ROLE undergo a delay when transferring the admin role                                            |
| [L=20] | One-off error when evaluating deposits to process with the ring buffer size                                                         |
| [R-01] | Consider implementing changeBridgedToken() and btokenBlacklist for ERC721Vault and ERC1155Vault                                     |
| [R-02] | Instead of passing an empty string for the data parameter in NFT vaults on token transfers, allow users to supply data              |
| [R-03] | Use named imports to improve readability of the code and avoid polluting the global namespace                                       |
| [N-01] | Avoid hardcoding data in BridgedERC1155                                                                                             |
| [N-02] | Missing source()/canonical() function on BridgedERC115 contract                                                                     |
| [N-03] | Using unchecked arithmetic in for loops is handled by solc compiler 0.8.22 onwards                                                  |
| [N-04] | Typo in comment in Bytes.sol                                                                                                        |
| [N-05] | Incorrect comment regarding gasLimit in processMessage()                                                                            |
| [N-06] | Use require instead of assert                                                                                                       |
| [N-07] | Incorrect natspec comment for proveMessageReceived()                                                                                |

## [L-01] Consider initializing ContextUpgradeable contract by calling __Context_init() in TaikoToken.sol

[Link](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoToken.sol#L25)

ContextUpgradeable is not initialized in TaikoToken.sol contract. This contract is used in ERC20PermitUpgradeable which is used in ERC20VotesUpgradeable. But neither contract initializes this Context contract when the contracts themselves are intialized. 

In TaikoToken.sol [here](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoToken.sol#L25), we can see that the below __Context_init() function is not called.
```solidity
File: ContextUpgradeable.sol
18:     function __Context_init() internal onlyInitializing {
19:     }
20: 
21:     function __Context_init_unchained() internal onlyInitializing {
22:     }
```

## [L-02] Missing address(0) check for USDC in USDCAdapter

[Link](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L38)

It is important to implement this check in init() functions since they can only be called once.

```solidity
File: USDCAdapter.sol
38:     function init(address _owner, address _addressManager, IUSDC _usdc) external initializer {
39:         __Essential_init(_owner, _addressManager);
40:        
41:         usdc = _usdc;
42:     }
```

## [L-03]  __ERC1155Receiver_init() not initialized in ERC1155Vault

[Link](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L29)

Consider initializing these functions in an init() function in the ERC1155Vault contract.
```solidity
File: ERC1155ReceiverUpgradeable.sol
14:     function __ERC1155Receiver_init() internal onlyInitializing {
15:     }
16: 
17:     function __ERC1155Receiver_init_unchained() internal onlyInitializing {
18:     }
```

## [L-04] srcToken and srcChainId is not updated on old token after migration through changeBridgedToken()

[Link](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L73)

When a token is migrated to another token, the old token still points towards the same srcToken and srcChainId as the new token since they are not updated through changeBridgedToken(). 

Due to this external dapps integrating and using these values as reference could run into potential issues. Consider clearing them or changing them to some placeholder data representing the src token and chainId but with a prefix. 
```solidity
File: BridgedERC20.sol
123:     function canonical() public view returns (address, uint256) {
124:         return (srcToken, srcChainId);
125:     }
```

## [L-05] MerkleClaimable does not check if claimStart is less than claimEnd

```solidity
File: MerkleClaimable.sol
90:     function _setConfig(uint64 _claimStart, uint64 _claimEnd, bytes32 _merkleRoot) private {
91:         
92:         claimStart = _claimStart;
93:         claimEnd = _claimEnd;
94:         merkleRoot = _merkleRoot;
95:     }
```

## [L-06] If amountUnlocked in TimelockTokenPool is less than 1e18, rounding down occurs

[Link](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L197)

If amountUnlocked is less than 1e18, round down occurs. This is not a problem since grants will usually be dealing with way higher values and thus higher unlocking. But this would be a problem for team members or advisors getting maybe 10 taiko or less (in case price of taiko is high). So the more frequent the withdrawing there might be chances of losing tokens due to round down.
```solidity
File: TimelockTokenPool.sol
198:         uint128 _amountUnlocked = amountUnlocked / 1e18; // divide first
```

## [L-07] sendSignal() calls can be spammed by attacker to relayer

[Link](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L63)

Since the function is external, an attacker can continuously spam signals to the offchain relayer which is always listening to signals. This would be more cost efficient on Taiko where fees are cheap.

The signals could also be used to mess with the relayer service i.e. by sending a the same signal early by frontrunning a user's bytes32 signal _parameter.
```solidity
File: SignalService.sol
68:     function sendSignal(bytes32 _signal) external returns (bytes32) {
69:         return _sendSignal(msg.sender, _signal, _signal);
70:     }
```

## [L-08] Consider calling Ownable_init() function in constructor to prevent frontrunning of initializer functions are non-approved attackers

[Link](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L65)

Most init functions inheriting from EssentialContract do not implement have restrictions on those functions, which allow anyone to initialize them if not done during deployment. 

Consider calling the function in the constructor and applying the onlyOwner modifier on the init functions.
```solidity
File: EssentialContract.sol
70:     constructor() {
71:         _disableInitializers();
72:     }
```

## [L-09] Add "Zero if owner will process themself" comment to gasLimit instead of fee

In the current code, the preferredExecutor for executing bridged transactions is determined by whether the gasLimit is 0 or not and not the fee.
```solidity
File: IBridge.sol
38:         // Processing fee for the relayer. Zero if owner will process themself. 
39:         uint256 fee;
40:         // gasLimit to invoke on the destination chain.
41:         uint256 gasLimit;
```

## [L-10] Bridge integration issues with swapping protocols

Cross-chain swapping could not occur on chains having long invocation delays since deadline of the swap might expire and become outdated. Consider having custom delays for dapps looking to use bridge. 

```solidity
File: Bridge.sol
459:     /// the transactor is not the preferredExecutor who proved this message.
460:     function getInvocationDelays()
461:         public
462:         view
463:         virtual
464:         returns (uint256 invocationDelay_, uint256 invocationExtraDelay_)
465:     {
466:         if (
467:             block.chainid == 1 // Ethereum mainnet
468:         ) {
469:             // For Taiko mainnet
470:             // 384 seconds = 6.4 minutes = one ethereum epoch
471:             return (1 hours, 384 seconds);
472:         } else if (
473:             block.chainid == 2 || // Ropsten
474:             block.chainid == 4 || // Rinkeby
475:             block.chainid == 5 || // Goerli
476:             block.chainid == 42 || // Kovan
477:             block.chainid == 17_000 || // Holesky
478:             block.chainid == 11_155_111 // Sepolia
479:         ) {
480:             // For all Taiko public testnets
481:             return (30 minutes, 384 seconds);
482:         } else if (block.chainid >= 32_300 && block.chainid <= 32_400) {
483:             // For all Taiko internal devnets
484:             return (5 minutes, 384 seconds);
485:         } else {
486:             // This is a Taiko L2 chain where no deleys are applied.
487:             return (0, 0);
488:         }
489:     }
```

## [L-11] sendMessage() does not check if STATUS is equal to NEW

[Link](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L115)

Adding a sanity check would be good to avoid being able to call message that is not in the STATUS = NEW state. This would ensure retriable, recalls and failed txns cannot be repeated again.
```solidity
File: Bridge.sol
119:     function sendMessage(
120:         Message calldata _message
121:     )
122:         external
123:         payable
124:         override
125:         nonReentrant
126:         whenNotPaused
127:         returns (bytes32 msgHash_, Message memory message_)
128:     {
129:         // Ensure the message owner is not null.
130:         if (
131:             _message.srcOwner == address(0) || _message.destOwner == address(0)
132:         ) {
133:             revert B_INVALID_USER();
134:         }
135: 
136:         // Check if the destination chain is enabled.
137:         (bool destChainEnabled, ) = isDestChainEnabled(_message.destChainId);
138: 
139:         // Verify destination chain and to address.
140:         if (!destChainEnabled) revert B_INVALID_CHAINID();
141:         if (_message.destChainId == block.chainid) {
142:             revert B_INVALID_CHAINID();
143:         }
144: 
145:         // Ensure the sent value matches the expected amount.
146:         
148:         uint256 expectedAmount = _message.value + _message.fee;
149:         if (expectedAmount != msg.value) revert B_INVALID_VALUE();
150: 
151:         message_ = _message;
152: 
153:         // Configure message details and send signal to indicate message sending.
154:         message_.id = nextMessageId++;
155:         message_.from = msg.sender; 
156:         message_.srcChainId = uint64(block.chainid);
157: 
158:         msgHash_ = hashMessage(message_);
159: 
160:         ISignalService(resolve("signal_service", false)).sendSignal(msgHash_);
161:         emit MessageSent(msgHash_, message_);
162:     }
```

## [L-12] Protocol does not refund extra ETH but implements strict check 

[See spec here](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/IBridge.sol#L105)

The IBridge.sol contract specifies that extra ETH provided when sending a message is refunded back to the user. This currently does not happen since the code implements strict equality check. Using strict equality is better but pointing out the spec described, which would either be followed in the code implemented or the spec should be described properly in the IBridge.sol contract.

```solidity
File: Bridge.sol
146:         uint256 expectedAmount = _message.value + _message.fee;
147:         if (expectedAmount != msg.value) revert B_INVALID_VALUE();
```

## [L-13] If a message is suspended before processMessage() is called, the ERC20 tokens on the source chain and Ether are not refunded.

If a message is suspended before processMessage() is called, the status of the message remains new and the ERC20 tokens on the source and the Ether is locked as well. If the message will never be unsuspended, consider refunding the tokens to the user.
```solidity
File: Bridge.sol
287:         if (block.timestamp >= invocationDelay + receivedAt) {
288:             // If the gas limit is set to zero, only the owner can process the message.
289:             if (_message.gasLimit == 0 && msg.sender != _message.destOwner) {
290:                 revert B_PERMISSION_DENIED();
291:             }
```

## [L-14] User loses all Ether if their address is blacklisted on canonical token

When recalls are made on the source chain using the function recallMessage(), it calls the onMessageRecalled() function on the ERC20Vault contract. The onMessageRecalled() function transfers the ERC20 tokens back to the user along with any Ether that was supplied.

The issue is with this dual transfer where both ERC20 tokens are Ether are transferred to the user in the same call. If the user is blacklisted on the canonical token, the whole call reverts, causing the Ether to be stuck in the Bridge contract.

To understand this, let's consider a simple example:
1. User bridges ERC20 canonical tokens and Ether from chain A to chain B.
2. The message call on the destination chain B goes into RETRIABLE status if it fails for the first time. (**Note: User can only process after invocation delay**).
3. On multiple retries after a while, the user decides to make a last attempt, on which the call fails and goes into FAILED status. 
4. During this time on chain B, the user was blacklisted on the ERC20 canonical token on the source chain.
4. When the failure signal is received by the source chain A from chain B, the user calls recallMessage() on chain A only to find out that although the blacklist is only for the canonical ERC20 token, the Ether is stuck as well. 

## [L-15] onMessageInvocation checks in _invokeMessageCall() can be bypassed to call arbitrary function from Bridge contract

[Link](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L490)

The if block requires the data to be greater than equal to 4 bytes, equal to the onMessageInvocation selector and last but not the least for the target address to be a contract.

What an attacker could do to bypass this expected spec is to pre-compute an address for the destination chain and pass it in `_message.to`. He can pass gasLimit = 0 from source to only allow him to process the message on the destination. 

On the destination chain, the attacker can deploy his pre-computed contract address and call processMessage() with it from the constructor. For a chain (L2s/L3s) with no invocation delays, the proving + executing of the message data would go through in one single call.

When we arrive at the isContract check below on the `_message.to` address, we evaluate to false since the size of the contract during construction is 0. Due to this, the attacker can validly bypass the onMessageInvocation selector that is a requirement/single source of tx origination by the protocol for all transactions occurring from the bridge contract. This breaks a core invariant of the protocol.
```solidity
File: Bridge.sol
513:         if (
514:             _message.data.length >= 4 && // msg can be empty
515:             bytes4(_message.data) !=
516:             IMessageInvocable.onMessageInvocation.selector &&
517:             _message.to.isContract()
518:         ) {
519:             success_ = false; 
520:         } else {
521:             (success_, ) = ExcessivelySafeCall.excessivelySafeCall(
522:                 _message.to,
523:                 _gasLimit,
524:                 _message.value,
525:                 64, // return max 64 bytes
526:                 _message.data
527:             );
528:         }
```

## [L-16] Consider reading return value from snapshot() function

[Link](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoToken.sol#L52)

The snapshot() function returns a uint256 snapshotId. These ids if retrieved earlier can make the devs life easier when taking multiple timely snapshots.
```solidity
File: TaikoToken.sol
54:     function snapshot() public onlyFromOwnerOrNamed("snapshooter") {
55:         _snapshot();
56:     }
```

## [L-17] One off error in block sync threshold check to sync chain data

The check should be _l1BlockId >= lastSyncedBlock + BLOCK_SYNC_THRESHOLD since threshold is the minimum threshold. 
```solidity
File: TaikoL2.sol
150:         if (_l1BlockId > lastSyncedBlock + BLOCK_SYNC_THRESHOLD) {
151:             // Store the L1's state root as a signal to the local signal service to
152:             // allow for multi-hop bridging.
153:             ISignalService(resolve("signal_service", false)).syncChainData(
154:                 ownerChainId,
155:                 LibSignals.STATE_ROOT,
156:                 _l1BlockId,
157:                 _l1StateRoot
158:             );
```

Same issue here:
```solidity
File: LibVerifying.sol
240:         if (_lastVerifiedBlockId > lastSyncedBlock + _config.blockSyncThreshold) {
241:             signalService.syncChainData(
242:                 _config.chainId, LibSignals.STATE_ROOT, _lastVerifiedBlockId, _stateRoot
243:             );
244:         }
```

## [L-18] Guardian proof that is never fully approved by minGuardians is never deleted

A guardian proof hashs is only deleted if it has been approved by min number of guardians in the approval bits. In case it is not, the approval for the hash remains and is not deleted. 
```solidity
File: GuardianProver.sol
50:         if (approved_) {
51:             deleteApproval(hash);
52:             ITaikoL1(resolve("taiko", false)).proveBlock(_meta.id, abi.encode(_meta, _tran, _proof));
53:         }
```

## [L-19] Consider making the TIMELOCK_ADMIN_ROLE undergo a delay when transferring the admin role

The admin is allowed to skip the delay in operations. But the delay should not be skipped when the role is being transferred.
```solidity
File: TaikoTimelockController.sol
25:     function getMinDelay() public view override returns (uint256) {
26:         return hasRole(TIMELOCK_ADMIN_ROLE, msg.sender) ? 0 : super.getMinDelay();
27:     }
```

## [L-20] One-off error when evaluating deposits to process with the ring buffer size

[Link](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L141)

When calculating the deposits to process, we do not want to overwrite existing slots. This is why the last check/condition is implemented.

The issue with the condition is that it is one-off by the max size the ring bugger allows. Since + 1 is already added, make the check < into <= to work to it's full capacity. 
```solidity
File: LibDepositing.sol
148:         unchecked {
149:              
150:             return
151:                 _amount >= _config.ethDepositMinAmount &&
152:                 _amount <= _config.ethDepositMaxAmount &&
153:                 _state.slotA.numEthDeposits -
154:                     _state.slotA.nextEthDepositToProcess <
155:                 _config.ethDepositRingBufferSize - 1;   
156:         }
```

## [R-01] Consider implementing changeBridgedToken() and btokenBlacklist for ERC721Vault and ERC1155Vault

[Link](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L29)

Both vaults are currently missing these two functions. Implementing them is not required but it would be good as a safety net for high-valued NFT collections in emergency scenarios that could arise.

## [R-02] Instead of passing an empty string for the data parameter in NFT vaults on token transfers, allow users to supply data

Allow users to supply the data parameter when transferring tokens from vault to them to ensure any off-chain compatibility/functionality can be built. 
```solidity
File: ERC1155Vault.sol
227:     function _transferTokens(
228:         CanonicalNFT memory ctoken,
229:         address to,
230:         uint256[] memory tokenIds,
231:         uint256[] memory amounts
232:     ) private returns (address token) {
233:         if (ctoken.chainId == block.chainid) {
234:             // Token lives on this chain
235:             token = ctoken.addr;
236:             
237:             IERC1155(token).safeBatchTransferFrom(
238:                 address(this),
239:                 to,
240:                 tokenIds,
241:                 amounts,
242:                 ""
243:             );
```

## [R-03] Use named imports to improve readability of the code and avoid polluting the global namespace

```solidity
File: LibAddress.sol
4: import "@openzeppelin/contracts/utils/Address.sol";
5: import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol";
6: import "@openzeppelin/contracts/utils/introspection/IERC165.sol";
7: import "@openzeppelin/contracts/interfaces/IERC1271.sol";
8: import "../thirdparty/nomad-xyz/ExcessivelySafeCall.sol";
```

## [N-01] Avoid hardcoding data in BridgedERC1155

[Link](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L52)

Instead of hardcoding the data, place it in a constant variable and assign the variables here for better maintainability.
```solidity
File: BridgedERC1155.sol
53:         LibBridgedToken.validateInputs(_srcToken, _srcChainId, "foo", "foo");
```

## [N-02] Missing source()/canonical() function on BridgedERC115 contract

[Link](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L52)

The BridgedERC1155 contract should implement a similar function to source()/canonical() as done in the other two vaults. This would better for external dapps to retrieve the data much easily.

## [N-03] Using unchecked arithmetic in for loops is handled by solc compiler 0.8.22 onwards

```solidity
File: MerkleTrie.sol
205:     function _parseProof(bytes[] memory _proof) private pure returns (TrieNode[] memory proof_) {
206:         uint256 length = _proof.length;
207:         proof_ = new TrieNode[](length);
208:         for (uint256 i = 0; i < length;) {
209:             proof_[i] = TrieNode({ encoded: _proof[i], decoded: RLPReader.readList(_proof[i]) });
210:             
211:             unchecked {
212:                 ++i;
213:             }
214:         }
215:     }
```

## [N-04] Typo in comment in Bytes.sol

Use rather instead of rathern.
```solidity
File: Bytes.sol
93:     /// @notice Slices a byte array with a given starting index up to the end of the original byte
94:     ///         array. Returns a new array rathern than a pointer to the original.
```

## [N-05] Incorrect comment regarding gasLimit in processMessage()

As confirmed with the sponsor, the comment above the gasLimit variable should be inversed i.e. use gasLeft is called by owner, else gasLimit
```solidity
File: Bridge.sol
307:             } else {
308:                 // Use the specified message gas limit if called by the owner, else
309:                 // use remaining gas
310:             
311:                 uint256 gasLimit = msg.sender == _message.destOwner
312:                     ? gasleft()
313:                     : _message.gasLimit;
```

## [N-06] Use require instead of assert

Use require instead of assert to avoid Panic error, see solidity docs [here](https://docs.soliditylang.org/en/v0.8.25/control-structures.html#panic-via-assert-and-error-via-require).
```solidity
File: Bridge.sol
503:     function _invokeMessageCall(
504:         Message calldata _message,
505:         bytes32 _msgHash,
506:         uint256 _gasLimit
507:     ) private returns (bool success_) {
508:         if (_gasLimit == 0) revert B_INVALID_GAS_LIMIT();
509:         assert(_message.from != address(this)); 
```

## [N-07] Incorrect natspec comment for proveMessageReceived()

Correct first comment on Line 394 to "msgHash has been received"
```solidity
File: Bridge.sol
394:     /// @notice Checks if a msgHash has failed on its destination chain. 
395:     /// @param _message The message.
396:     /// @param _proof The merkle inclusion proof.
397:     /// @return true if the message has failed, false otherwise.
398:     function proveMessageReceived(
399:         Message calldata _message,
400:         bytes calldata _proof
401:     ) public view returns (bool) {
```