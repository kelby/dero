    // this is used to print blockheader for the rpc and the daemon
    type BlockHeader_Print struct {
    	Depth         int64  `json:"depth"`
    	Difficulty    string `json:"difficulty"`
    	Hash          string `json:"hash"`
    	Height        int64  `json:"height"`
    	TopoHeight    int64  `json:"topoheight"`
    	Major_Version uint64 `json:"major_version"`
    	Minor_Version uint64 `json:"minor_version"`
    	Nonce         uint64 `json:"nonce"`
    	Orphan_Status bool   `json:"orphan_status"`
    	SyncBlock     bool   `json:"syncblock"`
    	TXCount       int64  `json:"txcount"`

    	Reward    uint64   `json:"reward"`
    	Tips      []string `json:"tips"`
    	Timestamp uint64   `json:"timestamp"`
    }



