
### Unnecessary Assert
Unnecessary `assert` statements in Solidity contracts can have several detrimental impacts on code readability, gas efficiency, and overall contract functionality. `assert` statements are typically used to check for conditions that should never occur under normal circumstances. While they can be valuable for catching unexpected errors and halting contract execution, their misuse can lead to unnecessary complexity and increased gas costs.


```solidity
Path: ./packages/protocol/contracts/L1/libs/LibProving.sol

223:                assert(tier.validityBond == 0);	// @audit-issue

224:                assert(ts.validityBond == 0 && ts.contestBond == 0 && ts.contester == address(0));	// @audit-issue
```
[223](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/L1/libs/LibProving.sol#L223-L223), [224](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/L1/libs/LibProving.sol#L224-L224), 


```solidity
Path: ./packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

138:        assert(success); // never reverts, always returns 0 or 1	// @audit-issue
```
[138](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L138-L138), 


```solidity
Path: ./packages/protocol/contracts/bridge/Bridge.sol

486:        assert(_message.from != address(this));	// @audit-issue
```
[486](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/bridge/Bridge.sol#L486-L486), 


#### Recommendation

Use 'assert' statements in Solidity judiciously, reserving them for conditions that indicate critical and unforeseen errors. Avoid overuse to maintain code clarity and prevent unnecessary gas consumption due to these costly checks.




### Cache State Variable Array Length In For Loop
Failing to cache the array length when iterating through arrays in Solidity can have significant performance and gas cost implications. In Solidity, array lengths can change during execution due to external calls or storage modifications. When the array length is not cached before entering a loop, it is recomputed with each iteration, leading to unnecessary gas consumption and potentially making the contract vulnerable to reentrancy attacks.        


```solidity
Path: ./packages/protocol/contracts/L1/provers/Guardians.sol

74:        for (uint256 i; i < guardians.length; ++i) {	// @audit-issue
```
[74](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/L1/provers/Guardians.sol#L74-L74), 


#### Recommendation

To enhance performance and reduce gas costs, cache the array length before entering a for loop in Solidity. This approach prevents repeated computation of the array length and mitigates the risk of reentrancy attacks due to array length changes during loop execution.


### Unnecessary Assignment
The identified issue involves an unnecessary step of assigning a condition's result to a boolean variable before using it in an if-statement. This extra variable assignment is not required as the condition can be directly evaluated within the if-statement itself, making the code more concise and efficient.


```solidity
Path: ./packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

318:        bool qeReportDataIsValid = expectedAuthDataHash == computedAuthDataHash;	// @audit-issue: This assignment is not needed. Binary operation can be used in condition directly.
319:        if (qeReportDataIsValid) {
```
[318](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L318-L319), 


#### Recommendation

Review your Solidity code for instances where boolean variables are unnecessarily assigned from conditions only to be used in immediate if-statements. Simplify these constructs by directly placing the conditional expression within the if-statement, eliminating the intermediary boolean variable. This practice not only streamlines your code, making it more concise, but also potentially reduces gas costs by minimizing the operations performed. Refactoring in this manner can enhance the readability and efficiency of your smart contracts. Always ensure that such optimizations maintain the original logic and intent of the code.


### Revert String Size Optimization
Shortening the revert strings to fit within 32 bytes will decrease deployment time and decrease runtime Gas when the revert condition is met.

Revert strings that are longer than 32 bytes require at least one additional `mstore`, along with additional overhead to calculate memory offset, etc.



```solidity
Path: ./packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

87:        require(	// @audit-issue: String length is `63`
88:            v3Quote.v3AuthData.certification.certType == 5,
89:            "certType must be 5: Concatenated PCK Cert Chain (PEM formatted)"
90:        );
```
[87](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L87-L90), 


```solidity
Path: ./packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

89:            require(currentKeyIndex <= key.length, "MerkleTrie: key index exceeds total key length");	// @audit-issue: String length is `46`

99:                require(	// @audit-issue: String length is `39`
100:                    Bytes.equal(abi.encodePacked(keccak256(currentNode.encoded)), currentNodeID),
101:                    "MerkleTrie: invalid large internal hash"
102:                );

105:                require(	// @audit-issue: String length is `38`
106:                    Bytes.equal(currentNode.encoded, currentNodeID),
107:                    "MerkleTrie: invalid internal node hash"
108:                );

119:                    require(	// @audit-issue: String length is `59`
120:                        value_.length > 0,
121:                        "MerkleTrie: value length must be greater than zero (branch)"
122:                    );

125:                    require(	// @audit-issue: String length is `58`
126:                        i == proof.length - 1,
127:                        "MerkleTrie: value node must be last node in proof (branch)"
128:                    );

150:                require(	// @audit-issue: String length is `58`
151:                    pathRemainder.length == sharedNibbleLength,
152:                    "MerkleTrie: path remainder must share all nibbles with key"
153:                );

162:                    require(	// @audit-issue: String length is `61`
163:                        keyRemainder.length == sharedNibbleLength,
164:                        "MerkleTrie: key remainder must be identical to path remainder"
165:                    );

172:                    require(	// @audit-issue: String length is `57`
173:                        value_.length > 0,
174:                        "MerkleTrie: value length must be greater than zero (leaf)"
175:                    );

178:                    require(	// @audit-issue: String length is `56`
179:                        i == proof.length - 1,
180:                        "MerkleTrie: value node must be last node in proof (leaf)"
181:                    );
```
[89](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L89-L89), [99](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L99-L102), [105](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L105-L108), [119](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L119-L122), [125](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L125-L128), [150](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L150-L153), [162](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L162-L165), [172](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L172-L175), [178](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L178-L181), 


```solidity
Path: ./packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol

37:        require(	// @audit-issue: String length is `74`
38:            _in.length > 0,
39:            "RLPReader: length of an RLP item must be greater than zero to be decodable"
40:        );

56:        require(	// @audit-issue: String length is `56`
57:            itemType == RLPItemType.LIST_ITEM,
58:            "RLPReader: decoded item type for list is not a list item"
59:        );

61:        require(	// @audit-issue: String length is `50`
62:            listOffset + listLength == _in.length,
63:            "RLPReader: list item has an invalid data remainder"
64:        );

112:        require(	// @audit-issue: String length is `57`
113:            itemType == RLPItemType.DATA_ITEM,
114:            "RLPReader: decoded item type for bytes is not a data item"
115:        );

117:        require(	// @audit-issue: String length is `52`
118:            _in.length == itemOffset + itemLength,
119:            "RLPReader: bytes value contains an invalid remainder"
120:        );

152:        require(	// @audit-issue: String length is `74`
153:            _in.length > 0,
154:            "RLPReader: length of an RLP item must be greater than zero to be decodable"
155:        );

172:            require(	// @audit-issue: String length is `78`
173:                _in.length > strLen,
174:                "RLPReader: length of content must be greater than string length (short string)"
175:            );

182:            require(	// @audit-issue: String length is `77`
183:                strLen != 1 || firstByteOfContent >= 0x80,
184:                "RLPReader: invalid prefix, single byte < 0x80 are not prefixed (short string)"
185:            );

192:            require(	// @audit-issue: String length is `81`
193:                _in.length > lenOfStrLen,
194:                "RLPReader: length of content must be > than length of string length (long string)"
195:            );

202:            require(	// @audit-issue: String length is `74`
203:                firstByteOfContent != 0x00,
204:                "RLPReader: length of content must not have any leading zeros (long string)"
205:            );

212:            require(	// @audit-issue: String length is `72`
213:                strLen > 55,
214:                "RLPReader: length of content must be greater than 55 bytes (long string)"
215:            );

217:            require(	// @audit-issue: String length is `76`
218:                _in.length > lenOfStrLen + strLen,
219:                "RLPReader: length of content must be greater than total length (long string)"
220:            );

228:            require(	// @audit-issue: String length is `74`
229:                _in.length > listLen,
230:                "RLPReader: length of content must be greater than list length (short list)"
231:            );

238:            require(	// @audit-issue: String length is `77`
239:                _in.length > lenOfListLen,
240:                "RLPReader: length of content must be > than length of list length (long list)"
241:            );

248:            require(	// @audit-issue: String length is `72`
249:                firstByteOfContent != 0x00,
250:                "RLPReader: length of content must not have any leading zeros (long list)"
251:            );

258:            require(	// @audit-issue: String length is `70`
259:                listLen > 55,
260:                "RLPReader: length of content must be greater than 55 bytes (long list)"
261:            );

263:            require(	// @audit-issue: String length is `74`
264:                _in.length > lenOfListLen + listLen,
265:                "RLPReader: length of content must be greater than total length (long list)"
266:            );
```
[37](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L37-L40), [56](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L56-L59), [61](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L61-L64), [112](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L112-L115), [117](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L117-L120), [152](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L152-L155), [172](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L172-L175), [182](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L182-L185), [192](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L192-L195), [202](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L202-L205), [212](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L212-L215), [217](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L217-L220), [228](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L228-L231), [238](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L238-L241), [248](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L248-L251), [258](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L258-L261), [263](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/thirdparty/optimism/rlp/RLPReader.sol#L263-L266), 


#### Recommendation


To optimize Gas usage in your Solidity contract, it is recommended to keep revert strings as short as possible and to ensure that they fit within 32 bytes. It is possible to use abbreviations or simplified error messages to keep the string length short. Doing so can reduce the amount of Gas used during deployment and runtime when the revert condition is met.



### Unused State Variables
There are state variables which are declared but not used in any function. This might increase the contract's gas usage unnecessarily.

```solidity
Path: ./packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol

6:    uint256 constant LOW_28_MASK =	// @audit-issue
```
[6](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/thirdparty/nomad-xyz/ExcessivelySafeCall.sol#L6-L6), 


#### Recommendation

To optimize your contract's gas usage, remove any state variables that are declared but not used in any function. Unnecessary state variables can increase gas costs and should be eliminated during code review.


### Unused `error` definition
Note that there may be cases where an error superficially appears to be used, but this is only because there are multiple definitions of the error in different files. In such cases, the error definition should be moved into a separate file. The instances below are the unused definitions.


```solidity
Path: ./packages/protocol/contracts/L1/TaikoErrors.sol

36:    error L1_TOO_MANY_TIERS();	// @audit-issue
```
[36](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/L1/TaikoErrors.sol#L36-L36), 


#### Recommendation

Unused `error` definitions should be removed from the contract, and if needed, consolidated into a separate file to avoid duplication.



### State Variables Only Set in The Constructor Should Be Declared `immutable`
Avoids a Gsset(** 20000 gas**) in the constructor, and replaces the first access in each transaction(Gcoldsload - ** 2100 gas **) and each access thereafter(Gwarmacces - ** 100 gas **) with a`PUSH32`(** 3 gas **).

While`string`s are not value types, and therefore cannot be`immutable` / `constant` if not hard - coded outside of the constructor, the same behavior can be achieved by making the current contract `abstract` with `virtual` functions for the`string` accessors, and having a child contract override the functions with the hard - coded implementation - specific values.

```solidity
Path: ./packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol

52:    address public owner;	// @audit-issue
```
[52](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L52-L52), 


```solidity
Path: ./packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol

18:    address private ES256VERIFIER;	// @audit-issue
```
[18](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L18-L18), 


#### Recommendation

Consider marking state variables as an immutable that never changes on the contract.


### Automated unchecked arithmetic is generated after solidity version 0.8.22
It is not needed to add unchecked block to for loop expressions after solidity version [0.8.22](https://soliditylang.org/blog/2023/10/25/solidity-0.8.22-release-announcement/)

```solidity
Path: ./packages/protocol/contracts/L1/libs/LibDepositing.sol

103:                    ++i;	// @audit-issue
```
[103](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/L1/libs/LibDepositing.sol#L103-L103), 


```solidity
Path: ./packages/protocol/contracts/L1/provers/Guardians.sol

133:            for (uint256 i; i < guardiansLength; ++i) {	// @audit-issue
```
[133](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/L1/provers/Guardians.sol#L133-L133), 


```solidity
Path: ./packages/protocol/contracts/tokenvault/ERC1155Vault.sol

251:                for (uint256 i; i < _op.tokenIds.length; ++i) {	// @audit-issue

269:                for (uint256 i; i < _op.tokenIds.length; ++i) {	// @audit-issue
```
[251](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L251-L251), [269](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/tokenvault/ERC1155Vault.sol#L269-L269), 


```solidity
Path: ./packages/protocol/contracts/tokenvault/ERC721Vault.sol

197:                for (uint256 i; i < _op.tokenIds.length; ++i) {	// @audit-issue

210:                for (uint256 i; i < _op.tokenIds.length; ++i) {	// @audit-issue
```
[197](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/tokenvault/ERC721Vault.sol#L197-L197), [210](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/tokenvault/ERC721Vault.sol#L210-L210), 


```solidity
Path: ./packages/protocol/contracts/L2/TaikoL2.sol

234:            for (uint256 i; i < 255 && _blockId >= i + 1; ++i) {	// @audit-issue
```
[234](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/L2/TaikoL2.sol#L234-L234), 


```solidity
Path: ./packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol

211:                ++i;	// @audit-issue
```
[211](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/thirdparty/optimism/trie/MerkleTrie.sol#L211-L211), 


#### Recommendation

Do not use unchecked keyword after solidity version [0.8.22](https://soliditylang.org/blog/2023/10/25/solidity-0.8.22-release-announcement/).


### Unnecessary Variable Initialization
In programming, it's a common practice to declare and initialize variables that will be used later in the code. However, if after declaration, the variable is not used anywhere else in the code, this leads to unnecessary variable initialization. In the context of Solidity and smart contracts, where gas efficiency is paramount, such redundant initializations not only consume extra gas but also clutter the codebase, making it less readable and harder to maintain.

Variables that are declared but never used represent dead code. They take up space in the bytecode, result in wasted gas when the contract is deployed, and can be confusing for anyone reading or auditing the code.


```solidity
Path: ./packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol

276:        IPEMCertChainLib.ECSha256Certificate[] memory parsedQuoteCerts;	// @audit-issue
```
[276](https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/./packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L276-L276), 


#### Recommendation

To avoid unnecessary variable initialization in Solidity code, regularly review and remove unused variables, use meaningful variable names, and avoid overly defensive coding. Prioritize gas efficiency and rigorous testing to maintain clean and efficient code.
