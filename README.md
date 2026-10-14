# Cryptography Algorithms Comparison

**The Role of Cryptography in Information Security: A Comparative Study of Cryptographic Algorithms**

Undergraduate research project · B.Sc. in Computer Engineering (Software), Islamic Azad University, Mashhad · Supervised by Dr. Gelareh Veisi · 2026

This project reviews how cryptography protects the confidentiality, integrity and availability of information, and compares the most widely used symmetric (DES, 3DES, AES) and asymmetric (RSA, ECC) algorithms by security, speed, key length and use cases. A companion web demo measures AES, RSA and ECC performance directly in the browser.

## Contents

| | |
|---|---|
| [`paper/cryptography-research-EN.pdf`](paper/cryptography-research-EN.pdf) | Full paper (English, revised edition) |
| [`paper/cryptography-research-EN-revised.md`](paper/cryptography-research-EN-revised.md) | Same paper, readable on GitHub |
| [`paper/cryptography-research-FA-original.pdf`](paper/cryptography-research-FA-original.pdf) | Original submission (Persian) |
| [`demo/index.html`](demo/index.html) | Browser benchmark and hybrid encryption demo |

## Key findings

- **No single algorithm does everything.** Modern systems use hybrid encryption: an asymmetric key exchange (ECDHE) agrees on a session key, and a symmetric cipher (AES-GCM) encrypts the data. TLS 1.3 works exactly this way.
- **AES** is the standard for bulk data. **DES** is broken by brute force and **3DES** was disallowed by NIST for encryption after 2023.
- **ECC** gives the same security as RSA with much shorter keys (256-bit ECC ≈ 3072-bit RSA).
- **Post-quantum cryptography** (NIST FIPS 203/204/205, 2024) is the next step, since quantum computers would break RSA and ECC but not AES-256.

## Measured performance

Sample results from the demo (Chromium, Linux x86-64; your numbers will differ):

| Operation | Algorithm | Avg time |
|---|---|---|
| Encrypt 8 MB | AES-256-GCM | 112 ms (72 MB/s) |
| Generate key pair | RSA-2048 | 128 ms |
| Generate key pair | ECC P-256 | 0.055 ms |
| Sign | RSA-2048 (PSS) | 1.135 ms |
| Sign | ECDSA P-256 | 0.110 ms |

ECC key generation was over 2,000 times faster than RSA-2048, and ECDSA signing about 10 times faster than RSA-PSS.

## Run the demo

The demo is a single HTML file with no dependencies. It uses the browser's built-in [Web Crypto API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Crypto_API).

```bash
git clone https://github.com/HabibullahHaqdost/Undergraduate-Researcher.git
cd Undergraduate-Researcher
npx http-server demo   # or open demo/index.html in a browser
```

It can also be published with GitHub Pages: Settings → Pages → deploy from the `main` branch root, and the demo is then live at `https://habibullahhaqdost.github.io/Undergraduate-Researcher/demo/`.

## Paper structure

1. Introduction
2. Information security concepts: the CIA triad, what cryptography is
3. Algorithms: symmetric (DES, AES) and asymmetric (RSA, ECC), with pseudocode
4. Comparison: tables and measured performance
5. Conclusions, recommendations and post-quantum outlook

## Author

**Habibullah Haqdost** · Web Developer & UI Designer · B.Sc. Computer Engineering (Software)
[GitHub](https://github.com/HabibullahHaqdost) · [LinkedIn](https://www.linkedin.com/in/habibullah-haqdost-842b8a443)
