```
// see https://cryptonote.org/cns/cns007.txt to understand address more
```

```
type Address struct {
    Network   uint64
    SpendKey  crypto.Key // these are public keys only
    ViewKey   crypto.Key // these are public keys only
    PaymentID []byte     //integrated payment id is 8 bytes
    // 8 byte version is encrypted on the blockchain
    // 32 byte version is dumped on the chain openly
}

const ChecksumLength = 4

type Checksum [ChecksumLength]byte
```



