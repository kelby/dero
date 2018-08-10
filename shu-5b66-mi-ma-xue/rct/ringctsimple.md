## 交易签名

#### Input\_info

```
// structure using which information is fed from wallet
// these are only used while proving ringct simple
type Input_info struct {
    Amount       uint64      // amount in this input
    Key_image    crypto.Hash // keyimage in this input
    Index        int         // index position within ring members
    Index_Global uint64
    Ring_Members []uint64 // ring members  already sorted absolute
    Pubs         []CtKey  // public keys from ring members ( secret key from our input)
    Sk           CtKey    // secret key for the input
}
```

#### Output\_info

```
type Output_info struct {
    Amount           uint64     // only first output is locked
    Public_View_Key  crypto.Key // taken from address
    Public_Spend_Key crypto.Key // taken from address
    Scalar_Key       crypto.Key // used to encrypt amounts
    // Destination crypto.Key
    //Addr  address.Address
}
```

#### Gen\_RingCT\_Simple

```
// this will prove  ringct signature
// message is the tx prefix hash
// inputs contain data of each and every input, together with the ring members and other data
// outputs contains the output amount and key to encode the amount
// fees is the fees to provide
// this function is equivalent to genRctSimple in rctSigs.cpp
```

#### Gen\_RingCT\_Simple\_BulletProof

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



