第一类：

**Generate\_Keys\_From\_Random**

```
// generate keys from using random numbers
```

**Generate\_Keys\_From\_Seed**

```
// generate keys from seed which is from the recovery words
// or we feed in direct
```

Generate\_Account\_From\_Recovery\_Words

```
// generate user account using recovery seeds
```

Generate\_Account\_From\_Seed

Generate\_Account\_View\_Only

```
// generate keys for view only wallet
```

Generate\_Account\_NONDeterministic\_Only

```
// generate keys for view only wallet
```

第二类：

GetSeed

GetSeedinLanguage

GetViewWalletKey

```
// view wallet key consists of public spendkey and private view key
```

GetAddress

GetRandomIAddress8

GetRandomIAddress32

**Is\_Output\_Ours**

```
// one simple function which does all the crypto to find out whether output belongs to this account
// NOTE: this function only uses view key secret and Spendkey_Public
// output index is the position of vout within the tx list itself
```

**Generate\_Helper\_Key\_Image**

```
// this function does all the keyderivation required for decrypting ringct outputs, generate keyimage etc
// also used when we build up a transaction for mining or sending amount
```

Decode\_RingCT\_Output

Add\_Transaction\_Record\_Funds

Is\_Our\_Fund\_Consumed

Consume\_Transaction\_Record\_Funds

Get\_Balance\_Rescan

Get\_Balance

Store\_Height\_Mapping

Add\_Possible\_Ring\_Member

Show\_Transfers

Get\_Payments\_Payment\_ID

Get\_Payments\_TXID

Start\_RPC\_Server

Stop\_RPC\_Server

Clean

Is\_View\_Only

Is\_Balance\_Modified

Get\_Height

Get\_TopoHeight

Get\_Daemon\_Height

Get\_Index\_Global

Get\_Keys

SetOfflineMode

GetMode

SetDaemonAddress

SetOnlineMode

SetMixin

GetMixin

SetFeeMultiplier

GetFeeMultiplier

getfees

SetSeedLanguage

GetSeedLanguage

GetTXKey

GetTXOutDetails

