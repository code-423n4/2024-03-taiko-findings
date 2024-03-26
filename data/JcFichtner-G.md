## [G-01] Optimizing `onlyFromOwnerOrNamed` modifier

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol

The `onlyFromOwnerOrNamed` modifier is designed to restrict function access to either the contract owner or an address that resolves to a specific name within the `AddressResolver`. The current implementation checks both conditions simultaneously, which can be inefficient because the `resolve()` function call might involve more computation or even state access, which is more expensive in terms of gas usage.

**Here's a detailed breakdown of the optimization**

**1 - Current Implementation:**

> if (msg.sender != owner() && msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();

This line checks if msg.sender is neither the owner nor a resolved address and reverts if both conditions are true.

**2 - Optimization:**

> if (msg.sender != owner()) {
    if (msg.sender != resolve(_name, true)) revert RESOLVER_DENIED();
}

With this optimization, the contract first checks if `msg.sender` is the `owner`. If this is true, the function execution continues without calling `resolve()`, saving gas.

**3 - Why It Saves Gas:**

- **Owner Check:** The `owner()` function typically returns a state variable, which is a relatively cheap operation in terms of gas.

- **Resolve Check:** The `resolve()` function may involve more complex logic and potentially additional state reads, which are more expensive.

## [G-02] Using `constants` for `votingDelay()`, `votingPeriod()`, and `proposalThreshold()`.

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/gov/TaikoGovernor.sol

In the given contract, `votingDelay()`, `votingPeriod()`, and `proposalThreshold()` are pure functions that return hardcoded values. Since these values are not intended to change, they can be declared as constants.

   > function votingDelay() public pure override returns (uint256) {
        return 7200; // 1 day
    }

    
   > function votingPeriod() public pure override returns (uint256) {
        return 50_400; // 1 week
    }

    
   > function proposalThreshold() public pure override returns (uint256) {
        return 1_000_000_000 ether / 10_000; // 0.01% of Taiko Token

**Here's how you might implement this:**

> uint256 public constant VOTING_DELAY = 7200;
> uint256 public constant VOTING_PERIOD = 50400;
> uint256 public constant PROPOSAL_THRESHOLD = 1000000000 ether / 10000;

Using `constants` instead of `pure` functions with hardcoded return values can reduce the contract size, which can lead to lower deployment costs.

## [G-03] Unnecessary Checks

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/libs/LibDepositing.sol

The _encodeEthDeposit() function is designed to encode an Ethereum deposit into a single uint256 value, where the higher bits represent the depositor's address and the lower bits represent the deposit amount. This encoding is used to efficiently store deposit information in the contract's state.

Within _encodeEthDeposit(), there is a check to ensure that the _amount being encoded does not exceed the maximum value that can be represented by a uint96 data type, which is 2^96 - 1. If _amount were to exceed this value, it would not fit into the designated bits for the amount in the encoded deposit, potentially leading to incorrect data storage and processing.

However, before _encodeEthDeposit() is called, the depositEtherToL2() function invokes canDepositEthToL2(), which includes its own set of validations on the deposit amount. Specifically, canDepositEthToL2() checks that the _amount is within the range defined by _config.ethDepositMinAmount and _config.ethDepositMaxAmount, which should be within the bounds of a uint96.

If the configuration guarantees that _config.ethDepositMaxAmount is less than or equal to type(uint96).max, then the check in _encodeEthDeposit() becomes redundant because _amount has already been confirmed to be within the uint96 range. In this case, removing the check could save gas since the Solidity compiler would no longer need to include the code for this check in the compiled contract, reducing the contract's size and deployment costs.








 












