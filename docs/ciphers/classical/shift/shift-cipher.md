---
title: Shift Cipher
aliases: Caesar Cipher, Additive Cipher
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

# Shift Cipher

> **A family of monoalphabetic substitution ciphers where each letter is replaced by another letter a fixed number of positions away in the alphabet.**

> [!tip] Browser Tool
> [[Tool - Caesar Cipher]]

---

## Overview

The shift cipher is the simplest classical encryption scheme. It operates by “shifting” every letter in the plaintext by a constant amount (the **key**) along the standard ordering of the alphabet. When the shift reaches the end, it wraps back to the beginning. The best‑known instance is the [[caesar-cipher]], which traditionally uses a shift of three.

Because its key space is limited to 25 non‑trivial values, the shift cipher offers no security today. However, its simplicity makes it the standard introduction to cryptography, cryptanalysis, and the concepts of modular arithmetic, keys, and brute‑force attacks.

---
## Classification

This cipher belongs to the **Substitution** family and specifically uses the **Shift** technique.

It is a **Classical Cipher** designed for manual encryption, employing a single numeric key.

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

Most implementations ignore non‑alphabetic characters or pass them through unchanged. Some variants extend the shift to digits or other character sets, but the core shift cipher only processes letters.

---

## History

The shift cipher is named after Julius Caesar, who used a key of three for confidential military correspondence. The concept is ancient and appears in other cultures as well, but it gained its most famous association from Suetonius’ description of Caesar’s communications. For centuries it remained a trivial but practical method until the development of frequency analysis rendered it obsolete. Today it is used exclusively for educational purposes, puzzle hunts, and ARGs.

---

## How It Works

### Encryption

1. Map each plaintext letter to a number: A → 0, B → 1, …, Z → 25.
2. Add the key value to each number.
3. Reduce the result modulo 26.
4. Map the number back to a letter (0 → A, 1 → B, …).
5. Non‑alphabetic characters are left as they are.

Lowercase letters are treated identically, either by converting them to the same numeric range or by preserving case after the operation.

### Decryption

Decryption subtracts the key modulo 26. Equivalently, one can encrypt with the complementary key (26 − key). The process is otherwise identical.

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

- **P** — numeric value of a plaintext letter (A=0, B=1, …, Z=25)
- **C** — numeric value of the corresponding ciphertext letter
- **K** — the shift key (1 ≤ K ≤ 25)

### Worked Example

| Parameter | Value |
|-----------|-------|
| **Plaintext** | `HELLO WORLD` |
| **Key** | `7` |

| Transformation | Data |
|----------------|------|
| Plaintext | `H E L L O (space) W O R L D` |
| Numeric (A=0) | 7 4 11 11 14 (space) 22 14 17 11 3 |
| Add key (7) mod 26 | 14 11 18 18 21 (space) 3 21 24 18 10 |
| Convert to letters | O L S S V (space) D V Y S K |
| Ciphertext | `OLSSV DVYSK` |

**Result**

```text
OLSSV DVYSK
```

## Analysis

### Security

A shift cipher provides no security in any modern context. The key space is only 25, so an attacker can try every possible key by hand in a few minutes. It is entirely broken by brute force or frequency analysis.

---

### Cryptanalysis

- **Brute-force attack:** enumerating all 25 shifts immediately reveals the plaintext.
- **Frequency analysis:** the relative frequency of letters is preserved, allowing the key to be deduced from the most common ciphertext letter (usually matching the letter ‘E’ in English).
- **Known-plaintext attack:** one known letter pair (e.g., P and C) gives K = (C − P) mod 26 directly.

---

### Recognition Patterns

- Only letters are altered; spaces and punctuation are unchanged, so word lengths remain apparent.
- Every occurrence of a given plaintext letter maps to the same ciphertext letter.
- Ciphertext alphabet is simply the plaintext alphabet rotated; the same relative letter frequencies appear.
- Simple tools can test all 25 keys instantly and find readable output.

---

## Similar Ciphers

### [[ROT13]]

- **Similarity:** A specific shift cipher with K=13; the encryption and decryption algorithms are identical because shifting twice returns the original text.
- **Difference:** ROT13 has no key selection – it is an involution with a fixed shift. The general shift cipher requires a key.

### [[Atbash Cipher]]

- **Similarity:** Both are monoalphabetic substitutions on the Latin alphabet.
- **Difference:** Atbash maps A↔Z, B↔Y, etc., which is not a uniform shift. It can be seen as an affine cipher with parameters a=25, b=25.

### [[Vigenère Cipher]]

- **Similarity:** Vigenère uses multiple interleaved shift ciphers, each with a different key letter.
- **Difference:** The shift changes with each character, making it polyalphabetic and resistant to simple frequency analysis.

---

## Variants

### [[caesar-cipher]]

The most famous variant, originally using K=3. The term “Caesar cipher” is often used interchangeably with “shift cipher”, though strictly it refers to the fixed‑key version.

### [[ROT5]]

Generalised rotation that operates on digits only, using a fixed shift of 5 modulo 10.

### [[ROT18]]

Generalised rotation that applies ROT13 to letters and ROT5 to digits simultaneously, using two different moduli.

### [[ROT47]]

Generalised rotation that shifts all printable ASCII characters (94 symbols) by a fixed offset of 47, covering letters, digits, and punctuation.

---

## Browser Tool

A browser‑based tool for shift ciphers allows encryption, decryption, and automatic brute‑force analysis. The user can set any key or scan all possibilities.

### Features

- Encrypt with a chosen key
- Decrypt with a known key
- Brute Force (try all 25 keys)
- Case‑sensitive mode
- Live preview

Tool:
[[Tool - Caesar Cipher]]