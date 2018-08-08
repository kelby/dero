BoltStore

```
type BoltStore struct {
	DB         *bolt.DB
	tx         *bolt.Tx
	sync.Mutex // lock this struct
	rw sync.RWMutex
}
```

BoltTXWrapper

```
// this object is returned
type BoltTXWrapper struct {
	bdb *BoltStore
	tx  *bolt.Tx
}
```



