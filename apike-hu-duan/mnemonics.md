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



