---
title: ROT18
aliases: Rot18, ROT-18, alphanumeric rotation
type: Cipher
class: Classical
category: Substitution
technique: Shift
character_support:
  - Uppercase
  - Lowercase
  - Numbers
  - Spaces
key_count: None
difficulty: ★☆☆☆☆
tags:
  - substitution
  - shift
  - classical
  - alphanumeric
  - rot18
  - rot13
  - rot5
status: Complete
created: 2026-06-30
updated: 2026-06-30
---

# ROT18

> **A combined fixed‑shift substitution that applies ROT13 to letters and ROT5 to digits, covering all alphanumeric characters in one self‑inverse operation.**

> [!tip] Browser Tool
> ROT18 is commonly provided as a combined mode in [[Tool - ROT13 Cipher]].

---

## Overview

ROT18 is a trivial obfuscation cipher that processes alphanumeric text by applying two separate fixed rotations: a shift of 13 for Latin letters (A–Z, a–z) and a shift of 5 for decimal digits (0–9). Because 13 is half of 26 and 5 is half of 10, both transformations are their own inverses; applying ROT18 twice restores the original string entirely. No key selection is required.

ROT18 is not a cryptographic primitive. It appears almost exclusively in puzzles, online forums, CTF challenges, and ARGs as a lightweight method to mask text that contains both letters and numbers while preserving spaces and punctuation.

---
## Classification

This cipher belongs to the **Substitution** family and uses two independent **Shift** techniques on separate alphabets.

It is a **Classical Cipher** with a fixed dual transformation and no variable key.

---
## Character Support

| Character Type | Input | Output |
|----------------|:-----:|:------:|
| Uppercase (A–Z) | ✓ | ✓ |
| Lowercase (a–z) | ✓ | ✓ |
| Numbers (0–9) | ✓ | ✓ |
| Spaces | ✓ | ✓ |
| Punctuation | ✗ | ✗ |
| Symbols | ✗ | ✗ |
| Unicode | ✗ | ✗ |
| Binary | ✗ | ✗ |

All non‑alphanumeric characters remain untouched.

---

## History

ROT18 arose organically in online communities as a natural extension of [[ROT13]]; when obfuscating strings that contained digits (such as phone numbers, IP addresses, or numerical data), users combined the well‑known ROT13 with the digit‑only [[ROT5]]. The name “ROT18” comes from the sum of the two shift values (13 + 5 = 18), even though the rotations operate within separate moduli (26 for letters, 10 for digits). Its earliest usage is tied to early‑1990s Usenet and BBS culture, and it remains a popular tool in recreational cryptography.

---

## How It Works

### Encryption

The input is processed character by character:

- **Letters (A–Z, a–z):** apply ROT13 — add 13 to the letter’s 0‑based index modulo 26, preserving case.
- **Digits (0–9):** apply ROT5 — add 5 to the digit modulo 10.
- **All other characters (spaces, punctuation, symbols):** left unchanged.

Encryption and decryption are the same operation.

### Decryption

Apply the exact same process to the ciphertext. The original text is recovered because both component shifts are involutory (doing twice equals the identity).

### Mathematical Formula

**For letters (ROT13):**

$$
C = (P + 13) \bmod 26
$$

**For digits (ROT5):**

$$
C = (P + 5) \bmod 10
$$

**Variables**

- **P** — numeric value of the input character in its respective alphabet: for letters, A=0, B=1, …, Z=25; for digits, 0=0, 1=1, …, 9=9.  
- **C** — numeric value of the output character, mapped back to its original character set.

### Worked Example

| Parameter | Value |
|-----------|-------|
| **Plaintext** | `ABC 123 xyz 789` |
| **Shift (letters)** | `13` |
| **Shift (digits)** | `5` |

| Transformation      | Data                                          |
| ------------------- | --------------------------------------------- |
| Input               | `A B C  1 2 3  x y z  7 8 9`                  |
| Letters: +13 mod 26 | `N O P` (A→N, B→O, C→P) … `x→k`, `y→l`, `z→m` |
| Digits: +5 mod 10   | 1→6, 2→7, 3→8; 7→2, 8→3, 9→4                  |
| Final output        | `NOP 678 klm 234`                             |

**Result**

```text
NOP 678 klm 234
```
## Analysis

### Security

ROT18 provides zero real‑world security. It is a deterministic, keyless substitution that can be reversed immediately by anyone who knows the technique or uses an automated tool. It offers only casual obfuscation, not encryption.

---

### Cryptanalysis

- Direct reversal: applying ROT18 again restores the plaintext.
- Brute‑force: the letter part can be broken by trying the 25 possible Caesar shifts; the digit part is broken by trying all 10 digit shifts. Together, this is trivial.
- Known‑plaintext: one known alphanumeric mapping reveals the entire scheme.
- Pattern analysis: word boundaries, spaces, and punctuation are fully visible, aiding recognition.

---

### Recognition Patterns

- Spaces and punctuation remain unaltered; the output looks like jumbled letters and digits with the same word structure.
- All letters consistently map to letters shifted by 13 (e.g., ‘A’ ↔ ‘N’, ‘B’ ↔ ‘O’).
- All digits map to digits shifted by 5 (e.g., ‘0’ ↔ ‘5’, ‘1’ ↔ ‘6’).
- The combination of a ROT13-like text with obviously shifted digits strongly indicates ROT18.

---

## Similar Ciphers

### [[rot13-cipher]]

- **Similarity:** ROT18 includes ROT13 for the letter part; the letter transformation is identical.
- **Difference:** ROT13 ignores digits entirely, leaving them unchanged; ROT18 actively transforms digits as well.

### [[rot5-cipher]]

- **Similarity:** ROT18 uses ROT5 for the digit part; the digit transformation is identical.
- **Difference:** ROT5 only operates on digits and ignores letters; ROT18 does both in one pass.

### [[ROT47 cipher]]

- **Similarity:** ROT47 is a self‑inverse, fixed‑shift substitution that covers a broader character set including punctuation and symbols.
- **Difference:** ROT47 rotates a 94‑character ASCII range (33‑126) by 47 positions, handling nearly all printable characters, whereas ROT18 handles only letters and digits with separate moduli.

### [[caesar-cipher]]

- **Similarity:** The letter part of ROT18 is a specific Caesar shift (shift 13).
- **Difference:** Caesar cipher typically applies a single shift to letters only, with variable key; ROT18 uses a fixed dual‑alphabet transformation with no key.

---

## Variants

### [[rot13-cipher]] + [[rot5-cipher]]

Often simply referred to as “ROT18”, this combination is a de facto standard in puzzles. Some implementations allow toggling ROT13 and ROT5 independently, but the combined mode is ROT18.

### [[ROT47]]

A single‑modulus rotation that covers letters, digits, and common punctuation in one sweep. For environments where the full printable ASCII set must be obfuscated, ROT47 is preferred over ROT18.

---

## Browser Tool

Most online ROT13 tools include a checkbox for “ROT5 digits” or a dedicated “ROT18” mode. The linked tool below supports combined ROT13/ROT5 (ROT18) operation, along with separate ROT13, ROT5, and ROT47 modes.

### Features

- Combined ROT13 (letters) + ROT5 (digits) in one step
- Toggle digit rotation on/off
- Live preview
- Copy‑to‑clipboard

Tool:
[[Tool - ROT13 Cipher]]