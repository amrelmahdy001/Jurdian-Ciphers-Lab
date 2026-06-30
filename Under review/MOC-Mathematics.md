---
type: moc
title: "MOC — Mathematics"
aliases:
  - "Mathematics Index"
  - "Cryptographic Mathematics"
  - "Number Theory Index"
tags:
  - moc
  - mathematics
created: 2025-01-01
updated: 2025-06-28
---

# Mathematics — Index

> **Definition:** Mathematical foundations underlying cryptographic algorithms. These are concepts, theorems, and operations — not ciphers or encodings.
> ← Back to [[MOC-Master]]

---

## Sub-Indexes
- [[MOC-Number-Theory]] — Primes, modular arithmetic, discrete logarithm
- [[MOC-Information-Theory]] — Entropy, perfect secrecy, Hamming distance

---

## Number Theory

### Modular Arithmetic
- [[Modular Arithmetic]] — The foundation of nearly all classical and modern cipher mathematics
- [[Modular Exponentiation]] — Computing `a^b mod n` efficiently; core of RSA and Diffie-Hellman
- [[Modular Multiplicative Inverse]] — Finding `x` such that `ax ≡ 1 (mod n)`; needed for affine cipher decryption
- [[Chinese Remainder Theorem]] — Solving systems of modular equations; used in RSA optimization
- [[Euler's Totient Function]] — Count of integers coprime to n; foundational to RSA

### Prime Numbers
- [[Prime Numbers]] — Integers with no divisors other than 1 and themselves
- [[Prime Factorization]] — Decomposing integers into prime factors; difficulty underpins RSA
- [[Fermat's Little Theorem]] — `a^p ≡ a (mod p)` for prime p; used in modular exponentiation

### Algorithms
- [[Extended GCD Algorithm]] — Finds GCD and Bézout coefficients; used for modular inverse
- [[Bezout's Identity]] — Linear combination expression for GCD
- [[Discrete Logarithm]] — Finding x in `g^x ≡ y (mod p)`; hardness underpins DH and ECC

---

## Abstract Algebra

- [[Groups in Cryptography]] — Mathematical groups and their role in modern crypto
- [[Finite Fields (Galois Fields)]] — GF(2^8) is the field underlying AES
- [[Elliptic Curves]] — Foundation of Elliptic Curve Cryptography (ECC)

---

## Information Theory

- [[Shannon Entropy]] — Measure of uncertainty/information content; H = -Σ p log p
- [[Perfect Secrecy]] — Shannon's definition; ciphertext reveals zero information about plaintext
- [[Confusion and Diffusion]] — Shannon's two design principles for strong block ciphers
- [[Hamming Distance]] — Number of positions where two strings differ
- [[Hamming Error-Correcting Code]] — Code that can detect and correct single-bit errors

---

## Low-Level Cryptographic Primitives
- [[XOR Operation]] — Bitwise exclusive-or; foundation of stream ciphers and one-time pads
- [[Circular Bit Shift]] — Rotate bits left/right; used in hash functions and block ciphers
- [[Linear Feedback Shift Register]] — Pseudorandom sequence generator; used in stream ciphers
- [[S-Box]] — Non-linear substitution table; provides confusion in block ciphers
- [[Feistel Network]] — Symmetric cipher construction; used in DES

---

## All Mathematics Articles

```dataview
TABLE subcategory
FROM "docs/mathematics"
WHERE type = "mathematical-concept"
SORT title ASC
```
