## 1. No need to assign zero value in else statement :-

The `meta_.txListByteOffset` is assigned zero value in line [132](https://github.com/pavankv241/2024-03-taiko-ICP/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L132) and in if statement the value get assigned but else statement again the `meta_.txListByteOffset` will be called to assign the zero value.

**Before**
```solidity
            meta_.blobHash = keccak256(_txList);
            meta_.txListByteOffset = 0;
            meta_.txListByteSize = uint24(_txList.length);

```


**After**

```solidity
	meta_.blobHash = keccak256(_txList);
            // Gas savings
            meta_.txListByteSize = uint24(_txList.length);

```

Code snippet:-
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibProposing.sol#L189C1-L191C59


## 2. Change the storage layout to save the gas of offset.

In below we can see that state array variables in between the other state variable the size of the `guardians` variables is not defined so that will keep on increasing , while calling the `version` , `minGuardians` 
Offset will also increases.

**Before**
```solidity

    /// @notice The set of guardians
    /// @dev Slot 3
    address[] public guardians;

    /// @notice The version of the guardians
    /// @dev Slot 4
    uint32 public version;

    /// @notice The minimum number of guardians required to approve
    uint32 public minGuardians;

    uint256[46] private __gap;

```

**After**
```solidity
    /// @notice The version of the guardians
    /// @dev Slot 4
    uint32 public version;

    /// @notice The minimum number of guardians required to approve
    uint32 public minGuardians;

    uint256[46] private __gap;
	
    /// @notice The set of guardians
    ///
    address[] public guardians; // @audit changed here

```

Code snippet:-
https://github.com/pavankv241/2024-03-taiko-ICP/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L21C1-L32C31


## 3. No need to access state variable in for-loop for comparison :-

Instead of that we can cache the state variable to save SLOAD opcode gas.

**Before**
```solidity
        unchecked {
            for (uint256 i; i < guardiansLength; ++i) {
                if (bits & 1 == 1) ++count;
                if (count == minGuardians) return true;
                bits >>= 1;
            }
        }

```


**After**

```solidity
	uint256 LminGuardians = minGuardians; //@audit Changed here
        unchecked {
            for (uint256 i; i < guardiansLength; ++i) {
                if (bits & 1 == 1) ++count;
                if (count == LminGuardians) return true; // @audit changed here
                bits >>= 1;
            }
        }


```


Code snippet:-
https://github.com/pavankv241/2024-03-taiko-ICP/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L132C1-L138C10

## 4. Do-while loop cost efficient that for-loop :-
If we want to push optimization at the expense of creating slightly unconventional code, Solidity do-while loops are more gas efficient than for loops

Code snippet:-
https://github.com/pavankv241/2024-03-taiko-ICP/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L132C1-L138C10
https://github.com/pavankv241/2024-03-taiko-ICP/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L80C1-L85C10


## 5.  Use inline assembly to check for address(0) :-

Writing contracts in inline assembly is generally considered gas optimized. we can manipulate memory directly and use fewer opcodes instead of leaving it to the Solidity compiler.

Code snippet :-
https://github.com/pavankv241/2024-03-taiko-ICP/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L82

## 6. We can use call data location to the arguments which doesn't modified in function :-

In below scenario we can see that `_newGuardians` which is used to comparison and assigning to the another variable no modification so `calldata` location is cost efficient than the `memory` location. 

**Before**
```solidity
    function setGuardians(
        address[] memory _newGuardians, // Gas savings can be call data
        uint8 _minGuardians
    )
```

**After**
```solidity
    function setGuardians(
        address[] calldata _newGuardians, // Gas savings can be call data
        uint8 _minGuardians
    )
```

Code snippet :-
https://github.com/pavankv241/2024-03-taiko-ICP/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L54

## 7. Constructor can payable :-
The constructor which is payable saved 200 gas on deployment. This is because non-payable functions have an implicit require(msg.value == 0) inserted in them. Additionally, fewer bytecode at deploy time mean less gas cost due to smaller calldata.


Code snippet :-
https://github.com/pavankv241/2024-03-taiko-ICP/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L54

## 8. Check effect statements should be top of the function :-

In the scenario below, the first if statement contains numerous OR operators, implying that it must evaluate each parameter sequentially until it finds a true statement. Instead of this, we can refactor it by adding a second if statement at the top. This is because the second if statement involves checking a constant variable GOLDEN_TOUCH_ADDRESS and a global variable msg.sender.

**Before**
```solidity

    function anchor(
        bytes32 _l1BlockHash,
        bytes32 _l1StateRoot,
        uint64 _l1BlockId,
        uint32 _parentGasUsed
    )
        external
        nonReentrant
    {
        if (
            _l1BlockHash == 0 || _l1StateRoot == 0 || _l1BlockId == 0
                || (block.number != 1 && _parentGasUsed == 0)
        ) {
            revert L2_INVALID_PARAM();
        }

        if (msg.sender != GOLDEN_TOUCH_ADDRESS) revert L2_INVALID_SENDER();


```

**After**
```solidity

    function anchor(
        bytes32 _l1BlockHash,
        bytes32 _l1StateRoot,
        uint64 _l1BlockId,
        uint32 _parentGasUsed
    )
        external
        nonReentrant
    {
        

        if (msg.sender != GOLDEN_TOUCH_ADDRESS) revert L2_INVALID_SENDER(); //@audit check here

	if (
            _l1BlockHash == 0 || _l1StateRoot == 0 || _l1BlockId == 0
                || (block.number != 1 && _parentGasUsed == 0)
        ) {
            revert L2_INVALID_PARAM();
        }


```

Code snippet:-

https://github.com/pavankv241/2024-03-taiko-ICP/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L116C1-L123C76


## 9. `SLOAD` opcode gas can be saved by caching the state variables in memory :-

In below scenario we can see that `lastSyncedBlock` state variables is called 3 times to comparison and subtraction. It can refactor to save gas by cache the state variable in memory variable and it can utilised
to comparison and subtraction.

**Beofore**
```solidity
            uint256 numL1Blocks;
            if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {
                numL1Blocks = _l1BlockId - lastSyncedBlock;
            }


```

**After**
```solidity

            uint256 numL1Blocks;
	    uint64 LlastSyncedBlock = lastSyncedBlock; // Gas savings
            if (LlastSyncedBlock > 0 && _l1BlockId > LlastSyncedBlock) {
                numL1Blocks = _l1BlockId - LlastSyncedBlock; //@audit Gas savings

            }


```

Code snippet :-
https://github.com/pavankv241/2024-03-taiko-ICP/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L279C1-L282C14


**Scenario 2**

In this scenario we can save the state variable address in local memory to save gas 

**Before**
```solidity
           emit MigratedTo(migratingAddress, _account, _amount);
            // Ask the new bridged token to mint token for the user.
            IBridgedERC20(migratingAddress).mint(_account, _amount);

```
**After**
```solidity
	   address LocalMigra = migratingAddress;
           emit MigratedTo(LocalMigra, _account, _amount); // Gas savings
            // Ask the new bridged token to mint token for the user.
            IBridgedERC20(LocalMigra).mint(_account, _amount); // Gas savings


```

Code snippet:-
https://github.com/pavankv241/2024-03-taiko-ICP/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L80C1-L82C69

## 10. Refactor the for-loop in order to save gas :-

Optimization can be achieved by caching the nextInstanceId state variable outside the for-loop. Subsequently, after the operation, assign the local variable to the global state variable to reduce gas consumption. Accessing the state variable within each loop iteration results in increased gas consumption. Therefore, by minimizing state variable access within the loop, gas costs can be reduced effectively.

**Before**
```solidity
        for (uint256 i; i < _instances.length; ++i) {
            if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();

            addressRegistered[_instances[i]] = true;

            if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();

            instances[nextInstanceId] = Instance(_instances[i], validSince);
            ids[i] = nextInstanceId;

            emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);

            nextInstanceId++;
        }

```

**After**
```solidity

	uint256 LnextInstanceId = nextInstanceId;
        for (uint256 i; i < _instances.length; ++i) {
            if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();

            addressRegistered[_instances[i]] = true;

            if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();

            instances[LnextInstanceId] = Instance(_instances[i], validSince);
            ids[i] = LnextInstanceId;

            emit InstanceAdded(LnextInstanceId, _instances[i], address(0), validSince);

            LnextInstanceId++;
        }
	nextInstanceId = LnextInstanceId;


```

Code snippet:-
https://github.com/pavankv241/2024-03-taiko-ICP/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210C1-L223C10

**Note**
Our gas optimisation doesn't cause any test fails 
