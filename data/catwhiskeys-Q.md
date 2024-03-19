## `@openzeppelin::ERC20SnapshotUpgradeable.sol` contract is not available

### Instance:
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L5

I tried to run `forge test` command I've got such error message:
```
[⠊] Compiling...2024-03-18T13:12:02.759579Z ERROR foundry_compilers::artifacts: error="/home/user/Documents/audit/taiko/packages/protocol/lib/openzeppelin-contracts-upgradeable/contracts/token/ERC20/extensions/ERC20SnapshotUpgradeable.sol": No such file or directory (os error 2)
[⠒] Compiling...
Error: 
failed to resolve file: "/home/user/Documents/audit/taiko/packages/protocol/lib/openzeppelin-contracts-upgradeable/contracts/token/ERC20/extensions/ERC20SnapshotUpgradeable.sol": No such file or directory (os error 2); check configured remappings
        --> /home/user/Documents/audit/taiko/packages/protocol/contracts/L1/TaikoToken.sol
        @openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20SnapshotUpgradeable.sol
```
It's because it coudn't import:
`import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20SnapshotUpgradeable.sol";`
        
I tried to search `ERC20SnapshotUpgradeable.sol` in internet, and I also couldn't find it, even on openzeppelin's official github:
https://github.com/OpenZeppelin/openzeppelin-contracts-upgradeable/blob/v5.0.2/contracts/token/ERC20/extensions

## Impact
Usage of degraded contract or of the contract that is not available any more.

## Recommended mitigation steps
Consider reviewing your dependencies, maybe `@openzeppelin::ERC20SnapshotUpgradeable.sol` is degraded, and it was pulled out of openzeppelin's official contracts.