# Jurdian Ciphers Lab — Architecture Review & Redesign

> **Document type:** Architecture specification  
> **Status:** Draft v1.0  
> **Scope:** Full knowledge base redesign for Obsidian + GitHub

---

## Table of Contents

1. [[#1. Architecture Review — What the Current Index Gets Right]]
2. [[#2. Critical Weaknesses of the Current Structure]]
3. [[#3. Recommended Repository Structure]]
4. [[#4. Recommended Category Hierarchy]]
5. [[#5. Navigation System — Maps of Content]]
6. [[#6. Metadata Schema (YAML Front Matter)]]
7. [[#7. Article Templates by Type]]
8. [[#8. Naming Conventions]]
9. [[#9. Obsidian Best Practices]]
10. [[#10. Final Recommendations]]

---

## 1. Architecture Review — What the Current Index Gets Right

Before criticizing, it's worth acknowledging what the existing structure does well:

- **Breadth:** The index captures ~95% of content from both source websites.
- **Classical grouping:** The shift/substitution/transposition/fractionation breakdown follows conventional cryptographic taxonomy.
- **Modern separation:** Distinguishing modern from classical is correct and necessary.
- **Steganography as a top-level domain:** Correct call. Steganography is a discipline, not a subset of ciphers.
- **Appendix B cipher identification table:** Good idea, wrong implementation (fragile markdown table — will rot).

The foundation is there. The execution needs serious work.

---

## 2. Critical Weaknesses of the Current Structure

These are not minor issues. Several are structural flaws that will make the knowledge base unmaintainable at scale.

### 2.1 The Master Index Is a 914-Line Flat List

A Master Index should be a **navigation hub**, not a complete catalog. The current file forces readers to scroll through 914 lines to find anything. At 500 articles, this becomes unusable.

**Fix:** The Master Index points to sub-indexes only. Sub-indexes (Maps of Content) point to articles.

---

### 2.2 Types Are Mixed Together Without Discipline

This is the single most damaging flaw. The current structure mixes these fundamentally different types of things into the same lists without distinction:

|Item|What it actually is|Where it currently lives|
|---|---|---|
|`[[Morse Code]]`|Communication code|Section 1.9 (Ciphers)|
|`[[Morse Audio Decoder]]`|Software tool|Section 1.9 (Ciphers)|
|`[[Hash Function]]`|Mathematical concept|Section 2.5 (Ciphers)|
|`[[Certificate Decoder]]`|Software tool|Section 2.7 (Crypto)|
|`[[Bubble Babble Code]]`|Encoding|Section 18 (Misc)|
|`[[UUID]]`|Identifier format|Section 18 (Misc)|
|`[[Zalgo Writing]]`|Text obfuscation|Section 3.4 (Encodings)|
|`[[Pig Latin]]`|Language game|Section 12.1 (Obfuscation)|
|`[[Klingon Language]]`|Constructed language|Section 9.3 (Symbol Ciphers)|
|`[[Leet Speak]]`|Internet slang|Section 7 (Telecom) + Section 12.1|

A knowledge base must be unambiguous about **what kind of thing** every article is. A reader looking for cipher articles should never have to wade past tool descriptions, encoding formats, and TV show alphabets.

**Fix:** Every article has a mandatory `type:` field in YAML. Navigation is organized by type first, then by topic.

---

### 2.3 Widespread Duplicate Entries

The following entries appear in **multiple sections** in the current index — this is a maintenance disaster:

|Article|Appears In|
|---|---|
|`[[ADFGVX Cipher]]`|§1.7 Fractionation AND §1.8 Grid AND §1.11 Military|
|`[[ADFGX Cipher]]`|§1.7 Fractionation AND §1.8 Grid AND §1.11 Military|
|`[[Bifid Cipher]]`|§1.5 Polygraphic AND §1.7 Fractionation AND §1.8 Grid|
|`[[Trifid Cipher]]`|§1.5 Polygraphic AND §1.7 Fractionation AND §1.8 Grid|
|`[[Playfair Cipher]]`|§1.5 Polygraphic AND §1.8 Grid|
|`[[Autoclave Cipher]]`|§1.3 Polyalphabetic AND §1.4 Autokey|
|`[[Jefferson Wheel Cipher]]`|§1.3 Polyalphabetic AND §1.10 Mechanical|
|`[[Enigma Machine]]`|§1.10 Mechanical AND §1.11 Military|
|`[[Diffie-Hellman Key Exchange]]`|§2.3 Asymmetric AND §2.4 Key Exchange AND §16.3 Math|
|`[[XOR Cipher]]`|§2.2 Stream AND §2.8 Low-Level|
|`[[Leet Speak]]`|§7 Telecom AND §12.1 Obfuscation|
|`[[Tally Marks]]`|§4.3 Numeric AND §13.4 Codes|

**Principle:** Every article lives in **exactly one folder**. Cross-referencing is done via **tags and backlinks**, never by listing the same article in two places in an index.

---

### 2.4 "Autokey Ciphers" Is Not a Real Category

Section 1.4 lists three items:

- `[[Autoclave Cipher]]` — already in §1.3
- `[[Beaufort Autokey Cipher]]` — a variant of Beaufort
- `[[Vigenère Autokey Cipher]]` — a variant of Vigenère

Autokey is a **key generation mode**, not a cipher family. These should be sibling articles to their parent ciphers with a `variant_of:` field and a `#autokey` tag. There is no reason to have a top-level category for three items that are variants of articles in the previous section.

---

### 2.5 "Grid & Polybius-Based" Is Not a Cipher Family

Section 1.8 lists 14 ciphers — all of which already exist in other categories (Polygraphic, Fractionation, Transposition). "Grid-based" is an **implementation characteristic**, not a cipher classification. It belongs as a `#grid-cipher` tag, not a category.

Same applies to "Morse-Based Ciphers" (Section 1.9). Fractionated Morse is a fractionation cipher. Pollux is a homophonic cipher. Morbit is a polygraphic cipher. They happen to use Morse — that's a tag, not a category.

---

### 2.6 Section 2 Mixes Ciphers, Hash Functions, and Concepts

Section 2 ("Modern Cryptography") contains:

- **Ciphers:** AES, DES, RC4, Blowfish (should be in `ciphers/modern/`)
- **Hash functions:** MD5, SHA, BLAKE (should be in `hashing/`)
- **Cryptographic concepts:** Key exchange, PKI (should be in `cryptography/concepts/`)
- **Software tools:** Certificate Decoder (should be in `tools/`)
- **Mathematical primitives:** XOR, circular bit shift (should be in `mathematics/`)

These are five completely different types of things. They should never be in the same section.

---

### 2.7 Section 9 (Symbol Ciphers) Will Explode

Section 9.3 "Fictional & Pop-Culture Alphabets" currently lists 80+ entries from video games, TV shows, and books. This section will grow to 200+ with no natural stopping point. More importantly, **a Klingon writing system is not a cipher**, and it doesn't belong in the same section as Pigpen or Rosicrucian.

**Fix:** Fictional/constructed scripts live in `writing-systems/constructed/`. Real historical scripts live in `writing-systems/historical/`. Classical symbol ciphers (Pigpen, Rosicrucian, Dancing Men) live in `ciphers/classical/substitution/symbolic/`. These are three completely different things.

---

### 2.8 Section 12.2 (Esoteric Programming Languages) Does Not Belong

Brainfuck, Malbolge, Shakespeare, and JSFuck are esoteric programming languages. They are not ciphers, not encodings, and not cryptographic tools. They are programming curiosities. Including them in a cipher knowledge base is a category error.

**Fix:** Either exclude them entirely, or create a clearly-labelled `miscellaneous/esolangs/` section that is explicitly out-of-scope for cryptographic purposes but included for completeness.

---

### 2.9 Appendix B Is a Maintenance Trap

The cipher identification table in Appendix B duplicates information that should live in a dedicated article (`cipher-identification-guide.md`) with proper structure, examples, and decision trees. A markdown table in an appendix will:

1. Go stale as new articles are added
2. Not be searchable in Obsidian
3. Break the single-source-of-truth principle

---

### 2.10 Missing Critical Categories

The current index is missing:

- **Cryptographic attacks** (Meet-in-the-middle, Birthday attack, Padding oracle, etc.)
- **Secret sharing** (Shamir's Secret Sharing, Blakley's scheme)
- **Zero-knowledge proofs** (conceptual coverage)
- **Information theory** (Shannon entropy, perfect secrecy, confusion/diffusion)
- **Cryptographic protocols** (TLS, PGP, Signal protocol as references)
- **Null ciphers** (hiding messages in plaintext)
- **Running key ciphers** (distinct from autokey)
- **ARG / Puzzle Design** guide articles
- **Glossary of terms**
- **Timeline of cryptography**

---

## 3. Recommended Repository Structure

```
jurdian-ciphers-lab/    
│    
├── README.md                        ← GitHub landing page (not an article)    
├── CONTRIBUTING.md                  ← How to add articles and tools    
├── CHANGELOG.md                     ← Version history    
├── .obsidian/                       ← Obsidian config (templates, snippets, graph settings)    
│    
├── docs/                            ← All knowledge base articles    
│   │    
│   ├── MOC-Master.md                ← Master Map of Content (navigation hub ONLY)    
│   │    
│   ├── ciphers/    
│   │   ├── MOC-Ciphers.md           ← Ciphers hub index    
│   │   │    
│   │   ├── classical/    
│   │   │   ├── MOC-Classical-Ciphers.md    
│   │   │   │    
│   │   │   ├── shift/    
│   │   │   │   ├── MOC-Shift-Ciphers.md    
│   │   │   │   ├── caesar-cipher.md    
│   │   │   │   ├── rot13-cipher.md    
│   │   │   │   ├── rot5-cipher.md    
│   │   │   │   ├── rot18-cipher.md    
│   │   │   │   ├── rot47-cipher.md    
│   │   │   │   ├── rot-n-cipher.md    
│   │   │   │   ├── shift-cipher.md    
│   │   │   │   ├── ascii-shift-cipher.md    
│   │   │   │   ├── keyboard-shift-cipher.md    
│   │   │   │   ├── keyed-caesar-cipher.md    
│   │   │   │   └── progressive-caesar-cipher.md    
│   │   │   │    
│   │   │   ├── substitution/    
│   │   │   │   ├── MOC-Substitution-Ciphers.md    
│   │   │   │   │    
│   │   │   │   ├── monoalphabetic/    
│   │   │   │   │   ├── MOC-Monoalphabetic.md    
│   │   │   │   │   ├── affine-cipher.md    
│   │   │   │   │   ├── atbash-cipher.md    
│   │   │   │   │   ├── bacon-cipher.md    
│   │   │   │   │   ├── book-cipher.md    
│   │   │   │   │   ├── consonants-vowels-rank-cipher.md    
│   │   │   │   │   ├── d3-code.md    
│   │   │   │   │   ├── k6-code.md    
│   │   │   │   │   ├── k7-code.md    
│   │   │   │   │   ├── malespin.md    
│   │   │   │   │   ├── modulo-cipher.md    
│   │   │   │   │   ├── monoalphabetic-substitution.md    
│   │   │   │   │   ├── multiplicative-cipher.md    
│   │   │   │   │   ├── null-cipher.md    
│   │   │   │   │   ├── periodic-table-cipher.md    
│   │   │   │   │   ├── prime-multiplication-cipher.md    
│   │   │   │   │   ├── prime-numbers-cipher.md    
│   │   │   │   │   ├── rozier-cipher.md    
│   │   │   │   │   ├── running-key-cipher.md    
│   │   │   │   │   ├── triliteral-cipher.md    
│   │   │   │   │   └── wolseley-cipher.md    
│   │   │   │   │    
│   │   │   │   ├── polyalphabetic/    
│   │   │   │   │   ├── MOC-Polyalphabetic.md    
│   │   │   │   │   ├── alberti-cipher.md    
│   │   │   │   │   ├── autoclave-cipher.md    
│   │   │   │   │   ├── bazeries-cipher.md    
│   │   │   │   │   ├── beaufort-cipher.md    
│   │   │   │   │   ├── beaufort-autokey-cipher.md    
│   │   │   │   │   ├── bellaso-cipher.md    
│   │   │   │   │   ├── chaocipher.md    
│   │   │   │   │   ├── gronsfeld-cipher.md    
│   │   │   │   │   ├── hill-cipher.md    
│   │   │   │   │   ├── nihilist-cipher.md    
│   │   │   │   │   ├── phillips-cipher.md    
│   │   │   │   │   ├── porta-cipher.md    
│   │   │   │   │   ├── ragbaby-cipher.md    
│   │   │   │   │   ├── slidefair-cipher.md    
│   │   │   │   │   ├── trithemius-cipher.md    
│   │   │   │   │   ├── variant-beaufort-cipher.md    
│   │   │   │   │   ├── vigenere-cipher.md    
│   │   │   │   │   ├── vigenere-autokey-cipher.md    
│   │   │   │   │   └── vigenere-multiplicative-cipher.md    
│   │   │   │   │    
│   │   │   │   ├── homophonic/    
│   │   │   │   │   ├── MOC-Homophonic-Ciphers.md    
│   │   │   │   │   ├── arnold-cipher.md    
│   │   │   │   │   ├── grandpre-cipher.md    
│   │   │   │   │   ├── homophonic-cipher.md    
│   │   │   │   │   ├── mexican-army-cipher-wheel.md    
│   │   │   │   │   ├── nomenclator-cipher.md    
│   │   │   │   │   └── numeric-homophonic-cipher.md    
│   │   │   │   │    
│   │   │   │   ├── polygraphic/    
│   │   │   │   │   ├── MOC-Polygraphic-Ciphers.md    
│   │   │   │   │   ├── bifid-cipher.md    
│   │   │   │   │   ├── collon-cipher.md    
│   │   │   │   │   ├── digrafid-cipher.md    
│   │   │   │   │   ├── four-square-cipher.md    
│   │   │   │   │   ├── morbit-cipher.md    
│   │   │   │   │   ├── playfair-cipher.md    
│   │   │   │   │   ├── pollux-cipher.md    
│   │   │   │   │   ├── polybius-cipher.md    
│   │   │   │   │   ├── three-square-cipher.md    
│   │   │   │   │   ├── trifid-cipher.md    
│   │   │   │   │   └── two-square-cipher.md    
│   │   │   │   │    
│   │   │   │   └── symbolic/    
│   │   │   │       ├── MOC-Symbolic-Ciphers.md    
│   │   │   │       ├── betamaze-cipher.md    
│   │   │   │       ├── birds-on-a-wire-cipher.md    
│   │   │   │       ├── clock-cipher.md    
│   │   │   │       ├── dancing-men-cipher.md    
│   │   │   │       ├── dorabella-cipher.md    
│   │   │   │       ├── elian-script.md    
│   │   │   │       ├── gold-bug-cipher.md    
│   │   │   │       ├── hexahue-cipher.md    
│   │   │   │       ├── ideograms-cipher.md    
│   │   │   │       ├── music-sheet-cipher.md    
│   │   │   │       ├── pigpen-cipher.md    
│   │   │   │       ├── rosicrucian-cipher.md    
│   │   │   │       ├── templars-cipher.md    
│   │   │   │       └── tic-tac-toe-cipher.md    
│   │   │   │    
│   │   │   ├── transposition/    
│   │   │   │   ├── MOC-Transposition-Ciphers.md    
│   │   │   │   ├── amsco-cipher.md    
│   │   │   │   ├── caesar-box-cipher.md    
│   │   │   │   ├── columnar-transposition-cipher.md    
│   │   │   │   ├── double-transposition-cipher.md    
│   │   │   │   ├── rail-fence-cipher.md    
│   │   │   │   ├── redefence-cipher.md    
│   │   │   │   ├── route-transposition-cipher.md    
│   │   │   │   ├── scytale-cipher.md    
│   │   │   │   ├── skip-cipher.md    
│   │   │   │   ├── spiral-cipher.md    
│   │   │   │   ├── swagman-cipher.md    
│   │   │   │   ├── transposition-cipher.md    
│   │   │   │   ├── turning-grille-cipher.md    
│   │   │   │   └── ubchi-cipher.md    
│   │   │   │    
│   │   │   ├── fractionation/    
│   │   │   │   ├── MOC-Fractionation-Ciphers.md    
│   │   │   │   ├── adfgvx-cipher.md    
│   │   │   │   ├── adfgx-cipher.md    
│   │   │   │   ├── bifid-cipher.md          ← canonical home for Bifid    
│   │   │   │   ├── fractionated-morse-cipher.md    
│   │   │   │   ├── monome-dinome-cipher.md    
│   │   │   │   └── trifid-cipher.md         ← canonical home for Trifid    
│   │   │   │    
│   │   │   └── mechanical/    
│   │   │       ├── MOC-Mechanical-Ciphers.md    
│   │   │       ├── chaocipher.md    
│   │   │       ├── cipher-disk.md    
│   │   │       ├── jefferson-wheel-cipher.md    
│   │   │       └── solitaire-cipher.md    
│   │   │    
│   │   ├── modern/    
│   │   │   ├── MOC-Modern-Ciphers.md    
│   │   │   │    
│   │   │   ├── block/    
│   │   │   │   ├── MOC-Block-Ciphers.md    
│   │   │   │   ├── aes-cipher.md    
│   │   │   │   ├── blowfish-cipher.md    
│   │   │   │   └── des-cipher.md    
│   │   │   │    
│   │   │   └── stream/    
│   │   │       ├── MOC-Stream-Ciphers.md    
│   │   │       ├── rc4-cipher.md    
│   │   │       ├── vernam-cipher.md    
│   │   │       └── xor-cipher.md    
│   │   │    
│   │   ├── military/    
│   │   │   ├── MOC-Military-Ciphers.md    
│   │   │   └── [articles are STUBS that link to canonical locations]    
│   │   │       ← This folder contains thematic MOC articles only,    
│   │   │         not duplicate cipher files. Ciphers live in classical/ or modern/    
│   │   │         and carry the tag #military    
│   │   │    
│   │   └── historical-unsolved/    
│   │       ├── MOC-Historical-Ciphers.md    
│   │       ├── copiale-cipher.md    
│   │       ├── dorabella-cipher.md    
│   │       ├── kryptos.md    
│   │       ├── mary-stuart-code.md    
│   │       ├── mccormick-cipher.md    
│   │       ├── medieval-ciphers.md    
│   │       ├── voynich-manuscript.md    
│   │       └── zodiac-killer-cipher.md    
│   │    
│   ├── cryptography/    
│   │   ├── MOC-Cryptography.md    
│   │   │    
│   │   ├── concepts/    
│   │   │   ├── confusion-and-diffusion.md    
│   │   │   ├── cryptographic-security-levels.md    
│   │   │   ├── information-theory.md    
│   │   │   ├── kerckhoffs-principle.md    
│   │   │   ├── perfect-secrecy.md    
│   │   │   ├── shannon-entropy.md    
│   │   │   └── symmetric-vs-asymmetric.md    
│   │   │    
│   │   ├── public-key/    
│   │   │   ├── MOC-Public-Key-Cryptography.md    
│   │   │   ├── diffie-hellman-key-exchange.md    
│   │   │   ├── elliptic-curve-cryptography.md    
│   │   │   └── rsa-algorithm.md    
│   │   │    
│   │   ├── key-management/    
│   │   │   ├── key-derivation-functions.md    
│   │   │   ├── key-exchange-protocols.md    
│   │   │   └── secret-sharing.md    
│   │   │    
│   │   └── pki/    
│   │       ├── digital-signatures.md    
│   │       ├── x509-certificate.md    
│   │       └── pgp-openpgp.md    
│   │    
│   ├── hashing/    
│   │   ├── MOC-Hashing.md    
│   │   │    
│   │   ├── cryptographic/    
│   │   │   ├── blake2-hash.md    
│   │   │   ├── blake3-hash.md    
│   │   │   ├── md4-hash.md    
│   │   │   ├── md5-hash.md    
│   │   │   ├── sha1-hash.md    
│   │   │   ├── sha256-hash.md    
│   │   │   └── sha512-hash.md    
│   │   │    
│   │   ├── password/    
│   │   │   ├── bcrypt.md    
│   │   │   ├── crypt-function.md    
│   │   │   ├── ntlm-hash.md    
│   │   │   └── pbkdf2.md    
│   │   │    
│   │   └── checksums/    
│   │       ├── crc32.md    
│   │       ├── luhn-algorithm.md    
│   │       └── verhoeff-algorithm.md    
│   │    
│   ├── encodings/    
│   │   ├── MOC-Encodings.md    
│   │   │    
│   │   ├── base/    
│   │   │   ├── MOC-Base-Encodings.md    
│   │   │   ├── base26-encoding.md    
│   │   │   ├── base32-encoding.md    
│   │   │   ├── base32-crockford.md    
│   │   │   ├── base36-encoding.md    
│   │   │   ├── base45-encoding.md    
│   │   │   ├── base58-encoding.md    
│   │   │   ├── base62-encoding.md    
│   │   │   ├── base64-encoding.md    
│   │   │   ├── base85-encoding.md    
│   │   │   ├── base91-encoding.md    
│   │   │   ├── base92-encoding.md    
│   │   │   ├── base100-encoding.md    
│   │   │   ├── base65536-encoding.md    
│   │   │   └── z-base32-encoding.md    
│   │   │    
│   │   ├── character/    
│   │   │   ├── MOC-Character-Encodings.md    
│   │   │   ├── ascii.md    
│   │   │   ├── baudot-code.md    
│   │   │   ├── bubble-babble-code.md    
│   │   │   ├── chuck-norris-unary-code.md    
│   │   │   ├── ebcdic.md    
│   │   │   ├── hex-encoding.md    
│   │   │   ├── leb128.md    
│   │   │   ├── punycode.md    
│   │   │   ├── unicode.md    
│   │   │   ├── url-encoding.md    
│   │   │   ├── utf8-encoding.md    
│   │   │   └── uuencode.md    
│   │   │    
│   │   ├── binary/    
│   │   │   ├── MOC-Binary-Encodings.md    
│   │   │   ├── bcd-binary-coded-decimal.md    
│   │   │   ├── bibi-binary-code.md    
│   │   │   ├── binary-code.md    
│   │   │   ├── excess3-code.md    
│   │   │   ├── gray-code.md    
│   │   │   └── little-big-endian.md    
│   │   │    
│   │   ├── numeric/    
│   │   │   ├── MOC-Numeric-Encodings.md    
│   │   │   ├── a1z26-cipher.md    
│   │   │   ├── fibonacci-encoding.md    
│   │   │   ├── greek-letter-number.md    
│   │   │   ├── letters-to-numbers.md    
│   │   │   ├── negafibonacci-encoding.md    
│   │   │   └── numbers-to-letters.md    
│   │   │    
│   │   └── visual/    
│   │       ├── MOC-Visual-Codes.md    
│   │       ├── aztec-barcode.md    
│   │       ├── barcode-39.md    
│   │       ├── barcode-93.md    
│   │       ├── barcode-128.md    
│   │       ├── barcode-codabar.md    
│   │       ├── barcode-ean8.md    
│   │       ├── barcode-ean13.md    
│   │       └── qr-code.md    
│   │    
│   ├── compression/    
│   │   ├── MOC-Compression.md    
│   │   ├── burrows-wheeler-transform.md    
│   │   ├── deflate.md    
│   │   ├── elias-delta-encoding.md    
│   │   ├── elias-gamma-encoding.md    
│   │   ├── gzip.md    
│   │   ├── huffman-coding.md    
│   │   ├── lzw-compression.md    
│   │   ├── rle-run-length-encoding.md    
│   │   └── zlib.md    
│   │    
│   ├── analysis/    
│   │   ├── MOC-Analysis.md    
│   │   │    
│   │   ├── cryptanalysis/    
│   │   │   ├── MOC-Cryptanalysis.md    
│   │   │   ├── attack-types-overview.md    
│   │   │   ├── birthday-attack.md    
│   │   │   ├── brute-force-attack.md    
│   │   │   ├── chosen-plaintext-attack.md    
│   │   │   ├── ciphertext-only-attack.md    
│   │   │   ├── differential-cryptanalysis.md    
│   │   │   ├── known-plaintext-attack.md    
│   │   │   ├── linear-cryptanalysis.md    
│   │   │   ├── meet-in-the-middle-attack.md    
│   │   │   └── side-channel-attack.md    
│   │   │    
│   │   ├── statistical/    
│   │   │   ├── MOC-Statistical-Analysis.md    
│   │   │   ├── bigrams-analysis.md    
│   │   │   ├── frequency-analysis.md    
│   │   │   ├── index-of-coincidence.md    
│   │   │   ├── kasiski-test.md    
│   │   │   ├── shannon-entropy-index.md    
│   │   │   └── trigrams-analysis.md    
│   │   │    
│   │   └── forensics/    
│   │       ├── MOC-Digital-Forensics.md    
│   │       ├── binary-analysis.md    
│   │       ├── binary-signature-scanning.md    
│   │       ├── exif-metadata.md    
│   │       ├── hex-dump-analysis.md    
│   │       ├── png-chunks-analysis.md    
│   │       └── zip-forensics.md    
│   │    
│   ├── mathematics/    
│   │   ├── MOC-Mathematics.md    
│   │   │    
│   │   ├── number-theory/    
│   │   │   ├── MOC-Number-Theory.md    
│   │   │   ├── bezouts-identity.md    
│   │   │   ├── chinese-remainder-theorem.md    
│   │   │   ├── discrete-logarithm.md    
│   │   │   ├── eulers-totient-function.md    
│   │   │   ├── extended-gcd.md    
│   │   │   ├── fermat-little-theorem.md    
│   │   │   ├── modular-arithmetic.md    
│   │   │   ├── modular-exponentiation.md    
│   │   │   ├── modular-multiplicative-inverse.md    
│   │   │   ├── prime-factorization.md    
│   │   │   └── prime-numbers.md    
│   │   │    
│   │   ├── information-theory/    
│   │   │   ├── entropy.md    
│   │   │   ├── hamming-distance.md    
│   │   │   ├── hamming-error-correcting-code.md    
│   │   │   ├── information-theory-overview.md    
│   │   │   └── perfect-secrecy.md    
│   │   │    
│   │   └── primitives/    
│   │       ├── circular-bit-shift.md    
│   │       ├── linear-feedback-shift-register.md    
│   │       └── xor-operation.md    
│   │    
│   ├── steganography/    
│   │   ├── MOC-Steganography.md    
│   │   │    
│   │   ├── image/    
│   │   │   ├── exif-steganography.md    
│   │   │   ├── invisible-ink-detection.md    
│   │   │   ├── lsb-steganography.md    
│   │   │   └── pixel-analysis.md    
│   │   │    
│   │   ├── audio/    
│   │   │   ├── audio-spectrogram.md    
│   │   │   ├── midi-steganography.md    
│   │   │   └── music-steganography.md    
│   │   │    
│   │   ├── text/    
│   │   │   ├── acrostic-cipher.md    
│   │   │   ├── null-cipher.md    
│   │   │   ├── whitespace-steganography.md    
│   │   │   └── zero-width-space.md    
│   │   │    
│   │   └── detection/    
│   │       ├── outguess-extractor.md    
│   │       ├── stegdetect.md    
│   │       └── steghide-extractor.md    
│   │    
│   ├── writing-systems/    
│   │   ├── MOC-Writing-Systems.md    
│   │   │    
│   │   ├── historical/    
│   │   │   ├── MOC-Historical-Writing-Systems.md    
│   │   │   ├── american-sign-language.md    
│   │   │   ├── braille-alphabet.md    
│   │   │   ├── chappe-semaphore.md    
│   │   │   ├── elder-futhark.md    
│   │   │   ├── enochian-alphabet.md    
│   │   │   ├── flag-semaphore.md    
│   │   │   ├── hieroglyphs.md    
│   │   │   ├── lingua-ignota.md    
│   │   │   ├── malachim-alphabet.md    
│   │   │   ├── moon-alphabet.md    
│   │   │   ├── nyctography.md    
│   │   │   ├── ogham-alphabet.md    
│   │   │   ├── passing-the-river-alphabet.md    
│   │   │   ├── theban-alphabet.md    
│   │   │   └── younger-futhark.md    
│   │   │    
│   │   └── constructed/    
│   │       ├── MOC-Constructed-Scripts.md    
│   │       ├── al-bhed-language.md    
│   │       ├── atlantean-language.md    
│   │       ├── aurebesh-alphabet.md    
│   │       ├── daedric-alphabet.md    
│   │       ├── dothraki-alphabet.md    
│   │       ├── dovahzul-language.md    
│   │       ├── enigma-machine.md    
│   │       ├── futurama-alien-alphabet.md    
│   │       ├── gnommish-language.md    
│   │       ├── gravity-falls-ciphers.md    
│   │       ├── hexahue-alphabet.md    
│   │       ├── hylian-language.md    
│   │       ├── illageralt-alphabet.md    
│   │       ├── klingon-language.md    
│   │       ├── kryptonian-alphabet.md    
│   │       ├── matoran-language.md    
│   │       ├── pigpen-cipher.md    
│   │       ├── sheikah-language.md    
│   │       ├── simlish-language.md    
│   │       ├── standard-galactic-alphabet.md    
│   │       ├── tenctonese-alphabet.md    
│   │       ├── theban-alphabet.md    
│   │       ├── unown-pokemon-alphabet.md    
│   │       ├── vulcan-language.md    
│   │       └── wingdings-font.md    
│   │    
│   ├── communication/    
│   │   ├── MOC-Communication-Codes.md    
│   │   │    
│   │   ├── telecom/    
│   │   │   ├── alternate-mark-inversion.md    
│   │   │   ├── baudot-code.md    
│   │   │   ├── decabit-code.md    
│   │   │   ├── dtmf-code.md    
│   │   │   ├── manchester-code.md    
│   │   │   ├── morse-code.md    
│   │   │   ├── t9-text-message.md    
│   │   │   └── wabun-code.md    
│   │   │    
│   │   ├── signals/    
│   │   │   ├── flag-semaphore.md    
│   │   │   ├── international-maritime-signals.md    
│   │   │   └── navy-signals-code.md    
│   │   │    
│   │   └── phonetic/    
│   │       ├── nato-phonetic-alphabet.md    
│   │       └── pgp-word-list.md    
│   │    
│   ├── number-systems/    
│   │   ├── MOC-Number-Systems.md    
│   │   ├── babylonian-numerals.md    
│   │   ├── bengali-numerals.md    
│   │   ├── binary-number-system.md    
│   │   ├── cistercian-numerals.md    
│   │   ├── dni-numerals.md    
│   │   ├── egyptian-numerals.md    
│   │   ├── hexadecimal.md    
│   │   ├── kaktovik-numerals.md    
│   │   ├── mayan-numerals.md    
│   │   ├── octal.md    
│   │   ├── roman-numerals.md    
│   │   ├── shadoks-numeral-system.md    
│   │   └── ternary.md    
│   │    
│   ├── puzzles/    
│   │   ├── MOC-Puzzles.md    
│   │   │    
│   │   ├── guides/    
│   │   │   ├── beginners-guide-to-ciphers.md    
│   │   │   ├── cipher-identification-guide.md    
│   │   │   ├── cryptic-crosswords-guide.md    
│   │   │   └── ctf-starter-guide.md    
│   │   │    
│   │   ├── famous-puzzles/    
│   │   │   ├── cicada-3301-overview.md    
│   │   │   ├── cicada-3301-liber-primus.md    
│   │   │   ├── cicada-3301-first-puzzle-walkthrough.md    
│   │   │   ├── kryptos-overview.md    
│   │   │   └── zodiac-ciphers-guide.md    
│   │   │    
│   │   └── design/    
│   │       ├── arg-design-principles.md    
│   │       ├── cipher-puzzle-design.md    
│   │       └── puzzle-difficulty-levels.md    
│   │    
│   └── references/    
│       ├── MOC-References.md    
│       ├── bibliography.md    
│       ├── cipher-identifier-quick-reference.md    
│       ├── cryptography-glossary.md    
│       ├── cryptography-timeline.md    
│       └── tool-index.md    
│    
├── tools/    
│   ├── MOC-Tools.md    
│   │    
│   ├── cipher-tools/    
│   │   ├── [tool articles for cipher-specific tools]    
│   │    
│   ├── encoding-tools/    
│   │   ├── [tool articles for encoding/decoding tools]    
│   │    
│   ├── analysis-tools/    
│   │   ├── [tool articles for analysis tools]    
│   │    
│   ├── hash-tools/    
│   │   ├── [tool articles for hashing tools]    
│   │    
│   └── visualization-tools/    
│       └── [tool articles for visualization tools]    
│    
├── assets/    
│   ├── images/    
│   │   ├── cipher-diagrams/    
│   │   ├── alphabet-charts/    
│   │   └── screenshots/    
│   ├── diagrams/    
│   │   └── [mermaid or drawio source files]    
│   └── data/    
│       └── [frequency tables, word lists, etc.]    
│    
└── templates/    
    ├── template-cipher-article.md    
    ├── template-encoding-article.md    
    ├── template-hash-article.md    
    ├── template-tool-article.md    
    ├── template-analysis-article.md    
    ├── template-writing-system-article.md    
    ├── template-moc.md    
    └── template-concept-article.md    
```

---

## 4. Recommended Category Hierarchy

The guiding principle: **organize by what a thing IS before organizing by what it does.**

### Tier 1 — Knowledge Domains (top-level folders)

```
ciphers/           → Algorithms that encrypt plaintext into ciphertext    
cryptography/      → Principles, protocols, and modern cryptographic systems    
hashing/           → One-way functions and checksums    
encodings/         → Format conversions without secrecy intent    
compression/       → Data size reduction algorithms    
analysis/          → Methods to break, analyze, or identify ciphers    
mathematics/       → Mathematical foundations used in cryptography    
steganography/     → Hiding information within other information    
writing-systems/   → Alphabets, scripts, and symbolic systems    
communication/     → Codes used for signaling and telecommunications    
number-systems/    → Numeral systems and representations    
puzzles/           → Guides, famous puzzles, and puzzle design    
references/        → Glossary, bibliography, timeline    
```

### Tier 2 — Classical Ciphers Subcategory Logic

This is the most complex area. The correct taxonomy is:

```
ciphers/classical/    
    shift/                  → Uniform alphabet shifts (Caesar family)    
    substitution/    
        monoalphabetic/     → One cipher alphabet, one-to-one mapping    
        polyalphabetic/     → Multiple cipher alphabets    
        homophonic/         → Many ciphertext symbols → one plaintext symbol    
        polygraphic/        → Multiple plaintext letters → multiple ciphertext (Playfair, Bifid)    
        symbolic/           → Symbol/glyph alphabets used as substitution ciphers    
    transposition/          → Letter positions rearranged, not substituted    
    fractionation/          → Letters fractioned then transposed (Bifid, ADFGVX)    
    mechanical/             → Mechanical devices (Enigma, Jefferson Wheel)    
```

**Critical classification decisions:**

|Cipher|Where it goes|Why|
|---|---|---|
|Bifid|`fractionation/`|Primary technique is fractionation of coordinates|
|Trifid|`fractionation/`|Same as Bifid but three-dimensional|
|Playfair|`polygraphic/`|Digraphic substitution is its defining characteristic|
|Polybius|`polygraphic/`|Coordinate-based, used as basis for others — not fractionation itself|
|ADFGVX|`fractionation/`|Polybius + fractionation + transposition|
|Nihilist|`polyalphabetic/`|Polybius-based but primarily polyalphabetic|
|VIC Cipher|`polyalphabetic/`|Complex polyalphabetic straddling checkerboard|
|Enigma|`mechanical/`|Defining characteristic is the rotor mechanism|
|Chaocipher|`mechanical/`|Mechanical disk-based polyalphabetic|
|Dancing Men|`substitution/symbolic/`|Symbol-substitution, not a separate cipher family|
|Pigpen|`substitution/symbolic/`|Same — symbol-substitution|
|Four-Square|`polygraphic/`|Digraphic substitution using four Polybius squares|

**Important:** `military/` and `historical-unsolved/` do NOT duplicate cipher articles. They contain:

- `military/`: MOC file + thematic essays about wartime cryptography
- `historical-unsolved/`: Articles about specific historical cipher **instances**, not the cipher algorithms themselves (e.g., Kryptos is an _instance_ using Vigenère + transposition, not a new cipher type)

---

## 5. Navigation System — Maps of Content (MOCs)

### 5.1 What Is a Map of Content?

A MOC is a note whose **sole purpose is navigation**. It does not contain article content. It lists links and brief descriptors to help readers find what they need.

### 5.2 MOC Hierarchy

```
MOC-Master.md    
├── [[MOC-Ciphers]]    
│   ├── [[MOC-Classical-Ciphers]]    
│   │   ├── [[MOC-Shift-Ciphers]]    
│   │   ├── [[MOC-Substitution-Ciphers]]    
│   │   │   ├── [[MOC-Monoalphabetic]]    
│   │   │   ├── [[MOC-Polyalphabetic]]    
│   │   │   ├── [[MOC-Homophonic-Ciphers]]    
│   │   │   ├── [[MOC-Polygraphic-Ciphers]]    
│   │   │   └── [[MOC-Symbolic-Ciphers]]    
│   │   ├── [[MOC-Transposition-Ciphers]]    
│   │   ├── [[MOC-Fractionation-Ciphers]]    
│   │   └── [[MOC-Mechanical-Ciphers]]    
│   ├── [[MOC-Modern-Ciphers]]    
│   │   ├── [[MOC-Block-Ciphers]]    
│   │   └── [[MOC-Stream-Ciphers]]    
│   └── [[MOC-Historical-Ciphers]]    
├── [[MOC-Cryptography]]    
├── [[MOC-Hashing]]    
├── [[MOC-Encodings]]    
│   ├── [[MOC-Base-Encodings]]    
│   ├── [[MOC-Character-Encodings]]    
│   └── [[MOC-Binary-Encodings]]    
├── [[MOC-Compression]]    
├── [[MOC-Analysis]]    
│   ├── [[MOC-Cryptanalysis]]    
│   └── [[MOC-Statistical-Analysis]]    
├── [[MOC-Mathematics]]    
├── [[MOC-Steganography]]    
├── [[MOC-Writing-Systems]]    
├── [[MOC-Communication-Codes]]    
├── [[MOC-Number-Systems]]    
├── [[MOC-Puzzles]]    
├── [[MOC-Tools]]    
└── [[MOC-References]]    
```

### 5.3 The Master MOC (Short Version)

The Master MOC is a single-screen navigation page. It should take **less than 30 seconds to scan**. Nothing more.

```markdown
# Jurdian Ciphers Lab — Master Index    
    
> Navigate by domain below. Each link goes to a sub-index.    
    
## 🔐 Cryptography    
- [[MOC-Ciphers]] — Classical, modern, historical cipher algorithms    
- [[MOC-Cryptography]] — Principles, protocols, public-key systems    
- [[MOC-Hashing]] — Hash functions, checksums, password hashing    
    
## 📦 Encoding & Data    
- [[MOC-Encodings]] — Base encodings, character sets, visual codes    
- [[MOC-Compression]] — Compression and lossless encoding algorithms    
- [[MOC-Number-Systems]] — Numeral systems across cultures    
    
## 🔍 Analysis    
- [[MOC-Analysis]] — Cryptanalysis, statistical methods, forensics    
- [[MOC-Mathematics]] — Number theory and mathematical foundations    
    
## 🫥 Hidden Data    
- [[MOC-Steganography]] — Image, audio, and text steganography    
    
## 🔣 Symbols & Scripts    
- [[MOC-Writing-Systems]] — Historical alphabets and constructed scripts    
    
## 📡 Communication    
- [[MOC-Communication-Codes]] — Morse, telecom, signaling, phonetic    
    
## 🧩 Puzzles & Research    
- [[MOC-Puzzles]] — CTF guides, ARG resources, famous puzzles    
- [[MOC-References]] — Glossary, timeline, bibliography    
    
## 🛠 Tools    
- [[MOC-Tools]] — Browser tools by category    
```

---

## 6. Recommended Metadata Schema (YAML Front Matter)

### 6.1 Universal Fields (all articles)

```yaml
---    
# ─── IDENTIFICATION ──────────────────────────────────────────────    
title: "Caesar Cipher"    
aliases:    
  - "Caesar's Cipher"    
  - "ROT-3"    
  - "Shift Cipher (Caesar)"    
    
# ─── CLASSIFICATION ──────────────────────────────────────────────    
type: cipher    
# Valid types: cipher | encoding | hash | cryptographic-concept |    
#              analysis-method | tool | mathematical-concept |    
#              writing-system | communication-code | puzzle-resource |    
#              historical-document    
    
category: classical    
subcategory: shift    
domain: ciphers/classical/shift    
    
# ─── ATTRIBUTES ──────────────────────────────────────────────────    
difficulty: beginner    
# Valid: beginner | intermediate | advanced | expert    
    
status: complete    
# Valid: stub | draft | review | complete    
    
# ─── HISTORICAL CONTEXT ──────────────────────────────────────────    
inventor: "Julius Caesar"    
year_invented: -50    
era: ancient    
# Valid: ancient | medieval | renaissance | 17th-century |    
#        18th-century | 19th-century | ww1 | ww2 | cold-war | modern    
    
# ─── CIPHER-SPECIFIC (only for type: cipher) ─────────────────────    
cipher_family: shift    
key_type: numeric    
# Valid: none | numeric | alphabetic | keyword | key-matrix |    
#        key-stream | key-schedule | asymmetric | passphrase    
    
key_length: "1 number (0-25)"    
plaintext_type: text    
ciphertext_type: text    
variant_of: "[[Shift Cipher]]"    
# (if this is a variant/special case of another cipher)    
    
broken: true    
# Whether this cipher is considered cryptographically broken    
    
# ─── CROSS-REFERENCES ────────────────────────────────────────────    
related:    
  - "[[ROT-13 Cipher]]"    
  - "[[Vigenère Cipher]]"    
  - "[[Affine Cipher]]"    
  - "[[Frequency Analysis]]"    
    
tool_available: true    
tool_link: "[[Tool - Caesar Cipher]]"    
    
# ─── TAGS ────────────────────────────────────────────────────────    
tags:    
  - cipher    
  - classical    
  - shift    
  - monoalphabetic    
  - substitution    
  - symmetric    
  - beginner    
  - historical    
  - broken    
  - roman    
    
# ─── METADATA ────────────────────────────────────────────────────    
created: 2025-01-01    
updated: 2025-06-28    
author: ""    
version: "1.0"    
---    
```

### 6.2 Type-Specific Extensions

#### For `type: encoding`

```yaml
reversible: true    
lossless: true    
purpose: data-transfer    
# Valid: data-transfer | obfuscation | compression | error-correction | identification    
output_alphabet: "A-Z, 2-7, ="    
standard: "RFC 4648"    
```

#### For `type: hash`

```yaml
output_bits: 256    
collision_resistant: true    
preimage_resistant: true    
cryptographic: true    
use_case: digital-signatures    
broken: false    
```

#### For `type: tool`

```yaml
tool_type: encryption    
# Valid: encryption | decryption | analysis | encoding | visualization | identification    
input_type: text    
output_type: text    
requires_key: true    
online_demo: "https://..."    
source_code: "https://github.com/..."    
```

#### For `type: writing-system`

```yaml
origin: historical    
# Valid: historical | fictional | constructed | symbolic    
culture: "Norse"    
period: "150–800 CE"    
script_type: alphabet    
# Valid: alphabet | syllabary | logographic | abjad | featural | symbolic    
used_as_cipher: false    
media_source: ""  # For fictional scripts: book/game/film source    
```

#### For `type: analysis-method`

```yaml
applies_to:    
  - "[[Monoalphabetic Substitution Cipher]]"    
  - "[[Caesar Cipher]]"    
attack_class: ciphertext-only    
# Valid: ciphertext-only | known-plaintext | chosen-plaintext | chosen-ciphertext | side-channel    
complexity: O(26)    
automated: true    
```

---

## 7. Article Templates by Type

### 7.1 Cipher Article Template

```markdown
---    
[YAML front matter as above]    
---    
    
# {{title}}    
    
> **One-line description.** What this cipher does in plain English.    
    
## Overview    
    
Brief introduction: what this cipher is, what family it belongs to, and why it matters.    
    
## History    
    
- **Inventor:** [[Person]]    
- **Year:**     
- **Era:**     
- **Original purpose:**     
    
Narrative history in 2–4 paragraphs.    
    
## Classification    
    
| Property | Value |    
|---|---|    
| Type | Cipher |    
| Family | [[MOC-Shift-Ciphers]] |    
| Variant of | [[Parent Cipher]] (if applicable) |    
| Key type | Numeric / Keyword / etc. |    
| Plaintext | Text |    
| Ciphertext | Text |    
| Broken? | Yes / No |    
    
## Known Variants & Related Ciphers    
    
- [[Related Cipher 1]] — how it differs    
- [[Related Cipher 2]] — how it differs    
    
## Encryption Process    
    
Step-by-step explanation of how to encrypt a message.    
    
### Formula    
    
```

C = (P + K) mod 26

```
    
Where:    
- `C` = ciphertext letter index    
- `P` = plaintext letter index      
- `K` = key (shift amount)    
    
### Worked Example    
    
**Plaintext:** `HELLO`      
**Key:** `3`      
**Ciphertext:** `KHOOR`    
    
Step-by-step walkthrough.    
    
## Decryption Process    
    
Step-by-step explanation of how to decrypt.    
    
### Formula    
    
```

P = (C - K + 26) mod 26

```
    
### Worked Example    
    
**Ciphertext:** `KHOOR`      
**Key:** `3`      
**Plaintext:** `HELLO`    
    
## Security Analysis    
    
### Strengths    
    
- Point 1    
- Point 2    
    
### Weaknesses    
    
- Point 1    
- Point 2    
    
### Known Attacks    
    
- [[Frequency Analysis]] — explain how it breaks this cipher    
- [[Brute Force Attack]] — explain feasibility    
    
## Cryptanalysis Walkthrough    
    
Practical demonstration of how to break this cipher.    
    
## Historical Usage    
    
Notable uses of this cipher in history, war, literature, or puzzles.    
    
## Applications    
    
Where this cipher is still used today (even if only pedagogically).    
    
## Interactive Tool    
    
[[Tool - Caesar Cipher]] — encrypt and decrypt with this tool.    
    
## Related Articles    
    
- [[ROT-13 Cipher]]    
- [[Vigenère Cipher]]    
- [[Frequency Analysis]]    
    
## References    
    
1. Author, *Book Title*, Publisher, Year.    
2. Author, "Article Title," *Journal*, Vol., Year.    
    
## External Resources    
    
- [Link 1](url) — description    
- [Link 2](url) — description    
```

---

### 7.2 Encoding Article Template

```markdown
---    
[YAML front matter]    
---    
    
# {{title}}    
    
> **One-line description.** Not a cipher — this converts data between formats.    
    
## Overview    
    
## Purpose & Use Cases    
    
Why this encoding exists. What problem it solves. Not a cipher.    
    
## Specification    
    
- **Standard:** RFC xxxx / ISO xxxx / informal    
- **Output alphabet:**     
- **Encoding ratio:** Input X bytes → Output Y characters    
- **Reversible:** Yes / No    
- **Lossless:** Yes / No    
    
## Encoding Process    
    
### Algorithm    
    
Step-by-step.    
    
### Example    
    
**Input:** `Hello`      
**Output:** `SGVsbG8=`    
    
## Decoding Process    
    
## Technical Details    
    
## Common Pitfalls    
    
- Padding confusion    
- Alphabet variants    
- URL-safe variants    
    
## Variants    
    
## Applications    
    
## Interactive Tool    
    
[[Tool - Base64 Encoder]]    
    
## Related Articles    
    
## References    
```

---

### 7.3 Hash Article Template

```markdown
---    
[YAML front matter]    
---    
    
# {{title}}    
    
> **One-line description.** A one-way function — cannot be reversed.    
    
## Overview    
    
## Specification    
    
| Property | Value |    
|---|---|    
| Output size | 256 bits (32 bytes) |    
| Block size | 512 bits |    
| Rounds | 64 |    
| Algorithm family | SHA-2 |    
| Status | Secure / Deprecated / Broken |    
    
## Algorithm Structure    
    
## Use Cases    
    
## Security Analysis    
    
### Current Status    
    
### Known Attacks    
    
## Comparison Table    
    
| Hash | Output | Speed | Status |    
|---|---|---|---|    
| MD5 | 128-bit | Very fast | Broken |    
| SHA-1 | 160-bit | Fast | Deprecated |    
| SHA-256 | 256-bit | Moderate | Secure |    
    
## Interactive Tool    
    
[[Tool - SHA-256 Hash Generator]]    
    
## Related Articles    
    
## References    
```

---

### 7.4 Tool Article Template

```markdown
---    
[YAML front matter with type: tool]    
---    
    
# Tool — {{cipher name}}    
    
> Browser-based tool for {{cipher name}}.    
    
## Tool Description    
    
What this tool does. Input/output description.    
    
## Supported Operations    
    
- [ ] Encrypt    
- [ ] Decrypt    
- [ ] Analyze    
- [ ] Identify    
- [ ] Convert    
    
## Input Format    
    
## Output Format    
    
## Parameters    
    
| Parameter | Type | Default | Description |    
|---|---|---|---|    
| Key | Integer | 3 | The shift amount |    
| Alphabet | Text | A-Z | Character set |    
    
## Usage Examples    
    
### Example 1 — Encrypt    
    
### Example 2 — Decrypt    
    
## Implementation Notes    
    
Technical notes for developers.    
    
## Related Cipher Article    
    
[[Caesar Cipher]]    
    
## Source Code    
    
[View source on GitHub](url)    
```

---

### 7.5 Map of Content (MOC) Template

```markdown
---    
type: moc    
title: "MOC — Classical Ciphers"    
domain: ciphers/classical    
tags: [moc, ciphers, classical]    
---    
    
# Classical Ciphers — Index    
    
> Navigation index. Each link goes to a cipher article or sub-index.    
> For the overview of classical cryptography, see [[Classical Cryptography Overview]].    
    
## Sub-Indexes    
    
- [[MOC-Shift-Ciphers]] — Caesar, ROT-13, and shift variants    
- [[MOC-Substitution-Ciphers]] — Monoalphabetic, polyalphabetic, homophonic, polygraphic    
- [[MOC-Transposition-Ciphers]] — Rail Fence, Columnar, and grid transpositions    
- [[MOC-Fractionation-Ciphers]] — Bifid, Trifid, ADFGVX    
- [[MOC-Mechanical-Ciphers]] — Enigma, Jefferson Wheel, Cipher Disk    
    
## Quick Navigation by Property    
    
**Beginner-friendly:** [[Caesar Cipher]] · [[ROT-13 Cipher]] · [[Atbash Cipher]] · [[Pigpen Cipher]]    
    
**Puzzle & CTF favorites:** [[Vigenère Cipher]] · [[Playfair Cipher]] · [[Bifid Cipher]] · [[Rail Fence Cipher]]    
    
**Historically significant:** [[Enigma Machine]] · [[ADFGVX Cipher]] · [[VIC Cipher]] · [[Nihilist Cipher]]    
    
**Unsolved / Famous:** [[Voynich Manuscript]] · [[Kryptos]] · [[Zodiac Killer Cipher]]    
    
## All Classical Ciphers (Alphabetical)    
    
[Auto-generated or manually maintained alphabetical list]    
```

---

## 8. Naming Conventions

### 8.1 Folders

- Always `kebab-case`
- Always lowercase
- No abbreviations unless universally recognized (`ctf`, `arg`, `pgp`)
- No version numbers in folder names

```
✅ ciphers/classical/shift/    
✅ encoding/base/    
✅ analysis/cryptanalysis/    
❌ Ciphers/Classical/Shift/    
❌ enc/b64/    
❌ analysis_methods/    
```

### 8.2 Article Files

Format: `{descriptive-name}.md`

- Always `kebab-case`
- Always lowercase
- Never include the type in the filename (it's in YAML)
- Exception: Tool articles prefix with `tool-`
- Exception: MOC files prefix with `MOC-` (capital, for visual distinction in file trees)

```
✅ caesar-cipher.md    
✅ base64-encoding.md    
✅ sha256-hash.md    
✅ tool-caesar-cipher.md    
✅ MOC-Ciphers.md    
❌ Caesar_Cipher.md    
❌ CaesarCipher.md    
❌ cipher-caesar.md       (type before name = confusing)    
❌ caesar-cipher-tool.md  (suffix is ambiguous)    
```

### 8.3 Obsidian Display Titles

Use the `title:` YAML field for proper display names. The file name is for navigation; the title is for display.

```yaml
# File: four-square-cipher.md    
title: "Four-Square Cipher"    
    
# File: aes-cipher.md    
title: "AES (Advanced Encryption Standard)"    
    
# File: sha256-hash.md    
title: "SHA-256 Hash Function"    
```

### 8.4 Tool Files

Format: `tool-{cipher-or-function}.md`

```
✅ tool-caesar-cipher.md    
✅ tool-base64-encoder.md    
✅ tool-frequency-analysis.md    
✅ tool-cipher-identifier.md    
✅ tool-sha256-generator.md    
```

### 8.5 MOC Files

Format: `MOC-{Domain-Name}.md`

```
✅ MOC-Master.md    
✅ MOC-Classical-Ciphers.md    
✅ MOC-Polyalphabetic.md    
✅ MOC-Base-Encodings.md    
❌ index-classical-ciphers.md    
❌ classical-ciphers-moc.md    
```

### 8.6 Templates

Format: `template-{type}.md`

```
✅ template-cipher-article.md    
✅ template-encoding-article.md    
✅ template-tool-article.md    
✅ template-moc.md    
```

### 8.7 Tags (Obsidian)

- Always lowercase
- Always singular when possible
- Hierarchical with `/` for Obsidian nested tags

```
#cipher    
#cipher/classical    
#cipher/classical/shift    
#cipher/modern    
#cipher/modern/block    
#encoding    
#encoding/base    
#hash    
#hash/cryptographic    
#analysis    
#analysis/statistical    
#tool    
#difficulty/beginner    
#difficulty/intermediate    
#era/ancient    
#era/ww2    
#era/modern    
#status/complete    
#status/stub    
#status/broken    
#technique/frequency-analysis    
#technique/kasiski    
#military    
#historical    
#unsolved    
#fictional-alphabet    
```

### 8.8 Aliases in YAML

Every article should have aliases covering:

1. The exact title
2. Common abbreviations (AES, DES, ROT13)
3. Common misspellings (Vigenère / Vigenere)
4. Alternative names used in different communities

```yaml
aliases:    
  - "Vigenere Cipher"         # Without accent (common search)    
  - "Vigenère Chiffre"        # French name    
  - "Le Chiffre Indéchiffrable"  # Historical name    
  - "Polyalphabetic Vigenère" # Descriptive variant    
```

---

## 9. Obsidian Best Practices

### 9.1 Graph View Organization

Obsidian's graph view becomes chaotic without discipline. To maintain a useful graph:

1. **MOC nodes** will naturally become hubs — this is correct and desired
2. **Type tags** allow color-coding by type in graph view
3. **Avoid orphaned notes** — every article must link to at least one MOC
4. **The "local graph" for a cipher article** should show: its MOC, its related ciphers, its analysis methods, and its tool — nothing more

**Recommended color coding in Obsidian Graph View settings:**

```
Red:     tag:#cipher    
Blue:    tag:#encoding      
Green:   tag:#hash    
Orange:  tag:#analysis    
Purple:  tag:#writing-system    
Yellow:  tag:#tool    
Gray:    tag:#moc    
White:   tag:#reference    
```

### 9.2 Obsidian Properties Panel

Enable the Properties panel view. Every article's YAML should be fully explorable via Properties.

Set these properties as "favorites" in Obsidian settings for quick access:

- `type`
- `difficulty`
- `status`
- `tool_available`
- `broken`

### 9.3 Templates Plugin

Use the Templater plugin (not the basic Templates plugin). Configure:

```
templates/ folder → Templater source folder    
```

Each template type maps to a keyboard shortcut:

- `Alt+C` → New cipher article
- `Alt+E` → New encoding article
- `Alt+H` → New hash article
- `Alt+T` → New tool article
- `Alt+M` → New MOC

### 9.4 Dataview Queries for Auto-Generated Lists

Use the Dataview plugin to auto-generate lists rather than maintaining them manually:

```markdown
## All Beginner-Friendly Ciphers (Auto-generated)    
    
\`\`\`dataview    
TABLE difficulty, era, tool_available AS "Tool?"    
FROM "docs/ciphers"    
WHERE type = "cipher" AND difficulty = "beginner"    
SORT title ASC    
\`\`\`    
```

```markdown
## All Broken Ciphers    
    
\`\`\`dataview    
LIST    
FROM "docs/ciphers"    
WHERE type = "cipher" AND broken = true    
SORT title ASC    
\`\`\`    
```

```markdown
## Ciphers Without a Tool Yet    
    
\`\`\`dataview    
TABLE category, subcategory    
FROM "docs/ciphers"    
WHERE type = "cipher" AND tool_available = false    
SORT title ASC    
\`\`\`    
```

```markdown
## Articles Still in Draft    
    
\`\`\`dataview    
TABLE type, status    
FROM "docs"    
WHERE status = "stub" OR status = "draft"    
SORT updated ASC    
\`\`\`    
```

These queries replace the brittle Appendix B tables entirely. They stay permanently current as new articles are added.

### 9.5 Backlinks as Cross-References

Never duplicate an article in two places to represent a cross-reference. Instead:

- Link to the article from related articles
- Tag appropriately
- Let Obsidian's backlinks panel show all articles that reference it

A cipher appearing in a "military ciphers" MOC is done via a **link in the MOC file**, not by duplicating the cipher file.

### 9.6 Callout Blocks for Standard Warnings

Define standard callout blocks for reuse:

```markdown
> [!warning] Cryptographically Broken    
> This cipher is **not secure** for modern use. It is included for historical and educational purposes only.    
    
> [!info] Classical Cipher    
> This is a **classical cipher** intended for puzzles, education, and historical study. Do not use it for real-world security.    
    
> [!tip] Tool Available    
> An interactive browser tool for this cipher is available: [[Tool - Caesar Cipher]]    
    
> [!example] Worked Example    
> The following example demonstrates encryption and decryption step by step.    
```

### 9.7 Folder Notes

Install the Folder Notes plugin. Each folder's MOC file acts as that folder's "folder note" — it opens automatically when you click the folder in the file tree.

Map:

```
docs/ciphers/ → MOC-Ciphers.md    
docs/ciphers/classical/ → MOC-Classical-Ciphers.md    
docs/encodings/ → MOC-Encodings.md    
```

### 9.8 Canvas for Visual Maps

Use Obsidian Canvas to create:

1. **Classical Cipher Family Tree** — visual relationship map
2. **Cryptographic Attack Surface** — which attacks break which ciphers
3. **Timeline Canvas** — historical progression of cryptography
4. **Encoding Comparison Canvas** — Base32 vs Base64 vs Base85 etc.

Store canvas files in: `assets/diagrams/canvas/`

---

## 10. Final Recommendations

### 10.1 Prioritized Action List

**Phase 1 — Foundation (do this first)**

1. Create the folder structure exactly as specified in Section 3
2. Write `MOC-Master.md` — keep it short
3. Write all domain-level MOC files (`MOC-Ciphers.md`, `MOC-Encodings.md`, etc.)
4. Create all 8 article templates with YAML front matter
5. Set up Obsidian plugins: Templater, Dataview, Folder Notes, Tag Wrangler

**Phase 2 — Core Content**  
6. Write the 30 most-referenced classical ciphers as complete articles first  
7. Priority order: Caesar → Vigenère → Playfair → Enigma → Bifid → Rail Fence → Atbash → Affine → Beaufort → Columnar Transposition  
8. Each article must reach `status: complete` before moving on  
9. Never create a stub for something already well-documented — write it properly

**Phase 3 — Expansion**  
10. Add encodings, hashing, and analysis articles  
11. Add tool articles as tools are built  
12. Add fictional alphabets and writing systems last (lowest research value)

---

### 10.2 The Single Most Important Rule

**One article, one location.**

Every piece of content lives in exactly one place. Cross-referencing is done through:

- Obsidian wiki links
- Tags
- Backlinks
- Dataview queries
- MOC files

Never copy-paste the same article or list item into multiple places. When the source changes, all copies become incorrect. This is the #1 cause of knowledge base rot.

---

### 10.3 Type Purity Enforced by Structure

The folder structure itself enforces type purity:

- If it's in `docs/ciphers/` it's a cipher algorithm
- If it's in `docs/encodings/` it's an encoding format
- If it's in `docs/writing-systems/` it's a script or alphabet
- If it's in `tools/` it's a tool description

Never mix them. A "Morse Code" article goes in `docs/communication/telecom/morse-code.md`. The Morbit Cipher (which uses Morse as fractionation) goes in `docs/ciphers/classical/polygraphic/morbit-cipher.md`. The fact that Morbit uses Morse is captured by a `related:` field and a `[[Morse Code]]` backlink — not by putting Morbit in a "Morse-based" category.

---

### 10.4 Scalability Benchmarks

This architecture is designed to handle:

|Content type|Current|At 500 articles|
|---|---|---|
|Cipher articles|~150 possible|Handled by depth-3 subfolders|
|Encoding articles|~40|One flat `encodings/base/` folder|
|Writing system articles|~100|Split historical/constructed|
|Analysis articles|~20|Stays small — few methods exist|
|Tool articles|~100|Mirror structure in `tools/`|
|MOC files|~25|One per folder — self-maintaining|

No restructuring will be needed until 1,000+ articles, at which point only `writing-systems/constructed/` may need subfolder splitting (by media franchise).

---

### 10.5 Things Deliberately Excluded

The following are **excluded by design** and should be clearly labelled as out-of-scope:

|Item|Reason|
|---|---|
|Esoteric programming languages (Brainfuck, etc.)|Not cryptography; category error|
|Numerology (Gematria, Pythagorean numerology)|Occult, not cryptographic|
|Word game solvers (Wordle, Scrabble)|Completely off-topic|
|Accent generators (British, French accent)|Off-topic|
|Sudoku solvers|Off-topic|
|Chemical/physics tools|Off-topic|

If any of these are desired for completeness, create a `miscellaneous/` folder with a clear disclaimer that it is outside the cryptographic scope of the knowledge base.

---

### 10.6 Contributing Guidelines Essentials

`CONTRIBUTING.md` must include:

1. **Article placement decision tree** — a flowchart to determine which folder an article belongs in
2. **Mandatory YAML fields** — which fields are required vs optional
3. **Minimum article quality bar** — a stub must have at least an Overview, Classification table, and Encryption/Decryption Process
4. **Naming convention reference** — a single table of all naming rules
5. **Template usage instructions** — how to use Templater shortcuts
6. **Review process** — who reviews new articles before `status: complete`

---

_End of Architecture Review — Jurdian Ciphers Lab v1.0_

---

**Related Documents:**

- [[MOC-Master]] — The redesigned Master Index
- [[template-cipher-article]] — Cipher article template
- [[template-encoding-article]] — Encoding article template
- [[template-moc]] — MOC template