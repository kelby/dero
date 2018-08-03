```
type Index_Data struct {
    InKey     ringct.CtKey
    ECDHTuple ringct.ECdhTuple // encrypted Amounts
    // Key crypto.Hash  // stealth address key
    // Commitment crypto.Hash // commitment public key
    Height        uint64 // height to which this belongs
    Unlock_Height uint64 // height at which it will unlock
}
```

Read\_output\_index

```
// this will read the output index data but will not deserialize it
// this is exposed for rpcserver giving access to wallet
```

Find\_TX\_Output\_Index

```
// this function finds output index for the tx
// first find a block index , and get the start offset
// then loop the index till you find the key in the result
// if something is not right, we return 0
```



