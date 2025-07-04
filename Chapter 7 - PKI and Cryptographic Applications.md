# Chapter 7: PKI and Cryptographic Applications

- [Asymmetric Cryptography](#asymmetric-cryptography)
  - [Public and Private Keys](#public-and-private-keys)
  - [RSA](#rsa)
  - [ElGamal](#elgamal)
  - [Elliptic Curve Cryptography](#elliptic-curve-cryptography)
  - [Diffie-Hellman Key Exchange](#diffie-hellman-key-exchange)
  - [Quantum Cryptography](#quantum-cryptography)
- [Hash Functions](#hash-functions)
  - [SHA Family](#sha-family)
  - [MD5](#md5)
  - [RIPEMD](#ripemd)
  - [Comparison of Hash Function Value Lengths](#comparison-of-hash-function-value-lengths)
- [Digital Signatures](#digital-signatures)
  - [HMAC](#hmac)
  - [Digital Signature Standard](#digital-signature-standard)
- [Public Key Infrastructure](#public-key-infrastructure)
  - [Certificates](#certificates)
  - [Certificate Authorities](#certificate-authorities)
  - [Certificate Life Cycle](#certificate-life-cycle)
  - [Certificate Formats](#certificate-formats)
- [Asymmetric Key Management](#asymmetric-key-management)
- [Hybrid Cryptography](#hybrid-cryptography)
- [Applied Cryptography](#applied-cryptography)
  - [Portable Devices](#portable-devices)
  - [Email](#email)
  - [Web Applications](#web-applications)
  - [Steganography and Watermarking](#steganography-and-watermarking)
  - [Networking](#networking)
  - [Emerging Applications](#emerging-applications)
- [Cryptographic Attacks](#cryptographic-attacks)
- [Summary](#summary)

## Asymmetric Cryptography  

Modern information security hinges on **public-key (asymmetric) algorithms** to solve the key-distribution problem that plagues symmetric ciphers. In an asymmetric scheme every entity owns a **key pair**: one key to share 💡 (the *public* key) and one to guard 🔒 (the *private* key).

### Public and Private Keys  

| Property | Public Key | Private Key |
|----------|------------|-------------|
| Visibility | Freely distributed (certificates, key servers, QR codes) | Kept secret—often inside an HSM, TPM, or smart card |
| Main Uses | **Encrypt** for confidentiality, **verify** signatures | **Decrypt** incoming data, **sign** outgoing data |
| Security Concern | Authenticity (is it really Alice’s?) | Confidentiality (must never leak) |

*🧠 Exam cues:*  
* “Encrypt with recipient’s ***public*** key” → only recipient can decrypt.  
* “Sign with sender’s ***private*** key” → anyone can verify authenticity & non-repudiation with sender’s public key.

### RSA  

* **Security principle:** Hardness of factoring a large composite \(n = p \times q\).  
* **Key generation steps (simplified):**  
  1. Pick two random ~2048-bit primes \(p, q\).  
  2. Compute \(n = p \times q\) and \(\phi(n) = (p-1)(q-1)\).  
  3. Choose public exponent \(e\) where \(1 < e < \phi(n)\) and \(\gcd(e,\phi(n)) = 1\) (65537 is common).  
  4. Find private exponent \(d\) such that \(e \times d \equiv 1 \;(\mathrm{mod}\;\phi(n))\).  
* **Operations:**  
  * Encryption: \(C = P^{e} \bmod n\)  
  * Decryption / Signature generation: \(P = C^{d} \bmod n\)  
* **Strength guidelines (NIST SP 800-57):**  
  * 2048-bit RSA ≈ 112-bit symmetric strength (good to ~2030).  
  * 3072-bit RSA ≈ 128-bit symmetric strength (good beyond 2030).

**Pros:** Mature, widely supported (TLS, SSH, PGP, S/MIME).  
**Cons:** Slow, large keys/ciphertexts; vulnerable to **quantum** factoring (Shor).

### ElGamal  

* Extension of Diffie-Hellman math; relies on the **discrete logarithm problem (DLP)** in a finite field.  
* Generates two-part ciphertext → **doubles message size** ⚠️.

* **Advantages:** Free of historical RSA patents, provides semantic security, supports **forward secrecy** when used ephemerally.  
* **Use cases:** PGP (for key transport), cryptographic libraries where RSA licensing once mattered.

### Elliptic Curve Cryptography

* Security from the **Elliptic-Curve Discrete Logarithm Problem (ECDLP)**—believed harder than integer DLP or factoring.  
* **Tiny keys, same strength:**  
  | Symmetric Strength | RSA/DH Key | ECC Key |
  |--------------------|------------|---------|
  | 112-bit | 2048 bits | 224 bits |
  | 128-bit | 3072 bits | 256 bits |
* Common curves: **P-256** (`secp256r1`), **P-384**, **Curve25519**.  
* Major protocols: **ECDSA** (signatures), **ECDH/ECDHE** (key exchange).  
* Perfect for mobile/IoT due to low CPU & battery demand 🔋.

### Diffie-Hellman Key Exchange  

* Goal: agree on a shared symmetric key over an open channel without sending the key itself.  
* **Classic DH math:**  
  1. Public parameters: prime \(p\) and generator \(g\).  
  2. Alice picks secret \(a\); sends \(A = g^{a} \bmod p\).  
  3. Bob picks secret \(b\); sends \(B = g^{b} \bmod p\).  
  4. Both compute \(K = (other^{secret}) \bmod p\).  
* **Variants:**  
  * **DHE** (ephemeral) → forward secrecy.  
  * **ECDHE** → uses ECC for speed & shorter keys.  
* **Not** an encryption algorithm by itself—only a **key agreement** mechanism.

### Quantum Cryptography  

* **Quantum computing threat:** Shor’s algorithm could break RSA, DH, ECC in polynomial time ⏱️.  
* **Quantum Key Distribution (QKD):** Uses photon polarization; eavesdropping collapses quantum state → immediately detectable.  
* **Post-Quantum Cryptography (PQC):** Lattice-based (CRYSTALS-Kyber), hash-based (SPHINCS+), multivariate, code-based schemes under NIST standardization.  
* **CISSP takeaway:**  
  * Inventory and classify cryptographic assets.  
  * Plan for **crypto agility**—ability to swap algorithms/keys quickly.  
  * Long-term sensitive data (▶ 10 years) should already consider PQC readiness.

## Hash Functions  

A **hash function** transforms an input of arbitrary length into a fixed-length **message digest** that uniquely represents the data yet cannot be reversed (one-way). In practice digests are appended to messages or signed to prove **integrity** and **origin**.

### Why Hashes Matter
1. **Integrity check** – Receiver re-hashes the message; matching digests ⇒ message unchanged.  
2. **Digital signatures** – Instead of signing large data directly, a sender signs the compact digest.  

> **Size note:** Most modern digests are ≥ 128 bits—the longer the digest, the lower the collision risk.

### Five Requirements for a Cryptographic Hash (RSA Security)  
1. **Arbitrary-length input** handled.  
2. **Fixed-length output** produced.  
3. **Efficiency** – quick to compute.  
4. **One-way** – infeasible to derive the input from the hash.  
5. **Collision resistance** – infeasible to find two inputs with the same hash.

### SHA Family  

| Variant | Digest (bits) | Block (bits) | Status (2025) | Notes |
|---------|---------------|--------------|---------------|-------|
| **SHA-1** | 160 | 512 | ❌ Deprecated | Collisions (“SHAttered”, 2017). |
| **SHA-256** | 256 | 512 | ✅ Secure | SHA-2 family. |
| **SHA-224** | 224 | 512 | ✅ Secure | Truncated SHA-256. |
| **SHA-512** | 512 | 1024 | ✅ Secure | SHA-2 family. |
| **SHA-384** | 384 | 1024 | ✅ Secure | Truncated SHA-512. |
| **SHA-3** (224-512) | 224-512 | Sponge | ✅ Secure | Keccak algorithm; slower in software but drop-in replacement for SHA-2. |

*Memorize the digest sizes*—a frequent CISSP question.

### MD5  

* Evolved from **MD2** (1989) → **MD4** (1990) → **MD5** (1992).  
* Processes 512-bit blocks, four rounds, outputs **128-bit** digest.  
* **Broken:** Practical collisions (Lenstra, 2005) allow forged certificates.  
* Acceptable only for non-security uses (e.g., file deduplication), never for signatures or certs.

### RIPEMD  

| Variant | Digest | Security |
|---------|--------|----------|
| RIPEMD | 128 b | Insecure |
| RIPEMD-128 | 128 b | Insecure |
| **RIPEMD-160** | 160 b | ✅ Secure (Bitcoin, open source) |
| RIPEMD-256 | 256 b | Same security as 128 b (insecure) |
| RIPEMD-320 | 320 b | Same security as 160 b (secure) |

> 🤔 **Odd fact:** Lengthening the digest (RIPEMD-256) does **not** always increase security.

### Comparison of Hash Function Value Lengths  

| Hash Function | Digest Length (bits) |
|---------------|----------------------|
| HAVAL | 128 / 160 / 192 / 224 / 256 |
| **HMAC** | Variable (depends on underlying hash) |
| MD5 | 128 |
| SHA-1 | 160 |
| SHA2-224 / SHA3-224 | 224 |
| SHA2-256 / SHA3-256 | 256 |
| SHA2-384 / SHA3-384 | 384 |
| SHA2-512 / SHA3-512 | 512 |
| RIPEMD-128 | 128 |
| RIPEMD-160 | 160 |
| RIPEMD-256 | 256 (security ≈ 128) |
| RIPEMD-320 | 320 (security ≈ 160) |

### Quick CISSP Takeaways 📌  
* Choose **SHA-256** or stronger for new deployments.  
* MD5 and SHA-1 are **unsuitable** for certificates, signatures, and integrity assurance.  
* Understand digest sizes and which variants are deprecated.  
* Remember the five hash requirements and the dual role of digests in integrity checks and digital signatures.

## Digital Signatures  

Digital signatures glue **hashing** and **public-key cryptography** together to reach three CISSP-critical goals:  

| Crypto Goal | How the Digital Signature Achieves It |
|-------------|---------------------------------------|
| **Integrity** 🛡️ | Receiver re-hashes the message and compares to the signed digest. |
| **Authentication** 🔑 | Only the **sender’s private key** could have produced the signature, and everyone can verify it with the sender’s public key. |
| **Non-repudiation** 📜 | The sender cannot credibly deny creating a signature that only their private key could have generated. |

**Core workflow (Alice ➔ Bob):**  
1. Alice hashes the plaintext (e.g., SHA-512) → digest.  
2. Alice encrypts that digest with **her private key** → digital signature.  
3. She appends the signature to the plaintext (or encrypts the whole bundle with Bob’s public key for confidentiality).  
4. Bob decrypts the signature with **Alice’s public key**, hashes the received plaintext, and compares digests. Match ⇒ authentic, intact.

> ℹ️ **Key-selection cheat sheet**  
> * Encrypt confidential data? **Recipient’s public key**  
> * Decrypt confidential data sent to you? **Your private key**  
> * Sign data? **Your private key**  
> * Verify signature? **Sender’s public key**

### HMAC  

**H**ash-based **M**essage **A**uthentication **C**ode is a *symmetric* alternative that mixes any standard hash (MD5, SHA-2, SHA-3, etc.) with a **shared secret key**.

| Feature | HMAC | Full Digital Signature (RSA / ECDSA / EdDSA) |
|---------|------|----------------------------------------------|
| Integrity | ✅ | ✅ |
| Authentication | ✅ (to those who know the key) | ✅ |
| Non-repudiation | ❌ (shared key) | ✅ |
| Keys Used | One shared secret | Public / private pair |
| Performance | Very fast ⚡ | Slower (asymmetric math) |

*Use cases:* VPN tunnels, TLS record MACs, API tokens—where both parties already share a secret and do **not** need non-repudiation.

### Digital Signature Standard  

NIST **FIPS 186-5** (a.k.a. DSS) lists U.S.-approved signature algorithms **and mandates SHA-3** hash functions for new federal systems.

| Algorithm | Key Type | Strength Notes | Typical Key Size | Highlights |
|-----------|----------|----------------|------------------|------------|
| **RSA** (RFC 8017) | Integer factoring | Mature, widespread | ≥ 2048 bits | Simple validation, large keys |
| **ECDSA** (FIPS 186-5) | Elliptic curve | Equivalent strength with tiny keys | 256 bits (P-256) | Good for IoT / mobile |
| **EdDSA** (RFC 8032) | Edwards-curve | Deterministic, side-channel-resistant | Ed25519 / Ed448 | Very fast verification |

*Exam tips:*  
* DSS does **not** approve DSA with SHA-1 anymore—SHA-3 only.  
* ECDSA & EdDSA inherently support non-repudiation.  
* When speed and small keys matter, expect a test answer pointing to **ECDSA** or **EdDSA** over RSA.

## Public Key Infrastructure  

A **PKI** is a hierarchy of trust that links verified identities to public keys via **digital certificates**.  
Result: strangers can bootstrap secure (hybrid) communication by trusting the certificate chain instead of pre-sharing secrets.

### Certificates  

* **Standard:** ITU-T **X.509**.  
* **Key fields (memorize!):** Version, **Serial Number**, Signature Algorithm, **Issuer**, **Validity**, **Subject**, **Subject Public Key Info**, Extensions.  
* **Wildcard** certs (`*.example.org`) cover one sub-domain level only.  
* Use cases: server TLS, e-mail, code signing, device authentication.  

| Certificate Type | Identity Vetting | Typical Use | Example |
|------------------|------------------|-------------|---------|
| **Domain Validation (DV)** | Proves control of domain | Basic HTTPS | letsencrypt.org |
| **Organization Validation (OV)** | Confirms legal entity | Enterprise apps | digicert.com |
| **Extended Validation (EV)** | Rigorous legal + operational checks | High-trust sites (banking) | green bar (legacy) |

### Certificate Authorities  

* **Root CA** (offline) → **Intermediate CAs** (online) → **End-entity certs**. This chaining lets the root’s private key stay powered-off 💡.  
* **Registration Authority (RA):** performs identity checks on behalf of a CA.  
* Trust model: browsers ship with a root store; anything signed down that chain is implicitly trusted.  
* Organizations may run an **internal CA** for intranet certificates (= self-signed root trusted only inside).  

> **Risk note:** A single sloppy CA can poison the trust chain (e.g., Symantec 2017 ➔ sold to DigiCert).

### Certificate Life Cycle  

| Phase | Key Activities | CISSP Focus |
|-------|----------------|-------------|
| **Enrollment** | Prove identity ➔ submit **CSR** ➔ CA issues & signs cert | DV vs EV requirements |
| **Operation / Use** | Install cert; peers validate chain and check revocation | PIN certs (HPKP deprecated) |
| **Renewal** | Obtain new cert before expiry; may reuse keys or generate fresh | Plan automation |
| **Revocation** | CA marks cert invalid before expiry (compromise, name change, etc.) | CRL, OCSP, stapling |
| **Expiration & Destruction** | Cert naturally expires; keys securely destroyed or archived | Enforce key-destruction policy |

#### Revocation Mechanisms  

| Method | How It Works | Latency | Load | Notes |
|--------|--------------|---------|------|-------|
| **CRL** | Client downloads CA-signed list of revoked serial #s | High (list refresh) | Low CA load | Periodic polling |
| **OCSP** | Client queries CA’s OCSP responder for real-time status | Low | High CA load | Response: good / revoked / unknown |
| **OCSP Stapling** | Server caches signed OCSP response ⏲️ (e.g., 24 h) and “staples” it to TLS handshake | Very low | Minimal CA load | Modern TLS default |

### Certificate Formats  

| Format | Encoding | File Ext. | Contains | Typical Platform |
|--------|----------|-----------|----------|------------------|
| **DER** | Binary ASN.1 | `.der`, `.crt`, `.cer` | Single cert | Java, appliances |
| **PEM** | Base64 (ASCII) | `.pem`, `.crt` | Cert, chain, or key | Unix/Linux, OpenSSL |
| **PFX / PKCS #12** | Binary container (password-protected) | `.pfx`, `.p12` | Cert **+** private key | Windows import/export |
| **P7B / PKCS #7** | Base64 (ASCII) | `.p7b` | Cert or chain (no private key) | Windows/IIS |

*Remember:* `.crt` may be PEM **or** DER—inspect the file (BEGIN/END == PEM). 🔍

## Asymmetric Key Management  

Good crypto is more than math—it’s also **key hygiene**. Follow these best-practice pillars:

| Control | Why It Matters | CISSP Pointers |
|---------|----------------|----------------|
| **Algorithm choice** | Public, peer-reviewed algorithms only (RSA, ECDSA, EdDSA). “Black-box” ≡ 🚩. | Security through obscurity ≠ security. |
| **Key length & randomness** | Longer keys ↔ stronger, but slower. Use FIPS / NIST tables; derive keys from **true random** or NIST-approved DRBG. | Avoid pattern bias that aids attacks. |
| **Private-key secrecy** | Exposure ➔ irreversible compromise & impersonation. | Store in HSMs, TPMs, smart cards; never share. |
| **Rotation / retirement** | Limits window of undetected compromise. | Enforce policy (e.g., 1–3 yrs) ⏳. |
| **Backup / escrow** | Loss of key = loss of access. | Split knowledge + dual control; encrypt escrow storage. |
| **Hardware Security Module (HSM)** | Tamper-resistant chip that generates, stores, and uses keys without revealing them. | Adds hardware acceleration & audit logs. |

## Hybrid Cryptography  

Combine the **speed** of symmetric with the **scalable key exchange** of asymmetric.

1. Parties negotiate a public-key method (e.g., ECDHE).  
2. They use it once to agree on a random **ephemeral symmetric key**.  
3. All bulk data travels under fast symmetric encryption (AES, ChaCha20).  
4. Session ends → key discarded 🗑️ (perfect forward secrecy).

**TLS 1.3** is the textbook example.

| Step | Handshake Action (simplified) |
|------|-------------------------------|
| 1️⃣ | ClientHello → lists supported cipher suites |
| 2️⃣ | ServerHello + cert → selects suite, sends public key |
| 3️⃣ | Both compute shared secret via ECDHE |
| 4️⃣ | Derive session keys; switch to symmetric encryption |

## Applied Cryptography  

### Portable Devices 📱  

* **Full-Disk / File Encryption:** BitLocker, FileVault, VeraCrypt.  
* **TPM chip** guards keys & ties them to boot measurements.  
* Mobile OSs (iOS, Android) provide hardware-backed AES-XTS or ChaCha20; mandate passcode/PIN to unlock keys.  
* Evaluate: key protection in RAM, FDE vs FBE, remote wipe support.

### Email ✉️  

| Need | Technique | Tool / Standard |
|------|-----------|-----------------|
| Confidentiality | Encrypt message | PGP, S/MIME |
| Integrity & Authn | Hash + Sign | PGP sig, S/MIME |
| Non-repudiation | Digital signature | PGP, S/MIME |
| All of the above | Encrypt **and** sign | PGP (OpenPGP) or S/MIME |

* **PGP / OpenPGP** – web-of-trust, hybrid encryption.  
* **S/MIME** – X.509 PKI, RSA/ECDH keys, built into Outlook, Apple Mail, Gmail Enterprise+.  
* Sender chooses: encrypt, sign, or both (cost vs need).

### Web Applications 🌐  

* **Transport Layer Security (TLS)** replaced SSL.  
* **Secure versions:** 1.2 (minimum) & 1.3 (preferred).  
* TLS 1.3 defaults: ECDHE for key exchange, AES-GCM or ChaCha20-Poly1305 bulk ciphers, SHA-256/384 for MAC.  
* **POODLE** & other attacks killed SSL 3.0 fallback.  
* **Cipher suite notation:** `TLS_AES_256_GCM_SHA384` (bulk cipher + MAC).  
* **Certificate pinning / HSTS** defend against rogue CAs & downgrade.

### Steganography and Watermarking 🖼️  

| Concept | How It Works | Use Cases | Risks |
|---------|--------------|-----------|-------|
| **Steganography** | Hide data in LSBs of images/audio/video or within text (concealment cipher). | Covert channels, espionage. | Hard to detect visually; tools exist to scan. |
| **Watermarking** | Embed owner/serial info invisibly. | IP protection, leak tracing. | Must survive format changes. |

### Networking 🔒  

#### Link vs End-to-End Encryption  

| Feature | **Link Encryption** | **End-to-End Encryption** |
|---------|--------------------|---------------------------|
| OSI Layer | 1–2 | 4–7 |
| Encrypts headers? | Yes → every hop decrypts/re-encrypts | No (payload only) |
| Example | IPSec **tunnel** mode | TLS, SSH |

#### Protocol Highlights  

* **SSH-2** – Diffie-Hellman / Ed25519 keys, SFTP, channel multiplexing.  
* **IPSec**  
  * Components: **AH** (integrity, auth) + **ESP** (confidentiality, integrity).  
  * Modes: **Transport** (payload only) vs **Tunnel** (entire packet).  
  * **Security Association (SA)** = one-way channel; two SAs per duplex connection.

### Emerging Applications 🚀  

| Area | Crypto Role | Key Points |
|------|-------------|------------|
| **Blockchain** | Distributed, immutable ledger | ECDSA/EdDSA signatures, PoW/PoS consensus. |
| **Lightweight Crypto** | Power-constrained or low-latency devices | Custom ASICs/FPGAs, NIST “LW-C” project (e.g., Ascon). |
| **Homomorphic Encryption** | Compute on ciphertexts without decrypting | Enables privacy-preserving analytics; still CPU-heavy. |

## Cryptographic Attacks  

Below are the attack patterns CISSP expects you to recognize, the weak point they exploit, and the classic counter-measure.

| Attack Type | Target / Principle | Exam-Ready Countermeasure |
|-------------|-------------------|---------------------------|
| **Brute force** | Tries every key 🙈 | Use long, random keys; lockout/delay mechanisms |
| **Rainbow table** | Pre-computed hash lists | Salt + key-stretch (PBKDF2, bcrypt, scrypt) |
| **Analytic** | Algebraic shortcut of algorithm | Peer-reviewed, publicly vetted ciphers |
| **Implementation** | Bugs / poor coding (not math) | Secure coding, patching, formal verification |
| **Statistical** | Poor RNG or bias | Use NIST-approved CSPRNG |
| **Fault injection** | Voltage, temp, laser fault to leak keys | Tamper-resistant HSMs, sensors, self-wipe |
| **Side-channel** | Power, EM, timing leakage | Constant-time code, shielding, noise injection |
| **Timing** | Measures op duration (variant of side-channel) | Equalize code paths, blinding in RSA/ECDSA |
| **Frequency analysis** (ciphertext-only) | Letter distribution in simple ciphers | Use modern polyalphabetic / block ciphers |
| **Known plaintext** | Have P + C pair | Use strong ciphers (AES, ChaCha20) |
| **Chosen plaintext** | Attacker feeds chosen P | Resistant designs (AES, modern block modes) |
| **Chosen ciphertext** | Oracle decrypts attacker’s C | Padding-proof modes (OAEP, GCM) |
| **Meet-in-the-middle** | Two-round encryption (e.g., 2DES) | Use ≥3 rounds (3DES, AES) |
| **Man-in-the-middle (MITM)** | Spoofs handshake, uses 2 keys | Mutual auth, certificates, pinning |
| **Birthday / collision** | Dual input with same hash | Long hash (≥ 256 b), collision-resistant algos |
| **Replay** | Re-sends captured packet | Timestamps, nonces, one-time tokens |

🔥 **Key concept:** every extra key bit doubles brute-force time; secure design = algorithm strength × flawless implementation × sound key management.

## Summary  

* **Asymmetric cryptography** enables scalable, trustable communication between strangers using public/private key pairs and PKI-issued certificates.  
* **Digital signatures** merge hashing + asymmetric encryption to supply integrity, authentication, and non-repudiation.  
* **Key management** best practices (strong algorithms, secret private keys, rotation, HSMs) keep crypto durable over time.  
* **Hybrid cryptography** (e.g., TLS 1.3) marries asymmetric key exchange with fast symmetric bulk encryption for real-world performance.  
* **Applied crypto** secures data at rest (BitLocker, FileVault), email (PGP, S/MIME), web (TLS), networks (IPSec, SSH), and newer arenas like blockchain, lightweight IoT, and homomorphic analytics.  
* **Attack landscape** spans brute-force, analytic, implementation, side-channel, MITM, replay, and collision methods—defense requires sound algorithms, sufficient key sizes, hardened implementations, and vigilant operational controls.

Master these principles and you’ll spot weak crypto — and pick the right fix — on the CISSP exam and in the field. 🚀
