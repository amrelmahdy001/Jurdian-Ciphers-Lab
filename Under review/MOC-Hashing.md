---
type: moc
title: "MOC — Hashing"
aliases:
  - "Hash Functions Index"
  - "Cryptographic Hash Index"
tags:
  - moc
  - hash
created: 2025-01-01
updated: 2025-06-28
---

# Hashing — Index

> **Definition:** A hash function takes arbitrary-length input and produces a fixed-length output (digest). Hash functions are one-way: you cannot recover the input from the digest.
> ← Back to [[MOC-Master]]

---

## Critical Distinction: Hash ≠ Cipher

| Property | Cipher | Hash Function |
|---|---|---|
| Reversible? | Yes (with key) | No |
| Key required? | Usually | No |
| Fixed output length? | No | Yes |
| Purpose | Confidentiality | Integrity / Identity |
| Example | [[AES Cipher]] | [[SHA-256 Hash]] |

---

## Sub-Categories

### Cryptographic Hash Functions
> Designed for security: collision resistance, preimage resistance, second-preimage resistance.

- [[BLAKE2 Hash]] — Fast, secure; used in password hashing and file integrity
- [[BLAKE3 Hash]] — BLAKE2 successor; even faster; parallelizable
- [[MD4 Hash]] — Broken; historical only
- [[MD5 Hash]] — Broken; collision attacks possible in seconds; do not use for security
- [[SHA-1 Hash]] — Deprecated; collision demonstrated 2017
- [[SHA-224 Hash]] — SHA-2 family; truncated SHA-256
- [[SHA-256 Hash]] — SHA-2 family; 256-bit output; widely used; currently secure
- [[SHA-384 Hash]] — SHA-2 family; truncated SHA-512
- [[SHA-512 Hash]] — SHA-2 family; 512-bit output; higher security margin
- [[SHA3-256 Hash]] — SHA-3 family; Keccak-based; different design from SHA-2

### Password Hashing & Key Derivation Functions
> Intentionally slow to resist brute force; include salt to prevent rainbow table attacks.

- [[Argon2 Hash]] — Winner of Password Hashing Competition 2015; recommended
- [[bcrypt Hash]] — Widely used; adaptive cost factor
- [[Crypt Function]] — Unix password hashing; various underlying algorithms
- [[NTLM Hash]] — Windows legacy; no salt; vulnerable to pass-the-hash attacks
- [[PBKDF2 Hash]] — PKCS#5 standard; HMAC-based; adjustable iterations
- [[scrypt Hash]] — Memory-hard; resistant to GPU attacks

### Checksums & Non-Cryptographic Hashes
> Fast; detect accidental corruption; not designed to resist deliberate manipulation.

- [[CRC-32]] — Cyclic redundancy check; 32-bit; used in ZIP, Ethernet
- [[Hamming Code]] — Error detection and correction; not a hash
- [[Luhn Algorithm]] — Credit card number validation
- [[Verhoeff Algorithm]] — Digit error detection; catches all single-digit errors and transpositions

---

## Security Status

| Hash | Output | Status | Broken Since |
|---|---|---|---|
| [[MD4 Hash]] | 128-bit | Broken | 1995 |
| [[MD5 Hash]] | 128-bit | Broken | 2004 (collision) |
| [[SHA-1 Hash]] | 160-bit | Deprecated | 2017 (SHAttered) |
| [[SHA-256 Hash]] | 256-bit | Secure | — |
| [[SHA-512 Hash]] | 512-bit | Secure | — |
| [[SHA3-256 Hash]] | 256-bit | Secure | — |
| [[BLAKE3 Hash]] | 256-bit | Secure | — |

---

## Hash Identification

Given an unknown hash string, use [[Tool - Hash Identifier]] or consult [[Cipher Identifier Quick Reference]].

Common hash lengths:
- 32 hex chars (128-bit) → MD5 or MD4
- 40 hex chars (160-bit) → SHA-1
- 56 hex chars (224-bit) → SHA-224
- 64 hex chars (256-bit) → SHA-256 or BLAKE2s
- 96 hex chars (384-bit) → SHA-384
- 128 hex chars (512-bit) → SHA-512 or BLAKE2b

---

## Interactive Tools

- [[Tool - Hash Generator]] — Generate hashes for any input
- [[Tool - Hash Identifier]] — Identify unknown hash strings
- [[Tool - Hash Lookup]] — Attempt reverse lookup via rainbow tables
