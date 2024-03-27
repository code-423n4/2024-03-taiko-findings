# Quality Assuarance

## L-01 Discrepancy between documentation and logic implementation wrt BLOCK_SYNC_THRESHOLD

# Lines of code
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L145-L152

### Impact
BLOCK_SYNC_THRESHOLD has the following natspec comment:

`@notice The number of L2 blocks to wait before syncing L1 block details`

But the issue here is that, it mentions number of L2 blocks. But there is no need to add number of L2 blocks on the L1 block height because the block durations are different in two chains. Hence the natspec comments should be corrected as number of L1 blocks

### Tools Used
Manual review

### Recommended Mitigation Steps
Update the natspec comment for better clarity

## L-02 Renundant check for validityBond for top tier proof

# Lines of code

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L223

### Impact
There is a existing top tier check [here](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L186) & a validity bond check [here](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L224) so the check on line 223 should be removed

### Tools Used
Manual review

### Recommended Mitigation Steps
remove the renundant check

## L-03 Wrong max prover fee value declared as a constant 

# Lines of code

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L38

### Impact
During external calls only 63/64 of the total gas limit is available hence the tx will revert if more than 63/64th of the total gas is used i.e 49219 gas in this case

### Tools Used
Manual review

### Recommended Mitigation Steps
either update the comment on line 37 or update the max value to 49219

## L-04 Lack of information around reward calculation in a scenario where the new prover is also the contestor and no previous contestor exists 

# Lines of code

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProving.sol#L376

### Impact
there is no information regarding the reward calculation mentioned [here](https://taiko.mirror.xyz/Z4I5ZhreGkyfdaL5I9P0Rj0DNX4zaWFmcws-0CVMJ2A) where the new prover is also the contestor and no previous contestor exists


### Tools Used
Manual review

### Recommended Mitigation Steps
add information regarding this scenario in comments for more clarity

## L-05 data length check in onMessageInvocation can be skipped

# Lines of code

https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L491

### Impact
In case of a fallback method there is no `msg.data` involved hence the if check can be by passed whereas it should be handled there in case of a contract


### Tools Used
Manual review

### Recommended Mitigation Steps
update this check to handle the fallback scenario
```
        if (
            _message.data.length >= 4 // msg can be empty
                && bytes4(_message.data) != IMessageInvocable.onMessageInvocation.selector
                && _message.to.isContract()
        )
``` 
to

```
        if (
            _message.data.length >= 4 // msg can be empty
                || (bytes4(_message.data) != IMessageInvocable.onMessageInvocation.selector
                && _message.to.isContract())
        )
```


## L-06 ERC1155Vault.supportsInterface function does not indicate support for IMessageInvocable interface
 

# Lines of code

https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L192

### Impact
The ERC1155Vault.supportsInterface indicates that it implements the following interfaces :
```
ERC1155ReceiverUpgradeable
IRecallableSender
```

But the ERC1155Vault implements the IMessageInvocable interface and it is not referred in the ERC1155Vault.supportsInterface function.


### Tools Used
Manual review

### Recommended Mitigation Steps
update the BaseVault.supportsInterface function as shown below:
```
function supportsInterface(bytes4 _interfaceId) public view virtual override returns (bool) {
        return _interfaceId == type(IRecallableSender).interfaceId || _interfaceId == type(IMessageInvocable).interfaceId;
}
```

## L-07 No recovery logic implementation in the bridge contract to recover the ERC20, ERC721, ERC1155 tokens mistakenly sent to it.
 

# Lines of code

https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L115

### Impact
The bridge contract allows the native eth transfer by directly calling the `bridge.sendMessage` function. 

But for transfer of ERC20, ERC721 and ERC1155 the vaults should be used and the transaction should initiate from the sendToken function of the respective vault.

But a user might erroneously call the bridge.sendMessage direclty to bridge ERC20, ERC721 or ERC1155 tokens by directly transaferring to the bridge contract. 

There is no recovery function to recover these tokens from the bridge


### Tools Used
Manual review

### Recommended Mitigation Steps
have a fund recovery mechanism in the bridge contract


## L-08 Renundant data conversion in BridgedERC721.tokenURI
 

# Lines of code

https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L110

### Impact
In `BridgedERC721.tokenURI` the method `LibBridgedToken.buildURI` is called which also returns a string value hence there is no need to use `abi.encodePacked` and cast it to string again
`

### Tools Used
Manual review

### Recommended Mitigation Steps
remove the unecessary string casting in `tokenURI`


## L-09 Logic implementation does not match the natspec comments
 

# Lines of code

https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L266

### Impact
In the ERC20Vault.onMessageInvocation function there is a discrepency beween the natspec comments and the logic implementation.

```
//Don't send the tokens back to from because from is on the source chain.

if (to == address(0) || to == address(this)) revert VAULT_INVALID_TO();
```

Above natspec comments states that from address should not be allowed. 

Hence the check should be updated

### Tools Used
Manual review

### Recommended Mitigation Steps
Update the check to 
```
if (to == address(0) || to == address(this) || to == from) revert VAULT_INVALID_TO();
```

## L-10 No implementation of _authorizeUpgrade in terms of the UUPS upgrade mechanism
 

# Lines of code

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L114

### Impact
In `EssentialContract` UUPS upgrade mechanism is used but `_authorizeUpgrade` is not implemented then what is the point of using UUPS upgrade  if there is no upgrade mechanism


### Tools Used
Manual review

### Recommended Mitigation Steps
Add implementation for `_authorizeUpgrade`

## L-11 Missing override for renounceOwnership
 

# Lines of code

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L109-L112

### Impact
The EssentialContract is an abstract contract which inherits from the Ownable2StepUpgradeable contract. 

There are multiple contracts which implements the EssentialContract contract by inheriting it. 

The Owner of the each of the child contracts is set during the initialization and is never allowed to be set to `address(0)`` as per the following logic implementation of `_transferOwnership`

Hence it is recommended to override the renounceOwnership function to revert if called such that the ownership is not set to address(0) by mistake or by a malicious current owner


### Tools Used
Manual review

### Recommended Mitigation Steps
override the `renounceOwnership` function to revert if new owner is `address(0)`