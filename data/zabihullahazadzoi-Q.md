### Low risk and Non-Critical issues


## [L-1] NFT doesn't handle hard forks
When there are hard forks, users often have to go through [many hoops](https://twitter.com/elerium115/status/1558471934924431363) to ensure that they control ownership on every fork. Consider adding `require(1 == chain.chainId)`, or the chain ID of whichever chain you prefer, to the functions below, or at least include the chain ID in the URI, so that there is no confusion about which chain is the owner of the NFT.

**Total Instances:** 1

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

 107:     function tokenURI(uint256 _tokenId) public view virtual override returns (string memory) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L107


## [L-2] Addition/multiplication in `unchecked` block is unsafe
The additions/multiplications may silently overflow because they’re in `unchecked` blocks with no preceding value checks, which may lead to unexpected results.

**Total Instances:** 3

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

 178:                 uint256 bondToReturn = uint256(ts.validityBond) + blk.livenessBond;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L178

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

 234:             for (uint256 i; i < 255 && _blockId >= i + 1; ++i) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L234

```solidity
File: packages/protocol/contracts/thirdparty/optimism/Bytes.sol

 25:             require(_length + 31 >= _length, "slice_overflow");
                require(_start + _length >= _start, "slice_overflow");
                require(_bytes.length >= _start + _length, "slice_outOfBounds");

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/Bytes.sol#L25


## [L-3] Array is `push()ed` but not `pop()ed`
Array entries are added but are never removed. Consider whether this should be the case, or whether there should be a maximum, or whether old entries should be removed. Cases where there are specific potential problems will be flagged separately under a different issue.

**Total Instances:** 1

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

 87:             guardians.push(guardian);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L87


## [L-4] Code does not follow the best practice of check-effects-interaction
Code should follow the best-practice of [check-effects-interaction](https://blockchain-academy.hs-mittweida.de/courses/solidity-coding-beginners-to-intermediate/lessons/solidity-11-coding-patterns/topic/checks-effects-interactions/), where state variables are updated before any external calls are made. Doing so prevents a large class of reentrancy bugs.

**Total Instances:** 2

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

 /// @audit  syncChainData() prior to this assignment
 151:             lastSyncedBlock = _l1BlockId;

 /// @audit  syncChainData() prior to this assignment
 151:             lastSyncedBlock = _l1BlockId;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L151


## [L-5] Consider implementing two-step procedure for updating protocol addresses
A copy-paste error or a typo may end up bricking protocol functionality, or sending tokens to an address with no known private key. Consider implementing a two-step procedure for updating protocol addresses, where the recipient is set as pending, and must "accept" the assignment by making an affirmative call. A straight forward way of doing this would be to have the target contracts implement [EIP-165](https://eips.ethereum.org/EIPS/eip-165), and to have the "set" functions ensure that the recipient is of the right interface type.

**Total Instances:** 5

```solidity
File: packages/protocol/contracts/common/AddressManager.sol

 38:     function setAddress(
            uint64 _chainId,
            bytes32 _name,
            address _newAddress
        )
            external
            virtual
            onlyOwner
        {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressManager.sol#L38

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

 80:     function setSnapshoter(address _snapshooter) external onlyOwner {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L80

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

 36:     function changeMigrationStatus(
            address _migratingAddress,
            bool _migratingInbound
        )
            external
            nonReentrant
            whenNotPaused
            onlyFromOwnerOrNamed("erc20_vault")
        {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L36

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

 148:     function changeBridgedToken(
             CanonicalERC20 calldata _ctoken,
             address _btokenNew
         )
             external
             nonReentrant
             whenNotPaused
             onlyOwner
             returns (address btokenOld_)
         {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L148

```solidity
File: packages/protocol/contracts/tokenvault/IBridgedERC20.sol

 24:     function changeMigrationStatus(address _addr, bool _inbound) external;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/IBridgedERC20.sol#L24


## [L-6] Empty `receive()`/`fallback()` function
If the intention is for Ether sent by a caller to be used for an actual purpose (i.e. the function is not just a WETH `withdraw()` handler), the function should call another function (e.g. call `weth.deposit()` and use the token on the caller’s behalf) or at least emit an event to track that funds were sent directly to it.

**Total Instances:** 1

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 70:     receive() external payable { }

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L70


## [L-7] Function can return unassigned variable
Make sure that functions with a return value always return a valid and assigned value. Even if the default value is as expected, it should be assigned with the default value for code clarity and to reduce confusion.

**Total Instances:** 7

```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

 /// @audit  customConfig is unassigned!
 44:         return customConfig;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L44

```solidity
File: packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol

 /// @audit  input is unassigned!
 263:             return input;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L263

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 /// @audit  __ctx is unassigned!
 567:             return __ctx;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L567

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

 /// @audit  _amount is unassigned!
 256:         if (_start == 0) return _amount;

 /// @audit  _amount is unassigned!
 259:         if (_period == 0) return _amount;

 /// @audit  _amount is unassigned!
 260:         if (block.timestamp >= _start + _period) return _amount;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L256

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

 /// @audit  __srcDecimals is unassigned!
 119:         return __srcDecimals;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L119


## [L-8] Functions calling contracts/addresses with transfer hooks should be protected by reentrancy guard
Even if the function follows the best practice of check-effects-interaction, not using a reentrancy guard when there may be transfer hooks opens the users of this protocol up to [read-only reentrancy vulnerability](https://chainsecurity.com/curve-lp-oracle-manipulation-post-mortem/) with no way to protect them except by block-listing the entire protocol.

**Total Instances:** 4

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

 219:         IERC20(taikoToken).transferFrom(sharedVault, _to, amountToWithdraw);

 220:         IERC20(costToken).safeTransferFrom(_recipient, sharedVault, costToWithdraw);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L219

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

 91:         IERC20(token).transferFrom(vault, user, amount);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L91

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

 330:             IERC20(token_).safeTransfer(_to, _amount);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L330


## [L-9] Governance functions should be controlled by time locks
Governance functions (such as upgrading contracts, setting critical parameters) should be controlled using time locks to introduce a delay between a proposal and its execution. This gives users time to exit before a potentially dangerous or malicious operation is applied.

**Total Instances:** 4

```solidity
File: packages/protocol/contracts/L1/provers/Guardians.sol

 53:     function setGuardians(
            address[] memory _newGuardians,
            uint8 _minGuardians
        )
            external
            onlyOwner
            nonReentrant
        {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/provers/Guardians.sol#L53

```solidity
File: packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol

 25:     function setConfigAndExcess(
            Config memory _newConfig,
            uint64 _newGasExcess
        )
            external
            virtual
            onlyOwner
        {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2EIP1559Configurable.sol#L25

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

 80:     function setSnapshoter(address _snapshooter) external onlyOwner {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L80

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

 36:     function changeMigrationStatus(
            address _migratingAddress,
            bool _migratingInbound
        )
            external
            nonReentrant
            whenNotPaused
            onlyFromOwnerOrNamed("erc20_vault")
        {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L36


## [L-10] Missing checks for `address(0x0)` in the constructor
'Constructors often take address parameters to initialize important components of a contract, such as owner or linked contracts. However, without a checking, there's a risk that an address parameter could be mistakenly set to the zero address (0x0). This could be due to an error or oversight during contract deployment. A zero address in a crucial role can cause serious issues, as it cannot perform actions like a normal address, and any funds sent to it will be irretrievable. It's therefore crucial to include a zero address check in constructors to prevent such potential problems. If a zero address is detected, the constructor should revert the transaction.'

**Total Instances:** 2

```solidity
File: packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

 /// @audit  sigVerifyLibAddr, pemCertLibAddr not checked!
 54:     constructor(address sigVerifyLibAddr, address pemCertLibAddr) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L54

```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

 /// @audit  es256Verifier not checked!
 20:     constructor(address es256Verifier) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L20


## [L-11] Missing checks for address(0x0) when updating address state variables
Consider adding a zero address check when updating address state variables.

**Total Instances:** 18

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 549:             __ctx = Context(_msgHash, _from, _srcChainId);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L549

```solidity
File: packages/protocol/contracts/common/AddressManager.sol

 49:         __addresses[_chainId][_name] = _newAddress;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/AddressManager.sol#L49

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

 122:         taikoToken = _taikoToken;

 125:         costToken = _costToken;

 128:         sharedVault = _sharedVault;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L122

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

 41:         token = _token;

 42:         vault = _vault;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L41

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

 69:         token = _token;

 70:         vault = _vault;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L69

```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

 39:         token = _token;

 40:         vault = _vault;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L39

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC1155.sol

 56:         srcToken = _srcToken;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC1155.sol#L56

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20.sol

 73:         srcToken = _srcToken;

 81:         snapshooter = _snapshooter;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20.sol#L73

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC20Base.sol

 49:         migratingAddress = _migratingAddress;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC20Base.sol#L49

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

 47:         srcToken = _srcToken;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L47

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

 189:         canonicalToBridged[_ctoken.chainId][_ctoken.addr] = _btokenNew;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L189

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

 229:         instances[id] = Instance(newInstance, uint64(block.timestamp));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L229


## [L-12] Missing contract-existence checks before low-level calls
Low-level calls return success if there is no code present at the specified address. In addition to the zero-address checks, add a check to verify that `<address>.code.length > 0`

**Total Instances:** 4

```solidity
File: packages/protocol/contracts/L2/CrossChainOwned.sol

 50:         (bool success,) = address(this).call(txdata);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/CrossChainOwned.sol#L50

```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

 137:         (bool success, bytes memory ret) = ES256VERIFIER.staticcall(args);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L137

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 591:         (success_,) = _signalService.staticcall(data);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L591

```solidity
File: packages/protocol/contracts/libs/Lib4844.sol

 43:         (bool ok, bytes memory ret) = POINT_EVALUATION_PRECOMPILE_ADDRESS.staticcall(

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/libs/Lib4844.sol#L43


## [L-13] Missing contract-existence checks before yul `call()`
Low-level calls return success if there is no code present at the specified address. In addition to the zero-address checks, add a check to verify that `extcodesize()` is non-zero.

**Total Instances:** 1

```solidity
File: packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol

 45:                 call(

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L45


## [L-14] Missing disallow list for `ERC721`
'Recently, there has been an increase in the theft of NFTs. These stolen NFTs are then added to platforms where they can be easily converted into liquidity. Some popular marketplaces(e.g. Opensea), have already taken steps to combat this problem by introducing a disallow list feature. This means that if an NFT is reported as stolen, it won't be listed or sold on their platform. This may increase the centralization of the project, but it can help solve this problem if it is a concern.'

**Total Instances:** 2

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

 12: contract BridgedERC721 is EssentialContract, ERC721Upgradeable {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L12

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

 16: contract ERC721Vault is BaseNFTVault, IERC721Receiver {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L16


## [L-15] `receive()`/`payable fallback()` function does not authorize requests
Having no access control on the function (e.g. `require(msg.sender == address(weth))`) means that someone may send Ether to the contract, and have no way to get anything back out, which is a loss of funds. If the concern is having to spend a small amount of gas to check the sender against an immutable address, the code should at least have a function to rescue mistakenly-sent Ether.

**Total Instances:** 2

```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

 34:     receive() external payable {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L34

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 70:     receive() external payable { }

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L70


## [L-16] `require()` should be used instead of `assert()`
Prior to solidity version 0.8.0, hitting an assert consumes the remainder of the transaction’s available gas rather than returning it, as `require()`/`revert()` do. `assert()` should be avoided even past solidity version 0.8.0 as its [documentation](https://docs.soliditylang.org/en/v0.8.14/control-structures.html#panic-via-assert-and-error-via-require) states that “The assert function creates an error of type Panic(uint256). … Properly functioning code should never create a Panic, not even on invalid external input. If this happens, then there is a bug in your contract which you should fix”.

**Total Instances:** 4

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

 223:                 assert(tier.validityBond == 0);

 224:                 assert(ts.validityBond == 0 && ts.contestBond == 0 && ts.contester == address(0));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L223

```solidity
File: packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

 138:         assert(success); // never reverts, always returns 0 or 1

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L138

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 486:         assert(_message.from != address(this));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L486


## [L-17] Revert on transfer to the zero address
It’s good practice to revert a token transfer transaction if the recipient’s address is the zero address. This can prevent unintentional transfers to the zero address due to accidental operations or programming errors. Many token contracts implement such a safeguard, such as `OpenZeppelin - ERC20`, `OpenZeppelin - ERC721`.

**Total Instances:** 8

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

 114:             IERC20(assignment.feeToken).safeTransferFrom(
                     _meta.coinbase, _blk.assignedProver, proverFee

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L114

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

 219:         IERC20(taikoToken).transferFrom(sharedVault, _to, amountToWithdraw);

 220:         IERC20(costToken).safeTransferFrom(_recipient, sharedVault, costToWithdraw);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L219

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

 63:         IERC20(token).transferFrom(vault, user, amount);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L63

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

 91:         IERC20(token).transferFrom(vault, user, amount);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L91

```solidity
File: packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol

 60:             IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC721Airdrop.sol#L60

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

 330:             IERC20(token_).safeTransfer(_to, _amount);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L330

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

 171:                 IERC721(token_).safeTransferFrom(address(this), _to, _tokenIds[i]);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L171


## [L-18] Some tokens may revert when large transfers are made
Tokens such as COMP or UNI will revert when an address’ balance reaches `type(uint96).max`. Ensure that the calls below can be broken up into smaller batches if necessary.

**Total Instances:** 7

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

 /// @audit  onBlockProposed()
 114:             IERC20(assignment.feeToken).safeTransferFrom(

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L114

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

 /// @audit  withdraw()
 176:             IERC20(_token).safeTransfer(_to, IERC20(_token).balanceOf(address(this)));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L176

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

 /// @audit  _withdraw()
 219:         IERC20(taikoToken).transferFrom(sharedVault, _to, amountToWithdraw);

 /// @audit  _withdraw()
 220:         IERC20(costToken).safeTransferFrom(_recipient, sharedVault, costToWithdraw);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L219

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

 /// @audit  claimAndDelegate()
 63:         IERC20(token).transferFrom(vault, user, amount);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L63

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

 /// @audit  withdraw()
 91:         IERC20(token).transferFrom(vault, user, amount);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L91

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

 /// @audit  _transferTokens()
 330:             IERC20(token_).safeTransfer(_to, _amount);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L330


## [L-19] Some tokens may revert when zero value transfers are made
Despite the fact that [EIP-20 states](https://github.com/ethereum/EIPs/blob/7500ac4fc1bbdfaf684e7ef851f798f6b667b2fe/EIPS/eip-20.md?plain=1#L116) that zero-value transfers must be accepted, some tokens, such as LEND, will revert if this is attempted, which may cause transactions that involve other tokens (such as batch operations) to fully revert. Consider skipping the transfer if the amount is zero, which will also save gas.

**Total Instances:** 7

```solidity
File: packages/protocol/contracts/L1/hooks/AssignmentHook.sol

 /// @audit  onBlockProposed()
 114:             IERC20(assignment.feeToken).safeTransferFrom(

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/hooks/AssignmentHook.sol#L114

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

 /// @audit  withdraw()
 176:             IERC20(_token).safeTransfer(_to, IERC20(_token).balanceOf(address(this)));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L176

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

 /// @audit  _withdraw()
 219:         IERC20(taikoToken).transferFrom(sharedVault, _to, amountToWithdraw);

 /// @audit  _withdraw()
 220:         IERC20(costToken).safeTransferFrom(_recipient, sharedVault, costToWithdraw);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L219

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol

 /// @audit  claimAndDelegate()
 63:         IERC20(token).transferFrom(vault, user, amount);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop.sol#L63

```solidity
File: packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol

 /// @audit  withdraw()
 91:         IERC20(token).transferFrom(vault, user, amount);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/airdrop/ERC20Airdrop2.sol#L91

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

 /// @audit  _transferTokens()
 330:             IERC20(token_).safeTransfer(_to, _amount);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L330


## [L-20] `tokenURI()` does not follow `EIP-721`
The [EIP](https://eips.ethereum.org/EIPS/eip-721) states that `tokenURI()` "Throws if `_tokenId` is not a valid NFT", which the code below does not do. If the NFT has not yet been minted, `tokenURI()` should revert

**Total Instances:** 1

```solidity
File: packages/protocol/contracts/tokenvault/BridgedERC721.sol

 107:     function tokenURI(uint256 _tokenId) public view virtual override returns (string memory) {

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/BridgedERC721.sol#L107


## [L-21] Unsafe conversion from unsigned to signed values
Solidity follows [two's complement](https://en.wikipedia.org/wiki/Two%27s_complement) rules for its integers, meaning that the most significant bit for signed integers is used to denote the sign, and converting between the two requires inverting all of the bits and adding one. Because of this, casting an unsigned integer to a signed one may result in a change of the sign and or magnitude of the value. For example, `int8(type(uint8).max)` is not equal to `type(int8).max`, but is equal to `-1`. `type(uint8).max` in binary is `11111111`, which if cast to a signed value, means the first binary `1` indicates a negative value, and the binary `1`s, invert to all zeroes, and when one is added, it becomes one, but negative, and therefore the decimal value of binary `11111111` is `-1`.

**Total Instances:** 4

```solidity
File: packages/protocol/contracts/L2/Lib1559Math.sol

 /// @audit  conversion from 'uint256' to 'int256'
 45:         return uint256(LibFixedPointMath.exp(int256(input)));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/Lib1559Math.sol#L45

```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

 /// @audit  conversion from 'uint256' to 'int256'
 97:                     return int256(diff);

 /// @audit  conversion from 'uint256' to 'int256'
 104:         return int256(len) - int256(otherlen);

 /// @audit  conversion from 'uint256' to 'int256'
 104:         return int256(len) - int256(otherlen);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L104


## [L-22] Unsafe Downcast
When a type is downcast to a smaller type, the higher order bits are truncated, effectively applying a modulo to the original value. The loss of data may cause incorrect calculations, unexpected state changes, or other unexpected behavior. It is recommended to use the [SafeCast library](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/utils/math/SafeCast.sol).

**Total Instances:** 47

```solidity
File: packages/protocol/contracts/L1/TaikoL1.sol

 /// @audit  uint256 downcasted to uint64
 126:         state.slotB.lastUnpausedAt = uint64(block.timestamp);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/TaikoL1.sol#L126

```solidity
File: packages/protocol/contracts/L1/libs/LibDepositing.sol

 /// @audit  uint256 downcasted to uint96
 53:                 amount: uint96(msg.value),

 /// @audit  uint256 downcasted to uint96
 83:             uint96 fee = uint96(_config.ethDepositMaxFee.min(block.basefee * _config.ethDepositGas));

 /// @audit  uint256 downcasted to uint160
 89:                     recipient: address(uint160(data >> 96)),

 /// @audit  uint256 downcasted to uint96
 90:                     amount: uint96(data),

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibDepositing.sol#L53

```solidity
File: packages/protocol/contracts/L1/libs/LibProposing.sol

 /// @audit  uint256 downcasted to uint64
 130:                 timestamp: uint64(block.timestamp),

 /// @audit  uint256 downcasted to uint64
 131:                 l1Height: uint64(block.number - 1),

 /// @audit  uint256 downcasted to uint24
 191:             meta_.txListByteSize = uint24(_txList.length);

 /// @audit  uint256 downcasted to uint64
 220:             proposedIn: uint64(block.number),

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProposing.sol#L130

```solidity
File: packages/protocol/contracts/L1/libs/LibProving.sol

 /// @audit  uint256 downcasted to uint64
 78:             _state.slotB.lastUnpausedAt = uint64(block.timestamp);

 /// @audit  uint256 downcasted to uint64
 264:         ts.timestamp = uint64(block.timestamp);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibProving.sol#L78

```solidity
File: packages/protocol/contracts/L1/libs/LibVerifying.sol

 /// @audit  uint256 downcasted to uint64
 57:         _state.slotA.genesisHeight = uint64(block.number);

 /// @audit  uint256 downcasted to uint64
 58:         _state.slotA.genesisTimestamp = uint64(block.timestamp);

 /// @audit  uint256 downcasted to uint64
 64:         blk.proposedAt = uint64(block.timestamp);

 /// @audit  uint256 downcasted to uint64
 71:         ts.timestamp = uint64(block.timestamp);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L1/libs/LibVerifying.sol#L57

```solidity
File: packages/protocol/contracts/L2/TaikoL2.sol

 /// @audit  uint256 downcasted to uint64
 284:             gasExcess_ = uint64(excess.min(type(uint64).max));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/L2/TaikoL2.sol#L284

```solidity
File: packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

 /// @audit  uint256 downcasted to uint16
 146:         enclaveReport.isvProdId = uint16(littleEndianDecode(rawEnclaveReport.substring(256, 2)));

 /// @audit  uint256 downcasted to uint16
 147:         enclaveReport.isvSvn = uint16(littleEndianDecode(rawEnclaveReport.substring(258, 2)));

 /// @audit  uint256 downcasted to uint16
 212:         qeAuthData.parsedDataSize = uint16(littleEndianDecode(rawAuthData.substring(576, 2)));

 /// @audit  uint256 downcasted to uint16
 217:         cert.certType = uint16(littleEndianDecode(rawAuthData.substring(offset, 2)));

 /// @audit  uint256 downcasted to uint32
 222:         cert.certDataSize = uint32(littleEndianDecode(rawAuthData.substring(offset, 4)));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L146

```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

 /// @audit  uint256 downcasted to uint80
 15:         return uint80(self);

 /// @audit  uint256 downcasted to uint80
 20:         return uint80(self >> 80);

 /// @audit  uint256 downcasted to uint80
 25:         return uint80(self >> 160);

 /// @audit  uint256 downcasted to uint80
 193:             ixFirstContentByte = uint80(ix + 2);

 /// @audit  uint256 downcasted to uint80
 194:             ixLastContentByte = uint80(ixFirstContentByte + length - 1);

 /// @audit  uint256 downcasted to uint80
 206:             ixFirstContentByte = uint80(ix + 2 + lengthbytesLength);

 /// @audit  uint256 downcasted to uint80
 207:             ixLastContentByte = uint80(ixFirstContentByte + length - 1);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L15

```solidity
File: packages/protocol/contracts/bridge/Bridge.sol

 /// @audit  uint256 downcasted to uint64
 89:         uint64 _timestamp = _suspend ? type(uint64).max : uint64(block.timestamp);

 /// @audit  uint256 downcasted to uint64
 146:         message_.srcChainId = uint64(block.chainid);

 /// @audit  uint256 downcasted to uint64
 183:             receivedAt = uint64(block.timestamp);

 /// @audit  uint256 downcasted to uint64
 240:             receivedAt = uint64(block.timestamp);

 /// @audit  uint256 downcasted to uint64
 533:             _storeContext(bytes32(PLACEHOLDER), address(uint160(PLACEHOLDER)), uint64(PLACEHOLDER));

 /// @audit  uint256 downcasted to uint160
 533:             _storeContext(bytes32(PLACEHOLDER), address(uint160(PLACEHOLDER)), uint64(PLACEHOLDER));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/bridge/Bridge.sol#L89

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

 /// @audit  uint256 downcasted to uint64
 264:         slot_ = getSignalSlot(uint64(block.chainid), _app, _signal);

 /// @audit  uint256 downcasted to uint64
 308:         bytes32 slot = getSignalSlot(uint64(block.chainid), _app, _signal);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L264

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

 /// @audit  uint256 downcasted to uint64
 264:         return _amount * uint64(block.timestamp - _start) / _period;

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L264

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol

 /// @audit  uint256 downcasted to uint8
 35:             out_[0] = bytes1(uint8(_len) + uint8(_offset));

 /// @audit  uint256 downcasted to uint8
 35:             out_[0] = bytes1(uint8(_len) + uint8(_offset));

 /// @audit  uint256 downcasted to uint8
 45:             out_[0] = bytes1(uint8(lenLen) + uint8(_offset) + 55);

 /// @audit  uint256 downcasted to uint8
 45:             out_[0] = bytes1(uint8(lenLen) + uint8(_offset) + 55);

 /// @audit  uint256 downcasted to uint8
 47:                 out_[i] = bytes1(uint8((_len / (256 ** (lenLen - i))) % 256));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPWriter.sol#L35

```solidity
File: packages/protocol/contracts/tokenvault/ERC1155Vault.sol

 /// @audit  uint256 downcasted to uint64
 257:                     chainId: uint64(block.chainid),

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L257

```solidity
File: packages/protocol/contracts/tokenvault/ERC20Vault.sol

 /// @audit  uint256 downcasted to uint64
 366:                 chainId: uint64(block.chainid),

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC20Vault.sol#L366

```solidity
File: packages/protocol/contracts/tokenvault/ERC721Vault.sol

 /// @audit  uint256 downcasted to uint64
 204:                     chainId: uint64(block.chainid),

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/tokenvault/ERC721Vault.sol#L204

```solidity
File: packages/protocol/contracts/verifiers/SgxVerifier.sol

 /// @audit  uint256 downcasted to uint64
 204:         uint64 validSince = uint64(block.timestamp);

 /// @audit  uint256 downcasted to uint64
 229:         instances[id] = Instance(newInstance, uint64(block.timestamp));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/verifiers/SgxVerifier.sol#L229


## [L-24] Use of abi.encodePacked with dynamic types inside keccak256
Using abi.encodePacked with dynamic types for hashing functions like keccak256 can be risky due to the potential for hash collisions. This function concatenates arguments tightly, without padding, which might lead to different inputs producing the same hash. This is especially problematic with dynamic types, where the boundaries between inputs can blur. To mitigate this, use abi.encode instead. abi.encode pads its arguments to 32 bytes, creating clear distinctions between different inputs and significantly reducing the chance of hash collisions. This approach ensures more reliable and collision-resistant hashing, crucial for maintaining data integrity and security in smart contracts.

**Total Instances:** 2

```solidity
File: packages/protocol/contracts/signal/SignalService.sol

 203:         return keccak256(abi.encodePacked("SIGNAL", _chainId, _app, _signal));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/signal/SignalService.sol#L203

```solidity
File: packages/protocol/contracts/team/TimelockTokenPool.sol

 170:         bytes32 hash = keccak256(abi.encodePacked("Withdraw unlocked Taiko token to: ", _to));

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/team/TimelockTokenPool.sol#L170


## [L-25] Use of a single-step ownership transfer
The existing `transferOwnership` function immediately transfers ownership to the new address. Consider implementing a two-step variant, where the ‘acceptor’ of the ownership must call a separate function in order for the transfer to take effect. This can help to prevent mistakes where the wrong address is used, and ownership is irrecoverably lost.

**Total Instances:** 1

```solidity
File: packages/protocol/contracts/common/EssentialContract.sol

 110:         _transferOwnership(_owner == address(0) ? msg.sender : _owner);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/common/EssentialContract.sol#L110


## [L-27] Using zero as a parameter
Taking `0` as a valid argument in Solidity without checks can lead to severe security issues. A historical example is the infamous `0x0` address bug where numerous tokens were lost. This happens because `0` can be interpreted as an uninitialized `address`, leading to transfers to the `0x0` `address`, effectively burning tokens. Moreover, `0` as a denominator in division operations would cause a runtime exception. It’s also often indicative of a logical error in the caller’s code. It’s important to always validate input and handle edge cases like `0` appropriately. Use `require()` statements to enforce conditions and provide clear error messages to facilitate debugging and safer code.

**Total Instances:** 5

```solidity
File: packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol

 48:         return _readNodeLength(der, 0);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/Asn1Decode.sol#L48

```solidity
File: packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol

 40:         return compare(self, 0, self.length, other, 0, other.length);

 169:         return self.length >= offset + other.length && equals(self, offset, other, 0, other.length);

 179:         return self.length == other.length && equals(self, 0, other, 0, self.length);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/automata-attestation/utils/BytesUtils.sol#L40

```solidity
File: packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

 136:         out_ = _copy(_in.ptr, 0, _in.length);

```
https://github.com/code-423n4/2024-03-taiko/blob/f58384f44dbf4c6535264a472322322705133b11/packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L136
