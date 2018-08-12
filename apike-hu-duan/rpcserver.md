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

还有变量：

```
var Exit_In_Progress bool
var chain *blockchain.Blockchain
var logger *log.Entry
```





