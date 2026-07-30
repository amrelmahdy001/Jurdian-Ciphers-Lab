---
title: ROT5
aliases: ROT-5, digit rotation cipher
type: Cipher
class: Classical
category: Substitution
technique: Shift
character_support:
  - Numbers
key_count: None
difficulty: ★☆☆☆☆
tags:
  - substitution
  - shift
  - classical
  - numeric
  - rot5
status: Complete
created: 2026-06-30
updated: 2026-06-30
---

# ROT5

> **A simple shift cipher for the digits 0–9 that rotates each numeral by 5 positions.**

> [!tip] Browser Tool
> ROT5 is typically implemented alongside [[ROT13]]; see [[Tool - ROT13 Cipher]].

---

## Overview

ROT5 (“rotate by 5”) is the numeric counterpart to [[ROT13]], applying a fixed shift of 5 to the decimal digits 0–9. Because the digit set has 10 elements, a shift of 5 means that applying ROT5 twice restores the original value — it is self‑inverse, just like ROT13. Its sole purpose is light obfuscation of numbers; it provides no security and is used almost exclusively in puzzles, recreational contexts, or combined with ROT13 to encode alphanumeric strings.

---
## Classification

This cipher belongs to the **Substitution** family and uses the **Shift** technique applied to a numeric alphabet.

It is a **Classical Cipher** with a fixed transformation and no variable key.

---
## Character Support

| Character Type | Input | Output |
|----------------|:-----:|:------:|
| Uppercase (A–Z) | ✗ | ✗ |
| Lowercase (a–z) | ✗ | ✗ |
| Numbers (0–9) | ✓ | ✓ |
| Spaces | ✗ | ✗ |
| Punctuation | ✗ | ✗ |
| Symbols | ✗ | ✗ |
| Unicode | ✗ | ✗ |
| Binary | ✗ | ✗ |

ROT5 only operates on the decimal digits; all other characters are left untouched.

---

## History

ROT5 emerged alongside other ROTx ciphers in early online communities as a trivial obfuscation method. There is no known historical attribution earlier than the Usenet era. It is most often encountered as the companion to ROT13 in the so‑called “ROT18” combination (ROT13 for letters, ROT5 for digits), used when a full alphanumeric string requires light masking.

---

## How It Works

### Encryption

1. Take each character from the input.
2. If it is a digit (0–9), add 5 to its numeric value and take the result modulo 10.
3. Replace the digit with the corresponding digit from the result.
4. Leave all other characters unchanged.

The process is identical for encryption and decryption.

### Decryption

Apply the exact same process to the ciphertext. Because (X + 5 + 5) mod 10 = X, the original digit is recovered.

### Mathematical Formula

**Encryption / Decryption**

$$
C = (P + 5) \bmod 10
$$

**Variables**

- **P** — numeric value of a plaintext/ciphertext digit (0–9)
- **C** — numeric value of the result (0–9)

### Worked Example

| Parameter | Value |
|-----------|-------|
| **Plaintext** | `1234 9876` |
| **Shift** | `5` |

| Transformation | Data |
|----------------|------|
| Plaintext digits | `1 2 3 4 9 8 7 6` |
| Add 5 mod 10 | 6 7 8 9 4 3 2 1 |
| Ciphertext | `6789 4321` |

Applying ROT5 again returns `1234 9876`.

```text
6789 4321  →  1234 9876
```
## Analysis

### Security

ROT5 offers zero cryptographic security; it is a trivial numeric substitution that can be reversed instantly by anyone who recognises it.

---

### Cryptanalysis

- **Direct reversal:** applying ROT5 again gives the original text.
- **Brute-force:** only 10 possible shifts exist for digits; trying them all is trivial.
- **Pattern recognition:** the presence of digits that map to “shifted” values (e.g., 6 ↔ 1, 7 ↔ 2) is an immediate giveaway.

---

### Recognition Patterns

- Only decimal digits are modified; letters and symbols stay unchanged.
- A known pair of digits (e.g., 9 → 4) reveals the shift.
- Often appears together with ROT13, where letters are garbled but digits follow a 5‑shift pattern.

---

## Similar Ciphers

### [[rot13-cipher]]

- **Similarity:** Both are fixed‑shift substitution ciphers that are their own inverses.
- **Difference:** ROT13 operates on the Latin alphabet (26 letters, shift 13), while ROT5 operates on decimal digits (10 symbols, shift 5).

### [[caesar-cipher]]

- **Similarity:** A generalisation that uses a shift value on an ordered alphabet; ROT5 is a specific case with a numeric alphabet.
- **Difference:** Caesar’s classic form applies to letters; ROT5’s alphabet is restricted to digits. The Caesar cipher can use any shift, but ROT5 is fixed.

---

## Variants

### [[ROT-18 Cipher]]

A common combination where letters are shifted by 13 (ROT13) and digits by 5 (ROT5) simultaneously. This covers the full set of alphanumeric characters, preserving case, and is also self‑inverse. It is frequently encountered in ARGs, CTFs, and online obfuscation. The name ROT18 reflects the sum of the two shift values (13 + 5), but each subset is rotated within its own modulus.

---

## Browser Tool

No dedicated ROT5‑only tool is maintained, but most [[Tool - ROT13 Cipher]] implementations include a “ROT5 for digits” option or a combined ROT13/ROT5 mode. The tool linked below supports full alphanumeric ROT13/ROT5 obfuscation.

### Features

- Apply ROT5 to digits independently
- Combine with ROT13 for full alphanumeric encoding
- Live preview

Tool:
[[Tool - ROT13 Cipher]]