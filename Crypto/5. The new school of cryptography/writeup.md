# The new school of cryptography

> > Crypto - 500pts
> 
> Ancient cryptography is old-school - let's go new-school!
> 
> ```
> n = 0xb705b3e846f84772baba18607a5686431967228b5aac2bd59bd4ab52fc4d31d07a14e6eea10fa4556e23f0f433de3233b60cd7237898012cf7086015a32575e36391fbaad50ee56c8a2f89e37195f891b0e40ea14f5023a1d53090efe72e1b96ea9597f302a2c20e0f3e19677d673e7821f2ec2a3bc839671a3555a43c1618cd9e5fcb0cd2a586b85c92dc57fdb31b9ddb751f295a4460ec52d9b6781f2a9a1a40bb69fe5f762f5f7b9acbd4200b99fc2834f02e1b27dba2ce7e8717cca3f7cd579fdabd123d053cebd36cf9060f73f8e3c7c0d013858f07ec0a98ebbca9d9e50b7f6b9db7f73fb8545a114a57972430428224aed62c22b9a3a2a32e398be61d771158b3749f3a2a43762418f8aad8aff7990922db8498bbcd140d1f5ef235b056708bba952c3fbb4bf583524545cfb09f8fba68df3d37d155063ab53a69b6bcdc140ef16edd3094e54baa95e1eef40ee11f2ca013e1d50449d5164af336ad559a4f691e0760ab76a6616778a4fe7d395ad737c47801d8cbecbe759154bc5ba8cba5c994273c646d363ede1c3b744ad45b147e53feb0d4c0e5a9897c1b58318309caa020581d4cd0a4b39159952da4b5dd4f381de35e7051c76c78059b4f84aba2b24310f4b477b2621e59ac09d3f757d78bf19e95d5c326defdfef9f0812b8c9961bd832c9059826cf6e48ccc3cbfe9414260595f53b7d14c18c77b5478b031
> e = 0x3
> c = 0x981ee50d7ce7cfc07aef3d4cb4ef6a444f381c1ad873538ee7dfc7d89f197897bc8588c5f2eb344de7c5999d42242a25c260fd408b932c342f0f8bcaf03b1005897468519e9140cb383dcfdf188f454d726f82337b085ca345e21de714a73f48e66b5177465
> ```
> 
> Can you figure out the original message, `m`?
> ...remember your discrete mathematics...

## Writeup

This is RSA, and we have `n`, `e` and `c`. Because `c` and `e` are small, we can check if the plaintext was so small that `m^e < n`, and to to decrypt the ciphertext that way.

We can verify this by executing the following sage script:
```python
m_guess = c.nth_root(e)
if m_guess.powermod(e, n) == c:
	print "Guessed correct m: %d" % m_guess
```

This mean that the modulo with `n` has no effect, and `c = m^e`, meaning `m` can be recovered by computing the e-th root of `c` and converting it back to ASCII.

After which the text can be retrieved.
The ciphertext can be decoded by execiting the following snippet of sage:
```python
from binascii import unhexlify
print unhexlify(hex(c.nth_root(e)))
```

Yielding the flag
`UiT{security_require_proper_usage}`
