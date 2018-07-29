```
type Index_Data struct {
	InKey     ringct.CtKey
	ECDHTuple ringct.ECdhTuple // encrypted Amounts
	// Key crypto.Hash  // stealth address key
	// Commitment crypto.Hash // commitment public key
	Height        uint64 // height to which this belongs
	Unlock_Height uint64 // height at which it will unlock
}
```



