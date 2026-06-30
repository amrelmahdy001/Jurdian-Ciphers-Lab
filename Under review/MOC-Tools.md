---
type: moc
title: "MOC — Tools"
aliases:
  - "Tools Index"
  - "Browser Tools"
tags:
  - moc
  - tool
created: 2025-01-01
updated: 2025-06-28
---

# Tools — Index

> **Definition:** Browser-based interactive tools for encryption, decryption, analysis, encoding, and visualization.
> ← Back to [[MOC-Master]]

---

## Find a Tool

### By Function

| Function | Tools |
|---|---|
| Encrypt a message | See [[#Cipher Tools — Encryption]] |
| Decrypt a message | See [[#Cipher Tools — Decryption]] |
| Identify an unknown cipher | [[Tool - Cipher Identifier]] |
| Analyze ciphertext statistically | [[Tool - Frequency Analysis]], [[Tool - Index of Coincidence]] |
| Encode data | See [[#Encoding Tools]] |
| Hash data | See [[#Hash Tools]] |
| Detect steganography | See [[#Steganography Tools]] |
| Convert between formats | See [[#Conversion Tools]] |
| Visualize | See [[#Visualization Tools]] |

---

## Cipher Tools — Encryption & Decryption

### Shift Ciphers
- [[Tool - Caesar Cipher]] — Encrypt/decrypt/brute-force; all 25 shifts
- [[Tool - ROT-13]] — One-click ROT-13
- [[Tool - ROT-47]] — Full ASCII printable rotation
- [[Tool - ROT-N]] — Configurable shift value

### Substitution Ciphers
- [[Tool - Affine Cipher]]
- [[Tool - Atbash Cipher]]
- [[Tool - Beaufort Cipher]]
- [[Tool - Gronsfeld Cipher]]
- [[Tool - Hill Cipher]]
- [[Tool - Monoalphabetic Substitution]]
- [[Tool - Vigenère Cipher]]

### Transposition Ciphers
- [[Tool - Caesar Box Cipher]]
- [[Tool - Columnar Transposition Cipher]]
- [[Tool - Rail Fence Cipher]]
- [[Tool - Route Transposition Cipher]]
- [[Tool - Scytale Cipher]]

### Polygraphic & Fractionation
- [[Tool - ADFGVX Cipher]]
- [[Tool - Bifid Cipher]]
- [[Tool - Four-Square Cipher]]
- [[Tool - Playfair Cipher]]
- [[Tool - Polybius Cipher]]
- [[Tool - Trifid Cipher]]

### Modern Ciphers
- [[Tool - AES Cipher]]
- [[Tool - RSA Cipher]]
- [[Tool - XOR Cipher]]

### Mechanical Simulators
- [[Tool - Cipher Disk Simulator]]
- [[Tool - Enigma Machine Simulator]]
- [[Tool - Jefferson Wheel Cipher]]

---

## Analysis Tools

- [[Tool - Cipher Identifier]] — Automated cipher type detection
- [[Tool - Frequency Analysis]] — Letter frequency histogram and comparison
- [[Tool - Hash Identifier]] — Identify hash type by string characteristics
- [[Tool - Index of Coincidence]] — IC calculation for key-length estimation
- [[Tool - Kasiski Test]] — Repeated sequence finder for Vigenère key length
- [[Tool - Shannon Entropy]] — Information density measurement
- [[Tool - Text Statistics]] — Letter, word, and pattern statistics

---

## Encoding Tools

- [[Tool - Base32 Encoder]]
- [[Tool - Base64 Encoder]]
- [[Tool - Base85 Encoder]]
- [[Tool - Binary Converter]]
- [[Tool - Hex Converter]]
- [[Tool - Morse Code Encoder]]
- [[Tool - Multi-Base Converter]] — Convert between any base (2–64)
- [[Tool - URL Encoder]]

---

## Hash Tools

- [[Tool - Hash Generator]] — Generate MD5, SHA-1, SHA-256, SHA-512, BLAKE2
- [[Tool - Hash Identifier]]
- [[Tool - Hash Lookup]] — Reverse lookup via public rainbow tables
- [[Tool - Luhn Validator]]

---

## Steganography Tools

- [[Tool - Audio Spectrogram Viewer]]
- [[Tool - EXIF Viewer]]
- [[Tool - Steganography Detector]]
- [[Tool - Zero-Width Character Detector]]

---

## Conversion & Utility Tools

- [[Tool - ASCII Table Reference]]
- [[Tool - Binary Signature Scanner]]
- [[Tool - Morse Audio Decoder]]
- [[Tool - Number Base Converter]]
- [[Tool - Roman Numeral Converter]]
- [[Tool - Unicode Character Lookup]]

---

## Visualization Tools

- [[Tool - Cipher Comparison Matrix]]
- [[Tool - Cryptography Timeline Viewer]]
- [[Tool - Frequency Chart Generator]]
- [[Tool - Vigenère Square Visualizer]]

---

## All Tools

```dataview
TABLE tool_type, requires_key, input_type
FROM "tools"
WHERE type = "tool"
SORT title ASC
```
