---
title: Affine Cipher
aliases: Affine substitution
type: Cipher
class: Classical
category: Substitution
technique: Monoalphabetic
character_support:
  - Uppercase
  - Lowercase
  - Spaces
key_count: 2 Keys
difficulty: ★★☆☆☆
tags:
  - substitution
  - monoalphabetic
  - classical
  - affine
status: Complete
created: 2026-07-01
updated: 2026-07-01
---

# Affine Cipher

> **A monoalphabetic substitution cipher that combines multiplication and addition to determine the shift for each letter, using two independent keys.**

> [!tip] Browser Tool
> [[Tool - Affine Cipher]]

---

## Overview

The affine cipher encrypts each letter using the mathematical function (ax + b) mod 26, where x is the plaintext letter’s numeric value, and a and b are the two keys. The multiplication by a, followed by the shift b, produces a scrambling that goes beyond a simple uniform shift. The key a must be coprime with 26 for the cipher to be reversible.

Because the same function is applied to every occurrence of a letter, the cipher is still monoalphabetic and susceptible to frequency analysis. It serves as a natural next step after the [[Caesar Cipher]] in educational contexts, introducing modular inverses and the concept of key space constraints. It also appears regularly in puzzle hunts and ARGs where an unknown substitution must be broken by solving for two parameters.

---
## Classification

This cipher belongs to the **Substitution** family and uses a **Monoalphabetic** technique with a two‑part arithmetic transformation.

It is a **Classical Cipher** designed for manual encryption using two keys.

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

The affine cipher has no single named inventor; it evolved as a natural generalisation of the [[Caesar Cipher]] when cryptographers explored combining multiplication and addition in modular systems. It became a standard topic in classical cryptography textbooks during the 20th century, valued for illustrating modular arithmetic, coprimality, and the limitations of monoalphabetic ciphers. Its historical military use is undocumented, as it offers little practical advantage over simpler shifts.

---

## How It Works

### Encryption

Each plaintext letter is converted to a number (A=0, B=1, …, Z=25). Two keys are chosen:

- **a** (multiplier): must be coprime with 26 (possible values: 1, 3, 5, 7, 9, 11, 15, 17, 19, 21, 23, 25).
- **b** (additive shift): any integer from 0 to 25.

The encryption formula E(x) = (a·x + b) mod 26 is applied to each letter. Non‑alphabetic characters are left unchanged. Case is typically preserved.

### Decryption

To reverse, the modular multiplicative inverse of a modulo 26, denoted a⁻¹, must be found such that a·a⁻¹ ≡ 1 (mod 26). Decryption then uses the formula D(y) = a⁻¹·(y − b) mod 26. Because a must be coprime with 26, the inverse always exists.

### Mathematical Formula

**Encryption**

$$
C = (a \cdot P + b) \bmod 26
$$

**Decryption**

$$
P = a^{-1} \cdot (C - b) \bmod 26
$$

**Variables**

- **P** — numeric value of a plaintext letter (A=0, B=1, …, Z=25)
- **C** — numeric value of the corresponding ciphertext letter
- **a** — multiplicative key; must be coprime with 26 (gcd(a, 26) = 1)
- **b** — additive key (0 ≤ b ≤ 25)
- **a⁻¹** — modular multiplicative inverse of a modulo 26

### Worked Example

| Parameter | Value |
|-----------|-------|
| **Plaintext** | `HELLO WORLD` |
| **a** | `5` |
| **b** | `8` |

| Letter | P | 5·P + 8 | (5·P + 8) mod 26 | Ciphertext |
|--------|---|---------|------------------|------------|
| H | 7 | 43 | 17 | `R` |
| E | 4 | 28 | 2 | `C` |
| L | 11 | 63 | 11 | `L` |
| L | 11 | 63 | 11 | `L` |
| O | 14 | 78 | 0 | `A` |
| (space) | – | – | – | (space) |
| W | 22 | 118 | 14 | `O` |
| O | 14 | 78 | 0 | `A` |
| R | 17 | 93 | 15 | `P` |
| L | 11 | 63 | 11 | `L` |
| D | 3 | 23 | 23 | `X` |

**Result**

```text
RCLLA OAPLX
```

## Analysis

### Security

The affine cipher is not secure. Its key space is limited to φ(26)·26 = 12·26 = 312 possible key pairs, making brute‑force trivial. It is monoalphabetic, so frequency analysis breaks it quickly.

---

### Cryptanalysis

- **Brute‑force attack:** testing all 312 possible (a, b) pairs is instantaneous with a computer.
- **Frequency analysis:** the cipher preserves letter frequencies; the most common ciphertext letters can be mapped to ‘E’, ‘T’, etc., yielding two equations to solve for a and b.
- **Known‑plaintext attack:** two known letter mappings are sufficient to solve for a and b via simultaneous equations modulo 26.
- **Ciphertext‑only probable‑word attack:** guessing a common word (e.g., "THE") and testing all positions reveals the mapping.

---

### Recognition Patterns

- Ciphertext is limited to uppercase or lowercase letters; spaces and punctuation are unchanged.
- The same plaintext letter always encrypts to the same ciphertext letter.
- The index of coincidence matches the underlying language, indicating a monoalphabetic substitution.
- The mapping does not follow a simple shifted alphabet pattern, ruling out the pure [[Caesar Cipher]].

---

## Similar Ciphers

### [[Caesar Cipher]]

- **Similarity:** The Caesar cipher is a special case of the affine cipher with a=1; both are monoalphabetic substitutions using modular arithmetic.
- **Difference:** The Caesar cipher uses only a single additive key; the affine cipher adds a multiplicative component, increasing the key space and scrambling the alphabet more thoroughly.

### [[Atbash Cipher]]

- **Similarity:** Atbash is an affine cipher with a=25, b=25 (since C = −x − 1 mod 26). Both are involutory under certain parameter choices.
- **Difference:** Atbash has fixed parameters and no key selection; the affine cipher allows variable a and b within coprimality constraints.

### [[Multiplicative Cipher]]

- **Similarity:** The multiplicative cipher is an affine cipher with b=0. Both rely on a multiplicative key that must be coprime with the modulus.
- **Difference:** The affine cipher combines both multiplication and addition; the multiplicative cipher uses only the multiplication step, making it a simpler and even weaker variant.

---

## Variants

### [[Atbash Cipher]]

An affine cipher with a=25 and b=25. It reverses the alphabet and is its own inverse. It is the best‑known fixed‑parameter instance of the affine family.

### [[Multiplicative Cipher]]

Sets b=0, so C = a·P mod 26. Even weaker than the full affine cipher because the letter ‘A’ (P=0) always maps to ‘A’, providing an immediate crib.

### [[Affine Cipher on Extended Alphabets]]

The same principle can be applied to larger character sets (e.g., alphanumeric, 256‑byte ASCII) as long as the multiplicative key is coprime with the modulus. This generalisation is rarely used in practice but appears occasionally in programming exercises.

---

## Browser Tool

A dedicated interactive tool allows encryption, decryption, and brute‑force key recovery for the affine cipher.

### Features

- Encrypt with chosen a and b
- Decrypt with known a and b
- Brute Force (try all valid key pairs)
- Display the full substitution alphabet
- Case‑sensitive and ignore‑non‑alpha modes

Tool:
[[Tool - Affine Cipher]]