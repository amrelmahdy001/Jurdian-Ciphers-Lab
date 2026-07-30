---
title: Atbash Cipher
aliases: Atbash, At-bash, Reverse Alphabet Cipher
type: Cipher
class: Ancient
category: Substitution
technique: Monoalphabetic
character_support:
  - Uppercase
  - Lowercase
  - Spaces
key_count: None
difficulty: ★☆☆☆☆
tags:
  - substitution
  - monoalphabetic
  - classical
  - ancient
  - atbash
status: Complete
created: 2026-07-01
updated: 2026-07-01
---

# Atbash Cipher

> **An ancient monoalphabetic substitution cipher that reverses the order of the alphabet, mapping the first letter to the last, the second to the second‑to‑last, and so on.**

> [!tip] Browser Tool
> [[Tool - Atbash Cipher]]

---

## Overview

The Atbash cipher replaces each letter of the alphabet with its mirror opposite: A becomes Z, B becomes Y, C becomes X, etc. Because the substitution is symmetric, encryption and decryption are the same operation. The cipher requires no key; it is completely fixed once the alphabet is chosen.

Originating in ancient Hebrew scribal traditions, Atbash is one of the oldest known ciphers. Today it appears almost exclusively in puzzles, CTFs, and ARGs as a simple layer of obfuscation that can be spotted instantly by its characteristic letter reversal.

---
## Classification

This cipher belongs to the **Substitution** family and uses a **Monoalphabetic** technique with a fixed reverse mapping.

It is an **Ancient Cipher** that requires no key.

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

---

## History

Atbash dates back to at least the 6th century BCE and appears in the Hebrew Bible (notably in Jeremiah 25:26 and 51:41, where “Sheshach” is understood as an Atbash encoding of “Babel”). The name “Atbash” derives from the Hebrew letters Aleph–Tav–Beth–Shin, the first, last, second, and second‑to‑last letters of the Hebrew alphabet, describing the substitution pattern. It was used by scribes for simple concealment and later entered the broader cryptographic canon as the archetypal reverse‑alphabet cipher.

---

## How It Works

### Encryption

Each letter is mapped to its positional reverse within the alphabet. For the English alphabet of 26 letters:

- A (position 1) ↔ Z (position 26)
- B (position 2) ↔ Y (position 25)
- C (position 3) ↔ X (position 24)
- …
- M (position 13) ↔ N (position 14)

Lowercase letters follow the same mapping (a ↔ z, b ↔ y, etc.). Non‑alphabetic characters such as spaces are left unchanged.

### Decryption

Decryption is identical to encryption. Applying Atbash to an Atbash‑enciphered text restores the original plaintext because the reverse mapping is involutory.

### Mathematical Formula

**Encryption / Decryption**

$$
C = 25 - P
$$

**Variables**

- **P** — numeric value of a plaintext or ciphertext letter (A=0, B=1, …, Z=25)
- **C** — numeric value of the resulting letter (0–25)

This formula assumes A=0. If using 1‑based indexing (A=1, …, Z=26), the formula becomes C = 27 − P.

### Worked Example

| Parameter | Value |
|-----------|-------|
| **Plaintext** | `HELLO WORLD` |

| Letter | P (A=0) | 25 − P | Ciphertext |
|--------|---------|--------|------------|
| H | 7 | 18 | `S` |
| E | 4 | 21 | `V` |
| L | 11 | 14 | `O` |
| L | 11 | 14 | `O` |
| O | 14 | 11 | `L` |
| (space) | – | – | (space) |
| W | 22 | 3 | `D` |
| O | 14 | 11 | `L` |
| R | 17 | 8 | `I` |
| L | 11 | 14 | `O` |
| D | 3 | 22 | `W` |

**Result**

```text
SVOOL DLIOW
```
## Analysis

### Security

Atbash provides no security. It is a keyless, fixed substitution that can be reversed by anyone who recognises it. It functions solely as obfuscation.

---

### Cryptanalysis

- **Direct reversal:** applying Atbash again instantly yields the plaintext.
- **Frequency analysis:** letter frequencies are preserved; the mapping is immediately apparent from the reversal pattern.
- **Pattern recognition:** common words reverse in predictable ways (e.g., "THE" becomes "GSV", "HELLO" → "SVOOL"), providing quick cribs.

---

### Recognition Patterns

- Only letters are transformed; spaces and punctuation remain unchanged.
- The substitution is symmetric: the first half of the alphabet maps to the second half in reverse order.
- Ciphertext letter frequencies mirror the plaintext language; no statistical flattening occurs.
- Repeated letters in the plaintext remain repeated identically in the ciphertext.
- Output often contains reversed‑sounding fragments of common words, making manual recognition easy.

---

## Similar Ciphers

### [[Caesar Cipher]]

- **Similarity:** Both are monoalphabetic substitution ciphers that are trivially reversible.
- **Difference:** The Caesar cipher uses a uniform shift with a variable key; Atbash uses a fixed reverse mapping. Atbash can be expressed as an [[Affine Cipher]] with a=25 and b=25.

### [[Affine Cipher]]

- **Similarity:** Atbash is a special case of the affine cipher (a=25, b=25 mod 26). Both use modular arithmetic to map letters.
- **Difference:** The affine cipher allows two variable keys; Atbash has no key and a fixed mapping.

### [[ROT13]]

- **Similarity:** Both are self‑inverse, keyless transformations that preserve letter case. Both are frequently used for casual obfuscation online.
- **Difference:** ROT13 shifts letters forward by 13 positions; Atbash reverses the alphabet order. They produce different mappings and are not interchangeable.

---

## Variants

### [[Hebrew Atbash]]

The original form of the cipher, applied to the 22‑letter Hebrew alphabet. It follows the same reverse‑order principle: Aleph ↔ Tav, Beth ↔ Shin, and so on. Biblical scholars study this variant for its potential exegetical significance.

### [[Albam Cipher]]

A related ancient Hebrew substitution where the alphabet is split in half and the halves are mapped directly (Aleph ↔ Lamed, Beth ↔ Mem, etc.), rather than reversed. It is structurally similar to ROT13 on the Hebrew alphabet.

### [[Atbah Cipher]]

Another Hebrew variant based on pairing letters by numerical value modulo a key number, producing a different fixed mapping. Less common than Atbash or Albam, but found in some historical manuscripts.

### [[Atbash on Extended Character Sets]]

The reverse‑mapping principle can be applied to any ordered character set, including digits (0↔9, 1↔8, etc.) or full printable ASCII ranges. These generalisations are sometimes encountered in CTFs and custom puzzle encodings.

---

## Browser Tool

A simple interactive tool allows instant Atbash encoding and decoding, with options to preserve or strip non‑alphabetic characters.

### Features

- Encode / Decode (same operation)
- Preserve spaces and punctuation
- Case‑sensitive mode
- Live preview

Tool:
[[Tool - Atbash Cipher]]