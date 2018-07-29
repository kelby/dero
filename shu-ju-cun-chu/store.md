```
var BLOCKCHAIN_UNIVERSE = []byte("U") //[]byte("BLOCKCHAIN_UNIVERSE") // all block chain data is store in this BLOCKCHAIN_UNIVERSE

// there are only 8 galaxies
var GALAXY_BLOCK = []byte("GB")
var GALAXY_TRANSACTION = []byte("GTX")           // []byte("TRANSACTION")
var GALAXY_TRANSACTION_VALIDITY = []byte("GTXV") //[]byte("TRANSACTIONVALIDITY")
var GALAXY_KEYIMAGE = []byte("GKI")              //[]byte("KEYIMAGE")

var GALAXY_TOPOLOGICAL_ORDER = []byte("GT")  // []byte("TOPOLOGICAL")       // stores  block to topo index mapping
var GALAXY_TOPOLOGICAL_INDEX = []byte("GTI") //[]byte("TOPOLOGICAL_INDEX") // stores topological index  to block mapping

//2 galaxies store inverse mapping
var GALAXY_HEIGHT = []byte("GH")        //[]byte("HEIGHT")             // height to block id mapping
var GALAXY_OUTPUT_INDEX = []byte("GOI") //[]byte("OUTPUT_INDEX") // output index to wallet data for blockchain verification and wallets

// these store unstructured data
var GALAXY_KEYVALUE = []byte("GKV") //[]byte("KEYVALUE") // used to store simple data

// the various attributes stored in keyvalue
var TOP_HEIGHT = []byte("TOP_HEIGHT")   // stores current TOP HEIGHT, only stores single value
var TOPO_HEIGHT = []byte("TOPO_HEIGHT") // stores current TOPO HEIGHT, only stores single value
var TIPS = []byte("TIPS")               // this stores tips
```

```
var PLANET_BLOB = []byte("BLOB")     //it shows serialised block
var PLANET_HEIGHT = []byte("HEIGHT") // contains height
var PLANET_PARENT = []byte("PARENT") // parent of block
var PLANET_PAST = []byte("PAST")     // past of block
var PLANET_FUTURE = []byte("FUTURE") // future of block only 1 level
```

```
var PLANET_SIZE = []byte("SIZE")                      // sum of block + all txs
var PLANET_ALREADY_GENERATED_COINS = []byte("CCOINS") // all coins generated till this block
var PLANET_OUTPUT_INDEX = []byte("OINDEX")            // tx outputs indexing starts from here for this block
var PLANET_OUTPUT_INDEX_END = []byte("OINDEXEND")     // tx outputs indexing ends here ( this is excluded )
var PLANET_CUMULATIVE_DIFFICULTY = []byte("CDIFF")    //[]byte("CDIFFICULTY") // Cumulative difficulty
var PLANET_DIFFICULTY = []byte("DIFF")                //[]byte("DIFFICULTY")             // difficulty
var PLANET_BASEREWARD = []byte("BREWARD")             // base reward of a block  ( new coins generated)
var PLANET_MINERTX_REWARD = []byte("REWARD")          //reward for minertx is stored here ( base reward + collected fees after client protocol run)

var PLANET_TIMESTAMP = []byte("TS") // []byte("TIMESTAMP")

// the TX has the following attributes
var PLANET_TX_BLOB = []byte("BLOB")          // contains serialised  TX , this attribute is also found in BLOCK where
var PLANET_TX_MINED_IN_BLOCK = []byte("MBL") //[]byte("MINERBLOCK") // which blocks mined this tx, stores topo height of mined block
var PLANET_TX_MINED = []byte("MIN")          // all blocks where tx is mined in in
var PLANET_TX_SIZE = []byte("SIZE")
```



