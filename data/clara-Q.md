        
### Low Risk Issues

| |Issue|Instances|
|-|:-|:-:|
| [[L001](#l001---abiencodepacked-should-not-be-used-with-dynamic-types-when-passing-the-result-to-a-hash-function-such-as-keccak256)] | `abi.encodePacked()` should not be used with dynamic types when passing the result to a hash function such as `keccak256()` | 3 |

| [[L002](#l003---array-lengths-not-checked)] | Array lengths not checked | 11 |

| [[L003](#l005---require-should-be-used-instead-of-assert)] | `require()` should be used instead of `assert()` | 4 |
| [[L004](#l006---missing-checks-for-address0x0-when-assigning-values-to-address-state-variables)] | Missing checks for `address(0x0)` when assigning values to address state variables | 13 |
| [[L005](#l007---unsafe-downcast)] | Unsafe downcast | 29 |

| [[L006](#l009---array-does-not-have-a-pop-function)] | Array does not have a `pop` function | 1 |

| [[L007](#l011---external-call-recipient-may-consume-all-transaction-gas)] | External call recipient may consume all transaction gas | 1 |
| [[L008](#l012---nft-doesnt-handle-hard-forks)] | NFT doesn't handle hard forks | 1 |
| [[L009](#l013---setters-should-have-initial-value-check)] | Setters should have initial value check | 5 |
| [[L010](#l014---empty-receivepayable-fallback-function-does-not-authorize-requests)] | Empty `receive()`/`payable fallback()` function does not authorize requests | 1 |
| [[L011](#l015---contracts-are-designed-to-receive-eth-but-do-not-implement-function-for-withdrawal)] | Contracts are designed to receive ETH but do not implement function for withdrawal | 1 |
| [[L012](#l016---tokenuri-does-not-follow-eip-721)] | `tokenURI()` does not follow EIP-721 | 1 |
| [[L013](#l017---int-casting-blocktimestamp-can-reduce-the-lifespan-of-a-contract)] | Int casting `block.timestamp` can reduce the lifespan of a contract | 12 |
| [[L014](#l018---constant-decimal-values)] | Constant decimal values | 1 |
| [[L015](#l019---no-limits-when-setting-state-variable-amounts)] | No limits when setting state variable amounts | 29 |
| [[L016](#l020---pausing-withdrawals-is-unfair-to-the-users)] | Pausing withdrawals is unfair to the users | 1 |
| [[L017](#l021---double-type-casts-create-complexity-within-the-code)] | Double type casts create complexity within the code | 16 |
| [[L018](#l022---constructor-contains-no-validation)] | Constructor contains no validation | 2 |
| [[L019](#l023---for-loops-in-public-or-external-functions-should-be-avoided-due-to-high-gas-costs-and-possible-dos)] | For loops in `public` or `external` functions should be avoided due to high gas costs and possible DOS | 10 |
| [[L020](#l024---function-calls-within-for-loops)] | Function calls within for loops | 5 |
| [[L021](#l025---external-calls-in-an-unbounded-for-loop-may-result-in-a-dos)] | External calls in an unbounded for-loop may result in a DoS | 16 |
| [[L022](#l026---contracts-are-not-using-their-oz-upgradeable-counterparts)] | Contracts are not using their OZ Upgradeable counterparts | 54 |
| [[L023](#l027---consider-implementing-two-step-procedure-for-updating-protocol-addresses)] | Consider implementing two-step procedure for updating protocol addresses | 2 |
| [[L024](#l028---decimals-is-not-a-part-of-the-erc-20-standard)] | `decimals()` is not a part of the ERC-20 standard | 4 |
| [[L025](#l029---symbol-is-not-a-part-of-the-erc-20-standard)] | `symbol()` is not a part of the ERC-20 standard | 9 |
| [[L026](#l030---name-is-not-a-part-of-the-erc-20-standard)] | `name()` is not a part of the ERC-20 standard | 9 |
| [[L027](#l031---missing-checks-for-address0x0-in-the-constructor)] | Missing checks for address(0x0) in the constructor | 1 |
| [[L028](#l032---governance-functions-should-be-controlled-by-time-locks)] | Governance functions should be controlled by time locks | 16 |
| [[L029](#l033---code-does-not-follow-the-best-practice-of-check-effects-interaction)] | Code does not follow the best practice of check-effects-interaction | 5 |
| [[L030](#l034---missing-checks-for-address0x0-when-updating-address-state-variables)] | Missing checks for address(0x0) when updating address state variables | 18 |
| [[L031](#l035---the-additionsmultiplications-may-silently-overflow-because-theyre-in-unchecked-blocks-with-no-preceding-value-checks-which-may-lead-to-unexpected-results)] | The additions/multiplications may silently overflow because they're in unchecked blocks with no preceding value checks, which may lead to unexpected results. | 32 |
| [[L032](#l036---the-setter-does-not-set-a-state-variable-or-call-a-fuction)] | The setter does not set a state variable or call a fuction | 2 |
| [[L033](#l037---unbounded-state-array-which-is-iterated-upon)] | Unbounded state array which is iterated upon | 24 |
| [[L034](#l038---prefer-continue-over-revert-model-in-iteration)] | Prefer continue over revert model in iteration | 8 |
| [[L035](#l039----subtraction-may-underflow-if-multiplication-is-too-large)] |  Subtraction may underflow if multiplication is too large | 1 |

Total: 377 instances over 39 issues





## L001 - `abi.encodePacked()` should not be used with dynamic types when passing the result to a hash function such as `keccak256()`:

Use `abi.encode()` instead which will pad items to 32 bytes, which will [prevent hash collisions](https://docs.soliditylang.org/en/v0.8.13/abi-spec.html#non-standard-packed-mode) (e.g. `abi.encodePacked(0x123,0x456)` => `0x123456` => `abi.encodePacked(0x1,0x23456)`, but `abi.encode(0x123,0x456)` => `0x0...1230...456`). Unless there is a compelling reason, `abi.encode` should be preferred. If there is only one argument to `abi.encodePacked()` it can often be cast to `bytes()` or `bytes32()` [instead](https://ethereum.stackexchange.com/questions/30912/how-to-compare-strings-in-solidity#answer-82739). If all arguments are strings and or bytes, `bytes.concat()` should be used instead.


```solidity
File: contracts/L1/libs/LibProposing.sol


meta_.difficulty = keccak256(abi.encodePacked(block.prevrandao, b.numBlocks, block.number));

```

https://github.com/llrr586570/Good/tree/main/L1/libs/LibProposing.sol#L204:204

```solidity
File: contracts/signal/SignalService.sol


return keccak256(abi.encodePacked("SIGNAL", _chainId, _app, _signal));

```

https://github.com/llrr586570/Good/tree/main/signal/SignalService.sol#L203:203

```solidity
File: contracts/team/TimelockTokenPool.sol


bytes32 hash = keccak256(abi.encodePacked("Withdraw unlocked Taiko token to: ", _to));

```

https://github.com/llrr586570/Good/tree/main/team/TimelockTokenPool.sol#L170:170


## L002 - Array lengths not checked:

If the length of the arrays are not required to be of the same length, user operations may not be fully executed due to a mismatch in the number of items iterated over, versus the number of items provided in the second array.


<details>
<summary>Click to show 11 findings</summary>

```solidity
File: contracts/L1/gov/TaikoGovernor.sol


48          function propose(
49              address[] memory _targets,
50              uint256[] memory _values,
51              bytes[] memory _calldatas,
52              string memory _description
53          )
54              public
55              override(IGovernorUpgradeable, GovernorUpgradeable, GovernorCompatibilityBravoUpgradeable)
56              returns (uint256)
57          {
58              return super.propose(_targets, _values, _calldatas, _description);
59          }


69          function propose(
70              address[] memory _targets,
71              uint256[] memory _values,
72              string[] memory _signatures,
73              bytes[] memory _calldatas,
74              string memory _description
75          )
76              public
77              virtual
78              override(GovernorCompatibilityBravoUpgradeable)
79              returns (uint256)
80          {
81              if (_signatures.length != _calldatas.length) revert TG_INVALID_SIGNATURES_LENGTH();
82      
83              return GovernorCompatibilityBravoUpgradeable.propose(
84                  _targets, _values, _signatures, _calldatas, _description
85              );
86          }


127         function _execute(
128             uint256 _proposalId,
129             address[] memory _targets,
130             uint256[] memory _values,
131             bytes[] memory _calldatas,
132             bytes32 _descriptionHash
133         )
134             internal
135             override(GovernorUpgradeable, GovernorTimelockControlUpgradeable)
136         {
137             super._execute(_proposalId, _targets, _values, _calldatas, _descriptionHash);
138         }


140         function _cancel(
141             address[] memory _targets,
142             uint256[] memory _values,
143             bytes[] memory _calldatas,
144             bytes32 _descriptionHash
145         )
146             internal
147             override(GovernorUpgradeable, GovernorTimelockControlUpgradeable)
148             returns (uint256)
149         {
150             return super._cancel(_targets, _values, _calldatas, _descriptionHash);
151         }


```

https://github.com/llrr586570/Good/tree/main/L1/gov/TaikoGovernor.sol#L140:151

```solidity
File: contracts/libs/Lib4844.sol


30          function evaluatePoint(
31              bytes32 _blobHash,
32              uint256 _x,
33              uint256 _y,
34              bytes1[48] memory _commitment,
35              bytes1[48] memory _pointProof
36          )
37              internal
38              view
39          {
40              if (_x >= BLS_MODULUS) revert POINT_X_TOO_LARGE();
41              if (_y >= BLS_MODULUS) revert POINT_Y_TOO_LARGE();
42      
43              (bool ok, bytes memory ret) = POINT_EVALUATION_PRECOMPILE_ADDRESS.staticcall(
44                  abi.encodePacked(_blobHash, _x, _y, _commitment, _pointProof)
45              );
46      
47              if (!ok) revert EVAL_FAILED_1();
48      
49              if (ret.length != 64) revert EVAL_FAILED_2();
50      
51              bytes32 first;
52              bytes32 second;
53              assembly {
54                  first := mload(add(ret, 32))
55                  second := mload(add(ret, 64))
56              }
57              if (uint256(first) != FIELD_ELEMENTS_PER_BLOB || uint256(second) != BLS_MODULUS) {
58                  revert EVAL_FAILED_2();
59              }
60          }


```

https://github.com/llrr586570/Good/tree/main/libs/Lib4844.sol#L30:60

```solidity
File: contracts/libs/LibTrieProof.sol


34          function verifyMerkleProof(
35              bytes32 _rootHash,
36              address _addr,
37              bytes32 _slot,
38              bytes32 _value,
39              bytes[] memory _accountProof,
40              bytes[] memory _storageProof
41          )
42              internal
43              pure
44              returns (bytes32 storageRoot_)
45          {
46              if (_accountProof.length != 0) {
47                  bytes memory rlpAccount =
48                      SecureMerkleTrie.get(abi.encodePacked(_addr), _accountProof, _rootHash);
49      
50                  if (rlpAccount.length == 0) revert LTP_INVALID_ACCOUNT_PROOF();
51      
52                  RLPReader.RLPItem[] memory accountState = RLPReader.readList(rlpAccount);
53      
54                  storageRoot_ =
55                      bytes32(RLPReader.readBytes(accountState[_ACCOUNT_FIELD_INDEX_STORAGE_HASH]));
56              } else {
57                  storageRoot_ = _rootHash;
58              }
59      
60              bool verified = SecureMerkleTrie.verifyInclusionProof(
61                  bytes.concat(_slot), RLPWriter.writeUint(uint256(_value)), _storageProof, storageRoot_
62              );
63      
64              if (!verified) revert LTP_INVALID_INCLUSION_PROOF();
65          }


```

https://github.com/llrr586570/Good/tree/main/libs/LibTrieProof.sol#L34:65

```solidity
File: contracts/team/airdrop/ERC721Airdrop.sol


47          function claim(
48              address user,
49              uint256[] calldata tokenIds,
50              bytes32[] calldata proof
51          )
52              external
53              nonReentrant
54          {
55              // Check if this can be claimed
56              _verifyClaim(abi.encode(user, tokenIds), proof);
57      
58              // Transfer the tokens
59              for (uint256 i; i < tokenIds.length; ++i) {
60                  IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);
61              }
62          }


```

https://github.com/llrr586570/Good/tree/main/team/airdrop/ERC721Airdrop.sol#L47:62

```solidity
File: contracts/tokenvault/BridgedERC1155.sol


83          function mintBatch(
84              address _to,
85              uint256[] memory _tokenIds,
86              uint256[] memory _amounts
87          )
88              public
89              nonReentrant
90              whenNotPaused
91              onlyFromNamed("erc1155_vault")
92          {
93              _mintBatch(_to, _tokenIds, _amounts, "");
94          }


125         function _beforeTokenTransfer(
126             address, /*_operator*/
127             address, /*_from*/
128             address _to,
129             uint256[] memory, /*_ids*/
130             uint256[] memory, /*_amounts*/
131             bytes memory /*_data*/
132         )
133             internal
134             virtual
135             override
136         {
137             if (_to == address(this)) revert BTOKEN_CANNOT_RECEIVE();
138             if (paused()) revert INVALID_PAUSE_STATUS();
139         }


```

https://github.com/llrr586570/Good/tree/main/tokenvault/BridgedERC1155.sol#L125:139

```solidity
File: contracts/tokenvault/ERC1155Vault.sol


160         function onERC1155BatchReceived(
161             address,
162             address,
163             uint256[] calldata,
164             uint256[] calldata,
165             bytes calldata
166         )
167             external
168             pure
169             returns (bytes4)
170         {
171             return IERC1155ReceiverUpgradeable.onERC1155BatchReceived.selector;
172         }


214         function _transferTokens(
215             CanonicalNFT memory ctoken,
216             address to,
217             uint256[] memory tokenIds,
218             uint256[] memory amounts
219         )
220             private
221             returns (address token)
222         {
223             if (ctoken.chainId == block.chainid) {
224                 // Token lives on this chain
225                 token = ctoken.addr;
226                 IERC1155(token).safeBatchTransferFrom(address(this), to, tokenIds, amounts, "");
227             } else {
228                 // Token does not live on this chain
229                 token = _getOrDeployBridgedToken(ctoken);
230                 BridgedERC1155(token).mintBatch(to, tokenIds, amounts);
231             }
232         }


```

https://github.com/llrr586570/Good/tree/main/tokenvault/ERC1155Vault.sol#L214:232

</details>


## L003 - `require()` should be used instead of `assert()`:

Prior to solidity version 0.8.0, hitting an assert consumes the remainder of the transaction's available gas rather than returning it, as require()/revert() do. assert() should be avoided even past solidity version 0.8.0 as its documentation states that 'The assert function creates an error of type Panic(uint256). ... Properly functioning code should never create a Panic, not even on invalid external input. If this happens, then there is a bug in your contract which you should fix'.


<details>
<summary>Click to show 4 findings</summary>

```solidity
File: contracts/L1/libs/LibProving.sol


223                     assert(tier.validityBond == 0);


224                     assert(ts.validityBond == 0 && ts.contestBond == 0 && ts.contester == address(0));


```

https://github.com/llrr586570/Good/tree/main/L1/libs/LibProving.sol#L224:224

```solidity
File: contracts/automata-attestation/utils/SigVerifyLib.sol


138             assert(success); // never reverts, always returns 0 or 1


```

https://github.com/llrr586570/Good/tree/main/automata-attestation/utils/SigVerifyLib.sol#L138:138

```solidity
File: contracts/bridge/Bridge.sol


486             assert(_message.from != address(this));


```

https://github.com/llrr586570/Good/tree/main/bridge/Bridge.sol#L486:486

</details>

## L004 - Missing checks for `address(0x0)` when assigning values to address state variables:

This issue arises when an address state variable is assigned a value without a preceding check to ensure it isn't address(0x0). This can lead to unexpected behavior as address(0x0) often represents an uninitialized address.


<details>
<summary>Click to show 13 findings</summary>

```solidity
File: contracts/bridge/Bridge.sol


549                 __ctx = Context(_msgHash, _from, _srcChainId);


```

https://github.com/llrr586570/Good/tree/main/bridge/Bridge.sol#L549:549

```solidity
File: contracts/common/AddressResolver.sol


62              addressManager = _addressManager;


```

https://github.com/llrr586570/Good/tree/main/common/AddressResolver.sol#L62:62

```solidity
File: contracts/team/airdrop/ERC20Airdrop.sol


41              token = _token;


42              vault = _vault;


```

https://github.com/llrr586570/Good/tree/main/team/airdrop/ERC20Airdrop.sol#L42:42

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol


69              token = _token;


70              vault = _vault;


```

https://github.com/llrr586570/Good/tree/main/team/airdrop/ERC20Airdrop2.sol#L70:70

```solidity
File: contracts/team/airdrop/ERC721Airdrop.sol


39              token = _token;


40              vault = _vault;


```

https://github.com/llrr586570/Good/tree/main/team/airdrop/ERC721Airdrop.sol#L40:40

```solidity
File: contracts/tokenvault/BridgedERC1155.sol


56              srcToken = _srcToken;


```

https://github.com/llrr586570/Good/tree/main/tokenvault/BridgedERC1155.sol#L56:56

```solidity
File: contracts/tokenvault/BridgedERC20.sol


73              srcToken = _srcToken;


81              snapshooter = _snapshooter;


```

https://github.com/llrr586570/Good/tree/main/tokenvault/BridgedERC20.sol#L81:81

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol


49              migratingAddress = _migratingAddress;


```

https://github.com/llrr586570/Good/tree/main/tokenvault/BridgedERC20Base.sol#L49:49

```solidity
File: contracts/tokenvault/BridgedERC721.sol


47              srcToken = _srcToken;


```

https://github.com/llrr586570/Good/tree/main/tokenvault/BridgedERC721.sol#L47:47

</details>

## L005 - Unsafe downcast:

When a type is downcast to a smaller type, the higher order bits are truncated, effectively applying a modulo to the original value. Without any other checks, this wrapping will lead to unexpected behavior and bugs.


<details>
<summary>Click to show 29 findings</summary>

```solidity
File: contracts/L1/TaikoL1.sol


126             state.slotB.lastUnpausedAt = uint64(block.timestamp);


```

https://github.com/llrr586570/Good/tree/main/L1/TaikoL1.sol#L126:126

```solidity
File: contracts/L1/libs/LibProposing.sol


191                 meta_.txListByteSize = uint24(_txList.length);


130                     timestamp: uint64(block.timestamp),


```

https://github.com/llrr586570/Good/tree/main/L1/libs/LibProposing.sol#L130:130

```solidity
File: contracts/L1/libs/LibProving.sol


414             bool inProvingWindow = uint256(_ts.timestamp).max(_state.slotB.lastUnpausedAt)


78                  _state.slotB.lastUnpausedAt = uint64(block.timestamp);


264             ts.timestamp = uint64(block.timestamp);


```

https://github.com/llrr586570/Good/tree/main/L1/libs/LibProving.sol#L264:264

```solidity
File: contracts/L1/libs/LibVerifying.sol


153                                 + uint256(ts.timestamp).max(_state.slotB.lastUnpausedAt) > block.timestamp


71              ts.timestamp = uint64(block.timestamp);


58              _state.slotA.genesisTimestamp = uint64(block.timestamp);


64              blk.proposedAt = uint64(block.timestamp);


```

https://github.com/llrr586570/Good/tree/main/L1/libs/LibVerifying.sol#L64:64

```solidity
File: contracts/automata-attestation/utils/Asn1Decode.sol


207                 ixLastContentByte = uint80(ixFirstContentByte + length - 1);


196                 uint8 lengthbytesLength = uint8(der[ix + 1] & 0x7F);


206                 ixFirstContentByte = uint80(ix + 2 + lengthbytesLength);


25              return uint80(self >> 160);


20              return uint80(self >> 80);


192                 length = uint8(der[ix + 1]);


193                 ixFirstContentByte = uint80(ix + 2);


194                 ixLastContentByte = uint80(ixFirstContentByte + length - 1);


15              return uint80(self);


```

https://github.com/llrr586570/Good/tree/main/automata-attestation/utils/Asn1Decode.sol#L15:15

```solidity
File: contracts/automata-attestation/utils/BytesUtils.sol


189             return uint8(self[idx]);


```

https://github.com/llrr586570/Good/tree/main/automata-attestation/utils/BytesUtils.sol#L189:189

```solidity
File: contracts/bridge/Bridge.sol


89              uint64 _timestamp = _suspend ? type(uint64).max : uint64(block.timestamp);


533                 _storeContext(bytes32(PLACEHOLDER), address(uint160(PLACEHOLDER)), uint64(PLACEHOLDER));


183                 receivedAt = uint64(block.timestamp);


240                 receivedAt = uint64(block.timestamp);


```

https://github.com/llrr586570/Good/tree/main/bridge/Bridge.sol#L240:240

```solidity
File: contracts/thirdparty/optimism/rlp/RLPWriter.sol


45                  out_[0] = bytes1(uint8(lenLen) + uint8(_offset) + 55);


47                      out_[i] = bytes1(uint8((_len / (256 ** (lenLen - i))) % 256));


35                  out_[0] = bytes1(uint8(_len) + uint8(_offset));


```

https://github.com/llrr586570/Good/tree/main/thirdparty/optimism/rlp/RLPWriter.sol#L35:35

```solidity
File: contracts/verifiers/SgxVerifier.sol


204             uint64 validSince = uint64(block.timestamp);


229             instances[id] = Instance(newInstance, uint64(block.timestamp));


```

https://github.com/llrr586570/Good/tree/main/verifiers/SgxVerifier.sol#L229:229

</details>



## L006 - Array does not have a `pop` function:

Arrays without the pop operation in Solidity can lead to inefficient memory management and increase the likelihood of out-of-gas errors.


```solidity
File: contracts/L1/provers/Guardians.sol


87                  guardians.push(guardian);


```

https://github.com/llrr586570/Good/tree/main/L1/provers/Guardians.sol#L87:87



## L007 - External call recipient may consume all transaction gas:

There is no limit specified on the amount of gas used, so the recipient can use up all of the transaction's gas, causing it to revert. Use `addr.call{gas: <amount>}()` or [this](https://github.com/nomad-xyz/ExcessivelySafeCall) library instead.


```solidity
File: contracts/L2/CrossChainOwned.sol


50              (bool success,) = address(this).call(txdata);


```

https://github.com/llrr586570/Good/tree/main/L2/CrossChainOwned.sol#L50:50

## L008 - NFT doesn't handle hard forks:

When there are hard forks, users often have to go through [many hoops](https://twitter.com/elerium115/status/1558471934924431363) to ensure that they control ownership on every fork. Consider adding `require(1 == chain.chainId)`, or the chain ID of whichever chain you prefer, to the functions below, or at least include the chain ID in the URI, so that there is no confusion about which chain is the owner of the NFT.


```solidity
File: contracts/tokenvault/BridgedERC721.sol


107         function tokenURI(uint256 _tokenId) public view virtual override returns (string memory) {
108             return string(
109                 abi.encodePacked(
110                     LibBridgedToken.buildURI(srcToken, srcChainId), Strings.toString(_tokenId)
111                 )
112             );
113         }


```

https://github.com/llrr586570/Good/tree/main/tokenvault/BridgedERC721.sol#L107:113

## L009 - Setters should have initial value check:

Setters should have initial value check to prevent assigning wrong value to the variable. Assginment of wrong value can lead to unexpected behavior of the contract.


<details>
<summary>Click to show 5 findings</summary>

```solidity
File: contracts/L2/TaikoL2EIP1559Configurable.sol


25          function setConfigAndExcess(
26              Config memory _newConfig,
27              uint64 _newGasExcess
28          )
29              external
30              virtual
31              onlyOwner
32          {
33              if (_newConfig.gasTargetPerL1Block == 0) revert L2_INVALID_CONFIG();
34              if (_newConfig.basefeeAdjustmentQuotient == 0) revert L2_INVALID_CONFIG();
35      
36              customConfig = _newConfig;
37              gasExcess = _newGasExcess;
38      
39              emit ConfigAndExcessChanged(_newConfig, _newGasExcess);
40          }


```

https://github.com/llrr586570/Good/tree/main/L2/TaikoL2EIP1559Configurable.sol#L25:40

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol


65          function setMrSigner(bytes32 _mrSigner, bool _trusted) external onlyOwner {
66              _trustedUserMrSigner[_mrSigner] = _trusted;
67          }


69          function setMrEnclave(bytes32 _mrEnclave, bool _trusted) external onlyOwner {
70              _trustedUserMrEnclave[_mrEnclave] = _trusted;
71          }


```

https://github.com/llrr586570/Good/tree/main/automata-attestation/AutomataDcapV3Attestation.sol#L69:71

```solidity
File: contracts/common/AddressManager.sol


38          function setAddress(
39              uint64 _chainId,
40              bytes32 _name,
41              address _newAddress
42          )
43              external
44              virtual
45              onlyOwner
46          {
47              address oldAddress = __addresses[_chainId][_name];
48              if (_newAddress == oldAddress) revert AM_INVALID_PARAMS();
49              __addresses[_chainId][_name] = _newAddress;
50              emit AddressSet(_chainId, _name, _newAddress, oldAddress);
51          }


```

https://github.com/llrr586570/Good/tree/main/common/AddressManager.sol#L38:51

```solidity
File: contracts/tokenvault/BridgedERC20.sol


80          function setSnapshoter(address _snapshooter) external onlyOwner {
81              snapshooter = _snapshooter;
82          }


```

https://github.com/llrr586570/Good/tree/main/tokenvault/BridgedERC20.sol#L80:82

</details>

## L010 - Empty `receive()`/`payable fallback()` function does not authorize requests:

If the intention is for the Ether to be used, the function should call another function, otherwise it should revert (e.g. `require(msg.sender == address(weth))`). Having no access control on the function means that someone may send Ether to the contract, and have no way to get anything back out, which is a loss of funds. If the concern is having to spend a small amount of gas to check the sender against an immutable address, the code should at least have a function to rescue unused Ether.


```solidity
File: contracts/bridge/Bridge.sol


70          receive() external payable { }


```

https://github.com/llrr586570/Good/tree/main/bridge/Bridge.sol#L70:70

## L011 - Contracts are designed to receive ETH but do not implement function for withdrawal:

The following contracts can receive ETH but can not withdraw, ETH is occasionally sent by users will be stuck in those contracts. This functionality also applies to baseTokens resulting in locked tokens and loss of funds.


```solidity
File: contracts/bridge/Bridge.sol


70          receive() external payable { }


```

https://github.com/llrr586570/Good/tree/main/bridge/Bridge.sol#L70:70

## L012 - `tokenURI()` does not follow EIP-721:

The [EIP](https://eips.ethereum.org/EIPS/eip-721) states that `tokenURI()` "Throws if `_tokenId` is not a valid NFT", which the code below does not do. If the NFT has not yet been minted, `tokenURI()` should revert.


```solidity
File: contracts/tokenvault/BridgedERC721.sol


107         function tokenURI(uint256 _tokenId) public view virtual override returns (string memory) {
108             return string(
109                 abi.encodePacked(
110                     LibBridgedToken.buildURI(srcToken, srcChainId), Strings.toString(_tokenId)
111                 )
112             );
113         }


```

https://github.com/llrr586570/Good/tree/main/tokenvault/BridgedERC721.sol#L107:113

## L013 - Int casting `block.timestamp` can reduce the lifespan of a contract:

Consider removing casting to ensure future functionality.


<details>
<summary>Click to show 12 findings</summary>

```solidity
File: contracts/L1/TaikoL1.sol


126             state.slotB.lastUnpausedAt = uint64(block.timestamp);


```

https://github.com/llrr586570/Good/tree/main/L1/TaikoL1.sol#L126:126

```solidity
File: contracts/L1/libs/LibProposing.sol


130                     timestamp: uint64(block.timestamp),


```

https://github.com/llrr586570/Good/tree/main/L1/libs/LibProposing.sol#L130:130

```solidity
File: contracts/L1/libs/LibProving.sol


78                  _state.slotB.lastUnpausedAt = uint64(block.timestamp);


264             ts.timestamp = uint64(block.timestamp);


```

https://github.com/llrr586570/Good/tree/main/L1/libs/LibProving.sol#L264:264

```solidity
File: contracts/L1/libs/LibVerifying.sol


58              _state.slotA.genesisTimestamp = uint64(block.timestamp);


64              blk.proposedAt = uint64(block.timestamp);


71              ts.timestamp = uint64(block.timestamp);


```

https://github.com/llrr586570/Good/tree/main/L1/libs/LibVerifying.sol#L71:71

```solidity
File: contracts/bridge/Bridge.sol


89              uint64 _timestamp = _suspend ? type(uint64).max : uint64(block.timestamp);


183                 receivedAt = uint64(block.timestamp);


240                 receivedAt = uint64(block.timestamp);


```

https://github.com/llrr586570/Good/tree/main/bridge/Bridge.sol#L240:240

```solidity
File: contracts/verifiers/SgxVerifier.sol


204             uint64 validSince = uint64(block.timestamp);


229             instances[id] = Instance(newInstance, uint64(block.timestamp));


```

https://github.com/llrr586570/Good/tree/main/verifiers/SgxVerifier.sol#L229:229

</details>

## L014 - Constant decimal values:

The use of fixed decimal values such as 1e18 or 1e8 in Solidity contracts can lead to inaccuracies, bugs, and vulnerabilities, particularly when interacting with tokens having different decimal configurations. Not all ERC20 tokens follow the standard 18 decimal places, and assumptions about decimal places can lead to miscalculations. Always retrieve and use the decimals() function from the token contract itself when performing calculations involving token amounts.


```solidity
File: contracts/team/TimelockTokenPool.sol


197             uint128 _amountUnlocked = amountUnlocked / 1e18; // divide first


```

https://github.com/llrr586570/Good/tree/main/team/TimelockTokenPool.sol#L197:197

## L015 - No limits when setting state variable amounts:

It is important to ensure state variables numbers are set to a reasonable value.


<details>
<summary>Click to show 29 findings</summary>

```solidity
File: contracts/L1/TaikoL1.sol


126             state.slotB.lastUnpausedAt = uint64(block.timestamp);


```

https://github.com/llrr586570/Good/tree/main/L1/TaikoL1.sol#L126:126

```solidity
File: contracts/L1/libs/LibDepositing.sol


107                 _state.slotA.nextEthDepositToProcess = j;


```

https://github.com/llrr586570/Good/tree/main/L1/libs/LibDepositing.sol#L107:107

```solidity
File: contracts/L1/libs/LibProving.sol


78                  _state.slotB.lastUnpausedAt = uint64(block.timestamp);


```

https://github.com/llrr586570/Good/tree/main/L1/libs/LibProving.sol#L78:78

```solidity
File: contracts/L1/libs/LibVerifying.sol


57              _state.slotA.genesisHeight = uint64(block.number);


58              _state.slotA.genesisTimestamp = uint64(block.timestamp);


216                     _state.slotB.lastVerifiedBlockId = lastVerifiedBlockId;


```

https://github.com/llrr586570/Good/tree/main/L1/libs/LibVerifying.sol#L216:216

```solidity
File: contracts/L2/TaikoL2.sol


96              gasExcess = _gasExcess;


284                 gasExcess_ = uint64(excess.min(type(uint64).max));


```

https://github.com/llrr586570/Good/tree/main/L2/TaikoL2.sol#L284:284

```solidity
File: contracts/L2/TaikoL2EIP1559Configurable.sol


37              gasExcess = _newGasExcess;


```

https://github.com/llrr586570/Good/tree/main/L2/TaikoL2EIP1559Configurable.sol#L37:37

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol


206                 cert.pck.sgxExtension.pcesvn = pcesvn;


363                     pcesvn = uint256(svnValue);


```

https://github.com/llrr586570/Good/tree/main/automata-attestation/lib/PEMCertChainLib.sol#L363:363

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol


146             enclaveReport.isvProdId = uint16(littleEndianDecode(rawEnclaveReport.substring(256, 2)));


147             enclaveReport.isvSvn = uint16(littleEndianDecode(rawEnclaveReport.substring(258, 2)));


```

https://github.com/llrr586570/Good/tree/main/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L147:147

```solidity
File: contracts/bridge/Bridge.sol


92                  proofReceipt[msgHash].receivedAt = _timestamp;


146             message_.srcChainId = uint64(block.chainid);


```

https://github.com/llrr586570/Good/tree/main/bridge/Bridge.sol#L146:146

```solidity
File: contracts/common/EssentialContract.sol


70              __paused = _TRUE;


79              __paused = _FALSE;


111             __paused = _FALSE;


125                 __reentry = _reentry;


136                 reentry_ = __reentry;


```

https://github.com/llrr586570/Good/tree/main/common/EssentialContract.sol#L136:136

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol


71              withdrawalWindow = _withdrawalWindow;


```

https://github.com/llrr586570/Good/tree/main/team/airdrop/ERC20Airdrop2.sol#L71:71

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol


91              claimStart = _claimStart;


92              claimEnd = _claimEnd;


```

https://github.com/llrr586570/Good/tree/main/team/airdrop/MerkleClaimable.sol#L92:92

```solidity
File: contracts/thirdparty/solmate/LibFixedPointMath.sol


76                  r = int256(


```

https://github.com/llrr586570/Good/tree/main/thirdparty/solmate/LibFixedPointMath.sol#L76:76

```solidity
File: contracts/tokenvault/BridgedERC1155.sol


57              srcChainId = _srcChainId;


```

https://github.com/llrr586570/Good/tree/main/tokenvault/BridgedERC1155.sol#L57:57

```solidity
File: contracts/tokenvault/BridgedERC20.sol


74              srcChainId = _srcChainId;


75              __srcDecimals = _decimals;


```

https://github.com/llrr586570/Good/tree/main/tokenvault/BridgedERC20.sol#L75:75

```solidity
File: contracts/tokenvault/BridgedERC721.sol


48              srcChainId = _srcChainId;


```

https://github.com/llrr586570/Good/tree/main/tokenvault/BridgedERC721.sol#L48:48

```solidity
File: contracts/tokenvault/ERC20Vault.sol


361                 balanceChange_ = _amount;


```

https://github.com/llrr586570/Good/tree/main/tokenvault/ERC20Vault.sol#L361:361

</details>

## L016 - Pausing withdrawals is unfair to the users:

Users should always have the possibility of accessing their own funds, but when these functions are paused, their funds will be locked until the contracts are unpaused.


```solidity
File: contracts/L2/TaikoL2.sol


163         function withdraw(


```

https://github.com/llrr586570/Good/tree/main/L2/TaikoL2.sol#L163:163

## L017 - Double type casts create complexity within the code:

Double type casting should be avoided in Solidity contracts to prevent unintended consequences and ensure accurate data representation. Performing multiple type casts in succession can lead to unexpected truncation, rounding errors, or loss of precision, potentially compromising the contract's functionality and reliability. Furthermore, double type casting can make the code less readable and harder to maintain, increasing the likelihood of errors and misunderstandings during development and debugging. To ensure precise and consistent data handling, developers should use appropriate data types and avoid unnecessary or excessive type casting, promoting a more robust and dependable contract execution.


<details>
<summary>Click to show 16 findings</summary>

```solidity
File: contracts/L1/libs/LibDepositing.sol


recipient: address(uint160(data >> 96)),

return (uint256(uint160(_addr)) << 96) | _amount;

```

https://github.com/llrr586570/Good/tree/main/L1/libs/LibDepositing.sol#L151:151

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol


? uint16(bytes2(svnValueBytes)) / 256

: uint16(bytes2(svnValueBytes));

```

https://github.com/llrr586570/Good/tree/main/automata-attestation/lib/PEMCertChainLib.sol#L360:360

```solidity
File: contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol


uint256 digits = uint256(uint8(bytes1(encoded[i])));

```

https://github.com/llrr586570/Good/tree/main/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L154:154

```solidity
File: contracts/automata-attestation/utils/BytesUtils.sol


decoded = uint8(BASE32_HEX_TABLE[uint256(uint8(char)) - 0x30]);

```

https://github.com/llrr586570/Good/tree/main/automata-attestation/utils/BytesUtils.sol#L336:336

```solidity
File: contracts/automata-attestation/utils/SigVerifyLib.sol


uint256 r = uint256(bytes32(signature.substring(0, 32)));

uint256 s = uint256(bytes32(signature.substring(32, 32)));

uint256 gx = uint256(bytes32(publicKey.substring(0, 32)));

uint256 gy = uint256(bytes32(publicKey.substring(32, 32)));

```

https://github.com/llrr586570/Good/tree/main/automata-attestation/utils/SigVerifyLib.sol#L133:133

```solidity
File: contracts/bridge/Bridge.sol


return _msgHash ^ bytes32(uint256(Status.FAILED));

_storeContext(bytes32(PLACEHOLDER), address(uint160(PLACEHOLDER)), uint64(PLACEHOLDER));

```

https://github.com/llrr586570/Good/tree/main/bridge/Bridge.sol#L533:533

```solidity
File: contracts/thirdparty/optimism/rlp/RLPWriter.sol


out_[i] = bytes1(uint8((_len / (256 ** (lenLen - i))) % 256));

```

https://github.com/llrr586570/Good/tree/main/thirdparty/optimism/rlp/RLPWriter.sol#L47:47

```solidity
File: contracts/verifiers/SgxVerifier.sol


_address[0] = address(bytes20(_attestation.localEnclaveReport.reportData));

uint32 id = uint32(bytes4(Bytes.slice(_proof.data, 0, 4)));

address newInstance = address(bytes20(Bytes.slice(_proof.data, 4, 20)));

```

https://github.com/llrr586570/Good/tree/main/verifiers/SgxVerifier.sol#L155:155

</details>

## L018 - Constructor contains no validation:

In Solidity, when values are being assigned in constructors to unsigned or integer variables, it's crucial to ensure the provided values adhere to the protocol's specific operational boundaries as laid out in the project specifications and documentation. If the constructors lack appropriate validation checks, there's a risk of setting state variables with values that could cause unexpected and potentially detrimental behavior within the contract's operations, violating the intended logic of the protocol. This can compromise the contract's security and impact the maintainability and reliability of the system. In order to avoid such issues, it is recommended to incorporate rigorous validation checks in constructors. These checks should align with the project's defined rules and constraints, making use of Solidity's built-in require function to enforce these conditions. If the validation checks fail, the require function will cause the transaction to revert, ensuring the integrity and adherence to the protocol's expected behavior.


```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol


54          constructor(address sigVerifyLibAddr, address pemCertLibAddr) {
55              sigVerifyLib = ISigVerifyLib(sigVerifyLibAddr);
56              pemCertLib = PEMCertChainLib(pemCertLibAddr);
57              owner = msg.sender;
58          }


```

https://github.com/llrr586570/Good/tree/main/automata-attestation/AutomataDcapV3Attestation.sol#L54:58

```solidity
File: contracts/automata-attestation/utils/SigVerifyLib.sol


20          constructor(address es256Verifier) {
21              ES256VERIFIER = es256Verifier;
22          }


```

https://github.com/llrr586570/Good/tree/main/automata-attestation/utils/SigVerifyLib.sol#L20:22

## L019 - For loops in `public` or `external` functions should be avoided due to high gas costs and possible DOS:

In Solidity, for loops can potentially cause Denial of Service (DoS) attacks if not handled carefully. DoS attacks can occur when an attacker intentionally exploits the gas cost of a function, causing it to run out of gas or making it too expensive for other users to call. Below are some scenarios where for loops can lead to DoS attacks: Nested for loops can become exceptionally gas expensive and should be used sparingly.


<details>
<summary>Click to show 10 findings</summary>

```solidity
File: contracts/L1/provers/Guardians.sol


53          function setGuardians(
54              address[] memory _newGuardians,
55              uint8 _minGuardians
56          )
57              external
58              onlyOwner
59              nonReentrant
60          {
61              // We need at least MIN_NUM_GUARDIANS and at most 255 guardians (so the approval bits fit in
62              // a uint256)
63              if (_newGuardians.length < MIN_NUM_GUARDIANS || _newGuardians.length > type(uint8).max) {
64                  revert INVALID_GUARDIAN_SET();
65              }
66              // Minimum number of guardians to approve is at least equal or greater than half the
67              // guardians (rounded up) and less or equal than the total number of guardians
68              if (_minGuardians < (_newGuardians.length + 1) >> 1 || _minGuardians > _newGuardians.length)
69              {
70                  revert INVALID_MIN_GUARDIANS();
71              }
72      
73              // Delete the current guardians
74              for (uint256 i; i < guardians.length; ++i) {
75                  delete guardianIds[guardians[i]];
76              }
77              delete guardians;
78      
79              // Set the new guardians
80              for (uint256 i = 0; i < _newGuardians.length; ++i) {
81                  address guardian = _newGuardians[i];
82                  if (guardian == address(0)) revert INVALID_GUARDIAN();
83                  // This makes sure there are not duplicate addresses
84                  if (guardianIds[guardian] != 0) revert INVALID_GUARDIAN_SET();
85      
86                  // Save and index the guardian
87                  guardians.push(guardian);
88                  guardianIds[guardian] = guardians.length;
89              }
90      
91              // Bump the version so previous approvals get invalidated
92              ++version;
93      
94              minGuardians = _minGuardians;
95              emit GuardiansUpdated(version, _newGuardians);
96          }


```

https://github.com/llrr586570/Good/tree/main/L1/provers/Guardians.sol#L53:96

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol


73          function addRevokedCertSerialNum(
74              uint256 index,
75              bytes[] calldata serialNumBatch
76          )
77              external
78              onlyOwner
79          {
80              for (uint256 i; i < serialNumBatch.length; ++i) {
81                  if (_serialNumIsRevoked[index][serialNumBatch[i]]) {
82                      continue;
83                  }
84                  _serialNumIsRevoked[index][serialNumBatch[i]] = true;
85              }
86          }


88          function removeRevokedCertSerialNum(
89              uint256 index,
90              bytes[] calldata serialNumBatch
91          )
92              external
93              onlyOwner
94          {
95              for (uint256 i; i < serialNumBatch.length; ++i) {
96                  if (!_serialNumIsRevoked[index][serialNumBatch[i]]) {
97                      continue;
98                  }
99                  delete _serialNumIsRevoked[index][serialNumBatch[i]];
100             }
101         }


```

https://github.com/llrr586570/Good/tree/main/automata-attestation/AutomataDcapV3Attestation.sol#L88:101

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol


40          function splitCertificateChain(
41              bytes memory pemChain,
42              uint256 size
43          )
44              external
45              pure
46              returns (bool success, bytes[] memory certs)
47          {
48              certs = new bytes[](size);
49              string memory pemChainStr = string(pemChain);
50      
51              uint256 index = 0;
52              uint256 len = pemChain.length;
53      
54              for (uint256 i; i < size; ++i) {
55                  string memory input;
56                  if (i > 0) {
57                      input = LibString.slice(pemChainStr, index, index + len);
58                  } else {
59                      input = pemChainStr;
60                  }
61                  uint256 increment;
62                  (success, certs[i], increment) = _removeHeadersAndFooters(input);
63      
64                  if (!success) {
65                      return (false, certs);
66                  }
67      
68                  index += increment;
69              }
70      
71              success = true;
72          }


```

https://github.com/llrr586570/Good/tree/main/automata-attestation/lib/PEMCertChainLib.sol#L40:72

```solidity
File: contracts/bridge/Bridge.sol


82          function suspendMessages(
83              bytes32[] calldata _msgHashes,
84              bool _suspend
85          )
86              external
87              onlyFromOwnerOrNamed("bridge_watchdog")
88          {
89              uint64 _timestamp = _suspend ? type(uint64).max : uint64(block.timestamp);
90              for (uint256 i; i < _msgHashes.length; ++i) {
91                  bytes32 msgHash = _msgHashes[i];
92                  proofReceipt[msgHash].receivedAt = _timestamp;
93                  emit MessageSuspended(msgHash, _suspend);
94              }
95          }


```

https://github.com/llrr586570/Good/tree/main/bridge/Bridge.sol#L82:95

```solidity
File: contracts/signal/SignalService.sol


83          function proveSignalReceived(
84              uint64 _chainId,
85              address _app,
86              bytes32 _signal,
87              bytes calldata _proof
88          )
89              public
90              virtual
91              validSender(_app)
92              nonZeroValue(_signal)
93          {
94              HopProof[] memory hopProofs = abi.decode(_proof, (HopProof[]));
95              if (hopProofs.length == 0) revert SS_EMPTY_PROOF();
96      
97              uint64 chainId = _chainId;
98              address app = _app;
99              bytes32 signal = _signal;
100             bytes32 value = _signal;
101             address signalService = resolve(chainId, "signal_service", false);
102     
103             HopProof memory hop;
104             for (uint256 i; i < hopProofs.length; ++i) {
105                 hop = hopProofs[i];
106     
107                 bytes32 signalRoot = _verifyHopProof(chainId, app, signal, value, hop, signalService);
108                 bool isLastHop = i == hopProofs.length - 1;
109     
110                 if (isLastHop) {
111                     if (hop.chainId != block.chainid) revert SS_INVALID_LAST_HOP_CHAINID();
112                     signalService = address(this);
113                 } else {
114                     if (hop.chainId == 0 || hop.chainId == block.chainid) {
115                         revert SS_INVALID_MID_HOP_CHAINID();
116                     }
117                     signalService = resolve(hop.chainId, "signal_service", false);
118                 }
119     
120                 bool isFullProof = hop.accountProof.length > 0;
121     
122                 _cacheChainData(hop, chainId, hop.blockId, signalRoot, isFullProof, isLastHop);
123     
124                 bytes32 kind = isFullProof ? LibSignals.STATE_ROOT : LibSignals.SIGNAL_ROOT;
125                 signal = signalForChainData(chainId, kind, hop.blockId);
126                 value = hop.rootHash;
127                 chainId = hop.chainId;
128                 app = signalService;
129             }
130     
131             if (value == 0 || value != _loadSignalValue(address(this), signal)) {
132                 revert SS_SIGNAL_NOT_FOUND();
133             }
134         }


```

https://github.com/llrr586570/Good/tree/main/signal/SignalService.sol#L83:134

```solidity
File: contracts/team/airdrop/ERC721Airdrop.sol


47          function claim(
48              address user,
49              uint256[] calldata tokenIds,
50              bytes32[] calldata proof
51          )
52              external
53              nonReentrant
54          {
55              // Check if this can be claimed
56              _verifyClaim(abi.encode(user, tokenIds), proof);
57      
58              // Transfer the tokens
59              for (uint256 i; i < tokenIds.length; ++i) {
60                  IERC721(token).safeTransferFrom(vault, user, tokenIds[i]);
61              }
62          }


```

https://github.com/llrr586570/Good/tree/main/team/airdrop/ERC721Airdrop.sol#L47:62

```solidity
File: contracts/tokenvault/ERC1155Vault.sol


39          function sendToken(BridgeTransferOp memory _op)
40              external
41              payable
42              nonReentrant
43              whenNotPaused
44              withValidOperation(_op)
45              returns (IBridge.Message memory message_)
46          {
47              for (uint256 i; i < _op.amounts.length; ++i) {
48                  if (_op.amounts[i] == 0) revert VAULT_INVALID_AMOUNT();
49              }
50              // Check token interface support
51              if (!_op.token.supportsInterface(ERC1155_INTERFACE_ID)) {
52                  revert VAULT_INTERFACE_NOT_SUPPORTED();
53              }
54      
55              (bytes memory data, CanonicalNFT memory ctoken) = _handleMessage(msg.sender, _op);
56      
57              // Create a message to send to the destination chain
58              IBridge.Message memory message = IBridge.Message({
59                  id: 0, // will receive a new value
60                  from: address(0), // will receive a new value
61                  srcChainId: 0, // will receive a new value
62                  destChainId: _op.destChainId,
63                  srcOwner: msg.sender,
64                  destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,
65                  to: resolve(_op.destChainId, name(), false),
66                  refundTo: _op.refundTo,
67                  value: msg.value - _op.fee,
68                  fee: _op.fee,
69                  gasLimit: _op.gasLimit,
70                  data: data,
71                  memo: _op.memo
72              });
73      
74              // Send the message and obtain the message hash
75              bytes32 msgHash;
76              (msgHash, message_) =
77                  IBridge(resolve("bridge", false)).sendMessage{ value: msg.value }(message);
78      
79              // Emit TokenSent event
80              emit TokenSent({
81                  msgHash: msgHash,
82                  from: message_.srcOwner,
83                  to: _op.to,
84                  destChainId: message_.destChainId,
85                  ctoken: ctoken.addr,
86                  token: _op.token,
87                  tokenIds: _op.tokenIds,
88                  amounts: _op.amounts
89              });
90          }


```

https://github.com/llrr586570/Good/tree/main/tokenvault/ERC1155Vault.sol#L39:90

```solidity
File: contracts/tokenvault/ERC721Vault.sol


26          function sendToken(BridgeTransferOp memory _op)
27              external
28              payable
29              nonReentrant
30              whenNotPaused
31              withValidOperation(_op)
32              returns (IBridge.Message memory message_)
33          {
34              for (uint256 i; i < _op.tokenIds.length; ++i) {
35                  if (_op.amounts[i] != 0) revert VAULT_INVALID_AMOUNT();
36              }
37      
38              if (!_op.token.supportsInterface(ERC721_INTERFACE_ID)) {
39                  revert VAULT_INTERFACE_NOT_SUPPORTED();
40              }
41      
42              (bytes memory data, CanonicalNFT memory ctoken) = _handleMessage(msg.sender, _op);
43      
44              IBridge.Message memory message = IBridge.Message({
45                  id: 0, // will receive a new value
46                  from: address(0), // will receive a new value
47                  srcChainId: 0, // will receive a new value
48                  destChainId: _op.destChainId,
49                  srcOwner: msg.sender,
50                  destOwner: _op.destOwner != address(0) ? _op.destOwner : msg.sender,
51                  to: resolve(_op.destChainId, name(), false),
52                  refundTo: _op.refundTo,
53                  value: msg.value - _op.fee,
54                  fee: _op.fee,
55                  gasLimit: _op.gasLimit,
56                  data: data,
57                  memo: _op.memo
58              });
59      
60              bytes32 msgHash;
61              (msgHash, message_) =
62                  IBridge(resolve("bridge", false)).sendMessage{ value: msg.value }(message);
63      
64              emit TokenSent({
65                  msgHash: msgHash,
66                  from: message_.srcOwner,
67                  to: _op.to,
68                  destChainId: message_.destChainId,
69                  ctoken: ctoken.addr,
70                  token: _op.token,
71                  tokenIds: _op.tokenIds,
72                  amounts: _op.amounts
73              });
74          }


```

https://github.com/llrr586570/Good/tree/main/tokenvault/ERC721Vault.sol#L26:74

```solidity
File: contracts/verifiers/SgxVerifier.sol


100         function deleteInstances(uint256[] calldata _ids)
101             external
102             onlyFromOwnerOrNamed("rollup_watchdog")
103         {
104             for (uint256 i; i < _ids.length; ++i) {
105                 uint256 idx = _ids[i];
106     
107                 if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();
108     
109                 emit InstanceDeleted(idx, instances[idx].addr);
110     
111                 delete instances[idx];
112             }
113         }


```

https://github.com/llrr586570/Good/tree/main/verifiers/SgxVerifier.sol#L100:113

</details>

## L020 - Function calls within for loops:

Making function calls within loops in Solidity can lead to inefficient gas usage, potential bottlenecks, and increased vulnerability to attacks. Each function call or external call consumes gas, and when executed within a loop, the gas cost multiplies, potentially causing the transaction to run out of gas or exceed block gas limits. This can result in transaction failure or unpredictable behavior.


<details>
<summary>Click to show 5 findings</summary>

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol


214             for (uint256 i; i < tcb.tcbLevels.length; ++i) {
215                 TCBInfoStruct.TCBLevelObj memory current = tcb.tcbLevels[i];
216                 bool pceSvnIsHigherOrGreater = pck.sgxExtension.pcesvn >= current.pcesvn;
217                 bool cpuSvnsAreHigherOrGreater = _isCpuSvnHigherOrGreater(
218                     pck.sgxExtension.sgxTcbCompSvnArr, current.sgxTcbCompSvnArr
219                 );
220                 if (pceSvnIsHigherOrGreater && cpuSvnsAreHigherOrGreater) {
221                     status = current.status;
222                     bool tcbIsRevoked = status == TCBInfoStruct.TCBStatus.TCB_REVOKED;
223                     return (!tcbIsRevoked, status);
224                 }
225             }


```

https://github.com/llrr586570/Good/tree/main/automata-attestation/AutomataDcapV3Attestation.sol#L214:225

```solidity
File: contracts/automata-attestation/lib/PEMCertChainLib.sol


54              for (uint256 i; i < size; ++i) {
55                  string memory input;
56                  if (i > 0) {
57                      input = LibString.slice(pemChainStr, index, index + len);
58                  } else {
59                      input = pemChainStr;
60                  }
61                  uint256 increment;
62                  (success, certs[i], increment) = _removeHeadersAndFooters(input);
63      
64                  if (!success) {
65                      return (false, certs);
66                  }
67      
68                  index += increment;
69              }


```

https://github.com/llrr586570/Good/tree/main/automata-attestation/lib/PEMCertChainLib.sol#L54:69

```solidity
File: contracts/automata-attestation/utils/X509DateUtils.sol


48              for (uint16 i = 1970; i < year; ++i) {
49                  if (isLeapYear(i)) {
50                      timestamp += 31_622_400; // Leap year in seconds
51                  } else {
52                      timestamp += 31_536_000; // Normal year in seconds
53                  }
54              }


```

https://github.com/llrr586570/Good/tree/main/automata-attestation/utils/X509DateUtils.sol#L48:54

```solidity
File: contracts/signal/SignalService.sol


104             for (uint256 i; i < hopProofs.length; ++i) {
105                 hop = hopProofs[i];
106     
107                 bytes32 signalRoot = _verifyHopProof(chainId, app, signal, value, hop, signalService);
108                 bool isLastHop = i == hopProofs.length - 1;
109     
110                 if (isLastHop) {
111                     if (hop.chainId != block.chainid) revert SS_INVALID_LAST_HOP_CHAINID();
112                     signalService = address(this);
113                 } else {
114                     if (hop.chainId == 0 || hop.chainId == block.chainid) {
115                         revert SS_INVALID_MID_HOP_CHAINID();
116                     }
117                     signalService = resolve(hop.chainId, "signal_service", false);
118                 }
119     
120                 bool isFullProof = hop.accountProof.length > 0;
121     
122                 _cacheChainData(hop, chainId, hop.blockId, signalRoot, isFullProof, isLastHop);
123     
124                 bytes32 kind = isFullProof ? LibSignals.STATE_ROOT : LibSignals.SIGNAL_ROOT;
125                 signal = signalForChainData(chainId, kind, hop.blockId);
126                 value = hop.rootHash;
127                 chainId = hop.chainId;
128                 app = signalService;
129             }


```

https://github.com/llrr586570/Good/tree/main/signal/SignalService.sol#L104:129

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol


85              for (uint256 i = 0; i < proof.length; i++) {
86                  TrieNode memory currentNode = proof[i];
87      
88                  // Key index should never exceed total key length or we'll be out of bounds.
89                  require(currentKeyIndex <= key.length, "MerkleTrie: key index exceeds total key length");
90      
91                  if (currentKeyIndex == 0) {
92                      // First proof element is always the root node.
93                      require(
94                          Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
95                          "MerkleTrie: invalid root hash"
96                      );
97                  } else if (currentNode.encoded.length >= 32) {
98                      // Nodes 32 bytes or larger are hashed inside branch nodes.
99                      require(
100                         Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
101                         "MerkleTrie: invalid large internal hash"
102                     );
103                 } else {
104                     // Nodes smaller than 32 bytes aren't hashed.
105                     require(
106                         Bytes.equal(currentNode.encoded, currentNodeID),
107                         "MerkleTrie: invalid internal node hash"
108                     );
109                 }
110     
111                 if (currentNode.decoded.length == BRANCH_NODE_LENGTH) {
112                     if (currentKeyIndex == key.length) {
113                         // Value is the last element of the decoded list (for branch nodes). There's
114                         // some ambiguity in the Merkle trie specification because bytes(0) is a
115                         // valid value to place into the trie, but for branch nodes bytes(0) can exist
116                         // even when the value wasn't explicitly placed there. Geth treats a value of
117                         // bytes(0) as "key does not exist" and so we do the same.
118                         value_ = RLPReader.readBytes(currentNode.decoded[TREE_RADIX]);
119                         require(
120                             value_.length > 0,
121                             "MerkleTrie: value length must be greater than zero (branch)"
122                         );
123     
124                         // Extra proof elements are not allowed.
125                         require(
126                             i == proof.length - 1,
127                             "MerkleTrie: value node must be last node in proof (branch)"
128                         );
129     
130                         return value_;
131                     } else {
132                         // We're not at the end of the key yet.
133                         // Figure out what the next node ID should be and continue.
134                         uint8 branchKey = uint8(key[currentKeyIndex]);
135                         RLPReader.RLPItem memory nextNode = currentNode.decoded[branchKey];
136                         currentNodeID = _getNodeID(nextNode);
137                         currentKeyIndex += 1;
138                     }
139                 } else if (currentNode.decoded.length == LEAF_OR_EXTENSION_NODE_LENGTH) {
140                     bytes memory path = _getNodePath(currentNode);
141                     uint8 prefix = uint8(path[0]);
142                     uint8 offset = 2 - (prefix % 2);
143                     bytes memory pathRemainder = Bytes.slice(path, offset);
144                     bytes memory keyRemainder = Bytes.slice(key, currentKeyIndex);
145                     uint256 sharedNibbleLength = _getSharedNibbleLength(pathRemainder, keyRemainder);
146     
147                     // Whether this is a leaf node or an extension node, the path remainder MUST be a
148                     // prefix of the key remainder (or be equal to the key remainder) or the proof is
149                     // considered invalid.
150                     require(
151                         pathRemainder.length == sharedNibbleLength,
152                         "MerkleTrie: path remainder must share all nibbles with key"
153                     );
154     
155                     if (prefix == PREFIX_LEAF_EVEN || prefix == PREFIX_LEAF_ODD) {
156                         // Prefix of 2 or 3 means this is a leaf node. For the leaf node to be valid,
157                         // the key remainder must be exactly equal to the path remainder. We already
158                         // did the necessary byte comparison, so it's more efficient here to check that
159                         // the key remainder length equals the shared nibble length, which implies
160                         // equality with the path remainder (since we already did the same check with
161                         // the path remainder and the shared nibble length).
162                         require(
163                             keyRemainder.length == sharedNibbleLength,
164                             "MerkleTrie: key remainder must be identical to path remainder"
165                         );
166     
167                         // Our Merkle Trie is designed specifically for the purposes of the Ethereum
168                         // state trie. Empty values are not allowed in the state trie, so we can safely
169                         // say that if the value is empty, the key should not exist and the proof is
170                         // invalid.
171                         value_ = RLPReader.readBytes(currentNode.decoded[1]);
172                         require(
173                             value_.length > 0,
174                             "MerkleTrie: value length must be greater than zero (leaf)"
175                         );
176     
177                         // Extra proof elements are not allowed.
178                         require(
179                             i == proof.length - 1,
180                             "MerkleTrie: value node must be last node in proof (leaf)"
181                         );
182     
183                         return value_;
184                     } else if (prefix == PREFIX_EXTENSION_EVEN || prefix == PREFIX_EXTENSION_ODD) {
185                         // Prefix of 0 or 1 means this is an extension node. We move onto the next node
186                         // in the proof and increment the key index by the length of the path remainder
187                         // which is equal to the shared nibble length.
188                         currentNodeID = _getNodeID(currentNode.decoded[1]);
189                         currentKeyIndex += sharedNibbleLength;
190                     } else {
191                         revert("MerkleTrie: received a node with an unknown prefix");
192                     }
193                 } else {
194                     revert("MerkleTrie: received an unparseable node");
195                 }
196             }


```

https://github.com/llrr586570/Good/tree/main/thirdparty/optimism/trie/MerkleTrie.sol#L85:196

</details>

## L021 - External calls in an unbounded for-loop may result in a DoS:

Consider limiting the number of iterations in for-loops that make external calls.


<details>
<summary>Click to show 16 findings</summary>

```solidity
File: contracts/L1/libs/LibProposing.sol


244                 for (uint256 i; i < params.hookCalls.length; ++i) {


```

https://github.com/llrr586570/Good/tree/main/L1/libs/LibProposing.sol#L244:244

```solidity
File: contracts/L1/provers/Guardians.sol


80              for (uint256 i = 0; i < _newGuardians.length; ++i) {


```

https://github.com/llrr586570/Good/tree/main/L1/provers/Guardians.sol#L80:80

```solidity
File: contracts/L2/TaikoL2.sol


234                 for (uint256 i; i < 255 && _blockId >= i + 1; ++i) {


```

https://github.com/llrr586570/Good/tree/main/L2/TaikoL2.sol#L234:234

```solidity
File: contracts/bridge/Bridge.sol


90              for (uint256 i; i < _msgHashes.length; ++i) {


```

https://github.com/llrr586570/Good/tree/main/bridge/Bridge.sol#L90:90

```solidity
File: contracts/signal/SignalService.sol


104             for (uint256 i; i < hopProofs.length; ++i) {


```

https://github.com/llrr586570/Good/tree/main/signal/SignalService.sol#L104:104

```solidity
File: contracts/team/airdrop/ERC721Airdrop.sol


59              for (uint256 i; i < tokenIds.length; ++i) {


```

https://github.com/llrr586570/Good/tree/main/team/airdrop/ERC721Airdrop.sol#L59:59

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol


85              for (uint256 i = 0; i < proof.length; i++) {


```

https://github.com/llrr586570/Good/tree/main/thirdparty/optimism/trie/MerkleTrie.sol#L85:85

```solidity
File: contracts/tokenvault/ERC1155Vault.sol


47              for (uint256 i; i < _op.amounts.length; ++i) {


251                     for (uint256 i; i < _op.tokenIds.length; ++i) {


269                     for (uint256 i; i < _op.tokenIds.length; ++i) {


```

https://github.com/llrr586570/Good/tree/main/tokenvault/ERC1155Vault.sol#L269:269

```solidity
File: contracts/tokenvault/ERC721Vault.sol


34              for (uint256 i; i < _op.tokenIds.length; ++i) {


170                 for (uint256 i; i < _tokenIds.length; ++i) {


175                 for (uint256 i; i < _tokenIds.length; ++i) {


197                     for (uint256 i; i < _op.tokenIds.length; ++i) {


```

https://github.com/llrr586570/Good/tree/main/tokenvault/ERC721Vault.sol#L197:197

```solidity
File: contracts/verifiers/SgxVerifier.sol


104             for (uint256 i; i < _ids.length; ++i) {


210             for (uint256 i; i < _instances.length; ++i) {


```

https://github.com/llrr586570/Good/tree/main/verifiers/SgxVerifier.sol#L210:210

</details>

## L022 - Contracts are not using their OZ Upgradeable counterparts:

The non-upgradeable standard version of OpenZeppelin’s library is inherited/used by the contracts. It would be safer to use the upgradeable versions of the library contracts to avoid unexpected behavior.

Use the contracts from `@openzeppelin/contracts-upgradeable` instead of `@openzeppelin/contracts` where applicable. See https://github.com/OpenZeppelin/openzeppelin-contracts-upgradeable/tree/master/contracts for a list of available upgradeable contracts


<details>
<summary>Click to show 54 findings</summary>

```solidity
File: contracts/L1/TaikoToken.sol


4       import "@openzeppelin/contracts-upgradeable/token/ERC20/ERC20Upgradeable.sol";


5       import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20SnapshotUpgradeable.sol";


6       import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20VotesUpgradeable.sol";


```

https://github.com/llrr586570/Good/tree/main/L1/TaikoToken.sol#L6:6

```solidity
File: contracts/L1/gov/TaikoGovernor.sol


4       import "@openzeppelin/contracts-upgradeable/governance/GovernorUpgradeable.sol";


8       import


5       import


7       import "@openzeppelin/contracts-upgradeable/governance/extensions/GovernorVotesUpgradeable.sol";


10      import


```

https://github.com/llrr586570/Good/tree/main/L1/gov/TaikoGovernor.sol#L10:10

```solidity
File: contracts/L1/gov/TaikoTimelockController.sol


4       import "@openzeppelin/contracts-upgradeable/governance/TimelockControllerUpgradeable.sol";


```

https://github.com/llrr586570/Good/tree/main/L1/gov/TaikoTimelockController.sol#L4:4

```solidity
File: contracts/L1/hooks/AssignmentHook.sol


4       import "@openzeppelin/contracts/token/ERC20/IERC20.sol";


5       import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";


```

https://github.com/llrr586570/Good/tree/main/L1/hooks/AssignmentHook.sol#L5:5

```solidity
File: contracts/L1/libs/LibProposing.sol


4       import "@openzeppelin/contracts/token/ERC20/IERC20.sol";


```

https://github.com/llrr586570/Good/tree/main/L1/libs/LibProposing.sol#L4:4

```solidity
File: contracts/L1/libs/LibProving.sol


4       import "@openzeppelin/contracts/token/ERC20/IERC20.sol";


```

https://github.com/llrr586570/Good/tree/main/L1/libs/LibProving.sol#L4:4

```solidity
File: contracts/L1/libs/LibVerifying.sol


4       import "@openzeppelin/contracts/token/ERC20/IERC20.sol";


```

https://github.com/llrr586570/Good/tree/main/L1/libs/LibVerifying.sol#L4:4

```solidity
File: contracts/L2/CrossChainOwned.sol


4       import "@openzeppelin/contracts/token/ERC20/IERC20.sol";


```

https://github.com/llrr586570/Good/tree/main/L2/CrossChainOwned.sol#L4:4

```solidity
File: contracts/L2/TaikoL2.sol


4       import "@openzeppelin/contracts/token/ERC20/IERC20.sol";


5       import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";


```

https://github.com/llrr586570/Good/tree/main/L2/TaikoL2.sol#L5:5

```solidity
File: contracts/bridge/Bridge.sol


4       import "@openzeppelin/contracts/utils/Address.sol";


```

https://github.com/llrr586570/Good/tree/main/bridge/Bridge.sol#L4:4

```solidity
File: contracts/common/AddressResolver.sol


4       import "@openzeppelin/contracts-upgradeable/proxy/utils/Initializable.sol";


```

https://github.com/llrr586570/Good/tree/main/common/AddressResolver.sol#L4:4

```solidity
File: contracts/common/EssentialContract.sol


4       import "@openzeppelin/contracts/proxy/utils/UUPSUpgradeable.sol";


5       import "@openzeppelin/contracts-upgradeable/access/Ownable2StepUpgradeable.sol";


```

https://github.com/llrr586570/Good/tree/main/common/EssentialContract.sol#L5:5

```solidity
File: contracts/libs/LibAddress.sol


4       import "@openzeppelin/contracts/utils/Address.sol";


5       import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol";


6       import "@openzeppelin/contracts/utils/introspection/IERC165.sol";


7       import "@openzeppelin/contracts/interfaces/IERC1271.sol";


```

https://github.com/llrr586570/Good/tree/main/libs/LibAddress.sol#L7:7

```solidity
File: contracts/signal/SignalService.sol


4       import "@openzeppelin/contracts/utils/math/SafeCast.sol";


```

https://github.com/llrr586570/Good/tree/main/signal/SignalService.sol#L4:4

```solidity
File: contracts/team/TimelockTokenPool.sol


4       import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol";


5       import "@openzeppelin/contracts/token/ERC20/IERC20.sol";


6       import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";


```

https://github.com/llrr586570/Good/tree/main/team/TimelockTokenPool.sol#L6:6

```solidity
File: contracts/team/airdrop/ERC20Airdrop.sol


4       import "@openzeppelin/contracts/token/ERC20/IERC20.sol";


5       import "@openzeppelin/contracts/governance/utils/IVotes.sol";


```

https://github.com/llrr586570/Good/tree/main/team/airdrop/ERC20Airdrop.sol#L5:5

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol


4       import "@openzeppelin/contracts/token/ERC20/IERC20.sol";


```

https://github.com/llrr586570/Good/tree/main/team/airdrop/ERC20Airdrop2.sol#L4:4

```solidity
File: contracts/team/airdrop/ERC721Airdrop.sol


4       import "@openzeppelin/contracts/token/ERC721/IERC721.sol";


```

https://github.com/llrr586570/Good/tree/main/team/airdrop/ERC721Airdrop.sol#L4:4

```solidity
File: contracts/team/airdrop/MerkleClaimable.sol


4       import "@openzeppelin/contracts/utils/cryptography/MerkleProof.sol";


```

https://github.com/llrr586570/Good/tree/main/team/airdrop/MerkleClaimable.sol#L4:4

```solidity
File: contracts/tokenvault/BaseVault.sol


4       import "@openzeppelin/contracts-upgradeable/utils/introspection/IERC165Upgradeable.sol";


5       import "@openzeppelin/contracts/proxy/ERC1967/ERC1967Proxy.sol";


```

https://github.com/llrr586570/Good/tree/main/tokenvault/BaseVault.sol#L5:5

```solidity
File: contracts/tokenvault/BridgedERC1155.sol


4       import "@openzeppelin/contracts/utils/Strings.sol";


5       import "@openzeppelin/contracts-upgradeable/token/ERC1155/ERC1155Upgradeable.sol";


6       import


```

https://github.com/llrr586570/Good/tree/main/tokenvault/BridgedERC1155.sol#L6:6

```solidity
File: contracts/tokenvault/BridgedERC20.sol


4       import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/IERC20MetadataUpgradeable.sol";


5       import "@openzeppelin/contracts/utils/Strings.sol";


6       import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20SnapshotUpgradeable.sol";


7       import "@openzeppelin/contracts-upgradeable/token/ERC20/extensions/ERC20VotesUpgradeable.sol";


```

https://github.com/llrr586570/Good/tree/main/tokenvault/BridgedERC20.sol#L7:7

```solidity
File: contracts/tokenvault/BridgedERC721.sol


4       import "@openzeppelin/contracts-upgradeable/token/ERC721/ERC721Upgradeable.sol";


5       import "@openzeppelin/contracts/utils/Strings.sol";


```

https://github.com/llrr586570/Good/tree/main/tokenvault/BridgedERC721.sol#L5:5

```solidity
File: contracts/tokenvault/ERC1155Vault.sol


4       import "@openzeppelin/contracts/token/ERC1155/IERC1155.sol";


5       import "@openzeppelin/contracts-upgradeable/token/ERC1155/utils/ERC1155ReceiverUpgradeable.sol";


```

https://github.com/llrr586570/Good/tree/main/tokenvault/ERC1155Vault.sol#L5:5

```solidity
File: contracts/tokenvault/ERC20Vault.sol


4       import "@openzeppelin/contracts/token/ERC20/IERC20.sol";


5       import "@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol";


6       import "@openzeppelin/contracts/token/ERC20/utils/SafeERC20.sol";


```

https://github.com/llrr586570/Good/tree/main/tokenvault/ERC20Vault.sol#L6:6

```solidity
File: contracts/tokenvault/ERC721Vault.sol


4       import "@openzeppelin/contracts/token/ERC721/IERC721.sol";


5       import "@openzeppelin/contracts/token/ERC721/IERC721Receiver.sol";


```

https://github.com/llrr586570/Good/tree/main/tokenvault/ERC721Vault.sol#L5:5

```solidity
File: contracts/tokenvault/LibBridgedToken.sol


4       import "@openzeppelin/contracts/utils/Strings.sol";


```

https://github.com/llrr586570/Good/tree/main/tokenvault/LibBridgedToken.sol#L4:4

```solidity
File: contracts/verifiers/SgxVerifier.sol


4       import "@openzeppelin/contracts/utils/cryptography/ECDSA.sol";


```

https://github.com/llrr586570/Good/tree/main/verifiers/SgxVerifier.sol#L4:4

</details>

## L023 - Consider implementing two-step procedure for updating protocol addresses:

Lack of two-step procedure for critical operations leaves them error-prone. Consider adding two step procedure on the critical functions. See similar findings in previous Code4rena contests for reference: https://code4rena.com/reports/2022-06-illuminate/#2-critical-changes-should-use-two-step-procedure


```solidity
File: contracts/common/AddressManager.sol


38          function setAddress(


```

https://github.com/llrr586570/Good/tree/main/common/AddressManager.sol#L38:38

```solidity
File: contracts/tokenvault/BridgedERC20.sol


80          function setSnapshoter(address _snapshooter) external onlyOwner {


```

https://github.com/llrr586570/Good/tree/main/tokenvault/BridgedERC20.sol#L80:80

## L024 - `decimals()` is not a part of the ERC-20 standard:

The `decimals()` function is not a part of the [ERC-20 standard](https://eips.ethereum.org/EIPS/eip-20), and was added later as an [optional extension](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC20/extensions/IERC20Metadata.sol). As such, some valid ERC20 tokens do not support this interface, so it is unsafe to blindly cast all tokens to this interface, and then call this function.


<details>
<summary>Click to show 4 findings</summary>

```solidity
File: contracts/tokenvault/ERC20Vault.sol


415                     ctoken.decimals,


431                 ctokenDecimal: ctoken.decimals


175                     ctoken.decimals != _ctoken.decimals


198                 ctokenDecimal: _ctoken.decimals


```

https://github.com/llrr586570/Good/tree/main/tokenvault/ERC20Vault.sol#L198:198

</details>

## L025 - `symbol()` is not a part of the ERC-20 standard:

The `symbol()` function is not a part of the [ERC-20 standard](https://eips.ethereum.org/EIPS/eip-20), and was added later as an [optional extension](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC20/extensions/IERC20Metadata.sol). As such, some valid ERC20 tokens do not support this interface, so it is unsafe to blindly cast all tokens to this interface, and then call this function.


<details>
<summary>Click to show 9 findings</summary>

```solidity
File: contracts/tokenvault/ERC1155Vault.sol


318                 ctokenSymbol: _ctoken.symbol,


267                         ctoken_.symbol = _symbol;


306                 (owner(), addressManager, _ctoken.addr, _ctoken.chainId, _ctoken.symbol, _ctoken.name)


```

https://github.com/llrr586570/Good/tree/main/tokenvault/ERC1155Vault.sol#L306:306

```solidity
File: contracts/tokenvault/ERC20Vault.sol


176                         || keccak256(bytes(ctoken.symbol)) != keccak256(bytes(_ctoken.symbol))


429                 ctokenSymbol: ctoken.symbol,


416                     ctoken.symbol,


196                 ctokenSymbol: _ctoken.symbol,


```

https://github.com/llrr586570/Good/tree/main/tokenvault/ERC20Vault.sol#L196:196

```solidity
File: contracts/tokenvault/ERC721Vault.sol


243                 (owner(), addressManager, _ctoken.addr, _ctoken.chainId, _ctoken.symbol, _ctoken.name)


254                 ctokenSymbol: _ctoken.symbol,


```

https://github.com/llrr586570/Good/tree/main/tokenvault/ERC721Vault.sol#L254:254

</details>

## L026 - `name()` is not a part of the ERC-20 standard:

The `name()` function is not a part of the [ERC-20 standard](https://eips.ethereum.org/EIPS/eip-20), and was added later as an [optional extension](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC20/extensions/IERC20Metadata.sol). As such, some valid ERC20 tokens do not support this interface, so it is unsafe to blindly cast all tokens to this interface, and then call this function.


<details>
<summary>Click to show 9 findings</summary>

```solidity
File: contracts/tokenvault/ERC1155Vault.sol


306                 (owner(), addressManager, _ctoken.addr, _ctoken.chainId, _ctoken.symbol, _ctoken.name)


264                         ctoken_.name = _name;


319                 ctokenName: _ctoken.name


```

https://github.com/llrr586570/Good/tree/main/tokenvault/ERC1155Vault.sol#L319:319

```solidity
File: contracts/tokenvault/ERC20Vault.sol


197                 ctokenName: _ctoken.name,


177                         || keccak256(bytes(ctoken.name)) != keccak256(bytes(_ctoken.name))


417                     ctoken.name


430                 ctokenName: ctoken.name,


```

https://github.com/llrr586570/Good/tree/main/tokenvault/ERC20Vault.sol#L430:430

```solidity
File: contracts/tokenvault/ERC721Vault.sol


255                 ctokenName: _ctoken.name


243                 (owner(), addressManager, _ctoken.addr, _ctoken.chainId, _ctoken.symbol, _ctoken.name)


```

https://github.com/llrr586570/Good/tree/main/tokenvault/ERC721Vault.sol#L243:243

</details>

## L027 - Missing checks for address(0x0) in the constructor:




```solidity
File: contracts/automata-attestation/utils/SigVerifyLib.sol


21              ES256VERIFIER = es256Verifier;


```

https://github.com/llrr586570/Good/tree/main/automata-attestation/utils/SigVerifyLib.sol#L21:21

## L028 - Governance functions should be controlled by time locks:

Governance functions (such as upgrading contracts, setting critical parameters) should be controlled using time locks to introduce a delay between a proposal and its execution. This gives users time to exit before a potentially dangerous or malicious operation is applied.


<details>
<summary>Click to show 16 findings</summary>

```solidity
File: contracts/L1/TaikoToken.sol


47          function burn(address _from, uint256 _amount) public onlyOwner {

```

https://github.com/llrr586570/Good/tree/main/L1/TaikoToken.sol#L47:49

```solidity
File: contracts/L2/TaikoL2EIP1559Configurable.sol


25          function setConfigAndExcess(
26              Config memory _newConfig,
27              uint64 _newGasExcess
28          )
29              external
30              virtual
31              onlyOwner
32          {

```

https://github.com/llrr586570/Good/tree/main/L2/TaikoL2EIP1559Configurable.sol#L25:40

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol


69          function setMrEnclave(bytes32 _mrEnclave, bool _trusted) external onlyOwner {

73          function addRevokedCertSerialNum(
74              uint256 index,
75              bytes[] calldata serialNumBatch
76          )
77              external
78              onlyOwner
79          {

65          function setMrSigner(bytes32 _mrSigner, bool _trusted) external onlyOwner {

88          function removeRevokedCertSerialNum(
89              uint256 index,
90              bytes[] calldata serialNumBatch
91          )
92              external
93              onlyOwner
94          {

122         function toggleLocalReportCheck() external onlyOwner {

114         function configureQeIdentityJson(EnclaveIdStruct.EnclaveId calldata qeIdentityInput)
115             external
116             onlyOwner
117         {

103         function configureTcbInfoJson(
104             string calldata fmspc,
105             TCBInfoStruct.TCBInfo calldata tcbInfoInput
106         )
107             public
108             onlyOwner
109         {

```

https://github.com/llrr586570/Good/tree/main/automata-attestation/AutomataDcapV3Attestation.sol#L103:112

```solidity
File: contracts/common/AddressManager.sol


38          function setAddress(
39              uint64 _chainId,
40              bytes32 _name,
41              address _newAddress
42          )
43              external
44              virtual
45              onlyOwner
46          {

```

https://github.com/llrr586570/Good/tree/main/common/AddressManager.sol#L38:51

```solidity
File: contracts/signal/SignalService.sol


56          function authorize(address _addr, bool _authorize) external onlyOwner {

```

https://github.com/llrr586570/Good/tree/main/signal/SignalService.sol#L56:60

```solidity
File: contracts/team/TimelockTokenPool.sol


150         function void(address _recipient) external onlyOwner {

135         function grant(address _recipient, Grant memory _grant) external onlyOwner {

```

https://github.com/llrr586570/Good/tree/main/team/TimelockTokenPool.sol#L135:144

```solidity
File: contracts/tokenvault/BridgedERC20.sol


80          function setSnapshoter(address _snapshooter) external onlyOwner {

```

https://github.com/llrr586570/Good/tree/main/tokenvault/BridgedERC20.sol#L80:82

```solidity
File: contracts/tokenvault/ERC20Vault.sol


148         function changeBridgedToken(
149             CanonicalERC20 calldata _ctoken,
150             address _btokenNew
151         )
152             external
153             nonReentrant
154             whenNotPaused
155             onlyOwner
156             returns (address btokenOld_)
157         {

```

https://github.com/llrr586570/Good/tree/main/tokenvault/ERC20Vault.sol#L148:200

```solidity
File: contracts/verifiers/SgxVerifier.sol


90          function addInstances(address[] calldata _instances)
91              external
92              onlyOwner
93              returns (uint256[] memory)
94          {

```

https://github.com/llrr586570/Good/tree/main/verifiers/SgxVerifier.sol#L90:96

</details>

## L029 - Code does not follow the best practice of check-effects-interaction:

Code should follow the best-practice of [check-effects-interaction](https://blockchain-academy.hs-mittweida.de/courses/solidity-coding-beginners-to-intermediate/lessons/solidity-11-coding-patterns/topic/checks-effects-interactions/), where state variables are updated before any external calls are made. Doing so prevents a large class of reentrancy bugs.


<details>
<summary>Click to show 5 findings</summary>

```solidity
File: contracts/tokenvault/ERC1155Vault.sol


/// @audit _deployBridgedToken() called prior to this assignment
/// @audit contains nested function call IAddressManager.getAddress() 
/// @audit located in file Good/contracts/tokenvault/ERC1155Vault.sol  
312             canonicalToBridged[_ctoken.chainId][_ctoken.addr] = btoken_;


```

https://github.com/llrr586570/Good/tree/main/tokenvault/ERC1155Vault.sol#L312:312

```solidity
File: contracts/tokenvault/ERC20Vault.sol


/// @audit _deployBridgedToken() called prior to this assignment
/// @audit contains nested function call IAddressManager.getAddress() 
/// @audit located in file Good/contracts/tokenvault/ERC20Vault.sol  
423             canonicalToBridged[ctoken.chainId][ctoken.addr] = btoken;


```

https://github.com/llrr586570/Good/tree/main/tokenvault/ERC20Vault.sol#L423:423

```solidity
File: contracts/tokenvault/ERC721Vault.sol


/// @audit _deployBridgedToken() called prior to this assignment
/// @audit contains nested function call IAddressManager.getAddress() 
/// @audit located in file Good/contracts/tokenvault/ERC721Vault.sol  
248             canonicalToBridged[_ctoken.chainId][_ctoken.addr] = btoken_;


```

https://github.com/llrr586570/Good/tree/main/tokenvault/ERC721Vault.sol#L248:248

```solidity
File: contracts/verifiers/SgxVerifier.sol


/// @audit IAttestation.verifyParsedQuote() called prior to this assignment
217                 instances[nextInstanceId] = Instance(_instances[i], validSince);


/// @audit getSignedHash() called prior to this assignment
/// @audit contains nested function call ITaikoL1.getConfig() 
/// @audit located in file Good/contracts/verifiers/SgxVerifier.sol  
229             instances[id] = Instance(newInstance, uint64(block.timestamp));


```

https://github.com/llrr586570/Good/tree/main/verifiers/SgxVerifier.sol#L229:229

</details>

## L030 - Missing checks for address(0x0) when updating address state variables:

issing checks for address(0x0) when updating address state variables


<details>
<summary>Click to show 18 findings</summary>

```solidity
File: contracts/L1/libs/LibProving.sol


303                 ts_.contester = address(0);


332                     ts_.prover = address(0);


```

https://github.com/llrr586570/Good/tree/main/L1/libs/LibProving.sol#L332:332

```solidity
File: contracts/automata-attestation/utils/SigVerifyLib.sol


21              ES256VERIFIER = es256Verifier;


```

https://github.com/llrr586570/Good/tree/main/automata-attestation/utils/SigVerifyLib.sol#L21:21

```solidity
File: contracts/common/AddressResolver.sol


62              addressManager = _addressManager;


```

https://github.com/llrr586570/Good/tree/main/common/AddressResolver.sol#L62:62

```solidity
File: contracts/team/airdrop/ERC20Airdrop.sol


41              token = _token;


42              vault = _vault;


```

https://github.com/llrr586570/Good/tree/main/team/airdrop/ERC20Airdrop.sol#L42:42

```solidity
File: contracts/team/airdrop/ERC20Airdrop2.sol


69              token = _token;


70              vault = _vault;


```

https://github.com/llrr586570/Good/tree/main/team/airdrop/ERC20Airdrop2.sol#L70:70

```solidity
File: contracts/team/airdrop/ERC721Airdrop.sol


39              token = _token;


40              vault = _vault;


```

https://github.com/llrr586570/Good/tree/main/team/airdrop/ERC721Airdrop.sol#L40:40

```solidity
File: contracts/tokenvault/BridgedERC1155.sol


56              srcToken = _srcToken;


```

https://github.com/llrr586570/Good/tree/main/tokenvault/BridgedERC1155.sol#L56:56

```solidity
File: contracts/tokenvault/BridgedERC20.sol


73              srcToken = _srcToken;


81              snapshooter = _snapshooter;


```

https://github.com/llrr586570/Good/tree/main/tokenvault/BridgedERC20.sol#L81:81

```solidity
File: contracts/tokenvault/BridgedERC20Base.sol


49              migratingAddress = _migratingAddress;


```

https://github.com/llrr586570/Good/tree/main/tokenvault/BridgedERC20Base.sol#L49:49

```solidity
File: contracts/tokenvault/BridgedERC721.sol


47              srcToken = _srcToken;


```

https://github.com/llrr586570/Good/tree/main/tokenvault/BridgedERC721.sol#L47:47

```solidity
File: contracts/tokenvault/ERC1155Vault.sol


309             btoken_ = address(new ERC1967Proxy(resolve("bridged_erc1155", false), data));


```

https://github.com/llrr586570/Good/tree/main/tokenvault/ERC1155Vault.sol#L309:309

```solidity
File: contracts/tokenvault/ERC20Vault.sol


421             btoken = address(new ERC1967Proxy(resolve("bridged_erc20", false), data));


```

https://github.com/llrr586570/Good/tree/main/tokenvault/ERC20Vault.sol#L421:421

```solidity
File: contracts/tokenvault/ERC721Vault.sol


246             btoken_ = address(new ERC1967Proxy(resolve("bridged_erc721", false), data));


```

https://github.com/llrr586570/Good/tree/main/tokenvault/ERC721Vault.sol#L246:246

</details>

## L031 - The additions/multiplications may silently overflow because they're in unchecked blocks with no preceding value checks, which may lead to unexpected results.:

The additions/multiplications may silently overflow because they're in unchecked blocks with no preceding value checks, which may lead to unexpected results.


<details>
<summary>Click to show 32 findings</summary>

```solidity
File: contracts/L1/libs/LibDepositing.sol


140                     && _state.slotA.numEthDeposits - _state.slotA.nextEthDepositToProcess


141                         < _config.ethDepositRingBufferSize - 1;


```

https://github.com/llrr586570/Good/tree/main/L1/libs/LibDepositing.sol#L141:141

```solidity
File: contracts/L1/libs/LibProposing.sol


122                     l1Hash: blockhash(block.number - 1),


131                     l1Height: uint64(block.number - 1),


```

https://github.com/llrr586570/Good/tree/main/L1/libs/LibProposing.sol#L131:131

```solidity
File: contracts/L1/libs/LibProving.sol


382                     _tko.transfer(msg.sender, reward - _tier.validityBond);


384                     _tko.transferFrom(msg.sender, address(this), _tier.validityBond - reward);


```

https://github.com/llrr586570/Good/tree/main/L1/libs/LibProving.sol#L384:384

```solidity
File: contracts/L1/libs/LibVerifying.sol


152                             uint256(ITierProvider(tierProvider).getTier(ts.tier).cooldownWindow) * 60
153                                 + uint256(ts.timestamp).max(_state.slotB.lastUnpausedAt) > block.timestamp


178                     uint256 bondToReturn = uint256(ts.validityBond) + blk.livenessBond;


213                     uint64 lastVerifiedBlockId = b.lastVerifiedBlockId + numBlocksVerified;


```

https://github.com/llrr586570/Good/tree/main/L1/libs/LibVerifying.sol#L213:213

```solidity
File: contracts/L1/provers/Guardians.sol


116                 _approvals[version][_hash] |= 1 << (id - 1);


```

https://github.com/llrr586570/Good/tree/main/L1/provers/Guardians.sol#L116:116

```solidity
File: contracts/L2/TaikoL2.sol


127                 parentId = block.number - 1;


234                 for (uint256 i; i < 255 && _blockId >= i + 1; ++i) {


235                     uint256 j = _blockId - i - 1;


```

https://github.com/llrr586570/Good/tree/main/L2/TaikoL2.sol#L235:235

```solidity
File: contracts/thirdparty/optimism/Bytes.sol


25                  require(_length + 31 >= _length, "slice_overflow");


26                  require(_start + _length >= _start, "slice_overflow");


27                  require(_bytes.length >= _start + _length, "slice_outOfBounds");


```

https://github.com/llrr586570/Good/tree/main/thirdparty/optimism/Bytes.sol#L27:27

```solidity
File: contracts/thirdparty/solmate/LibFixedPointMath.sol


33                  x = (x << 78) / 5 ** 18;


39                  int256 k = ((x << 96) / 54_916_777_467_707_473_351_141_471_128 + 2 ** 95) >> 96;


40                  x = x - k * 54_916_777_467_707_473_351_141_471_128;


45                  int256 y = x + 1_346_386_616_545_796_478_920_950_773_328;


46                  y = ((y * x) >> 96) + 57_155_421_227_552_351_082_224_309_758_442;


47                  int256 p = y + x - 94_201_549_194_550_492_254_356_042_504_812;


48                  p = ((p * y) >> 96) + 28_719_021_644_029_726_153_956_944_680_412_240;


49                  p = p * x + (4_385_272_521_454_847_904_659_076_985_693_276 << 96);


53                  int256 q = x - 2_855_989_394_907_223_263_936_484_059_900;


54                  q = ((q * x) >> 96) + 50_020_603_652_535_783_019_961_831_881_945;


55                  q = ((q * x) >> 96) - 533_845_033_583_426_703_283_633_433_725_380;


56                  q = ((q * x) >> 96) + 3_604_857_256_930_695_427_073_651_918_091_429;


57                  q = ((q * x) >> 96) - 14_423_608_567_350_463_180_887_372_962_807_573;


58                  q = ((q * x) >> 96) + 26_449_188_498_355_588_339_934_803_723_976_023;


77                      (uint256(r) * 3_822_833_074_963_236_453_042_738_258_902_158_003_155_416_615_667)


78                          >> uint256(195 - k)


```

https://github.com/llrr586570/Good/tree/main/thirdparty/solmate/LibFixedPointMath.sol#L78:78

</details>

## L032 - The setter does not set a state variable or call a fuction:




```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol


65          function setMrSigner(bytes32 _mrSigner, bool _trusted) external onlyOwner {
66              _trustedUserMrSigner[_mrSigner] = _trusted;
67          }


69          function setMrEnclave(bytes32 _mrEnclave, bool _trusted) external onlyOwner {
70              _trustedUserMrEnclave[_mrEnclave] = _trusted;
71          }


```

https://github.com/llrr586570/Good/tree/main/automata-attestation/AutomataDcapV3Attestation.sol#L69:71

## L033 - Unbounded state array which is iterated upon:

Iterating over an unbounded state array in Solidity can result in excessive gas consumption, especially if the array size exceeds the block gas limit. This issue commonly arises in tasks like token distribution. To address this, it is recommended to limit array sizes for iteration, consider alternative data structures like linked lists, adopt paginated processing for smaller batches over multiple transactions, or use a 'state array' with a separate index-tracking array to manage large datasets and avoid gas-related problems.


<details>
<summary>Click to show 24 findings</summary>

```solidity
File: contracts/L1/provers/Guardians.sol


75                  delete guardianIds[guardians[i]];


75                  delete guardianIds[guardians[i]];


84                  if (guardianIds[guardian] != 0) revert INVALID_GUARDIAN_SET();


88                  guardianIds[guardian] = guardians.length;


```

https://github.com/llrr586570/Good/tree/main/L1/provers/Guardians.sol#L88:88

```solidity
File: contracts/automata-attestation/AutomataDcapV3Attestation.sol


81                  if (_serialNumIsRevoked[index][serialNumBatch[i]]) {


81                  if (_serialNumIsRevoked[index][serialNumBatch[i]]) {


84                  _serialNumIsRevoked[index][serialNumBatch[i]] = true;


84                  _serialNumIsRevoked[index][serialNumBatch[i]] = true;


96                  if (!_serialNumIsRevoked[index][serialNumBatch[i]]) {


96                  if (!_serialNumIsRevoked[index][serialNumBatch[i]]) {


99                  delete _serialNumIsRevoked[index][serialNumBatch[i]];


99                  delete _serialNumIsRevoked[index][serialNumBatch[i]];


268                         certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.ROOT)][certs[i]
269                             .serialNumber];


268                         certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.ROOT)][certs[i]


271                         certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.PCK)][certs[i]
272                             .serialNumber];


271                         certRevoked = _serialNumIsRevoked[uint256(IPEMCertChainLib.CRL.PCK)][certs[i]


```

https://github.com/llrr586570/Good/tree/main/automata-attestation/AutomataDcapV3Attestation.sol#L271:271

```solidity
File: contracts/automata-attestation/utils/BytesUtils.sol


336                 decoded = uint8(BASE32_HEX_TABLE[uint256(uint8(char)) - 0x30]);


```

https://github.com/llrr586570/Good/tree/main/automata-attestation/utils/BytesUtils.sol#L336:336

```solidity
File: contracts/bridge/Bridge.sol


92                  proofReceipt[msgHash].receivedAt = _timestamp;


```

https://github.com/llrr586570/Good/tree/main/bridge/Bridge.sol#L92:92

```solidity
File: contracts/verifiers/SgxVerifier.sol


107                 if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();


109                 emit InstanceDeleted(idx, instances[idx].addr);


111                 delete instances[idx];


211                 if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();


213                 addressRegistered[_instances[i]] = true;


217                 instances[nextInstanceId] = Instance(_instances[i], validSince);


```

https://github.com/llrr586570/Good/tree/main/verifiers/SgxVerifier.sol#L217:217

</details>

## L034 - Prefer continue over revert model in iteration:

Preferably, it's better to skip operations on array indices when a condition is not met instead of reverting the entire transaction. Reverting could be exploited by malicious actors who might intentionally introduce array objects failing conditional checks, disrupting group operations. It's advisable to skip array indices rather than revert, unless there are valid security or logic reasons for doing otherwise


<details>
<summary>Click to show 8 findings</summary>

```solidity
File: contracts/L1/libs/LibProposing.sol


244                 for (uint256 i; i < params.hookCalls.length; ++i) {
245                     if (uint160(prevHook) >= uint160(params.hookCalls[i].hook)) {
246                         revert L1_INVALID_HOOK();
247                     }
248     
249                     // When a hook is called, all ether in this contract will be send to the hook.
250                     // If the ether sent to the hook is not used entirely, the hook shall send the Ether
251                     // back to this contract for the next hook to use.
252                     // Proposers shall choose use extra hooks wisely.
253                     IHook(params.hookCalls[i].hook).onBlockProposed{ value: address(this).balance }(
254                         blk, meta_, params.hookCalls[i].data
255                     );
256     
257                     prevHook = params.hookCalls[i].hook;
258                 }


```

https://github.com/llrr586570/Good/tree/main/L1/libs/LibProposing.sol#L244:258

```solidity
File: contracts/L1/provers/Guardians.sol


80              for (uint256 i = 0; i < _newGuardians.length; ++i) {
81                  address guardian = _newGuardians[i];
82                  if (guardian == address(0)) revert INVALID_GUARDIAN();
83                  // This makes sure there are not duplicate addresses
84                  if (guardianIds[guardian] != 0) revert INVALID_GUARDIAN_SET();
85      
86                  // Save and index the guardian
87                  guardians.push(guardian);
88                  guardianIds[guardian] = guardians.length;
89              }


```

https://github.com/llrr586570/Good/tree/main/L1/provers/Guardians.sol#L80:89

```solidity
File: contracts/signal/SignalService.sol


104             for (uint256 i; i < hopProofs.length; ++i) {
105                 hop = hopProofs[i];
106     
107                 bytes32 signalRoot = _verifyHopProof(chainId, app, signal, value, hop, signalService);
108                 bool isLastHop = i == hopProofs.length - 1;
109     
110                 if (isLastHop) {
111                     if (hop.chainId != block.chainid) revert SS_INVALID_LAST_HOP_CHAINID();
112                     signalService = address(this);
113                 } else {
114                     if (hop.chainId == 0 || hop.chainId == block.chainid) {
115                         revert SS_INVALID_MID_HOP_CHAINID();
116                     }
117                     signalService = resolve(hop.chainId, "signal_service", false);
118                 }
119     
120                 bool isFullProof = hop.accountProof.length > 0;
121     
122                 _cacheChainData(hop, chainId, hop.blockId, signalRoot, isFullProof, isLastHop);
123     
124                 bytes32 kind = isFullProof ? LibSignals.STATE_ROOT : LibSignals.SIGNAL_ROOT;
125                 signal = signalForChainData(chainId, kind, hop.blockId);
126                 value = hop.rootHash;
127                 chainId = hop.chainId;
128                 app = signalService;
129             }


```

https://github.com/llrr586570/Good/tree/main/signal/SignalService.sol#L104:129

```solidity
File: contracts/thirdparty/optimism/trie/MerkleTrie.sol


85              for (uint256 i = 0; i < proof.length; i++) {
86                  TrieNode memory currentNode = proof[i];
87      
88                  // Key index should never exceed total key length or we'll be out of bounds.
89                  require(currentKeyIndex <= key.length, "MerkleTrie: key index exceeds total key length");
90      
91                  if (currentKeyIndex == 0) {
92                      // First proof element is always the root node.
93                      require(
94                          Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
95                          "MerkleTrie: invalid root hash"
96                      );
97                  } else if (currentNode.encoded.length >= 32) {
98                      // Nodes 32 bytes or larger are hashed inside branch nodes.
99                      require(
100                         Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
101                         "MerkleTrie: invalid large internal hash"
102                     );
103                 } else {
104                     // Nodes smaller than 32 bytes aren't hashed.
105                     require(
106                         Bytes.equal(currentNode.encoded, currentNodeID),
107                         "MerkleTrie: invalid internal node hash"
108                     );
109                 }
110     
111                 if (currentNode.decoded.length == BRANCH_NODE_LENGTH) {
112                     if (currentKeyIndex == key.length) {
113                         // Value is the last element of the decoded list (for branch nodes). There's
114                         // some ambiguity in the Merkle trie specification because bytes(0) is a
115                         // valid value to place into the trie, but for branch nodes bytes(0) can exist
116                         // even when the value wasn't explicitly placed there. Geth treats a value of
117                         // bytes(0) as "key does not exist" and so we do the same.
118                         value_ = RLPReader.readBytes(currentNode.decoded[TREE_RADIX]);
119                         require(
120                             value_.length > 0,
121                             "MerkleTrie: value length must be greater than zero (branch)"
122                         );
123     
124                         // Extra proof elements are not allowed.
125                         require(
126                             i == proof.length - 1,
127                             "MerkleTrie: value node must be last node in proof (branch)"
128                         );
129     
130                         return value_;
131                     } else {
132                         // We're not at the end of the key yet.
133                         // Figure out what the next node ID should be and continue.
134                         uint8 branchKey = uint8(key[currentKeyIndex]);
135                         RLPReader.RLPItem memory nextNode = currentNode.decoded[branchKey];
136                         currentNodeID = _getNodeID(nextNode);
137                         currentKeyIndex += 1;
138                     }
139                 } else if (currentNode.decoded.length == LEAF_OR_EXTENSION_NODE_LENGTH) {
140                     bytes memory path = _getNodePath(currentNode);
141                     uint8 prefix = uint8(path[0]);
142                     uint8 offset = 2 - (prefix % 2);
143                     bytes memory pathRemainder = Bytes.slice(path, offset);
144                     bytes memory keyRemainder = Bytes.slice(key, currentKeyIndex);
145                     uint256 sharedNibbleLength = _getSharedNibbleLength(pathRemainder, keyRemainder);
146     
147                     // Whether this is a leaf node or an extension node, the path remainder MUST be a
148                     // prefix of the key remainder (or be equal to the key remainder) or the proof is
149                     // considered invalid.
150                     require(
151                         pathRemainder.length == sharedNibbleLength,
152                         "MerkleTrie: path remainder must share all nibbles with key"
153                     );
154     
155                     if (prefix == PREFIX_LEAF_EVEN || prefix == PREFIX_LEAF_ODD) {
156                         // Prefix of 2 or 3 means this is a leaf node. For the leaf node to be valid,
157                         // the key remainder must be exactly equal to the path remainder. We already
158                         // did the necessary byte comparison, so it's more efficient here to check that
159                         // the key remainder length equals the shared nibble length, which implies
160                         // equality with the path remainder (since we already did the same check with
161                         // the path remainder and the shared nibble length).
162                         require(
163                             keyRemainder.length == sharedNibbleLength,
164                             "MerkleTrie: key remainder must be identical to path remainder"
165                         );
166     
167                         // Our Merkle Trie is designed specifically for the purposes of the Ethereum
168                         // state trie. Empty values are not allowed in the state trie, so we can safely
169                         // say that if the value is empty, the key should not exist and the proof is
170                         // invalid.
171                         value_ = RLPReader.readBytes(currentNode.decoded[1]);
172                         require(
173                             value_.length > 0,
174                             "MerkleTrie: value length must be greater than zero (leaf)"
175                         );
176     
177                         // Extra proof elements are not allowed.
178                         require(
179                             i == proof.length - 1,
180                             "MerkleTrie: value node must be last node in proof (leaf)"
181                         );
182     
183                         return value_;
184                     } else if (prefix == PREFIX_EXTENSION_EVEN || prefix == PREFIX_EXTENSION_ODD) {
185                         // Prefix of 0 or 1 means this is an extension node. We move onto the next node
186                         // in the proof and increment the key index by the length of the path remainder
187                         // which is equal to the shared nibble length.
188                         currentNodeID = _getNodeID(currentNode.decoded[1]);
189                         currentKeyIndex += sharedNibbleLength;
190                     } else {
191                         revert("MerkleTrie: received a node with an unknown prefix");
192                     }
193                 } else {
194                     revert("MerkleTrie: received an unparseable node");
195                 }
196             }


```

https://github.com/llrr586570/Good/tree/main/thirdparty/optimism/trie/MerkleTrie.sol#L85:196

```solidity
File: contracts/tokenvault/ERC1155Vault.sol


47              for (uint256 i; i < _op.amounts.length; ++i) {
48                  if (_op.amounts[i] == 0) revert VAULT_INVALID_AMOUNT();
49              }


```

https://github.com/llrr586570/Good/tree/main/tokenvault/ERC1155Vault.sol#L47:49

```solidity
File: contracts/tokenvault/ERC721Vault.sol


34              for (uint256 i; i < _op.tokenIds.length; ++i) {
35                  if (_op.amounts[i] != 0) revert VAULT_INVALID_AMOUNT();
36              }


```

https://github.com/llrr586570/Good/tree/main/tokenvault/ERC721Vault.sol#L34:36

```solidity
File: contracts/verifiers/SgxVerifier.sol


104             for (uint256 i; i < _ids.length; ++i) {
105                 uint256 idx = _ids[i];
106     
107                 if (instances[idx].addr == address(0)) revert SGX_INVALID_INSTANCE();
108     
109                 emit InstanceDeleted(idx, instances[idx].addr);
110     
111                 delete instances[idx];
112             }


210             for (uint256 i; i < _instances.length; ++i) {
211                 if (addressRegistered[_instances[i]]) revert SGX_ALREADY_ATTESTED();
212     
213                 addressRegistered[_instances[i]] = true;
214     
215                 if (_instances[i] == address(0)) revert SGX_INVALID_INSTANCE();
216     
217                 instances[nextInstanceId] = Instance(_instances[i], validSince);
218                 ids[i] = nextInstanceId;
219     
220                 emit InstanceAdded(nextInstanceId, _instances[i], address(0), validSince);
221     
222                 nextInstanceId++;
223             }


```

https://github.com/llrr586570/Good/tree/main/verifiers/SgxVerifier.sol#L210:223

</details>

## L035 -  Subtraction may underflow if multiplication is too large:




```solidity
File: contracts/thirdparty/solmate/LibFixedPointMath.sol


40                  x = x - k * 54_916_777_467_707_473_351_141_471_128;


```
