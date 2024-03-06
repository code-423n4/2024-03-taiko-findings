## Splitting Require Statements
It is advisable to reduce the require statements to save gas

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L77-L81

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L82-L86

https://github.com//code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/QuoteV3Auth/V3Parser.sol#L94-L99

## Constructor can be defined payable to save gas
https://github.com//code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/utils/SigVerifyLib.sol#L20-L22

https://github.com//code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L54-L58


## Use bytes32 in place of string to save gas
https://github.com//code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/lib/PEMCertChainLib.sol#L17-L29

## 2**95 can be replaced by type(uint95).max; or type(uint95).min; to save some gas

https://github.com//code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/thirdparty/solmate/LibFixedPointMath.sol#L39-L39


## Function shall be external to save gas
https://github.com//code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/L1/TaikoToken.sol#L52-L54
https://github.com//code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/common/EssentialContract.sol#L69-L75
https://github.com//code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/signal/SignalService.sol#L83-L134
https://github.com//code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L103-L112

## Splitting the multiple if statements in the code base

https://github.com//code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/libs/Lib4844.sol#L57-L59
