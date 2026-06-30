---
type: moc
title: "MOC — Stream Ciphers"
aliases:
  - "Stream Cipher Index"
tags:
  - moc
  - cipher
  - modern
  - stream-cipher
created: 2025-01-01
updated: 2025-06-28
---

# Stream Ciphers — Index

> **Definition:** A stream cipher encrypts data one bit or byte at a time by XORing the plaintext with a pseudorandom keystream. Unlike block ciphers, they do not require padding.
> ← Back to [[MOC-Modern-Ciphers]]

---

## How Stream Ciphers Work

1. A **key** (and usually an **IV/nonce**) seeds a pseudorandom number generator
2. The generator produces a **keystream** — a sequence of seemingly random bits
3. Each plaintext bit is XORed with the corresponding keystream bit: `C = P ⊕ K`
4. Decryption is identical: `P = C ⊕ K` (XOR is self-inverse)

**Critical rule:** A keystream must **never be reused** with a different message. Reusing a keystream allows trivial recovery of the XOR of two plaintexts.

---

## Ciphers in This Family

### Modern Stream Ciphers
- [[RC4 Cipher]] — Ron Rivest, 1987; byte-oriented; used in WEP and early TLS; cryptographically broken

### Historical / Theoretical
- [[Vernam Cipher]] — Gilbert Vernam, 1917; XOR with a truly random key = one-time pad; proven theoretically unbreakable by Shannon
- [[XOR Cipher]] — Trivial stream cipher; only secure when keystream is truly random and never reused

### Related Concepts
- [[Linear Feedback Shift Register]] — Common building block for keystream generators
- [[One-Time Pad]] — Theoretical perfect cipher; Vernam's contribution
- [[Nonce and IV]] — Initialization vectors for stream ciphers

---

## All Stream Ciphers

```dataview
TABLE key_length, broken, year_invented
FROM "docs/ciphers/modern/stream"
WHERE type = "cipher"
SORT title ASC
```
