---
title: Bacon's Cipher
aliases: Baconian Cipher, Bacon's Bilateral Cipher
type: Cipher
class: Classical
category: Substitution
technique: Polygraphic
character_support:
  - Uppercase
  - Lowercase
  - Spaces
key_count: None
difficulty: ★★★☆☆
tags:
  - substitution
  - polygraphic
  - steganography
  - classical
  - bacon
status: Complete
created: 2026-07-01
updated: 2026-07-01
---

# Bacon's Cipher

> **A binary substitution cipher that encodes each letter of the alphabet using a 5‑bit pattern of two arbitrary symbols, effectively embedding a hidden message within any dual‑form carrier text.**

> [!tip] Browser Tool
> [[Tool - Bacon's Cipher]]

---

## Overview

Bacon's cipher, devised by Sir Francis Bacon in 1605, converts every letter into a 5‑character sequence made up of only two distinct symbols (typically **A** and **B**, hence “bilateral”). With five positions, 2⁵ = 32 combinations are possible, covering the 24‑letter Elizabethan alphabet (I/J and U/V were unified) and leaving room for control signals.

What makes Bacon's cipher unique is its dual nature as both a **cipher** and a **steganographic** system. The A/B patterns can be hidden within the letterforms of a separate overt message (e.g., using two different typefaces, italic vs. roman, or subtle variations in handwriting). A solver unaware of the steganographic layer sees only the innocent cover text. This fusion of secrecy and concealment makes it one of the earliest documented steganographic systems and a recurring favourite in modern ARGs, CTFs, and historical puzzle designs.

---
## Classification

This cipher belongs to the **Substitution** family and uses a **Polygraphic** technique, encoding each plaintext letter as a fixed‑length group of binary symbols.

It is a **Classical Cipher** designed for both manual encryption and steganographic embedding, requiring no numeric key.

---
## Character Support

| Character Type | Input | Output |
|----------------|:-----:|:------:|
| Uppercase (A–Z) | ✓ | ✓ |
| Lowercase (a–z) | ✓ | ✓ |
| Numbers (0–9) | ✗ | ✗ |
| Spaces | ✓ | ✓ |
| Punctuation | ✗ | ✗ |
| Symbols | ✗ | ✗ |
| Unicode | ✗ | ✗ |
| Binary | ✗ | ✗ |

The original cipher handles the 24‑letter classical alphabet. Modern adaptations extend it to the full 26‑letter English alphabet by assigning unique codes to I/J and U/V separately or including extra combinations.

---

## History

Sir Francis Bacon described the bilateral cipher in his 1605 work *Of the Proficience and Advancement of Learning* and later in *De Augmentis Scientiarum* (1623). He proposed it not only for secret correspondence but also as a method to embed hidden signatures or messages within printed books using two visibly distinct typefaces. Bacon saw it as a tool for intellectual communication that bypassed the scrutiny of political and religious authorities. The cipher gained renewed attention in the 19th and 20th centuries among Baconian theorists who claimed (controversially) that Bacon used it to sign the works attributed to William Shakespeare. Modern cryptography views it as a foundational work in binary encoding and steganography.

---

## How It Works

### Encryption

1. Choose two arbitrary symbols to represent the binary states. The original uses **A** and **B**, but any contrasting pair works (e.g., 0/1, italic/roman, uppercase/lowercase, two colours).
2. Convert each plaintext letter to its 5‑symbol Baconian code according to the chosen alphabet mapping.
3. Concatenate the resulting groups to form the raw ciphertext.

If the output is to be hidden steganographically, the 5‑bit patterns are overlaid onto a cover text of the same total length. Each character of the cover text carries one bit of the hidden message by its typographic style or some other binary property.

### Decryption

1. Extract the 5‑bit groups from the ciphertext (or from the steganographic carrier by observing the binary distinction on each character).
2. Split the bitstream into blocks of 5.
3. Map each 5‑bit pattern back to its corresponding letter using the agreed‑upon alphabet.

If the raw A/B string is provided without a carrier, decryption is a direct lookup.

### Mathematical Formula

No modular arithmetic is involved. The cipher is a deterministic mapping from an alphabet of size *n* to 5‑bit binary codes:

**Encryption**

$$
\text{Code}(L) = b_4 b_3 b_2 b_1 b_0
$$

**Decryption**

$$
L = \text{Table}^{-1}(b_4 b_3 b_2 b_1 b_0)
$$

**Variables**

- **L** — a plaintext or ciphertext letter from the defined alphabet
- **b₄…b₀** — the 5‑bit binary sequence (each bit is one of the two chosen symbols)

The standard mapping (A=0, B=1, treating the 5‑bit string as a binary number where AAAAA = 0 = ‘a’) is the most common modern convention, but Bacon’s original tables used a slightly different ordering.

### Worked Example

**Standard Modern Mapping (AAAAA = A, AAAAB = B, …)**

| Parameter | Value |
|-----------|-------|
| **Plaintext** | `HELLO` |
| **Alphabet** | 26‑letter English (with I/J and U/V separated) |
| **Code Symbols** | `A` and `B` |

| Letter | Binary Pattern (A=0, B=1) | Bacon Code |
|--------|---------------------------|------------|
| H | 00111 | AABBB |
| E | 00100 | AABAA |
| L | 01011 | ABABB |
| L | 01011 | ABABB |
| O | 01110 | ABBBA |

**Result (raw ciphertext)**

```text
AABBB AABAA ABABB ABABB ABBBA
```

**Steganographic Example:** Hiding this in a cover text of 25 letters by using bold for B and italic for A:

**Cover Text**

```text
this is a demonstration message
```

**Hidden Bits**
Applying the first 25 letters with bold for B, italic for A (spaces ignored):
```text
A A B B B A A B A A A B A B B A B A B B A B B B A
```

**Character Mapping**

| Cover Character | t | h | i | s | i | s | a | d | e | m | o | n | s | t | r | a | t | i | o | n | m | e | s | s | a |
|-----------------|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Hidden Bit      | A | A | B | B | B | A | A | B | A | A | A | B | A | B | B | A | B | A | B | B | A | B | B | B | A |

**Visual Representation**

*t* *h* **i** **s** **i** *s* *a* **d** *e* *m* *o* **n** *s* **t** **r** *a* **t** *i* **o** **n** *m* *e* **s** **s** *a*

> The overt message appears normal unless the reader knows to look at the typeface variations.

## Analysis

### Security

In its raw A/B form, Bacon's cipher provides no security; the encoding is well‑known and trivially reversible. When used as a steganographic system, its security depends entirely on the imperceptibility of the binary carrier distinction. If an interceptor notices two alternating typefaces or handwriting styles, the hidden message is exposed.

---

### Cryptanalysis

- **Direct lookup:** if the A/B string is given, the message can be decoded instantly with the standard alphabet table.
- **Carrier detection:** visible alternation between two styles (font, case, colour) strongly suggests a Baconian embedding.
- **Statistical analysis:** the 5‑bit grouping is a telltale sign; counts of 5 are always present in the total character length.
- **Brute‑force alphabet ordering:** if a non‑standard mapping of 5‑bit codes to letters is used, anagramming or frequency analysis on the decoded output reveals the mapping.

---

### Recognition Patterns

- A string consisting solely of two alternating symbols (A/B, 0/1, italic/roman, etc.) with a total length divisible by 5 strongly suggests Bacon's cipher.
- In steganographic form, any text where every fifth character is treated differently, or where two type styles visibly alternate, is a likely candidate.
- Ciphertext length is always exactly 5 times the plaintext letter count.
- Spaces are normally ignored; their presence or absence does not affect the 5‑bit grouping.
- If decoded as binary with A=0, B=1, the 5‑bit values range from 0–25 (for 26‑letter alphabets) or 0–23 (for the original 24‑letter alphabet).

---

## Similar Ciphers

### [[Binary Encoding]]

- **Similarity:** Bacon's cipher is essentially a 5‑bit binary encoding of the alphabet, identical in concept to modern binary representations.
- **Difference:** Bacon's cipher is designed for manual steganography using two arbitrary symbols; modern binary encoding uses 0/1 and is typically 7‑ or 8‑bit (ASCII). Bacon's 5‑bit scheme is optimised for a limited alphabet and human embedding.

### [[Polybius Square]]

- **Similarity:** Both are polygraphic substitution ciphers that encode each letter as a fixed‑length combination of symbols from a small set (5 symbols in Polybius when using a 5×5 grid with coordinates 1–5).
- **Difference:** Polybius uses a 2‑character coordinate pair and a variable grid layout (keyed by a keyword); Bacon uses a fixed 5‑bit binary code per letter. The steganographic application is unique to Bacon's design.

### [[Morse Code]]

- **Similarity:** Both represent each letter as a sequence of symbols from a very small set (dots/dashes, A/B). Both can be embedded in carrier media.
- **Difference:** Morse is a variable‑length code optimised for telegraphy and human listening; Bacon is a fixed‑length code designed for steganographic embedding. Morse requires a separator between letters; Bacon does not (the fixed length provides self‑synchronisation).

---

## Variants

### [[Original 24‑Letter Baconian Alphabet]]

Bacon's original mapping used 24 letters (I and J combined, U and V combined). This variant is encountered in historically accurate recreations and some period‑style puzzles. Decoding with a modern 26‑letter table produces discrepancies on I/J and U/V.

### [[Bacon's Cipher with Keyword Alphabet Ordering]]

Instead of the standard alphabetic order for assigning 5‑bit codes, the plaintext alphabet is permuted by a keyword. This adds a layer of secrecy, as an attacker must know the keyword to map the 5‑bit patterns correctly. The bilateral nature remains unchanged.

### [[Case‑Based Steganographic Bacon]]

One of the most common modern applications: hiding the A/B bits in the case of each letter in a cover sentence (e.g., lowercase = A, uppercase = B, or vice versa). This creates a sentence with seemingly erratic capitalisation that carries a hidden message.

### [[Font‑Based Steganographic Bacon]]

Using two visually similar fonts, or toggling between normal and italic, to encode the A/B bits in a printed or digital document. This is the closest modern equivalent to Bacon's original steganographic proposal.

---

## Browser Tool

An interactive tool supports encoding and decoding of Bacon's cipher with multiple output options, including raw A/B format, case‑based steganographic embedding, and extraction from case‑patterned text.

### Features

- Encode plaintext to A/B pattern or binary
- Decode A/B pattern or binary back to text
- Generate steganographic carrier text with case‑based embedding
- Extract hidden message from case‑patterned text
- Support for 24‑letter and 26‑letter alphabet mappings
- Custom symbol pairs (e.g., 0/1, X/O)

Tool:
[[Tool - Bacon's Cipher]]