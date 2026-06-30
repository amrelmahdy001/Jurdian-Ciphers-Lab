---
title: "Cipher Identification Guide"
aliases:
  - "Cipher Identifier Quick Reference"
  - "How to Identify a Cipher"
  - "Unknown Cipher Guide"
type: puzzle-resource
domain: references
status: complete
tags:
  - reference
  - puzzle
  - ctf
  - identification
created: 2025-01-01
updated: 2025-01-01
---

# Cipher Identification Guide

> A systematic approach to identifying an unknown cipher, encoding, or hash — step by step.
> ← Back to [[MOC-References]] · [[MOC-Puzzles]]

---

## Step 1 — Examine the Character Set

The character set of the ciphertext is the fastest first filter.

| Characters Present | Likely Type | Next Step |
|---|---|---|
| Only `0` and `1` | Binary encoding or [[Bacon Cipher]] | → Step 2A |
| Only `.` and `-` (or dots/dashes) | [[Morse Code]] | Decode directly |
| Only `A–Z`, uppercase | Classical cipher | → Step 2B |
| `A–Z` + `a–z` | Classical cipher or base encoding | → Step 2B or Step 3 |
| `A–Z` + `a–z` + `0–9` + `+/=` | [[Base64 Encoding]] | Decode directly |
| `A–Z` + `2–7` + `=` | [[Base32 Encoding]] | Decode directly |
| `0–9` + `A–F` only | [[Hex Encoding]] or hash | → Step 2C |
| Only symbols/glyphs | Symbol cipher or writing system | → Step 4 |
| Numbers only | Numeric encoding or homophonic | → Step 5 |
| Mix of letters + numbers + symbols | Modern cipher output or base encoding | → Step 3 |

---

## Step 2A — Binary / Two-Symbol Ciphertext

If your ciphertext uses exactly two distinct symbols (could be `0/1`, `A/B`, `./−`, dots/crosses, etc.):

| Groups of | Likely Cipher | Notes |
|---|---|---|
| 5 bits per letter | [[Bacon Cipher]] | `AAAAA` = A, `AAAAB` = B, ... |
| 5 bits, using `·` and `−` | [[Morse Code]] (binary) | Non-standard representation |
| 8 bits | [[Binary Code]] / ASCII | `01000001` = A |
| Variable length, spaced | [[Morse Code]] | Standard dots and dashes |
| Grouped in 5s with A–E labels | [[ADFGX Cipher]] | Five distinct symbols |
| Grouped in 5s or 6s with A–F labels | [[ADFGVX Cipher]] | Six distinct symbols |

---

## Step 2B — Letters Only (A–Z)

Run [[Frequency Analysis]] and [[Index of Coincidence]] on the ciphertext.

### Index of Coincidence (IC) Guide

```
IC ≈ 0.065  →  English plaintext (monoalphabetic cipher or transposition)
IC ≈ 0.045  →  Polyalphabetic cipher with short key (Vigenère, Beaufort)
IC ≈ 0.038  →  Random / long polyalphabetic key / good modern cipher
IC > 0.070  →  Possibly non-English source language
```

### If IC ≈ 0.065 (Monoalphabetic or Transposition)

Check letter frequencies:

- **Most frequent letter has ~10–13%** — Monoalphabetic substitution
  - If frequency distribution matches English (E=most frequent, etc.) → [[Transposition Cipher]]
  - If frequency distribution is shifted uniformly → [[Caesar Cipher]] or [[ROT-13 Cipher]]
  - If distribution is shifted mathematically → [[Affine Cipher]]
  - If distribution is scrambled but letter frequencies preserved → [[Monoalphabetic Substitution Cipher]]

- **Letter frequencies match English exactly** — [[Transposition Cipher]]
  - Try [[Rail Fence Cipher]] — zigzag pattern
  - Try [[Columnar Transposition Cipher]] — rearranged columns
  - Try [[Route Transposition Cipher]] — grid read in different order

### If IC ≈ 0.038–0.050 (Polyalphabetic)

Determine key length:

1. Run [[Kasiski Test]] — find repeated sequences, measure distances, find GCD
2. Try [[Index of Coincidence]] at periods 1–20 — highest IC indicates key length
3. Split into `n` streams (one per key position)
4. Apply [[Frequency Analysis]] to each stream independently
5. Most likely cipher: [[Vigenère Cipher]], [[Beaufort Cipher]], [[Gronsfeld Cipher]]

---

## Step 2C — Hex String (Fixed Length)

If the ciphertext is a fixed-length hex string with no spaces, it is likely a **hash**, not a cipher.

| Hex Length (chars) | Bits | Likely Hash |
|---|---|---|
| 32 | 128 | [[MD5 Hash]] or [[MD4 Hash]] |
| 40 | 160 | [[SHA-1 Hash]] |
| 56 | 224 | [[SHA-224 Hash]] |
| 64 | 256 | [[SHA-256 Hash]] or [[BLAKE2 Hash]] |
| 96 | 384 | [[SHA-384 Hash]] |
| 128 | 512 | [[SHA-512 Hash]] or [[BLAKE2 Hash]] |

> Use [[Tool - Hash Identifier]] for automated detection.

> [!warning] Hashes are one-way
> If this is a hash, you cannot decrypt it. You can attempt a lookup against known hash databases: [[Tool - Hash Lookup]].

---

## Step 3 — Base Encoding Detection

| Pattern | Encoding |
|---|---|
| Ends with `=` or `==`, uses `A–Z a–z 0–9 + /` | [[Base64 Encoding]] |
| Uses only `A–Z 2–7`, ends with `=` | [[Base32 Encoding]] |
| Uses `0–9 A–Z a–z` (no `+/=`) | [[Base62 Encoding]] or [[Base58 Encoding]] |
| Uses `0–9 A–Z` (uppercase only, no `I O`) | [[Base32 Crockford Encoding]] |
| Starts with `%` or contains `%XX` | [[URL Encoding]] |
| Contains `&#` or `&amp;` | [[HTML Escape]] |
| Looks like words separated by spaces, no digits | [[PGP Word List]] |

---

## Step 4 — Symbol or Glyph Ciphertext

If the ciphertext consists of non-Latin symbols or glyphs:

### Geometric Shapes
| Symbol Appearance | Likely Cipher |
|---|---|
| Segments of a tic-tac-toe grid | [[Pigpen Cipher]] or [[Rosicrucian Cipher]] |
| Cross/dagger shapes in a grid | [[Templars Cipher]] |
| Segment combinations forming letters | [[Elian Script]] |
| Birds on a wire / music staff | [[Birds on a Wire Cipher]] |
| Stick figures in various poses | [[Dancing Men Cipher]] |
| Curved symbols | Possibly [[Dorabella Cipher]] |
| Clock hand positions | [[Clock Cipher]] |
| Six-color hex blocks | [[Hexahue Cipher]] |

### Known Fictional Alphabets
| Context | Script |
|---|---|
| Star Wars props | [[Aurebesh Alphabet]] |
| Minecraft enchanting table | [[Standard Galactic Alphabet]] |
| Gravity Falls show | [[Gravity Falls Bill Cipher]] or related |
| Elder Scrolls games | [[Daedric Alphabet]] |
| Star Trek | [[Klingon Language]] or [[Vulcan Language]] |
| Zelda games | [[Hylian Language]] (multiple variants) |

> Consult [[MOC-Writing-Systems]] for the full list of constructed scripts.

### Icon Fonts
| Font | Appearance |
|---|---|
| [[Wingdings Font]] | Common Windows symbol font |
| [[Webdings Font]] | Web-oriented symbols |
| [[ITC Zapf Dingbats]] | Decorative typographic symbols |

---

## Step 5 — Numbers Only

| Pattern | Likely Cipher |
|---|---|
| Numbers 1–26 (or 0–25) only | [[A1Z26 Cipher]] (A=1, B=2... Z=26) |
| Numbers in pairs (11–55, no 6–9) | [[Polybius Cipher]] |
| Very large numbers | Possibly [[RSA Cipher]] output or [[Base10 Encoding]] |
| Sequences involving primes | [[Prime Numbers Cipher]] |
| Groups of 5 digits | [[Nihilist Cipher]] or [[VIC Cipher]] |
| Numbers 0–25 in groups | [[Affine Cipher]] or [[Monoalphabetic Substitution Cipher]] |

---

## Step 6 — Message Is Only Letters But Makes No Sense After Step 2

If frequency analysis gave no clear result, try:

1. **Is the message length prime?** — Unlikely to be columnar transposition (no clean grid)
2. **Try word boundaries** — Are there spaces? If so, can you find pattern words like `THE`, `AND`, `IS`?
3. **Reverse the message** — Some simple puzzles use reversed text
4. **Try multiple layers** — Could be encoded, then ciphered (Base64 → Vigenère is common in CTF)
5. **Check for steganography** — See [[MOC-Steganography]]

---

## Quick Summary Card

```
Unknown ciphertext
    │
    ├─ Only 0s and 1s ──────────────────────► Binary / Bacon / Morse
    ├─ Dots and dashes ─────────────────────► Morse Code
    ├─ Symbols / glyphs ────────────────────► Pigpen, Dancing Men, or writing system
    ├─ Fixed-length hex ────────────────────► Hash (MD5, SHA, etc.) — NOT decryptable
    ├─ Letters + = sign ────────────────────► Base64 / Base32
    ├─ Numbers only ────────────────────────► A1Z26, Polybius, Nihilist
    └─ Letters only
           │
           ├─ IC ≈ 0.065
           │      ├─ Frequencies shifted → Caesar / Affine
           │      ├─ Frequencies scrambled → Monoalphabetic substitution
           │      └─ Frequencies match English → Transposition
           └─ IC ≈ 0.038–0.050
                  └─ Run Kasiski → find key length → Vigenère / Beaufort
```

---

## Automated Tools

- [[Tool - Cipher Identifier]] — Paste ciphertext; get a list of likely cipher types
- [[Tool - Frequency Analysis]] — Visualise letter frequency distribution
- [[Tool - Index of Coincidence]] — Numeric IC and key-length estimation
- [[Tool - Hash Identifier]] — Identify hash type from string characteristics
- [[Tool - Kasiski Test]] — Automated key-length detection for polyalphabetic ciphers

---

## Related

- [[MOC-Cryptanalysis]] — Full attack method index
- [[MOC-Statistical-Analysis]] — Statistical tools
- [[Frequency Analysis]] — Detailed guide
- [[Index of Coincidence]] — Detailed guide
- [[Kasiski Test]] — Detailed guide
