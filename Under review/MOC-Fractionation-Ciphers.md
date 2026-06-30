---
type: moc
title: "MOC — Fractionation Ciphers"
aliases:
  - "Fractionation Ciphers Index"
  - "Bifid Family"
tags:
  - moc
  - cipher
  - classical
  - fractionation
created: 2025-01-01
updated: 2025-06-28
---

# Fractionation Ciphers — Index

> **Definition:** A fractionation cipher splits each plaintext letter into smaller components (fractions), then recombines and permutes those components before encoding the final ciphertext. The result combines substitution and transposition in a single operation.
> ← Back to [[MOC-Classical-Ciphers]]

---

## Core Concept

Fractionation is the most sophisticated classical cipher technique. The process:

1. **Substitute** — Convert each letter to a coordinate representation (usually via a Polybius square)
2. **Fractionate** — Separate the coordinates (row, column) and treat each digit as an independent element
3. **Permute** — Rearrange these fractional elements (transposition step)
4. **Re-combine** — Pair the permuted fractions back into coordinate pairs
5. **Encode** — Convert coordinate pairs back to letters

This interleaving of substitution and transposition gives fractionation ciphers **dramatically more security** than either operation alone. They were considered state-of-the-art for hand ciphers in the early 20th century.

All fractionation ciphers were invented by Felix Delastelle (1840–1902), except the ADFGVX which was adapted by Fritz Nebel.

---

## Ciphers in This Family

### Delastelle's Ciphers
- [[Bifid Cipher]] — Letters → Polybius coordinates → coordinates separated → transposed → new letter pairs; 2D
- [[Trifid Cipher]] — Extension of Bifid to a 3×3×3 cube; operates on triples of coordinates
- [[Four-Square Cipher]] — Uses four 5×5 Polybius squares; digraphic *(also in [[MOC-Polygraphic-Ciphers]])*

### WWI Military Applications
- [[ADFGX Cipher]] — German WWI cipher; 5×5 Polybius square + columnar transposition; 1918
- [[ADFGVX Cipher]] — Upgraded ADFGX; 6×6 grid adding digits; also 1918; broken by Georges Painvin

### Morse-Based Fractionation
- [[Fractionated Morse Cipher]] — Morse representations treated as fractions; then substituted via a keyed alphabet
- [[Monome-Dinome Cipher]] — Straddling checkerboard + transposition; compact and powerful

### Complex Hybrid
- [[Digrafid Cipher]] — Combines digraphic substitution with fractionation

---

## Classification Note

Ciphers like [[Bifid Cipher]] and [[Trifid Cipher]] could also be classified as polygraphic (since they output multiple ciphertext letters from multiple plaintext letters). They are placed here because **fractionation is their defining operation** — the mechanism that makes them cryptographically significant is the splitting and permuting of coordinates, not merely multi-letter substitution.

The [[ADFGVX Cipher]] is also a fractionation cipher despite additionally incorporating columnar transposition as a second layer.

---

## Cryptanalysis

Fractionation ciphers are significantly harder to break than simple substitution or transposition:

- **[[Bifid Cipher]]** — Vulnerable to probabilistic decryption with long ciphertext (~100+ letters); susceptible to simulated annealing attacks
- **[[Trifid Cipher]]** — Harder than Bifid; very long ciphertext required
- **[[ADFGVX Cipher]]** — Georges Painvin broke it in 1918 using the fact that the transposition key created repeated patterns when two messages shared the same key

**Modern attacks:** Hill-climbing and simulated annealing algorithms on modern hardware break most fractionation ciphers given sufficient ciphertext.

---

## Interactive Tools

- [[Tool - Bifid Cipher]]
- [[Tool - Trifid Cipher]]
- [[Tool - ADFGVX Cipher]]
- [[Tool - Fractionated Morse Cipher]]

---

## All Fractionation Ciphers

```dataview
TABLE difficulty, year_invented, inventor
FROM "docs/ciphers/classical/fractionation"
WHERE type = "cipher"
SORT title ASC
```
