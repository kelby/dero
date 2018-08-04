```
// all components requiring access to wallet must use , this struct to communicate
// this structure must be update while mutex
type RPCServer struct {
    address          string
    srv              *http.Server
    mux              *http.ServeMux
    mr               *jsonrpc.MethodRepository
    Exit_Event       chan bool // wallet is shutting down and we must quit ASAP
    Exit_In_Progress bool

    w *Wallet // reference to the wallet which is open
    sync.RWMutex
}
```

处理请求：

* GetBalance

* GetAddress

* GetHeight

* Transfer

* TransferSplit

* Get\_Bulk\_Payments

* Query\_Key

* Make\_Integrated\_Address

* Split\_Integrated\_Address

* Get\_Transfer\_By\_TXID

* Get\_Transfers

重要请求：

Transfer

TransferSplit



