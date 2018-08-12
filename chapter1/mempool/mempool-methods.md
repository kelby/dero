功能：

自我管理（self，状态、生命周期等）

交易相关管理（has\_many，交易、KeyImage 等）

方法：

Init\_Mempool

Init\_Block\_Mempool

HouseKeeping

Shutdown

Monitor

HasChanged

Mempool\_Add\_TX

Mempool\_TX\_Exist

Mempool\_Keyimage\_Spent

Mempool\_Delete\_TX

Mempool\_Get\_TX

Mempool\_List\_TX

Mempool\_List\_TX\_SortedInfo

Mempool\_Print

Mempool\_flush

Relayer\_and\_Cleaner（实现是“死循环” + 调用是“协程” ，即可构建一个持续运行的服务）



