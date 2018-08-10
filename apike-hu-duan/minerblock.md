## 区块的产生

#### Create\_new\_miner\_block

**自己构建“块”**

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

交易数据，可以从交易池里面获得；

块的元数据，可以自己构建；

Coinbase，可以自己创建；

其它数据，可以从内存或者数据库里获取。

**Create\_new\_block\_template\_mining**

```
// returns a new block template ready for mining
// block template has the following format
// miner block header in hex  +
// miner tx in hex +
// 2 bytes ( inhex 4 bytes for number of tx )
// tx hashes that follow
```

**Accept\_new\_block**

接收到“块”

```
// accept work given by us
// we should verify that the transaction list supplied back by the miner exists in the mempool
// otherwise the miner is trying to attack the network
```



