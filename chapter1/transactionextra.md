```
// refer https://cryptonote.org/cns/cns005.txt to understand slightly more ( it DOES NOT cover everything)
// much of these constants are understood from tx_extra.h and cryptonote_format_utils.cpp
// TODO pending test case
type EXTRA_TAG byte

const TX_EXTRA_PADDING EXTRA_TAG = 0 // followed by 1 byte of size, and then upto 255 bytes of padding
const TX_PUBLIC_KEY EXTRA_TAG = 1    // follwed by 32 bytes of tx public key
const TX_EXTRA_NONCE EXTRA_TAG = 2   // followed by 1 byte of size, and then upto 255 bytes of empty nonce

// TX_EXTRA_MERGE_MINING_TAG  we do NOT suppport merged mining at all
// TX_EXTRA_MYSTERIOUS_MINERGATE_TAG  as the name says mysterious we will not bring it

// these 2 fields have complicated parsing of extra, other the code was really simple
const TX_EXTRA_NONCE_PAYMENT_ID EXTRA_TAG = 0           // extra nonce within a non coinbase tx, can be unencrypted, is 32 bytes in size
const TX_EXTRA_NONCE_ENCRYPTED_PAYMENT_ID EXTRA_TAG = 1 // this is encrypted and is 9 bytes in size
```



