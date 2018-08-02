Create\_new\_miner\_block

```
//NOTE: this function is quite naughty due to chicken and egg problem
// we cannot calculate reward until we known blocksize ( exactly upto byte size )
// also note that we cannot calculate blocksize  until we know reward
// how we do it
// reward field is a varint, ( can be 8 bytes )
// so max deviation can be 8 bytes, due to reward
// so we do a bruterforce till the reward is obtained but lets try to KISS
// the top hash over which to do mining now ( it should already be in the chain)
// this is work in progress
// TODO we need to rework fees algorithm, to improve its quality and lower fees
```

Create\_new\_block\_template\_mining

```
// returns a new block template ready for mining
// block template has the following format
// miner block header in hex  +
// miner tx in hex +
// 2 bytes ( inhex 4 bytes for number of tx )
// tx hashes that follow
```

Accept\_new\_block

```
// accept work given by us
// we should verify that the transaction list supplied back by the miner exists in the mempool
// otherwise the miner is trying to attack the network
```



