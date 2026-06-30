# Jurdian Ciphers Lab

> **An open-source knowledge base for ciphers, cryptography, encodings, steganography, and code-breaking.**

Built for: CTF players · ARG creators · puzzle designers · cryptography researchers · developers · curious beginners.

---

## What's Inside

| Section | Contents |
|---|---|
| **Ciphers** | 150+ classical, modern, military, and historical cipher articles |
| **Cryptography** | Principles, protocols, public-key systems, PKI |
| **Hashing** | Hash functions, password hashing, checksums |
| **Encodings** | Base32/64/85, ASCII, Unicode, barcodes, binary formats |
| **Analysis** | Frequency analysis, Kasiski test, cryptanalysis attack types |
| **Mathematics** | Number theory, information theory, cryptographic primitives |
| **Steganography** | Image, audio, text steganography and detection |
| **Writing Systems** | 50+ historical alphabets and 80+ fictional/constructed scripts |
| **Communication** | Morse, semaphore, NATO phonetic, telecom codes |
| **Puzzles** | CTF guides, ARG resources, famous unsolved ciphers |
| **Tools** | 100+ browser-based cipher and analysis tools |

---

## Quick Start

**New to cryptography?** → Start with [Beginner's Guide to Ciphers](docs/puzzles/guides/beginners-guide-to-ciphers.md)

**Solving a CTF challenge?** → [Cipher Identification Guide](docs/references/cipher-identification-guide.md) · [CTF Starter Guide](docs/puzzles/guides/ctf-starter-guide.md)

**Looking for a specific cipher?** → [Master Index](docs/MOC-Master.md)

**Building with this repo?** → [Contributing Guide](CONTRIBUTING.md)

---

## Repository Structure

```
jurdian-ciphers-lab/
├── docs/
│   ├── MOC-Master.md              ← Start here
│   ├── ciphers/                   ← All cipher articles
│   │   ├── classical/             ← Shift, substitution, transposition, fractionation, mechanical
│   │   ├── modern/                ← Block ciphers, stream ciphers
│   │   ├── military/              ← Thematic wartime index
│   │   └── historical-unsolved/   ← Famous unsolved cipher instances
│   ├── cryptography/              ← Concepts, protocols, PKI
│   ├── hashing/                   ← Hash functions and checksums
│   ├── encodings/                 ← Data format conversions
│   ├── compression/               ← Compression algorithms
│   ├── analysis/                  ← Cryptanalysis and statistical methods
│   ├── mathematics/               ← Number theory and foundations
│   ├── steganography/             ← Hidden data techniques
│   ├── writing-systems/           ← Alphabets and constructed scripts
│   ├── communication/             ← Telecom and signaling codes
│   ├── number-systems/            ← Numeral systems
│   ├── puzzles/                   ← CTF, ARG, puzzle design
│   └── references/                ← Glossary, timeline, bibliography
├── tools/                         ← Browser-based tool articles
├── assets/                        ← Images, diagrams, data files
├── templates/                     ← Obsidian article templates
└── .obsidian/                     ← Obsidian configuration
```

---

## Design Principles

1. **One article, one location.** Every cipher lives in exactly one folder. Cross-references use wiki links and tags — never duplicate files.
2. **Type purity.** Ciphers, encodings, hashes, and writing systems are never mixed in the same section.
3. **Scalable to 500+ articles.** The MOC system scales without restructuring.
4. **Obsidian-native.** Dataview queries, Templater templates, and backlinks keep content current automatically.

---

## Using with Obsidian

1. Clone this repository
2. Open the repo folder as an Obsidian vault
3. Install recommended plugins: **Dataview**, **Templater**, **Folder Notes**, **Tag Wrangler**
4. Open `docs/MOC-Master.md` as your home note
5. Set `docs/MOC-Master.md` as your Obsidian start-up note

**Recommended graph view colors:**

| Color | Tag |
|---|---|
| Red | `#cipher` |
| Blue | `#encoding` |
| Green | `#hash` |
| Orange | `#analysis` |
| Purple | `#writing-system` |
| Yellow | `#tool` |
| Gray | `#moc` |

---

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for full guidelines.

**Quick rules:**
- Every article needs complete YAML front matter
- Use the template in `templates/` matching your article type
- One article per cipher — no duplicates
- Alphabetical order within MOC lists
- All internal links use Obsidian wiki link format `[[Article Name]]`

---

## Sources & Credits

Content synthesized and expanded from:
- [dCode.fr](https://www.dcode.fr/en) — Comprehensive cipher tool collection
- [Boxentriq.com](https://www.boxentriq.com) — Cipher tools and puzzle resources
- Primary academic sources listed in [Bibliography](docs/references/bibliography.md)

---

## License

[MIT License](LICENSE) — Free to use, modify, and distribute with attribution.
