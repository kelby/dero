GetChecksum 用 Keccak256 进行散列哈希获得

Base58 编码

IsMainnet // tells whether address is mainnet address，可以根据前缀（Network）进行判断

IsIntegratedAddress // tells whether address is mainnet address，可以根据前缀（Network）进行判断

NewAddress

NewAddressFromKeys // create a new address from keys

> 完全符合 cns007 - CryptoNote Keys and Addresses 所描述的内容。

实际操作过程中，我们可以从椭圆曲线上选择一个点做为花费私钥，然后对应的得到花费公钥。对花费私钥进行散列哈希，得到查看私钥，以及查看公钥。据此，我们只要保管好花费私钥即可。



