# gpg2openpgpkey
DNS OPENPGPKEY record generator  
Author: Shumon Huque

A command line program that generates a DNS OPENPGPKEY resource record
(in textual presentation format) from a given email address and file 
containing a GPG key.

Pre-requisites:  
- GNUpg, version 2.x (recommended, although works with 1.x too)
- Python 2.7 or later, or Python 3  

```
resolve.py version 0.14

$ gpg2openpgpkey.py

Usage: gpg2openpgpkey.py [-g] <email> <gpgkeyfile>

       -g     Output DNS generic RDATA format (rather than OPENPGPKEY)

Given an email address and a file containing a GPG public key, this program
generates a corresponding DNS OPENPGPKEY resource record in presentation
format.
```

Some example output:  

```
$ gpg2openpgpkey.py gaspard@dhautefeuille.eu test/key-ed25519-gaspara.asc

OpenPGPKey:
  keyid=5D388423C8F0A689 fpr=BF067A224E73007BA1C09DDA5D388423C8F0A689
  algorithm=22 (Ed25519) keylen=256 flags=[scESC]
  CreateDate: 2016-05-02
    uid: "Gaspard d'Hautefeuille" <gaspard@dhautefeuille.eu>
SubKey:
  keyid=A1A614F940DE794D fpr=5B7115DC092F350118FBF6D9A1A614F940DE794D
  algorithm=18 (ECDH) keylen=256 flags=[e]
  CreateDate: 2016-05-02

18fb60acb12a08530d95f8a11c43d917f0a2fd12f95ac4f96d469a0a._openpgpkey.dhautefeuille.eu. IN OPENPGPKEY (
                  mDMEVyeX/hYJKwYBBAHaRw8BAQdAU+F0jSwToQ2ddh5HPcE+QUwp3ZjufJtZ
                  31LQiq/92b60MUdhc3BhcmQgZCdIYXV0ZWZldWlsbGUgPGdhc3BhcmRAZGhh
                  dXRlZmV1aWxsZS5ldT6IfwQTFggAJwUCVyeX/gIbAwUJBaOagAULCQgHAgYV
                  CAkKCwIEFgIDAQIeAQIXgAAKCRBdOIQjyPCmicMuAPwLl+j0qfdet9MqAFQo
                  tTo5zkCyDi0ep9T+HxyzI1MEhwEAr/UmWC9/0EKQfEE0EnE6ja5bjBEwkUpb
                  xMlHlm2uEQu4OARXJ5f+EgorBgEEAZdVAQUBAQdAEOdBZ2Ob2VrM/+DLFaJt
                  Cck9kjcRI7ca586/zysZlg0DAQgHiGcEGBYIAA8FAlcnl/4CGwwFCQWjmoAA
                  CgkQXTiEI8jwpokY0QEAnP3YkqBV8hs5YodqqEBks/3kC/x2nrHfjLizaUyV
                  9bQA/A8gCB9CQkfSyZUA8AncxwcqbI19rcclaSxluaf2X44K
)
```

```
$ gpg2openpgpkey.py shuque@huque.com /tmp/key1.asc

OpenPGPKey:
  keyid=7B5CC91ED5FD4336 fpr=304E0AA4B055C944350EF6A87B5CC91ED5FD4336
  algorithm=1 (RSA) keylen=2048 flags=[scESC]
  CreateDate: 2014-04-16
    uid: "Shumon Huque" <shuque@verisign.com>
    uid: "Shumon Huque" <shuque@upenn.edu>
    uid: "Shumon Huque" <shuque@huque.com>
    uid: "Shumon Huque" <shuque@gmail.com>
SubKey:
  keyid=B2B5852A1E2B752A fpr=2359800E3D38C9AA453B5E8AB2B5852A1E2B752A
  algorithm=1 (RSA) keylen=2048 flags=[e]
  CreateDate: 2014-04-16

adcd5698c7fc6c44e65e893ab7e84a638db4910d04e8e53314e8a101._openpgpkey.huque.com. IN OPENPGPKEY (
                  mQENBFNPDOkBCADAZikSR4TvRxMtU0WhbWFkZvXWOYdhWSPigqbsy7T5PTNa
                  ALwPJaMGX5JLg/+T7kJK6WFjFfvuIc60PD5Rn71df/SqvyRdx2fWjWyjzvNf
                  pY9IdeouIUKhWTyL+XTxhog4Vcq0MpouePm9lXORE2PxNNjRkrO1RuttiQ9x
                  AqN+Mw2KJt+oP3cwIIKKD6s0igTz11cBb+7akogdjZv5kXdmkbXNqekqScIP
                  /iRw80lv80XS4FLOQizpQE3Owd7Y2eRY3KiydKEVFiV2mWHb2zK/p7zqt4Xs
                  5cYncnLVt7dHy4smXfgRDpx7aK+LxQDwXxI6C1fQM7MJRJbhs/l9YKI1ABEB
                  AAG0H1NodW1vbiBIdXF1ZSA8c2h1cXVlQHVwZW5uLmVkdT6JATgEEwECACIF
                  AlNPDyYCGwMGCwkIBwMCBhUIAgkKCwQWAgMBAh4BAheAAAoJEHtcyR7V/UM2
                  IdYH/17ZgkMzUjNyij1S5gDDxCAbITDQAm9bCqrvssvD1m7u3c05Zmm05ciM
                  nPaOREGIQ6oFpYQP2F+pDeVBMmzLiLEkw9yVu18hurg4cnBvq6bIL7K43ME5
                  hWXu31G6HvYsaMpOnSxt1vmtDpgj9UyN/KFBHzzlcY2qJbI90VCubzgBQuU1
                  4+NT2ZLYOedGBWlUpx1kRSHEOCkMebUKZl8I7ebO/2/h4LVYnLDjWMbaUrgn
                  hLi8xqYq/vmsWCpSkA3WZZTlaiCk7tDwmdR1YJoJixa42xkJ58CC2YYe1yF4
                  +5XK6dGVP2PL6/XPfS3pFf2FOXOSr9WVSyvBJlBxUjpz0We0H1NodW1vbiBI
                  dXF1ZSA8c2h1cXVlQGh1cXVlLmNvbT6JATgEEwECACIFAlNPDOkCGwMGCwkI
                  BwMCBhUIAgkKCwQWAgMBAh4BAheAAAoJEHtcyR7V/UM24bkIAJ9a60Tl96A9
                  5G4ow6leNPwUbpB4PFfOBPXaEPtQsug7NObeaS5cusrAqlhRtZY7TE7QqYSz
                  byKB4tHkaTDRDPjk85fB9nvHdFDv42s7O2Zos+MFMOUBN626Ejp8WmWBHPcw
                  vdFRb6Cp4c11txU7ShAlvQJ6uHff57ugGxYloEbaVILMU5iprk7GtdXJWkgW
                  jLOvLHr+fG2c59kYCI/8eMoyDp5ACGAHRUKV68yyZrpGBFRCQMZ3RDFVpGNd
                  zyZKHcvgEMwlpZoIgI6t9IQFMG8iRqGh/qx8LYeNFC9z2A0+28SDpqtB5/HA
                  O/QWJEi9iJSRt+J2SNTU0mI8rxUkE320H1NodW1vbiBIdXF1ZSA8c2h1cXVl
                  QGdtYWlsLmNvbT6JATgEEwECACIFAlNPDwgCGwMGCwkIBwMCBhUIAgkKCwQW
                  AgMBAh4BAheAAAoJEHtcyR7V/UM2CGYIAK9AF9wEvESkZXJfIQSf73A3jzwE
                  YjXVdWK9BnirYQOX6AynOf5uuDQLl305d8EAz7bB/iMF28wscxe001AyX7F+
                  dprF2wpBxPDLIVBfGuXP4JQ/rNqIOLc8pknT5gjzjp7mf7tObeURFi77Enmm
                  7Ubnk/jtcNSbPvyhVQNCLcL8su+4OJnGL9PgVeYpYVvkYx6u/OAt3BGlcL3o
                  SwY9EuxvQKjidStY8xYnPpsLusBYgwsgjfCw4J5HOjV0j0kvJMXKEHCpKWYf
                  YmG/LfuknyOZ9B6w7bng3vDcV11gcVZwsLivLceIr+LMdDT8wJRidykAhPxK
                  HHEqNpLkg6fHXxm0IlNodW1vbiBIdXF1ZSA8c2h1cXVlQHZlcmlzaWduLmNv
                  bT6JATgEEwECACIFAlNPERICGwMGCwkIBwMCBhUIAgkKCwQWAgMBAh4BAheA
                  AAoJEHtcyR7V/UM26BoH/iC3OBoTfV02ATh6Rz+CH4xnKq+qOvTrTDtnnJIZ
                  LZu32UIttJr+bmvbnEB9OoArQlkAQrZCP01BXoUb9EB2WK3gkp60iuptdekb
                  Lcs4pE+ykqbGvUnOEZa4RXVSDQracQsB6dcqlOOQorlYFuoTKhwQnfIsq+8P
                  c6Wf9r6LvsABampIrl3i/vv/ugDFo2tgdYKNMoz0b++GyvY4nFqTye339esT
                  d0LeJOHXWBuUp3v9h4LqvHvOPmWbwzcCyOPqA19ysvfhWMg5m04lphFAepcY
                  gf6fHh2ZEp9y/ewo/5WkR6rpoI29VtIenIip8bBpjtHLMCGyL4uwf9MoPEti
                  Sb65AQ0EU08M6QEIAOXjUAtI7ZpGB0+kT9Vr/kwoMNUvCc1uyz8yn6jA1XpI
                  Lh7mcx6V+zzB+GpC5+iOHl2GgFAlD89fB6UEyAhD0utFDDUawEBkzU/uj6yC
                  ze5FVYfDka9xX9GfKRmLVuDujF96VsUFzc0tIkzBiHVylr2WszY+MvtfJEER
                  UidGk7mUnNHuZYrRdMM1sF8Pn31u2zBxe1gb3kgRMJVOFNuc7UIYt8QVUnla
                  NBJ60NoNXQkMgFdhtW9YGDZsTHiJq5YrIVKzKsMft2KUWUN41VcKRIw/STD+
                  5mnIGZwIWSpOVPvvujkOlSO7AnHoyl5mQbhpO4R76BrUHngk53JuxKE4u9cA
                  EQEAAYkBHwQYAQIACQUCU08M6QIbDAAKCRB7XMke1f1DNtbAB/4hdah7V5oT
                  JdxbZZQxGHaHnarRBRmGlJlhObZpBIKQnNxr8f6mhgoy6ajveWM/RfiUNxex
                  +hSQshQDThPLKi2KNkp0gijB2RMK+0i4ikMRL24GqF/8ARel1KsastJ9Z4TS
                  9UBIh4MVeg44eMsMyvBwVi28BcgMHnrhXKJIM8xYjuXIYcnh/FsPYtn4NQmR
                  LCo3cHPG8AA4QBLGXhlfN8PefU4awjX/ig+KXJiBtaYyKxKQp7jKZDcjICJd
                  wFrgi09L6H4pkT4CLJM/OBcUB+JlkBPxyTelXhduJIDRxEy1gLlQijlVBZxe
                  vd4bOavKSL3b8L7QitewKsVdiptiFhwr
)
```

```
$ gpg2openpgpkey.py -g shuque@huque.com /tmp/key1.asc

OpenPGPKey:
  keyid=7B5CC91ED5FD4336 fpr=304E0AA4B055C944350EF6A87B5CC91ED5FD4336
  algorithm=1 (RSA) keylen=2048 flags=[scESC]
  CreateDate: 2014-04-16
    uid: "Shumon Huque" <shuque@verisign.com>
    uid: "Shumon Huque" <shuque@upenn.edu>
    uid: "Shumon Huque" <shuque@huque.com>
    uid: "Shumon Huque" <shuque@gmail.com>
SubKey:
  keyid=B2B5852A1E2B752A fpr=2359800E3D38C9AA453B5E8AB2B5852A1E2B752A
  algorithm=1 (RSA) keylen=2048 flags=[e]
  CreateDate: 2014-04-16

adcd5698c7fc6c44e65e893ab7e84a638db4910d04e8e53314e8a101._openpgpkey.huque.com. IN TYPE61 \# 2229 (                  99010d04534f0ce9010800c06629124784ef47132d5345a16d616466f5d6
                  3987615923e282a6eccbb4f93d335a00bc0f25a3065f924b83ff93ee424a
                  e9616315fbee21ceb43c3e519fbd5d7ff4aabf245dc767d68d6ca3cef35f
                  a58f4875ea2e2142a1593c8bf974f186883855cab4329a2e78f9bd957391
                  1363f134d8d192b3b546eb6d890f7102a37e330d8a26dfa83f773020828a
                  0fab348a04f3d757016feeda92881d8d9bf991776691b5cda9e92a49c20f
                  fe2470f3496ff345d2e052ce422ce9404dcec1ded8d9e458dca8b274a115
                  1625769961dbdb32bfa7bceab785ece5c6277272d5b7b747cb8b265df811
                  0e9c7b68af8bc500f05f123a0b57d033b3094496e1b3f97d60a235001101
                  0001b41f5368756d6f6e204875717565203c736875717565407570656e6e
                  2e6564753e8901380413010200220502534f0f26021b03060b0908070302
                  06150802090a0b0416020301021e01021780000a09107b5cc91ed5fd4336
                  21d607ff5ed98243335233728a3d52e600c3c4201b2130d0026f5b0aaaef
                  b2cbc3d66eeeddcd396669b4e5c88c9cf68e44418843aa05a5840fd85fa9
                  0de541326ccb88b124c3dc95bb5f21bab83872706faba6c82fb2b8dcc139
                  8565eedf51ba1ef62c68ca4e9d2c6dd6f9ad0e9823f54c8dfca1411f3ce5
                  718daa25b23dd150ae6f380142e535e3e353d992d839e746056954a71d64
                  4521c438290c79b50a665f08ede6ceff6fe1e0b5589cb0e358c6da52b827
                  84b8bcc6a62afef9ac582a52900dd66594e56a20a4eed0f099d475609a09
                  8b16b8db1909e7c082d9861ed72178fb95cae9d1953f63cbebf5cf7d2de9
                  15fd85397392afd5954b2bc1265071523a73d167b41f5368756d6f6e2048
                  75717565203c7368757175654068757175652e636f6d3e89013804130102
                  00220502534f0ce9021b03060b090807030206150802090a0b0416020301
                  021e01021780000a09107b5cc91ed5fd4336e1b908009f5aeb44e5f7a03d
                  e46e28c3a95e34fc146e90783c57ce04f5da10fb50b2e83b34e6de692e5c
                  bacac0aa5851b5963b4c4ed0a984b36f2281e2d1e46930d10cf8e4f397c1
                  f67bc77450efe36b3b3b6668b3e30530e50137adba123a7c5a65811cf730
                  bdd1516fa0a9e1cd75b7153b4a1025bd027ab877dfe7bba01b1625a046da
                  5482cc5398a9ae4ec6b5d5c95a48168cb3af2c7afe7c6d9ce7d918088ffc
                  78ca320e9e40086007454295ebccb266ba4604544240c677443155a4635d
                  cf264a1dcbe010cc25a59a08808eadf48405306f2246a1a1feac7c2d878d
                  142f73d80d3edbc483a6ab41e7f1c03bf4162448bd889491b7e27648d4d4
                  d2623caf1524137db41f5368756d6f6e204875717565203c736875717565
                  40676d61696c2e636f6d3e8901380413010200220502534f0f08021b0306
                  0b090807030206150802090a0b0416020301021e01021780000a09107b5c
                  c91ed5fd433608660800af4017dc04bc44a465725f21049fef70378f3c04
                  6235d57562bd0678ab610397e80ca739fe6eb8340b977d3977c100cfb6c1
                  fe2305dbcc2c7317b4d350325fb17e769ac5db0a41c4f0cb21505f1ae5cf
                  e0943facda8838b73ca649d3e608f38e9ee67fbb4e6de511162efb1279a6
                  ed46e793f8ed70d49b3efca15503422dc2fcb2efb83899c62fd3e055e629
                  615be4631eaefce02ddc11a570bde84b063d12ec6f40a8e2752b58f31627
                  3e9b0bbac058830b208df0b0e09e473a35748f492f24c5ca1070a929661f
                  6261bf2dfba49f2399f41eb0edb9e0def0dc575d60715670b0b8af2dc788
                  afe2cc7434fcc0946277290084fc4a1c712a3692e483a7c75f19b4225368
                  756d6f6e204875717565203c73687571756540766572697369676e2e636f
                  6d3e8901380413010200220502534f1112021b03060b0908070302061508
                  02090a0b0416020301021e01021780000a09107b5cc91ed5fd4336e81a07
                  fe20b7381a137d5d3601387a473f821f8c672aafaa3af4eb4c3b679c9219
                  2d9bb7d9422db49afe6e6bdb9c407d3a802b42590042b6423f4d415e851b
                  f4407658ade0929eb48aea6d75e91b2dcb38a44fb292a6c6bd49ce1196b8
                  4575520d0ada710b01e9d72a94e390a2b95816ea132a1c109df22cabef0f
                  73a59ff6be8bbec0016a6a48ae5de2fefbffba00c5a36b6075828d328cf4
                  6fef86caf6389c5a93c9edf7f5eb137742de24e1d7581b94a77bfd8782ea
                  bc7bce3e659bc33702c8e3ea035f72b2f7e158c8399b4e25a611407a9718
                  81fe9f1e1d99129f72fdec28ff95a447aae9a08dbd56d21e9c88a9f1b069
                  8ed1cb3021b22f8bb07fd3283c4b6249beb9010d04534f0ce9010800e5e3
                  500b48ed9a46074fa44fd56bfe4c2830d52f09cd6ecb3f329fa8c0d57a48
                  2e1ee6731e95fb3cc1f86a42e7e88e1e5d868050250fcf5f07a504c80843
                  d2eb450c351ac04064cd4fee8fac82cdee455587c391af715fd19f29198b
                  56e0ee8c5f7a56c505cdcd2d224cc188757296bd96b3363e32fb5f244111
                  52274693b9949cd1ee658ad174c335b05f0f9f7d6edb30717b581bde4811
                  30954e14db9ced4218b7c41552795a34127ad0da0d5d090c805761b56f58
                  18366c4c7889ab962b2152b32ac31fb76294594378d5570a448c3f4930fe
                  e669c8199c08592a4e54fbefba390e9523bb0271e8ca5e6641b8693b847b
                  e81ad41e7824e7726ec4a138bbd7001101000189011f0418010200090502
                  534f0ce9021b0c000a09107b5cc91ed5fd4336d6c007fe2175a87b579a13
                  25dc5b6594311876879daad105198694996139b6690482909cdc6bf1fea6
                  860a32e9a8ef79633f45f8943717b1fa1490b214034e13cb2a2d8a364a74
                  8228c1d9130afb48b88a43112f6e06a85ffc0117a5d4ab1ab2d27d6784d2
                  f540488783157a0e3878cb0ccaf070562dbc05c80c1e7ae15ca24833cc58
                  8ee5c861c9e1fc5b0f62d9f83509912c2a377073c6f000384012c65e195f
                  37c3de7d4e1ac235ff8a0f8a5c9881b5a6322b1290a7b8ca64372320225d
                  c05ae08b4f4be87e29913e022c933f38171407e2659013f1c937a55e176e
                  2480d1c44cb580b9508a3955059c5ebdde1b39abca48bddbf0bed08ad7b0
                  2ac55d8a9b62161c2b
)
```
