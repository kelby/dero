#### Transaction

GetHash

由 3 部分组合而成：prefix, rctBase and rctPrunable

```
        // version 2 requires first computing 3 separate hashes
        // prefix, rctBase and rctPrunable
        // and then hashing the hashes together to get the final hash
```

GetPrefixHash

IsCoinbase

```
// returns whether the tx is coinbase
```

DeserializeHeader

Clear

```
// calculated prefi has signature
```

SerializeHeader

Serialize



