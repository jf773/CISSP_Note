# Chapter 7: PKI and Cryptographic Applications

- [Asymmetric Cryptography]()
  - [Public and Private Keys]()
  - [RSA]()
  - [ElGamal]()
  - [Elliptic Curve Cryptography]()
  - [Diffie-Hellman Key Exchange]()
  - [Quantum Cryptography]()
- [Hash Functions]()
  - [SHA Family]()
  - [MD5]()
  - [RIPEMD]()
  - [Comparison of Hash Function Value Lengths]()
- [Digital Signatures]()
  - [HMAC]()
  - [Digital Signature Standard]()
- [Public Key Infrastructure]()
  - [Certificates]()
  - [Certificate Authorities]()
  - [Certificate life Cycle]()
  - [Certificate Formats]()
- [Asymmetric Key Management]()
- [Hybrid Cryptography]()
- [Applied Cryptography]()
  - [Portable Devices]()
  - [Email]()
  - [Web Applications]()
  - [Steganography and Watermarking]()
  - [Networking]()
  - [Emerging Applications]()
- [Cryptographic Attacks]()
- [Summary]()

## Asymmetric Cryptography  

### Public and Private Keys  
- **Key pair**: public key shared freely; private key kept secret.  
- Functions: **encryption, digital signatures, key exchange**.  
- Security depends on hardness of underlying math problem and **private-key protection**.

### RSA  
- Based on **integer-factorization** (n = p × q).  
- Key lengths ≥ 2048-bit (CISSP minimum); supports enc & signatures.  
- Use **PKCS #1 v2.2 (OAEP/PSS)** for modern padding.

### ElGamal  
- Discrete-logarithm variant; generates **ciphertext of double size**.  
- Often used in **PGP** for session-key encryption.

### Elliptic Curve Cryptography (ECC)  
- Security from **elliptic-curve discrete log**; much smaller keys  
  (e.g., 256-bit ECC ≈ 3072-bit RSA).  
- Algorithms: **ECDH, ECDSA, Ed25519**; ideal for mobile/IoT.

### Diffie-Hellman Key Exchange  
- First public key-agreement protocol (1976).  
- Provides **perfect forward secrecy** (with ephemeral keys → DHE/ECDHE).  
- Vulnerable to **MITM if unauthenticated**.

### Quantum Cryptography  
- **QKD** (BB84) uses photon polarization; eavesdropping causes errors.  
- Post-quantum algorithms (NIST PQC finalists) resist **Shor’s attack**.

---

## Hash Functions  

### SHA Family  
| Version | Digest bits | Notes |
|---------|-------------|-------|
| SHA-1 | 160 | Broken collisions (2017) |
| SHA-2 (SHA-256/512) | 256/512 | Current FIPS standard |
| SHA-3 (Keccak) | 224-512 | Sponge construction; drop-in alt |

### MD5  
- 128-bit digest; widespread **collision attacks**; no longer secure for signatures.

### RIPEMD  
- RIPEMD-160 still collision-free; Euro alternative to SHA.

### Comparison of Hash Function Value Lengths  
- Longer digest ⇒ **lower collision probability** (birthday bound ≈ 2^(n/2)).  
- Typical: MD5 128 < SHA-1 160 < SHA-256 256 < SHA-512 512.

---

## Digital Signatures  

### HMAC  
- **Keyed-hash MAC**; combines hash + secret key (e.g., HMAC-SHA-256).  
- Provides **integrity & authenticity**, not non-repudiation (symmetric).  

### Digital Signature Standard (DSS)  
- **FIPS 186-4**: DSA, RSA, ECDSA approved.  
- Process: hash → sign with sender’s private → verify with public.  
- Supports integrity, authentication, **non-repudiation**.

---

## Public Key Infrastructure  

### Certificates  
- Bind identity ↔ public key; follow **X.509 v3** format.  
- Fields: Subject, Issuer, Serial #, Validity, Key Usage, Extensions.

### Certificate Authorities (CAs)  
- **Root CA** (self-signed), **intermediate CAs**; trust anchored in root store.  
- Registration Authority (RA) verifies identity; CA issues & signs.

### Certificate Life Cycle  
1. **Enrollment** (CSR)  
2. Issue  
3. **Distribution**  
4. Usage  
5. **Renewal** / Rekey  
6. Revocation (CRL / OCSP)  
7. Expiration & archival/destruction.

### Certificate Formats  
- **PEM (.crt, .pem)** — Base64 + “-----BEGIN CERTIFICATE-----”.  
- **DER (.cer)** — binary ASN.1.  
- **PFX/P12** — cert + private key (password protected).  
- **CER** may be DER or PEM.

---

## Asymmetric Key Management  
- Store private keys in **HSM, TPM, smart card**; enforce split knowledge & backups.  
- Rotate per **NIST SP 800-57**; revoke on compromise or role change.  
- Support **key escrow** (recovery) vs **split custody** (dual control).

---

## Hybrid Cryptography  
- Combine strengths: **asymmetric** to exchange a random **symmetric session key**,  
  then bulk-encrypt with AES/ChaCha20.  
- Used in TLS, IPSec, PGP, S/MIME.

---

## Applied Cryptography  

### Portable Devices  
- **Full-device encryption** (AES-XTS), biometric unlock tied to hardware key (Secure Enclave, TrustZone).  

### Email  
- **S/MIME** (X.509), **PGP/OpenPGP** (web-of-trust).  
- Provides encrypt/sign; uses **MIME type application/pkcs7-mime**.

### Web Applications  
- **TLS 1.3**: ECDHE + AES-GCM/ChaCha20-Poly1305, forward secrecy, 0-RTT.  
- HSTS, HPKP (deprecated), certificate pinning defend against MITM.

### Steganography and Watermarking  
- Hide data inside carrier (LSB in images, audio).  
- Watermark = embed copyright mark; robust vs fragile variants.

### Networking  
- **IPSec** (IKEv2, ESP, AH), **SSH**, **WireGuard**.  
- VPN suites negotiate keys via **DH/ECDH**.

### Emerging Applications  
- **Blockchain/cryptocurrency** (ECDSA, secp256k1).  
- **Zero-knowledge proofs**, homomorphic encryption, **multisig**, **MPC**.

---

## Cryptographic Attacks  
| Attack | Target | Mitigation |
|--------|--------|------------|
| **Brute force** | Key space | Increase key length, rate-limit |
| **Cryptanalytic (mathematical)** | Algorithm weaknesses | Depricate DES/SHA-1 |
| **Birthday/collision** | Hash | Use SHA-256/SHA-3 |
| **Chosen-ciphertext (Bleichenbacher, padding oracle)** | RSA, CBC | OAEP, GCM |
| **Side-channel** (timing, power, EM) | Implementation | Constant-time code, shields |
| **Man-in-the-Middle** | Key exchange | Authenticated DHE, cert pinning |
| **Pass-the-Hash / Pass-the-Ticket** | Kerberos/NTLM | LSASS protection, SMB signing |

---

## Summary  
- **Asymmetric crypto** enables key exchange & signatures; know RSA, ECC, DH.  
- **Hash algorithms** ensure integrity; avoid MD5/SHA-1.  
- **Digital signatures + PKI** provide authentication & non-repudiation; grasp cert life cycle.  
- Real-world security uses **hybrid encryption** and demands solid **key management**.  
- Stay alert to **cryptographic attacks** and select modern, vetted algorithms & modes.  
Master these to ace CISSP questions on PKI trust paths, certificate revocation, signature verification, and secure protocol choices.

