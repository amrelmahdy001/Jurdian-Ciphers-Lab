---
title: Consonants/Vowels Rank Cipher
aliases: C/V Cipher, Consonant-Vowel Substitution
type: Cipher
class: Classical
category: Substitution
technique: Monoalphabetic
character_support:
  - Uppercase
  - Lowercase
  - Spaces
key_count: None
difficulty: ★★☆☆☆
tags:
  - substitution
  - monoalphabetic
  - classical
  - puzzle
status: Complete
created: 2026-07-01
updated: 2026-07-01
---

# Consonants/Vowels Rank Cipher

> **A monoalphabetic substitution cipher where letters are replaced by a number indicating their rank within two separate sequences: consonants and vowels.**

> [!tip] Browser Tool
> No dedicated browser tool is currently available. Encoding and decoding are straightforward with manual lookup tables or simple scripts.

---

## Overview

The Consonants/Vowels Rank cipher separates the alphabet into two groups — vowels (A, E, I, O, U, sometimes Y) and consonants (the remainder) — and assigns a sequential number to each letter based on its position within its respective group. Plaintext letters are replaced by a pair consisting of a group identifier (C or V) and the rank number. Common variants use only the numeric rank, relying on the solver to determine whether a number refers to a consonant or vowel from context and word structure.

This cipher is not a historical cryptographic system but a puzzle‑community construction, frequently encountered in ARGs, riddle hunts, and CTF challenges. Its appeal lies in the constraint‑satisfaction aspect of decoding: the sequence of numbers must be partitioned into vowels and consonants to form valid words.

---
## Classification

This cipher belongs to the **Substitution** family and uses a **Monoalphabetic** technique, mapping each letter to a fixed numeric identifier within its phonetic class.

It is a **Classical**‑style cipher with no key, though variations may reclassify Y or include other letter groupings.

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

No single inventor or historical period is associated with this cipher. It emerged organically in online puzzle communities during the late 1990s and early 2000s, where creators sought lightweight, easily implemented ciphers that could be broken by logic rather than brute force. The consonant/vowel distinction is a natural linguistic feature that solvers recognise quickly, making the cipher accessible while still requiring a small analytical leap. It has no known use in historical espionage or serious cryptography.

---

## How It Works

### Encryption

1. Define the vowel set (typically A, E, I, O, U) and the consonant set (all remaining letters). Y may be treated as either a vowel or a consonant depending on the variant, or excluded entirely.
2. Assign sequential numbers to each set independently, starting from 1:
   - Vowels: A=1, E=2, I=3, O=4, U=5.
   - Consonants: B=1, C=2, D=3, F=4, G=5, H=6, J=7, K=8, L=9, M=10, N=11, P=12, Q=13, R=14, S=15, T=16, V=17, W=18, X=19, Y=20, Z=21. (If Y is excluded from consonants, the count adjusts accordingly.)
3. Replace each plaintext letter with its group prefix and rank number. Common output formats include:
   - Prefixed: `C14 V2 C9 C9 V4` for "HELLO"
   - Numeric‑only: `14 2 9 9 4` (solvers must deduce the C/V split)
   - Concatenated: `C14V2C9C9V4`

Non‑alphabetic characters are typically passed through unchanged.

### Decryption

1. If prefixes are present, decode each pair directly by looking up the rank in the appropriate list.
2. If only numbers are given, solvers must determine for each number whether it represents a consonant or a vowel. This is done by testing possible splits against known word patterns — any English word must contain at least one vowel and consonant‑only sequences cannot exceed a few letters.

### Mathematical Formula

The cipher is a direct index lookup; no modular arithmetic is involved.

**Encryption**

$$
\text{Output} = \text{Group}(L) + \text{Rank}_{\text{Group}}(L)
$$

**Decryption**

$$
L = \text{Table}^{-1}(\text{Group}, \text{Rank})
$$

**Variables**

- **L** — a plaintext or ciphertext letter
- **Group(L)** — either C (consonant) or V (vowel)
- **Rank** — the 1‑based index of L within its group

### Worked Example

| Parameter | Value |
|-----------|-------|
| **Plaintext** | `HELLO` |
| **Vowel Set** | A, E, I, O, U |
| **Consonant Set** | B, C, D, F, G, H, J, K, L, M, N, P, Q, R, S, T, V, W, X, Y, Z |
| **Output Format** | Prefixed (C/V + number) |

| Letter | Type | Rank | Output |
|--------|------|------|--------|
| H | Consonant | 6 | `C6` |
| E | Vowel | 2 | `V2` |
| L | Consonant | 9 | `C9` |
| L | Consonant | 9 | `C9` |
| O | Vowel | 4 | `V4` |

**Result**

```text
C6 V2 C9 C9 V4
```

## Analysis

### Security

This cipher provides no cryptographic security. It is a trivial substitution with a known, unkeyed mapping. Its use is purely recreational.

---

### Cryptanalysis

- **Direct lookup:** if prefixes are included, decoding is immediate with the standard ranking table.
- **Pattern analysis:** without prefixes, the small range of vowel ranks (1–5) versus consonant ranks (1–21) provides a strong clue. Numbers ≤5 might be vowels; the solver tests possible splits.
- **Word structure constraints:** English words require vowels. Any sequence of larger numbers must be broken by a small number (vowel) regularly, limiting the possible decodings to valid word patterns.
- **Known‑plaintext:** a single known word provides the complete mapping since the ranking is standardised.

---

### Recognition Patterns

- Ciphertext consists of numbers, optionally preceded by C or V.
- Numbers are relatively low: 1–5 for vowels, 1–21 for consonants.
- If prefixes are present, the alternating C/V pattern mirrors the consonant/vowel structure of English words.
- The total absence of numbers above 21 (or 20 if Y is treated as a vowel) strongly suggests this cipher.
- Spaces between numbers are typically preserved, maintaining visible word boundaries.

---

## Similar Ciphers

### [[A1Z26 Cipher]]

- **Similarity:** Both replace letters with numbers based on their position in an ordered sequence.
- **Difference:** A1Z26 uses a single numbering scheme across the entire alphabet (A=1, B=2, …, Z=26). The Consonants/Vowels Rank cipher splits the alphabet into two groups with independent numbering, creating smaller ranges and an inherent ambiguity that A1Z26 lacks.

### [[Polybius Square]]

- **Similarity:** Both encode each letter as a combination of identifiers (consonant/vowel prefix + number vs. row/column coordinate pair).
- **Difference:** Polybius uses a 5×5 grid with letter coordinates (e.g., 1–5 for rows and columns) and often incorporates a keyword. The C/V rank cipher uses phonetic categories with no grid or keyword.

### [[Binary Encoding]]

- **Similarity:** Some puzzles encode the consonant/vowel pattern of text as a binary string (consonant=0, vowel=1, or vice versa), which is conceptually related.
- **Difference:** Binary consonant/vowel encoding outputs only the pattern, discarding which specific consonant or vowel was used; the rank cipher preserves the specific letter identity.

---

## Variants

### [[Y‑Flexible Classification]]

Some implementations treat Y as a vowel when it functions phonetically as one (as in "MYTH" or "FLY"), adding complexity. The standard puzzle variant typically fixes Y as a consonant to avoid ambiguity.

### [[W‑as‑Vowel Inclusion]]

Rare variants include W as a vowel (inspired by Welsh or certain English diphthongs), expanding the vowel rank range to 6. This is almost never used without explicit indication.

### [[Numeric‑Only Ambiguous Output]]

The most common puzzle form: output consists solely of numbers, and the solver must deduce the consonant/vowel split. This turns the cipher into a logic puzzle as much as a decryption task.

### [[Extended Character Set Ranking]]

The same principle can be applied to other writing systems or custom symbol sets, ranking characters within predefined categories. This is occasionally seen in constructed language puzzles and sci‑fi ARGs.

---

## Browser Tool

No dedicated browser tool is currently available in the lab. Encoding and decoding are easily performed manually or with basic scripting. A future addition may include an interactive solver for numeric‑only ciphertexts that suggests possible consonant/vowel splits.

Tool:
None currently available.