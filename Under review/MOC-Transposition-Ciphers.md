---
type: moc
title: "MOC — Transposition Ciphers"
aliases:
  - "Transposition Ciphers Index"
  - "Permutation Ciphers"
tags:
  - moc
  - cipher
  - classical
  - transposition
created: 2025-01-01
updated: 2025-06-28
---

# Transposition Ciphers — Index

> **Definition:** A transposition cipher rearranges the positions of plaintext letters without changing the letters themselves. The ciphertext contains exactly the same letters as the plaintext — only their order changes.
> ← Back to [[MOC-Classical-Ciphers]]

---

## Core Concept

Transposition is the **complement** of substitution. Where substitution changes *what* the letters are, transposition changes *where* the letters are.

**Key property:** An anagram analysis of any segment of ciphertext will reveal the original letters are unchanged. This is also the primary distinguishing attack.

**Combined with substitution:** Many strong cipher systems combine both operations. [[ADFGVX Cipher]] does substitution (Polybius) first, then transposition. The [[Enigma Machine]] is primarily substitution, but some variants include transposition.

---

## Ciphers in This Family

### Geometric Path Transpositions
- [[Caesar Box Cipher]] — Text written in a square, read out in a different direction
- [[Route Transposition Cipher]] — Text written into a grid; read out along a defined path (spiral, zigzag, etc.)
- [[Scytale Cipher]] — Ancient Spartan cipher; text wound on a rod of specific diameter
- [[Spiral Cipher]] — Text written or read in spiral order

### Rail & Fence Transpositions
- [[Rail Fence Cipher]] — Text written diagonally across N "rails"; read off row by row
- [[Redefence Cipher]] — Rail fence variant with a key specifying rail reading order

### Columnar Transpositions
- [[AMSCO Cipher]] — Irregular columnar transposition; alternating column lengths
- [[Columnar Transposition Cipher]] — Write in rows, read off by keyed column order
- [[Double Transposition Cipher]] — Columnar transposition applied twice; significantly stronger
- [[Skip Cipher]] — Characters taken from the ciphertext at fixed intervals
- [[Swagman Cipher]] — Complex keyed grid transposition
- [[Ubchi Cipher]] — Keyed columnar transposition with null padding

### Mechanical Transpositions
- [[Turning Grille Cipher]] — Cardboard grille with holes; rotated to different positions

---

## Cryptanalysis of Transposition Ciphers

### Detection
An important observation: **transposition ciphers preserve the letter frequencies of the plaintext**. If the ciphertext frequency distribution matches English (or the suspected language), a transposition cipher is likely.

Use [[Index of Coincidence]] — transposition gives the same IC as the plaintext language.

### Attacks
1. **Anagramming** — rearrange ciphertext letters to form meaningful words
2. **Column pattern detection** — for columnar transpositions, try different column widths
3. **Known plaintext** — if a word is guessed, its letters must appear in the ciphertext, revealing column structure
4. **Statistical cribs** — common letter pairs (`TH`, `HE`) constrain possible column assignments

### Double Transposition
Significantly harder than single transposition. No known efficient attack; must use hill-climbing or simulated annealing algorithms on modern hardware.

---

## Interactive Tools

- [[Tool - Rail Fence Cipher]]
- [[Tool - Columnar Transposition Cipher]]
- [[Tool - Route Transposition Cipher]]
- [[Tool - Caesar Box Cipher]]
- [[Tool - Scytale Cipher]]

---

## All Transposition Ciphers

```dataview
TABLE difficulty, year_invented, tool_available AS "Tool?"
FROM "docs/ciphers/classical/transposition"
WHERE type = "cipher"
SORT title ASC
```
