ProveRange

```
//ProveRange and VerifyRange
//ProveRange gives C, and mask such that \sumCi = C
//   c.f. http://eprint.iacr.org/2015/1098 section 5.1
//   and Ci is a commitment to either 0 or 2^i, i=0,...,63
//   thus this proves that "amount" is in [0, 2^64]
//   mask is a such that C = aG + bH, and b = amount
//VerifyRange verifies that \sum Ci = C and that each Ci is a commitment to 0 or 2^i
// this function proves a range using Pedersen  commitment and borromean signatures
// implemented in cryptonote rctSigs.cpp
```

VerifyRange

GenerateBorromean

```
//Borromean (c.f. gmax/andytoshi's paper)
```

VerifyBorromean

```
// Verify the Borromean sig
```



