---
type: moc
title: "MOC — Substitution Ciphers"
aliases:
  - "Substitution Ciphers Index"
tags:
  - moc
  - cipher
  - classical
  - substitution
created: 2025-01-01
updated: 2025-06-28
---

# Substitution Ciphers — Index

> **Definition:** A substitution cipher replaces each plaintext symbol with another symbol according to a fixed or variable mapping rule.
> ← Back to [[MOC-Classical-Ciphers]]

---

## What Is Substitution?

Substitution ciphers operate on the **identity** of letters, not their position. Every plaintext letter (or group of letters) is swapped with a ciphertext symbol from a predefined alphabet or table.

Substitution is the oldest and most fundamental operation in cryptography. All substitution ciphers are vulnerable to some form of [[Frequency Analysis]] unless the key space is large enough to prevent it.

**Contrast with transposition:** [[MOC-Transposition-Ciphers]] — transposition rearranges letters without changing them.

---

## Sub-Families

| Sub-Index | Core Idea | Broken By |
|---|---|---|
| [[MOC-Monoalphabetic]] | One cipher alphabet; letters map one-to-one | Frequency analysis |
| [[MOC-Polyalphabetic]] | Multiple cipher alphabets; mapping shifts with key | Kasiski test, IC analysis |
| [[MOC-Homophonic-Ciphers]] | Multiple ciphertext symbols per plaintext letter | Extended frequency analysis |
| [[MOC-Polygraphic-Ciphers]] | Groups of letters substituted together | Digraph/trigraph analysis |
| [[MOC-Symbolic-Ciphers]] | Symbols or glyphs replace letters | Visual pattern matching |

---

## Decision Tree — Which Sub-Family?

```
Does the cipher use exactly one substitute per plaintext letter?
├── Yes → Is the mapping fixed (same key position always maps same way)?
│   ├── Yes → Is the key one shift amount?
│   │   ├── Yes → Shift Cipher (→ [[MOC-Shift-Ciphers]])
│   │   └── No  → Monoalphabetic (→ [[MOC-Monoalphabetic]])
│   └── No (mapping changes based on key position)
│       → Polyalphabetic (→ [[MOC-Polyalphabetic]])
├── No → Can multiple ciphertext symbols represent one plaintext letter?
│   ├── Yes → Homophonic (→ [[MOC-Homophonic-Ciphers]])
│   └── No → Are groups of letters substituted together?
│       ├── Yes → Polygraphic (→ [[MOC-Polygraphic-Ciphers]])
│       └── No → Are symbols/glyphs used?
│           └── Yes → Symbolic (→ [[MOC-Symbolic-Ciphers]])
```

---

## Key Concepts

- [[Frequency Analysis]] — primary attack on monoalphabetic ciphers
- [[Index of Coincidence]] — distinguishes monoalphabetic from polyalphabetic
- [[Kasiski Test]] — determines key length for polyalphabetic ciphers
- [[Bigrams Analysis]] — extends frequency analysis to letter pairs
- [[Polybius Cipher]] — foundational grid used in many substitution systems

---

## Related

- [[MOC-Shift-Ciphers]] — Shift ciphers are a special case of monoalphabetic substitution
- [[MOC-Fractionation-Ciphers]] — Fractionation applies substitution then transposition
- [[MOC-Transposition-Ciphers]] — The complementary operation to substitution
