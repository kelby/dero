```
// 64 bit arch will use this DB
```

BadgerDBStore

```
type BadgerDBStore struct {
	DB         *badger.DB
	sync.Mutex // lock this struct TODO we must user a reader lock
}

```

BadgerTXWrapper

```
// this object is returned
type BadgerTXWrapper struct {
	bdb *BadgerDBStore
	tx  *badger.Txn
}
```



