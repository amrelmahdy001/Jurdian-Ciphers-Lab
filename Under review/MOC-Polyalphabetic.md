---
type: moc
title: "MOC — Polyalphabetic Ciphers"
aliases:
  - "Polyalphabetic Ciphers Index"
  - "Vigenère Family"
tags:
  - moc
  - cipher
  - classical
  - substitution
  - polyalphabetic
created: 2025-01-01
updated: 2025-06-28
---

# Polyalphabetic Ciphers — Index

> **Definition:** A polyalphabetic cipher uses multiple substitution alphabets, cycling through them according to a key. Different positions in the message are encrypted with different alphabets, defeating simple frequency analysis.
> ← Back to [[MOC-Substitution-Ciphers]]

---

## Core Concept

Polyalphabetic ciphers were created specifically to defeat [[Frequency Analysis]]. By using a different cipher alphabet for each plaintext position (determined by a repeating or running key), the frequency signature of the plaintext is flattened.

However, if the key repeats, the cipher reveals its period — which allows the [[Kasiski Test]] and [[Index of Coincidence]] to determine key length, then reduce the cipher to multiple parallel monoalphabetic problems.

**The key insight:** A polyalphabetic cipher with a key length of `n` is equivalent to `n` independent monoalphabetic ciphers operating in parallel.

---

## Ciphers in This Family

### The Vigenère Group
> All use a tabula recta (Vigenère square) or equivalent.

- [[Vigenère Cipher]] — The archetypal polyalphabetic cipher; `C = (P + K) mod 26` per position
- [[Vigenère Autokey Cipher]] — Key is the keyword + plaintext itself; breaks key repetition
- [[Vigenère Multiplicative Cipher]] — Multiplication-based variant of Vigenère

### The Beaufort Group
> Beaufort reverses the Vigenère formula; decryption and encryption are the same operation.

- [[Beaufort Cipher]] — `C = (K - P) mod 26`; self-reciprocal (encrypting = decrypting)
- [[Variant Beaufort Cipher]] — `C = (P - K) mod 26`; not self-reciprocal
- [[Beaufort Autokey Cipher]] — Beaufort with autokey key generation

### Early Polyalphabetic Systems
- [[Alberti Cipher]] — First polyalphabetic system (Leon Battista Alberti, 1467); cipher disk
- [[Bellaso Cipher]] — Giovan Battista Bellaso's keyword-based system (1553); origin of "Vigenère cipher"
- [[Trithemius Cipher]] — Progressive alphabet shift; precursor to Vigenère (Johannes Trithemius, 1508)
- [[Porta Cipher]] — Giovanni Battista della Porta's 1563 tabula; uses 13 reciprocal alphabets

### Advanced Polyalphabetic
- [[Autoclave Cipher]] — Running key variant; key is the message itself appended to the keyword
- [[Bazeries Cipher]] — Transposition + Caesar; hybrid polyalphabetic-transposition
- [[Chaocipher]] — Self-modifying cipher disk; mechanically polyalphabetic (→ [[MOC-Mechanical-Ciphers]])
- [[Gronsfeld Cipher]] — Vigenère restricted to numeric keys (0–9); weaker than Vigenère
- [[Hill Cipher]] — Matrix multiplication over alphabet; polygraphic and polyalphabetic
- [[Nihilist Cipher]] — Polybius + Vigenère addition; used by Russian nihilists
- [[Phillips Cipher]] — Square-based polyalphabetic system
- [[Ragbaby Cipher]] — Keyed alphabet + numeric offset; sequential key cycling
- [[Slidefair Cipher]] — Combining Beaufort and Playfair concepts
- [[VIC Cipher]] — Soviet spy cipher; straddling checkerboard + transposition; highly complex

---

## Autokey Variants

> Autokey ciphers extend the key with message content to avoid key repetition.
> They are a subset of polyalphabetic ciphers, not a separate family.

| Cipher | Autokey Source |
|---|---|
| [[Vigenère Autokey Cipher]] | Keyword + plaintext |
| [[Beaufort Autokey Cipher]] | Keyword + plaintext |
| [[Autoclave Cipher]] | Keyword + ciphertext (or plaintext variant) |

---

## Cryptanalysis

### Breaking Repeating-Key Polyalphabetic Ciphers

1. **[[Kasiski Test]]** — Find repeated ciphertext sequences → estimate key length
2. **[[Index of Coincidence]]** — Confirm key length estimate
3. **Split into monoalphabetic streams** — Each stream uses one alphabet; attack with [[Frequency Analysis]]

### Breaking Autokey Variants

Harder than repeating-key variants because the key is non-repeating. Requires:
- Cribs (known plaintext segments)
- Long ciphertext for statistical inference
- Probabilistic pattern matching

### Key Length vs Security

| Key length relative to message | Security level |
|---|---|
| Very short (1–3 letters) | Barely better than monoalphabetic |
| Medium (5–10 letters) | Moderate; Kasiski breaks it with ~200+ chars |
| Long (key ≥ message length, no repeat) | Approaches one-time pad security |
| Truly random, never reused, key = message length | [[Vernam Cipher]] — theoretically unbreakable |

---

## Interactive Tools

- [[Tool - Vigenère Cipher]]
- [[Tool - Beaufort Cipher]]
- [[Tool - Gronsfeld Cipher]]
- [[Tool - Kasiski Test]]
- [[Tool - Index of Coincidence]]

---

## All Polyalphabetic Ciphers

```dataview
TABLE difficulty, year_invented, inventor
FROM "docs/ciphers/classical/substitution/polyalphabetic"
WHERE type = "cipher"
SORT year_invented ASC
```
