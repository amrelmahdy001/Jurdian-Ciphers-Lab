---
type: moc
title: "MOC — Block Ciphers"
aliases:
  - "Block Cipher Index"
tags:
  - moc
  - cipher
  - modern
  - block-cipher
created: 2025-01-01
updated: 2025-06-28
---

# Block Ciphers — Index

> **Definition:** A block cipher encrypts plaintext in fixed-size chunks (blocks). A 128-bit block cipher encrypts exactly 128 bits at a time, regardless of message length (with padding as needed).
> ← Back to [[MOC-Modern-Ciphers]]

---

## How Block Ciphers Work

Block ciphers are constructed from repeated application of a **round function**:
1. A round function applies key-mixing, substitution (S-boxes), and permutation to one block
2. This is repeated for a fixed number of rounds (AES: 10/12/14, DES: 16)
3. The key is expanded into round keys via a **key schedule**
4. The final output after all rounds is the ciphertext block

The security of a block cipher rests on two principles ([[Confusion and Diffusion]]):
- **Confusion:** Each ciphertext bit depends on many key bits (via S-boxes)
- **Diffusion:** Each plaintext bit influences many ciphertext bits (via permutation)

---

## Block Cipher Modes of Operation

Block ciphers alone encrypt exactly one block. To handle arbitrary-length messages:

| Mode | Name | Properties |
|---|---|---|
| ECB | Electronic Codebook | Insecure; identical blocks → identical ciphertext |
| CBC | Cipher Block Chaining | Blocks chained; needs IV; sequential only |
| CTR | Counter Mode | Turns block cipher into stream cipher; parallelizable |
| GCM | Galois/Counter Mode | CTR + authentication tag; provides AEAD |
| CFB | Cipher Feedback | Stream-like; self-synchronising |
| OFB | Output Feedback | Stream-like; errors don't propagate |

See: [[Block Cipher Modes of Operation]]

---

## Ciphers in This Family

### Currently Secure
- [[AES Cipher]] — Advanced Encryption Standard; NIST 2001; 128/192/256-bit keys; Rijndael algorithm; gold standard
- [[Blowfish Cipher]] — Bruce Schneier, 1993; 32–448-bit keys; no known weaknesses; superseded by Twofish

### Deprecated / Broken
- [[DES Cipher]] — Data Encryption Standard; NIST 1977; 56-bit key; broken by brute force 1999; historical

### Related Concepts
- [[Block Cipher Modes of Operation]]
- [[Key Schedule]]
- [[S-Box (Substitution Box)]]
- [[Feistel Network]]
- [[Confusion and Diffusion]]

---

## All Block Ciphers

```dataview
TABLE key_length, broken, year_invented
FROM "docs/ciphers/modern/block"
WHERE type = "cipher"
SORT title ASC
```
