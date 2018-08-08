Verify

```
// this is the function which should be used by external world
// if any exceptions occur while handling, we simply return false
// transaction must be expanded before verification
// coinbase transactions are always success, since they are tied to PoW of block
```

VerifyRctSimple

```
// Verify a RCTTypeSimple RingCT Signature
```

VerifyRctSimpleBulletProof

```
// Verify a RCTTypeSimple RingCT Signature
```

VerifyRctFull

ParseBoroSig

```
// parse Borromean signature
```

ParseRangeSig

```
// range data consists of Single Borromean sig and 64 keys for 64 bits
```

ParseRingCtSignature

```
// parser for ringct signature
// we need to be extra cautious as almost anything cam come as input
```

ParseBulletProof

ecdhEncode

```
   //Elliptic Curve Diffie Helman: encodes and decodes the amount b and mask a
   // where C= aG + bH
   void ecdhEncode(ecdhTuple & unmasked, const key & sharedSec) {
       key sharedSec1 = hash_to_scalar(sharedSec);
       key sharedSec2 = hash_to_scalar(sharedSec1);
       //encode
       sc_add(unmasked.mask.bytes, unmasked.mask.bytes, sharedSec1.bytes);
       sc_add(unmasked.amount.bytes, unmasked.amount.bytes, sharedSec2.bytes);
   }
```

ecdhDecode

```
   //Elliptic Curve Diffie Helman: encodes and decodes the amount b and mask a
   // where C= aG + bH
   void ecdhDecode(ecdhTuple & masked, const key & sharedSec) {
       key sharedSec1 = hash_to_scalar(sharedSec);
       key sharedSec2 = hash_to_scalar(sharedSec1);
       //decode
       sc_sub(masked.mask.bytes, masked.mask.bytes, sharedSec1.bytes);
       sc_sub(masked.amount.bytes, masked.amount.bytes, sharedSec2.bytes);
   }
```

Decode\_Amount

```
// decode and verify a previously encrypted tuple
// the keys come in from the wallet
// tuple is the encoded data
// skey is the secret scalar key
// outpk is public key used to verify whether the decode was sucessfull
```

genC

```
/* from rctOps.cpp
//generates C =aG + bH from b, a is given..
    void genC(key & C, const key & a, xmr_amount amount) {
        key bH = scalarmultH(d2h(amount));
        addKeys1(C, a, bH);
    }
*/
// Commit X amount to random  // see Commitment_From_Amount and ZeroCommitment_From_Amount in key.go
```



