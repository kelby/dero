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

GetHash

```
// see spec here https://cryptonote.org/cns/cns003.txt
// this function gets the block identifier hash
// this has been simplified and varint length has been removed
```

GetBlockWork

输入为 Block\_Header（除 Miner\_TX 外）数据。

结果固定为 76 个字节，即长度为 146 的字符串。

```
// converts a block, into a getwork style work, ready for either submitting the block
// or doing Pow Calculations
```

getserializedheaderforwork

```
// serialize block header for calculating PoW
```

Miner\_TX.Serialize

```
// write miner tx
```

GetTipsHash

```
// get block transactions tree hash

// write tips,, merkle tree should be replaced with something faster
```

GetTXSHash

```
// hash of all transactions

// get block transactions
// we have discarded the merkle tree and have shifted to a plain version
```

GetPoWHash

针对在 GetBlockWork 的结果进行。

```
// Get PoW hash , this is very slow function
```

设置 Proof 功能尚未实现，即还不能直接运用此软件进行挖矿。

> 引入 DAG 后，把原来单一的父块 hash 变成了可有多个父块 hash.



