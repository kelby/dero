```
// this structure is way blockchain sends outputs to wallet
// this structure is also used internal by blockchain itself, when TXs are expanded and verified

// this structure needs to be expandable without breaking legacy
// This structure is the only information needed by wallet to decode previous and send new txs
// This opens up the case for mobile wallets without downloading entire blockchain
// Some of the fields get duplicated if a tx has multiple vouts
```

    type TX_Output_Data struct {
        BLID          crypto.Hash `msgpack:"L" json:"blid,omitempty"`       // the block id in which this was found, we are duplicating it for all
        TXID          crypto.Hash `msgpack:"T" json:"txid,omitempty"`       // the transaction id in which this was found, we are duplicating it for all vouts
        Tx_Public_Key crypto.Key  `msgpack:"P"  json:"publickey,omitempty"` // the public key of the tx ,  we are duplicating it for all vouts within the TX
        // this is extracted from the extra field

        // this data is consumed by the blockchain itself while expanding tx
        InKey           ringct.CtKey     `msgpack:"D"  json:"inkey,omitempty"`           // contains the vout key and encrypted commitment
        ECDHTuple       ringct.ECdhTuple `msgpack:"E" json:"ecdhtuple,omitempty"`        // encrypted Amounts, will be empty for miner tx
        SenderPk        crypto.Key       `msgpack:"K" json:"senderpk,omitempty"`         // from the outpk
        Amount          uint64           `msgpack:"A,omitempty" json:"amount,omitempty"` // amount used for miner tx
        SigType         uint64           `msgpack:"S" json:"sigtype,omitempty"`          // which ringct type the output was of
        Index_within_tx uint64           `msgpack:"W" json:"indexwithintx,omitempty"`    // output index  of vout within the tx
        Index_Global    uint64           `msgpack:"G" json:"indexglobal,omitempty"`      // position in global index
        Height          uint64           `msgpack:"H" json:"height,omitempty"`           // height to which this belongs
        Unlock_Height   uint64           `msgpack:"U" json:"unlockheight,omitempty"`     // height at which it will unlock
        TopoHeight      int64            `msgpack:"TH" json:"Topoheight,omitempty"`      // Topoheight
        Block_Time      uint64           `msgpack:"B"`                                   // when was this block found in epoch

        Key_Images []crypto.Key `msgpack:"KI,omitempty"`                           // all the key images consumed within the TX
        PaymentID  []byte       `msgpack:"I,omitempty" json:"paymentid,omitempty"` // payment ID contains both unencrypted (33byte)/encrypted (9 bytes)

        // TODO this structure must also keep payment ids and encrypted payment ids
    }



