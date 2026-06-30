---
type: moc
title: "MOC — Monoalphabetic Ciphers"
aliases:
  - "Monoalphabetic Substitution Index"
  - "Simple Substitution Ciphers"
tags:
  - moc
  - cipher
  - classical
  - substitution
  - monoalphabetic
created: 2025-01-01
updated: 2025-06-28
---

# Monoalphabetic Ciphers — Index

> **Definition:** A monoalphabetic cipher uses a single fixed substitution alphabet throughout the entire message. Each plaintext letter always maps to the same ciphertext letter.
> ← Back to [[MOC-Substitution-Ciphers]]

---

## Core Property & Weakness

Because the mapping is fixed, **letter frequencies in the ciphertext mirror those in the plaintext language**. In English, `E` appears ~12.7% of the time — the most frequent ciphertext letter will also appear ~12.7% of the time, pointing directly to `E`.

This means every monoalphabetic cipher is **broken by [[Frequency Analysis]]** given sufficient ciphertext (~100+ characters).

The theoretical key space (26! ≈ 4 × 10²⁶) is enormous, but irrelevant when frequency statistics bypass brute force entirely.

---

## Ciphers in This Family

### General Substitution
- [[Atbash Cipher]] — Reverse alphabet; A↔Z, B↔Y; no key; ancient Hebrew origin
- [[Monoalphabetic Substitution Cipher]] — General form; any permutation of A–Z as the key alphabet
- [[Null Cipher]] — Message hidden within innocent-looking plaintext by selection rules
- [[Running Key Cipher]] — Key is a long text passage; approaches one-time pad territory

### Mathematical Substitution
- [[Affine Cipher]] — `C = (aP + b) mod 26`; generalisation of shift and multiplicative
- [[Modulo Cipher]] — Substitution driven by modular arithmetic
- [[Multiplicative Cipher]] — `C = (aP) mod 26`; special case of Affine with `b = 0`
- [[Prime Numbers Cipher]] — Substitution table derived from prime number sequences
- [[Prime Multiplication Cipher]] — Letter values multiplied by primes

### Keyword-Based Substitution
- [[Bacon Cipher]] — Binary encoding of letters using two symbols (A and B); steganographic variant
- [[Book Cipher]] — Plaintext letters encoded as references to positions in a shared book
- [[Consonants-Vowels Rank Cipher]] — Consonants and vowels ranked separately as substitution key
- [[D3 Code]] — Keyword-derived substitution alphabet
- [[K6 Code]] — Numbered keyword substitution variant
- [[K7 Code]] — Numbered keyword substitution variant
- [[Keyword Shift Cipher]] — Keyword placed at start of alphabet before completing it
- [[Malespin]] — Nicaraguan folk cipher; swaps pairs of letters (a↔e, i↔o, etc.)
- [[Periodic Table Cipher]] — Atomic symbols and numbers as substitution alphabet
- [[Rozier Cipher]] — Historical keyword-based cipher
- [[Triliteral Cipher]] — Three-symbol encoding scheme
- [[Wolseley Cipher]] — Military cipher using keyword-derived mixed alphabet

---

## Key Properties Comparison

| Cipher | Key Type | Key Space | Self-Inverse? | Notable Feature |
|---|---|---|---|---|
| [[Atbash Cipher]] | None | 1 | Yes | No key needed |
| [[Caesar Cipher]] | Shift (0–25) | 25 | Only ROT-13 | Subset of monoalphabetic |
| [[Affine Cipher]] | Two integers (a,b) | 312 | Varies | Math-based |
| [[Multiplicative Cipher]] | One integer (a) | 11 | Varies | Affine with b=0 |
| [[Monoalphabetic Substitution Cipher]] | Permuted alphabet | 26! | Rarely | Maximum key space |
| [[Keyword Shift Cipher]] | Keyword | Varies | No | Easy to remember |
| [[Book Cipher]] | Shared book + position | Very large | No | Depends on shared key |

---

## Cryptanalysis

All ciphers in this family are broken by:

1. **[[Frequency Analysis]]** — map ciphertext frequencies to English letter frequencies
2. **Pattern analysis** — identify words with repeated letters (e.g., `ABBA` pattern = likely `THAT` or `NOON`)
3. **Digraph/trigraph analysis** — [[Bigrams Analysis]], [[Trigrams Analysis]]
4. **Word guessing (cribs)** — if any word is guessed, it unlocks others

**Required ciphertext length for reliable attack:** ~100 characters minimum; ~300 for high confidence.

---

## Interactive Tools

- [[Tool - Monoalphabetic Substitution]] — Full alphabet mapping tool
- [[Tool - Affine Cipher]] — Encrypt/decrypt with mathematical key
- [[Tool - Atbash Cipher]] — One-click Atbash conversion
- [[Tool - Frequency Analysis]] — Analyse ciphertext letter frequencies

---

## All Monoalphabetic Ciphers

```dataview
TABLE difficulty, year_invented, broken
FROM "docs/ciphers/classical/substitution/monoalphabetic"
WHERE type = "cipher"
SORT title ASC
```
