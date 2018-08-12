携带着 Params 参数请求过来，由对应 Handler 进行处理，返回对应 Result.

> jsonrpc.Unmarshal\(params, &p\) 将请求过来的参数 params 解析成可理解数据结构 p 然后进行处理，并返回结果。

自身：

RPCServer\_Start

RPCServer\_Stop

Run

请求：

* Echo
* GetBlockCount
* On\_GetBlockHash
* GetBlockTemplate
* SubmitBlock
* GetLastBlockHeader
* GetBlockHeaderByHash
* GetBlockHeaderByHeight
* GetBlockHeaderByTopoHeight
* GetBlock
* GetInfo
* GetTxPool

其它：

* getheight
* getoutputs
* gettransactions
* iskeyimagespent
* SendRawTransaction
* SubmitBlock



