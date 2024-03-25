# Gas Optimizations Report

| ID     | Gas Optimizations                                                                    | Instances |
|--------|--------------------------------------------------------------------------------------|-----------|
| [G-01] | Pack structs tightly to consume less slots and save gas                              | 2         |
| [G-02] | Remove block.coinbase != address(0) check in function onBlockProposed()              | 1         |
| [G-03] | Use do-while loop instead of for loop to save gas                                    | 7         |
| [G-04] | Instead of accessing `deposits_[i].amount` consider typecasting `data`               | 1         |
| [G-05] | Assigning `meta_.txListByteOffset` to 0 not required due to default value being 0    | 1         |
| [G-06] | Cache _newGuardians.length to save gas                                               | 1         |
| [G-07] | Instead of assigning guardians.length as guardianId, use i + 1 to save gas           | 1         |
| [G-08] | Consider removing redundant skipFeeCheck() condition                                 | 1         |
| [G-09] | Remove redundant nonReentrant modifier                                               | 1         |
| [G-10] | Consider adding refundAmount > 0 check to save gas on unnecessary sendEther() call   | 1         |
| [G-11] | No need to explicitly set success variable to false due to default value being false | 1         |
| [G-12] | Consider using if-else block instead of ternary operators                            | 2         |
| [G-13] | Modifier checks not required on function _verfiyHopProof()                           | 1         |
| [G-14] | Cache op.token in function _handleMessage() to save gas                              | 1         |
| [G-15] | Consider using safeBatchTransferFrom() instead of running a for loop                 | 1         |

## [G-01] Pack structs tightly to consume less slots and save gas

[Link to instance](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L39)

The struct currently uses 8 slots. One slot can be reduced by moving the `uint8 blockSyncThreshold` variable on Line 60 after `uint96 livenessBond; ` on Line 40. This is because variables from Lines 27 to 40 occupying slot 2 only use up 24 bytes, thus more variable of smaller size can be fit into the slot. The reason the last variable can be moved is to ensure the readability of the code due to the comments by the team grouping them. 
```solidity
File: TaikoData.sol
11:     struct Config {
12:         // ---------------------------------------------------------------------
13:         // Group 1: General configs
14:         // ---------------------------------------------------------------------
15:         // The chain ID of the network where Taiko contracts are deployed.
16:         uint64 chainId;
17:         // ---------------------------------------------------------------------
18:         // Group 2: Block level configs
19:         // ---------------------------------------------------------------------
20:         // The maximum number of proposals allowed in a single block.
21:         uint64 blockMaxProposals;
22:         // Size of the block ring buffer, allowing extra space for proposals.
23:         uint64 blockRingBufferSize;
24:         // The maximum number of verifications allowed when a block is proposed.
25:         uint64 maxBlocksToVerifyPerProposal; 
26:         // The maximum gas limit allowed for a block.
27:         uint32 blockMaxGasLimit;
28:         // The maximum allowed bytes for the proposed transaction list calldata.
29:         uint24 blockMaxTxListBytes;
30:         // The max period in seconds that a blob can be reused for DA.
31:         uint24 blobExpiry;
32:         // True if EIP-4844 is enabled for DA
33:         bool blobAllowedForDA;
34:         // True if blob can be reused
35:         bool blobReuseEnabled;
36:         // ---------------------------------------------------------------------
37:         // Group 3: Proof related configs
38:         // ---------------------------------------------------------------------
39:         // The amount of Taiko token as a prover liveness bond
40:         uint96 livenessBond; 
41:         // ---------------------------------------------------------------------
42:         // Group 4: ETH deposit related configs
43:         // ---------------------------------------------------------------------
44:         // The size of the ETH deposit ring buffer.
45:         uint256 ethDepositRingBufferSize;
46:         // The minimum number of ETH deposits allowed per block.
47:         uint64 ethDepositMinCountPerBlock;
48:         // The maximum number of ETH deposits allowed per block.
49:         uint64 ethDepositMaxCountPerBlock;
50:         // The minimum amount of ETH required for a deposit.
51:         uint96 ethDepositMinAmount;
52:         // The maximum amount of ETH allowed for a deposit.
53:         uint96 ethDepositMaxAmount;
54:         // The gas cost for processing an ETH deposit.
55:         uint256 ethDepositGas;
56:         // The maximum fee allowed for an ETH deposit.
57:         uint256 ethDepositMaxFee;
58:         // The max number of L2 blocks that can stay unsynced on L1 (a value of zero disables
59:         // syncing)
60:         uint8 blockSyncThreshold;
61:     }
```

[Link to instance](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoData.sol#L78)

The struct BlockParams can be packed by moving the variables from Lines 85-87 to the start of the struct. This would ensure that the first slot now not only contains a 20-byte address but also three variables totalling 7 bytes.
```solidity
File: TaikoData.sol
80:     struct BlockParams {
81:         address assignedProver;
82:         address coinbase;
83:         bytes32 extraData;
84:         bytes32 blobHash;
85:         uint24 txListByteOffset;
86:         uint24 txListByteSize;
87:         bool cacheBlobForReuse;
88:         bytes32 parentMetaHash;
89:         HookCall[] hookCalls;
90:     }
```

## [G-02] Remove block.coinbase != address(0) check in function onBlockProposed()

[Link to instance](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L120)

`block.coinbase` is the L1 block builder, which cannot be a zero address. Consider removing the unnecessary check to save gas.
```solidity
File: AssignmentHook.sol
145:         if (input.tip != 0 && block.coinbase != address(0)) {
146:             address(block.coinbase).sendEther(input.tip);
147:         }
```

## [G-03] Use do-while loop instead of for loop to save gas

[Link to POC](https://www.rareskills.io/post/gas-optimization#viewer-39vpt)

[Link to instance](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L59)

```solidity
File: ERC721Airdrop.sol
60:         for (uint256 i; i < tokenIds.length; ++i) {
61:             IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);
62:         }
```

[Link to instance](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L90)

```solidity
File: Bridge.sol
101:         for (uint256 i; i < _msgHashes.length; ++i) {
102:             bytes32 msgHash = _msgHashes[i];
103:             proofReceipt[msgHash].receivedAt = _timestamp;
104:             emit MessageSuspended(msgHash, _suspend);
105:         }
```

[Link to instance](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L234)

```solidity
File: TaikoL2.sol
259:             for (uint256 i; i < 255 && _blockId >= i + 1; ++i) {
260:                 uint256 j = _blockId - i - 1; 
261:                 inputs[j % 255] = blockhash(j);
262:             }
```

[Link to instance](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L74)

```solidity
File: Guardians.sol
83:         for (uint256 i; i < guardians.length; ++i) {
84:             delete guardianIds[guardians[i]];
85:         }
```

[Link to instance](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L172)

```solidity
File: AssignmentHook.sol
192:         for (uint256 i; i < _tierFees.length; ++i) {
193:             if (_tierFees[i].tier == _tierId) return _tierFees[i].fee;
194:         }
```

[Link to instance](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L86)

```solidity
File: LibDepositing.sol
099:             for (uint256 i; i < deposits_.length; ) {        
103:                 uint256 data = _state.ethDeposits[
104:                     j % _config.ethDepositRingBufferSize
105:                 ];
106:                 deposits_[i] = TaikoData.EthDeposit({
107:                     
108:                     recipient: address(uint160(data >> 96)),
109:                     amount: uint96(data),
110:                     id: j
111:                 });
112:                 
113:                 
114:                 uint96 _fee = deposits_[i].amount > fee
115:                     ? fee
116:                     : deposits_[i].amount;
117: 
118:                 // Unchecked is safe:
119:                 // - _fee cannot be bigger than deposits_[i].amount
120:                 // - all values are in the same range (uint96) except loop
121:                 // counter, which obviously cannot be bigger than uint95
122:                 // otherwise the function would be gassing out.
123:                 
124:                 unchecked {
125:                     deposits_[i].amount -= _fee;
126:                     totalFee += _fee;
127:                     ++i;
128:                     ++j;
129:                 }
130:             }
```

[Link to instance](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L244)

```solidity
File: LibProposing.sol
284:             for (uint256 i; i < params.hookCalls.length; ++i) {
285:                 if (uint160(prevHook) >= uint160(params.hookCalls[i].hook)) {
286:                     revert L1_INVALID_HOOK();
287:                 }
288: 
289:                 // When a hook is called, all ether in this contract will be send to the hook.
290:                 // If the ether sent to the hook is not used entirely, the hook shall send the Ether
291:                 // back to this contract for the next hook to use.
292:                 // Proposers shall choose use extra hooks wisely.
293:                      
295:                 IHook(params.hookCalls[i].hook).onBlockProposed{
296:                     value: address(this).balance
297:                 }(blk, meta_, params.hookCalls[i].data);
298: 
299:                 prevHook = params.hookCalls[i].hook;
300:             }
```

## [G-04] Instead of accessing `deposits_[i].amount` consider typecasting `data`

[Link to instance](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L89C2-L93C85)

Instead of accessing deposits_[i].amount on Lines 113 and 115, consider typecasting `data` to uint96 as done on Line 108 to avoid unnecessary memory reads.
```solidity
File: LibDepositing.sol
105:                 deposits_[i] = TaikoData.EthDeposit({
106:                   
107:                     recipient: address(uint160(data >> 96)),
108:                     amount: uint96(data),
109:                     id: j
110:                 });
111:                 
113:                 uint96 _fee = deposits_[i].amount > fee
114:                     ? fee
115:                     : deposits_[i].amount;
```

## [G-05] Assigning `meta_.txListByteOffset` to 0 not required due to default value being 0

[Link to instance](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L190)

Assigning the variable below to 0 is not required since there are not previous assignments made in the else block [here](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L177C1-L192C10) and a value was not for it [here](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L132).
```solidity
File: LibProposing.sol
219:             meta_.txListByteOffset = 0; 
```

## [G-06] Cache _newGuardians.length to save gas

[Link to instance](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L63C1-L69C10)

Lenght of _newGuardians array is accessed multiple times in the function setGuardians(). Consider caching the value.
```solidity
File: Guardians.sol
65:         if (
66:             _newGuardians.length < MIN_NUM_GUARDIANS ||
67:             _newGuardians.length > type(uint8).max
68:         ) {
69:             revert INVALID_GUARDIAN_SET();
70:         }
71:         // Minimum number of guardians to approve is at least equal or greater than half the
72:         // guardians (rounded up) and less or equal than the total number of guardians
73:         
74:         if (
75:             _minGuardians < (_newGuardians.length + 1) >> 1 ||
76:             _minGuardians > _newGuardians.length
77:         ) {
78:             revert INVALID_MIN_GUARDIANS();
79:         }
```

## [G-07] Instead of assigning guardians.length as guardianId, use i + 1 to save gas

[Link to instance](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L88)

Line 99 accesses length of storage array guardians on every iteration as it grows. Instead of doing that, use i + 1 to replicate the same behaviour since only one guardian is pushed every iteration.
```solidity
File: Guardians.sol
089:         for (uint256 i = 0; i < _newGuardians.length; ++i) {
090:             address guardian = _newGuardians[i];
091:             if (guardian == address(0)) revert INVALID_GUARDIAN();
092:             // This makes sure there are not duplicate addresses
093:             if (guardianIds[guardian] != 0) revert INVALID_GUARDIAN_SET();
094: 
095:             // Save and index the guardian
096:       
097:             
098:             guardians.push(guardian);
099:             guardianIds[guardian] = guardians.length;
100:         }
```

## [G-08] Consider removing redundant skipFeeCheck() condition

[Link to instance](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L141)

The function [skipFeeCheck()](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L219) currently returns false as hardcoded. This means that the check is redundant since we always arrive on the second condition in the check below. Consider removing the first condition to save gas.
```solidity
File: TaikoL2.sol
153:         if (!skipFeeCheck() && block.basefee != basefee) {
154:             revert L2_BASEFEE_MISMATCH();
155:         }
```

## [G-09] Remove redundant nonReentrant modifier

[Link to instance](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L107)

Reentrancy cannot occur in this function. Additionally, cross-function reentrancy cannot occur as well since function banAddress is restricted to the watchdog. 
```solidity
File: Bridge.sol
110:     function banAddress(
111:         address _addr,
112:         bool _ban
113:     )
114:         external
115:         onlyFromOwnerOrNamed("bridge_watchdog")
116:         nonReentrant 
117:     {
118:         if (addressBanned[_addr] == _ban) revert B_INVALID_STATUS();
119:         addressBanned[_addr] = _ban;
120:         emit AddressBanned(_addr, _ban);
121:     }
```

## [G-10] Consider adding refundAmount > 0 check to save gas on unnecessary sendEther() call

[Link to instance](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L299)

In the else block below, consider adding the check `refundAmount > 0` before Line 374. This will save us gas since in most cases the refundAmount would be 0 for most users. This is because refundAmount is only non-zero and assigned [here](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L275) for special addresses.
```solidity
File: Bridge.sol
368:             if (msg.sender == refundTo) {
369:                 refundTo.sendEther(_message.fee + refundAmount);
370:             } else {
371:                 // If sender is another address, reward it and refund the rest
372:                 msg.sender.sendEther(_message.fee);
373:
374:                 refundTo.sendEther(refundAmount);
375:             }
```

## [G-11] No need to explicitly set success variable to false due to default value being false

[Link to instance](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L495)

In function _invokeMessageCall(), the if block sets success_ to false in the if block if the conditions are met. This is not required since default value of bool is false.
```solidity
File: Bridge.sol
567:             success_ = false; 
```

## [G-12] Consider using if-else block instead of ternary operators

[Link to instance](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/LibMath.sol#L12)

```solidity
File: LibMath.sol
14:     function min(uint256 _a, uint256 _b) internal pure returns (uint256) {
15:         return _a > _b ? _b : _a;
16:     }
```

## [G-13] Modifier checks not required on function _verfiyHopProof()

[Link to instance](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L206)

The three modifier checks are not required below since the function is called from proveSignalReceived() [here](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L107), which already implements the checks.

```solidity
File: SignalService.sol
217:     function _verifyHopProof(
218:         uint64 _chainId,
219:         address _app,
220:         bytes32 _signal,
221:         bytes32 _value,
222:         HopProof memory _hop,
223:         address _signalService
224:     )
225:         internal
226:         virtual
227:         validSender(_app) 
228:         nonZeroValue(_signal)
229:         nonZeroValue(_value)
230:         returns (bytes32)
```

## [G-14] Cache op.token in function _handleMessage() to save gas

[Link to instance](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L249)

`op.token` is accessed multiple times in the function below. Consider caching it to save gas. 
```solidity
File: ERC1155Vault.sol
266:             if (bridgedToCanonical[_op.token].addr != address(0)) {
267:                 ctoken_ = bridgedToCanonical[_op.token];
268:                 for (uint256 i; i < _op.tokenIds.length; ++i) {
269:                  
270:                     BridgedERC1155(_op.token).burn(
271:                         _user,
272:                         _op.tokenIds[i],
273:                         _op.amounts[i]
274:                     );
275:                 }
276:             } else {
277:                 // is a ctoken token, meaning, it lives on this chain
278:                 ctoken_ = CanonicalNFT({
279:                     chainId: uint64(block.chainid),
280:                     addr: _op.token,
281:                     symbol: "",
282:                     name: ""
283:                 });
```

## [G-15] Consider using safeBatchTransferFrom() instead of running a for loop

[Link to instance](https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L270)

ERC1155 supports batch transfers. Instead of transferring each tokenId one-by-one, consider batch transferring them to save gas. 

```solidity
File: ERC1155Vault.sol
293:                 for (uint256 i; i < _op.tokenIds.length; ++i) {
294:                     IERC1155(_op.token).safeTransferFrom({
295:                         from: msg.sender,
296:                         to: address(this),
297:                         id: _op.tokenIds[i],
298:                         amount: _op.amounts[i],
299:                         data: ""
300:                     });
301:                 }
```