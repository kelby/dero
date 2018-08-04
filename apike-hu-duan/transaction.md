EncryptDecryptPaymentID

```
// this function is used to encrypt/decrypt payment id
// as the operation is symmetric XOR, is the same in both direction
```

Prove

```
// this function will prove detect and decode output amount for the tx
```

Transaction\_Prefix

    // the core transaction
    type Transaction_Prefix struct {
        Version       uint64 `json:"version"`
        Unlock_Time   uint64 `json:"unlock_time"` // used to lock first output
        Vin           []Txin_v
        Vout          []Tx_out
        Extra         []byte
        Extra_map     map[EXTRA_TAG]interface{} `json:"-"` // all information parsed from extra is placed here
        PaymentID_map map[EXTRA_TAG]interface{} `json:"-"` // payments id parsed or set are placed her
        ExtraType     byte                      `json:"-"` // NOT used, candidate for deletion
    }

Transaction

    type Transaction struct {
        Transaction_Prefix
        // same as Transaction_Prefix
        // Signature  not sure of what form
        Signature []Signature_v1 `json:"-"` // old format, the array size is always equal to vin length,
        //Signature_RCT RCT_Signature  // version 2

        RctSignature *ringct.RctSig
        Expanded     bool `json:"-"`
    }

交易拆分：

前缀，后缀（即签名）

前缀包含：输入、输出、额外数据、元数据。

GetHash

```
		// version 2 requires first computing 3 separate hashes
		// prefix, rctBase and rctPrunable
		// and then hashing the hashes together to get the final hash
```



