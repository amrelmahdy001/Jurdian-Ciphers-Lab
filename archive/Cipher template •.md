---
title:
aliases:
type: Cipher · Encoding · Hash Function · Concept · Protocol · Analysis Method · Steganography · Compression · Writing System · Communication Code · Number System · Puzzle · Tool · Reference
class: Ancient · Classical · Mechanical · Modern
category: Substitution · Transposition · Fractionation · Product Cipher · Block Cipher · Stream Cipher · One-Time Pad
technique: Shift · Monoalphabetic · Polyalphabetic · Homophonic · Polygraphic · Rail Fence · Columnar · Route · Polybius Square · Matrix · Cipher Disk · Rotor Machine · Feistel · SPN · XOR · LFSR
character_support:
  - Uppercase
  - Lowercase
  - Numbers
  - Spaces
  - Punctuation
  - Symbols
  - Unicode
  - Binary 
key_count: None · 1 Key · 2 Keys · Multiple Keys
difficulty: ★☆☆☆☆ → ★★★★★
tags:
status: Draft · Review · Complete
created: 2026-06-30
updated: 2026-06-30
---

# Caesar Cipher

> **A simple substitution cipher where each letter is shifted by a fixed number of positions in the alphabet.**

> [!tip] Browser Tool
> [[Tool - Caesar Cipher]]


---

## Overview

Briefly explain what this cipher is, how it works at a high level, and what makes it unique.

A second paragraph can describe its historical importance, educational value, or role in modern puzzles and ARGs.

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

A short paragraph describing who created the cipher (if known), why it was developed, and its historical significance.

---

## How It Works

### Encryption

Explain the encryption process in a concise, easy-to-follow manner. Describe how the plaintext is transformed, how the key is applied, and any important rules required to produce the ciphertext.

---

### Decryption

Explain the decryption process, describing how the original plaintext is recovered from the ciphertext, how the key is used, and any important considerations.

---

### Mathematical Formula

Present the encryption and decryption formulas using LaTeX notation whenever possible.

**Encryption**

$$
C = ...
$$

**Decryption**

$$
P = ...
$$

**Variables**

- **P** — Plaintext
- **C** — Ciphertext
- **K** — Key
- Add any additional variables used by the algorithm.

Briefly explain the purpose of each variable.

---

### Worked Example

Demonstrate the complete encryption process using a simple example.

| Parameter | Value |
|-----------|-------|
| **Plaintext** | `...` |
| **Key** | `...` |

| Transformation | Data |
|--------|------|
| Input | |
| Step 1 | |
| Step 2 | |
| ... | |
| Output | |

**Result**

```text
...
```
## Analysis

### Security

Briefly describe how secure the cipher is and whether it should be used today.

---

### Cryptanalysis

List the primary attacks against this cipher and briefly explain why each is effective.

---

### Recognition Patterns

Describe the characteristics that help identify this cipher during puzzle solving.

Examples:

- Fixed letter shift
- Same plaintext always produces the same ciphertext
- Preserves spaces
- Uses only uppercase letters

---

## Similar Ciphers

### [[Cipher Name]]

- **Similarity:** Explain why someone might confuse this cipher with **{{title}}**.
- **Difference:** Explain the primary feature that distinguishes the two ciphers.

Repeat this section for each closely related cipher.

---

## Variants

### [[Variant Name]]

Briefly describe how this variant modifies the original cipher and what changes in its behavior.

---

## Browser Tool

If available, briefly describe the interactive implementation and its capabilities.

### Features

- Encrypt
- Decrypt
- Brute Force
- ...

Tool:
[[Tool - {{title}}]]