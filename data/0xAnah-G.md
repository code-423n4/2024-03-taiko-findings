#   TAIKO GAS OPTIMIZATIONS


## INTRODUCTION
Highlighted below are optimizations exclusively targeting state-mutating functions and view/pure functions invoked by state-mutating functions. In the discussion that follows, only runtime gas is emphasized, given its inevitable dominance over deployment gas costs throughout the protocol's lifetime. 

Please be aware that some code snippets may be shortened to conserve space, and certain code snippets may include @audit tags in comments to facilitate issue explanations."



## [G-01] Refactor the following functions to avoid reading from or writing to storage on every iteration of a loop
Cache state variables outside of loop to avoid 
Reading from storage should always try to be avoided within loops. In the following instances, we are able to cache state variables outside of the loop to save a Gwarmaccess (100 gas) per loop iteration.

### Instances
1. #### A loop in `Guardians.setGuardians()` could be refactored to make the function cheaper
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L80-#L89

Prior to the for loop between [line 80 and 89](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L80-#L89) the array of guardians was cleared therefore guardians.length is 0. Since we know this having to call guardians.length (which involves reading from state) to determine a guardian's id  after adding a guardian to the guardians array is gas inefficient since we can easily calculate the length of the guardians array by just adding 1 to the loop's index (i). Applying this change to the code would help avoid having to read guardians.length from state (which cost 1 `SLOAD` Gcoldaccess 100 gas units) and replace it with simple stack arithmetic (which cost 6 gas units). The code should be refactored as shown in the diff below:

```solidity
file: contracts/L1/provers/Guardians.sol

53:    function setGuardians(
54:        address[] memory _newGuardians,
55:        uint8 _minGuardians
56:    )
57:        external
58:        onlyOwner
59:        nonReentrant
60:    {
.
.
.
77:         delete guardians;
78:
79:        // Set the new guardians
80:        for (uint256 i = 0; i < _newGuardians.length; ++i) {
81:            address guardian = _newGuardians[i];
82:            if (guardian == address(0)) revert INVALID_GUARDIAN();
83:            // This makes sure there are not duplicate addresses
84:            if (guardianIds[guardian] != 0) revert INVALID_GUARDIAN_SET();
85:
86:            // Save and index the guardian
87:            guardians.push(guardian);
88:            guardianIds[guardian] = guardians.length;
89:        }
.
.
.
96:    }
```

```diff
diff --git a/packages/protocol/contracts/L1/provers/Guardians.sol b/packages/protocol/contracts/L1/provers/Guardians.sol
index a4daa55..c4e0e9f 100644
--- a/packages/protocol/contracts/L1/provers/Guardians.sol
+++ b/packages/protocol/contracts/L1/provers/Guardians.sol
@@ -85,7 +85,7 @@ abstract contract Guardians is EssentialContract {

             // Save and index the guardian
             guardians.push(guardian);
-            guardianIds[guardian] = guardians.length;
+            guardianIds[guardian] = 1 + i;
         }

         // Bump the version so previous approvals get invalidated
```
```
Estimated gas saved: 94 gas units per loop iteration
```

2. #### The loop in `Guardians.setGuardians()` could be refactored to make the function cheaper
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L133-#L137

The loop in `Guardians.setGuardians()` reads the `minGuardians` state variable for every of its iteration which is highly gas inefficient rather the state variable should be cached in a stack variable the the stack variable be used in the loop. In implementing it this way we would save an around `97` gas units for every iteration of the loop. The diff below shows how the code should be refactored:

```solidity
file: contracts/L1/provers/Guardians.sol

128:    function isApproved(uint256 _approvalBits) internal view returns (bool) {
129:        uint256 count;
130:        uint256 bits = _approvalBits;
131:        uint256 guardiansLength = guardians.length;
132:        unchecked {
133:            for (uint256 i; i < guardiansLength; ++i) {
134:                if (bits & 1 == 1) ++count;
135:                if (count == minGuardians) return true;
136:                bits >>= 1;
137:            }
138:        }
139:        return false;
140:    }
```

```diff
diff --git a/packages/protocol/contracts/L1/provers/Guardians.sol b/packages/protocol/contracts/L1/provers/Guardians.sol
index a4daa55..c7528bb 100644
--- a/packages/protocol/contracts/L1/provers/Guardians.sol
+++ b/packages/protocol/contracts/L1/provers/Guardians.sol
@@ -129,10 +129,11 @@ abstract contract Guardians is EssentialContract {
         uint256 count;
         uint256 bits = _approvalBits;
         uint256 guardiansLength = guardians.length;
+        uint256 _minGuardians = minGuardians;
         unchecked {
             for (uint256 i; i < guardiansLength; ++i) {
                 if (bits & 1 == 1) ++count;
-                if (count == minGuardians) return true;
+                if (count == _minGuardians) return true;
                 bits >>= 1;
             }
         }
```

```
Estimated gas saved: 97 gas units per iteration
```

3. #### The loop in `SgxVerifier._addInstances()` could be refactored to make the function cheaper
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L210-#L223

The loop in the `SgxVerifier._addInstances()` function reads the state variable `nextInstanceId` four times which is highly gas inefficient. We could make this loop and by extension the function less gas consuming by caching the `nextInstanceId` state variable into a stack variable then use the stack variable in-place of the state variable for subsequent reads. The code could be refactored as shown in the diff below;

```solidity
file: contracts/verifiers/SgxVerifier.sol

195:    function _addInstances(
196:        address[] memory _instances,
197:        bool instantValid
198:    )
199:        private
200:        returns (uint256[] memory ids)
201:    {
.
.
.
210:        for (uint256 i; i < _instances.length; ++i) {
211:            if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();
212:
213:            addressRegistered[_instances[i]] = true;
214:
215:            if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();
216:
217:            instances[nextInstanceId] = Instance(_instances[i], validSince);
218:            ids[i] = nextInstanceId;
219:
220:            emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);
221:
222:            nextInstanceId++;
223:        }
224:    }
```

```diff
diff --git a/packages/protocol/contracts/verifiers/SgxVerifier.sol b/packages/protocol/contracts/verifiers/SgxVerifier.sol
index 8ea73fc..98d85f6 100644
--- a/packages/protocol/contracts/verifiers/SgxVerifier.sol
+++ b/packages/protocol/contracts/verifiers/SgxVerifier.sol
@@ -213,13 +213,13 @@ contract SgxVerifier is EssentialContract, IVerifier {
             addressRegistered[_instances[i]] = true;

             if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();
+            uint256 _nextInstanceId = nextInstanceId;
+            instances[_nextInstanceId] = Instance(_instances[i], validSince);
+            ids[i] = _nextInstanceId;

-            instances[nextInstanceId] = Instance(_instances[i], validSince);
-            ids[i] = nextInstanceId;
+            emit InstanceAdded(_nextInstanceId, _instances[i], address(0), validSince);

-            emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);
-
-            nextInstanceId++;
+            nextInstanceId = _nextInstanceId + 1;
         }
     }
```




## [G-02] State variables only set in the constructor should be declared immutable
State variables only set in the constructor should be declared immutable as it avoids a Gsset (20000 gas) in the constructor, and replaces the first access in each transaction (Gcoldsload - 2100 gas) and each access thereafter (Gwarmacces - 100 gas) with a PUSH32 (3 gas).

### 2 Instances

1. #### The `owner` state variable should be made an `immutable` variable
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L52

Making the `owner` state variable immutable would help avoid `Gsset` (20000 gas units) in the constructor during deployment. In implementing this change a cheaper stack read `3 gas` would be used in place of 1 `SLOAD` (cold access 2100 gas units) in the `onlyOwner` modifier and by extension the `setMrSigner)`, `setMrEnclave()`, `addRevokedCertSerialNum()`, `removeRevokedCertSerialNum()`, `configureTcbInfoJson()`, `configureQeIdentityJson()` and `toggleLocalReportCheck()` functions which incorporate the `onlyOwner` modifier. The diff below shows how the code should be refactored: 


```solidity
file: contracts/automata-attestation/AutomataDcapV3Attestation.sol

52:    address public owner;
```

```diff
diff --git a/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol b/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol
index 9ec78e6..7c4225e 100644
--- a/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol
+++ b/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol
@@ -49,7 +49,7 @@ contract AutomataDcapV3Attestation is IAttestation {
     mapping(string fmspc => TCBInfoStruct.TCBInfo tcbInfo) public tcbInfo;
     EnclaveIdStruct.EnclaveId public qeIdentity;

-    address public owner;
+    address public immutable owner;

     constructor(address sigVerifyLibAddr, address pemCertLibAddr) {
         sigVerifyLib = ISigVerifyLib(sigVerifyLibAddr);
```

2. #### The `ES256VERIFIER` state variable should be made an `immutable` variable
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L18

Making the `ES256VERIFIER` state variable immutable would help avoid `Gsset` (20000 gas units) in the constructor during deployment. In implementing this change a cheaper stack read `3 gas` would be used in place of 1 `SLOAD` (cold access 2100 gas units) in the `verifyES256Signature`  function  which reads the `ES256VERIFIER` variable. The diff below shows how the code should be refactored: 

```solidity
file: contracts/automata-attestation/utils/SigVerifyLib.sol

18:    address private ES256VERIFIER;
```

```diff
diff --git a/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol b/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol
index 2b42731..f3f96e8 100644
--- a/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol
+++ b/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol
@@ -15,7 +15,7 @@ import "./BytesUtils.sol";
 contract SigVerifyLib is ISigVerifyLib {
     using BytesUtils for bytes;

-    address private ES256VERIFIER;
+    address private immutable ES256VERIFIER;

     constructor(address es256Verifier) {
         ES256VERIFIER = es256Verifier;
```






## [G-03] Refactor the following function to reduce number of `SLOAD`

### Instances

1. #### Refactor the `LibDepositing.depositEtherToL2()` function such that the number of storage reads (`SLOAD`) is reduced
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol#L29-#L64

We can make the `LibDepositing.depositEtherToL2()` function better gas efficient if we reduce the number of state reads in the function. We can do this by caching state variables that are read more than once into stack variables. The `_state.slotA.numEthDeposits` variable was read three times in the function we should instead read it once and cache its value into a stack variable then use the stack variable for subsequent reads for the variable. Implementing this would avoid `SLOAD`(warmaccess) `100` gas units and replace it with cheaper stack read for the subsequent reads. The diff below shows how the function should be refactored.

```solidity
file: contracts/L1/libs/LibDepositing.sol

29:    function depositEtherToL2(
30:        TaikoData.State storage _state,
31:        TaikoData.Config memory _config,
32:        IAddressResolver _resolver,
33:        address _recipient
34:    )
35:        internal
36:    {
37:        if (!canDepositEthToL2(_state, _config, msg.value)) {
38:            revert L1_INVALID_ETH_DEPOSIT();
39:        }
40:
41:        _resolver.resolve("bridge", false).sendEther(msg.value);
42:
43:        // Append the deposit to the queue.
44:        address recipient_ = _recipient == address(0) ? msg.sender : _recipient;
45:        uint256 slot = _state.slotA.numEthDeposits % _config.ethDepositRingBufferSize;   //@audit 1st _state.slotA.numEthDeposits SLOAD
46:
47:        // range of msg.value is checked by next line.
48:        _state.ethDeposits[slot] = _encodeEthDeposit(recipient_, msg.value);
49:
50:        emit EthDeposited(
51:            TaikoData.EthDeposit({
52:                recipient: recipient_,
53:                amount: uint96(msg.value),
54:                id: _state.slotA.numEthDeposits   //@audit 2nd _state.slotA.numEthDeposits SLOAD
55:            })
56:        );
57:
58:        // Unchecked is safe:
59:        // - uint64 can store up to ~1.8 * 1e19, which can represent 584K years
60:        // if we are depositing at every second
61:        unchecked {
62:            _state.slotA.numEthDeposits++;   //@audit 3rd _state.slotA.numEthDeposits SLOAD
63:        }
64:    }
```

```diff
diff --git a/packages/protocol/contracts/L1/libs/LibDepositing.sol b/packages/protocol/contracts/L1/libs/LibDepositing.sol
index 1d4c9fc..5d2f6de 100644
--- a/packages/protocol/contracts/L1/libs/LibDepositing.sol
+++ b/packages/protocol/contracts/L1/libs/LibDepositing.sol
@@ -40,9 +40,10 @@ library LibDepositing {

         _resolver.resolve("bridge", false).sendEther(msg.value);

+        uint256 _numEthDeposits = _state.slotA.numEthDeposits;
         // Append the deposit to the queue.
         address recipient_ = _recipient == address(0) ? msg.sender : _recipient;
-        uint256 slot = _state.slotA.numEthDeposits % _config.ethDepositRingBufferSize;
+        uint256 slot = _numEthDeposits % _config.ethDepositRingBufferSize;

         // range of msg.value is checked by next line.
         _state.ethDeposits[slot] = _encodeEthDeposit(recipient_, msg.value);
@@ -51,7 +52,7 @@ library LibDepositing {
             TaikoData.EthDeposit({
                 recipient: recipient_,
                 amount: uint96(msg.value),
-                id: _state.slotA.numEthDeposits
+                id: _numEthDeposits
             })
         );

@@ -59,7 +60,7 @@ library LibDepositing {
         // - uint64 can store up to ~1.8 * 1e19, which can represent 584K years
         // if we are depositing at every second
         unchecked {
-            _state.slotA.numEthDeposits++;
+            _state.slotA.numEthDeposits = _numEthDeposits + 1;;
         }
     }
```


2. #### Refactor the `Guardians.setGuardians()` function such that the number of storage reads (`SLOAD`) is reduced
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/provers/Guardians.sol#L53-#L96

We can make the `Guardians.setGuardians()` function better gas efficient if we reduce the number of state reads in the function.  The `version` variable was incremented then read in the `GuardiansUpdated()` event. We could increment and read the `version` variable directly in the emit `GuardiansUpdated()` statement as doing it this way is better and more gas efficient than how it was done. The diff below shows how the code should be refactored: 

```solidity
file: contracts/L1/provers/Guardians.sol

53:    function setGuardians(
54:        address[] memory _newGuardians,
55:        uint8 _minGuardians
56:    )
57:        external
58:        onlyOwner
59:        nonReentrant
60:    {
61:        // We need at least MIN_NUM_GUARDIANS and at most 255 guardians (so the approval bits fit in
62:        // a uint256)
63:        if (_newGuardians.length < MIN_NUM_GUARDIANS || _newGuardians.length > type(uint8).max) {
64:            revert INVALID_GUARDIAN_SET();
65:        }
66:        // Minimum number of guardians to approve is at least equal or greater than half the
67:        // guardians (rounded up) and less or equal than the total number of guardians
68:        if (_minGuardians < (_newGuardians.length + 1) >> 1 || _minGuardians > _newGuardians.length)
69:        {
70:            revert INVALID_MIN_GUARDIANS();
71:        }
72:
73:        // Delete the current guardians
74:        for (uint256 i; i < guardians.length; ++i) {
75:            delete guardianIds[guardians[i]];
76:        }
77:        delete guardians;
78:
79:        // Set the new guardians
80:        for (uint256 i = 0; i < _newGuardians.length; ++i) {
81:            address guardian = _newGuardians[i];
82:            if (guardian == address(0)) revert INVALID_GUARDIAN();
83:            // This makes sure there are not duplicate addresses
84:            if (guardianIds[guardian] != 0) revert INVALID_GUARDIAN_SET();
85:
86:            // Save and index the guardian
87:            guardians.push(guardian);
88:            guardianIds[guardian] = guardians.length;
89:        }
90:
91:        // Bump the version so previous approvals get invalidated
92:        ++version;   //@audit 1st version SLOAD
93:
94:        minGuardians = _minGuardians;
95:        emit GuardiansUpdated(version, _newGuardians);   //@audit 2nd version SLOAD
96:    }
```

```diff
diff --git a/packages/protocol/contracts/L1/provers/Guardians.sol b/packages/protocol/contracts/L1/provers/Guardians.sol
index a4daa55..50c820a 100644
--- a/packages/protocol/contracts/L1/provers/Guardians.sol
+++ b/packages/protocol/contracts/L1/provers/Guardians.sol
@@ -89,10 +89,9 @@ abstract contract Guardians is EssentialContract {
         }

         // Bump the version so previous approvals get invalidated
-        ++version;

         minGuardians = _minGuardians;
-        emit GuardiansUpdated(version, _newGuardians);
+        emit GuardiansUpdated(++version, _newGuardians);
     }
```
```
Estimated gas saved: 100 gas units
```

3. #### Refactor the `TaikoL2._calc1559BaseFee()` function such that the number of storage reads (`SLOAD`) is reduced
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L252-#L297

We can make the `TaikoL2._calc1559BaseFee()` function better gas efficient if we reduce the number of state reads in the function. We can do this by caching state variables that are read more than once into stack variables. The `lastSyncedBlock` variable was read three times in the function we should instead read it once and cache its value into a stack variable then use the stack variable for subsequent reads for the variable. Implementing this would avoid `SLOAD`(warmaccess) `100` gas units and replace it with cheaper stack read for the subsequent reads. The diff below shows how the function should be refactored.

```solidity
file: contracts/L2/TaikoL2.sol

252:    function _calc1559BaseFee(
253:        Config memory _config,
254:        uint64 _l1BlockId,
255:        uint32 _parentGasUsed
256:    )
257:        private
258:        view
259:        returns (uint256 basefee_, uint64 gasExcess_)
260:    {
261:        // gasExcess being 0 indicate the dynamic 1559 base fee is disabled.
262:        if (gasExcess > 0) {
.
.
.
274:            // reverting the initial gas excess value back to 0.
275:            uint256 numL1Blocks;
276:            if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {   //@audit 1st and 2nd lastSyncedBlock SLOAD
277:                numL1Blocks = _l1BlockId - lastSyncedBlock; //@audit 3rd lastSyncedBlock SLOAD
278:            }
279:
280:            if (numL1Blocks > 0) {
281:                uint256 issuance = numL1Blocks * _config.gasTargetPerL1Block;
282:                excess = excess > issuance ? excess - issuance : 1;
283:            }
.
.
.
297:    }
```

```diff
diff --git a/packages/protocol/contracts/L2/TaikoL2.sol b/packages/protocol/contracts/L2/TaikoL2.sol
index 8ad2c82..0004e7b 100644
--- a/packages/protocol/contracts/L2/TaikoL2.sol
+++ b/packages/protocol/contracts/L2/TaikoL2.sol
@@ -272,8 +272,9 @@ contract TaikoL2 is CrossChainOwned {
             // and the difference between the L1 height would be extremely big,
             // reverting the initial gas excess value back to 0.
             uint256 numL1Blocks;
-            if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {
-                numL1Blocks = _l1BlockId - lastSyncedBlock;
+            uint256 _lastSyncedBlock = lastSyncedBlock;
+            if (_lastSyncedBlock > 0 && _l1BlockId > _lastSyncedBlock) {
+                numL1Blocks = _l1BlockId - _lastSyncedBlock;
             }

             if (numL1Blocks > 0) {

```
```
Estimated gas saved: 194 gas units
```

4. #### Refactor the `USDCAdapter._burnToken()` function such that the number of storage reads (`SLOAD`) is reduced
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol#L47-#L50

We can make the `USDCAdapter._burnToken()` function better gas efficient if we reduce the number of state reads in the function. We can do this by caching state variables that are read more than once into stack variables. The `usdc` variable was read twice in the function we should instead read it once and cache its value into a stack variable then use the stack variable for subsequent reads for the variable. Implementing this would avoid `SLOAD`(warmaccess) `100` gas units and replace it with cheaper stack read for the subsequent reads. The diff below shows how the function should be refactored.

```solidity
file: contracts/tokenvault/adapters/USDCAdapter.sol

47:    function _burnToken(address _from, uint256 _amount) internal override {
48:        usdc.transferFrom(_from, address(this), _amount);    //@audit 1st usdc SLOAD
49:        usdc.burn(_amount);    //@audit 2nd usdc SLOAD
50:    }
```

```diff
diff --git a/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol b/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol
index 84c5669..a44dc7d 100644
--- a/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol
+++ b/packages/protocol/contracts/tokenvault/adapters/USDCAdapter.sol
@@ -45,7 +45,8 @@ contract USDCAdapter is BridgedERC20Base {
     }

     function _burnToken(address _from, uint256 _amount) internal override {
-        usdc.transferFrom(_from, address(this), _amount);
-        usdc.burn(_amount);
+        IUSDC _usdc = usdc;
+        _usdc.transferFrom(_from, address(this), _amount);
+        _usdc.burn(_amount);
     }
 }
```
```
Estimated gas saved: 97 gas units
```

5. #### Refactor the `BridgedERC20Base.burn()` function such that the number of storage reads (`SLOAD`) is reduced
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L75-#L89

We can make the `BridgedERC20Base.burn()` function better gas efficient if we reduce the number of state reads in the function. We can do this by caching state variables that are read more than once into stack variables. The `migratingAddress` variable was read twice in the function we should instead read it once and cache its value into a stack variable then use the stack variable for subsequent reads for the variable. Implementing this would avoid `SLOAD`(warmaccess) `100` gas units and replace it with cheaper stack read for the subsequent reads. The diff below shows how the function should be refactored.

```solidity
file: contracts/tokenvault/BridgedERC20Base.sol

75:    function burn(address _account, uint256 _amount) public nonReentrant whenNotPaused {
76:        if (_isMigratingOut()) {
77:            // Only the owner of the tokens himself can migrate out
78:            if (msg.sender != _account) revert BB_PERMISSION_DENIED();
79:            // Outbound migration
80:            emit MigratedTo(migratingAddress, _account, _amount);    //@audit 1st migratingAddress SLOAD
81:            // Ask the new bridged token to mint token for the user.
82:            IBridgedERC20(migratingAddress).mint(_account, _amount);    //@audit 2nd migratingAddress SLOAD
83:        } else if (msg.sender != resolve("erc20_vault", true)) {
84:            // Only the vault can burn tokens when not migrating out
85:            revert RESOLVER_DENIED();
86:        }
87:
88:        _burnToken(_account, _amount);
89:    }
```

```diff
diff --git a/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol b/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol
index 73cb27f..02f6da0 100644
--- a/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol
+++ b/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol
@@ -77,9 +77,10 @@ abstract contract BridgedERC20Base is EssentialContract, IBridgedERC20 {
             // Only the owner of the tokens himself can migrate out
             if (msg.sender != _account) revert BB_PERMISSION_DENIED();
             // Outbound migration
-            emit MigratedTo(migratingAddress, _account, _amount);
+            address _migratingAddress = migratingAddress;
+            emit MigratedTo(_migratingAddress, _account, _amount);
             // Ask the new bridged token to mint token for the user.
-            IBridgedERC20(migratingAddress).mint(_account, _amount);
+            IBridgedERC20(_migratingAddress).mint(_account, _amount);
         } else if (msg.sender != resolve("erc20_vault", true)) {
             // Only the vault can burn tokens when not migrating out
             revert RESOLVER_DENIED();
```
```
Estimated gas saved: 97 gas units
```

6. #### Refactor the `ERC20Airdrop2.getBalance()` function such that the number of storage reads (`SLOAD`) is reduced
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L104-#L121

We can make the `ERC20Airdrop2.getBalance()` function better gas efficient if we reduce the number of state reads in the function. We can do this by caching state variables that are read more than once into stack variables. The `withdrawalWindow` variable was read twice in the function we should instead read it once and cache its value into a stack variable then use the stack variable for subsequent reads for the variable. Implementing this would avoid `SLOAD`(warmaccess) `100` gas units and replace it with cheaper stack read for the subsequent reads. The diff below shows how the function should be refactored.

```solidity
file: contracts/team/airdrop/ERC20Airdrop2.sol

104:    function getBalance(address user)
105:        public
106:        view
107:        returns (uint256 balance, uint256 withdrawableAmount)
108:    {
109:        balance = claimedAmount[user];
110:        // If balance is 0 then there is no balance and withdrawable amount
111:        if (balance == 0) return (0, 0);
112:        // Balance might be positive before end of claiming (claimEnd - if claimed already) but
113:        // withdrawable is 0.
114:        if (block.timestamp < claimEnd) return (balance, 0);
115:
116:        // Hard cap timestamp - so range cannot go over - to get more allocation over time.
117:        uint256 timeBasedAllowance = balance
118:            * (block.timestamp.min(claimEnd + withdrawalWindow) - claimEnd) / withdrawalWindow; //@audit 1st and 2nd withdrawalWindow SLOAD
119:
120:        withdrawableAmount = timeBasedAllowance - withdrawnAmount[user];
121:    }
```

```diff
diff --git a/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol b/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol
index 4ae538b..46a3573 100644
--- a/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol
+++ b/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol
@@ -113,9 +113,10 @@ contract ERC20Airdrop2 is MerkleClaimable {
         // withdrawable is 0.
         if (block.timestamp < claimEnd) return (balance, 0);

+        uint256 _withdrawalWindow = withdrawalWindow;
         // Hard cap timestamp - so range cannot go over - to get more allocation over time.
         uint256 timeBasedAllowance = balance
-            * (block.timestamp.min(claimEnd + withdrawalWindow) - claimEnd) / withdrawalWindow;
+            * (block.timestamp.min(claimEnd + _withdrawalWindow) - claimEnd) / _withdrawalWindow;

         withdrawableAmount = timeBasedAllowance - withdrawnAmount[user];
     }
```

7. #### Refactor the `TimelockTokenPool._withdraw()` function such that the number of storage reads (`SLOAD`) is reduced
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L208-#L223

We can make the `TimelockTokenPool._withdraw()` function better gas efficient if we reduce the number of state reads in the function. We can do this by caching state variables that are read more than once into stack variables. The `withdrawalWindow` variable was read twice in the function we should instead read it once and cache its value into a stack variable then use the stack variable for subsequent reads for the variable. Implementing this would avoid `SLOAD`(warmaccess) `100` gas units and replace it with cheaper stack read for the subsequent reads. The diff below shows how the function should be refactored.

```solidity
file: contracts/team/TimelockTokenPool.sol

208:    function _withdraw(address _recipient, address _to) private {
209:        Recipient storage r = recipients[_recipient];
210:
211:        (,,, uint128 amountToWithdraw, uint128 costToWithdraw) = getMyGrantSummary(_recipient);
212:
213:        r.amountWithdrawn += amountToWithdraw;
214:        r.costPaid += costToWithdraw;
215:
216:        totalAmountWithdrawn += amountToWithdraw;
217:        totalCostPaid += costToWithdraw;
218:
219:        IERC20(taikoToken).transferFrom(sharedVault, _to, amountToWithdraw);    //@audit 1st sharedVault SLOAD
220:        IERC20(costToken).safeTransferFrom(_recipient, sharedVault, costToWithdraw);    //@audit 2nd sharedVault SLOAD
221:
222:        emit Withdrawn(_recipient, _to, amountToWithdraw, costToWithdraw);
223:    }
```

```diff
diff --git a/packages/protocol/contracts/team/TimelockTokenPool.sol b/packages/protocol/contracts/team/TimelockTokenPool.sol
index 44850ab..af36d4f 100644
--- a/packages/protocol/contracts/team/TimelockTokenPool.sol
+++ b/packages/protocol/contracts/team/TimelockTokenPool.sol
@@ -216,8 +216,9 @@ contract TimelockTokenPool is EssentialContract {
         totalAmountWithdrawn += amountToWithdraw;
         totalCostPaid += costToWithdraw;

-        IERC20(taikoToken).transferFrom(sharedVault, _to, amountToWithdraw);
-        IERC20(costToken).safeTransferFrom(_recipient, sharedVault, costToWithdraw);
+        address _sharedVault = sharedVault;
+        IERC20(taikoToken).transferFrom(_sharedVault, _to, amountToWithdraw);
+        IERC20(costToken).safeTransferFrom(_recipient, _sharedVault, costToWithdraw);

         emit Withdrawn(_recipient, _to, amountToWithdraw, costToWithdraw);
     }
```
```
Estimated gas saved: 97 gas units
```



8. #### Refactor the `SgxVerifier.deleteInstances()` function such that the number of storage reads (`SLOAD`) is reduced
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L100-#L113

We can make the `SgxVerifier.deleteInstances()` function better gas efficient if we reduce the number of state reads in the function. We can do this by caching state variables that are read more than once into stack variables. The `migratingAddress` variable was read twice in the function we should instead read it once and cache its value into a stack variable then use the stack variable for subsequent reads for the variable. Implementing this would avoid `SLOAD`(warmaccess) `100` gas units and replace it with cheaper stack read for the subsequent reads. The diff below shows how the function should be refactored.

```solidity
file: contracts/verifiers/SgxVerifier.sol

100:    function deleteInstances(uint256[] calldata _ids)
101:        external
102:        onlyFromOwnerOrNamed("rollup_watchdog")
103:   {
104:        for (uint256 i; i < _ids.length; ++i) {
105:            uint256 idx = _ids[i];
106:
107:            if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();
108:
109:            emit InstanceDeleted(idx, instances[idx].addr);
110:
111:            delete instances[idx];
112:        }
113:    }
```

```diff
diff --git a/packages/protocol/contracts/verifiers/SgxVerifier.sol b/packages/protocol/contracts/verifiers/SgxVerifier.sol
index 8ea73fc..609ff6a 100644
--- a/packages/protocol/contracts/verifiers/SgxVerifier.sol
+++ b/packages/protocol/contracts/verifiers/SgxVerifier.sol
@@ -104,9 +104,10 @@ contract SgxVerifier is EssentialContract, IVerifier {
         for (uint256 i; i < _ids.length; ++i) {
             uint256 idx = _ids[i];

-            if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();
+            address _idxAddress = instances[idx].addr;
+            if (_idxAddress == address(0)) revert SGX_INVALID_INSTANCE();

-            emit InstanceDeleted(idx, instances[idx].addr);
+            emit InstanceDeleted(idx, _idxAddress);

             delete instances[idx];
         }
```
```
Estimated gas saved: 97 gas units
```

9. #### Refactor the `AddressResolver._resolve()` function such that the number of storage reads (`SLOAD`) is reduced
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/AddressResolver.sol#L72-#L88

We can make the `AddressResolver._resolve()` function better gas efficient if we reduce the number of state reads in the function. We can do this by caching state variables that are read more than once into stack variables. The `addressManager` variable was read twice in the function we should instead read it once and cache its value into a stack variable then use the stack variable for subsequent reads for the variable. Implementing this would avoid `SLOAD`(warmaccess) `100` gas units and replace it with cheaper stack read for the subsequent reads. The diff below shows how the function should be refactored.

```solidity
file: contracts/common/AddressResolver.sol

72:    function _resolve(
73:        uint64 _chainId,
74:        bytes32 _name,
75:        bool _allowZeroAddress
76:    )
77:        private
78:        view
79:        returns (address payable addr_)
80:    {
81:        if (addressManager == address(0)) revert RESOLVER_INVALID_MANAGER();
82:
83:        addr_ = payable(IAddressManager(addressManager).getAddress(_chainId, _name));
84:
85:        if (!_allowZeroAddress && addr_ == address(0)) {
86:            revert RESOLVER_ZERO_ADDR(_chainId, _name);
87:        }
88:    }
```

```diff
diff --git a/packages/protocol/contracts/common/AddressResolver.sol b/packages/protocol/contracts/common/AddressResolver.sol
index 122e93f..daf2545 100644
--- a/packages/protocol/contracts/common/AddressResolver.sol
+++ b/packages/protocol/contracts/common/AddressResolver.sol
@@ -78,9 +78,10 @@ abstract contract AddressResolver is IAddressResolver, Initializable {
         view
         returns (address payable addr_)
     {
-        if (addressManager == address(0)) revert RESOLVER_INVALID_MANAGER();
+        address _addressManager = addressManager;
+        if (_addressManager == address(0)) revert RESOLVER_INVALID_MANAGER();

-        addr_ = payable(IAddressManager(addressManager).getAddress(_chainId, _name));
+        addr_ = payable(IAddressManager(_addressManager).getAddress(_chainId, _name));

         if (!_allowZeroAddress && addr_ == address(0)) {
             revert RESOLVER_ZERO_ADDR(_chainId, _name);
```
```
Estimated gas saved: 97 gas units
```




## [G-04] Avoid using state variable in emit
In scenarios where you have a memory, calldata variable or parameter with the same value as the state variable you should use the memory, calldata variable or parameter in the emit statement rather than state variable.

### 1 Instances
1. #### Use `msg.sender` in place of `migratingAddress` in the `MigratedTo` event
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L63

We can make the `BridgedERC20Base.mint()` function cheaper if we use `msg.sender` in place of `migratingAddress` in the `MigratedTo` event. This is because before the event is emitted the if statement `if (msg.sender == migratingAddress)` ensures that the `migratingAddress` is equal to `msg.sender`, since they are both equal we can replace `migratingAddress` with `msg.sender` in the emit statement `emit MigratedTo(migratingAddress, _account, _amount)`. In implementing this change we would avoided 1 `SLOAD` Gwarmaccess `100` gas units and replaced it with a cheaper `CALLER` `2` gas units. The diff below shows how the code should be refactored:

```solidity
file: contracts/tokenvault/BridgedERC20Base.sol

57:    function mint(address _account, uint256 _amount) public nonReentrant whenNotPaused {
58:        // mint is disabled while migrating outbound.
59:        if (_isMigratingOut()) revert BB_MINT_DISALLOWED();
60:
61:        if (msg.sender == migratingAddress) {
62:            // Inbound migration
63:            emit MigratedTo(migratingAddress, _account, _amount);
64:        } else if (msg.sender != resolve("erc20_vault", true)) {
65:            // Bridging from vault
66:            revert BB_PERMISSION_DENIED();
67:        }
68:
69:        _mintToken(_account, _amount);
70:    }
```

```diff
diff --git a/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol b/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol
index 73cb27f..7ce7759 100644
--- a/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol
+++ b/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol
@@ -60,7 +60,7 @@ abstract contract BridgedERC20Base is EssentialContract, IBridgedERC20 {

         if (msg.sender == migratingAddress) {
             // Inbound migration
-            emit MigratedTo(migratingAddress, _account, _amount);
+            emit MigratedTo(msg.sender, _account, _amount);
         } else if (msg.sender != resolve("erc20_vault", true)) {
             // Bridging from vault
             revert BB_PERMISSION_DENIED();

```

```
Estimated gas saved: 98 gas units
```




## [G-05] Resolve `taiko_token` address outside of loop
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibVerifying.sol#L188

In the `LibVerifying.verifyBlocks()` function as shown below the external call  `_resolver.resolve("taiko_token", false))` was used in resolving the `taiko_token` address but this external call was made in a loop and the returned result is not in any way dependent of the loop iterations (i.e having to make the same external call to get the same value for every iteration of the loop) therby making the function highly gas consuming and inefficent. We should rather resolve the address outside the loop and cache the returned value then use the cached value in the loop. The diff below shows how the function should be refactored:

```solidity
file: contracts/L1/libs/LibVerifying.sol

85:     function verifyBlocks(
86:         TaikoData.State storage _state,
87:         TaikoData.Config memory _config,
88:         IAddressResolver _resolver,
89:         uint64 _maxBlocksToVerify
90:     )
91:         internal
92:     {
.
.
.
127:            while (blockId < b.numBlocks && numBlocksVerified < _maxBlocksToVerify) {
128:                slot = blockId % _config.blockRingBufferSize;
129:
130:                blk = _state.blocks[slot];
131:                if (blk.blockId != blockId) revert L1_BLOCK_MISMATCH();
132:
133:                tid = LibUtils.getTransitionId(_state, blk, slot, blockHash);
134:                // When `tid` is 0, it indicates that there is no proven
135:                // transition with its parentHash equal to the blockHash of the
136:                // most recently verified block.
137:                if (tid == 0) break;
138:
139:                // A transition with the correct `parentHash` has been located.
140:                TaikoData.TransitionState storage ts = _state.transitions[slot][tid];
141:
142:                // It's not possible to verify this block if either the
143:                // transition is contested and awaiting higher-tier proof or if
144:                // the transition is still within its cooldown period.
145:                if (ts.contester != address(0)) {
146:                    break;
147:                } else {
148:                    if (tierProvider == address(0)) {
149:                        tierProvider = _resolver.resolve("tier_provider", false);
150:                    }
151:                    if (
152:                        uint256(ITierProvider(tierProvider).getTier(ts.tier).cooldownWindow) * 60
153:                            + uint256(ts.timestamp).max(_state.slotB.lastUnpausedAt) > block.timestamp
154:                    ) {
155:                        // If cooldownWindow is 0, the block can theoretically
156:                        // be proved and verified within the same L1 block.
157:                        break;
158:                    }
159:                }
160:
161:                // Mark this block as verified
162:                blk.verifiedTransitionId = tid;
163:
164:                // Update variables
165:                blockHash = ts.blockHash;
166:                stateRoot = ts.stateRoot;
167:
168:                // We consistently return the liveness bond and the validity
169:                // bond to the actual prover of the transition utilized for
170:                // block verification. If the actual prover happens to be the
171:                // block's assigned prover, he will receive both deposits,
172:                // ultimately earning the proving fee paid during block
173:                // proposal. In contrast, if the actual prover is different from
174:                // the block's assigned prover, the liveness bond serves as a
175:                // reward to the actual prover, while the assigned prover
176:                // forfeits his liveness bond due to failure to fulfill their
177:                // commitment.
178:                uint256 bondToReturn = uint256(ts.validityBond) + blk.livenessBond;
179:
180:                // Nevertheless, it's possible for the actual prover to be the
181:                // same individual or entity as the block's assigned prover.
182:                // Consequently, we have chosen to grant the actual prover only
183:                // half of the liveness bond as a reward.
184:                if (ts.prover != blk.assignedProver) {
185:                    bondToReturn -= blk.livenessBond >> 1;
186:                }
187:
188:                IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));   //@audit resolve "taiko_token" outside loop
189:                tko.transfer(ts.prover, bondToReturn);
.
.
.
221:        }
222:    }
```

```diff
diff --git a/packages/protocol/contracts/L1/libs/LibVerifying.sol b/packages/protocol/contracts/L1/libs/LibVerifying.sol
index ce27624..46f14f4 100644
--- a/packages/protocol/contracts/L1/libs/LibVerifying.sol
+++ b/packages/protocol/contracts/L1/libs/LibVerifying.sol
@@ -117,6 +117,8 @@ library LibVerifying {
         uint64 numBlocksVerified;
         address tierProvider;

+        IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));
+
         // Unchecked is safe:
         // - assignment is within ranges
         // - blockId and numBlocksVerified values incremented will still be OK in the
@@ -185,7 +187,7 @@ library LibVerifying {
                     bondToReturn -= blk.livenessBond >> 1;
                 }

-                IERC20 tko = IERC20(_resolver.resolve("taiko_token", false));
+
                 tko.transfer(ts.prover, bondToReturn);

                 // Note: We exclusively address the bonds linked to the
```







## [G-06] Multiple accesses of a mapping should use a local variable cache
The instances below point to the second+ access of a value inside a mapping, within a function. Caching a mapping's value in a local storage or calldata variable when the value is accessed multiple times, saves ~42 gas per access due to not having to recalculate the key's keccak256 hash (Gkeccak256 - 30 gas) and that calculation's associated stack operations. 

### 2 Instances

1. #### Cache `proofReceipt[msgHash]` to a local storage `ProofReceipt` struct
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L230
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L243
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L250

We could save up to `80` gas units in the `Bridge.processMessage()` function if we cache `proofReceipt[msgHash]` into a local storage `ProofReceipt` struct variable as this saves the EVM from having to re-calculate the key has for subsequent operations that involves `proofReceipt[msgHash]`. The diff below shows how the code could be refactored:

```solidity
file: contracts/bridge/Bridge.sol

217:    function processMessage(
218:        Message calldata _message,
219:        bytes calldata _proof
220:    )
221:        external
222:        nonReentrant
223:        whenNotPaused
224:        sameChain(_message.destChainId)
225:    {
226:        bytes32 msgHash = hashMessage(_message);
227:        if (messageStatus[msgHash] != Status.NEW) revert B_STATUS_MISMATCH();
228:
229:        address signalService = resolve("signal_service", false);
230:        uint64 receivedAt = proofReceipt[msgHash].receivedAt;   //@audit mapping hash would be calculated
231:        bool isMessageProven = receivedAt != 0;
232:
233:        (uint256 invocationDelay, uint256 invocationExtraDelay) = getInvocationDelays();
234:
235:        if (!isMessageProven) {
236:            if (!_proveSignalReceived(signalService, msgHash, _message.srcChainId, _proof)) {
237:                revert B_NOT_RECEIVED();
238:            }
239:
240:            receivedAt = uint64(block.timestamp);
241:
242:            if (invocationDelay != 0) {
243:                proofReceipt[msgHash] = ProofReceipt({     //@audit mapping hash would be calculated
244:                    receivedAt: receivedAt,
245:                    preferredExecutor: _message.gasLimit == 0 ? _message.destOwner : msg.sender
246:                });
247:            }
248:        }
249:
250:        if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) {   //@audit mapping hash would be calculated
251:            // If msg.sender is not the one that proved the message, then there
252:            // is an extra delay.
253:            unchecked {
254:                invocationDelay += invocationExtraDelay;
255:            }
256:        }
.
.
.
307:    }
```

```diff
diff --git a/packages/protocol/contracts/bridge/Bridge.sol b/packages/protocol/contracts/bridge/Bridge.sol
index 0258845..3200bfa 100644
--- a/packages/protocol/contracts/bridge/Bridge.sol
+++ b/packages/protocol/contracts/bridge/Bridge.sol
@@ -227,7 +227,8 @@ contract Bridge is EssentialContract, IBridge {
         if (messageStatus[msgHash] != Status.NEW) revert B_STATUS_MISMATCH();

         address signalService = resolve("signal_service", false);
-        uint64 receivedAt = proofReceipt[msgHash].receivedAt;
+        ProofReceipt storage _proofReceipt = proofReceipt[msgHash];
+        uint64 receivedAt = _proofReceipt.receivedAt;
         bool isMessageProven = receivedAt != 0;

         (uint256 invocationDelay, uint256 invocationExtraDelay) = getInvocationDelays();
@@ -240,14 +241,12 @@ contract Bridge is EssentialContract, IBridge {
             receivedAt = uint64(block.timestamp);

             if (invocationDelay != 0) {
-                proofReceipt[msgHash] = ProofReceipt({
-                    receivedAt: receivedAt,
-                    preferredExecutor: _message.gasLimit == 0 ? _message.destOwner : msg.sender
-                });
+                _proofReceipt.receivedAt = receivedAt;
+                _proofReceipt.preferredExecutor = _message.gasLimit == 0 ? _message.destOwner : msg.sender;
             }
         }

-        if (invocationDelay != 0 && msg.sender != proofReceipt[msgHash].preferredExecutor) {
+        if (invocationDelay != 0 && msg.sender != _proofReceipt.preferredExecutor) {
             // If msg.sender is not the one that proved the message, then there
             // is an extra delay.
             unchecked {
```
```
Estimated gas saved: 80 gas units
```

2. #### Cache `instances[id]` to a local storage `Instance` struct
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L235
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L236
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/verifiers/SgxVerifier.sol#L237

We could save up to `80` gas units in the `SgxVerifier.processMessage()` function if we cache `instances[id]` into a local storage `Instance` struct variable as this saves the EVM from having to re-calculate the key has for subsequent operations that involves `instances[id]`. The diff below shows how the code could be refactored:

```solidity
file: contracts/verifiers/SgxVerifier.sol

233:    function _isInstanceValid(uint256 id, address instance) private view returns (bool) {
234:        if (instance == address(0)) return false;
235:        if (instance != instances[id].addr) return false;
236:        return instances[id].validSince <= block.timestamp
237:            && block.timestamp <= instances[id].validSince + INSTANCE_EXPIRY;
238:    }
```

```diff
diff --git a/packages/protocol/contracts/verifiers/SgxVerifier.sol b/packages/protocol/contracts/verifiers/SgxVerifier.sol
index 8ea73fc..032680e 100644
--- a/packages/protocol/contracts/verifiers/SgxVerifier.sol
+++ b/packages/protocol/contracts/verifiers/SgxVerifier.sol
@@ -232,8 +232,9 @@ contract SgxVerifier is EssentialContract, IVerifier {

     function _isInstanceValid(uint256 id, address instance) private view returns (bool) {
         if (instance == address(0)) return false;
-        if (instance != instances[id].addr) return false;
-        return instances[id].validSince <= block.timestamp
-            && block.timestamp <= instances[id].validSince + INSTANCE_EXPIRY;
+        Instance storage _instance = instances[id];
+        if (instance != _instance.addr) return false;
+        return _instance.validSince <= block.timestamp
+            && block.timestamp <= _instance.validSince + INSTANCE_EXPIRY;
     }
 }
```
```
Estimated gas saved: 80 gas units
```


## [G-06] Redundant state variable getters
Getters for public state variables are automatically generated by the solidity compiler so there is no need to code them manually as this increases deployment cost.

### 1 Instance

1. #### Make `customConfig` mapping variable `private` or `internal` since a getter function was defined for it.
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L11

The solidity compiler would automatically create a getter function for the `positionLendTokenData` mapping since it is declared as a `public` variable but a getter function `getConfig()` was also declared in the `TaikoL2EIP1559Configurable` contract for the same variable thereby making it two getter functions for the same variable in the contract. We could rectify this issue by making the `customConfig` variable private or internal (if the variable is to be inherited). The diff below shows how the code could be refactored:

```solidity
file: contracts/L2/TaikoL2EIP1559Configurable.sol

11:    Config public customConfig;
```

```diff
diff --git a/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol b/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol
index 1ae9071..663c3ba 100644
--- a/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol
+++ b/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol
@@ -8,7 +8,7 @@ import "./TaikoL2.sol";
 /// @custom:security-contact security@taiko.xyz
 contract TaikoL2EIP1559Configurable is TaikoL2 {
     /// @notice EIP-1559 configuration.
-    Config public customConfig;
+    Config internal customConfig;

     uint256[49] private __gap;
```


## [G-07] Structs can be packed into fewer storage slots by re-ordering the variables
The EVM works with 32 byte words. Variables less than 32 bytes can be declared next to eachother in storage and this will pack the values together into a single 32 byte storage slot (if values combined are <= 32 bytes). If the variables packed together are retrieved together in functions (more likely with structs) we will effectively save ~2000 gas with every subsequent SLOAD for that storage slot. This is due to us incurring a Gwarmaccess (100 gas) versus a Gcoldsload (2100 gas).  This optimization can help save gas costs by reducing the number of storage slots used.

### Instances

1. #### Pack `assignedProver`, `txListByteOffset`, `txListByteSize` and `cacheBlobForReuse` into one storage slot to save 1 SLOT (~2000 gas)
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L78-#L88

We could reduce the number of storage slots required for the `BlockParams` struct from 7 slots to 6 slots if we pack `assignedProver (20 bytes)`, `txListByteOffset (3 bytes)`, `txListByteSize (3 bytes)` and `cacheBlobForReuse (1 byte)` into one slot since their total bytes is less than 32 bytes there by saving 1 slot.

```solidity
file: contracts/L1/TaikoData.sol

78:    struct BlockParams {
79:        address assignedProver;      // SLOT 1
80:        address coinbase;            // SLOT 2
81:        bytes32 extraData;           // SLOT 3
82:        bytes32 blobHash;            // SLOT 4
83:        uint24 txListByteOffset;     // SLOT 5
84:        uint24 txListByteSize;       // SLOT 5
85:        bool cacheBlobForReuse;      // SLOT 5
86:        bytes32 parentMetaHash;      // SLOT 6
87:        HookCall[] hookCalls;        // SLOT 7
88:    }
```

```diff
diff --git a/packages/protocol/contracts/L1/TaikoData.sol b/packages/protocol/contracts/L1/TaikoData.sol
index 0b5513e..0f15954 100644
--- a/packages/protocol/contracts/L1/TaikoData.sol
+++ b/packages/protocol/contracts/L1/TaikoData.sol
@@ -77,12 +77,12 @@ library TaikoData {

     struct BlockParams {
         address assignedProver;  
-        address coinbase;
-        bytes32 extraData;
-        bytes32 blobHash;
         uint24 txListByteOffset;
         uint24 txListByteSize;
         bool cacheBlobForReuse;
+        address coinbase;
+        bytes32 extraData;
+        bytes32 blobHash;
         bytes32 parentMetaHash;
         HookCall[] hookCalls;
     }
```
```
Estimated gas saved: 2000 gas units
```

2. #### Pack `blockMaxGasLimit`, `blockMaxTxListBytes`, `blobExpiry`, `blobAllowedForDA`, `blobReuseEnabled`, `livenessBond` and `blockSyncThreshold` into one storage slot to save 1 SLOT (~2000 gas)
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoData.sol#L10-#L60

We could reduce the number of storage slots required for the `Config` struct from 8 slots to 7 slots if we pack `blockMaxGasLimit (4 bytes)`, `blockMaxTxListBytes (3 bytes)`, `blobExpiry (3 bytes)`, `blobAllowedForDA (1 byte)`, `blobReuseEnabled (1 byte)`, `livenessBond (12 bytes)` and `blockSyncThreshold (1 byte)` into one slot since their total bytes is less than 32 bytes there by saving 1 slot.

```solidity
file: contracts/L1/TaikoData.sol

10:    struct Config {
        
15:        uint64 chainId;                          // SLOT 1
20:        uint64 blockMaxProposals;                // SLOT 1
22:        uint64 blockRingBufferSize;              // SLOT 1
24:        uint64 maxBlocksToVerifyPerProposal;     // SLOT 1
26:        uint32 blockMaxGasLimit;                 // SLOT 2
28:        uint24 blockMaxTxListBytes;              // SLOT 2
30:        uint24 blobExpiry;                       // SLOT 2
32:        bool blobAllowedForDA;                   // SLOT 2
34:        bool blobReuseEnabled;                   // SLOT 2
39:        uint96 livenessBond;                     // SLOT 2
44:        uint256 ethDepositRingBufferSize;        // SLOT 3
46:        uint64 ethDepositMinCountPerBlock;       // SLOT 4
48:        uint64 ethDepositMaxCountPerBlock;       // SLOT 4
50:        uint96 ethDepositMinAmount;              // SLOT 4
52:        uint96 ethDepositMaxAmount;              // SLOT 5
54:        uint256 ethDepositGas;                   // SLOT 6
56:        uint256 ethDepositMaxFee;                // SLOT 7
59:        uint8 blockSyncThreshold;                // SLOT 8
60:    }
```

```diff
diff --git a/packages/protocol/contracts/L1/TaikoData.sol b/packages/protocol/contracts/L1/TaikoData.sol
index 0b5513e..69a6cdd 100644
--- a/packages/protocol/contracts/L1/TaikoData.sol
+++ b/packages/protocol/contracts/L1/TaikoData.sol
@@ -37,6 +37,7 @@ library TaikoData {
         uint64 chainId;
         uint64 blockMaxProposals;
         uint64 blockRingBufferSize;
         uint64 maxBlocksToVerifyPerProposal;
         uint32 blockMaxGasLimit;
         uint24 blockMaxTxListBytes; 
         uint24 blobExpiry;           
         bool blobAllowedForDA;      
         bool blobReuseEnabled;      
         uint96 livenessBond;
+        uint8 blockSyncThreshold;
         uint256 ethDepositRingBufferSize;
         uint64 ethDepositMinCountPerBlock;
         uint64 ethDepositMaxCountPerBlock;
         uint96 ethDepositMinAmount;
         uint96 ethDepositMaxAmount;
         uint256 ethDepositGas;  
@@ -56,7 +57,7 @@ library TaikoData {
         uint256 ethDepositMaxFee;
-        uint8 blockSyncThreshold;
```
```
Estimated gas saved: 2000gas units
```


3. #### Pack `cpuSvn`, `miscSelect`, `isvProdId` and `isvSvn` into one storage slot to save 1 SLOT (~2000 gas)
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol#L17-#L31

We could reduce the number of storage slots required for the `EnclaveReport` struct from 10 slots to 9 slots if we pack `cpuSvn (16 bytes)`, `miscSelect (4 bytes)`, `isvProdId (2 bytes)` and `isvSvn (2 bytes)` into one slot since their total bytes is less than 32 bytes there by saving 1 slot.

```solidity
file: contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol

17:    struct EnclaveReport {
18:        bytes16 cpuSvn;          // SLOT 1
19:        bytes4 miscSelect;       // SLOT 1
20:        bytes28 reserved1;       // SLOT 2
21:        bytes16 attributes;      // SLOT 3
22:        bytes32 mrEnclave;       // SLOT 4
23:        bytes32 reserved2;       // SLOT 5
24:        bytes32 mrSigner;        // SLOT 6
25:        bytes reserved3;         // SLOT 7
26:        uint16 isvProdId;        // SLOT 8
27:        uint16 isvSvn;           // SLOT 8
28:        bytes reserved4;         // SLOT 9
29:        bytes reportData;        // SLOT 10
30:            // of attestation key and QEAuthData
31:    }
```

```diff
diff --git a/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol b/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol
index 3fbf799..0c9a6d7 100644
--- a/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol
+++ b/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Struct.sol
@@ -17,14 +17,14 @@ library V3Struct {
     struct EnclaveReport {
         bytes16 cpuSvn;
         bytes4 miscSelect;
+        uint16 isvProdId;
+        uint16 isvSvn;
         bytes28 reserved1;
         bytes16 attributes;
         bytes32 mrEnclave;
         bytes32 reserved2;
         bytes32 mrSigner;
         bytes reserved3; // 96 bytes
-        uint16 isvProdId;
-        uint16 isvSvn;
         bytes reserved4; // 60 bytes
         bytes reportData; // 64 bytes - For QEReports, this contains the hash of the concatenation
             // of attestation key and QEAuthData
```
```
Estimated gas saved: 2000 gas units
```




## [G-08] Refactor external/internal function to avoid unnecessary SLOAD
The functions below read storage slots that are previously read in the functions that invoke them. We can refactor the external/internal functions to pass cached storage variables as stack variables and avoid the extra storage reads that would otherwise take place in the internal functions.

### Instances

1. #### Refactor the `processMessage()` and `retryMessage()` external functions and the `_updateMessageStatus()` private function
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L217-#L307 (external function)
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L310-#L337 (external function)
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L515-#L526 (private function)

The external functions `processMessage()` and `retryMessage()` as shown below both invoke the private function `_updateMessageStatus()` but both the external function and the private function read the `messageStatus[msgHash]` mapping also the private function `_updateMessageStatus()` was only invoked in these two external functions therefore we can refactor the functions such that the external functions `processMessage()` and `retryMessage()` passes the cached value of `messageStatus[msgHash]` as an argument to the `_updateMessageStatus()`. Refactoring the code this way would help make the `_updateMessageStatus()` function cheaper as it does not have to read the `messageStatus[msgHash]` mapping and by extension make the `processMessage()` and `retryMessage()` functions cheaper: The diff below shows how the code should be refactored: 

```solidity
file: contracts/bridge/Bridge.sol

217:    function processMessage(
218:        Message calldata _message,
219:        bytes calldata _proof
220:    )
221:        external
222:        nonReentrant
223:        whenNotPaused
224:        sameChain(_message.destChainId)
225:    {
226:        bytes32 msgHash = hashMessage(_message);
227:        if (messageStatus[msgHash] != Status.NEW) revert B_STATUS_MISMATCH();      //@audit state read in external function
.
.
.
258:        if (block.timestamp >= invocationDelay + receivedAt) {
259:            // If the gas limit is set to zero, only the owner can process the message.
260:            if (_message.gasLimit == 0 && msg.sender != _message.destOwner) {
261:                revert B_PERMISSION_DENIED();
262:            }
263:
264:            delete proofReceipt[msgHash];
265:
266:            uint256 refundAmount;
267:
268:            // Process message differently based on the target address
269:            if (
270:                _message.to == address(0) || _message.to == address(this)
271:                    || _message.to == signalService || addressBanned[_message.to]
272:            ) {
273:                // Handle special addresses that don't require actual invocation but
274:                // mark message as DONE
275:                refundAmount = _message.value;
276:                _updateMessageStatus(msgHash, Status.DONE); //@audit private _updateMessageStatus function invoked
277:            } else {
278:                // Use the specified message gas limit if called by the owner, else
279:                // use remaining gas
280:                uint256 gasLimit = msg.sender == _message.destOwner ? gasleft() : _message.gasLimit;
281:
282:                if (_invokeMessageCall(_message, msgHash, gasLimit)) {
283:                    _updateMessageStatus(msgHash, Status.DONE); //@audit private _updateMessageStatus function invoked
284:                } else {
285:                    _updateMessageStatus(msgHash, Status.RETRIABLE);    //@audit private _updateMessageStatus function invoked
286:                }
287:           }
.
.
.
307:    }
.
.
.
310:    function retryMessage(
311:        Message calldata _message,
312:        bool _isLastAttempt
313:    )
314:        external
315:        nonReentrant
316:        whenNotPaused
317:        sameChain(_message.destChainId)
318:    {
319:        // If the gasLimit is set to 0 or isLastAttempt is true, the caller must
320:        // be the message.destOwner.
321:        if (_message.gasLimit == 0 || _isLastAttempt) {
322:            if (msg.sender != _message.destOwner) revert B_PERMISSION_DENIED();
323:        }
324:
325:        bytes32 msgHash = hashMessage(_message);
326:        if (messageStatus[msgHash] != Status.RETRIABLE) {   //@audit state read in external function
327:            revert B_NON_RETRIABLE();
328:        }
329:
330:        // Attempt to invoke the messageCall.
331:        if (_invokeMessageCall(_message, msgHash, gasleft())) {
332:            _updateMessageStatus(msgHash, Status.DONE);     //@audit private _updateMessageStatus function invoked
333:        } else if (_isLastAttempt) {
334:            _updateMessageStatus(msgHash, Status.FAILED);     //@audit private _updateMessageStatus function invoked
335:        }
336:        emit MessageRetried(msgHash);
337:    }
.
.
.
515:    function _updateMessageStatus(bytes32 _msgHash, Status _status) private {
516:        if (messageStatus[_msgHash] == _status) return;     //@audit state read in private function
517:
518:        messageStatus[_msgHash] = _status;
519:        emit MessageStatusChanged(_msgHash, _status);
520:
521:        if (_status == Status.FAILED) {
522:            ISignalService(resolve("signal_service", false)).sendSignal(
523:                signalForFailedMessage(_msgHash)
524:            );
525:        }
526;    }
```

```diff
diff --git a/packages/protocol/contracts/bridge/Bridge.sol b/packages/protocol/contracts/bridge/Bridge.sol
index 0258845..3370521 100644
--- a/packages/protocol/contracts/bridge/Bridge.sol
+++ b/packages/protocol/contracts/bridge/Bridge.sol
@@ -224,7 +224,8 @@ contract Bridge is EssentialContract, IBridge {
         sameChain(_message.destChainId)
     {
         bytes32 msgHash = hashMessage(_message);
-        if (messageStatus[msgHash] != Status.NEW) revert B_STATUS_MISMATCH();
+        Status currentStatus = messageStatus[msgHash];
+        if (currentStatus != Status.NEW) revert B_STATUS_MISMATCH();

         address signalService = resolve("signal_service", false);
         uint64 receivedAt = proofReceipt[msgHash].receivedAt;
@@ -273,16 +274,16 @@ contract Bridge is EssentialContract, IBridge {
                 // Handle special addresses that don't require actual invocation but
                 // mark message as DONE
                 refundAmount = _message.value;
-                _updateMessageStatus(msgHash, Status.DONE);
+                _updateMessageStatus(currentStatus, msgHash, Status.DONE);
             } else {
                 // Use the specified message gas limit if called by the owner, else
                 // use remaining gas
                 uint256 gasLimit = msg.sender == _message.destOwner ? gasleft() : _message.gasLimit;

                 if (_invokeMessageCall(_message, msgHash, gasLimit)) {
-                    _updateMessageStatus(msgHash, Status.DONE);
+                    _updateMessageStatus(currentStatus, msgHash, Status.DONE);
                 } else {
-                    _updateMessageStatus(msgHash, Status.RETRIABLE);
+                    _updateMessageStatus(currentStatus, msgHash, Status.RETRIABLE);
                 }
             }

@@ -323,15 +324,16 @@ contract Bridge is EssentialContract, IBridge {
         }

         bytes32 msgHash = hashMessage(_message);
-        if (messageStatus[msgHash] != Status.RETRIABLE) {
+        Status currentStatus = messageStatus[msgHash];
+        if (currentStatus != Status.RETRIABLE) {
             revert B_NON_RETRIABLE();
         }

         // Attempt to invoke the messageCall.
         if (_invokeMessageCall(_message, msgHash, gasleft())) {
-            _updateMessageStatus(msgHash, Status.DONE);
+            _updateMessageStatus(currentStatus, msgHash, Status.DONE);
         } else if (_isLastAttempt) {
-            _updateMessageStatus(msgHash, Status.FAILED);
+            _updateMessageStatus(currentStatus, msgHash, Status.FAILED);
         }
         emit MessageRetried(msgHash);
     }
@@ -512,8 +514,8 @@ contract Bridge is EssentialContract, IBridge {
     /// mapping, the status is updated and an event is emitted.
     /// @param _msgHash The hash of the message.
     /// @param _status The new status of the message.
-    function _updateMessageStatus(bytes32 _msgHash, Status _status) private {
-        if (messageStatus[_msgHash] == _status) return;
+    function _updateMessageStatus(Status currentStatus, bytes32 _msgHash, Status _status) private {
+        if (currentStatus == _status) return;

         messageStatus[_msgHash] = _status;
         emit MessageStatusChanged(_msgHash, _status);
```



## [G-09] Refactor the `init` function  of `TimelockTokenPool` contract such that all the checks on the arguments are performed before assigning the values to state variables.
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L111-#L129

The `init` function  of `TimelockTokenPool` contract such that all the checks on the arguments are performed before assigning the values to state variables. because for example in a scenario such that the check on [line 127](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L127) fails the function would revert but it would have assigned values to the `taikoToken` and `costToken` state variables costing 2 `SSTORE` `40000` gas units. But if all the checks are performed first before assigning any value to any of state variables and a check fails the deployment would revert without performing consuming huge amount of gas thereby making the function better gas efficient. The diff below shows how the code could be refactored:

```solidity
file: contracts/team/TimelockTokenPool.sol

111:    function init(
112:        address _owner,
113:        address _taikoToken,
114:        address _costToken,
115:        address _sharedVault
116:    )
117:        external
118:        initializer
119:    {
120:        __Essential_init(_owner);
121:        if (_taikoToken == address(0)) revert INVALID_PARAM();
122:        taikoToken = _taikoToken;
123:
124:        if (_costToken == address(0)) revert INVALID_PARAM();
125:        costToken = _costToken;
126:
127:        if (_sharedVault == address(0)) revert INVALID_PARAM();
128:        sharedVault = _sharedVault;
129:    }
```

```diff
diff --git a/packages/protocol/contracts/team/TimelockTokenPool.sol b/packages/protocol/contracts/team/TimelockTokenPool.sol
index 44850ab..2eab958 100644
--- a/packages/protocol/contracts/team/TimelockTokenPool.sol
+++ b/packages/protocol/contracts/team/TimelockTokenPool.sol
@@ -119,12 +119,11 @@ contract TimelockTokenPool is EssentialContract {
     {
         __Essential_init(_owner);
         if (_taikoToken == address(0)) revert INVALID_PARAM();
-        taikoToken = _taikoToken;
-
         if (_costToken == address(0)) revert INVALID_PARAM();
-        costToken = _costToken;
-
         if (_sharedVault == address(0)) revert INVALID_PARAM();
+
+        taikoToken = _taikoToken;
+        costToken = _costToken;
         sharedVault = _sharedVault;
     }
```



## [G-10] Unchecked Divisions
Divisions which do not divide by -X cannot overflow or overflow so such operations can be unchecked to save gas.

### Instances
1. #### unchecked uint divisions in `Lib1559Math.basefee()` function to reduce its gas cost.
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/Lib1559Math.sol#L28-#L29

```solidity
file: contracts/L2/Lib1559Math.sol

16:    function basefee(
17:        uint256 _gasExcess,
18:        uint256 _adjustmentFactor
19:    )
20:        internal
21:        pure
22:        returns (uint256)
23:    {
24:        if (_adjustmentFactor == 0) {
25:            revert EIP1559_INVALID_PARAMS();
26:        }
27:
28:        return _ethQty(_gasExcess, _adjustmentFactor) / LibFixedPointMath.SCALING_FACTOR //@audit can be unchecked
29:            / _adjustmentFactor;
30:    }
```

```diff
diff --git a/packages/protocol/contracts/L2/Lib1559Math.sol b/packages/protocol/contracts/L2/Lib1559Math.sol
index efe3da5..1937fae 100644
--- a/packages/protocol/contracts/L2/Lib1559Math.sol
+++ b/packages/protocol/contracts/L2/Lib1559Math.sol
@@ -25,8 +25,11 @@ library Lib1559Math {
             revert EIP1559_INVALID_PARAMS();
         }

-        return _ethQty(_gasExcess, _adjustmentFactor) / LibFixedPointMath.SCALING_FACTOR
+        unchecked {
+            return _ethQty(_gasExcess, _adjustmentFactor) / LibFixedPointMath.SCALING_FACTOR
             / _adjustmentFactor;
+        }
+
     }

     /// @dev exp(gas_qty / TARGET / ADJUSTMENT_QUOTIENT)
```

2. #### unchecked uint divisions in `TimelockTokenPool.getMyGrantSummary()` function to reduce its gas cost.
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/team/TimelockTokenPool.sol#L197

```solidity
file: contracts/team/TimelockTokenPool.sol

176:    function getMyGrantSummary(address _recipient)
177:        public
178:        view
179:        returns (
180:            uint128 amountOwned,
181:            uint128 amountUnlocked,
182:            uint128 amountWithdrawn,
183:            uint128 amountToWithdraw,
184:            uint128 costToWithdraw
185:        )
186:    {
187:        Recipient storage r = recipients[_recipient];
188:
189:        amountOwned = _getAmountOwned(r.grant);
190:        amountUnlocked = _getAmountUnlocked(r.grant);
191:
192:        amountWithdrawn = r.amountWithdrawn;
193:        amountToWithdraw = amountUnlocked - amountWithdrawn;
194:
195:        // Note: precision is maintained at the token level rather than the wei level, otherwise,
196:        // `costPaid` must be a uint256.
197:        uint128 _amountUnlocked = amountUnlocked / 1e18; // divide first    //@audit can be unchecked
198:        costToWithdraw = _amountUnlocked * r.grant.costPerToken - r.costPaid;
199:    }
```

```diff
diff --git a/packages/protocol/contracts/team/TimelockTokenPool.sol b/packages/protocol/contracts/team/TimelockTokenPool.sol
index 44850ab..7f03d89 100644
--- a/packages/protocol/contracts/team/TimelockTokenPool.sol
+++ b/packages/protocol/contracts/team/TimelockTokenPool.sol
@@ -194,7 +194,11 @@ contract TimelockTokenPool is EssentialContract {

         // Note: precision is maintained at the token level rather than the wei level, otherwise,
         // `costPaid` must be a uint256.
-        uint128 _amountUnlocked = amountUnlocked / 1e18; // divide first
+        uint128 _amountUnlocked;
+        unchecked {
+            _amountUnlocked = amountUnlocked / 1e18;     // divide first
+        }
+
         costToWithdraw = _amountUnlocked * r.grant.costPerToken - r.costPaid;
     }
```

3. #### unchecked uint divisions in `V3Parser.littleEndianDecode()` function to reduce its gas cost.
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L155

```solidity
file: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

152:    function littleEndianDecode(bytes memory encoded) private pure returns (uint256 decoded) {
153:        for (uint256 i; i < encoded.length; ++i) {
154:            uint256 digits = uint256(uint8(bytes1(encoded[i])));
155:            uint256 upperDigit = digits / 16;
156:            uint256 lowerDigit = digits % 16;
157:
158:            uint256 acc = lowerDigit * (16 ** (2 * i));
159:            acc += upperDigit * (16 ** ((2 * i) + 1));
160:
161:            decoded += acc;
162:        }
163:    }
```

```diff
diff --git a/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol b/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol
index cb24cb7..c649c57 100644
--- a/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol
+++ b/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol
@@ -152,7 +152,10 @@ library V3Parser {
     function littleEndianDecode(bytes memory encoded) private pure returns (uint256 decoded) {
         for (uint256 i; i < encoded.length; ++i) {
             uint256 digits = uint256(uint8(bytes1(encoded[i])));
-            uint256 upperDigit = digits / 16;
+            uint256 upperDigit;
+            unchecked {
+                upperDigit = digits / 16;
+            }
             uint256 lowerDigit = digits % 16;

             uint256 acc = lowerDigit * (16 ** (2 * i));
```


## [G-11] Add unchecked blocks for subtractions where the operands cannot underflow
The solidity compiler introduces some checks to avoid an underflow, but in some scenarios where it is impossible for underflow to occur we can use unchecked blocks to have some gas savings.

### Instances
1. #### The calculations `numL1Blocks = _l1BlockId - lastSyncedBlock` and `excess = excess > issuance ? excess - issuance : 1` can be unchecked
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L275-#L282

The if statement `if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock)` ensures that its impossible for the value of `lastSyncedBlock` to be greater than the value of `_l1BlockId` therefore the calulation `numL1Blocks = _l1BlockId - lastSyncedBlock` cannot underflow. Since it cannot underflow we can safely do the calculation in an unchecked block and achieve some gas saving. also the ternary statement `excess = excess > issuance ? excess - issuance : 1` can also be unchecked since the `excess - issuance` subtraction would only occur if `excess` is greater than `issuance`  The diff beolw shows how the code could be refactored: 

```solidity
file: contracts/L2/TaikoL2.sol

252:    function _calc1559BaseFee(
253:        Config memory _config,
254:        uint64 _l1BlockId,
255:        uint32 _parentGasUsed
256:    )
257:        private
258:        view
259:        returns (uint256 basefee_, uint64 gasExcess_)
260:    {
.
.
.
274:            uint256 numL1Blocks;
275:            if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {
276:                numL1Blocks = _l1BlockId - lastSyncedBlock;
277:            }
278:
279:            if (numL1Blocks > 0) {
280:                uint256 issuance = numL1Blocks * _config.gasTargetPerL1Block;
281:                excess = excess > issuance ? excess - issuance : 1;
282:            }
283:
284:            gasExcess_ = uint64(excess.min(type(uint64).max));
.
.
.
297:    }
```

```diff
diff --git a/packages/protocol/contracts/L2/TaikoL2.sol b/packages/protocol/contracts/L2/TaikoL2.sol
index 8ad2c82..e838419 100644
--- a/packages/protocol/contracts/L2/TaikoL2.sol
+++ b/packages/protocol/contracts/L2/TaikoL2.sol
@@ -271,14 +271,16 @@ contract TaikoL2 is CrossChainOwned {
             // because that means this is the first time calculating the basefee
             // and the difference between the L1 height would be extremely big,
             // reverting the initial gas excess value back to 0.
-            uint256 numL1Blocks;
-            if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {
-                numL1Blocks = _l1BlockId - lastSyncedBlock;
-            }
-
-            if (numL1Blocks > 0) {
-                uint256 issuance = numL1Blocks * _config.gasTargetPerL1Block;
-                excess = excess > issuance ? excess - issuance : 1;
+            unchecked {
+                uint256 numL1Blocks;
+                if (lastSyncedBlock > 0 && _l1BlockId > lastSyncedBlock) {
+                    numL1Blocks = _l1BlockId - lastSyncedBlock;
+                }
+
+                if (numL1Blocks > 0) {
+                    uint256 issuance = numL1Blocks * _config.gasTargetPerL1Block;
+                    excess = excess > issuance ? excess - issuance : 1;
+                }
             }

             gasExcess_ = uint64(excess.min(type(uint64).max));
```


2. #### The calculation `uint256 lengthDiff = n - expectedLength` can be unchecked
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L265

The if statement `if (n <= expectedLength) {return input}` ensures that its impossible for the value of `expectedLength` to be greater than the value of `n` therefore the calulation `uint256 lengthDiff = n - expectedLength` cannot underflow. Since it cannot underflow we can safely do the calculation in an unchecked block and achieve some gas saving. The diff beolw shows how the code could be refactored: 

```solidity
file: contracts/automata-attestation/lib/PEMCertChainLib.sol

252:    function _trimBytes(
253:        bytes memory input,
254:        uint256 expectedLength
255:    )
256:        private
257:        pure
258:        returns (bytes memory output)
259:    {
260:        uint256 n = input.length;
261:
262:        if (n <= expectedLength) {
263:            return input;
264:        }
265:        uint256 lengthDiff = n - expectedLength;
266:        output = input.substring(lengthDiff, expectedLength);
267:    }
```

```diff
diff --git a/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol b/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol
index 79c694d..e51d9ba 100644
--- a/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol
+++ b/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol
@@ -262,7 +262,10 @@ contract PEMCertChainLib is IPEMCertChainLib {
         if (n <= expectedLength) {
             return input;
         }
-        uint256 lengthDiff = n - expectedLength;
+        uint256 lengthDiff;
+        unchecked {
+            lengthDiff = n - expectedLength;
+        }
         output = input.substring(lengthDiff, expectedLength);
     }
```



## [G-12] Sort Solidity operations using short-circuit mode
Short-circuiting is a solidity contract development model that uses OR/AND logic to sequence different cost operations. It puts low gas cost operations in the front and high gas cost operations in the back, so that if the front is low If the cost operation is feasible, you can skip (short-circuit) the subsequent high-cost Ethereum virtual machine operation.

//f(x) is a low gas cost operation \
//g(y) is a high gas cost operation 

//Sort operations with different gas costs as follows \
f(x) || g(y) \
f(x) && g(y)

### 1 Instance

1. #### Apply short-circuiting rule to the if statement `if (!skipFeeCheck() && block.basefee != basefee)`
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/TaikoL2.sol#L141


In the `TaikoL2.anchor()` function as shown below we can apply the concept of short-circuiting to the if statement `if (!skipFeeCheck() && block.basefee != basefee)` such that the statement `block.basefee != basefee` is evaluated first (since its gas cost is lesser) before `!skipFeeCheck()` (which is more gas expensive as it involves multiple `JUMP` instruction) so that in scenarios where the statement `block.basefee != basefee` results to false the functions would revert without having to execute the more gas consuming operation `!skipFeeCheck()`. The code could be refactored as shown in the diff below:

```solidity
file: contracts/L2/TaikoL2.sol

107:    function anchor(
108:        bytes32 _l1BlockHash,
109:        bytes32 _l1StateRoot,
110:        uint64 _l1BlockId,
111:        uint32 _parentGasUsed
112:    )
113:        external
114:        nonReentrant
115:    {
.
.
.
139:        uint256 basefee;
140:        (basefee, gasExcess) = _calc1559BaseFee(config, _l1BlockId, _parentGasUsed);
141:        if (!skipFeeCheck() && block.basefee != basefee) {
142:            revert L2_BASEFEE_MISMATCH();
143:        }
.
.
.
158:    }
```

```diff
diff --git a/packages/protocol/contracts/L2/TaikoL2.sol b/packages/protocol/contracts/L2/TaikoL2.sol
index 8ad2c82..af910e9 100644
--- a/packages/protocol/contracts/L2/TaikoL2.sol
+++ b/packages/protocol/contracts/L2/TaikoL2.sol
@@ -138,7 +138,7 @@ contract TaikoL2 is CrossChainOwned {
         // Verify the base fee per gas is correct
         uint256 basefee;
         (basefee, gasExcess) = _calc1559BaseFee(config, _l1BlockId, _parentGasUsed);
-        if (!skipFeeCheck() && block.basefee != basefee) {
+        if (block.basefee != basefee && !skipFeeCheck()) {
             revert L2_BASEFEE_MISMATCH();
         }
```




## [G-13]  Pre-calculate and save the `1_000_000_000 ether / 10_000` equation which contain only constant values to a constant variable
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol#L124

Rather than having the `proposalThreshold()` function to compute the value of `1_000_000_000 ether / 10_000` every time the function is called the we coud pre-calculate the value and assign the result to a constant variable (since the calculation involves only constant values) which would then be saved to the contracts byte code then make the `proposalThreshold()` function return this constant variable. The diff below shows how the function coud be refactored: 

```solidity
file: contracts/L1/gov/TaikoGovernor.sol

123:    function proposalThreshold() public pure override returns (uint256) {
124:        return 1_000_000_000 ether / 10_000; // 0.01% of Taiko Token
125:    }
```

```diff
diff --git a/packages/protocol/contracts/L1/gov/TaikoGovernor.sol b/packages/protocol/contracts/L1/gov/TaikoGovernor.sol
index 6a44820..687e432 100644
--- a/packages/protocol/contracts/L1/gov/TaikoGovernor.sol
+++ b/packages/protocol/contracts/L1/gov/TaikoGovernor.sol
@@ -22,6 +22,8 @@ contract TaikoGovernor is
 {
     uint256[50] private __gap;

+    uint256 private constant PRPOSAL_THRESHOLD = 1_000_000_000 ether / 10_000; // 0.01% of Taiko Token
+
     error TG_INVALID_SIGNATURES_LENGTH();

     /// @notice Initializes the contract.
@@ -121,7 +123,7 @@ contract TaikoGovernor is
     /// @notice The number of votes required in order for a voter to become a proposer.
     /// @return The number of votes required.
     function proposalThreshold() public pure override returns (uint256) {
-        return 1_000_000_000 ether / 10_000; // 0.01% of Taiko Token
+        return PRPOSAL_THRESHOLD;
     }

     function _execute(
```




## [G-14]  Move lesser gas costing  checks to the top
Revert() statements that check input arguments or cost lesser gas should be at the top of the function.
Checks that involve constants should come before checks that involve state variables, function calls, and calculations. By doing these checks first, the function is able to revert before wasting alot of gas in a function that may ultimately revert in the unhappy case.

### Instances
1. #### Move the `if (!_op.token.supportsInterface(ERC1155_INTERFACE_ID)) {revert VAULT_INTERFACE_NOT_SUPPORTED()} ` check to the top of the function.
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L39-#L90

We can make the `sendToken()` function more gas efficient by moving the if-revert statement `if (!_op.token.supportsInterface(ERC1155_INTERFACE_ID)) {revert VAULT_INTERFACE_NOT_SUPPORTED()}` to the top of the function so that in scenarios where the cheaper revert statement fails the function would revert without having to perform an operation on aloop which could be expensive. The diff below shows how the code should be refactored:

```solidity
file: contracts/tokenvault/ERC1155Vault.sol

39:    function sendToken(BridgeTransferOp memory _op)
40:        external
41:        payable
42:        nonReentrant
43:        whenNotPaused
44:        withValidOperation(_op)
45:        returns (IBridge.Message memory message_)
46:    {
47:        for (uint256 i; i < _op.amounts.length; ++i) {
48:            if (_op.amounts[i] == 0) revert VAULT_INVALID_AMOUNT();
49:        }
50:        // Check token interface support
51:        if (!_op.token.supportsInterface(ERC1155_INTERFACE_ID)) {    //@audit move check to function top
52:            revert VAULT_INTERFACE_NOT_SUPPORTED();
53:        }
.
.
.
90:    }
```

```diff
diff --git a/packages/protocol/contracts/tokenvault/ERC1155Vault.sol b/packages/protocol/contracts/tokenvault/ERC1155Vault.sol
index 5b98948..afa00fc 100644
--- a/packages/protocol/contracts/tokenvault/ERC1155Vault.sol
+++ b/packages/protocol/contracts/tokenvault/ERC1155Vault.sol
@@ -44,13 +44,16 @@ contract ERC1155Vault is BaseNFTVault, ERC1155ReceiverUpgradeable {
         withValidOperation(_op)
         returns (IBridge.Message memory message_)
     {
+
+        if (!_op.token.supportsInterface(ERC1155_INTERFACE_ID)) {
+            revert VAULT_INTERFACE_NOT_SUPPORTED();
+        }
+
         for (uint256 i; i < _op.amounts.length; ++i) {
             if (_op.amounts[i] == 0) revert VAULT_INVALID_AMOUNT();
         }
         // Check token interface support
-        if (!_op.token.supportsInterface(ERC1155_INTERFACE_ID)) {
-            revert VAULT_INTERFACE_NOT_SUPPORTED();
-        }
+

         (bytes memory data, CanonicalNFT memory ctoken) = _handleMessage(msg.sender, _op);
```



2. #### Move the `if (!_op.token.supportsInterface(ERC721_INTERFACE_ID)) {revert VAULT_INTERFACE_NOT_SUPPORTED()} ` check to the top of the function.
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L26-#L74

We can make the `sendToken()` function more gas efficient by moving the if-revert statement `if (!_op.token.supportsInterface(ERC721_INTERFACE_ID)) {revert VAULT_INTERFACE_NOT_SUPPORTED()}` to the top of the function so that in scenarios where the cheaper revert statement fails the function would revert without having to perform an operation on aloop which could be expensive. The diff below shows how the code should be refactored:

```solidity
file: contracts/tokenvault/ERC721Vault.sol

26:    function sendToken(BridgeTransferOp memory _op)
27:        external
28:        payable
29:        nonReentrant
30:        whenNotPaused
31:        withValidOperation(_op)
32:        returns (IBridge.Message memory message_)
33:    {
34:        for (uint256 i; i < _op.tokenIds.length; ++i) {
35:            if (_op.amounts[i] != 0) revert VAULT_INVALID_AMOUNT();
36:        }
37:
38:        if (!_op.token.supportsInterface(ERC721_INTERFACE_ID)) {    //@audit move check to function top
39:            revert VAULT_INTERFACE_NOT_SUPPORTED();
40:        }
.
.
.
74:    }
```

```diff
diff --git a/packages/protocol/contracts/tokenvault/ERC721Vault.sol b/packages/protocol/contracts/tokenvault/ERC721Vault.sol
index 71dc04e..b2410e2 100644
--- a/packages/protocol/contracts/tokenvault/ERC721Vault.sol
+++ b/packages/protocol/contracts/tokenvault/ERC721Vault.sol
@@ -31,14 +31,15 @@ contract ERC721Vault is BaseNFTVault, IERC721Receiver {
         withValidOperation(_op)
         returns (IBridge.Message memory message_)
     {
-        for (uint256 i; i < _op.tokenIds.length; ++i) {
-            if (_op.amounts[i] != 0) revert VAULT_INVALID_AMOUNT();
-        }

         if (!_op.token.supportsInterface(ERC721_INTERFACE_ID)) {
             revert VAULT_INTERFACE_NOT_SUPPORTED();
         }

+        for (uint256 i; i < _op.tokenIds.length; ++i) {
+            if (_op.amounts[i] != 0) revert VAULT_INVALID_AMOUNT();
+        }
+
         (bytes memory data, CanonicalNFT memory ctoken) = _handleMessage(msg.sender, _op);

         IBridge.Message memory message = IBridge.Message({
```



## [G-15] Calculations should be memoized rather than re-calculating them
In computing, memoization or memoisation is an optimization technique used primarily to speed up computer programs by storing the results of expensive function calls to pure functions and returning the cached result when the same inputs occur again.

### Instances
1. #### We can memoize the computations of `der.bytesAt(extnValueOidPtr)` 
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L306-#L316

We can reduce the gas usage of the `_findPckTcbInfo()` function by memoizing the computations of `der.bytesAt(extnValueOidPtr)` i.e cache the result of the computation so that for subsequent computations we can use the cached value rather than having to recompute the values. It is also important to note that the multiple computations `der.bytesAt(extnValueOidPtr)` is done inside a loop so it ends up consuming even more gas the more reason why memoizing the computation is important and gas efficient. The diff below shows how the code could be refactored:

```solidity
file: contracts/automata-attestation/lib/PEMCertChainLib.sol

269:    function _findPckTcbInfo(
270:        bytes memory der,
271:        uint256 tbsPtr,
272:        uint256 tbsParentPtr
273:    )
274:        private
275:        pure
276:        returns (
277:            bool success,
278:            uint256 pcesvn,
279:            uint256[] memory cpusvns,
280:            bytes memory fmspcBytes,
281:            bytes memory pceidBytes
282:        )
283:    {
.
.
.
301:                while (!(flags.fmspcFound && flags.pceidFound && flags.tcbFound)) {
302:                    uint256 extnValueOidPtr = der.firstChildOf(extnValuePtr);
303:                    if (der[extnValueOidPtr.ixs()] != 0x06) {
304:                        return (false, pcesvn, cpusvns, fmspcBytes, pceidBytes);
305:                    }
306:                    if (BytesUtils.compareBytes(der.bytesAt(extnValueOidPtr), TCB_OID)) {   //@audit memoize der.bytesAt(extnValueOidPtr)
307:                        // 1.2.840.113741.1.13.1.2
308:                        (flags.tcbFound, pcesvn, cpusvns) = _findTcb(der, extnValueOidPtr);
309:                    }
310:                    if (BytesUtils.compareBytes(der.bytesAt(extnValueOidPtr), PCEID_OID)) {   //@audit memoize der.bytesAt(extnValueOidPtr)
311:                        // 1.2.840.113741.1.13.1.3
312:                        uint256 pceidPtr = der.nextSiblingOf(extnValueOidPtr);
313:                        pceidBytes = der.bytesAt(pceidPtr);
314:                        flags.pceidFound = true;
315:                    }
316:                    if (BytesUtils.compareBytes(der.bytesAt(extnValueOidPtr), FMSPC_OID)) {   //@audit memoize der.bytesAt(extnValueOidPtr)
317:                        // 1.2.840.113741.1.13.1.4
318:                        uint256 fmspcPtr = der.nextSiblingOf(extnValueOidPtr);
319:                        fmspcBytes = der.bytesAt(fmspcPtr);
320:                        flags.fmspcFound = true;
321:                    }
322:
323:                    if (extnValuePtr.ixl() < extnValueParentPtr.ixl()) {
324:                        extnValuePtr = der.nextSiblingOf(extnValuePtr);
325:                    } else {
326:                        break;
327:                    }
328:                }
.
.
.
339:    }
```

```diff
diff --git a/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol b/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol
index 79c694d..ebc3c86 100644
--- a/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol
+++ b/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol
@@ -300,20 +300,21 @@ contract PEMCertChainLib is IPEMCertChainLib {

                 while (!(flags.fmspcFound && flags.pceidFound && flags.tcbFound)) {
                     uint256 extnValueOidPtr = der.firstChildOf(extnValuePtr);
+                    bytes memory extnValueOidPtrBytes = der.bytesAt(extnValueOidPtr);
                     if (der[extnValueOidPtr.ixs()] != 0x06) {
                         return (false, pcesvn, cpusvns, fmspcBytes, pceidBytes);
                     }
-                    if (BytesUtils.compareBytes(der.bytesAt(extnValueOidPtr), TCB_OID)) {
+                    if (BytesUtils.compareBytes(extnValueOidPtrBytes, TCB_OID)) {
                         // 1.2.840.113741.1.13.1.2
                         (flags.tcbFound, pcesvn, cpusvns) = _findTcb(der, extnValueOidPtr);
                     }
-                    if (BytesUtils.compareBytes(der.bytesAt(extnValueOidPtr), PCEID_OID)) {
+                    if (BytesUtils.compareBytes(extnValueOidPtrBytes, PCEID_OID)) {
                         // 1.2.840.113741.1.13.1.3
                         uint256 pceidPtr = der.nextSiblingOf(extnValueOidPtr);
                         pceidBytes = der.bytesAt(pceidPtr);
                         flags.pceidFound = true;
                     }
-                    if (BytesUtils.compareBytes(der.bytesAt(extnValueOidPtr), FMSPC_OID)) {
+                    if (BytesUtils.compareBytes(extnValueOidPtrBytes, FMSPC_OID)) {
                         // 1.2.840.113741.1.13.1.4
                         uint256 fmspcPtr = der.nextSiblingOf(extnValueOidPtr);
                         fmspcBytes = der.bytesAt(fmspcPtr);
```


2. ####  We can memoize the computations of `ptr.ixf()`
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L112

We can reduce the gas usage of the `bytesAt()` function by memoizing the computation of `ptr.ixf()` i.e cache the results of the computation so that for subsequent computation we can use the cached value rather than having to recompute the value. The diff below shows how the code could be refactored:

```solidity
file: contracts/automata-attestation/utils/Asn1Decode.sol

111:    function bytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes memory) {
112:        return der.substring(ptr.ixf(), ptr.ixl() + 1 - ptr.ixf());    //@audit memoize the ptr.ixf()
113:    }
```

```diff
diff --git a/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol b/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol
index 17b2fbd..b731011 100644
--- a/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol
+++ b/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol
@@ -109,7 +109,8 @@ library Asn1Decode {
     * @return Value bytes of node
     */
     function bytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes memory) {
-        return der.substring(ptr.ixf(), ptr.ixl() + 1 - ptr.ixf());
+        uint256 _ptrIxl = ptr.ixf();
+        return der.substring(_ptrIxl, ptr.ixl() + 1 - _ptrIxl);
     }

     /*
```

3. ####  We can memoize the computations of `ptr.ixs()`
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L122

We can reduce the gas usage of the `allBytesAt()` function by memoizing the computation of `ptr.ixs()` i.e cache the results of the computation so that for subsequent computation we can use the cached value rather than having to recompute the value. The diff below shows how the code could be refactored:

```solidity
file: contracts/automata-attestation/utils/Asn1Decode.sol

121:    function allBytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes memory) {
122:        return der.substring(ptr.ixs(), ptr.ixl() + 1 - ptr.ixs());  //@audit memoize the ptr.ixs()
123:    }
```

```diff
diff --git a/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol b/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol
index 17b2fbd..fd3dc36 100644
--- a/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol
+++ b/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol
@@ -119,7 +119,8 @@ library Asn1Decode {
     * @return All bytes of node
     */
     function allBytesAt(bytes memory der, uint256 ptr) internal pure returns (bytes memory) {
-        return der.substring(ptr.ixs(), ptr.ixl() + 1 - ptr.ixs());
+        uint256 _ptrIxs = ptr.ixs();
+        return der.substring(_ptrIxs, ptr.ixl() + 1 - _ptrIxs);
     }
```

### Other similar instances
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L141-#L146
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L154-#L163
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L166
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L170
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L179-#L185




## [G-16]  Low level call can be optimized with assembly
returnData is copied to memory even if the variable is not utilized: the proper way to handle this is through a low level assembly call.

### 1 Instances
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L2/CrossChainOwned.sol#L50
```solidity
file: contracts/L2/CrossChainOwned.sol

36:    function onMessageInvocation(bytes calldata _data)
37:        external
38:        payable
39:        whenNotPaused
40:        onlyFromNamed("bridge")
41:    {
42:        (uint64 txId, bytes memory txdata) = abi.decode(_data, (uint64, bytes));
43:        if (txId != nextTxId) revert XCO_INVALID_TX_ID();
44:
45:        IBridge.Context memory ctx = IBridge(msg.sender).context();
46:        if (ctx.srcChainId != ownerChainId || ctx.from != owner()) {
47:            revert XCO_PERMISSION_DENIED();
48:        }
49:
50:        (bool success,) = address(this).call(txdata); 
51:        if (!success) revert XCO_TX_REVERTED();
52:
53:        emit TransactionExecuted(nextTxId++, bytes4(txdata));
54:    }
```



## [G-17]  Use custom error instead of assert
In using the assert() function, when the conditions results to false all the changes made to the contract would be reverted all the remaining gas of the transaction would be consumed.
Meanwhile, in using an if revert custom error, when the condition in the if-statement results to true would revert all the changes made to the contract and does a refund all the remaining gas fees of the transaction.

### Instances
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L486
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L25
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L26
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L27
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L37-#L40
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L56-#L59
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L61-#L64
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L112-#L115
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L117-#L120
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L152-#L155
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L172-#L175
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L182-#L185
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L192-#L195
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L202-#L205
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L212-#L215
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L217-#L220
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L228-#L231
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L238-#L241
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L248-#L251
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L258-#L261
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L263-#L266
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L77
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L89
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L93-#L96
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L99-#L102
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L105-#L108
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L119-#L122
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L125-#L128
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L150-#L153
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L162-#L165
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L172-#L175
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L178-#L181
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L77-#L81
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L82-#L86
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L87-#L90
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L91-#L93
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L94-#L99
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L100-#L104
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L116
- https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L279

































## CONCLUSION
As you embark on incorporating the recommended optimizations, we want to emphasize the utmost importance of proceeding with vigilance and dedicating thorough efforts to comprehensive testing. It is of paramount significance to ensure that the proposed alterations do not inadvertently introduce fresh vulnerabilities, while also successfully achieving the anticipated enhancements in performance.

We strongly advise conducting a meticulous and exhaustive evaluation of the modifications made to the codebase. This rigorous scrutiny and exhaustive assessment will play a pivotal role in affirming both the security and efficacy of the refactored code. Your careful attention to detail, coupled with the implementation of a robust testing framework, will provide the necessary assurance that the refined code aligns with your security objectives and effectively fulfills the intended performance optimizations.
