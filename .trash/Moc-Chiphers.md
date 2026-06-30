---
type: moc
title: "MOC — Ciphers"
aliases:
  - "Ciphers Index"
  - "All Ciphers"
tags:
  - moc
  - cipher
created: 2025-01-01
updated: 2025-06-28
---

# Ciphers — Index

> **Domain:** Cipher algorithms that transform plaintext into ciphertext.
> This is the top-level index for all ciphers in the knowledge base.
> ← Back to [[MOC-Master]]

---

## Sub-Indexes by Era & Type

| Sub-Index | Description |
|---|---|
| [[MOC-Classical-Ciphers]] | Pre-computer ciphers: shift, substitution, transposition, mechanical |
| [[MOC-Modern-Ciphers]] | Computational ciphers: block ciphers, stream ciphers |
| [[MOC-Military-Ciphers]] | Thematic index of ciphers used in warfare |
| [[MOC-Historical-Ciphers]] | Famous historical instances and unsolved ciphers |

---

## Browse by Cipher Family

### Classical Families

| Family | Sub-Index | Typical Ciphers |
|---|---|---|
| Shift | [[MOC-Shift-Ciphers]] | Caesar, ROT-13, ROT-47 |
| Monoalphabetic | [[MOC-Monoalphabetic]] | Atbash, Affine, Multiplicative |
| Polyalphabetic | [[MOC-Polyalphabetic]] | Vigenère, Beaufort, Gronsfeld |
| Homophonic | [[MOC-Homophonic-Ciphers]] | Grandpré, Nomenclator, Arnold |
| Polygraphic | [[MOC-Polygraphic-Ciphers]] | Playfair, Four-Square, Polybius |
| Symbolic | [[MOC-Symbolic-Ciphers]] | Pigpen, Dancing Men, Rosicrucian |
| Transposition | [[MOC-Transposition-Ciphers]] | Rail Fence, Columnar, Scytale |
| Fractionation | [[MOC-Fractionation-Ciphers]] | Bifid, Trifid, ADFGVX |
| Mechanical | [[MOC-Mechanical-Ciphers]] | Enigma, Jefferson Wheel, Chaocipher |

### Modern Families

| Family | Sub-Index | Typical Ciphers |
|---|---|---|
| Block Ciphers | [[MOC-Block-Ciphers]] | AES, DES, Blowfish |
| Stream Ciphers | [[MOC-Stream-Ciphers]] | RC4, Vernam, XOR |

---

## Browse by Difficulty

```dataview
TABLE difficulty, category, subcategory, tool_available AS "Tool?"
FROM "docs/ciphers"
WHERE type = "cipher"
SORT difficulty ASC, title ASC
```

---

## Browse by Security Status

> [!warning] Broken Ciphers
> The following ciphers are **cryptographically broken** and included for educational purposes only.

```dataview
LIST
FROM "docs/ciphers"
WHERE type = "cipher" AND broken = true
SORT title ASC
```

---

## All Ciphers A–Z

```dataview
TABLE category, subcategory, difficulty
FROM "docs/ciphers"
WHERE type = "cipher"
SORT title ASC
```

---

## Missing Tools

```dataview
TABLE category, difficulty
FROM "docs/ciphers"
WHERE type = "cipher" AND tool_available = false
SORT title ASC
```
