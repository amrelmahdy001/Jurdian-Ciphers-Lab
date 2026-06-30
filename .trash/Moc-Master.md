---
type: moc
title: "Jurdian Ciphers Lab — Master Index"
aliases:
  - "Master Index"
  - "Home"
  - "Start Here"
tags:
  - moc
  - home
created: 2025-01-01
updated: 2025-06-28
---

# Jurdian Ciphers Lab

> **An open-source knowledge base for ciphers, cryptography, encodings, steganography, and code-breaking.**
> Navigate using the domain links below. Each link leads to a sub-index.
> For the full project overview, see the [[README]].

---

## 🔐 Ciphers & Cryptography

| Sub-Index | Contents |
|---|---|
| [[MOC-Ciphers]] | All cipher algorithms — classical, modern, historical |
| [[MOC-Cryptography]] | Principles, protocols, public-key systems, PKI |
| [[MOC-Hashing]] | Hash functions, checksums, password hashing |

---

## 📦 Encoding & Data

| Sub-Index | Contents |
|---|---|
| [[MOC-Encodings]] | Base encodings, character sets, binary formats, visual codes |
| [[MOC-Compression]] | Lossless and compression algorithms |
| [[MOC-Number-Systems]] | Numeral systems across history and cultures |

---

## 🔍 Analysis & Mathematics

| Sub-Index | Contents |
|---|---|
| [[MOC-Analysis]] | Cryptanalysis, statistical methods, digital forensics |
| [[MOC-Mathematics]] | Number theory, information theory, cryptographic primitives |

---

## 🫥 Hidden Data

| Sub-Index | Contents |
|---|---|
| [[MOC-Steganography]] | Image, audio, and text steganography; detection tools |

---

## 🔣 Symbols & Scripts

| Sub-Index | Contents |
|---|---|
| [[MOC-Writing-Systems]] | Historical alphabets, constructed scripts, symbolic systems |

---

## 📡 Communication

| Sub-Index | Contents |
|---|---|
| [[MOC-Communication-Codes]] | Morse, telecom, signaling, phonetic alphabets |

---

## 🧩 Puzzles & Research

| Sub-Index | Contents |
|---|---|
| [[MOC-Puzzles]] | CTF guides, ARG resources, famous puzzles, puzzle design |
| [[MOC-References]] | Glossary, timeline, bibliography, identification guides |

---

## 🛠 Tools

| Sub-Index | Contents |
|---|---|
| [[MOC-Tools]] | All browser-based tools, organized by function |

---

## ⚡ Quick Access

> Frequently used starting points.

**Start learning:** [[Beginners Guide to Ciphers]] · [[Cipher Identification Guide]] · [[Cryptography Glossary]]

**CTF & Puzzles:** [[CTF Starter Guide]] · [[Cipher Identifier Quick Reference]] · [[MOC-Puzzles]]

**Famous unsolved:** [[Voynich Manuscript]] · [[Kryptos]] · [[Zodiac Killer Cipher]] · [[Cicada 3301 Overview]]

**Most referenced ciphers:** [[Caesar Cipher]] · [[Vigenère Cipher]] · [[Playfair Cipher]] · [[Enigma Machine]] · [[Bifid Cipher]] · [[Rail Fence Cipher]] · [[AES Cipher]] · [[RSA Algorithm]]

---

## 📊 Knowledge Base Status

```dataview
TABLE length(rows) AS "Article Count"
FROM "docs"
WHERE type != "moc"
GROUP BY type
SORT length(rows) DESC
```

```dataview
TABLE length(rows) AS "Count"
FROM "docs"
WHERE status = "stub" OR status = "draft"
GROUP BY status
```

---

*Jurdian Ciphers Lab · Open Source · [[CONTRIBUTING|Contribute]] · [[CHANGELOG|Changelog]]*
