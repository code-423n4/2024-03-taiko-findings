# Analysis  - Taiko (A based rollup)
### Summary
| List |Head |Details|
|:--|:----------------|:------|
|a) |Overview of Taiko Protocol | overview of the key components and features Taiko RollUp |
|b) |Audit approach | Process and steps i followed |
|c) |Documents | What is the scope and quality of documentation for Users and Administrators? |
|d) |Possible Systemic Risks | The possible systemic risks based on my analysis |
|e) |Code Commentary  | Suggestions for existing code base |
|f) |Centralization risks | Concerns associated with centralized systems |
|g) |Gas Optimizations| Details about my gas optimizations findings and gas savings |
|h) |Risks as per Analysis | Possible risks |
|i) |Security Approach of the Project | Audit approach of the Project |
|k) |Non-functional aspects | General suggestions |
|l) |Time spent on analysis | The Over all time spend for this reports |


## a) Overview of Taiko Protocol


## b) Audit approach 


## Stages of audit

- ``The first stage of the audit``



- ``The second stage of the audit``

 

- ``The third stage of the audit``



- ``The fourth stage of the audit``



## c) Documents
- Documentation should be increased further, it is recommended to add the architectural design to the documents as infographic

- I would also recommend adding quality Medium articles, it's a great way to provide an in-depth look at many of the topics in the project and is used by many blockchain projects.

## d) Possible Systemic Risks

## e) Code Commentary
- Use consistant ``SPDX-License`` for all contracts 
 
- Inconsistance ``solidity versions`` used 

- Ensure that variable and function names follow ``consistent naming conventions`` for better ``readability`` and ``maintainability``. For example, use camelCase or snake_case consistently throughout the contract

-

-

-

-

-

## f) Centralization risks
A single point of failure is not acceptable for this project Centrality risk is high in the project, the role of ``onlyOwner``detailed below has very critical and important powers

Project and funds may be compromised by a malicious or stolen private key ``onlyOwner`` ``msg.sender``

## g) Gas Optimizations

## h) Risks as per Analysis

## i) Security Approach of the Project
Successful current security understanding of the project;
1- An older version of the protocol has been audited by Sigma Prime all security concerns were resolved, this is the case in both audit reports;

https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/audit/sigma_prime_taiko_smart_contract_security_assessment_report_v2_0.pdf

2- The corresponding bridge code has been audited by QuillAudits (report).
https://github.com/code-423n4/2024-03-taiko/blob/main/packages/protocol/audit/quill_audits_taiko_smart_contract_audit_report.pdf

While investigating the potential risks in the project, the past audit reports can give us serious insights, so they should be taken into account and analyzed in detail. 


What the project should add in the understanding of Security;
1- By distributing the project to testnets, ensuring that the audits are carried out in onchain audit. (This will increase coverage)
2- After the project is published on the mainnet, there should be emergency action plans (not found in the documents)

## k) Non-functional aspects

## l) Time spent on analysis







### Time spent:
50 hours

### Time spent:
50 hours