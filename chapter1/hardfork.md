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



