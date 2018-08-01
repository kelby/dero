```
/* this file handles communication with the daemon
 * this includes receiving output information
 */
```

IsDaemonOnlineCached

```
// returns whether wallet was online some time ago
```

IsDaemonOnline

```
// this is as simple as it gets
// single threaded communication to get the daemon status and height
// this will tell whether the wallet can connection successfully to  daemon or not
```

DetectSyncPoint

```
// do the entire sync
// lagging behind is the NOT the major problem
// the problem is the frequent soft-forks
// once an input has been detected, we must check whether the block is not orphan
// we must do this without leaking ourselves to the daemon itself
// this means, we will have to keep track of the chain in the wallet also, ofcouse for syncing purposes only
// we have a bucket where we store  topo height to block hash links , of course in encrypted form
// during syncing we do a a binary search style matching and then sync up from that point
```

Sync\_Wallet\_With\_Daemon

```
// get the outputs from the daemon, requesting specfic outputs
// the range can be anything
// if stop is zero,
// the daemon will flush out everything it has ASAP
// the stream can be saved and used later on
```

sync\_loop

```
// triggers syncing with wallet every 5 seconds
```

Rescan\_From\_Height

Scan\_Offline\_File

```
// offline file is scanned from start till finish
```

SendTransaction

```
// this is as simple as it gets
// single threaded communication to relay TX to daemon
// if this is successful, then daemon is in control
```

IsKeyImageSpent

```
// this is as simple as it gets
// single threaded communication  gets whether the the key image is spent in pool or in blockchain
// this can leak informtion which keyimage belongs to us
// TODO in order to stop privacy leaks we must guess this information somehow on client side itself
// maybe the server can broadcast a bloomfilter or something else from the mempool keyimages
```



