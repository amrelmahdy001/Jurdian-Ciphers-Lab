---
type: moc
title: "MOC — Symbolic Ciphers"
aliases:
  - "Symbol Cipher Index"
  - "Glyph Ciphers"
  - "Visual Substitution Ciphers"
tags:
  - moc
  - cipher
  - classical
  - substitution
  - symbolic
created: 2025-01-01
updated: 2025-06-28
---

# Symbolic Ciphers — Index

> **Definition:** A symbolic cipher substitutes plaintext letters with symbols, glyphs, or geometric shapes instead of other letters. Cryptographically equivalent to monoalphabetic substitution — broken by the same methods.
> ← Back to [[MOC-Substitution-Ciphers]]

---

## Important Distinction

Symbolic ciphers are **monoalphabetic substitution ciphers** where the ciphertext alphabet is visual rather than textual. Their cryptographic strength is identical to any other monoalphabetic cipher (i.e., they are broken by [[Frequency Analysis]]).

Their primary value today is:
- **Puzzle design** — visually distinctive and satisfying to solve
- **Steganographic obscurity** — unfamiliar symbols cause the message to be overlooked
- **CTF competitions** — recognizing the symbol set is often the first challenge

> Do not confuse symbolic ciphers with writing systems. [[Pigpen Cipher]] is a cipher — it encodes the Latin alphabet into geometric shapes. [[Elder Futhark]] is a historical writing system — it is an independent alphabet, not a substitution for Latin letters.
>
> See also: [[MOC-Writing-Systems]] for non-cipher scripts.

---

## Ciphers in This Family

### Geometric Symbol Ciphers
- [[Betamaze Cipher]] — Labyrinth-style symbol substitution
- [[Birds on a Wire Cipher]] — Birds on musical staff represent letters by position
- [[Clock Cipher]] — Clock hands indicate letters by hour position
- [[Hexahue Cipher]] — Six-color hex grid; colors encode letter groups
- [[Ideograms Cipher]] — Lines, circles, and dots form a systematic symbol alphabet
- [[Pigpen Cipher]] — Letters placed in a tic-tac-toe and X grid; the most common symbol cipher
- [[Rosicrucian Cipher]] — Variant of Pigpen; associated with secret societies
- [[Templars Cipher]] — Cross-based symbol substitution; allegedly used by Knights Templar
- [[Tic-Tac-Toe Cipher]] — Alternative name for the Pigpen grid system

### Line & Path Ciphers
- [[Daggers' Alphabet]] — Dagger/cross shaped symbols forming an alphabet
- [[Dancing Men Cipher]] — Stick figures in various poses; from Arthur Conan Doyle's Sherlock Holmes
- [[Elian Script]] — Alphabet encoded into segments of a 3×3 grid
- [[Music Sheet Cipher]] — Notes on a musical staff encode letters by pitch or position

### Hidden Message Ciphers
- [[Dorabella Cipher]] — Unsolved cipher by Edward Elgar using curved symbol shapes
- [[Gold Bug Cipher]] — Symbolic substitution cipher from Edgar Allan Poe's story

---

## Pigpen Variant Family

The Pigpen family is the largest group of symbol ciphers:

```
Standard Pigpen:    Letters placed in grid segments
Rosicrucian:        Same grid, different letter placement
Templar Cipher:     Cross-shaped variant
Tic-Tac-Toe:        Alternative naming for standard Pigpen
```

All share the same cryptographic weakness: they are simple monoalphabetic substitutions, and their symbols are widely documented.

---

## In Fiction & Puzzles

| Cipher | Appears In | Notes |
|---|---|---|
| [[Dancing Men Cipher]] | Sherlock Holmes, "The Adventure of the Dancing Men" | Stick figures in various stances |
| [[Gold Bug Cipher]] | Edgar Allan Poe, "The Gold-Bug" | Symbolic substitution; full solution in story |
| [[Dorabella Cipher]] | Edward Elgar's personal correspondence | Unsolved to this day |
| [[Pigpen Cipher]] | Freemasonry, National Treasure (film) | Widely recognized |

---

## Cryptanalysis

All symbolic ciphers are broken by:
1. **Symbol identification** — recognize which symbol system is in use
2. **[[Frequency Analysis]]** — the most frequent symbol maps to `E`
3. **Pattern matching** — look for double symbols, short words, common word shapes
4. **Known symbol tables** — most symbol ciphers have documented alphabets

---

## Interactive Tools

- [[Tool - Pigpen Cipher]]
- [[Tool - Dancing Men Cipher]]
- [[Tool - Elian Script]]
- [[Tool - Hexahue Cipher]]

---

## All Symbolic Ciphers

```dataview
TABLE difficulty, tool_available AS "Tool?"
FROM "docs/ciphers/classical/substitution/symbolic"
WHERE type = "cipher"
SORT title ASC
```
