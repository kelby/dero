```
// at this point in time, this is an ultrafast written mempool,
// it will not scale for more than 10000 transactions  but is good enough for now
// we can always come back and rewrite it
// NOTE: the pool is now persistant
type Mempool struct {
	txs           sync.Map //map[crypto.Hash]*mempool_object
	key_images    sync.Map //map[crypto.Hash]bool // contains key images of all txs
	sorted_by_fee []crypto.Hash        // contains txids sorted by fees
	sorted        []TX_Sorting_struct  // contains TX sorting information, so as new block can be forged easily
	modified      bool                 // used to monitor whethel mem pool contents have changed,
	height        uint64               // track blockchain height

	P2P_TX_Relayer p2p_TX_Relayer // actual pointer, setup by the dero daemon during runtime

	// global variable , but don't see it utilisation here except fot tx verification
	//chain *Blockchain
	Exit_Mutex chan bool

	sync.Mutex
}
```

```
// this is only used for sorting and nothing else
type TX_Sorting_struct struct {
	FeesPerByte uint64      // this is fees per byte
	Hash        crypto.Hash // transaction hash
	Size        uint64      // transaction size
}
```

```
// this object is serialized  and deserialized
type mempool_object struct {
	Tx         *transaction.Transaction
	Added      uint64 // time in epoch format
	Height     uint64 //  at which height the tx unlocks in the mempool
	Relayed    int    // relayed count
	RelayedAt  int64  // when was tx last relayed
	Size       uint64 // size in bytes of the TX
	FEEperBYTE uint64 // fee per byte
}
```

```
type p2p_TX_Relayer func(*transaction.Transaction, uint64) int // function type, exported in p2p but cannot use due to cyclic dependency
```



