ChaCha20-Poly1305 对称加密算法，是 Google 所采用的一种新式加密算法，性能强大。

ChaCha20-Poly1305 是由 ChaCha20 流密码和 Poly1305 消息认证码（MAC）结合的一种应用在互联网安全协议中的认证加密算法。

EncryptWithKey

```
// all data in encrypted within the storage using this, PERIOD
// all data has a new nonce, appended to the the data , last 12 bytes
```

DecryptWithKey

```
// extract 12 byte nonce from the data and deseal the data
```



