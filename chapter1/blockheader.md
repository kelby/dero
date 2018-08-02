    type Block_Header struct {
        Major_Version uint64                  `json:"major_version"`
        Minor_Version uint64                  `json:"minor_version"`
        Timestamp     uint64                  `json:"timestamp"`
        Nonce         uint32                  `json:"nonce"` // TODO make nonce 32 byte array for infinite work capacity
        ExtraNonce    [32]byte                `json:"-"`
        Miner_TX      transaction.Transaction `json:"miner_tx"` // has_one
    }

Major\_Version 和 Minor\_Version 为版本信息；

Timestamp 为时间戳；

Nonce 参与 PoW 运算的随机数；

ExtraNonce 如 Nonce 不够用，可使用此字段；

Miner\_TX 即 Coinbase，由挖矿产生

