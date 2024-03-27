## Summary

### Gas Optimization

no | Issue |Instances||
|-|:-|:-:|:-:|
| [G-01] |  Use assembly to check for `address(0)` | 6 | 
| [G-02] |  `abi.encode()` is less efficient than  `abi.encodepacked()` | 4 | 
| [G-03] | Use assembly to validate msg.sender | more than 1 | 
| [G-04] | State varaibles only set in the Constructor should be declared `Immutable` | 1 | 
| [G-05] | Do not calculate constant | 1 | 
| [G-06] | Use assembly to emit events | 3 | 
| [G-07] | Use assembly to calculate hashes to save gas | 4 | 
| [G-08] | Use hardcode address instead address(this) | 2 |
| [G-09] |  `require()` Should Be Used Instead Of `assert()` | 1 | 
| [G-10] | Expressions for constant values such as a call to keccak256(), should use immutable rather than constant | 1 | - |

## Gas Optimizations  


## [G-01] Use assembly to check for `address(0)`

```solidity
file: /contracts/common/AddressResolver.sol

81        if (addressManager == address(0)) revert RESOLVER_INVALID_MANAGER();

85        if (!_allowZeroAddress && addr_ == address(0)) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L81C1-L81C77


```solidity
file: /contracts/common/EssentialContract.so

105        if (_addressManager == address(0)) revert ZERO_ADDR_MANAGER();

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L105C1-L105C71


```solidity
file: /contracts/libs/LibAddress.sol

24        if (_to == address(0)) revert ETH_TRANSFER_FAILED();

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/LibAddress.sol#L24C1-L24C61


```solidity
file: /contracts/L1/hooks/AssignmentHook.sol

120        if (input.tip != 0 && block.coinbase != address(0)) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L120C1-L120C62


```solidity
file: /contracts/L1/libs/LibProving.sol

163            if (verifier != address(0)) {

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L163C1-L163C42



## [G-02] `abi.encode()` is less efficient than  `abi.encodepacked()`

In terms of efficiency, abi.encodePacked() is generally considered to be more gas-efficient than abi.encode(), because it skips the step of adding function signatures and other metadata to the encoded data. However, this comes at the cost of reduced safety, as abi.encodePacked() does not perform any type checking or padding of data.

```solidity
file: /contracts/automata-attestation/utils/SigVerifyLib.sol

136        bytes memory args = abi.encode(sha256(tbs), r, s, gx, gy);


```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L136


```solidity
file: /contracts/bridge/Bridge.sol
 
450        return keccak256(abi.encode("TAIKO_MESSAGE", _message));


```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L450


```solidity
file: /contracts/L1/provers/GuardianProver.sol

46        bytes32 hash = keccak256(abi.encode(_meta, _tran));

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/GuardianProver.sol#L46


```solidity
file: /contracts/team/airdrop/ERC20Airdrop2.sol

80        _verifyClaim(abi.encode(user, amount), proof);


```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L80


## [G-03]  Use assembly to validate msg.sender

We can use assembly to efficiently validate msg.sender for the didPay and uniswapV3SwapCallback functions with the least amount of opcodes necessary. Additionally, we can use xor() instead of iszero(eq()), saving 3 gas. We can also potentially save gas on the unhappy path by using scratch space to store the error selector, potentially avoiding memory expansion costs.


```solidity
file: /contracts/bridge/Bridge.sol

294            if (msg.sender == refundTo) {


```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#294



## [G-04]  State varaibles only set in the Constructor should be declared `Immutable`

```solidity
file: /contracts/automata-attestation/utils/SigVerifyLib.sol

18    address private ES256VERIFIER;

    constructor(address es256Verifier) {
        ES256VERIFIER = es256Verifier;
    }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L18



## [G-05] Do not calculate constant

When you define a constant in Solidity, the compiler can calculate its value at compile-time and replace all references to the constant with its computed value. This can be helpful for readability and reducing the size of the compiled code, but it can also increase gas usage at runtime.

```solidity
file: contracts/L1/libs/LibProposing.sol

21    uint256 public constant MAX_BYTES_PER_BLOB = 4096 * 32;


```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L21


## [G-06] Use assembly to emit events

We can use assembly to emit events efficiently by utilizing scratch space and the free memory pointer. This will allow us to potentially avoid memory expansion costs. Note: In order to do this optimization safely, we will need to cache and restore the free memory pointer.

```solidity
file: /contracts/common/AddressManager.sol

50        emit AddressSet(_chainId, _name, _newAddress, oldAddress);


```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressManager.sol#L50


```solidity
file: /contracts/common/EssentialContract.sol

80        emit Unpaused(msg.sender);


```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L80


```solidity
file: /contracts/L1/hooks/AssignmentHook.sol

129        emit BlockAssigned(_blk.assignedProver, _meta, assignment);


```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L129



## [G-07] Use assembly to calculate hashes to save gas

Using assembly to calculate hashes can save 80 gas per instance

```solidity
file: /contracts/automata-attestation/AutomataDcapV3Attestation.sol

292            bytes32 issuerPubKeyHash = keccak256(issuer.pubKey);


```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L292


```solidity
file: /contracts/L1/libs/LibProposing.sol

189            meta_.blobHash = keccak256(_txList);
            meta_.txListByteOffset = 0;
            meta_.txListByteSize = uint24(_txList.length);
        }

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L189


```solidity
file: /contracts/signal/SignalService.so

186        return keccak256(abi.encode(_chainId, _kind, _blockId));


```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L186



## [G-08]  Use hardcode address instead address(this)

```solidity
file: /contracts/bridge/Bridge.sol

174            if (!ISignalService(signalService).isSignalSent(address(this), msgHash)) {


```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L174


```solidity
file: /contracts/L1/libs/LibProposing.sol

253                IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }(


```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L253



## [G-09] `require()` Should Be Used Instead Of `assert()`

```solidity
file: /contracts/bridge/Bridge.sol

486        assert(_message.from != address(this));


```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L486


## [G-10] Expressions for constant values such as a call to keccak256(), should use immutable rather than constant


While it doesn't save any gas because the compiler knows that developers often make this mistake, it's still best to use theright tool for the task at hand. There is a difference between constant variables and immutable variables, and they shouldeach be used in their appropriate contexts. constants should be used for literal values written into the code, and immutablevariables should be used for expressions, or values calculated in, or passed into the constructor. 

```solidity
file:

20    bytes32 public constant RETURN_LIVENESS_BOND = keccak256("RETURN_LIVENESS_BOND");

23    bytes32 public constant TIER_OP = bytes32("tier_optimistic");

```
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L20


