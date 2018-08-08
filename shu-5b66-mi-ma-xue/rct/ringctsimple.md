Gen\_RingCT\_Simple

```
// this will prove  ringct signature
// message is the tx prefix hash
// inputs contain data of each and every input, together with the ring members and other data
// outputs contains the output amount and key to encode the amount
// fees is the fees to provide
// this function is equivalent to genRctSimple in rctSigs.cpp
```

Gen\_RingCT\_Simple\_BulletProof

```
// this will prove  ringct signature using bullet proof ranges
// message is the tx prefix hash
// inputs contain data of each and every input, together with the ring members and other data
// outputs contains the output amount and key to encode the amount
// fees is the fees to provide
// this function is equivalent to genRctSimple in rctSigs.cpp
```

proveRctMGSimple

```
//Ring-ct MG sigs Simple
//   Simple version for when we assume only
//       post rct inputs
//       here pubs is a vector of (P, C) length mixin
//   inSk is x, a_in corresponding to signing index from the inputs
//       a_out, Cout is for the output commitment
//       index is the signing index..
```



