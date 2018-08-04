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



