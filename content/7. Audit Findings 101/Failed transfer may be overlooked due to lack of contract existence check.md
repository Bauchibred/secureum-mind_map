
# 54 - [Failed transfer may be overlooked due to lack of contract existence check](./Failed%20transfer%20may%20be%20overlooked%20due%20to%20lack%20of%20contract%20existence%20check.md)

Failed transfer may be overlooked due to lack of contract existence check Because the pool fails to check that a contract exists, the pool may assume that failed transactions involving destructed tokens are successful. `TransferHelper.safeTransfer` performs a transfer with a low-level call without confirming the contract’s existence. As a result, if the tokens have not yet been deployed or have been destroyed, safeTransfer will return success even though no transfer was executed.


1.  Recommendation: Short term, check the contract’s existence prior to the low-level call in _TransferHelper.safeTransfer_. Long term, avoid low-level calls.
2.  High Risk severity finding from [ToB’s Audit of Uniswap V3](https://github.com/Uniswap/uniswap-v3-core/blob/main/audits/tob/audit.pdf)


___
## Slide Screenshot
![054.png](../../images/7.%20Audit%20Findings%20101/054.png)
___
## Slide Text
- 
___
## References
- Youtube Reference
___
## Tags