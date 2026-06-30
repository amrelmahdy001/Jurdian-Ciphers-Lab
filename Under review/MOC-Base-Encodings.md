---
type: moc
title: "MOC — Base Encodings"
aliases:
  - "Base Encoding Index"
  - "Binary-to-Text Encodings"
tags:
  - moc
  - encoding
  - base
created: 2025-01-01
updated: 2025-06-28
---

# Base Encodings — Index

> **Definition:** Base encodings represent binary data using a restricted alphabet of printable characters. They exist to safely transmit binary data through systems that only handle text.
> ← Back to [[MOC-Encodings]]

---

## Why Base Encodings Exist

Email systems, URLs, and many legacy protocols were designed for 7-bit ASCII text. Binary data (images, files, arbitrary bytes) cannot pass through these systems unchanged. Base encodings solve this by mapping every sequence of bits to printable characters.

**Trade-off:** Base encodings expand data size. Base64 adds ~33% overhead. Base85 reduces this to ~25%.

---

## All Base Encodings

| Encoding | Alphabet Size | Characters Used | Typical Use | Overhead |
|---|---|---|---|---|
| [[Base16 Encoding]] | 16 | `0-9, A-F` | Hex dump, debugging | 100% |
| [[Base26 Encoding]] | 26 | `A-Z` | Theoretical; rarely used | ~65% |
| [[Base32 Encoding]] | 32 | `A-Z, 2-7, =` | TOTP, DNS, file systems | 60% |
| [[Base32 Crockford Encoding]] | 32 | `0-9, A-Z` (no I,L,O,U) | Human-readable IDs | 60% |
| [[Z-Base-32 Encoding]] | 32 | Human-friendly 32-char set | Mnemonics | 60% |
| [[Base36 Encoding]] | 36 | `0-9, A-Z` | URL shorteners, IDs | ~55% |
| [[Base45 Encoding]] | 45 | `0-9, A-Z, space, $%*+-./:` | QR code data, EU COVID cert | ~48% |
| [[Base58 Encoding]] | 58 | `0-9, A-Z, a-z` (no 0,I,O,l) | Bitcoin addresses, IPFS | ~37% |
| [[Base62 Encoding]] | 62 | `0-9, A-Z, a-z` | URL shorteners, tokens | ~35% |
| [[Base64 Encoding]] | 64 | `A-Z, a-z, 0-9, +, /` | Email (MIME), JWT, web | 33% |
| [[Base85 Encoding]] | 85 | ASCII 33–117 | PDF, Adobe, Git patches | 25% |
| [[Base91 Encoding]] | 91 | Printable ASCII (subset) | File compression | ~23% |
| [[Base92 Encoding]] | 92 | Printable ASCII (subset) | Experimental | ~22% |
| [[Base100 Encoding]] | 100 | Emoji | Novelty; emoji encoding | Large |
| [[Base65536 Encoding]] | 65536 | Unicode characters | Novelty; high-density text | Varies |

---

## Choosing the Right Base Encoding

```
Is human readability important?
├── Yes → Is it for IDs or codes people type manually?
│   ├── Yes → [[Base32 Crockford Encoding]] (no confusing chars)
│   └── No → [[Base58 Encoding]] (crypto standard)
└── No → Is overhead a concern?
    ├── Yes → [[Base85 Encoding]] (25% overhead)
    └── No → [[Base64 Encoding]] (universal support)
```

---

## Interactive Tools

- [[Tool - Base64 Encoder]]
- [[Tool - Base32 Encoder]]
- [[Tool - Base58 Encoder]]
- [[Tool - Base85 Encoder]]
- [[Tool - Multi-Base Converter]]
