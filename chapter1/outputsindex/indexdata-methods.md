#### Read\_output\_index

```
// this will read the output index data but will not deserialize it
// this is exposed for rpcserver giving access to wallet
```

#### Find\_TX\_Output\_Index

```
// this function finds output index for the tx
// first find a block index , and get the start offset
// then loop the index till you find the key in the result
// if something is not right, we return 0
```

write\_output\_index

```
// this function writes or overwrites the data related to outputs
// the following data is collected from each output
// the secret key,
// the commitment  ( for miner tx the commitment is created from scratch
// 8 bytes blockheight to which this output belongs
// this function should always succeed or panic showing something is not correct
// NOTE: this function should only be called after all the tx and the block has been stored to DB
```

load\_output\_index

```
// this will load the index  data for specific index
// this should be done while holding the chain lock,
// since during reorganisation we might  give out wrong keys,
// to avoid that pitfall take the chain lock
// NOTE: this function is now for internal use only by the blockchain itself
```



