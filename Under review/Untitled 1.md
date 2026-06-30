# Contributing to Jurdian Ciphers Lab

Thank you for contributing. This document explains how to add articles, tools, and improvements correctly so the knowledge base stays consistent and scalable.

---

## Table of Contents

1. [Before You Start](#1-before-you-start)
2. [Article Placement Decision Tree](#2-article-placement-decision-tree)
3. [YAML Front Matter Rules](#3-yaml-front-matter-rules)
4. [Naming Conventions](#4-naming-conventions)
5. [Article Quality Standards](#5-article-quality-standards)
6. [Adding a New Cipher Article](#6-adding-a-new-cipher-article)
7. [Adding a New Encoding Article](#7-adding-a-new-encoding-article)
8. [Adding a New Tool Article](#8-adding-a-new-tool-article)
9. [Updating MOC Files](#9-updating-moc-files)
10. [Pull Request Checklist](#10-pull-request-checklist)

---

## 1. Before You Start

- Check that the article does not already exist. Search the repo before creating.
- Every article lives in **exactly one folder**. Cross-references use `[[wiki links]]` and tags — never duplicate content.
- Read the template for your article type before writing anything.

---

## 2. Article Placement Decision Tree

Use this to determine which folder your article belongs in.

```
What are you adding?
│
├── An algorithm that encrypts plaintext into ciphertext?
│   → docs/ciphers/
│   │
│   ├── Pre-computer, hand-operated?
│   │   → docs/ciphers/classical/
│   │   │
│   │   ├── Shifts the alphabet by a fixed amount?
│   │   │   → docs/ciphers/classical/shift/
│   │   │
│   │   ├── Substitutes letters using one fixed alphabet?
│   │   │   → docs/ciphers/classical/substitution/monoalphabetic/
│   │   │
│   │   ├── Substitutes letters using multiple alphabets?
│   │   │   → docs/ciphers/classical/substitution/polyalphabetic/
│   │   │
│   │   ├── One plaintext letter → multiple ciphertext symbols?
│   │   │   → docs/ciphers/classical/substitution/homophonic/
│   │   │
│   │   ├── Groups of letters substituted together?
│   │   │   → docs/ciphers/classical/substitution/polygraphic/
│   │   │
│   │   ├── Symbols or glyphs used instead of letters?
│   │   │   → docs/ciphers/classical/substitution/symbolic/
│   │   │
│   │   ├── Rearranges letter positions (no substitution)?
│   │   │   → docs/ciphers/classical/transposition/
│   │   │
│   │   ├── Splits letters into coordinate fractions then permutes?
│   │   │   → docs/ciphers/classical/fractionation/
│   │   │
│   │   └── Implemented by a physical device (disk, rotor, wheel)?
│   │       → docs/ciphers/classical/mechanical/
│   │
│   └── Computer-era, designed for computational security?
│       → docs/ciphers/modern/
│       ├── Fixed-size block encryption?  → docs/ciphers/modern/block/
│       └── Bit-by-bit stream encryption? → docs/ciphers/modern/stream/
│
├── A format conversion with no secrecy intent?
│   → docs/encodings/
│   ├── Binary-to-text (Base32, Base64, etc.)? → docs/encodings/base/
│   ├── Character set standard (ASCII, Unicode)? → docs/encodings/character/
│   ├── Binary format (BCD, Gray Code)?  → docs/encodings/binary/
│   ├── Letter-to-number conversion?     → docs/encodings/numeric/
│   └── Visual code (QR, barcode)?       → docs/encodings/visual/
│
├── A one-way function (hash, checksum)?
│   → docs/hashing/
│   ├── Designed for security (MD5, SHA, BLAKE)? → docs/hashing/cryptographic/
│   ├── Designed for passwords (bcrypt, Argon2)? → docs/hashing/password/
│   └── Detects accidental errors (CRC, Luhn)?   → docs/hashing/checksums/
│
├── A cryptographic system or protocol (not a cipher)?
│   → docs/cryptography/
│
├── A mathematical concept or theorem?
│   → docs/mathematics/
│
├── An analysis method or attack technique?
│   → docs/analysis/
│
├── A technique for hiding data inside other data?
│   → docs/steganography/
│
├── An alphabet, script, or writing system?
│   → docs/writing-systems/
│   ├── Real historical script?  → docs/writing-systems/historical/
│   └── Fictional/constructed?   → docs/writing-systems/constructed/
│
├── A telecom, signaling, or phonetic code?
│   → docs/communication/
│
├── A numeral system (Roman, Mayan, binary)?
│   → docs/number-systems/
│
├── A puzzle guide, CTF resource, or famous artifact?
│   → docs/puzzles/
│
└── A browser-based interactive tool?
    → tools/
```

---

## 3. YAML Front Matter Rules

Every article **must** have YAML front matter. Required fields vary by type.

### Required for ALL articles

```yaml
title:        # Display name, properly capitalised
type:         # cipher | encoding | hash | cryptographic-concept |
              # analysis-method | tool | mathematical-concept |
              # writing-system | communication-code | puzzle-resource |
              # historical-document
status:       # stub | draft | review | complete
tags:         # At minimum: the type tag
created:      # YYYY-MM-DD
updated:      # YYYY-MM-DD
```

### Additional required fields for `type: cipher`

```yaml
category:     # classical | modern
subcategory:  # shift | monoalphabetic | polyalphabetic | homophonic |
              # polygraphic | symbolic | transposition | fractionation |
              # mechanical | block | stream
difficulty:   # beginner | intermediate | advanced | expert
broken:       # true | false
```

### Rules

- **No blank required fields.** If you don't know the value, use `"unknown"` or `null`, not an empty string.
- **`aliases` must cover** common misspellings, abbreviations, and alternative names.
- **`related` must link** to at least one MOC and one directly related article.
- **`tool_available`** must be kept accurate. If you add a tool, update this field in the cipher article.

---

## 4. Naming Conventions

| Thing | Convention | Example |
|---|---|---|
| Article files | `kebab-case.md` | `vigenere-cipher.md` |
| MOC files | `MOC-Title-Case.md` | `MOC-Polyalphabetic.md` |
| Tool files | `tool-kebab-case.md` | `tool-vigenere-cipher.md` |
| Template files | `template-type.md` | `template-cipher-article.md` |
| Folders | `kebab-case/` | `classical/polyalphabetic/` |
| Tags | `#lowercase-hyphen` | `#cipher/classical/shift` |
| Obsidian links | Title Case | `[[Vigenère Cipher]]` |

**Hard rules:**
- No `CamelCase` in filenames
- No spaces in filenames
- No version numbers in filenames
- No type prefix in article filenames (use YAML `type:` instead)
- Exception: tool articles use `tool-` prefix; MOC files use `MOC-` prefix

---

## 5. Article Quality Standards

### Minimum for `status: stub`
- YAML front matter complete
- Overview section (1–2 paragraphs)
- Classification table filled in
- At least one related article linked

### Minimum for `status: draft`
- All sections present (may be incomplete)
- Encryption and decryption process described
- At least one worked example

### Minimum for `status: review`
- All sections complete
- Worked example verified correct
- Security analysis written
- All internal links working
- YAML fully complete

### Minimum for `status: complete`
- Peer-reviewed by at least one other contributor
- External references verified
- Tool article exists (if applicable) or `tool_available: false` confirmed

---

## 6. Adding a New Cipher Article

1. Determine the correct folder using the decision tree above.
2. Copy `templates/template-cipher-article.md` to the correct folder.
3. Rename the file to `cipher-name.md` (kebab-case).
4. Fill in all YAML fields.
5. Write the article content following the template structure.
6. Add the cipher to the relevant MOC file(s):
   - The direct parent MOC (e.g., `MOC-Monoalphabetic.md`)
   - The family MOC (e.g., `MOC-Classical-Ciphers.md`) if it warrants a curated mention
   - Do NOT add to grandparent MOCs — Dataview queries handle bulk listing
7. Submit a pull request.

**Do NOT:**
- List the same cipher in multiple MOC files as an article entry
- Create a separate "Variants" folder — variants are siblings with `variant_of:` YAML field
- Create a "Military" or "Historical" article copy — use tags and the thematic MOC

---

## 7. Adding a New Encoding Article

1. Copy `templates/template-encoding-article.md`.
2. Place in `docs/encodings/{subcategory}/`.
3. Add `type: encoding` and set `purpose:` clearly.
4. Add to `MOC-Encodings.md` or the relevant sub-MOC.
5. Make clear in the Overview that this is NOT a cipher.

---

## 8. Adding a New Tool Article

1. Copy `templates/template-tool-article.md`.
2. Place in `tools/{function}/tool-cipher-name.md`.
3. Link back to the cipher article with `related_article:`.
4. Update the cipher article's `tool_available: true` and `tool_link:` fields.
5. Add to `MOC-Tools.md` under the correct category.

---

## 9. Updating MOC Files

MOC files are maintained manually for curated sections and automatically via Dataview for bulk lists.

**When to update a MOC manually:**
- Adding a cipher to a curated "Entry Points" or "Highlights" section
- Fixing a broken link

**When NOT to update a MOC manually:**
- Adding routine articles — the Dataview query at the bottom picks them up automatically

**Never** add duplicate entries to a MOC. If a cipher appears in a curated section, it does not also need to be in the alphabetical Dataview list (Dataview handles that).

---

## 10. Pull Request Checklist

Before submitting, confirm:

- [ ] File is in the correct folder (verified against decision tree)
- [ ] Filename is `kebab-case.md`
- [ ] YAML front matter is complete — no blank required fields
- [ ] `type:` field is set correctly
- [ ] `status:` reflects actual completeness
- [ ] Article follows the correct template structure
- [ ] All `[[wiki links]]` resolve to real files in the repo
- [ ] Cipher articles: worked example is verified correct
- [ ] Added to at least one MOC file
- [ ] No content duplicated from another article
- [ ] Spelling checked; cipher names use the most common English form
- [ ] If tool exists: `tool_available: true` and `tool_link:` filled in cipher article

---

*Questions? Open a GitHub Discussion.*
