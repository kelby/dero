```
// Package keccak implements the Keccak (SHA-3) hash algorithm.
// http://keccak.noekeon.org / FIPS 202 draft.
```

```
type keccak struct {
    S         [25]uint64
    size      int
    blockSize int
    buf       []byte
    domain    byte
}
```

keccakf

