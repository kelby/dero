```
// This structure is used to do book keeping for the peer list and keeps other DATA related to peer
// all peers are servers, means they have exposed a port for connections
// all peers are identified by their endpoint tcp address
// all clients are identified by ther peer id ( however ip-address is used to control amount )
// the following daemon commands interact with the list
// bans := print current ban list
// ban address  time  // ban this address for specific time, if time not provided , default ban for 10 minutes
// unban address
// enableban address  // by default all addresses are bannable
// disableban address  // this address will never be banned

var ban_map = map[string]uint64{} // keeps ban maps
```



