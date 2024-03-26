### [Gas-0]
```
```
```
```

### [Gas-0]
```
```
```
```

### [Gas-0]
```
```
```
```

### [Gas-0]
```
```
```
```

### [Gas-0]
```
```
```
```

### [Gas-0]
```
```
```
```

### [Gas-0]
```
```
```
```

### [Gas-0]
```
```
```
```

### [Gas-0]
```
```
```
```

### [Gas-01] Stack variable is only used once
```
```
```
```

### [Gas-02] Use assembly for Efficient Event Emission
```
```
```
```



### [Gas-03] Assembly: Check msg.sender using xor and the scratch space
```
```
```
```

### [Gas-04] Assembly: Use scratch space when building emitted events with two data arguments
```
```
```
```

### [Gas-05] Use assembly to write mutable storage values
```
```
```
```

### [Gas-06] Avoid Zero to Non-Zero Storage Writes Where Possible
```
```
```
```

### [Gas-07] Use unchecked for division which do not divide by -X sonce they can't overflow
```
```
```
```

### [Gas-08] Use unchecked for %
```
```
```
```

### [Gas-09] abi.encodePacked is more gas efficient than abi.encode
```
```
```
```
### [Gas-10] Multiple address/ID mappings can be combined into a single mapping of an address/ID to a struct
```
```
```
```


### [Gas-11] Use solady library where possible to save gas
```
```
```
```

### [Gas-12] Cache multiple accesses of mapping/array values
```
```
```
```

### [Gas-13] Cache state variables accessed multiple times in the same function
```
```
```
```

### [Gas-14] Mappings are cheaper to use than storage arrays
```
```
```
```

### [Gas-15] Nesting if-statements is cheaper than using &&
```
```
```
```

### [Gas-16] Redundant state variable getters
```
```
```
```


### [Gas-17] Redundant type conversion
```
```
```
```

### [Gas-18] Replace OpenZeppelin components with Solady equivalents to save gas
```
```
```
```

### [Gas-19] Simple checks for zero can be done using assembly to save gas
```
```
```
```



### [Gas-20] The result of function calls should be cached rather than re-calling the function
```
```
```
```
### [Gas-21] Use calldata instead of memory for function arguments that are read only
```
```
```
```



### [Gas-0]
```
```
```
```

### [Gas-0]
```
```
```
```

### [Gas-0]
```
```
```
```

### [Gas-22] Assembly: Use scratch space for calculating small keccak256 hashes
```
```
```
```

### [Gas-23] Assembly: Use scratch space when building emitted events with two data arguments
```
```
```
```

### [Gas-24] Common Calculation could be hardcoded in a `constant` state variable.
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

### [Gas-0]
```
```
```
```

### [Gas-0]
```
```
```
```

### [Gas-0]
```
```
```
```

### [Gas-0]
```
```
```
```

### [Gas-0]
```
```
```
```

### [Gas-0]
```
```
```
```

### [Gas-0]
```
```
```
```

### [Gas-0]
```
```
```
```

### [Gas-0]
```
```
```
```

### [Gas-0]
```
```
```
```

### [Gas-0]
```
```
```
```

### [Gas-0]
```
```
```
```






### [Gas-25] Use assembly to check for address(0)
```
```
```
```

### [Gas-26] Optimize Gas by Using Only Named Returns
```
```
```
```

### [Gas-27] Simple checks for zero uint can be done using assembly to save gas
```
```
```
```

### [Gas-28] Use Assembly for Efficient Memory Management in Multiple External Calls
```
```
```
```

### [Gas-29] Use Assembly for Hash Calculations
```
```
```
```

### [Gas-30] Use unchecked for Math Operations if they already checked
```
```
```
```

### [Gas-31] Avoid transferring amounts of zero in order to save gas
```
```
```
```

### [Gas-32] Reduce deployment costs by tweaking contracts' metadata
```
```
```
```

### [Gas-33] Constructors can be marked payable
```
```
```
```

### [Gas-34] Use unchecked for Non-Loop Increment/Decrement Operations
```
```
```
```

### [Gas-35] Call msg.sender directly instead of caching it
```
```
```
```

### [Gas-36] Consider pre-calculating the address of address(this) to save gas
```
```
```
```


### [Gas-37] Use more recent OpenZeppelin version for gas boost
```
```
```
```

### [Gas-38] Enable IR-based code generation
```
```
```
```

### [Gas-39] Avoid updating storage when the value hasn't changed
```
```
```
```

### [Gas-40] Optimize External Calls with Assembly for Memory Efficiency
```
```
```
```

### [Gas-41] Use named return parameters
```
```
```
```

### [Gas-42] Optimize names to save gas
```
```
```
```

### [Gas-43] Inline modifiers that are only used once, to save gas
```
```
```
```

### [Gas-44] Inline internal functions that are only called once
```
```
```
```

### [Gas-0]
```
```
```
```

### [Gas-0]
```
```
```
```

### [Gas-0]
```
```
```
```

### [Gas-0]
```
```
```
```

### [Gas-0]
```
```
```
```

### [Gas-45] `0` trasfer amount check before token transfer
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

### [Gas-46] Instead of `block.number - 1` calculation directly 0 could used as here `block.number == 1`
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

### [Gas-47] PreIncreament (++i) costs less than PostIncrement(i++)
```
```
```
```

### [Gas-48] Some state variable could be `private` rather than `public`
```
```
```
```