# Taiko deps check

 @openzeppelin version **4.8.2**

https://github.com/code-423n4/2024-03-taiko/blob/d6d2be3ab0f42b0d997cf6c01117c65f046253a8/packages/protocol/package.json#L38

It has a vulns for this version

https://security.snyk.io/package/npm/@openzeppelin%2Fcontracts

Can be actual for current project

* Low
    * https://security.snyk.io/vuln/SNYK-JS-OPENZEPPELINCONTRACTS-5425827
    * https://security.snyk.io/vuln/SNYK-JS-OPENZEPPELINCONTRACTS-5672116

* Medium
    * https://security.snyk.io/vuln/SNYK-JS-OPENZEPPELINCONTRACTS-6346765


Just update dep to secure version.

### Time spent:
1 hours