---
title: Caesar Cipher
aliases: Shift Cipher, Caesar's Cipher
category: Classical
family: Substitution
difficulty: ★☆☆☆☆
era: Ancient
security: Very Low
key_required: Yes
key_type: Integer (shift value)
key_space: 26 (for English alphabet)
input: Text
output: Text
tags: cipher, classical, substitution, shift, puzzle, educational
---

# Caesar Cipher

> **A simple substitution cipher where each letter is shifted by a fixed number of positions in the alphabet.**

[[Tool - Caesar Cipher]]

---

## Overview

The Caesar Cipher is one of the simplest and most widely known encryption techniques. It works by shifting each letter in the plaintext by a fixed number of positions down the alphabet. For example, with a shift of 3, A becomes D, B becomes E, and so on.

Named after Julius Caesar, who used it to communicate with his generals, this cipher is fundamental to the history of cryptography. Today, it is primarily used for educational purposes and in puzzle-solving contexts like ARGs and escape rooms, where its simplicity makes it an accessible entry point into the world of codes and ciphers.

---

## Quick Facts

| Property | Value |
|----------|-------|
| Type | Cipher |
| Family | Substitution |
| Category | Monoalphabetic Substitution |
| Difficulty | ★☆☆☆☆ |
| Security | Extremely Low |

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

The Caesar Cipher is named after Julius Caesar (100–44 BCE), the Roman military general and statesman who used it to protect military communications. According to the historian Suetonius, Caesar would shift letters by three positions to make messages unreadable to his enemies. The cipher's simplicity made it effective for its time, but it was never intended for high-stakes secrecy.

Despite its historical roots, the Caesar Cipher was not the first known cipher — the Spartans used the scytale cipher earlier. However, it remains the most famous classical cipher, frequently appearing in modern popular culture, from children's puzzles to works like Dan Brown's *The Da Vinci Code*.

---

# How It Works

## Encryption

Encryption with the Caesar Cipher follows a straightforward process:

1. **Choose a shift value (key)** between 1 and 25 (for the English alphabet). This determines how many positions each letter will move.
2. **For each letter in the plaintext**, find its position in the alphabet (A=0, B=1, ..., Z=25).
3. **Add the shift value** to the letter's position, wrapping around to the start if the result exceeds Z.
4. **Convert the new position back** to a letter and append it to the ciphertext.
5. Non-alphabetic characters (spaces, numbers, punctuation) are typically left unchanged.

---

## Decryption

Decryption reverses the encryption process:

1. **Use the same shift value (key)** that was used for encryption.
2. **For each letter in the ciphertext**, find its position in the alphabet.
3. **Subtract the shift value** from the letter's position, wrapping around to Z if the result goes below A.
4. **Convert the new position back** to a letter to recover the plaintext.
5. Non-alphabetic characters are left unchanged.

Alternatively, decryption can be performed by encrypting with the negative of the original shift.

---

## Formula

```text
Encryption:
C = (P + K) mod 26

Decryption:
P = (C - K) mod 26
```

Where:

· P = Plaintext letter position (0–25)
· C = Ciphertext letter position (0–25)
· K = Key (shift value, 1–25)
· mod 26 = wrap around to the start of the alphabet when exceeding Z or going below A

The modulo operation ensures that the alphabet behaves like a circle: shifting past Z wraps back to A, and shifting below A wraps back to Z.

---

Worked Example

Plaintext

```text
HELLO
```

Key

```text
3
```

Plain H E L L O
Position 7 4 11 11 14
+ Key (3) 10 7 14 14 17
Cipher K H O O R

Ciphertext

```text
KHOOR
```

---

Analysis

Security

The Caesar Cipher offers virtually no security by modern standards. With only 26 possible keys, it is trivially breakable by brute force — a computer can try all possible shifts in fractions of a second. Even without computing power, a human can manually test all 25 shifts in a few minutes.

This cipher should never be used for any purpose requiring real confidentiality. It is purely an educational tool, a stepping stone for learning about cryptography, and a fun puzzle element in games and challenges.

---

Cryptanalysis

The Caesar Cipher is susceptible to several simple attacks:

· Brute Force: With only 26 possible shifts, an attacker can systematically try every key until the plaintext becomes readable. Even if the ciphertext is lowercase, the number of variants is trivial.
· Frequency Analysis: While the Caesar Cipher preserves the frequency distribution of letters, it simply shifts them. The most common letter in the ciphertext is likely to correspond to E (the most common letter in English). By comparing frequency charts, the shift can be determined with high confidence.
· Known Plaintext Attack: If an attacker knows even a single word or phrase from the plaintext (e.g., "HELLO" or "THE"), they can immediately derive the shift value.
· Pattern Recognition: Since the cipher is monoalphabetic, repeated patterns in the ciphertext reveal repeated patterns in the plaintext, aiding cryptanalysis.

---

Recognition Patterns

The Caesar Cipher has several telltale characteristics that help identify it:

· Fixed letter shift: Every letter in the ciphertext is shifted by the same amount, creating a consistent relationship to the original alphabet.
· Deterministic output: The same plaintext always produces the same ciphertext with the same key.
· Preserves spaces: Spaces between words are typically left unchanged, maintaining the original word boundaries.
· Preserves case: Uppercase letters map to uppercase, lowercase to lowercase (if case is preserved).
· Only alphabetic letters change: Numbers, punctuation, and symbols remain untouched.
· Alphabetical wrap-around: The ciphertext alphabet is a Caesar-shifted version of the plaintext alphabet (e.g., if A→D, then B→E, C→F, etc.).
· Common puzzle clue: In escape rooms and ARGs, hints often include phrases like "shift by 3" or "Caesar's favorite number."

---

Similar Ciphers

[[Atbash Cipher]]

· Similarity: Both are monoalphabetic substitution ciphers that are simple to implement and solve. Both preserve spaces and only affect letters.
· Difference: The Caesar Cipher uses a shift (additive transformation), while Atbash uses a mirror substitution (A↔Z, B↔Y, etc.) with no key required.

[[ROT13]]

· Similarity: ROT13 is a specific instance of the Caesar Cipher with a fixed shift of 13. Both operate on the English alphabet.
· Difference: ROT13 is a special case with no key variation (always shift 13), and is self-inverse (encrypting twice recovers the plaintext). The Caesar Cipher allows any shift from 1 to 25.

[[Vigenère Cipher]]

· Similarity: Both are substitution ciphers. The Vigenère cipher can be thought of as a sequence of Caesar shifts applied to individual letters.
· Difference: The Caesar Cipher uses a single, constant shift for the entire message. The Vigenère cipher uses a repeating keyword, making it significantly stronger and defeating simple frequency analysis.

---

Variants

[[ROT13]]

A fixed-shift variant where the key is always 13. This is self-inverse (applying it twice recovers the original text) and is widely used in online forums to obscure content (e.g., spoilers, jokes) without providing any real security.

[[ROT5]] & [[ROT18]] & [[ROT47]]

· ROT5: Shifts digits (0–9) by 5 positions, often combined with ROT13.
· ROT18: A combination of ROT13 (for letters) and ROT5 (for digits).
· ROT47: Shifts all printable ASCII characters (33–126) by 47 positions, affecting letters, digits, punctuation, and symbols.

[[Progressive Caesar Cipher]] (a.k.a. ROT-n or Running Key Caesar)

A variant where the shift value changes for each character, often incrementing by 1 each step (e.g., first letter shifts by 1, second by 2, etc.). This breaks the uniformity of the standard Caesar Cipher and adds a layer of complexity.

---

Browser Tool

An interactive web tool for the Caesar Cipher is available with the following features:

Available Features

· Encrypt any text with a custom shift value
· Decrypt ciphertext using the original shift
· Brute Force — automatically try all 26 shifts and display results
· Frequency Analysis — display letter frequency charts to aid cryptanalysis
· Export Results — copy or download encrypted/decrypted text

Tool:

[[Tool - Caesar Cipher]]

```