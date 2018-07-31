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

```
// this will map the key to recovery words from the spcific language
// language must exist,if not we return english
```



