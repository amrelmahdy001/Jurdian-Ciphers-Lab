---
type: moc
title: "MOC — Statistical Analysis"
aliases:
  - "Statistical Analysis Index"
  - "Frequency Analysis Index"
tags:
  - moc
  - analysis
  - statistical
created: 2025-01-01
updated: 2025-06-28
---

# Statistical Analysis — Index

> **Definition:** Statistical analysis applies mathematical techniques to ciphertext to extract information about the plaintext language, the cipher type, or the key — without the key.
> ← Back to [[MOC-Analysis]]

---

## Core Statistical Tools

### Frequency Methods
- [[Frequency Analysis]] — Count individual letter occurrences; compare to expected English frequencies
- [[Bigrams Analysis]] — Count digraph (letter pair) frequencies; `TH`, `HE`, `IN`, `ER` most common in English
- [[Trigrams Analysis]] — Count trigraph frequencies; `THE`, `AND`, `ING` most common
- [[Contact Analysis]] — Study which symbols appear adjacent to which others

### Information-Theoretic Methods
- [[Index of Coincidence]] — Probability that two randomly chosen letters from a text are the same; IC ≈ 0.065 for English monoalphabetic, ≈ 0.038 for random/polyalphabetic
- [[Shannon Entropy Index]] — Measure of information content per character; low entropy = structure = crackable
- [[Mutual Information]] — Correlation between plaintext and ciphertext characters

### Key-Length Analysis
- [[Kasiski Test]] — Find distances between repeated ciphertext sequences; GCD of distances = likely key length
- [[Friedman Test]] — Use IC values at different period guesses to find Vigenère key length
- [[Autocorrelation Analysis]] — Measure self-similarity at different offsets to detect periodicity

---

## English Language Reference Statistics

> Essential reference for frequency analysis attacks.

### Single Letter Frequencies (English)
| Rank | Letter | Frequency |
|---|---|---|
| 1 | E | 12.70% |
| 2 | T | 9.06% |
| 3 | A | 8.17% |
| 4 | O | 7.51% |
| 5 | I | 6.97% |
| 6 | N | 6.75% |
| 7 | S | 6.33% |
| 8 | H | 6.09% |
| 9 | R | 5.99% |
| 10 | D | 4.25% |

Most frequent: **ETAOIN SHRDLU** (mnemonic for top 12)

### Common Digraphs
`TH · HE · IN · ER · AN · RE · ON · EN · AT · ND · ST · ES`

### Common Trigraphs
`THE · AND · ING · ION · ENT · FOR · OFT · STH · ERE`

### Index of Coincidence by Language
| Language | IC |
|---|---|
| English | 0.0665 |
| French | 0.0778 |
| German | 0.0762 |
| Random | 0.0385 |

---

## Interactive Tools

- [[Tool - Frequency Analysis]]
- [[Tool - Index of Coincidence]]
- [[Tool - Kasiski Test]]
- [[Tool - Text Statistics]]
