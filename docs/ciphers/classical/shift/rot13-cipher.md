---
title: ROT13
aliases: Rot13, ROT-13, Caesar cipher with shift 13
type: Cipher
class: Classical
category: Substitution
technique: Shift
character_support:
  - Uppercase
  - Lowercase
  - Spaces
key_count: None
difficulty: ★☆☆☆☆
tags:
  - substitution
  - shift
  - classical
  - monoalphabetic
  - rot13
status: Complete
created: 2026-06-30
updated: 2026-06-30
---

# ROT13

> **A Caesar cipher with a fixed shift of 13 that is its own inverse – applying it twice returns the original text.**

> [!tip] Browser Tool
> [[Tool - ROT13 Cipher]]

---

## Overview

ROT13 (short for “rotate by 13 places”) is a specific case of the [[caesar-cipher]] where the shift is always exactly 13 positions. Because the Latin alphabet has 26 letters, a second application of ROT13 cancels the first, making encryption and decryption the same operation. This property simplifies its use: no key selection or separate decrypt function is needed.

Widely adopted on Usenet and later in online forums, ROT13 serves not for security but for casual obfuscation – hiding spoilers, punchlines, or potentially offensive content behind a trivially reversible substitution. It remains a staple in puzzle hunts, CTFs, and introductory cryptography exercises.

---
## Classification

This cipher belongs to the **Substitution** family and specifically uses the **Shift** technique.

It is a **Classical Cipher** with no variable key; the shift is fixed at 13.

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

ROT13 emerged in the early 1980s within the Usenet community as a quick method to mask potentially offensive or spoiler-laden content. The choice of shift 13 was deliberate: it allows a single operation to both hide and reveal the text, and the resulting ciphertext appears as a jumble of letters rather than common punctuation, which might be filtered or misinterpreted by early newsreaders. Today it is universally known and frequently used as a light‑hearted cipher in puzzles, internet memes, and programming tutorials.

---

## How It Works

### Encryption

1. For each alphabetic character, convert it to a number (A=0, B=1, …, Z=25; lowercase a=0, b=1, …).
2. Add 13 and take the result modulo 26.
3. Convert back to a letter, preserving the original case.

All non‑alphabetic characters (spaces, digits, punctuation) remain untouched. Because 13 + 13 ≡ 0 (mod 26), encryption and decryption are identical.

### Decryption

Decryption is performed by the exact same process: apply ROT13 to the ciphertext. The original plaintext is recovered.

### Mathematical Formula

**Encryption / Decryption**

$$
C = (P + 13) \bmod 26
$$

**Variables**

- **P** — numeric value of a plaintext/ciphertext letter (A=0, B=1, …, Z=25)  
- **C** — numeric value of the result  

No key variable is needed, as the shift is constant.

### Worked Example

| Parameter | Value |
|-----------|-------|
| **Plaintext** | `HELLO WORLD` |
| **Shift** | `13` |

| Transformation | Data |
|----------------|------|
| Plaintext | `HELLO WORLD` |
| Numeric (A=0) | 7 4 11 11 14 (space) 22 14 17 11 3 |
| Add 13 mod 26 | 20 17 24 24 1 (space) 9 1 4 24 16 |
| Convert to letters | U R Y Y B (space) J B E Y Q |
| Ciphertext | `URYYB JBEYQ` |

Applying ROT13 to the ciphertext returns `HELLO WORLD`:

```text
URYYB JBEYQ  →  HELLO WORLD
```
## Analysis

### Security

ROT13 provides no meaningful security. Anyone who recognises it can instantly reverse it with the same operation. It is not a cryptographic algorithm but a trivial obfuscation technique.

---

### Cryptanalysis

- **Direct reversal:** applying ROT13 to the ciphertext immediately yields the plaintext.
- **Brute‑force:** trying all 25 Caesar shifts will also reveal the content; ROT13 is just one of them.
- **Frequency analysis:** letter frequencies are preserved, so the most common ciphertext letter maps to ‘E’/‘e’, etc.
- **Pattern recognition:** word boundaries and word lengths are visible, and repeated letters remain consistent.

---

### Recognition Patterns

- Only letters A–Z and a–z are altered; everything else is unchanged.
- The same letter always maps to the same substitute (e.g., all ‘A’ become ‘N’).
- A ROT13 text often looks like garbled English with preserved spaces and punctuation.
- Applying ROT13 to a suspected ROT13 string produces readable English, confirming the encoding.

---

## Similar Ciphers

### [[caesar-cipher]]

- **Similarity:** ROT13 is exactly a Caesar cipher with a fixed shift of 13; the mechanical process is identical.
- **Difference:** The Caesar cipher can use any shift value, while ROT13 is locked to 13, giving it the unique self‑inverse property.

### [[Atbash Cipher]]

- **Similarity:** Both are fixed, monoalphabetic substitutions operating on the alphabet with no key.
- **Difference:** Atbash maps A↔Z, B↔Y, etc., which is not a uniform shift, and is not self‑inverse in the modular‑addition sense.

---

## Variants

### [[ROT5]]

A numeric variant that rotates digits 0–9 by 5. It is often combined with ROT13 to obfuscate alphanumeric data (e.g., ROT13 for letters, ROT5 for digits). Like ROT13, it is self‑inverse.

### [[ROT47]]

Rotates a larger set of printable ASCII characters (33 `!` to 126 `~`) by 47 positions. This covers letters, digits, and common punctuation. ROT47 is also self‑inverse and is used for simple obfuscation of strings that include special characters.

---

## Browser Tool

A dedicated interactive tool allows instant encoding and decoding, with options for letter‑only ROT13 as well as combined rotations (ROT5, ROT47).

### Features

- Encode / Decode (same action)
- Auto‑apply ROT13 to input
- Optional ROT5 for digits
- Optional ROT47 for full ASCII
- Live preview

Tool: [[Tool - ROT13 Cipher]]