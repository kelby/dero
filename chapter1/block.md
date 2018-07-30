    type Block struct {
        Block_Header
        Proof     [32]byte      `json:"-"` // Reserved for future
        Tips      []crypto.Hash `json:"tips"`
        Tx_hashes []crypto.Hash `json:"tx_hashes"`
    }

```
// we process incoming blocks in this format
type Complete_Block struct {
    Bl  *Block
    Txs []*transaction.Transaction
}
```



