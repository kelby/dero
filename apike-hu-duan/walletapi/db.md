```
const FUNDS_BUCKET = "FUNDS"                   // stores all incoming funds, key is global output index encrypted form
const FUNDS_AVAILABLE = "FUNDS_AVAILABLE"      // indices of all funds ready to spend
const FUNDS_SPENT = "FUNDS_SPENT"              // indices of all funds already spent
const FUNDS_SPENT_WHERE = "FUNDS_SPENT_WHERE"  // mapping which output -> spent where
const FUNDS_BUCKET_OUTGOING = "FUNDS_OUTGOING" // stores all tx where our funds were spent

const RING_BUCKET = "RING_BUCKET"         //  to randomly choose ring members when transactions are created
const KEYIMAGE_BUCKET = "KEYIMAGE_BUCKET" // used to track which funds have been spent (only on chain ) and which output was consumed
const SECRET_KEY_BUCKET = "TXSECRETKEY"   // used to keep secret keys for any tx this wallet has created
const TX_OUT_DETAILS_BUCKET = "TX_OUT_DETAILS"   // used to keep secret keys for any tx this wallet has created

const HEIGHT_TO_BLOCK_BUCKET = "H2BLOCK_BUCKET" // used to track height to block hash mapping
const OUR_TX_BUCKET = "OUR_TX_BUCKET"           // this contains all TXs in which we have spent OUR  FUNDS

// the strings are prepended so as there can NEVER be collision between TXID and payment ID
// as paymentID are chosen by users
const TXID = "TXID"   // all TX to output index will have this string prepended
const PAYID = "PAYID" // all payment ID to output index will have this string prepended,
```

```
const FUNDS_BY_TX_ID_BUCKET = 11              // each tx id is a bucket
const FUNDS_BY_BLOCK_HEIGHT_BUCKET = 12       // funds sorted by block height
const FUNDS_SPENT_BY_BLOCK_HEIGHT_BUCKET = 13 // funds spent by block height
const NOTES_BY_TXID = 14                      // any notes attached
```

    // see this https://godoc.org/golang.org/x/crypto/pbkdf2
    type KDF struct {
        Hashfunction string `json:"hash"` //"SHA1" currently only sha1 is supported
        Keylen       int    `json:"keylen"`
        Iterations   int    `json:"iterations"`
        Salt         []byte `json:"salt"`
    }


钱包对象

    // this is stored in disk in encrypted form
    type Wallet struct {
        Version semver.Version `json:"version"` // database version
        Secret  []byte         `json:"secret"`  // actual unlocker to the DB, depends on password from user, stored encrypted
        // secret key used to encrypt all DB data ( both keys and values )
        // this is always in encrypted form

        KDF KDF `json:"kdf"`

        account           *Account //`json:"-"` // not serialized, we store an encrypted version  // keys, seed language etc settings
        Account_Encrypted []byte   `json:"account_encrypted"`

        pbkdf2_password []byte // used to encrypt metadata on updates
        master_password []byte // single password which never changes

        Daemon_Endpoint   string `json:"-"` // endpoint used to communicate with daemon
        Daemon_Height     uint64 `json:"-"` // used to track  daemon height  ony if wallet in online
        Daemon_TopoHeight int64  `json:"-"` // used to track  daemon topo height  ony if wallet in online

        wallet_online_mode bool // set whether the mode is online or offline
        // an offline wallet can be converted to online mode, calling.
        // SetOffline() and vice versa using SetOnline
        // used to create transaction with this fee rate,
        //if this is lower than network, then created transaction will be rejected by network
        dynamic_fees_per_kb uint64
        quit                chan bool // channel to quit any processing go routines

        db *bolt.DB // access to DB

        rpcserver *RPCServer // reference to RPCserver

        id string // first 8 bytes of wallet address , to put into logs to identify different wallets in case many are active

        transfer_mutex sync.Mutex // to avoid races within the transfer
        //sync.Mutex  // used to syncronise access
        sync.RWMutex
    }



