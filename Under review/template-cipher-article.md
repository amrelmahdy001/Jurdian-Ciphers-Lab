---
# ─── IDENTIFICATION ──────────────────────────────────────────────
title: "{{title}}"
aliases:
  - "{{alias_1}}"
  - "{{alias_2}}"

# ─── CLASSIFICATION ──────────────────────────────────────────────
type: cipher
category: "classical"
subcategory: "shift"
# subcategory options: shift | monoalphabetic | polyalphabetic | homophonic |
#                      polygraphic | symbolic | transposition | fractionation |
#                      mechanical | block | stream

domain: "ciphers/classical/shift"

# ─── ATTRIBUTES ──────────────────────────────────────────────────
difficulty: "beginner"
# options: beginner | intermediate | advanced | expert

status: stub
# options: stub | draft | review | complete

# ─── HISTORICAL CONTEXT ──────────────────────────────────────────
inventor: ""
year_invented: 
era: ""
# era options: ancient | medieval | renaissance | 17th-century | 18th-century |
#              19th-century | ww1 | ww2 | cold-war | modern

# ─── CIPHER PROPERTIES ───────────────────────────────────────────
cipher_family: ""
key_type: ""
# key_type options: none | numeric | alphabetic | keyword | key-matrix |
#                   key-stream | asymmetric | passphrase

key_length: ""
plaintext_type: text
ciphertext_type: text
variant_of: ""
broken: true

# ─── CROSS-REFERENCES ────────────────────────────────────────────
related:
  - "[[]]"

tool_available: false
tool_link: ""

# ─── TAGS ────────────────────────────────────────────────────────
tags:
  - cipher
  - classical
  - shift
  - beginner

# ─── METADATA ────────────────────────────────────────────────────
created: 2025-01-01
updated: 2025-01-01
author: ""
version: "1.0"
---

# {{title}}

> **One-line summary.** Describe what this cipher does in a single plain-English sentence.

> [!info] Classical Cipher
> This is a classical cipher intended for education, puzzles, and historical study.

---

## Overview

A brief 2–3 paragraph introduction covering what this cipher is, which family it belongs to, why it was invented, and why it matters historically or in modern puzzle contexts.

---

## Classification

| Property | Value |
|---|---|
| **Type** | Cipher |
| **Era** | |
| **Family** | [[ ]] |
| **Subcategory** | |
| **Variant of** | [[ ]] |
| **Key type** | |
| **Key length** | |
| **Cryptographically broken?** | |

---

## History

- **Inventor:** 
- **Year invented:** 
- **Original purpose:** 
- **Notable uses:** 

Narrative history. 2–4 paragraphs covering invention, adoption, historical use, and eventual obsolescence or modern relevance.

---

## How It Works

### Encryption Process

Step-by-step explanation of how to encrypt a message.

1. Step one.
2. Step two.
3. Step three.

#### Mathematical Formula

```
C = (P + K) mod 26
```

Where:
- `C` = ciphertext letter index (A=0, B=1, ... Z=25)
- `P` = plaintext letter index
- `K` = key value

### Decryption Process

Step-by-step explanation of how to decrypt.

#### Mathematical Formula

```
P = (C - K + 26) mod 26
```

---

## Worked Example

**Plaintext:** `HELLO WORLD`
**Key:** `3`

| Plain  | H  | E  | L  | L  | O  | W  | O  | R  | L  | D  |
|--------|----|----|----|----|----|----|----|----|----|----|
| Index  | 7  | 4  | 11 | 11 | 14 | 22 | 14 | 17 | 11 | 3  |
| + Key  | 10 | 7  | 14 | 14 | 17 | 25 | 17 | 20 | 14 | 6  |
| Cipher | K  | H  | O  | O  | R  | Z  | R  | U  | O  | G  |

**Ciphertext:** `KHOOR ZRUOG`

---

## Variants & Related Ciphers

| Variant | Difference |
|---|---|
| [[Related Cipher A]] | How it differs |
| [[Related Cipher B]] | How it differs |

---

## Security Analysis

### Strengths

- Point 1.

### Weaknesses

- Point 1.

> [!warning] Cryptographically Broken
> This cipher **must not be used** for real-world security. It is presented for historical and educational purposes only.

---

## Cryptanalysis

### Primary Attack: [[Frequency Analysis]]

With a key space of only 25 possible shifts, this cipher is broken by trivial brute force or single-letter frequency analysis.

### Secondary Attack: [[Brute Force Attack]]

A modern computer can test all possible keys in microseconds.

---

## Historical Usage

Notable documented uses of this cipher.

---

## Modern Applications

Where this cipher appears today — education, CTF challenges, puzzle design.

---

## Interactive Tool

> [!tip] Tool Available
> [[Tool - Caesar Cipher]] — Encrypt, decrypt, and brute-force this cipher in your browser.

---

## Related Articles

- [[MOC-Shift-Ciphers]] — Index of all shift ciphers
- [[Frequency Analysis]] — Primary attack
- [[Affine Cipher]] — Mathematical generalisation
- [[Vigenère Cipher]] — Polyalphabetic evolution

---

## References

1. Author, *Title*, Publisher, Year.

## External Resources

- [Link](url) — Description.
