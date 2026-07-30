---
title: Book Cipher
aliases: Ottendorf Cipher, Codex Cipher
type: Cipher
class: Classical
category: Substitution
technique: Homophonic
character_support:
  - Uppercase
  - Lowercase
  - Numbers
  - Spaces
  - Punctuation
  - Symbols
  - Unicode
key_count: 1 Key
difficulty: ★★★☆☆
tags:
  - substitution
  - homophonic
  - classical
  - book
  - steganography
status: Complete
created: 2026-07-01
updated: 2026-07-01
---

# Book Cipher

> **A substitution cipher where each word or letter of the plaintext is replaced by coordinates referencing its position within a pre‑agreed text, typically a specific book.**

> [!tip] Browser Tool
> No dedicated browser tool is available; the cipher requires possession of the agreed‑upon source text. Some general‑purpose tools support decoding when the text is provided.

---

## Overview

A book cipher encodes a message by referencing the location of each plaintext word (or letter) within a shared source document, traditionally a printed book. A typical ciphertext consists of a sequence of numbers: page, line, and word position. To decrypt, the recipient must possess an identical copy of the same edition. Without the correct book, the ciphertext is essentially random numbers.

The book cipher is one of the most historically enduring low‑technology secure communication methods, used in espionage, prison correspondence, and resistance networks precisely because the key is a physical object that can be innocently possessed. It remains popular in puzzle design, ARGs, and fictional portrayals of cryptography where the challenge is discovering which book was used.

---
## Classification

This cipher belongs to the **Substitution** family and can behave as a **Homophonic** cipher, since a single plaintext word may appear multiple times in the source text and can be encoded using any of its occurrences.

It is a **Classical Cipher** that uses a physical or digital document as its single key.

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
| Unicode | ✓ | ✓ |
| Binary | ✗ | ✗ |

The book cipher can encode any word or character present in the chosen source text. Rare words, proper nouns, or special characters may require workarounds if absent from the book.

---

## History

Book ciphers have been used since at least the Renaissance, but they became prominent during the American Revolutionary War, where Benedict Arnold employed a book cipher using Blackstone’s *Commentaries on the Laws of England* for his treasonous correspondence with the British. In the 20th century, book ciphers were favoured by spies operating in civilian settings because carrying a common novel attracted no suspicion. More recently, the Zodiac Killer’s infamous unsolved ciphers, and various prison communication schemes, have kept the book cipher in the public imagination. Its fictional use appears in films like *National Treasure* and numerous spy novels.

---

## How It Works

### Encryption

1. The sender and receiver agree on a specific book, including edition and printing, to ensure identical pagination and line breaks.
2. For each word in the plaintext, the sender locates an occurrence of that word in the agreed book.
3. The sender records the coordinates of that word, typically as a triple: **page number – line number on the page – word position in the line**.
4. These coordinates form the ciphertext. Multiple occurrences of the same word can be used to avoid repetition patterns (homophonic substitution).

If a word does not exist in the book, the sender must either substitute a synonym or spell the word letter‑by‑letter using a separate convention (e.g., line‑letter referencing).

### Decryption

1. The recipient, possessing an identical copy of the book, looks up each coordinate triple.
2. The word at the specified page, line, and word position is retrieved.
3. These words are concatenated to reconstruct the plaintext.

### Mathematical Formula

No mathematical formula governs the cipher. It is a direct indexing system:

**Encryption**

$$
\text{Ciphertext} = \{ (P_i, L_i, W_i) \mid \text{word at } (P_i, L_i, W_i) \text{ equals } \text{Plaintext}_i \}
$$

**Decryption**

$$
\text{Plaintext}_i = \text{Book}(P_i, L_i, W_i)
$$

**Variables**

- **P** — page number
- **L** — line number on that page (counted from the top)
- **W** — word position within that line (counted from the left)

### Worked Example

| Parameter | Value |
|-----------|-------|
| **Plaintext** | `MEET AT DAWN` |
| **Book** | A specific edition of *Pride and Prejudice* |
| **Coordinate Format** | `PAGE.LINE.WORD` |

| Plaintext Word | Found At | Coordinates |
|----------------|----------|-------------|
| MEET | Page 12, line 5, word 3 | `12.5.3` |
| AT | Page 23, line 11, word 7 | `23.11.7` |
| DAWN | Page 47, line 2, word 1 | `47.2.1` |

**Result**

```text
12.5.3 23.11.7 47.2.1
```
## Analysis

### Security

The book cipher is highly secure against ciphertext‑only cryptanalysis provided the source book remains secret and its text is not guessable from context. Its key space is effectively the set of all printed texts, which is astronomically large. However, it is vulnerable to known‑book attacks, traffic analysis (repeated coordinates suggesting common words), and physical compromise of the book. Modern statistical methods applied to large corpora can sometimes identify the source text if enough ciphertext is intercepted.

---

### Cryptanalysis

- **Known‑book attack:** if the book is identified or guessed, decryption is trivial.
- **Frequency analysis of coordinates:** common words appear more frequently in the book; repeated or low‑index coordinates may correspond to high‑frequency English words like "the", "of", "and".
- **Traffic analysis:** repeated use of identical coordinate sets across messages strongly suggests the same word, enabling crib‑dragging.
- **Corpus‑based attack:** with sufficient ciphertext, statistical comparison against digitised book corpora (e.g., Project Gutenberg) can sometimes identify the source text by matching word‑position patterns.

---

### Recognition Patterns

- Ciphertext consists entirely of numbers, typically in groups of 2 or 3 per "word".
- Number values are bounded; page numbers are generally reasonable for a book (1–several hundred), line numbers rarely exceed 40, word counts stay within a line's capacity.
- The ciphertext length (in number groups) often matches the plaintext word count, preserving message structure.
- Separators such as dots, hyphens, or commas between the numbers in each triple are common.

---

## Similar Ciphers

### [[Ottendorf Cipher]]

- **Similarity:** Often used synonymously with "book cipher"; the Ottendorf cipher is a specific form where coordinates point to letters within words.
- **Difference:** Classical book cipher typically references whole words; the Ottendorf variant references individual letters (page–line–word–letter).

### [[Dictionary Cipher]]

- **Similarity:** Both use a shared reference text as the key and output numeric coordinates.
- **Difference:** The dictionary cipher uses an alphabetically sorted word list (a dictionary) and outputs only the word's entry number, not a page–line–word triple. This simplifies encryption but requires a standardised dictionary.

### [[Running Key Cipher]]

- **Similarity:** Both rely on a shared text to encipher and decipher the message.
- **Difference:** The running key cipher uses the source text as a keystream added to the plaintext numerically (a [[Vigenère Cipher]] variant), while the book cipher uses the text as a direct lookup table for word substitution.

### [[Beale Cipher]]

- **Similarity:** The Beale ciphers famously use a book (the Declaration of Independence) as the key, encoding each letter by the position of a word starting with that letter.
- **Difference:** The Beale cipher is a specific historical instance using letter‑level indexing; the book cipher is the broader method that can work at the word level.

---

## Variants

### [[Letter‑Level Book Cipher]]

Instead of encoding whole words, the cipher encodes individual letters. Each coordinate typically includes a fourth number: the letter position within the specified word (page–line–word–letter). This allows spelling any word, regardless of whether it appears in the book, but produces longer ciphertext.

### [[Newspaper Cipher]]

A variant using a specific issue of a newspaper as the source text. The shared key is the date and publication name. Popular in historical espionage because newspapers were universally available and discarded after use, reducing physical evidence.

### [[Bible Cipher]]

A common special case where the agreed book is a specific edition of the Bible (often the King James Version). Chapter and verse numbers provide a natural indexing system, and the ubiquity of the Bible historically made it an ideal key.

### [[Digital Book Cipher]]

A modern adaptation using a specific electronic text file (e.g., a Project Gutenberg eBook) as the source, with precise byte offsets or character positions replacing page–line–word. This eliminates the edition‑matching problem but requires access to the exact digital file.

---

## Browser Tool

No standalone book cipher tool exists in the lab, as the cipher fundamentally requires an external text. General‑purpose tools that accept a source text and coordinates can be used. Future lab additions may include a configurable lookup tool for digital source texts.

Tool:
None currently available.