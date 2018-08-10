    // This structure is used to do book keeping for the peer list and keeps other DATA related to peer
    // all peers are servers, means they have exposed a port for connections
    // all peers are identified by their endpoint tcp address
    // all clients are identified by ther peer id ( however ip-address is used to control amount )
    // the following daemon commands interact with the list
    // peer_list := print the peer list
    // ban address  time  // ban this address for spcific time
    // unban address
    // enableban address  // by default all addresses are bannable
    // disableban address  // this address will never be banned
    type Peer struct {
        Address string `json:"address"` // pairs in the ip:port or dns:port, basically  endpoint
        ID      uint64 `json:"peerid"`  // peer id
        Miner   bool   `json:"miner"`   // miner
        //NeverBlacklist    bool    // this address will never be blacklisted
        LastConnected   uint64 `json:"lastconnected"`   // epoch time when it was connected , 0 if never connected
        FailCount       uint64 `json:"failcount"`       // how many times have we failed  (tcp errors)
        ConnectAfter    uint64 `json:"connectafter"`    // we should connect when the following timestamp passes
        BlacklistBefore uint64 `json:"blacklistbefore"` // peer blacklisted till epoch , priority nodes are never blacklisted, 0 if not blacklist
        GoodCount       uint64 `json:"goodcount"`       // how many times peer has been shared with us
        Version         int    `json:"version"`         // version 1 is original C daemon peer, version 2 is golang p2p version
        Whitelist       bool   `json:"whitelist"`
        sync.Mutex
    }

IsPeerInList

GetPeerInList

Peer\_Add

Peer\_SetFail

Peer\_SetSuccess

Peer\_Delete

PeerList\_Print

Peer\_Counts



