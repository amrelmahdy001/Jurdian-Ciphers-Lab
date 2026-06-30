---
type: moc
title: "MOC — Shift Ciphers"
aliases:
  - "Shift Ciphers Index"
  - "Caesar Family"
tags:
  - moc
  - cipher
  - classical
  - shift
created: 2025-01-01
updated: 2025-06-28
---

# Shift Ciphers — Index

> **Definition:** A shift cipher replaces each plaintext letter with the letter a fixed number of positions along the alphabet.
> All shift ciphers are monoalphabetic and symmetric. They are all broken by frequency analysis.
> ← Back to [[MOC-Classical-Ciphers]]

---

## What Is a Shift Cipher?

A shift cipher applies a uniform numerical offset to every letter in the plaintext. With a 26-letter alphabet, there are only 25 non-trivial keys — making all shift ciphers trivially brute-forceable.

The entire family descends from the [[Caesar Cipher]]. Variants differ in which alphabet or character set they operate on, or how the shift is derived.

**Encryption formula:** `C = (P + K) mod N`
Where `P` = plaintext index, `K` = shift key, `N` = alphabet size.

---

## The Caesar Family

### Foundation
- [[Shift Cipher]] — The general form; any alphabet, any shift
- [[Caesar Cipher]] — Shift of 3 over A–Z; the canonical example

### Fixed-Shift Variants (ROT Family)
> All ROT ciphers are shift ciphers with a fixed key. No key is needed to decode — the name encodes the shift.

- [[ROT-1 Cipher]] — Shift of 1; `A→B`, `B→C` …
- [[ROT-5 Cipher]] — Shift of 5 over digits only (`0→5`, `5→0`)
- [[ROT-13 Cipher]] — Shift of 13; self-inverse over A–Z
- [[ROT-18 Cipher]] — ROT-13 (letters) + ROT-5 (digits) combined
- [[ROT-47 Cipher]] — Shift of 47 over ASCII printable characters (33–126)
- [[ROT-8000 Cipher]] — Unicode-aware shift; covers emoji and non-Latin scripts
- [[ROT-N Cipher]] — Generalised ROT; user-specified shift value

### Keyed & Modified Variants
- [[ASCII Shift Cipher]] — Shift applied to full ASCII byte values (0–127)
- [[Keyed Caesar Cipher]] — Caesar shift applied after a keyword-shuffled alphabet
- [[Keyboard Shift Cipher]] — Letters shifted by physical keyboard position rather than alphabet position
- [[Progressive Caesar Cipher]] — Shift value increases with each letter position
- [[Unicode Shift Cipher]] — Shift applied to Unicode code points

---

## Key Properties

| Cipher | Key Space | Alphabet | Self-Inverse? |
|---|---|---|---|
| [[Caesar Cipher]] | 25 | A–Z | No (unless shift = 13) |
| [[ROT-13 Cipher]] | Fixed | A–Z | Yes |
| [[ROT-47 Cipher]] | Fixed | ASCII 33–126 | Yes |
| [[ROT-5 Cipher]] | Fixed | 0–9 | Yes |
| [[ROT-18 Cipher]] | Fixed | A–Z + 0–9 | Yes |
| [[ASCII Shift Cipher]] | 127 | ASCII 0–127 | No |
| [[Progressive Caesar Cipher]] | Variable | A–Z | No |

---

## Cryptanalysis

All shift ciphers are broken by:
1. **Brute force** — at most 25 trials for standard A–Z
2. **[[Frequency Analysis]]** — most frequent ciphertext letter maps to `E`
3. **Pattern recognition** — common words like `THE`, `AND`, `IS`

See: [[Frequency Analysis]] · [[Brute Force Attack]] · [[Index of Coincidence]]

---

## Related Families

Shift ciphers are a strict subset of monoalphabetic substitution.
- For keyword-derived substitutions → [[MOC-Monoalphabetic]]
- For multi-alphabet systems → [[MOC-Polyalphabetic]]
- For mathematical generalisation → [[Affine Cipher]]

---

## Interactive Tools

- [[Tool - Caesar Cipher]] — Encrypt, decrypt, and brute-force all 25 shifts
- [[Tool - ROT-13]] — One-click ROT-13 encoder/decoder
- [[Tool - ROT-N]] — Configurable ROT encoder for any shift
- [[Tool - ROT-47]] — Full ASCII printable range rotation

---

## All Shift Ciphers

```dataview
TABLE difficulty, broken, tool_available AS "Tool?"
FROM "docs/ciphers/classical/shift"
WHERE type = "cipher"
SORT title ASC
```
