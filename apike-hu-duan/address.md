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

Network 1 字节，2 字符

SpendKey 32 字节，64 字符

ViewKey 32 字节，64 字符

ChecksumLength 4 字节，8 字符

```
prefix, a.SpendKey[:], a.ViewKey[:], checksum[:]
```

总长度 138（如果包含 PaymentID，即为集成地址，会更长）

```
prefix, a.SpendKey[:], a.ViewKey[:], a.PaymentID, checksum[:]
```

PaymentID 一般为 8 字节，16 字符。（此时总长度为 154）

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

GetChecksum 用 Keccak256 进行散列哈希获得

Base58 编码

IsMainnet // tells whether address is mainnet address，可以根据前缀（Network）进行判断

IsIntegratedAddress // tells whether address is mainnet address，可以根据前缀（Network）进行判断

NewAddress

NewAddressFromKeys // create a new address from keys

> 完全符合 cns007 - CryptoNote Keys and Addresses 所描述的内容。

实际操作过程中，我们可以从椭圆曲线上选择一个点做为花费私钥，然后对应的得到花费公钥。对花费私钥进行散列哈希，得到查看私钥，以及查看公钥。据此，我们只要保管好花费私钥即可。

