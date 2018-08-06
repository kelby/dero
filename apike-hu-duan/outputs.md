```
type Txout_to_script struct {
    Keys   [][32]byte
    Script []byte
}
```

```
type Txout_to_scripthash struct {
    Hash [32]byte
}
```

```
type Txout_to_key struct {
    Key crypto.Key
}
```

```
type Tx_out struct {
    Amount uint64
    Target interface{} // txout_target_v ;, it can only be  txout_to_script, txout_to_scripthash, txout_to_key
}
```

虽然有预留位置，但当前 Tx\_out 仅支持 `txout_to_key` 这一种格式。当前 CryptoNote 系统币种，均没有脚本、智能合约相关功能。



