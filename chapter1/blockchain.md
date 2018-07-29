```
// all components requiring access to blockchain must use , this struct to communicate
// this structure must be update while mutex
type Blockchain struct {
	store       storage.Store // interface to storage layer
	Height      int64         // chain height is always 1 more than block
	height_seen int64         // height seen on peers
	Top_ID      crypto.Hash   // id of the top block
	//Tips              map[crypto.Hash]crypto.Hash // current tips
	dag_unsettled              map[crypto.Hash]bool // current unsettled dag
	dag_past_unsettled_cache   *lru.Cache
	dag_future_unsettled_cache *lru.Cache
	lrucache_workscore         *lru.Cache
	lrucache_fullorder         *lru.Cache // keeps full order for  tips upto a certain height

	MINING_BLOCK bool // used to pause mining

	Difficulty        uint64 // current cumulative difficulty
	Median_Block_Size uint64 // current median block size
	Mempool           *mempool.Mempool
	Exit_Event        chan bool // blockchain is shutting down and we must quit ASAP

	Top_Block_Median_Size uint64 // median block size of current top block
	Top_Block_Base_Reward uint64 // top block base reward

	checkpints_disabled bool // are checkpoints disabled
	simulator           bool // is simulator mode

	P2P_Block_Relayer func(*block.Complete_Block, uint64) // tell p2p to broadcast any block this daemon hash found

	sync.RWMutex
}
```

```
// structure used to rank/sort  blocks on a number of factors
type BlockScore struct {
	BLID crypto.Hash
	// Weight uint64
	Height                int64    // block height
	Cumulative_Difficulty *big.Int // used to score blocks on cumulative difficulty
}
```

```
type cachekey struct {
	blid        crypto.Hash
	base        crypto.Hash
	base_height int64
}
```



