---
type: moc
title: "MOC — Steganography"
aliases:
  - "Steganography Index"
  - "Hidden Data"
tags:
  - moc
  - steganography
created: 2025-01-01
updated: 2025-06-28
---

# Steganography — Index

> **Definition:** Steganography hides the *existence* of a message within an innocent carrier medium (image, audio, text). Unlike cryptography, which hides the *content*, steganography hides the *fact that a message exists*.
> ← Back to [[MOC-Master]]

---

## Steganography vs Cryptography

| | Cryptography | Steganography |
|---|---|---|
| Hides | Content of message | Existence of message |
| Detectable? | Yes (ciphertext is obvious) | Ideally no |
| Broken when | Plaintext recovered | Hidden message detected |
| Best practice | Use both together | |

**Defense in depth:** Encrypt the secret first (cryptography), then hide it (steganography). This provides both confidentiality and concealment.

---

## Sub-Categories

### Image Steganography
- [[LSB Steganography]] — Hide data in the Least Significant Bits of pixel values; common and hard to detect
- [[Pixel Value Analysis]] — Detect steganography by statistical analysis of pixel distributions
- [[EXIF Steganography]] — Hide data in EXIF metadata fields of JPEG/TIFF files
- [[Invisible Ink Detection]] — Detect hidden content in image channels (e.g., near-invisible watermarks)
- [[PNG Chunks Analysis]] — Extra data hidden in non-standard PNG chunks

### Audio Steganography
- [[Audio Spectrogram Analysis]] — Hidden images or text encoded in the spectrogram of audio
- [[LSB Audio Steganography]] — Least significant bits of audio samples carry hidden data
- [[MIDI Steganography]] — Data hidden in MIDI note timing or velocity values
- [[Music Steganography]] — Broader category of audio-based hiding techniques

### Text Steganography
- [[Acrostic Cipher]] — First letter of each line/word spells the hidden message
- [[Null Cipher]] — Message hidden within innocent-looking text by selection rules (every Nth word, etc.)
- [[Whitespace Steganography]] — Data encoded in invisible whitespace characters
- [[Zero-Width Space]] — Unicode zero-width characters invisible to human readers but machine-readable

### Network & File Steganography
- [[IP Packet Steganography]] — Data hidden in protocol header fields
- [[ZIP Comment Steganography]] — Data hidden in ZIP file comment fields

---

## Detection & Extraction Tools

- [[OutGuess Extractor]] — Detect and extract data hidden with the OutGuess tool
- [[Stegdetect]] — Statistical detection of JPEG steganography
- [[Steghide Extractor]] — Extract data hidden with Steghide
- [[Tool - Binary Signature Scanner]] — Identify file types by magic bytes; detect embedded files
- [[Tool - EXIF Viewer]] — Read all EXIF metadata from images
- [[Tool - Strings Extractor]] — Extract readable strings from binary data

---

## CTF Steganography Checklist

> Quick reference for CTF participants encountering steganographic challenges.

**Given an image:**
1. Check EXIF: [[Tool - EXIF Viewer]]
2. Check file type vs extension: [[Tool - Binary Signature Scanner]]
3. Check LSB: steghide, stegdetect
4. Check color channels: blue channel often used
5. Check metadata strings: `strings` command
6. Check appended data: `binwalk`, hex editor

**Given an audio file:**
1. Open in spectrogram viewer: [[Audio Spectrogram Analysis]]
2. Check LSB in samples
3. Check ID3 metadata: [[Tool - ID3 Metadata Viewer]]
4. Listen at different speeds (0.5x, 2x, reversed)

**Given text:**
1. Check first letters of each line/word: [[Acrostic Cipher]]
2. Check every Nth word: [[Null Cipher]]
3. Check for zero-width characters: [[Zero-Width Space]]
4. Check whitespace patterns: [[Whitespace Steganography]]

---

## All Steganography Articles

```dataview
TABLE subcategory, tool_available AS "Tool?"
FROM "docs/steganography"
WHERE type != "moc"
SORT title ASC
```
