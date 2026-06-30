---
type: moc
title: "MOC — Analysis"
aliases:
  - "Analysis Methods Index"
  - "Cryptanalysis Index"
tags:
  - moc
  - analysis
created: 2025-01-01
updated: 2025-06-28
---

# Analysis — Index

> **Definition:** Analysis methods are techniques for studying, breaking, or identifying ciphers and encoded data without (necessarily) knowing the key.
> ← Back to [[MOC-Master]]

---

## Sub-Indexes

| Sub-Index | Contents |
|---|---|
| [[MOC-Cryptanalysis]] | Attack types and cipher-breaking methods |
| [[MOC-Statistical-Analysis]] | Mathematical and frequency-based analysis |
| [[MOC-Digital-Forensics]] | Binary analysis, file forensics, metadata |

---

## Identification Tools
- [[Cipher Identifier Quick Reference]] — Visual guide to identifying unknown ciphers
- [[Tool - Cipher Identifier]] — Automated cipher identification tool
- [[Tool - Hash Identifier]] — Identify unknown hash strings by length and character set

---

## The Analyst's Workflow

```
Unknown ciphertext received
        │
        ▼
1. Character set analysis
   ├── Only letters? → likely classical cipher
   ├── Letters + digits? → base encoding, or modern cipher
   ├── Binary (0/1)? → binary encoding or Bacon cipher
   ├── Symbols/glyphs? → see [[MOC-Symbolic-Ciphers]] or [[MOC-Writing-Systems]]
   └── Fixed-length hex string? → hash function (not a cipher)
        │
        ▼
2. Length analysis
   ├── Very short (< 20 chars)? → probably a code or identifier
   ├── Matches common hash length? → [[Tool - Hash Identifier]]
   └── Normal sentence length → proceed
        │
        ▼
3. Frequency analysis
   ├── [[Index of Coincidence]] — distinguishes mono- vs polyalphabetic
   ├── [[Frequency Analysis]] — monoalphabetic if IC ≈ 0.065 (English)
   └── Flat distribution → polyalphabetic or transposition
        │
        ▼
4. Key length estimation (if polyalphabetic)
   ├── [[Kasiski Test]] — repeated sequences reveal key period
   └── [[Index of Coincidence]] at various key lengths
        │
        ▼
5. Attack
   ├── Monoalphabetic → [[Frequency Analysis]] → manual substitution
   ├── Polyalphabetic → split into monoalphabetic streams → attack each
   ├── Transposition → anagramming, columnar structure detection
   └── Unknown → consult [[MOC-Cryptanalysis]] for attack types
```

---

## All Analysis Articles

```dataview
TABLE subcategory, applies_to
FROM "docs/analysis"
WHERE type = "analysis-method"
SORT title ASC
```
