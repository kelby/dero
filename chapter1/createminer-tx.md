```
// this function creates a miner tx, with specific blockreward
// TODO we should consider hardfork  version while creating a miner tx
```

参考其数据结构，包含属性：

Extra\_map

Version

Unlock\_Time

Vin

Vout

Extra

RctSignature

这是一次简单版本的“转账”，只有接收方，没有发送方。涉及到的数学、密码学知识是，随机生成交易公私钥，交易公钥公开记录在 Extra\_map，交易私钥同用户地址里的查看公钥、支付公钥混合后记录在 Vout；环签名数据 RctSignature 为空。

Vin 只有高度信息。

> 交易公私钥、混淆地址这块，完全符合 CryptoNote-whitepaper 里 Standard transaction structure 的描述。



