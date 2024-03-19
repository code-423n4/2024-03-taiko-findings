# Transient storage in EssentialContract should target base chain instead of chain id = 1

https://github.com/code-423n4/2024-03-taiko/blob/b6885955903c4ec6a0d72ebb79b124c6d0a1002b/packages/protocol/contracts/common/EssentialContract.sol#L120-L123

https://github.com/code-423n4/2024-03-taiko/blob/b6885955903c4ec6a0d72ebb79b124c6d0a1002b/packages/protocol/contracts/common/EssentialContract.sol#L131-L134

`TaikoL1` can be deployed on L2 as a base contract for L3. Hence when the reentrancy lock is loaded using transient storage, it should compare chain id of base chain, instead of chain id = 1.

For example
```solidity
        if (block.chainid == BASE_CHAIN_ID) {
            assembly {
                tstore(_REENTRY_SLOT, _reentry)
            }
        }
```

This `BASE_CHAIN_ID` can be initialized as an immutable variable.

# Cross chain signature replay attack
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L170-L171

Same signature can be used to claim grants on multiple chain, if the contract is deployed on multiple chains. It is recommend to hash chain id and address of the contract.

```solidity
        bytes32 hash = keccak256(abi.encodePacked("Withdraw unlocked Taiko token to: ", _to, block.chainid, address(this)));

```