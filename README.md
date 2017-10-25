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
$ .gpg2openpgpkey.py shuque@huque.com /tmp/key1.asc
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

