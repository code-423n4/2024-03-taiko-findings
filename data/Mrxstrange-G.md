## Use named returns for local variables of pure functions where it is possible

## Description

- Streamline return values: A simple yet effective optimisation technique is to name the return value in a function, eliminating the need for a separate local variable. For instance, in a function that calculates a product, you can directly name the return value, streamlining the process

## Proof of Concept

```
library NamedReturnArithmetic {

    function sum(uint256 num1, uint256 num2) internal pure returns(uint256 theSum){
        theSum = num1 + num2;
    }
}
contract NamedReturn {
    using NamedReturnArithmetic for uint256;
    uint256 public stateVar;
    function add2State(uint256 num) public {
        stateVar = stateVar.sum(num);
    }
}

######RUN######

test for test/NamedReturn.t.sol:NamedReturnTest
[PASS] test_Increment() (gas: 27613)

------------------------------------------------------------------------

library NoNamedReturnArithmetic {

    function sum(uint256 num1, uint256 num2) internal pure returns(uint256){
        return num1 + num2;
    }
}
contract NoNamedReturn {
    using NoNamedReturnArithmetic for uint256;
    uint256 public stateVar;
    function add2State(uint256 num) public {
        stateVar = stateVar.sum(num);
    }
}

######RUN######

test for test/NoNamedReturn.t.sol:NamedReturnTest
[PASS] test_Increment() (gas: 27639)

```

There are many instances of this issue:

https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L149


https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L449


https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L170


https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L201
