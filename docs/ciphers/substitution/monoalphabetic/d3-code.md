---
title: D3 Code
aliases: D3 Cipher, D-cube Code
type: Cipher
class: Modern
category: Substitution
technique: Polygraphic
character_support:
  - Uppercase
  - Lowercase
  - Spaces
key_count: None
difficulty: ★★☆☆☆
tags:
  - substitution
  - polygraphic
  - modern
  - puzzle
  - d3
status: Complete
created: 2026-07-01
updated: 2026-07-01
---

# D3 Code

> **A polygraphic substitution cipher that encodes letter pairs using a 3×3 grid of dots arranged in a diagonal pattern, producing a distinctive right‑leaning or left‑leaning glyph for each digraph.**

> [!tip] Browser Tool
> No dedicated browser tool is currently available. The cipher is typically decoded manually by recognising the dot patterns, or with custom scripts.

---

## Overview

The D3 code is a geometric substitution cipher that represents the alphabet through the positions of dots on a 3×3 grid. Each letter is a combination of two dots: one on the left diagonal and one on the right diagonal of the square. When two letters are paired into a digraph, their dots are superimposed, producing a composite pattern of up to four dots. The resulting symbols have a characteristic “bow‑tie” or “hourglass” appearance and are often drawn connected by lines.

The cipher appears almost exclusively in ARGs, escape rooms, and puzzle hunt communities. Its name derives from the 3×3 dot matrix and the diagonal lines used to construct it. It has no known historical cryptographic use and is purely a modern puzzle construction, valued for its visual distinctiveness and the satisfying “aha” moment when solvers recognise the underlying grid.

---
## Classification

This cipher belongs to the **Substitution** family and uses a **Polygraphic** technique, encoding letters in pairs on a fixed geometric grid.

It is a **Modern** puzzle cipher with no variable key, though the dot‑to‑letter assignment may be permuted in some variants.

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

The standard encoding covers the 26‑letter English alphabet. Spaces are typically represented by a blank glyph, a special symbol, or preserved in the ciphertext layout.

---

## History

The D3 code first appeared in online puzzle communities in the early 2000s, notably on forums dedicated to ARGs and cryptographic puzzles. Its exact originator is not definitively known; it emerged organically as solvers experimented with visual ciphers based on dot matrices. The cipher gained wider recognition through its inclusion in the puzzle‑hunt video game *Cypher* (2012) and subsequent appearances in independent puzzle suites. It has no connection to any historical cryptosystem or military usage.

---

## How It Works

### Encryption

1. A 3×3 grid of nine dot positions is defined. The positions are numbered 1–9, typically read left‑to‑right, top‑to‑bottom:
 ```
 123
 456
 789
 ```
 2. The left diagonal consists of positions 1, 5, 9. The right diagonal consists of positions 3, 5, 7.
3. Each letter of the alphabet is assigned a unique pair: one position from the left diagonal and one from the right diagonal. Because there are 3 × 3 = 9 possible combinations, the 26 letters reuse the grid with an additional modifier (commonly a dot in the centre cell, position 5, is added for letters beyond I; or the grid is used in multiple “banks” with a distinguishing mark).
   - The simplest standard assignment uses position 5 (the centre) on only one diagonal at a time. The nine base combinations (without centre) are: (1,3), (1,5), (1,7), (5,3), (5,7), (9,3), (9,5), (9,7). The centre dot on both diagonals (5,5) provides additional combinations when combined with an extra marker, or letters J–R use a solid centre dot and S–Z use a hollow centre dot. Exact conventions vary; puzzles typically provide a key or enough ciphertext for deduction.
4. The plaintext is divided into pairs of letters. For each pair, the dots from both letters are placed on a single 3×3 grid and optionally connected by lines to form the final glyph.

### Decryption

1. Each D3 glyph is decomposed into its constituent dots on the 3×3 grid.
2. The dots are separated into left‑diagonal positions and right‑diagonal positions.
3. Using the agreed assignment table, each (left, right) pair is converted back to its corresponding letter.
4. If a glyph contains four dots, it represents two letters; their order must be inferred from context or from a convention (e.g., the letter with the higher dot is read first, or simply left‑to‑right, top‑to‑bottom by the earliest dot).

### Mathematical Formula

The D3 code is a geometric lookup cipher. No algebraic formula governs encoding; it is defined by a mapping table.

**Encryption**

$$
\text{Glyph} = \text{Draw}( \text{Dots}(L_1) \cup \text{Dots}(L_2) )
$$

**Decryption**

$$
(L_1, L_2) = \text{Table}^{-1}( \text{Decompose}(\text{Glyph}) )
$$

**Variables**

- **L₁, L₂** — a pair of plaintext or ciphertext letters
- **Dots(L)** — the set of dot positions on the 3×3 grid assigned to a letter
- **Glyph** — the visual composite of the dot sets

### Worked Example

| Parameter | Value |
|-----------|-------|
| **Plaintext** | `HE` |
| **Grid Assignment (example convention)** | H = (1, 3), E = (5, 7) |

| Step | Description |
|------|-------------|
| Letter H | Dot at position 1 (top‑left of left diagonal). Dot at position 3 (top‑right of right diagonal). |
| Letter E | Dot at position 5 (centre, left diagonal). Dot at position 7 (bottom‑left of right diagonal). |
| Composite glyph | Dots at positions 1, 3, 5, 7. When drawn on a 3×3 square and connected with lines, this forms an “X” shape with an extra cross‑bar, visually resembling a stylised star or bow‑tie. |

**Result**

A D3 glyph with dots at the top‑left, top‑right, centre, and bottom‑left positions. In textual representation, this is often written as coordinates: `1,3,5,7` or depicted visually.

Decryption reverses the process: the four dots are identified as belonging to (1,3) and (5,7), mapping back to H and E.

## Analysis

### Security

The D3 code offers no cryptographic security. It is a fixed, unkeyed substitution cipher intended for visual puzzles. Anyone who recognises the 3×3 grid structure and the standard letter assignment can decode it instantly.

### Cryptanalysis

- **Pattern recognition:** the 3×3 dot matrix with diagonal emphasis is visually distinctive; once identified as D3, the standard mapping unlocks the message.
- **Frequency analysis:** if glyphs represent digraphs, common English digraphs (TH, HE, IN, ER) will appear frequently, aiding mapping recovery.
- **Grid geometry:** the limited number of dot combinations constrains the possible letters; systematic trial against expected plaintext quickly converges.

### Recognition Patterns

- Symbols are drawn on a 3×3 grid of dots or intersections.
- Each glyph contains 2–4 dots, often connected by lines forming diagonal crosses, V‑shapes, or hourglass figures.
- The presence of a recurring central dot (position 5) is a hallmark of the cipher.
- Glyphs are typically drawn within small square boundaries, sometimes arranged in a line like text.
- The symbols have no resemblance to any natural alphabet and appear as abstract geometric marks.

---

## Similar Ciphers

### [[Pigpen Cipher]]

- **Similarity:** Both are geometric substitution ciphers that use a grid to assign symbols to letters. Both produce distinctive, non‑alphabetic glyphs.
- **Difference:** Pigpen uses a 3×3 grid (and an X grid) with lines indicating which “pen” a letter sits in; each glyph represents a single letter. D3 uses dot positions on diagonals and encodes two letters per glyph (polygraphic vs. monoalphabetic).

### [[Polybius Square]]

- **Similarity:** Both rely on a grid structure and can encode letter pairs. Both use coordinate‑based substitution.
- **Difference:** Polybius encodes each letter as a pair of numbers (row and column) from a 5×5 grid. D3 encodes letter pairs visually on a 3×3 dot matrix using diagonals. Polybius output is numeric; D3 output is graphical.

### [[Templar Cipher]] / [[Rosicrucian Cipher]]

- **Similarity:** Both are grid‑based geometric ciphers that produce abstract symbols from a 3×3 layout.
- **Difference:** Templar and Rosicrucian ciphers are variants of the Pigpen family; they use lines and angles around a grid cell to represent single letters. D3 uses dots at intersections, encodes digraphs, and has a fundamentally different assignment logic.

---

## Variants

### Single‑Letter D3

A simplified form where each glyph represents exactly one letter, using exactly two dots per glyph (one on each diagonal). This eliminates the digraph ambiguity but reduces the number of available symbols to 9, requiring a second grid bank or modifier for the full alphabet.

### Left‑Diagonal / Right‑Diagonal Rotation

Some puzzles use a mirror‑image grid or rotate the assignment. The structural principle is identical; only the visual orientation changes. Recognising the 3×3 dot matrix is sufficient to adapt.

### D3 with Line Connections

A common presentation joins the dots of each glyph with straight lines, producing shapes such as chevrons, crosses, and hourglasses. The lines are purely aesthetic and do not affect the decoding; they enhance the visual language of the puzzle.

### Extended D3 for Numbers and Symbols

Experimental variants extend the grid to include numbers 0–9 or punctuation by using additional dot positions (e.g., midpoints on edges) or by introducing coloured dots. These are non‑standard and typically accompanied by an explicit key.

---

## Browser Tool

No interactive tool for the D3 code is currently available in the lab. Manual decoding with a reference grid is standard practice. A future visual tool may allow drawing glyphs on a 3×3 grid and automatically extracting the corresponding letter pairs.

Tool: None currently available.