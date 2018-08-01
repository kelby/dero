```
type Language struct {
    Name                 string   // Name of the language
    Name_English         string   // Name of the language in english
    Unique_Prefix_Length int      // number of utf8 chars (not bytes) to use for checksum
    Words                []string // 1626 words
}
```

```
// any language needs to be added to this array
var Languages = []Language{
    Mnemonics_English,
    Mnemonics_Japanese,
    Mnemonics_Chinese_Simplified,
    Mnemonics_Dutch,
    Mnemonics_Esperanto,
    Mnemonics_Russian,
    Mnemonics_Spanish,
    Mnemonics_Portuguese,
    Mnemonics_French,
    Mnemonics_German,
    Mnemonics_Italian,
}
```

```
const SEED_LENGTH = 24 // checksum seeds are 24 + 1 = 25 words long
```

Language\_List

```
// return all the languages support by us
```

Words\_To\_Key

长度、语言、校验和

每 3 个字（单词）为一组，共 8 组，进行转换。

```
//this function converts a list of words to a key
```

Key\_To\_Words

只有 SpendKey 参与转换，其它项都是固定配置好的。

SpendKey 共 32 字节，即 64 个字符，共 8 轮转换，每轮得到 3 个字（或单词）。

转换之前：每个字符是 16 进制

转换之后：每个字（或单词）是 1626 进制

所以，我们的助记词可以做到更短，但又不失安全性。

```
// this will map the key to recovery words from the spcific language
// language must exist,if not we return english
```



