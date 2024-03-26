###  Report 1:
#### Invalid Condition Validation
The code provided from the AutomataDcapV3Attestation contract shows how Tcb Levels are checked, as corrected in the cool the boolean of `pceSvn Is Higher Or Greater` should only return true when it is indeed greater than, however due to wrong implementation by the protocol it would return true when the two values are equal when it should only return true when it is greater than or higher.
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L216
```solidity
 function _checkTcbLevels(
        IPEMCertChainLib.PCKCertificateField memory pck,
        TCBInfoStruct.TCBInfo memory tcb
    )
        private
        pure
        returns (bool, TCBInfoStruct.TCBStatus status)
    {
        for (uint256 i; i < tcb.tcbLevels.length; ++i) {
            TCBInfoStruct.TCBLevelObj memory current = tcb.tcbLevels[i];
 ---           bool pceSvnIsHigherOrGreater = pck.sgxExtension.pcesvn >= current.pcesvn;
 +++           bool pceSvnIsHigherOrGreater = pck.sgxExtension.pcesvn > current.pcesvn;

            bool cpuSvnsAreHigherOrGreater = _isCpuSvnHigherOrGreater(
                pck.sgxExtension.sgxTcbCompSvnArr, current.sgxTcbCompSvnArr
            );
            if (pceSvnIsHigherOrGreater && cpuSvnsAreHigherOrGreater) {
                status = current.status;
                bool tcbIsRevoked = status == TCBInfoStruct.TCBStatus.TCB_REVOKED;
                return (!tcbIsRevoked, status);
            }
        }
        return (true, TCBInfoStruct.TCBStatus.TCB_UNRECOGNIZED);
    }
```
note: similar correction should be done at [L241](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L241) of same contract
###  Report 2:
#### Denial of Service from Excess Gas usage by a Single function
The code below from the AutomataDcapV3Attestation contract shows how _verifyParsedQuote(...) function is implemented, as noted from the comment descriptions, it shows the gas usage at each step in the function, accumulation of this gas usages opens up the risk of reaching gas limit due to excess gas usaged with would cause denial of Service, Protocol should consider a kind of Division of labour to reduce Gas usage.
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/automata-attestation/AutomataDcapV3Attestation.sol#L364
```solidity
function _verifyParsedQuote(V3Struct.ParsedV3QuoteStruct memory v3quote)
        internal
        view
        returns (bool, bytes memory)
    {
        bytes memory retData = abi.encodePacked(INVALID_EXIT_CODE);

        // // Step 1: Parse the quote input = 152k gas
        (
            ...
        }

        // Step 2: Verify application enclave report MRENCLAVE and MRSIGNER
        {
            if (_checkLocalEnclaveReport) {
                // 4k gas
                ...
        }

        // Step 3: Verify enclave identity = 43k gas
        EnclaveIdStruct.EnclaveIdStatus qeTcbStatus;
        {
            ...
        }

        // Step 4: Parse Quote CertChain
        IPEMCertChainLib.ECSha256Certificate[] memory parsedQuoteCerts;
        TCBInfoStruct.TCBInfo memory fetchedTcbInfo;
        {
            // 536k gas
           ...
        }

        // Step 5: basic PCK and TCB check = 381k gas
        {
           ...
            }
        }

        // Step 6: Verify TCB Level
        TCBInfoStruct.TCBStatus tcbStatus;
        {
            // 4k gas
           ...
            }
        }

        // Step 7: Verify cert chain for PCK
        {
            // 660k gas (rootCA pubkey is trusted)
           ...
        }

        // Step 8: Verify the local attestation sig and qe report sig = 670k gas
        ...

        retData = abi.encodePacked(sha256(abi.encode(v3quote)), tcbStatus);

        return (_attestationTcbIsValid(tcbStatus), retData);
    }
```
### Report 3:
#### Typographical Error
As corrected in the code below in the Bridge contract, it should be delays not deleys
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L443
```solidity
   function getInvocationDelays()
        public
        view
        virtual
        returns (uint256 invocationDelay_, uint256 invocationExtraDelay_)
    {
        if (
            block.chainid == 1 // Ethereum mainnet
        ) {
            // For Taiko mainnet
            // 384 seconds = 6.4 minutes = one ethereum epoch
            return (1 hours, 384 seconds);
        } else if (
           ...
        ) {
           ...
        } else if (block.chainid >= 32_300 && block.chainid <= 32_400) {
            ...
        } else {
 ---           // This is a Taiko L2 chain where no deleys are applied.
 +++           // This is a Taiko L2 chain where no delays are applied.
            return (0, 0);
        }
    }
```
###  Report 4:
#### Wrong Comment Description
As can be noted from the code description below, the comment description is met for proveMessageFailed(...) function at [L348](https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L348) and not proveMessageReceived(...) function as provided below, this description is contradictory to implementation and should be corrected by Protocol
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/contracts/bridge/Bridge.sol#L370-L373
```solidity
>>>   /// @notice Checks if a msgHash has failed on its destination chain.
>>>    /// @param _message The message.
>>>    /// @param _proof The merkle inclusion proof.
>>>    /// @return true if the message has failed, false otherwise.
    function proveMessageReceived(
        Message calldata _message,
        bytes calldata _proof
    )
        public
        view
        returns (bool)
    {
        if (_message.destChainId != block.chainid) return false;
        return _proveSignalReceived(
            resolve("signal_service", false), hashMessage(_message), _message.srcChainId, _proof
        );
    }
```