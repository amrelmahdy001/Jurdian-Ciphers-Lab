---
title: ROT47
aliases: Rot-47, ASCII rotation
type: Cipher
class: Classical
category: Substitution
technique: Shift
character_support:
  - Uppercase
  - Lowercase
  - Numbers
  - Spaces
  - Punctuation
  - Symbols
key_count: None
difficulty: ★☆☆☆☆
tags:
  - substitution
  - shift
  - ascii
  - rot47
  - obfuscation
status: Complete
created: 2026-06-30
updated: 2026-06-30
---

# ROT47

> **A self‑inverse shift cipher that rotates the 94 printable ASCII characters (excluding space) by 47 positions.**

> [!tip] Browser Tool
> ROT47 is frequently included in [[Tool - ROT13 Cipher]] implementations that support multiple rotation modes.

---

## Overview

ROT47 is a fixed‑shift substitution cipher operating on almost all printable ASCII characters: the range from `!` (ASCII 33) to `~` (ASCII 126), a total of 94 symbols. Each character in that set is replaced by the character that is 47 positions ahead, wrapping around. Because 47 is exactly half of 94, applying ROT47 twice returns the original text — it is its own inverse.

Its main use is lightweight obfuscation in online forums, CTFs, and puzzles, where it hides text that includes letters, digits, punctuation, and other special characters in a single step, without the need for separate letter and digit rotations.

---
## Classification

This cipher belongs to the **Substitution** family and uses the **Shift** technique on an extended, ordered character set.

It is a **Classical** monoalphabetic cipher with a fixed shift and no variable key.

---
## Character Support

| Character Type | Input | Output |
|----------------|:-----:|:------:|
| Uppercase (A–Z) | ✓ | ✓ |
| Lowercase (a–z) | ✓ | ✓ |
| Numbers (0–9) | ✓ | ✓ |
| Spaces | ✓ | ✓ |
| Punctuation | ✓ | ✓ |
| Symbols | ✓ | ✓ |
| Unicode | ✗ | ✗ |
| Binary | ✗ | ✗ |

The space character (ASCII 32) is **not** transformed; it passes through unchanged. All other characters in the range 33–126 are rotated. Characters outside this range (control characters, extended ASCII, Unicode) are left untouched.

---

## History

ROT47 evolved in the same early‑internet communities that gave rise to [[rot13-cipher]] and [[rot5-cipher]]. As users needed to obfuscate strings containing punctuation, special characters, and mixed case, the 94‑character printable ASCII set became a natural target. Shift 47 was chosen to preserve the self‑inverse property. The cipher gained popularity in hacker and puzzle circles and is regularly encountered in ARG puzzles, online riddle platforms, and as a simple example of character‑set rotation.

---

## How It Works

### Encryption

1. For each character in the input:
   - If the character’s ASCII code is between 33 (`!`) and 126 (`~`) inclusive:
     - Subtract 33 to get a 0‑based index in the range 0–93.
     - Add 47 (the shift), take the result modulo 94.
     - Add 33 to map back to the target character.
   - Otherwise (space, control characters, Unicode, etc.), leave the character unchanged.

Because the shift is exactly half the set size, encryption and decryption are the same operation.

### Decryption

Apply the identical process. The second rotation cancels the first, restoring the original plaintext.

### Mathematical Formula

**Encryption / Decryption**

$$
C = \big( (P - 33) + 47 \big) \bmod 94 + 33
$$

**Variables**

- **P** — ASCII value of a plaintext or ciphertext character, 33 ≤ P ≤ 126  
- **C** — ASCII value of the resulting character, within the same range  

Characters outside this range are passed through as-is.

### Worked Example

| Parameter | Value |
|-----------|-------|
| **Plaintext** | `Hello, World!` |
| **Shift** | `47` |

| Transformation | Data |
|----------------|------|
| Input characters | `H e l l o , (space) W o r l d !` |
| ASCII codes | 72 101 108 108 111 44 32 87 111 114 108 100 33 |
| (P − 33 + 47) mod 94 + 33 | `w` (119) `6` (54) `=` (61) `=` (61) `@` (64) `[` (91) (space→space) `(` (40) `@` (64) `C` (67) `=` (61) `5` (53) `P` (80) |
| Ciphertext | `w6==@ (@C=5P` |

**Result**

```text
w6==@[ (@C=5P
```

## Analysis

### Security

ROT47 provides no cryptographic security. It is a deterministic, keyless substitution that can be instantly reversed with the same algorithm or a single lookup table.

---

### Cryptanalysis

- Direct reversal: applying ROT47 again immediately yields the plaintext.
- Brute‑force: testing all 94 possible shifts is trivial; knowing that 47 is the half‑way point makes the attack even simpler.
- Known‑plaintext attack: a single known character mapping (e.g., ! ↔ P) reveals the entire transformation.

---

### Recognition Patterns

- Ciphertext consists exclusively of printable ASCII characters, often appearing as a jumble of letters, digits, and symbols.
- Spaces remain unchanged, preserving word boundaries and giving away the encoding.
- All characters rotate by the same fixed offset; thus, A always becomes ?, a → H, 1 → G, etc., which can be spotted with a frequency count on the 94‑character set.
- The self‑inverse property means that a second application produces readable text.

---

## Similar Ciphers

### [[rot13-cipher]]

- **Similarity:** Both are fixed, self‑inverse substitution ciphers that use a shift.
- **Difference:** ROT13 operates only on Latin letters (26 characters, shift 13), while ROT47 covers 94 printable ASCII characters (shift 47).

### [[rot18-cipher]]

- **Similarity:** Both handle letters and digits, and both are self‑inverse.
- **Difference:** ROT18 uses two separate moduli (26 for letters, 10 for digits) and leaves punctuation untouched; ROT47 uses a single modulus (94) and transforms nearly all punctuation and symbols as well.

### [[caesar-cipher]]

- **Similarity:** The underlying mechanism is a modular shift on an ordered alphabet.
- **Difference:** The Caesar cipher typically works on letters only, uses a variable key, and is not self‑inverse unless the key is 13. ROT47 has a fixed shift, no key, and acts on a much larger character set.

---

## Variants

ROT47 does not have widely recognised sub‑variants because it already spans the entire printable ASCII range. The concept can be generalised to:

### [[ROT94]]

A shift of 94 on the 94‑character set would be the identity function, serving no purpose.

### [[Arbitrary‑shift ASCII rotation]]

Any shift k modulo 94 can be used, producing a family of ASCII Caesar ciphers. Only k = 47 is self‑inverse. These variants are rarely seen in practice.

---

## Browser Tool

Most online [[rot13-cipher]] tools include a ROT47 option. The linked tool below supports ROT13, ROT5, ROT18, and ROT47 in a single interface.

### Features

- Apply ROT47 to all printable ASCII characters
- Self‑inverse: same button for encode and decode
- Preserve spaces option
- Live preview
- Integration with ROT13 and ROT5 modes

Tool:
[[Tool - ROT13 Cipher]]