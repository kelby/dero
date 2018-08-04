    type _Keys struct {
    	Spendkey_Secret crypto.Key `json:"spendkey_secret"`
    	Spendkey_Public crypto.Key `json:"spendkey_public"`
    	Viewkey_Secret  crypto.Key `json:"viewkey_secret"`
    	Viewkey_Public  crypto.Key `json:"viewkey_public"`
    }

    // all random outputs are stored within wallet in this form
    // to be used as ring members
    type Ring_Member struct { // structure size is around 74 bytes
    	InKey         ringct.CtKey `msgpack:"K"`
    	Index_Global  uint64       `msgpack:"I"`
    	Height        uint64       `msgpack:"H"`
    	Unlock_Height uint64       `msgpack:"U,omitempty"` // this is mostly empty
    	Sigtype       uint64       `msgpack:"S,omitempty"` // this is empty for miner tx
    }

    type Account struct {
    	Keys           _Keys   `json:"keys"`
    	SeedLanguage   string  `json:"seedlanguage"`
    	FeesMultiplier float32 `json:"feesmultiplier"` // fees multiplier accurate to 2 decimals
    	Mixin          int     `json:"mixin"`          // default mixn to use for txs

    	ViewOnly bool `json:"viewonly"` // is this viewonly wallet

    	Index_Global uint64 `json:"index_global"` // till where the indexes have been processed, it must only increase and never decrease
    	Height       uint64 `json:"height"`       // block height till where blockchain has been scanned
    	TopoHeight   int64  `json:"topoheight"`   // block height till where blockchain has been scanned

    	//Wallet_Height    uint64    `json:"wallet_height"`// used to track height till which we have scanned the inputs

    	balance_stale  bool   // whether the balance  is stale
    	Balance_Mature uint64 `json:"balance_mature"` // total balance of account
    	Balance_Locked uint64 `json:"balance_locked"` // balance locked

    	random_percent uint64 // number of outputs to store within the db, for mixing, default is 10%

    	key_image_checklist map[crypto.Key]bool // key images which need to be monitored, this is updated when new funds arrive

    	//Outputs_Array []TX_Wallet_Data // all outputs found in the chain belonging to us, as found in chain

    	// uint64 si the Index_Global which is the unique number
    	//Outputs_Index    map[uint64]bool               // all outputs which  are ours for deduplication
    	//Outputs_Ready    map[uint64]TX_Wallet_Data     // these outputs are ready for consumption ( maturity needs to be checked)
    	//Keyimages_Ready  map[crypto.Key]bool           // keyimages which are ready to get consumed, // we monitor them to find which
    	//Outputs_Consumed map[crypto.Key]TX_Wallet_Data // the key is the keyimage

    	//Random_Outputs  map[uint64]TX_Wallet_Data  // random ring members
    	//Random_Outputs_Recent map[uint64]TX_Wallet_Data  // random ring members from recent blocks
    	//Ring_Members    map[uint64]bool // ring members

    	sync.Mutex // syncronise modifications to this structure
    }

    // this structure is kept by wallet
    type TX_Wallet_Data struct {
    	TXdata globals.TX_Output_Data `msgpack:"txdata"` // all the fields of output data

    	WAmount      uint64       `msgpack:"wamount"` // actual amount, in case of miner it is verbatim, for other cases it decrypted
    	WKey         ringct.CtKey `msgpack:"wkey"`    // key which is used to later send this specific output
    	WKimage      crypto.Key   `msgpack:"wkimage"` // key image which gets consumed when this output is spent
    	WSpent       bool         `msgpack:"wspent"`  // whether this output has been spent
    	WSpentPool   bool         //`msgpack:""`// we built and send out a tx , but it has not been mined
    	WPaymentID   []byte       `msgpack:"wpaymentid"`   // payment if if present and decrypted if required
    	WSecretTXkey crypto.Key   `msgpack:"wsecrettxkey"` // tx secret which can be be used to prove that the funds have been spent
    }

```
type Entry struct {
	Index_Global uint64
	Height       uint64
	TopoHeight   int64
	TXID         crypto.Hash
	Amount       uint64
	PaymentID    []byte
	Status       byte
	Unlock_Time  uint64
}
```



