---
type: moc
title: "MOC — Modern Ciphers"
aliases:
  - "Modern Cryptography Ciphers Index"
  - "Computational Ciphers"
tags:
  - moc
  - cipher
  - modern
created: 2025-01-01
updated: 2025-06-28
---

# Modern Ciphers — Index

> **Definition:** Modern ciphers are designed for computer implementation and are evaluated against computational adversaries. Security is defined in terms of computational hardness, not mathematical elegance.
> ← Back to [[MOC-Ciphers]]

---

## Sub-Indexes

- [[MOC-Block-Ciphers]] — Fixed-size block encryption (AES, DES, Blowfish)
- [[MOC-Stream-Ciphers]] — Bit-by-bit or byte-by-byte encryption (RC4, Vernam, XOR)

---

## Public-Key Cryptography

> Public-key (asymmetric) algorithms are not ciphers in the classical sense — they are cryptographic systems.
> See: [[MOC-Cryptography]] → Public-Key Systems

- [[RSA Algorithm]] — Factoring hardness; Rivest–Shamir–Adleman, 1977
- [[Diffie-Hellman Key Exchange]] — Discrete log problem; key exchange, not encryption
- [[Elliptic Curve Cryptography]] — Discrete log on elliptic curves; smaller keys, same security

---

## Key Concepts Unique to Modern Ciphers

- **[[Confusion and Diffusion]]** — Shannon's two design principles for strong ciphers
- **[[Block Cipher Modes of Operation]]** — ECB, CBC, CTR, GCM — how block ciphers handle variable-length data
- **[[Key Schedule]]** — How the master key is expanded into round keys
- **[[Avalanche Effect]]** — Small input change → large output change; desirable property
- **[[Semantic Security]]** — Formal definition of "unbreakable" for computational adversaries
- **[[Perfect Forward Secrecy]]** — Session keys independent of long-term keys

---

## Security Status Overview

| Cipher | Type | Key Size | Status |
|---|---|---|---|
| [[DES Cipher]] | Block | 56-bit | Broken (1999) |
| [[3DES Cipher]] | Block | 112/168-bit | Deprecated (2023) |
| [[AES Cipher]] | Block | 128/192/256-bit | Secure |
| [[Blowfish Cipher]] | Block | 32–448-bit | Secure (limited use) |
| [[RC4 Cipher]] | Stream | 40–2048-bit | Broken (2015) |
| [[Vernam Cipher]] | Stream | = message length | Theoretically unbreakable |
| [[XOR Cipher]] | Stream | Any | Insecure alone |

---

## All Modern Ciphers

```dataview
TABLE subcategory, key_length, broken
FROM "docs/ciphers/modern"
WHERE type = "cipher"
SORT title ASC
```
