```
type Hard_fork struct {
    Version     int64 // which version will trigger
    Height      int64 // at what height hard fork will come into effect, trigger block
    Window_size int64 // how many votes to count (x number of votes)
    Threshold   int64 //  between 0 and 99  // percent number of votes required to lock in  hardfork, 0 = mandatory
    Votes       int64 // number of votes in favor
    Voted       bool  // whether voting resulted in hardfork
}
```

```
// this is work in progress
// hard forking is integrated deep within the the blockchain as almost anything can be replaced in DERO without disruption
const default_voting_window_size = 6000 // this many votes will counted
const default_vote_percent = 62         // 62 percent votes means the hard fork is locked in
```

硬分叉，没什么可怕：

Check\_Block\_Version

Get\_HF\_info

Get\_Current\_Version

Get\_Current\_Version\_at\_Height

Get\_Ideal\_Version

Get\_Ideal\_Version\_at\_Height



