---
title: Caesar Cipher
aliases: Shift Cipher
type: Cipher
class: Classical
category: Substitution
technique: Shift
character_support:
  - Uppercase
  - Lowercase
  - Spaces
key_count: 1 Key
difficulty: ★☆☆☆☆
tags:
  - substitution
  - shift
  - classical
  - monoalphabetic
status: Complete
created: 2026-06-30
updated: 2026-06-30
---

# Caesar Cipher

> **A simple substitution cipher where each letter is shifted by a fixed number of positions in the alphabet.**

> [!tip] Browser Tool
> [[Tool - Caesar Cipher]]

---

## Overview

The Caesar cipher is a monoalphabetic substitution cipher that replaces each letter in the plaintext with a letter located a fixed number of positions later in the alphabet. The shift amount, an integer typically between 1 and 25, serves as the key. When shifting causes the alphabet’s end to be exceeded, the mapping wraps around to the beginning.

Its historical use by Julius Caesar (shift of 3) makes it one of the oldest known ciphers. Today it is almost exclusively an educational example and a staple in puzzles, CTF challenges, and ARGs, demonstrating fundamental cryptographic concepts such as key space, brute‑force attacks, and frequency analysis.

---
## Classification

This cipher belongs to the **Substitution** family and specifically uses the **Shift** technique.

It is a **Classical Cipher** designed for manual encryption using a single numeric key.

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

Named after Julius Caesar, who employed it with a shift of 3 for securing military dispatches. The cipher is attested in Suetonius’ *Lives of the Caesars*. Its simplicity made it practical for manual encryption in ancient times. Over the centuries it became the archetypal classical cipher and a stepping‑stone in the study of cryptography.

---

## How It Works

### Encryption

For each letter in the plaintext:
1. Convert the letter to its numeric position (A=0, B=1, …, Z=25).
2. Add the key (the shift value) and take the result modulo 26.
3. Convert the resulting number back to a letter, preserving the original case.

Non‑alphabetic characters, such as spaces, are left unchanged. The alphabet is treated as circular: after Z comes A.

### Decryption

Decryption reverses the process by subtracting the key modulo 26. Equivalently, one can encrypt using the complementary shift (26 − key). The same case‑preservation and non‑letter handling rules apply.

### Mathematical Formula

**Encryption**

$$
C = (P + K) \bmod 26
$$

**Decryption**

$$
P = (C - K) \bmod 26
$$

**Variables**

- **P** — numerical value of a plaintext letter (A=0, B=1, …, Z=25)  
- **C** — numerical value of the corresponding ciphertext letter  
- **K** — the key (shift value, 1 ≤ K ≤ 25)

Lowercase letters can be handled identically by using the same numeric mapping or by treating ‘a’ as 0; the formulas remain unchanged as long as the output letter is returned to the correct case.

### Worked Example

| Parameter | Value |
|-----------|-------|
| **Plaintext** | `HELLO WORLD` |
| **Key** | `3` |

| Transformation | Data |
|----------------|------|
| Plaintext | `HELLO WORLD` |
| Convert to numeric (A=0) | 7 4 11 11 14 (space) 22 14 17 11 3 |
| Add key (3) mod 26 | 10 7 14 14 17 (space) 25 17 20 14 6 |
| Convert back to letters | K H O O R (space) Z R U O G |
| Ciphertext | `KHOOR ZRUOG` |

**Result**

```text
KHOOR ZRUOG
```

## Analysis

### Security

The Caesar cipher offers no security by modern standards. Its key space consists of only 25 possible shifts, making brute‑force exhaustive search trivial. It can be broken instantly with pen and paper or by a simple computer program.

---

### Cryptanalysis

- **Brute‑force attack:** Trying all 25 shifts immediately reveals the plaintext.
- **Frequency analysis:** The letter distribution is preserved; the most frequent ciphertext letter almost always corresponds to ‘E’ (or the language’s most common letter).
- **Known‑plaintext attack:** A single known letter mapping gives the key directly (K = C − P mod 26).

---

### Recognition Patterns

- Only alphabetic characters are transformed; spaces and other symbols either remain or are omitted.
- The same plaintext letter always encrypts to the same ciphertext letter (monoalphabetic).
- The relative positions of letters are preserved; a fixed offset is visually apparent in simple substitution puzzles.
- Word boundaries are usually visible, aiding identification.

---

## Similar Ciphers

### [[ROT13]]

- **Similarity:** Both are shift ciphers operating on the Latin alphabet.
- **Difference:** ROT13 uses a fixed shift of 13 and is its own inverse; encryption and decryption are identical. The Caesar cipher can use any shift value.

### [[Vigenère Cipher]]

- **Similarity:** Vigenère is built from multiple interleaved Caesar shifts.
- **Difference:** Vigenère employs a keyword to vary the shift per letter, making it polyalphabetic and resistant to simple frequency analysis.

### [[Atbash Cipher]]

- **Similarity:** Both are monoalphabetic substitution ciphers that map letters one‑to‑one.
- **Difference:** Atbash reverses the alphabet (A↔Z, B↔Y, …), which is not a uniform shift and does not use a numeric key.

---

## Variants

### [[ROT13]]

A fixed shift of 13, making encryption and decryption the same operation. It is frequently used for obfuscation in online forums, puzzle hunts, and as a quick way to hide spoilers.

---

## Browser Tool

A browser‑based interactive tool for the Caesar cipher is available, providing encryption, decryption, and brute‑force analysis with adjustable shift and case handling.

### Features

- Encrypt
- Decrypt
- Brute Force (try all shifts)
- Preserve or ignore non‑alphabetic characters
- Case‑sensitive mode

Tool: [[Tool - Caesar Cipher]]