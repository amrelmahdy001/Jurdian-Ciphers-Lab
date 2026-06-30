---
type: moc
title: "MOC — Cryptanalysis"
aliases:
  - "Cryptanalysis Index"
  - "Attack Methods"
  - "Cipher Breaking"
tags:
  - moc
  - analysis
  - cryptanalysis
created: 2025-01-01
updated: 2025-06-28
---

# Cryptanalysis — Index

> **Definition:** Cryptanalysis is the study of breaking cryptographic systems — recovering plaintext or keys without prior knowledge of the key.
> ← Back to [[MOC-Analysis]]

---

## Attack Classification by Adversary Access

| Attack Class | What the Adversary Has | Difficulty |
|---|---|---|
| [[Ciphertext-Only Attack]] | Only ciphertext | Hardest for adversary |
| [[Known-Plaintext Attack]] | Some plaintext + ciphertext pairs | Moderate |
| [[Chosen-Plaintext Attack]] | Can choose plaintext and see resulting ciphertext | Easier for adversary |
| [[Chosen-Ciphertext Attack]] | Can choose ciphertext and see resulting plaintext | Very easy for adversary |

Most classical cipher breaks are ciphertext-only. Many modern cipher breaks require chosen-plaintext conditions.

---

## Attack Types by Technique

### Statistical Attacks
- [[Frequency Analysis]] — Count letter frequencies; attack monoalphabetic ciphers
- [[Bigrams Analysis]] — Count letter pair frequencies; attack polygraphic ciphers
- [[Trigrams Analysis]] — Count letter triple frequencies
- [[Index of Coincidence]] — Distinguish mono- from polyalphabetic; estimate key length
- [[Kasiski Test]] — Find repeated ciphertext segments to determine Vigenère key length
- [[Shannon Entropy Index]] — Measure information density of ciphertext

### Mathematical Attacks
- [[Brute Force Attack]] — Exhaustive key search; feasible for short keys
- [[Birthday Attack]] — Exploits collision probability in hash functions
- [[Meet-in-the-Middle Attack]] — Attacks double-encryption schemes (e.g., 2DES)
- [[Modular Arithmetic Attack]] — Attacks affine and multiplicative ciphers
- [[Linear Cryptanalysis]] — Statistical attack on block ciphers; find linear approximations
- [[Differential Cryptanalysis]] — Exploits how differences in input affect output

### Structural Attacks
- [[Known-Plaintext Attack]] — Recover key from plaintext/ciphertext pairs
- [[Chosen-Plaintext Attack]] — Select specific plaintexts to maximize information gain
- [[Sliding Attack]] — Exploits self-similarity in cipher round structure

### Side-Channel Attacks
> Attacks on the *implementation*, not the algorithm.
- [[Timing Attack]] — Measure time to perform operations; infer key bits
- [[Power Analysis Attack]] — Measure power consumption during encryption
- [[Electromagnetic Attack]] — Detect EM emissions from encryption hardware
- [[Cache Timing Attack]] — Exploit CPU cache access patterns

### Padding & Protocol Attacks
- [[Padding Oracle Attack]] — Exploit padding validation errors to decrypt without key (CBC mode)
- [[BEAST Attack]] — Against TLS 1.0 CBC mode
- [[CRIME Attack]] — Exploit TLS compression
- [[Lucky Thirteen Attack]] — Timing-based CBC padding oracle

---

## Attacks by Target Cipher Family

| Cipher Family | Primary Attacks |
|---|---|
| Shift / Monoalphabetic | [[Brute Force Attack]], [[Frequency Analysis]] |
| Polyalphabetic | [[Kasiski Test]], [[Index of Coincidence]] + [[Frequency Analysis]] |
| Transposition | Anagramming, columnar pattern detection |
| Block Ciphers | [[Differential Cryptanalysis]], [[Linear Cryptanalysis]], [[Meet-in-the-Middle Attack]] |
| Hash Functions | [[Birthday Attack]], preimage attack |
| RSA | Integer factorization (no efficient classical algorithm known) |

---

## Interactive Tools

- [[Tool - Frequency Analysis]]
- [[Tool - Index of Coincidence]]
- [[Tool - Kasiski Test]]
- [[Tool - Cipher Identifier]]
