    type Block struct {
        Block_Header
        Proof     [32]byte      `json:"-"` // Reserved for future
        Tips      []crypto.Hash `json:"tips"` // belongs_to_many，可关联多个父块
        Tx_hashes []crypto.Hash `json:"tx_hashes"` // has_many，有多笔交易
    }

```
// we process incoming blocks in this format
type Complete_Block struct {
    Bl  *Block
    Txs []*transaction.Transaction
}
```



