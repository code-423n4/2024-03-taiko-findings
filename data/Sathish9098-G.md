# GAS OPTIMIZATION REPORTS

##

## [G-] Optimizing gas usage by caching state variables in local memory variables

The instances below point to the second+ access of a state variable within a function. Caching of a state variable replace each Gwarmaccess (100 gas) with a much cheaper stack read. Other less obvious fixes/optimizations include having local memory caches of state variable structs, or having local caches of state variable contracts/addresses. Most of the times this if statement will be true and we will save 100 gas at a small possibility of 3 gas loss

### [G-1.1] ``addressManager`` can be cached . Saves ``100 GAS`` , ``1 SLOD``

```diff
FILE: 2024-03-taiko/packages/protocol/contracts/common/AddressResolver.sol

+  address addressManager_= addressManager ;
- if (addressManager == address(0)) revert RESOLVER_INVALID_MANAGER();
+ if (addressManager_== address(0)) revert RESOLVER_INVALID_MANAGER();
-        addr_ = payable(IAddressManager(addressManager).getAddress(_chainId, _name));
+        addr_ = payable(IAddressManager(addressManager_).getAddress(_chainId, _name));

        if (!_allowZeroAddress && addr_ == address(0)) {
            revert RESOLVER_ZERO_ADDR(_chainId, _name);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressResolver.sol#L81-L83

### [G-1.2] ``gasExcess`` can be cached . Saves ``100 GAS`` , ``1 SLOD``

```diff
FILE

``

## 

## [G-] 

