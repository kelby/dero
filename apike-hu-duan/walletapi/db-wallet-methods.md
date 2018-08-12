第一类：

**Create\_Encrypted\_Wallet**

```
// this file implements the encrypted data store at rest
```

Create\_Encrypted\_Wallet\_From\_Recovery\_Words

```
// create an encrypted wallet using electrum recovery words
```

Create\_Encrypted\_Wallet\_Random

```
// create an encrypted wallet using electrum recovery words
```

Create\_Encrypted\_Wallet\_ViewOnly

```
// create an encrypted wallet using using random data
```

Create\_Encrypted\_Wallet\_NonDeterministic

```
// create an encrypted wallet using using random data
```

Open\_Encrypted\_Wallet

Generate\_Key

```
// generate key from password
```

第二类：

Set\_Encrypted\_Wallet\_Password

```
// wallet must already be open
```

Check\_Password

```
// check whether the already opened wallet can use this password
```

Save\_Wallet

```
// save updated copy of wallet
```

Close\_Encrypted\_Wallet

```
// close the wallet
```

check\_key\_exists

```
// check whether a key exists
```

delete\_key

```
// delete specified key
```

delete\_bucket

```
// delete specified key
```

store\_key\_value

```
// store a key-value, everything is encrypted
```

load\_key\_value

load\_all\_values\_from\_bucket

load\_ring\_member

