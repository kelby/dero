Key2Key

使用 sha256 加密。

```
// all keys are derived as follows ( entirely deterministic )
// ( key is derived from master secret and user supplied key)
// it's only 1 way
// all keys and bucket names are stored using this , except the metadata bucket
// all values are stored using salsa20 aead
// since all keys are dependent on the master password, almost 99.99% analsis are rendered useless
```



