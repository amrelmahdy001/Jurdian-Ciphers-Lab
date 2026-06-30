---
type: moc
title: "MOC — Classical Ciphers"
aliases:
  - "Classical Ciphers Index"
tags:
  - moc
  - cipher
  - classical
created: 2025-01-01
updated: 2025-06-28
---

# Classical Ciphers — Index

> **Definition:** Classical ciphers are pre-computer encryption methods — designed to be computed by hand or with mechanical devices.
> ← Back to [[MOC-Ciphers]]

---

## Sub-Indexes

- [[MOC-Shift-Ciphers]] — Uniform alphabet shifts; the Caesar family
- [[MOC-Substitution-Ciphers]] — All substitution cipher sub-families
  - [[MOC-Monoalphabetic]] — One cipher alphabet, fixed mapping
  - [[MOC-Polyalphabetic]] — Rotating or keyword-driven cipher alphabets
  - [[MOC-Homophonic-Ciphers]] — Many ciphertext symbols per plaintext letter
  - [[MOC-Polygraphic-Ciphers]] — Multi-letter substitution (digraphic, trigraphic)
  - [[MOC-Symbolic-Ciphers]] — Symbol or glyph-based substitution
- [[MOC-Transposition-Ciphers]] — Rearranging letter positions without substituting them
- [[MOC-Fractionation-Ciphers]] — Splitting letters into components before permuting
- [[MOC-Mechanical-Ciphers]] — Ciphers implemented via physical devices

---

## Curated Entry Points

### Beginner-Friendly Ciphers
- [[Caesar Cipher]] — The most well-known classical cipher
- [[ROT-13 Cipher]] — Caesar with shift of 13; self-inverse
- [[Atbash Cipher]] — Alphabet reversed; no key required
- [[Pigpen Cipher]] — Geometric symbol substitution
- [[Rail Fence Cipher]] — Zigzag transposition
- [[Polybius Cipher]] — Letters encoded as grid coordinates

### Intermediate Ciphers
- [[Vigenère Cipher]] — Polyalphabetic; defeated frequency analysis for centuries
- [[Playfair Cipher]] — Digraphic substitution; used in WWI
- [[Affine Cipher]] — Mathematical monoalphabetic substitution
- [[Beaufort Cipher]] — Vigenère variant; self-reciprocal
- [[Columnar Transposition Cipher]] — Systematic columnar rearrangement
- [[Bifid Cipher]] — Polybius square + fractionation

### Advanced Ciphers
- [[Enigma Machine]] — Electromechanical rotor cipher; WWII
- [[ADFGVX Cipher]] — Fractionation + transposition; WWI German
- [[VIC Cipher]] — Complex Soviet spy cipher; considered unbreakable by hand
- [[Chaocipher]] — Self-modifying cipher disk; never published
- [[Hill Cipher]] — Matrix-based polygraphic substitution
- [[Trifid Cipher]] — Three-dimensional Polybius fractionation

### Puzzle & CTF Favorites
- [[Vigenère Cipher]]
- [[Bifid Cipher]]
- [[Rail Fence Cipher]]
- [[Playfair Cipher]]
- [[Dancing Men Cipher]]
- [[Pigpen Cipher]]
- [[Four-Square Cipher]]

---

## Historical Significance Timeline

| ~50 BCE | [[Caesar Cipher]] — Julius Caesar's military cipher |
|---|---|
| ~600 CE | [[Atbash Cipher]] — Biblical Hebrew substitution |
| 1467 | [[Alberti Cipher]] — First polyalphabetic cipher |
| 1553 | [[Vigenère Cipher]] — Giovan Bellaso's invention (attributed to Vigenère) |
| 1854 | [[Playfair Cipher]] — Charles Wheatstone's digraphic cipher |
| 1861 | [[Polybius Cipher]] revival — square used in many later ciphers |
| 1914 | [[ADFGVX Cipher]] — German WWI fractionation cipher |
| 1918 | [[ADFGVX Cipher]] — Broken by Georges Painvin |
| 1923 | [[Enigma Machine]] — Arthur Scherbius patents rotor cipher |
| 1944 | [[VIC Cipher]] — Soviet spy cipher developed |

---

## All Classical Ciphers A–Z

```dataview
TABLE subcategory, difficulty, broken
FROM "docs/ciphers/classical"
WHERE type = "cipher"
SORT title ASC
```
