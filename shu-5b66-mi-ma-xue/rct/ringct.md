RCTType

```
const (
	RCTTypeNull = iota
	RCTTypeFull //  we do generate these but they are accepted
	RCTTypeSimple
	RCTTypeFullBulletproof // we DO NOT parse/support/generate these
	RCTTypeSimpleBulletproof
)
```

ECdhTuple

    // Pedersen Commitment is generated from this struct
    // C = aG + bH where a = mask and b = amount
    // senderPk is the one-time public key for ECDH exchange
    type ECdhTuple struct {
    	Mask   crypto.Key `msgpack:"M"`
    	Amount crypto.Key `msgpack:"A"`
    	//	senderPk Key
    }


Key64

```
// Range proof commitments
type Key64 [64]crypto.Key // for Borromean

```

RangeSig

```
// Range Signature
// Essentially data for a Borromean Signature
type RangeSig struct {
	asig BoroSig
	ci   Key64
}

```

BoroSig

```
// Borromean Signature
type BoroSig struct {
	s0 Key64
	s1 Key64
	ee crypto.Key
}
```

BulletProof

```
// size of  single bullet proof range
// we are currently only implementing non-aggregate version only
// as aggregate have following benefits and disadvntages
// 1) they are logarithmic in size but verification is linear, thus aggregate version may make it very easy to DOD
// 2) they can only be used for 2^n outputs  not for randon n
// 3) are very optimised and speedy to verify
// serialised size ((2*6 + 4 + 5)*32 + 3) * n_outputs;
type BulletProof struct {
	V []crypto.Key // 1 * 32           // extra 1 byte for length

	// 4
	A  crypto.Key // 1 * 32
	S  crypto.Key // 1 * 32
	T1 crypto.Key // 1 * 32
	T2 crypto.Key // 1 * 32

	// final 2/5
	taux crypto.Key // 1 * 32
	mu   crypto.Key // 1 * 32

	// 2*6
	L []crypto.Key // 6 * 32  // space requirements while serializing, extra 1 byte for length
	R []crypto.Key // 6 * 32 // space requirements while serializing, extra 1 byte for length

	// final 3/5
	a crypto.Key // 1 * 32
	b crypto.Key // 1 * 32
	t crypto.Key // 1 * 32
}

```

MlsagSig

```
// MLSAG (Multilayered Linkable Spontaneous Anonymous Group) Signature
type MlsagSig struct {
	ss [][]crypto.Key
	cc crypto.Key   // this stores the starting point
	II []crypto.Key // this stores the keyimage, but is taken from the tx/blockchain,it is NOT serialized
}
```

CtKey

    // Confidential Transaction Keys, mask is Pedersen Commitment
    // most of the time, it holds public keys, except (transaction making ) where it holds private keys
    type CtKey struct {
    	Destination crypto.Key `msgpack:"D"` // this is the destination and needs to expanded from blockchain
    	Mask        crypto.Key `msgpack:"M"` // this is the public key amount/commitment homomorphic mask
    }


RctSigBase

```
// Ring Confidential Signature parts that we have to keep
type RctSigBase struct {
	sigType    uint8
	Message    crypto.Key // transaction prefix hash
	MixRing    [][]CtKey  // this is not serialized
	pseudoOuts []crypto.Key
	ECdhInfo   []ECdhTuple
	OutPk      []CtKey // only mask amount is serialized
	txFee      uint64

	Txid crypto.Hash // this field is extra and only used for logging purposes to track which txid was at fault
}

```

RctSigPrunable

```
// Ring Confidential Signature parts that we can just prune later
type RctSigPrunable struct {
	rangeSigs  []RangeSig    //borrowmean range proof
	BulletSigs []BulletProof // bulletproofs range proofs
	MlsagSigs  []MlsagSig    // there can be as many mlsagsigs as many vins
}

```

RctSig

```
// Ring Confidential Signature struct that can verify everything
type RctSig struct {
	RctSigBase
	RctSigPrunable
}
```



