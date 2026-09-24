# Cryptographic Solutions

## Objectives
- Understand common cryptographic concepts
- Explain encryption, hashing, digital signatures, certificates, and PKI
- Connect cryptography to confidentiality, integrity, authentication, and non-repudiation

## Table of Contents

1. [Cryptography](#cryptography)
2. [Encryption](#encryption)
3. [Symmetric and Asymmetric Encryption](#symmetric-and-asymmetric-encryption)
4. [Hashing](#hashing)
5. [Digital Signatures](#digital-signatures)
6. [Certificates and PKI](#certificates-and-pki)
7. [Common Cryptographic Use Cases](#common-cryptographic-use-cases)
8. [Key Management](#key-management)
9. [Cryptographic Attacks](#cryptographic-attacks)
10. [Password Hash Protection](#password-hash-protection)
11. [Key Takeaways](#key-takeaways)

## Cryptography

- **Cryptography:** Techniques used to protect information by transforming it or proving its authenticity and integrity.
- Cryptography supports confidentiality, integrity, authentication, and non-repudiation.

## Encryption

- **Encryption:** Converts readable data into unreadable form using a key.
- **Plaintext:** Original readable data.
- **Ciphertext:** Encrypted unreadable data.
- **Decryption:** Converts ciphertext back into plaintext using the correct key.

Example:
- A laptop drive is encrypted so data is protected if the laptop is stolen.

## Symmetric and Asymmetric Encryption

- **Symmetric Encryption:** Same key is used to encrypt and decrypt.
  - Faster and useful for large amounts of data.
  - Example: AES.

- **Asymmetric Encryption:** Uses a public key and private key pair.
  - Public key can be shared.
  - Private key must be protected.
  - Example: RSA, ECC.

## Hashing

- **Hashing:** Converts data into a fixed-length value.
- Hashing is one-way and is used to verify integrity.

Examples:
- Verify downloaded file integrity
- Store password hashes instead of plaintext passwords
- Compare evidence without changing original data

## Digital Signatures

- **Digital Signature:** Uses cryptography to prove authenticity, integrity, and non-repudiation.

Digital signatures help prove:
- Who signed the data
- Data was not changed
- Sender cannot easily deny signing

## Certificates and PKI

- **Certificate:** Digital document that binds an identity to a public key.
- **PKI:** Public Key Infrastructure; system for creating, managing, distributing, and revoking certificates.
- **CA:** Certificate Authority; trusted entity that issues certificates.

Certificates are used for:
- HTTPS websites
- VPN authentication
- Email encryption
- Device identity
- Code signing

## Common Cryptographic Use Cases

- TLS for secure web traffic
- VPN encryption
- Full-disk encryption
- File encryption
- Password hashing
- Digital signatures
- Secure email
- Certificate-based authentication

## Key Management

- Keys must be protected because weak key management can break strong encryption.

Good practices:
- Rotate keys
- Limit access to keys
- Store keys securely
- Revoke compromised certificates
- Separate duties for key management
- Use HSM or secure key vault when appropriate

## Cryptographic Attacks

| Attack | Meaning and Example |
| --- | --- |
| **Downgrade** | Tricks systems into using weaker protection. Examples include stripping an HTTP-to-HTTPS upgrade or forcing a fallback from a newer TLS version to an older protocol when fallback is allowed. An on-path attacker can try to manipulate the negotiation or initial unprotected request. |
| **Collision** | Finds two different inputs with the same hash. This can undermine systems that rely on collision resistance, such as some digital-signature workflows. |
| **Birthday Attack** | Uses the birthday effect to find a collision faster than exhaustive search over all possible digest values. An ideal n-bit hash offers roughly n/2 bits of collision security: about 2^(n/2) trials. |
| **Brute Force** | Tries candidate keys or passwords until one succeeds. Feasibility depends on effective key strength or password entropy, rate limits, and the cost of each guess; exhaustive search of a properly generated AES-256 key is impractical. |
| **Side-Channel** | Infers secrets from implementation behavior, such as execution time, power consumption, or electromagnetic or acoustic emissions, rather than directly breaking the algorithm. |

Collision resistance means collisions are computationally infeasible to find, not that they cannot exist. Finding any colliding pair differs from finding a second input matching a specified input's hash (a second-preimage attack) or recovering an input from a given hash (a preimage attack). A collision may undermine digital signatures or integrity checks that trust only the hash. Password guessing against a stored hash is generally a preimage-style guessing problem, so a collision attack alone does not reveal the password. See [NIST's hash-function definitions](https://csrc.nist.gov/projects/hash-functions).

Use supported secure protocols, reject insecure fallback, and enforce HTTPS with HSTS where appropriate; see the [IETF TLS recommendations](https://www.rfc-editor.org/rfc/rfc9325.html). MD5 is unsuitable where collision resistance is required. For passwords, use a dedicated password-hashing scheme instead of relying on collision resistance alone. Side-channel defenses include constant-time implementations where appropriate and hardened cryptographic hardware; stronger key sizes alone do not fix implementation leakage.

**Dragonblood** was a 2019 set of attacks against WPA3-Personal's Dragonfly/SAE handshake and WPA2/WPA3 transition mode. It included timing and cache side channels as well as downgrade attacks. Implementations received patches and standards work followed, but affected configurations differed and later research found additional leakage. See the [researchers' summary](https://wpa3.mathyvanhoef.com/).

## Password Hash Protection

- **Salt:** A unique random value for each password hash, stored with the hash. It defeats reuse of precomputed rainbow tables across accounts and prevents identical passwords from producing identical stored hashes when salts differ.
- **Pepper:** An additional secret used in password protection and stored separately from the password database, such as in a secrets vault. It is not inherently ephemeral and does not replace a salt.
- Use a dedicated password-hashing scheme with an appropriate work factor. A fast general-purpose hash alone makes offline guessing easier.
- Salts do not prevent attackers from guessing each password individually; computational cost and strong passwords still matter. See [OWASP's password-storage guidance](https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html).

## Key Takeaways

- Encryption protects confidentiality.
- Hashing verifies integrity.
- Digital signatures support integrity, authentication, and non-repudiation.
- Certificates and PKI help establish trust.
