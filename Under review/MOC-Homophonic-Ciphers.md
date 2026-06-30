---
type: moc
title: "MOC — Homophonic Ciphers"
aliases:
  - "Homophonic Substitution Index"
tags:
  - moc
  - cipher
  - classical
  - substitution
  - homophonic
created: 2025-01-01
updated: 2025-06-28
---

# Homophonic Ciphers — Index

> **Definition:** A homophonic cipher maps each plaintext letter to multiple possible ciphertext symbols. The sender chooses randomly among the options. This flattens the frequency distribution of the ciphertext, defeating standard frequency analysis.
> ← Back to [[MOC-Substitution-Ciphers]]

---

## Core Concept

In a standard monoalphabetic cipher, `E` always produces the same ciphertext symbol. In a homophonic cipher, `E` (the most frequent English letter) might map to any of `17, 42, 63, 88` — and the sender picks one randomly each time.

If the number of homophones allocated to each letter is **proportional to its natural frequency**, the resulting ciphertext has a **flat frequency distribution**, making standard [[Frequency Analysis]] ineffective.

**Key trade-off:** Security increases with the number of homophones, but the key size and ciphertext length both grow accordingly.

---

## Ciphers in This Family

- [[Arnold Cipher]] — Numeric homophones; used by Benedict Arnold in the American Revolutionary War
- [[Grandpré Cipher]] — 10×10 grid; each row provides 10 homophones for one letter
- [[Homophonic Cipher]] — The general form; any scheme assigning multiple ciphertext symbols per letter
- [[Mexican Army Cipher Wheel]] — Mechanical cipher wheel with homophonic output
- [[Nomenclator Cipher]] — Hybrid: code-book for common words + homophonic cipher for letters; historically dominant
- [[Numeric Homophonic Cipher]] — General numeric homophonic substitution

---

## Historical Significance

Homophonic ciphers dominated professional cryptography from the Renaissance through the 18th century. The [[Nomenclator Cipher]] in particular was used by most European courts and governments.

Notable historical uses:
- [[Mary Stuart Code]] — Nomenclator system used by Mary Queen of Scots; broken by Thomas Phelippes
- [[Arnold Cipher]] — Benedict Arnold's treasonous correspondence with British Army

---

## Cryptanalysis

Homophonic ciphers resist basic frequency analysis, but remain vulnerable to:

1. **Extended frequency analysis** — With sufficient ciphertext, homophone groups cluster around their plaintext frequencies
2. **Contact analysis** — Certain homophones will never appear adjacent to certain others (based on English digraph rules)
3. **Known plaintext** — Partial decryption rapidly reveals the full homophone table
4. **Key recovery** — Once the table is reconstructed, decryption is trivial

**Minimum ciphertext for reliable attack:** ~500+ characters; often more for well-designed systems.

---

## Interactive Tools

- [[Tool - Homophonic Cipher]]
- [[Tool - Grandpré Cipher]]

---

## All Homophonic Ciphers

```dataview
TABLE difficulty, year_invented, tool_available AS "Tool?"
FROM "docs/ciphers/classical/substitution/homophonic"
WHERE type = "cipher"
SORT title ASC
```
