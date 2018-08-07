```
// caches x of transactions validity
// it is always atomic
// the cache is not txhash -> validity mapping
// instead it is txhash+expanded ringmembers
// if the entry exist, the tx is valid
// it stores special hash and first seen time
// this can only be used on expanded transactions
var transaction_valid_cache sync.Map
```

#### Verify\_Transaction\_Coinbase

Coinbase 交易校验

由于产生机制简单，校验也比较简单。

```
/* Coinbase transactions need to verify the amount of coins
```

#### Verify\_Transaction\_NonCoinbase

非 Coinbase 交易校验

元数据

Vin 输入数据

Vout 输出数据

RctSignature 签名数据

有简单的方式，通过观察即可验证；也有复杂的方式，需要通过计算才能验证。两种方式均通过验证，才是真正的、有效的“交易”。

```
// all non miner tx must be non-coinbase tx
// each check is placed in a separate  block of code, to avoid ambigous code or faulty checks
// all check are placed and not within individual functions ( so as we cannot skip a check )
// This function verifies tx fully, means all checks,
// if the transaction has passed the check it can be added to mempool, relayed or added to blockchain
// the transaction has already been deserialized thats it
```

#### Verify\_Transaction\_NonCoinbase\_DoubleSpend\_Check

双花校验

主要是利用 KeyImage，比较简单。

```
// double spend check is separate from the core checks ( due to softforks )
```

Verify\_Block\_DoubleSpending

```
// verify all non coinbase tx, single threaded for double spending on current active chain
```



