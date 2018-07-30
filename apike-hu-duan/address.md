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

地址由 5 部分组成，其中 Network、SpendKey、ViewKey 部分为必需项，PaymentID 和 ChecksumLength 为可选项。

```

                                         Keccak
                      +-----------------------------------+
                      |                                   |
                      |                                   V
   +---------+-------------+-------------+   +----------+--------------+
   | Public  |             |             |   | Checksum |              |
   | address |      A      |      B      |   |  (first  |    Unused    |
   | prefix  |             |             |   | 4 bytes) |              |
   +---------+-------------+-------------+   +----------+--------------+

   +<-------------------------------------------------->+
                              |
                              | Base58
                              V
                   +--------------------+
                   | CryptoNote Address |
                   +--------------------+

```



