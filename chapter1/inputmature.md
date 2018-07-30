```
//this file implements the logic to detect whether an input is mature or still locked
//This function is crucial as any bugs can have catastrophic effects
//this function is used both by the core blockchain and wallet
//TODO we need to check the edge cases
```

根据 current\_chain\_height、input\_block\_height、locked\_to\_height、sigtype，软件配置（挖矿交易锁定 60 个区块，普通交易锁定 11 个区块）及当前时间进行判断。



