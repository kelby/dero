    type Block_Header struct {
    	Major_Version uint64                  `json:"major_version"`
    	Minor_Version uint64                  `json:"minor_version"`
    	Timestamp     uint64                  `json:"timestamp"`
    	Nonce         uint32                  `json:"nonce"` // TODO make nonce 32 byte array for infinite work capacity
    	ExtraNonce    [32]byte                `json:"-"`
    	Miner_TX      transaction.Transaction `json:"miner_tx"`
    }



