# Quality assurance report

## Summary

| Issue Number | Issue Title                                           | Number of Instances |
|--------------|-------------------------------------------------------|---------------------|
| L-01         | Functions should have only one functionality           | 3                   |
| L-02         | Explain assembly code                                  | 2                   |
| L-03         | Avoid on-chain computation                            | 3                   |
| L-04         | Check if state exists before removing                 | 1                   |
| L-05         | Revert instead of returning zero                      | 1                   |
| L-06         | Function will always return false                     | 1                   |
| L-07         | Check if `_addr` exists before performing actions     | 2                   |
| L-08         | Validate cost token                                   | 1                   |
| L-09         | Require `msg.value` to equal `amount`                 | 1                   |
| L-10         | Check if token is blacklisted                         | 2                   |
| NC-01        | Use an un-initialized placeholder variable            | 1                   |
| NC-02        | Functions should emit an event                        | 2                   |
| NC-03        | Pass variables in error messages                      | 3                   |
| NC-04        | Perform checks before calling private functions        | 1                   |
| NC-05        | Initializer should emit an event                      | 1                   |
| NC-06        | Avoid hardcoded string and store in a variable         | 2                   |
| NC-07        | Rename event from `tokenRecieved` to `tokenTransferred`| 1                   |



## [L-01] Functions should have only one functionality
It is more advised to apply separation of concerns principle on functions by making them only have one functionality and not to mix things up, `banAddress` should only ban users and `unBanAddress` should only un-ban users
### Instances
* [Bridge.sol#101](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L101)
```solidity
    /// @notice Ban or unban an address. A banned addresses will not be invoked upon
    function banAddress(
        address _addr,
        bool _ban
    )
    
```

* [LibProving.sol#73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L73)
```solidity
function pauseProving(TaikoData.State storage _state, bool _pause)
    
```
* [SignalService.sol#L56](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L56C1-L60C6)
```solidity
    /// @dev Authorize or deauthorize an address for calling syncChainData.
    function authorize(address _addr, bool _authorize
    
```
## [L-02] Explain assembly code
### Instances
* [Bridge.sol#543](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L543C13-L547C14)
```solidity
    assembly {
                tstore(_CTX_SLOT, _msgHash)
                tstore(add(_CTX_SLOT, 1), _from)
                tstore(add(_CTX_SLOT, 2), _srcChainId)
            }
```
* [Bridge.sol#560](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L560C1-L564C14)
```solidity
            assembly {
                msgHash := tload(_CTX_SLOT)
                from := tload(add(_CTX_SLOT, 1))
                srcChainId := tload(add(_CTX_SLOT, 2))
            }
```
## [L-03] Avoid on-chain computation
### Instances
* [LibProposing.sol#21](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L21)
```solidity
    uint256 public constant MAX_BYTES_PER_BLOB = 4096 * 32;

```
* [LibVerifying.sol#L251](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L251)
```solidity
                || _config.blockMaxTxListBytes > 128 * 1024 // calldata up to 128K

```

* [TaikoL2.sol#L213](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L213)
```solidity
        config_.gasTargetPerL1Block = 15 * 1e6 * 4;

```

## [L-04] Check if state exists before removing
### Instances
* [LibProving.sol#L73](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L73C1-L81C6)
```solidity
    function pauseProving(TaikoData.State storage _state, bool _pause) external {
        if (_state.slotB.provingPaused == _pause) revert L1_INVALID_PAUSE_STATUS();
        _state.slotB.provingPaused = _pause;

        if (!_pause) {
            _state.slotB.lastUnpausedAt = uint64(block.timestamp);
        }
        emit ProvingPaused(_pause);
    }
```

## [L-05] It is more advised to revert instead returning zero
### Instances
* [TaikoL2.sol#L201](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L201)
```solidity
        if (_blockId >= block.number) return 0;

```

## [L-06] Function will always return false
### Instances
* [TaikoL2.sol#L219](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L219)
```solidity
    function skipFeeCheck() public pure virtual returns (bool) {
        return false;
    }
```

## [L-07] Check if `_addr` exists before peroforming actions
### Instances
* [SignalService.sol#L57](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L57)
```solidity
        if (isAuthorized[_addr] == _authorize) revert SS_INVALID_STATE();

```
* [TimelockTokenPool.sol#L151](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L151)
```solidity
        Recipient storage r = recipients[_recipient];

```


## [L-08] Validate cost token
More checks and validation should be applied on the cost token before deploying, for example cost token should be the same as taiko token, and if the passed cost token is allowed by the protocol or not
### Instances
* [TimelockTokenPool.sol#L124](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L124)
```solidity
        if (_costToken == address(0)) revert INVALID_PARAM();

```
## [L-09] require `msg.value` to equal `amount`
### Instances
* [ERC20Vault.sol#L218](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L218C1-L219C71)
```solidity
        (bytes memory data, CanonicalERC20 memory ctoken, uint256 balanceChange) =
            _handleMessage(msg.sender, _op.token, _op.to, _op.amount);

```
## [L-10] Check if token is blacklisted
### Instances
* [ERC20Vault.sol#L407](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L407)
```solidity
function _deployBridgedToken(CanonicalERC20 memory ctoken)  
```
* [ERC1155Vault.sol#L145](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L145)
```solidity
        address token = _transferTokens(ctoken, message.srcOwner, tokenIds, amounts);
```


## [NC-01] It is more advised to use an un-initialized placeholder variable
Instead of initializing variables with zero values and using address zero for variables that to be initialized later, use a placeholder variable that is marked as uninitialized.
### Instances
* [LibProposing.sol#123](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L123)
```solidity
        difficulty: 0, // to be initialized below
        blobHash: 0, // to be initialized below
```
## [NC-02] Functions should emit an event
### Instances
* [LibProposing.sol#260](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L260C1-L262C14)
```solidity
            if (address(this).balance != 0) {
                msg.sender.sendEther(address(this).balance);
                //@audit emit an transfer event
            }
```
* [TaikoL2.sol#L71](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L71C2-L71C5)
```solidity
    function init(
        address _owner,
        address _addressManager,
        uint64 _l1ChainId,
        uint64 _gasExcess
    )
```

## [NC-03] Pass variables in error messages
### Instances
* [TaikoL2.sol#L93](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L93)
```solidity
            revert L2_TOO_LATE();

```

* [TaikoL2.sol#L142](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L142)
```solidity
            revert L2_BASEFEE_MISMATCH();

```
* [SignalService.sol#L36](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L36)
```solidity
        if (_app == address(0)) revert SS_INVALID_SENDER();

```
* [SignalService.sol#L41](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L41)
```solidity
        if (_input == 0) revert SS_INVALID_VALUE();

```







## [NC-04] More recommended to perform checks before calling private functions
Checks for and validation for input and addresses are more advised to be done in the public functions before calling private functions
### Instances
* [SignalService.sol#L253](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L253)
```solidity
function _sendSignal(
        address _app,
        bytes32 _signal,
        bytes32 _value
    )
        private
        // @audit unnecessary check, sender is either msg.snder or the address of this contract, since  this function is private,
        // then in the future validate the input in the public function that will call it
        validSender(_app)
        nonZeroValue(_signal)
        nonZeroValue(_value)
        returns (bytes32 slot_)
```



## [NC-05] Initializer should emit an event
### Instances
* [TimelockTokenPool.sol#L111](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L111)
```solidity
    function init(
        address _owner,
        address _taikoToken,
        address _costToken,
        address _sharedVault
    )
```




## [NC-06] Avoid hardcoded string and store in a variable instead
### Instances
* [ERC20Vault.sol#L317](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L317)
```solidity
        return "erc20_vault";

```
* [ERC721Vault.sol#L157](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L157)
```solidity
        return "erc721_vault";

```


## [NC-07] Rename event from `tokenRecieved` to `tokenTransferred`
### Instances
* [ERC1155Vault.sol#L114](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L114)
```solidity
emit TokenReceived({
            msgHash: ctx.msgHash,
            from: from,
            to: to,
            srcChainId: ctx.srcChainId,
            ctoken: ctoken.addr,
            token: token,
            tokenIds: tokenIds,
            amounts: amounts
        });
```