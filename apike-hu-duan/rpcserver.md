服务端：处理软件相关 RPC 请求

软件 RPC

```
/* this file implements the rpcserver api, so as wallet and block explorer tools can work without migration */

// all components requiring access to blockchain must use , this struct to communicate
// this structure must be update while mutex
type RPCServer struct {
    srv        *http.Server
    mux        *http.ServeMux
    Exit_Event chan bool // blockchain is shutting down and we must quit ASAP
    sync.RWMutex
}
```

携带着 Params 参数请求过来，由对应 Handler 进行处理，返回对应 Result.

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



