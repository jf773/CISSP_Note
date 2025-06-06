# Chapter 6: Cryptography and Symmetric Key Algorithms

- [Cryptographic Foundations]()
  - [Goals of Cryptography]()
  - [Cryptography Concepts]()
  - [Cryptographic Mathematics]()
  - [Ciphers]()
- [Modern Cryptography]()
  - [Cyrptographic Keys]()
  - [Symmetic Key Algorithms]()
  - [Asymmetic Key Algorithms]()
  - [Hashing Algorithms]()
- [Symmetric Cryptography]()
  - [Block Cipher Modes of Operation]()
  - [Data Encryption Standard]()
  - [Triple DES]()
  - [International Data Encryption Algorithm]()
  - [Blowfish]()
  - [SKIPJACK]()
  - [Rivest Ciphers]()
  - [Advanced Encryption Standard]()
  - [CAST]()
  - [Comparison of Symmetric Encryption Algorithms]()
  - [Symmetric Key Management]()
- [Cryptographic Life Cycle]()
- [Summary]()


## Cryptographic Foundations  

### Goals of Cryptography  
| Goal | Security Service Provided | Example Control |
|------|---------------------------|-----------------|
| **Confidentiality** | Prevent disclosure | AES, TLS |
| **Integrity** | Detect alteration | SHA-256, HMAC |
| **Authentication** | Verify identity/source | Digital signature, MAC |
| **Non-repudiation** | Prevent sender denial | PKI sigs, log hashes |  

### Cryptography Concepts  
- **Plaintext ↔ Ciphertext** via algorithm + key.  
- **Confusion** (hide relationship between key & ciphertext) & **Diffusion** (spread influence over output) → Claude Shannon.  
- **Key space** size = 2^bits; work factor measures brute-force difficulty.  
- **Kerckhoffs’ principle:** secrecy should reside **only in the key**.

### Cryptographic Mathematics  
- **Modular arithmetic**, prime factoring, discrete logarithms, elliptic curves.  
- *n ≡ a (mod m)* forms basis of RSA, DH, ECC.  
- **Avalanche effect:** small input change ⇒ ~50 % output bits flip.

### Ciphers  
- **Substitution** (Caesar, Vigenère), **Transposition**, **Stream** vs **Block**.  
- **One-Time Pad** offers perfect secrecy if key random, same length, used once.

---

## Modern Cryptography  

### Cryptographic Keys  
- **Randomness & entropy** critical; use HRNG or CSPRNG.  
- Secure distribution: out-of-band, PKI, DH, QKD.  
- **Key escrow, split knowledge, dual control** for high assurance.

### Symmetric Key Algorithms  
| Algorithm | Key bits | Notes |
|-----------|----------|-------|
| **DES** | 56 | Feistel; obsolete (brute-forced) |
| **3DES** | 112/168 | Encrypt-Decrypt-Encrypt; legacy |
| **AES** | 128/192/256 | Rijndael; federal standard |
| **Blowfish** | 32–448 | Fast, free; 64-bit block |
| **Twofish / CAST / IDEA / RC-series / Skipjack** | Vary | Niche/legacy uses |

### Asymmetric Key Algorithms  
- **RSA** (factorization), **Diffie-Hellman** & **ElGamal** (discrete log),  
  **ECC / ECDH / ECDSA** (elliptic curve), **DSA**.  
- Provide **key exchange, digital signatures, PKI**, but are slower than symmetric crypto.

### Hashing Algorithms  
- **MD5, SHA-1** (deprecated), **SHA-2 family**, **SHA-3 (Keccak)**, **RIPEMD**, **Whirlpool**.  
- Properties: one-way, fixed length, collision- & pre-image-resistant.  
- **Salting** defends against rainbow tables; **key-stretch** PBKDF2, bcrypt, scrypt, Argon2.

---

## Symmetric Cryptography  

### Block Cipher Modes of Operation  
| Mode | Feature | Caveat |
|------|---------|--------|
| **ECB** | Simple, parallelizable | Pattern leaks |
| **CBC** | Adds IV, good default | Sequential, error-propagation |
| **CFB/OFB** | Self-synchronizing stream | Throughput = 1 block |
| **CTR** | Parallel, random access | Requires unique nonce |
| **GCM, XTS** | Authenticated & disk encryption | Tag management critical |

### Data Encryption Standard  
- 64-bit block, 56-bit key, 16 Feistel rounds; deprecated since 1998 **DES-Cracker**.

### Triple DES  
- 3 × DES (EDE); keying options K1-K2-K3; provides 112/168-bit effective strength; slow.

### International Data Encryption Algorithm  
- 128-bit key, 64-bit block; patented, strong but less common today.

### Blowfish  
- Bruce Schneier; variable-length key; 16 rounds; free; replaced by **Twofish** in some apps.

### SKIPJACK  
- NSA “Clipper Chip”; 80-bit key; no longer favored.

### Rivest Ciphers  
- **RC2/RC4** (stream; RC4 now banned in TLS), **RC5/RC6** (block).

### Advanced Encryption Standard  
- **Rijndael**; 128-bit block; 10/12/14 rounds; hardware acceleration (AES-NI).  
- Ubiquitous (TLS, VPN, disk encryption).

### CAST  
- **CAST-128 / CAST-256**; used by PGP; 64/128-bit block.

### Comparison of Symmetric Encryption Algorithms  
- Strength depends on **key size & block size**.  
- AES & Twofish outperform 3DES, DES, IDEA in both speed & security.

### Symmetric Key Management  
- **Generate → Distribute → Store → Use → Rotate → Revoke/Destroy**.  
- Employ **KMS/HSM**, key hierarchy (Key-Encrypting Key vs Data Key).  
- Limit key lifetime; enforce dual control for master keys.

---

## Cryptographic Life Cycle  
1. **Initiation** – Determine business need & risk.  
2. **Development/Acquisition** – Select algorithm, design key mgmt.  
3. **Implementation** – Integrate into systems, configure modes, store keys securely.  
4. **Operation & Maintenance** – Monitor strength, rotate keys, patch libraries.  
5. **Disposition** – Decommission algorithms/keys (NIST SP 800-57 guidance).

---

## Summary  
CISSP crypto mastery = understand **why** (CIA, integrity, auth), **how** (math, modes, key mgmt) and **when** to use each algorithm.  
Exam favorites:  
- Contrast **symmetric vs asymmetric** pros/cons.  
- Know **AES key sizes, DES weaknesses, mode characteristics (ECB vs CBC vs GCM)**.  
- Identify **hashing properties, collision attacks, key-stretch functions**.  
- Lifecycle & key-management best practices (split knowledge, escrow, rotation).  
Expect scenario Qs on algorithm choice, IV misuse, key distribution failures, and deciphering mode acronyms.





