Get\_pre\_mlsag\_hash

final\_data\_hash = message\_hash + base\_hash + other\_data\_hash

```
// this file has license pending  since it triggers a hard to find golang bug TODO add license after the golang bug is fixed
/* This file implements MLSAG signatures for the transactions */

// get the hash of the transaction which is used to create the mlsag later on, this hash is input to MLSAG
// the hash is = hash( message + hash(basehash) + hash(pederson and borromean data))
```

MLSAG\_Ver

```
//Multilayered Spontaneous Anonymous Group Signatures (MLSAG signatures)
//This is a just slghtly more efficient version than the ones described below
//(will be explained in more detail in Ring Multisig paper
//These are aka MG signatutes in earlier drafts of the ring ct paper
// c.f. http://eprint.iacr.org/2015/1098 section 2.
// keyImageV just does I[i] = xx[i] * Hash(xx[i] * G) for each i
// Gen creates a signature which proves that for some column in the keymatrix "pk"
//   the signer knows a secret key for each row in that column
// Ver verifies that the MG sig was created correctly
```

MLSAG\_Gen

```
//Multilayered Spontaneous Anonymous Group Signatures (MLSAG signatures)
//This is a just slghtly more efficient version than the ones described below
//(will be explained in more detail in Ring Multisig paper
//These are aka MG signatutes in earlier drafts of the ring ct paper
// c.f. http://eprint.iacr.org/2015/1098 section 2.
// keyImageV just does I[i] = xx[i] * Hash(xx[i] * G) for each i
// Gen creates a signature which proves that for some column in the keymatrix "pk"
//   the signer knows a secret key for each row in that column
// Ver verifies that the MG sig was created correctly
```



