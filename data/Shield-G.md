# Gas Optimisations

## G-01 Don't send ether when the value is zero

## Line of code

https://github.com/code-423n4/2024-03-taiko/blob/a30b5b6afd121e4de8ceff7165a2091e62194992/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L271

The user doesn't always send value

Hence not calling the function in this case can save about 2.6K (if to is cold, which seems likely to be the case)

## G-02 Secondary check in if condition can be avoided

## Line of code

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L316

`if proposer == address(0)` is true then no need to check the 2nd condition hence either the 2nd condition should be checked first or the 2nd check `msg.sender == proposer` should be avoided if 1st condition is true

## G-03 Remove uncessary addition in if condition to save gas

## Line of code

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L98
```
        if (b.numBlocks >= b.lastVerifiedBlockId + _config.blockMaxProposals + 1) {
            revert L1_TOO_MANY_BLOCKS();
        }
```
Can be updated by omitting the + 1 to save gas
```
        if (b.numBlocks > b.lastVerifiedBlockId + _config.blockMaxProposals) {
            revert L1_TOO_MANY_BLOCKS();
        }
```

## G-04 Missing Unchecked block can help save gas

## Line of code

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L185

The expression can be wrapped in a unchecked block to save gas as there is no chance of underflow
```
                if (ts.prover != blk.assignedProver) { 
                    bondToReturn -= blk.livenessBond >> 1; 
                }
```

## G-05 if condition in `ERC20Airdrop2.getBalance` can be updated to save gas

## Line of code

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L114

It is recommended to update the check in the `ERC20Airdrop2.getBalance` function as shown below to save gas as this method is called by the `withdraw` method


`if (block.timestamp <= claimEnd) return (balance, 0);`

