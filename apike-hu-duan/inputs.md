```
// used by miner
type Txin_gen struct {
    Height uint64 // stored as varint
}
```

当前还不支持 Txin\_to\_script

```
type Txin_to_script struct {
    Prev    [32]byte
    Prevout uint64
    Sigset  []byte
}
```

当前还不支持 Txin\_to\_scripthash

```
type Txin_to_scripthash struct {
    Prev    [32]byte
    Prevout uint64
    Script  Txout_to_script
    Sigset  []byte
}
```

    type Txin_to_key struct {
        Amount      uint64
        Key_offsets []uint64 // this is encoded as a varint for length and then all offsets are stored as varint
        //crypto::key_image k_image;      // double spending protection
        K_image crypto.Hash `json:"k_image"` // key image
    }

```
type Txin_v interface{} // it can only be txin_gen, txin_to_script, txin_to_scripthash, txin_to_key
```



