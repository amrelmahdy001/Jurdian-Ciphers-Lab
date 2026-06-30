---
type: moc
title: "MOC — Polygraphic Ciphers"
aliases:
  - "Polygraphic Ciphers Index"
  - "Digraphic Ciphers"
  - "Multi-letter Substitution"
tags:
  - moc
  - cipher
  - classical
  - substitution
  - polygraphic
created: 2025-01-01
updated: 2025-06-28
---

# Polygraphic Ciphers — Index

> **Definition:** A polygraphic cipher substitutes groups of plaintext letters (digraphs, trigraphs) with groups of ciphertext letters. Each letter's encryption depends on its neighbors, not just its own identity.
> ← Back to [[MOC-Substitution-Ciphers]]

---

## Core Concept

Standard substitution ciphers encrypt one letter at a time, making them vulnerable to single-letter frequency analysis. Polygraphic ciphers encrypt **pairs (digraphs) or triples (trigraphs) of letters** together.

This has two effects:
1. Single-letter frequency analysis is defeated
2. Digraph frequency analysis applies instead — but the statistics are far flatter and require much more ciphertext to be useful

The [[Polybius Cipher]] is the foundational grid that most polygraphic ciphers derive from. It converts letters to coordinate pairs, which can then be processed in various ways.

---

## Ciphers in This Family

### Digraphic (Pairs of Letters)
- [[Playfair Cipher]] — 5×5 keyword grid; encrypts letter pairs using geometric rules; Charles Wheatstone, 1854
- [[Four-Square Cipher]] — Uses four 5×5 Polybius squares; digraphic; Felix Delastelle, 1902
- [[Two-Square Cipher]] — Uses two Polybius squares; simpler than Four-Square
- [[Collon Cipher]] — Digraphic cipher using grid coordinates

### Trigraphic (Triples of Letters)
- [[Three-Square Cipher]] — Extension of Two-Square/Four-Square to trigraphs

### Coordinate-Based Substitution
- [[Polybius Cipher]] — Foundation cipher; letters become grid coordinates (row, column)
- [[Tap Code Cipher]] — Polybius derivative; used by prisoners of war via tapping sounds

### Morse-Based Polygraphic
- [[Morbit Cipher]] — Morse code representation + numeric key; each Morse symbol pair → digit
- [[Pollux Cipher]] — Morse code representation; each Morse dot/dash/space → digit homophones

### Matrix-Based
- [[Hill Cipher]] — Linear algebra; plaintext vectors multiplied by a key matrix mod 26; Lester Hill, 1929
- [[Digrafid Cipher]] — Combines digraphic substitution with fractionation

---

## Polybius Square — The Foundation

The [[Polybius Cipher]] underlies most polygraphic systems. A 5×5 grid (I/J combined) maps 25 letters to coordinate pairs:

```
    1   2   3   4   5
1   A   B   C   D   E
2   F   G   H  I/J  K
3   L   M   N   O   P
4   Q   R   S   T   U
5   V   W   X   Y   Z
```

`H` → `(1,3)` or `13` in standard Polybius notation.

Systems that extend this include: [[Bifid Cipher]], [[Trifid Cipher]], [[ADFGVX Cipher]], [[Nihilist Cipher]], [[Tap Code Cipher]].

> Note: [[Bifid Cipher]] and [[Trifid Cipher]] are listed here as polygraphic systems but reside in [[MOC-Fractionation-Ciphers]] because their defining operation is fractionation, not simple polygraphic substitution.

---

## Cryptanalysis

- **Digraph frequency analysis** — the 676 possible digraphs have known English frequencies (`TH`, `HE`, `IN`, `ER` are most common)
- **Structural attacks** — Playfair's geometric rules leak information about letter pairs
- **[[Hill Cipher]] attacks** — vulnerable to known-plaintext attack; the key matrix can be recovered with enough plaintext/ciphertext pairs

---

## Interactive Tools

- [[Tool - Playfair Cipher]]
- [[Tool - Four-Square Cipher]]
- [[Tool - Polybius Cipher]]
- [[Tool - Hill Cipher]]
- [[Tool - Tap Code Cipher]]

---

## All Polygraphic Ciphers

```dataview
TABLE difficulty, year_invented, inventor, tool_available AS "Tool?"
FROM "docs/ciphers/classical/substitution/polygraphic"
WHERE type = "cipher"
SORT title ASC
```
