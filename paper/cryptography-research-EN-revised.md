# The Role of Cryptography in Information Security and a Comparative Study of Cryptographic Algorithms

**Author:** Habibullah Haqdost  
**Supervisor:** Dr. Gelareh Veisi  
**Institution:** Islamic Azad University, Mashhad · B.Sc. in Computer Engineering (Software)  
**Date:** Winter 2026 (1404 SH)

> Revised English edition of the original Persian undergraduate research project. It updates the original with current standards (3DES deprecation, TLS 1.3 key exchange, post-quantum cryptography), adds measured performance results (Section 4.4) and completes the references. All changes are listed in Appendix A.

---

## Abstract

In today's world, the rapid expansion of information technology and the growing dependence of organizations and individuals on computer systems have made information security one of society's foremost concerns. Vast amounts of sensitive information, including financial data, personal records, government documents and confidential communications, are now stored and transmitted digitally. Within this landscape, cryptography plays a central role in protecting data as one of the most fundamental tools for achieving information security.

This study examines the role of cryptography in information security and compares widely used cryptographic algorithms from several perspectives. It first sets out the basic concepts of information security and cryptography, then introduces and analyzes symmetric and asymmetric algorithms. These algorithms are then compared in terms of speed, security, key length and typical applications, supported by performance measurements taken with the Web Crypto API in a web browser, and the most suitable options for different use cases are recommended. The study closes with an outlook on post-quantum cryptography.

**Keywords:** cryptography, information security, symmetric encryption, asymmetric encryption, DES, AES, RSA, ECC

---

## Table of Contents

1. Chapter 1: Introduction
2. Chapter 2: Theoretical Background and Information Security Concepts
3. Chapter 3: Cryptographic Algorithms
4. Chapter 4: Comparison of Cryptographic Algorithms
5. Chapter 5: Conclusions and Recommendations
6. References
7. Appendix A: Revisions to the Original

---

## Chapter 1: Introduction

### 1.1 Background

With advances in communication technologies and the growth of computer networks, digital information exchange has become an inseparable part of human life. Everything from everyday communication to banking transactions and critical systems depends on information security. Without appropriate security mechanisms, this information is exposed to threats such as eavesdropping, tampering, forgery and theft.

Cryptography is one of the most important tools for countering these threats: by transforming intelligible data into unintelligible data, it prevents information from being disclosed. The correct use of cryptographic algorithms plays a key role in guaranteeing the security of information systems.

### 1.2 Problem Statement

Despite the wide variety of cryptographic algorithms available, choosing the right algorithm for a specific application has always been challenging. Each algorithm has its own strengths and weaknesses in terms of speed, level of security and implementation complexity. An inadequate understanding of these algorithms can lead to poor choices and weaker system security. Examining and comparing cryptographic algorithms in order to make an optimal choice is therefore essential.

### 1.3 Research Objectives

The main objectives of this study are to:

- Examine the role of cryptography in ensuring information security
- Introduce the fundamental concepts of cryptography
- Classify cryptographic algorithms
- Compare symmetric and asymmetric algorithms
- Analyze the suitability of each algorithm for different systems

### 1.4 Structure of the Study

This study consists of five chapters. Chapter 1 has presented the general framework of the research. Chapter 2 covers the theoretical background and core concepts of information security. Chapter 3 introduces cryptographic algorithms. Chapter 4 is devoted to comparing and analyzing these algorithms, and Chapter 5 presents conclusions and recommendations.

---

## Chapter 2: Theoretical Background and Information Security Concepts

### 2.1 Information Security

Information security refers to the set of methods and policies used to protect information against various threats. Its main goal is to preserve the value of information and prevent unauthorized access to it.

### 2.2 Core Principles of Information Security

Information security rests on three core principles, commonly known as the CIA triad:

#### 2.2.1 Confidentiality

Confidentiality means preventing unauthorized individuals from accessing information. Cryptography plays the primary role in achieving this principle.

#### 2.2.2 Integrity

Integrity ensures that data remains unaltered during transmission or storage.

#### 2.2.3 Availability

Information must be accessible to authorized users whenever it is needed.

*Figure 2.1: The CIA triad (Confidentiality, Integrity, Availability) as the foundation of information security.*

### 2.3 The Concept of Cryptography

Cryptography is one of the most fundamental concepts in information security and computer science. Its main purpose is to protect information against unauthorized access, disclosure, modification or misuse. In its simplest definition, cryptography is a process in which intelligible information (plaintext) is transformed, using mathematical methods and well-defined algorithms, into unintelligible information (ciphertext), so that only authorized parties can recover and understand the original content.

Cryptography is not merely a technical tool; it is a scientific and mathematical framework that lies at the heart of many modern security systems, from internet communications and electronic banking to government and military systems and critical infrastructure.

---

## Chapter 3: Cryptographic Algorithms

### 3.1 Symmetric Cryptography

Symmetric cryptography is one of the oldest and, at the same time, most widely used methods in information security. In this type of cryptography, the sender and the receiver use a single, shared key for both encryption and decryption. In other words, the same key used to transform plaintext into ciphertext is also used to restore the ciphertext to its original form.

*Figure 3.1: Symmetric encryption workflow.*

```mermaid
flowchart LR
    A[Receive plaintext] --> B[Receive secret key] --> C[Run encryption algorithm] --> D[Produce ciphertext]
    D --> E[Send ciphertext over insecure channel] --> F[Receiver obtains ciphertext]
    F --> G[Receiver obtains shared key] --> H[Run decryption algorithm] --> I[Recover plaintext]
```

#### 3.1.1 Key Characteristics of Symmetric Cryptography

One of the most important characteristics of symmetric cryptography is its high processing speed. Because their structure is simpler and they require less computation than asymmetric algorithms, symmetric algorithms can encrypt and decrypt large volumes of data in a short time. For this reason, symmetric cryptography is commonly used to protect large data sets such as files, databases, storage disks and real-time communications.

On the other hand, symmetric cryptography faces a fundamental key-management challenge. Since the sender and receiver must exchange the shared key securely before communication begins, key distribution becomes a complex problem in large networks or insecure environments. If an attacker intercepts the key, the security of the entire system is compromised.

#### 3.1.2 Advantages of Symmetric Cryptography

- Very high encryption and decryption speed
- Lower consumption of processing resources
- Well suited to encrypting large volumes of data
- Simpler to implement than asymmetric methods

#### 3.1.3 Disadvantages of Symmetric Cryptography

- Fundamental difficulty in distributing keys securely
- Poor scalability in large networks
- Keys must be replaced if they are disclosed
- No direct support for digital signatures or non-repudiation

#### 3.1.4 The DES Algorithm

The Data Encryption Standard (DES) is one of the first standardized symmetric encryption algorithms and played an important role in shaping the field of information security. It was designed by IBM in the 1970s and adopted in 1977 by the U.S. National Bureau of Standards (NBS, now the National Institute of Standards and Technology, NIST) as the official standard for data encryption. The main goal behind DES was to provide a reliable encryption method for widespread use in organizations and government systems.

**1. Structure and operation**

DES is a block cipher that processes data in 64-bit blocks. Its input key is 64 bits long, of which only 56 bits are used as the effective key; the remaining 8 bits are used for parity checking. This key length was considered adequate when the algorithm was designed, but as computing power grew it became one of the main weaknesses of DES.

DES is built on a Feistel network and consists of 16 rounds. In each round, operations such as permutation, substitution and combination with round subkeys are performed. This design ensures that a small change in the plaintext or the key produces a substantial change in the ciphertext, a property known as the avalanche effect.

**2. Security and weaknesses**

When it was introduced, DES offered an adequate level of security. Today, however, its short key length makes it highly vulnerable to brute-force attacks. With modern hardware, a DES key can be broken in a very short time. For this reason, DES is not recommended for modern security systems and is used only for educational purposes or in legacy systems.

**3. Applications and current status**

DES is now considered obsolete and has been replaced by more secure algorithms such as AES. Nevertheless, studying DES remains valuable for teaching, because many fundamental concepts of block ciphers and the Feistel structure can be clearly observed in it.

**4. Pseudocode**

```text
Algorithm DES_Encryption
Input : Plaintext (64-bit), Key (64-bit)
Output: Ciphertext (64-bit)

Begin
    // Step 1: Key preparation
    Remove parity bits from Key
    Generate 16 subkeys (K1 to K16)

    // Step 2: Initial permutation
    Apply Initial Permutation (IP) on Plaintext
    Split result into L0 and R0 (32-bit each)

    // Step 3: 16 Feistel rounds
    For i = 1 to 16 do
        Li = Ri-1
        Ri = Li-1 XOR F(Ri-1, Ki)
    End For

    // Step 4: Combination and final permutation
    Combine R16 and L16
    Apply Final Permutation (IP⁻¹)

    Ciphertext = result
End
```

#### 3.1.5 The AES Algorithm

The Advanced Encryption Standard (AES), the successor to DES, is one of the most secure and widely used symmetric encryption algorithms in the world. Following an extensive international competition, it was announced by NIST in 2001 as the Advanced Encryption Standard. AES was designed by two Belgian cryptographers, Joan Daemen and Vincent Rijmen, and was originally known as Rijndael.

**1. Structure and technical characteristics**

AES is a block cipher that processes data in 128-bit blocks. It supports key lengths of 128, 192 and 256 bits, with 10, 12 and 14 rounds respectively. A larger number of rounds significantly increases the security margin of the algorithm.

Unlike DES, AES does not use a Feistel structure; it is based on a substitution–permutation network (SPN). Each round consists of the following operations:

- **SubBytes:** byte substitution
- **ShiftRows:** row shifting
- **MixColumns:** column mixing
- **AddRoundKey:** adding the round key

These operations are designed to provide a very high level of security while maintaining high speed.

**2. Security and advantages**

AES is resistant to all known classes of cryptographic attack, including brute-force, differential and linear attacks. To date, no practical attack capable of breaking full AES has been reported. In addition, thanks to its simple and efficient structure, AES performs well in both software and hardware, and runs efficiently even on resource-constrained devices.

**3. Applications**

AES is now the primary encryption standard in many security systems and protocols, including:

- Disk and file encryption
- Network communication security
- Banking and financial systems
- Modern security protocols such as TLS 1.3

AES is always used together with a mode of operation. Authenticated modes such as AES-GCM are recommended, because they protect both confidentiality and integrity. The simple ECB mode should not be used, since identical plaintext blocks produce identical ciphertext blocks and reveal patterns in the data.

**4. Pseudocode**

```text
Algorithm AES_Encryption
Input : Plaintext (128-bit), Key (128/192/256-bit)
Output: Ciphertext (128-bit)

Begin
    // Step 1: Key expansion
    Generate round keys using Key Expansion

    // Step 2: Initial round
    State = Plaintext
    State = State XOR RoundKey[0]

    // Step 3: Main rounds
    For round = 1 to Nr - 1 do
        State = SubBytes(State)
        State = ShiftRows(State)
        State = MixColumns(State)
        State = State XOR RoundKey[round]
    End For

    // Step 4: Final round (no MixColumns)
    State = SubBytes(State)
    State = ShiftRows(State)
    State = State XOR RoundKey[Nr]

    Ciphertext = State
End
```

#### 3.1.6 DES and AES: Comparative Summary

Overall, AES is markedly superior to DES in security, speed and scalability. While DES today has only historical and educational value, AES is recognized as the backbone of symmetric encryption in modern systems.

### 3.2 Asymmetric Cryptography

Asymmetric cryptography is one of the most important achievements of modern cryptography, developed to solve the fundamental key-distribution problem of symmetric cryptography. Unlike symmetric cryptography, which relies on a single shared key, this approach uses two distinct but mathematically related keys: a public key and a private key. The two keys are designed so that knowing one of them makes computing the other practically impossible or extremely difficult.

In an asymmetric cryptosystem, each user generates a key pair. The public key is shared freely with others, while the private key must remain strictly confidential. When a sender wants to send a secure message, they encrypt it with the recipient's public key. Only the recipient, who holds the corresponding private key, can then decrypt the message.

This property means that message security is preserved even over insecure communication channels, because disclosing the public key poses no risk to the confidentiality of the information.

*Figure 3.2: Asymmetric encryption workflow.*

```mermaid
flowchart LR
    A[Generate key pair: public + private] --> B[Keep private key secret] --> C[Publish public key] --> D[Sender receives plaintext] --> E[Encrypt with recipient's public key]
    E --> F[Produce ciphertext] --> G[Send ciphertext] --> H[Recipient receives ciphertext] --> I[Decrypt with private key] --> J[Recover plaintext]
```

#### 3.2.1 Advantages of Asymmetric Cryptography

- No need for a secure channel to exchange keys
- Enables secure communication between parties who have never met
- Supports digital signatures and non-repudiation
- Increases trust in distributed systems

#### 3.2.2 Disadvantages and Limitations

Despite its many advantages, asymmetric cryptography also has limitations:

- Slower than symmetric cryptography
- Higher consumption of processing resources
- Unsuitable for encrypting large volumes of data
- Greater implementation complexity

For this reason, in practice it is rarely used to encrypt large volumes of data directly.

#### 3.2.3 The RSA Algorithm

RSA is one of the oldest, best-known and most widely used asymmetric algorithms, and it has played a major role in the development of information security and secure communications. It was introduced in 1977 by three researchers, Ron Rivest, Adi Shamir and Leonard Adleman, and takes its name from their initials.

**1. Core idea and mathematical basis**

The security of RSA rests on the problem of factoring very large numbers into their prime factors. Two very large prime numbers are chosen, and their product is used as part of the public key. While multiplying two primes is simple, factoring the result back into its prime factors is computationally very hard and time-consuming, especially when the numbers are very large.

As a result, even if an attacker has access to the public key, they are practically unable to decrypt the message without knowing the private key.

RSA key generation consists of the following steps:

1. Choose two large, random prime numbers
2. Compute their product as the modulus
3. Compute Euler's totient function
4. Choose a suitable public exponent
5. Compute the private exponent so that the required mathematical relation holds

This process ensures that the public and private keys are mathematically linked, yet computationally infeasible to derive from one another.

```text
Algorithm RSA_Key_Generation()
    p, q                      // choose two large random primes
    n = p × q                 // compute the modulus
    φ(n) = (p − 1) × (q − 1)  // compute Euler's totient
    choose e such that
        1 < e < φ(n)
        gcd(e, φ(n)) = 1
    compute d such that
        d × e ≡ 1 (mod φ(n))
    Public key  = (e, n)
    Private key = (d, n)
End Algorithm
```

**2. Advantages and limitations of RSA**

Advantages:

- Relatively simple to implement
- Broad support in software and security protocols
- Well suited to key exchange and digital signatures

Limitations:

- Slow encryption and decryption
- Requires very large keys
- Unsuitable for resource-constrained devices

For this reason, RSA is usually not used to encrypt large amounts of data directly; it is mainly used for key exchange and digital signatures.

#### 3.2.4 The ECC Algorithm

Elliptic Curve Cryptography (ECC) is one of the most advanced and efficient asymmetric methods, based on the mathematics of elliptic curves. It was introduced in the 1980s and is now regarded as one of the most secure and efficient cryptographic approaches, especially in modern systems and resource-constrained devices.

**1. Mathematical basis**

The security of ECC relies on the elliptic curve discrete logarithm problem. This problem is such that solving it is practically impossible, or prohibitively expensive, even with very large computing power. In ECC, the mathematical operations are performed on points of a specific curve over a finite field.

**2. Structural difference between ECC and RSA**

Whereas RSA relies on very large integers, ECC uses the structure of elliptic curves to provide the same level of security with much shorter keys. For example, a 256-bit ECC key offers roughly the same security as a 3072-bit RSA key.

**3. Advantages and disadvantages of ECC**

Advantages:

- High efficiency
- Lower energy consumption
- Shorter keys and simpler key management
- Strong resistance to known attacks

Disadvantages:

- Difficult to implement correctly
- Highly sensitive to programming errors

---

## Chapter 4: Comparison of Cryptographic Algorithms

### 4.1 Comparison of Symmetric Algorithms

| Algorithm | Key length | Speed | Security |
|---|---|---|---|
| DES | 56 bits | High | Weak |
| 3DES | 168 bits (112-bit effective security) | Low | Medium; deprecated |
| AES | 128 / 192 / 256 bits | Very high | Very strong |

Triple DES (3DES) applies DES three times to extend its key length. Because of meet-in-the-middle attacks its effective security is about 112 bits, and its small 64-bit block makes it vulnerable to attacks on long sessions. NIST disallowed 3DES for encryption after 2023 (NIST SP 800-131A Rev. 2), so it should appear only in legacy systems.

### 4.2 Comparison of Asymmetric Algorithms

| Algorithm | Key length | Speed | Security |
|---|---|---|---|
| RSA | 2048 bits (≈112-bit security) | Low | High |
| ECC | 256 bits (≈128-bit security) | High | Very high |

Equivalent security levels follow NIST SP 800-57 Part 1: a 256-bit ECC key provides about the same security as a 3072-bit RSA key.

### 4.3 Overall Comparison

| Feature | Symmetric | Asymmetric |
|---|---|---|
| Speed | High | Low |
| Key management | Difficult | Easier |
| Typical use | Bulk data encryption | Key exchange, authentication, digital signatures |

### 4.4 Measured Performance

To complement the qualitative comparison above, the algorithms were benchmarked with the Web Crypto API, the cryptography interface built into modern web browsers. Each operation was repeated and averaged. The companion demo (`demo/index.html`) lets readers reproduce the measurements on their own devices.

*Table 4.4: Sample results (Chromium 141, Linux x86-64 cloud machine; values vary by device).*

| Operation | Algorithm | Average time | Rate |
|---|---|---|---|
| Encrypt 8 MB of data | AES-256-GCM | 112 ms | 72 MB/s |
| Decrypt 8 MB of data | AES-256-GCM | 101 ms | 79 MB/s |
| Generate key pair | RSA-2048 | 128 ms | 7.8 ops/s |
| Generate key pair | RSA-3072 | 171 ms | 5.9 ops/s |
| Generate key pair | ECC P-256 | 0.055 ms | 18,182 ops/s |
| Encrypt a 32-byte key | RSA-2048 (OAEP) | 0.032 ms | 31,250 ops/s |
| Decrypt a 32-byte key | RSA-2048 (OAEP) | 0.650 ms | 1,538 ops/s |
| Key agreement | ECDH P-256 | 0.094 ms | 10,638 ops/s |
| Sign | RSA-2048 (PSS) | 1.135 ms | 881 ops/s |
| Verify | RSA-2048 (PSS) | 0.048 ms | 20,833 ops/s |
| Sign | ECDSA P-256 | 0.110 ms | 9,091 ops/s |
| Verify | ECDSA P-256 | 0.156 ms | 6,410 ops/s |

The measurements support the main findings and refine them in three ways:

1. **Symmetric encryption is built for bulk data.** AES-GCM is measured in megabytes per second, whereas asymmetric operations are measured per operation on inputs of a few dozen bytes. This confirms why asymmetric algorithms are not used to encrypt large data directly.
2. **RSA is asymmetric in speed as well.** Its public-key operations (encryption and signature verification) are very fast because the public exponent is small, while its private-key operations (decryption and signing) are roughly 20 times slower. The general statement "RSA is slow" applies mainly to private-key operations and key generation.
3. **ECC's advantage is largest in key generation and signing.** Generating an ECC P-256 key pair was over 2,000 times faster than generating an RSA-2048 key pair, and ECDSA signing was about 10 times faster than RSA-PSS signing, while ECC also offers a higher security level. This is why modern protocols generate fresh ECC keys for every connection.

---

## Chapter 5: Conclusions and Recommendations

### 5.1 Conclusions

The findings of this study show that cryptography plays a fundamental role in information security. No single algorithm meets every security requirement on its own; combining symmetric and asymmetric algorithms, known as hybrid encryption, is the best approach for modern systems. TLS 1.3, which secures most web traffic today, follows exactly this pattern: an ephemeral elliptic-curve key exchange (ECDHE) establishes a shared secret, and AES-GCM or ChaCha20-Poly1305 encrypts the data. The measurements in Section 4.4 confirm the reasoning behind this design.

### 5.2 Recommendations

- Use AES in an authenticated mode (AES-GCM) to encrypt large volumes of data; avoid ECB mode
- Use elliptic-curve key exchange (ECDHE) for establishing session keys; RSA key transport has been removed from TLS 1.3
- Use ECDSA, EdDSA or RSA (with keys of at least 2048 bits) for digital signatures
- Do not use DES or 3DES in new systems
- Rotate keys regularly and follow current NIST guidance on key lengths
- Use well-tested cryptographic libraries rather than implementing algorithms from scratch, particularly for ECC, which is sensitive to implementation errors

### 5.3 Future Outlook: Post-Quantum Cryptography

A sufficiently powerful quantum computer running Shor's algorithm could solve both integer factorization and the elliptic-curve discrete logarithm problem efficiently, which would break RSA and ECC. Symmetric algorithms are far less affected: Grover's algorithm only halves their effective key length, so AES-256 remains secure. In August 2024 NIST published its first post-quantum standards: ML-KEM (FIPS 203) for key establishment and ML-DSA (FIPS 204) and SLH-DSA (FIPS 205) for digital signatures. Hybrid key exchanges that combine classical ECDHE with ML-KEM are already being deployed in web browsers. Future work should extend this comparison to these post-quantum algorithms.

---

## References

**English sources**

1. Stallings, W. (2020). *Cryptography and Network Security: Principles and Practice* (8th ed.). Pearson.
2. Schneier, B. (1996). *Applied Cryptography: Protocols, Algorithms, and Source Code in C* (2nd ed.). Wiley.
3. Menezes, A. J., van Oorschot, P. C., & Vanstone, S. A. (1996). *Handbook of Applied Cryptography.* CRC Press.
4. Rivest, R. L., Shamir, A., & Adleman, L. (1978). A method for obtaining digital signatures and public-key cryptosystems. *Communications of the ACM, 21*(2), 120–126.
5. Koblitz, N. (1987). Elliptic curve cryptosystems. *Mathematics of Computation, 48*(177), 203–209.
6. Miller, V. S. (1986). Use of elliptic curves in cryptography. In *Advances in Cryptology: CRYPTO '85* (LNCS 218, pp. 417–426). Springer.
7. National Institute of Standards and Technology. (1999). *Data Encryption Standard (DES)* (FIPS PUB 46-3).
8. National Institute of Standards and Technology. (2001, updated 2023). *Advanced Encryption Standard (AES)* (FIPS 197).
9. National Institute of Standards and Technology. (2019). *Transitioning the Use of Cryptographic Algorithms and Key Lengths* (SP 800-131A Rev. 2).
10. National Institute of Standards and Technology. (2020). *Recommendation for Key Management: Part 1 – General* (SP 800-57 Part 1 Rev. 5).
11. National Institute of Standards and Technology. (2024). *Module-Lattice-Based Key-Encapsulation Mechanism Standard* (FIPS 203).
12. Rescorla, E. (2018). *The Transport Layer Security (TLS) Protocol Version 1.3* (RFC 8446). IETF.

**Persian sources**

13. Abbasi, M. *Information Security and Computer Networks* [in Persian].
14. Rezaei, A. *Cryptography and Data Security* [in Persian].

---

## Appendix A: Revisions to the Original

| Section | Change |
|---|---|
| 3.1.4 | Corrected the standards body for 1977: the National Bureau of Standards (NBS), renamed NIST in 1988 |
| 3.1 | Renumbered subsections (the original began at 3-1-2) |
| 3.1.5 | Added modes of operation (AES-GCM recommended, ECB discouraged) |
| 3.2.4 | Removed "high mathematical complexity" from ECC advantages, as it is a property rather than a benefit |
| 4.1 | Corrected AES key lengths to 128/192/256 bits; added 3DES effective security and deprecation status; changed 3DES speed from Medium to Low, since it runs DES three times |
| 4.2 | Added equivalent security levels for RSA and ECC |
| 4.4 | New section: measured performance with the Web Crypto API |
| 5.1 | Added hybrid encryption in TLS 1.3 as a concrete example |
| 5.2 | Updated recommendations: ECDHE for key exchange, authenticated AES modes, no DES/3DES |
| 5.3 | New section: post-quantum cryptography |
| References | Added years, editions, publishers, original papers and standards |

*Closing verse from the original (free translation):*

> Through knowledge, the veil was lifted from hidden things;
> the world was lit by the light of understanding.
> When the cipher of science stands guard over truth,
> humankind finds refuge from fear and harm.
