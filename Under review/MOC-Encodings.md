---
type: moc
title: "MOC — Encodings"
aliases:
  - "Encodings Index"
  - "Data Formats Index"
tags:
  - moc
  - encoding
created: 2025-01-01
updated: 2025-06-28
---

# Encodings — Index

> **Definition:** An encoding converts data between formats for storage, transmission, or interoperability — with NO secrecy intent. Encodings are reversible by design and publicly documented.
> ← Back to [[MOC-Master]]

---

## Critical Distinction: Encoding ≠ Cipher

| Property | Cipher | Encoding |
|---|---|---|
| Secrecy intended? | Yes | No |
| Key required? | Usually | Never |
| Algorithm published? | Sometimes secret | Always public |
| Reversible without key? | No | Yes |
| Example | [[Vigenère Cipher]] | [[Base64 Encoding]] |

An encoding that is used to *obscure* data (e.g., Base64-encoded secrets) is still just an encoding — it provides **zero cryptographic security**. Security through obscurity is not security.

---

## Sub-Indexes

| Sub-Index | Contents |
|---|---|
| [[MOC-Base-Encodings]] | Base32, Base64, Base85 — binary-to-text conversions |
| [[MOC-Character-Encodings]] | ASCII, Unicode, UTF-8, EBCDIC — text representation standards |
| [[MOC-Binary-Encodings]] | BCD, Gray Code, binary formats |
| [[MOC-Numeric-Encodings]] | A1Z26, letter-number conversions, Fibonacci coding |
| [[MOC-Visual-Codes]] | QR codes, barcodes — visual data encoding |

---

## Quick Reference

### "What encoding is this?"
- Looks like letters and `=` → likely [[Base64 Encoding]]
- Only letters A–Z and 2–7 → likely [[Base32 Encoding]]
- Letters + numbers only, no symbols → could be [[Base62 Encoding]] or [[Base58 Encoding]]
- Only `0` and `1` → [[Binary Code]]
- Dots and dashes → [[Morse Code]] (see [[MOC-Communication-Codes]])
- `%XX` patterns → [[URL Encoding]]
- `&#XX;` or `&amp;` patterns → [[HTML Escape]]

---

## All Encodings A–Z

```dataview
TABLE subcategory, standard, reversible
FROM "docs/encodings"
WHERE type = "encoding"
SORT title ASC
```
