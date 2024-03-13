# an if statement check will never hit 

https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/bridge/Bridge.sol#L139
in sendMessage() function the "msg.value" will always be equal to "_message.value + _message.fee" 
```solidity
    // Ensure the sent value matches the expected amount.
    uint256 expectedAmount = _message.value + _message.fee;
    if (expectedAmount != msg.value) revert B_INVALID_VALUE();
```
consider checking if the "msg.value" is not equal to 0.