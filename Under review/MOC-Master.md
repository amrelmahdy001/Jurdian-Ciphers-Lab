---
type: moc
title: Jurdian Ciphers Lab — Master Index
aliases:
  - Master Index
  - Home
  - Start Here
tags:
  - moc
  - home
created: 2026-06-27
updated: 2026-06-29
---
# Jurdian Ciphers Lab

> **An open-source knowledge base dedicated to ciphers, cryptography, encodings, steganography, cryptanalysis, and puzzle research.**

This page is the central navigation hub of the project.

Every subject is organized through **Maps of Content (MOCs)**. Rather than listing every article here, each domain has its own index page that groups related documentation and maintains internal navigation.

For repository information, installation, contribution guidelines, and project goals, see [[README]].

---

# Getting Started

If this is your first visit, the following reading order is recommended.

1. [[Beginners Guide to Ciphers]]
2. [[Cipher Identification Guide]]
3. [[MOC-Ciphers]]
4. [[MOC-Analysis]]
5. [[MOC-Tools]]

---

# Knowledge Domains

## Cryptography

| Index | Description |
|--------|-------------|
| [[MOC-Ciphers]] | Classical, modern, historical, and mechanical cipher systems |
| [[MOC-Cryptography]] | Cryptographic concepts, protocols, public-key systems, and PKI |
| [[MOC-Hashing]] | Cryptographic hashes, password hashing, and checksums |

---

## Data Representation

| Index | Description |
|--------|-------------|
| [[MOC-Encodings]] | Character, binary, numeric, and visual encodings |
| [[MOC-Compression]] | Compression algorithms and data transformation |
| [[MOC-Number-Systems]] | Historical and modern numeral systems |

---

## Analysis

| Index | Description |
|--------|-------------|
| [[MOC-Analysis]] | Cryptanalysis, statistical methods, and digital forensics |
| [[MOC-Mathematics]] | Mathematical foundations used throughout cryptography |

---

## Hidden Information

| Index | Description |
|--------|-------------|
| [[MOC-Steganography]] | Image, audio, and text steganography together with extraction and detection techniques |

---

## Writing & Communication

| Index | Description |
|--------|-------------|
| [[MOC-Writing-Systems]] | Historical alphabets, symbolic scripts, and fictional writing systems |
| [[MOC-Communication-Codes]] | Morse, semaphore, telecom signaling, and phonetic alphabets |

---

## Puzzle Design

| Index | Description |
|--------|-------------|
| [[MOC-Puzzles]] | CTF guides, ARG design, famous puzzles, and puzzle construction |
| [[MOC-References]] | Glossary, bibliography, timeline, and reference material |

---

## Tools

| Index | Description |
|--------|-------------|
| [[MOC-Tools]] | Browser-based utilities for encryption, decryption, encoding, decoding, analysis, and visualization |

---

# Frequently Used Articles

## Learning

- [[Beginners Guide to Ciphers]]
- [[Cipher Identification Guide]]
- [[Cryptography Glossary]]

## Popular Algorithms

- [[Caesar Cipher]]
- [[Vigenère Cipher]]
- [[Playfair Cipher]]
- [[Rail Fence Cipher]]
- [[AES Cipher]]
- [[RSA Algorithm]]

## Famous Cases

- [[Voynich Manuscript]]
- [[Kryptos]]
- [[Zodiac Killer Cipher]]
- [[Cicada 3301 Overview]]

---

# Obsidian

This repository is designed to be used as an Obsidian vault.

Recommended plugins:

- Dataview
- Templater
- Folder Notes
- Tag Wrangler

Recommended startup page:

```
docs/MOC-Master.md
```

---

# Project Statistics

## Articles by Type

```dataview
TABLE length(rows) AS "Articles"
FROM "docs"
WHERE type != "moc"
GROUP BY type
SORT length(rows) DESC
```

## Draft Progress

```dataview
TABLE length(rows) AS "Articles"
FROM "docs"
WHERE status = "draft" OR status = "stub"
GROUP BY status
```

## Recently Updated

```dataview
TABLE file.mtime AS "Last Modified"
FROM "docs"
SORT file.mtime DESC
LIMIT 10
```

---

# Notes

- Every article exists in only one location.
- Cross-references are created using internal wiki links.
- MOCs act as navigation pages rather than documentation pages.
- Duplicate articles should never be created.

---

Jurdian Ciphers Lab

Open Source Knowledge Base

Version 0.1